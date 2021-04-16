---
title: Глава 3. Функциональное описание NetX LWM2M для ОСРВ Azure
description: Эта глава содержит функциональное описание NetX LWM2M для ОСРВ Azure.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f49a4f5f4c899dfa461a9d57a8b56e4503d6acd4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815172"
---
# <a name="chapter-3---functional-description-of-azure-rtos-netx-lwm2m"></a><span data-ttu-id="70e0c-103">Глава 3. Функциональное описание NetX LWM2M для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="70e0c-103">Chapter 3 - Functional description of Azure RTOS NetX LWM2M</span></span>

<span data-ttu-id="70e0c-104">Эта глава содержит функциональное описание NetX LWM2M для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="70e0c-104">This chapter contains a functional description of Azure RTOS NetX LWM2M.</span></span>

## <a name="lwm2m-client-initialization"></a><span data-ttu-id="70e0c-105">Инициализация клиента LWM2M</span><span class="sxs-lookup"><span data-stu-id="70e0c-105">LWM2M Client Initialization</span></span>

<span data-ttu-id="70e0c-106">Клиент LWM2M инициализируется путем вызова службы ***nx_lwm2m_client_create***.</span><span class="sxs-lookup"><span data-stu-id="70e0c-106">The LWM2M Client is initialized by calling ***nx_lwm2m_client_create*** service.</span></span> <span data-ttu-id="70e0c-107">Клиент LWM2M работает в отдельном потоке и может передавать в приложение некоторые события с помощью обратных вызовов или путем вызова методов из пользовательских объектов, реализованных в приложении.</span><span class="sxs-lookup"><span data-stu-id="70e0c-107">The LWM2M Client runs in its own thread and can report some events to the application through the use of callbacks, or by calling methods of the custom objects implemented by the application.</span></span>

<span data-ttu-id="70e0c-108">Кроме того, для поддержки связи с одним или несколькими серверами следует создавать сеансы клиента LWM2M путем вызова ***nx_lwm2m_client_session_create***.</span><span class="sxs-lookup"><span data-stu-id="70e0c-108">In addition, LWM2M Client Sessions must be created by calling ***nx_lwm2m_client_session_create*** for enabling communication with one or more servers.</span></span> <span data-ttu-id="70e0c-109">Каждый сеанс может взаимодействовать с серверами двух разных типов: сервер начальной загрузки или сервер LWM2M (управление устройством).</span><span class="sxs-lookup"><span data-stu-id="70e0c-109">A session can communicate with two different types of servers: a Bootstrap Server or a LWM2M Server (Device Management).</span></span>

### <a name="bootstrap-server-session"></a><span data-ttu-id="70e0c-110">Сеанс сервера начальной загрузки</span><span class="sxs-lookup"><span data-stu-id="70e0c-110">Bootstrap Server Session</span></span>

<span data-ttu-id="70e0c-111">Сеанс связи с сервером начальной загрузки позволяет предоставить клиенту LWM2M информацию, которая ему необходима для регистрации на одном или нескольких серверах LWM2M.</span><span class="sxs-lookup"><span data-stu-id="70e0c-111">A communication session with a Bootstrap Server is used to provision essential information into the LWM2M Client to enable the LWM2M Client to perform the operation "Register" with one or more LWM2M Servers.</span></span> <span data-ttu-id="70e0c-112">Этот тип сервера используется в режимах начальной загрузки, инициируемой клиентом и инициируемой сервером.</span><span class="sxs-lookup"><span data-stu-id="70e0c-112">This type of server is used during the Client Initiated and Server Initiated Bootstrap modes.</span></span>

<span data-ttu-id="70e0c-113">Приложение может запустить сеанс начальной загрузки путем вызова ***nx_lwm2m_client_session_bootstrap** _ или _*_nx_lwm2m_client_session_bootstrap_dtls_\*_, в которых нужно предоставить IP-адрес и номер порта сервера, а также необязательный идентификатор экземпляра объекта безопасности.</span><span class="sxs-lookup"><span data-stu-id="70e0c-113">The application can start a Bootstrap session by calling ***nx_lwm2m_client_session_bootstrap** _ or _*_nx_lwm2m_client_session_bootstrap_dtls_\*_, it must provide the IP address and port number of the server, and an optional Security Object Instance ID.</span></span> <span data-ttu-id="70e0c-114">Функция _*_nx_lwm2m_client_session_bootstrap_*_ использует обмен данными без защиты, а _ *_nx_lwm2m_client_session_bootstrap_dtls_*\* создает безопасное подключение к серверу по протоколу DTLS.</span><span class="sxs-lookup"><span data-stu-id="70e0c-114">The _*_nx_lwm2m_client_session_bootstrap_*_ function uses insecure communication, whereas _ *_nx_lwm2m_client_session_bootstrap_dtls_*\* establishes a secure DTLS connection with the server.</span></span>

<span data-ttu-id="70e0c-115">Если операция начальной загрузки выполняется успешно, на сервере начальной загрузки должны быть созданы экземпляры объектов безопасности для серверов начальной загрузки и LWM2M, а также экземпляры объектов для серверов LWM2M.</span><span class="sxs-lookup"><span data-stu-id="70e0c-115">If the Bootstrap operation is successful, the Bootstrap server should have created Security Object Instance(s) for the Bootstrap and LWM2M Servers, and Server Object Instance(s) for the LWM2M Servers.</span></span> <span data-ttu-id="70e0c-116">Эти сведения приложение должно использовать для создания сеанса связи с серверами LWM2M.</span><span class="sxs-lookup"><span data-stu-id="70e0c-116">The application must use this information for establishing a session with the LWM2M Server(s).</span></span>

<span data-ttu-id="70e0c-117">Данные начальной загрузки должны сохраняться приложением в долговременной памяти, чтобы получить возможность создать клиент LWM2M после следующей перезагрузки устройства.</span><span class="sxs-lookup"><span data-stu-id="70e0c-117">The Bootstrap data should be saved to non-volatile memory by the application in order to configure the LWM2M Client at the next reboot of the device.</span></span>

### <a name="lwm2m-server-session"></a><span data-ttu-id="70e0c-118">Сеанс сервера LWM2M</span><span class="sxs-lookup"><span data-stu-id="70e0c-118">LWM2M Server Session</span></span>

<span data-ttu-id="70e0c-119">Сеанс связи с сервером LWM2M используется для регистрации, управления устройствами и включения службы.</span><span class="sxs-lookup"><span data-stu-id="70e0c-119">A communication session with a LWM2M Server is used for Registration, Device Management and Service Enablement.</span></span>

<span data-ttu-id="70e0c-120">Приложение может зарегистрировать клиент LWM2M на сервере, вызвав ***nx_lwm2m_client_session_register** _ или _*_nx_lwm2m_client_session_register_dtls_\*_, в которых нужно предоставить IP-адрес и номер порта сервера, а также короткий идентификатор сервера, соответствующий существующему экземпляру объекта сервера.</span><span class="sxs-lookup"><span data-stu-id="70e0c-120">The application can register the LWM2M Client to a server by calling ***nx_lwm2m_client_session_register** _ or _*_nx_lwm2m_client_session_register_dtls_\*_, it must provide the IP address and port number of the server, and the Short Server ID which corresponds to an existing Server Object Instance.</span></span> <span data-ttu-id="70e0c-121">Функция _*_nx_lwm2m_client_session_register_*_ использует обмен данными без защиты, а _ *_nx_lwm2m_client_session_register_dtls_*\* создает безопасное подключение к серверу по протоколу DTLS.</span><span class="sxs-lookup"><span data-stu-id="70e0c-121">The _*_nx_lwm2m_client_session_register_*_ function uses insecure communication, whereas _ *_nx_lwm2m_client_session_register_dtls_*\* establishes a secure DTLS connection with the server.</span></span>

<span data-ttu-id="70e0c-122">Приложение может отменить регистрацию клиента LWM2M, вызвав ***nx_lwm2m_client_session_deregister** _, и попросить клиента отправить сообщение обновления (Update), вызвав _*_nx_lwm2m_client_session_update_\*\*.</span><span class="sxs-lookup"><span data-stu-id="70e0c-122">The application can de-register the LWM2M Client by calling ***nx_lwm2m_client_session_deregister** _, and ask the client to send an 'Update' message by calling _*_nx_lwm2m_client_session_update_\*\*.</span></span>

