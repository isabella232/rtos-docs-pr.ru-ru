---
title: Глава 3. Функциональное описание клиента LWM2M
description: Эта глава содержит функциональное описание клиента LWM2M.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 24b7ff66fb4d060075eb6bc81bed45b3479e18dc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814679"
---
# <a name="chapter-3--functional-description-of-lwm2m-client"></a><span data-ttu-id="fe54d-103">Глава 3. Функциональное описание клиента LWM2M</span><span class="sxs-lookup"><span data-stu-id="fe54d-103">Chapter 3  Functional Description of LWM2M Client</span></span>

> <span data-ttu-id="fe54d-104">Эта глава содержит функциональное описание клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="fe54d-104">This chapter contains a functional description of LWM2M Client.</span></span>

## <a name="lwm2m-client-initialization"></a><span data-ttu-id="fe54d-105">Инициализация клиента LWM2M</span><span class="sxs-lookup"><span data-stu-id="fe54d-105">LWM2M Client Initialization</span></span>

<span data-ttu-id="fe54d-106">Клиент LWM2M инициализируется путем вызова службы ***nx_lwm2m_client_create***.</span><span class="sxs-lookup"><span data-stu-id="fe54d-106">The LWM2M Client is initialized by calling ***nx_lwm2m_client_create*** service.</span></span> <span data-ttu-id="fe54d-107">Клиент LWM2M работает в отдельном потоке и может сообщать приложению о некоторых событиях с помощью обратных вызовов или путем вызова методов из пользовательских объектов, реализованных в приложении.</span><span class="sxs-lookup"><span data-stu-id="fe54d-107">The LWM2M Client runs in its own thread and can report some events to the application through the use of callbacks, or by calling methods of the custom objects implemented by the application.</span></span>

<span data-ttu-id="fe54d-108">Кроме того, для поддержки связи с одним или несколькими серверами следует создавать сеансы клиента LWM2M путем вызова ***nx_lwm2m_client_session_create***.</span><span class="sxs-lookup"><span data-stu-id="fe54d-108">In addition, LWM2M Client Sessions must be created by calling ***nx_lwm2m_client_session_create*** for enabling communication with one or more servers.</span></span> <span data-ttu-id="fe54d-109">Каждый сеанс может взаимодействовать с серверами двух разных типов: сервером начальной загрузки или сервером LWM2M (управление устройством).</span><span class="sxs-lookup"><span data-stu-id="fe54d-109">A session can communicate with two different types of servers: a Bootstrap Server or a LWM2M Server (Device Management).</span></span>

### <a name="bootstrap-server-session"></a><span data-ttu-id="fe54d-110">Сеанс сервера начальной загрузки</span><span class="sxs-lookup"><span data-stu-id="fe54d-110">Bootstrap Server Session</span></span>

<span data-ttu-id="fe54d-111">Сеанс связи с сервером начальной загрузки позволяет предоставить клиенту LWM2M информацию, которая необходима ему для регистрации на одном или нескольких серверах LWM2M.</span><span class="sxs-lookup"><span data-stu-id="fe54d-111">A communication session with a Bootstrap Server is used to provision essential information into the LWM2M Client to enable the LWM2M Client to perform the operation “Register” with one or more LWM2M Servers.</span></span> <span data-ttu-id="fe54d-112">Этот тип сервера используется в режимах начальной загрузки, инициируемой клиентом и сервером.</span><span class="sxs-lookup"><span data-stu-id="fe54d-112">This type of server is used during the Client Initiated and Server Initiated Bootstrap modes.</span></span>

<span data-ttu-id="fe54d-113">Приложение может запустить сеанс начальной загрузки путем вызова ***nx_lwm2m_client_session_bootstrap** _ или _*_nx_lwm2m_client_session_bootstrap_dtls_\*_, в которых оно должно указать IP-адрес и номер порта сервера, а также необязательный идентификатор экземпляра объекта безопасности.</span><span class="sxs-lookup"><span data-stu-id="fe54d-113">The application can start a Bootstrap session by calling ***nx_lwm2m_client_session_bootstrap** _ or _*_nx_lwm2m_client_session_bootstrap_dtls_\*_, it must provide the IP address and port number of the server, and an optional Security Object Instance ID.</span></span> <span data-ttu-id="fe54d-114">Функция _*_nx_lwm2m_client_session_bootstrap_*_ использует обмен данными без защиты, а _ *_nx_lwm2m_client_session_bootstrap_dtls_*\* создает безопасное подключение к серверу по протоколу DTLS.</span><span class="sxs-lookup"><span data-stu-id="fe54d-114">The _*_nx_lwm2m_client_session_bootstrap_*_ function uses insecure communication, whereas _ *_nx_lwm2m_client_session_bootstrap_dtls_*\* establishes a secure DTLS connection with the server.</span></span>

<span data-ttu-id="fe54d-115">Если операция начальной загрузки выполняется успешно, на сервере начальной загрузки должны быть созданы экземпляры объектов безопасности для серверов начальной загрузки и LWM2M, а также экземпляры объектов сервера для серверов LWM2M.</span><span class="sxs-lookup"><span data-stu-id="fe54d-115">If the Bootstrap operation is successful, the Bootstrap server should have created Security Object Instance(s) for the Bootstrap and LWM2M Servers, and Server Object Instance(s) for the LWM2M Servers.</span></span> <span data-ttu-id="fe54d-116">Приложение может вызвать функцию ***nx_lwm2m_client_session_register_info_get***, чтобы получить информацию о серверах LWM2M и использовать эти сведения для установления сеанса с серверами LWM2M.</span><span class="sxs-lookup"><span data-stu-id="fe54d-116">The application can call ***nx_lwm2m_client_session_register_info_get*** to get LWM2M Server(s) information and use this information for establishing a session with the LWM2M Server(s).</span></span>

<span data-ttu-id="fe54d-117">Данные начальной загрузки должны сохраняться приложением в энергонезависимой памяти, чтобы было можно создать клиент LWM2M при следующей перезагрузке устройства.</span><span class="sxs-lookup"><span data-stu-id="fe54d-117">The Bootstrap data should be saved to non-volatile memory by the application to configure the LWM2M Client at the next reboot of the device.</span></span>

### <a name="lwm2m-server-session"></a><span data-ttu-id="fe54d-118">Сеанс сервера LWM2M</span><span class="sxs-lookup"><span data-stu-id="fe54d-118">LWM2M Server Session</span></span>

<span data-ttu-id="fe54d-119">Сеанс связи с сервером LWM2M используется для регистрации, управления устройствами и включения службы.</span><span class="sxs-lookup"><span data-stu-id="fe54d-119">A communication session with a LWM2M Server is used for Registration, Device Management and Service Enablement.</span></span>

<span data-ttu-id="fe54d-120">Приложение может зарегистрировать клиент LWM2M на сервере путем вызова ***nx_lwm2m_client_session_register** _ или _*_nx_lwm2m_client_session_register_dtls_\*_, в которых оно должно указать IP-адрес и номер порта сервера, а также короткий идентификатор сервера, соответствующий существующему экземпляру объекта сервера.</span><span class="sxs-lookup"><span data-stu-id="fe54d-120">The application can register the LWM2M Client to a server by calling ***nx_lwm2m_client_session_register** _ or _*_nx_lwm2m_client_session_register_dtls_\*_, it must provide the IP address and port number of the server, and the Short Server ID which corresponds to an existing Server Object Instance.</span></span> <span data-ttu-id="fe54d-121">Функция _*_nx_lwm2m_client_session_register_*_ использует обмен данными без защиты, а _ *_nx_lwm2m_client_session_register_dtls_*\* создает безопасное подключение к серверу по протоколу DTLS.</span><span class="sxs-lookup"><span data-stu-id="fe54d-121">The _*_nx_lwm2m_client_session_register_*_ function uses insecure communication, whereas  _ *_nx_lwm2m_client_session_register_dtls_*\* establishes a secure DTLS connection with the server.</span></span>

<span data-ttu-id="fe54d-122">Приложение может отменить регистрацию клиента LWM2M, вызвав ***nx_lwm2m_client_session_deregister** _, и попросить клиента отправить сообщение обновления (Update), вызвав _*_nx_lwm2m_client_session_update_\*\*.</span><span class="sxs-lookup"><span data-stu-id="fe54d-122">The application can de-register the LWM2M Client by calling ***nx_lwm2m_client_session_deregister** _, and ask the client to send an ‘Update’ message by calling _*_nx_lwm2m_client_session_update_\*\*.</span></span>

### <a name="session-state-callback"></a><span data-ttu-id="fe54d-123">Обратный вызов состояния сеанса</span><span class="sxs-lookup"><span data-stu-id="fe54d-123">Session State Callback</span></span>

<span data-ttu-id="fe54d-124">Приложение регистрирует при создании сеанса обратный вызов, который вызывается при обновлении состояния сеанса. Функция обратного вызова **NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK** имеет следующий прототип.</span><span class="sxs-lookup"><span data-stu-id="fe54d-124">The application registers a callback at creation of a session which is called when the state of the session is updated, the callback function **NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK** has the following prototype.</span></span>

<span data-ttu-id="fe54d-125">typedef VOID (\*NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)(NX_LWM2M_CLIENT_SESSION \*session_ptr,UINT state);</span><span class="sxs-lookup"><span data-stu-id="fe54d-125">typedef VOID (\*NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)(NX_LWM2M_CLIENT_SESSION \*session_ptr,UINT state);</span></span>

<span data-ttu-id="fe54d-126">Определены следующие состояния.</span><span class="sxs-lookup"><span data-stu-id="fe54d-126">The following states are defined.</span></span>

