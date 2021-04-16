---
title: Приложение A. Описание функции восстановления состояния клиента DHCPv6 для NetX Duo в ОСРВ Azure
description: Параметр конфигурации клиента DHDPv6 для NetX Duo в ОСРВ Azure NX_DHCPV6_CLIENT_RESTORE_STATE позволяет системе восстанавливать ранее созданный клиент DHCP в состоянии привязки после перезагрузки системы.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3e642af158202bb3b2a4e2a37397b47d707b566e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814787"
---
# <a name="appendix-a---description-of-the-restore-state-feature-for-azure-rtos-netx-duo-dhcpv6-client"></a><span data-ttu-id="2b310-103">Приложение A. Описание функции восстановления состояния клиента DHCPv6 для NetX Duo в ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="2b310-103">Appendix A - Description of the Restore State Feature for Azure RTOS NetX Duo DHCPv6 Client</span></span>

<span data-ttu-id="2b310-104">Параметр конфигурации клиента DHDPv6 для NetX Duo в ОСРВ Azure NX_DHCPV6_CLIENT_RESTORE_STATE позволяет системе восстанавливать ранее созданный клиент DHCP в состоянии привязки после перезагрузки системы.</span><span class="sxs-lookup"><span data-stu-id="2b310-104">The Azure RTOS NetX Duo DHDPv6 Client configuration option, NX_DHCPV6_CLIENT_RESTORE_STATE, allows a system to restore a previously created DHCP Client in a Bound state between system reboots.</span></span>

<span data-ttu-id="2b310-105">Кроме того, этот параметр позволяет приложению приостанавливать клиентский поток DHCPv6 и возобновлять его, обновляя изменение времени с момента приостановки до возобновления потока без отключения питания.</span><span class="sxs-lookup"><span data-stu-id="2b310-105">This option also allows an application to suspend the DHCPv6 Client thread and resume it, updated with the elapsed time between suspending and resuming the thread without powering down.</span></span>

## <a name="restoring-the-dhcpv6-client-between-reboots"></a><span data-ttu-id="2b310-106">Восстановление клиента DHCPv6 после перезагрузки</span><span class="sxs-lookup"><span data-stu-id="2b310-106">Restoring the DHCPv6 Client between Reboots</span></span>

<span data-ttu-id="2b310-107">Чтобы восстанавливать клиент DHCPv6 после перезагрузки, приложение DHCPv6 создает экземпляр клиента DHCPv6 и получает аренду IP-адреса по обычным правилам протокола DHCPv6, а затем вызывает *nx_dhcpv6_start*.</span><span class="sxs-lookup"><span data-stu-id="2b310-107">To restore a DHCPv6 Client between reboots, the DHCPv6 application creates an instance of the DHCPv6 Client, and then obtains an IP address lease using the normal DHCPv6 protocol and calling *nx_dhcpv6_start*.</span></span> <span data-ttu-id="2b310-108">Затем приложение DHCPv6 ожидает завершения операций протокола.</span><span class="sxs-lookup"><span data-stu-id="2b310-108">Then the DHCPv6 application waits for the protocol to complete.</span></span> <span data-ttu-id="2b310-109">Если все проходит успешно, устройство переходит в состояние BOUND (Связано) и получает от сервера DHCPv6 допустимый IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="2b310-109">If all goes well, the device achieves the BOUND state with an assigned valid IP address from its DHCPv6 Server.</span></span> <span data-ttu-id="2b310-110">Перед отключением питания приложение клиента DHCPv6 переводит текущий экземпляр клиента DHCPv6 в формат записи клиента DHCPv6 и сохраняет его в энергонезависимой памяти.</span><span class="sxs-lookup"><span data-stu-id="2b310-110">Before it powers down, the DHCPv6 Client application saves the current DHCPv6 Client instance to a DHCPv6 Client record which is then stored in non-volatile memory.</span></span> <span data-ttu-id="2b310-111">Независимый компонент системы выполняет роль "хранителя времени", то есть отслеживает прошедшее время с момента отключения питания.</span><span class="sxs-lookup"><span data-stu-id="2b310-111">An independent ‘time keeper’ elsewhere in the system keeps track of the time elapsed during this powered down state.</span></span> <span data-ttu-id="2b310-112">После возобновления работы приложение создает новый экземпляр клиента DHCPv6 и обновляет его, используя данные из ранее сохраненной записи клиента DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="2b310-112">On powering up, the application creates a new DHCPv6 Client instance, and then updates it with the previously created DHCPv6 Client record.</span></span> <span data-ttu-id="2b310-113">От "хранителя времени" поступает информация о прошедшем времени, которое затем вычитается из остатка времени аренды, полученной клиентом DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="2b310-113">The elapsed time is obtained from the “time keeper” and then applied to the time remaining on the DHCP Clientv6 lease.</span></span> <span data-ttu-id="2b310-114">На этом этапе приложение может возобновить работу клиента DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="2b310-114">At this point, the application can resume the DHCPv6 Client.</span></span>