### <a name="session-state-callback"></a><span data-ttu-id="70e0c-123">Обратный вызов состояния сеанса</span><span class="sxs-lookup"><span data-stu-id="70e0c-123">Session State Callback</span></span>

<span data-ttu-id="70e0c-124">Приложение регистрирует при создании сеанса обратный вызов, который вызывается при обновлении состояния сеанса. Функция обратного вызова NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK имеет следующий прототип:</span><span class="sxs-lookup"><span data-stu-id="70e0c-124">The application registers a callback at creation of a session which is called when the state of the session is updated, the callback function NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK has the following prototype:</span></span>

```c
typedef VOID (*NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)
        (NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state);
```

<span data-ttu-id="70e0c-125">Определены следующие состояния:</span><span class="sxs-lookup"><span data-stu-id="70e0c-125">The following states are defined :</span></span>

- <span data-ttu-id="70e0c-126">**NX_LWM2M_CLIENT_SESSION_INIT**: исходное состояние после создания сеанса.</span><span class="sxs-lookup"><span data-stu-id="70e0c-126">**NX_LWM2M_CLIENT_SESSION_INIT**: The initial state after session creation.</span></span>

- <span data-ttu-id="70e0c-127">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING**: клиент ожидает истечения срока таймера задержки (Hold Off) или инициируемой сервером начальной загрузки.</span><span class="sxs-lookup"><span data-stu-id="70e0c-127">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING**: The client is waiting for the expiration of the 'Hold Off' timer or Server Initiated Bootstrap.</span></span>

- <span data-ttu-id="70e0c-128">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING**: клиент отправил сообщение запроса (Request) на сервер начальной загрузки (инициируемая клиентом начальная загрузка).</span><span class="sxs-lookup"><span data-stu-id="70e0c-128">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING**: The client has sent a 'Request' message to the Bootstrap Server (Client Initiated Bootstrap).</span></span>

- <span data-ttu-id="70e0c-129">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED**: клиент получает данные от сервера начальной загрузки.</span><span class="sxs-lookup"><span data-stu-id="70e0c-129">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED**: The client is receiving data from the Bootstrap Server.</span></span>

- <span data-ttu-id="70e0c-130">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED**: сервер начальной загрузки отправил сообщение завершения (Finished).</span><span class="sxs-lookup"><span data-stu-id="70e0c-130">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED**: The Bootstrap Server has sent a 'Finished' message.</span></span>

- <span data-ttu-id="70e0c-131">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR**: сеанс начальной загрузки завершился сбоем.</span><span class="sxs-lookup"><span data-stu-id="70e0c-131">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR**: The bootstrap session has failed.</span></span>

- <span data-ttu-id="70e0c-132">**NX_LWM2M_CLIENT_SESSION_REGISTERING**: клиент отправил сообщение о регистрации (Register) на сервер LWM2M.</span><span class="sxs-lookup"><span data-stu-id="70e0c-132">**NX_LWM2M_CLIENT_SESSION_REGISTERING**: The client has sent a 'Register' message to the LWM2M Server.</span></span>

- <span data-ttu-id="70e0c-133">**NX_LWM2M_CLIENT_SESSION_REGISTERED**: клиент успешно зарегистрировался на сервере LWM2M.</span><span class="sxs-lookup"><span data-stu-id="70e0c-133">**NX_LWM2M_CLIENT_SESSION_REGISTERED**: The client is registered to the LWM2M Server.</span></span>

- <span data-ttu-id="70e0c-134">**NX_LWM2M_CLIENT_SESSION_UPDATING**: клиент отправил сообщение обновления (Update) на сервер LWM2M.</span><span class="sxs-lookup"><span data-stu-id="70e0c-134">**NX_LWM2M_CLIENT_SESSION_UPDATING**: The client has sent an 'Update' message to the LWM2M Server.</span></span>

- <span data-ttu-id="70e0c-135">**NX_LWM2M_CLIENT_SESSION_DEREGISTERING**: клиент отправил сообщение отмены регистрации (De-register) на сервер LWM2M.</span><span class="sxs-lookup"><span data-stu-id="70e0c-135">**NX_LWM2M_CLIENT_SESSION_DEREGISTERING**: The client has sent an 'De-register' message to the LWM2M Server.</span></span>

- <span data-ttu-id="70e0c-136">**NX_LWM2M_CLIENT_SESSION_DEREGISTERED**: клиент успешно отменил регистрацию на сервере LWM2M.</span><span class="sxs-lookup"><span data-stu-id="70e0c-136">**NX_LWM2M_CLIENT_SESSION_DEREGISTERED**: The client is de-registered from the LWM2M Server.</span></span>

- <span data-ttu-id="70e0c-137">**NX_LWM2M_CLIENT_SESSION_DISABLED**: сервер LWM2M отключен.</span><span class="sxs-lookup"><span data-stu-id="70e0c-137">**NX_LWM2M_CLIENT_SESSION_DISABLED**: The LWM2M Server is disabled.</span></span> <span data-ttu-id="70e0c-138">Когда срок действия таймера отключения истечет, будет отправлено сообщение о регистрации.</span><span class="sxs-lookup"><span data-stu-id="70e0c-138">A 'Register' will be sent after the expiration of the disable timer.</span></span>

- <span data-ttu-id="70e0c-139">**NX_LWM2M_CLIENT_SESSION_ERROR**: операция регистрации или обновления на сервере LWM2M завершилась сбоем.</span><span class="sxs-lookup"><span data-stu-id="70e0c-139">**NX_LWM2M_CLIENT_SESSION_ERROR**: The registration or update operation to the LWM2M Server has failed.</span></span>

- <span data-ttu-id="70e0c-140">**NX_LWM2M_CLIENT_SESSION_DELETED**: удален экземпляр объекта сервера, соответствующий серверу LWM2M.</span><span class="sxs-lookup"><span data-stu-id="70e0c-140">**NX_LWM2M_CLIENT_SESSION_DELETED**: The Server Object Instance corresponding to the LWM2M Server has been deleted.</span></span> <span data-ttu-id="70e0c-141">В случае ошибки приложение может выяснить причину ошибки, вызвав **_nx_lwm2m_client_session_error_get_**.</span><span class="sxs-lookup"><span data-stu-id="70e0c-141">In case of error the application can retrieve the cause of the error by calling **_nx_lwm2m_client_session_error_get_**.</span></span>

## <a name="local-device-management"></a><span data-ttu-id="70e0c-142">Управление локальным устройством</span><span class="sxs-lookup"><span data-stu-id="70e0c-142">Local Device Management</span></span>

<span data-ttu-id="70e0c-143">Приложение может получить доступ к объектам клиента LWM2M с помощью функций управления локальным устройством.</span><span class="sxs-lookup"><span data-stu-id="70e0c-143">The application can access the Objects of the LWM2M Client by using the local device management functions.</span></span> <span data-ttu-id="70e0c-144">Для этого предлагаются следующие функции:</span><span class="sxs-lookup"><span data-stu-id="70e0c-144">The following functions are provided:</span></span>

- <span data-ttu-id="70e0c-145">***nx_lwm2m_client_object_read***: чтение ресурсов из экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="70e0c-145">***nx_lwm2m_client_object_read***: Read resources from an Object Instance.</span></span>

- <span data-ttu-id="70e0c-146">***nx_lwm2m_client_object_discover***: получение списка ресурсов из экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="70e0c-146">***nx_lwm2m_client_object_discover***: Get the list of the resources of an Object Instance.</span></span>

- <span data-ttu-id="70e0c-147">***nx_lwm2m_client_object_read***: запись ресурсов в экземпляр объекта.</span><span class="sxs-lookup"><span data-stu-id="70e0c-147">***nx_lwm2m_client_object_write***: Write resources to an Object Instance</span></span>

- <span data-ttu-id="70e0c-148">***nx_lwm2m_client_object_execute***: выполнение операции Execute для ресурса в экземпляре объекта.</span><span class="sxs-lookup"><span data-stu-id="70e0c-148">***nx_lwm2m_client_object_execute***: Perform the Execute operation on a resource of an Object Instance.</span></span>