| <span data-ttu-id="fe54d-127">Состояние&nbsp;сеанса</span><span class="sxs-lookup"><span data-stu-id="fe54d-127">Session&nbsp;State</span></span> | <span data-ttu-id="fe54d-128">Описание</span><span class="sxs-lookup"><span data-stu-id="fe54d-128">Description</span></span> |
| --- | --- |
| <span data-ttu-id="fe54d-129">**NX_LWM2M_CLIENT_SESSION_INIT**</span><span class="sxs-lookup"><span data-stu-id="fe54d-129">**NX_LWM2M_CLIENT_SESSION_INIT**</span></span> | <span data-ttu-id="fe54d-130">Начальное состояние после создания сеанса.</span><span class="sxs-lookup"><span data-stu-id="fe54d-130">The initial state after session creation.</span></span> |
| <span data-ttu-id="fe54d-131">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING**</span><span class="sxs-lookup"><span data-stu-id="fe54d-131">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING**</span></span> | <span data-ttu-id="fe54d-132">Клиент ожидает истечения срока действия таймера задержки (Hold Off) или начальной загрузки, инициированной сервером.</span><span class="sxs-lookup"><span data-stu-id="fe54d-132">The client is waiting for the expiration of the ‘Hold Off’ timer or Server Initiated Bootstrap.</span></span> |
| <span data-ttu-id="fe54d-133">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING**</span><span class="sxs-lookup"><span data-stu-id="fe54d-133">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING**</span></span> | <span data-ttu-id="fe54d-134">Клиент отправил сообщение запроса (Request) на сервер начальной загрузки (начальная загрузка, инициированная клиентом).</span><span class="sxs-lookup"><span data-stu-id="fe54d-134">The client has sent a ‘Request’ message to the Bootstrap Server (Client Initiated Bootstrap).</span></span> |
| <span data-ttu-id="fe54d-135">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED**</span><span class="sxs-lookup"><span data-stu-id="fe54d-135">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED**</span></span> | <span data-ttu-id="fe54d-136">Клиент получает данные с сервера начальной загрузки.</span><span class="sxs-lookup"><span data-stu-id="fe54d-136">The client is receiving data from the Bootstrap Server.</span></span> |
| <span data-ttu-id="fe54d-137">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED**</span><span class="sxs-lookup"><span data-stu-id="fe54d-137">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED**</span></span> | <span data-ttu-id="fe54d-138">Сервер начальной загрузки отправил сообщение о завершении (Finished).</span><span class="sxs-lookup"><span data-stu-id="fe54d-138">The Bootstrap Server has sent a ‘Finished’ message.</span></span> |
| <span data-ttu-id="fe54d-139">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR**</span><span class="sxs-lookup"><span data-stu-id="fe54d-139">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR**</span></span> | <span data-ttu-id="fe54d-140">Сеанс начальной загрузки завершился сбоем.</span><span class="sxs-lookup"><span data-stu-id="fe54d-140">The bootstrap session has failed.</span></span> |
| <span data-ttu-id="fe54d-141">**NX_LWM2M_CLIENT_SESSION_REGISTERING**</span><span class="sxs-lookup"><span data-stu-id="fe54d-141">**NX_LWM2M_CLIENT_SESSION_REGISTERING**</span></span> | <span data-ttu-id="fe54d-142">Клиент отправил сообщение Register на сервер LWM2M.</span><span class="sxs-lookup"><span data-stu-id="fe54d-142">The client has sent a ‘Register’ message to the LWM2M Server.</span></span> |
| <span data-ttu-id="fe54d-143">**NX_LWM2M_CLIENT_SESSION_REGISTERED**</span><span class="sxs-lookup"><span data-stu-id="fe54d-143">**NX_LWM2M_CLIENT_SESSION_REGISTERED**</span></span> | <span data-ttu-id="fe54d-144">Клиент зарегистрировался на сервере LWM2M.</span><span class="sxs-lookup"><span data-stu-id="fe54d-144">The client is registered to the LWM2M Server.</span></span> |
| <span data-ttu-id="fe54d-145">**NX_LWM2M_CLIENT_SESSION_UPDATING**</span><span class="sxs-lookup"><span data-stu-id="fe54d-145">**NX_LWM2M_CLIENT_SESSION_UPDATING**</span></span> | <span data-ttu-id="fe54d-146">Клиент отправил сообщение Update на сервер LWM2M.</span><span class="sxs-lookup"><span data-stu-id="fe54d-146">The client has sent an ‘Update’ message to the LWM2M Server.</span></span> |
| <span data-ttu-id="fe54d-147">**NX_LWM2M_CLIENT_SESSION_DEREGISTERING**</span><span class="sxs-lookup"><span data-stu-id="fe54d-147">**NX_LWM2M_CLIENT_SESSION_DEREGISTERING**</span></span> | <span data-ttu-id="fe54d-148">Клиент отправил сообщение De-register на сервер LWM2M.</span><span class="sxs-lookup"><span data-stu-id="fe54d-148">The client has sent an ‘De-register’ message to the LWM2M Server.</span></span> |
| <span data-ttu-id="fe54d-149">**NX_LWM2M_CLIENT_SESSION_DEREGISTERED**</span><span class="sxs-lookup"><span data-stu-id="fe54d-149">**NX_LWM2M_CLIENT_SESSION_DEREGISTERED**</span></span> | <span data-ttu-id="fe54d-150">Регистрация клиента на сервере LWM2M отменена.</span><span class="sxs-lookup"><span data-stu-id="fe54d-150">The client is de-registered from the LWM2M Server.</span></span> |
| <span data-ttu-id="fe54d-151">**NX_LWM2M_CLIENT_SESSION_DISABLED**</span><span class="sxs-lookup"><span data-stu-id="fe54d-151">**NX_LWM2M_CLIENT_SESSION_DISABLED**</span></span> | <span data-ttu-id="fe54d-152">Сервер LWM2M отключен.</span><span class="sxs-lookup"><span data-stu-id="fe54d-152">The LWM2M Server is disabled.</span></span> <span data-ttu-id="fe54d-153">Когда срок действия таймера отключения истечет, будет отправлено сообщение Register.</span><span class="sxs-lookup"><span data-stu-id="fe54d-153">A ‘Register’ will be sent after the expiration of the disable timer.</span></span> |
| <span data-ttu-id="fe54d-154">**NX_LWM2M_CLIENT_SESSION_ERROR**</span><span class="sxs-lookup"><span data-stu-id="fe54d-154">**NX_LWM2M_CLIENT_SESSION_ERROR**</span></span> | <span data-ttu-id="fe54d-155">Операция регистрации или обновления на сервере LWM2M завершилась сбоем.</span><span class="sxs-lookup"><span data-stu-id="fe54d-155">The registration or update operation to the LWM2M Server has failed.</span></span> |
| <span data-ttu-id="fe54d-156">**NX_LWM2M_CLIENT_SESSION_DELETED**</span><span class="sxs-lookup"><span data-stu-id="fe54d-156">**NX_LWM2M_CLIENT_SESSION_DELETED**</span></span> | <span data-ttu-id="fe54d-157">Экземпляр объекта сервера, соответствующий серверу LWM2M, удален.</span><span class="sxs-lookup"><span data-stu-id="fe54d-157">The Server Object Instance corresponding to the LWM2M Server has been deleted.</span></span> |

<span data-ttu-id="fe54d-158">В случае ошибки приложение может определить ее причину путем вызова ***nx_lwm2m_client_session_error_get***.</span><span class="sxs-lookup"><span data-stu-id="fe54d-158">In case of error the application can retrieve the cause of the error by calling ***nx_lwm2m_client_session_error_get***.</span></span>

## <a name="local-device-management"></a><span data-ttu-id="fe54d-159">Управление локальным устройством</span><span class="sxs-lookup"><span data-stu-id="fe54d-159">Local Device Management</span></span>

<span data-ttu-id="fe54d-160">Приложение может получить доступ к объектам клиента LWM2M с помощью функций управления локальным устройством.</span><span class="sxs-lookup"><span data-stu-id="fe54d-160">The application can access the Objects of the LWM2M Client by using the local device management functions.</span></span> <span data-ttu-id="fe54d-161">Для этого предоставляются следующие функции.</span><span class="sxs-lookup"><span data-stu-id="fe54d-161">The following functions are provided.</span></span>

