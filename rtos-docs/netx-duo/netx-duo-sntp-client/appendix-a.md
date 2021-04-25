---
title: Приложение A. Коды неустранимых ошибок SNTP NetX Duo для ОСРВ Azure
description: Следующие коды ошибок приведут к тому, что клиент SNTP NetX Duo для ОСРВ Azure прервет временные обновления с текущим сервером.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 065e7a3e65b3cf8d7fcfb34bb9568a673791609a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814560"
---
# <a name="appendix-a---azure-rtos-netx-duo-sntp-fatal-error-codes"></a><span data-ttu-id="de906-103">Приложение A. Коды неустранимых ошибок SNTP NetX Duo для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="de906-103">Appendix A - Azure RTOS NetX Duo SNTP Fatal Error Codes</span></span>

<span data-ttu-id="de906-104">Следующие коды ошибок приведут к тому, что клиент SNTP NetX Duo для ОСРВ Azure прервет временные обновления с текущим сервером.</span><span class="sxs-lookup"><span data-stu-id="de906-104">The following error codes will result in the Azure RTOS NetX Duo SNTP Client aborting time updates with the current server.</span></span> <span data-ttu-id="de906-105">Приложение должно решить, следует ли удалить сервер из списка доступных серверов клиента SNTP или просто переключиться на следующий доступный сервер в списке.</span><span class="sxs-lookup"><span data-stu-id="de906-105">It is up to the application to decide if the server should be removed from the SNTP Client list of available servers, or simply switch to the next available server on the list.</span></span> <span data-ttu-id="de906-106">Определение каждого состояния ошибки определено в файле \*nxd_sntp_client.h.</span><span class="sxs-lookup"><span data-stu-id="de906-106">The definition of each error status is defined in \*nxd_sntp_client.h.</span></span> *

<span data-ttu-id="de906-107">Когда клиент SNTP возвращает ошибку из приведенного ниже списка в приложение, сервер, возможно, будет заменен другим сервером.</span><span class="sxs-lookup"><span data-stu-id="de906-107">When the SNTP Client returns an error from the list below to the application, the Server should probably be replaced with another Server.</span></span> <span data-ttu-id="de906-108">Обратите внимание, что состояние ошибки NX_SNTP_KOD_REMOVE_SERVER требует от клиента SNTP установки обработчика (функции обратного вызова) пакета "Kiss-of-Death":</span><span class="sxs-lookup"><span data-stu-id="de906-108">Note that the NX_SNTP_KOD_REMOVE_SERVER error status is left to the SNTP Client kiss of death handler (callback function) to set:</span></span>

- <span data-ttu-id="de906-109">NX_SNTP_KOD_REMOVE_SERVER 0xD0C</span><span class="sxs-lookup"><span data-stu-id="de906-109">NX_SNTP_KOD_REMOVE_SERVER 0xD0C</span></span>  
- <span data-ttu-id="de906-110">NX_SNTP_SERVER_AUTH_FAIL 0xD0D</span><span class="sxs-lookup"><span data-stu-id="de906-110">NX_SNTP_SERVER_AUTH_FAIL 0xD0D</span></span>  
- <span data-ttu-id="de906-111">NX_SNTP_INVALID_NTP_VERSION 0xD11</span><span class="sxs-lookup"><span data-stu-id="de906-111">NX_SNTP_INVALID_NTP_VERSION 0xD11</span></span>  
- <span data-ttu-id="de906-112">NX_SNTP_INVALID_SERVER_MODE 0xD12</span><span class="sxs-lookup"><span data-stu-id="de906-112">NX_SNTP_INVALID_SERVER_MODE 0xD12</span></span>  
- <span data-ttu-id="de906-113">NX_SNTP_INVALID_SERVER_STRATUM 0xD15</span><span class="sxs-lookup"><span data-stu-id="de906-113">NX_SNTP_INVALID_SERVER_STRATUM 0xD15</span></span>  

<span data-ttu-id="de906-114">Когда клиент SNTP возвращает приложению ошибку из приведенного ниже списка, сервер может только временно не иметь возможности предоставлять действительные обновления времени и его не нужно удалять:</span><span class="sxs-lookup"><span data-stu-id="de906-114">When the SNTP Client returns an error from the list below to the application, the Server may only temporarily be unable to provide valid time updates and need not be removed:</span></span>

- <span data-ttu-id="de906-115">HNX_SNTP_NO_UNICAST_FROM_SERVER 0xD09</span><span class="sxs-lookup"><span data-stu-id="de906-115">HNX_SNTP_NO_UNICAST_FROM_SERVER 0xD09</span></span>  
- <span data-ttu-id="de906-116">NX_SNTP_SERVER_CLOCK_NOT_SYNC 0xD0A</span><span class="sxs-lookup"><span data-stu-id="de906-116">NX_SNTP_SERVER_CLOCK_NOT_SYNC 0xD0A</span></span>  
- <span data-ttu-id="de906-117">NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD0B</span><span class="sxs-lookup"><span data-stu-id="de906-117">NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD0B</span></span>  
- <span data-ttu-id="de906-118">NX_SNTP_OVER_BAD_UPDATE_LIMIT 0xD17</span><span class="sxs-lookup"><span data-stu-id="de906-118">NX_SNTP_OVER_BAD_UPDATE_LIMIT 0xD17</span></span>  
- <span data-ttu-id="de906-119">NX_SNTP_BAD_SERVER_ROOT_DISPERSION 0xD16</span><span class="sxs-lookup"><span data-stu-id="de906-119">NX_SNTP_BAD_SERVER_ROOT_DISPERSION 0xD16</span></span>  
- <span data-ttu-id="de906-120">NX_SNTP_INVALID_RTT_TIME 0xD21</span><span class="sxs-lookup"><span data-stu-id="de906-120">NX_SNTP_INVALID_RTT_TIME 0xD21</span></span>  
- <span data-ttu-id="de906-121">NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD24</span><span class="sxs-lookup"><span data-stu-id="de906-121">NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD24</span></span>