- <span data-ttu-id="70e0c-149">***nx_lwm2m_client_object_create***: создание экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="70e0c-149">***nx_lwm2m_client_object_create***: Create a new Object Instance.</span></span>

- <span data-ttu-id="70e0c-150">***nx_lwm2m_client_object_delete***: удаление существующего экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="70e0c-150">***nx_lwm2m_client_object_delete***: Delete an existing Object Instance.</span></span>

- <span data-ttu-id="70e0c-151">***nx_lwm2m_client_object_get_next***: получение следующего идентификатора объекта, реализованного клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="70e0c-151">***nx_lwm2m_client_object_get_next***: Get the next Object ID implemented by the LWM2M Client.</span></span>

- <span data-ttu-id="70e0c-152">***nx_lwm2m_client_object_instance_get_next***: получение следующего экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="70e0c-152">***nx_lwm2m_client_object_instance_get_next***: Get the next Instance of an Object.</span></span>

## <a name="resource-information"></a><span data-ttu-id="70e0c-153">Сведения о ресурсе</span><span class="sxs-lookup"><span data-stu-id="70e0c-153">Resource Information</span></span>

<span data-ttu-id="70e0c-154">При операциях чтения и записи в объекте ресурс представляется структурой NX_LWM2M_RESOURCE.</span><span class="sxs-lookup"><span data-stu-id="70e0c-154">When reading from and writing to Objects a Resource is represented by the NX_LWM2M_RESOURCE structure.</span></span> <span data-ttu-id="70e0c-155">Эта структура содержит идентификатор ресурса или экземпляра и соответствующее значение.</span><span class="sxs-lookup"><span data-stu-id="70e0c-155">This structure contains the ID of the Resource/Instance and its value.</span></span> <span data-ttu-id="70e0c-156">Используемая для этого значения кодировка зависит от типа значения и его происхождения (от приложения или из сети).</span><span class="sxs-lookup"><span data-stu-id="70e0c-156">The encoding of the value depends on its type and its origin (application or network).</span></span>

<span data-ttu-id="70e0c-157">Структура NX_LWM2M_RESOURCE имеет следующее определение:</span><span class="sxs-lookup"><span data-stu-id="70e0c-157">The NX_LWM2M_RESOURCE structure has the following definition:</span></span>

```c
typedef struct NX_LWM2M_RESOURCE_STRUCT
{
    NX_LWM2M_ID     nx_lwm2m_resource_id;
    UCHAR           nx_lwm2m_resource_type;
    union
    {
        struct
        {
            const VOID *     nx_lwm2m_resource_buffer_ptr;
            UINT             nx_lwm2m_resource_buffer_length;
        } nx_lwm2m_resource_bufferdata;
        const CHAR *         nx_lwm2m_resource_stringdata;
        NX_LWM2M_INT32       nx_lwm2m_resource_integer32data;
        NX_LWM2M_INT64       nx_lwm2m_resource_integer64data;
        NX_LWM2M_FLOAT32     nx_lwm2m_resource_float32data;
        NX_LWM2M_FLOAT64     nx_lwm2m_resource_float64data;
        NX_LWM2M_BOOL        nx_lwm2m_resource_booleandata;
        NX_LWM2M_OBJLNK      nx_lwm2m_resource_objlnkdata;
        
        struct
        {
            const VOID *     nx_lwm2m_resource_multiple_ptr;
            UINT             nx_lwm2m_resource_multiple_dim;
        } nx_lwm2m_resource_multipledata;
    } nx_lwm2m_resource_value;
} NX_LWM2M_RESOURCE;
```

- <span data-ttu-id="70e0c-158">**nx_lwm2m_resource_id**: идентификатор ресурса или экземпляра.</span><span class="sxs-lookup"><span data-stu-id="70e0c-158">**nx_lwm2m_resource_id**: The ID of the Resource or the Instance.</span></span>
- <span data-ttu-id="70e0c-159">**nx_lwm2m_resource_type**: тип значения (возможные варианты см. ниже).</span><span class="sxs-lookup"><span data-stu-id="70e0c-159">**nx_lwm2m_resource_type**: The type of the value, see below.</span></span>
- <span data-ttu-id="70e0c-160">**nx_lwm2m_resource_value**: значение ресурса с учетом типа этого значения.</span><span class="sxs-lookup"><span data-stu-id="70e0c-160">**nx_lwm2m_resource_value**: The value of the Resource, depends on the type of the value.</span></span>

<span data-ttu-id="70e0c-161">Определены следующие типы значений:</span><span class="sxs-lookup"><span data-stu-id="70e0c-161">The following type of values are defined :</span></span>

- <span data-ttu-id="70e0c-162">**NX_LWM2M_RESOURCE_NONE**: пустой ресурс.</span><span class="sxs-lookup"><span data-stu-id="70e0c-162">**NX_LWM2M_RESOURCE_NONE**: Empty resource.</span></span>

- <span data-ttu-id="70e0c-163">**NX_LWM2M_RESOURCE_STRING**: строковое значение UTF-8, которое оканчивается символом NULL, сохраненное в *nx_lwm2m_resource_stringdata*.</span><span class="sxs-lookup"><span data-stu-id="70e0c-163">**NX_LWM2M_RESOURCE_STRING**: A null-terminated UTF-8 string value stored in *nx_lwm2m_resource_stringdata*.</span></span>

- <span data-ttu-id="70e0c-164">**NX_LWM2M_RESOURCE_INTEGER32**: 32-разрядное целое число, сохраненное в *nx_lwm2m_resource_integer32data*.</span><span class="sxs-lookup"><span data-stu-id="70e0c-164">**NX_LWM2M_RESOURCE_INTEGER32**: A 32-Bit Integer value stored in *nx_lwm2m_resource_integer32data*.</span></span>

- <span data-ttu-id="70e0c-165">**NX_LWM2M_RESOURCE_INTEGER64**: 64-разрядное целое число, сохраненное в *nx_lwm2m_resource_integer64data*.</span><span class="sxs-lookup"><span data-stu-id="70e0c-165">**NX_LWM2M_RESOURCE_INTEGER64**: A 64-Bit Integer value stored in *nx_lwm2m_resource_integer64data*.</span></span>

- <span data-ttu-id="70e0c-166">**NX_LWM2M_RESOURCE_FLOAT32**: 32-разрядное число с плавающей запятой, сохраненное в *nx_lwm2m_resource_float32data*.</span><span class="sxs-lookup"><span data-stu-id="70e0c-166">**NX_LWM2M_RESOURCE_FLOAT32**: A 32-Bit Floating Point value stored in *nx_lwm2m_resource_float32data*.</span></span>

- <span data-ttu-id="70e0c-167">**NX_LWM2M_RESOURCE_FLOAT64**: 64-разрядное число с плавающей точкой, сохраненное в *nx_lwm2m_resource_float64data*.</span><span class="sxs-lookup"><span data-stu-id="70e0c-167">**NX_LWM2M_RESOURCE_FLOAT64**: A 64-Bit Floating Point value stored in *nx_lwm2m_resource_float64data*.</span></span>

- <span data-ttu-id="70e0c-168">**NX_LWM2M_RESOURCE_BOOLEAN**: логическое значение, сохраненное в *nx_lwm2m_resource_booleandata*.</span><span class="sxs-lookup"><span data-stu-id="70e0c-168">**NX_LWM2M_RESOURCE_BOOLEAN**: A Boolean value stored in *nx_lwm2m_resource_booleandata*.</span></span>

- <span data-ttu-id="70e0c-169">**NX_LWM2M_RESOURCE_OPAQUE**: значение Opaque, определенное в *nx_lwm2m_resource_bufferdata*.</span><span class="sxs-lookup"><span data-stu-id="70e0c-169">**NX_LWM2M_RESOURCE_OPAQUE**: An Opaque value defined by *nx_lwm2m_resource_bufferdata*.</span></span>