| <span data-ttu-id="fe54d-162">Имя&nbsp;функции</span><span class="sxs-lookup"><span data-stu-id="fe54d-162">Function&nbsp;Name</span></span> | <span data-ttu-id="fe54d-163">Описание</span><span class="sxs-lookup"><span data-stu-id="fe54d-163">Description</span></span> |
| --- | --- |
| <span data-ttu-id="fe54d-164">***nx_lwm2m_client_object_read***</span><span class="sxs-lookup"><span data-stu-id="fe54d-164">***nx_lwm2m_client_object_read***</span></span> | <span data-ttu-id="fe54d-165">Чтение ресурсов из экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="fe54d-165">Read resources from an Object Instance.</span></span> |
| <span data-ttu-id="fe54d-166">***nx_lwm2m_client_object_discover***</span><span class="sxs-lookup"><span data-stu-id="fe54d-166">***nx_lwm2m_client_object_discover***</span></span> | <span data-ttu-id="fe54d-167">Получение списка ресурсов экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="fe54d-167">Get the list of the resources of an Object Instance.</span></span>
| <span data-ttu-id="fe54d-168">***nx_lwm2m_client_object_write***</span><span class="sxs-lookup"><span data-stu-id="fe54d-168">***nx_lwm2m_client_object_write***</span></span> | <span data-ttu-id="fe54d-169">Запись ресурсов в экземпляр объекта.</span><span class="sxs-lookup"><span data-stu-id="fe54d-169">Write resources to an Object Instance.</span></span> |
| <span data-ttu-id="fe54d-170">***nx_lwm2m_client_object_execute***</span><span class="sxs-lookup"><span data-stu-id="fe54d-170">***nx_lwm2m_client_object_execute***</span></span> | <span data-ttu-id="fe54d-171">Осуществление операции выполнения в ресурсе экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="fe54d-171">Perform the Execute operation on a resource of an Object Instance.</span></span> |
| <span data-ttu-id="fe54d-172">***nx_lwm2m_client_object_create***</span><span class="sxs-lookup"><span data-stu-id="fe54d-172">***nx_lwm2m_client_object_create***</span></span> | <span data-ttu-id="fe54d-173">Создание нового экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="fe54d-173">Create a new Object Instance.</span></span> |
| <span data-ttu-id="fe54d-174">***nx_lwm2m_client_object_delete***</span><span class="sxs-lookup"><span data-stu-id="fe54d-174">***nx_lwm2m_client_object_delete***</span></span> | <span data-ttu-id="fe54d-175">Удаление существующего экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="fe54d-175">Delete an existing Object Instance.</span></span> |
| <span data-ttu-id="fe54d-176">***nx_lwm2m_client_object_next_get***</span><span class="sxs-lookup"><span data-stu-id="fe54d-176">***nx_lwm2m_client_object_next_get***</span></span> | <span data-ttu-id="fe54d-177">Получение следующего идентификатора объекта клиентом LWM2M.</span><span class="sxs-lookup"><span data-stu-id="fe54d-177">Get the next Object ID by the LWM2M Client.</span></span> |
| <span data-ttu-id="fe54d-178">***nx_lwm2m_client_object_instance_next_get***</span><span class="sxs-lookup"><span data-stu-id="fe54d-178">***nx_lwm2m_client_object_instance_next_get***</span></span> | <span data-ttu-id="fe54d-179">Получение следующего экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="fe54d-179">Get the next Instance of an Object.</span></span> |

## <a name="resource-information"></a><span data-ttu-id="fe54d-180">Сведения о ресурсе</span><span class="sxs-lookup"><span data-stu-id="fe54d-180">Resource Information</span></span>

<span data-ttu-id="fe54d-181">Во время операций чтения и записи в объекте ресурс представляется структурой NX_LWM2M_CLIENT_RESOURCE.</span><span class="sxs-lookup"><span data-stu-id="fe54d-181">When reading from and writing to Objects a Resource is represented by the NX_LWM2M_CLIENT_RESOURCE structure.</span></span> <span data-ttu-id="fe54d-182">Эта структура содержит идентификатор ресурса или экземпляра и соответствующее значение.</span><span class="sxs-lookup"><span data-stu-id="fe54d-182">This structure contains the ID of the Resource/Instance and its value.</span></span>

<span data-ttu-id="fe54d-183">Для настройки сведений о ресурсе и его значения существуют следующие функции.</span><span class="sxs-lookup"><span data-stu-id="fe54d-183">The following functions are provided for setting resource info and value.</span></span>

| <span data-ttu-id="fe54d-184">Имя&nbsp;функции</span><span class="sxs-lookup"><span data-stu-id="fe54d-184">Function&nbsp;Name</span></span> | <span data-ttu-id="fe54d-185">Описание</span><span class="sxs-lookup"><span data-stu-id="fe54d-185">Description</span></span> |
| --- | --- |
| <span data-ttu-id="fe54d-186">***nx_lwm2m_client_resource_info_set***</span><span class="sxs-lookup"><span data-stu-id="fe54d-186">***nx_lwm2m_client_resource_info_set***</span></span> | <span data-ttu-id="fe54d-187">Указание сведений о ресурсе: идентификатор ресурса и операция: READ, WRITE, EXECUTABLE.</span><span class="sxs-lookup"><span data-stu-id="fe54d-187">Set resource info: resource id and operation: READ, WRITE, EXECUTABLE.</span></span> |
| <span data-ttu-id="fe54d-188">***nx_lwm2m_client_resource_string_set***</span><span class="sxs-lookup"><span data-stu-id="fe54d-188">***nx_lwm2m_client_resource_string_set***</span></span> | <span data-ttu-id="fe54d-189">Указание значения ресурса в качестве строки.</span><span class="sxs-lookup"><span data-stu-id="fe54d-189">Set the resource value as string.</span></span> |
| <span data-ttu-id="fe54d-190">***nx_lwm2m_client_resource_integer32_set***</span><span class="sxs-lookup"><span data-stu-id="fe54d-190">***nx_lwm2m_client_resource_integer32_set***</span></span> | <span data-ttu-id="fe54d-191">Указание значения ресурса в виде 32-разрядного целого числа.</span><span class="sxs-lookup"><span data-stu-id="fe54d-191">Set the resource value as 32-Bit integer.</span></span> |
| <span data-ttu-id="fe54d-192">***nx_lwm2m_client_resource_integer64_set***</span><span class="sxs-lookup"><span data-stu-id="fe54d-192">***nx_lwm2m_client_resource_integer64_set***</span></span> | <span data-ttu-id="fe54d-193">Указание значения ресурса в виде 64-разрядного целого числа.</span><span class="sxs-lookup"><span data-stu-id="fe54d-193">Set the resource value as 64-Bit integer.</span></span> |
| <span data-ttu-id="fe54d-194">***nx_lwm2m_client_resource_float32_set***</span><span class="sxs-lookup"><span data-stu-id="fe54d-194">***nx_lwm2m_client_resource_float32_set***</span></span> | <span data-ttu-id="fe54d-195">Указание значения ресурса в виде 32-разрядного числа с плавающей точкой.</span><span class="sxs-lookup"><span data-stu-id="fe54d-195">Set the resource value as 32-Bit float.</span></span> |
| <span data-ttu-id="fe54d-196">***nx_lwm2m_client_resource_float64_set***</span><span class="sxs-lookup"><span data-stu-id="fe54d-196">***nx_lwm2m_client_resource_float64_set***</span></span> | <span data-ttu-id="fe54d-197">Указание значения ресурса в виде 64-разрядного числа с плавающей точкой.</span><span class="sxs-lookup"><span data-stu-id="fe54d-197">Set the resource value as 64-Bit float.</span></span> |
| <span data-ttu-id="fe54d-198">***nx_lwm2m_client_resource_boolean_set***</span><span class="sxs-lookup"><span data-stu-id="fe54d-198">***nx_lwm2m_client_resource_boolean_set***</span></span> | <span data-ttu-id="fe54d-199">Указание значения ресурса в качестве логического значения.</span><span class="sxs-lookup"><span data-stu-id="fe54d-199">Set the resource value as boolean.</span></span> |
| <span data-ttu-id="fe54d-200">***nx_lwm2m_client_resource_objlnk_set***</span><span class="sxs-lookup"><span data-stu-id="fe54d-200">***nx_lwm2m_client_resource_objlnk_set***</span></span> | <span data-ttu-id="fe54d-201">Указание значения ресурса в качестве ссылки на объект.</span><span class="sxs-lookup"><span data-stu-id="fe54d-201">Set the resource value as object link.</span></span> |
| <span data-ttu-id="fe54d-202">***nx_lwm2m_client_resource_opaque_set***</span><span class="sxs-lookup"><span data-stu-id="fe54d-202">***nx_lwm2m_client_resource_opaque_set***</span></span> | <span data-ttu-id="fe54d-203">Указание значения ресурса как непрозрачного.</span><span class="sxs-lookup"><span data-stu-id="fe54d-203">Set the resource value as opaque.</span></span> |
| <span data-ttu-id="fe54d-204">***nx_lwm2m_client_resource_instance_set***</span><span class="sxs-lookup"><span data-stu-id="fe54d-204">***nx_lwm2m_client_resource_instance_set***</span></span> | <span data-ttu-id="fe54d-205">Указание значения ресурса как экземпляра для нескольких ресурсов.</span><span class="sxs-lookup"><span data-stu-id="fe54d-205">Set the resource value as instance for multiple resource.</span></span> |
| <span data-ttu-id="fe54d-206">***nx_lwm2m_client_resource_dim_set***</span><span class="sxs-lookup"><span data-stu-id="fe54d-206">***nx_lwm2m_client_resource_dim_set***</span></span> | <span data-ttu-id="fe54d-207">Указание измерения ресурса для нескольких ресурсов для обнаружения.</span><span class="sxs-lookup"><span data-stu-id="fe54d-207">Set the resource dimension for multiple resource for discover.</span></span> |

<span data-ttu-id="fe54d-208">Для получения сведений о ресурсе и его значения существуют следующие функции.</span><span class="sxs-lookup"><span data-stu-id="fe54d-208">The following functions are provided for getting resource info and value.</span></span>

