---
title: Глава 3. Описание служб DNS-клиента для NetX Duo в ОСРВ Azure
description: В этой главе приводится описание всех служб DNS для NetX Duo в ОСРВ Azure, которые перечислены ниже в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9634adab3944c29f64d26dd688b5053dc1bd9bcb
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814731"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-dns-client-services"></a><span data-ttu-id="2966b-103">Глава 3. Описание служб DNS-клиента для NetX Duo в ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="2966b-103">Chapter 3 - Description of Azure RTOS NetX Duo DNS Client Services</span></span>

<span data-ttu-id="2966b-104">В этой главе приводится описание всех служб DNS для NetX в ОСРВ Azure, которые перечислены ниже в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="2966b-104">This chapter contains a description of all Azure RTOS NetX DNS services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="2966b-105">В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки API на предмет ошибок, в то время как значения без такого выделения полностью отключаются.</span><span class="sxs-lookup"><span data-stu-id="2966b-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="2966b-106">**nx_dns_authority_zone_start_get**: *поиск начала зоны полномочий, связанной с указанным именем узла*</span><span class="sxs-lookup"><span data-stu-id="2966b-106">**nx_dns_authority_zone_start_get** *Look up the start of a zone of authority associated with the specified host name*</span></span>

- <span data-ttu-id="2966b-107">**nx_dns_cache_initialize**: *инициализация кэша DNS*</span><span class="sxs-lookup"><span data-stu-id="2966b-107">**nx_dns_cache_initialize** *Initialize a DNS Cache.*</span></span>

- <span data-ttu-id="2966b-108">**nx_dns_cache_notify_clear**: *очистка функции уведомления о заполнении кэша*</span><span class="sxs-lookup"><span data-stu-id="2966b-108">**nx_dns_cache_notify_clear** *Clear the cache full notify function.*</span></span>

- <span data-ttu-id="2966b-109">**nx_dns_cache_notify_set**: *задание функции уведомления о заполнении кэша*</span><span class="sxs-lookup"><span data-stu-id="2966b-109">**nx_dns_cache_notify_set** *Set the cache full notify function.*</span></span>

- <span data-ttu-id="2966b-110">**nx_dns_cname_get**: *поиск канонического доменного имени для входного псевдонима доменного имени*</span><span class="sxs-lookup"><span data-stu-id="2966b-110">**nx_dns_cname_get** *Look up the canonical domain name for the input domain name alias*</span></span>

- <span data-ttu-id="2966b-111">**nx_dns_create**: *создание экземпляра DNS-клиента*</span><span class="sxs-lookup"><span data-stu-id="2966b-111">**nx_dns_create** *Create a DNS Client instance*</span></span>

- <span data-ttu-id="2966b-112">**nx_dns_delete**: *удаление экземпляра DNS-клиента*</span><span class="sxs-lookup"><span data-stu-id="2966b-112">**nx_dns_delete** *Delete a DNS Client instance*</span></span>

- <span data-ttu-id="2966b-113">**nx_dns_domain_name_server_get**: *поиск полномочных серверов доменных имен для входной зоны домена*</span><span class="sxs-lookup"><span data-stu-id="2966b-113">**nx_dns_domain_name_server_get** *Look up the authoritative name servers for the input domain zone*</span></span>

- <span data-ttu-id="2966b-114">**nx_dns_domain_mail_exchange_get**: *поиск обмена почтой, связанного с указанным именем узла*</span><span class="sxs-lookup"><span data-stu-id="2966b-114">**nx_dns_domain_mail_exchange_get** *Look up the mail exchange associated the specified host name.*</span></span>

- <span data-ttu-id="2966b-115">**nx_dns_domain_service_get**: *поиск служб, связанных с указанным именем узла*</span><span class="sxs-lookup"><span data-stu-id="2966b-115">**nx_dns_domain_service_get** *Look up the service(s) associated with the specified host name*</span></span>

- <span data-ttu-id="2966b-116">**nx_dns_get_serverlist_size**: *возврат размера списка серверов DNS-клиента*</span><span class="sxs-lookup"><span data-stu-id="2966b-116">**nx_dns_get_serverlist_size** *Return the size of the DNS Client server list*</span></span>

- <span data-ttu-id="2966b-117">**nx_dns_info_by_name_get**: *возврат IP-адреса и порта с запросом по входному имени узла*</span><span class="sxs-lookup"><span data-stu-id="2966b-117">**nx_dns_info_by_name_get** *Return IP address, port querying on input host name*</span></span>

- <span data-ttu-id="2966b-118">**nx_dns_ipv4_address_by_name_get**: *поиск IPv4-адреса по указанному имени узла*</span><span class="sxs-lookup"><span data-stu-id="2966b-118">**nx_dns_ipv4_address_by_name_get** *Look up the IPv4 address from the specified host name*</span></span>

- <span data-ttu-id="2966b-119">**nxd_dns_ipv6_address_by_name_get**: *поиск IPv6-адреса по указанному имени узла*</span><span class="sxs-lookup"><span data-stu-id="2966b-119">**nxd_dns_ipv6_address_by_name_get** *Look up the IPv6 address from the specified host name*</span></span>

- <span data-ttu-id="2966b-120">**nx_dns_host_by_address_get**: *функция-оболочка для nxd_dns_host_by_address_get для поиска имени узла по указанному IP-адресу (поддерживает только IPv4-адреса)*</span><span class="sxs-lookup"><span data-stu-id="2966b-120">**nx_dns_host_by_address_get** *Wrapper function for nxd_dns_host_by_address_get to look up a host name from a specified IP address (supports only IPv4 addresses)*</span></span>

- <span data-ttu-id="2966b-121">**nxd_dns_host_by_address_get**: *поиск IP-адреса по входному имени узла (поддерживает IPv4- и IPv6-адреса)*</span><span class="sxs-lookup"><span data-stu-id="2966b-121">**nxd_dns_host_by_address_get** *Look up an IP address from the input host name (supports both IPv4 and IPv6 addresses)*</span></span>

- <span data-ttu-id="2966b-122">**nx_dns_host_by_name_get**: *функция-оболочка для nxd_dns_host_by_address_get для поиска имени узла по указанному адресу (поддерживает только IPv4-адреса)*</span><span class="sxs-lookup"><span data-stu-id="2966b-122">**nx_dns_host_by_name_get** *Wrapper function for nxd_dns_host_by_address_get to look up a host name from the specified address (supports only IPv4 addresses)*</span></span>

- <span data-ttu-id="2966b-123">**nxd_dns_host_by_name_get**: *поиск IP-адреса по входному имени узла (поддерживает IPv4- и IPv6-адреса)*</span><span class="sxs-lookup"><span data-stu-id="2966b-123">**nxd_dns_host_by_name_get** *Look up an IP address from the input host name (supports both IPv4 and IPv6 addresses)*</span></span>

- <span data-ttu-id="2966b-124">**nx_dns_host_text_get**: *поиск текстовых данных для входного доменного имени*</span><span class="sxs-lookup"><span data-stu-id="2966b-124">**nx_dns_host_text_get** *Look up the text data for the input domain name*</span></span>

- <span data-ttu-id="2966b-125">**nx_dns_packet_pool_set**: *задание пула пакетов DNS-клиента*</span><span class="sxs-lookup"><span data-stu-id="2966b-125">**nx_dns_packet_pool_set** *Set the DNS Client packet pool*</span></span>

- <span data-ttu-id="2966b-126">**nx_dns_server_add**: *функция-оболочка для* nxd_dns_server_add *для добавления DNS-сервера по указанному адресу в список клиента (поддерживает только IPv4)*</span><span class="sxs-lookup"><span data-stu-id="2966b-126">**nx_dns_server_add** *Wrapper function for* nxd_dns_server_add *to add a DNS Server at the specified address to the Client list (supports only IPv4)*</span></span>

- <span data-ttu-id="2966b-127">**nxd_dns_server_add**: *добавление DNS-сервера по указанному IP-адресу в список серверов клиента (поддерживает IPv4- или IPv6-адреса)*</span><span class="sxs-lookup"><span data-stu-id="2966b-127">**nxd_dns_server_add** *Add a DNS Server of the specified IP address to the Client server list (supports both IPv4 or IPv6 addresses)*</span></span>

- <span data-ttu-id="2966b-128">**nx_dns_server_get**: *возврат DNS-сервера из списка клиента (поддерживает только IPv4-адреса)*</span><span class="sxs-lookup"><span data-stu-id="2966b-128">**nx_dns_server_get** *Return the DNS Server in the Client list (supports only IPv4 addresses)*</span></span>

- <span data-ttu-id="2966b-129">**nxd_dns_server_get**: *возврат DNS-сервера из списка клиента (поддерживает IPv4- или IPv6-адреса)*</span><span class="sxs-lookup"><span data-stu-id="2966b-129">**nxd_dns_server_get** *Return the DNS Server in the Client list (supports both IPv4 and IPv6 addresses)*</span></span>

- <span data-ttu-id="2966b-130">**nx_dns_server_remove**: *функция-оболочка для nxd_dns_server_remove для удаления DNS-сервера из списка клиента*</span><span class="sxs-lookup"><span data-stu-id="2966b-130">**nx_dns_server_remove** *Wrapper function for nxd_dns_server_remove to remove a DNS Server from the Client list*</span></span>

- <span data-ttu-id="2966b-131">**nxd_dns_server_remove** *удаление DNS-сервера по указанному IP-адресу из списка клиента (поддерживает IPv4- и IPv6-адреса)*</span><span class="sxs-lookup"><span data-stu-id="2966b-131">**nxd_dns_server_remove** *Remove a DNS Server of the specified IP address from the Client list (supports both IPv4 and IPv6 addresses)*</span></span>

- <span data-ttu-id="2966b-132">**nx_dns_server_remove_all**: *удаление всех DNS-серверов из списка клиента*</span><span class="sxs-lookup"><span data-stu-id="2966b-132">**nx_dns_server_remove_all** *Remove all DNS Servers from the Client list*</span></span>

## <a name="nx_dns_authority_zone_start_get"></a><span data-ttu-id="2966b-133">nx_dns_authority_zone_start_get</span><span class="sxs-lookup"><span data-stu-id="2966b-133">nx_dns_authority_zone_start_get</span></span>

<span data-ttu-id="2966b-134">Поиск начала зоны полномочий для входного узла.</span><span class="sxs-lookup"><span data-stu-id="2966b-134">Look up the start of the zone of authority for the input host</span></span>

### <a name="prototype"></a><span data-ttu-id="2966b-135">Прототип</span><span class="sxs-lookup"><span data-stu-id="2966b-135">Prototype</span></span>
```C
UINT nx_dns_authority_zone_start_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                      VOID *record_buffer,                                        
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="2966b-136">Описание</span><span class="sxs-lookup"><span data-stu-id="2966b-136">Description</span></span>

<span data-ttu-id="2966b-137">Если параметр NX_DNS_ENABLE_EXTENDED_RR_TYPES определен, эта служба отправляет запрос типа SOA с указанным доменным именем, чтобы получить начало зоны полномочий для входного доменного имени.</span><span class="sxs-lookup"><span data-stu-id="2966b-137">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type SOA with the specified domain name to obtain the start of the zone of authority for the input domain name.</span></span> <span data-ttu-id="2966b-138">DNS-клиент копирует записи SOA, возвращенные в ответе DNS-сервера, по адресу памяти *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="2966b-138">The DNS Client copies the SOA record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span>

> [!NOTE]
> <span data-ttu-id="2966b-139">Для получения данных *record_buffer* должен быть выровнен по 4 байт.</span><span class="sxs-lookup"><span data-stu-id="2966b-139">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="2966b-140">В DNS-клиенте для NetX Duo тип записи SOA (NX_DNS_SOA_ENTRY) сохраняется в виде семи 4-байтовых параметров, в сумме составляющих 28 байт.</span><span class="sxs-lookup"><span data-stu-id="2966b-140">In NetX Duo DNS Client, the SOA record type, NX_DNS_SOA_ENTRY, is saved as seven 4 byte parameters, totaling 28 bytes:</span></span>

- <span data-ttu-id="2966b-141">**nx_dns_soa_host_mname_ptr**: указатель на основной источник данных для этой зоны</span><span class="sxs-lookup"><span data-stu-id="2966b-141">**nx_dns_soa_host_mname_ptr** Pointer to primary source of data for this zone.</span></span>
- <span data-ttu-id="2966b-142">**nx_dns_soa_host_rname_ptr**: указатель на почтовый ящик, ответственный за эту зону</span><span class="sxs-lookup"><span data-stu-id="2966b-142">**nx_dns_soa_host_rname_ptr** Pointer to mailbox responsible for this zone</span></span>
- <span data-ttu-id="2966b-143">**nx_dns_soa_serial**: номер версии зоны</span><span class="sxs-lookup"><span data-stu-id="2966b-143">**nx_dns_soa_serial** Zone version number</span></span>
- <span data-ttu-id="2966b-144">**nx_dns_soa_refresh**: интервал обновления</span><span class="sxs-lookup"><span data-stu-id="2966b-144">**nx_dns_soa_refresh** Refresh interval</span></span>
- <span data-ttu-id="2966b-145">**nx_dns_soa_retry**: интервал между повторными попытками запроса SOA</span><span class="sxs-lookup"><span data-stu-id="2966b-145">**nx_dns_soa_retry** Interval between SOA query retries</span></span>
- <span data-ttu-id="2966b-146">**nx_dns_soa_expire**: время истечения срока действия SOA</span><span class="sxs-lookup"><span data-stu-id="2966b-146">**nx_dns_soa_expire** Time duration when SOA expires</span></span>
- <span data-ttu-id="2966b-147">**nx_dns_soa_minmum**: поле минимального срока жизни в сообщениях ответа DNS для имени узла SOA</span><span class="sxs-lookup"><span data-stu-id="2966b-147">**nx_dns_soa_minmum** Minimum TTL field in SOA hostname DNS reply messages</span></span>

<span data-ttu-id="2966b-148">Хранение двух записей SOA показано ниже.</span><span class="sxs-lookup"><span data-stu-id="2966b-148">The storage of a two SOA records is shown below.</span></span> <span data-ttu-id="2966b-149">Записи SOA, содержащие данные фиксированной длины, размещаются, начиная с верхней части буфера.</span><span class="sxs-lookup"><span data-stu-id="2966b-149">The SOA records containing fixed length data are entered starting at the top of the buffer.</span></span> <span data-ttu-id="2966b-150">Указатели MNAME и RNAME указывают на данные переменной длины (имена узлов), которые сохраняются в нижней части буфера.</span><span class="sxs-lookup"><span data-stu-id="2966b-150">The pointers MNAME and RNAME point to the variable length data (host names) which are stored at the bottom of the buffer.</span></span> <span data-ttu-id="2966b-151">Дополнительные записи SOA размещаются после первой записи ("дополнительные записи SOA..."), и их данные переменной длины сохраняются над данными переменной длины последней записи ("дополнительные данные переменной длины SOA").</span><span class="sxs-lookup"><span data-stu-id="2966b-151">Additional SOA records are entered after the first record (“additional SOA records…”) and their variable length data is stored above the last entry’s variable length data (“additional SOA variable length data”):</span></span>

![Хранение двух записей SOA](media/image4.png)

<span data-ttu-id="2966b-153">Если во входном *record_buffer* невозможно сохранить все данные SOA в ответе сервера, *record_buffer* будет содержать столько записей, сколько сможет, и возвратит это количество записей в буфере.</span><span class="sxs-lookup"><span data-stu-id="2966b-153">If the input *record_buffer* cannot hold all the SOA data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="2966b-154">На основе числа записей SOA, возвращенных в \**record_count*, приложение может проанализировать данные из *record_buffer* и извлечь строки имени узла начала зоны полномочий.</span><span class="sxs-lookup"><span data-stu-id="2966b-154">With the number of SOA records returned in \**record_count,* the application can parse the data from *record_buffer* and extract the start of zone authority host name strings.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2966b-155">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2966b-155">Input Parameters</span></span>

- <span data-ttu-id="2966b-156">**dns_ptr**: указатель на DNS-клиент</span><span class="sxs-lookup"><span data-stu-id="2966b-156">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="2966b-157">**host_name**: указатель на имя узла, для которого следует получить данные SOA</span><span class="sxs-lookup"><span data-stu-id="2966b-157">**host_name** Pointer to host name to obtain SOA data for</span></span>
- <span data-ttu-id="2966b-158">**record_buffer**: указатель на расположение, в которое следует извлечь данные SOA</span><span class="sxs-lookup"><span data-stu-id="2966b-158">**record_buffer** Pointer to location to extract SOA data into</span></span>
- <span data-ttu-id="2966b-159">**buffer_size**: размер буфера для хранения данных SOA</span><span class="sxs-lookup"><span data-stu-id="2966b-159">**buffer_size** Size of buffer to hold SOA data</span></span>
- <span data-ttu-id="2966b-160">**record_count**: указатель на количество полученных записей SOA</span><span class="sxs-lookup"><span data-stu-id="2966b-160">**record_count** Pointer to the number of SOA records retrieved</span></span>
- <span data-ttu-id="2966b-161">**wait_option**: параметр ожидания для получения ответа DNS-сервера</span><span class="sxs-lookup"><span data-stu-id="2966b-161">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="2966b-162">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2966b-162">Return Values</span></span>

- <span data-ttu-id="2966b-163">**NX_SUCCESS** (0x00) — данные SOA успешно получены.</span><span class="sxs-lookup"><span data-stu-id="2966b-163">**NX_SUCCESS** (0x00) Successfully obtained SOA data</span></span>
- <span data-ttu-id="2966b-164">**NX_DNS_NO_SERVER** (0xA1) — список серверов клиента пуст.</span><span class="sxs-lookup"><span data-stu-id="2966b-164">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="2966b-165">**NX_DNS_QUERY_FAILED** (0xA3) — не получен допустимый ответ DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-165">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="2966b-166">NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-166">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="2966b-167">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="2966b-167">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="2966b-168">NX_DNS_PARAM_ERROR (0xA8) — недопустимые входные данные без указателя.</span><span class="sxs-lookup"><span data-stu-id="2966b-168">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2966b-169">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2966b-169">Allowed From</span></span>

<span data-ttu-id="2966b-170">Потоки</span><span class="sxs-lookup"><span data-stu-id="2966b-170">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2966b-171">Пример</span><span class="sxs-lookup"><span data-stu-id="2966b-171">Example</span></span>
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

## <a name="nx_dns_cache_initialize"></a><span data-ttu-id="2966b-172">nx_dns_cache_initialize</span><span class="sxs-lookup"><span data-stu-id="2966b-172">nx_dns_cache_initialize</span></span>

<span data-ttu-id="2966b-173">Инициализация кэша DNS</span><span class="sxs-lookup"><span data-stu-id="2966b-173">Initialize the DNS Cache</span></span>

### <a name="prototype"></a><span data-ttu-id="2966b-174">Прототип</span><span class="sxs-lookup"><span data-stu-id="2966b-174">Prototype</span></span>
```C
UINT nx_dns_cache_initialize(NX_DNS *dns_ptr,
                            VOID *cache_ptr, UINT cache_size);
