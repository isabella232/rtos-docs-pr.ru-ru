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
# <a name="chapter-4---azure-rtos-netx-crypto-api-description"></a><span data-ttu-id="95fd7-103">Глава 4. Описание API ОСРВ Azure NetX Crypto</span><span class="sxs-lookup"><span data-stu-id="95fd7-103">Chapter 4 - Azure RTOS NetX Crypto API description</span></span>

## <a name="nx_crypto_initialize"></a><span data-ttu-id="95fd7-104">nx_crypto_initialize</span><span class="sxs-lookup"><span data-stu-id="95fd7-104">nx_crypto_initialize</span></span>

<span data-ttu-id="95fd7-105">Инициализация библиотеки NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="95fd7-105">Initializes the NetX Secure Library</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-106">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-106">Prototype</span></span>

```c
UINT nx_crypto_initialize(VOID);
```

### <a name="description"></a><span data-ttu-id="95fd7-107">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-107">Description</span></span>

<span data-ttu-id="95fd7-108">Эта функция инициализирует модуль библиотеки ОСРВ Azure NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-108">This function initializes the Azure RTOS NetX Crypto library module.</span></span> <span data-ttu-id="95fd7-109">Прежде чем использовать какие-либо другие криптографические функции, приложение должно вызвать эту функцию для инициализации и проверки целостности библиотеки.</span><span class="sxs-lookup"><span data-stu-id="95fd7-109">Before using any of the other cryptographic functions, the application must call this function to perform initialization and to validate the integrity of the library.</span></span> <span data-ttu-id="95fd7-110">Сбой при вызове этой функции перед использованием других служб NetX Crypto приведет к возвращению ошибок.</span><span class="sxs-lookup"><span data-stu-id="95fd7-110">Failure to call this function before using other NetX Crypto services will result in errors being returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-111">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-111">Parameters</span></span>

- <span data-ttu-id="95fd7-112">**Нет**</span><span class="sxs-lookup"><span data-stu-id="95fd7-112">**None**</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-113">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-113">Return Values</span></span>

- <span data-ttu-id="95fd7-114">**NX_CRYPTO_SUCCESS** (0X00): библиотека NetX Crypto успешно инициализирована.</span><span class="sxs-lookup"><span data-stu-id="95fd7-114">**NX_CRYPTO_SUCCESS** (0x00) Successful initialized NetX Crypto library.</span></span> <span data-ttu-id="95fd7-115">Функции библиотеки теперь готовы и могут использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-115">The library functions are now ready, and can be used.</span></span>
- <span data-ttu-id="95fd7-116">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): не удается инициализировать библиотеку шифрования или выполнить проверку целостности.</span><span class="sxs-lookup"><span data-stu-id="95fd7-116">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library fails to initialize, or fails the integrity check.</span></span> <span data-ttu-id="95fd7-117">Приложение не может использовать эту библиотеку.</span><span class="sxs-lookup"><span data-stu-id="95fd7-117">Application cannot use this library.</span></span>

### <a name="example"></a><span data-ttu-id="95fd7-118">Например, .</span><span class="sxs-lookup"><span data-stu-id="95fd7-118">Example</span></span>

<span data-ttu-id="95fd7-119">TODO</span><span class="sxs-lookup"><span data-stu-id="95fd7-119">TODO</span></span>

## <a name="nx_crypto_module_state_get"></a><span data-ttu-id="95fd7-120">nx_crypto_module_state_get</span><span class="sxs-lookup"><span data-stu-id="95fd7-120">nx_crypto_module_state_get</span></span>

<span data-ttu-id="95fd7-121">Получение текущего состояния модуля с поддержкой FIPS.</span><span class="sxs-lookup"><span data-stu-id="95fd7-121">Retrieve the current status of the FIPS-enabled module</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-122">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-122">Prototype</span></span>

```c
UINT nx_crypto_module_state_get(VOID);
```

### <a name="description"></a><span data-ttu-id="95fd7-123">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-123">Description</span></span>

<span data-ttu-id="95fd7-124">Эта служба доступна только в сборке библиотеки с поддержкой FIPS.</span><span class="sxs-lookup"><span data-stu-id="95fd7-124">This service is only available in the FIPS build library.</span></span> <span data-ttu-id="95fd7-125">Она возвращает значение текущего состояния библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-125">It returns the state of the current state of the NetX Crypto library.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-126">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-126">Parameters</span></span>

- <span data-ttu-id="95fd7-127">**Нет**</span><span class="sxs-lookup"><span data-stu-id="95fd7-127">**None**</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-128">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-128">Return Values</span></span>

- <span data-ttu-id="95fd7-129">**Флаг состояния:**</span><span class="sxs-lookup"><span data-stu-id="95fd7-129">**Status Flag:**</span></span>
  - <span data-ttu-id="95fd7-130">NX_CRYPTO_LIBRARY_STATE_UNINITIALIZED 0x00000001</span><span class="sxs-lookup"><span data-stu-id="95fd7-130">NX_CRYPTO_LIBRARY_STATE_UNINITIALIZED 0x00000001</span></span>
  - <span data-ttu-id="95fd7-131">NX_CRYPTO_LIBRARY_STATE_POST_IN_PROGRESS 0x00000002</span><span class="sxs-lookup"><span data-stu-id="95fd7-131">NX_CRYPTO_LIBRARY_STATE_POST_IN_PROGRESS 0x00000002</span></span>
  - <span data-ttu-id="95fd7-132">NX_CRYPTO_LIBRARY_STATE_INTEGRITY_TEST_FAILED 0x00000004</span><span class="sxs-lookup"><span data-stu-id="95fd7-132">NX_CRYPTO_LIBRARY_STATE_INTEGRITY_TEST_FAILED 0x00000004</span></span>
  - <span data-ttu-id="95fd7-133">NX_CRYPTO_LIBRARY_STATE_FUNCTIONAL_TEST_FAILED 0x00000008</span><span class="sxs-lookup"><span data-stu-id="95fd7-133">NX_CRYPTO_LIBRARY_STATE_FUNCTIONAL_TEST_FAILED 0x00000008</span></span>
  - <span data-ttu-id="95fd7-134">NX_CRYPTO_LIBRARY_STATE_OPERATIONAL 0x80000000</span><span class="sxs-lookup"><span data-stu-id="95fd7-134">NX_CRYPTO_LIBRARY_STATE_OPERATIONAL 0x80000000</span></span>
- <span data-ttu-id="95fd7-135">**Все остальные значения недопустимы.**</span><span class="sxs-lookup"><span data-stu-id="95fd7-135">**All other values are invalid.**</span></span>

### <a name="example"></a><span data-ttu-id="95fd7-136">Например, .</span><span class="sxs-lookup"><span data-stu-id="95fd7-136">Example</span></span>

<span data-ttu-id="95fd7-137">TODO</span><span class="sxs-lookup"><span data-stu-id="95fd7-137">TODO</span></span>

## <a name="_nx_crypto_method_aes_init"></a><span data-ttu-id="95fd7-138">_nx_crypto_method_aes_init</span><span class="sxs-lookup"><span data-stu-id="95fd7-138">_nx_crypto_method_aes_init</span></span>

<span data-ttu-id="95fd7-139">Инициализация блока управления шифрованием AES.</span><span class="sxs-lookup"><span data-stu-id="95fd7-139">Initializes the AES crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-140">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-140">Prototype</span></span>

```c
UINT _nx_crypto_method_aes_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="95fd7-141">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-141">Description</span></span>

<span data-ttu-id="95fd7-142">Эта функция инициализирует блок управления AES с заданной строкой ключа.</span><span class="sxs-lookup"><span data-stu-id="95fd7-142">This function initializes the AES control block with the given key string.</span></span> <span data-ttu-id="95fd7-143">После инициализации блока управления AES последующие операции AES будут использовать этот ключ и размер ключа.</span><span class="sxs-lookup"><span data-stu-id="95fd7-143">Once the AES control block is initialized, subsequent AES operation will be using the same key and key size.</span></span>

<span data-ttu-id="95fd7-144">Приложение может создать несколько блоков управления AES, представляющих отдельные сеансы.</span><span class="sxs-lookup"><span data-stu-id="95fd7-144">Application may create multiple AES control blocks, each represents a session.</span></span> <span data-ttu-id="95fd7-145">Блоку управления назначается ключ.</span><span class="sxs-lookup"><span data-stu-id="95fd7-145">A key is assigned to a control block.</span></span> <span data-ttu-id="95fd7-146">Последующие операции шифрования или расшифровки могут ссылаться на один и тот же блок управления AES без необходимости повторной инициализации блока управления AES.</span><span class="sxs-lookup"><span data-stu-id="95fd7-146">Subsequent encryption or decryption operation can reference to the same AES control block without the need to re-initialize the AES control block.</span></span> <span data-ttu-id="95fd7-147">Если ключ для сеанса изменен, приложению необходимо повторно инициализировать блок управления AES с обновленным ключом.</span><span class="sxs-lookup"><span data-stu-id="95fd7-147">If the key for the session is changed, application needs to re-initialize AES control block with the updated key.</span></span>

<span data-ttu-id="95fd7-148">Вызов службы _ *nx_crypto_method_aes_init()* приводит к автоматическому обновлению настроенных ранее ключа и размера ключа в соответствии с новым ключом.</span><span class="sxs-lookup"><span data-stu-id="95fd7-148">Calling _ *nx_crypto_method_aes_init()* automatically updates a previously configured key and key size to the new key.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-149">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-149">Parameters</span></span>

- <span data-ttu-id="95fd7-150">**method**: указатель на допустимый блок управления методом шифрования AES.</span><span class="sxs-lookup"><span data-stu-id="95fd7-150">**method** Pointer to a valid AES crypto method control block.</span></span> <span data-ttu-id="95fd7-151">Доступны следующие стандартные методы шифрования AES:</span><span class="sxs-lookup"><span data-stu-id="95fd7-151">The following pre-defined AES crypto methods are available:</span></span>
  - <span data-ttu-id="95fd7-152">*crypto_method_aes_cbc_128*</span><span class="sxs-lookup"><span data-stu-id="95fd7-152">*crypto_method_aes_cbc_128*</span></span>
  - <span data-ttu-id="95fd7-153">*crypto_method_aes_cbc_192*</span><span class="sxs-lookup"><span data-stu-id="95fd7-153">*crypto_method_aes_cbc_192*</span></span>
  - <span data-ttu-id="95fd7-154">*crypto_method_aes_cbc_256*</span><span class="sxs-lookup"><span data-stu-id="95fd7-154">*crypto_method_aes_cbc_256*</span></span>
  - <span data-ttu-id="95fd7-155">*crypto_method_aes_ctr_128*</span><span class="sxs-lookup"><span data-stu-id="95fd7-155">*crypto_method_aes_ctr_128*</span></span>
  - <span data-ttu-id="95fd7-156">*crypto_method_aes_ctr_192*</span><span class="sxs-lookup"><span data-stu-id="95fd7-156">*crypto_method_aes_ctr_192*</span></span>
  - <span data-ttu-id="95fd7-157">*crypto_method_aes_ctr_256*</span><span class="sxs-lookup"><span data-stu-id="95fd7-157">*crypto_method_aes_ctr_256*</span></span>
  - <span data-ttu-id="95fd7-158">*crypto_method_aes_xcbc_128*</span><span class="sxs-lookup"><span data-stu-id="95fd7-158">*crypto_method_aes_xcbc_128*</span></span>
  - <span data-ttu-id="95fd7-159">*crypto_method_aes_ccm_8_128*</span><span class="sxs-lookup"><span data-stu-id="95fd7-159">*crypto_method_aes_ccm_8_128*</span></span>
- <span data-ttu-id="95fd7-160">**key**: указывает на буфер, содержащий ключ AES.</span><span class="sxs-lookup"><span data-stu-id="95fd7-160">**key** Points to a buffer containing the AES key</span></span>
- <span data-ttu-id="95fd7-161">**key_size_in_bits**: размер ключа в битах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-161">**key_size_in_bits** Size of the key, in bits.</span></span> <span data-ttu-id="95fd7-162">Допустимые значения:</span><span class="sxs-lookup"><span data-stu-id="95fd7-162">Valid values are:</span></span>
  - <span data-ttu-id="95fd7-163">*NX_CRYPTO_AES_KEY_SIZE_128_BITS*</span><span class="sxs-lookup"><span data-stu-id="95fd7-163">*NX_CRYPTO_AES_KEY_SIZE_128_BITS*</span></span>
  - <span data-ttu-id="95fd7-164">*NX_CRYPTO_AES_KEY_SIZE_192_BITS*</span><span class="sxs-lookup"><span data-stu-id="95fd7-164">*NX_CRYPTO_AES_KEY_SIZE_192_BITS*</span></span>
  - <span data-ttu-id="95fd7-165">*NX_CRYPTO_AES_KEY_SIZE_256_BITS*</span><span class="sxs-lookup"><span data-stu-id="95fd7-165">*NX_CRYPTO_AES_KEY_SIZE_256_BITS*</span></span>
  - <span data-ttu-id="95fd7-166">**Все остальные значения недопустимы.**</span><span class="sxs-lookup"><span data-stu-id="95fd7-166">**All other values are invalid.**</span></span>
- <span data-ttu-id="95fd7-167">**handle**: эта служба возвращает дескриптор вызывающей стороне.</span><span class="sxs-lookup"><span data-stu-id="95fd7-167">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="95fd7-168">Этот дескриптор зависит от конкретной реализации и в данной реализации не используется.</span><span class="sxs-lookup"><span data-stu-id="95fd7-168">The handle is implementation-dependent, and is not being used in this implementation.</span></span> <span data-ttu-id="95fd7-169">Приложение должно передать значение NULL для этого дескриптора.</span><span class="sxs-lookup"><span data-stu-id="95fd7-169">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="95fd7-170">**crypto_metadata**: указатель на допустимое пространство памяти для блока управления AES.</span><span class="sxs-lookup"><span data-stu-id="95fd7-170">**crypto_metadata** Pointer to a valid memory space for the AES control block.</span></span> <span data-ttu-id="95fd7-171">Начальный адрес пространства памяти должен быть выделен с буфером в 4 байта.</span><span class="sxs-lookup"><span data-stu-id="95fd7-171">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="95fd7-172">**crypto_metadata_size**: размер области crypto_metadata в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-172">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="95fd7-173">Для AES размер метаданных должен быть равен *sizeof(NX_AES)* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-173">For AES, the metadata size must be *sizeof(NX_AES)*</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-174">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-174">Return Values</span></span>

- <span data-ttu-id="95fd7-175">**NX_CRYPTO_SUCCESS** (0X00): блок управления AES успешно инициализирован с заданными ключом и размером ключа.</span><span class="sxs-lookup"><span data-stu-id="95fd7-175">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the AES control block with the key and key size.</span></span>
- <span data-ttu-id="95fd7-176">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-176">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="95fd7-177">**NX_PTR_ERROR (0x07)** : недопустимый указатель на ключ, недопустимое значение crypto_metadata или crypto_metadata_size либо при выделении области crypto_metadata не был задан буфер в 4 байта.</span><span class="sxs-lookup"><span data-stu-id="95fd7-177">**NX_PTR_ERROR (0x07)** Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>
- <span data-ttu-id="95fd7-178">**NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002): размер ключа не является допустимым для AES.</span><span class="sxs-lookup"><span data-stu-id="95fd7-178">**NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) Key size is not a valid for AES.</span></span>

## <a name="_nx_crypto_method_aes_operation"></a><span data-ttu-id="95fd7-179">_nx_crypto_method_aes_operation</span><span class="sxs-lookup"><span data-stu-id="95fd7-179">_nx_crypto_method_aes_operation</span></span>

<span data-ttu-id="95fd7-180">Выполнение операции AES (шифрование или расшифровка).</span><span class="sxs-lookup"><span data-stu-id="95fd7-180">Perform an AES operation (encryption or decryption).</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-181">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-181">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="95fd7-182">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-182">Description</span></span>

<span data-ttu-id="95fd7-183">Эта функция выполняет операцию шифрования или расшифровки AES.</span><span class="sxs-lookup"><span data-stu-id="95fd7-183">This function performs AES encryption or decryption operation.</span></span> <span data-ttu-id="95fd7-184">Блок управления AES должен быть инициализирован с помощью службы _ *nx_crypto_method_aes_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-184">The AES control block must have been initialized with _ *nx_crypto_method_aes_init()*.</span></span> <span data-ttu-id="95fd7-185">Выполняемый алгоритм AES основан на алгоритме, указанном в блоке управления *method*.</span><span class="sxs-lookup"><span data-stu-id="95fd7-185">The AES algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="95fd7-186">Размер входного буфера должен быть кратен 16 байтам.</span><span class="sxs-lookup"><span data-stu-id="95fd7-186">The input buffer size must be a multiple of 16 bytes.</span></span> <span data-ttu-id="95fd7-187">Размер расшифрованных данных равен размеру входных данных.</span><span class="sxs-lookup"><span data-stu-id="95fd7-187">The size of the decrypted data is the same size of the input data size.</span></span> <span data-ttu-id="95fd7-188">Если зашифрованные данные были заполнены до размера, кратного блоку AES, то данные заполнения будут помещены в выходной буфер и должны обрабатываться приложением.</span><span class="sxs-lookup"><span data-stu-id="95fd7-188">If the encrypted data was padded to achieve an even multiple of the AES block size, the padding will be included in the output buffer and must be handled by the application.</span></span>

<span data-ttu-id="95fd7-189">Эта операция не сохраняет сведения о состоянии и не изменяет материал ключа в блоке управления AES.</span><span class="sxs-lookup"><span data-stu-id="95fd7-189">This operation does not keep state information, and does not alter the key material in the AES control block.</span></span>

<span data-ttu-id="95fd7-190">Когда op имеет значение NX_CRYPTO_SET_ADDITIONAL_DATA и указан алгоритм AES-CCM8, input указывает на дополнительные данные, а input_length_in_byte — это длина дополнительных данных.</span><span class="sxs-lookup"><span data-stu-id="95fd7-190">When the op is NX_CRYPTO_SET_ADDITIONAL_DATA and algoritm is AES-CCM8, the input points to additional data and input_length_in_byte is the length of additional data.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-191">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-191">Parameters</span></span>

- <span data-ttu-id="95fd7-192">**op**: тип выполняемой операции.</span><span class="sxs-lookup"><span data-stu-id="95fd7-192">**op** Type of operation to perform.</span></span> <span data-ttu-id="95fd7-193">Допустимые операции:</span><span class="sxs-lookup"><span data-stu-id="95fd7-193">Valid opertions are:</span></span>
  - <span data-ttu-id="95fd7-194">*NX_CRYPTO_ENCRYPT*</span><span class="sxs-lookup"><span data-stu-id="95fd7-194">*NX_CRYPTO_ENCRYPT*</span></span>
  - <span data-ttu-id="95fd7-195">*NX_CRYPTO_DECRYPT*</span><span class="sxs-lookup"><span data-stu-id="95fd7-195">*NX_CRYPTO_DECRYPT*</span></span>
  - <span data-ttu-id="95fd7-196">*NX_CRYPTO_AUTHENTICATE (только AES-XCBC)*</span><span class="sxs-lookup"><span data-stu-id="95fd7-196">*NX_CRYPTO_AUTHENTICATE (AES-XCBC only)*</span></span>
  - <span data-ttu-id="95fd7-197">*NX_CRYPTO_SET_ADDITIONAL_DATA (только AES-CCM8)*</span><span class="sxs-lookup"><span data-stu-id="95fd7-197">*NX_CRYPTO_SET_ADDITIONAL_DATA (AES-CCM8 only)*</span></span>
- <span data-ttu-id="95fd7-198">**handle**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-198">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-199">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-199">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="95fd7-200">**method**: указатель на допустимый метод шифрования AES.</span><span class="sxs-lookup"><span data-stu-id="95fd7-200">**method** Pointer to the valid AES crypto method.</span></span> <span data-ttu-id="95fd7-201">Используемый здесь метод шифрования должен совпадать с методом, указанным в *nx_crypto_method_aes_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-201">The crypto method used here must be the same used in the *nx_crypto_method_aes_init().*</span></span>
- <span data-ttu-id="95fd7-202">**input_data**: указывает на буфер, содержащий зашифрованные текстовые данные.</span><span class="sxs-lookup"><span data-stu-id="95fd7-202">**input_data** Points to a buffer containing encrypted text data.</span></span> <span data-ttu-id="95fd7-203">Ограничения для входного буфера отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="95fd7-203">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="95fd7-204">**input_data_size**: размер входных данных в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-204">**input_data_size** Size of the input data, in bytes.</span></span> <span data-ttu-id="95fd7-205">Размер входных данных должен быть кратен 16 байтам.</span><span class="sxs-lookup"><span data-stu-id="95fd7-205">The input data size must be a multiple of 16 bytes.</span></span>
- <span data-ttu-id="95fd7-206">**iv_ptr**: указатель на начальный вектор (IV).</span><span class="sxs-lookup"><span data-stu-id="95fd7-206">**iv_ptr** Pointer to the Initial Vector.</span></span> <span data-ttu-id="95fd7-207">Ограничения для буфера начальных векторов отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="95fd7-207">There are no restrictions on the IV buffer.</span></span>
- <span data-ttu-id="95fd7-208">**iv_size**: размер блока начального вектора (в байтах). Это поле должно иметь значение 16.</span><span class="sxs-lookup"><span data-stu-id="95fd7-208">**iv_size** Size of the Initial Vector block, in bytes This field must be 16.</span></span>
- <span data-ttu-id="95fd7-209">**output_buffer**: указатель на область памяти для AES, в которой хранятся данные в виде открытого текста.</span><span class="sxs-lookup"><span data-stu-id="95fd7-209">**output_buffer** Pointer to the memory area for AES to store the clear text data.</span></span> <span data-ttu-id="95fd7-210">Приложение должно выделить пространство для выходного буфера.</span><span class="sxs-lookup"><span data-stu-id="95fd7-210">Application must allocate space for the output buffer.</span></span> <span data-ttu-id="95fd7-211">Выходной буфер может перекрывать входной буфер.</span><span class="sxs-lookup"><span data-stu-id="95fd7-211">Output buffer may overlap with input buffer.</span></span> <span data-ttu-id="95fd7-212">Выходной буфер может перекрыть входной буфер, если у них одинаковый начальный адрес.</span><span class="sxs-lookup"><span data-stu-id="95fd7-212">The output buffer may overlap with the input buffer if they share the same starting address.</span></span>
- <span data-ttu-id="95fd7-213">**output_buffer_size**: размер выходного буфера в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-213">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="95fd7-214">Размер выходного буфера должен быть не меньше размера входного буфера. Кроме того, размер выходного буфера должен быть кратен 16 байтам.</span><span class="sxs-lookup"><span data-stu-id="95fd7-214">Output buffer size must be at least the same of the input buffer size, and the output buffer size must be a multiple of 16 bytes.</span></span>
- <span data-ttu-id="95fd7-215">**crypto_metadata**: указатель на блок управления AES, используемый в *_nx_crypto_method_aes_init(\*)\*.*</span><span class="sxs-lookup"><span data-stu-id="95fd7-215">**crypto_metadata** Pointer to the AES control block used in *_nx_crypto_method_aes_init()\*.\**</span></span>
- <span data-ttu-id="95fd7-216">**crypto_metadata_size**: размер области crypto_metadata в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-216">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="95fd7-217">Для AES размер метаданных должен быть равен *sizeof(NX_AES)* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-217">For AES, the metadata size must *sizeof(NX_AES)*</span></span>
- <span data-ttu-id="95fd7-218">**packet_ptr**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-218">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-219">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-219">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="95fd7-220">**nx_crypto_hw_process_callback**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-220">**nx_crypto_hw_process_callback** - This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-221">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-221">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-222">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-222">Return Values</span></span>

- <span data-ttu-id="95fd7-223">**NX_CRYPTO_SUCCESS** (0X00): операция AES успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="95fd7-223">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the AES operation.</span></span>
- <span data-ttu-id="95fd7-224">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-224">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="95fd7-225">**NX_PTR_ERROR** (0x07): недопустимый указатель ввода или длина.</span><span class="sxs-lookup"><span data-stu-id="95fd7-225">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="95fd7-226">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004): указан недопустимый алгоритм AES\*\*.</span><span class="sxs-lookup"><span data-stu-id="95fd7-226">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid AES algorithm being specified\*\*.</span></span>

## <a name="_nx_crypto_method_aes_cleanup"></a><span data-ttu-id="95fd7-227">_nx_crypto_method_aes_cleanup</span><span class="sxs-lookup"><span data-stu-id="95fd7-227">_nx_crypto_method_aes_cleanup</span></span>

<span data-ttu-id="95fd7-228">Очистка блока управления AES.</span><span class="sxs-lookup"><span data-stu-id="95fd7-228">Clean up the AES control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-229">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-229">Prototype</span></span>

```c
UINT _nx_crypto_method_aes_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="95fd7-230">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-230">Description</span></span>

