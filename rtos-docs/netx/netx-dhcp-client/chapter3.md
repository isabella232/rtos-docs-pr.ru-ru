---
title: Глава 3. Описание служб клиента ОСРВ Azure NetX DHCP
description: В этой главе приводится описание всех служб ОСРВ Azure NetX DHCP, которые перечислены ниже в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8a614d22eca4fe693209751d72958b7d975c64c2
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815251"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dhcp-client-services"></a>Глава 3. Описание служб клиента ОСРВ Azure NetX DHCP

В этой главе приводится описание всех служб ОСРВ Azure NetX DHCP, которые перечислены ниже в алфавитном порядке.

В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки API на предмет ошибок, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.

- **nx_dhcp_create**: *создание экземпляра DHCP*.

- **nx_dhcp_clear_broadcast_flag**: сброс флага трансляции в сообщениях клиента.

- **nx_dhcp_delete**: *удаление экземпляра DHCP*.

- **nx_dhcp_decline**: отправка *сообщения об отклонении на сервер*.

- **nx_dhcp_force_renew**: *отправка сообщения для принудительного обновления*.

- **nx_dhcp_packet_pool_set**: *задание пула пакетов DHCP-клиента*.

- **nx_dhcp_release**: отправка *сообщения об освобождении на сервер*.

- **nx_dhcp_reinitialize**: *сброс параметров сети DHCP-клиента*.

- **nx_dhcp_request_client_ip**: *указание определенного IP-адреса*.

- **nx_dhcp_send_request**: *отправка сообщения DHCP на сервер*.

- **nx_dhcp_server_address_get**: *получение адреса DHCP-сервера для DHCP-клиента*.

- **nx_dhcp_set_interface_index**: *указание сетевого интерфейса клиента*.

- **nx_dhcp_start**: *запуск обработки DHCP*.

- **nx_dhcp_state_change_notify**: *уведомление приложения об изменении состояния DHCP*.

- **nx_dhcp_stop**: *остановка обработки DHCP*.

- **nx_dhcp_user_option_retrieve**: *извлечение параметра DHCP*.

- **nx_dhcp_user_option_convert**: *преобразование четырех байт в значение ULONG*.

Службы DHCP-клиента, относящиеся к интерфейсу

- **nx_dhcp_interface_clear_broadcast_flag**: *снятие флага трансляции в сообщениях клиента на указанном интерфейсе*.

- **nx_dhcp_interface_enable**: *включение протокола DHCP для указанного интерфейса*.

- **nx_dhcp_interface_disable**: *отключение протокола DHCP для указанного интерфейса*.

- **nx_dhcp_interface_decline**: *отправка сообщения об отклонении на сервер через указанный интерфейс*.

- **nx_dhcp_interface_force_renew**: *отправка сообщения для принудительного обновления через указанный интерфейс*.

- **nx_dhcp_interface_reinitialize**: *сброс параметров сети DHCP-клиента на указанном интерфейсе*.

- **nx_dhcp_interface_release**: *отправка сообщения об освобождении на сервер через указанный интерфейс*.

- **nx_dhcp_interface_request_client_ip**: *указание IP-адреса для указанного интерфейса*.

- **nx_dhcp_interface_send_request**: *отправка сообщения DHCP на сервер через указанный интерфейс*.

- **nx_dhcp_interface_server_address_get**: *получение IP-адреса DHCP-сервера для указанного интерфейса*.

- **nx_dhcp_interface_start**: *запуск обработки DHCP-клиента на указанном интерфейсе*.

- **nx_dhcp_interface_stop**: *остановка обработки DHCP-клиента на указанном интерфейсе*.

- **nx_dhcp_interface_state_change_notify**: *указание функции обратного вызова при изменении состояния DHCP на указанном интерфейсе*.

- **nx_dhcp_interface_user_option_retrieve**: *получение указанного параметра DHCP для заданного интерфейса*.

Службы DHCP-клиента, если определено значение NX_DHCP_CLIENT_RESORE_STATE.

- **nx_dhcp_resume**: *восстановление ранее заданного состояния DHCP-клиента*.

- **nx_dhcp_suspend**: *приостановка обработки состояния DHCP-клиента*.

- **nx_dhcp_client_get_record**: *создание записи состояния DHCP-клиента*.

- **nx_dhcp_client_restore_record**: *восстановление ранее сохраненной записи в DHCP-клиенте*.

- **nx_dhcp_client_update_time_remaining**: *обновление значения оставшегося времени в текущем состоянии DHCP*.

Службы DHCP-клиента, относящиеся к интерфейсу, если определен параметр NX_DHCP_CLIENT_RESORE_STATE.

- **nx_dhcp_client_interface_get_record**: *создание записи состояния DHCP-клиента на указанном интерфейсе*.

- **nx_dhcp_client_interface_restore_record**: *восстановление ранее сохраненной записи состояния DHCP-клиента на указанном интерфейсе*.

- **nx_dhcp_client_interface_update_time_remaining**: *обновление значения оставшегося времени в текущем состоянии DHCP для указанного интерфейса*.

## <a name="nx_dhcp_create"></a>nx_dhcp_create

