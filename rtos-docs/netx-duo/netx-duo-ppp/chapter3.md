---
title: Глава 3. Описание служб протокола PPP для NetX Duo для ОСРВ Azure
description: В этой главе приводится описание всех служб PPP для NetX Duo для ОСРВ Azure, которые перечислены ниже в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1174d7fdc470bc91278413d56948789cc210aab9d7389a5ecad5baf4f6ad7a7f
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798084"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-point-to-point-protocol-ppp-services"></a>Глава 3. Описание служб протокола PPP для NetX Duo для ОСРВ Azure

В этой главе приводится описание всех служб PPP для NetX Duo для ОСРВ Azure, которые перечислены ниже в алфавитном порядке.

В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки ошибок API, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.

- **nx_ppp_byte_receive**: *получение байта от подпрограммы обработки прерываний (ISR) последовательного порта*
- **nx_ppp_chap_challenge**: *создание запроса CHAP*
- **nx_ppp_chap_enable**: *включение проверки подлинности CHAP*
- **nx_ppp_create**: *создание экземпляра PPP*
- **nx_ppp_delete**: *удаление экземпляра PPP*
- **nx_ppp_dns_address_get**: *получение IP-адреса сервера DNS*
- **nx_ppp_dns_address_set**: *настройка IP-адреса сервера DNS*
- **nx_ppp_secondary_dns_address_get**: *получение IP-адреса вторичного сервера DNS*
- **nx_ppp_secondary_dns_address_set**: *задание IP-адреса вторичного сервера DNS*
- **nx_ppp_interface_index_get**: *получение индекса IP-интерфейса*
- **nx_ppp_ip_address_assign**: *назначение IP-адресов для IPCP*
- **nx_ppp_link_down_notify**: *оповещение приложения об отключении канала*
- **nx_ppp_link_up_notify**: *оповещение приложения о включении канала*
- **nx_ppp_nak_authentication_notify**: *оповещение приложения о получении пакета NAK при проверке подлинности*
- **nx_ppp_pap_enable**: *включение проверки подлинности PAP*
- **nx_ppp_ping_request**: *отправка запроса проверки связи LCP*
- **nx_ppp_raw_string_send**: *отправка строки без протокола PPP*
- **nx_ppp_restart**: *перезапуск обработки PPP*
- **nx_ppp_start**: *начало обработки PPP*
- **nx_ppp_status_get**: *получение текущего состояния PPP*
- **nx_ppp_stop**: *прекращение обработки PPP*
- **nx_ppp_packet_receive**: *получение пакета PPP*
- **nx_ppp_packet_send_set**: *настройка функции отправки пакета PPP*

## <a name="nx_ppp_byte_receive"></a>nx_ppp_byte_receive

Получение байта от ISR последовательного порта

### <a name="prototype"></a>Прототип

```c
UINT nx_ppp_byte_receive(NX_PPP *ppp_ptr, UCHAR byte);
```

### <a name="description"></a>Описание

Обычно эта служба вызывается в приложении из ISR драйвера последовательного порта, чтобы передать байт в канал PPP. При вызове эта подпрограмма помещает полученный байт в циклический буфер байтов и оповещает соответствующий поток PPP о необходимости обработки.

### <a name="input-parameters"></a>Входные параметры

- **ppp_ptr**: указатель на блок управления PPP
- **byte**: байт, полученный от устройства c последовательным интерфейсом

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное получение байта в PPP.
- **NX_PPP_BUFFER_FULL** (0xB1) — последовательный буфер PPP заполнен.
- NX_PTR_ERROR (0x07) — недопустимый указатель PPP.

### <a name="allowed-from"></a>Допустимые источники

Потоки, подпрограммы ISR

### <a name="example"></a>Например, .

```c
/* Notify “my_ppp” of a received byte. */
status =  nx_ppp_byte_receive(&my_ppp, new_byte);

/* If status is NX_SUCCESS the received byte was successfully
   buffered. */
```

## <a name="nx_ppp_chap_challenge"></a>nx_ppp_chap_challenge