<span data-ttu-id="95fd7-231">Приложение вызывает эту функцию для очистки блока управления AES после того, как определит, что этот сеанс AES больше не требуется.</span><span class="sxs-lookup"><span data-stu-id="95fd7-231">Application calls this function to clean up the AES control block after it determines this AES session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-232">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-232">Parameters</span></span>

- <span data-ttu-id="95fd7-233">**crypto_metadata**: указатель на блок управления AES, используемый в *_nx_crypto_method_aes_init(\*)\*.*</span><span class="sxs-lookup"><span data-stu-id="95fd7-233">**crypto_metadata** Pointer to the AES control block used in *_nx_crypto_method_aes_init()\*.\**</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-234">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-234">Return Values</span></span>

- <span data-ttu-id="95fd7-235">**NX_CRYPTO_SUCCESS** (0X00): сеанс AES успешно очищен.</span><span class="sxs-lookup"><span data-stu-id="95fd7-235">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the AES session.</span></span>
- <span data-ttu-id="95fd7-236">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-236">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_3des_init"></a><span data-ttu-id="95fd7-237">_nx_crypto_method_3des_init</span><span class="sxs-lookup"><span data-stu-id="95fd7-237">_nx_crypto_method_3des_init</span></span>

<span data-ttu-id="95fd7-238">Инициализация блока управления 3DES.</span><span class="sxs-lookup"><span data-stu-id="95fd7-238">Initialize the 3DES control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-239">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-239">Prototype</span></span>