Создание экземпляра DHCP.

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_create(NX_DHCP *dhcp_ptr, NX_IP *ip_ptr, CHAR *name_ptr);
```

### <a name="description"></a>Описание

Эта служба создает экземпляр DHCP для созданного ранее экземпляра IP. По умолчанию протокол DHCP включается для основного интерфейса. Введенное имя, хотя и не используется в реализации DHCP-клиента в NetX, должно соответствовать требованиям RFC 1035 к именам узлов. Общая длина не должна превышать 255 символов, а элементы, разделяемые точками, должны начинаться с буквы, заканчиваться буквой или цифрой и могут содержать только буквы, цифры и дефисы.

Если приложению требуется запустить протокол DHCP на другом интерфейсе, зарегистрированном в экземпляре IP (с помощью *nx_ip_interface_attach*), оно может вызвать *nx_dhcp_set_interface_index* для запуска протокола DHCP только на этом интерфейсе или *nx_dhcp_interface_enable* для запуска протокола DHCP на этом интерфейсе в дополнение к другим. Дополнительные сведения см. в описании этих служб.

> [!NOTE]
> Приложение должно убедиться в том, что полезные данные пула пакетов DHCP-клиента соответствуют минимальному размеру сообщения DHCP, указанному в разделе 2 спецификации RFC 2131 (548 байт данных сообщения DHCP плюс заголовки UDP, IP и кадра физической сети).

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на блок управления DHCP.  
- **ip_ptr**: указатель на созданный ранее экземпляр IP.  
- **name_ptr**: указатель на имя узла для экземпляра DHCP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): экземпляр DHCP успешно создан.

- **NX_DHCP_INVALID_NAME** (0xA8): недопустимое имя узла.

- **NX_DHCP_INVALID_PAYLOAD** (0x9C): слишком маленький размер полезных данных для сообщения DHCP.

- NX_PTR_ERROR (0x16): недопустимый указатель IP или DHCP.

### <a name="allowed-from"></a>Допустимые источники

**Потоки**, инициализация.

### <a name="example"></a>Например, .

```C
/* Create a DHCP instance. */
status =  nx_dhcp_create(&my_dhcp, &my_ip, "My-DHCP");

/* If status is NX_SUCCESS a DHCP instance was successfully created. */
```

## <a name="nx_dhcp_interface_enable"></a>nx_dhcp_interface_enable

Включение протокола DHCP для указанного интерфейса. 

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_interface_enable(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a>Описание

Эта служба включает протокол DHCP для указанного интерфейса. По умолчанию для DHCP-клиента включен основной интерфейс. На этом этапе можно запустить DHCP либо на этом интерфейсе, вызвав *nx_dhcp_interface_start*, либо на всех интерфейсах с поддержкой DHCP, вызвав *nx_dhcp_start*.

Обратите внимание на то, что приложение должно сначала зарегистрировать этот интерфейс в экземпляре IP с помощью *nx_ip_interface_attach*.

Кроме того, для добавления этого интерфейса в список включенных должна быть доступная запись интерфейса DHCP-клиента. По умолчанию параметр NX_DHCP_CLIENT_MAX_RECORDS имеет значение 1. Задайте для этого параметра максимальное число интерфейсов для одновременного выполнения DHCP-клиента. Обычно значение NX_DHCP_CLIENT_MAX_RECORDS равно NX_MAX_PHYSICAL_INTERFACES. Но если у устройства больше физических интерфейсов, чем требуется для работы DHCP-клиента, можно сэкономить память, задав для параметра NX_DHCP_CLIENT_MAX_RECORDS меньшее число. Не существует однозначного сопоставления между физическими интерфейсами и записями интерфейсов DHCP-клиента.

Разница между этой службой и *nx_dhcp_set_interface_index* состоит в том, что последняя включает протокол DHCP только для одного интерфейса, тогда как данная служба просто добавляет указанный интерфейс в список интерфейсов клиента с поддержкой DHCP.

Чтобы отключить протокол DHCP для интерфейса, приложение может вызвать службу *nx_dhcp_interface_disable*.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на блок управления DHCP.  

- **interface_index**: индекс интерфейса, для которого нужно включить протокол DHCP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): протокол DHCP успешно включен.

- **NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7): нет доступной записи для другого интерфейса, для которого следует включить протокол DHCP.

- **NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3): для интерфейса включен протокол DHCP.

- NX_PTR_ERROR (0x16): недопустимый указатель IP или DHCP.

- NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.

### <a name="allowed-from"></a>Допустимые источники

Потоки, инициализация.

### <a name="example"></a>Например, .

```C
/* Enable DHCP on a secondary interface. It is already enabled on the primary 
   interface. NX_DHCP_CLIENT_MAX_RECORDS is set to 2. */

status =  nx_dhcp_interface_enable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface was successfully enabled. */


status = nx_dhcp_start(&my_dhcp);
/* If status is NX_SUCCESS DHCP is running on interface 0 and 1. */
```

## <a name="nx_dhcp_interface_disable"></a>nx_dhcp_interface_disable

Отключение протокола DHCP для указанного интерфейса. 

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_interface_disable(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a>Описание

Эта служба отключает протокол DHCP для указанного интерфейса. Она повторно инициализирует DHCP-клиент для этого интерфейса.

Чтобы перезапустить DHCP-клиент, приложение должно повторно включить интерфейс с помощью *nx_dhcp_interface_enable* и перезапустить DHCP, вызвав *nx_dhcp_interface_start*.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на блок управления DHCP.  

- **interface_index**: индекс интерфейса, для которого нужно отключить протокол DHCP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): экземпляр DHCP успешно создан.

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4): для интерфейса не включен протокол DHCP.

- NX_PTR_ERROR (0x16): недопустимый указатель IP или DHCP.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

- NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Disable DHCP on a secondary interface.
. */

status = nx_dhcp_interface_disable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface is successfully disabled. */
```

## <a name="nx_dhcp_clear_broadcast_flag"></a>nx_dhcp_clear_broadcast_flag

Установка флага широковещательного режима DHCP.

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_clear_broadcast_flag(NX_DHCP *dhcp_ptr, UINT clear_flag);
```

### <a name="description"></a>Описание

Эта служба устанавливает или снимает флаг широковещательного режима в заголовке сообщения DHCP для всех интерфейсов, для которых включен протокол DHCP. Для некоторых сообщений DHCP (например, DISCOVER) флаг широковещательного режима установлен, так как у клиента нет IP-адреса.

__clear_flag__


- **NX_TRUE**: флаг широковещательного режима снят (запрашивается одноадресный ответ).

- **NX_FALSE**: флаг широковещательного режима установлен (запрашивается широковещательный ответ).

Эта служба предназначена для DHCP-клиентов, которые должны обращаться к DHCP-серверу через маршрутизатор, который отклоняет переадресацию широковещательных сообщений.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на блок управления DHCP.  

- **clear_flag**: значение, устанавливаемое для флага широковещательного режима.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): флаг широковещательного режима успешно обновлен.

- NX_PTR_ERROR (0x16): недопустимый указатель IP или DHCP.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки, инициализация.

### <a name="example"></a>Например, .

```C
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a  
    unicast response). */
