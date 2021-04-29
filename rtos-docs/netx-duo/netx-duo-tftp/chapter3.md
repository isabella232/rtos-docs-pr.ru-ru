---
title: Глава 3. Описание служб ОСРВ Azure NetX Duo TFTP
description: Эта глава содержит описание всех служб NetX Duo TFTP, перечисленных ниже в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 56f0d8edb991fff6ae30b6411e375ace58c544f7
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814524"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-tftp-services"></a><span data-ttu-id="ef0d0-103">Глава 3. Описание служб ОСРВ Azure NetX Duo TFTP</span><span class="sxs-lookup"><span data-stu-id="ef0d0-103">Chapter 3 - Description of Azure RTOS NetX Duo TFTP services</span></span>

<span data-ttu-id="ef0d0-104">Эта глава содержит описание всех служб NetX Duo TFTP, перечисленных ниже в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-104">This chapter contains a description of all NetX Duo TFTP services (listed below) in alphabetic order.</span></span> <span data-ttu-id="ef0d0-105">Если не указано иное, все службы поддерживают взаимодействие по протоколам IPv6 и IPv4.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-105">Unless otherwise specified, all services support IPv6 and IPv4 communications.</span></span>

<span data-ttu-id="ef0d0-106">В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки API на предмет ошибок, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-106">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="ef0d0-107">**nxd_tftp_client_file_open**: *открытие файла клиента TFTP*.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-107">**nxd_tftp_client_file_open**: *Open TFTP client file*</span></span>

- <span data-ttu-id="ef0d0-108">**nxd_tftp_client_create**: *создание экземпляра клиента TFTP*.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-108">**nxd_tftp_client_create**: *Create a TFTP client instance*</span></span>

- <span data-ttu-id="ef0d0-109">**nxd_tftp_client_delete**: *удаление экземпляра клиента TFTP*.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-109">**nxd_tftp_client_delete**: *Delete a TFTP client instance*</span></span>

- <span data-ttu-id="ef0d0-110">**nxd_tftp_client_error_info_get**: *получение сведений об ошибке клиента*.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-110">**nxd_tftp_client_error_info_get**: *Get client error information*</span></span>

- <span data-ttu-id="ef0d0-111">**nxd_tftp_client_file_close**: *закрытие файла клиента*.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-111">**nxd_tftp_client_file_close**: *Close client file*</span></span>

- <span data-ttu-id="ef0d0-112">**nxd_tftp_client_file_open**: *открытие файла клиента*.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-112">**nxd_tftp_client_file_open**: *Open client file*</span></span>

- <span data-ttu-id="ef0d0-113">**nxd_tftp_client_file_read**: *чтение блока из файла клиента*.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-113">**nxd_tftp_client_file_read**: *Read a block from client file*</span></span>

- <span data-ttu-id="ef0d0-114">**nxd_tftp_client_file_write**: *запись блока в файл клиента*.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-114">**nxd_tftp_client_file_write**: *Write block to client file*</span></span>

- <span data-ttu-id="ef0d0-115">**nxd_tftp_client_packet_allocate**: *выделение пакета для записи в файл клиента*.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-115">**nxd_tftp_client_packet_allocate**: *Allocate packet for client file write*</span></span>

- <span data-ttu-id="ef0d0-116">**nxd_tftp_client_set_interface**: *настройка физического интерфейса для запросов TFTP*.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-116">**nxd_tftp_client_set_interface**: *Set the physical interface for TFTP requests*</span></span>

- <span data-ttu-id="ef0d0-117">**nxd_tftp_server_create**: *создание сервера TFTP*.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-117">**nxd_tftp_server_create**: *Create TFTP server*</span></span>

- <span data-ttu-id="ef0d0-118">**nxd_tftp_server_delete**: *удаление сервера TFTP*.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-118">**nxd_tftp_server_delete**: *Delete TFTP server*</span></span>

- <span data-ttu-id="ef0d0-119">**nxd_tftp_server_start**: *запуск сервера TFTP*.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-119">**nxd_tftp_server_start**: *Start TFTP server*</span></span>

- <span data-ttu-id="ef0d0-120">**nxd_tftp_server_stop**: *остановка сервера TFTP*.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-120">**nxd_tftp_server_stop**: *Stop TFTP server*</span></span>

> [!NOTE] 
> <span data-ttu-id="ef0d0-121">Эквиваленты всех перечисленных выше служб для протокола IPv4 доступны в клиенте и сервере NetX Duo TFTP, например *nx_tftp_server_create* и *nx_tftp_client_file_open*.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-121">The IPv4 equivalents of all the services listed above are available in NetX Duo TFTP Client and Server e.g. *nx_tftp_server_create* and *nx_tftp_client_file_open*.</span></span> <span data-ttu-id="ef0d0-122">На следующих страницах приведено только описание интерфейсов API для Duo (например, службы, начинающиеся с *nxd_* ).</span><span class="sxs-lookup"><span data-stu-id="ef0d0-122">Only the ‘Duo’ API descriptions, e.g. services beginning with *nxd_*, are provided in the following pages.</span></span> <span data-ttu-id="ef0d0-123">Если указаны входные данные NXD_ADDRESS\*, это означает эквивалентный вызов интерфейсов API IPv4 для входных данных типа ULONG.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-123">Where an NXD_ADDRESS \* input is specified, the IPv4 equivalent API calls for ULONG input.</span></span> <span data-ttu-id="ef0d0-124">В противном случае разницы в использовании API нет.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-124">Otherwise there is no difference in using the API.</span></span>

## <a name="nxd_tftp_client_create"></a><span data-ttu-id="ef0d0-125">nxd_tftp_client_create</span><span class="sxs-lookup"><span data-stu-id="ef0d0-125">nxd_tftp_client_create</span></span>

<span data-ttu-id="ef0d0-126">Создание экземпляра клиента TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-126">Create a TFTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ef0d0-127">Прототип</span><span class="sxs-lookup"><span data-stu-id="ef0d0-127">Prototype</span></span>

```C
UINT nxd_tftp_client_create(NX_TFTP_CLIENT *tftp_client_ptr,  
     CHAR *tftp_client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="ef0d0-128">Описание</span><span class="sxs-lookup"><span data-stu-id="ef0d0-128">Description</span></span>

<span data-ttu-id="ef0d0-129">Эта служба создает экземпляр клиента TFTP для созданного ранее экземпляра IP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-129">This service creates a TFTP Client instance for the previously created IP instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ef0d0-130">Приложение должно гарантировать, что указанный экземпляр IP и пул пакетов уже созданы.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-130">The application must make certain the supplied IP and packet pool are already created.</span></span> <span data-ttu-id="ef0d0-131">Кроме того, перед вызовом этой службы необходимо включить протокол UDP для экземпляра IP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-131">In addition, UDP must be enabled for the IP instance prior to calling this service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ef0d0-132">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ef0d0-132">Input Parameters</span></span>

- <span data-ttu-id="ef0d0-133">**client_ptr**: указатель на блок управления клиентом TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-133">**tftp_client_ptr** Pointer to TFTP Client control block.</span></span>

- <span data-ttu-id="ef0d0-134">**tftp_client_name**: имя этого экземпляра клиента TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-134">**tftp_client_name** Name of this TFTP Client instance</span></span>

- <span data-ttu-id="ef0d0-135">**ip_ptr**: указатель на созданный ранее экземпляр IP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-135">**ip_ptr** Pointer to previously created IP instance.</span></span>

- <span data-ttu-id="ef0d0-136">**pool_ptr**: указатель на пул пакетов экземпляра клиента TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-136">**pool_ptr** Pointer to packet pool TFTP Client instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ef0d0-137">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ef0d0-137">Return Values</span></span>

- <span data-ttu-id="ef0d0-138">**NX_SUCCESS** (0x00): экземпляр TFTP успешно создан.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-138">**NX_SUCCESS**(0x00) Successful TFTP create.</span></span>

- <span data-ttu-id="ef0d0-139">**NX_TFTP_INVALID_IP_VERSION** (0X0C): недопустимая или неподдерживаемая версия протокола IP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-139">**NX_TFTP_INVALID_IP_VERSION** (0x0C) Invalid or unsupported IP version</span></span>

- <span data-ttu-id="ef0d0-140">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08): получен недопустимый IP-адрес сервера.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-140">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Invalid Server IP address received</span></span>

- <span data-ttu-id="ef0d0-141">**NX_TFTP_NO_ACK_RECEIVED** (0x09): сообщение ACK от сервера не получено.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-141">**NX_TFTP_NO_ACK_RECEIVED** (0x09) Server ACK not received</span></span>

- <span data-ttu-id="ef0d0-142">NX_PTR_ERROR (0x16): недопустимый указатель на IP-адрес, пул или экземпляр TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-142">NX_PTR_ERROR (0x16) Invalid IP, pool, or TFTP pointer.</span></span>

- <span data-ttu-id="ef0d0-143">NX_INVALID_PARAMETERS (0x4D): недопустимые входные данные, отличные от указателя.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-143">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

- <span data-ttu-id="ef0d0-144">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-144">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ef0d0-145">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ef0d0-145">Allowed From</span></span>

<span data-ttu-id="ef0d0-146">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="ef0d0-146">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="ef0d0-147">Например, .</span><span class="sxs-lookup"><span data-stu-id="ef0d0-147">Example</span></span>

```C
/* Create a TFTP Client instance. */
status =  nxd_tftp_client_create(&my_tftp_client, “My TFTP Client”, 
                                                    &my_ip, &pool_ptr);

