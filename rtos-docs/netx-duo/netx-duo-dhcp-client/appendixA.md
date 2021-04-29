---
title: Приложение A. Описание функции восстановления состояния служб клиента ОСРВ Azure NetX Duo DHCP
description: В этой главе содержится описание функции восстановления состояния для служб клиента ОСРВ Azure NetX Duo DHCP
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 008ca6fb0052339e188e0240cc38a81d3a6b40e8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814816"
---
# <a name="appendix-a--description-of-the-restore-state-feature-for-azure-rtos-netx-duo-dhcp-client-services"></a><span data-ttu-id="d3199-103">Приложение A. Описание функции восстановления состояния клиента ОСРВ Azure NetX Duo DHCP</span><span class="sxs-lookup"><span data-stu-id="d3199-103">Appendix A : Description of the Restore state feature for Azure RTOS NetX Duo DHCP Client services</span></span>

<span data-ttu-id="d3199-104">Параметр конфигурации клиента NetX Duo DHDP NX_DHCP_CLIENT_RESTORE_STATE позволяет системе восстанавливать созданный ранее клиент DHCP в состоянии BOUND после перезагрузки системы.</span><span class="sxs-lookup"><span data-stu-id="d3199-104">The NetX Duo DHDP Client configuration option, NX_DHCP_CLIENT_RESTORE_STATE, allows a system to restore a previously created DHCP Client Record in a Bound state between system reboots.</span></span>

<span data-ttu-id="d3199-105">Если этот параметр включен, приложение может приостановить и возобновить поток DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="d3199-105">When this option is enabled, the application can suspend and resume the DHCP Client thread.</span></span> <span data-ttu-id="d3199-106">Существует также служба для передачи в DHCP-клиент времени, прошедшего между приостановкой и возобновлением потока.</span><span class="sxs-lookup"><span data-stu-id="d3199-106">There is also a service to update the DHCP Client with the elapsed time between suspending and resuming the thread.</span></span>

## <a name="restoring-the-dhcp-client-between-reboots"></a><span data-ttu-id="d3199-107">Восстановление DHCP-клиента после перезагрузки</span><span class="sxs-lookup"><span data-stu-id="d3199-107">Restoring the DHCP Client between Reboots</span></span>

<span data-ttu-id="d3199-108">Восстановление после перезагрузки можно использовать для созданного ранее DHCP-клиента, который должен перейти в состояние BOUND и получить IP-адрес от DHCP-сервера.</span><span class="sxs-lookup"><span data-stu-id="d3199-108">Before restoring a DHCP Client after rebooting, a previously created DHCP Client that must reach the Bound state and be is assigned an IP address from the DHCP server.</span></span> <span data-ttu-id="d3199-109">Прежде чем выключить питание, приложение DHCP должно сохранить текущую запись DHCP-клиента в энергонезависимой памяти.</span><span class="sxs-lookup"><span data-stu-id="d3199-109">Before it powers down, the DHCP application must then save the current DHCP Client record to non-volatile memory.</span></span> <span data-ttu-id="d3199-110">Кроме того, необходим независимый компонент системы, который выполняет роль "хронометра", то есть отслеживает прошедшее время с момента отключения питания.</span><span class="sxs-lookup"><span data-stu-id="d3199-110">There must also be an independent ‘time keeper’ elsewhere in the system to keep track of the time elapsed during this powered down state.</span></span> <span data-ttu-id="d3199-111">После включения питания приложение создает новый экземпляр DHCP-клиента и обновляет его, используя данные из ранее сохраненной записи DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="d3199-111">On powering up, the application creates a new DHCP Client instance, and then updates it with the previously created DHCP Client record.</span></span> <span data-ttu-id="d3199-112">Из "хронометра" поступает информация о прошедшем времени, которое затем вычитается из остатка времени аренды, полученной DHCP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="d3199-112">The elapsed time is obtained from the “time keeper” and then applied to the time remaining on the DHCP Client lease.</span></span> <span data-ttu-id="d3199-113">Обратите внимание на то, что это может привести к изменению состояния DHCP-клиента (например, с BOUND на RENEWING).</span><span class="sxs-lookup"><span data-stu-id="d3199-113">Note that this may cause the DHCP Client to change states e.g. from BOUND to RENEWING.</span></span> <span data-ttu-id="d3199-114">На этом этапе приложение может возобновить работу DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="d3199-114">At this point, the application can resume the DHCP Client.</span></span>

<span data-ttu-id="d3199-115">Если с момента отключения прошло столько времени, что DHCP-клиент переходит в состояние RENEW или REBIND, то он автоматически инициирует обмен сообщениями DHCP для продления или повторной привязки аренды IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d3199-115">If the time elapsed during power down puts the DHCP Client state in either a RENEW or REBIND state, the DHCP Client will automatically initiate DHCP messages requesting to renew or rebind the IP address lease.</span></span> <span data-ttu-id="d3199-116">Если срок действия IP-адреса уже истек, DHCP-клиент автоматически удалит IP-адрес из экземпляра IP и начнет процесс DHCP в состоянии INIT, запросив новый IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="d3199-116">If the IP address is expired, the DHCP Client will automatically clear the IP address on the IP instance and begin the DHCP process from the INIT state, requesting a new IP address.</span></span>

<span data-ttu-id="d3199-117">Это позволяет DHCP-клиенту работать после перезагрузки так, как если бы он не прерывал работу.</span><span class="sxs-lookup"><span data-stu-id="d3199-117">In this manner the DHCP Client can operate between reboots as if uninterrupted.</span></span>

<span data-ttu-id="d3199-118">Ниже приводится иллюстрация этой возможности.</span><span class="sxs-lookup"><span data-stu-id="d3199-118">Below is an illustration of this feature.</span></span> <span data-ttu-id="d3199-119">Предполагается, что DHCP-клиент работает только на основном интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="d3199-119">This assumes DHCP Client is running only on the primary interface.</span></span>