- <span data-ttu-id="70e0c-170">**NX_LWM2M_RESOURCE_OBJLNK**: значение ссылки на объект, сохраненное в *nx_lwm2m_resource_objlnkdata*.</span><span class="sxs-lookup"><span data-stu-id="70e0c-170">**NX_LWM2M_RESOURCE_OBJLNK**: An Object Link value stored in *nx_lwm2m_resource_objlnkdata*.</span></span>

- <span data-ttu-id="70e0c-171">**NX_LWM2M_RESOURCE_TLV**: значение в кодировке TLV, определенное в *nx_lwm2m_resource_bufferdata*.</span><span class="sxs-lookup"><span data-stu-id="70e0c-171">**NX_LWM2M_RESOURCE_TLV**: A TLV encoded value defined by *nx_lwm2m_resource_bufferdata*.</span></span>

- <span data-ttu-id="70e0c-172">**NX_LWM2M_RESOURCE_TEXT**: значение в формате простого текста, определенное в *nx_lwm2m_resource_bufferdata*.</span><span class="sxs-lookup"><span data-stu-id="70e0c-172">**NX_LWM2M_RESOURCE_TEXT**: A Plain-Text encoded value defined by *nx_lwm2m_resource_bufferdata*.</span></span>

- <span data-ttu-id="70e0c-173">**NX_LWM2M_RESOURCE_MULTIPLE**: ресурс с несколькими типами данных, определенный в *nx_lwm2m_resource_multipledata*.</span><span class="sxs-lookup"><span data-stu-id="70e0c-173">**NX_LWM2M_RESOURCE_MULTIPLE**: A Multiple Resource defined by *nx_lwm2m_resource_multipledata*.</span></span> <span data-ttu-id="70e0c-174">*nx_lwm2m_resource_multiple_ptr* содержит указатель на массив структур **NX_LWM2M_RESOURCE**, которые содержат информацию о каждом экземпляре ресурса.</span><span class="sxs-lookup"><span data-stu-id="70e0c-174">*nx_lwm2m_resource_multiple_ptr* is a pointer to an array of **NX_LWM2M_RESOURCE** structures containing information about each Resource Instances.</span></span>

- <span data-ttu-id="70e0c-175">**NX_LWM2M_RESOURCE_MULTIPLE_TLV**: ресурс с несколькими типами данных, определенный в *nx_lwm2m_resource_multipledata*.</span><span class="sxs-lookup"><span data-stu-id="70e0c-175">**NX_LWM2M_RESOURCE_MULTIPLE_TLV**: A Multiple Resource defined by *nx_lwm2m_resource_multipledata*.</span></span> <span data-ttu-id="70e0c-176">*nx_lwm2m_resource_multiple_ptr* содержит указатель на буфер в кодировке TLV.</span><span class="sxs-lookup"><span data-stu-id="70e0c-176">*nx_lwm2m_resource_multiple_ptr* is a pointer to a TLV encoded buffer.</span></span>

<span data-ttu-id="70e0c-177">Для получения значения и проверки его типа предоставляются вспомогательные функции. Приложение никогда не должно напрямую обращаться к полю *nx_lwm2m_resource_value* за значениями из структуры NX_LWM2M_RESOURCE.</span><span class="sxs-lookup"><span data-stu-id="70e0c-177">Convenience functions are provided for retrieving the value and checking its type, the application should never directly access the *nx_lwm2m_resource_value* field when getting a value from a NX_LWM2M_RESOURCE structure.</span></span> <span data-ttu-id="70e0c-178">Определены следующие функции:</span><span class="sxs-lookup"><span data-stu-id="70e0c-178">The following functions are defined :</span></span>

- <span data-ttu-id="70e0c-179">***nx_lwm2m_resource_get_***: получение значения с указанным типом.</span><span class="sxs-lookup"><span data-stu-id="70e0c-179">***nx_lwm2m_resource_get_***: Get a value with the given type.</span></span>
- <span data-ttu-id="70e0c-180">***nx_lwm2m_resource_multiple_get_***: получение значения с указанным типом из ресурса с несколькими типами.</span><span class="sxs-lookup"><span data-stu-id="70e0c-180">***nx_lwm2m_resource_multiple_get_***: Get a value with the given type from a Multiple Resource.</span></span>

<span data-ttu-id="70e0c-181">Макрос **NX_LWM2M_RESOURCE_IS_MULTIPLE** (тип) позволяет проверить, является ли определенный ресурс ресурсом с несколькими типами.</span><span class="sxs-lookup"><span data-stu-id="70e0c-181">The macro **NX_LWM2M_RESOURCE_IS_MULTIPLE**(type) can be used to check if a resource type is a Multiple Resource.</span></span>

## <a name="object-implementation"></a><span data-ttu-id="70e0c-182">Реализация объекта</span><span class="sxs-lookup"><span data-stu-id="70e0c-182">Object Implementation</span></span>

<span data-ttu-id="70e0c-183">Клиент LWM2M реализует обязательные объекты OMA LWM2M: Security (0), Server (1), Access Control (2) и Device (3).</span><span class="sxs-lookup"><span data-stu-id="70e0c-183">The LWM2M Client implements the mandatory OMA LWM2M Objects: Security (0), Server (1), Access Control (2) and Device (3).</span></span> <span data-ttu-id="70e0c-184">Другие объекты для конкретного устройства следует реализовывать в приложении.</span><span class="sxs-lookup"><span data-stu-id="70e0c-184">Other device specific objects must be implemented by the application.</span></span>

<span data-ttu-id="70e0c-185">Для определения объекта используются две структуры данных: структура NX_LWM2M_OBJECT определяет реализацию объекта, значение идентификатора и методы объекта, а структура NX_LWM2M_OBJECT_INSTANCE содержит данные для экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="70e0c-185">Two data structures are used to define an Object: the NX_LWM2M_OBJECT structure defines the Object implementation, including the Object ID and the object methods, and the NX_LWM2M_OBJECT_INSTANCE structure contains the data of an Object Instance.</span></span>

<span data-ttu-id="70e0c-186">Структура NX_LWM2M_OBJECT имеет следующее определение:</span><span class="sxs-lookup"><span data-stu-id="70e0c-186">The NX_LWM2M_OBJECT structure has the following definition:</span></span>

```c
typedef struct NX_LWM2M_OBJECT_STRUCT
{
    NX_LWM2M_OBJECT * nx_lwm2m_object_next;
    NX_LWM2M_ID nx_lwm2m_object_id;
    UINT (*nx_lwm2m_object_read)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
        NX_LWM2M_RESOURCE *values);
    UINT (*nx_lwm2m_object_discover)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT *num_resources,
        NX_LWM2M_RESOURCE_INFO *resources);
    UINT (*nx_lwm2m_object_write)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values, const
        NX_LWM2M_RESOURCE *values, UINT write_op);
    UINT (*nx_lwm2m_object_execute)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
        const CHAR *args_ptr, UINT args_length);
    UINT (*nx_lwm2m_object_create)(NX_LWM2M_OBJECT * object_ptr,
        NX_LWM2M_ID instance_id, UINT num_values, const NX_LWM2M_RESOURCE
        *values, NX_LWM2M_OBJECT_INSTANCE **instance_ptr);
    UINT (*nx_lwm2m_object_delete)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr);
    NX_LWM2M_OBJECT_INSTANCE * nx_lwm2m_object_instances;
} NX_LWM2M_OBJECT;
```

