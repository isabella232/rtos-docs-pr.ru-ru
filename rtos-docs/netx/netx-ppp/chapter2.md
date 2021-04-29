---
title: Глава 2. Установка и использование компонента Point-to-Point Protocol (PPP) NetX для ОСРВ Azure
description: В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента Point-to-Point Protocol (PPP) NetX для ОСРВ Azure.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 40f09da31f5541208c3b2cc0eeb54850b3d71f7c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815156"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-point-to-point-protocol-ppp"></a><span data-ttu-id="5c707-103">Глава 2. Установка и использование компонента Point-to-Point Protocol (PPP) NetX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="5c707-103">Chapter 2 - Installation and use of Azure RTOS NetX Point-to-Point Protocol (PPP)</span></span>

<span data-ttu-id="5c707-104">В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента Point-to-Point Protocol (PPP) NetX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="5c707-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Point-to-Point Protocol (PPP) component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="5c707-105">Распространение продукта</span><span class="sxs-lookup"><span data-stu-id="5c707-105">Product Distribution</span></span>

<span data-ttu-id="5c707-106">Пакет Point-to-Point Protocol (PPP) NetX для ОСРВ Azure доступен по адресу <https://github.com/azure-rtos/netx>.</span><span class="sxs-lookup"><span data-stu-id="5c707-106">The Azure RTOS NetX Point-to-Point Protocol (PPP) package is available at <https://github.com/azure-rtos/netx>.</span></span> <span data-ttu-id="5c707-107">В состав пакета входят следующие файлы.</span><span class="sxs-lookup"><span data-stu-id="5c707-107">The package includes the following files:</span></span>

- <span data-ttu-id="5c707-108">**nx_ppp.h**: файл заголовка для PPP для NetX</span><span class="sxs-lookup"><span data-stu-id="5c707-108">**nx_ppp.h**: Header file for PPP for NetX</span></span>
- <span data-ttu-id="5c707-109">**nx_ppp.c**: исходный файл для PPP для NetX</span><span class="sxs-lookup"><span data-stu-id="5c707-109">**nx_ppp.c**: C Source file for PPP for NetX</span></span>
- <span data-ttu-id="5c707-110">**nx_ppp.pdf**: описание PPP для NetX в формате PDF</span><span class="sxs-lookup"><span data-stu-id="5c707-110">**nx_ppp.pdf**: PDF description of PPP for NetX</span></span>
- <span data-ttu-id="5c707-111">**demo_netx_ppp.c**: демонстрация PPP для NetX</span><span class="sxs-lookup"><span data-stu-id="5c707-111">**demo_netx_ppp.c**: NetX PPP demonstration</span></span>

## <a name="ppp-installation"></a><span data-ttu-id="5c707-112">Установка PPP</span><span class="sxs-lookup"><span data-stu-id="5c707-112">PPP Installation</span></span>

<span data-ttu-id="5c707-113">Чтобы использовать PPP для NetX, весь дистрибутив, упомянутый ранее, должен быть скопирован в тот же каталог, где установлен NetX.</span><span class="sxs-lookup"><span data-stu-id="5c707-113">In order to use PPP for NetX, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="5c707-114">Например, если NetX установлен в каталоге *\threadx\arm7\green*, то файлы *nx_ppp.h* и *nx_ppp.c* необходимо скопировать в этот каталог.</span><span class="sxs-lookup"><span data-stu-id="5c707-114">For example, if NetX is installed in the directory “*\threadx\arm7\green*” then the *nx_ppp.h* and *nx_ppp.c* files should be copied into this directory.</span></span>

## <a name="using-ppp"></a><span data-ttu-id="5c707-115">Использование PPP</span><span class="sxs-lookup"><span data-stu-id="5c707-115">Using PPP</span></span>

<span data-ttu-id="5c707-116">Использовать PPP для NetX просто.</span><span class="sxs-lookup"><span data-stu-id="5c707-116">Using PPP for NetX is easy.</span></span> <span data-ttu-id="5c707-117">В код приложения следует добавить *nx_ppp.h* после *tx_api.h* и *nx_api.h*, чтобы использовать ThreadX и NetX соответственно.</span><span class="sxs-lookup"><span data-stu-id="5c707-117">Basically, the application code must include *nx_ppp.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX, respectively.</span></span> <span data-ttu-id="5c707-118">После добавления файла *nx_ppp.h* код приложения может выполнять вызовы функций PPP, указанные далее в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="5c707-118">Once *nx_ppp.h* is included, the application code is then able to make the PPP function calls specified later in this guide.</span></span> <span data-ttu-id="5c707-119">В приложение также следует включить файл *nx_ppp.c* в процессе сборки.</span><span class="sxs-lookup"><span data-stu-id="5c707-119">The application must also include *nx_ppp.c* in the build process.</span></span> <span data-ttu-id="5c707-120">Этот файл должен быть скомпилирован так же, как и другие файлы приложения, а его объектная форма должна быть связана с файлами приложения.</span><span class="sxs-lookup"><span data-stu-id="5c707-120">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="5c707-121">Это все, что необходимо для использования PPP NetX.</span><span class="sxs-lookup"><span data-stu-id="5c707-121">This is all that is required to use NetX PPP.</span></span>

