---
title: Глава 4. Описание API ОСРВ Azure NetX Crypto
description: Описание API ОСРВ Azure NetX Crypto
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 04e732bc1fd6012636aab3a57391829f529724cf
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815260"
---
# <a name="chapter-4---azure-rtos-netx-crypto-api-description"></a>Глава 4. Описание API ОСРВ Azure NetX Crypto

## <a name="nx_crypto_initialize"></a>nx_crypto_initialize

Инициализация библиотеки NetX Secure.

### <a name="prototype"></a>Прототип

```c
UINT nx_crypto_initialize(VOID);
```

### <a name="description"></a>Описание

Эта функция инициализирует модуль библиотеки ОСРВ Azure NetX Crypto. Прежде чем использовать какие-либо другие криптографические функции, приложение должно вызвать эту функцию для инициализации и проверки целостности библиотеки. Сбой при вызове этой функции перед использованием других служб NetX Crypto приведет к возвращению ошибок.

### <a name="parameters"></a>Параметры

- **Нет**

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): библиотека NetX Crypto успешно инициализирована. Функции библиотеки теперь готовы и могут использоваться.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): не удается инициализировать библиотеку шифрования или выполнить проверку целостности. Приложение не может использовать эту библиотеку.

### <a name="example"></a>Например, .

TODO

## <a name="nx_crypto_module_state_get"></a>nx_crypto_module_state_get

Получение текущего состояния модуля с поддержкой FIPS.

### <a name="prototype"></a>Прототип

```c
UINT nx_crypto_module_state_get(VOID);
```

### <a name="description"></a>Описание

Эта служба доступна только в сборке библиотеки с поддержкой FIPS. Она возвращает значение текущего состояния библиотеки NetX Crypto.

### <a name="parameters"></a>Параметры

- **Нет**

### <a name="return-values"></a>Возвращаемые значения

- **Флаг состояния:**
  - NX_CRYPTO_LIBRARY_STATE_UNINITIALIZED 0x00000001
  - NX_CRYPTO_LIBRARY_STATE_POST_IN_PROGRESS 0x00000002
  - NX_CRYPTO_LIBRARY_STATE_INTEGRITY_TEST_FAILED 0x00000004
  - NX_CRYPTO_LIBRARY_STATE_FUNCTIONAL_TEST_FAILED 0x00000008
  - NX_CRYPTO_LIBRARY_STATE_OPERATIONAL 0x80000000
- **Все остальные значения недопустимы.**

### <a name="example"></a>Например, .

TODO

## <a name="_nx_crypto_method_aes_init"></a>_nx_crypto_method_aes_init

Инициализация блока управления шифрованием AES.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_aes_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Описание

Эта функция инициализирует блок управления AES с заданной строкой ключа. После инициализации блока управления AES последующие операции AES будут использовать этот ключ и размер ключа.

Приложение может создать несколько блоков управления AES, представляющих отдельные сеансы. Блоку управления назначается ключ. Последующие операции шифрования или расшифровки могут ссылаться на один и тот же блок управления AES без необходимости повторной инициализации блока управления AES. Если ключ для сеанса изменен, приложению необходимо повторно инициализировать блок управления AES с обновленным ключом.

Вызов службы _ *nx_crypto_method_aes_init()* приводит к автоматическому обновлению настроенных ранее ключа и размера ключа в соответствии с новым ключом.

### <a name="parameters"></a>Параметры

- **method**: указатель на допустимый блок управления методом шифрования AES. Доступны следующие стандартные методы шифрования AES:
  - *crypto_method_aes_cbc_128*
  - *crypto_method_aes_cbc_192*
  - *crypto_method_aes_cbc_256*
  - *crypto_method_aes_ctr_128*
  - *crypto_method_aes_ctr_192*
  - *crypto_method_aes_ctr_256*
  - *crypto_method_aes_xcbc_128*
  - *crypto_method_aes_ccm_8_128*
- **key**: указывает на буфер, содержащий ключ AES.
- **key_size_in_bits**: размер ключа в битах. Допустимые значения:
  - *NX_CRYPTO_AES_KEY_SIZE_128_BITS*
  - *NX_CRYPTO_AES_KEY_SIZE_192_BITS*
  - *NX_CRYPTO_AES_KEY_SIZE_256_BITS*
  - **Все остальные значения недопустимы.**
- **handle**: эта служба возвращает дескриптор вызывающей стороне. Этот дескриптор зависит от конкретной реализации и в данной реализации не используется. Приложение должно передать значение NULL для этого дескриптора.
- **crypto_metadata**: указатель на допустимое пространство памяти для блока управления AES. Начальный адрес пространства памяти должен быть выделен с буфером в 4 байта.
- **crypto_metadata_size**: размер области crypto_metadata в байтах. Для AES размер метаданных должен быть равен *sizeof(NX_AES)* .

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): блок управления AES успешно инициализирован с заданными ключом и размером ключа.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.
- **NX_PTR_ERROR (0x07)** : недопустимый указатель на ключ, недопустимое значение crypto_metadata или crypto_metadata_size либо при выделении области crypto_metadata не был задан буфер в 4 байта.
- **NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002): размер ключа не является допустимым для AES.

## <a name="_nx_crypto_method_aes_operation"></a>_nx_crypto_method_aes_operation

