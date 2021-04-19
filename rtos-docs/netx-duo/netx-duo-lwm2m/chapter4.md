---
title: Глава 4 - Описание услуг LWM2M CLIENT
description: Эта глава содержит описание всех клиентских служб LWM2M в алфавитном порядке.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 825a215ba756b39b6d76e6cc773c288e8b8aab01
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814672"
---
# <a name="chapter-4--description-of-lwm2m-client-services"></a><span data-ttu-id="6a191-103">Глава 4 Описание услуг LWM2M CLIENT</span><span class="sxs-lookup"><span data-stu-id="6a191-103">Chapter 4  Description of LWM2M CLIENT Services</span></span>

<span data-ttu-id="6a191-104">В данной главе приводится описание всех нижеперечисленных клиентских сервисов LWM2M в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="6a191-104">This chapter contains a description of all LWM2M Client services listed below in alphabetic order.</span></span>

<span data-ttu-id="6a191-105">В разделе «Возвращаемые значения» в следующих описаниях API значения, выделенные полужирным шрифтом **BOLD**, не зависят от определения **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки ошибок API, в то время как значения, не выделенные жирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="6a191-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the  **NX_DISABLE_ERROR_CHECKING** define that is used to disable API  error checking, while non-bold values are completely disabled.</span></span>

<span data-ttu-id="6a191-106">**Управление клиентом LWM2M:**</span><span class="sxs-lookup"><span data-stu-id="6a191-106">**LWM2M Client Management:**</span></span>

- <span data-ttu-id="6a191-107">nx_lwm2m_client_create: *Создать клиент LWM2M*</span><span class="sxs-lookup"><span data-stu-id="6a191-107">nx_lwm2m_client_create: *Create LWM2M Client*</span></span>

- <span data-ttu-id="6a191-108">nx_lwm2m_client_delete: *Удалить клиент LWM2M*</span><span class="sxs-lookup"><span data-stu-id="6a191-108">nx_lwm2m_client_delete: *Delete LWM2M Client*</span></span>

- <span data-ttu-id="6a191-109">nx_lwm2m_client_lock: *Заблокировать клиент LWM2M*</span><span class="sxs-lookup"><span data-stu-id="6a191-109">nx_lwm2m_client_lock: *Lock LWM2M Client*</span></span>

- <span data-ttu-id="6a191-110">nx_lwm2m_client_unlock: *Разблокировать клиент LWM2M*</span><span class="sxs-lookup"><span data-stu-id="6a191-110">nx_lwm2m_client_unlock: *Unlock LWM2M Client*</span></span>

<span data-ttu-id="6a191-111">**Управление клиентскими сеансами LWM2M:**</span><span class="sxs-lookup"><span data-stu-id="6a191-111">**LWM2M Client Session Management:**</span></span>

- <span data-ttu-id="6a191-112">nx_lwm2m_client_session_create: *Создать клиентский сеанс LWM2M*</span><span class="sxs-lookup"><span data-stu-id="6a191-112">nx_lwm2m_client_session_create: *Create LWM2M Client Session*</span></span>

- <span data-ttu-id="6a191-113">nx_lwm2m_client_session_delete: *Удалить клиентский сеанс LWM2M*</span><span class="sxs-lookup"><span data-stu-id="6a191-113">nx_lwm2m_client_session_delete: *Delete LWM2M Client Session*</span></span>

- <span data-ttu-id="6a191-114">nx_lwm2m_client_session_bootstrap: *Начать сеанс с Bootstrap Server*</span><span class="sxs-lookup"><span data-stu-id="6a191-114">nx_lwm2m_client_session_bootstrap: *Start a session with a Bootstrap Server*</span></span>

- <span data-ttu-id="6a191-115">nx_lwm2m_client_session_bootstrap_dtls: *Начать безопасный сеанс с Bootstrap Server*</span><span class="sxs-lookup"><span data-stu-id="6a191-115">nx_lwm2m_client_session_bootstrap_dtls: *Start a secure session with a Bootstrap Server*</span></span>

- <span data-ttu-id="6a191-116">nx_lwm2m_client_session_register_info_get: *Получить информацию о регистрации сервера LWM2M*</span><span class="sxs-lookup"><span data-stu-id="6a191-116">nx_lwm2m_client_session_register_info_get: *Get LWM2M Server register info*</span></span>

- <span data-ttu-id="6a191-117">nx_lwm2m_client_session_register: *Начать сеанс с сервером LWM2M*</span><span class="sxs-lookup"><span data-stu-id="6a191-117">nx_lwm2m_client_session_register: *Start a session with a LWM2M Server*</span></span>

- <span data-ttu-id="6a191-118">nx_lwm2m_client_session_register_dtls: *Начать безопасный сеанс с сервером LWM2M*</span><span class="sxs-lookup"><span data-stu-id="6a191-118">nx_lwm2m_client_session_register_dtls: *Start a secure session with a LWM2M Server*</span></span>

- <span data-ttu-id="6a191-119">nx_lwm2m_client_session_update: *Обновить сеанс с сервером LWM2M*</span><span class="sxs-lookup"><span data-stu-id="6a191-119">nx_lwm2m_client_session_update: *Update a session with a LWM2M Server*</span></span>

- <span data-ttu-id="6a191-120">nx_lwm2m_client_session_deregister: *Завершить сеанс с сервером LWM2M*</span><span class="sxs-lookup"><span data-stu-id="6a191-120">nx_lwm2m_client_session_deregister: *Terminate a session with a LWM2M Server*</span></span>

- <span data-ttu-id="6a191-121">nx_lwm2m_client_session_error_get: *Получить сведения о последней ошибке сеанса*</span><span class="sxs-lookup"><span data-stu-id="6a191-121">nx_lwm2m_client_session_error_get: *Get last error of a session*</span></span>

<span data-ttu-id="6a191-122">**Реализация объекта устройства:**</span><span class="sxs-lookup"><span data-stu-id="6a191-122">**Device Object Implementation:**</span></span>

- <span data-ttu-id="6a191-123">nx_lwm2m_client_device_callbacks_set: *Установить обратные вызовы приложения объекта устройства*</span><span class="sxs-lookup"><span data-stu-id="6a191-123">nx_lwm2m_client_device_callbacks_set: *Set Device Object application callbacks*</span></span>

- <span data-ttu-id="6a191-124">nx_lwm2m_client_device_error_push: *Добавить код ошибки в объект устройства*</span><span class="sxs-lookup"><span data-stu-id="6a191-124">nx_lwm2m_client_device_error_push: *Add error code to Device Object*</span></span>

- <span data-ttu-id="6a191-125">nx_lwm2m_client_device_error_reset: *Сбросить коды ошибок объекта устройства*</span><span class="sxs-lookup"><span data-stu-id="6a191-125">nx_lwm2m_client_device_error_reset: *Reset error codes of Device Object*</span></span>

- <span data-ttu-id="6a191-126">nx_lwm2m_client_device_resource_changed: *Изменение сигнала ресурса объекта устройства*</span><span class="sxs-lookup"><span data-stu-id="6a191-126">nx_lwm2m_client_device_resource_changed: *Signal change of Device Object resource*</span></span>

<span data-ttu-id="6a191-127">**Реализация объекта обновления встроенного ПО:**</span><span class="sxs-lookup"><span data-stu-id="6a191-127">**Firmware Update Object Implementation:**</span></span>

- <span data-ttu-id="6a191-128">nx_lwm2m_firmware_create: *Создать объект обновления встроенного ПО*</span><span class="sxs-lookup"><span data-stu-id="6a191-128">nx_lwm2m_firmware_create: *Create Firmware Update Object*</span></span>

- <span data-ttu-id="6a191-129">nx_lwm2m_firmware_package_info_set: *Установить информацию о пакете обновления встроенного ПО*</span><span class="sxs-lookup"><span data-stu-id="6a191-129">nx_lwm2m_firmware_package_info_set: *Set Firmware Update Package Information*</span></span>

- <span data-ttu-id="6a191-130">nx_lwm2m_firmware_result_set: *Установить результат обновления встроенного ПО*</span><span class="sxs-lookup"><span data-stu-id="6a191-130">nx_lwm2m_firmware_result_set: *Set Firmware Update Result*</span></span>

- <span data-ttu-id="6a191-131">nx_lwm2m_firmware_state_set: *Установить состояние обновления встроенного ПО*</span><span class="sxs-lookup"><span data-stu-id="6a191-131">nx_lwm2m_firmware_state_set: *Set Firmware Update State*</span></span>

<span data-ttu-id="6a191-132">**Реализация пользовательских объектов:**</span><span class="sxs-lookup"><span data-stu-id="6a191-132">**Custom Objects Implementation:**</span></span>

- <span data-ttu-id="6a191-133">nx_lwm2m_client_object_add: *Добавить реализацию объекта в клиент LWM2M*</span><span class="sxs-lookup"><span data-stu-id="6a191-133">nx_lwm2m_client_object_add: *Add Object implementation to LWM2M Client*</span></span>

- <span data-ttu-id="6a191-134">nx_lwm2m_client_object_remove: *Удалить реализацию объекта из клиента LWM2M*</span><span class="sxs-lookup"><span data-stu-id="6a191-134">nx_lwm2m_client_object_remove: *Remove Object implementation from LWM2M Client*</span></span>

- <span data-ttu-id="6a191-135">nx_lwm2m_client_object_instance_add: *Добавить экземпляр объекта в клиент LWM2M*</span><span class="sxs-lookup"><span data-stu-id="6a191-135">nx_lwm2m_client_object_instance_add: *Add Object Instance to LWM2M Client*</span></span>

- <span data-ttu-id="6a191-136">nx_lwm2m_client_object_instance_remove: *Удалить экземпляр объекта из клиента LWM2M*</span><span class="sxs-lookup"><span data-stu-id="6a191-136">nx_lwm2m_client_object_instance_remove: *Remove Object Instance from LWM2M Client*</span></span>

- <span data-ttu-id="6a191-137">nx_lwm2m_object_resource_changed: *Сигнальное изменение значения ресурса экземпляра объекта*</span><span class="sxs-lookup"><span data-stu-id="6a191-137">nx_lwm2m_object_resource_changed: *Signal change of a resource value of an Object Instance*</span></span>

<span data-ttu-id="6a191-138">**Управление локальным устройством**</span><span class="sxs-lookup"><span data-stu-id="6a191-138">**Local Device Management**</span></span>

- <span data-ttu-id="6a191-139">nx_lwm2m_client_object_create: *Создать новый экземпляр объекта*</span><span class="sxs-lookup"><span data-stu-id="6a191-139">nx_lwm2m_client_object_create: *Create a new Object Instance*</span></span>

- <span data-ttu-id="6a191-140">nx_lwm2m_client_object_delete: *Удалить экземпляр объекта*</span><span class="sxs-lookup"><span data-stu-id="6a191-140">nx_lwm2m_client_object_delete: *Delete an Object Instance*</span></span>

- <span data-ttu-id="6a191-141">nx_lwm2m_client_object_discover: *Найти ресурсы экземпляра объекта*</span><span class="sxs-lookup"><span data-stu-id="6a191-141">nx_lwm2m_client_object_discover: *Discover resources of an Object Instance*</span></span>

- <span data-ttu-id="6a191-142">nx_lwm2m_client_object_execute: *Выполнить ресурс экземпляра объекта*</span><span class="sxs-lookup"><span data-stu-id="6a191-142">nx_lwm2m_client_object_execute: *Execute resource of an Object Instance*</span></span>

- <span data-ttu-id="6a191-143">nx_lwm2m_client_object_next_get: *Получить список объектов, реализованных клиентом LWM2M*</span><span class="sxs-lookup"><span data-stu-id="6a191-143">nx_lwm2m_client_object_next_get: *Get the list of Objects implemented by the LWM2M Client*</span></span>

- <span data-ttu-id="6a191-144">nx_lwm2m_client_object_instance_next_get: *Получить список экземпляров объекта*</span><span class="sxs-lookup"><span data-stu-id="6a191-144">nx_lwm2m_client_object_instance_next_get: *Get the list of Instances of an Object*</span></span>

- <span data-ttu-id="6a191-145">nx_lwm2m_client_object_read: *Сосчитать значения ресурсов экземпляра объекта*</span><span class="sxs-lookup"><span data-stu-id="6a191-145">nx_lwm2m_client_object_read: *Read resources values of an Object Instance*</span></span>

- <span data-ttu-id="6a191-146">nx_lwm2m_client_object_write: *Изменить значения ресурсов экземпляра объекта*</span><span class="sxs-lookup"><span data-stu-id="6a191-146">nx_lwm2m_client_object_write: *Change resources values of an Object instance*</span></span>

<span data-ttu-id="6a191-147">**Информация о ресурсах и настройка значений:**</span><span class="sxs-lookup"><span data-stu-id="6a191-147">**Resources Info and Values Setting:**</span></span>

- <span data-ttu-id="6a191-148">nx_lwm2m_client_resource_info_set: *Установить информацию о ресурсе*</span><span class="sxs-lookup"><span data-stu-id="6a191-148">nx_lwm2m_client_resource_info_set: *Set the resource info*</span></span>

- <span data-ttu-id="6a191-149">nx_lwm2m_client_resource_string_set: *Задать значение ресурса как строку*</span><span class="sxs-lookup"><span data-stu-id="6a191-149">nx_lwm2m_client_resource_string_set: *Set the resource value as string*</span></span>

- <span data-ttu-id="6a191-150">nx_lwm2m_client_resource_integer32_set: *Установить значение ресурса как 32-битное целое число*</span><span class="sxs-lookup"><span data-stu-id="6a191-150">nx_lwm2m_client_resource_integer32_set: *Set the resource value as 32-Bit integer*</span></span>

- <span data-ttu-id="6a191-151">nx_lwm2m_client_resource_integer64_set: *Установить значение ресурса как 64-битное целое число*</span><span class="sxs-lookup"><span data-stu-id="6a191-151">nx_lwm2m_client_resource_integer64_set: *Set the resource value as 64-Bit integer*</span></span>

- <span data-ttu-id="6a191-152">nx_lwm2m_client_resource_float32_set: *Установить значение ресурса как 32-битное число с плавающей точкой*</span><span class="sxs-lookup"><span data-stu-id="6a191-152">nx_lwm2m_client_resource_float32_set: *Set the resource value as 32-Bit float*</span></span>

- <span data-ttu-id="6a191-153">nx_lwm2m_client_resource_float64_set: *Установить значение ресурса как 64-битное число с плавающей точкой*</span><span class="sxs-lookup"><span data-stu-id="6a191-153">nx_lwm2m_client_resource_float64_set: *Set the resource value as 64-Bit float*</span></span>

- <span data-ttu-id="6a191-154">nx_lwm2m_client_resource_boolean_set: *Установить значение ресурса как логическое*</span><span class="sxs-lookup"><span data-stu-id="6a191-154">nx_lwm2m_client_resource_boolean_set: *Set the resource value as boolean*</span></span>

- <span data-ttu-id="6a191-155">nx_lwm2m_client_resource_objlnk_set: *Установить значение ресурса как ссылку на объект*</span><span class="sxs-lookup"><span data-stu-id="6a191-155">nx_lwm2m_client_resource_objlnk_set: *Set the resource value as object link*</span></span>

- <span data-ttu-id="6a191-156">nx_lwm2m_client_resource_opaque_set: *Установите значение ресурса как непрозрачное*</span><span class="sxs-lookup"><span data-stu-id="6a191-156">nx_lwm2m_client_resource_opaque_set: *Set the resource value as opaque*</span></span>

- <span data-ttu-id="6a191-157">nx_lwm2m_client_resource_instance_set: *Установить значение ресурса как экземпляр для нескольких ресурсов*</span><span class="sxs-lookup"><span data-stu-id="6a191-157">nx_lwm2m_client_resource_instance_set: *Set the resource value as instance for multiple resource*</span></span>
-
- <span data-ttu-id="6a191-158">nx_lwm2m_client_resource_dim_set: *Установить измерение ресурса для нескольких ресурсов .*</span><span class="sxs-lookup"><span data-stu-id="6a191-158">nx_lwm2m_client_resource_dim_set: *Set the resource dimension for multiple resource.*</span></span>

<span data-ttu-id="6a191-159">**Информация о ресурсах и получении значений:**</span><span class="sxs-lookup"><span data-stu-id="6a191-159">**Resources Info and Values Getting:**</span></span>

- <span data-ttu-id="6a191-160">nx_lwm2m_client_resource_info_get: *Получить информацию о ресурсе*</span><span class="sxs-lookup"><span data-stu-id="6a191-160">nx_lwm2m_client_resource_info_get: *Get the resource info*</span></span>

- <span data-ttu-id="6a191-161">nx_lwm2m_client_resource_string_get: *Получить значение строкового ресурса*</span><span class="sxs-lookup"><span data-stu-id="6a191-161">nx_lwm2m_client_resource_string_get: *Get the value of a string resource*</span></span>

- <span data-ttu-id="6a191-162">nx_lwm2m_client_resource_integer32_get: *Получить значение 32-битного целочисленного ресурса*</span><span class="sxs-lookup"><span data-stu-id="6a191-162">nx_lwm2m_client_resource_integer32_get: *Get the value of a 32-Bit integer resource*</span></span>

- <span data-ttu-id="6a191-163">nx_lwm2m_client_resource_integer64_get: *Получить значение 64-битного целочисленного ресурса*</span><span class="sxs-lookup"><span data-stu-id="6a191-163">nx_lwm2m_client_resource_integer64_get: *Get the value of a 64-Bit integer resource*</span></span>

- <span data-ttu-id="6a191-164">nx_lwm2m_client_resource_float32_get: *Получить значение 32-битного ресурса с плавающей точкой*</span><span class="sxs-lookup"><span data-stu-id="6a191-164">nx_lwm2m_client_resource_float32_get: *Get the value of a 32-Bit float resource*</span></span>

- <span data-ttu-id="6a191-165">nx_lwm2m_client_resource_float64_get: *Получить значение 64-битного ресурса с плавающей точкой*</span><span class="sxs-lookup"><span data-stu-id="6a191-165">nx_lwm2m_client_resource_float64_get: *Get the value of a 64-Bit float resource*</span></span>

- <span data-ttu-id="6a191-166">nx_lwm2m_client_resource_boolean_get: *Получить значение логического ресурса*</span><span class="sxs-lookup"><span data-stu-id="6a191-166">nx_lwm2m_client_resource_boolean_get: *Get the value of a boolean resource*</span></span>

- <span data-ttu-id="6a191-167">nx_lwm2m_client_resource_objlnk_get: *Получить значение ресурса ссылки на объект*</span><span class="sxs-lookup"><span data-stu-id="6a191-167">nx_lwm2m_client_resource_objlnk_get: *Get the value of an object link resource*</span></span>

- <span data-ttu-id="6a191-168">nx_lwm2m_client_resource_opaque_get: *Получить значение непрозрачного ресурса*</span><span class="sxs-lookup"><span data-stu-id="6a191-168">nx_lwm2m_client_resource_opaque_get: *Get the value of an opaque resource*</span></span>

- <span data-ttu-id="6a191-169">nx_lwm2m_client_resource_instance_get: *Получить экземпляр ресурса для нескольких ресурсов*</span><span class="sxs-lookup"><span data-stu-id="6a191-169">nx_lwm2m_client_resource_instance_get: *Get the resource instance for multiple resource*</span></span>

- <span data-ttu-id="6a191-170">lwm2m_client_resource_dim_get: *Получить измерение ресурса для нескольких ресурсов.*</span><span class="sxs-lookup"><span data-stu-id="6a191-170">nx_lwm2m_client_resource_dim_get: *Get the resource dimension for multiple resource.*</span></span>

## <a name="nx_lwm2m_client_create"></a><span data-ttu-id="6a191-171">nx_lwm2m_client_create</span><span class="sxs-lookup"><span data-stu-id="6a191-171">nx_lwm2m_client_create</span></span>

<span data-ttu-id="6a191-172">Создает клиент LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-172">Creates a LWM2M client.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-173">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-173">Prototype</span></span>