Создание запроса CHAP

### <a name="prototype"></a>Прототип

```c
UINT nx_ppp_chap_challenge(NX_PPP *ppp_ptr);
```

### <a name="description"></a>Описание

Эта служба создает запрос CHAP, когда подключение PPP уже установлено и успешно работает. Это дает приложению возможность периодически контролировать подлинность в подключении. Если нужный ответ на запрос не поступает, канал PPP закрывается.

### <a name="input-parameters"></a>Входные параметры

- **ppp_ptr**: указатель на блок управления PPP

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — запрос PPP успешно инициирован.
- **NX_PPP_FAILURE** (0xB0) — недопустимый запрос PPP, CHAP включался только для ответа.
- **NX_NOT_IMPLEMENTED** (0x80) — логика CHAP была отключена с помощью NX_PPP_DISABLE_CHAP.
- NX_PTR_ERROR (0x07) — недопустимый указатель PPP.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Initiate a PPP challenge for instance “my_ppp”. */
status =  nx_ppp_chap_challenge(&my_ppp);

/* If status is NX_SUCCESS a CHAP challenge “my_ppp” was successfully 
initiated. */
```

## <a name="nx_ppp_chap_enable"></a>nx_ppp_chap_enable

Включение проверки подлинности CHAP

### <a name="prototype"></a>Прототип

```c
UINT nx_ppp_chap_enable(NX_PPP *ppp_ptr, 
                        UINT (*get_challenge_values)(CHAR *rand_value,CHAR *id,CHAR *name),
                        UINT (*get_responder_values)(CHAR *system,CHAR *name,CHAR *secret),
                        UINT (*get_verification_values)(CHAR *system,CHAR *name,CHAR *secret)); 
```

### <a name="description"></a>Описание

Эта служба включает протокол CHAP (Challenge-Handshake Authentication Protocol) для указанного экземпляра PPP.

Если определены указатели на функции ***get_challenge_values**_и_*_get_verification_values_**, CHAP является обязательным для этого экземпляра PPP. В противном случае CHAP активируется только по запросу другой стороны канала.

Ниже упоминаются несколько элементов данных, которые используются в обязательных функциях обратного вызова. Элементы данных *secret*, *name* и *system* должны иметь формат строк, оканчивающихся символом NULL, и размер, не превышающий значения NX_PPP_NAME_SIZE-1. Элемент данных *rand_value* должен иметь формат строки, оканчивающейся символом NULL, и размер, не превышающий значения NX_PPP_VALUE_SIZE-1. Элемент данных *id* имеет простой символьный тип без знака.

>[!NOTE]
> Эта функция должна вызываться после *nx_ppp_create*, но раньше nx_ip_create или *nx_ip_interface_attach*.

### <a name="input-parameters"></a>Входные параметры

- **ppp_ptr**: указатель на блок управления PPP
- **get_challenge_values**: указатель на функцию приложения, которая извлекает значения для создания запроса. Обратите внимание, что значения *rand_value*, *id* и *secret* должны быть скопированы в указанные места назначения.
- **get_responder_values**: указатель на функцию приложения, которая извлекает значения для ответа на запрос. Обратите внимание, что значения *system*, *name* и *secret* должны быть скопированы в указанные места назначения.
- **get_verification_values**: указатель на функцию приложения, которая извлекает значения для проверки ответа на запрос. Обратите внимание, что значения *system*, *name* и *secret* должны быть скопированы в указанные места назначения.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — PPP CHAP успешно включено.
- **NX_NOT_IMPLEMENTED** (0x80) — логика CHAP была отключена с помощью NX_PPP_DISABLE_CHAP.
- NX_PTR_ERROR (0x07) — недопустимый указатель PPP или указатель на функцию обратного вызова. Обратите внимание, что, если предоставлена функция *get_challenge_values*, необходимо предоставить и функцию *get_verification_values*.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

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
## <a name="nx_ppp_create"></a>nx_ppp_create

Создание экземпляра PPP

### <a name="prototype"></a>Прототип

```c
UINT  nx_ppp_create(NX_PPP *ppp_ptr, CHAR *name, NX_IP *ip_ptr, 
                    VOID *stack_memory_ptr, ULONG stack_size, 
                    UINT thread_priority, NX_PACKET_POOL *pool_ptr,
                    void (*ppp_invalid_packet_handler)(NX_PACKET *packet_ptr),
                    void (*ppp_byte_send)(UCHAR byte));