```

### <a name="description"></a><span data-ttu-id="2966b-175">Описание</span><span class="sxs-lookup"><span data-stu-id="2966b-175">Description</span></span>

<span data-ttu-id="2966b-176">Эта служба создает кэш DNS и инициализирует его.</span><span class="sxs-lookup"><span data-stu-id="2966b-176">This service creates and initializes a DNS Cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2966b-177">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2966b-177">Input Parameters</span></span>

- <span data-ttu-id="2966b-178">**dns_ptr**: указатель на блок управления DNS</span><span class="sxs-lookup"><span data-stu-id="2966b-178">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="2966b-179">**cache_ptr**: указатель на кэш DNS</span><span class="sxs-lookup"><span data-stu-id="2966b-179">**cache_ptr** Pointer to DNS Cache.</span></span>
- <span data-ttu-id="2966b-180">**cache_size**: размер кэша DNS в байтах</span><span class="sxs-lookup"><span data-stu-id="2966b-180">**cache_size** Size of DNS Cache, in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="2966b-181">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2966b-181">Return Values</span></span>

- <span data-ttu-id="2966b-182">**NX_SUCCESS** (0x00) — кэш DNS успешно инициализирован.</span><span class="sxs-lookup"><span data-stu-id="2966b-182">**NX_SUCCESS** (0x00) DNS Cache successfully initialized</span></span>
- <span data-ttu-id="2966b-183">NX_DNS_PARAM_ERROR (0xA8) — недопустимые входные данные без указателя.</span><span class="sxs-lookup"><span data-stu-id="2966b-183">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="2966b-184">NX_DNS_CACHE_ERROR (0xB7) — недопустимый указатель на кэш.</span><span class="sxs-lookup"><span data-stu-id="2966b-184">NX_DNS_CACHE_ERROR (0xB7) Invalid Cache pointer.</span></span>
- <span data-ttu-id="2966b-185">NX_PTR_ERROR (0x07) — недопустимый указатель DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-185">NX_PTR_ERROR (0x07) Invalid DNS pointer.</span></span> 
- <span data-ttu-id="2966b-186">NX_DNS_ERROR (0xA0) — кэш не выровнен по 4 байт.</span><span class="sxs-lookup"><span data-stu-id="2966b-186">NX_DNS_ERROR (0xA0) Cache is not 4-byte aligned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2966b-187">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2966b-187">Allowed From</span></span>

<span data-ttu-id="2966b-188">Потоки</span><span class="sxs-lookup"><span data-stu-id="2966b-188">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2966b-189">Пример</span><span class="sxs-lookup"><span data-stu-id="2966b-189">Example</span></span>
```C
/* Initialize the DNS Cache.  */
status =  nx_dns_cache_initialize(&my_dns, &dns_cache, 2048);

/* If status is NX_SUCCESS DNS Cache was successfully initialized.  */
```

## <a name="nx_dns_cache_notify_clear"></a><span data-ttu-id="2966b-190">nx_dns_cache_notify_clear</span><span class="sxs-lookup"><span data-stu-id="2966b-190">nx_dns_cache_notify_clear</span></span>

<span data-ttu-id="2966b-191">Очистка функции уведомления о заполнении кэша DNS</span><span class="sxs-lookup"><span data-stu-id="2966b-191">Clear the DNS Cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="2966b-192">Прототип</span><span class="sxs-lookup"><span data-stu-id="2966b-192">Prototype</span></span>
```C
UINT nx_dns_cache_notify_clear(NX_DNS *dns_ptr);
```

### <a name="description"></a><span data-ttu-id="2966b-193">Описание</span><span class="sxs-lookup"><span data-stu-id="2966b-193">Description</span></span>

<span data-ttu-id="2966b-194">Эта служба очищает функцию уведомления о заполнении кэша.</span><span class="sxs-lookup"><span data-stu-id="2966b-194">This service clears the cache full notify function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2966b-195">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2966b-195">Input Parameters</span></span>

- <span data-ttu-id="2966b-196">**dns_ptr**: указатель на блок управления DNS</span><span class="sxs-lookup"><span data-stu-id="2966b-196">**dns_ptr** Pointer to DNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="2966b-197">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2966b-197">Return Values</span></span>

- <span data-ttu-id="2966b-198">**NX_SUCCESS** (0x00) — уведомление о заполнении кэша DNS успешно задано.</span><span class="sxs-lookup"><span data-stu-id="2966b-198">**NX_SUCCESS** (0x00) DNS cache notify successfully set</span></span>
- <span data-ttu-id="2966b-199">NX_DNS_PARAM_ERROR (0xA8) — недопустимые входные данные без указателя.</span><span class="sxs-lookup"><span data-stu-id="2966b-199">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="2966b-200">NX_PTR_ERROR (0x07) — недопустимый указатель DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-200">NX_PTR_ERROR (0x07) Invalid DNS pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2966b-201">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2966b-201">Allowed From</span></span>

<span data-ttu-id="2966b-202">Потоки</span><span class="sxs-lookup"><span data-stu-id="2966b-202">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2966b-203">Пример</span><span class="sxs-lookup"><span data-stu-id="2966b-203">Example</span></span>
```C
/* Clear the DNS Cache full notify function. */
status =  nx_dns_cache_notify_clear(&my_dns);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully cleared. */
```

## <a name="nx_dns_cache_notify_set"></a><span data-ttu-id="2966b-204">nx_dns_cache_notify_set</span><span class="sxs-lookup"><span data-stu-id="2966b-204">nx_dns_cache_notify_set</span></span>

<span data-ttu-id="2966b-205">Задание функции уведомления о заполнении кэша DNS</span><span class="sxs-lookup"><span data-stu-id="2966b-205">Set the DNS Cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="2966b-206">Прототип</span><span class="sxs-lookup"><span data-stu-id="2966b-206">Prototype</span></span>
```C
UINT nx_dns_cache_notify_set(NX_DNS *dns_ptr,
                            VOID (*cache_full_notify_cb)(NX_DNS *dns_ptr));
```

### <a name="description"></a><span data-ttu-id="2966b-207">Описание</span><span class="sxs-lookup"><span data-stu-id="2966b-207">Description</span></span>

<span data-ttu-id="2966b-208">Эта служба задает функцию уведомления о заполнении кэша.</span><span class="sxs-lookup"><span data-stu-id="2966b-208">This service sets the cache full notify function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2966b-209">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2966b-209">Input Parameters</span></span>

- <span data-ttu-id="2966b-210">**dns_ptr**: указатель на блок управления DNS</span><span class="sxs-lookup"><span data-stu-id="2966b-210">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="2966b-211">**cache_full_notify_cb**: функция обратного вызова, вызываемая при заполнении кэша</span><span class="sxs-lookup"><span data-stu-id="2966b-211">**cache_full_notify_cb** The callback function to be invoked when cache become full.</span></span>

### <a name="return-values"></a><span data-ttu-id="2966b-212">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2966b-212">Return Values</span></span>

- <span data-ttu-id="2966b-213">**NX_SUCCESS** (0x00) — уведомление о заполнении кэша DNS успешно задано.</span><span class="sxs-lookup"><span data-stu-id="2966b-213">**NX_SUCCESS** (0x00) DNS cache notify successfully set</span></span>
- <span data-ttu-id="2966b-214">NX_DNS_PARAM_ERROR (0xA8) — недопустимые входные данные без указателя.</span><span class="sxs-lookup"><span data-stu-id="2966b-214">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="2966b-215">NX_PTR_ERROR (0x07) — недопустимый указатель DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-215">NX_PTR_ERROR (0x07) Invalid DNS pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2966b-216">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2966b-216">Allowed From</span></span>

<span data-ttu-id="2966b-217">Потоки</span><span class="sxs-lookup"><span data-stu-id="2966b-217">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2966b-218">Пример</span><span class="sxs-lookup"><span data-stu-id="2966b-218">Example</span></span>
```C
/* Set the DNS Cache full notify function. */
status =  nx_dns_cache_notify_set(&my_dns, cache_full_notify_cb);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully set. */
```

## <a name="nx_dns_cname_get"></a><span data-ttu-id="2966b-219">nx_dns_cname_get</span><span class="sxs-lookup"><span data-stu-id="2966b-219">nx_dns_cname_get</span></span>

<span data-ttu-id="2966b-220">Поиск канонического имени для входного имени узла</span><span class="sxs-lookup"><span data-stu-id="2966b-220">Look up the canonical name for the input hostname</span></span>

### <a name="prototype"></a><span data-ttu-id="2966b-221">Прототип</span><span class="sxs-lookup"><span data-stu-id="2966b-221">Prototype</span></span>
```C
UINT nx_dns_cname_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                     UCHAR *record_buffer, UINT buffer_size, 
                     ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="2966b-222">Описание</span><span class="sxs-lookup"><span data-stu-id="2966b-222">Description</span></span>

<span data-ttu-id="2966b-223">Если параметр NX_DNS_ENABLE_EXTENDED_RR_TYPES определен в файле *nxd_dns.h*, эта служба отправляет запрос типа CNAME с указанным доменным именем для получения канонического доменного имени.</span><span class="sxs-lookup"><span data-stu-id="2966b-223">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined in *nxd_dns.h*, this service sends a query of type CNAME with the specified domain name to obtain the canonical domain name.</span></span> <span data-ttu-id="2966b-224">DNS-клиент копирует строку CNAME, возвращенную в ответе DNS-сервера, по адресу памяти *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="2966b-224">The DNS Client copies the CNAME string returned in the DNS Server response into the *record_buffer* memory location.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2966b-225">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2966b-225">Input Parameters</span></span>

- <span data-ttu-id="2966b-226">**dns_ptr**: указатель на DNS-клиент</span><span class="sxs-lookup"><span data-stu-id="2966b-226">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="2966b-227">**host_name**: указатель на имя узла, для которого следует получить данные CNAME</span><span class="sxs-lookup"><span data-stu-id="2966b-227">**host_name** Pointer to host name to obtain CNAME data for</span></span>
- <span data-ttu-id="2966b-228">**record_buffer**: указатель на расположение, в которое следует извлечь данные CNAME</span><span class="sxs-lookup"><span data-stu-id="2966b-228">**record_buffer** Pointer to location to extract CNAME data into</span></span>
- <span data-ttu-id="2966b-229">**buffer_size**: размер буфера для хранения данных CNAME</span><span class="sxs-lookup"><span data-stu-id="2966b-229">**buffer_size** Size of buffer to hold CNAME data</span></span>
- <span data-ttu-id="2966b-230">**wait_option**: параметр ожидания для получения ответа DNS-сервера</span><span class="sxs-lookup"><span data-stu-id="2966b-230">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="2966b-231">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2966b-231">Return Values</span></span>

- <span data-ttu-id="2966b-232">**NX_SUCCESS** (0x00) — данные CNAME успешно получены.</span><span class="sxs-lookup"><span data-stu-id="2966b-232">**NX_SUCCESS** (0x00) Successfully obtained CNAME data</span></span>
- <span data-ttu-id="2966b-233">**NX_DNS_NO_SERVER** (0xA1) — список серверов клиента пуст.</span><span class="sxs-lookup"><span data-stu-id="2966b-233">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="2966b-234">**NX_DNS_QUERY_FAILED** (0xA3) — не получен допустимый ответ DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-234">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="2966b-235">NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-235">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="2966b-236">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="2966b-236">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="2966b-237">NX_DNS_PARAM_ERROR (0xA8) — недопустимые входные данные без указателя.</span><span class="sxs-lookup"><span data-stu-id="2966b-237">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2966b-238">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2966b-238">Allowed From</span></span>

<span data-ttu-id="2966b-239">Потоки</span><span class="sxs-lookup"><span data-stu-id="2966b-239">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2966b-240">Пример</span><span class="sxs-lookup"><span data-stu-id="2966b-240">Example</span></span>
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

##  <a name="nx_dns_create"></a><span data-ttu-id="2966b-241">nx_dns_create</span><span class="sxs-lookup"><span data-stu-id="2966b-241">nx_dns_create</span></span>

<span data-ttu-id="2966b-242">Создание экземпляра DNS-клиента</span><span class="sxs-lookup"><span data-stu-id="2966b-242">Create a DNS Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="2966b-243">Прототип</span><span class="sxs-lookup"><span data-stu-id="2966b-243">Prototype</span></span>
```C
UINT nx_dns_create(NX_DNS *dns_ptr, NX_IP *ip_ptr, CHAR *domain_name);
```
### <a name="description"></a><span data-ttu-id="2966b-244">Описание</span><span class="sxs-lookup"><span data-stu-id="2966b-244">Description</span></span>

<span data-ttu-id="2966b-245">Эта служба создает экземпляр DNS-клиента для ранее созданного экземпляра IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="2966b-245">This service creates a DNS Client instance for the previously created IP instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2966b-246">Приложение должно гарантировать, что размер полезных данных пакета для пула пакетов, используемого DNS-клиентом, достаточен для поддержки сообщения DNS размером максимум 512 байт и заголовков UDP, IP и Ethernet.</span><span class="sxs-lookup"><span data-stu-id="2966b-246">The application must ensure that the packet payload of the packet pool used by the DNS Client is large enough for the maximum 512 byte DNS message, plus UDP, IP and Ethernet headers.</span></span> <span data-ttu-id="2966b-247">Если DNS-клиент создает собственный пул пакетов, он определяется параметрами NX_DNS_PACKET_PAYLOAD и NX_DNS_PACKET_POOL_SIZE.</span><span class="sxs-lookup"><span data-stu-id="2966b-247">If the DNS Client creates its own packet pool, this is defined by NX_DNS_PACKET_PAYLOAD and NX_DNS_PACKET_POOL_SIZE.</span></span>

<span data-ttu-id="2966b-248">Если приложение DNS-клиента предоставляет ранее созданный пул пакетов, размер полезных данных для DNS-клиента IPv4 должен составлять 512 байт для сообщения DNS максимального размера плюс 20 байт для заголовка IP, 8 байт для заголовка UDP и 14 байт для заголовка Ethernet.</span><span class="sxs-lookup"><span data-stu-id="2966b-248">If the DNS Client application prefers to supply a previously created packet pool, the payload for IPv4 DNS Client should be 512 bytes for the maximum DNS plus 20 bytes for the IP header, 8 bytes for the UDP header and 14 bytes for the Ethernet header.</span></span> <span data-ttu-id="2966b-249">Для IPv6 единственным отличием является заголовок IP-адреса размером 40 байт, поэтому пакет должен вмещать заголовок IPv6 в 40 байт.</span><span class="sxs-lookup"><span data-stu-id="2966b-249">For IPv6 the only difference is the IP header is 40 bytes, therefore the packet needs to accommodate the IPv6 header of 40 bytes.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2966b-250">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2966b-250">Input Parameters</span></span>

