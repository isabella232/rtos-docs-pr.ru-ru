---
title: Глава 4. Описание служб ОСРВ Azure NetX LWM2M
description: В этой главе приводится описание всех служб ОСРВ Azure NetX LWM2M, которые перечислены ниже в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d5a402790387c2720db304fe93d74252494d7638
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815168"
---
# <a name="chapter-4---description-of-azure-rtos-netx-lwm2m-services"></a><span data-ttu-id="15b51-103">Глава 4. Описание служб ОСРВ Azure NetX LWM2M</span><span class="sxs-lookup"><span data-stu-id="15b51-103">Chapter 4 - Description of Azure RTOS NetX LWM2M services</span></span>

<span data-ttu-id="15b51-104">В этой главе приводится описание всех служб ОСРВ Azure NetX LWM2M, которые перечислены ниже в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="15b51-104">This chapter contains a description of all Azure RTOS NetX LWM2M services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="15b51-105">В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, используемым для отключения проверки ошибок API, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="15b51-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

### <a name="lwm2m-client-management"></a><span data-ttu-id="15b51-106">Управление клиентом LWM2M</span><span class="sxs-lookup"><span data-stu-id="15b51-106">LWM2M Client Management</span></span>

- <span data-ttu-id="15b51-107">**nx_lwm2m_client_create**: *создание клиента LWM2M*.</span><span class="sxs-lookup"><span data-stu-id="15b51-107">**nx_lwm2m_client_create**: *Create LWM2M Client*</span></span>
- <span data-ttu-id="15b51-108">**nx_lwm2m_client_delete**: *удаление клиента LWM2M*.</span><span class="sxs-lookup"><span data-stu-id="15b51-108">**nx_lwm2m_client_delete**: *Delete LWM2M Client*</span></span>
- <span data-ttu-id="15b51-109">**nx_lwm2m_client_lock**: *блокирование клиента LWM2M*.</span><span class="sxs-lookup"><span data-stu-id="15b51-109">**nx_lwm2m_client_lock**: *Lock LWM2M Client*</span></span>
- <span data-ttu-id="15b51-110">**nx_lwm2m_client_object_add**: *добавление реализации объекта в клиент LWM2M*.</span><span class="sxs-lookup"><span data-stu-id="15b51-110">**nx_lwm2m_client_object_add**: *Add Object implementation to the LWM2M Client*</span></span>
- <span data-ttu-id="15b51-111">**nx_lwm2m_client_unlock**: *разблокирование клиента LWM2M*.</span><span class="sxs-lookup"><span data-stu-id="15b51-111">**nx_lwm2m_client_unlock**: *Unlock LWM2M Client*</span></span>

### <a name="lwm2m-client-session-management"></a><span data-ttu-id="15b51-112">Управление сеансами клиентов LWM2M</span><span class="sxs-lookup"><span data-stu-id="15b51-112">LWM2M Client Session Management</span></span>

- <span data-ttu-id="15b51-113">**nx_lwm2m_client_session_bootstrap**: *запуск сеанса с сервером начальной загрузки*.</span><span class="sxs-lookup"><span data-stu-id="15b51-113">**nx_lwm2m_client_session_bootstrap**: *Start a session with a Bootstrap Server*</span></span>
- <span data-ttu-id="15b51-114">**nx_lwm2m_client_session_bootstrap_dtls**: *запуск безопасного сеанса с сервером начальной загрузки*.</span><span class="sxs-lookup"><span data-stu-id="15b51-114">**nx_lwm2m_client_session_bootstrap_dtls**: *Start a secure session with a Bootstrap Server*</span></span>
- <span data-ttu-id="15b51-115">**nx_lwm2m_client_session_create**: *создание сеанса клиента LWM2M*.</span><span class="sxs-lookup"><span data-stu-id="15b51-115">**nx_lwm2m_client_session_create**: *Create LWM2M Client Session*</span></span>
- <span data-ttu-id="15b51-116">**nx_lwm2m_client_session_delete**: *удаление сеанса клиента LWM2M*.</span><span class="sxs-lookup"><span data-stu-id="15b51-116">**nx_lwm2m_client_session_delete**: *Delete LWM2M Client Session*</span></span>
- <span data-ttu-id="15b51-117">**nx_lwm2m_client_session_deregister**: *завершение сеанса взаимодействия с сервером LWM2M*.</span><span class="sxs-lookup"><span data-stu-id="15b51-117">**nx_lwm2m_client_session_deregister**: *Terminate a session with a LWM2M Server*</span></span>
- <span data-ttu-id="15b51-118">**nx_lwm2m_client_session_error_get**: *получение сведений о последней ошибке сеанса*.</span><span class="sxs-lookup"><span data-stu-id="15b51-118">**nx_lwm2m_client_session_error_get**: *Get last error of a session*</span></span>
- <span data-ttu-id="15b51-119">**nx_lwm2m_client_session_register**: *запуск сеанса взаимодействия с сервером LWM2M*.</span><span class="sxs-lookup"><span data-stu-id="15b51-119">**nx_lwm2m_client_session_register**: *Start a session with a LWM2M Server*</span></span>
- <span data-ttu-id="15b51-120">**nx_lwm2m_client_session_register_dtls**: *запуск безопасного сеанса взаимодействия с сервером LWM2M*.</span><span class="sxs-lookup"><span data-stu-id="15b51-120">**nx_lwm2m_client_session_register_dtls**: *Start a secure session with a LWM2M Server*</span></span>
- <span data-ttu-id="15b51-121">**nx_lwm2m_client_session_update**: *обновление сеанса взаимодействия с сервером LWM2M*.</span><span class="sxs-lookup"><span data-stu-id="15b51-121">**nx_lwm2m_client_session_update**: *Update a session with a LWM2M Server*</span></span>

### <a name="security-object-implementation"></a><span data-ttu-id="15b51-122">Реализация объекта безопасности</span><span class="sxs-lookup"><span data-stu-id="15b51-122">Security Object Implementation</span></span>

- <span data-ttu-id="15b51-123">**nx_lwm2m_client_security_key_callbacks_set**: *настройка обратных вызовов управления ключами безопасности*.</span><span class="sxs-lookup"><span data-stu-id="15b51-123">**nx_lwm2m_client_security_key_callbacks_set**: *Set security key management callbacks*</span></span>

### <a name="device-object-implementation"></a><span data-ttu-id="15b51-124">Реализация объекта устройства</span><span class="sxs-lookup"><span data-stu-id="15b51-124">Device Object Implementation</span></span>

- <span data-ttu-id="15b51-125">**nx_lwm2m_client_device_callbacks_set**: *настройка обратных вызовов приложения объекта устройства*.</span><span class="sxs-lookup"><span data-stu-id="15b51-125">**nx_lwm2m_client_device_callbacks_set**: *Set Device Object application callbacks*</span></span>
- <span data-ttu-id="15b51-126">**nx_lwm2m_client_device_error_push**: *добавление кода ошибки в объект устройства*.</span><span class="sxs-lookup"><span data-stu-id="15b51-126">**nx_lwm2m_client_device_error_push**: *Add error code to Device Object*</span></span>
- <span data-ttu-id="15b51-127">**nx_lwm2m_client_device_error_reset**: *сброс кодов ошибок объекта устройства*.</span><span class="sxs-lookup"><span data-stu-id="15b51-127">**nx_lwm2m_client_device_error_reset**: *Reset error codes of Device Object*</span></span>
- <span data-ttu-id="15b51-128">**nx_lwm2m_client_device_resource_changed**: *сигнальное изменение ресурса объекта устройства*.</span><span class="sxs-lookup"><span data-stu-id="15b51-128">**nx_lwm2m_client_device_resource_changed**: *Signal change of Device Object resource*</span></span>

### <a name="custom-objects-implementation"></a><span data-ttu-id="15b51-129">Реализация пользовательских объектов</span><span class="sxs-lookup"><span data-stu-id="15b51-129">Custom Objects Implementation</span></span>

- <span data-ttu-id="15b51-130">**nx_lwm2m_object_resource_changed**: *сигнальное изменение значения ресурса экземпляра объекта*.</span><span class="sxs-lookup"><span data-stu-id="15b51-130">**nx_lwm2m_object_resource_changed**: *Signal change of a resource value of an Object Instance*</span></span>

### <a name="local-device-management"></a><span data-ttu-id="15b51-131">Управление локальным устройством</span><span class="sxs-lookup"><span data-stu-id="15b51-131">Local Device Management</span></span>

- <span data-ttu-id="15b51-132">**nx_lwm2m_client_object_create**: *создание нового экземпляра объекта*.</span><span class="sxs-lookup"><span data-stu-id="15b51-132">**nx_lwm2m_client_object_create**: *Create a new Object Instance*</span></span>
- <span data-ttu-id="15b51-133">**nx_lwm2m_client_object_delete**: *удаление экземпляра объекта*.</span><span class="sxs-lookup"><span data-stu-id="15b51-133">**nx_lwm2m_client_object_delete**: *Delete an Object Instance*</span></span>
- <span data-ttu-id="15b51-134">**nx_lwm2m_client_object_discover**: *обнаружение ресурсов экземпляра объекта*.</span><span class="sxs-lookup"><span data-stu-id="15b51-134">**nx_lwm2m_client_object_discover**: *Discover resources of an Object Instance*</span></span>
- <span data-ttu-id="15b51-135">**nx_lwm2m_client_object_execute**: *выполнение ресурса экземпляра объекта*.</span><span class="sxs-lookup"><span data-stu-id="15b51-135">**nx_lwm2m_client_object_execute**: *Execute resource of an Object Instance*</span></span>
- <span data-ttu-id="15b51-136">**nx_lwm2m_client_object_next_get**: *получение списка объектов, реализованных в клиенте LWM2M*.</span><span class="sxs-lookup"><span data-stu-id="15b51-136">**nx_lwm2m_client_object_get_next**: *Get the list of Objects implemented by the LWM2M Client*</span></span>
- <span data-ttu-id="15b51-137">**nx_lwm2m_client_object_instance_get_next**: *получение списка экземпляров объекта*.</span><span class="sxs-lookup"><span data-stu-id="15b51-137">**nx_lwm2m_client_object_instance_get_next**: *Get the list of Instances of an Object*</span></span>
- <span data-ttu-id="15b51-138">**nx_lwm2m_client_object_read**: *чтение значений ресурсов экземпляра объекта*.</span><span class="sxs-lookup"><span data-stu-id="15b51-138">**nx_lwm2m_client_object_read**: *Read resources values of an Object Instance*</span></span>
- <span data-ttu-id="15b51-139">**nx_lwm2m_client_object_write**: *изменение значений ресурсов экземпляра объекта*.</span><span class="sxs-lookup"><span data-stu-id="15b51-139">**nx_lwm2m_client_object_write**: *Change resources values of an Object instance*</span></span>

### <a name="resources-values-decoding"></a><span data-ttu-id="15b51-140">Декодирование значений ресурсов</span><span class="sxs-lookup"><span data-stu-id="15b51-140">Resources Values Decoding</span></span>

- <span data-ttu-id="15b51-141">**nx_lwm2m_client_resource_boolean_get**: *получение значения логического ресурса*.</span><span class="sxs-lookup"><span data-stu-id="15b51-141">**nx_lwm2m_resource_get_boolean**: *Get the value of a Boolean Resource*</span></span>
- <span data-ttu-id="15b51-142">**nx_lwm2m_resource_get_float32**: *получение значения 32-разрядного ресурса с плавающей запятой*.</span><span class="sxs-lookup"><span data-stu-id="15b51-142">**nx_lwm2m_resource_get_float32**: *Get the value of a 32-bit Floating Point Resource*</span></span>
- <span data-ttu-id="15b51-143">**nx_lwm2m_resource_get_float64**: *получение значения 64-разрядного ресурса с плавающей запятой*.</span><span class="sxs-lookup"><span data-stu-id="15b51-143">**nx_lwm2m_resource_get_float64**: *Get the value of a 64-bit Floating Point Resource*</span></span>
- <span data-ttu-id="15b51-144">**nx_lwm2m_resource_get_integer32**: *получение значения 32-разрядного целочисленного ресурса*.</span><span class="sxs-lookup"><span data-stu-id="15b51-144">**nx_lwm2m_resource_get_integer32**: *Get the value of a 32-Bit Integer Resource*</span></span>
- <span data-ttu-id="15b51-145">**nx_lwm2m_resource_get_integer64**: *получение значения 64-разрядного целочисленного ресурса*.</span><span class="sxs-lookup"><span data-stu-id="15b51-145">**nx_lwm2m_resource_get_integer64**: *Get the value of a 64-Bit Integer Resource*</span></span>
- <span data-ttu-id="15b51-146">**nx_lwm2m_resource_get_objlnk**: *получение значения ресурса ссылки на объект*.</span><span class="sxs-lookup"><span data-stu-id="15b51-146">**nx_lwm2m_resource_get_objlnk**: *Get the value of an Object Link Resource*</span></span>
- <span data-ttu-id="15b51-147">**nx_lwm2m_resource_get_opaque**: *получение значения непрозрачного ресурса*.</span><span class="sxs-lookup"><span data-stu-id="15b51-147">**nx_lwm2m_resource_get_opaque**: *Get the value of an Opaque Resource*</span></span>
- <span data-ttu-id="15b51-148">**nx_lwm2m_resource_get_string**: *получение значения строкового ресурса*.</span><span class="sxs-lookup"><span data-stu-id="15b51-148">**nx_lwm2m_resource_get_string**: *Get the value of a String Resource*</span></span>
- <span data-ttu-id="15b51-149">**nx_lwm2m_resource_multiple_get_boolean**: *получение значения логического ресурса для нескольких экземпляров ресурса*.</span><span class="sxs-lookup"><span data-stu-id="15b51-149">**nx_lwm2m_resource_multiple_get_boolean**: *Get the value of a Boolean Resource Multiple Resource Instance*</span></span>
- <span data-ttu-id="15b51-150">**nx_lwm2m_resource_multiple_get_float32**: *получение значения 32-разрядного ресурса с плавающей запятой для нескольких экземпляров ресурса*.</span><span class="sxs-lookup"><span data-stu-id="15b51-150">**nx_lwm2m_resource_multiple_get_float32**: *Get the value of a 32-bit Floating Point Multiple Resource Instance*</span></span>
- <span data-ttu-id="15b51-151">**nx_lwm2m_resource_multiple_get_float64**: *получение значения 64-разрядного ресурса с плавающей запятой для нескольких экземпляров ресурса*.</span><span class="sxs-lookup"><span data-stu-id="15b51-151">**nx_lwm2m_resource_multiple_get_float64**: *Get the value of a 64-bit Floating Point Multiple Resource Instance*</span></span>
- <span data-ttu-id="15b51-152">**nx_lwm2m_resource_multiple_get_integer32**: *получение значения 32-разрядного целочисленного ресурса для нескольких экземпляров ресурса*.</span><span class="sxs-lookup"><span data-stu-id="15b51-152">**nx_lwm2m_resource_multiple_get_integer32**: *Get the value of a 32-Bit Integer Multiple Resource Instance*</span></span>
- <span data-ttu-id="15b51-153">**nx_lwm2m_resource_multiple_get_integer64**: *получение значения 64-разрядного целочисленного ресурса для нескольких экземпляров ресурса*.</span><span class="sxs-lookup"><span data-stu-id="15b51-153">**nx_lwm2m_resource_multiple_get_integer64**: *Get the value of a 64-Bit Integer Multiple Resource Instance*</span></span>
- <span data-ttu-id="15b51-154">**nx_lwm2m_resource_multiple_get_objlnk**: *получение значения ссылки на объект для нескольких экземпляров ресурса*.</span><span class="sxs-lookup"><span data-stu-id="15b51-154">**nx_lwm2m_resource_multiple_get_objlnk**: *Get the value of an Object Link Multiple Resource Instance*</span></span>
- <span data-ttu-id="15b51-155">**nx_lwm2m_resource_multiple_get_opaque**: *получение значения непрозрачного ресурса для нескольких экземпляров ресурса*.</span><span class="sxs-lookup"><span data-stu-id="15b51-155">**nx_lwm2m_resource_multiple_get_opaque**: *Get the value of an Opaque Multiple Resource Instance*</span></span>
- <span data-ttu-id="15b51-156">**nx_lwm2m_resource_multiple_get_string**: *получение значения строкового ресурса для нескольких экземпляров ресурса*.</span><span class="sxs-lookup"><span data-stu-id="15b51-156">**nx_lwm2m_resource_multiple_get_string**: *Get the value of a String Multiple Resource Instance*</span></span>

### <a name="firmware-update-object"></a><span data-ttu-id="15b51-157">Объект обновления встроенного ПО</span><span class="sxs-lookup"><span data-stu-id="15b51-157">Firmware Update Object</span></span>

- <span data-ttu-id="15b51-158">**nx_lwm2m_firmware_create**: *создание объекта обновления встроенного ПО*.</span><span class="sxs-lookup"><span data-stu-id="15b51-158">**nx_lwm2m_firmware_create**: *Create Firmware Update Object*</span></span>
- <span data-ttu-id="15b51-159">**nx_lwm2m_firmware_package_info_set**: *настройка сведений о пакете обновления встроенного ПО*.</span><span class="sxs-lookup"><span data-stu-id="15b51-159">**nx_lwm2m_firmware_package_info_set**: *Set Firmware Update Package Information*</span></span>
- <span data-ttu-id="15b51-160">**nx_lwm2m_firmware_result_set**: *настройка результата обновления встроенного ПО*.</span><span class="sxs-lookup"><span data-stu-id="15b51-160">**nx_lwm2m_firmware_result_set**: *Set Firmware Update Result*</span></span>
- <span data-ttu-id="15b51-161">**nx_lwm2m_firmware_state_set**: *настройка состояния обновления встроенного ПО*.</span><span class="sxs-lookup"><span data-stu-id="15b51-161">**nx_lwm2m_firmware_state_set**: *Set Firmware Update State*</span></span>

## <a name="nx_lwm2m_client_create"></a><span data-ttu-id="15b51-162">nx_lwm2m_client_create</span><span class="sxs-lookup"><span data-stu-id="15b51-162">nx_lwm2m_client_create</span></span>

<span data-ttu-id="15b51-163">Создание клиента LWM2M</span><span class="sxs-lookup"><span data-stu-id="15b51-163">Create LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-164">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-164">Prototype</span></span>

```c
UINT nx_lwm2m_client_create(NX_LWM2M_CLIENT *client_ptr, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr, UINT local_port, const CHAR *name_ptr,
    const CHAR *msisdn_ptr, UCHAR binding_modes, VOID *stack_ptr, ULONG stack_size);
```

### <a name="description"></a><span data-ttu-id="15b51-165">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-165">Description</span></span>

<span data-ttu-id="15b51-166">Эта служба создает экземпляр клиента LWM2M, который выполняется в контексте собственного потока ThreadX.</span><span class="sxs-lookup"><span data-stu-id="15b51-166">This service creates a LWM2M Client instance, which runs in the context of its own ThreadX thread.</span></span>

<span data-ttu-id="15b51-167">Клиент LWM2M реализует следующие объекты OMA LWM2M: безопасность (0), сервер (1), контроль доступа (2) и устройство (3).</span><span class="sxs-lookup"><span data-stu-id="15b51-167">The LWM2M Client implements the following OMA LWM2M Objects: Security (0), Server (1), Access Control (2) and Device (3).</span></span> <span data-ttu-id="15b51-168">Другие реализации объектов должны быть добавлены посредством приложения.</span><span class="sxs-lookup"><span data-stu-id="15b51-168">The other objects implementations must be added by the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-169">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-169">Parameters</span></span>

- <span data-ttu-id="15b51-170">**client_ptr**: указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-170">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="15b51-171">**ip_ptr**: указатель на созданный ранее экземпляр IP.</span><span class="sxs-lookup"><span data-stu-id="15b51-171">**ip_ptr**: Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="15b51-172">**packet_pool_ptr**: указатель на пул пакетов по умолчанию для данного клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-172">**packet_pool_ptr**: Pointer to the default packet pool for this LWM2M Client.</span></span>
- <span data-ttu-id="15b51-173">**local_port**: локальный UDP-порт, используемый для небезопасного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="15b51-173">**local_port**: The local UDP port used for non-secure communication.</span></span>
- <span data-ttu-id="15b51-174">**name_ptr**: указатель на имя конечной точки клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-174">**name_ptr**: Pointer to LWM2M Client endpoint name.</span></span>
- <span data-ttu-id="15b51-175">**msisdn_ptr**: указатель на номер мобильного абонента сети ISDN (MSISDN), по которому можно связаться с клиентом LWM2M для использования с привязкой SMS. Может иметь значение NULL, если привязка SMS не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="15b51-175">**msisdn_ptr**: Pointer to the MSISDN where the LWM2M Client can be reached for use with the SMS binding, can be NULL if SMS binding is not supported.</span></span>
- <span data-ttu-id="15b51-176">**binding_modes**: привязка и режимы, поддерживаемые клиентом LWM2M, должны являться комбинацией флагов NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S и NX_LWM2M_BINDING_SQ.</span><span class="sxs-lookup"><span data-stu-id="15b51-176">**binding_modes**: The binding and modes supported by the LWM2M Client, must be a combination of NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S and NX_LWM2M_BINDING_SQ flags.</span></span>
- <span data-ttu-id="15b51-177">**stack_ptr**: указатель на область стека потоков клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-177">**stack_ptr**: Pointer to LWM2M Client thread stack area.</span></span>
- <span data-ttu-id="15b51-178">**stack_size**: размер стека потоков клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-178">**stack_size**: The LWM2M Client thread stack size.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-179">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-179">Return Values</span></span>

- <span data-ttu-id="15b51-180">**NX_SUCCESS**: клиент LWM2M успешно создан.</span><span class="sxs-lookup"><span data-stu-id="15b51-180">**NX_SUCCESS**: The LWM2M Client has been successfully created.</span></span>
- <span data-ttu-id="15b51-181">**NX_LWM2M_ERROR**: ошибка создания клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-181">**NX_LWM2M_ERROR**: LWM2M Client create error.</span></span>
- <span data-ttu-id="15b51-182">NX_PTR_ERROR: недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="15b51-182">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_delete"></a><span data-ttu-id="15b51-183">nx_lwm2m_client_delete</span><span class="sxs-lookup"><span data-stu-id="15b51-183">nx_lwm2m_client_delete</span></span>

<span data-ttu-id="15b51-184">Удаление клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-184">Delete LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-185">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-185">Prototype</span></span>

```c
UINT nx_lwm2m_client_delete(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="15b51-186">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-186">Description</span></span>

<span data-ttu-id="15b51-187">Данная служба удаляет созданный ранее экземпляр клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-187">This service deletes a previously created LWM2M Client instance.</span></span>

<span data-ttu-id="15b51-188">Этот вызов также удаляет все сеансы, подключенные в данный момент к этому клиенту.</span><span class="sxs-lookup"><span data-stu-id="15b51-188">All sessions currently attached the client are also deleted by this call.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-189">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-189">Parameters</span></span>

- <span data-ttu-id="15b51-190">**client_ptr**: указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-190">**client_ptr**: Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-191">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-191">Return Values</span></span>

- <span data-ttu-id="15b51-192">**NX_SUCCESS**: клиент LWM2M успешно удален.</span><span class="sxs-lookup"><span data-stu-id="15b51-192">**NX_SUCCESS**: The LWM2M Client has been successfully deleted.</span></span>
- <span data-ttu-id="15b51-193">NX_PTR_ERROR: недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="15b51-193">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_device_callbacks_set"></a><span data-ttu-id="15b51-194">nx_lwm2m_client_device_callbacks_set</span><span class="sxs-lookup"><span data-stu-id="15b51-194">nx_lwm2m_client_device_callbacks_set</span></span>

<span data-ttu-id="15b51-195">Настройка обратных вызовов приложения объекта устройства.</span><span class="sxs-lookup"><span data-stu-id="15b51-195">Set Device Object application callbacks</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-196">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-196">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_callbacks_set(NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_DEVICE_READ_CALLBACK read_callback,
    NX_LWM2M_CLIENT_DEVICE_DISCOVER_CALLBACK discover_callback,
    NX_LWM2M_CLIENT_DEVICE_WRITE_CALLBACK write_callback,
    NX_LWM2M_CLIENT_DEVICE_EXECUTE_CALLBACK execute_callback);
```

### <a name="description"></a><span data-ttu-id="15b51-197">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-197">Description</span></span>

<span data-ttu-id="15b51-198">Данная служба устанавливает обратные вызовы приложения для реализации операций с ресурсами объекта устройства LWM2M, которые не обрабатываются клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-198">This service installs the application callbacks for implementing operations on the LWM2M Device Object resources that are not handled by the LWM2M Client.</span></span>

<span data-ttu-id="15b51-199">Клиент LWM2M реализует следующие ресурсы: код ошибки (11), сброс кода ошибки (12) и поддерживаемые привязки и режимы (16). Операции с другими ресурсами перенаправляются в приложение.</span><span class="sxs-lookup"><span data-stu-id="15b51-199">The LWM2M Client implements the following resources : Error Code (11), Reset Error Code (12) and Supported Binding and Modes (16), operations to the other resources are redirected to the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-200">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-200">Parameters</span></span>

- <span data-ttu-id="15b51-201">**client_ptr**: указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-201">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="15b51-202">**read_callback**: обратный вызов метода Read.</span><span class="sxs-lookup"><span data-stu-id="15b51-202">**read_callback**: The 'Read' method callback.</span></span>
- <span data-ttu-id="15b51-203">**discover_callback**: обратный вызов метода Discover.</span><span class="sxs-lookup"><span data-stu-id="15b51-203">**discover_callback**: The 'Discover' method callback.</span></span>
- <span data-ttu-id="15b51-204">**write_callback**: обратный вызов метода Write.</span><span class="sxs-lookup"><span data-stu-id="15b51-204">**write_callback**: The 'Write' method callback.</span></span>
- <span data-ttu-id="15b51-205">**execute_callback**: обратный вызов метода Execute.</span><span class="sxs-lookup"><span data-stu-id="15b51-205">**execute_callback**: The 'Execute' method callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-206">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-206">Return Values</span></span>

- <span data-ttu-id="15b51-207">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-207">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-208">NX_PTR_ERROR: недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="15b51-208">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_device_error_push"></a><span data-ttu-id="15b51-209">nx_lwm2m_client_device_error_push</span><span class="sxs-lookup"><span data-stu-id="15b51-209">nx_lwm2m_client_device_error_push</span></span>

<span data-ttu-id="15b51-210">Добавление кода ошибки в объект устройства.</span><span class="sxs-lookup"><span data-stu-id="15b51-210">Add error code to Device Object</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-211">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-211">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_error_push(NX_LWM2M_CLIENT *client_ptr, UCHAR code);
```

### <a name="description"></a><span data-ttu-id="15b51-212">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-212">Description</span></span>

<span data-ttu-id="15b51-213">Данная служба добавляет новый экземпляр в ресурс кода ошибки (11) объекта устройства.</span><span class="sxs-lookup"><span data-stu-id="15b51-213">This service adds a new instance to the Error Code (11) resource of the Object Device.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-214">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-214">Parameters</span></span>

- <span data-ttu-id="15b51-215">**client_ptr**: указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-215">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="15b51-216">**code**: новый код ошибки.</span><span class="sxs-lookup"><span data-stu-id="15b51-216">**code**: The new error code.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-217">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-217">Return Values</span></span>

- <span data-ttu-id="15b51-218">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-218">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-219">**NX_LWM2M_BUFFER_TOO_SMALL**: достигнуто максимальное число хранимых кодов ошибок.</span><span class="sxs-lookup"><span data-stu-id="15b51-219">**NX_LWM2M_BUFFER_TOO_SMALL**: The maximum number of stored error codes has been reached.</span></span>
- <span data-ttu-id="15b51-220">NX_PTR_ERROR: недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="15b51-220">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_device_error_reset"></a><span data-ttu-id="15b51-221">nx_lwm2m_client_device_error_reset</span><span class="sxs-lookup"><span data-stu-id="15b51-221">nx_lwm2m_client_device_error_reset</span></span>

<span data-ttu-id="15b51-222">Сброс кодов ошибок объекта устройства.</span><span class="sxs-lookup"><span data-stu-id="15b51-222">Reset error codes of Device Object</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-223">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-223">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_error_reset(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="15b51-224">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-224">Description</span></span>

<span data-ttu-id="15b51-225">Данная служба удаляет все экземпляры ресурса кода ошибки из объекта устройства.</span><span class="sxs-lookup"><span data-stu-id="15b51-225">This service deletes all error code resource instances from the Device Object.</span></span> <span data-ttu-id="15b51-226">Это эквивалентно выполнению кода ошибки сброса ресурса (12).</span><span class="sxs-lookup"><span data-stu-id="15b51-226">This is equivalent to executing the resource Reset Error Code (12).</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-227">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-227">Parameters</span></span>

- <span data-ttu-id="15b51-228">**client_ptr**: указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-228">**client_ptr**: Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-229">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-229">Return Values</span></span>

- <span data-ttu-id="15b51-230">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-230">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-231">NX_PTR_ERROR: недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="15b51-231">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_device_resource_changed"></a><span data-ttu-id="15b51-232">nx_lwm2m_client_device_resource_changed</span><span class="sxs-lookup"><span data-stu-id="15b51-232">nx_lwm2m_client_device_resource_changed</span></span>

<span data-ttu-id="15b51-233">Сигнальное изменение ресурса объекта устройства.</span><span class="sxs-lookup"><span data-stu-id="15b51-233">Signal change of Device Object resource</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-234">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-234">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_resource_changed(NX_LWM2M_CLIENT *client_ptr,
                                    const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a><span data-ttu-id="15b51-235">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-235">Description</span></span>

<span data-ttu-id="15b51-236">Служба используется приложением для сообщения клиенту LWM2M об изменении ресурса объектного устройства.</span><span class="sxs-lookup"><span data-stu-id="15b51-236">The service is used by the application to signal to the LWM2M Client that a resource of the Object Device has changed.</span></span> <span data-ttu-id="15b51-237">Если за ресурсом наблюдает сервер LWM2M, клиент LWM2M отправит соответствующее уведомление.</span><span class="sxs-lookup"><span data-stu-id="15b51-237">The LWM2M Client will send a notification if the resource is observed by a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-238">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-238">Parameters</span></span>

- <span data-ttu-id="15b51-239">**client_ptr**: указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-239">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="15b51-240">**resource**: указатель на структуру, описывающую измененный ресурс.</span><span class="sxs-lookup"><span data-stu-id="15b51-240">**resource**: Pointer to the structure describing the resource that has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-241">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-241">Return Values</span></span>

- <span data-ttu-id="15b51-242">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-242">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-243">NX_PTR_ERROR: недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="15b51-243">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_lock"></a><span data-ttu-id="15b51-244">nx_lwm2m_client_lock</span><span class="sxs-lookup"><span data-stu-id="15b51-244">nx_lwm2m_client_lock</span></span>

<span data-ttu-id="15b51-245">Блокировка клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-245">Lock LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-246">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-246">Prototype</span></span>

```c
UINT nx_lwm2m_client_lock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="15b51-247">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-247">Description</span></span>

<span data-ttu-id="15b51-248">Данная служба блокирует клиент LWM2M, чтобы предотвратить одновременный доступ к объектам LWM2M с серверов или из другого потока приложения.</span><span class="sxs-lookup"><span data-stu-id="15b51-248">This service locks the LWM2M Client to prevent concurent access to the LWM2M objects from the servers or another application thread.</span></span>

<span data-ttu-id="15b51-249">Если клиент LWM2M на данный момент заблокирован другим потоком, функция будет заблокирована до тех пор, пока клиент LWM2M не будет разблокирован.</span><span class="sxs-lookup"><span data-stu-id="15b51-249">If the LWM2M Client is currently locked by another thread, the function will block until the LWM2M Client is unlocked.</span></span>

<span data-ttu-id="15b51-250">Вызовы пар nx_lwm2m_client_lock() и nx_lwm2m_client_unlock() могут быть вложенными.</span><span class="sxs-lookup"><span data-stu-id="15b51-250">Calls to nx_lwm2m_client_lock()/nx_lwm2m_client_unlock() pairs can be nested.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-251">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-251">Parameters</span></span>

- <span data-ttu-id="15b51-252">**client_ptr**: указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-252">**client_ptr**: Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-253">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-253">Return Values</span></span>

- <span data-ttu-id="15b51-254">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-254">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-255">NX_PTR_ERROR: недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="15b51-255">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_add"></a><span data-ttu-id="15b51-256">nx_lwm2m_client_object_add</span><span class="sxs-lookup"><span data-stu-id="15b51-256">nx_lwm2m_client_object_add</span></span>

