---
title: Глава 3. Описание служб клиента PTP для NetX Duo в ОСРВ Azure
description: Эта глава содержит описание всех служб клиента PTP для NetX Duo в алфавитном порядке.
author: v-condav
ms.author: v-condav
ms.date: 01/27/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b4cdeca81c157934e35a219cd5535ec38f2c0746
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814588"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-ptp-client-services"></a><span data-ttu-id="af97c-103">Глава 3. Описание служб клиента PTP для NetX Duo в ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="af97c-103">Chapter 3 - Description of Azure RTOS NetX Duo PTP Client Services</span></span>

<span data-ttu-id="af97c-104">Эта глава содержит описание всех служб клиента PTP для NetX Duo, которые перечислены ниже в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="af97c-104">This chapter contains a description of all NetX Duo PTP client services (listed below) in alphabetical order.</span></span>

[!NOTE]
> <span data-ttu-id="af97c-105">*В разделе **Возвращаемые значения** для приведенных ниже описаний функций API значения, **выделенные полужирным шрифтом**, не затрагиваются определением параметра **NX_DISABLE_ERROR_CHECKING**, используемым для отключения проверки ошибок API, в то время как значения без такого выделения полностью отключаются.*</span><span class="sxs-lookup"><span data-stu-id="af97c-105">*In the **Return Values** section in the following API function descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.*</span></span>

## <a name="nx_ptp_client_create"></a><span data-ttu-id="af97c-106">nx_ptp_client_create</span><span class="sxs-lookup"><span data-stu-id="af97c-106">nx_ptp_client_create</span></span>

<span data-ttu-id="af97c-107">Создание экземпляра клиента PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-107">Create a PTP client instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="af97c-108">Прототип</span><span class="sxs-lookup"><span data-stu-id="af97c-108">Prototype</span></span>

```C
UINT nx_ptp_client_create(
    NX_PTP_CLIENT *client_ptr, NX_IP *ip_ptr, 
    UINT interface_index,
    NX_PACKET_POOL *packet_pool_ptr, 
    UINT thread_priority, 
    UCHAR *thread_stack, 
    UINT stack_size,
    NX_PTP_CLIENT_CLOCK_CALLBACK clock_callback, 
    VOID *clock_callback_data);
```

### <a name="description"></a><span data-ttu-id="af97c-109">Описание</span><span class="sxs-lookup"><span data-stu-id="af97c-109">Description</span></span>

<span data-ttu-id="af97c-110">Эта служба создает экземпляр клиента PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-110">This service creates an instance of the PTP client.</span></span>

<span data-ttu-id="af97c-111">Обратите внимание, что приложение должно сначала создать экземпляр IP-адреса и пул пакетов, чтобы клиент PTP мог передавать пакеты.</span><span class="sxs-lookup"><span data-stu-id="af97c-111">Note that the  application must first create an IP instance and a packet pool for the PTP client to transmit packets.</span></span> <span data-ttu-id="af97c-112">Что касается пула пакетов, приложение может использовать тот же пул пакетов в экземпляре IP-адреса или создать выделенный пул пакетов для клиента PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-112">For the packet pool, application may use the same packet pool in the IP instance; or it can create a dedicated packet pool for PTP client.</span></span>  <span data-ttu-id="af97c-113">Подход с выделенным пулом пакетов имеет преимущество использования небольших пакетов (128 байт, если используется IPv6, или 108 байт, если используется только IPv4).</span><span class="sxs-lookup"><span data-stu-id="af97c-113">The dedicated packet pool approach has the advantage of using small packets (128 bytes packets if IPv6 is used, or 108 bytes for IPv4-only).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="af97c-114">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="af97c-114">Input Parameters</span></span>
* <span data-ttu-id="af97c-115">**client_ptr** — указатель на создаваемый клиент PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-115">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="af97c-116">**ip_ptr** — указатель на экземпляр IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="af97c-116">**ip_ptr** Pointer to IP instance</span></span>
* <span data-ttu-id="af97c-117">**interface_index** — индекс сетевого интерфейса PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-117">**interface_index** Index of PTP network interface</span></span>
* <span data-ttu-id="af97c-118">**packet_pool_ptr** — указатель на пул пакетов клиента.</span><span class="sxs-lookup"><span data-stu-id="af97c-118">**packet_pool_ptr** Pointer to client packet pool</span></span>
* <span data-ttu-id="af97c-119">**thread_priority** — приоритет потока PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-119">**thread_priority**  Priority of PTP thread</span></span>
* <span data-ttu-id="af97c-120">**thread_stack** — указатель на стек потоков.</span><span class="sxs-lookup"><span data-stu-id="af97c-120">**thread_stack** Pointer to thread stack</span></span>
* <span data-ttu-id="af97c-121">**stack_size** — размер стека потоков.</span><span class="sxs-lookup"><span data-stu-id="af97c-121">**stack_size** Size of thread stack</span></span>
* <span data-ttu-id="af97c-122">**clock_callback** — обратный вызов тактового генератора PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-122">**clock_callback** PTP clock callback</span></span>
* <span data-ttu-id="af97c-123">**clock_callback_data** — данные для обратного вызова тактового генератора.</span><span class="sxs-lookup"><span data-stu-id="af97c-123">**clock_callback_data** Data for the clock callback</span></span>