```c
/* On the power up, create an IP instance, DHCP Client, enable ICMP and UDP
   and other resources (not shown) for the DHCP Client/application
   in tx_application_define().  */
 
/* Define the DHCP application thread. */     
void    thread_dhcp_client_entry(ULONG thread_input)
{

UINT        status;
UINT        time_elapsed = 0;
NX_DHCP_CLIENT_RECORD client_nv_record;


if (/* The application checks if there is a previously saved DHCP Client record. */)
{
    /* No previously saved Client record. Start the DHCP Client in the INIT state.  */
    status =  nx_dhcp_start(&dhcp_0);

    if (status !=NX_SUCCESS)
        return;

    do
    {
        /* Wait for DHCP to assign the IP address.  */
    } while (status != NX_SUCCESS);

    /* We have a valid IP address. */
    /* At some point decide we power down the system. */
    /* Save the Client state data which we will subsequently need to restore the DHCP    
       Client. */
    status = nx_dhcp_client_get_record(&dhcp_0, &client_nv_record);               

    /* Copy this memory to non-volatile memory (not shown). */
    /* Delete the IP and DHCP Client instances before powering down. */
    nx_dhcp_delete(&dhcp_0);

    nx_ip_delete(&ip_0);
    /* Ready to power down, having released other resources as necessary. */

}
else
{

    /* The application has determined there is a previously saved record. We will 
        restore it to the current DHCP Client instance.  */

    /* Get the previous Client state data from non-volatile memory. */

    /* Apply the record to the current Client instance. This will also 
        update the IP instance with IP address, mask etc. */
    status = nx_dhcp_client_restore_record(&dhcp_0, &client_nv_record, time_elapsed);   

    if (status != NX_SUCCESS)
        return;

    /* We are ready to resume the DHCP Client thread and use the assigned IP address. */
    status = nx_dhcp_resume(&dhcp_0);

    if (status != NX_SUCCESS)
        return;

}
```
## <a name="resuming-the-dhcp-client-thread-after-suspension"></a><span data-ttu-id="d3199-120">Возобновление потока DHCP-клиента после приостановки</span><span class="sxs-lookup"><span data-stu-id="d3199-120">Resuming the DHCP Client Thread after Suspension</span></span> 

<span data-ttu-id="d3199-121">Чтобы приостановить поток DHCP-клиента без выключения питания, приложение вызывает *nx_dhcp_suspend* для DHCP-клиента, который перешел в состояние BOUND и имеет допустимый IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="d3199-121">To suspend a DHCP Client thread without powering down, the application calls *nx_dhcp_suspend* on a DHCP Client which has achieved the BOUND state and which has a valid IP address.</span></span> <span data-ttu-id="d3199-122">Когда приложение готово возобновить работу DHCP-клиента, оно сначала вызывает службу *nx_dhcp_client_update_time_remaining*, чтобы обновить оставшееся время аренды DHCP-адреса (получив значение истекшего времени из независимого хронометра).</span><span class="sxs-lookup"><span data-stu-id="d3199-122">When it is ready to resume the DHCP Client it first calls *nx_dhcp_client_update_time_remaining* to update the time remaining on the DHCP address lease (obtaining the time elapsed from an independent time keeper).</span></span> <span data-ttu-id="d3199-123">Затем оно вызывает службу *nx_dhcp_resume* для возобновления потока DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="d3199-123">Then it calls the *nx_dhcp_resume* to resume the DHCP Client thread.</span></span>

<span data-ttu-id="d3199-124">Если прошло столько времени, что DHCP-клиент переходит в состояние RENEW или REBIND, то он автоматически инициирует обмен сообщениями DHCP для продления или повторной привязки аренды IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d3199-124">If the time elapsed puts the DHCP Client state in either a RENEW or REBIND state, the DHCP Client will automatically initiate DHCP messages requesting to renew or rebind the IP address lease.</span></span> <span data-ttu-id="d3199-125">Если срок действия IP-адреса уже истек, DHCP-клиент автоматически удалит IP-адрес и начнет процесс DHCP в состоянии INIT, запросив новый IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="d3199-125">If the IP address is expired, the DHCP Client will automatically clear the IP address and begin the DHCP process from the INIT state, requesting a new IP address.</span></span>

<span data-ttu-id="d3199-126">Ниже демонстрируется использование этой возможности.</span><span class="sxs-lookup"><span data-stu-id="d3199-126">Below is an illustration of using this feature.</span></span>

```c
/* Create an IP instance, DHCP Client, enable ICMP and UDP
   and other resources (not shown) typically in tx_application_define().  */
 
/* Define the DHCP application thread. */     
void    thread_dhcp_client_entry(ULONG thread_input)
{

  /* Start the DHCP Client.  */
  status =  nx_dhcp_start(&dhcp_0);

  if (status !=NX_SUCCESS)
    return;

  while(1)
  {
   /* Wait for DHCP to obtain an IP address.  */
  }

  /* Do tasks with the IP address e.g. send pings to another host on the network...  */
  status =  nx_icmp_ping(…);

  if (status !=NX_SUCCESS)
          printf("Failed %d byte Ping!\n", length);

  /* At some later time, suspend the DHCP Client e.g. the device is going to low 
   power mode (sleep) so we do not want any threads to wake it up. */

  nx_dhcp_suspend(&dhcp_0);  

  /* During this suspended state, an independent timer is keeping track of the elapsed      
     time. */


  /* At some point, we are ready to resume the DHCP Client thread. */

  /* Update the DHCP Client lease time remaining with the time elapsed. */
  status = nx_dhcp_client_update_time_remaining(&dhcp_0, time_elapsed);   

  if (status != NX_SUCCESS)
       return;

  /* We now can resume the DHCP Client thread. */
  status = nx_dhcp_resume(&dhcp_0);

  if (status != NX_SUCCESS)
       return;

  /* Resume tasks e.g. ping another host. */
  status =  nx_icmp_ping(…);

}

```
<span data-ttu-id="d3199-127">Ниже приведен список служб для восстановления состояния DHCP-клиента из памяти, а также для приостановки и возобновления работы DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="d3199-127">Below is a list of services for restoring a DHCP Client state from memory and for suspending and resuming the DHCP Client.</span></span>

