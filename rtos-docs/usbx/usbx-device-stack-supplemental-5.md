---
title: Глава 5. OTG в USBX
description: Узнайте подробности о поддержке USBX функциональных возможностей OTG для USB, если в архитектуре оборудования присутствует контроллер USB, совместимый с OTG.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 64a3c44f84b9ffca31d9e616d14d3d5d87c56bd7
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550326"
---
# <a name="chapter-5---usbx-otg"></a><span data-ttu-id="c3a93-103">Глава 5. OTG в USBX</span><span class="sxs-lookup"><span data-stu-id="c3a93-103">Chapter 5 - USBX OTG</span></span>

<span data-ttu-id="c3a93-104">USBX поддерживает функциональные возможности OTG для USB, если в архитектуре оборудования присутствует контроллер USB, совместимый с OTG.</span><span class="sxs-lookup"><span data-stu-id="c3a93-104">USBX supports the OTG functionalities of USB when an OTG compliant USB controller is available in the hardware design.</span></span>

<span data-ttu-id="c3a93-105">USBX поддерживает OTG в основном стеке USB.</span><span class="sxs-lookup"><span data-stu-id="c3a93-105">USBX supports OTG in the core USB stack.</span></span> <span data-ttu-id="c3a93-106">Но для работы OTG подходит не любой контроллер USB.</span><span class="sxs-lookup"><span data-stu-id="c3a93-106">But for OTG to function, it requires a specific USB controller.</span></span> <span data-ttu-id="c3a93-107">Функции контроллера OTG для USBX можно найти в каталоге usbx_otg.</span><span class="sxs-lookup"><span data-stu-id="c3a93-107">USBX OTG controller functions can be found in the usbx_otg directory.</span></span> <span data-ttu-id="c3a93-108">Текущая версия USBX полностью поддерживает возможности OTG только для NXP LPC3131.</span><span class="sxs-lookup"><span data-stu-id="c3a93-108">The current USBX version only supports the NXP LPC3131 with full OTG capabilities.</span></span>

<span data-ttu-id="c3a93-109">Стандартные функции драйвера контроллера (на узле или на устройстве) по-прежнему размещаются в стандартных файлах USBX (usbx_device_controllers и usbx_host_controllers), а каталог usbx_otg содержит только функции OTG, связанные с контроллером USB.</span><span class="sxs-lookup"><span data-stu-id="c3a93-109">The regular controller driver functions (host or device) can still be found in the standard USBX usbx_device_controllers and usbx_host_controllers but the usbx_otg directory contains the specific OTG functions associated with the USB controller.</span></span>

<span data-ttu-id="c3a93-110">Существует четыре категории функций контроллера OTG, дополняющих обычные функции узла и устройства:</span><span class="sxs-lookup"><span data-stu-id="c3a93-110">There are four categories of functions for an OTG controller in addition to the usual host/device functions.</span></span>

- <span data-ttu-id="c3a93-111">функции VBUS;</span><span class="sxs-lookup"><span data-stu-id="c3a93-111">VBUS specific functions</span></span>
- <span data-ttu-id="c3a93-112">запуск и остановка контроллера;</span><span class="sxs-lookup"><span data-stu-id="c3a93-112">Start and Stop of the controller</span></span>
- <span data-ttu-id="c3a93-113">диспетчер ролей USB;</span><span class="sxs-lookup"><span data-stu-id="c3a93-113">USB role manager</span></span>
- <span data-ttu-id="c3a93-114">обработчики прерываний.</span><span class="sxs-lookup"><span data-stu-id="c3a93-114">Interrupt handlers</span></span>

## <a name="vbus-functions"></a><span data-ttu-id="c3a93-115">Функции VBUS</span><span class="sxs-lookup"><span data-stu-id="c3a93-115">VBUS functions</span></span>