## <a name="using-modems"></a><span data-ttu-id="5c707-122">Использование модемов</span><span class="sxs-lookup"><span data-stu-id="5c707-122">Using Modems</span></span>

<span data-ttu-id="5c707-123">Если для подключения к Интернету требуется модем, для использования продукта PPP необходимо учитывать некоторые особенности.</span><span class="sxs-lookup"><span data-stu-id="5c707-123">If a modem is required for connection to the internet, some special considerations are required in order to use the NetX PPP product.</span></span> <span data-ttu-id="5c707-124">По сути, использование модема вводит дополнительную логику инициализации и логику потери связи.</span><span class="sxs-lookup"><span data-stu-id="5c707-124">Basically, using a modem introduces additional initialization logic and logic for loss of communication.</span></span> <span data-ttu-id="5c707-125">Кроме того, большая часть дополнительной логики модема реализуется вне контекста PPP NetX.</span><span class="sxs-lookup"><span data-stu-id="5c707-125">In addition, most of the additional modem logic is done outside the context of NetX PPP.</span></span> <span data-ttu-id="5c707-126">Основной процесс использования PPP NetX с модемом выглядит примерно так, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="5c707-126">The basic flow of using the NetX PPP with a modem goes something like this:</span></span>

1. <span data-ttu-id="5c707-127">Инициализация модема</span><span class="sxs-lookup"><span data-stu-id="5c707-127">Initialize Modem</span></span>

1. <span data-ttu-id="5c707-128">Установка связи с поставщиком услуг Интернета (ISP)</span><span class="sxs-lookup"><span data-stu-id="5c707-128">Dial Internet Service Provider (ISP)</span></span>

1. <span data-ttu-id="5c707-129">Ожидание подключения</span><span class="sxs-lookup"><span data-stu-id="5c707-129">Wait for Connection</span></span>

1. <span data-ttu-id="5c707-130">Ожидание запроса на ввод идентификатора пользователя</span><span class="sxs-lookup"><span data-stu-id="5c707-130">Wait for UserID Prompt</span></span>

1. <span data-ttu-id="5c707-131">Запуск PPP NetX [PPP работает]</span><span class="sxs-lookup"><span data-stu-id="5c707-131">Start NetX PPP [PPP in operation]</span></span>

1. <span data-ttu-id="5c707-132">Потеря связи</span><span class="sxs-lookup"><span data-stu-id="5c707-132">Loss of Communication</span></span>

1. <span data-ttu-id="5c707-133">Остановка PPP NetX (или перезапуск с помощью nx_ppp_restart)</span><span class="sxs-lookup"><span data-stu-id="5c707-133">Stop NetX PPP (or restart via nx_ppp_restart)</span></span>

### <a name="initialize-modem"></a><span data-ttu-id="5c707-134">Инициализация модема</span><span class="sxs-lookup"><span data-stu-id="5c707-134">Initialize Modem</span></span>

<span data-ttu-id="5c707-135">Используя низкоуровневую подпрограмму последовательного вывода приложения, модем инициализируется с помощью ряда команд с ASCII-символами (дополнительные сведения см. в документации по модему).</span><span class="sxs-lookup"><span data-stu-id="5c707-135">Using the application’s low-level serial output routine, the modem is initialized via a series of ASCII character commands (see modem’s documentation for more details).</span></span>

### <a name="dial-internet-service-provider"></a><span data-ttu-id="5c707-136">Установка связи с поставщиком услуг Интернета</span><span class="sxs-lookup"><span data-stu-id="5c707-136">Dial Internet Service Provider</span></span>

<span data-ttu-id="5c707-137">Низкоуровневая подпрограмма последовательного вывода указывает модему установить связь с поставщиком услуг Интернета.</span><span class="sxs-lookup"><span data-stu-id="5c707-137">Using the application’s low-level serial output routine, the modem is instructed to dial the ISP.</span></span> <span data-ttu-id="5c707-138">Например, ниже приведена стандартная строка ASCII для установки связи с поставщиком услуг Интернета по номеру телефона 123-4567.</span><span class="sxs-lookup"><span data-stu-id="5c707-138">For example, the following is typical of an ASCII string used to dial an ISP at the number 123-4567:</span></span>

<span data-ttu-id="5c707-139">"ATDT123456\r"</span><span class="sxs-lookup"><span data-stu-id="5c707-139">“ATDT123456\r”</span></span>

### <a name="wait-for-connection"></a><span data-ttu-id="5c707-140">Ожидание подключения</span><span class="sxs-lookup"><span data-stu-id="5c707-140">Wait for Connection</span></span>