## <a name="nx_dhcp_client_get_record"></a><span data-ttu-id="d3199-128">nx_dhcp_client_get_record</span><span class="sxs-lookup"><span data-stu-id="d3199-128">nx_dhcp_client_get_record</span></span>

<span data-ttu-id="d3199-129">Создание записи текущего состояния DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="d3199-129">Create a record of the current DHCP Client state</span></span>

### <a name="prototype"></a><span data-ttu-id="d3199-130">Прототип</span><span class="sxs-lookup"><span data-stu-id="d3199-130">Prototype</span></span>

```c
ULONG nx_dhcp_ client_get_record(NX_DHCP *dhcp_ptr, NX_DHCP_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a><span data-ttu-id="d3199-131">Описание</span><span class="sxs-lookup"><span data-stu-id="d3199-131">Description</span></span>

<span data-ttu-id="d3199-132">Эта служба сохраняет DHCP-клиент, работающий на первом интерфейсе с поддержкой DHCP, найденном в экземпляре DHCP-клиента, в записи, на которую указывает record_ptr.</span><span class="sxs-lookup"><span data-stu-id="d3199-132">This service saves the DHCP Client running on the first interface enabled for DHCP found on the DHCP Client instance to the record pointed to by record_ptr.</span></span> <span data-ttu-id="d3199-133">Это позволяет приложению DHCP-клиента восстановить состояние DHCP-клиента, например, после отключения питания и перезагрузки компьютера.</span><span class="sxs-lookup"><span data-stu-id="d3199-133">This allows the DHCP Client application restore its DHCP Client state after, for example, a power down and reboot.</span></span>

<span data-ttu-id="d3199-134">Чтобы сохранить запись DHCP-клиента на определенном интерфейсе, если для DHCP включено более одного интерфейса, используйте службу *nx_dhcp_interface_client_get_record*.</span><span class="sxs-lookup"><span data-stu-id="d3199-134">To save a DHCP Client record on a specific interface if more than one interface is enabled for DHCP, use the *nx_dhcp_interface_client_get_record* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d3199-135">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="d3199-135">Input Parameters</span></span>

- <span data-ttu-id="d3199-136">**dhcp_ptr**: указатель на DHCP-клиент.</span><span class="sxs-lookup"><span data-stu-id="d3199-136">**dhcp_ptr**: Pointer to DHCP Client</span></span>
- <span data-ttu-id="d3199-137">**record_ptr**: указатель на запись DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="d3199-137">**record_ptr**: Pointer to DHCP Client record</span></span>

### <a name="return-values"></a><span data-ttu-id="d3199-138">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d3199-138">Return Values</span></span>

- <span data-ttu-id="d3199-139">**NX_SUCCESS (0x0)** : запись клиента успешно создана.</span><span class="sxs-lookup"><span data-stu-id="d3199-139">**NX_SUCCESS (0x0)**: Client record created</span></span>
- <span data-ttu-id="d3199-140">**NX_DHCP_NOT_BOUND** (0x94): клиент не находится в состоянии BOUND.</span><span class="sxs-lookup"><span data-stu-id="d3199-140">**NX_DHCP_NOT_BOUND**: (0x94) Client not in Bound states</span></span>
- <span data-ttu-id="d3199-141">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5): протокол DHCP не включен ни для одного интерфейса.</span><span class="sxs-lookup"><span data-stu-id="d3199-141">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces enabled for DHCP</span></span>
- <span data-ttu-id="d3199-142">NX_PTR_ERROR (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="d3199-142">NX_PTR_ERROR: (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d3199-143">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d3199-143">Allowed From</span></span>

<span data-ttu-id="d3199-144">Потоки</span><span class="sxs-lookup"><span data-stu-id="d3199-144">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d3199-145">Например, .</span><span class="sxs-lookup"><span data-stu-id="d3199-145">Example</span></span>

```c
NX_DHCP_CLIENT_RECORD dhcp_record;

/* Obtain a record of the current client state. */
status=  nx_dhcp_client_get_record(dhcp_ptr, &dhcp_record);

