---
title: Глава 3. Описание служб протокола PPP для NetX Duo для ОСРВ Azure
description: В этой главе приводится описание всех служб PPP для NetX Duo для ОСРВ Azure, которые перечислены ниже в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 90c24cad5e595087ba27178243f9dda0dab11029
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814603"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-point-to-point-protocol-ppp-services"></a><span data-ttu-id="f3886-103">Глава 3. Описание служб протокола PPP для NetX Duo для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="f3886-103">Chapter 3 - Description of Azure RTOS NetX Duo Point-to-Point Protocol (PPP) services</span></span>

<span data-ttu-id="f3886-104">В этой главе приводится описание всех служб PPP для NetX Duo для ОСРВ Azure, которые перечислены ниже в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="f3886-104">This chapter contains a description of all Azure RTOS NetX Duo PPP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="f3886-105">В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки ошибок API, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="f3886-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="f3886-106">**nx_ppp_byte_receive**: *получение байта от подпрограммы обработки прерываний (ISR) последовательного порта*</span><span class="sxs-lookup"><span data-stu-id="f3886-106">**nx_ppp_byte_receive**: *Receive a byte from serial ISR*</span></span>
- <span data-ttu-id="f3886-107">**nx_ppp_chap_challenge**: *создание запроса CHAP*</span><span class="sxs-lookup"><span data-stu-id="f3886-107">**nx_ppp_chap_challenge**: *Generate a CHAP challenge*</span></span>
- <span data-ttu-id="f3886-108">**nx_ppp_chap_enable**: *включение проверки подлинности CHAP*</span><span class="sxs-lookup"><span data-stu-id="f3886-108">**nx_ppp_chap_enable**: *Enable CHAP authentication*</span></span>
- <span data-ttu-id="f3886-109">**nx_ppp_create**: *создание экземпляра PPP*</span><span class="sxs-lookup"><span data-stu-id="f3886-109">**nx_ppp_create**: *Create a PPP instance*</span></span>
- <span data-ttu-id="f3886-110">**nx_ppp_delete**: *удаление экземпляра PPP*</span><span class="sxs-lookup"><span data-stu-id="f3886-110">**nx_ppp_delete**: *Delete a PPP instance*</span></span>
- <span data-ttu-id="f3886-111">**nx_ppp_dns_address_get**: *получение IP-адреса сервера DNS*</span><span class="sxs-lookup"><span data-stu-id="f3886-111">**nx_ppp_dns_address_get**: *Get DNS Server IP address*</span></span>
- <span data-ttu-id="f3886-112">**nx_ppp_dns_address_set**: *настройка IP-адреса сервера DNS*</span><span class="sxs-lookup"><span data-stu-id="f3886-112">**nx_ppp_dns_address_set**:*Set DNS Server IP address*</span></span>
- <span data-ttu-id="f3886-113">**nx_ppp_secondary_dns_address_get**: *получение IP-адреса вторичного сервера DNS*</span><span class="sxs-lookup"><span data-stu-id="f3886-113">**nx_ppp_secondary_dns_address_get**: *Get Secondary DNS Server IP address*</span></span>
- <span data-ttu-id="f3886-114">**nx_ppp_secondary_dns_address_set**: *настройка IP-адреса вторичного сервера DNS*</span><span class="sxs-lookup"><span data-stu-id="f3886-114">**nx_ppp_secondary_dns_address_set**: *Set Secondary_DNS Server IP address*</span></span>
- <span data-ttu-id="f3886-115">**nx_ppp_interface_index_get**: *получение индекса IP-интерфейса*</span><span class="sxs-lookup"><span data-stu-id="f3886-115">**nx_ppp_interface_index_get**: *Get IP interface index*</span></span>
- <span data-ttu-id="f3886-116">**nx_ppp_ip_address_assign**: *назначение IP-адресов для IPCP*</span><span class="sxs-lookup"><span data-stu-id="f3886-116">**nx_ppp_ip_address_assign**: *Assign IP addresses for IPCP*</span></span>
- <span data-ttu-id="f3886-117">**nx_ppp_link_down_notify**: *оповещение приложения об отключении канала*</span><span class="sxs-lookup"><span data-stu-id="f3886-117">**nx_ppp_link_down_notify**: *Notify application on link down*</span></span>
- <span data-ttu-id="f3886-118">**nx_ppp_link_up_notify**: *оповещение приложения о включении канала*</span><span class="sxs-lookup"><span data-stu-id="f3886-118">**nx_ppp_link_up_notify**: *Notify application on link up*</span></span>
- <span data-ttu-id="f3886-119">**nx_ppp_nak_authentication_notify**: *оповещение приложения о получении пакета NAK при проверке подлинности*</span><span class="sxs-lookup"><span data-stu-id="f3886-119">**nx_ppp_nak_authentication_notify**: *Notify application if authentication NAK is received*</span></span>
- <span data-ttu-id="f3886-120">**nx_ppp_pap_enable**: *включение проверки подлинности PAP*</span><span class="sxs-lookup"><span data-stu-id="f3886-120">**nx_ppp_pap_enable**: *Enable PAP authentication*</span></span>
- <span data-ttu-id="f3886-121">**nx_ppp_ping_request**: *отправка запроса проверки связи LCP*</span><span class="sxs-lookup"><span data-stu-id="f3886-121">**nx_ppp_ping_request**: *Send an LCP echo request*</span></span>
- <span data-ttu-id="f3886-122">**nx_ppp_raw_string_send**: *отправка строки без протокола PPP*</span><span class="sxs-lookup"><span data-stu-id="f3886-122">**nx_ppp_raw_string_send**: *Send non PPP string*</span></span>
- <span data-ttu-id="f3886-123">**nx_ppp_restart**: *перезапуск обработки PPP*</span><span class="sxs-lookup"><span data-stu-id="f3886-123">**nx_ppp_restart**: *Restart PPP processing*</span></span>
- <span data-ttu-id="f3886-124">**nx_ppp_start**: *начало обработки PPP*</span><span class="sxs-lookup"><span data-stu-id="f3886-124">**nx_ppp_start**: *Start PPP processing*</span></span>
- <span data-ttu-id="f3886-125">**nx_ppp_status_get**: *получение текущего состояния PPP*</span><span class="sxs-lookup"><span data-stu-id="f3886-125">**nx_ppp_status_get**: *Get current PPP status*</span></span>
- <span data-ttu-id="f3886-126">**nx_ppp_stop**: *прекращение обработки PPP*</span><span class="sxs-lookup"><span data-stu-id="f3886-126">**nx_ppp_stop**: *Stop PPP processing*</span></span>
- <span data-ttu-id="f3886-127">**nx_ppp_packet_receive**: *получение пакета PPP*</span><span class="sxs-lookup"><span data-stu-id="f3886-127">**nx_ppp_packet_receive**: *Receive PPP packet*</span></span>
- <span data-ttu-id="f3886-128">**nx_ppp_packet_send_set**: *настройка функции отправки пакета PPP*</span><span class="sxs-lookup"><span data-stu-id="f3886-128">**nx_ppp_packet_send_set**: *Set PPP packet send function*</span></span>

## <a name="nx_ppp_byte_receive"></a><span data-ttu-id="f3886-129">nx_ppp_byte_receive</span><span class="sxs-lookup"><span data-stu-id="f3886-129">nx_ppp_byte_receive</span></span>

<span data-ttu-id="f3886-130">Получение байта от ISR последовательного порта</span><span class="sxs-lookup"><span data-stu-id="f3886-130">Receive a byte from serial ISR</span></span>

### <a name="prototype"></a><span data-ttu-id="f3886-131">Прототип</span><span class="sxs-lookup"><span data-stu-id="f3886-131">Prototype</span></span>

```c
UINT nx_ppp_byte_receive(NX_PPP *ppp_ptr, UCHAR byte);
```

### <a name="description"></a><span data-ttu-id="f3886-132">Описание</span><span class="sxs-lookup"><span data-stu-id="f3886-132">Description</span></span>

<span data-ttu-id="f3886-133">Обычно эта служба вызывается в приложении из ISR драйвера последовательного порта, чтобы передать байт в канал PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-133">This service is typically called from the application’s serial driver Interrupt Service Routine (ISR) to transfer a received byte to PPP.</span></span> <span data-ttu-id="f3886-134">При вызове эта подпрограмма помещает полученный байт в циклический буфер байтов и оповещает соответствующий поток PPP о необходимости обработки.</span><span class="sxs-lookup"><span data-stu-id="f3886-134">When called, this routine places the received byte into a circular byte buffer and notifies the appropriate PPP thread for processing.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f3886-135">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="f3886-135">Input Parameters</span></span>

- <span data-ttu-id="f3886-136">**ppp_ptr**: указатель на блок управления PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-136">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="f3886-137">**byte**: байт, полученный от устройства c последовательным интерфейсом.</span><span class="sxs-lookup"><span data-stu-id="f3886-137">**byte**: Byte received from serial device</span></span>

### <a name="return-values"></a><span data-ttu-id="f3886-138">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="f3886-138">Return Values</span></span>

- <span data-ttu-id="f3886-139">**NX_SUCCESS** (0x00): успешное получение байта в PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-139">**NX_SUCCESS**: (0x00) Successful PPP byte receive.</span></span>
- <span data-ttu-id="f3886-140">**NX_PPP_BUFFER_FULL** (0xB1): последовательный буфер PPP заполнен.</span><span class="sxs-lookup"><span data-stu-id="f3886-140">**NX_PPP_BUFFER_FULL**: (0xB1) PPP serial buffer is already full.</span></span>
- <span data-ttu-id="f3886-141">NX_PTR_ERROR (0x07): недопустимый указатель PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-141">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f3886-142">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="f3886-142">Allowed From</span></span>

<span data-ttu-id="f3886-143">Потоки, подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="f3886-143">Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="f3886-144">Например, .</span><span class="sxs-lookup"><span data-stu-id="f3886-144">Example</span></span>

```c
/* Notify “my_ppp” of a received byte. */
status =  nx_ppp_byte_receive(&my_ppp, new_byte);

/* If status is NX_SUCCESS the received byte was successfully
   buffered. */
```

## <a name="nx_ppp_chap_challenge"></a><span data-ttu-id="f3886-145">nx_ppp_chap_challenge</span><span class="sxs-lookup"><span data-stu-id="f3886-145">nx_ppp_chap_challenge</span></span>

<span data-ttu-id="f3886-146">Создание запроса CHAP</span><span class="sxs-lookup"><span data-stu-id="f3886-146">Generate a CHAP challenge</span></span>

### <a name="prototype"></a><span data-ttu-id="f3886-147">Прототип</span><span class="sxs-lookup"><span data-stu-id="f3886-147">Prototype</span></span>