```c
UINT _nx_crypto_method_3des_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="95fd7-240">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-240">Description</span></span>

<span data-ttu-id="95fd7-241">Эта функция инициализирует блок управления Triple DES (3DES) с применением трех заданных строк ключа.</span><span class="sxs-lookup"><span data-stu-id="95fd7-241">This function initializes the Triple DES (3DES) control block with the given three key strings.</span></span> <span data-ttu-id="95fd7-242">Каждая строка ключа должна содержать 8 байт.</span><span class="sxs-lookup"><span data-stu-id="95fd7-242">The key strings must be 8 bytes each.</span></span> <span data-ttu-id="95fd7-243">Три ключа DES необходимо объединить в непрерывную область памяти размером в 24 байта в буфере.</span><span class="sxs-lookup"><span data-stu-id="95fd7-243">The three DES keys must be concatenated into contiguous memory of 24-byte buffer.</span></span> <span data-ttu-id="95fd7-244">Для сборки с поддержкой FIPS эти три ключа должны быть разными, иначе функция вернет ошибку NX_CRYPTO_INVALID_KEY.</span><span class="sxs-lookup"><span data-stu-id="95fd7-244">For FIPS-compliant build, the three keys must be different from each or the function will return the NX_CRYPTO_INVALID_KEY error.</span></span> <span data-ttu-id="95fd7-245">После инициализации блока управления 3DES последующие операции 3DES будут использовать эти же ключи.</span><span class="sxs-lookup"><span data-stu-id="95fd7-245">Once the 3DES control block is initialized, subsequent 3DES operations will use the same keys.</span></span>

<span data-ttu-id="95fd7-246">Приложение может создать несколько блоков управления 3DES, представляющих отдельные сеансы.</span><span class="sxs-lookup"><span data-stu-id="95fd7-246">An application may create multiple 3DES control blocks, each representing a session.</span></span> <span data-ttu-id="95fd7-247">Ключ назначается блоку управления, и последующие операции шифрования или расшифровки могут ссылаться на один и тот же блок управления без необходимости повторной инициализации.</span><span class="sxs-lookup"><span data-stu-id="95fd7-247">A key is assigned to a control block and subsequent encryption or decryption operations can reference the same control block without needing to re-initialize.</span></span> <span data-ttu-id="95fd7-248">Если ключ для сеанса будет изменен, приложению потребуется повторно инициализировать блок управления с обновленным ключом.</span><span class="sxs-lookup"><span data-stu-id="95fd7-248">If the key for a session is changed, the application will need to re-initialize the control block with the updated key.</span></span>

<span data-ttu-id="95fd7-249">Вызов службы _ *nx_crypto_method_3des_init()* приводит к автоматическому обновлению настроенного ранее ключа в соответствии с новыми ключами.</span><span class="sxs-lookup"><span data-stu-id="95fd7-249">Calling _ *nx_crypto_method_3des_init()* automatically updates a previously configured key to the new keys.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-250">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-250">Parameters</span></span>

- <span data-ttu-id="95fd7-251">**method**: указатель на допустимый блок управления методом шифрования 3DES.</span><span class="sxs-lookup"><span data-stu-id="95fd7-251">**method** Pointer to a valid 3DES crypto method control block.</span></span> <span data-ttu-id="95fd7-252">Доступен следующий стандартный метод шифрования 3DES: ***crypto_method_3des***.</span><span class="sxs-lookup"><span data-stu-id="95fd7-252">The following pre-defined 3DES crypto method is available: ***crypto_method_3des***</span></span>
- <span data-ttu-id="95fd7-253">**key**: указывает на буфер, содержащий три ключа 3DES.</span><span class="sxs-lookup"><span data-stu-id="95fd7-253">**key** Points to a buffer containing the three (3) DES key</span></span>
- <span data-ttu-id="95fd7-254">**key_size_in_bits**: должен иметь значение 192 (3 ключа по 64 бит).</span><span class="sxs-lookup"><span data-stu-id="95fd7-254">**key_size_in_bits** Must be 192 (3 keys, each 64 bits).</span></span>
- <span data-ttu-id="95fd7-255">**handle**: эта служба возвращает дескриптор вызывающей стороне.</span><span class="sxs-lookup"><span data-stu-id="95fd7-255">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="95fd7-256">Этот дескриптор определяет инициализируемый блок управления 3DES.</span><span class="sxs-lookup"><span data-stu-id="95fd7-256">The handle identifies the 3DES control block being initialized.</span></span> <span data-ttu-id="95fd7-257">Последующие операции 3DES (шифрование, расшифровка и очистка) будут использовать этот дескриптор для обращения к блоку управления 3DES.</span><span class="sxs-lookup"><span data-stu-id="95fd7-257">Subsequent 3DES operations (encryption, decryption, and cleanup) use this handle to access the 3DES control block</span></span>
- <span data-ttu-id="95fd7-258">**crypto_metadata**: указатель на допустимое пространство памяти для блока управления 3DES.</span><span class="sxs-lookup"><span data-stu-id="95fd7-258">**crypto_metadata** Pointer to a valid memory space for the 3DES control block.</span></span> <span data-ttu-id="95fd7-259">Начальный адрес пространства памяти должен быть выделен с буфером в 4 байта.</span><span class="sxs-lookup"><span data-stu-id="95fd7-259">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="95fd7-260">**crypto_metadata_size**: размер области crypto_metadata в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-260">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="95fd7-261">Для 3DES размер метаданных должен быть равен *sizeof(NX_3DES)* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-261">For 3DES, the metadata size must be *sizeof(NX_3DES)*</span></span>

### <a name="return-value"></a><span data-ttu-id="95fd7-262">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="95fd7-262">Return Value</span></span>

- <span data-ttu-id="95fd7-263">**NX_CRYPTO_SUCCESS** (0X00): блок управления 3DES успешно инициализирован с заданными ключом и размером ключа.</span><span class="sxs-lookup"><span data-stu-id="95fd7-263">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the 3DES control block with the key and key size.</span></span>
- <span data-ttu-id="95fd7-264">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-264">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="95fd7-265">**NX_PTR_ERROR (0x07)** : недопустимый указатель на ключ, недопустимое значение crypto_metadata или crypto_metadata_size либо при выделении области crypto_metadata не был задан буфер в 4 байта.</span><span class="sxs-lookup"><span data-stu-id="95fd7-265">**NX_PTR_ERROR (0x07)** Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>
- <span data-ttu-id="95fd7-266">**NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002): размер ключа не является допустимым для 3DES.</span><span class="sxs-lookup"><span data-stu-id="95fd7-266">**NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) Key size is not a valid for 3DES.</span></span>

## <a name="_nx_crypto_method_3des_operation"></a><span data-ttu-id="95fd7-267">_nx_crypto_method_3des_operation</span><span class="sxs-lookup"><span data-stu-id="95fd7-267">_nx_crypto_method_3des_operation</span></span>

<span data-ttu-id="95fd7-268">Шифрование или расшифровка с помощью 3DES.</span><span class="sxs-lookup"><span data-stu-id="95fd7-268">Encrypt or Decrypt with 3DES.</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-269">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-269">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="95fd7-270">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-270">Description</span></span>

<span data-ttu-id="95fd7-271">Эта функция выполняет операцию шифрования или расшифровки 3DES.</span><span class="sxs-lookup"><span data-stu-id="95fd7-271">This function performs 3DES encryption or decryption operation.</span></span> <span data-ttu-id="95fd7-272">Блок управления 3DES должен быть инициализирован с помощью службы _ *nx_crypto_method_3des_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-272">The 3DES control block must have been initialized with _ *nx_crypto_method_3des_init()*.</span></span> <span data-ttu-id="95fd7-273">Выполняемый алгоритм 3DES основан на алгоритме, указанном в блоке управления *method*.</span><span class="sxs-lookup"><span data-stu-id="95fd7-273">The 3DES algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="95fd7-274">Размер входного буфера должен быть кратен 8 байтам.</span><span class="sxs-lookup"><span data-stu-id="95fd7-274">The input buffer size must be a multiple of 8 bytes.</span></span> <span data-ttu-id="95fd7-275">Размер расшифрованных данных равен размеру входных данных.</span><span class="sxs-lookup"><span data-stu-id="95fd7-275">The size of the decrypted data is the same size of the input data size.</span></span> <span data-ttu-id="95fd7-276">Если зашифрованные данные были заполнены до размера, кратного блоку 3DES, то данные заполнения будут помещены в выходной буфер и должны обрабатываться приложением.</span><span class="sxs-lookup"><span data-stu-id="95fd7-276">If the encrypted data was padded to achieve an even multiple of the 3DES block size, the padding will be included in the output buffer and must be handled by the application.</span></span>

<span data-ttu-id="95fd7-277">Эта операция не сохраняет сведения о состоянии и не изменяет материал ключа в блоке управления 3DES.</span><span class="sxs-lookup"><span data-stu-id="95fd7-277">This operation does not keep state information, and does not alter the key material in the 3DES control block.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-278">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-278">Parameters</span></span>

- <span data-ttu-id="95fd7-279">**op**: тип выполняемой операции.</span><span class="sxs-lookup"><span data-stu-id="95fd7-279">**op** Type of operation to perform.</span></span> <span data-ttu-id="95fd7-280">Допустимые операции:</span><span class="sxs-lookup"><span data-stu-id="95fd7-280">Valid operations are:</span></span>
  - <span data-ttu-id="95fd7-281">*NX_CRYPTO_ENCRYPT*</span><span class="sxs-lookup"><span data-stu-id="95fd7-281">*NX_CRYPTO_ENCRYPT*</span></span>
  - <span data-ttu-id="95fd7-282">*NX_CRYPTO_DECRYPT*</span><span class="sxs-lookup"><span data-stu-id="95fd7-282">*NX_CRYPTO_DECRYPT*</span></span>
- <span data-ttu-id="95fd7-283">**handle**: дескриптор, инициализируемый службой *_nx_crypto_method_3des_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-283">**handle** The handle initialized by *_nx_crypto_method_3des_init()*.</span></span>
- <span data-ttu-id="95fd7-284">**method**: указатель на допустимый метод шифрования 3DES.</span><span class="sxs-lookup"><span data-stu-id="95fd7-284">**method** Pointer to the valid 3DES crypto method.</span></span> <span data-ttu-id="95fd7-285">Используемый здесь метод шифрования должен совпадать с методом, указанным в *nx_crypto_method_3des_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-285">The crypto method used here must be the same used in the *nx_crypto_method_3des_init().*</span></span>
- <span data-ttu-id="95fd7-286">**input_data**: указывает на буфер, содержащий зашифрованные текстовые данные.</span><span class="sxs-lookup"><span data-stu-id="95fd7-286">**input_data** Points to a buffer containing encrypted text data.</span></span>
<span data-ttu-id="95fd7-287">Ограничения для входного буфера отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="95fd7-287">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="95fd7-288">**input_data_size**: размер входных данных в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-288">**input_data_size** Size of the input data, in bytes.</span></span> <span data-ttu-id="95fd7-289">Размер входных данных должен быть кратен 8 байтам.</span><span class="sxs-lookup"><span data-stu-id="95fd7-289">The input data size must be a multiple of 8 bytes.</span></span>
- <span data-ttu-id="95fd7-290">**iv_ptr**: указатель на начальный вектор (IV).</span><span class="sxs-lookup"><span data-stu-id="95fd7-290">**iv_ptr** Pointer to the Initial Vector.</span></span> <span data-ttu-id="95fd7-291">Ограничения для буфера начальных векторов отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="95fd7-291">There are no restrictions on the IV buffer.</span></span>
- <span data-ttu-id="95fd7-292">**iv_size**: размер блока начального вектора (в байтах). Это поле должно иметь значение 8.</span><span class="sxs-lookup"><span data-stu-id="95fd7-292">**iv_size** Size of the Initial Vector block, in bytes This field must be 8.</span></span>
- <span data-ttu-id="95fd7-293">**output_buffer**: указатель на область памяти для 3DES, в которой хранятся данные в виде открытого текста.</span><span class="sxs-lookup"><span data-stu-id="95fd7-293">**output_buffer** Pointer to the memory area for 3DES to store the clear text data.</span></span> <span data-ttu-id="95fd7-294">Приложение должно выделить пространство для выходного буфера.</span><span class="sxs-lookup"><span data-stu-id="95fd7-294">Application must allocate space for the output buffer.</span></span> <span data-ttu-id="95fd7-295">Выходной буфер может перекрывать входной буфер.</span><span class="sxs-lookup"><span data-stu-id="95fd7-295">Output buffer may overlap with input buffer.</span></span> <span data-ttu-id="95fd7-296">Выходной буфер может перекрыть входной буфер, если у них одинаковый начальный адрес.</span><span class="sxs-lookup"><span data-stu-id="95fd7-296">The output buffer may overlap with the input buffer if they share the same starting address.</span></span>
- <span data-ttu-id="95fd7-297">**output_buffer_size**: размер выходного буфера в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-297">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="95fd7-298">Размер выходного буфера должен быть не меньше размера входного буфера. Кроме того, размер выходного буфера должен быть кратен 8 байтам.</span><span class="sxs-lookup"><span data-stu-id="95fd7-298">Output buffer size must be at least the same of the input buffer size, and the output buffer size must be a multiple of 8 bytes.</span></span>
- <span data-ttu-id="95fd7-299">**crypto_metadata**: указатель на блок управления 3DES, используемый в *_nx_crypto_method_3des_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-299">**crypto_metadata** Pointer to the 3DES control block used in *_nx_crypto_method_3des_init()*.</span></span>
- <span data-ttu-id="95fd7-300">**crypto_metadata_size**: размер области crypto_metadata в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-300">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="95fd7-301">Для 3DES размер метаданных должен быть равен *sizeof(NX_3DES)* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-301">For 3DES, the metadata size must be *sizeof(NX_3DES)*</span></span>
- <span data-ttu-id="95fd7-302">**packet_ptr**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-302">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-303">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-303">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="95fd7-304">**nx_crypto_hw_process_callback**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-304">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-305">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-305">Any values passed in are silently ignored.</span></span>

### <a name="description"></a><span data-ttu-id="95fd7-306">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-306">Description</span></span>

<span data-ttu-id="95fd7-307">Эта функция выполняет шифрование 3DES.</span><span class="sxs-lookup"><span data-stu-id="95fd7-307">This function performs 3DES encryption.</span></span> <span data-ttu-id="95fd7-308">Блок управления 3DES должен быть инициализирован с помощью службы _ *nx_crypto_method_3des_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-308">The 3DES control block must have been initialized with _ *nx_crypto_moethod_3des_init()*.</span></span> <span data-ttu-id="95fd7-309">Эта операция не сохраняет сведения о состоянии и не изменяет материал ключа в блоке управления 3DES.</span><span class="sxs-lookup"><span data-stu-id="95fd7-309">This operation does not keep state information, and does not alter the key material in the 3DES control block.</span></span> <span data-ttu-id="95fd7-310">Обратите внимание на то, что эта функция не применяет заполнение, поэтому вызывающему объекту потребуется выполнить заполнение перед вызовом операции шифрования.</span><span class="sxs-lookup"><span data-stu-id="95fd7-310">Note that padding is not added by this function so the caller will need to handle padding before invoking the encryption operation.</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-311">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-311">Return Values</span></span>

- <span data-ttu-id="95fd7-312">**NX_CRYPTO_SUCCESS** (0X00): блок управления 3DES успешно инициализирован с заданными ключом и размером ключа.</span><span class="sxs-lookup"><span data-stu-id="95fd7-312">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the 3DES control block with the key and key size.</span></span>
- <span data-ttu-id="95fd7-313">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-313">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="95fd7-314">**NX_PTR_ERROR (0x07)** : недопустимый указатель на ключ, недопустимое значение crypto_metadata или crypto_metadata_size либо при выделении области crypto_metadata не был задан буфер в 4 байта.</span><span class="sxs-lookup"><span data-stu-id="95fd7-314">**NX_PTR_ERROR (0x07)** Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_3des_cleanup"></a><span data-ttu-id="95fd7-315">_nx_crypto_method_3des_cleanup</span><span class="sxs-lookup"><span data-stu-id="95fd7-315">_nx_crypto_method_3des_cleanup</span></span>

<span data-ttu-id="95fd7-316">Очистка блока управления 3DES.</span><span class="sxs-lookup"><span data-stu-id="95fd7-316">Clean up the 3DES control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-317">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-317">Prototype</span></span>

```c
UINT _nx_crypto_method_3des_cleanup(VOID *crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="95fd7-318">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-318">Description</span></span>

<span data-ttu-id="95fd7-319">Приложение вызывает эту функцию для очистки блока управления 3DES после того, как определит, что этот сеанс 3DES больше не требуется.</span><span class="sxs-lookup"><span data-stu-id="95fd7-319">Application calls this function to clean up the 3DES control block after it determines this 3DES session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-320">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-320">Parameters</span></span>

- <span data-ttu-id="95fd7-321">**handle**: дескриптор, инициализируемый службой *_nx_crypto_method_3des_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-321">**handle** The handle initialized by *_nx_crypto_method_3des_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-322">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-322">Return Values</span></span>

- <span data-ttu-id="95fd7-323">**NX_CRYPTO_SUCCESS** (0X00): сеанс 3DES успешно очищен.</span><span class="sxs-lookup"><span data-stu-id="95fd7-323">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the 3DES session.</span></span>
- <span data-ttu-id="95fd7-324">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-324">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_drbg_init"></a><span data-ttu-id="95fd7-325">_nx_crypto_method_drbg_init</span><span class="sxs-lookup"><span data-stu-id="95fd7-325">_nx_crypto_method_drbg_init</span></span>

<span data-ttu-id="95fd7-326">Инициализация блока управления шифрованием DRBG.</span><span class="sxs-lookup"><span data-stu-id="95fd7-326">Initializes the DRBG crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-327">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-327">Prototype</span></span>

```c
UINT _nx_crypto_method_drbg_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="95fd7-328">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-328">Description</span></span>

<span data-ttu-id="95fd7-329">Эта функция инициализирует блок управления DRBG с заданной строкой ключа.</span><span class="sxs-lookup"><span data-stu-id="95fd7-329">This function initializes the DRBG control block with the given key string.</span></span> <span data-ttu-id="95fd7-330">После инициализации блока управления DRBG последующая операция DRBG должна использовать этот же блок управления.</span><span class="sxs-lookup"><span data-stu-id="95fd7-330">Once the DRBG control block is initialized, subsequent DRBG operation shall be using the same control block.</span></span>

<span data-ttu-id="95fd7-331">Приложение может создать несколько блоков управления DRBG, представляющих отдельные сеансы.</span><span class="sxs-lookup"><span data-stu-id="95fd7-331">Application may create multiple DRBG control blocks, each represents a session.</span></span> <span data-ttu-id="95fd7-332">Инициализация блока управления DRBG запускает новый сеанс вычисления хэша.</span><span class="sxs-lookup"><span data-stu-id="95fd7-332">Initializing the DRBG control block starts a new hash computation session.</span></span> <span data-ttu-id="95fd7-333">Повторная инициализация блока управления DRBG прекращает текущий сеанс и запускает новый.</span><span class="sxs-lookup"><span data-stu-id="95fd7-333">Re-initializing the DRBG control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-334">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-334">Parameters</span></span>

- <span data-ttu-id="95fd7-335">**method**: указатель на допустимый блок управления методом шифрования DRBG.</span><span class="sxs-lookup"><span data-stu-id="95fd7-335">**method** Pointer to a valid DRBG crypto method control block.</span></span> <span data-ttu-id="95fd7-336">Доступны следующие стандартные методы шифрования:</span><span class="sxs-lookup"><span data-stu-id="95fd7-336">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="95fd7-337">*crypto_method_drbg*</span><span class="sxs-lookup"><span data-stu-id="95fd7-337">*crypto_method_drbg*</span></span>
- <span data-ttu-id="95fd7-338">**key**: это поле не используется для DRBG.</span><span class="sxs-lookup"><span data-stu-id="95fd7-338">**key** This field is not used for DRBG.</span></span>
- <span data-ttu-id="95fd7-339">**key_size_in_bits**: это поле не используется для DRBG.</span><span class="sxs-lookup"><span data-stu-id="95fd7-339">**key_size_in_bits** This field is not used for DRBG.</span></span>
- <span data-ttu-id="95fd7-340">**handle**: эта служба возвращает дескриптор вызывающей стороне.</span><span class="sxs-lookup"><span data-stu-id="95fd7-340">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="95fd7-341">Этот дескриптор зависит от конкретной реализации и в данной реализации не используется.</span><span class="sxs-lookup"><span data-stu-id="95fd7-341">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="95fd7-342">Приложение должно передать значение NULL для этого дескриптора.</span><span class="sxs-lookup"><span data-stu-id="95fd7-342">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="95fd7-343">**crypto_metadata**: указатель на допустимое пространство памяти для блока управления DRBG.</span><span class="sxs-lookup"><span data-stu-id="95fd7-343">**crypto_metadata** Pointer to a valid memory space for the DRBG control block.</span></span> <span data-ttu-id="95fd7-344">Начальный адрес пространства памяти должен быть выделен с буфером в 4 байта.</span><span class="sxs-lookup"><span data-stu-id="95fd7-344">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="95fd7-345">**crypto_metadata_size**: размер области crypto_metadata в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-345">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="95fd7-346">Для DRBG размер метаданных должен быть равен *sizeof(NX_CRYPTO_DRBG)* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-346">For DRBG, the metadata size must be *sizeof(NX_CRYPTO_DRBG)*</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-347">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-347">Return Values</span></span>

- <span data-ttu-id="95fd7-348">**NX_CRYPTO_SUCCESS** (0X00): блок управления DRBG успешно инициализирован с заданными ключом и размером ключа.</span><span class="sxs-lookup"><span data-stu-id="95fd7-348">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the DRBG control block with the key and key size.</span></span>
- <span data-ttu-id="95fd7-349">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-349">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="95fd7-350">**NX_PTR_ERROR (0x07)** : недопустимый указатель на ключ, недопустимое значение crypto_metadata или crypto_metadata_size либо при выделении области crypto_metadata не был задан буфер в 4 байта.</span><span class="sxs-lookup"><span data-stu-id="95fd7-350">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_drbg_operation"></a><span data-ttu-id="95fd7-351">_nx_crypto_method_drbg_operation</span><span class="sxs-lookup"><span data-stu-id="95fd7-351">_nx_crypto_method_drbg_operation</span></span>

<span data-ttu-id="95fd7-352">Выполнение операции DRBG.</span><span class="sxs-lookup"><span data-stu-id="95fd7-352">Perform DRBG operation</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-353">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-353">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="95fd7-354">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-354">Description</span></span>

<span data-ttu-id="95fd7-355">Эта функция выполняет операцию DRBG.</span><span class="sxs-lookup"><span data-stu-id="95fd7-355">This function performs DRBG operation.</span></span> <span data-ttu-id="95fd7-356">Блок управления DRBG должен быть инициализирован с помощью службы _ *nx_crypto_method_drbg_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-356">The DRBG control block must have been initialized with _ *nx_crypto_method_drbg_init()*.</span></span> <span data-ttu-id="95fd7-357">Выполняемый алгоритм DRBG основан на алгоритме, указанном в блоке управления *method*.</span><span class="sxs-lookup"><span data-stu-id="95fd7-357">The DRBG algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span> <span data-ttu-id="95fd7-358">По умолчанию для DRBG используется алгоритм AES-128.</span><span class="sxs-lookup"><span data-stu-id="95fd7-358">By default AES-128 is used for DRBG.</span></span>

<span data-ttu-id="95fd7-359">Если задана операция NX_CRYPTO_DRBG_OPTIONS_SET, то input указывает на структуру NX_CRYPTO_DRBG_OPTIONS.</span><span class="sxs-lookup"><span data-stu-id="95fd7-359">When the operation is NX_CRYPTO_DRBG_OPTIONS_SET, the input points to NX_CRYPTO_DRBG_OPTIONS structure.</span></span> <span data-ttu-id="95fd7-360">Если задана операция NX_CRYPTO_DRBG_INSTANTIATE, то key указывает на nonce, а input указывает на строку персонализации.</span><span class="sxs-lookup"><span data-stu-id="95fd7-360">When the operation is NX_CRYPTO_DRBG_INSTANTIATE, the key points to nonce, input points to personalization string.</span></span> <span data-ttu-id="95fd7-361">Если задана операция NX_CRYPTO_DRBG_RESEED или NX_CRYPTO_DRBG_GENERATE, то input указывает на дополнительные входные данные.</span><span class="sxs-lookup"><span data-stu-id="95fd7-361">When the operation is NX_CRYPTO_DRBG_RESEED or NX_CRYPTO_DRBG_GENERATE, the input points to additional input.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-362">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-362">Parameters</span></span>

- <span data-ttu-id="95fd7-363">**op**: тип выполняемой операции.</span><span class="sxs-lookup"><span data-stu-id="95fd7-363">**op** Type of operation to perform.</span></span> <span data-ttu-id="95fd7-364">Допустимые операции:</span><span class="sxs-lookup"><span data-stu-id="95fd7-364">Valid operation is:</span></span>
  - <span data-ttu-id="95fd7-365">*NX_CRYPTO_DRBG_OPTIONS_SET*</span><span class="sxs-lookup"><span data-stu-id="95fd7-365">*NX_CRYPTO_DRBG_OPTIONS_SET*</span></span>
  - <span data-ttu-id="95fd7-366">*NX_CRYPTO_DRBG_INSTANTIATE*</span><span class="sxs-lookup"><span data-stu-id="95fd7-366">*NX_CRYPTO_DRBG_INSTANTIATE*</span></span>
  - <span data-ttu-id="95fd7-367">*NX_CRYPTO_DRBG_RESEED NX_CRYPTO_DRBG_GENERATE*</span><span class="sxs-lookup"><span data-stu-id="95fd7-367">*NX_CRYPTO_DRBG_RESEED NX_CRYPTO_DRBG_GENERATE*</span></span>
- <span data-ttu-id="95fd7-368">**handle**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-368">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-369">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-369">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="95fd7-370">**method**: указатель на допустимый метод шифрования DRBG.</span><span class="sxs-lookup"><span data-stu-id="95fd7-370">**method** Pointer to the valid DRBG crypto method.</span></span> <span data-ttu-id="95fd7-371">Используемый здесь метод шифрования должен совпадать с методом, указанным в _ *nx_crypto_method_drbg_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-371">The crypto method used here must be the same used in the _ *nx_crypto_method_drbg_init().*</span></span>
- <span data-ttu-id="95fd7-372">**key**: указатель на ключ nonce для операции создания экземпляра.</span><span class="sxs-lookup"><span data-stu-id="95fd7-372">**key** Pointer to the the nonce for the instantiate operation.</span></span> <span data-ttu-id="95fd7-373">Это поле не используется для других операций.</span><span class="sxs-lookup"><span data-stu-id="95fd7-373">This field is not used for other operations.</span></span>
- <span data-ttu-id="95fd7-374">**key_size_in_bits**: размер ключа nonce в битах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-374">**key_size_in_bits** Size of the nonce, in bits.</span></span> <span data-ttu-id="95fd7-375">Это поле не используется для других операций.</span><span class="sxs-lookup"><span data-stu-id="95fd7-375">This field is not used for other operations.</span></span>
- <span data-ttu-id="95fd7-376">**input**: когда op имеет значение NX_CRYPTO_DRBG_OPTIONS_SET, это поле указывает на параметры DRBG.</span><span class="sxs-lookup"><span data-stu-id="95fd7-376">**input** When op is NX_CRYPTO_DRBG_OPTIONS_SET, this field points to DRBG options.</span></span> <span data-ttu-id="95fd7-377">Когда op имеет значение NX_CRYPTO_DRBG_INSTANTIATE, это поле указывает на строку персонализации.</span><span class="sxs-lookup"><span data-stu-id="95fd7-377">When op is NX_CRYPTO_DRBG_INSTANTIATE, this field points to personalization string.</span></span> <span data-ttu-id="95fd7-378">Если op имеет значение NX_CRYPTO_DRBG_RESEED или NX_CRYPTO_DRBG_GENERATE, это поле указывает на дополнительные входные данные.</span><span class="sxs-lookup"><span data-stu-id="95fd7-378">When op is NX_CRYPTO_DRBG_RESEED or NX_CRYPTO_DRBG_GENERATE, this field points to additional input data.</span></span>
- <span data-ttu-id="95fd7-379">**input_length_in_byte**: размер входных данных в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-379">**input_length_in_byte** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="95fd7-380">**iv_ptr**: это поле не используется для DRBG.</span><span class="sxs-lookup"><span data-stu-id="95fd7-380">**iv_ptr** This field is not used for DRBG.</span></span>
- <span data-ttu-id="95fd7-381">**output**: когда op имеет значение NX_CRYPTO_DRBG_GENERATE, это поле указывает на область памяти для созданного экземпляра DRBG.</span><span class="sxs-lookup"><span data-stu-id="95fd7-381">**output** When op is NX_CRYPTO_DRBG_GENERATE, this field points to the memory area for the generated DRBG.</span></span> <span data-ttu-id="95fd7-382">В противном случае это поле не используется.</span><span class="sxs-lookup"><span data-stu-id="95fd7-382">Otherwise, this field is not used.</span></span>
- <span data-ttu-id="95fd7-383">**output_length_in_byte**: указывает размер буфера вывода в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-383">**output_length_in_byte** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="95fd7-384">**crypto_metadata**: указатель на блок управления DRBG, используемый в *_nx_crypto_method_drbg_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-384">**crypto_metadata** Pointer to the DRBG control block used in *_nx_crypto_method_drbg_init()*.</span></span>
- <span data-ttu-id="95fd7-385">**crypto_metadata_size**: размер области crypto_metadata в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-385">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="95fd7-386">Для DRBG размер метаданных должен быть равен *sizeof(NX_CRYPTO_DRBG)* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-386">For DRBG, the metadata size must *sizeof(NX_CRYPTO_DRBG)*</span></span>
- <span data-ttu-id="95fd7-387">**packet_ptr**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-387">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-388">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-388">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="95fd7-389">**nx_crypto_hw_process_callback**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-389">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-390">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-390">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-391">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-391">Return Values</span></span>

- <span data-ttu-id="95fd7-392">**NX_CRYPTO_SUCCESS** (0X00): операция DRBG успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="95fd7-392">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the DRBG operation.</span></span>
- <span data-ttu-id="95fd7-393">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-393">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="95fd7-394">**NX_PTR_ERROR** (0x07): недопустимый указатель ввода или длина.</span><span class="sxs-lookup"><span data-stu-id="95fd7-394">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="95fd7-395">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004): указан недопустимый алгоритм DRBG.</span><span class="sxs-lookup"><span data-stu-id="95fd7-395">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid DRBG algorithm being specified.</span></span>
- <span data-ttu-id="95fd7-396">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005): недопустимый размер выходного буфера.</span><span class="sxs-lookup"><span data-stu-id="95fd7-396">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_drbg_cleanup"></a><span data-ttu-id="95fd7-397">_nx_crypto_method_drbg_cleanup</span><span class="sxs-lookup"><span data-stu-id="95fd7-397">_nx_crypto_method_drbg_cleanup</span></span>

<span data-ttu-id="95fd7-398">Очистка блока управления DRBG.</span><span class="sxs-lookup"><span data-stu-id="95fd7-398">Clean up the DRBG control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-399">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-399">Prototype</span></span>

```c
UINT _nx_crypto_method_drbg_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="95fd7-400">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-400">Description</span></span>

<span data-ttu-id="95fd7-401">Приложение вызывает эту функцию для очистки блока управления DRBG после того, как определит, что этот сеанс DRBG больше не требуется.</span><span class="sxs-lookup"><span data-stu-id="95fd7-401">Application calls this function to clean up the DRBG control block after it determines this DRBG session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-402">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-402">Parameters</span></span>

- <span data-ttu-id="95fd7-403">**crypto_metadata**: указатель на блок управления DRBG, используемый в *_nx_crypto_method_drbg_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-403">**crypto_metadata** Pointer to the DRBG control block used in *_nx_crypto_method_drbg_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-404">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-404">Return Values</span></span>

- <span data-ttu-id="95fd7-405">**NX_CRYPTO_SUCCESS** (0X00): сеанс DRBG успешно очищен.</span><span class="sxs-lookup"><span data-stu-id="95fd7-405">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the DRBG session.</span></span>
- <span data-ttu-id="95fd7-406">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-406">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_ecdh_init"></a><span data-ttu-id="95fd7-407">_nx_crypto_method_ecdh_init</span><span class="sxs-lookup"><span data-stu-id="95fd7-407">_nx_crypto_method_ecdh_init</span></span>

<span data-ttu-id="95fd7-408">Инициализация блока управления шифрованием ECDH.</span><span class="sxs-lookup"><span data-stu-id="95fd7-408">Initializes the ECDH crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-409">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-409">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdh_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="95fd7-410">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-410">Description</span></span>

<span data-ttu-id="95fd7-411">Эта функция инициализирует блок управления ECDH с заданной строкой ключа.</span><span class="sxs-lookup"><span data-stu-id="95fd7-411">This function initializes the ECDH control block with the given key string.</span></span> <span data-ttu-id="95fd7-412">После инициализации блока управления ECDH последующая операция ECDH должна использовать этот же блок управления.</span><span class="sxs-lookup"><span data-stu-id="95fd7-412">Once the ECDH control block is initialized, subsequent ECDH operation shall be using the same control block.</span></span>

<span data-ttu-id="95fd7-413">Приложение может создать несколько блоков управления ECDH, представляющих отдельные сеансы.</span><span class="sxs-lookup"><span data-stu-id="95fd7-413">Application may create multiple ECDH control blocks, each represents a session.</span></span> <span data-ttu-id="95fd7-414">Инициализация блока управления ECDH запускает новый сеанс вычисления хэша.</span><span class="sxs-lookup"><span data-stu-id="95fd7-414">Initializing the ECDH control block starts a new hash computation session.</span></span> <span data-ttu-id="95fd7-415">Повторная инициализация блока управления ECDH прекращает текущий сеанс и запускает новый.</span><span class="sxs-lookup"><span data-stu-id="95fd7-415">Re-initializing the ECDH control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-416">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-416">Parameters</span></span>

- <span data-ttu-id="95fd7-417">**method**: указатель на допустимый блок управления методом шифрования ECDH.</span><span class="sxs-lookup"><span data-stu-id="95fd7-417">**method** Pointer to a valid ECDH crypto method control block.</span></span> <span data-ttu-id="95fd7-418">Доступны следующие стандартные методы шифрования:</span><span class="sxs-lookup"><span data-stu-id="95fd7-418">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="95fd7-419">*crypto_method_ecdh*</span><span class="sxs-lookup"><span data-stu-id="95fd7-419">*crypto_method_ecdh*</span></span>
- <span data-ttu-id="95fd7-420">**key**: это поле не используется для ECDH.</span><span class="sxs-lookup"><span data-stu-id="95fd7-420">**key** This field is not used for ECDH.</span></span>
- <span data-ttu-id="95fd7-421">**key_size_in_bits**: это поле не используется для ECDH.</span><span class="sxs-lookup"><span data-stu-id="95fd7-421">**key_size_in_bits** This field is not used for ECDH.</span></span>
- <span data-ttu-id="95fd7-422">**handle**: эта служба возвращает дескриптор вызывающей стороне.</span><span class="sxs-lookup"><span data-stu-id="95fd7-422">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="95fd7-423">Этот дескриптор зависит от конкретной реализации и в данной реализации не используется.</span><span class="sxs-lookup"><span data-stu-id="95fd7-423">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="95fd7-424">Приложение должно передать значение NULL для этого дескриптора.</span><span class="sxs-lookup"><span data-stu-id="95fd7-424">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="95fd7-425">**crypto_metadata**: указатель на допустимое пространство памяти для блока управления ECDH.</span><span class="sxs-lookup"><span data-stu-id="95fd7-425">**crypto_metadata** Pointer to a valid memory space for the ECDH control block.</span></span> <span data-ttu-id="95fd7-426">Начальный адрес пространства памяти должен быть выделен с буфером в 4 байта.</span><span class="sxs-lookup"><span data-stu-id="95fd7-426">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="95fd7-427">**crypto_metadata_size**: размер области crypto_metadata в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-427">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="95fd7-428">Для ECDH размер метаданных должен быть равен *sizeof(NX_CRYPTO_ECDH)* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-428">For ECDH, the metadata size must be *sizeof(NX_CRYPTO_ECDH)*</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-429">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-429">Return Values</span></span>

- <span data-ttu-id="95fd7-430">**NX_CRYPTO_SUCCESS** (0X00): блок управления ECDH успешно инициализирован с заданными ключом и размером ключа.</span><span class="sxs-lookup"><span data-stu-id="95fd7-430">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the ECDH control block with the key and key size.</span></span>
- <span data-ttu-id="95fd7-431">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-431">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="95fd7-432">**NX_PTR_ERROR (0x07)** : недопустимый указатель на ключ, недопустимое значение crypto_metadata или crypto_metadata_size либо при выделении области crypto_metadata не был задан буфер в 4 байта.</span><span class="sxs-lookup"><span data-stu-id="95fd7-432">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_ecdh_operation"></a><span data-ttu-id="95fd7-433">_nx_crypto_method_ecdh_operation</span><span class="sxs-lookup"><span data-stu-id="95fd7-433">_nx_crypto_method_ecdh_operation</span></span>

<span data-ttu-id="95fd7-434">Выполнение операции ECDH.</span><span class="sxs-lookup"><span data-stu-id="95fd7-434">Perform ECDH operation</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-435">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-435">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="95fd7-436">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-436">Description</span></span>

<span data-ttu-id="95fd7-437">Эта функция выполняет операцию ECDH.</span><span class="sxs-lookup"><span data-stu-id="95fd7-437">This function performs ECDH operation.</span></span> <span data-ttu-id="95fd7-438">Блок управления ECDH должен быть инициализирован с помощью службы _ *nx_crypto_method_ecdh_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-438">The ECDH control block must have been initialized with _ *nx_crypto_method_ecdh_init()*.</span></span> <span data-ttu-id="95fd7-439">Выполняемый алгоритм ECDH основан на алгоритме, указанном в блоке управления *method*.</span><span class="sxs-lookup"><span data-stu-id="95fd7-439">The ECDH algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="95fd7-440">Если задана операция NX_CRYPTO_EC_CURVE_SET, то input указывает на метод шифрования на основе эллиптических кривых.</span><span class="sxs-lookup"><span data-stu-id="95fd7-440">When the operation is NX_CRYPTO_EC_CURVE_SET, the input points to Elliptic Curve crypto method.</span></span> <span data-ttu-id="95fd7-441">Если задана операция NX_CRYPTO_EC_KEY_PAIR_GENERATE, output указывает на структуру NX_CRYPTO_EXTENDED_OUTPUT, а пара ключей копируется в nx_crypto_extended_output_data.</span><span class="sxs-lookup"><span data-stu-id="95fd7-441">When the operation is NX_CRYPTO_EC_KEY_PAIR_GENERATE, the output points to NX_CRYPTO_EXTENDED_OUTPUT structure and the key pair is copied to nx_crypto_extended_output_data.</span></span> <span data-ttu-id="95fd7-442">Если задана операция NX_CRYPTO_DH_SETUP, то открытый ключ возвращается в nx_crypto_extended_output_data.</span><span class="sxs-lookup"><span data-stu-id="95fd7-442">When the operation is NX_CRYPTO_DH_SETUP, the public key is returned to nx_crypto_extended_output_data.</span></span> <span data-ttu-id="95fd7-443">Если задана операция NX_CRYPTO_DH_KEY_PAIR_IMPORT, то input указывает на открытый ключ, а key указывает на закрытый ключ.</span><span class="sxs-lookup"><span data-stu-id="95fd7-443">When the operation is NX_CRYPTO_DH_KEY_PAIR_IMPORT, the input points to public key and key points to private key.</span></span> <span data-ttu-id="95fd7-444">Если задана операция NX_CRYPTO_DH_PRIVATE_KEY_EXPORT, то закрытый ключ возвращается в nx_crypto_extended_output_data.</span><span class="sxs-lookup"><span data-stu-id="95fd7-444">When the operation is NX_CRYPTO_DH_PRIVATE_KEY_EXPORT, the private key is copied to nx_crypto_extended_output_data.</span></span> <span data-ttu-id="95fd7-445">Если задана операция NX_CRYPTO_DH_CALCULATE, то input указывает на удаленный открытый ключ, а общий секрет копируются в nx_crypto_extended_output_data.</span><span class="sxs-lookup"><span data-stu-id="95fd7-445">When the operation is NX_CRYPTO_DH_CALCULATE, the input points to remote public key and the shared secret is copied to nx_crypto_extended_output_data.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-446">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-446">Parameters</span></span>

- <span data-ttu-id="95fd7-447">**op**: тип выполняемой операции.</span><span class="sxs-lookup"><span data-stu-id="95fd7-447">**op** Type of operation to perform.</span></span> <span data-ttu-id="95fd7-448">Допустимые операции:</span><span class="sxs-lookup"><span data-stu-id="95fd7-448">Valid operation is:</span></span>
  - <span data-ttu-id="95fd7-449">*NX_CRYPTO_EC_CURVE_SET*</span><span class="sxs-lookup"><span data-stu-id="95fd7-449">*NX_CRYPTO_EC_CURVE_SET*</span></span>
  - <span data-ttu-id="95fd7-450">*NX_CRYPTO_DH_SETUP*</span><span class="sxs-lookup"><span data-stu-id="95fd7-450">*NX_CRYPTO_DH_SETUP*</span></span>
  - <span data-ttu-id="95fd7-451">*NX_CRYPTO_DH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="95fd7-451">*NX_CRYPTO_DH_CALCULATE*</span></span>
  - <span data-ttu-id="95fd7-452">*NX_CRYPTO_DH_KEY_PAIR_IMPOPRT*</span><span class="sxs-lookup"><span data-stu-id="95fd7-452">*NX_CRYPTO_DH_KEY_PAIR_IMPOPRT*</span></span>
  - <span data-ttu-id="95fd7-453">*NX_CRYPTO_DH_KEY_PAIR_GENERATE*</span><span class="sxs-lookup"><span data-stu-id="95fd7-453">*NX_CRYPTO_DH_KEY_PAIR_GENERATE*</span></span>
  - <span data-ttu-id="95fd7-454">*NX_CRYPTO_DH_PRIVATE_KEY_EXPORT*</span><span class="sxs-lookup"><span data-stu-id="95fd7-454">*NX_CRYPTO_DH_PRIVATE_KEY_EXPORT*</span></span>
- <span data-ttu-id="95fd7-455">**handle**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-455">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-456">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-456">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="95fd7-457">**method**: указатель на допустимый метод шифрования ECDH.</span><span class="sxs-lookup"><span data-stu-id="95fd7-457">**method** Pointer to the valid ECDH crypto method.</span></span> <span data-ttu-id="95fd7-458">Используемый здесь метод шифрования должен совпадать с методом, указанным в _ *nx_crypto_method_ecdh_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-458">The crypto method used here must be the same used in the _ *nx_crypto_method_ecdh_init().*</span></span>
- <span data-ttu-id="95fd7-459">**key**: когда op имеет значение NX_CRYPTO_DH_IMPORT_KEY_PAIR, это поле указывает на закрытый ключ.</span><span class="sxs-lookup"><span data-stu-id="95fd7-459">**key** When op is NX_CRYPTO_DH_IMPORT_KEY_PAIR, this field points to private key.</span></span> <span data-ttu-id="95fd7-460">В противном случае это поле не используется для ECDH.</span><span class="sxs-lookup"><span data-stu-id="95fd7-460">Otherwise, this field is not used for ECDH.</span></span>
- <span data-ttu-id="95fd7-461">**key_size_in_bits**: размер ключа в битах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-461">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="95fd7-462">**input**: когда op имеет значение NX_CRYPTO_EC_CURVE_SET, это поле указывает на метод шифрования на основе эллиптических кривых.</span><span class="sxs-lookup"><span data-stu-id="95fd7-462">**input** When op is NX_CRYPTO_EC_CURVE_SET, this field points to Elliptic Curve crypto method.</span></span> <span data-ttu-id="95fd7-463">Когда op имеет значение NX_CRYPTO_DH_SETUP, это поле не используется.</span><span class="sxs-lookup"><span data-stu-id="95fd7-463">When op is NX_CRYPTO_DH_SETUP, this field is not used.</span></span> <span data-ttu-id="95fd7-464">Когда op имеет значение NX_CRYPTO_DH_CALCULATE, это поле указывает на буфер, содержащий входные текстовые данные.</span><span class="sxs-lookup"><span data-stu-id="95fd7-464">When op is NX_CRYPTO_DH_CALCULATE, this field points to a buffer containing input text data.</span></span> <span data-ttu-id="95fd7-465">Когда op имеет значение NX_CRYPTO_DH_IMPORT_KEY_PAIR, это поле указывает на открытый ключ.</span><span class="sxs-lookup"><span data-stu-id="95fd7-465">When op is NX_CRYPTO_DH_IMPORT_KEY_PAIR, this field points to public key.</span></span>
- <span data-ttu-id="95fd7-466">**input_length_in_byte**: размер входных данных в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-466">**input_length_in_byte** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="95fd7-467">**iv_ptr**: это поле не используется для ECDH.</span><span class="sxs-lookup"><span data-stu-id="95fd7-467">**iv_ptr** This field is not used for ECDH.</span></span>
- <span data-ttu-id="95fd7-468">**output**: если op имеет значение NX_CRYPTO_EC_CURVE_SET или NX_CRYPTO_DH_IMPORT_KEY_PAIR, это поле не используется.</span><span class="sxs-lookup"><span data-stu-id="95fd7-468">**output** When op is NX_CRYPTO_EC_CURVE_SET or NX_CRYPTO_DH_IMPORT_KEY_PAIR, this field is not used.</span></span> <span data-ttu-id="95fd7-469">Когда op имеет значение NX_CRYPTO_DH_SETUP, это поле указывает на область памяти для созданного ECDH открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="95fd7-469">When op is NX_CRYPTO_DH_SETUP, this field points to the memory area for the generated ECDH public key.</span></span> <span data-ttu-id="95fd7-470">Когда op имеет значение NX_CRYPTO_DH_CALCULATE, это поле указывает на область памяти для созданного ECDH общего секрета.</span><span class="sxs-lookup"><span data-stu-id="95fd7-470">When op is NX_CRYPTO_DH_CALCULATE, this field points to the memory area for the generated ECDH shared secret.</span></span>
- <span data-ttu-id="95fd7-471">**output_length_in_byte**: указывает размер буфера вывода в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-471">**output_length_in_byte** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="95fd7-472">**crypto_metadata**: указатель на блок управления ECDH, используемый в *_nx_crypto_method_ecdh_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-472">**crypto_metadata** Pointer to the ECDH control block used in *_nx_crypto_method_ecdh_init()*.</span></span>
- <span data-ttu-id="95fd7-473">**crypto_metadata_size**: размер области crypto_metadata в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-473">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="95fd7-474">Для ECDH размер метаданных должен быть равен *sizeof(NX_CRYPTO_ECDH)* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-474">For ECDH, the metadata size must *sizeof(NX_CRYPTO_ECDH)*</span></span>
- <span data-ttu-id="95fd7-475">**packet_ptr**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-475">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-476">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-476">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="95fd7-477">**nx_crypto_hw_process_callback**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-477">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-478">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-478">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-479">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-479">Return Values</span></span>

- <span data-ttu-id="95fd7-480">**NX_CRYPTO_SUCCESS** (0X00): операция ECDH успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="95fd7-480">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the ECDH operation.</span></span>
- <span data-ttu-id="95fd7-481">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-481">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="95fd7-482">**NX_PTR_ERROR** (0x07): недопустимый указатель ввода или длина.</span><span class="sxs-lookup"><span data-stu-id="95fd7-482">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="95fd7-483">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004): указан недопустимый алгоритм ECDH.</span><span class="sxs-lookup"><span data-stu-id="95fd7-483">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid ECDH algorithm being specified.</span></span>
- <span data-ttu-id="95fd7-484">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005): недопустимый размер выходного буфера.</span><span class="sxs-lookup"><span data-stu-id="95fd7-484">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_ecdh_cleanup"></a><span data-ttu-id="95fd7-485">_nx_crypto_method_ecdh_cleanup</span><span class="sxs-lookup"><span data-stu-id="95fd7-485">_nx_crypto_method_ecdh_cleanup</span></span>