<span data-ttu-id="15b51-257">Добавление реализации объекта в клиент LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-257">Add Object implementation to the LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-258">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-258">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_add(NX_LWM2M_CLIENT *client_ptr,
                                NX_LWM2M_OBJECT *object_ptr);
```

### <a name="description"></a><span data-ttu-id="15b51-259">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-259">Description</span></span>

<span data-ttu-id="15b51-260">Данная служба добавляет новую реализацию объекта в клиент LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-260">This service adds a new Object implementation to the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-261">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-261">Parameters</span></span>

- <span data-ttu-id="15b51-262">**client_ptr**: указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-262">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="15b51-263">**object_ptr**: указатель на структуру, определяющую реализацию объекта.</span><span class="sxs-lookup"><span data-stu-id="15b51-263">**object_ptr**: Pointer to the structure defining the Object implementation.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-264">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-264">Return Values</span></span>

- <span data-ttu-id="15b51-265">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-265">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-266">**NX_LWM2M_ALREADY_EXIST**: идентификатор объекта уже существует.</span><span class="sxs-lookup"><span data-stu-id="15b51-266">**NX_LWM2M_ALREADY_EXIST**: The Object ID already exists.</span></span>
- <span data-ttu-id="15b51-267">NX_PTR_ERROR: недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="15b51-267">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_create"></a><span data-ttu-id="15b51-268">nx_lwm2m_client_object_create</span><span class="sxs-lookup"><span data-stu-id="15b51-268">nx_lwm2m_client_object_create</span></span>

<span data-ttu-id="15b51-269">Создание нового экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="15b51-269">Create a new Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-270">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-270">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_create(NX_LWM2M_CLIENT *client_ptr,
            NX_LWM2M_ID object_id, NX_LWM2M_ID *instance_id_ptr,
            UINT num_values, const NX_LWM2M_RESOURCE *values_ptr);
```

### <a name="description"></a><span data-ttu-id="15b51-271">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-271">Description</span></span>

<span data-ttu-id="15b51-272">Данная служба выполняет операцию Create с объектом клиента LWM2M для создания нового экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="15b51-272">This service performs a 'Create' operation on an Object of the LWM2M Client to create a new Object Instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-273">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-273">Parameters</span></span>

- <span data-ttu-id="15b51-274">**client_ptr**: указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-274">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="15b51-275">**object_id**: идентификатор объекта.</span><span class="sxs-lookup"><span data-stu-id="15b51-275">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="15b51-276">**instance_id_ptr**: указатель на идентификатор нового экземпляра. Если клиент LWM2M должен назначить идентификатор экземпляра, то этот параметр может иметь значение NULL.</span><span class="sxs-lookup"><span data-stu-id="15b51-276">**instance_id_ptr**: Pointer to the ID of the new instance, can be NULL if the LWM2M Client must assign an Instance ID.</span></span> <span data-ttu-id="15b51-277">Если идентификатор представляет собой зарезервированное значение 65535, то клиент LWM2M назначит идентификатор экземпляра.</span><span class="sxs-lookup"><span data-stu-id="15b51-277">If the ID is the reserved value 65535 the LWM2M Client will assign an Instance ID.</span></span> <span data-ttu-id="15b51-278">Если значение не равно NULL, то после вызова возвращается назначенный идентификатор.</span><span class="sxs-lookup"><span data-stu-id="15b51-278">If not NULL the assigned ID is returned after the call.</span></span>
- <span data-ttu-id="15b51-279">**num_values**: количество задаваемых значений.</span><span class="sxs-lookup"><span data-stu-id="15b51-279">**num_values**: The number of values to set.</span></span>
- <span data-ttu-id="15b51-280">**values_ptr**: указатель на массив значений ресурсов для инициализации нового экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="15b51-280">**values_ptr**: Pointer to an array of resource values to initialize the new Object Instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-281">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-281">Return Values</span></span>

- <span data-ttu-id="15b51-282">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-282">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-283">**NX_LWM2M_ALREADY_EXIST**: идентификатор экземпляра объекта уже существует.</span><span class="sxs-lookup"><span data-stu-id="15b51-283">**NX_LWM2M_ALREADY_EXIST**: The Object Instance ID already exists.</span></span>
- <span data-ttu-id="15b51-284">**NX_LWM2M_METHOD_NOT_ALLOWED**: объект не поддерживает создание экземпляров.</span><span class="sxs-lookup"><span data-stu-id="15b51-284">**NX_LWM2M_METHOD_NOT_ALLOWED**: The Object doesn't support instance creation.</span></span>
- <span data-ttu-id="15b51-285">**NX_LWM2M_NO_MEMORY**: невозможно выделить память для хранения нового экземпляра.</span><span class="sxs-lookup"><span data-stu-id="15b51-285">**NX_LWM2M_NO_MEMORY**: Cannot allocate memory to store the new instance.</span></span>
- <span data-ttu-id="15b51-286">**NX_LWM2M_NOT_FOUND**: идентификатор объекта не существует.</span><span class="sxs-lookup"><span data-stu-id="15b51-286">**NX_LWM2M_NOT_FOUND**: The Object ID doesn't exist.</span></span>
- <span data-ttu-id="15b51-287">NX_PTR_ERROR: недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="15b51-287">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_delete"></a><span data-ttu-id="15b51-288">nx_lwm2m_client_object_delete</span><span class="sxs-lookup"><span data-stu-id="15b51-288">nx_lwm2m_client_object_delete</span></span>

<span data-ttu-id="15b51-289">Удаление экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="15b51-289">Delete an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-290">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-290">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_delete(NX_LWM2M_CLIENT *client_ptr,
                NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id);
```

### <a name="description"></a><span data-ttu-id="15b51-291">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-291">Description</span></span>

<span data-ttu-id="15b51-292">Данная служба выполняет операцию Delete с экземпляром объекта клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-292">This service performs a 'Delete' operation on an Object Instance of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-293">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-293">Parameters</span></span>

- <span data-ttu-id="15b51-294">**client_ptr**: указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-294">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="15b51-295">**object_id**: идентификатор объекта.</span><span class="sxs-lookup"><span data-stu-id="15b51-295">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="15b51-296">**instance_id**: идентификатор экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="15b51-296">**instance_id**: The Object Instance ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-297">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-297">Return Values</span></span>

- <span data-ttu-id="15b51-298">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-298">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-299">**NX_LWM2M_METHOD_NOT_ALLOWED**: объект не поддерживает удаления экземпляров.</span><span class="sxs-lookup"><span data-stu-id="15b51-299">**NX_LWM2M_METHOD_NOT_ALLOWED**: The Object doesn't support instance deletion.</span></span>
- <span data-ttu-id="15b51-300">**NX_LWM2M_NOT_FOUND**: идентификатор объекта или идентификатор экземпляра объекта не существует.</span><span class="sxs-lookup"><span data-stu-id="15b51-300">**NX_LWM2M_NOT_FOUND**: The Object ID or Object Instance ID doesn't exist.</span></span>
- <span data-ttu-id="15b51-301">NX_PTR_ERROR: недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="15b51-301">NX_PTR_ERROR Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_discover"></a><span data-ttu-id="15b51-302">nx_lwm2m_client_object_discover</span><span class="sxs-lookup"><span data-stu-id="15b51-302">nx_lwm2m_client_object_discover</span></span>

<span data-ttu-id="15b51-303">Обнаружение ресурсов экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="15b51-303">Discover resources of an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-304">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-304">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_discover(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id,
        UINT *num_resources_ptr, NX_LWM2M_RESOURCE_INFO *resources_ptr);
```

### <a name="description"></a><span data-ttu-id="15b51-305">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-305">Description</span></span>

<span data-ttu-id="15b51-306">Данная служба выполняет операцию Discover для экземпляра объекта клиента LWM2M, в результате чего возвращается список ресурсов, реализованных объектом.</span><span class="sxs-lookup"><span data-stu-id="15b51-306">This service performs a 'Discover' operation on an Object Instance of the LWM2M Client, this returns the list of resources implemented by the Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-307">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-307">Parameters</span></span>

- <span data-ttu-id="15b51-308">**client_ptr**: указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-308">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="15b51-309">**object_id**: идентификатор объекта.</span><span class="sxs-lookup"><span data-stu-id="15b51-309">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="15b51-310">**instance_id**: идентификатор экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="15b51-310">**instance_id**: The Object Instance ID.</span></span>
- <span data-ttu-id="15b51-311">**num_resources_ptr**: для ввода содержит размер целевого буфера, а для вывода — количество записанных в этот буфер элементов.</span><span class="sxs-lookup"><span data-stu-id="15b51-311">**num_resources_ptr**: On input the size of the destination buffer, on output the number of elements writen to the buffer.</span></span>
- <span data-ttu-id="15b51-312">**resources_ptr**: указатель на целевой буфер.</span><span class="sxs-lookup"><span data-stu-id="15b51-312">**resources_ptr**: Pointer to the destination buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-313">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-313">Return Values</span></span>

- <span data-ttu-id="15b51-314">**NX_SUCCESS**: операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="15b51-314">**NX_SUCCESS**: Successful operation..</span></span>
- <span data-ttu-id="15b51-315">**NX_LWM2M_BUFFER_TOO_SMALL**: недостаточный размер буфера ресурсов для хранения списка ресурсов.</span><span class="sxs-lookup"><span data-stu-id="15b51-315">**NX_LWM2M_BUFFER_TOO_SMALL**: The resources buffer is too small to store the list of resources.</span></span>
- <span data-ttu-id="15b51-316">**NX_LWM2M_NOT_FOUND**: идентификатор объекта или идентификатор экземпляра объекта не существует.</span><span class="sxs-lookup"><span data-stu-id="15b51-316">**NX_LWM2M_NOT_FOUND**: The Object ID or Object Instance ID doesn't exist.</span></span>
- <span data-ttu-id="15b51-317">NX_PTR_ERROR: недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="15b51-317">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_execute"></a><span data-ttu-id="15b51-318">nx_lwm2m_client_object_execute</span><span class="sxs-lookup"><span data-stu-id="15b51-318">nx_lwm2m_client_object_execute</span></span>

<span data-ttu-id="15b51-319">Выполнение ресурса экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="15b51-319">Execute resource of an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-320">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-320">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_execute(NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id, NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr, UINT arguments_length);
```

### <a name="description"></a><span data-ttu-id="15b51-321">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-321">Description</span></span>

<span data-ttu-id="15b51-322">Данная служба выполняет операцию Execute с ресурсом экземпляра объекта клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-322">This service performs the 'Execute' operation on an Object Instance Resource of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-323">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-323">Parameters</span></span>

- <span data-ttu-id="15b51-324">**client_ptr**: указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-324">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="15b51-325">**object_id**: идентификатор объекта.</span><span class="sxs-lookup"><span data-stu-id="15b51-325">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="15b51-326">**instance_id**: идентификатор экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="15b51-326">**instance_id**: The Object Instance ID.</span></span>
- <span data-ttu-id="15b51-327">**resource_id**: идентификатор ресурса.</span><span class="sxs-lookup"><span data-stu-id="15b51-327">**resource_id**: The Resource ID.</span></span>
- <span data-ttu-id="15b51-328">**arguments_ptr**: указатель на аргументы операции выполнения.</span><span class="sxs-lookup"><span data-stu-id="15b51-328">**arguments_ptr**: Pointer to the arguments of the execute operation.</span></span> <span data-ttu-id="15b51-329">Может иметь значение NULL, если значение arguments_length равно нулю.</span><span class="sxs-lookup"><span data-stu-id="15b51-329">Can be NULL if arguments_length is zero.</span></span>
- <span data-ttu-id="15b51-330">**arguments_length**: длина аргументов.</span><span class="sxs-lookup"><span data-stu-id="15b51-330">**arguments_length**: The length of the arguments.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-331">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-331">Return Values</span></span>

- <span data-ttu-id="15b51-332">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-332">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-333">**NX_LWM2M_METHOD_NOT_ALLOWED**: ресурс не поддерживает операцию выполнения.</span><span class="sxs-lookup"><span data-stu-id="15b51-333">**NX_LWM2M_METHOD_NOT_ALLOWED**: The resource doesn't support the execute operation.</span></span>
- <span data-ttu-id="15b51-334">**NX_LWM2M_NOT_FOUND**: идентификатор объекта, идентификатор экземпляра объекта или идентификатор ресурса не существует.</span><span class="sxs-lookup"><span data-stu-id="15b51-334">**NX_LWM2M_NOT_FOUND**: The Object ID, Object Instance ID or the resource ID doesn't exist.</span></span>
- <span data-ttu-id="15b51-335">NX_PTR_ERROR: недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="15b51-335">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_get_next"></a><span data-ttu-id="15b51-336">nx_lwm2m_client_object_get_next</span><span class="sxs-lookup"><span data-stu-id="15b51-336">nx_lwm2m_client_object_get_next</span></span>

<span data-ttu-id="15b51-337">Получение списка объектов, реализованных клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-337">Get the list of Objects implemented by the LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-338">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-338">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_get_next(NX_LWM2M_CLIENT *client_ptr,
                                    NX_LWM2M_ID *object_id_ptr);
```

### <a name="description"></a><span data-ttu-id="15b51-339">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-339">Description</span></span>

<span data-ttu-id="15b51-340">Данная служба возвращает идентификатор следующего объекта, реализованного клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-340">This service returns the ID of the next Object implemented by the LWM2M Client.</span></span> <span data-ttu-id="15b51-341">Если для текущего идентификатора объекта установлено значение NX_LWM2M_RESERVED_ID (65535), возвращается первый идентификатор объекта.</span><span class="sxs-lookup"><span data-stu-id="15b51-341">If the current Object ID is set to NX_LWM2M_RESERVED_ID (65535) the first Object ID is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-342">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-342">Parameters</span></span>

- <span data-ttu-id="15b51-343">**client_ptr**: указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-343">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="15b51-344">**object_id_ptr**: указатель на текущий идентификатор объекта.</span><span class="sxs-lookup"><span data-stu-id="15b51-344">**object_id_ptr**: Pointer to the current Object ID.</span></span> <span data-ttu-id="15b51-345">При возврате содержит следующий идентификатор объекта, реализованный клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-345">On return contains the next Object ID implemented by the LWM2M Client.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-346">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-346">Return Values</span></span>

- <span data-ttu-id="15b51-347">**NX_SUCCESS**: операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="15b51-347">**NX_SUCCESS**: Successful operation..</span></span>
- <span data-ttu-id="15b51-348">**NX_LWM2M_NOT_FOUND**: данный идентификатор объекта является последним в базе данных.</span><span class="sxs-lookup"><span data-stu-id="15b51-348">**NX_LWM2M_NOT_FOUND**: The given Object ID is the last of the database.</span></span>
- <span data-ttu-id="15b51-349">NX_PTR_ERROR: недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="15b51-349">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_instance_get_next"></a><span data-ttu-id="15b51-350">nx_lwm2m_client_object_instance_get_next</span><span class="sxs-lookup"><span data-stu-id="15b51-350">nx_lwm2m_client_object_instance_get_next</span></span>