### <a name="return-values"></a><span data-ttu-id="af97c-124">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="af97c-124">Return Values</span></span>
* <span data-ttu-id="af97c-125">**NX_SUCCESS** (0x00) — клиент успешно создан.</span><span class="sxs-lookup"><span data-stu-id="af97c-125">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="af97c-126">**NX_PTP_CLIENT_INSUFFICIENT_PACKET_PAYLOAD** (0xD04) — слишком короткие полезные данные пакетов.</span><span class="sxs-lookup"><span data-stu-id="af97c-126">**NX_PTP_CLIENT_INSUFFICIENT_PACKET_PAYLOAD** (0xD04) Packet payload too small</span></span>
* <span data-ttu-id="af97c-127">**NX_PTP_CLIENT_CLOCK_CALLBACK_FAILURE** (0xD05) — сбой обратного вызова тактового генератора.</span><span class="sxs-lookup"><span data-stu-id="af97c-127">**NX_PTP_CLIENT_CLOCK_CALLBACK_FAILURE** (0xD05) Failure on clock callback</span></span>
* <span data-ttu-id="af97c-128">**status** — состояние завершения вызовов служб NetX Duo и ThreadX.</span><span class="sxs-lookup"><span data-stu-id="af97c-128">**status** Status completion of NetX Duo and ThreadX service calls</span></span>
* <span data-ttu-id="af97c-129">NX_PTR_ERROR (0x07) — недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="af97c-129">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
* <span data-ttu-id="af97c-130">NX_INVALID_INTERFACE (0x4C) — недопустимый интерфейс.</span><span class="sxs-lookup"><span data-stu-id="af97c-130">NX_INVALID_INTERFACE (0x4C) Invalid interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="af97c-131">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="af97c-131">Allowed From</span></span>
<span data-ttu-id="af97c-132">Потоки</span><span class="sxs-lookup"><span data-stu-id="af97c-132">Threads</span></span>

