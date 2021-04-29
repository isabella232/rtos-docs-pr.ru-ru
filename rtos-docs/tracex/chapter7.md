---
title: Глава 7. События трассировки FileX в ОСРВ Azure
description: В этой главе содержится описание событий FileX в ОСРВ Azure.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: c3cbc945e33b87b6759c56ec1429d6bf57259bd9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815715"
---
# <a name="chapter-7---azure-rtos-filex-trace-events"></a><span data-ttu-id="d83b7-103">Глава 7. События трассировки FileX в ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="d83b7-103">Chapter 7 - Azure RTOS FileX trace events</span></span>

<span data-ttu-id="d83b7-104">В этой главе содержится описание событий FileX в ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="d83b7-104">This chapter contains a description of the Azure RTOS FileX events.</span></span> 

## <a name="list-of-events-and-icons"></a><span data-ttu-id="d83b7-105">Список событий и значков</span><span class="sxs-lookup"><span data-stu-id="d83b7-105">List of Events and Icons</span></span>

<span data-ttu-id="d83b7-106">**Ниже приведен список событий FileX, отображаемых в TraceX.**</span><span class="sxs-lookup"><span data-stu-id="d83b7-106">**The following is a list of FileX events displayed by TraceX.**</span></span>

<span data-ttu-id="d83b7-107">Далее приводится описание всех этих событий:</span><span class="sxs-lookup"><span data-stu-id="d83b7-107">The following describes each event:</span></span>