- <span data-ttu-id="2966b-251">**dns_ptr**: указатель на DNS-клиент</span><span class="sxs-lookup"><span data-stu-id="2966b-251">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="2966b-252">**ip_ptr**: указатель на ранее созданный экземпляр IP-адреса</span><span class="sxs-lookup"><span data-stu-id="2966b-252">**ip_ptr** Pointer to previously created IP instance.</span></span>  
- <span data-ttu-id="2966b-253">**domain_name**: указатель на доменное имя для экземпляра DNS</span><span class="sxs-lookup"><span data-stu-id="2966b-253">**domain_name** Pointer to domain name for DNS instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="2966b-254">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2966b-254">Return Values</span></span>

- <span data-ttu-id="2966b-255">**NX_SUCCESS** (0x00) — экземпляр DNS-клиента успешно создан.</span><span class="sxs-lookup"><span data-stu-id="2966b-255">**NX_SUCCESS** (0x00) Successful DNS create</span></span>
- <span data-ttu-id="2966b-256">**NX_DNS_ERROR** (0xA0) — ошибка при создании экземпляра DNS-клиента.</span><span class="sxs-lookup"><span data-stu-id="2966b-256">**NX_DNS_ERROR** (0xA0) DNS create error</span></span>
- <span data-ttu-id="2966b-257">NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-257">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="2966b-258">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="2966b-258">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2966b-259">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2966b-259">Allowed From</span></span>

<span data-ttu-id="2966b-260">Потоки</span><span class="sxs-lookup"><span data-stu-id="2966b-260">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2966b-261">Пример</span><span class="sxs-lookup"><span data-stu-id="2966b-261">Example</span></span>
```C
/* Create a DNS Client instance. */
status =  nx_dns_create(&my_dns, &my_ip, "My DNS");

/* If status is NX_SUCCESS a DNS Client instance was successfully
   created. */
```

## <a name="nx_dns_delete"></a><span data-ttu-id="2966b-262">nx_dns_delete</span><span class="sxs-lookup"><span data-stu-id="2966b-262">nx_dns_delete</span></span>

<span data-ttu-id="2966b-263">Удаление экземпляра DNS-клиента</span><span class="sxs-lookup"><span data-stu-id="2966b-263">Delete a DNS Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="2966b-264">Прототип</span><span class="sxs-lookup"><span data-stu-id="2966b-264">Prototype</span></span>
```C
UINT nx_dns_delete(NX_DNS *dns_ptr);
```
### <a name="description"></a><span data-ttu-id="2966b-265">Описание</span><span class="sxs-lookup"><span data-stu-id="2966b-265">Description</span></span>

<span data-ttu-id="2966b-266">Эта служба удаляет ранее созданный экземпляр DNS-клиента и освобождает его ресурсы.</span><span class="sxs-lookup"><span data-stu-id="2966b-266">This service deletes a previously created DNS Client instance and frees up its resources.</span></span> 

> [!NOTE]
> <span data-ttu-id="2966b-267">Если параметр NX_DNS_CLIENT_USER_CREATE_PACKET_POOL определен и DNS-клиенту был назначен определяемый пользователем пул пакетов, приложение может удалить пул пакетов DNS-клиента, если он больше не нужен.</span><span class="sxs-lookup"><span data-stu-id="2966b-267">If NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is defined and the DNS Client was assigned a user defined packet pool, it is up to the application to delete the DNS Client packet pool if it no longer needs it.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2966b-268">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2966b-268">Input Parameters</span></span>

- <span data-ttu-id="2966b-269">**dns_ptr**: указатель на ранее созданный экземпляр DNS-клиента</span><span class="sxs-lookup"><span data-stu-id="2966b-269">**dns_ptr** Pointer to previously created DNS Client instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="2966b-270">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2966b-270">Return Values</span></span>

- <span data-ttu-id="2966b-271">**NX_SUCCESS** (0x00) — DNS-клиент успешно удален.</span><span class="sxs-lookup"><span data-stu-id="2966b-271">**NX_SUCCESS** (0x00) Successful DNS Client delete.</span></span>
- <span data-ttu-id="2966b-272">NX_PTR_ERROR (0x07) — недопустимый указатель IP-адреса или DNS-клиента.</span><span class="sxs-lookup"><span data-stu-id="2966b-272">NX_PTR_ERROR (0x07) Invalid IP or DNS Client pointer.</span></span>
- <span data-ttu-id="2966b-273">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="2966b-273">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2966b-274">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2966b-274">Allowed From</span></span>

<span data-ttu-id="2966b-275">Потоки</span><span class="sxs-lookup"><span data-stu-id="2966b-275">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2966b-276">Пример</span><span class="sxs-lookup"><span data-stu-id="2966b-276">Example</span></span>
```C
/* Delete a DNS Client instance. */
status =  nx_dns_delete(&my_dns);

/* If status is NX_SUCCESS the DNS Client instance was successfully
   deleted. */
```

## <a name="nx_dns_domain_name_server_get"></a><span data-ttu-id="2966b-277">nx_dns_domain_name_server_get</span><span class="sxs-lookup"><span data-stu-id="2966b-277">nx_dns_domain_name_server_get</span></span>

<span data-ttu-id="2966b-278">Поиск полномочных серверов доменных имен для входной зоны домена</span><span class="sxs-lookup"><span data-stu-id="2966b-278">Look up the authoritative name servers for the input domain zone</span></span>

### <a name="prototype"></a><span data-ttu-id="2966b-279">Прототип</span><span class="sxs-lookup"><span data-stu-id="2966b-279">Prototype</span></span>
```C
UINT nx_dns_domain_name_server_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                   VOID *record_buffer, UINT buffer_size, 
                                   UINT *record_count, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="2966b-280">Описание</span><span class="sxs-lookup"><span data-stu-id="2966b-280">Description</span></span>

<span data-ttu-id="2966b-281">Если параметр NX_DNS_ENABLE_EXTENDED_RR_TYPES определен, эта служба отправляет запрос типа NS с указанным доменным именем, чтобы получить серверы доменных имен для входного имени домена.</span><span class="sxs-lookup"><span data-stu-id="2966b-281">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type NS with the specified domain name to obtain the name servers for the input domain name.</span></span> <span data-ttu-id="2966b-282">DNS-клиент копирует записи NS, возвращенные в ответе DNS-сервера, по адресу памяти *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="2966b-282">The DNS Client copies the NS record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span>

> [!NOTE]
> <span data-ttu-id="2966b-283">Для получения данных *record_buffer* должен быть выровнен по 4 байт.</span><span class="sxs-lookup"><span data-stu-id="2966b-283">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="2966b-284">В DNS-клиенте для NetX Duo тип данных NS (NX_DNS_NS_ENTRY) сохраняется в виде двух 4-байтовых параметров.</span><span class="sxs-lookup"><span data-stu-id="2966b-284">In NetX Duo DNS Client the NS data type, NX_DNS_NS_ENTRY, is saved as two 4-byte parameters:</span></span>

- <span data-ttu-id="2966b-285">**nx_dns_ns_ipv4_address**: IPv4-адрес сервера доменных имен.</span><span class="sxs-lookup"><span data-stu-id="2966b-285">**nx_dns_ns_ipv4_address** Name server’s IPv4 address</span></span>
- <span data-ttu-id="2966b-286">**nx_dns_ns_hostname_ptr**: указатель на имя узла сервера доменных имен.</span><span class="sxs-lookup"><span data-stu-id="2966b-286">**nx_dns_ns_hostname_ptr** Pointer to the name server’s hostname</span></span>

<span data-ttu-id="2966b-287">Буфер, показанный ниже, содержит четыре записи NX_DNS_NS_ENTRY.</span><span class="sxs-lookup"><span data-stu-id="2966b-287">The buffer shown below contains four NX_DNS_NS_ENTRY records.</span></span> <span data-ttu-id="2966b-288">Указатель на строку имени узла в каждой записи указывает на соответствующую строку имени узла в нижней половине буфера.</span><span class="sxs-lookup"><span data-stu-id="2966b-288">The pointer to host name string in each entry points to the corresponding host name string in the bottom half of the buffer:</span></span>

![Содержит четыре записи NX_DNS_NS_ENTRY](media/image5.png)

<span data-ttu-id="2966b-290">Если во входном *record_buffer* невозможно сохранить все данные NS в ответе сервера, *record_buffer* будет содержать столько записей, сколько сможет, и возвратит это количество записей в буфере.</span><span class="sxs-lookup"><span data-stu-id="2966b-290">If the input *record_buffer* cannot hold all the NS data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="2966b-291">На основе числа записей NS, возвращенных в \**record_count*, приложение может проанализировать IP-адрес и имя узла каждой записи в *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="2966b-291">With the number of NS records returned in \**record_count,* the application can parse the IP address and host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2966b-292">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2966b-292">Input Parameters</span></span>

- <span data-ttu-id="2966b-293">**dns_ptr**: указатель на DNS-клиент</span><span class="sxs-lookup"><span data-stu-id="2966b-293">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="2966b-294">**host_name**: указатель на имя узла, для которого следует получить данные NS</span><span class="sxs-lookup"><span data-stu-id="2966b-294">**host_name** Pointer to host name to obtain NS data for</span></span>
- <span data-ttu-id="2966b-295">**record_buffer**: указатель на расположение, в которое следует извлечь данные NS</span><span class="sxs-lookup"><span data-stu-id="2966b-295">**record_buffer** Pointer to location to extract NS data into</span></span>
- <span data-ttu-id="2966b-296">**buffer_size**: размер буфера для хранения данных NS</span><span class="sxs-lookup"><span data-stu-id="2966b-296">**buffer_size** Size of buffer to hold NS data</span></span>
- <span data-ttu-id="2966b-297">**record_count**: указатель на количество полученных записей NS</span><span class="sxs-lookup"><span data-stu-id="2966b-297">**record_count** Pointer to the number of NS records retrieved</span></span>
- <span data-ttu-id="2966b-298">**wait_option**: параметр ожидания для получения ответа DNS-сервера</span><span class="sxs-lookup"><span data-stu-id="2966b-298">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="2966b-299">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2966b-299">Return Values</span></span>

- <span data-ttu-id="2966b-300">**NX_SUCCESS** (0x00) — данные NS успешно получены.</span><span class="sxs-lookup"><span data-stu-id="2966b-300">**NX_SUCCESS** (0x00) Successfully obtained NS data</span></span>
- <span data-ttu-id="2966b-301">**NX_DNS_NO_SERVER** (0xA1) — список серверов клиента пуст.</span><span class="sxs-lookup"><span data-stu-id="2966b-301">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="2966b-302">**NX_DNS_QUERY_FAILED** (0xA3) — не получен допустимый ответ DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-302">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="2966b-303">NX_DNS_PARAM_ERROR (0xA8) — недопустимые входные данные без указателя.</span><span class="sxs-lookup"><span data-stu-id="2966b-303">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="2966b-304">NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-304">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="2966b-305">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="2966b-305">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2966b-306">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2966b-306">Allowed From</span></span>

<span data-ttu-id="2966b-307">Потоки</span><span class="sxs-lookup"><span data-stu-id="2966b-307">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2966b-308">Пример</span><span class="sxs-lookup"><span data-stu-id="2966b-308">Example</span></span>
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

## <a name="nx_dns_domain_mail_exchange_get"></a><span data-ttu-id="2966b-309">nx_dns_domain_mail_exchange_get</span><span class="sxs-lookup"><span data-stu-id="2966b-309">nx_dns_domain_mail_exchange_get</span></span>

<span data-ttu-id="2966b-310">Поиск обмена почтой для входного имени узла</span><span class="sxs-lookup"><span data-stu-id="2966b-310">Look up the mail exchange(s) for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="2966b-311">Прототип</span><span class="sxs-lookup"><span data-stu-id="2966b-311">Prototype</span></span>
```C
UINT nx_dns_domain_mail_exchange_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                     VOID *record_buffer,                                        
                                     UINT buffer_size, 
                                     UINT *record_count, 
                                     ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="2966b-312">Описание</span><span class="sxs-lookup"><span data-stu-id="2966b-312">Description</span></span>

<span data-ttu-id="2966b-313">Если параметр NX_DNS_ENABLE_EXTENDED_RR_TYPES определен, эта служба отправляет запрос типа MX с указанным доменным именем, чтобы получить обмен почтой для входного имени домена.</span><span class="sxs-lookup"><span data-stu-id="2966b-313">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type MX with the specified domain name to obtain the mail exchange for the input domain name.</span></span> <span data-ttu-id="2966b-314">DNS-клиент копирует записи MX, возвращенные в ответе DNS-сервера, по адресу памяти *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="2966b-314">The DNS Client copies the MX record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

> [!NOTE]
> <span data-ttu-id="2966b-315">Для получения данных *record_buffer* должен быть выровнен по 4 байт.</span><span class="sxs-lookup"><span data-stu-id="2966b-315">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="2966b-316">В DNS-клиенте для NetX Duo тип записи обмена почтой (NX_DNS_MAIL_EXCHANGE_ENTRY) сохраняется как четыре параметра общим размером 12 байт.</span><span class="sxs-lookup"><span data-stu-id="2966b-316">In NetX Duo DNS Client, the mail exchange record type, NX_DNS_MAIL_EXCHANGE_ENTRY, is saved as four parameters, totaling 12 bytes:</span></span>

- <span data-ttu-id="2966b-317">**nx_dns_mx_ipv4_address**: IPv4 адрес обмена почтой, 4 байт</span><span class="sxs-lookup"><span data-stu-id="2966b-317">**nx_dns_mx_ipv4_address** Mail exchange IPv4 address 4 bytes</span></span>
- <span data-ttu-id="2966b-318">**nx_dns_mx_preference**: предпочтение, 2 байт</span><span class="sxs-lookup"><span data-stu-id="2966b-318">**nx_dns_mx_preference** Preference 2 bytes</span></span>
- <span data-ttu-id="2966b-319">**nx_dns_mx_reserved0**: зарезервировано, 2 байт</span><span class="sxs-lookup"><span data-stu-id="2966b-319">**nx_dns_mx_reserved0** Reserved 2 bytes</span></span>
- <span data-ttu-id="2966b-320">**nx_dns_mx_hostname_ptr**: указатель на имя узла сервера обмена почтой, 4 байт</span><span class="sxs-lookup"><span data-stu-id="2966b-320">**nx_dns_mx_hostname_ptr** Pointer to mail exchange server host name 4 bytes</span></span>

<span data-ttu-id="2966b-321">Ниже показан буфер, содержащий четыре записи MX.</span><span class="sxs-lookup"><span data-stu-id="2966b-321">A buffer containing four MX records is shown below.</span></span> <span data-ttu-id="2966b-322">Каждая запись содержит данные фиксированной длины из приведенного выше списка.</span><span class="sxs-lookup"><span data-stu-id="2966b-322">Each record contains the fixed length data from the list above.</span></span> <span data-ttu-id="2966b-323">Указатель на имя узла сервера обмена почтой указывает на соответствующее имя узла в нижней части буфера.</span><span class="sxs-lookup"><span data-stu-id="2966b-323">The pointer to the mail exchange server host name points to the corresponding host name at the bottom of the buffer.</span></span>

![Буфер, содержащий четыре записи MX](media/image6.png)

<span data-ttu-id="2966b-325">Если во входном *record_buffer* невозможно сохранить все данные MX в ответе сервера, *record_buffer* будет содержать столько записей, сколько сможет, и возвратит это количество записей в буфере.</span><span class="sxs-lookup"><span data-stu-id="2966b-325">If the input *record_buffer* cannot hold all the MX data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="2966b-326">На основе числа записей MX, возвращенных в \**record_count*, приложение может проанализировать параметры MX, включая имя узла почты каждой записи в *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="2966b-326">With the number of MX records returned in \**record_count,* the application can parse the MX parameters, including the mail host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2966b-327">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2966b-327">Input Parameters</span></span>

- <span data-ttu-id="2966b-328">**dns_ptr**: указатель на DNS-клиент</span><span class="sxs-lookup"><span data-stu-id="2966b-328">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="2966b-329">**host_name**: указатель на имя узла, для которого следует получить данные MX</span><span class="sxs-lookup"><span data-stu-id="2966b-329">**host_name** Pointer to host name to obtain MX data for</span></span>
- <span data-ttu-id="2966b-330">**record_buffer**: указатель на расположение, в которое следует извлечь данные MX</span><span class="sxs-lookup"><span data-stu-id="2966b-330">**record_buffer** Pointer to location to extract MX data into</span></span>
- <span data-ttu-id="2966b-331">**buffer_size**: размер буфера для хранения данных MX</span><span class="sxs-lookup"><span data-stu-id="2966b-331">**buffer_size** Size of buffer to hold MX data</span></span>
- <span data-ttu-id="2966b-332">**record_count**: указатель на количество полученных записей MX</span><span class="sxs-lookup"><span data-stu-id="2966b-332">**record_count** Pointer to the number of MX records retrieved</span></span>
- <span data-ttu-id="2966b-333">**wait_option**: параметр ожидания для получения ответа DNS-сервера</span><span class="sxs-lookup"><span data-stu-id="2966b-333">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="2966b-334">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2966b-334">Return Values</span></span>

