---
title: Глава 3. Описание служб FTP для NetX в ОСРВ Azure
description: В этой главе приводится описание всех служб FTP для NetX в ОСРВ Azure, которые перечислены ниже в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b05d03c45607c45acf32474cf8e40861532c5fae
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815200"
---
# <a name="chapter-3---description-of-azure-rtos-netx-ftp-services"></a><span data-ttu-id="0c97e-103">Глава 3. Описание служб FTP для NetX в ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="0c97e-103">Chapter 3 - Description of Azure RTOS NetX FTP services</span></span>

<span data-ttu-id="0c97e-104">В этой главе приводится описание всех служб FTP для NetX в ОСРВ Azure, которые перечислены ниже в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="0c97e-104">This chapter contains a description of all Azure RTOS NetX FTP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="0c97e-105">В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, используемым для отключения проверки ошибок API, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="0c97e-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="0c97e-106">**nx_ftp_client_connect**: *подключение к FTP-серверу*</span><span class="sxs-lookup"><span data-stu-id="0c97e-106">**nx_ftp_client_connect**: *Connect to FTP Server*</span></span>
- <span data-ttu-id="0c97e-107">**nx_ftp_client_create**: *создание экземпляра FTP-клиента*</span><span class="sxs-lookup"><span data-stu-id="0c97e-107">**nx_ftp_client_create**: *Create an FTP Client instance*</span></span>
- <span data-ttu-id="0c97e-108">**nx_ftp_client_delete**: *удаление экземпляра FTP-клиента*</span><span class="sxs-lookup"><span data-stu-id="0c97e-108">**nx_ftp_client_delete**: *Delete an FTP Client instance*</span></span>
- <span data-ttu-id="0c97e-109">**nx_ftp_client_directory_create**: *создание каталога на сервере*</span><span class="sxs-lookup"><span data-stu-id="0c97e-109">**nx_ftp_client_directory_create**: *Create a directory on Server*</span></span>
- <span data-ttu-id="0c97e-110">**nx_ftp_client_directory_default_set**: *задание каталога по умолчанию на сервере*</span><span class="sxs-lookup"><span data-stu-id="0c97e-110">**nx_ftp_client_directory_default_set**: *Set default directory on Server*</span></span>
- <span data-ttu-id="0c97e-111">**nx_ftp_client_directory_delete**: *удаление каталога на сервере*</span><span class="sxs-lookup"><span data-stu-id="0c97e-111">**nx_ftp_client_directory_delete**: *Delete a directory on Server*</span></span>
- <span data-ttu-id="0c97e-112">**nx_ftp_client_directory_listing_get**: *получение содержимого каталога с сервера*</span><span class="sxs-lookup"><span data-stu-id="0c97e-112">**nx_ftp_client_directory_listing_get**: *Get directory listing from Server*</span></span>
- <span data-ttu-id="0c97e-113">**nx_ftp_client_directory_listing_continue**: *продолжение получения содержимого каталога с сервера*</span><span class="sxs-lookup"><span data-stu-id="0c97e-113">**nx_ftp_client_directory_listing_continue**: *Continue directory listing from Server*</span></span>
- <span data-ttu-id="0c97e-114">**nx_ftp_client_disconnect**: *отключение от FTP-сервера*</span><span class="sxs-lookup"><span data-stu-id="0c97e-114">**nx_ftp_client_disconnect**: *Disconnect from FTP Server*</span></span>
- <span data-ttu-id="0c97e-115">**nx_ftp_client_file_close**: *закрытие файла клиента*</span><span class="sxs-lookup"><span data-stu-id="0c97e-115">**nx_ftp_client_file_close**: *Close Client file*</span></span>
- <span data-ttu-id="0c97e-116">**nx_ftp_client_file_delete**: *удаление файла на сервере*</span><span class="sxs-lookup"><span data-stu-id="0c97e-116">**nx_ftp_client_file_delete**: *Delete file on Server*</span></span>
- <span data-ttu-id="0c97e-117">**nx_ftp_client_file_open**: *открытие файла клиента*</span><span class="sxs-lookup"><span data-stu-id="0c97e-117">**nx_ftp_client_file_open**: *Open Client file*</span></span>
- <span data-ttu-id="0c97e-118">**nx_ftp_client_file_read**: *чтение из файла*</span><span class="sxs-lookup"><span data-stu-id="0c97e-118">**nx_ftp_client_file_read**: *Read from file*</span></span>
- <span data-ttu-id="0c97e-119">**nx_ftp_client_file_rename**: *переименование файла на сервере*</span><span class="sxs-lookup"><span data-stu-id="0c97e-119">**nx_ftp_client_file_rename**: *Rename file on Server*</span></span>
- <span data-ttu-id="0c97e-120">**nx_ftp_client_file_write**: *запись в файл*</span><span class="sxs-lookup"><span data-stu-id="0c97e-120">**nx_ftp_client_file_write**: *Write to file*</span></span>
- <span data-ttu-id="0c97e-121">**nx_ftp_server_create**: *создание FTP-сервера*</span><span class="sxs-lookup"><span data-stu-id="0c97e-121">**nx_ftp_server_create**: *Create FTP Server*</span></span>
- <span data-ttu-id="0c97e-122">**nx_ftp_server_delete**: *удаление FTP-сервера*</span><span class="sxs-lookup"><span data-stu-id="0c97e-122">**nx_ftp_server_delete**: *Delete FTP Server*</span></span>
- <span data-ttu-id="0c97e-123">**nx_ftp_server_start**: *запуск FTP-сервера*</span><span class="sxs-lookup"><span data-stu-id="0c97e-123">**nx_ftp_server_start**: *Start FTP Server*</span></span>
- <span data-ttu-id="0c97e-124">**nx_ftp_server_stop**: *остановка FTP-сервера*</span><span class="sxs-lookup"><span data-stu-id="0c97e-124">**nx_ftp_server_stop**: *Stop FTP Server*</span></span>

## <a name="nx_ftp_client_connect"></a><span data-ttu-id="0c97e-125">nx_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="0c97e-125">nx_ftp_client_connect</span></span>

<span data-ttu-id="0c97e-126">Подключение к FTP-серверу</span><span class="sxs-lookup"><span data-stu-id="0c97e-126">Connect to an FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0c97e-127">Прототип</span><span class="sxs-lookup"><span data-stu-id="0c97e-127">Prototype</span></span>

```c
UINT nx_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
        ULONG server_ip, CHAR *username, CHAR *password,
        ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0c97e-128">Описание</span><span class="sxs-lookup"><span data-stu-id="0c97e-128">Description</span></span>

<span data-ttu-id="0c97e-129">Эта служба подключает ранее созданный экземпляр FTP-клиента к FTP-серверу по заданному IP-адресу.</span><span class="sxs-lookup"><span data-stu-id="0c97e-129">This service connects the previously created FTP Client instance to the FTP Server at the supplied IP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c97e-130">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0c97e-130">Input Parameters</span></span>

- <span data-ttu-id="0c97e-131">**client_ptr**: указатель на блок управления FTP-клиентом</span><span class="sxs-lookup"><span data-stu-id="0c97e-131">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="0c97e-132">**server_ip**: IP-адрес FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="0c97e-132">**server_ip**: IP address of FTP Server.</span></span>
- <span data-ttu-id="0c97e-133">**username**: имя пользователя клиента для проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="0c97e-133">**username**: Client username for authentication.</span></span>
- <span data-ttu-id="0c97e-134">**пароль**: пароль клиента для проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="0c97e-134">**password**: Client password for authentication.</span></span>
- <span data-ttu-id="0c97e-135">**wait_option** определяет, как долго служба будет ожидать подключения FTP-клиента</span><span class="sxs-lookup"><span data-stu-id="0c97e-135">**wait_option**: Defines how long the service will wait for the FTP Client connection.</span></span> <span data-ttu-id="0c97e-136">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="0c97e-136">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="0c97e-137">**Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0c97e-137">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="0c97e-138">**TX_WAIT_FOREVER** (0xFFFFFFFF) — указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="0c97e-138">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="0c97e-139">Числовое значение (от 1 до 0xFFFFFFFE) указывает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа FTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="0c97e-139">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="0c97e-140">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0c97e-140">Return Values</span></span>

- <span data-ttu-id="0c97e-141">**NX_SUCCESS** (0x00) — FTP-подключение успешно создано.</span><span class="sxs-lookup"><span data-stu-id="0c97e-141">**NX_SUCCESS**: (0x00) Successful FTP connection.</span></span>
- <span data-ttu-id="0c97e-142">**NX_TFTP_EXPECTED_22X_CODE** (0xDB) — ответ 22X (OK) не получен.</span><span class="sxs-lookup"><span data-stu-id="0c97e-142">**NX_TFTP_EXPECTED_22X_CODE**: (0xDB) Did not get a 22X (ok) response</span></span>
- <span data-ttu-id="0c97e-143">**NX_FTP_EXPECTED_23X_CODE** (0xDC) — ответ 23X (OK) не получен.</span><span class="sxs-lookup"><span data-stu-id="0c97e-143">**NX_FTP_EXPECTED_23X_CODE**: (0xDC) Did not get a 23X (ok) response</span></span>
- <span data-ttu-id="0c97e-144">**NX_FTP_EXPECTED_33X_CODE** (0xDE) — ответ 33X (OK) не получен.</span><span class="sxs-lookup"><span data-stu-id="0c97e-144">**NX_FTP_EXPECTED_33X_CODE**: (0xDE) Did not get a 33X (ok) response</span></span>
- <span data-ttu-id="0c97e-145">**NX_FTP_NOT_DISCONNECTED** (0xD4) — клиент уже подключен.</span><span class="sxs-lookup"><span data-stu-id="0c97e-145">**NX_FTP_NOT_DISCONNECTED**: (0xD4) Client is already connected.</span></span>
- <span data-ttu-id="0c97e-146">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="0c97e-146">NX_PTR_ERROR: (0x07) Invalid pointer inout.</span></span>
- <span data-ttu-id="0c97e-147">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="0c97e-147">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0c97e-148">NX_IP_ADDRESS_ERROR (0x21) — недопустимый IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="0c97e-148">NX_IP_ADDRESS_ERROR: (0x21) Invalid IP address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c97e-149">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0c97e-149">Allowed From</span></span>

<span data-ttu-id="0c97e-150">Потоки</span><span class="sxs-lookup"><span data-stu-id="0c97e-150">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0c97e-151">Например, .</span><span class="sxs-lookup"><span data-stu-id="0c97e-151">Example</span></span>

```c
/* Connect the FTP Client instance "my_client" to the FTP Server at
    IP address 1.2.3.4. */