### <a name="example"></a><span data-ttu-id="af97c-133">Пример</span><span class="sxs-lookup"><span data-stu-id="af97c-133">Example</span></span>
```C
/* Create the PTP client instance */
status = nx_ptp_client_create(&ptp_client, &ip_0, 0, &pool_0, 
                              PTP_THREAD_PRIORITY, (UCHAR *)ptp_stack, sizeof(ptp_stack),
                              clock_callback, NX_NULL);

/* If the client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_delete"></a><span data-ttu-id="af97c-134">nx_ptp_client_delete</span><span class="sxs-lookup"><span data-stu-id="af97c-134">nx_ptp_client_delete</span></span>

<span data-ttu-id="af97c-135">Удаляет экземпляр клиента PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-135">Deletes a PTP client instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="af97c-136">Прототип</span><span class="sxs-lookup"><span data-stu-id="af97c-136">Prototype</span></span>

```C
UINT nx_ptp_client_delete(NX_PTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="af97c-137">Описание</span><span class="sxs-lookup"><span data-stu-id="af97c-137">Description</span></span>

<span data-ttu-id="af97c-138">Эта служба удаляет экземпляр клиента PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-138">This service deletes an instance of the PTP client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="af97c-139">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="af97c-139">Input Parameters</span></span>
* <span data-ttu-id="af97c-140">**client_ptr** — указатель на удаляемый клиент PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-140">**client_ptr** Pointer to PTP client to delete</span></span>

### <a name="return-values"></a><span data-ttu-id="af97c-141">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="af97c-141">Return Values</span></span>
* <span data-ttu-id="af97c-142">**NX_SUCCESS** (0x00) — клиент успешно удален.</span><span class="sxs-lookup"><span data-stu-id="af97c-142">**NX_SUCCESS** (0x00) Client successfully deleted</span></span>
* <span data-ttu-id="af97c-143">NX_PTR_ERROR (0x07) — недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="af97c-143">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="af97c-144">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="af97c-144">Allowed From</span></span>
<span data-ttu-id="af97c-145">Потоки</span><span class="sxs-lookup"><span data-stu-id="af97c-145">Threads</span></span>

### <a name="example"></a><span data-ttu-id="af97c-146">Пример</span><span class="sxs-lookup"><span data-stu-id="af97c-146">Example</span></span>
```C
/* Delete the PTP client instance */
status = nx_ptp_client_delete(&ptp_client);

/* If the client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_master_info_get"></a><span data-ttu-id="af97c-147">nx_ptp_client_master_info_get</span><span class="sxs-lookup"><span data-stu-id="af97c-147">nx_ptp_client_master_info_get</span></span>

<span data-ttu-id="af97c-148">Получение сведений о главном тактовом генераторе.</span><span class="sxs-lookup"><span data-stu-id="af97c-148">Get master clock information.</span></span>

### <a name="prototype"></a><span data-ttu-id="af97c-149">Прототип</span><span class="sxs-lookup"><span data-stu-id="af97c-149">Prototype</span></span>

```C
UINT nx_ptp_client_master_info_get(
    NX_PTP_CLIENT_MASTER *master_ptr, 
    NXD_ADDRESS *address, 
    UCHAR **port_identity, 
    UINT *port_identity_length, 
    UCHAR *priority1, 
    UCHAR *priority2, 
    UCHAR *clock_class, UCHAR *clock_accuracy, 
    USHORT *clock_variance, 
    UCHAR **grandmaster_identity,
    UINT *grandmaster_identity_length, 
    USHORT *steps_removed, 
    UCHAR *time_source);
```

### <a name="description"></a><span data-ttu-id="af97c-150">Описание</span><span class="sxs-lookup"><span data-stu-id="af97c-150">Description</span></span>
<span data-ttu-id="af97c-151">Эта служба получает сведения о главном тактовом генераторе.</span><span class="sxs-lookup"><span data-stu-id="af97c-151">This service gets information of master clock.</span></span> <span data-ttu-id="af97c-152">Основной блок управления передается пользовательскому приложению посредством функции обратного вызова события.</span><span class="sxs-lookup"><span data-stu-id="af97c-152">The master control block is passed to user application through event callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="af97c-153">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="af97c-153">Input Parameters</span></span>
* <span data-ttu-id="af97c-154">**master_ptr** — указатель на главный тактовый генератор PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-154">**master_ptr** Pointer to PTP master clock</span></span>
* <span data-ttu-id="af97c-155">**address** — адрес главного тактового генератора.</span><span class="sxs-lookup"><span data-stu-id="af97c-155">**address** Address of master clock</span></span>
* <span data-ttu-id="af97c-156">**port_identity** — главный порт и главное удостоверение PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-156">**port_identity** PTP master port and identity</span></span>
* <span data-ttu-id="af97c-157">**port_identity_length** — длина главного порта и главного удостоверения PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-157">**port_identity_length** Length of PTP master port and identity</span></span>
* <span data-ttu-id="af97c-158">**priority1** — приоритет Priority1 главного тактового генератора PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-158">**priority1** Priority1 of PTP master clock</span></span>
* <span data-ttu-id="af97c-159">**priority2** — приоритет Priority2 главного тактового генератора PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-159">**priority2** Priority2 of PTP master clock</span></span>
* <span data-ttu-id="af97c-160">**clock_class** — класс главного тактового генератора PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-160">**clock_class** Class of PTP master clock</span></span>
* <span data-ttu-id="af97c-161">**clock_accuracy** — точность главного тактового генератора PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-161">**clock_accuracy** Accuracy of PTP master clock</span></span>
* <span data-ttu-id="af97c-162">**clock_variance** — дисперсия главного тактового генератора PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-162">**clock_variance** Variance of PTP master clock</span></span>
* <span data-ttu-id="af97c-163">**grandmaster_identity** — удостоверение тактового генератора-грандмастера.</span><span class="sxs-lookup"><span data-stu-id="af97c-163">**grandmaster_identity** Identity of grandmaster clock</span></span>
* <span data-ttu-id="af97c-164">**grandmaster_identity_length** — длина удостоверения тактового генератора-грандмастера.</span><span class="sxs-lookup"><span data-stu-id="af97c-164">**grandmaster_identity_length** Length of grandmaster Identity</span></span>
* <span data-ttu-id="af97c-165">**steps_removed** — шаги, удаленные из заголовка PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-165">**steps_removed** Steps removed from PTP header</span></span>
* <span data-ttu-id="af97c-166">**time_source** — источник таймера, используемый тактовым генератором-грандмастером.</span><span class="sxs-lookup"><span data-stu-id="af97c-166">**time_source** The source of timer used by grandmaster clock</span></span>

### <a name="return-values"></a><span data-ttu-id="af97c-167">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="af97c-167">Return Values</span></span>
* <span data-ttu-id="af97c-168">**NX_SUCCESS** (0x00) — сведения о ведущем тактовом генераторе успешно получены.</span><span class="sxs-lookup"><span data-stu-id="af97c-168">**NX_SUCCESS** (0x00) Get master clock information successfully</span></span>
* <span data-ttu-id="af97c-169">NX_PTR_ERROR (0x07) — недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="af97c-169">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="af97c-170">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="af97c-170">Allowed From</span></span>
<span data-ttu-id="af97c-171">Потоки</span><span class="sxs-lookup"><span data-stu-id="af97c-171">Threads</span></span>

### <a name="example"></a><span data-ttu-id="af97c-172">Пример</span><span class="sxs-lookup"><span data-stu-id="af97c-172">Example</span></span>
```C
static UINT ptp_event_callback(NX_PTP_CLIENT *ptp_client_ptr, UINT event, VOID *event_data, VOID *callback_data)
{
NXD_ADDRESS address;
UCHAR *port_identity;
UINT port_identity_length;
UCHAR priority1, priority2;
UCHAR clock_class, clock_accuracy;
USHORT clock_variance;
UCHAR *grandmaster_identity;
UINT grandmaster_identity_length;
USHORT steps_removed;
UCHAR time_source;

    switch (event)
    {
        case NX_PTP_CLIENT_EVENT_MASTER:
        {
            status = nx_ptp_client_master_info_get((NX_PTP_CLIENT_MASTER *)event_data, 
                                                   &address, &port_identity,
                                                   &port_identity_length, &priority1, 
                                                   &priority2, &clock_class,
                                                   &clock_accuracy, &clock_variance, 
                                                   &grandmaster_identity,
                                                   &grandmaster_identity_length, 
                                                   &steps_removed, &time_source);

            /* If the master clock information was successfully get, status = NX_SUCCESS. */
            break;
        }

        /* Other event process. */
    }
}
```

## <a name="nx_ptp_client_packet_timestamp_notify"></a><span data-ttu-id="af97c-173">nx_ptp_client_packet_timestamp_notify</span><span class="sxs-lookup"><span data-stu-id="af97c-173">nx_ptp_client_packet_timestamp_notify</span></span>

<span data-ttu-id="af97c-174">Уведомление клиента PTP о метке времени пакета.</span><span class="sxs-lookup"><span data-stu-id="af97c-174">Notify PTP client the timestamp of the packet.</span></span>

### <a name="prototype"></a><span data-ttu-id="af97c-175">Прототип</span><span class="sxs-lookup"><span data-stu-id="af97c-175">Prototype</span></span>

```C
VOID nx_ptp_client_packet_timestamp_notify(
    NX_PTP_CLIENT *client_ptr, 
    NX_PACKET *packet_ptr, 
    NX_PTP_TIME *timestamp_ptr);
```

### <a name="description"></a><span data-ttu-id="af97c-176">Описание</span><span class="sxs-lookup"><span data-stu-id="af97c-176">Description</span></span>
<span data-ttu-id="af97c-177">Эта служба уведомляет клиент PTP о том, что пакет передается с меткой времени.</span><span class="sxs-lookup"><span data-stu-id="af97c-177">This service notifies the PTP client that packet is transmitted with timestamp.</span></span> <span data-ttu-id="af97c-178">Эта служба разработана для сетевого драйвера и вызывается при передаче пакета.</span><span class="sxs-lookup"><span data-stu-id="af97c-178">This service is designed for network driver and invoked when the packet is transmitted.</span></span> <span data-ttu-id="af97c-179">Метка времени обычно создается оборудованием.</span><span class="sxs-lookup"><span data-stu-id="af97c-179">The timestamp is usually generated by hardware.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="af97c-180">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="af97c-180">Input Parameters</span></span>
* <span data-ttu-id="af97c-181">**client_ptr** — указатель на создаваемый клиент PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-181">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="af97c-182">**packet_ptr** — указатель на передаваемый пакет PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-182">**packet_ptr** Pointer to PTP packet that is transmitted</span></span>
* <span data-ttu-id="af97c-183">**timestamp_ptr** — указатель на метку времени пакета PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-183">**timestamp_ptr** Pointer to timestamp of PTP packet</span></span>

### <a name="return-values"></a><span data-ttu-id="af97c-184">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="af97c-184">Return Values</span></span>
<span data-ttu-id="af97c-185">Нет</span><span class="sxs-lookup"><span data-stu-id="af97c-185">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="af97c-186">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="af97c-186">Allowed From</span></span>
<span data-ttu-id="af97c-187">Потоки</span><span class="sxs-lookup"><span data-stu-id="af97c-187">Threads</span></span>

### <a name="example"></a><span data-ttu-id="af97c-188">Пример</span><span class="sxs-lookup"><span data-stu-id="af97c-188">Example</span></span>
```C
/* Call notification callback */
nx_ptp_client_packet_timestamp_notify(client_ptr, packet_ptr, &ts);
```

## <a name="nx_ptp_client_soft_clock_callback"></a><span data-ttu-id="af97c-189">nx_ptp_client_soft_clock_callback</span><span class="sxs-lookup"><span data-stu-id="af97c-189">nx_ptp_client_soft_clock_callback</span></span>

<span data-ttu-id="af97c-190">Программная реализация тактового генератора PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-190">Software implementation of a PTP clock.</span></span>

### <a name="prototype"></a><span data-ttu-id="af97c-191">Прототип</span><span class="sxs-lookup"><span data-stu-id="af97c-191">Prototype</span></span>

```C
UINT nx_ptp_client_soft_clock_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT operation,
    NX_PTP_TIME *time_ptr, 
    NX_PACKET *packet_ptr,
    VOID *callback_data);