- <span data-ttu-id="2966b-335">**NX_SUCCESS** (0x00) — данные MX успешно получены.</span><span class="sxs-lookup"><span data-stu-id="2966b-335">**NX_SUCCESS** (0x00) Successfully obtained MX data</span></span>
- <span data-ttu-id="2966b-336">**NX_DNS_NO_SERVER** (0xA1) — список серверов клиента пуст.</span><span class="sxs-lookup"><span data-stu-id="2966b-336">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="2966b-337">**NX_DNS_QUERY_FAILED** (0xA3) — не получен допустимый ответ DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-337">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="2966b-338">NX_DNS_PARAM_ERROR (0xA8) — недопустимые входные данные без указателя.</span><span class="sxs-lookup"><span data-stu-id="2966b-338">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="2966b-339">NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-339">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="2966b-340">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="2966b-340">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2966b-341">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2966b-341">Allowed From</span></span>

<span data-ttu-id="2966b-342">Потоки</span><span class="sxs-lookup"><span data-stu-id="2966b-342">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2966b-343">Пример</span><span class="sxs-lookup"><span data-stu-id="2966b-343">Example</span></span>
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

## <a name="nx_dns_domain_service_get"></a><span data-ttu-id="2966b-344">nx_dns_domain_service_get</span><span class="sxs-lookup"><span data-stu-id="2966b-344">nx_dns_domain_service_get</span></span>

<span data-ttu-id="2966b-345">Поиск служб, предоставляемых по входному имени узла.</span><span class="sxs-lookup"><span data-stu-id="2966b-345">Look up the service(s) provided by the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="2966b-346">Прототип</span><span class="sxs-lookup"><span data-stu-id="2966b-346">Prototype</span></span>
```C
UINT nx_dns_domain_service_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                VOID *record_buffer, UINT buffer_size, 
                                UINT *record_count, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="2966b-347">Описание</span><span class="sxs-lookup"><span data-stu-id="2966b-347">Description</span></span>

<span data-ttu-id="2966b-348">Если параметр NX_DNS_ENABLE_EXTENDED_RR_TYPES определен, эта служба отправляет запрос типа SRV с указанным доменным именем для поиска служб и их номеров портов, связанных с указанным доменом.</span><span class="sxs-lookup"><span data-stu-id="2966b-348">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type SRV with the specified domain name to look up the service(s) and their port number associated with the specified domain.</span></span> <span data-ttu-id="2966b-349">DNS-клиент копирует записи SRV, возвращенные в ответе DNS-сервера, по адресу памяти *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="2966b-349">The DNS Client copies the SRV record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

> [!NOTE]
> <span data-ttu-id="2966b-350">Для получения данных *record_buffer* должен быть выровнен по 4 байт.</span><span class="sxs-lookup"><span data-stu-id="2966b-350">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="2966b-351">В DNS-клиенте для NetX Duo тип записи службы (NX_DNS_SRV_ENTRY) сохраняется в виде шести параметров общим размером 16 байт.</span><span class="sxs-lookup"><span data-stu-id="2966b-351">In NetX Duo DNS Client, the service record type, NX_DNS_SRV_ ENTRY, is saved as six parameters, totaling 16 bytes.</span></span> <span data-ttu-id="2966b-352">Это позволяет эффективно хранить данные SRV переменной длины в памяти.</span><span class="sxs-lookup"><span data-stu-id="2966b-352">This enables variable length SRV data to be stored in a memory efficient manner:</span></span>

- <span data-ttu-id="2966b-353">**nx_dns_srv_ipv4_address**: IPv4-адрес сервера, 4 байт</span><span class="sxs-lookup"><span data-stu-id="2966b-353">**Server IPv4 address** nx_dns_srv_ipv4_address 4 bytes</span></span>
- <span data-ttu-id="2966b-354">**nx_dns_srv_priority**: приоритет сервера, 2 байт</span><span class="sxs-lookup"><span data-stu-id="2966b-354">**Server priority** nx_dns_srv_priority 2 bytes</span></span>
- <span data-ttu-id="2966b-355">**nx_dns_srv_weight**: вес сервера, 2 байт</span><span class="sxs-lookup"><span data-stu-id="2966b-355">**Server weight** nx_dns_srv_weight 2 bytes</span></span>
- <span data-ttu-id="2966b-356">**nx_dns_srv_port_number**: номер порта службы, 2 байт</span><span class="sxs-lookup"><span data-stu-id="2966b-356">**Service port number** nx_dns_srv_port_number 2 bytes</span></span>
- <span data-ttu-id="2966b-357">**nx_dns_srv_reserved0**: зарезервировано для выравнивания по 4 байт, 2 байт</span><span class="sxs-lookup"><span data-stu-id="2966b-357">**Reserved for 4-byte alignment** nx_dns_srv_reserved0 2 bytes</span></span>
- <span data-ttu-id="2966b-358">\***nx_dns_srv_hostname_ptr**: указатель на имя узла сервера, 4 байт</span><span class="sxs-lookup"><span data-stu-id="2966b-358">**Pointer to server host name** \*nx_dns_srv_hostname_ptr 4 bytes</span></span>

<span data-ttu-id="2966b-359">В заданном буфере хранятся четыре записи SRV.</span><span class="sxs-lookup"><span data-stu-id="2966b-359">Four SRV records are stored in the supplied buffer.</span></span> <span data-ttu-id="2966b-360">Каждая запись NX_DNS_SRV_ENTRY содержит указатель, *nx_dns_srv_hostname_ptr*, указывающий на соответствующую строку имени узла в нижней части буфера записей.</span><span class="sxs-lookup"><span data-stu-id="2966b-360">Each NX_DNS_SRV_ENTRY record contains a pointer, *nx_dns_srv_hostname_ptr*, that points to the corresponding host name string in the bottom of the record buffer:</span></span>

![Четыре записи SRV](media/image7.png)

<span data-ttu-id="2966b-362">Если во входном *record_buffer* невозможно сохранить все данные SRV в ответе сервера, *record_buffer* будет содержать столько записей, сколько сможет, и возвратит это количество записей в буфере.</span><span class="sxs-lookup"><span data-stu-id="2966b-362">If the input *record_buffer* cannot hold all the SRV data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="2966b-363">На основе числа записей SRV, возвращенных в \**record_count*, приложение может проанализировать параметры SRV, включая имя узла сервера каждой записи в *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="2966b-363">With the number of SRV records returned in \**record_count,* the application can parse the SRV parameters, including the server host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2966b-364">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2966b-364">Input Parameters</span></span>

- <span data-ttu-id="2966b-365">**dns_ptr**: указатель на DNS-клиент</span><span class="sxs-lookup"><span data-stu-id="2966b-365">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="2966b-366">**host_name**: указатель на имя узла, для которого следует получить данные SRV</span><span class="sxs-lookup"><span data-stu-id="2966b-366">**host_name** Pointer to host name to obtain SRV data for</span></span>
- <span data-ttu-id="2966b-367">**record_buffer**: указатель на расположение, в которое следует извлечь данные SRV</span><span class="sxs-lookup"><span data-stu-id="2966b-367">**record_buffer** Pointer to location to extract SRV data into</span></span>
- <span data-ttu-id="2966b-368">**buffer_size**: размер буфера для хранения данных SRV</span><span class="sxs-lookup"><span data-stu-id="2966b-368">**buffer_size** Size of buffer to hold SRV data</span></span>
- <span data-ttu-id="2966b-369">**record_count**: указатель на количество полученных записей SRV</span><span class="sxs-lookup"><span data-stu-id="2966b-369">**record_count** Pointer to the number of SRV records retrieved</span></span>
- <span data-ttu-id="2966b-370">**wait_option**: параметр ожидания для получения ответа DNS-сервера</span><span class="sxs-lookup"><span data-stu-id="2966b-370">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="2966b-371">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2966b-371">Return Values</span></span>

- <span data-ttu-id="2966b-372">**NX_SUCCESS** (0x00) — данные SRV успешно получены.</span><span class="sxs-lookup"><span data-stu-id="2966b-372">**NX_SUCCESS** (0x00) Successfully obtained SRV data</span></span>
- <span data-ttu-id="2966b-373">**NX_DNS_NO_SERVER** (0xA1) — список серверов клиента пуст.</span><span class="sxs-lookup"><span data-stu-id="2966b-373">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="2966b-374">**NX_DNS_QUERY_FAILED** (0xA3) — не получен допустимый ответ DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-374">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="2966b-375">NX_DNS_PARAM_ERROR (0xA8) — недопустимый параметр без указателя.</span><span class="sxs-lookup"><span data-stu-id="2966b-375">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer parameter.</span></span>
- <span data-ttu-id="2966b-376">NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-376">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="2966b-377">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="2966b-377">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2966b-378">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2966b-378">Allowed From</span></span>

<span data-ttu-id="2966b-379">Потоки</span><span class="sxs-lookup"><span data-stu-id="2966b-379">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2966b-380">Пример</span><span class="sxs-lookup"><span data-stu-id="2966b-380">Example</span></span>
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

## <a name="nx_dns_get_serverlist_size"></a><span data-ttu-id="2966b-381">nx_dns_get_serverlist_size</span><span class="sxs-lookup"><span data-stu-id="2966b-381">nx_dns_get_serverlist_size</span></span>

<span data-ttu-id="2966b-382">Возврат размера списка серверов DNS-клиента.</span><span class="sxs-lookup"><span data-stu-id="2966b-382">Return the size of the DNS Client’s Server list</span></span>

### <a name="prototype"></a><span data-ttu-id="2966b-383">Прототип</span><span class="sxs-lookup"><span data-stu-id="2966b-383">Prototype</span></span>
```C
UINT nx_dns_get_serverlist_size (NX_DNS *dns_ptr, UINT *size);
```
### <a name="description"></a><span data-ttu-id="2966b-384">Описание</span><span class="sxs-lookup"><span data-stu-id="2966b-384">Description</span></span>

<span data-ttu-id="2966b-385">Эта служба возвращает количество допустимых DNS-серверов (IPv4 и IPv6) в списке клиента.</span><span class="sxs-lookup"><span data-stu-id="2966b-385">This service returns the number of valid DNS Servers (both IPv4 and IPv6) in the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2966b-386">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2966b-386">Input Parameters</span></span>

- <span data-ttu-id="2966b-387">**dns_ptr**: указатель на блок управления DNS</span><span class="sxs-lookup"><span data-stu-id="2966b-387">**dns_ptr** Pointer to DNS control block</span></span>  
- <span data-ttu-id="2966b-388">**size** возвращает количество серверов в списке</span><span class="sxs-lookup"><span data-stu-id="2966b-388">**size** Returns the number of servers in the list</span></span>

### <a name="return-values"></a><span data-ttu-id="2966b-389">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2966b-389">Return Values</span></span>

- <span data-ttu-id="2966b-390">**NX_SUCCESS** (0x00) — размер списка DNS-серверов успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="2966b-390">**NX_SUCCESS** (0x00) DNS Server list size successfully returned</span></span>
- <span data-ttu-id="2966b-391">NX_PTR_ERROR (0x07) — недопустимый указатель IP-адреса или DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-391">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="2966b-392">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="2966b-392">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2966b-393">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2966b-393">Allowed From</span></span>

<span data-ttu-id="2966b-394">Потоки</span><span class="sxs-lookup"><span data-stu-id="2966b-394">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2966b-395">Пример</span><span class="sxs-lookup"><span data-stu-id="2966b-395">Example</span></span>
```C
UINT my_listsize;

/* Get the number of non null DNS Servers in the Client list. */
status =  nx_dns_get_serverlist_size (&my_dns, 5, &my_listsize);

/* If status is NX_SUCCESS the size of the DNS Server list was successfully
   returned. */
```

## <a name="nx_dns_info_by_name_get"></a><span data-ttu-id="2966b-396">nx_dns_info_by_name_get</span><span class="sxs-lookup"><span data-stu-id="2966b-396">nx_dns_info_by_name_get</span></span>

<span data-ttu-id="2966b-397">Возврат IP-адреса и порта DNS-сервера по имени узла</span><span class="sxs-lookup"><span data-stu-id="2966b-397">Return ip address and port of DNS server by host name</span></span>

### <a name="prototype"></a><span data-ttu-id="2966b-398">Прототип</span><span class="sxs-lookup"><span data-stu-id="2966b-398">Prototype</span></span>
```C
UINT nx_dns_info_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr,  
                             USHORT *host_port_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="2966b-399">Описание</span><span class="sxs-lookup"><span data-stu-id="2966b-399">Description</span></span>

<span data-ttu-id="2966b-400">Эта служба возвращает IP-адрес и порт сервера (запись службы) на основе входного имени узла по запросу DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-400">This service returns the Server IP and port (service record) based on the input host name by DNS query.</span></span> <span data-ttu-id="2966b-401">Если запись службы не найдена, эта подпрограмма возвращает нулевой IP-адрес в указателе на входной адрес и ненулевое состояние ошибки, информирующее о возникновении ошибки.</span><span class="sxs-lookup"><span data-stu-id="2966b-401">If a service record is not found, this routine returns a zero IP address in the input address pointer and a non-zero error status return to signal an error.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2966b-402">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2966b-402">Input Parameters</span></span>

- <span data-ttu-id="2966b-403">**dns_ptr**: указатель на блок управления DNS</span><span class="sxs-lookup"><span data-stu-id="2966b-403">**dns_ptr** Pointer to DNS control block</span></span>  
- <span data-ttu-id="2966b-404">**host_name**: указатель на буфер имени узла</span><span class="sxs-lookup"><span data-stu-id="2966b-404">**host_name** Pointer to host name buffer</span></span>
- <span data-ttu-id="2966b-405">**host_address_ptr**: указатель на возвращаемый адрес</span><span class="sxs-lookup"><span data-stu-id="2966b-405">**host_address_ptr** Pointer to address to return</span></span>
- <span data-ttu-id="2966b-406">**host_port_ptr**: указатель на возвращаемый порт</span><span class="sxs-lookup"><span data-stu-id="2966b-406">**host_port_ptr** Pointer to port to return</span></span>
- <span data-ttu-id="2966b-407">**wait_option**: параметр ожидания ответа DNS</span><span class="sxs-lookup"><span data-stu-id="2966b-407">**wait_option** Wait option for the DNS response</span></span>

### <a name="return-values"></a><span data-ttu-id="2966b-408">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2966b-408">Return Values</span></span>

- <span data-ttu-id="2966b-409">**NX_SUCCESS** (0x00) — запись DNS-сервера успешно возвращена.</span><span class="sxs-lookup"><span data-stu-id="2966b-409">**NX_SUCCESS** (0x00) DNS Server record successfully returned</span></span>
- <span data-ttu-id="2966b-410">**NX_DNS_NO_SERVER** (0xA1) — DNS-сервер не зарегистрирован в клиенте для отправки запроса по имени узла.</span><span class="sxs-lookup"><span data-stu-id="2966b-410">**NX_DNS_NO_SERVER** (0xA1) No DNS Server registered with Client to send query on hostname</span></span>
- <span data-ttu-id="2966b-411">**NX_DNS_QUERY_FAILED** (0xA3) — не удалось выполнить запрос DNS. Ответ от DNS-серверов в списке клиента не получен, или нет доступных записей службы для входного имени узла.</span><span class="sxs-lookup"><span data-stu-id="2966b-411">**NX_DNS_QUERY_FAILED** (0xA3) DNS query failed; no response from any DNS servers in Client list or no service record is available for the input hostname.</span></span>
- <span data-ttu-id="2966b-412">NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-412">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="2966b-413">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект.</span><span class="sxs-lookup"><span data-stu-id="2966b-413">NX_CALLER_ERROR (0x11) Invalid caller</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2966b-414">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2966b-414">Allowed From</span></span>

<span data-ttu-id="2966b-415">Потоки</span><span class="sxs-lookup"><span data-stu-id="2966b-415">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2966b-416">Пример</span><span class="sxs-lookup"><span data-stu-id="2966b-416">Example</span></span>
```C
ULONG ip_address
USHORT port;

/* Attempt to resolve the IP address and ports for this host name. */
status =  nx_dns_info_by_name_get(&my_dns, “www.abc1234.com”, &ip_address, &port, 200);

/* If status is NX_SUCCESS the DNS query was successful and the IP address and
   report for the hostname are returned. */
```

## <a name="nx_dns_ipv4_address_by_name_get"></a><span data-ttu-id="2966b-417">nx_dns_ipv4_address_by_name_get</span><span class="sxs-lookup"><span data-stu-id="2966b-417">nx_dns_ipv4_address_by_name_get</span></span>

