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
# <a name="chapter-9---azure-rtos-usbx-trace-events"></a>Глава 9. События трассировки USBX в ОСРВ Azure

В этой главе содержится описание событий USBX в Azure ОСРВ, отображаемых в TraceX. 

## <a name="list-of-events-and-icons"></a>Список событий и значков

Ниже приведен список событий USBX, отображаемых в TraceX.

| Значок                             | Значение                               |
| -------------------------------- | ------------------------------------- |
| ![Значок активации класса CDC устройства](./media/user-guide/usbx-events/image1.png)    | **Активация класса CDC устройства** *(ux_device_class_cdc_activate)* |
| ![Значок деактивации класса CDC устройства](./media/user-guide/usbx-events/image2.png)    | **Деактивация класса CDC устройства** *(ux_device_class_cdc_deactivate)* |
| ![Значок считывания класса CDC устройства](./media/user-guide/usbx-events/image3.png)    | **Считывание класса CDC устройства** *(ux_device_class_cdc_read)* |
| ![Значок записи класса CDC устройства](./media/user-guide/usbx-events/image4.png)    | **Запись класса CDC устройства** *(ux_device_class_cdc_write)* |
| ![Значок активации класса Dpump устройства](./media/user-guide/usbx-events/image5.png)    | **Активация класса Dpump устройства** *(ux_device_class_dpump_activate)* |
| ![Значок деактивации класса Dpump устройства](./media/user-guide/usbx-events/image6.png)    | **Деактивация класса Dpump устройства** *(ux_device_class_dpump_deactivate)* |
| ![Значок считывания класса Dpump устройства](./media/user-guide/usbx-events/image7.png)    | **Считывание класса Dpump устройства** *(ux_device_class_dpump_read)* |
| ![Значок записи класса Dpump устройства](./media/user-guide/usbx-events/image8.png)    | **Запись класса Dpump устройства** *(ux_device_class_dpump_write)* |
| ![Значок активации класса Hid устройства](./media/user-guide/usbx-events/image9.png)    | **Активация класса Hid устройства** *(ux_device_class_hid_activate)* |
| ![Значок деактивации класса Hid устройства](./media/user-guide/usbx-events/image10.png)    | **Деактивация класса Hid устройства** *(ux_device_class_hid_deactivate)* |
| ![Значок отправки дескриптора класса Hid устройства](./media/user-guide/usbx-events/image11.png)    | **Отправка дескриптора класса Hid устройства** *(ux_device_class_hid_descriptor_send)* |
| ![Значок получения события класса Hid устройства](./media/user-guide/usbx-events/image12.png)    | **Получение события класса Hid устройства** *(ux_device_class_hid_event_get)* |
| ![Значок набора событий класса Hid устройства](./media/user-guide/usbx-events/image13.png)    | **Набор событий класса Hid устройства** *(ux_device_class_hid_event_set)* |
| ![Значок получения отчета класса Hid устройства](./media/user-guide/usbx-events/image14.png)    | **Получение отчета класса Hid устройства** *(ux_device_class_hid_report_get)* |
| ![Значок набора отчетов класса Hid устройства](./media/user-guide/usbx-events/image15.png)    | **Набор отчетов класса Hid устройства** *(ux_device_class_hid_report_set)* |
| ![Значок активации класса Pima устройства](./media/user-guide/usbx-events/image16.png)    | **Активация класса Pima устройства** *(ux_device_class_pima_activate)* |
| ![Значок деактивации класса Pima устройства](./media/user-guide/usbx-events/image17.png)    | **Деактивация класса Pima устройства** *(ux_device_class_pima_deactivate)* |
| ![Значок отправки сведений о классе Pima устройства](./media/user-guide/usbx-events/image18.png)    | **Отправка сведений о классе Pima устройства** *(ux_device_class_pima_device_info_send)* |
| ![Значок получения события класса Pima устройства](./media/user-guide/usbx-events/image19.png)    | **Получение события класса Pima устройства** *(ux_device_class_pima_event_get)* |
| ![Значок набора событий класса Pima устройства](./media/user-guide/usbx-events/image20.png)    | **Набор событий класса Pima устройства** *(ux_device_class_pima_event_set)* |
| ![Значок добавления объекта в класс Pima устройства](./media/user-guide/usbx-events/image21.png)    | **Добавление объекта в класс Pima устройства** *(ux_device_class_pima_object_add)* |
| ![Значок получения данных объекта в классе Pima устройства](./media/user-guide/usbx-events/image22.png)    | **Получение данных объекта в классе Pima устройства** *(ux_device_class_pima_object_data_get)* |
| ![Значок отправки данных объекта класса Pima устройства](./media/user-guide/usbx-events/image23.png)    | **Отправка данных объекта класса Pima устройства** *(ux_device_class_pima_object_data_send)* |
| ![Значок удаления объекта из класса Pima устройства](./media/user-guide/usbx-events/image24.png)    | **Удаление объекта из класса Pima устройства** *(ux_device_class_pima_object_delete)* |
| ![Значок отправки дескрипторов объекта класса Pima устройства](./media/user-guide/usbx-events/image25.png)    | **Отправка дескрипторов объекта класса Pima устройства** *(ux_device_class_pima_object_handles_send)* |
| ![Значок получения сведений об объекте класса Pima устройства](./media/user-guide/usbx-events/image26.png)    | **Получение сведений об объекте класса Pima устройства** *(ux_device_class_pima_object_info_get)* |
| ![Значок отправки сведений об объекте класса Pima устройства](./media/user-guide/usbx-events/image27.png)    | **Отправка сведений об объекте класса Pima устройства** *(ux_device_class_pima_object_info_send)* |
| ![Значок отправки номера объекта класса Pima устройства](./media/user-guide/usbx-events/image28.png)    | **Номер объекта класса Pima устройства** *(ux_device_class_pima_objects_number_send)* |
| ![Значок получения частичных данных об объекте класса Pima устройства](./media/user-guide/usbx-events/image29.png)    | **Получение частичных данных об объекте класса Pima устройства** *(ux_device_class_pima_partial_object_data_get)* |
| ![Значок отправки ответа класса Pima устройства](./media/user-guide/usbx-events/image30.png)    | **Отправка ответа класса Pima устройства** *(ux_device_class_pima_response_send)*|
| ![Значок отправки идентификатора хранилища класса Pima устройства](./media/user-guide/usbx-events/image31.png)    | **Отправка идентификатора хранилища класса Pima устройства** *(ux_device_class_pima_storage_id_send)* |
| ![Значок отправки сведений о хранилище класса Pima устройства](./media/user-guide/usbx-events/image32.png)    | **Отправка сведений о хранилище класса Pima устройства** *(ux_device_class_pima_storage_info_send)* |
| ![Значок активации класса RNDIS устройства](./media/user-guide/usbx-events/image33.png)    | **Активация класса RNDIS устройства** *(ux_device_class_rndis_activate)* |
| ![Значок деактивации класса RNDIS устройства](./media/user-guide/usbx-events/image34.png)    | **Деактивация класса RNDIS устройства** *(ux_device_class_rndis_deactivate)* |
| ![Значок сообщения для проверки активности класса RNDIS устройства](./media/user-guide/usbx-events/image35.png)    | **Сообщение для проверки активности класса RNDIS устройства** *(ux_device_class_rndis_msg_keep_alive)* |
| ![Значок запроса сообщения для класса RNDIS устройства](./media/user-guide/usbx-events/image36.png)    | **Запрос сообщения для класса RNDIS устройства** *(ux_device_class_rndis_msg_query)* |
| ![Значок сброса сообщения для класса RNDIS устройства](./media/user-guide/usbx-events/image37.png)    | **Сброс сообщения для класса RNDIS устройства** *(ux_device_class_rndis_msg_reset)* |
| ![Значок набора сообщений для класса RNDIS устройства](./media/user-guide/usbx-events/image38.png)    | **Набор сообщений для класса RNDIS устройства** *(ux_device_class_rndis_msg_set)* |
| ![Значок получения пакета для класса RNDIS устройства](./media/user-guide/usbx-events/image39.png)    | **Получение пакета для класса RNDIS устройства** *(ux_device_class_rndis_packet_receive)* |
| ![Значок передачи пакетов для класса RNDIS устройства](./media/user-guide/usbx-events/image40.png)    | **Передача пакетов для класса RNDIS устройства** *(ux_device_class_rndis_packet_transmit)* |
| ![Значок активации хранилища класса устройства](./media/user-guide/usbx-events/image41.png)    | **Активация хранилища класса устройства** *(ux_device_class_storage_activate)* |
| ![Значок деактивации хранилища класса устройства](./media/user-guide/usbx-events/image42.png)    | **Деактивация хранилища класса устройства** *(ux_device_class_storage_deactivate)* |
| ![Значок форматирования хранилища класса устройства](./media/user-guide/usbx-events/image43.png)    | **Форматирование хранилища класса устройства** *(ux_device_class_storage_format)* |
| ![Значок запроса хранилища класса устройства](./media/user-guide/usbx-events/image44.png)    | **Запрос хранилища класса устройства** *(ux_device_class_storage_inquiry)* |
| ![Значок выбора режима хранения класса устройства](./media/user-guide/usbx-events/image45.png)    | **Выбор режима хранения класса устройства** *(ux_device_class_storage_mode_select)* |
| ![Значок контроля режима хранения в классе устройства](./media/user-guide/usbx-events/image46.png)    | **Контроль режима хранения в классе устройства** *(ux_device_class_storage_mode_sense)* |
| ![Значок запрета удаления носителей в хранилище класса устройства](./media/user-guide/usbx-events/image47.png)    | **Запрет удаления носителей в хранилище класса устройства** *(ux_device_class_storage_prevent_allow_media_removal)* |
| ![Значок считывания хранилища класса устройства](./media/user-guide/usbx-events/image48.png)    | **Считывание хранилища класса устройства** *(ux_device_class_storage_read)* |
| ![Значок считывания емкости хранилища класса устройства](./media/user-guide/usbx-events/image49.png)    | **Считывание емкости хранилища класса устройства** *(ux_device_class_storage_read_capacity)* |
| ![Значок емкости носителя для форматирования хранилища класса устройства](./media/user-guide/usbx-events/image50.png)    | **Емкость носителя для форматирования хранилища класса устройства** *(ux_device_class_storage_read_format_capacity)* |
| ![Значок считывания оглавления хранилища класса устройства](./media/user-guide/usbx-events/image51.png)    | **Считывание оглавления хранилища класса устройства** *(ux_device_class_storage_read)* |
| ![Значок запроса на контроль хранилища класса устройства](./media/user-guide/usbx-events/image52.png)    | **Запрос на контроль хранилища класса устройства** *(ux_device_class_storage_request_sense)* |
| ![Значок запуска и остановки хранилища класса устройств](./media/user-guide/usbx-events/image53.png)    | **Запуск и остановка хранилища класса устройства** *(ux_device_class_storage_start_stop)* |
| ![Значок готовности к тестированию хранилища класса устройства](./media/user-guide/usbx-events/image54.png)    | **Готовность к тестированию хранилища класса устройства** *(ux_device_class_storage_test_ready)* |
| ![Значок проверки хранилища класса устройства](./media/user-guide/usbx-events/image55.png)    | **Проверка хранилища класса устройства** *(ux_device_class_storage_verify)* |
| ![Значок записи хранилища класса устройства](./media/user-guide/usbx-events/image56.png)    | **Запись хранилища класса устройства** *(ux_device_class_storage_write)* |
| ![Значок получения дополнительных параметров стека устройства](./media/user-guide/usbx-events/image57.png)    | **Получение дополнительных параметров стека устройства** *(ux_device_stack_alternate_setting_get)* |
| ![Значок установки дополнительных параметров стека устройства](./media/user-guide/usbx-events/image58.png)    | **Установка дополнительных параметров стека устройства** *(ux_device_stack_alternate_setting_set)* |
| ![Значок регистрации класса в стеке устройства](./media/user-guide/usbx-events/image59.png)    | **Регистрация класса в стеке устройства** *(ux_device_stack_class_register)* |
| ![Значок возможности очистки стека устройства](./media/user-guide/usbx-events/image60.png)    | **Возможность очистки стека устройства** *(ux_device_stack_clear_feature)* |
| ![Значок получения конфигурации стека устройства](./media/user-guide/usbx-events/image61.png)    | **Получение конфигурации стека устройства** *(ux_device_stack_configuration_get)* |
| ![Значок набора конфигурации стека устройства](./media/user-guide/usbx-events/image62.png)    | **Набор конфигурации стека устройства** *(ux_device_stack_configuration_set)* |
| ![Значок подключения к стеку устройства](./media/user-guide/usbx-events/image63.png)    | **Подключение к стеку устройства** *(ux_device_stack_connect)* |
| ![Значок отправки дескриптора стека устройства](./media/user-guide/usbx-events/image64.png)    | **Отправка дескриптора стека устройства** *(ux_device_stack_descriptor_send)* |
| ![Значок отключения стека устройства](./media/user-guide/usbx-events/image65.png)    | **Отключение стека устройства** *(ux_device_stack_disconnect)* |
| ![Значок остановки конечной точки стека устройства](./media/user-guide/usbx-events/image66.png)    | **Остановка конечной точки стека устройства** *(ux_device_stack_endpoint_stall)* |
| ![Значок состояния получения стека устройства](./media/user-guide/usbx-events/image67.png)    | **Состояние получения стека устройства** *(ux_device_stack_get_status)* |
| ![Значок выхода узла стека устройства из спящего режима](./media/user-guide/usbx-events/image68.png)    | **Выход узла стека устройства из спящего режима** *(ux_device_stack_host_wakeup)* |
| ![Значок инициализации стека устройства](./media/user-guide/usbx-events/image69.png)    | **Инициализация стека устройства** *(ux_device_stack_initialize)* |
| ![Значок удаления интерфейса стека устройства](./media/user-guide/usbx-events/image70.png)    | **Удаление интерфейса стека устройства** *(ux_device_stack_interface_delete)* |
| ![Значок получения интерфейса стека устройства](./media/user-guide/usbx-events/image71.png)    | **Получение интерфейса стека устройства** *(ux_device_stack_interface_get)* |
| ![Значок установки набора интерфейсов стека устройства](./media/user-guide/usbx-events/image72.png)    | **Набор интерфейсов стека устройства** *(ux_device_stack_interface_set)* |
| ![Значок возможностей набора стеков устройства](./media/user-guide/usbx-events/image73.png)    | **Возможности набора стеков устройства** *(ux_device_stack_set_feature)* |
| ![Значок прерывания перемещения стека устройства](./media/user-guide/usbx-events/image74.png)    | **Прерывание перемещения стека устройства** *(ux_device_stack_transfer_abort)* |
| ![*Значок прерывания всех запросов на передачу стека устройства](./media/user-guide/usbx-events/image75.png)    | **Прерывание всех запросов на передачу стека устройства** *(ux_device_stack_transfer_all_request_abort)* |
| ![Значок запроса на передачу стека устройства](./media/user-guide/usbx-events/image76.png)    | **Запрос на передачу стека устройства** *(ux_device_stack_transfer_request)* |
| ![Значок активации класса Asix узла](./media/user-guide/usbx-events/image77.png)    | **Активация класса Asix узла** *(ux_host_class_asix_activate)* |
| ![Значок деактивации класса Asix узла](./media/user-guide/usbx-events/image78.png)    | **Деактивация класса Asix узла** *(ux_host_class_asix_deactivate)* |
| ![Значок уведомления о прерывании класса Asix узла](./media/user-guide/usbx-events/image79.png)    | **Уведомление о прерывании класса Asix узла** *(ux_host_class_asix_interrupt_notification)* |
| ![Значок считывания класса Asix узла](./media/user-guide/usbx-events/image80.png)    | **Считывание класса Asix узла** *(ux_host_class_asix_read)* |
| ![Значок записи класса Asix узла](./media/user-guide/usbx-events/image81.png)    | **Запись класса Asix узла** *(ux_host_class_asix_write)* |
| ![Значок активации звука для класса узла](./media/user-guide/usbx-events/image82.png)    | **Активация звука для класса узла** *(ux_host_class_audio_activate)* |
| ![Значок получения значения элемента управления звуком для класса узла](./media/user-guide/usbx-events/image83.png)    | **Получение значения элемента управления звуком для класса узла** *(ux_host_class_audio_control_value_get)* |
| ![Значок установки значений элемента управления звуком для класса узла](./media/user-guide/usbx-events/image84.png)    | **Установка значений элемента управления звуком для класса узла** *(ux_host_class_audio_control_value_set)* |
| ![Значок деактивации звука для класса узла](./media/user-guide/usbx-events/image85.png)    | **Деактивация звука для класса узла** *(ux_host_class_audio_deactivate)* |
| ![Значок считывания звуковых данных класса узла](./media/user-guide/usbx-events/image86.png)    | **Считывание звуковых данных класса узла** *(ux_host_class_audio_read)* |
| ![Значок получения выборки данных звукового потока для класса узла](./media/user-guide/usbx-events/image87.png)    | **Получение выборки данных звукового потока для класса узла** *(ux_host_class_audio_streaming_sampling_get)* |
| ![Значок задания данных для выборки звукового потока для класса узла](./media/user-guide/usbx-events/image88.png)    | **Задание данных для выборки звукового потока для класса узла** *(ux_host_class_audio_streaming_sampling_set)* |
| ![Значок записи звуковых данных класса узла](./media/user-guide/usbx-events/image89.png)    | **Запись звуковых данных класса узла** *(ux_host_class_audio_write)* |
| ![Значок активации класса Cdc Acm узла](./media/user-guide/usbx-events/image90.png)    | **Активация класса Cdc Acm узла** *(ux_host_class_cdc_acm_activate)* |
| ![Значок деактивации класса Cdc Acm узла](./media/user-guide/usbx-events/image91.png)    | **Деактивация класса Cdc Acm узла** *(ux_host_class_cdc_acm_deactivate)* |
| ![Значок прерывания в канале класса Cdc Acm Ioctl узла](./media/user-guide/usbx-events/image92.png)    | **Прерывание в канале класса Cdc Acm Ioctl узла** *(ux_host_class_cdc_acm_ioctl_abort_in_pipe)* |
| ![Значок прерывания вне канала класса Cdc Acm Ioctl узла](./media/user-guide/usbx-events/image93.png)    | **Прерывание вне канала класса Cdc Acm Ioctl узла** *(ux_host_class_cdc_acm_ioctl_abort_out_pipe)* |
| ![Значок получения состояния устройства класса Cdc Acm Ioctl узла](./media/user-guide/usbx-events/image94.png)    | **Получение состояния устройства класса Cdc Acm Ioctl узла** *(ux_host_class_cdc_acm_ioctl_get_device_status)* |
| ![Значок получения кодировки строки класса Cdc Acm Ioctl узла](./media/user-guide/usbx-events/image95.png)    | **Получение кодировки строки класса Cdc Acm Ioctl узла** *(ux_host_class_cdc_acm_ioctl_get_line_coding)* |
| ![Значок обратного вызова уведомления класса Cdc Acm Ioctl узла](./media/user-guide/usbx-events/image96.png)    | **Обратный вызов уведомления класса Cdc Acm Ioctl узла** *(ux_host_class_cdc_acm_ioctl_notification_callback)* |
| ![Значок остановки отправки класса Cdc Acm Ioctl узла](./media/user-guide/usbx-events/image97.png)    | **Остановка отправки класса Cdc Acm Ioctl узла** *(ux_host_class_cdc_acm_ioctl_send_break)* |
| ![Значок задания кодировки строки в классе Cdc Acm Ioctl узла](./media/user-guide/usbx-events/image98.png)    | **Задание кодировки строки в классе Cdc Acm Ioctl узла** *(ux_host_class_cdc_acm_ioctl_set_line_coding)* |
| ![Значок задания состояния кодировки строки в классе Cdc Acm Ioctl узла](./media/user-guide/usbx-events/image99.png)    | **Задание состояния кодировки строки в классе Cdc Acm Ioctl узла** *(ux_host_class_cdc_acm_ioctl_set_line_state)* |
| ![Значок считывания класса Cdc Acm узла](./media/user-guide/usbx-events/image100.png)    | **Считывание класса Cdc Acm узла** *(ux_host_class_cdc_acm_read)* |
| ![Значок запуска приема класса Cdc Acm узла](./media/user-guide/usbx-events/image101.png)    | **Запуск приема класса Cdc Acm узла** *(ux_host_class_cdc_acm_reception_start)* |
| ![Значок остановки приема класса Cdc Acm узла](./media/user-guide/usbx-events/image102.png)    | **Остановка приема класса Cdc Acm узла** *(ux_host_class_cdc_acm_reception_stop)* |
| ![Значок записи класса Cdc Acm узла](./media/user-guide/usbx-events/image103.png)    | **Запись класса Cdc Acm узла** *(ux_host_class_cdc_acm_write)* |
| ![Значок активации класса Dpump узла](./media/user-guide/usbx-events/image104.png)    | **Активация класса Dpump узла** *(ux_host_class_dpump_activate)* |
| ![Значок деактивации класса Dpump узла](./media/user-guide/usbx-events/image105.png)    | **Деактивация класса Dpump узла** *(ux_host_class_dpump_deactivate)* |
| ![Значок считывания класса Dpump узла](./media/user-guide/usbx-events/image106.png)    | **Считывание класса Dpump узла** *(ux_host_class_dpump_read)* |
| ![Значок записи класса Dpump узла](./media/user-guide/usbx-events/image107.png)    | **Запись класса Dpump узла** *(ux_host_class_dpump_write)* |
| ![Значок активации класса Hid узла](./media/user-guide/usbx-events/image108.png)    | **Активация класса Hid узла** *(ux_host_class_hid_activate)* |
| ![Значок регистрации клиента класса Hid узла](./media/user-guide/usbx-events/image109.png)    | **Регистрация клиента класса Hid узла** *(ux_host_class_hid_client_register)* |
| ![Значок деактивации класса Hid узла](./media/user-guide/usbx-events/image110.png)    | **Деактивация класса Hid узла** *(ux_host_class_hid_deactivate)* |
| ![Значок получения состояния бездействия класса Hid узла](./media/user-guide/usbx-events/image111.png)    | **Получение состояния бездействия класса Hid узла** *(ux_host_class_hid_idle_get)* |
| ![Значок установки состояния бездействия класса Hid узла](./media/user-guide/usbx-events/image112.png)    | **Установка состояния бездействия класса Hid узла** *(ux_host_class_hid_idle_set)* |
| ![Значок активации клавиатуры для класса Hid узла](./media/user-guide/usbx-events/image113.png)    | **Активация клавиатуры для класса Hid узла** *(ux_host_class_hid_keyboard_activate)* |
| ![Значок деактивации клавиатуры для класса Hid узла](./media/user-guide/usbx-events/image114.png)    | **Деактивация клавиатуры для класса Hid узла** *(ux_host_class_hid_keyboard_deactivate)* |
| ![Значок активации мыши для класса Hid узла](./media/user-guide/usbx-events/image115.png)    | **Активация мыши для класса Hid узла** *(ux_host_class_hid_keyboard_activate)* |
| ![Значок деактивации мыши для класса Hid узла](./media/user-guide/usbx-events/image116.png)    | **Деактивация мыши для класса Hid узла** *(ux_host_class_hid_mouse_deactivate)* |
| ![Значок активации удаленного управления для класса Hid узла](./media/user-guide/usbx-events/image117.png)    | **Активация удаленного управления для класса Hid узла** *(ux_host_class_hid_remote_control_activate)* |
| ![Значок деактивации удаленного управления для класса Hid узла](./media/user-guide/usbx-events/image118.png)    | **Деактивация удаленного управления для класса Hid узла** *(ux_host_class_hid_remote_control_deactivate)* |
| ![Значок получения отчета класса Hid узла](./media/user-guide/usbx-events/image119.png)    | **Получение отчета класса Hid узла** *(ux_host_class_hid_report_get)* |
| ![Значок набора отчетов класса Hid узла](./media/user-guide/usbx-events/image120.png)    | **Набор отчетов класса Hid узла** *(ux_host_class_hid_report_get)* |
| ![Значок активации концентратора класса узла](./media/user-guide/usbx-events/image121.png)    | **Активация концентратора класса узла** *(ux_host_class_hub_activate)* |
| ![Значок обнаружения изменений концентратора класса узла](./media/user-guide/usbx-events/image122.png)    | **Обнаружение изменений концентратора класса узла** *(ux_host_class_hub_change_detect)* |
| ![*Значок деактивации концентратора класса узла](./media/user-guide/usbx-events/image123.png)    | **Деактивация концентратора класса узла** *(ux_host_class_hub_deactivate)* |
| ![Значок процесса подключения для изменения порта концентратора класса узла](./media/user-guide/usbx-events/image124.png)    | **Процесс подключения для изменения порта концентратора класса узла** *(ux_host_class_hub_port_change_connection_process)* |
| ![Значок процесса включения для изменения порта концентратора класса узла](./media/user-guide/usbx-events/image125.png)    | **Процесс включения для изменения порта концентратора класса узла** *(ux_host_class_hub_port_change_enable_process)* |
| ![Значок завершения текущего процесса для изменения порта концентратора класса узла](./media/user-guide/usbx-events/image126.png)    | **Завершение текущего процесса для изменения порта концентратора класса узла** *(ux_host_class_hub_port_change_over_current_process)* |
| ![Значок процесса сброса для изменения порта концентратора класса узла](./media/user-guide/usbx-events/image127.png)    | **Процесс сброса для изменения порта концентратора класса узла** *(ux_host_class_hub_port_change_reset_process)* |
| ![Значок процесса приостановки для изменения порта концентратора класса узла](./media/user-guide/usbx-events/image128.png)    | **Процесс приостановки для изменения порта концентратора класса узла** *(ux_host_class_hub_port_change_suspend_process)* |
| ![Значок активации класса Pima узла](./media/user-guide/usbx-events/image129.png)    | **Активация класса Pima узла** *(ux_host_class_prima_activate)* |
| ![Значок деактивации класса Pima узла](./media/user-guide/usbx-events/image130.png)    | **Деактивация класса Pima узла** *(ux_host_class_pima_deactivate)* |
| ![Значок получения сведений об устройстве для класса Pima узла](./media/user-guide/usbx-events/image131.png)    | **Получение сведений об устройстве для класса Pima узла** *(ux_host_class_pima_device_info_get)* |
| ![Значок сброса устройства для класса Pima узла](./media/user-guide/usbx-events/image132.png)    | **Сброс устройства для класса Pima узла** *(ux_host_class_pima_device_reset)* |
| ![Значок уведомления класса Pima узла](./media/user-guide/usbx-events/image133.png)    | **Уведомление класса Pima узла** *(ux_host_class_pima_notification)* |
| ![Значок получения объектов номера класса Pima узла](./media/user-guide/usbx-events/image134.png)    | **Получение объектов номера класса Pima узла** *(ux_host_class_pima_num_objects_get)* |
| ![Значок закрытия объекта класса Pima узла](./media/user-guide/usbx-events/image135.png)    | **Закрытие объекта класса Pima узла** *(ux_host_class_pima_object_close)* |
| ![Значок копирования объекта класса Pima узла](./media/user-guide/usbx-events/image136.png)    | **Копирование объекта класса Pimа узла** *(ux_host_class_pima_object_copy)* |
| ![Значок удаления объекта из класса Pima узла](./media/user-guide/usbx-events/image137.png)    | **Удаление объекта из класса Pima узла** *(ux_host_class_pima_object_delete)* |
| ![Значок получения объекта класса Pima узла](./media/user-guide/usbx-events/image138.png)    | **Получение объекта класса Pima узла** *(ux_host_class_pima_object_get)* |
| ![Значок получения сведений об объекте класса Pima узла](./media/user-guide/usbx-events/image139.png)    | **Получение сведений об объекте класса Pima узла** *(ux_host_class_pima_object_info_get)* |
| ![Значок отправки сведений об объекте класса Pima узла](./media/user-guide/usbx-events/image140.png)    | **Отправка сведений об объекте класса Pima узла** *(ux_host_class_pima_object_info_send)* |
| ![Значок перемещения объекта класса Pima узла](./media/user-guide/usbx-events/image141.png)    | **Перемещение объекта класса Pima узла** *(ux_host_class_pima_object_move)* |
| ![Значок отправки объекта класса Pima узла](./media/user-guide/usbx-events/image142.png)    | **Отправка объекта класса Pima узла** *(ux_host_class_pima_object_send)* |
| ![Значок прерывания перемещения объекта класса Pima узла](./media/user-guide/usbx-events/image143.png)    | **Прерывание перемещения объекта класса Pima узла** *(ux_host_class_object_transfer_abort)* |
| ![Значок считывания класса Pima узла](./media/user-guide/usbx-events/image144.png)    | **Считывание класса Pima узла** *(ux_host_class_pima_read)* |
| ![Значок отмены запроса класса Pima узла](./media/user-guide/usbx-events/image145.png)    | **Отмена запроса класса Pima узла** *(ux_host_class_pima_request_cancel)* |
| ![Значок завершения сеанса класса Pima узла](./media/user-guide/usbx-events/image146.png)    | **Завершение сеанса класса Pima узла** *(ux_host_class_pima_session_close)* |
| ![Значок начала сеанса класса Pima узла](./media/user-guide/usbx-events/image147.png)    | **Начало сеанса класса Pima узла** *(ux_host_class_pima_session_open)* |
| ![Значок получения идентификаторов хранилища класса Pima узла](./media/user-guide/usbx-events/image148.png)    | **Получение идентификаторов хранилища класса Pima узла** *(ux_host_class_pima_storage_ids_get)* |
| ![Значок получения сведений о хранилище класса Pima узла](./media/user-guide/usbx-events/image149.png)    | **Получение сведений о хранилище класса Pima узла** *(ux_host_class_pima_storage_info_get)* |
| ![Значок получения бегунка класса Pima узла](./media/user-guide/usbx-events/image150.png)    | **Получение бегунка класса Pima узла** *(ux_host_class_pima_thumb_get)* |
| ![Значок записи класса Pima узла](./media/user-guide/usbx-events/image151.png)    | **Запись класса Pima узла** *(ux_host_class_pima_write)* |
| ![Значок активации принтера класса узла](./media/user-guide/usbx-events/image152.png)    | **Активация принтера класса узла** *(ux_host_class_printer_activate)* |
| ![Значок деактивации принтера класса узла](./media/user-guide/usbx-events/image153.png)    | **Деактивация принтера класса узла** *(ux_host_class_printer_deactivate)* |
| ![Значок получения имени принтера класса узла](./media/user-guide/usbx-events/image154.png)    | **Получение имени принтера класса узла** *(ux_host_class_printer_name_get)* |
| ![Значок считывания принтера класса узла](./media/user-guide/usbx-events/image155.png)    |  **Считывание принтера класса узла** *(ux_host_class_printer_read)* |
| ![Значок частичного сброса принтера класса узла](./media/user-guide/usbx-events/image156.png)    | **Частичный сброс принтера класса узла** *(ux_host_class_printer_soft_reset)* |
| ![Значок получения состояния принтера класса узла](./media/user-guide/usbx-events/image157.png)    | **Получение состояния принтера класса узла** *(ux_host_class_printer_status_get)* |
| ![Значок записи принтера класса узла](./media/user-guide/usbx-events/image158.png)    | **Запись принтера класса узла** *(ux_host_class_printer_write)* |
| ![Значок активации класса Prolific узла](./media/user-guide/usbx-events/image159.png)    | **Активация класса Prolific узла** *(ux_host_class_prolific_activate)* |
| ![Значок деактивации класса Prolific узла](./media/user-guide/usbx-events/image160.png)    | **Деактивация класса Prolific узла** *(ux_host_class_prolific_deactivate)* |
| ![Значок прерывания в канале класса Prolific Ioctl узла](./media/user-guide/usbx-events/image161.png)    | **Прерывание в канале класса Prolific Ioctl узла** *(ux_host_class_prolific_ioctl_abort_in_pipe)* |
| ![Значок прерывания вне канала класса Prolific Ioctl узла](./media/user-guide/usbx-events/image162.png)    | **Прерывание вне канала класса Prolific Ioctl узла** *(ux_host_class_prolific_ioctl_abort_out_pipe)* |
| ![Значок получения состояния устройства в классе Prolific Ioctl узла](./media/user-guide/usbx-events/image163.png)    | **Получение состояния устройства в классе Prolific Ioctl узла** *(ux_host_class_prolific_ioctl_get_device_status)* |
| ![Значок получения кодировки строки в классе Prolific Ioctl узла](./media/user-guide/usbx-events/image164.png)    | **Получение кодировки строки в классе Prolific Ioctl узла** *(ux_host_class_prolific_ioctl_get_line_coding)* |
| ![Значок очистки класса Prolific Ioctl узла](./media/user-guide/usbx-events/image165.png)    | **Очистка класса Prolific Ioctl узла** *(ux_host_class_prolific_ioctl_purge)* |
| ![Значок изменения состояния отчета о классе Prolific Ioctl узла](./media/user-guide/usbx-events/image166.png)    | **Изменение состояния отчета о классе Prolific Ioctl узла** *(ux_host_class_prolific_ioctl_report_device_status_change)* |
| ![Значок остановки отправки в классе Prolific Ioctl узла](./media/user-guide/usbx-events/image167.png)    | **Остановка отправки в классе Prolific Ioctl узла** *(ux_host_class_prolific_ioctl_send_break)* |
| ![Значок задания кодировки строки в классе Prolific Ioctl узла](./media/user-guide/usbx-events/image168.png)    | **Задание кодировки строки в классе Prolific Ioctl узла** *(ux_host_class_prolific_ioctl_set_line_coding)* |
| ![Значок задания состояния строк в классе Prolific Ioctl узла](./media/user-guide/usbx-events/image169.png)    | **Задание состояния строк в классе Prolific Ioctl узла** *(ux_host_class_prolific_ioctl_set_line_state)* |
| ![Значок считывания класса Prolific узла](./media/user-guide/usbx-events/image170.png)    | **Считывание класса Prolific узла** *(ux_host_class_prolific_read)* |
| ![Значок запуска приема в классе Prolific узла](./media/user-guide/usbx-events/image171.png)    | **Запуск приема в классе Prolific узла** *(ux_host_class_prolific_reception_start)* |
| ![Значок остановки приема в классе Prolific узла](./media/user-guide/usbx-events/image172.png)    | **Остановка приема в классе Prolific узла** *(ux_host_class_prolific_reception_stop)* |
| ![Значок записи класса Prolific узла](./media/user-guide/usbx-events/image173.png)    | **Запись класса Prolific узла** *(ux_host_class_prolific_write)* |
| ![Значок активации хранилища класса узла](./media/user-guide/usbx-events/image174.png)    | **Активация хранилища класса узла** *(ux_device_class_storage_activate)* |
| ![Значок деактивации хранилища класса узла](./media/user-guide/usbx-events/image175.png)    | **Деактивация хранилища класса узла** *(ux_host_class_storage_deactivate)* |
| ![Значок получения емкости носителя для хранилища класса узла](./media/user-guide/usbx-events/image176.png)    | **Получение емкости носителя для хранилища класса узла** *(ux_host_class_storage_media_capacity_get)* |
| ![Значок получения формата емкости для носителя в хранилище класса узла](./media/user-guide/usbx-events/image177.png)    | **Получение формата емкости для носителя в хранилище класса узла** *(ux_host_class_storage_media_format_capacity_get)* |
| ![Значок подключения носителя хранилища класса узла](./media/user-guide/usbx-events/image178.png)    | **Подключение носителя хранилища класса узла** (ux_host_class_storage_media_mount)* |
| ![Значок открытия носителя хранилища класса узла](./media/user-guide/usbx-events/image179.png)    | **Открытие носителя хранилища класса узла** *(ux_host_class_storage_media_open)* |
| ![Значок считывания носителя хранилища класса узла](./media/user-guide/usbx-events/image180.png)    | **Считывание носителя хранилища класса узла** *(ux_host_class_storage_media_read)* |
| ![Значок записи носителя для хранилища класса узла](./media/user-guide/usbx-events/image181.png)    | **Запись носителя для хранилища класса узла** *(ux_host_class_storage_media_write)* |
| ![Значок запроса на контроль хранилища класса узла](./media/user-guide/usbx-events/image182.png)    | **Запрос на контроль хранилища класса узла** *(ux_device_class_storage_request_sense)* |
| ![Значок запуска и остановки хранилища класса узла](./media/user-guide/usbx-events/image183.png)    | **Запуск и остановка хранилища класса узла** *(ux_device_class_storage_start_stop)* |
| ![Значок теста готовности единиц хранения для класса узла](./media/user-guide/usbx-events/image184.png)    | **Тест готовности единиц хранения для класса узла** *(ux_host_class_storage_activate)* |
| ![Значок создания экземпляра класса стека узла](./media/user-guide/usbx-events/image185.png)    | **Создание экземпляра класса стека узла** *(ux_host_stack_class_instance_create)* |
| ![Значок уничтожения экземпляра класса стека узла](./media/user-guide/usbx-events/image186.png)    | **Уничтожение экземпляра класса стека узла** *(ux_host_stack_class_instance_destroy)* |
| ![Значок удаления конфигурации стека узла](./media/user-guide/usbx-events/image187.png)    | **Удаление конфигурации стека узла** *(ux_host_stack_configuration_delete)* |
| ![Значок перечисления конфигураций стека узла](./media/user-guide/usbx-events/image188.png)    | **Перечисление конфигураций стека узла** *(ux_host_stack_configuration_enumerate)* |
| ![Значок создания экземпляра конфигурации стека узла](./media/user-guide/usbx-events/image189.png)    | **Создание экземпляра конфигурации стека узла** *(ux_host_stack_configuration_instance_create)* |
| ![Значок удаления экземпляра конфигурации стека узла](./media/user-guide/usbx-events/image190.png)    | **Удаление экземпляра конфигурации стека узла** *(ux_host_stack_configuration_instance_delete)* |
| ![Значок набора конфигураций стека узла](./media/user-guide/usbx-events/image191.png)    | **Набор конфигураций стека узла** *(ux_host_stack_configuration_set)* |
| ![Значок набора адресов устройства стека узла](./media/user-guide/usbx-events/image192.png)    | **Набор адресов устройств стека узла** *(ux_host_stack_device_set)* |
| ![Значок получения конфигурации устройства стека узла](./media/user-guide/usbx-events/image193.png)    | **Получение конфигурации устройства стека узла** *(ux_host_stack_device_configuration_get)* |
| ![Значок выбора конфигурации устройства стека узла](./media/user-guide/usbx-events/image194.png)    | **Выбор конфигурации устройства стека узла** *(ux_host_stack_device_configuration_select)* |
| ![Значок считывания дескриптора устройства стека узла](./media/user-guide/usbx-events/image195.png)    | **Считывание дескриптора устройства стека узла** *(ux_host_stack_device_descriptor_read)* |
| ![Значок получения устройства стека узла](./media/user-guide/usbx-events/image196.png)    | **Получение устройства стека узла** (ux_host_stack_device_get) |
| ![Значок удаления устройства стека узла](./media/user-guide/usbx-events/image197.png)    | **Удаление устройства стека узла** (ux_host_stack_device_get) |
| ![Значок освобождения ресурса устройства стека узла](./media/user-guide/usbx-events/image198.png)    | **Освобождение ресурса устройства стека узла** (ux_host_stack_device_resource_free) |
| ![Значок создания экземпляра конечной точки стека узла](./media/user-guide/usbx-events/image199.png)    | **Создание экземпляра конечной точки стека узла** (ux_host_stack_endpoint_instance_create) |
| ![Значок удаления экземпляра конечной точки стека узла](./media/user-guide/usbx-events/image200.png)    | **Удаление экземпляра конечной точки стека узла** (ux_host_stack_endpoint_instance_delete) |
| ![Значок сброса конечной точки стека узла](./media/user-guide/usbx-events/image201.png)    | **Сброс конечной точки стека узла** (ux_host_stack_endpoint_reset) |
| ![Значок прерывания перемещения конечной точки стека узла](./media/user-guide/usbx-events/image202.png)    | **Прерывание перемещения конечной точки стека узла** (ux_host_stack_endpoint_transfer_abort) |
| ![Значок регистрации хост-контроллера в стеке узла](./media/user-guide/usbx-events/image203.png)    | **Регистрация хост-контроллера в стеке узла** *(ux_host_stack_hcd_register)* |
| ![Значок инициализации стека узла](./media/user-guide/usbx-events/image204.png)    | **Инициализация стека узла** *(ux_host_stack_initialize)* |
| ![Значок получения конечной точки интерфейса стека узла](./media/user-guide/usbx-events/image205.png)    | **Получение конечной точки интерфейса стека узла** *(ux_host_stack_interface_endpoint_get)* |
| ![Значок создания экземпляра интерфейса стека узла](./media/user-guide/usbx-events/image206.png)    | **Создание экземпляра интерфейса стека узла** *(ux_host_stack_interface_instance_create)* |
| ![Значок удаления экземпляра интерфейса стека узла](./media/user-guide/usbx-events/image207.png)    | **Удаление экземпляра интерфейса стека узла** *(ux_host_stack_interface_endpoint_get)* |
| ![Значок набора интерфейсов стека узла](./media/user-guide/usbx-events/image208.png)    | **Набор интерфейсов стека узла** *(ux_host_stack_interface_set)* |
| ![Значок выбора параметров интерфейса стека узла](./media/user-guide/usbx-events/image209.png)    | **Выбор параметров интерфейса стека узла** *(ux_host_stack_interface_setting_select)* |
| ![Значок создания конфигурации стека узла](./media/user-guide/usbx-events/image210.png)    | **Создание конфигурации стека узла** *(ux_host_stack_new_configuration_create)* |
| ![Значок создания устройства в стеке узла](./media/user-guide/usbx-events/image211.png)    | **Создание устройства в стеке узла** *(ux_host_stack_new_device_create)* |
| ![Значок создания новой конечной точки стека узла](./media/user-guide/usbx-events/image212.png)    | **Создание новой конечной точки стека узла** *(ux_host_stack_new_endpoint_create)* |
| ![Значок процесса изменения корневого концентратора стека узла](./media/user-guide/usbx-events/image213.png)    | **Процесс изменения корневого концентратора стека узла** *(ux_host_stack_rh_change_process)* |
| ![Значок извлечения устройства корневого концентратора стека узла](./media/user-guide/usbx-events/image214.png)    | **Извлечение устройства корневого концентратора стека узла** *(ux_host_stack_rh_device_extraction)* |
| ![Значок вставки устройства корневого концентратора стека узла](./media/user-guide/usbx-events/image215.png)    | **Вставка устройства корневого концентратора стека узла** *(ux_host_stack_rh_device_insertion)* |
| ![Значок запроса на передачу стека узла](./media/user-guide/usbx-events/image216.png)    | **Запрос на передачу стека узла** *(ux_device_stack_transfer_request)* |
| ![Значок прерывания запроса на передачу стека узла](./media/user-guide/usbx-events/image217.png)    | **Прерывание запроса на передачу стека узла** *(ux_host_stack_transfer_request_abort)* |
| ![Значок ошибки USBX](./media/user-guide/usbx-events/image218.png)    | **Ошибка USBX** *(ux_error)* |

