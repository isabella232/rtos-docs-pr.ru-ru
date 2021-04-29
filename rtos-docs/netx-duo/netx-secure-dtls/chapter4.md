---
title: Глава 4. Описание служб ОСРВ Azure NetX Secure DTLS
description: В этой главе приведено описание всех служб ОСРВ Azure NetX Secure DTLS, перечисленных в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e795a5fa35a4590e508c7fe2eec53f5494809657
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814512"
---
# <a name="chapter-4-description-of-azure-rtos-netx-secure-dtls-services"></a>Глава 4. Описание служб ОСРВ Azure NetX Secure DTLS

В этой главе приведено описание всех служб ОСРВ Azure NetX Secure DTLS (см. ниже), перечисленных в алфавитном порядке.

В разделе "Возвращаемые значения" в приведенных ниже описаниях API значения, **выделенные жирным шрифтом**, не обрабатываются макросом **NX_SECURE_DISABLE_ERROR_CHECKING**, который используется, чтобы отключить проверку ошибок API, в то время как для значений, не выделенных жирным шрифтом, эта проверка полностью отключена.

- [nx_secure_dtls_client_session_start](#nx_secure_dtls_client_session_start)
- [nx_secure_dtls_packet_allocate](#nx_secure_dtls_packet_allocate)
- [nx_secure_dtls_psk_add](#nx_secure_dtls_psk_add)
- [nx_secure_dtls_server_create](#nx_secure_dtls_server_create)
- [nx_secure_dtls_server_delete](#nx_secure_dtls_server_delete)
- [nx_secure_dtls_server_local_certificate_add](#nx_secure_dtls_server_local_certificate_add)
- [nx_secure_dtls_server_local_certificate_remove](#nx_secure_dtls_server_local_certificate_remove)
- [nx_secure_dtls_server_notify_set](#nx_secure_dtls_server_notify_set)
- [nx_secure_dtls_server_psk_add](#nx_secure_dtls_server_psk_add)
- [nx_secure_dtls_server_session_send](#nx_secure_dtls_server_session_send)
- [nx_secure_dtls_server_session_start](#nx_secure_dtls_server_session_start)
- [nx_secure_dtls_server_start](#nx_secure_dtls_server_start)
- [nx_secure_dtls_server_stop](#nx_secure_dtls_server_stop)
- [nx_secure_dtls_server_trusted_certificate_add](#nx_secure_dtls_server_trusted_certificate_add)
- [nx_secure_dtls_server_trusted_certificate_remove](#nx_secure_dtls_server_trusted_certificate_remove)
- [nx_secure_dtls_server_x509_client_verify_configure](#nx_secure_dtls_server_x509_client_verify_configure)
- [nx_secure_dtls_server_x509_client_verify_disable](#nx_secure_dtls_server_x509_client_verify_disable)
- [nx_secure_dtls_session_client_info_get](#nx_secure_dtls_session_client_info_get)
- [nx_secure_dtls_session_create](#nx_secure_dtls_session_create)
- [nx_secure_dtls_session_delete](#nx_secure_dtls_session_delete)
- [nx_secure_dtls_session_end](#nx_secure_dtls_session_end)
- [nx_secure_dtls_session_local_certificate_add](#nx_secure_dtls_session_local_certificate_add)
- [nx_secure_dtls_session_local_certificate_remove](#nx_secure_dtls_session_local_certificate_remove)
- [nx_secure_dtls_session_receive](#nx_secure_dtls_session_receive)
- [nx_secure_dtls_session_reset](#nx_secure_dtls_session_reset)
- [nx_secure_dtls_ session_send](#nx_secure_dtls_-session_send)
- [nx_secure_dtls_session_trusted_certificate_add](#nx_secure_dtls_session_trusted_certificate_add)
- [nx_secure_dtls_session_trusted_certificate_remove](#nx_secure_dtls_session_trusted_certificate_remove)


## <a name="nx_secure_dtls_client_session_start"></a>nx_secure_dtls_client_session_start

Запуск сеанса клиента NetX Secure DTLS.

### <a name="prototype"></a>Прототип

```C
UINT nx_secure_dtls_client_session_start(
                        NX_SECURE_DTLS_SESSION *dtls_session,
                        NX_UDP_SOCKET *udp_socket,
                        NXD_ADDRESS *ip_address, UINT port,
                        UINT wait_option);

```

### <a name="description"></a>Описание

Эта служба запускает сеанс клиента DTLS, подключаясь к серверу по указанному IP-адресу и UDP-порту с помощью предоставленного сокета UDP для сетевого взаимодействия.

Перед вызовом этой службы нужно инициализировать блок управления сеансом DTLS с помощью службы nx_secure_dtls_session_create. Кроме того, клиент DTLS требует, чтобы в сеанс был добавлен по крайней мере один сертификат доверенного ЦС с помощью nx_secure_dtls_session_trusted_certificate_add или включены и настроены общие ключи.

### <a name="parameters"></a>Параметры

- **dtls_session**: указатель на структуру сеанса DTLS, которая была инициализирована ранее.
- **udp_socket**: инициализированный сокет UDP, который будет использоваться для установления сетевого подключения к удаленному серверу DTLS.
- **ip_address**: указатель на структуру IP-адреса, содержащую адрес удаленного сервера DTLS.
- **port**: инициализированный порт, который будет использоваться для установления сетевого подключения к удаленному серверу DTLS.
- **wait_option**: параметр приостановки для попытки подключения.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): сертификат успешно назначен сеансу.
- **NX_NOT_CONNECTED** (0x38): сервер недоступен по указанному адресу и порту.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102): получен неправильный тип сообщения TLS или DTLS.
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106): шифр, предоставленный удаленным узлом, не поддерживается.
- **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107): не удалось обработать сообщение во время подтверждения TLS.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0X108): не удалось проверить хэш MAC во входящем сообщении.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109): не удалось отправить данные через базовый сокет TCP.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A): входящее сообщение содержало недопустимое поле длины.
- **NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B): неправильное входящее сообщение ChangeCipherSpec.
- **NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C): входящий сертификат TLS невозможно использовать для идентификации удаленного сервера DTLS.
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D): шифр с открытым ключом, предоставленный удаленным узлом, не поддерживается.
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0X10E): на удаленном узле нет ни одного комплекта шифров, поддерживаемого стеком NetX Secure DTLS.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F): в заголовке полученного сообщения DTLS указана неизвестная версия DTLS.
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110): в заголовке полученного сообщения DTLS указана неподдерживаемая версия DTLS.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111): не удалось выделить внутренний пакет TLS.
- **NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112): удаленный узел предоставил недопустимый сертификат.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114): удаленный узел отправил оповещение об ошибке и завершает сеанс TLS.
- **NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B): запись в таблице комплектов шифров содержала указатель на функцию со значением NULL.
- **NX_PTR_ERROR** (0x07): недопустимый указатель на сеанс, сокет или адрес.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                           &nx_crypto_tls_ciphers,
                                           crypto_metadata,
                                           sizeof(crypto_metadata),
                                           packet_buffer,
                                           sizeof(packet_buffer),
                                           REMOTE_CERT_NUMBER,
                                           remote_certs_buffer,
                                           sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
       Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                      trusted_cert_der,
                                      trusted_cert_der_len,
                                      NX_NULL, 0, NX_NULL, 0,
                                      NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                   &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                                  &udp_socket, &server_ip,
                                                  4443,
                                                  NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
      /* Error! */
      return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

    /* Receive response from server. */
    status = nx_secure_dtls_session_receive(&client_dtls_session, &receive_packet,
                                                            NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_end(&client_dtls_session, NX_IP_PERIODIC_RATE);

    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>См. также:

- nx_secure_dtls_session_receive, nx_secure_dtls_session_send
- nx_secure_dtls_session_create

## <a name="nx_secure_dtls_packet_allocate"></a>nx_secure_dtls_packet_allocate

Выделение пакета для сеанса NetX Secure DTLS.

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_dtls_packet_allocate(
                              NX_SECURE_DTLS_SESSION *session_ptr,
                         NX_PACKET_POOL *pool_ptr,
                         NX_PACKET **packet_ptr,
                              ULONG wait_option);

```

### <a name="description"></a>Описание

Эта служба выделяет пакет NX_PACKET для указанного активного сеанса DTLS из заданного пула NX_PACKET_POOL. Приложение должно вызывать эту службу для выделения пакетов данных, отправляемых через подключение DTLS. Перед вызовом данной службы необходимо инициализировать сеанс DTLS.

Выделенный пакет инициализируется таким образом, чтобы после заполнения данных пакета могли быть добавлены данные заголовка и примечания DTLS. В противном случае поведение идентично службе *nx_packet_allocate*.

### <a name="parameters"></a>Параметры

- **session_ptr**: указатель на экземпляр сеанса DTLS.
- **pool_ptr**: указатель на пул NX_PACKET_POOL, из которого выделяется пакет.
- **packet_ptr**: указатель вывода на выделенный пакет.
- **wait_option**: параметр приостановки выделения пакетов.


### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): пакет выделен успешно.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111): не удалось выделить базовый пакет.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101): указанный сеанс DTLS не инициализирован.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Allocate a new DTLS packet from the previously created packet pool and
previously initialized DTLS session.   */

status = nx_secure_dtls_packet_allocate(&dtls_session, &pool_0, &packet_ptr,
                                                              NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in
the variable packet_ptr.  */

```

### <a name="see-also"></a>См. также:

- nx_secure_x509_certificate_initialize, nx_secure_dtls_session_create
- nx_secure_dtls_session_trusted_certificate_add
- nx_secure_dtls_session_send, nx_secure_dtls_session_receive
- nx_secure_dtls_session_end, nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_psk_add"></a>nx_secure_dtls_psk_add

Добавление общего ключа в сеанс NetX Secure DTLS.

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_dtls_psk_add(NX_SECURE_DTLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a>Описание

Эта служба добавляет общий ключ (PSK), строку удостоверения и указание удостоверения в блок управления сеансом DTLS. Если включены и используются комплекты шифров PSK, то вместо цифрового сертификата используется PSK.

### <a name="parameters"></a>Параметры

- **session_ptr**: указатель на созданный ранее экземпляр сеанса DTLS.
- **pre_shared_key**: фактическое значение PSK.
- **psk_length**: длина значения PSK.
- **psk_identity**: строка, используемая для идентификации этого значения PSK.
- **identity_length**: длина удостоверения PSK.
- **hint**: строка, используемая для выбора группы PSK на сервере TLS.
- **hint_length**: длина строки указания.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): PSK успешно добавлен.
- **NX_PTR_ERROR** (0x07): недопустимый указатель на сеанс DTLS.
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0X125): невозможно добавить еще один PSK.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to DTLS session.  */
status =  nx_secure_dtls_psk_add(&dtls_session, psk,
                            sizeof(psk), “psk_1”, 4,
                            “Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */


```

### <a name="see-also"></a>См. также:

- nx_secure_dtls_server_psk_add, nx_secure_dtls_client_session_create

## <a name="nx_secure_dtls_server_create"></a>nx_secure_dtls_server_create

Создание сервера NetX Secure DTLS.

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_dtls_server_create(
                NX_SECURE_DTLS_SERVER *server_ptr, NX_IP *ip_ptr,
                UINT port, ULONG timeout, VOID *session_buffer,
                UINT session_buffer_size,
                const NX_SECURE_TLS_CRYPTO *crypto_table,
                VOID *crypto_metadata_buffer, ULONG crypto_metadata_size,
                UCHAR *packet_reassembly_buffer,
                UINT packet_reassembly_buffer_size,
                UINT (*connect_notify)(
                              NX_SECURE_DTLS_SESSION *dtls_session,
                              NXD_ADDRESS *ip_address, UINT port),
                UINT (*receive_notify)(
                              NX_SECURE_DTLS_SESSION *dtls_session)));

```

### <a name="description"></a>Описание

Эта служба создает экземпляр сервера DTLS для обработки входящих запросов DTLS на определенном UDP-порте. Так как протокол UDP не использует состояния, запросы DTLS от нескольких клиентов могут поступить на один порт, когда активны другие сеансы DTLS. Следовательно, необходим сервер для поддержания активных сеансов и правильного перенаправления входящих сообщений в соответствующий обработчик.

Параметр ip_ptr указывает на экземпляр NX_IP, который будет использоваться для внутреннего сокета UDP, связанного с сервером DTLS (и хранящегося в блоке управления NX_SECURE_DTLS_SERVER). Экземпляр IP и порт используются для определения интерфейса UDP, в котором создается экземпляр сервера службой nx_secure_dtls_server_start.

Параметр буфера сеанса используется для хранения блоков управления всех возможных одновременных сеансов DTLS для сервера DTLS. Выделяемый размер должен быть кратен размеру структуры блока управления NX_SECURE_DTLS_SESSION.

Чтобы вычислить необходимый размер метаданных, можно использовать API nx_secure_tls_metadata_size_calculate.

Параметр packet_reassembly_buffer используется протоколом DTLS для преобразования датаграмм UDP в полную запись DTLS, которая используется для расшифровки и должна быть достаточно большой, чтобы вместить самую большую запись DTLS (16 КБ — это максимальный размер записи DTLS, но многие приложения не отправляют данные такого объема в одной записи).

Процедура обратного вызова connect_notify вызывается всякий раз, когда новый клиент DTLS подключается к серверу. Приложение запускает сеанс DTLS с помощью службы *nx_secure_dtls_server_session_start*. Хотя сеанс может быть запущен в самом обратном вызове, рекомендуется использовать обратный вызов только для уведомления о потоке приложения (или выделенном потоке DTLS, созданном приложением) для подключения, так как обратный вызов выполняется потоком IP, который используется для обработки всех сетевых операций нижнего уровня (например, UDP). Это может быть не сложнее, чем просто сохранить параметр сеанса DTLS (предоставленный в качестве параметра обратного вызова) и вызвать nx_secure_dtls_server_session_start в другом потоке. Обратный вызов connect_notify обычно должен возвращать NX_SUCCESS.

Процедура обратного вызова receive_notify вызывается всякий раз, когда получена запись DTLS, которая соответствует уже установленному сеансу DTLS (IP-адрес и порт удаленного узла используются для идентификации существующего сеанса). Так представляются "данные приложения", которые шифруются и отправляются по протоколу DTLS. Приложение должно вызвать службу *nx_secure_dtls_session_receive* в предоставленном сеансе DTLS, чтобы извлечь полученные данные. Как и в случае с обратным вызовом connect_receive, рекомендуется передавать сеанс другому потоку для обработки сообщений, так как обратный вызов выполняется из потока IP. Обратный вызов receive_notify обычно должен возвращать NX_SUCCESS.

### <a name="parameters"></a>Параметры

- **server_ptr**: указатель на созданный ранее экземпляр сервера DTLS.
- **ip_ptr**: указатель на инициализированный блок управления NX_IP, используемый в качестве сетевого интерфейса сервера DTLS.
- **port**: локальный UDP-порт, к которому привязан сокет UDP сервера DTLS.
- **timeout**: значение времени ожидания сетевых операций.
- **session_buffer**: буферное пространство для хранения блоков управления всех экземпляров NX_SECURE_DTLS_SESSION, назначенных этому экземпляру сервера DTLS.
- **session_buffer_size**: размер буфера сеанса. Определяет количество сеансов DTLS, назначенных серверу DTLS.
- **crypto_table**: указатель на структуру таблицы шифрования TLS или DTLS, используемую для всех криптографических операций.
- **crypto_metadata_buffer**: буферное пространство для вычислений криптографических операций и хранения сведений о состоянии.
- **crypto_metadata_size**: размер буфера метаданных.
- **packet_reassembly_buffer**: буфер, используемый протоколом DTLS для преобразования данных UDP в записи DTLS для расшифровки.
- **packet_reassembly_buffer_size**: размер буфера преобразования данных. Обычно размер этого буфера должен быть больше 16 КБ, но он может быть меньше, что зависит от приложения.
- **connect_notify**: процедура обратного вызова, вызываемая всякий раз, когда удаленный клиент DTLS пытается подключиться к этому серверу DTLS.
- **receive_notify**: обратный вызов, выполняемый при получении данных приложения через имеющийся сеанс DTLS.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): сервер DTLS успешно создан.
- **NX_PTR_ERROR** (0x07): передан недопустимый указатель.
- **NX_INVALID_PARAMETERS** (0x4D): недостаточно пространства буфера для сеансов, повторной сборки пакетов или шифрования.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session, NXD_ADDRESS
    *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE, dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table, crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer), packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                        device_cert_der_len, NX_NULL, 0,
                        device_cert_key_der, device_cert_key_der_len,
                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);

        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                           NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
        status = nx_secure_dtls_packet_allocate(receive_dtls_session, &packet_pool,
                                                   &send_packet, NX_IP_PERIODIC_RATE);

        /* Check for errors and prepare response data
        (e.g. nx_packet_data_append). */

        /* Send response to client. */
        status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                            send_packet);

        }

        /* If not processing connections or received data,
        let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* Server processing is done, stop the server
    instance from accepting requests. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>См. также:

- nx_secure_dtls_server_start, nx_secure_dtls_server_delete
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send
- nx_secure_dtls_server_session_start
- nx_secure_dtls_server_session_stop
- nx_secure_dtls_server_local_certificate_add

## <a name="nx_secure_dtls_server_delete"></a>nx_secure_dtls_server_delete

Освобождение ресурсов, используемых сервером NetX Secure DTLS.

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_dtls_server_delete(NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a>Описание

Эта служба освобождает ресурсы, выделенные экземпляру сервера DTLS, включая внутренний сокет UDP, используемый сервером.

### <a name="parameters"></a>Параметры

- **server_ptr**: указатель на созданный ранее экземпляр сервера DTLS.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): сервер успешно удален.
- **NX_PTR_ERROR** (0x07): передан недопустимый указатель.
- **NX_STILL_BOUND** (0x42): сокет UDP все еще привязан.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session, NXD_ADDRESS
*ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                            LOCAL_SERVER_PORT,
                                            NX_IP_PERIODIC_RATE,
                                            dtls_server_session_buffer,
                                            sizeof(dtls_server_session_buffer),
                                            &tls_crypto_table,
                                            crypto_metadata_buffer,
                                            sizeof(crypto_metadata_buffer),
                                            packet_buffer, sizeof(packet_buffer),
                                            dtls_server_connect_notify,
                                            dtls_server_receive_notify);


    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                         NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
        status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                        &packet_pool,
                                                        &send_packet,
                                                        NX_IP_PERIODIC_RATE);

        /* Send response to client. */
        status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                            send_packet);

        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>См. также:

- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send
- nx_secure_dtls_server_session_start

## <a name="nx_secure_dtls_server_local_certificate_add"></a>nx_secure_dtls_server_local_certificate_add

Добавление локального удостоверяющего сертификата сервера на сервер NetX Secure DTLS.

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_dtls_server_local_certificate_add(
                                   NX_SECURE_DTLS_SERVER *server_ptr,
                                 NX_SECURE_X509_CERT *certificate,
                                 UINT cert_id);

```

### <a name="description"></a>Описание

Эта служба добавляет локальный сертификат удостоверения сервера в экземпляр сервера DTLS. Для подключения клиентов к серверу DTLS требуется по крайней мере один сертификат удостоверения, если не используется альтернативный механизм проверки подлинности (например, общие ключи).

Параметр cert_id — это числовой идентификатор сертификата, отличный от нуля. Он позволяет легко удалить сертификат или найти его в событии с несколькими сертификатами удостоверений, для которых указано одинаковое общее имя X.509 в хранилище сервера DTLS. Дополнительные сведения о сертификатах сервера X.509 см. в руководстве пользователя NetX Secure TLS.

### <a name="parameters"></a>Параметры

- **server_ptr**: указатель на созданный ранее экземпляр сервера DTLS.
- **certificate**: указатель на инициализированную ранее структуру сертификата X.509.
- **cert_ID**: отличный от нуля уникальный числовой идентификатор данного сертификата на этом сервере DTLS.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): сертификат успешно добавлен на сервер DTLS.
- **NX_PTR_ERROR** (0x07): передан недопустимый указатель.
- **NX_INVALID_PARAMETERS** (0x4D): передан идентификатор сертификата, равный 0.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

* Более полный пример доступен в справочнике по службе *nx_secure_dtls_server_create*.

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                            certificate_der_data,
                            sizeof(certificate_der_data),
                            NX_NULL, 0,
                            certificate_key_der_data,
                            sizeof(certificate_key_der_data),
                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Process incoming requests and data. */
    }

}

```

### <a name="see-also"></a>См. также:

- nx_secure_dtls_server_start, nx_secure_dtls_server_create
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send
- nx_secure_dtls_server_session_start
- nx_secure_dtls_server_local_certificate_remove
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_local_certificate_remove"></a>nx_secure_dtls_server_local_certificate_remove

Удаление локального удостоверяющего сертификата сервера с сервера NetX Secure DTLS

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_dtls_server_local_certificate_remove(
                                   NX_SECURE_DTLS_SERVER *server_ptr,
                                   UCHAR *common_name,
                                   UINT common_name_length,
                                   UINT cert_id);

```

### <a name="description"></a>Описание

Эта служба удаляет локальный сертификат удостоверения сервера из экземпляра сервера DTLS. Для подключения клиентов к серверу DTLS требуется по крайней мере один сертификат удостоверения, если не используется альтернативный механизм проверки подлинности (например, общие ключи).

Удаляемый сертификат можно идентифицировать по его общему имени X.509 или числовому значению cert_id, которое было назначено в вызове *nx_secure_dtls_server_local_certificate_add*. Значение cert_id используется только для идентификации сертификата и управляется приложением. Если вместо числового идентификатора сертификата используется общее имя, параметру cert_id должно быть присвоено значение 0.

> [!NOTE]
> Удаление сертификата во время обработки подтверждения DTLS приведет к непредвиденному поведению. Перед удалением сертификатов необходимо вызвать службу *nx_secure_dtls_server_stop*.

### <a name="parameters"></a>Параметры

- **server_ptr**: указатель на созданный ранее экземпляр сервера DTLS.
- **common_name**: общее имя X.509 сертификата, который необходимо удалить. Если используется этот параметр, присвойте параметру cert_id значение 0.
- **common_name_length**: длина common_name в байтах.
- **cert_ID**: отличный от нуля уникальный числовой идентификатор данного сертификата на этом сервере DTLS. Если используется этот параметр, присвойте значение NX_NULL параметру common_name.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): сертификат успешно удален с сервера DTLS.
- **NX_PTR_ERROR** (0x07): передан недопустимый указатель.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119): сертификат, соответствующий cert_id или common_name, не найден на данном сервере DTLS.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT, NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table, crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer), packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                        certificate_der_data,
                                        sizeof(certificate_der_data),
                                        NX_NULL, 0, certificate_key_der_data,
                                        sizeof(certificate_key_der_data),
                                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                     &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

    /* Stop the server before removing a certificate. */
    Status = nx_secure_dtls_server_stop(&dtls_server);

    /* At some point in the future we decide to remove the certificate we added.
    We can use the certificate identifier we passed into the call to
    nx_secure_dtls_local_certificate_add (value = 1); */
    status = nx_secure_dtls_server_local_certificate_remove(&dtls_server,
                                                          NX_NULL, 0, 1);

}

```

### <a name="see-also"></a>См. также:

- nx_secure_dtls_server_start, nx_secure_dtls_server_create
- nx_secure_dtls_server_session_start
- nx_secure_dtls_server_session_stop
- nx_secure_dtls_server_local_certificate_add
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_notify_set"></a>nx_secure_dtls_server_notify_set

Назначение необязательных процедур обратного вызова для уведомления серверу NetX Secure DTLS.

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_dtls_server_notify_set(
                         NX_SECURE_DTLS_SERVER *server_ptr,
                         UINT (*disconnect_notify)(
                                      NX_SECURE_DTLS_SESSION *dtls_session),
                         UINT (*error_notify)(
                                      NX_SECURE_DTLS_SESSION *dtls_session,
                                      UINT error_code));

```

### <a name="description"></a>Описание

Эту службу можно использовать для добавления на сервер DTLS необязательных процедур обратного вызова для уведомления. Если требуется только один ответный вызов, можно передать параметр обратного вызова NX_NULL.

Когда удаленный клиент завершает сеанс DTLS, выполняется обратный вызов disconnect_notify. Параметр dtls_session указывает экземпляр сеанса, который был закрыт. Обратный вызов обычно должен возвращать значение NX_SUCCESS.

Обратный вызов error_notify выполняется при возникновении ошибки или истечении времени ожидания DTLS. Параметр dtls_session указывает экземпляр сеанса, в котором произошла ошибка, а error_code — числовой код состояния ошибки, вызвавшей проблему (см. приложение А).

Ознакомьтесь со списком возвращаемых значений и кодов ошибок NetX Secure, чтобы узнать больше о возможных кодах ошибок. Обратный вызов обычно должен возвращать значение NX_SUCCESS.

### <a name="parameters"></a>Параметры

- **server_ptr**: указатель на созданный ранее экземпляр сервера DTLS.
- **disconnect_notify**: процедуры обратного вызова, вызываемые, когда удаленный клиентский узел закрывает сеанс DTLS.
- **error_notify**: процедуры обратного вызова, вызываемые при возникновении ошибки или истечении времени ожидания DTLS.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): процедуры обратного вызова успешно назначены.
- **NX_PTR_ERROR** (0x07): передан недопустимый указатель.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

UINT disconnect_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
NXD_ADDRESS client_ip_addr;
UINT client_port;
UINT local_port;

    /* We have received a disconnection notice (CloseNotify message) from a
       remote client. Application can use the dtls_session parameter for any
       desired processing. */

    /* See what client disconnected by extracting its IP address and port.
       NOTE: depending on how the session ended, the client information may
             no longer be available. */
    status  = nx_secure_dtls_session_client_info_get(dtls_session,
                                                    &ip_addr,
                                                    &client_port,
                                                    &local_port);

    return(NX_SUCCESS);
}

UINT error_notify(NX_SECURE_DTLS_SESSION *dtls_session, UINT error_code)
{
    /* The DTLS server has encountered an error or timeout condition. We
    can use the error_code parameter to determine the error and we
    can insect the dtls_session for more information. */

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table,
                                crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer),
                                packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Other setup (e.g. certificates) goes here … */

    status = nx_secure_dtls_server_notify_set(&dtls_server, disconnect_notify,
                                                                 error_notify);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

}

```

### <a name="see-also"></a>См. также:

- nx_secure_dtls_server_start, nx_secure_dtls_server_create
- nx_secure_dtls_server_session_start
- nx_secure_dtls_server_session_stop

## <a name="nx_secure_dtls_server_psk_add"></a>nx_secure_dtls_server_psk_add

Добавление общего ключа на сервер NetX Secure DTLS.

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_dtls_server_psk_add(
                                NX_SECURE_DTLS_SERVER *server_ptr,
                                UCHAR *pre_shared_key, UINT psk_length,
                                UCHAR *psk_identity,
                                UINT identity_length, UCHAR *hint,
                                UINT hint_length);

```

### <a name="description"></a>Описание

Эта служба добавляет общий ключ (PSK), строку удостоверения и указание удостоверения в блок управления сервером DTLS. Если включены и используются комплекты шифров PSK, то вместо цифрового сертификата используется PSK.

Добавленный PSK реплицируется во всех сеансах DTLS, назначенных серверу DTLS (через буфер сеанса, указанный в вызове nx_secure_dtls_server_create).

### <a name="parameters"></a>Параметры

- **server_ptr**: указатель на созданный ранее экземпляр сервера DTLS.
- **pre_shared_key**: фактическое значение PSK.
- **psk_length**: длина значения PSK.
- **psk_identity**: строка, используемая для идентификации этого значения PSK.
- **identity_length**: длина удостоверения PSK.
- **hint**: строка, используемая для выбора группы PSK на сервере TLS.
- **hint_length**: длина строки указания.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): PSK успешно добавлен.
- **NX_PTR_ERROR** (0x07): недопустимый указатель на сервер DTLS.
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0X125): невозможно добавить еще один PSK.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to DTLS session.  */
status =  nx_secure_dtls_server_psk_add(&dtls_server, psk, sizeof(psk), “psk_1”,
   4, “Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */

```

### <a name="see-also"></a>См. также:

- nx_secure_dtls_psk_add, nx_secure_dtls_server_create

## <a name="nx_secure_dtls_server_session_send"></a>nx_secure_dtls_server_session_send

Отправка данных через сеанс DTLS, установленный с помощью сервера NetX Secure DTLS.

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_dtls_server_session_send(
                                NX_SECURE_DTLS_SESSION *session_ptr,
                               NX_PACKET *packet_ptr);

```

### <a name="description"></a>Описание

Эта служба отправляет пакет данных через установленный сеанс сервера DTLS на удаленный узел клиента DTLS. Используемый сеанс передается в процедуре обратного вызова receive_notify, предоставленной службе nx_secure_dtls_session_create.

Данные в пакете, который должен быть выделен с помощью *nx_secure_dtls_packet_allocate*, шифруются с помощью криптографических параметров и процедур сеанса DTLS, а затем отправляются на удаленный узел через внутренний UDP-порт сервера DTLS на IP-адрес и порт подключенного клиента (которые хранятся в сеансе DTLS).

### <a name="parameters"></a>Параметры

- **session_ptr**: указатель на экземпляр сеанса DTLS, полученный из процедуры обратного вызова receive_notify, предоставленной приложением.
- **packet_ptr**: указатель на экземпляр NX_PACKET, выделенный ранее и заполненный данными приложения.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): сервер DTLS успешно создан.
- **NX_PTR_ERROR** (0x07): передан недопустимый указатель.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109): произошла ошибка в базовой операции отправки по протоколу UDP.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;


/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table,
                                crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer),
                                packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key
    and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                        device_cert_der,
                                        device_cert_der_len,
                                        NX_NULL,
                                        0, device_cert_key_der,
                                        device_cert_key_der_len,
                                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
        status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                &packet_pool,
                                                &send_packet,
                                                NX_IP_PERIODIC_RATE);

        /* Check for errors and prepare response data
        (e.g. nx_packet_data_append). */

        /* Send response to client. */
        status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                            send_packet);

}

/* If not processing connections or received data, let the thread sleep. */
if(!connect_flag && !receive_flag)
{
    tx_thread_sleep(100);
}
    }

    /* Server processing is done, stop the server instance
    from accepting requests. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>См. также:

- nx_secure_dtls_server_start, nx_secure_dtls_server_delete
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_create
- nx_secure_dtls_server_session_start, nx_secure_dtls_server_session_stop
- nx_secure_dtls_server_local_certificate_add

## <a name="nx_secure_dtls_server_session_start"></a>nx_secure_dtls_server_session_start

Запуск сеанса DTLS с сервера NetX Secure DTLS.

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_dtls_server_session_start(
                 NX_SECURE_DTLS_SESSION *session_ptr, UINT wait_option);

```

### <a name="description"></a>Описание

Эта служба запускает сеанс сервера DTLS, выполняя подтверждение DTLS на стороне сервера, когда удаленный клиент DTLS подключается к серверу и запрашивает подключение DTLS.

Сеанс DTLS извлекается из процедуры обратного вызова connect_notify, переданной службе nx_secure_dtls_server_create.

### <a name="parameters"></a>Параметры

- **session_ptr**: указатель на экземпляр сеанса DTLS, полученный из обратного вызова connect_notify сервера DTLS.
- **wait_option**: значение ожидания ThreadX, используемое для сетевых операций.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): сервер DTLS успешно создан.
- **NX_PTR_ERROR** (0x07): передан недопустимый указатель.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111): не удалось выделить пакет для подтверждения DTLS (пул пакетов пуст).
- **NX_SECURE_TLS_INVALID_PACKET** (0X104): получены данные, которые не являются допустимой записью DTLS.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108): не удалось правильно хэшировать запись DTLS (ошибка шифрования).
- **NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A): ошибка проверки заполнения шифрования.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0X114): во время подтверждения DTLS от удаленного узла получено оповещение.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0X102): во время подтверждения DTLS получено нераспознанное сообщение.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0X10A): получена запись DTLS с недопустимой длиной.
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0X10E): получено сообщение ClientHello, не содержащее поддерживаемых комплектов шифров DTLS.
- **NX_SECURE_TLS_BAD_COMPRESSION_METHOD** (0X118): получено сообщение ClientHello с неизвестным методом сжатия.
- **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0X107): общая (неопределенная) ошибка подтверждения, обычно возникающая из-за проблем с обработкой расширения.
- **NX_SECURE_TLS_UNSUPPORTED_FEATURE** (0x130): функция, которая еще не поддерживается, была вызвана во время подтверждения DTLS.
- **NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105): обнаружен неизвестный комплект шифров (внутренняя ошибка шифрования).
- **NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0X12E): получена запись DTLS с несоответствующей версией DTLS.
- **NX_SECURE_TLS_FINISHED_HASH_FAILURE** (0X115): не удалось проверить хэш подтверждения DTLS (недопустимый сеанс).
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109): сбой при внутренней операции отправки по протоколу UDP.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
* DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session,
                                    NXD_ADDRESS *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT, NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table, crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer), packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len, NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                        NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                    &packet_pool, &send_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
            (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                                send_packet);

        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* Server processing is done,
    stop the server instance from accepting requests. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>См. также:

- nx_secure_dtls_server_start, nx_secure_dtls_server_delete
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send
- nx_secure_dtls_server_session_create, nx_secure_dtls_server_session_stop
- nx_secure_dtls_server_local_certificate_add

## <a name="nx_secure_dtls_server_start"></a>nx_secure_dtls_server_start

Запуск экземпляра сервера NetX Secure DTLS, ожидающего передачи данных через настроенный UDP-порт.

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_dtls_server_start(
                  NX_SECURE_DTLS_SERVER *server_ptr);

```

### <a name="description"></a>Описание

Эта служба запускает сервер DTLS. После возвращения вызова сервер становится активным и начинает обрабатывать входящие запросы от клиентов DTLS. Экземпляр сервера должен быть настроен с помощью службы *nx_secure_dtls_server_create*.

> [!NOTE]
> Эта служба привязывает внутренний UDP-порт сервера DTLS к настроенному локальному порту, поэтому большинство возникающих проблем связано с обменом данными по протоколу UDP и конфигурацией сети.

### <a name="parameters"></a>Параметры

- **server_ptr**: указатель на созданный ранее экземпляр сервера DTLS.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): сервер успешно запущен.
- **NX_PTR_ERROR** (0x07): передан недопустимый указатель.
- **NX_NOT_ENABLED** (0X14): протокол UDP не включен.
- **NX_NO_FREE_PORTS** (0X45): нет доступных UDP-портов.
- **NX_INVALID_PORT** (0x46): недопустимый UDP-порт.
- **NX_ALREADY_BOUND** (0X22): UDP-порт уже привязан.
- **NX_PORT_UNAVAILABLE** (0x23): UDP-порт недоступен для использования.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session,
                                    NXD_ADDRESS *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                        &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                            NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                        NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session, &packet_pool,
                &send_packet, NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
                (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                send_packet);
        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>См. также:

- nx_secure_dtls_server_stop, nx_secure_dtls_server_create
- nx_secure_dtls_server_delete, nx_secure_dtls_session_receive
- nx_secure_dtls_server_session_send
- nx_secure_dtls_server_session_start

## <a name="nx_secure_dtls_server_stop"></a>nx_secure_dtls_server_stop

Остановка активного экземпляра сервера NetX Secure DTLS.

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_dtls_server_stop(NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a>Описание

Эта служба завершает ожидание сервером DTLS передачи данных через UDP-порт и сбрасывает все связанные сеансы DTLS, прекращая все выполняемые операции обмена данными по протоколу DTLS.

### <a name="parameters"></a>Параметры

- **server_ptr**: указатель на активный экземпляр сервера DTLS.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): сервер успешно остановлен.
- **NX_PTR_ERROR** (0x07): передан недопустимый указатель.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session,
                                    NXD_ADDRESS *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                        &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                            NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                &packet_pool,
                                                &send_packet,
                                                NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
            (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                send_packet);

        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* We have exited the processing loop, stop the server. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>См. также:

- nx_secure_dtls_server_start, nx_secure_dtls_server_create
- nx_secure_dtls_server_delete, nx_secure_dtls_session_receive
- nx_secure_dtls_server_session_send
- nx_secure_dtls_server_session_start

## <a name="nx_secure_dtls_server_trusted_certificate_add"></a>nx_secure_dtls_server_trusted_certificate_add

Добавление сертификата доверенного ЦС на сервер NetX Secure DTLS.

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_dtls_server_trusted_certificate_add(
                                         NX_SECURE_DTLS_SERVER *server_ptr,
                                         NX_SECURE_X509_CERT *certificate,
                                         UINT cert_id);

```