```

### <a name="description"></a>Описание

Эта служба создает экземпляр PPP для указанного экземпляра IP-адреса NetX. Эта функция должна вызываться до создания экземпляра IP-адреса для NetX.

>[!NOTE]
> Обычно считается, что IP-поток NetX следует создавать с более высоким приоритетом, чем у потока PPP. Дополнительные сведения об указании приоритета для IP-потока см. в описании службы *nx_ip_create*.

### <a name="input-parameters"></a>Входные параметры

- **ppp_ptr**: указатель на блок управления PPP
- **name**: имя экземпляра PPP
- **ip_ptr**: указатель на блок управления для еще не созданного экземпляра IP-адреса
- **stack_memory_ptr**: указатель на начало зоны стека для потока PPP
- **stack_size**: размер в байтах в стеке потока
- **pool_ptr**: указатель на пул пакетов по умолчанию
- **thread_priority**: приоритет внешних потоков PPP (1–31)
- **ppp_invalid_packet_handler**: указатель функции на обработчик приложения, который обрабатывает все пакеты, отличные от PPP Обычно PPP для NetX вызывает эту подпрограмму во время инициализации. Именно в ней приложение может реагировать на команды модема, а в среде Windows XP приложение PPP для NetX может запустить канал PPP, вернув ответ CLIENT SERVER на запрос CLIENT от ОС Windows XP.
- **ppp_byte_send**: указатель функции на подпрограмму приложения, которая обрабатывает последовательный байтовый вывод


### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — экземпляр PPP успешно создан.
- NX_PTR_ERROR (0x07) — недопустимый указатель функции на PPP, IP или байтовый вывод.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Create “my_ppp” for IP instance “my_ip”. */
status =  nx_ppp_create(&my_ppp, “my PPP”, &my_ip, stack_start, 1024, 2, 
                        &my_pool, my_invalid_packet_handler, my_out_byte);

/* If status is NX_SUCCESS the PPP instance was successfully
   created. */
```

## <a name="nx_ppp_delete"></a>nx_ppp_delete

Удаление экземпляра PPP

### <a name="prototype"></a>Прототип

```c
UINT nx_ppp_delete(NX_PPP *ppp_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет созданный ранее экземпляр PPP.

### <a name="input-parameters"></a>Входные параметры

- **ppp_ptr**: указатель на блок управления PPP

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — экземпляр PPP успешно удален.
- NX_PTR_ERROR (0x07) — недопустимый указатель PPP.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Delete PPP instance “my_ppp”. */
status =  nx_ppp_delete(&my_ppp);

/* If status is NX_SUCCESS the “my_ppp” was successfully deleted. */
```

## <a name="nx_ppp_dns_address_get"></a>nx_ppp_dns_address_get

Получение IP-адреса DNS-сервера

### <a name="prototype"></a>Прототип

```c
UINT nx_ppp_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a>Описание

Эта служба возвращает IP-адрес DNS-сервера, предоставленный одноранговым узлом в подтверждении IPCP. Если одноранговый узел не предоставил IP-адрес, возвращается значение 0.

### <a name="input-parameters"></a>Входные параметры

- **ppp_ptr**: указатель на блок управления PPP.
- **dns_address_ptr**: назначение для адреса DNS-сервера.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — адрес DNS-сервера успешно получен.
- **NX_PPP_NOT_ESTABLISHED** (0xB5) — не завершено согласование PPP с одноранговым узлом.
- NX_PTR_ERROR (0x07) — недопустимый указатель PPP.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="example"></a>Например, .

```c

ULONG  my_dns_address;