<span data-ttu-id="95fd7-486">Очистка блока управления ECDH.</span><span class="sxs-lookup"><span data-stu-id="95fd7-486">Clean up the ECDH control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-487">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-487">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdh_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="95fd7-488">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-488">Description</span></span>

<span data-ttu-id="95fd7-489">Приложение вызывает эту функцию для очистки блока управления ECDH после того, как определит, что этот сеанс ECDH больше не требуется.</span><span class="sxs-lookup"><span data-stu-id="95fd7-489">Application calls this function to clean up the ECDH control block after it determines this ECDH session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-490">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-490">Parameters</span></span>

- <span data-ttu-id="95fd7-491">**crypto_metadata**: указатель на блок управления ECDH, используемый в *_nx_crypto_method_ecdh_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-491">**crypto_metadata** Pointer to the ECDH control block used in *_nx_crypto_method_ecdh_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-492">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-492">Return Values</span></span>

- <span data-ttu-id="95fd7-493">**NX_CRYPTO_SUCCESS** (0X00): сеанс ECDH успешно очищен.</span><span class="sxs-lookup"><span data-stu-id="95fd7-493">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the ECDH session.</span></span>
- <span data-ttu-id="95fd7-494">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-494">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_ecdsa_init"></a><span data-ttu-id="95fd7-495">_nx_crypto_method_ecdsa_init</span><span class="sxs-lookup"><span data-stu-id="95fd7-495">_nx_crypto_method_ecdsa_init</span></span>

<span data-ttu-id="95fd7-496">Инициализация блока управления шифрованием ECDSA.</span><span class="sxs-lookup"><span data-stu-id="95fd7-496">Initializes the ECDSA crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-497">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-497">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdsa_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="95fd7-498">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-498">Description</span></span>

<span data-ttu-id="95fd7-499">Эта функция инициализирует блок управления ECDSA с заданной строкой ключа.</span><span class="sxs-lookup"><span data-stu-id="95fd7-499">This function initializes the ECDSA control block with the given key string.</span></span> <span data-ttu-id="95fd7-500">После инициализации блока управления ECDSA последующая операция ECDSA должна использовать этот же блок управления.</span><span class="sxs-lookup"><span data-stu-id="95fd7-500">Once the ECDSA control block is initialized, subsequent ECDSA operation shall be using the same control block.</span></span>

<span data-ttu-id="95fd7-501">Приложение может создать несколько блоков управления ECDSA, представляющих отдельные сеансы.</span><span class="sxs-lookup"><span data-stu-id="95fd7-501">Application may create multiple ECDSA control blocks, each represents a session.</span></span> <span data-ttu-id="95fd7-502">Инициализация блока управления ECDSA запускает новый сеанс вычисления хэша.</span><span class="sxs-lookup"><span data-stu-id="95fd7-502">Initializing the ECDSA control block starts a new hash computation session.</span></span> <span data-ttu-id="95fd7-503">Повторная инициализация блока управления ECDSA прекращает текущий сеанс и запускает новый.</span><span class="sxs-lookup"><span data-stu-id="95fd7-503">Re-initializing the ECDSA control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-504">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-504">Parameters</span></span>

- <span data-ttu-id="95fd7-505">**method**: указатель на допустимый блок управления методом шифрования ECDSA.</span><span class="sxs-lookup"><span data-stu-id="95fd7-505">**method** Pointer to a valid ECDSA crypto method control block.</span></span> <span data-ttu-id="95fd7-506">Доступны следующие стандартные методы шифрования:</span><span class="sxs-lookup"><span data-stu-id="95fd7-506">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="95fd7-507">*crypto_method_ecdsa*</span><span class="sxs-lookup"><span data-stu-id="95fd7-507">*crypto_method_ecdsa*</span></span>
- <span data-ttu-id="95fd7-508">**key**: это поле не используется для ECDSA.</span><span class="sxs-lookup"><span data-stu-id="95fd7-508">**key** This field is not used for ECDSA.</span></span>
- <span data-ttu-id="95fd7-509">**key_size_in_bits**: это поле не используется для ECDSA.</span><span class="sxs-lookup"><span data-stu-id="95fd7-509">**key_size_in_bits** This field is not used for ECDSA.</span></span>
- <span data-ttu-id="95fd7-510">**handle**: эта служба возвращает дескриптор вызывающей стороне.</span><span class="sxs-lookup"><span data-stu-id="95fd7-510">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="95fd7-511">Этот дескриптор зависит от конкретной реализации и в данной реализации не используется.</span><span class="sxs-lookup"><span data-stu-id="95fd7-511">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="95fd7-512">Приложение должно передать значение NULL для этого дескриптора.</span><span class="sxs-lookup"><span data-stu-id="95fd7-512">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="95fd7-513">**crypto_metadata**: указатель на допустимое пространство памяти для блока управления ECDSA.</span><span class="sxs-lookup"><span data-stu-id="95fd7-513">**crypto_metadata** Pointer to a valid memory space for the ECDSA control block.</span></span> <span data-ttu-id="95fd7-514">Начальный адрес пространства памяти должен быть выделен с буфером в 4 байта.</span><span class="sxs-lookup"><span data-stu-id="95fd7-514">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="95fd7-515">**crypto_metadata_size**: размер области crypto_metadata в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-515">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="95fd7-516">Для ECDSA размер метаданных должен быть равен *sizeof(NX_CRYPTO_ECDSA)* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-516">For ECDSA, the metadata size must be *sizeof(NX_CRYPTO_ECDSA)*</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-517">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-517">Return Values</span></span>

- <span data-ttu-id="95fd7-518">**NX_CRYPTO_SUCCESS** (0X00): блок управления ECDSA успешно инициализирован с заданными ключом и размером ключа.</span><span class="sxs-lookup"><span data-stu-id="95fd7-518">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the ECDSA control block with the key and key size.</span></span>
- <span data-ttu-id="95fd7-519">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-519">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="95fd7-520">**NX_PTR_ERROR (0x07)** : недопустимый указатель на ключ, недопустимое значение crypto_metadata или crypto_metadata_size либо при выделении области crypto_metadata не был задан буфер в 4 байта.</span><span class="sxs-lookup"><span data-stu-id="95fd7-520">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_ecdsa_operation"></a><span data-ttu-id="95fd7-521">_nx_crypto_method_ecdsa_operation</span><span class="sxs-lookup"><span data-stu-id="95fd7-521">_nx_crypto_method_ecdsa_operation</span></span>

<span data-ttu-id="95fd7-522">Выполнение операции ECDSA.</span><span class="sxs-lookup"><span data-stu-id="95fd7-522">Perform ECDSA operation</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-523">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-523">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="95fd7-524">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-524">Description</span></span>

<span data-ttu-id="95fd7-525">Эта функция выполняет операцию ECDSA.</span><span class="sxs-lookup"><span data-stu-id="95fd7-525">This function performs ECDSA operation.</span></span> <span data-ttu-id="95fd7-526">Блок управления ECDSA должен быть инициализирован с помощью службы _ *nx_crypto_method_ecdsa_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-526">The ECDSA control block must have been initialized with _ *nx_crypto_method_ecdsa_init()*.</span></span> <span data-ttu-id="95fd7-527">Выполняемый алгоритм ECDSA основан на алгоритме, указанном в блоке управления *method*.</span><span class="sxs-lookup"><span data-stu-id="95fd7-527">The ECDSA algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="95fd7-528">Если задана операция NX_CRYPTO_EC_CURVE_SET, то input указывает на метод шифрования на основе эллиптических кривых.</span><span class="sxs-lookup"><span data-stu-id="95fd7-528">When the operation is NX_CRYPTO_EC_CURVE_SET, the input points to Elliptic Curve crypto method.</span></span> <span data-ttu-id="95fd7-529">Если задана операция NX_CRYPTO_EC_KEY_PAIR_GENERATE, output указывает на структуру NX_CRYPTO_EXTENDED_OUTPUT, а пара ключей копируется в nx_crypto_extended_output_data.</span><span class="sxs-lookup"><span data-stu-id="95fd7-529">When the operation is NX_CRYPTO_EC_KEY_PAIR_GENERATE, the output points to NX_CRYPTO_EXTENDED_OUTPUT structure and the key pair is copied to nx_crypto_extended_output_data.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-530">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-530">Parameters</span></span>

- <span data-ttu-id="95fd7-531">**op**: тип выполняемой операции.</span><span class="sxs-lookup"><span data-stu-id="95fd7-531">**op** Type of operation to perform.</span></span> <span data-ttu-id="95fd7-532">Допустимые операции:</span><span class="sxs-lookup"><span data-stu-id="95fd7-532">Valid operation is:</span></span>
  - <span data-ttu-id="95fd7-533">*NX_CRYPTO_EC_CURVE_SET*</span><span class="sxs-lookup"><span data-stu-id="95fd7-533">*NX_CRYPTO_EC_CURVE_SET*</span></span>
  - <span data-ttu-id="95fd7-534">*NX_CRYPTO_AUTHENTICATE*</span><span class="sxs-lookup"><span data-stu-id="95fd7-534">*NX_CRYPTO_AUTHENTICATE*</span></span>
  - <span data-ttu-id="95fd7-535">*NX_CRYPTO_VERIFY*</span><span class="sxs-lookup"><span data-stu-id="95fd7-535">*NX_CRYPTO_VERIFY*</span></span>
- <span data-ttu-id="95fd7-536">**handle**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-536">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-537">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-537">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="95fd7-538">**method**: указатель на допустимый метод шифрования ECDSA.</span><span class="sxs-lookup"><span data-stu-id="95fd7-538">**method** Pointer to the valid ECDSA crypto method.</span></span> <span data-ttu-id="95fd7-539">Используемый здесь метод шифрования должен совпадать с методом, указанным в _ *nx_crypto_method_ecdsa_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-539">The crypto method used here must be the same used in the _ *nx_crypto_method_ecdsa_init().*</span></span>
- <span data-ttu-id="95fd7-540">**key**: указывает на ключ, когда op имеет значение NX_CRYPTO_VERIFY.</span><span class="sxs-lookup"><span data-stu-id="95fd7-540">**key** Points to the key when op is NX_CRYPTO_VERIFY.</span></span> <span data-ttu-id="95fd7-541">Ограничения для буфера ключей отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="95fd7-541">There are not restrictions on key buffer.</span></span> <span data-ttu-id="95fd7-542">Это поле не используется при других значениях параметра op.</span><span class="sxs-lookup"><span data-stu-id="95fd7-542">This field is not used for other values of op.</span></span>
- <span data-ttu-id="95fd7-543">**key_size_in_bits**: размер ключа в битах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-543">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="95fd7-544">**input**: когда op имеет значение NX_CRYPTO_EC_CURVE_SET, это поле указывает на метод шифрования на основе эллиптических кривых.</span><span class="sxs-lookup"><span data-stu-id="95fd7-544">**input** When op is NX_CRYPTO_EC_CURVE_SET, this field points to Elliptic Curve crypto method.</span></span> <span data-ttu-id="95fd7-545">В противном случае это поле указывает на буфер, содержащий входные текстовые данные.</span><span class="sxs-lookup"><span data-stu-id="95fd7-545">Otherwise, this field points to a buffer containing input text data.</span></span>
- <span data-ttu-id="95fd7-546">**input_length_in_byte**: размер входных данных в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-546">**input_length_in_byte** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="95fd7-547">**iv_ptr**: это поле не используется для ECDSA.</span><span class="sxs-lookup"><span data-stu-id="95fd7-547">**iv_ptr** This field is not used for ECDSA.</span></span>
- <span data-ttu-id="95fd7-548">**output**: если op имеет значение NX_CRYPTO_EC_CURVE_SET, это поле не используется.</span><span class="sxs-lookup"><span data-stu-id="95fd7-548">**output** When op is NX_CRYPTO_EC_CURVE_SET, this field is not used.</span></span> <span data-ttu-id="95fd7-549">Когда op имеет значение NX_CRYPTO_AUTHENTICATE, это поле указывает на область памяти для созданной ECDSA сигнатуры.</span><span class="sxs-lookup"><span data-stu-id="95fd7-549">When op is NX_CRYPTO_AUTHENTICATE, this field points to the memory area for the generated ECDSA signature.</span></span> <span data-ttu-id="95fd7-550">Когда op имеет значение NX_CRYPTO_VERIFY, это поле указывает на область памяти для проверенной ECDSA сигнатуры.</span><span class="sxs-lookup"><span data-stu-id="95fd7-550">When op is NX_CRYPTO_VERIFY, this field points to the memory area for the verified ECDSA signature.</span></span>
- <span data-ttu-id="95fd7-551">**output_length_in_byte**: указывает размер буфера вывода в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-551">**output_length_in_byte** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="95fd7-552">**crypto_metadata**: указатель на блок управления ECDSA, используемый в *_nx_crypto_method_ecdsa_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-552">**crypto_metadata** Pointer to the ECDSA control block used in *_nx_crypto_method_ecdsa_init()*.</span></span>
- <span data-ttu-id="95fd7-553">**crypto_metadata_size**: размер области crypto_metadata в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-553">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="95fd7-554">Для ECDSA размер метаданных должен быть равен *sizeof(NX_CRYPTO_ECDSA)* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-554">For ECDSA, the metadata size must *sizeof(NX_CRYPTO_ECDSA)*</span></span>
- <span data-ttu-id="95fd7-555">**packet_ptr**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-555">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-556">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-556">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="95fd7-557">**nx_crypto_hw_process_callback**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-557">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-558">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-558">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-559">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-559">Return Values</span></span>

- <span data-ttu-id="95fd7-560">**NX_CRYPTO_SUCCESS** (0X00): операция ECDSA успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="95fd7-560">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the ECDSA operation.</span></span>
- <span data-ttu-id="95fd7-561">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-561">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="95fd7-562">**NX_PTR_ERROR** (0x07): недопустимый указатель ввода или длина.</span><span class="sxs-lookup"><span data-stu-id="95fd7-562">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="95fd7-563">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004): указан недопустимый алгоритм ECDSA.</span><span class="sxs-lookup"><span data-stu-id="95fd7-563">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid ECDSA algorithm being specified.</span></span>
- <span data-ttu-id="95fd7-564">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005): недопустимый размер выходного буфера.</span><span class="sxs-lookup"><span data-stu-id="95fd7-564">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_ecdsa_cleanup"></a><span data-ttu-id="95fd7-565">_nx_crypto_method_ecdsa_cleanup</span><span class="sxs-lookup"><span data-stu-id="95fd7-565">_nx_crypto_method_ecdsa_cleanup</span></span>

<span data-ttu-id="95fd7-566">Очистка блока управления ECDSA.</span><span class="sxs-lookup"><span data-stu-id="95fd7-566">Clean up the ECDSA control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-567">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-567">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdsa_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="95fd7-568">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-568">Description</span></span>

<span data-ttu-id="95fd7-569">Приложение вызывает эту функцию для очистки блока управления ECDSA после того, как определит, что этот сеанс ECDSA больше не требуется.</span><span class="sxs-lookup"><span data-stu-id="95fd7-569">Application calls this function to clean up the ECDSA control block after it determines this ECDSA session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-570">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-570">Parameters</span></span>

- <span data-ttu-id="95fd7-571">**crypto_metadata**: указатель на блок управления ECDSA, используемый в *_nx_crypto_method_ecdsa_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-571">**crypto_metadata** Pointer to the ECDSA control block used in *_nx_crypto_method_ecdsa_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-572">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-572">Return Values</span></span>

- <span data-ttu-id="95fd7-573">**NX_CRYPTO_SUCCESS** (0X00): сеанс ECDSA успешно очищен.</span><span class="sxs-lookup"><span data-stu-id="95fd7-573">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the ECDSA session.</span></span>
- <span data-ttu-id="95fd7-574">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-574">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_hmac_md5_init"></a><span data-ttu-id="95fd7-575">_nx_crypto_method_hmac_md5_init</span><span class="sxs-lookup"><span data-stu-id="95fd7-575">_nx_crypto_method_hmac_md5_init</span></span>

<span data-ttu-id="95fd7-576">Инициализирует блок управления шифрованием HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="95fd7-576">Initializes the HMAC MD5 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-577">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-577">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_md5_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="95fd7-578">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-578">Description</span></span>

<span data-ttu-id="95fd7-579">Эта функция инициализирует блок управления HMAC MD5 с заданной строкой ключа.</span><span class="sxs-lookup"><span data-stu-id="95fd7-579">This function initializes the HMAC MD5 control block with the given key string.</span></span> <span data-ttu-id="95fd7-580">После инициализации блока управления HMAC MD5 последующая операция HMAC MD5 должна использовать этот же блок управления.</span><span class="sxs-lookup"><span data-stu-id="95fd7-580">Once the HMAC MD5 control block is initialized, subsequent HMAC MD5 operation shall be using the same control block.</span></span>