### <a name="description"></a>Описание

Эта служба добавляет сертификат доверенного или промежуточного ЦС в экземпляр сервера DTLS, который назначается всем внутренним сеансам сервера DTLS. Это необходимо, только если включена проверка подлинности на основе сертификата клиента X.509 с помощью службы *nx_secure_dtls_server_x509_client_verify_configure*. Добавленный сертификат будет использоваться для проверки входящих сертификатов клиента X.509.

Параметр cert_id — это числовой идентификатор сертификата, отличный от нуля. Он позволяет легко удалить сертификат или найти его в событии с несколькими сертификатами удостоверений, для которых указано одинаковое общее имя X.509 в хранилище сервера DTLS. Дополнительные сведения о сертификатах сервера X.509 см. в руководстве пользователя NetX Secure TLS.

### <a name="parameters"></a>Параметры

- **server_ptr**: указатель на созданный ранее экземпляр сервера DTLS.
- **certificate**: указатель на инициализированную ранее структуру сертификата X.509.
- **cert_ID**: отличный от нуля уникальный числовой идентификатор данного сертификата на этом сервере DTLS.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): сертификат успешно добавлен на сервер DTLS.
- **NX_PTR_ERROR** (0x07): передан недопустимый указатель.
- **NX_INVALID_PARAMETERS** (0x4D): передан идентификатор сертификата, равный 0.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