## <a name="event-descriptions"></a>Описания событий

На следующих страницах описаны события трассировки USBX.

### <a name="device-class-cdc-activate"></a>Активация класса CDC устройства 

#### <a name="ux_device_class_cdc_activate"></a>ux_device_class_cdc_activate

**Значок** ![Значок активации класса CDC устройства](./media/user-guide/usbx-events/image1.png)

**Описание**

Это событие представляет собой активацию класса Cdc устройства USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-cdc-deactivate"></a>Деактивация класса CDC устройства 

#### <a name="ux_device_class_cdc_deactivate"></a>ux_device_class_cdc_deactivate

**Значок** ![Значок деактивации класса CDC устройства](./media/user-guide/usbx-events/image2.png)

**Описание**

Это событие представляет собой деактивацию класса Cdc устройства USBX.

Поля сведений 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-cdc-read"></a>Считывание класса CDC устройства 

#### <a name="ux_device_class_cdc_read"></a>ux_device_class_cdc_read

**Значок** ![Значок считывания класса CDC устройства](./media/user-guide/usbx-events/image3.png)

**Описание**

Это событие представляет собой считывание класса Cdc устройства USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Указатель данных.
- Поле сведений 3. Запрошенная длина.
- Поле сведений 4. Не используется.

### <a name="device-class-cdc-write"></a>Запись класса CDC устройства 