/* Get DNS Server address supplied by peer. */
status =  nx_ppp_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the DNS IP address – 
   if the peer supplied one. */
```

## <a name="nx_ppp_secondary_dns_address_get"></a>nx_ppp_secondary_dns_address_get

Получение IP-адреса дополнительного DNS-сервера

### <a name="prototype"></a>Прототип

```c
UINT nx_ppp_secondary_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a>Описание

Эта служба возвращает IP-адрес дополнительного DNS-сервера, предоставленный одноранговым узлом в подтверждении IPCP. Если одноранговый узел не предоставил IP-адрес, возвращается значение 0.

### <a name="input-parameters"></a>Входные параметры

- **ppp_ptr**: указатель на блок управления PPP
- **dns_address_ptr**: назначение для адреса дополнительного DNS-сервера

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — адрес DNS-сервера успешно получен.
- **NX_PPP_NOT_ESTABLISHED** (0xB5) — не завершено согласование PPP с одноранговым узлом.
- NX_PTR_ERROR (0x07) — недопустимый указатель PPP.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="example"></a>Например, .

```c
ULONG  my_dns_address;

/* Get secondary DNS Server address supplied by peer. */
status =  nx_ppp_secondary_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the secondary DNS Server address – if the peer supplied one. */
```

## <a name="nx_ppp_dns_address_set"></a>nx_ppp_dns_address_set

Задание IP-адреса основного DNS-сервера

### <a name="prototype"></a>Прототип

```c
UINT nx_ppp_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a>Описание

Эта служба задает IP-адрес DNS-сервера. Если одноранговый узел отправляет в состоянии IPCP запрос параметра DNS-сервера, локальный узел предоставит эти сведения.

### <a name="input-parameters"></a>Входные параметры

- **ppp_ptr**: указатель на блок управления PPP
- **dns_address**: адрес DNS-сервера

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — адрес DNS-сервера успешно задан.
- **NX_PPP_NOT_ESTABLISHED** (0xB5) — не завершено согласование PPP с одноранговым узлом.
- NX_PTR_ERROR (0x07) — недопустимый указатель PPP.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c

ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the DNS Server address provided if the peer requests one. */

```

## <a name="nx_ppp_secondary_dns_address_set"></a>nx_ppp_secondary_dns_address_set

Здание IP-адреса дополнительного DNS-сервера

### <a name="prototype"></a>Прототип

```c
UINT nx_ppp_secondary_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a>Описание

Эта служба задает IP-адрес дополнительного DNS-сервера. Если одноранговый узел отправляет в состоянии IPCP запрос параметра дополнительного DNS-сервера, локальный узел предоставит эти сведения.

### <a name="input-parameters"></a>Входные параметры

- **ppp_ptr**: указатель на блок управления PPP
- **dns_address**: адрес дополнительного DNS-сервера

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — адрес DNS-сервера успешно задан. 
- **NX_PPP_NOT_ESTABLISHED** (0xB5) — не завершено согласование PPP с одноранговым узлом.
- NX_PTR_ERROR (0x07) — недопустимый указатель PPP.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_secondary_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the secondary DNS Server address provided if the peer requests one. */

```
## <a name="nx_ppp_interface_index_get"></a>nx_ppp_interface_index_get

Получение индекса IP-интерфейса

### <a name="prototype"></a>Прототип

```c
UINT nx_ppp_interface_index_get(NX_PPP *ppp_ptr, UINT *index_ptr);
```

### <a name="description"></a>Описание

Эта служба получает индекс IP-интерфейса, сопоставленного с этим экземпляром PPP. Это полезно только в том случае, если экземпляр PPP не является основным интерфейсом для экземпляра IP-адреса.

### <a name="input-parameters"></a>Входные параметры

- **ppp_ptr**: указатель на блок управления PPP
- **index_ptr**: назначение для индекса интерфейса

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — индекс PPP успешно получен.
- **NX_IN_PROGRESS** (0x37) — инициализация PPP не завершена.
- NX_PTR_ERROR (0x07) — недопустимый указатель PPP.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
ULONG  my_index;