| <span data-ttu-id="fe54d-209">Имя&nbsp;функции</span><span class="sxs-lookup"><span data-stu-id="fe54d-209">Function&nbsp;Name</span></span> | <span data-ttu-id="fe54d-210">Описание</span><span class="sxs-lookup"><span data-stu-id="fe54d-210">Description</span></span> |
| --- | --- |
| <span data-ttu-id="fe54d-211">***nx_lwm2m_client_resource_info_get***</span><span class="sxs-lookup"><span data-stu-id="fe54d-211">***nx_lwm2m_client_resource_info_get***</span></span> | <span data-ttu-id="fe54d-212">Получение сведений о ресурсе: идентификатор ресурса и операция: READ, WRITE, EXECUTABLE.</span><span class="sxs-lookup"><span data-stu-id="fe54d-212">Get resource info: resource id and operation: READ, WRITE, EXECUTABLE.</span></span> |
| <span data-ttu-id="fe54d-213">***nx_lwm2m_client_resource_string_get***</span><span class="sxs-lookup"><span data-stu-id="fe54d-213">***nx_lwm2m_client_resource_string_get***</span></span> | <span data-ttu-id="fe54d-214">Получение значения строкового ресурса.</span><span class="sxs-lookup"><span data-stu-id="fe54d-214">Get the value of a string resource.</span></span> |
| <span data-ttu-id="fe54d-215">***nx_lwm2m_client_resource_integer32_get***</span><span class="sxs-lookup"><span data-stu-id="fe54d-215">***nx_lwm2m_client_resource_integer32_get***</span></span> | <span data-ttu-id="fe54d-216">Получение значения 32-разрядного целочисленного ресурса.</span><span class="sxs-lookup"><span data-stu-id="fe54d-216">Get the value of a 32-Bit integer resource.</span></span> |
| <span data-ttu-id="fe54d-217">***nx_lwm2m_client_resource_integer64_get***</span><span class="sxs-lookup"><span data-stu-id="fe54d-217">***nx_lwm2m_client_resource_integer64_get***</span></span> | <span data-ttu-id="fe54d-218">Получение значения 64-разрядного целочисленного ресурса.</span><span class="sxs-lookup"><span data-stu-id="fe54d-218">Get the value of a b4-Bit integer resource.</span></span> |
| <span data-ttu-id="fe54d-219">***nx_lwm2m_client_resource_float32_get***</span><span class="sxs-lookup"><span data-stu-id="fe54d-219">***nx_lwm2m_client_resource_float32_get***</span></span> | <span data-ttu-id="fe54d-220">Получение значения 32-разрядного ресурса с плавающей точкой.</span><span class="sxs-lookup"><span data-stu-id="fe54d-220">Get the value of a 32-Bit float resource.</span></span> |
| <span data-ttu-id="fe54d-221">***nx_lwm2m_client_resource_float64_get***</span><span class="sxs-lookup"><span data-stu-id="fe54d-221">***nx_lwm2m_client_resource_float64_get***</span></span> | <span data-ttu-id="fe54d-222">Получение значения 64-разрядного ресурса с плавающей точкой.</span><span class="sxs-lookup"><span data-stu-id="fe54d-222">Get the value of a 64-Bit float resource.</span></span> |
| <span data-ttu-id="fe54d-223">***nx_lwm2m_client_resource_boolean_get***</span><span class="sxs-lookup"><span data-stu-id="fe54d-223">***nx_lwm2m_client_resource_boolean_get***</span></span> | <span data-ttu-id="fe54d-224">Получение значения логического ресурса.</span><span class="sxs-lookup"><span data-stu-id="fe54d-224">Get the value of a Boolean resource.</span></span> |
| <span data-ttu-id="fe54d-225">***nx_lwm2m_client_resource_objlnk_get***</span><span class="sxs-lookup"><span data-stu-id="fe54d-225">***nx_lwm2m_client_resource_objlnk_get***</span></span> | <span data-ttu-id="fe54d-226">Получение значения ресурса в виде ссылки на объект.</span><span class="sxs-lookup"><span data-stu-id="fe54d-226">Get the value of an object link resource.</span></span> |
| <span data-ttu-id="fe54d-227">***nx_lwm2m_client_resource_opaque_get***</span><span class="sxs-lookup"><span data-stu-id="fe54d-227">***nx_lwm2m_client_resource_opaque_get***</span></span> | <span data-ttu-id="fe54d-228">Получение значения непрозрачного ресурса.</span><span class="sxs-lookup"><span data-stu-id="fe54d-228">Get the value of an opaque resource.</span></span> |
| <span data-ttu-id="fe54d-229">***nx_lwm2m_client_resource_instance_get***</span><span class="sxs-lookup"><span data-stu-id="fe54d-229">***nx_lwm2m_client_resource_instance_get***</span></span> | <span data-ttu-id="fe54d-230">Получение экземпляра ресурса для нескольких ресурсов.</span><span class="sxs-lookup"><span data-stu-id="fe54d-230">Get the resource instance for multiple resource.</span></span> |
| <span data-ttu-id="fe54d-231">***nx_lwm2m_client_resource_dim_get***</span><span class="sxs-lookup"><span data-stu-id="fe54d-231">***nx_lwm2m_client_resource_dim_get***</span></span> | <span data-ttu-id="fe54d-232">Получение измерения ресурса для нескольких ресурсов.</span><span class="sxs-lookup"><span data-stu-id="fe54d-232">Get the resource dimension for multiple resource.</span></span> |

## <a name="object-implementation"></a><span data-ttu-id="fe54d-233">Реализация объектов</span><span class="sxs-lookup"><span data-stu-id="fe54d-233">Object Implementation</span></span>

<span data-ttu-id="fe54d-234">Клиент LWM2M реализует обязательные объекты OMA LWM2M: Security (0), Server (1), Access Control (2) и Device (3).</span><span class="sxs-lookup"><span data-stu-id="fe54d-234">The LWM2M Client implements the mandatory OMA LWM2M Objects: Security (0), Server (1), Access Control (2) and Device (3).</span></span> <span data-ttu-id="fe54d-235">Другие объекты для конкретного устройства должны быть реализованы приложением.</span><span class="sxs-lookup"><span data-stu-id="fe54d-235">Other device specific objects must be implemented by the application.</span></span>

<span data-ttu-id="fe54d-236">Для определения объекта используются две структуры данных: структура NX_LWM2M_CLIENT_OBJECT определяет реализацию объекта, идентификатор объекта и методы объекта, а структура NX_LWM2M_CLIENT_OBJECT_INSTANCE содержит данные экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="fe54d-236">Two data structures are used to define an Object: the NX_LWM2M_CLIENT_OBJECT structure defines the Object implementation, including the Object ID and the object methods, and the NX_LWM2M_CLIENT_OBJECT_INSTANCE structure contains the data of an Object Instance.</span></span>

<span data-ttu-id="fe54d-237">Для этого предоставляются следующие функции.</span><span class="sxs-lookup"><span data-stu-id="fe54d-237">The following functions are provided.</span></span>

| <span data-ttu-id="fe54d-238">Имя&nbsp;функции</span><span class="sxs-lookup"><span data-stu-id="fe54d-238">Function&nbsp;Name</span></span> | <span data-ttu-id="fe54d-239">Описание</span><span class="sxs-lookup"><span data-stu-id="fe54d-239">Description</span></span> |
| --- | --- |
| <span data-ttu-id="fe54d-240">***nx_lwm2m_client_object_add***</span><span class="sxs-lookup"><span data-stu-id="fe54d-240">***nx_lwm2m_client_object_add***</span></span> | <span data-ttu-id="fe54d-241">Добавление реализации объекта в клиент LwM2M.</span><span class="sxs-lookup"><span data-stu-id="fe54d-241">Add object implementation to the LwM2M Client.</span></span> |
| <span data-ttu-id="fe54d-242">***nx_lwm2m_client_object_remove***</span><span class="sxs-lookup"><span data-stu-id="fe54d-242">***nx_lwm2m_client_object_remove***</span></span> | <span data-ttu-id="fe54d-243">Удаление реализации объекта из клиента LwM2M.</span><span class="sxs-lookup"><span data-stu-id="fe54d-243">Remove object implementation from the LwM2M Client.</span></span> |
| <span data-ttu-id="fe54d-244">***nx_lwm2m_client_object_instance_add***</span><span class="sxs-lookup"><span data-stu-id="fe54d-244">***nx_lwm2m_client_object_instance_add***</span></span> | <span data-ttu-id="fe54d-245">Добавление экземпляра объекта в объект.</span><span class="sxs-lookup"><span data-stu-id="fe54d-245">Add object instance to the Object.</span></span> |
| <span data-ttu-id="fe54d-246">***nx_lwm2m_client_object_instance_remove***</span><span class="sxs-lookup"><span data-stu-id="fe54d-246">***nx_lwm2m_client_object_instance_remove***</span></span> | <span data-ttu-id="fe54d-247">Удаление экземпляра объекта из объекта.</span><span class="sxs-lookup"><span data-stu-id="fe54d-247">Remove object instance from the Object.</span></span> |

<span data-ttu-id="fe54d-248">Функция обратного вызова метода объекта имеет сигнатуру, показанную ниже.</span><span class="sxs-lookup"><span data-stu-id="fe54d-248">The object method callback function has signature shown below.</span></span>

```c
typedef UINT (*NX_LWM2M_CLIENT_OBJECT_OPERATION_CALLBACK)(
    UINT operation, 
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr,
    NX_LWM2M_CLIENT_RESOURCE *resource,
    UINT *resource_count,
    VOID *args_ptr,
    UINT args_length);
```

### <a name="the-read-method"></a><span data-ttu-id="fe54d-249">Метод Read</span><span class="sxs-lookup"><span data-stu-id="fe54d-249">The ‘Read’ Method</span></span>

<span data-ttu-id="fe54d-250">Метод Read используется для чтения значений ресурсов из экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="fe54d-250">The ‘Read’ method is used to read Resource values from an Object Instance.</span></span> <span data-ttu-id="fe54d-251">Параметры определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="fe54d-251">The parameters are defined as follows.</span></span>