#### <a name="ux_device_class_cdc_write"></a>ux_device_class_cdc_write

**Значок** ![Значок записи класса CDC устройства](./media/user-guide/usbx-events/image4.png)

**Описание**

Это событие представляет собой запись класса Cdc устройства USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Указатель данных.
- Поле сведений 3. Запрошенная длина.
- Поле сведений 4. Не используется.

### <a name="device-class-dpump-activate"></a>Активация класса Dpump устройства 

#### <a name="ux_device_class_dpump_activate"></a>ux_device_class_dpump_activate

**Значок** ![Значок активации класса Dpump устройства](./media/user-guide/usbx-events/image5.png)

**Описание**

Это событие представляет собой активацию класса Dpump устройства USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-dpump-deactivate"></a>Деактивация класса Dpump устройства 

#### <a name="ux_device_class_dpump_deactivate"></a>ux_device_class_dpump_deactivate

**Значок** ![Значок деактивации класса Dpump устройства](./media/user-guide/usbx-events/image6.png)

**Описание**

Это событие представляет собой деактивацию класса Dpump устройства USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-dpump-read"></a>Считывание класса Dpump устройства 

#### <a name="ux_device_class_dpump_read"></a>ux_device_class_dpump_read

**Значок** ![Значок считывания класса Dpump устройства](./media/user-guide/usbx-events/image7.png)

**Описание**

Это событие представляет собой считывание класса Dpump устройства USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Буфер.
- Поле сведений 3. Запрошенная длина.
- Поле сведений 4. Не используется.

### <a name="device-class-dpump-write"></a>Запись класса Dpump устройства 

#### <a name="ux_device_class_dpump_write"></a>ux_device_class_dpump_write

**Значок** ![Значок записи класса Dpump устройства](./media/user-guide/usbx-events/image8.png)

**Описание**

Это событие представляет собой запись класса Dpump устройства USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Указатель данных.
- Поле сведений 3. Запрошенная длина.
- Поле сведений 4. Не используется.

### <a name="device-class-hid-activate"></a>Активация класса Hid устройства 

#### <a name="ux_device_class_hid_activate"></a>ux_device_class_hid_activate

**Значок** ![Значок активации класса Hid устройства](./media/user-guide/usbx-events/image9.png)

**Описание**

Это событие представляет собой активацию класса Hid устройства USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-hid-deactivate"></a>Деактивация класса Hid устройства 

#### <a name="ux_device_class_hid_deactivate"></a>ux_device_class_hid_deactivate

**Значок** ![Значок деактивации класса Hid устройства](./media/user-guide/usbx-events/image10.png)

**Описание**

Это событие представляет собой деактивацию класса Hid устройства USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-hid-descriptor-send"></a>Отправка дескриптора класса Hid устройства 

#### <a name="ux_device_class_hid_descritpor_send"></a>ux_device_class_hid_descritpor_send

**Значок** ![Значок отправки дескриптора класса Hid устройства](./media/user-guide/usbx-events/image11.png)

**Описание**

Это событие представляет собой отправку дескриптора класса Hid устройства USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Тип дескриптора.
- Поле сведений 3. Индекс запроса.
- Поле сведений 4. Не используется.

### <a name="device-class-hid-event-get"></a>Получение события класса Hid устройства 

#### <a name="ux_device_class_hid_event_get"></a>ux_device_class_hid_event_get

**Значок** ![Значок получения события класса Hid устройства](./media/user-guide/usbx-events/image12.png)

**Описание**

Это событие представляет собой получение события класса Hid устройства USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-hid-event-set"></a>Установка события класса Hid устройства 

#### <a name="ux_device_class_hid_event_set"></a>ux_device_class_hid_event_set

**Значок** ![Значок установки события класса Hid устройства](./media/user-guide/usbx-events/image13.png)

**Описание**

Это событие представляет собой установку события класса Hid устройства USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-hid-report-get"></a>Получение отчета класса Hid устройства 

#### <a name="ux_device_class_hid_report_get"></a>ux_device_class_hid_report_get

**Значок** ![Значок получения отчета класса Hid устройства](./media/user-guide/usbx-events/image14.png)

**Описание**

Это событие представляет собой получение отчета класса Hid устройства USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Тип дескриптора.
- Поле сведений 3. Индекс запроса.
- Поле сведений 4. Не используется.

### <a name="device-class-hid-report-set"></a>Установка отчета класса Hid устройства 

#### <a name="ux_device_class_hid_report_set"></a>ux_device_class_hid_report_set

**Значок** ![Значок установки отчета класса Hid устройства](./media/user-guide/usbx-events/image15.png)

**Описание**

Это событие представляет собой установку отчета класса Hid устройства USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Тип дескриптора.
- Поле сведений 3. Индекс запроса.
- Поле сведений 4. Не используется.

### <a name="device-class-pima-activate"></a>Активация класса Pima устройства

#### <a name="ux_device_class_pima_activate"></a>ux_device_class_pima_activate

**Значок** ![Значок активации класса Pima устройства](./media/user-guide/usbx-events/image16.png)

**Описание**

Это событие представляет собой активацию класса Pima устройства USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-pima-deactivate"></a>Деактивация класса Pima устройства 

#### <a name="ux_device_class_pima_deactivate"></a>ux_device_class_pima_deactivate

**Значок** ![Значок деактивации класса Pima устройства](./media/user-guide/usbx-events/image17.png)

**Описание**

Это событие представляет собой деактивацию класса Pima устройства USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-pima-device-info-send"></a>Отправка сведений об устройстве класса Pima устройства 

#### <a name="ux_device_class_pima_device_info_send"></a>ux_device_class_pima_device_info_send

**Значок** ![Значок отправки сведений об устройстве класса Pima устройства](./media/user-guide/usbx-events/image18.png)

**Описание**

Это событие представляет собой отправку сведений об устройстве класса Pima устройства USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.

### <a name="device-class-pima-event-get"></a>Получение события класса Pima устройства 

#### <a name="ux_device_class_pima_event_get"></a>ux_device_class_pima_event_get

**Значок** ![Значок получения события класса Pima устройства](./media/user-guide/usbx-events/image19.png)

**Описание**

Это событие представляет собой получение события класса Pima устройства USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Событие Pima.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-pima-event-set"></a>Установка события класса Pima устройства 

#### <a name="ux_device_class_pima_event_set"></a>ux_device_class_pima_event_set