<span data-ttu-id="95fd7-581">Приложение может создать несколько блоков управления HMAC MD5, представляющих отдельные сеансы.</span><span class="sxs-lookup"><span data-stu-id="95fd7-581">Application may create multiple HMAC MD5 control blocks, each represents a session.</span></span> <span data-ttu-id="95fd7-582">Инициализация блока управления HMAC MD5 запускает новый сеанс вычисления хэша.</span><span class="sxs-lookup"><span data-stu-id="95fd7-582">Initializing the HMAC MD5 control block starts a new hash computation session.</span></span> <span data-ttu-id="95fd7-583">Повторная инициализация блока управления HMAC MD5 прекращает текущий сеанс и запускает новый.</span><span class="sxs-lookup"><span data-stu-id="95fd7-583">Re-initializing the HMAC MD5 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-584">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-584">Parameters</span></span>

- <span data-ttu-id="95fd7-585">**method**: указатель на допустимый блок управления методом шифрования HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="95fd7-585">**method** Pointer to a valid HMAC MD5 crypto method control block.</span></span>
<span data-ttu-id="95fd7-586">Доступны следующие стандартные методы шифрования:</span><span class="sxs-lookup"><span data-stu-id="95fd7-586">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="95fd7-587">*crypto_method_hmac_md5*</span><span class="sxs-lookup"><span data-stu-id="95fd7-587">*crypto_method_hmac_md5*</span></span>
- <span data-ttu-id="95fd7-588">**key**: указывает на ключ.</span><span class="sxs-lookup"><span data-stu-id="95fd7-588">**key** Points to the key.</span></span> <span data-ttu-id="95fd7-589">Ограничения для буфера ключей отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="95fd7-589">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="95fd7-590">**key_size_in_bits**: размер ключа в битах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-590">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="95fd7-591">**handle**: эта служба возвращает дескриптор вызывающей стороне.</span><span class="sxs-lookup"><span data-stu-id="95fd7-591">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="95fd7-592">Этот дескриптор зависит от конкретной реализации и в данной реализации не используется.</span><span class="sxs-lookup"><span data-stu-id="95fd7-592">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="95fd7-593">Приложение должно передать значение NULL для этого дескриптора.</span><span class="sxs-lookup"><span data-stu-id="95fd7-593">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="95fd7-594">**crypto_metadata**: указатель на допустимое пространство памяти для блока управления HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="95fd7-594">**crypto_metadata** Pointer to a valid memory space for the HMAC MD5 control block.</span></span> <span data-ttu-id="95fd7-595">Начальный адрес пространства памяти должен быть выделен с буфером в 4 байта.</span><span class="sxs-lookup"><span data-stu-id="95fd7-595">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="95fd7-596">**crypto_metadata_size**: размер области crypto_metadata в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-596">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="95fd7-597">Для HMAC MD5 размер метаданных должен быть равен *sizeof(NX_CRYPTO_MD5_HMAC)* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-597">For HMAC MD5, the metadata size must be *sizeof(NX_CRYPTO_MD5_HMAC)*</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-598">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-598">Return Values</span></span>

- <span data-ttu-id="95fd7-599">**NX_CRYPTO_SUCCESS** (0X00): блок управления HMAC MD5 успешно инициализирован с заданными ключом и размером ключа.</span><span class="sxs-lookup"><span data-stu-id="95fd7-599">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the HMAC MD5 control block with the key and key size.</span></span>
- <span data-ttu-id="95fd7-600">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-600">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="95fd7-601">**NX_PTR_ERROR (0x07)** : недопустимый указатель на ключ, недопустимое значение crypto_metadata или crypto_metadata_size либо при выделении области crypto_metadata не был задан буфер в 4 байта.</span><span class="sxs-lookup"><span data-stu-id="95fd7-601">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_hmac_md5_operation"></a><span data-ttu-id="95fd7-602">_nx_crypto_method_hmac_md5_operation</span><span class="sxs-lookup"><span data-stu-id="95fd7-602">_nx_crypto_method_hmac_md5_operation</span></span>

<span data-ttu-id="95fd7-603">Выполнение хэш-операции HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="95fd7-603">Perform an HMAC MD5 hash operation.</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-604">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-604">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="95fd7-605">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-605">Description</span></span>

<span data-ttu-id="95fd7-606">Эта функция выполняет хэш-операцию HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="95fd7-606">This function performs HMAC MD5 hash operation.</span></span> <span data-ttu-id="95fd7-607">Блок управления HMAC MD5 должен быть инициализирован с помощью службы _ *nx_crypto_method_hmac_md5_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-607">The HMAC MD5 control block must have been initialized with _ *nx_crypto_method_hmac_md5_init()*.</span></span> <span data-ttu-id="95fd7-608">Выполняемый алгоритм HMAC MD5 основан на алгоритме, указанном в блоке управления *method*.</span><span class="sxs-lookup"><span data-stu-id="95fd7-608">The HMAC MD5 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="95fd7-609">Для последней операции *NX_CRYPTO_HASH_CALCULATE* размер выходного буфера должен составлять 16 байт.</span><span class="sxs-lookup"><span data-stu-id="95fd7-609">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 16 bytes.</span></span>

<span data-ttu-id="95fd7-610">Эта операция не сохраняет сведения о состоянии и не изменяет материал ключа в блоке управления HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="95fd7-610">This operation does not keep state information, and does not alter the key material in the HMAC MD5 control block.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-611">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-611">Parameters</span></span>

- <span data-ttu-id="95fd7-612">**op**: тип выполняемой операции.</span><span class="sxs-lookup"><span data-stu-id="95fd7-612">**op** Type of operation to perform.</span></span> <span data-ttu-id="95fd7-613">Допустимые операции:</span><span class="sxs-lookup"><span data-stu-id="95fd7-613">Valid operation is:</span></span>
  - <span data-ttu-id="95fd7-614">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="95fd7-614">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="95fd7-615">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="95fd7-615">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="95fd7-616">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="95fd7-616">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="95fd7-617">**handle**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-617">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-618">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-618">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="95fd7-619">**method**: указатель на допустимый метод шифрования HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="95fd7-619">**method** Pointer to the valid HMAC MD5 crypto method.</span></span> <span data-ttu-id="95fd7-620">Используемый здесь метод шифрования должен совпадать с методом, указанным в *nx_crypto_method_hmac_md5_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-620">The crypto method used here must be the same used in the *nx_crypto_method_hmac_md5_init().*</span></span>
- <span data-ttu-id="95fd7-621">**key**: указывает на ключ.</span><span class="sxs-lookup"><span data-stu-id="95fd7-621">**key** Points to the key.</span></span> <span data-ttu-id="95fd7-622">Ограничения для буфера ключей отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="95fd7-622">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="95fd7-623">**key_size_in_bits**: размер ключа в битах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-623">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="95fd7-624">**input_data**: указывает на буфер, содержащий входные текстовые данные.</span><span class="sxs-lookup"><span data-stu-id="95fd7-624">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="95fd7-625">Ограничения для входного буфера отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="95fd7-625">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="95fd7-626">**input_data_size**: размер входных данных в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-626">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="95fd7-627">**iv_ptr**: это поле не используется для HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="95fd7-627">**iv_ptr** This field is not used for HMAC MD5.</span></span>
- <span data-ttu-id="95fd7-628">**iv_size**: это поле не используется для HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="95fd7-628">**iv_size** This field is not used for HMAC MD5.</span></span>
- <span data-ttu-id="95fd7-629">**output_buffer**: указатель на область памяти для созданного HMAC MD5 хэша.</span><span class="sxs-lookup"><span data-stu-id="95fd7-629">**output_buffer** Pointer to the memory area for the generated HMAC MD5 hash.</span></span>
- <span data-ttu-id="95fd7-630">**output_buffer_size**: размер выходного буфера в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-630">**output_buffer_size** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="95fd7-631">**crypto_metadata**: указатель на блок управления HMAC MD5, используемый в *_nx_crypto_method_hmac_md5_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-631">**crypto_metadata** Pointer to the HMAC MD5 control block used in *_nx_crypto_method_hmac_md5_init()*.</span></span>
- <span data-ttu-id="95fd7-632">**crypto_metadata_size**: размер области crypto_metadata в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-632">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="95fd7-633">Для HMAC MD5 размер метаданных должен быть равен *sizeof(NX_CRYPTO_MD5_HMAC)* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-633">For HMAC MD5, the metadata size must *sizeof(NX_CRYPTO_MD5_HMAC)*</span></span>
- <span data-ttu-id="95fd7-634">**packet_ptr**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-634">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-635">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-635">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="95fd7-636">**nx_crypto_hw_process_callback**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-636">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-637">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-637">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-638">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-638">Return Values</span></span>

- <span data-ttu-id="95fd7-639">**NX_CRYPTO_SUCCESS** (0X00): операция HMAC MD5 успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="95fd7-639">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the HMAC MD5 operation.</span></span>
- <span data-ttu-id="95fd7-640">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-640">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="95fd7-641">**NX_PTR_ERROR** (0x07): недопустимый указатель ввода или длина.</span><span class="sxs-lookup"><span data-stu-id="95fd7-641">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="95fd7-642">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004): указан недопустимый алгоритм HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="95fd7-642">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid HMAC MD5 algorithm being specified.</span></span>
- <span data-ttu-id="95fd7-643">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005): недопустимый размер выходного буфера.</span><span class="sxs-lookup"><span data-stu-id="95fd7-643">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_hmac_sha1_init"></a><span data-ttu-id="95fd7-644">_nx_crypto_method_hmac_sha1_init</span><span class="sxs-lookup"><span data-stu-id="95fd7-644">_nx_crypto_method_hmac_sha1_init</span></span>

<span data-ttu-id="95fd7-645">Инициализация блока управления шифрованием HMAC SHA1.</span><span class="sxs-lookup"><span data-stu-id="95fd7-645">Initializes the HMAC SHA1 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-646">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-646">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha1_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="95fd7-647">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-647">Description</span></span>

<span data-ttu-id="95fd7-648">Эта функция инициализирует блок управления HMAC SHA1 с заданной строкой ключа.</span><span class="sxs-lookup"><span data-stu-id="95fd7-648">This function initializes the HMAC SHA1 control block with the given key string.</span></span> <span data-ttu-id="95fd7-649">После инициализации блока управления HMAC SHA1 последующая операция HMAC SHA1 должна использовать этот же блок управления.</span><span class="sxs-lookup"><span data-stu-id="95fd7-649">Once the HMAC SHA1 control block is initialized, subsequent HMAC SHA1 operation shall be using the same control block.</span></span>

<span data-ttu-id="95fd7-650">Приложение может создать несколько блоков управления HMAC SHA1, представляющих отдельные сеансы.</span><span class="sxs-lookup"><span data-stu-id="95fd7-650">Application may create multiple HMAC SHA1 control blocks, each represents a session.</span></span> <span data-ttu-id="95fd7-651">Инициализация блока управления HMAC SHA1 запускает новый сеанс вычисления хэша.</span><span class="sxs-lookup"><span data-stu-id="95fd7-651">Initializing the HMAC SHA1 control block starts a new hash computation session.</span></span> <span data-ttu-id="95fd7-652">Повторная инициализация блока управления HMAC SHA1 прекращает текущий сеанс и запускает новый.</span><span class="sxs-lookup"><span data-stu-id="95fd7-652">Re-initializing the HMAC SHA1 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-653">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-653">Parameters</span></span>

- <span data-ttu-id="95fd7-654">**method**: указатель на допустимый блок управления методом шифрования HMAC SHA1.</span><span class="sxs-lookup"><span data-stu-id="95fd7-654">**method** Pointer to a valid HMAC SHA1 crypto method control block.</span></span> <span data-ttu-id="95fd7-655">Доступны следующие стандартные методы шифрования:</span><span class="sxs-lookup"><span data-stu-id="95fd7-655">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="95fd7-656">*crypto_method_hmac_sha1*</span><span class="sxs-lookup"><span data-stu-id="95fd7-656">*crypto_method_hmac_sha1*</span></span>
- <span data-ttu-id="95fd7-657">**key**: указывает на ключ.</span><span class="sxs-lookup"><span data-stu-id="95fd7-657">**key** Points to the key.</span></span> <span data-ttu-id="95fd7-658">Ограничения для буфера ключей отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="95fd7-658">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="95fd7-659">**key_size_in_bits**: размер ключа в битах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-659">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="95fd7-660">**handle**: эта служба возвращает дескриптор вызывающей стороне.</span><span class="sxs-lookup"><span data-stu-id="95fd7-660">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="95fd7-661">Этот дескриптор зависит от конкретной реализации и в данной реализации не используется.</span><span class="sxs-lookup"><span data-stu-id="95fd7-661">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="95fd7-662">Приложение должно передать значение NULL для этого дескриптора.</span><span class="sxs-lookup"><span data-stu-id="95fd7-662">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="95fd7-663">**crypto_metadata**: указатель на допустимое пространство памяти для блока управления HMAC SHA1.</span><span class="sxs-lookup"><span data-stu-id="95fd7-663">**crypto_metadata** Pointer to a valid memory space for the HMAC SHA1 control block.</span></span> <span data-ttu-id="95fd7-664">Начальный адрес пространства памяти должен быть выделен с буфером в 4 байта.</span><span class="sxs-lookup"><span data-stu-id="95fd7-664">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="95fd7-665">**crypto_metadata_size**: размер области crypto_metadata в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-665">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="95fd7-666">Для HMAC SHA1 размер метаданных должен быть равен *sizeof(NX_CRYPTO_SHA1_HMAC)* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-666">For HMAC SHA1, the metadata size must be *sizeof(NX_CRYPTO_SHA1_HMAC)*</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-667">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-667">Return Values</span></span>

- <span data-ttu-id="95fd7-668">**NX_CRYPTO_SUCCESS** (0X00): блок управления HMAC SHA1 успешно инициализирован с заданными ключом и размером ключа.</span><span class="sxs-lookup"><span data-stu-id="95fd7-668">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the HMAC SHA1control block with the key and key size.</span></span>
- <span data-ttu-id="95fd7-669">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-669">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="95fd7-670">**NX_PTR_ERROR (0x07)** : недопустимый указатель на ключ, недопустимое значение crypto_metadata или crypto_metadata_size либо при выделении области crypto_metadata не был задан буфер в 4 байта.</span><span class="sxs-lookup"><span data-stu-id="95fd7-670">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_hmac_sha1_operation"></a><span data-ttu-id="95fd7-671">_nx_crypto_method_hmac_sha1_operation</span><span class="sxs-lookup"><span data-stu-id="95fd7-671">_nx_crypto_method_hmac_sha1_operation</span></span>

<span data-ttu-id="95fd7-672">Выполнение хэш-операции HMAC SHA1.</span><span class="sxs-lookup"><span data-stu-id="95fd7-672">Perform HMAC SHA1 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-673">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-673">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="95fd7-674">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-674">Description</span></span>

<span data-ttu-id="95fd7-675">Эта функция выполняет хэш-операцию HMAC SHA1.</span><span class="sxs-lookup"><span data-stu-id="95fd7-675">This function performs HMAC SHA1 hash operation.</span></span> <span data-ttu-id="95fd7-676">Блок управления HMAC SHA1 должен быть инициализирован с помощью службы _ *nx_crypto_method_hmac_sha1_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-676">The HMAC SHA1 control block must have been initialized with _ *nx_crypto_method_hmac_sha1_init()*.</span></span> <span data-ttu-id="95fd7-677">Выполняемый алгоритм HMAC SHA1 основан на алгоритме, указанном в блоке управления *method*.</span><span class="sxs-lookup"><span data-stu-id="95fd7-677">The HMAC SHA1 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="95fd7-678">Для последней операции *NX_CRYPTO_HASH_CALCULATE* размер выходного буфера должен составлять 20 байт.</span><span class="sxs-lookup"><span data-stu-id="95fd7-678">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 20 bytes.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-679">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-679">Parameters</span></span>

- <span data-ttu-id="95fd7-680">**op**: тип выполняемой операции.</span><span class="sxs-lookup"><span data-stu-id="95fd7-680">**op** Type of operation to perform.</span></span> <span data-ttu-id="95fd7-681">Допустимые операции:</span><span class="sxs-lookup"><span data-stu-id="95fd7-681">Valid operation is:</span></span>
  - <span data-ttu-id="95fd7-682">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="95fd7-682">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="95fd7-683">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="95fd7-683">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="95fd7-684">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="95fd7-684">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="95fd7-685">**handle**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-685">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-686">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-686">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="95fd7-687">**method**: указатель на допустимый метод шифрования HMAC SHA1.</span><span class="sxs-lookup"><span data-stu-id="95fd7-687">**method** Pointer to the valid HMAC SHA1 crypto method.</span></span> <span data-ttu-id="95fd7-688">Используемый здесь метод шифрования должен совпадать с методом, указанным в _ *nx_crypto_method_hmac_sha1_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-688">The crypto method used here must be the same used in the _ *nx_crypto_method_hmac_sha1_init().*</span></span>
- <span data-ttu-id="95fd7-689">**key**: указывает на ключ.</span><span class="sxs-lookup"><span data-stu-id="95fd7-689">**key** Points to the key.</span></span> <span data-ttu-id="95fd7-690">Ограничения для буфера ключей отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="95fd7-690">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="95fd7-691">**key_size_in_bits**: размер ключа в битах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-691">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="95fd7-692">**input_data**: указывает на буфер, содержащий входные текстовые данные.</span><span class="sxs-lookup"><span data-stu-id="95fd7-692">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="95fd7-693">Ограничения для входного буфера отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="95fd7-693">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="95fd7-694">**input_data_size**: размер входных данных в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-694">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="95fd7-695">**iv_ptr**: это поле не используется для HMAC SHA1.</span><span class="sxs-lookup"><span data-stu-id="95fd7-695">**iv_ptr** This field is not used for HMAC SHA1.</span></span>
- <span data-ttu-id="95fd7-696">**iv_size**: это поле не используется для HMAC SHA1.</span><span class="sxs-lookup"><span data-stu-id="95fd7-696">**iv_size** This field is not used for HMAC SHA1.</span></span>
- <span data-ttu-id="95fd7-697">**output_buffer**: указатель на область памяти для созданного HMAC SHA1 хэша.</span><span class="sxs-lookup"><span data-stu-id="95fd7-697">**output_buffer** Pointer to the memory area for the generated HMAC SHA1 hash.</span></span>
- <span data-ttu-id="95fd7-698">**output_buffer_size**: размер выходного буфера в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-698">**output_buffer_size** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="95fd7-699">**crypto_metadata**: указатель на блок управления HMAC SHA1, используемый в *_nx_crypto_method_hmac_sha1_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-699">**crypto_metadata** Pointer to the HMAC SHA1 control block used in *_nx_crypto_method_hmac_sha1_init()*.</span></span>
- <span data-ttu-id="95fd7-700">**crypto_metadata_size**: размер области crypto_metadata в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-700">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="95fd7-701">Для HMAC SHA1 размер метаданных должен быть равен *sizeof(NX_CRYPTO_SHA1_HMAC)* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-701">For HMAC SHA1, the metadata size must *sizeof(NX_CRYPTO_SHA1_HMAC)*</span></span>
- <span data-ttu-id="95fd7-702">**packet_ptr**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-702">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-703">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-703">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="95fd7-704">**nx_crypto_hw_process_callback**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-704">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-705">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-705">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-706">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-706">Return Values</span></span>

- <span data-ttu-id="95fd7-707">**NX_CRYPTO_SUCCESS** (0X00): операция HMAC SHA1 успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="95fd7-707">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the HMAC SHA1 operation.</span></span>
- <span data-ttu-id="95fd7-708">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-708">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="95fd7-709">**NX_PTR_ERROR** (0x07): недопустимый указатель ввода или длина.</span><span class="sxs-lookup"><span data-stu-id="95fd7-709">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="95fd7-710">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004): указан недопустимый алгоритм HMAC SHA1.</span><span class="sxs-lookup"><span data-stu-id="95fd7-710">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid HMAC SHA1 algorithm being specified.</span></span>
- <span data-ttu-id="95fd7-711">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005): недопустимый размер выходного буфера.</span><span class="sxs-lookup"><span data-stu-id="95fd7-711">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_hmac_sha1_cleanup"></a><span data-ttu-id="95fd7-712">_nx_crypto_method_hmac_sha1_cleanup</span><span class="sxs-lookup"><span data-stu-id="95fd7-712">_nx_crypto_method_hmac_sha1_cleanup</span></span>

<span data-ttu-id="95fd7-713">Очистка блока управления HMAC SHA1.</span><span class="sxs-lookup"><span data-stu-id="95fd7-713">Clean up the HMAC SHA1 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-714">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-714">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha1_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="95fd7-715">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-715">Description</span></span>

<span data-ttu-id="95fd7-716">Приложение вызывает эту функцию для очистки блока управления HMAC SHA1 после того, как определит, что этот сеанс HMAC SHA1 больше не требуется.</span><span class="sxs-lookup"><span data-stu-id="95fd7-716">Application calls this function to clean up the HMAC SHA1 control block after it determines this HMAC SHA1 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-717">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-717">Parameters</span></span>

- <span data-ttu-id="95fd7-718">**crypto_metadata**: указатель на блок управления HMAC SHA1, используемый в *_nx_crypto_method_hmac_sha1_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-718">**crypto_metadata** Pointer to the HMAC SHA1 control block used in *_nx_crypto_method_hmac_sha1_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-719">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-719">Return Values</span></span>

- <span data-ttu-id="95fd7-720">**NX_CRYPTO_SUCCESS** (0X00): сеанс HMAC SHA1 успешно очищен.</span><span class="sxs-lookup"><span data-stu-id="95fd7-720">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the HMAC SHA1 session.</span></span>
- <span data-ttu-id="95fd7-721">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-721">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_hmac_sha256_init"></a><span data-ttu-id="95fd7-722">_nx_crypto_method_hmac_sha256_init</span><span class="sxs-lookup"><span data-stu-id="95fd7-722">_nx_crypto_method_hmac_sha256_init</span></span>

<span data-ttu-id="95fd7-723">Инициализация блока управления шифрованием HMAC SHA256.</span><span class="sxs-lookup"><span data-stu-id="95fd7-723">Initializes the HMAC SHA256 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-724">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-724">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha256_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="95fd7-725">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-725">Description</span></span>

<span data-ttu-id="95fd7-726">Эта функция инициализирует блок управления HMAC SHA256 с заданной строкой ключа.</span><span class="sxs-lookup"><span data-stu-id="95fd7-726">This function initializes the HMAC SHA256 control block with the given key string.</span></span> <span data-ttu-id="95fd7-727">После инициализации блока управления HMAC SHA256 последующая операция HMAC SHA256 должна использовать этот же блок управления.</span><span class="sxs-lookup"><span data-stu-id="95fd7-727">Once the HMAC SHA256 control block is initialized, subsequent HMAC SHA256 operation shall be using the same control block.</span></span>

<span data-ttu-id="95fd7-728">Приложение может создать несколько блоков управления HMAC SHA256, представляющих отдельные сеансы.</span><span class="sxs-lookup"><span data-stu-id="95fd7-728">Application may create multiple HMAC SHA256 control blocks, each represents a session.</span></span> <span data-ttu-id="95fd7-729">Инициализация блока управления HMAC SHA256 запускает новый сеанс вычисления хэша.</span><span class="sxs-lookup"><span data-stu-id="95fd7-729">Initializing the HMAC SH256 control block starts a new hash computation session.</span></span> <span data-ttu-id="95fd7-730">Повторная инициализация блока управления HMAC SHA256 прекращает текущий сеанс и запускает новый.</span><span class="sxs-lookup"><span data-stu-id="95fd7-730">Re-initializing the HMAC SHA256 control block abandons the current session and stars a new one with a new key.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-731">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-731">Parameters</span></span>

