---
title: Приложение A. Коды неустранимых ошибок SNTP NetX Duo для ОСРВ Azure
description: Следующие коды ошибок приведут к тому, что клиент SNTP NetX Duo для ОСРВ Azure прервет временные обновления с текущим сервером.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e0152c1342b3edffd42f7442c51e7c5d62b199a5b38085dac06b4c0dbee9e9a8
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790111"
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