- <span data-ttu-id="70e0c-187">**nx_lwm2m_object_next**: следующий объект в списке.</span><span class="sxs-lookup"><span data-stu-id="70e0c-187">**nx_lwm2m_object_next**: The next object in the list.</span></span>
- <span data-ttu-id="70e0c-188">**nx_lwm2m_object_id**: идентификатор объекта.</span><span class="sxs-lookup"><span data-stu-id="70e0c-188">**nx_lwm2m_object_id**: The Object ID.</span></span>
- <span data-ttu-id="70e0c-189">**nx_lwm2m_object_read**: метод Read, который описан ниже.</span><span class="sxs-lookup"><span data-stu-id="70e0c-189">**nx_lwm2m_object_read**: The 'Read' method, see below.</span></span>
- <span data-ttu-id="70e0c-190">**nx_lwm2m_object_discover**: метод Discover, который описан ниже.</span><span class="sxs-lookup"><span data-stu-id="70e0c-190">**nx_lwm2m_object_discover**: The 'Discover' method, see below.</span></span>
- <span data-ttu-id="70e0c-191">**nx_lwm2m_object_write**: метод Write, который описан ниже.</span><span class="sxs-lookup"><span data-stu-id="70e0c-191">**nx_lwm2m_object_write**: The 'Write' method, see below.</span></span>
- <span data-ttu-id="70e0c-192">**nx_lwm2m_object_execute**: метод Execute, который описан ниже.</span><span class="sxs-lookup"><span data-stu-id="70e0c-192">**nx_lwm2m_object_execute**: The 'Execute' method, see below.</span></span>
- <span data-ttu-id="70e0c-193">**nx_lwm2m_object_create**: метод Create, который описан ниже.</span><span class="sxs-lookup"><span data-stu-id="70e0c-193">**nx_lwm2m_object_create**: The 'Create' method, see below.</span></span>
- <span data-ttu-id="70e0c-194">**nx_lwm2m_object_delete**: метод Delete, который описан ниже.</span><span class="sxs-lookup"><span data-stu-id="70e0c-194">**nx_lwm2m_object_delete**: The 'Delete' method, see below.</span></span>
- <span data-ttu-id="70e0c-195">**nx_lwm2m_object_instances**: список экземпляров объектов, которые завершаются символом NULL.</span><span class="sxs-lookup"><span data-stu-id="70e0c-195">**nx_lwm2m_object_instances**: The NULL-terminated list of object instances.</span></span>

<span data-ttu-id="70e0c-196">Структура NX_LWM2M_OBJECT_INSTANCE имеет следующее определение:</span><span class="sxs-lookup"><span data-stu-id="70e0c-196">The NX_LWM2M_OBJECT_INSTANCE structure has the following definition:</span></span>

```c
typedef struct NX_LWM2M_OBJECT_INSTANCE_STRUCT
{
    NX_LWM2M_OBJECT_INSTANCE * nx_lwm2m_object_instance_next;
    NX_LWM2M_ID nx_lwm2m_object_instance_id;
} NX_LWM2M_OBJECT_INSTANCE;
```

- <span data-ttu-id="70e0c-197">**nx_lwm2m_object_instance_next**: следующий экземпляр в списке.</span><span class="sxs-lookup"><span data-stu-id="70e0c-197">**nx_lwm2m_object_instance_next**: The next instance in the list.</span></span>
- <span data-ttu-id="70e0c-198">**nx_lwm2m_object_instance_id**: идентификатор экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="70e0c-198">**nx_lwm2m_object_instance_id**: The Object Instance ID.</span></span>

<span data-ttu-id="70e0c-199">Объект должен реализовать методы, соответствующие операциям, которые определены в интерфейсе управления устройствами LWM2M: Read, Discover, Write, Execute, Create и Delete.</span><span class="sxs-lookup"><span data-stu-id="70e0c-199">The Object must implement the methods corresponding to the operations defined by the LWM2M Device Management Interface: 'Read', 'Discover', 'Write', 'Execute', 'Create' and 'Delete'.</span></span> <span data-ttu-id="70e0c-200">Для методов Create и Delete можно указать значение NULL, если объект не поддерживает динамическое создание экземпляров.</span><span class="sxs-lookup"><span data-stu-id="70e0c-200">The 'Create' and 'Delete' methods can be set to NULL if the object doesn't support dynamic creation of instances.</span></span>

### <a name="the-read-method"></a><span data-ttu-id="70e0c-201">Метод Read</span><span class="sxs-lookup"><span data-stu-id="70e0c-201">The 'Read' Method</span></span>

<span data-ttu-id="70e0c-202">Метод Read используется для считывания значений ресурса из экземпляра объекта и имеет следующее определение:</span><span class="sxs-lookup"><span data-stu-id="70e0c-202">The 'Read' method is used to read Resource values from an Object Instance, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_read(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    NX_LWM2M_RESOURCE *values_ptr);
```

<span data-ttu-id="70e0c-203">Входные параметры определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="70e0c-203">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="70e0c-204">**object_ptr**: указатель на реализацию объекта.</span><span class="sxs-lookup"><span data-stu-id="70e0c-204">**object_ptr**: Pointer to the Object implementation.</span></span>

- <span data-ttu-id="70e0c-205">**instance_ptr**: указатель на экземпляр объекта.</span><span class="sxs-lookup"><span data-stu-id="70e0c-205">**instance_ptr**: Pointer to the Object Instance.</span></span>

- <span data-ttu-id="70e0c-206">**num_values**: количество считываемых ресурсов.</span><span class="sxs-lookup"><span data-stu-id="70e0c-206">**num_values**: The number of resources to read.</span></span>

- <span data-ttu-id="70e0c-207">**values_ptr**: указатель на массив NX_LWM2M_RESOURCE, который содержит список считываемых идентификаторов.</span><span class="sxs-lookup"><span data-stu-id="70e0c-207">**values_ptr**: Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources to read.</span></span> <span data-ttu-id="70e0c-208">При возврате этот массив заполняется соответствующими типами и значениями.</span><span class="sxs-lookup"><span data-stu-id="70e0c-208">On return the array is filled with the corresponding types and values.</span></span>

### <a name="the-discover-method"></a><span data-ttu-id="70e0c-209">Метод Discover</span><span class="sxs-lookup"><span data-stu-id="70e0c-209">The 'Discover' Method</span></span>

<span data-ttu-id="70e0c-210">Метод Discover используется для получения списка всех ресурсов, реализованных объектом, и имеет следующее определение:</span><span class="sxs-lookup"><span data-stu-id="70e0c-210">The 'Discover' method is used to retrieve the list of all Resources implemented by an Object, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_discover(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT *num_resources_ptr,
    NX_LWM2M_RESOURCE_INFO *resources_ptr);
```

<span data-ttu-id="70e0c-211">Входные параметры определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="70e0c-211">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="70e0c-212">**object_ptr**: указатель на реализацию объекта.</span><span class="sxs-lookup"><span data-stu-id="70e0c-212">**object_ptr**: Pointer to the Object implementation.</span></span>

- <span data-ttu-id="70e0c-213">**instance_ptr**: указатель на экземпляр объекта.</span><span class="sxs-lookup"><span data-stu-id="70e0c-213">**instance_ptr**: Pointer to the Object Instance.</span></span>

- <span data-ttu-id="70e0c-214">**num_resources_ptr**: на входе содержит размер целевого буфера, а на выходе — количество записанных в этот буфер элементов.</span><span class="sxs-lookup"><span data-stu-id="70e0c-214">**num_resources_ptr**: On input the size of the destination buffer, on output the number of elements writen to the buffer.</span></span>

- <span data-ttu-id="70e0c-215">**resources_ptr**: указатель на целевой буфер.</span><span class="sxs-lookup"><span data-stu-id="70e0c-215">**resources_ptr**: Pointer to the destination buffer.</span></span>

<span data-ttu-id="70e0c-216">Сведения о ресурсе возвращаются в структуре NX_LWM2M_RESOURCE_INFO, которая определяется следующим образом:</span><span class="sxs-lookup"><span data-stu-id="70e0c-216">The resource information is returned in a NX_LWM2M_RESOURCE_INFO structure defined as follows:</span></span>

```c
typedef struct NX_LWM2M_RESOURCE_INFO_STRUCT
{
    NX_LWM2M_ID     nx_lwm2m_resource_info_id;
    USHORT          nx_lwm2m_resource_info_flags;
    UINT            nx_lwm2m_resource_info_dim;
} NX_LWM2M_RESOURCE_INFO;
```

- <span data-ttu-id="70e0c-217">**nx_lwm2m_resource_info_id**: идентификатор ресурса.</span><span class="sxs-lookup"><span data-stu-id="70e0c-217">**nx_lwm2m_resource_info_id**: The ID of the Resource.</span></span>

- <span data-ttu-id="70e0c-218">**nx_lwm2m_resource_info_flags**: см. описание ниже.</span><span class="sxs-lookup"><span data-stu-id="70e0c-218">**nx_lwm2m_resource_info_flags**: See below.</span></span>