**Значок** ![Значок установки события класса Pima устройства](./media/user-guide/usbx-events/image20.png)

**Описание**

Это событие представляет собой установку события класса Pima устройства USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Событие Pima.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-pima-object-add"></a>Добавление объекта в класс Pima устройства 

#### <a name="ux_device_class_pima_object_add"></a>ux_device_class_pima_object_add

**Значок** ![Значок добавления объекта в класс Pima устройства](./media/user-guide/usbx-events/image21.png)

**Описание**

Это событие представляет собой добавление объекта класса Pima устройства USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Дескриптор объекта.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-pima-object-data-get"></a>Получение данных объекта в классе Pima устройства 

#### <a name="ux_device_class_pima_object_data_get"></a>ux_device_class_pima_object_data_get

**Значок** ![Значок получения данных объекта класса Pima устройства](./media/user-guide/usbx-events/image22.png)

**Описание**

Это событие представляет собой получение данных объекта класса Pima устройства USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Дескриптор объекта.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-pima-object-data-send"></a>Отправка данных объекта класса Pima устройства 

#### <a name="ux_device_class_pima_object_data_send"></a>ux_device_class_pima_object_data_send

**Значок** ![Значок отправки данных объекта класса Pima устройства](./media/user-guide/usbx-events/image23.png)

**Описание**

Это событие представляет собой отправку данных объекта класса Pima устройства USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Дескриптор объекта.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-pima-object-delete"></a>Удаление объекта класса Pima устройства 

#### <a name="ux_device_class_pima_object_delete"></a>ux_device_class_pima_object_delete

**Значок** ![Значок удаления объекта класса Pima устройства](./media/user-guide/usbx-events/image24.png)

**Описание**

Это событие представляет собой удаление объекта класса Pima устройства USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Дескриптор объекта.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-pima-object-handles-send"></a>Отправка дескрипторов объекта класса Pima устройства 

#### <a name="ux_device_class_pima_object_handles_send"></a>ux_device_class_pima_object_handles_send

**Значок** ![Значок отправки дескрипторов объекта класса Pima устройства](./media/user-guide/usbx-events/image25.png)

**Описание**

Это событие представляет собой отправку дескрипторов объекта класса Pima устройства USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Идентификатор хранилища.
- Поле сведений 3. Код формата объекта.
- Поле сведений 4. Связь между объектами.

### <a name="device-class-pima-object-info-get"></a>Получение сведений об объекте класса Pima устройства 

#### <a name="ux_device_class_pima_object_info_send"></a>ux_device_class_pima_object_info_send

**Значок** ![Значок получения сведений об объекте класса Pima устройства](./media/user-guide/usbx-events/image26.png)

**Описание**

Это событие представляет собой получение сведений об объекте класса Pima устройства USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Дескриптор объекта.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-pima-object-info-send"></a>Отправка сведений об объекте класса Pima устройства 

#### <a name="ux_device_class_pima_object_info_send"></a>ux_device_class_pima_object_info_send

**Значок** ![Значок отправки сведений об объекте класса Pima устройства](./media/user-guide/usbx-events/image27.png)

**Описание**

Это событие представляет собой отправку сведений об объекте класса Pima устройства USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-pima-objects-number-send"></a>Отправка номера объектов класса Pima устройства 

#### <a name="ux_device_class_pima_object_number_send"></a>ux_device_class_pima_object_number_send

**Значок** ![Значок отправки номера объектов класса Pima устройства](./media/user-guide/usbx-events/image28.png)

**Описание**

Это событие представляет собой отправку номера объекта класса Pima устройства USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Идентификатор хранилища.
- Поле сведений 3. Код формата объекта.
- Поле сведений 4. Связь объекта.

### <a name="device-class-pima-partial-object-data-get"></a>Получение частичных данных объекта класса Pima устройства

#### <a name="ux_device_class_pima_partial_object_data_get"></a>ux_device_class_pima_partial_object_data_get

**Значок** ![Значок получения частичных данных объекта класса Pima устройства](./media/user-guide/usbx-events/image29.png)

**Описание**

Это событие представляет собой получение частичных данных объекта класса Pima устройства USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Дескриптор объекта.
- Поле сведений 3. Запрос на смещение выполнен.
- Поле сведений 4. Запрос на получение сведений о длине выполнен.

### <a name="device-class-pima-response-send"></a>Отправка отклика класса Pima устройства 

#### <a name="ux_device_class_pima_response_send"></a>ux_device_class_pima_response_send

**Значок** ![Значок отправки отклика класса Pima устройства](./media/user-guide/usbx-events/image30.png)

**Описание**

Это событие представляет собой отправку отклика класса Pima устройства USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Код отклика.
- Поле сведений 3. Числовой параметр.
- Поле сведений 4. Параметр 1 Pima.

### <a name="device-class-pima-storage-id-send"></a>Отправка идентификатора хранилища класса Pima устройства 

#### <a name="ux_device_class_pima_storage_id_send"></a>ux_device_class_pima_storage_id_send

**Значок** ![Значок отправки идентификатора хранилища класса Pima устройства](./media/user-guide/usbx-events/image31.png)

**Описание**

Это событие представляет собой отправку идентификатора хранилища класса Pima устройства USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-pima-storage-info-send"></a>Отправка сведений о хранилище класса Pima устройства 

#### <a name="ux_device_class_pima_storage_info_send"></a>ux_device_class_pima_storage_info_send

**Значок** ![Значок отправки сведений о хранилище класса Pima устройства](./media/user-guide/usbx-events/image32.png)

**Описание**

Это событие представляет собой отправку сведений о хранилище класса Pima устройства USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-rndis-activate"></a>Активация класса Rndis устройства 

#### <a name="ux_device_class_rndis_activate"></a>ux_device_class_rndis_activate

**Значок** ![Значок активации класса Rndis устройства](./media/user-guide/usbx-events/image33.png)

**Описание**

Это событие представляет собой активацию класса Rndis устройства USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-rndis-deactivate"></a>Деактивация класса Rndis устройства 

#### <a name="ux_device_class_rndis_deactivate"></a>ux_device_class_rndis_deactivate

**Значок** ![Значок деактивации класса Rndis устройства](./media/user-guide/usbx-events/image34.png)

**Описание**

Это событие представляет собой деактивацию класса Rndis устройства USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-rndis-message-keep-alive"></a>Проверка активности сообщений класса Rndis устройства 

#### <a name="ux_device_class_rndis_msg_keep_alive"></a>uux_device_class_rndis_msg_keep_alive

**Значок** ![Значок проверки активности сообщений класса Rndis устройства](./media/user-guide/usbx-events/image35.png)

**Описание**

Это событие представляет собой проверку активности сообщений класса Rndis устройства USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-rndis-message-query"></a>Запрос на сообщение класса Rndis устройства 

#### <a name="ux_device_class_rndis_msg_keep_query"></a>ux_device_class_rndis_msg_keep_query

**Значок** ![Значок запроса на сообщение класса Rndis устройства](./media/user-guide/usbx-events/image36.png)

**Описание**

Это событие представляет собой запрос на сообщение класса Rndis устройства USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Rndis OID.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-rndis-message-reset"></a>Сброс сообщения класса Rndis устройства 

#### <a name="ux_device_class_rndis_msg_reset"></a>ux_device_class_rndis_msg_reset

**Значок** ![Значок сброса сообщения класса Rndis устройства](./media/user-guide/usbx-events/image37.png)

**Описание**

Это событие представляет собой сброс сообщения класса Rndis устройства USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.

### <a name="device-class-rndis-message-set"></a>Набор сообщений класса Rndis устройства 

#### <a name="ux_device_class_rndis_msg_set"></a>ux_device_class_rndis_msg_set

**Значок** ![Значок набора сообщений класса Rndis устройства](./media/user-guide/usbx-events/image38.png)

**Описание**

Это событие представляет собой событие набора сообщений класса Rndis устройства USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Rndis OID.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-rndis-packet-receive"></a>Получения пакета класса Rndis устройства 

#### <a name="ux_device_class_rndis_packet_receive"></a>ux_device_class_rndis_packet_receive

**Значок** ![Значок получения пакета класса Rndis устройства](./media/user-guide/usbx-events/image39.png)

**Описание**

Это событие представляет собой получение пакета класса Rndis устройства USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-rndis-packet-transmit"></a>Передача пакета класса Rndis устройства 

#### <a name="ux_device_class_rndis_packet_transmit"></a>ux_device_class_rndis_packet_transmit

**Значок** ![Значок передачи пакета класса Rndis устройства](./media/user-guide/usbx-events/image40.png)

**Описание**

Это событие представляет собой передачу пакета класса Rndis устройства USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-storage-activate"></a>Активация хранилища класса устройства 

#### <a name="ux_device_class_storage_activate"></a>ux_device_class_storage_activate

**Значок** ![Значок активации хранилища класса устройства](./media/user-guide/usbx-events/image41.png)

**Описание**

Это событие представляет собой активацию хранилища класса устройства USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-storage-deactivate"></a>Деактивация хранилища класса устройства 

#### <a name="ux_device_class_storage_deactivate"></a>ux_device_class_storage_deactivate

**Значок** ![Значок деактивации хранилища класса устройства](./media/user-guide/usbx-events/image42.png)

**Описание**

Это событие представляет собой деактивацию хранилища класса устройства USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-storage-format"></a>Формат хранилища класса устройства 

#### <a name="ux_device_class_storage_format"></a>ux_device_class_storage_format

**Значок** ![Значок формата хранилища класса устройства](./media/user-guide/usbx-events/image43.png)

**Описание**

Это событие представляет собой событие формата хранилища класса устройства USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Номер логического устройства (LUN).
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-storage-inquiry"></a>Запрос хранилища класса устройства 

#### <a name="ux_device_class_storage_inquiry"></a>ux_device_class_storage_inquiry

**Значок** ![Значок запроса хранилища класса устройства](./media/user-guide/usbx-events/image44.png)

**Описание**

Это событие представляет собой запрос хранилища класса устройства USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Номер логического устройства (LUN).
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-storage-mode-select"></a>Выбор режима хранения класса устройства

#### <a name="ux_device_class_storage_mode_select"></a>ux_device_class_storage_mode_select

**Значок** ![Значок выбора режима хранения класса устройства](./media/user-guide/usbx-events/image45.png)

**Описание**

Это событие представляет собой выбор режима хранения класса устройства USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Номер логического устройства (LUN).
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-storage-mode-sense"></a>Контроль режима хранения класса устройства 

#### <a name="ux_device_class_storage_mode_sense"></a>ux_device_class_storage_mode_sense

**Значок** ![Значок контроля режима хранения класса устройства](./media/user-guide/usbx-events/image46.png)

**Описание**

Это событие представляет собой контроль режима хранения класса устройства USBX.

Поля сведений 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Номер логического устройства (LUN).
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-storage-prevent-allow-media-removal"></a>Запрет на удаление носителей в хранилище класса устройства 

#### <a name="ux_device_class_storage_prevent_allow_media_removal"></a>ux_device_class_storage_prevent_allow_media_removal

**Значок** ![Значок запрета на удаление носителей в хранилище класса устройства](./media/user-guide/usbx-events/image47.png)

**Описание**

Это событие представляет собой запрет на удаление носителей в хранилище класса устройства USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Номер логического устройства (LUN).
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-storage-read"></a>Считывание хранилища класса устройства 

#### <a name="ux_device_class_storage_read"></a>ux_device_class_storage_read

**Значок** ![Значок считывания хранилища класса устройства](./media/user-guide/usbx-events/image48.png)

**Описание**

Это событие представляет собой считывание хранилища класса устройства USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Номер логического устройства (LUN).
- Поле сведений 3. Сектор.
- Поле сведений 4. Число секторов.

### <a name="device-class-storage-read-capacity"></a>Считывание емкости хранилища класса устройства 

#### <a name="ux_device_class_storage_read_capacity"></a>ux_device_class_storage_read_capacity

**Значок** ![Значок считывания емкости хранилища класса устройства](./media/user-guide/usbx-events/image49.png)

**Описание**

Это событие представляет собой считывание емкости хранилища класса устройства USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Номер логического устройства (LUN).
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-storage-read-format-capacity"></a>Считывание формата емкости хранилища класса устройства 

#### <a name="ux_device_class_storage_read_format_capacity"></a>ux_device_class_storage_read_format_capacity

**Значок** ![Значок считывания формата емкости хранилища класса устройства](./media/user-guide/usbx-events/image50.png)

**Описание**

Это событие представляет собой считывание формата емкости хранилища класса устройства USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Номер логического устройства (LUN).
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-storage-read-toc"></a>Считывание оглавления хранилища класса устройства 

#### <a name="ux_device_class_storage_read_toc"></a>ux_device_class_storage_read_toc

**Значок** ![Значок считывания оглавления хранилища класса устройства](./media/user-guide/usbx-events/image51.png)

**Описание**

Это событие представляет собой считывание оглавления хранилища класса устройства USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Номер логического устройства (LUN).
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-storage-request-sense"></a>Запрос на контроль хранилища класса устройства 

#### <a name="ux_device_class_storage_request_sense"></a>ux_device_class_storage_request_sense

**Значок** ![Значок запроса на контроль хранилища класса устройства](./media/user-guide/usbx-events/image52.png)

**Описание**

Это событие представляет собой запрос на контроль хранилища класса устройства USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Номер логического устройства (LUN).
- Поле сведений 3. Ключ контроля.
- Поле сведений 4. Код.

### <a name="device-class-storage-start-stop"></a>Запуск и остановка хранилища класса устройства 

#### <a name="ux_device_class_storage_start_stop"></a>ux_device_class_storage_start_stop

**Значок** ![Значок запуска и остановки хранилища класса устройства](./media/user-guide/usbx-events/image53.png)

**Описание**

Это событие представляет собой запуск и остановку хранилища класса устройства USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Номер логического устройства (LUN).
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-storage-test-ready"></a>Готовность к тестированию хранилища класса устройства 

#### <a name="ux_device_class_storage_test_ready"></a>ux_device_class_storage_test_ready

**Значок** ![Значок готовности к тестированию хранилища класса устройства](./media/user-guide/usbx-events/image54.png)

**Описание**

Это событие представляет собой готовность к тестированию хранилища класса устройства USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Номер логического устройства (LUN).
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-storage-verify"></a>Проверка хранилища класса устройства 

#### <a name="ux_device_class_storage_verify"></a>ux_device_class_storage_verify

**Значок** ![Значок проверки хранилища класса устройства](./media/user-guide/usbx-events/image55.png)

**Описание**

Это событие представляет собой проверку хранилища класса устройства USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Номер логического устройства (LUN).
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-class-storage-write"></a>Запись хранилища класса устройства 

#### <a name="ux_device_class_storage_write"></a>ux_device_class_storage_write

**Значок** ![Значок записи хранилища класса устройства](./media/user-guide/usbx-events/image56.png)

**Описание**

Это событие представляет собой запись хранилища класса устройства USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Номер логического устройства (LUN).
- Поле сведений 3. Сектор.
- Поле сведений 4. Число секторов.

### <a name="device-stack-alternate-setting-get"></a>Получение дополнительных параметров стека устройства 

#### <a name="ux_device_class_alternate_setting_get"></a>ux_device_class_alternate_setting_get

**Значок** ![Значок получения дополнительных параметров стека устройства](./media/user-guide/usbx-events/image57.png)

**Описание**

Это событие представляет собой получение дополнительных параметров стека устройства USBX.

**Поля сведений**

- Поле сведений 1. Значение интерфейса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-stack-alternate-setting-set"></a>Установка дополнительных параметров стека устройства 

#### <a name="ux_device_class_alternate_setting_set"></a>ux_device_class_alternate_setting_set

**Значок** ![Значок установки дополнительных параметров стека устройства](./media/user-guide/usbx-events/image58.png)

**Описание**

Это событие представляет собой установку дополнительных параметров стека устройства USBX.

**Поля сведений**
- Поле сведений 1. Значение интерфейса.
- Поле сведений 2. Значение дополнительного параметра.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-stack-class-register"></a>Регистрация класса стека устройства 

#### <a name="ux_device_stack_class_register"></a>ux_device_stack_class_register

**Значок** ![Значок регистрации класса стека устройства](./media/user-guide/usbx-events/image59.png)

**Описание**

Это событие представляет собой регистрацию класса стека устройства USBX.

**Поля сведений**

- Поле сведений 1. Имя класса.
- Поле сведений 2. Номер интерфейса.
- Поле сведений 3. Параметр.
- Поле сведений 4. Не используется.

### <a name="device-stack-clear-feature"></a>Возможность очистки стека устройства 

#### <a name="ux_device_stack_clear_feature"></a>ux_device_stack_clear_feature

**Значок** ![Значок возможности очистки стека устройства](./media/user-guide/usbx-events/image60.png)

**Описание**

Это событие представляет собой возможность очистки стека устройства USBX.

**Поля сведений**

- Поле сведений 1. Тип запроса.
- Поле сведений 2. Значение запроса. Поле сведений 3. Индекс запроса.
- Поле сведений 4. Не используется.

### <a name="device-stack-configuration-get"></a>Получение конфигурации стека устройства 