<span data-ttu-id="2966b-418">Поиск IPv4-адреса для входного имени узла.</span><span class="sxs-lookup"><span data-stu-id="2966b-418">Look up the IPv4 address for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="2966b-419">Прототип</span><span class="sxs-lookup"><span data-stu-id="2966b-419">Prototype</span></span>
```C
UINT nx_ dns_ipv4_address_by_name_get (NX_DNS *dns_ptr, 
                                      UCHAR *host_name_ptr, VOID *buffer, 
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="2966b-420">Описание</span><span class="sxs-lookup"><span data-stu-id="2966b-420">Description</span></span>

<span data-ttu-id="2966b-421">Эта служба отправляет запрос типа A с указанным именем узла, чтобы получить IP-адреса для входного имени узла.</span><span class="sxs-lookup"><span data-stu-id="2966b-421">This service sends a query of Type A with the specified host name to obtain the IP addresses for the input host name.</span></span> <span data-ttu-id="2966b-422">DNS-клиент копирует IPv4-адреса из записей A, возвращенных в ответе DNS-сервера, по адресу памяти *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="2966b-422">The DNS Client copies the IPv4 address from the A record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span>

> [!NOTE]
> <span data-ttu-id="2966b-423">Для получения данных *record_buffer* должен быть выровнен по 4 байт.</span><span class="sxs-lookup"><span data-stu-id="2966b-423">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="2966b-424">В буфере, выровненном по 4 байт, хранится несколько IPv4-адресов, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="2966b-424">Multiple IPv4 addresses are stored in the 4-byte aligned buffer as shown below:</span></span>

![Выровненный по 4 байт буфер с несколькими адресами](media/image8.png)

<span data-ttu-id="2966b-426">Если указанный буфер не может содержать все данные IP-адреса, оставшиеся записи A не сохраняются в *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="2966b-426">If the supplied buffer cannot hold all the IP address data, the remaining A records are not stored in *record_buffer*.</span></span> <span data-ttu-id="2966b-427">Это позволяет приложению получить данные одного, нескольких или всех доступных IP-адресов в ответе сервера.</span><span class="sxs-lookup"><span data-stu-id="2966b-427">This enables the application to retrieve one, some or all of the available IP address data in the server reply.</span></span>

<span data-ttu-id="2966b-428">На основе числа записей A, возвращенных в \**record_count*, приложение может проанализировать данные IPv4-адреса из *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="2966b-428">With the number of A records returned in \**record_count* the application can parse the IPv4 address data from the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2966b-429">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2966b-429">Input Parameters</span></span>

- <span data-ttu-id="2966b-430">**dns_ptr**: указатель на DNS-клиент</span><span class="sxs-lookup"><span data-stu-id="2966b-430">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="2966b-431">**host_name_ptr**: указатель на имя узла для получения IPv4-адреса</span><span class="sxs-lookup"><span data-stu-id="2966b-431">**host_name_ptr** Pointer to host name to obtain IPv4 address</span></span>
- <span data-ttu-id="2966b-432">**buffer**: указатель на расположение, в которое следует извлечь данные IPv4</span><span class="sxs-lookup"><span data-stu-id="2966b-432">**buffer** Pointer to location to extract IPv4 data into</span></span>
- <span data-ttu-id="2966b-433">**buffer_size**: размер буфера для хранения данных IPv4</span><span class="sxs-lookup"><span data-stu-id="2966b-433">**buffer_size** Size of buffer to hold IPv4 data</span></span>
- <span data-ttu-id="2966b-434">**wait_option**: параметр ожидания для получения ответа DNS-сервера</span><span class="sxs-lookup"><span data-stu-id="2966b-434">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="2966b-435">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2966b-435">Return Values</span></span>

- <span data-ttu-id="2966b-436">**NX_SUCCESS** (0x00) — данные IPv4-адреса успешно получены.</span><span class="sxs-lookup"><span data-stu-id="2966b-436">**NX_SUCCESS** (0x00) Successfully obtained IPv4 data</span></span>
- <span data-ttu-id="2966b-437">**NX_DNS_NO_SERVER** (0xA1) — список серверов клиента пуст.</span><span class="sxs-lookup"><span data-stu-id="2966b-437">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="2966b-438">**NX_DNS_QUERY_FAILED** (0xA3) — не получен допустимый ответ DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-438">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="2966b-439">NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-439">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="2966b-440">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="2966b-440">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="2966b-441">NX_DNS_PARAM_ERROR (0xA8) — недопустимый параметр без указателя.</span><span class="sxs-lookup"><span data-stu-id="2966b-441">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2966b-442">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2966b-442">Allowed From</span></span>

<span data-ttu-id="2966b-443">Потоки</span><span class="sxs-lookup"><span data-stu-id="2966b-443">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2966b-444">Пример</span><span class="sxs-lookup"><span data-stu-id="2966b-444">Example</span></span>
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

## <a name="nxd_dns_ipv6_address_by_name_get"></a><span data-ttu-id="2966b-445">nxd_dns_ipv6_address_by_name_get</span><span class="sxs-lookup"><span data-stu-id="2966b-445">nxd_dns_ipv6_address_by_name_get</span></span>

<span data-ttu-id="2966b-446">Поиск IPv6-адреса для входного имени узла</span><span class="sxs-lookup"><span data-stu-id="2966b-446">Look up the IPv6 address for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="2966b-447">Прототип</span><span class="sxs-lookup"><span data-stu-id="2966b-447">Prototype</span></span>
```C
UINT nxd_ dns_ipv6_address_by_name_get(NX_DNS *dns_ptr, 
                                      UCHAR *host_name_ptr, VOID *buffer, 
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="2966b-448">Описание</span><span class="sxs-lookup"><span data-stu-id="2966b-448">Description</span></span>

<span data-ttu-id="2966b-449">Эта служба отправляет запрос типа AAAA с указанным доменным именем, чтобы получить IP-адреса для входного доменного имени.</span><span class="sxs-lookup"><span data-stu-id="2966b-449">This service sends a query of type AAAA with the specified domain name to obtain the IP addresses for the input domain name.</span></span> <span data-ttu-id="2966b-450">DNS-клиент копирует IPv6-адреса из записей AAAA, возвращенных в ответе DNS-сервера, по адресу памяти *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="2966b-450">The DNS Client copies the IPv6 address from the AAAA record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

> [!NOTE]
> <span data-ttu-id="2966b-451">Для получения данных *record_buffer* должен быть выровнен по 4 байт.</span><span class="sxs-lookup"><span data-stu-id="2966b-451">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="2966b-452">Ниже показан формат IPv6-адресов, хранящихся в буфере, выровненном по 4 байт.</span><span class="sxs-lookup"><span data-stu-id="2966b-452">The format of IPv6 addresses stored in the 4-byte aligned buffer is shown below:</span></span>

![Выровненный по 4 байт буфер формата IPv6](media/image9.png)

<span data-ttu-id="2966b-454">Если во входном *record_buffer* невозможно сохранить все данные AAAA в ответе сервера, *record_buffer* будет содержать столько записей, сколько сможет, и возвратит это количество записей в буфере.</span><span class="sxs-lookup"><span data-stu-id="2966b-454">If the input *record_buffer* cannot hold all the AAAA data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="2966b-455">На основе числа записей AAAA, возвращенных в \**record_count*, приложение может проанализировать IPv6-адреса из каждой записи в *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="2966b-455">With the number of AAAA records returned in \**record_count,* the application can parse the IPv6 addresses from each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2966b-456">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2966b-456">Input Parameters</span></span>

- <span data-ttu-id="2966b-457">**dns_ptr**: указатель на DNS-клиент</span><span class="sxs-lookup"><span data-stu-id="2966b-457">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="2966b-458">**host_name_ptr**: указатель на имя узла для получения IPv6-адреса</span><span class="sxs-lookup"><span data-stu-id="2966b-458">**host_name_ptr** Pointer to host name to obtain IPv6 address</span></span>
- <span data-ttu-id="2966b-459">**buffer**: указатель на расположение, в которое следует извлечь данные IPv6</span><span class="sxs-lookup"><span data-stu-id="2966b-459">**buffer** Pointer to location to extract IPv6 data into</span></span>
- <span data-ttu-id="2966b-460">**buffer_size**: размер буфера для хранения данных IPv6</span><span class="sxs-lookup"><span data-stu-id="2966b-460">**buffer_size** Size of buffer to hold IPv6 data</span></span>
- <span data-ttu-id="2966b-461">**wait_option**: параметр ожидания для получения ответа DNS-сервера</span><span class="sxs-lookup"><span data-stu-id="2966b-461">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="2966b-462">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2966b-462">Return Values</span></span>

- <span data-ttu-id="2966b-463">**NX_SUCCESS** (0x00) — данные IPv6-адреса успешно получены.</span><span class="sxs-lookup"><span data-stu-id="2966b-463">**NX_SUCCESS** (0x00) Successfully obtained IPv6 data</span></span>
- <span data-ttu-id="2966b-464">**NX_DNS_NO_SERVER** (0xA1) — список серверов клиента пуст.</span><span class="sxs-lookup"><span data-stu-id="2966b-464">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="2966b-465">**NX_DNS_QUERY_FAILED** (0xA3) — не получен допустимый ответ DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-465">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="2966b-466">NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-466">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="2966b-467">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="2966b-467">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="2966b-468">NX_DNS_PARAM_ERROR (0xA8) — недопустимый параметр без указателя.</span><span class="sxs-lookup"><span data-stu-id="2966b-468">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2966b-469">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2966b-469">Allowed From</span></span>

<span data-ttu-id="2966b-470">Потоки</span><span class="sxs-lookup"><span data-stu-id="2966b-470">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2966b-471">Пример</span><span class="sxs-lookup"><span data-stu-id="2966b-471">Example</span></span>
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

## <a name="nx_dns_host_by_address_get"></a><span data-ttu-id="2966b-472">nx_dns_host_by_address_get</span><span class="sxs-lookup"><span data-stu-id="2966b-472">nx_dns_host_by_address_get</span></span>

<span data-ttu-id="2966b-473">Поиск имени узла по IP-адресу</span><span class="sxs-lookup"><span data-stu-id="2966b-473">Look up a host name from an IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="2966b-474">Прототип</span><span class="sxs-lookup"><span data-stu-id="2966b-474">Prototype</span></span>
```C
UINT nx_dns_host_by_address_get(NX_DNS *dns_ptr, ULONG ip_address, 
                                ULONG *host_name_ptr, 
                                ULONG max_host_name_size, 
                                ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="2966b-475">Описание</span><span class="sxs-lookup"><span data-stu-id="2966b-475">Description</span></span>

<span data-ttu-id="2966b-476">Эта служба запрашивает разрешение имен для указанного IP-адреса с одного DNS-сервера или нескольких, ранее указанных приложением.</span><span class="sxs-lookup"><span data-stu-id="2966b-476">This service requests name resolution of the supplied IP address from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="2966b-477">В случае успешного выполнения возвращается имя узла, оканчивающееся символом NULL, в строке, заданной *host_name_ptr*.</span><span class="sxs-lookup"><span data-stu-id="2966b-477">If successful, the NULL-terminated host name is returned in the string specified by *host_name_ptr*.</span></span> <span data-ttu-id="2966b-478">Это функция-оболочка для службы *nxd_dns_host_by_address_get*, и она не принимает IPv6-адреса.</span><span class="sxs-lookup"><span data-stu-id="2966b-478">This is a wrapper function for *nxd_dns_host_by_address_get* service and does not accept IPv6 addresses.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2966b-479">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2966b-479">Input Parameters</span></span>

- <span data-ttu-id="2966b-480">**dns_ptr**: указатель на ранее созданный экземпляр DNS</span><span class="sxs-lookup"><span data-stu-id="2966b-480">**dns_ptr** Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="2966b-481">**ip_address**: IP-адрес для разрешения в имя</span><span class="sxs-lookup"><span data-stu-id="2966b-481">**ip_address** IP address to resolve into a name</span></span>
- <span data-ttu-id="2966b-482">**host_name_ptr**: указатель на область назначения для имени узла</span><span class="sxs-lookup"><span data-stu-id="2966b-482">**host_name_ptr** Pointer to destination area for host name</span></span>
- <span data-ttu-id="2966b-483">**max_host_name_size**: размер области назначения для имени узла</span><span class="sxs-lookup"><span data-stu-id="2966b-483">**max_host_name_size** Size of destination area for host name</span></span>
- <span data-ttu-id="2966b-484">**wait_option**: определяет, как долго служба будет ожидать (в тактах таймера) ответ DNS-сервера после каждого запроса DNS и повторных попыток выполнения запроса</span><span class="sxs-lookup"><span data-stu-id="2966b-484">**wait_option** Defines how long the service will wait in timer ticks for a DNS server response after each DNS query and query retry.</span></span> <span data-ttu-id="2966b-485">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="2966b-485">The wait options are defined as follows:</span></span>

  <span data-ttu-id="2966b-486">Значение времени ожидания (0x00000001–0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="2966b-486">timeout value (0x00000001-0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span></span>

  <span data-ttu-id="2966b-487">Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока DNS-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="2966b-487">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

  <span data-ttu-id="2966b-488">Числовое значение (1–0xFFFFFFFE) определяет максимальное количество тактов таймера, чтобы оставаться в состоянии приостановки во время ожидания разрешения DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-488">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>

### <a name="return-values"></a><span data-ttu-id="2966b-489">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2966b-489">Return Values</span></span>

- <span data-ttu-id="2966b-490">**NX_SUCCESS** (0x00) — разрешение DNS успешно выполнено.</span><span class="sxs-lookup"><span data-stu-id="2966b-490">**NX_SUCCESS** (0x00) Successful DNS resolution</span></span>  
- <span data-ttu-id="2966b-491">**NX_DNS_TIMEOUT** (0xA2) — истекло время ожидания при получении мьютекса DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-491">**NX_DNS_TIMEOUT** (0xA2) Timed out on obtaining DNS mutex</span></span>
- <span data-ttu-id="2966b-492">**NX_DNS_NO_SERVER** (0xA1) — не указан адрес DNS-сервера.</span><span class="sxs-lookup"><span data-stu-id="2966b-492">**NX_DNS_NO_SERVER** (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="2966b-493">**NX_DNS_QUERY_FAILED** (0xA3) — не получен ответ на запрос.</span><span class="sxs-lookup"><span data-stu-id="2966b-493">**NX_DNS_QUERY_FAILED** (0xA3) Received no response to query</span></span>
- <span data-ttu-id="2966b-494">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) — входной адрес имеет значение NULL.</span><span class="sxs-lookup"><span data-stu-id="2966b-494">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null input address</span></span>
- <span data-ttu-id="2966b-495">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) — индекс указывает на недопустимый тип адреса (например, IPv6).</span><span class="sxs-lookup"><span data-stu-id="2966b-495">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>
- <span data-ttu-id="2966b-496">**NX_DNS_PARAM_ERROR** (0xA8) — недопустимые входные данные без указателя.</span><span class="sxs-lookup"><span data-stu-id="2966b-496">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="2966b-497">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) — не удается обработать запись с отключенным IPv6.</span><span class="sxs-lookup"><span data-stu-id="2966b-497">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="2966b-498">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="2966b-498">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="2966b-499">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="2966b-499">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2966b-500">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2966b-500">Allowed From</span></span>

<span data-ttu-id="2966b-501">Потоки</span><span class="sxs-lookup"><span data-stu-id="2966b-501">Threads</span></span>

<span data-ttu-id="2966b-502">**Пример**</span><span class="sxs-lookup"><span data-stu-id="2966b-502">**Example**</span></span>
```C
#define BUFFER_SIZE   200

UCHAR   resolved_name[200];

/* Get the name associated with IP address 192.2.2.10.  */
status =  nx_dns_host_by_address_get(&my_dns, IP_ADDRESS(192.2.2.10),
                                     &resolved_name[0], BUFFER_SIZE, 450);

/* If status is NX_SUCCESS the name associated with the IP address
   can be found in the resolved_name variable.  */
```

## <a name="nxd_dns_host_by_address_get"></a><span data-ttu-id="2966b-503">nxd_dns_host_by_address_get</span><span class="sxs-lookup"><span data-stu-id="2966b-503">nxd_dns_host_by_address_get</span></span>

<span data-ttu-id="2966b-504">Поиск имени узла по IP-адресу</span><span class="sxs-lookup"><span data-stu-id="2966b-504">Look up a host name from the IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="2966b-505">Прототип</span><span class="sxs-lookup"><span data-stu-id="2966b-505">Prototype</span></span>
```C
UINT nxd_dns_host_by_address_get(NX_DNS *dns_ptr, 
                                 NXD_ADDRESS ip_address, 
                                 ULONG *host_name_ptr, 
                                 ULONG max_host_name_size, 
                                 ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="2966b-506">Описание</span><span class="sxs-lookup"><span data-stu-id="2966b-506">Description</span></span>

<span data-ttu-id="2966b-507">Эта служба запрашивает разрешение имен для IPv6- или IPv4-адреса во входном аргументе *ip_address* с одного DNS-сервера или нескольких, ранее указанных приложением.</span><span class="sxs-lookup"><span data-stu-id="2966b-507">This service requests name resolution of the IPv6 or IPv4 address in the *ip_address* input argument from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="2966b-508">В случае успешного выполнения возвращается имя узла, оканчивающееся символом NULL, в строке, заданной *host_name_ptr*.</span><span class="sxs-lookup"><span data-stu-id="2966b-508">If successful, the NULL-terminated host name is returned in the string specified by *host_name_ptr*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2966b-509">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2966b-509">Input Parameters</span></span>

- <span data-ttu-id="2966b-510">**dns_ptr**: указатель на ранее созданный экземпляр DNS</span><span class="sxs-lookup"><span data-stu-id="2966b-510">**dns_ptr** Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="2966b-511">**ip_address**: IP-адрес для разрешения в имя</span><span class="sxs-lookup"><span data-stu-id="2966b-511">**ip_address** IP address to resolve into a name</span></span>
- <span data-ttu-id="2966b-512">**host_name_ptr**: указатель на область назначения для имени узла</span><span class="sxs-lookup"><span data-stu-id="2966b-512">**host_name_ptr** Pointer to destination area for host name</span></span>
- <span data-ttu-id="2966b-513">**max_host_name_size**: размер области назначения для имени узла</span><span class="sxs-lookup"><span data-stu-id="2966b-513">**max_host_name_size** Size of destination area for host name</span></span>
- <span data-ttu-id="2966b-514">**wait_option**: определяет, как долго служба будет ожидать (в тактах таймера) ответ DNS-сервера после каждого запроса DNS и повторных попыток выполнения запроса</span><span class="sxs-lookup"><span data-stu-id="2966b-514">**wait_option** Defines how long the service will wait in timer ticks for a DNS server response after each DNS query and query retry.</span></span> <span data-ttu-id="2966b-515">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="2966b-515">The wait options are defined as follows:</span></span>

  <span data-ttu-id="2966b-516">Значение времени ожидания (0x00000001–0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="2966b-516">timeout value (0x00000001 through 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span></span>  

  <span data-ttu-id="2966b-517">Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока DNS-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="2966b-517">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

  <span data-ttu-id="2966b-518">Числовое значение (1–0xFFFFFFFE) определяет максимальное количество тактов таймера, чтобы оставаться в состоянии приостановки во время ожидания разрешения DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-518">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>

### <a name="return-values"></a><span data-ttu-id="2966b-519">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2966b-519">Return Values</span></span>

- <span data-ttu-id="2966b-520">**NX_SUCCESS** (0x00) — разрешение DNS успешно выполнено.</span><span class="sxs-lookup"><span data-stu-id="2966b-520">**NX_SUCCESS** (0x00) Successful DNS resolution</span></span>  
- <span data-ttu-id="2966b-521">**NX_DNS_TIMEOUT** (0xA2) — истекло время ожидания при получении мьютекса DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-521">**NX_DNS_TIMEOUT** (0xA2) Timed out on obtaining DNS mutex</span></span>
- <span data-ttu-id="2966b-522">**NX_DNS_NO_SERVER** (0xA1) — не указан адрес DNS-сервера.</span><span class="sxs-lookup"><span data-stu-id="2966b-522">**NX_DNS_NO_SERVER** (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="2966b-523">**NX_DNS_QUERY_FAILED** (0xA3) — не получен ответ на запрос.</span><span class="sxs-lookup"><span data-stu-id="2966b-523">**NX_DNS_QUERY_FAILED** (0xA3) Received no response to query</span></span>
- <span data-ttu-id="2966b-524">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) — входной адрес имеет значение NULL.</span><span class="sxs-lookup"><span data-stu-id="2966b-524">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null input address</span></span>
- <span data-ttu-id="2966b-525">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) — не удается обработать запись с отключенным IPv6.</span><span class="sxs-lookup"><span data-stu-id="2966b-525">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="2966b-526">NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-526">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="2966b-527">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="2966b-527">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="2966b-528">NX_DNS_PARAM_ERROR (0xA8) — недопустимые входные данные без указателя.</span><span class="sxs-lookup"><span data-stu-id="2966b-528">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2966b-529">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2966b-529">Allowed From</span></span>

<span data-ttu-id="2966b-530">Потоки</span><span class="sxs-lookup"><span data-stu-id="2966b-530">Threads</span></span>

<span data-ttu-id="2966b-531">**Пример**</span><span class="sxs-lookup"><span data-stu-id="2966b-531">**Example**</span></span>
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

## <a name="nx_dns_host_by_name_get"></a><span data-ttu-id="2966b-532">nx_dns_host_by_name_get</span><span class="sxs-lookup"><span data-stu-id="2966b-532">nx_dns_host_by_name_get</span></span>

<span data-ttu-id="2966b-533">Поиск IP-адреса по имени узла</span><span class="sxs-lookup"><span data-stu-id="2966b-533">Look up an IP address from the host name</span></span>

### <a name="prototype"></a><span data-ttu-id="2966b-534">Прототип</span><span class="sxs-lookup"><span data-stu-id="2966b-534">Prototype</span></span>
```C
UINT nx_dns_host_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="2966b-535">Описание</span><span class="sxs-lookup"><span data-stu-id="2966b-535">Description</span></span>

<span data-ttu-id="2966b-536">Эта служба запрашивает разрешение имен для указанного имени с одного DNS-сервера или нескольких, ранее указанных приложением.</span><span class="sxs-lookup"><span data-stu-id="2966b-536">This service requests name resolution of the supplied name from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="2966b-537">В случае успешного выполнения соответствующий IP-адрес возвращается в место назначения, на которое указывает host_address_ptr.</span><span class="sxs-lookup"><span data-stu-id="2966b-537">If successful, the associated IP address is returned in the destination pointed to by host_address_ptr.</span></span> <span data-ttu-id="2966b-538">Это функция-оболочка для службы *nxd_dns_host_by_name_get*, и в качестве входных данных она поддерживает только IPv4-адреса.</span><span class="sxs-lookup"><span data-stu-id="2966b-538">This is a wrapper function for the *nxd_dns_host_by_name_get* service, and is limited to IPv4 address input.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2966b-539">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2966b-539">Input Parameters</span></span>

- <span data-ttu-id="2966b-540">**dns_ptr**: указатель на ранее созданный экземпляр DNS</span><span class="sxs-lookup"><span data-stu-id="2966b-540">**dns_ptr** Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="2966b-541">**host_name**: указатель на имя узла</span><span class="sxs-lookup"><span data-stu-id="2966b-541">**host_name** Pointer to host name</span></span>
- <span data-ttu-id="2966b-542">**host_address_ptr**: возвращенный IP-адрес DNS-сервера</span><span class="sxs-lookup"><span data-stu-id="2966b-542">**host_address_ptr** DNS Server IP address returned</span></span>
- <span data-ttu-id="2966b-543">**wait_option**: определяет, как долго служба будет ожидать разрешение DNS</span><span class="sxs-lookup"><span data-stu-id="2966b-543">**wait_option** Defines how long the service will wait for the DNS resolution.</span></span> <span data-ttu-id="2966b-544">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="2966b-544">The wait options are defined as follows:</span></span>

  <span data-ttu-id="2966b-545">Значение времени ожидания (0x00000001–0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="2966b-545">timeout value (0x00000001 through 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span></span>

  <span data-ttu-id="2966b-546">Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока DNS-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="2966b-546">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

  <span data-ttu-id="2966b-547">Числовое значение (1–0xFFFFFFFE) определяет максимальное количество тактов таймера, чтобы оставаться в состоянии приостановки во время ожидания разрешения DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-547">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>

### <a name="return-values"></a><span data-ttu-id="2966b-548">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2966b-548">Return Values</span></span>

- <span data-ttu-id="2966b-549">**NX_SUCCESS** (0x00) — разрешение DNS успешно выполнено.</span><span class="sxs-lookup"><span data-stu-id="2966b-549">**NX_SUCCESS** (0x00) Successful DNS resolution.</span></span>
- <span data-ttu-id="2966b-550">**NX_DNS_NO_SERVER** (0xA1) — не указан адрес DNS-сервера.</span><span class="sxs-lookup"><span data-stu-id="2966b-550">**NX_DNS_NO_SERVER** (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="2966b-551">**NX_DNS_QUERY_FAILED** (0xA3) — не получен ответ на запрос.</span><span class="sxs-lookup"><span data-stu-id="2966b-551">**NX_DNS_QUERY_FAILED** (0xA3) Received no response to query</span></span>
- <span data-ttu-id="2966b-552">NX_DNS_PARAM_ERROR (0xA8) — недопустимые входные данные без указателя.</span><span class="sxs-lookup"><span data-stu-id="2966b-552">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="2966b-553">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="2966b-553">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="2966b-554">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="2966b-554">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2966b-555">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2966b-555">Allowed From</span></span>

<span data-ttu-id="2966b-556">Потоки</span><span class="sxs-lookup"><span data-stu-id="2966b-556">Threads</span></span>

<span data-ttu-id="2966b-557">**Пример**</span><span class="sxs-lookup"><span data-stu-id="2966b-557">**Example**</span></span>
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

## <a name="nxd_dns_host_by_name_get"></a><span data-ttu-id="2966b-558">nxd_dns_host_by_name_get</span><span class="sxs-lookup"><span data-stu-id="2966b-558">nxd_dns_host_by_name_get</span></span>

<span data-ttu-id="2966b-559">Поиск IP-адреса по имени узла</span><span class="sxs-lookup"><span data-stu-id="2966b-559">Lookup an IP address from the host name</span></span>

### <a name="prototype"></a><span data-ttu-id="2966b-560">Прототип</span><span class="sxs-lookup"><span data-stu-id="2966b-560">Prototype</span></span>
```C
UINT nxd_dns_host_by_name_get(NX_DNS *dns_ptr, ULONG *host_name, 
                              NXD_ADDRESS *host_address_ptr, 
                              ULONG wait_option, UINT lookup_type);
```

### <a name="description"></a><span data-ttu-id="2966b-561">Описание</span><span class="sxs-lookup"><span data-stu-id="2966b-561">Description</span></span>

<span data-ttu-id="2966b-562">Эта служба запрашивает разрешение имен для указанного IP-адреса с одного DNS-сервера или нескольких, ранее указанных приложением.</span><span class="sxs-lookup"><span data-stu-id="2966b-562">This service requests name resolution of the supplied IP address from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="2966b-563">В случае успешного выполнения соответствующий IP-адрес возвращается в NXD_ADDRESS, на который указывает *host_address_ptr*.</span><span class="sxs-lookup"><span data-stu-id="2966b-563">If successful, the associated IP address is returned in an NXD_ADDRESS pointed to by *host_address_ptr*.</span></span> <span data-ttu-id="2966b-564">Если вызывающий объект явно задает для входных данных lookup_type значение NX_IP_VERSION_V6, эта служба отправит запрос для IPv6-адреса узла (запись AAAA).</span><span class="sxs-lookup"><span data-stu-id="2966b-564">If the caller specifically sets the lookup_type input to NX_IP_VERSION_V6, this service will send out query for a host IPv6 address (AAAA record).</span></span> <span data-ttu-id="2966b-565">Если вызывающий объект явно задает для входных данных lookup_type значение NX_IP_VERSION_V4, эта служба отправит запрос для IPv4-адреса узла (запись A).</span><span class="sxs-lookup"><span data-stu-id="2966b-565">If the caller specifically sets the lookup_type input to NX_IP_VERSION_V4, this service will send out query for a host IPv4 address (A record).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2966b-566">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2966b-566">Input Parameters</span></span>

- <span data-ttu-id="2966b-567">**dns_ptr**: указатель на ранее созданный экземпляр DNS-клиента</span><span class="sxs-lookup"><span data-stu-id="2966b-567">**dns_ptr** Pointer to previously created DNS Client instance.</span></span>
- <span data-ttu-id="2966b-568">**host_name**: указатель на имя узла, IP-адрес которого нужно найти</span><span class="sxs-lookup"><span data-stu-id="2966b-568">**host_name** Pointer to host name to find an IP address of</span></span>
- <span data-ttu-id="2966b-569">**host_address_ptr**: указатель на назначение для NXD_ADDRESS, содержащего IP-адрес</span><span class="sxs-lookup"><span data-stu-id="2966b-569">**host_address_ptr** Pointer to destination for NXD_ADDRESS containing the IP address</span></span>
- <span data-ttu-id="2966b-570">**wait_option**: определяет, как долго служба будет ожидать (в тактах таймера) ответ DNS-сервера для каждой передачи и повторной передачи запроса</span><span class="sxs-lookup"><span data-stu-id="2966b-570">**wait_option** Defines how long the service will wait in timer ticks for the DNS Server response for each query transmission and retransmission.</span></span> <span data-ttu-id="2966b-571">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="2966b-571">The wait options are defined as follows:</span></span>

  <span data-ttu-id="2966b-572">Значение времени ожидания (0x00000001–0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="2966b-572">timeout value (0x00000001 through 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span></span>  

  <span data-ttu-id="2966b-573">Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока DNS-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="2966b-573">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS Server responds to the request.</span></span>

  <span data-ttu-id="2966b-574">Числовое значение (1–0xFFFFFFFE) определяет максимальное количество тактов таймера, чтобы оставаться в состоянии приостановки во время ожидания разрешения DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-574">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>

- <span data-ttu-id="2966b-575">**lookup_type**: указывает тип поиска (A или AAAA)</span><span class="sxs-lookup"><span data-stu-id="2966b-575">**lookup_type** Indicate type of lookup (A vs AAAA).</span></span>

### <a name="return-values"></a><span data-ttu-id="2966b-576">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2966b-576">Return Values</span></span>

- <span data-ttu-id="2966b-577">**NX_SUCCESS** (0x00) — разрешение DNS успешно выполнено.</span><span class="sxs-lookup"><span data-stu-id="2966b-577">**NX_SUCCESS** (0x00) Successful DNS resolution.</span></span>
- <span data-ttu-id="2966b-578">**NX_DNS_NO_SERVER** (0xA1) — не указан адрес DNS-сервера.</span><span class="sxs-lookup"><span data-stu-id="2966b-578">**NX_DNS_NO_SERVER** (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="2966b-579">**NX_DNS_QUERY_FAILED** (0xA3) — не получен ответ на запрос.</span><span class="sxs-lookup"><span data-stu-id="2966b-579">**NX_DNS_QUERY_FAILED** (0xA3) Received no response to query</span></span>
- <span data-ttu-id="2966b-580">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) — входной адрес имеет значение NULL.</span><span class="sxs-lookup"><span data-stu-id="2966b-580">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null input address</span></span>
- <span data-ttu-id="2966b-581">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) — не удается обработать запись с отключенным IPv6.</span><span class="sxs-lookup"><span data-stu-id="2966b-581">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="2966b-582">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="2966b-582">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="2966b-583">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="2966b-583">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="2966b-584">NX_DNS_PARAM_ERROR (0xA8) — недопустимые входные данные без указателя.</span><span class="sxs-lookup"><span data-stu-id="2966b-584">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2966b-585">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2966b-585">Allowed From</span></span>

<span data-ttu-id="2966b-586">Потоки</span><span class="sxs-lookup"><span data-stu-id="2966b-586">Threads</span></span>

<span data-ttu-id="2966b-587">**Пример**</span><span class="sxs-lookup"><span data-stu-id="2966b-587">**Example**</span></span>
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

<span data-ttu-id="2966b-588">Ниже приведен еще один пример использования этой службы времени, на этот раз с использованием IPv4-адреса и типов записей A.</span><span class="sxs-lookup"><span data-stu-id="2966b-588">Another example of using this time service, this time using IPv4 addresses and A record types, is shown below:</span></span>
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

## <a name="nx_dns_host_text_get"></a><span data-ttu-id="2966b-589">nx_dns_host_text_get</span><span class="sxs-lookup"><span data-stu-id="2966b-589">nx_dns_host_text_get</span></span>

<span data-ttu-id="2966b-590">Поиск текстовой строки для входного доменного имени</span><span class="sxs-lookup"><span data-stu-id="2966b-590">Look up the text string for the input domain name</span></span>

### <a name="prototype"></a><span data-ttu-id="2966b-591">Прототип</span><span class="sxs-lookup"><span data-stu-id="2966b-591">Prototype</span></span>
```C
UINT nx_dns_host_text_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                          UCHAR *record_buffer, 
                          UINT buffer_size, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="2966b-592">Описание</span><span class="sxs-lookup"><span data-stu-id="2966b-592">Description</span></span>

<span data-ttu-id="2966b-593">Эта служба отправляет запрос типа TXT с указанными доменным именем и буфером для получения произвольных строковых данных.</span><span class="sxs-lookup"><span data-stu-id="2966b-593">This service sends a query of type TXT with the specified domain name and buffer to obtain the arbitrary string data.</span></span>

<span data-ttu-id="2966b-594">DNS-клиент копирует текстовую строку в записи TXT в ответе DNS-сервера по адресу памяти *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="2966b-594">The DNS Client copies the text string in the TXT record in the DNS Server response into the *record_buffer* memory location.</span></span> 

> [!NOTE]
> <span data-ttu-id="2966b-595">Для получения данных выравнивание record_buffer по 4 байт не требуется.</span><span class="sxs-lookup"><span data-stu-id="2966b-595">The record_buffer does not need to be 4-byte aligned to receive the data.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2966b-596">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2966b-596">Input Parameters</span></span>

- <span data-ttu-id="2966b-597">**dns_ptr**: указатель на DNS-клиент</span><span class="sxs-lookup"><span data-stu-id="2966b-597">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="2966b-598">**host_name**: указатель на имя узла, по которому следует выполнять поиск</span><span class="sxs-lookup"><span data-stu-id="2966b-598">**host_name** Pointer to name of host to search on</span></span>
- <span data-ttu-id="2966b-599">**record_buffer**: указатель на расположение, в которое следует извлечь данные TXT</span><span class="sxs-lookup"><span data-stu-id="2966b-599">**record_buffer** Pointer to location to extract TXT data into</span></span>
- <span data-ttu-id="2966b-600">**buffer_size**: размер буфера для хранения данных TXT</span><span class="sxs-lookup"><span data-stu-id="2966b-600">**buffer_size** Size of buffer to hold TXT data</span></span>
- <span data-ttu-id="2966b-601">**wait_option**: параметр ожидания для получения ответа DNS-сервера</span><span class="sxs-lookup"><span data-stu-id="2966b-601">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="2966b-602">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2966b-602">Return Values</span></span>

- <span data-ttu-id="2966b-603">**NX_SUCCESS** (0x00) — строка TXT успешно получена.</span><span class="sxs-lookup"><span data-stu-id="2966b-603">**NX_SUCCESS** (0x00) Successfully TXT string obtained</span></span>
- <span data-ttu-id="2966b-604">**NX_DNS_NO_SERVER** (0xA1) — список серверов клиента пуст.</span><span class="sxs-lookup"><span data-stu-id="2966b-604">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="2966b-605">**NX_DNS_QUERY_FAILED** (0xA3) — не получен допустимый ответ DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-605">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="2966b-606">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="2966b-606">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="2966b-607">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="2966b-607">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="2966b-608">NX_DNS_PARAM_ERROR (0xA8) — недопустимые входные данные без указателя.</span><span class="sxs-lookup"><span data-stu-id="2966b-608">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2966b-609">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2966b-609">Allowed From</span></span>

<span data-ttu-id="2966b-610">Потоки</span><span class="sxs-lookup"><span data-stu-id="2966b-610">Threads</span></span>

######   
<span data-ttu-id="2966b-611">Пример</span><span class="sxs-lookup"><span data-stu-id="2966b-611">Example</span></span>
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

## <a name="nx_dns_packet_pool_set"></a><span data-ttu-id="2966b-612">nx_dns_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="2966b-612">nx_dns_packet_pool_set</span></span>

<span data-ttu-id="2966b-613">Задание пула пакетов DNS-клиента</span><span class="sxs-lookup"><span data-stu-id="2966b-613">Set the DNS Client packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="2966b-614">Прототип</span><span class="sxs-lookup"><span data-stu-id="2966b-614">Prototype</span></span>
```C
UINT nx_dns_packet_pool_set(NX_DNS *dns_ptr, NX_PACKET_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="2966b-615">Описание</span><span class="sxs-lookup"><span data-stu-id="2966b-615">Description</span></span>

<span data-ttu-id="2966b-616">Эта служба задает ранее созданный пул пакетов в качестве пула пакетов DNS-клиента.</span><span class="sxs-lookup"><span data-stu-id="2966b-616">This service sets a previously created packet pool as the DNS Client packet pool.</span></span> <span data-ttu-id="2966b-617">DNS-клиент будет использовать этот пул пакетов для отправки запросов DNS, поэтому размер полезных данных пакета должен быть не меньше значения NX_DNS_PACKET_PAYLOAD, включающего в себя заголовки Ethernet, IP и UDP и определенного в файле *nxd_dns.h*.</span><span class="sxs-lookup"><span data-stu-id="2966b-617">The DNS Client will use this packet pool to send DNS queries, so the packet payload should not be less than NX_DNS_PACKET_PAYLOAD which includes the Ethernet, IP and UDP headers and is defined in *nxd_dns.h.*</span></span> 

> [!NOTE]
> <span data-ttu-id="2966b-618">*П* ри удалении DNS-клиента пул пакетов не удаляется вместе с ним. Приложение может удалить пул пакетов, когда он больше не нужен.</span><span class="sxs-lookup"><span data-stu-id="2966b-618">*W* hen the DNS Client is deleted, the packet pool is not deleted with it and it is the responsibility of the application to delete the packet pool when it no longer needs it.</span></span>
>
> <span data-ttu-id="2966b-619">Эта служба доступна, только если параметр конфигурации NX_DNS_CLIENT_USER_CREATE_PACKET_POOL определен в файле *nxd_dns.h*.</span><span class="sxs-lookup"><span data-stu-id="2966b-619">This service is only available if the configuration option NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is defined in *nxd_dns.h*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2966b-620">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2966b-620">Input Parameters</span></span>

- <span data-ttu-id="2966b-621">**dns_ptr**: указатель на ранее созданный экземпляр DNS-клиента</span><span class="sxs-lookup"><span data-stu-id="2966b-621">**dns_ptr** Pointer to previously created DNS Client instance.</span></span>
- <span data-ttu-id="2966b-622">**pool_ptr**: указатель на ранее созданный пул пакетов</span><span class="sxs-lookup"><span data-stu-id="2966b-622">**pool_ptr** Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="2966b-623">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2966b-623">Return Values</span></span>

- <span data-ttu-id="2966b-624">**NX_SUCCESS** (0x00) — успешное выполнение.</span><span class="sxs-lookup"><span data-stu-id="2966b-624">**NX_SUCCESS** (0x00) Successful completion.</span></span>
- <span data-ttu-id="2966b-625">**NX_NOT_ENABLED** (0x14) — клиент не настроен для использования этого параметра.</span><span class="sxs-lookup"><span data-stu-id="2966b-625">**NX_NOT_ENABLED** (0x14) Client not configured for this option</span></span>
- <span data-ttu-id="2966b-626">NX_PTR_ERROR (0x07) — недопустимый указатель IP-адреса или DNS-клиента.</span><span class="sxs-lookup"><span data-stu-id="2966b-626">NX_PTR_ERROR (0x07) Invalid IP or DNS Client pointer.</span></span>
- <span data-ttu-id="2966b-627">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="2966b-627">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2966b-628">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2966b-628">Allowed From</span></span>

<span data-ttu-id="2966b-629">Потоки</span><span class="sxs-lookup"><span data-stu-id="2966b-629">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2966b-630">Пример</span><span class="sxs-lookup"><span data-stu-id="2966b-630">Example</span></span>
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

## <a name="nx_dns_server_add"></a><span data-ttu-id="2966b-631">nx_dns_server_add</span><span class="sxs-lookup"><span data-stu-id="2966b-631">nx_dns_server_add</span></span>

<span data-ttu-id="2966b-632">Добавление DNS-сервера с IP-адресом</span><span class="sxs-lookup"><span data-stu-id="2966b-632">Add DNS Server IP Address</span></span>

### <a name="prototype"></a><span data-ttu-id="2966b-633">Прототип</span><span class="sxs-lookup"><span data-stu-id="2966b-633">Prototype</span></span>
```C
UINT nx_dns_server_add(NX_DNS *dns_ptr, ULONG server_address);
```
### <a name="description"></a><span data-ttu-id="2966b-634">Описание</span><span class="sxs-lookup"><span data-stu-id="2966b-634">Description</span></span>

<span data-ttu-id="2966b-635">Эта служба добавляет DNS-сервер с IPv4-адресом в список серверов.</span><span class="sxs-lookup"><span data-stu-id="2966b-635">This service adds an IPv4 DNS Server to the server list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2966b-636">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2966b-636">Input Parameters</span></span>

- <span data-ttu-id="2966b-637">**dns_ptr**: указатель на блок управления DNS</span><span class="sxs-lookup"><span data-stu-id="2966b-637">**dns_ptr** Pointer to DNS control block.</span></span>  
- <span data-ttu-id="2966b-638">**server_address**: IP-адрес DNS-сервера</span><span class="sxs-lookup"><span data-stu-id="2966b-638">**server_address** IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="2966b-639">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2966b-639">Return Values</span></span>

- <span data-ttu-id="2966b-640">**NX_SUCCESS** (0x00) — сервер успешно добавлен.</span><span class="sxs-lookup"><span data-stu-id="2966b-640">**NX_SUCCESS** (0x00) Server successfully added</span></span>
- <span data-ttu-id="2966b-641">**NX_DNS_DUPLICATE_ENTRY**</span><span class="sxs-lookup"><span data-stu-id="2966b-641">**NX_DNS_DUPLICATE_ENTRY**</span></span>  
<span data-ttu-id="2966b-642">**NX_NO_MORE_ENTRIES** (0x17) — добавление DNS-серверов запрещено (список полон).</span><span class="sxs-lookup"><span data-stu-id="2966b-642">**NX_NO_MORE_ENTRIES** (0x17) No more DNS Servers Allowed (list is full)</span></span>
- <span data-ttu-id="2966b-643">**NX_DNS_PARAM_ERROR** (0xA8) — недопустимые входные данные без указателя.</span><span class="sxs-lookup"><span data-stu-id="2966b-643">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="2966b-644">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) — не удается обработать запись с отключенным IPv6.</span><span class="sxs-lookup"><span data-stu-id="2966b-644">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="2966b-645">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="2966b-645">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="2966b-646">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="2966b-646">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="2966b-647">NX_DNS_BAD_ADDRESS_ERROR (0xA4) — введен адрес сервера со значением NULL.</span><span class="sxs-lookup"><span data-stu-id="2966b-647">NX_DNS_BAD_ADDRESS_ERROR (0xA4) Null server address input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2966b-648">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2966b-648">Allowed From</span></span>

<span data-ttu-id="2966b-649">Потоки</span><span class="sxs-lookup"><span data-stu-id="2966b-649">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2966b-650">Пример</span><span class="sxs-lookup"><span data-stu-id="2966b-650">Example</span></span>
```C
/* Add a DNS Server at IP address 202.2.2.13. */
status =  nx_dns_server_add(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully added. */
```

## <a name="nxd_dns_server_add"></a><span data-ttu-id="2966b-651">nxd_dns_server_add</span><span class="sxs-lookup"><span data-stu-id="2966b-651">nxd_dns_server_add</span></span>

<span data-ttu-id="2966b-652">Добавление DNS-сервера в список клиента</span><span class="sxs-lookup"><span data-stu-id="2966b-652">Add DNS Server to the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="2966b-653">Прототип</span><span class="sxs-lookup"><span data-stu-id="2966b-653">Prototype</span></span>
```C
UINT nxd_dns_server_add(NX_DNS *dns_ptr, NXD_ADDRESS *server_address);
```
### <a name="description"></a><span data-ttu-id="2966b-654">Описание</span><span class="sxs-lookup"><span data-stu-id="2966b-654">Description</span></span>

<span data-ttu-id="2966b-655">Эта служба добавляет IP-адрес DNS-сервера в список серверов DNS-клиента.</span><span class="sxs-lookup"><span data-stu-id="2966b-655">This service adds the IP address of a DNS server to the DNS Client server list.</span></span> <span data-ttu-id="2966b-656">Значение server_address может быть IPv4- или IPv6-адресом.</span><span class="sxs-lookup"><span data-stu-id="2966b-656">The server_address may be either an IPv4 or IPv6 address.</span></span> <span data-ttu-id="2966b-657">Если клиент хочет получать доступ к одному серверу по его IPv4- или IPv6-адресу, он должен добавить оба IP-адреса в качестве записей в список серверов.</span><span class="sxs-lookup"><span data-stu-id="2966b-657">If the Client wishes to be able to access the same server by either its IPv4 address or IPv6 address it should add both IP addresses as entries to the server list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2966b-658">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2966b-658">Input Parameters</span></span>

- <span data-ttu-id="2966b-659">**dns_ptr**: указатель на блок управления DNS</span><span class="sxs-lookup"><span data-stu-id="2966b-659">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="2966b-660">**server_address**: указатель на NXD_ADDRESS, содержащий IP-адрес сервера для DNS-сервера</span><span class="sxs-lookup"><span data-stu-id="2966b-660">**server_address** Pointer to the NXD_ADDRESS containing the server IP address of DNS Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="2966b-661">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2966b-661">Return Values</span></span>

- <span data-ttu-id="2966b-662">**NX_SUCCESS** (0x00) — сервер успешно добавлен.</span><span class="sxs-lookup"><span data-stu-id="2966b-662">**NX_SUCCESS** (0x00) Server successfully added</span></span>
- <span data-ttu-id="2966b-663">**NX_DNS_DUPLICATE_ENTRY**</span><span class="sxs-lookup"><span data-stu-id="2966b-663">**NX_DNS_DUPLICATE_ENTRY**</span></span>  
<span data-ttu-id="2966b-664">**NX_NO_MORE_ENTRIES** (0x17) — добавление DNS-серверов запрещено (список полон).</span><span class="sxs-lookup"><span data-stu-id="2966b-664">**NX_NO_MORE_ENTRIES** (0x17) No more DNS Servers allowed (list is full)</span></span> 
- <span data-ttu-id="2966b-665">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) — не удается обработать запись с отключенным IPv6.</span><span class="sxs-lookup"><span data-stu-id="2966b-665">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="2966b-666">**NX_DNS_PARAM_ERROR** (0xA8) — недопустимые входные данные без указателя.</span><span class="sxs-lookup"><span data-stu-id="2966b-666">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="2966b-667">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="2966b-667">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="2966b-668">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="2966b-668">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="2966b-669">NX_DNS_BAD_ADDRESS_ERROR (0xA4) — введен адрес сервера со значением NULL.</span><span class="sxs-lookup"><span data-stu-id="2966b-669">NX_DNS_BAD_ADDRESS_ERROR (0xA4) Null server address input</span></span>
- <span data-ttu-id="2966b-670">NX_DNS_INVALID_ADDRESS_TYPE (0xB2) — индекс указывает на недопустимый тип адреса (например, IPv6).</span><span class="sxs-lookup"><span data-stu-id="2966b-670">NX_DNS_INVALID_ADDRESS_TYPE (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2966b-671">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2966b-671">Allowed From</span></span>

<span data-ttu-id="2966b-672">Потоки</span><span class="sxs-lookup"><span data-stu-id="2966b-672">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2966b-673">Пример</span><span class="sxs-lookup"><span data-stu-id="2966b-673">Example</span></span>
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

## <a name="nx_dns_server_get"></a><span data-ttu-id="2966b-674">nx_dns_server_get</span><span class="sxs-lookup"><span data-stu-id="2966b-674">nx_dns_server_get</span></span>

<span data-ttu-id="2966b-675">Возврат DNS-сервера с IPv4-адресом из списка клиента</span><span class="sxs-lookup"><span data-stu-id="2966b-675">Return an IPv4 DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="2966b-676">Прототип</span><span class="sxs-lookup"><span data-stu-id="2966b-676">Prototype</span></span>
```C
UINT nx_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                        ULONG *dns_server_address);
```

### <a name="description"></a><span data-ttu-id="2966b-677">Описание</span><span class="sxs-lookup"><span data-stu-id="2966b-677">Description</span></span>

<span data-ttu-id="2966b-678">Эта служба возвращает DNS-сервер с IPv4-адресом из списка серверов по указанному индексу.</span><span class="sxs-lookup"><span data-stu-id="2966b-678">This service returns the IPv4 DNS Server address from the server list at the specified index.</span></span> 

> [!NOTE]
> <span data-ttu-id="2966b-679">Индексация начинается с нуля.</span><span class="sxs-lookup"><span data-stu-id="2966b-679">The index is zero based.</span></span> <span data-ttu-id="2966b-680">Если входной индекс превышает размер списка DNS-клиента, в этом индексе находится IPv6-адрес или по указанному индексу обнаружен пустой адрес, возвращается ошибка.</span><span class="sxs-lookup"><span data-stu-id="2966b-680">If the input index exceeds the size of the DNS Client list, an IPv6 address is found at that index or a null address is found at the specified index, an error is returned.</span></span> <span data-ttu-id="2966b-681">Сначала можно вызвать службу *nx_dns_get_serverlist_size*, чтобы получить количество DNS-серверов в списке клиента.</span><span class="sxs-lookup"><span data-stu-id="2966b-681">The *nx_dns_get_serverlist_size* service may be called first obtain the number of DNS servers in the Client list.</span></span>

<span data-ttu-id="2966b-682">Эта служба поддерживает только IPv4-адреса.</span><span class="sxs-lookup"><span data-stu-id="2966b-682">This service does only supports IPv4 addresses.</span></span> <span data-ttu-id="2966b-683">Она вызывает службу *nxd_dns_server_get*, которая поддерживает IPv4- и IPv6-адреса.</span><span class="sxs-lookup"><span data-stu-id="2966b-683">It calls the *nxd_dns_server_get* service which supports both IPv4 and IPv6 addresses.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2966b-684">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2966b-684">Input Parameters</span></span>

- <span data-ttu-id="2966b-685">**dns_ptr**: указатель на блок управления DNS</span><span class="sxs-lookup"><span data-stu-id="2966b-685">**dns_ptr** Pointer to DNS control block</span></span>  
- <span data-ttu-id="2966b-686">**index**: индекс в списке серверов DNS-клиента</span><span class="sxs-lookup"><span data-stu-id="2966b-686">**index** Index into DNS Client’s list of servers</span></span>
- <span data-ttu-id="2966b-687">**dns_server_address**: указатель на IP-адрес DNS-сервера</span><span class="sxs-lookup"><span data-stu-id="2966b-687">**dns_server_address** Pointer to IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="2966b-688">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2966b-688">Return Values</span></span>

- <span data-ttu-id="2966b-689">**NX_SUCCESS** (0x00) — сервер успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="2966b-689">**NX_SUCCESS** (0x00) Successful server returned</span></span>
- <span data-ttu-id="2966b-690">**NX_DNS_SERVER_NOT_FOUND** (0xA9) — индекс указывает на пустой слот.</span><span class="sxs-lookup"><span data-stu-id="2966b-690">**NX_DNS_SERVER_NOT_FOUND** (0xA9) Index points to empty slot</span></span>
- <span data-ttu-id="2966b-691">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) — индекс указывает на пустой адрес.</span><span class="sxs-lookup"><span data-stu-id="2966b-691">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Index points to Null address</span></span>
- <span data-ttu-id="2966b-692">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) — индекс указывает на недопустимый тип адреса (например, IPv6).</span><span class="sxs-lookup"><span data-stu-id="2966b-692">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>
- <span data-ttu-id="2966b-693">**NX_DNS_PARAM_ERROR** (0xA8) — недопустимые входные данные без указателя.</span><span class="sxs-lookup"><span data-stu-id="2966b-693">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="2966b-694">NX_PTR_ERROR (0x07) — недопустимый указатель IP-адреса или DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-694">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="2966b-695">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="2966b-695">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2966b-696">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2966b-696">Allowed From</span></span>

<span data-ttu-id="2966b-697">Потоки</span><span class="sxs-lookup"><span data-stu-id="2966b-697">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2966b-698">Пример</span><span class="sxs-lookup"><span data-stu-id="2966b-698">Example</span></span>
```C
ULONG my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list. */
status =  nx_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned. */
```

## <a name="nxd_dns_server_get"></a><span data-ttu-id="2966b-699">nxd_dns_server_get</span><span class="sxs-lookup"><span data-stu-id="2966b-699">nxd_dns_server_get</span></span>

<span data-ttu-id="2966b-700">Возврат DNS-сервера из списка клиента</span><span class="sxs-lookup"><span data-stu-id="2966b-700">Return a DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="2966b-701">Прототип</span><span class="sxs-lookup"><span data-stu-id="2966b-701">Prototype</span></span>
```C
UINT nxd_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                        NXD_ADDRESS *dns_server_address);
```

### <a name="description"></a><span data-ttu-id="2966b-702">Описание</span><span class="sxs-lookup"><span data-stu-id="2966b-702">Description</span></span>

<span data-ttu-id="2966b-703">Эта служба возвращает DNS-сервер с IP-адресом из списка серверов по указанному индексу.</span><span class="sxs-lookup"><span data-stu-id="2966b-703">This service returns the DNS Server IP address from the server list at the specified index.</span></span> 

> [!NOTE]
> <span data-ttu-id="2966b-704">Индексация начинается с нуля.</span><span class="sxs-lookup"><span data-stu-id="2966b-704">The index is zero based.</span></span> <span data-ttu-id="2966b-705">Если входной индекс превышает размер списка DNS-клиента или по указанному индексу обнаружен пустой адрес, возвращается ошибка.</span><span class="sxs-lookup"><span data-stu-id="2966b-705">If the input index exceeds the size of the DNS Client list, or a null address is found at the specified index, an error is returned.</span></span> <span data-ttu-id="2966b-706">Сначала можно вызвать службу *nx_dns_get_serverlist_size*, чтобы получить количество DNS-серверов в списке серверов.</span><span class="sxs-lookup"><span data-stu-id="2966b-706">The *nx_dns_get_serverlist_size* service may be called first to obtain the number of DNS servers in the server list.</span></span>

<span data-ttu-id="2966b-707">Эта служба поддерживает IPv4- и IPv6-адреса.</span><span class="sxs-lookup"><span data-stu-id="2966b-707">This service supports IPv4 and IPv6 addresses.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2966b-708">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2966b-708">Input Parameters</span></span>

- <span data-ttu-id="2966b-709">**dns_ptr**: указатель на блок управления DNS</span><span class="sxs-lookup"><span data-stu-id="2966b-709">**dns_ptr** Pointer to DNS control block</span></span>  
- <span data-ttu-id="2966b-710">**index**: индекс в списке серверов DNS-клиента</span><span class="sxs-lookup"><span data-stu-id="2966b-710">**index** Index into DNS Client’s list of servers</span></span>
- <span data-ttu-id="2966b-711">**dns_server_address**: указатель на IP-адрес DNS-сервера</span><span class="sxs-lookup"><span data-stu-id="2966b-711">**dns_server_address** Pointer to IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="2966b-712">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2966b-712">Return Values</span></span>

- <span data-ttu-id="2966b-713">**NX_SUCCESS** (0x00) — IP-адрес сервера успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="2966b-713">**NX_SUCCESS** (0x00) Successfully returned server IP address</span></span>
- <span data-ttu-id="2966b-714">**NX_DNS_SERVER_NOT_FOUND** (0xA9) — индекс указывает на пустой слот.</span><span class="sxs-lookup"><span data-stu-id="2966b-714">**NX_DNS_SERVER_NOT_FOUND** (0xA9) Index points to empty slot</span></span>
- <span data-ttu-id="2966b-715">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) — индекс указывает на пустой адрес сервера.</span><span class="sxs-lookup"><span data-stu-id="2966b-715">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Index points to null server address</span></span>
- <span data-ttu-id="2966b-716">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) — индекс указывает на недопустимый тип адреса (например, IPv6).</span><span class="sxs-lookup"><span data-stu-id="2966b-716">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>
- <span data-ttu-id="2966b-717">**NX_DNS_PARAM_ERROR** (0xA8) — недопустимые входные данные без указателя.</span><span class="sxs-lookup"><span data-stu-id="2966b-717">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="2966b-718">NX_PTR_ERROR (0x07) — недопустимый указатель IP-адреса или DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-718">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="2966b-719">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="2966b-719">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2966b-720">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2966b-720">Allowed From</span></span>

<span data-ttu-id="2966b-721">Потоки</span><span class="sxs-lookup"><span data-stu-id="2966b-721">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2966b-722">Пример</span><span class="sxs-lookup"><span data-stu-id="2966b-722">Example</span></span>
```C
NXD_ADDRESS my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list. */
status =  nxd_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned. */
```

## <a name="nx_dns_server_remove"></a><span data-ttu-id="2966b-723">nx_dns_server_remove</span><span class="sxs-lookup"><span data-stu-id="2966b-723">nx_dns_server_remove</span></span>

<span data-ttu-id="2966b-724">Удаление DNS-сервера с IPv4-адресом из списка клиента</span><span class="sxs-lookup"><span data-stu-id="2966b-724">Remove an IPv4 DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="2966b-725">Прототип</span><span class="sxs-lookup"><span data-stu-id="2966b-725">Prototype</span></span>
```C
UINT nx_dns_server_remove(NX_DNS *dns_ptr, ULONG server_address);
```
### <a name="description"></a><span data-ttu-id="2966b-726">Описание</span><span class="sxs-lookup"><span data-stu-id="2966b-726">Description</span></span>

<span data-ttu-id="2966b-727">Эта служба удаляет DNS-сервер с IPv4-адресом из списка клиента.</span><span class="sxs-lookup"><span data-stu-id="2966b-727">This service removes an IPv4 DNS Server from the Client list.</span></span> <span data-ttu-id="2966b-728">Это функция-оболочка для *nxd_dns_server_remove*.</span><span class="sxs-lookup"><span data-stu-id="2966b-728">It is a wrapper function for *nxd_dns_server_remove*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2966b-729">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2966b-729">Input Parameters</span></span>

- <span data-ttu-id="2966b-730">**dns_ptr**: указатель на блок управления DNS</span><span class="sxs-lookup"><span data-stu-id="2966b-730">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="2966b-731">**server_address**: IP-адрес DNS-сервера</span><span class="sxs-lookup"><span data-stu-id="2966b-731">**server_address** IP address of DNS Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="2966b-732">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2966b-732">Return Values</span></span>

- <span data-ttu-id="2966b-733">**NX_SUCCESS** (0x00) — DNS-сервер успешно удален.</span><span class="sxs-lookup"><span data-stu-id="2966b-733">**NX_SUCCESS** (0x00) DNS Server successfully removed</span></span>
- <span data-ttu-id="2966b-734">**NX_DNS_SERVER_NOT_FOUND** (0xA9) — сервер отсутствует в списке клиента.</span><span class="sxs-lookup"><span data-stu-id="2966b-734">**NX_DNS_SERVER_NOT_FOUND** (0xA9) Server not in Client list</span></span>
- <span data-ttu-id="2966b-735">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) — введен адрес сервера со значением NULL.</span><span class="sxs-lookup"><span data-stu-id="2966b-735">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null server address input</span></span>
- <span data-ttu-id="2966b-736">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) — не удается обработать запись с отключенным IPv6.</span><span class="sxs-lookup"><span data-stu-id="2966b-736">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="2966b-737">NX_PTR_ERROR (0x07) — недопустимый указатель IP-адреса или DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-737">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="2966b-738">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="2966b-738">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2966b-739">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2966b-739">Allowed From</span></span>

<span data-ttu-id="2966b-740">Потоки</span><span class="sxs-lookup"><span data-stu-id="2966b-740">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2966b-741">Пример</span><span class="sxs-lookup"><span data-stu-id="2966b-741">Example</span></span>
```C
/* Remove the DNS Server at IP address is 202.2.2.13.  */
status =  nx_dns_server_remove(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully
   removed.  */
```

## <a name="nxd_dns_server_remove"></a><span data-ttu-id="2966b-742">nxd_dns_server_remove</span><span class="sxs-lookup"><span data-stu-id="2966b-742">nxd_dns_server_remove</span></span>

<span data-ttu-id="2966b-743">Удаление DNS-сервера из списка клиента</span><span class="sxs-lookup"><span data-stu-id="2966b-743">Remove a DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="2966b-744">Прототип</span><span class="sxs-lookup"><span data-stu-id="2966b-744">Prototype</span></span>
```C
UINT nxd_dns_server_remove(NX_DNS *dns_ptr, NXD_ADDRESS *server_address);
```
### <a name="description"></a><span data-ttu-id="2966b-745">Описание</span><span class="sxs-lookup"><span data-stu-id="2966b-745">Description</span></span>

<span data-ttu-id="2966b-746">Эта служба удаляет DNS-сервер с указанным IP-адресом из списка клиента.</span><span class="sxs-lookup"><span data-stu-id="2966b-746">This service removes a DNS Server of the specified IP address from the Client list.</span></span> <span data-ttu-id="2966b-747">Входной IP-адрес принимает IPv4- и IPv6-адреса.</span><span class="sxs-lookup"><span data-stu-id="2966b-747">The input IP address accepts both IPv4 and IPv6 addresses.</span></span> <span data-ttu-id="2966b-748">После удаления сервера оставшиеся серверы перемещаются в списке на одну позицию индекса вниз для заполнения освобожденного слота.</span><span class="sxs-lookup"><span data-stu-id="2966b-748">After the server is removed, the remaining servers move down one index in the list to fill the vacated slot.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2966b-749">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2966b-749">Input Parameters</span></span>

- <span data-ttu-id="2966b-750">**dns_ptr**: указатель на блок управления DNS</span><span class="sxs-lookup"><span data-stu-id="2966b-750">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="2966b-751">**server_address**: указатель на данные NXD_ADDRESS DNS-сервера, содержащие IP-адрес сервера</span><span class="sxs-lookup"><span data-stu-id="2966b-751">**server_address** Pointer to DNS Server NXD_ADDRESS data containing server IP address.</span></span>

### <a name="return-values"></a><span data-ttu-id="2966b-752">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2966b-752">Return Values</span></span>

- <span data-ttu-id="2966b-753">**NX_SUCCESS** (0x00) — DNS-сервер успешно удален.</span><span class="sxs-lookup"><span data-stu-id="2966b-753">**NX_SUCCESS** (0x00) DNS Server successfully removed</span></span>
- <span data-ttu-id="2966b-754">**NX_DNS_SERVER_NOT_FOUND** (0xA9) — сервер отсутствует в списке клиента.</span><span class="sxs-lookup"><span data-stu-id="2966b-754">**NX_DNS_SERVER_NOT_FOUND** (0xA9) Server not in Client list</span></span>
- <span data-ttu-id="2966b-755">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) — введен адрес сервера со значением NULL.</span><span class="sxs-lookup"><span data-stu-id="2966b-755">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null server address input</span></span>
- <span data-ttu-id="2966b-756">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) — не удается обработать запись с отключенным IPv6.</span><span class="sxs-lookup"><span data-stu-id="2966b-756">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="2966b-757">NX_PTR_ERROR (0x07) — недопустимый указатель IP-адреса или DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-757">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="2966b-758">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="2966b-758">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="2966b-759">NX_DNS_INVALID_ADDRESS_TYPE (0xB2) — индекс указывает на недопустимый тип адреса (например, IPv6).</span><span class="sxs-lookup"><span data-stu-id="2966b-759">NX_DNS_INVALID_ADDRESS_TYPE (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2966b-760">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2966b-760">Allowed From</span></span>

<span data-ttu-id="2966b-761">Потоки</span><span class="sxs-lookup"><span data-stu-id="2966b-761">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2966b-762">Пример</span><span class="sxs-lookup"><span data-stu-id="2966b-762">Example</span></span>
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

## <a name="nx_dns_server_remove_all"></a><span data-ttu-id="2966b-763">nx_dns_server_remove_all</span><span class="sxs-lookup"><span data-stu-id="2966b-763">nx_dns_server_remove_all</span></span>

<span data-ttu-id="2966b-764">Удаление всех DNS-серверов из списка клиента</span><span class="sxs-lookup"><span data-stu-id="2966b-764">Remove all DNS Servers from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="2966b-765">Прототип</span><span class="sxs-lookup"><span data-stu-id="2966b-765">Prototype</span></span>
```C
UINT nx_dns_server_remove_all(NX_DNS *dns_ptr);
```
### <a name="description"></a><span data-ttu-id="2966b-766">Описание</span><span class="sxs-lookup"><span data-stu-id="2966b-766">Description</span></span>

<span data-ttu-id="2966b-767">Эта служба удаляет все DNS-серверы из списка клиента.</span><span class="sxs-lookup"><span data-stu-id="2966b-767">This service removes all DNS Servers from the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2966b-768">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2966b-768">Input Parameters</span></span>

- <span data-ttu-id="2966b-769">**dns_ptr**: указатель на блок управления DNS</span><span class="sxs-lookup"><span data-stu-id="2966b-769">**dns_ptr** Pointer to DNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="2966b-770">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2966b-770">Return Values</span></span>

- <span data-ttu-id="2966b-771">**NX_SUCCESS** (0x00) — DNS-серверы успешно удалены.</span><span class="sxs-lookup"><span data-stu-id="2966b-771">**NX_SUCCESS** (0x00) DNS Servers successfully removed</span></span>
- <span data-ttu-id="2966b-772">**NX_DNS_ERROR** (0xA0) — не удается получить мьютекс защиты.</span><span class="sxs-lookup"><span data-stu-id="2966b-772">**NX_DNS_ERROR** (0xA0) Unable to obtain protection mutex</span></span>
- <span data-ttu-id="2966b-773">NX_PTR_ERROR (0x07) — недопустимый указатель IP-адреса или DNS.</span><span class="sxs-lookup"><span data-stu-id="2966b-773">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="2966b-774">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="2966b-774">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2966b-775">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2966b-775">Allowed From</span></span>

<span data-ttu-id="2966b-776">Потоки</span><span class="sxs-lookup"><span data-stu-id="2966b-776">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2966b-777">Пример</span><span class="sxs-lookup"><span data-stu-id="2966b-777">Example</span></span>
```C
/* Remove all DNS Servers from the Client list. */
status =  nx_dns_server_remove_all(&my_dns);

/* If status is NX_SUCCESS all DNS Servers were successfully removed. */
```