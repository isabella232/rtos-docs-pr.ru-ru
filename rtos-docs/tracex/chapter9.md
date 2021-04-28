---
title: Глава 9. События трассировки USBX в ОСРВ Azure
description: В этой главе содержится описание событий USBX в Azure ОСРВ, отображаемых в TraceX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 98561fe1d131e1d1b0893b7d89eb720881a82ac8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104816287"
---
# <a name="chapter-9---azure-rtos-usbx-trace-events"></a><span data-ttu-id="4c86d-103">Глава 9. События трассировки USBX в ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="4c86d-103">Chapter 9 - Azure RTOS USBX trace events</span></span>

<span data-ttu-id="4c86d-104">В этой главе содержится описание событий USBX в Azure ОСРВ, отображаемых в TraceX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-104">This chapter contains a description of the Azure RTOS USBX events displayed by TraceX.</span></span> 

## <a name="list-of-events-and-icons"></a><span data-ttu-id="4c86d-105">Список событий и значков</span><span class="sxs-lookup"><span data-stu-id="4c86d-105">List of Events and Icons</span></span>

<span data-ttu-id="4c86d-106">Ниже приведен список событий USBX, отображаемых в TraceX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-106">The following is a list of USBX events displayed by TraceX.</span></span>

| <span data-ttu-id="4c86d-107">Значок</span><span class="sxs-lookup"><span data-stu-id="4c86d-107">Icon</span></span>                             | <span data-ttu-id="4c86d-108">Значение</span><span class="sxs-lookup"><span data-stu-id="4c86d-108">Meaning</span></span>                               |
| -------------------------------- | ------------------------------------- |
| ![Значок активации класса CDC устройства](./media/user-guide/usbx-events/image1.png)    | <span data-ttu-id="4c86d-110">**Активация класса CDC устройства** *(ux_device_class_cdc_activate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-110">**Device Class Cdc Activate** *(ux_device_class_cdc_activate)*</span></span> |
| ![Значок деактивации класса CDC устройства](./media/user-guide/usbx-events/image2.png)    | <span data-ttu-id="4c86d-112">**Деактивация класса CDC устройства** *(ux_device_class_cdc_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-112">**Device Class Cdc Deactivate** *(ux_device_class_cdc_deactivate)*</span></span> |
| ![Значок считывания класса CDC устройства](./media/user-guide/usbx-events/image3.png)    | <span data-ttu-id="4c86d-114">**Считывание класса CDC устройства** *(ux_device_class_cdc_read)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-114">**Device Class Cdc Read** *(ux_device_class_cdc_read)*</span></span> |
| ![Значок записи класса CDC устройства](./media/user-guide/usbx-events/image4.png)    | <span data-ttu-id="4c86d-116">**Запись класса CDC устройства** *(ux_device_class_cdc_write)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-116">**Device Class Cdc Write** *(ux_device_class_cdc_write)*</span></span> |
| ![Значок активации класса Dpump устройства](./media/user-guide/usbx-events/image5.png)    | <span data-ttu-id="4c86d-118">**Активация класса Dpump устройства** *(ux_device_class_dpump_activate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-118">**Device Class Dpump Activate** *(ux_device_class_dpump_activate)*</span></span> |
| ![Значок деактивации класса Dpump устройства](./media/user-guide/usbx-events/image6.png)    | <span data-ttu-id="4c86d-120">**Деактивация класса Dpump устройства** *(ux_device_class_dpump_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-120">**Device Class Dpump Deactivate** *(ux_device_class_dpump_deactivate)*</span></span> |
| ![Значок считывания класса Dpump устройства](./media/user-guide/usbx-events/image7.png)    | <span data-ttu-id="4c86d-122">**Считывание класса Dpump устройства** *(ux_device_class_dpump_read)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-122">**Device Class Dpump Read** *(ux_device_class_dpump_read)*</span></span> |
| ![Значок записи класса Dpump устройства](./media/user-guide/usbx-events/image8.png)    | <span data-ttu-id="4c86d-124">**Запись класса Dpump устройства** *(ux_device_class_dpump_write)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-124">**Device Class Dpump Write** *(ux_device_class_dpump_write)*</span></span> |
| ![Значок активации класса Hid устройства](./media/user-guide/usbx-events/image9.png)    | <span data-ttu-id="4c86d-126">**Активация класса Hid устройства** *(ux_device_class_hid_activate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-126">**Device Class Hid Activate** *(ux_device_class_hid_activate)*</span></span> |
| ![Значок деактивации класса Hid устройства](./media/user-guide/usbx-events/image10.png)    | <span data-ttu-id="4c86d-128">**Деактивация класса Hid устройства** *(ux_device_class_hid_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-128">**Device Class Hid Deactivate** *(ux_device_class_hid_deactivate)*</span></span> |
| ![Значок отправки дескриптора класса Hid устройства](./media/user-guide/usbx-events/image11.png)    | <span data-ttu-id="4c86d-130">**Отправка дескриптора класса Hid устройства** *(ux_device_class_hid_descriptor_send)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-130">**Device Class Hid Descriptor Send** *(ux_device_class_hid_descriptor_send)*</span></span> |
| ![Значок получения события класса Hid устройства](./media/user-guide/usbx-events/image12.png)    | <span data-ttu-id="4c86d-132">**Получение события класса Hid устройства** *(ux_device_class_hid_event_get)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-132">**Device Class Hid Event Get** *(ux_device_class_hid_event_get)*</span></span> |
| ![Значок набора событий класса Hid устройства](./media/user-guide/usbx-events/image13.png)    | <span data-ttu-id="4c86d-134">**Набор событий класса Hid устройства** *(ux_device_class_hid_event_set)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-134">**Device Class Hid Event Set** *(ux_device_class_hid_event_set)*</span></span> |
| ![Значок получения отчета класса Hid устройства](./media/user-guide/usbx-events/image14.png)    | <span data-ttu-id="4c86d-136">**Получение отчета класса Hid устройства** *(ux_device_class_hid_report_get)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-136">**Device Class Hid Report Get** *(ux_device_class_hid_report_get)*</span></span> |
| ![Значок набора отчетов класса Hid устройства](./media/user-guide/usbx-events/image15.png)    | <span data-ttu-id="4c86d-138">**Набор отчетов класса Hid устройства** *(ux_device_class_hid_report_set)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-138">**Device Class Hid Report Set** *(ux_device_class_hid_report_set)*</span></span> |
| ![Значок активации класса Pima устройства](./media/user-guide/usbx-events/image16.png)    | <span data-ttu-id="4c86d-140">**Активация класса Pima устройства** *(ux_device_class_pima_activate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-140">**Device Class Pima Activate** *(ux_device_class_pima_activate)*</span></span> |
| ![Значок деактивации класса Pima устройства](./media/user-guide/usbx-events/image17.png)    | <span data-ttu-id="4c86d-142">**Деактивация класса Pima устройства** *(ux_device_class_pima_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-142">**Device Class Pima Deactivate** *(ux_device_class_pima_deactivate)*</span></span> |
| ![Значок отправки сведений о классе Pima устройства](./media/user-guide/usbx-events/image18.png)    | <span data-ttu-id="4c86d-144">**Отправка сведений о классе Pima устройства** *(ux_device_class_pima_device_info_send)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-144">**Device Class Pima Device Info Send** *(ux_device_class_pima_device_info_send)*</span></span> |
| ![Значок получения события класса Pima устройства](./media/user-guide/usbx-events/image19.png)    | <span data-ttu-id="4c86d-146">**Получение события класса Pima устройства** *(ux_device_class_pima_event_get)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-146">**Device Class Pima Event Get** *(ux_device_class_pima_event_get)*</span></span> |
| ![Значок набора событий класса Pima устройства](./media/user-guide/usbx-events/image20.png)    | <span data-ttu-id="4c86d-148">**Набор событий класса Pima устройства** *(ux_device_class_pima_event_set)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-148">**Device Class Pima Event Set** *(ux_device_class_pima_event_set)*</span></span> |
| ![Значок добавления объекта в класс Pima устройства](./media/user-guide/usbx-events/image21.png)    | <span data-ttu-id="4c86d-150">**Добавление объекта в класс Pima устройства** *(ux_device_class_pima_object_add)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-150">**Device Class Pima Object Add** *(ux_device_class_pima_object_add)*</span></span> |
| ![Значок получения данных объекта в классе Pima устройства](./media/user-guide/usbx-events/image22.png)    | <span data-ttu-id="4c86d-152">**Получение данных объекта в классе Pima устройства** *(ux_device_class_pima_object_data_get)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-152">**Device Class Pima Object Data Get** *(ux_device_class_pima_object_data_get)*</span></span> |
| ![Значок отправки данных объекта класса Pima устройства](./media/user-guide/usbx-events/image23.png)    | <span data-ttu-id="4c86d-154">**Отправка данных объекта класса Pima устройства** *(ux_device_class_pima_object_data_send)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-154">**Device Class Pima Object Data Send** *(ux_device_class_pima_object_data_send)*</span></span> |
| ![Значок удаления объекта из класса Pima устройства](./media/user-guide/usbx-events/image24.png)    | <span data-ttu-id="4c86d-156">**Удаление объекта из класса Pima устройства** *(ux_device_class_pima_object_delete)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-156">**Device Class Pima Object Delete** *(ux_device_class_pima_object_delete)*</span></span> |
| ![Значок отправки дескрипторов объекта класса Pima устройства](./media/user-guide/usbx-events/image25.png)    | <span data-ttu-id="4c86d-158">**Отправка дескрипторов объекта класса Pima устройства** *(ux_device_class_pima_object_handles_send)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-158">**Device Class Pima Object Handles Send** *(ux_device_class_pima_object_handles_send)*</span></span> |
| ![Значок получения сведений об объекте класса Pima устройства](./media/user-guide/usbx-events/image26.png)    | <span data-ttu-id="4c86d-160">**Получение сведений об объекте класса Pima устройства** *(ux_device_class_pima_object_info_get)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-160">**Device Class Pima Object Info Get** *(ux_device_class_pima_object_info_get)*</span></span> |
| ![Значок отправки сведений об объекте класса Pima устройства](./media/user-guide/usbx-events/image27.png)    | <span data-ttu-id="4c86d-162">**Отправка сведений об объекте класса Pima устройства** *(ux_device_class_pima_object_info_send)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-162">**Device Class Pima Object Info Send** *(ux_device_class_pima_object_info_send)*</span></span> |
| ![Значок отправки номера объекта класса Pima устройства](./media/user-guide/usbx-events/image28.png)    | <span data-ttu-id="4c86d-164">**Номер объекта класса Pima устройства** *(ux_device_class_pima_objects_number_send)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-164">**Device Class Pima Objects Number Send** *(ux_device_class_pima_objects_number_send)*</span></span> |
| ![Значок получения частичных данных об объекте класса Pima устройства](./media/user-guide/usbx-events/image29.png)    | <span data-ttu-id="4c86d-166">**Получение частичных данных об объекте класса Pima устройства** *(ux_device_class_pima_partial_object_data_get)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-166">**Device Class Pima Partial Object Data Get** *(ux_device_class_pima_partial_object_data_get)*</span></span> |
| ![Значок отправки ответа класса Pima устройства](./media/user-guide/usbx-events/image30.png)    | <span data-ttu-id="4c86d-168">**Отправка ответа класса Pima устройства** *(ux_device_class_pima_response_send)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-168">**Device Class Pima Response Send** *(ux_device_class_pima_response_send)*</span></span>|
| ![Значок отправки идентификатора хранилища класса Pima устройства](./media/user-guide/usbx-events/image31.png)    | <span data-ttu-id="4c86d-170">**Отправка идентификатора хранилища класса Pima устройства** *(ux_device_class_pima_storage_id_send)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-170">**Device Class Pima Storage Id Send** *(ux_device_class_pima_storage_id_send)*</span></span> |
| ![Значок отправки сведений о хранилище класса Pima устройства](./media/user-guide/usbx-events/image32.png)    | <span data-ttu-id="4c86d-172">**Отправка сведений о хранилище класса Pima устройства** *(ux_device_class_pima_storage_info_send)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-172">**Device Class Pima Storage Info Send** *(ux_device_class_pima_storage_info_send)*</span></span> |
| ![Значок активации класса RNDIS устройства](./media/user-guide/usbx-events/image33.png)    | <span data-ttu-id="4c86d-174">**Активация класса RNDIS устройства** *(ux_device_class_rndis_activate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-174">**Device Class Rndis Activate** *(ux_device_class_rndis_activate)*</span></span> |
| ![Значок деактивации класса RNDIS устройства](./media/user-guide/usbx-events/image34.png)    | <span data-ttu-id="4c86d-176">**Деактивация класса RNDIS устройства** *(ux_device_class_rndis_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-176">**Device Class Rndis Deactivate** *(ux_device_class_rndis_deactivate)*</span></span> |
| ![Значок сообщения для проверки активности класса RNDIS устройства](./media/user-guide/usbx-events/image35.png)    | <span data-ttu-id="4c86d-178">**Сообщение для проверки активности класса RNDIS устройства** *(ux_device_class_rndis_msg_keep_alive)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-178">**Device Class Rndis Message Keep Alive** *(ux_device_class_rndis_msg_keep_alive)*</span></span> |
| ![Значок запроса сообщения для класса RNDIS устройства](./media/user-guide/usbx-events/image36.png)    | <span data-ttu-id="4c86d-180">**Запрос сообщения для класса RNDIS устройства** *(ux_device_class_rndis_msg_query)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-180">**Device Class Rndis Message Query** *(ux_device_class_rndis_msg_query)*</span></span> |
| ![Значок сброса сообщения для класса RNDIS устройства](./media/user-guide/usbx-events/image37.png)    | <span data-ttu-id="4c86d-182">**Сброс сообщения для класса RNDIS устройства** *(ux_device_class_rndis_msg_reset)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-182">**Device Class Rndis Message Reset** *(ux_device_class_rndis_msg_reset)*</span></span> |
| ![Значок набора сообщений для класса RNDIS устройства](./media/user-guide/usbx-events/image38.png)    | <span data-ttu-id="4c86d-184">**Набор сообщений для класса RNDIS устройства** *(ux_device_class_rndis_msg_set)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-184">**Device Class Rndis Message Set** *(ux_device_class_rndis_msg_set)*</span></span> |
| ![Значок получения пакета для класса RNDIS устройства](./media/user-guide/usbx-events/image39.png)    | <span data-ttu-id="4c86d-186">**Получение пакета для класса RNDIS устройства** *(ux_device_class_rndis_packet_receive)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-186">**Device Class Rndis Packet Receive** *(ux_device_class_rndis_packet_receive)*</span></span> |
| ![Значок передачи пакетов для класса RNDIS устройства](./media/user-guide/usbx-events/image40.png)    | <span data-ttu-id="4c86d-188">**Передача пакетов для класса RNDIS устройства** *(ux_device_class_rndis_packet_transmit)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-188">**Device Class Rndis Packet Transmit** *(ux_device_class_rndis_packet_transmit)*</span></span> |
| ![Значок активации хранилища класса устройства](./media/user-guide/usbx-events/image41.png)    | <span data-ttu-id="4c86d-190">**Активация хранилища класса устройства** *(ux_device_class_storage_activate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-190">**Device Class Storage Activate** *(ux_device_class_storage_activate)*</span></span> |
| ![Значок деактивации хранилища класса устройства](./media/user-guide/usbx-events/image42.png)    | <span data-ttu-id="4c86d-192">**Деактивация хранилища класса устройства** *(ux_device_class_storage_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-192">**Device Class Storage Deactivate** *(ux_device_class_storage_deactivate)*</span></span> |
| ![Значок форматирования хранилища класса устройства](./media/user-guide/usbx-events/image43.png)    | <span data-ttu-id="4c86d-194">**Форматирование хранилища класса устройства** *(ux_device_class_storage_format)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-194">**Device Class Storage Format** *(ux_device_class_storage_format)*</span></span> |
| ![Значок запроса хранилища класса устройства](./media/user-guide/usbx-events/image44.png)    | <span data-ttu-id="4c86d-196">**Запрос хранилища класса устройства** *(ux_device_class_storage_inquiry)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-196">**Device Class Storage Inquiry** *(ux_device_class_storage_inquiry)*</span></span> |
| ![Значок выбора режима хранения класса устройства](./media/user-guide/usbx-events/image45.png)    | <span data-ttu-id="4c86d-198">**Выбор режима хранения класса устройства** *(ux_device_class_storage_mode_select)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-198">**Device Class Storage Mode Select** *(ux_device_class_storage_mode_select)*</span></span> |
| ![Значок контроля режима хранения в классе устройства](./media/user-guide/usbx-events/image46.png)    | <span data-ttu-id="4c86d-200">**Контроль режима хранения в классе устройства** *(ux_device_class_storage_mode_sense)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-200">**Device Class Storage Mode Sense** *(ux_device_class_storage_mode_sense)*</span></span> |
| ![Значок запрета удаления носителей в хранилище класса устройства](./media/user-guide/usbx-events/image47.png)    | <span data-ttu-id="4c86d-202">**Запрет удаления носителей в хранилище класса устройства** *(ux_device_class_storage_prevent_allow_media_removal)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-202">**Device Class Storage Prevent Allow Media Removal** *(ux_device_class_storage_prevent_allow_media_removal)*</span></span> |
| ![Значок считывания хранилища класса устройства](./media/user-guide/usbx-events/image48.png)    | <span data-ttu-id="4c86d-204">**Считывание хранилища класса устройства** *(ux_device_class_storage_read)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-204">**Device Class Storage Read** *(ux_device_class_storage_read)*</span></span> |
| ![Значок считывания емкости хранилища класса устройства](./media/user-guide/usbx-events/image49.png)    | <span data-ttu-id="4c86d-206">**Считывание емкости хранилища класса устройства** *(ux_device_class_storage_read_capacity)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-206">**Device Class Storage Read Capacity** *(ux_device_class_storage_read_capacity)*</span></span> |
| ![Значок емкости носителя для форматирования хранилища класса устройства](./media/user-guide/usbx-events/image50.png)    | <span data-ttu-id="4c86d-208">**Емкость носителя для форматирования хранилища класса устройства** *(ux_device_class_storage_read_format_capacity)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-208">**Device Class Storage Read Format Capacity** *(ux_device_class_storage_read_format_capacity)*</span></span> |
| ![Значок считывания оглавления хранилища класса устройства](./media/user-guide/usbx-events/image51.png)    | <span data-ttu-id="4c86d-210">**Считывание оглавления хранилища класса устройства** *(ux_device_class_storage_read)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-210">**Device Class Storage Read TOC** *(ux_device_class_storage_read_toc)*</span></span> |
| ![Значок запроса на контроль хранилища класса устройства](./media/user-guide/usbx-events/image52.png)    | <span data-ttu-id="4c86d-212">**Запрос на контроль хранилища класса устройства** *(ux_device_class_storage_request_sense)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-212">**Device Class Storage Request Sense** *(ux_device_class_storage_request_sense)*</span></span> |
| ![Значок запуска и остановки хранилища класса устройств](./media/user-guide/usbx-events/image53.png)    | <span data-ttu-id="4c86d-214">**Запуск и остановка хранилища класса устройства** *(ux_device_class_storage_start_stop)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-214">**Device Class Storage Start Stop** *(ux_device_class_storage_start_stop)*</span></span> |
| ![Значок готовности к тестированию хранилища класса устройства](./media/user-guide/usbx-events/image54.png)    | <span data-ttu-id="4c86d-216">**Готовность к тестированию хранилища класса устройства** *(ux_device_class_storage_test_ready)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-216">**Device Class Storage Test Ready** *(ux_device_class_storage_test_ready)*</span></span> |
| ![Значок проверки хранилища класса устройства](./media/user-guide/usbx-events/image55.png)    | <span data-ttu-id="4c86d-218">**Проверка хранилища класса устройства** *(ux_device_class_storage_verify)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-218">**Device Class Storage Verify** *(ux_device_class_storage_verify)*</span></span> |
| ![Значок записи хранилища класса устройства](./media/user-guide/usbx-events/image56.png)    | <span data-ttu-id="4c86d-220">**Запись хранилища класса устройства** *(ux_device_class_storage_write)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-220">**Device Class Storage Write** *(ux_device_class_storage_write)*</span></span> |
| ![Значок получения дополнительных параметров стека устройства](./media/user-guide/usbx-events/image57.png)    | <span data-ttu-id="4c86d-222">**Получение дополнительных параметров стека устройства** *(ux_device_stack_alternate_setting_get)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-222">**Device Stack Alternate Setting Get** *(ux_device_stack_alternate_setting_get)*</span></span> |
| ![Значок установки дополнительных параметров стека устройства](./media/user-guide/usbx-events/image58.png)    | <span data-ttu-id="4c86d-224">**Установка дополнительных параметров стека устройства** *(ux_device_stack_alternate_setting_set)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-224">**Device Stack Alternate Setting Set** *(ux_device_stack_alternate_setting_set)*</span></span> |
| ![Значок регистрации класса в стеке устройства](./media/user-guide/usbx-events/image59.png)    | <span data-ttu-id="4c86d-226">**Регистрация класса в стеке устройства** *(ux_device_stack_class_register)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-226">**Device Stack Class Register** *(ux_device_stack_class_register)*</span></span> |
| ![Значок возможности очистки стека устройства](./media/user-guide/usbx-events/image60.png)    | <span data-ttu-id="4c86d-228">**Возможность очистки стека устройства** *(ux_device_stack_clear_feature)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-228">**Device Stack Clear Feature** *(ux_device_stack_clear_feature)*</span></span> |
| ![Значок получения конфигурации стека устройства](./media/user-guide/usbx-events/image61.png)    | <span data-ttu-id="4c86d-230">**Получение конфигурации стека устройства** *(ux_device_stack_configuration_get)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-230">**Device Stack Configuration Get** *(ux_device_stack_configuration_get)*</span></span> |
| ![Значок набора конфигурации стека устройства](./media/user-guide/usbx-events/image62.png)    | <span data-ttu-id="4c86d-232">**Набор конфигурации стека устройства** *(ux_device_stack_configuration_set)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-232">**Device Stack Configuration Set** *(ux_device_stack_configuration_set)*</span></span> |
| ![Значок подключения к стеку устройства](./media/user-guide/usbx-events/image63.png)    | <span data-ttu-id="4c86d-234">**Подключение к стеку устройства** *(ux_device_stack_connect)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-234">**Device Stack Connect** *(ux_device_stack_connect)*</span></span> |
| ![Значок отправки дескриптора стека устройства](./media/user-guide/usbx-events/image64.png)    | <span data-ttu-id="4c86d-236">**Отправка дескриптора стека устройства** *(ux_device_stack_descriptor_send)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-236">**Device Stack Descriptor Send** *(ux_device_stack_descriptor_send)*</span></span> |
| ![Значок отключения стека устройства](./media/user-guide/usbx-events/image65.png)    | <span data-ttu-id="4c86d-238">**Отключение стека устройства** *(ux_device_stack_disconnect)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-238">**Device Stack Disconnect** *(ux_device_stack_disconnect)*</span></span> |
| ![Значок остановки конечной точки стека устройства](./media/user-guide/usbx-events/image66.png)    | <span data-ttu-id="4c86d-240">**Остановка конечной точки стека устройства** *(ux_device_stack_endpoint_stall)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-240">**Device Stack Endpoint Stall** *(ux_device_stack_endpoint_stall)*</span></span> |
| ![Значок состояния получения стека устройства](./media/user-guide/usbx-events/image67.png)    | <span data-ttu-id="4c86d-242">**Состояние получения стека устройства** *(ux_device_stack_get_status)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-242">**Device Stack Get Status** *(ux_device_stack_get_status)*</span></span> |
| ![Значок выхода узла стека устройства из спящего режима](./media/user-guide/usbx-events/image68.png)    | <span data-ttu-id="4c86d-244">**Выход узла стека устройства из спящего режима** *(ux_device_stack_host_wakeup)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-244">**Device Stack Host Wakeup** *(ux_device_stack_host_wakeup)*</span></span> |
| ![Значок инициализации стека устройства](./media/user-guide/usbx-events/image69.png)    | <span data-ttu-id="4c86d-246">**Инициализация стека устройства** *(ux_device_stack_initialize)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-246">**Device Stack Initialize** *(ux_device_stack_initialize)*</span></span> |
| ![Значок удаления интерфейса стека устройства](./media/user-guide/usbx-events/image70.png)    | <span data-ttu-id="4c86d-248">**Удаление интерфейса стека устройства** *(ux_device_stack_interface_delete)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-248">**Device Stack Interface Delete** *(ux_device_stack_interface_delete)*</span></span> |
| ![Значок получения интерфейса стека устройства](./media/user-guide/usbx-events/image71.png)    | <span data-ttu-id="4c86d-250">**Получение интерфейса стека устройства** *(ux_device_stack_interface_get)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-250">**Device Stack Interface Get** *(ux_device_stack_interface_get)*</span></span> |
| ![Значок установки набора интерфейсов стека устройства](./media/user-guide/usbx-events/image72.png)    | <span data-ttu-id="4c86d-252">**Набор интерфейсов стека устройства** *(ux_device_stack_interface_set)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-252">**Device Stack Interface Set** *(ux_device_stack_interface_set)*</span></span> |
| ![Значок возможностей набора стеков устройства](./media/user-guide/usbx-events/image73.png)    | <span data-ttu-id="4c86d-254">**Возможности набора стеков устройства** *(ux_device_stack_set_feature)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-254">**Device Stack Set Feature** *(ux_device_stack_set_feature)*</span></span> |
| ![Значок прерывания перемещения стека устройства](./media/user-guide/usbx-events/image74.png)    | <span data-ttu-id="4c86d-256">**Прерывание перемещения стека устройства** *(ux_device_stack_transfer_abort)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-256">**Device Stack Transfer Abort** *(ux_device_stack_transfer_abort)*</span></span> |
| ![\*Значок прерывания всех запросов на передачу стека устройства](./media/user-guide/usbx-events/image75.png)    | <span data-ttu-id="4c86d-258">**Прерывание всех запросов на передачу стека устройства** *(ux_device_stack_transfer_all_request_abort)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-258">**Device Stack Transfer All Request Abort** *(ux_device_stack_transfer_all_request_abort)*</span></span> |
| ![Значок запроса на передачу стека устройства](./media/user-guide/usbx-events/image76.png)    | <span data-ttu-id="4c86d-260">**Запрос на передачу стека устройства** *(ux_device_stack_transfer_request)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-260">**Device Stack Transfer Request** *(ux_device_stack_transfer_request)*</span></span> |
| ![Значок активации класса Asix узла](./media/user-guide/usbx-events/image77.png)    | <span data-ttu-id="4c86d-262">**Активация класса Asix узла** *(ux_host_class_asix_activate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-262">**Host Class Asix Activate** *(ux_host_class_asix_activate)*</span></span> |
| ![Значок деактивации класса Asix узла](./media/user-guide/usbx-events/image78.png)    | <span data-ttu-id="4c86d-264">**Деактивация класса Asix узла** *(ux_host_class_asix_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-264">**Host Class Asix Deactivate** *(ux_host_class_asix_deactivate)*</span></span> |
| ![Значок уведомления о прерывании класса Asix узла](./media/user-guide/usbx-events/image79.png)    | <span data-ttu-id="4c86d-266">**Уведомление о прерывании класса Asix узла** *(ux_host_class_asix_interrupt_notification)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-266">**Host Class Asix Interrupt Notification** *(ux_host_class_asix_interrupt_notification)*</span></span> |
| ![Значок считывания класса Asix узла](./media/user-guide/usbx-events/image80.png)    | <span data-ttu-id="4c86d-268">**Считывание класса Asix узла** *(ux_host_class_asix_read)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-268">**Host Class Asix Read** *(ux_host_class_asix_read)*</span></span> |
| ![Значок записи класса Asix узла](./media/user-guide/usbx-events/image81.png)    | <span data-ttu-id="4c86d-270">**Запись класса Asix узла** *(ux_host_class_asix_write)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-270">**Host Class Asix Write** *(ux_host_class_asix_write)*</span></span> |
| ![Значок активации звука для класса узла](./media/user-guide/usbx-events/image82.png)    | <span data-ttu-id="4c86d-272">**Активация звука для класса узла** *(ux_host_class_audio_activate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-272">**Host Class Audio Activate** *(ux_host_class_audio_activate)*</span></span> |
| ![Значок получения значения элемента управления звуком для класса узла](./media/user-guide/usbx-events/image83.png)    | <span data-ttu-id="4c86d-274">**Получение значения элемента управления звуком для класса узла** *(ux_host_class_audio_control_value_get)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-274">**Host Class Audio Control Value Get** *(ux_host_class_audio_control_value_get)*</span></span> |
| ![Значок установки значений элемента управления звуком для класса узла](./media/user-guide/usbx-events/image84.png)    | <span data-ttu-id="4c86d-276">**Установка значений элемента управления звуком для класса узла** *(ux_host_class_audio_control_value_set)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-276">**Host Class Audio Control Value Set** *(ux_host_class_audio_control_value_set)*</span></span> |
| ![Значок деактивации звука для класса узла](./media/user-guide/usbx-events/image85.png)    | <span data-ttu-id="4c86d-278">**Деактивация звука для класса узла** *(ux_host_class_audio_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-278">**Host Class Audio Deactivate** *(ux_host_class_audio_deactivate)*</span></span> |
| ![Значок считывания звуковых данных класса узла](./media/user-guide/usbx-events/image86.png)    | <span data-ttu-id="4c86d-280">**Считывание звуковых данных класса узла** *(ux_host_class_audio_read)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-280">**Host Class Audio Read** *(ux_host_class_audio_read)*</span></span> |
| ![Значок получения выборки данных звукового потока для класса узла](./media/user-guide/usbx-events/image87.png)    | <span data-ttu-id="4c86d-282">**Получение выборки данных звукового потока для класса узла** *(ux_host_class_audio_streaming_sampling_get)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-282">**Host Class Audio Streaming Sampling Get** *(ux_host_class_audio_streaming_sampling_get)*</span></span> |
| ![Значок задания данных для выборки звукового потока для класса узла](./media/user-guide/usbx-events/image88.png)    | <span data-ttu-id="4c86d-284">**Задание данных для выборки звукового потока для класса узла** *(ux_host_class_audio_streaming_sampling_set)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-284">**Host Class Audio Streaming Sampling Set** *(ux_host_class_audio_streaming_sampling_set)*</span></span> |
| ![Значок записи звуковых данных класса узла](./media/user-guide/usbx-events/image89.png)    | <span data-ttu-id="4c86d-286">**Запись звуковых данных класса узла** *(ux_host_class_audio_write)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-286">**Host Class Audio Write** *(ux_host_class_audio_write)*</span></span> |
| ![Значок активации класса Cdc Acm узла](./media/user-guide/usbx-events/image90.png)    | <span data-ttu-id="4c86d-288">**Активация класса Cdc Acm узла** *(ux_host_class_cdc_acm_activate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-288">**Host Class Cdc Acm Activate** *(ux_host_class_cdc_acm_activate)*</span></span> |
| ![Значок деактивации класса Cdc Acm узла](./media/user-guide/usbx-events/image91.png)    | <span data-ttu-id="4c86d-290">**Деактивация класса Cdc Acm узла** *(ux_host_class_cdc_acm_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-290">**Host Class Cdc Acm Deactivate** *(ux_host_class_cdc_acm_deactivate)*</span></span> |
| ![Значок прерывания в канале класса Cdc Acm Ioctl узла](./media/user-guide/usbx-events/image92.png)    | <span data-ttu-id="4c86d-292">**Прерывание в канале класса Cdc Acm Ioctl узла** *(ux_host_class_cdc_acm_ioctl_abort_in_pipe)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-292">**Host Class Cdc Acm Ioctl Abort In Pipe** *(ux_host_class_cdc_acm_ioctl_abort_in_pipe)*</span></span> |
| ![Значок прерывания вне канала класса Cdc Acm Ioctl узла](./media/user-guide/usbx-events/image93.png)    | <span data-ttu-id="4c86d-294">**Прерывание вне канала класса Cdc Acm Ioctl узла** *(ux_host_class_cdc_acm_ioctl_abort_out_pipe)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-294">**Host Class Cdc Acm Ioctl Abort Out Pipe** *(ux_host_class_cdc_acm_ioctl_abort_out_pipe)*</span></span> |
| ![Значок получения состояния устройства класса Cdc Acm Ioctl узла](./media/user-guide/usbx-events/image94.png)    | <span data-ttu-id="4c86d-296">**Получение состояния устройства класса Cdc Acm Ioctl узла** *(ux_host_class_cdc_acm_ioctl_get_device_status)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-296">**Host Class Cdc Acm Ioctl Get Device Status** *(ux_host_class_cdc_acm_ioctl_get_device_status)*</span></span> |
| ![Значок получения кодировки строки класса Cdc Acm Ioctl узла](./media/user-guide/usbx-events/image95.png)    | <span data-ttu-id="4c86d-298">**Получение кодировки строки класса Cdc Acm Ioctl узла** *(ux_host_class_cdc_acm_ioctl_get_line_coding)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-298">**Host Class Cdc Acm Ioctl Get Line Coding** *(ux_host_class_cdc_acm_ioctl_get_line_coding)*</span></span> |
| ![Значок обратного вызова уведомления класса Cdc Acm Ioctl узла](./media/user-guide/usbx-events/image96.png)    | <span data-ttu-id="4c86d-300">**Обратный вызов уведомления класса Cdc Acm Ioctl узла** *(ux_host_class_cdc_acm_ioctl_notification_callback)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-300">**Host Class Cdc Acm Ioctl Notification Callback** *(ux_host_class_cdc_acm_ioctl_notification_callback)*</span></span> |
| ![Значок остановки отправки класса Cdc Acm Ioctl узла](./media/user-guide/usbx-events/image97.png)    | <span data-ttu-id="4c86d-302">**Остановка отправки класса Cdc Acm Ioctl узла** *(ux_host_class_cdc_acm_ioctl_send_break)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-302">**Host Class Cdc Acm Ioctl Send Break** *(ux_host_class_cdc_acm_ioctl_send_break)*</span></span> |
| ![Значок задания кодировки строки в классе Cdc Acm Ioctl узла](./media/user-guide/usbx-events/image98.png)    | <span data-ttu-id="4c86d-304">**Задание кодировки строки в классе Cdc Acm Ioctl узла** *(ux_host_class_cdc_acm_ioctl_set_line_coding)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-304">**Host Class Cdc Acm Ioctl Set Line Coding** *(ux_host_class_cdc_acm_ioctl_set_line_coding)*</span></span> |
| ![Значок задания состояния кодировки строки в классе Cdc Acm Ioctl узла](./media/user-guide/usbx-events/image99.png)    | <span data-ttu-id="4c86d-306">**Задание состояния кодировки строки в классе Cdc Acm Ioctl узла** *(ux_host_class_cdc_acm_ioctl_set_line_state)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-306">**Host Class Cdc Acm Ioctl Set Line State** *(ux_host_class_cdc_acm_ioctl_set_line_state)*</span></span> |
| ![Значок считывания класса Cdc Acm узла](./media/user-guide/usbx-events/image100.png)    | <span data-ttu-id="4c86d-308">**Считывание класса Cdc Acm узла** *(ux_host_class_cdc_acm_read)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-308">**Host Class Cdc Acm Read** *(ux_host_class_cdc_acm_read)*</span></span> |
| ![Значок запуска приема класса Cdc Acm узла](./media/user-guide/usbx-events/image101.png)    | <span data-ttu-id="4c86d-310">**Запуск приема класса Cdc Acm узла** *(ux_host_class_cdc_acm_reception_start)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-310">**Host Class Cdc Acm Reception Start** *(ux_host_class_cdc_acm_reception_start)*</span></span> |
| ![Значок остановки приема класса Cdc Acm узла](./media/user-guide/usbx-events/image102.png)    | <span data-ttu-id="4c86d-312">**Остановка приема класса Cdc Acm узла** *(ux_host_class_cdc_acm_reception_stop)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-312">**Host Class Cdc Acm Reception Stop** *(ux_host_class_cdc_acm_reception_stop)*</span></span> |
| ![Значок записи класса Cdc Acm узла](./media/user-guide/usbx-events/image103.png)    | <span data-ttu-id="4c86d-314">**Запись класса Cdc Acm узла** *(ux_host_class_cdc_acm_write)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-314">**Host Class Cdc Acm Write** *(ux_host_class_cdc_acm_write)*</span></span> |
| ![Значок активации класса Dpump узла](./media/user-guide/usbx-events/image104.png)    | <span data-ttu-id="4c86d-316">**Активация класса Dpump узла** *(ux_host_class_dpump_activate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-316">**Host Class Dpump Activate** *(ux_host_class_dpump_activate)*</span></span> |
| ![Значок деактивации класса Dpump узла](./media/user-guide/usbx-events/image105.png)    | <span data-ttu-id="4c86d-318">**Деактивация класса Dpump узла** *(ux_host_class_dpump_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-318">**Host Class Dpump Deactivate** *(ux_host_class_dpump_deactivate)*</span></span> |
| ![Значок считывания класса Dpump узла](./media/user-guide/usbx-events/image106.png)    | <span data-ttu-id="4c86d-320">**Считывание класса Dpump узла** *(ux_host_class_dpump_read)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-320">**Host Class Dpump Read** *(ux_host_class_dpump_read)*</span></span> |
| ![Значок записи класса Dpump узла](./media/user-guide/usbx-events/image107.png)    | <span data-ttu-id="4c86d-322">**Запись класса Dpump узла** *(ux_host_class_dpump_write)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-322">**Host Class Dpump Write** *(ux_host_class_dpump_write)*</span></span> |
| ![Значок активации класса Hid узла](./media/user-guide/usbx-events/image108.png)    | <span data-ttu-id="4c86d-324">**Активация класса Hid узла** *(ux_host_class_hid_activate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-324">**Host Class Hid Activate** *(ux_host_class_hid_activate)*</span></span> |
| ![Значок регистрации клиента класса Hid узла](./media/user-guide/usbx-events/image109.png)    | <span data-ttu-id="4c86d-326">**Регистрация клиента класса Hid узла** *(ux_host_class_hid_client_register)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-326">**Host Class Hid Client Register** *(ux_host_class_hid_client_register)*</span></span> |
| ![Значок деактивации класса Hid узла](./media/user-guide/usbx-events/image110.png)    | <span data-ttu-id="4c86d-328">**Деактивация класса Hid узла** *(ux_host_class_hid_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-328">**Host Class Hid Deactivate** *(ux_host_class_hid_deactivate)*</span></span> |
| ![Значок получения состояния бездействия класса Hid узла](./media/user-guide/usbx-events/image111.png)    | <span data-ttu-id="4c86d-330">**Получение состояния бездействия класса Hid узла** *(ux_host_class_hid_idle_get)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-330">**Host Class Hid Idle Get** *(ux_host_class_hid_idle_get)*</span></span> |
| ![Значок установки состояния бездействия класса Hid узла](./media/user-guide/usbx-events/image112.png)    | <span data-ttu-id="4c86d-332">**Установка состояния бездействия класса Hid узла** *(ux_host_class_hid_idle_set)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-332">**Host Class Hid Idle Set** *(ux_host_class_hid_idle_set)*</span></span> |
| ![Значок активации клавиатуры для класса Hid узла](./media/user-guide/usbx-events/image113.png)    | <span data-ttu-id="4c86d-334">**Активация клавиатуры для класса Hid узла** *(ux_host_class_hid_keyboard_activate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-334">**Host Class Hid Keyboard Activate** *(ux_host_class_hid_keyboard_activate)*</span></span> |
| ![Значок деактивации клавиатуры для класса Hid узла](./media/user-guide/usbx-events/image114.png)    | <span data-ttu-id="4c86d-336">**Деактивация клавиатуры для класса Hid узла** *(ux_host_class_hid_keyboard_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-336">**Host Class Hid Keyboard Deactivate** *(ux_host_class_hid_keyboard_deactivate)*</span></span> |
| ![Значок активации мыши для класса Hid узла](./media/user-guide/usbx-events/image115.png)    | <span data-ttu-id="4c86d-338">**Активация мыши для класса Hid узла** *(ux_host_class_hid_keyboard_activate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-338">**Host Class Hid Mouse Activate** *(ux_host_class_hid_mouse_activate)*</span></span> |
| ![Значок деактивации мыши для класса Hid узла](./media/user-guide/usbx-events/image116.png)    | <span data-ttu-id="4c86d-340">**Деактивация мыши для класса Hid узла** *(ux_host_class_hid_mouse_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-340">**Host Class Hid Mouse Deactivate** *(ux_host_class_hid_mouse_deactivate)*</span></span> |
| ![Значок активации удаленного управления для класса Hid узла](./media/user-guide/usbx-events/image117.png)    | <span data-ttu-id="4c86d-342">**Активация удаленного управления для класса Hid узла** *(ux_host_class_hid_remote_control_activate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-342">**Host Class Hid Remote Control Activate** *(ux_host_class_hid_remote_control_activate)*</span></span> |
| ![Значок деактивации удаленного управления для класса Hid узла](./media/user-guide/usbx-events/image118.png)    | <span data-ttu-id="4c86d-344">**Деактивация удаленного управления для класса Hid узла** *(ux_host_class_hid_remote_control_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-344">**Host Class Hid Remote Control Deactivate** *(ux_host_class_hid_remote_control_deactivate)*</span></span> |
| ![Значок получения отчета класса Hid узла](./media/user-guide/usbx-events/image119.png)    | <span data-ttu-id="4c86d-346">**Получение отчета класса Hid узла** *(ux_host_class_hid_report_get)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-346">**Host Class Hid Report Get** *(ux_host_class_hid_report_get)*</span></span> |
| ![Значок набора отчетов класса Hid узла](./media/user-guide/usbx-events/image120.png)    | <span data-ttu-id="4c86d-348">**Набор отчетов класса Hid узла** *(ux_host_class_hid_report_get)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-348">**Host Class Hid Report Set** *(ux_host_class_hid_report_set)*</span></span> |
| ![Значок активации концентратора класса узла](./media/user-guide/usbx-events/image121.png)    | <span data-ttu-id="4c86d-350">**Активация концентратора класса узла** *(ux_host_class_hub_activate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-350">**Host Class Hub Activate** *(ux_host_class_hub_activate)*</span></span> |
| ![Значок обнаружения изменений концентратора класса узла](./media/user-guide/usbx-events/image122.png)    | <span data-ttu-id="4c86d-352">**Обнаружение изменений концентратора класса узла** *(ux_host_class_hub_change_detect)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-352">**Host Class Hub Change Detect** *(ux_host_class_hub_change_detect)*</span></span> |
| ![\*Значок деактивации концентратора класса узла](./media/user-guide/usbx-events/image123.png)    | <span data-ttu-id="4c86d-354">**Деактивация концентратора класса узла** *(ux_host_class_hub_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-354">**Host Class Hub Deactivate** *(ux_host_class_hub_deactivate)*</span></span> |
| ![Значок процесса подключения для изменения порта концентратора класса узла](./media/user-guide/usbx-events/image124.png)    | <span data-ttu-id="4c86d-356">**Процесс подключения для изменения порта концентратора класса узла** *(ux_host_class_hub_port_change_connection_process)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-356">**Host Class Hub Port Change Connection Process** *(ux_host_class_hub_port_change_connection_process)*</span></span> |
| ![Значок процесса включения для изменения порта концентратора класса узла](./media/user-guide/usbx-events/image125.png)    | <span data-ttu-id="4c86d-358">**Процесс включения для изменения порта концентратора класса узла** *(ux_host_class_hub_port_change_enable_process)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-358">**Host Class Hub Port Change Enable Process** *(ux_host_class_hub_port_change_enable_process)*</span></span> |
| ![Значок завершения текущего процесса для изменения порта концентратора класса узла](./media/user-guide/usbx-events/image126.png)    | <span data-ttu-id="4c86d-360">**Завершение текущего процесса для изменения порта концентратора класса узла** *(ux_host_class_hub_port_change_over_current_process)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-360">**Host Class Hub Port Change Over Current Process** *(ux_host_class_hub_port_change_over_current_process)*</span></span> |
| ![Значок процесса сброса для изменения порта концентратора класса узла](./media/user-guide/usbx-events/image127.png)    | <span data-ttu-id="4c86d-362">**Процесс сброса для изменения порта концентратора класса узла** *(ux_host_class_hub_port_change_reset_process)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-362">**Host Class Hub Port Change Reset Process** *(ux_host_class_hub_port_change_reset_process)*</span></span> |
| ![Значок процесса приостановки для изменения порта концентратора класса узла](./media/user-guide/usbx-events/image128.png)    | <span data-ttu-id="4c86d-364">**Процесс приостановки для изменения порта концентратора класса узла** *(ux_host_class_hub_port_change_suspend_process)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-364">**Host Class Hub Port Change Suspend Process** *(ux_host_class_hub_port_change_suspend_process)*</span></span> |
| ![Значок активации класса Pima узла](./media/user-guide/usbx-events/image129.png)    | <span data-ttu-id="4c86d-366">**Активация класса Pima узла** *(ux_host_class_prima_activate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-366">**Host Class Pima Activate** *(ux_host_class_prima_activate)*</span></span> |
| ![Значок деактивации класса Pima узла](./media/user-guide/usbx-events/image130.png)    | <span data-ttu-id="4c86d-368">**Деактивация класса Pima узла** *(ux_host_class_pima_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-368">**Host Class Pima Deactivate** *(ux_host_class_pima_deactivate)*</span></span> |
| ![Значок получения сведений об устройстве для класса Pima узла](./media/user-guide/usbx-events/image131.png)    | <span data-ttu-id="4c86d-370">**Получение сведений об устройстве для класса Pima узла** *(ux_host_class_pima_device_info_get)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-370">**Host Class Pima Device Info Get** *(ux_host_class_pima_device_info_get)*</span></span> |
| ![Значок сброса устройства для класса Pima узла](./media/user-guide/usbx-events/image132.png)    | <span data-ttu-id="4c86d-372">**Сброс устройства для класса Pima узла** *(ux_host_class_pima_device_reset)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-372">**Host Class Pima Device Reset** *(ux_host_class_pima_device_reset)*</span></span> |
| ![Значок уведомления класса Pima узла](./media/user-guide/usbx-events/image133.png)    | <span data-ttu-id="4c86d-374">**Уведомление класса Pima узла** *(ux_host_class_pima_notification)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-374">**Host Class Pima Notification** *(ux_host_class_pima_notification)*</span></span> |
| ![Значок получения объектов номера класса Pima узла](./media/user-guide/usbx-events/image134.png)    | <span data-ttu-id="4c86d-376">**Получение объектов номера класса Pima узла** *(ux_host_class_pima_num_objects_get)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-376">**Host Class Pima Number Objects Get** *(ux_host_class_pima_num_objects_get)*</span></span> |
| ![Значок закрытия объекта класса Pima узла](./media/user-guide/usbx-events/image135.png)    | <span data-ttu-id="4c86d-378">**Закрытие объекта класса Pima узла** *(ux_host_class_pima_object_close)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-378">**Host Class Pima Object Close** *(ux_host_class_pima_object_close)*</span></span> |
| ![Значок копирования объекта класса Pima узла](./media/user-guide/usbx-events/image136.png)    | <span data-ttu-id="4c86d-380">**Копирование объекта класса Pimа узла** *(ux_host_class_pima_object_copy)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-380">**Host Class Pima Object Copy** *(ux_host_class_pima_object_copy)*</span></span> |
| ![Значок удаления объекта из класса Pima узла](./media/user-guide/usbx-events/image137.png)    | <span data-ttu-id="4c86d-382">**Удаление объекта из класса Pima узла** *(ux_host_class_pima_object_delete)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-382">**Host Class Pima Object Delete** *(ux_host_class_pima_object_delete)*</span></span> |
| ![Значок получения объекта класса Pima узла](./media/user-guide/usbx-events/image138.png)    | <span data-ttu-id="4c86d-384">**Получение объекта класса Pima узла** *(ux_host_class_pima_object_get)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-384">**Host Class Pima Object Get** *(ux_host_class_pima_object_get)*</span></span> |
| ![Значок получения сведений об объекте класса Pima узла](./media/user-guide/usbx-events/image139.png)    | <span data-ttu-id="4c86d-386">**Получение сведений об объекте класса Pima узла** *(ux_host_class_pima_object_info_get)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-386">**Host Class Pima Object Info Get** *(ux_host_class_pima_object_info_get)*</span></span> |
| ![Значок отправки сведений об объекте класса Pima узла](./media/user-guide/usbx-events/image140.png)    | <span data-ttu-id="4c86d-388">**Отправка сведений об объекте класса Pima узла** *(ux_host_class_pima_object_info_send)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-388">**Host Class Pima Object Info Send** *(ux_host_class_pima_object_info_send)*</span></span> |
| ![Значок перемещения объекта класса Pima узла](./media/user-guide/usbx-events/image141.png)    | <span data-ttu-id="4c86d-390">**Перемещение объекта класса Pima узла** *(ux_host_class_pima_object_move)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-390">**Host Class Pima Object Move** *(ux_host_class_pima_object_move)*</span></span> |
| ![Значок отправки объекта класса Pima узла](./media/user-guide/usbx-events/image142.png)    | <span data-ttu-id="4c86d-392">**Отправка объекта класса Pima узла** *(ux_host_class_pima_object_send)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-392">**Host Class Pima Object Send** *(ux_host_class_pima_object_send)*</span></span> |
| ![Значок прерывания перемещения объекта класса Pima узла](./media/user-guide/usbx-events/image143.png)    | <span data-ttu-id="4c86d-394">**Прерывание перемещения объекта класса Pima узла** *(ux_host_class_object_transfer_abort)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-394">**Host Class Pima Object Transfer Abort** *(ux_host_class_object_transfer_abort)*</span></span> |
| ![Значок считывания класса Pima узла](./media/user-guide/usbx-events/image144.png)    | <span data-ttu-id="4c86d-396">**Считывание класса Pima узла** *(ux_host_class_pima_read)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-396">**Host Class Pima Read** *(ux_host_class_pima_read)*</span></span> |
| ![Значок отмены запроса класса Pima узла](./media/user-guide/usbx-events/image145.png)    | <span data-ttu-id="4c86d-398">**Отмена запроса класса Pima узла** *(ux_host_class_pima_request_cancel)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-398">**Host Class Pima Request Cancel** *(ux_host_class_pima_request_cancel)*</span></span> |
| ![Значок завершения сеанса класса Pima узла](./media/user-guide/usbx-events/image146.png)    | <span data-ttu-id="4c86d-400">**Завершение сеанса класса Pima узла** *(ux_host_class_pima_session_close)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-400">**Host Class Pima Session Close** *(ux_host_class_pima_session_close)*</span></span> |
| ![Значок начала сеанса класса Pima узла](./media/user-guide/usbx-events/image147.png)    | <span data-ttu-id="4c86d-402">**Начало сеанса класса Pima узла** *(ux_host_class_pima_session_open)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-402">**Host Class Pima Session Open** *(ux_host_class_pima_session_open)*</span></span> |
| ![Значок получения идентификаторов хранилища класса Pima узла](./media/user-guide/usbx-events/image148.png)    | <span data-ttu-id="4c86d-404">**Получение идентификаторов хранилища класса Pima узла** *(ux_host_class_pima_storage_ids_get)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-404">**Host Class Pima Storage Ids Get** *(ux_host_class_pima_storage_ids_get)*</span></span> |
| ![Значок получения сведений о хранилище класса Pima узла](./media/user-guide/usbx-events/image149.png)    | <span data-ttu-id="4c86d-406">**Получение сведений о хранилище класса Pima узла** *(ux_host_class_pima_storage_info_get)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-406">**Host Class Pima Storage Info Get** *(ux_host_class_pima_storage_info_get)*</span></span> |
| ![Значок получения бегунка класса Pima узла](./media/user-guide/usbx-events/image150.png)    | <span data-ttu-id="4c86d-408">**Получение бегунка класса Pima узла** *(ux_host_class_pima_thumb_get)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-408">**Host Class Pima Thumb Get** *(ux_host_class_pima_thumb_get)*</span></span> |
| ![Значок записи класса Pima узла](./media/user-guide/usbx-events/image151.png)    | <span data-ttu-id="4c86d-410">**Запись класса Pima узла** *(ux_host_class_pima_write)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-410">**Host Class Pima Write** *(ux_host_class_pima_write)*</span></span> |
| ![Значок активации принтера класса узла](./media/user-guide/usbx-events/image152.png)    | <span data-ttu-id="4c86d-412">**Активация принтера класса узла** *(ux_host_class_printer_activate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-412">**Host Class Printer Activate** *(ux_host_class_printer_activate)*</span></span> |
| ![Значок деактивации принтера класса узла](./media/user-guide/usbx-events/image153.png)    | <span data-ttu-id="4c86d-414">**Деактивация принтера класса узла** *(ux_host_class_printer_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-414">**Host Class Printer Deactivate** *(ux_host_class_printer_deactivate)*</span></span> |
| ![Значок получения имени принтера класса узла](./media/user-guide/usbx-events/image154.png)    | <span data-ttu-id="4c86d-416">**Получение имени принтера класса узла** *(ux_host_class_printer_name_get)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-416">**Host Class Printer Name Get** *(ux_host_class_printer_name_get)*</span></span> |
| ![Значок считывания принтера класса узла](./media/user-guide/usbx-events/image155.png)    |  <span data-ttu-id="4c86d-418">**Считывание принтера класса узла** *(ux_host_class_printer_read)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-418">**Host Class Printer Read** *(ux_host_class_printer_read)*</span></span> |
| ![Значок частичного сброса принтера класса узла](./media/user-guide/usbx-events/image156.png)    | <span data-ttu-id="4c86d-420">**Частичный сброс принтера класса узла** *(ux_host_class_printer_soft_reset)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-420">**Host Class Printer Soft Reset** *(ux_host_class_printer_soft_reset)*</span></span> |
| ![Значок получения состояния принтера класса узла](./media/user-guide/usbx-events/image157.png)    | <span data-ttu-id="4c86d-422">**Получение состояния принтера класса узла** *(ux_host_class_printer_status_get)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-422">**Host Class Printer Status Get** *(ux_host_class_printer_status_get)*</span></span> |
| ![Значок записи принтера класса узла](./media/user-guide/usbx-events/image158.png)    | <span data-ttu-id="4c86d-424">**Запись принтера класса узла** *(ux_host_class_printer_write)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-424">**Host Class Printer Write** *(ux_host_class_printer_write)*</span></span> |
| ![Значок активации класса Prolific узла](./media/user-guide/usbx-events/image159.png)    | <span data-ttu-id="4c86d-426">**Активация класса Prolific узла** *(ux_host_class_prolific_activate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-426">**Host Class Prolific Activate** *(ux_host_class_prolific_activate)*</span></span> |
| ![Значок деактивации класса Prolific узла](./media/user-guide/usbx-events/image160.png)    | <span data-ttu-id="4c86d-428">**Деактивация класса Prolific узла** *(ux_host_class_prolific_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-428">**Host Class Prolific Deactivate** *(ux_host_class_prolific_deactivate)*</span></span> |
| ![Значок прерывания в канале класса Prolific Ioctl узла](./media/user-guide/usbx-events/image161.png)    | <span data-ttu-id="4c86d-430">**Прерывание в канале класса Prolific Ioctl узла** *(ux_host_class_prolific_ioctl_abort_in_pipe)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-430">**Host Class Prolific Ioctl Abort In Pipe** *(ux_host_class_prolific_ioctl_abort_in_pipe)*</span></span> |
| ![Значок прерывания вне канала класса Prolific Ioctl узла](./media/user-guide/usbx-events/image162.png)    | <span data-ttu-id="4c86d-432">**Прерывание вне канала класса Prolific Ioctl узла** *(ux_host_class_prolific_ioctl_abort_out_pipe)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-432">**Host Class Prolific Ioctl Abort Out Pipe** *(ux_host_class_prolific_ioctl_abort_out_pipe)*</span></span> |
| ![Значок получения состояния устройства в классе Prolific Ioctl узла](./media/user-guide/usbx-events/image163.png)    | <span data-ttu-id="4c86d-434">**Получение состояния устройства в классе Prolific Ioctl узла** *(ux_host_class_prolific_ioctl_get_device_status)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-434">**Host Class Prolific Ioctl Get Device Status** *(ux_host_class_prolific_ioctl_get_device_status)*</span></span> |
| ![Значок получения кодировки строки в классе Prolific Ioctl узла](./media/user-guide/usbx-events/image164.png)    | <span data-ttu-id="4c86d-436">**Получение кодировки строки в классе Prolific Ioctl узла** *(ux_host_class_prolific_ioctl_get_line_coding)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-436">**Host Class Prolific Ioctl Get Line Coding** *(ux_host_class_prolific_ioctl_get_line_coding)*</span></span> |
| ![Значок очистки класса Prolific Ioctl узла](./media/user-guide/usbx-events/image165.png)    | <span data-ttu-id="4c86d-438">**Очистка класса Prolific Ioctl узла** *(ux_host_class_prolific_ioctl_purge)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-438">**Host Class Prolific Ioctl Purge** *(ux_host_class_prolific_ioctl_purge)*</span></span> |
| ![Значок изменения состояния отчета о классе Prolific Ioctl узла](./media/user-guide/usbx-events/image166.png)    | <span data-ttu-id="4c86d-440">**Изменение состояния отчета о классе Prolific Ioctl узла** *(ux_host_class_prolific_ioctl_report_device_status_change)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-440">**Host Class Prolific Ioctl Report Device Status Change** *(ux_host_class_prolific_ioctl_report_device_status_change)*</span></span> |
| ![Значок остановки отправки в классе Prolific Ioctl узла](./media/user-guide/usbx-events/image167.png)    | <span data-ttu-id="4c86d-442">**Остановка отправки в классе Prolific Ioctl узла** *(ux_host_class_prolific_ioctl_send_break)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-442">**Host Class Prolific Ioctl Send Break** *(ux_host_class_prolific_ioctl_send_break)*</span></span> |
| ![Значок задания кодировки строки в классе Prolific Ioctl узла](./media/user-guide/usbx-events/image168.png)    | <span data-ttu-id="4c86d-444">**Задание кодировки строки в классе Prolific Ioctl узла** *(ux_host_class_prolific_ioctl_set_line_coding)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-444">**Host Class Prolific Ioctl Set Line Coding** *(ux_host_class_prolific_ioctl_set_line_coding)*</span></span> |
| ![Значок задания состояния строк в классе Prolific Ioctl узла](./media/user-guide/usbx-events/image169.png)    | <span data-ttu-id="4c86d-446">**Задание состояния строк в классе Prolific Ioctl узла** *(ux_host_class_prolific_ioctl_set_line_state)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-446">**Host Class Prolific Ioctl Set Line State** *(ux_host_class_prolific_ioctl_set_line_state)*</span></span> |
| ![Значок считывания класса Prolific узла](./media/user-guide/usbx-events/image170.png)    | <span data-ttu-id="4c86d-448">**Считывание класса Prolific узла** *(ux_host_class_prolific_read)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-448">**Host Class Prolific Read** *(ux_host_class_prolific_read)*</span></span> |
| ![Значок запуска приема в классе Prolific узла](./media/user-guide/usbx-events/image171.png)    | <span data-ttu-id="4c86d-450">**Запуск приема в классе Prolific узла** *(ux_host_class_prolific_reception_start)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-450">**Host Class Prolific Reception Start** *(ux_host_class_prolific_reception_start)*</span></span> |
| ![Значок остановки приема в классе Prolific узла](./media/user-guide/usbx-events/image172.png)    | <span data-ttu-id="4c86d-452">**Остановка приема в классе Prolific узла** *(ux_host_class_prolific_reception_stop)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-452">**Host Class Prolific Reception Stop** *(ux_host_class_prolific_reception_stop)*</span></span> |
| ![Значок записи класса Prolific узла](./media/user-guide/usbx-events/image173.png)    | <span data-ttu-id="4c86d-454">**Запись класса Prolific узла** *(ux_host_class_prolific_write)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-454">**Host Class Prolific Write** *(ux_host_class_prolific_write)*</span></span> |
| ![Значок активации хранилища класса узла](./media/user-guide/usbx-events/image174.png)    | <span data-ttu-id="4c86d-456">**Активация хранилища класса узла** *(ux_device_class_storage_activate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-456">**Host Class Storage Activate** *(ux_host_class_storage_activate)*</span></span> |
| ![Значок деактивации хранилища класса узла](./media/user-guide/usbx-events/image175.png)    | <span data-ttu-id="4c86d-458">**Деактивация хранилища класса узла** *(ux_host_class_storage_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-458">**Host Class Storage Deactivate** (*ux_host_class_storage_deactivate)*</span></span> |
| ![Значок получения емкости носителя для хранилища класса узла](./media/user-guide/usbx-events/image176.png)    | <span data-ttu-id="4c86d-460">**Получение емкости носителя для хранилища класса узла** *(ux_host_class_storage_media_capacity_get)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-460">**Host Class Storage Media Capacity Get** *(ux_host_class_storage_media_capacity_get)*</span></span> |
| ![Значок получения формата емкости для носителя в хранилище класса узла](./media/user-guide/usbx-events/image177.png)    | <span data-ttu-id="4c86d-462">**Получение формата емкости для носителя в хранилище класса узла** *(ux_host_class_storage_media_format_capacity_get)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-462">**Host Class Storage Media Format Capacity Get** *(ux_host_class_storage_media_format_capacity_get)*</span></span> |
| ![Значок подключения носителя хранилища класса узла](./media/user-guide/usbx-events/image178.png)    | <span data-ttu-id="4c86d-464">**Подключение носителя хранилища класса узла** (ux_host_class_storage_media_mount)\*</span><span class="sxs-lookup"><span data-stu-id="4c86d-464">**Host Class Storage Media Mount** (ux_host_class_storage_media_mount)\*</span></span> |
| ![Значок открытия носителя хранилища класса узла](./media/user-guide/usbx-events/image179.png)    | <span data-ttu-id="4c86d-466">**Открытие носителя хранилища класса узла** *(ux_host_class_storage_media_open)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-466">**Host Class Storage Media Open** *(ux_host_class_storage_media_open)*</span></span> |
| ![Значок считывания носителя хранилища класса узла](./media/user-guide/usbx-events/image180.png)    | <span data-ttu-id="4c86d-468">**Считывание носителя хранилища класса узла** *(ux_host_class_storage_media_read)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-468">**Host Class Storage Media Read** *(ux_host_class_storage_media_read)*</span></span> |
| ![Значок записи носителя для хранилища класса узла](./media/user-guide/usbx-events/image181.png)    | <span data-ttu-id="4c86d-470">**Запись носителя для хранилища класса узла** *(ux_host_class_storage_media_write)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-470">**Host Class Storage Media Write** *(ux_host_class_storage_media_write)*</span></span> |
| ![Значок запроса на контроль хранилища класса узла](./media/user-guide/usbx-events/image182.png)    | <span data-ttu-id="4c86d-472">**Запрос на контроль хранилища класса узла** *(ux_device_class_storage_request_sense)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-472">**Host Class Storage Request Sense** *(ux_host_class_storage_request_sense)*</span></span> |
| ![Значок запуска и остановки хранилища класса узла](./media/user-guide/usbx-events/image183.png)    | <span data-ttu-id="4c86d-474">**Запуск и остановка хранилища класса узла** *(ux_device_class_storage_start_stop)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-474">**Host Class Storage Start Stop** *(ux_host_class_storage_start_stop)*</span></span> |
| ![Значок теста готовности единиц хранения для класса узла](./media/user-guide/usbx-events/image184.png)    | <span data-ttu-id="4c86d-476">**Тест готовности единиц хранения для класса узла** *(ux_host_class_storage_activate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-476">**Host Class Storage Unit Ready Test** *(ux_host_class_storage_activate)*</span></span> |
| ![Значок создания экземпляра класса стека узла](./media/user-guide/usbx-events/image185.png)    | <span data-ttu-id="4c86d-478">**Создание экземпляра класса стека узла** *(ux_host_stack_class_instance_create)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-478">**Host Stack Class Instance Create** *(ux_host_stack_class_instance_create)*</span></span> |
| ![Значок уничтожения экземпляра класса стека узла](./media/user-guide/usbx-events/image186.png)    | <span data-ttu-id="4c86d-480">**Уничтожение экземпляра класса стека узла** *(ux_host_stack_class_instance_destroy)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-480">**Host Stack Class Instance Destroy** *(ux_host_stack_class_instance_destroy)*</span></span> |
| ![Значок удаления конфигурации стека узла](./media/user-guide/usbx-events/image187.png)    | <span data-ttu-id="4c86d-482">**Удаление конфигурации стека узла** *(ux_host_stack_configuration_delete)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-482">**Host Stack Configuration Delete** *(ux_host_stack_configuration_delete)*</span></span> |
| ![Значок перечисления конфигураций стека узла](./media/user-guide/usbx-events/image188.png)    | <span data-ttu-id="4c86d-484">**Перечисление конфигураций стека узла** *(ux_host_stack_configuration_enumerate)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-484">**Host Stack Configuration Enumerate** *(ux_host_stack_configuration_enumerate)*</span></span> |
| ![Значок создания экземпляра конфигурации стека узла](./media/user-guide/usbx-events/image189.png)    | <span data-ttu-id="4c86d-486">**Создание экземпляра конфигурации стека узла** *(ux_host_stack_configuration_instance_create)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-486">**Host Stack Configuration Instance Create** *(ux_host_stack_configuration_instance_create)*</span></span> |
| ![Значок удаления экземпляра конфигурации стека узла](./media/user-guide/usbx-events/image190.png)    | <span data-ttu-id="4c86d-488">**Удаление экземпляра конфигурации стека узла** *(ux_host_stack_configuration_instance_delete)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-488">**Host Stack Configuration Instance Delete** *(ux_host_stack_configuration_instance_delete)*</span></span> |
| ![Значок набора конфигураций стека узла](./media/user-guide/usbx-events/image191.png)    | <span data-ttu-id="4c86d-490">**Набор конфигураций стека узла** *(ux_host_stack_configuration_set)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-490">**Host Stack Configuration Set** *(ux_host_stack_configuration_set)*</span></span> |
| ![Значок набора адресов устройства стека узла](./media/user-guide/usbx-events/image192.png)    | <span data-ttu-id="4c86d-492">**Набор адресов устройств стека узла** *(ux_host_stack_device_set)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-492">**Host Stack Device Address Set** *(ux_host_stack_device_set)*</span></span> |
| ![Значок получения конфигурации устройства стека узла](./media/user-guide/usbx-events/image193.png)    | <span data-ttu-id="4c86d-494">**Получение конфигурации устройства стека узла** *(ux_host_stack_device_configuration_get)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-494">**Host Stack Device Configuration Get** *(ux_host_stack_device_configuration_get)*</span></span> |
| ![Значок выбора конфигурации устройства стека узла](./media/user-guide/usbx-events/image194.png)    | <span data-ttu-id="4c86d-496">**Выбор конфигурации устройства стека узла** *(ux_host_stack_device_configuration_select)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-496">**Host Stack Device Configuration Select** *(ux_host_stack_device_configuration_select)*</span></span> |
| ![Значок считывания дескриптора устройства стека узла](./media/user-guide/usbx-events/image195.png)    | <span data-ttu-id="4c86d-498">**Считывание дескриптора устройства стека узла** *(ux_host_stack_device_descriptor_read)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-498">**Host Stack Device Descriptor Read** *(ux_host_stack_device_descriptor_read)*</span></span> |
| ![Значок получения устройства стека узла](./media/user-guide/usbx-events/image196.png)    | <span data-ttu-id="4c86d-500">**Получение устройства стека узла** (ux_host_stack_device_get)</span><span class="sxs-lookup"><span data-stu-id="4c86d-500">**Host Stack Device Get** (ux_host_stack_device_get)</span></span> |
| ![Значок удаления устройства стека узла](./media/user-guide/usbx-events/image197.png)    | <span data-ttu-id="4c86d-502">**Удаление устройства стека узла** (ux_host_stack_device_get)</span><span class="sxs-lookup"><span data-stu-id="4c86d-502">**Host Stack Device Remove** (ux_host_stack_device_get)</span></span> |
| ![Значок освобождения ресурса устройства стека узла](./media/user-guide/usbx-events/image198.png)    | <span data-ttu-id="4c86d-504">**Освобождение ресурса устройства стека узла** (ux_host_stack_device_resource_free)</span><span class="sxs-lookup"><span data-stu-id="4c86d-504">**Host Stack Device Resource Free** (ux_host_stack_device_resource_free)</span></span> |
| ![Значок создания экземпляра конечной точки стека узла](./media/user-guide/usbx-events/image199.png)    | <span data-ttu-id="4c86d-506">**Создание экземпляра конечной точки стека узла** (ux_host_stack_endpoint_instance_create)</span><span class="sxs-lookup"><span data-stu-id="4c86d-506">**Host Stack Endpoint Instance Create** (ux_host_stack_endpoint_instance_create)</span></span> |
| ![Значок удаления экземпляра конечной точки стека узла](./media/user-guide/usbx-events/image200.png)    | <span data-ttu-id="4c86d-508">**Удаление экземпляра конечной точки стека узла** (ux_host_stack_endpoint_instance_delete)</span><span class="sxs-lookup"><span data-stu-id="4c86d-508">**Host Stack Endpoint Instance Delete** (ux_host_stack_endpoint_instance_delete)</span></span> |
| ![Значок сброса конечной точки стека узла](./media/user-guide/usbx-events/image201.png)    | <span data-ttu-id="4c86d-510">**Сброс конечной точки стека узла** (ux_host_stack_endpoint_reset)</span><span class="sxs-lookup"><span data-stu-id="4c86d-510">**Host Stack Endpoint Reset** (ux_host_stack_endpoint_reset)</span></span> |
| ![Значок прерывания перемещения конечной точки стека узла](./media/user-guide/usbx-events/image202.png)    | <span data-ttu-id="4c86d-512">**Прерывание перемещения конечной точки стека узла** (ux_host_stack_endpoint_transfer_abort)</span><span class="sxs-lookup"><span data-stu-id="4c86d-512">**Host Stack Endpoint Transfer Abort** (ux_host_stack_endpoint_transfer_abort)</span></span> |
| ![Значок регистрации хост-контроллера в стеке узла](./media/user-guide/usbx-events/image203.png)    | <span data-ttu-id="4c86d-514">**Регистрация хост-контроллера в стеке узла** *(ux_host_stack_hcd_register)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-514">**Host Stack Host Controller Register** *(ux_host_stack_hcd_register)*</span></span> |
| ![Значок инициализации стека узла](./media/user-guide/usbx-events/image204.png)    | <span data-ttu-id="4c86d-516">**Инициализация стека узла** *(ux_host_stack_initialize)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-516">**Host Stack Initialize** *(ux_host_stack_initialize)*</span></span> |
| ![Значок получения конечной точки интерфейса стека узла](./media/user-guide/usbx-events/image205.png)    | <span data-ttu-id="4c86d-518">**Получение конечной точки интерфейса стека узла** *(ux_host_stack_interface_endpoint_get)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-518">**Host Stack Interface Endpoint Get** *(ux_host_stack_interface_endpoint_get)*</span></span> |
| ![Значок создания экземпляра интерфейса стека узла](./media/user-guide/usbx-events/image206.png)    | <span data-ttu-id="4c86d-520">**Создание экземпляра интерфейса стека узла** *(ux_host_stack_interface_instance_create)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-520">**Host Stack Interface Instance Create** *(ux_host_stack_interface_instance_create)*</span></span> |
| ![Значок удаления экземпляра интерфейса стека узла](./media/user-guide/usbx-events/image207.png)    | <span data-ttu-id="4c86d-522">**Удаление экземпляра интерфейса стека узла** *(ux_host_stack_interface_endpoint_get)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-522">**Host Stack Interface Instance Delete** *(ux_host_stack_interface_instance_delete)*</span></span> |
| ![Значок набора интерфейсов стека узла](./media/user-guide/usbx-events/image208.png)    | <span data-ttu-id="4c86d-524">**Набор интерфейсов стека узла** *(ux_host_stack_interface_set)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-524">**Host Stack Interface Set** *(ux_host_stack_interface_set)*</span></span> |
| ![Значок выбора параметров интерфейса стека узла](./media/user-guide/usbx-events/image209.png)    | <span data-ttu-id="4c86d-526">**Выбор параметров интерфейса стека узла** *(ux_host_stack_interface_setting_select)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-526">**Host Stack Interface Setting Select** *(ux_host_stack_interface_setting_select)*</span></span> |
| ![Значок создания конфигурации стека узла](./media/user-guide/usbx-events/image210.png)    | <span data-ttu-id="4c86d-528">**Создание конфигурации стека узла** *(ux_host_stack_new_configuration_create)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-528">**Host Stack New Configuration Create** *(ux_host_stack_new_configuration_create)*</span></span> |
| ![Значок создания устройства в стеке узла](./media/user-guide/usbx-events/image211.png)    | <span data-ttu-id="4c86d-530">**Создание устройства в стеке узла** *(ux_host_stack_new_device_create)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-530">**Host Stack New Device Create** *(ux_host_stack_new_device_create)*</span></span> |
| ![Значок создания новой конечной точки стека узла](./media/user-guide/usbx-events/image212.png)    | <span data-ttu-id="4c86d-532">**Создание новой конечной точки стека узла** *(ux_host_stack_new_endpoint_create)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-532">**Host Stack New Endpoint Create** *(ux_host_stack_new_endpoint_create)*</span></span> |
| ![Значок процесса изменения корневого концентратора стека узла](./media/user-guide/usbx-events/image213.png)    | <span data-ttu-id="4c86d-534">**Процесс изменения корневого концентратора стека узла** *(ux_host_stack_rh_change_process)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-534">**Host Stack Root Hub Change Process** *(ux_host_stack_rh_change_process)*</span></span> |
| ![Значок извлечения устройства корневого концентратора стека узла](./media/user-guide/usbx-events/image214.png)    | <span data-ttu-id="4c86d-536">**Извлечение устройства корневого концентратора стека узла** *(ux_host_stack_rh_device_extraction)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-536">**Host Stack Root Hub Device Extraction** *(ux_host_stack_rh_device_extraction)*</span></span> |
| ![Значок вставки устройства корневого концентратора стека узла](./media/user-guide/usbx-events/image215.png)    | <span data-ttu-id="4c86d-538">**Вставка устройства корневого концентратора стека узла** *(ux_host_stack_rh_device_insertion)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-538">**Host Stack Root Hub Device Insertion** *(ux_host_stack_rh_device_insertion)*</span></span> |
| ![Значок запроса на передачу стека узла](./media/user-guide/usbx-events/image216.png)    | <span data-ttu-id="4c86d-540">**Запрос на передачу стека узла** *(ux_device_stack_transfer_request)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-540">**Host Stack Transfer Request** *(ux_host_stack_transfer_request)*</span></span> |
| ![Значок прерывания запроса на передачу стека узла](./media/user-guide/usbx-events/image217.png)    | <span data-ttu-id="4c86d-542">**Прерывание запроса на передачу стека узла** *(ux_host_stack_transfer_request_abort)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-542">**Host Stack Transfer Request Abort** *(ux_host_stack_transfer_request_abort)*</span></span> |
| ![Значок ошибки USBX](./media/user-guide/usbx-events/image218.png)    | <span data-ttu-id="4c86d-544">**Ошибка USBX** *(ux_error)*</span><span class="sxs-lookup"><span data-stu-id="4c86d-544">**USBX Error** *(ux_error)*</span></span> |

## <a name="event-descriptions"></a><span data-ttu-id="4c86d-545">Описания событий</span><span class="sxs-lookup"><span data-stu-id="4c86d-545">Event Descriptions</span></span>

<span data-ttu-id="4c86d-546">На следующих страницах описаны события трассировки USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-546">The following pages describe the USBX Trace Events.</span></span>

### <a name="device-class-cdc-activate"></a><span data-ttu-id="4c86d-547">Активация класса CDC устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-547">Device Class Cdc Activate</span></span> 

#### <a name="ux_device_class_cdc_activate"></a><span data-ttu-id="4c86d-548">ux_device_class_cdc_activate</span><span class="sxs-lookup"><span data-stu-id="4c86d-548">ux_device_class_cdc_activate</span></span>

<span data-ttu-id="4c86d-549">**Значок** ![Значок активации класса CDC устройства](./media/user-guide/usbx-events/image1.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-549">**Icon** ![Device Class C D C Activate icon](./media/user-guide/usbx-events/image1.png)</span></span>

<span data-ttu-id="4c86d-550">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-550">**Description**</span></span>

<span data-ttu-id="4c86d-551">Это событие представляет собой активацию класса Cdc устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-551">This event represents a USBX Device Class Cdc Activate Event.</span></span>

<span data-ttu-id="4c86d-552">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-552">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-553">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-553">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-554">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-554">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-555">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-555">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-556">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-556">Info Field 4: Not used.</span></span>

### <a name="device-class-cdc-deactivate"></a><span data-ttu-id="4c86d-557">Деактивация класса CDC устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-557">Device Class Cdc Deactivate</span></span> 

#### <a name="ux_device_class_cdc_deactivate"></a><span data-ttu-id="4c86d-558">ux_device_class_cdc_deactivate</span><span class="sxs-lookup"><span data-stu-id="4c86d-558">ux_device_class_cdc_deactivate</span></span>

<span data-ttu-id="4c86d-559">**Значок** ![Значок деактивации класса CDC устройства](./media/user-guide/usbx-events/image2.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-559">**Icon** ![Device Class C D C Deactivate icon](./media/user-guide/usbx-events/image2.png)</span></span>

<span data-ttu-id="4c86d-560">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-560">**Description**</span></span>

<span data-ttu-id="4c86d-561">Это событие представляет собой деактивацию класса Cdc устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-561">This event represents a USBX Device Class Cdc Deactivate.</span></span>

<span data-ttu-id="4c86d-562">Поля сведений</span><span class="sxs-lookup"><span data-stu-id="4c86d-562">Information Fields</span></span> 

- <span data-ttu-id="4c86d-563">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-563">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-564">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-564">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-565">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-565">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-566">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-566">Info Field 4: Not used.</span></span>

### <a name="device-class-cdc-read"></a><span data-ttu-id="4c86d-567">Считывание класса CDC устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-567">Device Class Cdc Read</span></span> 

#### <a name="ux_device_class_cdc_read"></a><span data-ttu-id="4c86d-568">ux_device_class_cdc_read</span><span class="sxs-lookup"><span data-stu-id="4c86d-568">ux_device_class_cdc_read</span></span>

<span data-ttu-id="4c86d-569">**Значок** ![Значок считывания класса CDC устройства](./media/user-guide/usbx-events/image3.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-569">**Icon** ![Device Class C D C Read icon](./media/user-guide/usbx-events/image3.png)</span></span>

<span data-ttu-id="4c86d-570">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-570">**Description**</span></span>

<span data-ttu-id="4c86d-571">Это событие представляет собой считывание класса Cdc устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-571">This event represents a USBX Device Class Cdc Read Event.</span></span>

<span data-ttu-id="4c86d-572">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-572">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-573">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-573">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-574">Поле сведений 2. Указатель данных.</span><span class="sxs-lookup"><span data-stu-id="4c86d-574">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4c86d-575">Поле сведений 3. Запрошенная длина.</span><span class="sxs-lookup"><span data-stu-id="4c86d-575">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4c86d-576">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-576">Info Field 4: Not used.</span></span>

### <a name="device-class-cdc-write"></a><span data-ttu-id="4c86d-577">Запись класса CDC устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-577">Device Class Cdc Write</span></span> 

#### <a name="ux_device_class_cdc_write"></a><span data-ttu-id="4c86d-578">ux_device_class_cdc_write</span><span class="sxs-lookup"><span data-stu-id="4c86d-578">ux_device_class_cdc_write</span></span>

<span data-ttu-id="4c86d-579">**Значок** ![Значок записи класса CDC устройства](./media/user-guide/usbx-events/image4.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-579">**Icon** ![Device Class C D C Write icon](./media/user-guide/usbx-events/image4.png)</span></span>

<span data-ttu-id="4c86d-580">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-580">**Description**</span></span>

<span data-ttu-id="4c86d-581">Это событие представляет собой запись класса Cdc устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-581">This event represents a USBX Device Class Cdc Write Event.</span></span>

<span data-ttu-id="4c86d-582">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-582">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-583">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-583">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-584">Поле сведений 2. Указатель данных.</span><span class="sxs-lookup"><span data-stu-id="4c86d-584">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4c86d-585">Поле сведений 3. Запрошенная длина.</span><span class="sxs-lookup"><span data-stu-id="4c86d-585">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4c86d-586">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-586">Info Field 4: Not used.</span></span>

### <a name="device-class-dpump-activate"></a><span data-ttu-id="4c86d-587">Активация класса Dpump устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-587">Device Class Dpump Activate</span></span> 

#### <a name="ux_device_class_dpump_activate"></a><span data-ttu-id="4c86d-588">ux_device_class_dpump_activate</span><span class="sxs-lookup"><span data-stu-id="4c86d-588">ux_device_class_dpump_activate</span></span>

<span data-ttu-id="4c86d-589">**Значок** ![Значок активации класса Dpump устройства](./media/user-guide/usbx-events/image5.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-589">**Icon** ![Device Class Dpump Activate icon](./media/user-guide/usbx-events/image5.png)</span></span>

<span data-ttu-id="4c86d-590">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-590">**Description**</span></span>

<span data-ttu-id="4c86d-591">Это событие представляет собой активацию класса Dpump устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-591">This event represents a USBX Device Class Dpump Activate Event.</span></span>

<span data-ttu-id="4c86d-592">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-592">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-593">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-593">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-594">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-594">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-595">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-595">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-596">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-596">Info Field 4: Not used.</span></span>

### <a name="device-class-dpump-deactivate"></a><span data-ttu-id="4c86d-597">Деактивация класса Dpump устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-597">Device Class Dpump Deactivate</span></span> 

#### <a name="ux_device_class_dpump_deactivate"></a><span data-ttu-id="4c86d-598">ux_device_class_dpump_deactivate</span><span class="sxs-lookup"><span data-stu-id="4c86d-598">ux_device_class_dpump_deactivate</span></span>

<span data-ttu-id="4c86d-599">**Значок** ![Значок деактивации класса Dpump устройства](./media/user-guide/usbx-events/image6.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-599">**Icon** ![Device Class Dpump Deactivate icon](./media/user-guide/usbx-events/image6.png)</span></span>

<span data-ttu-id="4c86d-600">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-600">**Description**</span></span>

<span data-ttu-id="4c86d-601">Это событие представляет собой деактивацию класса Dpump устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-601">This event represents a USBX Device Class Dpump Deactivate Event.</span></span>

<span data-ttu-id="4c86d-602">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-602">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-603">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-603">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-604">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-604">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-605">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-605">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-606">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-606">Info Field 4: Not used.</span></span>

### <a name="device-class-dpump-read"></a><span data-ttu-id="4c86d-607">Считывание класса Dpump устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-607">Device Class Dpump Read</span></span> 

#### <a name="ux_device_class_dpump_read"></a><span data-ttu-id="4c86d-608">ux_device_class_dpump_read</span><span class="sxs-lookup"><span data-stu-id="4c86d-608">ux_device_class_dpump_read</span></span>

<span data-ttu-id="4c86d-609">**Значок** ![Значок считывания класса Dpump устройства](./media/user-guide/usbx-events/image7.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-609">**Icon** ![Device Class Dpump Read icon](./media/user-guide/usbx-events/image7.png)</span></span>

<span data-ttu-id="4c86d-610">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-610">**Description**</span></span>

<span data-ttu-id="4c86d-611">Это событие представляет собой считывание класса Dpump устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-611">This event represents a USBX Device Class Dpump Read Event.</span></span>

<span data-ttu-id="4c86d-612">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-612">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-613">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-613">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-614">Поле сведений 2. Буфер.</span><span class="sxs-lookup"><span data-stu-id="4c86d-614">Info Field 2: Buffer.</span></span>
- <span data-ttu-id="4c86d-615">Поле сведений 3. Запрошенная длина.</span><span class="sxs-lookup"><span data-stu-id="4c86d-615">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4c86d-616">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-616">Info Field 4: Not used.</span></span>

### <a name="device-class-dpump-write"></a><span data-ttu-id="4c86d-617">Запись класса Dpump устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-617">Device Class Dpump Write</span></span> 

#### <a name="ux_device_class_dpump_write"></a><span data-ttu-id="4c86d-618">ux_device_class_dpump_write</span><span class="sxs-lookup"><span data-stu-id="4c86d-618">ux_device_class_dpump_write</span></span>

<span data-ttu-id="4c86d-619">**Значок** ![Значок записи класса Dpump устройства](./media/user-guide/usbx-events/image8.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-619">**Icon** ![Device Class Dpump Write icon](./media/user-guide/usbx-events/image8.png)</span></span>

<span data-ttu-id="4c86d-620">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-620">**Description**</span></span>

<span data-ttu-id="4c86d-621">Это событие представляет собой запись класса Dpump устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-621">This event represents a USBX Device Class Dpump Write Event.</span></span>

<span data-ttu-id="4c86d-622">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-622">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-623">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-623">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-624">Поле сведений 2. Указатель данных.</span><span class="sxs-lookup"><span data-stu-id="4c86d-624">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4c86d-625">Поле сведений 3. Запрошенная длина.</span><span class="sxs-lookup"><span data-stu-id="4c86d-625">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4c86d-626">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-626">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-activate"></a><span data-ttu-id="4c86d-627">Активация класса Hid устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-627">Device Class Hid Activate</span></span> 

#### <a name="ux_device_class_hid_activate"></a><span data-ttu-id="4c86d-628">ux_device_class_hid_activate</span><span class="sxs-lookup"><span data-stu-id="4c86d-628">ux_device_class_hid_activate</span></span>

<span data-ttu-id="4c86d-629">**Значок** ![Значок активации класса Hid устройства](./media/user-guide/usbx-events/image9.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-629">**Icon** ![Device Class Hid Activate icon](./media/user-guide/usbx-events/image9.png)</span></span>

<span data-ttu-id="4c86d-630">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-630">**Description**</span></span>

<span data-ttu-id="4c86d-631">Это событие представляет собой активацию класса Hid устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-631">This event represents a USBX Device Class Hid Activate Event.</span></span>

<span data-ttu-id="4c86d-632">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-632">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-633">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-633">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-634">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-634">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-635">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-635">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-636">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-636">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-deactivate"></a><span data-ttu-id="4c86d-637">Деактивация класса Hid устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-637">Device Class Hid Deactivate</span></span> 

#### <a name="ux_device_class_hid_deactivate"></a><span data-ttu-id="4c86d-638">ux_device_class_hid_deactivate</span><span class="sxs-lookup"><span data-stu-id="4c86d-638">ux_device_class_hid_deactivate</span></span>

<span data-ttu-id="4c86d-639">**Значок** ![Значок деактивации класса Hid устройства](./media/user-guide/usbx-events/image10.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-639">**Icon** ![Device Class Hid Deactivate icon](./media/user-guide/usbx-events/image10.png)</span></span>

<span data-ttu-id="4c86d-640">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-640">**Description**</span></span>

<span data-ttu-id="4c86d-641">Это событие представляет собой деактивацию класса Hid устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-641">This event represents a USBX Device Class Hid Deactivate Event.</span></span>

<span data-ttu-id="4c86d-642">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-642">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-643">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-643">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-644">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-644">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-645">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-645">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-646">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-646">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-descriptor-send"></a><span data-ttu-id="4c86d-647">Отправка дескриптора класса Hid устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-647">Device Class Hid Descriptor Send</span></span> 

#### <a name="ux_device_class_hid_descritpor_send"></a><span data-ttu-id="4c86d-648">ux_device_class_hid_descritpor_send</span><span class="sxs-lookup"><span data-stu-id="4c86d-648">ux_device_class_hid_descritpor_send</span></span>

<span data-ttu-id="4c86d-649">**Значок** ![Значок отправки дескриптора класса Hid устройства](./media/user-guide/usbx-events/image11.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-649">**Icon** ![Device Class Hid Descriptor Send icon](./media/user-guide/usbx-events/image11.png)</span></span>

<span data-ttu-id="4c86d-650">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-650">**Description**</span></span>

<span data-ttu-id="4c86d-651">Это событие представляет собой отправку дескриптора класса Hid устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-651">This event represents a USBX Device Class Hid Descriptor Send Event.</span></span>

<span data-ttu-id="4c86d-652">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-652">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-653">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-653">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-654">Поле сведений 2. Тип дескриптора.</span><span class="sxs-lookup"><span data-stu-id="4c86d-654">Info Field 2: Descriptor type.</span></span>
- <span data-ttu-id="4c86d-655">Поле сведений 3. Индекс запроса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-655">Info Field 3: Request index.</span></span>
- <span data-ttu-id="4c86d-656">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-656">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-event-get"></a><span data-ttu-id="4c86d-657">Получение события класса Hid устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-657">Device Class Hid Event Get</span></span> 

#### <a name="ux_device_class_hid_event_get"></a><span data-ttu-id="4c86d-658">ux_device_class_hid_event_get</span><span class="sxs-lookup"><span data-stu-id="4c86d-658">ux_device_class_hid_event_get</span></span>

<span data-ttu-id="4c86d-659">**Значок** ![Значок получения события класса Hid устройства](./media/user-guide/usbx-events/image12.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-659">**Icon** ![Device Class Hid Event Get icon](./media/user-guide/usbx-events/image12.png)</span></span>

<span data-ttu-id="4c86d-660">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-660">**Description**</span></span>

<span data-ttu-id="4c86d-661">Это событие представляет собой получение события класса Hid устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-661">This event represents a USBX Device Class Hid Event Get Event.</span></span>

<span data-ttu-id="4c86d-662">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-662">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-663">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-663">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-664">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-664">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-665">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-665">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-666">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-666">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-event-set"></a><span data-ttu-id="4c86d-667">Установка события класса Hid устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-667">Device Class Hid Event Set</span></span> 

#### <a name="ux_device_class_hid_event_set"></a><span data-ttu-id="4c86d-668">ux_device_class_hid_event_set</span><span class="sxs-lookup"><span data-stu-id="4c86d-668">ux_device_class_hid_event_set</span></span>

<span data-ttu-id="4c86d-669">**Значок** ![Значок установки события класса Hid устройства](./media/user-guide/usbx-events/image13.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-669">**Icon** ![Device Class Hid Event Set icon](./media/user-guide/usbx-events/image13.png)</span></span>

<span data-ttu-id="4c86d-670">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-670">**Description**</span></span>

<span data-ttu-id="4c86d-671">Это событие представляет собой установку события класса Hid устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-671">This event represents a USBX Device Class Hid Event Set.</span></span>

<span data-ttu-id="4c86d-672">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-672">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-673">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-673">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-674">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-674">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-675">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-675">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-676">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-676">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-report-get"></a><span data-ttu-id="4c86d-677">Получение отчета класса Hid устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-677">Device Class Hid Report Get</span></span> 

#### <a name="ux_device_class_hid_report_get"></a><span data-ttu-id="4c86d-678">ux_device_class_hid_report_get</span><span class="sxs-lookup"><span data-stu-id="4c86d-678">ux_device_class_hid_report_get</span></span>

<span data-ttu-id="4c86d-679">**Значок** ![Значок получения отчета класса Hid устройства](./media/user-guide/usbx-events/image14.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-679">**Icon** ![Device Class Hid Report Get icon](./media/user-guide/usbx-events/image14.png)</span></span>

<span data-ttu-id="4c86d-680">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-680">**Description**</span></span>

<span data-ttu-id="4c86d-681">Это событие представляет собой получение отчета класса Hid устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-681">This event represents a USBX Device Class Hid Report Get Event.</span></span>

<span data-ttu-id="4c86d-682">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-682">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-683">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-683">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-684">Поле сведений 2. Тип дескриптора.</span><span class="sxs-lookup"><span data-stu-id="4c86d-684">Info Field 2: Descriptor type.</span></span>
- <span data-ttu-id="4c86d-685">Поле сведений 3. Индекс запроса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-685">Info Field 3: Request index.</span></span>
- <span data-ttu-id="4c86d-686">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-686">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-report-set"></a><span data-ttu-id="4c86d-687">Установка отчета класса Hid устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-687">Device Class Hid Report Set</span></span> 

#### <a name="ux_device_class_hid_report_set"></a><span data-ttu-id="4c86d-688">ux_device_class_hid_report_set</span><span class="sxs-lookup"><span data-stu-id="4c86d-688">ux_device_class_hid_report_set</span></span>

<span data-ttu-id="4c86d-689">**Значок** ![Значок установки отчета класса Hid устройства](./media/user-guide/usbx-events/image15.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-689">**Icon** ![Device Class Hid Report Set icon](./media/user-guide/usbx-events/image15.png)</span></span>

<span data-ttu-id="4c86d-690">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-690">**Description**</span></span>

<span data-ttu-id="4c86d-691">Это событие представляет собой установку отчета класса Hid устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-691">This event represents a USBX Device Class Hid Report Set Event.</span></span>

<span data-ttu-id="4c86d-692">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-692">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-693">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-693">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-694">Поле сведений 2. Тип дескриптора.</span><span class="sxs-lookup"><span data-stu-id="4c86d-694">Info Field 2: Descriptor type.</span></span>
- <span data-ttu-id="4c86d-695">Поле сведений 3. Индекс запроса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-695">Info Field 3: Request index.</span></span>
- <span data-ttu-id="4c86d-696">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-696">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-activate"></a><span data-ttu-id="4c86d-697">Активация класса Pima устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-697">Device Class Pima Activate</span></span>

#### <a name="ux_device_class_pima_activate"></a><span data-ttu-id="4c86d-698">ux_device_class_pima_activate</span><span class="sxs-lookup"><span data-stu-id="4c86d-698">ux_device_class_pima_activate</span></span>

<span data-ttu-id="4c86d-699">**Значок** ![Значок активации класса Pima устройства](./media/user-guide/usbx-events/image16.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-699">**Icon** ![Device Class Pima Activate icon](./media/user-guide/usbx-events/image16.png)</span></span>

<span data-ttu-id="4c86d-700">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-700">**Description**</span></span>

<span data-ttu-id="4c86d-701">Это событие представляет собой активацию класса Pima устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-701">This event represents a USBX Device Class Pima Activate Event.</span></span>

<span data-ttu-id="4c86d-702">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-702">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-703">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-703">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-704">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-704">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-705">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-705">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-706">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-706">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-deactivate"></a><span data-ttu-id="4c86d-707">Деактивация класса Pima устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-707">Device Class Pima Deactivate</span></span> 

#### <a name="ux_device_class_pima_deactivate"></a><span data-ttu-id="4c86d-708">ux_device_class_pima_deactivate</span><span class="sxs-lookup"><span data-stu-id="4c86d-708">ux_device_class_pima_deactivate</span></span>

<span data-ttu-id="4c86d-709">**Значок** ![Значок деактивации класса Pima устройства](./media/user-guide/usbx-events/image17.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-709">**Icon** ![Device Class Pima Deactivate icon](./media/user-guide/usbx-events/image17.png)</span></span>

<span data-ttu-id="4c86d-710">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-710">**Description**</span></span>

<span data-ttu-id="4c86d-711">Это событие представляет собой деактивацию класса Pima устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-711">This event represents a USBX Device Class Pima Deactivate Event.</span></span>

<span data-ttu-id="4c86d-712">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-712">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-713">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-713">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-714">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-714">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-715">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-715">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-716">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-716">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-device-info-send"></a><span data-ttu-id="4c86d-717">Отправка сведений об устройстве класса Pima устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-717">Device Class Pima Device Info Send</span></span> 

#### <a name="ux_device_class_pima_device_info_send"></a><span data-ttu-id="4c86d-718">ux_device_class_pima_device_info_send</span><span class="sxs-lookup"><span data-stu-id="4c86d-718">ux_device_class_pima_device_info_send</span></span>

<span data-ttu-id="4c86d-719">**Значок** ![Значок отправки сведений об устройстве класса Pima устройства](./media/user-guide/usbx-events/image18.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-719">**Icon** ![Device Class Pima Device Info Send icon](./media/user-guide/usbx-events/image18.png)</span></span>

<span data-ttu-id="4c86d-720">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-720">**Description**</span></span>

<span data-ttu-id="4c86d-721">Это событие представляет собой отправку сведений об устройстве класса Pima устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-721">This event represents a USBX Device Class Pima Device Info Send Event.</span></span>

<span data-ttu-id="4c86d-722">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-722">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-723">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-723">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-724">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-724">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-725">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-725">Info Field 3: Not used.</span></span>

### <a name="device-class-pima-event-get"></a><span data-ttu-id="4c86d-726">Получение события класса Pima устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-726">Device Class Pima Event Get</span></span> 

#### <a name="ux_device_class_pima_event_get"></a><span data-ttu-id="4c86d-727">ux_device_class_pima_event_get</span><span class="sxs-lookup"><span data-stu-id="4c86d-727">ux_device_class_pima_event_get</span></span>

<span data-ttu-id="4c86d-728">**Значок** ![Значок получения события класса Pima устройства](./media/user-guide/usbx-events/image19.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-728">**Icon** ![Device Class Pima Event Get icon](./media/user-guide/usbx-events/image19.png)</span></span>

<span data-ttu-id="4c86d-729">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-729">**Description**</span></span>

<span data-ttu-id="4c86d-730">Это событие представляет собой получение события класса Pima устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-730">This event represents a USBX Device Class Pima Event Get Event.</span></span>

<span data-ttu-id="4c86d-731">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-731">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-732">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-732">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-733">Поле сведений 2. Событие Pima.</span><span class="sxs-lookup"><span data-stu-id="4c86d-733">Info Field 2: Pima event.</span></span>
- <span data-ttu-id="4c86d-734">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-734">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-735">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-735">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-event-set"></a><span data-ttu-id="4c86d-736">Установка события класса Pima устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-736">Device Class Pima Event Set</span></span> 

#### <a name="ux_device_class_pima_event_set"></a><span data-ttu-id="4c86d-737">ux_device_class_pima_event_set</span><span class="sxs-lookup"><span data-stu-id="4c86d-737">ux_device_class_pima_event_set</span></span>

<span data-ttu-id="4c86d-738">**Значок** ![Значок установки события класса Pima устройства](./media/user-guide/usbx-events/image20.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-738">**Icon** ![Device Class Pima Event Set icon](./media/user-guide/usbx-events/image20.png)</span></span>

<span data-ttu-id="4c86d-739">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-739">**Description**</span></span>

<span data-ttu-id="4c86d-740">Это событие представляет собой установку события класса Pima устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-740">This event represents a USBX Device Class Pima Event Set Event.</span></span>

<span data-ttu-id="4c86d-741">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-741">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-742">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-742">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-743">Поле сведений 2. Событие Pima.</span><span class="sxs-lookup"><span data-stu-id="4c86d-743">Info Field 2: Pima event.</span></span>
- <span data-ttu-id="4c86d-744">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-744">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-745">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-745">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-add"></a><span data-ttu-id="4c86d-746">Добавление объекта в класс Pima устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-746">Device Class Pima Object Add</span></span> 

#### <a name="ux_device_class_pima_object_add"></a><span data-ttu-id="4c86d-747">ux_device_class_pima_object_add</span><span class="sxs-lookup"><span data-stu-id="4c86d-747">ux_device_class_pima_object_add</span></span>

<span data-ttu-id="4c86d-748">**Значок** ![Значок добавления объекта в класс Pima устройства](./media/user-guide/usbx-events/image21.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-748">**Icon** ![Device Class Pima Object Add icon](./media/user-guide/usbx-events/image21.png)</span></span>

<span data-ttu-id="4c86d-749">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-749">**Description**</span></span>

<span data-ttu-id="4c86d-750">Это событие представляет собой добавление объекта класса Pima устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-750">This event represents a USBX Device Class Pima Object Add Event.</span></span>

<span data-ttu-id="4c86d-751">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-751">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-752">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-752">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-753">Поле сведений 2. Дескриптор объекта.</span><span class="sxs-lookup"><span data-stu-id="4c86d-753">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4c86d-754">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-754">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-755">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-755">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-data-get"></a><span data-ttu-id="4c86d-756">Получение данных объекта в классе Pima устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-756">Device Class Pima Object Data Get</span></span> 

#### <a name="ux_device_class_pima_object_data_get"></a><span data-ttu-id="4c86d-757">ux_device_class_pima_object_data_get</span><span class="sxs-lookup"><span data-stu-id="4c86d-757">ux_device_class_pima_object_data_get</span></span>

<span data-ttu-id="4c86d-758">**Значок** ![Значок получения данных объекта класса Pima устройства](./media/user-guide/usbx-events/image22.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-758">**Icon** ![Device Class Pima Object Data Get icon](./media/user-guide/usbx-events/image22.png)</span></span>

<span data-ttu-id="4c86d-759">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-759">**Description**</span></span>

<span data-ttu-id="4c86d-760">Это событие представляет собой получение данных объекта класса Pima устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-760">This event represents a USBX Device Class Pima Object Data Get Event.</span></span>

<span data-ttu-id="4c86d-761">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-761">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-762">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-762">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-763">Поле сведений 2. Дескриптор объекта.</span><span class="sxs-lookup"><span data-stu-id="4c86d-763">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4c86d-764">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-764">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-765">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-765">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-data-send"></a><span data-ttu-id="4c86d-766">Отправка данных объекта класса Pima устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-766">Device Class Pima Object Data Send</span></span> 

#### <a name="ux_device_class_pima_object_data_send"></a><span data-ttu-id="4c86d-767">ux_device_class_pima_object_data_send</span><span class="sxs-lookup"><span data-stu-id="4c86d-767">ux_device_class_pima_object_data_send</span></span>

<span data-ttu-id="4c86d-768">**Значок** ![Значок отправки данных объекта класса Pima устройства](./media/user-guide/usbx-events/image23.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-768">**Icon** ![Device Class Pima Object Data Send icon](./media/user-guide/usbx-events/image23.png)</span></span>

<span data-ttu-id="4c86d-769">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-769">**Description**</span></span>

<span data-ttu-id="4c86d-770">Это событие представляет собой отправку данных объекта класса Pima устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-770">This event represents a USBX Device Class Pima Object Data Send Event.</span></span>

<span data-ttu-id="4c86d-771">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-771">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-772">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-772">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-773">Поле сведений 2. Дескриптор объекта.</span><span class="sxs-lookup"><span data-stu-id="4c86d-773">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4c86d-774">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-774">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-775">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-775">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-delete"></a><span data-ttu-id="4c86d-776">Удаление объекта класса Pima устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-776">Device Class Pima Object Delete</span></span> 

#### <a name="ux_device_class_pima_object_delete"></a><span data-ttu-id="4c86d-777">ux_device_class_pima_object_delete</span><span class="sxs-lookup"><span data-stu-id="4c86d-777">ux_device_class_pima_object_delete</span></span>

<span data-ttu-id="4c86d-778">**Значок** ![Значок удаления объекта класса Pima устройства](./media/user-guide/usbx-events/image24.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-778">**Icon** ![Device Class Pima Object Delete icon](./media/user-guide/usbx-events/image24.png)</span></span>

<span data-ttu-id="4c86d-779">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-779">**Description**</span></span>

<span data-ttu-id="4c86d-780">Это событие представляет собой удаление объекта класса Pima устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-780">This event represents a USBX Device Class Pima Object Delete Event.</span></span>

<span data-ttu-id="4c86d-781">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-781">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-782">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-782">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-783">Поле сведений 2. Дескриптор объекта.</span><span class="sxs-lookup"><span data-stu-id="4c86d-783">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4c86d-784">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-784">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-785">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-785">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-handles-send"></a><span data-ttu-id="4c86d-786">Отправка дескрипторов объекта класса Pima устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-786">Device Class Pima Object Handles Send</span></span> 

#### <a name="ux_device_class_pima_object_handles_send"></a><span data-ttu-id="4c86d-787">ux_device_class_pima_object_handles_send</span><span class="sxs-lookup"><span data-stu-id="4c86d-787">ux_device_class_pima_object_handles_send</span></span>

<span data-ttu-id="4c86d-788">**Значок** ![Значок отправки дескрипторов объекта класса Pima устройства](./media/user-guide/usbx-events/image25.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-788">**Icon** ![Device Class Pima Object Handles Send icon](./media/user-guide/usbx-events/image25.png)</span></span>

<span data-ttu-id="4c86d-789">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-789">**Description**</span></span>

<span data-ttu-id="4c86d-790">Это событие представляет собой отправку дескрипторов объекта класса Pima устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-790">This event represents a USBX Device Class Pima Object Handles Send Event.</span></span>

<span data-ttu-id="4c86d-791">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-791">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-792">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-792">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-793">Поле сведений 2. Идентификатор хранилища.</span><span class="sxs-lookup"><span data-stu-id="4c86d-793">Info Field 2: Storage ID.</span></span>
- <span data-ttu-id="4c86d-794">Поле сведений 3. Код формата объекта.</span><span class="sxs-lookup"><span data-stu-id="4c86d-794">Info Field 3: Object format code.</span></span>
- <span data-ttu-id="4c86d-795">Поле сведений 4. Связь между объектами.</span><span class="sxs-lookup"><span data-stu-id="4c86d-795">Info Field 4: Object association.</span></span>

### <a name="device-class-pima-object-info-get"></a><span data-ttu-id="4c86d-796">Получение сведений об объекте класса Pima устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-796">Device Class Pima Object Info Get</span></span> 

#### <a name="ux_device_class_pima_object_info_send"></a><span data-ttu-id="4c86d-797">ux_device_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="4c86d-797">ux_device_class_pima_object_info_send</span></span>

<span data-ttu-id="4c86d-798">**Значок** ![Значок получения сведений об объекте класса Pima устройства](./media/user-guide/usbx-events/image26.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-798">**Icon** ![Device Class Pima Object Info Get icon](./media/user-guide/usbx-events/image26.png)</span></span>

<span data-ttu-id="4c86d-799">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-799">**Description**</span></span>

<span data-ttu-id="4c86d-800">Это событие представляет собой получение сведений об объекте класса Pima устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-800">This event represents a USBX Device Class Pima Object Info Get Event.</span></span>

<span data-ttu-id="4c86d-801">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-801">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-802">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-802">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-803">Поле сведений 2. Дескриптор объекта.</span><span class="sxs-lookup"><span data-stu-id="4c86d-803">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4c86d-804">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-804">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-805">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-805">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-info-send"></a><span data-ttu-id="4c86d-806">Отправка сведений об объекте класса Pima устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-806">Device Class Pima Object Info Send</span></span> 

#### <a name="ux_device_class_pima_object_info_send"></a><span data-ttu-id="4c86d-807">ux_device_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="4c86d-807">ux_device_class_pima_object_info_send</span></span>

<span data-ttu-id="4c86d-808">**Значок** ![Значок отправки сведений об объекте класса Pima устройства](./media/user-guide/usbx-events/image27.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-808">**Icon** ![Device Class Pima Object Info Send icon](./media/user-guide/usbx-events/image27.png)</span></span>

<span data-ttu-id="4c86d-809">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-809">**Description**</span></span>

<span data-ttu-id="4c86d-810">Это событие представляет собой отправку сведений об объекте класса Pima устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-810">This event represents a USBX Device Class Pima Object Info Send Event.</span></span>

<span data-ttu-id="4c86d-811">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-811">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-812">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-812">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-813">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-813">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-814">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-814">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-815">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-815">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-objects-number-send"></a><span data-ttu-id="4c86d-816">Отправка номера объектов класса Pima устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-816">Device Class Pima Objects Number Send</span></span> 

#### <a name="ux_device_class_pima_object_number_send"></a><span data-ttu-id="4c86d-817">ux_device_class_pima_object_number_send</span><span class="sxs-lookup"><span data-stu-id="4c86d-817">ux_device_class_pima_object_number_send</span></span>

<span data-ttu-id="4c86d-818">**Значок** ![Значок отправки номера объектов класса Pima устройства](./media/user-guide/usbx-events/image28.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-818">**Icon** ![Device Class Pima Objects Number Send icon](./media/user-guide/usbx-events/image28.png)</span></span>

<span data-ttu-id="4c86d-819">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-819">**Description**</span></span>

<span data-ttu-id="4c86d-820">Это событие представляет собой отправку номера объекта класса Pima устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-820">This event represents a USBX Device Class Pima Object Number Send event.</span></span>

<span data-ttu-id="4c86d-821">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-821">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-822">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-822">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-823">Поле сведений 2. Идентификатор хранилища.</span><span class="sxs-lookup"><span data-stu-id="4c86d-823">Info Field 2: Storage ID.</span></span>
- <span data-ttu-id="4c86d-824">Поле сведений 3. Код формата объекта.</span><span class="sxs-lookup"><span data-stu-id="4c86d-824">Info Field 3: Object format code.</span></span>
- <span data-ttu-id="4c86d-825">Поле сведений 4. Связь объекта.</span><span class="sxs-lookup"><span data-stu-id="4c86d-825">Info Field 4: Object associate.</span></span>

### <a name="device-class-pima-partial-object-data-get"></a><span data-ttu-id="4c86d-826">Получение частичных данных объекта класса Pima устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-826">Device Class Pima Partial Object Data Get</span></span>

#### <a name="ux_device_class_pima_partial_object_data_get"></a><span data-ttu-id="4c86d-827">ux_device_class_pima_partial_object_data_get</span><span class="sxs-lookup"><span data-stu-id="4c86d-827">ux_device_class_pima_partial_object_data_get</span></span>

<span data-ttu-id="4c86d-828">**Значок** ![Значок получения частичных данных объекта класса Pima устройства](./media/user-guide/usbx-events/image29.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-828">**Icon** ![Device Class Pima Partial Object Data Get icon](./media/user-guide/usbx-events/image29.png)</span></span>

<span data-ttu-id="4c86d-829">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-829">**Description**</span></span>

<span data-ttu-id="4c86d-830">Это событие представляет собой получение частичных данных объекта класса Pima устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-830">This event represents a USBX Device Class Pima Partial Object Data Get Event.</span></span>

<span data-ttu-id="4c86d-831">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-831">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-832">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-832">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-833">Поле сведений 2. Дескриптор объекта.</span><span class="sxs-lookup"><span data-stu-id="4c86d-833">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4c86d-834">Поле сведений 3. Запрос на смещение выполнен.</span><span class="sxs-lookup"><span data-stu-id="4c86d-834">Info Field 3: Offset requested.</span></span>
- <span data-ttu-id="4c86d-835">Поле сведений 4. Запрос на получение сведений о длине выполнен.</span><span class="sxs-lookup"><span data-stu-id="4c86d-835">Info Field 4: Length requested.</span></span>

### <a name="device-class-pima-response-send"></a><span data-ttu-id="4c86d-836">Отправка отклика класса Pima устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-836">Device Class Pima Response Send</span></span> 

#### <a name="ux_device_class_pima_response_send"></a><span data-ttu-id="4c86d-837">ux_device_class_pima_response_send</span><span class="sxs-lookup"><span data-stu-id="4c86d-837">ux_device_class_pima_response_send</span></span>

<span data-ttu-id="4c86d-838">**Значок** ![Значок отправки отклика класса Pima устройства](./media/user-guide/usbx-events/image30.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-838">**Icon** ![Device Class Pima Response Send icon](./media/user-guide/usbx-events/image30.png)</span></span>

<span data-ttu-id="4c86d-839">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-839">**Description**</span></span>

<span data-ttu-id="4c86d-840">Это событие представляет собой отправку отклика класса Pima устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-840">This event represents a USBX Device Class Pima Response Send Event.</span></span>

<span data-ttu-id="4c86d-841">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-841">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-842">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-842">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-843">Поле сведений 2. Код отклика.</span><span class="sxs-lookup"><span data-stu-id="4c86d-843">Info Field 2: Response code.</span></span>
- <span data-ttu-id="4c86d-844">Поле сведений 3. Числовой параметр.</span><span class="sxs-lookup"><span data-stu-id="4c86d-844">Info Field 3: Number parameter.</span></span>
- <span data-ttu-id="4c86d-845">Поле сведений 4. Параметр 1 Pima.</span><span class="sxs-lookup"><span data-stu-id="4c86d-845">Info Field 4: Pima parameter 1.</span></span>

### <a name="device-class-pima-storage-id-send"></a><span data-ttu-id="4c86d-846">Отправка идентификатора хранилища класса Pima устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-846">Device Class Pima Storage Id Send</span></span> 

#### <a name="ux_device_class_pima_storage_id_send"></a><span data-ttu-id="4c86d-847">ux_device_class_pima_storage_id_send</span><span class="sxs-lookup"><span data-stu-id="4c86d-847">ux_device_class_pima_storage_id_send</span></span>

<span data-ttu-id="4c86d-848">**Значок** ![Значок отправки идентификатора хранилища класса Pima устройства](./media/user-guide/usbx-events/image31.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-848">**Icon** ![Device Class Pima Storage Id Send icon](./media/user-guide/usbx-events/image31.png)</span></span>

<span data-ttu-id="4c86d-849">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-849">**Description**</span></span>

<span data-ttu-id="4c86d-850">Это событие представляет собой отправку идентификатора хранилища класса Pima устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-850">This event represents a USBX Device Class Pima Storage Id Send Event.</span></span>

<span data-ttu-id="4c86d-851">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-851">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-852">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-852">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-853">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-853">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-854">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-854">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-855">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-855">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-storage-info-send"></a><span data-ttu-id="4c86d-856">Отправка сведений о хранилище класса Pima устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-856">Device Class Pima Storage Info Send</span></span> 

#### <a name="ux_device_class_pima_storage_info_send"></a><span data-ttu-id="4c86d-857">ux_device_class_pima_storage_info_send</span><span class="sxs-lookup"><span data-stu-id="4c86d-857">ux_device_class_pima_storage_info_send</span></span>

<span data-ttu-id="4c86d-858">**Значок** ![Значок отправки сведений о хранилище класса Pima устройства](./media/user-guide/usbx-events/image32.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-858">**Icon** ![Device Class Pima Storage Info Send icon](./media/user-guide/usbx-events/image32.png)</span></span>

<span data-ttu-id="4c86d-859">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-859">**Description**</span></span>

<span data-ttu-id="4c86d-860">Это событие представляет собой отправку сведений о хранилище класса Pima устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-860">This event represents a USBX Device Class Pima Storage Info Send Event.</span></span>

<span data-ttu-id="4c86d-861">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-861">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-862">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-862">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-863">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-863">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-864">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-864">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-865">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-865">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-activate"></a><span data-ttu-id="4c86d-866">Активация класса Rndis устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-866">Device Class Rndis Activate</span></span> 

#### <a name="ux_device_class_rndis_activate"></a><span data-ttu-id="4c86d-867">ux_device_class_rndis_activate</span><span class="sxs-lookup"><span data-stu-id="4c86d-867">ux_device_class_rndis_activate</span></span>

<span data-ttu-id="4c86d-868">**Значок** ![Значок активации класса Rndis устройства](./media/user-guide/usbx-events/image33.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-868">**Icon** ![Device Class Rndis Activate icon](./media/user-guide/usbx-events/image33.png)</span></span>

<span data-ttu-id="4c86d-869">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-869">**Description**</span></span>

<span data-ttu-id="4c86d-870">Это событие представляет собой активацию класса Rndis устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-870">This event represents a USBX Device Class Rndis Activate Event.</span></span>

<span data-ttu-id="4c86d-871">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-871">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-872">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-872">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-873">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-873">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-874">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-874">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-875">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-875">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-deactivate"></a><span data-ttu-id="4c86d-876">Деактивация класса Rndis устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-876">Device Class Rndis Deactivate</span></span> 

#### <a name="ux_device_class_rndis_deactivate"></a><span data-ttu-id="4c86d-877">ux_device_class_rndis_deactivate</span><span class="sxs-lookup"><span data-stu-id="4c86d-877">ux_device_class_rndis_deactivate</span></span>

<span data-ttu-id="4c86d-878">**Значок** ![Значок деактивации класса Rndis устройства](./media/user-guide/usbx-events/image34.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-878">**Icon** ![Device Class Rndis Deactivate icon](./media/user-guide/usbx-events/image34.png)</span></span>

<span data-ttu-id="4c86d-879">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-879">**Description**</span></span>

<span data-ttu-id="4c86d-880">Это событие представляет собой деактивацию класса Rndis устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-880">This event represents a USBX Device Class Rndis Deactivate Event.</span></span>

<span data-ttu-id="4c86d-881">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-881">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-882">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-882">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-883">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-883">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-884">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-884">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-885">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-885">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-message-keep-alive"></a><span data-ttu-id="4c86d-886">Проверка активности сообщений класса Rndis устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-886">Device Class Rndis Message Keep Alive</span></span> 

#### <a name="ux_device_class_rndis_msg_keep_alive"></a><span data-ttu-id="4c86d-887">uux_device_class_rndis_msg_keep_alive</span><span class="sxs-lookup"><span data-stu-id="4c86d-887">ux_device_class_rndis_msg_keep_alive</span></span>

<span data-ttu-id="4c86d-888">**Значок** ![Значок проверки активности сообщений класса Rndis устройства](./media/user-guide/usbx-events/image35.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-888">**Icon** ![Device Class Rndis Message Keep Alive icon](./media/user-guide/usbx-events/image35.png)</span></span>

<span data-ttu-id="4c86d-889">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-889">**Description**</span></span>

<span data-ttu-id="4c86d-890">Это событие представляет собой проверку активности сообщений класса Rndis устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-890">This event represents a USBX Device Class Rndis Message Keep Alive Event.</span></span>

<span data-ttu-id="4c86d-891">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-891">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-892">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-892">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-893">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-893">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-894">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-894">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-895">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-895">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-message-query"></a><span data-ttu-id="4c86d-896">Запрос на сообщение класса Rndis устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-896">Device Class Rndis Message Query</span></span> 

#### <a name="ux_device_class_rndis_msg_keep_query"></a><span data-ttu-id="4c86d-897">ux_device_class_rndis_msg_keep_query</span><span class="sxs-lookup"><span data-stu-id="4c86d-897">ux_device_class_rndis_msg_keep_query</span></span>

<span data-ttu-id="4c86d-898">**Значок** ![Значок запроса на сообщение класса Rndis устройства](./media/user-guide/usbx-events/image36.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-898">**Icon** ![Device Class Rndis Message Query icon](./media/user-guide/usbx-events/image36.png)</span></span>

<span data-ttu-id="4c86d-899">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-899">**Description**</span></span>

<span data-ttu-id="4c86d-900">Это событие представляет собой запрос на сообщение класса Rndis устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-900">This event represents a USBX Device Class Rndis Message Query Event.</span></span>

<span data-ttu-id="4c86d-901">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-901">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-902">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-902">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-903">Поле сведений 2. Rndis OID.</span><span class="sxs-lookup"><span data-stu-id="4c86d-903">Info Field 2: Rndis OID.</span></span>
- <span data-ttu-id="4c86d-904">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-904">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-905">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-905">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-message-reset"></a><span data-ttu-id="4c86d-906">Сброс сообщения класса Rndis устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-906">Device Class Rndis Message Reset</span></span> 

#### <a name="ux_device_class_rndis_msg_reset"></a><span data-ttu-id="4c86d-907">ux_device_class_rndis_msg_reset</span><span class="sxs-lookup"><span data-stu-id="4c86d-907">ux_device_class_rndis_msg_reset</span></span>

<span data-ttu-id="4c86d-908">**Значок** ![Значок сброса сообщения класса Rndis устройства](./media/user-guide/usbx-events/image37.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-908">**Icon** ![Device Class Rndis Message Reset icon](./media/user-guide/usbx-events/image37.png)</span></span>

<span data-ttu-id="4c86d-909">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-909">**Description**</span></span>

<span data-ttu-id="4c86d-910">Это событие представляет собой сброс сообщения класса Rndis устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-910">This event represents a USBX Device Class Rndis Message Reset Event.</span></span>

<span data-ttu-id="4c86d-911">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-911">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-912">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-912">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-913">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-913">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-914">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-914">Info Field 3: Not used.</span></span>

### <a name="device-class-rndis-message-set"></a><span data-ttu-id="4c86d-915">Набор сообщений класса Rndis устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-915">Device Class Rndis Message Set</span></span> 

#### <a name="ux_device_class_rndis_msg_set"></a><span data-ttu-id="4c86d-916">ux_device_class_rndis_msg_set</span><span class="sxs-lookup"><span data-stu-id="4c86d-916">ux_device_class_rndis_msg_set</span></span>

<span data-ttu-id="4c86d-917">**Значок** ![Значок набора сообщений класса Rndis устройства](./media/user-guide/usbx-events/image38.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-917">**Icon** ![Device Class Rndis Message Set icon](./media/user-guide/usbx-events/image38.png)</span></span>

<span data-ttu-id="4c86d-918">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-918">**Description**</span></span>

<span data-ttu-id="4c86d-919">Это событие представляет собой событие набора сообщений класса Rndis устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-919">This event represents a USBX Device Class Rndis Message Set Event.</span></span>

<span data-ttu-id="4c86d-920">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-920">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-921">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-921">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-922">Поле сведений 2. Rndis OID.</span><span class="sxs-lookup"><span data-stu-id="4c86d-922">Info Field 2: Rndis OID.</span></span>
- <span data-ttu-id="4c86d-923">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-923">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-924">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-924">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-packet-receive"></a><span data-ttu-id="4c86d-925">Получения пакета класса Rndis устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-925">Device Class Rndis Packet Receive</span></span> 

#### <a name="ux_device_class_rndis_packet_receive"></a><span data-ttu-id="4c86d-926">ux_device_class_rndis_packet_receive</span><span class="sxs-lookup"><span data-stu-id="4c86d-926">ux_device_class_rndis_packet_receive</span></span>

<span data-ttu-id="4c86d-927">**Значок** ![Значок получения пакета класса Rndis устройства](./media/user-guide/usbx-events/image39.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-927">**Icon** ![Device Class Rndis Packet Receive icon](./media/user-guide/usbx-events/image39.png)</span></span>

<span data-ttu-id="4c86d-928">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-928">**Description**</span></span>

<span data-ttu-id="4c86d-929">Это событие представляет собой получение пакета класса Rndis устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-929">This event represents a USBX Device Class Rndis Packet Receive Event.</span></span>

<span data-ttu-id="4c86d-930">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-930">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-931">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-931">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-932">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-932">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-933">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-933">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-934">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-934">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-packet-transmit"></a><span data-ttu-id="4c86d-935">Передача пакета класса Rndis устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-935">Device Class Rndis Packet Transmit</span></span> 

#### <a name="ux_device_class_rndis_packet_transmit"></a><span data-ttu-id="4c86d-936">ux_device_class_rndis_packet_transmit</span><span class="sxs-lookup"><span data-stu-id="4c86d-936">ux_device_class_rndis_packet_transmit</span></span>

<span data-ttu-id="4c86d-937">**Значок** ![Значок передачи пакета класса Rndis устройства](./media/user-guide/usbx-events/image40.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-937">**Icon** ![Device Class Rndis Packet Transmit icon](./media/user-guide/usbx-events/image40.png)</span></span>

<span data-ttu-id="4c86d-938">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-938">**Description**</span></span>

<span data-ttu-id="4c86d-939">Это событие представляет собой передачу пакета класса Rndis устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-939">This event represents a USBX Device Class Rndis Packet Transmit Event.</span></span>

<span data-ttu-id="4c86d-940">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-940">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-941">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-941">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-942">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-942">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-943">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-943">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-944">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-944">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-activate"></a><span data-ttu-id="4c86d-945">Активация хранилища класса устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-945">Device Class Storage Activate</span></span> 

#### <a name="ux_device_class_storage_activate"></a><span data-ttu-id="4c86d-946">ux_device_class_storage_activate</span><span class="sxs-lookup"><span data-stu-id="4c86d-946">ux_device_class_storage_activate</span></span>

<span data-ttu-id="4c86d-947">**Значок** ![Значок активации хранилища класса устройства](./media/user-guide/usbx-events/image41.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-947">**Icon** ![Device Class Storage Activate icon](./media/user-guide/usbx-events/image41.png)</span></span>

<span data-ttu-id="4c86d-948">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-948">**Description**</span></span>

<span data-ttu-id="4c86d-949">Это событие представляет собой активацию хранилища класса устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-949">This event represents a USBX Device Class Storage Activate Event.</span></span>

<span data-ttu-id="4c86d-950">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-950">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-951">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-951">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-952">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-952">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-953">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-953">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-954">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-954">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-deactivate"></a><span data-ttu-id="4c86d-955">Деактивация хранилища класса устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-955">Device Class Storage Deactivate</span></span> 

#### <a name="ux_device_class_storage_deactivate"></a><span data-ttu-id="4c86d-956">ux_device_class_storage_deactivate</span><span class="sxs-lookup"><span data-stu-id="4c86d-956">ux_device_class_storage_deactivate</span></span>

<span data-ttu-id="4c86d-957">**Значок** ![Значок деактивации хранилища класса устройства](./media/user-guide/usbx-events/image42.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-957">**Icon** ![Device Class Storage Deactivate icon](./media/user-guide/usbx-events/image42.png)</span></span>

<span data-ttu-id="4c86d-958">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-958">**Description**</span></span>

<span data-ttu-id="4c86d-959">Это событие представляет собой деактивацию хранилища класса устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-959">This event represents a USBX Device Class Storage Deactivate Event.</span></span>

<span data-ttu-id="4c86d-960">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-960">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-961">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-961">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-962">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-962">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-963">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-963">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-964">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-964">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-format"></a><span data-ttu-id="4c86d-965">Формат хранилища класса устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-965">Device Class Storage Format</span></span> 

#### <a name="ux_device_class_storage_format"></a><span data-ttu-id="4c86d-966">ux_device_class_storage_format</span><span class="sxs-lookup"><span data-stu-id="4c86d-966">ux_device_class_storage_format</span></span>

<span data-ttu-id="4c86d-967">**Значок** ![Значок формата хранилища класса устройства](./media/user-guide/usbx-events/image43.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-967">**Icon** ![Device Class Storage Format icon](./media/user-guide/usbx-events/image43.png)</span></span>

<span data-ttu-id="4c86d-968">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-968">**Description**</span></span>

<span data-ttu-id="4c86d-969">Это событие представляет собой событие формата хранилища класса устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-969">This event represents a USBX Device Class Storage Format Event.</span></span>

<span data-ttu-id="4c86d-970">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-970">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-971">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-971">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-972">Поле сведений 2. Номер логического устройства (LUN).</span><span class="sxs-lookup"><span data-stu-id="4c86d-972">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4c86d-973">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-973">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-974">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-974">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-inquiry"></a><span data-ttu-id="4c86d-975">Запрос хранилища класса устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-975">Device Class Storage Inquiry</span></span> 

#### <a name="ux_device_class_storage_inquiry"></a><span data-ttu-id="4c86d-976">ux_device_class_storage_inquiry</span><span class="sxs-lookup"><span data-stu-id="4c86d-976">ux_device_class_storage_inquiry</span></span>

<span data-ttu-id="4c86d-977">**Значок** ![Значок запроса хранилища класса устройства](./media/user-guide/usbx-events/image44.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-977">**Icon** ![Device Class Storage Inquiry icon](./media/user-guide/usbx-events/image44.png)</span></span>

<span data-ttu-id="4c86d-978">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-978">**Description**</span></span>

<span data-ttu-id="4c86d-979">Это событие представляет собой запрос хранилища класса устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-979">This event represents a USBX Device Class Storage Inquiry Event.</span></span>

<span data-ttu-id="4c86d-980">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-980">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-981">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-981">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-982">Поле сведений 2. Номер логического устройства (LUN).</span><span class="sxs-lookup"><span data-stu-id="4c86d-982">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4c86d-983">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-983">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-984">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-984">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-mode-select"></a><span data-ttu-id="4c86d-985">Выбор режима хранения класса устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-985">Device Class Storage Mode Select</span></span>

#### <a name="ux_device_class_storage_mode_select"></a><span data-ttu-id="4c86d-986">ux_device_class_storage_mode_select</span><span class="sxs-lookup"><span data-stu-id="4c86d-986">ux_device_class_storage_mode_select</span></span>

<span data-ttu-id="4c86d-987">**Значок** ![Значок выбора режима хранения класса устройства](./media/user-guide/usbx-events/image45.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-987">**Icon** ![Device Class Storage Mode Select icon](./media/user-guide/usbx-events/image45.png)</span></span>

<span data-ttu-id="4c86d-988">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-988">**Description**</span></span>

<span data-ttu-id="4c86d-989">Это событие представляет собой выбор режима хранения класса устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-989">This event represents a USBX Device Class Storage Mode Select Event.</span></span>

<span data-ttu-id="4c86d-990">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-990">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-991">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-991">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-992">Поле сведений 2. Номер логического устройства (LUN).</span><span class="sxs-lookup"><span data-stu-id="4c86d-992">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4c86d-993">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-993">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-994">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-994">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-mode-sense"></a><span data-ttu-id="4c86d-995">Контроль режима хранения класса устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-995">Device Class Storage Mode Sense</span></span> 

#### <a name="ux_device_class_storage_mode_sense"></a><span data-ttu-id="4c86d-996">ux_device_class_storage_mode_sense</span><span class="sxs-lookup"><span data-stu-id="4c86d-996">ux_device_class_storage_mode_sense</span></span>

<span data-ttu-id="4c86d-997">**Значок** ![Значок контроля режима хранения класса устройства](./media/user-guide/usbx-events/image46.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-997">**Icon** ![Device Class Storage Mode Sense icon](./media/user-guide/usbx-events/image46.png)</span></span>

<span data-ttu-id="4c86d-998">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-998">**Description**</span></span>

<span data-ttu-id="4c86d-999">Это событие представляет собой контроль режима хранения класса устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-999">This event represents a USBX Device Class Storage Mode Sense Event.</span></span>

<span data-ttu-id="4c86d-1000">Поля сведений</span><span class="sxs-lookup"><span data-stu-id="4c86d-1000">Information Fields</span></span> 

- <span data-ttu-id="4c86d-1001">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1001">nfo Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-1002">Поле сведений 2. Номер логического устройства (LUN).</span><span class="sxs-lookup"><span data-stu-id="4c86d-1002">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4c86d-1003">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1003">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1004">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1004">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-prevent-allow-media-removal"></a><span data-ttu-id="4c86d-1005">Запрет на удаление носителей в хранилище класса устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-1005">Device Class Storage Prevent Allow Media Removal</span></span> 

#### <a name="ux_device_class_storage_prevent_allow_media_removal"></a><span data-ttu-id="4c86d-1006">ux_device_class_storage_prevent_allow_media_removal</span><span class="sxs-lookup"><span data-stu-id="4c86d-1006">ux_device_class_storage_prevent_allow_media_removal</span></span>

<span data-ttu-id="4c86d-1007">**Значок** ![Значок запрета на удаление носителей в хранилище класса устройства](./media/user-guide/usbx-events/image47.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1007">**Icon** ![Device Class Storage Prevent Allow Media Removal icon](./media/user-guide/usbx-events/image47.png)</span></span>

<span data-ttu-id="4c86d-1008">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1008">**Description**</span></span>

<span data-ttu-id="4c86d-1009">Это событие представляет собой запрет на удаление носителей в хранилище класса устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1009">This event represents a USBX Device Class Storage Prevent Allow Media Removal Event.</span></span>

<span data-ttu-id="4c86d-1010">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1010">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1011">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1011">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-1012">Поле сведений 2. Номер логического устройства (LUN).</span><span class="sxs-lookup"><span data-stu-id="4c86d-1012">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4c86d-1013">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1013">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1014">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1014">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-read"></a><span data-ttu-id="4c86d-1015">Считывание хранилища класса устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-1015">Device Class Storage Read</span></span> 

#### <a name="ux_device_class_storage_read"></a><span data-ttu-id="4c86d-1016">ux_device_class_storage_read</span><span class="sxs-lookup"><span data-stu-id="4c86d-1016">ux_device_class_storage_read</span></span>

<span data-ttu-id="4c86d-1017">**Значок** ![Значок считывания хранилища класса устройства](./media/user-guide/usbx-events/image48.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1017">**Icon** ![Device Class Storage Read icon](./media/user-guide/usbx-events/image48.png)</span></span>

<span data-ttu-id="4c86d-1018">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1018">**Description**</span></span>

<span data-ttu-id="4c86d-1019">Это событие представляет собой считывание хранилища класса устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1019">This event represents a USBX Device Class Storage Read Event.</span></span>

<span data-ttu-id="4c86d-1020">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1020">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1021">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1021">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-1022">Поле сведений 2. Номер логического устройства (LUN).</span><span class="sxs-lookup"><span data-stu-id="4c86d-1022">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4c86d-1023">Поле сведений 3. Сектор.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1023">Info Field 3: Sector.</span></span>
- <span data-ttu-id="4c86d-1024">Поле сведений 4. Число секторов.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1024">Info Field 4: Number sectors.</span></span>

### <a name="device-class-storage-read-capacity"></a><span data-ttu-id="4c86d-1025">Считывание емкости хранилища класса устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-1025">Device Class Storage Read Capacity</span></span> 

#### <a name="ux_device_class_storage_read_capacity"></a><span data-ttu-id="4c86d-1026">ux_device_class_storage_read_capacity</span><span class="sxs-lookup"><span data-stu-id="4c86d-1026">ux_device_class_storage_read_capacity</span></span>

<span data-ttu-id="4c86d-1027">**Значок** ![Значок считывания емкости хранилища класса устройства](./media/user-guide/usbx-events/image49.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1027">**Icon** ![Device Class Storage Read Capacity icon](./media/user-guide/usbx-events/image49.png)</span></span>

<span data-ttu-id="4c86d-1028">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1028">**Description**</span></span>

<span data-ttu-id="4c86d-1029">Это событие представляет собой считывание емкости хранилища класса устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1029">This event represents a USBX Device Class Storage Read Capacity Event.</span></span>

<span data-ttu-id="4c86d-1030">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1030">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1031">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1031">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-1032">Поле сведений 2. Номер логического устройства (LUN).</span><span class="sxs-lookup"><span data-stu-id="4c86d-1032">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4c86d-1033">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1033">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1034">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1034">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-read-format-capacity"></a><span data-ttu-id="4c86d-1035">Считывание формата емкости хранилища класса устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-1035">Device Class Storage Read Format Capacity</span></span> 

#### <a name="ux_device_class_storage_read_format_capacity"></a><span data-ttu-id="4c86d-1036">ux_device_class_storage_read_format_capacity</span><span class="sxs-lookup"><span data-stu-id="4c86d-1036">ux_device_class_storage_read_format_capacity</span></span>

<span data-ttu-id="4c86d-1037">**Значок** ![Значок считывания формата емкости хранилища класса устройства](./media/user-guide/usbx-events/image50.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1037">**Icon** ![Device Class Storage Read Format Capacity icon](./media/user-guide/usbx-events/image50.png)</span></span>

<span data-ttu-id="4c86d-1038">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1038">**Description**</span></span>

<span data-ttu-id="4c86d-1039">Это событие представляет собой считывание формата емкости хранилища класса устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1039">This event represents a USBX Device Class Storage Read Format Capacity Event.</span></span>

<span data-ttu-id="4c86d-1040">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1040">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1041">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1041">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-1042">Поле сведений 2. Номер логического устройства (LUN).</span><span class="sxs-lookup"><span data-stu-id="4c86d-1042">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4c86d-1043">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1043">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1044">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1044">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-read-toc"></a><span data-ttu-id="4c86d-1045">Считывание оглавления хранилища класса устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-1045">Device Class Storage Read TOC</span></span> 

#### <a name="ux_device_class_storage_read_toc"></a><span data-ttu-id="4c86d-1046">ux_device_class_storage_read_toc</span><span class="sxs-lookup"><span data-stu-id="4c86d-1046">ux_device_class_storage_read_toc</span></span>

<span data-ttu-id="4c86d-1047">**Значок** ![Значок считывания оглавления хранилища класса устройства](./media/user-guide/usbx-events/image51.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1047">**Icon** ![Device Class Storage Read TOC icon](./media/user-guide/usbx-events/image51.png)</span></span>

<span data-ttu-id="4c86d-1048">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1048">**Description**</span></span>

<span data-ttu-id="4c86d-1049">Это событие представляет собой считывание оглавления хранилища класса устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1049">This event represents a USBX Device Class Storage Read TOC Event.</span></span>

<span data-ttu-id="4c86d-1050">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1050">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1051">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1051">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-1052">Поле сведений 2. Номер логического устройства (LUN).</span><span class="sxs-lookup"><span data-stu-id="4c86d-1052">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4c86d-1053">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1053">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1054">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1054">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-request-sense"></a><span data-ttu-id="4c86d-1055">Запрос на контроль хранилища класса устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-1055">Device Class Storage Request Sense</span></span> 

#### <a name="ux_device_class_storage_request_sense"></a><span data-ttu-id="4c86d-1056">ux_device_class_storage_request_sense</span><span class="sxs-lookup"><span data-stu-id="4c86d-1056">ux_device_class_storage_request_sense</span></span>

<span data-ttu-id="4c86d-1057">**Значок** ![Значок запроса на контроль хранилища класса устройства](./media/user-guide/usbx-events/image52.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1057">**Icon** ![Device Class Storage Request Sense icon](./media/user-guide/usbx-events/image52.png)</span></span>

<span data-ttu-id="4c86d-1058">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1058">**Description**</span></span>

<span data-ttu-id="4c86d-1059">Это событие представляет собой запрос на контроль хранилища класса устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1059">This event represents a USBX Device Class Storage Request Sense Event.</span></span>

<span data-ttu-id="4c86d-1060">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1060">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1061">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1061">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-1062">Поле сведений 2. Номер логического устройства (LUN).</span><span class="sxs-lookup"><span data-stu-id="4c86d-1062">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4c86d-1063">Поле сведений 3. Ключ контроля.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1063">Info Field 3: Sense key.</span></span>
- <span data-ttu-id="4c86d-1064">Поле сведений 4. Код.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1064">Info Field 4: Code.</span></span>

### <a name="device-class-storage-start-stop"></a><span data-ttu-id="4c86d-1065">Запуск и остановка хранилища класса устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-1065">Device Class Storage Start Stop</span></span> 

#### <a name="ux_device_class_storage_start_stop"></a><span data-ttu-id="4c86d-1066">ux_device_class_storage_start_stop</span><span class="sxs-lookup"><span data-stu-id="4c86d-1066">ux_device_class_storage_start_stop</span></span>

<span data-ttu-id="4c86d-1067">**Значок** ![Значок запуска и остановки хранилища класса устройства](./media/user-guide/usbx-events/image53.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1067">**Icon** ![Device Class Storage Start Stop icon](./media/user-guide/usbx-events/image53.png)</span></span>

<span data-ttu-id="4c86d-1068">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1068">**Description**</span></span>

<span data-ttu-id="4c86d-1069">Это событие представляет собой запуск и остановку хранилища класса устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1069">This event represents a USBX Device Class Storage Start Stop Event.</span></span>

<span data-ttu-id="4c86d-1070">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1070">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1071">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1071">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-1072">Поле сведений 2. Номер логического устройства (LUN).</span><span class="sxs-lookup"><span data-stu-id="4c86d-1072">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4c86d-1073">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1073">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1074">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1074">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-test-ready"></a><span data-ttu-id="4c86d-1075">Готовность к тестированию хранилища класса устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-1075">Device Class Storage Test Ready</span></span> 

#### <a name="ux_device_class_storage_test_ready"></a><span data-ttu-id="4c86d-1076">ux_device_class_storage_test_ready</span><span class="sxs-lookup"><span data-stu-id="4c86d-1076">ux_device_class_storage_test_ready</span></span>

<span data-ttu-id="4c86d-1077">**Значок** ![Значок готовности к тестированию хранилища класса устройства](./media/user-guide/usbx-events/image54.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1077">**Icon** ![Device Class Storage Test Ready icon](./media/user-guide/usbx-events/image54.png)</span></span>

<span data-ttu-id="4c86d-1078">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1078">**Description**</span></span>

<span data-ttu-id="4c86d-1079">Это событие представляет собой готовность к тестированию хранилища класса устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1079">This event represents a USBX Device Class Storage Test Ready Event.</span></span>

<span data-ttu-id="4c86d-1080">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1080">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1081">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1081">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-1082">Поле сведений 2. Номер логического устройства (LUN).</span><span class="sxs-lookup"><span data-stu-id="4c86d-1082">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4c86d-1083">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1083">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1084">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1084">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-verify"></a><span data-ttu-id="4c86d-1085">Проверка хранилища класса устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-1085">Device Class Storage Verify</span></span> 

#### <a name="ux_device_class_storage_verify"></a><span data-ttu-id="4c86d-1086">ux_device_class_storage_verify</span><span class="sxs-lookup"><span data-stu-id="4c86d-1086">ux_device_class_storage_verify</span></span>

<span data-ttu-id="4c86d-1087">**Значок** ![Значок проверки хранилища класса устройства](./media/user-guide/usbx-events/image55.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1087">**Icon** ![Device Class Storage Verify icon](./media/user-guide/usbx-events/image55.png)</span></span>

<span data-ttu-id="4c86d-1088">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1088">**Description**</span></span>

<span data-ttu-id="4c86d-1089">Это событие представляет собой проверку хранилища класса устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1089">This event represents a USBX Device Class Storage Verify Event.</span></span>

<span data-ttu-id="4c86d-1090">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1090">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1091">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1091">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-1092">Поле сведений 2. Номер логического устройства (LUN).</span><span class="sxs-lookup"><span data-stu-id="4c86d-1092">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4c86d-1093">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1093">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1094">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1094">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-write"></a><span data-ttu-id="4c86d-1095">Запись хранилища класса устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-1095">Device Class Storage Write</span></span> 

#### <a name="ux_device_class_storage_write"></a><span data-ttu-id="4c86d-1096">ux_device_class_storage_write</span><span class="sxs-lookup"><span data-stu-id="4c86d-1096">ux_device_class_storage_write</span></span>

<span data-ttu-id="4c86d-1097">**Значок** ![Значок записи хранилища класса устройства](./media/user-guide/usbx-events/image56.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1097">**Icon** ![Device Class Storage Write icon](./media/user-guide/usbx-events/image56.png)</span></span>

<span data-ttu-id="4c86d-1098">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1098">**Description**</span></span>

<span data-ttu-id="4c86d-1099">Это событие представляет собой запись хранилища класса устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1099">This event represents a USBX Device Class Storage Write Event.</span></span>

<span data-ttu-id="4c86d-1100">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1100">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1101">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1101">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-1102">Поле сведений 2. Номер логического устройства (LUN).</span><span class="sxs-lookup"><span data-stu-id="4c86d-1102">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4c86d-1103">Поле сведений 3. Сектор.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1103">Info Field 3: Sector.</span></span>
- <span data-ttu-id="4c86d-1104">Поле сведений 4. Число секторов.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1104">Info Field 4: Number sectors.</span></span>

### <a name="device-stack-alternate-setting-get"></a><span data-ttu-id="4c86d-1105">Получение дополнительных параметров стека устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-1105">Device Stack Alternate Setting Get</span></span> 

#### <a name="ux_device_class_alternate_setting_get"></a><span data-ttu-id="4c86d-1106">ux_device_class_alternate_setting_get</span><span class="sxs-lookup"><span data-stu-id="4c86d-1106">ux_device_class_alternate_setting_get</span></span>

<span data-ttu-id="4c86d-1107">**Значок** ![Значок получения дополнительных параметров стека устройства](./media/user-guide/usbx-events/image57.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1107">**Icon** ![Device Stack Alternate Setting Get icon](./media/user-guide/usbx-events/image57.png)</span></span>

<span data-ttu-id="4c86d-1108">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1108">**Description**</span></span>

<span data-ttu-id="4c86d-1109">Это событие представляет собой получение дополнительных параметров стека устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1109">This event represents a USBX Device Stack Alternate Setting Get Event.</span></span>

<span data-ttu-id="4c86d-1110">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1110">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1111">Поле сведений 1. Значение интерфейса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1111">Info Field 1: Interface value.</span></span>
- <span data-ttu-id="4c86d-1112">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1112">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1113">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1113">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1114">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1114">Info Field 4: Not used.</span></span>

### <a name="device-stack-alternate-setting-set"></a><span data-ttu-id="4c86d-1115">Установка дополнительных параметров стека устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-1115">Device Stack Alternate Setting Set</span></span> 

#### <a name="ux_device_class_alternate_setting_set"></a><span data-ttu-id="4c86d-1116">ux_device_class_alternate_setting_set</span><span class="sxs-lookup"><span data-stu-id="4c86d-1116">ux_device_class_alternate_setting_set</span></span>

<span data-ttu-id="4c86d-1117">**Значок** ![Значок установки дополнительных параметров стека устройства](./media/user-guide/usbx-events/image58.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1117">**Icon** ![Device Stack Alternate Setting Set icon](./media/user-guide/usbx-events/image58.png)</span></span>

<span data-ttu-id="4c86d-1118">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1118">**Description**</span></span>

<span data-ttu-id="4c86d-1119">Это событие представляет собой установку дополнительных параметров стека устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1119">This event represents a USBX Device Stack Alternate Setting Set Event.</span></span>

<span data-ttu-id="4c86d-1120">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1120">**Information Fields**</span></span>
- <span data-ttu-id="4c86d-1121">Поле сведений 1. Значение интерфейса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1121">Info Field 1: Interface value.</span></span>
- <span data-ttu-id="4c86d-1122">Поле сведений 2. Значение дополнительного параметра.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1122">Info Field 2: Alternate setting value.</span></span>
- <span data-ttu-id="4c86d-1123">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1123">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1124">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1124">Info Field 4: Not used.</span></span>

### <a name="device-stack-class-register"></a><span data-ttu-id="4c86d-1125">Регистрация класса стека устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-1125">Device Stack Class Register</span></span> 

#### <a name="ux_device_stack_class_register"></a><span data-ttu-id="4c86d-1126">ux_device_stack_class_register</span><span class="sxs-lookup"><span data-stu-id="4c86d-1126">ux_device_stack_class_register</span></span>

<span data-ttu-id="4c86d-1127">**Значок** ![Значок регистрации класса стека устройства](./media/user-guide/usbx-events/image59.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1127">**Icon** ![Device Stack Class Register icon](./media/user-guide/usbx-events/image59.png)</span></span>

<span data-ttu-id="4c86d-1128">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1128">**Description**</span></span>

<span data-ttu-id="4c86d-1129">Это событие представляет собой регистрацию класса стека устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1129">This event represents a USBX Device Stack Class Register Event.</span></span>

<span data-ttu-id="4c86d-1130">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1130">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1131">Поле сведений 1. Имя класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1131">Info Field 1: Class name.</span></span>
- <span data-ttu-id="4c86d-1132">Поле сведений 2. Номер интерфейса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1132">Info Field 2: Interface number.</span></span>
- <span data-ttu-id="4c86d-1133">Поле сведений 3. Параметр.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1133">Info Field 3: Parameter.</span></span>
- <span data-ttu-id="4c86d-1134">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1134">Info Field 4: Not used.</span></span>

### <a name="device-stack-clear-feature"></a><span data-ttu-id="4c86d-1135">Возможность очистки стека устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-1135">Device Stack Clear Feature</span></span> 

#### <a name="ux_device_stack_clear_feature"></a><span data-ttu-id="4c86d-1136">ux_device_stack_clear_feature</span><span class="sxs-lookup"><span data-stu-id="4c86d-1136">ux_device_stack_clear_feature</span></span>

<span data-ttu-id="4c86d-1137">**Значок** ![Значок возможности очистки стека устройства](./media/user-guide/usbx-events/image60.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1137">**Icon** ![Device Stack Clear Feature icon](./media/user-guide/usbx-events/image60.png)</span></span>

<span data-ttu-id="4c86d-1138">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1138">**Description**</span></span>

<span data-ttu-id="4c86d-1139">Это событие представляет собой возможность очистки стека устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1139">This event represents a USBX Device Stack Clear Feature Event.</span></span>

<span data-ttu-id="4c86d-1140">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1140">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1141">Поле сведений 1. Тип запроса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1141">Info Field 1: Request type.</span></span>
- <span data-ttu-id="4c86d-1142">Поле сведений 2. Значение запроса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1142">Info Field 2: Request value.</span></span> <span data-ttu-id="4c86d-1143">Поле сведений 3. Индекс запроса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1143">Info Field 3: Request index.</span></span>
- <span data-ttu-id="4c86d-1144">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1144">Info Field 4: Not used.</span></span>

### <a name="device-stack-configuration-get"></a><span data-ttu-id="4c86d-1145">Получение конфигурации стека устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-1145">Device Stack Configuration Get</span></span> 

#### <a name="ux_device_stack_configuration_get-t"></a><span data-ttu-id="4c86d-1146">ux_device_stack_configuration_get t</span><span class="sxs-lookup"><span data-stu-id="4c86d-1146">ux_device_stack_configuration_get t</span></span>

<span data-ttu-id="4c86d-1147">**Значок** ![Значок получения конфигурации стека устройства](./media/user-guide/usbx-events/image61.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1147">**Icon** ![Device Stack Configuration Get icon](./media/user-guide/usbx-events/image61.png)</span></span>

<span data-ttu-id="4c86d-1148">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1148">**Description**</span></span>

<span data-ttu-id="4c86d-1149">Это событие представляет собой получение конфигурации стека устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1149">This event represents a USBX Device Stack Configuration Get Event.</span></span>

<span data-ttu-id="4c86d-1150">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1150">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1151">Поле сведений 1. Значение конфигурации.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1151">Info Field 1: Configuration value.</span></span>
- <span data-ttu-id="4c86d-1152">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1152">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1153">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1153">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1154">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1154">Info Field 4: Not used.</span></span>

### <a name="device-stack-configuration-set"></a><span data-ttu-id="4c86d-1155">Установка конфигурации стека устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-1155">Device Stack Configuration Set</span></span> 

#### <a name="ux_device_stack_configuration_set"></a><span data-ttu-id="4c86d-1156">ux_device_stack_configuration_set</span><span class="sxs-lookup"><span data-stu-id="4c86d-1156">ux_device_stack_configuration_set</span></span>

<span data-ttu-id="4c86d-1157">**Значок** ![Значок установки конфигурации стека устройства](./media/user-guide/usbx-events/image62.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1157">**Icon** ![Device Stack Configuration Set icon](./media/user-guide/usbx-events/image62.png)</span></span>

<span data-ttu-id="4c86d-1158">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1158">**Description**</span></span>

<span data-ttu-id="4c86d-1159">Это событие представляет собой установку конфигурации стека устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1159">This event represents a USBX Device Stack Configuration Set Event.</span></span>

<span data-ttu-id="4c86d-1160">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1160">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1161">Поле сведений 1. Значение конфигурации.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1161">Info Field 1: Configuration value.</span></span>
- <span data-ttu-id="4c86d-1162">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1162">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1163">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1163">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1164">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1164">Info Field 4: Not used.</span></span>

### <a name="device-stack-connect"></a><span data-ttu-id="4c86d-1165">Подключение к стеку устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-1165">Device Stack Connect</span></span> 

#### <a name="ux_device_stack_connect"></a><span data-ttu-id="4c86d-1166">ux_device_stack_connect</span><span class="sxs-lookup"><span data-stu-id="4c86d-1166">ux_device_stack_connect</span></span>

<span data-ttu-id="4c86d-1167">**Значок** ![Значок подключения к стеку устройства](./media/user-guide/usbx-events/image63.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1167">**Icon** ![Device Stack Connect icon](./media/user-guide/usbx-events/image63.png)</span></span>

<span data-ttu-id="4c86d-1168">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1168">**Description**</span></span>

<span data-ttu-id="4c86d-1169">Это событие представляет собой отправку дескриптора стека устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1169">This event represents a USBX Device Stack Descriptor Send Event.</span></span>

<span data-ttu-id="4c86d-1170">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1170">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1171">Поле сведений 1. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1171">Info Field 1: Not used.</span></span>
- <span data-ttu-id="4c86d-1172">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1172">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1173">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1173">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1174">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1174">Info Field 4: Not used.</span></span>

### <a name="device-stack-descriptor-send"></a><span data-ttu-id="4c86d-1175">Отправка дескриптора стека устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-1175">Device Stack Descriptor Send</span></span> 

#### <a name="ux_device_stack_descriptor_send"></a><span data-ttu-id="4c86d-1176">ux_device_stack_descriptor_send</span><span class="sxs-lookup"><span data-stu-id="4c86d-1176">ux_device_stack_descriptor_send</span></span>

<span data-ttu-id="4c86d-1177">**Значок** ![Значок отправки дескриптора стека устройства](./media/user-guide/usbx-events/image64.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1177">**Icon** ![Device Stack Descriptor Send icon](./media/user-guide/usbx-events/image64.png)</span></span>

<span data-ttu-id="4c86d-1178">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1178">**Description**</span></span>

<span data-ttu-id="4c86d-1179">Это событие представляет собой отправку дескриптора стека устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1179">This event represents a USBX Device Stack Descriptor Send Event.</span></span>

<span data-ttu-id="4c86d-1180">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1180">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1181">Поле сведений 1. Тип дескриптора.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1181">Info Field 1: Descriptor type.</span></span>
- <span data-ttu-id="4c86d-1182">Поле сведений 2. Индекс запроса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1182">Info Field 2: Request index.</span></span>
- <span data-ttu-id="4c86d-1183">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1183">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1184">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1184">Info Field 4: Not used.</span></span>

### <a name="device-stack-disconnect"></a><span data-ttu-id="4c86d-1185">Отключение стека устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-1185">Device Stack Disconnect</span></span> 

#### <a name="ux_device_stack_disconnect"></a><span data-ttu-id="4c86d-1186">ux_device_stack_disconnect</span><span class="sxs-lookup"><span data-stu-id="4c86d-1186">ux_device_stack_disconnect</span></span>

<span data-ttu-id="4c86d-1187">**Значок** ![Значок отключения стека устройства](./media/user-guide/usbx-events/image65.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1187">**Icon** ![Device Stack Disconnect icon](./media/user-guide/usbx-events/image65.png)</span></span>

<span data-ttu-id="4c86d-1188">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1188">**Description**</span></span>

<span data-ttu-id="4c86d-1189">Это событие представляет собой отключение стека устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1189">This event represents a USBX Device Stack Disconnect Event.</span></span>

<span data-ttu-id="4c86d-1190">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1190">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1191">Поле сведений 1. Устройство.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1191">Info Field 1: Device.</span></span>
- <span data-ttu-id="4c86d-1192">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1192">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1193">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1193">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1194">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1194">Info Field 4: Not used.</span></span>

### <a name="device-stack-endpoint-stall"></a><span data-ttu-id="4c86d-1195">Остановка конечной точки стека устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-1195">Device Stack Endpoint Stall</span></span> 

#### <a name="ux_device_stack_endpoint_stall"></a><span data-ttu-id="4c86d-1196">ux_device_stack_endpoint_stall</span><span class="sxs-lookup"><span data-stu-id="4c86d-1196">ux_device_stack_endpoint_stall</span></span>

<span data-ttu-id="4c86d-1197">**Значок** ![Значок остановки конечной точки стека устройства](./media/user-guide/usbx-events/image66.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1197">**Icon** ![Device Stack Endpoint Stall icon](./media/user-guide/usbx-events/image66.png)</span></span>

<span data-ttu-id="4c86d-1198">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1198">**Description**</span></span>

<span data-ttu-id="4c86d-1199">Это событие представляет собой остановку конечной точки стека устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1199">This event represents a USBX Device Stack Endpoint Stall Event.</span></span>

<span data-ttu-id="4c86d-1200">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1200">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1201">Поле сведений 1. Конечная точка.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1201">Info Field 1: Endpoint.</span></span>
- <span data-ttu-id="4c86d-1202">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1202">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1203">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1203">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1204">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1204">Info Field 4: Not used.</span></span>

### <a name="device-stack-get-status"></a><span data-ttu-id="4c86d-1205">Получение состояния стека устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-1205">Device Stack Get Status</span></span> 

#### <a name="ux_device_stack_get_status"></a><span data-ttu-id="4c86d-1206">ux_device_stack_get_status</span><span class="sxs-lookup"><span data-stu-id="4c86d-1206">ux_device_stack_get_status</span></span>

<span data-ttu-id="4c86d-1207">**Значок** ![Значок получения состояния стека устройства](./media/user-guide/usbx-events/image67.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1207">**Icon** ![Device Stack Get Status icon](./media/user-guide/usbx-events/image67.png)</span></span>

<span data-ttu-id="4c86d-1208">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1208">**Description**</span></span>

<span data-ttu-id="4c86d-1209">Это событие представляет собой получение состояния стека устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1209">This event represents a USBX Device Stack Get Status Event.</span></span>

<span data-ttu-id="4c86d-1210">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1210">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1211">Поле сведений 1. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1211">Info Field 1: Not used.</span></span>
- <span data-ttu-id="4c86d-1212">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1212">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1213">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1213">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1214">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1214">Info Field 4: Not used.</span></span>

### <a name="device-stack-host-wakeup"></a><span data-ttu-id="4c86d-1215">Выход узла стека устройства из спящего режима</span><span class="sxs-lookup"><span data-stu-id="4c86d-1215">Device Stack Host Wakeup</span></span> 

#### <a name="ux_device_stack_host_wakeup"></a><span data-ttu-id="4c86d-1216">ux_device_stack_host_wakeup</span><span class="sxs-lookup"><span data-stu-id="4c86d-1216">ux_device_stack_host_wakeup</span></span>

<span data-ttu-id="4c86d-1217">**Значок** ![Значок выхода узла стека устройства из спящего режима](./media/user-guide/usbx-events/image68.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1217">**Icon** ![Device Stack Host Wakeup icon](./media/user-guide/usbx-events/image68.png)</span></span>

<span data-ttu-id="4c86d-1218">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1218">**Description**</span></span>

<span data-ttu-id="4c86d-1219">Это событие представляет собой выход узла стека устройства USBX из спящего режима.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1219">This event represents a USBX Device Stack Host Wakeup Event.</span></span>

<span data-ttu-id="4c86d-1220">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1220">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1221">Поле сведений 1. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1221">Info Field 1: Not used.</span></span>
- <span data-ttu-id="4c86d-1222">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1222">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1223">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1223">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1224">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1224">Info Field 4: Not used.</span></span>

### <a name="device-stack-initialize"></a><span data-ttu-id="4c86d-1225">Инициализация стека устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-1225">Device Stack Initialize</span></span> 

#### <a name="ux_device_stack_initialize"></a><span data-ttu-id="4c86d-1226">ux_device_stack_initialize</span><span class="sxs-lookup"><span data-stu-id="4c86d-1226">ux_device_stack_initialize</span></span>

<span data-ttu-id="4c86d-1227">**Значок** ![Значок инициализации стека устройства](./media/user-guide/usbx-events/image69.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1227">**Icon** ![Device Stack Initialize icon](./media/user-guide/usbx-events/image69.png)</span></span>

<span data-ttu-id="4c86d-1228">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1228">**Description**</span></span>

<span data-ttu-id="4c86d-1229">Это событие представляет собой инициализацию стека устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1229">This event represents a USBX Device Stack Initialize Event.</span></span>

<span data-ttu-id="4c86d-1230">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1230">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1231">Поле сведений 1. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1231">Info Field 1: Not used.</span></span>
- <span data-ttu-id="4c86d-1232">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1232">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1233">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1233">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1234">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1234">Info Field 4: Not used.</span></span>

### <a name="device-stack-interface-delete"></a><span data-ttu-id="4c86d-1235">Удаление интерфейса стека устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-1235">Device Stack Interface Delete</span></span> 

#### <a name="ux_device_stack_interface_delete"></a><span data-ttu-id="4c86d-1236">ux_device_stack_interface_delete</span><span class="sxs-lookup"><span data-stu-id="4c86d-1236">ux_device_stack_interface_delete</span></span>

<span data-ttu-id="4c86d-1237">**Значок** ![Значок удаления интерфейса стека устройства](./media/user-guide/usbx-events/image70.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1237">**Icon** ![Device Stack Interface Delete icon](./media/user-guide/usbx-events/image70.png)</span></span>

<span data-ttu-id="4c86d-1238">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1238">**Description**</span></span>

<span data-ttu-id="4c86d-1239">Это событие представляет собой удаление интерфейса стека устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1239">This event represents a USBX Device Stack Interface Delete Event.</span></span>

<span data-ttu-id="4c86d-1240">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1240">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1241">Поле сведений 1. Интерфейс.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1241">Info Field 1: Interface.</span></span>
- <span data-ttu-id="4c86d-1242">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1242">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1243">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1243">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1244">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1244">Info Field 4: Not used.</span></span>

### <a name="device-stack-interface-get"></a><span data-ttu-id="4c86d-1245">Получение интерфейса стека устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-1245">Device Stack Interface Get</span></span> 

#### <a name="ux_device_stack_interface_get"></a><span data-ttu-id="4c86d-1246">ux_device_stack_interface_get</span><span class="sxs-lookup"><span data-stu-id="4c86d-1246">ux_device_stack_interface_get</span></span>

<span data-ttu-id="4c86d-1247">**Значок** ![Значок получения интерфейса стека устройства](./media/user-guide/usbx-events/image71.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1247">**Icon** ![Device Stack Interface Get icon](./media/user-guide/usbx-events/image71.png)</span></span>

<span data-ttu-id="4c86d-1248">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1248">**Description**</span></span>

<span data-ttu-id="4c86d-1249">Это событие представляет собой получение интерфейса стека устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1249">This event represents a USBX Device Stack Interface Get Event.</span></span>

<span data-ttu-id="4c86d-1250">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1250">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1251">Поле сведений 1. Значение интерфейса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1251">Info Field 1: Interface value.</span></span>
- <span data-ttu-id="4c86d-1252">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1252">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1253">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1253">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1254">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1254">Info Field 4: Not used.</span></span>

### <a name="device-stack-interface-set"></a><span data-ttu-id="4c86d-1255">Установка интерфейса стека устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-1255">Device Stack Interface Set</span></span> 

#### <a name="ux_device_stack_interface_set"></a><span data-ttu-id="4c86d-1256">ux_device_stack_interface_set</span><span class="sxs-lookup"><span data-stu-id="4c86d-1256">ux_device_stack_interface_set</span></span>

<span data-ttu-id="4c86d-1257">**Значок** ![Значок установки интерфейса стека устройства](./media/user-guide/usbx-events/image72.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1257">**Icon** ![Device Stack Interface Set icon](./media/user-guide/usbx-events/image72.png)</span></span>

<span data-ttu-id="4c86d-1258">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1258">**Description**</span></span>

<span data-ttu-id="4c86d-1259">Это событие представляет собой установку интерфейса стека устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1259">This event represents a USBX Device Stack Interface Set Event.</span></span>

<span data-ttu-id="4c86d-1260">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1260">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1261">Поле сведений 1. Значение запроса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1261">Info Field 1: Request value.</span></span> <span data-ttu-id="4c86d-1262">Поле сведений 2. Индекс запроса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1262">Info Field 2: Request index.</span></span>
- <span data-ttu-id="4c86d-1263">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1263">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1264">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1264">Info Field 4: Not used.</span></span>

### <a name="device-stack-set-feature"></a><span data-ttu-id="4c86d-1265">Возможности набора стеков устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-1265">Device Stack Set Feature</span></span> 

#### <a name="ux_device_stack_set_feature"></a><span data-ttu-id="4c86d-1266">ux_device_stack_set_feature</span><span class="sxs-lookup"><span data-stu-id="4c86d-1266">ux_device_stack_set_feature</span></span>

<span data-ttu-id="4c86d-1267">**Значок** ![Значок возможностей набора стеков устройства](./media/user-guide/usbx-events/image73.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1267">**Icon** ![Device Stack Set Feature icon](./media/user-guide/usbx-events/image73.png)</span></span>

<span data-ttu-id="4c86d-1268">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1268">**Description**</span></span>

<span data-ttu-id="4c86d-1269">Это событие представляет собой событие возможностей набора стеков устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1269">This event represents a USBX Device Stack Set Feature Event.</span></span>

<span data-ttu-id="4c86d-1270">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1270">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1271">Поле сведений 1. Значение запроса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1271">Info Field 1: Request value.</span></span> <span data-ttu-id="4c86d-1272">Поле сведений 2. Индекс запроса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1272">Info Field 2: Request index.</span></span>
- <span data-ttu-id="4c86d-1273">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1273">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1274">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1274">Info Field 4: Not used.</span></span>

### <a name="device-stack-transfer-abort"></a><span data-ttu-id="4c86d-1275">Прерывание перемещения стека устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-1275">Device Stack Transfer Abort</span></span> 

#### <a name="ux_device_stack_transfer_abort"></a><span data-ttu-id="4c86d-1276">ux_device_stack_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="4c86d-1276">ux_device_stack_transfer_abort</span></span>

<span data-ttu-id="4c86d-1277">**Значок** ![Значок прерывания перемещения стека устройства](./media/user-guide/usbx-events/image74.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1277">**Icon** ![Device Stack Transfer Abort icon](./media/user-guide/usbx-events/image74.png)</span></span>

<span data-ttu-id="4c86d-1278">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1278">**Description**</span></span>

<span data-ttu-id="4c86d-1279">Это событие представляет собой прерывание перемещения стека устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1279">This event represents a USBX Device Stack Transfer Abort Event.</span></span>

<span data-ttu-id="4c86d-1280">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1280">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1281">Поле сведений 1. Запрос на передачу.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1281">Info Field 1: Transfer request.</span></span>
- <span data-ttu-id="4c86d-1282">Поле сведений 2. Код завершения.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1282">Info Field 2: Completion code.</span></span>
- <span data-ttu-id="4c86d-1283">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1283">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1284">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1284">Info Field 4: Not used.</span></span>

### <a name="device-stack-transfer-all-request-abort"></a><span data-ttu-id="4c86d-1285">Прерывание всех запросов на передачу стека устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-1285">Device Stack Transfer All Request Abort</span></span> 

#### <a name="ux_device_stack_transfer_all_request_abort"></a><span data-ttu-id="4c86d-1286">ux_device_stack_transfer_all_request_abort</span><span class="sxs-lookup"><span data-stu-id="4c86d-1286">ux_device_stack_transfer_all_request_abort</span></span>

<span data-ttu-id="4c86d-1287">**Значок** ![Значок прерывания всех запросов на передачу стека устройства](./media/user-guide/usbx-events/image75.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1287">**Icon** ![Device Stack Transfer All Request Abort icon](./media/user-guide/usbx-events/image75.png)</span></span>

<span data-ttu-id="4c86d-1288">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1288">**Description**</span></span>

<span data-ttu-id="4c86d-1289">Это событие представляет собой прерывание всех запросов на передачу стека устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1289">This event represents a USBX Device Stack Transfer All Request Abort Event.</span></span>

<span data-ttu-id="4c86d-1290">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1290">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1291">Поле сведений 1. Конечная точка.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1291">Info Field 1: Endpoint.</span></span>
- <span data-ttu-id="4c86d-1292">Поле сведений 2. Код завершения.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1292">Info Field 2: Completion code.</span></span>
- <span data-ttu-id="4c86d-1293">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1293">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1294">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1294">Info Field 4: Not used.</span></span>

### <a name="device-stack-transfer-request"></a><span data-ttu-id="4c86d-1295">Запрос на передачу стека устройства</span><span class="sxs-lookup"><span data-stu-id="4c86d-1295">Device Stack Transfer Request</span></span> 

#### <a name="ux_device_stack_transfer_request"></a><span data-ttu-id="4c86d-1296">ux_device_stack_transfer_request</span><span class="sxs-lookup"><span data-stu-id="4c86d-1296">ux_device_stack_transfer_request</span></span>

<span data-ttu-id="4c86d-1297">**Значок** ![Значок запроса на передачу стека устройства](./media/user-guide/usbx-events/image76.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1297">**Icon** ![Device Stack Transfer Request icon](./media/user-guide/usbx-events/image76.png)</span></span>

<span data-ttu-id="4c86d-1298">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1298">**Description**</span></span>

<span data-ttu-id="4c86d-1299">Это событие представляет собой запрос на передачу стека устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1299">This event represents a USBX Device Stack Transfer Request Event.</span></span>

<span data-ttu-id="4c86d-1300">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1300">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1301">Поле сведений 1. Запрос на передачу.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1301">Info Field 1: Transfer request.</span></span>
- <span data-ttu-id="4c86d-1302">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1302">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1303">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1303">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1304">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1304">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-activate"></a><span data-ttu-id="4c86d-1305">Активация класса Asix узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1305">Host Class Asix Activate</span></span> 

#### <a name="ux_host_class_asix_activate"></a><span data-ttu-id="4c86d-1306">ux_host_class_asix_activate</span><span class="sxs-lookup"><span data-stu-id="4c86d-1306">ux_host_class_asix_activate</span></span>

<span data-ttu-id="4c86d-1307">**Значок** ![Значок активации класса Asix узла](./media/user-guide/usbx-events/image77.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1307">**Icon** ![Host Class Asix Activate icon](./media/user-guide/usbx-events/image77.png)</span></span>

<span data-ttu-id="4c86d-1308">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1308">**Description**</span></span>

<span data-ttu-id="4c86d-1309">Это событие представляет собой активацию класса Asix узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1309">This event represents a USBX Host Class Asix Activate.</span></span>

<span data-ttu-id="4c86d-1310">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1310">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1311">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1311">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-1312">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1312">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1313">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1313">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1314">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1314">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-deactivate"></a><span data-ttu-id="4c86d-1315">Деактивация класса Asix узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1315">Host Class Asix Deactivate</span></span> 

#### <a name="ux_host_class_asix_deactivate"></a><span data-ttu-id="4c86d-1316">ux_host_class_asix_deactivate</span><span class="sxs-lookup"><span data-stu-id="4c86d-1316">ux_host_class_asix_deactivate</span></span>

<span data-ttu-id="4c86d-1317">**Значок** ![Значок деактивации класса Asix узла](./media/user-guide/usbx-events/image78.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1317">**Icon** ![Host Class Asix Deactivate icon](./media/user-guide/usbx-events/image78.png)</span></span>

<span data-ttu-id="4c86d-1318">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1318">**Description**</span></span>

<span data-ttu-id="4c86d-1319">Это событие представляет собой деактивацию класса Asix узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1319">This event represents a USBX Host Class Asix Deactivate Event.</span></span>

<span data-ttu-id="4c86d-1320">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1320">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1321">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1321">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-1322">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1322">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1323">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1323">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1324">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1324">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-interrupt-notification"></a><span data-ttu-id="4c86d-1325">Уведомление о прерывании класса Asix узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1325">Host Class Asix Interrupt Notification</span></span> 

#### <a name="ux_host_class_asix_interrupt_notification"></a><span data-ttu-id="4c86d-1326">ux_host_class_asix_interrupt_notification</span><span class="sxs-lookup"><span data-stu-id="4c86d-1326">ux_host_class_asix_interrupt_notification</span></span>

<span data-ttu-id="4c86d-1327">**Значок** ![Значок уведомления о прерывании класса Asix узла](./media/user-guide/usbx-events/image79.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1327">**Icon** ![Host Class Asix Interrupt Notification icon](./media/user-guide/usbx-events/image79.png)</span></span>

<span data-ttu-id="4c86d-1328">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1328">**Description**</span></span>

<span data-ttu-id="4c86d-1329">Это событие представляет собой уведомление о прерывании класса Asix узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1329">This event represents a USBX Host Class Asix Interrupt Notification Event.</span></span>

<span data-ttu-id="4c86d-1330">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1330">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1331">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1331">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-1332">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1332">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1333">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1333">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1334">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1334">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-read"></a><span data-ttu-id="4c86d-1335">Считывание класса Asix узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1335">Host Class Asix Read</span></span> 

#### <a name="ux_host_class_asix_read"></a><span data-ttu-id="4c86d-1336">ux_host_class_asix_read</span><span class="sxs-lookup"><span data-stu-id="4c86d-1336">ux_host_class_asix_read</span></span>

<span data-ttu-id="4c86d-1337">**Значок** ![Значок считывания класса Asix узла](./media/user-guide/usbx-events/image80.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1337">**Icon** ![Host Class Asix Read icon](./media/user-guide/usbx-events/image80.png)</span></span>

<span data-ttu-id="4c86d-1338">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1338">**Description**</span></span>

<span data-ttu-id="4c86d-1339">Это событие представляет собой считывание класса Asix узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1339">This event represents a USBX Host Class Asix Read Event.</span></span>

<span data-ttu-id="4c86d-1340">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1340">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1341">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1341">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1342">Поле сведений 2. Указатель данных.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1342">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4c86d-1343">Поле сведений 3. Запрошенная длина.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1343">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4c86d-1344">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1344">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-write"></a><span data-ttu-id="4c86d-1345">Запись класса Asix узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1345">Host Class Asix Write</span></span> 

#### <a name="ux_host_class_asix_write"></a><span data-ttu-id="4c86d-1346">ux_host_class_asix_write</span><span class="sxs-lookup"><span data-stu-id="4c86d-1346">ux_host_class_asix_write</span></span>

<span data-ttu-id="4c86d-1347">**Значок** ![Значок записи класса Asix узла](./media/user-guide/usbx-events/image81.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1347">**Icon** ![Host Class Asix Write icon](./media/user-guide/usbx-events/image81.png)</span></span>

<span data-ttu-id="4c86d-1348">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1348">**Description**</span></span>

<span data-ttu-id="4c86d-1349">Это событие представляет собой запись класса Asix узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1349">This event represents a USBX Host Class Asix Write Event.</span></span>

<span data-ttu-id="4c86d-1350">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1350">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1351">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1351">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1352">Поле сведений 2. Указатель данных.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1352">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4c86d-1353">Поле сведений 3. Запрошенная длина.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1353">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4c86d-1354">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1354">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-activate"></a><span data-ttu-id="4c86d-1355">Активация звука для класса узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1355">Host Class Audio Activate</span></span> 

#### <a name="ux_host_class_audio_activate"></a><span data-ttu-id="4c86d-1356">ux_host_class_audio_activate</span><span class="sxs-lookup"><span data-stu-id="4c86d-1356">ux_host_class_audio_activate</span></span>

<span data-ttu-id="4c86d-1357">**Значок** ![Значок активации звука класса узла](./media/user-guide/usbx-events/image82.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1357">**Icon** ![Host Class Audio Activate icon](./media/user-guide/usbx-events/image82.png)</span></span>

<span data-ttu-id="4c86d-1358">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1358">**Description**</span></span>

<span data-ttu-id="4c86d-1359">Это событие представляет собой активацию звука класса узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1359">This event represents a USBX Host Class Audio Activate Event.</span></span>

<span data-ttu-id="4c86d-1360">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1360">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1361">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1361">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1362">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1362">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1363">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1363">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1364">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1364">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-control-value-get"></a><span data-ttu-id="4c86d-1365">Получение значения элемента управления звуком для класса узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1365">Host Class Audio Control Value Get</span></span> 

#### <a name="ux_host_class_audio_control_value_get"></a><span data-ttu-id="4c86d-1366">ux_host_class_audio_control_value_get</span><span class="sxs-lookup"><span data-stu-id="4c86d-1366">ux_host_class_audio_control_value_get</span></span>

<span data-ttu-id="4c86d-1367">**Значок** ![Значок получения значения элемента управления звуком для класса узла](./media/user-guide/usbx-events/image83.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1367">**Icon** ![Host Class Audio Control Value Get icon](./media/user-guide/usbx-events/image83.png)</span></span>

<span data-ttu-id="4c86d-1368">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1368">**Description**</span></span>

<span data-ttu-id="4c86d-1369">Это событие представляет собой получение значения элемента управления звуком для класса узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1369">This event represents a USBX Host Class Audio Control Value Get Event.</span></span>

<span data-ttu-id="4c86d-1370">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1370">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1371">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1371">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1372">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1372">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1373">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1373">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1374">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1374">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-control-value-set"></a><span data-ttu-id="4c86d-1375">Установка значений элемента управления звуком для класса узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1375">Host Class Audio Control Value Set</span></span> 

#### <a name="ux_host_class_audio_control_value_set"></a><span data-ttu-id="4c86d-1376">ux_host_class_audio_control_value_set</span><span class="sxs-lookup"><span data-stu-id="4c86d-1376">ux_host_class_audio_control_value_set</span></span>

<span data-ttu-id="4c86d-1377">**Значок** ![Значок установки значений элемента управления звуком для класса узла](./media/user-guide/usbx-events/image84.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1377">**Icon** ![Host Class Audio Control Value Set icon](./media/user-guide/usbx-events/image84.png)</span></span>

<span data-ttu-id="4c86d-1378">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1378">**Description**</span></span>

<span data-ttu-id="4c86d-1379">Это событие представляет собой событие отложенной обработки внутреннего драйвера ввода-вывода в NetX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1379">This event represents an internal NetX I/O driver deferred processing event.</span></span>

<span data-ttu-id="4c86d-1380">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1380">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1381">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1381">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1382">Поле сведений 2. Элемент управления звуком.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1382">Info Field 2: Audio control.</span></span>
- <span data-ttu-id="4c86d-1383">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1383">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1384">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1384">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-deactivate"></a><span data-ttu-id="4c86d-1385">Деактивация звука класса узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1385">Host Class Audio Deactivate</span></span> 

#### <a name="ux_host_class_audio_deactivate"></a><span data-ttu-id="4c86d-1386">ux_host_class_audio_deactivate</span><span class="sxs-lookup"><span data-stu-id="4c86d-1386">ux_host_class_audio_deactivate</span></span>

<span data-ttu-id="4c86d-1387">**Значок** ![Значок деактивации звука класса узла](./media/user-guide/usbx-events/image85.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1387">**Icon** ![Host Class Audio Deactivate icon](./media/user-guide/usbx-events/image85.png)</span></span>

<span data-ttu-id="4c86d-1388">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1388">**Description**</span></span>

<span data-ttu-id="4c86d-1389">Это событие представляет собой деактивацию звука класса узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1389">This event represents a USBX Host Class Audio Deactivate Event.</span></span>

<span data-ttu-id="4c86d-1390">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1390">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1391">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1391">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1392">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1392">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1393">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1393">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1394">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1394">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-read"></a><span data-ttu-id="4c86d-1395">Считывание звуковых данных класса узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1395">Host Class Audio Read</span></span> 

#### <a name="ux_host_class_audio_read"></a><span data-ttu-id="4c86d-1396">ux_host_class_audio_read</span><span class="sxs-lookup"><span data-stu-id="4c86d-1396">ux_host_class_audio_read</span></span>

<span data-ttu-id="4c86d-1397">**Значок** ![Значок считывания звуковых данных класса узла](./media/user-guide/usbx-events/image86.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1397">**Icon** ![Host Class Audio Read icon](./media/user-guide/usbx-events/image86.png)</span></span>

<span data-ttu-id="4c86d-1398">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1398">**Description**</span></span>

<span data-ttu-id="4c86d-1399">Это событие представляет собой считывание звуковых данных класса узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1399">This event represents a USBX Host Class Audio Read Event.</span></span>

- <span data-ttu-id="4c86d-1400">Поля сведений</span><span class="sxs-lookup"><span data-stu-id="4c86d-1400">Information Fields</span></span> 
- <span data-ttu-id="4c86d-1401">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1401">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1402">Поле сведений 2. Указатель данных.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1402">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4c86d-1403">Поле сведений 3. Запрошенная длина.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1403">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4c86d-1404">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1404">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-streaming-sampling-get"></a><span data-ttu-id="4c86d-1405">Получение данных для выборки звукового потока для класса узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1405">Host Class Audio Streaming Sampling Get</span></span> 

#### <a name="ux_host_class_audio_streaming_sampling_get"></a><span data-ttu-id="4c86d-1406">ux_host_class_audio_streaming_sampling_get</span><span class="sxs-lookup"><span data-stu-id="4c86d-1406">ux_host_class_audio_streaming_sampling_get</span></span>

<span data-ttu-id="4c86d-1407">**Значок** ![Значок получения данных для выборки звукового потока для класса узла](./media/user-guide/usbx-events/image87.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1407">**Icon** ![Host Class Audio Streaming Sampling Get icon](./media/user-guide/usbx-events/image87.png)</span></span>

<span data-ttu-id="4c86d-1408">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1408">**Description**</span></span>

<span data-ttu-id="4c86d-1409">Это событие представляет собой получение данных для выборки звукового потока для класса узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1409">This event represents a USBX Host Class Audio Streaming Sampling Get Event.</span></span>

<span data-ttu-id="4c86d-1410">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1410">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1411">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1411">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1412">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1412">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1413">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1413">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1414">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1414">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-streaming-sampling-set"></a><span data-ttu-id="4c86d-1415">Задание данных для выборки звукового потока для класса узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1415">Host Class Audio Streaming Sampling Set</span></span> 

#### <a name="ux_host_class_audio_streaming_sampling_set"></a><span data-ttu-id="4c86d-1416">ux_host_class_audio_streaming_sampling_set</span><span class="sxs-lookup"><span data-stu-id="4c86d-1416">ux_host_class_audio_streaming_sampling_set</span></span>

<span data-ttu-id="4c86d-1417">**Значок** ![Значок задания данных для выборки звукового потока для класса узла](./media/user-guide/usbx-events/image88.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1417">**Icon** ![Host Class Audio Streaming Sampling Set icon](./media/user-guide/usbx-events/image88.png)</span></span>

<span data-ttu-id="4c86d-1418">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1418">**Description**</span></span>

<span data-ttu-id="4c86d-1419">Это событие представляет собой задание данных для выборки звукового потока для класса узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1419">This event represents a USBX Host Class Audio Streaming Sampling Set Event.</span></span>

<span data-ttu-id="4c86d-1420">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1420">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1421">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1421">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1422">Поле сведений 2. Выборка звукового потока.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1422">Info Field 2: Audio Sampling.</span></span>
- <span data-ttu-id="4c86d-1423">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1423">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1424">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1424">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-write"></a><span data-ttu-id="4c86d-1425">Запись звука класса узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1425">Host Class Audio Write</span></span> 

#### <a name="ux_host_class_audio_write"></a><span data-ttu-id="4c86d-1426">ux_host_class_audio_write</span><span class="sxs-lookup"><span data-stu-id="4c86d-1426">ux_host_class_audio_write</span></span>

<span data-ttu-id="4c86d-1427">**Значок** ![Значок записи звука класса узла](./media/user-guide/usbx-events/image89.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1427">**Icon** ![Host Class Audio Write icon](./media/user-guide/usbx-events/image89.png)</span></span>

<span data-ttu-id="4c86d-1428">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1428">**Description**</span></span>

<span data-ttu-id="4c86d-1429">Это событие представляет собой запись звука класса узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1429">This event represents a USBX Host Class Audio Write Event.</span></span>

<span data-ttu-id="4c86d-1430">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1430">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1431">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1431">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1432">Поле сведений 2. Указатель данных.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1432">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4c86d-1433">Поле сведений 3. Запрошенная длина.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1433">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4c86d-1434">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1434">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-activate"></a><span data-ttu-id="4c86d-1435">Активация класса Cdc Acm узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1435">Host Class Cdc Acm Activate</span></span> 

#### <a name="ux_host_class_cdc_acm_activate"></a><span data-ttu-id="4c86d-1436">ux_host_class_cdc_acm_activate</span><span class="sxs-lookup"><span data-stu-id="4c86d-1436">ux_host_class_cdc_acm_activate</span></span>

<span data-ttu-id="4c86d-1437">**Значок** ![Значок активации класса Cdc Acm узла](./media/user-guide/usbx-events/image90.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1437">**Icon** ![Host Class C D C A C M Activate icon](./media/user-guide/usbx-events/image90.png)</span></span>

<span data-ttu-id="4c86d-1438">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1438">**Description**</span></span>

<span data-ttu-id="4c86d-1439">Это событие представляет собой активацию класса Cdc Acm узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1439">This event represents a USBX Host Class Cdc Acm Activate Event.</span></span>

<span data-ttu-id="4c86d-1440">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1440">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1441">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1441">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1442">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1442">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1443">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1443">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1444">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1444">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-deactivate"></a><span data-ttu-id="4c86d-1445">Деактивация класса Cdc Acm узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1445">Host Class Cdc Acm Deactivate</span></span> 

#### <a name="ux_host_class_cdc_acm_deactivate"></a><span data-ttu-id="4c86d-1446">ux_host_class_cdc_acm_deactivate</span><span class="sxs-lookup"><span data-stu-id="4c86d-1446">ux_host_class_cdc_acm_deactivate</span></span>

<span data-ttu-id="4c86d-1447">**Значок** ![Значок деактивации класса Cdc Acm узла](./media/user-guide/usbx-events/image91.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1447">**Icon** ![Host Class C D C A C M Deactivate icon](./media/user-guide/usbx-events/image91.png)</span></span>

<span data-ttu-id="4c86d-1448">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1448">**Description**</span></span>

<span data-ttu-id="4c86d-1449">Это событие представляет собой деактивацию класса Cdc Acm узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1449">This event represents a USBX Host Class Cdc Acm Deactivate Event.</span></span>

<span data-ttu-id="4c86d-1450">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1450">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1451">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1451">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1452">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1452">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1453">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1453">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1454">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1454">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-abort-in-pipe"></a><span data-ttu-id="4c86d-1455">Прерывание в канале класса Cdc Acm Ioctl узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1455">Host Class Cdc Acm Ioctl Abort In Pipe</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_abort_in_pipe"></a><span data-ttu-id="4c86d-1456">ux_host_class_cdc_acm_ioctl_abort_in_pipe</span><span class="sxs-lookup"><span data-stu-id="4c86d-1456">ux_host_class_cdc_acm_ioctl_abort_in_pipe</span></span>

<span data-ttu-id="4c86d-1457">**Значок** ![Значок прерывания в канале класса Cdc Acm Ioctl узла](./media/user-guide/usbx-events/image92.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1457">**Icon** ![Host Class C D C A C M I O C T L Abort In Pipe icon](./media/user-guide/usbx-events/image92.png)</span></span>

<span data-ttu-id="4c86d-1458">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1458">**Description**</span></span>

<span data-ttu-id="4c86d-1459">Это событие представляет собой прерывание в канале класса Cdc Acm Ioctl узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1459">This event represents a USBX Host Class Cdc Acm Ioctl Abort In Pipe Event.</span></span>

<span data-ttu-id="4c86d-1460">Поля сведений</span><span class="sxs-lookup"><span data-stu-id="4c86d-1460">Information Fields</span></span> 

- <span data-ttu-id="4c86d-1461">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1461">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1462">Поле сведений 2. Конечная точка.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1462">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="4c86d-1463">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1463">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1464">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1464">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-abort-out-pipe"></a><span data-ttu-id="4c86d-1465">Прерывание вне канала класса Cdc Acm Ioctl узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1465">Host Class Cdc Acm Ioctl Abort Out Pipe</span></span> 

#### <a name="ux_host_class_cdc_acm_ioct_abort_out_pipe"></a><span data-ttu-id="4c86d-1466">ux_host_class_cdc_acm_ioct_abort_out_pipe</span><span class="sxs-lookup"><span data-stu-id="4c86d-1466">ux_host_class_cdc_acm_ioct_abort_out_pipe</span></span>

<span data-ttu-id="4c86d-1467">**Значок** [Значок прерывания вне канала класса Cdc Acm Ioctl узла](./media/user-guide/usbx-events/image93.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1467">**Icon** ![[Host Class C D C A C M I O C T L Abort Out Pipe icon](./media/user-guide/usbx-events/image93.png)</span></span>

<span data-ttu-id="4c86d-1468">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1468">**Description**</span></span>

<span data-ttu-id="4c86d-1469">Это событие представляет собой прерывание вне канала класса Cdc Acm Ioctl узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1469">This event represents a USBX Host Class Cdc Acm Ioctl Abort Out Pipe Event.</span></span>

<span data-ttu-id="4c86d-1470">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1470">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1471">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1471">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1472">Поле сведений 2. Конечная точка.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1472">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="4c86d-1473">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1473">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1474">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1474">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-get-device-status"></a><span data-ttu-id="4c86d-1475">Получение состояния устройства класса Cdc Acm Ioctl узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1475">Host Class Cdc Acm Ioctl Get Device Status</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_get_device_status"></a><span data-ttu-id="4c86d-1476">ux_host_class_cdc_acm_ioctl_get_device_status</span><span class="sxs-lookup"><span data-stu-id="4c86d-1476">ux_host_class_cdc_acm_ioctl_get_device_status</span></span>

<span data-ttu-id="4c86d-1477">**Значок** ![Значок получения состояния устройства класса Cdc Acm Ioctl узла](./media/user-guide/usbx-events/image94.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1477">**Icon** ![Host Class C D C A C M I O C T L Get Device Status icon](./media/user-guide/usbx-events/image94.png)</span></span>

<span data-ttu-id="4c86d-1478">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1478">**Description**</span></span>

<span data-ttu-id="4c86d-1479">Это событие представляет собой получение состояния устройства класса Cdc Acm Ioctl узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1479">This event represents a USBX Host Class Cdc Acm Ioctl Get Device Status Event.</span></span>

<span data-ttu-id="4c86d-1480">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1480">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1481">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1481">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1482">Поле сведений 2. Состояние устройства.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1482">Info Field 2: Device status.</span></span>
- <span data-ttu-id="4c86d-1483">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1483">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1484">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1484">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-get-line-coding"></a><span data-ttu-id="4c86d-1485">Получение кодировки строки в классе Cdc Acm Ioctl узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1485">Host Class Cdc Acm Ioctl Get Line Coding</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_get_line_coding"></a><span data-ttu-id="4c86d-1486">ux_host_class_cdc_acm_ioctl_get_line_coding</span><span class="sxs-lookup"><span data-stu-id="4c86d-1486">ux_host_class_cdc_acm_ioctl_get_line_coding</span></span>

<span data-ttu-id="4c86d-1487">**Значок** ![Значок получения кодировки строки в классе Cdc Acm Ioctl узла](./media/user-guide/usbx-events/image95.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1487">**Icon** ![Host Class C D C A C M I O C T L Get Line Coding icon](./media/user-guide/usbx-events/image95.png)</span></span>

<span data-ttu-id="4c86d-1488">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1488">**Description**</span></span>

<span data-ttu-id="4c86d-1489">Это событие представляет собой получение кодировки строки в классе Cdc Acm Ioctl узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1489">This event represents a USBX Host Class Cdc Acm Ioctl Get Line Coding Event.</span></span>

<span data-ttu-id="4c86d-1490">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1490">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1491">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1491">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1492">Поле сведений 2. Параметр.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1492">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="4c86d-1493">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1493">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1494">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1494">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-notification-callback"></a><span data-ttu-id="4c86d-1495">Обратный вызов уведомления класса Cdc Acm Ioctl узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1495">Host Class Cdc Acm Ioctl Notification Callback</span></span>

#### <a name="ux_host_class_cdc_acm_ioctl_notification_callback"></a><span data-ttu-id="4c86d-1496">ux_host_class_cdc_acm_ioctl_notification_callback</span><span class="sxs-lookup"><span data-stu-id="4c86d-1496">ux_host_class_cdc_acm_ioctl_notification_callback</span></span>

<span data-ttu-id="4c86d-1497">**Значок** ![Значок обратного вызова уведомления класса Cdc Acm Ioctl узла](./media/user-guide/usbx-events/image96.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1497">**Icon** ![Host Class C D C A C M I O C T L Notification Callback icon](./media/user-guide/usbx-events/image96.png)</span></span>

<span data-ttu-id="4c86d-1498">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1498">**Description**</span></span>

<span data-ttu-id="4c86d-1499">Это событие представляет собой обратный вызов уведомления класса Cdc Acm Ioctl узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1499">This event represents a USBX Host Class Cdc Acm Ioctl Notification Callback Event.</span></span>

<span data-ttu-id="4c86d-1500">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1500">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1501">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1501">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1502">Поле сведений 2. Параметр.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1502">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="4c86d-1503">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1503">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1504">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1504">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-send-break"></a><span data-ttu-id="4c86d-1505">Остановка отправки класса Cdc Acm Ioctl узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1505">Host Class Cdc Acm Ioctl Send Break</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_send_break"></a><span data-ttu-id="4c86d-1506">ux_host_class_cdc_acm_ioctl_send_break</span><span class="sxs-lookup"><span data-stu-id="4c86d-1506">ux_host_class_cdc_acm_ioctl_send_break</span></span>

<span data-ttu-id="4c86d-1507">**Значок** ![Значок остановки отправки класса Cdc Acm Ioctl узла](./media/user-guide/usbx-events/image97.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1507">**Icon** ![Host Class C D C A C M I O C T L Send Break icon](./media/user-guide/usbx-events/image97.png)</span></span>

<span data-ttu-id="4c86d-1508">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1508">**Description**</span></span>

<span data-ttu-id="4c86d-1509">Это событие представляет собой остановку отправки класса Cdc Acm Ioctl узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1509">This event represents a USBX Host Class Cdc Acm Ioctl Send Break Event.</span></span>

<span data-ttu-id="4c86d-1510">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1510">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1511">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1511">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1512">Поле сведений 2. Параметр.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1512">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="4c86d-1513">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1513">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1514">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1514">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-set-line-coding"></a><span data-ttu-id="4c86d-1515">Задание кодировки строки в классе Cdc Acm Ioctl узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1515">Host Class Cdc Acm Ioctl Set Line Coding</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_set_line_coding"></a><span data-ttu-id="4c86d-1516">ux_host_class_cdc_acm_ioctl_set_line_coding</span><span class="sxs-lookup"><span data-stu-id="4c86d-1516">ux_host_class_cdc_acm_ioctl_set_line_coding</span></span>

<span data-ttu-id="4c86d-1517">**Значок** ![Значок задания кодировки строки в классе Cdc Acm Ioctl узла](./media/user-guide/usbx-events/image97.png) значок](./media/user-guide/usbx-events/image98.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1517">**Icon** ![The Host Class C D C A C M I O C T L Set Line Coding icon](./media/user-guide/usbx-events/image97.png) icon](./media/user-guide/usbx-events/image98.png)</span></span>

<span data-ttu-id="4c86d-1518">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1518">**Description**</span></span>

<span data-ttu-id="4c86d-1519">Это событие представляет собой задание кодировки строки в классе Cdc Acm Ioctl узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1519">This event represents a USBX Host Class Cdc Acm Ioctl Set Line Coding Event.</span></span>

<span data-ttu-id="4c86d-1520">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1520">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1521">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1521">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1522">Поле сведений 2. Параметр.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1522">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="4c86d-1523">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1523">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1524">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1524">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-set-line-state"></a><span data-ttu-id="4c86d-1525">Задание состояния кодировки строки в классе Cdc Acm Ioctl узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1525">Host Class Cdc Acm Ioctl Set Line State</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_set_line_state"></a><span data-ttu-id="4c86d-1526">ux_host_class_cdc_acm_ioctl_set_line_state</span><span class="sxs-lookup"><span data-stu-id="4c86d-1526">ux_host_class_cdc_acm_ioctl_set_line_state</span></span>

<span data-ttu-id="4c86d-1527">**Значок** ![Значок задания состояния кодировки строки в классе Cdc Acm Ioctl узла](./media/user-guide/usbx-events/image99.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1527">**Icon** ![Host Class C D C A C M I O C T L Set Line State icon](./media/user-guide/usbx-events/image99.png)</span></span>

<span data-ttu-id="4c86d-1528">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1528">**Description**</span></span>

<span data-ttu-id="4c86d-1529">Это событие представляет собой задание состояния кодировки строки в классе Cdc Acm Ioctl узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1529">This event represents a USBX Host Class Cdc Acm Ioctl Set Line State Event.</span></span>

<span data-ttu-id="4c86d-1530">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1530">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1531">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1531">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1532">Поле сведений 2. Параметр.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1532">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="4c86d-1533">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1533">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1534">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1534">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-read"></a><span data-ttu-id="4c86d-1535">Считывание класса Cdc Acm узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1535">Host Class Cdc Acm Read</span></span> 

#### <a name="ux_host_class_cdc_acm_read"></a><span data-ttu-id="4c86d-1536">ux_host_class_cdc_acm_read</span><span class="sxs-lookup"><span data-stu-id="4c86d-1536">ux_host_class_cdc_acm_read</span></span>

<span data-ttu-id="4c86d-1537">**Значок** ![Значок считывания класса Cdc Acm узла](./media/user-guide/usbx-events/image100.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1537">**Icon** ![Host Class C D C A C M Read icon](./media/user-guide/usbx-events/image100.png)</span></span>

<span data-ttu-id="4c86d-1538">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1538">**Description**</span></span>

<span data-ttu-id="4c86d-1539">Это событие представляет собой считывание класса Cdc Acm узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1539">This event represents a USBX Host Class Cdc Acm Read Event.</span></span>

<span data-ttu-id="4c86d-1540">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1540">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1541">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1541">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1542">Поле сведений 2. Указатель данных.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1542">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4c86d-1543">Поле сведений 3. Запрошенная длина.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1543">Info Field 3: Requested Length.</span></span>
- <span data-ttu-id="4c86d-1544">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1544">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-reception-start"></a><span data-ttu-id="4c86d-1545">Запуск приема класса Cdc Acm узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1545">Host Class Cdc Acm Reception Start</span></span> 

#### <a name="ux_host_class_cdc_acm_reception_start"></a><span data-ttu-id="4c86d-1546">ux_host_class_cdc_acm_reception_start</span><span class="sxs-lookup"><span data-stu-id="4c86d-1546">ux_host_class_cdc_acm_reception_start</span></span>

<span data-ttu-id="4c86d-1547">**Значок** ![Значок запуска приема класса Cdc Acm узла](./media/user-guide/usbx-events/image101.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1547">**Icon** ![Host Class C D C A C M Reception Start icon](./media/user-guide/usbx-events/image101.png)</span></span>

<span data-ttu-id="4c86d-1548">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1548">**Description**</span></span>

<span data-ttu-id="4c86d-1549">Это событие представляет собой запуск приема узла класса Cdc Acm узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1549">This event represents a USBX Host Class Cdc Acm Reception Start Event.</span></span>

<span data-ttu-id="4c86d-1550">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1550">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1551">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1551">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1552">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1552">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1553">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1553">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1554">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1554">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-reception-stop"></a><span data-ttu-id="4c86d-1555">Остановка приема класса Cdc Acm узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1555">Host Class Cdc Acm Reception Stop</span></span> 

#### <a name="ux_host_class_cdc_acm_reception_stop"></a><span data-ttu-id="4c86d-1556">ux_host_class_cdc_acm_reception_stop</span><span class="sxs-lookup"><span data-stu-id="4c86d-1556">ux_host_class_cdc_acm_reception_stop</span></span>

<span data-ttu-id="4c86d-1557">**Значок** ![Значок остановки приема класса Cdc Acm узла](./media/user-guide/usbx-events/image102.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1557">**Icon** ![Host Class C D C A C M Reception Stop icon](./media/user-guide/usbx-events/image102.png)</span></span>

<span data-ttu-id="4c86d-1558">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1558">**Description**</span></span>

<span data-ttu-id="4c86d-1559">Это событие представляет собой остановку приема класса Cdc Acm узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1559">This event represents a USBX Host Class Cdc Acm Reception Stop Event.</span></span>

<span data-ttu-id="4c86d-1560">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1560">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1561">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1561">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1562">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1562">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1563">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1563">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-write"></a><span data-ttu-id="4c86d-1564">Запись класса Cdc Acm узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1564">Host Class Cdc Acm Write</span></span> 

#### <a name="ux_host_class_acm_write"></a><span data-ttu-id="4c86d-1565">ux_host_class_acm_write</span><span class="sxs-lookup"><span data-stu-id="4c86d-1565">ux_host_class_acm_write</span></span>

<span data-ttu-id="4c86d-1566">**Значок** ![Значок записи класса Cdc Acm узла](./media/user-guide/usbx-events/image103.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1566">**Icon** ![Host Class C D C A C M Write icon](./media/user-guide/usbx-events/image103.png)</span></span>

<span data-ttu-id="4c86d-1567">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1567">**Description**</span></span>

<span data-ttu-id="4c86d-1568">Это событие представляет собой запись класса Cdc Acm узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1568">This event represents a USBX Host Class Cdc Acm Write Event.</span></span>

<span data-ttu-id="4c86d-1569">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1569">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1570">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1570">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1571">Поле сведений 2. Указатель данных.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1571">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4c86d-1572">Поле сведений 3. Запрошенная длина.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1572">Info Field 3: Requested Length.</span></span>
- <span data-ttu-id="4c86d-1573">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1573">Info Field 4: Not used.</span></span>

### <a name="host-class-dpump-activate"></a><span data-ttu-id="4c86d-1574">Активация класса Dpump узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1574">Host Class Dpump Activate</span></span> 

#### <a name="ux_host_class_dpump_activate"></a><span data-ttu-id="4c86d-1575">ux_host_class_dpump_activate</span><span class="sxs-lookup"><span data-stu-id="4c86d-1575">ux_host_class_dpump_activate</span></span>

<span data-ttu-id="4c86d-1576">**Значок** ![Значок активации класса Dpump узла](./media/user-guide/usbx-events/image104.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1576">**Icon** ![Host Class Dpump Activate icon](./media/user-guide/usbx-events/image104.png)</span></span>

<span data-ttu-id="4c86d-1577">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1577">**Description**</span></span>

<span data-ttu-id="4c86d-1578">Это событие представляет собой активацию класса Dpump узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1578">This event represents a USBX Host Class Dpump Activate Event.</span></span>

<span data-ttu-id="4c86d-1579">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1579">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1580">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1580">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1581">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1581">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1582">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1582">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1583">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1583">Info Field 4: Not used.</span></span>

### <a name="host-class-dpump-deactivate"></a><span data-ttu-id="4c86d-1584">Деактивация класса Dpump узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1584">Host Class Dpump Deactivate</span></span> 

#### <a name="ux_host_class_dpump_deactivate"></a><span data-ttu-id="4c86d-1585">ux_host_class_dpump_deactivate</span><span class="sxs-lookup"><span data-stu-id="4c86d-1585">ux_host_class_dpump_deactivate</span></span>

<span data-ttu-id="4c86d-1586">**Значок** ![Значок деактивации класса Dpump узла](./media/user-guide/usbx-events/image105.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1586">**Icon** ![Host Class Dpump Deactivate icon](./media/user-guide/usbx-events/image105.png)</span></span>

<span data-ttu-id="4c86d-1587">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1587">**Description**</span></span>

<span data-ttu-id="4c86d-1588">Это событие представляет собой деактивацию класса Dpump узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1588">This event represents a USBX Host Class Dpump Deactivate Event.</span></span>

<span data-ttu-id="4c86d-1589">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1589">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1590">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1590">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1591">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1591">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1592">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1592">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1593">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1593">Info Field 4: Not used.</span></span>

### <a name="host-class-dpump-read"></a><span data-ttu-id="4c86d-1594">Считывание класса Dpump узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1594">Host Class Dpump Read</span></span> 

#### <a name="ux_host_class_dpump_read"></a><span data-ttu-id="4c86d-1595">ux_host_class_dpump_read</span><span class="sxs-lookup"><span data-stu-id="4c86d-1595">ux_host_class_dpump_read</span></span>

<span data-ttu-id="4c86d-1596">**Значок** ![Значок считывания класса Dpump узла](./media/user-guide/usbx-events/image106.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1596">**Icon** ![Host Class Dpump Read icon](./media/user-guide/usbx-events/image106.png)</span></span>

<span data-ttu-id="4c86d-1597">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1597">**Description**</span></span>

<span data-ttu-id="4c86d-1598">Это событие представляет собой считывание класса Dpump узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1598">This event represents a USBX Host Class Dpump Read Event.</span></span>

<span data-ttu-id="4c86d-1599">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1599">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1600">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1600">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1601">Поле сведений 2. Указатель данных.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1601">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4c86d-1602">Поле сведений 3. Запрошенная длина.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1602">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4c86d-1603">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1603">Info Field 4: Not used.</span></span>

### <a name="host-class-dpump-write"></a><span data-ttu-id="4c86d-1604">Запись класса Dpump узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1604">Host Class Dpump Write</span></span> 

#### <a name="ux_host_class_dpump_write"></a><span data-ttu-id="4c86d-1605">ux_host_class_dpump_write</span><span class="sxs-lookup"><span data-stu-id="4c86d-1605">ux_host_class_dpump_write</span></span>

<span data-ttu-id="4c86d-1606">**Значок** ![Значок записи класса Dpump узла](./media/user-guide/usbx-events/image107.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1606">**Icon** ![Host Class Dpump Write icon](./media/user-guide/usbx-events/image107.png)</span></span>

<span data-ttu-id="4c86d-1607">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1607">**Description**</span></span>

<span data-ttu-id="4c86d-1608">Это событие представляет собой запись класса Dpump узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1608">This event represents a USBX Host Class Dpump Write Event.</span></span>

<span data-ttu-id="4c86d-1609">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1609">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1610">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1610">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1611">Поле сведений 2. Указатель данных.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1611">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4c86d-1612">Поле сведений 3. Запрошенная длина.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1612">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4c86d-1613">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1613">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-activate"></a><span data-ttu-id="4c86d-1614">Активация класса Hid узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1614">Host Class Hid Activate</span></span> 

#### <a name="ux_host_class_hid_activate"></a><span data-ttu-id="4c86d-1615">ux_host_class_hid_activate</span><span class="sxs-lookup"><span data-stu-id="4c86d-1615">ux_host_class_hid_activate</span></span>

<span data-ttu-id="4c86d-1616">**Значок** ![Значок активации класса Hid узла](./media/user-guide/usbx-events/image108.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1616">**Icon** ![Host Class Hid Activate icon](./media/user-guide/usbx-events/image108.png)</span></span>

<span data-ttu-id="4c86d-1617">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1617">**Description**</span></span>

<span data-ttu-id="4c86d-1618">Это событие представляет собой активацию класса Hid узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1618">This event represents a USBX Host Class Hid Activate Event.</span></span>

<span data-ttu-id="4c86d-1619">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1619">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1620">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1620">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1621">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1621">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1622">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1622">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1623">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1623">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-client-register"></a><span data-ttu-id="4c86d-1624">Регистрация клиента класса Hid узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1624">Host Class Hid Client Register</span></span> 

#### <a name="ux_host_class_hid_client_register"></a><span data-ttu-id="4c86d-1625">ux_host_class_hid_client_register</span><span class="sxs-lookup"><span data-stu-id="4c86d-1625">ux_host_class_hid_client_register</span></span>

<span data-ttu-id="4c86d-1626">**Значок** ![Значок регистрации клиента класса Hid узла](./media/user-guide/usbx-events/image109.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1626">**Icon** ![Host Class Hid Client Register icon](./media/user-guide/usbx-events/image109.png)</span></span>

<span data-ttu-id="4c86d-1627">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1627">**Description**</span></span>

<span data-ttu-id="4c86d-1628">Это событие представляет собой регистрацию клиента класса Hid узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1628">This event represents a USBX Host Class Hid Client Register Event.</span></span>

<span data-ttu-id="4c86d-1629">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1629">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1630">Поле сведений 1. Имя клиента Hid.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1630">Info Field 1: Hid client name.</span></span>
- <span data-ttu-id="4c86d-1631">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1631">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1632">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1632">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1633">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1633">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-deactivate"></a><span data-ttu-id="4c86d-1634">Деактивация класса Hid узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1634">Host Class Hid Deactivate</span></span> 

#### <a name="ux_host_class_hid_deactivate"></a><span data-ttu-id="4c86d-1635">ux_host_class_hid_deactivate</span><span class="sxs-lookup"><span data-stu-id="4c86d-1635">ux_host_class_hid_deactivate</span></span>

<span data-ttu-id="4c86d-1636">**Значок** ![Значок деактивации класса Hid узла](./media/user-guide/usbx-events/image110.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1636">**Icon** ![Host Class Hid Deactivate icon](./media/user-guide/usbx-events/image110.png)</span></span>

<span data-ttu-id="4c86d-1637">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1637">**Description**</span></span>

<span data-ttu-id="4c86d-1638">Это событие представляет собой деактивацию класса Hid узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1638">This event represents a USBX Host Class Hid Deactivate Event.</span></span>

<span data-ttu-id="4c86d-1639">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1639">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1640">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1640">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1641">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1641">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1642">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1642">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1643">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1643">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-idle-get"></a><span data-ttu-id="4c86d-1644">Получение состояния бездействия класса Hid узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1644">Host Class Hid Idle Get</span></span> 

#### <a name="ux_host_class_hid_idle_get"></a><span data-ttu-id="4c86d-1645">ux_host_class_hid_idle_get</span><span class="sxs-lookup"><span data-stu-id="4c86d-1645">ux_host_class_hid_idle_get</span></span>

<span data-ttu-id="4c86d-1646">**Значок** ![Значок получения состояния бездействия класса Hid узла](./media/user-guide/usbx-events/image111.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1646">**Icon** ![Host Class Hid Idle Get icon](./media/user-guide/usbx-events/image111.png)</span></span>

<span data-ttu-id="4c86d-1647">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1647">**Description**</span></span>

<span data-ttu-id="4c86d-1648">Это событие представляет собой получение состояния бездействия класса Hid узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1648">This event represents a USBX Host Class Hid Idle Get Event.</span></span>

<span data-ttu-id="4c86d-1649">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1649">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1650">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1650">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1651">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1651">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1652">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1652">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1653">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1653">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-idle-set"></a><span data-ttu-id="4c86d-1654">Задание состояния бездействия класса Hid узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1654">Host Class Hid Idle Set</span></span> 

#### <a name="ux_host_class_hid_idle_set"></a><span data-ttu-id="4c86d-1655">ux_host_class_hid_idle_set</span><span class="sxs-lookup"><span data-stu-id="4c86d-1655">ux_host_class_hid_idle_set</span></span>

<span data-ttu-id="4c86d-1656">**Значок** ![Значок задания состояния бездействия класса Hid узла](./media/user-guide/usbx-events/image112.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1656">**Icon** ![Host Class Hid Idle Set icon](./media/user-guide/usbx-events/image112.png)</span></span>

<span data-ttu-id="4c86d-1657">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1657">**Description**</span></span>

<span data-ttu-id="4c86d-1658">Это событие представляет собой задание состояния бездействия класса Hid узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1658">This event represents a USBX Host Class Hid Idle Set Event.</span></span>

<span data-ttu-id="4c86d-1659">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1659">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1660">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1660">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1661">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1661">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1662">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1662">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1663">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1663">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-keyboard-activate"></a><span data-ttu-id="4c86d-1664">Активация клавиатуры для класса Hid узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1664">Host Class Hid Keyboard Activate</span></span> 

#### <a name="ux_host_class_hid_keyboard_activate"></a><span data-ttu-id="4c86d-1665">ux_host_class_hid_keyboard_activate</span><span class="sxs-lookup"><span data-stu-id="4c86d-1665">ux_host_class_hid_keyboard_activate</span></span>

<span data-ttu-id="4c86d-1666">**Значок** ![Значок активации клавиатуры для класса Hid узла](./media/user-guide/usbx-events/image113.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1666">**Icon** ![Host Class Hid Keyboard Activate icon](./media/user-guide/usbx-events/image113.png)</span></span>

<span data-ttu-id="4c86d-1667">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1667">**Description**</span></span>

<span data-ttu-id="4c86d-1668">Это событие представляет собой активацию клавиатуры для класса Hid узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1668">This event represents a USBX Host Class Hid Keyboard Activate Event.</span></span>

<span data-ttu-id="4c86d-1669">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1669">**Information Fields**</span></span>
<p><span data-ttu-id="4c86d-1670">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1670">Info Field 1: Class instance.</span></span>
<p><span data-ttu-id="4c86d-1671">Поле сведений 2. Экземпляр клиента Hid.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1671">Info Field 2: Hid client instance.</span></span>
<p><span data-ttu-id="4c86d-1672">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1672">Info Field 3: Not used.</span></span>
<p><span data-ttu-id="4c86d-1673">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1673">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-keyboard-deactivate"></a><span data-ttu-id="4c86d-1674">Деактивация клавиатуры для класса Hid узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1674">Host Class Hid Keyboard Deactivate</span></span> 

#### <a name="ux_host_class_hid_keyboard_deactivate"></a><span data-ttu-id="4c86d-1675">ux_host_class_hid_keyboard_deactivate</span><span class="sxs-lookup"><span data-stu-id="4c86d-1675">ux_host_class_hid_keyboard_deactivate</span></span>

<span data-ttu-id="4c86d-1676">**Значок** ![Значок деактивации клавиатуры для класса Hid узла](./media/user-guide/usbx-events/image114.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1676">**Icon** ![Host Class Hid Keyboard Deactivate icon](./media/user-guide/usbx-events/image114.png)</span></span>

<span data-ttu-id="4c86d-1677">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1677">**Description**</span></span>

<span data-ttu-id="4c86d-1678">Это событие представляет собой деактивацию клавиатуры для класса Hid узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1678">This event represents a USBX Host Class Hid Keyboard Deactivate Event.</span></span>

<span data-ttu-id="4c86d-1679">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1679">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1680">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1680">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1681">Поле сведений 2. Экземпляр клиента Hid.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1681">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="4c86d-1682">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1682">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1683">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1683">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-mouse-activate"></a><span data-ttu-id="4c86d-1684">Активация мыши для класса Hid узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1684">Host Class Hid Mouse Activate</span></span> 

#### <a name="ux_host_class_hid_mouse_activate"></a><span data-ttu-id="4c86d-1685">ux_host_class_hid_mouse_activate</span><span class="sxs-lookup"><span data-stu-id="4c86d-1685">ux_host_class_hid_mouse_activate</span></span>

<span data-ttu-id="4c86d-1686">**Значок** ![Значок активации мыши для класса Hid узла](./media/user-guide/usbx-events/image115.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1686">**Icon** ![Host Class Hid Mouse Activate icon](./media/user-guide/usbx-events/image115.png)</span></span>

<span data-ttu-id="4c86d-1687">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1687">**Description**</span></span>

<span data-ttu-id="4c86d-1688">Это событие представляет собой активацию мыши для класса Hid узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1688">This event represents a USBX Host Class Hid Mouse Activate Event.</span></span>

<span data-ttu-id="4c86d-1689">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1689">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1690">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1690">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1691">Поле сведений 2. Экземпляр клиента Hid.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1691">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="4c86d-1692">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1692">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1693">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1693">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-mouse-deactivate"></a><span data-ttu-id="4c86d-1694">Деактивация мыши для класса Hid узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1694">Host Class Hid Mouse Deactivate</span></span> 

#### <a name="ux_host_class_hid_mouse_deactivate"></a><span data-ttu-id="4c86d-1695">ux_host_class_hid_mouse_deactivate</span><span class="sxs-lookup"><span data-stu-id="4c86d-1695">ux_host_class_hid_mouse_deactivate</span></span>

<span data-ttu-id="4c86d-1696">**Значок** ![Значок деактивации мыши для класса Hid узла](./media/user-guide/usbx-events/image116.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1696">**Icon** ![Host Class Hid Mouse Deactivate icon](./media/user-guide/usbx-events/image116.png)</span></span>

<span data-ttu-id="4c86d-1697">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1697">**Description**</span></span>

- <span data-ttu-id="4c86d-1698">Это событие представляет собой деактивацию мыши для класса Hid узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1698">This event represents a USBX Host Class Hid Mouse Deactivate Event.</span></span>

<span data-ttu-id="4c86d-1699">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1699">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1700">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1700">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1701">Поле сведений 2. Экземпляр клиента Hid.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1701">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="4c86d-1702">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1702">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1703">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1703">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-remote-control-activate"></a><span data-ttu-id="4c86d-1704">Активация удаленного управления для класса Hid узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1704">Host Class Hid Remote Control Activate</span></span> 

#### <a name="ux_host_class_hid_remote_control_activate"></a><span data-ttu-id="4c86d-1705">ux_host_class_hid_remote_control_activate</span><span class="sxs-lookup"><span data-stu-id="4c86d-1705">ux_host_class_hid_remote_control_activate</span></span>

<span data-ttu-id="4c86d-1706">**Значок** ![Значок активации удаленного управления для класса Hid узла](./media/user-guide/usbx-events/image117.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1706">**Icon** ![Host Class Hid Remote Control Activate icon](./media/user-guide/usbx-events/image117.png)</span></span>

<span data-ttu-id="4c86d-1707">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1707">**Description**</span></span>

<span data-ttu-id="4c86d-1708">Это событие представляет собой активацию удаленного управления для класса Hid узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1708">This event represents a USBX Host Class Hid Remote Control Activate Event.</span></span>

<span data-ttu-id="4c86d-1709">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1709">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1710">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1710">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1711">Поле сведений 2. Экземпляр клиента Hid.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1711">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="4c86d-1712">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1712">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1713">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1713">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-remote-control-deactivate"></a><span data-ttu-id="4c86d-1714">Деактивация удаленного управления для класса Hid узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1714">Host Class Hid Remote Control Deactivate</span></span> 

#### <a name="ux_host_class_hid_remote_control_deactivate"></a><span data-ttu-id="4c86d-1715">ux_host_class_hid_remote_control_deactivate</span><span class="sxs-lookup"><span data-stu-id="4c86d-1715">ux_host_class_hid_remote_control_deactivate</span></span>

<span data-ttu-id="4c86d-1716">**Значок** ![Значок деактивации удаленного управления для класса Hid узла](./media/user-guide/usbx-events/image118.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1716">**Icon** ![Host Class Hid Remote Control Deactivate icon](./media/user-guide/usbx-events/image118.png)</span></span>

<span data-ttu-id="4c86d-1717">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1717">**Description**</span></span>

<span data-ttu-id="4c86d-1718">Это событие представляет собой деактивацию удаленного управления для класса Hid узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1718">This event represents a USBX Host Class Hid Remote Control Deactivate Event.</span></span>

<span data-ttu-id="4c86d-1719">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1719">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1720">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1720">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1721">Поле сведений 2. Экземпляр клиента Hid.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1721">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="4c86d-1722">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1722">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1723">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1723">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-report-get"></a><span data-ttu-id="4c86d-1724">Получение отчета класса Hid узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1724">Host Class Hid Report Get</span></span> 

#### <a name="ux_host_class_hid_report_get"></a><span data-ttu-id="4c86d-1725">ux_host_class_hid_report_get</span><span class="sxs-lookup"><span data-stu-id="4c86d-1725">ux_host_class_hid_report_get</span></span>

<span data-ttu-id="4c86d-1726">**Значок** ![Значок получения отчета класса Hid узла](./media/user-guide/usbx-events/image119.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1726">**Icon** ![Host Class Hid Report Get icon](./media/user-guide/usbx-events/image119.png)</span></span>

<span data-ttu-id="4c86d-1727">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1727">**Description**</span></span>

<span data-ttu-id="4c86d-1728">Это событие представляет собой получение отчета класса Hid узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1728">This event represents a USBX Host Class Hid Report Get.</span></span>

<span data-ttu-id="4c86d-1729">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1729">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1730">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1730">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1731">Поле сведений 2. Отчет клиента.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1731">Info Field 2: Client report.</span></span>
- <span data-ttu-id="4c86d-1732">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1732">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1733">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1733">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-report-set"></a><span data-ttu-id="4c86d-1734">Набор отчетов класса Hid узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1734">Host Class Hid Report Set</span></span> 

#### <a name="ux_host_class_hid_report_set"></a><span data-ttu-id="4c86d-1735">ux_host_class_hid_report_set</span><span class="sxs-lookup"><span data-stu-id="4c86d-1735">ux_host_class_hid_report_set</span></span>

<span data-ttu-id="4c86d-1736">**Значок** ![Значок набора отчетов класса Hid узла](./media/user-guide/usbx-events/image120.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1736">**Icon** ![Host Class Hid Report Set icon](./media/user-guide/usbx-events/image120.png)</span></span>

<span data-ttu-id="4c86d-1737">**Описание**. Это событие представляет собой событие набора отчетов класса Hid узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1737">**Description** This event represents a USBX Host Class Hid Report Set.</span></span>

<span data-ttu-id="4c86d-1738">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1738">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1739">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1739">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1740">Поле сведений 2. Отчет клиента.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1740">Info Field 2: Client report.</span></span>
- <span data-ttu-id="4c86d-1741">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1741">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1742">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1742">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-activate"></a><span data-ttu-id="4c86d-1743">Активация концентратора класса узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1743">Host Class Hub Activate</span></span> 

#### <a name="ux_host_class_hub_activate"></a><span data-ttu-id="4c86d-1744">ux_host_class_hub_activate</span><span class="sxs-lookup"><span data-stu-id="4c86d-1744">ux_host_class_hub_activate</span></span>

<span data-ttu-id="4c86d-1745">**Значок** ![Значок активации концентратора класса узла](./media/user-guide/usbx-events/image121.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1745">**Icon** ![Host Class Hub Activate icon](./media/user-guide/usbx-events/image121.png)</span></span>

<span data-ttu-id="4c86d-1746">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1746">**Description**</span></span>

<span data-ttu-id="4c86d-1747">Это событие представляет собой активацию концентратора класса узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1747">This event represents a USBX Host Class Hub Activate Event.</span></span>

<span data-ttu-id="4c86d-1748">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1748">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-1749">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1749">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1750">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1750">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1751">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1751">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1752">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1752">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-change-detect"></a><span data-ttu-id="4c86d-1753">Обнаружение изменений концентратора в классе узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1753">Host Class Hub Change Detect</span></span> 

#### <a name="ux_host_class_hub_change_detect"></a><span data-ttu-id="4c86d-1754">ux_host_class_hub_change_detect</span><span class="sxs-lookup"><span data-stu-id="4c86d-1754">ux_host_class_hub_change_detect</span></span>

<span data-ttu-id="4c86d-1755">**Значок** ![Значок обнаружения изменений концентратора в классе узла](./media/user-guide/usbx-events/image122.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1755">**Icon** ![Host Class Hub Change Detect icon](./media/user-guide/usbx-events/image122.png)</span></span>

<span data-ttu-id="4c86d-1756">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1756">**Description**</span></span>

<span data-ttu-id="4c86d-1757">Это событие представляет собой обнаружение изменений концентратора в классе узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1757">This event represents a USBX Host Class Hub Change Detect Event.</span></span>

<span data-ttu-id="4c86d-1758">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1758">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1759">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1759">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1760">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1760">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1761">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1761">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1762">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1762">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-deactivate"></a><span data-ttu-id="4c86d-1763">Деактивация концентратора класса узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1763">Host Class Hub Deactivate</span></span> 

#### <a name="ux_host_class_hub_deactivate"></a><span data-ttu-id="4c86d-1764">x_host_class_hub_deactivate</span><span class="sxs-lookup"><span data-stu-id="4c86d-1764">ux_host_class_hub_deactivate</span></span>

<span data-ttu-id="4c86d-1765">**Значок** ![Значок деактивации концентратора класса узла](./media/user-guide/usbx-events/image123.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1765">**Icon** ![Host Class Hub Deactivate icon](./media/user-guide/usbx-events/image123.png)</span></span>

<span data-ttu-id="4c86d-1766">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1766">**Description**</span></span>

<span data-ttu-id="4c86d-1767">Это событие представляет собой деактивацию концентратора класса узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1767">This event represents a USBX Host Class Hub Deactivate Event.</span></span>

<span data-ttu-id="4c86d-1768">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1768">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1769">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1769">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1770">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1770">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1771">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1771">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1772">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1772">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-connection-process"></a><span data-ttu-id="4c86d-1773">Процесс подключения для изменения порта концентратора класса узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1773">Host Class Hub Port Change Connection Process</span></span> 

#### <a name="ux_host_class_hub_change_connection_process"></a><span data-ttu-id="4c86d-1774">ux_host_class_hub_change_connection_process</span><span class="sxs-lookup"><span data-stu-id="4c86d-1774">ux_host_class_hub_change_connection_process</span></span>

<span data-ttu-id="4c86d-1775">**Значок** ![Значок процесса подключения для изменения порта концентратора класса узла](./media/user-guide/usbx-events/image124.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1775">**Icon** ![Host Class Hub Port Change Connection Process icon](./media/user-guide/usbx-events/image124.png)</span></span>

<span data-ttu-id="4c86d-1776">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1776">**Description**</span></span>

<span data-ttu-id="4c86d-1777">Это событие представляет собой процесс подключения для изменения порта концентратора класса узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1777">This event represents a USBX Host Class Hub Port Change Connection Process Event.</span></span>

<span data-ttu-id="4c86d-1778">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1778">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1779">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1779">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1780">Поле сведений 2. Порт.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1780">Info Field 2: Port.</span></span>
- <span data-ttu-id="4c86d-1781">Поле сведений 3. Состояние порта.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1781">Info Field 3: Port status.</span></span>
- <span data-ttu-id="4c86d-1782">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1782">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-enable-process"></a><span data-ttu-id="4c86d-1783">Процесс включения для изменения порта концентратора класса узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1783">Host Class Hub Port Change Enable Process</span></span> 

#### <a name="ux_host_class_hub_port_change_enable_process"></a><span data-ttu-id="4c86d-1784">ux_host_class_hub_port_change_enable_process</span><span class="sxs-lookup"><span data-stu-id="4c86d-1784">ux_host_class_hub_port_change_enable_process</span></span>

<span data-ttu-id="4c86d-1785">**Значок** ![Значок процесса включения для изменения порта концентратора класса узла](./media/user-guide/usbx-events/image125.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1785">**Icon** ![Host Class Hub Port Change Enable Process icon](./media/user-guide/usbx-events/image125.png)</span></span>

<span data-ttu-id="4c86d-1786">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1786">**Description**</span></span>

<span data-ttu-id="4c86d-1787">Это событие представляет собой процесс включения для изменения порта концентратора класса узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1787">This event represents a USBX Host Class Hub Port Change Enable Process Event.</span></span>

<span data-ttu-id="4c86d-1788">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1788">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1789">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1789">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1790">Поле сведений 2. Порт.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1790">Info Field 2: Port.</span></span>
- <span data-ttu-id="4c86d-1791">Поле сведений 3. Состояние порта.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1791">Info Field 3: Port status.</span></span>
- <span data-ttu-id="4c86d-1792">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1792">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-over-current-process"></a><span data-ttu-id="4c86d-1793">Завершение текущего процесса для изменения порта концентратора класса узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1793">Host Class Hub Port Change Over Current Process</span></span> 

#### <a name="ux_host_class_hub_port_change_over_current_process"></a><span data-ttu-id="4c86d-1794">ux_host_class_hub_port_change_over_current_process</span><span class="sxs-lookup"><span data-stu-id="4c86d-1794">ux_host_class_hub_port_change_over_current_process</span></span>

<span data-ttu-id="4c86d-1795">**Значок** ![Значок завершения текущего процесса для изменения порта концентратора класса узла](./media/user-guide/usbx-events/image126.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1795">**Icon** ![Host Class Hub Port Change Over Current Process icon](./media/user-guide/usbx-events/image126.png)</span></span>

<span data-ttu-id="4c86d-1796">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1796">**Description**</span></span>

<span data-ttu-id="4c86d-1797">Это событие представляет собой выделение пакета с помощью nx_packet_allocate.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1797">This event represents allocating a packet via nx_packet_allocate.</span></span>

<span data-ttu-id="4c86d-1798">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1798">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1799">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1799">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1800">Поле сведений 2. Порт.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1800">Info Field 2: Port.</span></span>
- <span data-ttu-id="4c86d-1801">Поле сведений 3. Состояние порта.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1801">Info Field 3: Port status.</span></span>
- <span data-ttu-id="4c86d-1802">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1802">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-reset-process"></a><span data-ttu-id="4c86d-1803">Процесс сброса для изменения порта концентратора класса узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1803">Host Class Hub Port Change Reset Process</span></span> 

#### <a name="ux_host_class_hub_port_change_reset_process"></a><span data-ttu-id="4c86d-1804">ux_host_class_hub_port_change_reset_process</span><span class="sxs-lookup"><span data-stu-id="4c86d-1804">ux_host_class_hub_port_change_reset_process</span></span>

<span data-ttu-id="4c86d-1805">**Значок** ![Значок процесса сброса для изменения порта концентратора класса узла](./media/user-guide/usbx-events/image127.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1805">**Icon** ![Host Class Hub Port Change Reset Process icon](./media/user-guide/usbx-events/image127.png)</span></span>

<span data-ttu-id="4c86d-1806">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1806">**Description**</span></span>

<span data-ttu-id="4c86d-1807">Это событие представляет собой процесс сброса для изменения порта концентратора класса узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1807">This event represents a USBX Host Class Hub Port Change Reset Process Event.</span></span>

<span data-ttu-id="4c86d-1808">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1808">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1809">Поле сведений 1. Концентратор.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1809">Info Field 1: Hub.</span></span> <span data-ttu-id="4c86d-1810">Поле сведений 2. Порт.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1810">Info Field 2: Port.</span></span>
- <span data-ttu-id="4c86d-1811">Поле сведений 3. Состояние порта.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1811">Info Field 3: Port status.</span></span>
- <span data-ttu-id="4c86d-1812">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1812">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-suspend-process"></a><span data-ttu-id="4c86d-1813">Процесс приостановки для изменения порта концентратора класса узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1813">Host Class Hub Port Change Suspend Process</span></span> 

#### <a name="ux_host_class_hub_port_change_suspend_process"></a><span data-ttu-id="4c86d-1814">ux_host_class_hub_port_change_suspend_process</span><span class="sxs-lookup"><span data-stu-id="4c86d-1814">ux_host_class_hub_port_change_suspend_process</span></span>

<span data-ttu-id="4c86d-1815">**Значок** ![Значок процесса приостановки для изменения порта концентратора класса узла](./media/user-guide/usbx-events/image128.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1815">**Icon** ![Host Class Hub Port Change Suspend Process icon](./media/user-guide/usbx-events/image128.png)</span></span>

<span data-ttu-id="4c86d-1816">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1816">**Description**</span></span>

<span data-ttu-id="4c86d-1817">Это событие представляет собой процесс приостановки для изменения порта концентратора класса узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1817">This event represents a USBX Host Class Hub Port Change Suspend Process Event.</span></span>

<span data-ttu-id="4c86d-1818">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1818">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1819">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1819">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1820">Поле сведений 2. Порт.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1820">Info Field 2: Port.</span></span>
- <span data-ttu-id="4c86d-1821">Поле сведений 3. Состояние порта.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1821">Info Field 3: Port status.</span></span>
- <span data-ttu-id="4c86d-1822">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1822">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-activate"></a><span data-ttu-id="4c86d-1823">Активация класса Pima узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1823">Host Class Pima Activate</span></span> 

#### <a name="ux_host_class_pima_activate"></a><span data-ttu-id="4c86d-1824">ux_host_class_pima_activate</span><span class="sxs-lookup"><span data-stu-id="4c86d-1824">ux_host_class_pima_activate</span></span>

<span data-ttu-id="4c86d-1825">**Значок** ![Значок активации класса Pima узла](./media/user-guide/usbx-events/image129.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1825">**Icon** ![Host Class Pima Activate icon](./media/user-guide/usbx-events/image129.png)</span></span>

<span data-ttu-id="4c86d-1826">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1826">**Description**</span></span>

<span data-ttu-id="4c86d-1827">Это событие представляет собой активацию класса Pima узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1827">This event represents a USBX Host Class Pima Activate Event.</span></span>

<span data-ttu-id="4c86d-1828">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1828">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1829">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1829">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1830">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1830">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1831">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1831">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1832">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1832">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-deactivate"></a><span data-ttu-id="4c86d-1833">Деактивация класса Pima узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1833">Host Class Pima Deactivate</span></span> 

#### <a name="ux_host_class_pima_deactivate"></a><span data-ttu-id="4c86d-1834">ux_host_class_pima_deactivate</span><span class="sxs-lookup"><span data-stu-id="4c86d-1834">ux_host_class_pima_deactivate</span></span>

<span data-ttu-id="4c86d-1835">**Значок** ![Значок деактивации класса Pima узла](./media/user-guide/usbx-events/image130.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1835">**Icon** ![Host Class Pima Deactivate icon](./media/user-guide/usbx-events/image130.png)</span></span>

<span data-ttu-id="4c86d-1836">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1836">**Description**</span></span>

<span data-ttu-id="4c86d-1837">Это событие представляет собой деактивацию класса Pima узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1837">This event represents a USBX Host Class Pima Deactivate Event.</span></span>

<span data-ttu-id="4c86d-1838">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1838">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1839">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1839">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1840">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1840">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1841">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1841">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1842">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1842">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-device-info-get"></a><span data-ttu-id="4c86d-1843">Получение сведений об устройстве для класса Pima узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1843">Host Class Pima Device Info Get</span></span> 

#### <a name="ux_host_class_pima_device_info_get"></a><span data-ttu-id="4c86d-1844">ux_host_class_pima_device_info_get</span><span class="sxs-lookup"><span data-stu-id="4c86d-1844">ux_host_class_pima_device_info_get</span></span>

<span data-ttu-id="4c86d-1845">**Значок** ![Значок получения сведений об устройстве для класса Pima узла](./media/user-guide/usbx-events/image131.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1845">**Icon** ![Host Class Pima Device Info Get icon](./media/user-guide/usbx-events/image131.png)</span></span>

<span data-ttu-id="4c86d-1846">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1846">**Description**</span></span>

<span data-ttu-id="4c86d-1847">Это событие представляет собой получение сведений о классе Pima узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1847">This event represents a USBX Host Class Pima Device Info Get Event.</span></span>

<span data-ttu-id="4c86d-1848">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1848">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1849">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1849">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1850">Поле сведений 2. Устройство Pima.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1850">Info Field 2: Pima device.</span></span>
- <span data-ttu-id="4c86d-1851">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1851">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1852">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1852">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-device-reset"></a><span data-ttu-id="4c86d-1853">Сброс устройства для класса Pima узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1853">Host Class Pima Device Reset</span></span> 

#### <a name="ux_host_class_pima_device_reset"></a><span data-ttu-id="4c86d-1854">ux_host_class_pima_device_reset</span><span class="sxs-lookup"><span data-stu-id="4c86d-1854">ux_host_class_pima_device_reset</span></span>

<span data-ttu-id="4c86d-1855">**Значок** ![Значок сброса устройства для класса Pima узла](./media/user-guide/usbx-events/image132.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1855">**Icon** ![Host Class Pima Device Reset icon](./media/user-guide/usbx-events/image132.png)</span></span>

<span data-ttu-id="4c86d-1856">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1856">**Description**</span></span>

<span data-ttu-id="4c86d-1857">Это событие представляет собой сброс устройства класса Pima узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1857">This event represents a USBX Host Class Pima Device Reset Event.</span></span>

<span data-ttu-id="4c86d-1858">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1858">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1859">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1859">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1860">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1860">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1861">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1861">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1862">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1862">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-notification"></a><span data-ttu-id="4c86d-1863">Уведомление класса Pima узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1863">Host Class Pima Notification</span></span> 

#### <a name="ux_host_class_pima_notification"></a><span data-ttu-id="4c86d-1864">ux_host_class_pima_notification</span><span class="sxs-lookup"><span data-stu-id="4c86d-1864">ux_host_class_pima_notification</span></span>

<span data-ttu-id="4c86d-1865">**Значок** ![Значок уведомления класса Pima узла](./media/user-guide/usbx-events/image133.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1865">**Icon** ![Host Class Pima Notification icon](./media/user-guide/usbx-events/image133.png)</span></span>

<span data-ttu-id="4c86d-1866">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1866">**Description**</span></span>

<span data-ttu-id="4c86d-1867">Это событие представляет собой уведомление класса Pima узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1867">This event represents a USBX Host Class Pima Notification Event.</span></span>

<span data-ttu-id="4c86d-1868">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1868">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1869">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1869">Info Field 1: Class instance.</span></span> <span data-ttu-id="4c86d-1870">Поле сведений 2. Код события.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1870">Info Field 2: Event code.</span></span>
- <span data-ttu-id="4c86d-1871">Поле сведений 3. Идентификатор транзакции.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1871">Info Field 3: Transaction ID.</span></span>
- <span data-ttu-id="4c86d-1872">Поле сведений 4. Параметр 1.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1872">Info Field 4: Parameter1.</span></span>

### <a name="host-class-pima-number-objects-get"></a><span data-ttu-id="4c86d-1873">Получение объектов номера класса Pima узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1873">Host Class Pima Number Objects Get</span></span> 

#### <a name="ux_host_class_pima_number_objects_get"></a><span data-ttu-id="4c86d-1874">ux_host_class_pima_number_objects_get</span><span class="sxs-lookup"><span data-stu-id="4c86d-1874">ux_host_class_pima_number_objects_get</span></span>

<span data-ttu-id="4c86d-1875">**Значок** ![Значок получения объектов номера класса Pima узла](./media/user-guide/usbx-events/image134.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1875">**Icon** ![Host Class Pima Number Objects Get icon](./media/user-guide/usbx-events/image134.png)</span></span>

<span data-ttu-id="4c86d-1876">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1876">**Description**</span></span>

<span data-ttu-id="4c86d-1877">Это событие представляет собой получение объектов номера класса Pima узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1877">This event represents a USBX Host Class Pima Number Objects Get Event.</span></span>

<span data-ttu-id="4c86d-1878">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1878">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1879">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1879">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1880">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1880">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1881">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1881">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1882">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1882">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-close"></a><span data-ttu-id="4c86d-1883">Закрытие объекта класса Pima узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1883">Host Class Pima Object Close</span></span> 

#### <a name="ux_host_class_pima_object_close"></a><span data-ttu-id="4c86d-1884">ux_host_class_pima_object_close</span><span class="sxs-lookup"><span data-stu-id="4c86d-1884">ux_host_class_pima_object_close</span></span>

<span data-ttu-id="4c86d-1885">**Значок** ![Значок закрытия объекта класса Pima узла](./media/user-guide/usbx-events/image135.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1885">**Icon** ![Host Class Pima Object Close icon](./media/user-guide/usbx-events/image135.png)</span></span>

<span data-ttu-id="4c86d-1886">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1886">**Description**</span></span>

<span data-ttu-id="4c86d-1887">Это событие представляет собой закрытие объекта класса Pima узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1887">This event represents a USBX Host Class Pima Object Close Event.</span></span>

<span data-ttu-id="4c86d-1888">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1888">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1889">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1889">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1890">Поле сведений 2. Объект.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1890">Info Field 2: Object.</span></span>
- <span data-ttu-id="4c86d-1891">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1891">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1892">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1892">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-copy"></a><span data-ttu-id="4c86d-1893">Копирование объекта класса Pima узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1893">Host Class Pima Object Copy</span></span> 

#### <a name="ux_host_class_pima_object_copy"></a><span data-ttu-id="4c86d-1894">ux_host_class_pima_object_copy</span><span class="sxs-lookup"><span data-stu-id="4c86d-1894">ux_host_class_pima_object_copy</span></span>

<span data-ttu-id="4c86d-1895">**Значок** ![Значок копирования объекта класса Pima узла](./media/user-guide/usbx-events/image136.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1895">**Icon** ![Host Class Pima Object Copy icon](./media/user-guide/usbx-events/image136.png)</span></span>

<span data-ttu-id="4c86d-1896">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1896">**Description**</span></span>

<span data-ttu-id="4c86d-1897">Это событие представляет собой копирование объекта класса Pima узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1897">This event represents a USBX Host Class Pima Object Copy Event.</span></span>

<span data-ttu-id="4c86d-1898">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1898">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1899">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1899">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1900">Поле сведений 2. Дескриптор объекта.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1900">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4c86d-1901">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1901">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1902">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1902">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-delete"></a><span data-ttu-id="4c86d-1903">Удаление объекта из класса Pima узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1903">Host Class Pima Object Delete</span></span> 

#### <a name="ux_host_class_pima_object_delete"></a><span data-ttu-id="4c86d-1904">ux_host_class_pima_object_delete</span><span class="sxs-lookup"><span data-stu-id="4c86d-1904">ux_host_class_pima_object_delete</span></span>

<span data-ttu-id="4c86d-1905">**Значок** ![Значок удаления объекта из класса Pima узла](./media/user-guide/usbx-events/image137.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1905">**Icon** ![Host Class Pima Object Delete icon](./media/user-guide/usbx-events/image137.png)</span></span>

<span data-ttu-id="4c86d-1906">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1906">**Description**</span></span>

<span data-ttu-id="4c86d-1907">Это событие представляет собой удаление объекта из класса Pima узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1907">This event represents a USBX Host Class Pima Object Delete Event.</span></span>

<span data-ttu-id="4c86d-1908">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1908">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1909">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1909">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1910">Поле сведений 2. Дескриптор объекта.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1910">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4c86d-1911">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1911">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1912">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1912">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-get"></a><span data-ttu-id="4c86d-1913">Получение объекта класса Pima узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1913">Host Class Pima Object Get</span></span> 

#### <a name="ux_host_class_pima_object_get"></a><span data-ttu-id="4c86d-1914">ux_host_class_pima_object_get</span><span class="sxs-lookup"><span data-stu-id="4c86d-1914">ux_host_class_pima_object_get</span></span>

<span data-ttu-id="4c86d-1915">**Значок** ![Значок получения объекта класса Pima узла](./media/user-guide/usbx-events/image138.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1915">**Icon** ![Host Class Pima Object Get icon](./media/user-guide/usbx-events/image138.png)</span></span>

<span data-ttu-id="4c86d-1916">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1916">**Description**</span></span>

<span data-ttu-id="4c86d-1917">Это событие представляет собой получение сведений о RARP с помощью nx_rarp_info_get.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1917">This event represents getting RARP information via nx_rarp_info_get.</span></span>

<span data-ttu-id="4c86d-1918">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1918">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1919">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1919">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1920">Поле сведений 2. Дескриптор объекта.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1920">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4c86d-1921">Поле сведений 3. Объект.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1921">Info Field 3: Object.</span></span>
- <span data-ttu-id="4c86d-1922">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1922">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-info-get"></a><span data-ttu-id="4c86d-1923">Получение сведений об объекте класса Pima узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1923">Host Class Pima Object Info Get</span></span> 

#### <a name="ux_host_class_pima_object_info_get"></a><span data-ttu-id="4c86d-1924">ux_host_class_pima_object_info_get</span><span class="sxs-lookup"><span data-stu-id="4c86d-1924">ux_host_class_pima_object_info_get</span></span>

<span data-ttu-id="4c86d-1925">**Значок** ![Значок получения сведений об объекте класса Pima узла](./media/user-guide/usbx-events/image139.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1925">**Icon** ![Host Class Pima Object Info Get icon](./media/user-guide/usbx-events/image139.png)</span></span>

<span data-ttu-id="4c86d-1926">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1926">**Description**</span></span>

<span data-ttu-id="4c86d-1927">Это событие представляет собой получение сведений об объекте класса Pima узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1927">This event represents a USBX Host Class Pima Object Info Get Event.</span></span>

<span data-ttu-id="4c86d-1928">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1928">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1929">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1929">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1930">Поле сведений 2. Дескриптор объекта.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1930">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4c86d-1931">Поле сведений 3. Объект.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1931">Info Field 3: Object.</span></span>
- <span data-ttu-id="4c86d-1932">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1932">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-info-send"></a><span data-ttu-id="4c86d-1933">Отправка сведений об объекте класса Pima узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1933">Host Class Pima Object Info Send</span></span> 

#### <a name="ux_host_class_pima_object_info_send"></a><span data-ttu-id="4c86d-1934">ux_host_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="4c86d-1934">ux_host_class_pima_object_info_send</span></span>

<span data-ttu-id="4c86d-1935">**Значок** ![Значок отправки сведений об объекте класса Pima узла](./media/user-guide/usbx-events/image140.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1935">**Icon** ![Host Class Pima Object Info Send icon](./media/user-guide/usbx-events/image140.png)</span></span>

<span data-ttu-id="4c86d-1936">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1936">**Description**</span></span>

<span data-ttu-id="4c86d-1937">Это событие представляет собой отправку сведений об объекте класса Pima узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1937">This event represents a USBX Host Class Pima Object Info Send Event.</span></span>

<span data-ttu-id="4c86d-1938">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1938">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1939">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1939">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1940">Поле сведений 2. Объект.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1940">Info Field 2: Object.</span></span>
- <span data-ttu-id="4c86d-1941">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1941">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1942">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1942">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-move"></a><span data-ttu-id="4c86d-1943">Перемещение объекта класса Pima узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1943">Host Class Pima Object Move</span></span> 

#### <a name="ux_host_class_pima_object_move"></a><span data-ttu-id="4c86d-1944">ux_host_class_pima_object_move</span><span class="sxs-lookup"><span data-stu-id="4c86d-1944">ux_host_class_pima_object_move</span></span>

<span data-ttu-id="4c86d-1945">**Значок** ![Значок перемещения объекта класса Pima узла](./media/user-guide/usbx-events/image141.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1945">**Icon** ![Host Class Pima Object Move icon](./media/user-guide/usbx-events/image141.png)</span></span>

<span data-ttu-id="4c86d-1946">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1946">**Description**</span></span>

<span data-ttu-id="4c86d-1947">Это событие представляет собой перемещение объекта класса Pima узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1947">This event reprThis event represents a USBX Host Class Pima Object Move Event.</span></span>

<span data-ttu-id="4c86d-1948">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1948">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1949">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1949">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1950">Поле сведений 2. Дескриптор объекта.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1950">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4c86d-1951">Поле сведений 3. Объект.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1951">Info Field 3: Object.</span></span>
- <span data-ttu-id="4c86d-1952">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1952">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-send"></a><span data-ttu-id="4c86d-1953">Отправка объекта класса Pima узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1953">Host Class Pima Object Send</span></span> 

#### <a name="ux_host_class_pima_object_move"></a><span data-ttu-id="4c86d-1954">ux_host_class_pima_object_move</span><span class="sxs-lookup"><span data-stu-id="4c86d-1954">ux_host_class_pima_object_move</span></span>

<span data-ttu-id="4c86d-1955">**Значок** ![Значок отправки объекта класса Pima узла](./media/user-guide/usbx-events/image142.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1955">**Icon** ![Host Class Pima Object Send icon](./media/user-guide/usbx-events/image142.png)</span></span>

<span data-ttu-id="4c86d-1956">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1956">**Description**</span></span>

<span data-ttu-id="4c86d-1957">Это событие представляет собой отправку объекта класса Pima узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1957">This event represents a USBX Host Class Pima Object Send Event.</span></span>

<span data-ttu-id="4c86d-1958">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1958">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1959">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1959">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1960">Поле сведений 2. Объект.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1960">Info Field 2: Object.</span></span>
- <span data-ttu-id="4c86d-1961">Поле сведений 3. Буфер объекта.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1961">Info Field 3: Object buffer.</span></span>
- <span data-ttu-id="4c86d-1962">Поле сведений 4. Длина объекта.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1962">Info Field 4: Object length.</span></span>

### <a name="host-class-pima-object-transfer-abort"></a><span data-ttu-id="4c86d-1963">Прерывание перемещения объекта класса Pima узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1963">Host Class Pima Object Transfer Abort</span></span> 

#### <a name="ux_host_class_pima_object_transfer_abort"></a><span data-ttu-id="4c86d-1964">ux_host_class_pima_object_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="4c86d-1964">ux_host_class_pima_object_transfer_abort</span></span>

<span data-ttu-id="4c86d-1965">**Значок** ![Значок прерывания перемещения объекта класса Pima узла](./media/user-guide/usbx-events/image143.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1965">**Icon** ![Host Class Pima Object Transfer Abort icon](./media/user-guide/usbx-events/image143.png)</span></span>

<span data-ttu-id="4c86d-1966">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1966">**Description**</span></span>

<span data-ttu-id="4c86d-1967">Это событие представляет собой прерывание перемещения объекта класса Pima узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1967">This event represents a USBX Host Class Pima Object Transfer Abort Event.</span></span>

<span data-ttu-id="4c86d-1968">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1968">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1969">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1969">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1970">Поле сведений 2. Дескриптор объекта.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1970">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4c86d-1971">Поле сведений 3. Объект.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1971">Info Field 3: Object.</span></span>
- <span data-ttu-id="4c86d-1972">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1972">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-read"></a><span data-ttu-id="4c86d-1973">Считывание класса Pima узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1973">Host Class Pima Read</span></span> 

#### <a name="ux_host_class_pima_read"></a><span data-ttu-id="4c86d-1974">ux_host_class_pima_read</span><span class="sxs-lookup"><span data-stu-id="4c86d-1974">ux_host_class_pima_read</span></span>

<span data-ttu-id="4c86d-1975">**Значок** ![Значок считывания класса Pima узла](./media/user-guide/usbx-events/image144.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1975">**Icon** ![Host Class Pima Read icon](./media/user-guide/usbx-events/image144.png)</span></span>

<span data-ttu-id="4c86d-1976">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1976">**Description**</span></span>

<span data-ttu-id="4c86d-1977">Это событие представляет собой считывание класса Pima узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1977">This event represents a USBX Host Class Pima Read Event.</span></span>

<span data-ttu-id="4c86d-1978">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1978">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1979">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1979">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1980">Поле сведений 2. Указатель данных.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1980">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4c86d-1981">Поле сведений 3. Длина данных.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1981">Info Field 3: Data length.</span></span>
- <span data-ttu-id="4c86d-1982">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1982">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-request-cancel"></a><span data-ttu-id="4c86d-1983">Отмена запроса класса Pima узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1983">Host Class Pima Request Cancel</span></span> 

#### <a name="ux_host_class_pima_request_cancel"></a><span data-ttu-id="4c86d-1984">ux_host_class_pima_request_cancel</span><span class="sxs-lookup"><span data-stu-id="4c86d-1984">ux_host_class_pima_request_cancel</span></span>

<span data-ttu-id="4c86d-1985">**Значок** ![Значок отмены запроса класса Pima узла](./media/user-guide/usbx-events/image145.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1985">**Icon** ![Host Class Pima Request Cancel icon](./media/user-guide/usbx-events/image145.png)</span></span>

<span data-ttu-id="4c86d-1986">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1986">**Description**</span></span>

<span data-ttu-id="4c86d-1987">Это событие представляет собой отмену запроса класса Pima узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1987">This event represents a USBX Host Class Pima Request Cancel Event.</span></span>

<span data-ttu-id="4c86d-1988">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1988">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1989">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1989">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-1990">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1990">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-1991">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1991">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-1992">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1992">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-session-close"></a><span data-ttu-id="4c86d-1993">Закрытие сеанса класса Pima узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-1993">Host Class Pima Session Close</span></span> 

#### <a name="ux_host_class_pima_session_close"></a><span data-ttu-id="4c86d-1994">ux_host_class_pima_session_close</span><span class="sxs-lookup"><span data-stu-id="4c86d-1994">ux_host_class_pima_session_close</span></span>

<span data-ttu-id="4c86d-1995">**Значок** ![Значок закрытия сеанса класса Pima узла](./media/user-guide/usbx-events/image146.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-1995">**Icon** ![Host Class Pima Session Close icon](./media/user-guide/usbx-events/image146.png)</span></span>

<span data-ttu-id="4c86d-1996">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1996">**Description**</span></span>

<span data-ttu-id="4c86d-1997">Это событие представляет собой закрытие сеанса класса Pima узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1997">This event represents a USBX Host Class Pima Session Close Event.</span></span>

<span data-ttu-id="4c86d-1998">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-1998">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-1999">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-1999">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2000">Поле сведений 2. Сеанс Pima.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2000">Info Field 2: Pima session.</span></span>
- <span data-ttu-id="4c86d-2001">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2001">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2002">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2002">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-session-open"></a><span data-ttu-id="4c86d-2003">Открытие сеанса класса Pima узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2003">Host Class Pima Session Open</span></span> 

#### <a name="ux_host_class_pima_session_open"></a><span data-ttu-id="4c86d-2004">ux_host_class_pima_session_open</span><span class="sxs-lookup"><span data-stu-id="4c86d-2004">ux_host_class_pima_session_open</span></span>

<span data-ttu-id="4c86d-2005">**Значок** ![Значок открытия сеанса класса Pima узла](./media/user-guide/usbx-events/image147.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2005">**Icon** ![Host Class Pima Session Open icon](./media/user-guide/usbx-events/image147.png)</span></span>

<span data-ttu-id="4c86d-2006">**Описание** Это событие представляет собой открытие сеанса класса Pima узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2006">**Description** This event represents a USBX Host Class Pima Session Open Event.</span></span>

<span data-ttu-id="4c86d-2007">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2007">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2008">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2008">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2009">Поле сведений 2. Сеанс Pima.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2009">Info Field 2: Pima session.</span></span>
- <span data-ttu-id="4c86d-2010">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2010">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2011">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2011">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-storage-ids-get"></a><span data-ttu-id="4c86d-2012">Получение идентификаторов хранилища класса Pima узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2012">Host Class Pima Storage Ids Get</span></span> 

#### <a name="ux_host_class_pima_session_ids_get"></a><span data-ttu-id="4c86d-2013">ux_host_class_pima_session_ids_get</span><span class="sxs-lookup"><span data-stu-id="4c86d-2013">ux_host_class_pima_session_ids_get</span></span>

<span data-ttu-id="4c86d-2014">**Значок** ![Значок получения идентификаторов хранилища класса Pima узла](./media/user-guide/usbx-events/image148.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2014">**Icon** ![Host Class Pima Storage Ids Get icon](./media/user-guide/usbx-events/image148.png)</span></span>

<span data-ttu-id="4c86d-2015">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2015">**Description**</span></span>

<span data-ttu-id="4c86d-2016">Это событие представляет собой получение идентификаторов хранилища класса Pima узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2016">This event represents a USBX Host Class Pima Storage Ids Get Event.</span></span>

<span data-ttu-id="4c86d-2017">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2017">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2018">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2018">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2019">Поле сведений 2. Массив идентификаторов хранилища.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2019">nfo Field 2: Storage ID array.</span></span>
- <span data-ttu-id="4c86d-2020">Поле сведений 3. Длина идентификатора хранилища.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2020">Info Field 3: Storage ID length.</span></span>
<span data-ttu-id="4c86d-2021">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2021">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-storage-info-get"></a><span data-ttu-id="4c86d-2022">Получение сведений о хранилище класса Pima узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2022">Host Class Pima Storage Info Get</span></span> 

#### <a name="ux_host_class_pima_storage_info_get"></a><span data-ttu-id="4c86d-2023">ux_host_class_pima_storage_info_get</span><span class="sxs-lookup"><span data-stu-id="4c86d-2023">ux_host_class_pima_storage_info_get</span></span>

<span data-ttu-id="4c86d-2024">**Значок** ![Значок получения сведений о хранилище класса Pima узла](./media/user-guide/usbx-events/image149.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2024">**Icon** ![Host Class Pima Storage Info Get icon](./media/user-guide/usbx-events/image149.png)</span></span>

<span data-ttu-id="4c86d-2025">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2025">**Description**</span></span>

<span data-ttu-id="4c86d-2026">Это событие представляет собой получение сведений о хранилище класса Pima узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2026">This event represents a USBX Host Class Pima Storage Info Get Event.</span></span>

<span data-ttu-id="4c86d-2027">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2027">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2028">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2028">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2029">Поле сведений 2. Идентификатор хранилища.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2029">Info Field 2: Storage ID.</span></span>
- <span data-ttu-id="4c86d-2030">Поле сведений 3. Хранилище.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2030">Info Field 3: Storage.</span></span>
- <span data-ttu-id="4c86d-2031">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2031">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-thumb-get"></a><span data-ttu-id="4c86d-2032">Получение бегунка класса Pima узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2032">Host Class Pima Thumb Get</span></span> 

#### <a name="ux_host_class_pima_thumb_get"></a><span data-ttu-id="4c86d-2033">ux_host_class_pima_thumb_get</span><span class="sxs-lookup"><span data-stu-id="4c86d-2033">ux_host_class_pima_thumb_get</span></span>

<span data-ttu-id="4c86d-2034">**Значок** ![Значок получения бегунка класса Pima узла](./media/user-guide/usbx-events/image150.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2034">**Icon** ![Host Class Pima Thumb Get icon](./media/user-guide/usbx-events/image150.png)</span></span>

<span data-ttu-id="4c86d-2035">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2035">**Description**</span></span>

<span data-ttu-id="4c86d-2036">Это событие представляет собой невозможность подключения к серверу TCP через nx_tcp_server_socket_unaccept.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2036">This event represents unaccepting a TCP server connection via nx_tcp_server_socket_unaccept.</span></span>

<span data-ttu-id="4c86d-2037">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2037">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-2038">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2038">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2039">Поле сведений 2. Дескриптор объекта.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2039">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4c86d-2040">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2040">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2041">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2041">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-write"></a><span data-ttu-id="4c86d-2042">Запись класса Pima узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2042">Host Class Pima Write</span></span> 

#### <a name="ux_host_class_pima_thumb_get"></a><span data-ttu-id="4c86d-2043">ux_host_class_pima_thumb_get</span><span class="sxs-lookup"><span data-stu-id="4c86d-2043">ux_host_class_pima_thumb_get</span></span>

<span data-ttu-id="4c86d-2044">**Значок** ![Значок записи класса Pima узла](./media/user-guide/usbx-events/image151.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2044">**Icon** ![Host Class Pima Write icon](./media/user-guide/usbx-events/image151.png)</span></span>

<span data-ttu-id="4c86d-2045">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2045">**Description**</span></span>

<span data-ttu-id="4c86d-2046">Это событие представляет собой запись класса Pima узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2046">This event represents a USBX Host Class Pima Write.</span></span>

<span data-ttu-id="4c86d-2047">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2047">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2048">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2048">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4c86d-2049">Поле сведений 2. Указатель данных.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2049">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4c86d-2050">Поле сведений 3. Длина данных.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2050">Info Field 3: Data length.</span></span>
- <span data-ttu-id="4c86d-2051">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2051">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-activate"></a><span data-ttu-id="4c86d-2052">Активация принтера класса узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2052">Host Class Printer Activate</span></span> 

#### <a name="ux_host_class_printer_activate"></a><span data-ttu-id="4c86d-2053">ux_host_class_printer_activate</span><span class="sxs-lookup"><span data-stu-id="4c86d-2053">ux_host_class_printer_activate</span></span>

<span data-ttu-id="4c86d-2054">**Значок** ![Значок активации принтера класса узла](./media/user-guide/usbx-events/image152.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2054">**Icon** ![Host Class Printer Activate icon](./media/user-guide/usbx-events/image152.png)</span></span>

<span data-ttu-id="4c86d-2055">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2055">**Description**</span></span>

<span data-ttu-id="4c86d-2056">Это событие представляет собой активацию принтера класса узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2056">This event represents a USBX Host Class Printer Activate Event.</span></span>

<span data-ttu-id="4c86d-2057">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2057">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2058">Поле сведений 1. Указатель на экземпляр IP.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2058">Info Field 1: Pointer to IP instance.</span></span>
- <span data-ttu-id="4c86d-2059">Поле сведений 2. Указатель на сокет.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2059">Info Field 2: Pointer to socket.</span></span>
- <span data-ttu-id="4c86d-2060">Поле сведений 3. Тип службы.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2060">Info Field 3: Type of service.</span></span>
- <span data-ttu-id="4c86d-2061">Поле сведений 4. Размер окна приема.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2061">Info Field 4: Receive window size.</span></span>

### <a name="host-class-printer-deactivate"></a><span data-ttu-id="4c86d-2062">Деактивация принтера класса узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2062">Host Class Printer Deactivate</span></span> 

#### <a name="ux_host_class_printer_deactivate"></a><span data-ttu-id="4c86d-2063">ux_host_class_printer_deactivate</span><span class="sxs-lookup"><span data-stu-id="4c86d-2063">ux_host_class_printer_deactivate</span></span>

<span data-ttu-id="4c86d-2064">**Значок** ![Значок деактивации принтера класса узла](./media/user-guide/usbx-events/image153.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2064">**Icon** ![Host Class Printer Deactivate icon](./media/user-guide/usbx-events/image153.png)</span></span>

<span data-ttu-id="4c86d-2065">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2065">**Description**</span></span>

<span data-ttu-id="4c86d-2066">Это событие представляет собой деактивацию принтера класса узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2066">This event represents a USBX Host Class Printer Deactivate Event.</span></span>

<span data-ttu-id="4c86d-2067">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2067">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2068">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2068">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2069">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2069">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-2070">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2070">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2071">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2071">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-name-get"></a><span data-ttu-id="4c86d-2072">Получение названия принтера класса узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2072">Host Class Printer Name Get</span></span> 

#### <a name="ux_host_class_printer_name_get"></a><span data-ttu-id="4c86d-2073">ux_host_class_printer_name_get</span><span class="sxs-lookup"><span data-stu-id="4c86d-2073">ux_host_class_printer_name_get</span></span>

<span data-ttu-id="4c86d-2074">**Значок** ![Значок получения названия принтера класса узла](./media/user-guide/usbx-events/image154.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2074">**Icon** ![Host Class Printer Name Get icon](./media/user-guide/usbx-events/image154.png)</span></span>

<span data-ttu-id="4c86d-2075">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2075">**Description**</span></span>

<span data-ttu-id="4c86d-2076">Это событие представляет собой получение названия принтера класса узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2076">This event represents a USBX Host Class Printer Name Get Event.</span></span>

<span data-ttu-id="4c86d-2077">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2077">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-2078">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2078">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2079">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2079">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-2080">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2080">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2081">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2081">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-read"></a><span data-ttu-id="4c86d-2082">Считывание принтера класса узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2082">Host Class Printer Read</span></span> 

#### <a name="ux_host_class_printer_read"></a><span data-ttu-id="4c86d-2083">ux_host_class_printer_read</span><span class="sxs-lookup"><span data-stu-id="4c86d-2083">ux_host_class_printer_read</span></span>

<span data-ttu-id="4c86d-2084">**Значок** ![Значок считывания принтера класса узла](./media/user-guide/usbx-events/image155.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2084">**Icon** ![Host Class Printer Read icon](./media/user-guide/usbx-events/image155.png)</span></span>

<span data-ttu-id="4c86d-2085">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2085">**Description**</span></span>

<span data-ttu-id="4c86d-2086">Это событие представляет собой считывание принтера класса узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2086">This event represents a USBX Host Class Printer Read Event.</span></span>

<span data-ttu-id="4c86d-2087">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2087">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2088">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2088">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2089">Поле сведений 2. Указатель данных.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2089">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4c86d-2090">Поле сведений 3. Запрошенная длина.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2090">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4c86d-2091">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2091">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-soft-reset"></a><span data-ttu-id="4c86d-2092">Частичный сброс принтера класса узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2092">Host Class Printer Soft Reset</span></span> 

#### <a name="ux_host_class_printer_soft_reset"></a><span data-ttu-id="4c86d-2093">ux_host_class_printer_soft_reset</span><span class="sxs-lookup"><span data-stu-id="4c86d-2093">ux_host_class_printer_soft_reset</span></span>

<span data-ttu-id="4c86d-2094">**Значок** ![Значок частичного сброса принтера класса узла](./media/user-guide/usbx-events/image156.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2094">**Icon** ![Host Class Printer Soft Reset icon](./media/user-guide/usbx-events/image156.png)</span></span>

<span data-ttu-id="4c86d-2095">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2095">**Description**</span></span>

<span data-ttu-id="4c86d-2096">Это событие представляет собой частичный сброс принтера класса узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2096">This event represents a USBX Host Class Printer Soft Reset Event.</span></span>

<span data-ttu-id="4c86d-2097">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2097">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2098">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2098">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2099">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2099">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-2100">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2100">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2101">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2101">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-status-get"></a><span data-ttu-id="4c86d-2102">Получение состояния принтера класса узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2102">Host Class Printer Status Get</span></span> 

#### <a name="ux_host_class_printer_status_get"></a><span data-ttu-id="4c86d-2103">ux_host_class_printer_status_get</span><span class="sxs-lookup"><span data-stu-id="4c86d-2103">ux_host_class_printer_status_get</span></span>

<span data-ttu-id="4c86d-2104">**Значок** ![Значок получения состояния принтера класса узла](./media/user-guide/usbx-events/image157.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2104">**Icon** ![Host Class Printer Status Get icon](./media/user-guide/usbx-events/image157.png)</span></span>

<span data-ttu-id="4c86d-2105">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2105">**Description**</span></span>

<span data-ttu-id="4c86d-2106">Это событие представляет собой получение состояния принтера класса узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2106">This event represents a USBX Host Class Printer Status Get Event.</span></span>

<span data-ttu-id="4c86d-2107">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2107">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2108">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2108">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2109">Поле сведений 2. Состояние принтера.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2109">Info Field 2: Printer status.</span></span>
- <span data-ttu-id="4c86d-2110">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2110">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2111">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2111">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-write"></a><span data-ttu-id="4c86d-2112">Запись принтера класса узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2112">Host Class Printer Write</span></span> 

#### <a name="ux_host_class_printer_write"></a><span data-ttu-id="4c86d-2113">ux_host_class_printer_write</span><span class="sxs-lookup"><span data-stu-id="4c86d-2113">ux_host_class_printer_write</span></span>

<span data-ttu-id="4c86d-2114">**Значок** ![Значок записи принтера класса узла](./media/user-guide/usbx-events/image158.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2114">**Icon** ![Host Class Printer Write icon](./media/user-guide/usbx-events/image158.png)</span></span>

<span data-ttu-id="4c86d-2115">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2115">**Description**</span></span>

<span data-ttu-id="4c86d-2116">Это событие представляет собой запись принтера класса узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2116">This event represents a USBX Host Class Printer Write.</span></span>

<span data-ttu-id="4c86d-2117">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2117">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-2118">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2118">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2119">Поле сведений 2. Указатель данных.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2119">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4c86d-2120">Поле сведений 3. Запрошенная длина.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2120">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4c86d-2121">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2121">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-activate"></a><span data-ttu-id="4c86d-2122">Активация класса Prolific узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2122">Host Class Prolific Activate</span></span> 

#### <a name="ux_host_class_prolific_activate"></a><span data-ttu-id="4c86d-2123">ux_host_class_prolific_activate</span><span class="sxs-lookup"><span data-stu-id="4c86d-2123">ux_host_class_prolific_activate</span></span> 

<span data-ttu-id="4c86d-2124">**Значок** ![Значок активации класса Prolific узла](./media/user-guide/usbx-events/image159.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2124">**Icon** ![Host Class Prolific Activate icon](./media/user-guide/usbx-events/image159.png)</span></span>

<span data-ttu-id="4c86d-2125">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2125">**Description**</span></span>

<span data-ttu-id="4c86d-2126">Это событие представляет собой активацию класса Prolific узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2126">This event represents a USBX Host Class Prolific Activate Event.</span></span>

<span data-ttu-id="4c86d-2127">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2127">**Information Fields**</span></span> 

- <span data-ttu-id="4c86d-2128">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2128">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2129">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2129">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-2130">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2130">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2131">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2131">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-deactivate"></a><span data-ttu-id="4c86d-2132">Деактивация класса Prolific узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2132">Host Class Prolific Deactivate</span></span> 

#### <a name="ux_host_class_prolific_deactivate"></a><span data-ttu-id="4c86d-2133">ux_host_class_prolific_deactivate</span><span class="sxs-lookup"><span data-stu-id="4c86d-2133">ux_host_class_prolific_deactivate</span></span> 

<span data-ttu-id="4c86d-2134">**Значок** ![Значок деактивации класса Prolific узла](./media/user-guide/usbx-events/image160.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2134">**Icon** ![Host Class Prolific Deactivate icon](./media/user-guide/usbx-events/image160.png)</span></span>

<span data-ttu-id="4c86d-2135">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2135">**Description**</span></span>

<span data-ttu-id="4c86d-2136">Это событие представляет собой деактивацию класса Prolific узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2136">This event represents a USBX Host Class Prolific Deactivate Event.</span></span>

<span data-ttu-id="4c86d-2137">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2137">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2138">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2138">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2139">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2139">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-2140">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2140">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2141">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2141">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-abort-in-pipe"></a><span data-ttu-id="4c86d-2142">Прерывание в канале класса Prolific Ioctl узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2142">Host Class Prolific Ioctl Abort In Pipe</span></span> 

#### <a name="ux_host_class_prolific_ioctl_abort_in_pipe"></a><span data-ttu-id="4c86d-2143">ux_host_class_prolific_ioctl_abort_in_pipe</span><span class="sxs-lookup"><span data-stu-id="4c86d-2143">ux_host_class_prolific_ioctl_abort_in_pipe</span></span>

<span data-ttu-id="4c86d-2144">**Значок** ![Значок прерывания в канале класса Prolific Ioctl узла](./media/user-guide/usbx-events/image161.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2144">**Icon** ![Host Class Prolific I O C T L Abort In Pipe icon](./media/user-guide/usbx-events/image161.png)</span></span>

<span data-ttu-id="4c86d-2145">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2145">**Description**</span></span>

<span data-ttu-id="4c86d-2146">Это событие представляет собой прерывание в канале класса Prolific Ioctl узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2146">This event represents a USBX Host Class Prolific Ioctl Abort In Pipe Event.</span></span>

<span data-ttu-id="4c86d-2147">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2147">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2148">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2148">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2149">Поле сведений 2. Конечная точка.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2149">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="4c86d-2150">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2150">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2151">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2151">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-abort-out-pipe"></a><span data-ttu-id="4c86d-2152">Прерывание вне канала класса Prolific Ioctl узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2152">Host Class Prolific Ioctl Abort Out Pipe</span></span> 

#### <a name="ux_host_class_prolific_ioctl_abort_out_pipe"></a><span data-ttu-id="4c86d-2153">ux_host_class_prolific_ioctl_abort_out_pipe</span><span class="sxs-lookup"><span data-stu-id="4c86d-2153">ux_host_class_prolific_ioctl_abort_out_pipe</span></span>

<span data-ttu-id="4c86d-2154">**Значок** ![Значок прерывания вне канала класса Prolific Ioctl узла](./media/user-guide/usbx-events/image162.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2154">**Icon** ![Host Class Prolific I O C T L Abort Out Pipe icon](./media/user-guide/usbx-events/image162.png)</span></span>

<span data-ttu-id="4c86d-2155">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2155">**Description**</span></span>

<span data-ttu-id="4c86d-2156">Это событие представляет собой прерывание вне канала класса Prolific Ioctl узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2156">This event represents a USBX Host Class Prolific Ioctl Abort Out Pipe Event.</span></span>

<span data-ttu-id="4c86d-2157">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2157">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2158">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2158">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2159">Поле сведений 2. Конечная точка.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2159">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="4c86d-2160">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2160">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2161">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2161">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-get-device-status"></a><span data-ttu-id="4c86d-2162">Получение состояния устройства класса Prolific Ioctl узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2162">Host Class Prolific Ioctl Get Device Status</span></span> 

#### <a name="ux_host_class_prolific_ioctl_get_device_status"></a><span data-ttu-id="4c86d-2163">ux_host_class_prolific_ioctl_get_device_status</span><span class="sxs-lookup"><span data-stu-id="4c86d-2163">ux_host_class_prolific_ioctl_get_device_status</span></span>

<span data-ttu-id="4c86d-2164">**Значок** ![Значок получения состояния устройства класса Prolific Ioctl узла](./media/user-guide/usbx-events/image163.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2164">**Icon** ![Host Class Prolific I O C T L Get Device Status icon](./media/user-guide/usbx-events/image163.png)</span></span>

<span data-ttu-id="4c86d-2165">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2165">**Description**</span></span>

<span data-ttu-id="4c86d-2166">Это событие представляет собой получение состояния устройства класса Prolific Ioctl узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2166">This event represents a USBX Host Class Prolific Ioctl Get Device Status Event.</span></span>

<span data-ttu-id="4c86d-2167">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2167">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2168">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2168">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2169">Поле сведений 2. Состояние устройства.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2169">Info Field 2: Device status.</span></span>
- <span data-ttu-id="4c86d-2170">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2170">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2171">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2171">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-get-line-coding"></a><span data-ttu-id="4c86d-2172">Получение кодировки строки класса Prolific Ioctl узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2172">Host Class Prolific Ioctl Get Line Coding</span></span> 

#### <a name="ux_host_class_prolific_ioctl_get_line_coding"></a><span data-ttu-id="4c86d-2173">ux_host_class_prolific_ioctl_get_line_coding</span><span class="sxs-lookup"><span data-stu-id="4c86d-2173">ux_host_class_prolific_ioctl_get_line_coding</span></span>

<span data-ttu-id="4c86d-2174">**Значок** ![Значок получения кодировки строки класса Prolific Ioctl узла](./media/user-guide/usbx-events/image164.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2174">**Icon** ![Host Class Prolific I O C T L Get Line Coding icon](./media/user-guide/usbx-events/image164.png)</span></span>

<span data-ttu-id="4c86d-2175">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2175">**Description**</span></span>

<span data-ttu-id="4c86d-2176">Это событие представляет собой получение кодировки строки класса Prolific Ioctl узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2176">This event represents a USBX Host Class Prolific Ioctl Get Line Coding Event.</span></span>

<span data-ttu-id="4c86d-2177">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2177">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2178">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2178">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2179">Поле сведений 2. Параметр.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2179">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="4c86d-2180">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2180">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2181">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2181">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-purge"></a><span data-ttu-id="4c86d-2182">Очистка класса Prolific Ioctl узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2182">Host Class Prolific Ioctl Purge</span></span> 

#### <a name="ux_host_class_prolific_ioctl_purge"></a><span data-ttu-id="4c86d-2183">ux_host_class_prolific_ioctl_purge</span><span class="sxs-lookup"><span data-stu-id="4c86d-2183">ux_host_class_prolific_ioctl_purge</span></span>

<span data-ttu-id="4c86d-2184">**Значок** ![Значок очистки класса Prolific Ioctl узла](./media/user-guide/usbx-events/image165.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2184">**Icon** ![Host Class Prolific Ioctl Purge icon](./media/user-guide/usbx-events/image165.png)</span></span>

<span data-ttu-id="4c86d-2185">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2185">**Description**</span></span>

<span data-ttu-id="4c86d-2186">Это событие представляет собой очистку класса Prolific Ioctl узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2186">This event represents a USBX Host Class Prolific Ioctl Purge Event.</span></span>

<span data-ttu-id="4c86d-2187">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2187">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2188">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2188">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2189">Поле сведений 2. Параметр.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2189">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="4c86d-2190">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2190">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2191">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2191">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-report-device"></a><span data-ttu-id="4c86d-2192">Устройство отчетов класса Prolific Ioctl узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2192">Host Class Prolific Ioctl Report Device</span></span> 

#### <a name="ux_host_class_prolific_ioctl_report_device"></a><span data-ttu-id="4c86d-2193">ux_host_class_prolific_ioctl_report_device</span><span class="sxs-lookup"><span data-stu-id="4c86d-2193">ux_host_class_prolific_ioctl_report_device</span></span>

<span data-ttu-id="4c86d-2194">**Значок** ![Значок устройства отчетов класса Prolific Ioctl узла](./media/user-guide/usbx-events/image166.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2194">**Icon** ![Host Class Prolific I O C T L Report Device icon](./media/user-guide/usbx-events/image166.png)</span></span>

<span data-ttu-id="4c86d-2195">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2195">**Description**</span></span>

<span data-ttu-id="4c86d-2196">Это событие представляет собой событие устройства отчетов класса Prolific Ioctl узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2196">This event represents a USBX Host Class Prolific Ioctl Report Device Status Change Event.</span></span>

<span data-ttu-id="4c86d-2197">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2197">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2198">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2198">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2199">Поле сведений 2. Параметр.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2199">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="4c86d-2200">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2200">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2201">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2201">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-send-break"></a><span data-ttu-id="4c86d-2202">Остановка отправки класса Prolific Ioctl узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2202">Host Class Prolific Ioctl Send Break</span></span> 

#### <a name="ux_host_class_prolific_ioctl_send_break"></a><span data-ttu-id="4c86d-2203">ux_host_class_prolific_ioctl_send_break</span><span class="sxs-lookup"><span data-stu-id="4c86d-2203">ux_host_class_prolific_ioctl_send_break</span></span>

<span data-ttu-id="4c86d-2204">**Значок** ![Значок остановки отправки класса Prolific Ioctl узла](./media/user-guide/usbx-events/image167.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2204">**Icon** ![Host Class Prolific I O C T L Send Break icon](./media/user-guide/usbx-events/image167.png)</span></span>

<span data-ttu-id="4c86d-2205">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2205">**Description**</span></span>

<span data-ttu-id="4c86d-2206">Это событие представляет собой остановку отправки класса Prolific Ioctl узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2206">This event represents a USBX Host Class Prolific Ioctl Send Break Event.</span></span>

<span data-ttu-id="4c86d-2207">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2207">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2208">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2208">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2209">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2209">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-2210">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2210">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2211">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2211">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-set-line-coding"></a><span data-ttu-id="4c86d-2212">Задание кодировки строки в классе Prolific Ioctl узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2212">Host Class Prolific Ioctl Set Line Coding</span></span> 

#### <a name="ux_host_class_prolific_ioctl_set_line_coding"></a><span data-ttu-id="4c86d-2213">ux_host_class_prolific_ioctl_set_line_coding</span><span class="sxs-lookup"><span data-stu-id="4c86d-2213">ux_host_class_prolific_ioctl_set_line_coding</span></span>

<span data-ttu-id="4c86d-2214">**Значок** ![Значок задания кодировки строки в классе Prolific Ioctl узла](./media/user-guide/usbx-events/image168.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2214">**Icon** ![Host Class Prolific I O C T L Set Line Coding icon](./media/user-guide/usbx-events/image168.png)</span></span>

<span data-ttu-id="4c86d-2215">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2215">**Description**</span></span>

<span data-ttu-id="4c86d-2216">Это событие представляет собой задание кодировки строки в классе Prolific Ioctl узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2216">This event represents a USBX Host Class Prolific Ioctl Set Line Coding Event.</span></span>

<span data-ttu-id="4c86d-2217">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2217">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2218">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2218">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2219">Поле сведений 2. Параметр.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2219">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="4c86d-2220">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2220">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2221">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2221">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-set-line-state"></a><span data-ttu-id="4c86d-2222">Задание состояния строки в классе Prolific Ioctl узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2222">Host Class Prolific Ioctl Set Line State</span></span> 

#### <a name="ux_host_class_prolific_ioctl_set_line_state"></a><span data-ttu-id="4c86d-2223">ux_host_class_prolific_ioctl_set_line_state</span><span class="sxs-lookup"><span data-stu-id="4c86d-2223">ux_host_class_prolific_ioctl_set_line_state</span></span>

<span data-ttu-id="4c86d-2224">**Значок** ![Значок задания состояния строки в классе Prolific Ioctl узла](./media/user-guide/usbx-events/image169.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2224">**Icon** ![Host Class Prolific I O C T L Set Line State icon](./media/user-guide/usbx-events/image169.png)</span></span>

<span data-ttu-id="4c86d-2225">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2225">**Description**</span></span>

<span data-ttu-id="4c86d-2226">Это событие представляет собой задание состояния строки в классе Prolific Ioctl узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2226">This event represents a USBX Host Class Prolific Ioctl Set Line State Event.</span></span>

<span data-ttu-id="4c86d-2227">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2227">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2228">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2228">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2229">Поле сведений 2. Параметр.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2229">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="4c86d-2230">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2230">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2231">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2231">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-read"></a><span data-ttu-id="4c86d-2232">Считывание класса Prolific узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2232">Host Class Prolific Read</span></span> 

#### <a name="ux_host_class_prolific_read"></a><span data-ttu-id="4c86d-2233">ux_host_class_prolific_read</span><span class="sxs-lookup"><span data-stu-id="4c86d-2233">ux_host_class_prolific_read</span></span>

<span data-ttu-id="4c86d-2234">**Значок** ![Значок считывания класса Prolific узла](./media/user-guide/usbx-events/image170.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2234">**Icon** ![Host Class Prolific Read icon](./media/user-guide/usbx-events/image170.png)</span></span>

<span data-ttu-id="4c86d-2235">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2235">**Description**</span></span>

<span data-ttu-id="4c86d-2236">Это событие представляет собой считывание класса Prolific узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2236">This event represents a USBX Host Class Prolific Read Event.</span></span>

<span data-ttu-id="4c86d-2237">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2237">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2238">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2238">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2239">Поле сведений 2. Указатель данных.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2239">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4c86d-2240">Поле сведений 3. Запрошенная длина.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2240">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4c86d-2241">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2241">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-reception-start"></a><span data-ttu-id="4c86d-2242">Запуск приема в классе Prolific узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2242">Host Class Prolific Reception Start</span></span> 

#### <a name="ux_host_class_prolific_reception_start"></a><span data-ttu-id="4c86d-2243">ux_host_class_prolific_reception_start</span><span class="sxs-lookup"><span data-stu-id="4c86d-2243">ux_host_class_prolific_reception_start</span></span>

<span data-ttu-id="4c86d-2244">**Значок** ![Значок запуска приема в классе Prolific узла](./media/user-guide/usbx-events/image171.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2244">**Icon** ![Host Class Prolific Reception Start icon](./media/user-guide/usbx-events/image171.png)</span></span>

<span data-ttu-id="4c86d-2245">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2245">**Description**</span></span>

<span data-ttu-id="4c86d-2246">Это событие представляет собой запуск приема в классе Prolific узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2246">This event represents a USBX Host Class Prolific Reception Start Event.</span></span>

<span data-ttu-id="4c86d-2247">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2247">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2248">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2248">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2249">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2249">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-2250">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2250">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2251">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2251">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-reception-stop"></a><span data-ttu-id="4c86d-2252">Остановка приема в классе Prolific узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2252">Host Class Prolific Reception Stop</span></span> 

#### <a name="ux_host_class_prolific_reception_stop"></a><span data-ttu-id="4c86d-2253">uux_host_class_prolific_reception_stop</span><span class="sxs-lookup"><span data-stu-id="4c86d-2253">ux_host_class_prolific_reception_stop</span></span>

<span data-ttu-id="4c86d-2254">**Значок** ![Значок остановки приема в классе Prolific узла](./media/user-guide/usbx-events/image172.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2254">**Icon** ![Host Class Prolific Reception Stop icon](./media/user-guide/usbx-events/image172.png)</span></span>

<span data-ttu-id="4c86d-2255">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2255">**Description**</span></span>

<span data-ttu-id="4c86d-2256">Это событие представляет собой остановку приема в классе Prolific узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2256">This event represents a USBX Host Class Prolific Reception Stop Event.</span></span>

<span data-ttu-id="4c86d-2257">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2257">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2258">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2258">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2259">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2259">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-2260">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2260">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2261">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2261">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-write"></a><span data-ttu-id="4c86d-2262">Запись класса Prolific узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2262">Host Class Prolific Write</span></span> 

#### <a name="ux_host_class_prolific_write"></a><span data-ttu-id="4c86d-2263">ux_host_class_prolific_write</span><span class="sxs-lookup"><span data-stu-id="4c86d-2263">ux_host_class_prolific_write</span></span>

<span data-ttu-id="4c86d-2264">**Значок** ![Значок записи класса Prolific узла](./media/user-guide/usbx-events/image173.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2264">**Icon** ![Host Class Prolific Write icon](./media/user-guide/usbx-events/image173.png)</span></span>

<span data-ttu-id="4c86d-2265">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2265">**Description**</span></span>

<span data-ttu-id="4c86d-2266">Это событие представляет собой запись класса Prolific узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2266">This event represents a USBX Host Class Prolific Write Event.</span></span>

<span data-ttu-id="4c86d-2267">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2267">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2268">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2268">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2269">Поле сведений 2. Указатель данных.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2269">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4c86d-2270">Поле сведений 3. Запрошенная длина.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2270">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4c86d-2271">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2271">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-activate"></a><span data-ttu-id="4c86d-2272">Активация хранилища класса узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2272">Host Class Storage Activate</span></span> 

#### <a name="ux_host_class_storage_activate"></a><span data-ttu-id="4c86d-2273">ux_host_class_storage_activate</span><span class="sxs-lookup"><span data-stu-id="4c86d-2273">ux_host_class_storage_activate</span></span>

<span data-ttu-id="4c86d-2274">**Значок** ![Значок активации хранилища класса узла](./media/user-guide/usbx-events/image174.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2274">**Icon** ![Host Class Storage Activate icon](./media/user-guide/usbx-events/image174.png)</span></span>

<span data-ttu-id="4c86d-2275">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2275">**Description**</span></span>

<span data-ttu-id="4c86d-2276">Это событие представляет собой активацию хранилища класса узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2276">This event represents a USBX Host Class Storage Activate Event.</span></span>

<span data-ttu-id="4c86d-2277">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2277">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2278">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2278">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2279">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2279">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-2280">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2280">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2281">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2281">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-deactivate"></a><span data-ttu-id="4c86d-2282">Деактивация хранилища класса узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2282">Host Class Storage Deactivate</span></span> 

#### <a name="ux_host_class_storage_deactivate"></a><span data-ttu-id="4c86d-2283">ux_host_class_storage_deactivate</span><span class="sxs-lookup"><span data-stu-id="4c86d-2283">ux_host_class_storage_deactivate</span></span>

<span data-ttu-id="4c86d-2284">**Значок** ![Значок деактивации хранилища класса узла](./media/user-guide/usbx-events/image175.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2284">**Icon** ![Host Class Storage Deactivate icon](./media/user-guide/usbx-events/image175.png)</span></span>

<span data-ttu-id="4c86d-2285">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2285">**Description**</span></span>

<span data-ttu-id="4c86d-2286">Это событие представляет собой деактивацию хранилища класса узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2286">This event represents a USBX Host Class Storage Deactivate Event.</span></span>

<span data-ttu-id="4c86d-2287">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2287">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2288">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2288">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2289">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2289">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-2290">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2290">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2291">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2291">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-media-capacity-get"></a><span data-ttu-id="4c86d-2292">Получение емкости носителя хранилища класса узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2292">Host Class Storage Media Capacity Get</span></span> 

#### <a name="ux_host_class_storage_media_capacity_get"></a><span data-ttu-id="4c86d-2293">ux_host_class_storage_media_capacity_get</span><span class="sxs-lookup"><span data-stu-id="4c86d-2293">ux_host_class_storage_media_capacity_get</span></span>

<span data-ttu-id="4c86d-2294">**Значок** ![Значок получения емкости носителя хранилища класса узла](./media/user-guide/usbx-events/image176.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2294">**Icon** ![Host Class Storage Media Capacity Get icon](./media/user-guide/usbx-events/image176.png)</span></span>

<span data-ttu-id="4c86d-2295">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2295">**Description**</span></span>

<span data-ttu-id="4c86d-2296">Это событие представляет собой получение емкости носителя хранилища класса узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2296">This event represents a USBX Host Class Storage Media Capacity Get Event.</span></span>

<span data-ttu-id="4c86d-2297">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2297">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2298">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2298">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2299">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2299">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-2300">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2300">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2301">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2301">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-media-format-capacity-get"></a><span data-ttu-id="4c86d-2302">Получение формата емкости носителя в хранилище класса узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2302">Host Class Storage Media Format Capacity Get</span></span>

#### <a name="ux_host_class_storage_media_format_capacity_get"></a><span data-ttu-id="4c86d-2303">ux_host_class_storage_media_format_capacity_get</span><span class="sxs-lookup"><span data-stu-id="4c86d-2303">ux_host_class_storage_media_format_capacity_get</span></span>

<span data-ttu-id="4c86d-2304">**Значок** ![Значок получения формата емкости носителя в хранилище класса узла](./media/user-guide/usbx-events/image177.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2304">**Icon** ![Host Class Storage Media Format Capacity Get icon](./media/user-guide/usbx-events/image177.png)</span></span>

<span data-ttu-id="4c86d-2305">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2305">**Description**</span></span>

<span data-ttu-id="4c86d-2306">Это событие представляет собой получение формата емкости носителя в хранилище класса узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2306">This event represents a USBX Host Class Storage Media Format Capacity Get Event.</span></span>

<span data-ttu-id="4c86d-2307">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2307">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2308">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2308">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2309">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2309">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-2310">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2310">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2311">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2311">Info Field 4: Not used.</span></span>

#### <a name="host-class-storage-media-mount"></a><span data-ttu-id="4c86d-2312">Подключение носителя хранилища класса узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2312">Host Class Storage Media Mount</span></span> 

#### <a name="ux_host_class_storage_media_mount"></a><span data-ttu-id="4c86d-2313">ux_host_class_storage_media_mount</span><span class="sxs-lookup"><span data-stu-id="4c86d-2313">ux_host_class_storage_media_mount</span></span>

<span data-ttu-id="4c86d-2314">**Значок** ![Значок подключения носителя хранилища класса узла](./media/user-guide/usbx-events/image178.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2314">**Icon** ![Host Class Storage Media Mount icon](./media/user-guide/usbx-events/image178.png)</span></span>

<span data-ttu-id="4c86d-2315">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2315">**Description**</span></span>

<span data-ttu-id="4c86d-2316">Это событие представляет собой подключение носителя хранилища класса узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2316">This event represents a USBX Host Class Storage Media Mount Event.</span></span>

<span data-ttu-id="4c86d-2317">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2317">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2318">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2318">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2319">Поле сведений 2. Сектор.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2319">Info Field 2: Sector.</span></span>
- <span data-ttu-id="4c86d-2320">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2320">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2321">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2321">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-media-open"></a><span data-ttu-id="4c86d-2322">Открытие носителя хранилища класса узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2322">Host Class Storage Media Open</span></span> 

#### <a name="ux_host_class_storage_media_open"></a><span data-ttu-id="4c86d-2323">ux_host_class_storage_media_open</span><span class="sxs-lookup"><span data-stu-id="4c86d-2323">ux_host_class_storage_media_open</span></span>

<span data-ttu-id="4c86d-2324">**Значок** ![Значок открытия носителя хранилища класса узла](./media/user-guide/usbx-events/image179.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2324">**Icon** ![Host Class Storage Media Open icon](./media/user-guide/usbx-events/image179.png)</span></span>

<span data-ttu-id="4c86d-2325">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2325">**Description**</span></span>

<span data-ttu-id="4c86d-2326">Это событие представляет собой открытие носителя хранилища класса узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2326">This event represents a USBX Host Class Storage Media Open Event.</span></span>

<span data-ttu-id="4c86d-2327">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2327">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2328">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2328">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2329">Поле сведений 2. Носитель.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2329">Info Field 2: Media.</span></span>
- <span data-ttu-id="4c86d-2330">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2330">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2331">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2331">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-media-read"></a><span data-ttu-id="4c86d-2332">Считывание носителя хранилища класса узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2332">Host Class Storage Media Read</span></span> 

#### <a name="ux_host_class_storage_media_read"></a><span data-ttu-id="4c86d-2333">ux_host_class_storage_media_read</span><span class="sxs-lookup"><span data-stu-id="4c86d-2333">ux_host_class_storage_media_read</span></span>

<span data-ttu-id="4c86d-2334">**Значок** ![Значок считывания носителя хранилища класса узла](./media/user-guide/usbx-events/image180.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2334">**Icon** ![Host Class Storage Media Read icon](./media/user-guide/usbx-events/image180.png)</span></span>

<span data-ttu-id="4c86d-2335">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2335">**Description**</span></span>

<span data-ttu-id="4c86d-2336">Это событие представляет собой считывание носителя хранилища класса узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2336">This event represents a USBX Host Class Storage Media Read Event.</span></span>

<span data-ttu-id="4c86d-2337">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2337">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2338">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2338">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2339">Поле сведений 2. Запуск сектора.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2339">Info Field 2: Sector start.</span></span>
- <span data-ttu-id="4c86d-2340">Поле сведений 3. Число секторов.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2340">Info Field 3: Sector count.</span></span>
- <span data-ttu-id="4c86d-2341">Поле сведений 4. Указатель данных.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2341">Info Field 4: Data pointer.</span></span>

### <a name="host-class-storage-media-write"></a><span data-ttu-id="4c86d-2342">Запись носителя хранилища класса узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2342">Host Class Storage Media Write</span></span> 

#### <a name="ux_host_class_storage_media_write"></a><span data-ttu-id="4c86d-2343">ux_host_class_storage_media_write</span><span class="sxs-lookup"><span data-stu-id="4c86d-2343">ux_host_class_storage_media_write</span></span>

<span data-ttu-id="4c86d-2344">**Значок** ![Значок записи носителя хранилища класса узла](./media/user-guide/usbx-events/image181.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2344">**Icon** ![Host Class Storage Media Write icon](./media/user-guide/usbx-events/image181.png)</span></span>

<span data-ttu-id="4c86d-2345">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2345">**Description**</span></span>

<span data-ttu-id="4c86d-2346">Это событие представляет собой запись носителя хранилища класса узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2346">This event represents a USBX Host Class Storage Media Write Event.</span></span>

<span data-ttu-id="4c86d-2347">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2347">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2348">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2348">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2349">Поле сведений 2. Запуск сектора.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2349">Info Field 2: Sector start.</span></span>
- <span data-ttu-id="4c86d-2350">Поле сведений 3. Число секторов.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2350">Info Field 3: Sector count.</span></span>
- <span data-ttu-id="4c86d-2351">Поле сведений 4. Указатель данных.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2351">Info Field 4: Data pointer.</span></span>

### <a name="host-class-storage-request-sense"></a><span data-ttu-id="4c86d-2352">Запрос на контроль хранилища класса узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2352">Host Class Storage Request Sense</span></span> 

#### <a name="ux_host_class_storage_request_sense"></a><span data-ttu-id="4c86d-2353">ux_host_class_storage_request_sense</span><span class="sxs-lookup"><span data-stu-id="4c86d-2353">ux_host_class_storage_request_sense</span></span>

<span data-ttu-id="4c86d-2354">**Значок** ![Значок запроса на контроль хранилища класса узла](./media/user-guide/usbx-events/image182.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2354">**Icon** ![Host Class Storage Request Sense icon](./media/user-guide/usbx-events/image182.png)</span></span>

<span data-ttu-id="4c86d-2355">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2355">**Description**</span></span>

<span data-ttu-id="4c86d-2356">Это событие представляет собой запрос на контроль хранилища класса узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2356">This event represents a USBX Host Class Storage Request Sense Event.</span></span>

<span data-ttu-id="4c86d-2357">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2357">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2358">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2358">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2359">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2359">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-2360">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2360">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2361">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2361">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-start-stop"></a><span data-ttu-id="4c86d-2362">Запуск и остановка хранилища класса узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2362">Host Class Storage Start Stop</span></span> 

#### <a name="ux_host_class_storage_start_stop"></a><span data-ttu-id="4c86d-2363">ux_host_class_storage_start_stop</span><span class="sxs-lookup"><span data-stu-id="4c86d-2363">ux_host_class_storage_start_stop</span></span>

<span data-ttu-id="4c86d-2364">**Значок** ![Значок запуска и остановки хранилища класса узла](./media/user-guide/usbx-events/image183.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2364">**Icon** ![Host Class Storage Start Stop icon](./media/user-guide/usbx-events/image183.png)</span></span>

<span data-ttu-id="4c86d-2365">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2365">**Description**</span></span>

<span data-ttu-id="4c86d-2366">Это событие представляет собой запуск и остановку хранилища класса узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2366">This event represents a USBX Host Class Storage Start Stop Event.</span></span>

<span data-ttu-id="4c86d-2367">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2367">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2368">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2368">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2369">Поле сведений 2. Сигнал о запуске и остановке.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2369">Info Field 2: Start stop signal.</span></span>
- <span data-ttu-id="4c86d-2370">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2370">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2371">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2371">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-unit-ready-test"></a><span data-ttu-id="4c86d-2372">Тест готовности единиц хранения для класса узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2372">Host Class Storage Unit Ready Test</span></span> 

#### <a name="ux_host_class_storage_unit_ready_test"></a><span data-ttu-id="4c86d-2373">ux_host_class_storage_unit_ready_test</span><span class="sxs-lookup"><span data-stu-id="4c86d-2373">ux_host_class_storage_unit_ready_test</span></span>

<span data-ttu-id="4c86d-2374">**Значок** ![Значок теста готовности единиц хранения для класса узла](./media/user-guide/usbx-events/image184.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2374">**Icon** ![Host Class Storage Unit Ready Test icon](./media/user-guide/usbx-events/image184.png)</span></span>

<span data-ttu-id="4c86d-2375">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2375">**Description**</span></span>

<span data-ttu-id="4c86d-2376">Это событие представляет собой событие теста готовности единиц хранения для класса узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2376">This event represents a USBX Host Class Storage Unit Ready Test Event.</span></span>

<span data-ttu-id="4c86d-2377">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2377">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2378">Поле сведений 1. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2378">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4c86d-2379">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2379">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-2380">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2380">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2381">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2381">Info Field 4: Not used.</span></span>

### <a name="host-stack-class-instance-create"></a><span data-ttu-id="4c86d-2382">Создание экземпляра класса стека узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2382">Host Stack Class Instance Create</span></span> 

#### <a name="ux_host_class_instance_create"></a><span data-ttu-id="4c86d-2383">ux_host_class_instance_create</span><span class="sxs-lookup"><span data-stu-id="4c86d-2383">ux_host_class_instance_create</span></span>

<span data-ttu-id="4c86d-2384">**Значок** ![Значок создания экземпляра класса стека узла](./media/user-guide/usbx-events/image185.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2384">**Icon** ![Host Stack Class Instance Create icon](./media/user-guide/usbx-events/image185.png)</span></span>

<span data-ttu-id="4c86d-2385">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2385">**Description**</span></span>

<span data-ttu-id="4c86d-2386">Это событие представляет собой создание экземпляра класса стека узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2386">This event represents a USBX Host Stack Class Instance Create Event.</span></span>

<span data-ttu-id="4c86d-2387">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2387">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2388">Поле сведений 1. Класс.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2388">Info Field 1: Class.</span></span>
- <span data-ttu-id="4c86d-2389">Поле сведений 2. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2389">Info Field 2: Class Instance.</span></span>
- <span data-ttu-id="4c86d-2390">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2390">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2391">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2391">Info Field 4: Not used.</span></span>

### <a name="host-stack-class-instance-destroy"></a><span data-ttu-id="4c86d-2392">Уничтожение экземпляра класса стека узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2392">Host Stack Class Instance Destroy</span></span> 

#### <a name="ux_host_class_instance_create"></a><span data-ttu-id="4c86d-2393">ux_host_class_instance_create</span><span class="sxs-lookup"><span data-stu-id="4c86d-2393">ux_host_class_instance_create</span></span>

<span data-ttu-id="4c86d-2394">**Значок** ![Значок уничтожения экземпляра класса стека узла](./media/user-guide/usbx-events/image186.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2394">**Icon** ![Host Stack Class Instance Destroy icon](./media/user-guide/usbx-events/image186.png)</span></span>

<span data-ttu-id="4c86d-2395">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2395">**Description**</span></span>

<span data-ttu-id="4c86d-2396">Это событие представляет собой уничтожение экземпляра класса стека узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2396">This event represents a USBX Host Stack Class Instance Destroy Event.</span></span>

<span data-ttu-id="4c86d-2397">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2397">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2398">Поле сведений 1. Класс.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2398">Info Field 1: Class.</span></span>
- <span data-ttu-id="4c86d-2399">Поле сведений 2. Экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2399">Info Field 2: Class Instance.</span></span>
- <span data-ttu-id="4c86d-2400">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2400">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2401">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2401">Info Field 4: Not used.</span></span>

### <a name="host-stack-configuration-delete"></a><span data-ttu-id="4c86d-2402">Удаление конфигурации стека узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2402">Host Stack Configuration Delete</span></span> 

#### <a name="ux_host_class_configuration_delete"></a><span data-ttu-id="4c86d-2403">ux_host_class_configuration_delete</span><span class="sxs-lookup"><span data-stu-id="4c86d-2403">ux_host_class_configuration_delete</span></span>

<span data-ttu-id="4c86d-2404">**Значок** ![Значок удаления конфигурации стека узла](./media/user-guide/usbx-events/image187.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2404">**Icon** ![Host Stack Configuration Delete icon](./media/user-guide/usbx-events/image187.png)</span></span>

<span data-ttu-id="4c86d-2405">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2405">**Description**</span></span>

<span data-ttu-id="4c86d-2406">Это событие представляет собой удаление конфигурации стека узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2406">This event represents a USBX Host Stack Configuration Delete Event.</span></span>

<span data-ttu-id="4c86d-2407">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2407">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2408">Поле сведений 1. Конфигурация.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2408">Info Field 1: Configuration.</span></span>
- <span data-ttu-id="4c86d-2409">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2409">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-2410">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2410">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2411">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2411">Info Field 4: Not used.</span></span>

### <a name="host-stack-configuration-enumerate"></a><span data-ttu-id="4c86d-2412">Перечисление конфигураций стека узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2412">Host Stack Configuration Enumerate</span></span> 

#### <a name="ux_host_stack_configuration_enumerate"></a><span data-ttu-id="4c86d-2413">ux_host_stack_configuration_enumerate</span><span class="sxs-lookup"><span data-stu-id="4c86d-2413">ux_host_stack_configuration_enumerate</span></span>

<span data-ttu-id="4c86d-2414">**Значок** ![Значок перечисления конфигураций стека узла](./media/user-guide/usbx-events/image188.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2414">**Icon** ![Host Stack Configuration Enumerate icon](./media/user-guide/usbx-events/image188.png)</span></span>

<span data-ttu-id="4c86d-2415">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2415">**Description**</span></span>

<span data-ttu-id="4c86d-2416">Это событие представляет собой перечисление конфигураций стека узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2416">This event represents a USBX Host Stack Configuration Enumerate Event.</span></span>

<span data-ttu-id="4c86d-2417">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2417">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2418">Поле сведений 1. Устройство.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2418">Info Field 1: Device.</span></span>
- <span data-ttu-id="4c86d-2419">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2419">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-2420">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2420">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2421">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2421">Info Field 4: Not used.</span></span>

### <a name="stack-configuration-instance-create"></a><span data-ttu-id="4c86d-2422">Создание экземпляра конфигурации стека</span><span class="sxs-lookup"><span data-stu-id="4c86d-2422">Stack Configuration Instance Create</span></span> 

#### <a name="ux_host_stack_configuration_instance_create"></a><span data-ttu-id="4c86d-2423">ux_host_stack_configuration_instance_create</span><span class="sxs-lookup"><span data-stu-id="4c86d-2423">ux_host_stack_configuration_instance_create</span></span>

<span data-ttu-id="4c86d-2424">**Значок** ![Значок создания экземпляра конфигурации стека](./media/user-guide/usbx-events/image189.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2424">**Icon** ![Stack Configuration Instance Create icon](./media/user-guide/usbx-events/image189.png)</span></span>

<span data-ttu-id="4c86d-2425">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2425">**Description**</span></span>

<span data-ttu-id="4c86d-2426">Это событие представляет собой создание экземпляра конфигурации стека узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2426">This event represents a USBX Host Stack Configuration Instance Create Event.</span></span>

<span data-ttu-id="4c86d-2427">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2427">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2428">Поле сведений 1. Конфигурация.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2428">Info Field 1: Configuration.</span></span>
- <span data-ttu-id="4c86d-2429">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2429">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-2430">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2430">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2431">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2431">Info Field 4: Not used.</span></span>

### <a name="host-stack-configuration-instance-delete"></a><span data-ttu-id="4c86d-2432">Удаление экземпляра конфигурации стека узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2432">Host Stack Configuration Instance Delete</span></span> 

#### <a name="ux_host_stack_configuration_instance_delete"></a><span data-ttu-id="4c86d-2433">ux_host_stack_configuration_instance_delete</span><span class="sxs-lookup"><span data-stu-id="4c86d-2433">ux_host_stack_configuration_instance_delete</span></span>

<span data-ttu-id="4c86d-2434">**Значок** ![Значок удаления экземпляра конфигурации стека узла](./media/user-guide/usbx-events/image190.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2434">**Icon** ![Host Stack Configuration Instance Delete icon](./media/user-guide/usbx-events/image190.png)</span></span>

<span data-ttu-id="4c86d-2435">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2435">**Description**</span></span>

<span data-ttu-id="4c86d-2436">Это событие представляет собой удаление экземпляра конфигурации стека узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2436">This event represents a USBX Host Stack Configuration Instance Delete Event.</span></span>

<span data-ttu-id="4c86d-2437">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2437">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2438">Поле сведений 1. Конфигурация.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2438">Info Field 1: Configuration.</span></span>
- <span data-ttu-id="4c86d-2439">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2439">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-2440">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2440">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2441">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2441">Info Field 4: Not used.</span></span>

### <a name="host-stack-configuration-set"></a><span data-ttu-id="4c86d-2442">Набор конфигураций стека узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2442">Host Stack Configuration Set</span></span> 

#### <a name="ux_host_stack_configuration_set"></a><span data-ttu-id="4c86d-2443">ux_host_stack_configuration_set</span><span class="sxs-lookup"><span data-stu-id="4c86d-2443">ux_host_stack_configuration_set</span></span>

<span data-ttu-id="4c86d-2444">**Значок** ![Значок набора конфигураций стека узла](./media/user-guide/usbx-events/image191.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2444">**Icon** ![Host Stack Configuration Set icon](./media/user-guide/usbx-events/image191.png)</span></span>

<span data-ttu-id="4c86d-2445">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2445">**Description**</span></span>

<span data-ttu-id="4c86d-2446">Это событие представляет собой событие набора конфигураций стека узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2446">This event represents a USBX Host Stack Configuration Set Event.</span></span>

<span data-ttu-id="4c86d-2447">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2447">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2448">Поле сведений 1. Конфигурация.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2448">Info Field 1: Configuration.</span></span>
- <span data-ttu-id="4c86d-2449">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2449">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-2450">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2450">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2451">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2451">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-address-set"></a><span data-ttu-id="4c86d-2452">Набор адресов устройства стека узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2452">Host Stack Device Address Set</span></span> 

#### <a name="ux_host_stack_device_address_set"></a><span data-ttu-id="4c86d-2453">ux_host_stack_device_address_set</span><span class="sxs-lookup"><span data-stu-id="4c86d-2453">ux_host_stack_device_address_set</span></span>

<span data-ttu-id="4c86d-2454">**Значок** ![Значок набора адресов устройства стека узла](./media/user-guide/usbx-events/image192.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2454">**Icon** ![Host Stack Device Address Set icon](./media/user-guide/usbx-events/image192.png)</span></span>

<span data-ttu-id="4c86d-2455">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2455">**Description**</span></span>

<span data-ttu-id="4c86d-2456">Это событие представляет собой событие набора адресов устройства стека узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2456">This event represents a USBX Host Stack Device Address Set Event.</span></span>

<span data-ttu-id="4c86d-2457">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2457">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2458">Поле сведений 1. Устройство.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2458">Info Field 1: Device.</span></span>
- <span data-ttu-id="4c86d-2459">Поле сведений 2. Адрес устройства.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2459">Info Field 2: Device Address.</span></span>
- <span data-ttu-id="4c86d-2460">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2460">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2461">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2461">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-configuration-get"></a><span data-ttu-id="4c86d-2462">Получение конфигурации устройства стека узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2462">Host Stack Device Configuration Get</span></span> 

#### <a name="ux_host_stack_device_configuration_get"></a><span data-ttu-id="4c86d-2463">ux_host_stack_device_configuration_get</span><span class="sxs-lookup"><span data-stu-id="4c86d-2463">ux_host_stack_device_configuration_get</span></span>

<span data-ttu-id="4c86d-2464">**Значок** ![Значок получения конфигурации устройства стека узла](./media/user-guide/usbx-events/image193.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2464">**Icon** ![Host Stack Device Configuration Get icon](./media/user-guide/usbx-events/image193.png)</span></span>

<span data-ttu-id="4c86d-2465">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2465">**Description**</span></span>

<span data-ttu-id="4c86d-2466">Это событие представляет собой получение конфигурации устройства стека узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2466">This event represents a USBX Host Stack Device Configuration Get Event.</span></span>

<span data-ttu-id="4c86d-2467">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2467">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2468">Поле сведений 1. Устройство.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2468">Info Field 1: Device.</span></span>
- <span data-ttu-id="4c86d-2469">Поле сведений 2. Конфигурация.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2469">nfo Field 2: Configuration.</span></span>
- <span data-ttu-id="4c86d-2470">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2470">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2471">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2471">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-configuration-select"></a><span data-ttu-id="4c86d-2472">Выбор конфигурации устройства стека узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2472">Host Stack Device Configuration Select</span></span> 

#### <a name="ux_host_stack_device_configuration_select"></a><span data-ttu-id="4c86d-2473">ux_host_stack_device_configuration_select</span><span class="sxs-lookup"><span data-stu-id="4c86d-2473">ux_host_stack_device_configuration_select</span></span>

<span data-ttu-id="4c86d-2474">**Значок** ![Значок выбора конфигурации устройства стека узла](./media/user-guide/usbx-events/image194.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2474">**Icon** ![Host Stack Device Configuration Select icon](./media/user-guide/usbx-events/image194.png)</span></span>

<span data-ttu-id="4c86d-2475">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2475">**Description**</span></span>

<span data-ttu-id="4c86d-2476">Это событие представляет собой выбор конфигурации устройства стека узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2476">This event represents a USBX Host Stack Device Configuration Select Event.</span></span>

<span data-ttu-id="4c86d-2477">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2477">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2478">Поле сведений 1. Устройство.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2478">Info Field 1: Device.</span></span>
- <span data-ttu-id="4c86d-2479">Поле сведений 2. Конфигурация.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2479">Info Field 2: Configuration.</span></span>
- <span data-ttu-id="4c86d-2480">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2480">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2481">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2481">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-descriptor-read"></a><span data-ttu-id="4c86d-2482">Считывание дескриптора устройства стека узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2482">Host Stack Device Descriptor Read</span></span> 

#### <a name="ux_host_stack_device_descriptor_read"></a><span data-ttu-id="4c86d-2483">ux_host_stack_device_descriptor_read</span><span class="sxs-lookup"><span data-stu-id="4c86d-2483">ux_host_stack_device_descriptor_read</span></span>

<span data-ttu-id="4c86d-2484">**Значок** ![Значок считывания дескриптора устройства стека узла](./media/user-guide/usbx-events/image195.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2484">**Icon** ![Host Stack Device Descriptor Read icon](./media/user-guide/usbx-events/image195.png)</span></span>

<span data-ttu-id="4c86d-2485">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2485">**Description**</span></span>

<span data-ttu-id="4c86d-2486">Это событие представляет собой считывание дескриптора устройства стека узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2486">This event represents a USBX Host Stack Device Descriptor Read Event.</span></span>

<span data-ttu-id="4c86d-2487">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2487">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2488">Поле сведений 1. Устройство.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2488">Info Field 1: Device.</span></span>
- <span data-ttu-id="4c86d-2489">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2489">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-2490">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2490">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2491">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2491">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-get"></a><span data-ttu-id="4c86d-2492">Получение устройства стека узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2492">Host Stack Device Get</span></span> 

#### <a name="ux_host_stack_device_get"></a><span data-ttu-id="4c86d-2493">ux_host_stack_device_get</span><span class="sxs-lookup"><span data-stu-id="4c86d-2493">ux_host_stack_device_get</span></span>

<span data-ttu-id="4c86d-2494">**Значок** ![Значок получения устройства стека узла](./media/user-guide/usbx-events/image196.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2494">**Icon** ![Host Stack Device Get icon](./media/user-guide/usbx-events/image196.png)</span></span>

<span data-ttu-id="4c86d-2495">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2495">**Description**</span></span>

<span data-ttu-id="4c86d-2496">Это событие представляет собой событие получения устройства стека узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2496">This event represents a USBX Host Stack Device Get Event.</span></span>

<span data-ttu-id="4c86d-2497">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2497">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2498">Поле сведений 1. Индекс устройства.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2498">Info Field 1: Device index.</span></span>
- <span data-ttu-id="4c86d-2499">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2499">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-2500">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2500">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2501">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2501">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-remove"></a><span data-ttu-id="4c86d-2502">Удаление устройства стека узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2502">Host Stack Device Remove</span></span> 

#### <a name="ux_host_stack_device_remove"></a><span data-ttu-id="4c86d-2503">ux_host_stack_device_remove</span><span class="sxs-lookup"><span data-stu-id="4c86d-2503">ux_host_stack_device_remove</span></span>

<span data-ttu-id="4c86d-2504">**Значок** ![Значок удаления устройства стека узла](./media/user-guide/usbx-events/image197.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2504">**Icon** ![Host Stack Device Remove icon](./media/user-guide/usbx-events/image197.png)</span></span>

<span data-ttu-id="4c86d-2505">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2505">**Description**</span></span>

<span data-ttu-id="4c86d-2506">Это событие представляет собой удаление устройства стека узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2506">This event represents a USBX Host Stack Device Remove Event.</span></span>

<span data-ttu-id="4c86d-2507">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2507">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2508">Поле сведений 1. Hcd.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2508">Info Field 1: Hcd.</span></span>
- <span data-ttu-id="4c86d-2509">Поле сведений 2. Родительский элемент.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2509">Info Field 2: Parent.</span></span>
- <span data-ttu-id="4c86d-2510">Поле сведений 3. Индекс порта.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2510">Info Field 3: Port Index.</span></span>
- <span data-ttu-id="4c86d-2511">Поле сведений 4. Устройство.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2511">Info Field 4: Device.</span></span>

### <a name="host-stack-device-resource-free"></a><span data-ttu-id="4c86d-2512">Освобождение ресурса устройства стека узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2512">Host Stack Device Resource Free</span></span> 

#### <a name="ux_host_stack_device_resource_free"></a><span data-ttu-id="4c86d-2513">ux_host_stack_device_resource_free</span><span class="sxs-lookup"><span data-stu-id="4c86d-2513">ux_host_stack_device_resource_free</span></span>

<span data-ttu-id="4c86d-2514">**Значок** ![Значок освобождения ресурса устройства стека узла](./media/user-guide/usbx-events/image198.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2514">**Icon** ![Host Stack Device Resource Free icon](./media/user-guide/usbx-events/image198.png)</span></span>

<span data-ttu-id="4c86d-2515">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2515">**Description**</span></span>

<span data-ttu-id="4c86d-2516">Это событие представляет собой освобождение ресурса устройства стека узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2516">This event represents a USBX Host Stack Device Resource Free Event.</span></span>

<span data-ttu-id="4c86d-2517">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2517">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2518">Поле сведений 1. Устройство.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2518">Info Field 1: Device.</span></span>
- <span data-ttu-id="4c86d-2519">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2519">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-2520">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2520">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2521">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2521">Info Field 4: Not used.</span></span>

### <a name="host-stack-endpoint-instance-create"></a><span data-ttu-id="4c86d-2522">Создание экземпляра конечной точки стека узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2522">Host Stack Endpoint Instance Create</span></span> 

#### <a name="ux_host_stack_endpoint_instance_create"></a><span data-ttu-id="4c86d-2523">ux_host_stack_endpoint_instance_create</span><span class="sxs-lookup"><span data-stu-id="4c86d-2523">ux_host_stack_endpoint_instance_create</span></span>

<span data-ttu-id="4c86d-2524">**Значок** ![Значок создания экземпляра конечной точки стека узла](./media/user-guide/usbx-events/image199.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2524">**Icon** ![Host Stack Endpoint Instance Create icon](./media/user-guide/usbx-events/image199.png)</span></span>

<span data-ttu-id="4c86d-2525">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2525">**Description**</span></span>

<span data-ttu-id="4c86d-2526">Это событие представляет собой создание экземпляра конечной точки стека узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2526">This event represents a USBX Host Stack Endpoint Instance Create Event.</span></span>

<span data-ttu-id="4c86d-2527">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2527">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2528">Поле сведений 1. Устройство.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2528">Info Field 1: Device.</span></span>
- <span data-ttu-id="4c86d-2529">Поле сведений 2. Конечная точка.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2529">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="4c86d-2530">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2530">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2531">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2531">Info Field 4: Not used.</span></span>

### <a name="host-stack-endpoint-instance-delete"></a><span data-ttu-id="4c86d-2532">Удаление экземпляра конечной точки стека узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2532">Host Stack Endpoint Instance Delete</span></span> 

#### <a name="ux_host_stack_endpoint_instance_delete"></a><span data-ttu-id="4c86d-2533">ux_host_stack_endpoint_instance_delete</span><span class="sxs-lookup"><span data-stu-id="4c86d-2533">ux_host_stack_endpoint_instance_delete</span></span>

<span data-ttu-id="4c86d-2534">**Значок** ![Значок удаления экземпляра конечной точки стека узла](./media/user-guide/usbx-events/image200.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2534">**Icon** ![Host Stack Endpoint Instance Delete icon](./media/user-guide/usbx-events/image200.png)</span></span>

<span data-ttu-id="4c86d-2535">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2535">**Description**</span></span>

<span data-ttu-id="4c86d-2536">Это событие представляет собой удаление экземпляра конечной точки стека узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2536">This event represents a USBX Host Stack Endpoint Instance Delete Event.</span></span>

<span data-ttu-id="4c86d-2537">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2537">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2538">Поле сведений 2. Конечная точка.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2538">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="4c86d-2539">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2539">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2540">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2540">Info Field 4: Not used.</span></span>

### <a name="host-stack-endpoint-reset"></a><span data-ttu-id="4c86d-2541">Сброс конечной точки стека узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2541">Host Stack Endpoint Reset</span></span> 

#### <a name="ux_host_stack_endpoint_reset"></a><span data-ttu-id="4c86d-2542">ux_host_stack_endpoint_reset</span><span class="sxs-lookup"><span data-stu-id="4c86d-2542">ux_host_stack_endpoint_reset</span></span>

<span data-ttu-id="4c86d-2543">**Значок** ![Значок сброса конечной точки стека узла](./media/user-guide/usbx-events/image201.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2543">**Icon** ![Host Stack Endpoint Reset icon](./media/user-guide/usbx-events/image201.png)</span></span>

<span data-ttu-id="4c86d-2544">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2544">**Description**</span></span>

<span data-ttu-id="4c86d-2545">Это событие представляет собой сброс конечной точки стека узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2545">This event represents a USBX Host Stack Endpoint Reset Event.</span></span>

<span data-ttu-id="4c86d-2546">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2546">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2547">Поле сведений 1. Устройство.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2547">Info Field 1: Device.</span></span>
- <span data-ttu-id="4c86d-2548">Поле сведений 2. Конечная точка.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2548">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="4c86d-2549">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2549">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2550">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2550">Info Field 4: Not used.</span></span>

### <a name="host-stack-endpoint-transfer-abort"></a><span data-ttu-id="4c86d-2551">Прерывание перемещения конечной точки стека узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2551">Host Stack Endpoint Transfer Abort</span></span> 

#### <a name="ux_host_stack_endpoint_transfer_abort"></a><span data-ttu-id="4c86d-2552">ux_host_stack_endpoint_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="4c86d-2552">ux_host_stack_endpoint_transfer_abort</span></span>

<span data-ttu-id="4c86d-2553">**Значок** ![Значок прерывания перемещения конечной точки стека узла](./media/user-guide/usbx-events/image202.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2553">**Icon** ![Host Stack Endpoint Transfer Abort icon](./media/user-guide/usbx-events/image202.png)</span></span>

<span data-ttu-id="4c86d-2554">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2554">**Description**</span></span>

<span data-ttu-id="4c86d-2555">Это событие представляет собой прерывание перемещения конечной точки стека узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2555">This event represents a USBX Host Stack Endpoint Transfer Abort Event.</span></span>

<span data-ttu-id="4c86d-2556">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2556">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2557">Поле сведений 1. Конечная точка.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2557">Info Field 1: Endpoint.</span></span>
- <span data-ttu-id="4c86d-2558">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2558">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-2559">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2559">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2560">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2560">Info Field 4: Not used.</span></span>

### <a name="host-stack-host-controller-register"></a><span data-ttu-id="4c86d-2561">Регистрация хост-контроллера стека узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2561">Host Stack Host Controller Register</span></span> 

#### <a name="ux_host_stack_hcd_register"></a><span data-ttu-id="4c86d-2562">ux_host_stack_hcd_register</span><span class="sxs-lookup"><span data-stu-id="4c86d-2562">ux_host_stack_hcd_register</span></span>

<span data-ttu-id="4c86d-2563">**Значок** ![Значок регистрации хост-контроллера стека узла](./media/user-guide/usbx-events/image203.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2563">**Icon** ![Host Stack Host Controller Register icon](./media/user-guide/usbx-events/image203.png)</span></span>

<span data-ttu-id="4c86d-2564">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2564">**Description**</span></span>

<span data-ttu-id="4c86d-2565">Это событие представляет собой регистрацию хост-контроллера стека узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2565">This event represents a USBX Host Stack Host Controller Register.</span></span>

<span data-ttu-id="4c86d-2566">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2566">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2567">Поле сведений 1. Имя Hcd.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2567">Info Field 1: Hcd Name.</span></span>
- <span data-ttu-id="4c86d-2568">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2568">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-2569">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2569">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2570">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2570">Info Field 4: Not used.</span></span>

### <a name="host-stack-initialize"></a><span data-ttu-id="4c86d-2571">Инициализация стека узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2571">Host Stack Initialize</span></span> 

#### <a name="ux_host_stack_initialize"></a><span data-ttu-id="4c86d-2572">ux_host_stack_initialize</span><span class="sxs-lookup"><span data-stu-id="4c86d-2572">ux_host_stack_initialize</span></span>

<span data-ttu-id="4c86d-2573">**Значок** ![Значок инициализации стека узла](./media/user-guide/usbx-events/image204.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2573">**Icon** ![Host Stack Initialize icon](./media/user-guide/usbx-events/image204.png)</span></span>

<span data-ttu-id="4c86d-2574">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2574">**Description**</span></span>

<span data-ttu-id="4c86d-2575">Это событие представляет собой инициализацию стека узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2575">This event represents a USBX Host Stack Initialize Event.</span></span>

<span data-ttu-id="4c86d-2576">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2576">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2577">Поле сведений 1. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2577">Info Field 1: Not used.</span></span>
- <span data-ttu-id="4c86d-2578">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2578">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-2579">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2579">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2580">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2580">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-endpoint-get"></a><span data-ttu-id="4c86d-2581">Получение конечной точки интерфейса стека узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2581">Host Stack Interface Endpoint Get</span></span> 

#### <a name="interface_-tcp-retry-entry"></a><span data-ttu-id="4c86d-2582">Interface_ TCP retry entry</span><span class="sxs-lookup"><span data-stu-id="4c86d-2582">Interface_ TCP retry entry</span></span>

<span data-ttu-id="4c86d-2583">**Значок** ![Значок получения конечной точки интерфейса стека узла](./media/user-guide/usbx-events/image205.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2583">**Icon** ![Host Stack Interface Endpoint Get icon](./media/user-guide/usbx-events/image205.png)</span></span>

<span data-ttu-id="4c86d-2584">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2584">**Description**</span></span>

<span data-ttu-id="4c86d-2585">Это событие представляет собой событие повторной попытки подключения по внутреннему протоколу TCP в NetX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2585">This event represents an internal NetX TCP retry event.</span></span>

<span data-ttu-id="4c86d-2586">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2586">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2587">Поле сведений 1. Интерфейс.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2587">Info Field 1: Interface.</span></span>
- <span data-ttu-id="4c86d-2588">Поле сведений 2. Индекс конечной точки.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2588">Info Field 2: Endpoint index.</span></span>
- <span data-ttu-id="4c86d-2589">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2589">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2590">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2590">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-instance-create"></a><span data-ttu-id="4c86d-2591">Создание экземпляра интерфейса стека узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2591">Host Stack Interface Instance Create</span></span> 

#### <a name="ux_host_stack_interface_instance_create"></a><span data-ttu-id="4c86d-2592">ux_host_stack_interface_instance_create</span><span class="sxs-lookup"><span data-stu-id="4c86d-2592">ux_host_stack_interface_instance_create</span></span>

<span data-ttu-id="4c86d-2593">**Значок** ![Значок создания экземпляра интерфейса стека узла](./media/user-guide/usbx-events/image206.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2593">**Icon** ![Host Stack Interface Instance Create icon](./media/user-guide/usbx-events/image206.png)</span></span>

<span data-ttu-id="4c86d-2594">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2594">**Description**</span></span>

<span data-ttu-id="4c86d-2595">Это событие представляет собой создание экземпляра интерфейса стека узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2595">This event represents a USBX Host Stack Interface Instance Create Event.</span></span>

<span data-ttu-id="4c86d-2596">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2596">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2597">Поле сведений 1. Интерфейс.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2597">Info Field 1: Interface.</span></span>
- <span data-ttu-id="4c86d-2598">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2598">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-2599">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2599">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2600">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2600">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-instance-delete"></a><span data-ttu-id="4c86d-2601">Удаление экземпляра интерфейса стека узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2601">Host Stack Interface Instance Delete</span></span> 

#### <a name="ux_host_stack_interface_instance_delete"></a><span data-ttu-id="4c86d-2602">ux_host_stack_interface_instance_delete</span><span class="sxs-lookup"><span data-stu-id="4c86d-2602">ux_host_stack_interface_instance_delete</span></span>

<span data-ttu-id="4c86d-2603">**Значок** ![Значок удаления экземпляра интерфейса стека узла](./media/user-guide/usbx-events/image207.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2603">**Icon** ![Host Stack Interface Instance Delete icon](./media/user-guide/usbx-events/image207.png)</span></span>

<span data-ttu-id="4c86d-2604">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2604">**Description**</span></span>

<span data-ttu-id="4c86d-2605">Это событие представляет собой удаление экземпляра интерфейса стека узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2605">This event represents a USBX Host Stack Interface Instance Delete Event.</span></span>

<span data-ttu-id="4c86d-2606">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2606">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2607">Поле сведений 1. Интерфейс.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2607">Info Field 1: Interface.</span></span>
- <span data-ttu-id="4c86d-2608">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2608">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-2609">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2609">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2610">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2610">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-set"></a><span data-ttu-id="4c86d-2611">Набор интерфейсов стека узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2611">Host Stack Interface Set</span></span> 

#### <a name="ux_host_stack_interface_set"></a><span data-ttu-id="4c86d-2612">ux_host_stack_interface_set</span><span class="sxs-lookup"><span data-stu-id="4c86d-2612">ux_host_stack_interface_set</span></span>

<span data-ttu-id="4c86d-2613">**Значок** ![Значок набора интерфейсов стека узла](./media/user-guide/usbx-events/image208.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2613">**Icon** ![Host Stack Interface Set icon](./media/user-guide/usbx-events/image208.png)</span></span>

<span data-ttu-id="4c86d-2614">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2614">**Description**</span></span>

<span data-ttu-id="4c86d-2615">Это событие представляет собой событие набора интерфейсов стека узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2615">This event represents a USBX Host Stack Interface Set Event.</span></span>

<span data-ttu-id="4c86d-2616">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2616">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2617">Поле сведений 1. Интерфейс.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2617">Info Field 1: Interface.</span></span>
- <span data-ttu-id="4c86d-2618">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2618">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-2619">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2619">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2620">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2620">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-setting-select"></a><span data-ttu-id="4c86d-2621">Выбор параметров для интерфейса стека узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2621">Host Stack Interface Setting Select</span></span> 

#### <a name="ux_host_stack_interface_setting_select"></a><span data-ttu-id="4c86d-2622">ux_host_stack_interface_setting_select</span><span class="sxs-lookup"><span data-stu-id="4c86d-2622">ux_host_stack_interface_setting_select</span></span>

<span data-ttu-id="4c86d-2623">**Значок** ![Значок выбора параметров для интерфейса стека узла](./media/user-guide/usbx-events/image209.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2623">**Icon** ![Host Stack Interface Setting Select icon](./media/user-guide/usbx-events/image209.png)</span></span>

<span data-ttu-id="4c86d-2624">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2624">**Description**</span></span>

<span data-ttu-id="4c86d-2625">Это событие представляет собой событие набора интерфейсов стека узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2625">This event represents a USBX Host Stack Interface Setting Select Event.</span></span>

<span data-ttu-id="4c86d-2626">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2626">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2627">Поле сведений 1. Интерфейс.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2627">Info Field 1: Interface.</span></span>
- <span data-ttu-id="4c86d-2628">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2628">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-2629">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2629">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2630">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2630">Info Field 4: Not used.</span></span>

### <a name="host-stack-new-configuration-create"></a><span data-ttu-id="4c86d-2631">Создание конфигурации стека узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2631">Host Stack New Configuration Create</span></span> 

#### <a name="ux_host_stack_new_configuration_create"></a><span data-ttu-id="4c86d-2632">ux_host_stack_new_configuration_create</span><span class="sxs-lookup"><span data-stu-id="4c86d-2632">ux_host_stack_new_configuration_create</span></span>

<span data-ttu-id="4c86d-2633">**Значок** ![Значок создания конфигурации стека узла](./media/user-guide/usbx-events/image210.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2633">**Icon** ![Host Stack New Configuration Create icon](./media/user-guide/usbx-events/image210.png)</span></span>

<span data-ttu-id="4c86d-2634">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2634">**Description**</span></span>
 
<span data-ttu-id="4c86d-2635">Это событие представляет собой создание конфигурации стека узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2635">This event represents a USBX Host Stack New Configuration Create Event.</span></span>

<span data-ttu-id="4c86d-2636">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2636">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2637">Поле сведений 1. Устройство.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2637">Info Field 1: Device.</span></span>
- <span data-ttu-id="4c86d-2638">Поле сведений 2. Конфигурация.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2638">Info Field 2: Configuration.</span></span>
- <span data-ttu-id="4c86d-2639">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2639">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2640">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2640">Info Field 4: Not used.</span></span>

### <a name="host-stack-new-device-create"></a><span data-ttu-id="4c86d-2641">Создание устройства в стеке узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2641">Host Stack New Device Create</span></span> 

#### <a name="ux_host_stack_new_device_create"></a><span data-ttu-id="4c86d-2642">ux_host_stack_new_device_create</span><span class="sxs-lookup"><span data-stu-id="4c86d-2642">ux_host_stack_new_device_create</span></span>

<span data-ttu-id="4c86d-2643">**Значок** ![Значок создания устройства в стеке узла](./media/user-guide/usbx-events/image211.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2643">**Icon** ![Host Stack New Device Create icon](./media/user-guide/usbx-events/image211.png)</span></span>

<span data-ttu-id="4c86d-2644">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2644">**Description**</span></span>
 
 <span data-ttu-id="4c86d-2645">Это событие представляет собой создание устройства в стеке узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2645">This event represents a USBX Host Stack New Device Create Event.</span></span>

<span data-ttu-id="4c86d-2646">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2646">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2647">Поле сведений 1. Hcd.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2647">Info Field 1: Hcd.</span></span>
- <span data-ttu-id="4c86d-2648">Поле сведений 2. Владелец устройства.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2648">Info Field 2: Device owner.</span></span>
- <span data-ttu-id="4c86d-2649">Поле сведений 3. Индекс порта.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2649">Info Field 3: Port index.</span></span>
- <span data-ttu-id="4c86d-2650">Поле сведений 4. Устройство.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2650">Info Field 4: Device.</span></span>

### <a name="host-stack-new-endpoint-create"></a><span data-ttu-id="4c86d-2651">Создание конечной точки стека узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2651">Host Stack New Endpoint Create</span></span> 

#### <a name="ux_host_stack_new_endpoint_create"></a><span data-ttu-id="4c86d-2652">ux_host_stack_new_endpoint_create</span><span class="sxs-lookup"><span data-stu-id="4c86d-2652">ux_host_stack_new_endpoint_create</span></span>

<span data-ttu-id="4c86d-2653">**Значок** ![Значок создания конечной точки стека узла](./media/user-guide/usbx-events/image212.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2653">**Icon** ![Host Stack New Endpoint Create icon](./media/user-guide/usbx-events/image212.png)</span></span>

<span data-ttu-id="4c86d-2654">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2654">**Description**</span></span>
 
<span data-ttu-id="4c86d-2655">Это событие представляет собой создание конечной точки стека узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2655">This event represents a USBX Host Stack New Endpoint Create Event.</span></span>

<span data-ttu-id="4c86d-2656">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2656">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2657">Поле сведений 1. Интерфейс.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2657">Info Field 1: Interface.</span></span>
- <span data-ttu-id="4c86d-2658">Поле сведений 2. Конечная точка.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2658">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="4c86d-2659">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2659">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2660">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2660">Info Field 4: Not used.</span></span>

### <a name="host-stack-root-hub-change-process"></a><span data-ttu-id="4c86d-2661">Процесс изменения корневого концентратора стека узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2661">Host Stack Root Hub Change Process</span></span> 

#### <a name="ux_host_stack_rh_change_process"></a><span data-ttu-id="4c86d-2662">ux_host_stack_rh_change_process</span><span class="sxs-lookup"><span data-stu-id="4c86d-2662">ux_host_stack_rh_change_process</span></span>

<span data-ttu-id="4c86d-2663">**Значок** ![Значок процесса изменения корневого концентратора стека узла](./media/user-guide/usbx-events/image213.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2663">**Icon** ![Host Stack Root Hub Change Process icon](./media/user-guide/usbx-events/image213.png)</span></span>

<span data-ttu-id="4c86d-2664">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2664">**Description**</span></span>
 
<span data-ttu-id="4c86d-2665">Это событие представляет собой процесс изменения корневого концентратора стека узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2665">This event represents a USBX Host Stack Root Hub Change Process.</span></span>

<span data-ttu-id="4c86d-2666">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2666">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2667">Поле сведений 1. Индекс порта.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2667">Info Field 1: Port index.</span></span>
- <span data-ttu-id="4c86d-2668">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2668">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c86d-2669">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2669">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2670">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2670">Info Field 4: Not used.</span></span>

### <a name="host-stack-root-hub-device-extraction"></a><span data-ttu-id="4c86d-2671">Извлечение устройства корневого концентратора стека узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2671">Host Stack Root Hub Device Extraction</span></span> 

#### <a name="ux_host_stack_rh_device_extraction"></a><span data-ttu-id="4c86d-2672">ux_host_stack_rh_device_extraction</span><span class="sxs-lookup"><span data-stu-id="4c86d-2672">ux_host_stack_rh_device_extraction</span></span>

<span data-ttu-id="4c86d-2673">**Значок** ![Значок извлечения устройства корневого концентратора стека узла](./media/user-guide/usbx-events/image214.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2673">**Icon** ![Host Stack Root Hub Device Extraction icon](./media/user-guide/usbx-events/image214.png)</span></span>

<span data-ttu-id="4c86d-2674">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2674">**Description**</span></span>

<span data-ttu-id="4c86d-2675">Это событие представляет собой извлечение устройства корневого концентратора стека узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2675">This event represents a USBX Host Stack Root Hub Device Extraction Event.</span></span>

<span data-ttu-id="4c86d-2676">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2676">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2677">Поле сведений 1. Hcd.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2677">Info Field 1: Hcd.</span></span>
- <span data-ttu-id="4c86d-2678">Поле сведений 2. Индекс порта.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2678">Info Field 2: Port index.</span></span>
- <span data-ttu-id="4c86d-2679">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2679">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2680">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2680">Info Field 4: Not used.</span></span>

### <a name="host-stack-root-hub-device-insertion"></a><span data-ttu-id="4c86d-2681">Вставка устройства корневого концентратора стека узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2681">Host Stack Root Hub Device Insertion</span></span> 

#### <a name="ux_host_stack_rh_device_insertion"></a><span data-ttu-id="4c86d-2682">ux_host_stack_rh_device_insertion</span><span class="sxs-lookup"><span data-stu-id="4c86d-2682">ux_host_stack_rh_device_insertion</span></span>

<span data-ttu-id="4c86d-2683">**Значок** ![Значок вставки устройства корневого концентратора стека узла](./media/user-guide/usbx-events/image215.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2683">**Icon** ![Host Stack Root Hub Device Insertion icon](./media/user-guide/usbx-events/image215.png)</span></span>

<span data-ttu-id="4c86d-2684">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2684">**Description**</span></span>

<span data-ttu-id="4c86d-2685">Это событие представляет собой вставку устройства корневого концентратора стека узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2685">This event represents a USBX Host Stack Root Hub Device Insertion.</span></span>

<span data-ttu-id="4c86d-2686">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2686">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2687">Поле сведений 1. Hcd.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2687">Info Field 1: Hcd.</span></span>
- <span data-ttu-id="4c86d-2688">Поле сведений 2. Индекс порта.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2688">Info Field 2: Port index.</span></span>
- <span data-ttu-id="4c86d-2689">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2689">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2690">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2690">Info Field 4: Not used.</span></span>

### <a name="host-stack-transfer-request"></a><span data-ttu-id="4c86d-2691">Запрос на передачу стека узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2691">Host Stack Transfer Request</span></span> 

#### <a name="ux_host_stack_transfer_request"></a><span data-ttu-id="4c86d-2692">ux_host_stack_transfer_request</span><span class="sxs-lookup"><span data-stu-id="4c86d-2692">ux_host_stack_transfer_request</span></span>

<span data-ttu-id="4c86d-2693">**Значок** ![Значок запроса на передачу стека узла](./media/user-guide/usbx-events/image216.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2693">**Icon** ![Host Stack Transfer Request icon](./media/user-guide/usbx-events/image216.png)</span></span>

<span data-ttu-id="4c86d-2694">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2694">**Description**</span></span>

<span data-ttu-id="4c86d-2695">Это событие представляет собой запрос на передачу стека узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2695">This event represents a USBX Host Stack Transfer Request.</span></span>

<span data-ttu-id="4c86d-2696">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2696">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2697">Поле сведений 1. Устройство.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2697">Info Field 1: Device.</span></span>
- <span data-ttu-id="4c86d-2698">Поле сведений 2. Конечная точка.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2698">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="4c86d-2699">Поле сведений 3. Запрос на передачу.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2699">Info Field 3: Transfer request.</span></span>
- <span data-ttu-id="4c86d-2700">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2700">Info Field 4: Not used.</span></span>

### <a name="host-stack-transfer-request-abort"></a><span data-ttu-id="4c86d-2701">Прерывание запроса на передачу стека узла</span><span class="sxs-lookup"><span data-stu-id="4c86d-2701">Host Stack Transfer Request Abort</span></span> 

#### <a name="internal-io-driver-get-status"></a><span data-ttu-id="4c86d-2702">Получение состояния внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="4c86d-2702">Internal I/O driver get status</span></span>

<span data-ttu-id="4c86d-2703">**Значок** ![Значок прерывания запроса на передачу стека узла](./media/user-guide/usbx-events/image217.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2703">**Icon** ![Host Stack Transfer Request Abort icon](./media/user-guide/usbx-events/image217.png)</span></span>

<span data-ttu-id="4c86d-2704">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2704">**Description**</span></span>

<span data-ttu-id="4c86d-2705">Это событие представляет собой прерывание запроса на передачу стека узла USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2705">This event represents a USBX Host Stack Transfer Request Abort.</span></span>

<span data-ttu-id="4c86d-2706">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2706">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2707">Поле сведений 1. Устройство.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2707">Info Field 1: Device.</span></span>
- <span data-ttu-id="4c86d-2708">Поле сведений 2. Конечная точка.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2708">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="4c86d-2709">Поле сведений 3. Запрос на передачу.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2709">Info Field 3: Transfer request.</span></span>
- <span data-ttu-id="4c86d-2710">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2710">Info Field 4: Not used.</span></span>

### <a name="usbx-error"></a><span data-ttu-id="4c86d-2711">Ошибка USBX</span><span class="sxs-lookup"><span data-stu-id="4c86d-2711">USBX Error</span></span> 

#### <a name="ux_error"></a><span data-ttu-id="4c86d-2712">ux_error</span><span class="sxs-lookup"><span data-stu-id="4c86d-2712">ux_error</span></span>

<span data-ttu-id="4c86d-2713">**Значок** ![Значок ошибки USBX](./media/user-guide/usbx-events/image218.png)</span><span class="sxs-lookup"><span data-stu-id="4c86d-2713">**Icon** ![U S B X Error icon](./media/user-guide/usbx-events/image218.png)</span></span>

<span data-ttu-id="4c86d-2714">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2714">**Description**</span></span>

<span data-ttu-id="4c86d-2715">Это событие представляет собой событие ошибки USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2715">This event represents a USBX Error Event.</span></span>

<span data-ttu-id="4c86d-2716">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="4c86d-2716">**Information Fields**</span></span>

- <span data-ttu-id="4c86d-2717">Поле сведений 1. Ошибка USBX.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2717">Info Field 1: USBX error.</span></span>
- <span data-ttu-id="4c86d-2718">Поле сведений 2. Имя ошибки.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2718">Info Field 2: Error Name.</span></span>
- <span data-ttu-id="4c86d-2719">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2719">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c86d-2720">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c86d-2720">Info Field 4: Not used.</span></span>