#### <a name="ux_device_stack_configuration_get-t"></a>ux_device_stack_configuration_get t

**Значок** ![Значок получения конфигурации стека устройства](./media/user-guide/usbx-events/image61.png)

**Описание**

Это событие представляет собой получение конфигурации стека устройства USBX.

**Поля сведений** 

- Поле сведений 1. Значение конфигурации.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-stack-configuration-set"></a>Установка конфигурации стека устройства 

#### <a name="ux_device_stack_configuration_set"></a>ux_device_stack_configuration_set

**Значок** ![Значок установки конфигурации стека устройства](./media/user-guide/usbx-events/image62.png)

**Описание**

Это событие представляет собой установку конфигурации стека устройства USBX.

**Поля сведений** 

- Поле сведений 1. Значение конфигурации.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-stack-connect"></a>Подключение к стеку устройства 

#### <a name="ux_device_stack_connect"></a>ux_device_stack_connect

**Значок** ![Значок подключения к стеку устройства](./media/user-guide/usbx-events/image63.png)

**Описание**

Это событие представляет собой отправку дескриптора стека устройства USBX.

**Поля сведений**

- Поле сведений 1. Не используется.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-stack-descriptor-send"></a>Отправка дескриптора стека устройства 

#### <a name="ux_device_stack_descriptor_send"></a>ux_device_stack_descriptor_send

**Значок** ![Значок отправки дескриптора стека устройства](./media/user-guide/usbx-events/image64.png)

**Описание**

Это событие представляет собой отправку дескриптора стека устройства USBX.

**Поля сведений**

- Поле сведений 1. Тип дескриптора.
- Поле сведений 2. Индекс запроса.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-stack-disconnect"></a>Отключение стека устройства 

#### <a name="ux_device_stack_disconnect"></a>ux_device_stack_disconnect

**Значок** ![Значок отключения стека устройства](./media/user-guide/usbx-events/image65.png)

**Описание**

Это событие представляет собой отключение стека устройства USBX.

**Поля сведений**

- Поле сведений 1. Устройство.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-stack-endpoint-stall"></a>Остановка конечной точки стека устройства 

#### <a name="ux_device_stack_endpoint_stall"></a>ux_device_stack_endpoint_stall

**Значок** ![Значок остановки конечной точки стека устройства](./media/user-guide/usbx-events/image66.png)

**Описание**

Это событие представляет собой остановку конечной точки стека устройства USBX.

**Поля сведений** 

- Поле сведений 1. Конечная точка.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-stack-get-status"></a>Получение состояния стека устройства 

#### <a name="ux_device_stack_get_status"></a>ux_device_stack_get_status

**Значок** ![Значок получения состояния стека устройства](./media/user-guide/usbx-events/image67.png)

**Описание**

Это событие представляет собой получение состояния стека устройства USBX.

**Поля сведений**

- Поле сведений 1. Не используется.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-stack-host-wakeup"></a>Выход узла стека устройства из спящего режима 

#### <a name="ux_device_stack_host_wakeup"></a>ux_device_stack_host_wakeup

**Значок** ![Значок выхода узла стека устройства из спящего режима](./media/user-guide/usbx-events/image68.png)

**Описание**

Это событие представляет собой выход узла стека устройства USBX из спящего режима.

**Поля сведений** 

- Поле сведений 1. Не используется.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-stack-initialize"></a>Инициализация стека устройства 

#### <a name="ux_device_stack_initialize"></a>ux_device_stack_initialize

**Значок** ![Значок инициализации стека устройства](./media/user-guide/usbx-events/image69.png)

**Описание**

Это событие представляет собой инициализацию стека устройства USBX.

**Поля сведений** 

- Поле сведений 1. Не используется.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-stack-interface-delete"></a>Удаление интерфейса стека устройства 

#### <a name="ux_device_stack_interface_delete"></a>ux_device_stack_interface_delete

**Значок** ![Значок удаления интерфейса стека устройства](./media/user-guide/usbx-events/image70.png)

**Описание**

Это событие представляет собой удаление интерфейса стека устройства USBX.

**Поля сведений**

- Поле сведений 1. Интерфейс.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-stack-interface-get"></a>Получение интерфейса стека устройства 

#### <a name="ux_device_stack_interface_get"></a>ux_device_stack_interface_get

**Значок** ![Значок получения интерфейса стека устройства](./media/user-guide/usbx-events/image71.png)

**Описание**

Это событие представляет собой получение интерфейса стека устройства USBX.

**Поля сведений** 

- Поле сведений 1. Значение интерфейса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-stack-interface-set"></a>Установка интерфейса стека устройства 

#### <a name="ux_device_stack_interface_set"></a>ux_device_stack_interface_set

**Значок** ![Значок установки интерфейса стека устройства](./media/user-guide/usbx-events/image72.png)

**Описание**

Это событие представляет собой установку интерфейса стека устройства USBX.

**Поля сведений** 

- Поле сведений 1. Значение запроса. Поле сведений 2. Индекс запроса.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-stack-set-feature"></a>Возможности набора стеков устройства 

#### <a name="ux_device_stack_set_feature"></a>ux_device_stack_set_feature

**Значок** ![Значок возможностей набора стеков устройства](./media/user-guide/usbx-events/image73.png)

**Описание**

Это событие представляет собой событие возможностей набора стеков устройства USBX.

**Поля сведений** 

- Поле сведений 1. Значение запроса. Поле сведений 2. Индекс запроса.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-stack-transfer-abort"></a>Прерывание перемещения стека устройства 

#### <a name="ux_device_stack_transfer_abort"></a>ux_device_stack_transfer_abort

**Значок** ![Значок прерывания перемещения стека устройства](./media/user-guide/usbx-events/image74.png)

**Описание**

Это событие представляет собой прерывание перемещения стека устройства USBX.

**Поля сведений** 

- Поле сведений 1. Запрос на передачу.
- Поле сведений 2. Код завершения.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-stack-transfer-all-request-abort"></a>Прерывание всех запросов на передачу стека устройства 

#### <a name="ux_device_stack_transfer_all_request_abort"></a>ux_device_stack_transfer_all_request_abort

**Значок** ![Значок прерывания всех запросов на передачу стека устройства](./media/user-guide/usbx-events/image75.png)

**Описание**

Это событие представляет собой прерывание всех запросов на передачу стека устройства USBX.

**Поля сведений** 

- Поле сведений 1. Конечная точка.
- Поле сведений 2. Код завершения.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="device-stack-transfer-request"></a>Запрос на передачу стека устройства 

#### <a name="ux_device_stack_transfer_request"></a>ux_device_stack_transfer_request

**Значок** ![Значок запроса на передачу стека устройства](./media/user-guide/usbx-events/image76.png)

**Описание**

Это событие представляет собой запрос на передачу стека устройства USBX.

**Поля сведений**

- Поле сведений 1. Запрос на передачу.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-asix-activate"></a>Активация класса Asix узла 

#### <a name="ux_host_class_asix_activate"></a>ux_host_class_asix_activate

**Значок** ![Значок активации класса Asix узла](./media/user-guide/usbx-events/image77.png)

**Описание**

Это событие представляет собой активацию класса Asix узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-asix-deactivate"></a>Деактивация класса Asix узла 

#### <a name="ux_host_class_asix_deactivate"></a>ux_host_class_asix_deactivate

**Значок** ![Значок деактивации класса Asix узла](./media/user-guide/usbx-events/image78.png)

**Описание**

Это событие представляет собой деактивацию класса Asix узла USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-asix-interrupt-notification"></a>Уведомление о прерывании класса Asix узла 

#### <a name="ux_host_class_asix_interrupt_notification"></a>ux_host_class_asix_interrupt_notification

**Значок** ![Значок уведомления о прерывании класса Asix узла](./media/user-guide/usbx-events/image79.png)

**Описание**

Это событие представляет собой уведомление о прерывании класса Asix узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-asix-read"></a>Считывание класса Asix узла 

#### <a name="ux_host_class_asix_read"></a>ux_host_class_asix_read

**Значок** ![Значок считывания класса Asix узла](./media/user-guide/usbx-events/image80.png)

**Описание**

Это событие представляет собой считывание класса Asix узла USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Указатель данных.
- Поле сведений 3. Запрошенная длина.
- Поле сведений 4. Не используется.

### <a name="host-class-asix-write"></a>Запись класса Asix узла 

#### <a name="ux_host_class_asix_write"></a>ux_host_class_asix_write

**Значок** ![Значок записи класса Asix узла](./media/user-guide/usbx-events/image81.png)

**Описание**

Это событие представляет собой запись класса Asix узла USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Указатель данных.
- Поле сведений 3. Запрошенная длина.
- Поле сведений 4. Не используется.

### <a name="host-class-audio-activate"></a>Активация звука для класса узла 

#### <a name="ux_host_class_audio_activate"></a>ux_host_class_audio_activate

**Значок** ![Значок активации звука класса узла](./media/user-guide/usbx-events/image82.png)

**Описание**

Это событие представляет собой активацию звука класса узла USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-audio-control-value-get"></a>Получение значения элемента управления звуком для класса узла 

#### <a name="ux_host_class_audio_control_value_get"></a>ux_host_class_audio_control_value_get

**Значок** ![Значок получения значения элемента управления звуком для класса узла](./media/user-guide/usbx-events/image83.png)

**Описание**

Это событие представляет собой получение значения элемента управления звуком для класса узла USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-audio-control-value-set"></a>Установка значений элемента управления звуком для класса узла 

#### <a name="ux_host_class_audio_control_value_set"></a>ux_host_class_audio_control_value_set

**Значок** ![Значок установки значений элемента управления звуком для класса узла](./media/user-guide/usbx-events/image84.png)

**Описание**

Это событие представляет собой событие отложенной обработки внутреннего драйвера ввода-вывода в NetX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Элемент управления звуком.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-audio-deactivate"></a>Деактивация звука класса узла 

#### <a name="ux_host_class_audio_deactivate"></a>ux_host_class_audio_deactivate

**Значок** ![Значок деактивации звука класса узла](./media/user-guide/usbx-events/image85.png)

**Описание**

Это событие представляет собой деактивацию звука класса узла USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-audio-read"></a>Считывание звуковых данных класса узла 

#### <a name="ux_host_class_audio_read"></a>ux_host_class_audio_read

**Значок** ![Значок считывания звуковых данных класса узла](./media/user-guide/usbx-events/image86.png)

**Описание**

Это событие представляет собой считывание звуковых данных класса узла USBX.

- Поля сведений 
- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Указатель данных.
- Поле сведений 3. Запрошенная длина.
- Поле сведений 4. Не используется.

### <a name="host-class-audio-streaming-sampling-get"></a>Получение данных для выборки звукового потока для класса узла 

#### <a name="ux_host_class_audio_streaming_sampling_get"></a>ux_host_class_audio_streaming_sampling_get

**Значок** ![Значок получения данных для выборки звукового потока для класса узла](./media/user-guide/usbx-events/image87.png)

**Описание**

Это событие представляет собой получение данных для выборки звукового потока для класса узла USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-audio-streaming-sampling-set"></a>Задание данных для выборки звукового потока для класса узла 

#### <a name="ux_host_class_audio_streaming_sampling_set"></a>ux_host_class_audio_streaming_sampling_set

**Значок** ![Значок задания данных для выборки звукового потока для класса узла](./media/user-guide/usbx-events/image88.png)

**Описание**

Это событие представляет собой задание данных для выборки звукового потока для класса узла USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Выборка звукового потока.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-audio-write"></a>Запись звука класса узла 

#### <a name="ux_host_class_audio_write"></a>ux_host_class_audio_write

**Значок** ![Значок записи звука класса узла](./media/user-guide/usbx-events/image89.png)

**Описание**

Это событие представляет собой запись звука класса узла USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Указатель данных.
- Поле сведений 3. Запрошенная длина.
- Поле сведений 4. Не используется.

### <a name="host-class-cdc-acm-activate"></a>Активация класса Cdc Acm узла 

#### <a name="ux_host_class_cdc_acm_activate"></a>ux_host_class_cdc_acm_activate

**Значок** ![Значок активации класса Cdc Acm узла](./media/user-guide/usbx-events/image90.png)

**Описание**

Это событие представляет собой активацию класса Cdc Acm узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-cdc-acm-deactivate"></a>Деактивация класса Cdc Acm узла 

#### <a name="ux_host_class_cdc_acm_deactivate"></a>ux_host_class_cdc_acm_deactivate

**Значок** ![Значок деактивации класса Cdc Acm узла](./media/user-guide/usbx-events/image91.png)

**Описание**

Это событие представляет собой деактивацию класса Cdc Acm узла USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-cdc-acm-ioctl-abort-in-pipe"></a>Прерывание в канале класса Cdc Acm Ioctl узла 

#### <a name="ux_host_class_cdc_acm_ioctl_abort_in_pipe"></a>ux_host_class_cdc_acm_ioctl_abort_in_pipe

**Значок** ![Значок прерывания в канале класса Cdc Acm Ioctl узла](./media/user-guide/usbx-events/image92.png)

**Описание**

Это событие представляет собой прерывание в канале класса Cdc Acm Ioctl узла USBX.

Поля сведений 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Конечная точка.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-cdc-acm-ioctl-abort-out-pipe"></a>Прерывание вне канала класса Cdc Acm Ioctl узла 

#### <a name="ux_host_class_cdc_acm_ioct_abort_out_pipe"></a>ux_host_class_cdc_acm_ioct_abort_out_pipe

**Значок** [Значок прерывания вне канала класса Cdc Acm Ioctl узла](./media/user-guide/usbx-events/image93.png)

**Описание**

Это событие представляет собой прерывание вне канала класса Cdc Acm Ioctl узла USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Конечная точка.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-cdc-acm-ioctl-get-device-status"></a>Получение состояния устройства класса Cdc Acm Ioctl узла 

#### <a name="ux_host_class_cdc_acm_ioctl_get_device_status"></a>ux_host_class_cdc_acm_ioctl_get_device_status

**Значок** ![Значок получения состояния устройства класса Cdc Acm Ioctl узла](./media/user-guide/usbx-events/image94.png)

**Описание**

Это событие представляет собой получение состояния устройства класса Cdc Acm Ioctl узла USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Состояние устройства.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-cdc-acm-ioctl-get-line-coding"></a>Получение кодировки строки в классе Cdc Acm Ioctl узла 

#### <a name="ux_host_class_cdc_acm_ioctl_get_line_coding"></a>ux_host_class_cdc_acm_ioctl_get_line_coding

**Значок** ![Значок получения кодировки строки в классе Cdc Acm Ioctl узла](./media/user-guide/usbx-events/image95.png)

**Описание**

Это событие представляет собой получение кодировки строки в классе Cdc Acm Ioctl узла USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Параметр.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-cdc-acm-ioctl-notification-callback"></a>Обратный вызов уведомления класса Cdc Acm Ioctl узла

#### <a name="ux_host_class_cdc_acm_ioctl_notification_callback"></a>ux_host_class_cdc_acm_ioctl_notification_callback

**Значок** ![Значок обратного вызова уведомления класса Cdc Acm Ioctl узла](./media/user-guide/usbx-events/image96.png)

**Описание**

Это событие представляет собой обратный вызов уведомления класса Cdc Acm Ioctl узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Параметр.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-cdc-acm-ioctl-send-break"></a>Остановка отправки класса Cdc Acm Ioctl узла 

#### <a name="ux_host_class_cdc_acm_ioctl_send_break"></a>ux_host_class_cdc_acm_ioctl_send_break

**Значок** ![Значок остановки отправки класса Cdc Acm Ioctl узла](./media/user-guide/usbx-events/image97.png)

**Описание**

Это событие представляет собой остановку отправки класса Cdc Acm Ioctl узла USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Параметр.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-cdc-acm-ioctl-set-line-coding"></a>Задание кодировки строки в классе Cdc Acm Ioctl узла 

#### <a name="ux_host_class_cdc_acm_ioctl_set_line_coding"></a>ux_host_class_cdc_acm_ioctl_set_line_coding

**Значок** ![Значок задания кодировки строки в классе Cdc Acm Ioctl узла](./media/user-guide/usbx-events/image97.png) значок](./media/user-guide/usbx-events/image98.png)

**Описание**

Это событие представляет собой задание кодировки строки в классе Cdc Acm Ioctl узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Параметр.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-cdc-acm-ioctl-set-line-state"></a>Задание состояния кодировки строки в классе Cdc Acm Ioctl узла 

#### <a name="ux_host_class_cdc_acm_ioctl_set_line_state"></a>ux_host_class_cdc_acm_ioctl_set_line_state

**Значок** ![Значок задания состояния кодировки строки в классе Cdc Acm Ioctl узла](./media/user-guide/usbx-events/image99.png)

**Описание**

Это событие представляет собой задание состояния кодировки строки в классе Cdc Acm Ioctl узла USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Параметр.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-cdc-acm-read"></a>Считывание класса Cdc Acm узла 

#### <a name="ux_host_class_cdc_acm_read"></a>ux_host_class_cdc_acm_read

