---
title: Глава 3. Функциональные компоненты стека устройств USBX
description: В этой главе приведено описание высокопроизводительного внедренного в USBX стека USB-устройств с точки зрения функциональности.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: dc57f3e0f6aa6731f4aaedee8169313ca7276cff
ms.sourcegitcommit: 1aeca2f91960856d8cc24fef65f909639e527599
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106082206"
---
# <a name="chapter-3---functional-components-of-usbx-device-stack"></a><span data-ttu-id="41062-103">Глава 3. Функциональные компоненты стека устройств USBX</span><span class="sxs-lookup"><span data-stu-id="41062-103">Chapter 3 - Functional Components of USBX Device Stack</span></span>

<span data-ttu-id="41062-104">В этой главе приведено описание высокопроизводительного внедренного в USBX стека USB-устройств с точки зрения функциональности.</span><span class="sxs-lookup"><span data-stu-id="41062-104">This chapter contains a description of the high performance USBX embedded USB device stack from a functional perspective.</span></span>

## <a name="execution-overview"></a><span data-ttu-id="41062-105">Общие сведения о выполнении</span><span class="sxs-lookup"><span data-stu-id="41062-105">Execution Overview</span></span>

<span data-ttu-id="41062-106">USBX для устройства включает несколько компонентов:</span><span class="sxs-lookup"><span data-stu-id="41062-106">USBX for the device is composed of several components.</span></span>

- <span data-ttu-id="41062-107">Инициализация</span><span class="sxs-lookup"><span data-stu-id="41062-107">Initialization</span></span>
- <span data-ttu-id="41062-108">вызовы интерфейса приложения;</span><span class="sxs-lookup"><span data-stu-id="41062-108">Application interface calls</span></span>
- <span data-ttu-id="41062-109">классы устройств;</span><span class="sxs-lookup"><span data-stu-id="41062-109">Device Classes</span></span>
- <span data-ttu-id="41062-110">стек USB-устройств;</span><span class="sxs-lookup"><span data-stu-id="41062-110">USB Device Stack</span></span>
- <span data-ttu-id="41062-111">контроллер устройства;</span><span class="sxs-lookup"><span data-stu-id="41062-111">Device controller</span></span>
- <span data-ttu-id="41062-112">диспетчер VBUS.</span><span class="sxs-lookup"><span data-stu-id="41062-112">VBUS manager</span></span>

<span data-ttu-id="41062-113">Стек устройств USBX показан на схеме ниже.</span><span class="sxs-lookup"><span data-stu-id="41062-113">The following diagram illustrates the USBX Device stack.</span></span>

![Стек устройств USBX](media/usbx-device-stack/usbx-device-stack.png)

### <a name="initialization"></a><span data-ttu-id="41062-115">Инициализация</span><span class="sxs-lookup"><span data-stu-id="41062-115">Initialization</span></span>

<span data-ttu-id="41062-116">Чтобы активировать USBX, нужно вызвать функцию ***ux_system_initialize***.</span><span class="sxs-lookup"><span data-stu-id="41062-116">In order to activate USBX, the function ***ux_system_initialize*** must be called.</span></span> <span data-ttu-id="41062-117">Эта функция инициализирует ресурсы памяти USBX.</span><span class="sxs-lookup"><span data-stu-id="41062-117">This function initializes the memory resources of USBX.</span></span>

<span data-ttu-id="41062-118">Чтобы активировать аппаратные ресурсы устройства USBX, необходимо вызвать функцию ***ux_device_stack_initialize***.</span><span class="sxs-lookup"><span data-stu-id="41062-118">In order to activate USBX device facilities, the function ***ux_device_stack_initialize*** must be called.</span></span> <span data-ttu-id="41062-119">Эта функция в свою очередь инициализирует все ресурсы, используемые стеком устройств USBX, например потоки ThreadX, мьютексы и семафоры.</span><span class="sxs-lookup"><span data-stu-id="41062-119">This function will in turn initialize all the resources used by the USBX device stack such as ThreadX threads, mutexes, and semaphores.</span></span>

