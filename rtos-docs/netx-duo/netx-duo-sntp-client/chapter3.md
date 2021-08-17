---
title: Глава 3. Описание служб клиента SNTP для NetX для ОСРВ Azure
description: Эта глава содержит описание всех служб клиента SNTP для NetX Duo, перечисленных ниже в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7aee18642e480ec61488515164c8a6816753dca86eb8f6d146ea22d4956e037a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791675"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-sntp-client-services"></a>Глава 3. Описание служб клиента SNTP для NetX для ОСРВ Azure

Эта глава содержит описание всех служб клиента SNTP для NetX Duo для ОСРВ Azure, перечисленных ниже в алфавитном порядке.

В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки ошибок API, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.

- **nx_sntp_client_create**: *создание клиента SNTP*
- **nx_sntp_client_delete**: *удаление клиента SNTP*
- **nx_sntp_client_get_local_time**: *получение местного времени клиента SNTP*
- **nx_sntp_client_get_local_time_extended**: *получение местного времени клиента SNTP*
- **nx_sntp_client_initialize_broadcast**: *инициализация клиента для широковещательной рассылки по IPv4*
- **nxd_sntp_client_initialize_broadcast**: *инициализация клиента для широковещательной рассылки по IPv6 или IPv4*
- **nx_sntp_client_initialize_unicast**: *инициализация клиента для одноадресной передачи данных по IPv4*
- **nxd_sntp_client_initialize_unicast**: *инициализация клиента для одноадресной передачи данных по IPv4 или IPv6*
- **nx_sntp_client_receiving_udpates**: *клиент в настоящее время получает допустимые обновления SNTP*
- **nx_sntp_client_request_unicast_time**: *отправка одноадресного запроса непосредственно на NTP-сервер*
- **nx_sntp_client_run_broadcast**: *выполнение клиента в широковещательном режиме*
- **nx_sntp_client_run_unicast**: *выполнение клиента в одноадресном режиме*
- **nx_sntp_client_set_local_time**: *настройка исходного местного времени для клиента SNTP*
- **nx_sntp_client_set_time_update_notify**: *настройка обратного вызова для обновления SNTP*
- **nx_sntp_client_stop**: *остановка потока клиента SNTP*
- **nx_sntp_client_utility_display_date_and_time**: *отображение времени NTP в секундах*
- **nx_sntp_client_utility_msecs_to_fraction**: *преобразование миллисекунд в дробный компонент NTP*
- **nx_sntp_client_utility_usecs_to_fraction**: *преобразование микросекунд в дробный компонент NTP*
- **nx_sntp_client_utility_fraction_to_usecs**: *преобразование дробного компонента NTP в микросекунды*


## <a name="nx_sntp_client_create"></a>nx_sntp_client_create

Создание клиента SNTP

### <a name="prototype"></a>Прототип

```C
UINT nx_sntp_client_create(NX_SNTP_CLIENT *client_ptr, NX_IP *ip_ptr,  
                                     UINT iface_index, 
                                     NX_PACKET_POOL *packet_pool_ptr, 
UINT (*leap_second_handler)(NX_SNTP_CLIENT *client_ptr, 
                                        UINT indicator), 
UINT (*kiss_of_death_handler)(NX_SNTP_CLIENT *client_ptr, 
                               NX_SNTP_TIME_MESSAGE *server_time_msg),
VOID (random_number_generator)(struct NX_SNTP_CLIENT_STRUCT 
                                *client_ptr, ULONG *rand));

```

### <a name="description"></a>Описание

Эта служба создает экземпляр клиента SNTP.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом SNTP.

- **ip_ptr**: указатель на экземпляр IP-адреса для клиента.

- **iface_index**: индекс сетевого интерфейса SNTP.

- **packet_pool_ptr**: указатель на пул пакетов клиента.

- **leap_second_handler**: обратный вызов, позволяющий приложению отреагировать на предстоящее применение корректировочной секунды.

- **kiss_of_death_handler**: обратный вызов, позволяющий приложению отреагировать на получение пакета KoD (Kiss of Death).

- **random_number_generator**: обратный вызов к службе создания случайных чисел.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): успешное создание клиента.