status =  nx_dhcp_clear_broadcast_flag(&my_dhcp, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated. */
```

## <a name="nx_dhcp_interface_clear_broadcast_flag"></a>nx_dhcp_interface_clear_broadcast_flag

Установка или снятие флага широковещательного режима для указанного интерфейса.

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_interface_clear_broadcast_flag(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            UINT clear_flag);
```

### <a name="description"></a>Описание

Эта служба позволяет ведущему приложению DHCP-клиента устанавливать или снимать флаг широковещательного режима в сообщениях DHCP-клиента, передаваемых DHCP-серверу через указанный интерфейс. Дополнительные сведения см. в описании службы **nx_dhcp_clear_broadcast_flag**.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на блок управления DHCP.

- **interface_index**: индекс интерфейса, для которого нужно установить флаг широковещательного режима.  

- **clear_flag**: значение, устанавливаемое для флага широковещательного режима.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): флаг широковещательного режима успешно обновлен.

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4): для интерфейса не включен протокол DHCP.

- NX_PTR_ERROR (0x16): недопустимый указатель IP или DHCP.

- NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.

### <a name="allowed-from"></a>Допустимые источники

Потоки, инициализация.

### <a name="example"></a>Например, .

```C
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a 
   unicast response) on a previously attached secondary interface. */

iface_index = 1;

status =  nx_dhcp_interface_clear_broadcast_flag(&my_dhcp, iface_index, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated. */
```

## <a name="nx_dhcp_delete"></a>nx_dhcp_delete

Удаление экземпляра DHCP.

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_delete(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет созданный ранее экземпляр DHCP.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): экземпляр DHCP успешно удален.

- NX_PTR_ERROR (0x16): недопустимый указатель DHCP.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Delete a DHCP instance. */
status =  nx_dhcp_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCP instance was successfully deleted. */
```

## <a name="nx_dhcp_-force_renew"></a>nx_dhcp_ force_renew

Отправка сообщения о принудительном обновлении. 

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp force_renew(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Описание

Эта служба позволяет ведущему приложению отправлять сообщение о принудительном обновлении для всех интерфейсов, для которых включен протокол DHCP. DHCP-клиент должен находиться в состоянии BOUND. Эта функция устанавливает состояние "RENEW" (Продление), чтобы DHCP-клиент пытался выполнить обновление до истечения времени ожидания T1.

Чтобы отправить сообщение о принудительном обновлении на определенный интерфейс, когда протокол DHCP включен для нескольких интерфейсов, используйте *nx_dhcp_interface_force_renew*.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): сообщение о принудительном обновлении успешно отправлено.  

- NX_PTR_ERROR (0x16): недопустимый указатель DHCP.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Send a force renew message from the Client. */
status =  nx_dhcp_force_renew(&my_dhcp);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired. */
```

## <a name="nx_dhcp_interface_force_renew"></a>nx_dhcp_interface_force_renew

Отправка сообщения о принудительном обновлении на указанный интерфейс.

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_interface_force_renew(NX_DHCP *dhcp_ptr,
                                    UINT interface_index);
```

### <a name="description"></a>Описание

Эта служба позволяет ведущему приложению отправлять сообщение о принудительном обновлении на указанный интерфейс, если для него включен протокол DHCP (см. описание службы *nx_dhcp_interface_enable*). DHCP-клиент на указанном интерфейсе должен находиться в состоянии BOUND. Эта функция устанавливает состояние "RENEW" (Продление), чтобы DHCP-клиент пытался выполнить обновление до истечения времени ожидания T1.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): сообщение о принудительном обновлении успешно отправлено.  

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4): для интерфейса не включен протокол DHCP.

- NX_PTR_ERROR (0x16): недопустимый указатель IP или DHCP.

- NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Send a force renew message to the server on interface 1. */
status =  nx_dhcp_interface_force_renew(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired. */
```

## <a name="nx_dhcp_packet_pool_set"></a>nx_dhcp_packet_pool_set

Задание пула пакетов DHCP-клиента.

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_packet_pool_set(NX_DHCP *dhcp_ptr,
                            NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a>Описание

Эта служба позволяет приложению создать пул пакетов DHCP-клиента путем передачи указателя на ранее созданный пул пакетов в этом вызове службы. Чтобы использовать эту функцию, ведущее приложение должно задать параметр NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL. Если этот параметр определен, служба *nx_dhcp_create* не создаст пул пакетов клиента. В приложении рекомендуется использовать значения по умолчанию для полезных данных пула пакетов DHCP-клиента, которые определяются в параметре NX_DHCP_PACKET_PAYLOAD в файле *nxd_dhcp_client.h* при создании пула пакетов.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на блок управления DHCP.  

- **packet_pool_ptr**: указатель на созданный ранее пул пакетов.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): пул пакетов DHCP-клиента задан.

- **NX_NOT_ENABLED** (0x14): служба не включена.

- NX_PTR_ERROR (0x16): недопустимый указатель DHCP.

- NX_DHCP_INVALID_PAYLOAD (0x9C): слишком маленький размер полезных данных.

### <a name="allowed-from"></a>Допустимые источники

Код приложения

### <a name="example"></a>Например, .

```C
/* Create the packet pool. */
status =  nx_packet_pool_create(&dhcp_pool, "DHCP Client Packet Pool", 
        NX_DHCP_PACKET_PAYLOAD, pointer, (15 * NX_DHCP_PACKET_PAYLOAD));

/* Create the DHCP Client. */
status =  nx_dhcp_create(&dhcp_0, &ip_0, "janetsdhcp1");

/* Set the DHCP Client packet pool. */
status =  nx_dhcp_packet_pool_set(&my_dhcp, packet_pool_ptr);
/* If status is NX_SUCCESS packet pool was successfully set. */
```

## <a name="nx_dhcp_request_client_ip"></a>nx_dhcp_request_client_ip

Задание запрошенного IP-адреса для экземпляра DHCP.

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_request_client_ip(NX_DHCP *dhcp_ptr,
                                ULONG client_ip_address,
                                UINT skip_discover_message);