<span data-ttu-id="41062-120">Активация контроллера USB-устройств и одного или нескольких классов USB выполняется уже при инициализации приложения.</span><span class="sxs-lookup"><span data-stu-id="41062-120">It is up to the application initialization to activate the USB device controller and one or more USB classes.</span></span> <span data-ttu-id="41062-121">В отличие от компьютера с USB, на стороне устройства в любое время может работать только один драйвер контроллера USB.</span><span class="sxs-lookup"><span data-stu-id="41062-121">Contrary to the USB host side, the device side can have only one USB controller driver running at any time.</span></span> <span data-ttu-id="41062-122">Если классы зарегистрированы в стеке и функция инициализации контроллеров устройств вызвана, шина активируется и стек будет реагировать на команды сброса шины и перечисления узла.</span><span class="sxs-lookup"><span data-stu-id="41062-122">When the classes have been registered to the stack and the device controller(s) initialization function has been called, the bus is active and the stack will reply to bus reset and host enumeration commands.</span></span>

### <a name="application-interface-calls"></a><span data-ttu-id="41062-123">Вызовы интерфейса приложения</span><span class="sxs-lookup"><span data-stu-id="41062-123">Application Interface Calls</span></span>

<span data-ttu-id="41062-124">В USBX доступно два уровня API:</span><span class="sxs-lookup"><span data-stu-id="41062-124">There are two levels of APIs in USBX.</span></span>

- <span data-ttu-id="41062-125">API стека USB-устройств;</span><span class="sxs-lookup"><span data-stu-id="41062-125">USB Device Stack APIs</span></span>
- <span data-ttu-id="41062-126">API классов USB-устройств.</span><span class="sxs-lookup"><span data-stu-id="41062-126">USB Device Class APIs</span></span>

<span data-ttu-id="41062-127">Как правило, приложение USBX не должно вызывать API стека USB-устройств.</span><span class="sxs-lookup"><span data-stu-id="41062-127">Normally, a USBX application should not have to call any of the USB device stack APIs.</span></span> <span data-ttu-id="41062-128">Большинство приложений обращаются только к API классов USB.</span><span class="sxs-lookup"><span data-stu-id="41062-128">Most applications will only access the USB Class APIs.</span></span>

### <a name="usb-device-stack-apis"></a><span data-ttu-id="41062-129">API стека USB-устройств</span><span class="sxs-lookup"><span data-stu-id="41062-129">USB Device Stack APIs</span></span>

<span data-ttu-id="41062-130">API стека устройств отвечают за регистрацию компонентов устройств USBX, таких как классы и структура устройств.</span><span class="sxs-lookup"><span data-stu-id="41062-130">The device stack APIs are responsible for the registration of USBX device components such as classes and the device framework.</span></span>

### <a name="usb-device-class-apis"></a><span data-ttu-id="41062-131">API классов USB-устройств</span><span class="sxs-lookup"><span data-stu-id="41062-131">USB Device Class APIs</span></span>

<span data-ttu-id="41062-132">Интерфейсы API классов для каждого класса USB сильно различаются.</span><span class="sxs-lookup"><span data-stu-id="41062-132">The Class APIs are very specific to each USB class.</span></span> <span data-ttu-id="41062-133">Большинство популярных API для классов USB предоставляют такие возможности, как выключение/включение устройства и считывание/запись на устройстве.</span><span class="sxs-lookup"><span data-stu-id="41062-133">Most of the common APIs for USB classes provided services such as opening/closing a device and reading from and writing to a device.</span></span> <span data-ttu-id="41062-134">Эти API по своей природе похожи на API на стороне компьютера.</span><span class="sxs-lookup"><span data-stu-id="41062-134">The APIs are similar in nature to the host side.</span></span>

## <a name="device-framework"></a><span data-ttu-id="41062-135">Структура устройства</span><span class="sxs-lookup"><span data-stu-id="41062-135">Device Framework</span></span>