- <span data-ttu-id="95fd7-732">**method**: указатель на допустимый блок управления методом шифрования HMAC SHA256.</span><span class="sxs-lookup"><span data-stu-id="95fd7-732">**method** Pointer to a valid HMAC SHA256 crypto method control block.</span></span> <span data-ttu-id="95fd7-733">Доступны следующие стандартные методы шифрования:</span><span class="sxs-lookup"><span data-stu-id="95fd7-733">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="95fd7-734">*crypto_method_hmac_sha224*</span><span class="sxs-lookup"><span data-stu-id="95fd7-734">*crypto_method_hmac_sha224*</span></span>
  - <span data-ttu-id="95fd7-735">*crypto_method_hmac_sha256*</span><span class="sxs-lookup"><span data-stu-id="95fd7-735">*crypto_method_hmac_sha256*</span></span>
- <span data-ttu-id="95fd7-736">**key**: указывает на ключ.</span><span class="sxs-lookup"><span data-stu-id="95fd7-736">**key** Points to the key.</span></span> <span data-ttu-id="95fd7-737">Ограничения для буфера ключей отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="95fd7-737">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="95fd7-738">**key_size_in_bits**: размер ключа в битах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-738">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="95fd7-739">**handle**: эта служба возвращает дескриптор вызывающей стороне.</span><span class="sxs-lookup"><span data-stu-id="95fd7-739">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="95fd7-740">Этот дескриптор зависит от конкретной реализации и в данной реализации не используется.</span><span class="sxs-lookup"><span data-stu-id="95fd7-740">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="95fd7-741">Приложение должно передать значение NULL для этого дескриптора.</span><span class="sxs-lookup"><span data-stu-id="95fd7-741">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="95fd7-742">**crypto_metadata**: указатель на допустимое пространство памяти для блока управления HMAC SHA256.</span><span class="sxs-lookup"><span data-stu-id="95fd7-742">**crypto_metadata** Pointer to a valid memory space for the HMAC SHA256 control block.</span></span> <span data-ttu-id="95fd7-743">Начальный адрес пространства памяти должен быть выделен с буфером в 4 байта.</span><span class="sxs-lookup"><span data-stu-id="95fd7-743">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="95fd7-744">**crypto_metadata_size**: размер области crypto_metadata в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-744">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="95fd7-745">Для HMAC SHA256 размер метаданных должен быть *sizeof(NX_CRYTPO_SHA256_HMAC)* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-745">For HMAC SHA256, the metadata size must be *sizeof(NX_CRYTPO_SHA256_HMAC)*</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-746">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-746">Return Values</span></span>

- <span data-ttu-id="95fd7-747">**NX_CRYPTO_SUCCESS** (0X00): блок управления HMAC SHA256 успешно инициализирован с заданными ключом и размером ключа.</span><span class="sxs-lookup"><span data-stu-id="95fd7-747">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the HMAC SHA256 control block with the key and key size.</span></span>
- <span data-ttu-id="95fd7-748">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-748">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="95fd7-749">**NX_PTR_ERROR (0x07)** : недопустимый указатель на ключ, недопустимое значение crypto_metadata или crypto_metadata_size либо при выделении области crypto_metadata не был задан буфер в 4 байта.</span><span class="sxs-lookup"><span data-stu-id="95fd7-749">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_hmac_sha256_operation"></a><span data-ttu-id="95fd7-750">_nx_crypto_method_hmac_sha256_operation</span><span class="sxs-lookup"><span data-stu-id="95fd7-750">_nx_crypto_method_hmac_sha256_operation</span></span>

<span data-ttu-id="95fd7-751">Выполнение хэш-операции HMAC SHA256.</span><span class="sxs-lookup"><span data-stu-id="95fd7-751">Perform HMAC SHA256 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-752">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-752">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="95fd7-753">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-753">Description</span></span>

<span data-ttu-id="95fd7-754">Эта функция выполняет хэш-операцию HMAC SHA256.</span><span class="sxs-lookup"><span data-stu-id="95fd7-754">This function performs HMAC SHA256 hash operation.</span></span> <span data-ttu-id="95fd7-755">Блок управления HMAC SHA256 должен быть инициализирован с помощью службы _ *nx_crypto_method_hmac_sha256_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-755">The HMAC SHA256 control block must have been initialized with _ *nx_crypto_method_hmac_sha256_init()*.</span></span> <span data-ttu-id="95fd7-756">Выполняемый алгоритм HMAC SHA256 основан на алгоритме, указанном в блоке управления *method*.</span><span class="sxs-lookup"><span data-stu-id="95fd7-756">The HMAC SHA256 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="95fd7-757">Для последней операции *NX_CRYPTO_HASH_CALCULATE* размер выходного буфера должен составлять 32 байта для SHA256 или 28 байт для SHA224.</span><span class="sxs-lookup"><span data-stu-id="95fd7-757">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 32 bytes for SHA256, or 28 bytes for SHA224.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-758">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-758">Parameters</span></span>

- <span data-ttu-id="95fd7-759">**op**: тип выполняемой операции.</span><span class="sxs-lookup"><span data-stu-id="95fd7-759">**op** Type of operation to perform.</span></span> <span data-ttu-id="95fd7-760">Допустимые операции:</span><span class="sxs-lookup"><span data-stu-id="95fd7-760">Valid operation is:</span></span>
  - <span data-ttu-id="95fd7-761">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="95fd7-761">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="95fd7-762">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="95fd7-762">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="95fd7-763">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="95fd7-763">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="95fd7-764">**handle**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-764">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-765">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-765">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="95fd7-766">**method**: указатель на допустимый метод шифрования HMAC SHA256.</span><span class="sxs-lookup"><span data-stu-id="95fd7-766">**method** Pointer to the valid HMAC SHA256 crypto method.</span></span> <span data-ttu-id="95fd7-767">Используемый здесь метод шифрования должен совпадать с методом, указанным в _ *nx_crypto_method_hmac_sha256_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-767">The crypto method used here must be the same used in the _ *nx_crypto_method_hmac_sha256_init().*</span></span>
- <span data-ttu-id="95fd7-768">**key**: указывает на ключ.</span><span class="sxs-lookup"><span data-stu-id="95fd7-768">**key** Points to the key.</span></span> <span data-ttu-id="95fd7-769">Ограничения для буфера ключей отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="95fd7-769">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="95fd7-770">**key_size_in_bits**: размер ключа в битах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-770">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="95fd7-771">**input_data**: указывает на буфер, содержащий входные текстовые данные.</span><span class="sxs-lookup"><span data-stu-id="95fd7-771">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="95fd7-772">Ограничения для входного буфера отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="95fd7-772">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="95fd7-773">**input_data_size**: размер входных данных в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-773">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="95fd7-774">**iv_ptr**: это поле не используется для HMAC SHA256.</span><span class="sxs-lookup"><span data-stu-id="95fd7-774">**iv_ptr** This field is not used for HMAC SHA256.</span></span>
- <span data-ttu-id="95fd7-775">**iv_size**: это поле не используется для HMAC SHA256.</span><span class="sxs-lookup"><span data-stu-id="95fd7-775">**iv_size** This field is not used for HMAC SHA256.</span></span>
- <span data-ttu-id="95fd7-776">**output_buffer**: указатель на область памяти для созданного HMAC SHA256 хэша.</span><span class="sxs-lookup"><span data-stu-id="95fd7-776">**output_buffer** Pointer to the memory area for the generated HMAC SHA256 hash.</span></span>
- <span data-ttu-id="95fd7-777">**output_buffer_size**: размер выходного буфера в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-777">**output_buffer_size** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="95fd7-778">**crypto_metadata**: указатель на блок управления HMAC SHA256, используемый в *_nx_crypto_method_hmac_sha256_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-778">**crypto_metadata** Pointer to the HMAC SHA256 control block used in *_nx_crypto_method_hmac_sha256_init()*.</span></span>
- <span data-ttu-id="95fd7-779">**crypto_metadata_size**: размер области crypto_metadata в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-779">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="95fd7-780">Для HMAC SHA256 размер метаданных должен быть равен *sizeof(NX_CRYTPO_SHA256_HMAC)* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-780">For HMAC SHA256, the metadata size must *sizeof(NX_CRYPTO_SHA256_HMAC)*</span></span>
- <span data-ttu-id="95fd7-781">**packet_ptr**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-781">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-782">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-782">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="95fd7-783">**nx_crypto_hw_process_callback**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-783">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-784">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-784">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-785">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-785">Return Values</span></span>

- <span data-ttu-id="95fd7-786">**NX_CRYPTO_SUCCESS** (0X00): операция HMAC SHA256 успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="95fd7-786">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the HMAC SHA256 operation.</span></span>
- <span data-ttu-id="95fd7-787">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-787">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="95fd7-788">**NX_PTR_ERROR** (0x07): недопустимый указатель ввода или длина.</span><span class="sxs-lookup"><span data-stu-id="95fd7-788">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="95fd7-789">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004): указан недопустимый алгоритм HMAC SHA256.</span><span class="sxs-lookup"><span data-stu-id="95fd7-789">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid HMAC SHA256 algorithm being specified.</span></span>
- <span data-ttu-id="95fd7-790">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005): недопустимый размер выходного буфера.</span><span class="sxs-lookup"><span data-stu-id="95fd7-790">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_hmac_sha256_cleanup"></a><span data-ttu-id="95fd7-791">_nx_crypto_method_hmac_sha256_cleanup</span><span class="sxs-lookup"><span data-stu-id="95fd7-791">_nx_crypto_method_hmac_sha256_cleanup</span></span>

<span data-ttu-id="95fd7-792">Очистка блока управления HMAC SHA256.</span><span class="sxs-lookup"><span data-stu-id="95fd7-792">Clean up the HMAC SHA256 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-793">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-793">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha256_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="95fd7-794">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-794">Description</span></span>

<span data-ttu-id="95fd7-795">Приложение вызывает эту функцию для очистки блока управления HMAC SHA256 после того, как определит, что этот сеанс HMAC SHA256 больше не требуется.</span><span class="sxs-lookup"><span data-stu-id="95fd7-795">Application calls this function to clean up the HMAC SHA256 control block after it determines this HMAC SHA256 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-796">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-796">Parameters</span></span>

- <span data-ttu-id="95fd7-797">**crypto_metadata**: указатель на блок управления HMAC SHA256, используемый в *_nx_crypto_method_hmac_sha256_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-797">**crypto_metadata** Pointer to the HMAC SHA256 control block used in *_nx_crypto_method_hmac_sha256_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-798">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-798">Return Values</span></span>

- <span data-ttu-id="95fd7-799">**NX_CRYPTO_SUCCESS** (0X00): сеанс HMAC SHA256 успешно очищен.</span><span class="sxs-lookup"><span data-stu-id="95fd7-799">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the HMAC SHA256 session.</span></span>
- <span data-ttu-id="95fd7-800">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-800">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_hmac_sha512_init"></a><span data-ttu-id="95fd7-801">_nx_crypto_method_hmac_sha512_init</span><span class="sxs-lookup"><span data-stu-id="95fd7-801">_nx_crypto_method_hmac_sha512_init</span></span>

<span data-ttu-id="95fd7-802">Инициализация блока управления шифрованием HMAC SHA512.</span><span class="sxs-lookup"><span data-stu-id="95fd7-802">Initializes the HMAC SHA512 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-803">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-803">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha512_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="95fd7-804">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-804">Description</span></span>

<span data-ttu-id="95fd7-805">Эта функция инициализирует блок управления HMAC SHA512 с заданной строкой ключа.</span><span class="sxs-lookup"><span data-stu-id="95fd7-805">This function initializes the HMAC SHA512 control block with the given key string.</span></span> <span data-ttu-id="95fd7-806">После инициализации блока управления HMAC SHA512 последующая операция HMAC SHA512 должна использовать этот же блок управления.</span><span class="sxs-lookup"><span data-stu-id="95fd7-806">Once the HMAC SHA512 control block is initialized, subsequent HMAC SHA512 operation shall be using the same control block.</span></span>

<span data-ttu-id="95fd7-807">Приложение может создать несколько блоков управления HMAC SHA512, представляющих отдельные сеансы.</span><span class="sxs-lookup"><span data-stu-id="95fd7-807">Application may create multiple HMAC SHA512 control blocks, each represents a session.</span></span> <span data-ttu-id="95fd7-808">Инициализация блока управления HMAC SHA512 запускает новый сеанс вычисления хэша.</span><span class="sxs-lookup"><span data-stu-id="95fd7-808">Initializing the HMAC SH512 control block starts a new hash computation session.</span></span> <span data-ttu-id="95fd7-809">Повторная инициализация блока управления HMAC SHA512 прекращает текущий сеанс и запускает новый.</span><span class="sxs-lookup"><span data-stu-id="95fd7-809">Re-initializing the HMAC SHA512 control block abandons the current session and stars a new one with a new key.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-810">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-810">Parameters</span></span>

- <span data-ttu-id="95fd7-811">**method**: указатель на допустимый блок управления методом шифрования HMAC SHA512.</span><span class="sxs-lookup"><span data-stu-id="95fd7-811">**method** Pointer to a valid HMAC SHA512 crypto method control block.</span></span> <span data-ttu-id="95fd7-812">Доступны следующие стандартные методы шифрования:</span><span class="sxs-lookup"><span data-stu-id="95fd7-812">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="95fd7-813">*crypto_method_hmac_sha384*</span><span class="sxs-lookup"><span data-stu-id="95fd7-813">*crypto_method_hmac_sha384*</span></span>
  - <span data-ttu-id="95fd7-814">*crypto_method_hmac_sha512*</span><span class="sxs-lookup"><span data-stu-id="95fd7-814">*crypto_method_hmac_sha512*</span></span>
- <span data-ttu-id="95fd7-815">**key**: указывает на ключ.</span><span class="sxs-lookup"><span data-stu-id="95fd7-815">**key** Points to the key.</span></span> <span data-ttu-id="95fd7-816">Ограничения для буфера ключей отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="95fd7-816">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="95fd7-817">**key_size_in_bits**: размер ключа в битах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-817">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="95fd7-818">**handle**: эта служба возвращает дескриптор вызывающей стороне.</span><span class="sxs-lookup"><span data-stu-id="95fd7-818">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="95fd7-819">Этот дескриптор зависит от конкретной реализации и в данной реализации не используется.</span><span class="sxs-lookup"><span data-stu-id="95fd7-819">The handle is implementation-dependent, and is not being used in this implementation.</span></span> <span data-ttu-id="95fd7-820">Приложение должно передать значение NULL для этого дескриптора.</span><span class="sxs-lookup"><span data-stu-id="95fd7-820">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="95fd7-821">**crypto_metadata**: указатель на допустимое пространство памяти для блока управления HMAC SHA512.</span><span class="sxs-lookup"><span data-stu-id="95fd7-821">**crypto_metadata** Pointer to a valid memory space for the HMAC SHA512 control block.</span></span> <span data-ttu-id="95fd7-822">Начальный адрес пространства памяти должен быть выделен с буфером в 4 байта.</span><span class="sxs-lookup"><span data-stu-id="95fd7-822">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="95fd7-823">**crypto_metadata_size**: размер области crypto_metadata в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-823">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="95fd7-824">Для HMAC SHA512 размер метаданных должен быть равен *sizeof(NX_CRYPTO_SHA512_HMAC)* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-824">For HMAC SHA512, the metadata size must be *sizeof(NX_CRYPTO_SHA512_HMAC)*</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-825">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-825">Return Values</span></span>

- <span data-ttu-id="95fd7-826">**NX_CRYPTO_SUCCESS** (0X00): блок управления HMAC SHA512 успешно инициализирован с заданными ключом и размером ключа.</span><span class="sxs-lookup"><span data-stu-id="95fd7-826">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the HMAC SHA512 control block with the key and key size.</span></span>
- <span data-ttu-id="95fd7-827">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-827">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="95fd7-828">**NX_PTR_ERROR (0x07)** : недопустимый указатель на ключ, недопустимое значение crypto_metadata или crypto_metadata_size либо при выделении области crypto_metadata не был задан буфер в 4 байта.</span><span class="sxs-lookup"><span data-stu-id="95fd7-828">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_hmac_sha512_operation"></a><span data-ttu-id="95fd7-829">_nx_crypto_method_hmac_sha512_operation</span><span class="sxs-lookup"><span data-stu-id="95fd7-829">_nx_crypto_method_hmac_sha512_operation</span></span>

<span data-ttu-id="95fd7-830">Выполнение хэш-операции HMAC SHA512.</span><span class="sxs-lookup"><span data-stu-id="95fd7-830">Perform HMAC SHA512 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-831">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-831">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="95fd7-832">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-832">Description</span></span>

<span data-ttu-id="95fd7-833">Эта функция выполняет хэш-операцию HMAC SHA512.</span><span class="sxs-lookup"><span data-stu-id="95fd7-833">This function performs HMAC SHA512 hash operation.</span></span> <span data-ttu-id="95fd7-834">Блок управления HMAC SHA512 должен быть инициализирован с помощью службы _ *nx_crypto_method_hmac_sha512_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-834">The HMAC SHA512 control block must have been initialized with _ *nx_crypto_method_hmac_sha512_init()*.</span></span> <span data-ttu-id="95fd7-835">Выполняемый алгоритм HMAC SHA512 основан на алгоритме, указанном в блоке управления *method*.</span><span class="sxs-lookup"><span data-stu-id="95fd7-835">The HMAC SHA512 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="95fd7-836">Для последней операции *NX_CRYPTO_HASH_CALCULATE* размер выходного буфера должен составлять 64 байта для SHA512 или 48 байт для SHA384.</span><span class="sxs-lookup"><span data-stu-id="95fd7-836">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 64 bytes for SHA512, or 48 bytes for SHA384.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-837">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-837">Parameters</span></span>

- <span data-ttu-id="95fd7-838">**op**: тип выполняемой операции.</span><span class="sxs-lookup"><span data-stu-id="95fd7-838">**op** Type of operation to perform.</span></span> <span data-ttu-id="95fd7-839">Допустимые операции:</span><span class="sxs-lookup"><span data-stu-id="95fd7-839">Valid operation is:</span></span>
  - <span data-ttu-id="95fd7-840">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="95fd7-840">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="95fd7-841">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="95fd7-841">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="95fd7-842">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="95fd7-842">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="95fd7-843">**handle**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-843">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-844">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-844">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="95fd7-845">**method**: указатель на допустимый метод шифрования HMAC SHA512.</span><span class="sxs-lookup"><span data-stu-id="95fd7-845">**method** Pointer to the valid HMAC SHA512 crypto method.</span></span> <span data-ttu-id="95fd7-846">Используемый здесь метод шифрования должен совпадать с методом, указанным в _ *nx_crypto_method_hmac_sha512_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-846">The crypto method used here must be the same used in the _ *nx_crypto_method_hmac_sha512_init().*</span></span>
- <span data-ttu-id="95fd7-847">**key**: указывает на ключ.</span><span class="sxs-lookup"><span data-stu-id="95fd7-847">**key** Points to the key.</span></span> <span data-ttu-id="95fd7-848">Ограничения для буфера ключей отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="95fd7-848">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="95fd7-849">**key_size_in_bits**: размер ключа в битах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-849">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="95fd7-850">**input_data**: указывает на буфер, содержащий входные текстовые данные.</span><span class="sxs-lookup"><span data-stu-id="95fd7-850">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="95fd7-851">Ограничения для входного буфера отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="95fd7-851">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="95fd7-852">**input_data_size**: размер входных данных в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-852">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="95fd7-853">**iv_ptr**: это поле не используется для HMAC SHA512.</span><span class="sxs-lookup"><span data-stu-id="95fd7-853">**iv_ptr** This field is not used for HMAC SHA512.</span></span>
- <span data-ttu-id="95fd7-854">**iv_size**: это поле не используется для HMAC SHA512.</span><span class="sxs-lookup"><span data-stu-id="95fd7-854">**iv_size** This field is not used for HMAC SHA512.</span></span>
- <span data-ttu-id="95fd7-855">**output_buffer**: указатель на область памяти для созданного HMAC SHA512 хэша.</span><span class="sxs-lookup"><span data-stu-id="95fd7-855">**output_buffer** Pointer to the memory area for the generated HMAC SHA512 hash.</span></span>
- <span data-ttu-id="95fd7-856">**output_buffer_size**: размер выходного буфера в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-856">**output_buffer_size** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="95fd7-857">**crypto_metadata**: указатель на блок управления HMAC SHA512, используемый в *_nx_crypto_method_hmac_sha512_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-857">**crypto_metadata** Pointer to the HMAC SHA512 control block used in *_nx_crypto_method_hmac_sha512_init()*.</span></span>
- <span data-ttu-id="95fd7-858">**crypto_metadata_size**: размер области crypto_metadata в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-858">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="95fd7-859">Для HMAC SHA512 размер метаданных должен быть равен *sizeof(NX_CRYPTO_SHA512_HMAC)* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-859">For HMAC SHA512, the metadata size must *sizeof(NX_CRYPTO_SHA512_HMAC)*</span></span>
- <span data-ttu-id="95fd7-860">**packet_ptr**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-860">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-861">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-861">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="95fd7-862">**nx_crypto_hw_process_callback**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-862">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-863">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-863">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-864">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-864">Return Values</span></span>

- <span data-ttu-id="95fd7-865">**NX_CRYPTO_SUCCESS** (0X00): операция HMAC SHA512 успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="95fd7-865">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the HMAC SHA512 operation.</span></span>
- <span data-ttu-id="95fd7-866">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-866">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="95fd7-867">**NX_PTR_ERROR** (0x07): недопустимый указатель ввода или длина.</span><span class="sxs-lookup"><span data-stu-id="95fd7-867">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="95fd7-868">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004): указан недопустимый алгоритм HMAC SHA512.</span><span class="sxs-lookup"><span data-stu-id="95fd7-868">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid HMAC SHA512 algorithm being specified.</span></span>
- <span data-ttu-id="95fd7-869">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005): недопустимый размер выходного буфера.</span><span class="sxs-lookup"><span data-stu-id="95fd7-869">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_hmac_sha512_cleanup"></a><span data-ttu-id="95fd7-870">_nx_crypto_method_hmac_sha512_cleanup</span><span class="sxs-lookup"><span data-stu-id="95fd7-870">_nx_crypto_method_hmac_sha512_cleanup</span></span>

<span data-ttu-id="95fd7-871">Очистка блока управления HMAC SHA512.</span><span class="sxs-lookup"><span data-stu-id="95fd7-871">Clean up the HMAC SHA512 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-872">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-872">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha512_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="95fd7-873">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-873">Description</span></span>