Выполнение операции AES (шифрование или расшифровка).

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_aes_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT status));
```

### <a name="description"></a>Описание

Эта функция выполняет операцию шифрования или расшифровки AES. Блок управления AES должен быть инициализирован с помощью службы _ *nx_crypto_method_aes_init()* . Выполняемый алгоритм AES основан на алгоритме, указанном в блоке управления *method*.

Размер входного буфера должен быть кратен 16 байтам. Размер расшифрованных данных равен размеру входных данных. Если зашифрованные данные были заполнены до размера, кратного блоку AES, то данные заполнения будут помещены в выходной буфер и должны обрабатываться приложением.

Эта операция не сохраняет сведения о состоянии и не изменяет материал ключа в блоке управления AES.

Когда op имеет значение NX_CRYPTO_SET_ADDITIONAL_DATA и указан алгоритм AES-CCM8, input указывает на дополнительные данные, а input_length_in_byte — это длина дополнительных данных.

### <a name="parameters"></a>Параметры

- **op**: тип выполняемой операции. Допустимые операции:
  - *NX_CRYPTO_ENCRYPT*
  - *NX_CRYPTO_DECRYPT*
  - *NX_CRYPTO_AUTHENTICATE (только AES-XCBC)*
  - *NX_CRYPTO_SET_ADDITIONAL_DATA (только AES-CCM8)*
- **handle**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.
- **method**: указатель на допустимый метод шифрования AES. Используемый здесь метод шифрования должен совпадать с методом, указанным в *nx_crypto_method_aes_init()* .
- **input_data**: указывает на буфер, содержащий зашифрованные текстовые данные. Ограничения для входного буфера отсутствуют.
- **input_data_size**: размер входных данных в байтах. Размер входных данных должен быть кратен 16 байтам.
- **iv_ptr**: указатель на начальный вектор (IV). Ограничения для буфера начальных векторов отсутствуют.
- **iv_size**: размер блока начального вектора (в байтах). Это поле должно иметь значение 16.
- **output_buffer**: указатель на область памяти для AES, в которой хранятся данные в виде открытого текста. Приложение должно выделить пространство для выходного буфера. Выходной буфер может перекрывать входной буфер. Выходной буфер может перекрыть входной буфер, если у них одинаковый начальный адрес.
- **output_buffer_size**: размер выходного буфера в байтах. Размер выходного буфера должен быть не меньше размера входного буфера. Кроме того, размер выходного буфера должен быть кратен 16 байтам.
- **crypto_metadata**: указатель на блок управления AES, используемый в *_nx_crypto_method_aes_init(\*)\*.*
- **crypto_metadata_size**: размер области crypto_metadata в байтах. Для AES размер метаданных должен быть равен *sizeof(NX_AES)* .
- **packet_ptr**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.
- **nx_crypto_hw_process_callback**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): операция AES успешно выполнена.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.
- **NX_PTR_ERROR** (0x07): недопустимый указатель ввода или длина.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004): указан недопустимый алгоритм AES**.

## <a name="_nx_crypto_method_aes_cleanup"></a>_nx_crypto_method_aes_cleanup

Очистка блока управления AES.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_aes_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Описание

Приложение вызывает эту функцию для очистки блока управления AES после того, как определит, что этот сеанс AES больше не требуется.

### <a name="parameters"></a>Параметры

- **crypto_metadata**: указатель на блок управления AES, используемый в *_nx_crypto_method_aes_init(\*)\*.*

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): сеанс AES успешно очищен.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.

## <a name="_nx_crypto_method_3des_init"></a>_nx_crypto_method_3des_init

Инициализация блока управления 3DES.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_3des_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Описание

Эта функция инициализирует блок управления Triple DES (3DES) с применением трех заданных строк ключа. Каждая строка ключа должна содержать 8 байт. Три ключа DES необходимо объединить в непрерывную область памяти размером в 24 байта в буфере. Для сборки с поддержкой FIPS эти три ключа должны быть разными, иначе функция вернет ошибку NX_CRYPTO_INVALID_KEY. После инициализации блока управления 3DES последующие операции 3DES будут использовать эти же ключи.

Приложение может создать несколько блоков управления 3DES, представляющих отдельные сеансы. Ключ назначается блоку управления, и последующие операции шифрования или расшифровки могут ссылаться на один и тот же блок управления без необходимости повторной инициализации. Если ключ для сеанса будет изменен, приложению потребуется повторно инициализировать блок управления с обновленным ключом.

Вызов службы _ *nx_crypto_method_3des_init()* приводит к автоматическому обновлению настроенного ранее ключа в соответствии с новыми ключами.

### <a name="parameters"></a>Параметры

- **method**: указатель на допустимый блок управления методом шифрования 3DES. Доступен следующий стандартный метод шифрования 3DES: ***crypto_method_3des***.
- **key**: указывает на буфер, содержащий три ключа 3DES.
- **key_size_in_bits**: должен иметь значение 192 (3 ключа по 64 бит).
- **handle**: эта служба возвращает дескриптор вызывающей стороне. Этот дескриптор определяет инициализируемый блок управления 3DES. Последующие операции 3DES (шифрование, расшифровка и очистка) будут использовать этот дескриптор для обращения к блоку управления 3DES.
- **crypto_metadata**: указатель на допустимое пространство памяти для блока управления 3DES. Начальный адрес пространства памяти должен быть выделен с буфером в 4 байта.
- **crypto_metadata_size**: размер области crypto_metadata в байтах. Для 3DES размер метаданных должен быть равен *sizeof(NX_3DES)* .

### <a name="return-value"></a>Возвращаемое значение

- **NX_CRYPTO_SUCCESS** (0X00): блок управления 3DES успешно инициализирован с заданными ключом и размером ключа.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.
- **NX_PTR_ERROR (0x07)** : недопустимый указатель на ключ, недопустимое значение crypto_metadata или crypto_metadata_size либо при выделении области crypto_metadata не был задан буфер в 4 байта.
- **NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002): размер ключа не является допустимым для 3DES.

## <a name="_nx_crypto_method_3des_operation"></a>_nx_crypto_method_3des_operation

Шифрование или расшифровка с помощью 3DES.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_3des_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>Описание

Эта функция выполняет операцию шифрования или расшифровки 3DES. Блок управления 3DES должен быть инициализирован с помощью службы _ *nx_crypto_method_3des_init()* . Выполняемый алгоритм 3DES основан на алгоритме, указанном в блоке управления *method*.

Размер входного буфера должен быть кратен 8 байтам. Размер расшифрованных данных равен размеру входных данных. Если зашифрованные данные были заполнены до размера, кратного блоку 3DES, то данные заполнения будут помещены в выходной буфер и должны обрабатываться приложением.

Эта операция не сохраняет сведения о состоянии и не изменяет материал ключа в блоке управления 3DES.

### <a name="parameters"></a>Параметры

- **op**: тип выполняемой операции. Допустимые операции:
  - *NX_CRYPTO_ENCRYPT*
  - *NX_CRYPTO_DECRYPT*
- **handle**: дескриптор, инициализируемый службой *_nx_crypto_method_3des_init()* .
- **method**: указатель на допустимый метод шифрования 3DES. Используемый здесь метод шифрования должен совпадать с методом, указанным в *nx_crypto_method_3des_init()* .
- **input_data**: указывает на буфер, содержащий зашифрованные текстовые данные.
Ограничения для входного буфера отсутствуют.
- **input_data_size**: размер входных данных в байтах. Размер входных данных должен быть кратен 8 байтам.
- **iv_ptr**: указатель на начальный вектор (IV). Ограничения для буфера начальных векторов отсутствуют.
- **iv_size**: размер блока начального вектора (в байтах). Это поле должно иметь значение 8.
- **output_buffer**: указатель на область памяти для 3DES, в которой хранятся данные в виде открытого текста. Приложение должно выделить пространство для выходного буфера. Выходной буфер может перекрывать входной буфер. Выходной буфер может перекрыть входной буфер, если у них одинаковый начальный адрес.
- **output_buffer_size**: размер выходного буфера в байтах. Размер выходного буфера должен быть не меньше размера входного буфера. Кроме того, размер выходного буфера должен быть кратен 8 байтам.
- **crypto_metadata**: указатель на блок управления 3DES, используемый в *_nx_crypto_method_3des_init()* .
- **crypto_metadata_size**: размер области crypto_metadata в байтах. Для 3DES размер метаданных должен быть равен *sizeof(NX_3DES)* .
- **packet_ptr**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.
- **nx_crypto_hw_process_callback**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.

### <a name="description"></a>Описание

Эта функция выполняет шифрование 3DES. Блок управления 3DES должен быть инициализирован с помощью службы _ *nx_crypto_method_3des_init()* . Эта операция не сохраняет сведения о состоянии и не изменяет материал ключа в блоке управления 3DES. Обратите внимание на то, что эта функция не применяет заполнение, поэтому вызывающему объекту потребуется выполнить заполнение перед вызовом операции шифрования.

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): блок управления 3DES успешно инициализирован с заданными ключом и размером ключа.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.
- **NX_PTR_ERROR (0x07)** : недопустимый указатель на ключ, недопустимое значение crypto_metadata или crypto_metadata_size либо при выделении области crypto_metadata не был задан буфер в 4 байта.

## <a name="_nx_crypto_method_3des_cleanup"></a>_nx_crypto_method_3des_cleanup

Очистка блока управления 3DES.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_3des_cleanup(VOID *crypto_metadata);
```

### <a name="description"></a>Описание

Приложение вызывает эту функцию для очистки блока управления 3DES после того, как определит, что этот сеанс 3DES больше не требуется.

### <a name="parameters"></a>Параметры

- **handle**: дескриптор, инициализируемый службой *_nx_crypto_method_3des_init()* .

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): сеанс 3DES успешно очищен.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.

## <a name="_nx_crypto_method_drbg_init"></a>_nx_crypto_method_drbg_init

Инициализация блока управления шифрованием DRBG.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_drbg_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Описание

Эта функция инициализирует блок управления DRBG с заданной строкой ключа. После инициализации блока управления DRBG последующая операция DRBG должна использовать этот же блок управления.

Приложение может создать несколько блоков управления DRBG, представляющих отдельные сеансы. Инициализация блока управления DRBG запускает новый сеанс вычисления хэша. Повторная инициализация блока управления DRBG прекращает текущий сеанс и запускает новый.

### <a name="parameters"></a>Параметры

- **method**: указатель на допустимый блок управления методом шифрования DRBG. Доступны следующие стандартные методы шифрования:
  - *crypto_method_drbg*
- **key**: это поле не используется для DRBG.
- **key_size_in_bits**: это поле не используется для DRBG.
- **handle**: эта служба возвращает дескриптор вызывающей стороне. Этот дескриптор зависит от конкретной реализации и в данной реализации не используется. Приложение должно передать значение NULL для этого дескриптора.
- **crypto_metadata**: указатель на допустимое пространство памяти для блока управления DRBG. Начальный адрес пространства памяти должен быть выделен с буфером в 4 байта.
- **crypto_metadata_size**: размер области crypto_metadata в байтах. Для DRBG размер метаданных должен быть равен *sizeof(NX_CRYPTO_DRBG)* .

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): блок управления DRBG успешно инициализирован с заданными ключом и размером ключа.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.
- **NX_PTR_ERROR (0x07)** : недопустимый указатель на ключ, недопустимое значение crypto_metadata или crypto_metadata_size либо при выделении области crypto_metadata не был задан буфер в 4 байта.

## <a name="_nx_crypto_method_drbg_operation"></a>_nx_crypto_method_drbg_operation

Выполнение операции DRBG.

### <a name="prototype"></a>Прототип

