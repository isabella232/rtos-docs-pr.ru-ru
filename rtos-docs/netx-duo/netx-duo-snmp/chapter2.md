---
title: Глава 2. Установка и использование SNMP-агента NetX Duo для ОСРВ Azure
description: В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием SNMP-агента NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6e18906b6356bd8ff4efdc1ab0f2809d75493ad027c3d3e27e0536ee4b80f43b
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798288"
---
# <a name="chapter-2---installation-and-use-of-the-azure-rtos-netx-duo-snmp-agent"></a>Глава 2. Установка и использование SNMP-агента NetX Duo для ОСРВ Azure

В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента SNMP-агент NetX Duo для ОСРВ Azure.

## <a name="product-distribution"></a>Распространение продукта

Агент SNMP для NetX Duo доступен по адресу [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo). Пакет содержит четыре файла исходного кода, один файл заголовков и PDF-файл, содержащий этот документ:

- **nxd_snmp.h** — заголовочный файл SNMP для NetX Duo.
- **demo_snmp_helper.h** — заголовочный файл для данных SNMP MIB.
- **nxd_snmp.c** — исходный файл C агента SNMP для NetX Duo.
- **nx_md5.c** — алгоритмы хэширования MD5.
- **nx_sha.c** — алгоритмы хэширования SHA.
- **nx_des.c** — алгоритмы шифрования DES.
- **nxd_snmp.pdf** — руководство пользователя для агента SNMP для NetX Duo.
- **demo_netxduo_snmp.c** — простая демонстрация работы SNMP.
- **demo_netxduo_mib2.c** — простая демонстрация работы MIB2 (MIB содержит элементы с адресами IPv6).
- **demo_snmp_helper.h** — заголовочный файл, определяющий элементы MIB.

## <a name="netx-duo-snmp-agent-installation"></a>Установка SNMP-агента NetX Duo

Чтобы использовать SNMP NetX Duo, весь дистрибутив, упомянутый ранее, необходимо скопировать на уровень каталога, где установлен NetX Duo. Например, если NetX Duo установлен в каталоге " *\threadx\arm7\green*", файлы *nxd_snmp.h*, *nxd_snmp.c*, *nx_md5.c, nx_sha.c* и nx_ *des.c* следует скопировать в этот каталог.

## <a name="using-the-netx-duo-snmp-agent"></a>Использование SNMP-агента NetX Duo

Приложение должно содержать в проекте сборки файлы *nxd_snmp.c*, *nx_md5.c, nx_sha.c* и *nx_des.c*. Код приложения также должен включать *nxd_snmp.h* после включения *nx_api.h*, чтобы иметь возможность вызывать службы SNMP. Эти файлы должны быть скомпилированы так же, как и другие файлы приложения, а их объектная форма должна быть связана с библиотекой NetX Duo. Это все, что необходимо для использования SNMP в NetX Duo.

> [!NOTE]
> *Если в процессе сборки указан параметр **NX_SNMP_NO_SECURITY**, то файлы nx_md5.c, nx_sha.c и nx_des.c не нужны.*

> [!NOTE]
> Поскольку протокол SNMP NetX Duo использует службы UDP, перед использованием SNMP следует включить протокол UDP с помощью вызова *nx_udp_enable*.

## <a name="small-example-system"></a>Небольшой пример системы

Пример использования SNMP-агента NetX Duo приведен на рисунке 1.0 ниже. В этом примере файл заголовков SNMP *nxd_snmp.h* находится на строке 6. Файл заголовка, определяющий элементы базы данных MIB *demo_snmp_helper.h*, перенесен в строку 8. MIB определяется начиная со строки 32. Затем создается SNMP-агент с помощью "*tx_application_define*" в строке 129. Обратите внимание, что блок управления агентом SNMP "*my_agent*" был определен как глобальная переменная ранее в строке 18. Если включен протокол IPv6, адреса IPv6 регистрируются в экземпляре IP в строках 166–223. Агент SNMP запускается в строке 229. Определения обратного вызова объекта SNMP для запросов GET, GETNEXT и SET диспетчера SNMP, а также запросов на обновление имени пользователя и MIB обрабатываются начиная со строки 250. В этом примере проверка подлинности не выполняется.