/* If status is NX_SUCCESS dhcp_record contains the current DHCP client record. */
```

## <a name="nx_dhcp_interface_client_get_record"></a><span data-ttu-id="d3199-146">nx_dhcp_interface_client_get_record</span><span class="sxs-lookup"><span data-stu-id="d3199-146">nx_dhcp_interface_client_get_record</span></span>

<span data-ttu-id="d3199-147">Создание записи текущего состояния DHCP-клиента на указанном интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="d3199-147">Create a record of the current DHCP Client state on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="d3199-148">Прототип</span><span class="sxs-lookup"><span data-stu-id="d3199-148">Prototype</span></span>

```c
ULONG nx_dhcp_interface_client_get_record(NX_DHCP *dhcp_ptr, UINT interface_index,
                                          NX_DHCP_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a><span data-ttu-id="d3199-149">Описание</span><span class="sxs-lookup"><span data-stu-id="d3199-149">Description</span></span>

<span data-ttu-id="d3199-150">Эта служба сохраняет состояние DHCP-клиента, работающего на указанном интерфейсе, в записи, на которую указывает record_ptr.</span><span class="sxs-lookup"><span data-stu-id="d3199-150">This service saves the DHCP Client running on the specified interface to the record pointed to by record_ptr.</span></span> <span data-ttu-id="d3199-151">Это позволяет приложению DHCP-клиента восстановить состояние DHCP-клиента, например, после отключения питания и перезагрузки компьютера.</span><span class="sxs-lookup"><span data-stu-id="d3199-151">This allows the DHCP Client application restore its DHCP Client state after, for example, a power down and reboot.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d3199-152">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="d3199-152">Input Parameters</span></span>

- <span data-ttu-id="d3199-153">**dhcp_ptr**: указатель на DHCP-клиент.</span><span class="sxs-lookup"><span data-stu-id="d3199-153">**dhcp_ptr**: Pointer to DHCP Client</span></span>
- <span data-ttu-id="d3199-154">**interface_index**: индекс, по которому нужно получить запись.</span><span class="sxs-lookup"><span data-stu-id="d3199-154">**interface_index**: Index on which to get record</span></span>
- <span data-ttu-id="d3199-155">**record_ptr**: указатель на запись DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="d3199-155">**record_ptr**: Pointer to DHCP Client record</span></span>

### <a name="return-values"></a><span data-ttu-id="d3199-156">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d3199-156">Return Values</span></span>

- <span data-ttu-id="d3199-157">**NX_SUCCESS (0x0)** : запись клиента успешно создана.</span><span class="sxs-lookup"><span data-stu-id="d3199-157">**NX_SUCCESS (0x0)**: Client record created</span></span>
- <span data-ttu-id="d3199-158">**NX_DHCP_NOT_BOUND** (0x94): **клиент не находится в состоянии BOUND.**</span><span class="sxs-lookup"><span data-stu-id="d3199-158">**NX_DHCP_NOT_BOUND**: (0x94) **Client not in Bound state**</span></span>
- <span data-ttu-id="d3199-159">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR** (0x9A): недопустимый индекс интерфейса.</span><span class="sxs-lookup"><span data-stu-id="d3199-159">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR**: (0x9A) Invalid interface index</span></span>
- <span data-ttu-id="d3199-160">NX_PTR_ERROR (0x16): недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="d3199-160">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="d3199-161">NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="d3199-161">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d3199-162">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d3199-162">Allowed From</span></span>

<span data-ttu-id="d3199-163">Потоки</span><span class="sxs-lookup"><span data-stu-id="d3199-163">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d3199-164">Например, .</span><span class="sxs-lookup"><span data-stu-id="d3199-164">Example</span></span>

```c
NX_DHCP_CLIENT_RECORD dhcp_record;
/* Obtain a record of the current client state on interface 1. */
status=  nx_dhcp_interface_client_get_record(dhcp_ptr, 1, &dhcp_record);

/* If status is NX_SUCCESS dhcp_record contains the current DHCP client record. */
```

## <a name="nx_dhcp_-client_restore_record"></a><span data-ttu-id="d3199-165">nx_dhcp_ client_restore_record</span><span class="sxs-lookup"><span data-stu-id="d3199-165">nx_dhcp_ client_restore_record</span></span>

<span data-ttu-id="d3199-166">Восстановление DHCP-клиента из сохраненной ранее записи.</span><span class="sxs-lookup"><span data-stu-id="d3199-166">Restore DHCP Client from a previously saved record</span></span>

### <a name="prototype"></a><span data-ttu-id="d3199-167">Прототип</span><span class="sxs-lookup"><span data-stu-id="d3199-167">Prototype</span></span>

```c
ULONG nx_dhcp_client_restore_record(NX_DHCP *dhcp_ptr, 
                                    NX_DHCP_CLIENT_RECORD *record_ptr, 
                                    ULONG time_elapsed);

```

### <a name="description"></a><span data-ttu-id="d3199-168">Описание</span><span class="sxs-lookup"><span data-stu-id="d3199-168">Description</span></span>

<span data-ttu-id="d3199-169">Эта служба позволяет приложению восстановить DHCP-клиент из предыдущего сеанса, используя запись DHCP-клиента, на которую указывает record_ptr.</span><span class="sxs-lookup"><span data-stu-id="d3199-169">This service enables an application to restore its DHCP Client from a previous session using the DHCP Client record pointed to by record_ptr.</span></span> <span data-ttu-id="d3199-170">Входное значение time_elapsed применяется к оставшемуся времени аренды DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="d3199-170">The time_elapsed input is applied to the time remaining on DHCP Client lease.</span></span>

<span data-ttu-id="d3199-171">Для этого нужно, чтобы приложение DHCP-клиента создало запись DHCP-клиента перед отключением питания и сохранило эту запись в энергонезависимой памяти.</span><span class="sxs-lookup"><span data-stu-id="d3199-171">This requires that the DHCP Client application created a record of the DHCP Client before powering down, and saved that record to nonvolatile memory.</span></span>

<span data-ttu-id="d3199-172">Если для DHCP-клиента включено более одного интерфейса, эта служба применяется к первому допустимому интерфейсу, обнаруженному в экземпляре DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="d3199-172">If more than one interface is enabled for DHCP Client, this service is applied to the first valid interface found in the DHCP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d3199-173">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="d3199-173">Input Parameters</span></span>

- <span data-ttu-id="d3199-174">**dhcp_ptr**: указатель на DHCP-клиент.</span><span class="sxs-lookup"><span data-stu-id="d3199-174">**dhcp_ptr**: Pointer to DHCP Client</span></span>
- <span data-ttu-id="d3199-175">**record_ptr**: указатель на запись DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="d3199-175">**record_ptr**: Pointer to DHCP Client record</span></span> 
- <span data-ttu-id="d3199-176">**time_elapsed**: время, которое нужно вычесть из остатка времени аренды в предоставленной записи клиента.</span><span class="sxs-lookup"><span data-stu-id="d3199-176">**time_elapsed**: Time to subtract from the lease time remaining in the input client record</span></span>

### <a name="return-values"></a><span data-ttu-id="d3199-177">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d3199-177">Return Values</span></span>

- <span data-ttu-id="d3199-178">**NX_SUCCESS (0x0)** : запись клиента успешно восстановлена.</span><span class="sxs-lookup"><span data-stu-id="d3199-178">**NX_SUCCESS**: (0x0) Client record restored</span></span>
- <span data-ttu-id="d3199-179">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5): отсутствуют интерфейсы, использующие протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="d3199-179">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces running DHCP</span></span>
- <span data-ttu-id="d3199-180">NX_PTR_ERROR (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="d3199-180">NX_PTR_ERROR: (0x16) Invalid pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d3199-181">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d3199-181">Allowed From</span></span>

<span data-ttu-id="d3199-182">Потоки</span><span class="sxs-lookup"><span data-stu-id="d3199-182">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d3199-183">Например, .</span><span class="sxs-lookup"><span data-stu-id="d3199-183">Example</span></span>

```c
NX_DHCP_CLIENT_RECORD dhcp_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
Time_elapsed = /* to be determined by application */ 1000; 

/* Obtain a record of the current client state. */
status=  nx_dhcp_client_restore_record(client_ptr, &dhcp_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCP Client pointed to by dhcp_ptr  contains the current client record updated for time elapsed during power down. */
```

## <a name="nx_dhcp_interace_client_restore_record"></a><span data-ttu-id="d3199-184">nx_dhcp_interace_client_restore_record</span><span class="sxs-lookup"><span data-stu-id="d3199-184">nx_dhcp_interace_client_restore_record</span></span>

<span data-ttu-id="d3199-185">Восстановление DHCP-клиента из сохраненной ранее записи на указанном интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="d3199-185">Restore DHCP Client from a previously saved record on specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="d3199-186">Прототип</span><span class="sxs-lookup"><span data-stu-id="d3199-186">Prototype</span></span>

```c
ULONG nx_dhcp_interface_client_restore_record(NX_DHCP *dhcp_ptr, 
                                              NX_DHCP_CLIENT_RECORD *record_ptr, 
                                              ULONG time_elapsed);
```

### <a name="description"></a><span data-ttu-id="d3199-187">Описание</span><span class="sxs-lookup"><span data-stu-id="d3199-187">Description</span></span>

<span data-ttu-id="d3199-188">Эта служба позволяет приложению восстановить DHCP-клиент на указанном интерфейсе, используя запись DHCP-клиента, на которую указывает record_ptr.</span><span class="sxs-lookup"><span data-stu-id="d3199-188">This service enables an application to restore its DHCP Client on the specified interface using the DHCP Client record pointed to by record_ptr.</span></span> <span data-ttu-id="d3199-189">Входное значение time_elapsed применяется к оставшемуся времени аренды DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="d3199-189">The time_elapsed input is applied to the time remaining on DHCP Client lease.</span></span>

<span data-ttu-id="d3199-190">Для этого нужно, чтобы приложение DHCP-клиента создало запись DHCP-клиента перед отключением питания и сохранило эту запись в энергонезависимой памяти.</span><span class="sxs-lookup"><span data-stu-id="d3199-190">This requires that the DHCP Client application created a record of the DHCP Client before powering down, and saved that record to nonvolatile memory.</span></span>

<span data-ttu-id="d3199-191">Если для DHCP-клиента включено более одного интерфейса, эта служба применяется к первому допустимому интерфейсу, обнаруженному в экземпляре DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="d3199-191">If more than one interface is enabled for DHCP Client, this service is applied to the first valid interface found in the DHCP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d3199-192">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="d3199-192">Input Parameters</span></span>

- <span data-ttu-id="d3199-193">**dhcp_ptr**: указатель на DHCP-клиент.</span><span class="sxs-lookup"><span data-stu-id="d3199-193">**dhcp_ptr**: Pointer to DHCP Client</span></span>
- <span data-ttu-id="d3199-194">**record_ptr**: указатель на запись DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="d3199-194">**record_ptr**: Pointer to DHCP Client record</span></span> 
- <span data-ttu-id="d3199-195">**time_elapsed**: время, которое нужно вычесть из остатка времени аренды в предоставленной записи клиента.</span><span class="sxs-lookup"><span data-stu-id="d3199-195">**time_elapsed**: Time to subtract from the lease time remaining in the input client record</span></span>

### <a name="return-values"></a><span data-ttu-id="d3199-196">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d3199-196">Return Values</span></span>

- <span data-ttu-id="d3199-197">**NX_SUCCESS (0x0)** : запись клиента успешно восстановлена.</span><span class="sxs-lookup"><span data-stu-id="d3199-197">**NX_SUCCESS**: (0x0) Client record restored</span></span>
- <span data-ttu-id="d3199-198">**NX_DHCP_NOT_BOUND** (0x94): клиент не привязан к IP-адресу.</span><span class="sxs-lookup"><span data-stu-id="d3199-198">**NX_DHCP_NOT_BOUND**: (0x94) Client not bound to IP address</span></span>
- <span data-ttu-id="d3199-199">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR** (0x9A): недопустимый индекс интерфейса.</span><span class="sxs-lookup"><span data-stu-id="d3199-199">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR**: (0x9A) Invalid interface index</span></span>
- <span data-ttu-id="d3199-200">NX_PTR_ERROR (0x16): недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="d3199-200">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="d3199-201">NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="d3199-201">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d3199-202">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d3199-202">Allowed From</span></span>

<span data-ttu-id="d3199-203">Потоки</span><span class="sxs-lookup"><span data-stu-id="d3199-203">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d3199-204">Например, .</span><span class="sxs-lookup"><span data-stu-id="d3199-204">Example</span></span>

```c
NX_DHCP_CLIENT_RECORD dhcp_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
Time_elapsed = /* to be determined by application */ 1000; 


/* Obtain a record of the current client state on the primary interface. */
status=  nx_dhcp_interface_client_restore_record(client_ptr, 0, &dhcp_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCP Client pointed to by dhcp_ptr  contains the current client record updated for time elapsed during power down. */
```

## <a name="nx_dhcp_-client_update_time_remaining"></a><span data-ttu-id="d3199-205">nx_dhcp_ client_update_time_remaining</span><span class="sxs-lookup"><span data-stu-id="d3199-205">nx_dhcp_ client_update_time_remaining</span></span>

<span data-ttu-id="d3199-206">Обновление оставшегося времени аренды DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="d3199-206">Update the time remaining on DHCP Client lease</span></span>

### <a name="prototype"></a><span data-ttu-id="d3199-207">Прототип</span><span class="sxs-lookup"><span data-stu-id="d3199-207">Prototype</span></span>

```c
ULONG nx_dhcp_client_update_time_remaining(NX_DHCP *dhcp_ptr, ULONG time_elapsed);
```

### <a name="description"></a><span data-ttu-id="d3199-208">Описание</span><span class="sxs-lookup"><span data-stu-id="d3199-208">Description</span></span>

<span data-ttu-id="d3199-209">Эта служба обновляет оставшееся время аренды IP-адреса DHCP-клиентом с учетом входного значения time_elapsed на первом интерфейсе с поддержкой протокола DHCP, найденном в экземпляре DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="d3199-209">This service updates the time remaining on the DHCP Client IP address lease with the time_elapsed input on the first interface enabled for DHCP found on the DHCP Client instance.</span></span> <span data-ttu-id="d3199-210">Приложение должно приостановить поток DHCP-клиента перед использованием этой службы с помощью *nx_dhcp_suspend*.</span><span class="sxs-lookup"><span data-stu-id="d3199-210">The application must suspend the DHCP Client thread before using this service using *nx_dhcp_suspend*.</span></span> <span data-ttu-id="d3199-211">После вызова этой службы приложение может возобновить поток DHCP-клиента, вызвав *nx_dhcp_resume*.</span><span class="sxs-lookup"><span data-stu-id="d3199-211">After calling this service, the application can resume the DHCP Client thread by calling *nx_dhcp_resume*.</span></span>

<span data-ttu-id="d3199-212">Эта служба предназначена для приложений DHCP-клиента, которым необходимо приостановить поток DHCP-клиента на определенный период времени, а затем обновить оставшееся время аренды IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d3199-212">This is intended for DHCP Client applications that need to suspend the DHCP Client thread for a period of time, and then update the IP address lease time remaining.</span></span>

<span data-ttu-id="d3199-213">Примечание. Она не предназначена для использования со службами *nx_dhcp_client_get_record* и *nx_dhcp_client_restore_record*, описанными выше.</span><span class="sxs-lookup"><span data-stu-id="d3199-213">Note: This service is not intended to be used with *nx_dhcp_client_get_record* and *nx_dhcp_client_restore_record* described previously).</span></span> <span data-ttu-id="d3199-214">Эти службы были рассмотрены ранее в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="d3199-214">These services are previously described in this section.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d3199-215">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="d3199-215">Input Parameters</span></span>

- <span data-ttu-id="d3199-216">**dhcp_ptr**: указатель на DHCP-клиент.</span><span class="sxs-lookup"><span data-stu-id="d3199-216">**dhcp_ptr**: Pointer to DHCP Client</span></span> 
- <span data-ttu-id="d3199-217">**time_elapsed**: время, вычитаемое из оставшегося времени аренды IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d3199-217">**time_elapsed**: Time to subtract from the time remaining on the IP address lease</span></span>

### <a name="return-values"></a><span data-ttu-id="d3199-218">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d3199-218">Return Values</span></span>

- <span data-ttu-id="d3199-219">**NX_SUCCESS** (0x0): аренда IP-адреса клиентом успешно обновлена.</span><span class="sxs-lookup"><span data-stu-id="d3199-219">**NX_SUCCESS**: (0x0) Client IP lease updated</span></span>
- <span data-ttu-id="d3199-220">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5): протокол DHCP не включен ни для одного интерфейса.</span><span class="sxs-lookup"><span data-stu-id="d3199-220">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces enabled for DHCP</span></span>
- <span data-ttu-id="d3199-221">NX_PTR_ERROR (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="d3199-221">NX_PTR_ERROR: (0x16) Invalid Pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d3199-222">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d3199-222">Allowed From</span></span>

<span data-ttu-id="d3199-223">Потоки</span><span class="sxs-lookup"><span data-stu-id="d3199-223">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d3199-224">Например, .</span><span class="sxs-lookup"><span data-stu-id="d3199-224">Example</span></span>

```c
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 


/* Apply the elapsed time to the DHCP Client address lease. */
status=  nx_dhcp_client_update_time_remaining(client_ptr, time_elapsed);

/* If status is NX_SUCCESS the DHCP Client is updated for time elapsed. */
```

## <a name="nx_dhcp_interface_client_update_time_remaining"></a><span data-ttu-id="d3199-225">nx_dhcp_interface_client_update_time_remaining</span><span class="sxs-lookup"><span data-stu-id="d3199-225">nx_dhcp_interface_client_update_time_remaining</span></span>

<span data-ttu-id="d3199-226">Обновление оставшегося времени аренды DHCP-клиента на указанном интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="d3199-226">Update the time remaining on DHCP Client lease on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="d3199-227">Прототип</span><span class="sxs-lookup"><span data-stu-id="d3199-227">Prototype</span></span>

```c
ULONG nx_dhcp_interface_client_update_time_remaining(NX_DHCP *dhcp_ptr,
                                                     UINT interface_index,
                                                     ULONG time_elapsed);
```

### <a name="description"></a><span data-ttu-id="d3199-228">Описание</span><span class="sxs-lookup"><span data-stu-id="d3199-228">Description</span></span>

<span data-ttu-id="d3199-229">Эта служба обновляет оставшееся время аренды IP-адреса DHCP-клиентом с учетом входного значения time_elapsed на указанном интерфейсе с поддержкой протокола DHCP.</span><span class="sxs-lookup"><span data-stu-id="d3199-229">This service updates the time remaining on the DHCP Client IP address lease with the time_elapsed input on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="d3199-230">Приложение должно приостановить поток DHCP-клиента перед использованием этой службы с помощью *nx_dhcp_suspend*.</span><span class="sxs-lookup"><span data-stu-id="d3199-230">The application must suspend the DHCP Client thread before using this service using *nx_dhcp_suspend*.</span></span> <span data-ttu-id="d3199-231">После вызова этой службы приложение может возобновить поток DHCP-клиента, вызвав *nx_dhcp_resume*.</span><span class="sxs-lookup"><span data-stu-id="d3199-231">After calling this service, the application can resume the DHCP Client thread by calling *nx_dhcp_resume*.</span></span> <span data-ttu-id="d3199-232">Обратите внимание на то, что приостановка и возобновление потока DHCP-клиента применяется ко всем интерфейсам, для которых включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="d3199-232">Note suspending and resuming the DHCP Client thread applies to all interfaces enabled for DHCP.</span></span>

<span data-ttu-id="d3199-233">Эта служба предназначена для приложений DHCP-клиента, которым необходимо приостановить поток DHCP-клиента на определенный период времени, а затем обновить оставшееся время аренды IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d3199-233">This is intended for DHCP Client applications that need to suspend the DHCP Client thread for a period of time, and then update the IP address lease time remaining.</span></span>

<span data-ttu-id="d3199-234">Примечание. Она не предназначена для использования со службами *nx_dhcp_client_get_record* и *nx_dhcp_client_restore_record*, описанными выше.</span><span class="sxs-lookup"><span data-stu-id="d3199-234">Note: This service is not intended to be used with *nx_dhcp_client_get_record* and *nx_dhcp_client_restore_record* described previously).</span></span> <span data-ttu-id="d3199-235">Эти службы были рассмотрены ранее в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="d3199-235">These services are previously described in this section.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d3199-236">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="d3199-236">Input Parameters</span></span>