```C
UINT nx_lwm2m_client_create(
    NX_LWM2M_CLIENT client_ptr,
    NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    const CHAR *name_ptr,
    UINT name_length,
    const CHAR *msisdn_ptr,
    UINT msisdn_length,
    UCHAR binding_modes,
    VOID *stack_ptr,
    ULONG stack_size,
    UINT priority);
```

### <a name="description"></a><span data-ttu-id="6a191-174">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-174">Description</span></span>

<span data-ttu-id="6a191-175">Данная служба создает экземпляр клиента LWM2M, который запускается в контексте собственного потока ThreadX.</span><span class="sxs-lookup"><span data-stu-id="6a191-175">This service creates a LWM2M Client instance, which runs in the context of its own ThreadX thread.</span></span>

<span data-ttu-id="6a191-176">Клиент LWM2M реализует следующие объекты OMA LWM2M: безопасность (0), сервер (1), контроль доступа (2) и устройство (3).</span><span class="sxs-lookup"><span data-stu-id="6a191-176">The LWM2M Client implements the following OMA LWM2M Objects: Security (0), Server (1), Access Control (2) and Device (3).</span></span> <span data-ttu-id="6a191-177">Другие реализации объектов должны быть добавлены посредством приложения.</span><span class="sxs-lookup"><span data-stu-id="6a191-177">The other objects implementations must be added by the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-178">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-178">Parameters</span></span>

- <span data-ttu-id="6a191-179">**client_ptr** Указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-179">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="6a191-180">**ip_ptr** Указатель на ранее созданный экземпляр IP.</span><span class="sxs-lookup"><span data-stu-id="6a191-180">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="6a191-181">**packet_pool_ptr** Указатель на пул пакетов по умолчанию для данного клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-181">**packet_pool_ptr** Pointer to the default packet pool for this LWM2M Client.</span></span>
- <span data-ttu-id="6a191-182">**name_ptr** Указатель на имя конечной точки клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-182">**name_ptr** Pointer to LWM2M Client endpoint name.</span></span>
- <span data-ttu-id="6a191-183">**name_length** Длина имени конечной точки клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-183">**name_length** Length of LWM2M Client endpoint name.</span></span>
- <span data-ttu-id="6a191-184">**msisdn_ptr** Указатель на номер мобильного абонента сети ISDN, по которому можно связаться с клиентом LWM2M для использования с привязкой SMS, может иметь значение NULL, если привязка SMS не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="6a191-184">**msisdn_ptr** Pointer to the MSISDN where the LWM2M Client can be reached for use with the SMS binding, can be NULL if SMS binding is not supported.</span></span>
- <span data-ttu-id="6a191-185">**msisdn_length** Длина номера MSISDN.</span><span class="sxs-lookup"><span data-stu-id="6a191-185">**msisdn_length** Length of MSISDN number.</span></span>
- <span data-ttu-id="6a191-186">**binding_modes** Привязка и режимы, поддерживаемые клиентом LWM2M, должны являться комбинацией флагов NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S и NX_LWM2M_BINDING_SQ.</span><span class="sxs-lookup"><span data-stu-id="6a191-186">**binding_modes** The binding and modes supported by the LWM2M Client, must be a combination of NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S and NX_LWM2M_BINDING_SQ flags.</span></span>
- <span data-ttu-id="6a191-187">**stack_ptr** Указатель на область стека потока клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-187">**stack_ptr** Pointer to LWM2M Client thread stack area.</span></span>
- <span data-ttu-id="6a191-188">**stack_size** Размер стека потока клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-188">**stack_size** The LWM2M Client thread stack size.</span></span>
- <span data-ttu-id="6a191-189">**priority** Приоритет клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-189">**priority** Priority of LWM2M Client.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-190">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-190">Return Values</span></span>

- <span data-ttu-id="6a191-191">**NX_SUCCESS** Клиент LWM2M успешно создан.</span><span class="sxs-lookup"><span data-stu-id="6a191-191">**NX_SUCCESS** The LWM2M Client has been successfully created.</span></span>
- <span data-ttu-id="6a191-192">**NX_LWM2M_CLIENT_ERROR** Ошибка создания клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-192">**NX_LWM2M_CLIENT_ERROR** LWM2M Client create error.</span></span>
- <span data-ttu-id="6a191-193">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Порт недоступен.</span><span class="sxs-lookup"><span data-stu-id="6a191-193">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="6a191-194">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-194">**NX_PTR_ERROR** Invalid pointer.</span></span>
- <span data-ttu-id="6a191-195">**NX_SIZE_ERROR** Недопустимый размер стека.</span><span class="sxs-lookup"><span data-stu-id="6a191-195">**NX_SIZE_ERROR** Invalid stack size.</span></span>
- <span data-ttu-id="6a191-196">**NX_OPTION_ERROR** Недопустимый приоритет.</span><span class="sxs-lookup"><span data-stu-id="6a191-196">**NX_OPTION_ERROR** Invalid priority.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-197">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-197">Allowed From</span></span>

<span data-ttu-id="6a191-198">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-198">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-199">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-199">Example</span></span>

```C
/* Create LWM2M Client instance.  */
status = nx_lwm2m_client_create(&lwm2m_client, &ip_0, &pool_0, 
  "netxlwm2mclient", sizeof("netxlwm2mclient") - 1,           
                                NX_NULL, 0, NX_LWM2M_CLIENT_BINDING_U, 
                                stack_ptr, stack_size, priority);

/* If status is NX_SUCCESS a LWM2M Client instance was successfully created.  */
```

## <a name="nx_lwm2m_client_delete"></a><span data-ttu-id="6a191-200">nx_lwm2m_client_delete</span><span class="sxs-lookup"><span data-stu-id="6a191-200">nx_lwm2m_client_delete</span></span>

<span data-ttu-id="6a191-201">Удаляет клиент LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-201">Deletes a LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-202">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-202">Prototype</span></span>

```C
UINT nx_lwm2m_client_delete(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="6a191-203">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-203">Description</span></span>

<span data-ttu-id="6a191-204">Данная служба удаляет ранее созданный экземпляр клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-204">This service deletes a previously created LWM2M Client instance.</span></span>

<span data-ttu-id="6a191-205">Все сеансы, подключенные в данный момент к клиенту, также удаляются посредством данного вызова.</span><span class="sxs-lookup"><span data-stu-id="6a191-205">All sessions currently attached the client are also deleted by this call.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-206">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-206">Parameters</span></span>

- <span data-ttu-id="6a191-207">**client_ptr** Указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-207">**client_ptr** Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-208">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-208">Return Values</span></span>

- <span data-ttu-id="6a191-209">**NX_SUCCESS** Клиент LWM2M успешно удален.</span><span class="sxs-lookup"><span data-stu-id="6a191-209">**NX_SUCCESS** The LWM2M Client has been successfully deleted.</span></span>
- <span data-ttu-id="6a191-210">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-210">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-211">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-211">Allowed From</span></span>

<span data-ttu-id="6a191-212">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-212">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-213">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-213">Example</span></span>

```c
/* Delete the LWM2M Client instance.  */
status = nx_lwm2m_client_create(&lwm2m_client);

/* If status is NX_SUCCESS a LWM2M Client instance was successfully deleted.  */
```

## <a name="nx_lwm2m_client_device_callback_set"></a><span data-ttu-id="6a191-214">nx_lwm2m_client_device_callback_set</span><span class="sxs-lookup"><span data-stu-id="6a191-214">nx_lwm2m_client_device_callback_set</span></span>

<span data-ttu-id="6a191-215">Устанавливает обратный вызов приложения объекта устройства.</span><span class="sxs-lookup"><span data-stu-id="6a191-215">Sets a device object's application callback.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-216">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-216">Prototype</span></span>

```C
UINT **nx_lwm2m_client_device_callback_set**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_DEVICE_OPERATION_CALLBACK operation_callback);
```

### <a name="description"></a><span data-ttu-id="6a191-217">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-217">Description</span></span>

<span data-ttu-id="6a191-218">Данная служба устанавливает обратный вызов приложения для реализации операций с ресурсами объекта устройства LWM2M, которые не обрабатываются клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-218">This service installs the application callback for implementing operations on the LWM2M Device Object resources that are not handled by the LWM2M Client.</span></span>

<span data-ttu-id="6a191-219">Клиент LWM2M реализует следующие ресурсы: код ошибки (11), сброс кода ошибки (12) и поддерживаемые привязки и режимы (16), операции с другими ресурсами перенаправляются в приложение.</span><span class="sxs-lookup"><span data-stu-id="6a191-219">The LWM2M Client implements the following resources: Error Code (11), Reset Error Code (12) and Supported Binding and Modes (16), operations to the other resources are redirected to the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-220">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-220">Parameters</span></span>

- <span data-ttu-id="6a191-221">**client_ptr** Указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-221">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="6a191-222">**operation_callback** Обратный вызов операции для команд «Чтение», «Обнаружение», «Запись» и «Выполнение».</span><span class="sxs-lookup"><span data-stu-id="6a191-222">**operation_callback** The operation callback for “Read”, “Discover”, “Write” and “Execute”.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-223">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-223">Return Values</span></span>

- <span data-ttu-id="6a191-224">**NX_SUCCESS** Обратный вызов операции успешно установлен.</span><span class="sxs-lookup"><span data-stu-id="6a191-224">**NX_SUCCESS** The operation callback has been successfully set.</span></span>
- <span data-ttu-id="6a191-225">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-225">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-226">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-226">Allowed From</span></span>

<span data-ttu-id="6a191-227">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-227">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-228">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-228">Example</span></span>

```c
/* Set device callback.  */
status = nx_lwm2m_client_device_callback_set(&lwm2m_client, device_operation);

/* If status is NX_SUCCESS a device callback was successfully set.  */
```

## <a name="nx_lwm2m_client_device_error_push"></a><span data-ttu-id="6a191-229">nx_lwm2m_client_device_error_push</span><span class="sxs-lookup"><span data-stu-id="6a191-229">nx_lwm2m_client_device_error_push</span></span>
<span data-ttu-id="6a191-230">Добавляет код ошибки к объекту устройства.</span><span class="sxs-lookup"><span data-stu-id="6a191-230">Adds an error code to a device object.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-231">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-231">Prototype</span></span>

```C
UINT **nx_lwm2m_client_device_error_push**(
    NX_LWM2M_CLIENT *client_ptr,
    UCHAR code);
```

### <a name="description"></a><span data-ttu-id="6a191-232">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-232">Description</span></span>

<span data-ttu-id="6a191-233">Данная служба добавляет новый экземпляр к ресурсу кода ошибки (11) объектного устройства.</span><span class="sxs-lookup"><span data-stu-id="6a191-233">This service adds a new instance to the Error Code (11) resource of the Object Device.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-234">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-234">Parameters</span></span>

- <span data-ttu-id="6a191-235">**client_ptr** Указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-235">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="6a191-236">**code** Новый код ошибки.</span><span class="sxs-lookup"><span data-stu-id="6a191-236">**code** The new error code.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-237">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-237">Return Values</span></span>

- <span data-ttu-id="6a191-238">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-238">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-239">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL**</span><span class="sxs-lookup"><span data-stu-id="6a191-239">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL**</span></span>

<span data-ttu-id="6a191-240">Достигнуто максимальное количество сохраненных</span><span class="sxs-lookup"><span data-stu-id="6a191-240">The maximum number of stored error codes has</span></span>

<span data-ttu-id="6a191-241">кодов ошибок.</span><span class="sxs-lookup"><span data-stu-id="6a191-241">been reached.</span></span>

<span data-ttu-id="6a191-242">NX_PTR_ERROR Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-242">NX_PTR_ERROR Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-243">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-243">Allowed From</span></span>

<span data-ttu-id="6a191-244">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-244">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-245">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-245">Example</span></span>

```C
/* Push device error 1 (Low battery power) to server.  */
status = nx_lwm2m_client_device_error_push(&lwm2m_client, 1);

/* If status is NX_SUCCESS a device error was successfully pushed.  */
```

## <a name="nx_lwm2m_client_device_error_reset"></a><span data-ttu-id="6a191-246">nx_lwm2m_client_device_error_reset</span><span class="sxs-lookup"><span data-stu-id="6a191-246">nx_lwm2m_client_device_error_reset</span></span>

<span data-ttu-id="6a191-247">Сбрасывает коды ошибок объекта устройства.</span><span class="sxs-lookup"><span data-stu-id="6a191-247">Resets the error codes of Device Object.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-248">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-248">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_error_reset(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="6a191-249">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-249">Description</span></span>

<span data-ttu-id="6a191-250">Данная служба удаляет все экземпляры ресурса кода ошибки из объекта устройства.</span><span class="sxs-lookup"><span data-stu-id="6a191-250">This service deletes all error code resource instances from the Device Object.</span></span> <span data-ttu-id="6a191-251">Это эквивалентно выполнению кода ошибки сброса ресурса (12).</span><span class="sxs-lookup"><span data-stu-id="6a191-251">This is equivalent to executing the resource Reset Error Code (12).</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-252">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-252">Parameters</span></span>

- <span data-ttu-id="6a191-253">**client_ptr** Указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-253">**client_ptr** Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-254">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-254">Return Values</span></span>

- <span data-ttu-id="6a191-255">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-255">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-256">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-256">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-257">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-257">Allowed From</span></span>

<span data-ttu-id="6a191-258">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-258">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-259">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-259">Example</span></span>

```c
/* Delete all device error code.  */
status = nx_lwm2m_client_device_error_reset(&lwm2m_client);

/* If status is NX_SUCCESS, reset device error successfully.  */
```

## <a name="nx_lwm2m_client_device_resource_changed"></a><span data-ttu-id="6a191-260">nx_lwm2m_client_device_resource_changed</span><span class="sxs-lookup"><span data-stu-id="6a191-260">nx_lwm2m_client_device_resource_changed</span></span>

<span data-ttu-id="6a191-261">Сообщает об изменении ресурса объекта устройства.</span><span class="sxs-lookup"><span data-stu-id="6a191-261">Signals a change to a Device Object resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-262">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-262">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_resource_changed(
    NX_LWM2M_CLIENT *client_ptr, 
    const NX_LWM2M_RESOURCE *resource);

```

### <a name="description"></a><span data-ttu-id="6a191-263">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-263">Description</span></span>

<span data-ttu-id="6a191-264">Служба используется приложением для сигнализации клиенту LWM2M об изменении ресурса объектного устройства.</span><span class="sxs-lookup"><span data-stu-id="6a191-264">The service is used by the application to signal to the LWM2M Client that a resource of the Object Device has changed.</span></span> <span data-ttu-id="6a191-265">В случае если за ресурсом наблюдает сервер LWM2M, клиент LWM2M отправит соответствующее уведомление.</span><span class="sxs-lookup"><span data-stu-id="6a191-265">The LWM2M Client will send a notification if the resource is observed by a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-266">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-266">Parameters</span></span>

- <span data-ttu-id="6a191-267">**client_ptr** Указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-267">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="6a191-268">**resource** Указатель на структуру, описывающую измененный ресурс.</span><span class="sxs-lookup"><span data-stu-id="6a191-268">**resource** Pointer to the structure describing the resource that has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-269">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-269">Return Values</span></span>

- <span data-ttu-id="6a191-270">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-270">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-271">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-271">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-272">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-272">Allowed From</span></span>

<span data-ttu-id="6a191-273">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-273">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-274">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-274">Example</span></span>

```c
/* Change device resource.  */
status = nx_lwm2m_client_device_resource_changed(&lwm2m_client, &resource);

/* If status is NX_SUCCESS, a device resource was successfully changed.  */
```

##  <a name="nx_lwm2m_client_firmware_create"></a><span data-ttu-id="6a191-275">nx_lwm2m_client_firmware_create</span><span class="sxs-lookup"><span data-stu-id="6a191-275">nx_lwm2m_client_firmware_create</span></span>

<span data-ttu-id="6a191-276">Создать объект микропрограммы клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-276">Create a LWM2M Client Firmware Object.</span></span> 

### <a name="prototype"></a><span data-ttu-id="6a191-277">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-277">Prototype</span></span>

```c
UINT nx_lwm2m_client_firmware_create(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    NX_LWM2M_CLIENT *client_ptr, 
    UINT protocols,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_CALLBACK package_callback,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_URI_CALLBACK package_uri_callback,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_URI_CALLBACK update_callback);
```

### <a name="description"></a><span data-ttu-id="6a191-278">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-278">Description</span></span>

<span data-ttu-id="6a191-279">Сервис используется приложением для создания объекта встроенного ПО.</span><span class="sxs-lookup"><span data-stu-id="6a191-279">The service is used by the application to create firmware object.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-280">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-280">Parameters</span></span>

- <span data-ttu-id="6a191-281">**firmware_ptr** Указатель на объект встроенного ПО клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-281">**firmware_ptr** Pointer to LWM2M Client Firmware object.</span></span>
- <span data-ttu-id="6a191-282">**client_ptr** Указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-282">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="6a191-283">**protocols** Поддерживаемые протоколы.</span><span class="sxs-lookup"><span data-stu-id="6a191-283">**protocols** The supported protocols.</span></span>
- <span data-ttu-id="6a191-284">**package_callback** Обратный вызов пакета.</span><span class="sxs-lookup"><span data-stu-id="6a191-284">**package_callback** The package callback.</span></span>
- <span data-ttu-id="6a191-285">**package_uri_callback** Обратный вызов универсального кода ресурса пакета.</span><span class="sxs-lookup"><span data-stu-id="6a191-285">**package_uri_callback** The package URI callback.</span></span>
- <span data-ttu-id="6a191-286">**update_callback** Обратный вызов обновления.</span><span class="sxs-lookup"><span data-stu-id="6a191-286">**update_callback** The update callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-287">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-287">Return Values</span></span>

<span data-ttu-id="6a191-288">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-288">**NX_SUCCESS** Successful operation.</span></span>
<span data-ttu-id="6a191-289">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-289">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-290">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-290">Allowed From</span></span>

<span data-ttu-id="6a191-291">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-291">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-292">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-292">Example</span></span>

```c
/* Create firmware object.  */
status = nx_lwm2m_client_firmware_create(&firmware, &lwm2m_client,     
                                         NX_LWM2M_CLIENT_FIRMWARE_PROTOCOL_HTTP, 
                                         NX_NULL, firmware_packet_uri,
                                         firmware_update);

/* If status is NX_SUCCESS, firmware object was successfully created.  */
```

##  <a name="nx_lwm2m_client_firmware_package_info_set"></a><span data-ttu-id="6a191-293">nx_lwm2m_client_firmware_package_info_set</span><span class="sxs-lookup"><span data-stu-id="6a191-293">nx_lwm2m_client_firmware_package_info_set</span></span>

<span data-ttu-id="6a191-294">Устанавливает информацию о пакете встроенного ПО клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-294">Sets the LWM2M Client Firmware package information.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-295">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-295">Prototype</span></span>

```c
UINT nx_lwm2m_client_firmware_package_info_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    const CHAR *name, 
    UINT name_length, 
    const CHAR *version, 
    UINT version_length);
```

### <a name="description"></a><span data-ttu-id="6a191-296">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-296">Description</span></span>

<span data-ttu-id="6a191-297">Служба используется приложением для настройки информационных ресурсов пакета объекта обновления встроенного ПО.</span><span class="sxs-lookup"><span data-stu-id="6a191-297">The service is used by the application to set the package information resources of the firmware update object.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-298">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-298">Parameters</span></span>

- <span data-ttu-id="6a191-299">**firmware_ptr** Указатель на объект встроенного ПО клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-299">**firmware_ptr** Pointer to LWM2M Client Firmware object.</span></span>
- <span data-ttu-id="6a191-300">**name** Имя пакета встроенного ПО.</span><span class="sxs-lookup"><span data-stu-id="6a191-300">**name** The name of firmware package.</span></span>
- <span data-ttu-id="6a191-301">**name_length** Длина имени.</span><span class="sxs-lookup"><span data-stu-id="6a191-301">**name_length** The length of name.</span></span>
- <span data-ttu-id="6a191-302">**version** Версия пакета встроенного ПО.</span><span class="sxs-lookup"><span data-stu-id="6a191-302">**version** The version of firmware package.</span></span>
- <span data-ttu-id="6a191-303">**version_length** Длина версии.</span><span class="sxs-lookup"><span data-stu-id="6a191-303">**version_length** The length of version.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-304">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-304">Return Values</span></span>

