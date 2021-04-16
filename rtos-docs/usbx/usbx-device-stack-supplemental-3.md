---
title: Глава 3. Сведения о классах DPUMP в USBX
description: USBX содержит класс DPUMP для узла и устройства. Этот класс не является стандартным классом, а скорее примером для демонстрации создания простого устройства с помощью двух блочных каналов и отправки данных между этими каналами.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c7870f1984fe3104d30e3b9efd82010218acbe27
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104816463"
---
# <a name="chapter-3---usbx-dpump-class-considerations"></a><span data-ttu-id="c2bb1-104">Глава 3. Сведения о классах DPUMP в USBX</span><span class="sxs-lookup"><span data-stu-id="c2bb1-104">Chapter 3 - USBX DPUMP Class Considerations</span></span>

<span data-ttu-id="c2bb1-105">USBX содержит класс **DPUMP** для узла и устройства.</span><span class="sxs-lookup"><span data-stu-id="c2bb1-105">USBX contains a **DPUMP** class for the host and device side.</span></span> <span data-ttu-id="c2bb1-106">Этот класс не является стандартным классом, а скорее примером для демонстрации создания простого устройства с помощью двух блочных каналов и отправки данных между этими каналами.</span><span class="sxs-lookup"><span data-stu-id="c2bb1-106">This class is not a standard class in itself, but rather an example that illustrates how to create a simple device by using two bulk pipes and sending data back and forth on these two pipes.</span></span> <span data-ttu-id="c2bb1-107">Класс **DPUMP** можно использовать для создания пользовательского класса или для устаревших устройств RS232.</span><span class="sxs-lookup"><span data-stu-id="c2bb1-107">The **DPUMP** class could be used to start a custom class or for legacy RS232 devices.</span></span>

<span data-ttu-id="c2bb1-108">Блок-схема USBX DPUMP:</span><span class="sxs-lookup"><span data-stu-id="c2bb1-108">USB DPUMP flow chart:</span></span>

![Блок-схема USBX DPUMP](./media/usbx-device-stack-supplemental/usb-dpump-flow-chart.png)

## <a name="usbx-dpump-device-class"></a><span data-ttu-id="c2bb1-110">Класс устройства USBX DPUMP</span><span class="sxs-lookup"><span data-stu-id="c2bb1-110">USBX DPUMP Device Class</span></span>

<span data-ttu-id="c2bb1-111">Класс **DPUMP** на стороне устройства использует поток, который запускается при подключении к узлу с USB.</span><span class="sxs-lookup"><span data-stu-id="c2bb1-111">The device **DPUMP** class uses a thread, which is started upon connection to the USB host.</span></span> <span data-ttu-id="c2bb1-112">Этот поток ожидает входящие пакеты в конечной точке Bulk Out.</span><span class="sxs-lookup"><span data-stu-id="c2bb1-112">The thread waits for a packet coming on the Bulk Out endpoint.</span></span> <span data-ttu-id="c2bb1-113">Содержимое полученного пакета копируется в буфер конечной точки Bulk In, и в этой конечной точке публикуется транзакция, которая ожидает от узла запрос на чтение из этой конечной точки.</span><span class="sxs-lookup"><span data-stu-id="c2bb1-113">When a packet is received, it copies the content to the Bulk In endpoint buffer and posts a transaction on this endpoint, waiting for the host to issue a request to read from this endpoint.</span></span> <span data-ttu-id="c2bb1-114">Этот механизм по сути замыкает конечную точку Bulk Out на Bulk In.</span><span class="sxs-lookup"><span data-stu-id="c2bb1-114">This provides a loopback mechanism between the Bulk Out and Bulk In endpoints.</span></span>