- <span data-ttu-id="70e0c-219">**nx_lwm2m_resource_info_dim**: размерность ресурса с несколькими типами, если установлен флаг NX_LWM2M_RESOURCE_INFO_MULTIPLE.</span><span class="sxs-lookup"><span data-stu-id="70e0c-219">**nx_lwm2m_resource_info_dim**: The dimension of Multiple Resource if the flag NX_LWM2M_RESOURCE_INFO_MULTIPLE is set.</span></span>

<span data-ttu-id="70e0c-220">Поле *nx_lwm2m_resource_flags* может иметь следующие значения:</span><span class="sxs-lookup"><span data-stu-id="70e0c-220">The field *nx_lwm2m_resource_flags* can have to the following values:</span></span>

- <span data-ttu-id="70e0c-221">0: один доступный для чтения ресурс.</span><span class="sxs-lookup"><span data-stu-id="70e0c-221">0: Single readable resource.</span></span>

- <span data-ttu-id="70e0c-222">**NX_LWM2M_RESOURCE_INFO_MULTIPLE**: ресурс с несколькими типами, для которого должен быть определен *nx_lwm2m_resource_info_dim*.</span><span class="sxs-lookup"><span data-stu-id="70e0c-222">**NX_LWM2M_RESOURCE_INFO_MULTIPLE**: Multiple Resource, *nx_lwm2m_resource_info_dim* must be defined.</span></span>

- <span data-ttu-id="70e0c-223">**NX_LWM2M_RESOURCE_INFO_EXECUTABLE**: исполняемый или недоступный для чтения ресурс.</span><span class="sxs-lookup"><span data-stu-id="70e0c-223">**NX_LWM2M_RESOURCE_INFO_EXECUTABLE**: Executable or Non-Readable Resource.</span></span>

### <a name="the-write-method"></a><span data-ttu-id="70e0c-224">Метод Write</span><span class="sxs-lookup"><span data-stu-id="70e0c-224">The 'Write' Method</span></span>

<span data-ttu-id="70e0c-225">Метод Write используется для обновления или замены ресурсов в экземпляре объекта и имеет следующее определение:</span><span class="sxs-lookup"><span data-stu-id="70e0c-225">The 'Write' method is used to update or replace resources of an Object Instance, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_write(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr, UINT write_op);
```

<span data-ttu-id="70e0c-226">Входные параметры определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="70e0c-226">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="70e0c-227">**object_ptr**: указатель на реализацию объекта.</span><span class="sxs-lookup"><span data-stu-id="70e0c-227">**object_ptr**: Pointer to the Object implementation.</span></span>
- <span data-ttu-id="70e0c-228">**instance_ptr**: указатель на экземпляр объекта.</span><span class="sxs-lookup"><span data-stu-id="70e0c-228">**instance_ptr**: Pointer to the Object Instance.</span></span>
- <span data-ttu-id="70e0c-229">**num_values**: количество записываемых ресурсов.</span><span class="sxs-lookup"><span data-stu-id="70e0c-229">**num_values**: The number of resources to write.</span></span>
- <span data-ttu-id="70e0c-230">**values_ptr**: указатель на значения ресурсов.</span><span class="sxs-lookup"><span data-stu-id="70e0c-230">**values_ptr**: Pointer to the resources values.</span></span>
- <span data-ttu-id="70e0c-231">**write_op**: тип операций записи.</span><span class="sxs-lookup"><span data-stu-id="70e0c-231">**write_op**: The type of write operations.</span></span>

<span data-ttu-id="70e0c-232">Для параметра *write_op* можно указать следующие операции записи:</span><span class="sxs-lookup"><span data-stu-id="70e0c-232">The following write operations can be specified to the *write_op* parameter :</span></span>

- <span data-ttu-id="70e0c-233">0 &mdash; частичное обновление. Добавляет или обновляет ресурсы, указанные в новом значении, и сохраняет остальные существующие ресурсы без изменений.</span><span class="sxs-lookup"><span data-stu-id="70e0c-233">0 &mdash; Partial Update: adds or updates Resources provided in the new value and leaves other existing Resources unchanged,</span></span>

- <span data-ttu-id="70e0c-234">**NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; замена экземпляра. Заменяет существующий экземпляр объекта новым экземпляром с указанными значениями ресурса.</span><span class="sxs-lookup"><span data-stu-id="70e0c-234">**NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; Replace Instance: replaces the Object Instance with the new provided resource values.</span></span>

- <span data-ttu-id="70e0c-235">**NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; замена ресурса. Заменяет ресурсы новыми ресурсами с указанными значениями ресурса (используется для замены ресурсов с несколькими типами).</span><span class="sxs-lookup"><span data-stu-id="70e0c-235">**NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; Replace Resource: replaces the Resources with the new provided resource values (used to replace Multiple Resources).</span></span>

- <span data-ttu-id="70e0c-236">**NX_LWM2M_OBJECT_WRITE_CREATE** &mdash; создание экземпляра. Инициализирует новый экземпляр объекта с указанными значениями ресурса (вызывается из метода *nx_lwm2m_object_create*).</span><span class="sxs-lookup"><span data-stu-id="70e0c-236">**NX_LWM2M_OBJECT_WRITE_CREATE** &mdash; Create Instance: initializes the newly created Object Instance with the provided resource values (called from the *nx_lwm2m_object_create* method).</span></span>

- <span data-ttu-id="70e0c-237">**NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; запись при начальной загрузке. Вызывается при выполнении последовательности начальной загрузки.</span><span class="sxs-lookup"><span data-stu-id="70e0c-237">**NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; Bootstrap Write: called during Bootstrap sequence.</span></span>

### <a name="the-execute-method"></a><span data-ttu-id="70e0c-238">Метод Execute</span><span class="sxs-lookup"><span data-stu-id="70e0c-238">The 'Execute' Method</span></span>

<span data-ttu-id="70e0c-239">Метод Execute реализует выполнение ресурса объекта и имеет следующее определение:</span><span class="sxs-lookup"><span data-stu-id="70e0c-239">The 'Execute' method implements the execution of an Object Resource, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_execute(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr);
```

<span data-ttu-id="70e0c-240">Входные параметры определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="70e0c-240">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="70e0c-241">**object_ptr**: указатель на реализацию объекта.</span><span class="sxs-lookup"><span data-stu-id="70e0c-241">**object_ptr**: Pointer to the Object implementation</span></span>
- <span data-ttu-id="70e0c-242">**instance_ptr**: указатель на экземпляр объекта.</span><span class="sxs-lookup"><span data-stu-id="70e0c-242">**instance_ptr**: Pointer to the Object Instance.</span></span>
- <span data-ttu-id="70e0c-243">**resource_id**: идентификатор ресурса.</span><span class="sxs-lookup"><span data-stu-id="70e0c-243">**resource_id**: The Resource ID.</span></span>
- <span data-ttu-id="70e0c-244">**arguments_ptr**: указатель на аргументы операции исполнения.</span><span class="sxs-lookup"><span data-stu-id="70e0c-244">**arguments_ptr**: Pointer to the arguments of the execute operation.</span></span> <span data-ttu-id="70e0c-245">Может иметь значение NULL, если *arguments_length* равен нулю.</span><span class="sxs-lookup"><span data-stu-id="70e0c-245">Can be NULL if *arguments_length* is zero.</span></span>
- <span data-ttu-id="70e0c-246">**arguments_length**: длина аргументов.</span><span class="sxs-lookup"><span data-stu-id="70e0c-246">**arguments_length**: The length of the arguments.</span></span>

<span data-ttu-id="70e0c-247">Эта функция должна возвращать NX_LWM2M_NOT_FOUND, если идентификатор ресурса не существует, или NX_LWM2M_METHOD_NOT_ALLOWED, если он не поддерживает исполнение.</span><span class="sxs-lookup"><span data-stu-id="70e0c-247">The function must return NX_LWM2M_NOT_FOUND if the Resource ID doesn't exist, or NX_LWM2M_METHOD_NOT_ALLOWED if it doesn't support execution.</span></span>

### <a name="the-create-method"></a><span data-ttu-id="70e0c-248">Метод Create</span><span class="sxs-lookup"><span data-stu-id="70e0c-248">The 'Create' Method</span></span>