<span data-ttu-id="c3a93-116">Каждый контроллер должен иметь диспетчер VBUS, чтобы изменять состояние VBUS с учетом требований к управлению питанием.</span><span class="sxs-lookup"><span data-stu-id="c3a93-116">Each controller needs to have a VBUS manager to change the state of VBUS based on power management requirements.</span></span> <span data-ttu-id="c3a93-117">Обычно его функциональность ограничивается включением и отключением VBUS.</span><span class="sxs-lookup"><span data-stu-id="c3a93-117">Usually, this function only performs turning on or off VBUS.</span></span>

## <a name="start-and-stop-the-controller"></a><span data-ttu-id="c3a93-118">Запуск и остановка контроллера</span><span class="sxs-lookup"><span data-stu-id="c3a93-118">Start and Stop the controller</span></span>

<span data-ttu-id="c3a93-119">В отличие от обычной реализации USB, для OTG нужно, чтобы стек узла и (или) устройства изменял состояние активации при изменении роли.</span><span class="sxs-lookup"><span data-stu-id="c3a93-119">Unlike a regular USB implementation, OTG requires the host and/or the device stack to be activated and deactivated when the role changes.</span></span>

## <a name="usb-role-manager"></a><span data-ttu-id="c3a93-120">Диспетчер ролей USB</span><span class="sxs-lookup"><span data-stu-id="c3a93-120">USB role Manager</span></span>

<span data-ttu-id="c3a93-121">Диспетчер ролей USB получает команды на изменение состояния USB.</span><span class="sxs-lookup"><span data-stu-id="c3a93-121">The USB role manager receives commands to change the state of the USB.</span></span> <span data-ttu-id="c3a93-122">Существует несколько состояний, в которые и из которых может потребоваться переход.</span><span class="sxs-lookup"><span data-stu-id="c3a93-122">There are several states that need transitions to and from:</span></span>