<span data-ttu-id="95fd7-874">Приложение вызывает эту функцию для очистки блока управления HMAC SHA512 после того, как определит, что этот сеанс HMAC SHA512 больше не требуется.</span><span class="sxs-lookup"><span data-stu-id="95fd7-874">Application calls this function to clean up the HMAC SHA512 control block after it determines this HMAC SHA512 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-875">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-875">Parameters</span></span>

- <span data-ttu-id="95fd7-876">**crypto_metadata**: указатель на блок управления HMAC SHA512, используемый в *_nx_crypto_method_hmac_sha512_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-876">**crypto_metadata** Pointer to the HMAC SHA512 control block used in *_nx_crypto_method_hmac_sha512_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-877">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-877">Return Values</span></span>

- <span data-ttu-id="95fd7-878">**NX_CRYPTO_SUCCESS** (0X00): сеанс HMAC SHA512 успешно очищен.</span><span class="sxs-lookup"><span data-stu-id="95fd7-878">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the HMAC SHA512 session.</span></span>
- <span data-ttu-id="95fd7-879">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-879">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

### <a name="example"></a><span data-ttu-id="95fd7-880">Например, .</span><span class="sxs-lookup"><span data-stu-id="95fd7-880">Example</span></span> 

## <a name="_nx_crypto_method_md5_init"></a><span data-ttu-id="95fd7-881">_nx_crypto_method_md5_init</span><span class="sxs-lookup"><span data-stu-id="95fd7-881">_nx_crypto_method_md5_init</span></span>

<span data-ttu-id="95fd7-882">Инициализация блока управления шифрованием MD5.</span><span class="sxs-lookup"><span data-stu-id="95fd7-882">Initializes the MD5 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-883">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-883">Prototype</span></span>

```c
UINT _nx_crypto_method_md5_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="95fd7-884">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-884">Description</span></span>

<span data-ttu-id="95fd7-885">Эта функция инициализирует блок управления MD5 с заданной строкой ключа.</span><span class="sxs-lookup"><span data-stu-id="95fd7-885">This function initializes the MD5 control block with the given key string.</span></span> <span data-ttu-id="95fd7-886">После инициализации блока управления MD5 последующая операция MD5 должна использовать этот же блок управления.</span><span class="sxs-lookup"><span data-stu-id="95fd7-886">Once the MD5 control block is initialized, subsequent MD5 operation shall be using the same control block.</span></span>

<span data-ttu-id="95fd7-887">Приложение может создать несколько блоков управления MD5, представляющих отдельные сеансы.</span><span class="sxs-lookup"><span data-stu-id="95fd7-887">Application may create multiple MD5 control blocks, each represents a session.</span></span> <span data-ttu-id="95fd7-888">Инициализация блока управления MD5 запускает новый сеанс вычисления хэша.</span><span class="sxs-lookup"><span data-stu-id="95fd7-888">Initializing the MD5 control block starts a new hash computation session.</span></span> <span data-ttu-id="95fd7-889">Повторная инициализация блока управления MD5 прекращает текущий сеанс и запускает новый.</span><span class="sxs-lookup"><span data-stu-id="95fd7-889">Re-initializing the MD5 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-890">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-890">Parameters</span></span>

- <span data-ttu-id="95fd7-891">**method**: указатель на допустимый блок управления методом шифрования MD5.</span><span class="sxs-lookup"><span data-stu-id="95fd7-891">**method** Pointer to a valid MD5 crypto method control block.</span></span> <span data-ttu-id="95fd7-892">Доступны следующие стандартные методы шифрования:</span><span class="sxs-lookup"><span data-stu-id="95fd7-892">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="95fd7-893">*crypto_method_md5*</span><span class="sxs-lookup"><span data-stu-id="95fd7-893">*crypto_method_md5*</span></span>
- <span data-ttu-id="95fd7-894">**key**: это поле не используется для MD5.</span><span class="sxs-lookup"><span data-stu-id="95fd7-894">**key** This field is not used for MD5.</span></span>
- <span data-ttu-id="95fd7-895">**key_size_in_bits**: это поле не используется для MD5.</span><span class="sxs-lookup"><span data-stu-id="95fd7-895">**key_size_in_bits** This field is not used for MD5</span></span>
- <span data-ttu-id="95fd7-896">**handle**: эта служба возвращает дескриптор вызывающей стороне.</span><span class="sxs-lookup"><span data-stu-id="95fd7-896">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="95fd7-897">Этот дескриптор зависит от конкретной реализации и в данной реализации не используется.</span><span class="sxs-lookup"><span data-stu-id="95fd7-897">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="95fd7-898">Приложение должно передать значение NULL для этого дескриптора.</span><span class="sxs-lookup"><span data-stu-id="95fd7-898">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="95fd7-899">**crypto_metadata**: указатель на допустимое пространство памяти для блока управления MD5.</span><span class="sxs-lookup"><span data-stu-id="95fd7-899">**crypto_metadata** Pointer to a valid memory space for the MD5 control block.</span></span> <span data-ttu-id="95fd7-900">Начальный адрес пространства памяти должен быть выделен с буфером в 4 байта.</span><span class="sxs-lookup"><span data-stu-id="95fd7-900">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="95fd7-901">**crypto_metadata_size**: размер области crypto_metadata в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-901">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="95fd7-902">Для MD5 размер метаданных должен быть равен *sizeof(NX_CRYPTO_MD5)* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-902">For MD5, the metadata size must be *sizeof(NX_CRYPTO_MD5)*</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-903">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-903">Return Values</span></span>

- <span data-ttu-id="95fd7-904">**NX_CRYPTO_SUCCESS** (0X00): блок управления MD5 успешно инициализирован с заданными ключом и размером ключа.</span><span class="sxs-lookup"><span data-stu-id="95fd7-904">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the MD5 control block with the key and key size.</span></span>
- <span data-ttu-id="95fd7-905">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-905">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="95fd7-906">**NX_PTR_ERROR (0x07)** : недопустимый указатель на ключ, недопустимое значение crypto_metadata или crypto_metadata_size либо при выделении области crypto_metadata не был задан буфер в 4 байта.</span><span class="sxs-lookup"><span data-stu-id="95fd7-906">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

### <a name="example"></a><span data-ttu-id="95fd7-907">Например, .</span><span class="sxs-lookup"><span data-stu-id="95fd7-907">Example</span></span>

## <a name="_nx_crypto_method_md5_operation"></a><span data-ttu-id="95fd7-908">_nx_crypto_method_md5_operation</span><span class="sxs-lookup"><span data-stu-id="95fd7-908">_nx_crypto_method_md5_operation</span></span>

<span data-ttu-id="95fd7-909">Выполнение хэш-операции MD5.</span><span class="sxs-lookup"><span data-stu-id="95fd7-909">Perform an MD5 hash operation.</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-910">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-910">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="95fd7-911">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-911">Description</span></span>

<span data-ttu-id="95fd7-912">Эта функция выполняет хэш-операцию MD5.</span><span class="sxs-lookup"><span data-stu-id="95fd7-912">This function performs MD5 hash operation.</span></span> <span data-ttu-id="95fd7-913">Блок управления MD5 должен быть инициализирован с помощью службы _ *nx_crypto_method_md5_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-913">The MD5 control block must have been initialized with _ *nx_crypto_method_md5_init()*.</span></span> <span data-ttu-id="95fd7-914">Выполняемый алгоритм MD5 основан на алгоритме, указанном в блоке управления *method*.</span><span class="sxs-lookup"><span data-stu-id="95fd7-914">The MD5 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="95fd7-915">Для последней операции *NX_CRYPTO_HASH_CALCULATE* размер выходного буфера должен составлять 16 байт.</span><span class="sxs-lookup"><span data-stu-id="95fd7-915">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 16 bytes.</span></span>

<span data-ttu-id="95fd7-916">Эта операция не сохраняет сведения о состоянии и не изменяет материал ключа в блоке управления MD5.</span><span class="sxs-lookup"><span data-stu-id="95fd7-916">This operation does not keep state information and does not alter the key material in the MD5 control block.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-917">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-917">Parameters</span></span>

- <span data-ttu-id="95fd7-918">**op**: тип выполняемой операции.</span><span class="sxs-lookup"><span data-stu-id="95fd7-918">**op** Type of operation to perform.</span></span> <span data-ttu-id="95fd7-919">Допустимые операции:</span><span class="sxs-lookup"><span data-stu-id="95fd7-919">Valid operation is:</span></span>
  - <span data-ttu-id="95fd7-920">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="95fd7-920">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="95fd7-921">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="95fd7-921">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="95fd7-922">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="95fd7-922">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="95fd7-923">**handle**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-923">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-924">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-924">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="95fd7-925">**method**: указатель на допустимый метод шифрования MD5.</span><span class="sxs-lookup"><span data-stu-id="95fd7-925">**method** Pointer to the valid MD5 crypto method.</span></span> <span data-ttu-id="95fd7-926">Используемый здесь метод шифрования должен совпадать с методом, указанным в _ *nx_crypto_method_md5_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-926">The crypto method used here must be the same used in the _ *nx_crypto_method_md5_init().*</span></span>
- <span data-ttu-id="95fd7-927">**input_data**: указывает на буфер, содержащий входные текстовые данные.</span><span class="sxs-lookup"><span data-stu-id="95fd7-927">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="95fd7-928">Ограничения для входного буфера отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="95fd7-928">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="95fd7-929">**input_data_size**: размер входных данных в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-929">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="95fd7-930">**iv_ptr**: это поле не используется для MD5.</span><span class="sxs-lookup"><span data-stu-id="95fd7-930">**iv_ptr** This field is not used for MD5.</span></span>
- <span data-ttu-id="95fd7-931">**iv_size**: это поле не используется для MD5.</span><span class="sxs-lookup"><span data-stu-id="95fd7-931">**iv_size** This field is not used for MD5.</span></span>
- <span data-ttu-id="95fd7-932">**output_buffer**: указатель на область памяти для созданного MD5 хэша.</span><span class="sxs-lookup"><span data-stu-id="95fd7-932">**output_buffer** Pointer to the memory area for the generated MD5 hash.</span></span>
- <span data-ttu-id="95fd7-933">**output_buffer_size**: размер выходного буфера в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-933">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="95fd7-934">Для MD5 размер буфера должен составлять 16 байт.</span><span class="sxs-lookup"><span data-stu-id="95fd7-934">For MD5 the buffer size must be 16 bytes.</span></span>
- <span data-ttu-id="95fd7-935">**crypto_metadata**: указатель на блок управления MD5, используемый в *_nx_crypto_method_md5_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-935">**crypto_metadata** Pointer to the MD5 control block used in *_nx_crypto_method_md5_init()*.</span></span>
- <span data-ttu-id="95fd7-936">**crypto_metadata_size**: размер области crypto_metadata в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-936">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="95fd7-937">Для MD5 размер метаданных должен быть равен *sizeof(NX_CRYPTO_MD5)* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-937">For MD5, the metadata size must *sizeof(NX_CRYPTO_MD5)*</span></span>
- <span data-ttu-id="95fd7-938">**packet_ptr**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-938">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-939">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-939">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="95fd7-940">**nx_crypto_hw_process_callback**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-940">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-941">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-941">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-942">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-942">Return Values</span></span>

- <span data-ttu-id="95fd7-943">**NX_CRYPTO_SUCCESS** (0X00): операция MD5 успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="95fd7-943">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the MD5 operation.</span></span>
- <span data-ttu-id="95fd7-944">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-944">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="95fd7-945">**NX_PTR_ERROR** (0x07): недопустимый указатель ввода или длина.</span><span class="sxs-lookup"><span data-stu-id="95fd7-945">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="95fd7-946">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004): указан недопустимый алгоритм MD5.</span><span class="sxs-lookup"><span data-stu-id="95fd7-946">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid MD5 algorithm being specified.</span></span>
- <span data-ttu-id="95fd7-947">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005): недопустимый размер выходного буфера.</span><span class="sxs-lookup"><span data-stu-id="95fd7-947">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_md5_cleanup"></a><span data-ttu-id="95fd7-948">_nx_crypto_method_md5_cleanup</span><span class="sxs-lookup"><span data-stu-id="95fd7-948">_nx_crypto_method_md5_cleanup</span></span>

<span data-ttu-id="95fd7-949">Очистка блока управления MD5.</span><span class="sxs-lookup"><span data-stu-id="95fd7-949">Clean up the MD5 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-950">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-950">Prototype</span></span>

```c
UINT _nx_crypto_method_md5_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="95fd7-951">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-951">Description</span></span>

<span data-ttu-id="95fd7-952">Приложение вызывает эту функцию для очистки блока управления MD5 после того, как определит, что этот сеанс MD5 больше не требуется.</span><span class="sxs-lookup"><span data-stu-id="95fd7-952">Application calls this function to clean up the MD5 control block after it determines this MD5 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-953">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-953">Parameters</span></span>

- <span data-ttu-id="95fd7-954">**crypto_metadata**: указатель на блок управления MD5, используемый в *_nx_crypto_method_md5_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-954">**crypto_metadata** Pointer to the MD5 control block used in *_nx_crypto_method_md5_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-955">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-955">Return Values</span></span>

- <span data-ttu-id="95fd7-956">**NX_CRYPTO_SUCCESS** (0X00): сеанс MD5 успешно очищен.</span><span class="sxs-lookup"><span data-stu-id="95fd7-956">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the MD5 session.</span></span>
- <span data-ttu-id="95fd7-957">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-957">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_sha1_init"></a><span data-ttu-id="95fd7-958">_nx_crypto_method_sha1_init</span><span class="sxs-lookup"><span data-stu-id="95fd7-958">_nx_crypto_method_sha1_init</span></span>

<span data-ttu-id="95fd7-959">Инициализация блока управления шифрованием SHA1.</span><span class="sxs-lookup"><span data-stu-id="95fd7-959">Initializes the SHA1 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-960">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-960">Prototype</span></span>

```c
UINT _nx_crypto_method_sha1_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="95fd7-961">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-961">Description</span></span>

<span data-ttu-id="95fd7-962">Эта функция инициализирует блок управления SHA1 с заданной строкой ключа.</span><span class="sxs-lookup"><span data-stu-id="95fd7-962">This function initializes the SHA1 control block with the given key string.</span></span> <span data-ttu-id="95fd7-963">После инициализации блока управления SHA1 последующая операция SHA1 должна использовать этот же блок управления.</span><span class="sxs-lookup"><span data-stu-id="95fd7-963">Once the SHA1 control block is initialized, subsequent SHA1 operation shall be using the same control block.</span></span>

<span data-ttu-id="95fd7-964">Приложение может создать несколько блоков управления SHA1, представляющих отдельные сеансы.</span><span class="sxs-lookup"><span data-stu-id="95fd7-964">Application may create multiple SHA1 control blocks, each represents a session.</span></span> <span data-ttu-id="95fd7-965">Инициализация блока управления SHA1 запускает новый сеанс вычисления хэша.</span><span class="sxs-lookup"><span data-stu-id="95fd7-965">Initializing the SHA1 control block starts a new hash computation session.</span></span> <span data-ttu-id="95fd7-966">Повторная инициализация блока управления SHA1 прекращает текущий сеанс и запускает новый.</span><span class="sxs-lookup"><span data-stu-id="95fd7-966">Re-initializing the SHA1 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-967">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-967">Parameters</span></span>

- <span data-ttu-id="95fd7-968">**method**: указатель на допустимый блок управления методом шифрования SHA1.</span><span class="sxs-lookup"><span data-stu-id="95fd7-968">**method** Pointer to a valid SHA1 crypto method control block.</span></span> <span data-ttu-id="95fd7-969">Доступны следующие стандартные методы шифрования:</span><span class="sxs-lookup"><span data-stu-id="95fd7-969">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="95fd7-970">*crypto_method_sha1*</span><span class="sxs-lookup"><span data-stu-id="95fd7-970">*crypto_method_sha1*</span></span>
- <span data-ttu-id="95fd7-971">**key**: это поле не используется для SHA1.</span><span class="sxs-lookup"><span data-stu-id="95fd7-971">**key** This field is not used for SHA1.</span></span>
- <span data-ttu-id="95fd7-972">**key_size_in_bits**: это поле не используется для SHA1.</span><span class="sxs-lookup"><span data-stu-id="95fd7-972">**key_size_in_bits** This field is not used for SHA1</span></span>
- <span data-ttu-id="95fd7-973">**handle**: эта служба возвращает дескриптор вызывающей стороне.</span><span class="sxs-lookup"><span data-stu-id="95fd7-973">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="95fd7-974">Этот дескриптор зависит от конкретной реализации и в данной реализации не используется.</span><span class="sxs-lookup"><span data-stu-id="95fd7-974">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="95fd7-975">Приложение должно передать значение NULL для этого дескриптора.</span><span class="sxs-lookup"><span data-stu-id="95fd7-975">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="95fd7-976">**crypto_metadata**: указатель на допустимое пространство памяти для блока управления SHA1.</span><span class="sxs-lookup"><span data-stu-id="95fd7-976">**crypto_metadata** Pointer to a valid memory space for the SHA1 control block.</span></span> <span data-ttu-id="95fd7-977">Начальный адрес пространства памяти должен быть выделен с буфером в 4 байта.</span><span class="sxs-lookup"><span data-stu-id="95fd7-977">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="95fd7-978">**crypto_metadata_size**: размер области crypto_metadata в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-978">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="95fd7-979">Для SHA1 размер метаданных должен быть равен *sizeof(NX_CRYPTO_SHA1)* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-979">For SHA1, the metadata size must be *sizeof(NX_CRYPTO_SHA1)*</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-980">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-980">Return Values</span></span>

- <span data-ttu-id="95fd7-981">**NX_CRYPTO_SUCCESS** (0X00): блок управления SHA1 успешно инициализирован с заданными ключом и размером ключа.</span><span class="sxs-lookup"><span data-stu-id="95fd7-981">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the SHA1control block with the key and key size.</span></span>
- <span data-ttu-id="95fd7-982">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-982">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="95fd7-983">**NX_PTR_ERROR (0x07)** : недопустимый указатель на ключ, недопустимое значение crypto_metadata или crypto_metadata_size либо при выделении области crypto_metadata не был задан буфер в 4 байта.</span><span class="sxs-lookup"><span data-stu-id="95fd7-983">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_sha1_operation"></a><span data-ttu-id="95fd7-984">_nx_crypto_method_sha1_operation</span><span class="sxs-lookup"><span data-stu-id="95fd7-984">_nx_crypto_method_sha1_operation</span></span>

<span data-ttu-id="95fd7-985">Выполнение хэш-операции SHA1.</span><span class="sxs-lookup"><span data-stu-id="95fd7-985">Perform SHA1 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-986">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-986">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="95fd7-987">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-987">Description</span></span>

<span data-ttu-id="95fd7-988">Эта функция выполняет хэш-операцию SHA1.</span><span class="sxs-lookup"><span data-stu-id="95fd7-988">This function performs SHA1 hash operation.</span></span> <span data-ttu-id="95fd7-989">Блок управления SHA1 должен быть инициализирован с помощью службы _ *nx_crypto_method_sha1_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-989">The SHA1 control block must have been initialized with _ *nx_crypto_method_sha1_init()*.</span></span> <span data-ttu-id="95fd7-990">Выполняемый алгоритм SHA1 основан на алгоритме, указанном в блоке управления *method*.</span><span class="sxs-lookup"><span data-stu-id="95fd7-990">The SHA1 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="95fd7-991">Для последней операции *NX_CRYPTO_HASH_CALCULATE* размер выходного буфера должен составлять 20 байт.</span><span class="sxs-lookup"><span data-stu-id="95fd7-991">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 20 bytes.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-992">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-992">Parameters</span></span>

- <span data-ttu-id="95fd7-993">**op**: тип выполняемой операции.</span><span class="sxs-lookup"><span data-stu-id="95fd7-993">**op** Type of operation to perform.</span></span> <span data-ttu-id="95fd7-994">Допустимые операции:</span><span class="sxs-lookup"><span data-stu-id="95fd7-994">Valid operation is:</span></span>
  - <span data-ttu-id="95fd7-995">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="95fd7-995">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="95fd7-996">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="95fd7-996">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="95fd7-997">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="95fd7-997">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="95fd7-998">**handle**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-998">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-999">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-999">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="95fd7-1000">**method**: указатель на допустимый метод шифрования SHA1.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1000">**method** Pointer to the valid SHA1 crypto method.</span></span> <span data-ttu-id="95fd7-1001">Используемый здесь метод шифрования должен совпадать с методом, указанным в *nx_crypto_method_sha1_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-1001">The crypto method used here must be the same used in the *nx_crypto_method_sha1_init().*</span></span>
- <span data-ttu-id="95fd7-1002">**input_data**: указывает на буфер, содержащий входные текстовые данные.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1002">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="95fd7-1003">Ограничения для входного буфера отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1003">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="95fd7-1004">**input_data_size**: размер входных данных в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1004">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="95fd7-1005">**iv_ptr**: это поле не используется для SHA1.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1005">**iv_ptr** This field is not used for SHA1.</span></span>
- <span data-ttu-id="95fd7-1006">**iv_size**: это поле не используется для SHA1.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1006">**iv_size** This field is not used for SHA1.</span></span>
- <span data-ttu-id="95fd7-1007">**output_buffer**: указатель на область памяти для созданного SHA1 хэша.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1007">**output_buffer** Pointer to the memory area for the generated SHA1 hash.</span></span>
- <span data-ttu-id="95fd7-1008">**output_buffer_size**: размер выходного буфера в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1008">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="95fd7-1009">Для SHA1 размер буфера должен составлять 20 байт.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1009">For SHA1 the buffer size must be 20 bytes.</span></span>
- <span data-ttu-id="95fd7-1010">**crypto_metadata**: указатель на блок управления SHA1, используемый в *_nx_crypto_method_sha1_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-1010">**crypto_metadata** Pointer to the SHA1 control block used in *_nx_crypto_method_sha1_init()*.</span></span>
- <span data-ttu-id="95fd7-1011">**crypto_metadata_size**: размер области crypto_metadata в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1011">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="95fd7-1012">Для SHA1 размер метаданных должен быть равен *sizeof(NX_CRYPTO_SHA1)* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-1012">For SHA1, the metadata size must *sizeof(NX_CRYPTO_SHA1)*</span></span>
- <span data-ttu-id="95fd7-1013">**packet_ptr**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1013">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-1014">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1014">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="95fd7-1015">**nx_crypto_hw_process_callback**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1015">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-1016">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1016">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-1017">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-1017">Return Values</span></span>

- <span data-ttu-id="95fd7-1018">**NX_CRYPTO_SUCCESS** (0X00): операция SHA1 успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1018">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the SHA1 operation.</span></span>
- <span data-ttu-id="95fd7-1019">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1019">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="95fd7-1020">**NX_PTR_ERROR** (0x07): недопустимый указатель ввода или длина.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1020">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="95fd7-1021">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004): указан недопустимый алгоритм SHA1.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1021">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid SHA1 algorithm being specified.</span></span>
- <span data-ttu-id="95fd7-1022">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005): недопустимый размер выходного буфера.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1022">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

### <a name="example"></a><span data-ttu-id="95fd7-1023">Например, .</span><span class="sxs-lookup"><span data-stu-id="95fd7-1023">Example</span></span>

## <a name="_nx_crypto_method_sha1_cleanup"></a><span data-ttu-id="95fd7-1024">_nx_crypto_method_sha1_cleanup</span><span class="sxs-lookup"><span data-stu-id="95fd7-1024">_nx_crypto_method_sha1_cleanup</span></span>

<span data-ttu-id="95fd7-1025">Очистка блока управления SHA1.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1025">Clean up the SHA1 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-1026">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-1026">Prototype</span></span>

```c
UINT _nx_crypto_method_sha1_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="95fd7-1027">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-1027">Description</span></span>