```c
UINT __nx_crypto_method_drbg_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>Описание

Эта функция выполняет операцию DRBG. Блок управления DRBG должен быть инициализирован с помощью службы _ *nx_crypto_method_drbg_init()* . Выполняемый алгоритм DRBG основан на алгоритме, указанном в блоке управления *method*. По умолчанию для DRBG используется алгоритм AES-128.

Если задана операция NX_CRYPTO_DRBG_OPTIONS_SET, то input указывает на структуру NX_CRYPTO_DRBG_OPTIONS. Если задана операция NX_CRYPTO_DRBG_INSTANTIATE, то key указывает на nonce, а input указывает на строку персонализации. Если задана операция NX_CRYPTO_DRBG_RESEED или NX_CRYPTO_DRBG_GENERATE, то input указывает на дополнительные входные данные.

### <a name="parameters"></a>Параметры

- **op**: тип выполняемой операции. Допустимые операции:
  - *NX_CRYPTO_DRBG_OPTIONS_SET*
  - *NX_CRYPTO_DRBG_INSTANTIATE*
  - *NX_CRYPTO_DRBG_RESEED NX_CRYPTO_DRBG_GENERATE*
- **handle**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.
- **method**: указатель на допустимый метод шифрования DRBG. Используемый здесь метод шифрования должен совпадать с методом, указанным в _ *nx_crypto_method_drbg_init()* .
- **key**: указатель на ключ nonce для операции создания экземпляра. Это поле не используется для других операций.
- **key_size_in_bits**: размер ключа nonce в битах. Это поле не используется для других операций.
- **input**: когда op имеет значение NX_CRYPTO_DRBG_OPTIONS_SET, это поле указывает на параметры DRBG. Когда op имеет значение NX_CRYPTO_DRBG_INSTANTIATE, это поле указывает на строку персонализации. Если op имеет значение NX_CRYPTO_DRBG_RESEED или NX_CRYPTO_DRBG_GENERATE, это поле указывает на дополнительные входные данные.
- **input_length_in_byte**: размер входных данных в байтах.
- **iv_ptr**: это поле не используется для DRBG.
- **output**: когда op имеет значение NX_CRYPTO_DRBG_GENERATE, это поле указывает на область памяти для созданного экземпляра DRBG. В противном случае это поле не используется.
- **output_length_in_byte**: указывает размер буфера вывода в байтах.
- **crypto_metadata**: указатель на блок управления DRBG, используемый в *_nx_crypto_method_drbg_init()* .
- **crypto_metadata_size**: размер области crypto_metadata в байтах. Для DRBG размер метаданных должен быть равен *sizeof(NX_CRYPTO_DRBG)* .
- **packet_ptr**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.
- **nx_crypto_hw_process_callback**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): операция DRBG успешно выполнена.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.
- **NX_PTR_ERROR** (0x07): недопустимый указатель ввода или длина.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004): указан недопустимый алгоритм DRBG.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005): недопустимый размер выходного буфера.

## <a name="_nx_crypto_method_drbg_cleanup"></a>_nx_crypto_method_drbg_cleanup

Очистка блока управления DRBG.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_drbg_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Описание

Приложение вызывает эту функцию для очистки блока управления DRBG после того, как определит, что этот сеанс DRBG больше не требуется.

### <a name="parameters"></a>Параметры

- **crypto_metadata**: указатель на блок управления DRBG, используемый в *_nx_crypto_method_drbg_init()* .

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): сеанс DRBG успешно очищен.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.

## <a name="_nx_crypto_method_ecdh_init"></a>_nx_crypto_method_ecdh_init

Инициализация блока управления шифрованием ECDH.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_ecdh_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Описание

Эта функция инициализирует блок управления ECDH с заданной строкой ключа. После инициализации блока управления ECDH последующая операция ECDH должна использовать этот же блок управления.

Приложение может создать несколько блоков управления ECDH, представляющих отдельные сеансы. Инициализация блока управления ECDH запускает новый сеанс вычисления хэша. Повторная инициализация блока управления ECDH прекращает текущий сеанс и запускает новый.

### <a name="parameters"></a>Параметры

- **method**: указатель на допустимый блок управления методом шифрования ECDH. Доступны следующие стандартные методы шифрования:
  - *crypto_method_ecdh*
- **key**: это поле не используется для ECDH.
- **key_size_in_bits**: это поле не используется для ECDH.
- **handle**: эта служба возвращает дескриптор вызывающей стороне. Этот дескриптор зависит от конкретной реализации и в данной реализации не используется. Приложение должно передать значение NULL для этого дескриптора.
- **crypto_metadata**: указатель на допустимое пространство памяти для блока управления ECDH. Начальный адрес пространства памяти должен быть выделен с буфером в 4 байта.
- **crypto_metadata_size**: размер области crypto_metadata в байтах. Для ECDH размер метаданных должен быть равен *sizeof(NX_CRYPTO_ECDH)* .

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): блок управления ECDH успешно инициализирован с заданными ключом и размером ключа.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.
- **NX_PTR_ERROR (0x07)** : недопустимый указатель на ключ, недопустимое значение crypto_metadata или crypto_metadata_size либо при выделении области crypto_metadata не был задан буфер в 4 байта.

## <a name="_nx_crypto_method_ecdh_operation"></a>_nx_crypto_method_ecdh_operation

Выполнение операции ECDH.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_ecdh_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>Описание

Эта функция выполняет операцию ECDH. Блок управления ECDH должен быть инициализирован с помощью службы _ *nx_crypto_method_ecdh_init()* . Выполняемый алгоритм ECDH основан на алгоритме, указанном в блоке управления *method*.

Если задана операция NX_CRYPTO_EC_CURVE_SET, то input указывает на метод шифрования на основе эллиптических кривых. Если задана операция NX_CRYPTO_EC_KEY_PAIR_GENERATE, output указывает на структуру NX_CRYPTO_EXTENDED_OUTPUT, а пара ключей копируется в nx_crypto_extended_output_data. Если задана операция NX_CRYPTO_DH_SETUP, то открытый ключ возвращается в nx_crypto_extended_output_data. Если задана операция NX_CRYPTO_DH_KEY_PAIR_IMPORT, то input указывает на открытый ключ, а key указывает на закрытый ключ. Если задана операция NX_CRYPTO_DH_PRIVATE_KEY_EXPORT, то закрытый ключ возвращается в nx_crypto_extended_output_data. Если задана операция NX_CRYPTO_DH_CALCULATE, то input указывает на удаленный открытый ключ, а общий секрет копируются в nx_crypto_extended_output_data.

### <a name="parameters"></a>Параметры

- **op**: тип выполняемой операции. Допустимые операции:
  - *NX_CRYPTO_EC_CURVE_SET*
  - *NX_CRYPTO_DH_SETUP*
  - *NX_CRYPTO_DH_CALCULATE*
  - *NX_CRYPTO_DH_KEY_PAIR_IMPOPRT*
  - *NX_CRYPTO_DH_KEY_PAIR_GENERATE*
  - *NX_CRYPTO_DH_PRIVATE_KEY_EXPORT*
- **handle**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.
- **method**: указатель на допустимый метод шифрования ECDH. Используемый здесь метод шифрования должен совпадать с методом, указанным в _ *nx_crypto_method_ecdh_init()* .
- **key**: когда op имеет значение NX_CRYPTO_DH_IMPORT_KEY_PAIR, это поле указывает на закрытый ключ. В противном случае это поле не используется для ECDH.
- **key_size_in_bits**: размер ключа в битах.
- **input**: когда op имеет значение NX_CRYPTO_EC_CURVE_SET, это поле указывает на метод шифрования на основе эллиптических кривых. Когда op имеет значение NX_CRYPTO_DH_SETUP, это поле не используется. Когда op имеет значение NX_CRYPTO_DH_CALCULATE, это поле указывает на буфер, содержащий входные текстовые данные. Когда op имеет значение NX_CRYPTO_DH_IMPORT_KEY_PAIR, это поле указывает на открытый ключ.
- **input_length_in_byte**: размер входных данных в байтах.
- **iv_ptr**: это поле не используется для ECDH.
- **output**: если op имеет значение NX_CRYPTO_EC_CURVE_SET или NX_CRYPTO_DH_IMPORT_KEY_PAIR, это поле не используется. Когда op имеет значение NX_CRYPTO_DH_SETUP, это поле указывает на область памяти для созданного ECDH открытого ключа. Когда op имеет значение NX_CRYPTO_DH_CALCULATE, это поле указывает на область памяти для созданного ECDH общего секрета.
- **output_length_in_byte**: указывает размер буфера вывода в байтах.
- **crypto_metadata**: указатель на блок управления ECDH, используемый в *_nx_crypto_method_ecdh_init()* .
- **crypto_metadata_size**: размер области crypto_metadata в байтах. Для ECDH размер метаданных должен быть равен *sizeof(NX_CRYPTO_ECDH)* .
- **packet_ptr**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.
- **nx_crypto_hw_process_callback**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): операция ECDH успешно выполнена.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.
- **NX_PTR_ERROR** (0x07): недопустимый указатель ввода или длина.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004): указан недопустимый алгоритм ECDH.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005): недопустимый размер выходного буфера.

## <a name="_nx_crypto_method_ecdh_cleanup"></a>_nx_crypto_method_ecdh_cleanup

Очистка блока управления ECDH.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_ecdh_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Описание

Приложение вызывает эту функцию для очистки блока управления ECDH после того, как определит, что этот сеанс ECDH больше не требуется.

### <a name="parameters"></a>Параметры

- **crypto_metadata**: указатель на блок управления ECDH, используемый в *_nx_crypto_method_ecdh_init()* .

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): сеанс ECDH успешно очищен.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.

## <a name="_nx_crypto_method_ecdsa_init"></a>_nx_crypto_method_ecdsa_init

Инициализация блока управления шифрованием ECDSA.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_ecdsa_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Описание

Эта функция инициализирует блок управления ECDSA с заданной строкой ключа. После инициализации блока управления ECDSA последующая операция ECDSA должна использовать этот же блок управления.

Приложение может создать несколько блоков управления ECDSA, представляющих отдельные сеансы. Инициализация блока управления ECDSA запускает новый сеанс вычисления хэша. Повторная инициализация блока управления ECDSA прекращает текущий сеанс и запускает новый.

### <a name="parameters"></a>Параметры

- **method**: указатель на допустимый блок управления методом шифрования ECDSA. Доступны следующие стандартные методы шифрования:
  - *crypto_method_ecdsa*
- **key**: это поле не используется для ECDSA.
- **key_size_in_bits**: это поле не используется для ECDSA.
- **handle**: эта служба возвращает дескриптор вызывающей стороне. Этот дескриптор зависит от конкретной реализации и в данной реализации не используется. Приложение должно передать значение NULL для этого дескриптора.
- **crypto_metadata**: указатель на допустимое пространство памяти для блока управления ECDSA. Начальный адрес пространства памяти должен быть выделен с буфером в 4 байта.
- **crypto_metadata_size**: размер области crypto_metadata в байтах. Для ECDSA размер метаданных должен быть равен *sizeof(NX_CRYPTO_ECDSA)* .

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): блок управления ECDSA успешно инициализирован с заданными ключом и размером ключа.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.
- **NX_PTR_ERROR (0x07)** : недопустимый указатель на ключ, недопустимое значение crypto_metadata или crypto_metadata_size либо при выделении области crypto_metadata не был задан буфер в 4 байта.

## <a name="_nx_crypto_method_ecdsa_operation"></a>_nx_crypto_method_ecdsa_operation

Выполнение операции ECDSA.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_ecdsa_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>Описание

Эта функция выполняет операцию ECDSA. Блок управления ECDSA должен быть инициализирован с помощью службы _ *nx_crypto_method_ecdsa_init()* . Выполняемый алгоритм ECDSA основан на алгоритме, указанном в блоке управления *method*.

Если задана операция NX_CRYPTO_EC_CURVE_SET, то input указывает на метод шифрования на основе эллиптических кривых. Если задана операция NX_CRYPTO_EC_KEY_PAIR_GENERATE, output указывает на структуру NX_CRYPTO_EXTENDED_OUTPUT, а пара ключей копируется в nx_crypto_extended_output_data.

### <a name="parameters"></a>Параметры

- **op**: тип выполняемой операции. Допустимые операции:
  - *NX_CRYPTO_EC_CURVE_SET*
  - *NX_CRYPTO_AUTHENTICATE*
  - *NX_CRYPTO_VERIFY*
- **handle**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.
- **method**: указатель на допустимый метод шифрования ECDSA. Используемый здесь метод шифрования должен совпадать с методом, указанным в _ *nx_crypto_method_ecdsa_init()* .
- **key**: указывает на ключ, когда op имеет значение NX_CRYPTO_VERIFY. Ограничения для буфера ключей отсутствуют. Это поле не используется при других значениях параметра op.
- **key_size_in_bits**: размер ключа в битах.
- **input**: когда op имеет значение NX_CRYPTO_EC_CURVE_SET, это поле указывает на метод шифрования на основе эллиптических кривых. В противном случае это поле указывает на буфер, содержащий входные текстовые данные.
- **input_length_in_byte**: размер входных данных в байтах.
- **iv_ptr**: это поле не используется для ECDSA.
- **output**: если op имеет значение NX_CRYPTO_EC_CURVE_SET, это поле не используется. Когда op имеет значение NX_CRYPTO_AUTHENTICATE, это поле указывает на область памяти для созданной ECDSA сигнатуры. Когда op имеет значение NX_CRYPTO_VERIFY, это поле указывает на область памяти для проверенной ECDSA сигнатуры.
- **output_length_in_byte**: указывает размер буфера вывода в байтах.
- **crypto_metadata**: указатель на блок управления ECDSA, используемый в *_nx_crypto_method_ecdsa_init()* .
- **crypto_metadata_size**: размер области crypto_metadata в байтах. Для ECDSA размер метаданных должен быть равен *sizeof(NX_CRYPTO_ECDSA)* .
- **packet_ptr**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.
- **nx_crypto_hw_process_callback**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): операция ECDSA успешно выполнена.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.
- **NX_PTR_ERROR** (0x07): недопустимый указатель ввода или длина.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004): указан недопустимый алгоритм ECDSA.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005): недопустимый размер выходного буфера.

## <a name="_nx_crypto_method_ecdsa_cleanup"></a>_nx_crypto_method_ecdsa_cleanup

Очистка блока управления ECDSA.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_ecdsa_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Описание

Приложение вызывает эту функцию для очистки блока управления ECDSA после того, как определит, что этот сеанс ECDSA больше не требуется.

### <a name="parameters"></a>Параметры

- **crypto_metadata**: указатель на блок управления ECDSA, используемый в *_nx_crypto_method_ecdsa_init()* .

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): сеанс ECDSA успешно очищен.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.

## <a name="_nx_crypto_method_hmac_md5_init"></a>_nx_crypto_method_hmac_md5_init

Инициализирует блок управления шифрованием HMAC MD5.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_hmac_md5_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Описание

Эта функция инициализирует блок управления HMAC MD5 с заданной строкой ключа. После инициализации блока управления HMAC MD5 последующая операция HMAC MD5 должна использовать этот же блок управления.

Приложение может создать несколько блоков управления HMAC MD5, представляющих отдельные сеансы. Инициализация блока управления HMAC MD5 запускает новый сеанс вычисления хэша. Повторная инициализация блока управления HMAC MD5 прекращает текущий сеанс и запускает новый.

### <a name="parameters"></a>Параметры

- **method**: указатель на допустимый блок управления методом шифрования HMAC MD5.
Доступны следующие стандартные методы шифрования:
  - *crypto_method_hmac_md5*
- **key**: указывает на ключ. Ограничения для буфера ключей отсутствуют.
- **key_size_in_bits**: размер ключа в битах.
- **handle**: эта служба возвращает дескриптор вызывающей стороне. Этот дескриптор зависит от конкретной реализации и в данной реализации не используется. Приложение должно передать значение NULL для этого дескриптора.
- **crypto_metadata**: указатель на допустимое пространство памяти для блока управления HMAC MD5. Начальный адрес пространства памяти должен быть выделен с буфером в 4 байта.
- **crypto_metadata_size**: размер области crypto_metadata в байтах. Для HMAC MD5 размер метаданных должен быть равен *sizeof(NX_CRYPTO_MD5_HMAC)* .

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): блок управления HMAC MD5 успешно инициализирован с заданными ключом и размером ключа.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.
- **NX_PTR_ERROR (0x07)** : недопустимый указатель на ключ, недопустимое значение crypto_metadata или crypto_metadata_size либо при выделении области crypto_metadata не был задан буфер в 4 байта.

## <a name="_nx_crypto_method_hmac_md5_operation"></a>_nx_crypto_method_hmac_md5_operation

Выполнение хэш-операции HMAC MD5.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_hmac_md5_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>Описание

Эта функция выполняет хэш-операцию HMAC MD5. Блок управления HMAC MD5 должен быть инициализирован с помощью службы _ *nx_crypto_method_hmac_md5_init()* . Выполняемый алгоритм HMAC MD5 основан на алгоритме, указанном в блоке управления *method*.

Для последней операции *NX_CRYPTO_HASH_CALCULATE* размер выходного буфера должен составлять 16 байт.

Эта операция не сохраняет сведения о состоянии и не изменяет материал ключа в блоке управления HMAC MD5.

### <a name="parameters"></a>Параметры

- **op**: тип выполняемой операции. Допустимые операции:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.
- **method**: указатель на допустимый метод шифрования HMAC MD5. Используемый здесь метод шифрования должен совпадать с методом, указанным в *nx_crypto_method_hmac_md5_init()* .
- **key**: указывает на ключ. Ограничения для буфера ключей отсутствуют.
- **key_size_in_bits**: размер ключа в битах.
- **input_data**: указывает на буфер, содержащий входные текстовые данные. Ограничения для входного буфера отсутствуют.
- **input_data_size**: размер входных данных в байтах.
- **iv_ptr**: это поле не используется для HMAC MD5.
- **iv_size**: это поле не используется для HMAC MD5.
- **output_buffer**: указатель на область памяти для созданного HMAC MD5 хэша.
- **output_buffer_size**: размер выходного буфера в байтах.
- **crypto_metadata**: указатель на блок управления HMAC MD5, используемый в *_nx_crypto_method_hmac_md5_init()* .
- **crypto_metadata_size**: размер области crypto_metadata в байтах. Для HMAC MD5 размер метаданных должен быть равен *sizeof(NX_CRYPTO_MD5_HMAC)* .
- **packet_ptr**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.
- **nx_crypto_hw_process_callback**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): операция HMAC MD5 успешно выполнена.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.
- **NX_PTR_ERROR** (0x07): недопустимый указатель ввода или длина.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004): указан недопустимый алгоритм HMAC MD5.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005): недопустимый размер выходного буфера.

## <a name="_nx_crypto_method_hmac_sha1_init"></a>_nx_crypto_method_hmac_sha1_init

Инициализация блока управления шифрованием HMAC SHA1.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_hmac_sha1_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Описание

Эта функция инициализирует блок управления HMAC SHA1 с заданной строкой ключа. После инициализации блока управления HMAC SHA1 последующая операция HMAC SHA1 должна использовать этот же блок управления.

Приложение может создать несколько блоков управления HMAC SHA1, представляющих отдельные сеансы. Инициализация блока управления HMAC SHA1 запускает новый сеанс вычисления хэша. Повторная инициализация блока управления HMAC SHA1 прекращает текущий сеанс и запускает новый.

### <a name="parameters"></a>Параметры

- **method**: указатель на допустимый блок управления методом шифрования HMAC SHA1. Доступны следующие стандартные методы шифрования:
  - *crypto_method_hmac_sha1*
- **key**: указывает на ключ. Ограничения для буфера ключей отсутствуют.
- **key_size_in_bits**: размер ключа в битах.
- **handle**: эта служба возвращает дескриптор вызывающей стороне. Этот дескриптор зависит от конкретной реализации и в данной реализации не используется. Приложение должно передать значение NULL для этого дескриптора.
- **crypto_metadata**: указатель на допустимое пространство памяти для блока управления HMAC SHA1. Начальный адрес пространства памяти должен быть выделен с буфером в 4 байта.
- **crypto_metadata_size**: размер области crypto_metadata в байтах. Для HMAC SHA1 размер метаданных должен быть равен *sizeof(NX_CRYPTO_SHA1_HMAC)* .

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): блок управления HMAC SHA1 успешно инициализирован с заданными ключом и размером ключа.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.
- **NX_PTR_ERROR (0x07)** : недопустимый указатель на ключ, недопустимое значение crypto_metadata или crypto_metadata_size либо при выделении области crypto_metadata не был задан буфер в 4 байта.

## <a name="_nx_crypto_method_hmac_sha1_operation"></a>_nx_crypto_method_hmac_sha1_operation

Выполнение хэш-операции HMAC SHA1.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_hmac_sha1_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>Описание

Эта функция выполняет хэш-операцию HMAC SHA1. Блок управления HMAC SHA1 должен быть инициализирован с помощью службы _ *nx_crypto_method_hmac_sha1_init()* . Выполняемый алгоритм HMAC SHA1 основан на алгоритме, указанном в блоке управления *method*.

Для последней операции *NX_CRYPTO_HASH_CALCULATE* размер выходного буфера должен составлять 20 байт.

### <a name="parameters"></a>Параметры

- **op**: тип выполняемой операции. Допустимые операции:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.
- **method**: указатель на допустимый метод шифрования HMAC SHA1. Используемый здесь метод шифрования должен совпадать с методом, указанным в _ *nx_crypto_method_hmac_sha1_init()* .
- **key**: указывает на ключ. Ограничения для буфера ключей отсутствуют.
- **key_size_in_bits**: размер ключа в битах.
- **input_data**: указывает на буфер, содержащий входные текстовые данные. Ограничения для входного буфера отсутствуют.
- **input_data_size**: размер входных данных в байтах.
- **iv_ptr**: это поле не используется для HMAC SHA1.
- **iv_size**: это поле не используется для HMAC SHA1.
- **output_buffer**: указатель на область памяти для созданного HMAC SHA1 хэша.
- **output_buffer_size**: размер выходного буфера в байтах.
- **crypto_metadata**: указатель на блок управления HMAC SHA1, используемый в *_nx_crypto_method_hmac_sha1_init()* .
- **crypto_metadata_size**: размер области crypto_metadata в байтах. Для HMAC SHA1 размер метаданных должен быть равен *sizeof(NX_CRYPTO_SHA1_HMAC)* .
- **packet_ptr**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.
- **nx_crypto_hw_process_callback**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): операция HMAC SHA1 успешно выполнена.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.
- **NX_PTR_ERROR** (0x07): недопустимый указатель ввода или длина.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004): указан недопустимый алгоритм HMAC SHA1.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005): недопустимый размер выходного буфера.

## <a name="_nx_crypto_method_hmac_sha1_cleanup"></a>_nx_crypto_method_hmac_sha1_cleanup

Очистка блока управления HMAC SHA1.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_hmac_sha1_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Описание

Приложение вызывает эту функцию для очистки блока управления HMAC SHA1 после того, как определит, что этот сеанс HMAC SHA1 больше не требуется.

### <a name="parameters"></a>Параметры

- **crypto_metadata**: указатель на блок управления HMAC SHA1, используемый в *_nx_crypto_method_hmac_sha1_init()* .

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): сеанс HMAC SHA1 успешно очищен.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.

## <a name="_nx_crypto_method_hmac_sha256_init"></a>_nx_crypto_method_hmac_sha256_init

Инициализация блока управления шифрованием HMAC SHA256.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_hmac_sha256_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Описание

Эта функция инициализирует блок управления HMAC SHA256 с заданной строкой ключа. После инициализации блока управления HMAC SHA256 последующая операция HMAC SHA256 должна использовать этот же блок управления.

Приложение может создать несколько блоков управления HMAC SHA256, представляющих отдельные сеансы. Инициализация блока управления HMAC SHA256 запускает новый сеанс вычисления хэша. Повторная инициализация блока управления HMAC SHA256 прекращает текущий сеанс и запускает новый.

### <a name="parameters"></a>Параметры

- **method**: указатель на допустимый блок управления методом шифрования HMAC SHA256. Доступны следующие стандартные методы шифрования:
  - *crypto_method_hmac_sha224*
  - *crypto_method_hmac_sha256*
- **key**: указывает на ключ. Ограничения для буфера ключей отсутствуют.
- **key_size_in_bits**: размер ключа в битах.
- **handle**: эта служба возвращает дескриптор вызывающей стороне. Этот дескриптор зависит от конкретной реализации и в данной реализации не используется. Приложение должно передать значение NULL для этого дескриптора.
- **crypto_metadata**: указатель на допустимое пространство памяти для блока управления HMAC SHA256. Начальный адрес пространства памяти должен быть выделен с буфером в 4 байта.
- **crypto_metadata_size**: размер области crypto_metadata в байтах. Для HMAC SHA256 размер метаданных должен быть *sizeof(NX_CRYTPO_SHA256_HMAC)* .

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): блок управления HMAC SHA256 успешно инициализирован с заданными ключом и размером ключа.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.
- **NX_PTR_ERROR (0x07)** : недопустимый указатель на ключ, недопустимое значение crypto_metadata или crypto_metadata_size либо при выделении области crypto_metadata не был задан буфер в 4 байта.

## <a name="_nx_crypto_method_hmac_sha256_operation"></a>_nx_crypto_method_hmac_sha256_operation

Выполнение хэш-операции HMAC SHA256.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_hmac_sha256_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>Описание

Эта функция выполняет хэш-операцию HMAC SHA256. Блок управления HMAC SHA256 должен быть инициализирован с помощью службы _ *nx_crypto_method_hmac_sha256_init()* . Выполняемый алгоритм HMAC SHA256 основан на алгоритме, указанном в блоке управления *method*.

Для последней операции *NX_CRYPTO_HASH_CALCULATE* размер выходного буфера должен составлять 32 байта для SHA256 или 28 байт для SHA224.

### <a name="parameters"></a>Параметры

- **op**: тип выполняемой операции. Допустимые операции:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.
- **method**: указатель на допустимый метод шифрования HMAC SHA256. Используемый здесь метод шифрования должен совпадать с методом, указанным в _ *nx_crypto_method_hmac_sha256_init()* .
- **key**: указывает на ключ. Ограничения для буфера ключей отсутствуют.
- **key_size_in_bits**: размер ключа в битах.
- **input_data**: указывает на буфер, содержащий входные текстовые данные. Ограничения для входного буфера отсутствуют.
- **input_data_size**: размер входных данных в байтах.
- **iv_ptr**: это поле не используется для HMAC SHA256.
- **iv_size**: это поле не используется для HMAC SHA256.
- **output_buffer**: указатель на область памяти для созданного HMAC SHA256 хэша.
- **output_buffer_size**: размер выходного буфера в байтах.
- **crypto_metadata**: указатель на блок управления HMAC SHA256, используемый в *_nx_crypto_method_hmac_sha256_init()* .
- **crypto_metadata_size**: размер области crypto_metadata в байтах. Для HMAC SHA256 размер метаданных должен быть равен *sizeof(NX_CRYTPO_SHA256_HMAC)* .
- **packet_ptr**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.
- **nx_crypto_hw_process_callback**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): операция HMAC SHA256 успешно выполнена.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.
- **NX_PTR_ERROR** (0x07): недопустимый указатель ввода или длина.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004): указан недопустимый алгоритм HMAC SHA256.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005): недопустимый размер выходного буфера.

## <a name="_nx_crypto_method_hmac_sha256_cleanup"></a>_nx_crypto_method_hmac_sha256_cleanup

Очистка блока управления HMAC SHA256.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_hmac_sha256_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Описание

Приложение вызывает эту функцию для очистки блока управления HMAC SHA256 после того, как определит, что этот сеанс HMAC SHA256 больше не требуется.

### <a name="parameters"></a>Параметры

- **crypto_metadata**: указатель на блок управления HMAC SHA256, используемый в *_nx_crypto_method_hmac_sha256_init()* .

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): сеанс HMAC SHA256 успешно очищен.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.

## <a name="_nx_crypto_method_hmac_sha512_init"></a>_nx_crypto_method_hmac_sha512_init

Инициализация блока управления шифрованием HMAC SHA512.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_hmac_sha512_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Описание

Эта функция инициализирует блок управления HMAC SHA512 с заданной строкой ключа. После инициализации блока управления HMAC SHA512 последующая операция HMAC SHA512 должна использовать этот же блок управления.

Приложение может создать несколько блоков управления HMAC SHA512, представляющих отдельные сеансы. Инициализация блока управления HMAC SHA512 запускает новый сеанс вычисления хэша. Повторная инициализация блока управления HMAC SHA512 прекращает текущий сеанс и запускает новый.

### <a name="parameters"></a>Параметры

- **method**: указатель на допустимый блок управления методом шифрования HMAC SHA512. Доступны следующие стандартные методы шифрования:
  - *crypto_method_hmac_sha384*
  - *crypto_method_hmac_sha512*
- **key**: указывает на ключ. Ограничения для буфера ключей отсутствуют.
- **key_size_in_bits**: размер ключа в битах.
- **handle**: эта служба возвращает дескриптор вызывающей стороне. Этот дескриптор зависит от конкретной реализации и в данной реализации не используется. Приложение должно передать значение NULL для этого дескриптора.
- **crypto_metadata**: указатель на допустимое пространство памяти для блока управления HMAC SHA512. Начальный адрес пространства памяти должен быть выделен с буфером в 4 байта.
- **crypto_metadata_size**: размер области crypto_metadata в байтах. Для HMAC SHA512 размер метаданных должен быть равен *sizeof(NX_CRYPTO_SHA512_HMAC)* .

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): блок управления HMAC SHA512 успешно инициализирован с заданными ключом и размером ключа.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.
- **NX_PTR_ERROR (0x07)** : недопустимый указатель на ключ, недопустимое значение crypto_metadata или crypto_metadata_size либо при выделении области crypto_metadata не был задан буфер в 4 байта.

## <a name="_nx_crypto_method_hmac_sha512_operation"></a>_nx_crypto_method_hmac_sha512_operation

Выполнение хэш-операции HMAC SHA512.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_hmac_sha512_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>Описание

Эта функция выполняет хэш-операцию HMAC SHA512. Блок управления HMAC SHA512 должен быть инициализирован с помощью службы _ *nx_crypto_method_hmac_sha512_init()* . Выполняемый алгоритм HMAC SHA512 основан на алгоритме, указанном в блоке управления *method*.

Для последней операции *NX_CRYPTO_HASH_CALCULATE* размер выходного буфера должен составлять 64 байта для SHA512 или 48 байт для SHA384.

### <a name="parameters"></a>Параметры

- **op**: тип выполняемой операции. Допустимые операции:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.
- **method**: указатель на допустимый метод шифрования HMAC SHA512. Используемый здесь метод шифрования должен совпадать с методом, указанным в _ *nx_crypto_method_hmac_sha512_init()* .
- **key**: указывает на ключ. Ограничения для буфера ключей отсутствуют.
- **key_size_in_bits**: размер ключа в битах.
- **input_data**: указывает на буфер, содержащий входные текстовые данные. Ограничения для входного буфера отсутствуют.
- **input_data_size**: размер входных данных в байтах.
- **iv_ptr**: это поле не используется для HMAC SHA512.
- **iv_size**: это поле не используется для HMAC SHA512.
- **output_buffer**: указатель на область памяти для созданного HMAC SHA512 хэша.
- **output_buffer_size**: размер выходного буфера в байтах.
- **crypto_metadata**: указатель на блок управления HMAC SHA512, используемый в *_nx_crypto_method_hmac_sha512_init()* .
- **crypto_metadata_size**: размер области crypto_metadata в байтах. Для HMAC SHA512 размер метаданных должен быть равен *sizeof(NX_CRYPTO_SHA512_HMAC)* .
- **packet_ptr**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.
- **nx_crypto_hw_process_callback**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): операция HMAC SHA512 успешно выполнена.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.
- **NX_PTR_ERROR** (0x07): недопустимый указатель ввода или длина.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004): указан недопустимый алгоритм HMAC SHA512.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005): недопустимый размер выходного буфера.

## <a name="_nx_crypto_method_hmac_sha512_cleanup"></a>_nx_crypto_method_hmac_sha512_cleanup

Очистка блока управления HMAC SHA512.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_hmac_sha512_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Описание

Приложение вызывает эту функцию для очистки блока управления HMAC SHA512 после того, как определит, что этот сеанс HMAC SHA512 больше не требуется.

### <a name="parameters"></a>Параметры

- **crypto_metadata**: указатель на блок управления HMAC SHA512, используемый в *_nx_crypto_method_hmac_sha512_init()* .

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): сеанс HMAC SHA512 успешно очищен.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.

### <a name="example"></a>Например, . 

## <a name="_nx_crypto_method_md5_init"></a>_nx_crypto_method_md5_init

Инициализация блока управления шифрованием MD5.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_md5_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Описание

Эта функция инициализирует блок управления MD5 с заданной строкой ключа. После инициализации блока управления MD5 последующая операция MD5 должна использовать этот же блок управления.

Приложение может создать несколько блоков управления MD5, представляющих отдельные сеансы. Инициализация блока управления MD5 запускает новый сеанс вычисления хэша. Повторная инициализация блока управления MD5 прекращает текущий сеанс и запускает новый.

### <a name="parameters"></a>Параметры

- **method**: указатель на допустимый блок управления методом шифрования MD5. Доступны следующие стандартные методы шифрования:
  - *crypto_method_md5*
- **key**: это поле не используется для MD5.
- **key_size_in_bits**: это поле не используется для MD5.
- **handle**: эта служба возвращает дескриптор вызывающей стороне. Этот дескриптор зависит от конкретной реализации и в данной реализации не используется. Приложение должно передать значение NULL для этого дескриптора.
- **crypto_metadata**: указатель на допустимое пространство памяти для блока управления MD5. Начальный адрес пространства памяти должен быть выделен с буфером в 4 байта.
- **crypto_metadata_size**: размер области crypto_metadata в байтах. Для MD5 размер метаданных должен быть равен *sizeof(NX_CRYPTO_MD5)* .

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): блок управления MD5 успешно инициализирован с заданными ключом и размером ключа.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.
- **NX_PTR_ERROR (0x07)** : недопустимый указатель на ключ, недопустимое значение crypto_metadata или crypto_metadata_size либо при выделении области crypto_metadata не был задан буфер в 4 байта.

### <a name="example"></a>Например, .

## <a name="_nx_crypto_method_md5_operation"></a>_nx_crypto_method_md5_operation

Выполнение хэш-операции MD5.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_md5_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>Описание

Эта функция выполняет хэш-операцию MD5. Блок управления MD5 должен быть инициализирован с помощью службы _ *nx_crypto_method_md5_init()* . Выполняемый алгоритм MD5 основан на алгоритме, указанном в блоке управления *method*.

Для последней операции *NX_CRYPTO_HASH_CALCULATE* размер выходного буфера должен составлять 16 байт.

Эта операция не сохраняет сведения о состоянии и не изменяет материал ключа в блоке управления MD5.

### <a name="parameters"></a>Параметры

- **op**: тип выполняемой операции. Допустимые операции:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.
- **method**: указатель на допустимый метод шифрования MD5. Используемый здесь метод шифрования должен совпадать с методом, указанным в _ *nx_crypto_method_md5_init()* .
- **input_data**: указывает на буфер, содержащий входные текстовые данные. Ограничения для входного буфера отсутствуют.
- **input_data_size**: размер входных данных в байтах.
- **iv_ptr**: это поле не используется для MD5.
- **iv_size**: это поле не используется для MD5.
- **output_buffer**: указатель на область памяти для созданного MD5 хэша.
- **output_buffer_size**: размер выходного буфера в байтах. Для MD5 размер буфера должен составлять 16 байт.
- **crypto_metadata**: указатель на блок управления MD5, используемый в *_nx_crypto_method_md5_init()* .
- **crypto_metadata_size**: размер области crypto_metadata в байтах. Для MD5 размер метаданных должен быть равен *sizeof(NX_CRYPTO_MD5)* .
- **packet_ptr**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.
- **nx_crypto_hw_process_callback**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): операция MD5 успешно выполнена.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.
- **NX_PTR_ERROR** (0x07): недопустимый указатель ввода или длина.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004): указан недопустимый алгоритм MD5.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005): недопустимый размер выходного буфера.

## <a name="_nx_crypto_method_md5_cleanup"></a>_nx_crypto_method_md5_cleanup

Очистка блока управления MD5.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_md5_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Описание

Приложение вызывает эту функцию для очистки блока управления MD5 после того, как определит, что этот сеанс MD5 больше не требуется.

### <a name="parameters"></a>Параметры

- **crypto_metadata**: указатель на блок управления MD5, используемый в *_nx_crypto_method_md5_init()* .

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): сеанс MD5 успешно очищен.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.

## <a name="_nx_crypto_method_sha1_init"></a>_nx_crypto_method_sha1_init

Инициализация блока управления шифрованием SHA1.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_sha1_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Описание

Эта функция инициализирует блок управления SHA1 с заданной строкой ключа. После инициализации блока управления SHA1 последующая операция SHA1 должна использовать этот же блок управления.

Приложение может создать несколько блоков управления SHA1, представляющих отдельные сеансы. Инициализация блока управления SHA1 запускает новый сеанс вычисления хэша. Повторная инициализация блока управления SHA1 прекращает текущий сеанс и запускает новый.

### <a name="parameters"></a>Параметры

- **method**: указатель на допустимый блок управления методом шифрования SHA1. Доступны следующие стандартные методы шифрования:
  - *crypto_method_sha1*
- **key**: это поле не используется для SHA1.
- **key_size_in_bits**: это поле не используется для SHA1.
- **handle**: эта служба возвращает дескриптор вызывающей стороне. Этот дескриптор зависит от конкретной реализации и в данной реализации не используется. Приложение должно передать значение NULL для этого дескриптора.
- **crypto_metadata**: указатель на допустимое пространство памяти для блока управления SHA1. Начальный адрес пространства памяти должен быть выделен с буфером в 4 байта.
- **crypto_metadata_size**: размер области crypto_metadata в байтах. Для SHA1 размер метаданных должен быть равен *sizeof(NX_CRYPTO_SHA1)* .

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): блок управления SHA1 успешно инициализирован с заданными ключом и размером ключа.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.
- **NX_PTR_ERROR (0x07)** : недопустимый указатель на ключ, недопустимое значение crypto_metadata или crypto_metadata_size либо при выделении области crypto_metadata не был задан буфер в 4 байта.

## <a name="_nx_crypto_method_sha1_operation"></a>_nx_crypto_method_sha1_operation

Выполнение хэш-операции SHA1.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_sha1_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>Описание

Эта функция выполняет хэш-операцию SHA1. Блок управления SHA1 должен быть инициализирован с помощью службы _ *nx_crypto_method_sha1_init()* . Выполняемый алгоритм SHA1 основан на алгоритме, указанном в блоке управления *method*.

Для последней операции *NX_CRYPTO_HASH_CALCULATE* размер выходного буфера должен составлять 20 байт.

### <a name="parameters"></a>Параметры

- **op**: тип выполняемой операции. Допустимые операции:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.
- **method**: указатель на допустимый метод шифрования SHA1. Используемый здесь метод шифрования должен совпадать с методом, указанным в *nx_crypto_method_sha1_init()* .
- **input_data**: указывает на буфер, содержащий входные текстовые данные. Ограничения для входного буфера отсутствуют.
- **input_data_size**: размер входных данных в байтах.
- **iv_ptr**: это поле не используется для SHA1.
- **iv_size**: это поле не используется для SHA1.
- **output_buffer**: указатель на область памяти для созданного SHA1 хэша.
- **output_buffer_size**: размер выходного буфера в байтах. Для SHA1 размер буфера должен составлять 20 байт.
- **crypto_metadata**: указатель на блок управления SHA1, используемый в *_nx_crypto_method_sha1_init()* .
- **crypto_metadata_size**: размер области crypto_metadata в байтах. Для SHA1 размер метаданных должен быть равен *sizeof(NX_CRYPTO_SHA1)* .
- **packet_ptr**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.
- **nx_crypto_hw_process_callback**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): операция SHA1 успешно выполнена.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.
- **NX_PTR_ERROR** (0x07): недопустимый указатель ввода или длина.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004): указан недопустимый алгоритм SHA1.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005): недопустимый размер выходного буфера.

### <a name="example"></a>Например, .

## <a name="_nx_crypto_method_sha1_cleanup"></a>_nx_crypto_method_sha1_cleanup

Очистка блока управления SHA1.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_sha1_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Описание

Приложение вызывает эту функцию для очистки блока управления SHA1 после того, как определит, что этот сеанс SHA1 больше не требуется.

### <a name="parameters"></a>Параметры

- **crypto_metadata**: указатель на блок управления SHA1, используемый в *_nx_crypto_method_sha1_init()* .

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): сеанс SHA1 успешно очищен.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.

## <a name="_nx_crypto_method_sha256_init"></a>_nx_crypto_method_sha256_init

Инициализация блока управления шифрованием SHA256.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_sha256_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size)
```

