---
title: Приложение A. Описание функции восстановления состояния служб клиента ОСРВ Azure NetX Duo DHCP
description: В этой главе содержится описание функции восстановления состояния для служб клиента ОСРВ Azure NetX Duo DHCP
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5b6d01930abdf7dd9d91ebe2e60eaac69ac73d2663a10263f07380e5c2895551
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788462"
---
# <a name="appendix-a--description-of-the-restore-state-feature-for-azure-rtos-netx-duo-dhcp-client-services"></a>Приложение A. Описание функции восстановления состояния клиента ОСРВ Azure NetX Duo DHCP

Параметр конфигурации клиента NetX Duo DHDP NX_DHCP_CLIENT_RESTORE_STATE позволяет системе восстанавливать созданный ранее клиент DHCP в состоянии BOUND после перезагрузки системы.

Если этот параметр включен, приложение может приостановить и возобновить поток DHCP-клиента. Существует также служба для передачи в DHCP-клиент времени, прошедшего между приостановкой и возобновлением потока.

## <a name="restoring-the-dhcp-client-between-reboots"></a>Восстановление DHCP-клиента после перезагрузки

Восстановление после перезагрузки можно использовать для созданного ранее DHCP-клиента, который должен перейти в состояние BOUND и получить IP-адрес от DHCP-сервера. Прежде чем выключить питание, приложение DHCP должно сохранить текущую запись DHCP-клиента в энергонезависимой памяти. Кроме того, необходим независимый компонент системы, который выполняет роль "хронометра", то есть отслеживает прошедшее время с момента отключения питания. После включения питания приложение создает новый экземпляр DHCP-клиента и обновляет его, используя данные из ранее сохраненной записи DHCP-клиента. Из "хронометра" поступает информация о прошедшем времени, которое затем вычитается из остатка времени аренды, полученной DHCP-клиентом. Обратите внимание на то, что это может привести к изменению состояния DHCP-клиента (например, с BOUND на RENEWING). На этом этапе приложение может возобновить работу DHCP-клиента.

Если с момента отключения прошло столько времени, что DHCP-клиент переходит в состояние RENEW или REBIND, то он автоматически инициирует обмен сообщениями DHCP для продления или повторной привязки аренды IP-адреса. Если срок действия IP-адреса уже истек, DHCP-клиент автоматически удалит IP-адрес из экземпляра IP и начнет процесс DHCP в состоянии INIT, запросив новый IP-адрес.

Это позволяет DHCP-клиенту работать после перезагрузки так, как если бы он не прерывал работу.

Ниже приводится иллюстрация этой возможности. Предполагается, что DHCP-клиент работает только на основном интерфейсе.

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
## <a name="resuming-the-dhcp-client-thread-after-suspension"></a>Возобновление потока DHCP-клиента после приостановки 

Чтобы приостановить поток DHCP-клиента без выключения питания, приложение вызывает *nx_dhcp_suspend* для DHCP-клиента, который перешел в состояние BOUND и имеет допустимый IP-адрес. Когда приложение готово возобновить работу DHCP-клиента, оно сначала вызывает службу *nx_dhcp_client_update_time_remaining*, чтобы обновить оставшееся время аренды DHCP-адреса (получив значение истекшего времени из независимого хронометра). Затем оно вызывает службу *nx_dhcp_resume* для возобновления потока DHCP-клиента.

Если прошло столько времени, что DHCP-клиент переходит в состояние RENEW или REBIND, то он автоматически инициирует обмен сообщениями DHCP для продления или повторной привязки аренды IP-адреса. Если срок действия IP-адреса уже истек, DHCP-клиент автоматически удалит IP-адрес и начнет процесс DHCP в состоянии INIT, запросив новый IP-адрес.

Ниже демонстрируется использование этой возможности.

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
Ниже приведен список служб для восстановления состояния DHCP-клиента из памяти, а также для приостановки и возобновления работы DHCP-клиента.

## <a name="nx_dhcp_client_get_record"></a>nx_dhcp_client_get_record

Создание записи текущего состояния DHCP-клиента.

### <a name="prototype"></a>Прототип