<span data-ttu-id="15b51-351">Получение списка экземпляров объекта.</span><span class="sxs-lookup"><span data-stu-id="15b51-351">Get the list of Instances of an Object</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-352">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-352">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_instance_get_next(NX_LWM2M_CLIENT *client_ptr,
                    NX_LWM2M_ID object_id, NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a><span data-ttu-id="15b51-353">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-353">Description</span></span>

<span data-ttu-id="15b51-354">Данная служба возвращает идентификатор следующего экземпляра данного объекта.</span><span class="sxs-lookup"><span data-stu-id="15b51-354">This service returns the ID of the next Object Instance of the given Object.</span></span> <span data-ttu-id="15b51-355">Если для текущего идентификатора экземпляра установлено NX_LWM2M_RESERVED_ID (65535), возвращается идентификатор первого экземпляра.</span><span class="sxs-lookup"><span data-stu-id="15b51-355">If the current Instance ID is set to NX_LWM2M_RESERVED_ID (65535) the ID of the first instance is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-356">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-356">Parameters</span></span>

- <span data-ttu-id="15b51-357">**client_ptr**: указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-357">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="15b51-358">**object_id**: идентификатор объекта.</span><span class="sxs-lookup"><span data-stu-id="15b51-358">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="15b51-359">**instance_id_ptr**: указатель на текущий идентификатор экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="15b51-359">**instance_id_ptr**: Pointer to the current Object Instance ID.</span></span> <span data-ttu-id="15b51-360">При возврате содержит идентификатор следующего экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="15b51-360">On return contains the next Instance ID of the Object.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-361">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-361">Return Values</span></span>

- <span data-ttu-id="15b51-362">**NX_SUCCESS**: операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="15b51-362">**NX_SUCCESS**: Successful operation..</span></span>
- <span data-ttu-id="15b51-363">**NX_LWM2M_NOT_FOUND**: заданный идентификатор экземпляра является последним для объекта, или идентификатор объекта не реализован.</span><span class="sxs-lookup"><span data-stu-id="15b51-363">**NX_LWM2M_NOT_FOUND**: The given Instance ID is the last of the object, or the Object ID is not implemented.</span></span>
- <span data-ttu-id="15b51-364">NX_PTR_ERROR: недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="15b51-364">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_read"></a><span data-ttu-id="15b51-365">nx_lwm2m_client_object_read</span><span class="sxs-lookup"><span data-stu-id="15b51-365">nx_lwm2m_client_object_read</span></span>

<span data-ttu-id="15b51-366">Чтение значений ресурсов экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="15b51-366">Read resources values of an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-367">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-367">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_read(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id,
        UINT num_values, NX_LWM2M_RESOURCE *values);
```

### <a name="description"></a><span data-ttu-id="15b51-368">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-368">Description</span></span>

<span data-ttu-id="15b51-369">Эта служба выполняет операцию Read с экземпляром объекта клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-369">This service performs a 'Read' operation on an Object Instance of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-370">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-370">Parameters</span></span>

- <span data-ttu-id="15b51-371">**client_ptr**: указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-371">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="15b51-372">**object_id**: идентификатор объекта.</span><span class="sxs-lookup"><span data-stu-id="15b51-372">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="15b51-373">**instance_id**: идентификатор экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="15b51-373">**instance_id**: The Object Instance ID.</span></span>
- <span data-ttu-id="15b51-374">**num_values**: количество считываемых ресурсов.</span><span class="sxs-lookup"><span data-stu-id="15b51-374">**num_values**: The number of resources to read.</span></span>
- <span data-ttu-id="15b51-375">**values_ptr**: указатель на массив NX_LWM2M_RESOURCE, который содержит список считываемых идентификаторов.</span><span class="sxs-lookup"><span data-stu-id="15b51-375">**values_ptr**: Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources to read.</span></span> <span data-ttu-id="15b51-376">По возвращении массив заполняется соответствующими типами и значениями.</span><span class="sxs-lookup"><span data-stu-id="15b51-376">On return the array is filled with the corresponding types and values.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-377">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-377">Return Values</span></span>

- <span data-ttu-id="15b51-378">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-378">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-379">**NX_LWM2M_METHOD_NOT_ALLOWED**: ресурс не поддерживает операцию считывания.</span><span class="sxs-lookup"><span data-stu-id="15b51-379">**NX_LWM2M_METHOD_NOT_ALLOWED**: A resource doesn't support the read operation.</span></span>
- <span data-ttu-id="15b51-380">**NX_LWM2M_NOT_FOUND**: идентификатор объекта, идентификатор экземпляра объекта или идентификатор ресурса не существует.</span><span class="sxs-lookup"><span data-stu-id="15b51-380">**NX_LWM2M_NOT_FOUND**: The Object ID, Object Instance ID or a resource ID doesn't exist.</span></span>
- <span data-ttu-id="15b51-381">NX_PTR_ERROR: недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="15b51-381">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_write"></a><span data-ttu-id="15b51-382">nx_lwm2m_client_object_write</span><span class="sxs-lookup"><span data-stu-id="15b51-382">nx_lwm2m_client_object_write</span></span>

<span data-ttu-id="15b51-383">Изменение значений ресурсов экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="15b51-383">Change resources values of an Object instance</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-384">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-384">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_write(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id, UINT num_values,
        const NX_LWM2M_RESOURCE *values_ptr, UINT write_op);
```

### <a name="description"></a><span data-ttu-id="15b51-385">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-385">Description</span></span>

<span data-ttu-id="15b51-386">Данная служба выполняет операцию Write с экземпляром объекта клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-386">This service performs a 'Write' operation on an Object Instance of the LWM2M Client.</span></span>

<span data-ttu-id="15b51-387">Для параметра *write_op* можно указать следующие операции записи.</span><span class="sxs-lookup"><span data-stu-id="15b51-387">The following write operations can be specified to the *write_op* parameter:</span></span>

- <span data-ttu-id="15b51-388">**0**: частичное обновление. Добавляет или обновляет ресурсы, указанные в новом значении, и сохраняет остальные существующие ресурсы без изменений.</span><span class="sxs-lookup"><span data-stu-id="15b51-388">**0** &mdash; Partial Update: adds or updates Resources provided in the new value and leaves other existing Resources unchanged,</span></span>

- <span data-ttu-id="15b51-389">**NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE**: замена экземпляра. Заменяет существующий экземпляр объекта новым экземпляром с указанными значениями ресурса.</span><span class="sxs-lookup"><span data-stu-id="15b51-389">**NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; Replace Instance: replaces the Object Instance with the new provided resource values.</span></span>

- <span data-ttu-id="15b51-390">**NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE**: замена ресурса. Заменяет ресурсы новыми ресурсами с указанными значениями ресурса (используется для замены ресурсов с несколькими типами).</span><span class="sxs-lookup"><span data-stu-id="15b51-390">**NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; Replace Resource: replaces the Resources with the new provided resource values (used to replace Multiple Resources).</span></span>

- <span data-ttu-id="15b51-391">**NX_LWM2M_OBJECT_WRITE_BOOTSTRAP**: запись начальной загрузки. Указывает вызов из последовательности начальной загрузки.</span><span class="sxs-lookup"><span data-stu-id="15b51-391">**NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; Bootstrap Write: indicates a call from a Bootstrap sequence.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-392">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-392">Parameters</span></span>

- <span data-ttu-id="15b51-393">**client_ptr**: указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-393">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="15b51-394">**object_id**: идентификатор объекта.</span><span class="sxs-lookup"><span data-stu-id="15b51-394">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="15b51-395">**instance_id**: идентификатор экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="15b51-395">**instance_id**: The Object Instance ID.</span></span>
- <span data-ttu-id="15b51-396">**num_values**: количество записываемых ресурсов.</span><span class="sxs-lookup"><span data-stu-id="15b51-396">**num_values**: The number of resources to write.</span></span>
- <span data-ttu-id="15b51-397">**values_ptr**: указатель на массив NX_LWM2M_RESOURCE, содержащий идентификаторы ресурсов, типы и значения для записи.</span><span class="sxs-lookup"><span data-stu-id="15b51-397">**values_ptr**: Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources, the types and the values to write.</span></span>
- <span data-ttu-id="15b51-398">**write_op**: тип операции записи.</span><span class="sxs-lookup"><span data-stu-id="15b51-398">**write_op**: The type of write operation.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-399">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-399">Return Values</span></span>

- <span data-ttu-id="15b51-400">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-400">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-401">**NX_LWM2M_BAD_ENCODING**: недопустимый тип ресурса.</span><span class="sxs-lookup"><span data-stu-id="15b51-401">**NX_LWM2M_BAD_ENCODING**: The type of a resource is not valid.</span></span>
- <span data-ttu-id="15b51-402">**NX_LWM2M_BUFFER_TOO_SMALL**: длина значения слишком велика для сохранения в экземпляре.</span><span class="sxs-lookup"><span data-stu-id="15b51-402">**NX_LWM2M_BUFFER_TOO_SMALL**: The length of a value is too big to be stored in the instance.</span></span>
- <span data-ttu-id="15b51-403">**NX_LWM2M_METHOD_NOT_ALLOWED**: ресурс не поддерживает операции записи.</span><span class="sxs-lookup"><span data-stu-id="15b51-403">**NX_LWM2M_METHOD_NOT_ALLOWED**: A resource doesn't support the write operation.</span></span>
- <span data-ttu-id="15b51-404">**NX_LWM2M_NO_MEMORY**: невозможно выделить память для хранения значения ресурса.</span><span class="sxs-lookup"><span data-stu-id="15b51-404">**NX_LWM2M_NO_MEMORY**: Cannot allocate memory to store a resource value.</span></span>
- <span data-ttu-id="15b51-405">**NX_LWM2M_NOT_ACCEPTABLE**: недопустимое значение ресурса.</span><span class="sxs-lookup"><span data-stu-id="15b51-405">**NX_LWM2M_NOT_ACCEPTABLE**: The value of a resource is not valid.</span></span>
- <span data-ttu-id="15b51-406">**NX_LWM2M_NOT_FOUND**: идентификатор объекта, идентификатор экземпляра объекта или идентификатор ресурса не существует.</span><span class="sxs-lookup"><span data-stu-id="15b51-406">**NX_LWM2M_NOT_FOUND**: The Object ID, Object Instance ID or a resource ID doesn't exist.</span></span>
- <span data-ttu-id="15b51-407">NX_OPTION_ERROR: недопустимый тип операции записи.</span><span class="sxs-lookup"><span data-stu-id="15b51-407">NX_OPTION_ERROR: Invalid type of write operation.</span></span>
- <span data-ttu-id="15b51-408">NX_PTR_ERROR: недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="15b51-408">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_security_key_callbacks_set"></a><span data-ttu-id="15b51-409">nx_lwm2m_client_security_key_callbacks_set</span><span class="sxs-lookup"><span data-stu-id="15b51-409">nx_lwm2m_client_security_key_callbacks_set</span></span>

<span data-ttu-id="15b51-410">Настройка обратных вызовов управления ключами объекта безопасности.</span><span class="sxs-lookup"><span data-stu-id="15b51-410">Set Security Object key management callbacks</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-411">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-411">Prototype</span></span>

```c
UINT nx_lwm2m_client_security_key_callbacks_set(NX_LWM2M_CLIENT *client_ptr,
                NX_LWM2M_CLIENT_SECURITY_KEY_WRITE_CALLBACK write_callback,
                NX_LWM2M_CLIENT_SECURITY_KEY_DELETE_CALLBACK delete_callback);
```

### <a name="description"></a><span data-ttu-id="15b51-412">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-412">Description</span></span>

<span data-ttu-id="15b51-413">Эта служба устанавливает обратные вызовы приложения для реализации операций с ресурсами объекта безопасности LWM2M, связанными с ключами безопасности.</span><span class="sxs-lookup"><span data-stu-id="15b51-413">This service installs the application callbacks for implementing operations on the LWM2M Security Object resources related to the security keys.</span></span>

<span data-ttu-id="15b51-414">Клиент LWM2M делегирует управление ключами безопасности приложению во время сеансов начальной загрузки. Обратные вызовы вызываются, когда сервер начальной загрузки записывает или удаляет следующие ресурсы в экземпляре объекта безопасности: открытый ключ или удостоверение (3), открытый ключ сервера (4), секретный ключ (5).</span><span class="sxs-lookup"><span data-stu-id="15b51-414">The LWM2M Client delegates the security key management to the application during the Bootstrap sessions, the callbacks will be called when the Bootstrap Server writes or deletes the following resources on a Security Object Instance: Public Key or Identity (3), Server Public Key (4), Secret Key (5).</span></span>

<span data-ttu-id="15b51-415">Приложение отвечает за хранение данных ключей и настройку сеансов DTLS, используемых клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-415">The application is responsible for storing the keys data and for configuring the DTLS sessions used by the LWM2M client.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-416">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-416">Parameters</span></span>

- <span data-ttu-id="15b51-417">**client_ptr**: указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-417">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="15b51-418">**write_callback**: обратный вызов метода Write для ключа.</span><span class="sxs-lookup"><span data-stu-id="15b51-418">**write_callback**: The 'Write' key method callback.</span></span>
- <span data-ttu-id="15b51-419">**delete_callback**: обратный вызов метода Delete для ключа.</span><span class="sxs-lookup"><span data-stu-id="15b51-419">**delete_callback**: The 'Delete' key method callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-420">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-420">Return Values</span></span>

- <span data-ttu-id="15b51-421">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-421">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-422">NX_PTR_ERROR: недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="15b51-422">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_bootstrap"></a><span data-ttu-id="15b51-423">nx_lwm2m_client_session_bootstrap</span><span class="sxs-lookup"><span data-stu-id="15b51-423">nx_lwm2m_client_session_bootstrap</span></span>

<span data-ttu-id="15b51-424">Запуск сеанса взаимодействия с сервером начальной загрузки.</span><span class="sxs-lookup"><span data-stu-id="15b51-424">Start a session with a Bootstrap Server</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-425">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-425">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_bootstrap(NX_LWM2M_CLIENT_SESSION
    *session_ptr, NX_LWM2M_ID security_id, ULONG ip_address, UINT port);
```

### <a name="description"></a><span data-ttu-id="15b51-426">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-426">Description</span></span>

<span data-ttu-id="15b51-427">Данная служба запускает сеанс взаимодействия с сервером начальной загрузки.</span><span class="sxs-lookup"><span data-stu-id="15b51-427">This service start a session with a Bootstrap Server.</span></span> <span data-ttu-id="15b51-428">Сервер должен иметь соответствующий экземпляр безопасности в объекте безопасности.</span><span class="sxs-lookup"><span data-stu-id="15b51-428">The server should have a corresponding security instance in the Security Object.</span></span>

<span data-ttu-id="15b51-429">Если ожидающий ресурс отличен от нуля в экземпляре безопасности, связанном с данным сервером, сеанс будет ожидать инициируемой сервером начальной загрузки. Если сервер не инициирует загрузку по истечении этого периода времени, будет выполнена инициированная клиентом начальная загрузка.</span><span class="sxs-lookup"><span data-stu-id="15b51-429">If the 'Hold Off' resource is different than zero in the Security Instance associated with this server the session will wait for a Server Initiated Bootstrap, if no bootstrap is initiated by the server after this period of time a Client Initiated Boostrap will be performed.</span></span>

<span data-ttu-id="15b51-430">Любой текущий активный сеанс прерывается этим вызовом и заменяется новым сеансом сервера начальной загрузки.</span><span class="sxs-lookup"><span data-stu-id="15b51-430">Any current active session is aborted by this call and replaced by the new Bootstrap Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-431">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-431">Parameters</span></span>

- <span data-ttu-id="15b51-432">**session_ptr**: указатель на блок управления сеансом клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-432">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="15b51-433">**security_id**: если на сервере начальной загрузки не определен экземпляр безопасности, то идентификатор экземпляра безопасности сервера начальной загрузки должен иметь значение NX_LWM2M_RESERVED_ID (65535).</span><span class="sxs-lookup"><span data-stu-id="15b51-433">**security_id**: The Security Instance ID of the Bootstrap Server, must be set to NX_LWM2M_RESERVED_ID (65535) if the Bootstrap Server has no Security Instance defined.</span></span>
- <span data-ttu-id="15b51-434">**ip_address**: IP-адрес сервера.</span><span class="sxs-lookup"><span data-stu-id="15b51-434">**ip_address**: The IP address of the server.</span></span>
- <span data-ttu-id="15b51-435">**port**: UDP-порт сервера.</span><span class="sxs-lookup"><span data-stu-id="15b51-435">**port**: The UDP port of the server.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-436">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-436">Return Values</span></span>

- <span data-ttu-id="15b51-437">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-437">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-438">**NX_LWM2M_NOT_FOUND**: отсутствует экземпляр объекта безопасности, соответствующий идентификатору экземпляра безопасности.</span><span class="sxs-lookup"><span data-stu-id="15b51-438">**NX_LWM2M_NOT_FOUND**: There is No Security Object instance corresponding to the Security Instance ID.</span></span>
- <span data-ttu-id="15b51-439">NX_PTR_ERROR: недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="15b51-439">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_bootstrap_dtls"></a><span data-ttu-id="15b51-440">nx_lwm2m_client_session_bootstrap_dtls</span><span class="sxs-lookup"><span data-stu-id="15b51-440">nx_lwm2m_client_session_bootstrap_dtls</span></span>

<span data-ttu-id="15b51-441">Запуск безопасного сеанса взаимодействия с сервером начальной загрузки.</span><span class="sxs-lookup"><span data-stu-id="15b51-441">Start a secure session with a Bootstrap Server</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-442">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-442">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_bootstrap_dtls(NX_LWM2M_CLIENT_SESSION *session_ptr,
    NX_LWM2M_ID security_id, ULONG ip_address, UINT port, NX_SECURE_DTLS_SESSION
    *dtls_session_ptr, UINT dtls_local_port);
```

### <a name="description"></a><span data-ttu-id="15b51-443">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-443">Description</span></span>

<span data-ttu-id="15b51-444">Данная служба запускает сеанс с сервером начальной загрузки, используя безопасное подключение DTLS.</span><span class="sxs-lookup"><span data-stu-id="15b51-444">This service start a session with a Bootstrap Server using a secure DTLS connection.</span></span> <span data-ttu-id="15b51-445">Сервер должен иметь соответствующий экземпляр безопасности в объекте безопасности.</span><span class="sxs-lookup"><span data-stu-id="15b51-445">The server should have a corresponding security instance in the Security Object.</span></span>

<span data-ttu-id="15b51-446">Перед вызовом данной функции необходимо настроить сеанс DTLS с использованием соответствующих комплектов шифров и материала ключа.</span><span class="sxs-lookup"><span data-stu-id="15b51-446">The DTLS session must have been configured with the proper cipher suites and key material before calling this function.</span></span> <span data-ttu-id="15b51-447">Необходимо определить NX_SECURE_ENABLE_DTLS.</span><span class="sxs-lookup"><span data-stu-id="15b51-447">NX_SECURE_ENABLE_DTLS must be defined.</span></span>

<span data-ttu-id="15b51-448">Если ожидающий ресурс отличен от нуля в экземпляре безопасности, связанном с данным сервером, сеанс будет ожидать инициируемой сервером начальной загрузки. Если сервер не инициирует загрузку по истечении этого периода времени, будет выполнена инициированная клиентом начальная загрузка.</span><span class="sxs-lookup"><span data-stu-id="15b51-448">If the 'Hold Off' resource is different than zero in the Security Instance associated with this server the session will wait for a Server Initiated Bootstrap, if no bootstrap is initiated by the server after this period of time a Client Initiated Boostrap will be performed.</span></span>

<span data-ttu-id="15b51-449">Любой текущий активный сеанс прерывается этим вызовом и заменяется новым сеансом сервера начальной загрузки.</span><span class="sxs-lookup"><span data-stu-id="15b51-449">Any current active session is aborted by this call and replaced by the new Bootstrap Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-450">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-450">Parameters</span></span>

- <span data-ttu-id="15b51-451">**session_ptr**: указатель на блок управления сеансом клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-451">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="15b51-452">**security_id**: если на сервере начальной загрузки не определен экземпляр безопасности, то идентификатор экземпляра безопасности сервера начальной загрузки должен иметь значение NX_LWM2M_RESERVED_ID (65535).</span><span class="sxs-lookup"><span data-stu-id="15b51-452">**security_id**: The Security Instance ID of the Bootstrap Server, must be set to NX_LWM2M_RESERVED_ID (65535) if the Bootstrap Server has no Security Instance defined.</span></span>
- <span data-ttu-id="15b51-453">**ip_address**: IP-адрес сервера.</span><span class="sxs-lookup"><span data-stu-id="15b51-453">**ip_address**: The IP address of the server.</span></span>
- <span data-ttu-id="15b51-454">**port**: UDP-порт сервера.</span><span class="sxs-lookup"><span data-stu-id="15b51-454">**port**: The UDP port of the server.</span></span>
- <span data-ttu-id="15b51-455">**dtls_session_ptr**: сеанс DTLS, используемый для сеанса начальной загрузки.</span><span class="sxs-lookup"><span data-stu-id="15b51-455">**dtls_session_ptr**: The DTLS session to use for the Bootstrap session.</span></span>
- <span data-ttu-id="15b51-456">**dtls_local_port**: локальный UDP-порт, используемый для сеанса DTLS.</span><span class="sxs-lookup"><span data-stu-id="15b51-456">**dtls_local_port**: The local UDP port used for the DTLS session.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-457">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-457">Return Values</span></span>

- <span data-ttu-id="15b51-458">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-458">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-459">**NX_LWM2M_NOT_FOUND**: отсутствует экземпляр объекта безопасности, соответствующий идентификатору экземпляра безопасности.</span><span class="sxs-lookup"><span data-stu-id="15b51-459">**NX_LWM2M_NOT_FOUND**: There is No Security Object instance corresponding to the Security Instance ID.</span></span>
- <span data-ttu-id="15b51-460">NX_PTR_ERROR: недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="15b51-460">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_create"></a><span data-ttu-id="15b51-461">nx_lwm2m_client_session_create</span><span class="sxs-lookup"><span data-stu-id="15b51-461">nx_lwm2m_client_session_create</span></span>

<span data-ttu-id="15b51-462">Создание сеанса клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-462">Create LWM2M Client Session</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-463">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-463">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_create(NX_LWM2M_CLIENT_SESSION *session_ptr,
         NX_LWM2M_CLIENT *client_ptr,
         NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK state_callback);
