---
title: Приложение B. Коды состояния DHCPv6-сервера NetX Duo для ОСРВ Azure
description: В этой главе приведено описание всех кодов состояния DHCPv6-сервера NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7c79a0c0bc9acfcfca69c7333d30cd7cab35ba5f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814759"
---
# <a name="appendix-b---azure-rtos-netx-duo-dhcpv6-server-status-codes"></a><span data-ttu-id="c4993-103">Приложение B. Коды состояния DHCPv6-сервера NetX Duo для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="c4993-103">Appendix B - Azure RTOS NetX Duo DHCPv6 server status codes</span></span>

| <span data-ttu-id="c4993-104">Имя</span><span class="sxs-lookup"><span data-stu-id="c4993-104">Name</span></span>              | <span data-ttu-id="c4993-105">Код</span><span class="sxs-lookup"><span data-stu-id="c4993-105">Code</span></span>            | <span data-ttu-id="c4993-106">Описание</span><span class="sxs-lookup"><span data-stu-id="c4993-106">Description</span></span> |
| ------------------- | ------------------- | --------------- |
| <span data-ttu-id="c4993-107">Успешно</span><span class="sxs-lookup"><span data-stu-id="c4993-107">Success</span></span> | <span data-ttu-id="c4993-108">0</span><span class="sxs-lookup"><span data-stu-id="c4993-108">0</span></span> | <span data-ttu-id="c4993-109">Успех</span><span class="sxs-lookup"><span data-stu-id="c4993-109">Success</span></span> |
| <span data-ttu-id="c4993-110">Неизвестный сбой</span><span class="sxs-lookup"><span data-stu-id="c4993-110">Unspecified Failure</span></span> | <span data-ttu-id="c4993-111">1</span><span class="sxs-lookup"><span data-stu-id="c4993-111">1</span></span> | <span data-ttu-id="c4993-112">Сбой, причина не указана. Этот код состояния задается сервером для указания на общий сбой, которому не соответствуют другие коды, при предоставлении запроса клиента.</span><span class="sxs-lookup"><span data-stu-id="c4993-112">Failure, reason unspecified; this status code is set by the Server to indicate a general failure in granting the Client request not matching the other codes</span></span> |
| <span data-ttu-id="c4993-113">Адрес недоступен</span><span class="sxs-lookup"><span data-stu-id="c4993-113">NoAddress Available</span></span> | <span data-ttu-id="c4993-114">2</span><span class="sxs-lookup"><span data-stu-id="c4993-114">2</span></span> | <span data-ttu-id="c4993-115">У сервера нет доступных адресов для назначения клиенту</span><span class="sxs-lookup"><span data-stu-id="c4993-115">Server has no addresses available to assign to the Client</span></span> |
| <span data-ttu-id="c4993-116">NoBinding</span><span class="sxs-lookup"><span data-stu-id="c4993-116">NoBinding</span></span> | <span data-ttu-id="c4993-117">3</span><span class="sxs-lookup"><span data-stu-id="c4993-117">3</span></span> | <span data-ttu-id="c4993-118">Адрес IA клиента (привязка) недоступен. Например, запрошенный IP-адрес не может быть выдан сервером в аренду либо он назначен другому клиенту.</span><span class="sxs-lookup"><span data-stu-id="c4993-118">Client IA address (binding) is not available e.g. the requested IP address is not available for the Server to lease or assigned to another Client.</span></span> |
| <span data-ttu-id="c4993-119">NotOnLink</span><span class="sxs-lookup"><span data-stu-id="c4993-119">NotOnLink</span></span> | <span data-ttu-id="c4993-120">4</span><span class="sxs-lookup"><span data-stu-id="c4993-120">4</span></span> | <span data-ttu-id="c4993-121">Префикс адреса указывает на то, что IP-адрес не является связанным.</span><span class="sxs-lookup"><span data-stu-id="c4993-121">The prefix for the address indicates the IP address is not an on link address</span></span> |
| <span data-ttu-id="c4993-122">UseMulticast</span><span class="sxs-lookup"><span data-stu-id="c4993-122">UseMulticast</span></span> | <span data-ttu-id="c4993-123">5</span><span class="sxs-lookup"><span data-stu-id="c4993-123">5</span></span> | <span data-ttu-id="c4993-124">Отправляется сервером в ответ на сообщение клиента, полученное по адресу сервера для одноадресного взаимодействия, а не многоадресного (*All_DHCP_Relay_Agents_and_Servers*).</span><span class="sxs-lookup"><span data-stu-id="c4993-124">Sent by a Server in response to receiving a Client message using the Server’s unicast address instead of the *All_DHCP_Relay_Agents_and_Servers* multicast address</span></span> |