**Значок** ![Значок считывания класса Cdc Acm узла](./media/user-guide/usbx-events/image100.png)

**Описание**

Это событие представляет собой считывание класса Cdc Acm узла USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Указатель данных.
- Поле сведений 3. Запрошенная длина.
- Поле сведений 4. Не используется.

### <a name="host-class-cdc-acm-reception-start"></a>Запуск приема класса Cdc Acm узла 

#### <a name="ux_host_class_cdc_acm_reception_start"></a>ux_host_class_cdc_acm_reception_start

**Значок** ![Значок запуска приема класса Cdc Acm узла](./media/user-guide/usbx-events/image101.png)

**Описание**

Это событие представляет собой запуск приема узла класса Cdc Acm узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-cdc-acm-reception-stop"></a>Остановка приема класса Cdc Acm узла 

#### <a name="ux_host_class_cdc_acm_reception_stop"></a>ux_host_class_cdc_acm_reception_stop

**Значок** ![Значок остановки приема класса Cdc Acm узла](./media/user-guide/usbx-events/image102.png)

**Описание**

Это событие представляет собой остановку приема класса Cdc Acm узла USBX.

**Поля сведений**

- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-cdc-acm-write"></a>Запись класса Cdc Acm узла 

#### <a name="ux_host_class_acm_write"></a>ux_host_class_acm_write

**Значок** ![Значок записи класса Cdc Acm узла](./media/user-guide/usbx-events/image103.png)

**Описание**

Это событие представляет собой запись класса Cdc Acm узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Указатель данных.
- Поле сведений 3. Запрошенная длина.
- Поле сведений 4. Не используется.

### <a name="host-class-dpump-activate"></a>Активация класса Dpump узла 

#### <a name="ux_host_class_dpump_activate"></a>ux_host_class_dpump_activate

**Значок** ![Значок активации класса Dpump узла](./media/user-guide/usbx-events/image104.png)

**Описание**

Это событие представляет собой активацию класса Dpump узла USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-dpump-deactivate"></a>Деактивация класса Dpump узла 

#### <a name="ux_host_class_dpump_deactivate"></a>ux_host_class_dpump_deactivate

**Значок** ![Значок деактивации класса Dpump узла](./media/user-guide/usbx-events/image105.png)

**Описание**

Это событие представляет собой деактивацию класса Dpump узла USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-dpump-read"></a>Считывание класса Dpump узла 

#### <a name="ux_host_class_dpump_read"></a>ux_host_class_dpump_read

**Значок** ![Значок считывания класса Dpump узла](./media/user-guide/usbx-events/image106.png)

**Описание**

Это событие представляет собой считывание класса Dpump узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Указатель данных.
- Поле сведений 3. Запрошенная длина.
- Поле сведений 4. Не используется.

### <a name="host-class-dpump-write"></a>Запись класса Dpump узла 

#### <a name="ux_host_class_dpump_write"></a>ux_host_class_dpump_write

**Значок** ![Значок записи класса Dpump узла](./media/user-guide/usbx-events/image107.png)

**Описание**

Это событие представляет собой запись класса Dpump узла USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Указатель данных.
- Поле сведений 3. Запрошенная длина.
- Поле сведений 4. Не используется.

### <a name="host-class-hid-activate"></a>Активация класса Hid узла 

#### <a name="ux_host_class_hid_activate"></a>ux_host_class_hid_activate

**Значок** ![Значок активации класса Hid узла](./media/user-guide/usbx-events/image108.png)

**Описание**

Это событие представляет собой активацию класса Hid узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-hid-client-register"></a>Регистрация клиента класса Hid узла 

#### <a name="ux_host_class_hid_client_register"></a>ux_host_class_hid_client_register

**Значок** ![Значок регистрации клиента класса Hid узла](./media/user-guide/usbx-events/image109.png)

**Описание**

Это событие представляет собой регистрацию клиента класса Hid узла USBX.

**Поля сведений** 

- Поле сведений 1. Имя клиента Hid.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-hid-deactivate"></a>Деактивация класса Hid узла 

#### <a name="ux_host_class_hid_deactivate"></a>ux_host_class_hid_deactivate

**Значок** ![Значок деактивации класса Hid узла](./media/user-guide/usbx-events/image110.png)

**Описание**

Это событие представляет собой деактивацию класса Hid узла USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-hid-idle-get"></a>Получение состояния бездействия класса Hid узла 

#### <a name="ux_host_class_hid_idle_get"></a>ux_host_class_hid_idle_get

**Значок** ![Значок получения состояния бездействия класса Hid узла](./media/user-guide/usbx-events/image111.png)

**Описание**

Это событие представляет собой получение состояния бездействия класса Hid узла USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-hid-idle-set"></a>Задание состояния бездействия класса Hid узла 

#### <a name="ux_host_class_hid_idle_set"></a>ux_host_class_hid_idle_set

**Значок** ![Значок задания состояния бездействия класса Hid узла](./media/user-guide/usbx-events/image112.png)

**Описание**

Это событие представляет собой задание состояния бездействия класса Hid узла USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-hid-keyboard-activate"></a>Активация клавиатуры для класса Hid узла 

#### <a name="ux_host_class_hid_keyboard_activate"></a>ux_host_class_hid_keyboard_activate

**Значок** ![Значок активации клавиатуры для класса Hid узла](./media/user-guide/usbx-events/image113.png)

**Описание**

Это событие представляет собой активацию клавиатуры для класса Hid узла USBX.

**Поля сведений**
<p>Поле сведений 1. Экземпляр класса.
<p>Поле сведений 2. Экземпляр клиента Hid.
<p>Поле сведений 3. Не используется.
<p>Поле сведений 4. Не используется.

### <a name="host-class-hid-keyboard-deactivate"></a>Деактивация клавиатуры для класса Hid узла 

#### <a name="ux_host_class_hid_keyboard_deactivate"></a>ux_host_class_hid_keyboard_deactivate

**Значок** ![Значок деактивации клавиатуры для класса Hid узла](./media/user-guide/usbx-events/image114.png)

**Описание**

Это событие представляет собой деактивацию клавиатуры для класса Hid узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Экземпляр клиента Hid.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-hid-mouse-activate"></a>Активация мыши для класса Hid узла 

#### <a name="ux_host_class_hid_mouse_activate"></a>ux_host_class_hid_mouse_activate

**Значок** ![Значок активации мыши для класса Hid узла](./media/user-guide/usbx-events/image115.png)

**Описание**

Это событие представляет собой активацию мыши для класса Hid узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Экземпляр клиента Hid.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-hid-mouse-deactivate"></a>Деактивация мыши для класса Hid узла 

#### <a name="ux_host_class_hid_mouse_deactivate"></a>ux_host_class_hid_mouse_deactivate

**Значок** ![Значок деактивации мыши для класса Hid узла](./media/user-guide/usbx-events/image116.png)

**Описание**

- Это событие представляет собой деактивацию мыши для класса Hid узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Экземпляр клиента Hid.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-hid-remote-control-activate"></a>Активация удаленного управления для класса Hid узла 

#### <a name="ux_host_class_hid_remote_control_activate"></a>ux_host_class_hid_remote_control_activate

**Значок** ![Значок активации удаленного управления для класса Hid узла](./media/user-guide/usbx-events/image117.png)

**Описание**

Это событие представляет собой активацию удаленного управления для класса Hid узла USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Экземпляр клиента Hid.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-hid-remote-control-deactivate"></a>Деактивация удаленного управления для класса Hid узла 

#### <a name="ux_host_class_hid_remote_control_deactivate"></a>ux_host_class_hid_remote_control_deactivate

**Значок** ![Значок деактивации удаленного управления для класса Hid узла](./media/user-guide/usbx-events/image118.png)

**Описание**

Это событие представляет собой деактивацию удаленного управления для класса Hid узла USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Экземпляр клиента Hid.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-hid-report-get"></a>Получение отчета класса Hid узла 

#### <a name="ux_host_class_hid_report_get"></a>ux_host_class_hid_report_get

**Значок** ![Значок получения отчета класса Hid узла](./media/user-guide/usbx-events/image119.png)

**Описание**

Это событие представляет собой получение отчета класса Hid узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Отчет клиента.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-hid-report-set"></a>Набор отчетов класса Hid узла 

#### <a name="ux_host_class_hid_report_set"></a>ux_host_class_hid_report_set

**Значок** ![Значок набора отчетов класса Hid узла](./media/user-guide/usbx-events/image120.png)

**Описание**. Это событие представляет собой событие набора отчетов класса Hid узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Отчет клиента.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-hub-activate"></a>Активация концентратора класса узла 

#### <a name="ux_host_class_hub_activate"></a>ux_host_class_hub_activate

**Значок** ![Значок активации концентратора класса узла](./media/user-guide/usbx-events/image121.png)

**Описание**

Это событие представляет собой активацию концентратора класса узла USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-hub-change-detect"></a>Обнаружение изменений концентратора в классе узла 

#### <a name="ux_host_class_hub_change_detect"></a>ux_host_class_hub_change_detect

**Значок** ![Значок обнаружения изменений концентратора в классе узла](./media/user-guide/usbx-events/image122.png)

**Описание**

Это событие представляет собой обнаружение изменений концентратора в классе узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-hub-deactivate"></a>Деактивация концентратора класса узла 

#### <a name="ux_host_class_hub_deactivate"></a>x_host_class_hub_deactivate

**Значок** ![Значок деактивации концентратора класса узла](./media/user-guide/usbx-events/image123.png)

**Описание**

Это событие представляет собой деактивацию концентратора класса узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-hub-port-change-connection-process"></a>Процесс подключения для изменения порта концентратора класса узла 

#### <a name="ux_host_class_hub_change_connection_process"></a>ux_host_class_hub_change_connection_process

**Значок** ![Значок процесса подключения для изменения порта концентратора класса узла](./media/user-guide/usbx-events/image124.png)

**Описание**

Это событие представляет собой процесс подключения для изменения порта концентратора класса узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Порт.
- Поле сведений 3. Состояние порта.
- Поле сведений 4. Не используется.

### <a name="host-class-hub-port-change-enable-process"></a>Процесс включения для изменения порта концентратора класса узла 

#### <a name="ux_host_class_hub_port_change_enable_process"></a>ux_host_class_hub_port_change_enable_process

**Значок** ![Значок процесса включения для изменения порта концентратора класса узла](./media/user-guide/usbx-events/image125.png)

**Описание**

Это событие представляет собой процесс включения для изменения порта концентратора класса узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Порт.
- Поле сведений 3. Состояние порта.
- Поле сведений 4. Не используется.

### <a name="host-class-hub-port-change-over-current-process"></a>Завершение текущего процесса для изменения порта концентратора класса узла 

#### <a name="ux_host_class_hub_port_change_over_current_process"></a>ux_host_class_hub_port_change_over_current_process

**Значок** ![Значок завершения текущего процесса для изменения порта концентратора класса узла](./media/user-guide/usbx-events/image126.png)

**Описание**

Это событие представляет собой выделение пакета с помощью nx_packet_allocate.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Порт.
- Поле сведений 3. Состояние порта.
- Поле сведений 4. Не используется.

### <a name="host-class-hub-port-change-reset-process"></a>Процесс сброса для изменения порта концентратора класса узла 

#### <a name="ux_host_class_hub_port_change_reset_process"></a>ux_host_class_hub_port_change_reset_process

**Значок** ![Значок процесса сброса для изменения порта концентратора класса узла](./media/user-guide/usbx-events/image127.png)

**Описание**

Это событие представляет собой процесс сброса для изменения порта концентратора класса узла USBX.

**Поля сведений**

- Поле сведений 1. Концентратор. Поле сведений 2. Порт.
- Поле сведений 3. Состояние порта.
- Поле сведений 4. Не используется.

### <a name="host-class-hub-port-change-suspend-process"></a>Процесс приостановки для изменения порта концентратора класса узла 

#### <a name="ux_host_class_hub_port_change_suspend_process"></a>ux_host_class_hub_port_change_suspend_process

**Значок** ![Значок процесса приостановки для изменения порта концентратора класса узла](./media/user-guide/usbx-events/image128.png)

**Описание**

Это событие представляет собой процесс приостановки для изменения порта концентратора класса узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Порт.
- Поле сведений 3. Состояние порта.
- Поле сведений 4. Не используется.

### <a name="host-class-pima-activate"></a>Активация класса Pima узла 

#### <a name="ux_host_class_pima_activate"></a>ux_host_class_pima_activate

**Значок** ![Значок активации класса Pima узла](./media/user-guide/usbx-events/image129.png)

**Описание**

Это событие представляет собой активацию класса Pima узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-pima-deactivate"></a>Деактивация класса Pima узла 

#### <a name="ux_host_class_pima_deactivate"></a>ux_host_class_pima_deactivate

**Значок** ![Значок деактивации класса Pima узла](./media/user-guide/usbx-events/image130.png)

**Описание**

Это событие представляет собой деактивацию класса Pima узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-pima-device-info-get"></a>Получение сведений об устройстве для класса Pima узла 

#### <a name="ux_host_class_pima_device_info_get"></a>ux_host_class_pima_device_info_get

**Значок** ![Значок получения сведений об устройстве для класса Pima узла](./media/user-guide/usbx-events/image131.png)

**Описание**

Это событие представляет собой получение сведений о классе Pima узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Устройство Pima.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-pima-device-reset"></a>Сброс устройства для класса Pima узла 

#### <a name="ux_host_class_pima_device_reset"></a>ux_host_class_pima_device_reset

**Значок** ![Значок сброса устройства для класса Pima узла](./media/user-guide/usbx-events/image132.png)

**Описание**

Это событие представляет собой сброс устройства класса Pima узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-pima-notification"></a>Уведомление класса Pima узла 

#### <a name="ux_host_class_pima_notification"></a>ux_host_class_pima_notification

**Значок** ![Значок уведомления класса Pima узла](./media/user-guide/usbx-events/image133.png)

**Описание**

Это событие представляет собой уведомление класса Pima узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса. Поле сведений 2. Код события.
- Поле сведений 3. Идентификатор транзакции.
- Поле сведений 4. Параметр 1.

### <a name="host-class-pima-number-objects-get"></a>Получение объектов номера класса Pima узла 

#### <a name="ux_host_class_pima_number_objects_get"></a>ux_host_class_pima_number_objects_get

**Значок** ![Значок получения объектов номера класса Pima узла](./media/user-guide/usbx-events/image134.png)

**Описание**

Это событие представляет собой получение объектов номера класса Pima узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-pima-object-close"></a>Закрытие объекта класса Pima узла 

#### <a name="ux_host_class_pima_object_close"></a>ux_host_class_pima_object_close

**Значок** ![Значок закрытия объекта класса Pima узла](./media/user-guide/usbx-events/image135.png)

**Описание**

Это событие представляет собой закрытие объекта класса Pima узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Объект.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-pima-object-copy"></a>Копирование объекта класса Pima узла 

#### <a name="ux_host_class_pima_object_copy"></a>ux_host_class_pima_object_copy

**Значок** ![Значок копирования объекта класса Pima узла](./media/user-guide/usbx-events/image136.png)

**Описание**

Это событие представляет собой копирование объекта класса Pima узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Дескриптор объекта.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-pima-object-delete"></a>Удаление объекта из класса Pima узла 

#### <a name="ux_host_class_pima_object_delete"></a>ux_host_class_pima_object_delete

**Значок** ![Значок удаления объекта из класса Pima узла](./media/user-guide/usbx-events/image137.png)

**Описание**

Это событие представляет собой удаление объекта из класса Pima узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Дескриптор объекта.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-pima-object-get"></a>Получение объекта класса Pima узла 

#### <a name="ux_host_class_pima_object_get"></a>ux_host_class_pima_object_get

**Значок** ![Значок получения объекта класса Pima узла](./media/user-guide/usbx-events/image138.png)

**Описание**

Это событие представляет собой получение сведений о RARP с помощью nx_rarp_info_get.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Дескриптор объекта.
- Поле сведений 3. Объект.
- Поле сведений 4. Не используется.

### <a name="host-class-pima-object-info-get"></a>Получение сведений об объекте класса Pima узла 

#### <a name="ux_host_class_pima_object_info_get"></a>ux_host_class_pima_object_info_get

**Значок** ![Значок получения сведений об объекте класса Pima узла](./media/user-guide/usbx-events/image139.png)

**Описание**

Это событие представляет собой получение сведений об объекте класса Pima узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Дескриптор объекта.
- Поле сведений 3. Объект.
- Поле сведений 4. Не используется.

### <a name="host-class-pima-object-info-send"></a>Отправка сведений об объекте класса Pima узла 

#### <a name="ux_host_class_pima_object_info_send"></a>ux_host_class_pima_object_info_send

**Значок** ![Значок отправки сведений об объекте класса Pima узла](./media/user-guide/usbx-events/image140.png)

**Описание**

Это событие представляет собой отправку сведений об объекте класса Pima узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Объект.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-pima-object-move"></a>Перемещение объекта класса Pima узла 