<span data-ttu-id="5c707-141">Теперь приложение ожидает от модема сообщения о том, что подключение установлено.</span><span class="sxs-lookup"><span data-stu-id="5c707-141">At this point, the application waits to receive indication from the modem that a connection has been established.</span></span> <span data-ttu-id="5c707-142">Чтобы проверить состояние, нужно взглянуть на символы, выведенные низкоуровневой подпрограммой последовательного вывода приложения.</span><span class="sxs-lookup"><span data-stu-id="5c707-142">This is accomplished by looking for characters from the application’s low-level serial input routine.</span></span> <span data-ttu-id="5c707-143">Как правило, модемы возвращают строку ASCII "CONNECT", если подключение установлено.</span><span class="sxs-lookup"><span data-stu-id="5c707-143">Typically, modems return an ASCII string “CONNECT” when a connection has been established.</span></span>

### <a name="wait-for-user-id-prompt"></a><span data-ttu-id="5c707-144">Ожидание запроса на ввод идентификатора пользователя</span><span class="sxs-lookup"><span data-stu-id="5c707-144">Wait for User ID Prompt</span></span>

<span data-ttu-id="5c707-145">После установки подключения приложение ожидает начальный запрос имени входа от поставщика услуг Интернета.</span><span class="sxs-lookup"><span data-stu-id="5c707-145">Once the connection has been established, the application must now wait for an initial login request from the ISP.</span></span> <span data-ttu-id="5c707-146">Обычно он имеет вид строки ASCII, например "Login?".</span><span class="sxs-lookup"><span data-stu-id="5c707-146">This typically takes the form of an ASCII string like “Login?”</span></span>

### <a name="start-netx-ppp"></a><span data-ttu-id="5c707-147">Запуск PPP NetX</span><span class="sxs-lookup"><span data-stu-id="5c707-147">Start NetX PPP</span></span>

<span data-ttu-id="5c707-148">На этом этапе можно запустить PPP NetX.</span><span class="sxs-lookup"><span data-stu-id="5c707-148">At this point, the NetX PPP can be started.</span></span> <span data-ttu-id="5c707-149">Для этого вызывается служба *nx_ppp_create*, а затем — служба *nx_ip_create*.</span><span class="sxs-lookup"><span data-stu-id="5c707-149">This is accomplished by calling the *nx_ppp_create* service followed by the *nx_ip_create* service.</span></span> <span data-ttu-id="5c707-150">Кроме того, могут потребоваться дополнительные службы для включения PAP и настройки IP-адресов PPP.</span><span class="sxs-lookup"><span data-stu-id="5c707-150">Additional services to enable PAP and to setup the PPP IP addresses might also be required.</span></span> <span data-ttu-id="5c707-151">Дополнительные сведения можно найти в следующих разделах этого руководства.</span><span class="sxs-lookup"><span data-stu-id="5c707-151">Please review the following sections of this guide for more information.</span></span>

### <a name="loss-of-communication"></a><span data-ttu-id="5c707-152">Потеря связи</span><span class="sxs-lookup"><span data-stu-id="5c707-152">Loss of Communication</span></span>

<span data-ttu-id="5c707-153">После запуска PPP все сведения, не относящиеся к PPP, передаются в подпрограмму обработки недопустимых пакетов, указанную приложением в службе *nx_ppp_create*.</span><span class="sxs-lookup"><span data-stu-id="5c707-153">Once PPP is started, any non-PPP information is passed to the “invalid packet handling” routine the application specified to the *nx_ppp_create* service.</span></span> <span data-ttu-id="5c707-154">Как правило, при потере связи с поставщиком услуг Интернета модемы отправляют строку ASCII, такую как "NO CARRIER".</span><span class="sxs-lookup"><span data-stu-id="5c707-154">Typically, modems send an ASCII string such as “NO CARRIER” when communication is lost with the ISP.</span></span> <span data-ttu-id="5c707-155">Когда приложение получает пакет, не относящийся к PPP, с такой информацией, оно должно либо остановить экземпляр PPP NetX, либо перезапустить конечный автомат PPP с помощью API *nx_ppp_restart*.</span><span class="sxs-lookup"><span data-stu-id="5c707-155">When the application receives a non-PPP packet with such information, it should proceed to either stop the NetX PPP instance or to restart the PPP state machine via the *nx_ppp_restart* API.</span></span>

### <a name="stop-netx-ppp"></a><span data-ttu-id="5c707-156">Остановка PPP NetX</span><span class="sxs-lookup"><span data-stu-id="5c707-156">Stop NetX PPP</span></span>

<span data-ttu-id="5c707-157">Остановить PPP NetX довольно просто.</span><span class="sxs-lookup"><span data-stu-id="5c707-157">Stopping the NetX PPP is fairly straightforward.</span></span> <span data-ttu-id="5c707-158">По сути, все созданные сокеты должны быть освобождены и удалены.</span><span class="sxs-lookup"><span data-stu-id="5c707-158">Basically, all created sockets must be unbound and deleted.</span></span> <span data-ttu-id="5c707-159">Затем следует удалить экземпляр IP-адреса с помощью службы *nx_ip_delete*.</span><span class="sxs-lookup"><span data-stu-id="5c707-159">Next, delete the IP instance via the *nx_ip_delete* service.</span></span> <span data-ttu-id="5c707-160">После удаления экземпляра IP необходимо вызвать службу *nx_ppp_delete*, чтобы завершить процесс остановки PPP.</span><span class="sxs-lookup"><span data-stu-id="5c707-160">Once the IP instance is deleted, the *nx_ppp_delete* service should be called to finish the process of stopping PPP.</span></span> <span data-ttu-id="5c707-161">Теперь приложение может попытаться восстановить связь с поставщиком услуг Интернета.</span><span class="sxs-lookup"><span data-stu-id="5c707-161">At this point, the application is now able to attempt to reestablish communication with the ISP.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="5c707-162">Пример небольшой системы</span><span class="sxs-lookup"><span data-stu-id="5c707-162">Small Example System</span></span>