<span data-ttu-id="95fd7-1028">Приложение вызывает эту функцию для очистки блока управления SHA1 после того, как определит, что этот сеанс SHA1 больше не требуется.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1028">Application calls this function to clean up the SHA1 control block after it determines this SHA1 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-1029">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-1029">Parameters</span></span>

- <span data-ttu-id="95fd7-1030">**crypto_metadata**: указатель на блок управления SHA1, используемый в *_nx_crypto_method_sha1_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-1030">**crypto_metadata** Pointer to the SHA1 control block used in *_nx_crypto_method_sha1_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-1031">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-1031">Return Values</span></span>

- <span data-ttu-id="95fd7-1032">**NX_CRYPTO_SUCCESS** (0X00): сеанс SHA1 успешно очищен.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1032">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the SHA1 session.</span></span>
- <span data-ttu-id="95fd7-1033">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1033">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_sha256_init"></a><span data-ttu-id="95fd7-1034">_nx_crypto_method_sha256_init</span><span class="sxs-lookup"><span data-stu-id="95fd7-1034">_nx_crypto_method_sha256_init</span></span>

<span data-ttu-id="95fd7-1035">Инициализация блока управления шифрованием SHA256.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1035">Initializes the SHA256 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-1036">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-1036">Prototype</span></span>

```c
UINT _nx_crypto_method_sha256_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size)
```

### <a name="description"></a><span data-ttu-id="95fd7-1037">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-1037">Description</span></span>

<span data-ttu-id="95fd7-1038">Эта функция инициализирует блок управления SHA256 с заданной строкой ключа.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1038">This function initializes the SHA256 control block with the given key string.</span></span> <span data-ttu-id="95fd7-1039">После инициализации блока управления SHA256 последующая операция SHA256 должна использовать этот же блок управления.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1039">Once the SHA256 control block is initialized, subsequent SHA256 operation shall be using the same control block.</span></span>

<span data-ttu-id="95fd7-1040">Приложение может создать несколько блоков управления SHA256, представляющих отдельные сеансы.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1040">Application may create multiple SHA256 control blocks, each represents a session.</span></span> <span data-ttu-id="95fd7-1041">Инициализация блока управления SHA256 запускает новый сеанс вычисления хэша.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1041">Initializing the SHA256 control block starts a new hash computation session.</span></span> <span data-ttu-id="95fd7-1042">Повторная инициализация блока управления SHA256 прекращает текущий сеанс и запускает новый.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1042">Re-initializing the SHA256 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-1043">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-1043">Parameters</span></span>

- <span data-ttu-id="95fd7-1044">**method**: указатель на допустимый блок управления методом шифрования SHA256.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1044">**method** Pointer to a valid SHA256 crypto method control block.</span></span> <span data-ttu-id="95fd7-1045">Доступны следующие стандартные методы шифрования:</span><span class="sxs-lookup"><span data-stu-id="95fd7-1045">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="95fd7-1046">*crypto_method_sha256*</span><span class="sxs-lookup"><span data-stu-id="95fd7-1046">*crypto_method_sha256*</span></span>
  - <span data-ttu-id="95fd7-1047">*crypto_method_sha224*</span><span class="sxs-lookup"><span data-stu-id="95fd7-1047">*crypto_method_sha224*</span></span>
- <span data-ttu-id="95fd7-1048">**key**: это поле не используется для SHA256.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1048">**key** This field is not used for SHA256.</span></span>
- <span data-ttu-id="95fd7-1049">**key_size_in_bits**: это поле не используется для SHA256.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1049">**key_size_in_bits** This field is not used for SHA256</span></span>
- <span data-ttu-id="95fd7-1050">**handle**: эта служба возвращает дескриптор вызывающей стороне.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1050">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="95fd7-1051">Этот дескриптор зависит от конкретной реализации и в данной реализации не используется.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1051">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="95fd7-1052">Приложение должно передать значение NULL для этого дескриптора.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1052">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="95fd7-1053">**crypto_metadata**: указатель на допустимое пространство памяти для блока управления SHA256.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1053">**crypto_metadata** Pointer to a valid memory space for the SHA256 control block.</span></span> <span data-ttu-id="95fd7-1054">Начальный адрес пространства памяти должен быть выделен с буфером в 4 байта.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1054">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="95fd7-1055">**crypto_metadata_size**: размер области crypto_metadata в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1055">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="95fd7-1056">Для SHA256 размер метаданных должен быть равен *sizeof(NX_CRYPTO_SHA256)* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-1056">For SHA256, the metadata size must be *sizeof(NX_CRYPTO_SHA256)*</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-1057">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-1057">Return Values</span></span>

- <span data-ttu-id="95fd7-1058">**NX_CRYPTO_SUCCESS** (0X00): блок управления SHA256 успешно инициализирован с заданными ключом и размером ключа.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1058">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the SHA256 control block with the key and key size.</span></span>
- <span data-ttu-id="95fd7-1059">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1059">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="95fd7-1060">**NX_PTR_ERROR (0x07)** : недопустимый указатель на ключ, недопустимое значение crypto_metadata или crypto_metadata_size либо при выделении области crypto_metadata не был задан буфер в 4 байта.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1060">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_sha256_operation"></a><span data-ttu-id="95fd7-1061">_nx_crypto_method_sha256_operation</span><span class="sxs-lookup"><span data-stu-id="95fd7-1061">_nx_crypto_method_sha256_operation</span></span>

<span data-ttu-id="95fd7-1062">Выполнение хэш-операции SHA256.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1062">Perform SHA256 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-1063">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-1063">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="95fd7-1064">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-1064">Description</span></span>

<span data-ttu-id="95fd7-1065">Эта функция выполняет хэш-операцию SHA256.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1065">This function performs SHA256 hash operation.</span></span> <span data-ttu-id="95fd7-1066">Блок управления SHA256 должен быть инициализирован с помощью службы _ ***nx_crypto_method_sha256_init()***.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1066">The SHA256 control block must have been initialized with _ ***nx_crypto_method_sha256_init()***.</span></span> <span data-ttu-id="95fd7-1067">Выполняемый алгоритм SHA256 основан на алгоритме, указанном в блоке управления *method*.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1067">The SHA256 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="95fd7-1068">Для последней операции *NX_CRYPTO_HASH_CALCULATE* размер выходного буфера должен составлять 32 байта для SHA256 или 28 байт для SHA224.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1068">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 32 bytes for SHA256, or 28 bytes for SHA224.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-1069">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-1069">Parameters</span></span>

- <span data-ttu-id="95fd7-1070">**op**: тип выполняемой операции.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1070">**op** Type of operation to perform.</span></span> <span data-ttu-id="95fd7-1071">Допустимые операции:</span><span class="sxs-lookup"><span data-stu-id="95fd7-1071">Valid operation is:</span></span>
  - <span data-ttu-id="95fd7-1072">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="95fd7-1072">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="95fd7-1073">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="95fd7-1073">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="95fd7-1074">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="95fd7-1074">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="95fd7-1075">**handle**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1075">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-1076">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1076">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="95fd7-1077">**method**: указатель на допустимый метод шифрования SHA256.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1077">**method** Pointer to the valid SHA256 crypto method.</span></span> <span data-ttu-id="95fd7-1078">Используемый здесь метод шифрования должен совпадать с методом, указанным в _ *nx_crypto_method_sha256_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-1078">The crypto method used here must be the same used in the _ *nx_crypto_method_sha256_init().*</span></span>
- <span data-ttu-id="95fd7-1079">**input_data**: указывает на буфер, содержащий входные текстовые данные.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1079">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="95fd7-1080">Ограничения для входного буфера отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1080">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="95fd7-1081">**input_data_size**: размер входных данных в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1081">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="95fd7-1082">**iv_ptr**: это поле не используется для SHA256.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1082">**iv_ptr** This field is not used for SHA256.</span></span>
- <span data-ttu-id="95fd7-1083">**iv_size**: это поле не используется для SHA256.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1083">**iv_size** This field is not used for SHA256.</span></span>
- <span data-ttu-id="95fd7-1084">**output_buffer**: указатель на область памяти для созданного SHA256 хэша.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1084">**output_buffer** Pointer to the memory area for the generated SHA256 hash.</span></span>
- <span data-ttu-id="95fd7-1085">**output_buffer_size**: размер выходного буфера в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1085">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="95fd7-1086">Для SHA256 размер буфера должен составлять 32 байта.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1086">For SHA256 the buffer size must be 32 bytes.</span></span> <span data-ttu-id="95fd7-1087">Для SHA224 размер буфера должен составлять 28 байт.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1087">For SHA224 the buffer size must be 28 bytes.</span></span>
- <span data-ttu-id="95fd7-1088">**crypto_metadata**: указатель на блок управления SHA2, используемый в *_nx_crypto_method_sha2_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-1088">**crypto_metadata** Pointer to the SHA2 control block used in *_nx_crypto_method_sha2_init()*.</span></span>
- <span data-ttu-id="95fd7-1089">**crypto_metadata_size**: размер области crypto_metadata в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1089">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="95fd7-1090">Для SHA256 размер метаданных должен быть равен *sizeof(NX_CRYPTO_SHA256)* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-1090">For SHA256, the metadata size must *sizeof(NX_CRYPTO_SHA256)*</span></span>
- <span data-ttu-id="95fd7-1091">**packet_ptr**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1091">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-1092">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1092">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="95fd7-1093">**nx_crypto_hw_process_callback**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1093">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-1094">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1094">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-1095">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-1095">Return Values</span></span>

- <span data-ttu-id="95fd7-1096">**NX_CRYPTO_SUCCESS** (0X00): операция SHA256 успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1096">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the SHA256 operation.</span></span>
- <span data-ttu-id="95fd7-1097">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1097">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="95fd7-1098">**NX_PTR_ERROR** (0x07): недопустимый указатель ввода или длина.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1098">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="95fd7-1099">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004): указан недопустимый алгоритм SHA256.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1099">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid SHA256 algorithm being specified.</span></span>
- <span data-ttu-id="95fd7-1100">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005): недопустимый размер выходного буфера.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1100">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_sha256_cleanup"></a><span data-ttu-id="95fd7-1101">_nx_crypto_method_sha256_cleanup</span><span class="sxs-lookup"><span data-stu-id="95fd7-1101">_nx_crypto_method_sha256_cleanup</span></span>

<span data-ttu-id="95fd7-1102">Очистка блока управления SHA256.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1102">Clean up the SHA256 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-1103">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-1103">Prototype</span></span>

```c
UINT _nx_crypto_method_sha256_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="95fd7-1104">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-1104">Description</span></span>

<span data-ttu-id="95fd7-1105">Приложение вызывает эту функцию для очистки блока управления SHA256 после того, как определит, что этот сеанс SHA256 больше не требуется.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1105">Application calls this function to clean up the SHA256 control block after it determines this SHA256 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-1106">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-1106">Parameters</span></span>

- <span data-ttu-id="95fd7-1107">**crypto_metadata**: указатель на блок управления SHA256, используемый в *_nx_crypto_method_sha256_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-1107">**crypto_metadata** Pointer to the SHA256 control block used in *_nx_crypto_method_sha256_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-1108">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-1108">Return Values</span></span>

- <span data-ttu-id="95fd7-1109">**NX_CRYPTO_SUCCESS** (0X00): сеанс SHA256 успешно очищен.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1109">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the SHA256 session.</span></span>
- <span data-ttu-id="95fd7-1110">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1110">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_sha512_init"></a><span data-ttu-id="95fd7-1111">_nx_crypto_method_sha512_init</span><span class="sxs-lookup"><span data-stu-id="95fd7-1111">_nx_crypto_method_sha512_init</span></span>

<span data-ttu-id="95fd7-1112">Инициализация блока управления шифрованием SHA512.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1112">Initializes the SHA512 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-1113">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-1113">Prototype</span></span>

```c
UINT _nx_crypto_method_sha512_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="95fd7-1114">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-1114">Description</span></span>

<span data-ttu-id="95fd7-1115">Эта функция инициализирует блок управления SHA512 с заданной строкой ключа.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1115">This function initializes the SHA512 control block with the given key string.</span></span> <span data-ttu-id="95fd7-1116">После инициализации блока управления SHA512 последующая операция SHA512 должна использовать этот же блок управления.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1116">Once the SHA512 control block is initialized, subsequent SHA512 operation shall be using the same control block.</span></span>

<span data-ttu-id="95fd7-1117">Приложение может создать несколько блоков управления SHA512, представляющих отдельные сеансы.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1117">Application may create multiple SHA512 control blocks, each represents a session.</span></span> <span data-ttu-id="95fd7-1118">Инициализация блока управления SHA512 запускает новый сеанс вычисления хэша.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1118">Initializing the SHA512 control block starts a new hash computation session.</span></span> <span data-ttu-id="95fd7-1119">Повторная инициализация блока управления SHA512 прекращает текущий сеанс и запускает новый.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1119">Re-initializing the SHA512 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-1120">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-1120">Parameters</span></span>

- <span data-ttu-id="95fd7-1121">**method**: указатель на допустимый блок управления методом шифрования SHA512.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1121">**method** Pointer to a valid SHA512 crypto method control block.</span></span> <span data-ttu-id="95fd7-1122">Доступны следующие стандартные методы шифрования:</span><span class="sxs-lookup"><span data-stu-id="95fd7-1122">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="95fd7-1123">*crypto_method_sha512*</span><span class="sxs-lookup"><span data-stu-id="95fd7-1123">*crypto_method_sha512*</span></span>
  - <span data-ttu-id="95fd7-1124">*crypto_method_sha384*</span><span class="sxs-lookup"><span data-stu-id="95fd7-1124">*crypto_method_sha384*</span></span>
- <span data-ttu-id="95fd7-1125">**key**: это поле не используется для SHA512.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1125">**key** This field is not used for SHA512.</span></span>
- <span data-ttu-id="95fd7-1126">**key_size_in_bits**: это поле не используется для SHA512.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1126">**key_size_in_bits** This field is not used for SHA512</span></span>
- <span data-ttu-id="95fd7-1127">**handle**: эта служба возвращает дескриптор вызывающей стороне.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1127">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="95fd7-1128">Этот дескриптор зависит от конкретной реализации и в данной реализации не используется.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1128">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="95fd7-1129">Приложение должно передать значение NULL для этого дескриптора.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1129">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="95fd7-1130">**crypto_metadata**: указатель на допустимое пространство памяти для блока управления SHA512.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1130">**crypto_metadata** Pointer to a valid memory space for the SHA512 control block.</span></span> <span data-ttu-id="95fd7-1131">Начальный адрес пространства памяти должен быть выделен с буфером в 4 байта.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1131">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="95fd7-1132">**crypto_metadata_size**: размер области crypto_metadata в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1132">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="95fd7-1133">Для SHA512 размер метаданных должен быть равен *sizeof(NX_CRYPTO_SHA512)* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-1133">For SHA512, the metadata size must be *sizeof(NX_CRYPTO_SHA512)*</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-1134">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-1134">Return Values</span></span>

- <span data-ttu-id="95fd7-1135">**NX_CRYPTO_SUCCESS** (0X00): блок управления SHA512 успешно инициализирован с заданными ключом и размером ключа.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1135">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the SHA512 control block with the key and key size.</span></span>
- <span data-ttu-id="95fd7-1136">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1136">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="95fd7-1137">**NX_PTR_ERROR (0x07)** : недопустимый указатель на ключ, недопустимое значение crypto_metadata или crypto_metadata_size либо при выделении области crypto_metadata не был задан буфер в 4 байта.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1137">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_sha512_operation"></a><span data-ttu-id="95fd7-1138">_nx_crypto_method_sha512_operation</span><span class="sxs-lookup"><span data-stu-id="95fd7-1138">_nx_crypto_method_sha512_operation</span></span>

<span data-ttu-id="95fd7-1139">Выполнение хэш-операции SHA512.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1139">Perform SHA512 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-1140">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-1140">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="95fd7-1141">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-1141">Description</span></span>

<span data-ttu-id="95fd7-1142">Эта функция выполняет хэш-операцию SHA512.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1142">This function performs SHA512 hash operation.</span></span> <span data-ttu-id="95fd7-1143">Блок управления SHA512 должен быть инициализирован с помощью службы _ *nx_crypto_method_sha512_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-1143">The SHA512 control block must have been initialized with _ *nx_crypto_method_sha512_init()*.</span></span> <span data-ttu-id="95fd7-1144">Выполняемый алгоритм SHA512 основан на алгоритме, указанном в блоке управления *method*.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1144">The SHA512 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="95fd7-1145">Для последней операции *NX_CRYPTO_HASH_CALCULATE* размер выходного буфера должен составлять 64 байта для SHA512 или 48 байт для SHA384.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1145">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 64 bytes for SHA512, or 48 bytes for SHA384.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-1146">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-1146">Parameters</span></span>

- <span data-ttu-id="95fd7-1147">**op**: тип выполняемой операции.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1147">**op** Type of operation to perform.</span></span> <span data-ttu-id="95fd7-1148">Допустимые операции:</span><span class="sxs-lookup"><span data-stu-id="95fd7-1148">Valid operation is:</span></span>
  - <span data-ttu-id="95fd7-1149">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="95fd7-1149">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="95fd7-1150">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="95fd7-1150">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="95fd7-1151">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="95fd7-1151">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="95fd7-1152">**handle**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1152">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-1153">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1153">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="95fd7-1154">**method**: указатель на допустимый метод шифрования SHA512.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1154">**method** Pointer to the valid SHA512 crypto method.</span></span> <span data-ttu-id="95fd7-1155">Используемый здесь метод шифрования должен совпадать с методом, указанным в _ *nx_crypto_method_sha512_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-1155">The crypto method used here must be the same used in the _ *nx_crypto_method_sha512_init().*</span></span>
- <span data-ttu-id="95fd7-1156">**input_data**: указывает на буфер, содержащий входные текстовые данные.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1156">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="95fd7-1157">Ограничения для входного буфера отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1157">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="95fd7-1158">**input_data_size**: размер входных данных в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1158">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="95fd7-1159">**iv_ptr**: это поле не используется для SHA512.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1159">**iv_ptr** This field is not used for SHA512.</span></span>
- <span data-ttu-id="95fd7-1160">**iv_size**: это поле не используется для SHA512.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1160">**iv_size** This field is not used for SHA512.</span></span>
- <span data-ttu-id="95fd7-1161">**output_buffer**: указатель на область памяти для созданного SHA512 хэша.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1161">**output_buffer** Pointer to the memory area for the generated SHA512 hash.</span></span>
- <span data-ttu-id="95fd7-1162">**output_buffer_size**: размер выходного буфера в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1162">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="95fd7-1163">Для SHA512 размер буфера должен составлять 64 байта.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1163">For SHA512 the buffer size must be 64 bytes.</span></span> <span data-ttu-id="95fd7-1164">Для SHA384 размер буфера должен составлять 48 байт.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1164">For SHA384 the buffer size must be 48 bytes.</span></span>
- <span data-ttu-id="95fd7-1165">**crypto_metadata**: указатель на блок управления SHA512, используемый в *_nx_crypto_method_sha512_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-1165">**crypto_metadata** Pointer to the SHA512 control block used in *_nx_crypto_method_sha512_init()*.</span></span>
- <span data-ttu-id="95fd7-1166">**crypto_metadata_size**: размер области crypto_metadata в байтах.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1166">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="95fd7-1167">Для SHA512 размер метаданных должен быть равен *sizeof(NX_CRYPTO_SHA512)* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-1167">For SHA512, the metadata size must *sizeof(NX_CRYPTO_SHA512)*</span></span>
- <span data-ttu-id="95fd7-1168">**packet_ptr**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1168">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-1169">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1169">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="95fd7-1170">**nx_crypto_hw_process_callback**: это поле не используется в программной реализации библиотеки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1170">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="95fd7-1171">Любые переданные в него значения автоматически игнорируются.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1171">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-1172">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-1172">Return Values</span></span>

- <span data-ttu-id="95fd7-1173">**NX_CRYPTO_SUCCESS** (0X00): операция SHA512 успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1173">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the SHA512 operation.</span></span>
- <span data-ttu-id="95fd7-1174">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1174">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="95fd7-1175">**NX_PTR_ERROR** (0x07): недопустимый указатель ввода или длина.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1175">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="95fd7-1176">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004): указан недопустимый алгоритм SHA512.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1176">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid SHA512 algorithm being specified.</span></span>
- <span data-ttu-id="95fd7-1177">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005): недопустимый размер выходного буфера.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1177">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_sha512_cleanup"></a><span data-ttu-id="95fd7-1178">_nx_crypto_method_sha512_cleanup</span><span class="sxs-lookup"><span data-stu-id="95fd7-1178">_nx_crypto_method_sha512_cleanup</span></span>

<span data-ttu-id="95fd7-1179">Очистка блока управления SHA512.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1179">Clean up the SHA512 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="95fd7-1180">Прототип</span><span class="sxs-lookup"><span data-stu-id="95fd7-1180">Prototype</span></span>

```c
UINT _nx_crypto_method_sha512_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="95fd7-1181">Описание</span><span class="sxs-lookup"><span data-stu-id="95fd7-1181">Description</span></span>

<span data-ttu-id="95fd7-1182">Приложение вызывает эту функцию для очистки блока управления SHA512 после того, как определит, что этот сеанс SHA512 больше не требуется.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1182">Application calls this function to clean up the SHA512 control block after it determines this SHA512 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="95fd7-1183">Параметры</span><span class="sxs-lookup"><span data-stu-id="95fd7-1183">Parameters</span></span>

- <span data-ttu-id="95fd7-1184">**crypto_metadata**: указатель на блок управления SHA512, используемый в *_nx_crypto_method_sha512_init()* .</span><span class="sxs-lookup"><span data-stu-id="95fd7-1184">**crypto_metadata** Pointer to the SHA512 control block used in *_nx_crypto_method_sha512_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="95fd7-1185">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="95fd7-1185">Return Values</span></span>

- <span data-ttu-id="95fd7-1186">**NX_CRYPTO_SUCCESS** (0X00): сеанс SHA512 успешно очищен.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1186">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the SHA512 session.</span></span>
- <span data-ttu-id="95fd7-1187">**NX_CRYPTO_INVALID_LIBRARY** (0x20001): библиотека шифрования находится в недопустимом состоянии и не может использоваться.</span><span class="sxs-lookup"><span data-stu-id="95fd7-1187">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>