- **NX_SNTP_INSUFFICIENT_PACKET_PAYLOAD** (0xD2A): недопустимые входные данные, кроме указателей.

- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

- NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```C
/* Create the SNTP Client on the primary interface. */
UINT iface_index = 0;
status =  nx_sntp_client_create(&demo_client, 
                     iface_index, &client_ip, 
&client_packet_pool, leap_second_handler, 
                    kiss_of_death_handler, 
NULL /* no random_number_generator callback */);

/* If status is NX_SUCCESS an SNTP Client instance was successfully
   created.  */

```

## <a name="nx_sntp_client_delete"></a>nx_sntp_client_delete

Удаление клиента SNTP

### <a name="prototype"></a>Прототип

```C
UINT nx_sntp_client_delete(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет экземпляр клиента SNTP.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом SNTP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): успешное создание клиента.

- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Delete the SNTP Client. */
status =  nx_sntp_client_delete(&demo_client);

/* If status is NX_SUCCESS an SNTP Client 
   instance was successfully deleted.  */

```

## <a name="nx_sntp_client_get_local_time"></a>nx_sntp_client_get_local_time

Получение местного времени клиента SNTP

### <a name="prototype"></a>Прототип

```C
UINT nx_sntp_client_get_local_time(NX_SNTP_CLIENT *client_ptr , 
                                                ULONG *seconds, 
                                                ULONG *fraction, 
                                                CHAR *buffer);

```

### <a name="description"></a>Описание

Эта служба получает местное время клиента SNTP и принимает входной указатель на буфер параметров, позволяющий получить данные в формате строкового сообщения.

использовать эту службу больше не рекомендуется. Мы рекомендуем разработчикам перейти на службу *nx_sntp_client_get_local_time_extended*().

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом SNTP.

- **seconds**: указатель на секунды местного времени.

- **fraction**: дробный компонент местного времени.

- **buffer**: указатель на буфер для записи данных о времени.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): успешное создание клиента.

- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Get the SNTP Client local time without the 
   string message option. */

ULONG base_seconds;
ULONG base_fraction;

status =  nx_sntp_client_get_local_time(&demo_client, 
                                       &base_seconds, 
                                       &base_fraction, 
                                       NX_NULL);
/* If status is NX_SUCCESS an SNTP Client time was successfully
   retrieved.  */

```

## <a name="nx_sntp_client_get_local_time_extended"></a>nx_sntp_client_get_local_time_extended

Получение местного времени клиента SNTP в расширенном формате

### <a name="prototype"></a>Прототип

```C
UINT nx_sntp_client_get_local_time_extended(
                 NX_SNTP_CLIENT *client_ptr,
                 ULONG *seconds, 
                 ULONG *fraction, 
                 CHAR *buffer
                 UINT buffer_size);

```

### <a name="description"></a>Описание

Эта служба получает местное время клиента SNTP в расширенном формате и принимает входной указатель на буфер параметров, позволяющий получить данные в формате строкового сообщения.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом SNTP.

- **seconds**: указатель на секунды местного времени.

- **fraction**: указатель на дробный компонент.

- **buffer**: указатель на буфер для записи данных о времени.

- **buffer_size**: длина буфера.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): успешное создание клиента.

- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект службы.

- NX_SIZE_ERROR (0x09): сбой проверки размера буфера.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Get the SNTP Client local time without the 
   string message option. */

#define BUFSIZE 50

ULONG seconds;
ULONG fraction;
CHAR  buffer[BUFSIZE];

status =  nx_sntp_client_get_local_time_extended(&demo_client, 
                                                &seconds, 
                                                &fraction, 
                                                buffer, 
                                                BUFSIZE);

/* If status is NX_SUCCESS an SNTP Client 
   time was successfully retrieved.  */

```

## <a name="nx_sntp_client_initialize_broadcast"></a>nx_sntp_client_initialize_broadcast

Инициализация клиента для широковещательной рассылки

### <a name="prototype"></a>Прототип

```C
UINT nx_sntp_client_initialize_broadcast(NX_SNTP_CLIENT *client_ptr,
                                    ULONG multicast_server_address, 
                                    ULONG broadcast_time_servers);


```

### <a name="description"></a>Описание