```

### <a name="description"></a><span data-ttu-id="15b51-464">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-464">Description</span></span>

<span data-ttu-id="15b51-465">Данная служба создает новый сеанс клиента LWM2M, подключенный к существующему клиенту LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-465">This service creates a new LWM2M Client Session attached to an existing LWM2M Client.</span></span> <span data-ttu-id="15b51-466">Этот сеанс используется клиентом LWM2M для взаимодействия с сервером начальной загрузки или сервером LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-466">The session is used by the LWM2M Client to communicate with a Bootstrap Server or a LWM2M Server.</span></span>

<span data-ttu-id="15b51-467">Приложение должно предоставить функцию обратного вызова, которая будет вызываться при обновлении состояния сеанса.</span><span class="sxs-lookup"><span data-stu-id="15b51-467">The application must provide a callback function that will be called when the state of the session is updated.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-468">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-468">Parameters</span></span>

- <span data-ttu-id="15b51-469">**session_ptr**: указатель на блок управления сеансом клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-469">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="15b51-470">**client_ptr**: указатель на созданный ранее клиент LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-470">**client_ptr**: Pointer to the previously created LWM2M Client.</span></span>
- <span data-ttu-id="15b51-471">**state_callback**: обратный вызов приложения, который выполняется при изменении состояния сеанса.</span><span class="sxs-lookup"><span data-stu-id="15b51-471">**state_callback**: Application callback that is called when the state of the session has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-472">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-472">Return Values</span></span>

- <span data-ttu-id="15b51-473">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-473">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-474">NX_PTR_ERROR: недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="15b51-474">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_delete"></a><span data-ttu-id="15b51-475">nx_lwm2m_client_session_delete</span><span class="sxs-lookup"><span data-stu-id="15b51-475">nx_lwm2m_client_session_delete</span></span>

<span data-ttu-id="15b51-476">Удаление сеанса клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-476">Delete LWM2M Client Session</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-477">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-477">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_delete(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="15b51-478">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-478">Description</span></span>

<span data-ttu-id="15b51-479">Данная служба удаляет сеанс клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-479">This service deletes a LWM2M Client Session.</span></span>

<span data-ttu-id="15b51-480">Когда клиент LWM2M удаляется вызовом nx_lwm2m_client_delete, также удаляются все сеансы, подключенные к этому клиенту.</span><span class="sxs-lookup"><span data-stu-id="15b51-480">When a LWM2M Client is deleted by calling nx_lwm2m_client_delete all sessions attached to the client are also deleted.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-481">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-481">Parameters</span></span>

- <span data-ttu-id="15b51-482">**session_ptr**: указатель на блок управления сеансом клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-482">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-483">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-483">Return Values</span></span>

- <span data-ttu-id="15b51-484">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-484">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-485">NX_PTR_ERROR: недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="15b51-485">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_deregister"></a><span data-ttu-id="15b51-486">nx_lwm2m_client_session_deregister</span><span class="sxs-lookup"><span data-stu-id="15b51-486">nx_lwm2m_client_session_deregister</span></span>

<span data-ttu-id="15b51-487">Завершение сеанса взаимодействия с сервером LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-487">Terminate a session with a LWM2M Server</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-488">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-488">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_deregister(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="15b51-489">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-489">Description</span></span>

<span data-ttu-id="15b51-490">Данная служба выполняет операцию De-Register на сервере LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-490">This service performs a 'De-Register' operation to a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-491">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-491">Parameters</span></span>

- <span data-ttu-id="15b51-492">**session_ptr**: указатель на блок управления сеансом клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-492">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-493">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-493">Return Values</span></span>

- <span data-ttu-id="15b51-494">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-494">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-495">**NX_LWM2M_NOT_REGISTERED**: клиент не зарегистрирован на сервере.</span><span class="sxs-lookup"><span data-stu-id="15b51-495">**NX_LWM2M_NOT_REGISTERED**: The client is not registered to the server.</span></span>
- <span data-ttu-id="15b51-496">NX_PTR_ERROR: недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="15b51-496">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_error_get"></a><span data-ttu-id="15b51-497">nx_lwm2m_client_session_error_get</span><span class="sxs-lookup"><span data-stu-id="15b51-497">nx_lwm2m_client_session_error_get</span></span>

<span data-ttu-id="15b51-498">Получение последней ошибки сеанса.</span><span class="sxs-lookup"><span data-stu-id="15b51-498">Get last error of a session</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-499">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-499">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_error_get(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="15b51-500">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-500">Description</span></span>

<span data-ttu-id="15b51-501">Данная служба возвращает код ошибки сеанса в случае, когда сеанс находится в состоянии ошибки.</span><span class="sxs-lookup"><span data-stu-id="15b51-501">This service returns the error code of the session when the session is in an error state.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-502">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-502">Parameters</span></span>

- <span data-ttu-id="15b51-503">**session_ptr**: указатель на блок управления сеансом клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-503">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-504">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-504">Return Values</span></span>

- <span data-ttu-id="15b51-505">**NX_SUCCESS**: сеанс не находится в состоянии ошибки.</span><span class="sxs-lookup"><span data-stu-id="15b51-505">**NX_SUCCESS**: The session is not in error state.</span></span>
- <span data-ttu-id="15b51-506">**NX_LWM2M_ADDRESS_ERROR**: недопустимый адрес сервера.</span><span class="sxs-lookup"><span data-stu-id="15b51-506">**NX_LWM2M_ADDRESS_ERROR**: Invalid server address.</span></span>
- <span data-ttu-id="15b51-507">**NX_LWM2M_BUFFER_TOO_SMALL**: полезные данные запроса не вмещаются в сетевой буфер.</span><span class="sxs-lookup"><span data-stu-id="15b51-507">**NX_LWM2M_BUFFER_TOO_SMALL**: Payload of request doesn't fit in network buffer.</span></span>
- <span data-ttu-id="15b51-508">**NX_LWM2M_ NX_LWM2M_DTLS_ERROR**: не удалось установить защищенное подключение к серверу.</span><span class="sxs-lookup"><span data-stu-id="15b51-508">**NX_LWM2M_DTLS_ERROR**: Failed to establish secured connection with server.</span></span>
- <span data-ttu-id="15b51-509">**NX_LWM2M_ERROR**: неопределенная ошибка.</span><span class="sxs-lookup"><span data-stu-id="15b51-509">**NX_LWM2M_ERROR**: Unspecified error.</span></span>
- <span data-ttu-id="15b51-510">**NX_LWM2M_FORBIDDEN**: сервер отказал в регистрации.</span><span class="sxs-lookup"><span data-stu-id="15b51-510">**NX_LWM2M_FORBIDDEN**: Registration refused by server.</span></span>
- <span data-ttu-id="15b51-511">**NX_LWM2M_NOT_FOUND**: клиент не найден сервером при обновлении или отмене регистрации.</span><span class="sxs-lookup"><span data-stu-id="15b51-511">**NX_LWM2M_NOT_FOUND**: Client not found by server when updating/deregistering.</span></span>
- <span data-ttu-id="15b51-512">**NX_LWM2M_SERVER_INSTANCE_DELETED**: экземпляр объекта сервера, соответствующий сеансу, был удален.</span><span class="sxs-lookup"><span data-stu-id="15b51-512">**NX_LWM2M_SERVER_INSTANCE_DELETED**: The Server Object Instance corresponding to the session has been deleted.</span></span>
- <span data-ttu-id="15b51-513">**NX_LWM2M_TIMED_OUT**: нет ответа с сервера.</span><span class="sxs-lookup"><span data-stu-id="15b51-513">**NX_LWM2M_TIMED_OUT**: No answer from server.</span></span>
- <span data-ttu-id="15b51-514">NX_PTR_ERROR: недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="15b51-514">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_register"></a><span data-ttu-id="15b51-515">nx_lwm2m_client_session_register</span><span class="sxs-lookup"><span data-stu-id="15b51-515">nx_lwm2m_client_session_register</span></span>

<span data-ttu-id="15b51-516">Запуск сеанса взаимодействия с сервером LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-516">Start a session with a LWM2M Server</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-517">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-517">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register(NX_LWM2M_CLIENT_SESSION *session_ptr,
                    NX_LWM2M_ID server_id, ULONG ip_address, UINT port);
```

### <a name="description"></a><span data-ttu-id="15b51-518">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-518">Description</span></span>

<span data-ttu-id="15b51-519">Данная служба выполняет операцию Register на сервере LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-519">This service performs a 'Register' operation to a LWM2M Server.</span></span> <span data-ttu-id="15b51-520">Сервер должен иметь соответствующий экземпляр сервера в объекте сервера.</span><span class="sxs-lookup"><span data-stu-id="15b51-520">The server must have a corresponding server instance in the Server Object.</span></span>

<span data-ttu-id="15b51-521">Если регистрация прошла успешно, клиент LWM2M будет обрабатывать дальнейшие операции с сервера и периодически отправлять сообщения Update, пока регистрация клиента не будет отменена.</span><span class="sxs-lookup"><span data-stu-id="15b51-521">If the registration is successful the LWM2M Client will process further operations from the server and will periodically send 'Update' messages until the client is de-registered.</span></span>

<span data-ttu-id="15b51-522">Любой текущий активный сеанс прерывается этим вызовом и заменяется новым сеансом LWM2M Server.</span><span class="sxs-lookup"><span data-stu-id="15b51-522">Any current active session is aborted by this call and replaced by the new LWM2M Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-523">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-523">Parameters</span></span>

- <span data-ttu-id="15b51-524">**session_ptr**: указатель на блок управления сеансом клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-524">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="15b51-525">**server_id**: краткий идентификатор сервера LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-525">**server_id**: The Short Server ID of the LWM2M Server.</span></span>
- <span data-ttu-id="15b51-526">**ip_address**: IP-адрес сервера.</span><span class="sxs-lookup"><span data-stu-id="15b51-526">**ip_address**: The IP address of the server.</span></span>
- <span data-ttu-id="15b51-527">**port**: UDP-порт сервера.</span><span class="sxs-lookup"><span data-stu-id="15b51-527">**port**: The UDP port of the server.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-528">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-528">Return Values</span></span>

- <span data-ttu-id="15b51-529">**NX_SUCCESS**: операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="15b51-529">**NX_SUCCESS**: Successful operation..</span></span>
- <span data-ttu-id="15b51-530">**NX_LWM2M_NOT_FOUND**: отсутствует экземпляр объекта сервера, соответствующий короткому идентификатору сервера.</span><span class="sxs-lookup"><span data-stu-id="15b51-530">**NX_LWM2M_NOT_FOUND**: There is No Server Object instance corresponding to the Short Server ID.</span></span>
- <span data-ttu-id="15b51-531">NX_PTR_ERROR: недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="15b51-531">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_register_dtls"></a><span data-ttu-id="15b51-532">nx_lwm2m_client_session_register_dtls</span><span class="sxs-lookup"><span data-stu-id="15b51-532">nx_lwm2m_client_session_register_dtls</span></span>

<span data-ttu-id="15b51-533">Запуск безопасного сеанса взаимодействия с сервером LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-533">Start a secure session with a LWM2M Server</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-534">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-534">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register_dtls(NX_LWM2M_CLIENT_SESSION *session_ptr,
    NX_LWM2M_ID server_id, ULONG ip_address, UINT port, NX_SECURE_DTLS_SESSION
    *dtls_session_ptr, UINT dtls_local_port);