```c
UINT nx_ppp_chap_challenge(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="f3886-148">Описание</span><span class="sxs-lookup"><span data-stu-id="f3886-148">Description</span></span>

<span data-ttu-id="f3886-149">Эта служба создает запрос CHAP, когда подключение PPP уже установлено и успешно работает.</span><span class="sxs-lookup"><span data-stu-id="f3886-149">This service initiates a CHAP challenge after the PPP connection is already up and running.</span></span> <span data-ttu-id="f3886-150">Это дает приложению возможность периодически контролировать подлинность в подключении.</span><span class="sxs-lookup"><span data-stu-id="f3886-150">This gives the application the ability to verify the authenticity of the connection on a periodic basis.</span></span> <span data-ttu-id="f3886-151">Если нужный ответ на запрос не поступает, канал PPP закрывается.</span><span class="sxs-lookup"><span data-stu-id="f3886-151">If the challenge is unsuccessful, the PPP link is closed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f3886-152">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="f3886-152">Input Parameters</span></span>

- <span data-ttu-id="f3886-153">**ppp_ptr**: указатель на блок управления PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-153">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="f3886-154">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="f3886-154">Return Values</span></span>

- <span data-ttu-id="f3886-155">**NX_SUCCESS** (0x00): запрос PPP инициирован успешно.</span><span class="sxs-lookup"><span data-stu-id="f3886-155">**NX_SUCCESS**: (0x00) Successful PPP challenge initiated.</span></span>
- <span data-ttu-id="f3886-156">**NX_PPP_FAILURE** (0xB0): недопустимый запрос PPP, CHAP включался только для ответа.</span><span class="sxs-lookup"><span data-stu-id="f3886-156">**NX_PPP_FAILURE**: (0xB0) Invalid PPP challenge, CHAP was enabled only for response.</span></span>
- <span data-ttu-id="f3886-157">**NX_NOT_IMPLEMENTED** (0x80): логика CHAP была отключена с помощью NX_PPP_DISABLE_CHAP.</span><span class="sxs-lookup"><span data-stu-id="f3886-157">**NX_NOT_IMPLEMENTED**: (0x80) CHAP logic was disabled via NX_PPP_DISABLE_CHAP.</span></span>
- <span data-ttu-id="f3886-158">NX_PTR_ERROR (0x07): недопустимый указатель PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-158">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="f3886-159">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="f3886-159">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f3886-160">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="f3886-160">Allowed From</span></span>

<span data-ttu-id="f3886-161">Потоки</span><span class="sxs-lookup"><span data-stu-id="f3886-161">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f3886-162">Например, .</span><span class="sxs-lookup"><span data-stu-id="f3886-162">Example</span></span>

```c
/* Initiate a PPP challenge for instance “my_ppp”. */
status =  nx_ppp_chap_challenge(&my_ppp);

/* If status is NX_SUCCESS a CHAP challenge “my_ppp” was successfully 
initiated. */
```

## <a name="nx_ppp_chap_enable"></a><span data-ttu-id="f3886-163">nx_ppp_chap_enable</span><span class="sxs-lookup"><span data-stu-id="f3886-163">nx_ppp_chap_enable</span></span>

<span data-ttu-id="f3886-164">Включение проверки подлинности CHAP</span><span class="sxs-lookup"><span data-stu-id="f3886-164">Enable CHAP authentication</span></span>

### <a name="prototype"></a><span data-ttu-id="f3886-165">Прототип</span><span class="sxs-lookup"><span data-stu-id="f3886-165">Prototype</span></span>

```c
UINT nx_ppp_chap_enable(NX_PPP *ppp_ptr, 
                        UINT (*get_challenge_values)(CHAR *rand_value,CHAR *id,CHAR *name),
                        UINT (*get_responder_values)(CHAR *system,CHAR *name,CHAR *secret),
                        UINT (*get_verification_values)(CHAR *system,CHAR *name,CHAR *secret)); 
```

### <a name="description"></a><span data-ttu-id="f3886-166">Описание</span><span class="sxs-lookup"><span data-stu-id="f3886-166">Description</span></span>

<span data-ttu-id="f3886-167">Эта служба включает протокол CHAP (Challenge-Handshake Authentication Protocol) для указанного экземпляра PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-167">This service enables the Challenge-Handshake Authentication Protocol (CHAP) for the specified PPP instance.</span></span>

<span data-ttu-id="f3886-168">Если определены указатели на функции \***get_challenge_values**_и_\*_get_verification_values_\*\*, CHAP является обязательным для этого экземпляра PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-168">If the “\***get_challenge_values**_” and “_\*_get_verification_values_\*\*” function pointers are specified, CHAP is required by this PPP instance.</span></span> <span data-ttu-id="f3886-169">В противном случае CHAP активируется только по запросу другой стороны канала.</span><span class="sxs-lookup"><span data-stu-id="f3886-169">Otherwise, CHAP only responds to the peer’s challenge requests.</span></span>

<span data-ttu-id="f3886-170">Ниже упоминаются несколько элементов данных, которые используются в обязательных функциях обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="f3886-170">There are several data items referenced below in the required callback functions.</span></span> <span data-ttu-id="f3886-171">Элементы данных *secret*, *name* и *system* должны иметь формат строк, оканчивающихся символом NULL, и размер, не превышающий значения NX_PPP_NAME_SIZE-1.</span><span class="sxs-lookup"><span data-stu-id="f3886-171">The data items *secret*, *name*, and *system* are expected to be NULL-terminated strings with a maximum size of NX_PPP_NAME_SIZE-1.</span></span> <span data-ttu-id="f3886-172">Элемент данных *rand_value* должен иметь формат строки, оканчивающейся символом NULL, и размер, не превышающий значения NX_PPP_VALUE_SIZE-1.</span><span class="sxs-lookup"><span data-stu-id="f3886-172">The data item *rand_value* is expected to be a NULL-terminated string with a maximum size of NX_PPP_VALUE_SIZE-1.</span></span> <span data-ttu-id="f3886-173">Элемент данных *id* имеет простой символьный тип без знака.</span><span class="sxs-lookup"><span data-stu-id="f3886-173">The data item *id* is a simple unsigned character type.</span></span>

>[!NOTE]
> <span data-ttu-id="f3886-174">Эта функция должна вызываться после *nx_ppp_create*, но раньше nx_ip_create или *nx_ip_interface_attach*.</span><span class="sxs-lookup"><span data-stu-id="f3886-174">This function must be called after *nx_ppp_create* but before nx_ip_create or *nx_ip_interface_attach*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f3886-175">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="f3886-175">Input Parameters</span></span>

- <span data-ttu-id="f3886-176">**ppp_ptr**: указатель на блок управления PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-176">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="f3886-177">**get_challenge_values**: указатель на функцию приложения, которая извлекает значения для создания запроса.</span><span class="sxs-lookup"><span data-stu-id="f3886-177">**get_challenge_values**: Pointer to application function to retrieve values used for the challenge.</span></span> <span data-ttu-id="f3886-178">Обратите внимание, что значения *rand_value*, *id* и *secret* должны быть скопированы в указанные места назначения.</span><span class="sxs-lookup"><span data-stu-id="f3886-178">Note that the *rand_value*, *id*, and *secret* values must be copied into the supplied destinations.</span></span>
- <span data-ttu-id="f3886-179">**get_responder_values**: указатель на функцию приложения, которая извлекает значения для ответа на запрос.</span><span class="sxs-lookup"><span data-stu-id="f3886-179">**get_responder_values**: Pointer to application function that retrieves values used to respond to a challenge.</span></span> <span data-ttu-id="f3886-180">Обратите внимание, что значения *system*, *name* и *secret* должны быть скопированы в указанные места назначения.</span><span class="sxs-lookup"><span data-stu-id="f3886-180">Note that the *system*, *name*, and *secret* values must be copied into the supplied destinations.</span></span>
- <span data-ttu-id="f3886-181">**get_verification_values**: указатель на функцию приложения, которая извлекает значения для проверки ответа на запрос.</span><span class="sxs-lookup"><span data-stu-id="f3886-181">**get_verification_values**: Pointer to application function that retrieves values used to verify the challenge response.</span></span> <span data-ttu-id="f3886-182">Обратите внимание, что значения *system*, *name* и *secret* должны быть скопированы в указанные места назначения.</span><span class="sxs-lookup"><span data-stu-id="f3886-182">Note that the *system*,*name*, and *secret* values must be copied into the supplied destinations.</span></span>

### <a name="return-values"></a><span data-ttu-id="f3886-183">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="f3886-183">Return Values</span></span>

- <span data-ttu-id="f3886-184">**NX_SUCCESS** (0x00): PPP CHAP успешно включено.</span><span class="sxs-lookup"><span data-stu-id="f3886-184">**NX_SUCCESS**: (0x00) Successful PPP CHAP enable</span></span>
- <span data-ttu-id="f3886-185">**NX_NOT_IMPLEMENTED** (0x80): логика CHAP была отключена с помощью NX_PPP_DISABLE_CHAP.</span><span class="sxs-lookup"><span data-stu-id="f3886-185">**NX_NOT_IMPLEMENTED**: (0x80) CHAP logic was disabled via NX_PPP_DISABLE_CHAP.</span></span>
- <span data-ttu-id="f3886-186">NX_PTR_ERROR (0x07): недопустимый указатель PPP или указатель на функцию обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="f3886-186">NX_PTR_ERROR: (0x07) Invalid PPP pointer or callback function pointer.</span></span> <span data-ttu-id="f3886-187">Обратите внимание, что если предоставлена функция *get_challenge_values*, необходимо предоставить и функцию *get_verification_values*.</span><span class="sxs-lookup"><span data-stu-id="f3886-187">Note that if *get_challenge_values* is specified, then the *get_verification_values* function must also be supplied.</span></span>
- <span data-ttu-id="f3886-188">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="f3886-188">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f3886-189">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="f3886-189">Allowed From</span></span>

<span data-ttu-id="f3886-190">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="f3886-190">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="f3886-191">Например, .</span><span class="sxs-lookup"><span data-stu-id="f3886-191">Example</span></span>

```c
CHAR    name_string[] = "username";
CHAR    rand_value_string[] = "123456";
CHAR    system_string[] = "system";
CHAR    secret_string[] = "secret";

/* Enable CHAP in both directions (CHAP challenger and CHAP responder) for 
“my_ppp”. */
status =  nx_ppp_chap_enable(&my_ppp,   get_challenge_values, 
                              get_responder_values,
                              get_verification_values);


/* If status is NX_SUCCESS, “my_ppp” has CHAP enabled. */
/* Define the CHAP enable routines.  */
UINT  get_challenge_values(CHAR *rand_value, CHAR *id, CHAR *name)
{
   UINT    i;
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;
   
   *id =  '1';  /* One byte  */
   for (i = 0; i< (NX_PPP_VALUE_SIZE-1); i++)
   {
      rand_value[i] =  rand_value_string[i];
   }
   rand_value[i] =  0;
   
   return(NX_SUCCESS);  
}


UINT  get_responder_values(CHAR *system, CHAR *name, CHAR *secret)
{
   UINT    i;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;

   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      system[i] =  system_string[i];
   }
   system[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      secret[i] =  secret_string[i];
   }
   secret[i] =  0;
   
   return(NX_SUCCESS);  
}

UINT  get_verification_values(CHAR *system, CHAR *name, CHAR *secret)
{
   UINT    i;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      system[i] =  system_string[i];
   }
   system[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      secret[i] =  secret_string[i];
   }
   secret[i] =  0;
   
   return(NX_SUCCESS);  
}