| <span data-ttu-id="fe54d-252">Параметр</span><span class="sxs-lookup"><span data-stu-id="fe54d-252">Parameter</span></span> | <span data-ttu-id="fe54d-253">Описание</span><span class="sxs-lookup"><span data-stu-id="fe54d-253">Description</span></span> |
| --- | --- |
| <span data-ttu-id="fe54d-254">**operation**</span><span class="sxs-lookup"><span data-stu-id="fe54d-254">**operation**</span></span> | <span data-ttu-id="fe54d-255">**NX_LWM2M_CLIENT_OBJECT_READ**</span><span class="sxs-lookup"><span data-stu-id="fe54d-255">**NX_LWM2M_CLIENT_OBJECT_READ**</span></span> |
| <span data-ttu-id="fe54d-256">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="fe54d-256">**object_ptr**</span></span> | <span data-ttu-id="fe54d-257">Указатель на реализацию объекта.</span><span class="sxs-lookup"><span data-stu-id="fe54d-257">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="fe54d-258">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="fe54d-258">**instance_ptr**</span></span> | <span data-ttu-id="fe54d-259">Указатель на экземпляр объекта.</span><span class="sxs-lookup"><span data-stu-id="fe54d-259">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="fe54d-260">**resource**</span><span class="sxs-lookup"><span data-stu-id="fe54d-260">**resource**</span></span> | <span data-ttu-id="fe54d-261">Указатель на массив **NX_LWM2M_CLIENT_RESOURCE**, который содержит идентификаторы считываемых ресурсов.</span><span class="sxs-lookup"><span data-stu-id="fe54d-261">Pointer to an array of **NX_LWM2M_CLIENT_RESOURCE** containing the IDs of the resources to read.</span></span> <span data-ttu-id="fe54d-262">При возврате этот массив заполняется соответствующими типами и значениями.</span><span class="sxs-lookup"><span data-stu-id="fe54d-262">On return the array is filled with corresponding types and values.</span></span> |
| <span data-ttu-id="fe54d-263">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="fe54d-263">**resource_count**</span></span> | <span data-ttu-id="fe54d-264">Указатель на количество считываемых ресурсов.</span><span class="sxs-lookup"><span data-stu-id="fe54d-264">Pointer to the number of resources to read.</span></span> |
| <span data-ttu-id="fe54d-265">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="fe54d-265">**args_ptr**</span></span> | <span data-ttu-id="fe54d-266">Неиспользуемый параметр для чтения.</span><span class="sxs-lookup"><span data-stu-id="fe54d-266">Unused parameter for read.</span></span> |
| <span data-ttu-id="fe54d-267">**args_length**</span><span class="sxs-lookup"><span data-stu-id="fe54d-267">**args_length**</span></span> | <span data-ttu-id="fe54d-268">Неиспользуемый параметр для чтения.</span><span class="sxs-lookup"><span data-stu-id="fe54d-268">Unused parameter for read.</span></span> |

### <a name="the-discover-method"></a><span data-ttu-id="fe54d-269">Метод Discover</span><span class="sxs-lookup"><span data-stu-id="fe54d-269">The ‘Discover’ Method</span></span>

<span data-ttu-id="fe54d-270">Метод Discover используется для получения списка всех ресурсов, реализованных объектом.</span><span class="sxs-lookup"><span data-stu-id="fe54d-270">The ‘Discover’ method is used to retrieve the list of all Resources implemented by an Object.</span></span> <span data-ttu-id="fe54d-271">Параметры определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="fe54d-271">The parameters are defined as follows.</span></span>

| <span data-ttu-id="fe54d-272">Параметр</span><span class="sxs-lookup"><span data-stu-id="fe54d-272">Parameter</span></span> | <span data-ttu-id="fe54d-273">Описание</span><span class="sxs-lookup"><span data-stu-id="fe54d-273">Description</span></span> |
| --- | --- |
| <span data-ttu-id="fe54d-274">**operation**</span><span class="sxs-lookup"><span data-stu-id="fe54d-274">**operation**</span></span> | <span data-ttu-id="fe54d-275">**NX_LWM2M_CLIENT_OBJECT_DISCOVER**</span><span class="sxs-lookup"><span data-stu-id="fe54d-275">**NX_LWM2M_CLIENT_OBJECT_DISCOVER**</span></span> |
| <span data-ttu-id="fe54d-276">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="fe54d-276">**object_ptr**</span></span> | <span data-ttu-id="fe54d-277">Указатель на реализацию объекта.</span><span class="sxs-lookup"><span data-stu-id="fe54d-277">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="fe54d-278">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="fe54d-278">**instance_ptr**</span></span> | <span data-ttu-id="fe54d-279">Указатель на экземпляр объекта.</span><span class="sxs-lookup"><span data-stu-id="fe54d-279">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="fe54d-280">**resource**</span><span class="sxs-lookup"><span data-stu-id="fe54d-280">**resource**</span></span> | <span data-ttu-id="fe54d-281">Указатель на массив NX_LWM2M_CLIENT_RESOURCE.</span><span class="sxs-lookup"><span data-stu-id="fe54d-281">Pointer to an array of NX_LWM2M_CLIENT_RESOURCE.</span></span> <span data-ttu-id="fe54d-282">При возврате этот массив заполняется соответствующими сведениями о ресурсах.</span><span class="sxs-lookup"><span data-stu-id="fe54d-282">On return the array is filled with corresponding resource info.</span></span> |
| <span data-ttu-id="fe54d-283">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="fe54d-283">**resource_count**</span></span> | <span data-ttu-id="fe54d-284">Указатель на количество обнаруживаемых ресурсов.</span><span class="sxs-lookup"><span data-stu-id="fe54d-284">Pointer to the number of resources to discover.</span></span> <span data-ttu-id="fe54d-285">При возврате этот параметр должен быть обновлен как истинное значение.</span><span class="sxs-lookup"><span data-stu-id="fe54d-285">On return this parameter must be updated as the true value.</span></span> |
| <span data-ttu-id="fe54d-286">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="fe54d-286">**args_ptr**</span></span> | <span data-ttu-id="fe54d-287">Неиспользуемый параметр для обнаружения.</span><span class="sxs-lookup"><span data-stu-id="fe54d-287">Unused parameter for discover.</span></span> |
| <span data-ttu-id="fe54d-288">**args_length**</span><span class="sxs-lookup"><span data-stu-id="fe54d-288">**args_length**</span></span> | <span data-ttu-id="fe54d-289">Неиспользуемый параметр для обнаружения.</span><span class="sxs-lookup"><span data-stu-id="fe54d-289">Unused parameter for discover.</span></span> |

### <a name="the-write-method"></a><span data-ttu-id="fe54d-290">Метод Write</span><span class="sxs-lookup"><span data-stu-id="fe54d-290">The ‘Write’ Method</span></span>

<span data-ttu-id="fe54d-291">Метод Write используется для обновления или замены ресурсов экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="fe54d-291">The ‘Write’ method is used to update or replace resources of an Object Instance.</span></span> <span data-ttu-id="fe54d-292">Параметры определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="fe54d-292">The parameters are defined as follows.</span></span>

| <span data-ttu-id="fe54d-293">Параметр</span><span class="sxs-lookup"><span data-stu-id="fe54d-293">Parameter</span></span>  | <span data-ttu-id="fe54d-294">Описание</span><span class="sxs-lookup"><span data-stu-id="fe54d-294">Description</span></span> |
| --- | --- |
| <span data-ttu-id="fe54d-295">**operation**</span><span class="sxs-lookup"><span data-stu-id="fe54d-295">**operation**</span></span> | <span data-ttu-id="fe54d-296">**NX_LWM2M_CLIENT_OBJECT_WRITE**</span><span class="sxs-lookup"><span data-stu-id="fe54d-296">**NX_LWM2M_CLIENT_OBJECT_WRITE**</span></span> |
| <span data-ttu-id="fe54d-297">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="fe54d-297">**object_ptr**</span></span> | <span data-ttu-id="fe54d-298">Указатель на реализацию объекта.</span><span class="sxs-lookup"><span data-stu-id="fe54d-298">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="fe54d-299">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="fe54d-299">**instance_ptr**</span></span> | <span data-ttu-id="fe54d-300">Указатель на экземпляр объекта.</span><span class="sxs-lookup"><span data-stu-id="fe54d-300">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="fe54d-301">**resource**</span><span class="sxs-lookup"><span data-stu-id="fe54d-301">**resource**</span></span> | <span data-ttu-id="fe54d-302">Указатель на массив **NX_LWM2M_CLIENT_RESOURCE**, который содержит идентификаторы считываемых ресурсов.</span><span class="sxs-lookup"><span data-stu-id="fe54d-302">Pointer to an array of **NX_LWM2M_CLIENT_RESOURCE** containing the IDs of the resources to read.</span></span> <span data-ttu-id="fe54d-303">При возврате этот массив заполняется соответствующими типами и значениями.</span><span class="sxs-lookup"><span data-stu-id="fe54d-303">On return the array is filled with corresponding types and values.</span></span> |
| <span data-ttu-id="fe54d-304">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="fe54d-304">**resource_count**</span></span> | <span data-ttu-id="fe54d-305">Указатель на количество обнаруживаемых ресурсов.</span><span class="sxs-lookup"><span data-stu-id="fe54d-305">Pointer to the number of resources to discover.</span></span> |
| <span data-ttu-id="fe54d-306">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="fe54d-306">**args_ptr**</span></span> | <span data-ttu-id="fe54d-307">Флаги для записи.</span><span class="sxs-lookup"><span data-stu-id="fe54d-307">Write flags.</span></span> |
| <span data-ttu-id="fe54d-308">**args_length**</span><span class="sxs-lookup"><span data-stu-id="fe54d-308">**args_length**</span></span> | <span data-ttu-id="fe54d-309">Длина аргументов.</span><span class="sxs-lookup"><span data-stu-id="fe54d-309">The length of the arguments.</span></span> |