* Более полный пример доступен в справочнике по службе *nx_secure_dtls_server_create*.

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table,
                                crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer),
                                packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                            certificate_der_data,
                                            sizeof(certificate_der_data),
                                            NX_NULL, 0, NX_NULL,
                                            0, NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add trusted CA certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                            &trusted_ca_certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Process incoming requests and data. */
    }

}

```

### <a name="see-also"></a>См. также:

- nx_secure_dtls_server_start, nx_secure_dtls_server_create
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send
- nx_secure_dtls_server_session_start
- nx_secure_dtls_server_local_certificate_add
- nx_secure_dtls_server_trusted_certificate_remove
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_trusted_certificate_remove"></a>nx_secure_dtls_server_trusted_certificate_remove

Удаление сертификата доверенного ЦС с сервера NetX Secure DTLS.

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_dtls_server_trusted_certificate_remove(
                                NX_SECURE_DTLS_SERVER *server_ptr,
                                UCHAR *common_name,
                                UINT common_name_length,
                                UINT cert_id);

```

### <a name="description"></a>Описание

Эта служба удаляет сертификат доверенного ЦС из экземпляра сервера DTLS. Сертификаты доверенного ЦС необходимы только для сервера DTLS, для которого включена проверка на основе сертификата клиента X.509 путем вызова службы *nx_secure_dtls_server_x509_client_verify_configure*.