Эта служба инициализирует клиент для широковещательной рассылки, позволяя задать IP-адрес сервера SNTP, настроить параметры запуска и время ожидания SNTP. Если оба адреса (многоадресной и широковещательной рассылки) не равны NULL, выбирается адрес многоадресной рассылки. Если оба этих адреса равны NULL, возвращается ошибка. Обратите внимание, что для серверов поддерживаются только IPv4-адреса.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом SNTP.

- **multicast_server_address**: адрес SNTP для многоадресной рассылки.

- **broadcast_time_server**: адрес сервера SNTP для широковещательной рассылки.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): успешное создание клиента.

- **NX_INVALID_PARAMETERS** (0x4D): недопустимые входные данные, кроме указателей.

- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```C
/* Initialize the client for broadcast operation.  */
status =  nx_sntp_client_initialize_broadcast(client_ptr,0x0,
                            NX_NULL, IP_ADDRESS(192,2,2,255);

/* If status is NX_SUCCESS the Client 
   was successfully initialized.  */

```

## <a name="nxd_sntp_client_initialize_broadcast"></a>nxd_sntp_client_initialize_broadcast

Инициализация клиента для широковещательной рассылки по IPv4 или IPv6

### <a name="prototype"></a>Прототип

```C
UINT nxd_sntp_client_initialize_broadcast(NX_SNTP_CLIENT *client_ptr,
                            NXD_ADDRESS *multicast_server_address, 
                            NXD_ADDRESS *broadcast_server_address);

```

### <a name="description"></a>Описание

Эта служба инициализирует клиент для операции широковещательной рассылки, позволяя задать IP-адрес сервера SNTP, настроить параметры запуска и время ожидания SNTP. Если оба указателя (многоадресной и широковещательной рассылки) не равны NULL, выбирается адрес многоадресной рассылки. Если оба этих указателя равны NULL, возвращается ошибка. Поддерживаются типы адресов IPv4 и IPv6. Обратите внимание, что IPv6 не поддерживает широковещательную рассылку. Если указатель на широковещательный адрес имеет значение IPv6, возвращается ошибка.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом SNTP.

- **multicast_server_address**: адрес многоадресной рассылки сервера SNTP.

- **broadcast_server_address**: адрес широковещательной рассылки сервера SNTP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): клиент успешно инициализирован.

- NX_SNTP_PARAM_ERROR (0xD0D): недопустимые входные данные, кроме указателей.

- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект службы.


### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```C
/* Initialize the client for broadcast operation.  */
NXD_ADDRESS broadcast_server;

Broadcast_server.nxd_ip_address = NX_IP_VERSION_V6;
Broadcast_server.nxd_ip_address.v6[0] = 0x20010db1;
Broadcast_server.nxd_ip_address.v6[1] = 0x0f101;
Broadcast_server.nxd_ip_address.v6[2] = 0x0;
Broadcast_server.nxd_ip_address.v6[3] = 0x101;

status =  nxd_sntp_client_initialize_broadcast(client_ptr,0x0,
                                  NX_NULL, &broadcast_server)


/* If status is NX_SUCCESS the Client 
   was successfully initialized.  */

```

## <a name="nx_sntp_client_initialize_unicast"></a>nx_sntp_client_initialize_unicast

Настройка клиента SNTP для работы в одноадресном режиме

### <a name="prototype"></a>Прототип

```C
UINT nx_sntp_client_initialize_unicast(NX_SNTP_CLIENT * client_ptr, 
                                        ULONG unicast_time_server);

```
### <a name="description"></a>Описание

Эта служба инициализирует клиент для одноадресной передачи данных, позволяя задать IP-адрес сервера SNTP, настроить параметры запуска и время ожидания SNTP. Обратите внимание, что для серверов поддерживаются только IPv4-адреса.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом SNTP.

- **unicast_time_server**: IP-адрес сервера SNTP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): клиент успешно инициализирован.

- NX_INVALID_PARAMETERS (0x4D): недопустимые входные данные, кроме указателей.

- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```C
/* Initialize the Client for unicast operation.  */
status =  nx_sntp_client_initialize_unicast(&client_ptr, 
                                 IP_ADDRESS(192,2,2,1));