```

### <a name="description"></a><span data-ttu-id="15b51-535">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-535">Description</span></span>

<span data-ttu-id="15b51-536">Данная служба выполняет операцию Register на сервере LWM2M, используя безопасное подключение DTLS.</span><span class="sxs-lookup"><span data-stu-id="15b51-536">This service performs a 'Register' operation to a LWM2M Server using a secure DTLS connection.</span></span> <span data-ttu-id="15b51-537">Сервер должен иметь соответствующий экземпляр сервера в объекте сервера.</span><span class="sxs-lookup"><span data-stu-id="15b51-537">The server must have a corresponding server instance in the Server Object.</span></span>

<span data-ttu-id="15b51-538">Перед вызовом данной функции необходимо настроить сеанс DTLS с использованием соответствующих комплектов шифров и материала ключа.</span><span class="sxs-lookup"><span data-stu-id="15b51-538">The DTLS session must have been configured with the proper cipher suites and key material before calling this function.</span></span> <span data-ttu-id="15b51-539">Необходимо определить NX_SECURE_ENABLE_DTLS.</span><span class="sxs-lookup"><span data-stu-id="15b51-539">NX_SECURE_ENABLE_DTLS must be defined.</span></span>

<span data-ttu-id="15b51-540">Каждый сеанс DTLS использует собственный сокет UDP для обмена данными, поэтому локальный порт dtls_local_port должен быть разным для каждого сеанса, если приложение создает несколько безопасных сеансов.</span><span class="sxs-lookup"><span data-stu-id="15b51-540">Each DTLS session uses its own UDP socket for communication, so the local port dtls_local_port must be different for each session if the application creates several secure sessions.</span></span>

<span data-ttu-id="15b51-541">Если регистрация прошла успешно, клиент LWM2M будет обрабатывать дальнейшие операции с сервера и периодически отправлять сообщения Update, пока регистрация клиента не будет отменена.</span><span class="sxs-lookup"><span data-stu-id="15b51-541">If the registration is successful the LWM2M Client will process further operations from the server and will periodically send 'Update' messages until the client is de-registered.</span></span>

<span data-ttu-id="15b51-542">Любой текущий активный сеанс прерывается этим вызовом и заменяется новым сеансом LWM2M Server.</span><span class="sxs-lookup"><span data-stu-id="15b51-542">Any current active session is aborted by this call and replaced by the new LWM2M Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-543">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-543">Parameters</span></span>

- <span data-ttu-id="15b51-544">**session_ptr**: указатель на блок управления сеансом клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-544">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="15b51-545">**server_id**: краткий идентификатор сервера LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-545">**server_id**: The Short Server ID of the LWM2M Server.</span></span>
- <span data-ttu-id="15b51-546">**ip_address**: IP-адрес сервера.</span><span class="sxs-lookup"><span data-stu-id="15b51-546">**ip_address**: The IP address of the server.</span></span>
- <span data-ttu-id="15b51-547">**port**: UDP-порт сервера.</span><span class="sxs-lookup"><span data-stu-id="15b51-547">**port**: The UDP port of the server.</span></span>
- <span data-ttu-id="15b51-548">**dtls_session_ptr**: сеанс DTLS, используемый для сеанса LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-548">**dtls_session_ptr**: The DTLS session to use for the LWM2M session.</span></span>
- <span data-ttu-id="15b51-549">**dtls_local_port**: локальный UDP-порт, используемый для сеанса DTLS.</span><span class="sxs-lookup"><span data-stu-id="15b51-549">**dtls_local_port**: The local UDP port used for the DTLS session.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-550">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-550">Return Values</span></span>

- <span data-ttu-id="15b51-551">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-551">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-552">**NX_LWM2M_NOT_FOUND**: отсутствует экземпляр объекта сервера, соответствующий короткому идентификатору сервера.</span><span class="sxs-lookup"><span data-stu-id="15b51-552">**NX_LWM2M_NOT_FOUND**: There is No Server Object instance corresponding to the Short Server ID.</span></span>
- <span data-ttu-id="15b51-553">NX_PTR_ERROR: недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="15b51-553">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_update"></a><span data-ttu-id="15b51-554">nx_lwm2m_client_session_update</span><span class="sxs-lookup"><span data-stu-id="15b51-554">nx_lwm2m_client_session_update</span></span>

<span data-ttu-id="15b51-555">Обновление сеанса взаимодействия с сервером LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-555">Update a session with a LWM2M Server</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-556">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-556">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_update(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="15b51-557">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-557">Description</span></span>

<span data-ttu-id="15b51-558">Данная служба выполняет операцию Update на сервере LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-558">This service performs an 'Update' operation to a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-559">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-559">Parameters</span></span>

- <span data-ttu-id="15b51-560">**session_ptr**: указатель на блок управления сеансом клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-560">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-561">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-561">Return Values</span></span>

- <span data-ttu-id="15b51-562">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-562">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-563">**NX_LWM2M_NOT_REGISTERED**: клиент не зарегистрирован на сервере.</span><span class="sxs-lookup"><span data-stu-id="15b51-563">**NX_LWM2M_NOT_REGISTERED**: The client is not registered to the server.</span></span>
- <span data-ttu-id="15b51-564">NX_PTR_ERROR: недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="15b51-564">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_unlock"></a><span data-ttu-id="15b51-565">nx_lwm2m_client_unlock</span><span class="sxs-lookup"><span data-stu-id="15b51-565">nx_lwm2m_client_unlock</span></span>

<span data-ttu-id="15b51-566">Разблокирование клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-566">Unlock LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-567">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-567">Prototype</span></span>

```c
UINT nx_lwm2m_client_unlock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="15b51-568">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-568">Description</span></span>

<span data-ttu-id="15b51-569">Данная служба разблокирует заблокированный ранее клиент LWM2M вызовом nx_lwm2m_client_unlock().</span><span class="sxs-lookup"><span data-stu-id="15b51-569">This service unlocks the LWM2M Client previoulsy locked by a call to nx_lwm2m_client_unlock().</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-570">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-570">Parameters</span></span>

- <span data-ttu-id="15b51-571">**client_ptr**: указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-571">**client_ptr**: Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-572">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-572">Return Values</span></span>

- <span data-ttu-id="15b51-573">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-573">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-574">NX_PTR_ERROR: недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="15b51-574">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_firmware_create"></a><span data-ttu-id="15b51-575">nx_lwm2m_firmware_create</span><span class="sxs-lookup"><span data-stu-id="15b51-575">nx_lwm2m_firmware_create</span></span>

<span data-ttu-id="15b51-576">Создание объекта обновления встроенного ПО.</span><span class="sxs-lookup"><span data-stu-id="15b51-576">Create Firmware Update Object</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-577">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-577">Prototype</span></span>

```c
UINT nx_lwm2m_firmware_create(NX_LWM2M_FIRMWARE *firmware_ptr,
    NX_LWM2M_CLIENT *client_ptr, UINT protocols,
    NX_LWM2M_FIRMWARE_PACKAGE_CALLBACK package_callback,
    NX_LWM2M_FIRMWARE_PACKAGE_URI_CALLBACK package_uri_callback,
    NX_LWM2M_FIRMWARE_UPDATE_CALLBACK update_callback);
```

### <a name="description"></a><span data-ttu-id="15b51-578">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-578">Description</span></span>

<span data-ttu-id="15b51-579">Эта служба инициализирует объект обновления встроенного ПО и добавляет этот объект в созданный ранее клиент LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-579">This service initializes a Firmware Update Object and adds the Object to a previously created LWM2M Client.</span></span> <span data-ttu-id="15b51-580">Объект обновления встроенного ПО реализует ресурсы для взаимодействия с сервером LWM2M, но приложение должно обеспечить обратные вызовы для реализации фактических операций со встроенным ПО (скачивание, хранение и обновление встроенного ПО).</span><span class="sxs-lookup"><span data-stu-id="15b51-580">The Firmware Update Object implements the resources for communicating with a LWM2M Server but the application must provide callbacks for implementing the actual operations on the firmware (dowloading, storing, and updating the firmware).</span></span>

<span data-ttu-id="15b51-581">Параметр protocols указывает, какие протоколы поддерживаются приложением для получения встроенного ПО с помощью ресурса URI пакета. Определяются следующие флаги:</span><span class="sxs-lookup"><span data-stu-id="15b51-581">The protocols parameter indicates which protocols are supported by the application for retrieving the firmware with the 'Package URI' resource, the following flags are defined:</span></span>

<span data-ttu-id="15b51-582">NX_LWM2M_FIRMWARE_PROTOCOL_COAP, NX_LWM2M_FIRMWARE_PROTOCOL_COAPS, NX_LWM2M_FIRMWARE_PROTOCOL_HTTP, NX_LWM2M_FIRMWARE_PROTOCOL_HTPPS.</span><span class="sxs-lookup"><span data-stu-id="15b51-582">NX_LWM2M_FIRMWARE_PROTOCOL_COAP, NX_LWM2M_FIRMWARE_PROTOCOL_COAPS, NX_LWM2M_FIRMWARE_PROTOCOL_HTTP, NX_LWM2M_FIRMWARE_PROTOCOL_HTPPS.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-583">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-583">Parameters</span></span>

- <span data-ttu-id="15b51-584">**firmware_ptr**: указатель на блок управления объектом встроенного ПО.</span><span class="sxs-lookup"><span data-stu-id="15b51-584">**firmware_ptr**: Pointer to the Firmware Object control block.</span></span>
- <span data-ttu-id="15b51-585">**client_ptr**: указатель на созданный ранее клиент LWM2M.</span><span class="sxs-lookup"><span data-stu-id="15b51-585">**client_ptr**: Pointer to previsously created LWM2M Client.</span></span>
- <span data-ttu-id="15b51-586">**protocols**: флаги, указывающие, какие протоколы поддерживаются ресурсом URI пакета.</span><span class="sxs-lookup"><span data-stu-id="15b51-586">**protocols**: Flags indicating which protocols are supported by the Package URI resource.</span></span>
- <span data-ttu-id="15b51-587">**package_callback**: должен иметь значение NULL [подлежит уточнению].</span><span class="sxs-lookup"><span data-stu-id="15b51-587">**package_callback**: Must be NULL [TBD].</span></span>
- <span data-ttu-id="15b51-588">**package_uri_callback**: обратный вызов, используемый для реализации ресурса URI пакета.</span><span class="sxs-lookup"><span data-stu-id="15b51-588">**package_uri_callback**: Callback used to implement the Package URI resource.</span></span>
- <span data-ttu-id="15b51-589">**update_callback**: обратный вызов, используемый для реализации ресурса обновления.</span><span class="sxs-lookup"><span data-stu-id="15b51-589">**update_callback**: Callback used to implement the Update resource.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-590">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-590">Return Values</span></span>

- <span data-ttu-id="15b51-591">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-591">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-592">NX_PTR_ERROR: недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="15b51-592">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_firmware_package_info_set"></a><span data-ttu-id="15b51-593">nx_lwm2m_firmware_package_info_set</span><span class="sxs-lookup"><span data-stu-id="15b51-593">nx_lwm2m_firmware_package_info_set</span></span>

<span data-ttu-id="15b51-594">Настройка сведений о пакете обновления встроенного ПО.</span><span class="sxs-lookup"><span data-stu-id="15b51-594">Set Firmware Update Package Information</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-595">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-595">Prototype</span></span>

```c
UINT nx_lwm2m_firmware_package_info_set(NX_LWM2M_FIRMWARE *firmware_ptr,
                                const CHAR *name, const CHAR *version);
```

### <a name="description"></a><span data-ttu-id="15b51-596">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-596">Description</span></span>

<span data-ttu-id="15b51-597">Эта служба изменяет значения ресурсов PkgName (6) и PkgVersion (7) объекта обновления встроенного ПО.</span><span class="sxs-lookup"><span data-stu-id="15b51-597">This service changes the values of the 'PkgName' (6) and 'PkgVersion' (7) resources of the Firmware Update Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-598">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-598">Parameters</span></span>

- <span data-ttu-id="15b51-599">**firmware_ptr**: указатель на объект обновления встроенного ПО.</span><span class="sxs-lookup"><span data-stu-id="15b51-599">**firmware_ptr**: Pointer to the Firmware Update Object.</span></span>
- <span data-ttu-id="15b51-600">**name**: новое значение имени пакета.</span><span class="sxs-lookup"><span data-stu-id="15b51-600">**name**: The new value of the Package Name.</span></span>
- <span data-ttu-id="15b51-601">**version**: новое значение версии пакета.</span><span class="sxs-lookup"><span data-stu-id="15b51-601">**version**: The new value of the Package Version.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-602">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-602">Return Values</span></span>

- <span data-ttu-id="15b51-603">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-603">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-604">NX_PTR_ERROR: недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="15b51-604">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_firmware_result_set"></a><span data-ttu-id="15b51-605">nx_lwm2m_firmware_result_set</span><span class="sxs-lookup"><span data-stu-id="15b51-605">nx_lwm2m_firmware_result_set</span></span>

<span data-ttu-id="15b51-606">Настройка результата обновления встроенного ПО.</span><span class="sxs-lookup"><span data-stu-id="15b51-606">Set Firmware Update Result</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-607">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-607">Prototype</span></span>

```c
UINT nx_lwm2m_firmware_result_set(NX_LWM2M_FIRMWARE *firmware_ptr, UCHAR result);
```

### <a name="description"></a><span data-ttu-id="15b51-608">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-608">Description</span></span>

<span data-ttu-id="15b51-609">Эта служба изменяет значение ресурса Update Result (5) объекта обновления встроенного ПО.</span><span class="sxs-lookup"><span data-stu-id="15b51-609">This service changes the value of the 'Update Result' (5) resource of the Firmware Update Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-610">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-610">Parameters</span></span>

- <span data-ttu-id="15b51-611">**firmware_ptr**: указатель на объект обновления встроенного ПО.</span><span class="sxs-lookup"><span data-stu-id="15b51-611">**firmware_ptr**: Pointer to the Firmware Update Object.</span></span>
- <span data-ttu-id="15b51-612">**result**: новое значение ресурса Update Result.</span><span class="sxs-lookup"><span data-stu-id="15b51-612">**result**: The new value of the Update Result resource.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-613">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-613">Return Values</span></span>

- <span data-ttu-id="15b51-614">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-614">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-615">NX_PTR_ERROR: недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="15b51-615">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_firmware_state_set"></a><span data-ttu-id="15b51-616">nx_lwm2m_firmware_state_set</span><span class="sxs-lookup"><span data-stu-id="15b51-616">nx_lwm2m_firmware_state_set</span></span>

<span data-ttu-id="15b51-617">Настройка состояния обновления встроенного ПО.</span><span class="sxs-lookup"><span data-stu-id="15b51-617">Set Firmware Update State</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-618">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-618">Prototype</span></span>

```c
UINT nx_lwm2m_firmware_state_set(NX_LWM2M_FIRMWARE *firmware_ptr, UCHAR state);
```

### <a name="description"></a><span data-ttu-id="15b51-619">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-619">Description</span></span>

<span data-ttu-id="15b51-620">Эта служба изменяет значение ресурса State (3) объекта обновления встроенного ПО.</span><span class="sxs-lookup"><span data-stu-id="15b51-620">This service changes the value of the 'State' (3) resource of the Firmware Update Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-621">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-621">Parameters</span></span>

- <span data-ttu-id="15b51-622">**firmware_ptr**: указатель на объект обновления встроенного ПО.</span><span class="sxs-lookup"><span data-stu-id="15b51-622">**firmware_ptr**: Pointer to the Firmware Update Object.</span></span>
- <span data-ttu-id="15b51-623">**state**: новое значение ресурса State.</span><span class="sxs-lookup"><span data-stu-id="15b51-623">**state**: The new value of the State resource.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-624">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-624">Return Values</span></span>

- <span data-ttu-id="15b51-625">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-625">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-626">NX_PTR_ERROR: недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="15b51-626">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_object_resource_changed"></a><span data-ttu-id="15b51-627">nx_lwm2m_object_resource_changed</span><span class="sxs-lookup"><span data-stu-id="15b51-627">nx_lwm2m_object_resource_changed</span></span>

<span data-ttu-id="15b51-628">Сигнальное изменение значения ресурса экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="15b51-628">Signal change of a resource value of an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-629">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-629">Prototype</span></span>