- <span data-ttu-id="d3199-237">**dhcp_ptr**: указатель на DHCP-клиент.</span><span class="sxs-lookup"><span data-stu-id="d3199-237">**dhcp_ptr**: Pointer to DHCP Client</span></span>
- <span data-ttu-id="d3199-238">**interface_index**: индекс интерфейса, для которого необходимо учесть истекшее время.</span><span class="sxs-lookup"><span data-stu-id="d3199-238">**interface_index**: Index to interface to apply elapsed time to</span></span>
- <span data-ttu-id="d3199-239">**time_elapsed**: время, вычитаемое из оставшегося времени аренды IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d3199-239">**time_elapsed**: Time to subtract from the time remaining on the IP address lease</span></span>

### <a name="return-values"></a><span data-ttu-id="d3199-240">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d3199-240">Return Values</span></span>

- <span data-ttu-id="d3199-241">**NX_SUCCESS** (0x0): аренда IP-адреса клиентом успешно обновлена.</span><span class="sxs-lookup"><span data-stu-id="d3199-241">**NX_SUCCESS**: (0x0) Client IP lease updated</span></span>
- <span data-ttu-id="d3199-242">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR** (0x9A): недопустимый индекс интерфейса.</span><span class="sxs-lookup"><span data-stu-id="d3199-242">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR**: (0x9A) Invalid interface index</span></span>
- <span data-ttu-id="d3199-243">NX_PTR_ERROR (0x16): недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="d3199-243">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="d3199-244">NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="d3199-244">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d3199-245">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d3199-245">Allowed From</span></span>