status = nx_ftp_client_connect(&my_client, IP_ADDRESS(1,2,3,4), NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
connected to the FTP Server. */
```

## <a name="nx_ftp_client_create"></a><span data-ttu-id="0c97e-152">nx_ftp_client_create</span><span class="sxs-lookup"><span data-stu-id="0c97e-152">nx_ftp_client_create</span></span>

<span data-ttu-id="0c97e-153">Создание экземпляра клиента FTP</span><span class="sxs-lookup"><span data-stu-id="0c97e-153">Create an FTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="0c97e-154">Прототип</span><span class="sxs-lookup"><span data-stu-id="0c97e-154">Prototype</span></span>

```c
UINT nx_ftp_client_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *ftp_client_name, NX_IP *ip_ptr, ULONG window_size,
    NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="0c97e-155">Описание</span><span class="sxs-lookup"><span data-stu-id="0c97e-155">Description</span></span>

<span data-ttu-id="0c97e-156">Эта служба создает экземпляр клиента FTP.</span><span class="sxs-lookup"><span data-stu-id="0c97e-156">This service creates an FTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c97e-157">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0c97e-157">Input Parameters</span></span>

- <span data-ttu-id="0c97e-158">**client_ptr**: указатель на блок управления FTP-клиентом</span><span class="sxs-lookup"><span data-stu-id="0c97e-158">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="0c97e-159">**ftp_client_name**: имя FTP-клиента</span><span class="sxs-lookup"><span data-stu-id="0c97e-159">**ftp_client_name**: Name of FTP Client.</span></span>
- <span data-ttu-id="0c97e-160">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="0c97e-160">**ip_ptr**: Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0c97e-161">**window_size**: размер объявленного окна для сокета TCP этого FTP-клиента</span><span class="sxs-lookup"><span data-stu-id="0c97e-161">**window_size**: Advertised window size for TCP socket of this FTP Client.</span></span>
- <span data-ttu-id="0c97e-162">**pool_ptr**: указатель на пул пакетов по умолчанию для этого FTP-клиента</span><span class="sxs-lookup"><span data-stu-id="0c97e-162">**pool_ptr**: Pointer to the default packet pool for this FTP Client.</span></span> <span data-ttu-id="0c97e-163">Обратите внимание, что минимальная полезная нагрузка пакета должна быть достаточно большой, чтобы вмещать полный путь и имя файла или каталога.</span><span class="sxs-lookup"><span data-stu-id="0c97e-163">Note that the minimum packet payload must be large enough to hold complete path and the file or directory name.</span></span>

### <a name="return-values"></a><span data-ttu-id="0c97e-164">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0c97e-164">Return Values</span></span>

- <span data-ttu-id="0c97e-165">**NX_SUCCESS** (0x00) — FTP-клиент успешно создан.</span><span class="sxs-lookup"><span data-stu-id="0c97e-165">**NX_SUCCESS**: (0x00) Successful FTP Client create.</span></span>
- <span data-ttu-id="0c97e-166">NX_PTR_ERROR (0x16) — недопустимый указатель на FTP, IP или пул пакетов.</span><span class="sxs-lookup"><span data-stu-id="0c97e-166">NX_PTR_ERROR: (0x16) Invalid FTP, IP pointer, or packet pool pointer.</span></span> <span data-ttu-id="0c97e-167">Указатель пароля.</span><span class="sxs-lookup"><span data-stu-id="0c97e-167">password pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c97e-168">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0c97e-168">Allowed From</span></span>

<span data-ttu-id="0c97e-169">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="0c97e-169">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="0c97e-170">Например, .</span><span class="sxs-lookup"><span data-stu-id="0c97e-170">Example</span></span>

```c
/* Create the FTP Client instance "my_client." */
status = nx_ftp_client_create(&my_client, "My Client", &client_ip,
                                2000, &client_pool);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
created. */
```

## <a name="nx_ftp_client_delete"></a><span data-ttu-id="0c97e-171">nx_ftp_client_delete</span><span class="sxs-lookup"><span data-stu-id="0c97e-171">nx_ftp_client_delete</span></span>

<span data-ttu-id="0c97e-172">Удаление экземпляра клиента FTP</span><span class="sxs-lookup"><span data-stu-id="0c97e-172">Delete an FTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="0c97e-173">Прототип</span><span class="sxs-lookup"><span data-stu-id="0c97e-173">Prototype</span></span>

```c
UINT nx_ftp_client_delete(NX_FTP_CLIENT *ftp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="0c97e-174">Описание</span><span class="sxs-lookup"><span data-stu-id="0c97e-174">Description</span></span>

<span data-ttu-id="0c97e-175">Эта служба удаляет экземпляр клиента FTP.</span><span class="sxs-lookup"><span data-stu-id="0c97e-175">This service deletes an FTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c97e-176">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0c97e-176">Input Parameters</span></span>

- <span data-ttu-id="0c97e-177">**client_ptr**: указатель на блок управления FTP-клиентом</span><span class="sxs-lookup"><span data-stu-id="0c97e-177">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="0c97e-178">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0c97e-178">Return Values</span></span>

- <span data-ttu-id="0c97e-179">**NX_SUCCESS** (0x00) — FTP-клиент успешно удален.</span><span class="sxs-lookup"><span data-stu-id="0c97e-179">**NX_SUCCESS**: (0x00) Successful FTP Client delete.</span></span>
- <span data-ttu-id="0c97e-180">**NX_FTP_NOT_DISCONNECTED** (0xD4) — ошибка удаления FTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="0c97e-180">**NX_FTP_NOT_DISCONNECTED**: (0xD4) FTP Client delete error.</span></span>
- <span data-ttu-id="0c97e-181">NX_PTR_ERROR (0x16) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="0c97e-181">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>
- <span data-ttu-id="0c97e-182">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="0c97e-182">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c97e-183">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0c97e-183">Allowed From</span></span>

<span data-ttu-id="0c97e-184">Потоки</span><span class="sxs-lookup"><span data-stu-id="0c97e-184">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0c97e-185">Например, .</span><span class="sxs-lookup"><span data-stu-id="0c97e-185">Example</span></span>

```c
/* Delete the FTP Client instance "my_client." */
status = nx_ftp_client_delete(&my_client);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
    deleted. */
```

## <a name="nx_ftp_client_directory_create"></a><span data-ttu-id="0c97e-186">nx_ftp_client_directory_create</span><span class="sxs-lookup"><span data-stu-id="0c97e-186">nx_ftp_client_directory_create</span></span>

<span data-ttu-id="0c97e-187">Создание каталога на FTP-сервере</span><span class="sxs-lookup"><span data-stu-id="0c97e-187">Create a directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0c97e-188">Прототип</span><span class="sxs-lookup"><span data-stu-id="0c97e-188">Prototype</span></span>

```c
UINT nx_ftp_client_directory_create(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0c97e-189">Описание</span><span class="sxs-lookup"><span data-stu-id="0c97e-189">Description</span></span>

<span data-ttu-id="0c97e-190">Эта служба создает указанный каталог на FTP-сервере, подключенном к указанному клиенту FTP.</span><span class="sxs-lookup"><span data-stu-id="0c97e-190">This service creates the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c97e-191">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0c97e-191">Input Parameters</span></span>

- <span data-ttu-id="0c97e-192">**client_ptr**: указатель на блок управления FTP-клиентом</span><span class="sxs-lookup"><span data-stu-id="0c97e-192">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="0c97e-193">**directory_name**: имя создаваемого каталога</span><span class="sxs-lookup"><span data-stu-id="0c97e-193">**directory_name**: Name of directory to create.</span></span>
- <span data-ttu-id="0c97e-194">**wait_option** определяет, как долго служба будет ожидать создания каталога FTP</span><span class="sxs-lookup"><span data-stu-id="0c97e-194">**wait_option**: Defines how long the service will wait for the FTP directory create.</span></span> <span data-ttu-id="0c97e-195">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="0c97e-195">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="0c97e-196">**Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0c97e-196">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="0c97e-197">**TX_WAIT_FOREVER** (0xFFFFFFFF) — указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="0c97e-197">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="0c97e-198">Числовое значение (от 1 до 0xFFFFFFFE) указывает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа FTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="0c97e-198">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="0c97e-199">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0c97e-199">Return Values</span></span>

- <span data-ttu-id="0c97e-200">**NX_SUCCESS** (0x00) — каталог FTP успешно создан.</span><span class="sxs-lookup"><span data-stu-id="0c97e-200">**NX_SUCCESS**: (0x00) Successful FTP directory create.</span></span>
- <span data-ttu-id="0c97e-201">**NX_FTP_NOT_CONNECTED** (0xD3) — FTP-клиент не подключен.</span><span class="sxs-lookup"><span data-stu-id="0c97e-201">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="0c97e-202">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) — ответ 2XX (OK) не получен.</span><span class="sxs-lookup"><span data-stu-id="0c97e-202">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span> 
- <span data-ttu-id="0c97e-203">NX_PTR_ERROR (0x07) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="0c97e-203">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span> 
- <span data-ttu-id="0c97e-204">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="0c97e-204">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c97e-205">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0c97e-205">Allowed From</span></span>

<span data-ttu-id="0c97e-206">Потоки</span><span class="sxs-lookup"><span data-stu-id="0c97e-206">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0c97e-207">Например, .</span><span class="sxs-lookup"><span data-stu-id="0c97e-207">Example</span></span>

```c
/* Create the directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_create(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" was successfully  
    created. */
```

## <a name="nx_ftp_client_directory_default_set"></a><span data-ttu-id="0c97e-208">nx_ftp_client_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="0c97e-208">nx_ftp_client_directory_default_set</span></span>

<span data-ttu-id="0c97e-209">Задание каталога по умолчанию на FTP-сервере</span><span class="sxs-lookup"><span data-stu-id="0c97e-209">Set default directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0c97e-210">Прототип</span><span class="sxs-lookup"><span data-stu-id="0c97e-210">Prototype</span></span>

```c
UINT nx_ftp_client_directory_default_set(NX_FTP_CLIENT *ftp_client_ptr,
                                CHAR *directory_path, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0c97e-211">Описание</span><span class="sxs-lookup"><span data-stu-id="0c97e-211">Description</span></span>

<span data-ttu-id="0c97e-212">Эта служба задает каталог по умолчанию на FTP-сервере, подключенном к указанному клиенту FTP.</span><span class="sxs-lookup"><span data-stu-id="0c97e-212">This service sets the default directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="0c97e-213">Этот каталог по умолчанию применяется только к подключению этого клиента.</span><span class="sxs-lookup"><span data-stu-id="0c97e-213">This default directory applies only to this client's connection.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c97e-214">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0c97e-214">Input Parameters</span></span>

- <span data-ttu-id="0c97e-215">**client_ptr**: указатель на блок управления FTP-клиентом</span><span class="sxs-lookup"><span data-stu-id="0c97e-215">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="0c97e-216">**directory_path**: имя пути к каталогу, который необходимо задать</span><span class="sxs-lookup"><span data-stu-id="0c97e-216">**directory_path**: Name of directory path to set.</span></span>
- <span data-ttu-id="0c97e-217">**wait_option** определяет, как долго служба будет ожидать задания каталога FTP по умолчанию</span><span class="sxs-lookup"><span data-stu-id="0c97e-217">**wait_option**: Defines how long the service will wait for the FTP default directory set.</span></span> <span data-ttu-id="0c97e-218">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="0c97e-218">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="0c97e-219">**Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0c97e-219">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="0c97e-220">**TX_WAIT_FOREVER** (0xFFFFFFFF) — указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="0c97e-220">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="0c97e-221">Числовое значение (от 1 до 0xFFFFFFFE) указывает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа FTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="0c97e-221">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="0c97e-222">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0c97e-222">Return Values</span></span>

- <span data-ttu-id="0c97e-223">**NX_SUCCESS** (0x00) — каталог FTP по умолчанию успешно задан.</span><span class="sxs-lookup"><span data-stu-id="0c97e-223">**NX_SUCCESS**: (0x00) Successful FTP default set.</span></span>
- <span data-ttu-id="0c97e-224">**NX_FTP_NOT_CONNECTED** (0xD3) — FTP-клиент не подключен.</span><span class="sxs-lookup"><span data-stu-id="0c97e-224">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="0c97e-225">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) — ответ 2XX (OK) не получен.</span><span class="sxs-lookup"><span data-stu-id="0c97e-225">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span> 
- <span data-ttu-id="0c97e-226">NX_PTR_ERROR (0x07) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="0c97e-226">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span> 
- <span data-ttu-id="0c97e-227">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="0c97e-227">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c97e-228">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0c97e-228">Allowed From</span></span>

<span data-ttu-id="0c97e-229">Потоки</span><span class="sxs-lookup"><span data-stu-id="0c97e-229">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0c97e-230">Например, .</span><span class="sxs-lookup"><span data-stu-id="0c97e-230">Example</span></span>

```c
/* Set the default directory to "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_default_set(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" is the default directory. */
```

## <a name="nx_ftp_client_directory_delete"></a><span data-ttu-id="0c97e-231">nx_ftp_client_directory_delete</span><span class="sxs-lookup"><span data-stu-id="0c97e-231">nx_ftp_client_directory_delete</span></span>

<span data-ttu-id="0c97e-232">Удаление каталога на FTP-сервере</span><span class="sxs-lookup"><span data-stu-id="0c97e-232">Delete directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0c97e-233">Прототип</span><span class="sxs-lookup"><span data-stu-id="0c97e-233">Prototype</span></span>

```c
UINT nx_ftp_client_directory_delete(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0c97e-234">Описание</span><span class="sxs-lookup"><span data-stu-id="0c97e-234">Description</span></span>

<span data-ttu-id="0c97e-235">Эта служба удаляет указанный каталог на FTP-сервере, подключенном к указанному клиенту FTP.</span><span class="sxs-lookup"><span data-stu-id="0c97e-235">This service deletes the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c97e-236">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0c97e-236">Input Parameters</span></span>

- <span data-ttu-id="0c97e-237">**client_ptr**: указатель на блок управления FTP-клиентом</span><span class="sxs-lookup"><span data-stu-id="0c97e-237">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="0c97e-238">**directory_name**: имя удаляемого каталога</span><span class="sxs-lookup"><span data-stu-id="0c97e-238">**directory_name**: Name of directory to delete.</span></span>
- <span data-ttu-id="0c97e-239">**wait_option** определяет, как долго служба будет ожидать удаления каталога FTP</span><span class="sxs-lookup"><span data-stu-id="0c97e-239">**wait_option**: Defines how long the service will wait for the FTP directory delete.</span></span> <span data-ttu-id="0c97e-240">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="0c97e-240">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="0c97e-241">**Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0c97e-241">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="0c97e-242">**TX_WAIT_FOREVER** (0xFFFFFFFF) — указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="0c97e-242">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="0c97e-243">Числовое значение (от 1 до 0xFFFFFFFE) указывает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа FTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="0c97e-243">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="0c97e-244">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0c97e-244">Return Values</span></span>

- <span data-ttu-id="0c97e-245">**NX_SUCCESS** (0x00) — каталог FTP успешно удален.</span><span class="sxs-lookup"><span data-stu-id="0c97e-245">**NX_SUCCESS**: (0x00) Successful FTP directory delete.</span></span>
- <span data-ttu-id="0c97e-246">**NX_FTP_NOT_CONNECTED** (0xD3) — FTP-клиент не подключен.</span><span class="sxs-lookup"><span data-stu-id="0c97e-246">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="0c97e-247">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) — ответ 2XX (OK) не получен.</span><span class="sxs-lookup"><span data-stu-id="0c97e-247">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span> 
- <span data-ttu-id="0c97e-248">NX_PTR_ERROR (0x07) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="0c97e-248">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span> 
- <span data-ttu-id="0c97e-249">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="0c97e-249">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c97e-250">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0c97e-250">Allowed From</span></span>

<span data-ttu-id="0c97e-251">Потоки</span><span class="sxs-lookup"><span data-stu-id="0c97e-251">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0c97e-252">Например, .</span><span class="sxs-lookup"><span data-stu-id="0c97e-252">Example</span></span>

```c
/* Delete directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_delete(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" is deleted. */
```

## <a name="nx_ftp_client_directory_listing_get"></a><span data-ttu-id="0c97e-253">nx_ftp_client_directory_listing_get</span><span class="sxs-lookup"><span data-stu-id="0c97e-253">nx_ftp_client_directory_listing_get</span></span>

<span data-ttu-id="0c97e-254">Получение содержимого каталога с FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="0c97e-254">Get directory listing from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0c97e-255">Прототип</span><span class="sxs-lookup"><span data-stu-id="0c97e-255">Prototype</span></span>

```c
UINT nx_ftp_client_directory_listing_get(NX_FTP_CLIENT *ftp_client_ptr,
                            CHAR *directory_name, NX_PACKET **packet_ptr,
                            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0c97e-256">Описание</span><span class="sxs-lookup"><span data-stu-id="0c97e-256">Description</span></span>

<span data-ttu-id="0c97e-257">Эта служба получает содержимое указанного каталога на FTP-сервере, подключенном к указанному клиенту FTP.</span><span class="sxs-lookup"><span data-stu-id="0c97e-257">This service gets the contents of the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="0c97e-258">Приведенный указатель пакета будет содержать одну запись каталога или несколько.</span><span class="sxs-lookup"><span data-stu-id="0c97e-258">The supplied packet pointer will contain one or more directory entries.</span></span> <span data-ttu-id="0c97e-259">Каждая запись отделяется комбинацией символов &lt;cr/lf.</span><span class="sxs-lookup"><span data-stu-id="0c97e-259">Each entry is separated by a &lt;cr/lf\combination.</span></span> <span data-ttu-id="0c97e-260">Для завершения операции получения каталога необходимо вызвать службу ***nx_ftp_client_directory_listing_continue***.</span><span class="sxs-lookup"><span data-stu-id="0c97e-260">The ***nx_ftp_client_directory_listing_continue***: should be called to complete the directory get operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c97e-261">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0c97e-261">Input Parameters</span></span>

- <span data-ttu-id="0c97e-262">**client_ptr**: указатель на блок управления FTP-клиентом</span><span class="sxs-lookup"><span data-stu-id="0c97e-262">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="0c97e-263">**directory_name**: имя каталога, содержимое которого нужно получить</span><span class="sxs-lookup"><span data-stu-id="0c97e-263">**directory_name**: Name of directory to get contents of.</span></span>
- <span data-ttu-id="0c97e-264">**packet_ptr**: указатель на указатель пакета назначения</span><span class="sxs-lookup"><span data-stu-id="0c97e-264">**packet_ptr**: Pointer to destination packet pointer.</span></span> <span data-ttu-id="0c97e-265">В случае успешного выполнения полезная нагрузка пакета будет содержать одну запись каталога или несколько.</span><span class="sxs-lookup"><span data-stu-id="0c97e-265">If successful, the packet payload will contain one or more directory entries.</span></span>
- <span data-ttu-id="0c97e-266">**wait_option** определяет, как долго служба будет ожидать получения содержимого каталога FTP</span><span class="sxs-lookup"><span data-stu-id="0c97e-266">**wait_option**: Defines how long the service will wait for the FTP directory listing.</span></span> <span data-ttu-id="0c97e-267">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="0c97e-267">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="0c97e-268">**Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0c97e-268">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="0c97e-269">**TX_WAIT_FOREVER** (0xFFFFFFFF) — указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="0c97e-269">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="0c97e-270">Числовое значение (от 1 до 0xFFFFFFFE) указывает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа FTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="0c97e-270">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="0c97e-271">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0c97e-271">Return Values</span></span>

- <span data-ttu-id="0c97e-272">**NX_SUCCESS** (0x00) — содержимое каталога FTP успешно получено.</span><span class="sxs-lookup"><span data-stu-id="0c97e-272">**NX_SUCCESS**: (0x00) Successful FTP directory listing.</span></span>
- <span data-ttu-id="0c97e-273">**NX_FTP_NOT_CONNECTED** (0xD3) — FTP-клиент не подключен.</span><span class="sxs-lookup"><span data-stu-id="0c97e-273">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="0c97e-274">**NX_NOT_ENABLED** (0x14) — служба (IPv6) не включена.</span><span class="sxs-lookup"><span data-stu-id="0c97e-274">**NX_NOT_ENABLED**: (0x14) Service (IPv6) not enabled</span></span>
- <span data-ttu-id="0c97e-275">**NX_FTP_EXPECTED_1XX_CODE** (0xD9) — ответ 1XX (OK) не получен.</span><span class="sxs-lookup"><span data-stu-id="0c97e-275">**NX_FTP_EXPECTED_1XX_CODE**: (0xD9) Did not get a 1XX (ok) response</span></span>
- <span data-ttu-id="0c97e-276">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) — ответ 2XX (OK) не получен.</span><span class="sxs-lookup"><span data-stu-id="0c97e-276">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="0c97e-277">NX_PTR_ERROR (0x07) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="0c97e-277">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="0c97e-278">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="0c97e-278">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c97e-279">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0c97e-279">Allowed From</span></span>

<span data-ttu-id="0c97e-280">Потоки</span><span class="sxs-lookup"><span data-stu-id="0c97e-280">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0c97e-281">Например, .</span><span class="sxs-lookup"><span data-stu-id="0c97e-281">Example</span></span>

```c
/* Get the contents of directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_listing_get(&my_client, "my_dir", &my_packet,
                                            200);

/* If status is NX_SUCCESS, one or more entries of the directory "my_dir"
    can be found in "my_packet". */
```

## <a name="nx_ftp_client_directory_listing_continue"></a><span data-ttu-id="0c97e-282">nx_ftp_client_directory_listing_continue</span><span class="sxs-lookup"><span data-stu-id="0c97e-282">nx_ftp_client_directory_listing_continue</span></span>

<span data-ttu-id="0c97e-283">Продолжение получения содержимого каталога с FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="0c97e-283">Continue directory listing from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0c97e-284">Прототип</span><span class="sxs-lookup"><span data-stu-id="0c97e-284">Prototype</span></span>

```c
UINT nx_ftp_client_directory_listing_continue(NX_FTP_CLIENT
                    *ftp_client_ptr, NX_PACKET **packet_ptr,
                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0c97e-285">Описание</span><span class="sxs-lookup"><span data-stu-id="0c97e-285">Description</span></span>

<span data-ttu-id="0c97e-286">Эта служба продолжает получать содержимое указанного каталога на FTP-сервере, подключенном к указанному клиенту FTP.</span><span class="sxs-lookup"><span data-stu-id="0c97e-286">This service continues getting the contents of the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="0c97e-287">Перед ней должен быть выполнен вызов службы ***nx_ftp_client_directory_listing_get***.</span><span class="sxs-lookup"><span data-stu-id="0c97e-287">It should have been immediately preceded by a call to ***nx_ftp_client_directory_listing_get***.</span></span> <span data-ttu-id="0c97e-288">В случае успеха заданный указатель пакета будет содержать одну запись каталога или несколько.</span><span class="sxs-lookup"><span data-stu-id="0c97e-288">If successful, the supplied packet pointer will contain one or more directory entries.</span></span> <span data-ttu-id="0c97e-289">Эту подпрограмму следует вызывать до получения состояния NX_FTP_END_OF_LISTING.</span><span class="sxs-lookup"><span data-stu-id="0c97e-289">This routine should be called until an NX_FTP_END_OF_LISTING status is received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c97e-290">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0c97e-290">Input Parameters</span></span>

- <span data-ttu-id="0c97e-291">**client_ptr**: указатель на блок управления FTP-клиентом</span><span class="sxs-lookup"><span data-stu-id="0c97e-291">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="0c97e-292">**packet_ptr**: указатель на указатель пакета назначения</span><span class="sxs-lookup"><span data-stu-id="0c97e-292">**packet_ptr**: Pointer to destination packet pointer.</span></span> <span data-ttu-id="0c97e-293">В случае успешного выполнения полезная нагрузка пакета будет содержать одну запись каталога или несколько записей, разделенных комбинацией символов &lt;cr/lf&gt;.</span><span class="sxs-lookup"><span data-stu-id="0c97e-293">If successful, the packet payload will contain one or more directory entries, separated by a &lt;cr/lf&gt;.</span></span>
- <span data-ttu-id="0c97e-294">**wait_option** определяет, как долго служба будет ожидать получения содержимого каталога FTP</span><span class="sxs-lookup"><span data-stu-id="0c97e-294">**wait_option**: Defines how long the service will wait for the FTP directory listing.</span></span> <span data-ttu-id="0c97e-295">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="0c97e-295">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="0c97e-296">**Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0c97e-296">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="0c97e-297">**TX_WAIT_FOREVER** (0xFFFFFFFF) — указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="0c97e-297">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="0c97e-298">Числовое значение (от 1 до 0xFFFFFFFE) указывает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа FTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="0c97e-298">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="0c97e-299">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0c97e-299">Return Values</span></span>

- <span data-ttu-id="0c97e-300">**NX_SUCCESS** (0x00) — содержимое каталога FTP успешно получено.</span><span class="sxs-lookup"><span data-stu-id="0c97e-300">**NX_SUCCESS**: (0x00) Successful FTP directory listing.</span></span>
- <span data-ttu-id="0c97e-301">**NX_FTP_END_OF_LISTING** (0xD8) — в этом каталоге больше нет записей.</span><span class="sxs-lookup"><span data-stu-id="0c97e-301">**NX_FTP_END_OF_LISTING**: (0xD8) No more entries in this directory.</span></span>
- <span data-ttu-id="0c97e-302">**NX_FTP_NOT_CONNECTED** (0xD3) — FTP-клиент не подключен.</span><span class="sxs-lookup"><span data-stu-id="0c97e-302">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="0c97e-303">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) — ответ 2xx (OK) не получен.</span><span class="sxs-lookup"><span data-stu-id="0c97e-303">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="0c97e-304">NX_PTR_ERROR (0x07) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="0c97e-304">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="0c97e-305">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="0c97e-305">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c97e-306">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0c97e-306">Allowed From</span></span>

<span data-ttu-id="0c97e-307">Потоки</span><span class="sxs-lookup"><span data-stu-id="0c97e-307">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0c97e-308">Например, .</span><span class="sxs-lookup"><span data-stu-id="0c97e-308">Example</span></span>

```c
/* Continue getting the contents of directory "my_dir" on the FTP Server
    connected to the FTP Client instance "my_client." */
status = nx_ftp_client_directory_listing_continue(&my_client, &my_packet,
                                                200);

/* If status is NX_SUCCESS, one or more entries of the directory "my_dir"
    can be found in "my_packet". */
```

## <a name="nx_ftp_client_disconnect"></a><span data-ttu-id="0c97e-309">nx_ftp_client_disconnect</span><span class="sxs-lookup"><span data-stu-id="0c97e-309">nx_ftp_client_disconnect</span></span>

<span data-ttu-id="0c97e-310">Отключение от FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="0c97e-310">Disconnect from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0c97e-311">Прототип</span><span class="sxs-lookup"><span data-stu-id="0c97e-311">Prototype</span></span>

```c
UINT nx_ftp_client_disconnect(NX_FTP_CLIENT *ftp_client_ptr,
                            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0c97e-312">Описание</span><span class="sxs-lookup"><span data-stu-id="0c97e-312">Description</span></span>

<span data-ttu-id="0c97e-313">Эта служба отключает ранее установленное подключение FTP-сервера к указанному клиенту FTP.</span><span class="sxs-lookup"><span data-stu-id="0c97e-313">This service disconnects a previously established FTP Server connection with the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c97e-314">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0c97e-314">Input Parameters</span></span>

- <span data-ttu-id="0c97e-315">**client_ptr**: указатель на блок управления FTP-клиентом</span><span class="sxs-lookup"><span data-stu-id="0c97e-315">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="0c97e-316">**wait_option** определяет, как долго служба будет ожидать отключения FTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="0c97e-316">**wait_option**: Defines how long the service will wait for the FTP Client disconnect.</span></span> <span data-ttu-id="0c97e-317">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="0c97e-317">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="0c97e-318">**Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0c97e-318">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="0c97e-319">**TX_WAIT_FOREVER** (0xFFFFFFFF) — указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="0c97e-319">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="0c97e-320">Числовое значение (от 1 до 0xFFFFFFFE) указывает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа FTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="0c97e-320">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="0c97e-321">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0c97e-321">Return Values</span></span>

- <span data-ttu-id="0c97e-322">**NX_SUCCESS** (0x00) — FTP-подключение отключено.</span><span class="sxs-lookup"><span data-stu-id="0c97e-322">**NX_SUCCESS**: (0x00) Successful FTP disconnect.</span></span>
- <span data-ttu-id="0c97e-323">**NX_FTP_NOT_CONNECTED** (0xD3) — FTP-клиент не подключен.</span><span class="sxs-lookup"><span data-stu-id="0c97e-323">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="0c97e-324">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) — ответ 2XX (OK) не получен.</span><span class="sxs-lookup"><span data-stu-id="0c97e-324">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="0c97e-325">NX_PTR_ERROR (0x07) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="0c97e-325">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="0c97e-326">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="0c97e-326">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c97e-327">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0c97e-327">Allowed From</span></span>

<span data-ttu-id="0c97e-328">Потоки</span><span class="sxs-lookup"><span data-stu-id="0c97e-328">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0c97e-329">Например, .</span><span class="sxs-lookup"><span data-stu-id="0c97e-329">Example</span></span>

```c
/* Disconnect "my_client" from the FTP Server. */
status = nx_ftp_client_disconnect(&my_client, 200);

/* If status is NX_SUCCESS, "my_client" has been disconnected. */
```

## <a name="nx_ftp_client_file_close"></a><span data-ttu-id="0c97e-330">nx_ftp_client_file_close</span><span class="sxs-lookup"><span data-stu-id="0c97e-330">nx_ftp_client_file_close</span></span>

<span data-ttu-id="0c97e-331">Закрытие файла клиента</span><span class="sxs-lookup"><span data-stu-id="0c97e-331">Close Client file</span></span>

### <a name="prototype"></a><span data-ttu-id="0c97e-332">Прототип</span><span class="sxs-lookup"><span data-stu-id="0c97e-332">Prototype</span></span>

```c
UINT nx_ftp_client_file_close(NX_FTP_CLIENT *ftp_client_ptr,
                            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0c97e-333">Описание</span><span class="sxs-lookup"><span data-stu-id="0c97e-333">Description</span></span>

<span data-ttu-id="0c97e-334">Эта служба закрывает ранее открытый файл на FTP-сервере.</span><span class="sxs-lookup"><span data-stu-id="0c97e-334">This service closes a previously opened file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c97e-335">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0c97e-335">Input Parameters</span></span>

- <span data-ttu-id="0c97e-336">**client_ptr**: указатель на блок управления FTP-клиентом</span><span class="sxs-lookup"><span data-stu-id="0c97e-336">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="0c97e-337">**wait_option** определяет, как долго служба будет ожидать закрытия файла FTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="0c97e-337">**wait_option**: Defines how long the service will wait for the FTP Client file close.</span></span> <span data-ttu-id="0c97e-338">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="0c97e-338">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="0c97e-339">**Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0c97e-339">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="0c97e-340">**TX_WAIT_FOREVER** (0xFFFFFFFF) — указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="0c97e-340">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="0c97e-341">Числовое значение (от 1 до 0xFFFFFFFE) указывает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа FTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="0c97e-341">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="0c97e-342">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0c97e-342">Return Values</span></span>

- <span data-ttu-id="0c97e-343">**NX_SUCCESS** (0x00) — FTP-файл успешно закрыт.</span><span class="sxs-lookup"><span data-stu-id="0c97e-343">**NX_SUCCESS**: (0x00) Successful FTP file close.</span></span>
- <span data-ttu-id="0c97e-344">**NX_FTP_NOT_CONNECTED** (0xD3) — FTP-клиент не подключен.</span><span class="sxs-lookup"><span data-stu-id="0c97e-344">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="0c97e-345">**NX_FTP_NOT_OPEN (0xD5)**  — файл не открыт; его невозможно закрыть.</span><span class="sxs-lookup"><span data-stu-id="0c97e-345">**NX_FTP_NOT_OPEN (0xD5)**: File not open; cannot close it</span></span>
- <span data-ttu-id="0c97e-346">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) — ответ 2XX (OK) не получен.</span><span class="sxs-lookup"><span data-stu-id="0c97e-346">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="0c97e-347">NX_PTR_ERROR (0x07) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="0c97e-347">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="0c97e-348">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="0c97e-348">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c97e-349">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0c97e-349">Allowed From</span></span>

<span data-ttu-id="0c97e-350">Потоки</span><span class="sxs-lookup"><span data-stu-id="0c97e-350">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0c97e-351">Например, .</span><span class="sxs-lookup"><span data-stu-id="0c97e-351">Example</span></span>

```c
/* Close previously opened file of client "my_client" on the FTP Server. */
status = nx_ftp_client_file_close(&my_client, 200);

/* If status is NX_SUCCESS, the file opened previously in the "my_client" FTP
    connection has been closed. */
```

## <a name="nx_ftp_client_file_delete"></a><span data-ttu-id="0c97e-352">nx_ftp_client_file_delete</span><span class="sxs-lookup"><span data-stu-id="0c97e-352">nx_ftp_client_file_delete</span></span>

<span data-ttu-id="0c97e-353">Удаление файла на FTP-сервере</span><span class="sxs-lookup"><span data-stu-id="0c97e-353">Delete file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0c97e-354">Прототип</span><span class="sxs-lookup"><span data-stu-id="0c97e-354">Prototype</span></span>

```c
UINT nx_ftp_client_file_delete(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *file_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0c97e-355">Описание</span><span class="sxs-lookup"><span data-stu-id="0c97e-355">Description</span></span>

<span data-ttu-id="0c97e-356">Эта служба удаляет указанный файл на FTP-сервере.</span><span class="sxs-lookup"><span data-stu-id="0c97e-356">This service deletes the specified file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c97e-357">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0c97e-357">Input Parameters</span></span>

- <span data-ttu-id="0c97e-358">**client_ptr**: указатель на блок управления FTP-клиентом</span><span class="sxs-lookup"><span data-stu-id="0c97e-358">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="0c97e-359">**file_name**: имя файла для удаления</span><span class="sxs-lookup"><span data-stu-id="0c97e-359">**file_name**: Name of file to delete.</span></span>
- <span data-ttu-id="0c97e-360">**wait_option** определяет, как долго служба будет ожидать удаления файла FTP-клиента</span><span class="sxs-lookup"><span data-stu-id="0c97e-360">**wait_option**: Defines how long the service will wait for the FTP Client file delete.</span></span> <span data-ttu-id="0c97e-361">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="0c97e-361">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="0c97e-362">**Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0c97e-362">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="0c97e-363">**TX_WAIT_FOREVER** (0xFFFFFFFF) — указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="0c97e-363">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="0c97e-364">Числовое значение (от 1 до 0xFFFFFFFE) указывает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа FTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="0c97e-364">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="0c97e-365">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0c97e-365">Return Values</span></span>

- <span data-ttu-id="0c97e-366">**NX_SUCCESS** (0x00) — FTP-файл успешно удален.</span><span class="sxs-lookup"><span data-stu-id="0c97e-366">**NX_SUCCESS**: (0x00) Successful FTP file delete.</span></span>
- <span data-ttu-id="0c97e-367">**NX_FTP_NOT_CONNECTED** (0xD3) — FTP-клиент не подключен.</span><span class="sxs-lookup"><span data-stu-id="0c97e-367">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="0c97e-368">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) — ответ 2XX (OK) не получен.</span><span class="sxs-lookup"><span data-stu-id="0c97e-368">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="0c97e-369">NX_PTR_ERROR (0x07) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="0c97e-369">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="0c97e-370">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="0c97e-370">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c97e-371">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0c97e-371">Allowed From</span></span>

<span data-ttu-id="0c97e-372">Потоки</span><span class="sxs-lookup"><span data-stu-id="0c97e-372">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0c97e-373">Например, .</span><span class="sxs-lookup"><span data-stu-id="0c97e-373">Example</span></span>

```c
/* Delete the file "my_file.txt" on the FTP Server using the previously
    connected client "my_client." */
status = nx_ftp_client_file_delete(&my_client, "my_file.txt", 200);

/* If status is NX_SUCCESS, the file "my_file.txt" on the FTP Server is
    deleted. */
```

## <a name="nx_ftp_client_file_open"></a><span data-ttu-id="0c97e-374">nx_ftp_client_file_open</span><span class="sxs-lookup"><span data-stu-id="0c97e-374">nx_ftp_client_file_open</span></span>

<span data-ttu-id="0c97e-375">Открытие файла на FTP-сервере</span><span class="sxs-lookup"><span data-stu-id="0c97e-375">Opens file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0c97e-376">Прототип</span><span class="sxs-lookup"><span data-stu-id="0c97e-376">Prototype</span></span>

```c
UINT nx_ftp_client_file_open(NX_FTP_CLIENT *ftp_client_ptr,
        CHAR *file_name, UINT open_type, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0c97e-377">Описание</span><span class="sxs-lookup"><span data-stu-id="0c97e-377">Description</span></span>

<span data-ttu-id="0c97e-378">Эта служба открывает указанный файл для чтения или записи на FTP-сервере, ранее подключенном к указанному экземпляру клиента.</span><span class="sxs-lookup"><span data-stu-id="0c97e-378">This service opens the specified file – for reading or writing – on the FTP Server previously connected to the specified Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c97e-379">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0c97e-379">Input Parameters</span></span>

- <span data-ttu-id="0c97e-380">**client_ptr**: указатель на блок управления FTP-клиентом</span><span class="sxs-lookup"><span data-stu-id="0c97e-380">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="0c97e-381">**file_name**: имя файла для открытия</span><span class="sxs-lookup"><span data-stu-id="0c97e-381">**file_name**: Name of file to open.</span></span>
- <span data-ttu-id="0c97e-382">**open_type**: **NX_FTP_OPEN_FOR_READ** или **NX_FTP_OPEN_FOR_WRITE**</span><span class="sxs-lookup"><span data-stu-id="0c97e-382">**open_type**: Either **NX_FTP_OPEN_FOR_READ** or **NX_FTP_OPEN_FOR_WRITE**.</span></span>
- <span data-ttu-id="0c97e-383">**wait_option** определяет, как долго служба будет ожидать открытия файла FTP-клиента</span><span class="sxs-lookup"><span data-stu-id="0c97e-383">**wait_option**: Defines how long the service will wait for the FTP Client file open.</span></span> <span data-ttu-id="0c97e-384">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="0c97e-384">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="0c97e-385">**Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0c97e-385">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="0c97e-386">**TX_WAIT_FOREVER** (0xFFFFFFFF) — указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="0c97e-386">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="0c97e-387">Числовое значение (от 1 до 0xFFFFFFFE) указывает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа FTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="0c97e-387">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="0c97e-388">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0c97e-388">Return Values</span></span>

- <span data-ttu-id="0c97e-389">**NX_SUCCESS** (0x00) — FTP-файл успешно открыт.</span><span class="sxs-lookup"><span data-stu-id="0c97e-389">**NX_SUCCESS**: (0x00) Successful FTP file open.</span></span>
- <span data-ttu-id="0c97e-390">**NX_OPTION_ERROR** (0x0A) — недопустимый тип открытого файла.</span><span class="sxs-lookup"><span data-stu-id="0c97e-390">**NX_OPTION_ERROR**: (0x0A) Invalid open type.</span></span>
- <span data-ttu-id="0c97e-391">**NX_FTP_NOT_CONNECTED** (0xD3) — FTP-клиент не подключен.</span><span class="sxs-lookup"><span data-stu-id="0c97e-391">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="0c97e-392">**NX_FTP_NOT_CLOSED** (0xD6) — FTP-клиент уже открыт.</span><span class="sxs-lookup"><span data-stu-id="0c97e-392">**NX_FTP_NOT_CLOSED**: (0xD6) FTP Client is already opened.</span></span>
- <span data-ttu-id="0c97e-393">**NX_NO_FREE_PORTS** (0x45) — нет доступных портов TCP для назначения.</span><span class="sxs-lookup"><span data-stu-id="0c97e-393">**NX_NO_FREE_PORTS**: (0x45) No TCP ports available to assign</span></span>
- <span data-ttu-id="0c97e-394">NX_PTR_ERROR (0x07) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="0c97e-394">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="0c97e-395">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="0c97e-395">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c97e-396">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0c97e-396">Allowed From</span></span>

<span data-ttu-id="0c97e-397">Потоки</span><span class="sxs-lookup"><span data-stu-id="0c97e-397">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0c97e-398">Например, .</span><span class="sxs-lookup"><span data-stu-id="0c97e-398">Example</span></span>

```c
/* Open the file "my_file.txt" for reading on the FTP Server using the previously
    connected client "my_client." */
status = nx_ftp_client_file_open(&my_client, "my_file.txt", NX_FTP_OPEN_FOR_READ,
                                200);

/* If status is NX_SUCCESS, the file "my_file.txt" on the FTP Server is
    open for reading. */
```

## <a name="nx_ftp_client_file_read"></a><span data-ttu-id="0c97e-399">nx_ftp_client_file_read</span><span class="sxs-lookup"><span data-stu-id="0c97e-399">nx_ftp_client_file_read</span></span>

<span data-ttu-id="0c97e-400">Чтение из файла</span><span class="sxs-lookup"><span data-stu-id="0c97e-400">Read from file</span></span>

### <a name="prototype"></a><span data-ttu-id="0c97e-401">Прототип</span><span class="sxs-lookup"><span data-stu-id="0c97e-401">Prototype</span></span>

```c
UINT nx_ftp_client_file_read(NX_FTP_CLIENT *ftp_client_ptr,
                NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0c97e-402">Описание</span><span class="sxs-lookup"><span data-stu-id="0c97e-402">Description</span></span>

<span data-ttu-id="0c97e-403">Эта служба считывает пакет из ранее открытого файла.</span><span class="sxs-lookup"><span data-stu-id="0c97e-403">This service reads a packet from a previously opened file.</span></span> <span data-ttu-id="0c97e-404">Ее следует вызывать повторно, пока не будет получено состояние NX_FTP_END_OF_FILE.</span><span class="sxs-lookup"><span data-stu-id="0c97e-404">It should be called repetitively until a status of NX_FTP_END_OF_FILE is received.</span></span>

<span data-ttu-id="0c97e-405">Обратите внимание, что вызывающий объект не выделяет пакет для этой службы.</span><span class="sxs-lookup"><span data-stu-id="0c97e-405">Note that the caller does not allocate a packet for this service.</span></span>  <span data-ttu-id="0c97e-406">Он должен предоставлять только указатель на указатель пакета.</span><span class="sxs-lookup"><span data-stu-id="0c97e-406">It need only supply a pointer to a packet pointer.</span></span> <span data-ttu-id="0c97e-407">Эта служба обновит указатель на пакет так, чтобы он указывал на пакет, полученный из очереди получения сокета.</span><span class="sxs-lookup"><span data-stu-id="0c97e-407">This service will update that packet pointer to point to a packet retrieved from the socket receive queue.</span></span>  <span data-ttu-id="0c97e-408">Если возвращено успешное состояние, это означает, что пакет доступен, а вызывающий объект отвечает за освобождение пакета после завершения работы с ним.</span><span class="sxs-lookup"><span data-stu-id="0c97e-408">If a successful status is returned, that means there was a packet available, and it is the caller's responsibility to release the packet when it is done with it.</span></span>

<span data-ttu-id="0c97e-409">Если возвращается ненулевое состояние (состояние ошибки или NX_FTP_END_OF_FILE), вызывающий объект не освобождает пакет.</span><span class="sxs-lookup"><span data-stu-id="0c97e-409">If a non-zero status (either an error status or NX_FTP_END_OF_FILE) is returned, the caller does not release the packet.</span></span> <span data-ttu-id="0c97e-410">Если указатель пакета имеет значение NULL, возникает ошибка.</span><span class="sxs-lookup"><span data-stu-id="0c97e-410">Otherwise, an error is generated when if the packet pointer is NULL.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c97e-411">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0c97e-411">Input Parameters</span></span>

- <span data-ttu-id="0c97e-412">**client_ptr**: указатель на блок управления FTP-клиентом</span><span class="sxs-lookup"><span data-stu-id="0c97e-412">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="0c97e-413">**packet_ptr**: указатель на место назначения для указателя пакета данных, полученного из очереди</span><span class="sxs-lookup"><span data-stu-id="0c97e-413">**packet_ptr**: Pointer to destination for the data packet pointer retrieved from the queue.</span></span> <span data-ttu-id="0c97e-414">В случае успеха данные пакета будут содержать часть файла или файл полностью.</span><span class="sxs-lookup"><span data-stu-id="0c97e-414">If successful, the packet data contains some or all of the file.</span></span>
- <span data-ttu-id="0c97e-415">**wait_option** определяет, как долго служба будет ожидать чтения файла FTP-клиента</span><span class="sxs-lookup"><span data-stu-id="0c97e-415">**wait_option**: Defines how long the service will wait for the FTP Client file read.</span></span> <span data-ttu-id="0c97e-416">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="0c97e-416">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="0c97e-417">**Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0c97e-417">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="0c97e-418">**TX_WAIT_FOREVER** (0xFFFFFFFF) — указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="0c97e-418">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="0c97e-419">Числовое значение (от 1 до 0xFFFFFFFE) указывает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа FTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="0c97e-419">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="0c97e-420">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0c97e-420">Return Values</span></span>

- <span data-ttu-id="0c97e-421">**NX_SUCCESS** (0x00) — FTP-файл успешно считан.</span><span class="sxs-lookup"><span data-stu-id="0c97e-421">**NX_SUCCESS**: (0x00) Successful FTP file read.</span></span>
- <span data-ttu-id="0c97e-422">**NX_FTP_NOT_OPEN** (0xD5) — FTP-клиент не открыт.</span><span class="sxs-lookup"><span data-stu-id="0c97e-422">**NX_FTP_NOT_OPEN**: (0xD5) FTP Client is not opened.</span></span>
- <span data-ttu-id="0c97e-423">**NX_FTP_END_OF_FILE** (0xD7) — конец условия файла.</span><span class="sxs-lookup"><span data-stu-id="0c97e-423">**NX_FTP_END_OF_FILE**: (0xD7) End of file condition.</span></span>
- <span data-ttu-id="0c97e-424">NX_PTR_ERROR (0x07) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="0c97e-424">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="0c97e-425">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="0c97e-425">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c97e-426">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0c97e-426">Allowed From</span></span>

<span data-ttu-id="0c97e-427">Потоки</span><span class="sxs-lookup"><span data-stu-id="0c97e-427">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0c97e-428">Например, .</span><span class="sxs-lookup"><span data-stu-id="0c97e-428">Example</span></span>

```c
       NX_PACKET   *my_packet;

/* Read a packet of data from the file "my_file.txt" that was previously opened
    from the client "my_client." */

status = nx_ftp_client_file_read(&my_client, &my_packet, 200);

        /* Check status.  */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }
        else
        {
            /* Release packet when done with it. */
            nx_packet_release(my_packet);
        }

/* If status is NX_SUCCESS, the packet pointer, "my_packet" points to the packet
that contains the next bytes from the file. If the file is completely
downloaded, an NX_FTP_END_OF_FILE status is returned (no packet retrieved). */
```

## <a name="nx_ftp_client_file_rename"></a><span data-ttu-id="0c97e-429">nx_ftp_client_file_rename</span><span class="sxs-lookup"><span data-stu-id="0c97e-429">nx_ftp_client_file_rename</span></span>

<span data-ttu-id="0c97e-430">Переименование файла на FTP-сервере</span><span class="sxs-lookup"><span data-stu-id="0c97e-430">Rename file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0c97e-431">Прототип</span><span class="sxs-lookup"><span data-stu-id="0c97e-431">Prototype</span></span>

```c
UINT nx_ftp_client_file_rename(NX_FTP_CLIENT *ftp_ptr, CHAR *filename,
                                CHAR *new_filename, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0c97e-432">Описание</span><span class="sxs-lookup"><span data-stu-id="0c97e-432">Description</span></span>

<span data-ttu-id="0c97e-433">Эта служба переименовывает файл на FTP-сервере.</span><span class="sxs-lookup"><span data-stu-id="0c97e-433">This service renames a file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c97e-434">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0c97e-434">Input Parameters</span></span>

- <span data-ttu-id="0c97e-435">**client_ptr**: указатель на блок управления FTP-клиентом</span><span class="sxs-lookup"><span data-stu-id="0c97e-435">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="0c97e-436">**filename**: текущее имя файла</span><span class="sxs-lookup"><span data-stu-id="0c97e-436">**filename**: Current name of file.</span></span>
- <span data-ttu-id="0c97e-437">**new_filename**: новое имя файла</span><span class="sxs-lookup"><span data-stu-id="0c97e-437">**new_filename**: New name for file.</span></span>
- <span data-ttu-id="0c97e-438">**wait_option** определяет, как долго служба будет ожидать переименования файла FTP-клиента</span><span class="sxs-lookup"><span data-stu-id="0c97e-438">**wait_option**: Defines how long the service will wait for the FTP Client file rename.</span></span> <span data-ttu-id="0c97e-439">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="0c97e-439">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="0c97e-440">**Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0c97e-440">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="0c97e-441">**TX_WAIT_FOREVER** (0xFFFFFFFF) — указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="0c97e-441">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="0c97e-442">Числовое значение (от 1 до 0xFFFFFFFE) указывает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа FTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="0c97e-442">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="0c97e-443">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0c97e-443">Return Values</span></span>

- <span data-ttu-id="0c97e-444">**NX_SUCCESS** (0x00) — FTP-файл успешно переименован.</span><span class="sxs-lookup"><span data-stu-id="0c97e-444">**NX_SUCCESS**: (0x00) Successful FTP file rename.</span></span>
- <span data-ttu-id="0c97e-445">**NX_FTP_NOT_CONNECTED** (0xD3) — FTP-клиент не подключен.</span><span class="sxs-lookup"><span data-stu-id="0c97e-445">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="0c97e-446">**NX_FTP_EXPECTED_3XX_CODE** (0XDD) — ответ 3XX (OK) не получен.</span><span class="sxs-lookup"><span data-stu-id="0c97e-446">**NX_FTP_EXPECTED_3XX_CODE**: (0XDD) Did not receive 3XX (ok) response</span></span>
- <span data-ttu-id="0c97e-447">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) — ответ 2XX (OK) не получен.</span><span class="sxs-lookup"><span data-stu-id="0c97e-447">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="0c97e-448">NX_PTR_ERROR (0x07) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="0c97e-448">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="0c97e-449">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="0c97e-449">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c97e-450">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0c97e-450">Allowed From</span></span>

<span data-ttu-id="0c97e-451">Потоки</span><span class="sxs-lookup"><span data-stu-id="0c97e-451">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0c97e-452">Например, .</span><span class="sxs-lookup"><span data-stu-id="0c97e-452">Example</span></span>

```c
/* Rename file "my_file.txt" to "new_file.txt" on the previously connected
    Client instance "my_client." */

status = nx_ftp_client_file_rename(&my_client, "my_file.txt", "new_file.txt",
                                    200);

/* If status is NX_SUCCESS, the file has been renamed. */
```

## <a name="nx_ftp_client_file_write"></a><span data-ttu-id="0c97e-453">nx_ftp_client_file_write</span><span class="sxs-lookup"><span data-stu-id="0c97e-453">nx_ftp_client_file_write</span></span>

<span data-ttu-id="0c97e-454">Запись в файл</span><span class="sxs-lookup"><span data-stu-id="0c97e-454">Write to file</span></span>

### <a name="prototype"></a><span data-ttu-id="0c97e-455">Прототип</span><span class="sxs-lookup"><span data-stu-id="0c97e-455">Prototype</span></span>

```c
UINT nx_ftp_client_file_write(NX_FTP_CLIENT *ftp_client_ptr,
                    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0c97e-456">Описание</span><span class="sxs-lookup"><span data-stu-id="0c97e-456">Description</span></span>

<span data-ttu-id="0c97e-457">Эта служба записывает пакет данных в ранее открытый файл на FTP-сервере.</span><span class="sxs-lookup"><span data-stu-id="0c97e-457">This service writes a packet of data to the previously opened file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c97e-458">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0c97e-458">Input Parameters</span></span>

- <span data-ttu-id="0c97e-459">**client_ptr**: указатель на блок управления FTP-клиентом</span><span class="sxs-lookup"><span data-stu-id="0c97e-459">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="0c97e-460">**packet_ptr**: указатель пакета, содержащий данные для записи</span><span class="sxs-lookup"><span data-stu-id="0c97e-460">**packet_ptr**: Packet pointer containing data to write.</span></span>
- <span data-ttu-id="0c97e-461">**wait_option** определяет, как долго служба будет ожидать записи в файл FTP-клиента</span><span class="sxs-lookup"><span data-stu-id="0c97e-461">**wait_option**: Defines how long the service will wait for the FTP Client file write.</span></span> <span data-ttu-id="0c97e-462">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="0c97e-462">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="0c97e-463">**Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0c97e-463">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="0c97e-464">**TX_WAIT_FOREVER** (0xFFFFFFFF) — указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="0c97e-464">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="0c97e-465">Числовое значение (от 1 до 0xFFFFFFFE) указывает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа FTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="0c97e-465">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="0c97e-466">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0c97e-466">Return Values</span></span>

- <span data-ttu-id="0c97e-467">**NX_SUCCESS** (0x00) — запись в FTP-файл успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="0c97e-467">**NX_SUCCESS**: (0x00) Successful FTP file write.</span></span>
- <span data-ttu-id="0c97e-468">**NX_FTP_NOT_OPEN** (0xD5) — FTP-клиент не открыт.</span><span class="sxs-lookup"><span data-stu-id="0c97e-468">**NX_FTP_NOT_OPEN**: (0xD5) FTP Client is not opened.</span></span>
- <span data-ttu-id="0c97e-469">NX_PTR_ERROR (0x07) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="0c97e-469">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="0c97e-470">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="0c97e-470">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c97e-471">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0c97e-471">Allowed From</span></span>

<span data-ttu-id="0c97e-472">Потоки</span><span class="sxs-lookup"><span data-stu-id="0c97e-472">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0c97e-473">Например, .</span><span class="sxs-lookup"><span data-stu-id="0c97e-473">Example</span></span>

```c
/* Write the data contained in "my_packet" to the previously opened file
    "my_file.txt". */

status = nx_ftp_client_file_write(&my_client, my_packet, 200);

/* If status is NX_SUCCESS, the file has been written to. */
```

## <a name="nx_ftp_client_passive_mode_set"></a><span data-ttu-id="0c97e-474">nx_ftp_client_passive_mode_set</span><span class="sxs-lookup"><span data-stu-id="0c97e-474">nx_ftp_client_passive_mode_set</span></span>

<span data-ttu-id="0c97e-475">Включение или отключение пассивного режима передачи</span><span class="sxs-lookup"><span data-stu-id="0c97e-475">Enable or disable passive transfer mode</span></span>

### <a name="prototype"></a><span data-ttu-id="0c97e-476">Прототип</span><span class="sxs-lookup"><span data-stu-id="0c97e-476">Prototype</span></span>

```c
UINT nx_ftp_client_passive_mode_set(NX_FTP_CLIENT *ftp_client_ptr,
                                    UINT passive_mode_enabled);
```

### <a name="description"></a><span data-ttu-id="0c97e-477">Описание</span><span class="sxs-lookup"><span data-stu-id="0c97e-477">Description</span></span>

<span data-ttu-id="0c97e-478">Эта служба включает пассивный режим передачи, если для входных данных passive_mode_enabled задано NX_TRUE в ранее созданном экземпляре клиента FTP, так что последующие вызовы для чтения или записи файлов (RETR, STOR) или скачивания содержимого каталога (NLST) выполняются в режиме передачи.</span><span class="sxs-lookup"><span data-stu-id="0c97e-478">This service enables passive transfer mode if the passive_mode_enabled input is set to NX_TRUE on a previously created FTP Client instance such that subsequent calls to read or write files (RETR, STOR) or download a directory listing (NLST) are done in transfer mode.</span></span> <span data-ttu-id="0c97e-479">Чтобы отключить пассивный режим передачи и вернуться к заданному по умолчанию активному режиму передачи, вызовите эту функцию, для входных данных passive_mode_enabled которой задано NX_FALSE.</span><span class="sxs-lookup"><span data-stu-id="0c97e-479">To disable passive mode transfer and return to the default behavior of active transfer mode, call this function with the passive_mode_enabled input set to NX_FALSE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c97e-480">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0c97e-480">Input Parameters</span></span>

- <span data-ttu-id="0c97e-481">**client_ptr**: указатель на блок управления FTP-клиентом</span><span class="sxs-lookup"><span data-stu-id="0c97e-481">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="0c97e-482">**passive_mode_enabled**:</span><span class="sxs-lookup"><span data-stu-id="0c97e-482">**passive_mode_enabled**:</span></span>
  - <span data-ttu-id="0c97e-483">если задано значение NX_TRUE, пассивный режим включен;</span><span class="sxs-lookup"><span data-stu-id="0c97e-483">If set to NX_TRUE, passive mode is enabled.</span></span>
  - <span data-ttu-id="0c97e-484">если задано значение NX_FALSE, пассивный режим отключен.</span><span class="sxs-lookup"><span data-stu-id="0c97e-484">If set to NX_FALSE, passive mode is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="0c97e-485">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0c97e-485">Return Values</span></span>

- <span data-ttu-id="0c97e-486">**NX_SUCCESS** (0x00) — пассивный режим успешно задан.</span><span class="sxs-lookup"><span data-stu-id="0c97e-486">**NX_SUCCESS**: (0x00) Successful passive mode set.</span></span>
- <span data-ttu-id="0c97e-487">NX_PTR_ERROR (0x16) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="0c97e-487">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>
- <span data-ttu-id="0c97e-488">NX_INVALID_PARAMETERS (0x4D) — недопустимые входные данные, кроме указателей.</span><span class="sxs-lookup"><span data-stu-id="0c97e-488">NX_INVALID_PARAMETERS: (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c97e-489">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0c97e-489">Allowed From</span></span>

<span data-ttu-id="0c97e-490">Потоки</span><span class="sxs-lookup"><span data-stu-id="0c97e-490">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0c97e-491">Например, .</span><span class="sxs-lookup"><span data-stu-id="0c97e-491">Example</span></span>

```c
/* Enable the FTP Client to exchange data with the FTP server in passive mode. */

status = nx_ftp_client_passive_mode_set(&my_client, NX_TRUE);

/* If status is NX_SUCCESS, the FTP client is in passive transfer mode. */
```

## <a name="nx_ftp_server_create"></a><span data-ttu-id="0c97e-492">nx_ftp_server_create</span><span class="sxs-lookup"><span data-stu-id="0c97e-492">nx_ftp_server_create</span></span>

<span data-ttu-id="0c97e-493">Создание FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="0c97e-493">Create FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0c97e-494">Прототип</span><span class="sxs-lookup"><span data-stu-id="0c97e-494">Prototype</span></span>

```c
UINT nx_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
        CHAR *ftp_server_name, NX_IP *ip_ptr,
        FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
        NX_PACKET_POOL *pool_ptr,
        UINT (*ftp_login)(struct NX_FTP_SERVER_STRUCT
                *ftp_server_ptr, ULONG client_ip_address,
                UINT client_port, CHAR *name, CHAR *password,
                CHAR *extra_info),
        UINT (*ftp_logout)(struct NX_FTP_SERVER_STRUCT
                *ftp_server_ptr, ULONG client_ip_address,
                UINT client_port, CHAR *name, CHAR *password,
                CHAR *extra_info));