- <span data-ttu-id="6a191-305">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-305">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-306">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-306">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-307">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-307">Allowed From</span></span>

<span data-ttu-id="6a191-308">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-308">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-309">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-309">Example</span></span>

```c
/* Set the package information resources of the firmware object.  */
status = nx_lwm2m_client_firmware_package_info_set(&firmware, 2m_client,     
                                    “LWM2M Firmware”, sizeof(“LWM2M Firmware”) -1,
                                    “1.0.0.0”, sizeof(“1.0.0.0”) - 1);

/* If status is NX_SUCCESS, package information resources was successfully set. */
```

##  <a name="nx_lwm2m_client_firmware_result_set"></a><span data-ttu-id="6a191-310">nx_lwm2m_client_firmware_result_set</span><span class="sxs-lookup"><span data-stu-id="6a191-310">nx_lwm2m_client_firmware_result_set</span></span>

<span data-ttu-id="6a191-311">Задает ресурс результата обновления для объекта обновления встроенного ПО.</span><span class="sxs-lookup"><span data-stu-id="6a191-311">Sets the update result resource of the firmware update object.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-312">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-312">Prototype</span></span>

```c
UINT nx_lwm2m_client_firmware_result_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    UCHAR result);
```

### <a name="description"></a><span data-ttu-id="6a191-313">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-313">Description</span></span>

<span data-ttu-id="6a191-314">Служба используется приложением для установки ресурса результата обновления объекта обновления встроенного ПО.</span><span class="sxs-lookup"><span data-stu-id="6a191-314">The service is used by the application to set the update result resource of the firmware update object.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-315">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-315">Parameters</span></span>

- <span data-ttu-id="6a191-316">**firmware_ptr** Указатель на объект встроенного ПО клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-316">**firmware_ptr** Pointer to LWM2M Client Firmware object.</span></span>
- <span data-ttu-id="6a191-317">**result** Результат обновления.</span><span class="sxs-lookup"><span data-stu-id="6a191-317">**result** The update result.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-318">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-318">Return Values</span></span>

- <span data-ttu-id="6a191-319">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-319">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-320">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-320">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-321">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-321">Allowed From</span></span>

<span data-ttu-id="6a191-322">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-322">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-323">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-323">Example</span></span>

```c
/* Set the update result resource of the firmware object.  */
status = nx_lwm2m_client_firmware_result_set(&firmware, 
                                         NX_LWM2M_CLIENT_FIRMWARE_RESULT_SUCCESS);

/* If status is NX_SUCCESS, the update result resource was successfully set.  */
```

##  <a name="nx_lwm2m_client_firmware_state_set"></a><span data-ttu-id="6a191-324">nx_lwm2m_client_firmware_state_set</span><span class="sxs-lookup"><span data-stu-id="6a191-324">nx_lwm2m_client_firmware_state_set</span></span>

<span data-ttu-id="6a191-325">Задает ресурс результата обновления для объекта обновления встроенного ПО.</span><span class="sxs-lookup"><span data-stu-id="6a191-325">Sets the update result resource of the firmware update object.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-326">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-326">Prototype</span></span>

```c
UINT nx_lwm2m_client_firmware_state_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    UCHAR result);
```

### <a name="description"></a><span data-ttu-id="6a191-327">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-327">Description</span></span>

<span data-ttu-id="6a191-328">Сервис используется приложением для установки состояния объекта обновления встроенного ПО.</span><span class="sxs-lookup"><span data-stu-id="6a191-328">The service is used by the application to set the state of the firmware update object.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-329">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-329">Parameters</span></span>

- <span data-ttu-id="6a191-330">**firmware_ptr** Указатель на объект встроенного ПО клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-330">**firmware_ptr** Pointer to LWM2M Client Firmware object.</span></span>
- <span data-ttu-id="6a191-331">**state** Состояние объекта встроенного ПО.</span><span class="sxs-lookup"><span data-stu-id="6a191-331">**state** The state of the firmware object.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-332">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-332">Return Values</span></span>

- <span data-ttu-id="6a191-333">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-333">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-334">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-334">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-335">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-335">Allowed From</span></span>

<span data-ttu-id="6a191-336">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-336">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-337">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-337">Example</span></span>

```c
/* Set the state of the firmware object.  */
status = nx_lwm2m_client_firmware_state_set(&firmware, 
                                         NX_LWM2M_CLIENT_FIRMWARE_STATE_IDLE);

/* If status is NX_SUCCESS, the state was successfully set.  */
```

## <a name="nx_lwm2m_client_lock"></a><span data-ttu-id="6a191-338">nx_lwm2m_client_lock</span><span class="sxs-lookup"><span data-stu-id="6a191-338">nx_lwm2m_client_lock</span></span>

<span data-ttu-id="6a191-339">Блокирует клиент LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-339">Locks the LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-340">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-340">Prototype</span></span>

```c
UINT **nx_lwm2m_client_lock**(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="6a191-341">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-341">Description</span></span>

<span data-ttu-id="6a191-342">Данная служба блокирует клиент LWM2M с целью предотвратить одновременный доступ к объектам LWM2M с серверов или другого потока приложения.</span><span class="sxs-lookup"><span data-stu-id="6a191-342">This service locks the LWM2M Client to prevent concurrent access to the LWM2M objects from the servers or another application thread.</span></span>

<span data-ttu-id="6a191-343">Если клиент LWM2M на данный момент заблокирован другим потоком, функция будет заблокирована до тех пор, пока клиент LWM2M не будет разблокирован.</span><span class="sxs-lookup"><span data-stu-id="6a191-343">If the LWM2M Client is currently locked by another thread, the function will block until the LWM2M Client is unlocked.</span></span>

<span data-ttu-id="6a191-344">Вызовы к парам ***nx_lwm2m_client_lock** _/_ *_nx_lwm2m_client_unlock_** могут быть вложенными.</span><span class="sxs-lookup"><span data-stu-id="6a191-344">Calls to \***nx_lwm2m_client_lock**_/_*_nx_lwm2m_client_unlock_*\* pairs can be nested.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-345">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-345">Parameters</span></span>

- <span data-ttu-id="6a191-346">**client_ptr** Указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-346">**client_ptr** Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-347">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-347">Return Values</span></span>

- <span data-ttu-id="6a191-348">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-348">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-349">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-349">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-350">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-350">Allowed From</span></span>

<span data-ttu-id="6a191-351">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-351">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-352">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-352">Example</span></span>

```c
/* Lock the LWM2M client.  */
status = nx_lwm2m_client_lock(&lwm2m_client);

/* If status is NX_SUCCESS, lwm2m client was successfully locked.  */
```

## <a name="nx_lwm2m_client_object_add"></a><span data-ttu-id="6a191-353">nx_lwm2m_client_object_add</span><span class="sxs-lookup"><span data-stu-id="6a191-353">nx_lwm2m_client_object_add</span></span>

<span data-ttu-id="6a191-354">Добавляет реализацию объекта в клиент LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-354">Adds an Object implementation to the LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-355">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-355">Prototype</span></span>

```c
UINT **nx_lwm2m_client_object_add**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_CLIENT_OBJECT_OPERATION_CALLBACK object_operation);
```

### <a name="description"></a><span data-ttu-id="6a191-356">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-356">Description</span></span>

<span data-ttu-id="6a191-357">Данная служба добавляет новую реализацию объекта в клиент LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-357">This service adds a new Object implementation to the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-358">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-358">Parameters</span></span>

- <span data-ttu-id="6a191-359">**client_ptr** Указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-359">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="6a191-360">**object_ptr** Указатель на структуру, определяющую реализацию объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-360">**object_ptr** Pointer to the structure defining the Object implementation.</span></span>
- <span data-ttu-id="6a191-361">**object_id** Идентификатор объекта</span><span class="sxs-lookup"><span data-stu-id="6a191-361">**object_id** The object id.</span></span>
- <span data-ttu-id="6a191-362">**object_operation** Функция обратного вызова операции с объектом.</span><span class="sxs-lookup"><span data-stu-id="6a191-362">**object_operation** The object operation callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-363">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-363">Return Values</span></span>

- <span data-ttu-id="6a191-364">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-364">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-365">**NX_LWM2M_CLIENT_ALREADY_EXIST** Идентификатор объекта уже существует.</span><span class="sxs-lookup"><span data-stu-id="6a191-365">**NX_LWM2M_CLIENT_ALREADY_EXIST** The Object ID already exists.</span></span>
- <span data-ttu-id="6a191-366">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-366">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-367">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-367">Allowed From</span></span>

<span data-ttu-id="6a191-368">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-368">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-369">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-369">Example</span></span>

```c
/* Add new object to the lwm2m client.  */
status = nx_lwm2m_client_object_add(&lwm2m_client, &object, 
                                    3303, object_operation);

/* If status is NX_SUCCESS, the new object was successfully added.  */
```

## <a name="nx_lwm2m_client_object_create"></a><span data-ttu-id="6a191-370">nx_lwm2m_client_object_create</span><span class="sxs-lookup"><span data-stu-id="6a191-370">nx_lwm2m_client_object_create</span></span>

<span data-ttu-id="6a191-371">Создает новый экземпляр объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-371">Creates a new Object Instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-372">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-372">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_create(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID *instance_id_ptr,
    UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr);
```

### <a name="description"></a><span data-ttu-id="6a191-373">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-373">Description</span></span>

<span data-ttu-id="6a191-374">Данная служба выполняет операцию «Создать» над объектом клиента LWM2M для создания нового экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-374">This service performs a ‘Create’ operation on an Object of the LWM2M Client to create a new Object Instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-375">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-375">Parameters</span></span>

- <span data-ttu-id="6a191-376">**client_ptr** Указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-376">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="6a191-377">**object_id** Идентификатор объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-377">**object_id** The Object ID.</span></span>
- <span data-ttu-id="6a191-378">**instance_id_ptr** Если клиент LWM2M должен назначить идентификатор экземпляра, указатель на идентификатор нового экземпляра может иметь значение **NULL**.</span><span class="sxs-lookup"><span data-stu-id="6a191-378">**instance_id_ptr** Pointer to the ID of the new instance, can be **NULL** if the LWM2M Client must assign an Instance ID.</span></span> <span data-ttu-id="6a191-379">Если идентификатор представляет собой зарезервированное значение 65535, клиент LWM2M назначит идентификатор экземпляра.</span><span class="sxs-lookup"><span data-stu-id="6a191-379">If the ID is the reserved value 65535 the LWM2M Client will assign an Instance ID.</span></span> <span data-ttu-id="6a191-380">Если это не NULL, присвоенный идентификатор назначается повторно после вызова.</span><span class="sxs-lookup"><span data-stu-id="6a191-380">If not NULL the assigned ID is returned after the call.</span></span>
- <span data-ttu-id="6a191-381">**num_values** Количество устанавливаемых значений.</span><span class="sxs-lookup"><span data-stu-id="6a191-381">**num_values** The number of values to set.</span></span>
- <span data-ttu-id="6a191-382">**values_ptr** Указатель на массив значений ресурсов для инициализации нового экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-382">**values_ptr** Pointer to an array of resource values to initialize the new Object Instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-383">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-383">Return Values</span></span>

- <span data-ttu-id="6a191-384">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-384">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-385">**NX_LWM2M_CLIENT_ALREADY_EXIST** Идентификатор экземпляра объекта уже существует.</span><span class="sxs-lookup"><span data-stu-id="6a191-385">**NX_LWM2M_CLIENT_ALREADY_EXIST** The Object Instance ID already exists.</span></span>
- <span data-ttu-id="6a191-386">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** Объект не поддерживает функцию создания экземпляров.</span><span class="sxs-lookup"><span data-stu-id="6a191-386">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** The Object doesn’t support instance creation.</span></span>
- <span data-ttu-id="6a191-387">**NX_LWM2M_CLIENT_NO_MEMORY** Невозможно выделить память для хранения нового экземпляра.</span><span class="sxs-lookup"><span data-stu-id="6a191-387">**NX_LWM2M_CLIENT_NO_MEMORY** Cannot allocate memory to store the new instance.</span></span>
- <span data-ttu-id="6a191-388">**NX_LWM2M_CLIENT_NOT_FOUND** Идентификатор объекта не существует.</span><span class="sxs-lookup"><span data-stu-id="6a191-388">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID doesn’t exist.</span></span>
- <span data-ttu-id="6a191-389">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-389">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-390">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-390">Allowed From</span></span>

<span data-ttu-id="6a191-391">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-391">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-392">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-392">Example</span></span>

```c
/* Create new object instance.  */
status = nx_lwm2m_client_object_create(&lwm2m_client, 3303, 0, 2, &resource);

/* If status is NX_SUCCESS, a new object instance was successfully created.  */
```

## <a name="nx_lwm2m_client_object_delete"></a><span data-ttu-id="6a191-393">nx_lwm2m_client_object_delete</span><span class="sxs-lookup"><span data-stu-id="6a191-393">nx_lwm2m_client_object_delete</span></span>

<span data-ttu-id="6a191-394">Удаляет экземпляр объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-394">Deletes an Object Instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-395">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-395">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_delete(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id);
```

### <a name="description"></a><span data-ttu-id="6a191-396">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-396">Description</span></span>

<span data-ttu-id="6a191-397">Данная служба выполняет операцию «Удалить» для экземпляра объекта клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-397">This service performs a ‘Delete’ operation on an Object Instance of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-398">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-398">Parameters</span></span>

- <span data-ttu-id="6a191-399">**client_ptr** Указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-399">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="6a191-400">**object_id** Идентификатор объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-400">**object_id** The Object ID.</span></span>
- <span data-ttu-id="6a191-401">**instance_id** Идентификатор экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-401">**instance_id** The Object Instance ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-402">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-402">Return Values</span></span>

- <span data-ttu-id="6a191-403">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-403">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-404">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** Объект не поддерживает функцию удаления экземпляра.</span><span class="sxs-lookup"><span data-stu-id="6a191-404">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** The Object doesn’t support instance deletion.</span></span>
- <span data-ttu-id="6a191-405">**NX_LWM2M_CLIENT_NOT_FOUND** Идентификатор объекта или идентификатор экземпляра объекта не существует.</span><span class="sxs-lookup"><span data-stu-id="6a191-405">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID or Object Instance ID doesn’t exist.</span></span>
- <span data-ttu-id="6a191-406">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-406">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-407">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-407">Allowed From</span></span>

<span data-ttu-id="6a191-408">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-408">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-409">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-409">Example</span></span>

```c
/* Delete an object instance.  */
status = nx_lwm2m_client_object_delete(&lwm2m_client, 3303, 0);

/* If status is NX_SUCCESS, an object instance was successfully deleted.  */
```

## <a name="nx_lwm2m_client_object_discover"></a><span data-ttu-id="6a191-410">nx_lwm2m_client_object_discover</span><span class="sxs-lookup"><span data-stu-id="6a191-410">nx_lwm2m_client_object_discover</span></span>

<span data-ttu-id="6a191-411">Производит поиск ресурсов экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-411">Discovers resources of an Object Instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-412">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-412">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_discover(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT *num_resources,
    NX_LWM2M_CLIENT_RESOURCE *resources);

```

### <a name="description"></a><span data-ttu-id="6a191-413">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-413">Description</span></span>

<span data-ttu-id="6a191-414">Данная служба выполняет операцию «Найти» на экземпляре объекта клиента LWM2M, в результате чего возвращается список ресурсов, реализованных объектом.</span><span class="sxs-lookup"><span data-stu-id="6a191-414">This service performs a ‘Discover’ operation on an Object Instance of the LWM2M Client, this returns the list of resources implemented by the Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-415">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-415">Parameters</span></span>

- <span data-ttu-id="6a191-416">**client_ptr** Указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-416">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="6a191-417">**object_id** Идентификатор объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-417">**object_id** The Object ID.</span></span>
- <span data-ttu-id="6a191-418">**instance_id** Идентификатор экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-418">**instance_id** The Object Instance ID.</span></span>
- <span data-ttu-id="6a191-419">**num_resources** На входе - размер целевого буфера, на выходе - количество элементов, записанных в буфер.</span><span class="sxs-lookup"><span data-stu-id="6a191-419">**num_resources** On input the size of the destination buffer, on output the number of elements written to the buffer.</span></span>
- <span data-ttu-id="6a191-420">**resources** Указатель на целевой буфер.</span><span class="sxs-lookup"><span data-stu-id="6a191-420">**resources** Pointer to the destination buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-421">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-421">Return Values</span></span>

- <span data-ttu-id="6a191-422">*NX_SUCCESS*\* Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-422">*NX_SUCCESS*\* Successful operation.</span></span>
- <span data-ttu-id="6a191-423">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** Буфер ресурсов слишком мал для хранения списка ресурсов.</span><span class="sxs-lookup"><span data-stu-id="6a191-423">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** The resources buffer is too small to store the list of resources.</span></span>
- <span data-ttu-id="6a191-424">**NX_LWM2M_CLIENT_NOT_FOUND** Идентификатор объекта или идентификатор экземпляра объекта не существует.</span><span class="sxs-lookup"><span data-stu-id="6a191-424">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID or Object Instance ID doesn’t exist.</span></span>
- <span data-ttu-id="6a191-425">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-425">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-426">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-426">Allowed From</span></span>

<span data-ttu-id="6a191-427">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-427">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-428">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-428">Example</span></span>

```c
NX_LWM2M_CLIENT_RESOURCE resources[10]
UINT num_resources = 10;

/* Discover object resources.  */
status = nx_lwm2m_client_object_discover(&lwm2m_client, 3303, 0, 
                                         &num_resources, resource);

/* If status is NX_SUCCESS, discover object resources successfully.  */
```

## <a name="nx_lwm2m_client_object_execute"></a><span data-ttu-id="6a191-429">nx_lwm2m_client_object_execute</span><span class="sxs-lookup"><span data-stu-id="6a191-429">nx_lwm2m_client_object_execute</span></span>

<span data-ttu-id="6a191-430">Выполняет операцию «Выполнить» над ресурсом экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-430">Performs an 'Execute' operation on a resource of an Object Instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-431">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-431">Prototype</span></span>

```C
UINT **nx_lwm2m_client_object_execute**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr,
    UINT arguments_length);
```

### <a name="description"></a><span data-ttu-id="6a191-432">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-432">Description</span></span>

<span data-ttu-id="6a191-433">Данная служба выполняет операцию «Выполнить» для ресурса экземпляра объекта клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-433">This service performs the ‘Execute’ operation on an Object Instance Resource of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-434">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-434">Parameters</span></span>

- <span data-ttu-id="6a191-435">**client_ptr** Указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-435">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="6a191-436">**object_id** Идентификатор объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-436">**object_id** The Object ID.</span></span>
- <span data-ttu-id="6a191-437">**instance_id** Идентификатор экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-437">**instance_id** The Object Instance ID.</span></span>
- <span data-ttu-id="6a191-438">**resource_id** Идентификатор ресурса.</span><span class="sxs-lookup"><span data-stu-id="6a191-438">**resource_id** The Resource ID.</span></span>
- <span data-ttu-id="6a191-439">**arguments_ptr** Указатель на аргументы операции выполнения.</span><span class="sxs-lookup"><span data-stu-id="6a191-439">**arguments_ptr** Pointer to the arguments of the execute operation.</span></span> <span data-ttu-id="6a191-440">Может быть NULL, если значение arguments_length равно нулю.</span><span class="sxs-lookup"><span data-stu-id="6a191-440">Can be NULL if arguments_length is zero.</span></span>
- <span data-ttu-id="6a191-441">**arguments_length** The length of the arguments.</span><span class="sxs-lookup"><span data-stu-id="6a191-441">**arguments_length** The length of the arguments.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-442">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-442">Return Values</span></span>