```

### <a name="description"></a>Описание

Эта служба задает IP-адрес, запрашиваемый DHCP-клиентом у DHCP-сервера, для первого интерфейса, для которого включен протокол DHCP в записи DHCP-клиента. Если установлен флаг *skip_discover_message*, DHCP-клиент пропускает сообщение об обнаружении и отправляет сообщение запроса.

Чтобы настроить запрос определенного IP-адреса для сообщений DHCP через определенный интерфейс, используйте службу *nx_dhcp_interface_request_client_ip*.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на блок управления DHCP.  

- **client_ip_address**: IP-адрес, запрашиваемый у DHCP-сервера.

- **skip_discover_message**: если задано значение true, DHCP-клиент отправляет сообщение запроса.  
Если значение равно false, отправляется сообщение об обнаружении.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): запрошенный IP-адрес задан.

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4): для интерфейса не включен протокол DHCP.

- NX_PTR_ERROR (0x16): недопустимый указатель IP или DHCP.

- NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.
 
### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Set the DHCP Client requested IP address and skip the discover message. */

status =  nx_dhcp_request_client_ip(&my_dhcp, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set. */
```

## <a name="nx_dhcp_interface_request_client_ip"></a>nx_dhcp_interface_request_client_ip

Задание запрошенного IP-адреса для экземпляра DHCP на указанном интерфейсе.

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_interface_request_client_ip(NX_DHCP *dhcp_ptr,
                                        UINT interface_index,
                                        ULONG client_ip_address,
                                        UINT skip_discover_message);
```

### <a name="description"></a>Описание

Эта служба задает IP-адрес, запрашиваемый DHCP-клиентом у DHCP-сервера, для указанного интерфейса, если для него включен протокол DHCP (см. описание службы *nx_dhcp_interface_enable*). Если установлен флаг *skip_discover_message*, DHCP-клиент пропускает сообщение об обнаружении и отправляет сообщение запроса.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на блок управления DHCP.

- **Interface_index**: индекс интерфейса для запроса IP-адреса.

- **client_ip_address**: IP-адрес, запрашиваемый у DHCP-сервера.

- **skip_discover_message**: если задано значение true, DHCP-клиент отправляет сообщение запроса; в противном случае отправляется сообщение об обнаружении.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): запрошенный IP-адрес задан.

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4): для интерфейса не включен протокол DHCP.

- NX_PTR_ERROR (0x16): недопустимый указатель IP или DHCP.

- NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.


### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Set the DHCP Client requested IP address and skip the discover message on  
   interface 0. */
status =  nx_dhcp_interface_request_client_ip(&my_dhcp, 0, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set. */
```

## <a name="nx_dhcp_reinitialize"></a>nx_dhcp_reinitialize

Сброс параметров сети DHCP-клиента. 

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_reinitialize(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Описание

Эта служба сбрасывает параметры сети ведущего приложения (IP-адрес, сетевой адрес и маску сети) и очищает состояние DHCP-клиента на всех интерфейсах, для которых включен протокол DHCP. Она используется в сочетании с *nx_dhcp_stop* и *nx_dhcp_start* для перезапуска конечного автомата DHCP: 

nx_dhcp_stop(&my_dhcp);  
nx_dhcp_reinitialize(&my_dhcp);  
nx_dhcp_start(&my_dhcp);


Для повторной инициализации DHCP-клиента на определенном интерфейсе, когда протокол DHCP включен для нескольких интерфейсов, используйте службу *nx_dhcp_interface_reinitialize*.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): протокол DHCP инициализирован повторно. 

- NX_PTR_ERROR (0x16): недопустимый указатель DHCP.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Reinitialize the previously started DHCP client. */
status =  nx_dhcp_reinitialize(&my_dhcp);

/* If status is NX_SUCCESS the host application successfully reinitialized its 
network parameters and DHCP client state. */
```

## <a name="nx_dhcp_interface_reinitialize"></a>nx_dhcp_interface_reinitialize

Сброс параметров сети DHCP-клиента для указанного интерфейса. 

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_interface_reinitialize(NX_DHCP *dhcp_ptr,
                                    UINT interface_index);
```

### <a name="description"></a>Описание

Эта служба сбрасывает параметры сети (IP-адрес, сетевой адрес и маску сети) для указанного интерфейса, если для него включен протокол DHCP (см. описание службы *nx_dhcp_interface_enable*). Дополнительные сведения см. в описании службы *nx_dhcp_reinitialize*.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.

- **interface_index**: индекс интерфейса, который нужно инициализировать повторно.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): интерфейс инициализирован повторно.

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4): для интерфейса не включен протокол DHCP.

- NX_PTR_ERROR (0x16): недопустимый указатель DHCP.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

- NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Reinitialize the previously started DHCP client on interface 1. */
status =  nx_dhcp_interface_reinitialize(&my_dhcp, 1);

/* If status is NX_SUCCESS the host application successfully reinitialized its 
network parameters and DHCP client state. */
```

## <a name="nx_dhcp_release"></a>nx_dhcp_release

Освобождение арендованного IP-адреса.

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_release(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Описание

Эта служба освобождает IP-адрес, полученный от DHCP-сервера, отправляя на него сообщение RELEASE. Затем она повторно инициализирует DHCP-клиент. Эта служба применяется ко всем интерфейсам, для которых включен протокол DHCP.

Приложение может перезапустить DHCP-клиент, вызвав *nx_dhcp_start*.

Чтобы вернуть адрес DHCP-серверу на определенном интерфейсе, используйте службу *nx_dhcp_interface_release*.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): экземпляр DHCP успешно освобожден.  

- **NX_DHCP_NOT_BOUND** (0x94): IP-адрес не был арендован, поэтому его невозможно освободить.

- NX_PTR_ERROR (0x16): недопустимый указатель DHCP.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Release the previously leased IP address. */
status =  nx_dhcp_release(&my_dhcp);

/* If status is NX_SUCCESS the previous IP lease was successfully released. */
```

## <a name="nx_dhcp_interface_release"></a>nx_dhcp_interface_release