### <a name="description"></a>Описание

Эта функция инициализирует блок управления SHA256 с заданной строкой ключа. После инициализации блока управления SHA256 последующая операция SHA256 должна использовать этот же блок управления.

Приложение может создать несколько блоков управления SHA256, представляющих отдельные сеансы. Инициализация блока управления SHA256 запускает новый сеанс вычисления хэша. Повторная инициализация блока управления SHA256 прекращает текущий сеанс и запускает новый.

### <a name="parameters"></a>Параметры

- **method**: указатель на допустимый блок управления методом шифрования SHA256. Доступны следующие стандартные методы шифрования:
  - *crypto_method_sha256*
  - *crypto_method_sha224*
- **key**: это поле не используется для SHA256.
- **key_size_in_bits**: это поле не используется для SHA256.
- **handle**: эта служба возвращает дескриптор вызывающей стороне. Этот дескриптор зависит от конкретной реализации и в данной реализации не используется. Приложение должно передать значение NULL для этого дескриптора.
- **crypto_metadata**: указатель на допустимое пространство памяти для блока управления SHA256. Начальный адрес пространства памяти должен быть выделен с буфером в 4 байта.
- **crypto_metadata_size**: размер области crypto_metadata в байтах. Для SHA256 размер метаданных должен быть равен *sizeof(NX_CRYPTO_SHA256)* .

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): блок управления SHA256 успешно инициализирован с заданными ключом и размером ключа.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.
- **NX_PTR_ERROR (0x07)** : недопустимый указатель на ключ, недопустимое значение crypto_metadata или crypto_metadata_size либо при выделении области crypto_metadata не был задан буфер в 4 байта.

## <a name="_nx_crypto_method_sha256_operation"></a>_nx_crypto_method_sha256_operation

Выполнение хэш-операции SHA256.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_sha256_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>Описание

Эта функция выполняет хэш-операцию SHA256. Блок управления SHA256 должен быть инициализирован с помощью службы _ ***nx_crypto_method_sha256_init()***. Выполняемый алгоритм SHA256 основан на алгоритме, указанном в блоке управления *method*.

Для последней операции *NX_CRYPTO_HASH_CALCULATE* размер выходного буфера должен составлять 32 байта для SHA256 или 28 байт для SHA224.

### <a name="parameters"></a>Параметры

- **op**: тип выполняемой операции. Допустимые операции:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.
- **method**: указатель на допустимый метод шифрования SHA256. Используемый здесь метод шифрования должен совпадать с методом, указанным в _ *nx_crypto_method_sha256_init()* .
- **input_data**: указывает на буфер, содержащий входные текстовые данные. Ограничения для входного буфера отсутствуют.
- **input_data_size**: размер входных данных в байтах.
- **iv_ptr**: это поле не используется для SHA256.
- **iv_size**: это поле не используется для SHA256.
- **output_buffer**: указатель на область памяти для созданного SHA256 хэша.
- **output_buffer_size**: размер выходного буфера в байтах. Для SHA256 размер буфера должен составлять 32 байта. Для SHA224 размер буфера должен составлять 28 байт.
- **crypto_metadata**: указатель на блок управления SHA2, используемый в *_nx_crypto_method_sha2_init()* .
- **crypto_metadata_size**: размер области crypto_metadata в байтах. Для SHA256 размер метаданных должен быть равен *sizeof(NX_CRYPTO_SHA256)* .
- **packet_ptr**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.
- **nx_crypto_hw_process_callback**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): операция SHA256 успешно выполнена.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.
- **NX_PTR_ERROR** (0x07): недопустимый указатель ввода или длина.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004): указан недопустимый алгоритм SHA256.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005): недопустимый размер выходного буфера.