- <span data-ttu-id="6a191-443">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-443">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-444">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** Буфер ресурсов слишком мал для хранения списка ресурсов.</span><span class="sxs-lookup"><span data-stu-id="6a191-444">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** The resources buffer is too small to store the list of resources.</span></span>
- <span data-ttu-id="6a191-445">**NX_LWM2M_CLIENT_NOT_FOUND** Идентификатор объекта или идентификатор экземпляра объекта не существует.</span><span class="sxs-lookup"><span data-stu-id="6a191-445">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID or Object Instance ID doesn’t exist.</span></span>
- <span data-ttu-id="6a191-446">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-446">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-447">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-447">Allowed From</span></span>

<span data-ttu-id="6a191-448">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-448">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-449">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-449">Example</span></span>

```c
/* Execute object resource.  */
status = nx_lwm2m_client_object_execute (&lwm2m_client, 3303, 0, 0,  
                                         “5”, 1);

/* If status is NX_SUCCESS, an object resource was successfully executed.  */
```

## <a name="nx_lwm2m_client_object_instance_add"></a><span data-ttu-id="6a191-450">nx_lwm2m_client_object_instance_add</span><span class="sxs-lookup"><span data-stu-id="6a191-450">nx_lwm2m_client_object_instance_add</span></span>

<span data-ttu-id="6a191-451">Добавляет реализацию экземпляра объекта к объекту.</span><span class="sxs-lookup"><span data-stu-id="6a191-451">Adds an Object instance implementation to an object.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-452">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-452">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_instance_add(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr,
    NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a><span data-ttu-id="6a191-453">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-453">Description</span></span>

<span data-ttu-id="6a191-454">Данная служба добавляет новую реализацию экземпляра объекта в клиент LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-454">This service adds a new Object instance implementation to the LWM2M Client.</span></span> <span data-ttu-id="6a191-455">Если значение instance_id_ptr равно **NX_LWM2M_CLIENT_RESERVED_ID**, клиент LWM2M автоматически назначит неиспользуемый идентификатор экземпляра, в противном случае клиент LWM2M будет использовать значение, установленное приложением.</span><span class="sxs-lookup"><span data-stu-id="6a191-455">If the value of instance_id_ptr is **NX_LWM2M_CLIENT_RESERVED_ID**, LWM2M Client will automatically assign an unused instance id, otherwise, LWM2M Client will use the value application set.</span></span> <span data-ttu-id="6a191-456">После успешного добавления нового экземпляра для возврата в приложение значение instance_id будет заполнено instance_id_ptr.</span><span class="sxs-lookup"><span data-stu-id="6a191-456">Once new instance was added successfully, the instance_id will be filled in instance_id_ptr to return to application.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-457">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-457">Parameters</span></span>

- <span data-ttu-id="6a191-458">**object_ptr** Указатель на структуру, определяющую реализацию объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-458">**object_ptr** Pointer to the structure defining the Object implementation.</span></span>
- <span data-ttu-id="6a191-459">**instance_ptr** Указатель на структуру, определяющую реализацию экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-459">**instance_ptr** Pointer to the structure defining the Object instance implementation.</span></span>
- <span data-ttu-id="6a191-460">**instance_id_ptr** Указатель на идентификатор экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-460">**instance_id_ptr** Pointer to the object instance id.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-461">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-461">Return Values</span></span>

- <span data-ttu-id="6a191-462">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-462">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-463">**NX_CLIENT_LWM2M_ALREADY_EXIST** Идентификатор объекта уже существует.</span><span class="sxs-lookup"><span data-stu-id="6a191-463">**NX_CLIENT_LWM2M_ALREADY_EXIST** The Object ID already exists.</span></span>
- <span data-ttu-id="6a191-464">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-464">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-465">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-465">Allowed From</span></span>

<span data-ttu-id="6a191-466">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-466">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-467">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-467">Example</span></span>

```c
/* Add new object instance to the object.  */
status = nx_lwm2m_client_object_instance_add(&object, &object_instance,
                                             &instance_id);

/* If status is NX_SUCCESS, the new object instance was successfully added.  */
```

## <a name="nx_lwm2m_client_object_instance_next_get"></a><span data-ttu-id="6a191-468">nx_lwm2m_client_object_instance_next_get</span><span class="sxs-lookup"><span data-stu-id="6a191-468">nx_lwm2m_client_object_instance_next_get</span></span>

<span data-ttu-id="6a191-469">Получает следующий экземпляр объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-469">Gets the next instance of an Object.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-470">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-470">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_instance_next_get(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a><span data-ttu-id="6a191-471">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-471">Description</span></span>

<span data-ttu-id="6a191-472">Данная служба возвращает идентификатор следующего экземпляра данного объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-472">This service returns the ID of the next Object Instance of the given Object.</span></span> <span data-ttu-id="6a191-473">Если текущий идентификатор экземпляра установлен на NX_LWM2M_RESERVED_ID (65535), возвращается идентификатор первого экземпляра.</span><span class="sxs-lookup"><span data-stu-id="6a191-473">If the current Instance ID is set to NX_LWM2M_RESERVED_ID (65535) the ID of the first instance is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-474">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-474">Parameters</span></span>

- <span data-ttu-id="6a191-475">**client_ptr** Указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-475">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="6a191-476">**object_id** Идентификатор объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-476">**object_id** The Object ID.</span></span>
- <span data-ttu-id="6a191-477">**instance_id_ptr** Указатель на текущий идентификатор экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-477">**instance_id_ptr** Pointer to the current Object Instance ID.</span></span> <span data-ttu-id="6a191-478">При возврате содержит идентификатор следующего экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-478">On return contains the next Instance ID of the Object.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-479">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-479">Return Values</span></span>

- <span data-ttu-id="6a191-480">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-480">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-481">**NX_CLIENT_LWM2M_NOT_FOUND** Данный идентификатор экземпляра является последним из объекта, или идентификатор объекта не реализован.</span><span class="sxs-lookup"><span data-stu-id="6a191-481">**NX_CLIENT_LWM2M_NOT_FOUND** The given Instance ID is the last of the object, or the Object ID is not implemented.</span></span>
- <span data-ttu-id="6a191-482">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-482">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-483">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-483">Allowed From</span></span>

<span data-ttu-id="6a191-484">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-484">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-485">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-485">Example</span></span>

```c
/* Get the next instance of an object.  */
status = nx_lwm2m_client_object_instance_next_get(&lwm2m_client, 3303, 
                                                  &instance_id);

/* If status is NX_SUCCESS, get the next instance successfully.  */
```

## <a name="nx_lwm2m_client_object_instance_remove"></a><span data-ttu-id="6a191-486">nx_lwm2m_client_object_instance_remove</span><span class="sxs-lookup"><span data-stu-id="6a191-486">nx_lwm2m_client_object_instance_remove</span></span>

<span data-ttu-id="6a191-487">Удаляет реализацию экземпляра объекта из объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-487">Removes an  Object instance implementation from an object.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-488">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-488">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_instance_remove(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr);
```

### <a name="description"></a><span data-ttu-id="6a191-489">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-489">Description</span></span>

<span data-ttu-id="6a191-490">Данная служба удаляет экземпляр объекта из объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-490">This service removes an Object instance from an object.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-491">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-491">Parameters</span></span>

- <span data-ttu-id="6a191-492">***object_ptr*** Указатель на структуру, определяющую реализацию объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-492">***object_ptr*** Pointer to the structure defining the Object implementation.</span></span>
- <span data-ttu-id="6a191-493">**instance_ptr** Указатель на структуру, определяющую реализацию экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-493">**instance_ptr** Pointer to the structure defining the Object instance implementation.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-494">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-494">Return Values</span></span>

- <span data-ttu-id="6a191-495">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-495">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-496">**NX_LWM2M_CLIENT_ALREADY_EXIST** Идентификатор объекта уже существует.</span><span class="sxs-lookup"><span data-stu-id="6a191-496">**NX_LWM2M_CLIENT_ALREADY_EXIST** The Object ID already exists.</span></span>
- <span data-ttu-id="6a191-497">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-497">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-498">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-498">Allowed From</span></span>

<span data-ttu-id="6a191-499">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-499">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-500">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-500">Example</span></span>

```c
/* Remove object instance from an object.  */
status = nx_lwm2m_client_object_instance_remove(&object, &object_instance);

/* If status is NX_SUCCESS, the object instance was successfully removed.  */
```

## <a name="nx_lwm2m_client_object_next_get"></a><span data-ttu-id="6a191-501">nx_lwm2m_client_object_next_get</span><span class="sxs-lookup"><span data-stu-id="6a191-501">nx_lwm2m_client_object_next_get</span></span>

<span data-ttu-id="6a191-502">Получает следующий объект клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-502">Gets the next object of the LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-503">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-503">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_next_get(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID \*object_id_ptr);
```

### <a name="description"></a><span data-ttu-id="6a191-504">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-504">Description</span></span>

<span data-ttu-id="6a191-505">Данная служба возвращает идентификатор следующего объекта, реализованного клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-505">This service returns the ID of the next Object implemented by the LWM2M Client.</span></span> <span data-ttu-id="6a191-506">Если текущий идентификатор объекта установлен на NX_LWM2M_RESERVED_ID (65535), возвращается первый идентификатор объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-506">If the current Object ID is set to NX_LWM2M_RESERVED_ID (65535) the first Object ID is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-507">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-507">Parameters</span></span>

- <span data-ttu-id="6a191-508">**client_ptr** Указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-508">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="6a191-509">**object_id_ptr** Указатель на текущий идентификатор объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-509">**object_id_ptr** Pointer to the current Object ID.</span></span> <span data-ttu-id="6a191-510">При возврате содержит следующий идентификатор объекта, реализованный клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-510">On return contains the next Object ID implemented by the LWM2M Client.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-511">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-511">Return Values</span></span>

- <span data-ttu-id="6a191-512">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-512">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-513">**NX_LWM2M_CLIENT_NOT_FOUND** Данный идентификатор объекта является последним в базе данных.</span><span class="sxs-lookup"><span data-stu-id="6a191-513">**NX_LWM2M_CLIENT_NOT_FOUND** The given Object ID is the last of the database.</span></span>
<span data-ttu-id="6a191-514">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-514">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-515">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-515">Allowed From</span></span>

<span data-ttu-id="6a191-516">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-516">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-517">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-517">Example</span></span>

```c
/* Get the next object of lwm2m client.  */
status = nx_lwm2m_client_object_next_get(&lwm2m_client, &object_id);

/* If status is NX_SUCCESS, get the next object successfully.  */
```

## <a name="nx_lwm2m_client_object_read"></a><span data-ttu-id="6a191-518">nx_lwm2m_client_object_read</span><span class="sxs-lookup"><span data-stu-id="6a191-518">nx_lwm2m_client_object_read</span></span>

<span data-ttu-id="6a191-519">Считывает значения ресурса экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-519">Reads an Object Instance's resource's values.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-520">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-520">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_read(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT num_values,
    NX_LWM2M_RESOURCE *values);
```

### <a name="description"></a><span data-ttu-id="6a191-521">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-521">Description</span></span>

<span data-ttu-id="6a191-522">Эта служба выполняет операцию «Сосчитать» на экземпляре объекта клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-522">This service performs a ‘Read’ operation on an Object Instance of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-523">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-523">Parameters</span></span>

- <span data-ttu-id="6a191-524">**client_ptr** Указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-524">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="6a191-525">**object_id** Идентификатор объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-525">**object_id** The Object ID.</span></span>
- <span data-ttu-id="6a191-526">**instance_id** Идентификатор экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-526">**instance_id** The Object Instance ID.</span></span>
- <span data-ttu-id="6a191-527">**num_values** Количество ресурсов для считывания.</span><span class="sxs-lookup"><span data-stu-id="6a191-527">**num_values** The number of resources to read.</span></span>
- <span data-ttu-id="6a191-528">**values_ptr** Указатель на массив NX_LWM2M_RESOURCE, содержащий идентификаторы считываемых ресурсов</span><span class="sxs-lookup"><span data-stu-id="6a191-528">**values_ptr** Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources to read.</span></span> <span data-ttu-id="6a191-529">По возвращении массив заполняется соответствующими типами и значениями.</span><span class="sxs-lookup"><span data-stu-id="6a191-529">On return the array is filled with the corresponding types and values.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-530">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-530">Return Values</span></span>

- <span data-ttu-id="6a191-531">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-531">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-532">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** Ресурс не поддерживает операцию считывания.</span><span class="sxs-lookup"><span data-stu-id="6a191-532">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** A resource doesn’t support the read operation.</span></span>
- <span data-ttu-id="6a191-533">**NX_LWM2M_CLIENT_NOT_FOUND** Идентификатор объекта, идентификатор экземпляра объекта или идентификатор ресурса не существует.</span><span class="sxs-lookup"><span data-stu-id="6a191-533">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID, Object Instance ID or a resource ID doesn’t exist.</span></span>
- <span data-ttu-id="6a191-534">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-534">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-535">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-535">Allowed From</span></span>

<span data-ttu-id="6a191-536">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-536">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-537">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-537">Example</span></span>

```c
/* Read the object resources.  */
status = nx_lwm2m_client_object_read(&lwm2m_client, 3303, 0, 2, &resource);

/* If status is NX_SUCCESS, the resources were successfully read.  */
```

## <a name="nx_lwm2m_client_object_remove"></a><span data-ttu-id="6a191-538">nx_lwm2m_client_object_remove</span><span class="sxs-lookup"><span data-stu-id="6a191-538">nx_lwm2m_client_object_remove</span></span>

<span data-ttu-id="6a191-539">Удаляет реализацию экземпляра объекта из объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-539">Removes an Object instance implementation from an object.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-540">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-540">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_remove(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_OBJECT *object_ptr);
```

### <a name="description"></a><span data-ttu-id="6a191-541">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-541">Description</span></span>

<span data-ttu-id="6a191-542">Данная служба удаляет объект из клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-542">This service removes an Object from the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-543">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-543">Parameters</span></span>

- <span data-ttu-id="6a191-544">**client_ptr** Указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-544">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="6a191-545">**object_ptr** Указатель на структуру, определяющую реализацию объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-545">**object_ptr** Pointer to the structure defining the Object implementation.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-546">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-546">Return Values</span></span>

- <span data-ttu-id="6a191-547">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-547">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-548">**NX_LWM2M_CLIENT_ALREADY_EXIST** Идентификатор объекта уже существует.</span><span class="sxs-lookup"><span data-stu-id="6a191-548">**NX_LWM2M_CLIENT_ALREADY_EXIST** The Object ID already exists.</span></span>
- <span data-ttu-id="6a191-549">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-549">**NX_PTR_ERROR** Invalid pointer.</span></span>
- <span data-ttu-id="6a191-550">**NX_LWM2M_CLIENT_FORBIDDEN** Удаление внутреннего объекта недопустимо.</span><span class="sxs-lookup"><span data-stu-id="6a191-550">**NX_LWM2M_CLIENT_FORBIDDEN** Removing internal object is forbidden.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-551">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-551">Allowed From</span></span>

<span data-ttu-id="6a191-552">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-552">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-553">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-553">Example</span></span>

```c
/* Remove object from lwm2m client.  */
status = nx_lwm2m_client_object_remove(&lwm2m_client, &object);

/* If status is NX_SUCCESS, the object was successfully removed.  */
```

## <a name="nx_lwm2m_client_object_resource_changed"></a><span data-ttu-id="6a191-554">nx_lwm2m_client_object_resource_changed</span><span class="sxs-lookup"><span data-stu-id="6a191-554">nx_lwm2m_client_object_resource_changed</span></span>

<span data-ttu-id="6a191-555">Сигнализирует об изменении ресурса объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-555">Signals a change of an Object resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-556">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-556">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_resource_changed(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr,
    const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a><span data-ttu-id="6a191-557">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-557">Description</span></span>

<span data-ttu-id="6a191-558">Служба используется приложением, чтобы сигнализировать клиенту LWM2M об изменении ресурса объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-558">The service is used by the application to signal to the LWM2M Client that a resource of the Object has changed.</span></span> <span data-ttu-id="6a191-559">В случае если за ресурсом наблюдает сервер LWM2M, клиент LWM2M отправит соответствующее уведомление.</span><span class="sxs-lookup"><span data-stu-id="6a191-559">The LWM2M Client will send a notification if the resource is observed by a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-560">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-560">Parameters</span></span>

- <span data-ttu-id="6a191-561">**object_ptr** Указатель на структуру, определяющую реализацию объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-561">**object_ptr** Pointer to the structure defining the Object implementation.</span></span>
- <span data-ttu-id="6a191-562">***instance_ptr*** Указатель на структуру, определяющую реализацию экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-562">***instance_ptr*** Pointer to the structure defining the Object instance implementation.</span></span>
- <span data-ttu-id="6a191-563">**resource** Указатель на структуру, описывающую измененный ресурс.</span><span class="sxs-lookup"><span data-stu-id="6a191-563">**resource** Pointer to the structure describing the resource that has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-564">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-564">Return Values</span></span>

- <span data-ttu-id="6a191-565">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-565">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-566">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-566">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-567">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-567">Allowed From</span></span>

<span data-ttu-id="6a191-568">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-568">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-569">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-569">Example</span></span>

```c
/* Change object resource.  */
status = nx_lwm2m_client_object_resource_changed(&object, &instance, &resource);

/* If status is NX_SUCCESS, a resource was successfully changed.  */
```

## <a name="nx_lwm2m_client_object_write"></a><span data-ttu-id="6a191-570">nx_lwm2m_client_object_write</span><span class="sxs-lookup"><span data-stu-id="6a191-570">nx_lwm2m_client_object_write</span></span>

<span data-ttu-id="6a191-571">Изменяет значения ресурса экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-571">Changes resource's values of an Object instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-572">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-572">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_write(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr,
    UINT write_op);