| <span data-ttu-id="d83b7-108">**Значок**:</span><span class="sxs-lookup"><span data-stu-id="d83b7-108">**Icon**</span></span>                         | <span data-ttu-id="d83b7-109">**Значение**</span><span class="sxs-lookup"><span data-stu-id="d83b7-109">**Meaning**</span></span>                               |
| -------------------------------- | ----------------------------------------- |
| ![Значок промаха внутреннего кэша логического сектора](./media/user-guide/fx-events/image1.png)    | <span data-ttu-id="d83b7-111">Промах внутреннего кэша логического сектора</span><span class="sxs-lookup"><span data-stu-id="d83b7-111">Internal Logical Sector Cache Miss</span></span> |
| ![Значок промаха внутреннего кэша каталога](./media/user-guide/fx-events/image2.png)    | <span data-ttu-id="d83b7-113">Промах внутреннего кэша каталога</span><span class="sxs-lookup"><span data-stu-id="d83b7-113">Internal Directory Cache Miss</span></span> |
| ![Значок очистки внутреннего носителя](./media/user-guide/fx-events/image3.png)    | <span data-ttu-id="d83b7-115">Очистка внутреннего носителя</span><span class="sxs-lookup"><span data-stu-id="d83b7-115">Internal Media Flush</span></span> |
| ![Значок чтения записи внутреннего каталога](./media/user-guide/fx-events/image4.png)    | <span data-ttu-id="d83b7-117">Чтение записи внутреннего каталога</span><span class="sxs-lookup"><span data-stu-id="d83b7-117">Internal Directory Entry Read</span></span> |
| ![Значок записи внутреннего каталога](./media/user-guide/fx-events/image5.png)    | <span data-ttu-id="d83b7-119">Запись внутреннего каталога</span><span class="sxs-lookup"><span data-stu-id="d83b7-119">Internal Directory Entry Write</span></span> |
| ![Значок чтения внутреннего драйвера ввода-вывода](./media/user-guide/fx-events/image6.png)    | <span data-ttu-id="d83b7-121">Чтение внутреннего драйвера ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="d83b7-121">Internal I/O Driver Read</span></span> |
| ![Значок записи внутреннего драйвера ввода-вывода](./media/user-guide/fx-events/image7.png)    | <span data-ttu-id="d83b7-123">Запись внутреннего драйвера ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="d83b7-123">Internal I/O Driver Write</span></span> |
| ![Значок очистки внутреннего драйвера ввода-вывода](./media/user-guide/fx-events/image8.png)    | <span data-ttu-id="d83b7-125">Очистка внутреннего драйвера ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="d83b7-125">Internal I/O Driver Flush</span></span> |
| ![Значок прерывания внутреннего драйвера ввода-вывода](./media/user-guide/fx-events/image9.png)    | <span data-ttu-id="d83b7-127">Прерывание внутреннего драйвера ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="d83b7-127">Internal I/O Driver Abort</span></span> |
| ![Значок инициализации внутреннего драйвера ввода-вывода](./media/user-guide/fx-events/image10.png)    | <span data-ttu-id="d83b7-129">Инициализация внутреннего драйвера ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="d83b7-129">Internal I/O Driver Initialize</span></span> |
| ![Значок чтения при загрузке внутреннего драйвера ввода-вывода](./media/user-guide/fx-events/image11.png)    | <span data-ttu-id="d83b7-131">Чтение при загрузке внутреннего драйвера ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="d83b7-131">Internal I/O Driver Boot Read</span></span> |
| ![Значок освобождения секторов внутреннего драйвера ввода-вывода](./media/user-guide/fx-events/image12.png)    | <span data-ttu-id="d83b7-133">Освобождение секторов внутреннего драйвера ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="d83b7-133">Internal I/O Driver Release Sectors</span></span> |
| ![Значок записи при загрузке внутреннего драйвера ввода-вывода](./media/user-guide/fx-events/image13.png)    | <span data-ttu-id="d83b7-135">Запись при загрузке внутреннего драйвера ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="d83b7-135">Internal I/O Driver Boot Write</span></span> |
| ![Значок отмены инициализации внутреннего драйвера ввода-вывода](./media/user-guide/fx-events/image14.png)    | <span data-ttu-id="d83b7-137">Отмена инициализации внутреннего драйвера ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="d83b7-137">Internal I / O Driver Driver Un-initialize</span></span> |
| ![Значок чтения атрибутов каталога](./media/user-guide/fx-events/image15.png)    | <span data-ttu-id="d83b7-139">**Чтение атрибутов каталога** (*fx_directory_attributes_read*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-139">**Directory Attributes Read** (*fx_directory_attributes_read*)</span></span> |
| ![Значок установки атрибутов каталога](./media/user-guide/fx-events/image16.png)    | <span data-ttu-id="d83b7-141">**Установка атрибутов каталога** (*fx_directory_attributes_set*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-141">**Directory Attributes Set** (*fx_directory_attributes_set*)</span></span> |
| ![Значок создания каталога](./media/user-guide/fx-events/image17.png)    | <span data-ttu-id="d83b7-143">**Создание каталога** (*fx_directory_create*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-143">**Directory Create** (*fx_directory_create*)</span></span> |
| ![Значок получения каталога по умолчанию](./media/user-guide/fx-events/image18.png)    | <span data-ttu-id="d83b7-145">**Получение каталога по умолчанию** (*fx_directory_default_get*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-145">**Directory Default Get** (*fx_directory_default_get*)</span></span> |
| ![Значок установки каталога по умолчанию](./media/user-guide/fx-events/image19.png)    | <span data-ttu-id="d83b7-147">**Установка каталога по умолчанию** (*fx_directory_default_set*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-147">**Directory Default Set** (*fx_directory_default_set*)</span></span> |
| ![Значок удаления каталога](./media/user-guide/fx-events/image20.png)    | <span data-ttu-id="d83b7-149">**Удаление каталога** (*fx_directory_delete*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-149">**Directory Delete** (*fx_directory_delete*)</span></span> |
| ![Значок поиска первой записи каталога](./media/user-guide/fx-events/image21.png)    | <span data-ttu-id="d83b7-151">**Поиск первой записи каталога** (*fx_directory_first_entry_find*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-151">**Directory First Entry Find** (*fx_directory_first_entry_find*)</span></span> |
| ![Значок поиска первой полной записи каталога](./media/user-guide/fx-events/image22.png)    | <span data-ttu-id="d83b7-153">**Поиск первой полной записи каталога** (*fx_directory_first_full_entry_find*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-153">**Directory First Full Entry Find** (*fx_directory_first_full_entry_find*)</span></span> |
| ![Значок получения сведений о каталоге](./media/user-guide/fx-events/image23.png)    | <span data-ttu-id="d83b7-155">**Получение сведений о каталоге** (*fx_directory_information_get*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-155">**Directory Information Get** (*fx_directory_information_get*)</span></span> |
| ![Значок очистки локального пути к каталогу](./media/user-guide/fx-events/image24.png)    | <span data-ttu-id="d83b7-157">**Очистка локального пути к каталогу** (*fx_directory_local_path_clear*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-157">**Directory Local Path Clear** (*fx_directory_local_path_clear*)</span></span> |
| ![Значок получения локального пути к каталогу](./media/user-guide/fx-events/image25.png)    | <span data-ttu-id="d83b7-159">**Получение локального пути к каталогу** (*fx_directory_local_path_get*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-159">**Directory Local Path Get** (*fx_directory_local_path_get*)</span></span> |
| ![Значок восстановления локального пути к каталогу](./media/user-guide/fx-events/image26.png)    | <span data-ttu-id="d83b7-161">**Восстановление локального пути к каталогу** (*fx_directory_local_path_restore*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-161">**Directory Local Path Restore** (*fx_directory_local_path_restore*)</span></span> |
| ![Значок установки локального пути к каталогу](./media/user-guide/fx-events/image27.png)    | <span data-ttu-id="d83b7-163">**Установка локального пути к каталогу** (*fx_directory_local_path_set*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-163">**Directory Local Path Set** (*fx_directory_local_path_set*)</span></span> |
| ![Значок получения полного имени каталога](./media/user-guide/fx-events/image28.png)    | <span data-ttu-id="d83b7-165">**Получение полного имени каталога** (*fx_directory_long_name_get*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-165">**Directory Long Name Get** (*fx_directory_long_name_get*)</span></span> |
| ![Значок проверки имени каталога](./media/user-guide/fx-events/image29.png)    | <span data-ttu-id="d83b7-167">**Проверка имени каталога** (*fx_directory_name_test*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-167">**Directory Name Test** (*fx_directory_name_test*)</span></span> |
| ![Значок поиска следующей записи каталога](./media/user-guide/fx-events/image30.png)    | <span data-ttu-id="d83b7-169">**Поиск следующей записи каталога** (*fx_directory_next_entry_find*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-169">**Directory Next Entry Find** (*fx_directory_next_entry_find*)</span></span> |
| ![Значок поиска следующей полной записи каталога](./media/user-guide/fx-events/image31.png)    | <span data-ttu-id="d83b7-171">**Поиск следующей полной записи каталога** (*fx_directory_next_full_entry_find*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-171">**Directory Next Full Entry Find** (*fx_directory_next_full_entry_find*)</span></span> |
| ![Значок переименования каталога](./media/user-guide/fx-events/image32.png)    | <span data-ttu-id="d83b7-173">**Переименование каталога** (*fx_directory_rename*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-173">**Directory Rename** (*fx_directory_rename*)</span></span> |
| ![Значок получения краткого имени каталога](./media/user-guide/fx-events/image33.png)    | <span data-ttu-id="d83b7-175">**Получение краткого имени каталога** (*fx_directory_short_name_get*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-175">**Directory Short Name Get** (*fx_directory_short_name_get*)</span></span> |
| ![Значок выделения файла](./media/user-guide/fx-events/image34.png)    | <span data-ttu-id="d83b7-177">**Выделение файла** (*fx_file_allocate*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-177">**File Allocate** (*fx_file_allocate*)</span></span> |
| ![Значок чтения атрибутов файла](./media/user-guide/fx-events/image35.png)    | <span data-ttu-id="d83b7-179">**Чтение атрибутов файла** (*fx_file_attributes_read*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-179">**File Attributes Read** (*fx_file_attributes_read*)</span></span> |
| ![Значок установки атрибутов файла](./media/user-guide/fx-events/image36.png)    | <span data-ttu-id="d83b7-181">**Установка атрибутов файла** (*fx_file_attributes_set*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-181">**File Attributes Set** (*fx_file_attributes_set*)</span></span> |
| ![Значок негарантированного выделения файла](./media/user-guide/fx-events/image37.png)    | <span data-ttu-id="d83b7-183">**Негарантированное выделение файла** (*fx_file_best_effort_allocate*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-183">**File Best Effort Allocate** (*fx_file_best_effort_allocate*)</span></span> |
| ![Значок закрытия файла](./media/user-guide/fx-events/image38.png)    | <span data-ttu-id="d83b7-185">**Закрытие файла** (*fx_file_close*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-185">**File Close** (*fx_file_close*)</span></span> |
| ![Значок создания файла](./media/user-guide/fx-events/image39.png)    | <span data-ttu-id="d83b7-187">**Создание файла** (*fx_file_create*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-187">**File Create** (*fx_file_create*)</span></span> |
| ![Значок установки даты и времени для файла](./media/user-guide/fx-events/image40.png)    | <span data-ttu-id="d83b7-189">**Установка даты и времени для файла** (*fx_file_date_time_set*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-189">**File Date Time Set** (*fx_file_date_time_set*)</span></span> |
| ![Значок удаления файла](./media/user-guide/fx-events/image41.png)    | <span data-ttu-id="d83b7-191">**Удаление файла** (*fx_file_delete*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-191">**File Delete** (*fx_file_delete*)</span></span> |
| ![Значок открытия файла](./media/user-guide/fx-events/image42.png)    | <span data-ttu-id="d83b7-193">**Открытие файла** (*fx_file_open*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-193">**File Open** (*fx_file_open*)</span></span> |
| ![Значок чтения файла](./media/user-guide/fx-events/image43.png)    | <span data-ttu-id="d83b7-195">**Чтение файла** (*fx_file_read*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-195">**File Read** (*fx_file_read*)</span></span> |
| ![Значок относительного поиска в файле](./media/user-guide/fx-events/image44.png)    | <span data-ttu-id="d83b7-197">**Относительный поиск в файле** (*fx_file_relative_seek*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-197">**File Relative Seek** (*fx_file_relative_seek*)</span></span> |
| ![Значок переименования файла](./media/user-guide/fx-events/image45.png)    | <span data-ttu-id="d83b7-199">**Переименование файла** (*fx_file_rename*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-199">**File Rename** (*fx_file_rename*)</span></span> |
| ![Значок поиска в файле](./media/user-guide/fx-events/image46.png)    | <span data-ttu-id="d83b7-201">**Поиск в файле** (*fx_file_seek*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-201">**File Seek** (*fx_file_seek*)</span></span> |
| ![Значок усечения файла](./media/user-guide/fx-events/image47.png)    | <span data-ttu-id="d83b7-203">**Усечение файла** (*fx_file_truncate*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-203">**File Truncate** (*fx_file_truncate*)</span></span> |
| ![Значок освобождения усечения файла](./media/user-guide/fx-events/image48.png)    | <span data-ttu-id="d83b7-205">**Освобождение усечения файла** (*fx_file_truncate_release*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-205">**File Truncate Release** (*fx_file_truncate_release*)</span></span> |
| ![Значок записи файла](./media/user-guide/fx-events/image49.png)    | <span data-ttu-id="d83b7-207">**Запись файла** (*fx_file_write*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-207">**File Write** (*fx_file_write*)</span></span> |
| ![Значок прерывания носителя](./media/user-guide/fx-events/image50.png)    | <span data-ttu-id="d83b7-209">**Прерывание носителя** (*fx_media_abort*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-209">**Media Abort** (*fx_media_abort*)</span></span> |
| ![Значок недействительности кэша носителя](./media/user-guide/fx-events/image51.png)    | <span data-ttu-id="d83b7-211">**Недействительность кэша носителя** (*fx_media_cache_invalidate*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-211">**Media Cache Invalidate** (*fx_media_cache_invalidate*)</span></span> |
| ![Значок проверки носителя](./media/user-guide/fx-events/image52.png)    | <span data-ttu-id="d83b7-213">**Проверка носителя** (*fx_media_check*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-213">**Media Check** (*fx_media_check*)</span></span> |
| ![\*Значок закрытия носителя](./media/user-guide/fx-events/image53.png)    | <span data-ttu-id="d83b7-215">**Закрытие носителя** (*fx_media_close*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-215">**Media Close** (*fx_media_close*)</span></span> |
| ![Значок очистки носителя](./media/user-guide/fx-events/image54.png)    | <span data-ttu-id="d83b7-217">**Очистка носителя** (*fx_media_flush*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-217">**Media Flush** (*fx_media_flush*)</span></span> |
| ![Значок форматирования носителя](./media/user-guide/fx-events/image55.png)    | <span data-ttu-id="d83b7-219">**Форматирование носителя** (*fx_media_format*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-219">**Media Format** (*fx_media_format*)</span></span> |
| ![Значок открытия носителя](./media/user-guide/fx-events/image56.png)    | <span data-ttu-id="d83b7-221">**Открытие носителя** (*fx_media_open*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-221">**Media Open** (*fx_media_open*)</span></span> |
| ![Значок чтения носителя](./media/user-guide/fx-events/image57.png)    | <span data-ttu-id="d83b7-223">**Чтение носителя** (*fx_media_read*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-223">**Media Read** (*fx_media_read*)</span></span> |
| ![Значок доступного места на носителе](./media/user-guide/fx-events/image58.png)    | <span data-ttu-id="d83b7-225">**Доступное место на носителе** (*fx_media_space_available*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-225">**Media Space Available** (*fx_media_space_available*)</span></span> |
| ![Значок получения тома на носителе](./media/user-guide/fx-events/image59.png)    | <span data-ttu-id="d83b7-227">**Получение тома на носителе** (*fx_media_volume_get*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-227">**Media Volume Get** (*fx_media_volume_get*)</span></span> |
| ![Значок установки тома на носителе](./media/user-guide/fx-events/image60.png)    | <span data-ttu-id="d83b7-229">**Установка тома на носителе** (*fx_media_volume_set*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-229">**Media Volume Set** (*fx_media_volume_set*)</span></span> |
| ![Значок записи на носитель.](./media/user-guide/fx-events/image61.png)    | <span data-ttu-id="d83b7-231">**Запись на носитель** (*fx_media_write*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-231">**Media Write** (*fx_media_write*)</span></span> |
| ![Значок получения системной даты](./media/user-guide/fx-events/image62.png)    | <span data-ttu-id="d83b7-233">**Получение системной даты** (*fx_system_date_get*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-233">**System Date Get** (*fx_system_date_get*)</span></span> |
| ![Значок установки системной даты](./media/user-guide/fx-events/image63.png)    | <span data-ttu-id="d83b7-235">**Установка системной даты** (*fx_system_date_set*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-235">**System Date Set** (*fx_system_date_set*)</span></span> |
| ![Значок инициализации системы](./media/user-guide/fx-events/image64.png)    | <span data-ttu-id="d83b7-237">**Инициализация системы** (*fx_system_initialize*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-237">**System Initialize** (*fx_system_initialize*)</span></span> |
| ![Значок получения системного времени](./media/user-guide/fx-events/image65.png)    | <span data-ttu-id="d83b7-239">**Получение системного времени** (*fx_system_time_get*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-239">**System Time Get** (*fx_system_time_get*)</span></span> |
| ![Значок установки системного времени](./media/user-guide/fx-events/image66.png)    | <span data-ttu-id="d83b7-241">**Установка системного времени** (*fx_system_time_set*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-241">**System Time Set** (*fx_system_time_set*)</span></span> |
| ![Значок создания каталога Юникода](./media/user-guide/fx-events/image67.png)    | <span data-ttu-id="d83b7-243">**Создание каталога Юникода** (*fx_unicode_directory_create*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-243">**Unicode Directory Create** (*fx_unicode_directory_create*)</span></span> |
| ![Значок переименования каталога Юникода](./media/user-guide/fx-events/image68.png)    | <span data-ttu-id="d83b7-245">**Переименование каталога Юникода** (*fx_unicode_directory_rename*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-245">**Unicode Directory Rename** (*fx_unicode_directory_rename*)</span></span> |
| ![Значок создания файла Юникода](./media/user-guide/fx-events/image69.png)    | <span data-ttu-id="d83b7-247">**Создание файла Юникода** (*fx_unicode_file_create*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-247">**Unicode File Create** (*fx_unicode_file_create*)</span></span> |
| ![Значок переименования файла Юникода](./media/user-guide/fx-events/image70.png)    | <span data-ttu-id="d83b7-249">**Переименование файла Юникода** (*fx_unicode_file_rename*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-249">**Unicode File Rename** (*fx_unicode_file_rename*)</span></span> |
| ![Значок получения длина Юникода](./media/user-guide/fx-events/image71.png)    | <span data-ttu-id="d83b7-251">**Получение длины Юникода** (*fx_unicode_length_get*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-251">**Unicode Lenght Get** (*fx_unicode_length_get*)</span></span> |
| ![Значок получения имени Юникода](./media/user-guide/fx-events/image72.png)    | <span data-ttu-id="d83b7-253">**Получение имени Юникода** (*fx_unicode_name_get*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-253">**Unicode Name Get** (*fx_unicode_name_get*)</span></span> |
| ![Значок получения краткого имени Юникода](./media/user-guide/fx-events/image73.png)    | <span data-ttu-id="d83b7-255">**Получение краткого имени Юникода** (*fx_unicode_short_name_get*)</span><span class="sxs-lookup"><span data-stu-id="d83b7-255">**Unicode Short Name Get** (*fx_unicode_short_name_get*)</span></span> |

## <a name="event-descriptions"></a><span data-ttu-id="d83b7-256">Описания событий</span><span class="sxs-lookup"><span data-stu-id="d83b7-256">Event Descriptions</span></span>

<span data-ttu-id="d83b7-257">Ниже приводится описание каждого отдельного события.</span><span class="sxs-lookup"><span data-stu-id="d83b7-257">The following describes each individual event.</span></span>

### <a name="internal-logical-sector-cache-miss"></a><span data-ttu-id="d83b7-258">Промах внутреннего кэша логического сектора</span><span class="sxs-lookup"><span data-stu-id="d83b7-258">Internal Logical Sector Cache Miss</span></span> 

#### <a name="internal-logical-sector-cache-miss"></a><span data-ttu-id="d83b7-259">Промах внутреннего кэша логического сектора</span><span class="sxs-lookup"><span data-stu-id="d83b7-259">Internal logical sector cache miss</span></span>

<span data-ttu-id="d83b7-260">**Значок** ![Значок промаха внутреннего кэша логического сектора](./media/user-guide/fx-events/image1.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-260">**Icon** ![Internal logical sector cache miss icon](./media/user-guide/fx-events/image1.png)</span></span>

<span data-ttu-id="d83b7-261">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-261">**Description**</span></span>

<span data-ttu-id="d83b7-262">Это событие представляет промах внутреннего кэша логического сектора FileX.</span><span class="sxs-lookup"><span data-stu-id="d83b7-262">This event represents an internal FileX logical sector cache miss.</span></span>

<span data-ttu-id="d83b7-263">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-263">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-264">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-264">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-265">Поле сведений 2. Сектор.</span><span class="sxs-lookup"><span data-stu-id="d83b7-265">Info Field 2: Sector.</span></span>
- <span data-ttu-id="d83b7-266">Поле сведений 3. Общее количество промахов.</span><span class="sxs-lookup"><span data-stu-id="d83b7-266">Info Field 3: Total misses.</span></span>
- <span data-ttu-id="d83b7-267">Поле сведений 4. Размер кэша.</span><span class="sxs-lookup"><span data-stu-id="d83b7-267">Info Field 4: Cache size.</span></span>

### <a name="internal-directory-cache-miss"></a><span data-ttu-id="d83b7-268">Промах внутреннего кэша каталога</span><span class="sxs-lookup"><span data-stu-id="d83b7-268">Internal Directory Cache Miss</span></span>

#### <a name="internal-directory-cache-miss"></a><span data-ttu-id="d83b7-269">Промах внутреннего кэша каталога</span><span class="sxs-lookup"><span data-stu-id="d83b7-269">Internal directory cache miss</span></span>

<span data-ttu-id="d83b7-270">**Значок** ![Значок промаха внутреннего кэша каталога](./media/user-guide/fx-events/image2.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-270">**Icon** ![Internal directory cache miss icon](./media/user-guide/fx-events/image2.png)</span></span>

<span data-ttu-id="d83b7-271">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-271">**Description**</span></span> 

<span data-ttu-id="d83b7-272">Это событие представляет промах внутреннего кэша каталога FileX.</span><span class="sxs-lookup"><span data-stu-id="d83b7-272">This event represents an internal FileX directory cache miss.</span></span>

<span data-ttu-id="d83b7-273">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-273">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-274">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-274">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-275">Поле сведений 2. Общее количество промахов.</span><span class="sxs-lookup"><span data-stu-id="d83b7-275">Info Field 2: Total misses.</span></span>
- <span data-ttu-id="d83b7-276">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-276">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-277">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-277">Info Field 4: Not used.</span></span>

### <a name="internal-media-flush"></a><span data-ttu-id="d83b7-278">Очистка внутреннего носителя</span><span class="sxs-lookup"><span data-stu-id="d83b7-278">Internal Media Flush</span></span> 

#### <a name="internal-media-flush"></a><span data-ttu-id="d83b7-279">Очистка внутреннего носителя</span><span class="sxs-lookup"><span data-stu-id="d83b7-279">Internal media flush</span></span>

<span data-ttu-id="d83b7-280">**Значок** ![Значок очистки внутреннего носителя](./media/user-guide/fx-events/image3.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-280">**Icon** ![Internal media flush icon](./media/user-guide/fx-events/image3.png)</span></span>

<span data-ttu-id="d83b7-281">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-281">**Description**</span></span>

<span data-ttu-id="d83b7-282">Это событие представляет очистку внутреннего носителя FileX.</span><span class="sxs-lookup"><span data-stu-id="d83b7-282">This event represents an internal FileX media flush.</span></span>

<span data-ttu-id="d83b7-283">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-283">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-284">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-284">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-285">Поле сведений 2. Количество измененных секторов.</span><span class="sxs-lookup"><span data-stu-id="d83b7-285">Info Field 2: Number of dirty sectors.</span></span>
- <span data-ttu-id="d83b7-286">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-286">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-287">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-287">Info Field 4: Not used.</span></span>


### <a name="internal-directory-entry-read"></a><span data-ttu-id="d83b7-288">Чтение записи внутреннего каталога</span><span class="sxs-lookup"><span data-stu-id="d83b7-288">Internal Directory Entry Read</span></span> 

#### <a name="internal-directory-entry-read"></a><span data-ttu-id="d83b7-289">Чтение записи внутреннего каталога</span><span class="sxs-lookup"><span data-stu-id="d83b7-289">Internal directory entry read</span></span>

<span data-ttu-id="d83b7-290">**Значок** ![Значок чтения записи внутреннего каталога](./media/user-guide/fx-events/image4.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-290">**Icon** ![Internal directory entry read icon](./media/user-guide/fx-events/image4.png)</span></span>

<span data-ttu-id="d83b7-291">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-291">**Description**</span></span>

<span data-ttu-id="d83b7-292">Это событие представляет событие чтения записи каталога FileX.</span><span class="sxs-lookup"><span data-stu-id="d83b7-292">This event represents an internal FileX directory entry read event.</span></span>

<span data-ttu-id="d83b7-293">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-293">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-294">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-294">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-295">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-295">Info Field 2: Not used.</span></span>
- <span data-ttu-id="d83b7-296">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-296">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-297">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-297">Info Field 4: Not used.</span></span>

### <a name="internal-directory-entry-write"></a><span data-ttu-id="d83b7-298">Запись внутреннего каталога</span><span class="sxs-lookup"><span data-stu-id="d83b7-298">Internal Directory Entry Write</span></span>

#### <a name="internal-directory-entry-write"></a><span data-ttu-id="d83b7-299">Запись внутреннего каталога</span><span class="sxs-lookup"><span data-stu-id="d83b7-299">Internal directory entry write</span></span>

<span data-ttu-id="d83b7-300">**Значок** ![Значок записи внутреннего каталога](./media/user-guide/fx-events/image5.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-300">**Icon** ![Internal directory entry write icon](./media/user-guide/fx-events/image5.png)</span></span>

<span data-ttu-id="d83b7-301">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-301">**Description**</span></span>

<span data-ttu-id="d83b7-302">Это событие представляет событие записи каталога FileX.</span><span class="sxs-lookup"><span data-stu-id="d83b7-302">This event represents an internal FileX directory entry write event.</span></span>

<span data-ttu-id="d83b7-303">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-303">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-304">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-304">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-305">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-305">Info Field 2: Not used.</span></span>
- <span data-ttu-id="d83b7-306">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-306">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-307">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-307">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-read"></a><span data-ttu-id="d83b7-308">Чтение внутреннего драйвера ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="d83b7-308">Internal I/O Driver Read</span></span> 

#### <a name="internal-io-driver-read"></a><span data-ttu-id="d83b7-309">Чтение внутреннего драйвера ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="d83b7-309">Internal I/O driver read</span></span> 

<span data-ttu-id="d83b7-310">**Значок** ![Значок чтения внутреннего драйвера ввода-вывода](./media/user-guide/fx-events/image6.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-310">**Icon** ![Internal I / O driver read icon](./media/user-guide/fx-events/image6.png)</span></span>

<span data-ttu-id="d83b7-311">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-311">**Description**</span></span> 

<span data-ttu-id="d83b7-312">Это событие представляет событие чтения внутреннего драйвера ввода-вывода FileX.</span><span class="sxs-lookup"><span data-stu-id="d83b7-312">This event represents an internal FileX I/O driver read event.</span></span>

<span data-ttu-id="d83b7-313">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-313">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-314">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-314">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-315">Поле сведений 2. Сектор.</span><span class="sxs-lookup"><span data-stu-id="d83b7-315">Info Field 2: Sector.</span></span>
- <span data-ttu-id="d83b7-316">Поле сведений 3. Количество секторов.</span><span class="sxs-lookup"><span data-stu-id="d83b7-316">Info Field 3: Number of sectors.</span></span>
- <span data-ttu-id="d83b7-317">Поле сведений 4. Указатель на буфер.</span><span class="sxs-lookup"><span data-stu-id="d83b7-317">Info Field 4: Buffer pointer.</span></span>

### <a name="internal-io-driver-write"></a><span data-ttu-id="d83b7-318">Запись внутреннего драйвера ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="d83b7-318">Internal I/O Driver Write</span></span> 

#### <a name="internal-io-driver-write"></a><span data-ttu-id="d83b7-319">Запись внутреннего драйвера ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="d83b7-319">Internal I/O driver write</span></span> 

<span data-ttu-id="d83b7-320">**Значок** ![Значок записи внутреннего драйвера ввода-вывода](./media/user-guide/fx-events/image7.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-320">**Icon** ![Internal I / O driver write icon](./media/user-guide/fx-events/image7.png)</span></span>

<span data-ttu-id="d83b7-321">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-321">**Description**</span></span> 

<span data-ttu-id="d83b7-322">Это событие представляет событие записи внутреннего драйвера ввода-вывода FileX.</span><span class="sxs-lookup"><span data-stu-id="d83b7-322">This event represents an internal FileX I/O driver write event.</span></span>

<span data-ttu-id="d83b7-323">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-323">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-324">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-324">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-325">Поле сведений 2. Сектор.</span><span class="sxs-lookup"><span data-stu-id="d83b7-325">Info Field 2: Sector.</span></span>
- <span data-ttu-id="d83b7-326">Поле сведений 3. Количество секторов.</span><span class="sxs-lookup"><span data-stu-id="d83b7-326">Info Field 3: Number of sectors.</span></span>
- <span data-ttu-id="d83b7-327">Поле сведений 4. Указатель на буфер.</span><span class="sxs-lookup"><span data-stu-id="d83b7-327">Info Field 4: Buffer pointer.</span></span>

### <a name="internal-io-driver-flush"></a><span data-ttu-id="d83b7-328">Очистка внутреннего драйвера ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="d83b7-328">Internal I/O Driver Flush</span></span> 

#### <a name="internal-io-driver-flush"></a><span data-ttu-id="d83b7-329">Очистка внутреннего драйвера ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="d83b7-329">Internal I/O driver flush</span></span> 

<span data-ttu-id="d83b7-330">**Значок** ![Значок очистки внутреннего драйвера ввода-вывода](./media/user-guide/fx-events/image8.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-330">**Icon** ![Internal I / O driver flush icon](./media/user-guide/fx-events/image8.png)</span></span>

<span data-ttu-id="d83b7-331">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-331">**Description**</span></span> 

<span data-ttu-id="d83b7-332">Это событие представляет событие очистки внутреннего драйвера ввода-вывода FileX.</span><span class="sxs-lookup"><span data-stu-id="d83b7-332">This event represents an internal FileX I/O driver flush event.</span></span>

<span data-ttu-id="d83b7-333">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-333">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-334">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-334">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-335">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-335">Info Field 2: Not used.</span></span>
- <span data-ttu-id="d83b7-336">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-336">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-337">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-337">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-abort"></a><span data-ttu-id="d83b7-338">Прерывание внутреннего драйвера ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="d83b7-338">Internal I/O Driver Abort</span></span> 

#### <a name="internal-io-dirver-abort"></a><span data-ttu-id="d83b7-339">Прерывание внутреннего драйвера ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="d83b7-339">Internal I/O dirver abort</span></span>

<span data-ttu-id="d83b7-340">**Значок** ![Значок прерывания внутреннего драйвера ввода-вывода](./media/user-guide/fx-events/image9.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-340">**Icon** ![Internal I / O driver abort icon](./media/user-guide/fx-events/image9.png)</span></span>

<span data-ttu-id="d83b7-341">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-341">**Description**</span></span>

<span data-ttu-id="d83b7-342">Это событие представляет событие прерывания внутреннего драйвера ввода-вывода FileX.</span><span class="sxs-lookup"><span data-stu-id="d83b7-342">This event represents an internal FileX I/O driver abort event.</span></span>

<span data-ttu-id="d83b7-343">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-343">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-344">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-344">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-345">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-345">Info Field 2: Not used.</span></span>
- <span data-ttu-id="d83b7-346">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-346">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-347">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-347">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-initialize"></a><span data-ttu-id="d83b7-348">Инициализация внутреннего драйвера ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="d83b7-348">Internal I/O Driver Initialize</span></span> 

#### <a name="internal-io-driver-initialize"></a><span data-ttu-id="d83b7-349">Инициализация внутреннего драйвера ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="d83b7-349">Internal I/O driver initialize</span></span> 

<span data-ttu-id="d83b7-350">**Значок** ![Значок инициализации внутреннего драйвера ввода-вывода](./media/user-guide/fx-events/image10.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-350">**Icon** ![Internal I / O driver initialize icon](./media/user-guide/fx-events/image10.png)</span></span>

<span data-ttu-id="d83b7-351">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-351">**Description**</span></span> 

<span data-ttu-id="d83b7-352">Это событие представляет событие инициализации внутреннего драйвера ввода-вывода FileX.</span><span class="sxs-lookup"><span data-stu-id="d83b7-352">This event represents an internal FileX I/O driver initialize event.</span></span>

<span data-ttu-id="d83b7-353">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-353">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-354">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-354">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-355">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-355">Info Field 2: Not used.</span></span>
- <span data-ttu-id="d83b7-356">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-356">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-357">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-357">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-boot-sector-read"></a><span data-ttu-id="d83b7-358">Чтение загрузочного сектора внутреннего драйвера ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="d83b7-358">Internal I/O Driver Boot Sector Read</span></span> 

#### <a name="internal-io-driver-boot-sector-read"></a><span data-ttu-id="d83b7-359">Чтение загрузочного сектора внутреннего драйвера ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="d83b7-359">Internal I/O driver boot sector read</span></span> 

<span data-ttu-id="d83b7-360">**Значок** ![Значок чтения загрузочного сектора внутреннего драйвера ввода-вывода](./media/user-guide/fx-events/image11.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-360">**Icon** ![Internal I / O driver boot sector read icon](./media/user-guide/fx-events/image11.png)</span></span>

<span data-ttu-id="d83b7-361">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-361">**Description**</span></span> 

<span data-ttu-id="d83b7-362">Это событие представляет событие чтения загрузочного сектора внутреннего драйвера ввода-вывода FileX.</span><span class="sxs-lookup"><span data-stu-id="d83b7-362">This event represents an internal FileX I/O driver boot sector read event.</span></span>

<span data-ttu-id="d83b7-363">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-363">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-364">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-364">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-365">Поле сведений 2. Указатель на буфер.</span><span class="sxs-lookup"><span data-stu-id="d83b7-365">Info Field 2: Buffer pointer.</span></span>
- <span data-ttu-id="d83b7-366">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-366">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-367">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-367">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-release-sectors"></a><span data-ttu-id="d83b7-368">Освобождение секторов внутреннего драйвера ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="d83b7-368">Internal I/O Driver Release Sectors</span></span> 

#### <a name="internal-io-driver-release-sectors"></a><span data-ttu-id="d83b7-369">Освобождение секторов внутреннего драйвера ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="d83b7-369">Internal I/O driver release sectors</span></span> 

<span data-ttu-id="d83b7-370">**Значок** ![Значок освобождения секторов внутреннего драйвера ввода-вывода](./media/user-guide/fx-events/image12.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-370">**Icon** ![Internal I / O driver release sectors icon](./media/user-guide/fx-events/image12.png)</span></span>

<span data-ttu-id="d83b7-371">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-371">**Description**</span></span> 

<span data-ttu-id="d83b7-372">Это событие представляет событие освобождения секторов внутреннего драйвера ввода-вывода FileX.</span><span class="sxs-lookup"><span data-stu-id="d83b7-372">This event represents an internal FileX I/O driver release sectors event.</span></span>

<span data-ttu-id="d83b7-373">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-373">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-374">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-374">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-375">Поле сведений 2. Сектор.</span><span class="sxs-lookup"><span data-stu-id="d83b7-375">Info Field 2: Sector.</span></span>
- <span data-ttu-id="d83b7-376">Поле сведений 3. Количество секторов.</span><span class="sxs-lookup"><span data-stu-id="d83b7-376">Info Field 3: Number of sectors.</span></span>
- <span data-ttu-id="d83b7-377">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-377">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-boot-sector-write"></a><span data-ttu-id="d83b7-378">Запись загрузочного сектора внутреннего драйвера ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="d83b7-378">Internal I/O Driver Boot Sector Write</span></span>

#### <a name="internal-io-driver-boot-sector-write"></a><span data-ttu-id="d83b7-379">Запись загрузочного сектора внутреннего драйвера ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="d83b7-379">Internal I/O driver boot sector write</span></span> 

<span data-ttu-id="d83b7-380">**Значок** ![Значок записи загрузочного сектора внутреннего драйвера ввода-вывода](./media/user-guide/fx-events/image13.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-380">**Icon** ![Internal I / O driver boot sector write icon](./media/user-guide/fx-events/image13.png)</span></span>

<span data-ttu-id="d83b7-381">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-381">**Description**</span></span> 

<span data-ttu-id="d83b7-382">Это событие представляет событие записи загрузочного сектора внутреннего драйвера ввода-вывода FileX.</span><span class="sxs-lookup"><span data-stu-id="d83b7-382">This event represents an internal FileX I/O driver boot sector write event.</span></span>

<span data-ttu-id="d83b7-383">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-383">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-384">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-384">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-385">Поле сведений 2. Указатель на буфер.</span><span class="sxs-lookup"><span data-stu-id="d83b7-385">Info Field 2: Buffer pointer.</span></span>
- <span data-ttu-id="d83b7-386">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-386">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-387">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-387">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-un-initialize"></a><span data-ttu-id="d83b7-388">Отмена инициализации внутреннего драйвера ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="d83b7-388">Internal I/O Driver Un-initialize</span></span> 

#### <a name="internal-io-driver-un-initialize"></a><span data-ttu-id="d83b7-389">Отмена инициализации внутреннего драйвера ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="d83b7-389">Internal I/O driver un-initialize</span></span> 

<span data-ttu-id="d83b7-390">**Значок** ![Значок отмены инициализации внутреннего драйвера ввода-вывода](./media/user-guide/fx-events/image14.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-390">**Icon** ![Internal I / O driver un-initialize icon](./media/user-guide/fx-events/image14.png)</span></span>

<span data-ttu-id="d83b7-391">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-391">**Description**</span></span> 

<span data-ttu-id="d83b7-392">Это событие представляет событие отмены инициализации внутреннего драйвера ввода-вывода FileX.</span><span class="sxs-lookup"><span data-stu-id="d83b7-392">This event represents an internal FileX I/O driver un-initialize event.</span></span>

<span data-ttu-id="d83b7-393">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-393">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-394">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-394">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-395">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-395">Info Field 2: Not used.</span></span>
- <span data-ttu-id="d83b7-396">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-396">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-397">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-397">Info Field 4: Not used.</span></span>
</blockquote></td>

### <a name="directory-attributes-read"></a><span data-ttu-id="d83b7-398">Чтение атрибутов каталога</span><span class="sxs-lookup"><span data-stu-id="d83b7-398">Directory Attributes Read</span></span> 

#### <a name="fx_directory_attributes_read"></a><span data-ttu-id="d83b7-399">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="d83b7-399">fx_directory_attributes_read</span></span> 

<span data-ttu-id="d83b7-400">**Значок** ![Значок чтения атрибутов каталога](./media/user-guide/fx-events/image15.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-400">**Icon** ![Directory attributes read icon](./media/user-guide/fx-events/image15.png)</span></span>

<span data-ttu-id="d83b7-401">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-401">**Description**</span></span> 

<span data-ttu-id="d83b7-402">Это событие представляет событие чтения атрибутов каталога.</span><span class="sxs-lookup"><span data-stu-id="d83b7-402">This event represents a directory attributes read event.</span></span>

<span data-ttu-id="d83b7-403">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-403">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-404">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-404">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-405">Поле сведений 2. Указатель на имя каталога.</span><span class="sxs-lookup"><span data-stu-id="d83b7-405">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="d83b7-406">Поле сведений 3. Битовая схема атрибутов:</span><span class="sxs-lookup"><span data-stu-id="d83b7-406">Info Field 3: Attributes bit map:</span></span>

  | <span data-ttu-id="d83b7-407">attribute</span><span class="sxs-lookup"><span data-stu-id="d83b7-407">Attribute</span></span>                         | <span data-ttu-id="d83b7-408">Значение</span><span class="sxs-lookup"><span data-stu-id="d83b7-408">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="d83b7-409">Только для чтения</span><span class="sxs-lookup"><span data-stu-id="d83b7-409">Read Only</span></span>                        | <span data-ttu-id="d83b7-410">(0x01)</span><span class="sxs-lookup"><span data-stu-id="d83b7-410">(0x01)</span></span>  |
  |  <span data-ttu-id="d83b7-411">Скрытый</span><span class="sxs-lookup"><span data-stu-id="d83b7-411">Hidden</span></span>                           | <span data-ttu-id="d83b7-412">(0x02)</span><span class="sxs-lookup"><span data-stu-id="d83b7-412">(0x02)</span></span>  |
  |  <span data-ttu-id="d83b7-413">Система</span><span class="sxs-lookup"><span data-stu-id="d83b7-413">System</span></span>                           | <span data-ttu-id="d83b7-414">(0x04)</span><span class="sxs-lookup"><span data-stu-id="d83b7-414">(0x04)</span></span>  |
  |  <span data-ttu-id="d83b7-415">Том</span><span class="sxs-lookup"><span data-stu-id="d83b7-415">Volume</span></span>                           | <span data-ttu-id="d83b7-416">(0x08)</span><span class="sxs-lookup"><span data-stu-id="d83b7-416">(0x08)</span></span>  |
  |  <span data-ttu-id="d83b7-417">Каталог</span><span class="sxs-lookup"><span data-stu-id="d83b7-417">Directory</span></span>                        | <span data-ttu-id="d83b7-418">(0x10)</span><span class="sxs-lookup"><span data-stu-id="d83b7-418">(0x10)</span></span>  |
  |  <span data-ttu-id="d83b7-419">Архив</span><span class="sxs-lookup"><span data-stu-id="d83b7-419">Archive</span></span>                          | <span data-ttu-id="d83b7-420">(0x20)</span><span class="sxs-lookup"><span data-stu-id="d83b7-420">(0x20)</span></span>  |
- <span data-ttu-id="d83b7-421">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-421">Info Field 4: Not used.</span></span>

### <a name="directory-attributes-set"></a><span data-ttu-id="d83b7-422">Установка атрибутов каталога</span><span class="sxs-lookup"><span data-stu-id="d83b7-422">Directory Attributes Set</span></span> 

#### <a name="fx_directory_attributes_set"></a><span data-ttu-id="d83b7-423">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="d83b7-423">fx_directory_attributes_set</span></span> 

<span data-ttu-id="d83b7-424">**Значок установки атрибутов файла** ![Значок установки атрибутов](./media/user-guide/fx-events/image16.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-424">**Icon** ![Attributes set icon](./media/user-guide/fx-events/image16.png)</span></span>

<span data-ttu-id="d83b7-425">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-425">**Description**</span></span> 

<span data-ttu-id="d83b7-426">Это событие представляет событие установки атрибутов каталога.</span><span class="sxs-lookup"><span data-stu-id="d83b7-426">This event represents a directory a directory attributes set event.</span></span>

<span data-ttu-id="d83b7-427">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-427">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-428">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-428">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-429">Поле сведений 2. Указатель на имя каталога.</span><span class="sxs-lookup"><span data-stu-id="d83b7-429">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="d83b7-430">Поле сведений 3. Битовая схема атрибутов:</span><span class="sxs-lookup"><span data-stu-id="d83b7-430">Info Field 3: Attributes bit map:</span></span>

  |  <span data-ttu-id="d83b7-431">attribute</span><span class="sxs-lookup"><span data-stu-id="d83b7-431">Attribute</span></span>                        | <span data-ttu-id="d83b7-432">Значение</span><span class="sxs-lookup"><span data-stu-id="d83b7-432">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="d83b7-433">Только для чтения</span><span class="sxs-lookup"><span data-stu-id="d83b7-433">Read Only</span></span>                        | <span data-ttu-id="d83b7-434">(0x01)</span><span class="sxs-lookup"><span data-stu-id="d83b7-434">(0x01)</span></span>  |
  |  <span data-ttu-id="d83b7-435">Скрытый</span><span class="sxs-lookup"><span data-stu-id="d83b7-435">Hidden</span></span>                           | <span data-ttu-id="d83b7-436">(0x02)</span><span class="sxs-lookup"><span data-stu-id="d83b7-436">(0x02)</span></span>  |
  |  <span data-ttu-id="d83b7-437">Система</span><span class="sxs-lookup"><span data-stu-id="d83b7-437">System</span></span>                           | <span data-ttu-id="d83b7-438">(0x04)</span><span class="sxs-lookup"><span data-stu-id="d83b7-438">(0x04)</span></span>  |
  |  <span data-ttu-id="d83b7-439">Архив</span><span class="sxs-lookup"><span data-stu-id="d83b7-439">Archive</span></span>                          | <span data-ttu-id="d83b7-440">(0x20)</span><span class="sxs-lookup"><span data-stu-id="d83b7-440">(0x20)</span></span>  |
- <span data-ttu-id="d83b7-441">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-441">Info Field 4: Not used.</span></span>

### <a name="directory-create"></a><span data-ttu-id="d83b7-442">Создание каталога</span><span class="sxs-lookup"><span data-stu-id="d83b7-442">Directory Create</span></span> 

#### <a name="fx_directory_create"></a><span data-ttu-id="d83b7-443">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="d83b7-443">fx_directory_create</span></span>

<span data-ttu-id="d83b7-444">**Значок** ![Значок создания каталога](./media/user-guide/fx-events/image17.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-444">**Icon** ![Directory create icon](./media/user-guide/fx-events/image17.png)</span></span>

<span data-ttu-id="d83b7-445">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-445">**Description**</span></span> 

<span data-ttu-id="d83b7-446">Это событие представляет событие создания каталога.</span><span class="sxs-lookup"><span data-stu-id="d83b7-446">This event represents a directory create event.</span></span>

<span data-ttu-id="d83b7-447">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-447">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-448">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-448">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-449">Поле сведений 2. Указатель на имя каталога.</span><span class="sxs-lookup"><span data-stu-id="d83b7-449">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="d83b7-450">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-450">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-451">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-451">Info Field 4: Not used.</span></span>

### <a name="directory-default-get"></a><span data-ttu-id="d83b7-452">Получение каталога по умолчанию</span><span class="sxs-lookup"><span data-stu-id="d83b7-452">Directory Default Get</span></span> 

#### <a name="fx_directory_default_get"></a><span data-ttu-id="d83b7-453">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="d83b7-453">fx_directory_default_get</span></span> 

<span data-ttu-id="d83b7-454">**Значок** ![Значок получения каталога по умолчанию](./media/user-guide/fx-events/image18.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-454">**Icon** ![Directory default get icon](./media/user-guide/fx-events/image18.png)</span></span>

<span data-ttu-id="d83b7-455">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-455">**Description**</span></span> 

<span data-ttu-id="d83b7-456">Это событие представляет событие установки каталога по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="d83b7-456">This event represents a directory default set event.</span></span>

<span data-ttu-id="d83b7-457">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-457">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-458">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-458">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-459">Поле сведений 2. Указатель на имя возвращаемого пути.</span><span class="sxs-lookup"><span data-stu-id="d83b7-459">Info Field 2: Pointer to return path name.</span></span>
- <span data-ttu-id="d83b7-460">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-460">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-461">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-461">Info Field 4: Not used.</span></span>

### <a name="directory-default-set"></a><span data-ttu-id="d83b7-462">Установка каталога по умолчанию</span><span class="sxs-lookup"><span data-stu-id="d83b7-462">Directory Default Set</span></span> 

#### <a name="fx_directory_default_set"></a><span data-ttu-id="d83b7-463">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="d83b7-463">fx_directory_default_set</span></span> 

<span data-ttu-id="d83b7-464">**Значок** ![Значок установки каталога по умолчанию](./media/user-guide/fx-events/image19.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-464">**Icon** ![Directory default set icon](./media/user-guide/fx-events/image19.png)</span></span>

<span data-ttu-id="d83b7-465">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-465">**Description**</span></span> 

<span data-ttu-id="d83b7-466">Это событие представляет событие установки каталога по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="d83b7-466">This event represents a directory default set event.</span></span>

<span data-ttu-id="d83b7-467">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-467">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-468">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-468">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-469">Поле сведений 2. Указатель на имя нового пути по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="d83b7-469">Info Field 2: Pointer to new default path name.</span></span>
- <span data-ttu-id="d83b7-470">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-470">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-471">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-471">Info Field 4: Not used.</span></span>

### <a name="directory-delete"></a><span data-ttu-id="d83b7-472">Удаление каталога</span><span class="sxs-lookup"><span data-stu-id="d83b7-472">Directory Delete</span></span> 

#### <a name="fx_directory_delete"></a><span data-ttu-id="d83b7-473">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="d83b7-473">fx_directory_delete</span></span>

<span data-ttu-id="d83b7-474">**Значок** ![Значок удаления каталога](./media/user-guide/fx-events/image20.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-474">**Icon** ![Directory delete icon](./media/user-guide/fx-events/image20.png)</span></span>

<span data-ttu-id="d83b7-475">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-475">**Description**</span></span> 

<span data-ttu-id="d83b7-476">Это событие представляет событие удаления каталога.</span><span class="sxs-lookup"><span data-stu-id="d83b7-476">This event represents a directory delete event.</span></span>

<span data-ttu-id="d83b7-477">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-477">**Information Fields**</span></span>
- <span data-ttu-id="d83b7-478">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-478">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-479">Поле сведений 2. Указатель на имя каталога.</span><span class="sxs-lookup"><span data-stu-id="d83b7-479">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="d83b7-480">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-480">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-481">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-481">Info Field 4: Not used.</span></span>

### <a name="directory-first-entry-find"></a><span data-ttu-id="d83b7-482">Поиск в первой записи каталога</span><span class="sxs-lookup"><span data-stu-id="d83b7-482">Directory First Entry Find</span></span> 

#### <a name="fx_directory_first_entry_find"></a><span data-ttu-id="d83b7-483">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="d83b7-483">fx_directory_first_entry_find</span></span>

<span data-ttu-id="d83b7-484">**Значок** ![Значок поиска первой записи каталога](./media/user-guide/fx-events/image21.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-484">**Icon** ![Directory first entry find icon](./media/user-guide/fx-events/image21.png)</span></span>

<span data-ttu-id="d83b7-485">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-485">**Description**</span></span> 

<span data-ttu-id="d83b7-486">Это событие представляет событие поиска первой записи каталога.</span><span class="sxs-lookup"><span data-stu-id="d83b7-486">This event represents a directory first entry find event.</span></span>

<span data-ttu-id="d83b7-487">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-487">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-488">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-488">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-489">Поле сведений 2. Указатель на имя каталога.</span><span class="sxs-lookup"><span data-stu-id="d83b7-489">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="d83b7-490">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-490">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-491">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-491">Info Field 4: Not used.</span></span>

### <a name="directory-first-full-entry-find"></a><span data-ttu-id="d83b7-492">Поиск первой полной записи каталога</span><span class="sxs-lookup"><span data-stu-id="d83b7-492">Directory First Full Entry Find</span></span> 

#### <a name="fx_directory_first_full_entry_find"></a><span data-ttu-id="d83b7-493">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="d83b7-493">fx_directory_first_full_entry_find</span></span>

<span data-ttu-id="d83b7-494">**Значок** ![Значок поиска первой полной записи каталога](./media/user-guide/fx-events/image22.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-494">**Icon** ![Directory first full entry find icon](./media/user-guide/fx-events/image22.png)</span></span>

<span data-ttu-id="d83b7-495">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-495">**Description**</span></span> 

<span data-ttu-id="d83b7-496">Это событие представляет событие поиска первой полной записи каталога.</span><span class="sxs-lookup"><span data-stu-id="d83b7-496">This event represents a directory first full entry find event.</span></span>

<span data-ttu-id="d83b7-497">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-497">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-498">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-498">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-499">Поле сведений 2. Указатель на имя каталога.</span><span class="sxs-lookup"><span data-stu-id="d83b7-499">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="d83b7-500">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-500">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-501">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-501">Info Field 4: Not used.</span></span>

### <a name="directory-information-get"></a><span data-ttu-id="d83b7-502">Получение сведений о каталоге</span><span class="sxs-lookup"><span data-stu-id="d83b7-502">Directory Information Get</span></span> 

#### <a name="fx_directory_information_get"></a><span data-ttu-id="d83b7-503">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="d83b7-503">fx_directory_information_get</span></span>

<span data-ttu-id="d83b7-504">**Значок** ![Значок получения сведений о каталоге](./media/user-guide/fx-events/image23.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-504">**Icon** ![Directory information get icon](./media/user-guide/fx-events/image23.png)</span></span>

<span data-ttu-id="d83b7-505">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-505">**Description**</span></span> 

<span data-ttu-id="d83b7-506">Это событие представляет событие получения сведений о каталоге.</span><span class="sxs-lookup"><span data-stu-id="d83b7-506">This event represents a directory information get event.</span></span>

<span data-ttu-id="d83b7-507">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-507">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-508">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-508">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-509">Поле сведений 2. Указатель на имя каталога.</span><span class="sxs-lookup"><span data-stu-id="d83b7-509">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="d83b7-510">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-510">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-511">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-511">Info Field 4: Not used.</span></span>

### <a name="directory-local-path-clear"></a><span data-ttu-id="d83b7-512">Очистка локального пути к каталогу</span><span class="sxs-lookup"><span data-stu-id="d83b7-512">Directory Local Path Clear</span></span> 

#### <a name="fx_directory_local_path_clear"></a><span data-ttu-id="d83b7-513">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="d83b7-513">fx_directory_local_path_clear</span></span>

<span data-ttu-id="d83b7-514">**Значок** ![Значок очистки локального пути к каталогу](./media/user-guide/fx-events/image24.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-514">**Icon** ![Directory local path clear icon](./media/user-guide/fx-events/image24.png)</span></span>

<span data-ttu-id="d83b7-515">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-515">**Description**</span></span> 

<span data-ttu-id="d83b7-516">Это событие представляет событие очистки локального пути к каталогу.</span><span class="sxs-lookup"><span data-stu-id="d83b7-516">This event represents a directory local path clear event.</span></span>

<span data-ttu-id="d83b7-517">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-517">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-518">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-518">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-519">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-519">Info Field 2: Not used.</span></span>
- <span data-ttu-id="d83b7-520">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-520">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-521">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-521">Info Field 4: Not used.</span></span>

### <a name="directory-local-path-get"></a><span data-ttu-id="d83b7-522">Получение локального пути к каталогу</span><span class="sxs-lookup"><span data-stu-id="d83b7-522">Directory Local Path Get</span></span> 

#### <a name="fx_directory_local_path_get"></a><span data-ttu-id="d83b7-523">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="d83b7-523">fx_directory_local_path_get</span></span>

<span data-ttu-id="d83b7-524">**Значок** ![Значок получения локального пути к каталогу](./media/user-guide/fx-events/image25.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-524">**Icon** ![Directory local path get icon](./media/user-guide/fx-events/image25.png)</span></span>

<span data-ttu-id="d83b7-525">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-525">**Description**</span></span> 

<span data-ttu-id="d83b7-526">Это событие представляет событие получения локального пути к каталогу.</span><span class="sxs-lookup"><span data-stu-id="d83b7-526">This event represents a directory local path get event.</span></span>

<span data-ttu-id="d83b7-527">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-527">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-528">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-528">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-529">Поле сведений 2. Указатель на имя возвращаемого пути.</span><span class="sxs-lookup"><span data-stu-id="d83b7-529">Info Field 2: Pointer to return path name.</span></span>
- <span data-ttu-id="d83b7-530">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-530">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-531">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-531">Info Field 4: Not used.</span></span>

### <a name="directory-local-path-restore"></a><span data-ttu-id="d83b7-532">Восстановление локального пути к каталогу</span><span class="sxs-lookup"><span data-stu-id="d83b7-532">Directory Local Path Restore</span></span> 

#### <a name="fx_directory_local_path_restore"></a><span data-ttu-id="d83b7-533">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="d83b7-533">fx_directory_local_path_restore</span></span>

<span data-ttu-id="d83b7-534">**Значок** ![Значок восстановления локального пути к каталогу](./media/user-guide/fx-events/image26.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-534">**Icon** ![Directory local path restore icon](./media/user-guide/fx-events/image26.png)</span></span>

<span data-ttu-id="d83b7-535">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-535">**Description**</span></span> 

<span data-ttu-id="d83b7-536">Это событие представляет событие восстановления локального пути к каталогу.</span><span class="sxs-lookup"><span data-stu-id="d83b7-536">This event represents a directory local path restore event.</span></span>

<span data-ttu-id="d83b7-537">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-537">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-538">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-538">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-539">Поле сведений 2. Указатель на структуру локального пути.</span><span class="sxs-lookup"><span data-stu-id="d83b7-539">Info Field 2: Pointer to local path structure.</span></span>
- <span data-ttu-id="d83b7-540">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-540">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-541">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-541">Info Field 4: Not used.</span></span>

### <a name="directory-local-path-set"></a><span data-ttu-id="d83b7-542">Установка локального пути к каталогу</span><span class="sxs-lookup"><span data-stu-id="d83b7-542">Directory Local Path Set</span></span> 

#### <a name="fx_directory_local_path_set"></a><span data-ttu-id="d83b7-543">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="d83b7-543">fx_directory_local_path_set</span></span>

<span data-ttu-id="d83b7-544">**Значок** ![Значок установки локального пути к каталогу](./media/user-guide/fx-events/image27.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-544">**Icon** ![Directory local path set icon](./media/user-guide/fx-events/image27.png)</span></span>

<span data-ttu-id="d83b7-545">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-545">**Description**</span></span> 

<span data-ttu-id="d83b7-546">Это событие представляет событие установки локального пути к каталогу.</span><span class="sxs-lookup"><span data-stu-id="d83b7-546">This event represents a directory local path set event.</span></span>

<span data-ttu-id="d83b7-547">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-547">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-548">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-548">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-549">Поле сведений 2. Указатель на структуру локального пути.</span><span class="sxs-lookup"><span data-stu-id="d83b7-549">Info Field 2: Pointer to local path structure.</span></span>
- <span data-ttu-id="d83b7-550">Поле сведений 3. Указатель на имя нового пути.</span><span class="sxs-lookup"><span data-stu-id="d83b7-550">Info Field 3: Pointer to new path name.</span></span>
- <span data-ttu-id="d83b7-551">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-551">Info Field 4: Not used.</span></span>

### <a name="directory-long-name-get"></a><span data-ttu-id="d83b7-552">Получение полного имени каталога</span><span class="sxs-lookup"><span data-stu-id="d83b7-552">Directory Long Name Get</span></span> 

#### <a name="fx_directory_long_name_get"></a><span data-ttu-id="d83b7-553">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="d83b7-553">fx_directory_long_name_get</span></span>

<span data-ttu-id="d83b7-554">**Значок** ![Значок получения полного имени каталога](./media/user-guide/fx-events/image28.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-554">**Icon** ![Directory long name get icon](./media/user-guide/fx-events/image28.png)</span></span>

<span data-ttu-id="d83b7-555">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-555">**Description**</span></span> 

<span data-ttu-id="d83b7-556">Это событие представляет событие получения полного имени каталога.</span><span class="sxs-lookup"><span data-stu-id="d83b7-556">This event represents a directory long name get event.</span></span>

<span data-ttu-id="d83b7-557">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-557">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-558">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-558">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-559">Поле сведений 2. Указатель на краткое имя файла.</span><span class="sxs-lookup"><span data-stu-id="d83b7-559">Info Field 2: Pointer to short file name.</span></span>
- <span data-ttu-id="d83b7-560">Поле сведений 3. Указатель на полное имя файла.</span><span class="sxs-lookup"><span data-stu-id="d83b7-560">Info Field 3: Pointer to long file name.</span></span>
- <span data-ttu-id="d83b7-561">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-561">Info Field 4: Not used.</span></span>

### <a name="directory-name-test"></a><span data-ttu-id="d83b7-562">Проверка имени каталога</span><span class="sxs-lookup"><span data-stu-id="d83b7-562">Directory Name Test</span></span> 

#### <a name="fx_directory_name_test"></a><span data-ttu-id="d83b7-563">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="d83b7-563">fx_directory_name_test</span></span>

<span data-ttu-id="d83b7-564">**Значок** ![Значок проверки имени каталога](./media/user-guide/fx-events/image29.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-564">**Icon** ![Directory name test icon](./media/user-guide/fx-events/image29.png)</span></span>

<span data-ttu-id="d83b7-565">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-565">**Description**</span></span> 

<span data-ttu-id="d83b7-566">Это событие представляет событие проверки имени каталога.</span><span class="sxs-lookup"><span data-stu-id="d83b7-566">This event represents a directory name test event.</span></span>

<span data-ttu-id="d83b7-567">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-567">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-568">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-568">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-569">Поле сведений 2. Указатель на имя каталога.</span><span class="sxs-lookup"><span data-stu-id="d83b7-569">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="d83b7-570">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-570">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-571">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-571">Info Field 4: Not used.</span></span>

### <a name="directory-next-entry-find"></a><span data-ttu-id="d83b7-572">Поиск следующей записи каталога</span><span class="sxs-lookup"><span data-stu-id="d83b7-572">Directory Next Entry Find</span></span> 

#### <a name="fx_directory_next_entry_find"></a><span data-ttu-id="d83b7-573">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="d83b7-573">fx_directory_next_entry_find</span></span>

<span data-ttu-id="d83b7-574">**Значок** ![Значок поиска следующей записи каталога](./media/user-guide/fx-events/image30.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-574">**Icon** ![Directory next entry find icon](./media/user-guide/fx-events/image30.png)</span></span>

<span data-ttu-id="d83b7-575">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-575">**Description**</span></span> 

<span data-ttu-id="d83b7-576">Это событие представляет событие поиска следующей записи каталога.</span><span class="sxs-lookup"><span data-stu-id="d83b7-576">This event represents a directory next entry find event.</span></span>

<span data-ttu-id="d83b7-577">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-577">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-578">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-578">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-579">Поле сведений 2. Указатель на имя каталога.</span><span class="sxs-lookup"><span data-stu-id="d83b7-579">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="d83b7-580">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-580">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-581">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-581">Info Field 4: Not used.</span></span>

### <a name="directory-next-full-entry-find"></a><span data-ttu-id="d83b7-582">Поиск следующей полной записи каталога</span><span class="sxs-lookup"><span data-stu-id="d83b7-582">Directory Next Full Entry Find</span></span> 

#### <a name="fx_directory_next_full_entry_find"></a><span data-ttu-id="d83b7-583">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="d83b7-583">fx_directory_next_full_entry_find</span></span>

<span data-ttu-id="d83b7-584">**Значок** ![Значок поиска следующей полной записи каталога](./media/user-guide/fx-events/image31.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-584">**Icon** ![Directory next full entry find icon](./media/user-guide/fx-events/image31.png)</span></span>

<span data-ttu-id="d83b7-585">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-585">**Description**</span></span>

<span data-ttu-id="d83b7-586">Это событие представляет событие поиска следующей полной записи каталога.</span><span class="sxs-lookup"><span data-stu-id="d83b7-586">This event represents a directory next full entry find event.</span></span>

<span data-ttu-id="d83b7-587">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-587">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-588">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-588">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-589">Поле сведений 2. Указатель на имя каталога.</span><span class="sxs-lookup"><span data-stu-id="d83b7-589">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="d83b7-590">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-590">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-591">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-591">Info Field 4: Not used.</span></span>

### <a name="directory-rename"></a><span data-ttu-id="d83b7-592">Переименование каталога</span><span class="sxs-lookup"><span data-stu-id="d83b7-592">Directory Rename</span></span> 

#### <a name="fx_directory_rename-event"></a><span data-ttu-id="d83b7-593">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="d83b7-593">fx_directory_rename event</span></span>

<span data-ttu-id="d83b7-594">**Значок** ![Значок переименования каталога](./media/user-guide/fx-events/image32.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-594">**Icon** ![Directory rename icon](./media/user-guide/fx-events/image32.png)</span></span>

<span data-ttu-id="d83b7-595">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-595">**Description**</span></span>

<span data-ttu-id="d83b7-596">Это событие представляет событие переименования каталога.</span><span class="sxs-lookup"><span data-stu-id="d83b7-596">This event represents a directory rename event.</span></span>

<span data-ttu-id="d83b7-597">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-597">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-598">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-598">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-599">Поле сведений 2. Указатель на старое имя каталога.</span><span class="sxs-lookup"><span data-stu-id="d83b7-599">Info Field 2: Pointer to old directory name.</span></span>
- <span data-ttu-id="d83b7-600">Поле сведений 3. Указатель на новое имя каталога.</span><span class="sxs-lookup"><span data-stu-id="d83b7-600">Info Field 3: Pointer to new directory name.</span></span>
- <span data-ttu-id="d83b7-601">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-601">Info Field 4: Not used.</span></span>

### <a name="directory-short-name-get"></a><span data-ttu-id="d83b7-602">Получение краткого имени каталога</span><span class="sxs-lookup"><span data-stu-id="d83b7-602">Directory Short Name Get</span></span> 

#### <a name="fx_directory_short_name_get"></a><span data-ttu-id="d83b7-603">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="d83b7-603">fx_directory_short_name_get</span></span>

<span data-ttu-id="d83b7-604">**Значок** ![Значок получения краткого имени каталога](./media/user-guide/fx-events/image33.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-604">**Icon** ![Directory short name get icon](./media/user-guide/fx-events/image33.png)</span></span>

<span data-ttu-id="d83b7-605">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-605">**Description**</span></span>

<span data-ttu-id="d83b7-606">Это событие представляет событие получения краткого имени каталога.</span><span class="sxs-lookup"><span data-stu-id="d83b7-606">This event represents a directory short name get event.</span></span>

<span data-ttu-id="d83b7-607">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-607">**Information Fields**</span></span> 

- <span data-ttu-id="d83b7-608">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-608">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-609">Поле сведений 2. Указатель на полное имя файла.</span><span class="sxs-lookup"><span data-stu-id="d83b7-609">Info Field 2: Pointer to long file name.</span></span>
- <span data-ttu-id="d83b7-610">Поле сведений 3. Указатель на краткое имя файла.</span><span class="sxs-lookup"><span data-stu-id="d83b7-610">Info Field 3: Pointer to short file name.</span></span>
- <span data-ttu-id="d83b7-611">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-611">Info Field 4: Not used.</span></span>

### <a name="file-allocate"></a><span data-ttu-id="d83b7-612">Выделение файла</span><span class="sxs-lookup"><span data-stu-id="d83b7-612">File Allocate</span></span> 

#### <a name="fx_file_allocate"></a><span data-ttu-id="d83b7-613">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="d83b7-613">fx_file_allocate</span></span>

<span data-ttu-id="d83b7-614">**Значок** ![Значок выделения файла](./media/user-guide/fx-events/image34.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-614">**Icon** ![File allocate icon](./media/user-guide/fx-events/image34.png)</span></span>

<span data-ttu-id="d83b7-615">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-615">**Description**</span></span>

<span data-ttu-id="d83b7-616">Это событие представляет событие выделения файла.</span><span class="sxs-lookup"><span data-stu-id="d83b7-616">This event represents a file allocate event.</span></span>

<span data-ttu-id="d83b7-617">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-617">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-618">Поле сведений 1. Указатель на файл.</span><span class="sxs-lookup"><span data-stu-id="d83b7-618">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="d83b7-619">Поле сведений 2. Запрашиваемый размер.</span><span class="sxs-lookup"><span data-stu-id="d83b7-619">Info Field 2: Requested size.</span></span>
- <span data-ttu-id="d83b7-620">Поле сведений 3. Текущий размер.</span><span class="sxs-lookup"><span data-stu-id="d83b7-620">Info Field 3: Current size.</span></span>
- <span data-ttu-id="d83b7-621">Поле сведений 4. Новый размер.</span><span class="sxs-lookup"><span data-stu-id="d83b7-621">Info Field 4: New size.</span></span>

### <a name="file-attributes-read"></a><span data-ttu-id="d83b7-622">Чтение атрибутов файла</span><span class="sxs-lookup"><span data-stu-id="d83b7-622">File Attributes Read</span></span> 

#### <a name="fx_file_attributes_read"></a><span data-ttu-id="d83b7-623">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="d83b7-623">fx_file_attributes_read</span></span>

<span data-ttu-id="d83b7-624">**Значок** ![Значок чтения атрибутов файла](./media/user-guide/fx-events/image35.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-624">**Icon** ![File attributes read icon](./media/user-guide/fx-events/image35.png)</span></span>

<span data-ttu-id="d83b7-625">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-625">**Description**</span></span>

<span data-ttu-id="d83b7-626">Это событие представляет событие чтения атрибутов файла.</span><span class="sxs-lookup"><span data-stu-id="d83b7-626">This event represents a file attributes read event.</span></span>

<span data-ttu-id="d83b7-627">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-627">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-628">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-628">Info Field 1: Pointer to the media.</span></span> 
- <span data-ttu-id="d83b7-629">Поле сведений 2. Битовая схема атрибутов:</span><span class="sxs-lookup"><span data-stu-id="d83b7-629">Info Field 2: Attributes bit map:</span></span>

  |  <span data-ttu-id="d83b7-630">Атрибут</span><span class="sxs-lookup"><span data-stu-id="d83b7-630">Attribut</span></span>                         | <span data-ttu-id="d83b7-631">Значение</span><span class="sxs-lookup"><span data-stu-id="d83b7-631">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="d83b7-632">Только для чтения</span><span class="sxs-lookup"><span data-stu-id="d83b7-632">Read Only</span></span>                        | <span data-ttu-id="d83b7-633">(0x01)</span><span class="sxs-lookup"><span data-stu-id="d83b7-633">(0x01)</span></span>  |
  |  <span data-ttu-id="d83b7-634">Скрытый</span><span class="sxs-lookup"><span data-stu-id="d83b7-634">Hidden</span></span>                           | <span data-ttu-id="d83b7-635">(0x02)</span><span class="sxs-lookup"><span data-stu-id="d83b7-635">(0x02)</span></span>  |
  |  <span data-ttu-id="d83b7-636">Система</span><span class="sxs-lookup"><span data-stu-id="d83b7-636">System</span></span>                           | <span data-ttu-id="d83b7-637">(0x04)</span><span class="sxs-lookup"><span data-stu-id="d83b7-637">(0x04)</span></span>  |
  |  <span data-ttu-id="d83b7-638">Том</span><span class="sxs-lookup"><span data-stu-id="d83b7-638">Volume</span></span>                           | <span data-ttu-id="d83b7-639">(0x08)</span><span class="sxs-lookup"><span data-stu-id="d83b7-639">(0x08)</span></span>  |
  |  <span data-ttu-id="d83b7-640">Каталог</span><span class="sxs-lookup"><span data-stu-id="d83b7-640">Directory</span></span>                        | <span data-ttu-id="d83b7-641">(0x10)</span><span class="sxs-lookup"><span data-stu-id="d83b7-641">(0x10)</span></span>  |
  |  <span data-ttu-id="d83b7-642">Архив</span><span class="sxs-lookup"><span data-stu-id="d83b7-642">Archive</span></span>                          | <span data-ttu-id="d83b7-643">(0x20)</span><span class="sxs-lookup"><span data-stu-id="d83b7-643">(0x20)</span></span>  |
- <span data-ttu-id="d83b7-644">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-644">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-645">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-645">Info Field 4: Not used.</span></span>

### <a name="file-attributes-set"></a><span data-ttu-id="d83b7-646">Установка атрибутов файла</span><span class="sxs-lookup"><span data-stu-id="d83b7-646">File Attributes Set</span></span> 

#### <a name="fx_file_attributes_set"></a><span data-ttu-id="d83b7-647">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="d83b7-647">fx_file_attributes_set</span></span>

<span data-ttu-id="d83b7-648">**Значок** ![Значок установки атрибутов файла](./media/user-guide/fx-events/image36.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-648">**Icon** ![File attributes set icon](./media/user-guide/fx-events/image36.png)</span></span>

<span data-ttu-id="d83b7-649">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-649">**Description**</span></span> 

<span data-ttu-id="d83b7-650">Это событие представляет событие установки атрибутов файла.</span><span class="sxs-lookup"><span data-stu-id="d83b7-650">This event represents a file attributes set event.</span></span>

<span data-ttu-id="d83b7-651">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-651">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-652">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-652">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-653">Поле сведений 2. Указатель на имя файла.</span><span class="sxs-lookup"><span data-stu-id="d83b7-653">Info Field 2: Pointer to file name.</span></span> 
- <span data-ttu-id="d83b7-654">Поле сведений 3. Битовая схема атрибутов:</span><span class="sxs-lookup"><span data-stu-id="d83b7-654">Info Field 3: Attributes bit map:</span></span>

  | <span data-ttu-id="d83b7-655">attribute</span><span class="sxs-lookup"><span data-stu-id="d83b7-655">Attribute</span></span>                         | <span data-ttu-id="d83b7-656">Значение</span><span class="sxs-lookup"><span data-stu-id="d83b7-656">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="d83b7-657">Только для чтения</span><span class="sxs-lookup"><span data-stu-id="d83b7-657">Read Only</span></span>                        | <span data-ttu-id="d83b7-658">(0x01)</span><span class="sxs-lookup"><span data-stu-id="d83b7-658">(0x01)</span></span>  |
  |  <span data-ttu-id="d83b7-659">Скрытый</span><span class="sxs-lookup"><span data-stu-id="d83b7-659">Hidden</span></span>                           | <span data-ttu-id="d83b7-660">(0x02)</span><span class="sxs-lookup"><span data-stu-id="d83b7-660">(0x02)</span></span>  |
  |  <span data-ttu-id="d83b7-661">Система</span><span class="sxs-lookup"><span data-stu-id="d83b7-661">System</span></span>                           | <span data-ttu-id="d83b7-662">(0x04)</span><span class="sxs-lookup"><span data-stu-id="d83b7-662">(0x04)</span></span>  |
  |  <span data-ttu-id="d83b7-663">Архив</span><span class="sxs-lookup"><span data-stu-id="d83b7-663">Archive</span></span>                          | <span data-ttu-id="d83b7-664">(0x20)</span><span class="sxs-lookup"><span data-stu-id="d83b7-664">(0x20)</span></span>  |
- <span data-ttu-id="d83b7-665">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-665">Info Field 4: Not used.</span></span>

### <a name="file-best-effort-allocate"></a><span data-ttu-id="d83b7-666">Негарантированное выделение файла</span><span class="sxs-lookup"><span data-stu-id="d83b7-666">File Best Effort Allocate</span></span> 

#### <a name="fx_file_best_effort_allocate"></a><span data-ttu-id="d83b7-667">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="d83b7-667">fx_file_best_effort_allocate</span></span>

<span data-ttu-id="d83b7-668">**Значок** ![Значок негарантированного выделения файла](./media/user-guide/fx-events/image37.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-668">**Icon** ![File best effort allocate icon](./media/user-guide/fx-events/image37.png)</span></span>

<span data-ttu-id="d83b7-669">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-669">**Description**</span></span> 

<span data-ttu-id="d83b7-670">Это событие представляет событие негарантированного выделения файла.</span><span class="sxs-lookup"><span data-stu-id="d83b7-670">This event represents a file best effort allocate event.</span></span>

<span data-ttu-id="d83b7-671">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-671">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-672">Поле сведений 1. Указатель на файл.</span><span class="sxs-lookup"><span data-stu-id="d83b7-672">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="d83b7-673">Поле сведений 2. Запрашиваемый размер.</span><span class="sxs-lookup"><span data-stu-id="d83b7-673">Info Field 2: Requested size.</span></span>
- <span data-ttu-id="d83b7-674">Поле сведений 3. Фактически выделенный размер.</span><span class="sxs-lookup"><span data-stu-id="d83b7-674">Info Field 3: Actual size allocated.</span></span>
- <span data-ttu-id="d83b7-675">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-675">Info Field 4: Not used.</span></span>

### <a name="file-close"></a><span data-ttu-id="d83b7-676">Закрытие файла</span><span class="sxs-lookup"><span data-stu-id="d83b7-676">File Close</span></span> 

#### <a name="fx_file_close"></a><span data-ttu-id="d83b7-677">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="d83b7-677">fx_file_close</span></span>

<span data-ttu-id="d83b7-678">**Значок** ![Значок закрытия файла](./media/user-guide/fx-events/image38.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-678">**Icon** ![File close icon](./media/user-guide/fx-events/image38.png)</span></span>

<span data-ttu-id="d83b7-679">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-679">**Description**</span></span> 

<span data-ttu-id="d83b7-680">Это событие представляет событие закрытия файла.</span><span class="sxs-lookup"><span data-stu-id="d83b7-680">This event represents a file close event.</span></span>

<span data-ttu-id="d83b7-681">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-681">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-682">Поле сведений 1. Указатель на файл.</span><span class="sxs-lookup"><span data-stu-id="d83b7-682">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="d83b7-683">Поле сведений 2. Размер файла.</span><span class="sxs-lookup"><span data-stu-id="d83b7-683">Info Field 2: File size.</span></span>
- <span data-ttu-id="d83b7-684">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-684">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-685">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-685">Info Field 4: Not used.</span></span>

### <a name="file-create"></a><span data-ttu-id="d83b7-686">Создание файла</span><span class="sxs-lookup"><span data-stu-id="d83b7-686">File Create</span></span>

#### <a name="fx_file_create"></a><span data-ttu-id="d83b7-687">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="d83b7-687">fx_file_create</span></span>

<span data-ttu-id="d83b7-688">**Значок** ![Значок создания файла](./media/user-guide/fx-events/image39.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-688">**Icon** ![File create icon](./media/user-guide/fx-events/image39.png)</span></span>

<span data-ttu-id="d83b7-689">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-689">**Description**</span></span>

<span data-ttu-id="d83b7-690">Это событие представляет событие создания файла.</span><span class="sxs-lookup"><span data-stu-id="d83b7-690">This event represents a file create event.</span></span>

<span data-ttu-id="d83b7-691">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-691">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-692">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-692">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-693">Поле сведений 2. Указатель на имя файла.</span><span class="sxs-lookup"><span data-stu-id="d83b7-693">Info Field 2: Pointer to file name.</span></span>
- <span data-ttu-id="d83b7-694">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-694">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-695">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-695">Info Field 4: Not used.</span></span>

### <a name="file-date-time-set"></a><span data-ttu-id="d83b7-696">Установка даты и времени для файла</span><span class="sxs-lookup"><span data-stu-id="d83b7-696">File Date Time Set</span></span> 

#### <a name="fx_file_date_time_set"></a><span data-ttu-id="d83b7-697">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="d83b7-697">fx_file_date_time_set</span></span>

<span data-ttu-id="d83b7-698">**Значок** ![Значок установки даты и времени для файла](./media/user-guide/fx-events/image40.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-698">**Icon** ![File date time set icon](./media/user-guide/fx-events/image40.png)</span></span>

<span data-ttu-id="d83b7-699">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-699">**Description**</span></span>

<span data-ttu-id="d83b7-700">Это событие представляет событие установки даты и времени для файла.</span><span class="sxs-lookup"><span data-stu-id="d83b7-700">This event represents a file date/time set event.</span></span>

<span data-ttu-id="d83b7-701">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-701">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-702">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-702">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-703">Поле сведений 2. Указатель на имя файла.</span><span class="sxs-lookup"><span data-stu-id="d83b7-703">Info Field 2: Pointer to file name.</span></span>
- <span data-ttu-id="d83b7-704">Поле сведений 3. Год.</span><span class="sxs-lookup"><span data-stu-id="d83b7-704">Info Field 3: Year.</span></span>
- <span data-ttu-id="d83b7-705">Поле сведений 4. Месяц.</span><span class="sxs-lookup"><span data-stu-id="d83b7-705">Info Field 4: Month.</span></span>

### <a name="file-delete"></a><span data-ttu-id="d83b7-706">Удаление файла</span><span class="sxs-lookup"><span data-stu-id="d83b7-706">File Delete</span></span> 

#### <a name="fx_file_delete"></a><span data-ttu-id="d83b7-707">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="d83b7-707">fx_file_delete</span></span>

<span data-ttu-id="d83b7-708">**Значок** ![Значок удаления файла](./media/user-guide/fx-events/image41.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-708">**Icon** ![File delete icon](./media/user-guide/fx-events/image41.png)</span></span>

<span data-ttu-id="d83b7-709">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-709">**Description**</span></span>

<span data-ttu-id="d83b7-710">Это событие представляет событие удаления файла.</span><span class="sxs-lookup"><span data-stu-id="d83b7-710">This event represents a file delete event.</span></span>

<span data-ttu-id="d83b7-711">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-711">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-712">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-712">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-713">Поле сведений 2. Указатель на имя файла.</span><span class="sxs-lookup"><span data-stu-id="d83b7-713">Info Field 2: Pointer to file name.</span></span>
- <span data-ttu-id="d83b7-714">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-714">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-715">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-715">Info Field 4: Not used.</span></span>

### <a name="file-open"></a><span data-ttu-id="d83b7-716">Открытие файла</span><span class="sxs-lookup"><span data-stu-id="d83b7-716">File Open</span></span> 

#### <a name="fx_file_open"></a><span data-ttu-id="d83b7-717">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="d83b7-717">fx_file_open</span></span>

<span data-ttu-id="d83b7-718">**Значок** ![Значок открытия файла](./media/user-guide/fx-events/image42.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-718">**Icon** ![File open icon](./media/user-guide/fx-events/image42.png)</span></span>

<span data-ttu-id="d83b7-719">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-719">**Description**</span></span>

<span data-ttu-id="d83b7-720">Это событие представляет событие открытия файла.</span><span class="sxs-lookup"><span data-stu-id="d83b7-720">This event represents a file open event.</span></span>

<span data-ttu-id="d83b7-721">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-721">**Information Fields**</span></span> 

- <span data-ttu-id="d83b7-722">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-722">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-723">Поле сведений 2. Указатель на блок управления файлами.</span><span class="sxs-lookup"><span data-stu-id="d83b7-723">Info Field 2: Pointer to the file control block.</span></span>
- <span data-ttu-id="d83b7-724">Поле сведений 3. Указатель на имя файла.</span><span class="sxs-lookup"><span data-stu-id="d83b7-724">Info Field 3: Pointer to file name.</span></span>
- <span data-ttu-id="d83b7-725">Поле сведений 4. Тип операции открытия:</span><span class="sxs-lookup"><span data-stu-id="d83b7-725">Info Field 4: Open type:</span></span>

  |  <span data-ttu-id="d83b7-726">Тип операции открытия</span><span class="sxs-lookup"><span data-stu-id="d83b7-726">Open Type</span></span>                        | <span data-ttu-id="d83b7-727">Значение</span><span class="sxs-lookup"><span data-stu-id="d83b7-727">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="d83b7-728">Открытие для чтения</span><span class="sxs-lookup"><span data-stu-id="d83b7-728">Open for Read</span></span>                    | <span data-ttu-id="d83b7-729">(0x00)</span><span class="sxs-lookup"><span data-stu-id="d83b7-729">(0x00)</span></span>  |
  |  <span data-ttu-id="d83b7-730">Открытие для записи</span><span class="sxs-lookup"><span data-stu-id="d83b7-730">Open for Write</span></span>                   | <span data-ttu-id="d83b7-731">(0x01)</span><span class="sxs-lookup"><span data-stu-id="d83b7-731">(0x01)</span></span>  |
  |  <span data-ttu-id="d83b7-732">Быстрое открытие для чтения</span><span class="sxs-lookup"><span data-stu-id="d83b7-732">Fast Open for Read</span></span>               | <span data-ttu-id="d83b7-733">(0x02)</span><span class="sxs-lookup"><span data-stu-id="d83b7-733">(0x02)</span></span>  |

### <a name="file-read"></a><span data-ttu-id="d83b7-734">Чтение файла</span><span class="sxs-lookup"><span data-stu-id="d83b7-734">File Read</span></span> 

#### <a name="fx_file_read"></a><span data-ttu-id="d83b7-735">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="d83b7-735">fx_file_read</span></span>

<span data-ttu-id="d83b7-736">**Значок** ![Значок чтения файла](./media/user-guide/fx-events/image43.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-736">**Icon** ![File read icon](./media/user-guide/fx-events/image43.png)</span></span>

<span data-ttu-id="d83b7-737">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-737">**Description**</span></span>

<span data-ttu-id="d83b7-738">Это событие представляет событие чтения файла.</span><span class="sxs-lookup"><span data-stu-id="d83b7-738">This event represents a file read event.</span></span>

<span data-ttu-id="d83b7-739">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-739">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-740">Поле сведений 1. Указатель на файл.</span><span class="sxs-lookup"><span data-stu-id="d83b7-740">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="d83b7-741">Поле сведений 2. Указатель на буфер.</span><span class="sxs-lookup"><span data-stu-id="d83b7-741">Info Field 2: Buffer pointer.</span></span>
- <span data-ttu-id="d83b7-742">Поле сведений 3. Запрашиваемый размер.</span><span class="sxs-lookup"><span data-stu-id="d83b7-742">Info Field 3: Request size.</span></span>
- <span data-ttu-id="d83b7-743">Поле сведений 4. Фактически считанный размер.</span><span class="sxs-lookup"><span data-stu-id="d83b7-743">Info Field 4: Actual size read.</span></span>

### <a name="file-relative-seek"></a><span data-ttu-id="d83b7-744">Относительный поиск в файле</span><span class="sxs-lookup"><span data-stu-id="d83b7-744">File Relative Seek</span></span> 

#### <a name="fx_file_relative_seek"></a><span data-ttu-id="d83b7-745">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="d83b7-745">fx_file_relative_seek</span></span>

<span data-ttu-id="d83b7-746">**Значок** ![Значок относительного поиска в файле](./media/user-guide/fx-events/image44.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-746">**Icon** ![File relative seek icon](./media/user-guide/fx-events/image44.png)</span></span>

<span data-ttu-id="d83b7-747">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-747">**Description**</span></span>

<span data-ttu-id="d83b7-748">Это событие представляет событие относительного поиска в файле.</span><span class="sxs-lookup"><span data-stu-id="d83b7-748">This event represents a file relative seek event.</span></span>

<span data-ttu-id="d83b7-749">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-749">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-750">Поле сведений 1. Указатель на файл.</span><span class="sxs-lookup"><span data-stu-id="d83b7-750">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="d83b7-751">Поле сведений 2. Смещение в байтах.</span><span class="sxs-lookup"><span data-stu-id="d83b7-751">Info Field 2: Byte offset.</span></span>
- <span data-ttu-id="d83b7-752">Поле сведений 3. Точка начала поиска:</span><span class="sxs-lookup"><span data-stu-id="d83b7-752">Info Field 3: Seek from:</span></span>

  | <span data-ttu-id="d83b7-753">Событие</span><span class="sxs-lookup"><span data-stu-id="d83b7-753">Event</span></span>                             | <span data-ttu-id="d83b7-754">Значение</span><span class="sxs-lookup"><span data-stu-id="d83b7-754">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="d83b7-755">С начала</span><span class="sxs-lookup"><span data-stu-id="d83b7-755">From Beginning</span></span>                   | <span data-ttu-id="d83b7-756">(0x00)</span><span class="sxs-lookup"><span data-stu-id="d83b7-756">(0x00)</span></span>  |
  |  <span data-ttu-id="d83b7-757">С конца</span><span class="sxs-lookup"><span data-stu-id="d83b7-757">From End</span></span>                         | <span data-ttu-id="d83b7-758">(0x01)</span><span class="sxs-lookup"><span data-stu-id="d83b7-758">(0x01)</span></span>  | 
  |  <span data-ttu-id="d83b7-759">Вперед</span><span class="sxs-lookup"><span data-stu-id="d83b7-759">Forward</span></span>                          | <span data-ttu-id="d83b7-760">(0x02)</span><span class="sxs-lookup"><span data-stu-id="d83b7-760">(0x02)</span></span>  |
  |  <span data-ttu-id="d83b7-761">Назад</span><span class="sxs-lookup"><span data-stu-id="d83b7-761">Backward</span></span>                         | <span data-ttu-id="d83b7-762">(0x03)</span><span class="sxs-lookup"><span data-stu-id="d83b7-762">(0x03)</span></span>  |
- <span data-ttu-id="d83b7-763">Поле сведений 4. Предыдущее смещение.</span><span class="sxs-lookup"><span data-stu-id="d83b7-763">Info Field 4: Previous offset.</span></span>

### <a name="file-rename"></a><span data-ttu-id="d83b7-764">Переименование файла</span><span class="sxs-lookup"><span data-stu-id="d83b7-764">File Rename</span></span> 

#### <a name="fx_file_rename"></a><span data-ttu-id="d83b7-765">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="d83b7-765">fx_file_rename</span></span>

<span data-ttu-id="d83b7-766">**Значок** ![Значок переименования файла](./media/user-guide/fx-events/image45.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-766">**Icon** ![File rename icon](./media/user-guide/fx-events/image45.png)</span></span>

<span data-ttu-id="d83b7-767">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-767">**Description**</span></span>

<span data-ttu-id="d83b7-768">Это событие представляет событие переименования файла.</span><span class="sxs-lookup"><span data-stu-id="d83b7-768">This event represents a file rename event.</span></span>

<span data-ttu-id="d83b7-769">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-769">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-770">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-770">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-771">Поле сведений 2. Указатель на старое имя файла.</span><span class="sxs-lookup"><span data-stu-id="d83b7-771">Info Field 2: Pointer to old file name.</span></span>
- <span data-ttu-id="d83b7-772">Поле сведений 3. Указатель на новое имя файла.</span><span class="sxs-lookup"><span data-stu-id="d83b7-772">Info Field 3: Pointer to new file name.</span></span>
- <span data-ttu-id="d83b7-773">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-773">Info Field 4: Not used.</span></span>

### <a name="file-seek"></a><span data-ttu-id="d83b7-774">Поиск в файле</span><span class="sxs-lookup"><span data-stu-id="d83b7-774">File Seek</span></span> 

#### <a name="fx_file_seek"></a><span data-ttu-id="d83b7-775">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="d83b7-775">fx_file_seek</span></span>

<span data-ttu-id="d83b7-776">**Значок** ![Значок поиска в файле](./media/user-guide/fx-events/image46.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-776">**Icon** ![File seek icon](./media/user-guide/fx-events/image46.png)</span></span>

<span data-ttu-id="d83b7-777">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-777">**Description**</span></span>

<span data-ttu-id="d83b7-778">Это событие представляет событие поиска в файле.</span><span class="sxs-lookup"><span data-stu-id="d83b7-778">This event represents a file seek event.</span></span>

<span data-ttu-id="d83b7-779">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-779">**Information Fields**</span></span> 

- <span data-ttu-id="d83b7-780">Поле сведений 1. Указатель на файл.</span><span class="sxs-lookup"><span data-stu-id="d83b7-780">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="d83b7-781">Поле сведений 2. Смещение в байтах.</span><span class="sxs-lookup"><span data-stu-id="d83b7-781">Info Field 2: Byte offset.</span></span>
- <span data-ttu-id="d83b7-782">Поле сведений 3. Предыдущее смещение.</span><span class="sxs-lookup"><span data-stu-id="d83b7-782">Info Field 3: Previous offset.</span></span>
- <span data-ttu-id="d83b7-783">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-783">Info Field 4: Not used.</span></span>

### <a name="file-truncate"></a><span data-ttu-id="d83b7-784">Усечение файла</span><span class="sxs-lookup"><span data-stu-id="d83b7-784">File Truncate</span></span> 

#### <a name="fx_file_truncate"></a><span data-ttu-id="d83b7-785">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="d83b7-785">fx_file_truncate</span></span>

<span data-ttu-id="d83b7-786">**Значок** ![Значок усечения файла](./media/user-guide/fx-events/image47.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-786">**Icon** ![File truncate icon](./media/user-guide/fx-events/image47.png)</span></span>

<span data-ttu-id="d83b7-787">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-787">**Description**</span></span>

<span data-ttu-id="d83b7-788">Это событие представляет событие усечения файла.</span><span class="sxs-lookup"><span data-stu-id="d83b7-788">This event represents a file truncate event.</span></span>

<span data-ttu-id="d83b7-789">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-789">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-790">Поле сведений 1. Указатель на файл.</span><span class="sxs-lookup"><span data-stu-id="d83b7-790">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="d83b7-791">Поле сведений 2. Запрашиваемый размер.</span><span class="sxs-lookup"><span data-stu-id="d83b7-791">Info Field 2: Requested size.</span></span>
- <span data-ttu-id="d83b7-792">Поле сведений 3. Предыдущий размер.</span><span class="sxs-lookup"><span data-stu-id="d83b7-792">Info Field 3: Previous size.</span></span>
- <span data-ttu-id="d83b7-793">Поле сведений 4. Новый размер.</span><span class="sxs-lookup"><span data-stu-id="d83b7-793">Info Field 4: New size.</span></span>

### <a name="file-truncate-release"></a><span data-ttu-id="d83b7-794">Освобождение усечения файла</span><span class="sxs-lookup"><span data-stu-id="d83b7-794">File Truncate Release</span></span> 

#### <a name="fx_file_truncate_release"></a><span data-ttu-id="d83b7-795">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="d83b7-795">fx_file_truncate_release</span></span> 

<span data-ttu-id="d83b7-796">**Значок** ![Значок освобождения усечения файла](./media/user-guide/fx-events/image48.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-796">**Icon** ![File truncate release icon](./media/user-guide/fx-events/image48.png)</span></span>

<span data-ttu-id="d83b7-797">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-797">**Description**</span></span>

<span data-ttu-id="d83b7-798">Это событие представляет событие освобождения усечения файла.</span><span class="sxs-lookup"><span data-stu-id="d83b7-798">This event represents a file truncate release event.</span></span>

<span data-ttu-id="d83b7-799">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-799">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-800">Поле сведений 1. Указатель на файл.</span><span class="sxs-lookup"><span data-stu-id="d83b7-800">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="d83b7-801">Поле сведений 2. Запрашиваемый размер.</span><span class="sxs-lookup"><span data-stu-id="d83b7-801">Info Field 2: Requested size.</span></span>
- <span data-ttu-id="d83b7-802">Поле сведений 3. Предыдущий размер.</span><span class="sxs-lookup"><span data-stu-id="d83b7-802">Info Field 3: Previous size.</span></span>
- <span data-ttu-id="d83b7-803">Поле сведений 4. Новый размер.</span><span class="sxs-lookup"><span data-stu-id="d83b7-803">Info Field 4: New size.</span></span>

### <a name="file-write"></a><span data-ttu-id="d83b7-804">Запись файла</span><span class="sxs-lookup"><span data-stu-id="d83b7-804">File Write</span></span> 

#### <a name="fx_file_write"></a><span data-ttu-id="d83b7-805">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="d83b7-805">fx_file_write</span></span> 

<span data-ttu-id="d83b7-806">**Значок** ![Значок записи файла](./media/user-guide/fx-events/image49.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-806">**Icon** ![File write icon](./media/user-guide/fx-events/image49.png)</span></span>

<span data-ttu-id="d83b7-807">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-807">**Description**</span></span>

<span data-ttu-id="d83b7-808">Это событие представляет событие записи файла.</span><span class="sxs-lookup"><span data-stu-id="d83b7-808">This event represents a file write event.</span></span>

<span data-ttu-id="d83b7-809">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-809">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-810">Поле сведений 1. Указатель на файл.</span><span class="sxs-lookup"><span data-stu-id="d83b7-810">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="d83b7-811">Поле сведений 2. Указатель на буфер.</span><span class="sxs-lookup"><span data-stu-id="d83b7-811">Info Field 2: Buffer pointer.</span></span>
- <span data-ttu-id="d83b7-812">Поле сведений 3. Запрашиваемый размер.</span><span class="sxs-lookup"><span data-stu-id="d83b7-812">Info Field 3: Request size.</span></span>
- <span data-ttu-id="d83b7-813">Поле сведений 4. Фактически записанный размер.</span><span class="sxs-lookup"><span data-stu-id="d83b7-813">Info Field 4: Actual size written.</span></span>

### <a name="media-abort"></a><span data-ttu-id="d83b7-814">Прерывание носителя</span><span class="sxs-lookup"><span data-stu-id="d83b7-814">Media Abort</span></span> 

#### <a name="fx_media_abort"></a><span data-ttu-id="d83b7-815">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="d83b7-815">fx_media_abort</span></span> 

<span data-ttu-id="d83b7-816">**Значок** ![Значок прерывания носителя](./media/user-guide/fx-events/image50.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-816">**Icon** ![Media abort icon](./media/user-guide/fx-events/image50.png)</span></span>

<span data-ttu-id="d83b7-817">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-817">**Description**</span></span>

<span data-ttu-id="d83b7-818">Это событие представляет событие прерывания носителя.</span><span class="sxs-lookup"><span data-stu-id="d83b7-818">This event represents a media abort event.</span></span>

<span data-ttu-id="d83b7-819">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-819">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-820">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-820">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-821">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-821">Info Field 2: Not used.</span></span>
- <span data-ttu-id="d83b7-822">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-822">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-823">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-823">Info Field 4: Not used.</span></span>

### <a name="media-cache-invalidate"></a><span data-ttu-id="d83b7-824">Недействительность кэша носителя</span><span class="sxs-lookup"><span data-stu-id="d83b7-824">Media Cache Invalidate</span></span>

#### <a name="fx_media_cache_invalidate"></a><span data-ttu-id="d83b7-825">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="d83b7-825">fx_media_cache_invalidate</span></span>

<span data-ttu-id="d83b7-826">**Значок** ![Значок недействительности кэша носителя](./media/user-guide/fx-events/image51.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-826">**Icon** ![Media cache invalidate icon](./media/user-guide/fx-events/image51.png)</span></span>

<span data-ttu-id="d83b7-827">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-827">**Description**</span></span>

<span data-ttu-id="d83b7-828">Это событие представляет событие недействительности кэша носителя.</span><span class="sxs-lookup"><span data-stu-id="d83b7-828">This event represents a media cache invalidate event.</span></span>

<span data-ttu-id="d83b7-829">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-829">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-830">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-830">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-831">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-831">Info Field 2: Not used.</span></span>
- <span data-ttu-id="d83b7-832">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-832">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-833">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-833">Info Field 4: Not used.</span></span>

### <a name="media-check"></a><span data-ttu-id="d83b7-834">Проверка носителя</span><span class="sxs-lookup"><span data-stu-id="d83b7-834">Media Check</span></span> 

#### <a name="fx_media_check"></a><span data-ttu-id="d83b7-835">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="d83b7-835">fx_media_check</span></span>

<span data-ttu-id="d83b7-836">**Значок** ![Значок проверки носителя](./media/user-guide/fx-events/image52.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-836">**Icon** ![Media check icon](./media/user-guide/fx-events/image52.png)</span></span>

<span data-ttu-id="d83b7-837">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-837">**Description**</span></span>

<span data-ttu-id="d83b7-838">Это событие представляет событие проверки носителя.</span><span class="sxs-lookup"><span data-stu-id="d83b7-838">This event represents a media check event.</span></span>

<span data-ttu-id="d83b7-839">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-839">**Information Fields**</span></span> 

- <span data-ttu-id="d83b7-840">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-840">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-841">Поле сведений 2. Указатель на временную область памяти.</span><span class="sxs-lookup"><span data-stu-id="d83b7-841">Info Field 2: Scratch memory pointer.</span></span>
- <span data-ttu-id="d83b7-842">Поле сведений 3. Размер временной области памяти.</span><span class="sxs-lookup"><span data-stu-id="d83b7-842">Info Field 3: Scratch memory size.</span></span>
- <span data-ttu-id="d83b7-843">Поле сведений 4. Битовая схема ошибок:</span><span class="sxs-lookup"><span data-stu-id="d83b7-843">Info Field 4: Errors bit map:</span></span>

  | <span data-ttu-id="d83b7-844">Тип ошибки</span><span class="sxs-lookup"><span data-stu-id="d83b7-844">Error type</span></span>                        | <span data-ttu-id="d83b7-845">Значение</span><span class="sxs-lookup"><span data-stu-id="d83b7-845">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="d83b7-846">Ошибка цепочки FAT</span><span class="sxs-lookup"><span data-stu-id="d83b7-846">FAT Chain Error</span></span>                  | <span data-ttu-id="d83b7-847">(0x01)</span><span class="sxs-lookup"><span data-stu-id="d83b7-847">(0x01)</span></span>  |
  |  <span data-ttu-id="d83b7-848">Ошибка каталога</span><span class="sxs-lookup"><span data-stu-id="d83b7-848">Directory Error</span></span>                  | <span data-ttu-id="d83b7-849">(0x02)</span><span class="sxs-lookup"><span data-stu-id="d83b7-849">(0x02)</span></span>  |
  |  <span data-ttu-id="d83b7-850">Ошибка потери кластера</span><span class="sxs-lookup"><span data-stu-id="d83b7-850">Lost Cluster Error</span></span>               | <span data-ttu-id="d83b7-851">(0x04)</span><span class="sxs-lookup"><span data-stu-id="d83b7-851">(0x04)</span></span>  |
  |  <span data-ttu-id="d83b7-852">Ошибка размера файла</span><span class="sxs-lookup"><span data-stu-id="d83b7-852">File Size Error</span></span>                  | <span data-ttu-id="d83b7-853">(0x08)</span><span class="sxs-lookup"><span data-stu-id="d83b7-853">(0x08)</span></span>  |

### <a name="media-close"></a><span data-ttu-id="d83b7-854">Закрытие носителя</span><span class="sxs-lookup"><span data-stu-id="d83b7-854">Media Close</span></span> 

#### <a name="fx_media_close"></a><span data-ttu-id="d83b7-855">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="d83b7-855">fx_media_close</span></span>

<span data-ttu-id="d83b7-856">**Значок** ![Значок закрытия носителя](./media/user-guide/fx-events/image53.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-856">**Icon** ![Media Close icon](./media/user-guide/fx-events/image53.png)</span></span>

<span data-ttu-id="d83b7-857">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-857">**Description**</span></span>

<span data-ttu-id="d83b7-858">Это событие представляет событие закрытия носителя.</span><span class="sxs-lookup"><span data-stu-id="d83b7-858">This event represents a media close event.</span></span>

<span data-ttu-id="d83b7-859">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-859">**Information Fields**</span></span> 

- <span data-ttu-id="d83b7-860">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-860">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-861">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-861">Info Field 2: Not used.</span></span>
- <span data-ttu-id="d83b7-862">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-862">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-863">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-863">Info Field 4: Not used.</span></span>

### <a name="media-flush"></a><span data-ttu-id="d83b7-864">Очистка носителя</span><span class="sxs-lookup"><span data-stu-id="d83b7-864">Media Flush</span></span> 

#### <a name="fx_media_flush"></a><span data-ttu-id="d83b7-865">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="d83b7-865">fx_media_flush</span></span>

<span data-ttu-id="d83b7-866">**Значок** ![Значок очистки носителя](./media/user-guide/fx-events/image54.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-866">**Icon** ![Media flush icon](./media/user-guide/fx-events/image54.png)</span></span>

<span data-ttu-id="d83b7-867">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-867">**Description**</span></span>

<span data-ttu-id="d83b7-868">Это событие представляет событие очистки носителя.</span><span class="sxs-lookup"><span data-stu-id="d83b7-868">This event represents a media flush event.</span></span>

<span data-ttu-id="d83b7-869">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-869">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-870">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-870">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-871">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-871">Info Field 2: Not used.</span></span>
- <span data-ttu-id="d83b7-872">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-872">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-873">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-873">Info Field 4: Not used.</span></span>

### <a name="media-format"></a><span data-ttu-id="d83b7-874">Форматирование носителя</span><span class="sxs-lookup"><span data-stu-id="d83b7-874">Media Format</span></span> 

#### <a name="fx_media_format"></a><span data-ttu-id="d83b7-875">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="d83b7-875">fx_media_format</span></span>

<span data-ttu-id="d83b7-876">**Значок** ![Значок форматирования носителя](./media/user-guide/fx-events/image55.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-876">**Icon** ![Media format icon](./media/user-guide/fx-events/image55.png)</span></span>

<span data-ttu-id="d83b7-877">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-877">**Description**</span></span>

<span data-ttu-id="d83b7-878">Это событие представляет событие форматирования носителя.</span><span class="sxs-lookup"><span data-stu-id="d83b7-878">This event represents a media format event.</span></span>

<span data-ttu-id="d83b7-879">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-879">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-880">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-880">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-881">Поле сведений 2. Количество корневых записей.</span><span class="sxs-lookup"><span data-stu-id="d83b7-881">Info Field 2: Number of root entries.</span></span>
- <span data-ttu-id="d83b7-882">Поле сведений 3. Секторы.</span><span class="sxs-lookup"><span data-stu-id="d83b7-882">Info Field 3: Sectors.</span></span>
- <span data-ttu-id="d83b7-883">Поле сведений 4. Количество секторов на кластер.</span><span class="sxs-lookup"><span data-stu-id="d83b7-883">Info Field 4: Sectors per cluster.</span></span>

### <a name="media-open"></a><span data-ttu-id="d83b7-884">Открытие носителя</span><span class="sxs-lookup"><span data-stu-id="d83b7-884">Media Open</span></span> 

#### <a name="fx_media_open"></a><span data-ttu-id="d83b7-885">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="d83b7-885">fx_media_open</span></span>

<span data-ttu-id="d83b7-886">**Значок** ![Значок открытия носителя](./media/user-guide/fx-events/image56.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-886">**Icon** ![Media open icon](./media/user-guide/fx-events/image56.png)</span></span>

<span data-ttu-id="d83b7-887">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-887">**Description**</span></span>

<span data-ttu-id="d83b7-888">Это событие представляет событие открытия носителя.</span><span class="sxs-lookup"><span data-stu-id="d83b7-888">This event represents a media open event.</span></span>

<span data-ttu-id="d83b7-889">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-889">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-890">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-890">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-891">Поле сведений 2. Указатель на запись драйвера носителя.</span><span class="sxs-lookup"><span data-stu-id="d83b7-891">Info Field 2: Pointer to media driver entry.</span></span>
- <span data-ttu-id="d83b7-892">Поле сведений 3. Указатель на область памяти.</span><span class="sxs-lookup"><span data-stu-id="d83b7-892">Info Field 3: Memory pointer.</span></span>
- <span data-ttu-id="d83b7-893">Поле сведений 4. Размер области памяти.</span><span class="sxs-lookup"><span data-stu-id="d83b7-893">Info Field 4: Memory size.</span></span>

### <a name="media-read-media-read"></a><span data-ttu-id="d83b7-894">Чтение носителя</span><span class="sxs-lookup"><span data-stu-id="d83b7-894">Media Read Media Read</span></span> 

#### <a name="fx_media_read"></a><span data-ttu-id="d83b7-895">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="d83b7-895">fx_media_read</span></span>

<span data-ttu-id="d83b7-896">**Значок** ![Значок чтения носителя](./media/user-guide/fx-events/image57.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-896">**Icon** ![Media read icon](./media/user-guide/fx-events/image57.png)</span></span>

<span data-ttu-id="d83b7-897">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-897">**Description**</span></span>

<span data-ttu-id="d83b7-898">Это событие представляет событие чтения носителя.</span><span class="sxs-lookup"><span data-stu-id="d83b7-898">This event represents a media read event.</span></span>

<span data-ttu-id="d83b7-899">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-899">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-900">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-900">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-901">Поле сведений 2. Логический сектор.</span><span class="sxs-lookup"><span data-stu-id="d83b7-901">Info Field 2: Logical sector.</span></span>
- <span data-ttu-id="d83b7-902">Поле сведений 3. Указатель на буфер.</span><span class="sxs-lookup"><span data-stu-id="d83b7-902">Info Field 3: Buffer pointer.</span></span>
- <span data-ttu-id="d83b7-903">Поле сведений 4. Считанные байты.</span><span class="sxs-lookup"><span data-stu-id="d83b7-903">Info Field 4: Bytes read.</span></span>

### <a name="media-space-available"></a><span data-ttu-id="d83b7-904">Доступное место на носителе</span><span class="sxs-lookup"><span data-stu-id="d83b7-904">Media Space Available</span></span> 

#### <a name="fx_media_space_available"></a><span data-ttu-id="d83b7-905">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="d83b7-905">fx_media_space_available</span></span>

<span data-ttu-id="d83b7-906">**Значок** ![Значок доступного места на носителе](./media/user-guide/fx-events/image58.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-906">**Icon** ![Media space available icon](./media/user-guide/fx-events/image58.png)</span></span>

<span data-ttu-id="d83b7-907">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-907">**Description**</span></span>

<span data-ttu-id="d83b7-908">Это событие представляет событие доступного места на носителе.</span><span class="sxs-lookup"><span data-stu-id="d83b7-908">This event represents a media space available event.</span></span>

<span data-ttu-id="d83b7-909">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-909">**Information Fields**</span></span> 

- <span data-ttu-id="d83b7-910">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-910">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-911">Поле сведений 2. Указатель на доступные байты.</span><span class="sxs-lookup"><span data-stu-id="d83b7-911">Info Field 2: Available bytes pointer.</span></span>
- <span data-ttu-id="d83b7-912">Поле сведений 3. Количество свободных кластеров.</span><span class="sxs-lookup"><span data-stu-id="d83b7-912">Info Field 3: Number of free clusters.</span></span>
- <span data-ttu-id="d83b7-913">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-913">Info Field 4: Not used.</span></span>

### <a name="media-volume-get"></a><span data-ttu-id="d83b7-914">Получение тома на носителе</span><span class="sxs-lookup"><span data-stu-id="d83b7-914">Media Volume Get</span></span> 

#### <a name="fx_media_volume_get"></a><span data-ttu-id="d83b7-915">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="d83b7-915">fx_media_volume_get</span></span>

<span data-ttu-id="d83b7-916">**Значок** ![Значок получения тома на носителе](./media/user-guide/fx-events/image59.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-916">**Icon** ![Media volume get icon](./media/user-guide/fx-events/image59.png)</span></span>

<span data-ttu-id="d83b7-917">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-917">**Description**</span></span>

<span data-ttu-id="d83b7-918">Это событие представляет событие получения тома на носителе.</span><span class="sxs-lookup"><span data-stu-id="d83b7-918">This event represents a media volume get event.</span></span>

<span data-ttu-id="d83b7-919">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-919">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-920">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-920">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-921">Поле сведений 2. Указатель на имя тома.</span><span class="sxs-lookup"><span data-stu-id="d83b7-921">Info Field 2: Pointer to volume name.</span></span>
- <span data-ttu-id="d83b7-922">Поле сведений 3. Источник тома.</span><span class="sxs-lookup"><span data-stu-id="d83b7-922">Info Field 3: Volume source.</span></span>
- <span data-ttu-id="d83b7-923">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-923">Info Field 4: Not used.</span></span>

### <a name="media-volume-set"></a><span data-ttu-id="d83b7-924">Установка тома на носителе</span><span class="sxs-lookup"><span data-stu-id="d83b7-924">Media Volume Set</span></span> 

#### <a name="fx_media_volume_set"></a><span data-ttu-id="d83b7-925">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="d83b7-925">fx_media_volume_set</span></span>

<span data-ttu-id="d83b7-926">**Значок** ![Значок установки тома на носителе](./media/user-guide/fx-events/image60.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-926">**Icon** ![Media volume set icon](./media/user-guide/fx-events/image60.png)</span></span>

<span data-ttu-id="d83b7-927">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-927">**Description**</span></span>

<span data-ttu-id="d83b7-928">Это событие представляет событие установки тома на носителе.</span><span class="sxs-lookup"><span data-stu-id="d83b7-928">This event represents a media volume set event.</span></span>

<span data-ttu-id="d83b7-929">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-929">**Information Fields**</span></span> 
- <span data-ttu-id="d83b7-930">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-930">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-931">Поле сведений 2. Указатель на имя тома.</span><span class="sxs-lookup"><span data-stu-id="d83b7-931">Info Field 2: Pointer to volume name.</span></span>
- <span data-ttu-id="d83b7-932">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-932">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-933">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-933">Info Field 4: Not used.</span></span>

### <a name="media-write"></a><span data-ttu-id="d83b7-934">Запись на носитель</span><span class="sxs-lookup"><span data-stu-id="d83b7-934">Media Write</span></span> 

#### <a name="fx_media_write"></a><span data-ttu-id="d83b7-935">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="d83b7-935">fx_media_write</span></span>

<span data-ttu-id="d83b7-936">**Значок** ![Значок записи на носитель.](./media/user-guide/fx-events/image61.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-936">**Icon** ![Media write icon](./media/user-guide/fx-events/image61.png)</span></span>

<span data-ttu-id="d83b7-937">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-937">**Description**</span></span>

<span data-ttu-id="d83b7-938">Это событие представляет событие записи на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-938">This event represents a media write event.</span></span>

<span data-ttu-id="d83b7-939">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-939">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-940">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-940">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-941">Поле сведений 2. Логический сектор.</span><span class="sxs-lookup"><span data-stu-id="d83b7-941">Info Field 2: Logical sector.</span></span>
- <span data-ttu-id="d83b7-942">Поле сведений 3. Указатель на буфер.</span><span class="sxs-lookup"><span data-stu-id="d83b7-942">Info Field 3: Buffer pointer.</span></span>
- <span data-ttu-id="d83b7-943">Поле сведений 4. Записанные байты.</span><span class="sxs-lookup"><span data-stu-id="d83b7-943">Info Field 4: Bytes written.</span></span>

### <a name="system-date-get"></a><span data-ttu-id="d83b7-944">Получение системной даты</span><span class="sxs-lookup"><span data-stu-id="d83b7-944">System Date Get</span></span> 

#### <a name="fx_system_date_get"></a><span data-ttu-id="d83b7-945">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="d83b7-945">fx_system_date_get</span></span> 

<span data-ttu-id="d83b7-946">**Значок** ![Значок получения системной даты](./media/user-guide/fx-events/image62.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-946">**Icon** ![System date get icon](./media/user-guide/fx-events/image62.png)</span></span>

<span data-ttu-id="d83b7-947">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-947">**Description**</span></span>

<span data-ttu-id="d83b7-948">Это событие представляет событие получения системной даты.</span><span class="sxs-lookup"><span data-stu-id="d83b7-948">This event represents a system date get event.</span></span>

<span data-ttu-id="d83b7-949">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-949">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-950">Поле сведений 1. Год.</span><span class="sxs-lookup"><span data-stu-id="d83b7-950">Info Field 1: Year.</span></span>
- <span data-ttu-id="d83b7-951">Поле сведений 2. Месяц.</span><span class="sxs-lookup"><span data-stu-id="d83b7-951">Info Field 2: Month.</span></span>
- <span data-ttu-id="d83b7-952">Поле сведений 3. День.</span><span class="sxs-lookup"><span data-stu-id="d83b7-952">Info Field 3: Day.</span></span>
- <span data-ttu-id="d83b7-953">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-953">Info Field 4: Not used.</span></span>

### <a name="system-date-set"></a><span data-ttu-id="d83b7-954">Установка системной даты</span><span class="sxs-lookup"><span data-stu-id="d83b7-954">System Date Set</span></span> 

#### <a name="fx_system_date_set"></a><span data-ttu-id="d83b7-955">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="d83b7-955">fx_system_date_set</span></span> 

<span data-ttu-id="d83b7-956">**Значок** ![Значок установки системной даты](./media/user-guide/fx-events/image63.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-956">**Icon** ![System date set icon](./media/user-guide/fx-events/image63.png)</span></span>

<span data-ttu-id="d83b7-957">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-957">**Description**</span></span>

<span data-ttu-id="d83b7-958">Это событие представляет событие установки системной даты.</span><span class="sxs-lookup"><span data-stu-id="d83b7-958">This event represents a system date set event.</span></span>

<span data-ttu-id="d83b7-959">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-959">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-960">Поле сведений 1. Год.</span><span class="sxs-lookup"><span data-stu-id="d83b7-960">Info Field 1: Year.</span></span>
- <span data-ttu-id="d83b7-961">Поле сведений 2. Месяц.</span><span class="sxs-lookup"><span data-stu-id="d83b7-961">Info Field 2: Month.</span></span>
- <span data-ttu-id="d83b7-962">Поле сведений 3. День.</span><span class="sxs-lookup"><span data-stu-id="d83b7-962">Info Field 3: Day.</span></span>
- <span data-ttu-id="d83b7-963">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-963">Info Field 4: Not used.</span></span>

### <a name="system-initialize"></a><span data-ttu-id="d83b7-964">Инициализация системы</span><span class="sxs-lookup"><span data-stu-id="d83b7-964">System Initialize</span></span> 

#### <a name="fx_system_initialize"></a><span data-ttu-id="d83b7-965">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="d83b7-965">fx_system_initialize</span></span> 

<span data-ttu-id="d83b7-966">**Значок** ![Значок инициализации системы](./media/user-guide/fx-events/image64.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-966">**Icon** ![System initialize icon](./media/user-guide/fx-events/image64.png)</span></span>

<span data-ttu-id="d83b7-967">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-967">**Description**</span></span>

<span data-ttu-id="d83b7-968">Это событие представляет событие инициализации системы.</span><span class="sxs-lookup"><span data-stu-id="d83b7-968">This event represents a system initialize event.</span></span>

<span data-ttu-id="d83b7-969">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-969">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-970">Поле сведений 1. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-970">Info Field 1: Not used.</span></span>
- <span data-ttu-id="d83b7-971">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-971">Info Field 2: Not used.</span></span>
- <span data-ttu-id="d83b7-972">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-972">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-973">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-973">Info Field 4: Not used.</span></span>

### <a name="system-time-get"></a><span data-ttu-id="d83b7-974">Получение системного времени</span><span class="sxs-lookup"><span data-stu-id="d83b7-974">System Time Get</span></span> 

#### <a name="fx_system_time_get"></a><span data-ttu-id="d83b7-975">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="d83b7-975">fx_system_time_get</span></span> 

<span data-ttu-id="d83b7-976">**Значок** ![Значок получения системного времени](./media/user-guide/fx-events/image65.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-976">**Icon** ![System time get icon](./media/user-guide/fx-events/image65.png)</span></span>

<span data-ttu-id="d83b7-977">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-977">**Description**</span></span>

<span data-ttu-id="d83b7-978">Это событие представляет событие получения системного времени.</span><span class="sxs-lookup"><span data-stu-id="d83b7-978">This event represents a system time get event.</span></span>

<span data-ttu-id="d83b7-979">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-979">**Information Fields**</span></span> 

- <span data-ttu-id="d83b7-980">Поле сведений 1. Час.</span><span class="sxs-lookup"><span data-stu-id="d83b7-980">Info Field 1: Hour.</span></span>
- <span data-ttu-id="d83b7-981">Поле сведений 2. Минута.</span><span class="sxs-lookup"><span data-stu-id="d83b7-981">Info Field 2: Minute.</span></span>
- <span data-ttu-id="d83b7-982">Поле сведений 3. Секунда.</span><span class="sxs-lookup"><span data-stu-id="d83b7-982">Info Field 3: Second.</span></span>
- <span data-ttu-id="d83b7-983">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-983">Info Field 4: Not used.</span></span>

### <a name="system-time-set"></a><span data-ttu-id="d83b7-984">Установка системного времени</span><span class="sxs-lookup"><span data-stu-id="d83b7-984">System Time Set</span></span> 

#### <a name="fx_system_time_set"></a><span data-ttu-id="d83b7-985">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="d83b7-985">fx_system_time_set</span></span> 

<span data-ttu-id="d83b7-986">**Значок** ![Значок установки системного времени](./media/user-guide/fx-events/image66.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-986">**Icon** ![System time set icon](./media/user-guide/fx-events/image66.png)</span></span>

<span data-ttu-id="d83b7-987">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-987">**Description**</span></span>

<span data-ttu-id="d83b7-988">Это событие представляет событие установки системного времени.</span><span class="sxs-lookup"><span data-stu-id="d83b7-988">This event represents a system time set event.</span></span>

<span data-ttu-id="d83b7-989">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-989">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-990">Поле сведений 1. Час.</span><span class="sxs-lookup"><span data-stu-id="d83b7-990">Info Field 1: Hour.</span></span>
- <span data-ttu-id="d83b7-991">Поле сведений 2. Минута.</span><span class="sxs-lookup"><span data-stu-id="d83b7-991">Info Field 2: Minute.</span></span>
- <span data-ttu-id="d83b7-992">Поле сведений 3. Секунда.</span><span class="sxs-lookup"><span data-stu-id="d83b7-992">Info Field 3: Second.</span></span>
- <span data-ttu-id="d83b7-993">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-993">Info Field 4: Not used.</span></span>

### <a name="unicode-directory-create"></a><span data-ttu-id="d83b7-994">Создание каталога Юникода</span><span class="sxs-lookup"><span data-stu-id="d83b7-994">Unicode Directory Create</span></span> 

#### <a name="fx_unicode_directory_create"></a><span data-ttu-id="d83b7-995">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="d83b7-995">fx_unicode_directory_create</span></span> 

<span data-ttu-id="d83b7-996">**Значок** ![Значок создания каталога Юникода](./media/user-guide/fx-events/image67.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-996">**Icon** ![Unicode directory create icon](./media/user-guide/fx-events/image67.png)</span></span>

<span data-ttu-id="d83b7-997">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-997">**Description**</span></span>

<span data-ttu-id="d83b7-998">Это событие представляет событие создания каталога Юникода.</span><span class="sxs-lookup"><span data-stu-id="d83b7-998">This event represents a Unicode directory create event.</span></span>

<span data-ttu-id="d83b7-999">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-999">**Information Fields**</span></span> 

- <span data-ttu-id="d83b7-1000">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1000">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-1001">Поле сведений 2. Указатель на имя в формате Юникода.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1001">Info Field 2: Pointer to Unicode name.</span></span>
- <span data-ttu-id="d83b7-1002">Поле сведений 3. Размер имени в формате Юникода.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1002">Info Field 3: Size of Unicode name.</span></span>
- <span data-ttu-id="d83b7-1003">Поле сведений 4. Указатель на краткое имя.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1003">Info Field 4: Pointer to short name.</span></span>

### <a name="unicode-directory-rename"></a><span data-ttu-id="d83b7-1004">Переименование каталога Юникода</span><span class="sxs-lookup"><span data-stu-id="d83b7-1004">Unicode Directory Rename</span></span> 

#### <a name="fx_unicode_directory_rename"></a><span data-ttu-id="d83b7-1005">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="d83b7-1005">fx_unicode_directory_rename</span></span>

<span data-ttu-id="d83b7-1006">**Значок** ![Значок переименования каталога Юникода](./media/user-guide/fx-events/image68.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-1006">**Icon** ![Unicode directory rename icon](./media/user-guide/fx-events/image68.png)</span></span>

<span data-ttu-id="d83b7-1007">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-1007">**Description**</span></span>

<span data-ttu-id="d83b7-1008">Это событие представляет событие переименования каталога Юникода.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1008">This event represents a Unicode directory rename event.</span></span>

<span data-ttu-id="d83b7-1009">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-1009">**Information Fields**</span></span> 

- <span data-ttu-id="d83b7-1010">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1010">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-1011">Поле сведений 2. Указатель на имя в формате Юникода.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1011">Info Field 2: Pointer to Unicode name.</span></span>
- <span data-ttu-id="d83b7-1012">Поле сведений 3. Размер имени в формате Юникода.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1012">Info Field 3: Size of Unicode name.</span></span>
- <span data-ttu-id="d83b7-1013">Поле сведений 4. Указатель на краткое имя.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1013">Info Field 4: Pointer to short name.</span></span>

### <a name="unicode-file-create"></a><span data-ttu-id="d83b7-1014">Создание файла Юникода</span><span class="sxs-lookup"><span data-stu-id="d83b7-1014">Unicode File Create</span></span> 

#### <a name="fx_unicode_file_create"></a><span data-ttu-id="d83b7-1015">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="d83b7-1015">fx_unicode_file_create</span></span>

<span data-ttu-id="d83b7-1016">**Значок** ![Значок создания файла Юникода](./media/user-guide/fx-events/image69.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-1016">**Icon** ![Unicode file create icon](./media/user-guide/fx-events/image69.png)</span></span>

<span data-ttu-id="d83b7-1017">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-1017">**Description**</span></span>

<span data-ttu-id="d83b7-1018">Это событие представляет событие создания файла Юникода.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1018">This event represents a Unicode file create event.</span></span>

<span data-ttu-id="d83b7-1019">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-1019">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-1020">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1020">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-1021">Поле сведений 2. Указатель на имя в формате Юникода.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1021">Info Field 2: Pointer to the Unicode name.</span></span>
- <span data-ttu-id="d83b7-1022">Поле сведений 3. Размер имени в формате Юникода.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1022">Info Field 3: Size of Unicode name.</span></span>
- <span data-ttu-id="d83b7-1023">Поле сведений 4. Указатель на краткое имя.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1023">Info Field 4: Pointer to short name.</span></span>

### <a name="unicode-file-rename"></a><span data-ttu-id="d83b7-1024">Переименование файла Юникода</span><span class="sxs-lookup"><span data-stu-id="d83b7-1024">Unicode File Rename</span></span> 

#### <a name="fx_unicode_file_rename"></a><span data-ttu-id="d83b7-1025">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="d83b7-1025">fx_unicode_file_rename</span></span>

<span data-ttu-id="d83b7-1026">**Значок** ![Значок переименования файла Юникода](./media/user-guide/fx-events/image70.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-1026">**Icon** ![Unicode file rename icon](./media/user-guide/fx-events/image70.png)</span></span>

<span data-ttu-id="d83b7-1027">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-1027">**Description**</span></span>

<span data-ttu-id="d83b7-1028">Это событие представляет событие переименования файла Юникода.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1028">This event represents a Unicode file rename event.</span></span>

<span data-ttu-id="d83b7-1029">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-1029">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-1030">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1030">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-1031">Поле сведений 2. Указатель на имя в формате Юникода.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1031">Info Field 2: Pointer to Unicode name.</span></span>
- <span data-ttu-id="d83b7-1032">Поле сведений 3. Размер имени в формате Юникода.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1032">Info Field 3: Size of Unicode name.</span></span>
- <span data-ttu-id="d83b7-1033">Поле сведений 4. Указатель на краткое имя.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1033">Info Field 4: Pointer to short name.</span></span>

### <a name="unicode-length-get"></a><span data-ttu-id="d83b7-1034">Получение длины Юникода</span><span class="sxs-lookup"><span data-stu-id="d83b7-1034">Unicode Length Get</span></span> 

#### <a name="fx_unicode_length_get"></a><span data-ttu-id="d83b7-1035">fx_unicode_length_get</span><span class="sxs-lookup"><span data-stu-id="d83b7-1035">fx_unicode_length_get</span></span>

<span data-ttu-id="d83b7-1036">**Значок** ![Значок получения длины Юникода](./media/user-guide/fx-events/image71.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-1036">**Icon** ![Unicode length get icon](./media/user-guide/fx-events/image71.png)</span></span>

<span data-ttu-id="d83b7-1037">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-1037">**Description**</span></span>

<span data-ttu-id="d83b7-1038">Это событие представляет событие получения длины Юникода.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1038">This event represents a Unicode length get event.</span></span>

<span data-ttu-id="d83b7-1039">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-1039">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-1040">Поле сведений 1. Указатель на имя в формате Юникода.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1040">Info Field 1: Pointer to the Unicode name.</span></span>
- <span data-ttu-id="d83b7-1041">Поле сведений 2. Длина.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1041">Info Field 2: Length.</span></span>
- <span data-ttu-id="d83b7-1042">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1042">Info Field 3: Not used.</span></span>
- <span data-ttu-id="d83b7-1043">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1043">Info Field 4: Not used.</span></span>

### <a name="unicode-name-get"></a><span data-ttu-id="d83b7-1044">Получение имени Юникода</span><span class="sxs-lookup"><span data-stu-id="d83b7-1044">Unicode Name Get</span></span> 

#### <a name="fx_unicode_name_get"></a><span data-ttu-id="d83b7-1045">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="d83b7-1045">fx_unicode_name_get</span></span>

<span data-ttu-id="d83b7-1046">**Значок** ![Значок получения имени Юникода](./media/user-guide/fx-events/image72.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-1046">**Icon** ![Unicode name get icon](./media/user-guide/fx-events/image72.png)</span></span>

<span data-ttu-id="d83b7-1047">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-1047">**Description**</span></span>

<span data-ttu-id="d83b7-1048">Это событие представляет событие получения имени Юникода.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1048">This event represents a Unicode name get event.</span></span>

<span data-ttu-id="d83b7-1049">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-1049">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-1050">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1050">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-1051">Поле сведений 2. Исходное краткое имя.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1051">Info Field 2: Source short name.</span></span>
- <span data-ttu-id="d83b7-1052">Поле сведений 3. Указатель на целевое имя в формате Юникода.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1052">Info Field 3: Destination Unicode name pointer.</span></span>
- <span data-ttu-id="d83b7-1053">Поле сведений 4. Длина целевого имени в формате Юникода.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1053">Info Field 4: Destination Unicode name length.</span></span>

### <a name="unicode-short-name-get"></a><span data-ttu-id="d83b7-1054">Получение краткого имени Юникода</span><span class="sxs-lookup"><span data-stu-id="d83b7-1054">Unicode Short Name Get</span></span> 

#### <a name="fx_unicode_short_name_get"></a><span data-ttu-id="d83b7-1055">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="d83b7-1055">fx_unicode_short_name_get</span></span>

<span data-ttu-id="d83b7-1056">**Значок** ![Значок получения краткого имени Юникода](./media/user-guide/fx-events/image73.png)</span><span class="sxs-lookup"><span data-stu-id="d83b7-1056">**Icon** ![Unicode short name get icon](./media/user-guide/fx-events/image73.png)</span></span>

<span data-ttu-id="d83b7-1057">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d83b7-1057">**Description**</span></span>

<span data-ttu-id="d83b7-1058">Это событие представляет событие получения краткого имени Юникода.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1058">This event represents a Unicode short name get event.</span></span>

<span data-ttu-id="d83b7-1059">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="d83b7-1059">**Information Fields**</span></span>

- <span data-ttu-id="d83b7-1060">Поле сведений 1. Указатель на носитель.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1060">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="d83b7-1061">Поле сведений 2. Указатель на исходное имя в формате Юникода.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1061">Info Field 2: Pointer to source Unicode name.</span></span>
- <span data-ttu-id="d83b7-1062">Поле сведений 3. Длина имени в формате Юникода.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1062">Info Field 3: Length of Unicode name.</span></span>
- <span data-ttu-id="d83b7-1063">Поле сведений 4. Указатель на краткое имя.</span><span class="sxs-lookup"><span data-stu-id="d83b7-1063">Info Field 4: Pointer to short name.</span></span>