| <span data-ttu-id="c3a93-123">Состояние</span><span class="sxs-lookup"><span data-stu-id="c3a93-123">State</span></span>                    | <span data-ttu-id="c3a93-124">Значение</span><span class="sxs-lookup"><span data-stu-id="c3a93-124">Value</span></span> | <span data-ttu-id="c3a93-125">Описание</span><span class="sxs-lookup"><span data-stu-id="c3a93-125">Description</span></span>                                           |
| ------------------------ | ----- | ----------------------------------------------------- |
| <span data-ttu-id="c3a93-126">UX_OTG_IDLE</span><span class="sxs-lookup"><span data-stu-id="c3a93-126">UX_OTG_IDLE</span></span>            | <span data-ttu-id="c3a93-127">0</span><span class="sxs-lookup"><span data-stu-id="c3a93-127">0</span></span>     | <span data-ttu-id="c3a93-128">Устройство неактивно.</span><span class="sxs-lookup"><span data-stu-id="c3a93-128">The device is Idle.</span></span> <span data-ttu-id="c3a93-129">Нет никаких подключений.</span><span class="sxs-lookup"><span data-stu-id="c3a93-129">Not connected to anything</span></span> |
| <span data-ttu-id="c3a93-130">UX_OTG_IDLE_TO_HOST</span><span class="sxs-lookup"><span data-stu-id="c3a93-130">UX_OTG_IDLE_TO_HOST</span></span>  | <span data-ttu-id="c3a93-131">1</span><span class="sxs-lookup"><span data-stu-id="c3a93-131">1</span></span>     | <span data-ttu-id="c3a93-132">Устройство подключено с помощью разъема типа A.</span><span class="sxs-lookup"><span data-stu-id="c3a93-132">Device is connected with type A connector</span></span>             |
| <span data-ttu-id="c3a93-133">UX_OTG_IDLE_TO_SLAVE</span><span class="sxs-lookup"><span data-stu-id="c3a93-133">UX_OTG_IDLE_TO_SLAVE</span></span> | <span data-ttu-id="c3a93-134">2</span><span class="sxs-lookup"><span data-stu-id="c3a93-134">2</span></span>     | <span data-ttu-id="c3a93-135">Устройство подключено с помощью разъема типа B.</span><span class="sxs-lookup"><span data-stu-id="c3a93-135">Device is connected with type B connector</span></span>             |
| <span data-ttu-id="c3a93-136">UX_OTG_HOST_TO_IDLE</span><span class="sxs-lookup"><span data-stu-id="c3a93-136">UX_OTG_HOST_TO_IDLE</span></span>  | <span data-ttu-id="c3a93-137">3</span><span class="sxs-lookup"><span data-stu-id="c3a93-137">3</span></span>     | <span data-ttu-id="c3a93-138">Устройство узла отключено.</span><span class="sxs-lookup"><span data-stu-id="c3a93-138">Host device got disconnected</span></span>                          |
| <span data-ttu-id="c3a93-139">UX_OTG_HOST_TO_SLAVE</span><span class="sxs-lookup"><span data-stu-id="c3a93-139">UX_OTG_HOST_TO_SLAVE</span></span> | <span data-ttu-id="c3a93-140">4</span><span class="sxs-lookup"><span data-stu-id="c3a93-140">4</span></span>     | <span data-ttu-id="c3a93-141">Идет переключение ролей с узла на подчиненное устройство.</span><span class="sxs-lookup"><span data-stu-id="c3a93-141">Role swap from Host to Slave</span></span>                          |
| <span data-ttu-id="c3a93-142">UX_OTG_SLAVE_TO_IDLE</span><span class="sxs-lookup"><span data-stu-id="c3a93-142">UX_OTG_SLAVE_TO_IDLE</span></span> | <span data-ttu-id="c3a93-143">5</span><span class="sxs-lookup"><span data-stu-id="c3a93-143">5</span></span>     | <span data-ttu-id="c3a93-144">Подчиненное устройство отключено.</span><span class="sxs-lookup"><span data-stu-id="c3a93-144">Slave device is disconnected</span></span>                          |
| <span data-ttu-id="c3a93-145">UX_OTG_SLAVE_TO_HOST</span><span class="sxs-lookup"><span data-stu-id="c3a93-145">UX_OTG_SLAVE_TO_HOST</span></span> | <span data-ttu-id="c3a93-146">6</span><span class="sxs-lookup"><span data-stu-id="c3a93-146">6</span></span>     | <span data-ttu-id="c3a93-147">Идет переключение ролей с подчиненного устройства на узел.</span><span class="sxs-lookup"><span data-stu-id="c3a93-147">Role swap from Slave to Host</span></span>                          |

## <a name="interrupt-handlers"></a><span data-ttu-id="c3a93-148">Обработчики прерываний</span><span class="sxs-lookup"><span data-stu-id="c3a93-148">Interrupt handlers</span></span>

<span data-ttu-id="c3a93-149">Драйверам контроллера в узле и на устройстве для использования OTG требуются другие обработчики прерываний, которые будут отслеживать дополнительные сигналы помимо традиционных прерываний USB, в частности это сигналы SRP и VBUS.</span><span class="sxs-lookup"><span data-stu-id="c3a93-149">Both host and device controller drivers for OTG needs different interrupt handlers to monitor signals beyond traditional USB interrupts, in particular signals due to SRP and VBUS.</span></span>

<span data-ttu-id="c3a93-150">Как же выполнить инициализацию контроллера OTG в USB?</span><span class="sxs-lookup"><span data-stu-id="c3a93-150">How to initialize a USB OTG controller.</span></span> <span data-ttu-id="c3a93-151">В качестве примера мы используем NXP LPC3131.</span><span class="sxs-lookup"><span data-stu-id="c3a93-151">We use the NXP LPC3131 as an example here.</span></span>

```C
/* Initialize the LPC3131 OTG controller. */
status = ux_otg_lpc3131_initialize(0x19000000, lpc3131_vbus_function,
    tx_demo_change_mode_callback);
```

<span data-ttu-id="c3a93-152">В нашем примере мы инициализируем LPC3131 в режиме OTG, передав функцию VBUS и обратный вызов для изменения режима (с узла на подчиненное устройство или наоборот).</span><span class="sxs-lookup"><span data-stu-id="c3a93-152">In this example, we initialize the LPC3131 in OTG mode by passing a VBUS function and a callback for mode change (from host to slave or vice versa).</span></span>