<span data-ttu-id="5c707-163">Пример, демонстрирующий, насколько просто использовать PPP NetX, приведен в блоке 1.1 ниже.</span><span class="sxs-lookup"><span data-stu-id="5c707-163">An example that illustrates how easy it is to use NetX PPP is described in Figure 1.1 that appears below.</span></span> <span data-ttu-id="5c707-164">В этом примере файл включения PPP *nx_ppp.h* находится на строке 3.</span><span class="sxs-lookup"><span data-stu-id="5c707-164">In this example, the PPP include file *nx_ppp.h* is brought in at line 3.</span></span> <span data-ttu-id="5c707-165">Затем PPP создается в *tx_application_define* в строке 56.</span><span class="sxs-lookup"><span data-stu-id="5c707-165">Next, PPP is created in *”tx_application_define*” at line 56.</span></span> <span data-ttu-id="5c707-166">Блок управления PPP *my_ppp* был определен ранее в качестве глобальной переменной в строке 9.</span><span class="sxs-lookup"><span data-stu-id="5c707-166">The PPP control block “*my_ppp*” was defined as a global variable at line 9 previously.</span></span> 

>[!NOTE]
><span data-ttu-id="5c707-167">PPP следует создать до создания экземпляра IP.</span><span class="sxs-lookup"><span data-stu-id="5c707-167">PPP should be created prior to creating the IP instance.</span></span> <span data-ttu-id="5c707-168">После успешного создания PPP и IP поток *my_thread* ожидает перехода канала PPP в активное состояние в строке 98.</span><span class="sxs-lookup"><span data-stu-id="5c707-168">After successful creation of PPP and IP, the thread “*my_thread*” waits for the PPP link to come alive at line 98.</span></span> <span data-ttu-id="5c707-169">В строке 104 и PPP, и NetX являются полностью работоспособными.</span><span class="sxs-lookup"><span data-stu-id="5c707-169">At line 104, both PPP and NetX are fully operational.</span></span>

<span data-ttu-id="5c707-170">Одним из элементов, не показанных в этом примере, является получение последовательного байта ISR.</span><span class="sxs-lookup"><span data-stu-id="5c707-170">The one item not shown in this example is the application’s serial byte receive ISR.</span></span> <span data-ttu-id="5c707-171">Необходимо вызвать *nx_ppp_byte_receive* с параметром *my_ppp* и байтом, полученным в качестве входных параметров.</span><span class="sxs-lookup"><span data-stu-id="5c707-171">It will need to call *nx_ppp_byte_receive* with “*my_ppp*” and the byte received as input parameters.</span></span>

```c
#include   "tx_api.h"
#include   "nx_api.h"
#include   "nx_ppp.h"

#define     DEMO_STACK_SIZE         4096
TX_THREAD               my_thread;
NX_PACKET_POOL          my_pool;
NX_IP                   my_ip;
NX_PPP                  my_ppp;

/* Define function prototypes. */

void    my_thread_entry(ULONG thread_input);
void    my_serial_driver_byte_output(UCHAR byte);
void    my_invalid_packet_handler(NX_PACKET *packet_ptr);
 
/* Define main entry point. */
intmain()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
 }


/* Define what the initial system looks like. */

void    tx_application_define(void *first_unused_memory)
{

CHAR    *pointer;
UINT    status;

/* Setup the working pointer. */
pointer =  (CHAR *) first_unused_memory;

/* Create “my_thread”. */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0,  
                  pointer, DEMO_STACK_SIZE, 
                  2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a packet pool. */
    status =  nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                                    1024, pointer, 64000);
    pointer = pointer + 64000;

    /* Check for pool creation error. */
    if (status)
        error_counter++;

    /* Create a PPP instance. */
    status = nx_ppp_create(&my_ppp, “My PPP”, &my_ip, pointer, 1024, 2, 
                           &my_pool, my_invalid_packet_handler, my_serial_driver_byte_output);
    pointer =  pointer + 1024;
    /* Check for PPP creation pool. */
    if (status)
        error_counter++;

    /* Create an IP instance with the PPP driver. */
    status = nx_ip_create(&my_ip,"My NetX IP Instance", 
                           IP_ADDRESS(216,2,3,1), 0xFFFFFF00, &my_pool, 
                           nx_ppp_driver, pointer, DEMO_STACK_SIZE, 1);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check for IP create errors. */
    if (status)
        error_counter++;

    /* Enable ICMP for my IP Instance. */
    status =  nx_icmp_enable(&my_ip);

    /* Check for ICMP enable errors. */
    if (status)
        error_counter++;

    /* Enable UDP. */
    status =  nx_udp_enable(&my_ip);
    if (status)
        error_counter++;
}

/* Define my thread. */
void    my_thread_entry(ULONG thread_input)
{

UINT        status;
ULONG       ip_status;
NX_PACKET   *my_packet;

/* Wait for the PPP link in my_ip to become enabled. */
    status =  nx_ip_status_check(&my_ip,NX_IP_LINK_ENABLED,&ip_status,3000);

    /* Check for IP status error. */
    if (status) 
        return;

    /* Link is fully up and operational. All NetX activities 
    are now available. */

}
```
## <a name="configuration-options"></a><span data-ttu-id="5c707-172">Параметры конфигурации</span><span class="sxs-lookup"><span data-stu-id="5c707-172">Configuration Options</span></span>