<span data-ttu-id="d3199-246">Потоки</span><span class="sxs-lookup"><span data-stu-id="d3199-246">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d3199-247">Например, .</span><span class="sxs-lookup"><span data-stu-id="d3199-247">Example</span></span>

```c
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 


/* Apply the elapsed time to the DHCP Client address lease on interface 1. */
status=  nx_dhcp_interface_client_update_time_remaining(client_ptr, 1, time_elapsed);

/* If status is NX_SUCCESS the DHCP Client is updated for time elapsed. */

```

## <a name="nx_dhcp_suspend"></a><span data-ttu-id="d3199-248">nx_dhcp_suspend</span><span class="sxs-lookup"><span data-stu-id="d3199-248">nx_dhcp_suspend</span></span>

<span data-ttu-id="d3199-249">Приостановка потока DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="d3199-249">Suspend the DHCP Client thread</span></span>

### <a name="prototype"></a><span data-ttu-id="d3199-250">Прототип</span><span class="sxs-lookup"><span data-stu-id="d3199-250">Prototype</span></span>

```c
ULONG nx_dhcp_suspend(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="d3199-251">Описание</span><span class="sxs-lookup"><span data-stu-id="d3199-251">Description</span></span>

<span data-ttu-id="d3199-252">Эта служба приостанавливает текущий поток DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="d3199-252">This service suspends the current DHCP Client thread.</span></span> <span data-ttu-id="d3199-253">Обратите внимание на то, что, в отличие от *nx_dhcp_stop*, при вызове этой службы не происходит никаких изменений в состоянии DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="d3199-253">Note that unlike *nx_dhcp_stop*, there is no change to the DHCP Client state when this service is called.</span></span>

<span data-ttu-id="d3199-254">Эта служба приостанавливает работу протокола DHCP на всех интерфейсах, для которых включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="d3199-254">This service suspends DHCP running on all interfaces enabled for DHCP.</span></span>

<span data-ttu-id="d3199-255">Чтобы узнать, как обновить состояние DHCP-клиента с учетом времени, в течение которого этот DHCP-клиент был приостановлен, ознакомьтесь со службой *nx_dhcp_client_update_time_remaining*, описанной выше.</span><span class="sxs-lookup"><span data-stu-id="d3199-255">To update the DHCP Client state with elapsed time while the DHCP Client is suspended, see the *nx_dhcp_client_update_time_remaining* described previously.</span></span> <span data-ttu-id="d3199-256">Чтобы возобновить приостановленный поток DHCP-клиента, приложение должно вызвать службу *nx_dhcp_resume*.</span><span class="sxs-lookup"><span data-stu-id="d3199-256">To resume a suspended DHCP Client thread, the application should call *nx_dhcp_resume*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d3199-257">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="d3199-257">Input Parameters</span></span>

- <span data-ttu-id="d3199-258">**dhcp_ptr**: указатель на DHCP-клиент.</span><span class="sxs-lookup"><span data-stu-id="d3199-258">**dhcp_ptr**: Pointer to DHCP Client</span></span>

### <a name="return-values"></a><span data-ttu-id="d3199-259">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d3199-259">Return Values</span></span>

- <span data-ttu-id="d3199-260">**NX_SUCCESS** (0x0): поток клиента приостановлен.</span><span class="sxs-lookup"><span data-stu-id="d3199-260">**NX_SUCCESS**: (0x0) Client thread is suspended</span></span>
- <span data-ttu-id="d3199-261">NX_PTR_ERROR (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="d3199-261">NX_PTR_ERROR: (0x16) Invalid pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d3199-262">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d3199-262">Allowed From</span></span>

<span data-ttu-id="d3199-263">Потоки</span><span class="sxs-lookup"><span data-stu-id="d3199-263">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d3199-264">Например, .</span><span class="sxs-lookup"><span data-stu-id="d3199-264">Example</span></span>

```c
/* Pause the DHCP client thread. */
status=  nx_dhcp_suspend(client_ptr);