#### <a name="ux_host_class_pima_object_move"></a>ux_host_class_pima_object_move

**Значок** ![Значок перемещения объекта класса Pima узла](./media/user-guide/usbx-events/image141.png)

**Описание**

Это событие представляет собой перемещение объекта класса Pima узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Дескриптор объекта.
- Поле сведений 3. Объект.
- Поле сведений 4. Не используется.

### <a name="host-class-pima-object-send"></a>Отправка объекта класса Pima узла 

#### <a name="ux_host_class_pima_object_move"></a>ux_host_class_pima_object_move

**Значок** ![Значок отправки объекта класса Pima узла](./media/user-guide/usbx-events/image142.png)

**Описание**

Это событие представляет собой отправку объекта класса Pima узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Объект.
- Поле сведений 3. Буфер объекта.
- Поле сведений 4. Длина объекта.

### <a name="host-class-pima-object-transfer-abort"></a>Прерывание перемещения объекта класса Pima узла 

#### <a name="ux_host_class_pima_object_transfer_abort"></a>ux_host_class_pima_object_transfer_abort

**Значок** ![Значок прерывания перемещения объекта класса Pima узла](./media/user-guide/usbx-events/image143.png)

**Описание**

Это событие представляет собой прерывание перемещения объекта класса Pima узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Дескриптор объекта.
- Поле сведений 3. Объект.
- Поле сведений 4. Не используется.

### <a name="host-class-pima-read"></a>Считывание класса Pima узла 

#### <a name="ux_host_class_pima_read"></a>ux_host_class_pima_read

**Значок** ![Значок считывания класса Pima узла](./media/user-guide/usbx-events/image144.png)

**Описание**

Это событие представляет собой считывание класса Pima узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Указатель данных.
- Поле сведений 3. Длина данных.
- Поле сведений 4. Не используется.

### <a name="host-class-pima-request-cancel"></a>Отмена запроса класса Pima узла 

#### <a name="ux_host_class_pima_request_cancel"></a>ux_host_class_pima_request_cancel

**Значок** ![Значок отмены запроса класса Pima узла](./media/user-guide/usbx-events/image145.png)

**Описание**

Это событие представляет собой отмену запроса класса Pima узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-pima-session-close"></a>Закрытие сеанса класса Pima узла 

#### <a name="ux_host_class_pima_session_close"></a>ux_host_class_pima_session_close

**Значок** ![Значок закрытия сеанса класса Pima узла](./media/user-guide/usbx-events/image146.png)

**Описание**

Это событие представляет собой закрытие сеанса класса Pima узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Сеанс Pima.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-pima-session-open"></a>Открытие сеанса класса Pima узла 

#### <a name="ux_host_class_pima_session_open"></a>ux_host_class_pima_session_open

**Значок** ![Значок открытия сеанса класса Pima узла](./media/user-guide/usbx-events/image147.png)

**Описание** Это событие представляет собой открытие сеанса класса Pima узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Сеанс Pima.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-pima-storage-ids-get"></a>Получение идентификаторов хранилища класса Pima узла 

#### <a name="ux_host_class_pima_session_ids_get"></a>ux_host_class_pima_session_ids_get

**Значок** ![Значок получения идентификаторов хранилища класса Pima узла](./media/user-guide/usbx-events/image148.png)

**Описание**

Это событие представляет собой получение идентификаторов хранилища класса Pima узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Массив идентификаторов хранилища.
- Поле сведений 3. Длина идентификатора хранилища.
Поле сведений 4. Не используется.

### <a name="host-class-pima-storage-info-get"></a>Получение сведений о хранилище класса Pima узла 

#### <a name="ux_host_class_pima_storage_info_get"></a>ux_host_class_pima_storage_info_get

**Значок** ![Значок получения сведений о хранилище класса Pima узла](./media/user-guide/usbx-events/image149.png)

**Описание**

Это событие представляет собой получение сведений о хранилище класса Pima узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Идентификатор хранилища.
- Поле сведений 3. Хранилище.
- Поле сведений 4. Не используется.

### <a name="host-class-pima-thumb-get"></a>Получение бегунка класса Pima узла 

#### <a name="ux_host_class_pima_thumb_get"></a>ux_host_class_pima_thumb_get

**Значок** ![Значок получения бегунка класса Pima узла](./media/user-guide/usbx-events/image150.png)

**Описание**

Это событие представляет собой невозможность подключения к серверу TCP через nx_tcp_server_socket_unaccept.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Дескриптор объекта.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-pima-write"></a>Запись класса Pima узла 

#### <a name="ux_host_class_pima_thumb_get"></a>ux_host_class_pima_thumb_get

**Значок** ![Значок записи класса Pima узла](./media/user-guide/usbx-events/image151.png)

**Описание**

Это событие представляет собой запись класса Pima узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Указатель данных.
- Поле сведений 3. Длина данных.
- Поле сведений 4. Не используется.

### <a name="host-class-printer-activate"></a>Активация принтера класса узла 

#### <a name="ux_host_class_printer_activate"></a>ux_host_class_printer_activate

**Значок** ![Значок активации принтера класса узла](./media/user-guide/usbx-events/image152.png)

**Описание**

Это событие представляет собой активацию принтера класса узла USBX.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP.
- Поле сведений 2. Указатель на сокет.
- Поле сведений 3. Тип службы.
- Поле сведений 4. Размер окна приема.

### <a name="host-class-printer-deactivate"></a>Деактивация принтера класса узла 

#### <a name="ux_host_class_printer_deactivate"></a>ux_host_class_printer_deactivate

**Значок** ![Значок деактивации принтера класса узла](./media/user-guide/usbx-events/image153.png)

**Описание**

Это событие представляет собой деактивацию принтера класса узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-printer-name-get"></a>Получение названия принтера класса узла 

#### <a name="ux_host_class_printer_name_get"></a>ux_host_class_printer_name_get

**Значок** ![Значок получения названия принтера класса узла](./media/user-guide/usbx-events/image154.png)

**Описание**

Это событие представляет собой получение названия принтера класса узла USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-printer-read"></a>Считывание принтера класса узла 

#### <a name="ux_host_class_printer_read"></a>ux_host_class_printer_read

**Значок** ![Значок считывания принтера класса узла](./media/user-guide/usbx-events/image155.png)

**Описание**

Это событие представляет собой считывание принтера класса узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Указатель данных.
- Поле сведений 3. Запрошенная длина.
- Поле сведений 4. Не используется.

### <a name="host-class-printer-soft-reset"></a>Частичный сброс принтера класса узла 

#### <a name="ux_host_class_printer_soft_reset"></a>ux_host_class_printer_soft_reset

**Значок** ![Значок частичного сброса принтера класса узла](./media/user-guide/usbx-events/image156.png)

**Описание**

Это событие представляет собой частичный сброс принтера класса узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-printer-status-get"></a>Получение состояния принтера класса узла 

#### <a name="ux_host_class_printer_status_get"></a>ux_host_class_printer_status_get

**Значок** ![Значок получения состояния принтера класса узла](./media/user-guide/usbx-events/image157.png)

**Описание**

Это событие представляет собой получение состояния принтера класса узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Состояние принтера.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-printer-write"></a>Запись принтера класса узла 

#### <a name="ux_host_class_printer_write"></a>ux_host_class_printer_write

**Значок** ![Значок записи принтера класса узла](./media/user-guide/usbx-events/image158.png)

**Описание**

Это событие представляет собой запись принтера класса узла USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Указатель данных.
- Поле сведений 3. Запрошенная длина.
- Поле сведений 4. Не используется.

### <a name="host-class-prolific-activate"></a>Активация класса Prolific узла 

#### <a name="ux_host_class_prolific_activate"></a>ux_host_class_prolific_activate 

**Значок** ![Значок активации класса Prolific узла](./media/user-guide/usbx-events/image159.png)

**Описание**

Это событие представляет собой активацию класса Prolific узла USBX.

**Поля сведений** 

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-prolific-deactivate"></a>Деактивация класса Prolific узла 

#### <a name="ux_host_class_prolific_deactivate"></a>ux_host_class_prolific_deactivate 

**Значок** ![Значок деактивации класса Prolific узла](./media/user-guide/usbx-events/image160.png)

**Описание**

Это событие представляет собой деактивацию класса Prolific узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-prolific-ioctl-abort-in-pipe"></a>Прерывание в канале класса Prolific Ioctl узла 

#### <a name="ux_host_class_prolific_ioctl_abort_in_pipe"></a>ux_host_class_prolific_ioctl_abort_in_pipe

**Значок** ![Значок прерывания в канале класса Prolific Ioctl узла](./media/user-guide/usbx-events/image161.png)

**Описание**

Это событие представляет собой прерывание в канале класса Prolific Ioctl узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Конечная точка.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-prolific-ioctl-abort-out-pipe"></a>Прерывание вне канала класса Prolific Ioctl узла 

#### <a name="ux_host_class_prolific_ioctl_abort_out_pipe"></a>ux_host_class_prolific_ioctl_abort_out_pipe

**Значок** ![Значок прерывания вне канала класса Prolific Ioctl узла](./media/user-guide/usbx-events/image162.png)

**Описание**

Это событие представляет собой прерывание вне канала класса Prolific Ioctl узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Конечная точка.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-prolific-ioctl-get-device-status"></a>Получение состояния устройства класса Prolific Ioctl узла 

#### <a name="ux_host_class_prolific_ioctl_get_device_status"></a>ux_host_class_prolific_ioctl_get_device_status

**Значок** ![Значок получения состояния устройства класса Prolific Ioctl узла](./media/user-guide/usbx-events/image163.png)

**Описание**

Это событие представляет собой получение состояния устройства класса Prolific Ioctl узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Состояние устройства.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-prolific-ioctl-get-line-coding"></a>Получение кодировки строки класса Prolific Ioctl узла 

#### <a name="ux_host_class_prolific_ioctl_get_line_coding"></a>ux_host_class_prolific_ioctl_get_line_coding

**Значок** ![Значок получения кодировки строки класса Prolific Ioctl узла](./media/user-guide/usbx-events/image164.png)

**Описание**

Это событие представляет собой получение кодировки строки класса Prolific Ioctl узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Параметр.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-prolific-ioctl-purge"></a>Очистка класса Prolific Ioctl узла 

#### <a name="ux_host_class_prolific_ioctl_purge"></a>ux_host_class_prolific_ioctl_purge

**Значок** ![Значок очистки класса Prolific Ioctl узла](./media/user-guide/usbx-events/image165.png)

**Описание**

Это событие представляет собой очистку класса Prolific Ioctl узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Параметр.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-prolific-ioctl-report-device"></a>Устройство отчетов класса Prolific Ioctl узла 

#### <a name="ux_host_class_prolific_ioctl_report_device"></a>ux_host_class_prolific_ioctl_report_device

**Значок** ![Значок устройства отчетов класса Prolific Ioctl узла](./media/user-guide/usbx-events/image166.png)

**Описание**

Это событие представляет собой событие устройства отчетов класса Prolific Ioctl узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Параметр.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-prolific-ioctl-send-break"></a>Остановка отправки класса Prolific Ioctl узла 

#### <a name="ux_host_class_prolific_ioctl_send_break"></a>ux_host_class_prolific_ioctl_send_break

**Значок** ![Значок остановки отправки класса Prolific Ioctl узла](./media/user-guide/usbx-events/image167.png)

**Описание**

Это событие представляет собой остановку отправки класса Prolific Ioctl узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-prolific-ioctl-set-line-coding"></a>Задание кодировки строки в классе Prolific Ioctl узла 

#### <a name="ux_host_class_prolific_ioctl_set_line_coding"></a>ux_host_class_prolific_ioctl_set_line_coding

**Значок** ![Значок задания кодировки строки в классе Prolific Ioctl узла](./media/user-guide/usbx-events/image168.png)

**Описание**

Это событие представляет собой задание кодировки строки в классе Prolific Ioctl узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Параметр.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-prolific-ioctl-set-line-state"></a>Задание состояния строки в классе Prolific Ioctl узла 

#### <a name="ux_host_class_prolific_ioctl_set_line_state"></a>ux_host_class_prolific_ioctl_set_line_state

**Значок** ![Значок задания состояния строки в классе Prolific Ioctl узла](./media/user-guide/usbx-events/image169.png)

**Описание**

Это событие представляет собой задание состояния строки в классе Prolific Ioctl узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Параметр.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-prolific-read"></a>Считывание класса Prolific узла 

#### <a name="ux_host_class_prolific_read"></a>ux_host_class_prolific_read

**Значок** ![Значок считывания класса Prolific узла](./media/user-guide/usbx-events/image170.png)

**Описание**

Это событие представляет собой считывание класса Prolific узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Указатель данных.
- Поле сведений 3. Запрошенная длина.
- Поле сведений 4. Не используется.

### <a name="host-class-prolific-reception-start"></a>Запуск приема в классе Prolific узла 

#### <a name="ux_host_class_prolific_reception_start"></a>ux_host_class_prolific_reception_start

**Значок** ![Значок запуска приема в классе Prolific узла](./media/user-guide/usbx-events/image171.png)

**Описание**

Это событие представляет собой запуск приема в классе Prolific узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-prolific-reception-stop"></a>Остановка приема в классе Prolific узла 

#### <a name="ux_host_class_prolific_reception_stop"></a>uux_host_class_prolific_reception_stop

**Значок** ![Значок остановки приема в классе Prolific узла](./media/user-guide/usbx-events/image172.png)

**Описание**

Это событие представляет собой остановку приема в классе Prolific узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-prolific-write"></a>Запись класса Prolific узла 

#### <a name="ux_host_class_prolific_write"></a>ux_host_class_prolific_write

**Значок** ![Значок записи класса Prolific узла](./media/user-guide/usbx-events/image173.png)

**Описание**

Это событие представляет собой запись класса Prolific узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Указатель данных.
- Поле сведений 3. Запрошенная длина.
- Поле сведений 4. Не используется.

### <a name="host-class-storage-activate"></a>Активация хранилища класса узла 

#### <a name="ux_host_class_storage_activate"></a>ux_host_class_storage_activate

**Значок** ![Значок активации хранилища класса узла](./media/user-guide/usbx-events/image174.png)

**Описание**

Это событие представляет собой активацию хранилища класса узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-storage-deactivate"></a>Деактивация хранилища класса узла 

#### <a name="ux_host_class_storage_deactivate"></a>ux_host_class_storage_deactivate

**Значок** ![Значок деактивации хранилища класса узла](./media/user-guide/usbx-events/image175.png)

**Описание**

Это событие представляет собой деактивацию хранилища класса узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-storage-media-capacity-get"></a>Получение емкости носителя хранилища класса узла 

#### <a name="ux_host_class_storage_media_capacity_get"></a>ux_host_class_storage_media_capacity_get

**Значок** ![Значок получения емкости носителя хранилища класса узла](./media/user-guide/usbx-events/image176.png)

**Описание**

Это событие представляет собой получение емкости носителя хранилища класса узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-storage-media-format-capacity-get"></a>Получение формата емкости носителя в хранилище класса узла

#### <a name="ux_host_class_storage_media_format_capacity_get"></a>ux_host_class_storage_media_format_capacity_get

**Значок** ![Значок получения формата емкости носителя в хранилище класса узла](./media/user-guide/usbx-events/image177.png)

**Описание**

Это событие представляет собой получение формата емкости носителя в хранилище класса узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

#### <a name="host-class-storage-media-mount"></a>Подключение носителя хранилища класса узла 

#### <a name="ux_host_class_storage_media_mount"></a>ux_host_class_storage_media_mount

**Значок** ![Значок подключения носителя хранилища класса узла](./media/user-guide/usbx-events/image178.png)

**Описание**

Это событие представляет собой подключение носителя хранилища класса узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Сектор.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-storage-media-open"></a>Открытие носителя хранилища класса узла 

#### <a name="ux_host_class_storage_media_open"></a>ux_host_class_storage_media_open

**Значок** ![Значок открытия носителя хранилища класса узла](./media/user-guide/usbx-events/image179.png)

**Описание**

Это событие представляет собой открытие носителя хранилища класса узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Носитель.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-storage-media-read"></a>Считывание носителя хранилища класса узла 

#### <a name="ux_host_class_storage_media_read"></a>ux_host_class_storage_media_read

**Значок** ![Значок считывания носителя хранилища класса узла](./media/user-guide/usbx-events/image180.png)

**Описание**

Это событие представляет собой считывание носителя хранилища класса узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Запуск сектора.
- Поле сведений 3. Число секторов.
- Поле сведений 4. Указатель данных.

### <a name="host-class-storage-media-write"></a>Запись носителя хранилища класса узла 

#### <a name="ux_host_class_storage_media_write"></a>ux_host_class_storage_media_write

**Значок** ![Значок записи носителя хранилища класса узла](./media/user-guide/usbx-events/image181.png)

**Описание**

Это событие представляет собой запись носителя хранилища класса узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Запуск сектора.
- Поле сведений 3. Число секторов.
- Поле сведений 4. Указатель данных.