Освобождение IP-адреса на указанном интерфейсе.

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_interface_release(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a>Описание

Эта служба освобождает IP-адрес, полученный от DHCP-сервера, на указанном интерфейсе и повторно инициализирует DHCP-клиент. DHCP-клиент можно перезапустить, вызвав *nx_dhcp_start*.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): экземпляр DHCP успешно освобожден.

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4): для интерфейса не включен протокол DHCP.

- **NX_DHCP_NOT_BOUND** (0x94): IP-адрес не был арендован, поэтому его невозможно освободить.

- NX_PTR_ERROR (0x16): недопустимый указатель DHCP.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

- NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Release the previously leased IP address on interface 1. */
status =  nx_dhcp_interface_release(&my_dhcp, 1);

/* If status is NX_SUCCESS the previous IP lease was successfully released. */
```

## <a name="nx_dhcp_decline"></a>nx_dhcp_decline

Отклонение IP-адреса от DHCP-сервера.

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_decline(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Описание

Эта служба отклоняет IP-адрес, арендованный у DHCP-сервера, на всех интерфейсах, для которых включен протокол DHCP. Когда задан параметр NX_DHCP_CLIENT_SEND_ARP_PROBE, DHCP-клиент отправляет сообщение DECLINE, если обнаруживает, что IP-адрес уже занят. Дополнительные сведения о настройке проб ARP в клиенте NetX DHCP см. в разделе **Пробы ARP** главы 1.

Приложение может использовать эту службу для отклонения IP-адреса, если обнаруживает, что адрес используется каким-либо иным образом.

Эта служба повторно инициализирует DHCP-клиент, чтобы его можно было перезапустить, вызвав *nx_dhcp_start*.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): отклонение успешно выполнено.  

- **NX_DHCP_NOT_STARTED** (0x96): экземпляр DHCP не запущен.

- NX_PTR_ERROR (0x16): недопустимый указатель DHCP.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Decline the IP address offered by the DHCP server. */
status =  nx_dhcp_decline(&my_dhcp);

/* If status is NX_SUCCESS the previous IP address decline message was 
   successfully trasnmitted. */
```

## <a name="nx_dhcp_interface_decline"></a>nx_dhcp_interface_decline

Отклонение IP-адреса от DHCP-сервера на указанном интерфейсе.

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_interface_decline(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a>Описание

Эта служба отправляет сообщение DECLINE на сервер, чтобы отклонить IP-адрес, назначенный DHCP-сервером. Она также повторно инициализирует DHCP-клиент. Дополнительные сведения см. в описании службы *nx_dhcp_decline*.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.

- **Interface_index**: индекс интерфейса для отклонения IP-адреса.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): отправлено сообщение об отклонении DHCP.  

- **NX_DHCP_NOT_BOUND** (0x94): DHCP-клиент не привязан.

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4): для интерфейса не включен протокол DHCP.

- NX_PTR_ERROR (0x16): недопустимый указатель DHCP.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

- NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .
```C
/* Decline the IP address offered by the DHCP server on interface 2. */
status =  nx_dhcp_interface_decline(&my_dhcp, 2);

/* If status is NX_SUCCESS the previous IP address decline message was
   successfully trasnmitted. */
```

## <a name="nx_dhcp_send_request"></a>nx_dhcp_send_request

Отправка сообщения DHCP на сервер.

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_send_request(NX_DHCP *dhcp_ptr, UINT dhcp_message_type);
```

### <a name="description"></a>Описание

Эта служба отправляет указанное сообщение DHCP на DHCP-сервер через первый интерфейс, для которого включен протокол DHCP, найденный в записи DHCP-клиента. Чтобы отправить сообщение RELEASE или DECLINE, приложение должно использовать службу *nx_dhcp[_interface]_release()* или *nx_dhcp_interface_decline()* соответственно.

Для использования этой службы DHCP-клиент должен быть запущен, за исключением отправки сообщений типа INFORM_REQUEST.

> [!NOTE] 
> Эта служба не предназначена для запуска конечного автомата DHCP-клиента ведущим приложением.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на блок управления DHCP.  

- **dhcp_message_type**: запрос сообщения (определен в *nx_dhcp.h*).

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): сообщение DHCP отправлено.  

- **NX_DHCP_NOT_STARTED** (0x96): недопустимый индекс интерфейса.

- **NX_DHCP_INVALID_MESSAGE** (0x9B): недопустимый тип отправляемого сообщения.

- NX_PTR_ERROR (0x16): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Send the DHCP INFORM REQUEST message to the server. */

status =  nx_dhcp_send_request(&my_dhcp, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent. */
```

## <a name="nx_dhcp_interface_send_request"></a>nx_dhcp_interface_send_request

Отправка сообщения DHCP на сервер через указанный интерфейс.

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_interface_send_request(NX_DHCP *dhcp_ptr,
                                    UINT interface_index,
                                    UINT dhcp_message_type);
```

### <a name="description"></a>Описание

Эта служба отправляет сообщение на DHCP-сервер через указанный интерфейс, если для него включен протокол DHCP. Чтобы отправить сообщение RELEASE или DECLINE, приложение должно использовать службу *nx_dhcp[_interface]_release()* или *nx_dhcp_interface_decline()* соответственно.

Для использования этой службы DHCP-клиент должен быть запущен, за исключением отправки сообщений DHCP типа INFORM_REQUEST.

Эта служба не предназначена для запуска конечного автомата DHCP-клиента ведущим приложением.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на блок управления DHCP.

- **interface_index**: индекс интерфейса для отправки сообщения.  

- **dhcp_message_type**: запрос сообщения (определен в *nx_dhcp.h*).

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): сообщение DHCP отправлено.  

- **NX_DHCP_NOT_STARTED** (0x96): недопустимый индекс интерфейса.

- **NX_DHCP_INVALID_MESSAGE** (0x9B): недопустимый тип отправляемого сообщения.

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4): для интерфейса не включен протокол DHCP.

- NX_PTR_ERROR (0x16): недопустимый указатель DHCP.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

- NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Send the INFORM REQUEST message to the server on the primary interface. */

status =  nx_dhcp_interface_send_request(&my_dhcp, 0, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent. */
```