<span data-ttu-id="c3a93-153">Эта функция обратного вызова должна просто сохранить новый режим и пробудить ожидающий поток, чтобы он работал в новом состоянии.</span><span class="sxs-lookup"><span data-stu-id="c3a93-153">The callback function should simply record the new mode and wake up a pending thread to act up the new state.</span></span>

```C
void tx_demo_change_mode_callback(ULONG mode) {
    /* Simply save the otg mode. */
    otg_mode = mode;

    /* Wake up the thread that is waiting. */
    ux_utility_semaphore_put(&mode_change_semaphore);
}
```

<span data-ttu-id="c3a93-154">Передаваемое значение режима может иметь следующие значения.</span><span class="sxs-lookup"><span data-stu-id="c3a93-154">The mode value that is passed can have the following values.</span></span>

- <span data-ttu-id="c3a93-155">**UX_OTG_MODE_IDLE**;</span><span class="sxs-lookup"><span data-stu-id="c3a93-155">**UX_OTG_MODE_IDLE**</span></span>
- <span data-ttu-id="c3a93-156">**UX_OTG_MODE_SLAVE**;</span><span class="sxs-lookup"><span data-stu-id="c3a93-156">**UX_OTG_MODE_SLAVE**</span></span>
- <span data-ttu-id="c3a93-157">**UX_OTG_MODE_HOST**.</span><span class="sxs-lookup"><span data-stu-id="c3a93-157">**UX_OTG_MODE_HOST**</span></span>

<span data-ttu-id="c3a93-158">Приложение всегда может проверить роль устройства, считав эту переменную.</span><span class="sxs-lookup"><span data-stu-id="c3a93-158">The application can always check what the device is by looking at the variable:</span></span>

```C
_ux_system_otg -> ux_system_otg_device_type
```

<span data-ttu-id="c3a93-159">Она может иметь любое из следующих значений:</span><span class="sxs-lookup"><span data-stu-id="c3a93-159">Its values can be any of the following.</span></span>

- <span data-ttu-id="c3a93-160">**UX_OTG_DEVICE_A**;</span><span class="sxs-lookup"><span data-stu-id="c3a93-160">**UX_OTG_DEVICE_A**</span></span>
- <span data-ttu-id="c3a93-161">**UX_OTG_DEVICE_B**;</span><span class="sxs-lookup"><span data-stu-id="c3a93-161">**UX_OTG_DEVICE_B**</span></span>
- <span data-ttu-id="c3a93-162">**UX_OTG_DEVICE_IDLE**.</span><span class="sxs-lookup"><span data-stu-id="c3a93-162">**UX_OTG_DEVICE_IDLE**</span></span>

<span data-ttu-id="c3a93-163">Главное устройство OTG USB всегда может выполнить следующую команду, которая инициирует переключение ролей.</span><span class="sxs-lookup"><span data-stu-id="c3a93-163">A USB OTG host device can always ask for a role swap by issuing the following command.</span></span>

```C
/* Ask the stack to perform a HNP swap with the device. We relinquish the host role to A device. */
ux_host_stack_role_swap(storage -> ux_host_class_storage_device);
```

<span data-ttu-id="c3a93-164">Для подчиненного устройства такая команда не предусмотрена, но подчиненное устройство может установить состояние изменения роли, о котором узел узнает при выполнении команды **GET_STATUS** и сможет инициировать переключение.</span><span class="sxs-lookup"><span data-stu-id="c3a93-164">For a slave device, there is no command to issue but the slave device can set a state to change the role, which will be picked up by the host when it issues a **GET_STATUS** and the swap will then be initiated.</span></span>

```C
/* We are a B device, ask for role swap.
   The next GET_STATUS from the host will get the status change and do the HNP. */
_ux_system_otg -> ux_system_otg_slave_role_swap_flag =
    UX_OTG_HOST_REQUEST_FLAG;
```