<span data-ttu-id="41062-136">Сторона USB-устройства отвечает за определение структуры устройства.</span><span class="sxs-lookup"><span data-stu-id="41062-136">The USB device side is responsible for the definition of the device framework.</span></span> <span data-ttu-id="41062-137">Структура устройства разделяется на три категории, как описано в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="41062-137">The device framework is divided into three categories, as described in the following sections.</span></span>

### <a name="definition-of-the-components-of-the-device-framework"></a><span data-ttu-id="41062-138">Определение компонентов структуры устройства</span><span class="sxs-lookup"><span data-stu-id="41062-138">Definition of the Components of the Device Framework</span></span>

<span data-ttu-id="41062-139">Определение каждого компонента в структуре устройства зависит от особенностей устройства и используемых им ресурсов.</span><span class="sxs-lookup"><span data-stu-id="41062-139">The definition of each component of the device framework is related to the nature of the device and the resources utilized by the device.</span></span> <span data-ttu-id="41062-140">Основные категории:</span><span class="sxs-lookup"><span data-stu-id="41062-140">Following are the main categories.</span></span>

- <span data-ttu-id="41062-141">дескриптор устройства;</span><span class="sxs-lookup"><span data-stu-id="41062-141">Device Descriptor</span></span>
- <span data-ttu-id="41062-142">дескриптор конфигурации;</span><span class="sxs-lookup"><span data-stu-id="41062-142">Configuration Descriptor</span></span>
- <span data-ttu-id="41062-143">дескриптор интерфейса;</span><span class="sxs-lookup"><span data-stu-id="41062-143">Interface Descriptor</span></span>
- <span data-ttu-id="41062-144">дескриптор конечной точки.</span><span class="sxs-lookup"><span data-stu-id="41062-144">Endpoint Descriptor</span></span>

<span data-ttu-id="41062-145">USBX поддерживает определение компонентов устройства для спецификаций High Speed и Full Speed (Low Speed рассматривается как Full Speed).</span><span class="sxs-lookup"><span data-stu-id="41062-145">USBX supports device component definition for both high and full speed (low speed being treated the same way as full speed).</span></span> <span data-ttu-id="41062-146">Это позволяет устройству менять режим работы при подключении к компьютеру в зависимости от интерфейса (High Speed или Full Speed).</span><span class="sxs-lookup"><span data-stu-id="41062-146">This allows the device to operate differently when connected to a high speed or full speed host.</span></span> <span data-ttu-id="41062-147">Отличаются обычно размер каждой конечной точки и потребляемая устройством энергия.</span><span class="sxs-lookup"><span data-stu-id="41062-147">The typical differences are the size of each endpoint and the power consumed by the device.</span></span>

<span data-ttu-id="41062-148">Определение компонента устройства принимает вид байтовой строки, соответствующей USB-спецификации.</span><span class="sxs-lookup"><span data-stu-id="41062-148">The definition of the device component takes the form of a byte string that follows the USB specification.</span></span> <span data-ttu-id="41062-149">Определение не фрагментируется, а порядок, в котором структура представляется в памяти, не отличается от порядка, в котором структура возвращается компьютеру при перечислении.</span><span class="sxs-lookup"><span data-stu-id="41062-149">The definition is contiguous and the order in which the framework is represented in memory will be the same as the one returned to the host during enumeration.</span></span>

<span data-ttu-id="41062-150">Ниже приведен пример структуры устройства для флэш-накопителя USB с подключением High Speed.</span><span class="sxs-lookup"><span data-stu-id="41062-150">Following is an example of a device framework for a high speed USB Flash Disk.</span></span>

```c
#define DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED 60
UCHAR device_framework_high_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40, 0x0a, 0x07, 0x25, 0x40, 0x01, 0x00, 0x01, 0x02, 0x03, 0x01,

    /* Device qualifier descriptor */
    0x0a, 0x06, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40, 0x01, 0x00,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0, 0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50, 0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x00, 0x02, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x00, 0x02, 0x00
};
```

### <a name="definition-of-the-strings-of-the-device-framework"></a><span data-ttu-id="41062-151">Определение строк структуры устройства</span><span class="sxs-lookup"><span data-stu-id="41062-151">Definition of the Strings of the Device Framework</span></span>

