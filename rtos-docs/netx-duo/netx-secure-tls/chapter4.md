---
title: Глава 4. Описание служб NetX Secure для ОСРВ Azure
description: В этой главе приведено описание всех служб NetX Secure, перечисленных ниже в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 89761ec3438b1b16c1a603764bf7d4e1eac1b4ea
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815352"
---
# <a name="chapter-4---description-of-azure-rtos-netx-secure-services"></a>Глава 4. Описание служб NetX Secure для ОСРВ Azure

В этой главе приведено описание всех служб NetX Secure для ОСРВ Azure, перечисленных ниже в алфавитном порядке.

В разделе "Возвращаемые значения" в приведенных ниже описаниях API значения, выделенные **полужирным шрифтом**, не затрагиваются макросом **NX_SECURE_DISABLE_ERROR_CHECKING**, который используется для отключения проверки API на предмет ошибок. Значения, не выделенные полужирным шрифтом, полностью отключены.

- [nx_secure_crypto_table_self_test](#nx_secure_crypto_table_self_test)
  - Выполнение самостоятельного тестирования для методов шифрования
- [nx_secure_module_hash_compute](#nx_secure_module_hash_compute)
  - Вычисление хэш-значения с помощью пользовательской хэш-функции
- [nx_secure_tls_active_certificate_set](#nx_secure_tls_active_certificate_set)
  - Установка активного сертификата удостоверения для сеанса NetX Secure TLS
- [nx_secure_tls_client_psk_set](#nx_secure_tls_client_psk_set)
  - Установка общего ключа для сеанса клиента NetX Secure TLS
- [nx_secure_tls_initialize](#nx_secure_tls_initialize)
  - Инициализация модуля NetX Secure TLS
- [nx_secure_tls_local_certificate_add](#nx_secure_tls_local_certificate_add)
  - Добавление локального сертификата в сеанс NetX Secure TLS
- [nx_secure_tls_local_certificate_find](#nx_secure_tls_local_certificate_find)
  - Поиск локального сертификата в сеансе NetX Secure TLS по общему имени
- [nx_secure_tls_local_certificate_remove](#nx_secure_tls_local_certificate_remove)
  - Удалить локальный сертификат из сеанса NetX Secure TLS
- [nx_secure_tls_metadata_size_calculate](#nx_secure_tls_metadata_size_calculate)
  - Вычисление размера криптографических метаданных для сеанса NetX Secure TLS
- [nx_secure_tls_packet_allocate](#nx_secure_tls_packet_allocate)
  - Выделение пакета для сеанса NetX Secure TLS
- [nx_secure_tls_psk_add](#nx_secure_tls_psk_add)
  - Добавление общего ключа в сеанс TLS в NetX Secure
- [nx_secure_tls_remote_certificate_allocate](#nx_secure_tls_remote_certificate_allocate)
  - Выделение пространства для сертификата, предоставленного удаленным узлом TLS
- [nx_secure_tls_remote_certificate_buffer_allocate](#nx_secure_tls_remote_certificate_buffer_allocate)
  - Выделение пространства для всех сертификатов, предоставленных удаленным узлом TLS
- [nx_secure_tls_remote_certificate_free_all](#nx_secure_tls_remote_certificate_free_all)
  - Освобождение места, выделенного для входящих сертификатов
- [nx_secure_tls_server_certificate_add](#nx_secure_tls_server_certificate_add)
  - Добавление сертификата специально для серверов TLS с помощью числового идентификатора
- [nx_secure_tls_server_certificate_find](#nx_secure_tls_server_certificate_find)
  - Поиск сертификата по числовому идентификатору
- [nx_secure_tls_server_certificate_remove](#nx_secure_tls_server_certificate_remove)
  - Удаление сертификата локального сервера с помощью числового идентификатора
- [nx_secure_tls_session_certificate_callback_set](#nx_secure_tls_session_certificate_callback_set)
  - Настройка обратного вызова для протокола TLS, который будет использоваться для дополнительной проверки сертификата
- [nx_secure_tls_session_client_callback_set](#nx_secure_tls_session_client_callback_set)
  - Настройка обратного вызова для протокола TLS для вызова в начале подтверждения клиента TLS
- [nx_secure_tls_session_x509_client_verify_configure](#nx_secure_tls_session_x509_client_verify_configure)
  - Включение проверки X.509 клиента и выделение места для сертификатов клиента
- [nx_secure_tls_session_client_verify_disable](#nx_secure_tls_session_client_verify_disable)
  - Отключение проверки подлинности сертификата клиента для сеанса NetX Secure TLS
- [nx_secure_tls_session_client_verify_enable](#nx_secure_tls_session_client_verify_enable)
  - Отключение проверки подлинности сертификата клиента для сеанса NetX Secure TLS
- [nx_secure_tls_session_create](#nx_secure_tls_session_create)
  - Создание сеанса NetX Secure TLS для обеспечения безопасности подключений
- [nx_secure_tls_session_delete](#nx_secure_tls_session_delete)
  - Удаление сеанса NetX Secure TLS
- [nx_secure_tls_session_end](#nx_secure_tls_session_end)
  - Завершение активного сеанса NetX Secure TLS
- [nx_secure_tls_session_packet_buffer_set](#nx_secure_tls_session_packet_buffer_set)
  - Установка буфера повторной сборки пакетов для сеанса NetX Secure TLS
- [nx_secure_tls_session_protocol_version_override](#nx_secure_tls_session_protocol_version_override)
  - Переопределение версии протокола TLS по умолчанию для сеанса NetX Secure TLS
- [nx_secure_tls_session_receive](#nx_secure_tls_session_receive)
  - Получение данных из сеанса NetX Secure TLS
- [nx_secure_tls_session_renegotiate_callback_set](#nx_secure_tls_session_renegotiate_callback_set)
  - Назначение обратного вызова, который будет выполняться в начале повторного согласования сеанса
- [nx_secure_tls_session_renegotiate](#nx_secure_tls_session_renegotiate)
  - Инициация подтверждения повторного согласования сеанса с удаленным узлом
- [nx_secure_tls_session_reset](#nx_secure_tls_session_reset)
  - Очистка и сброс сеанса NetX Secure TLS
- [nx_secure_tls_session_send](#nx_secure_tls_session_send)
  - Отправка данных через сеанс NetX Secure TLS
- [nx_secure_tls_session_server_callback_set](#nx_secure_tls_session_server_callback_set)
  - Настройка обратного вызова для протокола TLS для вызова в начале подтверждения сервера TLS
- [nx_secure_tls_session_sni_extension_parse](#nx_secure_tls_session_sni_extension_parse)
  - Анализ расширения указания имени сервера (SNI), полученного от клиента TLS
- [nx_secure_tls_session_sni_extension_set](#nx_secure_tls_session_sni_extension_set)
  - Установка DNS-имени расширения указания имени сервера (SNI) для отправки на удаленный сервер
- [nx_secure_tls_session_start](#nx_secure_tls_session_start)
  - Запуск сеанса NetX Secure TLS
- [nx_secure_tls_session_time_function_set](#nx_secure_tls_session_time_function_set)
  - Назначение функции метки времени в сеансе NetX Secure TLS
- [nx_secure_tls_trusted_certificate_add](#nx_secure_tls_trusted_certificate_add)
  - Добавление доверенного сертификата в сеансе NetX Secure TLS
- [nx_secure_tls_trusted_certificate_remove](#nx_secure_tls_trusted_certificate_remove)
  - Удаление доверенного сертификата из сеанса NetX Secure TLS
- [nx_secure_x509_certificate_initialize](#nx_secure_x509_certificate_initialize)
  - Инициализация сертификата X.509 для NetX Secure TLS
- [nx_secure_x509_common_name_dns_check](#nx_secure_x509_common_name_dns_check)
  - Проверка DNS-имени на соответствие сертификату X.509
- [nx_secure_x509_crl_revocation_check](#nx_secure_x509_crl_revocation_check)
  - Проверка сертификата X.509 на соответствие заданному списку отзыва сертификатов
- [nx_secure_x509_dns_name_initialize](#nx_secure_x509_dns_name_initialize)
  - Инициализация структуры DNS-имени X.509
- [nx_secure_x509_extended_key_usage_extension_parse](#nx_secure_x509_extended_key_usage_extension_parse)
  - Поиск и анализ расширения расширенного использования ключа X.509 в сертификате X.509
- [nx_secure_x509_extension_find](#nx_secure_x509_extension_find)
  - Поиск и возврат расширения X.509 в сертификате X.509
- [nx_secure_x509_key_usage_extension_parse](#nx_secure_x509_key_usage_extension_parse)
  - Поиск и анализ расширения использования ключа X.509 в сертификате X.509

## <a name="nx_secure_crypto_table_self_test"></a>nx_secure_crypto_table_self_test

Выполнение самостоятельного тестирования для методов шифрования

### <a name="prototype"></a>Прототип

```C
UINT nx_secure_crypto_table_self_test(
                                  const NX_SECURE_TLS_CRYPTO *crypto_table,
                                  VOID *metadata, UINT metadata_size);
```

### <a name="description"></a>Описание

Эта служба выполняет самостоятельное тестирование методов шифрования для проверки. Самостоятельное тестирование доступно только в том случае, если библиотека NetX Secure создана с определенным символом NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK.

Для каждого поддерживаемого метода шифрования самостоятельное тестирование предоставляет предварительно определенные входные данные и проверяет их на соответствие предварительно определенному ожидаемому значению.

Самостоятельное тестирование шифрования NetX Secure поддерживает следующие алгоритмы и размеры ключей:

- DES: шифрование и расшифровка;
- Triple DES (3DES): шифрование и расшифровка;
- AES: 128-, 192-, 256-битный размер ключа, шифрование и расшифровка в режиме CBC и режиме счетчика;
- HMAC-MD5: проверка подлинности и вычисление хэша;
- HMAC-SHA: SHA1-96, SHA1-160, SHA2-256, SHA2-384, SHA2-512, проверка подлинности и вычисление хэша;
- MD5: проверка подлинности;
- псевдослучайная функция (PRF): PRF_HMAC_SHA1 и PRF_HMAC_SHA2-256;
- RSA: 1024-, 2048-, 4096-битная операция модуля питания RSA;
- SHA: проверка подлинности SHA1 (96- и 160-битная), SHA2 (256-, 384-, 512-битная).

Эта функция имеет встроенные векторы для алгоритмов шифрования, перечисленных выше. Однако она проверяет только алгоритмы, перечисленные в параметре *cipher_table*, переданном в эту функцию. Например, для сеанса TLS используется только набор шифров TLS_RSA_WITH_AES_128_CBC_SHA. Эта функция выполняет самостоятельное тестирование в RSA (1024-, 2048-, 4096-битные), AES-CBC (128-битный) и SHA1.

### <a name="parameters"></a>Параметры

- **crypto_table** — указатель на таблицу шифрования, используемую сеансом TLS. Это тот же параметр crypto_table, который передается в вызов **_nx_secure_tls_session_create()_**.
- **metadata** — указатель на пространство для области метаданных шифрования. .
- **metadata_size** — размер буфера метаданных.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SECURE_TLS_SUCCESS** (0x00) — предоставленные методы шифрования успешно протестированы.
- **NX_PTR_ERROR** (0x07) — недопустимая структура метода шифрования.
- **NX_NOT_SUCCESSFUL** (0x43) — сбой самостоятельного тестирования шифрования.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Пример

```C
/* crypto_tls_ciphers is the cipher table for the TLS session. */
/* metadata_buffer is the memory area used by the cipher functions. */

/* The following function verifies the supplied ciphersuties using the built-in
   self test. */

if (nx_secure_crypto_table_self_test(&crypto_tls_ciphers, metadata_buffer,
    sizeof(metadata_buffer)))
{
    printf("Crypto self test failed!\r\n");
    exit(0);
}
else
{
    printf("Crypto self test succeed!\r\n");
}

/* Now the ciphersuites are successfully test, it can be used in
   nx_secure_tls_session_create() */
```

### <a name="see-also"></a>См. также:

- nx_secure_tls_session_create

## <a name="nx_secure_module_hash_compute"></a>nx_secure_module_hash_compute

Вычисление хэш-значения с помощью пользовательской хэш-функции

### <a name="prototype"></a>Прототип

```C
UINT nx_secure_module_hash_compute(
                      NX_CRYPTO_METHOD *hamc_ptr,
                      UINT start_address, UINT end_address,
                      UCHAR *key, UINT key_length,
                      VOID *metadata, UINT metadata_size,
                      UCHAR *output_buffer, UINT output_buffer_size,
                      UINT *actual_size);
```

### <a name="description"></a>Описание

Эта функция вычисляет хэш-значение потока данных в указанной области памяти, используя указанный метод шифрования HMAC и строку ключа. Функция вычисления хэша модуля доступна, только если библиотека NetX Secure создана со следующим определяемым символом: NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK

### <a name="parameters"></a>Параметры

- **hmac_ptr** — указатель на метод шифрования HMAC, используемый для вычисления хэш-значения.
- **start_address** — начальный адрес буфера данных.
- **end_address** — конечный адрес буфера данных. Обратите внимание, что вычисление хэша не распространяется на данные, расположенные по этому адресу end_address.
- **key** — строка ключа, используемая в вычислении HMAC.
- **key_length** — размер строки ключа в байтах.
- **metadata** — указатель на пространство, используемое алгоритмом HMAC.
- **metadata_size** — размер буфера метаданных.
- **output_buffer** — место в памяти, где хранятся выходные данные хэша.
- **output_buffer_size** — доступное место в буфере вывода в байтах.
- **actual_size** — параметр, возвращаемый функцией, которая указывает фактическое число байтов, записываемых в параметр output_buffer.

### <a name="return-values"></a>Возвращаемые значения

- **0** — вычисление хэш-значения успешно выполнено.
- **1** — не удалось выполнить вычисление хэша.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Пример

```C
/* Define the HMAC SHA256 method */
NX_CRYPTO_METHOD hmac_sha256 =
{
    NX_CRYPTO_AUTHENTICATION_HMAC_SHA2_256,    /* HMAC SHA256 algorithm  */
    0,                                         /* Key size, not used     */
    0,                                         /* IV size, not used      */
    NX_CRYPTO_HMAC_SHA256_ICV_FULL_LEN_IN_BITS,/* Transmitted ICV size   */
    NX_CRYPTO_SHA2_BLOCK_SIZE_IN_BYTES,        /* Block size in bytes    */
    sizeof(NX_CRYPTO_SHA256_HMAC),             /* Metadata size in bytes */
    _nx_crypto_method_hmac_sha256_init,        /* HMAC SHA256 init       */
    _nx_crypto_method_hmac_sha256_cleanup,     /* HMAC SHA256 cleanup    */
    _nx_crypto_method_hmac_sha256_operation    /* HMAC SHA256 operation  */
};

/* Define the hash key being used. */
const CHAR hash_key = “my hash key”;

/* Define starting address. */
UINT starting_address = 0x10000;

/* Define the ending address.
   Note that the hash computation covers the memory location
   before the ending address. */
UINT ending_address = 0x11000;

/* Declare the output buffer. */
#define OUTPUT_BUFFER_SIZE
UCHAR output_buffer[OUTPUT_BUFFER_SIZE];

UINT actual_size;

/* Declare 1K bytes of metadata buffer area. */
UCHAR metadata_buffer[1024];

/* Compute the hash value of the data between 0x10000 – 0x10FFF */
nx_secure_module_hash_compute(&hmac_sha256,
                              starting_address, ending_address,
                              hash_key, strlen(hash_key),
                              metadata_buffer, sizeof(metadata_buffer),
                              output_buffer, OUTPUT_BUFFER_SIZE, &actual_size);

/* If this function returns “0”, the hash value has been computed and is stored
   in output_buffer. */
```

### <a name="see-also"></a>См. также:

- nx_secure_crypto_method_self_test

## <a name="nx_secure_tls_active_certificate_set"></a>nx_secure_tls_active_certificate_set

Установка активного сертификата удостоверения для сеанса NetX Secure TLS

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_active_certificate_set(
                   NX_SECURE_TLS_SESSION *tls_session,
                   NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a>Описание

Эта служба должна вызываться из обратного вызова сеанса (см. nx_secure_tls_session_client_callback_set и nx_secure_tls_session_server_callback_set). При вызове с ранее инициализированной структурой NX_SECURE_X509_CERT этот сертификат будет использоваться вместо сертификата удостоверения по умолчанию. В большинстве случаев сертификат необходимо добавить в локальное хранилище (см. nx_secure_tls_local_certificate_add), иначе подтверждение TLS может завершиться ошибкой.

Эта служба предназначена для того, чтобы протокол TLS поддерживал несколько сертификатов удостоверений. Это полезно для сервера TLS, который обслуживает несколько сетевых адресов, чтобы сервер мог выбрать соответствующий сертификат для удаленного клиента в зависимости от точки входа клиента. В клиенте TLS эту подпрограмму можно использовать для изменения сертификата, отправленного на удаленный сервер во время выполнения, после идентификации сервера в подтверждении TLS (это происходит реже, чем в случае использования сервера TLS).

Если несколько сертификатов могут совместно использовать одно и то же различающееся имя X.509, их необходимо добавить с использованием параметра nx_secure_tls_server_certificate_add, который представляет числовой идентификатор, отделенный от сертификата.

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на экземпляр сеанса TLS, переданный в обратный вызов сеанса.
- **certificate** — указатель на инициализированный сертификат X.509, который будет использоваться в текущем сеансе.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сертификат успешно назначен сеансу.
- **NX_PTR_ERROR** (0x07) — недопустимый сеанс TLS или указатель на сертификат.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
#define TLS_SNI_SERVER_NAME “www.example.com”
#define TLS_DEFAULT_SERVER_CERT_ID 2
#define TLS_EXAMPLE_CERT_ID 3


/* Callback for ClientHello extensions processing. */
static ULONG tls_server_callback(NX_SECURE_TLS_SESSION *tls_session,
                                 NX_SECURE_TLS_HELLO_EXTENSION *extensions,
                                 UINT num_extensions)
{
NX_SECURE_X509_DNS_NAME dns_name;
INT compare_value;
UINT status;
NX_SECURE_X509_CERT *cert_ptr;

    /* Grab a pointer to our default certificate in case the SNI extension is not
       available or the specified server name is unknown. */
    nx_secure_tls_server_certificate_find(tls_session, &cert_ptr,
                                     TLS_DEFAULT_SERVER_CERT_ID);


    /* Process Server Name Indication extension. */
    status = _nx_secure_tls_session_sni_extension_parse(tls_session, extensions,
                                                    num_extensions, &dns_name);

    /* If no extension found, that is OK. Use default certificate. */
    if(status == NX_SUCCESS)
    {
          /* SNI extension found, select an active certificate based on the server
             name. */

          /* Make sure our SNI name matches. */
          compare_value = memcmp(dns_name.nx_secure_x509_dns_name,
                                TLS_SNI_SERVER_NAME, strlen(TLS_SNI_SERVER_NAME));

          if(compare_value == 0 && dns_name.nx_secure_x509_dns_name_length !=
             strlen(TLS_SNI_SERVER_NAME))
          {
             /* Found a match, find the certificate we want to use. */
             _nx_secure_tls_server_certificate_find(tls_session, &cert_ptr,
                                                      TLS_EXAMPLE_CERT_ID);
          }
          else
          {
             /* No matching server name found. The application may choose to simply
                provide the default certificate (and probably resulting in an error
                in the remote client) or returning an error here to end the
                handshake. A user-defined non-zero error code will be sufficient –
                the error code will abort the TLS handshake and be returned to the
                caller that started the server. */
                return(0x500);
          }
      }
      else
      {
      }
      /* Set the certificate we want to use. */
      nx_secure_tls_active_certificate_set(tls_session, cert_ptr);

      /* Return success to continue TLS handshake. */
      return(NX_SUCCESS);
}

/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_TLS_SESSION server_tls_session;

/* Application where TLS session is started. */
void main()
{
    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_tls_session_create(&server_tls_session,
                                           &nx_crypto_tls_ciphers,
                                           server_crypto_metadata,
                                           sizeof(server_crypto_metadata));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_tls_session_create: 0x%x\n", status);
    }

    /* Setup our packet reassembly buffer. See
       nx_secure_tls_session_packet_buffer_set for more information. */
    nx_secure_tls_session_packet_buffer_set(&server_tls_session,
                                      server_packet_buffer,
                                      sizeof(server_packet_buffer));


    /* Set callback for server TLS extension handling. */
    _nx_secure_tls_session_server_callback_set(&server_tls_session,
                                              tls_server_callback);

    /* Initialize our certificates – certificate data defined elsewhere. See
       section “Importing X.509 Certificates into NetX Secure” for more
       information. */
    nx_secure_x509_certificate_initialize(&default_certificate,
                                      default_cert_der,
                                      default _cert_der_len, NX_NULL, 0,
                                      default_cert_key_der,
                                      default_cert_key_der_len,
                                      NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_tls_server_certificate_add(&server_tls_session,
                                         &default_certificate,
                                         TLS_DEFAULT_SERVER_CERT_ID);

    /* Alternative identity certificate, needs to have a private key! */
    nx_secure_x509_certificate_initialize(&example_certificate,
                                      example_cert_der,
                                      example cert_der_len, NX_NULL, 0,
                                      example_cert_key_der,
                                      example_cert_key_der_len,
                                      NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_tls_server_certificate_add(&server_tls_session,
                                         &example_certificate,
                                         TLS_EXAMPLE_CERT_ID);

    /* Now we can start the TLS session as normal. */
       …
}
```

### <a name="see-also"></a>См. также:

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_session_client_callback_set
- nx_secure_tls_session_server_callback_set
- nx_secure_tls_server_certificate_add
- nx_secure_tls_server_certificate_find
- nx_secure_tls_server_certificate_remove

## <a name="nx_secure_tls_client_psk_set"></a>nx_secure_tls_client_psk_set

Установка общего ключа для сеанса клиента NetX Secure TLS

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_client_psk_set(NX_SECURE_TLS_SESSION *session_ptr,
                              UCHAR *pre_shared_key, UINT psk_length,
                              UCHAR *psk_identity, UINT identity_length,
                              UCHAR *hint, UINT hint_length);
```

### <a name="description"></a>Описание

Эта служба добавляет общий ключ (PSK), строку идентификатора и указание удостоверения в блок управления сеансом TLS и задает использование этого PSK в последующих подключениях клиентов TLS. Если включены и используются наборы шифров PSK, то вместо цифрового сертификата используется PSK.

В этом случае PSK связывается с конкретным удаленным сервером TLS, с которым клиент TLS будет обмениваться данными. PSK, заданный через этот API, будет предоставляться узлу удаленного сервера TLS во время следующего подтверждения TLS.

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.
- **pre_shared_key** — фактическое значение PSK.
- **psk_length** — длина значения PSK.
- **psk_identity** — строка, используемая для идентификации этого значения PSK.
- **identity_length** — длина удостоверения PSK.
- **hint** — строка, используемая для указания группы ключей PSK, из которой необходимо выбрать ключ на сервере TLS.
- **hint_length** — длина строки указания.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное добавление PSK.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) — невозможно добавить еще один PSK.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_client_psk_set(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a>См. также:

- nx_secure_tls_psk_add
- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_add

## <a name="nx_secure_tls_initialize"></a>nx_secure_tls_initialize

Инициализация модуля NetX Secure TLS

### <a name="prototype"></a>Прототип

```C
VOID nx_secure_tls_initialize(VOID);
```

### <a name="description"></a>Описание

Эта служба инициализирует модуль NetX Secure TLS. Его необходимо вызвать до доступа к другим службам NetX Secure.

### <a name="parameters"></a>Параметры

None

### <a name="return-values"></a>Возвращаемые значения

Нет

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Пример

```C
/* Initializes the TLS module. */
Nx_secure_tls_initialize();
```

### <a name="see-also"></a>См. также:

- nx_secure_tls_session_create

## <a name="nx_secure_tls_local_certificate_add"></a>nx_secure_tls_local_certificate_add

Добавление локального сертификата в сеанс NetX Secure TLS

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_local_certificate_add(
              NX_SECURE_TLS_SESSION *session_ptr,
              NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a>Описание

Эта служба добавляет инициализированный экземпляр структуры NX_SECURE_X509_CERT в локальное хранилище сеанса TLS. Этот сертификат может использоваться стеком TLS для идентификации устройства во время подтверждения TLS (если оно было помечено как сертификат удостоверения во время инициализации структуры сертификата с помощью nx_secure_x509_certificate_initialize) или в качестве издателя в составе цепочки сертификатов, предоставленной удаленному узлу во время подтверждения TLS.

Если требуется несколько локальных сертификатов с одинаковым общим именем, их можно добавить с помощью службы *nx_secure_tls_server_certificate_add* (см. предупреждение ниже).

Сертификат **требуется** для режима сервера TLS.

Для режима клиента TLS сертификат *необязателен*.

> [!IMPORTANT]
> *Этот API не следует использовать с тем же сеансом TLS при использовании nx_secure_tls_server_certificate_add. API сертификата сервера использует уникальный числовой идентификатор для каждого сертификата, а nx_secure_tls_local_certificate_add использует индексы на основе общего имени X.509. Службы локальных сертификатов предоставляют удобную альтернативу числовому идентификатору для приложений, использующих только один сертификат удостоверения — общее имя. Приложению не нужно отслеживать числовые идентификаторы*.

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.
- **certificate_ptr** — указатель на инициализированный экземпляр сертификата TLS.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное добавление сертификата.
- **NX_INVALID_PARAMETERS** (0x4D) — выполнена попытка добавления недопустимого сертификата или дубликата сертификата.
- **NX_PTR_ERROR** (0x07) — недопустимый сеанс TLS или указатель на сертификат.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Initialize certificate structure. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */
```

### <a name="see-also"></a>См. также:

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_remove
- nx_secure_tls_local_certificate_find

## <a name="nx_secure_tls_local_certificate_find"></a>nx_secure_tls_local_certificate_find

Поиск локального сертификата в сеансе NetX Secure TLS по общему имени

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_local_certificate_find(NX_SECURE_TLS_SESSION
                        *session_ptr, NX_SECURE_X509_CERT
                        **certificate, UCHAR *common_name, UINT
                        name_length);
```

### <a name="description"></a>Описание

Эта служба находит сертификат в хранилище сертификатов локального устройства в сеансе TLS и возвращает указатель на структуру NX_SECURE_X509_CERT в хранилище. Параметр common_name и его длина (name_length) используются для обнаружения сертификата в хранилище путем сопоставления поля общего имени субъекта X.509 сертификата.

При наличии нескольких сертификатов с одним общим именем будет возвращен только первый из них. Используйте *nx_secure_tls_server_certificate_find*.

> [!IMPORTANT]
> *Этот API не следует использовать с тем же сеансом TLS при использовании nx_secure_tls_server_certificate_add. API сертификата сервера использует уникальный числовой идентификатор для каждого сертификата, а nx_secure_tls_local_certificate_add использует индексы на основе общего имени X.509. Службы локальных сертификатов предоставляют удобную альтернативу числовому идентификатору для приложений, использующих только один сертификат удостоверения — общее имя. Приложению не нужно отслеживать числовые идентификаторы*.

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.
- **certificate** — возврат указателя на сопоставленный сертификат.
- **common_name** — строка общего имени для сопоставления (DNS-имя).
- **name_length** — длина строковых данных параметра common_name.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сертификат найден, а указатель возвращен в параметре certificate.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) — сертификат с указанным общим именем не найден.
- **NX_PTR_ERROR** (0x07) — недопустимый сеанс TLS, указатель сертификата или строка общего имени.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
NX_SECURE_X509_CERT *certificate_ptr;

/* Initialize certificate structure. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */

status = nx_secure_tls_local_certificate_find(&tls_session, &certificate_ptr,
                                      “common name”, strlen(“common name”));

/* If status is NX_SUCCESS the variable “certificate_ptr” points to a certificate
   structure containing a certificate with the Common Name “common name”. */
```

### <a name="see-also"></a>См. также:

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_remove
- nx_secure_tls_local_certificate_add

## <a name="nx_secure_tls_local_certificate_remove"></a>nx_secure_tls_local_certificate_remove

Удалить локальный сертификат из сеанса NetX Secure TLS

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_local_certificate_remove(NX_SECURE_TLS_SESSION
                  *session_ptr, UCHAR *common_name, UINT
                  common_name_length);
```

### <a name="description"></a>Описание

Эта служба удаляет экземпляр локального сертификата из сеанса TLS, введенный в поле общего имени сертификата.

> [!IMPORTANT]
> *Этот API не следует использовать с тем же сеансом TLS при использовании nx_secure_tls_server_certificate_add. API сертификата сервера использует уникальный числовой идентификатор для каждого сертификата, а nx_secure_tls_local_certificate_add использует индексы на основе общего имени X.509. Службы локальных сертификатов предоставляют удобную альтернативу числовому идентификатору для приложений, использующих только один сертификат удостоверения — общее имя. Приложению не нужно отслеживать числовые идентификаторы*.

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.
- **common_name** — значение общего имени удаляемого сертификата.
- **common_name_length** — длина строки общего имени.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное добавление сертификата.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) — сертификат не найден.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a>См. также:

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_add

## <a name="nx_secure_tls_metadata_size_calculate"></a>nx_secure_tls_metadata_size_calculate

Вычисление размера криптографических метаданных для сеанса NetX Secure TLS

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_metadata_size_calculate(
                        const NX_SECURE_TLS_CRYPTO *crypto_table,
                        ULONG *metadata_size);
```

### <a name="description"></a>Описание

Эта служба вычисляет и возвращает размер криптографических метаданных, необходимых для конкретного сеанса TLS и таблицы шифрования TLS (дополнительные сведения о таблице криптографических шифров см. в разделе «Инициализация TLS с помощью методов шифрования»).

Эту службу следует вызывать вместе с необходимой криптографической таблицей для вычисления размера буфера метаданных, переданного в nx_secure_tls_session_create.

### <a name="parameters"></a>Параметры

- **crypto_table** — указатель на заполненную таблицу шифрования NetX Secure TLS.
- **metadata_size** — выходные данные вычисления размера в байтах.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — вычисление размера метаданных выполнено успешно.
- **NX_PTR_ERROR** (0x07) — недопустимая таблица шифрования или указатель на возвращаемый размер.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Pointer to the platform-specific cipher table. */
extern nx_crypto_tls_ciphers;

/* Return variable for metadata size. */
ULONG crypto_metadata_size;

/* Calculate metadata size.  */
status =  nx_secure_tls_metadata_size_calculate(&nx_crypto_tls_ciphers,
                                                &crypto_metadata_size);


/* If status is NX_SUCCESS then crypto_metadata_size contains the size of the
   metadata buffer for the table nx_crypto_tls_ciphers.  */
```

### <a name="see-also"></a>См. также:

- nx_secure_tls_session_create

## <a name="nx_secure_module_hash_compute"></a>nx_secure_module_hash_compute

Вычисление хэш-значения подпрограмм библиотеки NetX Secure

### <a name="prototype"></a>Прототип

```C
VOID nx_secure_module_hash_compute(VOID);
```

### <a name="description"></a>Описание

Эта служба инициализирует модуль NetX Secure TLS. Его необходимо вызвать до доступа к другим службам NetX Secure.

### <a name="parameters"></a>Параметры

None

### <a name="return-values"></a>Возвращаемые значения

Нет

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Пример

```C
/* Initializes the TLS module. */
Nx_secure_tls_initialize();
```

### <a name="see-also"></a>См. также:

- nx_secure_tls_session_create

## <a name="nx_secure_tls_packet_allocate"></a>nx_secure_tls_packet_allocate

Выделение пакета для сеанса NetX Secure TLS

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_packet_allocate(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET_POOL *pool_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба выделяет пакет NX_PACKET для указанного активного сеанса TLS из заданного пула NX_PACKET_POOL. Приложение должно вызывать эту службу для выделения пакетов данных, которые отправляют через подключение TLS. Перед вызовом этой службы необходимо инициализировать сеанс TLS.

Выделенный пакет инициализируется таким образом, чтобы после заполнения данных пакета можно было добавить данные верхнего и нижнего колонтитулов TLS. В противном случае поведение идентично службе *nx_packet_allocate*.

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на экземпляр сеанса TLS.
- **pool_ptr** — указатель на пул NX_PACKET_POOL, из которого выделяется пакет.
- **packet_ptr** — указатель вывода на вновь выделенный пакет.
- **wait_option** — параметр приостановки выделения пакетов.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — пакет выделен успешно.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) — не удалось выделить базовый пакет.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) — указанный сеанс TLS не инициализирован.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Allocate a new TLS packet from the previously created packet pool and
previously initialized TLS session.   */

status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &packet_ptr,
                                       NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
variable packet_ptr.  */
```

### <a name="see-also"></a>См. также:

- nx_tcp_socket_receive
- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_receive
- nx_secure_tls_session_send
- nx_secure_tls_session_end
- nx_secure_tls_session_create

## <a name="nx_secure_tls_psk_add"></a>nx_secure_tls_psk_add

Добавление общего ключа в сеанс NetX Secure TLS

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_psk_add(NX_SECURE_TLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a>Описание

Эта служба добавляет общий ключ (PSK), строку удостоверения и указание удостоверения в блок управления сеансом TLS. Если включены и используются наборы шифров PSK, то вместо цифрового сертификата используется PSK.

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.
- **pre_shared_key** — фактическое значение PSK.
- **psk_length** — длина значения PSK.
- **psk_identity** — строка, используемая для идентификации этого значения PSK.
- **identity_length** — длина удостоверения PSK.
- **hint** — строка, используемая для указания группы ключей PSK, из которой необходимо выбрать ключ на сервере TLS.
- **hint_length** — длина строки указания.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное добавление PSK.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) — невозможно добавить еще один PSK.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_psk_add(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a>См. также:

- nx_secure_tls_client_psk_set
- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_add

## <a name="nx_secure_tls_remote_certificate_allocate"></a>nx_secure_tls_remote_certificate_allocate

Выделение пространства для сертификата, предоставленного удаленным узлом TLS

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_remote_certificate_allocate(
                 NX_SECURE_TLS_SESSION *session_ptr,
                 NX_SECURE_X509_CERT *certificate_ptr,
                 UCHAR *raw_certificate_buffer,
                 UINT raw_buffer_size);
```

### <a name="description"></a>Описание

Эта служба добавляет неинициализированный экземпляр структуры NX_SECURE_X509_CERT в сеанс TLS с целью выделения места для сертификатов, которые предоставляет удаленный узел во время сеанса TLS. Данные удаленного сертификата анализируются с помощью NetX Secure TLS. Эти сведения затем используют для заполнения экземпляра структуры сертификата, предоставленного в эту функцию. Сертификаты, добавленные таким способом, помещаются в связанный список.

Если предполагается, что удаленный узел предоставит несколько сертификатов, эту функцию следует вызывать повторно, чтобы выделить место для всех сертификатов. Дополнительные сертификаты добавляются в конец связанного списка сертификатов.

Сбой выделения удаленного сертификата приведет к сбою режима клиента TLS во время подтверждения TLS, если не используется набор шифров для общего ключа (PSK).

Параметр *raw_certificate_buffer* указывает на место, выделенное для хранения входящего удаленного сертификата. Размеры типичных сертификатов с 2048-битными ключами RSA, использующих SHA-256 для подписей, находятся в диапазоне от 1000 до 2000 байтов. Буфер должен быть достаточно большим, чтобы вместить этот размер, но в зависимости от сертификатов удаленного узла может быть значительно меньше или больше. Обратите внимание, если размера буфера недостаточно для хранения входящего сертификата, то подтверждение TLS завершится ошибкой.

Для режима сервера TLS удаленное выделение сертификатов требуется только в том случае, если включена проверка подлинности с помощью сертификата клиента.

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.
- **certificate_ptr** — указатель на неинициализированный экземпляр сертификата X.509.
- **raw_certificate_buffer** — указатель на буфер для хранения непроанализированного сертификата, полученного с удаленного узла.
- **buffer_size** — размер необработанного буфера сертификата.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сертификат успешно выделен.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.
- **NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) — указанный буфер слишком мал.
- **NX_INVALID_PARAMETERS** (0x4D) — попытка добавить недопустимый сертификат.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;

/* Buffer space to hold the incoming certificate. */
UCHAR certificate_buffer[2000];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_allocate(&tls_session, &certificate,
                                                    certificate_buffer,
                                                    sizeof(certificate_buffer));


/* If status is NX_SUCCESS the certificate was successfully allocated.  */
```

### <a name="see-also"></a>См. также:

- nx_secure_x509_certificate_initialize,
- nx_secure_tls_session_create

## <a name="nx_secure_tls_remote_certificate_buffer_allocate"></a>nx_secure_tls_remote_certificate_buffer_allocate

Выделение пространства для всех сертификатов, предоставленных удаленным узлом TLS

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_remote_certificate_buffer_allocate(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a>Описание

Эта служба выделяет место для обработки входящих цепочек сертификатов с удаленных узлов сервера для выполнения проверки подлинности X.509 и проверки в экземпляре клиента TLS. Для режима сервера TLS удаленное выделение сертификатов требуется только в том случае, если включена проверка подлинности клиента X.509. Для экземпляров сервера TLS следует использовать службу *nx_secure_tls_session_x509_client_verify_configure*.

Сбой выделения удаленных сертификатов приведет к сбою режима клиента TLS во время подтверждения TLS, если не используется набор шифров для общего ключа (PSK).

Параметр *certificate_buffer* указывает на место, выделенное для хранения входящих удаленных сертификатов и блоков управления, необходимых для этих сертификатов. Буфер будет разделен по количеству сертификатов (*certs_number*) на равные части для каждого сертификата. Параметр *buffer_size* указывает размер буфера. Необходимый объем пространства можно вычислить по следующей формуле:

```C
buffer_size = (<expected max number of certificates in chain>) *
                 (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

Размеры типичных сертификатов с 2048-битными ключами RSA, использующих SHA-256 для подписей, находятся в диапазоне от 1000 до 2000 байтов. Буфер должен быть достаточно большим, чтобы вместить этот размер для каждого сертификата, но в зависимости от сертификатов удаленного узла может быть значительно меньше или больше. Обратите внимание, если размера буфера недостаточно для хранения входящего сертификата, то подтверждение TLS завершится ошибкой.

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.
- **certs_number** — количество сертификатов, выделенных из предоставленного буфера.
- **certificate_buffer** — указатель на буфер для хранения сертификатов, полученных с удаленного узла.
- **buffer_size** — размер буфера сертификата.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сертификат успешно выделен.
- **NX_PTR_ERROR** (0x07) — недопустимый сеанс TLS или указатель буфера.
- **NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) — указанный буфер слишком мал.
- **NX_INVALID_PARAMETERS** (0x4D) — буфер слишком мал, чтобы вместить необходимое количество сертификатов.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Buffer space to hold the incoming certificates. */
#define CERTIFICATE_NUMBER    (2)
#define CERTIFICATE_SIZE      (2000)
#define BUFFER_SIZE           (CERTIFICATE_NUMBER * \
                              (sizeof(NX_SECURE_X509_CERT) + CERTIFICATE_SIZE))
UCHAR certificate_buffer[BUFFER_SIZE];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_buffer_allocate(&tls_session,
                                                      CERTIFICATE_NUMBER,
                                                      certificate_buffer,
                                                      BUFFER_SIZE);


/* If status is NX_SUCCESS the buffer was successfully allocated.  */
```

### <a name="see-also"></a>См. также:

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create

## <a name="nx_secure_tls_remote_certificate_free_all"></a>nx_secure_tls_remote_certificate_free_all

Освобождение места, выделенного для входящих сертификатов

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_remote_certificate_free_all(
                  NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Описание

Эта служба используется для высвобождения всех буферов сертификатов, выделенных для определенного сеанса TLS з помощью nx_secure_tls_remote_certificate_allocated, путем их возврата в свободное место на этом сеансе. Это может быть необходимо, если приложение повторно использует объект сеанса TLS без удаления и повторного создания этого объекта с помощью nx_secure_tls_session_delete и nx_secure_tls_session_create.

Обратите внимание, что удаленное пространство сертификатов автоматически восстанавливается при сбросе сеанса TLS, как это происходит в nx_secure_tls_session_end, поэтому большинству приложений не требуется вызывать эту службу.

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — операция выполнена успешно.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.
- **NX_INVALID_PARAMETERS** (0x4D) — внутренняя ошибка — вероятное повреждение хранилища сертификатов.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;

/* Buffer space to hold the incoming certificate. */
UCHAR certificate_buffer[2000];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_allocate(&tls_session, &certificate,
                                                    certificate_buffer,
                                                    sizeof(certificate_buffer));


/* If status is NX_SUCCESS the certificate was successfully allocated.  */

/* … TLS session setup, TCP connection, etc… */

/* End TLS session. */
nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

/* Free up certificate buffers for next connection. */
nx_secure_tls_remote_certificate_free_all(&tls_session);
```

### <a name="see-also"></a>См. также:

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_end

## <a name="nx_secure_tls_server_certificate_add"></a>nx_secure_tls_server_certificate_add

Добавление сертификата специально для серверов TLS с помощью числового идентификатора

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_server_certificate_add(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT *certificate, UINT cert_id);
```

### <a name="description"></a>Описание

Эта служба используется для добавления сертификата в локальное хранилище сеанса TLS (см. nx_secure_tls_local_certificate_add) с использованием числового идентификатора вместо индексирования хранилища с помощью субъекта X.509 (общее имя) в сертификате. Числовой идентификатор не зависит от сертификата и позволяет добавлять на сервер TLS несколько сертификатов в качестве сертификатов удостоверений, а также позволяет добавлять несколько сертификатов с одинаковым общим именем в одно и то же локальное хранилище сеанса TLS. Эту же службу можно использовать для сертификатов клиента, но в клиенте TLS крайне редко бывает несколько сертификатов удостоверений.

Параметр cert_id — это ненулевое положительное целое число, которое назначает приложение. Фактическое значение не играет роли (кроме нуля), но оно должно быть уникальным в хранилище для указанного сеанса TLS. Значение cert_id можно использовать для поиска и удаления сертификатов из локального хранилища с помощью nx_secure_tls_server_certificate_find и nx_secure_tls_server_certificate_remove соответственно.

> [!IMPORTANT]
> *Этот API не следует использовать с тем же сеансом TLS при использовании nx_secure_tls_local_certificate_add. API nx_secure_tls_server_certificate_add использует уникальный числовой идентификатор для каждого сертификата и локальный индекс служб сертификатов на основе общего имени X.509. Службы сертификатов сервера позволяют хранить несколько сертификатов с общими данными (особенно общим именем) в одном локальном хранилище — это полезно для сервера с несколькими удостоверениями.*

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.
- **certificate** — указатель на инициализированный ранее экземпляр сертификата X.509.
- **cert_id** — положительный, ненулевой, сравнительно уникальный код сертификата.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — операция выполнена успешно.
- **NX_PTR_ERROR** (0x07) — недопустимый сеанс TLS или указатель на сертификат.
- **NX_SECURE_TLS_CERT_ID_INVALID** (0x138) — указанный идентификатор сертификата имел недопустимое значение (скорее всего 0).
- **NX_SECURE_TLS_CERT_ID_DUPLICATE** (0x139) — указанный идентификатор сертификата уже есть в локальном хранилище.
- **NX_INVALID_PARAMETERS** (0x4D) — внутренняя ошибка — вероятное повреждение хранилища сертификатов.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;


/* Add certificate to TLS session.  */
status =  nx_secure_tls_server_certificate_add(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully added with the ID
0x12.  */
```

### <a name="see-also"></a>См. также:

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_active_certificate_set
- nx_secure_tls_server_certificate_find
- nx_secure_tls_server_certificate_remove

## <a name="nx_secure_tls_server_certificate_find"></a>nx_secure_tls_server_certificate_find

Поиск сертификата по числовому идентификатору

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_server_certificate_find(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT **certificate, UINT cert_id);
```

### <a name="description"></a>Описание

Эта служба используется для поиска сертификата в локальном хранилище сеанса TLS (см. nx_secure_tls_local_certificate_add) с использованием числового идентификатора вместо индексирования хранилища с помощью субъекта X.509 (общее имя) в сертификате.

Параметр cert_id — ненулевое положительное целое число, которое назначает приложение при добавлении сертификата в локальное хранилище сеанса TLS с помощью nx_secure_tls_server_certificate_add.

> [!IMPORTANT]
> *Этот API не следует использовать с тем же сеансом TLS при использовании nx_secure_tls_local_certificate_add. API nx_secure_tls_server_certificate_add использует уникальный числовой идентификатор для каждого сертификата и локальный индекс служб сертификатов на основе общего имени X.509. Службы сертификатов сервера позволяют хранить несколько сертификатов с общими данными (особенно общим именем) в одном локальном хранилище — это полезно для сервера с несколькими удостоверениями.*

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.
- **certificate** — указатель на указатель сертификата X.509 для возврата ссылки на найденный сертификат.
- **cert_id** — ненулевое положительное значение идентификатора сертификата.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — операция выполнена успешно.
- **NX_PTR_ERROR** (0x07) — недопустимый сеанс TLS или указатель на сертификат.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) — указанный идентификатор сертификата не соответствует ни одному из локальных хранилищ указанного сеанса TLS.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
NX_SECURE_X509_CERT *certificate;


/* Find certificate in TLS session.  */
status =  nx_secure_tls_server_certificate_find(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully found and a reference
returned in the certificate parameter.  */
```

### <a name="see-also"></a>См. также:

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_active_certificate_set
- nx_secure_tls_server_certificate_add
- nx_secure_tls_server_certificate_remove

##  <a name="nx_secure_tls_server_certificate_remove"></a>nx_secure_tls_server_certificate_remove

Удаление сертификата локального сервера с помощью числового идентификатора

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_server_certificate_remove(
                  NX_SECURE_TLS_SESSION *session_ptr, UINT cert_id);
```

### <a name="description"></a>Описание

Эта служба используется для удаления сертификата из локального хранилища сеанса TLS (см. nx_secure_tls_local_certificate_add) с использованием числового идентификатора вместо индексирования хранилища с помощью субъекта X.509 (общее имя) в сертификате.

Параметр cert_id — ненулевое положительное целое число, которое назначает приложение при добавлении сертификата в локальное хранилище сеанса TLS с помощью nx_secure_tls_server_certificate_add.

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.
- **cert_id** — ненулевое положительное значение идентификатора сертификата.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — операция выполнена успешно.
- **NX_PTR_ERROR** (0x07) — недопустимый сеанс TLS.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) — указанный идентификатор сертификата не соответствует ни одному из локальных хранилищ указанного сеанса TLS.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;


/* Add certificate to TLS session with id 0x12.  */
status =  nx_secure_tls_server_certificate_add(&tls_session, &certificate, 0x12);
/* Use certificate in TLS session, etc… */

/* Remove certificate from TLS session with id 0x12.  */
status =  nx_secure_tls_server_certificate_remove(&tls_session, 0x12);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a>См. также:

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_active_certificate_set
- nx_secure_tls_server_certificate_add
- nx_secure_tls_server_certificate_find

## <a name="nx_secure_tls_session_alert_value_get"></a>nx_secure_tls_session_alert_value_get

Получение значения и уровня оповещения TLS, отправленного удаленным узлом

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_session_alert_value_get(
                   NX_SECURE_TLS_SESSION *session_ptr,
                   UINT *alert_level, UINT *alert_value);
```

### <a name="description"></a>Описание

Эта служба используется для получения уровня и значения оповещения TLS, когда удаленный узел отправляет оповещение в ответ на какую-либо проблему или ошибку.

Значения параметров alert_level и alert_value допустимы только в том случае, если эта функция вызывается сразу после вызова API TLS, который вернул состояние NX_SECURE_TLS_ALERT_RECEIVED (0x114), указывающее на то, что оповещение получено из удаленного узла.

Обратите внимание, что если TLS на локальном узле отправляет оповещение, полученные коды ошибок содержат намного больше полезной информации по фактической ошибке, чем само оповещение TLS, так как значения оповещений TLS преднамеренно оставлены неоднозначными для предотвращения определенных типов атак (например, атака типа padding oracle или подобные).

Уровень оповещения принимает одно из двух значений: NX_SECURE_TLS_ALERT_LEVEL_WARNING (0x1) или NX_SECURE_TLS_ALERT_LEVEL_FATAL (0x2). Как правило, только оповещение CloseNotify (используемое для указания успешного завершения сеанса TLS) будет иметь уровень "Предупреждение", хотя некоторые ситуации конфигурации расширения также могут считаться предупреждениями. Подавляющее большинство оповещений будут иметь значение «Неустранимый», что свидетельствует о возможной ошибке безопасности и приведет к немедленному закрытию TLS-подключения (подтверждения или сеанса).

Значения оповещений TLS определены в документах RFC по протоколу TLS. Ниже приведен список из документа RFC 5246 (TLSv1.2) для справки.

| Имя предупреждения                     | Значение | Описание                                                                                                                                                  |
| ---------------------------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| close_notify                  | 0     | Без ошибок, указывает на успешное завершение сеанса                                                                                                                   |
| unexpected_message            | 10    | Протокол TLS получил неожиданное или неупорядоченное сообщение                                                                                                           |
| bad_record_mac               | 20    | Сбой расшифровки или проверки MAC                                                                                                                    |
| decryption_failed_RESERVED   | 21    | **Не рекомендуется**. Сбой расшифровки (не рекомендуется из-за атак padding oracle)                                                                                      |
| record_overflow               | 22    | Размер полученной записи превышает максимальный размер записи TLS                                                                                        |
| decompression_failure         | 30    | Возникла проблема при сжатии или распаковке записи TLS                                                                                       |
| handshake_failure             | 40    | Произошла неопределенная ошибка подтверждения, не связанная с другим оповещением                                                                            |
| no_certificate_RESERVED      | 41    | **Не рекомендуется** в протоколе TLS (только SSL)                                                                                                                                 |
| bad_certificate               | 42    | Полученный сертификат содержал недопустимое форматирование или подписи                                                                                   |
| unsupported_certificate       | 43    | Получен сертификат недопустимого типа (например, сертификат только для подписи, используемый для проверки подлинности сервера TLS)                                    |
| certificate_revoked           | 44    | Состояние сертификата (предоставленное списком отзыва сертификатов или OCSP) указано как "Отозвано"                                                                       |
| certificate_expired           | 45    | Полученный сертификат находится за пределами допустимого диапазона дат (он еще не действителен или устарел)                                                                 |
| certificate_unknown           | 46    | Обнаружена неизвестная ошибка сертификата, которая не относится к другим оповещениям                                                                          |
| illegal_parameter             | 47    | Конфигурация или согласованное значение в подтверждении TLS являются недопустимыми или находятся за пределами диапазона                                                                      |
| unknown_ca                    | 48    | Не удалось отследить полученный сертификат удостоверения через цепочку сертификатов до доверенного корневого сертификата ЦС.                                              |
| access_denied                 | 49    | Указывает, что был получен допустимый сертификат, но контроль доступа к приложениям указал, что для запрашиваемых ресурсов сертификат был недопустимым.            |
| decode_error                  | 50    | Поле или значения в сообщении с заголовком или подтверждением TLS находились вне допустимого диапазона или являются недопустимыми, что привело к сбою при декодировании записи TLS.                      |
| decrypt_error                 | 51    | Не удалось проверить хэш подписи или сообщения о завершении подтверждения TLS.                                                                         |
| export_restriction_RESERVED  | 60    | Не рекомендуется для версии TLSv1.2                                                                                                                                        |
| protocol_version              | 70    | Версия протокола TLS, согласованная во время подтверждения, распознана, но не поддерживается (например, если версия TLSv1.0 предоставлена, но не включена).                       |
| insufficient_security         | 71    | Отправляется при сбое подтверждения из-за отсутствия безопасных шифров (например, если размер ключа слишком мал согласно требованиям приложения).                                |
| internal_error                | 80    | Произошла ошибка, не относящаяся к протоколу TLS (например, проблемы с выделением памяти или проблемы с приложением), что привело к прекращению сеанса TLS.                                         |
| user_canceled                 | 90    | Возвращается, если пользователь или приложение отменили сеанс TLS до завершения подтверждения (подобно оповещению CloseNotify).                                 |
| no_renegotiation              | 100   | Указывает, что удаленный узел не может выполнить подтверждения повторного согласования TLS в ответ на запрос на повторное согласование.                                 |
| unsupported_extension         | 110   | Отправляется, если клиент TLS получает ServerHello с расширениями, которые явным образом не запрашивались в первоначальном ClientHello (что указывает на проблему с сервером). |

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на экземпляр сеанса TLS.
- **alert_level** — возвращает уровень полученного оповещения (предупреждение или неустранимая ошибка).
- **alert_value** — возвращает значение полученного оповещения (см. таблицу).

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — операция выполнена успешно.
- **NX_PTR_ERROR** (0x07) — недопустимый сеанс TLS.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Return values. */
UINT status, alert_level, alert_value;


/* Start a TLS session.  */
status =  nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);

/* Check for “alert received” error. */
if(status == NX_SECURE_TLS_ALERT_RECEIVED)
{

        /* Get the alert level and value. */
        status =  nx_secure_tls_session_alert_value_get(&tls_session,
                                             &alert_level, &alert_value);

        /* Print out the received alert level and value. */
        printf("Alert recieved. Value: %d, Level: %d\n", alert_value,
                alert_level);
}
else if(status != NX_SUCCESS)
{
    /* Additional error handling. */
}
```

### <a name="see-also"></a>См. также:

- nx_secure_tls_session_start
- nx_secure_tls_session_send
- nx_secure_tls_session_receive

## <a name="nx_secure_tls_session_certificate_callback_set"></a>nx_secure_tls_session_certificate_callback_set

Настройка обратного вызова для протокола TLS, который будет использоваться для дополнительной проверки сертификата

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_ session_certificate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *session,
                                    NX_SECURE_X509_CERT *certificate));
```

### <a name="description"></a>Описание

Эта служба назначает указатель функции на сеанс TLS, который будет вызываться протоколом TLS при получении сертификата с удаленного узла. Таким образом приложение сможет выполнять такие проверки, как проверка DNS, отзыв сертификата и принудительное применение политики сертификатов.

NetX Secure TLS выполняет базовую проверку пути X.509 для сертификата перед выполнением обратного вызова, чтобы убедиться, что сертификат можно отследить до сертификата в хранилище доверенных сертификатов TLS, но все остальные проверки будут обрабатываться этим обратным вызовом.

Обратный вызов предоставляет указатель сеанса TLS и указатель на сертификат удостоверения удаленного узла (конечный объект в цепочке сертификатов). Обратный вызов должен возвращать значение NX_SUCCESS, если вся проверка прошла успешно. В противном случае он должен вернуть код ошибки, указывающий на сбой проверки. Любое значение, кроме NX_SUCCESS, приведет к немедленному прерыванию подтверждения TLS.

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.
- **func_ptr** — указатель на функцию обратного вызова проверки сертификата.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное выделение указателя функции.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
    /* Certificate validation checking goes here. */
    return(NX_SUCCESS);
}

/* In TLS setup routine. */
{
        /* Add callback to TLS session.  */
        status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                            certificate_callback);

        /* If status is NX_SUCCESS the certificate callback was added.  */
}
```

### <a name="see-also"></a>См. также:

- nx_secure_tls_session_create
- nx_secure_x509_common_name_dns_check
- nx_secure_x509_crl_revocation_check

## <a name="nx_secure_tls_session_client_callback_set"></a>nx_secure_tls_session_client_callback_set

Настройка обратного вызова для протокола TLS для вызова в начале подтверждения клиента TLS

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_ session_client_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions, UINT num_extensions));
```

### <a name="description"></a>Описание

Эта служба назначает указатель функции сеансу TLS, который будет вызывать протокол TLS, если подтверждение клиента TLS получило сообщение ServerHelloDone. Функция обратного вызова позволяет приложению обрабатывать любые расширения TLS из полученного сообщения ServerHello, для которого необходимо ввести данные или принять решение.

Обратный вызов выполняется с помощью блока управления сеансом TLS и массива объектов NX_SECURE_TLS_HELLO_EXTENSION. Массив объектов расширения необходимо передать во вспомогательную функцию, которая найдет и проанализирует определенное расширение. Сейчас в NetX Secure не поддерживаются специальные расширения, для которых требуются входные данные клиента TLS. Однако разработчикам приложений доступен обратный вызов для обработки пользовательских или новых расширений, которые могут стать доступными. Пример вспомогательной функции, которая анализирует расширения TLS, предоставленные в сообщениях приветствия, см. на странице *nx_secure_tls_session_sni_extension_parse*.

Обратный вызов клиента также может использоваться для выбора активного сертификата удостоверения с помощью *nx_secure_tls_active_certificate_set* для клиента TLS в случае, если удаленный сервер запросил сертификат и предоставил сведения, позволяющие клиенту TLS выбирать конкретный сертификат. Дополнительные сведения см. в справочнике по nx_secure_tls_active_certificate_set.

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.
- **func_ptr** — указатель на функцию обратного вызова клиента TLS.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное выделение указателя функции.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Callback routine used to process ServerHello extensions and perform other
   runtime actions at the beginning of a TLS handshake (such as selecting an
   identify certificate to provide to the server). */

ULONG tls_client_callback(NX_SECURE_TLS_SESSION *session,
                          NX_SECURE_TLS_HELLO_EXTENSION *extensions, UINT
                          num_extensions)
{

    /* Extension parsing would go here. */

    /* Set an active identity certificate – the certificate should have been added
       to the local store at application start with
       nx_secure_tls_local_certificate_add. */
    nx_secure_tls_active_certificate_set(session, &global_identity_certificate);

    return(NX_SUCCESS);
}

/* TLS setup routine. */
UINT tls_setup(NX_SECURE_TLS_SESSION *tls_session)
{
    /* Add callback to TLS session.  */
    status =  nx_secure_tls_session_client_callback_set(tls_session,
                                                        client_callback);

    /* If status is NX_SUCCESS the callback was added and will be invoked once
       a ServerHelloDone message is received. */

    return(status);
}
```

### <a name="see-also"></a>См. также:

- nx_secure_tls_session_create
- nx_secure_tls_session_server_callback_set
- nx_secure_tls_active_certificate_set

## <a name="nx_secure_tls_session_x509_client_verify_configure"></a>nx_secure_tls_session_x509_client_verify_configure

Включение проверки X.509 клиента и выделение места для сертификатов клиента

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_session_x509_client_verify_configure(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a>Описание

Эта служба включает необязательную проверку подлинности клиента X.509 для экземпляра сервера TLS. Она также выделяет пространство, необходимое для обработки входящих цепочек сертификатов с удаленного узла клиента. Сертификаты, которые предоставляет удаленный клиент, будут проверены на соответствие доверенным сертификатам экземпляра сервера TLS, который назначила служба *nx_secure_tls_trusted_certificate_add*.

Для режима клиента TLS требуется удаленное выделение сертификатов и следует использовать службу *nx_secure_tls_remote_certificate_buffer_allocate*. Включение проверки подлинности клиента X.509 в экземпляре клиента TLS не будет действовать.

Параметр *certificate_buffer* указывает на место, выделенное для хранения входящих удаленных сертификатов и блоков управления, необходимых для этих сертификатов. Буфер будет разделен по количеству сертификатов (*certs_number*) на равные части для каждого сертификата. Параметр *buffer_size* указывает размер буфера. Необходимый объем пространства можно вычислить по следующей формуле:

```C
buffer_size = (<expected max number of certificates in chain>) *
             (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

Размеры типичных сертификатов с 2048-битными ключами RSA, использующих SHA-256 для подписей, находятся в диапазоне от 1000 до 2000 байтов. Буфер должен быть достаточно большим, чтобы вместить этот размер для каждого сертификата, но в зависимости от сертификатов удаленного узла может быть значительно меньше или больше. Обратите внимание, если размера буфера недостаточно для хранения входящего сертификата, то подтверждение TLS завершится ошибкой.

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.
- **certs_number** — число сертификатов, выделенных из предоставленного буфера.
- **certificate_buffer** — указатель на буфер для хранения сертификатов, полученных с удаленного узла.
- **buffer_size** — размер буфера сертификата.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сертификат успешно выделен.
- **NX_PTR_ERROR** (0x07) — недопустимый сеанс TLS или указатель буфера.
- **NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) — указанный буфер слишком мал.
- **NX_INVALID_PARAMETERS** (0x4D) — буфер слишком мал, чтобы вместить необходимое количество сертификатов.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Buffer space to hold the incoming certificates. */
#define CERTIFICATE_NUMBER    (2)
#define CERTIFICATE_SIZE      (2000)
#define BUFFER_SIZE          (CERTIFICATE_NUMBER * \
                                (sizeof(NX_SECURE_X509_CERT) + CERTIFICATE_SIZE))
UCHAR certificate_buffer[BUFFER_SIZE];

/* Enable X.509 Client verification and allocate certificate space in our TLS
   Server session.  */
status =  nx_secure_tls_session_x509_client_verify_configure(&tls_session,
                                                    CERTIFICATE_NUMBER,
                                                    certificate_buffer,
                                                    BUFFER_SIZE);


/* If status is NX_SUCCESS the buffer was successfully allocated.  */
```

### <a name="see-also"></a>См. также:

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_buffer_allocate

## <a name="nx_secure_tls_session_client_verify_disable"></a>nx_secure_tls_session_client_verify_disable

Отключение проверки подлинности сертификата клиента для сеанса NetX Secure TLS

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_session_client_verify_disable(
                              NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Описание

Эта служба отключает проверку подлинности сертификата клиента для определенного сеанса TLS. Дополнительные сведения см. в справочнике по nx_secure_tls_session_client_verify_enable.

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на экземпляр сеанса TLS.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное изменение состояния.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_disable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will not
request certificates from the remote TLS client.  */
```

### <a name="see-also"></a>См. также:

- nx_secure_tls_session_client_verify_enable
- nx_secure_tls_session_start
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_client_verify_enable"></a>nx_secure_tls_session_client_verify_enable

Отключение проверки подлинности сертификата клиента для сеанса NetX Secure TLS

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_session_client_verify_enable(
                                NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Описание

Эта служба включает проверку подлинности сертификата клиента для определенного сеанса TLS. Включение проверки подлинности сертификата клиента для экземпляра сервера TLS приведет к тому, что сервер TLS запросит сертификат из любого удаленного клиента TLS во время первоначального подтверждения TLS. Сертификат, полученный от удаленного клиента TLS, сопровождается сообщением CertificateVerify, которое сервер TLS использует для проверки на наличие прав владения сертификатом у клиента (наличие доступа к закрытому ключу, связанному с этим сертификатом).

Если предоставленный сертификат можно проверить и отследить до сертификата в хранилище доверенных сертификатов сервера TLS с помощью цепочки сертификатов X.509, удаленный клиент TLS проходит проверку подлинности, а подтверждение остается в силе. В случае возникновения ошибок при обработке сертификата или сообщения CertificateVerify подтверждение TLS завершается с ошибкой.

> [!NOTE]
> *У сервера TLS должен быть по крайней мере один сертификат, добавленный с помощью nx_secure_tls_trusted_certificate_add, иначе проверка подлинности всегда будет завершаться ошибкой.*

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на экземпляр сеанса TLS.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное изменение состояния.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Add a trusted certificate so the TLS Server has something to verify against. */
status = nx_secure_tls_trusted_certificate_add(&tls_session,
                                               &trusted_certificate);

/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_enable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will now
request and verify certificates from the remote TLS client.  */
```

### <a name="see-also"></a>См. также:

- nx_secure_tls_session_client_verify_enable
- nx_secure_tls_session_start
- nx_secure_tls_session_create
- nx_secure_tls_trusted_certificate_add

## <a name="nx_secure_tls_session_create"></a>nx_secure_tls_session_create

Создание сеанса NetX Secure TLS для обеспечения безопасности подключений

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_session_create(NX_SECURE_TLS_SESSION *session_ptr
                                   NX_SECURE_TLS_CRYPTO *cipher_table,
                                   VOID *encryption_metadata_area,
                                   ULONG encryption_metadata_size);
```

### <a name="description"></a>Описание

Эта служба инициализирует экземпляр структуры NX_SECURE_TLS_SESSION для использования во время безопасного взаимодействия по протоколу TLS через сетевое подключение.

Метод принимает объект NX_SECURE_TLS_CRYPTO, который заполняется доступными криптографическими методами для использования с протоколом TLS. *encryption_metadata_area* указывает на буфер, выделенный для использования протоколом TLS для "метаданных", которые используются криптографическими методами в таблице NX_SECURE_TLS_CRYPTO для вычислений. Размер таблицы можно определить с помощью службы nx_secure_tls_metadata_size_calculate. Дополнительные сведения см. в разделе "Шифрование в NetX Secure TLS" главы 3.

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на экземпляр сеанса TLS.
- **cipher_table** — указатель на криптографические методы TLS.
- **encryption_metadata_area** — указатель на пространство для метаданных шифрования.
- **encryption_metadata_size** — размер буфера метаданных.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сеанс TLS успешно инициализирован.
- **NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.
- **NX_INVALID_PARAMETERS** (0x4D) — буфер метаданных слишком мал для указанных методов.
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) — необходимый метод шифра для включенной версии TLS не указан в таблице шифров.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Reference the platform-specific TLS cryptographic method table. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;

/* Declare a buffer for the cryptographic metadata. The size should be calculated
   using nx_secure_tls_metadata_size_calculate. */
UCHAR crypto_metadata[4500];

/* Initialize TLS session.  */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* If status is NX_SUCCESS the TLS Session was successfully initialized.  */
```

### <a name="see-also"></a>См. также:

- nx_secure_x509_certificate_initialize
- nx_secure_tls_metadata_size_calculate
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_end
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_delete
- Шифрование для NetX Secure TLS в главе 3

## <a name="nx_secure_tls_session_delete"></a>nx_secure_tls_session_delete

Удаление сеанса NetX Secure TLS

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_session_delete(NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет сеанс TLS, представленный экземпляром структуры NX_SECURE_TLS_SESSION, и освобождает все системные ресурсы этого экземпляра сеанса.

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на экземпляр сеанса TLS.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сеанс TLS успешно инициализирован.
- **NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Delete TLS session.  */
status =  nx_secure_tls_session_delete(&tls_session);


/* If status is NX_SUCCESS the TLS Session was successfully deleted.  */
```

### <a name="see-also"></a>См. также:

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_end
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_end"></a>nx_secure_tls_session_end

Завершение активного сеанса NetX Secure TLS

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_session_end(NX_SECURE_TLS_SESSION *session_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба завершает сеанс TLS, представленный экземпляром структуры NX_SECURE_TLS_SESSION, путем отправления сообщения CloseNotify протокола TLS на удаленный узел. Затем служба ожидает ответа от удаленного узла с собственным сообщением CloseNotify.

Если удаленный узел не отправляет сообщение CloseNotify, протокол TLS считает это ошибкой и возможным нарушением безопасности, поэтому проверка возвращаемого значения важна для безопасного подключения. Параметр **wait_option** можно использовать для управления длительностью ожидания ответа для службы перед возвращением управления вызывающему потоку.

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на экземпляр сеанса TLS.
- **wait_option** — указывает на длительность ожидания ответа для службы от удаленного узла.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сеанс TLS успешно инициализирован.
- **NX_SECURE_TLS_NO_CLOSE_RESPONSE** (0x113) — не получен ответ от удаленного узла до истечения времени ожидания.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) — не удалось выделить пакет для отправки сообщения CloseNotify.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) — не удалось отправить сообщение CloseNotify по TCP-сокету.
- **NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* End TLS session.  */
status =  nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the TLS Session was successfully ended.  */
```

### <a name="see-also"></a>См. также:

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_packet_buffer_set"></a>nx_secure_tls_session_packet_buffer_set

Установка буфера повторной сборки пакетов для сеанса NetX Secure TLS

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_session_packet_buffer_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *buffer_ptr,
                                    ULONG buffer_size);
```

### <a name="description"></a>Описание

Эта служба связывает буфер повторной сборки пакетов с сеансом TLS. Для расшифровки и анализа входящих записей TLS необходимо собрать данные в каждой записи из базовых TCP-пакетов. Размер записей TLS может составлять до 16 КБ (хотя обычно намного меньше), поэтому они могут не поместиться в один TCP-пакет.

Если известно, что размер входящего сообщения будет меньше предельного числа записей TLS, равного 16 КБ, размер буфера можно уменьшить. Однако для обработки неизвестных входящих данных буфер следует сделать максимально большим. Если входящая запись больше, чем заданный буфер, то сеанс TLS завершится с ошибкой.

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на экземпляр сеанса TLS.
- **buffer_ptr** — указатель на буфер для протокола TLS, используемый для повторной сборки пакетов.
- **buffer_size** — размер заданного буфера в байтах.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сеанс TLS успешно инициализирован.
- **NX_INVALID_PARAMETERS** (0x4D) — недопустимый буфер или указатель сеанса TLS.
- **NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Buffer for TLS packet reassembly. */
UCHAR tls_packet_buffer[16384];
/* Assign buffer to TLS session.  */
status =  nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                  sizeof(tls_packet_buffer));


/* If status is NX_SUCCESS the buffer was successfully added.  */
```

### <a name="see-also"></a>См. также:

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_protocol_version_override"></a>nx_secure_tls_session_protocol_version_override

Переопределение версии протокола TLS по умолчанию для сеанса NetX Secure TLS

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_session_protocol_version_override(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              USHORT protocol_version);
```

### <a name="description"></a>Описание

Эта служба переопределяет версию протокола TLS по умолчанию (самую новую), используемую в определенном сеансе. Это позволяет NetX Secure TLS использовать более раннюю версию протокола TLS для определенного сеанса протокола, не отключая ее во время компиляции. Это может быть полезно в приложениях, которым может потребоваться обмен данными с узлом более ранней версии, который не поддерживает последнюю версию TLS.

> [!IMPORTANT]
> *Начиная с версии 5.11 с пакетом обновления 3 (SP3), NetX Secure TLS поддерживает RFC 7507 (см. примечание ниже) и любое переопределение более старой версии с помощью этого API приведет к тому, что в ClientHello будет отправлено резервное SCSV. Если сервер поддерживает более новую версию TLS и резервное SCSV добавлено в ClientHello, этот сервер прервет подтверждение TLS с оповещением "Неприемлемый резерв". SCSV отправляется, только если версия переопределения является более старой, чем используемая версия TLS (например, при переопределении версии до TLS 1.2 SCSV не будет отправлен).*

Допустимыми значениями параметра protocol_version являются следующие макросы: NX_SECURE_TLS_VERSION_TLS_1_0, NX_SECURE_TLS_VERSION_TLS_1_1 и NX_SECURE_TLS_VERSION_TLS_1_2.

Макросы NX_SECURE_TLS_DISABLE_TLS_1_1 и NX_SECURE_TLS_ENABLE_TLS_1_0 могут использоваться для управления версиями TLS, компилируемыми в приложение. Протокол TLS версии 1.2 всегда включен.

Обратите внимание, что если удаленный узел не поддерживает предоставленную версию, произойдет сбой подключения. Только предоставленная версия переопределения будет согласовываться с помощью NetX Secure TLS.

> [!IMPORTANT]
> RFC 7507: резервное SCSV протокола TLS. Этот документ RFC предназначен для устранения проблемы безопасности, которая изначально была вызвана серверами, которые обрабатывали согласование с предыдущими протоколами ненадлежащим образом и отказались от других допустимых сообщений ClientHello. При попытке сохранить совместимость с этими старыми серверами некоторые клиентские приложения TLS начали повторно выполнять завершившиеся сбоем подтверждения с помощью более старой версии TLS (например, при сбое TLS 1.2 использовали TLS 1.1). Однако это обходное решение создало новую проблему. Злоумышленники могут заставить клиента перейти на более раннюю версию, искусственно вызывая ошибку сети или пакета, из-за которой происходит сбой подключения к серверу, даже если сервер поддерживает более новую версию TLS. При переходе на более старую версию злоумышленник может использовать слабые места в этой версии (SSLv3<sup>21</sup> особенно подвержен атаке POODLE). Чтобы предотвратить такую ситуацию, в документе RFC 7507 представлено "резервное SCSV" — псевдокомплект шифров <sup>22</sup>. Этот комплект отправляется в ClientHello, которое уведомляет сервер TLS, когда клиент протокола TLS использует не самую новую поддерживаемую версию протокола. Таким образом, сервер, поддерживающий более новую версию, может отклонить ClientHello, содержащее резервное SCSV, и предотвратить атаку, предполагающую переход на более раннюю версию.

21. NetX Secure не применяет SSLv3 из-за наличия серьезных слабых мест, таких как POODLE.

22. Псевдокомплект шифров или SCSV (сигнальное значение комплекта шифров) — это зарезервированное число комплектов шифров, которое используется для оповещения включенных реализаций TLS о функциях, которые были недоступны в более старых версиях TLS. Примерами являются резервное SCSV и TLS_EMPTY_RENEGOTIATION_INFO_SCSV (RFC 5746).

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на экземпляр сеанса TLS.
- **protocol_version** — макрос версии TLS для конкретной версии TLS.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное изменение состояния.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) — известная, но неподдерживаемая версия TLS.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) — недопустимая версия протокола.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Set the protocol version to be used to TLSv1.1. */
status = nx_secure_tls_session_protocol_version_override(&tls_session,
                                              NX_SECURE_TLS_VERSION_TLS_1_1);

/* This TLS Session will use TLSv1.1 for the handshake and TLS session. */
status = nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);
```

### <a name="see-also"></a>См. также:

- nx_secure_tls_session_start
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_receive"></a>nx_secure_tls_session_receive

Получение данных из сеанса NetX Secure TLS

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_session_receive(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба получает данные из указанного активного сеанса TLS, выполняя расшифровку этих данных перед их предоставлением вызывающему объекту в параметре NX_PACKET. Если в указанном сеансе в очереди нет данных, вызов приостанавливается в зависимости от указанного параметра ожидания.

> [!IMPORTANT]
> *Если возвращается значение NX_SUCCESS, приложение отвечает за освобождение полученного пакета, когда он больше не нужен.*

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на экземпляр сеанса TLS.
- **packet_ptr** — указатель на выделенный указатель пакета TLS.
- **wait_option** — указывает, как долго служба должна ожидать пакет от удаленного узла перед возвратом.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сеанс TLS успешно инициализирован.
- **NX_NO_PACKET** (0x01) — данные не получены.
- **NX_NOT_CONNECTED** (0x38) — базовый TCP-сокет больше не подключен.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) — полученное сообщение не прошло проверку подлинности хэша.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) — в заголовке полученного сообщения указана неизвестная версия протокола.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) — от удаленного узла получено оповещение TLS.
- **NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) — указанный сеанс TLS не инициализирован.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Receive a packet from an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is received, blocking otherwise.
*/
status =  nx_secure_tls_session_receive(&tls_session, &packet_ptr,
NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the received packet is pointed to by  "packet_ptr". */
```

### <a name="see-also"></a>См. также:

- nx_tcp_socket_receive
- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_send
- nx_secure_tls_session_end
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_renegotiate_callback_set"></a>nx_secure_tls_session_renegotiate_callback_set

Назначение обратного вызова, который будет выполняться в начале повторного согласования сеанса

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_ session_renegotiate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(struct NX_SECURE_TLS_SESSION_struct
                  *session));
```

### <a name="description"></a>Описание

Эта служба назначает обратный вызов сеансу TLS, который будет вызываться при получении первого сообщения о подтверждении повторного согласования сеанса от удаленного узла.

Функция обратного вызова предназначена для уведомления приложения о начале подтверждения повторного согласования. Приложение может завершить сеанс TLS, возвратив любое ненулевое значение из обратного вызова, которое приведет к завершению сеанса TLS с ошибкой. Если приложение продолжает повторное согласование, обратный вызов должен возвращать значение NX_SUCCESS.

> [!NOTE]
> *Из-за семантики повторного согласования TLS обратный вызов будет выполняться для клиентов NetX Secure TLS при получении HelloRequest с удаленного сервера, но не в момент инициации клиентом повторного согласования. На серверах NetX Secure TLS обратный вызов будет выполняться при каждом получении повторного согласования ClientHello (любое сообщение ClientHello, полученное в контексте активного сеанса TLS). Это означает, что обратный вызов будет выполняться независимо от того, инициировал ли повторное согласование удаленный узел или локальное приложение, так как сервер TLS отправит HelloRequest, на который будет отвечать удаленный клиент.*

NetX Secure TLS вводит в действие расширение для указания безопасного повторного согласования из документа RFC 5746, чтобы гарантировать, что подтверждения повторного согласования не будут подвергаться атакам "злоумышленник в середине".

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на экземпляр сеанса TLS.
- **func_ptr** — указатель на функцию обратного вызова.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — функция обратного вызова успешно назначена.
- **NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя для функции обратного вызова или сеанса TLS.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Simple callback notifying the user that a renegotiation is starting. */
ULONG tls_renegotiation_callback(NX_SECURE_TLS_SESSION *session)
{
    printf("Renegotiation initiated by remote host\n");

    return(NX_SUCCESS);
}

/* Establish a TLS session with a remote host (TLS Client) */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* Set callback for renegotiation notification. */
status = nx_secure_tls_session_renegotiate_callback_set(&tls_session,
                                                tls_renegotiation_callback);
```

### <a name="see-also"></a>См. также:

- nx_secure_tls_session_create
- nx_secure_tls_session_start
- nx_secure_tls_session_receive
- nx_secure_tls_session_send
- nx_secure_tls_session_renegotiate

## <a name="nx_secure_tls_session_renegotiate"></a>nx_secure_tls_session_renegotiate

Инициация подтверждения повторного согласования сеанса с удаленным узлом

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_ session_renegotiate (
                  NX_SECURE_TLS_SESSION *tls_session,
                  UINT wait_option);
```

### <a name="description"></a>Описание

Эта служба инициирует подтверждение *повторного согласования* сеанса с подключенным удаленным узлом TLS. Повторное согласование состоит из второго подтверждения TLS в контексте ранее установленного сеанса TLS. Каждое новое сообщение подтверждения шифруется с помощью сеанса TLS до создания новых ключей сеанса и обмена сообщениями ChangeCipherSpec, при этом новые ключи используются для шифрования всех сообщений.

Повторное согласование можно инициировать в любое время после установки сеанса TLS. Если повторное согласование выполняется во время подтверждения TLS или до установки сеанса TLS, никакие действия не выполняются.

> [!NOTE]
> *При вызове этой службы будет выполнено полное подтверждение TLS, поэтому время выполнения и возврата состояния будет зависеть от текущих параметров TLS и параметров сеанса.*

NetX Secure TLS вводит в действие расширение для указания безопасного повторного согласования из документа RFC 5746, чтобы гарантировать, что подтверждения повторного согласования не будут подвергаться атакам "злоумышленник в середине".

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на экземпляр сеанса TLS.
- **wait_option** — указывает, как долго служба должна ожидать пакет от удаленного узла перед возвратом. Это передается всем службам NetX в TLS.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — повторное согласование выполнено успешно.
- **NX_NO_PACKET** (0x01) — данные не получены.
- **NX_NOT_CONNECTED** (0x38) — базовый TCP-сокет больше не подключен.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) — полученное сообщение не прошло проверку подлинности хэша.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) — в заголовке полученного сообщения указана неизвестная версия протокола.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) — от удаленного узла получено оповещение TLS.
- **NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE** (0x134) — локальный или удаленный сеанс TLS неактивен, из-за чего выполнение повторного согласования невозможно.
- **NX_SECURE_TLS_RENEGOTIATION_FAILURE** (0x13A) — удаленный узел не предоставил ни SCSV, ни расширение безопасного повторного согласования, из-за чего не удалось выполнить повторное согласование.
- **NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) — указанный сеанс TLS не инициализирован.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) — не удалось выделить базовый пакет.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Establish a TLS session with a remote host (TLS Client) */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* Setup a client socket connection.  */
status = nx_tcp_client_socket_connect(&tcp_socket, server_ipv4_address,
REMOTE_SERVER_PORT, NX_WAIT_FOREVER);

/* Start the TLS session. */
status = nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);

/* Send some data in the first TLS session. (Check “status” for errors…)*/
status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                       NX_WAIT_FOREVER);
status = nx_packet_data_append(send_packet, "Hello there!\r\n", 14, &pool_0,
                               NX_WAIT_FOREVER);
status = nx_secure_tls_session_send(&tls_session, send_packet,
                                    NX_IP_PERIODIC_RATE);

/* Now renegotiate the session. */
status  = nx_secure_tls_session_renegotiate(&tls_session, NX_WAIT_FOREVER);

/* If status == NX_SUCCESS, new TLS session keys have been generated. */

/* Send some data in the new TLS session. This will be encrypted using the new
   keys. */
status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                       NX_WAIT_FOREVER);
status = nx_packet_data_append(send_packet, "Another message…\r\n", 18, &pool_0,
                               NX_WAIT_FOREVER);
status = nx_secure_tls_session_send(&tls_session, send_packet,
                                    NX_IP_PERIODIC_RATE);
```

### <a name="see-also"></a>См. также:

- nx_secure_tls_session_create
- nx_secure_tls_session_start
- nx_secure_tls_session_receive
- nx_secure_tls_session_send
- nx_secure_tls_session_renegotiation_callback_set

## <a name="nx_secure_tls_session_reset"></a>nx_secure_tls_session_reset

Очистка и сброс сеанса NetX Secure TLS

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_session_reset (NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Описание

Эта служба очищает сеанс TLS и сбрасывает состояние, как если бы сеанс был только что создан, чтобы существующий объект сеанса TLS можно было повторно использовать для нового сеанса.

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на экземпляр сеанса TLS.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сеанс TLS успешно инициализирован.
- **NX_INVALID_PARAMETERS** (0x4D) — недопустимый указатель сеанса TLS.
- **NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Reset a TLS session.  */
status =  nx_secure_tls_session_reset(&tls_session);


/* If status is NX_SUCCESS the session was successfully reset and may be reused.*/
```

### <a name="see-also"></a>См. также:

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_send"></a>nx_secure_tls_session_send

Отправка данных через сеанс NetX Secure TLS

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_session_send(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET *packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба отправляет данные в указанном NX_PACKET, используя указанный активный сеанс TLS, и выполняет шифрование этих данных перед их отправкой на удаленный узел. Если последний объявленный размер окна получателя меньше, чем этот запрос, служба при необходимости приостанавливает выполнение в соответствии с указанными параметрами ожидания.

> [!IMPORTANT]
> *Если не возвращается ошибка, приложение не должно освобождать пакет после этого вызова. Иначе это приведет к непредсказуемым результатам, так как сетевой драйвер освободит пакет после передачи*.

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на экземпляр сеанса TLS.
- **packet_ptr** — указатель на пакет TLS, содержащий данные для отправки.
- **wait_option** — определяет поведение службы в случае, если запрос превышает размер окна получателя.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сеанс TLS успешно инициализирован.
- **NX_NO_PACKET** (0x01) — данные не получены.
- **NX_NOT_CONNECTED** (0x38) — базовый TCP-сокет больше не подключен.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) — не удалось отправить данные через базовый TCP-сокет.
- **NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) — указанный сеанс TLS не инициализирован.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Send a packet using an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is sent, blocking otherwise.   */
status =  nx_secure_tls_session_send(&tls_session, &packet_ptr, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the packet has been sent. */
```

### <a name="see-also"></a>См. также:

- nx_tcp_socket_receive
- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_packet_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_receive
- nx_secure_tls_session_end
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_server_callback_set"></a>nx_secure_tls_session_server_callback_set

Настройка обратного вызова для протокола TLS для вызова в начале подтверждения сервера TLS

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_ session_server_callback_set (
                 NX_SECURE_TLS_SESSION *tls_session,
                 ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                   NX_SECURE_TLS_HELLO_EXTENSION
                                   *extensions, UINT num_extensions));
```

### <a name="description"></a>Описание

Эта служба назначает указатель функции сеансу TLS, который будет вызывать протокол TLS, если подтверждение сервера TLS получило сообщение ClientHello. Функция обратного вызова позволяет приложению обрабатывать любые расширения TLS из полученного сообщения ClientHello, для которого необходимо ввести данные или принять решение.

Обратный вызов выполняется с помощью блока управления сеансом TLS и массива объектов NX_SECURE_TLS_HELLO_EXTENSION. Массив объектов расширения необходимо передать во вспомогательную функцию, которая найдет и проанализирует определенное расширение. Пример вспомогательной функции, которая анализирует расширения TLS, предоставленные в сообщениях приветствия, см. на странице *nx_secure_tls_session_sni_extension_parse*.

Обратный вызов сервера также можно использовать для выбора активного сертификата удостоверения с помощью *nx_secure_tls_active_certificate_set* для сервера TLS. Чаще всего это происходит в ответ на расширение указания имени сервера (SNI), которое позволяет клиенту TLS указывать, какой сервер пытается связаться. Дополнительные сведения см. в справочниках по *nx_secure_tls_session_sni_extension_parse* и *nx_secure_tls_active_certificate_set*.

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.
- **func_ptr** — указатель на функцию обратного вызова сервера TLS.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное выделение указателя функции.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Application-supplied function to map server DNS name to a specific certificate
   ID. The certificate ID is supplied by the application when the certificate is
   added with nx_secure_tls_server_certificate_add. */
UINT application_find_id_by_dns_name(NX_SECURE_X509_DNS_NAME *dns_name)
{
    if(strncmp(dns_name->nx_secure_x509_dns_name, “server_name”,
               dns_name->nx_secure_x509_dns_name_length) == 0)
    {
        /* DNS name matches one we know, return it’s ID. */
        return(0x12);
    }

    /* Unknown DNS name, return 0 to indicate no matching ID found. */
    return(0);
}

/* Callback routine used to process ClientHello extensions and perform other
   runtime actions at the beginning of a TLS handshake (such as selecting an
   identify certificate to provide to the client). */
ULONG tls_server_callback(NX_SECURE_TLS_SESSION *session,
                          NX_SECURE_TLS_HELLO_EXTENSION *extensions, UINT
                          num_extensions)
{
UINT status;
NX_SECURE_X509_DNS_NAME dns_name;
UINT cert_id;
NX_SECURE_X509_CERT *certificate;


    /* Find and parse a Server Name Indication (SNI) extension. */
    status = nx_secure_tls_session_sni_extension_parse(session, extensions,
                                                       num_extensions, &dns_name);

    if(status != NX_SUCCESS && status != NX_SECURE_TLS_EXTENSION_NOT_FOUND)
    {
        /* Parsed an invalid extension, return the error. */
        return(status);
    }

    if(status == NX_SECURE_TLS_EXTENSION_NOT_FOUND)
    {
            /* SNI extension not found, just return success to use the default
               certificate. */
            return(NX_SUCCESS);
    }

    /* Find the application-supplied numeric identifier for the specified DNS
       name provided by the remote client. */
    cert_id = application_find_id_by_dns_name(&dns_name);

    /* If cert_id is 0, just use the default identity certificate added with
       nx_secure_tls_local_certificate_add. */
    if(cert_id != 0)
    {
        /* Application found a matching name, find the certificate in our
           store. */
        status = nx_secure_tls_server_certificate_find(tls_session, &certificate,
                                                       cert_id);

        if(status != NX_SUCCESS)
        {
            /* Didn’t find a valid certificate with the supplied ID. Return an
               error so TLS can shut down the handshake. */
            return(NX_SECURE_TLS_CERTIFICATE_NOT_FOUND);
        }

        /* Set the active identity certificate – the certificate should have been
           added to the local store at application start with
           nx_secure_tls_local_certificate_add. */
        nx_secure_tls_active_certificate_set(session, certificate);
    }

    return(NX_SUCCESS);
}

/* TLS setup routine. */
UINT tls_setup(NX_SECURE_TLS_SESSION *tls_session)
{
        /* Add callback to TLS session.  */
        status =  nx_secure_tls_session_server_callback_set(tls_session,
                                                            server_callback);

        /* If status is NX_SUCCESS the callback was added and will be invoked
           immediately after a ClientHello message is received. */

        return(status);
}
```

### <a name="see-also"></a>См. также:

- nx_secure_tls_session_create
- nx_secure_tls_session_client_callback_set
- nx_secure_tls_active_certificate_set
- nx_secure_tls_session_sni_extension_parse
- nx_secure_tls_server_certificate_add
- nx_secure_tls_server_certificate_find

## <a name="nx_secure_tls_session_sni_extension_parse"></a>nx_secure_tls_session_sni_extension_parse

Анализ расширения указания имени сервера (SNI), полученного от клиента TLS

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_session_sni_extension_parse(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions,
                                    UINT num_extensions,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a>Описание

Эта служба должна вызываться из обратного вызова сеанса сервера TLS, который добавляется в сеанс TLS с помощью nx_secure_tls_session_server_callback_set. Обратный вызов вызывается после получения сообщения ClientHello от удаленного клиента TLS и предоставляет массив доступных расширений (и количество расширений в массиве). Этот массив и его длину можно передать непосредственно в эту подпрограмму, чтобы определить наличие расширения SNI. Если нет, возвращается NX_SECURE_TLS_EXTENSION_NOT_FOUND, указывая, что клиент решил не использовать расширение SNI (это не ошибка).

Если обнаружено расширение SNI, то в структуре dns_name возвращается DNS-имя X.509, предоставленное клиентом TLS. Сейчас расширение SNI предоставляет только одну запись DNS-имени, которая может использоваться сервером TLS для определения сертификата удостоверения, отправляемого удаленному клиенту.**

Структура NX_SECURE_X509_DNS_NAME содержит только DNS-имя в виде строки UCHAR в поле *nx_secure_x509_dns_name* и длину строки имени в поле *nx_secure_x509_dns_name_length*. Макрос NX_SECURE_X509_DNS_NAME_MAX определяет размер буфера nx_secure_x509_dns_name.

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на экземпляр сеанса TLS.
- **extensions** — указатель на массив расширений протокола TLS Hello (из обратного вызова сеанса).
- **num_extensions** — количество расширений в массиве (из обратного вызова сеанса).
- **dns_name** — возвращает DNS-имя, заданное в расширении SNI.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное выполнение анализа расширения.
- **NX_PTR_ERROR** (0x07) — недопустимый массив расширений или указатель сеанса TLS.
- **NX_SECURE_TLS_EXTENSION_NOT_FOUND** (0x136) — расширение SNI не найдено.
- **NX_SECURE_TLS_SNI_EXTENSION_INVALID** (0x137) — недопустимый формат расширения SNI.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

### <a name="see-also"></a>См. также:

- nx_secure_tls_session_server_callback_set
- nx_secure_tls_session_client_callback_set
- nx_secure_tls_server_callback_set
- nx_secure_tls_active_certificate_set

## <a name="nx_secure_tls_session_sni_extension_set"></a>nx_secure_tls_session_sni_extension_set

Установка DNS-имени расширения указания имени сервера (SNI) для отправки на удаленный сервер

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_session_sni_extension_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a>Описание

Эта служба позволяет приложению клиента TLS предоставлять предпочитаемое DNS-имя сервера удаленному серверу TLS с помощью расширения указания имени сервера (SNI) TLS. Расширение SNI позволяет серверу выбрать правильный сертификат удостоверения и параметры на основе указанных предпочтений для сервера клиента. Сейчас расширение SNI поддерживает отправку только одного DNS-имени, поэтому параметр имени имеет единственное число. Параметр dns_name необходимо инициализировать с помощью *nx_secure_x509_dns_name_initialize* и он будет содержать предпочитаемый сервер клиента. Чтобы удалить имя расширения, просто вызовите эту службу, задав для параметра dns_name значение NX_NULL.

Структура NX_SECURE_X509_DNS_NAME содержит только DNS-имя в виде строки UCHAR в поле *nx_secure_x509_dns_name* и длину строки имени в поле *nx_secure_x509_dns_name_length*. Макрос NX_SECURE_X509_DNS_NAME_MAX определяет размер буфера nx_secure_x509_dns_name.

> [!NOTE]
> *Эту подпрограмму следует вызывать до вызова nx_secure_tls_session_start, иначе ClientHello не будет содержать расширение SNI*.

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на экземпляр сеанса TLS.
- **dns_name** — DNS-имя, предоставленное приложением.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — DNS-имя сервера успешно добавлено.
- **NX_PTR_ERROR** (0x07) — недопустимое DNS-имя или указатель сеанса TLS.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
#define TLS_SNI_SERVER_NAME “www.example.com”

NX_SECURE_X509_DNS_NAME dns_name;
NX_SECURE_TLS_SESSION client_tls_session;

/* Application where TLS session is started. */
void main()
{
    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_tls_session_create(&client_tls_session,
                                           &nx_crypto_tls_ciphers,
                                           server_crypto_metadata,
                                           sizeof(server_crypto_metadata));


    /* Initialize the DNS server name we want to send in the SNI extension. */
    nx_secure_x509_dns_name_initialize(&dns_name, TLS_SNI_SERVER_NAME,
                                    strlen(TLS_SNI_SERVER_NAME));

    /* The SNI server name needs to be set prior to starting the TLS session. */
    nx_secure_tls_session_sni_extension_set(&tls_session, &dns_name);

   /* Start TLS session as normal. */
}
```

### <a name="see-also"></a>См. также:

- nx_secure_tls_session_start
- nx_secure_x509_dns_name_initialize

## <a name="nx_secure_tls_session_start"></a>nx_secure_tls_session_start

Запуск сеанса NetX Secure TLS

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_session_start(NX_SECURE_TLS_SESSION *session_ptr,
                                  NX_TCP_SOCKET *tcp_socket_ptr,
                                  ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба запускает сеанс TLS, используя указанный блок управления сеансом TLS и подключенный TCP-сокет. TCP-соединение должно завершиться после успешного вызова nx_tcp_client_socket_connect или nx_tcp_server_socket_accept.

Эта служба определит тип сеанса TLS (клиент или сервер) из TCP-сокета.

Параметр ожидания определяет поведение службы во время подтверждения TLS.

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на экземпляр сеанса TLS.
- **tcp_socket_ptr** — указатель на подключенный TCP-сокет.
- **wait_option** — определяет поведение службы во время подтверждения TLS.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сеанс TLS успешно инициализирован.
- **NX_NOT_CONNECTED** (0x38) — базовый TCP-сокет больше не подключен.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) — получен неправильный тип сообщения TLS.
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) — шифр, предоставленный удаленным узлом, не поддерживается.
- **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) — не удалось обработать сообщение во время подтверждения TLS.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) — не удалось проверить хэш MAC во входящем сообщении.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) — не удалось отправить данные через базовый TCP-сокет.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) — входящее сообщение содержало недопустимое поле длины.
- **NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) — неправильное входящее сообщение ChangeCipherSpec.
- **NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) — входящий сертификат TLS невозможно использовать для идентификации удаленного сервера TLS.
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) — шифр с открытым ключом, предоставленный удаленным узлом, не поддерживается.
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) — на удаленном узле нет ни одного комплекта шифров, поддерживаемого стеком NetX Secure TLS.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) — в заголовке полученного сообщения TLS указана неизвестная версия TLS.
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) — в заголовке полученного сообщения TLS указана известная, но неподдерживаемая версия TLS.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) — не удалось выделить внутренний пакет TLS.
- **NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) — удаленный узел предоставил недопустимый сертификат.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) — удаленный узел отправил оповещение об ошибке и завершает сеанс TLS.
- **NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) —запись в таблице комплектов шифров содержала указатель на функцию со значением NULL.
- **NX_SECURE_TLS_INAPPROPRIATE_FALLBACK** (0x146) — удаленное ClientHello TLS включало резервное SCSV и была выполнена попытка отката версии.
- **NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
NX_TCP_SOCKET tcp_socket;
NX_SECURE_TLS_SESSION tls_session;
NX_SECURE_X509_CERT certificate;

/* Initialize the TLS session structure. */
nx_secure_tls_session_create(&tls_session,
                              &nx_crypto_tls_ciphers,
                              crypto_metadata,
                              sizeof(crypto_metadata));

/* Setup the TLS packet reassembly buffer. */
status = nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                 sizeof(tls_packet_buffer));

/* Initialize a certificate for the TLS server. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data, 500,
NX_NULL, 0, private_key, 64);

/* If status is NX_SUCCESS, certificate is initialized. */

/* Add the certificate a local certificate to identify this TLS server. */
status = nx_secure_tls_add_local_certificate(&tls_session, &certificate);

/* If status is NX_SUCCESS, certificate was added successfully. */

/* Create and start a TCP socket as a server. */
/* NOTE: This assumes an IP instance called “ip_0” has already been created. */

/* Create a TCP server socket on the previously created IP instance, with normal
   delivery, IP fragmentation enabled, default time to live, a 8192-byte receive
   window, no urgent callback routine, and the "client_disconnect" routine to
   handle disconnection initiated from the other end of the connection.  */
status =  nx_tcp_socket_create(&ip_0, &tcp_socket, "TLS Server Socket", NX_IP_NORMAL,
                               NX_FRAGMENT_OKAY, NX_IP_TIME_TO_LIVE, 8192, NX_NULL,
                               NX_NULL);

/* If status is NX_SUCCESS, the TCP socket was created successfully. */

/* Start up a TCP server socket by listening on port 443 with a listen queue of
   size 5. */
status =  nx_tcp_server_socket_listen(&ip_0, 443, &tcp_socket, 5, NX_NULL);

/* Application main loop. */
while(1)
{
        /* Accept incoming requests on the TCP socket. */
        status =  nx_tcp_server_socket_accept(&tcp_socket, NX_WAIT_FOREVER);

        /* At this point, the TCP socket should be established (but not the TLS
        session yet). */

        /* Start the TLS session on our active TCP socket. */
        status = nx_secure_tls_session_start(&tls_session, &tcp_socket,
                                             NX_WAIT_FOREVER);

        /* At this point, if status is NX_SUCCESS, the TLS session has been
           established.  Application may now send/receive data through this
           channel. */

        /* Send and receive data using the TLS session. */
        /* Allocate TLS packets using nx_secure_tls_packet_allocate, write data with
           nx_packet_data_append, read data with nx_packet_data_extract_offset. */

        /* Send TLS data. */
        nx_secure_tls_session_send(&tls_session, &send_packet, NX_WAIT_FOREVER);

        nx_secure_tls_session_receive(&tls_session, &receive_packet_ptr,
        NX_WAIT_FOREVER);


        /* Once all application data is sent/received, end the TLS session. */
        status = nx_secure_tls_session_end(&tls_session);

        /* If status is NX_SUCCESS, the TLS session has been closed properly. */

        /* Now disconnect the TCP server socket from the client.  */
        nx_tcp_socket_disconnect(&tcp_socket, 200);

        /* Unaccept the TCP server socket.  Note that unaccept is called even if
           disconnect or accept fails.  */
        nx_tcp_server_socket_unaccept(&tcp_socket);

        /* Setup server socket for listening with this socket again.  */
        nx_tcp_server_socket_relisten(&ip_0, 443, &tcp_socket);
}

/* When the server application is shut down, clean up the TLS session. */
nx_secure_tls_session_delete(&tls_session);

/* Finally, clean up the TCP socket as well. */
nx_tcp_socket_delete(&tcp_socket);
```

### <a name="see-also"></a>См. также:

- nx_tcp_socket_receive
- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_send
- nx_secure_tls_session_delete
- nx_secure_tls_session_receive
- nx_secure_tls_packet_allocate
- nx_secure_tls_session_end
- nx_secure_tls_session_create
- nx_tcp_socket_accept
- nx_tcp_socket_listen
- nx_tcp_socket_disconnect
- nx_tcp_socket_unaccept
- nx_tcp_socket_relisten
- nx_tcp_socket_delete
- nx_packet_allocate
- nx_packet_data_append
- nx_packet_data_extract_offset

## <a name="nx_secure_tls_session_time_function_set"></a>nx_secure_tls_session_time_function_set

Назначение функции метки времени в сеансе NetX Secure TLS

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_time_function_set(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              ULONG (*time_func_ptr)(void));
```

### <a name="description"></a>Описание

Эта функция устанавливает указатель функции, который будет вызываться проколом TLS, когда необходимо получить текущее время, которое используется в различных сообщениях подтверждения TLS и для проверки сертификатов.

Функция должна вернуть текущее время GMT в 32-битном формате UNIX (секунды с момента полуночи 1 января 1970 г., в формате UTC, игнорируя корректировочные секунды) согласно требованиям ClientHello в документе TLS RFC 5246.

Если функция метки времени не назначена, в подтверждении TLS для метки времени будет использоваться значение 0 и проверка истечения срока действия сертификата не будет работать.

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на экземпляр сеанса TLS.
- **time_func_ptr** — указатель на функцию, которая возвращает текущее время (GMT) в 32-битном формате UNIX.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сеанс TLS успешно инициализирован.
- **NX_INVALID_PARAMETERS** (0x4D) — недопустимый указатель сеанса TLS.
- **NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* This function returns a 32-bit UNIX-style representation of the current GMT
   time. */
ULONG get_gmt_time(void)
{
ULONG time_value;

   /* Platform-specific time calculation goes here… */

   return(time_value);
}

/* Reset a TLS session.  */
status =  nx_secure_tls_timestamp_function_set(&tls_session, get_gmt_time);


/* If status is NX_SUCCESS the function was successfully added.*/
```

### <a name="see-also"></a>См. также:

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_sendnx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_trusted_certificate_add"></a>nx_secure_tls_trusted_certificate_add

Добавление доверенного сертификата в сеансе NetX Secure TLS

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_trusted_certificate_add(NX_SECURE_TLS_SESSION
                            *session_ptr, NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a>Описание

Эта служба добавляет инициализированный экземпляр структуры NX_SECURE_X509_CERT в сеанс TLS. Этот сертификат используется в стеке TLS для проверки сертификатов, предоставляемых удаленным узлом во время подтверждения TLS.

Доверенные сертификаты необходимы для режима клиента TLS.

Доверенные сертификаты требуются только для режима сервера TLS, если включена проверка подлинности с помощью сертификата клиента.

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.
- **certificate_ptr** — указатель на инициализированный экземпляр сертификата TLS.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное добавление сертификата.
- **NX_INVALID_PARAMETERS** (0x4D) — попытка добавить недопустимый сертификат.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Initialize certificate structure. */
status = nx_secure_x509_certificate_initialize(&certificate, certificate_data,
                                               certificate_buffer,
                                               sizeof(certificate_buffer), 500,
                                               private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_trusted_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */
```

### <a name="see-also"></a>См. также:

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_trusted_certificate_remove

## <a name="nx_secure_tls_trusted_certificate_remove"></a>nx_secure_tls_trusted_certificate_remove

Удаление доверенного сертификата из сеанса NetX Secure TLS

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_tls_trusted_certificate_remove(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *common_name,
                                    UINT common_name_length);
```

### <a name="description"></a>Описание

Эта служба удаляет доверенный сертификат из сеанса TLS, введенный в поле "Общее имя" сертификата.

### <a name="parameters"></a>Параметры

- **session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.
- **common_name** — значение общего имени удаляемого сертификата.
- **common_name_length** — длина строки общего имени.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное добавление сертификата.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) — сертификат не найден.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Remove certificate from TLS session.  */
status =  nx_secure_tls_trusted_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a>См. также:

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_trusted_certificate_add

## <a name="nx_secure_x509_certificate_initialize"></a>nx_secure_x509_certificate_initialize

Инициализация сертификата X.509 для NetX Secure TLS

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_x509_certificate_initialize(
                  NX_SECURE_X509_CERT *certificate_ptr,
                  const UCHAR *certificate_data,
                  USHORT certificate_data_length,
                  UCHAR *raw_data_buffer,
                  USHORT buffer_size,
                  const UCHAR *private_key_data,
                  USHORT private_key_data_length,
                  UINT private_key_type);
```

### <a name="description"></a>Описание

Эта служба инициализирует структуру NX_SECURE_X509_CERT из цифрового сертификата X.509 в двоичной кодировке для использования в сеансе TLS.

Данные сертификата **должны** быть данными допустимого цифрового сертификата X.509 в формате двоичной кодировки DER. Любой объект может стать источником данных (например, файловая система, скомпилированный буфер констант и т. д.), если на эти данные предоставлен указатель UCHAR.

Параметр *raw_data_buffer* и его размер являются необязательными параметрами, которые указывают выделенный буфер, в который копируются данные сертификата перед синтаксическим анализом. Если raw_data_buffer передается со значением NX_NULL, то структура NX_SECURE_X509_CERT будет указывать непосредственно в массив certificate_data (в этом случае buffer_size игнорируется). Если raw_data_buffer передается со значением NX_NULL, ***не*** изменяйте данные, на которые указывает указатель certificate_data, иначе обработка сертификата, скорее всего, завершится ошибкой.

Параметр закрытого ключа предназначен для локальных сертификатов удостоверений. Закрытый ключ используется серверами для расшифровки входных данных ключа от клиента (зашифрованных с помощью открытого ключа сервера) и клиентами для проверки их удостоверений на сервере, когда сервер запрашивает сертификат клиента. При добавлении закрытого ключа с помощью этого API соответствующий сертификат автоматически помечается как сертификат удостоверения для приложения TLS. При инициализации сертификатов для других целей (например, доверенного хранилища) параметр *private_key_data* должен передаваться со значением NULL, *private_key_data_length* — с 0, а *private_key_type* — с NX_SECURE_X509_KEY_TYPE_NONE.

Параметр *private_key_type* указывает форматирование закрытого ключа. Например, если закрытый ключ является закрытым ключом RSA в формате PKCS#1 с кодировкой DER, private_key_type необходимо передавать со значением NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER. Этот тип также известен NetX Secure, как тип, который будет немедленно проанализирован и сохранен для последующего использования.

private_key_type также поддерживает определяемые пользователем типы ключей<sup>23</sup> для платформ и приложений, имеющих определенные форматы ключей или другие потребности. Например, аппаратное средство шифрования может использовать конкретный формат, не распознаваемый программным обеспечением NetX Secure, либо закрытый ключ может быть зашифрован или представлен криптографическим маркером, как это может быть в случае с таким оборудованием шифрования, как доверенный платформенный модуль (TPM) или PKCS#11. При использовании определяемого пользователем типа ключа данные ключа передаются в соответствующую криптографическую подпрограмму. Например, закрытый ключ RSA передается без какого-либо анализа или обработки непосредственно в подпрограмму шифрования RSA, предоставляемую для TLS в таблице комплектов шифров. Определяемый пользователем тип ключа также передается в подпрограммы шифрования (в случае RSA это параметр "op").

Диапазон определяемых пользователем ключей охватывает верхнюю половину 32-битного целого числа без знака от значения 0x0001 0000-0xFFFF FFFF. Значения меньше 0x0001 0000 зарезервированы для использования в NetX Secure.

Определяемые пользователем типы ключей представляют собой дополнительную возможность, требующую пользовательских криптографических подпрограмм для обработки необработанных данных закрытого ключа. Если вам нужна эта возможность, обратитесь к своему представителю Express Logic.

### <a name="parameters"></a>Параметры

- **certificate_ptr** — указатель на неинициализированный экземпляр сертификата X.509.
- **certificate_data** — указатель на двоичные данные X.509 в кодировке DER.
- **raw_data_buffer** — указатель на необязательный буфер данных выделенного сертификата.
- **buffer_size** — размер необязательного буфера данных выделенного сертификата.
- **certificate_data_length** — длина двоичных данных сертификата в байтах.
- **private_key_data** — указатель на необязательные данные закрытого ключа.
- **private_key_data_length** — длина данных закрытого ключа.
- **private_key_type** — идентификатор типа ключа.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное добавление сертификата.
- **NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.
- **NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) — данные сертификата не содержат сертификат X.509 в кодировке DER.
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) — в сертификате отсутствует шифр открытого ключа, поддерживаемый в NetX Secure.
- **NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE** (0x186) — закрытый ключ или сертификат не содержат допустимую последовательность ASN.1.
- **NX_SECURE_PKCS1_INVALID_PRIVATE_KEY** (0x18A) — предоставленный закрытый ключ не является допустимым ключом PKCS#1 RSA.
- **NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE** (0x19D) — указанный тип закрытого ключа не был определен пользователем и не соответствует ни одному известному типу.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Initialize certificate structure. The certificate structure will point directly
   into the certificate_data array since we are passing the raw_data_buffer as
   NX_NULL. This certificate has a private key so it will be used to identify this
   device. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, NX_NULL, 0, private_key, 64, NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);


/* If status is NX_SUCCESS the certificate was successfully initialized.  */
```

### <a name="see-also"></a>См. также:

- nx_secure_local_certificate_add
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- Импорт сертификатов X.509 в NetX Secure в главе 3.

## <a name="nx_secure_x509_common_name_dns_check"></a>nx_secure_x509_common_name_dns_check

Проверка DNS-имени на соответствие сертификату X.509

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_x509_common_name_dns_check(
                        NX_SECURE_X509_CERT *certificate,
                        const UCHAR *dns_tld, UINT dns_tld_length);
```

### <a name="description"></a>Описание

Эта служба проверяет общее имя сертификата на соответствие доменному имени верхнего уровня (TLD), предоставленному вызывающим объектом в целях проверки DNS удаленного узла. Эту служебную функцию должна вызывать предоставленная приложением подпрограмма обратного вызова для проверки сертификата. Имя TLD должно быть верхней частью URL-адреса, используемого для доступа к удаленному узлу (строка, разделенная "."перед первой косой чертой). Если общее имя содержит подстановочный знак (например, *.example.com), то подстановочный знак будет соответствовать любому суффиксу. Обратите внимание, что только первый обнаруженный подстановочный знак ("* ") (при чтении справа налево) будет учитываться при сопоставлении с подстановочными знаками, например abc.*.example.com будет соответствовать *любому* имени, которое заканчивается на ".example.com".

Если общее имя не совпадает с указанной строкой, то будет выполняться анализ расширения subjectAltName (если оно есть в сертификате), а также будут сравниваться все записи DNSName. Если ни одна из этих записей не совпадает с указанной строкой, возвращается ошибка.

Важно понимать, в каком формате находится общее имя (и записи subjectAltName) в ожидаемых сертификатах. Например, некоторые сертификаты могут использовать необработанный IP-адрес или подстановочный знак. Строка доменов верхнего уровня DNS должна быть отформатирована таким образом, чтоб она соответствовала ожидаемым значениям в полученных сертификатах.

### <a name="parameters"></a>Параметры

- **certificate_ptr** — указатель на экземпляр сертификата X.509.
- **dns_tld** — имя домена верхнего уровня для сравнения.
- **dns_tld_length** — длина строки TLD.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное сравнение с общим именем или subjectAltName.
- **NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH** (0x195) — соответствующее имя не найдено.
- **NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
ULONG status;
UCHAR *tld = “www.example.com”;

    /* Check our DNS TLD against the certificate provided by the
       remote TLS host. */
    status = nx_secure_x509_common_name_dns_check(certificate, tld, strlen(tld));

        if(status != NX_SUCCESS)
        {
            /* TLD did not match any names in the certificate. */
            return(status);
        }

        /* DNS validation and any other checks were successful. */
        return(NX_SUCCESS);
}

…

/* Add callback to TLS session in TLS setup routine.  */
status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                         certificate_callback);
```

### <a name="see-also"></a>См. также:

- nx_secure_tls_session_create
- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_crl_revocation_check

## <a name="nx_secure_x509_crl_revocation_check"></a>nx_secure_x509_crl_revocation_check

Проверка сертификата X.509 на соответствие заданному списку отзыва сертификатов

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_x509_crl_revocation_check(const UCHAR *crl_data,
                              UINT crl_length,
                              NX_SECURE_X509_CERTIFICATE_STORE *store,
                              NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a>Описание

Эта служба принимает список отзыва сертификатов в кодировке DER и ищет конкретный сертификат в этом списке. Издатель списка отзыва сертификатов проверяется на соответствие предоставленному хранилищу сертификатов. Издатель списка отзыва сертификатов должен совпадать с издателем проверяемого сертификата, а серийный номер рассматриваемого сертификата используется для поиска по списку отозванных сертификатов. Если издатели совпадают, подпись извлекается, а сертификат **отсутствует** в списке, вызов завершается успешно. Во всех остальных случаях возвращается ошибка.

### <a name="parameters"></a>Параметры

- **crl_data** — указатель на список отзыва сертификатов в кодировке DER.
- **crl_length** — длина данных списка отзыва сертификатов в байтах.
- **store** — указатель на хранилище сертификатов X.509.
- **certificate_ptr** — указатель на экземпляр сертификата X.509.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешная проверка того, что сертификат не был отозван.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) — сертификат издателя списка отзыва сертификатов не найден.
- **NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND** (0x11B) — сертификат издателя сертификатов не найден.
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) — список отзыва сертификатов ASN.1 содержит поле недопустимой длины.
- **NX_SECURE_X509_UNEXPECTED_ASN1_TAG** (0x189) — список отзыва сертификатов содержал недопустимый ASN.1.
- **NX_SECURE_X509_CHAIN_VERIFY_FAILURE** (0x18C) — не удалось проверить цепочку сертификатов.
- **NX_SECURE_X509_CRL_ISSUER_MISMATCH** (0x197) — список отзыва сертификатов и издатели сертификатов не совпадают.
- **NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED** (0x198) — недопустимая подпись списка отзыва сертификатов.
- **NX_SECURE_X509_CRL_CERTIFICATE_REVOKED** (0x199) — проверяемый сертификат был найден в списке отзыва сертификатов и поэтому отозван.
- **NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* CRL obtained for the expected certificate issuer through some means (downloaded
   from server manually, obtained from CRL endpoint, etc…) */
const UCHAR *crl_data;
UINT crl_length = 300;

/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
ULONG status;
NX_SECURE_X509_CERTIFICATE_STORE *store;

    /* Obtain a certificate store to check against. In the certificate callback,
       it usually makes the most sense to use the store associated with the TLS
       session. */
    store = &session -> nx_secure_tls_credentials.nx_secure_tls_certificate_store;

    /* Check our certificate against the CRL and TLS certificate store. */
    status = nx_secure_x509_crl_revocation_check(crl, crl_length, store,
                                                 certificate);

        if(status != NX_SUCCESS)
        {
            if(status == NX_SECURE_X509_CRL_CERTIFICATE_REVOKED)
            {
                /* Certificate was revoked. */
               return(status);
            }
            else
            {
               /* CRL was invalid or some other issue. In this case the certificate
                  may still be valid since the CRL itself was a problem. At this
                  point it is up to the application to decide whether to continue
                  with the TLS handshake. For this example, assume certificate is
                  valid (faulty CRL is a possible Denial-of-Service attack).*/
               status = NX_SUCCESS;
        }

    /* Other certificate checking can go here. */

    /* Return status of certificate checks. */
    return(status);
}

…

/* Add callback to TLS session in TLS setup routine.  */
status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                         certificate_callback);
```

### <a name="see-also"></a>См. также:

- nx_secure_tls_session_create
- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_common_name_dns_check

## <a name="nx_secure_x509_dns_name_initialize"></a>nx_secure_x509_dns_name_initialize

Инициализация структуры DNS-имени X.509

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_x509_dns_name_initialize(
                        NX_SECURE_X509_DNS_NAME *dns_name,
                        const UCHAR *name_string, UINT length);
```

### <a name="description"></a>Описание

Эта служба инициализирует DNS-имя X.509 для использования с определенными службами API, для которых необходим определенный формат имени. Например, служба *nx_secure_tls_sni_extension_parse* ожидает объект NX_SECURE_X509_DNS_NAME, чтобы сопоставить имя, которое предоставил удаленный узел в расширении указания имени сервера во время подтверждения TLS. DNS-имя — это просто строка символов, которая имеет длину. Максимально допустимой длиной DNS-имени (и размером внутреннего буфера в NX_SECURE_X509_DNS_NAME) управляет макрос NX_SECURE_X509_DNS_NAME_MAX (по умолчанию 100 байт).

### <a name="parameters"></a>Параметры

- **dns_name** — структура DNS-имени для инициализации.
- **name_string** — данные строки DNS-имени.
- **length** — длина строки имени.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешная инициализация.
- **NX_SECURE_X509_NAME_STRING_TOO_LONG** (0x19E) — заданная строка имени превысила значение NX_SECURE_X509_DNS_NAME_MAX.
- **NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
NX_SECURE_X509_DNS_NAME dns_name;

/* Initialize DNS name. */
status = nx_secure_x509_dns_name_initialize(&dns_name, “www.example.com”,
                                            strlen(“www.example.com”);

/* Use initialized DNS name to send the Server Name Indication extension to the
   remote TLS server. */
status = nx_secure_tls_session_sni_extension_set(&tls_session, &dns_name);
```

### <a name="see-also"></a>См. также:

- nx_secure_tls_session_create
- nx_secure_tls_session_sni_extension_parse
- nx_secure_tls_session_sni_extension_set

## <a name="nx_secure_x509_extended_key_usage_extension_parse"></a>nx_secure_x509_extended_key_usage_extension_parse

Поиск и анализ расширения расширенного использования ключа X.509 в сертификате X.509

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_x509_extended_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        UINT key_usage);
```

### <a name="description"></a>Описание

Эта служба должна вызываться из обратного вызова проверки сертификата (см. *nx_secure_tls_session_certificate_callback_set)* . Она выполнит поиск конкретного идентификатора объекта расширенного использования ключа в сертификате X.509 и возвратит сведения о том, присутствует ли этот идентификатор объекта. Параметр key_usage — это сопоставление целых чисел идентификаторов объектов, которые используются внутри NetX Secure X.509 и TLS для избежания передачи строк идентификатора объекта переменной длины в качестве параметров.

Соответствующие идентификаторы объектов для расширения расширенного использования ключа приведены в таблице ниже. В типичной реализации клиента TLS, предусматривающей проверку расширенного использования ключа в полученном сертификате сервера TLS, будет выполнена проверка наличия идентификатора объекта NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH. Если расширение есть, а не идентификатора объекта нет, сертификат будет считаться недопустимым для идентификации узла в качестве сервера TLS, а обратный вызов проверки сертификата возвратит ошибку. Приложение может выбирать, требуется ли продолжать подтверждение TLS, если само расширение отсутствует.

В обратном вызове проверки сертификата код возврата ошибки NX_SECURE_X509_KEY_USAGE_ERROR зарезервирован для использования приложением. Если при проверке использования ключа возникает ошибка, обратный вызов может возвратить это значение для указания причины сбоя.

| Идентификатор NetX Secure                                | Значение идентификатора объекта         | Описание                                      |
| --------------------------------------------------------- | --------------------- | ---------------------------------------------------- |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH   | 1.3.6.1.5.5.7.3.1 | Сертификат можно использовать для определения сервера TLS |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_CLIENT_AUTH   | 1.3.6.1.5.5.7.3.2 | Сертификат можно использовать для определения клиента TLS |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_CODE_SIGNING  | 1.3.6.1.5.5.7.3.3 | Сертификат можно использовать для подписи кода             |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_EMAIL_PROTECT | 1.3.6.1.5.5.7.3.4 | Сертификат можно использовать для подписи сообщений электронной почты           |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_TIME_STAMPING | 1.3.6.1.5.5.7.3.8 | Сертификат можно использовать для подписи меток времени       |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_OCSP_SIGNING  | 1.3.6.1.5.5.7.3.9 | Сертификат можно использовать для подписи ответов OCSP   |

Идентификаторы объектов и сопоставления для расширения расширенного использования ключа X.509

### <a name="parameters"></a>Параметры

- **certificate** — указатель на проверяемый сертификат.
- **key_usage** — сопоставление целых чисел идентификатора объекта из таблицы выше.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — указанный идентификатор объекта использования ключа найден.
- **NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) — обнаружен многобайтовый тег ASN.1 (неподдерживаемый сертификат).
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) — обнаружено недопустимое поле ASN.1 (недопустимый сертификат).
- **NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) — обнаружен недопустимый класс тегов ASN.1 (недопустимый сертификат).
- **NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) — обнаружено недопустимое расширение (недопустимый сертификат).
- **NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) — расширение расширенного использования ключа не найдено в указанном сертификате.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель сертификата.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
ULONG certificate_verification_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT* certificate)
{
UINT status;

    /* Extended key usage - look for specific OIDs. */
    status = nx_secure_x509_extended_key_usage_extension_parse(certificate,
                        NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH);

    if(status != NX_SUCCESS)
    {
        if(NX_SECURE_X509_EXT_KEY_USAGE_NOT_FOUND)
        {
            printf("Extended key usage extension not found or specified key usage OID not
                    provided in extension.\n");
            /* The certificate was valid but the specified OID was not found. The
               application can decide whether to continue or abort the TLS handshake. */
            return(NX_SECURE_X509_KEY_USAGE_ERROR);
        }
        else
        {
            /* The extension or certificate was invalid. */
            return(status);
        }
    }

    /* The specified OID was found, return success! */
    return(NX_SUCCESS);
}
```

### <a name="see-also"></a>См. также:

- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_key_usage_extension_parse
- nx_secure_x509_crl_revocation_check
- nx_secure_x509_common_name_dns_check
- nx_secure_x509_extension_find

## <a name="nx_secure_x509_extension_find"></a>nx_secure_x509_extension_find

Поиск и возврат расширения X.509 в сертификате X.509

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_x509_extension_find(
                        NX_SECURE_X509_CERT *certificate,
                        NX_SECURE_X509_EXTENSION *extension,
                        USHORT extension_id);
```

### <a name="description"></a>Описание

Эту службу следует вызывать из обратного вызова проверки сертификата (см. *nx_secure_tls_session_certificate_callback_set*). Она является расширенной службой X.509.

Функция будет искать определенное расширение в сертификате X.509 на основе идентификатора объекта и возвратит сведения о том, присутствует ли идентификатор, а также структуру, содержащую ссылки на соответствующие необработанные данные расширения. Параметр extension_id — это сопоставление целых чисел идентификаторов объектов, которые используются внутри NetX Secure X.509 и TLS для избежания передачи строк идентификатора объекта переменной длины в качестве параметров.

Вспомогательные функции для конкретных расширений (например, *nx_secure_x509_key_usage_extension_parse*) вызывают nx_secure_x509_extension_find внутренне для получения данных расширения.

Соответствующие идентификаторы объектов для известных расширений X.509 приведены в таблице ниже.

Структура NX_SECURE_X509_EXTENSION содержит указатели на сертификат X.509, которые позволяют вспомогательным функциям, таким как *nx_secure_x509_key_usage_extension_parse*, быстро декодировать необработанные данные расширения ASN.1 в кодировке DER.

Сведения о конкретных расширениях см. в документе RFC 5280 (спецификация X.509) или в справочнике по соответствующим вспомогательным функциям, если они доступны.

Текущая версия NetX Secure X.509 имеет ограниченную поддержку расширений X.509. В будущем будут добавлены дополнительные вспомогательные функции.

> [!IMPORTANT]
> *Эта служба является расширенной функцией для пользователей, знакомых с расширениями X.509 и ASN.1 в кодировке DER. Она предоставляет этим пользователям доступ к расширениям, для которых NetX Secure X.509 в данный момент не предоставляет вспомогательные функции. Для этих расширений без вспомогательных функций необходимо самостоятельно анализировать необработанный ASN.1 в кодировке DER.*

| Идентификатор NetX Secure                              | Значение идентификатора объекта | Описание                                                                    | Вспомогательная функция? |
| ------------------------------------------------------- | ------------- | ---------------------------------------------------------------------------------- | -------------------- |
| NX_SECURE_TLS_X509_TYPE_DIRECTORY_ATTRIBUTES  | 2.5.29.9  | Атрибуты каталога — это основные атрибуты сведений о субъекте сертификата  | Нет               |
| NX_SECURE_TLS_X509_TYPE_SUBJECT_KEY_ID       | 2.5.29.14 | Используется для определения конкретного открытого ключа                                         | Нет               |
| NX_SECURE_TLS_X509_TYPE_KEY_USAGE             | 2.5.29.15 | Предоставляет сведения о допустимых методах использования открытого ключа сертификата              | Да              |
| NX_SECURE_TLS_X509_TYPE_SUBJECT_ALT_NAME     | 2.5.29.17 | Предоставляет альтернативные DNS-имена для определения сертификата                     | Да<sup>24</sup>        |
| NX_SECURE_TLS_X509_TYPE_ISSUER_ALT_NAME      | 2.5.29.18 | Предоставляет альтернативные DNS-имена для определения издателя сертификата            | Нет               |
| NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS     | 2.5.29.19 | Предоставляет основные сведения об ограничении использования сертификатов                        | Нет               |
| NX_SECURE_TLS_X509_TYPE_NAME_CONSTRAINTS      | 2.5.29.30 | Используется, чтобы ограничить использование имен сертификатов до конкретных доменов                        | Нет               |
| NX_SECURE_TLS_X509_TYPE_CRL_DISTRIBUTION      | 2.5.29.31 | Предоставляет коды URI для распространения списка отзыва сертификатов                                             | Нет               |
| NX_SECURE_TLS_X509_TYPE_CERTIFICATE_POLICIES  | 2.5.29.32 | Список политик сертификатов для крупных систем PKI                             | Нет               |
| NX_SECURE_TLS_X509_TYPE_CERT_POLICY_MAPPINGS | 2.5.29.33 | Список политик сертификатов ЦС                                                | Нет               |
| NX_SECURE_TLS_X509_TYPE_AUTHORITY_KEY_ID     | 2.5.29.35 | Используется для идентификации определенного открытого ключа, связанного с подписью сертификата | Нет               |
| NX_SECURE_TLS_X509_TYPE_POLICY_CONSTRAINTS    | 2.5.29.36 | Ограничения политики ЦС                                                          | Нет               |
| NX_SECURE_TLS_X509_TYPE_EXTENDED_KEY_USAGE   | 2.5.29.37 | Дополнительные сведения об использовании ключа на основе идентификатора объекта                                     | Да              |
| NX_SECURE_TLS_X509_TYPE_FRESHEST_CRL          | 2.5.29.46 | Предоставляет сведения для получения разностных списков отзыва сертификатов                                  | Нет               |
| NX_SECURE_TLS_X509_TYPE_INHIBIT_ANYPOLICY     | 2.5.29.54 | Поле сертификата ЦС, указывающее, что AnyPolicy нельзя использовать                  | Нет               |

Идентификаторы объектов и сопоставления для расширений X.509

24. Расширение SubjectAltName анализируется как часть проверки DNS-имени в службе nx_secure_x509_common_name_dns_check.

### <a name="parameters"></a>Параметры

- **certificate** — указатель на проверяемый сертификат.
- **extension** — возвращает структуру, содержащую указатель и длину данных расширения.
- **extension_id** — сопоставление целых чисел идентификатора объекта из таблицы выше.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — указанный идентификатор объекта расширения найден, а данные возвращены.
- **NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) — обнаружен многобайтовый тег ASN.1 (неподдерживаемый сертификат).
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) — обнаружено недопустимое поле ASN.1 (недопустимый сертификат).
- **NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) — обнаружен недопустимый класс тегов ASN.1 (недопустимый сертификат).
- **NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) — обнаружено недопустимое расширение.
- **NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) — указанный идентификатор объекта расширения не найден в указанном сертификате.
- **NX_PTR_ERROR** (0x07) — недопустимый сертификат или указатель расширения.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Function to parse a Basic Constraints X.509 extension. */
UINT _basic_constraints_extension_parse(NX_SECURE_X509_CERT *certificate)
{
const UCHAR             *current_buffer;
ULONG                    length;
UINT                     status;
NX_SECURE_X509_EXTENSION extension_data;

    /* Find the Basic Constraints extension in the certificate. */
    status = _nx_secure_x509_extension_find(certificate, &extension_data,
                              NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS);

    /* See if extension present - it might be OK if not present! */
    if (status != NX_SUCCESS)
    {
        return(status);
    }

    /* The extension_data structure now points to the raw extension ASN.1
      (DER-encoded). */
    current_buffer = extension_data.nx_secure_x509_extension_data;
    length = extension_data.nx_secure_x509_extension_data_length;

   /* Extension ASN.1 parsing… */

   return(NX_SUCCESS);
}
```

### <a name="see-also"></a>См. также:

- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_key_usage_extension_parse
- nx_secure_x509_crl_revocation_check
- nx_secure_x509_common_name_dns_check
- nx_secure_x509_extended_key_usage_extension_parse

## <a name="nx_secure_x509_key_usage_extension_parse"></a>nx_secure_x509_key_usage_extension_parse

Поиск и анализ расширения использования ключа X.509 в сертификате X.509

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_x509_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        USHORT *bitfield);
```

### <a name="description"></a>Описание

Эта служба должна вызываться из обратного вызова проверки сертификата (см. *nx_secure_tls_session_certificate_callback_set)* . Она будет искать расширение использования ключа и, если оно найдено, возвратит битовое поле использования ключа в параметре bitfield.

Биты, как определено спецификацией X.509 (RFC 5280), приведены в таблице ниже. Побитовое И с соответствующей битовой маской (и проверкой на наличие ненулевого значения) предоставит значение каждому биту.

Обратите внимание, что кодировка DER битового поля устраняет лишние нули, поэтому фактическое положение битов в необработанных данных сертификата, скорее всего, будет отличаться от их положений в декодированном битовом поле. Указанные битовые маски предназначены только для использования в декодированных битовых полях, которые возвращает *nx_secure_x509_key_usage_extension_parse*, а не с необработанными данными сертификата в кодировке DER.

В обратном вызове проверки сертификата код возврата ошибки NX_SECURE_X509_KEY_USAGE_ERROR зарезервирован для использования приложением. Если при проверке использования ключа возникает ошибка, обратный вызов может возвратить это значение для указания причины сбоя.

| Идентификатор NetX Secure                            | Позиции | Описание                                                                                                                                                  |
| ----------------------------------------------------- | ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE  | 0            | Сертификат можно использовать для цифровых подписей                                                                                                               |
| NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION    | 1            | Сертификат можно использовать для проверки цифровых подписей, кроме подписей для сертификатов и списков отзыва сертификатов                                                              |
| NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT   | 2            | Сертификат можно использовать для шифрования симметричных ключей (транспорт ключей)                                                                                            |
| NX_SECURE_X509_KEY_USAGE_DATA_ENCIPHERMENT  | 3            | Сертификат можно использовать для прямого шифрования необработанных данных пользователя (редко)                                                                                         |
| NX_SECURE_X509_KEY_USAGE_KEY_AGREEMENT      | 4            | Сертификат можно использовать для согласования ключей (как в случае Диффи-Хелмана)                                                                                           |
| NX_SECURE_X509_KEY_USAGE_KEY_CERT_SIGN     | 5            | Сертификат можно использовать для подписи и проверки других сертификатов (сертификат относится к ЦС или ICA).                                                  |
| NX_SECURE_X509_KEY_USAGE_CRL_SIGN           | 6            | Открытый ключ сертификата используется для проверки подписей в списках отзыва сертификатов                                                                                                  |
| NX_SECURE_X509_KEY_USAGE_ENCIPHER_ONLY      | 7            | Используется с битом согласования ключей (бит 4). После установки ключ сертификата можно использовать только для шифрования во время согласования ключей. Значение не определено, если бит согласования ключей не установлен. |
| NX_SECURE_X509_KEY_USAGE_DECIPHER_ONLY      | 8            | Используется с битом согласования ключей (бит 4). После установки ключ сертификата можно использовать только для расшифровки во время согласования ключей. Значение не определено, если бит согласования ключей не установлен. |

Битовые маски и значения для расширения использования ключа X.509

### <a name="parameters"></a>Параметры

- **certificate** — указатель на проверяемый сертификат.
- **bitfield** — возврат всего битового поля из расширения.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — найдено расширение использования ключа и возвращено битовое поле.
- **NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) — обнаружен многобайтовый тег ASN.1 (неподдерживаемый сертификат).
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) — обнаружено недопустимое поле ASN.1 (недопустимый сертификат).
- **NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) — обнаружен недопустимый класс тегов ASN.1 (недопустимый сертификат).
- **NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) — обнаружено недопустимое расширение (недопустимый сертификат).
- **NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) — расширение использования ключа не найдено в указанном сертификате.
- **NX_PTR_ERROR** (0x07) — недопустимый сертификат или указатель битового поля.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
ULONG certificate_verification_callback(NX_SECURE_TLS_SESSION *session,
  NX_SECURE_X509_CERT* certificate)
{
UINT status;
USHORT key_usage_bitfield;

    /* Key usage – extract key usage bitfield. */
    status = nx_secure_x509_key_usage_extension_parse(certificate, &key_usage_bitfield);

   /* Check certificate for a few specific key usage bits. */
   if((key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE) == 0 ||
      (key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION)   == 0 ||
      (key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT)  == 0)
    {
        printf("Expected key usage bitfield bits not set!\n");
        return(NX_SECURE_X509_KEY_USAGE_ERROR);
    }

    /* The specified bits were set, return success! */
    return(NX_SUCCESS);
}
```

### <a name="see-also"></a>См. также:

- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_extended_key_usage_extension_parse
- nx_secure_x509_crl_revocation_check
- nx_secure_x509_common_name_dns_check
- nx_secure_x509_extension_find