/* If status is NX_SUCCESS the Client 
   is initialized for unicast operation.  */

```


## <a name="nxd_sntp_client_initialize_unicast"></a>nxd_sntp_client_initialize_unicast

Настройка клиента SNTP для работы в одноадресном режиме IPv4 или IPv6

### <a name="prototype"></a>Прототип

```C
UINT nxd_sntp_client_initialize_unicast(NX_SNTP_CLIENT * client_ptr, 
                                  NXD_ADDRESS *unicast_time_server);

```

### <a name="description"></a>Описание

Эта служба инициализирует клиент для одноадресной передачи данных, позволяя задать IP-адрес сервера SNTP, настроить параметры запуска и время ожидания SNTP. Поддерживаются типы адресов IPv4 и IPv6.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом SNTP.

- **unicast_time_server**: IP-адрес сервера SNTP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): клиент успешно инициализирован.

- NX_INVALID_PARAMETERS (0x4D): недопустимые входные данные, кроме указателей.

- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```C
/* Initialize the Client for unicast operation.  */
NXD_ADDRESS unicast_server;

unicast _server.nxd_ip_address = NX_IP_VERSION_V6;
unicast _server.nxd_ip_address.v6[0] = 0x20010db1;
unicast _server.nxd_ip_address.v6[1] = 0x0f101;
unicast _server.nxd_ip_address.v6[2] = 0x0;
unicast _server.nxd_ip_address.v6[3] = 0x101;

status =  nxd_sntp_client_initialize_unicast(&client_ptr, 
                                        *unicast_server); 


/* If status is NX_SUCCESS the Client 
   is initialized for unicast operation.  */

```

## <a name="nx_sntp_client_receiving_updates"></a>nx_sntp_client_receiving_updates

Сведения о том, получает ли клиент допустимые обновления

### <a name="prototype"></a>Прототип

```C
UINT nx_sntp_client_receiving_updates(NX_SNTP_CLIENT *client_ptr, 
                                           UINT *receive_status);

```

### <a name="description"></a>Описание

Эта служба сообщает, получает ли клиент допустимые обновления SNTP. Если превышен максимальный промежуток времени без допустимого обновления или превышено ограничение на количество последовательных недопустимых обновлений, в качестве состояния получения возвращается значение false. Обратите внимание, что клиент SNTP будет работать и дальше. Если приложению нужно перезапустить клиент SNTP с другим сервером в одноадресном, широковещательном или многоадресном режиме, придется отключить текущий клиент SNTP с помощью службы *nx_sntp_client_stop* и повторно инициализировать клиент с помощью любой из служб инициализации, указав другой сервер.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом SNTP.

- **receive_status**: указатель на сведения о том, получает ли клиент допустимые обновления.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): клиент успешно получил состояние обновления.

- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```C
/* Determine if the SNTP Client is receiving valid udpates.  */
UINT receive_status;

status =  nx_sntp_client_receiving_updates(client_ptr, 
                                     &receive_status);

/* If status is NX_SUCCESS and receive_status is NX_TRUE, 
   the client is currently receiving valid updates.  */

```

## <a name="nx_sntp_client_request_unicast_time"></a>nx_sntp_client_request_unicast_time

Отправка одноадресного запроса непосредственно на сервер NTP


### <a name="prototype"></a>Прототип

```C
UINT nx_sntp_client_request_unicast_time(NX_SNTP_CLIENT *client_ptr, 
                                                  UINT wait_option);
```

### <a name="description"></a>Описание

Эта служба позволяет приложению асинхронно отправить одноадресный запрос серверу NTP напрямую из задачи потока клиента SNTP. Параметр wait задает время ожидания ответа. Если запрос выполнен успешно, приложение может использовать другие службы клиента SNTP для получения последнего времени. Дополнительные сведения см. в разделе **Асинхронные одноадресные запросы SNTP**.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом SNTP.

- **Wait_option**: время ожидания ответа NTP, выраженное в тактах таймера.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): клиент успешно отправляет и получает обновления в одноадресном режиме.

- **NX_SNTP_CLIENT_NOT_STARTED** (0xD0B): поток клиента не запущен.

- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Determine if the SNTP Client is receiving valid udpates.  */
UINT receive_status;

status =  nx_sntp_client_request_unicast_time(client_ptr, 400);

/* If status is NX_SUCCESS and receive_status is NX_TRUE, 
   the client is received a valid response to the unicast request.  */

```