```

### <a name="description"></a><span data-ttu-id="0c97e-495">Описание</span><span class="sxs-lookup"><span data-stu-id="0c97e-495">Description</span></span>

<span data-ttu-id="0c97e-496">Эта служба создает экземпляр FTP-сервера в указанном и ранее созданном экземпляре IP для NetX.</span><span class="sxs-lookup"><span data-stu-id="0c97e-496">This service creates an FTP Server instance on the specified and previously created NetX IP instance.</span></span> <span data-ttu-id="0c97e-497">Обратите внимание, что для начала работы FTP-сервер должен быть запущен с помощью вызова службы ***nx_ftp_server_start***.</span><span class="sxs-lookup"><span data-stu-id="0c97e-497">Note the FTP Server needs to be started with a call to ***nx_ftp_server_start*** for it to begin operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c97e-498">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0c97e-498">Input Parameters</span></span>

- <span data-ttu-id="0c97e-499">**ftp_server_ptr**: указатель на блок управления FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="0c97e-499">**ftp_server_ptr**: Pointer to FTP Server control block.</span></span>
- <span data-ttu-id="0c97e-500">**ftp_server_name**: имя FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="0c97e-500">**ftp_server_name**: Name of FTP Server.</span></span>
- <span data-ttu-id="0c97e-501">**ip_ptr**: указатель на связанный экземпляр IP для NetX</span><span class="sxs-lookup"><span data-stu-id="0c97e-501">**ip_ptr**: Pointer to associated NetX IP instance.</span></span> <span data-ttu-id="0c97e-502">Обратите внимание, что для экземпляра IP может существовать только один FTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="0c97e-502">Note there can only be one FTP Server for an IP instance.</span></span>
- <span data-ttu-id="0c97e-503">**media_ptr**: указатель на связанный экземпляр носителя FileX</span><span class="sxs-lookup"><span data-stu-id="0c97e-503">**media_ptr**: Pointer to associated FileX media instance.</span></span>
- <span data-ttu-id="0c97e-504">**stack_ptr**: указатель на память области стека внутреннего потока FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="0c97e-504">**stack_ptr**: Pointer to memory for the internal FTP Server thread's stack area.</span></span>
- <span data-ttu-id="0c97e-505">**stack_size**: размер области стека, заданный параметром *stack_ptr*</span><span class="sxs-lookup"><span data-stu-id="0c97e-505">**stack_size**: Size of stack area specified by *stack_ptr*.</span></span>
- <span data-ttu-id="0c97e-506">**pool_ptr**: указатель на пул пакетов NetX по умолчанию</span><span class="sxs-lookup"><span data-stu-id="0c97e-506">**pool_ptr**: Pointer to default NetX packet pool.</span></span> <span data-ttu-id="0c97e-507">Обратите внимание, что размер полезных данных пакетов в пуле должен быть достаточно большим, чтобы вмещать максимально длинное имя файла или путь.</span><span class="sxs-lookup"><span data-stu-id="0c97e-507">Note the payload size of packets in the pool must be large enough to accommodate the largest filename/path.</span></span>
- <span data-ttu-id="0c97e-508">**ftp_login**: указатель функции для функции входа в приложение</span><span class="sxs-lookup"><span data-stu-id="0c97e-508">**ftp_login**: Function pointer to application's login function.</span></span> <span data-ttu-id="0c97e-509">Эта функция предоставляет имя пользователя и пароль от клиента, запросившего подключение.</span><span class="sxs-lookup"><span data-stu-id="0c97e-509">This function is supplied the username and password from the Client requesting a connection.</span></span> <span data-ttu-id="0c97e-510">Если они являются допустимыми, функция входа в приложение должна вернуть NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="0c97e-510">If this is valid, the application's login function should return NX_SUCCESS.</span></span>
- <span data-ttu-id="0c97e-511">**ftp_logout**: указатель функции на функцию выхода из приложения</span><span class="sxs-lookup"><span data-stu-id="0c97e-511">**ftp_logout**: Function pointer to application's logout function.</span></span> <span data-ttu-id="0c97e-512">Эта функция предоставляет имя пользователя и пароль от клиента, запросившего отключение.</span><span class="sxs-lookup"><span data-stu-id="0c97e-512">This function is supplied the username and password from the Client requesting a disconnection.</span></span> <span data-ttu-id="0c97e-513">Если они являются допустимыми, функция входа в приложение должна вернуть NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="0c97e-513">If this is valid, the application's login function should return NX_SUCCESS.</span></span>

### <a name="return-values"></a><span data-ttu-id="0c97e-514">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0c97e-514">Return Values</span></span>

- <span data-ttu-id="0c97e-515">**NX_SUCCESS** (0x00) — FTP-сервер успешно создан.</span><span class="sxs-lookup"><span data-stu-id="0c97e-515">**NX_SUCCESS**: (0x00) Successful FTP Server create.</span></span>
- <span data-ttu-id="0c97e-516">NX_PTR_ERROR (0x16) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="0c97e-516">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c97e-517">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0c97e-517">Allowed From</span></span>

<span data-ttu-id="0c97e-518">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="0c97e-518">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="0c97e-519">Например, .</span><span class="sxs-lookup"><span data-stu-id="0c97e-519">Example</span></span>

```c
/* Create the FTP Server "my_server" on the IP instance "ip_0" using the
    "ram_disk" media. */

