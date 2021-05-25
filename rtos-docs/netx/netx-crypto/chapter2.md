---
title: Глава 2. Установка и использование ОСРВ Azure NetX Crypto
description: В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента NetX Crypto.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cd736cf6bbe15e1f407d1812072a4308435c8007
ms.sourcegitcommit: c2f5da5d6c7b230799f8fbd77885e9940acfbab4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/21/2021
ms.locfileid: "110236158"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-crypto"></a><span data-ttu-id="620c9-103">Глава 2. Установка и использование ОСРВ Azure NetX Crypto</span><span class="sxs-lookup"><span data-stu-id="620c9-103">Chapter 2 - Installation and use of Azure RTOS NetX Crypto</span></span>

<span data-ttu-id="620c9-104">В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента ОСРВ Azure NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="620c9-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Crypto component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="620c9-105">Распространение продукта</span><span class="sxs-lookup"><span data-stu-id="620c9-105">Product Distribution</span></span>

<span data-ttu-id="620c9-106">Компонент ОСРВ Azure NetX Crypto доступен по адресу [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span><span class="sxs-lookup"><span data-stu-id="620c9-106">Azure RTOS NetX Crypto is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="620c9-107">Он содержит файлы исходного кода, включаемые файлы и PDF-файл, содержащий этот документ:</span><span class="sxs-lookup"><span data-stu-id="620c9-107">The package includes source files, include files, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="620c9-108">**nx_crypto.h**: файл заголовка общедоступного API модуля NetX Crypto;</span><span class="sxs-lookup"><span data-stu-id="620c9-108">**nx_crypto.h**: Public API header file NetX Crypto module</span></span>
- <span data-ttu-id="620c9-109">**nx_crypto_\*.c/h**: файлы исходного кода C/H для NetX Crypto;</span><span class="sxs-lookup"><span data-stu-id="620c9-109">**nx_crypto_\*.c/h**: C/H Source files for NetX Crypto</span></span>
- <span data-ttu-id="620c9-110">**nx_port.h**: файл заголовка C, содержащий все определения и структуры данных для инструментов разработки и целевых платформ;</span><span class="sxs-lookup"><span data-stu-id="620c9-110">**nx_crypto_port.h**: C header file containing all development-tool and target specific data definitions and structures.</span></span>
- <span data-ttu-id="620c9-111">**NetX_Crypto_User_Guide.pdf**: PDF-файл с описанием модуля NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="620c9-111">**NetX_Crypto_User_Guide.pdf**: PDF description of NetX Crypto Module.</span></span>

## <a name="netx-crypto-installation"></a><span data-ttu-id="620c9-112">Установка NetX Crypto</span><span class="sxs-lookup"><span data-stu-id="620c9-112">NetX Crypto Installation</span></span>

<span data-ttu-id="620c9-113">Все ранее упомянутые дистрибутивы доступны в каталоге **crypto_libraries**, который находится на корневом уровне репозитория NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="620c9-113">The entire distribution mentioned previously is available in **crypto_libraries** directory, present at root level of NetX Duo repository.</span></span>

<span data-ttu-id="620c9-114">Чтобы использовать NetX Crypto, весь дистрибутив, упомянутый ранее, должен быть скопирован в каталог, где установлен экземпляр NetX.</span><span class="sxs-lookup"><span data-stu-id="620c9-114">In order to use NetX Crypto, the entire distribution mentioned previously should be copied to the same directory level where NetX is installed.</span></span> <span data-ttu-id="620c9-115">Например, если экземпляр NetX установлен в каталоге \threadx\arm7\NetX, то каталоги nx_crypto *.*</span><span class="sxs-lookup"><span data-stu-id="620c9-115">For example, if NetX is installed in the directory "\threadx\arm7\NetX" then the nx_crypto *.*</span></span> <span data-ttu-id="620c9-116">должны быть скопированы в \threadx\arm7\NetXCrypto.</span><span class="sxs-lookup"><span data-stu-id="620c9-116">directories should be copied into "\threadx\arm7\NetXCrypto".</span></span>

<span data-ttu-id="620c9-117">Чтобы использовать NetX Crypto в изолированном режиме, необходимо скопировать в проект приложения весь дистрибутив, упомянутый выше.</span><span class="sxs-lookup"><span data-stu-id="620c9-117">For NetX Crypto to be used in standalone mode, the entire distribution mentioned previously should be copied to the application project.</span></span> <span data-ttu-id="620c9-118">Например, следует скопировать в проект приложения каталог **crypto_libraries** или создать проект библиотеки с каталогом **crypto_libraries**, а затем связать ее с проектом приложения.</span><span class="sxs-lookup"><span data-stu-id="620c9-118">For example **crypto_libraries** directory should be copied to the application project or a library project with **crypto_libraries** directory should be created and linked to the application project.</span></span> 

## <a name="using-netx-crypto"></a><span data-ttu-id="620c9-119">Использование NetX Crypto</span><span class="sxs-lookup"><span data-stu-id="620c9-119">Using NetX Crypto</span></span>

<span data-ttu-id="620c9-120">Статья описывает установку, настройку и использование компонента NetX Crypto для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="620c9-120">This chapter describes installation, setup, and usage of the Azure RTOS NetX Crypto component.</span></span> <span data-ttu-id="620c9-121">Проще говоря, код приложения должен включать в себя *nx_crypto.h*.</span><span class="sxs-lookup"><span data-stu-id="620c9-121">Basically, the application code must include the *nx_crypto.h*.</span></span>  <span data-ttu-id="620c9-122">После добавления файла *nx_crypto.h* код приложения сможет выполнять вызовы функций NetX Crypto, описанных далее в этом руководстве.</span><span class="sxs-lookup"><span data-stu-id="620c9-122">Once *nx_crypto.h* is included, the application code is then able to make the NetX Crypto function calls specified later in this guide.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="620c9-123">Параметры конфигурации</span><span class="sxs-lookup"><span data-stu-id="620c9-123">Configuration Options</span></span>

<span data-ttu-id="620c9-124">Существует ряд параметров конфигурации для сборки NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="620c9-124">There are several configuration options for building NetX Crypto.</span></span> <span data-ttu-id="620c9-125">Ниже приведен список всех параметров с подробным описанием каждого из них.</span><span class="sxs-lookup"><span data-stu-id="620c9-125">Following is a list of all options, where each is described in detail:</span></span>

- <span data-ttu-id="620c9-126">**NX_CRYPTO_MAX_RSA_MODULUS_SIZE**: если этот параметр определен, он задает максимальный ожидаемый размер модуля RSA в битах.</span><span class="sxs-lookup"><span data-stu-id="620c9-126">**NX_CRYPTO_MAX_RSA_MODULUS_SIZE**: Defined, this option gives the maximum RSA modulus expected, in bits.</span></span> <span data-ttu-id="620c9-127">Значение по умолчанию — 4096 для 4096-разрядных модулей.</span><span class="sxs-lookup"><span data-stu-id="620c9-127">The default value is 4096 for a 4096-bit modulus.</span></span> <span data-ttu-id="620c9-128">Другие возможные значения: 3072, 2048 или 1024 (не рекомендуется).</span><span class="sxs-lookup"><span data-stu-id="620c9-128">Other values can be 3072, 2048, or 1024 (not recommended).</span></span>
- <span data-ttu-id="620c9-129">**NX_CRYPTO_SELF_TEST**: если этот параметр определен, он активирует для модуля NetX Crypto автоматические тесты.</span><span class="sxs-lookup"><span data-stu-id="620c9-129">**NX_CRYPTO_SELF_TEST**: Defined, enables self tests for NetX Crypto module.</span></span> <span data-ttu-id="620c9-130">Символ **NX_CRYPTO_FIPS** теперь является нерекомендуемым, и он переименован в **NX_CRYPTO_SELF_TEST**.</span><span class="sxs-lookup"><span data-stu-id="620c9-130">**NX_CRYPTO_FIPS** symbol is now deprecated and renamed to **NX_CRYPTO_SELF_TEST**</span></span>
- <span data-ttu-id="620c9-131">**NX_CRYPTO_STANDALONE_ENABLE**: если этот параметр определен, он позволяет использовать NetX Crypto в изолированном режиме (без ОСРВ Azure).</span><span class="sxs-lookup"><span data-stu-id="620c9-131">**NX_CRYPTO_STANDALONE_ENABLE**: Defined enables NetX Crypto to be used in standalone mode (without Azure RTOS).</span></span> <span data-ttu-id="620c9-132">По умолчанию этот символ не определен.</span><span class="sxs-lookup"><span data-stu-id="620c9-132">By default this symbol is not defined.</span></span>