```
## <a name="nx_ppp_create"></a><span data-ttu-id="f3886-192">nx_ppp_create</span><span class="sxs-lookup"><span data-stu-id="f3886-192">nx_ppp_create</span></span>

<span data-ttu-id="f3886-193">Создание экземпляра PPP</span><span class="sxs-lookup"><span data-stu-id="f3886-193">Create a PPP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="f3886-194">Прототип</span><span class="sxs-lookup"><span data-stu-id="f3886-194">Prototype</span></span>

```c
UINT  nx_ppp_create(NX_PPP *ppp_ptr, CHAR *name, NX_IP *ip_ptr, 
                    VOID *stack_memory_ptr, ULONG stack_size, 
                    UINT thread_priority, NX_PACKET_POOL *pool_ptr,
                    void (*ppp_invalid_packet_handler)(NX_PACKET *packet_ptr),
                    void (*ppp_byte_send)(UCHAR byte));
```

### <a name="description"></a><span data-ttu-id="f3886-195">Описание</span><span class="sxs-lookup"><span data-stu-id="f3886-195">Description</span></span>

<span data-ttu-id="f3886-196">Эта служба создает экземпляр PPP для указанного экземпляра IP-адреса NetX.</span><span class="sxs-lookup"><span data-stu-id="f3886-196">This service creates a PPP instance for the specified NetX IP instance.</span></span> <span data-ttu-id="f3886-197">Эта функция должна вызываться до создания экземпляра IP-адреса для NetX.</span><span class="sxs-lookup"><span data-stu-id="f3886-197">This function must be called prior to creating the NetX IP instance.</span></span>

>[!NOTE]
> <span data-ttu-id="f3886-198">Обычно считается, что IP-поток NetX следует создавать с более высоким приоритетом, чем у потока PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-198">It is generally a good idea to create the NetX IP thread at a higher priority than the PPP thread priority.</span></span> <span data-ttu-id="f3886-199">Дополнительные сведения об указании приоритета для IP-потока см. в описании службы *nx_ip_create*.</span><span class="sxs-lookup"><span data-stu-id="f3886-199">Please refer to the *nx_ip_create* service for more information on specifying the IP thread priority.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f3886-200">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="f3886-200">Input Parameters</span></span>

- <span data-ttu-id="f3886-201">**ppp_ptr**: указатель на блок управления PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-201">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="f3886-202">**name**: имя экземпляра PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-202">**name**: Name of this PPP instance.</span></span>
- <span data-ttu-id="f3886-203">**ip_ptr**: указатель на блок управления для еще не созданного экземпляра IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="f3886-203">**ip_ptr**: Pointer to control block for not-yet-created IP instance.</span></span>
- <span data-ttu-id="f3886-204">**stack_memory_ptr**: указатель на начало зоны стека для потока PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-204">**stack_memory_ptr**: Pointer to start of PPP thread’s stack area.</span></span>
- <span data-ttu-id="f3886-205">**stack_size**: размер в байтах в стеке потока.</span><span class="sxs-lookup"><span data-stu-id="f3886-205">**stack_size**: Size in bytes in the thread’s stack.</span></span>
- <span data-ttu-id="f3886-206">**pool_ptr**: указатель на пул пакетов по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f3886-206">**pool_ptr**: Pointer to default packet pool.</span></span>
- <span data-ttu-id="f3886-207">**thread_priority**: приоритет внешних потоков PPP (1–31).</span><span class="sxs-lookup"><span data-stu-id="f3886-207">**thread_priority**: Priority of internal PPP threads (1-31).</span></span>
- <span data-ttu-id="f3886-208">**ppp_invalid_packet_handler**: указатель функции на обработчик приложения, который обрабатывает все пакеты, отличные от PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-208">**ppp_invalid_packet_handler**: Function pointer to application’s handler for all non-PPP packets.</span></span> <span data-ttu-id="f3886-209">Обычно PPP для NetX вызывает эту подпрограмму во время инициализации.</span><span class="sxs-lookup"><span data-stu-id="f3886-209">The NetX PPP typically calls this routine during initialization.</span></span> <span data-ttu-id="f3886-210">Именно в ней приложение может реагировать на команды модема, а в среде Windows XP приложение PPP для NetX может запустить канал PPP, вернув ответ CLIENT SERVER на запрос CLIENT от ОС Windows XP.</span><span class="sxs-lookup"><span data-stu-id="f3886-210">This is where the application can respond to modem commands or in the case of Windows XP, the NetX PPP application can initiate PPP by responding with“ CLIENT SERVER” to the initial “CLIENT” sent by Windows XP.</span></span>
- <span data-ttu-id="f3886-211">**ppp_byte_send**: указатель функции на подпрограмму приложения, которая обрабатывает последовательный байтовый вывод.</span><span class="sxs-lookup"><span data-stu-id="f3886-211">**ppp_byte_send**: Function pointer to application’s serial byte output routine.</span></span>


### <a name="return-values"></a><span data-ttu-id="f3886-212">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="f3886-212">Return Values</span></span>

- <span data-ttu-id="f3886-213">**NX_SUCCESS** (0x00): экземпляр PPP успешно создан.</span><span class="sxs-lookup"><span data-stu-id="f3886-213">**NX_SUCCESS**: (0x00) Successful PPP create.</span></span>
- <span data-ttu-id="f3886-214">NX_PTR_ERROR: (0x07) недопустимый указатель функции на PPP, IP или байтовый вывод.</span><span class="sxs-lookup"><span data-stu-id="f3886-214">NX_PTR_ERROR: (0x07) Invalid PPP, IP, or byte output function pointer.</span></span>
- <span data-ttu-id="f3886-215">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="f3886-215">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f3886-216">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="f3886-216">Allowed From</span></span>

<span data-ttu-id="f3886-217">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="f3886-217">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="f3886-218">Например, .</span><span class="sxs-lookup"><span data-stu-id="f3886-218">Example</span></span>

```c
/* Create “my_ppp” for IP instance “my_ip”. */
status =  nx_ppp_create(&my_ppp, “my PPP”, &my_ip, stack_start, 1024, 2, 
                        &my_pool, my_invalid_packet_handler, my_out_byte);

/* If status is NX_SUCCESS the PPP instance was successfully
   created. */