<span data-ttu-id="5c707-173">Существует ряд параметров конфигурации для использования PPP для NetX.</span><span class="sxs-lookup"><span data-stu-id="5c707-173">There are several configuration options for building PPP for NetX.</span></span> <span data-ttu-id="5c707-174">Их подробное описание приводится ниже.</span><span class="sxs-lookup"><span data-stu-id="5c707-174">The following list describes each in detail:</span></span>

- <span data-ttu-id="5c707-175">**NX_DISABLE_ERROR_CHECKING** — если определен, этот параметр удаляет базовую проверку ошибок PPP.</span><span class="sxs-lookup"><span data-stu-id="5c707-175">**NX_DISABLE_ERROR_CHECKING**: Defined, this option removes the basic PPP error checking.</span></span> <span data-ttu-id="5c707-176">Обычно он используется после отладки приложения.</span><span class="sxs-lookup"><span data-stu-id="5c707-176">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="5c707-177">**NX_PPP_PPPOE_ENABLE** — если определен, PPP может передавать пакеты через Ethernet.</span><span class="sxs-lookup"><span data-stu-id="5c707-177">**NX_PPP_PPPOE_ENABLE**: If defined, PPP can transmit packet over Ethernet</span></span>
- <span data-ttu-id="5c707-178">**NX_PPP_BASE_TIMEOUT** — определяет частоту периода (в тактах таймера) активации задачи потока PPP для проверки на наличие событий PPP.</span><span class="sxs-lookup"><span data-stu-id="5c707-178">**NX_PPP_BASE_TIMEOUT**: This defines the period rate (in timer ticks) that the PPP thread task is woken to check for PPP events.</span></span> <span data-ttu-id="5c707-179">Значение по умолчанию — 1\*NX_IP_PERIODIC_RATE (100 тактов).</span><span class="sxs-lookup"><span data-stu-id="5c707-179">The default value is 1\*NX_IP_PERIODIC_RATE (100 ticks).</span></span>
- <span data-ttu-id="5c707-180">**NX_PPP_DISABLE_INFO** — если определен, сбор внутренних данных PPP отключен.</span><span class="sxs-lookup"><span data-stu-id="5c707-180">**NX_PPP_DISABLE_INFO**: If defined, internal PPP information gathering is disabled.</span></span>
- <span data-ttu-id="5c707-181">**NX_PPP_DEBUG_LOG_ENABLE** — если определен, включен внутренний журнал отладки PPP.</span><span class="sxs-lookup"><span data-stu-id="5c707-181">**NX_PPP_DEBUG_LOG_ENABLE**: If defined, internal PPP debug log is enabled.</span></span>
- <span data-ttu-id="5c707-182">**NX_PPP_DEBUG_LOG_PRINT_ENABLE** — если определен, включен внутренний журнал отладки PPP для функции *printf* в *stdio*.</span><span class="sxs-lookup"><span data-stu-id="5c707-182">**NX_PPP_DEBUG_LOG_PRINT_ENABLE**:If defined, internal PPP debug log *printf* to *stdio* is enabled.</span></span> <span data-ttu-id="5c707-183">Этот параметр допустим, только если также включен журнал отладки.</span><span class="sxs-lookup"><span data-stu-id="5c707-183">This is only valid if the debug log is also enabled.</span></span>
- <span data-ttu-id="5c707-184">**NX_PPP_DEBUG_LOG_SIZE** — размер журнала отладки (число записей в журнале отладки).</span><span class="sxs-lookup"><span data-stu-id="5c707-184">**NX_PPP_DEBUG_LOG_SIZE**: Size of debug log (number of entries in the debug log).</span></span> <span data-ttu-id="5c707-185">При достижении последней записи запись отладки переносится к первой записи и перезаписывает все записанные ранее данные.</span><span class="sxs-lookup"><span data-stu-id="5c707-185">On reaching the last entry, the debug capture wraps to the first entry and overwrites any data previously captured.</span></span> <span data-ttu-id="5c707-186">Значение по умолчанию — 50.</span><span class="sxs-lookup"><span data-stu-id="5c707-186">The default value is 50.</span></span>
- <span data-ttu-id="5c707-187">**NX_PPP_DEBUG_FRAME_SIZE** — максимальный объем данных, захваченных из полезных данных полученного пакета и сохраненных в выходных данных отладки.</span><span class="sxs-lookup"><span data-stu-id="5c707-187">**NX_PPP_DEBUG_FRAME_SIZE**: Maximum amount of data captured from a received packet payload and saved to debug output.</span></span> <span data-ttu-id="5c707-188">Значение по умолчанию — 50.</span><span class="sxs-lookup"><span data-stu-id="5c707-188">The default value is 50.</span></span>
- <span data-ttu-id="5c707-189">**NX_PPP_DISABLE_CHAP** — если определен, удаляется внутренняя логика CHAP PPP, включая логику дайджеста MD5.</span><span class="sxs-lookup"><span data-stu-id="5c707-189">**NX_PPP_DISABLE_CHAP**: If defined, internal PPP CHAP logic is removed, including the MD5 digest logic.</span></span>
- <span data-ttu-id="5c707-190">**NX_PPP_DISABLE_PAP** — если определен, удаляется внутренняя логика PAP PPP.</span><span class="sxs-lookup"><span data-stu-id="5c707-190">**NX_PPP_DISABLE_PAP**: If defined, internal PPP PAP logic is removed.</span></span>
- <span data-ttu-id="5c707-191">**NX_PPP_DNS_OPTION_DISABLE** — если определен, параметр DNS в ответе IPCP отключен.</span><span class="sxs-lookup"><span data-stu-id="5c707-191">**NX_PPP_DNS_OPTION_DISABLE**: If defined, DNS Option is disabled in the IPCP response.</span></span>  <span data-ttu-id="5c707-192">По умолчанию этот параметр не определен (параметр DNS задан).</span><span class="sxs-lookup"><span data-stu-id="5c707-192">By default this option is not defined (DNS option is set).</span></span>
- <span data-ttu-id="5c707-193">**NX_PPP_DNS_ADDRESS_MAX_RETRIES** — указывает, сколько раз узел PPP будет запрашивать адрес DNS-сервера от однорангового узла в состоянии IPCP.</span><span class="sxs-lookup"><span data-stu-id="5c707-193">**NX_PPP_DNS_ADDRESS_MAX_RETRIES**: This specifies how many times the PPP host will request a DNS Server address from the peer in the IPCP state.</span></span> <span data-ttu-id="5c707-194">Этот параметр не работает, если определен параметр NX_PPP_DNS_OPTION_DISABLE.</span><span class="sxs-lookup"><span data-stu-id="5c707-194">This has no effect if NX_PPP_DNS_OPTION_DISABLE is defined.</span></span> <span data-ttu-id="5c707-195">Значение по умолчанию — 2.</span><span class="sxs-lookup"><span data-stu-id="5c707-195">The default value is 2.</span></span>
- <span data-ttu-id="5c707-196">**NX_PPP_HASHED_VALUE_SIZE** — указывает размер строк хэшированного значения, используемых при проверке подлинности CHAP.</span><span class="sxs-lookup"><span data-stu-id="5c707-196">**NX_PPP_HASHED_VALUE_SIZE**: Specifies the size of “hashed value” strings used in CHAP authentication.</span></span> <span data-ttu-id="5c707-197">Значение по умолчанию равно 16 байт, но может быть переопределено перед включением *nx_ppp.h*.</span><span class="sxs-lookup"><span data-stu-id="5c707-197">The default value is set to 16 bytes, but can be redefined prior to inclusion of *nx_ppp.h.*</span></span>
- <span data-ttu-id="5c707-198">**NX_PPP_MAX_LCP_PROTOCOL_RETRIES** — определяет максимальное число повторных попыток, если время ожидания PPP истекло до отправки другого сообщения запроса настройки LCP.</span><span class="sxs-lookup"><span data-stu-id="5c707-198">**NX_PPP_MAX_LCP_PROTOCOL_RETRIES**: This defines the max number of retries if the PPP times out before sending another LCP configure request message.</span></span> <span data-ttu-id="5c707-199">При достижении этого значения подтверждение PPP прерывается, а канал переходит в нерабочее состояние.</span><span class="sxs-lookup"><span data-stu-id="5c707-199">When this number is reached the PPP handshake is aborted and the link status is down.</span></span> <span data-ttu-id="5c707-200">Значение по умолчанию — 20.</span><span class="sxs-lookup"><span data-stu-id="5c707-200">The default value is 20.</span></span>
- <span data-ttu-id="5c707-201">**NX_PPP_MAX_PAP_PROTOCOL_RETRIES** — определяет максимальное число повторных попыток, если время ожидания PPP истекло до отправки другого сообщения запроса проверки подлинности PAP.</span><span class="sxs-lookup"><span data-stu-id="5c707-201">**NX_PPP_MAX_PAP_PROTOCOL_RETRIES**: This defines the max number of retries if the PPP times out before sending another PAP authentication request message.</span></span> <span data-ttu-id="5c707-202">При достижении этого значения подтверждение PPP прерывается, а канал переходит в нерабочее состояние.</span><span class="sxs-lookup"><span data-stu-id="5c707-202">When this number is reached the PPP handshake is aborted and the link status is down.</span></span> <span data-ttu-id="5c707-203">Значение по умолчанию — 20.</span><span class="sxs-lookup"><span data-stu-id="5c707-203">The default value is 20.</span></span>
- <span data-ttu-id="5c707-204">**NX_PPP_MAX_CHAP_PROTOCOL_RETRIES** — определяет максимальное число повторных попыток, если время ожидания PPP истекло до отправки другого сообщения запроса CHAP.</span><span class="sxs-lookup"><span data-stu-id="5c707-204">**NX_PPP_MAX_CHAP_PROTOCOL_RETRIES**: This defines the max number of retries if the PPP times out before sending another CHAP challenge message.</span></span> <span data-ttu-id="5c707-205">При достижении этого значения подтверждение PPP прерывается, а канал переходит в нерабочее состояние.</span><span class="sxs-lookup"><span data-stu-id="5c707-205">When this number is reached the PPP handshake is aborted and the link status is down.</span></span> <span data-ttu-id="5c707-206">Значение по умолчанию — 20.</span><span class="sxs-lookup"><span data-stu-id="5c707-206">The default value is 20.</span></span>
- <span data-ttu-id="5c707-207">**NX_PPP_MAX_IPCP_PROTOCOL_RETRIES** — определяет максимальное число повторных попыток, если время ожидания PPP истекло до отправки другого сообщения запроса настройки IPCP.</span><span class="sxs-lookup"><span data-stu-id="5c707-207">**NX_PPP_MAX_IPCP_PROTOCOL_RETRIES**: This defines the max number of retries if the PPP times out before sending another IPCP configure request message.</span></span> <span data-ttu-id="5c707-208">При достижении этого значения подтверждение PPP прерывается, а канал переходит в нерабочее состояние.</span><span class="sxs-lookup"><span data-stu-id="5c707-208">When this number is reached the PPP handshake is aborted and the link status is down.</span></span> <span data-ttu-id="5c707-209">Значение по умолчанию — 20.</span><span class="sxs-lookup"><span data-stu-id="5c707-209">The default value is 20.</span></span>
- <span data-ttu-id="5c707-210">**NX_PPP_MRU** — указывает максимальный размер данных, передаваемых в пакете (MRU) для PPP.</span><span class="sxs-lookup"><span data-stu-id="5c707-210">**NX_PPP_MRU**: Specifies the Maximum Receive Unit (MRU) for PPP.</span></span> <span data-ttu-id="5c707-211">По умолчанию это значение равно 1500 байт (минимальное значение).</span><span class="sxs-lookup"><span data-stu-id="5c707-211">By default, this value is 1,500 bytes (the minimum value).</span></span> <span data-ttu-id="5c707-212">Это определение можно задать в приложении перед включением *nx_ppp.h*.</span><span class="sxs-lookup"><span data-stu-id="5c707-212">This define can be set by the application prior to inclusion of *nx_ppp.h*.</span></span>
- <span data-ttu-id="5c707-213">**NX_PPP_MINIMUM_MRU** — указывает минимальный объем MRU, полученный в сообщении запроса настройки LCP.</span><span class="sxs-lookup"><span data-stu-id="5c707-213">**NX_PPP_MINIMUM_MRU**: Specifies the minimum MRU received in an LCP configure request message.</span></span> <span data-ttu-id="5c707-214">По умолчанию это значение равно 1500 байт (минимальное значение).</span><span class="sxs-lookup"><span data-stu-id="5c707-214">By default, this value is 1,500 bytes (the minimum value).</span></span> <span data-ttu-id="5c707-215">Это определение можно задать в приложении перед включением *nx_ppp.h*.</span><span class="sxs-lookup"><span data-stu-id="5c707-215">This define can be set by the application prior to inclusion of *nx_ppp.h*.</span></span>
- <span data-ttu-id="5c707-216">**NX_PPP_NAME_SIZE** — указывает размер строк имени, используемых при проверке подлинности.</span><span class="sxs-lookup"><span data-stu-id="5c707-216">**NX_PPP_NAME_SIZE**: Specifies the size of “name” strings used in authentication.</span></span> <span data-ttu-id="5c707-217">Значение по умолчанию равно 32 байт, но может быть переопределено перед включением \*nx_ppp.h.</span><span class="sxs-lookup"><span data-stu-id="5c707-217">The default value is set to 32bytes, but can be redefined prior to inclusion of \*nx_ppp.h.</span></span>
- <span data-ttu-id="5c707-218">**NX_PPP_PASSWORD_SIZE** — указывает размер строк пароля, используемых при проверке подлинности.</span><span class="sxs-lookup"><span data-stu-id="5c707-218">**NX_PPP_PASSWORD_SIZE**: Specifies the size of “password” strings used in authentication.</span></span> <span data-ttu-id="5c707-219">Значение по умолчанию равно 32 байт, но может быть переопределено перед включением *nx_ppp.h*.</span><span class="sxs-lookup"><span data-stu-id="5c707-219">The default value is set to 32bytes, but can be redefined prior to inclusion of *nx_ppp.h.*</span></span>
- <span data-ttu-id="5c707-220">**NX_PPP_PROTOCOL_TIMEOUT** — определяет параметр ожидания (в секундах), в течение которого задача PPP получает ответ на сообщение запроса протокола PPP.</span><span class="sxs-lookup"><span data-stu-id="5c707-220">**NX_PPP_PROTOCOL_TIMEOUT**: This defines the wait option (in seconds) for the PPP task to receive a response to a PPP protocol request message.</span></span> <span data-ttu-id="5c707-221">Значение по умолчанию — 4 секунды.</span><span class="sxs-lookup"><span data-stu-id="5c707-221">The default value is 4 seconds.</span></span>
- <span data-ttu-id="5c707-222">**NX_PPP_RECEIVE_TIMEOUTS** — определяет, сколько раз истекает время ожидания задачи потока PPP до получения следующего символа в потоке сообщений PPP.</span><span class="sxs-lookup"><span data-stu-id="5c707-222">**NX_PPP_RECEIVE_TIMEOUTS**: This defines the number of times the PPP thread task times out waiting to receive the next character in a PPP message stream.</span></span> <span data-ttu-id="5c707-223">После этого протокол PPP освобождает пакет и начинает ждать получения следующего сообщения PPP.</span><span class="sxs-lookup"><span data-stu-id="5c707-223">Thereafter, PPP releases the packet and begins waiting to receive the next PPP message.</span></span> <span data-ttu-id="5c707-224">Значение по умолчанию — 4.</span><span class="sxs-lookup"><span data-stu-id="5c707-224">The default value is 4.</span></span>
- <span data-ttu-id="5c707-225">**NX_PPP_SERIAL_BUFFER_SIZE** — указывает размер последовательного буфера получения символа.</span><span class="sxs-lookup"><span data-stu-id="5c707-225">**NX_PPP_SERIAL_BUFFER_SIZE**: Specifies the size of the receive character serial buffer.</span></span> <span data-ttu-id="5c707-226">По умолчанию это значение равно 3000 байт.</span><span class="sxs-lookup"><span data-stu-id="5c707-226">By default, this value is 3,000 bytes.</span></span> <span data-ttu-id="5c707-227">Это определение можно задать в приложении перед включением *nx_ppp.h*.</span><span class="sxs-lookup"><span data-stu-id="5c707-227">This define can be set by the application prior to inclusion of *nx_ppp.h*.</span></span>
- <span data-ttu-id="5c707-228">**NX_PPP_TIMEOUT** — определяет параметр ожидания (в тактах таймера) для выделения пакетов для передачи данных, а также для добавления последовательных данных PPP в пакеты для отправки на уровень IP.</span><span class="sxs-lookup"><span data-stu-id="5c707-228">**NX_PPP_TIMEOUT**: This defines the wait option (in timer ticks) for allocating packets to transmit data as well as buffer PPP serial data into packets to send to the IP layer.</span></span> <span data-ttu-id="5c707-229">Значение по умолчанию — 4\*NX_IP_PERIODIC_RATE (400 тактов).</span><span class="sxs-lookup"><span data-stu-id="5c707-229">The default value is 4\*NX_IP_PERIODIC_RATE (400 ticks).</span></span>
- <span data-ttu-id="5c707-230">**NX_PPP_THREAD_TIME_SLICE** — параметр временного среза для потоков PPP.</span><span class="sxs-lookup"><span data-stu-id="5c707-230">**NX_PPP_THREAD_TIME_SLICE**: Time-slice option for PPP threads.</span></span> <span data-ttu-id="5c707-231">Значением по умолчанию является TX_NO_TIME_SLICE.</span><span class="sxs-lookup"><span data-stu-id="5c707-231">By default, this value is TX_NO_TIME_SLICE.</span></span> <span data-ttu-id="5c707-232">Это определение можно задать в приложении перед включением *nx_ppp.h*.</span><span class="sxs-lookup"><span data-stu-id="5c707-232">This define can be set by the application prior to inclusion of *nx_ppp.h*.</span></span>
- <span data-ttu-id="5c707-233">**NX_PPP_VALUE_SIZE** — указывает размер строк значения, используемых при проверке подлинности CHAP.</span><span class="sxs-lookup"><span data-stu-id="5c707-233">**NX_PPP_VALUE_SIZE**: Specifies the size of “value” strings used in CHAP authentication.</span></span> <span data-ttu-id="5c707-234">Значение по умолчанию равно 32 байт, но может быть переопределено перед включением nx_ppp.h.</span><span class="sxs-lookup"><span data-stu-id="5c707-234">The default value is set to 32bytes, but can be redefined prior to inclusion of nx_ppp.h.</span></span>