```

### <a name="description"></a><span data-ttu-id="af97c-192">Описание</span><span class="sxs-lookup"><span data-stu-id="af97c-192">Description</span></span>
<span data-ttu-id="af97c-193">Эта функция обратного вызова выступает в качестве источника имитированного тактового генератора низкого разрешения для PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-193">This callback function serves as a simulated low resolution clock source for PTP.</span></span> <span data-ttu-id="af97c-194">Эта подпрограммы предоставляется только для справки и не может использоваться для рабочей среды.</span><span class="sxs-lookup"><span data-stu-id="af97c-194">This routine is provided as a reference and cannot be used for production.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="af97c-195">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="af97c-195">Input Parameters</span></span>
* <span data-ttu-id="af97c-196">**client_ptr** — указатель на создаваемый клиент PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-196">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="af97c-197">**operation** — операция обратного вызова, допустимые значения определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="af97c-197">**operation** Callback operation, valid values are defined as:</span></span>
  * <span data-ttu-id="af97c-198">**NX_PTP_CLIENT_CLOCK_INIT** — инициализация тактового генератора.</span><span class="sxs-lookup"><span data-stu-id="af97c-198">**NX_PTP_CLIENT_CLOCK_INIT** Initialize clock.</span></span>
  * <span data-ttu-id="af97c-199">**NX_PTP_CLIENT_CLOCK_SET** — настройка текущей метки времени, которая задана `time_ptr`.</span><span class="sxs-lookup"><span data-stu-id="af97c-199">**NX_PTP_CLIENT_CLOCK_SET** Set current timestamp specified by `time_ptr`.</span></span>
  * <span data-ttu-id="af97c-200">**NX_PTP_CLIENT_CLOCK_GET** — передача текущей метки времени в `time_ptr`.</span><span class="sxs-lookup"><span data-stu-id="af97c-200">**NX_PTP_CLIENT_CLOCK_GET** Return current timestamp to `time_ptr`.</span></span>
  * <span data-ttu-id="af97c-201">**NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** — извлечение метки времени из `packet_ptr` в `time_ptr`.</span><span class="sxs-lookup"><span data-stu-id="af97c-201">**NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Extract timestamp from `packet_ptr` to `time_ptr`.</span></span>
  * <span data-ttu-id="af97c-202">**NX_PTP_CLIENT_CLOCK_ADJUST** — корректировка текущей метки времени менее чем на *1* секунду.</span><span class="sxs-lookup"><span data-stu-id="af97c-202">**NX_PTP_CLIENT_CLOCK_ADJUST** Adjust current timestamp less than *1* second.</span></span>
  * <span data-ttu-id="af97c-203">**NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** — отметка `packet_ptr`, предписывающая уведомить клиента PTP о метке времени при ее передаче.</span><span class="sxs-lookup"><span data-stu-id="af97c-203">**NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Mark the `packet_ptr` which requires to notify PTP client the timestamp when it is transmitted.</span></span>
  * <span data-ttu-id="af97c-204">**NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** — обновление программного таймера.</span><span class="sxs-lookup"><span data-stu-id="af97c-204">**NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Update soft timer.</span></span> <span data-ttu-id="af97c-205">Может игнорироваться аппаратными часами.</span><span class="sxs-lookup"><span data-stu-id="af97c-205">It can be ignored by hardware clock.</span></span>
* <span data-ttu-id="af97c-206">**time_ptr** — указатель на метку времени.</span><span class="sxs-lookup"><span data-stu-id="af97c-206">**time_ptr** Pointer to timestamp.</span></span>
* <span data-ttu-id="af97c-207">**packet_ptr** — указатель на пакет.</span><span class="sxs-lookup"><span data-stu-id="af97c-207">**packet_ptr** Pointer to packet.</span></span>
* <span data-ttu-id="af97c-208">**callback_data** — указатель на непрозрачные данные обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="af97c-208">**callback_data** Pointer to opaque callback data.</span></span>

### <a name="return-values"></a><span data-ttu-id="af97c-209">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="af97c-209">Return Values</span></span>
* <span data-ttu-id="af97c-210">**NX_SUCCESS** (0x00) — операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="af97c-210">**NX_SUCCESS** (0x00) Operation successfully</span></span>
* <span data-ttu-id="af97c-211">**NX_PTP_PARAM_ERROR** (0xD03) — недопустимый параметр.</span><span class="sxs-lookup"><span data-stu-id="af97c-211">**NX_PTP_PARAM_ERROR** (0xD03) Invalid parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="af97c-212">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="af97c-212">Allowed From</span></span>
<span data-ttu-id="af97c-213">Внутренняя часть PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-213">PTP internal</span></span>

### <a name="example"></a><span data-ttu-id="af97c-214">Пример</span><span class="sxs-lookup"><span data-stu-id="af97c-214">Example</span></span>
```C/* Create the PTP client instance */
status = nx_ptp_client_create(&ptp_client, &ip_0, 0, &pool_0, 
                              PTP_THREAD_PRIORITY, (UCHAR *)ptp_stack, sizeof(ptp_stack),
                              nx_ptp_client_soft_clock_callback, NX_NULL);