/* If status is NX_SUCCESS a TFTP Client instance was successfully
   created. */
```

## <a name="nxd_tftp_client_delete"></a><span data-ttu-id="ef0d0-148">nxd_tftp_client_delete</span><span class="sxs-lookup"><span data-stu-id="ef0d0-148">nxd_tftp_client_delete</span></span>

<span data-ttu-id="ef0d0-149">Удаление экземпляра клиента TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-149">Delete a TFTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ef0d0-150">Прототип</span><span class="sxs-lookup"><span data-stu-id="ef0d0-150">Prototype</span></span>

```C
UINT nxd_tftp_client_delete(NX_TFTP_CLIENT *tftp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="ef0d0-151">Описание</span><span class="sxs-lookup"><span data-stu-id="ef0d0-151">Description</span></span>

<span data-ttu-id="ef0d0-152">Эта служба удаляет созданный ранее экземпляр клиента TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-152">This service deletes a previously created TFTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ef0d0-153">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ef0d0-153">Input Parameters</span></span>

- <span data-ttu-id="ef0d0-154">**tftp_client_ptr**: указатель на созданный ранее экземпляр клиента TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-154">**tftp_client_ptr** Pointer to previously created TFTP client instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ef0d0-155">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ef0d0-155">Return Values</span></span>

- <span data-ttu-id="ef0d0-156">**NX_SUCCESS** (0x00): клиент TFTP успешно удален.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-156">**NX_SUCCESS** (0x00) Successful TFTP Client delete.</span></span>

- <span data-ttu-id="ef0d0-157">NX_PTR_ERROR (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-157">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="ef0d0-158">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-158">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ef0d0-159">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ef0d0-159">Allowed From</span></span>

<span data-ttu-id="ef0d0-160">Потоки</span><span class="sxs-lookup"><span data-stu-id="ef0d0-160">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ef0d0-161">Например, .</span><span class="sxs-lookup"><span data-stu-id="ef0d0-161">Example</span></span>

```C
/* Delete a TFTP Client instance. */
status =  nxd_tftp_client_delete(&my_tftp_client);

/* If status is NX_SUCCESS the TFTP Client instance was successfully
   deleted. */
```

## <a name="nxd_tftp_client_error_info_get"></a><span data-ttu-id="ef0d0-162">nxd_tftp_client_error_info_get</span><span class="sxs-lookup"><span data-stu-id="ef0d0-162">nxd_tftp_client_error_info_get</span></span>

<span data-ttu-id="ef0d0-163">Получение сведений об ошибке клиента.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-163">Get client error information</span></span>

### <a name="prototype"></a><span data-ttu-id="ef0d0-164">Прототип</span><span class="sxs-lookup"><span data-stu-id="ef0d0-164">Prototype</span></span>

```C
UINT nxd_tftp_client_error_info_get(NX_TFTP_CLIENT *tftp_client_ptr,
                        UINT *error_code, CHAR **error_string);
```

### <a name="description"></a><span data-ttu-id="ef0d0-165">Описание</span><span class="sxs-lookup"><span data-stu-id="ef0d0-165">Description</span></span>

<span data-ttu-id="ef0d0-166">Эта служба возвращает последний полученный код ошибки и задает указатель на внутреннюю строку ошибки клиента.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-166">This service returns the last error code received and sets the pointer to the client’s internal error string.</span></span> <span data-ttu-id="ef0d0-167">В описании ошибки пользователь может просмотреть последнюю ошибку, отправленную сервером.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-167">In error conditions, the user can view the last error sent by the server.</span></span> <span data-ttu-id="ef0d0-168">Строка ошибки со значением NULL указывает на отсутствие ошибки.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-168">A null error string indicates no error is present.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ef0d0-169">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ef0d0-169">Input Parameters</span></span>

- <span data-ttu-id="ef0d0-170">**tftp_client_ptr**: указатель на созданный ранее экземпляр клиента TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-170">**tftp_client_ptr** Pointer to previously created TFTP Client instance.</span></span>

- <span data-ttu-id="ef0d0-171">**error_code**: указатель на область назначения для кода ошибки.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-171">**error_code** Pointer to destination area for error code</span></span>

- <span data-ttu-id="ef0d0-172">**error_string**: указатель на место назначения для строки ошибки.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-172">**error_string** Pointer to destination for error string</span></span>

### <a name="return-values"></a><span data-ttu-id="ef0d0-173">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ef0d0-173">Return Values</span></span>

- <span data-ttu-id="ef0d0-174">**NX_SUCCESS** (0X00): сведения об ошибке TFTP успешно получены.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-174">**NX_SUCCESS** (0x00) Successful TFTP error info get.</span></span>  

- <span data-ttu-id="ef0d0-175">NX_PTR_ERROR (0x16): недопустимый указатель на клиент TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-175">NX_PTR_ERROR (0x16) Invalid TFTP Client pointer.</span></span>

- <span data-ttu-id="ef0d0-176">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-176">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ef0d0-177">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ef0d0-177">Allowed From</span></span>

<span data-ttu-id="ef0d0-178">Потоки</span><span class="sxs-lookup"><span data-stu-id="ef0d0-178">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ef0d0-179">Например, .</span><span class="sxs-lookup"><span data-stu-id="ef0d0-179">Example</span></span>

```C
/* Get error information for client. */
status =  nxd_tftp_client_error_info_get(&my_tftp_client, &error_code,
                    &error_string_ptr);

/* If status is NX_SUCCESS the error code and error string are available. */
```

## <a name="nxd_tftp_client_file_close"></a><span data-ttu-id="ef0d0-180">nxd_tftp_client_file_close</span><span class="sxs-lookup"><span data-stu-id="ef0d0-180">nxd_tftp_client_file_close</span></span>

<span data-ttu-id="ef0d0-181">Закрытие файла клиента.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-181">Close client file</span></span>

### <a name="prototype"></a><span data-ttu-id="ef0d0-182">Прототип</span><span class="sxs-lookup"><span data-stu-id="ef0d0-182">Prototype</span></span>

```C
UINT nxd_tftp_client_file_close(NX_TFTP_CLIENT *tftp_client_ptr,
                                    UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="ef0d0-183">Описание</span><span class="sxs-lookup"><span data-stu-id="ef0d0-183">Description</span></span>

<span data-ttu-id="ef0d0-184">Эта служба закрывает файл, открытый ранее этим экземпляром клиента TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-184">This service closes the previously opened file by this TFTP Client instance.</span></span> <span data-ttu-id="ef0d0-185">Экземпляр клиента TFTP может одновременно открыть только один файл.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-185">A TFTP Client instance is allowed to have only one file open at a time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ef0d0-186">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ef0d0-186">Input Parameters</span></span>

- <span data-ttu-id="ef0d0-187">**tftp_client_ptr**: указатель на созданный ранее экземпляр клиента TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-187">**tftp_client_ptr** Pointer to previously created TFTP Client instance.</span></span>

- <span data-ttu-id="ef0d0-188">**ip_type**: позволяет указать, какой протокол IP использовать.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-188">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="ef0d0-189">Допустимые значения: IPv4 (4) или IPv6 (6).</span><span class="sxs-lookup"><span data-stu-id="ef0d0-189">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="ef0d0-190">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ef0d0-190">Return Values</span></span>

- <span data-ttu-id="ef0d0-191">**NX_SUCCESS** (0x00): файл TFTP успешно закрыт.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-191">**NX_SUCCESS** (0x00) Successful TFTP file close.</span></span>

- <span data-ttu-id="ef0d0-192">NX_PTR_ERROR (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-192">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="ef0d0-193">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-193">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="ef0d0-194">NX_INVALID_PARAMETERS (0x4D): недопустимые входные данные, отличные от указателя.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-194">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ef0d0-195">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ef0d0-195">Allowed From</span></span>

<span data-ttu-id="ef0d0-196">Потоки</span><span class="sxs-lookup"><span data-stu-id="ef0d0-196">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ef0d0-197">Например, .</span><span class="sxs-lookup"><span data-stu-id="ef0d0-197">Example</span></span>

```C
/* Close the previously opened file associated with “my_client”. */
status =  nxd_tftp_client_file_close(&my_tftp_client);

/* If status is NX_SUCCESS the TFTP file is closed. */
```

## <a name="nx_tftp_client_file_open"></a><span data-ttu-id="ef0d0-198">nx_tftp_client_file_open</span><span class="sxs-lookup"><span data-stu-id="ef0d0-198">nx_tftp_client_file_open</span></span>

<span data-ttu-id="ef0d0-199">Открытие файла клиента TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-199">Open TFTP client file</span></span>

### <a name="prototype"></a><span data-ttu-id="ef0d0-200">Прототип</span><span class="sxs-lookup"><span data-stu-id="ef0d0-200">Prototype</span></span>

```C
UINT nx_tftp_client_file_open(NX_TFTP_CLIENT *tftp_client_ptr, 
            CHAR *file_name, NXD_ADDRESS *server_ip_address, UINT 
            open_type, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ef0d0-201">Описание</span><span class="sxs-lookup"><span data-stu-id="ef0d0-201">Description</span></span>

<span data-ttu-id="ef0d0-202">Эта служба пытается открыть указанный файл на сервере TFTP по заданному IP-адресу.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-202">This service attempts to open the specified file on the TFTP Server at the specified IP address.</span></span> <span data-ttu-id="ef0d0-203">Файл будет открыт для чтения или записи.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-203">The file will be opened for either reading or writing.</span></span> 

> [!NOTE] 
> <span data-ttu-id="ef0d0-204">Это ограничение относится только к пакетам IPv4 и предназначено для поддержки приложений NetX TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-204">This is limited to IPv4 packets only, and is intended for supporting NetX TFTP applications.</span></span> <span data-ttu-id="ef0d0-205">Разработчикам рекомендуется перенести свои приложения для использование эквивалентной службы Duo, *nxd_tftp_client_file_open*.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-205">Developers are encouraged to port their applications to using equivalent “duo” service *nxd_tftp_client_file_open.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ef0d0-206">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ef0d0-206">Input Parameters</span></span>

- <span data-ttu-id="ef0d0-207">**tftp_client_ptr**: указатель на блок управления TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-207">**tftp_client_ptr** Pointer to TFTP control block.</span></span>

- <span data-ttu-id="ef0d0-208">**file_name**: имя файла ASCII, оканчивающееся нулевым символом, и соответствующие сведения о пути.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-208">**file_name** ASCII file name, NULL-terminated and with appropriate path information.</span></span>

- <span data-ttu-id="ef0d0-209">**server_ip_address**: адрес сервера TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-209">**server_ip_address** Server TFTP address.</span></span>

- <span data-ttu-id="ef0d0-210">**open_type**: тип запроса на открытие:</span><span class="sxs-lookup"><span data-stu-id="ef0d0-210">**open_type** Type of open request, either:</span></span>

  <span data-ttu-id="ef0d0-211">**NX_TFTP_OPEN_FOR_READ** (0x01)</span><span class="sxs-lookup"><span data-stu-id="ef0d0-211">**NX_TFTP_OPEN_FOR_READ** (0x01)</span></span>

  <span data-ttu-id="ef0d0-212">**NX_TFTP_OPEN_FOR_WRITE** (0x02)</span><span class="sxs-lookup"><span data-stu-id="ef0d0-212">**NX_TFTP_OPEN_FOR_WRITE** (0x02)</span></span>

- <span data-ttu-id="ef0d0-213">**wait_option**: определяет, как долго служба будет ожидать открытия файла клиента TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-213">**wait_option** Defines how long the service will wait for the TFTP Client file open.</span></span> <span data-ttu-id="ef0d0-214">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="ef0d0-214">The wait options are defined as follows:</span></span>

  <span data-ttu-id="ef0d0-215">**значение времени ожидания** (от 0X00000001 до 0xFFFFFFFE);</span><span class="sxs-lookup"><span data-stu-id="ef0d0-215">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="ef0d0-216">**TX_WAIT_FOREVER** (0xFFFFFFFF).</span><span class="sxs-lookup"><span data-stu-id="ef0d0-216">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span> 
  
  <span data-ttu-id="ef0d0-217">Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока сервер TFTP не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-217">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a TFTP Server responds to the request.</span></span> 
  
  <span data-ttu-id="ef0d0-218">Числовое значение (от 1 до 0xFFFFFFFE) указывает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа сервера TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-218">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the TFTP server response.</span></span>

- <span data-ttu-id="ef0d0-219">**ip_type**: позволяет указать, какой протокол IP использовать.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-219">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="ef0d0-220">Допустимые значения: IPv4 (4) или IPv6 (6).</span><span class="sxs-lookup"><span data-stu-id="ef0d0-220">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="ef0d0-221">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ef0d0-221">Return Values</span></span>

- <span data-ttu-id="ef0d0-222">**NX_SUCCESS** (0x00): файл клиента успешно открыт.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-222">**NX_SUCCESS** (0x00) Successful Client file open</span></span>

- <span data-ttu-id="ef0d0-223">**NX_TFTP_NOT_CLOSED** (0xC3): клиент уже открыл файл.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-223">**NX_TFTP_NOT_CLOSED** (0xC3) Client already has file open</span></span>

- <span data-ttu-id="ef0d0-224">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08): получен недопустимый адрес сервера.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-224">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="ef0d0-225">**NX_TFTP_NO_ACK_RECEIVED** (0x09): не получено сообщение ACK от сервера.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-225">**NX_TFTP_NO_ACK_RECEIVED** (0x09) No ACK received from server</span></span>

- <span data-ttu-id="ef0d0-226">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08): получен недопустимый IP-адрес сервера.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-226">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Invalid Server IP received</span></span>

- <span data-ttu-id="ef0d0-227">**NX_TFTP_CODE_ERROR** (0X05): получен код ошибки.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-227">**NX_TFTP_CODE_ERROR** (0x05) Received error code</span></span>

- <span data-ttu-id="ef0d0-228">NX_PTR_ERROR (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-228">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="ef0d0-229">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-229">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="ef0d0-230">NX_IP_ADDRESS_ERROR (0x21): недопустимый IP-адрес сервера.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-230">NX_IP_ADDRESS_ERROR (0x21) Invalid Server IP address</span></span>

- <span data-ttu-id="ef0d0-231">NX_OPTION_ERROR (0x0A): недопустимый тип операции открытия.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-231">NX_OPTION_ERROR (0x0A) Invalid open type</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ef0d0-232">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ef0d0-232">Allowed From</span></span>

<span data-ttu-id="ef0d0-233">Потоки</span><span class="sxs-lookup"><span data-stu-id="ef0d0-233">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ef0d0-234">Например, .</span><span class="sxs-lookup"><span data-stu-id="ef0d0-234">Example</span></span>

```C
/* Define the TFTP server address. */
NXD_ADDRESS server_ip_address;

server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server _ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server _ip_address.nxd_ip_address.v6[1] = 0xf101;
server _ip_address.nxd_ip_address.v6[2] = 0;
server _ip_address.nxd_ip_address.v6[3] = 0x101;

/* Open file “test.txt” for reading on the TFTP Server. */
status =  nxd_tftp_client_file_open(&my_tftp_client, “test.txt”,
        & server_ip_address, NX_TFTP_OPEN_FOR_READ, 200);

/* If status is NX_SUCCESS the “test.txt” file is now open for reading. */
```

## <a name="nxd_tftp_client_file_open"></a><span data-ttu-id="ef0d0-235">nxd_tftp_client_file_open</span><span class="sxs-lookup"><span data-stu-id="ef0d0-235">nxd_tftp_client_file_open</span></span>

<span data-ttu-id="ef0d0-236">Открытие файла клиента TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-236">Open TFTP client file</span></span>

### <a name="prototype"></a><span data-ttu-id="ef0d0-237">Прототип</span><span class="sxs-lookup"><span data-stu-id="ef0d0-237">Prototype</span></span>

```C
UINT nxd_tftp_client_file_open(NX_TFTP_CLIENT *tftp_client_ptr,
        CHAR *file_name, NXD_ADDRESS *server_ip_address, UINT 
        open_type, ULONG wait_option, UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="ef0d0-238">Описание</span><span class="sxs-lookup"><span data-stu-id="ef0d0-238">Description</span></span>

<span data-ttu-id="ef0d0-239">Эта служба пытается открыть указанный файл на сервере TFTP по заданному IPv6-адресу.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-239">This service attempts to open the specified file on the TFTP Server at the specified IPv6 address.</span></span> <span data-ttu-id="ef0d0-240">Файл будет открыт для чтения или записи.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-240">The file will be opened for either reading or writing.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ef0d0-241">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ef0d0-241">Input Parameters</span></span>

- <span data-ttu-id="ef0d0-242">**tftp_client_ptr**: указатель на блок управления TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-242">**tftp_client_ptr** Pointer to TFTP control block.</span></span>

- <span data-ttu-id="ef0d0-243">**file_name**: имя файла ASCII, оканчивающееся нулевым символом, и соответствующие сведения о пути.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-243">**file_name** ASCII file name, NULL-terminated and with appropriate path information.</span></span>

- <span data-ttu-id="ef0d0-244">**server_ip_address**: адрес сервера TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-244">**server_ip_address** Server TFTP address.</span></span>

- <span data-ttu-id="ef0d0-245">**open_type**: тип запроса на открытие:</span><span class="sxs-lookup"><span data-stu-id="ef0d0-245">**open_type** Type of open request, either:</span></span>

  <span data-ttu-id="ef0d0-246">**NX_TFTP_OPEN_FOR_READ** (0x01)</span><span class="sxs-lookup"><span data-stu-id="ef0d0-246">**NX_TFTP_OPEN_FOR_READ** (0x01)</span></span>

  <span data-ttu-id="ef0d0-247">**NX_TFTP_OPEN_FOR_WRITE** (0x02)</span><span class="sxs-lookup"><span data-stu-id="ef0d0-247">**NX_TFTP_OPEN_FOR_WRITE** (0x02)</span></span>

- <span data-ttu-id="ef0d0-248">**wait_option**: определяет, как долго служба будет ожидать открытия файла клиента TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-248">**wait_option** Defines how long the service will wait for the TFTP Client file open.</span></span> <span data-ttu-id="ef0d0-249">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="ef0d0-249">The wait options are defined as follows:</span></span>

  <span data-ttu-id="ef0d0-250">**значение времени ожидания** (от 0X00000001 до 0xFFFFFFFE);</span><span class="sxs-lookup"><span data-stu-id="ef0d0-250">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="ef0d0-251">**TX_WAIT_FOREVER** (0xFFFFFFFF).</span><span class="sxs-lookup"><span data-stu-id="ef0d0-251">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

  <span data-ttu-id="ef0d0-252">Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока сервер TFTP не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-252">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a TFTP Server responds to the request.</span></span>

  <span data-ttu-id="ef0d0-253">Числовое значение (от 1 до 0xFFFFFFFE) указывает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа сервера TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-253">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the TFTP server response.</span></span>

- <span data-ttu-id="ef0d0-254">**ip_type**: позволяет указать, какой протокол IP использовать.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-254">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="ef0d0-255">Допустимые значения: IPv4 (4) или IPv6 (6).</span><span class="sxs-lookup"><span data-stu-id="ef0d0-255">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="ef0d0-256">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ef0d0-256">Return Values</span></span>

- <span data-ttu-id="ef0d0-257">**NX_SUCCESS** (0x00): файл клиента успешно открыт.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-257">**NX_SUCCESS** (0x00) Successful Client file open</span></span>

- <span data-ttu-id="ef0d0-258">**NX_TFTP_NOT_CLOSED** (0xC3): клиент уже открыл файл.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-258">**NX_TFTP_NOT_CLOSED** (0xC3) Client already has file open</span></span>

- <span data-ttu-id="ef0d0-259">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08): получен недопустимый адрес сервера.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-259">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="ef0d0-260">**NX_TFTP_NO_ACK_RECEIVED** (0x09): не получено сообщение ACK от сервера.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-260">**NX_TFTP_NO_ACK_RECEIVED** (0x09) No ACK received from server</span></span>

- <span data-ttu-id="ef0d0-261">**NX_TFTP_INVALID_IP_VERSION** (0X0C): недопустимая версия протокола IP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-261">**NX_TFTP_INVALID_IP_VERSION** (0x0C) Invalid IP version</span></span>

- <span data-ttu-id="ef0d0-262">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08): получен недопустимый IP-адрес сервера.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-262">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Invalid Server IP received</span></span>

- <span data-ttu-id="ef0d0-263">**NX_TFTP_CODE_ERROR** (0X05): получен код ошибки.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-263">**NX_TFTP_CODE_ERROR** (0x05) Received error code</span></span>

- <span data-ttu-id="ef0d0-264">NX_PTR_ERROR (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-264">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="ef0d0-265">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-265">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="ef0d0-266">NX_IP_ADDRESS_ERROR (0x21): недопустимый IP-адрес сервера.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-266">NX_IP_ADDRESS_ERROR (0x21) Invalid Server IP address</span></span>

- <span data-ttu-id="ef0d0-267">NX_OPTION_ERROR (0x0A): недопустимый тип операции открытия.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-267">NX_OPTION_ERROR (0x0A) Invalid open type</span></span>

- <span data-ttu-id="ef0d0-268">NX_INVALID_PARAMETERS (0x4D): недопустимые входные данные, отличные от указателя.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-268">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ef0d0-269">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ef0d0-269">Allowed From</span></span>

<span data-ttu-id="ef0d0-270">Потоки</span><span class="sxs-lookup"><span data-stu-id="ef0d0-270">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ef0d0-271">Например, .</span><span class="sxs-lookup"><span data-stu-id="ef0d0-271">Example</span></span>

```C
/* Define the TFTP server address. */
NXD_ADDRESS server_ip_address;

server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server _ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server _ip_address.nxd_ip_address.v6[1] = 0xf101;
server _ip_address.nxd_ip_address.v6[2] = 0;
server _ip_address.nxd_ip_address.v6[3] = 0x101;

/* Open file “test.txt” for reading on the TFTP Server. */
status =  nxd_tftp_client_file_open(&my_tftp_client, “test.txt”,
                & server_ip_address, NX_TFTP_OPEN_FOR_READ, 200);

/* If status is NX_SUCCESS the “test.txt” file is now open for reading. */
```

## <a name="nxd_tftp_client_file_read"></a><span data-ttu-id="ef0d0-272">nxd_tftp_client_file_read</span><span class="sxs-lookup"><span data-stu-id="ef0d0-272">nxd_tftp_client_file_read</span></span>

<span data-ttu-id="ef0d0-273">Чтение блока из файла клиента.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-273">Read a block from client file</span></span>

### <a name="prototype"></a><span data-ttu-id="ef0d0-274">Прототип</span><span class="sxs-lookup"><span data-stu-id="ef0d0-274">Prototype</span></span>

```C
UINT nxd_tftp_client_file_read(NX_TFTP_CLIENT *tftp_client_ptr,
                        NX_PACKET **packet_ptr, ULONG wait_option,
                        UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="ef0d0-275">Описание</span><span class="sxs-lookup"><span data-stu-id="ef0d0-275">Description</span></span>

<span data-ttu-id="ef0d0-276">Эта служба считывает блок размером в 512 байт из открытого ранее файла клиента TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-276">This service reads a 512-byte block from the previously opened TFTP Client file.</span></span> <span data-ttu-id="ef0d0-277">Блок, содержащий менее 512 байт, означает конец файла.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-277">A block containing fewer than 512 bytes signals the end of the file.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ef0d0-278">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ef0d0-278">Input Parameters</span></span>

- <span data-ttu-id="ef0d0-279">**client_ptr**: указатель на блок управления клиентом TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-279">**tftp_client_ptr** Pointer to TFTP Client control block.</span></span>

- <span data-ttu-id="ef0d0-280">**packet_ptr**: место назначения для пакета, содержащего блок, считанный из файла.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-280">**packet_ptr** Destination for packet containing the block read from the file.</span></span>

- <span data-ttu-id="ef0d0-281">**wait_option**: определяет, как долго служба будет ожидать завершения чтения.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-281">**wait_option** Defines how long the service will wait for the read to complete.</span></span> <span data-ttu-id="ef0d0-282">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="ef0d0-282">The wait options are defined as follows:</span></span>

  <span data-ttu-id="ef0d0-283">**значение времени ожидания** (от 0X00000001 до 0xFFFFFFFE);</span><span class="sxs-lookup"><span data-stu-id="ef0d0-283">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="ef0d0-284">**TX_WAIT_FOREVER** (0xFFFFFFFF).</span><span class="sxs-lookup"><span data-stu-id="ef0d0-284">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

  <span data-ttu-id="ef0d0-285">Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока сервер TFTP не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-285">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the TFTP Server responds to the request.</span></span>

  <span data-ttu-id="ef0d0-286">Числовое значение (от 1 до 0xFFFFFFFE) указывает максимальное количество тактов таймера для ожидания в состоянии приостановки, пока сервер TFTP не отправит блок из файла.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-286">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the TFTP server to send a block of the file.</span></span>

- <span data-ttu-id="ef0d0-287">**ip_type**: позволяет указать, какой протокол IP использовать.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-287">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="ef0d0-288">Допустимые значения: IPv4 (4) или IPv6 (6).</span><span class="sxs-lookup"><span data-stu-id="ef0d0-288">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="ef0d0-289">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ef0d0-289">Return Values</span></span>

- <span data-ttu-id="ef0d0-290">**NX_SUCCESS** (0x00): блок успешно считан из файла клиента.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-290">**NX_SUCCESS** (0x00) Successful Client block read</span></span>

- <span data-ttu-id="ef0d0-291">**NX_TFTP_NOT_OPEN** (0xC3): указанный файл клиента не открыт для чтения.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-291">**NX_TFTP_NOT_OPEN** (0xC3) Specified Client file is not open for reading</span></span>

- <span data-ttu-id="ef0d0-292">**NX_NO_PACKET** (0X01): сервер не передал какие-либо пакеты.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-292">**NX_NO_PACKET** (0x01) No Packet received from Server.</span></span>

- <span data-ttu-id="ef0d0-293">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08): получен недопустимый адрес сервера.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-293">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="ef0d0-294">**NX_TFTP_NO_ACK_RECEIVED** (0x09): не получено сообщение ACK от сервера.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-294">**NX_TFTP_NO_ACK_RECEIVED** (0x09) No ACK received from Server</span></span>

- <span data-ttu-id="ef0d0-295">**NX_TFTP_END_OF_FILE** (0xC5): обнаружен конец файла (не ошибка).</span><span class="sxs-lookup"><span data-stu-id="ef0d0-295">**NX_TFTP_END_OF_FILE** (0xC5) End of file detected (not an error).</span></span>

- <span data-ttu-id="ef0d0-296">**NX_TFTP_INVALID_IP_VERSION** (0X0C): недопустимая версия протокола IP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-296">**NX_TFTP_INVALID_IP_VERSION** (0x0C) Invalid IP version</span></span>

- <span data-ttu-id="ef0d0-297">**NX_TFTP_CODE_ERROR** (0X05): получен код ошибки.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-297">**NX_TFTP_CODE_ERROR** (0x05) Received error code</span></span>

- <span data-ttu-id="ef0d0-298">**NX_TFTP_FAILED** (0xC2): получен неизвестный код TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-298">**NX_TFTP_FAILED** (0xC2) Unknown TFTP code received</span></span>

- <span data-ttu-id="ef0d0-299">**NX_TFTP_INVALID_BLOCK_NUMBER** (0x0A): получен недопустимый номер блока.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-299">**NX_TFTP_INVALID_BLOCK_NUMBER** (0x0A) Invalid block number received</span></span>

- <span data-ttu-id="ef0d0-300">NX_PTR_ERROR (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-300">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="ef0d0-301">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-301">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="ef0d0-302">NX_INVALID_PARAMETERS (0x4D): недопустимые входные данные, отличные от указателя.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-302">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ef0d0-303">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ef0d0-303">Allowed From</span></span>

<span data-ttu-id="ef0d0-304">Потоки</span><span class="sxs-lookup"><span data-stu-id="ef0d0-304">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ef0d0-305">Например, .</span><span class="sxs-lookup"><span data-stu-id="ef0d0-305">Example</span></span>

```C
/* Read a block from a previously opened file of “my_client”. */
status =  nxd_tftp_client_file_read(&my_tftp_client, &return_packet_ptr, 200);

/* If status is NX_SUCCESS a block of the TFTP file is in the payload of
   “return_packet_ptr”. */
```

## <a name="nxd_tftp_client_file_write"></a><span data-ttu-id="ef0d0-306">nxd_tftp_client_file_write</span><span class="sxs-lookup"><span data-stu-id="ef0d0-306">nxd_tftp_client_file_write</span></span>

<span data-ttu-id="ef0d0-307">Запись блока в файл клиента.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-307">Write a block to Client file</span></span>

### <a name="prototype"></a><span data-ttu-id="ef0d0-308">Прототип</span><span class="sxs-lookup"><span data-stu-id="ef0d0-308">Prototype</span></span>

```C
UINT nxd_tftp_client_file_write(NX_TFTP_CLIENT *tftp_client_ptr,
            NX_PACKET *packet_ptr, ULONG wait_option, UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="ef0d0-309">Описание</span><span class="sxs-lookup"><span data-stu-id="ef0d0-309">Description</span></span>

<span data-ttu-id="ef0d0-310">Эта служба записывает блок размером в 512 байт в открытый ранее файл клиента TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-310">This service writes a 512-byte block to the previously opened TFTP Client file.</span></span> <span data-ttu-id="ef0d0-311">Если указан блок, содержащий менее 512 байт, это означает конец файла.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-311">Specifying a block containing fewer than 512 bytes signals the end of the file.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ef0d0-312">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ef0d0-312">Input Parameters</span></span>

- <span data-ttu-id="ef0d0-313">**client_ptr**: указатель на блок управления клиентом TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-313">**tftp_client_ptr** Pointer to TFTP Client control block.</span></span>

- <span data-ttu-id="ef0d0-314">**packet_ptr**: пакет, содержащий блок для записи в файл.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-314">**packet_ptr** Packet containing the block to write to the file.</span></span>

- <span data-ttu-id="ef0d0-315">**wait_option**: определяет, как долго служба будет ожидать завершения записи.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-315">**wait_option** Defines how long the service will wait for the write to complete.</span></span> <span data-ttu-id="ef0d0-316">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="ef0d0-316">The wait options are defined as follows:</span></span>

  <span data-ttu-id="ef0d0-317">**значение времени ожидания** (от 0X00000001 до 0xFFFFFFFE);</span><span class="sxs-lookup"><span data-stu-id="ef0d0-317">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="ef0d0-318">**TX_WAIT_FOREVER** (0xFFFFFFFF).</span><span class="sxs-lookup"><span data-stu-id="ef0d0-318">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

  <span data-ttu-id="ef0d0-319">Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока сервер TFTP не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-319">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the TFTP Server responds to the request.</span></span>
 
  <span data-ttu-id="ef0d0-320">Числовое значение (от 1 до 0xFFFFFFFE) указывает максимальное количество тактов таймера для ожидания в состоянии приостановки, пока сервер TFTP не отправит сообщение ACK для запроса на запись.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-320">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the TFTP server to send an ACK for the write request.</span></span>

- <span data-ttu-id="ef0d0-321">**ip_type**: позволяет указать, какой протокол IP использовать.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-321">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="ef0d0-322">Допустимые значения: IPv4 (4) или IPv6 (6).</span><span class="sxs-lookup"><span data-stu-id="ef0d0-322">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="ef0d0-323">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ef0d0-323">Return Values</span></span>

- <span data-ttu-id="ef0d0-324">**NX_SUCCESS** (0x00): блок успешно записан в файл клиента.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-324">**NX_SUCCESS** (0x00) Successful Client block write</span></span>

- <span data-ttu-id="ef0d0-325">**NX_TFTP_NOT_OPEN** (0xC3): указанный файл клиента не открыт для записи.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-325">**NX_TFTP_NOT_OPEN** (0xC3) Specified Client file is not open for writing</span></span>

- <span data-ttu-id="ef0d0-326">**NX_TFTP_TIMEOUT** (0XC1): время ожидания сообщения ACK от сервера.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-326">**NX_TFTP_TIMEOUT** (0xC1) Timeout waiting for Server ACK</span></span>

- <span data-ttu-id="ef0d0-327">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08): получен недопустимый адрес сервера.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-327">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="ef0d0-328">**NX_TFTP_NO_ACK_RECEIVED** (0x09): не получено сообщение ACK от сервера.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-328">**NX_TFTP_NO_ACK_RECEIVED** (0x09) No ACK received from server</span></span>

- <span data-ttu-id="ef0d0-329">**NX_TFTP_INVALID_IP_VERSION** (0X0C): недопустимая версия протокола IP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-329">**NX_TFTP_INVALID_IP_VERSION** (0x0C) Invalid IP version</span></span>

- <span data-ttu-id="ef0d0-330">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08): получен недопустимый адрес сервера.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-330">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="ef0d0-331">**NX_TFTP_CODE_ERROR** (0X05): получен код ошибки.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-331">**NX_TFTP_CODE_ERROR** (0x05) Received error code</span></span>

- <span data-ttu-id="ef0d0-332">NX_PTR_ERROR (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-332">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="ef0d0-333">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-333">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="ef0d0-334">NX_INVALID_PARAMETERS (0x4D): недопустимые входные данные, отличные от указателя.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-334">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ef0d0-335">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ef0d0-335">Allowed From</span></span>

<span data-ttu-id="ef0d0-336">Потоки</span><span class="sxs-lookup"><span data-stu-id="ef0d0-336">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ef0d0-337">Например, .</span><span class="sxs-lookup"><span data-stu-id="ef0d0-337">Example</span></span>

```C
/* Write a block to the previously opened file of “my_client”. */
status =  nxd_tftp_client_file_write(&my_tftp_client, packet_ptr, 200);

/* If status is NX_SUCCESS the block in the payload of “packet_ptr” was 
   written to the TFTP file opened by “my_client”. */
```

## <a name="nxd_tftp_client_packet_allocate"></a><span data-ttu-id="ef0d0-338">nxd_tftp_client_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="ef0d0-338">nxd_tftp_client_packet_allocate</span></span>

<span data-ttu-id="ef0d0-339">Выделение пакета для записи в файл клиента.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-339">Allocate packet for Client file write</span></span>

### <a name="prototype"></a><span data-ttu-id="ef0d0-340">Прототип</span><span class="sxs-lookup"><span data-stu-id="ef0d0-340">Prototype</span></span>

```C
UINT nxd_tftp_client_packet_allocate(NX_PACKET_POOL *pool_ptr,
                        NX_PACKET **packet_ptr, ULONG wait_option,
                        UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="ef0d0-341">Описание</span><span class="sxs-lookup"><span data-stu-id="ef0d0-341">Description</span></span>

<span data-ttu-id="ef0d0-342">Эта служба выделяет пакет UDP из указанного пула пакетов и освобождает пространство для 4-байтового заголовка TFTP перед возвращением пакета вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-342">This service allocates a UDP packet from the specified packet pool and makes room for the 4-byte TFTP header before the packet is returned to the caller.</span></span> <span data-ttu-id="ef0d0-343">После этого вызывающий объект может создать буфер для записи в файл клиента.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-343">The caller can then build a buffer for writing to a client file.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ef0d0-344">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ef0d0-344">Input Parameters</span></span>

- <span data-ttu-id="ef0d0-345">**pool_ptr**: указатель на пул пакетов.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-345">**pool_ptr** Pointer to packet pool.</span></span>

- <span data-ttu-id="ef0d0-346">**packet_ptr**: место назначения для указателя на выделенный пакет.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-346">**packet_ptr** Destination for pointer to allocated packet.</span></span>

- <span data-ttu-id="ef0d0-347">**wait_option**: определяет, как долго служба будет ожидать завершения выделения пакета.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-347">**wait_option** Defines how long the service will wait for the packet allocate to complete.</span></span> <span data-ttu-id="ef0d0-348">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="ef0d0-348">The wait options are defined as follows:</span></span>

  <span data-ttu-id="ef0d0-349">**значение времени ожидания** (от 0X00000001 до 0xFFFFFFFE);</span><span class="sxs-lookup"><span data-stu-id="ef0d0-349">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="ef0d0-350">**TX_WAIT_FOREVER** (0xFFFFFFFF).</span><span class="sxs-lookup"><span data-stu-id="ef0d0-350">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

  <span data-ttu-id="ef0d0-351">В случае выбора TX_WAIT_FOREVER вызывающий поток приостанавливается на неопределенное время, пока пакет не будет выделен.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-351">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the allocation completes.</span></span>

  <span data-ttu-id="ef0d0-352">Числовое значение (от 1 до 0xFFFFFFFE) указывает максимальное количество тактов таймера для ожидания выделения пакета в состоянии приостановки.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-352">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the packet allocation.</span></span>

- <span data-ttu-id="ef0d0-353">**ip_type**: позволяет указать, какой протокол IP использовать.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-353">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="ef0d0-354">Допустимые значения: IPv4 (4) или IPv6 (6).</span><span class="sxs-lookup"><span data-stu-id="ef0d0-354">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="ef0d0-355">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ef0d0-355">Return Values</span></span>

- <span data-ttu-id="ef0d0-356">**NX_SUCCESS** (0x00): пакет выделен успешно.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-356">**NX_SUCCESS** (0x00) Successful packet allocate</span></span>

- <span data-ttu-id="ef0d0-357">NX_PTR_ERROR (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-357">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="ef0d0-358">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-358">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="ef0d0-359">NX_INVALID_PARAMETERS (0x4D): недопустимые входные данные, отличные от указателя.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-359">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ef0d0-360">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ef0d0-360">Allowed From</span></span>

<span data-ttu-id="ef0d0-361">Потоки</span><span class="sxs-lookup"><span data-stu-id="ef0d0-361">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ef0d0-362">Например, .</span><span class="sxs-lookup"><span data-stu-id="ef0d0-362">Example</span></span>

```C
/* Allocate a packet for TFTP file write. */
status =  nxd_tftp_client_packet_allocate(&my_pool, &packet_ptr, 200);

/* If status is NX_SUCCESS “packet_ptr” contains the new packet. */
```

## <a name="nxd_tftp_client_set_interface"></a><span data-ttu-id="ef0d0-363">nxd_tftp_client_set_interface</span><span class="sxs-lookup"><span data-stu-id="ef0d0-363">nxd_tftp_client_set_interface</span></span>

<span data-ttu-id="ef0d0-364">Настройка физического интерфейса для запросов TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-364">Set physical interface for TFTP requests</span></span>

### <a name="prototype"></a><span data-ttu-id="ef0d0-365">Прототип</span><span class="sxs-lookup"><span data-stu-id="ef0d0-365">Prototype</span></span>

```C
UINT nxd_tftp_client_set_interface(NX_TFTP_CLIENT *tftp_client_ptr,
                                    UINT if_index);
```

### <a name="description"></a><span data-ttu-id="ef0d0-366">Описание</span><span class="sxs-lookup"><span data-stu-id="ef0d0-366">Description</span></span>

<span data-ttu-id="ef0d0-367">Эта служба использует входной индекс интерфейса, чтобы задать физический интерфейс клиента TFTP для отправки и получения пакетов TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-367">This service uses the input interface index to set the physical interface for the TFTP Client to send and receive TFTP packets.</span></span> <span data-ttu-id="ef0d0-368">Значение по умолчанию равно нулю, что соответствует основному интерфейсу.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-368">The default value is zero, for the primary interface.</span></span>

> [!NOTE]
> <span data-ttu-id="ef0d0-369">Для использования этой службы версия NetX Duo должна поддерживать множественную адресацию (версия 5.6 или более поздняя версия).</span><span class="sxs-lookup"><span data-stu-id="ef0d0-369">NetX Duo must support multihome addressing (v5.6 or later) to use this service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ef0d0-370">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ef0d0-370">Input Parameters</span></span>

- <span data-ttu-id="ef0d0-371">**tftp_client_ptr**: указатель на экземпляр клиента TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-371">**tftp_client_ptr** Pointer to TFTP Client instance</span></span>

- <span data-ttu-id="ef0d0-372">**if_index**: индекс используемого физического интерфейса.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-372">**if_index** Index of physical interface to use</span></span>

### <a name="return-values"></a><span data-ttu-id="ef0d0-373">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ef0d0-373">Return Values</span></span>

- <span data-ttu-id="ef0d0-374">**NX_SUCCESS** (0X00): интерфейс успешно задан; (0x0B): недопустимые входные данные интерфейса.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-374">**NX_SUCCESS** (0x00) Successfully set interface (0x0B) Invalid interface input</span></span>

- <span data-ttu-id="ef0d0-375">NX_PTR_ERROR (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-375">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="ef0d0-376">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-376">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="ef0d0-377">NX_TFTP_INVALID_INTERFACE (0x0B): недопустимые входные данные интерфейса.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-377">NX_TFTP_INVALID_INTERFACE (0x0B) Invalid interface input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ef0d0-378">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ef0d0-378">Allowed From</span></span>

<span data-ttu-id="ef0d0-379">Потоки</span><span class="sxs-lookup"><span data-stu-id="ef0d0-379">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ef0d0-380">Например, .</span><span class="sxs-lookup"><span data-stu-id="ef0d0-380">Example</span></span>

```C
/* Specify the primary interface for TFTP requests. */
status =  nxd_tftp_client_set_interface(&client, 0);

/* If status is NX_SUCCESS the primary interface will be use for TFTP communications. */
```

## <a name="nxd_tftp_server_create"></a><span data-ttu-id="ef0d0-381">nxd_tftp_server_create</span><span class="sxs-lookup"><span data-stu-id="ef0d0-381">nxd_tftp_server_create</span></span>

<span data-ttu-id="ef0d0-382">Создание сервера TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-382">Create TFTP server</span></span>

### <a name="prototype"></a><span data-ttu-id="ef0d0-383">Прототип</span><span class="sxs-lookup"><span data-stu-id="ef0d0-383">Prototype</span></span>

```C
UINT nxd_tftp_server_create(NX_TFTP_SERVER *tftp_server_ptr,
            CHAR *tftp_server_name, NX_IP *ip_ptr, FX_MEDIA *media_ptr, 
            VOID *stack_ptr, ULONG stack_size,
            NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="ef0d0-384">Описание</span><span class="sxs-lookup"><span data-stu-id="ef0d0-384">Description</span></span>

<span data-ttu-id="ef0d0-385">Эта служба создает сервер TFTP, отвечающий на запросы клиентов TFTP через порт 69.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-385">This service creates a TFTP Server that responds to TFTP Client requests on port 69.</span></span> <span data-ttu-id="ef0d0-386">Данный сервер должен быть запущен последующим вызовом *nxd_tftp_server_start*.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-386">The Server must be started by a subsequent call to *nxd_tftp_server_start*.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ef0d0-387">Приложение должно обеспечить предварительное создание указанного экземпляра IP, пула пакетов и экземпляра носителя FileX.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-387">The application must make certain the supplied IP instance, packet pool, and FileX media instance are already created.</span></span> <span data-ttu-id="ef0d0-388">Кроме того, перед вызовом этой службы необходимо включить протокол UDP для экземпляра IP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-388">In addition, UDP must be enabled for the IP instance prior to calling this service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ef0d0-389">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ef0d0-389">Input Parameters</span></span>

- <span data-ttu-id="ef0d0-390">**tftp_server_ptr**: указатель на блок управления сервером TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-390">**tftp_server_ptr** Pointer to TFTP Server control block.</span></span>

- <span data-ttu-id="ef0d0-391">**tftp_server_name**: имя этого экземпляра сервера TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-391">**tftp_server_name** Name of this TFTP Server instance</span></span>

- <span data-ttu-id="ef0d0-392">**ip_ptr**: указатель на созданный ранее экземпляр IP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-392">**ip_ptr** Pointer to previously created IP instance.</span></span>

- <span data-ttu-id="ef0d0-393">**media_ptr**: указатель на экземпляр носителя FileX.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-393">**media_ptr** Pointer to FileX media instance.</span></span>

- <span data-ttu-id="ef0d0-394">**stack_ptr**: указатель на область стека сервера TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-394">**stack_ptr** Pointer to TFTP Server stack area.</span></span>

- <span data-ttu-id="ef0d0-395">**stack_size**: число байтов в стеке сервера TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-395">**stack_size** Number of bytes in the TFTP Server stack.</span></span>

- <span data-ttu-id="ef0d0-396">**pool_ptr**: указатель на пул пакетов TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-396">**pool_ptr** Pointer to TFTP packet pool.</span></span> 

> [!NOTE]
> <span data-ttu-id="ef0d0-397">Указанный пул должен вмещать полезные данные пакетов размером не менее 580 байт.<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="ef0d0-397">The supplied pool must have packet payloads at least 580 bytes in size.<sup>1</sup></span></span>

<span data-ttu-id="ef0d0-398"><sup>1</sup> Сами данные пакета занимают ровно 512 байт, но размер полезных данных пакета должен составлять не менее 572 байт.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-398"><sup>1</sup> The data portion of a packet is exactly 512 bytes, but the packet payload size must be at least 572 bytes.</span></span> <span data-ttu-id="ef0d0-399">Оставшиеся байты используются для заголовков UDP, IPv6 и Ethernet и потенциальных младших байтов, необходимых драйверу для выравнивания.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-399">The remaining bytes are used for the UDP, IPv6, and Ethernet headers and potential trailing bytes required by the driver for alignment.</span></span>

### <a name="return-values"></a><span data-ttu-id="ef0d0-400">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ef0d0-400">Return Values</span></span>

- <span data-ttu-id="ef0d0-401">**NX_SUCCESS**: (0x00) сервер успешно создан.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-401">**NX_SUCCESS** (0x00) Successful Server create</span></span>

- <span data-ttu-id="ef0d0-402">**NX_TFTP_POOL_ERROR** (0xC6): размер пакета в пуле пакетов меньше 560 байт.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-402">**NX_TFTP_POOL_ERROR** (0xC6) Packet pool has packet size of less than 560 bytes</span></span>

- <span data-ttu-id="ef0d0-403">NX_PTR_ERROR (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-403">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ef0d0-404">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ef0d0-404">Allowed From</span></span>

<span data-ttu-id="ef0d0-405">Инициализация, потоки.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-405">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="ef0d0-406">Например, .</span><span class="sxs-lookup"><span data-stu-id="ef0d0-406">Example</span></span>

```C
/* Create a TFTP Server called “my_server”. */
status =  nxd_tftp_server_create(&my_server, “My TFTP Server”, &server_ip, 
                &ram_disk, stack_ptr, 2048, pool_ptr);

/* If status is NX_SUCCESS the TFTP Server is created. */
```

## <a name="nxd_tftp_server_delete"></a><span data-ttu-id="ef0d0-407">nxd_tftp_server_delete</span><span class="sxs-lookup"><span data-stu-id="ef0d0-407">nxd_tftp_server_delete</span></span>

<span data-ttu-id="ef0d0-408">Удаление сервера TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-408">Delete TFTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ef0d0-409">Прототип</span><span class="sxs-lookup"><span data-stu-id="ef0d0-409">Prototype</span></span>

```C
UINT nxd_tftp_server_delete(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="ef0d0-410">Описание</span><span class="sxs-lookup"><span data-stu-id="ef0d0-410">Description</span></span>

<span data-ttu-id="ef0d0-411">Эта служба удаляет созданный ранее сервер TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-411">This service deletes a previously created TFTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ef0d0-412">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ef0d0-412">Input Parameters</span></span>

- <span data-ttu-id="ef0d0-413">**tftp_server_ptr**: указатель на блок управления сервером TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-413">**tftp_server_ptr** Pointer to TFTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="ef0d0-414">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ef0d0-414">Return Values</span></span>

- <span data-ttu-id="ef0d0-415">**NX_SUCCESS** (0x00): сервер успешно удален.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-415">**NX_SUCCESS** (0x00) Successful Server delete</span></span>

- <span data-ttu-id="ef0d0-416">NX_PTR_ERROR (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-416">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="ef0d0-417">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-417">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ef0d0-418">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ef0d0-418">Allowed From</span></span>

<span data-ttu-id="ef0d0-419">Потоки</span><span class="sxs-lookup"><span data-stu-id="ef0d0-419">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ef0d0-420">Например, .</span><span class="sxs-lookup"><span data-stu-id="ef0d0-420">Example</span></span>

```C
/* Delete the TFTP Server called “my_server”. */
status =  nxd_tftp_server_delete(&my_server);

/* If status is NX_SUCCESS the TFTP Server is deleted. */
```

## <a name="nxd_tftp_server_start"></a><span data-ttu-id="ef0d0-421">nxd_tftp_server_start</span><span class="sxs-lookup"><span data-stu-id="ef0d0-421">nxd_tftp_server_start</span></span>

<span data-ttu-id="ef0d0-422">Запуск сервера TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-422">Start TFTP server</span></span>

### <a name="prototype"></a><span data-ttu-id="ef0d0-423">Прототип</span><span class="sxs-lookup"><span data-stu-id="ef0d0-423">Prototype</span></span>

```C
UINT nxd_tftp_server_start(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="ef0d0-424">Описание</span><span class="sxs-lookup"><span data-stu-id="ef0d0-424">Description</span></span>

<span data-ttu-id="ef0d0-425">Эта служба запускает созданный ранее сервер TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-425">This service starts the previously created TFTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ef0d0-426">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ef0d0-426">Input Parameters</span></span>

- <span data-ttu-id="ef0d0-427">**tftp_server_ptr**: указатель на блок управления сервером TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-427">**tftp_server_ptr** Pointer to TFTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="ef0d0-428">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ef0d0-428">Return Values</span></span>

- <span data-ttu-id="ef0d0-429">**NX_SUCCESS** (0x00): сервер успешно запущен.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-429">**NX_SUCCESS** (0x00) Successful Server start</span></span>

- <span data-ttu-id="ef0d0-430">NX_PTR_ERROR (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-430">NX_PTR_ERROR (0x16) Invalid pointer input .</span></span>
 
### <a name="allowed-from"></a><span data-ttu-id="ef0d0-431">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ef0d0-431">Allowed From</span></span>

<span data-ttu-id="ef0d0-432">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="ef0d0-432">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="ef0d0-433">Например, .</span><span class="sxs-lookup"><span data-stu-id="ef0d0-433">Example</span></span>

```C
/* Start the TFTP Server called “my_server”. */
status =  nxd_tftp_server_start(&my_server);

/* If status is NX_SUCCESS the TFTP Server is started. */
```

## <a name="nxd_tftp_server_stop"></a><span data-ttu-id="ef0d0-434">nxd_tftp_server_stop</span><span class="sxs-lookup"><span data-stu-id="ef0d0-434">nxd_tftp_server_stop</span></span>

<span data-ttu-id="ef0d0-435">Остановка сервера TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-435">Stop TFTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ef0d0-436">Прототип</span><span class="sxs-lookup"><span data-stu-id="ef0d0-436">Prototype</span></span>

```C
UINT nxd_tftp_server_stop(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="ef0d0-437">Описание</span><span class="sxs-lookup"><span data-stu-id="ef0d0-437">Description</span></span>

<span data-ttu-id="ef0d0-438">Эта служба останавливает созданный ранее сервер TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-438">This service stops the previously created TFTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ef0d0-439">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ef0d0-439">Input Parameters</span></span>

- <span data-ttu-id="ef0d0-440">**tftp_server_ptr**: указатель на блок управления сервером TFTP.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-440">**tftp_server_ptr** Pointer to TFTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="ef0d0-441">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ef0d0-441">Return Values</span></span>

- <span data-ttu-id="ef0d0-442">**NX_SUCCESS** (0x00): сервер успешно остановлен.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-442">**NX_SUCCESS** (0x00) Successful Server stop</span></span>

- <span data-ttu-id="ef0d0-443">NX_PTR_ERROR (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-443">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="ef0d0-444">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ef0d0-444">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ef0d0-445">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ef0d0-445">Allowed From</span></span>

<span data-ttu-id="ef0d0-446">Потоки</span><span class="sxs-lookup"><span data-stu-id="ef0d0-446">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ef0d0-447">Пример</span><span class="sxs-lookup"><span data-stu-id="ef0d0-447">Example</span></span>

```C
/* Stop the TFTP Server called “my_server”. */
status =  nxd_tftp_server_stop(&my_server);

/* If status is NX_SUCCESS the TFTP Server is stopped. */
```