<span data-ttu-id="2b310-115">Если с момента отключения прошло столько времени, что клиент DHCPv6 переходит в состояние RENEW (Продление) или REBIND (Повторная привязка), то он автоматически инициирует обмен сообщениями DHCPv6 для продления или повторной привязки аренды IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="2b310-115">If the time elapsed during power down puts the DHCPv6 Client state in either a RENEW or REBIND state, the DHCPv6 Client will automatically initiate DHCPv6 messages requesting to renew or rebind the IP address lease.</span></span> <span data-ttu-id="2b310-116">Если срок действия IP-адреса уже истек, клиент DHCPv6 автоматически удалит IP-адрес из экземпляра IP и начнет процесс DHCPv6 с состояния INIT (Инициализация) для получения нового IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="2b310-116">If the IP address is expired, the DHCPv6 Client will automatically clear the IP address on the IP instance and begin the DHCPv6 process from the INIT state, requesting a new IP address.</span></span>

<span data-ttu-id="2b310-117">Это позволяет клиенту DHCPv6 работать после перезагрузки так, как если бы он не прерывал работу.</span><span class="sxs-lookup"><span data-stu-id="2b310-117">In this manner the DHCPv6 Client can operate between reboots as if uninterrupted.</span></span>

<span data-ttu-id="2b310-118">Ниже приводится иллюстрация этой возможности.</span><span class="sxs-lookup"><span data-stu-id="2b310-118">Below is an illustration of this feature.</span></span>

```C
/* On the power up, create an IP instance, DHCPv6 Client, enable ICMPv6 and UDP
   and other resources (not shown) for the DHCPv6 Client/application
   in tx_application_define(). */
 
/* Define the DHCPv6 Client application thread. */     
void    thread_dhcpv6_client_entry(ULONG thread_input)
{

UINT        status;
UINT        time_elapsed = 0;
NX_DHCPV6_CLIENT_RECORD client_my_record;


    /* No previously saved Client record. Start the DHCPv6 Client in the INIT state. */
    status =  nx_dhcpv6_start(&dhcp_0);

    if (status !=NX_SUCCESS)
        return;

    while(1)    
    {
    
        /* Wait for DHCPv6 Client to get the IP address. */
    }

    /* At some point decide we power down the system. */

    /* Save the Client state data which we will subsequently need to restore the DHCPv6    
       Client. */
    status = nx_dhcpv6_client_get_record(&dhcp_0, &client_my_record);               

    /* Copy this memory to non-volatile memory (not shown). */

    /* Delete the IP and DHCPv6 Client instances before powering down. */
    nx_dhcpv6_client_delete(&dhcp_0);

    nx_ip_delete(&ip_0);

    /* Ready to power down, having released other resources as necessary. */

    /* The application has determined there is a previously saved record. We will 
       restore it to the current DHCPv6 Client instance. */

/* Create the IP and DHCPv6 Client instances, enable ICMPv6 and UDP after powering up. */

/* Calculate the time elapsed during power down */

    /* Get the previous Client state data from non-volatile memory. */

    /* Apply the record to the current Client instance. This will also 
       update the IP instance with IP address, mask etc. */
    status = nx_dhcpv6_client_restore_record(&dhcp_0, &client_my_record, time_elapsed);   

     if (status != NX_SUCCESS)
          return;

     /* We are ready to resume the DHCPv6 Client thread and use the assigned IP address. */
     status = nx_dhcpv6_resume(&dhcp_0);

     if (status != NX_SUCCESS)
          return;

}
```

## <a name="nx_dhcpv6_client_get_record"></a><span data-ttu-id="2b310-119">nx_dhcpv6_client_get_record</span><span class="sxs-lookup"><span data-stu-id="2b310-119">nx_dhcpv6_client_get_record</span></span>