<span data-ttu-id="70e0c-249">Метод Create реализует создание нового экземпляра объекта и имеет следующее определение:</span><span class="sxs-lookup"><span data-stu-id="70e0c-249">The 'Create' method implements the creation of a new Object Instance, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_create(NX_LWM2M_OBJECT * object_ptr,
    NX_LWM2M_ID instance_id, UINT num_values, const NX_LWM2M_RESOURCE *values_ptr,
    NX_LWM2M_OBJECT_INSTANCE **instance_ptr, NX_LWM2M_BOOL bootstrap);
```

<span data-ttu-id="70e0c-250">Входные параметры определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="70e0c-250">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="70e0c-251">**object_ptr**: указатель на реализацию объекта.</span><span class="sxs-lookup"><span data-stu-id="70e0c-251">**object_ptr**: Pointer to the Object implementation.</span></span>
- <span data-ttu-id="70e0c-252">**instance_id**: идентификатор нового экземпляра.</span><span class="sxs-lookup"><span data-stu-id="70e0c-252">**instance_id**: The ID of the new Instance.</span></span>
- <span data-ttu-id="70e0c-253">**num_values**: количество инициализируемых ресурсов.</span><span class="sxs-lookup"><span data-stu-id="70e0c-253">**num_values**: The number of resources to initialize.</span></span>
- <span data-ttu-id="70e0c-254">**values_ptr**: указатель на значения ресурсов.</span><span class="sxs-lookup"><span data-stu-id="70e0c-254">**values_ptr**: Pointer to the resources values.</span></span>
- <span data-ttu-id="70e0c-255">**instance_ptr**: указатель на целевой указатель созданного экземпляра.</span><span class="sxs-lookup"><span data-stu-id="70e0c-255">**instance_ptr**: Pointer to the destination pointer of the created instance.</span></span>
- <span data-ttu-id="70e0c-256">**bootstrap**: имеет значение True, если вызов осуществляется при начальной загрузке.</span><span class="sxs-lookup"><span data-stu-id="70e0c-256">**bootstrap**: True if called from bootstrap sequence.</span></span>

<span data-ttu-id="70e0c-257">Объект должен выделить и инициализировать новый экземпляр объекта, используя предоставленный список значений ресурсов.</span><span class="sxs-lookup"><span data-stu-id="70e0c-257">The Object must allocate and initialiaze a new Object instance, using the provided list of resource values.</span></span>

### <a name="the-delete-method"></a><span data-ttu-id="70e0c-258">Метод Delete</span><span class="sxs-lookup"><span data-stu-id="70e0c-258">The 'Delete' Method</span></span>

<span data-ttu-id="70e0c-259">Метод Delete реализует удаление экземпляра объекта и имеет следующее определение:</span><span class="sxs-lookup"><span data-stu-id="70e0c-259">The 'Delete' method implements the deletion of an object instance, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_delete(NX_LWM2M_OBJECT *object_ptr,
                NX_LWM2M_OBJECT_INSTANCE *instance_ptr);
```

<span data-ttu-id="70e0c-260">Входные параметры определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="70e0c-260">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="70e0c-261">**object_ptr**: указатель на реализацию объекта.</span><span class="sxs-lookup"><span data-stu-id="70e0c-261">**object_ptr**: Pointer to the Object implementation.</span></span>
- <span data-ttu-id="70e0c-262">**instance_ptr**: указатель на экземпляр объекта.</span><span class="sxs-lookup"><span data-stu-id="70e0c-262">**instance_ptr**: Pointer to the Object Instance.</span></span>

<span data-ttu-id="70e0c-263">При успешном выполнении объект должен освободить память, занимаемую данными экземпляра объекта и любыми ресурсами, которые выделил этот экземпляр.</span><span class="sxs-lookup"><span data-stu-id="70e0c-263">On success the Object must release the Object Instance data and any other resource allocated by the instance.</span></span>

### <a name="adding-object-implementations-and-instances-to-the-lwm2m-client"></a><span data-ttu-id="70e0c-264">Добавление реализаций и экземпляров объектов в клиент LWM2M</span><span class="sxs-lookup"><span data-stu-id="70e0c-264">Adding Object Implementations and Instances to the LWM2M Client</span></span>

<span data-ttu-id="70e0c-265">Приложение может добавить в клиент LWM2M новую реализацию объекта, вызвав службу ***nx_lwm2m_client_object_add***.</span><span class="sxs-lookup"><span data-stu-id="70e0c-265">The application can add new object implementation to the LWM2M Client by calling the ***nx_lwm2m_client_object_add*** service.</span></span>

<span data-ttu-id="70e0c-266">Если объект не поддерживает динамическое создание экземпляров, (например, используется только один экземпляр объекта), то поле *nx_lwm2m_object_instances* в структуре объекта должно указывать на список структур статических экземпляров.</span><span class="sxs-lookup"><span data-stu-id="70e0c-266">If the Object doesn't support dynamic creation of Instances, for example if it's a single instance only Object, the *nx_lwm2m_object_instances* field of the object structure should point to the list of the static instances structures.</span></span>

<span data-ttu-id="70e0c-267">Если объект поддерживает динамическое создание экземпляров, то *nx_lwm2m_object_instances* должно иметь значение NULL, а для вызова метода Create этого объекта следует использовать службу ***nx_lwm2m_client_object_create***.</span><span class="sxs-lookup"><span data-stu-id="70e0c-267">If the Object supports dynamic instance creation, *nx_lwm2m_object_instances* should be set to NULL and the ***nx_lwm2m_client_object_create*** service should be used instead in order to call the 'Create' method of the object.</span></span>

## <a name="example-of-lwm2m-client-application"></a><span data-ttu-id="70e0c-268">Пример клиентского приложения LWM2M</span><span class="sxs-lookup"><span data-stu-id="70e0c-268">Example of LWM2M Client Application</span></span>

<span data-ttu-id="70e0c-269">Следующий код содержит пример простого клиентского приложения LWM2M, которое реализует пользовательское устройство с датчиком температуры и выключателем освещения.</span><span class="sxs-lookup"><span data-stu-id="70e0c-269">The following code is an example of a simple LWM2M Client Application which implements a custom device consisting of a temperature sensor and a light switch.</span></span>

<span data-ttu-id="70e0c-270">Это устройство позволяет серверу считывать значение датчика температуры и логическое состояние выключателя освещения, а также устанавливать этот переключатель в положения "Включено" и "Выключено".</span><span class="sxs-lookup"><span data-stu-id="70e0c-270">The device allows a server to read the value of the temperature sensor and the boolean state of the light switch, and to set the light switch to on/off.</span></span>