<span data-ttu-id="fe54d-310">Для параметра *flag* можно указать следующие операции записи.</span><span class="sxs-lookup"><span data-stu-id="fe54d-310">The following write operations can be specified to the *flag* parameter.</span></span>

| <span data-ttu-id="fe54d-311">Операция</span><span class="sxs-lookup"><span data-stu-id="fe54d-311">Operation</span></span> | <span data-ttu-id="fe54d-312">Действие</span><span class="sxs-lookup"><span data-stu-id="fe54d-312">Action</span></span> | <span data-ttu-id="fe54d-313">Описание</span><span class="sxs-lookup"><span data-stu-id="fe54d-313">Description</span></span> |
| --- | ---| --- |
| <span data-ttu-id="fe54d-314">0</span><span class="sxs-lookup"><span data-stu-id="fe54d-314">0</span></span> | <span data-ttu-id="fe54d-315">Частичное обновление</span><span class="sxs-lookup"><span data-stu-id="fe54d-315">Partial Update</span></span> | <span data-ttu-id="fe54d-316">Добавляет или обновляет ресурсы, указанные в новом значении, и сохраняет остальные существующие ресурсы без изменений.</span><span class="sxs-lookup"><span data-stu-id="fe54d-316">Adds or updates Resources provided in the new value and leaves other existing Resources unchanged.</span></span>
| <span data-ttu-id="fe54d-317">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE**</span><span class="sxs-lookup"><span data-stu-id="fe54d-317">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE**</span></span> | <span data-ttu-id="fe54d-318">Замена экземпляра</span><span class="sxs-lookup"><span data-stu-id="fe54d-318">Replace Instance</span></span> | <span data-ttu-id="fe54d-319">Заменяет экземпляр объекта новыми указанными значениями ресурсов.</span><span class="sxs-lookup"><span data-stu-id="fe54d-319">Replaces the Object Instance with the new provided resource values.</span></span>
| <span data-ttu-id="fe54d-320">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE**</span><span class="sxs-lookup"><span data-stu-id="fe54d-320">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE**</span></span> |  <span data-ttu-id="fe54d-321">Замена ресурса</span><span class="sxs-lookup"><span data-stu-id="fe54d-321">Replace Resource</span></span> | <span data-ttu-id="fe54d-322">Заменяет ресурсы новыми указанными значениями ресурсов (используется для замены нескольких ресурсов).</span><span class="sxs-lookup"><span data-stu-id="fe54d-322">Replaces the Resources with the new provided resource values (used to replace Multiple Resources).</span></span> |
| <span data-ttu-id="fe54d-323">**NX_LWM2M_CLIENT_OBJECT_WRITE_CREATE**</span><span class="sxs-lookup"><span data-stu-id="fe54d-323">**NX_LWM2M_CLIENT_OBJECT_WRITE_CREATE**</span></span> | <span data-ttu-id="fe54d-324">создание экземпляра</span><span class="sxs-lookup"><span data-stu-id="fe54d-324">Create Instance</span></span> | <span data-ttu-id="fe54d-325">Инициализирует новый экземпляр объекта с указанными значениями ресурсов (вызывается из метода **_nx_lwm2m_object_create_**).</span><span class="sxs-lookup"><span data-stu-id="fe54d-325">Initializes the newly created Object Instance with the provided resource values (called from the **_nx_lwm2m_object_create_** method).</span></span> |
| <span data-ttu-id="fe54d-326">**NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP**</span><span class="sxs-lookup"><span data-stu-id="fe54d-326">**NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP**</span></span> | <span data-ttu-id="fe54d-327">Запись при начальной загрузке</span><span class="sxs-lookup"><span data-stu-id="fe54d-327">Bootstrap Write</span></span> | <span data-ttu-id="fe54d-328">Вызывается во время начальной загрузки.</span><span class="sxs-lookup"><span data-stu-id="fe54d-328">Called during Bootstrap sequence.</span></span> |

### <a name="the-execute-method"></a><span data-ttu-id="fe54d-329">Метод Execute</span><span class="sxs-lookup"><span data-stu-id="fe54d-329">The ‘Execute’ Method</span></span>

<span data-ttu-id="fe54d-330">Метод Execute реализует выполнение ресурса объекта.</span><span class="sxs-lookup"><span data-stu-id="fe54d-330">The ‘Execute’ method implements the execution of an Object Resource.</span></span>

<span data-ttu-id="fe54d-331">Входные параметры определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="fe54d-331">The input parameters are defined as follows.</span></span>

| <span data-ttu-id="fe54d-332">Параметр</span><span class="sxs-lookup"><span data-stu-id="fe54d-332">Parameter</span></span>  | <span data-ttu-id="fe54d-333">Описание</span><span class="sxs-lookup"><span data-stu-id="fe54d-333">Description</span></span> |
| --- | --- |
| <span data-ttu-id="fe54d-334">**operation**</span><span class="sxs-lookup"><span data-stu-id="fe54d-334">**operation**</span></span> | <span data-ttu-id="fe54d-335">NX_LWM2M_CLIENT_OBJECT_EXECUTE</span><span class="sxs-lookup"><span data-stu-id="fe54d-335">NX_LWM2M_CLIENT_OBJECT_EXECUTE</span></span> |
| <span data-ttu-id="fe54d-336">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="fe54d-336">**object_ptr**</span></span> | <span data-ttu-id="fe54d-337">Указатель на реализацию объекта.</span><span class="sxs-lookup"><span data-stu-id="fe54d-337">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="fe54d-338">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="fe54d-338">**instance_ptr**</span></span> | <span data-ttu-id="fe54d-339">Указатель на экземпляр объекта.</span><span class="sxs-lookup"><span data-stu-id="fe54d-339">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="fe54d-340">**resource**</span><span class="sxs-lookup"><span data-stu-id="fe54d-340">**resource**</span></span> | <span data-ttu-id="fe54d-341">Указатель на массив **NX_LWM2M_CLIENT_RESOURCE**, который содержит идентификаторы считываемых ресурсов.</span><span class="sxs-lookup"><span data-stu-id="fe54d-341">Pointer to an array of **NX_LWM2M_CLIENT_RESOURCE** containing the IDs of the resources to read.</span></span> <span data-ttu-id="fe54d-342">При возврате этот массив заполняется соответствующими типами и значениями.</span><span class="sxs-lookup"><span data-stu-id="fe54d-342">On return the array is filled with corresponding types and values.</span></span> |
| <span data-ttu-id="fe54d-343">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="fe54d-343">**resource_count**</span></span> | <span data-ttu-id="fe54d-344">Указатель на количество обнаруживаемых ресурсов.</span><span class="sxs-lookup"><span data-stu-id="fe54d-344">Pointer to the number of resources to discover.</span></span> |
| <span data-ttu-id="fe54d-345">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="fe54d-345">**args_ptr**</span></span> | <span data-ttu-id="fe54d-346">Указатель на аргументы.</span><span class="sxs-lookup"><span data-stu-id="fe54d-346">Pointer to the arguments.</span></span> |
| <span data-ttu-id="fe54d-347">**args_length**</span><span class="sxs-lookup"><span data-stu-id="fe54d-347">**args_length**</span></span> | <span data-ttu-id="fe54d-348">Длина аргументов.</span><span class="sxs-lookup"><span data-stu-id="fe54d-348">The length of the arguments.</span></span>  |

<span data-ttu-id="fe54d-349">Функция должна возвращать **NX_LWM2M_CLIENT_NOT_FOUND**, если идентификатор ресурса не существует, или **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED**, если он не поддерживает выполнение.</span><span class="sxs-lookup"><span data-stu-id="fe54d-349">The function must return **NX_LWM2M_CLIENT_NOT_FOUND** if the Resource ID doesn’t exist, or **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** if it doesn’t support execution.</span></span>

### <a name="the-create-method"></a><span data-ttu-id="fe54d-350">Метод Create</span><span class="sxs-lookup"><span data-stu-id="fe54d-350">The ‘Create’ Method</span></span>

<span data-ttu-id="fe54d-351">Метод Create реализует создание нового экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="fe54d-351">The ‘Create’ method implements the creation of a new Object Instance.</span></span>

<span data-ttu-id="fe54d-352">Входные параметры определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="fe54d-352">The input parameters are defined as follows.</span></span>