Удаляемый сертификат можно идентифицировать по его общему имени X.509 или числовому значению cert_id, которое было назначено в вызове *nx_secure_dtls_server_trusted_certificate_add*. Значение cert_id используется только для идентификации сертификата и управляется приложением. Если вместо числового идентификатора сертификата используется общее имя, параметру cert_id должно быть присвоено значение 0.

> [!NOTE]
> Удаление сертификата во время обработки подтверждения DTLS может привести к непредвиденному поведению. Перед удалением сертификатов необходимо вызвать службу *nx_secure_dtls_server_stop*.

### <a name="parameters"></a>Параметры

- **server_ptr**: указатель на созданный ранее экземпляр сервера DTLS.
- **common_name**: общее имя X.509 сертификата, который необходимо удалить. Если используется этот параметр, присвойте параметру cert_id значение 0.
- **common_name_length**: длина common_name в байтах.
- **cert_ID**: отличный от нуля уникальный числовой идентификатор данного сертификата на этом сервере DTLS. Если используется этот параметр, присвойте значение NX_NULL параметру common_name.


### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): сертификат успешно удален с сервера DTLS.
- **NX_PTR_ERROR** (0x07): передан недопустимый указатель.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119): сертификат, соответствующий cert_id или common_name, не найден на данном сервере DTLS.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                                    certificate_der_data,
                                                    sizeof(certificate_der_data),
                                                    NX_NULL, 0, NX_NULL, 0,
                                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                                       &trusted_ca_certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

    /* Stop the server before removing a certificate. */
    Status = nx_secure_dtls_server_stop(&dtls_server);


/* At some point in the future we decide to remove the certificate we added. We can
       use the certificate identifier we passed into the call to
       nx_secure_dtls_trusted_certificate_add (value = 1); */
    status = nx_secure_dtls_server_trusted_certificate_remove(&dtls_server,
                                                          NX_NULL, 0, 1);

}

```

### <a name="see-also"></a>См. также:

- nx_secure_dtls_server_start, nx_secure_dtls_server_create
- nx_secure_dtls_server_session_start
- nx_secure_dtls_server_session_stop
- nx_secure_dtls_server_trusted_certificate_add
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_x509_client_verify_configure"></a>nx_secure_dtls_server_x509_client_verify_configure

Настройка сервера NetX Secure DTLS для запроса и проверки сертификатов клиентов.

### <a name="prototype"></a>Прототип

```C
UINT nx_secure_dtls_server_x509_client_verify_configure(
                           NX_SECURE_DTLS_SERVER *server_ptr,
                               UINT certs_per_session,
                               UCHAR *certs_buffer, ULONG buffer_size);

```

### <a name="description"></a>Описание

Эта служба настраивает сервер DTLS для запроса и проверки сертификатов клиента DTLS. Эта дополнительная функция используется, когда сертификаты X.509 предпочтительнее использовать для проверки подлинности клиентов, чем другие механизмы (например, общие ключи).

> [!IMPORTANT]
> *Если сервер DTLS настроен для проверки сертификатов клиента с помощью этой службы, необходимо добавить по крайней мере один сертификат доверенного ЦС на сервер, вызвав службу nx_secure_dtls_server_trusted_certificate_add, иначе сервер будет отклонять все входящие клиентские подключения, так как не сможет проверить сертификаты клиента с помощью доверенного хранилища.*

После вызова этой службы экземпляр сервера DTLS (после запуска) будет запрашивать сертификаты клиента в ходе подтверждения DTLS. Предполагая, что для клиента правильно настроен сертификат удостоверения (и связанная цепочка сертификатов, когда это применимо), серверу DTLS потребуется выделить память для обработки данных сертификата клиента. Этот объем памяти передается в качестве параметра *certs_buffer*.

Величина certs_buffer должна соответствовать размеру самой большой цепочки сертификатов от клиента DTLS, *умноженному на количество сеансов сервера DTLS*. Этот буфер распределяется между доступными сеансами с помощью параметра *certs_per_session*, который задает максимальное ожидаемое число сертификатов в цепочке сертификатов клиента. Буфер также должен предоставить пространство для структуры данных NX_SECURE_X509_CERT, которая используется для анализа данных сертификата.

Вычислить правильный размер буфера можно с помощью следующей формулы:

```C
buffer_size = (# of DTLS sessions in server) *
                (certs_per_session) *
                (    maximum expected certificate size +
                      sizeof(NX_SECURE_X509_CERT)    )

```

- Количество сеансов DTLS определяется размером буфера сеанса, переданного в nx_secure_dtls_server_create.
- Для параметра certs_per_session должно быть задано ожидаемое максимальное число сертификатов в любой цепочке сертификатов клиента.
- Ожидаемый максимальный размер сертификата зависит от приложения, размеров ключей и других факторов, но 2 КБ обычно достаточно.

### <a name="parameters"></a>Параметры

- **server_ptr**: указатель на созданный ранее экземпляр сервера DTLS.
- **certs_per_session**: число сертификатов, выделяемых для каждого сеанса сервера DTLS.
- **certs_buffer**: пространство буфера для данных входящего сертификата.
- **buffer_size**: размер буфера сертификата.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): проверка клиента X.509 успешно настроена.
- **NX_PTR_ERROR** (0x07): передан недопустимый указатель.
- **NX_INVALID_PARAMETERS** (0X4D): недопустимое хранилище сертификатов (возможно, экземпляр сервера DTLS не инициализирован).

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Configure number of sessions per server. */
#define DTLS_SERVER_SESSIONS 3

/* Define parameters for X.509 client verification. */
#define MAX_CERT_SIZE         (2000)       /* 2KB expected maximum certificate size. */
#define CERTS_PER_SESSION (3)            /* Assume maximum chain length of 3 certificates. */
#define CERT_BUFFER_SIZE     (DTLS_SERVER_SESSIONS * CERTS_PER_SESSION * \
 (MAX_CERT_SIZE + sizeof(NX_SECURE_X509_CERT))

/* Define our incoming certificate buffer. */
UCHAR client_certs_buffer[CERT_BUFFER_SIZE];

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                    certificate_der_data,
                                    sizeof(certificate_der_data),
                                    NX_NULL, 0,
                                    NX_NULL, 0, NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                                &trusted_ca_certificate, 1);

    /* Configure client X.509 authentication and verification. */
    status = nx_secure_dtls_server_x509_client_verify_configure(&dtls_server,
        CERTS_PER_SESSION,
        client_certs_buffer,
        sizeof(client_certs_buffer));

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */
}

```

### <a name="see-also"></a>См. также:

- nx_secure_dtls_server_x509_client_verify_disable
- nx_secure_dtls_server_start, nx_secure_dtls_server_create
- nx_secure_dtls_server_session_start
- nx_secure_dtls_server_session_stop
- nx_secure_dtls_server_trusted_certificate_add
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_x509_client_verify_disable"></a>nx_secure_dtls_server_x509_client_verify_disable

Отключение проверки сертификатов клиента X.509 для сервера NetX Secure DTLS.

### <a name="prototype"></a>Прототип

```C
UINT nx_secure_dtls_server_x509_client_verify_disable(
                           NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a>Описание

Эта служба отключает проверку сертификатов клиента X.509 на сервере DTLS. Эта служба не действует, если не включена проверка на основе сертификата клиента X.509.

> [!NOTE]
> Отключение проверки подлинности клиента в активном экземпляре сервера DTLS может привести к непредсказуемому поведению. Перед изменением состояния сервера необходимо вызвать службу nx_secure_dtls_server_stop.

### <a name="parameters"></a>Параметры

- **server_ptr**: указатель на созданный ранее экземпляр сервера DTLS.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): проверка подлинности клиента X.509 успешно отключена.
- **NX_PTR_ERROR** (0x07): передан недопустимый указатель.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Configure number of sessions per server. */
#define DTLS_SERVER_SESSIONS 3

/* Define parameters for X.509 client verification. */
#define MAX_CERT_SIZE         (2000)       /* 2KB expected maximum certificate size. */
#define CERTS_PER_SESSION (3)            /* Assume maximum chain length of 3 certificates. */
#define CERT_BUFFER_SIZE     (DTLS_SERVER_SESSIONS * CERTS_PER_SESSION * \
 (MAX_CERT_SIZE + sizeof(NX_SECURE_X509_CERT))

/* Define our incoming certificate buffer. */
UCHAR client_certs_buffer[CERT_BUFFER_SIZE];

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                    certificate_der_data,
                        sizeof(certificate_der_data), NX_NULL, 0,
                        NX_NULL, 0, NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                            &trusted_ca_certificate, 1);

    /* Configure client X.509 authentication and verification. */
    status = nx_secure_dtls_server_x509_client_verify_configure(&dtls_server,
        CERTS_PER_SESSION,
        client_certs_buffer,
        sizeof(client_certs_buffer));

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

    /* Stop the server before changing state. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* Disable X.509 authentication and verification. */
    status = nx_secure_dtls_server_x509_client_verify_disable(&dtls_server);

}

```

### <a name="see-also"></a>См. также:

- nx_secure_dtls_server_x509_client_verify_configure
- nx_secure_dtls_server_start, nx_secure_dtls_server_create
- nx_secure_dtls_server_session_start
- nx_secure_dtls_server_session_stop
- nx_secure_dtls_server_trusted_certificate_add
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_session_client_info_get"></a>nx_secure_dtls_session_client_info_get

Получение сведений об удаленном клиенте из сеанса сервера DTLS.

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_dtls_session_client_info_get(
                                    NX_SECURE_DTLS_SESSION *session_ptr,
                                    NXD_ADDRESS *client_ip_address,
                                    UINT *client_port, UINT *local_port);

```

### <a name="description"></a>Описание

Эта служба возвращает сведения о сети клиента DTLS, подключенного к определенному сеансу сервера DTLS. Возвращаемые сведения содержат IP-адрес удаленного клиента и UDP-порт, а также локальный порт сервера, к которому подключен клиент.

В общем случае экземпляр сеанса DTLS будет получен в результате вызова одной из процедур обратного вызова для уведомления DTLS (например, процедуры обратного вызова connect_notify или receive_notify, переданной в nx_secure_dtls_server_create).

### <a name="parameters"></a>Параметры

- **session_ptr**: указатель на активный экземпляр сеанса сервера DTLS.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): сервер успешно удален.
- **NX_PTR_ERROR** (0x07): передан недопустимый указатель.
- **NX_INVALID_SOCKET** (0x13): недопустимый связанный сокет UDP (возможно, сеанс не инициализирован).
- **NX_NOT_CONNECTED** (0X38): сокет UDP не подключен; подключение клиента удалено или еще не установлено.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array
   or list in case a new connection is
   attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session, NXD_ADDRESS
                                                            *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    NXD_ADDRESS client_ip;
    UINT client_port, server_port;

    /* Get DTLS client information which can be used in filtering or associating
       the DTLS session with application data (e.g. a session pointer table). */
    status = nx_secure_dtls_session_client_info_get(dtls_session, &client_ip,
   &client_port, &server_port);

    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                            LOCAL_SERVER_PORT,
                                            NX_IP_PERIODIC_RATE,
                                            dtls_server_session_buffer,
                                            sizeof(dtls_server_session_buffer),
                                            &tls_crypto_table,
                                            crypto_metadata_buffer,
                                            sizeof(crypto_metadata_buffer),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            dtls_server_connect_notify,
                                            dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                            device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                        &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                            NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                &packet_pool,
                                                &send_packet,
                                                NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
            (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                send_packet);
        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>См. также:

- nx_secure_dtls_server_start, nx_secure_dtls_server_stop
- nx_secure_dtls_server_create, nx_secure_dtls_server_delete
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send
- nx_secure_dtls_server_session_start

## <a name="nx_secure_dtls_session_create"></a>nx_secure_dtls_session_create

Создание и настройка сеанса NetX Secure DTLS.

### <a name="prototype"></a>Прототип

```C
UINT nx_secure_dtls_session_create(
                        NX_SECURE_DTLS_SESSION *dtls_session,
                        const NX_SECURE_TLS_CRYPTO *crypto_table,
                        VOID *metadata_buffer, ULONG metadata_size,
                        UCHAR *packet_reassembly_buffer,
                        UINT packet_reassembly_buffer_size,
                        UINT certs_number,
                        UCHAR *remote_certificate_buffer,
                        ULONG remote_certificate_buffer_size));

