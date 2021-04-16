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
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-pppoe-server"></a>Глава 2. Установка и использование PPPoE-сервера в NetX для ОСРВ Azure

В этой главе рассматриваются разные вопросы, связанные с установкой, настройкой и использованием компонента PPPoE-сервера в NetX для ОСРВ Azure.

## <a name="product-distribution"></a>Распространение продукта

PPPoE-сервера в NetX доступен по адресу [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx). Этот пакет включает в себя два исходных файла и PDF-файл с этим документом:

- **nx_pppoe_server.h**: файл заголовка для PPPoE-сервера для NetX.
- **nx_pppoe_server.h**: исходный файл на C для PPPoE-сервера для NetX.
- **nx_pppoe_server.pdf**: описание PPPoE-сервера для NetX в формате PDF.
- **demo_netx_pppoe_server.c**: демонстрационный пример PPPoE-сервера для NetX.

## <a name="pppoe-server-installation"></a>Установка PPPoE-сервера

Чтобы использовать PPPoE-сервер для NetX, следует скопировать упомянутый выше дистрибутив целиком в тот же каталог, где установлен NetX. Например, если NetX установлен в каталоге *\threadx\arm7\green*, нужно скопировать в тот же каталог файлы *nx_pppoe_server.h* и *nx_pppoe_server.c*.

## <a name="using-pppoe-server"></a>Использование PPPoE-сервера

Использование PPPoE-сервера для NetX не представляет никаких трудностей. В коде приложения следует включить файл *nx_pppoe_server.h* после *tx_api.h* и *nx_api.h*, чтобы использовать ThreadX и NetX соответственно. После включения файла *nx_pppoe_server.h* код приложения может выполнять вызовы функций PPPoE-сервера, приведенные далее в этом руководстве. Приложение также должно включить файл *nx_pppoe_server.c* в ходе сборки. Этот файл должен быть скомпилирован так же, как и другие файлы приложения, а его форма объекта должна быть связана с файлами приложения. Это все, что необходимо для использования PPPoE-сервера в NetX.

## <a name="small-example-system"></a>Пример небольшой системы

Ниже на рис. 1.1 приведен пример, демонстрирующий использование PPPoE-сервера в NetX. В этом примере выполняется включение файла *nx_pppoe_server.h* для PPPoE-сервера (строка 50). Затем создается PPPoE-сервер в *thread_0_entry* (строка 248). Обратите внимание, что PPPoE-сервер следует создавать после создания экземпляра IP-адреса. Экземпляр IP-адреса создается и инициализируется в строке 165. Блок управления PPPoE-сервером *pppoe_server* определен в глобальной переменной ранее (строка 79). Функции уведомления задаются в строке 257. Обратите внимание, что необходимо задать функцию уведомления pppoe_session_data_receive. Когда экземпляры IP-адреса и PPPoE-сервера будут успешно созданы, запускается процесс PPPoE-сервера для создания сеанса PPPoE путем вызова nx_pppoe_server_enable (строка 272).

Как правило, модуль PPPoE следует использовать совместно с модулем PPP. В этом примере включается файл *nx_ppp.h* для PPP-сервера (строка 49). Затем создается PPP-сервера (строка 174). Строка 182 настраивает функцию для отправки пакета PPP. Строки 188–200 настраивают IP-адреса и определяют протокол PAP. Строки 115–139 настраивают имя пользователя и пароль для протокола PAP.

После этого создается сеанс PPPoE. Приложение может вызвать nx_pppoe_server_session_get, чтобы получить сведения о сеансе, а именно MAC-адрес клиента и идентификатор сеанса (строка 281).

Если приложению больше не нужно обрабатывать трафик PPP, следует выполнить PppCloseInd или nx_pppoe_server_session_terminate для завершения сеанса PPPoE.

> [!NOTE]
> В нашем примере PPPoE-сервер работает с обычным стеком IP, и они совместно используют один драйвер Ethernet. Один и тот же драйвер Ethernet передается обычному экземпляру IP-адреса (строка 165) и экземпляру PPPoE-сервера (строка 248).

> [!NOTE]
> Реализация протокола PPPoE предоставляет функции для вызова из программного обеспечения, для которого определено NX_PPPoE_SERVER_SESSION_CONTROL_ENABELE.

Если этот параметр определен, включаются функции для управления сеансом PPPoE.

Тогда PPPoE-сервер не будет автоматически отвечать на запросы до тех пор, пока приложение не вызовет конкретный API. Если этот параметр не определен, PPPoE-сервер будет автоматически отвечать на запросы. Он включается по умолчанию в файле nx_pppoe_server.h.

Не забудьте указать для **NX_PHYSICAL_HEADER** значение 24, чтобы иметь достаточно места для заполнения физического заголовка. Физический заголовок: 14 (заголовок Ethernet) + 6 (заголовок PPPoE) + 2 (заголовок PPP) + 2 (4-байтовое выравнивание).

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

Рис. 1.1. Пример использования PPPoE-сервера с NetX

## <a name="configuration-options"></a>Параметры конфигурации

Существует ряд параметров конфигурации для сборки PPPoE-сервера для NetX. Их подробное описание приводится ниже:

- **NX_DISABLE_ERROR_CHECKING** — если определен, удаляет базовую проверку ошибок PPPoE-сервера. Обычно он включается после завершения отладки приложения.

- **NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE** — если определен, включает возможность управления сеансом PPPoE. PPPoE-сервера не будет автоматически отвечать на запросы до тех пор, пока приложение не вызовет конкретный API.

- **NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE** — если определен, включает возможность инициализировать драйвер Ethernet в модуле PPPoE. По умолчанию он отключен.

- **NX_PPPOE_SERVER_THREAD_TIME_SLICE** — временной интервал для потока PPPoE-сервера. По умолчанию имеет значение TX_NO_TIME_SLICE.

- **NX_PPPOE_SERVER_MAX_CLIENT_SESSION_NUMBER** — определяет максимальное количество одновременных сеансов клиента. По умолчанию имеет значение 10.

- **NX_PPPOE_SERVER_MAX_HOST_UNIQ_SIZE** — определяет максимальное значение параметра Host-Uniq. По умолчанию имеет значение 32.

- **NX_PPPOE_SERVER_MAX_RELAY_SESSION_ID_SIZE** — определяет максимальный размер параметра Relay-Session-Id. По умолчанию имеет значение 12.

- **NX_PPPOE_SERVER_MIN_PACKET_PAYLOAD_SIZE** — определяет минимальный размер полезных данных в пакете для PPPoE-сервера. Если размер полезных данных в пакете превышает это значение, можно избежать появления цепочки пакетов. По умолчанию имеет значение 1520 байт (то есть максимальный размер полезных данных Ethernet 1500 + заголовок Ethernet 14 + CRC 2 + четырехбайтовое выравнивание 4).

- **NX_PPPOE_SERVER_PACKET_TIMEOUT** — определяет время ожидания для выделения пакетов или добавления данных в пакеты (в тактах таймера). По умолчанию это значение равно **NX_IP_PERIODIC_RATE** (100 тактов).

- **NX_PPPOE_SERVER_START_SESSION_ID** — определяет начальное значение идентификатора сеанса для присвоения сеансу PPPoE. По умолчанию это значение равно 0X4944 (значение ASCII для строки "ID").