```

### <a name="description"></a><span data-ttu-id="6a191-573">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-573">Description</span></span>

<span data-ttu-id="6a191-574">Данная служба выполняет операцию «Запись» для экземпляра объекта клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-574">This service performs a ‘Write’ operation on an Object Instance of the LWM2M Client.</span></span>

<span data-ttu-id="6a191-575">Для параметра *write_op* можно указать следующие операции записи.</span><span class="sxs-lookup"><span data-stu-id="6a191-575">The following write operations can be specified to the *write_op* parameter.</span></span>

| <span data-ttu-id="6a191-576">Значение</span><span class="sxs-lookup"><span data-stu-id="6a191-576">Value</span></span> | <span data-ttu-id="6a191-577">Операция&nbsp;записи</span><span class="sxs-lookup"><span data-stu-id="6a191-577">Write&nbsp;Operation</span></span> | <span data-ttu-id="6a191-578">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-578">Description</span></span> |
| --- | ---| --- |
| <span data-ttu-id="6a191-579">0</span><span class="sxs-lookup"><span data-stu-id="6a191-579">0</span></span> | <span data-ttu-id="6a191-580">Частичное обновление</span><span class="sxs-lookup"><span data-stu-id="6a191-580">Partial Update</span></span> | <span data-ttu-id="6a191-581">Добавляет или обновляет Ресурсы, представленные в новом значении, и оставляет другие существующие Ресурсы без изменений.</span><span class="sxs-lookup"><span data-stu-id="6a191-581">Adds or updates Resources provided in the new value and leaves other existing Resources unchanged.</span></span> |
| <span data-ttu-id="6a191-582">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE**</span><span class="sxs-lookup"><span data-stu-id="6a191-582">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE**</span></span> | <span data-ttu-id="6a191-583">Заменить экземпляр</span><span class="sxs-lookup"><span data-stu-id="6a191-583">Replace Instance</span></span> | <span data-ttu-id="6a191-584">Заменяет экземпляр объекта новыми предоставленными значениями ресурсов.</span><span class="sxs-lookup"><span data-stu-id="6a191-584">Replaces the Object Instance with the new provided resource values.</span></span> |
| <span data-ttu-id="6a191-585">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE**</span><span class="sxs-lookup"><span data-stu-id="6a191-585">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE**</span></span> | <span data-ttu-id="6a191-586">Заменить ресурс</span><span class="sxs-lookup"><span data-stu-id="6a191-586">Replace Resource</span></span> | <span data-ttu-id="6a191-587">Заменяет ресурсы новыми предоставленными значениями ресурсов (используется для замены нескольких ресурсов).</span><span class="sxs-lookup"><span data-stu-id="6a191-587">Replaces the Resources with the new provided resource values (used to replace Multiple Resources).</span></span> |
| <span data-ttu-id="6a191-588">**NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP**</span><span class="sxs-lookup"><span data-stu-id="6a191-588">**NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP**</span></span> | <span data-ttu-id="6a191-589">Запись при начальной загрузке</span><span class="sxs-lookup"><span data-stu-id="6a191-589">Bootstrap Write</span></span> | <span data-ttu-id="6a191-590">Обозначает вызов из последовательности начальной загрузки.</span><span class="sxs-lookup"><span data-stu-id="6a191-590">Indicates a call from a Bootstrap sequence.</span></span> |

### <a name="parameters"></a><span data-ttu-id="6a191-591">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-591">Parameters</span></span>

- <span data-ttu-id="6a191-592">**client_ptr** Указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-592">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="6a191-593">**object_id** Идентификатор объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-593">**object_id** The Object ID.</span></span>
- <span data-ttu-id="6a191-594">**instance_id** Идентификатор экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-594">**instance_id** The Object Instance ID.</span></span>
- <span data-ttu-id="6a191-595">**num_values** Количество записываемых ресурсов.</span><span class="sxs-lookup"><span data-stu-id="6a191-595">**num_values** The number of resources to write.</span></span>
- <span data-ttu-id="6a191-596">**values_ptr** Указатель на массив NX_LWM2M_RESOURCE, содержащий идентификаторы ресурсов, типы и значения для записи.</span><span class="sxs-lookup"><span data-stu-id="6a191-596">**values_ptr** Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources, the types and the values to write.</span></span>
- <span data-ttu-id="6a191-597">**write_op** Тип операции записи.</span><span class="sxs-lookup"><span data-stu-id="6a191-597">**write_op** The type of write operation.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-598">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-598">Return Values</span></span>

- <span data-ttu-id="6a191-599">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-599">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-600">**NX_LWM2M_CLIENT_BAD_ENCODING** Тип ресурса недействителен.</span><span class="sxs-lookup"><span data-stu-id="6a191-600">**NX_LWM2M_CLIENT_BAD_ENCODING** The type of a resource is not valid.</span></span>
- <span data-ttu-id="6a191-601">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** Длина значения слишком велика для сохранения в экземпляре.</span><span class="sxs-lookup"><span data-stu-id="6a191-601">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** The length of a value is too big to be stored in the instance.</span></span>
- <span data-ttu-id="6a191-602">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** Ресурс не поддерживает функцию операции записи.</span><span class="sxs-lookup"><span data-stu-id="6a191-602">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** A resource doesn’t support the write operation.</span></span>
- <span data-ttu-id="6a191-603">**NX_LWM2M_CLIENT_NO_MEMORY** Невозможно выделить память для хранения значения ресурса.</span><span class="sxs-lookup"><span data-stu-id="6a191-603">**NX_LWM2M_CLIENT_NO_MEMORY** Cannot allocate memory to store a resource value.</span></span>
- <span data-ttu-id="6a191-604">**NX_LWM2M_CLIENT_NOT_ACCEPTABLE** Значение ресурса недействительно.</span><span class="sxs-lookup"><span data-stu-id="6a191-604">**NX_LWM2M_CLIENT_NOT_ACCEPTABLE** The value of a resource is not valid.</span></span>
- <span data-ttu-id="6a191-605">**NX_LWM2M_CLIENT_NOT_FOUND** Идентификатор объекта, идентификатор экземпляра объекта или идентификатор ресурса не существует.</span><span class="sxs-lookup"><span data-stu-id="6a191-605">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID, Object Instance ID or a resource ID doesn’t exist.</span></span>
- <span data-ttu-id="6a191-606">**NX_OPTION_ERROR** Неверный тип операции записи.</span><span class="sxs-lookup"><span data-stu-id="6a191-606">**NX_OPTION_ERROR** Invalid type of write operation.</span></span> 
- <span data-ttu-id="6a191-607">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-607">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-608">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-608">Allowed From</span></span>

<span data-ttu-id="6a191-609">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-609">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-610">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-610">Example</span></span>

```c
/* Write object resources.  */
status = nx_lwm2m_client_object_write(&lwm2m_client, 3303, 0, 2, &resource,
                                      NX_LWM2M_CLIENT_OBJECT_WRITE_UPDATE);

/* If status is NX_SUCCESS, write object resources successfully.  */
```

## <a name="nx_lwm2m_client_resource_boolean_get"></a><span data-ttu-id="6a191-611">nx_lwm2m_client_resource_boolean_get</span><span class="sxs-lookup"><span data-stu-id="6a191-611">nx_lwm2m_client_resource_boolean_get</span></span>

<span data-ttu-id="6a191-612">Получает значение логического ресурса.</span><span class="sxs-lookup"><span data-stu-id="6a191-612">Gets the value of a Boolean Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-613">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-613">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_boolean_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a><span data-ttu-id="6a191-614">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-614">Description</span></span>

<span data-ttu-id="6a191-615">Служба извлекает значение логического ресурса.</span><span class="sxs-lookup"><span data-stu-id="6a191-615">The service retrieves the value of a Boolean Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-616">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-616">Parameters</span></span>

- <span data-ttu-id="6a191-617">**resource** Указатель на описание значения ресурса.</span><span class="sxs-lookup"><span data-stu-id="6a191-617">**resource** Pointer to Resource value description.</span></span>
- <span data-ttu-id="6a191-618">**bool_ptr** Указатель на целевое логическое значение.</span><span class="sxs-lookup"><span data-stu-id="6a191-618">**bool_ptr** Pointer to the destination Boolean value.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-619">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-619">Return Values</span></span>

- <span data-ttu-id="6a191-620">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-620">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-621">**NX_LWM2M_CLIENT_BAD_ENCODING** Значение ресурса не является логическим значением.</span><span class="sxs-lookup"><span data-stu-id="6a191-621">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a Boolean value.</span></span>
- <span data-ttu-id="6a191-622">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-622">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-623">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-623">Allowed From</span></span>

<span data-ttu-id="6a191-624">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-624">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-625">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-625">Example</span></span>

```c
/* Get the value of a Boolean resource.  */
status = nx_lwm2m_client_resource_boolean_get(&resource, &bool);

/* If status is NX_SUCCESS, the value of Boolean resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_boolean_set"></a><span data-ttu-id="6a191-626">nx_lwm2m_client_resource_boolean_set</span><span class="sxs-lookup"><span data-stu-id="6a191-626">nx_lwm2m_client_resource_boolean_set</span></span>

<span data-ttu-id="6a191-627">Устанавливает значение логического ресурса.</span><span class="sxs-lookup"><span data-stu-id="6a191-627">Sets the value of a Boolean Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-628">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-628">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_boolean_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_BOOL bool_data);
```

### <a name="description"></a><span data-ttu-id="6a191-629">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-629">Description</span></span>

<span data-ttu-id="6a191-630">Служба устанавливает значение логического ресурса.</span><span class="sxs-lookup"><span data-stu-id="6a191-630">The service sets the value of a Boolean Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-631">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-631">Parameters</span></span>

- <span data-ttu-id="6a191-632">**resource** Указатель на ресурс.</span><span class="sxs-lookup"><span data-stu-id="6a191-632">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="6a191-633">**bool_data** Логические данные.</span><span class="sxs-lookup"><span data-stu-id="6a191-633">**bool_data** Boolean data.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-634">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-634">Return Values</span></span>

- <span data-ttu-id="6a191-635">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-635">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-636">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-636">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-637">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-637">Allowed From</span></span>

<span data-ttu-id="6a191-638">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-638">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-639">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-639">Example</span></span>

```c
/* Set the value of a Boolean resource.  */
status = nx_lwm2m_client_resource_boolean_set(&resource, NX_TRUE);

/* If status is NX_SUCCESS, the value of Boolean resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_dim_get"></a><span data-ttu-id="6a191-640">nx_lwm2m_client_resource_dim_get</span><span class="sxs-lookup"><span data-stu-id="6a191-640">nx_lwm2m_client_resource_dim_get</span></span>

<span data-ttu-id="6a191-641">Получает измерение ресурса для нескольких ресурсов</span><span class="sxs-lookup"><span data-stu-id="6a191-641">Gets the resource dimension for multiple Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-642">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-642">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_dim_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    UCHAR *dim);
```

### <a name="description"></a><span data-ttu-id="6a191-643">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-643">Description</span></span>

<span data-ttu-id="6a191-644">Служба извлекает измерение ресурса для нескольких ресурсов.</span><span class="sxs-lookup"><span data-stu-id="6a191-644">The service retrieves the resource dimension for multiple resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-645">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-645">Parameters</span></span>

- <span data-ttu-id="6a191-646">**resource** Указатель на ресурс.</span><span class="sxs-lookup"><span data-stu-id="6a191-646">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="6a191-647">**dim** Указатель на размер назначения.</span><span class="sxs-lookup"><span data-stu-id="6a191-647">**dim** Pointer to the destination dimension.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-648">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-648">Return Values</span></span>

- <span data-ttu-id="6a191-649">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-649">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-650">**NX_LWM2M_CLIENT_BAD_ENCODING** Значение ресурса не является логическим значением.</span><span class="sxs-lookup"><span data-stu-id="6a191-650">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a Boolean value.</span></span>
- <span data-ttu-id="6a191-651">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-651">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-652">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-652">Allowed From</span></span>

<span data-ttu-id="6a191-653">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-653">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-654">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-654">Example</span></span>

```c
/* Get the resource dimension for multiple resource.  */
status = nx_lwm2m_client_resource_dim_get(&resource, &dim);

/* If status is NX_SUCCESS, the resource dimension was successfully get. */
```

## <a name="nx_lwm2m_client_resource_dim_set"></a><span data-ttu-id="6a191-655">nx_lwm2m_client_resource_dim_set</span><span class="sxs-lookup"><span data-stu-id="6a191-655">nx_lwm2m_client_resource_dim_set</span></span>

<span data-ttu-id="6a191-656">Устанавливает измерение ресурса для нескольких ресурсов.</span><span class="sxs-lookup"><span data-stu-id="6a191-656">Sets the resource dimension for multiple resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-657">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-657">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_dim_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    CHAR dim);
```

### <a name="description"></a><span data-ttu-id="6a191-658">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-658">Description</span></span>

<span data-ttu-id="6a191-659">Служба устанавливает измерение ресурса для нескольких ресурсов.</span><span class="sxs-lookup"><span data-stu-id="6a191-659">The service sets the resource dimension for multiple resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-660">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-660">Parameters</span></span>

- <span data-ttu-id="6a191-661">**value** Указатель на описание значения ресурса.</span><span class="sxs-lookup"><span data-stu-id="6a191-661">**value** Pointer to Resource value description.</span></span>
- <span data-ttu-id="6a191-662">**dim** Значение измерения.</span><span class="sxs-lookup"><span data-stu-id="6a191-662">**dim** Dimension value.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-663">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-663">Return Values</span></span>

- <span data-ttu-id="6a191-664">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-664">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-665">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-665">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-666">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-666">Allowed From</span></span>

<span data-ttu-id="6a191-667">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-667">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-668">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-668">Example</span></span>

```c
/* Set the resource dimension.  */
status = nx_lwm2m_client_resource_dim_set(&resource, 3);

/* If status is NX_SUCCESS, the resource dimension was successfully set. */
```

## <a name="nx_lwm2m_client_resource_float32_get"></a><span data-ttu-id="6a191-669">nx_lwm2m_client_resource_float32_get</span><span class="sxs-lookup"><span data-stu-id="6a191-669">nx_lwm2m_client_resource_float32_get</span></span>

<span data-ttu-id="6a191-670">Получает значение 32-битного ресурса **с плавающей точкой**.</span><span class="sxs-lookup"><span data-stu-id="6a191-670">Gets the value of a 32-Bit **float** Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-671">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-671">Prototype</span></span>

```C
UINT nx_lwm2m_client_resource_float32_get(
    NX_LWM2M_CLIENT_RESOURCE *resource,
    NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a><span data-ttu-id="6a191-672">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-672">Description</span></span>

<span data-ttu-id="6a191-673">Служба извлекает значение 32-битного ресурса **с плавающей точкой**.</span><span class="sxs-lookup"><span data-stu-id="6a191-673">The service retrieves the value of a 32-Bit **float** Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-674">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-674">Parameters</span></span>

- <span data-ttu-id="6a191-675">**resource** Указатель на ресурс.</span><span class="sxs-lookup"><span data-stu-id="6a191-675">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="6a191-676">**float32_ptr** Указатель на целевое 32-битное **значение с плавающей точкой**.</span><span class="sxs-lookup"><span data-stu-id="6a191-676">**float32_ptr** Pointer to the destination 32-Bit **float** value.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-677">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-677">Return Values</span></span>

- <span data-ttu-id="6a191-678">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-678">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-679">**NX_LWM2M_CLIENT_BAD_ENCODING** Значение ресурса не является логическим значением.</span><span class="sxs-lookup"><span data-stu-id="6a191-679">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a Boolean value.</span></span>
- <span data-ttu-id="6a191-680">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-680">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-681">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-681">Allowed From</span></span>

<span data-ttu-id="6a191-682">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-682">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-683">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-683">Example</span></span>

```C
/* Get the value of a 32-Bit float resource.  */
status = nx_lwm2m_client_resource_float32_get(&resource, &float32);

/* If status is NX_SUCCESS, the value of 32-Bit float resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_float32_set"></a><span data-ttu-id="6a191-684">nx_lwm2m_client_resource_float32_set</span><span class="sxs-lookup"><span data-stu-id="6a191-684">nx_lwm2m_client_resource_float32_set</span></span>

<span data-ttu-id="6a191-685">Устанавливает значение 32-битного ресурса **с плавающей точкой**.</span><span class="sxs-lookup"><span data-stu-id="6a191-685">Sets the value of a 32-Bit **float** Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-686">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-686">Prototype</span></span>

```C
UINT nx_lwm2m_client_resource_float32_set(
    NX_LWM2M_CLIENT_RESOURCE *resource,
    NX_LWM2M_FLOAT32 float32_data);
```

### <a name="description"></a><span data-ttu-id="6a191-687">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-687">Description</span></span>

<span data-ttu-id="6a191-688">Служба устанавливает значение 32-битного ресурса **с плавающей точкой**.</span><span class="sxs-lookup"><span data-stu-id="6a191-688">The service sets the value of a 32-Bit **float** Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-689">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-689">Parameters</span></span>

- <span data-ttu-id="6a191-690">**resource** Указатель на ресурс.</span><span class="sxs-lookup"><span data-stu-id="6a191-690">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="6a191-691">**float32_data** 32-битные **данные с плавающей точкой**.</span><span class="sxs-lookup"><span data-stu-id="6a191-691">**float32_data** 32-Bit **float** data.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-692">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-692">Return Values</span></span>

- <span data-ttu-id="6a191-693">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-693">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-694">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-694">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-695">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-695">Allowed From</span></span>

<span data-ttu-id="6a191-696">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-696">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-697">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-697">Example</span></span>

```c
/* Set the value of a 32-Bit float resource.  */
status = nx_lwm2m_client_resource_float32_set(&resource, 1.24);

/* If status is NX_SUCCESS, the value of 32-Bit float resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_float64_get"></a><span data-ttu-id="6a191-698">nx_lwm2m_client_resource_float64_get</span><span class="sxs-lookup"><span data-stu-id="6a191-698">nx_lwm2m_client_resource_float64_get</span></span>

<span data-ttu-id="6a191-699">Получает значение 64-битного ресурса с плавающей точкой.</span><span class="sxs-lookup"><span data-stu-id="6a191-699">Gets the value of a 64-Bit float Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-700">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-700">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_float64_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a><span data-ttu-id="6a191-701">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-701">Description</span></span>

<span data-ttu-id="6a191-702">Служба извлекает значение 64-битного ресурса **с плавающей точкой**.</span><span class="sxs-lookup"><span data-stu-id="6a191-702">The service retrieves the value of a 64-Bit **float** Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-703">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-703">Parameters</span></span>

- <span data-ttu-id="6a191-704">**resource** Указатель на ресурс.</span><span class="sxs-lookup"><span data-stu-id="6a191-704">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="6a191-705">**float64_ptr** Указатель на целевое 64-битное **значение с плавающей точкой**.</span><span class="sxs-lookup"><span data-stu-id="6a191-705">**float64_ptr** Pointer to the destination 64-Bit **float** value.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-706">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-706">Return Values</span></span>

- <span data-ttu-id="6a191-707">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-707">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-708">**NX_LWM2M_CLIENT_BAD_ENCODING** Значение ресурса не является значением с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="6a191-708">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a float value.</span></span>
- <span data-ttu-id="6a191-709">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-709">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-710">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-710">Allowed From</span></span>

<span data-ttu-id="6a191-711">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-711">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-712">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-712">Example</span></span>

```c
/* Get the value of a 64-Bit float resource.  */
status = nx_lwm2m_client_resource_float64_get(&resource, &float64);

/* If status is NX_SUCCESS, the value of 64-Bit float resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_float64_set"></a><span data-ttu-id="6a191-713">nx_lwm2m_client_resource_float64_set</span><span class="sxs-lookup"><span data-stu-id="6a191-713">nx_lwm2m_client_resource_float64_set</span></span>

<span data-ttu-id="6a191-714">Устанавливает значение 64-битного ресурса **с плавающей точкой**.</span><span class="sxs-lookup"><span data-stu-id="6a191-714">Sets the value of a 64-Bit **float** Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-715">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-715">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_float64_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_FLOAT64 float64_data);
```

### <a name="description"></a><span data-ttu-id="6a191-716">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-716">Description</span></span>

<span data-ttu-id="6a191-717">Служба устанавливает значение 64-битного ресурса **с плавающей точкой**.</span><span class="sxs-lookup"><span data-stu-id="6a191-717">The service sets the value of a 64-Bit **float** Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-718">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-718">Parameters</span></span>

- <span data-ttu-id="6a191-719">**resource** Указатель на ресурс.</span><span class="sxs-lookup"><span data-stu-id="6a191-719">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="6a191-720">**float64_data** 64-битные **данные с плавающей точкой**.</span><span class="sxs-lookup"><span data-stu-id="6a191-720">**float64_data** 64-bit **float** data.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-721">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-721">Return Values</span></span>

- <span data-ttu-id="6a191-722">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-722">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-723">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-723">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-724">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-724">Allowed From</span></span>

<span data-ttu-id="6a191-725">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-725">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-726">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-726">Example</span></span>

```c
/* Set the value of a 64-Bit float resource.  */
status = nx_lwm2m_client_resource_float64_set(&resource, 1.24);

/* If status is NX_SUCCESS, the value of 64-Bit float resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_info_get"></a><span data-ttu-id="6a191-727">nx_lwm2m_client_resource_info_get</span><span class="sxs-lookup"><span data-stu-id="6a191-727">nx_lwm2m_client_resource_info_get</span></span>

<span data-ttu-id="6a191-728">Получает информацию о ресурсе.</span><span class="sxs-lookup"><span data-stu-id="6a191-728">Gets the resource info.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-729">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-729">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_info_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_ID *resource_id, 
    ULONG *operation);
```

### <a name="description"></a><span data-ttu-id="6a191-730">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-730">Description</span></span>

<span data-ttu-id="6a191-731">Служба извлекает информацию о ресурсе.</span><span class="sxs-lookup"><span data-stu-id="6a191-731">The service retrieves the resource information of Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-732">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-732">Parameters</span></span>

- <span data-ttu-id="6a191-733">**resource** Указатель на ресурс.</span><span class="sxs-lookup"><span data-stu-id="6a191-733">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="6a191-734">**resource_id** Указатель на идентификатор ресурса назначения.</span><span class="sxs-lookup"><span data-stu-id="6a191-734">**resource_id** Pointer to the destination resource ID.</span></span>
- <span data-ttu-id="6a191-735">**operation** Указатель на целевую операцию ресурса.</span><span class="sxs-lookup"><span data-stu-id="6a191-735">**operation** Pointer to the destination resource operation.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-736">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-736">Return Values</span></span>

- <span data-ttu-id="6a191-737">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-737">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-738">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-738">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-739">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-739">Allowed From</span></span>

<span data-ttu-id="6a191-740">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-740">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-741">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-741">Example</span></span>

```c
/* Get the resource information.  */
status = nx_lwm2m_client_resource_info_get(&resource, &resource_id, &operation);