/* If the client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_start"></a><span data-ttu-id="af97c-215">nx_ptp_client_start</span><span class="sxs-lookup"><span data-stu-id="af97c-215">nx_ptp_client_start</span></span>

<span data-ttu-id="af97c-216">Запуск клиента PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-216">Start PTP client.</span></span>

### <a name="prototype"></a><span data-ttu-id="af97c-217">Прототип</span><span class="sxs-lookup"><span data-stu-id="af97c-217">Prototype</span></span>

```C
UINT nx_ptp_client_start(
    NX_PTP_CLIENT *client_ptr, 
    UCHAR *client_port_identity_ptr, 
    UINT client_port_identity_length,
    UINT domain, 
    UINT transport_specific, 
    NX_PTP_CLIENT_EVENT_CALLBACK event_callback,
    VOID *event_callback_data)
```

### <a name="description"></a><span data-ttu-id="af97c-218">Описание</span><span class="sxs-lookup"><span data-stu-id="af97c-218">Description</span></span>
<span data-ttu-id="af97c-219">Эта служба запускает ранее созданный экземпляр клиента PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-219">This service starts a previously created PTP client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="af97c-220">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="af97c-220">Input Parameters</span></span>
* <span data-ttu-id="af97c-221">**client_ptr** — указатель на создаваемый клиент PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-221">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="af97c-222">**client_port_identity_ptr** — указатель на порт и удостоверение клиента, может иметь значение NULL.</span><span class="sxs-lookup"><span data-stu-id="af97c-222">**client_port_identity_ptr** Pointer to client port and identity, it can be NULL</span></span>
* <span data-ttu-id="af97c-223">**client_port_identity_length** — длина порта и удостоверения клиента.</span><span class="sxs-lookup"><span data-stu-id="af97c-223">**client_port_identity_length** Length of client port and identity.</span></span> <span data-ttu-id="af97c-224">Она должна быть равна 0, если client_port_identity_ptr имеет значение NULL или NX_PTP_CLOCK_PORT_IDENTITY_SIZE (10)</span><span class="sxs-lookup"><span data-stu-id="af97c-224">It must be 0 if client_port_identity_ptr is NULL or NX_PTP_CLOCK_PORT_IDENTITY_SIZE (10)</span></span>
* <span data-ttu-id="af97c-225">**domain** — домен таковых генераторов PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-225">**domain** PTP clock domain</span></span>
* <span data-ttu-id="af97c-226">**transport_specific** — 4 бита, относящиеся к транспорту.</span><span class="sxs-lookup"><span data-stu-id="af97c-226">**transport_specific** 4 bits of transport specific</span></span>
* <span data-ttu-id="af97c-227">**event_callback** — функция обратного вызова, вызванная для события.</span><span class="sxs-lookup"><span data-stu-id="af97c-227">**event_callback** Callback function invoked on event</span></span>
* <span data-ttu-id="af97c-228">**event_callback_data** — данные для обратного вызова события.</span><span class="sxs-lookup"><span data-stu-id="af97c-228">**event_callback_data** Data for the event callback</span></span>

### <a name="return-values"></a><span data-ttu-id="af97c-229">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="af97c-229">Return Values</span></span>
* <span data-ttu-id="af97c-230">**NX_SUCCESS** (0x00) — клиент успешно запущен.</span><span class="sxs-lookup"><span data-stu-id="af97c-230">**NX_SUCCESS** (0x00) Client successfully started</span></span>
* <span data-ttu-id="af97c-231">**NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) — клиент PTP уже запущен.</span><span class="sxs-lookup"><span data-stu-id="af97c-231">**NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) PTP client already started</span></span>
* <span data-ttu-id="af97c-232">**status** — состояние завершения вызовов служб NetX Duo и ThreadX.</span><span class="sxs-lookup"><span data-stu-id="af97c-232">**status** Status completion of NetX Duo and ThreadX service calls</span></span>
* <span data-ttu-id="af97c-233">NX_PTR_ERROR (0x07) — недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="af97c-233">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="af97c-234">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="af97c-234">Allowed From</span></span>
<span data-ttu-id="af97c-235">Потоки</span><span class="sxs-lookup"><span data-stu-id="af97c-235">Threads</span></span>

### <a name="example"></a><span data-ttu-id="af97c-236">Пример</span><span class="sxs-lookup"><span data-stu-id="af97c-236">Example</span></span>
```C
status = nx_ptp_client_start(&ptp_client, NX_NULL, 0, 0, 0, ptp_event_callback, NX_NULL);

/* If the client was successfully started, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_stop"></a><span data-ttu-id="af97c-237">nx_ptp_client_stop</span><span class="sxs-lookup"><span data-stu-id="af97c-237">nx_ptp_client_stop</span></span>

<span data-ttu-id="af97c-238">Остановка клиента PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-238">Stop PTP client.</span></span>  <span data-ttu-id="af97c-239">После остановки клиент PTP не обрабатывает пакеты PTP и не передает их.</span><span class="sxs-lookup"><span data-stu-id="af97c-239">After the PTP client is stopped, it does not process PTP packets, nor does it transmit PTP packets.</span></span>

### <a name="prototype"></a><span data-ttu-id="af97c-240">Прототип</span><span class="sxs-lookup"><span data-stu-id="af97c-240">Prototype</span></span>

```C
UINT nx_ptp_client_stop(NX_PTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="af97c-241">Описание</span><span class="sxs-lookup"><span data-stu-id="af97c-241">Description</span></span>
<span data-ttu-id="af97c-242">Эта служба останавливает ранее созданный и запущенный экземпляр клиента PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-242">This service stops a previously created and started PTP client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="af97c-243">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="af97c-243">Input Parameters</span></span>
* <span data-ttu-id="af97c-244">**client_ptr** — указатель на останавливаемый клиент PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-244">**client_ptr** Pointer to PTP client to stop</span></span>

### <a name="return-values"></a><span data-ttu-id="af97c-245">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="af97c-245">Return Values</span></span>
* <span data-ttu-id="af97c-246">**NX_SUCCESS** (0x00) — клиент успешно остановлен.</span><span class="sxs-lookup"><span data-stu-id="af97c-246">**NX_SUCCESS** (0x00) Client successfully stopped</span></span>
* <span data-ttu-id="af97c-247">**NX_PTP_CLIENT_NOT_STARTED** (0xD01) клиент не запущен.</span><span class="sxs-lookup"><span data-stu-id="af97c-247">**NX_PTP_CLIENT_NOT_STARTED** (0xD01) Client not started</span></span>
* <span data-ttu-id="af97c-248">NX_PTR_ERROR (0x07) — недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="af97c-248">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="af97c-249">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="af97c-249">Allowed From</span></span>
<span data-ttu-id="af97c-250">Потоки</span><span class="sxs-lookup"><span data-stu-id="af97c-250">Threads</span></span>

### <a name="example"></a><span data-ttu-id="af97c-251">Пример</span><span class="sxs-lookup"><span data-stu-id="af97c-251">Example</span></span>
```C
status = nx_ptp_client_stop(&ptp_client);

/* If the client was successfully stopped, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_sync_info_get"></a><span data-ttu-id="af97c-252">nx_ptp_client_sync_info_get</span><span class="sxs-lookup"><span data-stu-id="af97c-252">nx_ptp_client_sync_info_get</span></span>

<span data-ttu-id="af97c-253">Получение сведений о синхронизации.</span><span class="sxs-lookup"><span data-stu-id="af97c-253">Get Sync information.</span></span>

### <a name="prototype"></a><span data-ttu-id="af97c-254">Прототип</span><span class="sxs-lookup"><span data-stu-id="af97c-254">Prototype</span></span>

```C
UINT nx_ptp_client_sync_info_get(
    NX_PTP_CLIENT_SYNC *sync_ptr, 
    USHORT *flags, 
    SHORT *utc_offset);
```

### <a name="description"></a><span data-ttu-id="af97c-255">Описание</span><span class="sxs-lookup"><span data-stu-id="af97c-255">Description</span></span>
<span data-ttu-id="af97c-256">Эта служба получает сведения о сообщении синхронизации.</span><span class="sxs-lookup"><span data-stu-id="af97c-256">This service gets information of Sync message.</span></span> <span data-ttu-id="af97c-257">Блок управления синхронизацией передается пользовательскому приложению посредством функции обратного вызова события.</span><span class="sxs-lookup"><span data-stu-id="af97c-257">The Sync control block is passed to user application through event callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="af97c-258">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="af97c-258">Input Parameters</span></span>
* <span data-ttu-id="af97c-259">**client_ptr** — указатель на создаваемый клиент PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-259">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="af97c-260">**flags** — флаги в сообщении синхронизации.</span><span class="sxs-lookup"><span data-stu-id="af97c-260">**flags** Flags in Sync message</span></span>
* <span data-ttu-id="af97c-261">**utc_offset** — смещение между TAI и UTC.</span><span class="sxs-lookup"><span data-stu-id="af97c-261">**utc_offset** Offset between TAI and UTC</span></span>

### <a name="return-values"></a><span data-ttu-id="af97c-262">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="af97c-262">Return Values</span></span>
* <span data-ttu-id="af97c-263">**NX_SUCCESS** (0x00) — сведения о синхронизации успешно получены.</span><span class="sxs-lookup"><span data-stu-id="af97c-263">**NX_SUCCESS** (0x00) Get Sync information successfully</span></span>
* <span data-ttu-id="af97c-264">NX_PTR_ERROR (0x07) — недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="af97c-264">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="af97c-265">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="af97c-265">Allowed From</span></span>
<span data-ttu-id="af97c-266">Потоки</span><span class="sxs-lookup"><span data-stu-id="af97c-266">Threads</span></span>

### <a name="example"></a><span data-ttu-id="af97c-267">Пример</span><span class="sxs-lookup"><span data-stu-id="af97c-267">Example</span></span>
```C
static UINT ptp_event_callback(NX_PTP_CLIENT *ptp_client_ptr, UINT event, VOID *event_data, VOID *callback_data)
{
USHORT utc_offset;

    switch (event)
    {
        case NX_PTP_CLIENT_EVENT_SYNC:
        {
            nx_ptp_client_sync_info_get((NX_PTP_CLIENT_SYNC *)event_data, NX_NULL, &utc_offset);

            /* If the Sync information was successfully get, status = NX_SUCCESS. */
            break;
        }

        /* Other event process. */
    }
}
```

## <a name="nx_ptp_client_time_get"></a><span data-ttu-id="af97c-268">nx_ptp_client_time_get</span><span class="sxs-lookup"><span data-stu-id="af97c-268">nx_ptp_client_time_get</span></span>

<span data-ttu-id="af97c-269">Получение текущего времени.</span><span class="sxs-lookup"><span data-stu-id="af97c-269">Get current time.</span></span>

### <a name="prototype"></a><span data-ttu-id="af97c-270">Прототип</span><span class="sxs-lookup"><span data-stu-id="af97c-270">Prototype</span></span>

```C
UINT nx_ptp_client_time_get(
    NX_PTP_CLIENT *client_ptr, 
    NX_PTP_TIME *time_ptr);