```c
ULONG nx_dhcp_ client_get_record(NX_DHCP *dhcp_ptr, NX_DHCP_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a>Описание

Эта служба сохраняет DHCP-клиент, работающий на первом интерфейсе с поддержкой DHCP, найденном в экземпляре DHCP-клиента, в записи, на которую указывает record_ptr. Это позволяет приложению DHCP-клиента восстановить состояние DHCP-клиента, например, после отключения питания и перезагрузки компьютера.

Чтобы сохранить запись DHCP-клиента на определенном интерфейсе, если для DHCP включено более одного интерфейса, используйте службу *nx_dhcp_interface_client_get_record*.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на DHCP-клиент.
- **record_ptr**: указатель на запись DHCP-клиента.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS (0x0)** : запись клиента успешно создана.
- **NX_DHCP_NOT_BOUND** (0x94): клиент не находится в состоянии BOUND.
- **NX_DHCP_NO_INTERFACES_ENABLED** (0xA5): протокол DHCP не включен ни для одного интерфейса.
- NX_PTR_ERROR (0x16): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
NX_DHCP_CLIENT_RECORD dhcp_record;

/* Obtain a record of the current client state. */
status=  nx_dhcp_client_get_record(dhcp_ptr, &dhcp_record);

/* If status is NX_SUCCESS dhcp_record contains the current DHCP client record. */
```

## <a name="nx_dhcp_interface_client_get_record"></a>nx_dhcp_interface_client_get_record

Создание записи текущего состояния DHCP-клиента на указанном интерфейсе.

### <a name="prototype"></a>Прототип

```c
ULONG nx_dhcp_interface_client_get_record(NX_DHCP *dhcp_ptr, UINT interface_index,
                                          NX_DHCP_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a>Описание

Эта служба сохраняет состояние DHCP-клиента, работающего на указанном интерфейсе, в записи, на которую указывает record_ptr. Это позволяет приложению DHCP-клиента восстановить состояние DHCP-клиента, например, после отключения питания и перезагрузки компьютера.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на DHCP-клиент.
- **interface_index**: индекс, по которому нужно получить запись.
- **record_ptr**: указатель на запись DHCP-клиента.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS (0x0)** : запись клиента успешно создана.
- **NX_DHCP_NOT_BOUND** (0x94): **клиент не находится в состоянии BOUND.**
- **NX_DHCP_BAD_INTERFACE_INDEX_ERROR** (0x9A): недопустимый индекс интерфейса.
- NX_PTR_ERROR (0x16): недопустимый указатель DHCP.
- NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
NX_DHCP_CLIENT_RECORD dhcp_record;
/* Obtain a record of the current client state on interface 1. */
status=  nx_dhcp_interface_client_get_record(dhcp_ptr, 1, &dhcp_record);

/* If status is NX_SUCCESS dhcp_record contains the current DHCP client record. */
```

## <a name="nx_dhcp_-client_restore_record"></a>nx_dhcp_ client_restore_record

Восстановление DHCP-клиента из сохраненной ранее записи.

### <a name="prototype"></a>Прототип

```c
ULONG nx_dhcp_client_restore_record(NX_DHCP *dhcp_ptr, 
                                    NX_DHCP_CLIENT_RECORD *record_ptr, 
                                    ULONG time_elapsed);

```

### <a name="description"></a>Описание

Эта служба позволяет приложению восстановить DHCP-клиент из предыдущего сеанса, используя запись DHCP-клиента, на которую указывает record_ptr. Входное значение time_elapsed применяется к оставшемуся времени аренды DHCP-клиента.

Для этого нужно, чтобы приложение DHCP-клиента создало запись DHCP-клиента перед отключением питания и сохранило эту запись в энергонезависимой памяти.

Если для DHCP-клиента включено более одного интерфейса, эта служба применяется к первому допустимому интерфейсу, обнаруженному в экземпляре DHCP-клиента.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на DHCP-клиент.
- **record_ptr**: указатель на запись DHCP-клиента. 
- **time_elapsed**: время, которое нужно вычесть из остатка времени аренды в предоставленной записи клиента.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS (0x0)** : запись клиента успешно восстановлена.
- **NX_DHCP_NO_INTERFACES_ENABLED** (0xA5): отсутствуют интерфейсы, использующие протокол DHCP.
- NX_PTR_ERROR (0x16): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
NX_DHCP_CLIENT_RECORD dhcp_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
Time_elapsed = /* to be determined by application */ 1000; 