| <span data-ttu-id="fe54d-353">Параметр</span><span class="sxs-lookup"><span data-stu-id="fe54d-353">Parameter</span></span>  | <span data-ttu-id="fe54d-354">Описание</span><span class="sxs-lookup"><span data-stu-id="fe54d-354">Description</span></span> |
| --- | --- |
| <span data-ttu-id="fe54d-355">**operation**</span><span class="sxs-lookup"><span data-stu-id="fe54d-355">**operation**</span></span> | <span data-ttu-id="fe54d-356">**NX_LWM2M_CLIENT_OBJECT_CREATE**</span><span class="sxs-lookup"><span data-stu-id="fe54d-356">**NX_LWM2M_CLIENT_OBJECT_CREATE**</span></span> |
| <span data-ttu-id="fe54d-357">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="fe54d-357">**object_ptr**</span></span> | <span data-ttu-id="fe54d-358">Указатель на реализацию объекта.</span><span class="sxs-lookup"><span data-stu-id="fe54d-358">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="fe54d-359">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="fe54d-359">**instance_ptr**</span></span> | <span data-ttu-id="fe54d-360">Неиспользуемый параметр.</span><span class="sxs-lookup"><span data-stu-id="fe54d-360">Unused parameter.</span></span> |
| <span data-ttu-id="fe54d-361">**resource**</span><span class="sxs-lookup"><span data-stu-id="fe54d-361">**resource**</span></span> | <span data-ttu-id="fe54d-362">Указатель на массив **NX_LWM2M_CLIENT_RESOURCE**, который содержит идентификаторы считываемых ресурсов.</span><span class="sxs-lookup"><span data-stu-id="fe54d-362">Pointer to an array of **NX_LWM2M_CLIENT_RESOURCE** containing the IDs of the resources to read.</span></span> <span data-ttu-id="fe54d-363">При возврате этот массив заполняется соответствующими типами и значениями.</span><span class="sxs-lookup"><span data-stu-id="fe54d-363">On return the array is filled with corresponding types and values.</span></span> |
| <span data-ttu-id="fe54d-364">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="fe54d-364">**resource_count**</span></span> | <span data-ttu-id="fe54d-365">Указатель на количество обнаруживаемых ресурсов.</span><span class="sxs-lookup"><span data-stu-id="fe54d-365">Pointer to the number of resources to discover.</span></span> |
| <span data-ttu-id="fe54d-366">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="fe54d-366">**args_ptr**</span></span> | <span data-ttu-id="fe54d-367">Идентификатор экземпляра объекта.</span><span class="sxs-lookup"><span data-stu-id="fe54d-367">Object instance id.</span></span> |
| <span data-ttu-id="fe54d-368">**args_length**</span><span class="sxs-lookup"><span data-stu-id="fe54d-368">**args_length**</span></span> | <span data-ttu-id="fe54d-369">Длина аргументов.</span><span class="sxs-lookup"><span data-stu-id="fe54d-369">The length of the arguments.</span></span> |

### <a name="the-delete-method"></a><span data-ttu-id="fe54d-370">Метод Delete</span><span class="sxs-lookup"><span data-stu-id="fe54d-370">The ‘Delete’ Method</span></span>

<span data-ttu-id="fe54d-371">Метод Delete реализует удаление экземпляра объекта. Входные параметры определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="fe54d-371">The ‘Delete’ method implements the deletion of an object instance, the input parameters are defined as follows.</span></span>

| <span data-ttu-id="fe54d-372">Параметр</span><span class="sxs-lookup"><span data-stu-id="fe54d-372">Parameter</span></span>  | <span data-ttu-id="fe54d-373">Описание</span><span class="sxs-lookup"><span data-stu-id="fe54d-373">Description</span></span> |
| --- | --- |
| <span data-ttu-id="fe54d-374">**operation**</span><span class="sxs-lookup"><span data-stu-id="fe54d-374">**operation**</span></span> | <span data-ttu-id="fe54d-375">NX_LWM2M_CLIENT_OBJECT_DELETE</span><span class="sxs-lookup"><span data-stu-id="fe54d-375">NX_LWM2M_CLIENT_OBJECT_DELETE</span></span> |
| <span data-ttu-id="fe54d-376">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="fe54d-376">**object_ptr**</span></span> | <span data-ttu-id="fe54d-377">Указатель на реализацию объекта.</span><span class="sxs-lookup"><span data-stu-id="fe54d-377">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="fe54d-378">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="fe54d-378">**instance_ptr**</span></span> | <span data-ttu-id="fe54d-379">Указатель на экземпляр объекта.</span><span class="sxs-lookup"><span data-stu-id="fe54d-379">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="fe54d-380">**resource**</span><span class="sxs-lookup"><span data-stu-id="fe54d-380">**resource**</span></span> | <span data-ttu-id="fe54d-381">Неиспользуемый параметр.</span><span class="sxs-lookup"><span data-stu-id="fe54d-381">Unused parameter.</span></span> |
| <span data-ttu-id="fe54d-382">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="fe54d-382">**resource_count**</span></span> | <span data-ttu-id="fe54d-383">Неиспользуемый параметр.</span><span class="sxs-lookup"><span data-stu-id="fe54d-383">Unused parameter.</span></span> |
| <span data-ttu-id="fe54d-384">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="fe54d-384">**args_ptr**</span></span> | <span data-ttu-id="fe54d-385">Неиспользуемый параметр.</span><span class="sxs-lookup"><span data-stu-id="fe54d-385">Unused parameter.</span></span> |
| <span data-ttu-id="fe54d-386">**args_length**</span><span class="sxs-lookup"><span data-stu-id="fe54d-386">**args_length**</span></span> | <span data-ttu-id="fe54d-387">Неиспользуемый параметр.</span><span class="sxs-lookup"><span data-stu-id="fe54d-387">Unused parameter.</span></span> |

<span data-ttu-id="fe54d-388">При успешном выполнении объект должен освободить данные экземпляра объекта и любые другие ресурсы, выделенные экземпляром.</span><span class="sxs-lookup"><span data-stu-id="fe54d-388">On success the Object must release the Object Instance data and any other resource allocated by the instance.</span></span>

## <a name="example-of-lwm2m-client-application"></a><span data-ttu-id="fe54d-389">Пример клиентского приложения LWM2M</span><span class="sxs-lookup"><span data-stu-id="fe54d-389">Example of LWM2M Client Application</span></span>

<span data-ttu-id="fe54d-390">Следующий код представляет собой пример простого клиентского приложения LWM2M, которое реализует пользовательское устройство, состоящее из датчика температуры и выключателя света.</span><span class="sxs-lookup"><span data-stu-id="fe54d-390">The following code is an example of a simple LWM2M Client Application which implements a custom device consisting of a temperature sensor and a light switch.</span></span>

<span data-ttu-id="fe54d-391">Это устройство позволяет серверу считывать значение датчика температуры и логическое состояние выключателя света, а также устанавливать этот выключатель в положения "Включено" или "Выключено".</span><span class="sxs-lookup"><span data-stu-id="fe54d-391">The device allows a server to read the value of the temperature sensor and the boolean state of the light switch, and to set the light switch to on/off.</span></span>