```

### <a name="description"></a>Описание

Эта служба создает и настраивает сеанс DTLS. Как правило, она используется для создания сеансов клиента DTLS, так как сеансами сервера DTLS управляет механизм сервера DTLS (см. описание службы *nx_secure_dtls_server_create*), но возможны случаи, в которых приложению необходимо создать единственный изолированный экземпляр сеанса сервера DTLS, для чего можно использовать эту службу<sup>7</sup>.

Параметры определяют сведения и выделение памяти, необходимые для создания экземпляра сеанса DTLS. Параметр crypto_table указывает таблицу TLS, содержащую все криптографические процедуры, необходимые для шифрования и проверки подлинности TLS или DTLS. Параметр metadata_buffer используется для вычислительных операций шифрования (см. описание службы nx_secure_tls_metadata_size_calculate в руководстве пользователя NetX Secure TLS), а параметр packet_reassembly_buffer используется для преобразования датаграмм UDP в полные записи DTLS для расшифровки.

Параметры certs_number и remote_certificate_buffer необходимы для клиентов DTLS, которым требуется пространство для хранения и обработки входящей цепочки сертификатов сервера DTLS. Буфер должен вмещать ожидаемый максимальный размер цепочки сертификатов для любого сервера, к которому будет подключаться клиент. Буфер распределяется между всеми ожидаемыми сертификатами (их число задает параметр certs_number). Он должен быть достаточно большим, чтобы вместить одну структуру NX_SECURE_X509_CERT на сертификат. Размер буфера можно определить с помощью следующей формулы:

```C
remote_certificate_buffer_size = (certs_number) *
                 (maximum cert size + sizeof(NX_SECURE_X509_CERT))
```

- Параметр certs_number задает ожидаемое максимальное число сертификатов в цепочке сертификатов сервера.
- Максимальный размер сертификата зависит от размера используемых ключей и сведений в сертификате, но 2 КБ обычно достаточно.

**7** Создание сеансов сервера DTLS с помощью этой процедуры не рекомендуется и связано с определенными ограничениями. Основной проблемой является то, что сеанс не будет корректно работать с дополнительными подключениями клиентов. Так как протокол UDP не зависит от подключения, а второй клиент вполне может отправить данные на UDP-порт сервера, пока предыдущий сеанс DTLS еще активен, это вызовет завершение сбоем сеанса сервера.

### <a name="parameters"></a>Параметры

- **dtls_session**: указатель на неинициализированную структуру сеанса DTLS.
- **crypto_table**: указатель на структуру таблицы шифрования TLS или DTLS, используемую для всех криптографических операций.
- **crypto_metadata_buffer**: буферное пространство для вычислений криптографических операций и хранения сведений о состоянии.
- **crypto_metadata_size**: размер буфера метаданных.
- **packet_reassembly_buffer**: буфер, используемый протоколом DTLS для преобразования данных UDP в записи DTLS для расшифровки.
- **packet_reassembly_buffer_size**: размер буфера преобразования данных. Обычно размер этого буфера должен быть больше 16 КБ, но он может быть меньше, что зависит от приложения.
- **certs_number**: ожидаемое максимальное число сертификатов в цепочке сертификатов удаленного сервера.
- **remote_certificate_buffer**: пространство буфера для данных входящего сертификата.
- **remote_certificate_buffer_size**: размер буфера сертификата.


### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): сеанс успешно создан.
- **NX_PTR_ERROR** (0x07): недопустимый указатель на сеанс или буфер.
- **NX_INVALID_PARAMETERS** (0x4D): недостаточно пространства буфера для повторной сборки пакетов, сертификатов или шифрования.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len,
                                    NX_NULL, 0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
    &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                            &udp_socket, &server_ip,
                                            4443,
                                            NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session,
                                                &send_packet,
                                                &server_ip, 4443);

    /* Receive response from server. */
    status = nx_secure_dtls_session_receive(&client_dtls_session,
                                            &receive_packet,
                                            NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
        status = nx_secure_dtls_session_end(&client_dtls_session,
                                            NX_IP_PERIODIC_RATE);

    /* Clean up. */
        status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>См. также:

- nx_secure_dtls_client_session_start,nx_secure_dtls_session_receive
- nx_secure_dtls_session_send

## <a name="nx_secure_dtls_session_delete"></a>nx_secure_dtls_session_delete

Освобождение ресурсов, используемых сеансом NetX Secure DTLS.

### <a name="prototype"></a>Прототип

```C
UINT nx_secure_dtls_session_delete(
                        NX_SECURE_DTLS_SESSION *dtls_session);