<span data-ttu-id="2b310-120">Создание записи текущего состояния клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="2b310-120">Create a record of the current DHCPv6 Client state</span></span>

### <a name="prototype"></a><span data-ttu-id="2b310-121">Прототип</span><span class="sxs-lookup"><span data-stu-id="2b310-121">Prototype</span></span>

```C
ULONG nx_dhcpv6_client_get_record(NX_DHCPV6 *dhcpv6_ptr, 
                                  NX_DHCPV6_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a><span data-ttu-id="2b310-122">Описание</span><span class="sxs-lookup"><span data-stu-id="2b310-122">Description</span></span>

<span data-ttu-id="2b310-123">Эта служба сохраняет клиент DHCPv6 в формате записи, на которую указывает record_ptr.</span><span class="sxs-lookup"><span data-stu-id="2b310-123">This service saves the DHCPv6 Client to the record pointed to by record_ptr.</span></span> <span data-ttu-id="2b310-124">Это позволяет приложению клиента DHCPv6 восстановить состояние клиента DHCPv6, например, после отключения питания и перезагрузки компьютера.</span><span class="sxs-lookup"><span data-stu-id="2b310-124">This allows the DHCPv6 Client application restore its DHCPv6 Client state after, for example, a power down and reboot.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b310-125">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2b310-125">Input Parameters</span></span>

- <span data-ttu-id="2b310-126">**dhcpv6_ptr** — указатель на клиент DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="2b310-126">**dhcpv6_ptr** Pointer to DHCPv6 Client</span></span>

- <span data-ttu-id="2b310-127">**record_ptr** — указатель на запись клиента DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="2b310-127">**record_ptr** Pointer to DHCPv6 Client record</span></span>

### <a name="return-values"></a><span data-ttu-id="2b310-128">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2b310-128">Return Values</span></span>

- <span data-ttu-id="2b310-129">**NX_SUCCESS (0x0)** : допустимая запись клиента успешно создана.</span><span class="sxs-lookup"><span data-stu-id="2b310-129">**NX_SUCCESS (0x0)** Valid Client record created</span></span>

- <span data-ttu-id="2b310-130">**NX_DHCPV6_NOT_BOUND** (0xE94): клиент не находится в состоянии привязки, то есть ему не назначен допустимый IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="2b310-130">**NX_DHCPV6_NOT_BOUND** (0xE94) Client not in bound state, therefore not assigned valid IP address</span></span>

- <span data-ttu-id="2b310-131">**NX_PTR_ERROR** (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="2b310-131">**NX_PTR_ERROR** (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b310-132">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2b310-132">Allowed From</span></span>

<span data-ttu-id="2b310-133">Потоки</span><span class="sxs-lookup"><span data-stu-id="2b310-133">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b310-134">Пример</span><span class="sxs-lookup"><span data-stu-id="2b310-134">Example</span></span>

```C
NX_DHCPV6_CLIENT_RECORD dhcpv6_record;


/* Obtain a record of the current client state. */
status=  nx_dhcpv6_client_get_record(&dhcpv6_ptr, &dhcpv6_record);

/* If status is NX_SUCCESS dhcpv6_record contains the current DHCPv6 client record. */
```

### <a name="see-also"></a><span data-ttu-id="2b310-135">См. также:</span><span class="sxs-lookup"><span data-stu-id="2b310-135">See Also</span></span>

- <span data-ttu-id="2b310-136">nx_dhcpv6_resume;</span><span class="sxs-lookup"><span data-stu-id="2b310-136">nx_dhcpv6_resume</span></span>
- <span data-ttu-id="2b310-137">nx_dhcpv6_suspend;</span><span class="sxs-lookup"><span data-stu-id="2b310-137">nx_dhcpv6_suspend</span></span>
- <span data-ttu-id="2b310-138">nx_dhcpv6_client_restore_record.</span><span class="sxs-lookup"><span data-stu-id="2b310-138">nx_dhcpv6_client_restore_record</span></span>

## <a name="nx_dhcpv6_client_restore_record"></a><span data-ttu-id="2b310-139">nx_dhcpv6_client_restore_record</span><span class="sxs-lookup"><span data-stu-id="2b310-139">nx_dhcpv6_client_restore_record</span></span>

<span data-ttu-id="2b310-140">Восстановление состояния клиента DHCPv6 из сохраненной записи</span><span class="sxs-lookup"><span data-stu-id="2b310-140">Restore DHCPv6 Client state from saved record</span></span>

### <a name="prototype"></a><span data-ttu-id="2b310-141">Прототип</span><span class="sxs-lookup"><span data-stu-id="2b310-141">Prototype</span></span>

```C
ULONG nx_dhcpv6_client_restore_record(NX_DHCPV6 *dhcpv6_ptr, 
                                      NX_DHCPV6_CLIENT_RECORD       
                                      *record_ptr, ULONG time_elapsed);