## <a name="nx_sntp_client_run_broadcast"></a>nx_sntp_client_run_broadcast

Запуск клиента в широковещательном режиме

### <a name="prototype"></a>Прототип

```C
UINT nx_sntp_client_run_broadcast(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a>Описание

Эта служба запускает клиент в широковещательном режиме, то есть в режиме ожидания широковещательной передачи данных от сервера SNTP. При получении допустимого широковещательного сообщения SNTP сбрасываются счетчики максимального времени ожидания сведений от клиента SNTP и последовательных недопустимых сообщений. Если любое из этих ограничений превышено, клиент SNTP устанавливает для сервера состояние "недопустимо", но при этом продолжает ожидать обновления. Приложение может получить состояние сервера от задачи клиента SNTP, в случае наличия проблем остановить клиент SNTP и повторно инициализировать его с другим адресом широковещательной рассылки SNTP. Также можно переключиться на одноадресный сервер SNTP.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом SNTP.

### <a name="return-values"></a>Возвращаемые значения

- **status**: фактическое состояние завершения.

- **NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C): клиент уже запущен.

- **NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01): клиент не инициализирован.

- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Start Client running in broadcast mode.  */
status =  nx_sntp_client_run_broadcast(client_ptr);

/* If status is NX_SUCCESS, the client is successfully started.  */

```

## <a name="nx_sntp_client_run_unicast"></a>nx_sntp_client_run_unicast

Запуск клиента в одноадресном режиме

### <a name="prototype"></a>Прототип

```C
UINT nx_sntp_client_run_unicast(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a>Описание

Эта служба запускает клиент в одноадресном режиме, в котором он периодически отправляет одноадресный запрос на сервер SNTP для обновления времени. При получении допустимого сообщения SNTP сбрасываются счетчики максимального времени ожидания сведений от клиента SNTP, начального интервала опроса и последовательных недопустимых сообщений. Если любое из этих ограничений превышено, клиент SNTP устанавливает для сервера состояние "недопустимо", но при этом продолжает опрашивать сервер и получать обновления. Приложение может получить состояние сервера от задачи клиента SNTP, в случае наличия проблем остановить клиент SNTP и повторно инициализировать его с другим адресом одноадресной передачи данных SNTP. Также можно переключиться на широковещательный сервер SNTP.

.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом SNTP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): клиент успешно запущен в одноадресном режиме.

- **NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C): клиент уже запущен.

- **NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01): клиент не инициализирован.

- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект службы.


### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Start the Client in unicast mode. */
status =  nx_sntp_client_run_unicast(client_ptr);

/* If status = NX_SUCCESS, the Client was successfully started.  */

```

## <a name="nx_sntp_client_set_local_time"></a>nx_sntp_client_set_local_time

Настройка местного времени клиента SNTP

### <a name="prototype"></a>Прототип

```C
UINT nx_sntp_client_set_local_time(NX_SNTP_CLIENT *client_ptr , 
                                ULONG seconds, ULONG fraction);

```

### <a name="description"></a>Описание

Эта служба задает полученное время в качестве местного времени для клиента SNTP в формате SNTP (секунды и дробный компонент, который обозначает доли секунды в шестнадцатеричном формате). Она предназначена для обновления местного времени клиента SNTP по данным от независимого источника, например часов реального времени. Протокол SNTP поддерживает обновление времени SNTP, чтобы показания локальных часов не отклонялись от истинного времени. Хотя этот режим и не рекомендуется, обновления времени с сервера SNTP могут являться единственным источником местного времени для клиента SNTP, если на устройстве приложения нет независимого источника времени.

Этот API также можно использовать для предоставления клиенту SNTP базового времени перед запуском потока клиента SNTP. Местное время клиента SNTP сравнивается с полученными обновлениями для проверки допустимости данных. При первом получении обновления может возникнуть очень большое несоответствие. Поэтому у клиента SNTP есть параметр, позволяющий игнорировать расхождение при первом обновлении. Это позволяет запустить клиент SNTP без указания базового времени. Входное значение времени можно получить от известных источников времени эпохи (доступны через Интернет), которое выражается в количестве секунд, прошедших с 1-го января 1900 года (эта дата актуальна до начала следующей эпохи, то есть до 2036 года).

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом SNTP.