```c
#include "nx_lwm2m_client.h"


/* Custom Object implementation. */

/* Temperature Object ID and resource IDs. */
#define IPSO_TEMPERATURE_OBJECT_ID   3303

#define IPSO_RESOURCE_MIN_VALUE      5601
#define IPSO_RESOURCE_MAX_VALUE      5602
#define IPSO_RESOURCE_RESET_MINMAX   5605
#define IPSO_RESOURCE_VALUE          5700
#define IPSO_RESOURCE_UNITS          5701

/* Actuation Object ID and resource IDs. */
#define IPSO_ACTUATION_OBJECT_ID     3306

#define IPSO_RESOURCE_ONOFF          5850

/* Define the Temperature Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_CLIENT_OBJECT_INSTANCE    object_instance;

    /* Resources Data */
    NX_LWM2M_FLOAT32                   temperature;
    NX_LWM2M_FLOAT32                   min_temperature;
    NX_LWM2M_FLOAT32                   max_temperature;

} IPSO_TEMPERATURE_INSTANCE;

/* Define the Actuation Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_CLIENT_OBJECT_INSTANCE    object_instance;

    /* Resources Data */
    NX_LWM2M_BOOL                      onoff;

} IPSO_ACTUATION_INSTANCE;

/* IPSO Temperature */
/* Define the 'Read' Method */
UINT ipso_temperature_read(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count)
{
IPSO_TEMPERATURE_INSTANCE *temp = ((IPSO_TEMPERATURE_INSTANCE *) instance_ptr);
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_MIN_VALUE:

            /* return the minimum measured temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> min_temperature);
            break;

        case IPSO_RESOURCE_MAX_VALUE:

            /* return the maximum measured temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> max_temperature);
            break;

        case IPSO_RESOURCE_VALUE:

            /* return the temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> temperature);
            break;

        case IPSO_RESOURCE_RESET_MINMAX:

            /* Not readable */
            return(NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED);

        case IPSO_RESOURCE_UNITS:

            /* return the temperature units */
            nx_lwm2m_client_resource_string_set(&resource[i], "Cel", 3);
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}

/* Define the 'Discover' method */
UINT ipso_temperature_discover(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resources, UINT *resource_count)
{
    if (*resource_count < 5)
    {
        return(NX_LWM2M_CLIENT_BUFFER_TOO_SMALL);
    }

    /* return the list of supported resources IDs */
    *resource_count = 5;
    nx_lwm2m_client_resource_info_set(&resources[0], IPSO_RESOURCE_MIN_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[1], IPSO_RESOURCE_MAX_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[2], IPSO_RESOURCE_RESET_MINMAX, NX_LWM2M_CLIENT_RESOURCE_OPERATION_EXECUTABLE);
    nx_lwm2m_client_resource_info_set(&resources[3], IPSO_RESOURCE_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[4], IPSO_RESOURCE_UNITS, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);

    return(NX_SUCCESS);
}

/* Define the 'Execute' method */
UINT ipso_temperature_execute(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, const CHAR *args_ptr, UINT args_length)
{
IPSO_TEMPERATURE_INSTANCE *temp = ((IPSO_TEMPERATURE_INSTANCE *) instance_ptr);
NX_LWM2M_CLIENT_RESOURCE value;
NX_LWM2M_ID resource_id;

    /* Get resource id */
    nx_lwm2m_client_resource_info_get(resource, &resource_id, NX_NULL);

    switch (resource_id)
    {

    case IPSO_RESOURCE_MIN_VALUE:
    case IPSO_RESOURCE_MAX_VALUE:
    case IPSO_RESOURCE_VALUE:
    case IPSO_RESOURCE_UNITS:

        /* read-only resource */
        return(NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED);

    case IPSO_RESOURCE_RESET_MINMAX:

        /* reset min/max values to current temperature */
        nx_lwm2m_client_resource_float32_set(&value, temp -> temperature);
        if (temp -> min_temperature != temp -> temperature)
        {
            temp -> min_temperature = temp -> temperature;
            nx_lwm2m_client_resource_info_set(&value, IPSO_RESOURCE_MIN_VALUE, NX_NULL);
            nx_lwm2m_client_object_resource_changed(object_ptr, instance_ptr, &value);
        }
        if (temp -> max_temperature != temp -> temperature)
        {
            temp -> max_temperature = temp -> temperature;
            nx_lwm2m_client_resource_info_set(&value, IPSO_RESOURCE_MAX_VALUE, NX_NULL);
            nx_lwm2m_client_object_resource_changed(object_ptr, instance_ptr, &value);
        }

        break;

    default:

        /* unknown resource ID */
        return(NX_LWM2M_CLIENT_NOT_FOUND);
    }

    return(NX_SUCCESS);
}

/* Define the operation callback function of Temperature Object */
UINT ipso_temperature_operation(UINT operation, NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT *resource_count, VOID *args_ptr, UINT args_length)
{

    switch (operation)
    {
    case NX_LWM2M_CLIENT_OBJECT_READ:

        /* Call read function */
        return ipso_temperature_read(object_ptr, object_instance_ptr, resource, *resource_count);
    case NX_LWM2M_CLIENT_OBJECT_DISCOVER:

        /* Call discover function */
        return ipso_temperature_discover(object_ptr, object_instance_ptr, resource, resource_count);

    case NX_LWM2M_CLIENT_OBJECT_EXECUTE:

        /* Call execute function */
        return ipso_temperature_execute(object_ptr, object_instance_ptr, resource, args_ptr, args_length);
    default:

        /*Unsupported operation */
        return(NX_LWM2M_CLIENT_NOT_SUPPORTED);
    }
}


/* IPSO Actuation */
/* Define the 'Read' Method */
UINT ipso_actuation_read(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count)
{
IPSO_ACTUATION_INSTANCE *act = ((IPSO_ACTUATION_INSTANCE *) instance_ptr);
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_ONOFF:

            /* return the on/off value */
            nx_lwm2m_client_resource_boolean_set(&resource[i], act -> onoff);
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}


/* Define the 'Discover' method */
UINT ipso_actuation_discover(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resources, UINT *resource_count)
{
    if (*resource_count < 1)
    {
        return(NX_LWM2M_CLIENT_BUFFER_TOO_SMALL);
    }

    /* return the list of supported resources IDs */
    *resource_count = 1;
    nx_lwm2m_client_resource_info_set(&resources[0], IPSO_RESOURCE_ONOFF, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ_WRITE);

    return(NX_SUCCESS);
}

/* Define the 'Write' method */
UINT ipso_actuation_write(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count, UINT flags)
{
IPSO_ACTUATION_INSTANCE *act = ((IPSO_ACTUATION_INSTANCE *) instance_ptr);
UINT ret;
NX_LWM2M_BOOL onoff;
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_ONOFF:

            /* assign on/off boolean value */
            ret = nx_lwm2m_client_resource_boolean_get(&resource[i], &onoff);
            if (ret != NX_SUCCESS)
            {
                /* invalid value type */
                return(ret);
            }
            if (onoff != act->onoff)
            {
                act->onoff = onoff;

                printf("Set actuation switch %s\n", onoff ? "On" : "Off");
            }
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}

/* Define the operation callback function of Actuation Object */
UINT ipso_actuation_operation(UINT operation, NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT *resource_count, VOID *args_ptr, UINT args_length)
{
UINT write_op;

    switch (operation)
    {
    case NX_LWM2M_CLIENT_OBJECT_READ:

        /* Call read function */
        return ipso_actuation_read(object_ptr, object_instance_ptr, resource, *resource_count);
    case NX_LWM2M_CLIENT_OBJECT_DISCOVER:

        /* Call discover function */
        return ipso_actuation_discover(object_ptr, object_instance_ptr, resource, resource_count);
    case NX_LWM2M_CLIENT_OBJECT_WRITE:

        /* Get the type of write operation */
        write_op = *(UINT *)args_ptr;

        /* Call write function */
        return ipso_actuation_write(object_ptr, object_instance_ptr, resource, *resource_count, write_op);
    default:

        /* Unsupported operation */
        return(NX_LWM2M_CLIENT_NOT_SUPPORTED);
    }
}


/* NetX data.  */
NX_IP                   ip_0;
NX_PACKET_POOL          pool_0;

/* LWM2M Client data.  */
NX_LWM2M_CLIENT         client;
ULONG                   client_stack[4096 / sizeof(ULONG)];
NX_LWM2M_CLIENT_SESSION session;

/* Objects and instances.  */
NX_LWM2M_CLIENT_OBJECT      temperature_object;
NX_LWM2M_CLIENT_OBJECT      actuation_object;
IPSO_TEMPERATURE_INSTANCE   temperature_instance;
IPSO_ACTUATION_INSTANCE     actuation_instance;

/* Define the session state callback */
void session_callback(NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state)
{
    printf("LWM2M Callback: -> %d\n", state);

    switch (state)
    {

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING:

        printf("Start client initiated bootstrap\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED:

        printf("Got message from boostrap server\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED:

         /* Bootstrap session done, we can register to the LWM2M Server */
        printf( "Boostrap finished.\n");
#ifdef BOOTSTRAP
        tx_semaphore_put(&semaphore_bootstarp_finish);
#endif
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR:

        /* Failed to Bootstrap the LWM2M Client. */
        printf( "Failed to boostrap device, error=%02x\n", nx_lwm2m_client_session_error_get(session_ptr));
        break;

    case NX_LWM2M_CLIENT_SESSION_REGISTERED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device registered.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_DISABLED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device disabled.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_DEREGISTERED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device deregistered.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_ERROR:

        /* Failed to register to the LWM2M Client. */
        printf( "Failed to register device, error=%02x\n", nx_lwm2m_client_session_error_get(session_ptr));
        break;
    }
}


/* Application main thread */
void application_thread(ULONG info)
{

UINT status;
NX_LWM2M_ID server_id = 0;
NXD_ADDRESS server_addr;
CHAR *server_uri = NX_NULL;
UINT server_uri_len = 0;
UCHAR security_mode = 0;
   
    /* Create the LWM2M client */
    status = nx_lwm2m_client_create(&client, &ip_0, &pool_0, "nxlwm2mclient", sizeof("nxlwm2mclient") - 1, NX_NULL, 0, NX_LWM2M_CLIENT_BINDING_U, client_stack, sizeof(client_stack), 4);
    if (status)
    {
        return;
    }

    /* Define our custom objects: */
    /* Add Temperature Object */
    status = nx_lwm2m_client_object_add(&client, &temperature_object, IPSO_TEMPERATURE_OBJECT_ID, ipso_temperature_operation);
    if (status)
    {
        return;
    }

    /* Define a single instance */
    temperature_instance.temperature = 22.5f;
    temperature_instance.min_temperature = temperature_instance.temperature;
    temperature_instance.max_temperature = temperature_instance.temperature;
    status = nx_lwm2m_client_object_instance_add(&temperature_object, &temperature_instance.object_instance, NX_NULL);
    if (status)
    {
        return;
    }

    /* Add Actuation Object */
    status = nx_lwm2m_client_object_add(&client, &actuation_object, IPSO_ACTUATION_OBJECT_ID, ipso_actuation_operation);
    if (status)
    {
        return;
    }

    /* Define a single instance */
    actuation_instance.onoff = NX_FALSE;
    status = nx_lwm2m_client_object_instance_add(&actuation_object, &actuation_instance.object_instance, NX_NULL);
    if (status)
    {
        return;
    }

    /* Create a session */
    status = nx_lwm2m_client_session_create(&session, &client, session_callback);
    if (status)
    {
        return;
}

    /* Set bootstrap server address.  */
    server_addr.nxd_ip_version = NX_IP_VERSION_V4;
    server_addr.nxd_ip_address.v4 = IP_ADDRESS(23, 97, 187, 154);

    printf("Start boostraping\r\n");
    status = nx_lwm2m_client_session_bootstrap(&session, 0, &server_addr, 5783);
    if (status)
    {
        return;
    }

    status = nx_lwm2m_client_session_register_info_get(&session, NX_LWM2M_CLIENT_RESERVED_ID, &server_id, &server_uri, &server_uri_len, &security_mode, NX_NULL, NX_NULL, NX_NULL, NX_NULL, NX_NULL, NX_NULL);
    if (status || (security_mode != NX_LWM2M_CLIENT_SECURITY_MODE_NOSEC))
    {
        return;
    }

printf("Register to LWM2M server\r\n");
status = nx_lwm2m_client_session_register(&session, server_id, &server_addr, 5683);

    if (status)
    {
        return;
    }

    /* Application main loop */
    while (1)
    {

        /* application code... */
        tx_thread_sleep(NX_IP_PERIODIC_RATE);
    }

    /* Terminate the LWM2M Client */
    nx_lwm2m_client_delete(&client);
}

```