```

### <a name="description"></a>Описание

Эта служба удаляет сеанс DTLS, освобождая все ресурсы, которые были выделены при его создании.

### <a name="parameters"></a>Параметры

- **dtls_session**: указатель на структуру сеанса DTLS, которая была инициализирована ранее.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): сеанс успешно удален.
- **NX_PTR_ERROR** (0x07): недопустимый указатель на сеанс или буфер.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                        trusted_cert_der,
                                        trusted_cert_der_len,
                                        NX_NULL, 0, NX_NULL, 0,
                                        NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                                    &udp_socket,
                                                    &server_ip, 4443,
                                                    NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

        /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                &receive_packet,
                                                NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
        status = nx_secure_dtls_session_end(&client_dtls_session,
                                            NX_IP_PERIODIC_RATE);

    /* Clean up. */
        status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>См. также:

- nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive
- nx_secure_dtls_session_send, nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_session_end"></a>nx_secure_dtls_session_end

Завершение активного сеанса NetX Secure DTLS.

### <a name="prototype"></a>Прототип

```C
UINT nx_secure_dtls_session_end(NX_SECURE_DTLS_SESSION *dtls_session,
                                UINT wait_option);

```

### <a name="description"></a>Описание

Эта служба завершает активный сеанс DTLS, отправляя оповещение CloseNotify (TLS или DTLS) на удаленный узел. Используются IP-адрес и порт, указанные в предыдущем вызове nx_secure_dtls_session_send.

### <a name="parameters"></a>Параметры

- **dtls_session**: указатель на структуру сеанса DTLS, которая была инициализирована ранее.
- **wait_option**: значение ожидания ThreadX, используемое для сетевых операций.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): сеанс успешно удален.
- **NX_PTR_ERROR** (0x07): недопустимый указатель на сеанс или буфер.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111): не удалось выделить пакеты для оповещения CloseNotify.
- **NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105): возможно, внутренняя ошибка; не распознана криптографическая процедура.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109): сбой при базовой операции отправки по протоколу UDP.
- **NX_IP_ADDRESS_ERROR** (0x21): ошибка из-за IP-адреса удаленного узла.
- **NX_NOT_BOUND** (0X24): базовый сокет UDP не привязан к порту.
- **NX_INVALID_PORT** (0x46): недопустимый UDP-порт.
- **NX_PORT_UNAVAILABLE** (0x23): UDP-порт недоступен для использования.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
            Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session,
                                                &send_packet,
                                                &server_ip, 4443);

    /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_end(&client_dtls_session,
                                        NX_IP_PERIODIC_RATE);

    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

    }

```

### <a name="see-also"></a>См. также:

- nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive
- nx_secure_dtls_session_send, nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_session_local_certificate_add"></a>nx_secure_dtls_session_local_certificate_add

Добавление локального удостоверяющего сертификата в сеанс NetX Secure DTLS.

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_dtls_session_local_certificate_add(
                            NX_SECURE_DTLS_SESSION *session_ptr,
                            NX_SECURE_X509_CERT *certificate,
                            UINT cert_id);

```

### <a name="description"></a>Описание

Эта служба добавляет локальный сертификат удостоверения в экземпляр сеанса DTLS. В общем случае эта служба используется, когда сеансу клиента DTLS требуется предоставить сертификат удостоверения для узла удаленного сервера. Это необязательная конфигурация для протокола DTLS, поэтому сертификат для клиентов DTLS, как правило, не требуется. Для сертификата удостоверения требуется связанный закрытый ключ.

Параметр cert_id — это числовой идентификатор сертификата, отличный от нуля. Он позволяет легко удалить сертификат или найти его в событии с несколькими сертификатами удостоверений, для которых указано одинаковое общее имя X.509 в хранилище сертификатов DTLS. Дополнительные сведения о сертификатах X.509 см. в руководстве пользователя NetX Secure TLS.

### <a name="parameters"></a>Параметры

- **session_ptr**: указатель на созданный ранее экземпляр сеанса DTLS.
- **certificate**: указатель на инициализированную ранее структуру сертификата X.509.
- **cert_ID**: отличный от нуля уникальный числовой идентификатор данного сертификата на этом сервере DTLS.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): сертификат успешно добавлен в сеанс DTLS.
- **NX_PTR_ERROR** (0x07): передан недопустимый указатель.
- **NX_INVALID_PARAMETERS** (0x4D): передан идентификатор сертификата, равный 0.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

* Более полный пример доступен в справочнике по службе *nx_secure_dtls_session_create*.

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data. Identity
certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

/* Create a TLS session for our socket. Ciphers and metadata defined
   elsewhere. See nx_secure_tls_session_create reference for more
   information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
{
    printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
}

/* Initialize our trusted certificate. See section “Importing X.509
   Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len,
                                    NX_NULL, 0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

/* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                              &certificate, 1);

    /* Initialize local server identity certificate with key and
    add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                        certificate_der_data,
                        sizeof(certificate_der_data),
                        NX_NULL, 0,
                        certificate_key_der_data,
                        sizeof(certificate_key_der_data),
                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                    &certificate, 1);

/* Set up IP address of remote host. */
server_ip.nxd_ip_version = NX_IP_VERSION_V4;
server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


/* Now we can start the DTLS session as normal. */
status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                    &udp_socket, &server_ip, 4443,
                                    NX_IP_PERIODIC_RATE);


    /* Process responses, etc…*/
}

```

### <a name="see-also"></a>См. также:

- nx_secure_dtls_session_create, nx_secure_dtls_session_receive
- nx_secure_dtls_session_send, nx_secure_dtls_session_start
- nx_secure_dtls_session_local_certificate_remove
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_session_local_certificate_remove"></a>nx_secure_dtls_session_local_certificate_remove

Удаление локального удостоверяющего сертификата из сеанса NetX Secure DTLS

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_dtls_session_local_certificate_remove(
                                         NX_SECURE_DTLS_SESSION *session_ptr,
                                         UCHAR *common_name,
                                         UINT common_name_length, UINT cert_id);

```

### <a name="description"></a>Описание

Эта служба удаляет локальный сертификат удостоверения из экземпляра сеанса DTLS, используя идентификационный номер сертификата (назначенный при добавлении сертификата с помощью службы nx_secure_dtls_session_local_certificate_add) или поле общего имени X.509, CommonName.

Если для сопоставления сертификатов используется параметр common_name, то параметру cert_id должно быть присвоено значение 0. Если используется параметр cert_id, то параметру common_name должно быть присвоено значение NX_NULL.

Параметр cert_id — это числовой идентификатор сертификата, отличный от нуля. Он позволяет легко удалить сертификат или найти его в событии с несколькими сертификатами удостоверений, для которых указано одинаковое общее имя X.509 в хранилище сертификатов DTLS. Дополнительные сведения о сертификатах X.509 см. в руководстве пользователя NetX Secure TLS.

### <a name="parameters"></a>Параметры

- **session_ptr**: указатель на созданный ранее экземпляр сеанса DTLS.
- **common_name**: указатель на строку CommonName для сопоставления.
- **common_name_length**: длина строки common_name.
- **cert_ID**: отличный от нуля уникальный числовой идентификатор данного сертификата на этом сервере DTLS.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): сертификат успешно удален из сеанса DTLS.
- **NX_PTR_ERROR** (0x07): передан недопустимый указатель.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119): сертификат, соответствующий cert_id или common_name, не найден в данном сеансе DTLS.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

* Более полный пример доступен в справочнике по службе *nx_secure_dtls_session_create*.

```C

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data.
Identity certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
        nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                            &certificate, 1);

        /* Initialize local server identity certificate with key
        and add to server. */
        status = nx_secure_x509_certificate_initialize(&certificate,
                                certificate_der_data,
                                sizeof(certificate_der_data),
                                NX_NULL, 0,
                                certificate_key_der_data,
                                sizeof(certificate_key_der_data),
                                NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

        /* Add local server identity certificate to DTLS server with ID of 1. */
        status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                            &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
        &udp_socket, &server_ip, 4443,
        NX_IP_PERIODIC_RATE);

        /* Process responses, etc…*/

    /* At some point in the future,
    we decide to remove the certificate using the ID of 1
    when it was added to the session. */
        status = nx_secure_dtls_session_local_certificate_remove(&client_dtls_session,
                                                                NX_NULL, 0, 1);
}

```

### <a name="see-also"></a>См. также:

- nx_secure_dtls_session_create, nx_secure_dtls_session_receive
- nx_secure_dtls_session_send, nx_secure_dtls_session_start
- nx_secure_dtls_session_local_certificate_add
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_session_receive"></a>nx_secure_dtls_session_receive

Получение данных приложения через установленный сеанс NetX Secure DTLS.

### <a name="prototype"></a>Прототип

```C
UINT nx_secure_dtls_session_receive(
                                NX_SECURE_DTLS_SESSION *dtls_session,
                                NX_PACKET **packet_ptr_ptr,
                                UINT wait_option);