/* Obtain a record of the current client state. */
status=  nx_dhcp_client_restore_record(client_ptr, &dhcp_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCP Client pointed to by dhcp_ptr  contains the current client record updated for time elapsed during power down. */
```

## <a name="nx_dhcp_interace_client_restore_record"></a>nx_dhcp_interace_client_restore_record

Восстановление DHCP-клиента из сохраненной ранее записи на указанном интерфейсе.

### <a name="prototype"></a>Прототип

```c
ULONG nx_dhcp_interface_client_restore_record(NX_DHCP *dhcp_ptr, 
                                              NX_DHCP_CLIENT_RECORD *record_ptr, 
                                              ULONG time_elapsed);
```

### <a name="description"></a>Описание

Эта служба позволяет приложению восстановить DHCP-клиент на указанном интерфейсе, используя запись DHCP-клиента, на которую указывает record_ptr. Входное значение time_elapsed применяется к оставшемуся времени аренды DHCP-клиента.

Для этого нужно, чтобы приложение DHCP-клиента создало запись DHCP-клиента перед отключением питания и сохранило эту запись в энергонезависимой памяти.

Если для DHCP-клиента включено более одного интерфейса, эта служба применяется к первому допустимому интерфейсу, обнаруженному в экземпляре DHCP-клиента.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на DHCP-клиент.
- **record_ptr**: указатель на запись DHCP-клиента. 
- **time_elapsed**: время, которое нужно вычесть из остатка времени аренды в предоставленной записи клиента.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS (0x0)** : запись клиента успешно восстановлена.
- **NX_DHCP_NOT_BOUND** (0x94): клиент не привязан к IP-адресу.
- **NX_DHCP_BAD_INTERFACE_INDEX_ERROR** (0x9A): недопустимый индекс интерфейса.
- NX_PTR_ERROR (0x16): недопустимый указатель DHCP.
- NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
NX_DHCP_CLIENT_RECORD dhcp_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
Time_elapsed = /* to be determined by application */ 1000; 


/* Obtain a record of the current client state on the primary interface. */
status=  nx_dhcp_interface_client_restore_record(client_ptr, 0, &dhcp_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCP Client pointed to by dhcp_ptr  contains the current client record updated for time elapsed during power down. */
```

## <a name="nx_dhcp_-client_update_time_remaining"></a>nx_dhcp_ client_update_time_remaining

Обновление оставшегося времени аренды DHCP-клиента.

### <a name="prototype"></a>Прототип

```c
ULONG nx_dhcp_client_update_time_remaining(NX_DHCP *dhcp_ptr, ULONG time_elapsed);
```

### <a name="description"></a>Описание

Эта служба обновляет оставшееся время аренды IP-адреса DHCP-клиентом с учетом входного значения time_elapsed на первом интерфейсе с поддержкой протокола DHCP, найденном в экземпляре DHCP-клиента. Приложение должно приостановить поток DHCP-клиента перед использованием этой службы с помощью *nx_dhcp_suspend*. После вызова этой службы приложение может возобновить поток DHCP-клиента, вызвав *nx_dhcp_resume*.

Эта служба предназначена для приложений DHCP-клиента, которым необходимо приостановить поток DHCP-клиента на определенный период времени, а затем обновить оставшееся время аренды IP-адреса.

Примечание. Она не предназначена для использования со службами *nx_dhcp_client_get_record* и *nx_dhcp_client_restore_record*, описанными выше. Эти службы были рассмотрены ранее в этом разделе.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на DHCP-клиент. 
- **time_elapsed**: время, вычитаемое из оставшегося времени аренды IP-адреса.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x0): аренда IP-адреса клиентом успешно обновлена.
- **NX_DHCP_NO_INTERFACES_ENABLED** (0xA5): протокол DHCP не включен ни для одного интерфейса.
- NX_PTR_ERROR (0x16): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 


/* Apply the elapsed time to the DHCP Client address lease. */
status=  nx_dhcp_client_update_time_remaining(client_ptr, time_elapsed);

