---
title: Сведения о классах DPUMP USBX
description: USBX содержит класс DPUMP для узла и устройства.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9960b391418fa2f9203e761115bcba71cc3619e8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104816103"
---
# <a name="chapter-3-usbx-dpump-class-considerations"></a><span data-ttu-id="7a50d-103">Глава 3. Сведения о классах DPUMP USBX</span><span class="sxs-lookup"><span data-stu-id="7a50d-103">Chapter 3: USBX DPUMP Class Considerations</span></span>

<span data-ttu-id="7a50d-104">USBX содержит класс DPUMP для узла и устройства.</span><span class="sxs-lookup"><span data-stu-id="7a50d-104">USBX contains a DPUMP class for the host and device side.</span></span> <span data-ttu-id="7a50d-105">Этот класс не является стандартным классом, а скорее примером для демонстрации создания простого устройства с помощью двух блочных каналов и отправки данных через эти каналы.</span><span class="sxs-lookup"><span data-stu-id="7a50d-105">This class is not a standard class in itself, but rather an example that illustrates how to create a simple device by using two bulk pipes and sending data back and forth on these two pipes.</span></span> <span data-ttu-id="7a50d-106">Класс DPUMP можно использовать для создания пользовательского класса или для устаревших устройств RS232.</span><span class="sxs-lookup"><span data-stu-id="7a50d-106">The DPUMP class could be used to start a custom class or for legacy RS232 devices.</span></span>

<span data-ttu-id="7a50d-107">Блок-схема DPUMP USB:</span><span class="sxs-lookup"><span data-stu-id="7a50d-107">USB DPUMP flow chart:</span></span>

![Блок-схема DPUMP USB](./media/usbx-host-stack-supplemental/usb-dpump-flow-chart.png)

## <a name="usbx-dpump-host-class"></a><span data-ttu-id="7a50d-109">Класс узла USBX DPUMP</span><span class="sxs-lookup"><span data-stu-id="7a50d-109">USBX DPUMP Host Class</span></span>

<span data-ttu-id="7a50d-110">На стороне узла класс DPUMP имеет две функции: одну для отправки и другую для получения данных.</span><span class="sxs-lookup"><span data-stu-id="7a50d-110">The host side of the DPUMP Class has two functions, one for sending data and one for receiving data:</span></span>

- `ux_host_class_dpump_write`
- `ux_host_class_dpump_read`

<span data-ttu-id="7a50d-111">Обе функции используют блокировку, чтобы упростить приложение DPUMP.</span><span class="sxs-lookup"><span data-stu-id="7a50d-111">Both functions are blocking to make the DPUMP application easier.</span></span> <span data-ttu-id="7a50d-112">Если вам нужно одновременно выполнять оба канала (IN и OUT), приложению придется создать отдельные потоки для передачи и приема.</span><span class="sxs-lookup"><span data-stu-id="7a50d-112">If it is necessary to have both pipes (IN and OUT) running at the same time, the application will be required to create a transmit thread and a receive thread.</span></span>

<span data-ttu-id="7a50d-113">Ниже предоставлен прототип для функции записи.</span><span class="sxs-lookup"><span data-stu-id="7a50d-113">The prototype for the writing function is as follows.</span></span>

```C
UINT ux_host_class_dpump_write(UX_HOST_CLASS_DPUMP *dpump,
    UCHAR *data_pointer,
    ULONG requested_length,  
    ULONG *actual_length)
```

<span data-ttu-id="7a50d-114">Где:</span><span class="sxs-lookup"><span data-stu-id="7a50d-114">Where:</span></span>

- <span data-ttu-id="7a50d-115">dpump является экземпляром класса;</span><span class="sxs-lookup"><span data-stu-id="7a50d-115">dpump is the instance of the class</span></span>
- <span data-ttu-id="7a50d-116">data_pointer является указателем на буфер для отправки;</span><span class="sxs-lookup"><span data-stu-id="7a50d-116">data_pointer is the pointer to the buffer to be sent</span></span>
- <span data-ttu-id="7a50d-117">requested_length обозначает длину данных для отправки;</span><span class="sxs-lookup"><span data-stu-id="7a50d-117">requested_length is the length to send</span></span>
- <span data-ttu-id="7a50d-118">actual_length обозначает длину отправленных данных после завершения передачи, успешной или частичной.</span><span class="sxs-lookup"><span data-stu-id="7a50d-118">actual_length is the length sent after completion of the transfer, either successfully or partially.</span></span>

<span data-ttu-id="7a50d-119">Прототип для функции получения выглядит почти так же.</span><span class="sxs-lookup"><span data-stu-id="7a50d-119">The prototype for the receiving function is similar.</span></span>

```C
UINT ux_host_class_dpump_read(
    UX_HOST_CLASS_DPUMP *dpump,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

<span data-ttu-id="7a50d-120">Ниже приведен пример класса DPUMP для узла, в котором приложение записывает пакет на устройство и получает тот же пакет через поток приема:</span><span class="sxs-lookup"><span data-stu-id="7a50d-120">Here is an example of the host DPUMP class where an application writes a packet to the device side and receives the same packet on the reception:</span></span>

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

## <a name="usbx-dpump-device-class"></a><span data-ttu-id="7a50d-121">Класс устройства USBX DPUMP</span><span class="sxs-lookup"><span data-stu-id="7a50d-121">USBX DPUMP Device Class</span></span>

<span data-ttu-id="7a50d-122">Класс DPUMP на стороне устройства использует поток, который запускается при подключении к USB-узлу.</span><span class="sxs-lookup"><span data-stu-id="7a50d-122">The device DPUMP class uses a thread, which is started upon connection to the USB host.</span></span> <span data-ttu-id="7a50d-123">Этот поток ожидает входящие пакеты в конечной точке Bulk Out.</span><span class="sxs-lookup"><span data-stu-id="7a50d-123">The thread waits for a packet coming on the Bulk Out endpoint.</span></span> <span data-ttu-id="7a50d-124">Содержимое полученного пакета копируется в буфер конечной точки Bulk In, и в этой конечной точке публикуется транзакция, которая ожидает от узла запрос на чтение из этой конечной точки.</span><span class="sxs-lookup"><span data-stu-id="7a50d-124">When a packet is received, it copies the content to the Bulk In endpoint buffer and posts a transaction on this endpoint, waiting for the host to issue a request to read from this endpoint.</span></span> <span data-ttu-id="7a50d-125">Этот механизм по сути замыкает конечную точку Bulk Out на Bulk In.</span><span class="sxs-lookup"><span data-stu-id="7a50d-125">This provides a loopback mechanism between the Bulk Out and Bulk In endpoints.</span></span>