/* If status is NX_SUCCESS, the resource information was successfully get. */
```

## <a name="nx_lwm2m_client_resource_info_set"></a><span data-ttu-id="6a191-742">nx_lwm2m_client_resource_info_set</span><span class="sxs-lookup"><span data-stu-id="6a191-742">nx_lwm2m_client_resource_info_set</span></span>

<span data-ttu-id="6a191-743">Устанавливает информацию о ресурсе.</span><span class="sxs-lookup"><span data-stu-id="6a191-743">Sets the resource information.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-744">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-744">Prototype</span></span>

```C
UINT nx_lwm2m_client_resource_info_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    NX_LWM2M_FLOAT64 float64_data);
```

### <a name="description"></a><span data-ttu-id="6a191-745">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-745">Description</span></span>

<span data-ttu-id="6a191-746">Сервис устанавливает информацию о ресурсе.</span><span class="sxs-lookup"><span data-stu-id="6a191-746">The service sets the resource information.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-747">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-747">Parameters</span></span>

- <span data-ttu-id="6a191-748">**resource** Указатель на ресурс.</span><span class="sxs-lookup"><span data-stu-id="6a191-748">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="6a191-749">**resource_id** Идентификатор ресурса.</span><span class="sxs-lookup"><span data-stu-id="6a191-749">**resource_id** ID of the resource.</span></span>
- <span data-ttu-id="6a191-750">**operation** Операция ресурса.</span><span class="sxs-lookup"><span data-stu-id="6a191-750">**operation** Operation of the resource.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-751">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-751">Return Values</span></span>

- <span data-ttu-id="6a191-752">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-752">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-753">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-753">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-754">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-754">Allowed From</span></span>

<span data-ttu-id="6a191-755">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-755">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-756">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-756">Example</span></span>

```c
/* Set the resource information.  */
status = nx_lwm2m_client_resource_info_set(&resource, 0, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);

/* If status is NX_SUCCESS, the resource information was successfully set. */
```

## <a name="nx_lwm2m_client_resource_instances_get"></a><span data-ttu-id="6a191-757">nx_lwm2m_client_resource_instances_get</span><span class="sxs-lookup"><span data-stu-id="6a191-757">nx_lwm2m_client_resource_instances_get</span></span>

<span data-ttu-id="6a191-758">Получает экземпляр нескольких ресурсов.</span><span class="sxs-lookup"><span data-stu-id="6a191-758">Gets the instance of multiple resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-759">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-759">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_instances_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_CLIENT_RESOURCE *resource_instances, 
    UINT *count);
```

### <a name="description"></a><span data-ttu-id="6a191-760">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-760">Description</span></span>

<span data-ttu-id="6a191-761">Служба извлекает информацию о ресурсе.</span><span class="sxs-lookup"><span data-stu-id="6a191-761">The service retrieves the resource information of Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-762">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-762">Parameters</span></span>

- <span data-ttu-id="6a191-763">**resource** Указатель на ресурс.</span><span class="sxs-lookup"><span data-stu-id="6a191-763">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="6a191-764">**resource_instances** Указатель на идентификатор ресурса назначения.</span><span class="sxs-lookup"><span data-stu-id="6a191-764">**resource_instances** Pointer to the destination resource ID.</span></span>
- <span data-ttu-id="6a191-765">**count** Указатель на счетчик.</span><span class="sxs-lookup"><span data-stu-id="6a191-765">**count** Pointer to the count.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-766">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-766">Return Values</span></span>

- <span data-ttu-id="6a191-767">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-767">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-768">**NX_LWM2M_CLIENT_BAD_ENCODING** Значение ресурса не является логическим значением.</span><span class="sxs-lookup"><span data-stu-id="6a191-768">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a Boolean value.</span></span>
- <span data-ttu-id="6a191-769">**NX_LWM2M_CLIENT_NO_MEMORY** Отсутствует память для заполнения экземпляров.</span><span class="sxs-lookup"><span data-stu-id="6a191-769">**NX_LWM2M_CLIENT_NO_MEMORY** No memory to fill out instances.</span></span>
- <span data-ttu-id="6a191-770">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-770">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-771">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-771">Allowed From</span></span>

<span data-ttu-id="6a191-772">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-772">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-773">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-773">Example</span></span>

```c
/* Get the resource information.  */
status = nx_lwm2m_client_resource_instances_get(&resource, &resource_instances,
                                                &count);

/* If status is NX_SUCCESS, the instances of multiple resource information were successfully get. */
```

## <a name="nx_lwm2m_client_resource_instances_set"></a><span data-ttu-id="6a191-774">nx_lwm2m_client_resource_instances_set</span><span class="sxs-lookup"><span data-stu-id="6a191-774">nx_lwm2m_client_resource_instances_set</span></span>

<span data-ttu-id="6a191-775">Устанавливает экземпляры ресурса.</span><span class="sxs-lookup"><span data-stu-id="6a191-775">Sets the resource instances.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-776">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-776">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_instances_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_CLIENT_RESOURCE *resource_instances, 
    UINT count);
```
### <a name="description"></a><span data-ttu-id="6a191-777">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-777">Description</span></span>

<span data-ttu-id="6a191-778">Служба устанавливает экземпляры ресурса для нескольких ресурсов.</span><span class="sxs-lookup"><span data-stu-id="6a191-778">The service sets the resource instances for multiple resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-779">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-779">Parameters</span></span>

- <span data-ttu-id="6a191-780">**resource** Указатель на ресурс.</span><span class="sxs-lookup"><span data-stu-id="6a191-780">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="6a191-781">**resource_instance** Указатель на экземпляры ресурса.</span><span class="sxs-lookup"><span data-stu-id="6a191-781">**resource_instance** Pointer to resource instances.</span></span>
- <span data-ttu-id="6a191-782">**count** Количество экземпляров ресурса.</span><span class="sxs-lookup"><span data-stu-id="6a191-782">**count** Count of resource instances.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-783">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-783">Return Values</span></span>

- <span data-ttu-id="6a191-784">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-784">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-785">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-785">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-786">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-786">Allowed From</span></span>

<span data-ttu-id="6a191-787">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-787">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-788">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-788">Example</span></span>

```c
/* Set the resource information.  */
status = nx_lwm2m_client_resource_instances_set(&resource, &resource_instance, 2);

/* If status is NX_SUCCESS, the resource instances were successfully set. */
```

## <a name="nx_lwm2m_client_resource_integer32_get"></a><span data-ttu-id="6a191-789">nx_lwm2m_client_resource_integer32_get</span><span class="sxs-lookup"><span data-stu-id="6a191-789">nx_lwm2m_client_resource_integer32_get</span></span>

<span data-ttu-id="6a191-790">Получает значение 32-разрядного целочисленного ресурса.</span><span class="sxs-lookup"><span data-stu-id="6a191-790">Gets the value of a 32-Bit integer Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-791">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-791">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_integer32_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER32 *integer32_ptr);
```

### <a name="description"></a><span data-ttu-id="6a191-792">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-792">Description</span></span>

<span data-ttu-id="6a191-793">Служба извлекает значение 32-разрядного целочисленного ресурса.</span><span class="sxs-lookup"><span data-stu-id="6a191-793">The service retrieves the value of a 32-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-794">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-794">Parameters</span></span>

- <span data-ttu-id="6a191-795">**resource** Указатель на ресурс.</span><span class="sxs-lookup"><span data-stu-id="6a191-795">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="6a191-796">**integer32_ptr** Указатель на 32-битное целое число.</span><span class="sxs-lookup"><span data-stu-id="6a191-796">**integer32_ptr** Pointer to the 32-Bit integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-797">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-797">Return Values</span></span>

- <span data-ttu-id="6a191-798">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-798">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-799">**NX_LWM2M_CLIENT_BAD_ENCODING** Значение ресурса не является целым числом.</span><span class="sxs-lookup"><span data-stu-id="6a191-799">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not integer value.</span></span>
- <span data-ttu-id="6a191-800">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-800">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-801">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-801">Allowed From</span></span>

<span data-ttu-id="6a191-802">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-802">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-803">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-803">Example</span></span>

```c
/* Get the value of a 32-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer32_get(&resource, &integer32);

/* If status is NX_SUCCESS, the value of 32-Bit integer resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_integer32_set"></a><span data-ttu-id="6a191-804">nx_lwm2m_client_resource_integer32_set</span><span class="sxs-lookup"><span data-stu-id="6a191-804">nx_lwm2m_client_resource_integer32_set</span></span>

<span data-ttu-id="6a191-805">Устанавливает значение 32-битного целочисленного ресурса.</span><span class="sxs-lookup"><span data-stu-id="6a191-805">Sets the value of a 32-Bit integer Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-806">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-806">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_integer32_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER32 integer32_data);
```

### <a name="description"></a><span data-ttu-id="6a191-807">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-807">Description</span></span>

<span data-ttu-id="6a191-808">Служба устанавливает значение 32-битного целого ресурса.</span><span class="sxs-lookup"><span data-stu-id="6a191-808">The service sets the value of a 32-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-809">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-809">Parameters</span></span>

- <span data-ttu-id="6a191-810">**resource** Указатель на ресурс.</span><span class="sxs-lookup"><span data-stu-id="6a191-810">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="6a191-811">**integer32_data** 32-битные целочисленные данные.</span><span class="sxs-lookup"><span data-stu-id="6a191-811">**integer32_data** 32-Bit integer data.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-812">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-812">Return Values</span></span>

- <span data-ttu-id="6a191-813">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-813">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-814">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-814">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-815">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-815">Allowed From</span></span>

<span data-ttu-id="6a191-816">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-816">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-817">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-817">Example</span></span>

```c
/* Set the value of a 32-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer32_set(&resource, 8);

/* If status is NX_SUCCESS, the value of 32-Bit integer resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_integer64_get"></a><span data-ttu-id="6a191-818">nx_lwm2m_client_resource_integer64_get</span><span class="sxs-lookup"><span data-stu-id="6a191-818">nx_lwm2m_client_resource_integer64_get</span></span>

<span data-ttu-id="6a191-819">Получает значение ресурса 64-разрядного целого числа.</span><span class="sxs-lookup"><span data-stu-id="6a191-819">Gets the value of a 64-Bit integer Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-820">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-820">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_integer64_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER64 *integer64_ptr);
```

### <a name="description"></a><span data-ttu-id="6a191-821">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-821">Description</span></span>

<span data-ttu-id="6a191-822">Служба извлекает значение 64-битного целочисленного ресурса.</span><span class="sxs-lookup"><span data-stu-id="6a191-822">The service retrieves the value of a 64-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-823">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-823">Parameters</span></span>

- <span data-ttu-id="6a191-824">**resource** Указатель на ресурс.</span><span class="sxs-lookup"><span data-stu-id="6a191-824">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="6a191-825">**integer64_ptr** Указатель на 64-битное целое число.</span><span class="sxs-lookup"><span data-stu-id="6a191-825">**integer64_ptr** Pointer to the 64-Bit integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-826">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-826">Return Values</span></span>

- <span data-ttu-id="6a191-827">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-827">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-828">**NX_LWM2M_CLIENT_BAD_ENCODING** Значение ресурса не является 64-битным целым числом.</span><span class="sxs-lookup"><span data-stu-id="6a191-828">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not 64-Bit integer value.</span></span>
- <span data-ttu-id="6a191-829">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-829">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-830">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-830">Allowed From</span></span>

<span data-ttu-id="6a191-831">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-831">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-832">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-832">Example</span></span>

```c
/* Get the value of a 64-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer64_get(&resource, &integer64);

/* If status is NX_SUCCESS, the value of 64-Bit integer resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_integer64_set"></a><span data-ttu-id="6a191-833">nx_lwm2m_client_resource_integer64_set</span><span class="sxs-lookup"><span data-stu-id="6a191-833">nx_lwm2m_client_resource_integer64_set</span></span>

## <a name="set-the-value-of-a-64-bit-integer-resource"></a><span data-ttu-id="6a191-834">Установить значение 64-битного целочисленного ресурса</span><span class="sxs-lookup"><span data-stu-id="6a191-834">Set the value of a 64-Bit integer Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-835">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-835">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_integer64_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER64 integer64_data);
```

### <a name="description"></a><span data-ttu-id="6a191-836">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-836">Description</span></span>

<span data-ttu-id="6a191-837">Сервис устанавливает значение 64-битного целого ресурса.</span><span class="sxs-lookup"><span data-stu-id="6a191-837">The service sets the value of a 64-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-838">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-838">Parameters</span></span>

- <span data-ttu-id="6a191-839">**resource** Указатель на ресурс.</span><span class="sxs-lookup"><span data-stu-id="6a191-839">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="6a191-840">**integer64_data** 64-битное целое число.</span><span class="sxs-lookup"><span data-stu-id="6a191-840">**integer64_data** 64-bit integer.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-841">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-841">Return Values</span></span>

- <span data-ttu-id="6a191-842">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-842">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-843">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-843">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-844">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-844">Allowed From</span></span>

<span data-ttu-id="6a191-845">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-845">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-846">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-846">Example</span></span>

```c
/* Set the value of a 64-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer64_set(&resource, 32323);

/* If status is NX_SUCCESS, the value of 64-Bit integer resource was successfully set. */
```

##  <a name="nx_lwm2m_client_resource_objlnk_get"></a><span data-ttu-id="6a191-847">nx_lwm2m_client_resource_objlnk_get</span><span class="sxs-lookup"><span data-stu-id="6a191-847">nx_lwm2m_client_resource_objlnk_get</span></span>

<span data-ttu-id="6a191-848">Получает значение ресурса ссылки на объект.</span><span class="sxs-lookup"><span data-stu-id="6a191-848">Gets the value of an object link resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-849">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-849">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_objlnk_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_ID *object_id, 
    NX_LWM2M_ID *instance_id);
```

### <a name="description"></a><span data-ttu-id="6a191-850">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-850">Description</span></span>

<span data-ttu-id="6a191-851">Служба получает значение ссылки на объект.</span><span class="sxs-lookup"><span data-stu-id="6a191-851">The service retrieves the value of object link.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-852">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-852">Parameters</span></span>

- <span data-ttu-id="6a191-853">**resource** Указатель на ресурс.</span><span class="sxs-lookup"><span data-stu-id="6a191-853">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="6a191-854">**object_id** Указатель на идентификатор объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-854">**object_id** Pointer to the object ID.</span></span>
- <span data-ttu-id="6a191-855">**instance_id** Указатель на идентификатор экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-855">**instance_id** Pointer to the object instance ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-856">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-856">Return Values</span></span>

- <span data-ttu-id="6a191-857">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-857">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-858">**NX_LWM2M_CLIENT_BAD_ENCODING** Значение ресурса не является значением ссылки на объект.</span><span class="sxs-lookup"><span data-stu-id="6a191-858">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not an object link value.</span></span>
- <span data-ttu-id="6a191-859">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-859">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-860">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-860">Allowed From</span></span>

<span data-ttu-id="6a191-861">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-861">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-862">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-862">Example</span></span>

```c
/* Get the value of the object link resource.  */
status = nx_lwm2m_client_resource_objlnk_get(&resource, &object_id, &instance_id);

/* If status is NX_SUCCESS, the object link value was successfully get. */
```

## <a name="nx_lwm2m_client_resource_objlnk_set"></a><span data-ttu-id="6a191-863">nx_lwm2m_client_resource_objlnk_set</span><span class="sxs-lookup"><span data-stu-id="6a191-863">nx_lwm2m_client_resource_objlnk_set</span></span>

<span data-ttu-id="6a191-864">Устанавливает экземпляры ресурса</span><span class="sxs-lookup"><span data-stu-id="6a191-864">Sets the resource instances</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-865">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-865">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_objlnk_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    NX_LWM2M_ID object_id, 
    NX_LWM2M_ID instance_id);
```

### <a name="description"></a><span data-ttu-id="6a191-866">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-866">Description</span></span>

<span data-ttu-id="6a191-867">Служба устанавливает значение ресурса ссылки на объект.</span><span class="sxs-lookup"><span data-stu-id="6a191-867">The service sets the value of the object link resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-868">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-868">Parameters</span></span>

- <span data-ttu-id="6a191-869">**resource** Указатель на ресурс.</span><span class="sxs-lookup"><span data-stu-id="6a191-869">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="6a191-870">**object_id** Идентификатор объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-870">**object_id** Object ID.</span></span>
- <span data-ttu-id="6a191-871">**instance_id** Идентификатор экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="6a191-871">**instance_id** Object instance ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-872">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-872">Return Values</span></span>

- <span data-ttu-id="6a191-873">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-873">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-874">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-874">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-875">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-875">Allowed From</span></span>

<span data-ttu-id="6a191-876">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-876">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-877">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-877">Example</span></span>

```c
/* Set the value of object link resource.  */
status = nx_lwm2m_client_resource_objlnk_set(&resource, 3303, 2);

/* If status is NX_SUCCESS, the value of object link resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_opaque_get"></a><span data-ttu-id="6a191-878">nx_lwm2m_client_resource_opaque_get</span><span class="sxs-lookup"><span data-stu-id="6a191-878">nx_lwm2m_client_resource_opaque_get</span></span>

<span data-ttu-id="6a191-879">Получает значение непрозрачного ресурса.</span><span class="sxs-lookup"><span data-stu-id="6a191-879">Gets the value of an opaque Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-880">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-880">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_opaque_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    const VOID **opaque_ptr, 
    UINT \*opaque_length);
```


### <a name="description"></a><span data-ttu-id="6a191-881">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-881">Description</span></span>

<span data-ttu-id="6a191-882">Служба извлекает значение непрозрачного ресурса.</span><span class="sxs-lookup"><span data-stu-id="6a191-882">The service retrieves the value of an opaque Resource.</span></span> <span data-ttu-id="6a191-883">Значение непрозрачного ресурса состоит из указателя на буфер и длины.</span><span class="sxs-lookup"><span data-stu-id="6a191-883">An opaque resource value consists of a pointer to a buffer and a length.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-884">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-884">Parameters</span></span>

- <span data-ttu-id="6a191-885">**resource** Указатель на ресурс.</span><span class="sxs-lookup"><span data-stu-id="6a191-885">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="6a191-886">**opaque_ptr** Указатель на непрозрачные данные.</span><span class="sxs-lookup"><span data-stu-id="6a191-886">**opaque_ptr** Pointer to the opaque data.</span></span>
- <span data-ttu-id="6a191-887">**opaque_length** Указатель на длину непрозрачных данных.</span><span class="sxs-lookup"><span data-stu-id="6a191-887">**opaque_length** Pointer to the opaque data length.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-888">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-888">Return Values</span></span>

- <span data-ttu-id="6a191-889">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-889">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-890">**NX_LWM2M_CLIENT_BAD_ENCODING** Значение ресурса не является непрозрачным ресурсом.</span><span class="sxs-lookup"><span data-stu-id="6a191-890">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not an opaque resource.</span></span>
- <span data-ttu-id="6a191-891">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-891">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-892">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-892">Allowed From</span></span>

<span data-ttu-id="6a191-893">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-893">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-894">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-894">Example</span></span>

```c
/* Get the value of an opaque resource.  */
status = nx_lwm2m_client_resource_opaque_get(&resource, &opaque_ptr, &opaque_length);

/* If status is NX_SUCCESS, the value of opaque resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_opaque_set"></a><span data-ttu-id="6a191-895">nx_lwm2m_client_resource_opaque_set</span><span class="sxs-lookup"><span data-stu-id="6a191-895">nx_lwm2m_client_resource_opaque_set</span></span>

<span data-ttu-id="6a191-896">Устанавливает значение непрозрачного ресурса.</span><span class="sxs-lookup"><span data-stu-id="6a191-896">Sets the value of an opaque Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-897">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-897">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_opaque_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    VOID *opaque_ptr, 
    UINT opaque_length);
```

### <a name="description"></a><span data-ttu-id="6a191-898">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-898">Description</span></span>