## <a name="nx_dhcp_server_address_get"></a>nx_dhcp_server_address_get

Получение IP-адреса DHCP-сервера для DHCP-клиента.

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_server_address_get(NX_DHCP *dhcp_ptr,
                                ULONG server_address);
```

### <a name="description"></a>Описание

Эта служба получает IP-адрес DHCP-сервера для DHCP-клиента через первый интерфейс, для которого включен протокол DHCP, найденный в записи DHCP-клиента. Вызывающая сторона может использовать эту службу только после привязки DHCP-клиента к IP-адресу, назначенному DHCP-сервером. Ведущее приложение может использовать службу *nx_ip_status_check* для проверки того, задан ли IP-адрес, или использовать nx *_dhcp_state_change_notify* и проверить, находится ли DHCP-клиент в состоянии NX_DHCP_STATE_BOUND. Дополнительные сведения о настройке функции обратного вызова для изменения состояния см. в описании функции *nx_dhcp_state_change_notify*.

Чтобы найти DHCP-сервер на определенном интерфейсе, когда для DHCP-клиента включено несколько интерфейсов, используйте службу *nx_dhcp_interface_server_address_get*.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на блок управления DHCP.

- **server_address**: указатель на IP-адрес сервера.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): адрес DHCP-сервера возвращен.

- NX_PTR_ERROR (0x16): недопустимый указатель ввода.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. 
/* void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter. */
    state_changes++;

    if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
    {
            status = nx_dhcp_server_address_get(&dhcp_0, &server_address);
    }
```

## <a name="nx_dhcp_interface_server_address_get"></a>nx_dhcp_interface_server_address_get

Получение IP-адреса DHCP-сервера для DHCP-клиента на указанном интерфейсе.

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_interface_server_address_get(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            ULONG server_address);
```

### <a name="description"></a>Описание

Эта служба получает IP-адрес DHCP-сервера для DHCP-клиента на указанном интерфейсе, если для него включен протокол DHCP. DHCP-клиент должен находиться в состоянии BOUND. После запуска DHCP-клиента на этом интерфейсе ведущее приложение может либо использовать службу *nx_ip_status_check*, чтобы проверить, задан ли IP-адрес, либо использовать обратный вызов для изменения состояния DHCP-клиента и проверить, находится ли DHCP-клиент в состоянии NX_DHCP_STATE_BOUND. Дополнительные сведения о настройке функции обратного вызова для изменения состояния см. в описании функции *nx_dhcp_state_change_notify*.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на блок управления DHCP.

- **interface_index**: индекс интерфейса для получения IP-адреса.  

- **server_address**: указатель на IP-адрес сервера.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): адрес DHCP-сервера возвращен.

- **NX_DHCP_NO_INTERFACES_ENABLED** (0xA5): протокол DHCP не включен ни для одного интерфейса.

- **NX_DHCP_NOT_BOUND** (0x94): DHCP-клиент не привязан.

- NX_PTR_ERROR (0x16): недопустимый указатель DHCP.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

- NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. 
/* void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter. */
    state_changes++;

    /* Get the DHCP server IP address on interface 1 */
    if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
    {
            status = nx_dhcp_interface_server_address_get(&dhcp_0, 1, 
                                                    &server_address);
    }
```

## <a name="nx_dhcp_set_interface_index"></a>nx_dhcp_set_interface_index

Задание сетевого интерфейса для экземпляра DHCP.

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_set_interface_index(NX_DHCP *dhcp_ptr, UINT index);
```

### <a name="description"></a>Описание

Эта служба задает сетевой интерфейс для подключения экземпляра DHCP к DHCP-серверу, когда для DHCP-клиента настроен один сетевой интерфейс.

По умолчанию DHCP-клиент выполняется на основном интерфейсе. Чтобы запустить DHCP-клиент на дополнительном интерфейсе, с помощью этой службы установите дополнительный интерфейс в качестве интерфейса DHCP-клиента. Приложение должно предварительно зарегистрировать указанный интерфейс в экземпляре IP с помощью службы *nx_ip_interface_attach*.

Эта служба предназначена для приложений, которые будут запускать DHCP-клиент только на одном интерфейсе. Дополнительные сведения о запуске DHCP на нескольких интерфейсах см. в описании службы *nx_dhcp_interface_enable*.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на блок управления DHCP.  

- **index**: индекс сетевого интерфейса устройства.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): интерфейс успешно задан.

- **NX_INVALID_INTERFACE** (0x4C): недопустимый сетевой интерфейс.

- **NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3): для интерфейса включен протокол DHCP.

- **NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7): доступная запись отсутствует.

- NX_PTR_ERROR (0x16): недопустимый указатель DHCP.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Set the DHCP Client interface to the secondary interface (index 1). */
status =  nx_dhcp_set_interface_index(&my_dhcp, 1);
/* If status is NX_SUCCESS a DHCP interface was successfully set. */
```

## <a name="nx_dhcp_start"></a>nx_dhcp_start

Запуск обработки DHCP.

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_start(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Описание

Эта служба запускает обработку DHCP на всех интерфейсах, для которых включен протокол DHCP. По умолчанию протокол DHCP включен для основного интерфейса, когда приложение вызывает *nx_dhcp_create*.

Чтобы проверить, привязан ли экземпляр IP к IP-адресу на интерфейсе DHCP-клиента, используйте *nx_ip_status_check* для подтверждения допустимости IP-адреса.

Если протокол DHCP уже выполняется на других интерфейсах, эта служба не повлияет на них.

Чтобы запустить DHCP на определенном интерфейсе, когда включено несколько интерфейсов, используйте службу *nx_dhcp_interface_start*.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): протокол DHCP успешно запущен.  

- **NX_DHCP_ALREADY_STARTED** (0x93): протокол DHCP уже запущен.