/* Get the interface index for this PPP instance. */
status =  nx_ppp_interface_index_get(&my_ppp, &my_index);

/* If status is NX_SUCCESS the “my_index” contains the IP interface index for
   this PPP instance. */

```
## <a name="nx_ppp_ip_address_assign"></a>nx_ppp_ip_address_assign

Назначение IP-адресов для IPCP

### <a name="prototype"></a>Прототип

```c
UINT nx_ppp_ip_address_assign(NX_PPP *ppp_ptr, ULONG local_ip_address, 
            ULONG peer_ip_address);
```

### <a name="description"></a>Описание

Эта служба настраивает IP-адреса локального и однорангового узлов для использования в протоколе IPCP (протокол управления протоколом IP). Ее нужно вызывать для того экземпляра PPP, у которого есть допустимые IP-адреса для себя и другого однорангового узла.

### <a name="input-parameters"></a>Входные параметры

- **ppp_ptr**: указатель на блок управления PPP
- **local_ip_address**: локальный IP-адрес
- **peer_ip_address**: IP-адрес однорангового узла

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — адрес PPP успешно назначен.
- NX_PTR_ERROR (0x07) — недопустимый указатель PPP.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Set IP addresses for “my_ppp”. */
status =  nx_ppp_ip_address_assign(&my_ppp, IP_ADDRESS(256,2,2,187), 
IP_ADDRESS(256,2,2,188));


/* If status is NX_SUCCESS the “my_ppp” has the IP addresses. */
```

## <a name="nx_ppp_link_down_notify"></a>nx_ppp_link_down_notify

Оповещение приложения об отключении канала

### <a name="prototype"></a>Прототип

```c
UINT nx_ppp_link_down_notify(NX_PPP *ppp_ptr, 
                             VOID (*link_down_callback)(NX_PPP *ppp_ptr));
```

### <a name="description"></a>Описание

Эта служба регистрирует обратный вызов для информирования приложения об отключении канала для указанного экземпляра PPP. Если значение отлично от NULL, указанная функция обратного вызова будет вызываться каждый раз при отключении этого канала.

### <a name="input-parameters"></a>Входные параметры

- **ppp_ptr**: указатель на блок управления PPP
- **link_down_callback**: указатель на функцию обратного вызова для уведомления приложения об отключении канала. Если значение равно NULL, уведомление об отключении канала не используется.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — обратный вызов для уведомления об отключении канала успешно зарегистрирован.
- NX_PTR_ERROR (0x07) — недопустимый указатель PPP.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="example"></a>Например, .

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
## <a name="nx_ppp_link_up_notify"></a>nx_ppp_link_up_notify

Оповещение приложения о включении канала

### <a name="prototype"></a>Прототип

```c
UINT nx_ppp_link_up_notify(NX_PPP *ppp_ptr, 
                           VOID (*link_up_callback)(NX_PPP *ppp_ptr));
```
### <a name="description"></a>Описание

Эта служба регистрирует обратный вызов для информирования приложения о включении канала для указанного экземпляра PPP. Если значение отлично от NULL, указанная функция обратного вызова будет вызываться каждый раз при включении этого канала.

### <a name="input-parameters"></a>Входные параметры

- **ppp_ptr**: указатель на блок управления PPP
- **link_up_callback**: указатель на функцию обратного вызова для уведомления приложения о включении канала Если значение равно NULL, уведомление о включении канала не используется.**

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — обратный вызов для уведомления о включении канала успешно зарегистрирован.
- NX_PTR_ERROR (0x07) — недопустимый указатель PPP.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="example"></a>Например, .

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

## <a name="nx_ppp_nak_authentication_notify"></a>nx_ppp_nak_authentication_notify

Уведомление приложения о получении пакета NAK при проверке подлинности

### <a name="prototype"></a>Прототип

```c
UINT    nx_ppp_nak_authentication_notify(NX_PPP *ppp_ptr, 
                                         void (*nak_authentication_notify)(void));
```