```

### <a name="description"></a><span data-ttu-id="2b310-142">Описание</span><span class="sxs-lookup"><span data-stu-id="2b310-142">Description</span></span>

<span data-ttu-id="2b310-143">Эта служба позволяет приложению DHCPv6 восстановить прежнее состояние клиента DHCPv6 из предыдущего сеанса, обновив клиент DHCPv6 по информации из записи клиента DHCPv6, на которую указывает record_ptr, и применить изменения времени аренды клиента DHCPv6 на основе входного параметра time_elapsed.</span><span class="sxs-lookup"><span data-stu-id="2b310-143">This service enables a DHCPv6 application to recreate its DHCPv6 Client state from a previous session by updating the DHCPv6 Client with the DHCPv6 Client record pointed to by record_ptr, and updates the time remaining on DHCPv6 Client lease with the time_elapsed input.</span></span> <span data-ttu-id="2b310-144">Это означает, что приложение клиента DHCPv6 может повторно создать клиент DHCPv6 (например, после отключения питания).</span><span class="sxs-lookup"><span data-stu-id="2b310-144">This allows the DHCPv6 Client application to recreate its DHCPv6 Client, for example, after powering down.</span></span> <span data-ttu-id="2b310-145">Для этого нужно, чтобы приложение клиента DHCPv6 создало запись клиента DHCPv6 перед отключением питания и сохранило эту запись в энергонезависимой памяти.</span><span class="sxs-lookup"><span data-stu-id="2b310-145">This requires that the DHCPv6 Client application created a record of the DHCPv6 Client before powering down, and saved that record to non-volatile memory.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b310-146">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2b310-146">Input Parameters</span></span>

- <span data-ttu-id="2b310-147">**dhcpv6_ptr** — указатель на клиент DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="2b310-147">**dhcpv6_ptr** Pointer to DHCPv6 Client</span></span>

- <span data-ttu-id="2b310-148">**record_ptr** — указатель на запись клиента DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="2b310-148">**record_ptr** Pointer to DHCPv6 Client record</span></span>

- <span data-ttu-id="2b310-149">**time_elapsed** — время, которое нужно вычесть из остатка времени аренды в предоставленной записи клиента.</span><span class="sxs-lookup"><span data-stu-id="2b310-149">**time_elapsed** Time to subtract from the lease time remaining in the input client record</span></span>

### <a name="return-values"></a><span data-ttu-id="2b310-150">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2b310-150">Return Values</span></span>

- <span data-ttu-id="2b310-151">**NX_SUCCESS (0x0)** : запись клиента успешно восстановлена.</span><span class="sxs-lookup"><span data-stu-id="2b310-151">**NX_SUCCESS (0x0)** Client record restored</span></span>

- <span data-ttu-id="2b310-152">NX_PTR_ERROR (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="2b310-152">NX_PTR_ERROR (0x16) Invalid Pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b310-153">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2b310-153">Allowed From</span></span>

<span data-ttu-id="2b310-154">Потоки</span><span class="sxs-lookup"><span data-stu-id="2b310-154">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b310-155">Пример</span><span class="sxs-lookup"><span data-stu-id="2b310-155">Example</span></span>

```C
NX_DHCPV6_CLIENT_RECORD dhcpv6_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 

/* Obtain a record of the current client state. */
status=  nx_dhcpv6_client_restore_record(&dhcpv6_ptr, &dhcpv6_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCPv6 Client pointed to by dhcpv6_ptr contains the current client record updated for time elapsed during power down. */
```

### <a name="see-also"></a><span data-ttu-id="2b310-156">См. также:</span><span class="sxs-lookup"><span data-stu-id="2b310-156">See Also</span></span>

- <span data-ttu-id="2b310-157">nx_dhcpv6_client_get_record.</span><span class="sxs-lookup"><span data-stu-id="2b310-157">nx_dhcpv6_client_get_record</span></span>