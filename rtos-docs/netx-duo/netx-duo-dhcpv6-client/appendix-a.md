---
title: Приложение A. Описание функции восстановления состояния клиента DHCPv6 для NetX Duo в ОСРВ Azure
description: Параметр конфигурации клиента DHDPv6 для NetX Duo в ОСРВ Azure NX_DHCPV6_CLIENT_RESTORE_STATE позволяет системе восстанавливать ранее созданный клиент DHCP в состоянии привязки после перезагрузки системы.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6840f89e66d713b1839ac84427b73273b3f9601d4b6d9d39cd94908ac77a77ca
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791335"
---
# <a name="appendix-a---description-of-the-restore-state-feature-for-azure-rtos-netx-duo-dhcpv6-client"></a>Приложение A. Описание функции восстановления состояния клиента DHCPv6 для NetX Duo в ОСРВ Azure

Параметр конфигурации клиента DHDPv6 для NetX Duo в ОСРВ Azure NX_DHCPV6_CLIENT_RESTORE_STATE позволяет системе восстанавливать ранее созданный клиент DHCP в состоянии привязки после перезагрузки системы.

Кроме того, этот параметр позволяет приложению приостанавливать клиентский поток DHCPv6 и возобновлять его, обновляя изменение времени с момента приостановки до возобновления потока без отключения питания.

## <a name="restoring-the-dhcpv6-client-between-reboots"></a>Восстановление клиента DHCPv6 после перезагрузки

Чтобы восстанавливать клиент DHCPv6 после перезагрузки, приложение DHCPv6 создает экземпляр клиента DHCPv6 и получает аренду IP-адреса по обычным правилам протокола DHCPv6, а затем вызывает *nx_dhcpv6_start*. Затем приложение DHCPv6 ожидает завершения операций протокола. Если все проходит успешно, устройство переходит в состояние BOUND (Связано) и получает от сервера DHCPv6 допустимый IP-адрес. Перед отключением питания приложение клиента DHCPv6 переводит текущий экземпляр клиента DHCPv6 в формат записи клиента DHCPv6 и сохраняет его в энергонезависимой памяти. Независимый компонент системы выполняет роль "хранителя времени", то есть отслеживает прошедшее время с момента отключения питания. После возобновления работы приложение создает новый экземпляр клиента DHCPv6 и обновляет его, используя данные из ранее сохраненной записи клиента DHCPv6. От "хранителя времени" поступает информация о прошедшем времени, которое затем вычитается из остатка времени аренды, полученной клиентом DHCPv6. На этом этапе приложение может возобновить работу клиента DHCPv6.

Если с момента отключения прошло столько времени, что клиент DHCPv6 переходит в состояние RENEW (Продление) или REBIND (Повторная привязка), то он автоматически инициирует обмен сообщениями DHCPv6 для продления или повторной привязки аренды IP-адреса. Если срок действия IP-адреса уже истек, клиент DHCPv6 автоматически удалит IP-адрес из экземпляра IP и начнет процесс DHCPv6 с состояния INIT (Инициализация) для получения нового IP-адреса.

Это позволяет клиенту DHCPv6 работать после перезагрузки так, как если бы он не прерывал работу.

Ниже приводится иллюстрация этой возможности.

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

## <a name="nx_dhcpv6_client_get_record"></a>nx_dhcpv6_client_get_record

Создание записи текущего состояния клиента DHCPv6

### <a name="prototype"></a>Прототип

```C
ULONG nx_dhcpv6_client_get_record(NX_DHCPV6 *dhcpv6_ptr, 
                                  NX_DHCPV6_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a>Описание

Эта служба сохраняет клиент DHCPv6 в формате записи, на которую указывает record_ptr. Это позволяет приложению клиента DHCPv6 восстановить состояние клиента DHCPv6, например, после отключения питания и перезагрузки компьютера.

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr** — указатель на клиент DHCPv6.

- **record_ptr** — указатель на запись клиента DHCPv6.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS (0x0)** : допустимая запись клиента успешно создана.

- **NX_DHCPV6_NOT_BOUND** (0xE94): клиент не находится в состоянии привязки, то есть ему не назначен допустимый IP-адрес.

- **NX_PTR_ERROR** (0x16): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
NX_DHCPV6_CLIENT_RECORD dhcpv6_record;


/* Obtain a record of the current client state. */
status=  nx_dhcpv6_client_get_record(&dhcpv6_ptr, &dhcpv6_record);

/* If status is NX_SUCCESS dhcpv6_record contains the current DHCPv6 client record. */
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_resume
- nx_dhcpv6_suspend;
- nx_dhcpv6_client_restore_record.

## <a name="nx_dhcpv6_client_restore_record"></a>nx_dhcpv6_client_restore_record

Восстановление состояния клиента DHCPv6 из сохраненной записи

### <a name="prototype"></a>Прототип

```C
ULONG nx_dhcpv6_client_restore_record(NX_DHCPV6 *dhcpv6_ptr, 
                                      NX_DHCPV6_CLIENT_RECORD       
                                      *record_ptr, ULONG time_elapsed);
```

### <a name="description"></a>Описание

Эта служба позволяет приложению DHCPv6 восстановить прежнее состояние клиента DHCPv6 из предыдущего сеанса, обновив клиент DHCPv6 по информации из записи клиента DHCPv6, на которую указывает record_ptr, и применить изменения времени аренды клиента DHCPv6 на основе входного параметра time_elapsed. Это означает, что приложение клиента DHCPv6 может повторно создать клиент DHCPv6 (например, после отключения питания). Для этого нужно, чтобы приложение клиента DHCPv6 создало запись клиента DHCPv6 перед отключением питания и сохранило эту запись в энергонезависимой памяти.

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr** — указатель на клиент DHCPv6.

- **record_ptr** — указатель на запись клиента DHCPv6.

- **time_elapsed** — время, которое нужно вычесть из остатка времени аренды в предоставленной записи клиента.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS (0x0)** : запись клиента успешно восстановлена.

- NX_PTR_ERROR (0x16): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
NX_DHCPV6_CLIENT_RECORD dhcpv6_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 

/* Obtain a record of the current client state. */
status=  nx_dhcpv6_client_restore_record(&dhcpv6_ptr, &dhcpv6_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCPv6 Client pointed to by dhcpv6_ptr contains the current client record updated for time elapsed during power down. */
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_client_get_record.