```c
#include "nx_lwm2m_client.h"

/* Custom Object implementation */
/* Define the Custom Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_OBJECT_INSTANCE     lwm2m;

    /* Resources Data */
    NX_LWM2M_FLOAT32             temperature;
    NX_LWM2M_BOOL                light;
} MYOBJECT_INSTANCE;

/* Define the Resources IDs */
#define MYOBJECT_RES_TEMPERATURE     0 /* temperature sensor */
#define MYOBJECT_RES_LIGHT           1 /* light switch */

/* Define the 'Read' Method */
UINT myobject_read(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr,
    UINT num_values, NX_LWM2M_RESOURCE *values)
{
    UINT i;
    for (i=0; i<num_values; i++)
    {
        switch (values[i].nx_lwm2m_resource_id)
        {
        case MYOBJECT_RES_TEMPERATURE:

            /* return the temperature value */
            values[i].nx_lwm2m_resource_type = NX_LWM2M_RESOURCE_FLOAT32;
            values[i].nx_lwm2m_resource_value.nx_lwm2m_resource_float32data =
                ((MYOBJECT_INSTANCE *) instance_ptr)->temperature;
            break;
        case MYOBJECT_RES_LIGHT:

            /* return the state of the light switch */
            values[i].nx_lwm2m_resource_type = NX_LWM2M_RESOURCE_BOOLEAN;
            values[i].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata =
                ((MYOBJECT_INSTANCE *) instance_ptr)->light;
            break;

        default:

            /* unknown resource ID */
            return NX_LWM2M_NOT_FOUND;
        }
    }
    return NX_SUCCESS;
}

/* Define the 'Discover' method */
UINT myobject_discover(NX_LWM2M_OBJECT *object_ptr, NX_LWM2M_OBJECT_INSTANCE *instance_ptr,
                                    UINT *num_resources, NX_LWM2M_RESOURCE_INFO *resources)
{
    if (*num_resources < 2)
    {
        return NX_LWM2M_BUFFER_TOO_SMALL;
    }

    /* return the list of supported resources IDs */
    *num_resources = 2;
    resources[0].nx_lwm2m_resource_info_id        = MYOBJECT_RES_TEMPERATURE;
    resources[0].nx_lwm2m_resource_info_flags     = 0;
    resources[1].nx_lwm2m_resource_info_id        = MYOBJECT_RES_LIGHT;
    resources[1].nx_lwm2m_resource_info_flags     = 0;
    return NX_SUCCESS;
}

/* Define the 'Write' method */
UINT myobject_write(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    const NX_LWM2M_RESOURCE *values, UINT flags)
{
    UINT i;
    for (i=0; i<num_values; i++)
    {
        UINT ret;
        switch (values[i].nx_lwm2m_resource_id)
        {

        case MYOBJECT_RES_TEMPERATURE:

            /* read-only resource */
            return NX_LWM2M_METHOD_NOT_ALLOWED;

        case MYOBJECT_RES_LIGHT:

            /* assign boolean value */

            ret = nx_lwm2m_resource_get_boolean(&values[i],
                &((MYOBJECT_INSTANCE *) instance_ptr)->light);

            if (ret != NX_SUCCESS)
            {

                /* invalid value type */
                return ret;
            }
            break;

        default:

            /* unknown resource ID */
            return NX_LWM2M_NOT_FOUND;
        }
    }
    return NX_SUCCESS;
}

/* Define the 'Execute' method */
UINT myobject_execute(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
    const CHAR *args_ptr, UINT args_length)
{
    switch (resource_id)
    {

    case MYOBJECT_RES_TEMPERATURE:
    case MYOBJECT_RES_LIGHT:

        /* read-only resource */
        return NX_LWM2M_METHOD_NOT_ALLOWED;

    default:

        /* unknown resource ID */
        return NX_LWM2M_NOT_FOUND;

    }
}

/* NetX data */
NX_IP                       ip;
NX_PACKET_POOL              packet_pool;

/* LWM2M Client data */
NX_LWM2M_CLIENT             client;
ULONG                       client_stack[4096 / sizeof(ULONG)];
NX_LWM2M_CLIENT_SESSION     session;

/* Custom Object Data */
NX_LWM2M_OBJECT             myobject;
MYOBJECT_INSTANCE           myinstance;

/* Define the session state callback */
void session_callback(NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state)
{
    switch (state)
    {

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED:

        /* Bootstrap session done, we can register to the LWM2M Server */
        {
            NX_LWM2M_ID security_id;

            /* find the Security Object Instance of the LWM2M Server */
            security_id = NX_LWM2M_RESERVED_ID;
            while (nx_lwm2m_client_object_instance_get_next(&client,
                NX_LWM2M_SECURITY_OBJECT_ID, &security_id) == NX_SUCCESS)
            {
                NX_LWM2M_RESOURCE res[3];

                /* retrieve instance data: */
                /* Bootstrap server flag */
                res[0].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_BOOTSTRAP_ID;

                /* URI of server */
                res[1].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_URI_ID;

                /* Short Server ID */
                res[2].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_SHORT_SERVER_ID;

                /* Read Object Instance: */
                nx_lwm2m_client_object_read(&client,
                    NX_LWM2M_SECURITY_OBJECT_ID, security_id, 3, res);

                /* Not a bootstrap server? */
                if (!res[0].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata)
                {
                    ULONG ip_addr;
                    UINT udp_port;

                    /* get IP address and UDP port from server URI */
                    parse_uri(res[1].nx_lwm2m_resource_value.nx_lwm2m_resource_stringdata, &ip_addr, &udp_port);

                    /* Start registration to the LWM2M server */
                    nx_lwm2m_client_session_register(&session,
                        (NX_LWM2M_ID) res[2].nx_lwm2m_resource_value.
                        nx_lwm2m_resource_integer32data,
                        ip_addr, udp_port);
                    break;
                }
            }
        }
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR:

        /* Failed to Bootstrap the LWM2M Client. */
        break;

    case NX_LWM2M_CLIENT_SESSION_REGISTERED:

        /* Registration to the LWM2M Client done. */
        break;

    case NX_LWM2M_CLIENT_SESSION_ERROR:

        /* Failed to register to the LWM2M Client. */
        break;
    }
}

/* Application main thread */
void application_thread(ULONG info)
{
    NX_LWM2M_RESOURCE res[4];
    NX_LWM2M_ID security_id;

    /* Create the LWM2M client */
    nx_lwm2m_client_create(&client, &ip, &packet_pool, NX_LWM2M_COAP_PORT,
        "mylwm2mclient", NULL, NX_LWM2M_BINDING_U,
        client_stack, sizeof(client_stack));

    /* Define our custom object */
    myobject.nx_lwm2m_object_id           = 1024;
    myobject.nx_lwm2m_object_read         = myobject_read;
    myobject.nx_lwm2m_object_discover     = myobject_discover;
    myobject.nx_lwm2m_object_write        = myobject_write;
    myobject.nx_lwm2m_object_execute      = myobject_execute;
    myobject.nx_lwm2m_object_create       = NULL;
    myobject.nx_lwm2m_object_delete       = NULL;

    /* Define a single instance */
    myobject.nx_lwm2m_object_instances             = (NX_LWM2M_OBJECT_INSTANCE *) &myinstance;
    myinstance.lwm2m.nx_lwm2m_object_instance_id   = 0;
    myinstance.lwm2m.nx_lwm2m_object_instance_next = NULL;
    myinstance.temperature                         = 22.5f;
    myinstance.light                               = NX_FALSE;

    /* Add the object to the LWM2M Client */
    nx_lwm2m_client_object_add(&client, &myobject);

    /* Create a security entry for the bootstrap server */
    security_id = 0;

    /* set the URI of the server */
    res[0].nx_lwm2m_resource_id                                 = NX_LWM2M_SECURITY_URI_ID;
    res[0].nx_lwm2m_resource_type                               = NX_LWM2M_RESOURCE_STRING;
    res[0].nx_lwm2m_resource_value.nx_lwm2m_resource_stringdata = "coap://1.2.3.4";

    /* set the Bootstrap flag */
    res[1].nx_lwm2m_resource_id                                  = NX_LWM2M_SECURITY_BOOTSTRAP_ID;
    res[1].nx_lwm2m_resource_type                                = NX_LWM2M_RESOURCE_BOOLEAN;
    res[1].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata = NX_TRUE;

    /* set the security mode */
    res[2].nx_lwm2m_resource_id                                    = NX_LWM2M_SECURITY_MODE_ID;
    res[2].nx_lwm2m_resource_type                                  = NX_LWM2M_RESOURCE_INTEGER32;
    res[2].nx_lwm2m_resource_value.nx_lwm2m_resource_integer32data =
    NX_LWM2M_SECURITY_MODE_NOSEC;

    /* set the Hold Off timer */
    res[3].nx_lwm2m_resource_id                                    = NX_LWM2M_SECURITY_HOLD_OFF_ID;
    res[3].nx_lwm2m_resource_type                                  = NX_LWM2M_RESOURCE_INTEGER32;
    res[3].nx_lwm2m_resource_value.nx_lwm2m_resource_integer32data = 10;
    nx_lwm2m_client_object_create(&client, NX_LWM2M_SECURITY_OBJECT_ID,
        &security_id, 4, res);

    /* Create a session */
    nx_lwm2m_client_session_create(&session, &client, session_callback);

    /* start bootstrap session */
    nx_lwm2m_client_session_bootstrap(&session, security_id,
                            IP_ADDRESS(1, 2, 3, 4), 5683);

    /* Application main loop */
    while (1)
    {
        /* ...application code... */
    }

    /* Terminate the LWM2M Client */
    nx_lwm2m_client_delete(&client);
}
```