### <a name="description"></a>Описание

Эта служба регистрирует обратный вызов для информирования приложения о получении пакета NAK при проверке подлинности для указанного экземпляра PPP. Если значение не равно NULL, эта функция обратного вызова вызывается каждый раз, когда экземпляр PPP получает пакет NAK во время проверки подлинности.

### <a name="input-parameters"></a>Входные параметры

- **ppp_ptr**: указатель на блок управления PPP
- **nak_authentication_notify**: указатель на функцию, которая вызывается при получении экземпляром PPP пакета NAK при проверке подлинности Если значение равно NULL, это уведомление не используется.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — обратный вызов для уведомления успешно зарегистрирован.
- NX_PTR_ERROR (0x07) — недопустимый указатель PPP.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="example"></a>Например, .

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

## <a name="nx_ppp_pap_enable"></a>nx_ppp_pap_enable

Включение проверки подлинности PAP

### <a name="prototype"></a>Прототип

```c

UINT  nx_ppp_pap_enable(NX_PPP *ppp_ptr, 
                        UINT (*generate_login)(CHAR *name, CHAR *password),
                        UINT (*verify_login)(CHAR *name, CHAR *password));
```

### <a name="description"></a>Описание

Эта служба включает протокол PAP (протокол проверки пароля) для указанного экземпляра PPP. Если указана функция ***verify_login***, использование PAP считается обязательным для этого экземпляра PPP. В противном случае PAP включается только по требованию однорангового узла, полученному при согласовании LCP.

Ниже упоминаются несколько элементов данных, которые используются в обязательных функциях обратного вызова. Элемент данных *name* должен иметь формат строки, оканчивающейся символом NULL, и размер, не превышающий значение NX_PPP_NAME_SIZE-1. Элемент данных *password* должен также иметь формат строки, оканчивающейся символом NULL, и размер, не превышающий значение NX_PPP_PASSWORD_SIZE-1.

>[!NOTE]
> Эта функция должна вызываться после *nx_ppp_create*, но раньше *nx_ip_create* или *nx_ip_interface_attach*.

### <a name="input-parameters"></a>Входные параметры

- **ppp_ptr**: указатель на блок управления PPP
- **generate_login**: указатель на функцию приложения, которая предоставляет одноранговому узлу параметры *name* и *password* для проверки подлинности Обратите внимание, что значения *name* и *password* должны быть скопированы в указанные места назначения.
- **verify_login**: указатель на функцию приложения, которая проверяет параметры *name* и *password*, предоставленные одноранговым узлом Эта подпрограмма должна сравнивать предоставленные значения *name* и *password*. Если она возвращает NX_SUCCESS, значит, имя и пароль верны и PPP может перейти к следующему шагу. В противном случае подпрограмма возвращает NX_PPP_ERROR, и тогда PPP ожидает новые значения имени и пароля.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — PPP PAP успешно включено.
- **NX_NOT_IMPLEMENTED** (0x80) — логика PAP была отключена с помощью параметра NX_PPP_DISABLE_PAP.
- NX_PTR_ERROR (0x07) — недопустимый указатель PPP или указатель на функцию приложения.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

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

## <a name="nx_ppp_ping_request"></a>nx_ppp_ping_request

Отправка запроса проверки связи LCP

### <a name="prototype"></a>Прототип

```c
UINT  nx_ppp_ping_request(NX_PPP *ppp_ptr, CHAR *data, 
                          UINT data_size, ULONG wait_opion);
```

### <a name="description"></a>Описание

Эта служба отправляет запрос LCP и устанавливает флаг, обозначающий, что устройство PPP ожидает ответ на проверку связи. Параметр wait здесь предназначен в первую очередь для вызова *nx_packet_allocate*. Служба возвращает управление сразу после отправки запроса. Она не ждет никакого ответа. 

При получении соответствующего ответа проверки связи установленный флаг будет снят задачей потока PPP. Устройство PPP должно выполнить часть согласования PPP, относящуюся к LCP.