<span data-ttu-id="6a191-899">Сервис устанавливает значение непрозрачного ресурса.</span><span class="sxs-lookup"><span data-stu-id="6a191-899">The service sets the value of an opaque Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-900">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-900">Parameters</span></span>

- <span data-ttu-id="6a191-901">**resource** Указатель на ресурс.</span><span class="sxs-lookup"><span data-stu-id="6a191-901">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="6a191-902">**opaque_ptr** Указатель на непрозрачные данные.</span><span class="sxs-lookup"><span data-stu-id="6a191-902">**opaque_ptr** Pointer to the opaque data.</span></span>
- <span data-ttu-id="6a191-903">**opaque_length** Длина непрозрачных данных.</span><span class="sxs-lookup"><span data-stu-id="6a191-903">**opaque_length** Length of the opaque data.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-904">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-904">Return Values</span></span>

- <span data-ttu-id="6a191-905">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-905">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-906">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-906">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-907">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-907">Allowed From</span></span>

<span data-ttu-id="6a191-908">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-908">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-909">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-909">Example</span></span>

```c
/* Set the value of an opaque resource.  */
status = nx_lwm2m_client_resource_opaque_set(&resource, “AQIDBAU=”, 8);

/* If status is NX_SUCCESS, the value of opaque resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_string_get"></a><span data-ttu-id="6a191-910">nx_lwm2m_client_resource_string_get</span><span class="sxs-lookup"><span data-stu-id="6a191-910">nx_lwm2m_client_resource_string_get</span></span>

<span data-ttu-id="6a191-911">Получает значение строкового ресурса.</span><span class="sxs-lookup"><span data-stu-id="6a191-911">Gets the value of a string Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-912">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-912">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_string_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    const CHAR **string_ptr, 
    UINT *string_length);
```

### <a name="description"></a><span data-ttu-id="6a191-913">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-913">Description</span></span>

<span data-ttu-id="6a191-914">Служба извлекает значение строкового ресурса.</span><span class="sxs-lookup"><span data-stu-id="6a191-914">The service retrieves the value of a string Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-915">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-915">Parameters</span></span>

- <span data-ttu-id="6a191-916">**resource** Указатель на ресурс.</span><span class="sxs-lookup"><span data-stu-id="6a191-916">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="6a191-917">**string_ptr** Указатель на указатель целевой строки.</span><span class="sxs-lookup"><span data-stu-id="6a191-917">**string_ptr** Pointer to the destination string pointer.</span></span>
- <span data-ttu-id="6a191-918">**string_length** Указатель на длину целевой строки.</span><span class="sxs-lookup"><span data-stu-id="6a191-918">**string_length** Pointer to the destination string length.</span></span> <span data-ttu-id="6a191-919">Может иметь значение **NULL**, если строка заканчивается нулем.</span><span class="sxs-lookup"><span data-stu-id="6a191-919">Can be **NULL** if the string is null-terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-920">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-920">Return Values</span></span>

- <span data-ttu-id="6a191-921">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-921">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-922">**NX_LWM2M_CLIENT_BAD_ENCODING** Значение ресурса не является строковым значением.</span><span class="sxs-lookup"><span data-stu-id="6a191-922">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a string value.</span></span>
- <span data-ttu-id="6a191-923">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-923">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-924">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-924">Allowed From</span></span>

<span data-ttu-id="6a191-925">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-925">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-926">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-926">Example</span></span>

```c
/* Get the value of a string resource.  */
status = nx_lwm2m_client_resource_string_get(&resource, &string_ptr, &string_length);

/* If status is NX_SUCCESS, the value of string resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_string_set"></a><span data-ttu-id="6a191-927">nx_lwm2m_client_resource_string_set</span><span class="sxs-lookup"><span data-stu-id="6a191-927">nx_lwm2m_client_resource_string_set</span></span>

<span data-ttu-id="6a191-928">Устанавливает значение строкового ресурса.</span><span class="sxs-lookup"><span data-stu-id="6a191-928">Sets the value of a string Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-929">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-929">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_string_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    CHAR *string_ptr, 
    UINT string_length);
```

### <a name="description"></a><span data-ttu-id="6a191-930">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-930">Description</span></span>

<span data-ttu-id="6a191-931">Сервис устанавливает значение 64-битного целого ресурса.</span><span class="sxs-lookup"><span data-stu-id="6a191-931">The service sets the value of a 64-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-932">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-932">Parameters</span></span>

- <span data-ttu-id="6a191-933">**resource** Указатель на ресурс.</span><span class="sxs-lookup"><span data-stu-id="6a191-933">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="6a191-934">**string_ptr** Указатель на строку.</span><span class="sxs-lookup"><span data-stu-id="6a191-934">**string_ptr** Pointer to the string.</span></span>
- <span data-ttu-id="6a191-935">**string_length** Длина строки.</span><span class="sxs-lookup"><span data-stu-id="6a191-935">**string_length** Length of the string.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-936">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-936">Return Values</span></span>

- <span data-ttu-id="6a191-937">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-937">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-938">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-938">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-939">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-939">Allowed From</span></span>

<span data-ttu-id="6a191-940">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-940">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-941">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-941">Example</span></span>

```c
/* Set the value of a string resource.  */
status = nx_lwm2m_client_resource_string_set(&resource, “test”, sizeof(“test”) - 1);

/* If status is NX_SUCCESS, the value of string resource was successfully set. */
```

## <a name="nx_lwm2m_client_session_bootstrap"></a><span data-ttu-id="6a191-942">nx_lwm2m_client_session_bootstrap</span><span class="sxs-lookup"><span data-stu-id="6a191-942">nx_lwm2m_client_session_bootstrap</span></span>

<span data-ttu-id="6a191-943">Начинает сеанс с сервером начальной загрузки.</span><span class="sxs-lookup"><span data-stu-id="6a191-943">Starts a session with a Bootstrap Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-944">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-944">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_bootstrap(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID security_id, 
    ULONG ip_address, 
    UINT port);
```

### <a name="description"></a><span data-ttu-id="6a191-945">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-945">Description</span></span>

<span data-ttu-id="6a191-946">Данная служба запускает сеанс с сервером начальной загрузки.</span><span class="sxs-lookup"><span data-stu-id="6a191-946">This service starts a session with a Bootstrap Server.</span></span> <span data-ttu-id="6a191-947">Сервер должен иметь соответствующий экземпляр защиты в объекте защиты.</span><span class="sxs-lookup"><span data-stu-id="6a191-947">The server should have a corresponding security instance in the Security Object.</span></span>

<span data-ttu-id="6a191-948">Если ресурс «Ожидание» отличен от нуля в экземпляре безопасности, связанном с данным сервером, сеанс будет ожидать инициированной сервером начальной загрузки. Если по истечении этого периода времени сервер не инициирует загрузку, будет выполнено инициированное клиентом ускорение.</span><span class="sxs-lookup"><span data-stu-id="6a191-948">If the ‘Hold Off’ resource is different than zero in the Security Instance associated with this server the session will wait for a Server Initiated Bootstrap, If no bootstrap is initiated by the server after this period of time a Client Initiated Boostrap will be performed.</span></span>

<span data-ttu-id="6a191-949">Любой текущий активный сеанс прерывается этим вызовом и заменяется новым сеансом сервера начальной загрузки.</span><span class="sxs-lookup"><span data-stu-id="6a191-949">Any current active session is aborted by this call and replaced by the new Bootstrap Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-950">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-950">Parameters</span></span>

- <span data-ttu-id="6a191-951">**session_ptr** Указатель на блок управления сеансом клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-951">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="6a191-952">**security_id** Если на сервере начальной загрузки не определен экземпляр безопасности, идентификатор экземпляра безопасности сервера начальной загрузки должен иметь значение NX_LWM2M_RESERVED_ID (65535),</span><span class="sxs-lookup"><span data-stu-id="6a191-952">**security_id** The Security Instance ID of the Bootstrap Server, must be set to NX_LWM2M_RESERVED_ID (65535) if the Bootstrap Server has no Security Instance defined.</span></span>
- <span data-ttu-id="6a191-953">**ip_address** IP-адрес сервера.</span><span class="sxs-lookup"><span data-stu-id="6a191-953">**ip_address** The IP address of the server.</span></span>
- <span data-ttu-id="6a191-954">**port** UDP-порт сервера.</span><span class="sxs-lookup"><span data-stu-id="6a191-954">**port** The UDP port of the server.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-955">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-955">Return Values</span></span>

- <span data-ttu-id="6a191-956">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-956">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-957">**NX_LWM2M_CLIENT_ERROR** Ошибка начальной загрузки.</span><span class="sxs-lookup"><span data-stu-id="6a191-957">**NX_LWM2M_CLIENT_ERROR** Bootstrap error.</span></span>
- <span data-ttu-id="6a191-958">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Порт недоступен.</span><span class="sxs-lookup"><span data-stu-id="6a191-958">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="6a191-959">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-959">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-960">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-960">Allowed From</span></span>

<span data-ttu-id="6a191-961">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-961">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-962">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-962">Example</span></span>

```c
/* Start bootstrap.  */
status = nx_lwm2m_client_session_bootstrap(&lwm2m_client, 0, &ip_address, 5783);

/* If status is NX_SUCCESS, start bootstrap successfully.  */
```

## <a name="nx_lwm2m_client_session_bootstrap_dtls"></a><span data-ttu-id="6a191-963">nx_lwm2m_client_session_bootstrap_dtls</span><span class="sxs-lookup"><span data-stu-id="6a191-963">nx_lwm2m_client_session_bootstrap_dtls</span></span>

<span data-ttu-id="6a191-964">Запускает безопасный сеанс с сервером начальной загрузки</span><span class="sxs-lookup"><span data-stu-id="6a191-964">Starts a secure session with a Bootstrap Server</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-965">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-965">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_bootstrap_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID security_id, 
    ULONG ip_address, 
    UINT port, 
    NX_SECURE_DTLS_SESSION *dtls_session_ptr);
```

### <a name="description"></a><span data-ttu-id="6a191-966">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-966">Description</span></span>

<span data-ttu-id="6a191-967">Данная служба запускает сеанс с сервером начальной загрузки, используя безопасное соединение DTLS.</span><span class="sxs-lookup"><span data-stu-id="6a191-967">This service start a session with a Bootstrap Server using a secure DTLS connection.</span></span> <span data-ttu-id="6a191-968">Сервер должен иметь соответствующий экземпляр защиты в объекте защиты.</span><span class="sxs-lookup"><span data-stu-id="6a191-968">The server should have a corresponding security instance in the Security Object.</span></span>

<span data-ttu-id="6a191-969">Перед вызовом данной функции сеанс протокола DTLS должен быть настроен с использованием надлежащих наборов шифров и ключевого материала.</span><span class="sxs-lookup"><span data-stu-id="6a191-969">The DTLS session must have been configured with the proper cipher suites and key material before calling this function.</span></span> <span data-ttu-id="6a191-970">Необходимо определить **NX_SECURE_ENABLE_DTLS**.</span><span class="sxs-lookup"><span data-stu-id="6a191-970">**NX_SECURE_ENABLE_DTLS** must be defined.</span></span>

<span data-ttu-id="6a191-971">Если ресурс «Ожидание» отличен от нуля в экземпляре безопасности, связанном с данным сервером, сеанс будет ожидать инициируемой сервером начальной загрузки, если сервер не инициирует загрузку по истечении этого периода времени, будет выполнено инициированное клиентом ускорение.</span><span class="sxs-lookup"><span data-stu-id="6a191-971">If the ‘Hold Off’ resource is different than zero in the Security Instance associated with this server the session will wait for a Server Initiated Bootstrap, if no bootstrap is initiated by the server after this period of time a Client Initiated Boostrap will be performed.</span></span> 

<span data-ttu-id="6a191-972">Любой текущий активный сеанс прерывается этим вызовом и заменяется новым сеансом сервера начальной загрузки.</span><span class="sxs-lookup"><span data-stu-id="6a191-972">Any current active session is aborted by this call and replaced by the new Bootstrap Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-973">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-973">Parameters</span></span>

- <span data-ttu-id="6a191-974">**session_ptr** Указатель на блок управления сеансом клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-974">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="6a191-975">**security_id** Если на сервере начальной загрузки не определен экземпляр безопасности, идентификатор экземпляра безопасности сервера начальной загрузки должен иметь значение **NX_LWM2M_RESERVED_ID** (65535).</span><span class="sxs-lookup"><span data-stu-id="6a191-975">**security_id** The Security Instance ID of the Bootstrap Server, must be set to **NX_LWM2M_RESERVED_ID** (65535) if the Bootstrap Server has no Security Instance defined.</span></span>
- <span data-ttu-id="6a191-976">**ip_address** IP-адрес сервера.</span><span class="sxs-lookup"><span data-stu-id="6a191-976">**ip_address** The IP address of the server.</span></span>
- <span data-ttu-id="6a191-977">**port** UDP-порт сервера.</span><span class="sxs-lookup"><span data-stu-id="6a191-977">**port** The UDP port of the server.</span></span>
- <span data-ttu-id="6a191-978">**dtls_session_ptr** Сеанс DTLS, используемый для сеанса начальной загрузки.</span><span class="sxs-lookup"><span data-stu-id="6a191-978">**dtls_session_ptr** The DTLS session to use for the Bootstrap session.</span></span>
- <span data-ttu-id="6a191-979">**dtls_local_port** Локальный UDP-порт, используемый для сеанса DTLS.</span><span class="sxs-lookup"><span data-stu-id="6a191-979">**dtls_local_port** The local UDP port used for the DTLS session.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-980">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-980">Return Values</span></span>

- <span data-ttu-id="6a191-981">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-981">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-982">**NX_LWM2M_CLIENT_ERROR** Ошибка начальной загрузки.</span><span class="sxs-lookup"><span data-stu-id="6a191-982">**NX_LWM2M_CLIENT_ERROR** Bootstrap error.</span></span>
- <span data-ttu-id="6a191-983">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Порт недоступен.</span><span class="sxs-lookup"><span data-stu-id="6a191-983">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="6a191-984">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-984">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-985">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-985">Allowed From</span></span>

<span data-ttu-id="6a191-986">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-986">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-987">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-987">Example</span></span>

```c
/* Start bootstrap with DTLS.  */
status = nx_lwm2m_client_session_bootstrap_dtls(&lwm2m_client, 0, &ip_address, 5784, &dtls_session);

/* If status is NX_SUCCESS, start bootstrap successfully.  */
```

## <a name="nx_lwm2m_client_session_create"></a><span data-ttu-id="6a191-988">nx_lwm2m_client_session_create</span><span class="sxs-lookup"><span data-stu-id="6a191-988">nx_lwm2m_client_session_create</span></span>

<span data-ttu-id="6a191-989">Создает клиентский сеанс LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-989">Creates a LWM2M Client Session.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-990">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-990">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_create(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK state_callback);
```

### <a name="description"></a><span data-ttu-id="6a191-991">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-991">Description</span></span>

<span data-ttu-id="6a191-992">Данная служба создает новый клиентский сеанс LWM2M, присоединенный к существующему клиенту LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-992">This service creates a new LWM2M Client Session attached to an existing LWM2M Client.</span></span> <span data-ttu-id="6a191-993">Сеанс используется клиентом LWM2M для связи с сервером начальной загрузки или сервером LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-993">The session is used by the LWM2M Client to communicate with a Bootstrap Server or a LWM2M Server.</span></span> 

<span data-ttu-id="6a191-994">Приложение должно предоставить функцию обратного вызова, которая будет вызываться при обновлении состояния сеанса.</span><span class="sxs-lookup"><span data-stu-id="6a191-994">The application must provide a callback function that will be called when the state of the session is updated.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-995">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-995">Parameters</span></span>

- <span data-ttu-id="6a191-996">**session_ptr** Указатель на блок управления сеансом клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-996">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="6a191-997">**client_ptr** Указатель на ранее созданный клиент LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-997">**client_ptr** Pointer to the previously created LWM2M Client.</span></span>
- <span data-ttu-id="6a191-998">**state_callback** Обратный вызов приложения, который вызывается при изменении состояния сеанса.</span><span class="sxs-lookup"><span data-stu-id="6a191-998">**state_callback** Application callback that is called when the state of the session has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-999">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-999">Return Values</span></span>

- <span data-ttu-id="6a191-1000">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-1000">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-1001">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-1001">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-1002">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-1002">Allowed From</span></span>

<span data-ttu-id="6a191-1003">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-1003">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-1004">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-1004">Example</span></span>

```c
/* Create session.  */
status = nx_lwm2m_client_session_create(&session, &lwm2m_client, session_callback);

/* If status is NX_SUCCESS, a session was successfully created.  */
```

## <a name="nx_lwm2m_client_session_delete"></a><span data-ttu-id="6a191-1005">nx_lwm2m_client_session_delete</span><span class="sxs-lookup"><span data-stu-id="6a191-1005">nx_lwm2m_client_session_delete</span></span>

<span data-ttu-id="6a191-1006">Удаляет клиентский сеанс LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-1006">Deletes a LWM2M Client Session.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-1007">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-1007">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_delete(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="6a191-1008">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-1008">Description</span></span>

<span data-ttu-id="6a191-1009">Данная служба удаляет клиентский сеанс LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-1009">This service deletes a LWM2M Client Session.</span></span>

<span data-ttu-id="6a191-1010">Когда клиент LWM2M удаляется вызовом nx_lwm2m_client_delete, также удаляются все сеансы, подключенные к клиенту.</span><span class="sxs-lookup"><span data-stu-id="6a191-1010">When a LWM2M Client is deleted by calling nx_lwm2m_client_delete all sessions attached to the client are also deleted.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-1011">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-1011">Parameters</span></span>

- <span data-ttu-id="6a191-1012">**session_ptr** Указатель на блок управления сеансом клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-1012">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-1013">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-1013">Return Values</span></span>

- <span data-ttu-id="6a191-1014">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-1014">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-1015">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-1015">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-1016">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-1016">Allowed From</span></span>

<span data-ttu-id="6a191-1017">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-1017">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-1018">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-1018">Example</span></span>

```c
/* Delete session.  */
status = nx_lwm2m_client_session_delete(&session);

/* If status is NX_SUCCESS, a session was successfully deleted.  */
```

## <a name="nx_lwm2m_client_session_deregister"></a><span data-ttu-id="6a191-1019">nx_lwm2m_client_session_deregister</span><span class="sxs-lookup"><span data-stu-id="6a191-1019">nx_lwm2m_client_session_deregister</span></span>

<span data-ttu-id="6a191-1020">Завершает сеанс с сервером LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-1020">Terminates a session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-1021">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-1021">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_deregister(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="6a191-1022">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-1022">Description</span></span>

<span data-ttu-id="6a191-1023">Данная служба выполняет операцию «Отмена регистрации» на сервере LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-1023">This service performs a ‘De-Register’ operation to a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-1024">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-1024">Parameters</span></span>

- <span data-ttu-id="6a191-1025">**session_ptr** Указатель на блок управления сеансом клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-1025">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-1026">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-1026">Return Values</span></span>

- <span data-ttu-id="6a191-1027">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-1027">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-1028">**NX_LWM2M_CLIENT_NOT_REGISTERED** Клиент не зарегистрирован на сервере.</span><span class="sxs-lookup"><span data-stu-id="6a191-1028">**NX_LWM2M_CLIENT_NOT_REGISTERED** The client is not registered to the server.</span></span>
- <span data-ttu-id="6a191-1029">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-1029">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-1030">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-1030">Allowed From</span></span>

<span data-ttu-id="6a191-1031">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-1031">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-1032">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-1032">Example</span></span>

```c
/* De-register session.  */
status = nx_lwm2m_client_session_deregister(&session);