```c
UINT nx_lwm2m_object_resource_changed(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a><span data-ttu-id="15b51-630">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-630">Description</span></span>

<span data-ttu-id="15b51-631">Эта служба используется реализацией объекта для сообщения клиенту LWM2M о том, что одно из его значений ресурсов изменилось.</span><span class="sxs-lookup"><span data-stu-id="15b51-631">This service is used by an Object implementation to signals the LWM2M Client that one of its resource value has changed.</span></span> <span data-ttu-id="15b51-632">Если за ресурсом наблюдает сервер LWM2M, клиент LWM2M отправит соответствующее уведомление.</span><span class="sxs-lookup"><span data-stu-id="15b51-632">The LWM2M Client will send a notification if the resource is observed by a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-633">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-633">Parameters</span></span>

- <span data-ttu-id="15b51-634">**object_ptr**: указатель на реализацию объекта.</span><span class="sxs-lookup"><span data-stu-id="15b51-634">**object_ptr**: Pointer to the Object implementation.</span></span>
- <span data-ttu-id="15b51-635">**instance_ptr**: указатель на экземпляр объекта.</span><span class="sxs-lookup"><span data-stu-id="15b51-635">**instance_ptr**: Pointer to the Object Instance.</span></span>
- <span data-ttu-id="15b51-636">**resource**: указатель на структуру, описывающую измененный ресурс.</span><span class="sxs-lookup"><span data-stu-id="15b51-636">**resource**: Pointer to the structure describing the resource that has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-637">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-637">Return Values</span></span>

- <span data-ttu-id="15b51-638">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-638">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-639">NX_PTR_ERROR: недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="15b51-639">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_resource_get_boolean"></a><span data-ttu-id="15b51-640">nx_lwm2m_resource_get_boolean</span><span class="sxs-lookup"><span data-stu-id="15b51-640">nx_lwm2m_resource_get_boolean</span></span>

<span data-ttu-id="15b51-641">Получение значения логического ресурса.</span><span class="sxs-lookup"><span data-stu-id="15b51-641">Get the value of a Boolean Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-642">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-642">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_boolean(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a><span data-ttu-id="15b51-643">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-643">Description</span></span>

<span data-ttu-id="15b51-644">Служба извлекает значение логического ресурса.</span><span class="sxs-lookup"><span data-stu-id="15b51-644">The service retrieves the value of a Boolean Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-645">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-645">Parameters</span></span>

- <span data-ttu-id="15b51-646">**value**: указатель на описание значения ресурса.</span><span class="sxs-lookup"><span data-stu-id="15b51-646">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="15b51-647">**bool_ptr**: указатель на целевое логическое значение.</span><span class="sxs-lookup"><span data-stu-id="15b51-647">**bool_ptr**: Pointer to the destination Boolean value.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-648">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-648">Return Values</span></span>

- <span data-ttu-id="15b51-649">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-649">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-650">**NX_LWM2M_BAD_ENCODING**: значение ресурса не является логическим значением.</span><span class="sxs-lookup"><span data-stu-id="15b51-650">**NX_LWM2M_BAD_ENCODING**: The resource value is not a Boolean value.</span></span>

## <a name="nx_lwm2m_resource_get_float32"></a><span data-ttu-id="15b51-651">nx_lwm2m_resource_get_float32</span><span class="sxs-lookup"><span data-stu-id="15b51-651">nx_lwm2m_resource_get_float32</span></span>

<span data-ttu-id="15b51-652">Получение значения 32-разрядного ресурса с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="15b51-652">Get the value of a 32-bit Floating Point Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-653">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-653">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_float32(const NX_LWM2M_RESOURCE *value,
                                NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a><span data-ttu-id="15b51-654">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-654">Description</span></span>

<span data-ttu-id="15b51-655">Эта служба извлекает значение 32-разрядного ресурса с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="15b51-655">The service retrieves the value of a 32-bit Floating Point Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-656">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-656">Parameters</span></span>

- <span data-ttu-id="15b51-657">**value**: указатель на описание значения ресурса.</span><span class="sxs-lookup"><span data-stu-id="15b51-657">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="15b51-658">**float32_ptr**: указатель на целевое 32-разрядное значение с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="15b51-658">**float32_ptr**: Pointer to the destination 32-Bit Floating Point value.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-659">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-659">Return Values</span></span>

- <span data-ttu-id="15b51-660">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-660">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-661">**NX_LWM2M_BAD_ENCODING**: значение ресурса не является значением с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="15b51-661">**NX_LWM2M_BAD_ENCODING**: The resource value is not a Floating Point value.</span></span>

## <a name="nx_lwm2m_resource_get_float64"></a><span data-ttu-id="15b51-662">nx_lwm2m_resource_get_float64</span><span class="sxs-lookup"><span data-stu-id="15b51-662">nx_lwm2m_resource_get_float64</span></span>

<span data-ttu-id="15b51-663">Получение значения 64-разрядного ресурса с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="15b51-663">Get the value of a 64-bit Floating Point Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-664">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-664">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_float64(const NX_LWM2M_RESOURCE *value,
                                NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a><span data-ttu-id="15b51-665">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-665">Description</span></span>

<span data-ttu-id="15b51-666">Эта служба извлекает значение 64-разрядного ресурса с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="15b51-666">The service retrieves the value of a 64-bit Floating Point Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-667">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-667">Parameters</span></span>

- <span data-ttu-id="15b51-668">**value**: указатель на описание значения ресурса.</span><span class="sxs-lookup"><span data-stu-id="15b51-668">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="15b51-669">**float64_ptr**: указатель на целевое 64-разрядное значение с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="15b51-669">**float64_ptr**: Pointer to the destination 64-Bit Floating Point value.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-670">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-670">Return Values</span></span>

- <span data-ttu-id="15b51-671">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-671">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-672">**NX_LWM2M_BAD_ENCODING**: значение ресурса не является значением с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="15b51-672">**NX_LWM2M_BAD_ENCODING**: The resource value is not a Floating Point value.</span></span>

## <a name="nx_lwm2m_resource_get_integer32"></a><span data-ttu-id="15b51-673">nx_lwm2m_resource_get_integer32</span><span class="sxs-lookup"><span data-stu-id="15b51-673">nx_lwm2m_resource_get_integer32</span></span>

<span data-ttu-id="15b51-674">Получение значения 32-разрядного целочисленного ресурса.</span><span class="sxs-lookup"><span data-stu-id="15b51-674">Get the value of a 32-Bit Integer Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-675">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-675">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_integer32(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_INT32 *int32_ptr);
```

### <a name="description"></a><span data-ttu-id="15b51-676">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-676">Description</span></span>

<span data-ttu-id="15b51-677">Служба извлекает значение 32-разрядного целочисленного ресурса.</span><span class="sxs-lookup"><span data-stu-id="15b51-677">The service retrieves the value of a 32-Bit Integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-678">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-678">Parameters</span></span>

- <span data-ttu-id="15b51-679">**value**: указатель на описание значения ресурса.</span><span class="sxs-lookup"><span data-stu-id="15b51-679">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="15b51-680">**int32_ptr**: указатель на целевое 32-разрядное целочисленное значение.</span><span class="sxs-lookup"><span data-stu-id="15b51-680">**int32_ptr**: Pointer to the destination 32-Bit Integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-681">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-681">Return Values</span></span>

- <span data-ttu-id="15b51-682">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-682">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-683">**NX_LWM2M_BAD_ENCODING**: значение ресурса не является целым числом или целочисленное значение не умещается в 32-разрядном числе.</span><span class="sxs-lookup"><span data-stu-id="15b51-683">**NX_LWM2M_BAD_ENCODING**: The resource value is not an Integer value, or the Integer value doesn't fit in a 32-Bit number.</span></span>

## <a name="nx_lwm2m_resource_get_integer64"></a><span data-ttu-id="15b51-684">nx_lwm2m_resource_get_integer64</span><span class="sxs-lookup"><span data-stu-id="15b51-684">nx_lwm2m_resource_get_integer64</span></span>

<span data-ttu-id="15b51-685">Получение значения 64-разрядного целочисленного ресурса.</span><span class="sxs-lookup"><span data-stu-id="15b51-685">Get the value of a 64-Bit Integer Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-686">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-686">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_integer64(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_INT64 *int64_ptr);
```

### <a name="description"></a><span data-ttu-id="15b51-687">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-687">Description</span></span>

<span data-ttu-id="15b51-688">Служба извлекает значение 64-разрядного целочисленного ресурса.</span><span class="sxs-lookup"><span data-stu-id="15b51-688">The service retrieves the value of a 64-Bit Integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-689">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-689">Parameters</span></span>

- <span data-ttu-id="15b51-690">**value**: указатель на описание значения ресурса.</span><span class="sxs-lookup"><span data-stu-id="15b51-690">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="15b51-691">**int64_ptr**: указатель на целевое 64-разрядное целочисленное значение.</span><span class="sxs-lookup"><span data-stu-id="15b51-691">**int64_ptr**: Pointer to the destination 64-Bit Integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-692">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-692">Return Values</span></span>

- <span data-ttu-id="15b51-693">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-693">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-694">**NX_LWM2M_BAD_ENCODING**: значение ресурса не является целым числом.</span><span class="sxs-lookup"><span data-stu-id="15b51-694">**NX_LWM2M_BAD_ENCODING**: The resource value is not an Integer value.</span></span>

## <a name="nx_lwm2m_resource_get_objlnk"></a><span data-ttu-id="15b51-695">nx_lwm2m_resource_get_objlnk</span><span class="sxs-lookup"><span data-stu-id="15b51-695">nx_lwm2m_resource_get_objlnk</span></span>

<span data-ttu-id="15b51-696">Получение значения ресурса ссылки на объект.</span><span class="sxs-lookup"><span data-stu-id="15b51-696">Get the value of an Object Link Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-697">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-697">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_objlnk(const NX_LWM2M_RESOURCE *value,
                                    NX_LWM2M_OBJLNK *objlnk_ptr);
```

### <a name="description"></a><span data-ttu-id="15b51-698">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-698">Description</span></span>

<span data-ttu-id="15b51-699">Служба извлекает значение ресурса ссылки на объект.</span><span class="sxs-lookup"><span data-stu-id="15b51-699">The service retrieves the value of an Object Link Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-700">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-700">Parameters</span></span>

- <span data-ttu-id="15b51-701">**value**: указатель на описание значения ресурса.</span><span class="sxs-lookup"><span data-stu-id="15b51-701">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="15b51-702">**objlnk_ptr**: указатель на целевое значение ссылки на объект.</span><span class="sxs-lookup"><span data-stu-id="15b51-702">**objlnk_ptr**: Pointer to the destination Object Link value.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-703">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-703">Return Values</span></span>

- <span data-ttu-id="15b51-704">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-704">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-705">**NX_LWM2M_BAD_ENCODING**: значение ресурса не является ссылкой на объект.</span><span class="sxs-lookup"><span data-stu-id="15b51-705">**NX_LWM2M_BAD_ENCODING**: The resource value is not an Object Link value.</span></span>

## <a name="nx_lwm2m_resource_get_opaque"></a><span data-ttu-id="15b51-706">nx_lwm2m_resource_get_opaque</span><span class="sxs-lookup"><span data-stu-id="15b51-706">nx_lwm2m_resource_get_opaque</span></span>

<span data-ttu-id="15b51-707">Получение значения непрозрачного ресурса.</span><span class="sxs-lookup"><span data-stu-id="15b51-707">Get the value of an Opaque Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-708">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-708">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_opaque(const NX_LWM2M_RESOURCE *value,
            const VOID **opaque_ptr_ptr, UINT *opaque_length_ptr);
```

### <a name="description"></a><span data-ttu-id="15b51-709">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-709">Description</span></span>

<span data-ttu-id="15b51-710">Эта служба извлекает значение непрозрачного ресурса.</span><span class="sxs-lookup"><span data-stu-id="15b51-710">The service retrieves the value of an Opaque Resource.</span></span>

<span data-ttu-id="15b51-711">Значение непрозрачного ресурса состоит из указателя на буфер и длины.</span><span class="sxs-lookup"><span data-stu-id="15b51-711">An opaque resource value consists of a pointer to a buffer and a length.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-712">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-712">Parameters</span></span>

- <span data-ttu-id="15b51-713">**value**: указатель на описание значения ресурса.</span><span class="sxs-lookup"><span data-stu-id="15b51-713">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="15b51-714">**opaque_ptr_ptr**: указатель на указатель на целевой непрозрачный буфер.</span><span class="sxs-lookup"><span data-stu-id="15b51-714">**opaque_ptr_ptr**: Pointer to the destination opaque buffer pointer.</span></span>
- <span data-ttu-id="15b51-715">**opaque_length_ptr**: указатель на длину целевого непрозрачного буфера.</span><span class="sxs-lookup"><span data-stu-id="15b51-715">**opaque_length_ptr**: Pointer to the destination opaque buffer length.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-716">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-716">Return Values</span></span>

- <span data-ttu-id="15b51-717">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-717">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-718">**NX_LWM2M_BAD_ENCODING**: значение ресурса не является непрозрачным значением.</span><span class="sxs-lookup"><span data-stu-id="15b51-718">**NX_LWM2M_BAD_ENCODING**: The resource value is not an Opaque value.</span></span>

## <a name="nx_lwm2m_resource_get_string"></a><span data-ttu-id="15b51-719">nx_lwm2m_resource_get_string</span><span class="sxs-lookup"><span data-stu-id="15b51-719">nx_lwm2m_resource_get_string</span></span>

<span data-ttu-id="15b51-720">Получение значения строкового ресурса.</span><span class="sxs-lookup"><span data-stu-id="15b51-720">Get the value of a String Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-721">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-721">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_string(const NX_LWM2M_RESOURCE *value,
            const CHAR **string_ptr_ptr, UINT *string_length_ptr);
```

### <a name="description"></a><span data-ttu-id="15b51-722">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-722">Description</span></span>

<span data-ttu-id="15b51-723">Эта служба извлекает значение строкового ресурса.</span><span class="sxs-lookup"><span data-stu-id="15b51-723">The service retrieves the value of a String Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-724">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-724">Parameters</span></span>

- <span data-ttu-id="15b51-725">**value**: указатель на описание значения ресурса.</span><span class="sxs-lookup"><span data-stu-id="15b51-725">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="15b51-726">**string_ptr_ptr**: указатель на указатель на целевую строку.</span><span class="sxs-lookup"><span data-stu-id="15b51-726">**string_ptr_ptr**: Pointer to the destination string pointer.</span></span>
- <span data-ttu-id="15b51-727">**string_length_ptr**: указатель на длину целевой строки.</span><span class="sxs-lookup"><span data-stu-id="15b51-727">**string_length_ptr**: Pointer to the destination string length.</span></span> <span data-ttu-id="15b51-728">Может иметь значение NULL, если строка оканчивается нулевым символом.</span><span class="sxs-lookup"><span data-stu-id="15b51-728">Can be NULL if the string is null-terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-729">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-729">Return Values</span></span>

- <span data-ttu-id="15b51-730">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-730">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-731">**NX_LWM2M_BAD_ENCODING**: значение ресурса не является строкой.</span><span class="sxs-lookup"><span data-stu-id="15b51-731">**NX_LWM2M_BAD_ENCODING**: The resource value is not a String value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_boolean"></a><span data-ttu-id="15b51-732">nx_lwm2m_resource_multiple_get_boolean</span><span class="sxs-lookup"><span data-stu-id="15b51-732">nx_lwm2m_resource_multiple_get_boolean</span></span>