- **seconds**: компонент секунд во входных данных времени.

- **fraction**: компонент с долей секунды в дробном формате SNTP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): местное время успешно задано.

- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Инициализация

### <a name="example"></a>Например, .

```C
/* Set the SNTP Client local time. */
base_seconds =  0xd2c50b71;
base_fraction = 0xa132db1e;

status =  nx_sntp_client_set_local_time(&demo_client, 
                                        base_seconds, 
                                        base_fraction);

/* If status is NX_SUCCESS an SNTP Client time 
   was successfully set.  */

```

## <a name="nx_sntp_client_set_time_update_notify"></a>nx_sntp_client_set_time_update_notify

Настройка обратного вызова для обновления SNTP

### <a name="prototype"></a>Прототип

```C
UINT nx_sntp_client_set_time_update_notify(NX_SNTP_CLIENT *client_ptr, 
                           VOID (time_update_cb)(NX_SNTP_TIME_MESSAGE 
                        *time_update_ptr, NX_SNTP_TIME *local_time)));

```

### <a name="description"></a>Описание

Эта служба задает обратный вызов, позволяющий оповестить приложение о получении допустимого обновления времени клиентом SNTP. Она передает полученное сообщение SNTP и местное время клиента SNTP (обычно они совпадают) в формате NTP. Приложение может напрямую применить данные NTP или вызвать службу *nx_sntp_client_utility_display_date_time* для преобразования времени в удобочитаемый формат.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом SNTP.

- **time_update_cb**: указатель на функцию обратного вызова.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): обратный вызов успешно задан.

- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Инициализация

### <a name="example"></a>Например, .

```C
/* Set the SNTP Client time update callback. */
VOID client_time_update_notify(NX_SNTP_TIME_MESSAGE *time_update_ptr, 
                                           NX_SNTP_TIME *local time);

NX_SNTP_CLIENT demo_client;


status = nx_sntp_client_set_time_update_notify(&demo_client, 
                                            time_update_cb);

/* If status is NX_SUCCESS an SNTP Client 
   time update callback was successfully set.  */

```

## <a name="nx_sntp_client_stop"></a>nx_sntp_client_stop

Остановка потока клиента SNTP

### <a name="prototype"></a>Прототип

```C
UINT nx_sntp_client_stop(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a>Описание

Эта служба останавливает поток клиента SNTP. Задачи потока клиента SNTP, который работает в бесконечном цикле, приостанавливаются при каждой итерации, чтобы передать другим службам контроль за состоянием клиента SNTP и позволить приложениям выполнять вызовы API на клиенте SNTP.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом SNTP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): поток клиента успешно остановлен.

- **NX_SNTP_CLIENT_NOT_STARTED** (0xDB): поток клиента SNTP не запущен.

- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```C
/* Stop the SNTP Client. */
status =  nx_sntp_client_stop(&demo_client);

/* If status is NX_SUCCESS an SNTP 
   Client instance was successfully stopped.  */

```

## <a name="nx_sntp_client_utility_display_date_time"></a>nx_sntp_client_utility_display_date_time

Преобразование времени NTP в строку даты и времени

### <a name="prototype"></a>Прототип

```C
UINT nx_sntp_client_utility_display_date_time (NX_SNTP_CLIENT 
                      *client_ptr, CHAR *buffer, UINT length);

```

### <a name="description"></a>Описание

Эта служба преобразует местное время клиента SNTP в формат даты "год, месяц, день" и возвращает эту дату в предоставленном буфере. Значение NX_SNTP_CURRENT_YEAR не обязано совпадать с годом в текущем времени клиента, но должно быть определено.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на клиент SNTP.

- **buffer**: указатель на буфер для хранения даты.

- **length**: размер входного буфера.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): успешное преобразование

- **NX_SNTP_ERROR_CONVERTING_DATETIME** (0xD08): значение NX_SNTP_CURRENT_YEAR не определено или местное время клиента не задано.

- **NX_SNTP_INVALID_DATETIME_BUFFER** (0xD07): недостаточная длина буфера.


### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```C
/* Convert and display the Client’s local time. */