> [!NOTE]
> *Приведенная ниже таблица MIB2 является просто примером. Приложение может использовать другой MIB и включать его в отдельные файлы, а также определять обработку GET, GETNEXT или SET в соответствии с требованиями приложения.*

```c
/* This is a small demo of the NetX SNMP Agent on the high-performance NetX TCP/IP  
   stack. This demo relies on ThreadX and NetX to show simple SNMP the SNMP
   GET/GETNEXT/SET requests on MIB-2 objects.  */

#include  "tx_api.h"
#include  "nx_api.h"
#include  "nxd_snmp.h"
#include  "demo_snmp_helper.h"

#define     DEMO_STACK_SIZE         4096
#define     AGENT_PRIMARY_ADDRESS   IP_ADDRESS(192, 2, 2, 66)

/* Define the ThreadX and NetX object control blocks...  */

TX_THREAD               thread_0;
NX_PACKET_POOL          pool_0;
NX_IP                   ip_0;
NX_SNMP_AGENT           my_agent;


/* Indicate if using IPv6 to communicate with SNMP servers. Note that
   IPv6 must be enabled in the NetX Duo library first. Further, IPv6
   and ICMPv6 services are enabled before starting the SNMP agent. */
#define USE_IPV6


/* Define authentication and privacy keys.  */

#ifdef AUTHENTICATION_REQUIRED
NX_SNMP_SECURITY_KEY    my_authentication_key;
#endif

#ifdef PRIVACY_REQUIRED
NX_SNMP_SECURITY_KEY    my_privacy_key;
#endif

/* Define an error counter variable. */
UINT error_counter = 0;

/* This binds a secondary interfaces to the primary IP network interface 
   if SNMP is required for required for that interface. */
/* #define  MULTI_HOMED_DEVICE */

/* Define function prototypes.  A generic ram driver is used in this demo.  However
   to properly run an SNMP agent demo, a real driver should be substituted. */

VOID    thread_agent_entry(ULONG thread_input);
VOID    _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);
UINT    mib2_get_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                            NX_SNMP_OBJECT_DATA *object_data);
UINT    mib2_getnext_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                            NX_SNMP_OBJECT_DATA *object_data);
UINT    mib2_set_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                            NX_SNMP_OBJECT_DATA *object_data);
UINT    mib2_username_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *username);
VOID    mib2_variable_update(NX_IP *ip_ptr, NX_SNMP_AGENT *agent_ptr);


UCHAR context_engine_id[] = {0x80, 0x00, 0x0d, 0xfe, 0x03, 0x00, 0x11, 0x23, 0x23, 
                             0x44, 0x55};
UINT  context_engine_size = 11;
UCHAR context_name[] = {0x69, 0x6e, 0x69, 0x74, 0x69, 0x61, 0x6c};
UINT  context_name_size = 7;

/* Define main entry point.  */

int main()
{

   /* Enter the ThreadX kernel.  */
   tx_kernel_enter();
}


/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

UCHAR   *pointer;
UINT    status;


   /* Setup the working pointer.  */
   pointer =  (UCHAR *) first_unused_memory;

   status = tx_thread_create(&thread_0, "agent thread", thread_agent_entry, 0,  
            pointer, DEMO_STACK_SIZE, 
            4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);
   if (status != NX_SUCCESS)
   {
      return;
   }

   pointer =  pointer + DEMO_STACK_SIZE;


   /* Initialize the NetX system.  */
   nx_system_initialize();

   /* Create packet pool.  */
   status = nx_packet_pool_create(&pool_0, "NetX Packet Pool 0", 2048, 
                                   pointer, 20000);

   if (status != NX_SUCCESS)
   {
      return;
   }
  
   pointer = pointer + 20000;
  
   /* Create an IP instance.  */
   status = nx_ip_create(&ip_0, "SNMP Agent IP Instance", AGENT_PRIMARY_ADDRESS, 
                        0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                        pointer, 4096, 1);

   if (status != NX_SUCCESS)
   {
      return;
   }
  
   pointer =  pointer + 4096;
  
   /* Enable ARP and supply ARP cache memory for IP Instance 0.  */
   nx_arp_enable(&ip_0, (void *) pointer, 1024);
   pointer = pointer + 1024;

   /* Enable UPD processing for IP instance.  */
   nx_udp_enable(&ip_0);
  
   /* Enable ICMP for ping.  */
   nx_icmp_enable(&ip_0);
  
   /* Create an SNMP agent instance.  */
   status = nx_snmp_agent_create(&my_agent, "SNMP Agent", &ip_0, pointer, 4096, 
                                 &pool_0, 
                                 mib2_username_processing, mib2_get_processing, 
                                 mib2_getnext_processing, 
                                 mib2_set_processing);


  
   if (status != NX_SUCCESS)
   {
      return;
   }
  
   pointer =  pointer + 4096;
  
   status = nx_snmp_agent_context_engine_set(&my_agent, context_engine_id, 
                                             context_engine_size);
  
   if (status != NX_SUCCESS)
   {
      error_counter++;
   }
  
   return;
}
  
VOID thread_agent_entry(ULONG thread_input)
{
  
#ifdef USE_IPV6
UINT        iface_index, address_index;
UINT        status;
NXD_ADDRESS agent_ipv6_address;
#endif
  
  
      /* Allow NetX time to get initialized. */
      tx_thread_sleep(100);
  
      /* If using IPv6, enable IPv6 and ICMPv6 services and get IPv6 addresses 
         registered with NetX Dou. */
  
#ifdef USE_IPV6
  
      /* Enable IPv6 on the IP instance. */
      status = nxd_ipv6_enable(&ip_0);
   
      /* Check for enable errors.  */
      if (status)
      {
  
         error_counter++;
         return;
      }
      /* Enable ICMPv6 on the IP instance. */
      status = nxd_icmp_enable(&ip_0);
  
      /* Check for enable errors.  */
      if (status)
      {
  
         error_counter++;
         return;
      }
  
      agent_ipv6_address.nxd_ip_address.v6[3] = 0x101;
      agent_ipv6_address.nxd_ip_address.v6[2] = 0x0;
      agent_ipv6_address.nxd_ip_address.v6[1] = 0x0000f101;
      agent_ipv6_address.nxd_ip_address.v6[0] = 0x20010db8;
      agent_ipv6_address.nxd_ip_version = NX_IP_VERSION_V6;
  
      /* Set the primary interface for our DNS IPv6 addresses. */
      iface_index = 0;
  
      /* This assumes we are using the primary network interface (index 0). */
      status = nxd_ipv6_address_set(&ip_0, iface_index, NX_NULL, 10, &address_index);
  
      /* Check for link local address set error.  */
      if (status) 
      {
  
         error_counter++;
         return;
      }
  
      /* Set the host global IP address. We are assuming a 64 
         bit prefix here but this can be any value (< 128). */
      status = nxd_ipv6_address_set(&ip_0, iface_index, &agent_ipv6_address, 64, 
                                    &address_index);
  
      /* Check for global address set error.  */
      if (status) 
      {
  
         error_counter++;
         return;
      }

      /* Wait while NetX Duo validates the link local and global address. */
      tx_thread_sleep(500);
#endif
  
#ifdef AUTHENTICATION_REQUIRED

      /* Create an authentication key.  */
      nx_snmp_agent_md5_key_create(&my_agent, "authpassword", &my_authentication_key);
  
      /* Use the authentication key.  */
      nx_snmp_agent_authenticate_key_use(&my_agent, &my_authentication_key);
#endif
  
#ifdef PRIVACY_REQUIRED
  
      /* Create a privacy key.  */
      nx_snmp_agent_md5_key_create(&my_agent, "privpassword", &my_privacy_key);
  
      /* Use the privacy key.  */
      nx_snmp_agent_privacy_key_use(&my_agent, &my_privacy_key);
#endif
  
      /* Start the SNMP instance.  */
      nx_snmp_agent_start(&my_agent);
  
}
  
/* Define the application's GET processing routine.  */
  
UINT    mib2_get_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                            NX_SNMP_OBJECT_DATA *object_data)
{
  
UINT    i;
UINT    status;
  
  
      printf("SNMP Manager GET Request For:  %s", object_requested);
  
      /* Loop through the sample MIB to see if we have information for the supplied 
         variable.  */
      i =  0;
      status =  NX_SNMP_ERROR;
      while (mib2_mib[i].object_name)
      {
  
         /* See if we have found the matching entry.  */
         status =  nx_snmp_object_compare(object_requested, mib2_mib[i].object_name);
  
         /* Was it found?  */
         if (status == NX_SUCCESS)
         {
  
            /* Yes it was found.  */
            break;
         }
  
         /* Move to the next index.  */
         i++;
      }
  
      /* Determine if a not found condition is present.  */
      if (status != NX_SUCCESS)
      {
  
         printf(" NO SUCH NAME!\n");
  
         /* The object was not found - return an error.  */
         return(NX_SNMP_ERROR_NOSUCHNAME);
      }
  
      /* Determine if the entry has a get function.  */
      if (mib2_mib[i].object_get_callback)
      {
  
         /* Yes, call the get function.  */
         status =  (mib2_mib[i].object_get_callback)(mib2_mib[i].object_value_ptr, 
                                                     object_data);
      }
      else
      {
  
         printf(" NO GET FUNCTION!");
  
         /* No get function, return no access.  */
         status =  NX_SNMP_ERROR_NOACCESS;
      }
  
      printf("\n");

      /* Return the status.  */
      return(status);
}
  
  
/* Define the application's GETNEXT processing routine.  */
  
UINT    mib2_getnext_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                                NX_SNMP_OBJECT_DATA *object_data)
{
  
UINT    i;
UINT    status;
  
  
   printf("SNMP Manager GETNEXT Request For:  %s", object_requested);
  
   /* Loop through the sample MIB to see if we have information for the supplied 
      variable.  */
      i =  0;
      status =  NX_SNMP_ERROR;
      while (mib2_mib[i].object_name)
      {
  
         /* See if we have found the next entry.  */
         status =  nx_snmp_object_compare(object_requested, mib2_mib[i].object_name);
  
         /* Is the next entry the mib greater?  */
         if (status == NX_SNMP_NEXT_ENTRY)
         {
  
            /* Yes it was found.  */
            break;
         }
  
         /* Move to the next index.  */
         i++;
      }
  
      /* Determine if a not found condition is present.  */
      if (status != NX_SNMP_NEXT_ENTRY)
      {
  
         printf(" NO SUCH NAME!\n");
  
         /* The object was not found - return an error.  */
         return(NX_SNMP_ERROR_NOSUCHNAME);
      }
  
  
      /* Copy the new name into the object.  */
      nx_snmp_object_copy(mib2_mib[i].object_name, object_requested);
  
      printf(" Next Name is: %s", object_requested);
  
      /* Determine if the entry has a get function.  */
      if (mib2_mib[i].object_get_callback)
      {
  
         /* Yes, call the get function.  */
         status =  (mib2_mib[i].object_get_callback)(mib2_mib[i].object_value_ptr, 
                                                     object_data);
  
         /* Determine if the object data indicates an end-of-mib condition.  */
         if (object_data -> nx_snmp_object_data_type == NX_SNMP_END_OF_MIB_VIEW)
         {
  
            /* Copy the name supplied in the mib table.  */
            nx_snmp_object_copy(mib2_mib[i].object_value_ptr, object_requested);
         }
      }
      else
      {
  
         printf(" NO GET FUNCTION!");
  
         /* No get function, return no access.  */
         status =  NX_SNMP_ERROR_NOACCESS;
      }
  
      printf("\n");

      /* Return the status.  */
      return(status);
}
  
  
/* Define the application's SET processing routine.  */
  
UINT    mib2_set_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                            NX_SNMP_OBJECT_DATA *object_data)
{
  
UINT    i;
UINT    status;
  
  
   printf("SNMP Manager SET Request For:  %s", object_requested);
  
   /* Loop through the sample MIB to see if we have information for the supplied variable.  */
      i =  0;
      status =  NX_SNMP_ERROR;
      while (mib2_mib[i].object_name)
      {
  
         /* See if we have found the matching entry.  */
         status =  nx_snmp_object_compare(object_requested, mib2_mib[i].object_name);
  
         /* Was it found?  */
         if (status == NX_SUCCESS)
         {
  
            /* Yes it was found.  */
            break;
         }
  
         /* Move to the next index.  */
         i++;
      }
  
      /* Determine if a not found condition is present.  */
      if (status != NX_SUCCESS)
      {
  
         printf(" NO SUCH NAME!\n");
  
         /* The object was not found - return an error.  */
         return(NX_SNMP_ERROR_NOSUCHNAME);
      }
  
  
      /* Determine if the entry has a set function.  */
      if (mib2_mib[i].object_set_callback)
      {
  
         /* Yes, call the set function.  */
         status =  (mib2_mib[i].object_set_callback)(mib2_mib[i].object_value_ptr, 
                                                     object_data);
      }
      else
      {
  
         printf(" NO SET FUNCTION!");
  
         /* No get function, return no access.  */
         status =  NX_SNMP_ERROR_NOACCESS;
      }
  
      printf("\n");

      /* Return the status.  */
      return(status);
}
  
  
/* Define the application's authentication routine.  */
  
UINT  mib2_username_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *username)
{
  
      printf("Username is:  %s\n", username);
  
      /* Update MIB-2 objects. In this example, it is only the SNMP objects.  */
      mib2_variable_update(&ip_0, &my_agent);
  
      /* No authentication is done, just return success!  */
      return(NX_SUCCESS);
}
  
  
/* Define the application's update routine.  */ 
  
VOID  mib2_variable_update(NX_IP *ip_ptr, NX_SNMP_AGENT *agent_ptr)
{
  
      /* Update the snmp parameters.  */
      snmpInPkts =                agent_ptr -> nx_snmp_agent_packets_received;
      snmpOutPkts =               agent_ptr -> nx_snmp_agent_packets_sent;
      snmpInBadVersions =         agent_ptr -> nx_snmp_agent_invalid_version;
      snmpInBadCommunityNames =   agent_ptr -> nx_snmp_agent_authentication_errors;
      snmpInBadCommunityUsers =   agent_ptr -> nx_snmp_agent_username_errors; 
      snmpInASNParseErrs =        agent_ptr -> nx_snmp_agent_internal_errors;
      snmpInTotalReqVars =        agent_ptr -> nx_snmp_agent_total_get_variables;
      snmpInTotalSetVars =        agent_ptr -> nx_snmp_agent_total_set_variables;
      snmpInGetRequests =         agent_ptr -> nx_snmp_agent_get_requests;
      snmpInGetNexts =            agent_ptr -> nx_snmp_agent_getnext_requests;
      snmpInSetRequests =         agent_ptr -> nx_snmp_agent_set_requests;
      snmpOutTooBigs =            agent_ptr -> nx_snmp_agent_too_big_errors;
      snmpOutNoSuchNames =        agent_ptr -> nx_snmp_agent_no_such_name_errors;
      snmpOutBadValues =          agent_ptr -> nx_snmp_agent_bad_value_errors;
      snmpOutGenErrs =            agent_ptr -> nx_snmp_agent_general_errors;
      snmpOutTraps =              agent_ptr -> nx_snmp_agent_traps_sent;
}   
```
Рисунок 1.0. Пример использования SNMP-агента с NetX Duo