```

### <a name="description"></a><span data-ttu-id="af97c-271">Описание</span><span class="sxs-lookup"><span data-stu-id="af97c-271">Description</span></span>
<span data-ttu-id="af97c-272">Эта служба получает текущее значение тактового генератора PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-272">This service gets the current value of the PTP clock.</span></span> <span data-ttu-id="af97c-273">Она доступна независимо от того, синхронизирован ли клиент PTP с главным тактовым генератором.</span><span class="sxs-lookup"><span data-stu-id="af97c-273">It is available no matter PTP client is synchronized with master clock or not.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="af97c-274">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="af97c-274">Input Parameters</span></span>
* <span data-ttu-id="af97c-275">**client_ptr** — указатель на создаваемый клиент PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-275">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="af97c-276">**time_ptr** — указатель на время PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-276">**time_ptr** Pointer to PTP time</span></span>

### <a name="return-values"></a><span data-ttu-id="af97c-277">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="af97c-277">Return Values</span></span>
* <span data-ttu-id="af97c-278">**NX_SUCCESS** (0x00) — клиент успешно создан.</span><span class="sxs-lookup"><span data-stu-id="af97c-278">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="af97c-279">NX_PTR_ERROR (0x07) — недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="af97c-279">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="af97c-280">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="af97c-280">Allowed From</span></span>
<span data-ttu-id="af97c-281">Потоки</span><span class="sxs-lookup"><span data-stu-id="af97c-281">Threads</span></span>

### <a name="example"></a><span data-ttu-id="af97c-282">Пример</span><span class="sxs-lookup"><span data-stu-id="af97c-282">Example</span></span>
```C
/* Get the PTP clock */
nx_ptp_client_time_get(&ptp_client, &tm);
```

## <a name="nx_ptp_client_time_set"></a><span data-ttu-id="af97c-283">nx_ptp_client_time_set</span><span class="sxs-lookup"><span data-stu-id="af97c-283">nx_ptp_client_time_set</span></span>

<span data-ttu-id="af97c-284">Задание текущего времени.</span><span class="sxs-lookup"><span data-stu-id="af97c-284">Set current time.</span></span>

### <a name="prototype"></a><span data-ttu-id="af97c-285">Прототип</span><span class="sxs-lookup"><span data-stu-id="af97c-285">Prototype</span></span>

```C
UINT nx_ptp_client_time_set(
    NX_PTP_CLIENT *client_ptr, 
    NX_PTP_TIME *time_ptr);