status =  nx_sntp_client_utility_display_date_time(client_ptr , 
                                        buffer, sizeof(buffer));

/* If status is NX_SUCCESS, 
   date was successfully written to buffer.  */

```

## <a name="nx_sntp_client_utility_msecs_to_fraction"></a>nx_sntp_client_utility_msecs_to_fraction

Преобразование миллисекунд в дробный компонент NTP

### <a name="prototype"></a>Прототип

```C
UINT nx_sntp_client_utility_msecs_to_fraction (ULONG milliseconds,   
                                                 ULONG *fraction);

```

### <a name="description"></a>Описание

Эта служба преобразует миллисекунды из входных данных в дробный компонент NTP. Она предназначена для использования с приложениями, которые задают для клиента SNTP базовое время в формате, отличном от стандарта NTP (секунды и дробный компонент). Чтобы дробная часть была допустимой, число миллисекунд должно не превышать 1000.

### <a name="input-parameters"></a>Входные параметры

- **milliseconds**: количество миллисекунд для преобразования.

- **fraction**: указатель на миллисекунды, преобразованные в дробный компонент.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): успешное преобразование

- **NX_SNTP_OVERFLOW_ERROR** (0xD32): ошибка преобразования времени в дату.

- NX_SNTP_INVALID_TIME (0xD30): недопустимые входные данные SNTP.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```C
/* Convert the milliseconds to a fraction. */


status =  nx_sntp_client_utility_msecs_to_fraction(milliseconds, 
                                                     &fraction);

/* If status is NX_SUCCESS, 
   data was successfully converted.  */

```

## <a name="nx_sntp_client_utility_usecs_to_fraction"></a>nx_sntp_client_utility_usecs_to_fraction

Преобразование микросекунд в дробный компонент NTP

### <a name="prototype"></a>Прототип

```C
UINT nx_sntp_client_utility_usecs_to_fraction (ULONG microseconds,   
                                                 ULONG *fraction);

```
### <a name="description"></a>Описание

Эта служба преобразует микросекунды из входных данных в дробный компонент NTP. Она предназначена для использования с приложениями, которые задают для клиента SNTP базовое время в формате, отличном от стандарта NTP (секунды и дробный компонент). Чтобы дробная часть была допустимой, число микросекунд должно не превышать 1 000 000.

### <a name="input-parameters"></a>Входные параметры

- **microseconds**: количество микросекунд для преобразования.

- **fraction**: указатель на микросекунды, преобразованные в дробный компонент.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): успешное преобразование

- **NX_SNTP_OVERFLOW_ERROR** (0xD32): ошибка преобразования времени в дату.

- NX_SNTP_INVALID_TIME (0xD30): недопустимые входные данные SNTP.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```C
/* Convert the microseconds to a fraction. */


status =  nx_sntp_client_utility_msecs_to_fraction(microseconds, 
                                                     &fraction);

/* If status is NX_SUCCESS, data was successfully converted.  */

```

## <a name="nx_sntp_client_utility_fraction_to_usecs"></a>nx_sntp_client_utility_fraction_to_usecs

Преобразование дробного компонента NTP в микросекунды

### <a name="prototype"></a>Прототип

```C
UINT nx_sntp_client_utility_fraction_to_usecs (ULONG fraction,   
                                         ULONG *microseconds);

```

### <a name="description"></a>Описание

Эта служба преобразует дробный компонент NTP из входных данных в микросекунды.

### <a name="input-parameters"></a>Входные параметры

- **fraction**: дробный компонент для преобразования.

- **microseconds**: указатель на дробный компонент, преобразованный в микросекунды.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): успешное преобразование

- NX_SNTP_INVALID_TIME (0xD30): недопустимые входные данные SNTP.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Пример

```C
/* Convert the fraction to microseconds. */


status =  nx_sntp_client_utility_fraction_to_msecs(fraction, 
                                             &microseconds);

/* If status is NX_SUCCESS, data was successfully converted.  */
```