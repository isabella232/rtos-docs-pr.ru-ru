---
title: Глава 2. Установка и использование PPPoE-сервера в NetX для ОСРВ Azure
description: В этой главе рассматриваются разные вопросы, связанные с установкой, настройкой и использованием компонента PPPoE-сервера в NetX для ОСРВ Azure.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5b52164911676b68c67da01d698e41c02730e45a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814444"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-pppoe-server"></a><span data-ttu-id="9586b-103">Глава 2. Установка и использование PPPoE-сервера в NetX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="9586b-103">Chapter 2 - Installation and use of Azure RTOS NetX PPPoE Server</span></span>

<span data-ttu-id="9586b-104">В этой главе рассматриваются разные вопросы, связанные с установкой, настройкой и использованием компонента PPPoE-сервера в NetX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="9586b-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX PPPoE Server component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="9586b-105">Распространение продукта</span><span class="sxs-lookup"><span data-stu-id="9586b-105">Product Distribution</span></span>

<span data-ttu-id="9586b-106">PPPoE-сервера в NetX доступен по адресу [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span><span class="sxs-lookup"><span data-stu-id="9586b-106">PPPoE Server for NetX is available at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span> <span data-ttu-id="9586b-107">Этот пакет включает в себя два исходных файла и PDF-файл с этим документом:</span><span class="sxs-lookup"><span data-stu-id="9586b-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="9586b-108">**nx_pppoe_server.h**: файл заголовка для PPPoE-сервера для NetX.</span><span class="sxs-lookup"><span data-stu-id="9586b-108">**nx_pppoe_server.h**: Header file for PPPoE Server for NetX</span></span>
- <span data-ttu-id="9586b-109">**nx_pppoe_server.h**: исходный файл на C для PPPoE-сервера для NetX.</span><span class="sxs-lookup"><span data-stu-id="9586b-109">**nx_pppoe_server.c**: C Source file for PPPoE Server for NetX</span></span>
- <span data-ttu-id="9586b-110">**nx_pppoe_server.pdf**: описание PPPoE-сервера для NetX в формате PDF.</span><span class="sxs-lookup"><span data-stu-id="9586b-110">**nx_pppoe_server.pdf**: PDF description of PPPoE Server for NetX</span></span>
- <span data-ttu-id="9586b-111">**demo_netx_pppoe_server.c**: демонстрационный пример PPPoE-сервера для NetX.</span><span class="sxs-lookup"><span data-stu-id="9586b-111">**demo_netx_pppoe_server.c**: NetX PPPoE Server demonstration</span></span>

## <a name="pppoe-server-installation"></a><span data-ttu-id="9586b-112">Установка PPPoE-сервера</span><span class="sxs-lookup"><span data-stu-id="9586b-112">PPPoE Server Installation</span></span>

<span data-ttu-id="9586b-113">Чтобы использовать PPPoE-сервер для NetX, следует скопировать упомянутый выше дистрибутив целиком в тот же каталог, где установлен NetX.</span><span class="sxs-lookup"><span data-stu-id="9586b-113">In order to use PPPoE Server for NetX, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="9586b-114">Например, если NetX установлен в каталоге *\threadx\arm7\green*, нужно скопировать в тот же каталог файлы *nx_pppoe_server.h* и *nx_pppoe_server.c*.</span><span class="sxs-lookup"><span data-stu-id="9586b-114">For example, if NetX is installed in the directory "*\threadx\arm7\green*" then the *nx_pppoe_server.h* and *nx_pppoe_server.c* files should be copied into this directory.</span></span>

## <a name="using-pppoe-server"></a><span data-ttu-id="9586b-115">Использование PPPoE-сервера</span><span class="sxs-lookup"><span data-stu-id="9586b-115">Using PPPoE Server</span></span>

<span data-ttu-id="9586b-116">Использование PPPoE-сервера для NetX не представляет никаких трудностей.</span><span class="sxs-lookup"><span data-stu-id="9586b-116">Using PPPoE Server for NetX is easy.</span></span> <span data-ttu-id="9586b-117">В коде приложения следует включить файл *nx_pppoe_server.h* после *tx_api.h* и *nx_api.h*, чтобы использовать ThreadX и NetX соответственно.</span><span class="sxs-lookup"><span data-stu-id="9586b-117">Basically, the application code must include *nx_pppoe_server.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX, respectively.</span></span> <span data-ttu-id="9586b-118">После включения файла *nx_pppoe_server.h* код приложения может выполнять вызовы функций PPPoE-сервера, приведенные далее в этом руководстве.</span><span class="sxs-lookup"><span data-stu-id="9586b-118">Once *nx_pppoe_server.h* is included, the application code is then able to make the PPPoE Server function calls specified later in this guide.</span></span> <span data-ttu-id="9586b-119">Приложение также должно включить файл *nx_pppoe_server.c* в ходе сборки.</span><span class="sxs-lookup"><span data-stu-id="9586b-119">The application must also include *nx_pppoe_server.c* in the build process.</span></span> <span data-ttu-id="9586b-120">Этот файл должен быть скомпилирован так же, как и другие файлы приложения, а его форма объекта должна быть связана с файлами приложения.</span><span class="sxs-lookup"><span data-stu-id="9586b-120">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="9586b-121">Это все, что необходимо для использования PPPoE-сервера в NetX.</span><span class="sxs-lookup"><span data-stu-id="9586b-121">This is all that is required to use NetX PPPoE Server.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="9586b-122">Пример небольшой системы</span><span class="sxs-lookup"><span data-stu-id="9586b-122">Small Example System</span></span>

<span data-ttu-id="9586b-123">Ниже на рис. 1.1 приведен пример, демонстрирующий использование PPPoE-сервера в NetX.</span><span class="sxs-lookup"><span data-stu-id="9586b-123">The following is an example that illustrates how to use NetX PPPoE Server is described in Figure 1.1.</span></span> <span data-ttu-id="9586b-124">В этом примере выполняется включение файла *nx_pppoe_server.h* для PPPoE-сервера (строка 50).</span><span class="sxs-lookup"><span data-stu-id="9586b-124">In this example, the PPPoE Server include file *nx_pppoe_server.h* is brought in at line 50.</span></span> <span data-ttu-id="9586b-125">Затем создается PPPoE-сервер в *thread_0_entry* (строка 248).</span><span class="sxs-lookup"><span data-stu-id="9586b-125">Next, PPPoE Server is created in *"thread_0_entry*" at line 248.</span></span> <span data-ttu-id="9586b-126">Обратите внимание, что PPPoE-сервер следует создавать после создания экземпляра IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="9586b-126">Note that PPPoE Server should be created after create the IP instance.</span></span> <span data-ttu-id="9586b-127">Экземпляр IP-адреса создается и инициализируется в строке 165.</span><span class="sxs-lookup"><span data-stu-id="9586b-127">The IP instance is created and initialized line165.</span></span> <span data-ttu-id="9586b-128">Блок управления PPPoE-сервером *pppoe_server* определен в глобальной переменной ранее (строка 79).</span><span class="sxs-lookup"><span data-stu-id="9586b-128">The PPPoE Server control block "*pppoe_server*" was defined as a global variable at line 79 previously.</span></span> <span data-ttu-id="9586b-129">Функции уведомления задаются в строке 257.</span><span class="sxs-lookup"><span data-stu-id="9586b-129">The notify functions are set at line 257.</span></span> <span data-ttu-id="9586b-130">Обратите внимание, что необходимо задать функцию уведомления pppoe_session_data_receive.</span><span class="sxs-lookup"><span data-stu-id="9586b-130">Note that pppoe_session_data_receive notify function must be set.</span></span> <span data-ttu-id="9586b-131">Когда экземпляры IP-адреса и PPPoE-сервера будут успешно созданы, запускается процесс PPPoE-сервера для создания сеанса PPPoE путем вызова nx_pppoe_server_enable (строка 272).</span><span class="sxs-lookup"><span data-stu-id="9586b-131">After successful creation of IP and PPPoE Server, the PPPoE Server process of establishing a PPPoE session at the call to nx_pppoe_server_enable at line 272.</span></span>

<span data-ttu-id="9586b-132">Как правило, модуль PPPoE следует использовать совместно с модулем PPP.</span><span class="sxs-lookup"><span data-stu-id="9586b-132">In general, PPPoE module should be used with PPP module.</span></span> <span data-ttu-id="9586b-133">В этом примере включается файл *nx_ppp.h* для PPP-сервера (строка 49).</span><span class="sxs-lookup"><span data-stu-id="9586b-133">In this example, the PPP Server include file *nx_ppp.h* is brought in at line 49.</span></span> <span data-ttu-id="9586b-134">Затем создается PPP-сервера (строка 174).</span><span class="sxs-lookup"><span data-stu-id="9586b-134">Next, PPP Server is created at line 174.</span></span> <span data-ttu-id="9586b-135">Строка 182 настраивает функцию для отправки пакета PPP.</span><span class="sxs-lookup"><span data-stu-id="9586b-135">Line 182 setup the function to send PPP packet.</span></span> <span data-ttu-id="9586b-136">Строки 188–200 настраивают IP-адреса и определяют протокол PAP.</span><span class="sxs-lookup"><span data-stu-id="9586b-136">Line 188-200 setup the IP addresses and define the pap protocol.</span></span> <span data-ttu-id="9586b-137">Строки 115–139 настраивают имя пользователя и пароль для протокола PAP.</span><span class="sxs-lookup"><span data-stu-id="9586b-137">Line 115-139 setup the user name and password for pap protocol.</span></span>

<span data-ttu-id="9586b-138">После этого создается сеанс PPPoE.</span><span class="sxs-lookup"><span data-stu-id="9586b-138">After the PPPoE session established.</span></span> <span data-ttu-id="9586b-139">Приложение может вызвать nx_pppoe_server_session_get, чтобы получить сведения о сеансе, а именно MAC-адрес клиента и идентификатор сеанса (строка 281).</span><span class="sxs-lookup"><span data-stu-id="9586b-139">The application can call nx_pppoe_server_session_get to get the session information (client MAC address and session id) at line 281.</span></span>

<span data-ttu-id="9586b-140">Если приложению больше не нужно обрабатывать трафик PPP, следует выполнить PppCloseInd или nx_pppoe_server_session_terminate для завершения сеанса PPPoE.</span><span class="sxs-lookup"><span data-stu-id="9586b-140">When the application no longer process PPP traffic, the application PppCloseInd or nx_pppoe_server_session_terminate to terminate the PPPoE session.</span></span>

> [!NOTE]
> <span data-ttu-id="9586b-141">В нашем примере PPPoE-сервер работает с обычным стеком IP, и они совместно используют один драйвер Ethernet.</span><span class="sxs-lookup"><span data-stu-id="9586b-141">In this example, PPPoE Server work with normal IP stack at the same time, and share one Ethernet driver.</span></span> <span data-ttu-id="9586b-142">Один и тот же драйвер Ethernet передается обычному экземпляру IP-адреса (строка 165) и экземпляру PPPoE-сервера (строка 248).</span><span class="sxs-lookup"><span data-stu-id="9586b-142">Pass the same Ethernet driver for normal IP instance at line 165 and PPPoE Server instance at line 248.</span></span>

> [!NOTE]
> <span data-ttu-id="9586b-143">Реализация протокола PPPoE предоставляет функции для вызова из программного обеспечения, для которого определено NX_PPPoE_SERVER_SESSION_CONTROL_ENABELE.</span><span class="sxs-lookup"><span data-stu-id="9586b-143">The functions are provided by the PPPoE implementation for calling by the software under defined NX_PPPoE_SERVER_SESSION_CONTROL_ENABELE.</span></span>

<span data-ttu-id="9586b-144">Если этот параметр определен, включаются функции для управления сеансом PPPoE.</span><span class="sxs-lookup"><span data-stu-id="9586b-144">If defined, enables the feature that controls the PPPoE session.</span></span>

<span data-ttu-id="9586b-145">Тогда PPPoE-сервер не будет автоматически отвечать на запросы до тех пор, пока приложение не вызовет конкретный API. Если этот параметр не определен, PPPoE-сервер будет автоматически отвечать на запросы.</span><span class="sxs-lookup"><span data-stu-id="9586b-145">PPPoE server does not automatically response to the request until application call specific API, if not defined, PPPoE Server automatically responses to the request.</span></span> <span data-ttu-id="9586b-146">Он включается по умолчанию в файле nx_pppoe_server.h.</span><span class="sxs-lookup"><span data-stu-id="9586b-146">It enables by default in nx_pppoe_server.h.</span></span>

<span data-ttu-id="9586b-147">Не забудьте указать для **NX_PHYSICAL_HEADER** значение 24, чтобы иметь достаточно места для заполнения физического заголовка.</span><span class="sxs-lookup"><span data-stu-id="9586b-147">Note, redefine **NX_PHYSICAL_HEADER** to 24 to ensure enough space for filling in physical header.</span></span> <span data-ttu-id="9586b-148">Физический заголовок: 14 (заголовок Ethernet) + 6 (заголовок PPPoE) + 2 (заголовок PPP) + 2 (4-байтовое выравнивание).</span><span class="sxs-lookup"><span data-stu-id="9586b-148">Physical header:14(Ethernet header) + 6(PPPoE header) + 2(PPP header) + 2(four-byte aligment).</span></span>

```c
/**************************************************************************/
/**************************************************************************/
/**                                                                       */
/** NetX PPPoE Server stack Component                                     */
/**                                                                       */
/** This is a small demo of the high-performance NetX PPPoE Server        */
/** stack. This demo includes IP instance, PPPoE Server and PPP Server    */
/** stack. Create one IP instance includes two interfaces to support      */
/** for normal IP stack and PPPoE Server, PPPoE Server can use the        */
/** mutex of IP instance to send PPPoE message when share one Ethernet    */
/** driver. PPPoE Server work with normal IP instance at the same time.   */
/**                                                                       */
/** Note1: Substitute your Ethernet driver instead of                     */
/** _nx_ram_network_driver before run this demo                           */
/**                                                                       */
/** Note2: Prerequisite for using PPPoE.                                  */
/** Redefine NX_PHYSICAL_HEADER to 24 to ensure enough space for filling  */
/** in physical header. Physical header:14(Ethernet header)               */
/** + 6(PPPoE header) + 2(PPP header) + 2(four-byte aligment)             */
/**                                                                       */
/**************************************************************************/
/**************************************************************************/


/*****************************************************************/
/*                            NetX Stack                         */
/*****************************************************************/

                                      /***************************/
                                      /* PPP Server              */
                                      /***************************/

                                      /***************************/
                                      /* PPPoE Server            */
                                      /***************************/
/***************************/         /***************************/
/* Normal Ethernet Type    */         /* PPPoE Ethernet Type     */
/***************************/         /***************************/
/***************************/         /***************************/
/* Interface 0             */         /* Interface 1             */
/***************************/         /***************************/

/*****************************************************************/
/*                     Ethernet Dirver                           */
/*****************************************************************/

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nx_ppp.h"
#include     "nx_pppoe_server.h"

/* Defined NX_PPP_PPPOE_ENABLE if use Express Logic's PPP, since PPP module has been modified to match PPPoE moduler under this definition. */
#ifdef NX_PPP_PPPOE_ENABLE

/*   If the driver is not initialized in other module, define */
/*   NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE to initialize the driver in PPPoE module. */
/*   In this demo, the driver has been initialized in IP module. */

#ifdef NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE

/*   NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE: If defined, enables the feature that */
/*   controls the PPPoE session. PPPoE server does not automatically response to the */
/*   request until application call specific API. */

/* Define the block size. */
#define     NX_PACKET_POOL_SIZE     ((1536 + sizeof(NX_PACKET)) * 30)
#define     DEMO_STACK_SIZE         2048
#define     PPPOE_THREAD_SIZE       2048

/* Define the ThreadX and NetX object control blocks... */
TX_THREAD           thread_0;

/* Define the packet pool and IP instance for normal IP instnace. */
NX_PACKET_POOL      pool_0;
NX_IP               ip_0;

/* Define the PPP Server instance. */
NX_PPP              ppp_server;

/* Define the PPPoE Server instance. */
NX_PPPOE_SERVER     pppoe_server;

/* Define the counters. */
CHAR                *pointer;
ULONG               error_counter;

/* Define thread prototypes. */
void     thread_0_entry(ULONG thread_input);

/***** Substitute your PPP driver entry function here *********/
extern void     _nx_ppp_driver(NX_IP_DRIVER *driver_req_ptr);

/***** Substitute your Ethernet driver entry function here *********/
extern void     _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);

/* Define the callback functions. */
void     PppDiscoverReq(UINT interfaceHandle);
void     PppOpenReq(UINT interfaceHandle, ULONG length, UCHAR *data);
void     PppCloseRsp(UINT interfaceHandle);
void     PppCloseReq(UINT interfaceHandle);
void     PppTransmitDataReq(UINT interfaceHandle, ULONG length, UCHAR *data, UINT packet_id);
void     PppReceiveDataRsp(UINT interfaceHandle, UCHAR *data);

/* Define the porting layer function for Express Logic's PPP to simulate TTP's PPP. */
/* Functions to be provided by PPP for calling by the PPPoE Stack. */
void     ppp_server_packet_send(NX_PACKET *packet_ptr);

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

UINT verify_login(CHAR *name, CHAR *password)
{

    if ((name[0] == 'm') &&
        (name[1] == 'y') &&
        (name[2] == 'n') &&
        (name[3] == 'a') &&
        (name[4] == 'm') &&
        (name[5] == 'e') &&
        (name[6] == (CHAR) 0) &&
        (password[0] == 'm') &&
        (password[1] == 'y') &&
        (password[2] == 'p') &&
        (password[3] == 'a') &&
        (password[4] == 's') &&
        (password[5] == 's') &&
        (password[6] == 'w') &&
        (password[7] == 'o') &&
        (password[8] == 'r') &&
        (password[9] == 'd') &&
        (password[10] == (CHAR) 0))
            return(NX_SUCCESS);
    else
        return(NX_PPP_ERROR);
}

/* Define what the initial system looks like. */

void tx_application_define(void *first_unused_memory)
{

    UINT status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a packet pool for normal IP instance. */
    status = nx_packet_pool_create(&pool_0, "NetX Main Packet Pool",
                                    (1536 + sizeof(NX_PACKET)),
                                    pointer, NX_PACKET_POOL_SIZE);
                                    pointer = pointer + NX_PACKET_POOL_SIZE;

    /* Check for error. */
    if (status)
        error_counter++;

    /* Create an normal IP instance. */
    status = nx_ip_create(&ip_0, "NetX IP Instance", IP_ADDRESS(192, 168, 100, 43),
                        0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                        pointer, 2048, 1);
                        pointer = pointer + 2048;

    /* Check for error. */
    if (status)
        error_counter++;

    /* Create the PPP instance. */
    status = nx_ppp_create(&ppp_server, "PPP Instance", &ip_0, pointer, 2048, 1,
                            &pool_0, NX_NULL, NX_NULL);
    pointer = pointer + 2048;

    /* Check for PPP create error. */
    if (status)
        error_counter++;

    /* Set the PPP packet send function. */
    status = nx_ppp_packet_send_set(&ppp_server, ppp_server_packet_send);

    /* Check for PPP packet send function set error. */
    if (status)
        error_counter++;

    /* Define IP address. This PPP instance is effectively the server since it has both IP addresses. */
    status = nx_ppp_ip_address_assign(&ppp_server, IP_ADDRESS(192, 168, 10, 43),                                         IP_ADDRESS(192, 168, 10, 44));

    /* Check for PPP IP address assign error. */
    if (status)
        error_counter++;

    /* Setup PAP, this PPP instance is effectively the server since it will verify the name and password. */
    status = nx_ppp_pap_enable(&ppp_server, NX_NULL, verify_login);

    /* Check for PPP PAP enable error. */
    if (status)
        error_counter++;

    /* Attach an interface for PPP. */
    status = nx_ip_interface_attach(&ip_0, "Second Interface For PPP", 
                            IP_ADDRESS(0, 0, 0, 0), 0, nx_ppp_driver);

    /* Check for error. */
    if (status)
        error_counter++;

    /* Enable ARP and supply ARP cache memory for Normal IP Instance. */
    status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors. */
    if (status)
        error_counter++;

    /* Enable ICMP */
    status = nx_icmp_enable(&ip_0);
    if(status)
        error_counter++;

    /* Enable UDP traffic. */
    status = nx_udp_enable(&ip_0);
    if (status)
        error_counter++;

    /* Enable TCP traffic. */
    status = nx_tcp_enable(&ip_0);
    if (status)
        error_counter++;

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
                    pointer, DEMO_STACK_SIZE,
                    4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);
                    pointer = pointer + DEMO_STACK_SIZE;
}

/* Define the test threads. */

void     thread_0_entry(ULONG thread_input)
{
UINT     status;
ULONG    ip_status;

    /* Create the PPPoE instance. */
    status = nx_pppoe_server_create(&pppoe_server, (UCHAR *)"PPPoE Server", &ip_0, 0,
                    _nx_ram_network_driver, &pool_0, pointer, PPPOE_THREAD_SIZE, 4);
    pointer = pointer + PPPOE_THREAD_SIZE;
    if (status)
    {
        error_counter++;
        return;
    }

    /* Set the callback notify function. */
    status = nx_pppoe_server_callback_notify_set(&pppoe_server, PppDiscoverReq,
        PppOpenReq, PppCloseRsp, PppCloseReq, PppTransmitDataReq, PppReceiveDataRsp);

    if (status)
    {
        error_counter++;
        return;
    }

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call function function to set the default service Name. */
        /* PppInitInd(length, aData); */
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */

    /* Enable PPPoE Server. */
    status = nx_pppoe_server_enable(&pppoe_server);
    if (status)
    {
        error_counter++;
        return;
    }

    /* Get the PPPoE Client physical address and Session ID after establish PPPoE Session. */
    /*
        status = nx_pppoe_server_session_get(&pppoe_server, interfaceHandle, &client_mac_msw, &client_mac_lsw, &session_id);
        if (status)
            error_counter++;
    */

    /* Wait for the link to come up. */
    status = nx_ip_interface_status_check(&ip_0, 1, NX_IP_ADDRESS_RESOLVED,
                                            &ip_status, NX_WAIT_FOREVER);
    if (status)
    {
        error_counter++;
        return;
    }

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to terminate the PPPoE Session. */
        /* PppCloseInd(interfaceHandle, causeCode); */
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */

}

void     PppDiscoverReq(UINT interfaceHandle)
{

    /* Receive the PPPoE Discovery Initiation Message. */
    
    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to allow TTP's software to define the Service Name field of the PADO packet. */
        PppDiscoverCnf(0, NX_NULL, interfaceHandle);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}

void     PppOpenReq(UINT interfaceHandle, ULONG length, UCHAR *data)
{

    /* Get the notify that receive the PPPoE Discovery Request Message. */

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to allow TTP's software to accept the PPPoE session. */
        PppOpenCnf(NX_TRUE, interfaceHandle);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}

void     PppCloseRsp(UINT interfaceHandle)
{

    /* Get the notify that receive the PPPoE Discovery Terminate Message. */

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to allow TTP's software to confirm that the handle has been freed. */
        PppCloseCnf(interfaceHandle);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}

void     PppCloseReq(UINT interfaceHandle)
{

    /* Get the notify that PPPoE Discovery Terminate Message has been sent. */

}

void     PppTransmitDataReq(UINT interfaceHandle, ULONG length, UCHAR *data, UINT packet_id)
{

    NX_PACKET *packet_ptr;

    /* Get the notify that receive the PPPoE Session data. */

    /* Call PPP Server to receive the PPP data fame. */
    packet_ptr = (NX_PACKET *)(packet_id);
    nx_ppp_packet_receive(&ppp_server, packet_ptr);

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to confirm that the data has been processed. */
        PppTransmitDataCnf(interfaceHandle, data, packet_id);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}

void     PppReceiveDataRsp(UINT interfaceHandle, UCHAR *data)
{

    /* Get the notify that the PPPoE Session data has been sent. */

}

/* PPP Server send function. */
void     ppp_server_packet_send(NX_PACKET *packet_ptr)
{

    /* For Express Logic's PPP test, the session should be the first session, so set interfaceHandle as 0. */
    UINT interfaceHandle = 0;

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        while(packet_ptr)
        {

            /* Call functions to be provided by PPPoE for TTP. */
            PppReceiveDataInd(interfaceHandle, (packet_ptr -> nx_packet_append_ptr -
            packet_ptr -> nx_packet_prepend_ptr), packet_ptr -> nx_packet_prepend_ptr);

            /* Move to the next packet structure. */
            packet_ptr = packet_ptr -> nx_packet_next;
        }
    #else
        /* Directly Call PPPoE send function to send out the data through PPPoE module. */
        nx_pppoe_server_session_packet_send(&pppoe_server, interfaceHandle, packet_ptr);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}
#endif /* NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE */

#endif /* NX_PPP_PPPOE_ENABLE */
```

<span data-ttu-id="9586b-149">Рис. 1.1. Пример использования PPPoE-сервера с NetX</span><span class="sxs-lookup"><span data-stu-id="9586b-149">Figure 1.1 Example of PPPoE Server use with NetX</span></span>

## <a name="configuration-options"></a><span data-ttu-id="9586b-150">Параметры конфигурации</span><span class="sxs-lookup"><span data-stu-id="9586b-150">Configuration Options</span></span>

<span data-ttu-id="9586b-151">Существует ряд параметров конфигурации для сборки PPPoE-сервера для NetX.</span><span class="sxs-lookup"><span data-stu-id="9586b-151">There are several configuration options for building PPPoE Server for NetX.</span></span> <span data-ttu-id="9586b-152">Их подробное описание приводится ниже:</span><span class="sxs-lookup"><span data-stu-id="9586b-152">The following list describes each in detail:</span></span>

- <span data-ttu-id="9586b-153">**NX_DISABLE_ERROR_CHECKING** — если определен, удаляет базовую проверку ошибок PPPoE-сервера.</span><span class="sxs-lookup"><span data-stu-id="9586b-153">**NX_DISABLE_ERROR_CHECKING**: Defined, this option removes the basic PPPoE Server error checking.</span></span> <span data-ttu-id="9586b-154">Обычно он включается после завершения отладки приложения.</span><span class="sxs-lookup"><span data-stu-id="9586b-154">It is typically used after the application has been debugged.</span></span>

- <span data-ttu-id="9586b-155">**NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE** — если определен, включает возможность управления сеансом PPPoE.</span><span class="sxs-lookup"><span data-stu-id="9586b-155">**NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE**: If defined, enables the feature that controls the PPPoE session.</span></span> <span data-ttu-id="9586b-156">PPPoE-сервера не будет автоматически отвечать на запросы до тех пор, пока приложение не вызовет конкретный API.</span><span class="sxs-lookup"><span data-stu-id="9586b-156">PPPoE server does not automatically response to the request until application call specific API.</span></span>

- <span data-ttu-id="9586b-157">**NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE** — если определен, включает возможность инициализировать драйвер Ethernet в модуле PPPoE.</span><span class="sxs-lookup"><span data-stu-id="9586b-157">**NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE**: If defined, enables the feature to initialize the Ethernet driver in PPPoE module.</span></span> <span data-ttu-id="9586b-158">По умолчанию он отключен.</span><span class="sxs-lookup"><span data-stu-id="9586b-158">It disables by default.</span></span>

- <span data-ttu-id="9586b-159">**NX_PPPOE_SERVER_THREAD_TIME_SLICE** — временной интервал для потока PPPoE-сервера.</span><span class="sxs-lookup"><span data-stu-id="9586b-159">**NX_PPPOE_SERVER_THREAD_TIME_SLICE**: Time-slice option for PPPoE Server thread.</span></span> <span data-ttu-id="9586b-160">По умолчанию имеет значение TX_NO_TIME_SLICE.</span><span class="sxs-lookup"><span data-stu-id="9586b-160">By default, this value is TX_NO_TIME_SLICE.</span></span>

- <span data-ttu-id="9586b-161">**NX_PPPOE_SERVER_MAX_CLIENT_SESSION_NUMBER** — определяет максимальное количество одновременных сеансов клиента.</span><span class="sxs-lookup"><span data-stu-id="9586b-161">**NX_PPPOE_SERVER_MAX_CLIENT_SESSION_NUMBER**: This defines the max number of concurrent client sessions.</span></span> <span data-ttu-id="9586b-162">По умолчанию имеет значение 10.</span><span class="sxs-lookup"><span data-stu-id="9586b-162">By default, this value is 10.</span></span>

- <span data-ttu-id="9586b-163">**NX_PPPOE_SERVER_MAX_HOST_UNIQ_SIZE** — определяет максимальное значение параметра Host-Uniq.</span><span class="sxs-lookup"><span data-stu-id="9586b-163">**NX_PPPOE_SERVER_MAX_HOST_UNIQ_SIZE**: This defines the max size of Host-Uniq.</span></span> <span data-ttu-id="9586b-164">По умолчанию имеет значение 32.</span><span class="sxs-lookup"><span data-stu-id="9586b-164">By default, this value is 32.</span></span>

- <span data-ttu-id="9586b-165">**NX_PPPOE_SERVER_MAX_RELAY_SESSION_ID_SIZE** — определяет максимальный размер параметра Relay-Session-Id. По умолчанию имеет значение 12.</span><span class="sxs-lookup"><span data-stu-id="9586b-165">**NX_PPPOE_SERVER_MAX_RELAY_SESSION_ID_SIZE**: This defines the max size of Relay-Session-Id. By default, this value is 12.</span></span>

- <span data-ttu-id="9586b-166">**NX_PPPOE_SERVER_MIN_PACKET_PAYLOAD_SIZE** — определяет минимальный размер полезных данных в пакете для PPPoE-сервера.</span><span class="sxs-lookup"><span data-stu-id="9586b-166">**NX_PPPOE_SERVER_MIN_PACKET_PAYLOAD_SIZE**: Specifies the Minimum packet payload size for PPPoE Server.</span></span> <span data-ttu-id="9586b-167">Если размер полезных данных в пакете превышает это значение, можно избежать появления цепочки пакетов.</span><span class="sxs-lookup"><span data-stu-id="9586b-167">If the packet payload size is greater than this value, can avoid packet chained.</span></span> <span data-ttu-id="9586b-168">По умолчанию имеет значение 1520 байт (то есть максимальный размер полезных данных Ethernet 1500 + заголовок Ethernet 14 + CRC 2 + четырехбайтовое выравнивание 4).</span><span class="sxs-lookup"><span data-stu-id="9586b-168">By default, this value is 1520 (Maximum Payload Size of Ethernet 1500, Ethernet Header 14, CRC 2 and Four-byte alignment 4).</span></span>

- <span data-ttu-id="9586b-169">**NX_PPPOE_SERVER_PACKET_TIMEOUT** — определяет время ожидания для выделения пакетов или добавления данных в пакеты (в тактах таймера).</span><span class="sxs-lookup"><span data-stu-id="9586b-169">**NX_PPPOE_SERVER_PACKET_TIMEOUT**: This defines the wait potion(in timer ticks) for allocating packets or appending data into packets.</span></span> <span data-ttu-id="9586b-170">По умолчанию это значение равно **NX_IP_PERIODIC_RATE** (100 тактов).</span><span class="sxs-lookup"><span data-stu-id="9586b-170">By default, this value is **NX_IP_PERIODIC_RATE** (100 ticks).</span></span>

- <span data-ttu-id="9586b-171">**NX_PPPOE_SERVER_START_SESSION_ID** — определяет начальное значение идентификатора сеанса для присвоения сеансу PPPoE.</span><span class="sxs-lookup"><span data-stu-id="9586b-171">**NX_PPPOE_SERVER_START_SESSION_ID**: This defines the start Session ID for assigning to the PPPoE Session.</span></span> <span data-ttu-id="9586b-172">По умолчанию это значение равно 0X4944 (значение ASCII для строки "ID").</span><span class="sxs-lookup"><span data-stu-id="9586b-172">By default, this value is 0X4944(ASCII value for ID).</span></span>