<span data-ttu-id="41062-152">Строки необязательны на устройстве.</span><span class="sxs-lookup"><span data-stu-id="41062-152">Strings are optional in a device.</span></span> <span data-ttu-id="41062-153">Их назначение — сообщить компьютеру с USB о производителе устройства, имени продукта и номере редакции с помощью строк в формате Юникода.</span><span class="sxs-lookup"><span data-stu-id="41062-153">Their purpose is to let the USB host know about the manufacturer of the device, the product name, and the revision number through Unicode strings.</span></span>

<span data-ttu-id="41062-154">Основные строки представляют собой индексы, внедренные в дескрипторы устройств.</span><span class="sxs-lookup"><span data-stu-id="41062-154">The main strings are indexes embedded in the device descriptors.</span></span> <span data-ttu-id="41062-155">Дополнительные индексы строк можно внедрить в отдельные интерфейсы.</span><span class="sxs-lookup"><span data-stu-id="41062-155">Additional strings indexes can be embedded into individual interfaces.</span></span>

<span data-ttu-id="41062-156">Если приведенная выше структура устройства включает три строковых индекса, внедренных в дескриптор устройства, строковое определение структуры будет выглядеть примерно так, как показано в этом примере кода.</span><span class="sxs-lookup"><span data-stu-id="41062-156">Assuming the device framework above has three string indexes embedded into the device descriptor, the string framework definition could look like this example code.</span></span>

```c
/* String Device Framework:
    Byte 0 and 1: Word containing the language ID: 0x0904 for US
    Byte 2 : Byte containing the index of the descriptor
    Byte 3 : Byte containing the length of the descriptor string
*/

#define STRING_FRAMEWORK_LENGTH 38
UCHAR string_framework[] = {
    /* Manufacturer string descriptor: Index 1 */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72, 0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,

    /* Product string descriptor: Index 2 */
    0x09, 0x04, 0x02, 0x0c,
    0x4D, 0x4C, 0x36, 0x39, 0x36, 0x35, 0x30, 0x30,
    0x20, 0x53, 0x44, 0x4B,

    /* Serial Number string descriptor: Index 3 */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31
};
```

<span data-ttu-id="41062-157">Если нужно использовать разные строки для отдельных скоростных режимов, также потребуются и разные индексы, так как они не зависят от скорости.</span><span class="sxs-lookup"><span data-stu-id="41062-157">If different strings have to be used for each speed, different indexes must be used as the indexes are speed agnostic.</span></span>

<span data-ttu-id="41062-158">При кодировании строки используется формат Юникода.</span><span class="sxs-lookup"><span data-stu-id="41062-158">The encoding of the string is UNICODE-based.</span></span> <span data-ttu-id="41062-159">Дополнительные сведения о стандарте кодирования "Юникод" см. в следующей публикации:</span><span class="sxs-lookup"><span data-stu-id="41062-159">For more information on the UNICODE encoding standard refer to the following publication:</span></span>

<span data-ttu-id="41062-160">*The Unicode Standard, Worldwide Character Encoding, Version 1., Volumes 1 and 2, The Unicode Consortium, Addison-Wesley Publishing Company, Reading MA* (Юникод — международный стандарт кодирования символов).</span><span class="sxs-lookup"><span data-stu-id="41062-160">*The Unicode Standard, Worldwide Character Encoding, Version 1., Volumes 1 and 2, The Unicode Consortium, Addison-Wesley Publishing Company, Reading MA.*</span></span>

### <a name="definition-of-the-languages-supported-by-the-device-for-each-string"></a><span data-ttu-id="41062-161">Определение языков, поддерживаемых устройством для каждой строки</span><span class="sxs-lookup"><span data-stu-id="41062-161">Definition of the Languages Supported by the Device for each String</span></span>

<span data-ttu-id="41062-162">USBX может поддерживать различные языки, хотя по умолчанию используется английский.</span><span class="sxs-lookup"><span data-stu-id="41062-162">USBX has the ability to support multiple languages although English is the default.</span></span> <span data-ttu-id="41062-163">Определение каждого языка для строковых дескрипторов представлено в виде массива определений языков следующим образом.</span><span class="sxs-lookup"><span data-stu-id="41062-163">The definition of each language for the string descriptors is in the form of an array of languages definition defined as follows.</span></span>