/* If status is NX_SUCCESS the DHCP Client is updated for time elapsed. */
```

## <a name="nx_dhcp_interface_client_update_time_remaining"></a>nx_dhcp_interface_client_update_time_remaining

Обновление оставшегося времени аренды DHCP-клиента на указанном интерфейсе.

### <a name="prototype"></a>Прототип

```c
ULONG nx_dhcp_interface_client_update_time_remaining(NX_DHCP *dhcp_ptr,
                                                     UINT interface_index,
                                                     ULONG time_elapsed);
```

### <a name="description"></a>Описание

Эта служба обновляет оставшееся время аренды IP-адреса DHCP-клиентом с учетом входного значения time_elapsed на указанном интерфейсе с поддержкой протокола DHCP. Приложение должно приостановить поток DHCP-клиента перед использованием этой службы с помощью *nx_dhcp_suspend*. После вызова этой службы приложение может возобновить поток DHCP-клиента, вызвав *nx_dhcp_resume*. Обратите внимание на то, что приостановка и возобновление потока DHCP-клиента применяется ко всем интерфейсам, для которых включен протокол DHCP.

Эта служба предназначена для приложений DHCP-клиента, которым необходимо приостановить поток DHCP-клиента на определенный период времени, а затем обновить оставшееся время аренды IP-адреса.

Примечание. Она не предназначена для использования со службами *nx_dhcp_client_get_record* и *nx_dhcp_client_restore_record*, описанными выше. Эти службы были рассмотрены ранее в этом разделе.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на DHCP-клиент.
- **interface_index**: индекс интерфейса, для которого необходимо учесть истекшее время.
- **time_elapsed**: время, вычитаемое из оставшегося времени аренды IP-адреса.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x0): аренда IP-адреса клиентом успешно обновлена.
- **NX_DHCP_BAD_INTERFACE_INDEX_ERROR** (0x9A): недопустимый индекс интерфейса.
- NX_PTR_ERROR (0x16): недопустимый указатель DHCP.
- NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 


/* Apply the elapsed time to the DHCP Client address lease on interface 1. */
status=  nx_dhcp_interface_client_update_time_remaining(client_ptr, 1, time_elapsed);

/* If status is NX_SUCCESS the DHCP Client is updated for time elapsed. */

```

## <a name="nx_dhcp_suspend"></a>nx_dhcp_suspend

Приостановка потока DHCP-клиента.

### <a name="prototype"></a>Прототип

```c
ULONG nx_dhcp_suspend(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Описание

Эта служба приостанавливает текущий поток DHCP-клиента. Обратите внимание на то, что, в отличие от *nx_dhcp_stop*, при вызове этой службы не происходит никаких изменений в состоянии DHCP-клиента.

Эта служба приостанавливает работу протокола DHCP на всех интерфейсах, для которых включен протокол DHCP.

Чтобы узнать, как обновить состояние DHCP-клиента с учетом времени, в течение которого этот DHCP-клиент был приостановлен, ознакомьтесь со службой *nx_dhcp_client_update_time_remaining*, описанной выше. Чтобы возобновить приостановленный поток DHCP-клиента, приложение должно вызвать службу *nx_dhcp_resume*.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на DHCP-клиент.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x0): поток клиента приостановлен.
- NX_PTR_ERROR (0x16): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Pause the DHCP client thread. */
status=  nx_dhcp_suspend(client_ptr);

/* If status is NX_SUCCESS the current DHCP Client thread is paused. */
```

## <a name="nx_dhcp_resume"></a>nx_dhcp_resume

Возобновление приостановленного потока DHCP-клиента.

### <a name="prototype"></a>Прототип

```c
ULONG nx_dhcp_resume(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Описание

Эта служба возобновляет приостановленный поток DHCP-клиента. Обратите внимание на то, что после возобновления потока клиента фактическое состояние DHCP-клиента не изменяется. Чтобы узнать, как обновить оставшееся время аренды IP-адреса DHCP-клиентом с учетом прошедшего времени перед вызовом службы *nx_dhcp_resume*, ознакомьтесь со службой *nx_dhcp_client_update_time_remaining*, описанной выше.

Эта служба возобновляет работу протокола DHCP на всех интерфейсах, для которых включен протокол DHCP.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на DHCP-клиент.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x0): поток клиента возобновлен.
- NX_PTR_ERROR (0x16): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
/* Resume the DHCP client thread. */
status=  nx_dhcp_resume(client_ptr);

/* If status is NX_SUCCESS the current DHCP Client thread is resumed. */
```