Эта служба полезна для настроек PPP, в которых не используется опрос оборудования для получения состояния канала.

### <a name="input-parameters"></a>Входные параметры

- **ppp_ptr**: указатель на блок управления PPP
- **data**: указатель на данные, которые отправляются в запросе проверки связи.
- **data_size**: размер данных для отправки wait_option: время ожидания до отправки сообщения проверки связи LCP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — запрос проверки связи успешно отправлен.
- **NX_PPP_NOT_ESTABLISHED** (0xB5) — соединение PPP не установлено.
- NX_PTR_ERROR (0x07) — недопустимый указатель PPP или указатель на функцию приложения.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки приложения

### <a name="example"></a>Например, .

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

## <a name="nx_ppp_raw_string_send"></a>nx_ppp_raw_string_send

Отправка необработанной строки ASCII

### <a name="prototype"></a>Прототип

```c
UINT  nx_ppp_raw_sting_send(NX_PPP *ppp_ptr, CHAR *string_ptr);
```

### <a name="description"></a>Описание

Эта служба отправляет из интерфейса PPP строку ASCII без использования протокола PPP. Обычно она вызывается в том случае, если PPP получает пакет с информацией об управлении модемом в формате, отличном от PPP.

### <a name="input-parameters"></a>Входные параметры

- **ppp_ptr**: указатель на блок управления PPP
- **string_ptr**: указатель на строку для отправки

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — необработанная строка PPP успешно отправлена.
- NX_PTR_ERROR (0x07) — недопустимый указатель PPP или указатель на строку.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c

/* Send “CLIENTSERVER” to “CLIENT” sent by Windows 98 before PPP is
initiated.  */
status =  nx_ppp_raw_string_send(&my_ppp, “CLIENTSERVER”);

/* If status is NX_SUCCESS the raw string was successfully Sent via PPP. */
```
## <a name="nx_ppp_restart"></a>nx_ppp_restart

Перезапуск обработки PPP

### <a name="prototype"></a>Прототип

```c
UINT  nx_ppp_restart(NX_PPP *ppp_ptr);
```

### <a name="description"></a>Описание

Эта служба перезапускает обработку PPP. Обычно она вызывается, когда необходимо восстановить связь при получении сведений об отключении канала через обратный вызов или сообщения управления модемом в формате, отличном от PPP.

### <a name="input-parameters"></a>Входные параметры

- **ppp_ptr**: указатель на блок управления PPP

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — перезапуск PPP успешно инициирован.
- NX_PTR_ERROR (0x07) — недопустимый указатель PPP.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Restart the PPP instance “my_ppp”.  */
status =  nx_ppp_restart(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been restarted. */
```

## <a name="nx_ppp_start"></a>nx_ppp_start

Запуск обработки PPP

### <a name="prototype"></a>Прототип

```c
UINT  nx_ppp_start(NX_PPP *ppp_ptr);
```

### <a name="description"></a>Описание

Эта служба запускает обработку PPP. Обычно она вызывается сразу после вызова nx_ppp_stop().

>[!NOTE]
> PPP автоматически начинает обработку PPP, как только связь будет установлена.

### <a name="input-parameters"></a>Входные параметры