```c
#define LANGUAGE_ID_FRAMEWORK_LENGTH 2
UCHAR language_id_framework[] = {
    /* English. */
    0x09, 0x04
};
```

<span data-ttu-id="41062-164">Для поддержки дополнительных языков просто добавьте двухбайтовое определение кода языка после кода для английского языка.</span><span class="sxs-lookup"><span data-stu-id="41062-164">To support additional languages, simply add the language code double-byte definition after the default English code.</span></span> <span data-ttu-id="41062-165">Коды языков определены корпорацией Майкрософт в следующем документе:</span><span class="sxs-lookup"><span data-stu-id="41062-165">The language code has been defined by Microsoft in the document.</span></span>

<span data-ttu-id="41062-166">*Developing International Software for Windows 95 and Windows NT, Nadine Kano, Microsoft Press, Redmond WA* (Разработка международного программного обеспечения для Windows 95 и Windows NT)</span><span class="sxs-lookup"><span data-stu-id="41062-166">*Developing International Software for Windows 95 and Windows NT, Nadine Kano, Microsoft Press, Redmond WA*</span></span>

## <a name="vbus-manager"></a><span data-ttu-id="41062-167">Диспетчер VBUS</span><span class="sxs-lookup"><span data-stu-id="41062-167">VBUS Manager</span></span>

<span data-ttu-id="41062-168">В большинстве архитектур USB-устройств VBUS не является частью ядра USB-устройства, а подключается к внешнему интерфейсу GPIO, который отслеживает линейный сигнал.</span><span class="sxs-lookup"><span data-stu-id="41062-168">In most USB device designs, VBUS is not part of the USB Device core but rather connected to an external GPIO, which monitors the line signal.</span></span>

<span data-ttu-id="41062-169">Поэтому VBUS необходимо управлять отдельно от драйвера контроллера устройств.</span><span class="sxs-lookup"><span data-stu-id="41062-169">As a result, VBUS has to be managed separately from the device controller driver.</span></span>

<span data-ttu-id="41062-170">Именно приложение должно предоставить контроллеру устройств адрес ввода-вывода для VBUS.</span><span class="sxs-lookup"><span data-stu-id="41062-170">It is up to the application to provide the device controller with the address of the VBUS IO.</span></span> <span data-ttu-id="41062-171">VBUS нужно инициализировать до инициализации контроллера устройств.</span><span class="sxs-lookup"><span data-stu-id="41062-171">VBUS must be initialized prior to the device controller initialization.</span></span>

<span data-ttu-id="41062-172">Некоторые спецификации платформы для мониторинга VBUS позволяют передать драйверу контроллера обработку сигналов VBUS после инициализации ввода-вывода для VBUS или, если это возможно, приложение должно предоставить код для обработки сигналов VBUS.</span><span class="sxs-lookup"><span data-stu-id="41062-172">Depending on the platform specification for monitoring VBUS, it is possible to let the controller driver handle VBUS signals after the VBUS IO is initialized or if this is not possible, the application has to provide the code for handling VBUS.</span></span>

<span data-ttu-id="41062-173">Если приложение должно обрабатывать сигналы VBUS самостоятельно, ему нужно вызывать функцию ***ux_device_stack_disconnect***, когда оно определяет, что устройство было отключено.</span><span class="sxs-lookup"><span data-stu-id="41062-173">If the application wishes to handle VBUS by itself, its only requirement is to call the function ***ux_device_stack_disconnect*** when it detects that a device has been extracted.</span></span> <span data-ttu-id="41062-174">Сообщать контроллеру о подключении устройства необязательно, так как контроллер включается автоматически при обнаружении сигнала активации или отмены BUS RESET.</span><span class="sxs-lookup"><span data-stu-id="41062-174">It is not necessary to inform the controller when a device is inserted because the controller will wake up when the BUS RESET assert/deassert signal is detected.</span></span>