```

## <a name="nx_ppp_delete"></a><span data-ttu-id="f3886-219">nx_ppp_delete</span><span class="sxs-lookup"><span data-stu-id="f3886-219">nx_ppp_delete</span></span>

<span data-ttu-id="f3886-220">Удаление экземпляра PPP</span><span class="sxs-lookup"><span data-stu-id="f3886-220">Delete a PPP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="f3886-221">Прототип</span><span class="sxs-lookup"><span data-stu-id="f3886-221">Prototype</span></span>

```c
UINT nx_ppp_delete(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="f3886-222">Описание</span><span class="sxs-lookup"><span data-stu-id="f3886-222">Description</span></span>

<span data-ttu-id="f3886-223">Эта служба удаляет созданный ранее экземпляр PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-223">This service deletes the previously created PPP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f3886-224">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="f3886-224">Input Parameters</span></span>

- <span data-ttu-id="f3886-225">**ppp_ptr**: указатель на блок управления PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-225">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="f3886-226">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="f3886-226">Return Values</span></span>

- <span data-ttu-id="f3886-227">**NX_SUCCESS** (0x00): экземпляр PPP успешно удален.</span><span class="sxs-lookup"><span data-stu-id="f3886-227">**NX_SUCCESS**: (0x00) Successful PPP deletion.</span></span>
- <span data-ttu-id="f3886-228">NX_PTR_ERROR (0x07): недопустимый указатель PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-228">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="f3886-229">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="f3886-229">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f3886-230">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="f3886-230">Allowed From</span></span>

<span data-ttu-id="f3886-231">Потоки</span><span class="sxs-lookup"><span data-stu-id="f3886-231">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f3886-232">Например, .</span><span class="sxs-lookup"><span data-stu-id="f3886-232">Example</span></span>

```c
/* Delete PPP instance “my_ppp”. */
status =  nx_ppp_delete(&my_ppp);

/* If status is NX_SUCCESS the “my_ppp” was successfully deleted. */
```

## <a name="nx_ppp_dns_address_get"></a><span data-ttu-id="f3886-233">nx_ppp_dns_address_get</span><span class="sxs-lookup"><span data-stu-id="f3886-233">nx_ppp_dns_address_get</span></span>

<span data-ttu-id="f3886-234">Получение IP-адреса DNS-сервера</span><span class="sxs-lookup"><span data-stu-id="f3886-234">Get DNS Server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="f3886-235">Прототип</span><span class="sxs-lookup"><span data-stu-id="f3886-235">Prototype</span></span>

```c
UINT nx_ppp_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a><span data-ttu-id="f3886-236">Описание</span><span class="sxs-lookup"><span data-stu-id="f3886-236">Description</span></span>

<span data-ttu-id="f3886-237">Эта служба возвращает IP-адрес DNS-сервера, предоставленный одноранговым узлом в подтверждении IPCP.</span><span class="sxs-lookup"><span data-stu-id="f3886-237">This service retrieves the DNS IP address supplied by the peer in the IPCP handshake.</span></span> <span data-ttu-id="f3886-238">Если одноранговый узел не предоставил IP-адрес, возвращается значение 0.</span><span class="sxs-lookup"><span data-stu-id="f3886-238">If no IP address was supplied by the peer, an IP address of 0 is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f3886-239">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="f3886-239">Input Parameters</span></span>

- <span data-ttu-id="f3886-240">**ppp_ptr**: указатель на блок управления PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-240">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="f3886-241">**dns_address_ptr**: назначение для адреса DNS-сервера.</span><span class="sxs-lookup"><span data-stu-id="f3886-241">**dns_address_ptr**: Destination for DNS server address</span></span>

### <a name="return-values"></a><span data-ttu-id="f3886-242">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="f3886-242">Return Values</span></span>

- <span data-ttu-id="f3886-243">**NX_SUCCESS** (0x00): успешное получение адреса DNS.</span><span class="sxs-lookup"><span data-stu-id="f3886-243">**NX_SUCCESS**: (0x00) Successful DNS address get.</span></span>
- <span data-ttu-id="f3886-244">**NX_PPP_NOT_ESTABLISHED** (0xB5): не завершено согласование PPP с одноранговым узлом.</span><span class="sxs-lookup"><span data-stu-id="f3886-244">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="f3886-245">NX_PTR_ERROR (0x07): недопустимый указатель PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-245">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f3886-246">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="f3886-246">Allowed From</span></span>

<span data-ttu-id="f3886-247">Инициализация, потоки, таймеры, подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="f3886-247">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="f3886-248">Например, .</span><span class="sxs-lookup"><span data-stu-id="f3886-248">Example</span></span>

```c

ULONG  my_dns_address;

/* Get DNS Server address supplied by peer. */
status =  nx_ppp_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the DNS IP address – 
   if the peer supplied one. */
```

## <a name="nx_ppp_secondary_dns_address_get"></a><span data-ttu-id="f3886-249">nx_ppp_secondary_dns_address_get</span><span class="sxs-lookup"><span data-stu-id="f3886-249">nx_ppp_secondary_dns_address_get</span></span>

<span data-ttu-id="f3886-250">Получение IP-адреса дополнительного DNS-сервера</span><span class="sxs-lookup"><span data-stu-id="f3886-250">Get Secondary DNS Server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="f3886-251">Прототип</span><span class="sxs-lookup"><span data-stu-id="f3886-251">Prototype</span></span>

```c
UINT nx_ppp_secondary_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a><span data-ttu-id="f3886-252">Описание</span><span class="sxs-lookup"><span data-stu-id="f3886-252">Description</span></span>

<span data-ttu-id="f3886-253">Эта служба возвращает IP-адрес дополнительного DNS-сервера, предоставленный одноранговым узлом в подтверждении IPCP.</span><span class="sxs-lookup"><span data-stu-id="f3886-253">This service retrieves the secondary DNS IP address supplied by the peer in the IPCP handshake.</span></span> <span data-ttu-id="f3886-254">Если одноранговый узел не предоставил IP-адрес, возвращается значение 0.</span><span class="sxs-lookup"><span data-stu-id="f3886-254">If no IP address was supplied by the peer, an IP address of 0 is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f3886-255">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="f3886-255">Input Parameters</span></span>

- <span data-ttu-id="f3886-256">**ppp_ptr**: указатель на блок управления PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-256">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="f3886-257">**dns_address_ptr**: назначение для адреса дополнительного DNS-сервера.</span><span class="sxs-lookup"><span data-stu-id="f3886-257">**dns_address_ptr**: Destination for Secondary DNS server address</span></span>

### <a name="return-values"></a><span data-ttu-id="f3886-258">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="f3886-258">Return Values</span></span>

- <span data-ttu-id="f3886-259">**NX_SUCCESS** (0x00): успешное получение адреса DNS.</span><span class="sxs-lookup"><span data-stu-id="f3886-259">**NX_SUCCESS**: (0x00) Successful DNS address get.</span></span>
- <span data-ttu-id="f3886-260">**NX_PPP_NOT_ESTABLISHED** (0xB5): не завершено согласование PPP с одноранговым узлом.</span><span class="sxs-lookup"><span data-stu-id="f3886-260">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="f3886-261">NX_PTR_ERROR (0x07): недопустимый указатель PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-261">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f3886-262">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="f3886-262">Allowed From</span></span>

<span data-ttu-id="f3886-263">Инициализация, потоки, таймеры, подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="f3886-263">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="f3886-264">Например, .</span><span class="sxs-lookup"><span data-stu-id="f3886-264">Example</span></span>

```c
ULONG  my_dns_address;

/* Get secondary DNS Server address supplied by peer. */
status =  nx_ppp_secondary_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the secondary DNS Server address – if the peer supplied one. */
```

## <a name="nx_ppp_dns_address_set"></a><span data-ttu-id="f3886-265">nx_ppp_dns_address_set</span><span class="sxs-lookup"><span data-stu-id="f3886-265">nx_ppp_dns_address_set</span></span>

<span data-ttu-id="f3886-266">Настройка IP-адреса основного DNS-сервера</span><span class="sxs-lookup"><span data-stu-id="f3886-266">Set primary DNS Server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="f3886-267">Прототип</span><span class="sxs-lookup"><span data-stu-id="f3886-267">Prototype</span></span>

```c
UINT nx_ppp_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a><span data-ttu-id="f3886-268">Описание</span><span class="sxs-lookup"><span data-stu-id="f3886-268">Description</span></span>

<span data-ttu-id="f3886-269">Эта служба задает IP-адрес DNS-сервера.</span><span class="sxs-lookup"><span data-stu-id="f3886-269">This service sets the DNS Server IP address.</span></span> <span data-ttu-id="f3886-270">Если одноранговый узел отправляет в состоянии IPCP запрос параметра DNS-сервера, локальный узел предоставит эти сведения.</span><span class="sxs-lookup"><span data-stu-id="f3886-270">If the peer sends a DNS Server option request in the IPCP state, this host will provide the information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f3886-271">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="f3886-271">Input Parameters</span></span>

- <span data-ttu-id="f3886-272">**ppp_ptr**: указатель на блок управления PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-272">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="f3886-273">**dns_address**: адрес DNS-сервера.</span><span class="sxs-lookup"><span data-stu-id="f3886-273">**dns_address**: DNS server address</span></span>

### <a name="return-values"></a><span data-ttu-id="f3886-274">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="f3886-274">Return Values</span></span>

- <span data-ttu-id="f3886-275">**NX_SUCCESS** (0x00): успешное сохранение адреса DNS.</span><span class="sxs-lookup"><span data-stu-id="f3886-275">**NX_SUCCESS**: (0x00) Successful DNS address set.</span></span>
- <span data-ttu-id="f3886-276">**NX_PPP_NOT_ESTABLISHED** (0xB5): не завершено согласование PPP с одноранговым узлом.</span><span class="sxs-lookup"><span data-stu-id="f3886-276">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="f3886-277">NX_PTR_ERROR (0x07): недопустимый указатель PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-277">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f3886-278">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="f3886-278">Allowed From</span></span>

<span data-ttu-id="f3886-279">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="f3886-279">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="f3886-280">Например, .</span><span class="sxs-lookup"><span data-stu-id="f3886-280">Example</span></span>

```c

ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the DNS Server address provided if the peer requests one. */

```

## <a name="nx_ppp_secondary_dns_address_set"></a><span data-ttu-id="f3886-281">nx_ppp_secondary_dns_address_set</span><span class="sxs-lookup"><span data-stu-id="f3886-281">nx_ppp_secondary_dns_address_set</span></span>

<span data-ttu-id="f3886-282">Настройка IP-адреса дополнительного DNS-сервера</span><span class="sxs-lookup"><span data-stu-id="f3886-282">Set secondary DNS Server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="f3886-283">Прототип</span><span class="sxs-lookup"><span data-stu-id="f3886-283">Prototype</span></span>

```c
UINT nx_ppp_secondary_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a><span data-ttu-id="f3886-284">Описание</span><span class="sxs-lookup"><span data-stu-id="f3886-284">Description</span></span>

<span data-ttu-id="f3886-285">Эта служба задает IP-адрес дополнительного DNS-сервера.</span><span class="sxs-lookup"><span data-stu-id="f3886-285">This service sets the secondary DNS Server IP address.</span></span> <span data-ttu-id="f3886-286">Если одноранговый узел отправляет в состоянии IPCP запрос параметра дополнительного DNS-сервера, локальный узел предоставит эти сведения.</span><span class="sxs-lookup"><span data-stu-id="f3886-286">If the peer sends a secondary DNS Server option request in the IPCP state, this host will provide the information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f3886-287">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="f3886-287">Input Parameters</span></span>

- <span data-ttu-id="f3886-288">**ppp_ptr**: указатель на блок управления PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-288">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="f3886-289">**dns_address**: адрес дополнительного DNS-сервера.</span><span class="sxs-lookup"><span data-stu-id="f3886-289">**dns_address**: Secondary DNS server address</span></span>

### <a name="return-values"></a><span data-ttu-id="f3886-290">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="f3886-290">Return Values</span></span>

- <span data-ttu-id="f3886-291">**NX_SUCCESS** (0x00): успешное сохранение адреса DNS.</span><span class="sxs-lookup"><span data-stu-id="f3886-291">**NX_SUCCESS**: (0x00) Successful DNS address set.</span></span> 
- <span data-ttu-id="f3886-292">**NX_PPP_NOT_ESTABLISHED** (0xB5): не завершено согласование PPP с одноранговым узлом.</span><span class="sxs-lookup"><span data-stu-id="f3886-292">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="f3886-293">NX_PTR_ERROR (0x07): недопустимый указатель PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-293">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f3886-294">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="f3886-294">Allowed From</span></span>

<span data-ttu-id="f3886-295">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="f3886-295">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="f3886-296">Например, .</span><span class="sxs-lookup"><span data-stu-id="f3886-296">Example</span></span>

```c
ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_secondary_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the secondary DNS Server address provided if the peer requests one. */

```
## <a name="nx_ppp_interface_index_get"></a><span data-ttu-id="f3886-297">nx_ppp_interface_index_get</span><span class="sxs-lookup"><span data-stu-id="f3886-297">nx_ppp_interface_index_get</span></span>

<span data-ttu-id="f3886-298">Получение индекса IP-интерфейса</span><span class="sxs-lookup"><span data-stu-id="f3886-298">Get IP interface index</span></span>

### <a name="prototype"></a><span data-ttu-id="f3886-299">Прототип</span><span class="sxs-lookup"><span data-stu-id="f3886-299">Prototype</span></span>

```c
UINT nx_ppp_interface_index_get(NX_PPP *ppp_ptr, UINT *index_ptr);
```

### <a name="description"></a><span data-ttu-id="f3886-300">Описание</span><span class="sxs-lookup"><span data-stu-id="f3886-300">Description</span></span>

<span data-ttu-id="f3886-301">Эта служба получает индекс IP-интерфейса, сопоставленного с этим экземпляром PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-301">This service retrieves the IP interface index associated with this PPP instance.</span></span> <span data-ttu-id="f3886-302">Это полезно только в том случае, если экземпляр PPP не является основным интерфейсом для экземпляра IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="f3886-302">This is only useful when the PPP instance is not the primary interface of an IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f3886-303">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="f3886-303">Input Parameters</span></span>

- <span data-ttu-id="f3886-304">**ppp_ptr**: указатель на блок управления PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-304">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="f3886-305">**index_ptr**: назначение для индекса интерфейса.</span><span class="sxs-lookup"><span data-stu-id="f3886-305">**index_ptr**: Destination for interface index</span></span>

### <a name="return-values"></a><span data-ttu-id="f3886-306">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="f3886-306">Return Values</span></span>

- <span data-ttu-id="f3886-307">**NX_SUCCESS** (0x00): индекс PPP успешно получен.</span><span class="sxs-lookup"><span data-stu-id="f3886-307">**NX_SUCCESS**: (0x00) Successful PPP index get.</span></span>
- <span data-ttu-id="f3886-308">**NX_IN_PROGRESS** (0x37): не завершена инициализация PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-308">**NX_IN_PROGRESS**: (0x37) PPP has not completed initialization.</span></span>
- <span data-ttu-id="f3886-309">NX_PTR_ERROR (0x07): недопустимый указатель PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-309">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f3886-310">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="f3886-310">Allowed From</span></span>

<span data-ttu-id="f3886-311">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="f3886-311">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="f3886-312">Например, .</span><span class="sxs-lookup"><span data-stu-id="f3886-312">Example</span></span>

```c
ULONG  my_index;

/* Get the interface index for this PPP instance. */
status =  nx_ppp_interface_index_get(&my_ppp, &my_index);

/* If status is NX_SUCCESS the “my_index” contains the IP interface index for
   this PPP instance. */

```
## <a name="nx_ppp_ip_address_assign"></a><span data-ttu-id="f3886-313">nx_ppp_ip_address_assign</span><span class="sxs-lookup"><span data-stu-id="f3886-313">nx_ppp_ip_address_assign</span></span>

<span data-ttu-id="f3886-314">Назначение IP-адресов для IPCP</span><span class="sxs-lookup"><span data-stu-id="f3886-314">Assign IP addresses for IPCP</span></span>

### <a name="prototype"></a><span data-ttu-id="f3886-315">Прототип</span><span class="sxs-lookup"><span data-stu-id="f3886-315">Prototype</span></span>

```c
UINT nx_ppp_ip_address_assign(NX_PPP *ppp_ptr, ULONG local_ip_address, 
            ULONG peer_ip_address);
```

### <a name="description"></a><span data-ttu-id="f3886-316">Описание</span><span class="sxs-lookup"><span data-stu-id="f3886-316">Description</span></span>

<span data-ttu-id="f3886-317">Эта служба настраивает IP-адреса локального и однорангового узлов для использования в протоколе IPCP (протокол управления протоколом IP).</span><span class="sxs-lookup"><span data-stu-id="f3886-317">This service sets up the local and peer IP addresses for use in the Internet Protocol Control Protocol (IPCP.</span></span> <span data-ttu-id="f3886-318">Ее нужно вызывать для того экземпляра PPP, у которого есть допустимые IP-адреса для себя и другого однорангового узла.</span><span class="sxs-lookup"><span data-stu-id="f3886-318">It should be called for the PPP instance that has valid IP addresses for itself and the other peer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f3886-319">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="f3886-319">Input Parameters</span></span>

- <span data-ttu-id="f3886-320">**ppp_ptr**: указатель на блок управления PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-320">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="f3886-321">**local_ip_address**: локальный IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="f3886-321">**local_ip_address**: Local IP address.</span></span>
- <span data-ttu-id="f3886-322">**peer_ip_address**: IP-адрес однорангового узла.</span><span class="sxs-lookup"><span data-stu-id="f3886-322">**peer_ip_address**: Peer’s IP address.</span></span>

### <a name="return-values"></a><span data-ttu-id="f3886-323">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="f3886-323">Return Values</span></span>

- <span data-ttu-id="f3886-324">**NX_SUCCESS** (0x00): адрес PPP успешно назначен.</span><span class="sxs-lookup"><span data-stu-id="f3886-324">**NX_SUCCESS**: (0x00) Successful PPP address assignment.</span></span>
- <span data-ttu-id="f3886-325">NX_PTR_ERROR (0x07): недопустимый указатель PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-325">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="f3886-326">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="f3886-326">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f3886-327">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="f3886-327">Allowed From</span></span>

<span data-ttu-id="f3886-328">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="f3886-328">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="f3886-329">Например, .</span><span class="sxs-lookup"><span data-stu-id="f3886-329">Example</span></span>

```c
/* Set IP addresses for “my_ppp”. */
status =  nx_ppp_ip_address_assign(&my_ppp, IP_ADDRESS(256,2,2,187), 
IP_ADDRESS(256,2,2,188));


/* If status is NX_SUCCESS the “my_ppp” has the IP addresses. */
```

## <a name="nx_ppp_link_down_notify"></a><span data-ttu-id="f3886-330">nx_ppp_link_down_notify</span><span class="sxs-lookup"><span data-stu-id="f3886-330">nx_ppp_link_down_notify</span></span>

<span data-ttu-id="f3886-331">Уведомление приложения об отключении канала</span><span class="sxs-lookup"><span data-stu-id="f3886-331">Notify application on link down</span></span>

### <a name="prototype"></a><span data-ttu-id="f3886-332">Прототип</span><span class="sxs-lookup"><span data-stu-id="f3886-332">Prototype</span></span>

```c
UINT nx_ppp_link_down_notify(NX_PPP *ppp_ptr, 
                             VOID (*link_down_callback)(NX_PPP *ppp_ptr));
```

### <a name="description"></a><span data-ttu-id="f3886-333">Описание</span><span class="sxs-lookup"><span data-stu-id="f3886-333">Description</span></span>

<span data-ttu-id="f3886-334">Эта служба регистрирует обратный вызов для информирования приложения об отключении канала для указанного экземпляра PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-334">This service registers the application’s link down notification callback with the specified PPP instance.</span></span> <span data-ttu-id="f3886-335">Если значение отлично от NULL, указанная функция обратного вызова будет вызываться каждый раз при отключении этого канала.</span><span class="sxs-lookup"><span data-stu-id="f3886-335">If non-NULL, the application’s link down callback function is called whenever the link goes down.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f3886-336">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="f3886-336">Input Parameters</span></span>

- <span data-ttu-id="f3886-337">**ppp_ptr**: указатель на блок управления PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-337">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="f3886-338">**link_down_callback**: указатель на функцию обратного вызова для уведомления приложения об отключении канала.</span><span class="sxs-lookup"><span data-stu-id="f3886-338">**link_down_callback**: Application’s link down notification function pointer.</span></span> <span data-ttu-id="f3886-339">Если значение равно NULL, уведомление об отключении канала не используется.</span><span class="sxs-lookup"><span data-stu-id="f3886-339">If NULL, link down notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="f3886-340">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="f3886-340">Return Values</span></span>

- <span data-ttu-id="f3886-341">**NX_SUCCESS** (0x00): обратный вызов для уведомления об отключении канала успешно зарегистрирован.</span><span class="sxs-lookup"><span data-stu-id="f3886-341">**NX_SUCCESS**: (0x00) Successful link down notification callback registration.</span></span>
- <span data-ttu-id="f3886-342">NX_PTR_ERROR (0x07): недопустимый указатель PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-342">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f3886-343">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="f3886-343">Allowed From</span></span>

<span data-ttu-id="f3886-344">Инициализация, потоки, таймеры, подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="f3886-344">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="f3886-345">Например, .</span><span class="sxs-lookup"><span data-stu-id="f3886-345">Example</span></span>

```c
/* Register “my_link_down_callback” to be called whenever the PPP
   link goes down. */
status =  nx_ppp_link_down_notify(&my_ppp, my_link_down_callback);


/* If status is NX_SUCCESS the function “my_link_down_callback” has been
   registered with this PPP instance. */

VOID my_link_down_callback(NX_PPP *ppp_ptr)
{

/* On link down, simply restart PPP.  */
    nx_ppp_restart(ppp_ptr);
} 
```
## <a name="nx_ppp_link_up_notify"></a><span data-ttu-id="f3886-346">nx_ppp_link_up_notify</span><span class="sxs-lookup"><span data-stu-id="f3886-346">nx_ppp_link_up_notify</span></span>

<span data-ttu-id="f3886-347">Уведомление приложения о включении канала</span><span class="sxs-lookup"><span data-stu-id="f3886-347">Notify application on link up</span></span>

### <a name="prototype"></a><span data-ttu-id="f3886-348">Прототип</span><span class="sxs-lookup"><span data-stu-id="f3886-348">Prototype</span></span>

```c
UINT nx_ppp_link_up_notify(NX_PPP *ppp_ptr, 
                           VOID (*link_up_callback)(NX_PPP *ppp_ptr));
```
### <a name="description"></a><span data-ttu-id="f3886-349">Описание</span><span class="sxs-lookup"><span data-stu-id="f3886-349">Description</span></span>

<span data-ttu-id="f3886-350">Эта служба регистрирует обратный вызов для информирования приложения о включении канала для указанного экземпляра PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-350">This service registers the application’s link up notification callback with the specified PPP instance.</span></span> <span data-ttu-id="f3886-351">Если значение отлично от NULL, указанная функция обратного вызова будет вызываться каждый раз при включении этого канала.</span><span class="sxs-lookup"><span data-stu-id="f3886-351">If non-NULL, the application’s link up callback function is called whenever the link comes up.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f3886-352">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="f3886-352">Input Parameters</span></span>

- <span data-ttu-id="f3886-353">**ppp_ptr**: указатель на блок управления PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-353">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="f3886-354">**link_up_callback**: указатель на функцию обратного вызова для уведомления приложения о включении канала.</span><span class="sxs-lookup"><span data-stu-id="f3886-354">**link_up_callback**: Application’s link up notification function pointer.</span></span> <span data-ttu-id="f3886-355">Если значение равно NULL, уведомление о включении канала не используется.\*\*</span><span class="sxs-lookup"><span data-stu-id="f3886-355">If NULL, link up notification is disabled.\*\*</span></span>

### <a name="return-values"></a><span data-ttu-id="f3886-356">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="f3886-356">Return Values</span></span>

- <span data-ttu-id="f3886-357">**NX_SUCCESS** (0x00): обратный вызов для уведомления о включении канала успешно зарегистрирован.</span><span class="sxs-lookup"><span data-stu-id="f3886-357">**NX_SUCCESS**: (0x00) Successful link up notification callback registration.</span></span>
- <span data-ttu-id="f3886-358">NX_PTR_ERROR (0x07): недопустимый указатель PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-358">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f3886-359">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="f3886-359">Allowed From</span></span>

<span data-ttu-id="f3886-360">Инициализация, потоки, таймеры, подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="f3886-360">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="f3886-361">Например, .</span><span class="sxs-lookup"><span data-stu-id="f3886-361">Example</span></span>

```c
/* Register “my_link_up_callback” to be called whenever the PPP
   link comes up. */
status =  nx_ppp_link_up_notify(&my_ppp, my_link_up_callback);


/* If status is NX_SUCCESS the function “my_link_up_callback” has been
   registered with this PPP instance. */

VOID my_link_up_callback(NX_PPP *ppp_ptr)
{
    /* On link up, the application my want to start sending/receiving
       UPD/TCP data.  */
}
```

## <a name="nx_ppp_nak_authentication_notify"></a><span data-ttu-id="f3886-362">nx_ppp_nak_authentication_notify</span><span class="sxs-lookup"><span data-stu-id="f3886-362">nx_ppp_nak_authentication_notify</span></span>

<span data-ttu-id="f3886-363">Уведомление приложения о получении пакета NAK при проверке подлинности</span><span class="sxs-lookup"><span data-stu-id="f3886-363">Notify application if authentication NAK received</span></span>

### <a name="prototype"></a><span data-ttu-id="f3886-364">Прототип</span><span class="sxs-lookup"><span data-stu-id="f3886-364">Prototype</span></span>

```c
UINT    nx_ppp_nak_authentication_notify(NX_PPP *ppp_ptr, 
                                         void (*nak_authentication_notify)(void));
```

### <a name="description"></a><span data-ttu-id="f3886-365">Описание</span><span class="sxs-lookup"><span data-stu-id="f3886-365">Description</span></span>

<span data-ttu-id="f3886-366">Эта служба регистрирует обратный вызов для информирования приложения о получении пакета NAK при проверке подлинности для указанного экземпляра PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-366">This service registers the application’s authentication nak notification callback with the specified PPP instance.</span></span> <span data-ttu-id="f3886-367">Если значение не равно NULL, эта функция обратного вызова вызывается каждый раз, когда экземпляр PPP получает пакет NAK во время проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="f3886-367">If non-NULL, this callback function is called whenever the PPP instance receives a NAK during authentiaction.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f3886-368">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="f3886-368">Input Parameters</span></span>

- <span data-ttu-id="f3886-369">**ppp_ptr**: указатель на блок управления PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-369">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="f3886-370">**nak_authentication_notify**: указатель на функцию, которая вызывается при получении экземпляром PPP пакета NAK при проверке подлинности.</span><span class="sxs-lookup"><span data-stu-id="f3886-370">**nak_authentication_notify**: Pointer to function called when the PPP instance receives an authentication NAK.</span></span> <span data-ttu-id="f3886-371">Если значение равно NULL, это уведомление не используется.</span><span class="sxs-lookup"><span data-stu-id="f3886-371">If NULL, the notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="f3886-372">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="f3886-372">Return Values</span></span>

- <span data-ttu-id="f3886-373">**NX_SUCCESS** (0x00): обратный вызов для уведомления успешно зарегистрирован.</span><span class="sxs-lookup"><span data-stu-id="f3886-373">**NX_SUCCESS**: (0x00) Successful notification callback registration.</span></span>
- <span data-ttu-id="f3886-374">NX_PTR_ERROR (0x07): недопустимый указатель PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-374">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f3886-375">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="f3886-375">Allowed From</span></span>

<span data-ttu-id="f3886-376">Инициализация, потоки, таймеры, подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="f3886-376">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="f3886-377">Например, .</span><span class="sxs-lookup"><span data-stu-id="f3886-377">Example</span></span>

```c
/* Register “my_nak_auth_callback” to be called whenever the PPP
   receives a NAK during authentication. */
status =  nx_ppp_nak_authentication_notify(&my_ppp, my_nak_auth_callback);

/* If status is NX_SUCCESS the function “my_nak_auth_callback” has been
   registered with this PPP instance. */

VOID my_nak_auth_callback(NX_PPP *ppp_ptr)
{
   /* Handle the situation of receiving an authentication NAK */
}

```

## <a name="nx_ppp_pap_enable"></a><span data-ttu-id="f3886-378">nx_ppp_pap_enable</span><span class="sxs-lookup"><span data-stu-id="f3886-378">nx_ppp_pap_enable</span></span>

<span data-ttu-id="f3886-379">Включение проверки подлинности PAP</span><span class="sxs-lookup"><span data-stu-id="f3886-379">Enable PAP Authentication</span></span>

### <a name="prototype"></a><span data-ttu-id="f3886-380">Прототип</span><span class="sxs-lookup"><span data-stu-id="f3886-380">Prototype</span></span>

```c

UINT  nx_ppp_pap_enable(NX_PPP *ppp_ptr, 
                        UINT (*generate_login)(CHAR *name, CHAR *password),
                        UINT (*verify_login)(CHAR *name, CHAR *password));
```

### <a name="description"></a><span data-ttu-id="f3886-381">Описание</span><span class="sxs-lookup"><span data-stu-id="f3886-381">Description</span></span>

<span data-ttu-id="f3886-382">Эта служба включает протокол PAP (протокол проверки пароля) для указанного экземпляра PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-382">This service enables the Password Authentication Protocol (PAP) for the specified PPP instance.</span></span> <span data-ttu-id="f3886-383">Если указана функция ***verify_login***, использование PAP считается обязательным для этого экземпляра PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-383">If the “***verify_login***” function pointer is specified, PAP is required by this PPP instance.</span></span> <span data-ttu-id="f3886-384">В противном случае PAP включается только по требованию однорангового узла, полученному при согласовании LCP.</span><span class="sxs-lookup"><span data-stu-id="f3886-384">Otherwise, PAP only responds to the peer’s PAP requirements as specified during LCP negotiation.</span></span>

<span data-ttu-id="f3886-385">Ниже упоминаются несколько элементов данных, которые используются в обязательных функциях обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="f3886-385">There are several data items referenced below in the required callback functions.</span></span> <span data-ttu-id="f3886-386">Элемент данных *name* должен иметь формат строки, оканчивающейся символом NULL, и размер, не превышающий значение NX_PPP_NAME_SIZE-1.</span><span class="sxs-lookup"><span data-stu-id="f3886-386">The data item *name* is expected to be NULL-terminated string with a maximum size of NX_PPP_NAME_SIZE-1.</span></span> <span data-ttu-id="f3886-387">Элемент данных *password* должен также иметь формат строки, оканчивающейся символом NULL, и размер, не превышающий значение NX_PPP_PASSWORD_SIZE-1.</span><span class="sxs-lookup"><span data-stu-id="f3886-387">The data item *password* is also expected to be a NULL-terminated string with a maximum size of NX_PPP_PASSWORD_SIZE-1.</span></span>

>[!NOTE]
> <span data-ttu-id="f3886-388">Эта функция должна вызываться после *nx_ppp_create*, но раньше *nx_ip_create* или *nx_ip_interface_attach*.</span><span class="sxs-lookup"><span data-stu-id="f3886-388">This function must be called after *nx_ppp_create* but before *nx_ip_create* or *nx_ip_interface_attach*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f3886-389">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="f3886-389">Input Parameters</span></span>

- <span data-ttu-id="f3886-390">**ppp_ptr**: указатель на блок управления PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-390">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="f3886-391">**generate_login**: указатель на функцию приложения, которая предоставляет одноранговому узлу параметры *name* и *password* для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="f3886-391">**generate_login**: Pointer to application function that produces a *name* and *password* for authentication by the peer.</span></span> <span data-ttu-id="f3886-392">Обратите внимание, что значения *name* и *password* должны быть скопированы в указанные места назначения.</span><span class="sxs-lookup"><span data-stu-id="f3886-392">Note that the *name* and *password* values must be copied into the supplied destinations.</span></span>
- <span data-ttu-id="f3886-393">**verify_login**: указатель на функцию приложения, которая проверяет параметры *name* и *password*, предоставленные одноранговым узлом.</span><span class="sxs-lookup"><span data-stu-id="f3886-393">**verify_login**: Pointer to application function that verifies the *name* and *password* supplied by the peer.</span></span> <span data-ttu-id="f3886-394">Эта подпрограмма должна сравнивать предоставленные значения *name* и *password*.</span><span class="sxs-lookup"><span data-stu-id="f3886-394">This routine must compare the supplied *name* and *password*.</span></span> <span data-ttu-id="f3886-395">Если она возвращает NX_SUCCESS, значит имя и пароль верны, и PPP может перейти к следующему шагу.</span><span class="sxs-lookup"><span data-stu-id="f3886-395">If this routine returns NX_SUCCESS, the name and password are correct and PPP can proceed to the next step.</span></span> <span data-ttu-id="f3886-396">В противном случае подпрограмма возвращает NX_PPP_ERROR, и тогда PPP ожидает новые значения имени и пароля.</span><span class="sxs-lookup"><span data-stu-id="f3886-396">Otherwise, this routine returns NX_PPP_ERROR and PPP simply waits for another name and password.</span></span>

### <a name="return-values"></a><span data-ttu-id="f3886-397">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="f3886-397">Return Values</span></span>

- <span data-ttu-id="f3886-398">**NX_SUCCESS** (0x00): PPP PAP успешно включено.</span><span class="sxs-lookup"><span data-stu-id="f3886-398">**NX_SUCCESS**: (0x00) Successful PPP PAP enable.</span></span>
- <span data-ttu-id="f3886-399">**NX_NOT_IMPLEMENTED** (0x80): логика PAP была отключена с помощью параметра NX_PPP_DISABLE_PAP.</span><span class="sxs-lookup"><span data-stu-id="f3886-399">**NX_NOT_IMPLEMENTED**: (0x80) PAP logic was disabled via NX_PPP_DISABLE_PAP.</span></span>
- <span data-ttu-id="f3886-400">NX_PTR_ERROR (0x07): недопустимый указатель PPP или указатель на функцию приложения.</span><span class="sxs-lookup"><span data-stu-id="f3886-400">NX_PTR_ERROR: (0x07) Invalid PPP pointer or application function pointer.</span></span>
- <span data-ttu-id="f3886-401">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="f3886-401">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f3886-402">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="f3886-402">Allowed From</span></span>

<span data-ttu-id="f3886-403">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="f3886-403">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="f3886-404">Например, .</span><span class="sxs-lookup"><span data-stu-id="f3886-404">Example</span></span>

```c
CHAR    name_string[] = "username";
CHAR    password_string[] =  "password";

/* Enable PAP for PPP instance “my_ppp”. */
status =  nx_ppp_pap_enable(&my_ppp, my_generate_login, my_verify_login);

/* If status is NX_SUCCESS the “my_ppp” now has PAP enabled. */

/* Define callback routines for PAP enable.  */

UINT  generate_login(CHAR *name, CHAR *password)
{

UINT    i;

for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
name[i] = name_string[i];
name[i] =  0;

for (i = 0; i< (NX_PPP_PASSWORD_SIZE-1); i++)
password[i] = password_string[i];
password_string[i] =  0;

return(NX_SUCCESS);  
}

UINT  verify_login(CHAR *name, CHAR *password)
{

/* Assume name and password are correct. Normally, 
a comparison would be made here!  */
printf("Name: %s, Password: %s\n", name, password);

return(NX_SUCCESS);  
}
```

## <a name="nx_ppp_ping_request"></a><span data-ttu-id="f3886-405">nx_ppp_ping_request</span><span class="sxs-lookup"><span data-stu-id="f3886-405">nx_ppp_ping_request</span></span>

<span data-ttu-id="f3886-406">Отправка запроса проверки связи LCP</span><span class="sxs-lookup"><span data-stu-id="f3886-406">Send an LCP ping request</span></span>

### <a name="prototype"></a><span data-ttu-id="f3886-407">Прототип</span><span class="sxs-lookup"><span data-stu-id="f3886-407">Prototype</span></span>

```c
UINT  nx_ppp_ping_request(NX_PPP *ppp_ptr, CHAR *data, 
                          UINT data_size, ULONG wait_opion);
```

### <a name="description"></a><span data-ttu-id="f3886-408">Описание</span><span class="sxs-lookup"><span data-stu-id="f3886-408">Description</span></span>

<span data-ttu-id="f3886-409">Эта служба отправляет запрос LCP и устанавливает флаг, обозначающий, что устройство PPP ожидает ответ на проверку связи.</span><span class="sxs-lookup"><span data-stu-id="f3886-409">This service sends an LCP request and sets a flag that the PPP device is waiting for an echo response.</span></span> <span data-ttu-id="f3886-410">Параметр wait здесь предназначен в первую очередь для вызова *nx_packet_allocate*.</span><span class="sxs-lookup"><span data-stu-id="f3886-410">The wait option is primarily for the *nx_packet_allocate* call.</span></span> <span data-ttu-id="f3886-411">Служба возвращает управление сразу после отправки запроса.</span><span class="sxs-lookup"><span data-stu-id="f3886-411">The service returns as soon as the request is sent.</span></span> <span data-ttu-id="f3886-412">Она не ждет никакого ответа.</span><span class="sxs-lookup"><span data-stu-id="f3886-412">It does not wait for a response.</span></span> 

<span data-ttu-id="f3886-413">При получении соответствующего ответа на проверку связи установленный флаг будет снят задачей потока PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-413">When a matching echo response is received, the PPP thread task will clear the flag.</span></span> <span data-ttu-id="f3886-414">Устройство PPP должно выполнить часть согласования PPP, относящуюся к LCP.</span><span class="sxs-lookup"><span data-stu-id="f3886-414">The PPP device must have completed the LCP part of the PPP negotiation.</span></span>

<span data-ttu-id="f3886-415">Эта служба полезна для настроек PPP, в которых не используется опрос оборудования для получения состояния канала.</span><span class="sxs-lookup"><span data-stu-id="f3886-415">This service is useful for PPP set ups where polling the hardware for link status may not be readily possible.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f3886-416">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="f3886-416">Input Parameters</span></span>

- <span data-ttu-id="f3886-417">**ppp_ptr**: указатель на блок управления PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-417">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="f3886-418">**data**: указатель на данные, которые отправляются в запросе проверки связи.</span><span class="sxs-lookup"><span data-stu-id="f3886-418">**data**: Pointer to data to send in echo request.</span></span>
- <span data-ttu-id="f3886-419">**data_size**: размер данных для отправки wait_option: время ожидания до отправки сообщения проверки связи LCP.</span><span class="sxs-lookup"><span data-stu-id="f3886-419">**data_size**: Size of data to send wait_option Time to wait to send the LCP echo message.</span></span>

### <a name="return-values"></a><span data-ttu-id="f3886-420">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="f3886-420">Return Values</span></span>

- <span data-ttu-id="f3886-421">**NX_SUCCESS** (0x00): запрос проверки связи успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="f3886-421">**NX_SUCCESS**: (0x00) Successful sent echo request.</span></span>
- <span data-ttu-id="f3886-422">**NX_PPP_NOT_ESTABLISHED** (0xB5): соединение PPP не установлено.</span><span class="sxs-lookup"><span data-stu-id="f3886-422">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP connection not established.</span></span>
- <span data-ttu-id="f3886-423">NX_PTR_ERROR (0x07): недопустимый указатель PPP или указатель на функцию приложения.</span><span class="sxs-lookup"><span data-stu-id="f3886-423">NX_PTR_ERROR: (0x07) Invalid PPP pointer or application function pointer.</span></span>
- <span data-ttu-id="f3886-424">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="f3886-424">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f3886-425">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="f3886-425">Allowed From</span></span>

<span data-ttu-id="f3886-426">Потоки приложения</span><span class="sxs-lookup"><span data-stu-id="f3886-426">Application threads</span></span>

### <a name="example"></a><span data-ttu-id="f3886-427">Например, .</span><span class="sxs-lookup"><span data-stu-id="f3886-427">Example</span></span>

```c

CHAR    buffer[] = "username";
UINT    buffer_length =  sizeof("username ") - 1;

/* Send an LCP ping request”. */
status =  nx_ppp_ping_request(&my_ppp, &buffer[0], buffer_length, 200);

/* If status is NX_SUCCESS the LCP echo request was successfully sent. Now wait to 
   receive a response. */

while(my_ppp.nx_ppp_lcp_echo_reply_id > 0)
{
    tx_thread_sleep(100);
}

/* Got a valid reply! */
```

## <a name="nx_ppp_raw_string_send"></a><span data-ttu-id="f3886-428">nx_ppp_raw_string_send</span><span class="sxs-lookup"><span data-stu-id="f3886-428">nx_ppp_raw_string_send</span></span>

<span data-ttu-id="f3886-429">Отправка необработанной строки ASCII</span><span class="sxs-lookup"><span data-stu-id="f3886-429">Send a raw ASCII string</span></span>

### <a name="prototype"></a><span data-ttu-id="f3886-430">Прототип</span><span class="sxs-lookup"><span data-stu-id="f3886-430">Prototype</span></span>

```c
UINT  nx_ppp_raw_sting_send(NX_PPP *ppp_ptr, CHAR *string_ptr);
```

### <a name="description"></a><span data-ttu-id="f3886-431">Описание</span><span class="sxs-lookup"><span data-stu-id="f3886-431">Description</span></span>

<span data-ttu-id="f3886-432">Эта служба отправляет из интерфейса PPP строку ASCII без использования протокола PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-432">This service sends a non-PPP ASCII string directly out the PPP interface.</span></span> <span data-ttu-id="f3886-433">Обычно она вызывается в том случае, если PPP получает пакет с информацией об управлении модемом в формате, отличном от PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-433">It is typically used after PPP receives an non-PPP packet that contains modem control information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f3886-434">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="f3886-434">Input Parameters</span></span>

- <span data-ttu-id="f3886-435">**ppp_ptr**: указатель на блок управления PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-435">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="f3886-436">**string_ptr**: указатель на строку для отправки.</span><span class="sxs-lookup"><span data-stu-id="f3886-436">**string_ptr**: Pointer to string to send.</span></span>

### <a name="return-values"></a><span data-ttu-id="f3886-437">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="f3886-437">Return Values</span></span>

- <span data-ttu-id="f3886-438">**NX_SUCCESS** (0x00): необработанная строка PPP успешно отправлена.</span><span class="sxs-lookup"><span data-stu-id="f3886-438">**NX_SUCCESS**: (0x00) Successful PPP raw string send.</span></span>
- <span data-ttu-id="f3886-439">NX_PTR_ERROR (0x07): недопустимый указатель PPP или указатель на строку.</span><span class="sxs-lookup"><span data-stu-id="f3886-439">NX_PTR_ERROR: (0x07) Invalid PPP pointer or string pointer.</span></span>
- <span data-ttu-id="f3886-440">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="f3886-440">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f3886-441">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="f3886-441">Allowed From</span></span>

<span data-ttu-id="f3886-442">Потоки</span><span class="sxs-lookup"><span data-stu-id="f3886-442">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f3886-443">Например, .</span><span class="sxs-lookup"><span data-stu-id="f3886-443">Example</span></span>

```c

/* Send “CLIENTSERVER” to “CLIENT” sent by Windows 98 before PPP is
initiated.  */
status =  nx_ppp_raw_string_send(&my_ppp, “CLIENTSERVER”);

/* If status is NX_SUCCESS the raw string was successfully Sent via PPP. */
```
## <a name="nx_ppp_restart"></a><span data-ttu-id="f3886-444">nx_ppp_restart</span><span class="sxs-lookup"><span data-stu-id="f3886-444">nx_ppp_restart</span></span>

<span data-ttu-id="f3886-445">Перезапуск обработки PPP</span><span class="sxs-lookup"><span data-stu-id="f3886-445">Restart PPP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="f3886-446">Прототип</span><span class="sxs-lookup"><span data-stu-id="f3886-446">Prototype</span></span>

```c
UINT  nx_ppp_restart(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="f3886-447">Описание</span><span class="sxs-lookup"><span data-stu-id="f3886-447">Description</span></span>

<span data-ttu-id="f3886-448">Эта служба перезапускает обработку PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-448">This service restarts the PPP processing.</span></span> <span data-ttu-id="f3886-449">Обычно она вызывается, когда необходимо восстановить связь при получении сведений об отключении канала через обратный вызов или сообщения управления модемом в формате, отличном от PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-449">It is typically called when the link needs to be re-established either from a link down callback or by a non-PPP modem message indicating communication was lost.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f3886-450">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="f3886-450">Input Parameters</span></span>

- <span data-ttu-id="f3886-451">**ppp_ptr**: указатель на блок управления PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-451">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="f3886-452">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="f3886-452">Return Values</span></span>

- <span data-ttu-id="f3886-453">**NX_SUCCESS** (0x00): перезапуск PPP успешно инициирован.</span><span class="sxs-lookup"><span data-stu-id="f3886-453">**NX_SUCCESS**: (0x00) Successful PPP restart initiated.</span></span>
- <span data-ttu-id="f3886-454">NX_PTR_ERROR (0x07): недопустимый указатель PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-454">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="f3886-455">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="f3886-455">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f3886-456">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="f3886-456">Allowed From</span></span>

<span data-ttu-id="f3886-457">Потоки</span><span class="sxs-lookup"><span data-stu-id="f3886-457">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f3886-458">Например, .</span><span class="sxs-lookup"><span data-stu-id="f3886-458">Example</span></span>

```c
/* Restart the PPP instance “my_ppp”.  */
status =  nx_ppp_restart(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been restarted. */
```

## <a name="nx_ppp_start"></a><span data-ttu-id="f3886-459">nx_ppp_start</span><span class="sxs-lookup"><span data-stu-id="f3886-459">nx_ppp_start</span></span>

<span data-ttu-id="f3886-460">Запуск обработки PPP</span><span class="sxs-lookup"><span data-stu-id="f3886-460">Start PPP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="f3886-461">Прототип</span><span class="sxs-lookup"><span data-stu-id="f3886-461">Prototype</span></span>

```c
UINT  nx_ppp_start(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="f3886-462">Описание</span><span class="sxs-lookup"><span data-stu-id="f3886-462">Description</span></span>

<span data-ttu-id="f3886-463">Эта служба запускает обработку PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-463">This service starts the PPP processing.</span></span> <span data-ttu-id="f3886-464">Обычно она вызывается сразу после вызова nx_ppp_stop().</span><span class="sxs-lookup"><span data-stu-id="f3886-464">It is typically called after nx_ppp_stop() called.</span></span>

>[!NOTE]
> <span data-ttu-id="f3886-465">PPP автоматически начинает обработку PPP, как только связь будет установлена.</span><span class="sxs-lookup"><span data-stu-id="f3886-465">PPP automatically starts the PPP processing when the link is enabled.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f3886-466">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="f3886-466">Input Parameters</span></span>

- <span data-ttu-id="f3886-467">**ppp_ptr**: указатель на блок управления PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-467">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="f3886-468">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="f3886-468">Return Values</span></span>

- <span data-ttu-id="f3886-469">**NX_SUCCESS** (0x00): запуск PPP успешно инициирован.</span><span class="sxs-lookup"><span data-stu-id="f3886-469">**NX_SUCCESS**: (0x00) Successful PPP start initiated.</span></span> 
- <span data-ttu-id="f3886-470">**NX_PPP_ALREADY_STARTED** (0xb9): соединение PPP уже запущено.</span><span class="sxs-lookup"><span data-stu-id="f3886-470">**NX_PPP_ALREADY_STARTED**: (0xb9) PPP already started.</span></span>
- <span data-ttu-id="f3886-471">NX_PTR_ERROR (0x07): недопустимый указатель PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-471">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="f3886-472">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="f3886-472">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f3886-473">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="f3886-473">Allowed From</span></span>

<span data-ttu-id="f3886-474">Потоки</span><span class="sxs-lookup"><span data-stu-id="f3886-474">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f3886-475">Например, .</span><span class="sxs-lookup"><span data-stu-id="f3886-475">Example</span></span>

```c
/* Start the PPP instance “my_ppp”.  */
status =  nx_ppp_start(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been started. */
```

## <a name="nx_ppp_status_get"></a><span data-ttu-id="f3886-476">nx_ppp_status_get</span><span class="sxs-lookup"><span data-stu-id="f3886-476">nx_ppp_status_get</span></span>

<span data-ttu-id="f3886-477">Получение текущего состояния PPP</span><span class="sxs-lookup"><span data-stu-id="f3886-477">Get current PPP status</span></span>

### <a name="prototype"></a><span data-ttu-id="f3886-478">Прототип</span><span class="sxs-lookup"><span data-stu-id="f3886-478">Prototype</span></span>

```c
UINT  nx_ppp_status_get(NX_PPP *ppp_ptr, UINT *status_ptr);
```
### <a name="description"></a><span data-ttu-id="f3886-479">Описание</span><span class="sxs-lookup"><span data-stu-id="f3886-479">Description</span></span>

<span data-ttu-id="f3886-480">Эта служба получает текущее состояние указанного экземпляра PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-480">This service gets the current status of the specified PPP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f3886-481">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="f3886-481">Input Parameters</span></span>

- <span data-ttu-id="f3886-482">**ppp_ptr**: указатель на блок управления PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-482">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="f3886-483">**status_ptr**: назначение для состояния PPP, которое может принимать приведенные ниже значения состояния.</span><span class="sxs-lookup"><span data-stu-id="f3886-483">**status_ptr**: Destination for the PPP status, the following are possible status values:</span></span>
    - <span data-ttu-id="f3886-484">**NX_PPP_STATUS_ESTABLISHED**</span><span class="sxs-lookup"><span data-stu-id="f3886-484">**NX_PPP_STATUS_ESTABLISHED**</span></span>
    - <span data-ttu-id="f3886-485">**NX_PPP_STATUS_LCP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="f3886-485">**NX_PPP_STATUS_LCP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="f3886-486">**NX_PPP_STATUS_LCP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="f3886-486">**NX_PPP_STATUS_LCP_FAILED**</span></span>
    - <span data-ttu-id="f3886-487">**NX_PPP_STATUS_PAP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="f3886-487">**NX_PPP_STATUS_PAP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="f3886-488">**NX_PPP_STATUS_PAP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="f3886-488">**NX_PPP_STATUS_PAP_FAILED**</span></span>
    - <span data-ttu-id="f3886-489">**NX_PPP_STATUS_CHAP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="f3886-489">**NX_PPP_STATUS_CHAP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="f3886-490">**NX_PPP_STATUS_CHAP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="f3886-490">**NX_PPP_STATUS_CHAP_FAILED**</span></span>
    - <span data-ttu-id="f3886-491">**NX_PPP_STATUS_IPCP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="f3886-491">**NX_PPP_STATUS_IPCP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="f3886-492">**NX_PPP_STATUS_IPCP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="f3886-492">**NX_PPP_STATUS_IPCP_FAILED**</span></span>

>[!NOTE]
> <span data-ttu-id="f3886-493">Состояние считается допустимым только в том случае, если API возвращает значение NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="f3886-493">The status is only valid if the API returns NX_SUCCESS.</span></span> <span data-ttu-id="f3886-494">Кроме того, при получении любого значения состояния с постфиксом _FAILED обработка PPP прекращается до тех пор, пока приложение не перезапустит ее.</span><span class="sxs-lookup"><span data-stu-id="f3886-494">In addition, if any of the \*_FAILED status values are returned, PPP processing is effectively stopped until it is restarted again by the application.</span></span>

### <a name="return-values"></a><span data-ttu-id="f3886-495">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="f3886-495">Return Values</span></span>

- <span data-ttu-id="f3886-496">**NX_SUCCESS** (0x00): запрос состояния PPP успешно выполнен.</span><span class="sxs-lookup"><span data-stu-id="f3886-496">**NX_SUCCESS**: (0x00) Successful PPP status request.</span></span>
- <span data-ttu-id="f3886-497">NX_PTR_ERROR (0x07): недопустимый указатель PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-497">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f3886-498">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="f3886-498">Allowed From</span></span>

<span data-ttu-id="f3886-499">Инициализация, потоки, таймеры, подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="f3886-499">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="f3886-500">Например, .</span><span class="sxs-lookup"><span data-stu-id="f3886-500">Example</span></span>

```c
UINT ppp_status;
UINT status;


/* Get the current status of PPP instance “my_ppp”.  */
status =  nx_ppp_status_get(&my_ppp, &ppp_status);

/* If status is NX_SUCCESS the current internal PPP status is contained in
   “ppp_status”. */
```
## <a name="nx_ppp_stop"></a><span data-ttu-id="f3886-501">nx_ppp_stop</span><span class="sxs-lookup"><span data-stu-id="f3886-501">nx_ppp_stop</span></span>

<span data-ttu-id="f3886-502">Запуск обработки PPP</span><span class="sxs-lookup"><span data-stu-id="f3886-502">Start PPP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="f3886-503">Прототип</span><span class="sxs-lookup"><span data-stu-id="f3886-503">Prototype</span></span>

```c
UINT  nx_ppp_stop(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="f3886-504">Описание</span><span class="sxs-lookup"><span data-stu-id="f3886-504">Description</span></span>

<span data-ttu-id="f3886-505">Эта служба останавливает обработку PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-505">This service stops the PPP processing.</span></span> <span data-ttu-id="f3886-506">Пользователь также может вызвать nx_ppp_start(), чтобы начать обработку PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-506">User also can calls nx_ppp_start() to start the PPP processing if needed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f3886-507">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="f3886-507">Input Parameters</span></span>

- <span data-ttu-id="f3886-508">**ppp_ptr**: указатель на блок управления PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-508">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="f3886-509">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="f3886-509">Return Values</span></span>

- <span data-ttu-id="f3886-510">**NX_SUCCESS** (0x00): запуск PPP успешно инициирован.</span><span class="sxs-lookup"><span data-stu-id="f3886-510">**NX_SUCCESS**: (0x00) Successful PPP start initiated.</span></span> 
- <span data-ttu-id="f3886-511">**NX_PPP_ALREADY_STOPPED** (0xb8): обработка PPP уже остановлена.</span><span class="sxs-lookup"><span data-stu-id="f3886-511">**NX_PPP_ALREADY_STOPPED**: (0xb8) PPP already stopped.</span></span>
- <span data-ttu-id="f3886-512">NX_PTR_ERROR (0x07): недопустимый указатель PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-512">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="f3886-513">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="f3886-513">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f3886-514">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="f3886-514">Allowed From</span></span>

<span data-ttu-id="f3886-515">Потоки</span><span class="sxs-lookup"><span data-stu-id="f3886-515">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f3886-516">Например, .</span><span class="sxs-lookup"><span data-stu-id="f3886-516">Example</span></span>

```c
/* Stop the PPP instance “my_ppp”.  */
status =  nx_ppp_stop(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been stopped. */
```
## <a name="nx_ppp_packet_receive"></a><span data-ttu-id="f3886-517">nx_ppp_packet_receive</span><span class="sxs-lookup"><span data-stu-id="f3886-517">nx_ppp_packet_receive</span></span>

<span data-ttu-id="f3886-518">Получение пакета PPP</span><span class="sxs-lookup"><span data-stu-id="f3886-518">Receive PPP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="f3886-519">Прототип</span><span class="sxs-lookup"><span data-stu-id="f3886-519">Prototype</span></span>

```c
UINT  nx_ppp_packet_receive(NX_PPP *ppp_ptr, NX_PACKET *packet_ptr);

```

### <a name="description"></a><span data-ttu-id="f3886-520">Описание</span><span class="sxs-lookup"><span data-stu-id="f3886-520">Description</span></span>

<span data-ttu-id="f3886-521">Эта служба получает пакет PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-521">This service receives PPP packet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f3886-522">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="f3886-522">Input Parameters</span></span>

- <span data-ttu-id="f3886-523">**ppp_ptr**: указатель на блок управления PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-523">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="f3886-524">**packet_ptr**: указатель на пакет PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-524">**packet_ptr**: Pointer to PPP packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="f3886-525">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="f3886-525">Return Values</span></span>

- <span data-ttu-id="f3886-526">**NX_SUCCESS** (0x00): запрос состояния PPP успешно выполнен.</span><span class="sxs-lookup"><span data-stu-id="f3886-526">**NX_SUCCESS**: (0x00) Successful PPP status request.</span></span>
- <span data-ttu-id="f3886-527">NX_PTR_ERROR (0x07): недопустимый указатель PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-527">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f3886-528">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="f3886-528">Allowed From</span></span>

<span data-ttu-id="f3886-529">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="f3886-529">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="f3886-530">Например, .</span><span class="sxs-lookup"><span data-stu-id="f3886-530">Example</span></span>

```c
/* Receive the PPP packet of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_receive(&my_ppp, packet_ptr);

/* If status is NX_SUCCESS the PPP packet has received. */


```
## <a name="nx_ppp_packet_send_set"></a><span data-ttu-id="f3886-531">nx_ppp_packet_send_set</span><span class="sxs-lookup"><span data-stu-id="f3886-531">nx_ppp_packet_send_set</span></span>

<span data-ttu-id="f3886-532">Определение функции отправки пакета PPP</span><span class="sxs-lookup"><span data-stu-id="f3886-532">Set the PPP packet send function</span></span>

### <a name="prototype"></a><span data-ttu-id="f3886-533">Прототип</span><span class="sxs-lookup"><span data-stu-id="f3886-533">Prototype</span></span>

```c
UINT  nx_ppp_packet_send_set(NX_PPP *ppp_ptr, 
                             VOID (*nx_ppp_packet_send)(NX_PACKET *packet_ptr));

```

### <a name="description"></a><span data-ttu-id="f3886-534">Описание</span><span class="sxs-lookup"><span data-stu-id="f3886-534">Description</span></span>

<span data-ttu-id="f3886-535">Эта служба задает функцию для отправки пакета PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-535">This service sets the PPP packet send funciton.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f3886-536">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="f3886-536">Input Parameters</span></span>

- <span data-ttu-id="f3886-537">**ppp_ptr**: указатель на блок управления PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-537">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="f3886-538">**nx_ppp_packet_send**: подпрограмма для отправки пакета PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-538">**nx_ppp_packet_send**: Routine to send PPP packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="f3886-539">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="f3886-539">Return Values</span></span>

- <span data-ttu-id="f3886-540">**NX_SUCCESS** (0x00): запрос состояния PPP успешно выполнен.</span><span class="sxs-lookup"><span data-stu-id="f3886-540">**NX_SUCCESS**: (0x00) Successful PPP status request.</span></span>
- <span data-ttu-id="f3886-541">NX_PTR_ERROR (0x07): недопустимый указатель PPP.</span><span class="sxs-lookup"><span data-stu-id="f3886-541">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f3886-542">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="f3886-542">Allowed From</span></span>

<span data-ttu-id="f3886-543">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="f3886-543">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="f3886-544">Пример</span><span class="sxs-lookup"><span data-stu-id="f3886-544">Example</span></span>

```c
/* Set the PPP packet send function of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_send_set(&my_ppp, nx_ppp_packet_send);

/* If status is NX_SUCCESS the PPP packet send function has set. */


```