/* If status is NX_SUCCESS the current DHCP Client thread is paused. */
```

## <a name="nx_dhcp_resume"></a><span data-ttu-id="d3199-265">nx_dhcp_resume</span><span class="sxs-lookup"><span data-stu-id="d3199-265">nx_dhcp_resume</span></span>

<span data-ttu-id="d3199-266">Возобновление приостановленного потока DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="d3199-266">Resume a suspended DHCP Client thread</span></span>

### <a name="prototype"></a><span data-ttu-id="d3199-267">Прототип</span><span class="sxs-lookup"><span data-stu-id="d3199-267">Prototype</span></span>

```c
ULONG nx_dhcp_resume(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="d3199-268">Описание</span><span class="sxs-lookup"><span data-stu-id="d3199-268">Description</span></span>

<span data-ttu-id="d3199-269">Эта служба возобновляет приостановленный поток DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="d3199-269">This service resumes a suspended DHCP Client thread.</span></span> <span data-ttu-id="d3199-270">Обратите внимание на то, что после возобновления потока клиента фактическое состояние DHCP-клиента не изменяется.</span><span class="sxs-lookup"><span data-stu-id="d3199-270">Note that there is no change to the actual DHCP Client state after resuming the Client thread.</span></span> <span data-ttu-id="d3199-271">Чтобы узнать, как обновить оставшееся время аренды IP-адреса DHCP-клиентом с учетом прошедшего времени перед вызовом службы *nx_dhcp_resume*, ознакомьтесь со службой *nx_dhcp_client_update_time_remaining*, описанной выше.</span><span class="sxs-lookup"><span data-stu-id="d3199-271">To update the time remaining on the DHCP Client IP address lease with elapsed time before calling *nx_dhcp_resume*, see the *nx_dhcp_client_update_time_remaining* described previously.</span></span>

<span data-ttu-id="d3199-272">Эта служба возобновляет работу протокола DHCP на всех интерфейсах, для которых включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="d3199-272">This service resumes DHCP running on all interfaces enabled for DHCP.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d3199-273">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="d3199-273">Input Parameters</span></span>

- <span data-ttu-id="d3199-274">**dhcp_ptr**: указатель на DHCP-клиент.</span><span class="sxs-lookup"><span data-stu-id="d3199-274">**dhcp_ptr**: Pointer to DHCP Client</span></span>

### <a name="return-values"></a><span data-ttu-id="d3199-275">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d3199-275">Return Values</span></span>

- <span data-ttu-id="d3199-276">**NX_SUCCESS** (0x0): поток клиента возобновлен.</span><span class="sxs-lookup"><span data-stu-id="d3199-276">**NX_SUCCESS**: (0x0) Client thread is resumed</span></span>
- <span data-ttu-id="d3199-277">NX_PTR_ERROR (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="d3199-277">NX_PTR_ERROR: (0x16) Invalid pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d3199-278">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d3199-278">Allowed From</span></span>

<span data-ttu-id="d3199-279">Потоки</span><span class="sxs-lookup"><span data-stu-id="d3199-279">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d3199-280">Пример</span><span class="sxs-lookup"><span data-stu-id="d3199-280">Example</span></span>

```c
/* Resume the DHCP client thread. */
status=  nx_dhcp_resume(client_ptr);

/* If status is NX_SUCCESS the current DHCP Client thread is resumed. */
```