- NX_PTR_ERROR (0x16): недопустимый указатель DHCP.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Start the DHCP processing for this IP instance. */
status =  nx_dhcp_start(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully started. */
```

## <a name="nx_dhcp_interface_start"></a>nx_dhcp_interface_start

Запуск обработки DHCP на указанном интерфейсе.

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_interface_start(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a>Описание

Эта служба запускает обработку DHCP на указанном интерфейсе, если для него включен протокол DHCP. Дополнительные сведения о включении протокола DHCP на интерфейсе см. в описании службы *nx_dhcp_interface_enable()* . По умолчанию протокол DHCP включен для основного интерфейса, когда приложение вызывает *nx_dhcp_create*.

Если нет других интерфейсов, на которых выполняется DHCP-клиент, эта служба запустит или возобновит выполнение потока DHCP-клиента и (повторно) активирует таймер DHCP-клиента.  
  
Приложение должно использовать *nx_ip_status_check*, чтобы проверить, получен ли IP-адрес.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.

- **Interface_index**: индекс, по которому следует запустить DHCP-клиент.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): протокол DHCP успешно запущен.  

- **NX_DHCP_ALREADY_STARTED** (0X93): экземпляр DHCP уже запущен.

- NX_PTR_ERROR (0x16): недопустимый указатель DHCP.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.

- NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Start the DHCP processing for this IP instance on interface 1. */
status =  nx_dhcp_interface_start(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully started. */
```

## <a name="nx_dhcp_state_change_notify"></a>nx_dhcp_state_change_notify

Задание функции обратного вызова для изменения состояния DHCP.

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_state_change_notify(
          NX_DHCP *dhcp_ptr, 
          VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                           UCHAR new_state));
```

### <a name="description"></a>Описание

Эта служба регистрирует указанную функцию обратного вызова dhcp_state_change_notify для уведомления приложения об изменениях состояния DHCP. Функция обратного вызова предоставляет состояние, в которое перешел DHCP-клиент.

Ниже приведены значения, связанные с различными состояниями DHCP.

| Состояние                             | Значение |
|-----------------------------------|-------|
| NX\_DHCP\_STATE\_BOOT             | 1     |
| NX\_DHCP\_STATE\_INIT             | 2     |
| NX\_DHCP\_STATE\_SELECTING        | 3     |
| NX\_DHCP\_STATE\_REQUESTING       | 4     |
| NX\_DHCP\_STATE\_BOUND            | 5     |
| NX\_DHCP\_STATE\_RENEWING         | 6     |
| NX\_DHCP\_STATE\_REBINDING        | 7     |
| NX_DHCP_STATE_FORCERENEW          | 8     |
| NX\_DHCP\_STATE\_ADDRESS\_PROBING | 9     |


### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.

- **dhcp_state_change_notify**: указатель функции обратного вызова для изменения состояния.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): обратный вызов успешно задан.  

- NX_PTR_ERROR (0x16): недопустимый указатель DHCP.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки, инициализация.

### <a name="example"></a>Например, .

```C
/* Register the “my_state_change” function to be called on any DHCP state change, 
   assuming DHCP has alreadybeen created. */
status =  nx_dhcp_state_change_notify(&my_dhcp, my_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered. */
```

## <a name="nx_dhcp_interface_state_change_notify"></a>nx_dhcp_interface_state_change_notify

Задание функции обратного вызова для изменения состояния DHCP на указанном интерфейсе.

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_interface_state_change_notify(
              NX_DHCP *dhcp_ptr, 
              UINT interface_index,
              VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                               UINT interface_index,
                                               UCHAR new_state));
```

### <a name="description"></a>Описание

Эта служба регистрирует указанную функцию обратного вызова для уведомления приложения об изменениях состояния DHCP. Входные аргументы функции обратного вызова — это индекс интерфейса и состояние, в которое DHCP-клиент перешел на этом интерфейсе.

Дополнительные сведения о функциях изменения состояния см. в описании функции *nx_dhcp_state_change_notify()* .

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.

- **dhcp_interface_state_change_notify**: указатель функции обратного вызова приложения.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): обратный вызов успешно задан.  

- NX_PTR_ERROR (0x16): недопустимый указатель DHCP.

### <a name="allowed-from"></a>Допустимые источники

Потоки, инициализация.

### <a name="example"></a>Например, .

```C
/* Register the “my_state_change” function to be called on any DHCP state 
   change, assuming DHCP has alreadybeen created. */

void dhcp_interstate_state_change(NX_DHCP *dhcp_ptr, UINT iface_index, 
                                 UCHAR new_state);


status =  nx_dhcp_interstate_state_change_notify(&my_dhcp,  
                                                 dhcp_interstate_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered. */
```

## <a name="nx_dhcp_stop"></a>nx_dhcp_stop

Остановка обработки DHCP.

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_stop(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Описание

Эта служба останавливает обработку DHCP на всех интерфейсах, на которых она запущена. Если протокол DHCP не обрабатывается ни одним интерфейсом, эта служба приостанавливает поток DHCP-клиента и отключает таймер DHCP-клиента.

Чтобы остановить обработку DHCP на определенном интерфейсе, когда протокол DHCP включен для нескольких интерфейсов, используйте службу *nx_dhcp_interface_stop*.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): протокол DHCP успешно остановлен.

- **NX_DHCP_NOT_STARTED** (0x96): экземпляр DHCP не запущен.