<span data-ttu-id="15b51-733">Получение значения логического ресурса для нескольких экземпляров ресурса.</span><span class="sxs-lookup"><span data-stu-id="15b51-733">Get the value of a Boolean Resource Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-734">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-734">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_boolean(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a><span data-ttu-id="15b51-735">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-735">Description</span></span>

<span data-ttu-id="15b51-736">Эта служба получает значение экземпляра логического ресурса для нескольких ресурсов.</span><span class="sxs-lookup"><span data-stu-id="15b51-736">The service retrieves the value of a Boolean Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-737">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-737">Parameters</span></span>

- <span data-ttu-id="15b51-738">**value**: указатель на описание значения нескольких ресурсов.</span><span class="sxs-lookup"><span data-stu-id="15b51-738">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="15b51-739">**index**: индекс экземпляра, который необходимо получить из массива значений ресурсов.</span><span class="sxs-lookup"><span data-stu-id="15b51-739">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="15b51-740">**instance_id_ptr**: указатель на идентификатор целевого экземпляра.</span><span class="sxs-lookup"><span data-stu-id="15b51-740">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="15b51-741">**bool_ptr**: указатель на целевое логическое значение.</span><span class="sxs-lookup"><span data-stu-id="15b51-741">**bool_ptr**: Pointer to the destination Boolean value.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-742">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-742">Return Values</span></span>

- <span data-ttu-id="15b51-743">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-743">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-744">**NX_LWM2M_BAD_PARAMETER**: индекс вне диапазона.</span><span class="sxs-lookup"><span data-stu-id="15b51-744">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="15b51-745">**NX_LWM2M_BAD_ENCODING**: ресурс не является множественным ресурсом или значение ресурса не является логическим значением.</span><span class="sxs-lookup"><span data-stu-id="15b51-745">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not a Boolean value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_float32"></a><span data-ttu-id="15b51-746">nx_lwm2m_resource_multiple_get_float32</span><span class="sxs-lookup"><span data-stu-id="15b51-746">nx_lwm2m_resource_multiple_get_float32</span></span>

<span data-ttu-id="15b51-747">Получение значения 32-разрядного ресурса с плавающей запятой для нескольких экземпляров ресурса.</span><span class="sxs-lookup"><span data-stu-id="15b51-747">Get the value of a 32-bit Floating Point Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-748">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-748">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_float32(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a><span data-ttu-id="15b51-749">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-749">Description</span></span>

<span data-ttu-id="15b51-750">Эта служба получает значение экземпляра 32-разрядного ресурса с плавающей запятой для нескольких ресурсов.</span><span class="sxs-lookup"><span data-stu-id="15b51-750">The service retrieves the value of a 32-bit Floating Point Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-751">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-751">Parameters</span></span>

- <span data-ttu-id="15b51-752">**value**: указатель на описание значения нескольких ресурсов.</span><span class="sxs-lookup"><span data-stu-id="15b51-752">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="15b51-753">**index**: индекс экземпляра, который необходимо получить из массива значений ресурсов.</span><span class="sxs-lookup"><span data-stu-id="15b51-753">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="15b51-754">**instance_id_ptr**: указатель на идентификатор целевого экземпляра.</span><span class="sxs-lookup"><span data-stu-id="15b51-754">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="15b51-755">**float32_ptr**: указатель на целевое 32-разрядное значение с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="15b51-755">**float32_ptr**: Pointer to the destination 32-Bit Floating Point value.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-756">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-756">Return Values</span></span>

- <span data-ttu-id="15b51-757">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-757">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-758">**NX_LWM2M_BAD_PARAMETER**: индекс вне диапазона.</span><span class="sxs-lookup"><span data-stu-id="15b51-758">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="15b51-759">**NX_LWM2M_BAD_ENCODING**: ресурс не является множественным ресурсом или значение ресурса не является числом с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="15b51-759">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not a Floating Point value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_float64"></a><span data-ttu-id="15b51-760">nx_lwm2m_resource_multiple_get_float64</span><span class="sxs-lookup"><span data-stu-id="15b51-760">nx_lwm2m_resource_multiple_get_float64</span></span>

<span data-ttu-id="15b51-761">Получение значения 64-разрядного ресурса с плавающей запятой для нескольких экземпляров ресурса.</span><span class="sxs-lookup"><span data-stu-id="15b51-761">Get the value of a 64-bit Floating Point Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-762">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-762">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_float64(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a><span data-ttu-id="15b51-763">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-763">Description</span></span>

<span data-ttu-id="15b51-764">Эта служба получает значение экземпляра 64-разрядного ресурса с плавающей запятой для нескольких ресурсов.</span><span class="sxs-lookup"><span data-stu-id="15b51-764">The service retrieves the value of a 64-bit Floating Point Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-765">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-765">Parameters</span></span>

- <span data-ttu-id="15b51-766">**value**: указатель на описание значения нескольких ресурсов.</span><span class="sxs-lookup"><span data-stu-id="15b51-766">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="15b51-767">**index**: индекс экземпляра, который необходимо получить из массива значений ресурсов.</span><span class="sxs-lookup"><span data-stu-id="15b51-767">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="15b51-768">**instance_id_ptr**: указатель на идентификатор целевого экземпляра.</span><span class="sxs-lookup"><span data-stu-id="15b51-768">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="15b51-769">**float64_ptr**: указатель на целевое 64-разрядное значение с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="15b51-769">**float64_ptr**: Pointer to the destination 64-Bit Floating Point value.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-770">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-770">Return Values</span></span>

- <span data-ttu-id="15b51-771">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-771">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-772">**NX_LWM2M_BAD_PARAMETER**: индекс вне диапазона.</span><span class="sxs-lookup"><span data-stu-id="15b51-772">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="15b51-773">**NX_LWM2M_BAD_ENCODING**: ресурс не является множественным ресурсом или значение ресурса не является числом с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="15b51-773">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not a Floating Point value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_integer32"></a><span data-ttu-id="15b51-774">nx_lwm2m_resource_multiple_get_integer32</span><span class="sxs-lookup"><span data-stu-id="15b51-774">nx_lwm2m_resource_multiple_get_integer32</span></span>

<span data-ttu-id="15b51-775">Получение значения 32-разрядного целочисленного ресурса для нескольких экземпляров ресурса.</span><span class="sxs-lookup"><span data-stu-id="15b51-775">Get the value of a 32-Bit Integer Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-776">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-776">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_integer32(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_INT32 *int32_ptr);
```

### <a name="description"></a><span data-ttu-id="15b51-777">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-777">Description</span></span>

<span data-ttu-id="15b51-778">Эта служба получает значение экземпляра 32-разрядного целочисленного ресурса для нескольких ресурсов.</span><span class="sxs-lookup"><span data-stu-id="15b51-778">The service retrieves the value of a 32-Bit Integer Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-779">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-779">Parameters</span></span>

- <span data-ttu-id="15b51-780">**value**: указатель на описание значения нескольких ресурсов.</span><span class="sxs-lookup"><span data-stu-id="15b51-780">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="15b51-781">**index**: индекс экземпляра, который необходимо получить из массива значений ресурсов.</span><span class="sxs-lookup"><span data-stu-id="15b51-781">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="15b51-782">**instance_id_ptr**: указатель на идентификатор целевого экземпляра.</span><span class="sxs-lookup"><span data-stu-id="15b51-782">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="15b51-783">**int32_ptr**: указатель на целевое 32-разрядное целочисленное значение.</span><span class="sxs-lookup"><span data-stu-id="15b51-783">**int32_ptr**: Pointer to the destination 32-Bit Integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-784">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-784">Return Values</span></span>

- <span data-ttu-id="15b51-785">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-785">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-786">**NX_LWM2M_BAD_PARAMETER**: индекс вне диапазона.</span><span class="sxs-lookup"><span data-stu-id="15b51-786">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="15b51-787">**NX_LWM2M_BAD_ENCODING**: ресурс не является множественным ресурсом, значение ресурса не является целым числом или целочисленное значение не умещается в 32-разрядном числе.</span><span class="sxs-lookup"><span data-stu-id="15b51-787">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not an Integer value, or the Integer value doesn't fit in a 32-Bit number.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_integer64"></a><span data-ttu-id="15b51-788">nx_lwm2m_resource_multiple_get_integer64</span><span class="sxs-lookup"><span data-stu-id="15b51-788">nx_lwm2m_resource_multiple_get_integer64</span></span>

<span data-ttu-id="15b51-789">Получение значения 64-разрядного целочисленного ресурса для нескольких экземпляров ресурса.</span><span class="sxs-lookup"><span data-stu-id="15b51-789">Get the value of a 64-Bit Integer Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-790">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-790">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_integer64(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_INT64 *int64_ptr);
```

### <a name="description"></a><span data-ttu-id="15b51-791">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-791">Description</span></span>

<span data-ttu-id="15b51-792">Эта служба получает значение экземпляра 64-разрядного целочисленного ресурса для нескольких ресурсов.</span><span class="sxs-lookup"><span data-stu-id="15b51-792">The service retrieves the value of a 64-Bit Integer Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-793">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-793">Parameters</span></span>

- <span data-ttu-id="15b51-794">**value**: указатель на описание значения нескольких ресурсов.</span><span class="sxs-lookup"><span data-stu-id="15b51-794">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="15b51-795">**index**: индекс экземпляра, который необходимо получить из массива значений ресурсов.</span><span class="sxs-lookup"><span data-stu-id="15b51-795">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="15b51-796">**instance_id_ptr**: указатель на идентификатор целевого экземпляра.</span><span class="sxs-lookup"><span data-stu-id="15b51-796">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="15b51-797">**int64_ptr**: указатель на целевое 64-разрядное целочисленное значение.</span><span class="sxs-lookup"><span data-stu-id="15b51-797">**int64_ptr**: Pointer to the destination 64-Bit Integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-798">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-798">Return Values</span></span>

- <span data-ttu-id="15b51-799">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-799">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-800">**NX_LWM2M_BAD_PARAMETER**: индекс вне диапазона.</span><span class="sxs-lookup"><span data-stu-id="15b51-800">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="15b51-801">**NX_LWM2M_BAD_ENCODING**: ресурс не является множественным ресурсом или значение ресурса не является целым числом.</span><span class="sxs-lookup"><span data-stu-id="15b51-801">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not an Integer value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_objlnk"></a><span data-ttu-id="15b51-802">nx_lwm2m_resource_multiple_get_objlnk</span><span class="sxs-lookup"><span data-stu-id="15b51-802">nx_lwm2m_resource_multiple_get_objlnk</span></span>

<span data-ttu-id="15b51-803">Получение значения ссылки на объект для нескольких экземпляров ресурса.</span><span class="sxs-lookup"><span data-stu-id="15b51-803">Get the value of an Object Link Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-804">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-804">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_objlnk(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_OBJLNK *objlnk_ptr);
```

### <a name="description"></a><span data-ttu-id="15b51-805">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-805">Description</span></span>

<span data-ttu-id="15b51-806">Эта служба получает значение экземпляра ресурса ссылки на объект для нескольких ресурсов.</span><span class="sxs-lookup"><span data-stu-id="15b51-806">The service retrieves the value of an Object Link Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-807">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-807">Parameters</span></span>

- <span data-ttu-id="15b51-808">**value**: указатель на описание значения нескольких ресурсов.</span><span class="sxs-lookup"><span data-stu-id="15b51-808">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="15b51-809">**index**: индекс экземпляра, который необходимо получить из массива значений ресурсов.</span><span class="sxs-lookup"><span data-stu-id="15b51-809">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="15b51-810">**instance_id_ptr**: указатель на идентификатор целевого экземпляра.</span><span class="sxs-lookup"><span data-stu-id="15b51-810">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="15b51-811">**objlnk_ptr**: указатель на целевое значение ссылки на объект.</span><span class="sxs-lookup"><span data-stu-id="15b51-811">**objlnk_ptr**: Pointer to the destination Object Link value.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-812">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-812">Return Values</span></span>

- <span data-ttu-id="15b51-813">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-813">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-814">**NX_LWM2M_BAD_PARAMETER**: индекс вне диапазона.</span><span class="sxs-lookup"><span data-stu-id="15b51-814">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="15b51-815">**NX_LWM2M_BAD_ENCODING**: ресурс не является множественным ресурсом или значение ресурса не является ссылкой на объект.</span><span class="sxs-lookup"><span data-stu-id="15b51-815">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not an Object Link value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_opaque"></a><span data-ttu-id="15b51-816">nx_lwm2m_resource_multiple_get_opaque</span><span class="sxs-lookup"><span data-stu-id="15b51-816">nx_lwm2m_resource_multiple_get_opaque</span></span>

<span data-ttu-id="15b51-817">Получение значения непрозрачного ресурса для нескольких экземпляров ресурса.</span><span class="sxs-lookup"><span data-stu-id="15b51-817">Get the value of an Opaque Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-818">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-818">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_opaque(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, const VOID **opaque_ptr_ptr,
    UINT *opaque_length_ptr);
```

### <a name="description"></a><span data-ttu-id="15b51-819">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-819">Description</span></span>

<span data-ttu-id="15b51-820">Эта служба получает значение экземпляра непрозрачного ресурса для нескольких ресурсов.</span><span class="sxs-lookup"><span data-stu-id="15b51-820">The service retrieves the value of an Opaque Resource Instance from a Multiple Resource.</span></span>

<span data-ttu-id="15b51-821">Значение непрозрачного ресурса состоит из указателя на буфер и длины.</span><span class="sxs-lookup"><span data-stu-id="15b51-821">An opaque resource value consists of a pointer to a buffer and a length.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-822">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-822">Parameters</span></span>

- <span data-ttu-id="15b51-823">**value**: указатель на описание значения нескольких ресурсов.</span><span class="sxs-lookup"><span data-stu-id="15b51-823">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="15b51-824">**index**: индекс экземпляра, который необходимо получить из массива значений ресурсов.</span><span class="sxs-lookup"><span data-stu-id="15b51-824">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="15b51-825">**instance_id_ptr**: указатель на идентификатор целевого экземпляра.</span><span class="sxs-lookup"><span data-stu-id="15b51-825">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="15b51-826">**opaque_ptr_ptr**: указатель на указатель на целевой непрозрачный буфер.</span><span class="sxs-lookup"><span data-stu-id="15b51-826">**opaque_ptr_ptr**: Pointer to the destination opaque buffer pointer.</span></span>
- <span data-ttu-id="15b51-827">**opaque_length_ptr**: указатель на длину целевого непрозрачного буфера.</span><span class="sxs-lookup"><span data-stu-id="15b51-827">**opaque_length_ptr**: Pointer to the destination opaque buffer length.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-828">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-828">Return Values</span></span>

- <span data-ttu-id="15b51-829">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-829">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-830">**NX_LWM2M_BAD_PARAMETER**: индекс вне диапазона.</span><span class="sxs-lookup"><span data-stu-id="15b51-830">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="15b51-831">**NX_LWM2M_BAD_ENCODING**: ресурс не является множественным ресурсом или значение ресурса не является непрозрачным значением.</span><span class="sxs-lookup"><span data-stu-id="15b51-831">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not an Opaque value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_string"></a><span data-ttu-id="15b51-832">nx_lwm2m_resource_multiple_get_string</span><span class="sxs-lookup"><span data-stu-id="15b51-832">nx_lwm2m_resource_multiple_get_string</span></span>

<span data-ttu-id="15b51-833">Получение значения строкового ресурса для нескольких экземпляров ресурса.</span><span class="sxs-lookup"><span data-stu-id="15b51-833">Get the value of a String Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="15b51-834">Прототип</span><span class="sxs-lookup"><span data-stu-id="15b51-834">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_string(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, const CHAR **string_ptr_ptr,
    UINT *string_length_ptr);
```

### <a name="description"></a><span data-ttu-id="15b51-835">Описание</span><span class="sxs-lookup"><span data-stu-id="15b51-835">Description</span></span>

<span data-ttu-id="15b51-836">Эта служба получает значение экземпляра строкового ресурса для нескольких ресурсов.</span><span class="sxs-lookup"><span data-stu-id="15b51-836">The service retrieves the value of a String Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="15b51-837">Параметры</span><span class="sxs-lookup"><span data-stu-id="15b51-837">Parameters</span></span>

- <span data-ttu-id="15b51-838">**value**: указатель на описание значения нескольких ресурсов.</span><span class="sxs-lookup"><span data-stu-id="15b51-838">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="15b51-839">**index**: индекс экземпляра, который необходимо получить из массива значений ресурсов.</span><span class="sxs-lookup"><span data-stu-id="15b51-839">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="15b51-840">**instance_id_ptr**: указатель на идентификатор целевого экземпляра.</span><span class="sxs-lookup"><span data-stu-id="15b51-840">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="15b51-841">**string_ptr_ptr**: указатель на указатель на целевую строку.</span><span class="sxs-lookup"><span data-stu-id="15b51-841">**string_ptr_ptr**: Pointer to the destination string pointer.</span></span>
- <span data-ttu-id="15b51-842">**string_length_ptr**: указатель на длину целевой строки.</span><span class="sxs-lookup"><span data-stu-id="15b51-842">**string_length_ptr**: Pointer to the destination string length.</span></span> <span data-ttu-id="15b51-843">Может иметь значение NULL, если строка оканчивается нулевым символом.</span><span class="sxs-lookup"><span data-stu-id="15b51-843">Can be NULL if the string is null-terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="15b51-844">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="15b51-844">Return Values</span></span>

- <span data-ttu-id="15b51-845">**NX_SUCCESS**: операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="15b51-845">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="15b51-846">**NX_LWM2M_BAD_PARAMETER**: индекс вне диапазона.</span><span class="sxs-lookup"><span data-stu-id="15b51-846">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="15b51-847">**NX_LWM2M_BAD_ENCODING**: ресурс не является множественным ресурсом или значение экземпляра не является строкой.</span><span class="sxs-lookup"><span data-stu-id="15b51-847">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the instance value is not a String value.</span></span>