## <a name="_nx_crypto_method_sha256_cleanup"></a>_nx_crypto_method_sha256_cleanup

Очистка блока управления SHA256.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_sha256_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Описание

Приложение вызывает эту функцию для очистки блока управления SHA256 после того, как определит, что этот сеанс SHA256 больше не требуется.

### <a name="parameters"></a>Параметры

- **crypto_metadata**: указатель на блок управления SHA256, используемый в *_nx_crypto_method_sha256_init()* .

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): сеанс SHA256 успешно очищен.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.

## <a name="_nx_crypto_method_sha512_init"></a>_nx_crypto_method_sha512_init

Инициализация блока управления шифрованием SHA512.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_sha512_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Описание

Эта функция инициализирует блок управления SHA512 с заданной строкой ключа. После инициализации блока управления SHA512 последующая операция SHA512 должна использовать этот же блок управления.

Приложение может создать несколько блоков управления SHA512, представляющих отдельные сеансы. Инициализация блока управления SHA512 запускает новый сеанс вычисления хэша. Повторная инициализация блока управления SHA512 прекращает текущий сеанс и запускает новый.

### <a name="parameters"></a>Параметры

- **method**: указатель на допустимый блок управления методом шифрования SHA512. Доступны следующие стандартные методы шифрования:
  - *crypto_method_sha512*
  - *crypto_method_sha384*