- **ppp_ptr**: указатель на блок управления PPP

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — запуск PPP успешно инициирован. 
- **NX_PPP_ALREADY_STARTED** (0xb9) — запуск PPP уже выполнен.
- NX_PTR_ERROR (0x07) — недопустимый указатель PPP.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Start the PPP instance “my_ppp”.  */
status =  nx_ppp_start(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been started. */
```

## <a name="nx_ppp_status_get"></a>nx_ppp_status_get

Получение текущего состояния PPP

### <a name="prototype"></a>Прототип

```c
UINT  nx_ppp_status_get(NX_PPP *ppp_ptr, UINT *status_ptr);
```
### <a name="description"></a>Описание

Эта служба получает текущее состояние указанного экземпляра PPP.

### <a name="input-parameters"></a>Входные параметры

- **ppp_ptr**: указатель на блок управления PPP
- **status_ptr**: назначение для состояния PPP, которое может принимать приведенные ниже значения состояния
    - **NX_PPP_STATUS_ESTABLISHED**
    - **NX_PPP_STATUS_LCP_IN_PROGRESS**
    - **NX_PPP_STATUS_LCP_FAILED**
    - **NX_PPP_STATUS_PAP_IN_PROGRESS**
    - **NX_PPP_STATUS_PAP_FAILED**
    - **NX_PPP_STATUS_CHAP_IN_PROGRESS**
    - **NX_PPP_STATUS_CHAP_FAILED**
    - **NX_PPP_STATUS_IPCP_IN_PROGRESS**
    - **NX_PPP_STATUS_IPCP_FAILED**

>[!NOTE]
> Состояние считается допустимым только в том случае, если API возвращает значение NX_SUCCESS. Кроме того, при получении любого значения состояния с постфиксом *_FAILED обработка PPP прекращается до тех пор, пока приложение не перезапустит ее.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — запрос состояния PPP успешно выполнен.
- NX_PTR_ERROR (0x07) — недопустимый указатель PPP.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="example"></a>Например, .

```c
UINT ppp_status;
UINT status;


/* Get the current status of PPP instance “my_ppp”.  */
status =  nx_ppp_status_get(&my_ppp, &ppp_status);

/* If status is NX_SUCCESS the current internal PPP status is contained in
   “ppp_status”. */
```
## <a name="nx_ppp_stop"></a>nx_ppp_stop

Запуск обработки PPP

### <a name="prototype"></a>Прототип

```c
UINT  nx_ppp_stop(NX_PPP *ppp_ptr);
```

### <a name="description"></a>Описание

Эта служба останавливает обработку PPP. Пользователь также может вызвать nx_ppp_start(), чтобы начать обработку PPP.

### <a name="input-parameters"></a>Входные параметры

- **ppp_ptr**: указатель на блок управления PPP

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — запуск PPP успешно инициирован. 
- **NX_PPP_ALREADY_STOPPED** (0xb8) — обработка PPP уже остановлена.
- NX_PTR_ERROR (0x07) — недопустимый указатель PPP.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Stop the PPP instance “my_ppp”.  */
status =  nx_ppp_stop(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been stopped. */
```
## <a name="nx_ppp_packet_receive"></a>nx_ppp_packet_receive

Получение пакета PPP

### <a name="prototype"></a>Прототип

```c
UINT  nx_ppp_packet_receive(NX_PPP *ppp_ptr, NX_PACKET *packet_ptr);

```

### <a name="description"></a>Описание

Эта служба получает пакет PPP.

### <a name="input-parameters"></a>Входные параметры

- **ppp_ptr**: указатель на блок управления PPP
- **packet_ptr**: указатель на пакет PPP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — запрос состояния PPP успешно выполнен.
- NX_PTR_ERROR (0x07) — недопустимый указатель PPP.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Receive the PPP packet of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_receive(&my_ppp, packet_ptr);

/* If status is NX_SUCCESS the PPP packet has received. */


```
## <a name="nx_ppp_packet_send_set"></a>nx_ppp_packet_send_set

Задание функции отправки пакета PPP

### <a name="prototype"></a>Прототип

```c
UINT  nx_ppp_packet_send_set(NX_PPP *ppp_ptr, 
                             VOID (*nx_ppp_packet_send)(NX_PACKET *packet_ptr));

```

### <a name="description"></a>Описание

Эта служба задает функцию для отправки пакета PPP.

### <a name="input-parameters"></a>Входные параметры

- **ppp_ptr**: указатель на блок управления PPP
- **nx_ppp_packet_send**: подпрограмма для отправки пакета PPP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — запрос состояния PPP успешно выполнен.
- NX_PTR_ERROR (0x07) — недопустимый указатель PPP.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Пример

```c
/* Set the PPP packet send function of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_send_set(&my_ppp, nx_ppp_packet_send);

/* If status is NX_SUCCESS the PPP packet send function has set. */


```