```

### <a name="description"></a><span data-ttu-id="af97c-286">Описание</span><span class="sxs-lookup"><span data-stu-id="af97c-286">Description</span></span>
<span data-ttu-id="af97c-287">Эта служба задает текущее значение тактового генератора PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-287">This service sets the current value of the PTP clock.</span></span> <span data-ttu-id="af97c-288">Она должна быть вызвана до запуска клиента PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-288">It must be invoked before PTP client starts.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="af97c-289">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="af97c-289">Input Parameters</span></span>
* <span data-ttu-id="af97c-290">**client_ptr** — указатель на создаваемый клиент PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-290">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="af97c-291">**time_ptr** — указатель на время PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-291">**time_ptr** Pointer to PTP time</span></span>

### <a name="return-values"></a><span data-ttu-id="af97c-292">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="af97c-292">Return Values</span></span>
* <span data-ttu-id="af97c-293">**NX_SUCCESS** (0x00) — клиент успешно создан.</span><span class="sxs-lookup"><span data-stu-id="af97c-293">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="af97c-294">**NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) — клиент PTP уже запущен.</span><span class="sxs-lookup"><span data-stu-id="af97c-294">**NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) PTP client already started</span></span>
* <span data-ttu-id="af97c-295">NX_PTR_ERROR (0x07) — недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="af97c-295">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="af97c-296">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="af97c-296">Allowed From</span></span>
<span data-ttu-id="af97c-297">Потоки</span><span class="sxs-lookup"><span data-stu-id="af97c-297">Threads</span></span>

### <a name="example"></a><span data-ttu-id="af97c-298">Пример</span><span class="sxs-lookup"><span data-stu-id="af97c-298">Example</span></span>
```C
/* Set current time before PTP client started.  */
status = nx_ptp_client_time_set(&ptp_client, &tm);
```

## <a name="nx_ptp_client_utility_convert_time_to_date"></a><span data-ttu-id="af97c-299">nx_ptp_client_utility_convert_time_to_date</span><span class="sxs-lookup"><span data-stu-id="af97c-299">nx_ptp_client_utility_convert_time_to_date</span></span>

<span data-ttu-id="af97c-300">Преобразование времени PTP в дату и время в формате UTC.</span><span class="sxs-lookup"><span data-stu-id="af97c-300">Convert PTP time to a UTC date and time.</span></span>

### <a name="prototype"></a><span data-ttu-id="af97c-301">Прототип</span><span class="sxs-lookup"><span data-stu-id="af97c-301">Prototype</span></span>

```C
UINT nx_ptp_client_utility_convert_time_to_date(
    NX_PTP_TIME *time_ptr, 
    LONG offset, 
    NX_PTP_DATE_TIME *date_time_ptr);