/* If status is NX_SUCCESS, session was successfully de-registered.  */
```

## <a name="nx_lwm2m_client_session_error_get"></a><span data-ttu-id="6a191-1033">nx_lwm2m_client_session_error_get</span><span class="sxs-lookup"><span data-stu-id="6a191-1033">nx_lwm2m_client_session_error_get</span></span>

<span data-ttu-id="6a191-1034">Получает последнюю ошибку сеанса.</span><span class="sxs-lookup"><span data-stu-id="6a191-1034">Gets the last error of a session.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-1035">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-1035">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_error_get(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="6a191-1036">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-1036">Description</span></span>

<span data-ttu-id="6a191-1037">Данная служба возвращает код ошибки сеанса в случаях, когда сеанс находится в состоянии ошибки.</span><span class="sxs-lookup"><span data-stu-id="6a191-1037">This service returns the error code of the session when the session is in an error state.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-1038">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-1038">Parameters</span></span>

- <span data-ttu-id="6a191-1039">**session_ptr** Указатель на блок управления сеансом клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-1039">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-1040">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-1040">Return Values</span></span>

- <span data-ttu-id="6a191-1041">**NX_SUCCESS** Сеанс не находится в состоянии ошибки.</span><span class="sxs-lookup"><span data-stu-id="6a191-1041">**NX_SUCCESS** The session is not in error state.</span></span>
- <span data-ttu-id="6a191-1042">**NX_LWM2M_CLIENT_ADDRESS_ERROR** Недопустимый адрес сервера.</span><span class="sxs-lookup"><span data-stu-id="6a191-1042">**NX_LWM2M_CLIENT_ADDRESS_ERROR** Invalid server address.</span></span>
- <span data-ttu-id="6a191-1043">**NX_LWM2M_ CLIENT_BUFFER_TOO_SMALL** Полезные данные запроса не помещаются в сетевой буфер.</span><span class="sxs-lookup"><span data-stu-id="6a191-1043">**NX_LWM2M_ CLIENT_BUFFER_TOO_SMALL** Payload of request doesn’t fit in network buffer.</span></span>
- <span data-ttu-id="6a191-1044">**NX_LWM2M_ CLIENT_DTLS_ERROR** Не удалось установить защищенное соединение с сервером.</span><span class="sxs-lookup"><span data-stu-id="6a191-1044">**NX_LWM2M_ CLIENT_DTLS_ERROR** Failed to establish secured connection with server.</span></span>
- <span data-ttu-id="6a191-1045">**NX_LWM2M_ CLIENT_ERROR** Неопределенная ошибка.</span><span class="sxs-lookup"><span data-stu-id="6a191-1045">**NX_LWM2M_ CLIENT_ERROR** Unspecified error.</span></span>
- <span data-ttu-id="6a191-1046">**NX_LWM2M_ CLIENT_FORBIDDEN** В регистрации отказано со стороны сервера.</span><span class="sxs-lookup"><span data-stu-id="6a191-1046">**NX_LWM2M_ CLIENT_FORBIDDEN** Registration refused by server.</span></span>
- <span data-ttu-id="6a191-1047">**NX_LWM2M_ CLIENT_NOT_FOUND** Клиент не найден сервером при обновлении/отмене регистрации.</span><span class="sxs-lookup"><span data-stu-id="6a191-1047">**NX_LWM2M_ CLIENT_NOT_FOUND** Client not found by server when updating/deregistering.</span></span>
- <span data-ttu-id="6a191-1048">**NX_LWM2M_ CLIENT_SERVER_INSTANCE_DELETED** Экземпляр объекта сервера, соответствующий сеансу, был удален.</span><span class="sxs-lookup"><span data-stu-id="6a191-1048">**NX_LWM2M_ CLIENT_SERVER_INSTANCE_DELETED** The Server Object Instance corresponding to the session has been deleted.</span></span>
- <span data-ttu-id="6a191-1049">**NX_LWM2M_ CLIENT_TIMED_OUT** Нет ответа с сервера.</span><span class="sxs-lookup"><span data-stu-id="6a191-1049">**NX_LWM2M_ CLIENT_TIMED_OUT** No answer from server.</span></span>
- <span data-ttu-id="6a191-1050">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-1050">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-1051">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-1051">Allowed From</span></span>

<span data-ttu-id="6a191-1052">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-1052">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-1053">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-1053">Example</span></span>

```c
/* Get the error.  */
status = nx_lwm2m_client_session_error_get(&session);
```
## <a name="nx_lwm2m_client_session_register"></a><span data-ttu-id="6a191-1054">nx_lwm2m_client_session_register</span><span class="sxs-lookup"><span data-stu-id="6a191-1054">nx_lwm2m_client_session_register</span></span>

<span data-ttu-id="6a191-1055">Начинает сеанс с сервером LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-1055">Starts a session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-1056">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-1056">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID server_id, 
    ULONG ip_address, 
    UINT port);
```


### <a name="description"></a><span data-ttu-id="6a191-1057">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-1057">Description</span></span>

<span data-ttu-id="6a191-1058">Данная служба выполняет операцию «Регистрация» на сервере LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-1058">This service performs a ‘Register’ operation to a LWM2M Server.</span></span> <span data-ttu-id="6a191-1059">Сервер должен иметь соответствующий экземпляр сервера в объекте сервера.</span><span class="sxs-lookup"><span data-stu-id="6a191-1059">The server must have a corresponding server instance in the Server Object.</span></span>

<span data-ttu-id="6a191-1060">Если регистрация прошла успешно, клиент LWM2M будет обрабатывать дальнейшие операции с сервера и периодически отправлять сообщения «Обновить» до момента отмены регистрации клиента.</span><span class="sxs-lookup"><span data-stu-id="6a191-1060">If the registration is successfully the LWM2M Client will process further operations from the server and will periodically send ‘Update’ messages until the client is de-registered.</span></span>

<span data-ttu-id="6a191-1061">Любой текущий активный сеанс прерывается этим вызовом и заменяется новым сеансом LWM2M Server.</span><span class="sxs-lookup"><span data-stu-id="6a191-1061">Any current active session is aborted by this call and replaced by the new LWM2M Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-1062">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-1062">Parameters</span></span>

- <span data-ttu-id="6a191-1063">**session_ptr** Указатель на блок управления сеансом клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-1063">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="6a191-1064">**server_id** Краткий идентификатор сервера LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-1064">**server_id** The Short Server ID of the LWM2M Server.</span></span>
- <span data-ttu-id="6a191-1065">**ip_address** IP-адрес сервера.</span><span class="sxs-lookup"><span data-stu-id="6a191-1065">**ip_address** The IP address of the server.</span></span>
- <span data-ttu-id="6a191-1066">**port** UDP-порт сервера.</span><span class="sxs-lookup"><span data-stu-id="6a191-1066">**port** The UDP port of the server.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-1067">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-1067">Return Values</span></span>

- <span data-ttu-id="6a191-1068">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-1068">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-1069">**NX_LWM2M_CLIENT_ERROR** Ошибка начальной загрузки.</span><span class="sxs-lookup"><span data-stu-id="6a191-1069">**NX_LWM2M_CLIENT_ERROR** Bootstrap error.</span></span>
- <span data-ttu-id="6a191-1070">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Порт недоступен.</span><span class="sxs-lookup"><span data-stu-id="6a191-1070">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="6a191-1071">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-1071">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-1072">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-1072">Allowed From</span></span>

<span data-ttu-id="6a191-1073">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-1073">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-1074">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-1074">Example</span></span>

```c
/* Start register.  */
status = nx_lwm2m_client_session_register (&lwm2m_client, 123, &ip_address, 5683);

/* If status is NX_SUCCESS, start register successfully.  */
```

## <a name="nx_lwm2m_client_session_register_dtls"></a><span data-ttu-id="6a191-1075">nx_lwm2m_client_session_register_dtls</span><span class="sxs-lookup"><span data-stu-id="6a191-1075">nx_lwm2m_client_session_register_dtls</span></span>

<span data-ttu-id="6a191-1076">Запускает безопасный сеанс с сервером LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-1076">Starts a secure session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-1077">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-1077">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID server_id, 
    ULONG ip_address, 
    UINT port,
    NX_SECURE_DTLS_SESSION *dtls_session_ptr);
```

### <a name="description"></a><span data-ttu-id="6a191-1078">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-1078">Description</span></span>

<span data-ttu-id="6a191-1079">Данная служба выполняет операцию «Регистрация» на сервере LWM2M, используя безопасное соединение DTLS.</span><span class="sxs-lookup"><span data-stu-id="6a191-1079">This service performs a ‘Register’ operation to a LWM2M Server using a secure DTLS connection.</span></span> <span data-ttu-id="6a191-1080">Сервер должен иметь соответствующий экземпляр сервера в объекте сервера.</span><span class="sxs-lookup"><span data-stu-id="6a191-1080">The server must have a corresponding server instance in the Server Object.</span></span>

<span data-ttu-id="6a191-1081">Перед вызовом данной функции сеанс протокола DTLS должен быть настроен с использованием надлежащих наборов шифров и ключевого материала.</span><span class="sxs-lookup"><span data-stu-id="6a191-1081">The DTLS session must have been configured with the proper cipher suites and key material before calling this function.</span></span> <span data-ttu-id="6a191-1082">Необходимо определить **NX_SECURE_ENABLE_DTLS**.</span><span class="sxs-lookup"><span data-stu-id="6a191-1082">**NX_SECURE_ENABLE_DTLS** must be defined.</span></span>

<span data-ttu-id="6a191-1083">Если регистрация прошла успешно, клиент LWM2M будет обрабатывать дальнейшие операции с сервера и периодически отправлять сообщения «Обновить» до момента отмены регистрации клиента.</span><span class="sxs-lookup"><span data-stu-id="6a191-1083">If the registration is successfully the LWM2M Client will process further operations from the server and will periodically send ‘Update’ messages until the client is de-registered.</span></span>

<span data-ttu-id="6a191-1084">Любой текущий активный сеанс прерывается этим вызовом и заменяется новым сеансом LWM2M Server.</span><span class="sxs-lookup"><span data-stu-id="6a191-1084">Any current active session is aborted by this call and replaced by the new LWM2M Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-1085">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-1085">Parameters</span></span>

- <span data-ttu-id="6a191-1086">**session_ptr** Указатель на блок управления сеансом клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-1086">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="6a191-1087">**server_id** Краткий идентификатор сервера LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-1087">**server_id** The Short Server ID of the LWM2M Server.</span></span>
- <span data-ttu-id="6a191-1088">**ip_address** IP-адрес сервера.</span><span class="sxs-lookup"><span data-stu-id="6a191-1088">**ip_address** The IP address of the server.</span></span>
- <span data-ttu-id="6a191-1089">**port** UDP-порт сервера.</span><span class="sxs-lookup"><span data-stu-id="6a191-1089">**port** The UDP port of the server.</span></span>
- <span data-ttu-id="6a191-1090">**dtls_session_ptr** Сеанс протокола DTLS, используемый для сеанса LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-1090">**dtls_session_ptr** The DTLS session to use for the LWM2M session.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-1091">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-1091">Return Values</span></span>

- <span data-ttu-id="6a191-1092">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-1092">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-1093">**NX_LWM2M_CLIENT_ERROR** Ошибка начальной загрузки.</span><span class="sxs-lookup"><span data-stu-id="6a191-1093">**NX_LWM2M_CLIENT_ERROR** Bootstrap error.</span></span>
- <span data-ttu-id="6a191-1094">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Порт недоступен.</span><span class="sxs-lookup"><span data-stu-id="6a191-1094">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="6a191-1095">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-1095">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-1096">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-1096">Allowed From</span></span>

<span data-ttu-id="6a191-1097">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-1097">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-1098">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-1098">Example</span></span>

```c
/* Start register with DTLS.  */
status = nx_lwm2m_client_session_register_dtls(&lwm2m_client, 123, &ip_address, 5683, &dtls_session);

/* If status is NX_SUCCESS, start register with DTLS successfully.  */
```

## <a name="nx_lwm2m_client_session_register_info_get"></a><span data-ttu-id="6a191-1099">nx_lwm2m_client_session_register_info_get</span><span class="sxs-lookup"><span data-stu-id="6a191-1099">nx_lwm2m_client_session_register_info_get</span></span>

<span data-ttu-id="6a191-1100">Запускает безопасный сеанс с сервером LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-1100">Starts a secure session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-1101">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-1101">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    UINT security_instance_id, 
    NX_LWM2M_ID *server_id,
    CHAR **server_uri, 
    UINT *server_uri_length, 
    UCHAR *security_mode, 
    UCHAR **pub_key_or_id, 
    UINT *pub_key_or_id_len, 
    UCHAR **server_pub_key, 
    UINT *server_pub_key_len, 
    UCHAR **secret_key, 
    UINT *secret_key_len);
```

### <a name="description"></a><span data-ttu-id="6a191-1102">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-1102">Description</span></span>

<span data-ttu-id="6a191-1103">После установления сеанса связи с сервером начальной загрузки.</span><span class="sxs-lookup"><span data-stu-id="6a191-1103">Once a communication session with a Bootstrap server was established.</span></span> <span data-ttu-id="6a191-1104">Приложение может вызвать данный API для получения информации о сервере и безопасности для следующего шага регистрации.</span><span class="sxs-lookup"><span data-stu-id="6a191-1104">Application can call this api to get the server and security information for the next registration step.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-1105">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-1105">Parameters</span></span>

- <span data-ttu-id="6a191-1106">**session_ptr** Указатель на блок управления сеансом клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-1106">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="6a191-1107">**security_instance_id** Идентификатор экземпляра безопасности.</span><span class="sxs-lookup"><span data-stu-id="6a191-1107">**security_instance_id** Security instance ID.</span></span>
- <span data-ttu-id="6a191-1108">**server_id** Указатель на идентификатор целевого сервера.</span><span class="sxs-lookup"><span data-stu-id="6a191-1108">**server_id** Pointer to destination server ID.</span></span>
- <span data-ttu-id="6a191-1109">**server_uri** Указатель на URI-идентификатор сервера назначения.</span><span class="sxs-lookup"><span data-stu-id="6a191-1109">**server_uri** Pointer to destination server uri.</span></span>
- <span data-ttu-id="6a191-1110">**server_uri_len** Указатель на длину URI-идентификатора сервера назначения.</span><span class="sxs-lookup"><span data-stu-id="6a191-1110">**server_uri_len** Pointer to destination server uri length.</span></span>
- <span data-ttu-id="6a191-1111">**security_mode** Указатель на режим безопасности назначения.</span><span class="sxs-lookup"><span data-stu-id="6a191-1111">**security_mode** Pointer to destination security mode.</span></span>
- <span data-ttu-id="6a191-1112">**pub_key_or_id** Указатель на открытый ключ или идентификатор назначения.</span><span class="sxs-lookup"><span data-stu-id="6a191-1112">**pub_key_or_id** Pointer to destination public key or identity.</span></span>
- <span data-ttu-id="6a191-1113">**pub_key_or_id_len** Указатель на открытый ключ назначения или длину идентификатора.</span><span class="sxs-lookup"><span data-stu-id="6a191-1113">**pub_key_or_id_len** Pointer to destination public key or identity length.</span></span>
- <span data-ttu-id="6a191-1114">**server_pub_key** Указатель на открытый ключ целевого сервера.</span><span class="sxs-lookup"><span data-stu-id="6a191-1114">**server_pub_key** Pointer to destination server public key.</span></span>
- <span data-ttu-id="6a191-1115">**server_pub_key_len** Указатель на длину открытого ключа целевого сервера.</span><span class="sxs-lookup"><span data-stu-id="6a191-1115">**server_pub_key_len** Pointer to destination server public key length.</span></span>
- <span data-ttu-id="6a191-1116">**secret_key** Указатель на секретный ключ назначения.</span><span class="sxs-lookup"><span data-stu-id="6a191-1116">**secret_key** Pointer to destination secret key.</span></span>
- <span data-ttu-id="6a191-1117">**secret_key_len** Указатель на длину секретного ключа назначения.</span><span class="sxs-lookup"><span data-stu-id="6a191-1117">**secret_key_len** Pointer to destination secret key length.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-1118">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-1118">Return Values</span></span>

- <span data-ttu-id="6a191-1119">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-1119">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-1120">**NX_LWM2M_CLIENT_NOT_FOUND** Экземпляр объекта безопасности отсутствует.</span><span class="sxs-lookup"><span data-stu-id="6a191-1120">**NX_LWM2M_CLIENT_NOT_FOUND** There is no security Object instance.</span></span>
- <span data-ttu-id="6a191-1121">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-1121">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-1122">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-1122">Allowed From</span></span>

<span data-ttu-id="6a191-1123">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-1123">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-1124">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-1124">Example</span></span>

```c
/* Get the register information.  */
status = nx_lwm2m_client_session_register_info_get(&session, NX_LWM2M_CLIENT_RESERVED_ID, &server_id, &server_uri, &server_uri_length, &security_mode, &pub_key_or_id, &pub_key_or_id_len, NX_NULL, NX_NULL, &secret_key, &secret_key_len);

/* If status is NX_SUCCESS, the register information was successfully gotten.  */
```

## <a name="nx_lwm2m_client_session_update"></a><span data-ttu-id="6a191-1125">nx_lwm2m_client_session_update</span><span class="sxs-lookup"><span data-stu-id="6a191-1125">nx_lwm2m_client_session_update</span></span>

<span data-ttu-id="6a191-1126">Обновляет сеанс с сервером LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-1126">Updates a session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-1127">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-1127">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_update(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="6a191-1128">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-1128">Description</span></span>

<span data-ttu-id="6a191-1129">Данная служба выполняет операцию «Обновить» на сервере LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-1129">This service performs an ‘Update’ operation to a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-1130">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-1130">Parameters</span></span>

- <span data-ttu-id="6a191-1131">**session_ptr** Указатель на блок управления сеансом клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-1131">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-1132">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-1132">Return Values</span></span>

- <span data-ttu-id="6a191-1133">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-1133">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-1134">**NX_LWM2M_CLIENT_NOT_REGISTERED** Клиент не зарегистрирован на сервере.</span><span class="sxs-lookup"><span data-stu-id="6a191-1134">**NX_LWM2M_CLIENT_NOT_REGISTERED** The client is not registered to the server.</span></span>
- <span data-ttu-id="6a191-1135">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-1135">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-1136">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-1136">Allowed From</span></span>

<span data-ttu-id="6a191-1137">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-1137">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-1138">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-1138">Example</span></span>

```c
/* Update a session.  */
status = nx_lwm2m_client_session_update(&session);

/* If status is NX_SUCCESS, a session was successfully updated.  */
```

## <a name="nx_lwm2m_client_unlock"></a><span data-ttu-id="6a191-1139">nx_lwm2m_client_unlock</span><span class="sxs-lookup"><span data-stu-id="6a191-1139">nx_lwm2m_client_unlock</span></span>

<span data-ttu-id="6a191-1140">Разблокирует клиент LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-1140">Unlocks a LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="6a191-1141">Прототип</span><span class="sxs-lookup"><span data-stu-id="6a191-1141">Prototype</span></span>

```c
UINT nx_lwm2m_client_unlock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="6a191-1142">Описание</span><span class="sxs-lookup"><span data-stu-id="6a191-1142">Description</span></span>

<span data-ttu-id="6a191-1143">Данная служба разблокирует клиент LWM2M, ранее заблокированный вызовом ***nx_lwm2m_client_unlock***.</span><span class="sxs-lookup"><span data-stu-id="6a191-1143">This service unlocks the LWM2M Client previously locked by a call to ***nx_lwm2m_client_unlock***.</span></span>

### <a name="parameters"></a><span data-ttu-id="6a191-1144">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a191-1144">Parameters</span></span>

- <span data-ttu-id="6a191-1145">**client_ptr** Указатель на блок управления клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6a191-1145">**client_ptr** Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="6a191-1146">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="6a191-1146">Return Values</span></span>

- <span data-ttu-id="6a191-1147">**NX_SUCCESS** Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6a191-1147">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="6a191-1148">**NX_PTR_ERROR** Недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="6a191-1148">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6a191-1149">Разрешено с</span><span class="sxs-lookup"><span data-stu-id="6a191-1149">Allowed From</span></span>

<span data-ttu-id="6a191-1150">Потоки, Инициализация</span><span class="sxs-lookup"><span data-stu-id="6a191-1150">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6a191-1151">Пример</span><span class="sxs-lookup"><span data-stu-id="6a191-1151">Example</span></span>

```c
/* Unlock lwm2m client.  */
status = nx_lwm2m_client_unlock(&lwm2m_client);

/* If status is NX_SUCCESS, unlock lwm2m client successfully.  */
```