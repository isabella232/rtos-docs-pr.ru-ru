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
# <a name="appendix-a---azure-rtos-netx-duo-sntp-fatal-error-codes"></a>Приложение A. Коды неустранимых ошибок SNTP NetX Duo для ОСРВ Azure

Следующие коды ошибок приведут к тому, что клиент SNTP NetX Duo для ОСРВ Azure прервет временные обновления с текущим сервером. Приложение должно решить, следует ли удалить сервер из списка доступных серверов клиента SNTP или просто переключиться на следующий доступный сервер в списке. Определение каждого состояния ошибки определено в файле *nxd_sntp_client.h. *

Когда клиент SNTP возвращает ошибку из приведенного ниже списка в приложение, сервер, возможно, будет заменен другим сервером. Обратите внимание, что состояние ошибки NX_SNTP_KOD_REMOVE_SERVER требует от клиента SNTP установки обработчика (функции обратного вызова) пакета "Kiss-of-Death":

- NX_SNTP_KOD_REMOVE_SERVER 0xD0C  
- NX_SNTP_SERVER_AUTH_FAIL 0xD0D  
- NX_SNTP_INVALID_NTP_VERSION 0xD11  
- NX_SNTP_INVALID_SERVER_MODE 0xD12  
- NX_SNTP_INVALID_SERVER_STRATUM 0xD15  

Когда клиент SNTP возвращает приложению ошибку из приведенного ниже списка, сервер может только временно не иметь возможности предоставлять действительные обновления времени и его не нужно удалять:

- HNX_SNTP_NO_UNICAST_FROM_SERVER 0xD09  
- NX_SNTP_SERVER_CLOCK_NOT_SYNC 0xD0A  
- NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD0B  
- NX_SNTP_OVER_BAD_UPDATE_LIMIT 0xD17  
- NX_SNTP_BAD_SERVER_ROOT_DISPERSION 0xD16  
- NX_SNTP_INVALID_RTT_TIME 0xD21  
- NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD24