---
title: Глава 2. Установка и использование ОСРВ Azure NetX LWM2M
description: В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента ОСРВ Azure NetX LWM2M.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8c13d3b092d3a5b59bd0369f6ffc162509d02590
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815187"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-lwm2m"></a><span data-ttu-id="7c5fd-103">Глава 2. Установка и использование ОСРВ Azure NetX LWM2M</span><span class="sxs-lookup"><span data-stu-id="7c5fd-103">Chapter 2 - Installation and use of Azure RTOS NetX LWM2M</span></span>

<span data-ttu-id="7c5fd-104">В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента ОСРВ Azure NetX LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX LWM2M component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="7c5fd-105">Распространение продукта</span><span class="sxs-lookup"><span data-stu-id="7c5fd-105">Product Distribution</span></span>

<span data-ttu-id="7c5fd-106">Пакет NetX LWM2M доступен по адресу [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span><span class="sxs-lookup"><span data-stu-id="7c5fd-106">NetX LWM2M is available at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span> <span data-ttu-id="7c5fd-107">Пакет содержит три файла исходного кода, один включаемый файл и PDF-файл, содержащий этот документ:</span><span class="sxs-lookup"><span data-stu-id="7c5fd-107">The package includes three source files, one include files, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="7c5fd-108">**nx_lwm2m_client.h**: файл заголовка для клиента NetX LWM2M;</span><span class="sxs-lookup"><span data-stu-id="7c5fd-108">**nx_lwm2m_client.h**: Header file for the NetX LWM2M Client</span></span>

- <span data-ttu-id="7c5fd-109">**nx_lwm2m_\*. c/h**: файлы исходного кода C/H для NetX LWM2M;</span><span class="sxs-lookup"><span data-stu-id="7c5fd-109">**nx_lwm2m_\*.c/h**: C/H Source files for NetX LWM2M</span></span>

- <span data-ttu-id="7c5fd-110">**demo_netx_lwm2m_client.c**: демонстрационный файл исходного кода C клиента NetX LWM2M;</span><span class="sxs-lookup"><span data-stu-id="7c5fd-110">**demo_netx_lwm2m_client.c**: C Source file for NetX LWM2M Client Demo</span></span>

- <span data-ttu-id="7c5fd-111">**NetX_LWM2M_User_Guide.pdf**: PDF-файл с описанием продукта NetX LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-111">**NetX_LWM2M_User_Guide.pdf**: PDF description of NetX LWM2M product</span></span>

## <a name="netx-lwm2m-installation"></a><span data-ttu-id="7c5fd-112">Установка протокола NetX LWM2M</span><span class="sxs-lookup"><span data-stu-id="7c5fd-112">NetX LWM2M Installation</span></span>

<span data-ttu-id="7c5fd-113">Чтобы использовать NetX LWM2M, следует скопировать упомянутый выше дистрибутив целиком в тот же каталог, где установлен экземпляр NetX.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-113">In order to use NetX LWM2M, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="7c5fd-114">Например, если экземпляр NetX установлен в каталог *\\threadx\\arm7\\green*, то файлы *nx_lwm2m&#42;.&#42;* необходимо скопировать в этот каталог.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-114">For example, if NetX is installed in the directory "*\\threadx\\arm7\\green*" then the *nx_lwm2m&#42;.&#42;* files should be copied into this directory.</span></span>

## <a name="using-netx-lwm2m"></a><span data-ttu-id="7c5fd-115">Использование протокола NetX LWM2M</span><span class="sxs-lookup"><span data-stu-id="7c5fd-115">Using NetX LWM2M</span></span>

<span data-ttu-id="7c5fd-116">Использовать протокол NetX LWM2M просто.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-116">Using NetX LWM2M is easy.</span></span> <span data-ttu-id="7c5fd-117">В код приложения следует добавить *nx_lwm2m_client.h* после *tx_api.h* и *nx_api.h*, чтобы использовать ThreadX и NetX соответственно.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-117">Basically, the application code must include *nx_lwm2m_client.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX.</span></span> <span data-ttu-id="7c5fd-118">После включения файла *nx_lwm2m_client.h* код приложения может выполнять вызовы функций NetX LWM2M, описанных далее в этом руководстве.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-118">Once *nx_lwm2m_client.h* is included, the application code is then able to make the NetX LWM2M function calls specified later in this guide.</span></span> <span data-ttu-id="7c5fd-119">Приложение также должно импортировать файлы *nx_lwm2m&#42;.&#42;* в библиотеку NetX.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-119">The application must also import the *nx_lwm2m&#42;.&#42;* files into the NetX library.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="7c5fd-120">Параметры конфигурации</span><span class="sxs-lookup"><span data-stu-id="7c5fd-120">Configuration Options</span></span>

<span data-ttu-id="7c5fd-121">При сборке библиотеки клиента LWM2M и приложения, использующего клиент LWM2M, можно применить несколько параметров конфигурации.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-121">There are several configuration options when building the LWM2M Client library and the application using the LWM2M Client.</span></span> <span data-ttu-id="7c5fd-122">Параметры конфигурации можно определить в исходном коде приложения или в командной строке, если не указано иное.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-122">The configuration options can be defined in the application source, on the command line, unless otherwise specified.</span></span>

### <a name="nx_lwm2m_client_disable_error_checking"></a><span data-ttu-id="7c5fd-123">NX_LWM2M_CLIENT_DISABLE_ERROR_CHECKING</span><span class="sxs-lookup"><span data-stu-id="7c5fd-123">NX_LWM2M_CLIENT_DISABLE_ERROR_CHECKING</span></span>

<span data-ttu-id="7c5fd-124">Если этот параметр определен, то он отключает базовый API проверки на ошибки клиента LWM2M и повышает производительность.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-124">Defined, removes the basic LWM2M Client error checking API and improves performance.</span></span> <span data-ttu-id="7c5fd-125">Коды возврата API, которые не затрагиваются при отключении проверки на ошибки, выделены полужирным шрифтом в определении API.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-125">API return codes not affected by disabling error checking are listed in bold typeface in the API definition.</span></span>

### <a name="nx_lwm2m_client_disable_float"></a><span data-ttu-id="7c5fd-126">NX_LWM2M_CLIENT_DISABLE_FLOAT</span><span class="sxs-lookup"><span data-stu-id="7c5fd-126">NX_LWM2M_CLIENT_DISABLE_FLOAT</span></span>

<span data-ttu-id="7c5fd-127">Если этот параметр определен, то он отключает поддержку чисел с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-127">Defined, removes the support of floating point numbers values.</span></span> <span data-ttu-id="7c5fd-128">В этом случае клиент LWM2M не сможет поддерживать ресурсы с типом данных с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-128">When disabled the LWM2M Client cannot support Resources with Float data type.</span></span>

### <a name="nx_lwm2m_client_disable_float64"></a><span data-ttu-id="7c5fd-129">NX_LWM2M_CLIENT_DISABLE_FLOAT64</span><span class="sxs-lookup"><span data-stu-id="7c5fd-129">NX_LWM2M_CLIENT_DISABLE_FLOAT64</span></span>

<span data-ttu-id="7c5fd-130">Если этот параметр определен, то он отключает поддержку 64-разрядных чисел с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-130">Defined, removes the support of 64-bit floating point numbers values.</span></span> <span data-ttu-id="7c5fd-131">Клиент LWM2M по-прежнему сможет принимать сообщения TLV, содержащие 64-разрядные числа с плавающей запятой, но для обработки эти значения будут преобразовываться в 32-разрядные числа с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-131">The LWM2M Client can still receive TLV messages containing 64-bit floating numbers, but the values are converted to 32-bit floating point for processing.</span></span>

### <a name="nx_lwm2m_client_priority"></a><span data-ttu-id="7c5fd-132">NX_LWM2M_CLIENT_PRIORITY</span><span class="sxs-lookup"><span data-stu-id="7c5fd-132">NX_LWM2M_CLIENT_PRIORITY</span></span>

<span data-ttu-id="7c5fd-133">Указывает приоритет потока клиента LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-133">Specifies the priority of the LWM2M Client thread.</span></span> <span data-ttu-id="7c5fd-134">По умолчанию указано значение 16 для задания приоритета 16.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-134">By default, this value is defined as 16 to specify priority 16.</span></span>

### <a name="nx_lwm2m_client_max_device_errors"></a><span data-ttu-id="7c5fd-135">NX_LWM2M_CLIENT_MAX_DEVICE_ERRORS</span><span class="sxs-lookup"><span data-stu-id="7c5fd-135">NX_LWM2M_CLIENT_MAX_DEVICE_ERRORS</span></span>

<span data-ttu-id="7c5fd-136">Указывает максимальное количество кодов ошибок, хранящихся в объекте устройства.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-136">Specifies the maximum number of error codes stored by the Device Object.</span></span> <span data-ttu-id="7c5fd-137">Значение по умолчанию: 8.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-137">The default value is 8.</span></span>

### <a name="nx_lwm2m_client_max_security_instances"></a><span data-ttu-id="7c5fd-138">NX_LWM2M_CLIENT_MAX_SECURITY_INSTANCES</span><span class="sxs-lookup"><span data-stu-id="7c5fd-138">NX_LWM2M_CLIENT_MAX_SECURITY_INSTANCES</span></span>

<span data-ttu-id="7c5fd-139">Указывает максимальное число экземпляров объекта безопасности.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-139">Specifies the maximum number of Security Object Instances.</span></span> <span data-ttu-id="7c5fd-140">По умолчанию имеет значение 2, чтобы поддерживать сервер начальной загрузки и стандартный сервер.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-140">The default value is 2 for supporting a Bootstrap Server and a standard Server.</span></span>

### <a name="nx_lwm2m_client_max_server_instances"></a><span data-ttu-id="7c5fd-141">NX_LWM2M_CLIENT_MAX_SERVER_INSTANCES</span><span class="sxs-lookup"><span data-stu-id="7c5fd-141">NX_LWM2M_CLIENT_MAX_SERVER_INSTANCES</span></span>

<span data-ttu-id="7c5fd-142">Указывает максимальное число экземпляров объекта сервера.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-142">Specifies the maximum number of Server Object Instances.</span></span> <span data-ttu-id="7c5fd-143">По умолчанию имеет значение 1, чтобы поддерживать один стандартный сервер.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-143">The default value is 1 for supporting a single standard Server.</span></span>

### <a name="nx_lwm2m_client_max_server_uri"></a><span data-ttu-id="7c5fd-144">NX_LWM2M_CLIENT_MAX_SERVER_URI</span><span class="sxs-lookup"><span data-stu-id="7c5fd-144">NX_LWM2M_CLIENT_MAX_SERVER_URI</span></span>

<span data-ttu-id="7c5fd-145">Указывает максимальную длину универсального кода ресурса (URI) сервера, включая завершающий нулевой символ.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-145">Specifies the maximum length of a server URI, including terminating nil character.</span></span> <span data-ttu-id="7c5fd-146">Значение по умолчанию — 128.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-146">The default value is 128.</span></span>

### <a name="nx_lwm2m_client_max_access_control_instances"></a><span data-ttu-id="7c5fd-147">NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_INSTANCES</span><span class="sxs-lookup"><span data-stu-id="7c5fd-147">NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_INSTANCES</span></span>

<span data-ttu-id="7c5fd-148">Указывает максимальное число экземпляров службы контроля доступа.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-148">Specifies the maximum number of Access Control Instances.</span></span> <span data-ttu-id="7c5fd-149">По умолчанию имеет значение 0. При этом контроль доступа отключен.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-149">The default value is 0, which disables access control.</span></span> <span data-ttu-id="7c5fd-150">Если приложение поддерживает несколько серверов LWM2M, максимальное число экземпляров управления доступом должно совпадать с максимальным числом экземпляров объектов, которые будет поддерживать клиент LWM2M, так как для каждого экземпляра объекта (за исключением экземпляров объекта безопасности) должен быть создан один экземпляр управления доступом.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-150">If the application supports more than one LWM2M Server, the maximum number of Access Control Instances must be set to the maximum number of Object Instances that the LWM2M Client will support, as one Access Control Instance must be created for each Object Instance (except for the Security Object Instances).</span></span>

### <a name="nx_lwm2m_client_max_access_control_acls"></a><span data-ttu-id="7c5fd-151">NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_ACLS</span><span class="sxs-lookup"><span data-stu-id="7c5fd-151">NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_ACLS</span></span>

<span data-ttu-id="7c5fd-152">Указывает максимальное количество ресурсов ACL на экземпляр службы контроля доступа.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-152">Specifies the maximum number of ACL resources per Access Control Instance.</span></span> <span data-ttu-id="7c5fd-153">Значение по умолчанию — 4.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-153">The default value is 4.</span></span>

### <a name="nx_lwm2m_client_max_notifications"></a><span data-ttu-id="7c5fd-154">NX_LWM2M_CLIENT_MAX_NOTIFICATIONS</span><span class="sxs-lookup"><span data-stu-id="7c5fd-154">NX_LWM2M_CLIENT_MAX_NOTIFICATIONS</span></span>

<span data-ttu-id="7c5fd-155">Указывает максимальное количество уведомлений, которые будет поддерживать клиент LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-155">Specifies the maximum number of notifications that the LWM2M Client will support.</span></span> <span data-ttu-id="7c5fd-156">Сервер LWM2M может устанавливать уведомления для объектов, экземпляров объектов и ресурсов.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-156">A LWM2M Server can set notifications on Objects, Object Instances, and Resources.</span></span> <span data-ttu-id="7c5fd-157">Значение по умолчанию: 8.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-157">The default value is 8.</span></span>

### <a name="nx_lwm2m_client_max_resources"></a><span data-ttu-id="7c5fd-158">NX_LWM2M_CLIENT_MAX_RESOURCES</span><span class="sxs-lookup"><span data-stu-id="7c5fd-158">NX_LWM2M_CLIENT_MAX_RESOURCES</span></span>

<span data-ttu-id="7c5fd-159">Указывает максимальное количество ресурсов на объект.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-159">Specifies the maximum number of Resources per Object.</span></span> <span data-ttu-id="7c5fd-160">Значение по умолчанию: 32.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-160">The default value is 32.</span></span>

### <a name="nx_lwm2m_client_bootstrap_idle_timer"></a><span data-ttu-id="7c5fd-161">NX_LWM2M_CLIENT_BOOTSTRAP_IDLE_TIMER</span><span class="sxs-lookup"><span data-stu-id="7c5fd-161">NX_LWM2M_CLIENT_BOOTSTRAP_IDLE_TIMER</span></span>

<span data-ttu-id="7c5fd-162">Указывает максимальное время ожидания запросов сервера начальной загрузки при запуске сеанса начальной загрузки перед прерыванием сеанса.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-162">Specifies the maximum time to wait for bootstrap server requests when the bootstrap session is initiated before aborting the session.</span></span> <span data-ttu-id="7c5fd-163">Значение по умолчанию — 60 секунд.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-163">The default value is 60 seconds.</span></span>

### <a name="nx_lwm2m_client_dtls_start_timeout"></a><span data-ttu-id="7c5fd-164">NX_LWM2M_CLIENT_DTLS_START_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7c5fd-164">NX_LWM2M_CLIENT_DTLS_START_TIMEOUT</span></span>

<span data-ttu-id="7c5fd-165">Указывает максимальное время ожидания для завершения подтверждения DTLS.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-165">Specifies the maximum time to wait for DTLS handshake completion.</span></span> <span data-ttu-id="7c5fd-166">Значение по умолчанию - 30 секунды.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-166">The default value is 30 seconds.</span></span>

### <a name="nx_lwm2m_client_dtls_end_timeout"></a><span data-ttu-id="7c5fd-167">NX_LWM2M_CLIENT_DTLS_END_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7c5fd-167">NX_LWM2M_CLIENT_DTLS_END_TIMEOUT</span></span>

<span data-ttu-id="7c5fd-168">Указывает максимальное время ожидания для завершения работы DTLS.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-168">Specifies the maximum time to wait for DTLS shutdown completion.</span></span> <span data-ttu-id="7c5fd-169">Значение по умолчанию — 5 секунд.</span><span class="sxs-lookup"><span data-stu-id="7c5fd-169">The default value is 5 seconds.</span></span>