## <a name="configuration-options"></a>Параметры конфигурации

Существует ряд параметров конфигурации для использования SNMP с NetX Duo. Ниже приведен список всех параметров с описанием.  
  
| Определение                     | Значение                                                                                                                                                                                                                                                                        |
|----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **NX_SNMP_AGENT_PRIORITY**     | Приоритет потока агента SNMP. По умолчанию указано значение 16 для задания приоритета 16.                                                                                                                                                                         |
| **NX_SNMP_TYPE_OF_SERVICE**    | Тип службы, необходимый для ответов SNMP UDP. По умолчанию это значение определено как NX_IP_NORMAL для указания обычной службы IP-пакетов. Это определение можно задать в приложении перед включением *nxd_snmp.h*.                                                       |
| **NX_SNMP_FRAGMENT_OPTION**    | Включение фрагментов для запросов SNMP UDP. По умолчанию имеет значение NX_DONT_FRAGMENT, которое отключает фрагментирование UDP в SNMP. Это определение можно задать в приложении перед включением *nxd_snmp.h*.                                                                                 |
| **NX_SNMP_TIME_TO_LIVE**       | Указывает срок жизни до истечения срока действия. Значение по умолчанию равно 0x80, но может быть переопределено перед включением *nxd_snmp.h*.                                                                                                                                         |
| **NX_SNMP_AGENT_TIMEOUT**      | Указывает число тактов ThreadX, на которое внутренние службы приостановят работу. Значение по умолчанию равно 100, но может быть переопределено перед включением *nxd_snmp.h.*                                                                                                         |
| **NX_SNMP_MAX_OCTET_STRING**   | Задает максимальное число байтов, разрешенное в строке октета в агенте SNMP. Значение по умолчанию равно 255, но может быть переопределено перед включением *nxd_snmp.h.*                                                                                                    |
| **NX_SNMP_MAX_CONTEXT_STRING** | Задает максимальное число байтов для строки обработчика контекста в агенте SNMP. Значение по умолчанию равно 32, но может быть переопределено перед включением *nxd_snmp.h.*                                                                                                    |
| **NX_SNMP_MAX_USER_NAME**      | Указывает максимальное число байтов в имени пользователя (включая строки сообщества). Значение по умолчанию равно 64, но может быть переопределено перед включением *nxd_snmp.h.*                                                                                                      |
| **NX_SNMP_MAX_SECURITY_KEY**   | Указывает число байтов, разрешенное в строке ключа безопасности. Значение по умолчанию равно 64, но может быть переопределено перед включением *nxd_snmp.h.*                                                                                                                          |
| **NX_SNMP_PACKET_SIZE**        | Задает минимальный размер пакетов в пуле, указанный при создании агента SNMP. Минимальный размер нужно указать, чтобы обеспечить включение всех полезных данных SNMP в один пакет. Значение по умолчанию равно 560, но может быть переопределено перед включением *nxd_snmp.h.* |
| **NX_SNMP_AGENT_PORT**         | Задает порт UDP для отправки запросов диспетчера SNMP. По умолчанию используется порт UDP 161, но может быть переопределен перед включением *nxd_snmp.h.*                                                                                                                             |
| **NX_SNMP_MANAGER_TRAP_PORT**  | Задает порт UDP для отправки запросов ловушек агента SNMP. По умолчанию используется порт UDP 162, но может быть переопределен перед включением *nxd_snmp.h.*                                                                                                                           |
| **NX_SNMP_MAX_TRAP_NAME**      | Указывает размер массива, в котором будет храниться имя пользователя, отправленное с помощью сообщений ловушек. Значение по умолчанию — 64.                                                                                                                                                                         |
| **NX_SNMP_MAX_TRAP_KEY**       | Указывает размер ключей проверки подлинности и конфиденциальных ключей для сообщений ловушек. Значение по умолчанию — 64.                                                                                                                                                                          |
| **NX_SNMP_TIME_INTERVAL**      | Определяет интервал ожидания в тактах таймера, выполняемых задачей потока SNMP между обработкой полученных пакетов SNMP. Значение по умолчанию — 100. В течение этого интервала ожидания ведущее приложение имеет доступ к службам API SNMP.                                           |
| **NX_SNMP_DISABLE_V1**         | Указание параметра приведет к удалению всей обработки SNMP версии 1 в файле *nxd_snmp. c.* По умолчанию параметр отключен.                                                                                                                                                                         |
| **NX_SNMP_DISABLE_V2**         | Указание параметра приведет к удалению всей обработки SNMP версии 2 в файле *nxd_snmp. c.* По умолчанию параметр отключен.                                                                                                                                                                         |
| **NX_SNMP_DISABLE_V3**         | Указание параметра приведет к удалению всей обработки SNMP версии 3 в файле *nxd_snmp.c.* По умолчанию параметр отключен.                                                                                                                                                                                 |