```

### <a name="description"></a><span data-ttu-id="af97c-302">Описание</span><span class="sxs-lookup"><span data-stu-id="af97c-302">Description</span></span>
<span data-ttu-id="af97c-303">Эта служба преобразует время PTP в дату и время в формате UTC.</span><span class="sxs-lookup"><span data-stu-id="af97c-303">This service converts PTP time to a UTC date and time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="af97c-304">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="af97c-304">Input Parameters</span></span>
* <span data-ttu-id="af97c-305">**time_ptr** — указатель на время PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-305">**time_ptr** Pointer to PTP time</span></span>
* <span data-ttu-id="af97c-306">**offset** — второе смещение со знаком, добавляемое ко времени PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-306">**offset** Signed second offset to add the PTP time</span></span>
* <span data-ttu-id="af97c-307">**date_time_ptr** — указатель на результирующую дату.</span><span class="sxs-lookup"><span data-stu-id="af97c-307">**date_time_ptr** Pointer to resulting date</span></span>

### <a name="return-values"></a><span data-ttu-id="af97c-308">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="af97c-308">Return Values</span></span>
* <span data-ttu-id="af97c-309">**NX_SUCCESS** (0x00) — клиент успешно создан.</span><span class="sxs-lookup"><span data-stu-id="af97c-309">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="af97c-310">**Указатель на результирующую дату** (0xD03) — недопустимый параметр.</span><span class="sxs-lookup"><span data-stu-id="af97c-310">**Pointer to resulting date** (0xD03) Invalid input parameter</span></span>
* <span data-ttu-id="af97c-311">NX_PTR_ERROR (0x07) — недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="af97c-311">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="af97c-312">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="af97c-312">Allowed From</span></span>
<span data-ttu-id="af97c-313">Потоки</span><span class="sxs-lookup"><span data-stu-id="af97c-313">Threads</span></span>

### <a name="example"></a><span data-ttu-id="af97c-314">Пример</span><span class="sxs-lookup"><span data-stu-id="af97c-314">Example</span></span>
```C
/* convert PTP time to UTC date and time */
status = nx_ptp_client_utility_convert_time_to_date(&tm, -ptp_utc_offset, &date);

/* If the time was successfully converted, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_utility_time_diff"></a><span data-ttu-id="af97c-315">nx_ptp_client_utility_time_diff</span><span class="sxs-lookup"><span data-stu-id="af97c-315">nx_ptp_client_utility_time_diff</span></span>

<span data-ttu-id="af97c-316">Разница между двумя значениями времени PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-316">Diff two PTP times.</span></span>

### <a name="prototype"></a><span data-ttu-id="af97c-317">Прототип</span><span class="sxs-lookup"><span data-stu-id="af97c-317">Prototype</span></span>

```C
UINT nx_ptp_client_utility_time_diff(
    NX_PTP_TIME *time1_ptr, 
    NX_PTP_TIME *time2_ptr, 
    NX_PTP_TIME *result_ptr);
```

### <a name="description"></a><span data-ttu-id="af97c-318">Описание</span><span class="sxs-lookup"><span data-stu-id="af97c-318">Description</span></span>
<span data-ttu-id="af97c-319">Эта служба рассчитывает разницу между двумя значениями времени PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-319">This service computes the difference between two PTP times.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="af97c-320">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="af97c-320">Input Parameters</span></span>
* <span data-ttu-id="af97c-321">**time1_ptr** — указатель на первое время PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-321">**time1_ptr** Pointer to first PTP time</span></span>
* <span data-ttu-id="af97c-322">**time2_ptr** — указатель на второе время PTP.</span><span class="sxs-lookup"><span data-stu-id="af97c-322">**time2_ptr** Pointer to second PTP time</span></span>
* <span data-ttu-id="af97c-323">**result_ptr** — указатель на разность первого и второго значений времени.</span><span class="sxs-lookup"><span data-stu-id="af97c-323">**result_ptr** Pointer to result time1-time2</span></span>

### <a name="return-values"></a><span data-ttu-id="af97c-324">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="af97c-324">Return Values</span></span>
* <span data-ttu-id="af97c-325">**NX_SUCCESS** (0x00) — клиент успешно создан.</span><span class="sxs-lookup"><span data-stu-id="af97c-325">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="af97c-326">NX_PTR_ERROR (0x07) — недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="af97c-326">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="af97c-327">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="af97c-327">Allowed From</span></span>
<span data-ttu-id="af97c-328">Потоки</span><span class="sxs-lookup"><span data-stu-id="af97c-328">Threads</span></span>

### <a name="example"></a><span data-ttu-id="af97c-329">Пример</span><span class="sxs-lookup"><span data-stu-id="af97c-329">Example</span></span>
```C
/* Diff time.  */
status = nx_ptp_client_utility_time_diff(&time1, &time2, &result);

/* If the calculation was successfully, status = NX_SUCCESS. */
```