- **key**: это поле не используется для SHA512.
- **key_size_in_bits**: это поле не используется для SHA512.
- **handle**: эта служба возвращает дескриптор вызывающей стороне. Этот дескриптор зависит от конкретной реализации и в данной реализации не используется. Приложение должно передать значение NULL для этого дескриптора.
- **crypto_metadata**: указатель на допустимое пространство памяти для блока управления SHA512. Начальный адрес пространства памяти должен быть выделен с буфером в 4 байта.
- **crypto_metadata_size**: размер области crypto_metadata в байтах. Для SHA512 размер метаданных должен быть равен *sizeof(NX_CRYPTO_SHA512)* .

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): блок управления SHA512 успешно инициализирован с заданными ключом и размером ключа.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.
- **NX_PTR_ERROR (0x07)** : недопустимый указатель на ключ, недопустимое значение crypto_metadata или crypto_metadata_size либо при выделении области crypto_metadata не был задан буфер в 4 байта.

## <a name="_nx_crypto_method_sha512_operation"></a>_nx_crypto_method_sha512_operation

Выполнение хэш-операции SHA512.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_sha512_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT status));
```

### <a name="description"></a>Описание

Эта функция выполняет хэш-операцию SHA512. Блок управления SHA512 должен быть инициализирован с помощью службы _ *nx_crypto_method_sha512_init()* . Выполняемый алгоритм SHA512 основан на алгоритме, указанном в блоке управления *method*.

Для последней операции *NX_CRYPTO_HASH_CALCULATE* размер выходного буфера должен составлять 64 байта для SHA512 или 48 байт для SHA384.

### <a name="parameters"></a>Параметры

- **op**: тип выполняемой операции. Допустимые операции:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.
- **method**: указатель на допустимый метод шифрования SHA512. Используемый здесь метод шифрования должен совпадать с методом, указанным в _ *nx_crypto_method_sha512_init()* .
- **input_data**: указывает на буфер, содержащий входные текстовые данные. Ограничения для входного буфера отсутствуют.
- **input_data_size**: размер входных данных в байтах.
- **iv_ptr**: это поле не используется для SHA512.
- **iv_size**: это поле не используется для SHA512.
- **output_buffer**: указатель на область памяти для созданного SHA512 хэша.
- **output_buffer_size**: размер выходного буфера в байтах. Для SHA512 размер буфера должен составлять 64 байта. Для SHA384 размер буфера должен составлять 48 байт.
- **crypto_metadata**: указатель на блок управления SHA512, используемый в *_nx_crypto_method_sha512_init()* .
- **crypto_metadata_size**: размер области crypto_metadata в байтах. Для SHA512 размер метаданных должен быть равен *sizeof(NX_CRYPTO_SHA512)* .
- **packet_ptr**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.
- **nx_crypto_hw_process_callback**: это поле не используется в программной реализации библиотеки NetX Crypto. Любые переданные в него значения автоматически игнорируются.

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): операция SHA512 успешно выполнена.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.
- **NX_PTR_ERROR** (0x07): недопустимый указатель ввода или длина.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004): указан недопустимый алгоритм SHA512.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005): недопустимый размер выходного буфера.

## <a name="_nx_crypto_method_sha512_cleanup"></a>_nx_crypto_method_sha512_cleanup

Очистка блока управления SHA512.

### <a name="prototype"></a>Прототип

```c
UINT _nx_crypto_method_sha512_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Описание

Приложение вызывает эту функцию для очистки блока управления SHA512 после того, как определит, что этот сеанс SHA512 больше не требуется.

### <a name="parameters"></a>Параметры

- **crypto_metadata**: указатель на блок управления SHA512, используемый в *_nx_crypto_method_sha512_init()* .

### <a name="return-values"></a>Возвращаемые значения

- **NX_CRYPTO_SUCCESS** (0X00): сеанс SHA512 успешно очищен.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.