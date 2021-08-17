---
title: Сведения о классах DPUMP USBX
description: USBX содержит класс DPUMP для узла и устройства.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 72aa9c1e2200049bf81d64543b690edd001c4ecf9c2cdeb4c3bea5f1b03aa5b8
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116802585"
---
# <a name="chapter-3-usbx-dpump-class-considerations"></a>Глава 3. Сведения о классах DPUMP USBX

USBX содержит класс DPUMP для узла и устройства. Этот класс не является стандартным классом, а скорее примером для демонстрации создания простого устройства с помощью двух блочных каналов и отправки данных через эти каналы. Класс DPUMP можно использовать для создания пользовательского класса или для устаревших устройств RS232.

Блок-схема DPUMP USB:

![Блок-схема DPUMP USB](./media/usbx-host-stack-supplemental/usb-dpump-flow-chart.png)

## <a name="usbx-dpump-host-class"></a>Класс узла USBX DPUMP

На стороне узла класс DPUMP имеет две функции: одну для отправки и другую для получения данных.

- `ux_host_class_dpump_write`
- `ux_host_class_dpump_read`

Обе функции используют блокировку, чтобы упростить приложение DPUMP. Если вам нужно одновременно выполнять оба канала (IN и OUT), приложению придется создать отдельные потоки для передачи и приема.

Ниже предоставлен прототип для функции записи.

```C
UINT ux_host_class_dpump_write(UX_HOST_CLASS_DPUMP *dpump,
    UCHAR *data_pointer,
    ULONG requested_length,  
    ULONG *actual_length)
```

Где:

- dpump является экземпляром класса;
- data_pointer является указателем на буфер для отправки;
- requested_length обозначает длину данных для отправки;
- actual_length обозначает длину отправленных данных после завершения передачи, успешной или частичной.

Прототип для функции получения выглядит почти так же.

```C
UINT ux_host_class_dpump_read(
    UX_HOST_CLASS_DPUMP *dpump,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

Ниже приведен пример класса DPUMP для узла, в котором приложение записывает пакет на устройство и получает тот же пакет через поток приема:

```C
/* We start with a 'A' in buffer. */
current_char = 'A';

while(1)
{
    /* Initialize the write buffer. */
    ux_utility_memory_set(out_buffer, current_char,
        UX_HOST_CLASS_DPUMP_PACKET_SIZE);

    /* Increment the character in buffer. */
    current_char++;

    /* Check for upper alphabet limit. */
    if (current_char > 'Z')
        current_char = 'A';

    /* Write to the Data Pump Bulk out endpoint. */
    status = ux_host_class_dpump_write (dpump, out_buffer,
        UX_HOST_CLASS_DPUMP_PACKET_SIZE,
        &actual_length);

    /* Verify that the status and the amount of data is correct. */
    if ((status == UX_SUCCESS) && actual_length == UX_HOST_CLASS_DPUMP_PACKET_SIZE)
    {
        /* Read to the Data Pump Bulk out endpoint. */
        status = ux_host_class_dpump_read (dpump, in_buffer,
            UX_HOST_CLASS_DPUMP_PACKET_SIZE, &actual_length);
    }
}
```

## <a name="usbx-dpump-device-class"></a>Класс устройства USBX DPUMP

Класс DPUMP на стороне устройства использует поток, который запускается при подключении к USB-узлу. Этот поток ожидает входящие пакеты в конечной точке Bulk Out. Содержимое полученного пакета копируется в буфер конечной точки Bulk In, и в этой конечной точке публикуется транзакция, которая ожидает от узла запрос на чтение из этой конечной точки. Этот механизм по сути замыкает конечную точку Bulk Out на Bulk In.
