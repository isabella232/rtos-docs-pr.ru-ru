---
title: Глава 5. OTG в USBX
description: Узнайте подробности о поддержке USBX функциональных возможностей OTG для USB, если в архитектуре оборудования присутствует контроллер USB, совместимый с OTG.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1a0abe355f05492edb74635db2aa6607abbcf9de6b2693290b06b740d2b9286d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791063"
---
# <a name="chapter-5---usbx-otg"></a>Глава 5. OTG в USBX

USBX поддерживает функциональные возможности OTG для USB, если в архитектуре оборудования присутствует контроллер USB, совместимый с OTG.

USBX поддерживает OTG в основном стеке USB. Но для работы OTG подходит не любой контроллер USB. Функции контроллера OTG для USBX можно найти в каталоге usbx_otg. Текущая версия USBX полностью поддерживает возможности OTG только для NXP LPC3131.

Стандартные функции драйвера контроллера (на узле или на устройстве) по-прежнему размещаются в стандартных файлах USBX (usbx_device_controllers и usbx_host_controllers), а каталог usbx_otg содержит только функции OTG, связанные с контроллером USB.

Существует четыре категории функций контроллера OTG, дополняющих обычные функции узла и устройства:

- функции VBUS;
- запуск и остановка контроллера;
- диспетчер ролей USB;
- обработчики прерываний.

## <a name="vbus-functions"></a>Функции VBUS

Каждый контроллер должен иметь диспетчер VBUS, чтобы изменять состояние VBUS с учетом требований к управлению питанием. Обычно его функциональность ограничивается включением и отключением VBUS.

## <a name="start-and-stop-the-controller"></a>Запуск и остановка контроллера

В отличие от обычной реализации USB, для OTG нужно, чтобы стек узла и (или) устройства изменял состояние активации при изменении роли.

## <a name="usb-role-manager"></a>Диспетчер ролей USB

Диспетчер ролей USB получает команды на изменение состояния USB. Существует несколько состояний, в которые и из которых может потребоваться переход.

| Состояние                    | Значение | Описание                                           |
| ------------------------ | ----- | ----------------------------------------------------- |
| UX_OTG_IDLE            | 0     | Устройство неактивно. Нет никаких подключений. |
| UX_OTG_IDLE_TO_HOST  | 1     | Устройство подключено с помощью разъема типа A.             |
| UX_OTG_IDLE_TO_SLAVE | 2     | Устройство подключено с помощью разъема типа B.             |
| UX_OTG_HOST_TO_IDLE  | 3     | Устройство узла отключено.                          |
| UX_OTG_HOST_TO_SLAVE | 4     | Идет переключение ролей с узла на подчиненное устройство.                          |
| UX_OTG_SLAVE_TO_IDLE | 5     | Подчиненное устройство отключено.                          |
| UX_OTG_SLAVE_TO_HOST | 6     | Идет переключение ролей с подчиненного устройства на узел.                          |

## <a name="interrupt-handlers"></a>Обработчики прерываний

Драйверам контроллера в узле и на устройстве для использования OTG требуются другие обработчики прерываний, которые будут отслеживать дополнительные сигналы помимо традиционных прерываний USB, в частности это сигналы SRP и VBUS.

Как же выполнить инициализацию контроллера OTG в USB? В качестве примера мы используем NXP LPC3131.

```C
/* Initialize the LPC3131 OTG controller. */
status = ux_otg_lpc3131_initialize(0x19000000, lpc3131_vbus_function,
    tx_demo_change_mode_callback);
```

В нашем примере мы инициализируем LPC3131 в режиме OTG, передав функцию VBUS и обратный вызов для изменения режима (с узла на подчиненное устройство или наоборот).

Эта функция обратного вызова должна просто сохранить новый режим и пробудить ожидающий поток, чтобы он работал в новом состоянии.

```C
void tx_demo_change_mode_callback(ULONG mode) {
    /* Simply save the otg mode. */
    otg_mode = mode;

    /* Wake up the thread that is waiting. */
    ux_utility_semaphore_put(&mode_change_semaphore);
}
```

Передаваемое значение режима может иметь следующие значения.

- **UX_OTG_MODE_IDLE**;
- **UX_OTG_MODE_SLAVE**;
- **UX_OTG_MODE_HOST**.

Приложение всегда может проверить роль устройства, считав эту переменную.

```C
_ux_system_otg -> ux_system_otg_device_type
```

Она может иметь любое из следующих значений:

- **UX_OTG_DEVICE_A**;
- **UX_OTG_DEVICE_B**;
- **UX_OTG_DEVICE_IDLE**.

Главное устройство OTG USB всегда может выполнить следующую команду, которая инициирует переключение ролей.

```C
/* Ask the stack to perform a HNP swap with the device. We relinquish the host role to A device. */
ux_host_stack_role_swap(storage -> ux_host_class_storage_device);
```

Для подчиненного устройства такая команда не предусмотрена, но подчиненное устройство может установить состояние изменения роли, о котором узел узнает при выполнении команды **GET_STATUS** и сможет инициировать переключение.

```C
/* We are a B device, ask for role swap.
   The next GET_STATUS from the host will get the status change and do the HNP. */
_ux_system_otg -> ux_system_otg_slave_role_swap_flag =
    UX_OTG_HOST_REQUEST_FLAG;
```