### <a name="host-class-storage-request-sense"></a>Запрос на контроль хранилища класса узла 

#### <a name="ux_host_class_storage_request_sense"></a>ux_host_class_storage_request_sense

**Значок** ![Значок запроса на контроль хранилища класса узла](./media/user-guide/usbx-events/image182.png)

**Описание**

Это событие представляет собой запрос на контроль хранилища класса узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-storage-start-stop"></a>Запуск и остановка хранилища класса узла 

#### <a name="ux_host_class_storage_start_stop"></a>ux_host_class_storage_start_stop

**Значок** ![Значок запуска и остановки хранилища класса узла](./media/user-guide/usbx-events/image183.png)

**Описание**

Это событие представляет собой запуск и остановку хранилища класса узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Сигнал о запуске и остановке.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-class-storage-unit-ready-test"></a>Тест готовности единиц хранения для класса узла 

#### <a name="ux_host_class_storage_unit_ready_test"></a>ux_host_class_storage_unit_ready_test

**Значок** ![Значок теста готовности единиц хранения для класса узла](./media/user-guide/usbx-events/image184.png)

**Описание**

Это событие представляет собой событие теста готовности единиц хранения для класса узла USBX.

**Поля сведений**

- Поле сведений 1. Экземпляр класса.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-stack-class-instance-create"></a>Создание экземпляра класса стека узла 

#### <a name="ux_host_class_instance_create"></a>ux_host_class_instance_create

**Значок** ![Значок создания экземпляра класса стека узла](./media/user-guide/usbx-events/image185.png)

**Описание**

Это событие представляет собой создание экземпляра класса стека узла USBX.

**Поля сведений**

- Поле сведений 1. Класс.
- Поле сведений 2. Экземпляр класса.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-stack-class-instance-destroy"></a>Уничтожение экземпляра класса стека узла 

#### <a name="ux_host_class_instance_create"></a>ux_host_class_instance_create

**Значок** ![Значок уничтожения экземпляра класса стека узла](./media/user-guide/usbx-events/image186.png)

**Описание**

Это событие представляет собой уничтожение экземпляра класса стека узла USBX.

**Поля сведений**

- Поле сведений 1. Класс.
- Поле сведений 2. Экземпляр класса.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-stack-configuration-delete"></a>Удаление конфигурации стека узла 

#### <a name="ux_host_class_configuration_delete"></a>ux_host_class_configuration_delete

**Значок** ![Значок удаления конфигурации стека узла](./media/user-guide/usbx-events/image187.png)

**Описание**

Это событие представляет собой удаление конфигурации стека узла USBX.

**Поля сведений**

- Поле сведений 1. Конфигурация.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-stack-configuration-enumerate"></a>Перечисление конфигураций стека узла 

#### <a name="ux_host_stack_configuration_enumerate"></a>ux_host_stack_configuration_enumerate

**Значок** ![Значок перечисления конфигураций стека узла](./media/user-guide/usbx-events/image188.png)

**Описание**

Это событие представляет собой перечисление конфигураций стека узла USBX.

**Поля сведений**

- Поле сведений 1. Устройство.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="stack-configuration-instance-create"></a>Создание экземпляра конфигурации стека 

#### <a name="ux_host_stack_configuration_instance_create"></a>ux_host_stack_configuration_instance_create

**Значок** ![Значок создания экземпляра конфигурации стека](./media/user-guide/usbx-events/image189.png)

**Описание**

Это событие представляет собой создание экземпляра конфигурации стека узла USBX.

**Поля сведений**

- Поле сведений 1. Конфигурация.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-stack-configuration-instance-delete"></a>Удаление экземпляра конфигурации стека узла 

#### <a name="ux_host_stack_configuration_instance_delete"></a>ux_host_stack_configuration_instance_delete

**Значок** ![Значок удаления экземпляра конфигурации стека узла](./media/user-guide/usbx-events/image190.png)

**Описание**

Это событие представляет собой удаление экземпляра конфигурации стека узла USBX.

**Поля сведений**

- Поле сведений 1. Конфигурация.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-stack-configuration-set"></a>Набор конфигураций стека узла 

#### <a name="ux_host_stack_configuration_set"></a>ux_host_stack_configuration_set

**Значок** ![Значок набора конфигураций стека узла](./media/user-guide/usbx-events/image191.png)

**Описание**

Это событие представляет собой событие набора конфигураций стека узла USBX.

**Поля сведений**

- Поле сведений 1. Конфигурация.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-stack-device-address-set"></a>Набор адресов устройства стека узла 

#### <a name="ux_host_stack_device_address_set"></a>ux_host_stack_device_address_set

**Значок** ![Значок набора адресов устройства стека узла](./media/user-guide/usbx-events/image192.png)

**Описание**

Это событие представляет собой событие набора адресов устройства стека узла USBX.

**Поля сведений**

- Поле сведений 1. Устройство.
- Поле сведений 2. Адрес устройства.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-stack-device-configuration-get"></a>Получение конфигурации устройства стека узла 

#### <a name="ux_host_stack_device_configuration_get"></a>ux_host_stack_device_configuration_get

**Значок** ![Значок получения конфигурации устройства стека узла](./media/user-guide/usbx-events/image193.png)

**Описание**

Это событие представляет собой получение конфигурации устройства стека узла USBX.

**Поля сведений**

- Поле сведений 1. Устройство.
- Поле сведений 2. Конфигурация.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-stack-device-configuration-select"></a>Выбор конфигурации устройства стека узла 

#### <a name="ux_host_stack_device_configuration_select"></a>ux_host_stack_device_configuration_select

**Значок** ![Значок выбора конфигурации устройства стека узла](./media/user-guide/usbx-events/image194.png)

**Описание**

Это событие представляет собой выбор конфигурации устройства стека узла USBX.

**Поля сведений**

- Поле сведений 1. Устройство.
- Поле сведений 2. Конфигурация.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-stack-device-descriptor-read"></a>Считывание дескриптора устройства стека узла 

#### <a name="ux_host_stack_device_descriptor_read"></a>ux_host_stack_device_descriptor_read

**Значок** ![Значок считывания дескриптора устройства стека узла](./media/user-guide/usbx-events/image195.png)

**Описание**

Это событие представляет собой считывание дескриптора устройства стека узла USBX.

**Поля сведений**

- Поле сведений 1. Устройство.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-stack-device-get"></a>Получение устройства стека узла 

#### <a name="ux_host_stack_device_get"></a>ux_host_stack_device_get

**Значок** ![Значок получения устройства стека узла](./media/user-guide/usbx-events/image196.png)

**Описание**

Это событие представляет собой событие получения устройства стека узла USBX.

**Поля сведений**

- Поле сведений 1. Индекс устройства.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-stack-device-remove"></a>Удаление устройства стека узла 

#### <a name="ux_host_stack_device_remove"></a>ux_host_stack_device_remove

**Значок** ![Значок удаления устройства стека узла](./media/user-guide/usbx-events/image197.png)

**Описание**

Это событие представляет собой удаление устройства стека узла USBX.

**Поля сведений**

- Поле сведений 1. Hcd.
- Поле сведений 2. Родительский элемент.
- Поле сведений 3. Индекс порта.
- Поле сведений 4. Устройство.

### <a name="host-stack-device-resource-free"></a>Освобождение ресурса устройства стека узла 

#### <a name="ux_host_stack_device_resource_free"></a>ux_host_stack_device_resource_free

**Значок** ![Значок освобождения ресурса устройства стека узла](./media/user-guide/usbx-events/image198.png)

**Описание**

Это событие представляет собой освобождение ресурса устройства стека узла USBX.

**Поля сведений**

- Поле сведений 1. Устройство.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-stack-endpoint-instance-create"></a>Создание экземпляра конечной точки стека узла 

#### <a name="ux_host_stack_endpoint_instance_create"></a>ux_host_stack_endpoint_instance_create

**Значок** ![Значок создания экземпляра конечной точки стека узла](./media/user-guide/usbx-events/image199.png)

**Описание**

Это событие представляет собой создание экземпляра конечной точки стека узла USBX.

**Поля сведений**

- Поле сведений 1. Устройство.
- Поле сведений 2. Конечная точка.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-stack-endpoint-instance-delete"></a>Удаление экземпляра конечной точки стека узла 

#### <a name="ux_host_stack_endpoint_instance_delete"></a>ux_host_stack_endpoint_instance_delete

**Значок** ![Значок удаления экземпляра конечной точки стека узла](./media/user-guide/usbx-events/image200.png)

**Описание**

Это событие представляет собой удаление экземпляра конечной точки стека узла USBX.

**Поля сведений**

- Поле сведений 2. Конечная точка.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-stack-endpoint-reset"></a>Сброс конечной точки стека узла 

#### <a name="ux_host_stack_endpoint_reset"></a>ux_host_stack_endpoint_reset

**Значок** ![Значок сброса конечной точки стека узла](./media/user-guide/usbx-events/image201.png)

**Описание**

Это событие представляет собой сброс конечной точки стека узла USBX.

**Поля сведений**

- Поле сведений 1. Устройство.
- Поле сведений 2. Конечная точка.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-stack-endpoint-transfer-abort"></a>Прерывание перемещения конечной точки стека узла 

#### <a name="ux_host_stack_endpoint_transfer_abort"></a>ux_host_stack_endpoint_transfer_abort

**Значок** ![Значок прерывания перемещения конечной точки стека узла](./media/user-guide/usbx-events/image202.png)

**Описание**

Это событие представляет собой прерывание перемещения конечной точки стека узла USBX.

**Поля сведений**

- Поле сведений 1. Конечная точка.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-stack-host-controller-register"></a>Регистрация хост-контроллера стека узла 

#### <a name="ux_host_stack_hcd_register"></a>ux_host_stack_hcd_register

**Значок** ![Значок регистрации хост-контроллера стека узла](./media/user-guide/usbx-events/image203.png)

**Описание**

Это событие представляет собой регистрацию хост-контроллера стека узла USBX.

**Поля сведений**

- Поле сведений 1. Имя Hcd.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-stack-initialize"></a>Инициализация стека узла 

#### <a name="ux_host_stack_initialize"></a>ux_host_stack_initialize

**Значок** ![Значок инициализации стека узла](./media/user-guide/usbx-events/image204.png)

**Описание**

Это событие представляет собой инициализацию стека узла USBX.

**Поля сведений**

- Поле сведений 1. Не используется.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-stack-interface-endpoint-get"></a>Получение конечной точки интерфейса стека узла 

#### <a name="interface_-tcp-retry-entry"></a>Interface_ TCP retry entry

**Значок** ![Значок получения конечной точки интерфейса стека узла](./media/user-guide/usbx-events/image205.png)

**Описание**

Это событие представляет собой событие повторной попытки подключения по внутреннему протоколу TCP в NetX.

**Поля сведений**

- Поле сведений 1. Интерфейс.
- Поле сведений 2. Индекс конечной точки.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-stack-interface-instance-create"></a>Создание экземпляра интерфейса стека узла 

#### <a name="ux_host_stack_interface_instance_create"></a>ux_host_stack_interface_instance_create

**Значок** ![Значок создания экземпляра интерфейса стека узла](./media/user-guide/usbx-events/image206.png)

**Описание**

Это событие представляет собой создание экземпляра интерфейса стека узла USBX.

**Поля сведений**

- Поле сведений 1. Интерфейс.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-stack-interface-instance-delete"></a>Удаление экземпляра интерфейса стека узла 

#### <a name="ux_host_stack_interface_instance_delete"></a>ux_host_stack_interface_instance_delete

**Значок** ![Значок удаления экземпляра интерфейса стека узла](./media/user-guide/usbx-events/image207.png)

**Описание**

Это событие представляет собой удаление экземпляра интерфейса стека узла USBX.

**Поля сведений**

- Поле сведений 1. Интерфейс.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-stack-interface-set"></a>Набор интерфейсов стека узла 

#### <a name="ux_host_stack_interface_set"></a>ux_host_stack_interface_set

**Значок** ![Значок набора интерфейсов стека узла](./media/user-guide/usbx-events/image208.png)

**Описание**

Это событие представляет собой событие набора интерфейсов стека узла USBX.

**Поля сведений**

- Поле сведений 1. Интерфейс.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-stack-interface-setting-select"></a>Выбор параметров для интерфейса стека узла 

#### <a name="ux_host_stack_interface_setting_select"></a>ux_host_stack_interface_setting_select

**Значок** ![Значок выбора параметров для интерфейса стека узла](./media/user-guide/usbx-events/image209.png)

**Описание**

Это событие представляет собой событие набора интерфейсов стека узла USBX.

**Поля сведений**

- Поле сведений 1. Интерфейс.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-stack-new-configuration-create"></a>Создание конфигурации стека узла 

#### <a name="ux_host_stack_new_configuration_create"></a>ux_host_stack_new_configuration_create

**Значок** ![Значок создания конфигурации стека узла](./media/user-guide/usbx-events/image210.png)

**Описание**
 
Это событие представляет собой создание конфигурации стека узла USBX.

**Поля сведений**

- Поле сведений 1. Устройство.
- Поле сведений 2. Конфигурация.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-stack-new-device-create"></a>Создание устройства в стеке узла 

#### <a name="ux_host_stack_new_device_create"></a>ux_host_stack_new_device_create

**Значок** ![Значок создания устройства в стеке узла](./media/user-guide/usbx-events/image211.png)

**Описание**
 
 Это событие представляет собой создание устройства в стеке узла USBX.

**Поля сведений**

- Поле сведений 1. Hcd.
- Поле сведений 2. Владелец устройства.
- Поле сведений 3. Индекс порта.
- Поле сведений 4. Устройство.

### <a name="host-stack-new-endpoint-create"></a>Создание конечной точки стека узла 

#### <a name="ux_host_stack_new_endpoint_create"></a>ux_host_stack_new_endpoint_create

**Значок** ![Значок создания конечной точки стека узла](./media/user-guide/usbx-events/image212.png)

**Описание**
 
Это событие представляет собой создание конечной точки стека узла USBX.

**Поля сведений**

- Поле сведений 1. Интерфейс.
- Поле сведений 2. Конечная точка.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-stack-root-hub-change-process"></a>Процесс изменения корневого концентратора стека узла 

#### <a name="ux_host_stack_rh_change_process"></a>ux_host_stack_rh_change_process

**Значок** ![Значок процесса изменения корневого концентратора стека узла](./media/user-guide/usbx-events/image213.png)

**Описание**
 
Это событие представляет собой процесс изменения корневого концентратора стека узла USBX.

**Поля сведений**

- Поле сведений 1. Индекс порта.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-stack-root-hub-device-extraction"></a>Извлечение устройства корневого концентратора стека узла 

#### <a name="ux_host_stack_rh_device_extraction"></a>ux_host_stack_rh_device_extraction

**Значок** ![Значок извлечения устройства корневого концентратора стека узла](./media/user-guide/usbx-events/image214.png)

**Описание**

Это событие представляет собой извлечение устройства корневого концентратора стека узла USBX.

**Поля сведений**

- Поле сведений 1. Hcd.
- Поле сведений 2. Индекс порта.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-stack-root-hub-device-insertion"></a>Вставка устройства корневого концентратора стека узла 

#### <a name="ux_host_stack_rh_device_insertion"></a>ux_host_stack_rh_device_insertion

**Значок** ![Значок вставки устройства корневого концентратора стека узла](./media/user-guide/usbx-events/image215.png)

**Описание**

Это событие представляет собой вставку устройства корневого концентратора стека узла USBX.

**Поля сведений**

- Поле сведений 1. Hcd.
- Поле сведений 2. Индекс порта.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="host-stack-transfer-request"></a>Запрос на передачу стека узла 

#### <a name="ux_host_stack_transfer_request"></a>ux_host_stack_transfer_request

**Значок** ![Значок запроса на передачу стека узла](./media/user-guide/usbx-events/image216.png)

**Описание**

Это событие представляет собой запрос на передачу стека узла USBX.

**Поля сведений**

- Поле сведений 1. Устройство.
- Поле сведений 2. Конечная точка.
- Поле сведений 3. Запрос на передачу.
- Поле сведений 4. Не используется.

### <a name="host-stack-transfer-request-abort"></a>Прерывание запроса на передачу стека узла 

#### <a name="internal-io-driver-get-status"></a>Получение состояния внутреннего драйвера устройств ввода-вывода

**Значок** ![Значок прерывания запроса на передачу стека узла](./media/user-guide/usbx-events/image217.png)

**Описание**

Это событие представляет собой прерывание запроса на передачу стека узла USBX.

**Поля сведений**

- Поле сведений 1. Устройство.
- Поле сведений 2. Конечная точка.
- Поле сведений 3. Запрос на передачу.
- Поле сведений 4. Не используется.

### <a name="usbx-error"></a>Ошибка USBX 

#### <a name="ux_error"></a>ux_error

**Значок** ![Значок ошибки USBX](./media/user-guide/usbx-events/image218.png)

**Описание**

Это событие представляет собой событие ошибки USBX.

**Поля сведений**

- Поле сведений 1. Ошибка USBX.
- Поле сведений 2. Имя ошибки.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.