```

### <a name="description"></a>Описание

Эта служба возвращает данные приложения, полученные активным сеансом DTLS. Это может быть либо сеанс сервера DTLS (управляемый экземпляром сервера DTLS), либо сеанс клиента DTLS. Возвращаемый пакет может обрабатываться с помощью любой из служб API NX_PACKET (дополнительные сведения см. в документации по NetX).

### <a name="parameters"></a>Параметры

- **dtls_session**: указатель на структуру сеанса DTLS, которая была инициализирована ранее.
- **packet_ptr_ptr**: указатель на указатель NX_PACKET для возвращаемого пакета.
- **wait_option**: значение ожидания ThreadX, используемое для сетевых операций.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): пакет данных приложения успешно получен.
- **NX_PTR_ERROR** (0x07): недопустимый указатель на сеанс или пакет.
- **NX_NOT_ENABLED** (0X14): протокол UDP не включен.
- **NX_NOT_BOUND** (0X24): сокет UDP не привязан к порту.
- **NX_SECURE_TLS_INVALID_PACKET** (0X104): получены данные, которые не являются допустимой записью DTLS.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108): не удалось правильно хэшировать запись DTLS (ошибка шифрования).
- **NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A): ошибка проверки заполнения шифрования.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0X114): от удаленного узла получено оповещение.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0X102): получено нераспознанное сообщение.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0X10A): получена запись DTLS с недопустимой длиной.
- **NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105): обнаружен неизвестный комплект шифров (внутренняя ошибка шифрования).
- **NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0X12E): получена запись DTLS с несоответствующей версией DTLS.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
    printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
            Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

    /* Receive response from server. */
    status = nx_secure_dtls_session_receive(&client_dtls_session, &receive_packet,
                                                            NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_end(&client_dtls_session, NX_IP_PERIODIC_RATE);

    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>См. также:

- nx_secure_dtls_client_session_start, nx_secure_dtls_session_end
- nx_secure_dtls_session_send, nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_session_reset"></a>nx_secure_dtls_session_reset

Очистка данных в экземпляре сеанса NetX Secure DTLS.

### <a name="prototype"></a>Прототип

```C
UINT nx_secure_dtls_session_reset(NX_SECURE_DTLS_SESSION *dtls_session);
```

### <a name="description"></a>Описание

Эта служба сбрасывает сеанс DTLS, удаляя все временные криптографические данные и позволяя повторно использовать структуру для нового сеанса. Постоянные данные (например, хранилища сертификатов) сохраняются, чтобы службу nx_secure_dtls_session_create не нужно было вызывать повторно.

### <a name="parameters"></a>Параметры

- **dtls_session**: указатель на структуру сеанса DTLS, которая была инициализирована ранее.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): сеанс успешно сброшен.
- **NX_PTR_ERROR** (0x07): недопустимый указатель на сеанс или буфер.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
    printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
            Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

    /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_reset(&client_dtls_session);

    /* A new session can now be started using the same structure. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,



    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>См. также:

- nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive
- nx_secure_dtls_session_send, nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_-session_send"></a>nx_secure_dtls_ session_send

Отправка данных через сеанс DTLS.

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_dtls_session_send(NX_SECURE_DTLS_SESSION *session_ptr,
                                          NX_PACKET *packet_ptr,
                                          NXD_ADDRESS *ip_address, UINT port);

```

### <a name="description"></a>Описание

Эта служба отправляет пакет данных через установленный сеанс DTLS на удаленный узел DTLS, используя заданные IP-адрес и порт. Для этого используется активный сеанс клиента DTLS. Обратите внимание на то, что IP-адрес и порт предоставляются ввиду особенностей протокола UDP, в котором состояния не сохраняются, но в общем случае они должны соответствовать адресу и порту, используемым в службе nx_secure_dtls_session_start для запуска сеанса.

Данные в пакете, который должен быть выделены с помощью службы *nx_secure_dtls_packet_allocate*, шифруются с помощью криптографических параметров и процедур сеанса DTLS, а затем отправляются на удаленный узел через сокет UDP сеанса DTLS.

### <a name="parameters"></a>Параметры

- **session_ptr**: указатель на активный экземпляр сеанса клиента DTLS.
- **packet_ptr**: указатель на экземпляр NX_PACKET, выделенный ранее и заполненный данными приложения.
- **ip_address**: указатель на структуру NXD_ADDRESS, содержащую IP-адрес удаленного узла.
- **port**: UDP-порт на удаленном узле.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): пакет успешно отправлен.
- **NX_PTR_ERROR** (0x07): передан недопустимый указатель.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109): произошла ошибка в базовой операции отправки по протоколу UDP.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
    /* Error! */
    return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

        /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
        status = nx_secure_dtls_session_end(&client_dtls_session,
                                            NX_IP_PERIODIC_RATE);

    /* Clean up. */
        status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>См. также:

- nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive
- nx_secure_dtls_session_create

## <a name="nx_secure_dtls_session_trusted_certificate_add"></a>nx_secure_dtls_session_trusted_certificate_add

Добавление сертификата доверенного ЦС в сеанс NetX Secure DTLS.

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_dtls_session_trusted_certificate_add(
                                         NX_SECURE_DTLS_SESSION *session_ptr,
                                         NX_SECURE_X509_CERT *certificate,
                                         UINT cert_id);

```

### <a name="description"></a>Описание

Эта служба добавляет сертификат доверенного или промежуточного ЦС X.509 в экземпляр сеанса DTLS. Клиент DTLS должен иметь по крайней мере один доверенный сертификат для проверки сертификатов удаленных серверов, если не используется альтернативный механизм проверки подлинности (например, общие ключи). Доверенный сертификат обычно не имеет закрытого ключа.

Параметр cert_id — это числовой идентификатор сертификата, отличный от нуля. Он позволяет легко удалить сертификат или найти его в событии с несколькими сертификатами удостоверений, для которых указано одинаковое общее имя X.509 в хранилище сертификатов DTLS. Дополнительные сведения о сертификатах X.509 см. в руководстве пользователя NetX Secure TLS.

### <a name="parameters"></a>Параметры

- **session_ptr**: указатель на созданный ранее экземпляр сеанса DTLS.
- **certificate**: указатель на инициализированную ранее структуру сертификата X.509.
- **cert_ID**: отличный от нуля уникальный числовой идентификатор данного сертификата на этом сервере DTLS.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): сертификат успешно добавлен в сеанс DTLS.
- **NX_PTR_ERROR** (0x07): передан недопустимый указатель.
- **NX_INVALID_PARAMETERS** (0x4D): передан идентификатор сертификата, равный 0.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

* Более полный пример доступен в справочнике по службе *nx_secure_dtls_session_create*.

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data.
Identity certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
   Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                            trusted_cert_der,
                                            trusted_cert_der_len,
                                            NX_NULL, 0, NX_NULL, 0,
                                            NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the trusted store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                      &certificate, 1);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                            certificate_der_data,
                                            sizeof(certificate_der_data),
                                            NX_NULL, 0,
                                            certificate_key_der_data,
                                            sizeof(certificate_key_der_data),
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);

    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
         &udp_socket, &server_ip, 4443,
         NX_IP_PERIODIC_RATE);


    /* Process responses, etc…*/
}

```

### <a name="see-also"></a>См. также:

- nx_secure_dtls_session_create, nx_secure_dtls_session_receive
- nx_secure_dtls_session_send, nx_secure_dtls_session_start
- nx_secure_dtls_session_trusted_certificate_remove
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_session_trusted_certificate_remove"></a>nx_secure_dtls_session_trusted_certificate_remove

Удаление сертификата доверенного ЦС из сеанса NetX Secure DTLS.

### <a name="prototype"></a>Прототип

```C
UINT  nx_secure_dtls_session_trusted_certificate_remove(
                            NX_SECURE_DTLS_SESSION *session_ptr,
                            UCHAR *common_name,
                            UINT common_name_length, UINT cert_id);

```

### <a name="description"></a>Описание

Эта служба удаляет сертификат доверенного ЦС из экземпляра сеанса DTLS, используя идентификационный номер сертификата (назначенный при добавлении сертификата с помощью службы nx_secure_dtls_session_local_certificate_add) или поле общего имени X.509, CommonName.

Если для сопоставления сертификатов используется параметр common_name, то параметру cert_id должно быть присвоено значение 0. Если используется параметр cert_id, то параметру common_name должно быть присвоено значение NX_NULL.

Параметр cert_id — это числовой идентификатор сертификата, отличный от нуля. Он позволяет легко удалить сертификат или найти его в событии с несколькими сертификатами удостоверений, для которых указано одинаковое общее имя X.509 в хранилище сертификатов DTLS. Дополнительные сведения о сертификатах X.509 см. в руководстве пользователя NetX Secure TLS.

### <a name="parameters"></a>Параметры

- **session_ptr**: указатель на созданный ранее экземпляр сеанса DTLS.
- **common_name**: указатель на строку CommonName для сопоставления.
- **common_name_length**: длина строки common_name.
- **cert_ID**: отличный от нуля уникальный числовой идентификатор данного сертификата на этом сервере DTLS.


### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): сертификат успешно удален из сеанса DTLS.
- **NX_PTR_ERROR** (0x07): передан недопустимый указатель.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119): сертификат, соответствующий cert_id или common_name, не найден в данном сеансе DTLS.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

* Более полный пример доступен в справочнике по службе *nx_secure_dtls_session_create*.

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data. Identity certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL, 0,
                                    NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
        nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                            &certificate, 1);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                            certificate_der_data,
                                            sizeof(certificate_der_data),
                                            NX_NULL, 0,
                                            certificate_key_der_data,
                                            sizeof(certificate_key_der_data),
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    /* Process responses, etc…*/

    /* At some point in the future,
    we decide to remove the certificate using the ID of 1
    when it was added to the session. */
    status = nx_secure_dtls_session_trusted_certificate_remove(&client_dtls_session,
                                                                    NX_NULL, 0, 1);
}

```

### <a name="see-also"></a>См. также:

- nx_secure_dtls_session_create, nx_secure_dtls_session_receive
- nx_secure_dtls_session_send, nx_secure_dtls_session_start
- nx_secure_dtls_session_trusted_certificate_add
- nx_secure_x509_certificate_initialize