status = nx_ftp_server_create(&my_server, "My Server Name", &ip_0, &ram_disk,
                                stack_ptr, stack_size, &pool_0,
                                my_login, my_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nx_ftp_server_delete"></a><span data-ttu-id="0c97e-520">nx_ftp_server_delete</span><span class="sxs-lookup"><span data-stu-id="0c97e-520">nx_ftp_server_delete</span></span>

<span data-ttu-id="0c97e-521">Удаление FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="0c97e-521">Delete FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0c97e-522">Прототип</span><span class="sxs-lookup"><span data-stu-id="0c97e-522">Prototype</span></span>

```c
UINT nx_ftp_server_delete(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="0c97e-523">Описание</span><span class="sxs-lookup"><span data-stu-id="0c97e-523">Description</span></span>

<span data-ttu-id="0c97e-524">Эта служба удаляет ранее созданный экземпляр FTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="0c97e-524">This service deletes a previously created FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c97e-525">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0c97e-525">Input Parameters</span></span>

- <span data-ttu-id="0c97e-526">**ftp_server_ptr**: указатель на блок управления FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="0c97e-526">**ftp_server_ptr**: Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="0c97e-527">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0c97e-527">Return Values</span></span>

- <span data-ttu-id="0c97e-528">**NX_SUCCESS** (0x00) — FTP-сервер успешно удален.</span><span class="sxs-lookup"><span data-stu-id="0c97e-528">**NX_SUCCESS**: (0x00) Successful FTP Server delete.</span></span>
- <span data-ttu-id="0c97e-529">NX_PTR_ERROR (0x16) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="0c97e-529">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>
- <span data-ttu-id="0c97e-530">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="0c97e-530">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c97e-531">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0c97e-531">Allowed From</span></span>

<span data-ttu-id="0c97e-532">Потоки</span><span class="sxs-lookup"><span data-stu-id="0c97e-532">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0c97e-533">Например, .</span><span class="sxs-lookup"><span data-stu-id="0c97e-533">Example</span></span>

```c
/* Delete the FTP Server "my_server". */

status = nx_ftp_server_delete(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been deleted. */
```

## <a name="nx_ftp_server_start"></a><span data-ttu-id="0c97e-534">nx_ftp_server_start</span><span class="sxs-lookup"><span data-stu-id="0c97e-534">nx_ftp_server_start</span></span>

<span data-ttu-id="0c97e-535">Запуск FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="0c97e-535">Start FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0c97e-536">Прототип</span><span class="sxs-lookup"><span data-stu-id="0c97e-536">Prototype</span></span>

```c
UINT nx_ftp_server_start(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="0c97e-537">Описание</span><span class="sxs-lookup"><span data-stu-id="0c97e-537">Description</span></span>

<span data-ttu-id="0c97e-538">Эта служба запускает ранее созданный экземпляр FTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="0c97e-538">This service starts a previously created FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c97e-539">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0c97e-539">Input Parameters</span></span>

- <span data-ttu-id="0c97e-540">**ftp_server_ptr**: указатель на блок управления FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="0c97e-540">**ftp_server_ptr**: Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="0c97e-541">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0c97e-541">Return Values</span></span>

- <span data-ttu-id="0c97e-542">**NX_SUCCESS** (0x00) — FTP-сервер успешно запущен.</span><span class="sxs-lookup"><span data-stu-id="0c97e-542">**NX_SUCCESS**: (0x00) Successful FTP Server start.</span></span>
- <span data-ttu-id="0c97e-543">NX_PTR_ERROR (0x16) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="0c97e-543">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c97e-544">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0c97e-544">Allowed From</span></span>

<span data-ttu-id="0c97e-545">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="0c97e-545">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="0c97e-546">Например, .</span><span class="sxs-lookup"><span data-stu-id="0c97e-546">Example</span></span>

```c
/* Start the FTP Server "my_server". */

status = nx_ftp_server_start(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been started. */
```

## <a name="nx_ftp_server_stop"></a><span data-ttu-id="0c97e-547">nx_ftp_server_stop</span><span class="sxs-lookup"><span data-stu-id="0c97e-547">nx_ftp_server_stop</span></span>

<span data-ttu-id="0c97e-548">Остановка FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="0c97e-548">Stop FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0c97e-549">Прототип</span><span class="sxs-lookup"><span data-stu-id="0c97e-549">Prototype</span></span>

```c
UINT nx_ftp_server_stop(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="0c97e-550">Описание</span><span class="sxs-lookup"><span data-stu-id="0c97e-550">Description</span></span>

<span data-ttu-id="0c97e-551">Эта служба останавливает ранее созданный и запущенный экземпляр FTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="0c97e-551">This service stops a previously created and started FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c97e-552">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0c97e-552">Input Parameters</span></span>

- <span data-ttu-id="0c97e-553">**ftp_server_ptr**: указатель на блок управления FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="0c97e-553">**ftp_server_ptr**: Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="0c97e-554">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0c97e-554">Return Values</span></span>

- <span data-ttu-id="0c97e-555">**NX_SUCCESS** (0x00) — FTP-сервер успешно остановлен.</span><span class="sxs-lookup"><span data-stu-id="0c97e-555">**NX_SUCCESS**: (0x00) Successful FTP Server stop.</span></span>
- <span data-ttu-id="0c97e-556">NX_PTR_ERROR (0x16) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="0c97e-556">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>
- <span data-ttu-id="0c97e-557">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="0c97e-557">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c97e-558">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0c97e-558">Allowed From</span></span>

<span data-ttu-id="0c97e-559">Потоки</span><span class="sxs-lookup"><span data-stu-id="0c97e-559">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0c97e-560">Пример</span><span class="sxs-lookup"><span data-stu-id="0c97e-560">Example</span></span>

```c
/* Stop the FTP Server "my_server". */

status = nx_ftp_server_stop(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been stopped. */
```
