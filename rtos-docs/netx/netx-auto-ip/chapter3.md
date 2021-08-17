---
title: Глава 3. Описание служб ОСРВ Azure NetX AutoIP
description: В этой главе приведено описание всех служб ОСРВ Azure NetX AutoIP, которые перечислены ниже в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 15a70416f9d4d1324d930820b09366a7e7cd6f4525872472cd88edfbb25ee155
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796877"
---
# <a name="chapter-3---description-of-azure-rtos-netx-autoip-services"></a>Глава 3. Описание служб ОСРВ Azure NetX AutoIP

В этой главе приведено описание всех служб ОСРВ Azure NetX AutoIP, которые перечислены ниже в алфавитном порядке.

В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, используемым для отключения проверки ошибок API, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.

- **nx_auto_ip_create**: *создание экземпляра AutoIP*.
- **nx_auto_ip_delete**: *удаление экземпляра AutoIP*.
- **nx_auto_ip_get_address**: *получение текущего адреса AutoIP*.
- **nx_auto_ip_set_interface**: *настройка интерфейса IP, требующего адрес AutoIP*.
- **nx_auto_ip_start**: *запуск обработки AutoIP*.
- **nx_auto_ip_stop**: *завершение обработки AutoIP*.

## <a name="nx_auto_ip_create"></a>nx_auto_ip_create

Создание экземпляра AutoIP.

### <a name="prototype"></a>Прототип

```c
UINT nx_auto_ip_create(NX_AUTO_IP *auto_ip_ptr, CHAR *name,
            NX_IP *ip_ptr, VOID *stack_ptr, ULONG stack_size,
            UINT priority);
```

### <a name="description"></a>Описание

Эта служба создает экземпляр AutoIP по указанному экземпляру IP.

- **auto_ip_ptr**: указатель на блок управления AutoIP.
- **name**: имя экземпляра AutoIP.
- **ip_ptr**: указатель на экземпляр IP.
- **stack_ptr**: указатель на область стека потоков AutoIP.
- **stack_size**: размер области стека потоков AutoIP.
- **priority**: приоритет потока AutoIP.

> [!NOTE]
> Если используется протокол DHCP, то поток DHCP должен иметь более высокий приоритет, чем поток экземпляра IP и поток AutoIP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): экземпляр AutoIP успешно создан.
- **NX_AUTO_IP_ERROR** (0XA00): ошибка создания AutoIP.
- NX_PTR_ERROR: (0x16): недопустимый указатель AutoIP, ip_ptr или указатель стека.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Пример

```c
/* Create the AutoIP instance "auto_ip_0" on "ip_0". */
status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);

/* If status is NX_SUCCESS an AutoIP instance was successfully created. */
```

### <a name="see-also"></a>См. также:

nx_auto_ip_delete, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop

## <a name="nx_auto_ip_delete"></a>nx_auto_ip_delete

Удаление экземпляра AutoIP.

### <a name="prototype"></a>Прототип

```c
UINT nx_auto_ip_delete(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет созданный ранее экземпляр AutoIP по указанному экземпляру IP.

### <a name="input-parameters"></a>Входные параметры

- **auto_ip_ptr**: указатель на блок управления AutoIP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): экземпляр AutoIP успешно удален.
- **NX_AUTO_IP_ERROR** (0XA00): ошибка удаления AutoIP.
- NX_PTR_ERROR (0x16): недопустимый указатель AutoIP.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
/* Delete the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_delete(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully deleted. */
```

### <a name="see-also"></a>См. также:

nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop

## <a name="nx_auto_ip_get_address"></a>nx_auto_ip_get_address

Получение текущего адреса AutoIP.

### <a name="prototype"></a>Прототип

```c
UINT nx_auto_ip_get_address(NX_AUTO_IP *auto_ip_ptr,
                            ULONG *local_ip_address);
```

### <a name="description"></a>Описание

Эта служба получает текущий адрес конфигурации AutoIP. Если его нет, возвращается IP-адрес 0.0.0.0.

### <a name="input-parameters"></a>Входные параметры

- **auto_ip_ptr**: указатель на блок управления AutoIP.
- **local_ip_address**: назначение для обратного IP-адреса.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): адрес AutoIP успешно получен.
- **NX_AUTO_IP_NO_LOCAL** (0XA01): допустимый адрес AutoIP отсутствует.
- NX_PTR_ERROR (0x16): недопустимый указатель AutoIP.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, таймеры, потоки, подпрограммы ISR