- NX_PTR_ERROR (0x16): недопустимый указатель DHCP.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Stop the DHCP processing for this IP instance. */
status =  nx_dhcp_stop(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully stopped. */
```

## <a name="nx_dhcp_interface_stop"></a>nx_dhcp_interface_stop

Остановка обработки DHCP на указанном интерфейсе.

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_interface_stop(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a>Описание

Эта служба останавливает обработку DHCP на указанном интерфейсе, если она запущена. Если нет других интерфейсов, использующих DHCP, поток и таймер DHCP приостанавливаются.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.

- **Interface_index**: интерфейс, для которого необходимо остановить обработку DHCP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): протокол DHCP успешно остановлен.

- **NX_DHCP_NOT_STARTED** (0x96): обработка DHCP не запущена.

- NX_PTR_ERROR (0x16): недопустимый указатель DHCP.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.

- NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Stop DHCP processing for this IP instance on interface 1. */
status =  nx_dhcp_interface_stop(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully stopped. */
```

## <a name="nx_dhcp_user_option_retrieve"></a>nx_dhcp_user_option_retrieve

Получение параметра DHCP из последнего ответа сервера.

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_user_option_retrieve(NX_DHCP *dhcp_ptr, 
            UINT request_option, UCHAR *destination_ptr, 
            UINT *destination_size);
```

### <a name="description"></a>Описание

Эта служба извлекает указанный параметр DHCP из буфера параметров DHCP на первом интерфейсе с включенным протоколом DHCP, найденным в записи DHCP-клиента. В случае успешного выполнения данные параметра копируются в указанный буфер.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.  

- **request_option**: параметр DHCP согласно документам RFC. Ознакомьтесь с параметром NX_DHCP_OPTION в файле *nxd_dhcp_client.h*.

- **destination_ptr**: указатель на место назначения для строки ответа.  

- **destination_size**: указатель на размер места назначения и, при возвращении, место назначения для размещения числа возвращенных байтов.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): параметр успешно получен.  

- **NX_DHCP_NOT_BOUND** (0x94): DHCP-клиент не привязан.

- **NX_DHCP_NO_INTERFACES_ENABLED** (0xA5): протокол DHCP не включен ни для одного интерфейса.

- **NX_DHCP_DEST_TO_SMALL** (0x95): размер места назначения слишком мал для сохранения ответа.

- **NX_DHCP_PARSE_ERROR** (0x97): параметр DHCP не найден в ответе сервера.

- NX_PTR_ERROR (0x16): недопустимый указатель ввода.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server. */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_user_option_retrieve(&my_dhcp, NX_DHCP_OPTION_DNS_SVR,
        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string. */
```

## <a name="nx_dhcp_interface_user_option_retrieve"></a>nx_dhcp_interface_user_option_retrieve

Получение параметра DHCP из последнего ответа сервера на указанном интерфейсе.

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_interface_user_option_retrieve(NX_DHCP *dhcp_ptr,
                  UINT interface_index, 
            UINT request_option, UCHAR *destination_ptr, 
            UINT *destination_size);
```

### <a name="description"></a>Описание

Эта служба извлекает указанный параметр DHCP из буфера параметров DHCP на указанном интерфейсе, если для него включен протокол DHCP. В случае успешного выполнения данные параметра копируются в указанный буфер.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.

- **interface_index**: индекс, по которому извлекается указанный параметр.  

- **request_option**: параметр DHCP согласно документам RFC. Ознакомьтесь с параметром NX_DHCP_OPTION в файле *nxd_dhcp_client.h*.  

- **destination_ptr**: указатель на место назначения для строки ответа.  

- **destination_size**: указатель на размер места назначения и, при возвращении, место назначения для размещения числа возвращенных байтов.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): параметр успешно получен.  

- **NX_DHCP_NOT_BOUND** (0x94): IP-адрес не назначен.

- **NX_DHCP_DEST_TO_SMALL** (0x95): слишком маленький буфер.

- **NX_DHCP_PARSE_ERROR** (0x97): параметр DHCP не найден в ответе сервера.

- NX_PTR_ERROR (0x16): недопустимый указатель DHCP.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.

- NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server on the prmary interface. */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_interface_user_option_retrieve(&my_dhcp, 0, NX_DHCP_OPTION_DNS_SVR,
        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string. */
```

## <a name="nx_dhcp_user_option_convert"></a>nx_dhcp_user_option_convert

Преобразование четырех байт в значение ULONG.

### <a name="prototype"></a>Прототип

```C
ULONG nx_dhcp_user_option_convert(UCHAR *option_string_ptr);
```

### <a name="description"></a>Описание

Эта служба преобразовывает четыре символа, на которые указывает option_string_ptr, в длинное целое число без знака. Она особенно удобна при наличии IP-адресов.

### <a name="input-parameters"></a>Входные параметры

- **option_string_ptr**: указатель на ранее извлеченную строку параметра.

### <a name="return-values"></a>Возвращаемые значения

- **value**: значение первых четырех байт.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
UCHAR  dns_ip_string[4];
ULONG  dns_ip;

/* Convert the first four bytes of “dns_ip_string” to an actual IP
address in “dns_ip.”  */
dns_ip=  nx_dhcp_user_option_convert(dns_ip_string);

/* If status is NX_SUCCESS the DNS IP address is in “dns_ip.”  */
```

## <a name="nx_dhcp_user_option_add_callback_set"></a>nx_dhcp_user_option_add_callback_set

Задание функции обратного вызова для добавления параметров, предоставленных пользователем.

### <a name="prototype"></a>Прототип

```C
ULONG nx_dhcp_user_option_add_callbcak_set(NX_DHCP *dhcp_ptr, 
    UINT (*dhcp_user_option_add)(NX_DHCP *dhcp_ptr, 
                                 UINT iface_index, 
                                 UINT message_type, 
                                 UCHAR *user_option_ptr, 
                                 UINT *user_option_length));
```

### <a name="description"></a>Описание

Эта служба регистрирует указанную функцию обратного вызова для добавления предоставленных пользователем параметров.

Если эта функция обратного вызова задана, приложения могут добавлять предоставленные пользователем параметры в пакет по iface_index и message_type.

> [!NOTE]
> Подпрограмма пользователя. При добавлении параметров, предоставляемых пользователем, приложения должны соблюдать формат параметров DHCP. Общий размер пользовательских параметров должен быть не больше user_option_length. Значение user_option_length должно обновляться в соответствии с реальной длиной параметров. Если параметры добавлены успешно, возвращается значение NX_TRUE. В противном случае возвращается значение NX_FALSE.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.

- **dhcp_user_option_add**: указатель на функцию добавления пользовательских параметров.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): обратный вызов успешно задан.

- NX_PTR_ERROR (0x16): недопустимый указатель.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Register the “my_dhcp_user_option_add” function to be called when add DHCP
options, assuming DHCP has already been created. */

status =  nx_dhcp_user_option_add_callback_set(&my_dhcp, my_dhcp_user_option_add);

/* If status is NX_SUCCESS the callback function was successfully registered. */
```