### <a name="example"></a>Пример

```c
ULONG local_address;

/* Get the AutoIP address resolved by the instance "auto_ip_0." */
status = nx_auto_ip_get_address(&auto_ip_0, &local_address);

/* If status is NX_SUCCESS the local IP address is in "local_address." */
```

### <a name="see-also"></a>См. также:

nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop

## <a name="nx_auto_ip_set_interface"></a>nx_auto_ip_set_interface

Настройка сетевого интерфейса для AutoIP.

### <a name="prototype"></a>Прототип

```c
UINT nx_auto_ip_set_interface(NX_AUTO_IP *auto_ip_ptr,
                                UINT interface_index);
```

### <a name="description"></a>Описание

Эта служба задает индекс для сетевого интерфейса, с помощью которого AutoIP который будет отправлять пробу на IP-адрес в сети. Значение по умолчанию равно нулю (основной сетевой интерфейс). Применимо только к многосетевым устройствам.

### <a name="input-parameters"></a>Входные параметры

- **auto_ip_ptr**: указатель на блок управления AutoIP.
- **interface_index**: интерфейс для проверки IP-адреса с помощью пробы.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): интерфейс AutoIP успешно задан.
- **NX_AUTO_IP_BAD_INTERFACE_INDEX** (0xA02): недопустимый сетевой интерфейс. 
- NX_PTR_ERROR (0x16): недопустимый указатель AutoIP.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, таймеры, потоки, подпрограммы ISR

### <a name="example"></a>Пример

```c
ULONG interface_index;

/* Set the network interface on which AutoIP probes for host address. */
status = nx_auto_ip_set_interface(&auto_ip_0, interface_index);

/* If status is NX_SUCCESS the network interface is valid and set in the AutoIP control block auto_ip_0. */
```

### <a name="see-also"></a>См. также:

nx_auto_ip_create, nx_auto_ip_get_address, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop

## <a name="nx_auto_ip_start"></a>nx_auto_ip_start

Начало обработки AutoIP.

### <a name="prototype"></a>Прототип

```c
UINT nx_auto_ip_start(NX_AUTO_IP *auto_ip_ptr,
                    ULONG starting_local_address);
```

### <a name="description"></a>Описание

Эта служба запускает протокол AutoIP на созданном ранее экземпляре AutoIP.

### <a name="input-parameters"></a>Входные параметры

- **auto_ip_ptr**: указатель на блок управления AutoIP.
- **starting_local_address**: необязательный начальный адрес AutoIP. Значение IP_ADDRESS (0,0,0,0) указывает, что случайный адрес AutoIP должен быть производным. В противном случае, если указан допустимый адрес AutoIP, NetX AutoIP попытается назначить этот адрес.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): протокол AutoIP успешно запущен.
- **NX_AUTO_IP_ERROR** (0XA00): ошибка запуска протокола AutoIP.
- NX_PTR_ERROR (0x16): недопустимый указатель AutoIP.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Пример

```c
/* Start the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_start(&auto_ip_0, IP_ADDRESS(0,0,0,0));

/* If status is NX_SUCCESS an AutoIP instance was successfully started. */
```

### <a name="see-also"></a>См. также:

nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_stop

## <a name="nx_auto_ip_stop"></a>nx_auto_ip_stop

Остановка обработки AutoIP.

### <a name="prototype"></a>Прототип

```c
UINT nx_auto_ip_stop(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a>Описание

Эта служба останавливает протокол AutoIP на созданном ранее и запущенном экземпляре AutoIP. Эта служба обычно используется при изменении IP-адреса с помощью DHCP или вручную на адрес, отличный от AutoIP.

### <a name="input-parameters"></a>Входные параметры

- **auto_ip_ptr**: указатель на блок управления AutoIP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): протокол AutoIP успешно остановлен.
- **NX_AUTO_IP_ERROR** (0XA00): ошибка остановки протокола AutoIP.
- NX_PTR_ERROR (0x16): недопустимый указатель AutoIP.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
/* Stop the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_stop(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully stopped. */
```

### <a name="see-also"></a>См. также:

nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_start