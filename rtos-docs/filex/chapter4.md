---
title: Глава 4. Описание служб FileX для ОСРВ Azure
description: В этой главе содержится описание всех служб FileX для ОСРВ Azure в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c9e91244856b322d53f85bdd572bd317a055776a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815083"
---
# <a name="chapter-4--description-of-azure-rtos-filex-services"></a><span data-ttu-id="887e6-103">Глава 4. Описание служб FileX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="887e6-103">Chapter 4- Description of Azure RTOS FileX services</span></span>

<span data-ttu-id="887e6-104">В этой главе содержится описание всех служб FileX для ОСРВ Azure в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="887e6-104">This chapter contains a description of all Azure RTOS FileX services in alphabetic order.</span></span> <span data-ttu-id="887e6-105">Имена служб реализованы так, что все аналогичные службы группируются вместе.</span><span class="sxs-lookup"><span data-stu-id="887e6-105">Service names are designed so all similar services are grouped together.</span></span>

## <a name="fx_directory_attributes_read"></a><span data-ttu-id="887e6-106">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-106">fx_directory_attributes_read</span></span>

<span data-ttu-id="887e6-107">Считывает атрибуты каталога</span><span class="sxs-lookup"><span data-stu-id="887e6-107">Reads directory attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-108">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-108">Prototype</span></span>

```c
UINT fx_directory_attributes_read ( 
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes_ptr);
```

### <a name="description"></a><span data-ttu-id="887e6-109">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-109">Description</span></span>

<span data-ttu-id="887e6-110">Эта служба считывает атрибуты каталога с указанного носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-110">This service reads the directory's attributes from the specified media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-111">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-111">Input Parameters</span></span>

- <span data-ttu-id="887e6-112">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-112">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="887e6-113">**directory_name**: указатель на имя запрашиваемого каталога (путь к каталогу является необязательным)</span><span class="sxs-lookup"><span data-stu-id="887e6-113">**directory_name**: Pointer to the name of the requested directory (directory path is optional).</span></span>
- <span data-ttu-id="887e6-114">**attributes_ptr**: указатель на назначение для размещения атрибутов каталога</span><span class="sxs-lookup"><span data-stu-id="887e6-114">**attributes** _ptr: Pointer to the destination for the directory's attributes to be placed.</span></span> <span data-ttu-id="887e6-115">Атрибуты каталога возвращаются в формате битовой карты со следующими возможными параметрами.</span><span class="sxs-lookup"><span data-stu-id="887e6-115">The directory attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="887e6-116">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="887e6-116">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="887e6-117">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="887e6-117">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="887e6-118">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="887e6-118">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="887e6-119">FX_VOLUME (0x08)</span><span class="sxs-lookup"><span data-stu-id="887e6-119">FX_VOLUME (0x08)</span></span>
  - <span data-ttu-id="887e6-120">FX_DIRECTORY (0x10)</span><span class="sxs-lookup"><span data-stu-id="887e6-120">FX_DIRECTORY (0x10)</span></span>
  - <span data-ttu-id="887e6-121">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="887e6-121">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-122">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-122">Return Values</span></span>

- <span data-ttu-id="887e6-123">**FX_SUCCESS** (0x00) — атрибуты каталога успешно считаны.</span><span class="sxs-lookup"><span data-stu-id="887e6-123">**FX_SUCCESS** (0x00) Successful directory attributes read</span></span>
- <span data-ttu-id="887e6-124">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-124">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="887e6-125">**FX_NOT_FOUND** (0x04) — указанный каталог не найден на носителе.</span><span class="sxs-lookup"><span data-stu-id="887e6-125">**FX _NOT FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="887e6-126">**FX_NOT_DIRECTORY** (0x0E) — запись является каталогом.</span><span class="sxs-lookup"><span data-stu-id="887e6-126">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory</span></span>
- <span data-ttu-id="887e6-127">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-127">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="887e6-128">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-128">**FX_FILE_CORRUPT** 0x08) File is corrupted</span></span>
- <span data-ttu-id="887e6-129">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-129">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="887e6-130">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-130">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="887e6-131">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="887e6-131">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="887e6-132">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="887e6-132">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="887e6-133">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-133">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="887e6-134">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-134">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-135">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-135">Allowed From</span></span>

<span data-ttu-id="887e6-136">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-136">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-137">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-137">Example</span></span>

```c
FX_MEDIA     my_media;
UINT     status;
/* Retrieve the attributes of "mydir" from the specified media.*/
status = fx_directory_attributes_read(&my_media, "mydir", &attributes);
/* If status equals FX_SUCCESS, "attributes" contains the directory attributes of "mydir". */
```

### <a name="see-also"></a><span data-ttu-id="887e6-138">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-138">See Also</span></span>

- <span data-ttu-id="887e6-139">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-139">fx_directory_attributes_set</span></span>
- <span data-ttu-id="887e6-140">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-140">fx_directory_create</span></span>
- <span data-ttu-id="887e6-141">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="887e6-141">fx_directory_default_get</span></span>
- <span data-ttu-id="887e6-142">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="887e6-142">fx_directory_default_set</span></span>
- <span data-ttu-id="887e6-143">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-143">fx_directory_delete</span></span>
- <span data-ttu-id="887e6-144">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-144">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="887e6-145">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-145">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="887e6-146">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="887e6-146">fx_directory_information_get</span></span>
- <span data-ttu-id="887e6-147">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="887e6-147">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="887e6-148">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="887e6-148">fx_directory_local_path_get</span></span>
- <span data-ttu-id="887e6-149">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="887e6-149">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="887e6-150">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="887e6-150">fx_directory_local_path_set</span></span>
- <span data-ttu-id="887e6-151">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-151">fx_directory_long_name_get</span></span>
- <span data-ttu-id="887e6-152">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="887e6-152">fx_directory_name_test</span></span>
- <span data-ttu-id="887e6-153">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-153">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="887e6-154">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-154">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="887e6-155">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-155">fx_directory_rename</span></span>
- <span data-ttu-id="887e6-156">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-156">fx_directory_short_name_get</span></span>
- <span data-ttu-id="887e6-157">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-157">fx_unicode_directory_create</span></span>
- <span data-ttu-id="887e6-158">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-158">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_attributes_set"></a><span data-ttu-id="887e6-159">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-159">fx_directory_attributes_set</span></span>

<span data-ttu-id="887e6-160">Задает атрибуты каталога</span><span class="sxs-lookup"><span data-stu-id="887e6-160">Sets directory attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-161">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-161">Prototype</span></span>

```c
UINT fx_directory_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes);
```

### <a name="description"></a><span data-ttu-id="887e6-162">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-162">Description</span></span>

<span data-ttu-id="887e6-163">Эта служба задает атрибуты каталога, указанные вызывающим объектом.</span><span class="sxs-lookup"><span data-stu-id="887e6-163">This service sets the directory's attributes to those specified by the caller.</span></span>

> [!WARNING]
> <span data-ttu-id="887e6-164">*Этому приложению разрешено изменять только подмножество атрибутов каталога, используя эту службу. Любая попытка задать дополнительные атрибуты приведет к ошибке.*</span><span class="sxs-lookup"><span data-stu-id="887e6-164">*This application is only allowed to modify a subset of the directory's attributes with this service. Any attempt to set additional attributes will result in an error.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-165">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-165">Input Parameters</span></span>

- <span data-ttu-id="887e6-166">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-166">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="887e6-167">**directory_name**: указатель на имя запрашиваемого каталога (путь к каталогу является необязательным)</span><span class="sxs-lookup"><span data-stu-id="887e6-167">**directory_name**: Pointer to the name of the requested directory (directory path is optional).</span></span>
- <span data-ttu-id="887e6-168">**attributes**: новые атрибуты для этого каталога</span><span class="sxs-lookup"><span data-stu-id="887e6-168">**attributes**: The new attributes to this directory.</span></span> <span data-ttu-id="887e6-169">Допустимые атрибуты каталога определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="887e6-169">The valid directory attributes are defined as follows:</span></span>
  - <span data-ttu-id="887e6-170">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="887e6-170">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="887e6-171">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="887e6-171">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="887e6-172">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="887e6-172">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="887e6-173">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="887e6-173">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-174">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-174">Return Values</span></span>

- <span data-ttu-id="887e6-175">**FX_SUCCESS** (0x00) — атрибут каталога успешно задан.</span><span class="sxs-lookup"><span data-stu-id="887e6-175">**FX_SUCCESS** (0x00) Successful directory attribute set</span></span>
- <span data-ttu-id="887e6-176">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-176">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="887e6-177">**FX_NOT_FOUND** (0x04) — указанный каталог не найден на носителе.</span><span class="sxs-lookup"><span data-stu-id="887e6-177">**FX_NOT_FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="887e6-178">**FX_NOT_DIRECTORY** (0x0E) — запись является каталогом.</span><span class="sxs-lookup"><span data-stu-id="887e6-178">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory</span></span>
- <span data-ttu-id="887e6-179">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-179">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="887e6-180">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-180">**FX_WRITE_PROTECT** (0x23) Specified media is write protected</span></span>
- <span data-ttu-id="887e6-181">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-181">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="887e6-182">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-182">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="887e6-183">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-183">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="887e6-184">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="887e6-184">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="887e6-185">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="887e6-185">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="887e6-186">**FX_NO_MORE_ENTRIES** (0x0F) — в этом каталоге больше нет записей.</span><span class="sxs-lookup"><span data-stu-id="887e6-186">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="887e6-187">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-187">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="887e6-188">**FX_INVALID_ATTR** (0x19) — выбраны недопустимые атрибуты.</span><span class="sxs-lookup"><span data-stu-id="887e6-188">**FX_INVALID_ATTR** (0x19) Invalid attributes selected.</span></span>
- <span data-ttu-id="887e6-189">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-189">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-190">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-190">Allowed From</span></span>

<span data-ttu-id="887e6-191">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-191">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-192">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-192">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
status = fx_directory_attributes_set(&my_media, "mydir", FX_READ_ONLY);
/*Set the attributes of "mydir" to read-only. */
/* If status equals FX_SUCCESS, the directory "mydir" is read-only. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-193">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-193">See Also</span></span>

- <span data-ttu-id="887e6-194">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-194">fx_directory_attributes_read</span></span>
- <span data-ttu-id="887e6-195">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-195">fx_directory_create</span></span>
- <span data-ttu-id="887e6-196">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="887e6-196">fx_directory_default_get</span></span>
- <span data-ttu-id="887e6-197">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="887e6-197">fx_directory_default_set</span></span>
- <span data-ttu-id="887e6-198">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-198">fx_directory_delete</span></span>
- <span data-ttu-id="887e6-199">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-199">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="887e6-200">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-200">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="887e6-201">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="887e6-201">fx_directory_information_get</span></span>
- <span data-ttu-id="887e6-202">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="887e6-202">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="887e6-203">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="887e6-203">fx_directory_local_path_get</span></span>
- <span data-ttu-id="887e6-204">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="887e6-204">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="887e6-205">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="887e6-205">fx_directory_local_path_set</span></span>
- <span data-ttu-id="887e6-206">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-206">fx_directory_long_name_get</span></span>
- <span data-ttu-id="887e6-207">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="887e6-207">fx_directory_name_test</span></span>
- <span data-ttu-id="887e6-208">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-208">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="887e6-209">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-209">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="887e6-210">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-210">fx_directory_rename</span></span>
- <span data-ttu-id="887e6-211">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-211">fx_directory_short_name_get</span></span>
- <span data-ttu-id="887e6-212">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-212">fx_unicode_directory_create</span></span>
- <span data-ttu-id="887e6-213">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-213">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_create"></a><span data-ttu-id="887e6-214">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-214">fx_directory_create</span></span>

<span data-ttu-id="887e6-215">Создает подкаталог</span><span class="sxs-lookup"><span data-stu-id="887e6-215">Creates subdirectory</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-216">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-216">Prototype</span></span>

```c
UINT fx_directory_create(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```
### <a name="description"></a><span data-ttu-id="887e6-217">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-217">Description</span></span>

<span data-ttu-id="887e6-218">Эта служба создает подкаталог в текущем каталоге по умолчанию или в пути, указанном в имени каталога.</span><span class="sxs-lookup"><span data-stu-id="887e6-218">This service creates a subdirectory in the current default directory or in the path supplied in the directory name.</span></span> <span data-ttu-id="887e6-219">В отличие от корневого каталога подкаталоги не имеют ограничения на количество файлов, которые могут в них храниться.</span><span class="sxs-lookup"><span data-stu-id="887e6-219">Unlike the root directory, subdirectories do not have a limit on the number of files they can hold.</span></span> <span data-ttu-id="887e6-220">Корневой каталог может содержать только число записей, которое определено загрузочной записью.</span><span class="sxs-lookup"><span data-stu-id="887e6-220">The root directory can only hold the number of entries determined by the boot record.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-221">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-221">Input Parameters</span></span>

- <span data-ttu-id="887e6-222">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-222">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="887e6-223">**directory_name**: указатель на имя создаваемого каталога (путь к каталогу является необязательным)</span><span class="sxs-lookup"><span data-stu-id="887e6-223">**directory_name**: Pointer to the name of the directory to create (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-224">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-224">Return Values</span></span>

- <span data-ttu-id="887e6-225">**FX_SUCCESS** (0x00) — каталог успешно создан.</span><span class="sxs-lookup"><span data-stu-id="887e6-225">**FX_SUCCESS** (0x00) Successful directory create.</span></span>
- <span data-ttu-id="887e6-226">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-226">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="887e6-227">**FX_NOT_FOUND** (0x04) — указанный каталог не найден на носителе.</span><span class="sxs-lookup"><span data-stu-id="887e6-227">**FX_NOT_FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="887e6-228">**FX_NOT_DIRECTORY** (0x0E) — запись является каталогом.</span><span class="sxs-lookup"><span data-stu-id="887e6-228">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory</span></span>
- <span data-ttu-id="887e6-229">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-229">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="887e6-230">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-230">**FX_FILE _CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="887e6-231">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-231">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="887e6-232">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-232">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="887e6-233">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="887e6-233">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="887e6-234">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="887e6-234">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="887e6-235">**FX_NO_MORE_ENTRIES** (0x0F) — в этом каталоге больше нет записей.</span><span class="sxs-lookup"><span data-stu-id="887e6-235">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="887e6-236">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-236">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="887e6-237">**FX_INVALID_ATTR** (0x19) — выбраны недопустимые атрибуты.</span><span class="sxs-lookup"><span data-stu-id="887e6-237">**FX_INVALID_ATTR** (0x19) Invalid attributes selected.</span></span>
- <span data-ttu-id="887e6-238">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-238">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-239">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-239">Allowed From</span></span>

<span data-ttu-id="887e6-240">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-240">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-241">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-241">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
/* Create a subdirectory called "temp" in the current default directory. */

status = fx_directory_create(&my_media, "temp");

/* If status equals FX_SUCCESS, the new subdirectory "temp" has been created. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-242">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-242">See Also</span></span>

- <span data-ttu-id="887e6-243">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-243">fx_directory_attributes_read</span></span>
- <span data-ttu-id="887e6-244">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-244">fx_directory_attributes_set</span></span>
- <span data-ttu-id="887e6-245">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="887e6-245">fx_directory_default_get</span></span>
- <span data-ttu-id="887e6-246">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="887e6-246">fx_directory_default_set</span></span>
- <span data-ttu-id="887e6-247">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-247">fx_directory_delete</span></span>
- <span data-ttu-id="887e6-248">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-248">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="887e6-249">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-249">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="887e6-250">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="887e6-250">fx_directory_information_get</span></span>
- <span data-ttu-id="887e6-251">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="887e6-251">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="887e6-252">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="887e6-252">fx_directory_local_path_get</span></span>
- <span data-ttu-id="887e6-253">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="887e6-253">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="887e6-254">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="887e6-254">fx_directory_local_path_set</span></span>
- <span data-ttu-id="887e6-255">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-255">fx_directory_long_name_get</span></span>
- <span data-ttu-id="887e6-256">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="887e6-256">fx_directory_name_test</span></span>
- <span data-ttu-id="887e6-257">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-257">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="887e6-258">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-258">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="887e6-259">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-259">fx_directory_rename</span></span>
- <span data-ttu-id="887e6-260">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-260">fx_directory_short_name_get</span></span>
- <span data-ttu-id="887e6-261">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-261">fx_unicode_directory_create</span></span>
- <span data-ttu-id="887e6-262">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-262">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_default_get"></a><span data-ttu-id="887e6-263">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="887e6-263">fx_directory_default_get</span></span>

<span data-ttu-id="887e6-264">Получает последний каталог по умолчанию</span><span class="sxs-lookup"><span data-stu-id="887e6-264">Gets last default directory</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-265">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-265">Prototype</span></span>

```c
UINT fx_directory_default_get(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a><span data-ttu-id="887e6-266">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-266">Description</span></span>

<span data-ttu-id="887e6-267">Эта служба возвращает указатель на путь, заданный службой ***fx_directory_default_set*** в последний раз.</span><span class="sxs-lookup"><span data-stu-id="887e6-267">This service returns the pointer to the path last set by ***fx_directory_default_set***.</span></span> <span data-ttu-id="887e6-268">Если каталог по умолчанию не задан или текущий каталог по умолчанию является корневым каталогом, возвращается значение FX_NULL.</span><span class="sxs-lookup"><span data-stu-id="887e6-268">If the default directory has not been set or if the current default directory is the root directory, a value of FX_NULL is returned.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="887e6-269">*Размер по умолчанию для строки внутреннего пути составляет 256 символов; можно указать другой размер, изменив **FX_MAXIMUM_PATH** в файле **fx_api. h** и перестроив всю библиотеку FileX. Путь к строке символов сохраняется для приложения и не используется FileX внутри.*</span><span class="sxs-lookup"><span data-stu-id="887e6-269">*The default size of the internal path string is 256 characters; it can be changed by modifying **FX_MAXIMUM_PATH** in **fx_api.h** and rebuilding the entire FileX library. The character string path is maintained for the application and is not used internally by FileX.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-270">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-270">Input Parameters</span></span>

- <span data-ttu-id="887e6-271">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-271">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="887e6-272">**return_path_name**: указатель на назначение для последней строки каталога по умолчанию</span><span class="sxs-lookup"><span data-stu-id="887e6-272">**return_path_name**: Pointer to the destination for the last default directory string.</span></span> <span data-ttu-id="887e6-273">Если текущим значением каталога по умолчанию является корневой каталог, возвращается значение FX_NULL.</span><span class="sxs-lookup"><span data-stu-id="887e6-273">A value of FX_NULL is returned if the current setting of the default directory is the root.</span></span> <span data-ttu-id="887e6-274">При открытии носителя по умолчанию используется корневой каталог.</span><span class="sxs-lookup"><span data-stu-id="887e6-274">When the media is opened, root is the default.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-275">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-275">Return Values</span></span>

- <span data-ttu-id="887e6-276">**FX_SUCCESS** (0x00) — каталог по умолчанию успешно получен.</span><span class="sxs-lookup"><span data-stu-id="887e6-276">**FX_SUCCESS** (0x00) Successful default directory get</span></span>
- <span data-ttu-id="887e6-277">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-277">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="887e6-278">**FX_PTR_ERROR** (0x18) — недопустимый указатель места назначения или носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-278">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer.</span></span>
- <span data-ttu-id="887e6-279">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-279">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-280">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-280">Allowed From</span></span>

<span data-ttu-id="887e6-281">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-281">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-282">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-282">Example</span></span>

```c
FX_MEDIA my_media;
CHAR *current_default_dir;
UINT status;
/* Retrieve the current default directory. */
status = fx_directory_default_get(&my_media, &current_default_dir);
/* If status equals FX_SUCCESS, "current_default_dir" 
    contains a pointer to the current default directory).*/
```

### <a name="see-also"></a><span data-ttu-id="887e6-283">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-283">See Also</span></span>

- <span data-ttu-id="887e6-284">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-284">fx_directory_attributes_read</span></span>
- <span data-ttu-id="887e6-285">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-285">fx_directory_attributes_set</span></span>
- <span data-ttu-id="887e6-286">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-286">fx_directory_create</span></span>
- <span data-ttu-id="887e6-287">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="887e6-287">fx_directory_default_set</span></span>
- <span data-ttu-id="887e6-288">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-288">fx_directory_delete</span></span>
- <span data-ttu-id="887e6-289">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-289">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="887e6-290">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-290">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="887e6-291">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="887e6-291">fx_directory_information_get</span></span>
- <span data-ttu-id="887e6-292">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="887e6-292">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="887e6-293">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="887e6-293">fx_directory_local_path_get</span></span>
- <span data-ttu-id="887e6-294">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="887e6-294">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="887e6-295">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="887e6-295">fx_directory_local_path_set</span></span>
- <span data-ttu-id="887e6-296">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-296">fx_directory_long_name_get</span></span>
- <span data-ttu-id="887e6-297">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="887e6-297">fx_directory_name_test</span></span>
- <span data-ttu-id="887e6-298">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-298">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="887e6-299">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-299">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="887e6-300">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-300">fx_directory_rename</span></span>
- <span data-ttu-id="887e6-301">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-301">fx_directory_short_name_get</span></span>
- <span data-ttu-id="887e6-302">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-302">fx_unicode_directory_create</span></span>
- <span data-ttu-id="887e6-303">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-303">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_default_set"></a><span data-ttu-id="887e6-304">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="887e6-304">fx_directory_default_set</span></span>

<span data-ttu-id="887e6-305">Задает каталог по умолчанию</span><span class="sxs-lookup"><span data-stu-id="887e6-305">Sets default directory</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-306">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-306">Prototype</span></span>

```c

UINT fx_directory_default_set(
    FX_MEDIA *media_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a><span data-ttu-id="887e6-307">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-307">Description</span></span>

<span data-ttu-id="887e6-308">Эта служба задает каталог по умолчанию для носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-308">This service sets the default directory of the media.</span></span> <span data-ttu-id="887e6-309">Если указано значение FX_NULL, то в качестве каталога по умолчанию задается корневой каталог носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-309">If a value of FX_NULL is supplied, the default directory is set to the media's root directory.</span></span> <span data-ttu-id="887e6-310">Все последующие операции с файлами, в которых явно не указан путь, по умолчанию будут использовать этот каталог.</span><span class="sxs-lookup"><span data-stu-id="887e6-310">All subsequent file operations that do not explicitly specify a path will default to this directory.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="887e6-311">*Размер по умолчанию для строки внутреннего пути составляет 256 символов; можно указать другой размер, изменив **FX_MAXIMUM_PATH** в файле **fx_api. h** и перестроив всю библиотеку FileX. Путь к строке символов сохраняется для приложения и не используется FileX внутри.*</span><span class="sxs-lookup"><span data-stu-id="887e6-311">*The default size of the internal path string is 256 characters; it can be changed by modifying **FX_MAXIMUM_PATH** in **fx_api.h** and rebuilding the entire FileX library. The character string path is maintained for the application and is not used internally by FileX.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="887e6-312">*Для имен, предоставленных приложением, FileX поддерживает как обратную косую черту (\\), так и символ косой черты (/) для разделения каталогов, подкаталогов и имен файлов. Однако в путях, возвращаемых приложению, FileX использует только символ обратной косой черты.*</span><span class="sxs-lookup"><span data-stu-id="887e6-312">*For names supplied by the application, FileX supports both backslash (\\) and forward slash (/) characters to separate directories, subdirectories, and file names. However, FileX only uses the backslash character in paths returned to the application.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-313">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-313">Input Parameters</span></span>

- <span data-ttu-id="887e6-314">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-314">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="887e6-315">**new_path_name**: указатель на новое имя каталога по умолчанию</span><span class="sxs-lookup"><span data-stu-id="887e6-315">**new_path_name**: Pointer to new default directory name.</span></span> <span data-ttu-id="887e6-316">Если указано значение FX_NULL, то в качестве каталога носителя по умолчанию задается корневой каталог носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-316">If a value of FX_NULL is supplied, the default directory of the media is set to the media's root directory.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-317">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-317">Return Values</span></span>

- <span data-ttu-id="887e6-318">**FX_SUCCESS** (0x00) — каталог по умолчанию успешно задан.</span><span class="sxs-lookup"><span data-stu-id="887e6-318">**FX_SUCCESS** (0x00)  Successful default directory set</span></span>
- <span data-ttu-id="887e6-319">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-319">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="887e6-320">**FX_INVALID_PATH** (0x0D) — не удалось найти новый каталог.</span><span class="sxs-lookup"><span data-stu-id="887e6-320">**FX_INVALID_PATH** (0x0D) New directory could not be found</span></span>
- <span data-ttu-id="887e6-321">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-321">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="887e6-322">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-322">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-323">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-323">Allowed From</span></span>

<span data-ttu-id="887e6-324">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-324">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-325">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-325">Example</span></span>

```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_default_set(&my_media, "\\abc\\def\\ghi");
/* If status equals FX_SUCCESS, the default directory for this media is \abc\def\ghi. All subsequent file operations that do not explicitly specify a path will default to this directory. Note that the character "\" serves as an escape character in a string. To represent the character "\", use the construct "\\". This is done because of the C language- only one "\" is really present in the string. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-326">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-326">See Also</span></span>

- <span data-ttu-id="887e6-327">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-327">fx_directory_attributes_read</span></span>
- <span data-ttu-id="887e6-328">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-328">fx_directory_attributes_set</span></span>
- <span data-ttu-id="887e6-329">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-329">fx_directory_create</span></span>
- <span data-ttu-id="887e6-330">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="887e6-330">fx_directory_default_get</span></span>
- <span data-ttu-id="887e6-331">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-331">fx_directory_delete</span></span>
- <span data-ttu-id="887e6-332">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-332">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="887e6-333">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-333">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="887e6-334">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="887e6-334">fx_directory_information_get</span></span>
- <span data-ttu-id="887e6-335">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="887e6-335">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="887e6-336">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="887e6-336">fx_directory_local_path_get</span></span>
- <span data-ttu-id="887e6-337">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="887e6-337">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="887e6-338">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="887e6-338">fx_directory_local_path_set</span></span>
- <span data-ttu-id="887e6-339">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-339">fx_directory_long_name_get</span></span>
- <span data-ttu-id="887e6-340">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="887e6-340">fx_directory_name_test</span></span>
- <span data-ttu-id="887e6-341">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-341">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="887e6-342">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-342">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="887e6-343">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-343">fx_directory_rename</span></span>
- <span data-ttu-id="887e6-344">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-344">fx_directory_short_name_get</span></span>
- <span data-ttu-id="887e6-345">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-345">fx_unicode_directory_create</span></span>
- <span data-ttu-id="887e6-346">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-346">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_delete"></a><span data-ttu-id="887e6-347">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-347">fx_directory_delete</span></span>

<span data-ttu-id="887e6-348">Удаляет подкаталог</span><span class="sxs-lookup"><span data-stu-id="887e6-348">Deletes subdirectory</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-349">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-349">Prototype</span></span>

```c
UINT fx_directory_delete(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a><span data-ttu-id="887e6-350">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-350">Description</span></span>

<span data-ttu-id="887e6-351">Эта служба удаляет указанный каталог.</span><span class="sxs-lookup"><span data-stu-id="887e6-351">This service deletes the specified directory.</span></span> <span data-ttu-id="887e6-352">Обратите внимание, что каталог должен быть пустым, чтобы его можно было удалить.</span><span class="sxs-lookup"><span data-stu-id="887e6-352">Note that the directory must be empty to delete it.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-353">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-353">Input Parameters</span></span>

- <span data-ttu-id="887e6-354">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-354">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="887e6-355">**directory_name**: указатель на имя удаляемого каталога (путь к каталогу является необязательным)</span><span class="sxs-lookup"><span data-stu-id="887e6-355">**directory_name**: Pointer to name of directory to delete (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-356">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-356">Return Values</span></span>

- <span data-ttu-id="887e6-357">**FX_SUCCESS** (0x00) — каталог успешно удален.</span><span class="sxs-lookup"><span data-stu-id="887e6-357">**FX_SUCCESS** (0x00) Successful directory delete</span></span>
- <span data-ttu-id="887e6-358">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-358">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="887e6-359">**FX_NOT_FOUND** (0x04) — указанный каталог не найден.</span><span class="sxs-lookup"><span data-stu-id="887e6-359">**FX_NOT_FOUND** (0x04) Specified directory was not found</span></span>
- <span data-ttu-id="887e6-360">**FX_DIR_NOT_EMPTY** (0x10) — указанный каталог не пуст.</span><span class="sxs-lookup"><span data-stu-id="887e6-360">**FX_DIR_NOT_EMPTY** (0x10) Specified directory is not empty</span></span>
- <span data-ttu-id="887e6-361">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-361">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="887e6-362">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-362">**FX_WRITE_PROTECT** (0x23) Specified media is write protected</span></span>
- <span data-ttu-id="887e6-363">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-363">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="887e6-364">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-364">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="887e6-365">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-365">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="887e6-366">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="887e6-366">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="887e6-367">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="887e6-367">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="887e6-368">**FX_NO_MORE_ENTRIES** (0x0F) — в этом каталоге больше нет записей.</span><span class="sxs-lookup"><span data-stu-id="887e6-368">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="887e6-369">**FX_NOT_DIRECTORY** (0x0E) — не является записью каталога.</span><span class="sxs-lookup"><span data-stu-id="887e6-369">**FX_NOT_DIRECTORY** (0x0E) Not a directory entry</span></span>
- <span data-ttu-id="887e6-370">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-370">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="887e6-371">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-371">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-372">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-372">Allowed From</span></span>

<span data-ttu-id="887e6-373">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-373">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-374">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-374">Example</span></span>
```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_delete(&my_media, "abc");
/* Delete the subdirectory "abc." */
/* If status equals FX_SUCCESS, the subdirectory "abc" was deleted. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-375">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-375">See Also</span></span>

- <span data-ttu-id="887e6-376">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-376">fx_directory_attributes_read</span></span>
- <span data-ttu-id="887e6-377">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-377">fx_directory_attributes_set</span></span>
- <span data-ttu-id="887e6-378">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-378">fx_directory_create</span></span>
- <span data-ttu-id="887e6-379">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="887e6-379">fx_directory_default_get</span></span>
- <span data-ttu-id="887e6-380">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="887e6-380">fx_directory_default_set</span></span>
- <span data-ttu-id="887e6-381">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-381">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="887e6-382">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-382">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="887e6-383">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="887e6-383">fx_directory_information_get</span></span>
- <span data-ttu-id="887e6-384">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="887e6-384">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="887e6-385">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="887e6-385">fx_directory_local_path_get</span></span>
- <span data-ttu-id="887e6-386">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="887e6-386">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="887e6-387">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="887e6-387">fx_directory_local_path_set</span></span>
- <span data-ttu-id="887e6-388">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-388">fx_directory_long_name_get</span></span>
- <span data-ttu-id="887e6-389">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="887e6-389">fx_directory_name_test</span></span>
- <span data-ttu-id="887e6-390">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-390">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="887e6-391">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-391">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="887e6-392">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-392">fx_directory_rename</span></span>
- <span data-ttu-id="887e6-393">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-393">fx_directory_short_name_get</span></span>
- <span data-ttu-id="887e6-394">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-394">fx_unicode_directory_create</span></span>
- <span data-ttu-id="887e6-395">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-395">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_first_entry_find"></a><span data-ttu-id="887e6-396">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-396">fx_directory_first_entry_find</span></span>

<span data-ttu-id="887e6-397">Получает первую запись каталога</span><span class="sxs-lookup"><span data-stu-id="887e6-397">Gets first directory entry</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-398">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-398">Prototype</span></span>

```c
UINT fx_directory_first_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a><span data-ttu-id="887e6-399">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-399">Description</span></span>

<span data-ttu-id="887e6-400">Эта служба получает имя первой записи в каталоге по умолчанию и копирует его в указанное место назначения.</span><span class="sxs-lookup"><span data-stu-id="887e6-400">This service retrieves the first entry name in the default directory and copies it to the specified destination.</span></span>

> [!WARNING]
> <span data-ttu-id="887e6-401">*Указанное назначение должно быть достаточно большим, чтобы вместить имя FileX максимального размера, как определено **FX_MAX_LONG_NAME_LEN.***</span><span class="sxs-lookup"><span data-stu-id="887e6-401">*The specified destination must be large enough to hold the maximum sized FileX name, as defined by **FX_MAX_LONG_NAME_LEN.***</span></span>

> [!WARNING]
> <span data-ttu-id="887e6-402">*При использовании нелокального пути важно предотвратить изменение этого каталога (с помощью семафора ThreadX, мьютекса или изменения уровня приоритета) другими потоками приложения во время обхода каталога. В противном случае могут быть получены недопустимые результаты.*</span><span class="sxs-lookup"><span data-stu-id="887e6-402">*If using a non-local path, it is important to prevent (with a ThreadX semaphore, mutex, or priority level change) other application threads from changing this directory while a directory traversal is taking place. Otherwise, invalid results may be obtained.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-403">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-403">Input Parameters</span></span>

- <span data-ttu-id="887e6-404">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-404">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="887e6-405">**return_entry_name**: указатель на назначение для имени первой записи в каталоге по умолчанию</span><span class="sxs-lookup"><span data-stu-id="887e6-405">**return_entry_name**: Pointer to destination for the first entry name in the default directory.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-406">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-406">Return Values</span></span>

- <span data-ttu-id="887e6-407">**FX_SUCCESS** (0x00) — первая запись каталога успешно найдена.</span><span class="sxs-lookup"><span data-stu-id="887e6-407">**FX_SUCCESS** (0x00) Successful first directory entry find</span></span>
- <span data-ttu-id="887e6-408">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-408">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="887e6-409">**FX_NO_MORE_ENTRIES** (0x0F) — в этом каталоге больше нет записей.</span><span class="sxs-lookup"><span data-stu-id="887e6-409">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="887e6-410">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-410">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="887e6-411">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-411">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="887e6-412">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-412">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="887e6-413">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-413">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="887e6-414">**FX_PTR_ERROR** (0x18) — недопустимый указатель места назначения или носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-414">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer</span></span>
- <span data-ttu-id="887e6-415">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-415">**FX_CALLER_ERROR** (0x20) Caller is not a thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-416">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-416">Allowed From</span></span>

<span data-ttu-id="887e6-417">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-417">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-418">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-418">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;
CHAR             entry[FX_MAX_LONG_NAME_LEN];
/* Retrieve the first directory entry in the current directory. */
status = fx_directory_first_entry_find(&my_media, entry);
/* If status equals FX_SUCCESS, the entry in the directory is the "entry" string. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-419">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-419">See Also</span></span>

- <span data-ttu-id="887e6-420">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-420">fx_directory_attributes_read</span></span>
- <span data-ttu-id="887e6-421">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-421">fx_directory_attributes_set</span></span>
- <span data-ttu-id="887e6-422">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-422">fx_directory_create</span></span>
- <span data-ttu-id="887e6-423">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="887e6-423">fx_directory_default_get</span></span>
- <span data-ttu-id="887e6-424">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="887e6-424">fx_directory_default_set</span></span>
- <span data-ttu-id="887e6-425">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-425">fx_directory_delete</span></span>
- <span data-ttu-id="887e6-426">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-426">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="887e6-427">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="887e6-427">fx_directory_information_get</span></span>
- <span data-ttu-id="887e6-428">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="887e6-428">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="887e6-429">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="887e6-429">fx_directory_local_path_get</span></span>
- <span data-ttu-id="887e6-430">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="887e6-430">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="887e6-431">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="887e6-431">fx_directory_local_path_set</span></span>
- <span data-ttu-id="887e6-432">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-432">fx_directory_long_name_get</span></span>
- <span data-ttu-id="887e6-433">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="887e6-433">fx_directory_name_test</span></span>
- <span data-ttu-id="887e6-434">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-434">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="887e6-435">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-435">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="887e6-436">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-436">fx_directory_rename</span></span>
- <span data-ttu-id="887e6-437">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-437">fx_directory_short_name_get</span></span>
- <span data-ttu-id="887e6-438">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-438">fx_unicode_directory_create</span></span>
- <span data-ttu-id="887e6-439">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-439">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_first_full_entry_find"></a><span data-ttu-id="887e6-440">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-440">fx_directory_first_full_entry_find</span></span>

<span data-ttu-id="887e6-441">Получает первую запись каталога с полной информацией</span><span class="sxs-lookup"><span data-stu-id="887e6-441">Gets first directory entry with full information</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-442">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-442">Prototype</span></span>

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a><span data-ttu-id="887e6-443">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-443">Input Parameters</span></span>

- <span data-ttu-id="887e6-444">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-444">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="887e6-445">**directory_name**: указатель на назначение для имени записи каталога</span><span class="sxs-lookup"><span data-stu-id="887e6-445">**directory_name**: Pointer to the destination for the name of a directory entry.</span></span> <span data-ttu-id="887e6-446">Размер должен быть не меньше FX_MAX_LONG_NAME_LEN.</span><span class="sxs-lookup"><span data-stu-id="887e6-446">Must be at least as big as FX_MAX_LONG_NAME_LEN.</span></span>
- <span data-ttu-id="887e6-447">**attributes_ptr**: указатель на назначение для размещения атрибутов записи, если не NULL</span><span class="sxs-lookup"><span data-stu-id="887e6-447">**attributes**: If non-null, pointer to the destination for the entry's attributes to be placed.</span></span> <span data-ttu-id="887e6-448">Атрибуты возвращаются в формате битовой карты со следующими возможными параметрами.</span><span class="sxs-lookup"><span data-stu-id="887e6-448">The attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="887e6-449">**FX_READ_ONLY** (0x01)</span><span class="sxs-lookup"><span data-stu-id="887e6-449">**FX_READ_ONLY** (0x01)</span></span>
  - <span data-ttu-id="887e6-450">**FX_HIDDEN** (0x02)</span><span class="sxs-lookup"><span data-stu-id="887e6-450">**FX_HIDDEN** (0x02)</span></span>
  - <span data-ttu-id="887e6-451">**FX_SYSTEM** (0x04)</span><span class="sxs-lookup"><span data-stu-id="887e6-451">**FX_SYSTEM** (0x04)</span></span>
  - <span data-ttu-id="887e6-452">**FX_VOLUME** (0x08)</span><span class="sxs-lookup"><span data-stu-id="887e6-452">**FX_VOLUME** (0x08)</span></span>
  - <span data-ttu-id="887e6-453">**FX_DIRECTORY** (0x10)</span><span class="sxs-lookup"><span data-stu-id="887e6-453">**FX_DIRECTORY** (0x10)</span></span>
  - <span data-ttu-id="887e6-454">**FX_ARCHIVE** (0x20)</span><span class="sxs-lookup"><span data-stu-id="887e6-454">**FX_ARCHIVE** (0x20)</span></span>
- <span data-ttu-id="887e6-455">**size**: указатель на назначение для размера записи в байтах, если не NULL</span><span class="sxs-lookup"><span data-stu-id="887e6-455">**size**: If non-null, pointer to the destination for the entry's size in bytes.</span></span>
- <span data-ttu-id="887e6-456">**year**: указатель на назначение для года записи, если не NULL</span><span class="sxs-lookup"><span data-stu-id="887e6-456">**year**: If non-null, pointer to the destination for the entry's year of modification.</span></span>
- <span data-ttu-id="887e6-457">**month**: указатель на назначение для месяца записи, если не NULL</span><span class="sxs-lookup"><span data-stu-id="887e6-457">**month**: If non-null, pointer to the destination for the entry's month of modification.</span></span>
- <span data-ttu-id="887e6-458">**day**: указатель на назначение для дня записи, если не NULL</span><span class="sxs-lookup"><span data-stu-id="887e6-458">**day**: If non-null, pointer to the destination for the entry's day of modification.</span></span>
- <span data-ttu-id="887e6-459">**hour**: указатель на назначение для часа записи, если не NULL</span><span class="sxs-lookup"><span data-stu-id="887e6-459">**hour**: If non-null, pointer to the destination for the entry's hour of modification.</span></span>
- <span data-ttu-id="887e6-460">**minute**: указатель на назначение для минуты записи, если не NULL</span><span class="sxs-lookup"><span data-stu-id="887e6-460">**minute**: If non-null, pointer to the destination for the entry's minute of modification.</span></span>
- <span data-ttu-id="887e6-461">**second**: указатель на назначение для секунды записи, если не NULL</span><span class="sxs-lookup"><span data-stu-id="887e6-461">**second**: If non-null, pointer to the destination for the entry's second of modification.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-462">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-462">Return Values</span></span>

- <span data-ttu-id="887e6-463">**FX_SUCCESS** (0x00) — первая запись каталога успешно найдена.</span><span class="sxs-lookup"><span data-stu-id="887e6-463">**FX_SUCCESS** (0x00) Successful first directory entry find</span></span>
- <span data-ttu-id="887e6-464">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-464">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="887e6-465">**FX_NO_MORE_ENTRIES** (0x0F) — в этом каталоге больше нет записей.</span><span class="sxs-lookup"><span data-stu-id="887e6-465">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="887e6-466">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-466">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="887e6-467">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-467">**FX_WRITE_PROTECT** (0x23) Specified media is write protected</span></span>
- <span data-ttu-id="887e6-468">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-468">**FX_FILE _CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="887e6-469">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-469">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="887e6-470">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-470">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="887e6-471">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="887e6-471">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="887e6-472">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="887e6-472">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="887e6-473">**FX_PTR_ERROR** (0x18) — недопустимый указатель места назначения или носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-473">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer.</span></span>
- <span data-ttu-id="887e6-474">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-474">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-475">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-475">Allowed From</span></span>

<span data-ttu-id="887e6-476">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-476">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-477">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-477">Example</span></span>

```c
FX_MEDIA     my_media;
UINT         status;
CHAR         entry_name[FX_MAX_LONG_NAME_LEN];
UINT         attributes;
ULONG        size;
UINT         year;
UINT         month;
UINT         day;
UINT         hour;
UINT         minute;
UINT         second;
/* Get the first directory entry in the default directory with full information. */
status = fx_directory_first_full_entry_find(&my_media, entry_name,
    &attributes, &size, &year, &month, &day, &hour, &minute, &second);

/* If status equals FX_SUCCESS, the entry's information is in the local variables. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-478">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-478">See Also</span></span>

- <span data-ttu-id="887e6-479">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-479">fx_directory_attributes_read</span></span>
- <span data-ttu-id="887e6-480">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-480">fx_directory_attributes_set</span></span>
- <span data-ttu-id="887e6-481">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-481">fx_directory_create</span></span>
- <span data-ttu-id="887e6-482">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="887e6-482">fx_directory_default_get</span></span>
- <span data-ttu-id="887e6-483">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="887e6-483">fx_directory_default_set</span></span>
- <span data-ttu-id="887e6-484">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-484">fx_directory_delete</span></span>
- <span data-ttu-id="887e6-485">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-485">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="887e6-486">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="887e6-486">fx_directory_information_get</span></span>
- <span data-ttu-id="887e6-487">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="887e6-487">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="887e6-488">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="887e6-488">fx_directory_local_path_get</span></span>
- <span data-ttu-id="887e6-489">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="887e6-489">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="887e6-490">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="887e6-490">fx_directory_local_path_set</span></span>
- <span data-ttu-id="887e6-491">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-491">fx_directory_long_name_get</span></span>
- <span data-ttu-id="887e6-492">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="887e6-492">fx_directory_name_test</span></span>
- <span data-ttu-id="887e6-493">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-493">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="887e6-494">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-494">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="887e6-495">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-495">fx_directory_rename</span></span>
- <span data-ttu-id="887e6-496">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-496">fx_directory_short_name_get</span></span>
- <span data-ttu-id="887e6-497">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-497">fx_unicode_directory_create</span></span>
- <span data-ttu-id="887e6-498">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-498">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_information_get"></a><span data-ttu-id="887e6-499">fx_directory_information_get:</span><span class="sxs-lookup"><span data-stu-id="887e6-499">fx_directory_information_get:</span></span>

<span data-ttu-id="887e6-500">Получает сведения о записи каталога</span><span class="sxs-lookup"><span data-stu-id="887e6-500">Gets directory entry information</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-501">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-501">Prototype</span></span>

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a><span data-ttu-id="887e6-502">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-502">Input Parameters</span></span>

- <span data-ttu-id="887e6-503">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-503">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="887e6-504">**directory_name**: указатель на имя записи каталога</span><span class="sxs-lookup"><span data-stu-id="887e6-504">**directory_name**: Pointer to name of the directory entry.</span></span>
- <span data-ttu-id="887e6-505">**attributes**: указатель на назначение для атрибутов</span><span class="sxs-lookup"><span data-stu-id="887e6-505">**attributes**: Pointer to the destination for the attributes.</span></span>
- <span data-ttu-id="887e6-506">**size**: указатель на назначение для размера</span><span class="sxs-lookup"><span data-stu-id="887e6-506">**size**: Pointer to the destination for the size.</span></span>
- <span data-ttu-id="887e6-507">**year**: указатель на назначение для года</span><span class="sxs-lookup"><span data-stu-id="887e6-507">**year**: Pointer to the destination for the year.</span></span>
- <span data-ttu-id="887e6-508">**month**: указатель на назначение для месяца</span><span class="sxs-lookup"><span data-stu-id="887e6-508">**month**: Pointer to the destination for the month.</span></span>
- <span data-ttu-id="887e6-509">**day**: указатель на назначение для дня</span><span class="sxs-lookup"><span data-stu-id="887e6-509">**day**: Pointer to the destination for the day.</span></span>
- <span data-ttu-id="887e6-510">**hour**: указатель на назначение для часа</span><span class="sxs-lookup"><span data-stu-id="887e6-510">**hour**: Pointer to the destination for the hour.</span></span>
- <span data-ttu-id="887e6-511">**minute**: указатель на назначение для минуты</span><span class="sxs-lookup"><span data-stu-id="887e6-511">**minute**: Pointer to the destination for the minute.</span></span>
- <span data-ttu-id="887e6-512">**second**: указатель на назначение для секунды</span><span class="sxs-lookup"><span data-stu-id="887e6-512">**second**: Pointer to the destination for the second.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-513">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-513">Return Values</span></span>

- <span data-ttu-id="887e6-514">**FX_SUCCESS** (0x00) — первая запись каталога успешно найдена.</span><span class="sxs-lookup"><span data-stu-id="887e6-514">**FX_SUCCESS** (0x00) Successful first directory entry find</span></span>
- <span data-ttu-id="887e6-515">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-515">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="887e6-516">**FX_NOT_FOUND** (0x04) — указанный каталог не найден на носителе.</span><span class="sxs-lookup"><span data-stu-id="887e6-516">**FX_NOT_FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="887e6-517">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-517">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="887e6-518">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="887e6-518">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="887e6-519">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-519">**FX_FILE _CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="887e6-520">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-520">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="887e6-521">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="887e6-521">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="887e6-522">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-522">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="887e6-523">**FX_PTR_ERROR** (0x18) — недопустимый указатель места назначения или носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-523">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer.</span></span>
- <span data-ttu-id="887e6-524">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-524">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-525">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-525">Allowed From</span></span>

<span data-ttu-id="887e6-526">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-526">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-527">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-527">Example</span></span>

```c
FX_MEDIA     my_media;
UINT         status; attributes; year; month; day;
CHAR         entry_name[FX_MAX_LONG_NAME_LEN];
ULONG        size;
UINT         hour; minute; second;
/* Retrieve information about the directory entry "myfile.txt".*/
status = fx_directory_information_get(&my_media, "myfile.txt", &attributes, &size,
                                      &year, &month, &day,
                                      &hour, &minute, &second);
/* If status equals FX_SUCCESS, the directory entry information is available in the local variables. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-528">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-528">See Also</span></span>

- <span data-ttu-id="887e6-529">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-529">fx_directory_attributes_read</span></span>
- <span data-ttu-id="887e6-530">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-530">fx_directory_attributes_set</span></span>
- <span data-ttu-id="887e6-531">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-531">fx_directory_create</span></span>
- <span data-ttu-id="887e6-532">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="887e6-532">fx_directory_default_get</span></span>
- <span data-ttu-id="887e6-533">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="887e6-533">fx_directory_default_set</span></span>
- <span data-ttu-id="887e6-534">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-534">fx_directory_delete</span></span>
- <span data-ttu-id="887e6-535">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-535">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="887e6-536">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-536">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="887e6-537">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="887e6-537">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="887e6-538">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="887e6-538">fx_directory_local_path_get</span></span>
- <span data-ttu-id="887e6-539">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="887e6-539">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="887e6-540">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="887e6-540">fx_directory_local_path_set</span></span>
- <span data-ttu-id="887e6-541">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-541">fx_directory_long_name_get</span></span>
- <span data-ttu-id="887e6-542">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="887e6-542">fx_directory_name_test</span></span>
- <span data-ttu-id="887e6-543">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-543">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="887e6-544">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-544">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="887e6-545">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-545">fx_directory_rename</span></span>
- <span data-ttu-id="887e6-546">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-546">fx_directory_short_name_get</span></span>
- <span data-ttu-id="887e6-547">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-547">fx_unicode_directory_create</span></span>
- <span data-ttu-id="887e6-548">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-548">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_clear"></a><span data-ttu-id="887e6-549">fx_directory_local_path_clear:</span><span class="sxs-lookup"><span data-stu-id="887e6-549">fx_directory_local_path_clear:</span></span>

<span data-ttu-id="887e6-550">Очищает локальный путь по умолчанию</span><span class="sxs-lookup"><span data-stu-id="887e6-550">Clears default local path</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-551">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-551">Prototype</span></span>

```c
UINT fx_directory_local_path_clear(FX_MEDIA *media_ptr);
```

### <a name="description"></a><span data-ttu-id="887e6-552">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-552">Description</span></span>

<span data-ttu-id="887e6-553">Эта служба очищает предыдущий локальный путь, настроенный для вызывающего потока.</span><span class="sxs-lookup"><span data-stu-id="887e6-553">This service clears the previous local path set up for the calling thread.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-554">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-554">Input Parameters</span></span>

- <span data-ttu-id="887e6-555">**media_ptr**: указатель на открытый ранее носитель</span><span class="sxs-lookup"><span data-stu-id="887e6-555">**media_ptr**: Pointer to a previously opened media.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-556">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-556">Return Values</span></span>

- <span data-ttu-id="887e6-557">**FX_SUCCESS** (0x00) — локальный путь успешно очищен.</span><span class="sxs-lookup"><span data-stu-id="887e6-557">**FX_SUCCESS** (0x00) Successful local path clear.</span></span>
- <span data-ttu-id="887e6-558">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель в настоящее время не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-558">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not currently open</span></span>
- <span data-ttu-id="887e6-559">**FX_NOT_IMPLEMENTED** (0x22) — определен FX_NO_LCOAL_PATH.</span><span class="sxs-lookup"><span data-stu-id="887e6-559">**FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH is defined</span></span>
- <span data-ttu-id="887e6-560">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-560">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-561">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-561">Allowed From</span></span>

<span data-ttu-id="887e6-562">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-562">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-563">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-563">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
/* Clear the previously setup local path for this media. */
status = fx_directory_local_path_clear(&my_media);
/* If status equals FX_SUCCESS the local path is cleared. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-564">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-564">See Also</span></span>

- <span data-ttu-id="887e6-565">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-565">fx_directory_attributes_read</span></span>
- <span data-ttu-id="887e6-566">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-566">fx_directory_attributes_set</span></span>
- <span data-ttu-id="887e6-567">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-567">fx_directory_create</span></span>
- <span data-ttu-id="887e6-568">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="887e6-568">fx_directory_default_get</span></span>
- <span data-ttu-id="887e6-569">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="887e6-569">fx_directory_default_set</span></span>
- <span data-ttu-id="887e6-570">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-570">fx_directory_delete</span></span>
- <span data-ttu-id="887e6-571">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-571">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="887e6-572">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-572">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="887e6-573">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="887e6-573">fx_directory_information_get</span></span>
- <span data-ttu-id="887e6-574">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="887e6-574">fx_directory_local_path_get</span></span>
- <span data-ttu-id="887e6-575">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="887e6-575">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="887e6-576">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="887e6-576">fx_directory_local_path_set</span></span>
- <span data-ttu-id="887e6-577">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-577">fx_directory_long_name_get</span></span>
- <span data-ttu-id="887e6-578">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="887e6-578">fx_directory_name_test</span></span>
- <span data-ttu-id="887e6-579">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-579">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="887e6-580">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-580">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="887e6-581">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-581">fx_directory_rename</span></span>
- <span data-ttu-id="887e6-582">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-582">fx_directory_short_name_get</span></span>
- <span data-ttu-id="887e6-583">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-583">fx_unicode_directory_create</span></span>
- <span data-ttu-id="887e6-584">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-584">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_get"></a><span data-ttu-id="887e6-585">fx_directory_local_path_get:</span><span class="sxs-lookup"><span data-stu-id="887e6-585">fx_directory_local_path_get:</span></span>

<span data-ttu-id="887e6-586">Возвращает строку текущего локального пути</span><span class="sxs-lookup"><span data-stu-id="887e6-586">Gets the current local path string</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-587">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-587">Prototype</span></span>

```c
UINT fx_directory_local_path_clear(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a><span data-ttu-id="887e6-588">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-588">Description</span></span>

<span data-ttu-id="887e6-589">Эта служба возвращает указатель локального пути для указанного носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-589">This service returns the local path pointer of the specified media.</span></span> <span data-ttu-id="887e6-590">Если локальный путь не задан, вызывающему объекту возвращается значение NULL.</span><span class="sxs-lookup"><span data-stu-id="887e6-590">If there is no local path set, a NULL is returned to the caller.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-591">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-591">Input Parameters</span></span>

- <span data-ttu-id="887e6-592">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-592">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="887e6-593">**return_path_name**: указатель на указатель строки назначения для сохраняемой строки локального пути</span><span class="sxs-lookup"><span data-stu-id="887e6-593">**return_path_name**: Pointer to the destination string pointer for the local path string to be stored.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-594">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-594">Return Values</span></span>

- <span data-ttu-id="887e6-595">**FX_SUCCESS** (0x00) — локальный путь успешно получен.</span><span class="sxs-lookup"><span data-stu-id="887e6-595">**FX_SUCCESS** (0x00) Successful local path get.</span></span>
- <span data-ttu-id="887e6-596">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель в настоящее время не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-596">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not currently open</span></span>
- <span data-ttu-id="887e6-597">**FX_NOT_IMPLEMENTED** (0x22) — NX_NO_LCOAL_PATH</span><span class="sxs-lookup"><span data-stu-id="887e6-597">**FX_NOT_IMPLEMENTED** (0x22) NX_NO_LCOAL_PATH</span></span>
- <span data-ttu-id="887e6-598">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-598">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>


### <a name="allowed-from"></a><span data-ttu-id="887e6-599">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-599">Allowed From</span></span>

<span data-ttu-id="887e6-600">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-600">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-601">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-601">Example</span></span>

```c
FX_MEDIA         my_media;
CHAR             *my_path;
UINT             status;
/* Retrieve the current local path string. */
status = fx_directory_local_path_get(&my_media, &my_path);
/* If status equals FX_SUCCESS, "my_path" points to the local path string. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-602">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-602">See Also</span></span>

- <span data-ttu-id="887e6-603">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-603">fx_directory_attributes_read</span></span>
- <span data-ttu-id="887e6-604">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-604">fx_directory_attributes_set</span></span>
- <span data-ttu-id="887e6-605">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-605">fx_directory_create</span></span>
- <span data-ttu-id="887e6-606">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="887e6-606">fx_directory_default_get</span></span>
- <span data-ttu-id="887e6-607">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="887e6-607">fx_directory_default_set</span></span>
- <span data-ttu-id="887e6-608">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-608">fx_directory_delete</span></span>
- <span data-ttu-id="887e6-609">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-609">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="887e6-610">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-610">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="887e6-611">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="887e6-611">fx_directory_information_get</span></span>
- <span data-ttu-id="887e6-612">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="887e6-612">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="887e6-613">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="887e6-613">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="887e6-614">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="887e6-614">fx_directory_local_path_set</span></span>
- <span data-ttu-id="887e6-615">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-615">fx_directory_long_name_get</span></span>
- <span data-ttu-id="887e6-616">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="887e6-616">fx_directory_name_test</span></span>
- <span data-ttu-id="887e6-617">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-617">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="887e6-618">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-618">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="887e6-619">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-619">fx_directory_rename</span></span>
- <span data-ttu-id="887e6-620">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-620">fx_directory_short_name_get</span></span>
- <span data-ttu-id="887e6-621">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-621">fx_unicode_directory_create</span></span>
- <span data-ttu-id="887e6-622">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-622">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_restore"></a><span data-ttu-id="887e6-623">fx_directory_local_path_restore:</span><span class="sxs-lookup"><span data-stu-id="887e6-623">fx_directory_local_path_restore:</span></span>

<span data-ttu-id="887e6-624">Восстанавливает предыдущий локальный путь</span><span class="sxs-lookup"><span data-stu-id="887e6-624">Restores previous local path</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-625">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-625">Prototype</span></span>

```c
UINT fx_directory_local_path_restore(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr);
```

### <a name="description"></a><span data-ttu-id="887e6-626">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-626">Description</span></span>

<span data-ttu-id="887e6-627">Эта служба восстанавливает заданный ранее локальный путь.</span><span class="sxs-lookup"><span data-stu-id="887e6-627">This service restores a previously set local path.</span></span> <span data-ttu-id="887e6-628">Также восстанавливается расположение поиска в каталоге по этому локальному пути, что делает эту подпрограмму полезной в рекурсивных обходах каталогов приложением.</span><span class="sxs-lookup"><span data-stu-id="887e6-628">The directory search position made on this local path is also restored, which makes this routine useful in recursive directory traversals by the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="887e6-629">*Каждый локальный путь содержит строку локального пути размером **FX_MAXIMUM_PATH** (значение по умолчанию — 256 символов). Эта строка внутреннего пути не используется FileX и предоставляется только для использования приложением. Если **FX_LOCAL_PATH** будет объявлена как локальная переменная, пользователям следует помнить, что стек увеличивается на размер этой структуры. Пользователи могут уменьшить размер **FX_MAXIMUM_PATH** и перестроить источник библиотеки FileX.*</span><span class="sxs-lookup"><span data-stu-id="887e6-629">*Each local path contains a local path string of **FX_MAXIMUM_PATH** in size, which by default is 256 characters. This internal path string is not used by FileX and is provided only for the application's use. If **FX_LOCAL_PATH** is going to be declared as a local variable, users should beware of the stack growing by the size of this structure. Users are welcome to reduce the size of **FX_MAXIMUM_PATH** and rebuild the FileX library source.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-630">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-630">Input Parameters</span></span>

- <span data-ttu-id="887e6-631">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-631">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="887e6-632">**local_path_ptr**: указатель на заданный ранее локальный путь</span><span class="sxs-lookup"><span data-stu-id="887e6-632">**local_path_ptr**: Pointer to the previously set local path.</span></span> <span data-ttu-id="887e6-633">Очень важно убедиться, что этот указатель действительно указывает на ранее использовавшийся, но незатронутый локальный путь.</span><span class="sxs-lookup"><span data-stu-id="887e6-633">It's very important to ensure that this pointer does indeed point to a previously used and still intact local path.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-634">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-634">Return Values</span></span>

- <span data-ttu-id="887e6-635">**FX_SUCCESS** (0x00) — локальный путь успешно восстановлен.</span><span class="sxs-lookup"><span data-stu-id="887e6-635">**FX_SUCCESS** (0x00) Successful local path restore.</span></span>
- <span data-ttu-id="887e6-636">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель в настоящее время не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-636">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not currently open.</span></span>
- <span data-ttu-id="887e6-637">**FX_NOT_IMPLEMENTED** (0x22) — определен FX_NO_LCOAL_PATH.</span><span class="sxs-lookup"><span data-stu-id="887e6-637">**FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH is defined.</span></span>
- <span data-ttu-id="887e6-638">**FX_PTR_ERROR** (0x18) — недопустимый указатель на носитель или локальный путь.</span><span class="sxs-lookup"><span data-stu-id="887e6-638">**FX_PTR_ERROR** (0x18) Invalid media or local path pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-639">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-639">Allowed From</span></span>

<span data-ttu-id="887e6-640">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-640">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-641">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-641">Example</span></span>

```c
FX_MEDIA                  my_media;
FX_LOCAL_PATH             my_previous_local_path;
UINT                      status;
/* Restore the previous local path. */
status = fx_directory_local_path_restore(&my_media, &my_previous_local_path);
/* If status equals FX_SUCCESS, the previous local path has been restored. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-642">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-642">See Also</span></span>

- <span data-ttu-id="887e6-643">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-643">fx_directory_attributes_read</span></span>
- <span data-ttu-id="887e6-644">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-644">fx_directory_attributes_set</span></span>
- <span data-ttu-id="887e6-645">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-645">fx_directory_create</span></span>
- <span data-ttu-id="887e6-646">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="887e6-646">fx_directory_default_get</span></span>
- <span data-ttu-id="887e6-647">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="887e6-647">fx_directory_default_set</span></span>
- <span data-ttu-id="887e6-648">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-648">fx_directory_delete</span></span>
- <span data-ttu-id="887e6-649">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-649">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="887e6-650">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-650">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="887e6-651">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="887e6-651">fx_directory_information_get</span></span>
- <span data-ttu-id="887e6-652">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="887e6-652">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="887e6-653">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="887e6-653">fx_directory_local_path_get</span></span>
- <span data-ttu-id="887e6-654">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="887e6-654">fx_directory_local_path_set</span></span>
- <span data-ttu-id="887e6-655">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-655">fx_directory_long_name_get</span></span>
- <span data-ttu-id="887e6-656">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="887e6-656">fx_directory_name_test</span></span>
- <span data-ttu-id="887e6-657">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-657">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="887e6-658">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-658">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="887e6-659">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-659">fx_directory_rename</span></span>
- <span data-ttu-id="887e6-660">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-660">fx_directory_short_name_get</span></span>
- <span data-ttu-id="887e6-661">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-661">fx_unicode_directory_create</span></span>
- <span data-ttu-id="887e6-662">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-662">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_set"></a><span data-ttu-id="887e6-663">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="887e6-663">fx_directory_local_path_set</span></span>

<span data-ttu-id="887e6-664">Задает локальный путь для конкретного потока</span><span class="sxs-lookup"><span data-stu-id="887e6-664">Sets up a thread-specific local path</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-665">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-665">Prototype</span></span>

```c
UINT fx_directory_local_path_set(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a><span data-ttu-id="887e6-666">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-666">Description</span></span>

<span data-ttu-id="887e6-667">Эта служба задает путь для конкретного потока, как указано в \***new_path_string** _.</span><span class="sxs-lookup"><span data-stu-id="887e6-667">This service sets up a thread-specific path as specified by the \***new_path_string** _.</span></span> <span data-ttu-id="887e6-668">После успешного выполнения этой подпрограммы сведения о локальном пути, хранящиеся в файле _ \*_local_path_ptr_\*\*, будут иметь приоритет над глобальным путем к носителю для всех операций с файлами и каталогами, выполняемыми этим потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-668">After successful completion of this routine, the local path information stored in _ *_local_path_ptr_*\* will take precedence over the global media path for all file and directory operations made by this thread.</span></span> <span data-ttu-id="887e6-669">Это не влияет на любой другой поток в системе.</span><span class="sxs-lookup"><span data-stu-id="887e6-669">This will have no impact on any other thread in the system</span></span> 
> [!IMPORTANT]
> <span data-ttu-id="887e6-670">*Размер по умолчанию для строки локального пути составляет 256 символов; можно указать другой размер, изменив **FX_MAXIMUM_PATH** в файле **fx_api. h** и перестроив всю библиотеку FileX. Путь к строке символов сохраняется для приложения и не используется FileX внутри.*</span><span class="sxs-lookup"><span data-stu-id="887e6-670">*The default size of the local path string is 256 characters; it can be changed by modifying **FX_MAXIMUM_PATH** in **fx_api.h** and rebuilding the entire FileX library. The character string path is maintained for the application and is not used internally by FileX.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="887e6-671">*Для имен, предоставленных приложением, FileX поддерживает как обратную косую черту (\\), так и символ косой черты (/) для разделения каталогов, подкаталогов и имен файлов. Однако в путях, возвращаемых приложению, FileX использует только символ обратной косой черты.*</span><span class="sxs-lookup"><span data-stu-id="887e6-671">*For names supplied by the application, FileX supports both backslash (\\) and forward slash (/) characters to separate directories, subdirectories, and file names. However, FileX only uses the backslash character in paths returned to the application.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-672">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-672">Input Parameters</span></span>

- <span data-ttu-id="887e6-673">**media_ptr**: указатель на открытый ранее носитель</span><span class="sxs-lookup"><span data-stu-id="887e6-673">**media_ptr**: Pointer to the previously opened media.</span></span>
- <span data-ttu-id="887e6-674">**local_path_ptr**: назначение для хранения сведений о локальном пути для конкретного потока</span><span class="sxs-lookup"><span data-stu-id="887e6-674">**local_path_ptr**: Destination for holding the thread-specific local path information.</span></span> <span data-ttu-id="887e6-675">В будущем для функции восстановления локального пути можно предоставить адрес этой структуры.</span><span class="sxs-lookup"><span data-stu-id="887e6-675">The address of this structure may be supplied to the local path restore function in the future.</span></span>
- <span data-ttu-id="887e6-676">**new_path_name**: указывает локальный путь для настройки</span><span class="sxs-lookup"><span data-stu-id="887e6-676">**new_path_name**: Specifies the local path to setup.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-677">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-677">Return Values</span></span>

- <span data-ttu-id="887e6-678">**FX_SUCCESS** (0x00) — каталог по умолчанию успешно задан.</span><span class="sxs-lookup"><span data-stu-id="887e6-678">**FX_SUCCESS** (0x00) Successful default directory set.</span></span>
- <span data-ttu-id="887e6-679">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-679">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="887e6-680">**FX_NOT_IMPLEMENTED** (0x22) — \*\*FX_NO_LCOAL_PATH</span><span class="sxs-lookup"><span data-stu-id="887e6-680">**FX_NOT_IMPLEMENTED** (0x22) \*\*FX_NO_LCOAL_PATH</span></span>
- <span data-ttu-id="887e6-681">**FX_INVALID_PATH** (0x0D) — не удалось найти новый каталог.</span><span class="sxs-lookup"><span data-stu-id="887e6-681">**FX_INVALID_PATH** (0x0D) New directory could not be found.</span></span>
- <span data-ttu-id="887e6-682">**FX_NOT_IMPLEMENTED** (0x22) — определен \*\*FX_NO_LOCAL_PATH.</span><span class="sxs-lookup"><span data-stu-id="887e6-682">**FX_NOT_IMPLEMENTED** (0x22)- \*\*FX_NO_LOCAL_PATH is defined.</span></span>
- <span data-ttu-id="887e6-683">**FX_PTR_ERROR** (0x18) — недопустимый указатель на носитель или локальный путь.</span><span class="sxs-lookup"><span data-stu-id="887e6-683">**FX_PTR_ERROR** (0x18) Invalid media or local path pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-684">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-684">Allowed From</span></span>

<span data-ttu-id="887e6-685">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-685">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-686">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-686">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;
FX_LOCAL_PATH     my_previous_local_path;
/* Set the local path to \abc\def\ghi. */
status = fx_directory_local_path_set (&my_media,&local_path,"\\abc\\def\\ghi");

/* If status equals FX_SUCCESS, the default directory for this thread
is \abc\def\ghi. All subsequent file operations that do not explicitly
specify a path will default to this directory. Note that the character
"\" serves as an escape character in a string. To represent the
character "\", use the construct "\\".*/
```

### <a name="see-also"></a><span data-ttu-id="887e6-687">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-687">See Also</span></span>

- <span data-ttu-id="887e6-688">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-688">fx_directory_attributes_read</span></span>
- <span data-ttu-id="887e6-689">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-689">fx_directory_attributes_set</span></span>
- <span data-ttu-id="887e6-690">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-690">fx_directory_create</span></span>
- <span data-ttu-id="887e6-691">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="887e6-691">fx_directory_default_get</span></span>
- <span data-ttu-id="887e6-692">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="887e6-692">fx_directory_default_set</span></span>
- <span data-ttu-id="887e6-693">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-693">fx_directory_delete</span></span>
- <span data-ttu-id="887e6-694">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-694">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="887e6-695">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-695">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="887e6-696">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="887e6-696">fx_directory_information_get</span></span>
- <span data-ttu-id="887e6-697">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="887e6-697">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="887e6-698">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="887e6-698">fx_directory_local_path_get</span></span>
- <span data-ttu-id="887e6-699">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="887e6-699">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="887e6-700">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-700">fx_directory_long_name_get</span></span>
- <span data-ttu-id="887e6-701">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="887e6-701">fx_directory_name_test</span></span>
- <span data-ttu-id="887e6-702">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-702">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="887e6-703">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-703">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="887e6-704">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-704">fx_directory_rename</span></span>
- <span data-ttu-id="887e6-705">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-705">fx_directory_short_name_get</span></span>
- <span data-ttu-id="887e6-706">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-706">fx_unicode_directory_create</span></span>
- <span data-ttu-id="887e6-707">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-707">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_long_name_get"></a><span data-ttu-id="887e6-708">fx_directory_long_name_get:</span><span class="sxs-lookup"><span data-stu-id="887e6-708">fx_directory_long_name_get:</span></span>

<span data-ttu-id="887e6-709">Получает длинное имя из краткого имени</span><span class="sxs-lookup"><span data-stu-id="887e6-709">Gets long name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-710">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-710">Prototype</span></span>

```c
UINT fx_directory_long_name_get(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name);
```

### <a name="description"></a><span data-ttu-id="887e6-711">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-711">Description</span></span>

<span data-ttu-id="887e6-712">Эта служба получает длинное имя (если имеется), связанное с переданным кратким именем (формат 8.3).</span><span class="sxs-lookup"><span data-stu-id="887e6-712">This service retrieves the long name (if any) associated with the supplied short (8.3 format) name.</span></span> <span data-ttu-id="887e6-713">Краткое имя может быть либо именем файла, либо именем каталога.</span><span class="sxs-lookup"><span data-stu-id="887e6-713">The short name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-714">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-714">Input Parameters</span></span>

- <span data-ttu-id="887e6-715">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-715">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="887e6-716">**short_name**: указатель на исходное краткое имя (формат 8.3)</span><span class="sxs-lookup"><span data-stu-id="887e6-716">**short_name**: Pointer to source short name (8.3 format).</span></span>
- <span data-ttu-id="887e6-717">**long_name**: указатель на назначение для длинного имени</span><span class="sxs-lookup"><span data-stu-id="887e6-717">**long_name**: Pointer to destination for the long name.</span></span> <span data-ttu-id="887e6-718">Если нет длинного имени, возвращается краткое имя.</span><span class="sxs-lookup"><span data-stu-id="887e6-718">If there is no long name, the short name is returned.</span></span> <span data-ttu-id="887e6-719">Обратите внимание, что назначение для длинного имени должно быть достаточно большим, чтобы вместить FX_MAX_LONG_NAME_LEN символов.</span><span class="sxs-lookup"><span data-stu-id="887e6-719">Note that the destination for the long name must be large enough to hold FX_MAX_LONG_NAME_LEN characters.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-720">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-720">Return Values</span></span>

- <span data-ttu-id="887e6-721">**FX_SUCCESS** (0x00) — длинное имя успешно получено.</span><span class="sxs-lookup"><span data-stu-id="887e6-721">**FX_SUCCESS** (0x00) Successful long name get</span></span>
- <span data-ttu-id="887e6-722">**FX_NOT_FOUND** (0x04) — краткое имя не найдено.</span><span class="sxs-lookup"><span data-stu-id="887e6-722">**FX_NOT_FOUND** (0x04) Short name was not found</span></span>
- <span data-ttu-id="887e6-723">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-723">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="887e6-724">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="887e6-724">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="887e6-725">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-725">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="887e6-726">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-726">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="887e6-727">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-727">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="887e6-728">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="887e6-728">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="887e6-729">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.</span><span class="sxs-lookup"><span data-stu-id="887e6-729">**FX_PTR_ERROR** (0x18) Invalid media or name pointer</span></span>
- <span data-ttu-id="887e6-730">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-730">**FX_CALLER_ERROR** (0x20) Caller is not a thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-731">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-731">Allowed From</span></span>

<span data-ttu-id="887e6-732">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-732">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-733">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-733">Example</span></span>

```c
FX_MEDIA            my_media;
UCHAR               my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */
status = fx_directory_long_name_get(&my_media, "TEXT~01.TXT", my_long_name);
/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-734">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-734">See Also</span></span>

- <span data-ttu-id="887e6-735">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-735">fx_directory_attributes_read</span></span>
- <span data-ttu-id="887e6-736">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-736">fx_directory_attributes_set</span></span>
- <span data-ttu-id="887e6-737">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-737">fx_directory_create</span></span>
- <span data-ttu-id="887e6-738">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="887e6-738">fx_directory_default_get</span></span>
- <span data-ttu-id="887e6-739">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="887e6-739">fx_directory_default_set</span></span>
- <span data-ttu-id="887e6-740">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-740">fx_directory_delete</span></span>
- <span data-ttu-id="887e6-741">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-741">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="887e6-742">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-742">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="887e6-743">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="887e6-743">fx_directory_information_get</span></span>
- <span data-ttu-id="887e6-744">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="887e6-744">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="887e6-745">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="887e6-745">fx_directory_local_path_get</span></span>
- <span data-ttu-id="887e6-746">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="887e6-746">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="887e6-747">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="887e6-747">fx_directory_local_path_set</span></span>
- <span data-ttu-id="887e6-748">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="887e6-748">fx_directory_name_test</span></span>
- <span data-ttu-id="887e6-749">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-749">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="887e6-750">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-750">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="887e6-751">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-751">fx_directory_rename</span></span>
- <span data-ttu-id="887e6-752">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-752">fx_directory_short_name_get</span></span>
- <span data-ttu-id="887e6-753">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-753">fx_unicode_directory_create</span></span>
- <span data-ttu-id="887e6-754">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-754">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_long_name_get_extended"></a><span data-ttu-id="887e6-755">fx_directory_long_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="887e6-755">fx_directory_long_name_get_extended</span></span>

<span data-ttu-id="887e6-756">Получает длинное имя из краткого имени</span><span class="sxs-lookup"><span data-stu-id="887e6-756">Gets long name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-757">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-757">Prototype</span></span>

```c
UINT fx_directory_long_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name,
    UINT long_file_name_buffer_length);
```

### <a name="description"></a><span data-ttu-id="887e6-758">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-758">Description</span></span>

<span data-ttu-id="887e6-759">Эта служба получает длинное имя (если имеется), связанное с переданным кратким именем (формат 8.3).</span><span class="sxs-lookup"><span data-stu-id="887e6-759">This service retrieves the long name (if any) associated with the supplied short (8.3 format) name.</span></span> <span data-ttu-id="887e6-760">Краткое имя может быть либо именем файла, либо именем каталога.</span><span class="sxs-lookup"><span data-stu-id="887e6-760">The short name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-761">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-761">Input Parameters</span></span>

- <span data-ttu-id="887e6-762">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-762">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="887e6-763">**short_name**: указатель на исходное краткое имя (формат 8.3)</span><span class="sxs-lookup"><span data-stu-id="887e6-763">**short_name**: Pointer to source short name (8.3 format).</span></span>
- <span data-ttu-id="887e6-764">**long_name**: указатель на назначение для длинного имени</span><span class="sxs-lookup"><span data-stu-id="887e6-764">**long_name**: Pointer to destination for the long name.</span></span> <span data-ttu-id="887e6-765">Если нет длинного имени, возвращается краткое имя.</span><span class="sxs-lookup"><span data-stu-id="887e6-765">If there is no long name, the short name is returned.</span></span> <span data-ttu-id="887e6-766">Обратите внимание, что назначение для длинного имени должно быть достаточно большим, чтобы вместить **FX_MAX_LONG_NAME_LEN** символов.</span><span class="sxs-lookup"><span data-stu-id="887e6-766">Note: Destination for the long name must be large enough to hold **FX_MAX_LONG_NAME_LEN** characters.</span></span>
- <span data-ttu-id="887e6-767">**long_file_name_buffer_length**: длина буфера длинного имени</span><span class="sxs-lookup"><span data-stu-id="887e6-767">**long_file_name_buffer_length**: Length of the long name buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-768">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-768">Return Values</span></span>

- <span data-ttu-id="887e6-769">**FX_SUCCESS** (0x00) — длинное имя успешно получено.</span><span class="sxs-lookup"><span data-stu-id="887e6-769">**FX_SUCCESS** (0x00) Successful long name get.</span></span>
- <span data-ttu-id="887e6-770">**FX_NOT_FOUND** (0x04) — краткое имя не найдено.</span><span class="sxs-lookup"><span data-stu-id="887e6-770">**FX_NOT_FOUND** (0x04) Short name was not found.</span></span>
- <span data-ttu-id="887e6-771">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-771">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-772">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="887e6-772">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="887e6-773">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-773">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="887e6-774">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-774">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="887e6-775">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-775">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="887e6-776">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="887e6-776">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="887e6-777">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.</span><span class="sxs-lookup"><span data-stu-id="887e6-777">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="887e6-778">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-778">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-779">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-779">Allowed From</span></span>

<span data-ttu-id="887e6-780">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-780">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-781">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-781">Example</span></span>

```c
FX_MEDIA        my_media;
UCHAR            my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */

status = fx_directory_long_name_get_extended(&my_media,
    "TEXT~01.TXT", my_long_name), sizeof(my_long_name));

/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-782">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-782">See Also</span></span>

- <span data-ttu-id="887e6-783">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-783">fx_directory_attributes_read</span></span>
- <span data-ttu-id="887e6-784">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-784">fx_directory_attributes_set</span></span>
- <span data-ttu-id="887e6-785">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-785">fx_directory_create</span></span>
- <span data-ttu-id="887e6-786">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="887e6-786">fx_directory_default_get</span></span>
- <span data-ttu-id="887e6-787">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="887e6-787">fx_directory_default_set</span></span>
- <span data-ttu-id="887e6-788">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-788">fx_directory_delete</span></span>
- <span data-ttu-id="887e6-789">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-789">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="887e6-790">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-790">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="887e6-791">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="887e6-791">fx_directory_information_get</span></span>
- <span data-ttu-id="887e6-792">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="887e6-792">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="887e6-793">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="887e6-793">fx_directory_local_path_get</span></span>
- <span data-ttu-id="887e6-794">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="887e6-794">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="887e6-795">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="887e6-795">fx_directory_local_path_set</span></span>
- <span data-ttu-id="887e6-796">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-796">fx_directory_long_name_get</span></span>
- <span data-ttu-id="887e6-797">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-797">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="887e6-798">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-798">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="887e6-799">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-799">fx_directory_rename</span></span>
- <span data-ttu-id="887e6-800">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-800">fx_directory_short_name_get</span></span>
- <span data-ttu-id="887e6-801">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-801">fx_unicode_directory_create</span></span>
- <span data-ttu-id="887e6-802">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-802">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_name_test"></a><span data-ttu-id="887e6-803">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="887e6-803">fx_directory_name_test</span></span>

<span data-ttu-id="887e6-804">Проверяет каталог</span><span class="sxs-lookup"><span data-stu-id="887e6-804">Tests for directory</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-805">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-805">Prototype</span></span>

```c
UINT fx_directory_name_test(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a><span data-ttu-id="887e6-806">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-806">Description</span></span>

<span data-ttu-id="887e6-807">Эта служба проверяет, является ли переданное имя каталогом.</span><span class="sxs-lookup"><span data-stu-id="887e6-807">This service tests whether or not the supplied name is a directory.</span></span> <span data-ttu-id="887e6-808">Если это так, возвращается FX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="887e6-808">If so, a FX_SUCCESS is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-809">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-809">Input Parameters</span></span>

- <span data-ttu-id="887e6-810">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-810">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="887e6-811">**directory_name**: указатель на имя записи каталога</span><span class="sxs-lookup"><span data-stu-id="887e6-811">**directory_name**: Pointer to name of the directory entry.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-812">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-812">Return Values</span></span>

- <span data-ttu-id="887e6-813">**FX_SUCCESS** (0x00) — указанное имя является каталогом.</span><span class="sxs-lookup"><span data-stu-id="887e6-813">**FX_SUCCESS** (0x00) Supplied name is a directory.</span></span>
- <span data-ttu-id="887e6-814">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-814">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="887e6-815">**FX_NOT_FOUND** (0x04) — не удалось найти запись каталога.</span><span class="sxs-lookup"><span data-stu-id="887e6-815">**FX_NOT_FOUND** (0x04) Directory entry could not be found.</span></span>
- <span data-ttu-id="887e6-816">**FX_NOT_DIRECTORY** (0x0E) — запись не является каталогом.</span><span class="sxs-lookup"><span data-stu-id="887e6-816">**FX_NOT_DIRECTORY** (0x0E)  Entry is not a directory</span></span>
- <span data-ttu-id="887e6-817">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-817">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-818">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="887e6-818">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="887e6-819">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-819">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="887e6-820">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-820">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="887e6-821">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-821">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="887e6-822">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="887e6-822">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="887e6-823">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.</span><span class="sxs-lookup"><span data-stu-id="887e6-823">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="887e6-824">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-824">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-825">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-825">Allowed From</span></span>

<span data-ttu-id="887e6-826">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-826">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-827">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-827">Example</span></span>

```c
FX_MEDIA        my_media;
UNIT             status;
/* Check to see if the name "abc" is directory */

status = fx_directory_name_test(&my_media, "abc");

/* If status equals FX_SUCCESS "abc" is a directory. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-828">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-828">See Also</span></span>

- <span data-ttu-id="887e6-829">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-829">fx_directory_attributes_read</span></span>
- <span data-ttu-id="887e6-830">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-830">fx_directory_attributes_set</span></span>
- <span data-ttu-id="887e6-831">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-831">fx_directory_create</span></span>
- <span data-ttu-id="887e6-832">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="887e6-832">fx_directory_default_get</span></span>
- <span data-ttu-id="887e6-833">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="887e6-833">fx_directory_default_set</span></span>
- <span data-ttu-id="887e6-834">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-834">fx_directory_delete</span></span>
- <span data-ttu-id="887e6-835">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-835">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="887e6-836">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-836">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="887e6-837">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="887e6-837">fx_directory_information_get</span></span>
- <span data-ttu-id="887e6-838">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="887e6-838">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="887e6-839">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="887e6-839">fx_directory_local_path_get</span></span>
- <span data-ttu-id="887e6-840">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="887e6-840">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="887e6-841">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="887e6-841">fx_directory_local_path_set</span></span>
- <span data-ttu-id="887e6-842">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-842">fx_directory_long_name_get</span></span>
- <span data-ttu-id="887e6-843">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-843">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="887e6-844">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-844">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="887e6-845">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-845">fx_directory_rename</span></span>
- <span data-ttu-id="887e6-846">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-846">fx_directory_short_name_get</span></span>
- <span data-ttu-id="887e6-847">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-847">fx_unicode_directory_create</span></span>

## <a name="fx_directory_next_entry_find"></a><span data-ttu-id="887e6-848">fx_directory_next_entry_find:</span><span class="sxs-lookup"><span data-stu-id="887e6-848">fx_directory_next_entry_find:</span></span>

<span data-ttu-id="887e6-849">Выбирает новую запись каталога</span><span class="sxs-lookup"><span data-stu-id="887e6-849">Picks up next directory entry</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-850">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-850">Prototype</span></span>

```c
UINT fx_directory_next_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a><span data-ttu-id="887e6-851">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-851">Description</span></span>

<span data-ttu-id="887e6-852">Эта служба возвращает имя следующей записи в текущем каталоге по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="887e6-852">This service returns the next entry name in the current default directory.</span></span>

> [!WARNING]
> <span data-ttu-id="887e6-853">*При использовании нелокального пути также важно предотвратить изменение этого каталога (с помощью семафора ThreadX или уровня приоритета потока) другими потоками приложения во время обхода каталога. В противном случае могут быть получены недопустимые результаты.*</span><span class="sxs-lookup"><span data-stu-id="887e6-853">*If using a non-local path, it is also important to prevent (with a ThreadX semaphore or thread priority level) other application threads from changing this directory while a directory traversal is taking place. Otherwise, invalid results may be obtained.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-854">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-854">Input Parameters</span></span>

- <span data-ttu-id="887e6-855">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-855">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="887e6-856">**return_entry_name**: указатель на назначение для имени следующей записи в каталоге по умолчанию</span><span class="sxs-lookup"><span data-stu-id="887e6-856">**return_entry_name**: Pointer to destination for the next entry name in the default directory.</span></span> <span data-ttu-id="887e6-857">Буфер, на который указывает этот указатель, должен быть достаточно большим, чтобы вместить имя FileX максимального размера, как определено **_FX_MAX_LONG_NAME_LEN_**.</span><span class="sxs-lookup"><span data-stu-id="887e6-857">The buffer this pointer points to must be large enough to hold the maximum size of FileX name, defined by **_FX_MAX_LONG_NAME_LEN_**.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-858">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-858">Return Values</span></span>

- <span data-ttu-id="887e6-859">**FX_SUCCESS** (0x00) — следующая запись успешно найдена.</span><span class="sxs-lookup"><span data-stu-id="887e6-859">**FX_SUCCESS** (0x00) Successful next entry find</span></span>
- <span data-ttu-id="887e6-860">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-860">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="887e6-861">**FX_NO_MORE_ENTRIES** (0x0F) — в этом каталоге больше нет записей.</span><span class="sxs-lookup"><span data-stu-id="887e6-861">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory.</span></span>
- <span data-ttu-id="887e6-862">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-862">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-863">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-863">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="887e6-864">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-864">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="887e6-865">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-865">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="887e6-866">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-866">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="887e6-867">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-867">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="887e6-868">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-868">**FX_CALLER_ERROR** (0x20)     Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-869">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-869">Allowed From</span></span>

<span data-ttu-id="887e6-870">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-870">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-871">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-871">Example</span></span>

```c
FX_MEDIA        my_media;
CHAR            next_name[FX_MAX_LONG_NAME_LEN];
UINT            status;

/* Retrieve the next entry in the default directory. */

status = fx_directory_next_entry_find(&my_media, next_name);

/* If status equals TX_SUCCESS, the name of the next directory entry is in "next_name". */
```

### <a name="see-also"></a><span data-ttu-id="887e6-872">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-872">See Also</span></span>

- <span data-ttu-id="887e6-873">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-873">fx_directory_attributes_read</span></span>
- <span data-ttu-id="887e6-874">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-874">fx_directory_attributes_set</span></span>
- <span data-ttu-id="887e6-875">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-875">fx_directory_create</span></span>
- <span data-ttu-id="887e6-876">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="887e6-876">fx_directory_default_get</span></span>
- <span data-ttu-id="887e6-877">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="887e6-877">fx_directory_default_set</span></span>
- <span data-ttu-id="887e6-878">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-878">fx_directory_delete</span></span>
- <span data-ttu-id="887e6-879">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-879">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="887e6-880">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-880">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="887e6-881">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="887e6-881">fx_directory_information_get</span></span>
- <span data-ttu-id="887e6-882">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="887e6-882">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="887e6-883">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="887e6-883">fx_directory_local_path_get</span></span>
- <span data-ttu-id="887e6-884">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="887e6-884">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="887e6-885">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="887e6-885">fx_directory_local_path_set</span></span>
- <span data-ttu-id="887e6-886">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-886">fx_directory_long_name_get</span></span>
- <span data-ttu-id="887e6-887">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="887e6-887">fx_directory_name_test</span></span>
- <span data-ttu-id="887e6-888">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-888">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="887e6-889">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-889">fx_directory_rename</span></span>
- <span data-ttu-id="887e6-890">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-890">fx_directory_short_name_get</span></span>
- <span data-ttu-id="887e6-891">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-891">fx_unicode_directory_create</span></span>
- <span data-ttu-id="887e6-892">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-892">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_next_full_entry_find"></a><span data-ttu-id="887e6-893">fx_directory_next_full_entry_find:</span><span class="sxs-lookup"><span data-stu-id="887e6-893">fx_directory_next_full_entry_find:</span></span>

<span data-ttu-id="887e6-894">Получает следующую запись каталога с полной информацией</span><span class="sxs-lookup"><span data-stu-id="887e6-894">Gets next directory entry with full information</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-895">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-895">Prototype</span></span>

```c
UINT fx_directory_next_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes, 
    ULONG *size,
    UINT *year, 
    UINT *month, 
    UINT *day,
    UINT *hour, 
    UINT *minute, 
    UINT *second);
```

### <a name="description"></a><span data-ttu-id="887e6-896">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-896">Description</span></span>

<span data-ttu-id="887e6-897">Эта служба получает имя следующей записи в каталоге по умолчанию и копирует его в указанное место назначения.</span><span class="sxs-lookup"><span data-stu-id="887e6-897">This service retrieves the next entry name in the default directory and copies it to the specified destination.</span></span> <span data-ttu-id="887e6-898">Она также возвращает полные сведения о записи, указанные дополнительными входными параметрами.</span><span class="sxs-lookup"><span data-stu-id="887e6-898">It also returns full information about the entry as specified by the additional input parameters.</span></span>

> [!WARNING]
> <span data-ttu-id="887e6-899">\*Указанное назначение должно быть достаточно большим, чтобы вместить имя FileX максимального размера, как определено ***FX_MAX_LONG_NAME_LEN***.</span><span class="sxs-lookup"><span data-stu-id="887e6-899">\*The specified destination must be large enough to hold the maximum sized FileX name, as defined by \*\*\*FX_MAX_LONG_NAME_LEN\*\*\*\*</span></span>

> [!WARNING]
> <span data-ttu-id="887e6-900">*При использовании нелокального пути важно предотвратить изменение этого каталога (с помощью семафора ThreadX, мьютекса или изменения уровня приоритета) другими потоками приложения во время обхода каталога. В противном случае могут быть получены недопустимые результаты.*</span><span class="sxs-lookup"><span data-stu-id="887e6-900">*If using a non-local path, it is important to prevent (with a ThreadX semaphore, mutex, or priority level change) other application threads from changing this directory while a directory traversal is taking place. Otherwise, invalid results may be obtained.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-901">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-901">Input Parameters</span></span>

- <span data-ttu-id="887e6-902">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-902">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="887e6-903">**directory_name**: указатель на назначение для имени записи каталога</span><span class="sxs-lookup"><span data-stu-id="887e6-903">**directory_name**: Pointer to the destination for the name of a directory entry.</span></span> <span data-ttu-id="887e6-904">Размер должен быть не меньше **FX_MAX_LONG_NAME_LEN**.</span><span class="sxs-lookup"><span data-stu-id="887e6-904">Must be at least as big as **FX_MAX_LONG_NAME_LEN**.</span></span>
- <span data-ttu-id="887e6-905">**attributes**: если значение не равно NULL, указатель на назначение для атрибутов записи, которые необходимо разместить. Атрибуты возвращаются в формате битовой карты со следующими возможными параметрами.</span><span class="sxs-lookup"><span data-stu-id="887e6-905">**attributes**: If non-null, pointer to the destination for the entry's attributes to be placed.The attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="887e6-906">**FX_READ_ONLY** (0x01)</span><span class="sxs-lookup"><span data-stu-id="887e6-906">**FX_READ_ONLY** (0x01)</span></span>
  - <span data-ttu-id="887e6-907">**FX_HIDDEN** (0x02)</span><span class="sxs-lookup"><span data-stu-id="887e6-907">**FX_HIDDEN** (0x02)</span></span>
  - <span data-ttu-id="887e6-908">**FX_SYSTEM** (0x04)</span><span class="sxs-lookup"><span data-stu-id="887e6-908">**FX_SYSTEM** (0x04)</span></span>
  - <span data-ttu-id="887e6-909">**FX_VOLUME** (0x08)</span><span class="sxs-lookup"><span data-stu-id="887e6-909">**FX_VOLUME** (0x08)</span></span>
  - <span data-ttu-id="887e6-910">**FX_DIRECTORY** (0x10)</span><span class="sxs-lookup"><span data-stu-id="887e6-910">**FX_DIRECTORY** (0x10)</span></span>
  - <span data-ttu-id="887e6-911">**FX_ARCHIVE** (0x20)</span><span class="sxs-lookup"><span data-stu-id="887e6-911">**FX_ARCHIVE** (0x20)</span></span>
- <span data-ttu-id="887e6-912">**size**: указатель на назначение для размера записи в байтах, если не NULL</span><span class="sxs-lookup"><span data-stu-id="887e6-912">**size**: If non-null, pointer to the destination for the entry's size in bytes.</span></span>
- <span data-ttu-id="887e6-913">**month**: указатель на назначение для месяца записи, если не NULL</span><span class="sxs-lookup"><span data-stu-id="887e6-913">**month**: If non-null, pointer to the destination for the entry's month of modification.</span></span>
- <span data-ttu-id="887e6-914">**year**: указатель на назначение для года записи, если не NULL</span><span class="sxs-lookup"><span data-stu-id="887e6-914">**year**: If non-null, pointer to the destination for the entry's year of modification.</span></span>
- <span data-ttu-id="887e6-915">**day**: указатель на назначение для дня записи, если не NULL</span><span class="sxs-lookup"><span data-stu-id="887e6-915">**day**: If non-null, pointer to the destination for the entry's day of modification.</span></span>
- <span data-ttu-id="887e6-916">**hour**: указатель на назначение для часа записи, если не NULL</span><span class="sxs-lookup"><span data-stu-id="887e6-916">**hour**: If non-null, pointer to the destination for the entry's hour of modification.</span></span>
- <span data-ttu-id="887e6-917">**minute**: указатель на назначение для минуты записи, если не NULL</span><span class="sxs-lookup"><span data-stu-id="887e6-917">**minute**: If non-null, pointer to the destination for the entry's minute of modification.</span></span>
- <span data-ttu-id="887e6-918">**second**: указатель на назначение для секунды записи, если не NULL</span><span class="sxs-lookup"><span data-stu-id="887e6-918">**second**: If non-null, pointer to the destination for the entry's second of modification.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-919">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-919">Return Values</span></span>

- <span data-ttu-id="887e6-920">**FX_SUCCESS** (0x00) — следующая запись каталога успешно найдена.</span><span class="sxs-lookup"><span data-stu-id="887e6-920">**FX_SUCCESS** (0x00) Successful directory next entry find.</span></span>
- <span data-ttu-id="887e6-921">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-921">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="887e6-922">**FX_NO_MORE_ENTRIES** (0x0F) — в этом каталоге больше нет записей.</span><span class="sxs-lookup"><span data-stu-id="887e6-922">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory.</span></span>
- <span data-ttu-id="887e6-923">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-923">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-924">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-924">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="887e6-925">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-925">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="887e6-926">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-926">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="887e6-927">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="887e6-927">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="887e6-928">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="887e6-928">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="887e6-929">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя, или все входные параметры имеют значение NULL.</span><span class="sxs-lookup"><span data-stu-id="887e6-929">**FX_PTR_ERROR** (0x18) Invalid media pointer or all input parameters are NULL.</span></span>
- <span data-ttu-id="887e6-930">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-930">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-931">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-931">Allowed From</span></span>

<span data-ttu-id="887e6-932">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-932">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-933">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-933">Example</span></span>

```c
FX_MEDIA    my_media;
UINT        status;
CHAR        entry_name[FX_MAX_LONG_NAME_LEN];
UINT        attributes;
ULONG       size;
UINT        year;
UINT        month;
UINT        day;
UINT        hour;
UINT        minute;
UINT        second;

/* Get the next directory entry in the default directory with full information. */
status = fx_directory_next_full_entry_find(&my_media, entry_name, &attributes, &size,
                                           &year, &month, &day,
                                           &hour, &minute, &second);

/* If status equals FX_SUCCESS, the entry's information is in the local variables. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-934">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-934">See Also</span></span>

- <span data-ttu-id="887e6-935">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-935">fx_directory_attributes_read</span></span>
- <span data-ttu-id="887e6-936">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-936">fx_directory_attributes_set</span></span>
- <span data-ttu-id="887e6-937">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-937">fx_directory_create</span></span>
- <span data-ttu-id="887e6-938">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="887e6-938">fx_directory_default_get</span></span>
- <span data-ttu-id="887e6-939">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="887e6-939">fx_directory_default_set</span></span>
- <span data-ttu-id="887e6-940">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-940">fx_directory_delete</span></span>
- <span data-ttu-id="887e6-941">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-941">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="887e6-942">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-942">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="887e6-943">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="887e6-943">fx_directory_information_get</span></span>
- <span data-ttu-id="887e6-944">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="887e6-944">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="887e6-945">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="887e6-945">fx_directory_local_path_get</span></span>
- <span data-ttu-id="887e6-946">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="887e6-946">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="887e6-947">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="887e6-947">fx_directory_local_path_set</span></span>
- <span data-ttu-id="887e6-948">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-948">fx_directory_long_name_get</span></span>
- <span data-ttu-id="887e6-949">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="887e6-949">fx_directory_name_test</span></span>
- <span data-ttu-id="887e6-950">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-950">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="887e6-951">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-951">fx_directory_rename</span></span>
- <span data-ttu-id="887e6-952">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-952">fx_directory_short_name_get</span></span>
- <span data-ttu-id="887e6-953">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-953">fx_unicode_directory_create</span></span>
- <span data-ttu-id="887e6-954">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-954">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_rename"></a><span data-ttu-id="887e6-955">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-955">fx_directory_rename</span></span>

<span data-ttu-id="887e6-956">Переименовывает каталог</span><span class="sxs-lookup"><span data-stu-id="887e6-956">Renames directory</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-957">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-957">Prototype</span></span>

```c
UINT fx_directory_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_directory_name,
    CHAR *new_directory_name);
```

### <a name="description"></a><span data-ttu-id="887e6-958">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-958">Description</span></span>

<span data-ttu-id="887e6-959">Эта служба изменяет имя каталога на указанное новое имя каталога.</span><span class="sxs-lookup"><span data-stu-id="887e6-959">This service changes the directory name to the specified new directory name.</span></span> <span data-ttu-id="887e6-960">Переименование также выполняется относительно указанного пути или пути по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="887e6-960">Renaming is also done relative to the specified path or the default path.</span></span> <span data-ttu-id="887e6-961">Если в новом имени каталога указан путь, переименованный каталог фактически перемещается по указанному пути.</span><span class="sxs-lookup"><span data-stu-id="887e6-961">If a path is specified in the new directory name, the renamed directory is effectively moved to the specified path.</span></span> <span data-ttu-id="887e6-962">Если путь не указан, переименованный каталог помещается в текущий путь по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="887e6-962">If no path is specified, the renamed directory is placed in the current default path.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-963">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-963">Input Parameters</span></span>

- <span data-ttu-id="887e6-964">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-964">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="887e6-965">**old_directory_name**: указатель на текущее имя каталога</span><span class="sxs-lookup"><span data-stu-id="887e6-965">**old_directory_name**: Pointer to current directory name.</span></span>
- <span data-ttu-id="887e6-966">**new_directory_name**: указатель на новое имя каталога</span><span class="sxs-lookup"><span data-stu-id="887e6-966">**new_directory_name**: Pointer to new directory name.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-967">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-967">Return Values</span></span>

- <span data-ttu-id="887e6-968">**FX_SUCCESS** (0x00) — каталог успешно переименован.</span><span class="sxs-lookup"><span data-stu-id="887e6-968">**FX_SUCCESS** (0x00) Successful directory rename.</span></span>
- <span data-ttu-id="887e6-969">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-969">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="887e6-970">**FX_NOT_FOUND** (0x04) — не удалось найти запись каталога.</span><span class="sxs-lookup"><span data-stu-id="887e6-970">**FX_NOT_FOUND** (0x04) Directory entry could not be found.</span></span>
- <span data-ttu-id="887e6-971">**FX_NOT_DIRECTORY** (0x0E) — запись не является каталогом.</span><span class="sxs-lookup"><span data-stu-id="887e6-971">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory.</span></span>
- <span data-ttu-id="887e6-972">**FX_INVALID_NAME** (0x0C) — недопустимое имя каталога.</span><span class="sxs-lookup"><span data-stu-id="887e6-972">**FX_INVALID_NAME** (0x0C) New directory name is invalid.</span></span>
- <span data-ttu-id="887e6-973">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-973">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-974">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-974">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="887e6-975">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-975">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="887e6-976">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-976">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="887e6-977">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-977">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="887e6-978">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="887e6-978">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="887e6-979">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="887e6-979">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="887e6-980">**FX_NO_MORE_ENTRIES** (0x0F) — в этом каталоге больше нет записей.</span><span class="sxs-lookup"><span data-stu-id="887e6-980">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory.</span></span>
- <span data-ttu-id="887e6-981">**FX_INVALID_PATH** (0x0D) — указан недопустимый путь с именем каталога.</span><span class="sxs-lookup"><span data-stu-id="887e6-981">**FX_INVALID_PATH** (0x0D) Invalid path supplied with directory name.</span></span>
- <span data-ttu-id="887e6-982">**FX_ALREADY_CREATED** (0x0B) — указанный каталог уже создан.</span><span class="sxs-lookup"><span data-stu-id="887e6-982">**FX_ALREADY_CREATED** (0x0B) Specified directory was already created.</span></span>
- <span data-ttu-id="887e6-983">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-983">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="887e6-984">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-984">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-985">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-985">Allowed From</span></span>

<span data-ttu-id="887e6-986">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-986">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-987">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-987">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;

/* Change the directory "abc" to "def". */
status = fx_directory_rename(&my_media, "abc", "def");

/* If status equals FX_SUCCESS, the directory was changed to "def". */
```

### <a name="see-also"></a><span data-ttu-id="887e6-988">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-988">See Also</span></span>

- <span data-ttu-id="887e6-989">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-989">fx_directory_attributes_read</span></span>
- <span data-ttu-id="887e6-990">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-990">fx_directory_attributes_set</span></span>
- <span data-ttu-id="887e6-991">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-991">fx_directory_create</span></span>
- <span data-ttu-id="887e6-992">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="887e6-992">fx_directory_default_get</span></span>
- <span data-ttu-id="887e6-993">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="887e6-993">fx_directory_default_set</span></span>
- <span data-ttu-id="887e6-994">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-994">fx_directory_delete</span></span>
- <span data-ttu-id="887e6-995">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-995">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="887e6-996">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-996">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="887e6-997">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="887e6-997">fx_directory_information_get</span></span>
- <span data-ttu-id="887e6-998">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="887e6-998">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="887e6-999">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="887e6-999">fx_directory_local_path_get</span></span>
- <span data-ttu-id="887e6-1000">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="887e6-1000">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="887e6-1001">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1001">fx_directory_local_path_set</span></span>
- <span data-ttu-id="887e6-1002">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1002">fx_directory_long_name_get</span></span>
- <span data-ttu-id="887e6-1003">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="887e6-1003">fx_directory_name_test</span></span>
- <span data-ttu-id="887e6-1004">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-1004">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="887e6-1005">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-1005">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="887e6-1006">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1006">fx_directory_short_name_get</span></span>
- <span data-ttu-id="887e6-1007">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1007">fx_unicode_directory_create</span></span>
- <span data-ttu-id="887e6-1008">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1008">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_short_name_get"></a><span data-ttu-id="887e6-1009">fx_directory_short_name_get:</span><span class="sxs-lookup"><span data-stu-id="887e6-1009">fx_directory_short_name_get:</span></span>

<span data-ttu-id="887e6-1010">Получение краткого имени из длинного</span><span class="sxs-lookup"><span data-stu-id="887e6-1010">Gets short name from a long name</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-1011">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-1011">Prototype</span></span>

```c
UINT fx_directory_short_name_get(
    FX_MEDIA *media_ptr,
    CHAR *long_name, 
    CHAR *short_name);
```

### <a name="description"></a><span data-ttu-id="887e6-1012">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-1012">Description</span></span>

<span data-ttu-id="887e6-1013">Эта служба получает краткое имя (формат 8.3), связанное с переданным длинным именем.</span><span class="sxs-lookup"><span data-stu-id="887e6-1013">This service retrieves the short (8.3 format) name associated with the supplied long name.</span></span> <span data-ttu-id="887e6-1014">Длинное имя может быть либо именем файла, либо именем каталога.</span><span class="sxs-lookup"><span data-stu-id="887e6-1014">The long name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-1015">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-1015">Input Parameters</span></span>

- <span data-ttu-id="887e6-1016">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-1016">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="887e6-1017">**long_name**: указатель на исходное длинное имя</span><span class="sxs-lookup"><span data-stu-id="887e6-1017">**long_name**: Pointer to source long name.</span></span>
- <span data-ttu-id="887e6-1018">**short_name**: указатель на назначение краткого имени (формат 8.3)</span><span class="sxs-lookup"><span data-stu-id="887e6-1018">**short_name**: Pointer to destination short name (8.3 format).</span></span> <span data-ttu-id="887e6-1019">Обратите внимание, что назначение для краткого имени должно быть достаточно большим, чтобы вместить 14 символов.</span><span class="sxs-lookup"><span data-stu-id="887e6-1019">Note that the destination for the short name must be large enough to hold 14 characters.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-1020">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-1020">Return Values</span></span>

- <span data-ttu-id="887e6-1021">**FX_SUCCESS** (0x00) — краткое имя успешно получено.</span><span class="sxs-lookup"><span data-stu-id="887e6-1021">**FX_SUCCESS** (0x00) Successful short name get.</span></span>
- <span data-ttu-id="887e6-1022">**FX_NOT_FOUND** (0x04) — длинное имя не найдено.</span><span class="sxs-lookup"><span data-stu-id="887e6-1022">**FX_NOT_FOUND** (0x04) Long name was not found.</span></span>
- <span data-ttu-id="887e6-1023">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-1023">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-1024">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-1024">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="887e6-1025">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-1025">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="887e6-1026">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-1026">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="887e6-1027">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-1027">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="887e6-1028">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="887e6-1028">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="887e6-1029">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="887e6-1029">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="887e6-1030">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.</span><span class="sxs-lookup"><span data-stu-id="887e6-1030">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="887e6-1031">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-1031">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-1032">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-1032">Allowed From</span></span>

<span data-ttu-id="887e6-1033">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-1033">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-1034">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-1034">Example</span></span>

```c
FX_MEDIA         my_media;
UCHAR             my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get(&my_media,
    "my_really_long_name", my_short_name);

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-1035">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-1035">See Also</span></span>

- <span data-ttu-id="887e6-1036">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1036">fx_directory_attributes_read</span></span>
- <span data-ttu-id="887e6-1037">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1037">fx_directory_attributes_set</span></span>
- <span data-ttu-id="887e6-1038">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1038">fx_directory_create</span></span>
- <span data-ttu-id="887e6-1039">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1039">fx_directory_default_get</span></span>
- <span data-ttu-id="887e6-1040">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1040">fx_directory_default_set</span></span>
- <span data-ttu-id="887e6-1041">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-1041">fx_directory_delete</span></span>
- <span data-ttu-id="887e6-1042">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-1042">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="887e6-1043">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-1043">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="887e6-1044">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1044">fx_directory_information_get</span></span>
- <span data-ttu-id="887e6-1045">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="887e6-1045">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="887e6-1046">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1046">fx_directory_local_path_get</span></span>
- <span data-ttu-id="887e6-1047">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="887e6-1047">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="887e6-1048">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1048">fx_directory_local_path_set</span></span>
- <span data-ttu-id="887e6-1049">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1049">fx_directory_long_name_get</span></span>
- <span data-ttu-id="887e6-1050">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="887e6-1050">fx_directory_name_test</span></span>
- <span data-ttu-id="887e6-1051">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-1051">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="887e6-1052">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-1052">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="887e6-1053">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1053">fx_directory_rename</span></span>
- <span data-ttu-id="887e6-1054">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1054">fx_unicode_directory_create</span></span>
- <span data-ttu-id="887e6-1055">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1055">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_short_name_get_extended"></a><span data-ttu-id="887e6-1056">fx_directory_short_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="887e6-1056">fx_directory_short_name_get_extended</span></span>

<span data-ttu-id="887e6-1057">Получение краткого имени из длинного</span><span class="sxs-lookup"><span data-stu-id="887e6-1057">Gets short name from a long name</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-1058">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-1058">Prototype</span></span>

```csharp
UINT fx_directory_short_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *long_name,
    CHAR *short_name,
    UINT short_file_name_length);
```

### <a name="description"></a><span data-ttu-id="887e6-1059">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-1059">Description</span></span>

<span data-ttu-id="887e6-1060">Эта служба получает краткое имя (формат 8.3), связанное с переданным длинным именем.</span><span class="sxs-lookup"><span data-stu-id="887e6-1060">This service retrieves the short (8.3 format) name associated with the supplied long name.</span></span> <span data-ttu-id="887e6-1061">Длинное имя может быть либо именем файла, либо именем каталога.</span><span class="sxs-lookup"><span data-stu-id="887e6-1061">The long name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-1062">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-1062">Input Parameters</span></span>

- <span data-ttu-id="887e6-1063">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-1063">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="887e6-1064">**long_name**: указатель на исходное длинное имя</span><span class="sxs-lookup"><span data-stu-id="887e6-1064">**long_name**: Pointer to source long name.</span></span>
- <span data-ttu-id="887e6-1065">**short_name**: указатель на назначение краткого имени (формат 8.3)</span><span class="sxs-lookup"><span data-stu-id="887e6-1065">**short_name**: Pointer to destination short name (8.3 format).</span></span> <span data-ttu-id="887e6-1066">Обратите внимание, что назначение для краткого имени должно быть достаточно большим, чтобы вместить 14 символов.</span><span class="sxs-lookup"><span data-stu-id="887e6-1066">Note: Destination for the short name must be large enough to hold 14 characters.</span></span>
- <span data-ttu-id="887e6-1067">**short_file_name_length**: длина буфера коротких имен</span><span class="sxs-lookup"><span data-stu-id="887e6-1067">**short_file_name_length**: Length of short name buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-1068">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-1068">Return Values</span></span>

- <span data-ttu-id="887e6-1069">**FX_SUCCESS** (0x00) — краткое имя успешно получено.</span><span class="sxs-lookup"><span data-stu-id="887e6-1069">**FX_SUCCESS** (0x00) Successful short name get.</span></span>
- <span data-ttu-id="887e6-1070">**FX_NOT_FOUND** (0x04) — длинное имя не найдено.</span><span class="sxs-lookup"><span data-stu-id="887e6-1070">**FX_NOT_FOUND** (0x04) Long name was not found.</span></span>
- <span data-ttu-id="887e6-1071">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-1071">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-1072">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-1072">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="887e6-1073">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-1073">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="887e6-1074">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-1074">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="887e6-1075">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-1075">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="887e6-1076">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="887e6-1076">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="887e6-1077">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="887e6-1077">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="887e6-1078">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.</span><span class="sxs-lookup"><span data-stu-id="887e6-1078">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="887e6-1079">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-1079">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-1080">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-1080">Allowed From</span></span>

<span data-ttu-id="887e6-1081">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-1081">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-1082">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-1082">Example</span></span>

```c
FX_MEDIA        my_media;
UCHAR            my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get_extended(&my_media,
    "my_really_long_name", my_short_name, sizeof(my_short_name));

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-1083">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-1083">See Also</span></span>

- <span data-ttu-id="887e6-1084">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1084">fx_directory_attributes_read</span></span>
- <span data-ttu-id="887e6-1085">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1085">fx_directory_attributes_set</span></span>
- <span data-ttu-id="887e6-1086">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1086">fx_directory_create</span></span>
- <span data-ttu-id="887e6-1087">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1087">fx_directory_default_get</span></span>
- <span data-ttu-id="887e6-1088">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1088">fx_directory_default_set</span></span>
- <span data-ttu-id="887e6-1089">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-1089">fx_directory_delete</span></span>
- <span data-ttu-id="887e6-1090">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-1090">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="887e6-1091">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-1091">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="887e6-1092">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1092">fx_directory_information_get</span></span>
- <span data-ttu-id="887e6-1093">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="887e6-1093">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="887e6-1094">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1094">fx_directory_local_path_get</span></span>
- <span data-ttu-id="887e6-1095">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="887e6-1095">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="887e6-1096">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1096">fx_directory_local_path_set</span></span>
- <span data-ttu-id="887e6-1097">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1097">fx_directory_long_name_get</span></span>
- <span data-ttu-id="887e6-1098">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="887e6-1098">fx_directory_name_test</span></span>
- <span data-ttu-id="887e6-1099">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-1099">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="887e6-1100">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-1100">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="887e6-1101">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1101">fx_directory_rename</span></span>
- <span data-ttu-id="887e6-1102">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1102">fx_unicode_directory_create</span></span>
- <span data-ttu-id="887e6-1103">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1103">fx_unicode_directory_rename</span></span>

## <a name="fx_fault_tolerant_enable"></a><span data-ttu-id="887e6-1104">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="887e6-1104">fx_fault_tolerant_enable</span></span>

<span data-ttu-id="887e6-1105">Включает отказоустойчивую службу</span><span class="sxs-lookup"><span data-stu-id="887e6-1105">Enables the fault tolerant service</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-1106">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-1106">Prototype</span></span>

```csharp
UINT fx_fault_tolerant_enable(
    FX_MEDIA *media_ptr,
    VOID *memory_buffer,
    UINT memory_size);
```

### <a name="description"></a><span data-ttu-id="887e6-1107">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-1107">Description</span></span>

<span data-ttu-id="887e6-1108">Эта служба включает отказоустойчивый модуль.</span><span class="sxs-lookup"><span data-stu-id="887e6-1108">This service enables the fault tolerant module.</span></span> <span data-ttu-id="887e6-1109">После запуска отказоустойчивый модуль определяет, находится ли файловая система в режиме отказоустойчивой защиты FileX.</span><span class="sxs-lookup"><span data-stu-id="887e6-1109">Upon starting, the fault tolerant module detects whether or not the file system is under FileX fault tolerant protection.</span></span> <span data-ttu-id="887e6-1110">Если это не так, служба находит в файловой системе доступные секторы для хранения журналов транзакций файловой системы.</span><span class="sxs-lookup"><span data-stu-id="887e6-1110">If it is not, the service finds available sectors on the file system to store logs on file system transactions.</span></span> <span data-ttu-id="887e6-1111">Если файловая система находится в режиме отказоустойчивой защиты FileX, она применяет журналы к файловой системе для обеспечения целостности.</span><span class="sxs-lookup"><span data-stu-id="887e6-1111">If the file system is under FileX fault tolerant protection, it applies the logs to the file system to maintain its integrity.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-1112">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-1112">Input Parameters</span></span>

- <span data-ttu-id="887e6-1113">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-1113">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="887e6-1114">**memory_ptr**: указатель на блок памяти, используемый отказоустойчивым модулем в качестве вспомогательной памяти</span><span class="sxs-lookup"><span data-stu-id="887e6-1114">**memory_ptr**: Pointer to a block of memory used by the fault tolerant module as scratch memory.</span></span>
- <span data-ttu-id="887e6-1115">**memory_size**: размер вспомогательной памяти</span><span class="sxs-lookup"><span data-stu-id="887e6-1115">**memory_size**: The size of the scratch memory.</span></span> <span data-ttu-id="887e6-1116">Чтобы отказоустойчивость работала правильно, размер вспомогательной памяти должен составлять не менее 3072 байт и должен быть кратен размеру сектора.</span><span class="sxs-lookup"><span data-stu-id="887e6-1116">In order for fault tolerant to work properly, the scratch memory size shall be at least 3072 bytes,- and must be multiple of sector size.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-1117">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-1117">Return Values</span></span>

- <span data-ttu-id="887e6-1118">**FX_SUCCESS** (0x00) — отказоустойчивость успешно включена.</span><span class="sxs-lookup"><span data-stu-id="887e6-1118">**FX_SUCCESS** (0x00) Successfully enabled fault tolerant.</span></span>
- <span data-ttu-id="887e6-1119">**FX_NOT_ENOUGH_MEMORY** (0x91) — слишком маленький размер памяти.</span><span class="sxs-lookup"><span data-stu-id="887e6-1119">**FX_NOT_ENOUGH_MEMORY** (0x91)    memory size too small.</span></span>
- <span data-ttu-id="887e6-1120">**FX_BOOT_ERROR** (0x01) — ошибка загрузочного сектора.</span><span class="sxs-lookup"><span data-stu-id="887e6-1120">**FX_BOOT_ERROR** (0x01) Boot sector error.</span></span>
- <span data-ttu-id="887e6-1121">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-1121">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="887e6-1122">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет свободных кластеров.</span><span class="sxs-lookup"><span data-stu-id="887e6-1122">**FX_NO_MORE_ENTRIES** (0x0F) No more free cluster available.</span></span>
- <span data-ttu-id="887e6-1123">**FX_NO_MORE_SPACE** (0x0A) — на носителе, связанном с этим файлом, недостаточно доступных кластеров.</span><span class="sxs-lookup"><span data-stu-id="887e6-1123">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="887e6-1124">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-1124">**FX_SECTOR_INVALID** (0x89) Sector is invalid</span></span>
- <span data-ttu-id="887e6-1125">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-1125">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-1126">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-1126">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="887e6-1127">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-1127">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-1128">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-1128">Allowed From</span></span>

<span data-ttu-id="887e6-1129">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-1129">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-1130">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-1130">Example</span></span>

```c

/* Declare memory space used for fault tolerant. */

ULONG fault tolerant_memory[3072 / sizeof(ULONG)];

/* Enable fault tolerant. */

fx_fault_tolerant_enable(media_ptr, fault_tolerant_memory, sizeof(fault_tolerant_memory));

```

### <a name="see-also"></a><span data-ttu-id="887e6-1131">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-1131">See Also</span></span>

- <span data-ttu-id="887e6-1132">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="887e6-1132">fx_system_initialize</span></span>
- <span data-ttu-id="887e6-1133">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="887e6-1133">fx_media_abort</span></span>
- <span data-ttu-id="887e6-1134">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="887e6-1134">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="887e6-1135">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="887e6-1135">fx_media_check</span></span>
- <span data-ttu-id="887e6-1136">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="887e6-1136">fx_media_close</span></span>
- <span data-ttu-id="887e6-1137">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1137">fx_media_close_notify_set</span></span>
- <span data-ttu-id="887e6-1138">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="887e6-1138">fx_media_exFAT_format</span></span>
- <span data-ttu-id="887e6-1139">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-1139">fx_media_extended_space_available</span></span>
- <span data-ttu-id="887e6-1140">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="887e6-1140">fx_media_flush</span></span>
- <span data-ttu-id="887e6-1141">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="887e6-1141">fx_media_format</span></span>
- <span data-ttu-id="887e6-1142">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="887e6-1142">fx_media_open</span></span>
- <span data-ttu-id="887e6-1143">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1143">fx_media_open_notify_set</span></span>
- <span data-ttu-id="887e6-1144">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1144">fx_media_read</span></span>
- <span data-ttu-id="887e6-1145">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-1145">fx_media_space_available</span></span>
- <span data-ttu-id="887e6-1146">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1146">fx_media_volume_get</span></span>
- <span data-ttu-id="887e6-1147">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1147">fx_media_volume_set</span></span>
- <span data-ttu-id="887e6-1148">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="887e6-1148">fx_media_write</span></span>

## <a name="fx_file_allocate"></a><span data-ttu-id="887e6-1149">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1149">fx_file_allocate</span></span>

<span data-ttu-id="887e6-1150">Выделяет место для файла</span><span class="sxs-lookup"><span data-stu-id="887e6-1150">Allocates space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-1151">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-1151">Prototype</span></span>

```csharp
UINT fx_file_allocate(
    FX_FILE *file_ptr, 
    ULONG size);
```
### <a name="description"></a><span data-ttu-id="887e6-1152">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-1152">Description</span></span>

<span data-ttu-id="887e6-1153">Эта служба выделяет один кластер или несколько последовательных и связывает их с концом указанного файла.</span><span class="sxs-lookup"><span data-stu-id="887e6-1153">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="887e6-1154">FileX определяет количество кластеров, необходимое для деления запрошенного размера на число байтов на кластер.</span><span class="sxs-lookup"><span data-stu-id="887e6-1154">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="887e6-1155">Затем результат округляется до следующего целого кластера.</span><span class="sxs-lookup"><span data-stu-id="887e6-1155">The result is then rounded up to the next whole cluster.</span></span>

<span data-ttu-id="887e6-1156">Чтобы выделить место свыше 4 ГБ, приложение должно использовать службу *fx_file_extended_allocate*.</span><span class="sxs-lookup"><span data-stu-id="887e6-1156">To allocate space beyond 4GB, application shall use the service *fx_file_extended_allocate*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-1157">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-1157">Input Parameters</span></span>

- <span data-ttu-id="887e6-1158">**file_ptr**: указатель на открытый ранее файл</span><span class="sxs-lookup"><span data-stu-id="887e6-1158">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="887e6-1159">**size**: число байтов, выделяемых для файла</span><span class="sxs-lookup"><span data-stu-id="887e6-1159">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-1160">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-1160">Return Values</span></span>

- <span data-ttu-id="887e6-1161">**FX_SUCCESS** (0x00) — файл успешно выделен.</span><span class="sxs-lookup"><span data-stu-id="887e6-1161">**FX_SUCCESS** (0x00) Successful file allocation.</span></span>
- <span data-ttu-id="887e6-1162">**FX_ACCESS_ERROR** (0x06) — указанный файл не открыт для записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-1162">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="887e6-1163">**FX_FAT_READ_ERROR** (0x03) — не удалось прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-1163">**FX_FAT_READ_ERROR** (0x03) Failed to read FAT entry.</span></span>
- <span data-ttu-id="887e6-1164">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-1164">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="887e6-1165">**FX_NOT_OPEN** (0x07) — указанный файл в настоящее время не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-1165">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="887e6-1166">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет свободных кластеров.</span><span class="sxs-lookup"><span data-stu-id="887e6-1166">**FX_NO_MORE_ENTRIES** (0x0F) No more free cluster available.</span></span>
- <span data-ttu-id="887e6-1167">**FX_NO_MORE_SPACE** (0x0A) — на носителе, связанном с этим файлом, недостаточно доступных кластеров.</span><span class="sxs-lookup"><span data-stu-id="887e6-1167">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="887e6-1168">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-1168">**FX_SECTOR_INVALID** (0x89) Sector is invalid</span></span>
- <span data-ttu-id="887e6-1169">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-1169">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-1170">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-1170">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="887e6-1171">**FX_PTR_ERROR** (0x18) — недопустимый указатель на файл.</span><span class="sxs-lookup"><span data-stu-id="887e6-1171">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="887e6-1172">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-1172">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-1173">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-1173">Allowed From</span></span>

<span data-ttu-id="887e6-1174">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-1174">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-1175">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-1175">Example</span></span>

```c

FX_FILE            my_file;
UINT            status;

/* Allocate 1024 bytes to the end of my_file. */

status = fx_file_allocate(&my_file, 1024);

/* If status equals FX_SUCCESS the file now has one or more
    contiguous cluster(s) that can accommodate at least 1024 bytes of user data. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-1176">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-1176">See Also</span></span>

- <span data-ttu-id="887e6-1177">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1177">fx_file_attributes_read</span></span>
- <span data-ttu-id="887e6-1178">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1178">fx_file_attributes_set</span></span>
- <span data-ttu-id="887e6-1179">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1179">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-1180">fx_file_close- fx_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1180">fx_file_close- fx_file_create</span></span>
- <span data-ttu-id="887e6-1181">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1181">fx_file_date_time_set</span></span>
- <span data-ttu-id="887e6-1182">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-1182">fx_file_delete</span></span>
- <span data-ttu-id="887e6-1183">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1183">fx_file_extended_allocate</span></span>
- <span data-ttu-id="887e6-1184">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1184">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-1185">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1185">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="887e6-1186">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1186">fx_file_extended_seek</span></span>
- <span data-ttu-id="887e6-1187">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-1187">fx_file_extended_truncate</span></span>
- <span data-ttu-id="887e6-1188">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-1188">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="887e6-1189">fx_file_open- fx_file_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1189">fx_file_open- fx_file_read</span></span>
- <span data-ttu-id="887e6-1190">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1190">fx_file_relative_seek</span></span>
- <span data-ttu-id="887e6-1191">fx_file_rename- fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1191">fx_file_rename- fx_file_seek</span></span>
- <span data-ttu-id="887e6-1192">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-1192">fx_file_truncate</span></span>
- <span data-ttu-id="887e6-1193">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-1193">fx_file_truncate_release</span></span>
- <span data-ttu-id="887e6-1194">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="887e6-1194">fx_file_write</span></span>
- <span data-ttu-id="887e6-1195">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1195">fx_file_write_notify_set</span></span>
- <span data-ttu-id="887e6-1196">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1196">fx_unicode_file_create</span></span>
- <span data-ttu-id="887e6-1197">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1197">fx_unicode_file_rename</span></span>
- <span data-ttu-id="887e6-1198">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1198">fx_unicode_name_get</span></span>
- <span data-ttu-id="887e6-1199">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1199">fx_unicode_short_name_get</span></span>

## <a name="fx_file_attributes_read"></a><span data-ttu-id="887e6-1200">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1200">fx_file_attributes_read</span></span>

<span data-ttu-id="887e6-1201">Считывает атрибуты файла</span><span class="sxs-lookup"><span data-stu-id="887e6-1201">Reads file attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-1202">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-1202">Prototype</span></span>

```c
    UINT fx_file_attributes_read(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT *attributes_ptr);
```
### <a name="description"></a><span data-ttu-id="887e6-1203">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-1203">Description</span></span>

<span data-ttu-id="887e6-1204">Эта служба считывает атрибуты файла с указанного носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-1204">This service reads the file's attributes from the specified media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-1205">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-1205">Input Parameters</span></span>

- <span data-ttu-id="887e6-1206">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-1206">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="887e6-1207">**file_name**: указатель на имя запрошенного файла (путь к каталогу является необязательным)</span><span class="sxs-lookup"><span data-stu-id="887e6-1207">**file_name**: Pointer to the name of the requested file (directory path is optional).</span></span>
- <span data-ttu-id="887e6-1208">**attributes_ptr**: указатель на назначение для размещения атрибутов файла</span><span class="sxs-lookup"><span data-stu-id="887e6-1208">**attributes_ptr**: Pointer to the destination for the file's attributes to be placed.</span></span> <span data-ttu-id="887e6-1209">Атрибуты файла возвращаются в формате битовой карты со следующими возможными параметрами.</span><span class="sxs-lookup"><span data-stu-id="887e6-1209">The file attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="887e6-1210">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="887e6-1210">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="887e6-1211">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="887e6-1211">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="887e6-1212">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="887e6-1212">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="887e6-1213">FX_VOLUME (0x08)</span><span class="sxs-lookup"><span data-stu-id="887e6-1213">FX_VOLUME (0x08)</span></span>
  - <span data-ttu-id="887e6-1214">FX_DIRECTORY (0x10)</span><span class="sxs-lookup"><span data-stu-id="887e6-1214">FX_DIRECTORY (0x10)</span></span>
  - <span data-ttu-id="887e6-1215">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="887e6-1215">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-1216">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-1216">Return Values</span></span>

- <span data-ttu-id="887e6-1217">**FX_SUCCESS** (0x00) — атрибут успешно считан.</span><span class="sxs-lookup"><span data-stu-id="887e6-1217">**FX_SUCCESS** (0x00) Successful attribute read.</span></span>
- <span data-ttu-id="887e6-1218">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-1218">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="887e6-1219">**FX_NOT_FOUND** (0x04) — указанный файл не найден на носителе.</span><span class="sxs-lookup"><span data-stu-id="887e6-1219">**FX_NOT_FOUND** (0x04) Specified file was not found in the media.</span></span>
- <span data-ttu-id="887e6-1220">**FX_NOT_A_FILE** (0x05) — указанный файл является каталогом.</span><span class="sxs-lookup"><span data-stu-id="887e6-1220">**FX_NOT_A_FILE** (0x05) Specified file is a directory.</span></span>
- <span data-ttu-id="887e6-1221">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-1221">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="887e6-1222">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-1222">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="887e6-1223">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-1223">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="887e6-1224">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="887e6-1224">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="887e6-1225">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-1225">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-1226">**FX_PTR_ERROR** (0x18) — недопустимый носитель или указатель на атрибуты.</span><span class="sxs-lookup"><span data-stu-id="887e6-1226">**FX_PTR_ERROR** (0x18) Invalid media or attributes pointer.</span></span>
- <span data-ttu-id="887e6-1227">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-1227">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-1228">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-1228">Allowed From</span></span>

<span data-ttu-id="887e6-1229">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-1229">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-1230">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-1230">Example</span></span>

```c

FX_MEDIA         my_media;
UINT             status;
UINT             attributes;

/* Retrieve the attributes of "myfile.txt" from the specified media. */

status = fx_file_attributes_read(&my_media, "myfile.txt", &attributes);

/* If status equals FX_SUCCESS, "attributes"
    contains the file attributes for "myfile.txt". */

```

### <a name="see-also"></a><span data-ttu-id="887e6-1231">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-1231">See Also</span></span>

- <span data-ttu-id="887e6-1232">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1232">fx_file_allocate</span></span>
- <span data-ttu-id="887e6-1233">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1233">fx_file_attributes_set</span></span>
- <span data-ttu-id="887e6-1234">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1234">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-1235">fx_file_close- fx_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1235">fx_file_close- fx_file_create</span></span>
- <span data-ttu-id="887e6-1236">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1236">fx_file_date_time_set</span></span>
- <span data-ttu-id="887e6-1237">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-1237">fx_file_delete</span></span>
- <span data-ttu-id="887e6-1238">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1238">fx_file_extended_allocate</span></span>
- <span data-ttu-id="887e6-1239">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1239">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-1240">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1240">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="887e6-1241">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1241">fx_file_extended_seek</span></span>
- <span data-ttu-id="887e6-1242">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-1242">fx_file_extended_truncate</span></span>
- <span data-ttu-id="887e6-1243">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-1243">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="887e6-1244">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="887e6-1244">fx_file_open</span></span>
- <span data-ttu-id="887e6-1245">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1245">fx_file_read</span></span>
- <span data-ttu-id="887e6-1246">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1246">fx_file_relative_seek</span></span>
- <span data-ttu-id="887e6-1247">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1247">fx_file_rename</span></span>
- <span data-ttu-id="887e6-1248">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1248">fx_file_seek</span></span>
- <span data-ttu-id="887e6-1249">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-1249">fx_file_truncate</span></span>
- <span data-ttu-id="887e6-1250">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-1250">fx_file_truncate_release</span></span>
- <span data-ttu-id="887e6-1251">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="887e6-1251">fx_file_write</span></span>
- <span data-ttu-id="887e6-1252">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1252">fx_file_write_notify_set</span></span>
- <span data-ttu-id="887e6-1253">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1253">fx_unicode_file_create</span></span>
- <span data-ttu-id="887e6-1254">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1254">fx_unicode_file_rename</span></span>
- <span data-ttu-id="887e6-1255">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1255">fx_unicode_name_get</span></span>
- <span data-ttu-id="887e6-1256">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1256">fx_unicode_short_name_get</span></span>

## <a name="fx_file_attributes_set"></a><span data-ttu-id="887e6-1257">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1257">fx_file_attributes_set</span></span>

<span data-ttu-id="887e6-1258">Задает атрибуты файла</span><span class="sxs-lookup"><span data-stu-id="887e6-1258">Sets file attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-1259">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-1259">Prototype</span></span>

```c
UINT fx_file_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT attributes);
```
### <a name="description"></a><span data-ttu-id="887e6-1260">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-1260">Description</span></span>

<span data-ttu-id="887e6-1261">Эта служба задает атрибуты файла, указанные вызывающим объектом.</span><span class="sxs-lookup"><span data-stu-id="887e6-1261">This service sets the file's attributes to those specified by the caller.</span></span>

> [!WARNING]
> <span data-ttu-id="887e6-1262">*Этому приложению разрешено изменять только подмножество атрибутов файла, используя эту службу. Любая попытка задать дополнительные атрибуты приведет к ошибке.*</span><span class="sxs-lookup"><span data-stu-id="887e6-1262">*The application is only allowed to modify a subset of the file's attributes with this service. Any attempt to set additional attributes will result in an error.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-1263">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-1263">Input Parameters</span></span>

- <span data-ttu-id="887e6-1264">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-1264">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="887e6-1265">**file_name**: указатель на имя запрошенного файла\*\* (путь к каталогу является необязательным)</span><span class="sxs-lookup"><span data-stu-id="887e6-1265">**file_name**: Pointer to the name of the requested file\*\* (directory path is optional).</span></span>
- <span data-ttu-id="887e6-1266">**attributes**: новые атрибуты для файла</span><span class="sxs-lookup"><span data-stu-id="887e6-1266">**attributes**: The new attributes for the file.</span></span> <span data-ttu-id="887e6-1267">Допустимые атрибуты файла определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="887e6-1267">The valid file attributes are defined as follows:</span></span>
  - <span data-ttu-id="887e6-1268">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="887e6-1268">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="887e6-1269">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="887e6-1269">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="887e6-1270">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="887e6-1270">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="887e6-1271">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="887e6-1271">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-1272">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-1272">Return Values</span></span>

- <span data-ttu-id="887e6-1273">**FX_SUCCESS** (0x00) — атрибут успешно задан.</span><span class="sxs-lookup"><span data-stu-id="887e6-1273">**FX_SUCCESS** (0x00) Successful attribute set.</span></span>
- <span data-ttu-id="887e6-1274">**FX_ACCESS_ERROR** (0x06) — файл открыт, невозможно задать его атрибуты.</span><span class="sxs-lookup"><span data-stu-id="887e6-1274">**FX_ACCESS_ERROR** (0x06) File is open and cannot have its attributes set.</span></span>
- <span data-ttu-id="887e6-1275">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-1275">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="887e6-1276">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-1276">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="887e6-1277">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-1277">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="887e6-1278">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей в таблице FAT или карте кластера exFAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-1278">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in the FAT table or exFAT cluster map.</span></span>
- <span data-ttu-id="887e6-1279">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="887e6-1279">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="887e6-1280">**FX_NOT_FOUND** (0x04) — указанный файл не найден на носителе.</span><span class="sxs-lookup"><span data-stu-id="887e6-1280">**FX_NOT_FOUND** (0x04) Specified file was not found in the media.</span></span>
- <span data-ttu-id="887e6-1281">**FX_NOT_A_FILE** (0x05) — указанный файл является каталогом.</span><span class="sxs-lookup"><span data-stu-id="887e6-1281">**FX_NOT_A_FILE** (0x05) Specified file is a directory.</span></span>
- <span data-ttu-id="887e6-1282">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-1282">**FX_SECTOR_INVALID** (0x89) Sector is invalid</span></span>
- <span data-ttu-id="887e6-1283">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-1283">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-1284">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-1284">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="887e6-1285">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="887e6-1285">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="887e6-1286">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-1286">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="887e6-1287">**FX_INVALID_ATTR** (0x19) — выбраны недопустимые атрибуты.</span><span class="sxs-lookup"><span data-stu-id="887e6-1287">**FX_INVALID_ATTR** (0x19) Invalid attributes selected.</span></span>
- <span data-ttu-id="887e6-1288">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-1288">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-1289">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-1289">Allowed From</span></span>

<span data-ttu-id="887e6-1290">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-1290">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-1291">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-1291">Example</span></span>

```c

FX_MEDIA         my_media;
UINT             status;

/* Set the attributes of "myfile.txt" to read-only. */

status = fx_file_attributes_set(&my_media, "myfile.txt", FX_READ_ONLY);

/* If status equals FX_SUCCESS, the file is now read-only. */

```

### <a name="see-also"></a><span data-ttu-id="887e6-1292">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-1292">See Also</span></span>

- <span data-ttu-id="887e6-1293">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1293">fx_file_allocate</span></span>
- <span data-ttu-id="887e6-1294">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1294">fx_file_attributes_read</span></span>
- <span data-ttu-id="887e6-1295">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1295">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-1296">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="887e6-1296">fx_file_close</span></span>
- <span data-ttu-id="887e6-1297">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1297">fx_file_create</span></span>
- <span data-ttu-id="887e6-1298">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1298">fx_file_date_time_set</span></span>
- <span data-ttu-id="887e6-1299">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-1299">fx_file_delete</span></span>
- <span data-ttu-id="887e6-1300">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1300">fx_file_extended_allocate</span></span>
- <span data-ttu-id="887e6-1301">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1301">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-1302">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1302">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="887e6-1303">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1303">fx_file_extended_seek</span></span>
- <span data-ttu-id="887e6-1304">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-1304">fx_file_extended_truncate</span></span>
- <span data-ttu-id="887e6-1305">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-1305">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="887e6-1306">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="887e6-1306">fx_file_open</span></span>
- <span data-ttu-id="887e6-1307">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1307">fx_file_read</span></span>
- <span data-ttu-id="887e6-1308">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1308">fx_file_relative_seek</span></span>
- <span data-ttu-id="887e6-1309">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1309">fx_file_rename</span></span>
- <span data-ttu-id="887e6-1310">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1310">fx_file_seek</span></span>
- <span data-ttu-id="887e6-1311">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-1311">fx_file_truncate</span></span>
- <span data-ttu-id="887e6-1312">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-1312">fx_file_truncate_release</span></span>
- <span data-ttu-id="887e6-1313">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="887e6-1313">fx_file_write</span></span>
- <span data-ttu-id="887e6-1314">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1314">fx_file_write_notify_set</span></span>
- <span data-ttu-id="887e6-1315">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1315">fx_unicode_file_create</span></span>
- <span data-ttu-id="887e6-1316">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1316">fx_unicode_file_rename</span></span>
- <span data-ttu-id="887e6-1317">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1317">fx_unicode_name_get</span></span>
- <span data-ttu-id="887e6-1318">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1318">fx_unicode_short_name_get</span></span>

## <a name="fx_file_best_effort_allocate"></a><span data-ttu-id="887e6-1319">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1319">fx_file_best_effort_allocate</span></span>

<span data-ttu-id="887e6-1320">Наиболее оптимальное выделение пространства для файла</span><span class="sxs-lookup"><span data-stu-id="887e6-1320">Best effort to allocate space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-1321">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-1321">Prototype</span></span>

```c
UINT fx_file_best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG size,
    ULONG *actual_size_allocated);
```
### <a name="description"></a><span data-ttu-id="887e6-1322">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-1322">Description</span></span>

<span data-ttu-id="887e6-1323">Эта служба выделяет один кластер или несколько последовательных и связывает их с концом указанного файла.</span><span class="sxs-lookup"><span data-stu-id="887e6-1323">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="887e6-1324">FileX определяет количество кластеров, необходимое для деления запрошенного размера на число байтов на кластер.</span><span class="sxs-lookup"><span data-stu-id="887e6-1324">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="887e6-1325">Затем результат округляется до следующего целого кластера.</span><span class="sxs-lookup"><span data-stu-id="887e6-1325">The result is then rounded up to the next whole cluster.</span></span> <span data-ttu-id="887e6-1326">Если на носителе нет достаточного количества последовательных кластеров, эта служба связывает с файлом самый большой доступный блок последовательных кластеров.</span><span class="sxs-lookup"><span data-stu-id="887e6-1326">If there are not enough consecutive clusters available in the media, this service links the largest available block of consecutive clusters to the file.</span></span> <span data-ttu-id="887e6-1327">Объем пространства, фактически выделяемый файлу, возвращается вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="887e6-1327">The amount of space actually allocated to the file is returned to the caller.</span></span>

<span data-ttu-id="887e6-1328">Чтобы выделить место свыше 4 ГБ, приложение должно использовать службу *fx_file_extended_best_effort_allocate*.</span><span class="sxs-lookup"><span data-stu-id="887e6-1328">To allocate space beyond 4GB, application shall use the service *fx_file_extended_best_effort_allocate*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-1329">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-1329">Input Parameters</span></span>

- <span data-ttu-id="887e6-1330">**file_ptr**: указатель на открытый ранее файл</span><span class="sxs-lookup"><span data-stu-id="887e6-1330">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="887e6-1331">**size**: число байтов, выделяемых для файла</span><span class="sxs-lookup"><span data-stu-id="887e6-1331">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-1332">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-1332">Return Values</span></span>

- <span data-ttu-id="887e6-1333">**FX_SUCCESS** (0x00) — наиболее оптимальное выделение пространства для файла успешно выполнено.</span><span class="sxs-lookup"><span data-stu-id="887e6-1333">**FX_SUCCESS** (0x00) Successful best-effort file allocation.</span></span>
- <span data-ttu-id="887e6-1334">**FX_ACCESS_ERROR** (0x06) — указанный файл не открыт для записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-1334">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="887e6-1335">**FX_NOT_OPEN** (0x07) — указанный файл в настоящее время не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-1335">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="887e6-1336">**FX_NO_MORE_SPACE** (0x0A) — на носителе, связанном с этим файлом, недостаточно доступных кластеров.</span><span class="sxs-lookup"><span data-stu-id="887e6-1336">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="887e6-1337">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-1337">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="887e6-1338">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-1338">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="887e6-1339">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-1339">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="887e6-1340">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-1340">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="887e6-1341">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-1341">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-1342">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-1342">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="887e6-1343">**FX_PTR_ERROR** (0x18) — недопустимый указатель или назначение файла.</span><span class="sxs-lookup"><span data-stu-id="887e6-1343">**FX_PTR_ERROR** (0x18) Invalid file pointer or destination.</span></span>
- <span data-ttu-id="887e6-1344">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-1344">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-1345">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-1345">Allowed From</span></span>

<span data-ttu-id="887e6-1346">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-1346">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-1347">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-1347">Example</span></span>

```c

FX_FILE         my_file;
UINT             status;
ULONG             actual_allocation;

/* Attempt to allocate 1024 bytes to the end of my_file. */

status = fx_file_best_effort_allocate(&my_file, 1024, &actual_allocation);

/* If status equals FX_SUCCESS, the number of bytes
    allocated to the file is found in actual_allocation. */

```

### <a name="see-also"></a><span data-ttu-id="887e6-1348">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-1348">See Also</span></span>

- <span data-ttu-id="887e6-1349">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1349">fx_file_allocate</span></span>
- <span data-ttu-id="887e6-1350">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1350">fx_file_attributes_read</span></span>
- <span data-ttu-id="887e6-1351">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1351">fx_file_attributes_set</span></span>
- <span data-ttu-id="887e6-1352">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="887e6-1352">fx_file_close</span></span>
- <span data-ttu-id="887e6-1353">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1353">fx_file_create</span></span>
- <span data-ttu-id="887e6-1354">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1354">fx_file_date_time_set</span></span>
- <span data-ttu-id="887e6-1355">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-1355">fx_file_delete</span></span>
- <span data-ttu-id="887e6-1356">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1356">fx_file_extended_allocate</span></span>
- <span data-ttu-id="887e6-1357">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1357">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-1358">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1358">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="887e6-1359">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1359">fx_file_extended_seek</span></span>
- <span data-ttu-id="887e6-1360">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-1360">fx_file_extended_truncate</span></span>
- <span data-ttu-id="887e6-1361">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-1361">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="887e6-1362">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="887e6-1362">fx_file_open</span></span>
- <span data-ttu-id="887e6-1363">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1363">fx_file_read</span></span>
- <span data-ttu-id="887e6-1364">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1364">fx_file_relative_seek</span></span>
- <span data-ttu-id="887e6-1365">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1365">fx_file_rename</span></span>
- <span data-ttu-id="887e6-1366">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1366">fx_file_seek</span></span>
- <span data-ttu-id="887e6-1367">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-1367">fx_file_truncate</span></span>
- <span data-ttu-id="887e6-1368">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-1368">fx_file_truncate_release</span></span>
- <span data-ttu-id="887e6-1369">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="887e6-1369">fx_file_write</span></span>
- <span data-ttu-id="887e6-1370">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1370">fx_file_write_notify_set</span></span>
- <span data-ttu-id="887e6-1371">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1371">fx_unicode_file_create</span></span>
- <span data-ttu-id="887e6-1372">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1372">fx_unicode_file_rename</span></span>
- <span data-ttu-id="887e6-1373">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1373">fx_unicode_name_get</span></span>
- <span data-ttu-id="887e6-1374">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1374">fx_unicode_short_name_get</span></span>

## <a name="fx_file_close"></a><span data-ttu-id="887e6-1375">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="887e6-1375">fx_file_close</span></span>

<span data-ttu-id="887e6-1376">Закрывает файл</span><span class="sxs-lookup"><span data-stu-id="887e6-1376">Closes file</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-1377">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-1377">Prototype</span></span>

```c
UINT fx_file_close(FX_FILE *file_ptr);
```
### <a name="description"></a><span data-ttu-id="887e6-1378">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-1378">Description</span></span>

<span data-ttu-id="887e6-1379">Эта служба закрывает указанный файл.</span><span class="sxs-lookup"><span data-stu-id="887e6-1379">This service closes the specified file.</span></span> <span data-ttu-id="887e6-1380">Если файл был открыт для записи и если он был изменен, эта служба завершает процесс изменения файла, обновляя запись каталога с новым размером и текущими системными временем и датой.</span><span class="sxs-lookup"><span data-stu-id="887e6-1380">If the file was open for writing and if it was modified, this service completes the file modification process by updating its directory entry with the new size and the current system time and date.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-1381">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-1381">Input Parameters</span></span>

- <span data-ttu-id="887e6-1382">**file_ptr**: указатель на открытый ранее файл</span><span class="sxs-lookup"><span data-stu-id="887e6-1382">**file_ptr**: Pointer to a previously opened file.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-1383">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-1383">Return Values</span></span>

- <span data-ttu-id="887e6-1384">**FX_SUCCESS** (0x00) — файл успешно закрыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-1384">**FX_SUCCESS** (0x00) Successful file close.</span></span>
- <span data-ttu-id="887e6-1385">**FX_NOT_OPEN** (0x07) — указанный файл не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-1385">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="887e6-1386">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-1386">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="887e6-1387">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-1387">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="887e6-1388">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-1388">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-1389">**FX_PTR_ERROR** (0x18) — недопустимый носитель или указатель на атрибуты.</span><span class="sxs-lookup"><span data-stu-id="887e6-1389">**FX_PTR_ERROR** (0x18) Invalid media or attributes pointer.</span></span>
- <span data-ttu-id="887e6-1390">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-1390">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-1391">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-1391">Allowed From</span></span>

<span data-ttu-id="887e6-1392">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-1392">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-1393">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-1393">Example</span></span>

```c

FX_FILE        my_file;
UINT        status;

/* Close the previously opened file "my_file". */
status = fx_file_close(&my_file);

/* If status equals FX_SUCCESS, the file was closed successfully. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-1394">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-1394">See Also</span></span>

- <span data-ttu-id="887e6-1395">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1395">fx_file_allocate</span></span>
- <span data-ttu-id="887e6-1396">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1396">fx_file_attributes_read</span></span>
- <span data-ttu-id="887e6-1397">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1397">fx_file_attributes_set</span></span>
- <span data-ttu-id="887e6-1398">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1398">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-1399">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1399">fx_file_create</span></span>
- <span data-ttu-id="887e6-1400">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1400">fx_file_date_time_set</span></span>
- <span data-ttu-id="887e6-1401">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-1401">fx_file_delete</span></span>
- <span data-ttu-id="887e6-1402">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1402">fx_file_extended_allocate</span></span>
- <span data-ttu-id="887e6-1403">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1403">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-1404">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1404">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="887e6-1405">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1405">fx_file_extended_seek</span></span>
- <span data-ttu-id="887e6-1406">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-1406">fx_file_extended_truncate</span></span>
- <span data-ttu-id="887e6-1407">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-1407">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="887e6-1408">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="887e6-1408">fx_file_open</span></span>
- <span data-ttu-id="887e6-1409">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1409">fx_file_read</span></span>
- <span data-ttu-id="887e6-1410">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1410">fx_file_relative_seek</span></span>
- <span data-ttu-id="887e6-1411">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1411">fx_file_rename</span></span>
- <span data-ttu-id="887e6-1412">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1412">fx_file_seek</span></span>
- <span data-ttu-id="887e6-1413">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-1413">fx_file_truncate</span></span>
- <span data-ttu-id="887e6-1414">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-1414">fx_file_truncate_release</span></span>
- <span data-ttu-id="887e6-1415">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="887e6-1415">fx_file_write</span></span>
- <span data-ttu-id="887e6-1416">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1416">fx_file_write_notify_set</span></span>
- <span data-ttu-id="887e6-1417">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1417">fx_unicode_file_create</span></span>
- <span data-ttu-id="887e6-1418">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1418">fx_unicode_file_rename</span></span>
- <span data-ttu-id="887e6-1419">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1419">fx_unicode_name_get</span></span>
- <span data-ttu-id="887e6-1420">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1420">fx_unicode_short_name_get</span></span>

## <a name="fx_file_create"></a><span data-ttu-id="887e6-1421">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1421">fx_file_create</span></span>

<span data-ttu-id="887e6-1422">Создает файл</span><span class="sxs-lookup"><span data-stu-id="887e6-1422">Creates file</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-1423">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-1423">Prototype</span></span>

```c
UINT fx_file_create(
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```
### <a name="description"></a><span data-ttu-id="887e6-1424">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-1424">Description</span></span>

<span data-ttu-id="887e6-1425">Эта служба создает указанный файл в каталоге по умолчанию или в каталоге, путь к которому указан с именем файла.</span><span class="sxs-lookup"><span data-stu-id="887e6-1425">This service creates the specified file in the default directory or in the directory path supplied with the file name.</span></span>

> [!WARNING]
> <span data-ttu-id="887e6-1426">*Эта служба создает файл нулевой длины, т. е. без выделенных кластеров. Выделение будет автоматически выполняться при последующих операциях записи файла. Также это можно сделать заранее с помощью службы fx_file_allocate или fx_file_extended_allocate, если размер превышает 4 ГБ).*</span><span class="sxs-lookup"><span data-stu-id="887e6-1426">*This service creates a file of zero length, i.e., no clusters allocated. Allocation will automatically take place on subsequent file writes or can be done in advance with the fx_file_allocate service or fx_file_extended_allocate for space beyond 4GB) service.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-1427">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-1427">Input Parameters</span></span>

- <span data-ttu-id="887e6-1428">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-1428">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="887e6-1429">**file_name**: указатель на имя создаваемого файла (путь к каталогу является необязательным)</span><span class="sxs-lookup"><span data-stu-id="887e6-1429">**file_name**: Pointer to the name of the file to create (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-1430">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-1430">Return Values</span></span>

- <span data-ttu-id="887e6-1431">**FX_SUCCESS** (0x00) — файл успешно создан.</span><span class="sxs-lookup"><span data-stu-id="887e6-1431">**FX_SUCCESS** (0x00) Successful file create.</span></span>
- <span data-ttu-id="887e6-1432">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-1432">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="887e6-1433">**FX_ALREADY_CREATED** (0x0B) — указанный файл уже создан.</span><span class="sxs-lookup"><span data-stu-id="887e6-1433">**FX_ALREADY_CREATED** (0x0B) Specified file was already created.</span></span>
- <span data-ttu-id="887e6-1434">**FX_NO_MORE_SPACE** (0x0A) —  в корневом каталоге больше нет записей, или нет доступных кластеров.</span><span class="sxs-lookup"><span data-stu-id="887e6-1434">**FX_NO_MORE_SPACE** (0x0A)    Either there are no more entries in the root directory or there are no more clusters available.</span></span>
- <span data-ttu-id="887e6-1435">**FX_INVALID_PATH** (0x0D) — указан недопустимый путь с именем файла.</span><span class="sxs-lookup"><span data-stu-id="887e6-1435">**FX_INVALID_PATH** (0x0D) Invalid path supplied with file name.</span></span>
- <span data-ttu-id="887e6-1436">**FX_INVALID_NAME** (0x0C) — недопустимое имя файла.</span><span class="sxs-lookup"><span data-stu-id="887e6-1436">**FX_INVALID_NAME** (0x0C) File name is invalid.</span></span>
- <span data-ttu-id="887e6-1437">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-1437">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="887e6-1438">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-1438">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="887e6-1439">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-1439">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="887e6-1440">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-1440">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="887e6-1441">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="887e6-1441">**FX_NO_MORE_SPACE** (0x0A)    No more space to complete the operation</span></span>
- <span data-ttu-id="887e6-1442">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="887e6-1442">**FX_MEDIA_INVALID** (0x02)Invalid media.</span></span>
- <span data-ttu-id="887e6-1443">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-1443">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-1444">**FX_WRITE_PROTECT** (0x23) — носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-1444">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="887e6-1445">**FX_PTR_ERROR** (0x18) — недопустимый носитель или указатель имени файла.</span><span class="sxs-lookup"><span data-stu-id="887e6-1445">**FX_PTR_ERROR** (0x18) Invalid media or file name pointer.</span></span>
- <span data-ttu-id="887e6-1446">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-1446">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-1447">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-1447">Allowed From</span></span>

<span data-ttu-id="887e6-1448">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-1448">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-1449">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-1449">Example</span></span>

```c

FX_MEDIA         my_media;
UINT             status;

/* Create a file called "myfile.txt" in the
    root or the default directory of the media. */

status = fx_file_create(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, a zero sized file named "myfile.txt". */
```

### <a name="see-also"></a><span data-ttu-id="887e6-1450">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-1450">See Also</span></span>
- <span data-ttu-id="887e6-1451">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1451">fx_file_allocate</span></span>
- <span data-ttu-id="887e6-1452">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1452">fx_file_attributes_read</span></span>
- <span data-ttu-id="887e6-1453">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1453">fx_file_attributes_set</span></span>
- <span data-ttu-id="887e6-1454">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1454">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-1455">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="887e6-1455">fx_file_close</span></span>
- <span data-ttu-id="887e6-1456">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1456">fx_file_date_time_set</span></span>
- <span data-ttu-id="887e6-1457">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-1457">fx_file_delete</span></span>
- <span data-ttu-id="887e6-1458">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1458">fx_file_extended_allocate</span></span>
- <span data-ttu-id="887e6-1459">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1459">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-1460">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1460">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="887e6-1461">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1461">fx_file_extended_seek</span></span>
- <span data-ttu-id="887e6-1462">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-1462">fx_file_extended_truncate</span></span>
- <span data-ttu-id="887e6-1463">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-1463">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="887e6-1464">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="887e6-1464">fx_file_open</span></span>
- <span data-ttu-id="887e6-1465">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1465">fx_file_read</span></span>
- <span data-ttu-id="887e6-1466">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1466">fx_file_relative_seek</span></span>
- <span data-ttu-id="887e6-1467">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1467">fx_file_rename</span></span>
- <span data-ttu-id="887e6-1468">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1468">fx_file_seek</span></span>
- <span data-ttu-id="887e6-1469">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-1469">fx_file_truncate</span></span>
- <span data-ttu-id="887e6-1470">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-1470">fx_file_truncate_release</span></span>
- <span data-ttu-id="887e6-1471">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="887e6-1471">fx_file_write</span></span>
- <span data-ttu-id="887e6-1472">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1472">fx_file_write_notify_set</span></span>
- <span data-ttu-id="887e6-1473">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1473">fx_unicode_file_create</span></span>
- <span data-ttu-id="887e6-1474">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1474">fx_unicode_file_rename</span></span>
- <span data-ttu-id="887e6-1475">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1475">fx_unicode_name_get</span></span>
- <span data-ttu-id="887e6-1476">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1476">fx_unicode_short_name_get</span></span>

## <a name="fx_file_date_time_set"></a><span data-ttu-id="887e6-1477">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1477">fx_file_date_time_set</span></span>

### <a name="sets-file-date-and-time"></a><span data-ttu-id="887e6-1478">Задает дату и время файла</span><span class="sxs-lookup"><span data-stu-id="887e6-1478">Sets file date and time</span></span>

<span data-ttu-id="887e6-1479">Задание даты и времени для файла</span><span class="sxs-lookup"><span data-stu-id="887e6-1479">Setting File Date and Time</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-1480">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-1480">Prototype</span></span>

```c
UINT fx_file_date_time_set(
    FX_MEDIA *media_ptr, 
    CHAR *file_name,
    UINT year, 
    UINT month, 
    UINT day,
    UINT hour, 
    UINT minute, 
    UINT second);
```
### <a name="description"></a><span data-ttu-id="887e6-1481">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-1481">Description</span></span>

<span data-ttu-id="887e6-1482">Эта служба задает дату и время для указанного файла.</span><span class="sxs-lookup"><span data-stu-id="887e6-1482">This service sets the date and time of the specified file.</span></span>

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="input-parameters"></a><span data-ttu-id="887e6-1483">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-1483">Input Parameters</span></span>

- <span data-ttu-id="887e6-1484">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-1484">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="887e6-1485">**file_name**: указатель на имя файла</span><span class="sxs-lookup"><span data-stu-id="887e6-1485">**file_name**: Pointer to name of the file.</span></span>
- <span data-ttu-id="887e6-1486">**year**: значение года (1980–2107 включительно)</span><span class="sxs-lookup"><span data-stu-id="887e6-1486">**year**: Value of year (1980-2107 inclusive).</span></span>
- <span data-ttu-id="887e6-1487">**month**: значение месяца (1–12 включительно)</span><span class="sxs-lookup"><span data-stu-id="887e6-1487">**month**: Value of month (1-12 inclusive).</span></span>
- <span data-ttu-id="887e6-1488">**day**: значение дня (1–31 включительно)</span><span class="sxs-lookup"><span data-stu-id="887e6-1488">**day**: Value of day (1-31 inclusive).</span></span>
- <span data-ttu-id="887e6-1489">**hour**: значение часа (0–23 включительно)</span><span class="sxs-lookup"><span data-stu-id="887e6-1489">**hour**: Value of hour (0-23 inclusive).</span></span>
- <span data-ttu-id="887e6-1490">**minute**: значение минуты (0–59 включительно)</span><span class="sxs-lookup"><span data-stu-id="887e6-1490">**minute**: Value of minute (0-59 inclusive).</span></span>
- <span data-ttu-id="887e6-1491">**second**: значение секунды (0–59 включительно)</span><span class="sxs-lookup"><span data-stu-id="887e6-1491">**second**: Value of second (0-59 inclusive).</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-1492">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-1492">Return Values</span></span>

- <span data-ttu-id="887e6-1493">**FX_SUCCESS** (0x00) — дата/время успешно заданы.</span><span class="sxs-lookup"><span data-stu-id="887e6-1493">**FX_SUCCESS** (0x00) Successful date/time set.</span></span>
- <span data-ttu-id="887e6-1494">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-1494">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="887e6-1495">**FX_NOT_FOUND** (0x04) — файл не найден.</span><span class="sxs-lookup"><span data-stu-id="887e6-1495">**FX_NOT_FOUND** (0x04)    File was not found.</span></span>
- <span data-ttu-id="887e6-1496">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-1496">**FX_FILE_CORRUPT** (0x08)    File is corrupted.</span></span>
- <span data-ttu-id="887e6-1497">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-1497">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="887e6-1498">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-1498">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="887e6-1499">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-1499">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="887e6-1500">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="887e6-1500">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="887e6-1501">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-1501">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-1502">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-1502">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="887e6-1503">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.</span><span class="sxs-lookup"><span data-stu-id="887e6-1503">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="887e6-1504">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-1504">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>
- <span data-ttu-id="887e6-1505">**FX_INVALID_YEAR** (0x12) — недопустимый год.</span><span class="sxs-lookup"><span data-stu-id="887e6-1505">**FX_INVALID_YEAR** (0x12) Year is invalid.</span></span>
- <span data-ttu-id="887e6-1506">**FX_INVALID_MONTH** (0x13) — недопустимый месяц.</span><span class="sxs-lookup"><span data-stu-id="887e6-1506">**FX_INVALID_MONTH** (0x13) Month is invalid.</span></span>
- <span data-ttu-id="887e6-1507">**FX_INVALID_DAY** (0x14) — недопустимый день.</span><span class="sxs-lookup"><span data-stu-id="887e6-1507">**FX_INVALID_DAY** (0x14) Day is invalid.</span></span>
- <span data-ttu-id="887e6-1508">**FX_INVALID_HOUR** (0x15) — недопустимый час.</span><span class="sxs-lookup"><span data-stu-id="887e6-1508">**FX_INVALID_HOUR** (0x15)    Hour is invalid.</span></span>
- <span data-ttu-id="887e6-1509">**FX_INVALID_MINUTE** (0x16) — недопустимая минута.</span><span class="sxs-lookup"><span data-stu-id="887e6-1509">**FX_INVALID_MINUTE** (0x16) Minute is invalid.</span></span>
- <span data-ttu-id="887e6-1510">**FX_INVALID_SECOND** (0x17) — недопустимая секунда.</span><span class="sxs-lookup"><span data-stu-id="887e6-1510">**FX_INVALID_SECOND** (0x17) Second is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-1511">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-1511">Allowed From</span></span>

<span data-ttu-id="887e6-1512">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-1512">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-1513">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-1513">Example</span></span>

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="see-also"></a><span data-ttu-id="887e6-1514">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-1514">See Also</span></span>

- <span data-ttu-id="887e6-1515">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1515">fx_file_allocate</span></span>
- <span data-ttu-id="887e6-1516">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1516">fx_file_attributes_read</span></span>
- <span data-ttu-id="887e6-1517">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1517">fx_file_attributes_set</span></span>
- <span data-ttu-id="887e6-1518">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1518">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-1519">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="887e6-1519">fx_file_close</span></span>
- <span data-ttu-id="887e6-1520">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1520">fx_file_create</span></span>
- <span data-ttu-id="887e6-1521">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-1521">fx_file_delete</span></span>
- <span data-ttu-id="887e6-1522">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1522">fx_file_extended_allocate</span></span>
- <span data-ttu-id="887e6-1523">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1523">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-1524">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1524">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="887e6-1525">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1525">fx_file_extended_seek</span></span>
- <span data-ttu-id="887e6-1526">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-1526">fx_file_extended_truncate</span></span>
- <span data-ttu-id="887e6-1527">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-1527">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="887e6-1528">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="887e6-1528">fx_file_open</span></span>
- <span data-ttu-id="887e6-1529">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1529">fx_file_read</span></span>
- <span data-ttu-id="887e6-1530">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1530">fx_file_relative_seek</span></span>
- <span data-ttu-id="887e6-1531">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1531">fx_file_rename</span></span>
- <span data-ttu-id="887e6-1532">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1532">fx_file_seek</span></span>
- <span data-ttu-id="887e6-1533">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-1533">fx_file_truncate</span></span>
- <span data-ttu-id="887e6-1534">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-1534">fx_file_truncate_release</span></span>
- <span data-ttu-id="887e6-1535">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="887e6-1535">fx_file_write</span></span>
- <span data-ttu-id="887e6-1536">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1536">fx_file_write_notify_set</span></span>
- <span data-ttu-id="887e6-1537">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1537">fx_unicode_file_create</span></span>
- <span data-ttu-id="887e6-1538">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1538">fx_unicode_file_rename</span></span>
- <span data-ttu-id="887e6-1539">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1539">fx_unicode_name_get</span></span>
- <span data-ttu-id="887e6-1540">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1540">fx_unicode_short_name_get</span></span>

## <a name="fx_file_delete"></a><span data-ttu-id="887e6-1541">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-1541">fx_file_delete</span></span>

### <a name="deletes-file"></a><span data-ttu-id="887e6-1542">Удаляет файл</span><span class="sxs-lookup"><span data-stu-id="887e6-1542">Deletes file</span></span>

<span data-ttu-id="887e6-1543">Удаление файла</span><span class="sxs-lookup"><span data-stu-id="887e6-1543">File Deletion</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-1544">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-1544">Prototype</span></span>

```c
UINT fx_file_delete(
    FX_MEDIA *media_ptr, 
    CHAR *file_name);
```
### <a name="description"></a><span data-ttu-id="887e6-1545">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-1545">Description</span></span>

<span data-ttu-id="887e6-1546">Эта служба удаляет указанный файл.</span><span class="sxs-lookup"><span data-stu-id="887e6-1546">This service deletes the specified file.</span></span>


### <a name="input-parameters"></a><span data-ttu-id="887e6-1547">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-1547">Input Parameters</span></span>

- <span data-ttu-id="887e6-1548">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-1548">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="887e6-1549">**file_name**: указатель на имя удаляемого файла (путь к каталогу является необязательным)</span><span class="sxs-lookup"><span data-stu-id="887e6-1549">**file_name**: Pointer to the name of the file to delete (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-1550">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-1550">Return Values</span></span>

- <span data-ttu-id="887e6-1551">**FX_SUCCESS** (0x00) — файл успешно удален.</span><span class="sxs-lookup"><span data-stu-id="887e6-1551">**FX_SUCCESS** (0x00) Successful file delete.</span></span>
- <span data-ttu-id="887e6-1552">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-1552">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="887e6-1553">**FX_NOT_FOUND** (0x04) — указанный файл не найден.</span><span class="sxs-lookup"><span data-stu-id="887e6-1553">**FX_NOT_FOUND** (0x04) Specified file was not found.</span></span>
- <span data-ttu-id="887e6-1554">**FX_NOT_A_FILE** (0x05) — указанное имя файла является каталогом или томом.</span><span class="sxs-lookup"><span data-stu-id="887e6-1554">**FX_NOT_A_FILE** (0x05) Specified file name was a directory or volume.</span></span>
- <span data-ttu-id="887e6-1555">**FX_ACCESS_ERROR** (0x06) — указанный файл в настоящее время открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-1555">**FX_ACCESS_ERROR** (0x06) Specified file is currently open.</span></span>
- <span data-ttu-id="887e6-1556">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-1556">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="887e6-1557">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-1557">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="887e6-1558">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-1558">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="887e6-1559">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-1559">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="887e6-1560">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="887e6-1560">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="887e6-1561">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-1561">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-1562">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-1562">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="887e6-1563">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="887e6-1563">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="887e6-1564">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-1564">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="887e6-1565">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-1565">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-1566">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-1566">Allowed From</span></span>

<span data-ttu-id="887e6-1567">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-1567">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-1568">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-1568">Example</span></span>

```c

FX_MEDIA            my_media;
UINT                 status;
/* Delete the file "myfile.txt". */

status = fx_file_delete(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, "myfile.txt" has been deleted. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-1569">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-1569">See Also</span></span>

- <span data-ttu-id="887e6-1570">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1570">fx_file_allocate</span></span>
- <span data-ttu-id="887e6-1571">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1571">fx_file_attributes_read</span></span>
- <span data-ttu-id="887e6-1572">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1572">fx_file_attributes_set</span></span>
- <span data-ttu-id="887e6-1573">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1573">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-1574">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="887e6-1574">fx_file_close</span></span>
- <span data-ttu-id="887e6-1575">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1575">fx_file_create</span></span>
- <span data-ttu-id="887e6-1576">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1576">fx_file_date_time_set</span></span>
- <span data-ttu-id="887e6-1577">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1577">fx_file_extended_allocate</span></span>
- <span data-ttu-id="887e6-1578">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1578">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-1579">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1579">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="887e6-1580">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1580">fx_file_extended_seek</span></span>
- <span data-ttu-id="887e6-1581">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-1581">fx_file_extended_truncate</span></span>
- <span data-ttu-id="887e6-1582">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-1582">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="887e6-1583">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="887e6-1583">fx_file_open</span></span>
- <span data-ttu-id="887e6-1584">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1584">fx_file_read</span></span>
- <span data-ttu-id="887e6-1585">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1585">fx_file_relative_seek</span></span>
- <span data-ttu-id="887e6-1586">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1586">fx_file_rename</span></span>
- <span data-ttu-id="887e6-1587">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1587">fx_file_seek</span></span>
- <span data-ttu-id="887e6-1588">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-1588">fx_file_truncate</span></span>
- <span data-ttu-id="887e6-1589">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-1589">fx_file_truncate_release</span></span>
- <span data-ttu-id="887e6-1590">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="887e6-1590">fx_file_write</span></span>
- <span data-ttu-id="887e6-1591">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1591">fx_file_write_notify_set</span></span>
- <span data-ttu-id="887e6-1592">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1592">fx_unicode_file_create</span></span>
- <span data-ttu-id="887e6-1593">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1593">fx_unicode_file_rename</span></span>
- <span data-ttu-id="887e6-1594">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1594">fx_unicode_name_get</span></span>
- <span data-ttu-id="887e6-1595">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1595">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_allocate"></a><span data-ttu-id="887e6-1596">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1596">fx_file_extended_allocate</span></span>

<span data-ttu-id="887e6-1597">Выделяет место для файла</span><span class="sxs-lookup"><span data-stu-id="887e6-1597">Allocates space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-1598">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-1598">Prototype</span></span>

```c
UINT fx_file_extended_allocate(
    FX_FILE *file_ptr, 
    ULONG64 size);
```
### <a name="description"></a><span data-ttu-id="887e6-1599">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-1599">Description</span></span>

<span data-ttu-id="887e6-1600">Эта служба выделяет один кластер или несколько последовательных и связывает их с концом указанного файла.</span><span class="sxs-lookup"><span data-stu-id="887e6-1600">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="887e6-1601">FileX определяет количество кластеров, необходимое для деления запрошенного размера на число байтов на кластер.</span><span class="sxs-lookup"><span data-stu-id="887e6-1601">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="887e6-1602">Затем результат округляется до следующего целого кластера.</span><span class="sxs-lookup"><span data-stu-id="887e6-1602">The result is then rounded up to the next whole cluster.</span></span>

<span data-ttu-id="887e6-1603">Эта служба разработана для exFAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-1603">This service is designed for exFAT.</span></span> <span data-ttu-id="887e6-1604">Параметр *size* принимает значение 64-разрядного целого числа, которое позволяет вызывающему объекту предварительно выделить пространство свыше 4 ГБ.</span><span class="sxs-lookup"><span data-stu-id="887e6-1604">The *size* parameter takes a 64-bit integer value, which allows the caller to pre-allocate space beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-1605">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-1605">Input Parameters</span></span>

- <span data-ttu-id="887e6-1606">**file_ptr**: указатель на открытый ранее файл</span><span class="sxs-lookup"><span data-stu-id="887e6-1606">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="887e6-1607">**size**: число байтов, выделяемых для файла</span><span class="sxs-lookup"><span data-stu-id="887e6-1607">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-1608">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-1608">Return Values</span></span>

- <span data-ttu-id="887e6-1609">**FX_SUCCESS** (0x00) — файл успешно выделен.</span><span class="sxs-lookup"><span data-stu-id="887e6-1609">**FX_SUCCESS** (0x00) Successful file allocation.</span></span>
- <span data-ttu-id="887e6-1610">**FX_ACCESS_ERROR** (0x06) — указанный файл не открыт для записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-1610">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="887e6-1611">**FX_NOT_OPEN** (0x07) — указанный файл в настоящее время не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-1611">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="887e6-1612">**FX_NO_MORE_SPACE** (0x0A) — на носителе, связанном с этим файлом, недостаточно доступных кластеров.</span><span class="sxs-lookup"><span data-stu-id="887e6-1612">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="887e6-1613">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-1613">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="887e6-1614">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-1614">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="887e6-1615">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-1615">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="887e6-1616">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-1616">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="887e6-1617">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-1617">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-1618">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-1618">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="887e6-1619">**FX_PTR_ERROR** (0x18) — недопустимый указатель на файл.</span><span class="sxs-lookup"><span data-stu-id="887e6-1619">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="887e6-1620">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-1620">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-1621">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-1621">Allowed From</span></span>

<span data-ttu-id="887e6-1622">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-1622">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-1623">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-1623">Example</span></span>

```c

FX_FILE            my_file;
UINT            status;
/* Allocate 0x100000000 bytes to the end of my_file. */

status = fx_file_extended_allocate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS the file now has
    one or more contiguous cluster(s) that can accommodate at least
    1024 bytes of user data. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-1624">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-1624">See Also</span></span>

- <span data-ttu-id="887e6-1625">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1625">fx_file_allocate</span></span>
- <span data-ttu-id="887e6-1626">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1626">fx_file_attributes_read</span></span>
- <span data-ttu-id="887e6-1627">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1627">fx_file_attributes_set</span></span>
- <span data-ttu-id="887e6-1628">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1628">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-1629">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="887e6-1629">fx_file_close</span></span>
- <span data-ttu-id="887e6-1630">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1630">fx_file_create</span></span>
- <span data-ttu-id="887e6-1631">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1631">fx_file_date_time_set</span></span>
- <span data-ttu-id="887e6-1632">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-1632">fx_file_delete</span></span>
- <span data-ttu-id="887e6-1633">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1633">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-1634">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1634">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="887e6-1635">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1635">fx_file_extended_seek</span></span>
- <span data-ttu-id="887e6-1636">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-1636">fx_file_extended_truncate</span></span>
- <span data-ttu-id="887e6-1637">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-1637">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="887e6-1638">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="887e6-1638">fx_file_open</span></span>
- <span data-ttu-id="887e6-1639">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1639">fx_file_read</span></span>
- <span data-ttu-id="887e6-1640">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1640">fx_file_relative_seek</span></span>
- <span data-ttu-id="887e6-1641">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1641">fx_file_rename</span></span>
- <span data-ttu-id="887e6-1642">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1642">fx_file_seek</span></span>
- <span data-ttu-id="887e6-1643">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-1643">fx_file_truncate</span></span>
- <span data-ttu-id="887e6-1644">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-1644">fx_file_truncate_release</span></span>
- <span data-ttu-id="887e6-1645">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="887e6-1645">fx_file_write</span></span>
- <span data-ttu-id="887e6-1646">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1646">fx_file_write_notify_set</span></span>
- <span data-ttu-id="887e6-1647">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1647">fx_unicode_file_create</span></span>
- <span data-ttu-id="887e6-1648">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1648">fx_unicode_file_rename</span></span>
- <span data-ttu-id="887e6-1649">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1649">fx_unicode_name_get</span></span>
- <span data-ttu-id="887e6-1650">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1650">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_best_effort_allocate"></a><span data-ttu-id="887e6-1651">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1651">fx_file_extended_best_effort_allocate</span></span>

<span data-ttu-id="887e6-1652">Наиболее оптимальное выделение пространства для файла</span><span class="sxs-lookup"><span data-stu-id="887e6-1652">Best effort to allocate space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-1653">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-1653">Prototype</span></span>

```c
UINT fx_file_extended best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG64 size,
    ULONG64 *actual_size_allocated);
```
### <a name="description"></a><span data-ttu-id="887e6-1654">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-1654">Description</span></span>

<span data-ttu-id="887e6-1655">Эта служба выделяет один кластер или несколько последовательных и связывает их с концом указанного файла.</span><span class="sxs-lookup"><span data-stu-id="887e6-1655">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="887e6-1656">FileX определяет количество кластеров, необходимое для деления запрошенного размера на число байтов на кластер.</span><span class="sxs-lookup"><span data-stu-id="887e6-1656">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="887e6-1657">Затем результат округляется до следующего целого кластера.</span><span class="sxs-lookup"><span data-stu-id="887e6-1657">The result is then rounded up to the next whole cluster.</span></span> <span data-ttu-id="887e6-1658">Если на носителе нет достаточного количества последовательных кластеров, эта служба связывает с файлом самый большой доступный блок последовательных кластеров.</span><span class="sxs-lookup"><span data-stu-id="887e6-1658">If there are not enough consecutive clusters available in the media, this service links the largest available block of consecutive clusters to the file.</span></span> <span data-ttu-id="887e6-1659">Объем пространства, фактически выделяемый файлу, возвращается вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="887e6-1659">The amount of space actually allocated to the file is returned to the caller.</span></span>

<span data-ttu-id="887e6-1660">Эта служба разработана для exFAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-1660">This service is designed for exFAT.</span></span> <span data-ttu-id="887e6-1661">Параметр *size* принимает значение 64-разрядного целого числа, которое позволяет вызывающему объекту предварительно выделить пространство свыше 4 ГБ.</span><span class="sxs-lookup"><span data-stu-id="887e6-1661">The *size* parameter takes a 64-bit integer value, which allows the caller to pre-allocate space beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-1662">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-1662">Input Parameters</span></span>

- <span data-ttu-id="887e6-1663">**file_ptr**: указатель на открытый ранее файл</span><span class="sxs-lookup"><span data-stu-id="887e6-1663">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="887e6-1664">**size**: число байтов, выделяемых для файла</span><span class="sxs-lookup"><span data-stu-id="887e6-1664">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-1665">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-1665">Return Values</span></span>

- <span data-ttu-id="887e6-1666">**FX_SUCCESS** (0x00) — файл успешно выделен.</span><span class="sxs-lookup"><span data-stu-id="887e6-1666">**FX_SUCCESS** (0x00) Successful file allocation.</span></span>
- <span data-ttu-id="887e6-1667">**FX_ACCESS_ERROR** (0x06) — указанный файл не открыт для записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-1667">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="887e6-1668">**FX_NOT_OPEN** (0x07) — указанный файл в настоящее время не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-1668">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="887e6-1669">**FX_NO_MORE_SPACE** (0x0A) — на носителе, связанном с этим файлом, недостаточно доступных кластеров.</span><span class="sxs-lookup"><span data-stu-id="887e6-1669">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="887e6-1670">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-1670">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="887e6-1671">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-1671">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="887e6-1672">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-1672">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="887e6-1673">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-1673">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="887e6-1674">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-1674">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-1675">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-1675">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="887e6-1676">**FX_PTR_ERROR** (0x18) — недопустимый указатель на файл.</span><span class="sxs-lookup"><span data-stu-id="887e6-1676">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="887e6-1677">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-1677">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-1678">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-1678">Allowed From</span></span>

<span data-ttu-id="887e6-1679">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-1679">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-1680">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-1680">Example</span></span>

```c

FX_FILE my_file;
UINT             status;
ULONG64         actual_allocation;

/* Attempt to allocate 0x100000000 bytes to the end of my_file. */

status = fx_file_extended_best_effort_allocate(&my_file,
    0x100000000, &actual_allocation);

/* If status equals FX_SUCCESS, the number of bytes
    allocated to the file is found in actual_allocation. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-1681">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-1681">See Also</span></span>

- <span data-ttu-id="887e6-1682">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1682">fx_file_allocate</span></span>
- <span data-ttu-id="887e6-1683">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1683">fx_file_attributes_read</span></span>
- <span data-ttu-id="887e6-1684">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1684">fx_file_attributes_set</span></span>
- <span data-ttu-id="887e6-1685">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1685">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-1686">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="887e6-1686">fx_file_close</span></span>
- <span data-ttu-id="887e6-1687">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1687">fx_file_create</span></span>
- <span data-ttu-id="887e6-1688">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1688">fx_file_date_time_set</span></span>
- <span data-ttu-id="887e6-1689">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-1689">fx_file_delete</span></span>
- <span data-ttu-id="887e6-1690">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1690">fx_file_extended_allocate</span></span>
- <span data-ttu-id="887e6-1691">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1691">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="887e6-1692">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1692">fx_file_extended_seek</span></span>
- <span data-ttu-id="887e6-1693">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-1693">fx_file_extended_truncate</span></span>
- <span data-ttu-id="887e6-1694">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-1694">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="887e6-1695">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="887e6-1695">fx_file_open</span></span>
- <span data-ttu-id="887e6-1696">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1696">fx_file_read</span></span>
- <span data-ttu-id="887e6-1697">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1697">fx_file_relative_seek</span></span>
- <span data-ttu-id="887e6-1698">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1698">fx_file_rename</span></span>
- <span data-ttu-id="887e6-1699">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1699">fx_file_seek</span></span>
- <span data-ttu-id="887e6-1700">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-1700">fx_file_truncate</span></span>
- <span data-ttu-id="887e6-1701">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-1701">fx_file_truncate_release</span></span>
- <span data-ttu-id="887e6-1702">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="887e6-1702">fx_file_write</span></span>
- <span data-ttu-id="887e6-1703">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1703">fx_file_write_notify_set</span></span>
- <span data-ttu-id="887e6-1704">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1704">fx_unicode_file_create</span></span>
- <span data-ttu-id="887e6-1705">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1705">fx_unicode_file_rename</span></span>
- <span data-ttu-id="887e6-1706">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1706">fx_unicode_name_get</span></span>
- <span data-ttu-id="887e6-1707">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1707">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_relative_seek"></a><span data-ttu-id="887e6-1708">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1708">fx_file_extended_relative_seek</span></span>

<span data-ttu-id="887e6-1709">Размещение на указанное относительное смещение в байтах</span><span class="sxs-lookup"><span data-stu-id="887e6-1709">Positions to a relative byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-1710">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-1710">Prototype</span></span>

```c
UINT fx_file_extended_relative_seek(
    FX_FILE *file_ptr,
    ULONG64 byte_offset,
    UINT seek_from);
```
### <a name="description"></a><span data-ttu-id="887e6-1711">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-1711">Description</span></span>

<span data-ttu-id="887e6-1712">Эта служба размещает внутренний указатель чтения/записи файла на указанное относительное смещение в байтах.</span><span class="sxs-lookup"><span data-stu-id="887e6-1712">This service positions the internal file read/write pointer to the specified relative byte offset.</span></span> <span data-ttu-id="887e6-1713">Все последующие запросы на чтение или запись файла будут начинаться с этого места в файле.</span><span class="sxs-lookup"><span data-stu-id="887e6-1713">Any subsequent file read or write request will begin at this location in the file.</span></span>

<span data-ttu-id="887e6-1714">Эта служба разработана для exFAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-1714">This service is designed for exFAT.</span></span> <span data-ttu-id="887e6-1715">Параметр *byte_offset* принимает 64-разрядное целочисленное значение, которое позволяет вызывающему объекту изменить расположение указателя чтения/записи за пределами 4 ГБ.</span><span class="sxs-lookup"><span data-stu-id="887e6-1715">The *byte_offset* parameter takes a 64bit integer value, which allows the caller to reposition the read/write pointer beyond 4GB range.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="887e6-1716">*Если операция поиска пытается выполнить поиск после конца файла, указатель на чтение и запись файла помещается в конец файла. И наоборот, если операция поиска пытается установить положение после начала файла, указатель на чтение и запись файла помещается в начало файла.*</span><span class="sxs-lookup"><span data-stu-id="887e6-1716">*If the seek operation attempts to seek past the end of the file, the file's read/write pointer is positioned to the end of the file. Conversely, if the seek operation attempts to position past the beginning of the file, the file's read/write pointer is positioned to the beginning of the file.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-1717">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-1717">Input Parameters</span></span>

- <span data-ttu-id="887e6-1718">**file_ptr**: указатель на открытый ранее файл</span><span class="sxs-lookup"><span data-stu-id="887e6-1718">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="887e6-1719">**byte_offset**: требуемое относительное смещение в байтах в файле</span><span class="sxs-lookup"><span data-stu-id="887e6-1719">**byte_offset**: Desired relative byte offset in file.</span></span>
- <span data-ttu-id="887e6-1720">**seek_from**: направление и расположение для выполнения относительного поиска</span><span class="sxs-lookup"><span data-stu-id="887e6-1720">**seek_from**: The direction and location of where to perform the relative seek from.</span></span> <span data-ttu-id="887e6-1721">Допустимые параметры чтения определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="887e6-1721">Valid seek options are defined as follows:</span></span>
  - <span data-ttu-id="887e6-1722">FX_SEEK_BEGIN (0x00)</span><span class="sxs-lookup"><span data-stu-id="887e6-1722">FX_SEEK_BEGIN (0x00)</span></span>
  - <span data-ttu-id="887e6-1723">FX_SEEK_END (0x01)</span><span class="sxs-lookup"><span data-stu-id="887e6-1723">FX_SEEK_END (0x01)</span></span>
  - <span data-ttu-id="887e6-1724">FX_SEEK_FORWARD (0x02)</span><span class="sxs-lookup"><span data-stu-id="887e6-1724">FX_SEEK_FORWARD (0x02)</span></span>
  - <span data-ttu-id="887e6-1725">FX_SEEK_BACK (0x03). Если указан параметр FX_SEEK_BEGIN, операция поиска выполняется с начала файла.</span><span class="sxs-lookup"><span data-stu-id="887e6-1725">FX_SEEK_BACK (0x03) If FX_SEEK_BEGIN is specified, the seek operation is performed from the beginning of the file.</span></span> <span data-ttu-id="887e6-1726">Если указан параметр FX_SEEK_END, операция поиска выполняется в обратном направлении с конца файла.</span><span class="sxs-lookup"><span data-stu-id="887e6-1726">If FX_SEEK_END is specified the seek operation is performed backward from the end of the file.</span></span> <span data-ttu-id="887e6-1727">Если указан параметр FX_SEEK_FORWARD, операция поиска выполняется вперед от текущего расположения файла.</span><span class="sxs-lookup"><span data-stu-id="887e6-1727">If FX_SEEK_FORWARD is specified, the seek operation is performed forward from the current file position.</span></span> <span data-ttu-id="887e6-1728">Если указан параметр FX_SEEK_BACK, операция поиска выполняется в обратном направлении от текущей позиции файла.</span><span class="sxs-lookup"><span data-stu-id="887e6-1728">If FX_SEEK_BACK is specified, the seek operation is performed backward from the current file position.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-1729">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-1729">Return Values</span></span>

- <span data-ttu-id="887e6-1730">**FX_SUCCESS** (0x00) — относительный поиск файла успешно выполнен.</span><span class="sxs-lookup"><span data-stu-id="887e6-1730">**FX_SUCCESS** (0x00) Successful file relative seek.</span></span>
- <span data-ttu-id="887e6-1731">**FX_NOT_OPEN** (0x07) — указанный файл в настоящее время не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-1731">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="887e6-1732">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-1732">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="887e6-1733">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-1733">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="887e6-1734">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="887e6-1734">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="887e6-1735">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-1735">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-1736">**FX_PTR_ERROR** (0x18) — недопустимый указатель на файл.</span><span class="sxs-lookup"><span data-stu-id="887e6-1736">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="887e6-1737">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-1737">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-1738">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-1738">Allowed From</span></span>

<span data-ttu-id="887e6-1739">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-1739">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-1740">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-1740">Example</span></span>

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to seek forward 0x100000000 bytes in "my_file". */

status = fx_file_extended_relative_seek(&my_file, 0x100000000, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write
    pointers are positioned 0x100000000 bytes forward. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-1741">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-1741">See Also</span></span>

- <span data-ttu-id="887e6-1742">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1742">fx_file_allocate</span></span>
- <span data-ttu-id="887e6-1743">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1743">fx_file_attributes_read</span></span>
- <span data-ttu-id="887e6-1744">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1744">fx_file_attributes_set</span></span>
- <span data-ttu-id="887e6-1745">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1745">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-1746">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="887e6-1746">fx_file_close</span></span>
- <span data-ttu-id="887e6-1747">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1747">fx_file_create</span></span>
- <span data-ttu-id="887e6-1748">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1748">fx_file_date_time_set</span></span>
- <span data-ttu-id="887e6-1749">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-1749">fx_file_delete</span></span>
- <span data-ttu-id="887e6-1750">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1750">fx_file_extended_allocate</span></span>
- <span data-ttu-id="887e6-1751">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1751">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-1752">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1752">fx_file_extended_seek</span></span>
- <span data-ttu-id="887e6-1753">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-1753">fx_file_extended_truncate</span></span>
- <span data-ttu-id="887e6-1754">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-1754">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="887e6-1755">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="887e6-1755">fx_file_open</span></span>
- <span data-ttu-id="887e6-1756">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1756">fx_file_read</span></span>
- <span data-ttu-id="887e6-1757">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1757">fx_file_relative_seek</span></span>
- <span data-ttu-id="887e6-1758">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1758">fx_file_rename</span></span>
- <span data-ttu-id="887e6-1759">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1759">fx_file_seek</span></span>
- <span data-ttu-id="887e6-1760">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-1760">fx_file_truncate</span></span>
- <span data-ttu-id="887e6-1761">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-1761">fx_file_truncate_release</span></span>
- <span data-ttu-id="887e6-1762">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="887e6-1762">fx_file_write</span></span>
- <span data-ttu-id="887e6-1763">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1763">fx_file_write_notify_set</span></span>
- <span data-ttu-id="887e6-1764">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1764">fx_unicode_file_create</span></span>
- <span data-ttu-id="887e6-1765">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1765">fx_unicode_file_rename</span></span>
- <span data-ttu-id="887e6-1766">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1766">fx_unicode_name_get</span></span>
- <span data-ttu-id="887e6-1767">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1767">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_seek"></a><span data-ttu-id="887e6-1768">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1768">fx_file_extended_seek</span></span>

<span data-ttu-id="887e6-1769">Размещение на указанное смещение в байтах</span><span class="sxs-lookup"><span data-stu-id="887e6-1769">Positions to byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-1770">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-1770">Prototype</span></span>

```c
UINT fx_file_extended_seek(
    FX_FILE *file_ptr, 
    ULONG64 byte_offset);
```
### <a name="description"></a><span data-ttu-id="887e6-1771">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-1771">Description</span></span>

<span data-ttu-id="887e6-1772">Эта служба размещает внутренний указатель чтения/записи файла на указанное смещение в байтах.</span><span class="sxs-lookup"><span data-stu-id="887e6-1772">This service positions the internal file read/write pointer to the specified byte offset.</span></span> <span data-ttu-id="887e6-1773">Все последующие запросы на чтение или запись файла будут начинаться с этого места в файле.</span><span class="sxs-lookup"><span data-stu-id="887e6-1773">Any subsequent file read or write request will begin at this location in the file.</span></span>

<span data-ttu-id="887e6-1774">Эта служба разработана для exFAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-1774">This service is designed for exFAT.</span></span> <span data-ttu-id="887e6-1775">Параметр *byte_offset* принимает 64-разрядное целочисленное значение, которое позволяет вызывающему объекту изменить расположение указателя чтения/записи за пределами 4 ГБ.</span><span class="sxs-lookup"><span data-stu-id="887e6-1775">The *byte_offset* parameter takes a 64bit integer value, which allows the caller to reposition the read/write pointer beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-1776">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-1776">Input Parameters</span></span>

- <span data-ttu-id="887e6-1777">**file_ptr**: указатель на блок управления файлом</span><span class="sxs-lookup"><span data-stu-id="887e6-1777">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="887e6-1778">**byte_offset**: требуемое смещение в байтах в файле</span><span class="sxs-lookup"><span data-stu-id="887e6-1778">**byte_offset**: Desired byte offset in file.</span></span> <span data-ttu-id="887e6-1779">При нулевом значении указатель чтения/записи будет размещен в начале файла, а при значении, превышающем размер файла, указатель чтения/записи будет помещен в конец файла.</span><span class="sxs-lookup"><span data-stu-id="887e6-1779">A value of zero will position the read/write pointer at the beginning of the file, while a value greater than the file's size will position the read/write pointer at the end of the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-1780">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-1780">Return Values</span></span>

- <span data-ttu-id="887e6-1781">**FX_SUCCESS** (0x00) — файл успешно найден.</span><span class="sxs-lookup"><span data-stu-id="887e6-1781">**FX_SUCCESS** (0x00) Successful file seek.</span></span>
- <span data-ttu-id="887e6-1782">**FX_NOT_OPEN** (0x07) — указанный файл не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-1782">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="887e6-1783">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-1783">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="887e6-1784">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-1784">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="887e6-1785">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="887e6-1785">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="887e6-1786">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-1786">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-1787">**FX_PTR_ERROR** (0x18) — недопустимый указатель на файл.</span><span class="sxs-lookup"><span data-stu-id="887e6-1787">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="887e6-1788">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-1788">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-1789">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-1789">Allowed From</span></span>

<span data-ttu-id="887e6-1790">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-1790">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-1791">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-1791">Example</span></span>

```c
FX_FILE         my_file;
UINT             status;
/* Seek to position 0x100000000 of "my_file." */

status = fx_file_extended_seek(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned 0x100000000 bytes from the beginning of the file. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-1792">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-1792">See Also</span></span>

- <span data-ttu-id="887e6-1793">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1793">fx_file_allocate</span></span>
- <span data-ttu-id="887e6-1794">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1794">fx_file_attributes_read</span></span>
- <span data-ttu-id="887e6-1795">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1795">fx_file_attributes_set</span></span>
- <span data-ttu-id="887e6-1796">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1796">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-1797">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="887e6-1797">fx_file_close</span></span>
- <span data-ttu-id="887e6-1798">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1798">fx_file_create</span></span>
- <span data-ttu-id="887e6-1799">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1799">fx_file_date_time_set</span></span>
- <span data-ttu-id="887e6-1800">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-1800">fx_file_delete</span></span>
- <span data-ttu-id="887e6-1801">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1801">fx_file_extended_allocate</span></span>
- <span data-ttu-id="887e6-1802">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1802">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-1803">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1803">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="887e6-1804">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-1804">fx_file_extended_truncate</span></span>
- <span data-ttu-id="887e6-1805">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-1805">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="887e6-1806">fx_file_open- fx_file_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1806">fx_file_open- fx_file_read</span></span>
- <span data-ttu-id="887e6-1807">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1807">fx_file_relative_seek</span></span>
- <span data-ttu-id="887e6-1808">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1808">fx_file_rename</span></span>
- <span data-ttu-id="887e6-1809">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1809">fx_file_seek</span></span>
- <span data-ttu-id="887e6-1810">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-1810">fx_file_truncate</span></span>
- <span data-ttu-id="887e6-1811">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-1811">fx_file_truncate_release</span></span>
- <span data-ttu-id="887e6-1812">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="887e6-1812">fx_file_write</span></span>
- <span data-ttu-id="887e6-1813">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1813">fx_file_write_notify_set</span></span>
- <span data-ttu-id="887e6-1814">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1814">fx_unicode_file_create</span></span>
- <span data-ttu-id="887e6-1815">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1815">fx_unicode_file_rename</span></span>
- <span data-ttu-id="887e6-1816">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1816">fx_unicode_name_get</span></span>
- <span data-ttu-id="887e6-1817">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1817">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_truncate"></a><span data-ttu-id="887e6-1818">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-1818">fx_file_extended_truncate</span></span>

<span data-ttu-id="887e6-1819">Усекает файл</span><span class="sxs-lookup"><span data-stu-id="887e6-1819">Truncates file</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-1820">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-1820">Prototype</span></span>

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG64 size);
```
### <a name="description"></a><span data-ttu-id="887e6-1821">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-1821">Description</span></span>

<span data-ttu-id="887e6-1822">Эта служба усекает размер файла до указанного.</span><span class="sxs-lookup"><span data-stu-id="887e6-1822">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="887e6-1823">Если указанный размер превышает фактический размер файла, эта служба не выполняет никаких действий.</span><span class="sxs-lookup"><span data-stu-id="887e6-1823">If the supplied size is greater than the actual file size, this service doesn't do anything.</span></span> <span data-ttu-id="887e6-1824">Ни один из кластеров носителя, связанных с файлом, не освобождается.</span><span class="sxs-lookup"><span data-stu-id="887e6-1824">None of the media clusters associated with the file are released.</span></span>

> [!WARNING]
> <span data-ttu-id="887e6-1825">*Проявляйте осторожность при усечении файлов, которые также могут быть открыты для одновременного чтения. Усечение файла, открытого для чтения, может привести к чтению недопустимых данных.*</span><span class="sxs-lookup"><span data-stu-id="887e6-1825">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="887e6-1826">Эта служба разработана для exFAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-1826">This service is designed for exFAT.</span></span> <span data-ttu-id="887e6-1827">Параметр *size* принимает значение 64-разрядного целого числа, которое позволяет вызывающему объекту действовать за пределами 4 ГБ.</span><span class="sxs-lookup"><span data-stu-id="887e6-1827">The *size* parameter takes a 64-bit integer value, which allows the caller to operate beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-1828">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-1828">Input Parameters</span></span>

- <span data-ttu-id="887e6-1829">**file_ptr**: указатель на блок управления файлом</span><span class="sxs-lookup"><span data-stu-id="887e6-1829">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="887e6-1830">**size**: новый размер файла</span><span class="sxs-lookup"><span data-stu-id="887e6-1830">**size**: New file size.</span></span> <span data-ttu-id="887e6-1831">Число байтов после нового размера файла не учитывается.</span><span class="sxs-lookup"><span data-stu-id="887e6-1831">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-1832">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-1832">Return Values</span></span>

- <span data-ttu-id="887e6-1833">**FX_SUCCESS** (0x00) — файл успешно усечен.</span><span class="sxs-lookup"><span data-stu-id="887e6-1833">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="887e6-1834">**FX_NOT_OPEN** (0x07) — указанный файл не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-1834">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="887e6-1835">**FX_ACCESS_ERROR** (0x06) — указанный файл не открыт для записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-1835">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="887e6-1836">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-1836">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="887e6-1837">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-1837">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="887e6-1838">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-1838">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="887e6-1839">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="887e6-1839">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="887e6-1840">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-1840">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-1841">**FX_WRITE_PROTECT** (0x23) — носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-1841">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="887e6-1842">**FX_PTR_ERROR** (0x18) — недопустимый указатель на файл.</span><span class="sxs-lookup"><span data-stu-id="887e6-1842">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="887e6-1843">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-1843">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-1844">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-1844">Allowed From</span></span>

<span data-ttu-id="887e6-1845">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-1845">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-1846">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-1846">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Truncate "my_file" to 0x100000000 bytes. */

status = fx_file_extended_truncate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, "my_file" contains 0x100000000 or fewer bytes. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-1847">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-1847">See Also</span></span>

- <span data-ttu-id="887e6-1848">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1848">fx_file_allocate</span></span>
- <span data-ttu-id="887e6-1849">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1849">fx_file_attributes_read</span></span>
- <span data-ttu-id="887e6-1850">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1850">fx_file_attributes_set</span></span>
- <span data-ttu-id="887e6-1851">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1851">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-1852">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="887e6-1852">fx_file_close</span></span>
- <span data-ttu-id="887e6-1853">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1853">fx_file_create</span></span>
- <span data-ttu-id="887e6-1854">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1854">fx_file_date_time_set</span></span>
- <span data-ttu-id="887e6-1855">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-1855">fx_file_delete</span></span>
- <span data-ttu-id="887e6-1856">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1856">fx_file_extended_allocate</span></span>
- <span data-ttu-id="887e6-1857">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1857">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-1858">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1858">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="887e6-1859">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1859">fx_file_extended_seek</span></span>
- <span data-ttu-id="887e6-1860">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-1860">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="887e6-1861">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="887e6-1861">fx_file_open</span></span>
- <span data-ttu-id="887e6-1862">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1862">fx_file_read</span></span>
- <span data-ttu-id="887e6-1863">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1863">fx_file_relative_seek</span></span>
- <span data-ttu-id="887e6-1864">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1864">fx_file_rename</span></span>
- <span data-ttu-id="887e6-1865">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1865">fx_file_seek</span></span>
- <span data-ttu-id="887e6-1866">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-1866">fx_file_truncate</span></span>
- <span data-ttu-id="887e6-1867">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-1867">fx_file_truncate_release</span></span>
- <span data-ttu-id="887e6-1868">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="887e6-1868">fx_file_write</span></span>
- <span data-ttu-id="887e6-1869">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1869">fx_file_write_notify_set</span></span>
- <span data-ttu-id="887e6-1870">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1870">fx_unicode_file_create</span></span>
- <span data-ttu-id="887e6-1871">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1871">fx_unicode_file_rename</span></span>
- <span data-ttu-id="887e6-1872">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1872">fx_unicode_name_get</span></span>
- <span data-ttu-id="887e6-1873">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1873">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_truncate_release"></a><span data-ttu-id="887e6-1874">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-1874">fx_file_extended_truncate_release</span></span>

<span data-ttu-id="887e6-1875">Усекает кластеры файлов и выпусков</span><span class="sxs-lookup"><span data-stu-id="887e6-1875">Truncates file and releases cluster(s)</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-1876">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-1876">Prototype</span></span>

```c
UINT fx_file_extended_truncate_release(
    FX_FILE *file_ptr, 
    ULONG64 size);
```

### <a name="description"></a><span data-ttu-id="887e6-1877">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-1877">Description</span></span>

<span data-ttu-id="887e6-1878">Эта служба усекает размер файла до указанного.</span><span class="sxs-lookup"><span data-stu-id="887e6-1878">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="887e6-1879">Если указанный размер превышает фактический размер файла, эта служба не выполняет никаких действий.</span><span class="sxs-lookup"><span data-stu-id="887e6-1879">If the supplied size is greater than the actual file size, this service does not do anything.</span></span> <span data-ttu-id="887e6-1880">В отличие от службы ***fx_file_extended_truncate*** эта служба освобождает неиспользуемые кластеры.</span><span class="sxs-lookup"><span data-stu-id="887e6-1880">Unlike the ***fx_file_extended_truncate*** service, this service does release any unused clusters.</span></span>

> [!WARNING]
> <span data-ttu-id="887e6-1881">*Проявляйте осторожность при усечении файлов, которые также могут быть открыты для одновременного чтения. Усечение файла, открытого для чтения, может привести к чтению недопустимых данных.*</span><span class="sxs-lookup"><span data-stu-id="887e6-1881">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="887e6-1882">Эта служба разработана для exFAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-1882">This service is designed for exFAT.</span></span> <span data-ttu-id="887e6-1883">Параметр *size* принимает значение 64-разрядного целого числа, которое позволяет вызывающему объекту действовать за пределами 4 ГБ.</span><span class="sxs-lookup"><span data-stu-id="887e6-1883">The *size* parameter takes a 64-bit integer value, which allows the caller to operate beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-1884">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-1884">Input Parameters</span></span>

- <span data-ttu-id="887e6-1885">**file_ptr**: указатель на открытый ранее файл</span><span class="sxs-lookup"><span data-stu-id="887e6-1885">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="887e6-1886">**size**: новый размер файла</span><span class="sxs-lookup"><span data-stu-id="887e6-1886">**size**: New file size.</span></span> <span data-ttu-id="887e6-1887">Число байтов после нового размера файла не учитывается.</span><span class="sxs-lookup"><span data-stu-id="887e6-1887">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-1888">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-1888">Return Values</span></span>

- <span data-ttu-id="887e6-1889">**FX_SUCCESS** (0x00) — файл успешно усечен.</span><span class="sxs-lookup"><span data-stu-id="887e6-1889">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="887e6-1890">**FX_ACCESS_ERROR** (0x06) — указанный файл не открыт для записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-1890">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="887e6-1891">**FX_NOT_OPEN** (0x07) — указанный файл в настоящее время не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-1891">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="887e6-1892">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-1892">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="887e6-1893">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-1893">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="887e6-1894">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-1894">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="887e6-1895">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-1895">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="887e6-1896">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="887e6-1896">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="887e6-1897">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-1897">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-1898">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-1898">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="887e6-1899">**FX_PTR_ERROR** (0x18) — недопустимый указатель на файл.</span><span class="sxs-lookup"><span data-stu-id="887e6-1899">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="887e6-1900">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-1900">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-1901">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-1901">Allowed From</span></span>

<span data-ttu-id="887e6-1902">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-1902">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-1903">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-1903">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Attempt to truncate everything after the first 0x100000000 bytes of "my_file". */

status = fx_file_extended_truncate_release(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file is now 0x100000000
    bytes or fewer and all unused clusters have been released. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-1904">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-1904">See Also</span></span>

- <span data-ttu-id="887e6-1905">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1905">fx_file_allocate</span></span>
- <span data-ttu-id="887e6-1906">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1906">fx_file_attributes_read</span></span>
- <span data-ttu-id="887e6-1907">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1907">fx_file_attributes_set</span></span>
- <span data-ttu-id="887e6-1908">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1908">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-1909">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="887e6-1909">fx_file_close</span></span>
- <span data-ttu-id="887e6-1910">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1910">fx_file_create</span></span>
- <span data-ttu-id="887e6-1911">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1911">fx_file_date_time_set</span></span>
- <span data-ttu-id="887e6-1912">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-1912">fx_file_delete</span></span>
- <span data-ttu-id="887e6-1913">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1913">fx_file_extended_allocate</span></span>
- <span data-ttu-id="887e6-1914">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1914">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-1915">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1915">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="887e6-1916">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1916">fx_file_extended_seek</span></span>
- <span data-ttu-id="887e6-1917">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-1917">fx_file_extended_truncate</span></span>
- <span data-ttu-id="887e6-1918">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="887e6-1918">fx_file_open</span></span>
- <span data-ttu-id="887e6-1919">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1919">fx_file_read</span></span>
- <span data-ttu-id="887e6-1920">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1920">fx_file_relative_seek</span></span>
- <span data-ttu-id="887e6-1921">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1921">fx_file_rename</span></span>
- <span data-ttu-id="887e6-1922">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1922">fx_file_seek</span></span>
- <span data-ttu-id="887e6-1923">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-1923">fx_file_truncate</span></span>
- <span data-ttu-id="887e6-1924">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-1924">fx_file_truncate_release</span></span>
- <span data-ttu-id="887e6-1925">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="887e6-1925">fx_file_write</span></span>
- <span data-ttu-id="887e6-1926">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1926">fx_file_write_notify_set</span></span>
- <span data-ttu-id="887e6-1927">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1927">fx_unicode_file_create</span></span>
- <span data-ttu-id="887e6-1928">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1928">fx_unicode_file_rename</span></span>
- <span data-ttu-id="887e6-1929">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1929">fx_unicode_name_get</span></span>
- <span data-ttu-id="887e6-1930">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1930">fx_unicode_short_name_get</span></span>

## <a name="fx_file_open"></a><span data-ttu-id="887e6-1931">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="887e6-1931">fx_file_open</span></span>

<span data-ttu-id="887e6-1932">Открывает файл</span><span class="sxs-lookup"><span data-stu-id="887e6-1932">Opens file</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-1933">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-1933">Prototype</span></span>

```c
UINT fx_file_open(
    FX_MEDIA *media_ptr,
    FX_FILE *file_ptr,
    CHAR *file_name,
    UINT open_type);
```
### <a name="description"></a><span data-ttu-id="887e6-1934">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-1934">Description</span></span>

<span data-ttu-id="887e6-1935">Эта служба открывает указанный файл для чтения или записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-1935">This service opens the specified file for either reading or writing.</span></span> <span data-ttu-id="887e6-1936">Файл может быть открыт для чтения несколько раз, однако открыть файл для записи можно только один раз, пока модуль записи не закроет файл.</span><span class="sxs-lookup"><span data-stu-id="887e6-1936">A file may be opened for reading multiple times, while a file can only be opened for writing once until the writer closes the file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="887e6-1937">*Необходимо соблюдать осторожность, если файл параллельно открыт для чтения и записи. Запись файла, выполняемая при одновременном открытии файла для чтения, может не отображаться средством чтения, если только средство чтения не закроет и не откроет файл для чтения. Аналогично, при использовании служб усечения файлов следует соблюдать осторожность. Если файл усекается модулем записи, читатели одного и того же файла могут вернуть недопустимые данные.*</span><span class="sxs-lookup"><span data-stu-id="887e6-1937">*Care must be taken if a file is concurrently open for reading and writing. File writing performed when a file is simultaneously opened for reading may not be seen by the reader, unless the reader closes and reopens the file for reading. Similarly, the file writer should be careful when using file truncate services. If a file is truncated by the writer, readers of the same file could return invalid data.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-1938">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-1938">Input Parameters</span></span>

- <span data-ttu-id="887e6-1939">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-1939">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="887e6-1940">**file_ptr**: указатель на блок управления файлом</span><span class="sxs-lookup"><span data-stu-id="887e6-1940">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="887e6-1941">**file_name**: указатель на имя открываемого файла (путь к каталогу является необязательным)</span><span class="sxs-lookup"><span data-stu-id="887e6-1941">**file_name**: Pointer to the name of the file to open (directory path is optional).</span></span>
- <span data-ttu-id="887e6-1942">**open_type**: тип открываемого файла</span><span class="sxs-lookup"><span data-stu-id="887e6-1942">**open_type**: Type of file open.</span></span> <span data-ttu-id="887e6-1943">Допустимые параметры типа открытия</span><span class="sxs-lookup"><span data-stu-id="887e6-1943">Valid open type options are:</span></span>
  - <span data-ttu-id="887e6-1944">FX_OPEN_FOR_READ (0x00)</span><span class="sxs-lookup"><span data-stu-id="887e6-1944">FX_OPEN_FOR_READ (0x00)</span></span>
  - <span data-ttu-id="887e6-1945">FX_OPEN_FOR_WRITE (0x01)</span><span class="sxs-lookup"><span data-stu-id="887e6-1945">FX_OPEN_FOR_WRITE (0x01)</span></span>
  - <span data-ttu-id="887e6-1946">FX_OPEN_FOR_READ_FAST (0x02)</span><span class="sxs-lookup"><span data-stu-id="887e6-1946">FX_OPEN_FOR_READ_FAST (0x02)</span></span>

<span data-ttu-id="887e6-1947">Открытие файлов с помощью FX_OPEN_FOR_READ и FX_OPEN_FOR_READ_FAST выполняется аналогично.</span><span class="sxs-lookup"><span data-stu-id="887e6-1947">Opening files with FX_OPEN_FOR_READ and FX_OPEN_FOR_READ_FAST is similar:</span></span>

- <span data-ttu-id="887e6-1948">FX_OPEN_FOR_READ включает проверку того, что связанный список кластеров, составляющих файл, не изменяется, а FX_OPEN_FOR_READ_FAST не выполняет такую проверку, что ускоряет работу.</span><span class="sxs-lookup"><span data-stu-id="887e6-1948">FX_OPEN_FOR_READ includes verification that the linked-list of clusters that comprise the file are intact, and FX_OPEN_FOR_READ_FAST does not perform this verification, which makes it faster.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-1949">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-1949">Return Values</span></span>

- <span data-ttu-id="887e6-1950">**FX_SUCCESS** (0x00) — файл успешно открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-1950">**FX_SUCCESS** (0x00) Successful file open.</span></span>
- <span data-ttu-id="887e6-1951">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-1951">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="887e6-1952">**FX_NOT_FOUND** (0x04) — указанный файл не найден.</span><span class="sxs-lookup"><span data-stu-id="887e6-1952">**FX_NOT_FOUND** (0x04) Specified file was not found.</span></span>
- <span data-ttu-id="887e6-1953">**FX_NOT_A_FILE** (0x05) — указанное имя файла является каталогом или томом.</span><span class="sxs-lookup"><span data-stu-id="887e6-1953">**FX_NOT_A_FILE** (0x05) Specified file name was a directory or volume.</span></span>
- <span data-ttu-id="887e6-1954">**FX_FILE_CORRUPT** (0x08) — указанный файл поврежден, или его не удалось открыть.</span><span class="sxs-lookup"><span data-stu-id="887e6-1954">**FX_FILE_CORRUPT** (0x08) Specified file is corrupt and the open failed.</span></span>
- <span data-ttu-id="887e6-1955">**FX_ACCESS_ERROR** (0x06) — указанный файл уже открыт, или недопустимый тип открытия.</span><span class="sxs-lookup"><span data-stu-id="887e6-1955">**FX_ACCESS_ERROR** (0x06) Specified file is already open or open type is invalid.</span></span>
- <span data-ttu-id="887e6-1956">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-1956">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="887e6-1957">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="887e6-1957">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="887e6-1958">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-1958">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="887e6-1959">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="887e6-1959">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="887e6-1960">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-1960">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-1961">**FX_WRITE_PROTECT** (0x23) — носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-1961">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="887e6-1962">**FX_PTR_ERROR** (0x18) — недопустимый носитель или указатель файла.</span><span class="sxs-lookup"><span data-stu-id="887e6-1962">**FX_PTR_ERROR** (0x18) Invalid media or file pointer.</span></span>
- <span data-ttu-id="887e6-1963">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-1963">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-1964">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-1964">Allowed From</span></span>

<span data-ttu-id="887e6-1965">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-1965">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-1966">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-1966">Example</span></span>

```c
FX_MEDIA     my_media;
FX_FILE     my_file;
UINT         status;

/* Open the file "myfile.txt" for reading. */

status = fx_file_open(&my_media, &my_file, "myfile.txt", FX_OPEN_FOR_READ);

/* If status equals FX_SUCCESS, file "myfile.txt" is now
    open and may be accessed now with the my_file pointer. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-1967">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-1967">See Also</span></span>

- <span data-ttu-id="887e6-1968">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1968">fx_file_allocate</span></span>
- <span data-ttu-id="887e6-1969">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1969">fx_file_attributes_read</span></span>
- <span data-ttu-id="887e6-1970">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1970">fx_file_attributes_set</span></span>
- <span data-ttu-id="887e6-1971">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1971">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-1972">fx_file_close- fx_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1972">fx_file_close- fx_file_create</span></span>
- <span data-ttu-id="887e6-1973">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1973">fx_file_date_time_set</span></span>
- <span data-ttu-id="887e6-1974">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-1974">fx_file_delete</span></span>
- <span data-ttu-id="887e6-1975">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1975">fx_file_extended_allocate</span></span>
- <span data-ttu-id="887e6-1976">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-1976">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-1977">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1977">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="887e6-1978">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1978">fx_file_extended_seek</span></span>
- <span data-ttu-id="887e6-1979">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-1979">fx_file_extended_truncate</span></span>
- <span data-ttu-id="887e6-1980">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-1980">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="887e6-1981">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1981">fx_file_read</span></span>
- <span data-ttu-id="887e6-1982">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1982">fx_file_relative_seek</span></span>
- <span data-ttu-id="887e6-1983">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1983">fx_file_rename</span></span>
- <span data-ttu-id="887e6-1984">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-1984">fx_file_seek</span></span>
- <span data-ttu-id="887e6-1985">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-1985">fx_file_truncate</span></span>
- <span data-ttu-id="887e6-1986">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-1986">fx_file_truncate_release</span></span>
- <span data-ttu-id="887e6-1987">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="887e6-1987">fx_file_write</span></span>
- <span data-ttu-id="887e6-1988">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-1988">fx_file_write_notify_set</span></span>
- <span data-ttu-id="887e6-1989">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-1989">fx_unicode_file_create</span></span>
- <span data-ttu-id="887e6-1990">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-1990">fx_unicode_file_rename</span></span>
- <span data-ttu-id="887e6-1991">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1991">fx_unicode_name_get</span></span>
- <span data-ttu-id="887e6-1992">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-1992">fx_unicode_short_name_get</span></span>

## <a name="fx_file_read"></a><span data-ttu-id="887e6-1993">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="887e6-1993">fx_file_read</span></span>

<span data-ttu-id="887e6-1994">Считывает байты из файла</span><span class="sxs-lookup"><span data-stu-id="887e6-1994">Reads bytes from file</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-1995">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-1995">Prototype</span></span>

```c
UINT fx_file_read(
    FX_FILE *file_ptr, 
    VOID *buffer_ptr,
    ULONG request_size, 
    ULONG *actual_size);
```
### <a name="description"></a><span data-ttu-id="887e6-1996">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-1996">Description</span></span>

<span data-ttu-id="887e6-1997">Эта служба считывает байты из файла и сохраняет их в заданном буфере.</span><span class="sxs-lookup"><span data-stu-id="887e6-1997">This service reads bytes from the file and stores them in the supplied buffer.</span></span> <span data-ttu-id="887e6-1998">После завершения чтения внутренний указатель чтения файла корректируется так, чтобы он указывал на следующий байт в файле.</span><span class="sxs-lookup"><span data-stu-id="887e6-1998">After the read is complete, the file's internal read pointer is adjusted to point at the next byte in the file.</span></span> <span data-ttu-id="887e6-1999">Если в запросе осталось меньше байтов, в буфер будут сохранены только оставшиеся байты.</span><span class="sxs-lookup"><span data-stu-id="887e6-1999">If there are fewer bytes remaining in the request, only the bytes remaining are stored in the buffer.</span></span> <span data-ttu-id="887e6-2000">В любом случае общее число байтов, помещенных в буфер, возвращается вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="887e6-2000">In any case, the total number of bytes placed in the buffer is returned to the caller.</span></span>

> [!WARNING]
> <span data-ttu-id="887e6-2001">*Приложение должно гарантировать, что предоставленный буфер способен хранить указанное число запрошенных байтов.*</span><span class="sxs-lookup"><span data-stu-id="887e6-2001">*The application must ensure that the buffer supplied is able to store the specified number of requested bytes.*</span></span>

> [!WARNING]
> <span data-ttu-id="887e6-2002">*Более высокая производительность достигается тогда, когда буфер назначения находится на границе длинного слова, а запрошенный размер делится на sizeof(**ULONG**) без остатка.*</span><span class="sxs-lookup"><span data-stu-id="887e6-2002">*Faster performance is achieved if the destination buffer is on a long-word boundary and the requested size is evenly divisible by sizeof(**ULONG**).*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-2003">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-2003">Input Parameters</span></span>

- <span data-ttu-id="887e6-2004">**file_ptr**: указатель на блок управления файлом</span><span class="sxs-lookup"><span data-stu-id="887e6-2004">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="887e6-2005">**buffer_ptr**: указатель на буфер назначения для чтения</span><span class="sxs-lookup"><span data-stu-id="887e6-2005">**buffer_ptr**: Pointer to the destination buffer for the read.</span></span>
- <span data-ttu-id="887e6-2006">**request_size**: максимальное количество байтов для чтения</span><span class="sxs-lookup"><span data-stu-id="887e6-2006">**request_size**: Maximum number of bytes to read.</span></span>
- <span data-ttu-id="887e6-2007">**actual_size**: указатель на переменную для хранения фактического числа байтов, считанных в указанный буфер</span><span class="sxs-lookup"><span data-stu-id="887e6-2007">**actual_size**: Pointer to the variable to hold the actual number of bytes read into the supplied buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-2008">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-2008">Return Values</span></span>

- <span data-ttu-id="887e6-2009">**FX_SUCCESS** (0x00) — чтение из файла успешно выполнено.</span><span class="sxs-lookup"><span data-stu-id="887e6-2009">**FX_SUCCESS** (0x00) Successful file read.</span></span>
- <span data-ttu-id="887e6-2010">**FX_NOT_OPEN** (0x07) — указанный файл не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-2010">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="887e6-2011">**FX_FILE_CORRUPT** (0x08) — указанный файл поврежден,и не удалось выполнить чтение.</span><span class="sxs-lookup"><span data-stu-id="887e6-2011">**FX_FILE_CORRUPT** (0x08) Specified file is corrupt and the read failed.</span></span>
- <span data-ttu-id="887e6-2012">**FX_END_OF_FILE** (0x09) — достигнут конец файла.</span><span class="sxs-lookup"><span data-stu-id="887e6-2012">**FX_END_OF_FILE** (0x09) End of file has been reached.</span></span>
- <span data-ttu-id="887e6-2013">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-2013">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="887e6-2014">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="887e6-2014">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="887e6-2015">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-2015">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-2016">**FX_PTR_ERROR** (0x18) — недопустимый указатель на файл или буфер.</span><span class="sxs-lookup"><span data-stu-id="887e6-2016">**FX_PTR_ERROR** (0x18) Invalid file or buffer pointer.</span></span>
- <span data-ttu-id="887e6-2017">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-2017">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-2018">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-2018">Allowed From</span></span>

<span data-ttu-id="887e6-2019">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-2019">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-2020">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-2020">Example</span></span>

```c
FX_FILE                 my_file;
unsigned char           my_buffer[1024];
ULONG                   actual_bytes;
UINT                    status;

/* Read up to 1024 bytes into "my_buffer." */
status = fx_file_read(&my_file, my_buffer, 1024, &actual_bytes);

/* If status equals FX_SUCCESS, "my_buffer" contains the bytes
    read from the file. The total number of bytes read is in "actual_bytes." */
```
### <a name="see-also"></a><span data-ttu-id="887e6-2021">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-2021">See Also</span></span>

- <span data-ttu-id="887e6-2022">fx_file_allocate,</span><span class="sxs-lookup"><span data-stu-id="887e6-2022">fx_file_allocate,</span></span>
- <span data-ttu-id="887e6-2023">fx_file_attributes_read,</span><span class="sxs-lookup"><span data-stu-id="887e6-2023">fx_file_attributes_read,</span></span>
- <span data-ttu-id="887e6-2024">fx_file_attributes_set,</span><span class="sxs-lookup"><span data-stu-id="887e6-2024">fx_file_attributes_set,</span></span>
- <span data-ttu-id="887e6-2025">fx_file_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="887e6-2025">fx_file_best_effort_allocate,</span></span>
- <span data-ttu-id="887e6-2026">fx_file_close,</span><span class="sxs-lookup"><span data-stu-id="887e6-2026">fx_file_close,</span></span>
- <span data-ttu-id="887e6-2027">fx_file_create,</span><span class="sxs-lookup"><span data-stu-id="887e6-2027">fx_file_create,</span></span>
- <span data-ttu-id="887e6-2028">fx_file_date_time_set,</span><span class="sxs-lookup"><span data-stu-id="887e6-2028">fx_file_date_time_set,</span></span>
- <span data-ttu-id="887e6-2029">fx_file_delete,</span><span class="sxs-lookup"><span data-stu-id="887e6-2029">fx_file_delete,</span></span>
- <span data-ttu-id="887e6-2030">fx_file_extended_allocate,</span><span class="sxs-lookup"><span data-stu-id="887e6-2030">fx_file_extended_allocate,</span></span>
- <span data-ttu-id="887e6-2031">fx_file_extended_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="887e6-2031">fx_file_extended_best_effort_allocate,</span></span>
- <span data-ttu-id="887e6-2032">fx_file_extended_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="887e6-2032">fx_file_extended_relative_seek,</span></span>
- <span data-ttu-id="887e6-2033">fx_file_extended_seek,</span><span class="sxs-lookup"><span data-stu-id="887e6-2033">fx_file_extended_seek,</span></span>
- <span data-ttu-id="887e6-2034">fx_file_extended_truncate,</span><span class="sxs-lookup"><span data-stu-id="887e6-2034">fx_file_extended_truncate,</span></span>
- <span data-ttu-id="887e6-2035">fx_file_extended_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="887e6-2035">fx_file_extended_truncate_release,</span></span>
- <span data-ttu-id="887e6-2036">fx_file_open,</span><span class="sxs-lookup"><span data-stu-id="887e6-2036">fx_file_open,</span></span>
- <span data-ttu-id="887e6-2037">fx_file_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="887e6-2037">fx_file_relative_seek,</span></span>
- <span data-ttu-id="887e6-2038">fx_file_rename,</span><span class="sxs-lookup"><span data-stu-id="887e6-2038">fx_file_rename,</span></span>
- <span data-ttu-id="887e6-2039">fx_file_seek,</span><span class="sxs-lookup"><span data-stu-id="887e6-2039">fx_file_seek,</span></span>
- <span data-ttu-id="887e6-2040">fx_file_truncate,</span><span class="sxs-lookup"><span data-stu-id="887e6-2040">fx_file_truncate,</span></span>
- <span data-ttu-id="887e6-2041">fx_file_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="887e6-2041">fx_file_truncate_release,</span></span>
- <span data-ttu-id="887e6-2042">fx_file_write,</span><span class="sxs-lookup"><span data-stu-id="887e6-2042">fx_file_write,</span></span>
- <span data-ttu-id="887e6-2043">fx_file_write_notify_set,</span><span class="sxs-lookup"><span data-stu-id="887e6-2043">fx_file_write_notify_set,</span></span>
- <span data-ttu-id="887e6-2044">fx_unicode_file_create,</span><span class="sxs-lookup"><span data-stu-id="887e6-2044">fx_unicode_file_create,</span></span>
- <span data-ttu-id="887e6-2045">fx_unicode_file_rename,</span><span class="sxs-lookup"><span data-stu-id="887e6-2045">fx_unicode_file_rename,</span></span>
- <span data-ttu-id="887e6-2046">fx_unicode_name_get,</span><span class="sxs-lookup"><span data-stu-id="887e6-2046">fx_unicode_name_get,</span></span>
- <span data-ttu-id="887e6-2047">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-2047">fx_unicode_short_name_get</span></span>

## <a name="fx_file_relative_seek"></a><span data-ttu-id="887e6-2048">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-2048">fx_file_relative_seek</span></span>

<span data-ttu-id="887e6-2049">Размещение на указанное относительное смещение в байтах</span><span class="sxs-lookup"><span data-stu-id="887e6-2049">Positions to a relative byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-2050">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-2050">Prototype</span></span>

```c
UINT fx_file_relative_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset,
    UINT seek_from);
```
### <a name="description"></a><span data-ttu-id="887e6-2051">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-2051">Description</span></span>

<span data-ttu-id="887e6-2052">Эта служба размещает внутренний указатель чтения/записи файла на указанное относительное смещение в байтах.</span><span class="sxs-lookup"><span data-stu-id="887e6-2052">This service positions the internal file read/write pointer to the specified relative byte offset.</span></span> <span data-ttu-id="887e6-2053">Все последующие запросы на чтение или запись файла будут начинаться с этого места в файле.</span><span class="sxs-lookup"><span data-stu-id="887e6-2053">Any subsequent file read or write request will begin at this location in the file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="887e6-2054">*Если операция поиска пытается выполнить поиск после конца файла, указатель на чтение и запись файла помещается в конец файла. И наоборот, если операция поиска пытается установить положение после начала файла, указатель на чтение и запись файла помещается в начало файла.*</span><span class="sxs-lookup"><span data-stu-id="887e6-2054">*If the seek operation attempts to seek past the end of the file, the file's read/write pointer is positioned to the end of the file. Conversely, if the seek operation attempts to position past the beginning of the file, the file's read/write pointer is positioned to the beginning of the file.*</span></span>

<span data-ttu-id="887e6-2055">Чтобы найти значение смещения, превышающее 4 ГБ, приложение должно использовать службу *fx_file_extended_relative_seek*.</span><span class="sxs-lookup"><span data-stu-id="887e6-2055">To seek with an offset value beyond 4GB, application shall use the service *fx_file_extended_relative_seek*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-2056">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-2056">Input Parameters</span></span>

- <span data-ttu-id="887e6-2057">**file_ptr**: указатель на открытый ранее файл</span><span class="sxs-lookup"><span data-stu-id="887e6-2057">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="887e6-2058">**byte_offset**: требуемое относительное смещение в байтах в файле</span><span class="sxs-lookup"><span data-stu-id="887e6-2058">**byte_offset**: Desired relative byte offset in file.</span></span>
- <span data-ttu-id="887e6-2059">**seek_from**: направление и расположение для выполнения относительного поиска</span><span class="sxs-lookup"><span data-stu-id="887e6-2059">**seek_from**: The direction and location of where to perform the relative seek from.</span></span> <span data-ttu-id="887e6-2060">Допустимые параметры чтения определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="887e6-2060">Valid seek options are defined as follows:</span></span>
  - <span data-ttu-id="887e6-2061">FX_SEEK_BEGIN (0x00)</span><span class="sxs-lookup"><span data-stu-id="887e6-2061">FX_SEEK_BEGIN (0x00)</span></span>
  - <span data-ttu-id="887e6-2062">FX_SEEK_END (0x01)</span><span class="sxs-lookup"><span data-stu-id="887e6-2062">FX_SEEK_END (0x01)</span></span>
  - <span data-ttu-id="887e6-2063">FX_SEEK_FORWARD (0x02)</span><span class="sxs-lookup"><span data-stu-id="887e6-2063">FX_SEEK_FORWARD (0x02)</span></span>
  - <span data-ttu-id="887e6-2064">FX_SEEK_BACK (0x03)</span><span class="sxs-lookup"><span data-stu-id="887e6-2064">FX_SEEK_BACK (0x03)</span></span>

<span data-ttu-id="887e6-2065">Если указан параметр FX_SEEK_BEGIN, операция поиска выполняется с начала файла.</span><span class="sxs-lookup"><span data-stu-id="887e6-2065">If FX_SEEK_BEGIN is specified, the seek operation is performed from the beginning of the file.</span></span> <span data-ttu-id="887e6-2066">Если указан параметр FX_SEEK_END, операция поиска выполняется в обратном направлении с конца файла.</span><span class="sxs-lookup"><span data-stu-id="887e6-2066">If FX_SEEK_END is specified the seek operation is performed backward from the end of the file.</span></span> <span data-ttu-id="887e6-2067">Если указан параметр FX_SEEK_FORWARD, операция поиска выполняется вперед от текущего расположения файла.</span><span class="sxs-lookup"><span data-stu-id="887e6-2067">If FX_SEEK_FORWARD is specified, the seek operation is performed forward from the current file position.</span></span> <span data-ttu-id="887e6-2068">Если указан параметр FX_SEEK_BACK, операция поиска выполняется в обратном направлении от текущей позиции файла.</span><span class="sxs-lookup"><span data-stu-id="887e6-2068">If FX_SEEK_BACK is specified, the seek operation is performed backward from the current file position.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-2069">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-2069">Return Values</span></span>

- <span data-ttu-id="887e6-2070">**FX_SUCCESS** (0x00) — относительный поиск файла успешно выполнен.</span><span class="sxs-lookup"><span data-stu-id="887e6-2070">**FX_SUCCESS** (0x00) Successful file relative seek.</span></span>
- <span data-ttu-id="887e6-2071">**FX_NOT_OPEN** (0x07) — указанный файл в настоящее время не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-2071">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="887e6-2072">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-2072">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-2073">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-2073">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="887e6-2074">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-2074">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="887e6-2075">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-2075">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="887e6-2076">**FX_PTR_ERROR** (0x18) — недопустимый указатель на файл.</span><span class="sxs-lookup"><span data-stu-id="887e6-2076">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="887e6-2077">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-2077">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-2078">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-2078">Allowed From</span></span>

<span data-ttu-id="887e6-2079">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-2079">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-2080">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-2080">Example</span></span>

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to move 10 bytes forward in "my_file". */

status = fx_file_relative_seek(&my_file, 10, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write pointers
    are positioned 10 bytes forward. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-2081">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-2081">See Also</span></span>

- <span data-ttu-id="887e6-2082">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-2082">fx_file_allocate</span></span>
- <span data-ttu-id="887e6-2083">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-2083">fx_file_attributes_read</span></span>
- <span data-ttu-id="887e6-2084">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2084">fx_file_attributes_set</span></span>
- <span data-ttu-id="887e6-2085">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-2085">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-2086">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="887e6-2086">fx_file_close</span></span>
- <span data-ttu-id="887e6-2087">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-2087">fx_file_create</span></span>
- <span data-ttu-id="887e6-2088">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2088">fx_file_date_time_set</span></span>
- <span data-ttu-id="887e6-2089">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-2089">fx_file_delete</span></span>
- <span data-ttu-id="887e6-2090">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-2090">fx_file_extended_allocate</span></span>
- <span data-ttu-id="887e6-2091">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-2091">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-2092">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-2092">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="887e6-2093">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-2093">fx_file_extended_seek</span></span>
- <span data-ttu-id="887e6-2094">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-2094">fx_file_extended_truncate</span></span>
- <span data-ttu-id="887e6-2095">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-2095">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="887e6-2096">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="887e6-2096">fx_file_open</span></span>
- <span data-ttu-id="887e6-2097">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="887e6-2097">fx_file_read</span></span>
- <span data-ttu-id="887e6-2098">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-2098">fx_file_rename</span></span>
- <span data-ttu-id="887e6-2099">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-2099">fx_file_seek</span></span>
- <span data-ttu-id="887e6-2100">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-2100">fx_file_truncate</span></span>
- <span data-ttu-id="887e6-2101">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-2101">fx_file_truncate_release</span></span>
- <span data-ttu-id="887e6-2102">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="887e6-2102">fx_file_write</span></span>
- <span data-ttu-id="887e6-2103">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2103">fx_file_write_notify_set</span></span>
- <span data-ttu-id="887e6-2104">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-2104">fx_unicode_file_create</span></span>
- <span data-ttu-id="887e6-2105">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-2105">fx_unicode_file_rename</span></span>
- <span data-ttu-id="887e6-2106">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-2106">fx_unicode_name_get</span></span>
- <span data-ttu-id="887e6-2107">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-2107">fx_unicode_short_name_get</span></span>

## <a name="fx_file_rename"></a><span data-ttu-id="887e6-2108">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-2108">fx_file_rename</span></span>

<span data-ttu-id="887e6-2109">Переименовывает файл</span><span class="sxs-lookup"><span data-stu-id="887e6-2109">Renames  file</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-2110">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-2110">Prototype</span></span>

```c
UINT fx_file_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_file_name,
    CHAR *new_file_name);
```
### <a name="description"></a><span data-ttu-id="887e6-2111">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-2111">Description</span></span>

<span data-ttu-id="887e6-2112">Эта служба изменяет имя файла, указанного параметром *old_file_name*.</span><span class="sxs-lookup"><span data-stu-id="887e6-2112">This service changes the name of the file specified by *old_file_name*.</span></span> <span data-ttu-id="887e6-2113">Переименование также выполняется относительно указанного пути или пути по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="887e6-2113">Renaming is also done relative to the specified path or the default path.</span></span> <span data-ttu-id="887e6-2114">Если в новом имени файла указан путь, переименованный файл фактически перемещается по указанному пути.</span><span class="sxs-lookup"><span data-stu-id="887e6-2114">If a path is specified in the new file name, the renamed file is effectively moved to the specified path.</span></span> <span data-ttu-id="887e6-2115">Если путь не указан, переименованный файл помещается в текущий путь по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="887e6-2115">If no path is specified, the renamed file is placed in the current default path.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-2116">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-2116">Input Parameters</span></span>

- <span data-ttu-id="887e6-2117">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-2117">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="887e6-2118">**old_file_name**: указатель на имя переименовываемого файла (путь к каталогу является необязательным)</span><span class="sxs-lookup"><span data-stu-id="887e6-2118">**old_file_name**: Pointer to the name of the file to rename (directory path is optional).</span></span>
- <span data-ttu-id="887e6-2119">**new_file_name**: указатель на новое имя файла</span><span class="sxs-lookup"><span data-stu-id="887e6-2119">**new_file_name**: Pointer to the new file name.</span></span> <span data-ttu-id="887e6-2120">Путь к каталогу не допускается.</span><span class="sxs-lookup"><span data-stu-id="887e6-2120">The directory path is not allowed.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-2121">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-2121">Return Values</span></span>

- <span data-ttu-id="887e6-2122">**FX_SUCCESS** (0x00) — файл успешно переименован.</span><span class="sxs-lookup"><span data-stu-id="887e6-2122">**FX_SUCCESS** (0x00) Successful file rename.</span></span>
- <span data-ttu-id="887e6-2123">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-2123">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="887e6-2124">**FX_NOT_FOUND** (0x04) — указанный файл не найден.</span><span class="sxs-lookup"><span data-stu-id="887e6-2124">**FX_NOT_FOUND** (0x04)    Specified file was not found.</span></span>
- <span data-ttu-id="887e6-2125">**FX_NOT_A_FILE** (0x05) — указанный файл является каталогом.</span><span class="sxs-lookup"><span data-stu-id="887e6-2125">**FX_NOT_A_FILE** (0x05) Specified file is a directory.</span></span>
- <span data-ttu-id="887e6-2126">**FX_ACCESS_ERROR** (0x06) — указанный файл уже открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-2126">**FX_ACCESS_ERROR** (0x06) Specified file is already open.</span></span>
- <span data-ttu-id="887e6-2127">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-2127">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-2128">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-2128">**FX_WRITE_PROTECT** (0x23)    Specified media is write protected.</span></span>
- <span data-ttu-id="887e6-2129">**FX_INVALID_NAME** (0x0C) — указанное новое имя файла не является допустимым именем файла.</span><span class="sxs-lookup"><span data-stu-id="887e6-2129">**FX_INVALID_NAME** (0x0C) Specified new file name is not a valid file name.</span></span>
- <span data-ttu-id="887e6-2130">**FX_INVALID_PATH** (0x0D) — недопустимый путь.</span><span class="sxs-lookup"><span data-stu-id="887e6-2130">**FX_INVALID_PATH** (0x0D)    Path is invalid.</span></span>
- <span data-ttu-id="887e6-2131">**FX_ALREADY_CREATED** (0x0B) — новое имя файла уже используется.</span><span class="sxs-lookup"><span data-stu-id="887e6-2131">**FX_ALREADY_CREATED** (0x0B) The new file name is used.</span></span>
- <span data-ttu-id="887e6-2132">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="887e6-2132">**FX_MEDIA_INVALID** (0x02)    Media is invalid.</span></span>
- <span data-ttu-id="887e6-2133">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-2133">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="887e6-2134">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-2134">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="887e6-2135">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-2135">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="887e6-2136">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="887e6-2136">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="887e6-2137">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать таблицу FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-2137">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="887e6-2138">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-2138">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="887e6-2139">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-2139">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-2140">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-2140">Allowed From</span></span>

<span data-ttu-id="887e6-2141">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-2141">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-2142">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-2142">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;

/* Rename "myfile1.txt" to "myfile2.txt" in the default directory of the media. */

status = fx_file_rename(&my_media, "myfile1.txt", "myfile2.txt");

/* If status equals FX_SUCCESS, the file was successfully renamed. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-2143">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-2143">See Also</span></span>

- <span data-ttu-id="887e6-2144">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-2144">fx_file_allocate</span></span>
- <span data-ttu-id="887e6-2145">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-2145">fx_file_attributes_read</span></span>
- <span data-ttu-id="887e6-2146">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2146">fx_file_attributes_set</span></span>
- <span data-ttu-id="887e6-2147">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-2147">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-2148">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="887e6-2148">fx_file_close</span></span>
- <span data-ttu-id="887e6-2149">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-2149">fx_file_create</span></span>
- <span data-ttu-id="887e6-2150">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2150">fx_file_date_time_set</span></span>
- <span data-ttu-id="887e6-2151">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-2151">fx_file_delete</span></span>
- <span data-ttu-id="887e6-2152">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-2152">fx_file_extended_allocate</span></span>
- <span data-ttu-id="887e6-2153">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-2153">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-2154">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-2154">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="887e6-2155">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-2155">fx_file_extended_seek</span></span>
- <span data-ttu-id="887e6-2156">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-2156">fx_file_extended_truncate</span></span>
- <span data-ttu-id="887e6-2157">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-2157">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="887e6-2158">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="887e6-2158">fx_file_open</span></span>
- <span data-ttu-id="887e6-2159">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="887e6-2159">fx_file_read</span></span>
- <span data-ttu-id="887e6-2160">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-2160">fx_file_relative_seek</span></span>
- <span data-ttu-id="887e6-2161">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-2161">fx_file_seek</span></span>
- <span data-ttu-id="887e6-2162">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-2162">fx_file_truncate</span></span>
- <span data-ttu-id="887e6-2163">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-2163">fx_file_truncate_release</span></span>
- <span data-ttu-id="887e6-2164">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="887e6-2164">fx_file_write</span></span>
- <span data-ttu-id="887e6-2165">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2165">fx_file_write_notify_set</span></span>
- <span data-ttu-id="887e6-2166">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-2166">fx_unicode_file_create</span></span>
- <span data-ttu-id="887e6-2167">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-2167">fx_unicode_file_rename</span></span>
- <span data-ttu-id="887e6-2168">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-2168">fx_unicode_name_get</span></span>
- <span data-ttu-id="887e6-2169">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-2169">fx_unicode_short_name_get</span></span>

## <a name="fx_file_seek"></a><span data-ttu-id="887e6-2170">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-2170">fx_file_seek</span></span>

<span data-ttu-id="887e6-2171">Размещение на указанное смещение в байтах</span><span class="sxs-lookup"><span data-stu-id="887e6-2171">Positions to byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-2172">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-2172">Prototype</span></span>

```c
UINT fx_file_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset);
```
### <a name="description"></a><span data-ttu-id="887e6-2173">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-2173">Description</span></span>

<span data-ttu-id="887e6-2174">Эта служба размещает внутренний указатель чтения/записи файла на указанное смещение в байтах.</span><span class="sxs-lookup"><span data-stu-id="887e6-2174">This service positions the internal file read/write pointer to the specified byte offset.</span></span> <span data-ttu-id="887e6-2175">Все последующие запросы на чтение или запись файла будут начинаться с этого места в файле.</span><span class="sxs-lookup"><span data-stu-id="887e6-2175">Any subsequent file read or write request will begin at this location in the file.</span></span>

<span data-ttu-id="887e6-2176">Чтобы найти значение смещения, превышающее 4 ГБ, приложение должно использовать службу *fx_file_extended_seek*.</span><span class="sxs-lookup"><span data-stu-id="887e6-2176">To seek with an offset value beyond 4GB, application shall use the service *fx_file_extended_seek*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-2177">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-2177">Input Parameters</span></span>

- <span data-ttu-id="887e6-2178">**file_ptr**: указатель на блок управления файлом</span><span class="sxs-lookup"><span data-stu-id="887e6-2178">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="887e6-2179">**byte_offset**: требуемое смещение в байтах в файле</span><span class="sxs-lookup"><span data-stu-id="887e6-2179">**byte_offset**: Desired byte offset in file.</span></span> <span data-ttu-id="887e6-2180">При нулевом значении указатель чтения/записи будет размещен в начале файла, а при значении, превышающем размер файла, указатель чтения/записи будет помещен в конец файла.</span><span class="sxs-lookup"><span data-stu-id="887e6-2180">A value of zero will position the read/write pointer at the beginning of the file, while a value greater than the file's size will position the read/write pointer at the end of the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-2181">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-2181">Return Values</span></span>

- <span data-ttu-id="887e6-2182">**FX_SUCCESS** (0x00) — файл успешно найден.</span><span class="sxs-lookup"><span data-stu-id="887e6-2182">**FX_SUCCESS** (0x00) Successful file seek.</span></span>
- <span data-ttu-id="887e6-2183">**FX_NOT_OPEN** (0x07) — указанный файл не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-2183">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="887e6-2184">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-2184">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-2185">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-2185">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="887e6-2186">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-2186">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="887e6-2187">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="887e6-2187">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="887e6-2188">**FX_PTR_ERROR** (0x18) — недопустимый указатель на файл.</span><span class="sxs-lookup"><span data-stu-id="887e6-2188">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="887e6-2189">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-2189">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-2190">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-2190">Allowed From</span></span>

<span data-ttu-id="887e6-2191">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-2191">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-2192">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-2192">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Seek to the beginning of "my_file." */
status = fx_file_seek(&my_file, 0);
/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned to the beginning of the file. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-2193">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-2193">See Also</span></span>

- <span data-ttu-id="887e6-2194">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-2194">fx_file_allocate</span></span>
- <span data-ttu-id="887e6-2195">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-2195">fx_file_attributes_read</span></span>
- <span data-ttu-id="887e6-2196">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2196">fx_file_attributes_set</span></span>
- <span data-ttu-id="887e6-2197">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-2197">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-2198">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="887e6-2198">fx_file_close</span></span>
- <span data-ttu-id="887e6-2199">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-2199">fx_file_create</span></span>
- <span data-ttu-id="887e6-2200">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2200">fx_file_date_time_set</span></span>
- <span data-ttu-id="887e6-2201">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-2201">fx_file_delete</span></span>
- <span data-ttu-id="887e6-2202">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-2202">fx_file_extended_allocate</span></span>
- <span data-ttu-id="887e6-2203">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-2203">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-2204">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-2204">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="887e6-2205">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-2205">fx_file_extended_seek</span></span>
- <span data-ttu-id="887e6-2206">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-2206">fx_file_extended_truncate</span></span>
- <span data-ttu-id="887e6-2207">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-2207">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="887e6-2208">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="887e6-2208">fx_file_open</span></span>
- <span data-ttu-id="887e6-2209">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="887e6-2209">fx_file_read</span></span>
- <span data-ttu-id="887e6-2210">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-2210">fx_file_rename</span></span>
- <span data-ttu-id="887e6-2211">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-2211">fx_file_seek</span></span>
- <span data-ttu-id="887e6-2212">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-2212">fx_file_truncate</span></span>
- <span data-ttu-id="887e6-2213">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-2213">fx_file_truncate_release</span></span>
- <span data-ttu-id="887e6-2214">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="887e6-2214">fx_file_write</span></span>
- <span data-ttu-id="887e6-2215">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2215">fx_file_write_notify_set</span></span>
- <span data-ttu-id="887e6-2216">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-2216">fx_unicode_file_create</span></span>
- <span data-ttu-id="887e6-2217">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-2217">fx_unicode_file_rename</span></span>
- <span data-ttu-id="887e6-2218">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-2218">fx_unicode_name_get</span></span>
- <span data-ttu-id="887e6-2219">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-2219">fx_unicode_short_name_get</span></span>

## <a name="fx_file_truncate"></a><span data-ttu-id="887e6-2220">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-2220">fx_file_truncate</span></span>

<span data-ttu-id="887e6-2221">Усекает файл</span><span class="sxs-lookup"><span data-stu-id="887e6-2221">Truncates file</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-2222">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-2222">Prototype</span></span>

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```

### <a name="description"></a><span data-ttu-id="887e6-2223">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-2223">Description</span></span>

<span data-ttu-id="887e6-2224">Эта служба усекает размер файла до указанного.</span><span class="sxs-lookup"><span data-stu-id="887e6-2224">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="887e6-2225">Если указанный размер превышает фактический размер файла, эта служба не выполняет никаких действий.</span><span class="sxs-lookup"><span data-stu-id="887e6-2225">If the supplied size is greater than the actual file size, this service doesn't do anything.</span></span> <span data-ttu-id="887e6-2226">Ни один из кластеров носителя, связанных с файлом, не освобождается.</span><span class="sxs-lookup"><span data-stu-id="887e6-2226">None of the media clusters associated with the file are released.</span></span>

> [!WARNING]
> <span data-ttu-id="887e6-2227">*Проявляйте осторожность при усечении файлов, которые также могут быть открыты для одновременного чтения. Усечение файла, открытого для чтения, может привести к чтению недопустимых данных.*</span><span class="sxs-lookup"><span data-stu-id="887e6-2227">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="887e6-2228">Если размер превышает 4 ГБ, приложение должно использовать службу *fx_file_extended_truncate*.</span><span class="sxs-lookup"><span data-stu-id="887e6-2228">To operate beyond 4GB, application shall use the service *fx_file_extended_truncate*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-2229">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-2229">Input Parameters</span></span>

- <span data-ttu-id="887e6-2230">**file_ptr**: указатель на блок управления файлом</span><span class="sxs-lookup"><span data-stu-id="887e6-2230">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="887e6-2231">**size**: новый размер файла</span><span class="sxs-lookup"><span data-stu-id="887e6-2231">**size**: New file size.</span></span> <span data-ttu-id="887e6-2232">Число байтов после нового размера файла не учитывается.</span><span class="sxs-lookup"><span data-stu-id="887e6-2232">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-2233">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-2233">Return Values</span></span>

- <span data-ttu-id="887e6-2234">**FX_SUCCESS** (0x00) — файл успешно усечен.</span><span class="sxs-lookup"><span data-stu-id="887e6-2234">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="887e6-2235">**FX_NOT_OPEN** (0x07) — указанный файл не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-2235">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="887e6-2236">**FX_ACCESS_ERROR** (0x06) — указанный файл не открыт для записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-2236">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="887e6-2237">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-2237">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-2238">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-2238">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="887e6-2239">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-2239">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="887e6-2240">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-2240">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="887e6-2241">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-2241">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="887e6-2242">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="887e6-2242">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="887e6-2243">**FX_PTR_ERROR** (0x18) — недопустимый указатель на файл.</span><span class="sxs-lookup"><span data-stu-id="887e6-2243">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="887e6-2244">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-2244">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-2245">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-2245">Allowed From</span></span>

<span data-ttu-id="887e6-2246">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-2246">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-2247">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-2247">Example</span></span>

```c
FX_FILE                my_file;
UINT                status;
/* Truncate "my_file" to 100 bytes. */

status = fx_file_truncate(&my_file, 100);

/* If status equals FX_SUCCESS, "my_file" contains 100 or fewer bytes. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-2248">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-2248">See Also</span></span>

- <span data-ttu-id="887e6-2249">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-2249">fx_file_allocate</span></span>
- <span data-ttu-id="887e6-2250">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-2250">fx_file_attributes_read</span></span>
- <span data-ttu-id="887e6-2251">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2251">fx_file_attributes_set</span></span>
- <span data-ttu-id="887e6-2252">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-2252">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-2253">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="887e6-2253">fx_file_close</span></span>
- <span data-ttu-id="887e6-2254">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-2254">fx_file_create</span></span>
- <span data-ttu-id="887e6-2255">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2255">fx_file_date_time_set</span></span>
- <span data-ttu-id="887e6-2256">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-2256">fx_file_delete</span></span>
- <span data-ttu-id="887e6-2257">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-2257">fx_file_extended_allocate</span></span>
- <span data-ttu-id="887e6-2258">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-2258">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-2259">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-2259">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="887e6-2260">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-2260">fx_file_extended_seek</span></span>
- <span data-ttu-id="887e6-2261">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-2261">fx_file_extended_truncate</span></span>
- <span data-ttu-id="887e6-2262">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-2262">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="887e6-2263">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="887e6-2263">fx_file_open</span></span>
- <span data-ttu-id="887e6-2264">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="887e6-2264">fx_file_read</span></span>
- <span data-ttu-id="887e6-2265">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-2265">fx_file_relative_seek</span></span>
- <span data-ttu-id="887e6-2266">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-2266">fx_file_rename</span></span>
- <span data-ttu-id="887e6-2267">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-2267">fx_file_seek</span></span>
- <span data-ttu-id="887e6-2268">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-2268">fx_file_truncate_release</span></span>
- <span data-ttu-id="887e6-2269">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="887e6-2269">fx_file_write</span></span>
- <span data-ttu-id="887e6-2270">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2270">fx_file_write_notify_set</span></span>
- <span data-ttu-id="887e6-2271">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-2271">fx_unicode_file_create</span></span>
- <span data-ttu-id="887e6-2272">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-2272">fx_unicode_file_rename</span></span>
- <span data-ttu-id="887e6-2273">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-2273">fx_unicode_name_get</span></span>
- <span data-ttu-id="887e6-2274">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-2274">fx_unicode_short_name_get</span></span>

## <a name="fx_file_truncate_release"></a><span data-ttu-id="887e6-2275">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-2275">fx_file_truncate_release</span></span>

<span data-ttu-id="887e6-2276">Усекает кластеры файлов и выпусков</span><span class="sxs-lookup"><span data-stu-id="887e6-2276">Truncates file and releases cluster(s)</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-2277">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-2277">Prototype</span></span>

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```
### <a name="description"></a><span data-ttu-id="887e6-2278">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-2278">Description</span></span>

<span data-ttu-id="887e6-2279">Эта служба усекает размер файла до указанного.</span><span class="sxs-lookup"><span data-stu-id="887e6-2279">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="887e6-2280">Если указанный размер превышает фактический размер файла, эта служба не выполняет никаких действий.</span><span class="sxs-lookup"><span data-stu-id="887e6-2280">If the supplied size is greater than the actual file size, this service does not do anything.</span></span> <span data-ttu-id="887e6-2281">В отличие от службы ***fx_file_truncate*** эта служба освобождает неиспользуемые кластеры.</span><span class="sxs-lookup"><span data-stu-id="887e6-2281">Unlike the ***fx_file_truncate*** service, this service does release any unused clusters.</span></span>

> [!WARNING]
> <span data-ttu-id="887e6-2282">*Проявляйте осторожность при усечении файлов, которые также могут быть открыты для одновременного чтения. Усечение файла, открытого для чтения, может привести к чтению недопустимых данных.*</span><span class="sxs-lookup"><span data-stu-id="887e6-2282">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="887e6-2283">Если размер превышает 4 ГБ, приложение должно использовать службу *fx_file_extended_truncate_release*.</span><span class="sxs-lookup"><span data-stu-id="887e6-2283">To operate beyond 4GB, application shall use the service *fx_file_extended_truncate_release*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-2284">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-2284">Input Parameters</span></span>

- <span data-ttu-id="887e6-2285">**file_ptr**: указатель на открытый ранее файл</span><span class="sxs-lookup"><span data-stu-id="887e6-2285">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="887e6-2286">**size**: новый размер файла</span><span class="sxs-lookup"><span data-stu-id="887e6-2286">**size**: New file size.</span></span> <span data-ttu-id="887e6-2287">Число байтов после нового размера файла не учитывается.</span><span class="sxs-lookup"><span data-stu-id="887e6-2287">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-2288">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-2288">Return Values</span></span>

- <span data-ttu-id="887e6-2289">**FX_SUCCESS** (0x00) — файл успешно усечен.</span><span class="sxs-lookup"><span data-stu-id="887e6-2289">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="887e6-2290">**FX_ACCESS_ERROR** (0x06) — указанный файл не открыт для записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-2290">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="887e6-2291">**FX_NOT_OPEN** (0x07) — указанный файл в настоящее время не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-2291">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="887e6-2292">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-2292">**FX_IO_ERROR** (0x90)    Driver I/O error.</span></span>
- <span data-ttu-id="887e6-2293">**FX_WRITE_PROTECT** (0x23) — носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-2293">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="887e6-2294">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-2294">**FX_FILE_CORRUPT** (0x08)    File is corrupted.</span></span>
- <span data-ttu-id="887e6-2295">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-2295">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="887e6-2296">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-2296">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="887e6-2297">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-2297">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="887e6-2298">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="887e6-2298">**FX_NO_MORE_SPACE** (0x0A)    No more space to complete the operation.</span></span>
- <span data-ttu-id="887e6-2299">**FX_PTR_ERROR** (0x18) — недопустимый указатель на файл.</span><span class="sxs-lookup"><span data-stu-id="887e6-2299">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="887e6-2300">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-2300">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-2301">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-2301">Allowed From</span></span>

<span data-ttu-id="887e6-2302">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-2302">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-2303">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-2303">Example</span></span>

```c
FX_FILE         my_file;
UINT             status;

/* Attempt to truncate everything after the first 100 bytes of "my_file". */

status = fx_file_truncate_release(&my_file, 100);

/* If status equals FX_SUCCESS, the file is now 100 bytes
    or fewer and all unused clusters have been released. */
```
### <a name="see-also"></a><span data-ttu-id="887e6-2304">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-2304">See Also</span></span>

- <span data-ttu-id="887e6-2305">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-2305">fx_file_allocate</span></span>
- <span data-ttu-id="887e6-2306">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-2306">fx_file_attributes_read</span></span>
- <span data-ttu-id="887e6-2307">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2307">fx_file_attributes_set</span></span>
- <span data-ttu-id="887e6-2308">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-2308">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-2309">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="887e6-2309">fx_file_close</span></span>
- <span data-ttu-id="887e6-2310">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-2310">fx_file_create</span></span>
- <span data-ttu-id="887e6-2311">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2311">fx_file_date_time_set</span></span>
- <span data-ttu-id="887e6-2312">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-2312">fx_file_delete</span></span>
- <span data-ttu-id="887e6-2313">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-2313">fx_file_extended_allocate</span></span>
- <span data-ttu-id="887e6-2314">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-2314">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-2315">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-2315">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="887e6-2316">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-2316">fx_file_extended_seek</span></span>
- <span data-ttu-id="887e6-2317">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-2317">fx_file_extended_truncate</span></span>
- <span data-ttu-id="887e6-2318">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-2318">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="887e6-2319">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="887e6-2319">fx_file_open</span></span>
- <span data-ttu-id="887e6-2320">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="887e6-2320">fx_file_read</span></span>
- <span data-ttu-id="887e6-2321">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-2321">fx_file_relative_seek</span></span>
- <span data-ttu-id="887e6-2322">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-2322">fx_file_rename</span></span>
- <span data-ttu-id="887e6-2323">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-2323">fx_file_seek</span></span>
- <span data-ttu-id="887e6-2324">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-2324">fx_file_truncate</span></span>
- <span data-ttu-id="887e6-2325">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="887e6-2325">fx_file_write</span></span>
- <span data-ttu-id="887e6-2326">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2326">fx_file_write_notify_set</span></span>
- <span data-ttu-id="887e6-2327">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-2327">fx_unicode_file_create</span></span>
- <span data-ttu-id="887e6-2328">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-2328">fx_unicode_file_rename</span></span>
- <span data-ttu-id="887e6-2329">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-2329">fx_unicode_name_get</span></span>
- <span data-ttu-id="887e6-2330">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-2330">fx_unicode_short_name_get</span></span>

## <a name="fx_file_write"></a><span data-ttu-id="887e6-2331">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="887e6-2331">fx_file_write</span></span>

<span data-ttu-id="887e6-2332">Записывает байты в файл</span><span class="sxs-lookup"><span data-stu-id="887e6-2332">Writes bytes to file</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-2333">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-2333">Prototype</span></span>

```c
UINT fx_file_write(
    FX_FILE *file_ptr,
    VOID *buffer_ptr,
    ULONG size);
```
### <a name="description"></a><span data-ttu-id="887e6-2334">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-2334">Description</span></span>

<span data-ttu-id="887e6-2335">Эта служба записывает байты из указанного буфера, начиная с текущей позиции файла.</span><span class="sxs-lookup"><span data-stu-id="887e6-2335">This service writes bytes from the specified buffer starting at the file's current position.</span></span> <span data-ttu-id="887e6-2336">После завершения записи внутренний указатель чтения файла корректируется так, чтобы он указывал на следующий байт в файле.</span><span class="sxs-lookup"><span data-stu-id="887e6-2336">After the write is complete, the file's internal read pointer is adjusted to point at the next byte in the file.</span></span>

> [!WARNING]
> <span data-ttu-id="887e6-2337">*Более высокая производительность достигается тогда, когда исходный буфер находится на границе длинного слова, а запрошенный размер делится на sizeof(**ULONG**) без остатка.*</span><span class="sxs-lookup"><span data-stu-id="887e6-2337">*Faster performance is achieved if the source buffer is on a long-word boundary and the requested size is evenly divisible by sizeof(**ULONG**).*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-2338">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-2338">Input Parameters</span></span>

- <span data-ttu-id="887e6-2339">**file_ptr**: указатель на блок управления файлом</span><span class="sxs-lookup"><span data-stu-id="887e6-2339">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="887e6-2340">**buffer_ptr**: указатель на исходный буфер для записи</span><span class="sxs-lookup"><span data-stu-id="887e6-2340">**buffer_ptr**: Pointer to the source buffer for the write.</span></span>
- <span data-ttu-id="887e6-2341">**size**: количество байтов для записи</span><span class="sxs-lookup"><span data-stu-id="887e6-2341">**size**: Number of bytes to write.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-2342">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-2342">Return Values</span></span>

- <span data-ttu-id="887e6-2343">**FX_SUCCESS** (0x00) — запись в файл успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="887e6-2343">**FX_SUCCESS** (0x00) Successful file write.</span></span>
- <span data-ttu-id="887e6-2344">**FX_NOT_OPEN** (0x07) — указанный файл не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-2344">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="887e6-2345">**FX_ACCESS_ERROR** (0x06) — указанный файл не открыт для записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-2345">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="887e6-2346">**FX_NO_MORE_SPACE** (0x0A) — недостаточно места на носителе для выполнения этой операции записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-2346">**FX_NO_MORE_SPACE** (0x0A) There is no more room available in the media to perform this write.</span></span>
- <span data-ttu-id="887e6-2347">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-2347">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-2348">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-2348">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="887e6-2349">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-2349">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="887e6-2350">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-2350">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="887e6-2351">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-2351">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="887e6-2352">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-2352">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="887e6-2353">**FX_PTR_ERROR** (0x18) — недопустимый указатель на файл или буфер.</span><span class="sxs-lookup"><span data-stu-id="887e6-2353">**FX_PTR_ERROR** (0x18) Invalid file or buffer pointer.</span></span>
- <span data-ttu-id="887e6-2354">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-2354">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-2355">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-2355">Allowed From</span></span>

<span data-ttu-id="887e6-2356">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-2356">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-2357">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-2357">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Write a 10 character buffer to "my_file." */

status = fx_file_write(&my_file, "1234567890", 10);

/* If status equals FX_SUCCESS, the small text string was written out to the file. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-2358">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-2358">See Also</span></span>

- <span data-ttu-id="887e6-2359">fx_file_allocate,</span><span class="sxs-lookup"><span data-stu-id="887e6-2359">fx_file_allocate,</span></span>
- <span data-ttu-id="887e6-2360">fx_file_attributes_read,</span><span class="sxs-lookup"><span data-stu-id="887e6-2360">fx_file_attributes_read,</span></span>
- <span data-ttu-id="887e6-2361">fx_file_attributes_set,</span><span class="sxs-lookup"><span data-stu-id="887e6-2361">fx_file_attributes_set,</span></span>
- <span data-ttu-id="887e6-2362">fx_file_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="887e6-2362">fx_file_best_effort_allocate,</span></span>
- <span data-ttu-id="887e6-2363">fx_file_close,</span><span class="sxs-lookup"><span data-stu-id="887e6-2363">fx_file_close,</span></span>
- <span data-ttu-id="887e6-2364">fx_file_create,</span><span class="sxs-lookup"><span data-stu-id="887e6-2364">fx_file_create,</span></span>
- <span data-ttu-id="887e6-2365">fx_file_date_time_set,</span><span class="sxs-lookup"><span data-stu-id="887e6-2365">fx_file_date_time_set,</span></span>
- <span data-ttu-id="887e6-2366">fx_file_delete,</span><span class="sxs-lookup"><span data-stu-id="887e6-2366">fx_file_delete,</span></span>
- <span data-ttu-id="887e6-2367">fx_file_extended_allocate,</span><span class="sxs-lookup"><span data-stu-id="887e6-2367">fx_file_extended_allocate,</span></span>
- <span data-ttu-id="887e6-2368">fx_file_extended_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="887e6-2368">fx_file_extended_best_effort_allocate,</span></span>
- <span data-ttu-id="887e6-2369">fx_file_extended_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="887e6-2369">fx_file_extended_relative_seek,</span></span>
- <span data-ttu-id="887e6-2370">fx_file_extended_seek,</span><span class="sxs-lookup"><span data-stu-id="887e6-2370">fx_file_extended_seek,</span></span>
- <span data-ttu-id="887e6-2371">fx_file_extended_truncate,</span><span class="sxs-lookup"><span data-stu-id="887e6-2371">fx_file_extended_truncate,</span></span>
- <span data-ttu-id="887e6-2372">fx_file_extended_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="887e6-2372">fx_file_extended_truncate_release,</span></span>
- <span data-ttu-id="887e6-2373">fx_file_open,</span><span class="sxs-lookup"><span data-stu-id="887e6-2373">fx_file_open,</span></span>
- <span data-ttu-id="887e6-2374">fx_file_read,</span><span class="sxs-lookup"><span data-stu-id="887e6-2374">fx_file_read,</span></span>
- <span data-ttu-id="887e6-2375">fx_file_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="887e6-2375">fx_file_relative_seek,</span></span>
- <span data-ttu-id="887e6-2376">fx_file_rename,</span><span class="sxs-lookup"><span data-stu-id="887e6-2376">fx_file_rename,</span></span>
- <span data-ttu-id="887e6-2377">fx_file_seek,</span><span class="sxs-lookup"><span data-stu-id="887e6-2377">fx_file_seek,</span></span>
- <span data-ttu-id="887e6-2378">fx_file_truncate,</span><span class="sxs-lookup"><span data-stu-id="887e6-2378">fx_file_truncate,</span></span>
- <span data-ttu-id="887e6-2379">fx_file_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="887e6-2379">fx_file_truncate_release,</span></span>
- <span data-ttu-id="887e6-2380">fx_file_write_notify_set,</span><span class="sxs-lookup"><span data-stu-id="887e6-2380">fx_file_write_notify_set,</span></span>
- <span data-ttu-id="887e6-2381">fx_unicode_file_create,</span><span class="sxs-lookup"><span data-stu-id="887e6-2381">fx_unicode_file_create,</span></span>
- <span data-ttu-id="887e6-2382">fx_unicode_file_rename,</span><span class="sxs-lookup"><span data-stu-id="887e6-2382">fx_unicode_file_rename,</span></span>
- <span data-ttu-id="887e6-2383">fx_unicode_name_get,</span><span class="sxs-lookup"><span data-stu-id="887e6-2383">fx_unicode_name_get,</span></span>
- <span data-ttu-id="887e6-2384">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-2384">fx_unicode_short_name_get</span></span>

## <a name="fx_file_write_notify_set"></a><span data-ttu-id="887e6-2385">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2385">fx_file_write_notify_set</span></span>

<span data-ttu-id="887e6-2386">Задает функцию уведомления о записи в файл</span><span class="sxs-lookup"><span data-stu-id="887e6-2386">Sets the file write notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-2387">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-2387">Prototype</span></span>

```c
UINT fx_file_write_notify_set(
    FX_FILE *file_ptr,
    VOID (*file_write_notify)(FX_FILE*));
```
### <a name="description"></a><span data-ttu-id="887e6-2388">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-2388">Description</span></span>

<span data-ttu-id="887e6-2389">Эта служба устанавливает функцию обратного вызова, которая вызывается после успешной операции записи в файл.</span><span class="sxs-lookup"><span data-stu-id="887e6-2389">This service installs callback function that is invoked after a successful file write operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-2390">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-2390">Input Parameters</span></span>

- <span data-ttu-id="887e6-2391">**file_ptr**: указатель на блок управления файлом</span><span class="sxs-lookup"><span data-stu-id="887e6-2391">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="887e6-2392">**file_write_notify**: устанавливаемая функция обратного вызова записи в файл</span><span class="sxs-lookup"><span data-stu-id="887e6-2392">**file_write_notify**: File write callback function to be installed.</span></span> <span data-ttu-id="887e6-2393">Задайте для функции обратного вызова значение NULL, чтобы отключить функцию обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="887e6-2393">Set the callback function to NULL disables the callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-2394">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-2394">Return Values</span></span>

- <span data-ttu-id="887e6-2395">**FX_SUCCESS** (0x00) — функция обратного вызова успешно установлена.</span><span class="sxs-lookup"><span data-stu-id="887e6-2395">**FX_SUCCESS** (0x00) Successfully installed the callback function.</span></span>
- <span data-ttu-id="887e6-2396">**FX_PTR_ERROR** (0x18) — file_ptr имеет значение NULL.</span><span class="sxs-lookup"><span data-stu-id="887e6-2396">**FX_PTR_ERROR** (0x18) file_ptr is NULL.</span></span>
- <span data-ttu-id="887e6-2397">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-2397">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-2398">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-2398">Allowed From</span></span>

<span data-ttu-id="887e6-2399">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-2399">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-2400">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-2400">Example</span></span>

```c
fx_file_write_notify_set(file_ptr, my_file_close_callback);

```

### <a name="see-also"></a><span data-ttu-id="887e6-2401">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-2401">See Also</span></span>

- <span data-ttu-id="887e6-2402">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-2402">fx_file_allocate</span></span>
- <span data-ttu-id="887e6-2403">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-2403">fx_file_attributes_read</span></span>
- <span data-ttu-id="887e6-2404">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2404">fx_file_attributes_set</span></span>
- <span data-ttu-id="887e6-2405">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-2405">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-2406">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="887e6-2406">fx_file_close</span></span>
- <span data-ttu-id="887e6-2407">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-2407">fx_file_create</span></span>
- <span data-ttu-id="887e6-2408">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2408">fx_file_date_time_set</span></span>
- <span data-ttu-id="887e6-2409">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-2409">fx_file_delete</span></span>
- <span data-ttu-id="887e6-2410">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-2410">fx_file_extended_allocate</span></span>
- <span data-ttu-id="887e6-2411">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-2411">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-2412">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-2412">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="887e6-2413">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-2413">fx_file_extended_seek</span></span>
- <span data-ttu-id="887e6-2414">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-2414">fx_file_extended_truncate</span></span>
- <span data-ttu-id="887e6-2415">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-2415">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="887e6-2416">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="887e6-2416">fx_file_open</span></span>
- <span data-ttu-id="887e6-2417">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="887e6-2417">fx_file_read</span></span>
- <span data-ttu-id="887e6-2418">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-2418">fx_file_relative_seek</span></span>
- <span data-ttu-id="887e6-2419">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-2419">fx_file_rename</span></span>
- <span data-ttu-id="887e6-2420">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-2420">fx_file_seek</span></span>
- <span data-ttu-id="887e6-2421">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-2421">fx_file_truncate</span></span>
- <span data-ttu-id="887e6-2422">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-2422">fx_file_truncate_release</span></span>
- <span data-ttu-id="887e6-2423">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="887e6-2423">fx_file_write</span></span>
- <span data-ttu-id="887e6-2424">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-2424">fx_unicode_file_create</span></span>
- <span data-ttu-id="887e6-2425">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-2425">fx_unicode_file_rename</span></span>
- <span data-ttu-id="887e6-2426">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-2426">fx_unicode_name_get</span></span>
- <span data-ttu-id="887e6-2427">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-2427">fx_unicode_short_name_get</span></span>

## <a name="fx_media_abort"></a><span data-ttu-id="887e6-2428">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="887e6-2428">fx_media_abort</span></span>

<span data-ttu-id="887e6-2429">Прерывает действия носителя</span><span class="sxs-lookup"><span data-stu-id="887e6-2429">Aborts media activities</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-2430">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-2430">Prototype</span></span>

```c
UINT fx_media_abort(FX_MEDIA *media_ptr);
```
### <a name="description"></a><span data-ttu-id="887e6-2431">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-2431">Description</span></span>

<span data-ttu-id="887e6-2432">Эта служба прерывает все текущие действия, связанные с носителем, включая закрытие всех открытых файлов, отправку запроса на прерывание соответствующему драйверу и помещение носителя в состояние прерванной работы.</span><span class="sxs-lookup"><span data-stu-id="887e6-2432">This service aborts all current activities associated with the media, including closing all open files, sending an abort request to the associated driver, and placing the media in an aborted state.</span></span> <span data-ttu-id="887e6-2433">Эта служба обычно вызывается при обнаружении ошибок ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="887e6-2433">This service is typically called when I/O errors are detected.</span></span>

> [!WARNING]
> <span data-ttu-id="887e6-2434">*Чтобы повторно использовать носитель после выполнения операции прерывания, его необходимо открыть повторно.*</span><span class="sxs-lookup"><span data-stu-id="887e6-2434">*The media must be re-opened to use it again after an abort operation is performed.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-2435">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-2435">Input Parameters</span></span>

- <span data-ttu-id="887e6-2436">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-2436">**media_ptr**: Pointer to media control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-2437">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-2437">Return Values</span></span>

- <span data-ttu-id="887e6-2438">**FX_SUCCESS** (0x00) — работа носителя успешно прервана.</span><span class="sxs-lookup"><span data-stu-id="887e6-2438">**FX_SUCCESS** (0x00) Successful media abort.</span></span>
- <span data-ttu-id="887e6-2439">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-2439">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="887e6-2440">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-2440">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="887e6-2441">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-2441">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-2442">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-2442">Allowed From</span></span>

<span data-ttu-id="887e6-2443">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-2443">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-2444">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-2444">Example</span></span>

```c
FX_MEDIA    my_media;
UINT        status;
/* Abort all activity associated with "my_media". */

status = fx_media_abort(&my_media);

/* If status equals FX_SUCCESS, all activity
    associated with the media has been aborted. */

```

### <a name="see-also"></a><span data-ttu-id="887e6-2445">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-2445">See Also</span></span>

- <span data-ttu-id="887e6-2446">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="887e6-2446">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="887e6-2447">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="887e6-2447">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="887e6-2448">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="887e6-2448">fx_media_check</span></span>
- <span data-ttu-id="887e6-2449">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="887e6-2449">fx_media_close</span></span>
- <span data-ttu-id="887e6-2450">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2450">fx_media_close_notify_set</span></span>
- <span data-ttu-id="887e6-2451">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="887e6-2451">fx_media_exFAT_format</span></span>
- <span data-ttu-id="887e6-2452">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-2452">fx_media_extended_space_available</span></span>
- <span data-ttu-id="887e6-2453">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="887e6-2453">fx_media_flush</span></span>
- <span data-ttu-id="887e6-2454">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="887e6-2454">fx_media_format</span></span>
- <span data-ttu-id="887e6-2455">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="887e6-2455">fx_media_open</span></span>
- <span data-ttu-id="887e6-2456">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2456">fx_media_open_notify_set</span></span>
- <span data-ttu-id="887e6-2457">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="887e6-2457">fx_media_read</span></span>
- <span data-ttu-id="887e6-2458">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-2458">fx_media_space_available</span></span>
- <span data-ttu-id="887e6-2459">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="887e6-2459">fx_media_volume_get</span></span>
- <span data-ttu-id="887e6-2460">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2460">fx_media_volume_set</span></span>
- <span data-ttu-id="887e6-2461">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="887e6-2461">fx_media_write</span></span>
- <span data-ttu-id="887e6-2462">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="887e6-2462">fx_system_initialize</span></span>

## <a name="fx_media_cache_invalidate"></a><span data-ttu-id="887e6-2463">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="887e6-2463">fx_media_cache_invalidate</span></span>

<span data-ttu-id="887e6-2464">Делает недействительным кэш логического сектора</span><span class="sxs-lookup"><span data-stu-id="887e6-2464">Invalidates logical sector cache</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-2465">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-2465">Prototype</span></span>

```c
UINT fx_media_cache_invalidate(FX_MEDIA *media_ptr);
```

### <a name="description"></a><span data-ttu-id="887e6-2466">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-2466">Description</span></span>

<span data-ttu-id="887e6-2467">Эта служба очищает все "грязные" секторы в кэше, а затем делает недействительным весь кэш логического сектора.</span><span class="sxs-lookup"><span data-stu-id="887e6-2467">This service flushes all dirty sectors in the cache and then invalidates the entire logical sector cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-2468">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-2468">Input Parameters</span></span>

- <span data-ttu-id="887e6-2469">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-2469">**media_ptr**: Pointer to media control block</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-2470">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-2470">Return Values</span></span>

- <span data-ttu-id="887e6-2471">**FX_SUCCESS** (0x00) — кэш носителя успешно сделан недействительным.</span><span class="sxs-lookup"><span data-stu-id="887e6-2471">**FX_SUCCESS** (0x00) Successful media cache invalidate.</span></span>
- <span data-ttu-id="887e6-2472">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-2472">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="887e6-2473">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-2473">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-2474">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или временной памяти.</span><span class="sxs-lookup"><span data-stu-id="887e6-2474">**FX_PTR_ERROR** (0x18) Invalid media or scratch pointer.</span></span>
- <span data-ttu-id="887e6-2475">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-2475">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-2476">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-2476">Allowed From</span></span>

<span data-ttu-id="887e6-2477">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-2477">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-2478">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-2478">Example</span></span>

```c
FX_MEDIA     my_media;

/* Invalidate the cache of the media. */
status = fx_media_cache_invalidate(&my_media);

/* If status is FX_SUCCESS the cache in the media
    was successfully flushed and invalidated. */

```

### <a name="see-also"></a><span data-ttu-id="887e6-2479">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-2479">See Also</span></span>

- <span data-ttu-id="887e6-2480">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="887e6-2480">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="887e6-2481">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="887e6-2481">fx_media_abort</span></span>
- <span data-ttu-id="887e6-2482">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="887e6-2482">fx_media_check</span></span>
- <span data-ttu-id="887e6-2483">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="887e6-2483">fx_media_close</span></span>
- <span data-ttu-id="887e6-2484">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2484">fx_media_close_notify_set</span></span>
- <span data-ttu-id="887e6-2485">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="887e6-2485">fx_media_exFAT_format</span></span>
- <span data-ttu-id="887e6-2486">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-2486">fx_media_extended_space_available</span></span>
- <span data-ttu-id="887e6-2487">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="887e6-2487">fx_media_flush</span></span>
- <span data-ttu-id="887e6-2488">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="887e6-2488">fx_media_format</span></span>
- <span data-ttu-id="887e6-2489">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="887e6-2489">fx_media_open</span></span>
- <span data-ttu-id="887e6-2490">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2490">fx_media_open_notify_set</span></span>
- <span data-ttu-id="887e6-2491">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="887e6-2491">fx_media_read</span></span>
- <span data-ttu-id="887e6-2492">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-2492">fx_media_space_available</span></span>
- <span data-ttu-id="887e6-2493">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="887e6-2493">fx_media_volume_get</span></span>
- <span data-ttu-id="887e6-2494">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2494">fx_media_volume_set</span></span>
- <span data-ttu-id="887e6-2495">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="887e6-2495">fx_media_write</span></span>
- <span data-ttu-id="887e6-2496">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="887e6-2496">fx_system_initialize</span></span>

## <a name="fx_media_check"></a><span data-ttu-id="887e6-2497">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="887e6-2497">fx_media_check</span></span>

<span data-ttu-id="887e6-2498">Проверяет наличие ошибок на носителе</span><span class="sxs-lookup"><span data-stu-id="887e6-2498">Checks media for errors</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-2499">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-2499">Prototype</span></span>

```c
UINT fx_media_check(
    FX_MEDIA *media_ptr,
    UCHAR *scratch_memory_ptr,
    ULONG scratch_memory_size,
    ULONG error_correction_option,
    ULONG *errors_detected_ptr);
```
### <a name="description"></a><span data-ttu-id="887e6-2500">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-2500">Description</span></span>

<span data-ttu-id="887e6-2501">Эта служба проверяет указанный носитель на наличие базовых структурных ошибок, включая перекрестные ссылки на файлы и каталоги, недопустимые цепочки FAT и потерянные кластеры.</span><span class="sxs-lookup"><span data-stu-id="887e6-2501">This service checks the specified media for basic structural errors, including file/directory cross-linking, invalid FAT chains, and lost clusters.</span></span> <span data-ttu-id="887e6-2502">Эта служба также предоставляет возможность исправить обнаруженные ошибки.</span><span class="sxs-lookup"><span data-stu-id="887e6-2502">This service also provides the capability to correct detected errors.</span></span>

<span data-ttu-id="887e6-2503">Служба fx_media_check требует наличия вспомогательной памяти для предварительного анализа глубины вложения каталогов и файлов на носителе.</span><span class="sxs-lookup"><span data-stu-id="887e6-2503">The fx_media_check service requires scratch memory for its depth-first analysis of directories and files in the media.</span></span> <span data-ttu-id="887e6-2504">В частности, вспомогательная память, предоставленная службе проверки носителей, должна быть достаточно большой для хранения нескольких записей каталога, структуры данных для помещения в стек текущей позиции записи каталога перед входом в подкаталоги и, наконец, логической битовой карты FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-2504">Specifically, the scratch memory supplied to the media check service must be large enough to hold several directory entries, a data structure to "stack" the current directory entry position before entering into subdirectories, and finally the logical FAT bit map.</span></span> <span data-ttu-id="887e6-2505">Объем вспомогательной памяти должен составлять по крайней мере 512–1024 байт плюс память для логической файловой системы FAT, для которой требуется столько битов, сколько кластеров находится в носителе.</span><span class="sxs-lookup"><span data-stu-id="887e6-2505">The scratch memory should be at least 512-1024 bytes plus memory for the logical FAT bit map, which requires as many bits as there are clusters in the media.</span></span> <span data-ttu-id="887e6-2506">Например, устройству с 8000 кластерам потребовалось бы 1000 байт для представления и, таким образом, требуемый размер общей временной области составляет порядка 2048 байт.</span><span class="sxs-lookup"><span data-stu-id="887e6-2506">For example, a device with 8000 clusters would require 1000 bytes to represent and thus require a total scratch area on the order of 2048 bytes.</span></span>

> [!WARNING]
> <span data-ttu-id="887e6-2507">*Эту службу следует вызывать только сразу после fx_media_open и без каких бы то ни было других действий с файловой системой.*</span><span class="sxs-lookup"><span data-stu-id="887e6-2507">*This service should only be called immediately after fx_media_open and without any other file system activity.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-2508">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-2508">Input Parameters</span></span>

- <span data-ttu-id="887e6-2509">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-2509">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="887e6-2510">**scratch_memory_ptr**: указатель на начало вспомогательной памяти</span><span class="sxs-lookup"><span data-stu-id="887e6-2510">**scratch_memory_ptr**: Pointer to the start of scratch memory.</span></span>
- <span data-ttu-id="887e6-2511">**scratch_memory_size**: размер вспомогательной памяти в байтах</span><span class="sxs-lookup"><span data-stu-id="887e6-2511">**scratch_memory_size**: Size of scratch memory in bytes.</span></span>
- <span data-ttu-id="887e6-2512">**error_correction_option**: биты при исправлении ошибок, если бит задан, выполняется исправление ошибок</span><span class="sxs-lookup"><span data-stu-id="887e6-2512">**error_correction_option**: Error correction option bits, when the bit is set, error correction is performed.</span></span> <span data-ttu-id="887e6-2513">Биты параметра исправления ошибок определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="887e6-2513">The error correction option bits are defined as follows:</span></span>
  - <span data-ttu-id="887e6-2514">FX_FAT_CHAIN_ERROR (0x01)</span><span class="sxs-lookup"><span data-stu-id="887e6-2514">FX_FAT_CHAIN_ERROR (0x01)</span></span>
  - <span data-ttu-id="887e6-2515">FX_DIRECTORY_ERROR (0x02)</span><span class="sxs-lookup"><span data-stu-id="887e6-2515">FX_DIRECTORY_ERROR (0x02)</span></span>
  - <span data-ttu-id="887e6-2516">FX_LOST_CLUSTER_ERROR (0x04): просто ИЛИ вместе с необходимыми параметрами исправления ошибок</span><span class="sxs-lookup"><span data-stu-id="887e6-2516">FX_LOST_CLUSTER_ERROR (0x04) Simply OR together the required error correction options.</span></span> <span data-ttu-id="887e6-2517">Если исправление ошибок не требуется, необходимо указать значение 0.</span><span class="sxs-lookup"><span data-stu-id="887e6-2517">If no error correction is required, a value of 0 should be supplied.</span></span>
- <span data-ttu-id="887e6-2518">**errors_detected_ptr**: назначение для битов обнаружения ошибок, как определено ниже.</span><span class="sxs-lookup"><span data-stu-id="887e6-2518">**errors_detected_ptr**: Destination for error detection bits, as defined below:</span></span>
  - <span data-ttu-id="887e6-2519">FX_FAT_CHAIN_ERROR (0x01)</span><span class="sxs-lookup"><span data-stu-id="887e6-2519">FX_FAT_CHAIN_ERROR (0x01)</span></span>
  - <span data-ttu-id="887e6-2520">FX_DIRECTORY_ERROR (0x02) FX_LOST_CLUSTER_ERROR (0x04)</span><span class="sxs-lookup"><span data-stu-id="887e6-2520">FX_DIRECTORY_ERROR (0x02) FX_LOST_CLUSTER_ERROR (0x04)</span></span>
  - <span data-ttu-id="887e6-2521">FX_FILE_SIZE_ERROR (0x08)</span><span class="sxs-lookup"><span data-stu-id="887e6-2521">FX_FILE_SIZE_ERROR (0x08)</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-2522">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-2522">Return Values</span></span>

- <span data-ttu-id="887e6-2523">**FX_SUCCESS** (0x00) — носитель успешно проверен; ознакомьтесь со сведениями об обнаруженных ошибках.</span><span class="sxs-lookup"><span data-stu-id="887e6-2523">**FX_SUCCESS** (0x00) Successful media check, view the errors detected destination for details.</span></span>
- <span data-ttu-id="887e6-2524">**FX_ACCESS_ERROR** (0x06) — не удается выполнить проверку с открытыми файлами.</span><span class="sxs-lookup"><span data-stu-id="887e6-2524">**FX_ACCESS_ERROR** (0x06) Unable to perform check with open files.</span></span>
- <span data-ttu-id="887e6-2525">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-2525">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="887e6-2526">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-2526">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="887e6-2527">**FX_NO_MORE_SPACE** (0x0A) — на носителе больше нет места.</span><span class="sxs-lookup"><span data-stu-id="887e6-2527">**FX_NO_MORE_SPACE** (0x0A) No more space on the media.</span></span>
- <span data-ttu-id="887e6-2528">**FX_NOT_ENOUGH_MEMORY** (0x91) — указан недостаточный размер вспомогательной памяти.</span><span class="sxs-lookup"><span data-stu-id="887e6-2528">**FX_NOT_ENOUGH_MEMORY** (0x91) Supplied scratch memory is not large enough.</span></span>
- <span data-ttu-id="887e6-2529">**FX_ERROR_NOT_FIXED** (0x93) — повреждение корневого каталога FAT32, которое не удалось исправить.</span><span class="sxs-lookup"><span data-stu-id="887e6-2529">**FX_ERROR_NOT_FIXED** (0x93) Corruption of FAT32 root directory that could not be fixed.</span></span>
- <span data-ttu-id="887e6-2530">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-2530">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-2531">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-2531">**FX_SECTOR_INVALID** (0x89) Sector is invalid.</span></span>
- <span data-ttu-id="887e6-2532">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или временной памяти.</span><span class="sxs-lookup"><span data-stu-id="887e6-2532">**FX_PTR_ERROR** (0x18) Invalid media or scratch pointer.</span></span>
- <span data-ttu-id="887e6-2533">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-2533">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="887e6-2534">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-2534">Allowed From</span></span>

<span data-ttu-id="887e6-2535">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-2535">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-2536">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-2536">Example</span></span>

```c
FX_MEDIA         my_media;
ULONG             detected_errors;
UCHAR             sratch_memory[4096];

/* Check the media and correct all errors. */

status = fx_media_check(&my_media, sratch_memory, 4096,
                        FX_FAT_CHAIN_ERROR |
                        FX_DIRECTORY_ERROR |
                        FX_LOST_CLUSTER_ERROR, &detected_errors);

/* If status is FX_SUCCESS and detected_errors is 0,
    the media was successfully checked and found to be error free. */

```

### <a name="see-also"></a><span data-ttu-id="887e6-2537">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-2537">See Also</span></span>

- <span data-ttu-id="887e6-2538">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="887e6-2538">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="887e6-2539">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="887e6-2539">fx_media_abort</span></span>
- <span data-ttu-id="887e6-2540">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="887e6-2540">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="887e6-2541">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="887e6-2541">fx_media_close</span></span>
- <span data-ttu-id="887e6-2542">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2542">fx_media_close_notify_set</span></span>
- <span data-ttu-id="887e6-2543">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="887e6-2543">fx_media_exFAT_format</span></span>
- <span data-ttu-id="887e6-2544">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-2544">fx_media_extended_space_available</span></span>
- <span data-ttu-id="887e6-2545">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="887e6-2545">fx_media_flush</span></span>
- <span data-ttu-id="887e6-2546">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="887e6-2546">fx_media_format</span></span>
- <span data-ttu-id="887e6-2547">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="887e6-2547">fx_media_open</span></span>
- <span data-ttu-id="887e6-2548">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2548">fx_media_open_notify_set</span></span>
- <span data-ttu-id="887e6-2549">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="887e6-2549">fx_media_read</span></span>
- <span data-ttu-id="887e6-2550">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-2550">fx_media_space_available</span></span>
- <span data-ttu-id="887e6-2551">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="887e6-2551">fx_media_volume_get</span></span>
- <span data-ttu-id="887e6-2552">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2552">fx_media_volume_set</span></span>
- <span data-ttu-id="887e6-2553">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="887e6-2553">fx_media_write</span></span>
- <span data-ttu-id="887e6-2554">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="887e6-2554">fx_system_initialize</span></span>

## <a name="fx_media_close"></a><span data-ttu-id="887e6-2555">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="887e6-2555">fx_media_close</span></span>

<span data-ttu-id="887e6-2556">Закрывает носитель</span><span class="sxs-lookup"><span data-stu-id="887e6-2556">Closes media</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-2557">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-2557">Prototype</span></span>

```c
UINT fx_media_close(FX_MEDIA *media_ptr);
```
### <a name="description"></a><span data-ttu-id="887e6-2558">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-2558">Description</span></span>

<span data-ttu-id="887e6-2559">Эта служба закрывает указанный носитель.</span><span class="sxs-lookup"><span data-stu-id="887e6-2559">This service closes the specified media.</span></span> <span data-ttu-id="887e6-2560">В процессе закрытия носителя все открытые файлы закрываются, а оставшиеся буферы записываются на физический носитель.</span><span class="sxs-lookup"><span data-stu-id="887e6-2560">In the process of closing the media, all open files are closed and any remaining buffers are flushed to the physical media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-2561">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-2561">Input Parameters</span></span>

- <span data-ttu-id="887e6-2562">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-2562">**media_ptr**: Pointer to media control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-2563">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-2563">Return Values</span></span>

- <span data-ttu-id="887e6-2564">**FX_SUCCESS** (0x00) — носитель успешно закрыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-2564">**FX_SUCCESS** (0x00) Successful media close.</span></span>
- <span data-ttu-id="887e6-2565">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-2565">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="887e6-2566">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-2566">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-2567">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-2567">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="887e6-2568">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-2568">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-2569">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-2569">Allowed From</span></span>

<span data-ttu-id="887e6-2570">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-2570">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-2571">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-2571">Example</span></span>

```c
FX_MEDIA    my_media;
UINT        status;
/* Close "my_media". */

status = fx_media_close(&my_media);

/* If status equals FX_SUCCESS, "my_media" is closed. */

```

### <a name="see-also"></a><span data-ttu-id="887e6-2572">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-2572">See Also</span></span>

- <span data-ttu-id="887e6-2573">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="887e6-2573">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="887e6-2574">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="887e6-2574">fx_media_abort</span></span>
- <span data-ttu-id="887e6-2575">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="887e6-2575">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="887e6-2576">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="887e6-2576">fx_media_check</span></span>
- <span data-ttu-id="887e6-2577">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2577">fx_media_close_notify_set</span></span>
- <span data-ttu-id="887e6-2578">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="887e6-2578">fx_media_exFAT_format</span></span>
- <span data-ttu-id="887e6-2579">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-2579">fx_media_extended_space_available</span></span>
- <span data-ttu-id="887e6-2580">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="887e6-2580">fx_media_flush</span></span>
- <span data-ttu-id="887e6-2581">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="887e6-2581">fx_media_format</span></span>
- <span data-ttu-id="887e6-2582">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="887e6-2582">fx_media_open</span></span>
- <span data-ttu-id="887e6-2583">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2583">fx_media_open_notify_set</span></span>
- <span data-ttu-id="887e6-2584">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="887e6-2584">fx_media_read</span></span>
- <span data-ttu-id="887e6-2585">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-2585">fx_media_space_available</span></span>
- <span data-ttu-id="887e6-2586">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="887e6-2586">fx_media_volume_get</span></span>
- <span data-ttu-id="887e6-2587">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2587">fx_media_volume_set</span></span>
- <span data-ttu-id="887e6-2588">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="887e6-2588">fx_media_write</span></span>
- <span data-ttu-id="887e6-2589">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="887e6-2589">fx_system_initialize</span></span>

## <a name="fx_media_close_notify_set"></a><span data-ttu-id="887e6-2590">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2590">fx_media_close_notify_set</span></span>

<span data-ttu-id="887e6-2591">Задает функцию уведомления о закрытии носителя</span><span class="sxs-lookup"><span data-stu-id="887e6-2591">Sets the media close notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-2592">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-2592">Prototype</span></span>

```c
UINT fx_media_close_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_close_notify)(FX_MEDIA*));
```

### <a name="description"></a><span data-ttu-id="887e6-2593">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-2593">Description</span></span>

<span data-ttu-id="887e6-2594">Эта служба задает функцию обратного вызова уведомления, которая будет вызываться после успешного закрытия носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-2594">This service sets a notify callback function which will be invoked after a media is successfully closed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-2595">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-2595">Input Parameters</span></span>

- <span data-ttu-id="887e6-2596">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-2596">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="887e6-2597">**media_close_notify**: функция обратного вызова уведомления о закрытии носителя для установки</span><span class="sxs-lookup"><span data-stu-id="887e6-2597">**media_close_notify**: Media close notify callback function to be installed.</span></span> <span data-ttu-id="887e6-2598">Передача значения NULL в качестве функции обратного вызова отключает обратный вызов закрытия носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-2598">Passing NULL as the callback function disables the media close callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-2599">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-2599">Return Values</span></span>

- <span data-ttu-id="887e6-2600">**FX_SUCCESS** (0x00) — функция обратного вызова успешно установлена.</span><span class="sxs-lookup"><span data-stu-id="887e6-2600">**FX_SUCCESS** (0x00) Successfully installed the callback function.</span></span>
- <span data-ttu-id="887e6-2601">**FX_PTR_ERROR** (0x18) — параметр media_ptr имеет значение NULL.</span><span class="sxs-lookup"><span data-stu-id="887e6-2601">**FX_PTR_ERROR** (0x18) media_ptr is NULL.</span></span>
- <span data-ttu-id="887e6-2602">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-2602">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-2603">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-2603">Allowed From</span></span>

<span data-ttu-id="887e6-2604">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-2604">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-2605">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-2605">Example</span></span>

```c
fx_media_close_notify_set(media_ptr, my_media_close_callback);

```
### <a name="see-also"></a><span data-ttu-id="887e6-2606">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-2606">See Also</span></span>

- <span data-ttu-id="887e6-2607">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="887e6-2607">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="887e6-2608">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="887e6-2608">fx_media_abort</span></span>
- <span data-ttu-id="887e6-2609">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="887e6-2609">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="887e6-2610">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="887e6-2610">fx_media_check</span></span>
- <span data-ttu-id="887e6-2611">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="887e6-2611">fx_media_close</span></span>
- <span data-ttu-id="887e6-2612">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="887e6-2612">fx_media_exFAT_format</span></span>
- <span data-ttu-id="887e6-2613">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-2613">fx_media_extended_space_available</span></span>
- <span data-ttu-id="887e6-2614">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="887e6-2614">fx_media_flush</span></span>
- <span data-ttu-id="887e6-2615">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="887e6-2615">fx_media_format</span></span>
- <span data-ttu-id="887e6-2616">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="887e6-2616">fx_media_open</span></span>
- <span data-ttu-id="887e6-2617">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2617">fx_media_open_notify_set</span></span>
- <span data-ttu-id="887e6-2618">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="887e6-2618">fx_media_read</span></span>
- <span data-ttu-id="887e6-2619">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-2619">fx_media_space_available</span></span>
- <span data-ttu-id="887e6-2620">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="887e6-2620">fx_media_volume_get</span></span>
- <span data-ttu-id="887e6-2621">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2621">fx_media_volume_set</span></span>
- <span data-ttu-id="887e6-2622">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="887e6-2622">fx_media_write</span></span>
- <span data-ttu-id="887e6-2623">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="887e6-2623">fx_system_initialize</span></span>

## <a name="fx_media_exfat_format"></a><span data-ttu-id="887e6-2624">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="887e6-2624">fx_media_exFAT_format</span></span>

<span data-ttu-id="887e6-2625">Форматирует носитель</span><span class="sxs-lookup"><span data-stu-id="887e6-2625">Formats media</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-2626">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-2626">Prototype</span></span>

```c
UINT fx_media_exFAT_format(
    FX_MEDIA *media_ptr,
    VOID (*driver)(FX_MEDIA *media),
    VOID *driver_info_ptr, 
    UCHAR *memory_ptr,
    UINT memory_size, 
    CHAR *volume_name,
    UINT number_of_fats,
    ULONG64 hidden_sectors, 
    ULONG64 total_sectors,
    UINT bytes_per_sector, 
    UINT sectors_per_cluster,
    UINT volume_serial_number, 
    UINT boundary_unit);
```
### <a name="description"></a><span data-ttu-id="887e6-2627">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-2627">Description</span></span>

<span data-ttu-id="887e6-2628">Эта служба форматирует указанный носитель в формате, совместимом с exFAT, на основе заданных параметров.</span><span class="sxs-lookup"><span data-stu-id="887e6-2628">This service formats the supplied media in an exFAT compatible manner based on the supplied parameters.</span></span> <span data-ttu-id="887e6-2629">Эту службу следует вызывать перед открытием носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-2629">This service must be called prior to opening the media.</span></span>

> [!WARNING]
> <span data-ttu-id="887e6-2630">*Форматирование уже отформатированного носителя фактически приводит к удалению всех файлов и каталогов на нем.*</span><span class="sxs-lookup"><span data-stu-id="887e6-2630">*Formatting an already formatted media effectively erases all files and directories on the media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-2631">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-2631">Input Parameters</span></span>

- <span data-ttu-id="887e6-2632">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-2632">**media_ptr**: Pointer to media control block.</span></span> <span data-ttu-id="887e6-2633">Он используется только для предоставления некоторых основных сведений, необходимых для функционирования драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-2633">This is used only to provide some basic information necessary for the driver to operate.</span></span>
- <span data-ttu-id="887e6-2634">**driver**: указатель на драйвер ввода-вывода для этого носителя</span><span class="sxs-lookup"><span data-stu-id="887e6-2634">**driver**: Pointer to the I/O driver for this media.</span></span> <span data-ttu-id="887e6-2635">Обычно это тот же драйвер, который передается последующему вызову fx_media_open.</span><span class="sxs-lookup"><span data-stu-id="887e6-2635">This will typically be the same driver supplied to the subsequent fx_media_open call.</span></span>
- <span data-ttu-id="887e6-2636">**driver_info_ptr**: указатель на необязательные сведения, которые может использовать драйвер ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="887e6-2636">**driver_info_ptr**: Pointer to optional information that the I/O driver may utilize.</span></span>
- <span data-ttu-id="887e6-2637">**memory_ptr**: указатель на рабочую память для носителя</span><span class="sxs-lookup"><span data-stu-id="887e6-2637">**memory_ptr**: Pointer to the working memory for the media.</span></span> <span data-ttu-id="887e6-2638">memory_size: указывает размер рабочей памяти носителя</span><span class="sxs-lookup"><span data-stu-id="887e6-2638">memory_size Specifies the size of the working media memory.</span></span> <span data-ttu-id="887e6-2639">Размер должен быть не меньше размера сектора носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-2639">The size must be at least as large as the media's sector size.</span></span>
- <span data-ttu-id="887e6-2640">**volume_name**: указатель на строку имени тома (не более 11 символов)</span><span class="sxs-lookup"><span data-stu-id="887e6-2640">**volume_name**: Pointer to the volume name string, which is a maximum of 11 characters.</span></span>
- <span data-ttu-id="887e6-2641">**number_of_fats**: количество FAT на носителе</span><span class="sxs-lookup"><span data-stu-id="887e6-2641">**number_of_fats**: Number of FATs on the media.</span></span> <span data-ttu-id="887e6-2642">Текущая реализация поддерживает одну FAT на носителе.</span><span class="sxs-lookup"><span data-stu-id="887e6-2642">Current implementation supports one FAT on the media.</span></span>
- <span data-ttu-id="887e6-2643">**hidden_sectors**: количество секторов, скрытых перед загрузочным сектором этого носителя</span><span class="sxs-lookup"><span data-stu-id="887e6-2643">**hidden_sectors**: Number of sectors hidden before this media's boot sector.</span></span> <span data-ttu-id="887e6-2644">Это характерно при наличии нескольких разделов.</span><span class="sxs-lookup"><span data-stu-id="887e6-2644">This is typical when multiple partitions are present.</span></span>
- <span data-ttu-id="887e6-2645">**total_sectors**: общее количество секторов на носителе</span><span class="sxs-lookup"><span data-stu-id="887e6-2645">**total_sectors**: Total number of sectors in the media.</span></span>
- <span data-ttu-id="887e6-2646">**bytes_per_sector**: число байтов на сектор (обычно 512)</span><span class="sxs-lookup"><span data-stu-id="887e6-2646">**bytes_per_sector**: Number of bytes per sector, which is typically 512.</span></span> <span data-ttu-id="887e6-2647">Для FileX требуется, чтобы оно было кратным 32.</span><span class="sxs-lookup"><span data-stu-id="887e6-2647">FileX requires this to be a multiple of 32.</span></span>
- <span data-ttu-id="887e6-2648">**sectors_per_cluster**: количество секторов в каждом кластере</span><span class="sxs-lookup"><span data-stu-id="887e6-2648">**sectors_per_cluster**: Number of sectors in each cluster.</span></span> <span data-ttu-id="887e6-2649">Кластер является минимальной единицей размещения в файловой системе FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-2649">The cluster is the minimum allocation unit in a FAT file system.</span></span>
- <span data-ttu-id="887e6-2650">**volumne_serial_number**: серийный номер, используемый для этого тома</span><span class="sxs-lookup"><span data-stu-id="887e6-2650">**volumne_serial_number**: Serial number to be used for this volume.</span></span>
- <span data-ttu-id="887e6-2651">**boundary_unit**: размер для выравнивания области физических данных (в количестве секторов)</span><span class="sxs-lookup"><span data-stu-id="887e6-2651">**boundary_unit**: Physical data area alignment size, in number of sectors.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-2652">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-2652">Return Values</span></span>

- <span data-ttu-id="887e6-2653">**FX_SUCCESS** (0x00) — носитель успешно отформатирован.</span><span class="sxs-lookup"><span data-stu-id="887e6-2653">**FX_SUCCESS** (0x00) Successful media format.</span></span>
- <span data-ttu-id="887e6-2654">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-2654">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-2655">**FX_PTR_ERROR** (0x18) — недопустимый носитель, драйвер или указатель на память.</span><span class="sxs-lookup"><span data-stu-id="887e6-2655">**FX_PTR_ERROR** (0x18) Invalid media, driver, or memory pointer.</span></span>
- <span data-ttu-id="887e6-2656">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-2656">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-2657">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-2657">Allowed From</span></span>

<span data-ttu-id="887e6-2658">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-2658">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-2659">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-2659">Example</span></span>

```c
FX_MEDIA             sd_card;
UCHAR                 media_memory[512];

/* Format a 64GB SD card with exFAT file system. The media has
    been properly partitioned, with the partition starts from sector 32768.
    For 64GB, there are total of 120913920 sectors, each sector 512 bytes. */

status = fx_media_exFAT_format(&sd_card, _fx_sd_driver,
                                driver_information, media_memory,
                                sizeof(media_memory),
                                "exFAT_DISK" /* Volume Name */,
                                1 /* Number of FATs */,
                                32768 /* Hidden sectors */,
                                120913920 /* Total sectors */,
                                512 /* Sector size */,
                                256 /* Sectors per cluster */,
                                12345 /* Volume ID */,
                                8192 /* Boundary unit */);

/* If status is FX_SUCCESS, the media was successfully formatted. */

```

### <a name="see-also"></a><span data-ttu-id="887e6-2660">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-2660">See Also</span></span>

- <span data-ttu-id="887e6-2661">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="887e6-2661">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="887e6-2662">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="887e6-2662">fx_media_abort</span></span>
- <span data-ttu-id="887e6-2663">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="887e6-2663">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="887e6-2664">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="887e6-2664">fx_media_check</span></span>
- <span data-ttu-id="887e6-2665">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="887e6-2665">fx_media_close</span></span>
- <span data-ttu-id="887e6-2666">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2666">fx_media_close_notify_set</span></span>
- <span data-ttu-id="887e6-2667">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-2667">fx_media_extended_space_available</span></span>
- <span data-ttu-id="887e6-2668">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="887e6-2668">fx_media_flush</span></span>
- <span data-ttu-id="887e6-2669">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="887e6-2669">fx_media_format</span></span>
- <span data-ttu-id="887e6-2670">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="887e6-2670">fx_media_open</span></span>
- <span data-ttu-id="887e6-2671">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2671">fx_media_open_notify_set</span></span>
- <span data-ttu-id="887e6-2672">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="887e6-2672">fx_media_read</span></span>
- <span data-ttu-id="887e6-2673">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-2673">fx_media_space_available</span></span>
- <span data-ttu-id="887e6-2674">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="887e6-2674">fx_media_volume_get</span></span>
- <span data-ttu-id="887e6-2675">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2675">fx_media_volume_set</span></span>
- <span data-ttu-id="887e6-2676">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="887e6-2676">fx_media_write</span></span>
- <span data-ttu-id="887e6-2677">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="887e6-2677">fx_system_initialize</span></span>

## <a name="fx_media_extended_space_available"></a><span data-ttu-id="887e6-2678">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-2678">fx_media_extended_space_available</span></span>

<span data-ttu-id="887e6-2679">Возвращает доступное пространство на носителе</span><span class="sxs-lookup"><span data-stu-id="887e6-2679">Returns available media space</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-2680">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-2680">Prototype</span></span>

```c
UINT fx_media_extended_space_available(
    FX_MEDIA *media_ptr,
    ULONG64 *available_bytes_ptr);
```
### <a name="description"></a><span data-ttu-id="887e6-2681">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-2681">Description</span></span>

<span data-ttu-id="887e6-2682">Эта служба возвращает число байтов, доступных на носителе.</span><span class="sxs-lookup"><span data-stu-id="887e6-2682">This service returns the number of bytes available in the media.</span></span>

<span data-ttu-id="887e6-2683">Эта служба разработана для exFAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-2683">This service is designed for exFAT.</span></span> <span data-ttu-id="887e6-2684">Указатель на параметр *available_bytes* принимает значение 64-разрядного целого числа, которое позволяет вызывающему объекту работать с носителями объемом свыше 4 ГБ.</span><span class="sxs-lookup"><span data-stu-id="887e6-2684">The pointer to *available_bytes* parameter takes a 64-bit integer value, which allows the caller to work with media beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-2685">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-2685">Input Parameters</span></span>

- <span data-ttu-id="887e6-2686">**media_ptr**: указатель на открытый ранее носитель</span><span class="sxs-lookup"><span data-stu-id="887e6-2686">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="887e6-2687">**available_bytes_ptr**: число байтов, доступное на носителе</span><span class="sxs-lookup"><span data-stu-id="887e6-2687">**available_bytes_ptr**: Available bytes left in the media.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-2688">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-2688">Return Values</span></span>

- <span data-ttu-id="887e6-2689">**FX_SUCCESS** (0x00) — доступное место на носителе успешно получено.</span><span class="sxs-lookup"><span data-stu-id="887e6-2689">**FX_SUCCESS** (0x00) Successfully retrieved space available on the media.</span></span>
- <span data-ttu-id="887e6-2690">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-2690">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="887e6-2691">**FX_PTR_ERROR** (0x18) — недопустимый указатель на носитель, или доступное количество байтов имеет значение NULL.</span><span class="sxs-lookup"><span data-stu-id="887e6-2691">**FX_PTR_ERROR** (0x18) Invalid media pointer or available bytes pointer is NULL.</span></span>
- <span data-ttu-id="887e6-2692">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-2692">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-2693">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-2693">Allowed From</span></span>

<span data-ttu-id="887e6-2694">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-2694">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-2695">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-2695">Example</span></span>

```c
FX_MEDIA        my_media;
ULONG64            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_extended_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a><span data-ttu-id="887e6-2696">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-2696">See Also</span></span>

- <span data-ttu-id="887e6-2697">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="887e6-2697">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="887e6-2698">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="887e6-2698">fx_media_abort</span></span>
- <span data-ttu-id="887e6-2699">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="887e6-2699">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="887e6-2700">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="887e6-2700">fx_media_check</span></span>
- <span data-ttu-id="887e6-2701">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="887e6-2701">fx_media_close</span></span>
- <span data-ttu-id="887e6-2702">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2702">fx_media_close_notify_set</span></span>
- <span data-ttu-id="887e6-2703">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="887e6-2703">fx_media_exFAT_format</span></span>
- <span data-ttu-id="887e6-2704">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="887e6-2704">fx_media_flush</span></span>
- <span data-ttu-id="887e6-2705">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="887e6-2705">fx_media_format</span></span>
- <span data-ttu-id="887e6-2706">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="887e6-2706">fx_media_open</span></span>
- <span data-ttu-id="887e6-2707">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2707">fx_media_open_notify_set</span></span>
- <span data-ttu-id="887e6-2708">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="887e6-2708">fx_media_read</span></span>
- <span data-ttu-id="887e6-2709">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-2709">fx_media_space_available</span></span>
- <span data-ttu-id="887e6-2710">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="887e6-2710">fx_media_volume_get</span></span>
- <span data-ttu-id="887e6-2711">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2711">fx_media_volume_set</span></span>
- <span data-ttu-id="887e6-2712">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="887e6-2712">fx_media_write</span></span>
- <span data-ttu-id="887e6-2713">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="887e6-2713">fx_system_initialize</span></span>

## <a name="fx_media_flush"></a><span data-ttu-id="887e6-2714">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="887e6-2714">fx_media_flush</span></span>

<span data-ttu-id="887e6-2715">Записывает данные на физический носитель</span><span class="sxs-lookup"><span data-stu-id="887e6-2715">Flushes data to physical media</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-2716">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-2716">Prototype</span></span>

```c
UINT fx_media_flush(FX_MEDIA *media_ptr);
```
### <a name="description"></a><span data-ttu-id="887e6-2717">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-2717">Description</span></span>

<span data-ttu-id="887e6-2718">Эта служба записывает все кэшированные секторы и записи каталога всех измененных файлов на физический носитель.</span><span class="sxs-lookup"><span data-stu-id="887e6-2718">This service flushes all cached sectors and directory entries of any modified files to the physical media.</span></span>

> [!WARNING]
> <span data-ttu-id="887e6-2719">*Эта процедура может периодически вызываться приложением для снижения риска повреждения файла и (или) потери данных в случае внезапного отключения питания целевого объекта.*</span><span class="sxs-lookup"><span data-stu-id="887e6-2719">*This routine may be called periodically by the application to reduce the risk of file corruption and/or data loss in the event of a sudden loss of power on the target.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-2720">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-2720">Input Parameters</span></span>

- <span data-ttu-id="887e6-2721">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-2721">**media_ptr**: Pointer to media control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-2722">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-2722">Return Values</span></span>

- <span data-ttu-id="887e6-2723">**FX_SUCCESS** (0x00) — запись на диск успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="887e6-2723">**FX_SUCCESS** (0x00) Successful media flush.</span></span>
- <span data-ttu-id="887e6-2724">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-2724">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="887e6-2725">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-2725">**FX_FILE_CORRUPT**    (0x08) File is corrupted.</span></span>
- <span data-ttu-id="887e6-2726">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-2726">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="887e6-2727">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-2727">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-2728">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-2728">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="887e6-2729">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-2729">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="887e6-2730">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-2730">**FX_CALLER_ERROR**    (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-2731">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-2731">Allowed From</span></span>

<span data-ttu-id="887e6-2732">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-2732">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-2733">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-2733">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;

/* Flush all cached sectors and modified file entries to the physical media. */

status = fx_media_flush(&my_media);

/* If status equals FX_SUCCESS, the physical media is completely up-to-date. */

```

### <a name="see-also"></a><span data-ttu-id="887e6-2734">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-2734">See Also</span></span>

- <span data-ttu-id="887e6-2735">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="887e6-2735">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="887e6-2736">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="887e6-2736">fx_media_abort</span></span>
- <span data-ttu-id="887e6-2737">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="887e6-2737">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="887e6-2738">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="887e6-2738">fx_media_check</span></span>
- <span data-ttu-id="887e6-2739">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="887e6-2739">fx_media_close</span></span>
- <span data-ttu-id="887e6-2740">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2740">fx_media_close_notify_set</span></span>
- <span data-ttu-id="887e6-2741">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="887e6-2741">fx_media_exFAT_format</span></span>
- <span data-ttu-id="887e6-2742">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-2742">fx_media_extended_space_available</span></span>
- <span data-ttu-id="887e6-2743">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="887e6-2743">fx_media_format</span></span>
- <span data-ttu-id="887e6-2744">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="887e6-2744">fx_media_open</span></span>
- <span data-ttu-id="887e6-2745">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2745">fx_media_open_notify_set</span></span>
- <span data-ttu-id="887e6-2746">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="887e6-2746">fx_media_read</span></span>
- <span data-ttu-id="887e6-2747">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-2747">fx_media_space_available</span></span>
- <span data-ttu-id="887e6-2748">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="887e6-2748">fx_media_volume_get</span></span>
- <span data-ttu-id="887e6-2749">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2749">fx_media_volume_set</span></span>
- <span data-ttu-id="887e6-2750">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="887e6-2750">fx_media_write</span></span>
- <span data-ttu-id="887e6-2751">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="887e6-2751">fx_system_initialize</span></span>

## <a name="fx_media_format"></a><span data-ttu-id="887e6-2752">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="887e6-2752">fx_media_format</span></span>

<span data-ttu-id="887e6-2753">Форматирует носитель</span><span class="sxs-lookup"><span data-stu-id="887e6-2753">Formats media</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-2754">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-2754">Prototype</span></span>

```c
UINT fx_media_format(
    FX_MEDIA *media_ptr,
    VOID (*driver)(FX_MEDIA *media),
    VOID *driver_info_ptr,
    UCHAR *memory_ptr, 
    UINT memory_size,
    CHAR *volume_name, 
    UINT number_of_fats,
    UINT directory_entries, 
    UINT hidden_sectors,
    ULONG total_sectors, 
    UINT bytes_per_sector,
    UINT sectors_per_cluster,
    UINT heads,
    UINT sectors_per_track);
```
### <a name="description"></a><span data-ttu-id="887e6-2755">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-2755">Description</span></span>

<span data-ttu-id="887e6-2756">Эта служба форматирует указанный носитель в формате, совместимом с FAT 12/16/32, на основе заданных параметров.</span><span class="sxs-lookup"><span data-stu-id="887e6-2756">This service formats the supplied media in a FAT 12/16/32 compatible manner based on the supplied parameters.</span></span> <span data-ttu-id="887e6-2757">Эту службу следует вызывать перед открытием носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-2757">This service must be called prior to opening the media.</span></span>

> [!WARNING]
> <span data-ttu-id="887e6-2758">*Форматирование уже отформатированного носителя фактически приводит к удалению всех файлов и каталогов на нем.*</span><span class="sxs-lookup"><span data-stu-id="887e6-2758">*Formatting an already formatted media effectively erases all files and directories on the media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-2759">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-2759">Input Parameters</span></span>

- <span data-ttu-id="887e6-2760">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-2760">**media_ptr**: Pointer to media control block.</span></span> <span data-ttu-id="887e6-2761">Он используется только для предоставления некоторых основных сведений, необходимых для функционирования драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-2761">This is used only to provide some basic information necessary for the driver to operate.</span></span>
- <span data-ttu-id="887e6-2762">**driver**: указатель на драйвер ввода-вывода для этого носителя</span><span class="sxs-lookup"><span data-stu-id="887e6-2762">**driver**: Pointer to the I/O driver for this media.</span></span> <span data-ttu-id="887e6-2763">Обычно это тот же драйвер, который передается последующему вызову fx_media_open.</span><span class="sxs-lookup"><span data-stu-id="887e6-2763">This will typically be the same driver supplied to the subsequent fx_media_open call.</span></span>
- <span data-ttu-id="887e6-2764">**driver_info_ptr**: указатель на необязательные сведения, которые может использовать драйвер ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="887e6-2764">**driver_info_ptr**: Pointer to optional information that the I/O driver may utilize.</span></span>
- <span data-ttu-id="887e6-2765">**memory_ptr**: указатель на рабочую память для носителя</span><span class="sxs-lookup"><span data-stu-id="887e6-2765">**memory_ptr**: Pointer to the working memory for the media.</span></span>
- <span data-ttu-id="887e6-2766">**memory_size** указывает размер рабочей памяти носителя</span><span class="sxs-lookup"><span data-stu-id="887e6-2766">**memory_size**: Specifies the size of the working media memory.</span></span> <span data-ttu-id="887e6-2767">Размер должен быть не меньше размера сектора носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-2767">The size must be at least as large as the media's sector size.</span></span>
- <span data-ttu-id="887e6-2768">**volume_name**: указатель на строку имени тома (не более 11 символов)</span><span class="sxs-lookup"><span data-stu-id="887e6-2768">**volume_name**: Pointer to the volume name string, which is a maximum of 11 characters.</span></span>
- <span data-ttu-id="887e6-2769">**number_of_fats**: количество FAT на носителе</span><span class="sxs-lookup"><span data-stu-id="887e6-2769">**number_of_fats**: Number of FATs in the media.</span></span> <span data-ttu-id="887e6-2770">Минимальное значение равно 1 для основной файловой системы FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-2770">The minimal value is 1 for the primary FAT.</span></span> <span data-ttu-id="887e6-2771">Значения, превышающие 1, приводят к поддержке дополнительных копий FAT во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="887e6-2771">Values greater than 1 result in additional FAT copies being maintained at run-time.</span></span>
- <span data-ttu-id="887e6-2772">**directory_entries**: количество записей каталога в корневом каталоге</span><span class="sxs-lookup"><span data-stu-id="887e6-2772">**directory_entries**: Number of directory entries in the root directory.</span></span>
- <span data-ttu-id="887e6-2773">**hidden_sectors**: количество секторов, скрытых перед загрузочным сектором этого носителя</span><span class="sxs-lookup"><span data-stu-id="887e6-2773">**hidden_sectors**: Number of sectors hidden before this media's boot sector.</span></span> <span data-ttu-id="887e6-2774">Это характерно при наличии нескольких разделов.</span><span class="sxs-lookup"><span data-stu-id="887e6-2774">This is typical when multiple partitions are present.</span></span>
- <span data-ttu-id="887e6-2775">**total_sectors**: общее количество секторов на носителе</span><span class="sxs-lookup"><span data-stu-id="887e6-2775">**total_sectors**: Total number of sectors in the media.</span></span>
- <span data-ttu-id="887e6-2776">**bytes_per_sector**: число байтов на сектор (обычно 512)</span><span class="sxs-lookup"><span data-stu-id="887e6-2776">**bytes_per_sector**: Number of bytes per sector, which is typically 512.</span></span> <span data-ttu-id="887e6-2777">Для FileX требуется, чтобы оно было кратным 32.</span><span class="sxs-lookup"><span data-stu-id="887e6-2777">FileX requires this to be a multiple of 32.</span></span>
- <span data-ttu-id="887e6-2778">**sectors_per_cluster**: количество секторов в каждом кластере</span><span class="sxs-lookup"><span data-stu-id="887e6-2778">**sectors_per_cluster**: Number of sectors in each cluster.</span></span> <span data-ttu-id="887e6-2779">Кластер является минимальной единицей размещения в файловой системе FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-2779">The cluster is the minimum allocation unit in a FAT file system.</span></span>
- <span data-ttu-id="887e6-2780">**heads**: количество физических головок</span><span class="sxs-lookup"><span data-stu-id="887e6-2780">**heads**: Number of physical heads.</span></span>
- <span data-ttu-id="887e6-2781">**sectors_per_track**: количество секторов на дорожке</span><span class="sxs-lookup"><span data-stu-id="887e6-2781">**sectors_per_track**: Number of sectors per track.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-2782">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-2782">Return Values</span></span>

- <span data-ttu-id="887e6-2783">**FX_SUCCESS** (0x00) — носитель успешно отформатирован.</span><span class="sxs-lookup"><span data-stu-id="887e6-2783">**FX_SUCCESS** (0x00) Successful media format.</span></span>
- <span data-ttu-id="887e6-2784">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-2784">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-2785">**FX_PTR_ERROR** (0x18) — недопустимый носитель, драйвер или указатель на память.</span><span class="sxs-lookup"><span data-stu-id="887e6-2785">**FX_PTR_ERROR** (0x18) Invalid media, driver, or memory pointer.</span></span>
- <span data-ttu-id="887e6-2786">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-2786">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-2787">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-2787">Allowed From</span></span>

<span data-ttu-id="887e6-2788">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-2788">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-2789">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-2789">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             media_memory[512];
UCHAR             ram_disk_memory[32768];

/* Format a RAM disk with 32768 bytes and 512 bytes per sector. */

status = fx_media_format(&ram_disk, _fx_ram_driver,
                         ram_disk_memory, media_memory,
                         sizeof(media_memory),
                         "MY_RAM_DISK" /* Volume Name */,
                         1 /* Number of FATs */,
                         32 /* Directory Entries */,
                         0 /* Hidden sectors */,
                         64 /* Total sectors */,
                         512 /* Sector size */,
                         1 /* Sectors per cluster */,
                         1 /* Heads */,
                         1 /* Sectors per track */);

/* If status is FX_SUCCESS, the media was successfully formatted
    and can now be opened with the following call: */

```

### <a name="see-also"></a><span data-ttu-id="887e6-2790">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-2790">See Also</span></span>

- <span data-ttu-id="887e6-2791">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="887e6-2791">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="887e6-2792">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="887e6-2792">fx_media_abort</span></span>
- <span data-ttu-id="887e6-2793">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="887e6-2793">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="887e6-2794">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="887e6-2794">fx_media_check</span></span>
- <span data-ttu-id="887e6-2795">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="887e6-2795">fx_media_close</span></span>
- <span data-ttu-id="887e6-2796">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2796">fx_media_close_notify_set</span></span>
- <span data-ttu-id="887e6-2797">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="887e6-2797">fx_media_exFAT_format</span></span>
- <span data-ttu-id="887e6-2798">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-2798">fx_media_extended_space_available</span></span>
- <span data-ttu-id="887e6-2799">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="887e6-2799">fx_media_flush</span></span>
- <span data-ttu-id="887e6-2800">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="887e6-2800">fx_media_open</span></span>
- <span data-ttu-id="887e6-2801">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2801">fx_media_open_notify_set</span></span>
- <span data-ttu-id="887e6-2802">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="887e6-2802">fx_media_read</span></span>
- <span data-ttu-id="887e6-2803">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-2803">fx_media_space_available</span></span>
- <span data-ttu-id="887e6-2804">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="887e6-2804">fx_media_volume_get</span></span>
- <span data-ttu-id="887e6-2805">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2805">fx_media_volume_set</span></span>
- <span data-ttu-id="887e6-2806">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="887e6-2806">fx_media_write</span></span>
- <span data-ttu-id="887e6-2807">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="887e6-2807">fx_system_initialize</span></span>

## <a name="fx_media_open"></a><span data-ttu-id="887e6-2808">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="887e6-2808">fx_media_open</span></span>

<span data-ttu-id="887e6-2809">Открывает носитель для доступа к файлам</span><span class="sxs-lookup"><span data-stu-id="887e6-2809">Opens media for file access</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-2810">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-2810">Prototype</span></span>

```c
UINT fx_media_open(
    FX_MEDIA *media_ptr, 
    CHAR *media_name,
    VOID(*media_driver)(FX_MEDIA *),
    VOID *driver_info_ptr,
    VOID *memory_ptr, 
    ULONG memory_size);
```
### <a name="description"></a><span data-ttu-id="887e6-2811">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-2811">Description</span></span>

<span data-ttu-id="887e6-2812">Эта служба открывает носитель для доступа к файлам с помощью предоставляемого драйвера ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="887e6-2812">This service opens a media for file access using the supplied I/O driver.</span></span>

> [!WARNING]
> <span data-ttu-id="887e6-2813">*Память, предоставляемая этой службе, используется для реализации внутреннего кэша логических секторов, поэтому чем больше памяти выделяется, тем меньше снижается объем физического ввода-вывода. Для FileX требуется кэш по крайней мере для одного логического сектора (байт на сектор носителя).*</span><span class="sxs-lookup"><span data-stu-id="887e6-2813">*The memory supplied to this service is used to implement an internal logical sector cache, hence, the more memory supplied the more physical I/O is reduced. FileX requires a cache of at least one logical sector (bytes per sector of the media).*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-2814">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-2814">Input Parameters</span></span>

- <span data-ttu-id="887e6-2815">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-2815">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="887e6-2816">**media_name**: указатель на имя носителя</span><span class="sxs-lookup"><span data-stu-id="887e6-2816">**media_name**: Pointer to media's name.</span></span>
- <span data-ttu-id="887e6-2817">**media_driver**: указатель на драйвер ввода-вывода для этого носителя</span><span class="sxs-lookup"><span data-stu-id="887e6-2817">**media_driver**: Pointer to I/O driver for this media.</span></span> <span data-ttu-id="887e6-2818">Драйвер ввода-вывода должен соответствовать требованиям к драйверу FileX, определенным в главе 5.</span><span class="sxs-lookup"><span data-stu-id="887e6-2818">The I/O driver must conform to FileX driver requirements defined in Chapter 5.</span></span>
- <span data-ttu-id="887e6-2819">**driver_info_ptr**: указатель на необязательные сведения, которые может использовать указанный драйвер ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="887e6-2819">**driver_info_ptr**: Pointer to optional information that the supplied I/O driver may utilize.</span></span>
- <span data-ttu-id="887e6-2820">**memory_ptr**: указатель на рабочую память для носителя</span><span class="sxs-lookup"><span data-stu-id="887e6-2820">**memory_ptr**: Pointer to the working memory for the media.</span></span>
- <span data-ttu-id="887e6-2821">**memory_size** указывает размер рабочей памяти носителя</span><span class="sxs-lookup"><span data-stu-id="887e6-2821">**memory_size**: Specifies the size of the working media memory.</span></span> <span data-ttu-id="887e6-2822">Размер должен быть больше, чем размер сектора носителя (обычно 512 байт).</span><span class="sxs-lookup"><span data-stu-id="887e6-2822">The size must be as large as the media's sector size (typically 512 bytes).</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-2823">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-2823">Return Values</span></span>

- <span data-ttu-id="887e6-2824">**FX_SUCCESS** (0x00) — носитель успешно открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-2824">**FX_SUCCESS** (0x00) Successful media open.</span></span>
- <span data-ttu-id="887e6-2825">**FX_BOOT_ERROR** (0x01) — ошибка при чтении загрузочного сектора носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-2825">**FX_BOOT_ERROR** (0x01) Error reading the media's boot sector.</span></span>
- <span data-ttu-id="887e6-2826">**FX_MEDIA_INVALID** (0x02) — указанный загрузочный сектор носителя поврежден или недопустим.</span><span class="sxs-lookup"><span data-stu-id="887e6-2826">**FX_MEDIA_INVALID** (0x02) Specified media's boot sector is corrupt or invalid.</span></span> <span data-ttu-id="887e6-2827">Кроме того, этот код возврата используется, чтобы указать, что либо размер кэша логического сектора, либо размер записи FAT не является степенью 2.</span><span class="sxs-lookup"><span data-stu-id="887e6-2827">In addition, this return code is used to indicate that either the logical sector cache size or the FAT entry size is not a power of 2.</span></span>
- <span data-ttu-id="887e6-2828">**FX_FAT_READ_ERROR** (0x03) — ошибка при чтении FAT носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-2828">**FX_FAT_READ_ERROR** (0x03) Error reading the media FAT.</span></span>
- <span data-ttu-id="887e6-2829">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-2829">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-2830">**FX_PTR_ERROR** (0x18) — один указатель или несколько имеют значение NULL.</span><span class="sxs-lookup"><span data-stu-id="887e6-2830">**FX_PTR_ERROR** (0x18) One or more pointers are NULL.</span></span>
- <span data-ttu-id="887e6-2831">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-2831">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-2832">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-2832">Allowed From</span></span>

<span data-ttu-id="887e6-2833">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-2833">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-2834">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-2834">Example</span></span>

```c
FX_MEDIA         ram_disk,
UINT             status;
UCHAR             buffer[128];
/* Open a 32KByte RAM disk starting at the fixed address of 0x800000.
    Note that the total 32KByte media size and 128-byte sector size is defined inside of the driver. */

status = fx_media_open(&ram_disk, "RAM DISK", fx_ram_driver, 0, &buffer[0], sizeof(buffer));

/* If status equals FX_SUCCESS, the RAM disk has been successfully setup and is ready for file access! */

```

### <a name="see-also"></a><span data-ttu-id="887e6-2835">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-2835">See Also</span></span>

- <span data-ttu-id="887e6-2836">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="887e6-2836">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="887e6-2837">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="887e6-2837">fx_media_abort</span></span>
- <span data-ttu-id="887e6-2838">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="887e6-2838">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="887e6-2839">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="887e6-2839">fx_media_check</span></span>
- <span data-ttu-id="887e6-2840">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="887e6-2840">fx_media_close</span></span>
- <span data-ttu-id="887e6-2841">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2841">fx_media_close_notify_set</span></span>
- <span data-ttu-id="887e6-2842">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="887e6-2842">fx_media_exFAT_format</span></span>
- <span data-ttu-id="887e6-2843">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-2843">fx_media_extended_space_available</span></span>
- <span data-ttu-id="887e6-2844">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="887e6-2844">fx_media_flush</span></span>
- <span data-ttu-id="887e6-2845">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="887e6-2845">fx_media_format</span></span>
- <span data-ttu-id="887e6-2846">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2846">fx_media_open_notify_set</span></span>
- <span data-ttu-id="887e6-2847">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="887e6-2847">fx_media_read</span></span>
- <span data-ttu-id="887e6-2848">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-2848">fx_media_space_available</span></span>
- <span data-ttu-id="887e6-2849">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="887e6-2849">fx_media_volume_get</span></span>
- <span data-ttu-id="887e6-2850">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2850">fx_media_volume_set</span></span>
- <span data-ttu-id="887e6-2851">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="887e6-2851">fx_media_write</span></span>
- <span data-ttu-id="887e6-2852">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="887e6-2852">fx_system_initialize</span></span>

## <a name="fx_media_open_notify_set"></a><span data-ttu-id="887e6-2853">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2853">fx_media_open_notify_set</span></span>

<span data-ttu-id="887e6-2854">Задает функцию уведомления об открытии носителя</span><span class="sxs-lookup"><span data-stu-id="887e6-2854">Sets the media open notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-2855">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-2855">Prototype</span></span>

```c
UINT fx_media_open_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_open_notify)(FX_MEDIA*));
```
### <a name="description"></a><span data-ttu-id="887e6-2856">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-2856">Description</span></span>

<span data-ttu-id="887e6-2857">Эта служба задает функцию обратного вызова уведомления, которая будет вызываться после успешного открытия носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-2857">This service sets a notify callback function which will be invoked after a media is successfully opened.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-2858">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-2858">Input Parameters</span></span>

- <span data-ttu-id="887e6-2859">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-2859">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="887e6-2860">**media_open_notify**: функция обратного вызова уведомления об открытии носителя для установки</span><span class="sxs-lookup"><span data-stu-id="887e6-2860">**media_open_notify**: Media open notify callback function to be installed.</span></span> <span data-ttu-id="887e6-2861">Передача значения NULL в качестве функции обратного вызова отключает обратный вызов открытия носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-2861">Passing NULL as the callback function disables the media open callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-2862">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-2862">Return Values</span></span>


- <span data-ttu-id="887e6-2863">**FX_SUCCESS** (0x00) — функция обратного вызова успешно установлена.</span><span class="sxs-lookup"><span data-stu-id="887e6-2863">**FX_SUCCESS** (0x00) Successfuly installed the callback function.</span></span>
- <span data-ttu-id="887e6-2864">**FX_PTR_ERROR** (0x18) — параметр media_ptr имеет значение NULL.</span><span class="sxs-lookup"><span data-stu-id="887e6-2864">**FX_PTR_ERROR** (0x18) media_ptr is NULL.</span></span>
- <span data-ttu-id="887e6-2865">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-2865">**FX_CALLER_ERROR**    (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-2866">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-2866">Allowed From</span></span>

<span data-ttu-id="887e6-2867">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-2867">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-2868">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-2868">Example</span></span>

```c
fx_media_open_notify_set(media_ptr, my_media_open_callback);

```

### <a name="see-also"></a><span data-ttu-id="887e6-2869">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-2869">See Also</span></span>

- <span data-ttu-id="887e6-2870">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="887e6-2870">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="887e6-2871">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="887e6-2871">fx_media_abort</span></span>
- <span data-ttu-id="887e6-2872">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="887e6-2872">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="887e6-2873">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="887e6-2873">fx_media_check</span></span>
- <span data-ttu-id="887e6-2874">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="887e6-2874">fx_media_close</span></span>
- <span data-ttu-id="887e6-2875">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2875">fx_media_close_notify_set</span></span>
- <span data-ttu-id="887e6-2876">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="887e6-2876">fx_media_exFAT_format</span></span>
- <span data-ttu-id="887e6-2877">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-2877">fx_media_extended_space_available</span></span>
- <span data-ttu-id="887e6-2878">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="887e6-2878">fx_media_flush</span></span>
- <span data-ttu-id="887e6-2879">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="887e6-2879">fx_media_format</span></span>
- <span data-ttu-id="887e6-2880">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="887e6-2880">fx_media_open</span></span>
- <span data-ttu-id="887e6-2881">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2881">fx_media_open_notify_set</span></span>
- <span data-ttu-id="887e6-2882">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-2882">fx_media_space_available</span></span>
- <span data-ttu-id="887e6-2883">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="887e6-2883">fx_media_volume_get</span></span>
- <span data-ttu-id="887e6-2884">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2884">fx_media_volume_set</span></span>
- <span data-ttu-id="887e6-2885">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="887e6-2885">fx_media_write</span></span>
- <span data-ttu-id="887e6-2886">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="887e6-2886">fx_system_initialize</span></span>

## <a name="fx_media_read"></a><span data-ttu-id="887e6-2887">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="887e6-2887">fx_media_read</span></span>

<span data-ttu-id="887e6-2888">Чтение логического сектора с носителя</span><span class="sxs-lookup"><span data-stu-id="887e6-2888">Reads logical sector from media</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-2889">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-2889">Prototype</span></span>

```c
UINT fx_media_read(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector, 
    VOID *buffer_ptr);
```
### <a name="description"></a><span data-ttu-id="887e6-2890">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-2890">Description</span></span>

<span data-ttu-id="887e6-2891">Эта служба считывает логический сектор с носителя и помещает его в указанный буфер.</span><span class="sxs-lookup"><span data-stu-id="887e6-2891">This service reads a logical sector from the media and places it into the supplied buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-2892">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-2892">Input Parameters</span></span>

- <span data-ttu-id="887e6-2893">**media_ptr**: указатель на открытый ранее носитель</span><span class="sxs-lookup"><span data-stu-id="887e6-2893">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="887e6-2894">**logical_sector**: логический сектор для считывания</span><span class="sxs-lookup"><span data-stu-id="887e6-2894">**logical_sector**: Logical sector to read.</span></span>
- <span data-ttu-id="887e6-2895">**buffer_ptr**: указатель на назначение для считывания логического сектора</span><span class="sxs-lookup"><span data-stu-id="887e6-2895">**buffer_ptr**: Pointer to the destination for the logical sector read.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-2896">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-2896">Return Values</span></span>

- <span data-ttu-id="887e6-2897">**FX_SUCCESS** (0x00) — носитель успешно считан.</span><span class="sxs-lookup"><span data-stu-id="887e6-2897">**FX_SUCCESS** (0x00) Successful media read.</span></span>
- <span data-ttu-id="887e6-2898">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-2898">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="887e6-2899">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-2899">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-2900">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-2900">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="887e6-2901">**FX_PTR_ERROR** (0x18) — недопустимый указатель на носитель или буфер.</span><span class="sxs-lookup"><span data-stu-id="887e6-2901">**FX_PTR_ERROR** (0x18) Invalid media or buffer pointer.</span></span>
- <span data-ttu-id="887e6-2902">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-2902">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-2903">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-2903">Allowed From</span></span>

<span data-ttu-id="887e6-2904">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-2904">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-2905">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-2905">Example</span></span>

```c
FX_MEDIA         my_media;
UCHAR             my_buffer[128];
UINT            STATUS;
/* Read logical sector 22 into "my_buffer" assuming the
    physical media has a sector size of 128. */
status = fx_media_read(&my_media, 22, my_buffer);
/* If status equals FX_SUCCESS, the contents of logical sector 22 are in "my_buffer". */
```

### <a name="see-also"></a><span data-ttu-id="887e6-2906">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-2906">See Also</span></span>

- <span data-ttu-id="887e6-2907">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="887e6-2907">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="887e6-2908">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="887e6-2908">fx_media_abort</span></span>
- <span data-ttu-id="887e6-2909">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="887e6-2909">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="887e6-2910">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="887e6-2910">fx_media_check</span></span>
- <span data-ttu-id="887e6-2911">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="887e6-2911">fx_media_close</span></span>
- <span data-ttu-id="887e6-2912">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2912">fx_media_close_notify_set</span></span>
- <span data-ttu-id="887e6-2913">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="887e6-2913">fx_media_exFAT_format</span></span>
- <span data-ttu-id="887e6-2914">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-2914">fx_media_extended_space_available</span></span>
- <span data-ttu-id="887e6-2915">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="887e6-2915">fx_media_flush</span></span>
- <span data-ttu-id="887e6-2916">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="887e6-2916">fx_media_format</span></span>
- <span data-ttu-id="887e6-2917">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="887e6-2917">fx_media_open</span></span>
- <span data-ttu-id="887e6-2918">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2918">fx_media_open_notify_set</span></span>
- <span data-ttu-id="887e6-2919">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-2919">fx_media_space_available</span></span>
- <span data-ttu-id="887e6-2920">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="887e6-2920">fx_media_volume_get</span></span>
- <span data-ttu-id="887e6-2921">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2921">fx_media_volume_set</span></span>
- <span data-ttu-id="887e6-2922">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="887e6-2922">fx_media_write</span></span>
- <span data-ttu-id="887e6-2923">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="887e6-2923">fx_system_initialize</span></span>

## <a name="fx_media_space_available"></a><span data-ttu-id="887e6-2924">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-2924">fx_media_space_available</span></span>

<span data-ttu-id="887e6-2925">Возвращает доступное пространство на носителе</span><span class="sxs-lookup"><span data-stu-id="887e6-2925">Returns available media space</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-2926">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-2926">Prototype</span></span>

```c
UINT fx_media_space_available(
    FX_MEDIA *media_ptr,
    ULONG *available_bytes_ptr);
```

### <a name="description"></a><span data-ttu-id="887e6-2927">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-2927">Description</span></span>

<span data-ttu-id="887e6-2928">Эта служба возвращает число байтов, доступных на носителе.</span><span class="sxs-lookup"><span data-stu-id="887e6-2928">This service returns the number of bytes available in the media.</span></span>

<span data-ttu-id="887e6-2929">Для работы с носителями объемом более 4 ГБ приложение должно использовать службу *fx_media_extended_space_available*.</span><span class="sxs-lookup"><span data-stu-id="887e6-2929">To work with the media larger than 4GB, application shall use the service *fx_media_extended_space_available*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-2930">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-2930">Input Parameters</span></span>

- <span data-ttu-id="887e6-2931">**media_ptr**: указатель на открытый ранее носитель</span><span class="sxs-lookup"><span data-stu-id="887e6-2931">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="887e6-2932">**available_bytes_ptr**: число байтов, доступное на носителе</span><span class="sxs-lookup"><span data-stu-id="887e6-2932">**available_bytes_ptr**: Available bytes left in the media.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-2933">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-2933">Return Values</span></span>

- <span data-ttu-id="887e6-2934">**FX_SUCCESS** (0x00) — доступное место на носителе успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="887e6-2934">**FX_SUCCESS** (0x00) Successfully returned available space on media.</span></span>
- <span data-ttu-id="887e6-2935">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-2935">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="887e6-2936">**FX_PTR_ERROR** (0x18) — недопустимый указатель на носитель, или доступное количество байтов имеет значение NULL.</span><span class="sxs-lookup"><span data-stu-id="887e6-2936">**FX_PTR_ERROR** (0x18) Invalid media pointer or available bytes pointer is NULL.</span></span>
- <span data-ttu-id="887e6-2937">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-2937">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-2938">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-2938">Allowed From</span></span>

<span data-ttu-id="887e6-2939">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-2939">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-2940">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-2940">Example</span></span>

```c
FX_MEDIA        my_media;
ULONG            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a><span data-ttu-id="887e6-2941">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-2941">See Also</span></span>

- <span data-ttu-id="887e6-2942">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="887e6-2942">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="887e6-2943">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="887e6-2943">fx_media_abort</span></span>
- <span data-ttu-id="887e6-2944">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="887e6-2944">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="887e6-2945">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="887e6-2945">fx_media_check</span></span>
- <span data-ttu-id="887e6-2946">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="887e6-2946">fx_media_close</span></span>
- <span data-ttu-id="887e6-2947">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2947">fx_media_close_notify_set</span></span>
- <span data-ttu-id="887e6-2948">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="887e6-2948">fx_media_exFAT_format</span></span>
- <span data-ttu-id="887e6-2949">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-2949">fx_media_extended_space_available</span></span>
- <span data-ttu-id="887e6-2950">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="887e6-2950">fx_media_flush</span></span>
- <span data-ttu-id="887e6-2951">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="887e6-2951">fx_media_format</span></span>
- <span data-ttu-id="887e6-2952">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="887e6-2952">fx_media_open</span></span>
- <span data-ttu-id="887e6-2953">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2953">fx_media_open_notify_set</span></span>
- <span data-ttu-id="887e6-2954">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="887e6-2954">fx_media_read</span></span>
- <span data-ttu-id="887e6-2955">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="887e6-2955">fx_media_volume_get</span></span>
- <span data-ttu-id="887e6-2956">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2956">fx_media_volume_set</span></span>
- <span data-ttu-id="887e6-2957">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="887e6-2957">fx_media_write</span></span>
- <span data-ttu-id="887e6-2958">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="887e6-2958">fx_system_initialize</span></span>

## <a name="fx_media_volume_get"></a><span data-ttu-id="887e6-2959">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="887e6-2959">fx_media_volume_get</span></span>

<span data-ttu-id="887e6-2960">Получает имя тома носителя</span><span class="sxs-lookup"><span data-stu-id="887e6-2960">Gets media volume name</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-2961">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-2961">Prototype</span></span>

```c
UINT fx_media_volume_get(
    FX_MEDIA *media_ptr,
    CHAR *volume_name,
    UINT volume_source);
```
### <a name="description"></a><span data-ttu-id="887e6-2962">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-2962">Description</span></span>

<span data-ttu-id="887e6-2963">Эта служба получает имя тома ранее открытого носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-2963">This service retrieves the volume name of the previously opened media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-2964">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-2964">Input Parameters</span></span>

- <span data-ttu-id="887e6-2965">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-2965">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="887e6-2966">**volume_name**: указатель на место назначения для имени тома</span><span class="sxs-lookup"><span data-stu-id="887e6-2966">**volume_name**: Pointer to destination for volume name.</span></span> <span data-ttu-id="887e6-2967">Обратите внимание, что место назначения должно быть как достаточно большим, чтобы вместить 12 символов.</span><span class="sxs-lookup"><span data-stu-id="887e6-2967">Note that the destination must be at least large enough to hold 12 characters.</span></span>
- <span data-ttu-id="887e6-2968">**volume_source**: указывает, где следует получить имя из загрузочного или корневого каталога</span><span class="sxs-lookup"><span data-stu-id="887e6-2968">**volume_source**: Designates where to retrieve the name, either from the boot sector or the root directory.</span></span> <span data-ttu-id="887e6-2969">Допустимые значения для этого параметра:</span><span class="sxs-lookup"><span data-stu-id="887e6-2969">Valid values for this parameter are:</span></span>
  - <span data-ttu-id="887e6-2970">FX_BOOT_SECTOR</span><span class="sxs-lookup"><span data-stu-id="887e6-2970">FX_BOOT_SECTOR</span></span>
  - <span data-ttu-id="887e6-2971">FX_DIRECTORY_SECTOR</span><span class="sxs-lookup"><span data-stu-id="887e6-2971">FX_DIRECTORY_SECTOR</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-2972">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-2972">Return Values</span></span>

- <span data-ttu-id="887e6-2973">**FX_SUCCESS** (0x00) — том носителя успешно получен.</span><span class="sxs-lookup"><span data-stu-id="887e6-2973">**FX_SUCCESS** (0x00) Successful media volume get.</span></span>
- <span data-ttu-id="887e6-2974">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-2974">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="887e6-2975">**FX_NOT_FOUND** (0x04) — том не найден.</span><span class="sxs-lookup"><span data-stu-id="887e6-2975">**FX_NOT_FOUND** (0x04) Volume not found.</span></span>
- <span data-ttu-id="887e6-2976">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-2976">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-2977">**FX_PTR_ERROR** (0x18) — недопустимый указатель места назначения носителя или тома.</span><span class="sxs-lookup"><span data-stu-id="887e6-2977">**FX_PTR_ERROR** (0x18) Invalid media or volume destination pointer.</span></span>
- <span data-ttu-id="887e6-2978">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-2978">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-2979">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-2979">Allowed From</span></span>

<span data-ttu-id="887e6-2980">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-2980">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-2981">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-2981">Example</span></span>

```c
FX_MEDIA        ram_disk;
UCHAR             volume_name[12];
/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name), FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */

```

### <a name="see-also"></a><span data-ttu-id="887e6-2982">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-2982">See Also</span></span>

- <span data-ttu-id="887e6-2983">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="887e6-2983">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="887e6-2984">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="887e6-2984">fx_media_abort</span></span>
- <span data-ttu-id="887e6-2985">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="887e6-2985">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="887e6-2986">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="887e6-2986">fx_media_check</span></span>
- <span data-ttu-id="887e6-2987">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="887e6-2987">fx_media_close</span></span>
- <span data-ttu-id="887e6-2988">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2988">fx_media_close_notify_set</span></span>
- <span data-ttu-id="887e6-2989">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="887e6-2989">fx_media_exFAT_format</span></span>
- <span data-ttu-id="887e6-2990">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-2990">fx_media_extended_space_available</span></span>
- <span data-ttu-id="887e6-2991">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="887e6-2991">fx_media_flush</span></span>
- <span data-ttu-id="887e6-2992">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="887e6-2992">fx_media_format</span></span>
- <span data-ttu-id="887e6-2993">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="887e6-2993">fx_media_open</span></span>
- <span data-ttu-id="887e6-2994">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2994">fx_media_open_notify_set</span></span>
- <span data-ttu-id="887e6-2995">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="887e6-2995">fx_media_read</span></span>
- <span data-ttu-id="887e6-2996">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-2996">fx_media_space_available</span></span>
- <span data-ttu-id="887e6-2997">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="887e6-2997">fx_media_volume_set</span></span>
- <span data-ttu-id="887e6-2998">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="887e6-2998">fx_media_write</span></span>
- <span data-ttu-id="887e6-2999">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="887e6-2999">fx_system_initialize</span></span>

## <a name="fx_media_volume_get_extended"></a><span data-ttu-id="887e6-3000">fx_media_volume_get_extended</span><span class="sxs-lookup"><span data-stu-id="887e6-3000">fx_media_volume_get_extended</span></span>

<span data-ttu-id="887e6-3001">Получает имя тома ранее открытого носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-3001">Gets media volume name of previously opened media</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-3002">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-3002">Prototype</span></span>

```c
UINT fx_media_volume_get_extended(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name,
    UINT volume_name_buffer_length,
    UINT volume_source);
```
### <a name="description"></a><span data-ttu-id="887e6-3003">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-3003">Description</span></span>

<span data-ttu-id="887e6-3004">Эта служба получает имя тома ранее открытого носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-3004">This service retrieves the volume name of the previously opened media.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="887e6-3005">Эта служба идентична \***fx_media_volume_get()** _, за исключением того, что вызывающий объект передает размер буфера _ \*volume_name\*\*.</span><span class="sxs-lookup"><span data-stu-id="887e6-3005">This service is identical to ***fx_media_volume_get()** _ except the caller passes in the size of the _ *volume_name** buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-3006">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-3006">Input Parameters</span></span>


- <span data-ttu-id="887e6-3007">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-3007">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="887e6-3008">**volume_name**: указатель на место назначения для имени тома</span><span class="sxs-lookup"><span data-stu-id="887e6-3008">**volume_name**: Pointer to destination for volume name.</span></span> <span data-ttu-id="887e6-3009">Обратите внимание, что место назначения должно быть как достаточно большим, чтобы вместить 12 символов.</span><span class="sxs-lookup"><span data-stu-id="887e6-3009">Note that the destination must be at least large enough to hold 12 characters.</span></span>
- <span data-ttu-id="887e6-3010">**volume_name_buffer_length**: размер буфера volume_name</span><span class="sxs-lookup"><span data-stu-id="887e6-3010">**volume_name_buffer_length**: Size of volume_name buffer.</span></span>
- <span data-ttu-id="887e6-3011">**volume_source**: указывает, где следует получить имя из загрузочного или корневого каталога</span><span class="sxs-lookup"><span data-stu-id="887e6-3011">**volume_source**: Designates where to retrieve the name, either from the boot sector or the root directory.</span></span> <span data-ttu-id="887e6-3012">Допустимые значения для этого параметра:</span><span class="sxs-lookup"><span data-stu-id="887e6-3012">Valid values for this parameter are:</span></span>
  - <span data-ttu-id="887e6-3013">FX_BOOT_SECTOR</span><span class="sxs-lookup"><span data-stu-id="887e6-3013">FX_BOOT_SECTOR</span></span>
  - <span data-ttu-id="887e6-3014">FX_DIRECTORY_SECTOR</span><span class="sxs-lookup"><span data-stu-id="887e6-3014">FX_DIRECTORY_SECTOR</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-3015">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-3015">Return Values</span></span>

- <span data-ttu-id="887e6-3016">**FX_SUCCESS** (0x00) — том носителя успешно получен.</span><span class="sxs-lookup"><span data-stu-id="887e6-3016">**FX_SUCCESS** (0x00) Successful media volume get.</span></span>
- <span data-ttu-id="887e6-3017">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-3017">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="887e6-3018">**FX_NOT_FOUND** (0x04) — том не найден.</span><span class="sxs-lookup"><span data-stu-id="887e6-3018">**FX_NOT_FOUND** (0x04) Volume not found.</span></span>
- <span data-ttu-id="887e6-3019">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-3019">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-3020">**FX_PTR_ERROR** (0x18) — недопустимый указатель места назначения носителя или тома.</span><span class="sxs-lookup"><span data-stu-id="887e6-3020">**FX_PTR_ERROR** (0x18) Invalid media or volume destination pointer.</span></span>
- <span data-ttu-id="887e6-3021">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-3021">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-3022">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-3022">Allowed From</span></span>

<span data-ttu-id="887e6-3023">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-3023">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-3024">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-3024">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             volume_name[12];

/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name),
                                      FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-3025">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-3025">See Also</span></span>

- <span data-ttu-id="887e6-3026">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="887e6-3026">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="887e6-3027">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="887e6-3027">fx_media_abort</span></span>
- <span data-ttu-id="887e6-3028">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="887e6-3028">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="887e6-3029">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="887e6-3029">fx_media_check</span></span>
- <span data-ttu-id="887e6-3030">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="887e6-3030">fx_media_close</span></span>
- <span data-ttu-id="887e6-3031">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3031">fx_media_close_notify_set</span></span>
- <span data-ttu-id="887e6-3032">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="887e6-3032">fx_media_exFAT_format</span></span>
- <span data-ttu-id="887e6-3033">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-3033">fx_media_extended_space_available</span></span>
- <span data-ttu-id="887e6-3034">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="887e6-3034">fx_media_flush</span></span>
- <span data-ttu-id="887e6-3035">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="887e6-3035">fx_media_format</span></span>
- <span data-ttu-id="887e6-3036">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="887e6-3036">fx_media_open</span></span>
- <span data-ttu-id="887e6-3037">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3037">fx_media_open_notify_set</span></span>
- <span data-ttu-id="887e6-3038">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="887e6-3038">fx_media_read</span></span>
- <span data-ttu-id="887e6-3039">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-3039">fx_media_space_available</span></span>
- <span data-ttu-id="887e6-3040">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3040">fx_media_volume_set</span></span>
- <span data-ttu-id="887e6-3041">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="887e6-3041">fx_media_write</span></span>
- <span data-ttu-id="887e6-3042">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="887e6-3042">fx_system_initialize</span></span>

## <a name="fx_media_volume_set"></a><span data-ttu-id="887e6-3043">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3043">fx_media_volume_set</span></span>

<span data-ttu-id="887e6-3044">Задает имя тома носителя</span><span class="sxs-lookup"><span data-stu-id="887e6-3044">Sets media volume name</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-3045">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-3045">Prototype</span></span>

```c
UINT fx_media_volume_set(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name);
```
### <a name="description"></a><span data-ttu-id="887e6-3046">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-3046">Description</span></span>

<span data-ttu-id="887e6-3047">Эта служба задает имя тома для ранее открытого носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-3047">This service sets the volume name of the previously opened media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-3048">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-3048">Input Parameters</span></span>

- <span data-ttu-id="887e6-3049">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-3049">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="887e6-3050">**volume_name**: указатель на имя тома</span><span class="sxs-lookup"><span data-stu-id="887e6-3050">**volume_name**: Pointer to the volume name.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-3051">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-3051">Return Values</span></span>

- <span data-ttu-id="887e6-3052">**FX_SUCCESS** (0x00) — том носителя успешно задан.</span><span class="sxs-lookup"><span data-stu-id="887e6-3052">**FX_SUCCESS** (0x00) Successful media volume set.</span></span>
- <span data-ttu-id="887e6-3053">**FX_INVALID_NAME** (0x0C) — недопустимый параметр volume_name.</span><span class="sxs-lookup"><span data-stu-id="887e6-3053">**FX_INVALID_NAME** (0x0C) Volume_name is invalid.</span></span>
- <span data-ttu-id="887e6-3054">**FX_MEDIA_INVALID** (0x02) — не удается задать имя тома.</span><span class="sxs-lookup"><span data-stu-id="887e6-3054">**FX_MEDIA_INVALID** (0x02) Unable to set volume name.</span></span>
- <span data-ttu-id="887e6-3055">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-3055">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="887e6-3056">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-3056">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-3057">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-3057">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="887e6-3058">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени тома.</span><span class="sxs-lookup"><span data-stu-id="887e6-3058">**FX_PTR_ERROR** (0x18) Invalid media or volume name pointer.</span></span>
- <span data-ttu-id="887e6-3059">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-3059">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-3060">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-3060">Allowed From</span></span>

<span data-ttu-id="887e6-3061">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-3061">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-3062">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-3062">Example</span></span>

```c
FX_MEDIA ram_disk;

/* Set the volume name to "MY_VOLUME". */

status = fx_media_volume_set(&ram_disk, "MY_VOLUME");

/* If status is FX_SUCCESS, the volume name was successfully set. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-3063">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-3063">See Also</span></span>

- <span data-ttu-id="887e6-3064">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="887e6-3064">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="887e6-3065">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="887e6-3065">fx_media_abort</span></span>
- <span data-ttu-id="887e6-3066">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="887e6-3066">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="887e6-3067">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="887e6-3067">fx_media_check</span></span>
- <span data-ttu-id="887e6-3068">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="887e6-3068">fx_media_close</span></span>
- <span data-ttu-id="887e6-3069">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3069">fx_media_close_notify_set</span></span>
- <span data-ttu-id="887e6-3070">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="887e6-3070">fx_media_exFAT_format</span></span>
- <span data-ttu-id="887e6-3071">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-3071">fx_media_extended_space_available</span></span>
- <span data-ttu-id="887e6-3072">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="887e6-3072">fx_media_flush</span></span>
- <span data-ttu-id="887e6-3073">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="887e6-3073">fx_media_format</span></span>
- <span data-ttu-id="887e6-3074">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="887e6-3074">fx_media_open</span></span>
- <span data-ttu-id="887e6-3075">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3075">fx_media_open_notify_set</span></span>
- <span data-ttu-id="887e6-3076">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="887e6-3076">fx_media_read</span></span>
- <span data-ttu-id="887e6-3077">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-3077">fx_media_space_available</span></span>
- <span data-ttu-id="887e6-3078">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3078">fx_media_volume_get</span></span>
- <span data-ttu-id="887e6-3079">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="887e6-3079">fx_media_write</span></span>
- <span data-ttu-id="887e6-3080">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="887e6-3080">fx_system_initialize</span></span>

## <a name="fx_media_write"></a><span data-ttu-id="887e6-3081">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="887e6-3081">fx_media_write</span></span>

<span data-ttu-id="887e6-3082">Записывает логический сектор</span><span class="sxs-lookup"><span data-stu-id="887e6-3082">Writes logical sector</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-3083">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-3083">Prototype</span></span>

```c
UINT fx_media_write(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector,
    VOID *buffer_ptr);
```
### <a name="description"></a><span data-ttu-id="887e6-3084">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-3084">Description</span></span>

<span data-ttu-id="887e6-3085">Эта служба записывает указанный буфер в указанный логический сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-3085">This service writes the supplied buffer to the specified logical sector.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-3086">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-3086">Input Parameters</span></span>

- <span data-ttu-id="887e6-3087">**media_ptr**: указатель на открытый ранее носитель</span><span class="sxs-lookup"><span data-stu-id="887e6-3087">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="887e6-3088">**logical_sector**: логический сектор для записи</span><span class="sxs-lookup"><span data-stu-id="887e6-3088">**logical_sector**: Logical sector to write.</span></span>
- <span data-ttu-id="887e6-3089">**buffer_ptr**: указатель на источник для записи логического сектора</span><span class="sxs-lookup"><span data-stu-id="887e6-3089">**buffer_ptr**: Pointer to the source for the logical sector write.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-3090">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-3090">Return Values</span></span>

- <span data-ttu-id="887e6-3091">**FX_SUCCESS** (0x00) — запись на носитель успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="887e6-3091">**FX_SUCCESS** (0x00) Successful media write.</span></span>
- <span data-ttu-id="887e6-3092">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-3092">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="887e6-3093">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-3093">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="887e6-3094">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-3094">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-3095">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-3095">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="887e6-3096">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="887e6-3096">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="887e6-3097">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-3097">**FX_CALLER_ERROR**    (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-3098">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-3098">Allowed From</span></span>

<span data-ttu-id="887e6-3099">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-3099">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-3100">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-3100">Example</span></span>

```c
FX_MEDIA             my_media;
UCHAR                 my_buffer[128];
UINT                 status;

/* Write logical sector 22 from "my_buffer" assuming
    the physical media has a sector size of 128. */

status = fx_media_write(&my_media, 22, my_buffer);

/* If status equals FX_SUCCESS, the contents of logical
    sector 22 are now the same as "my_buffer." */
```

### <a name="see-also"></a><span data-ttu-id="887e6-3101">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-3101">See Also</span></span>

- <span data-ttu-id="887e6-3102">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="887e6-3102">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="887e6-3103">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="887e6-3103">fx_media_abort</span></span>
- <span data-ttu-id="887e6-3104">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="887e6-3104">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="887e6-3105">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="887e6-3105">fx_media_check</span></span>
- <span data-ttu-id="887e6-3106">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="887e6-3106">fx_media_close</span></span>
- <span data-ttu-id="887e6-3107">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3107">fx_media_close_notify_set</span></span>
- <span data-ttu-id="887e6-3108">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="887e6-3108">fx_media_exFAT_format</span></span>
- <span data-ttu-id="887e6-3109">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-3109">fx_media_extended_space_available</span></span>
- <span data-ttu-id="887e6-3110">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="887e6-3110">fx_media_flush</span></span>
- <span data-ttu-id="887e6-3111">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="887e6-3111">fx_media_format</span></span>
- <span data-ttu-id="887e6-3112">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="887e6-3112">fx_media_open</span></span>
- <span data-ttu-id="887e6-3113">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3113">fx_media_open_notify_set</span></span>
- <span data-ttu-id="887e6-3114">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="887e6-3114">fx_media_read</span></span>
- <span data-ttu-id="887e6-3115">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="887e6-3115">fx_media_space_available</span></span>
- <span data-ttu-id="887e6-3116">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3116">fx_media_volume_get</span></span>
- <span data-ttu-id="887e6-3117">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3117">fx_media_volume_set</span></span>
- <span data-ttu-id="887e6-3118">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="887e6-3118">fx_system_initialize</span></span>

## <a name="fx_system_date_get"></a><span data-ttu-id="887e6-3119">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3119">fx_system_date_get</span></span>

<span data-ttu-id="887e6-3120">Возвращает дату файловой системы</span><span class="sxs-lookup"><span data-stu-id="887e6-3120">Gets file system date</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-3121">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-3121">Prototype</span></span>

```c
UINT fx_system_date_get(
    UINT *year, 
    UINT *month, 
    UINT *day);
```
### <a name="description"></a><span data-ttu-id="887e6-3122">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-3122">Description</span></span>

<span data-ttu-id="887e6-3123">Эта служба возвращает текущую системную дату.</span><span class="sxs-lookup"><span data-stu-id="887e6-3123">This service returns the current system date.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-3124">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-3124">Input Parameters</span></span>

- <span data-ttu-id="887e6-3125">**year**: указатель на назначение для года</span><span class="sxs-lookup"><span data-stu-id="887e6-3125">**year**: Pointer to destination for year.</span></span>
- <span data-ttu-id="887e6-3126">**month**: указатель на назначение для месяца</span><span class="sxs-lookup"><span data-stu-id="887e6-3126">**month**: Pointer to destination for month.</span></span>
- <span data-ttu-id="887e6-3127">**day**: указатель на назначение для дня</span><span class="sxs-lookup"><span data-stu-id="887e6-3127">**day**: Pointer to destination for day.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-3128">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-3128">Return Values</span></span>

- <span data-ttu-id="887e6-3129">**FX_SUCCESS** (0x00) — дата успешно получена.</span><span class="sxs-lookup"><span data-stu-id="887e6-3129">**FX_SUCCESS** (0x00) Successful date retrieval.</span></span>
- <span data-ttu-id="887e6-3130">**FX_PTR_ERROR** (0x18) — один входной параметр ил несколько имеют значение NULL.</span><span class="sxs-lookup"><span data-stu-id="887e6-3130">**FX_PTR_ERROR** (0x18) One or more of the input parameters are NULL.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-3131">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-3131">Allowed From</span></span>

<span data-ttu-id="887e6-3132">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-3132">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-3133">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-3133">Example</span></span>

```c
UINT            status;
UINT            year;
UINT            month;
UINT            day;
/* Retrieve the current system date. */

status = fx_system_date_get(&year, &month, &day);

/* If status equals FX_SUCCESS, the year, month,
    and day parameters now have meaningful information. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-3134">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-3134">See Also</span></span>

- <span data-ttu-id="887e6-3135">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3135">fx_system_date_set</span></span>
- <span data-ttu-id="887e6-3136">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="887e6-3136">fx_system_initialize</span></span>
- <span data-ttu-id="887e6-3137">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3137">fx_system_time_get</span></span>
- <span data-ttu-id="887e6-3138">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3138">fx_system_time_set</span></span>

## <a name="fx_system_date_set"></a><span data-ttu-id="887e6-3139">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3139">fx_system_date_set</span></span>

<span data-ttu-id="887e6-3140">Задает системную дату</span><span class="sxs-lookup"><span data-stu-id="887e6-3140">Sets system date</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-3141">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-3141">Prototype</span></span>

```c
UINT fx_system_date_set(
    UINT year, 
    UINT month, 
    UINT day);
```

### <a name="description"></a><span data-ttu-id="887e6-3142">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-3142">Description</span></span>

<span data-ttu-id="887e6-3143">Эта служба задает системную дату указанным образом.</span><span class="sxs-lookup"><span data-stu-id="887e6-3143">This service sets the system date as specified.</span></span>

> [!WARNING]
> <span data-ttu-id="887e6-3144">*Эту службу следует вызывать вскоре после **fx_system_initialize** для задания начальной системной даты. По умолчанию системная дата является датой последнего общего выпуска FileX.*</span><span class="sxs-lookup"><span data-stu-id="887e6-3144">*This service should be called shortly after **fx_system_initialize** to set the initial system date. By default, the system date is that of the last generic FileX release.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-3145">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-3145">Input Parameters</span></span>

- <span data-ttu-id="887e6-3146">**year**: новый год</span><span class="sxs-lookup"><span data-stu-id="887e6-3146">**year**: New year.</span></span> <span data-ttu-id="887e6-3147">Допустимый диапазон — от 1980 до 2107.</span><span class="sxs-lookup"><span data-stu-id="887e6-3147">The valid range is from 1980 through the year 2107.</span></span>
- <span data-ttu-id="887e6-3148">**month**: новый месяц</span><span class="sxs-lookup"><span data-stu-id="887e6-3148">**month**: New month.</span></span> <span data-ttu-id="887e6-3149">Допустимый диапазон — от 1 до 12.</span><span class="sxs-lookup"><span data-stu-id="887e6-3149">The valid range is from 1 through 12.</span></span>
- <span data-ttu-id="887e6-3150">**day**: новый день</span><span class="sxs-lookup"><span data-stu-id="887e6-3150">**day**: New day.</span></span> <span data-ttu-id="887e6-3151">Допустимый диапазон — от 1 до 31 (в зависимости от месяца и високосного года).</span><span class="sxs-lookup"><span data-stu-id="887e6-3151">The valid range is from 1 through 31, depending on month and leap year conditions.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-3152">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-3152">Return Values</span></span>

- <span data-ttu-id="887e6-3153">**FX_SUCCESS** (0x00) — дата успешно задана.</span><span class="sxs-lookup"><span data-stu-id="887e6-3153">**FX_SUCCESS** (0x00) Successful date setting.</span></span>
- <span data-ttu-id="887e6-3154">**FX_INVALID_YEAR** (0x12) — указан недопустимый год.</span><span class="sxs-lookup"><span data-stu-id="887e6-3154">**FX_INVALID_YEAR** (0x12) Invalid year specified.</span></span>
- <span data-ttu-id="887e6-3155">**FX_INVALID_MONTH** (0x13) — указан недопустимый месяц.</span><span class="sxs-lookup"><span data-stu-id="887e6-3155">**FX_INVALID_MONTH** (0x13) Invalid month specified.</span></span>
- <span data-ttu-id="887e6-3156">**FX_INVALID_DAY** (0x14) — указан недопустимый день.</span><span class="sxs-lookup"><span data-stu-id="887e6-3156">**FX_INVALID_DAY** (0x14) Invalid day specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-3157">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-3157">Allowed From</span></span>

<span data-ttu-id="887e6-3158">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-3158">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-3159">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-3159">Example</span></span>

```c
 UINT             status;

/* Set the system date to December 12, 2005. */

status = fx_system_date_set(2005, 12, 12);

/* If status equals FX_SUCCESS, the file system date is now
    12-12-2005. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-3160">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-3160">See Also</span></span>

- <span data-ttu-id="887e6-3161">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3161">fx_system_date_get</span></span>
- <span data-ttu-id="887e6-3162">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="887e6-3162">fx_system_initialize</span></span>
- <span data-ttu-id="887e6-3163">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3163">fx_system_time_get</span></span>
- <span data-ttu-id="887e6-3164">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3164">fx_system_time_set</span></span>

## <a name="fx_system_initialize"></a><span data-ttu-id="887e6-3165">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="887e6-3165">fx_system_initialize</span></span>

<span data-ttu-id="887e6-3166">Инициализирует всю систему</span><span class="sxs-lookup"><span data-stu-id="887e6-3166">Initializes entire system</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-3167">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-3167">Prototype</span></span>

```c
VOID fx_system_initialize(void);
```

### <a name="description"></a><span data-ttu-id="887e6-3168">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-3168">Description</span></span>

<span data-ttu-id="887e6-3169">Эта служба инициализирует все основные структуры данных FileX.</span><span class="sxs-lookup"><span data-stu-id="887e6-3169">This service initializes all the major FileX data structures.</span></span> <span data-ttu-id="887e6-3170">Следует вызывать либо в ***tx_application_define***, либо, возможно, из потока инициализации, а также следует вызывать перед использованием любой другой службы FileX.</span><span class="sxs-lookup"><span data-stu-id="887e6-3170">It should be called either in ***tx_application_define*** or possibly from an initialization thread and must be called prior to using any other FileX service.</span></span>

> [!WARNING]
> <span data-ttu-id="887e6-3171">\*После инициализации этим вызовом приложение должно вызвать \***fx_system_date_set** _ и _ *fx_system_time_set\*\*, чтобы начать с точных системных даты и времени.*</span><span class="sxs-lookup"><span data-stu-id="887e6-3171">*Once initialized by this call, the application should call ***fx_system_date_set** _ and _ *fx_system_time_set** to start with an accurate system date and time.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-3172">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-3172">Input Parameters</span></span>

<span data-ttu-id="887e6-3173">Нет</span><span class="sxs-lookup"><span data-stu-id="887e6-3173">None</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-3174">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-3174">Return Values</span></span>

<span data-ttu-id="887e6-3175">Нет.</span><span class="sxs-lookup"><span data-stu-id="887e6-3175">None.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-3176">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-3176">Allowed From</span></span>

<span data-ttu-id="887e6-3177">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-3177">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-3178">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-3178">Example</span></span>

```c
void tx_application_define(VOID *free_memory)
{
    UINT status;
    /* Initialize the FileX system. */
    fx_system_initialize();
    /* Set the file system date. */
    fx_system_date_set(my_year, my_month, my_day);

    /* Set the file system time. */
    fx_system_time_set(my_hour, my_minute, my_second);

    /* Now perform all other initialization and possibly FileX media
        open calls if the corresponding driver does not block on the boot sector read. */

    ...

}
```

### <a name="see-also"></a><span data-ttu-id="887e6-3179">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-3179">See Also</span></span>

- <span data-ttu-id="887e6-3180">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3180">fx_system_date_get</span></span>
- <span data-ttu-id="887e6-3181">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3181">fx_system_date_set</span></span>
- <span data-ttu-id="887e6-3182">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3182">fx_system_time_get</span></span>
- <span data-ttu-id="887e6-3183">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3183">fx_system_time_set</span></span>

## <a name="fx_system_time_get"></a><span data-ttu-id="887e6-3184">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3184">fx_system_time_get</span></span>

<span data-ttu-id="887e6-3185">Получает текущее системное время</span><span class="sxs-lookup"><span data-stu-id="887e6-3185">Gets current system time</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-3186">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-3186">Prototype</span></span>

```c
UINT fx_system_time_get(
    UINT *hour,
    UINT *minute,
    UINT *second);
```

### <a name="description"></a><span data-ttu-id="887e6-3187">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-3187">Description</span></span>

<span data-ttu-id="887e6-3188">Эта служба получает текущее системное время.</span><span class="sxs-lookup"><span data-stu-id="887e6-3188">This service retrieves the current system time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-3189">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-3189">Input Parameters</span></span>

- <span data-ttu-id="887e6-3190">**hour**: указатель на назначение для часа</span><span class="sxs-lookup"><span data-stu-id="887e6-3190">**hour**: Pointer to destination for hour.</span></span>
- <span data-ttu-id="887e6-3191">**minute**: указатель на назначение для минуты</span><span class="sxs-lookup"><span data-stu-id="887e6-3191">**minute**: Pointer to destination for minute.</span></span>
- <span data-ttu-id="887e6-3192">**second**: указатель на назначение для секунды</span><span class="sxs-lookup"><span data-stu-id="887e6-3192">**second**: Pointer to destination for second.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-3193">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-3193">Return Values</span></span>

- <span data-ttu-id="887e6-3194">**FX_SUCCESS** (0x00) — системное время успешно получено.</span><span class="sxs-lookup"><span data-stu-id="887e6-3194">**FX_SUCCESS** (0x00) Successful system time retrieval.</span></span>
- <span data-ttu-id="887e6-3195">**FX_PTR_ERROR** (0x18) — один входной параметр или несколько.</span><span class="sxs-lookup"><span data-stu-id="887e6-3195">**FX_PTR_ERROR** (0x18) One or more of the input parameters</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-3196">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-3196">Allowed From</span></span>

<span data-ttu-id="887e6-3197">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-3197">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-3198">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-3198">Example</span></span>

```c
UINT             status;
UINT             hour;
UINT             minute;
UINT             second;

/* Retrieve the current system time. */

status = fx_system_time_get(&hour, &minute, &second);

/* If status equals FX_SUCCESS, the current system time
    is in the hour, minute, and second variables. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-3199">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-3199">See Also</span></span>

- <span data-ttu-id="887e6-3200">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3200">fx_system_date_get</span></span>
- <span data-ttu-id="887e6-3201">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3201">fx_system_date_set</span></span>
- <span data-ttu-id="887e6-3202">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="887e6-3202">fx_system_initialize</span></span>
- <span data-ttu-id="887e6-3203">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3203">fx_system_time_set</span></span>

## <a name="fx_system_time_set"></a><span data-ttu-id="887e6-3204">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3204">fx_system_time_set</span></span>

<span data-ttu-id="887e6-3205">Задает текущее системное время</span><span class="sxs-lookup"><span data-stu-id="887e6-3205">Sets current system time</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-3206">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-3206">Prototype</span></span>

```c
UINT fx_system_time_set(UINT hour, UINT minute, UINT second);
```

### <a name="description"></a><span data-ttu-id="887e6-3207">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-3207">Description</span></span>

<span data-ttu-id="887e6-3208">Эта служба задает текущее системное время в соответствии с заданными входными параметрами.</span><span class="sxs-lookup"><span data-stu-id="887e6-3208">This service sets the current system time to that specified by the input parameters.</span></span>

> [!WARNING]
> <span data-ttu-id="887e6-3209">*Эту службу следует вызывать вскоре после **fx_system_initialize** для задания начального системного времени. По умолчанию системным временем является 0:0:0.*</span><span class="sxs-lookup"><span data-stu-id="887e6-3209">*This service should be called shortly after **fx_system_initialize** to set the initial system time. By default, the system time is 0:0:0.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-3210">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-3210">Input Parameters</span></span>

- <span data-ttu-id="887e6-3211">**hour**: новый час (0–23)</span><span class="sxs-lookup"><span data-stu-id="887e6-3211">**hour**: New hour (0-23).</span></span>
- <span data-ttu-id="887e6-3212">**minute**: новая минута (0–59)</span><span class="sxs-lookup"><span data-stu-id="887e6-3212">**minute**: New minute (0-59).</span></span>
- <span data-ttu-id="887e6-3213">**second**: новая секунда (0–59)</span><span class="sxs-lookup"><span data-stu-id="887e6-3213">**second**: New second (0-59).</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-3214">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-3214">Return Values</span></span>

- <span data-ttu-id="887e6-3215">**FX_SUCCESS** (0x00) — системное время успешно получено.</span><span class="sxs-lookup"><span data-stu-id="887e6-3215">**FX_SUCCESS** (0x00) Successful system time retrieval.</span></span>
- <span data-ttu-id="887e6-3216">**FX_INVALID_HOUR** (0x15) — недопустимый новый час.</span><span class="sxs-lookup"><span data-stu-id="887e6-3216">**FX_INVALID_HOUR**    (0x15) New hour is invalid.</span></span>
- <span data-ttu-id="887e6-3217">**FX_INVALID_MINUTE** (0x16) — недопустимая новая минута.</span><span class="sxs-lookup"><span data-stu-id="887e6-3217">**FX_INVALID_MINUTE** (0x16) New minute is invalid.</span></span>
- <span data-ttu-id="887e6-3218">**FX_INVALID_SECOND** (0x17) — недопустимая новая секунда.</span><span class="sxs-lookup"><span data-stu-id="887e6-3218">**FX_INVALID_SECOND** (0x17) New second is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-3219">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-3219">Allowed From</span></span>

<span data-ttu-id="887e6-3220">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-3220">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-3221">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-3221">Example</span></span>

```c
 UINT status;

/* Set the current system time to hour 23, minute 21, and second 20. */

status = fx_system_time_set(23, 21, 20);

/* If status is FX_SUCCESS, the current system time has been set. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-3222">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-3222">See Also</span></span>

- <span data-ttu-id="887e6-3223">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3223">fx_system_date_get</span></span>
- <span data-ttu-id="887e6-3224">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3224">fx_system_date_set</span></span>
- <span data-ttu-id="887e6-3225">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="887e6-3225">fx_system_initialize</span></span>
- <span data-ttu-id="887e6-3226">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3226">fx_system_time_get</span></span>

## <a name="fx_unicode_directory_create"></a><span data-ttu-id="887e6-3227">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-3227">fx_unicode_directory_create</span></span>

<span data-ttu-id="887e6-3228">Создает каталог Юникода</span><span class="sxs-lookup"><span data-stu-id="887e6-3228">Creates a Unicode directory</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-3229">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-3229">Prototype</span></span>

```c
UINT fx_unicode_directory_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```
### <a name="description"></a><span data-ttu-id="887e6-3230">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-3230">Description</span></span>

<span data-ttu-id="887e6-3231">Эта служба создает подкаталог с именем в Юникоде в текущем каталоге по умолчанию — в параметре имени источника в Юникоде не допускаются сведения о пути.</span><span class="sxs-lookup"><span data-stu-id="887e6-3231">This service creates a Unicode-named subdirectory in the current default directory—no path information is allowed in the Unicode source name parameter.</span></span> <span data-ttu-id="887e6-3232">В случае успешного выполнения служба возвращает короткое имя (формат 8.3) только что созданного подкаталога Юникода.</span><span class="sxs-lookup"><span data-stu-id="887e6-3232">If successful, the short name (8.3 format) of the newly created Unicode subdirectory is returned by the service.</span></span>

> [!WARNING]
> <span data-ttu-id="887e6-3233">*Все операции в подкаталоге Юникода (выбор в качестве пути по умолчанию, удаление и т. д.) должны выполняться путем предоставления возвращенного краткого имени (формат 8.3) стандартным службам каталогов FileX.*</span><span class="sxs-lookup"><span data-stu-id="887e6-3233">*All operations on the Unicode subdirectory (making it the default path, deleting, etc.) should be done by supplying the returned short name (8.3 format) to the standard FileX directory services.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="887e6-3234">*Эта служба не поддерживается на носителях exFAT.*</span><span class="sxs-lookup"><span data-stu-id="887e6-3234">*This service is not supported on exFAT media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-3235">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-3235">Input Parameters</span></span>

- <span data-ttu-id="887e6-3236">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-3236">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="887e6-3237">**source_unicode_name**: указатель на имя в Юникоде для нового подкаталога</span><span class="sxs-lookup"><span data-stu-id="887e6-3237">**source_unicode_name**: Pointer to the Unicode name for the new subdirectory.</span></span>
- <span data-ttu-id="887e6-3238">**source_unicode_length**: длина имени в Юникоде</span><span class="sxs-lookup"><span data-stu-id="887e6-3238">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="887e6-3239">**short_name**: указатель на назначение для краткого имени (формат 8.3) для нового подкаталога Юникода</span><span class="sxs-lookup"><span data-stu-id="887e6-3239">**short_name**: Pointer to destination for short name (8.3 format) for the new Unicode subdirectory.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-3240">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-3240">Return Values</span></span>

- <span data-ttu-id="887e6-3241">**FX_SUCCESS** (0x00) — каталог Юникода успешно задан.</span><span class="sxs-lookup"><span data-stu-id="887e6-3241">**FX_SUCCESS** (0x00) Successful Unicode directory create.</span></span>
- <span data-ttu-id="887e6-3242">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-3242">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="887e6-3243">**FX_ALREADY_CREATED** (0x0B) — указанный каталог уже существует.</span><span class="sxs-lookup"><span data-stu-id="887e6-3243">**FX_ALREADY_CREATED** (0x0B) Specified directory already exists.</span></span>
- <span data-ttu-id="887e6-3244">**FX_NO_MORE_SPACE** (0x0A) — на носителе больше нет доступных кластеров для новой записи каталога.</span><span class="sxs-lookup"><span data-stu-id="887e6-3244">**FX_NO_MORE_SPACE** (0x0A) No more clusters available in the media for the new directory entry.</span></span>
- <span data-ttu-id="887e6-3245">**FX_NOT_IMPLEMENTED** (0x22) — служба не реализована для файловой системы exFAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-3245">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="887e6-3246">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-3246">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="887e6-3247">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.</span><span class="sxs-lookup"><span data-stu-id="887e6-3247">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="887e6-3248">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-3248">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>
- <span data-ttu-id="887e6-3249">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-3249">**FX_IO_ERROR    (0x90)** Driver I/O error.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-3250">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-3250">Allowed From</span></span>

<span data-ttu-id="887e6-3251">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-3251">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-3252">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-3252">Example</span></span>

```c
FX_MEDIA             ram_disk;
UCHAR                 my_short_name[13];
UCHAR                 my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                         0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                         0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                         0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                         0x63,0x00, 0x00,0x00};

/* Create a Unicode subdirectory with the name contained in "my_unicode_name". */

length = fx_unicode_directory_create(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the Unicode subdirectory is created and "my_short_name"
    contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-3253">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-3253">See Also</span></span>

- <span data-ttu-id="887e6-3254">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-3254">fx_directory_attributes_read</span></span>
- <span data-ttu-id="887e6-3255">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3255">fx_directory_attributes_set</span></span>
- <span data-ttu-id="887e6-3256">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-3256">fx_directory_create</span></span>
- <span data-ttu-id="887e6-3257">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3257">fx_directory_default_get</span></span>
- <span data-ttu-id="887e6-3258">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3258">fx_directory_default_set</span></span>
- <span data-ttu-id="887e6-3259">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-3259">fx_directory_delete</span></span>
- <span data-ttu-id="887e6-3260">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-3260">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="887e6-3261">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-3261">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="887e6-3262">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3262">fx_directory_information_get</span></span>
- <span data-ttu-id="887e6-3263">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="887e6-3263">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="887e6-3264">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3264">fx_directory_local_path_get</span></span>
- <span data-ttu-id="887e6-3265">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="887e6-3265">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="887e6-3266">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3266">fx_directory_local_path_set</span></span>
- <span data-ttu-id="887e6-3267">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3267">fx_directory_long_name_get</span></span>
- <span data-ttu-id="887e6-3268">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="887e6-3268">fx_directory_name_test</span></span>
- <span data-ttu-id="887e6-3269">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-3269">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="887e6-3270">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-3270">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="887e6-3271">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-3271">fx_directory_rename</span></span>
- <span data-ttu-id="887e6-3272">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3272">fx_directory_short_name_get</span></span>
- <span data-ttu-id="887e6-3273">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-3273">fx_unicode_directory_rename</span></span>

## <a name="fx_unicode_directory_rename"></a><span data-ttu-id="887e6-3274">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-3274">fx_unicode_directory_rename</span></span>

<span data-ttu-id="887e6-3275">Переименовывает каталог, используя строку в Юникоде</span><span class="sxs-lookup"><span data-stu-id="887e6-3275">Renames directory using Unicode string</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-3276">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-3276">Prototype</span></span>

```c
UINT fx_unicode_directory_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length,
    CHAR *new_short_name);
```
### <a name="description"></a><span data-ttu-id="887e6-3277">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-3277">Description</span></span>

<span data-ttu-id="887e6-3278">Эта служба изменяет подкаталог с именем в Юникоде на указанное новое имя в Юникоде в текущем рабочем каталоге.</span><span class="sxs-lookup"><span data-stu-id="887e6-3278">This service changes a Unicode-named subdirectory to specified new Unicode name in current working directory.</span></span> <span data-ttu-id="887e6-3279">Параметры имени в Юникоде не должны содержать сведения о пути.</span><span class="sxs-lookup"><span data-stu-id="887e6-3279">The Unicode name parameters must not have path information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="887e6-3280">*Эта служба не поддерживается на носителях exFAT.*</span><span class="sxs-lookup"><span data-stu-id="887e6-3280">*This service is not supported on exFAT media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-3281">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-3281">Input Parameters</span></span>

- <span data-ttu-id="887e6-3282">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-3282">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="887e6-3283">**old_unicode_name**: указатель на имя в Юникоде для текущего файла</span><span class="sxs-lookup"><span data-stu-id="887e6-3283">**old_unicode_name**: Pointer to the Unicode name for the current file.</span></span>
- <span data-ttu-id="887e6-3284">**old_unicode_name_length**: длина текущего имени в Юникоде</span><span class="sxs-lookup"><span data-stu-id="887e6-3284">**old_unicode_name_length**: Length of current Unicode name.</span></span>
- <span data-ttu-id="887e6-3285">**new_unicode_name**: указатель на новое имя файла Юникода</span><span class="sxs-lookup"><span data-stu-id="887e6-3285">**new_unicode_name**: Pointer to the new Unicode file name.</span></span>
- <span data-ttu-id="887e6-3286">**old_unicode_name_length**: длина старого имени в Юникоде</span><span class="sxs-lookup"><span data-stu-id="887e6-3286">**old_unicode_name_length**: Length of new Unicode name.</span></span>
- <span data-ttu-id="887e6-3287">**new_short_name**: указатель на назначение для краткого имени (формат 8.3) для переименованного файла в Юникода</span><span class="sxs-lookup"><span data-stu-id="887e6-3287">**new_short_name**: Pointer to destination for short name (8.3 format) for the renamed Unicode file.</span></span> <span data-ttu-id="887e6-3288">Переименование каталога с помощью Юникода</span><span class="sxs-lookup"><span data-stu-id="887e6-3288">Rename Directory with Unicode</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-3289">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-3289">Return Values</span></span>

- <span data-ttu-id="887e6-3290">**FX_SUCCESS** (0x00) — носитель успешно открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-3290">**FX_SUCCESS** (0x00) Successful media open.</span></span>
- <span data-ttu-id="887e6-3291">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-3291">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="887e6-3292">**FX_ALREADY_CREATED** (0x0B) — каталог с указанным именем уже существует.</span><span class="sxs-lookup"><span data-stu-id="887e6-3292">**FX_ALREADY_CREATED** (0x0B) Specified directory name already exists.</span></span>
- <span data-ttu-id="887e6-3293">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-3293">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-3294">**FX_PTR_ERROR** (0x18) — один указатель или несколько имеют значение NULL.</span><span class="sxs-lookup"><span data-stu-id="887e6-3294">**FX_PTR_ERROR** (0x18) One or more pointers are NULL.</span></span>
- <span data-ttu-id="887e6-3295">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-3295">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>
- <span data-ttu-id="887e6-3296">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-3296">**FX_WRITE_PROTECT** (0x23) Specified media is write-protected.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-3297">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-3297">Allowed From</span></span>

<span data-ttu-id="887e6-3298">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-3298">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-3299">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-3299">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
UCHAR                 my_short_name[13];
UCHAR                 my_old_unicode_name[] = {'a', '\0', 'b', '\0', 'c', '\0', '\0', '\0'};
UCHAR                 my_new_unicode_name[] = {'d', '\0', 'e', '\0', 'f', '\0', '\0', '\0'};

/* Change the Unicode-named file "abc" to "def". */

status = fx_unicode_directory_rename(&my_media, my_old_unicode_name,
    3, my_new_unicode_name, 3, my_short_name);

/* If status equals FX_SUCCESS, the directory was changed to "def" and
    "my_short_name" contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-3300">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-3300">See Also</span></span>

- <span data-ttu-id="887e6-3301">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-3301">fx_directory_attributes_read</span></span>
- <span data-ttu-id="887e6-3302">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3302">fx_directory_attributes_set</span></span>
- <span data-ttu-id="887e6-3303">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-3303">fx_directory_create</span></span>
- <span data-ttu-id="887e6-3304">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3304">fx_directory_default_get</span></span>
- <span data-ttu-id="887e6-3305">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3305">fx_directory_default_set</span></span>
- <span data-ttu-id="887e6-3306">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-3306">fx_directory_delete</span></span>
- <span data-ttu-id="887e6-3307">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-3307">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="887e6-3308">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-3308">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="887e6-3309">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3309">fx_directory_information_get</span></span>
- <span data-ttu-id="887e6-3310">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="887e6-3310">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="887e6-3311">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3311">fx_directory_local_path_get</span></span>
- <span data-ttu-id="887e6-3312">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="887e6-3312">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="887e6-3313">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3313">fx_directory_local_path_set</span></span>
- <span data-ttu-id="887e6-3314">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3314">fx_directory_long_name_get</span></span>
- <span data-ttu-id="887e6-3315">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="887e6-3315">fx_directory_name_test</span></span>
- <span data-ttu-id="887e6-3316">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-3316">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="887e6-3317">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="887e6-3317">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="887e6-3318">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-3318">fx_directory_rename</span></span>
- <span data-ttu-id="887e6-3319">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3319">fx_directory_short_name_get</span></span>
- <span data-ttu-id="887e6-3320">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="887e6-3320">fx_unicode_directory_create</span></span>

## <a name="fx_unicode_file_create"></a><span data-ttu-id="887e6-3321">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-3321">fx_unicode_file_create</span></span>

<span data-ttu-id="887e6-3322">Создает файл в Юникоде</span><span class="sxs-lookup"><span data-stu-id="887e6-3322">Creates a Unicode file</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-3323">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-3323">Prototype</span></span>

```c
UINT fx_unicode_file_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```

### <a name="description"></a><span data-ttu-id="887e6-3324">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-3324">Description</span></span>

<span data-ttu-id="887e6-3325">Эта служба создает файл с именем в Юникоде в текущем каталоге по умолчанию — в параметре имени источника в Юникоде не допускаются сведения о пути.</span><span class="sxs-lookup"><span data-stu-id="887e6-3325">This service creates a Unicode-named file in the current default directory—no path information is allowed in the Unicode source name parameter.</span></span> <span data-ttu-id="887e6-3326">В случае успешного выполнения служба возвращает краткое имя (формат 8.3) только что созданного файла в Юникоде.</span><span class="sxs-lookup"><span data-stu-id="887e6-3326">If successful, the short name (8.3 format) of the newly created Unicode file is returned by the service.</span></span>

> [!WARNING]
> <span data-ttu-id="887e6-3327">*Все операции с файлом в Юникоде (открытие, запись, чтение, закрытие и т. д.) должны выполняться путем предоставления возвращенного краткого имени (формат 8.3) стандартным файловым службам FileX.*</span><span class="sxs-lookup"><span data-stu-id="887e6-3327">*All operations on the Unicode file (opening, writing, reading, closing, etc.) should be done by supplying the returned short name (8.3 format) to the standard FileX file services.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-3328">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-3328">Input Parameters</span></span>


- <span data-ttu-id="887e6-3329">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-3329">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="887e6-3330">**source_unicode_name**: указатель на имя в Юникоде для нового файла</span><span class="sxs-lookup"><span data-stu-id="887e6-3330">**source_unicode_name**: Pointer to the Unicode name for the new file.</span></span>
- <span data-ttu-id="887e6-3331">**source_unicode_length**: длина имени в Юникоде</span><span class="sxs-lookup"><span data-stu-id="887e6-3331">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="887e6-3332">**short_name**: указатель на назначение для краткого имени (формат 8.3) для нового файла в Юникоде</span><span class="sxs-lookup"><span data-stu-id="887e6-3332">**short_name**: Pointer to destination for short name (8.3 format) for the new Unicode file.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-3333">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-3333">Return Values</span></span>

- <span data-ttu-id="887e6-3334">**FX_SUCCESS** (0x00) — файл успешно создан.</span><span class="sxs-lookup"><span data-stu-id="887e6-3334">**FX_SUCCESS** (0x00) Successful file create.</span></span>
- <span data-ttu-id="887e6-3335">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-3335">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="887e6-3336">**FX_ALREADY_CREATED** (0x0B) — указанный файл уже существует.</span><span class="sxs-lookup"><span data-stu-id="887e6-3336">**FX_ALREADY_CREATED** (0x0B) Specified file already exists.</span></span>
- <span data-ttu-id="887e6-3337">**FX_NO_MORE_SPACE** (0x0A) — на носителе больше нет доступных кластеров для новой записи файла.</span><span class="sxs-lookup"><span data-stu-id="887e6-3337">**FX_NO_MORE_SPACE** (0x0A) No more clusters available in the media for the new file entry.</span></span>
- <span data-ttu-id="887e6-3338">**FX_NOT_IMPLEMENTED** (0x22) — служба не реализована для файловой системы exFAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-3338">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="887e6-3339">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-3339">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-3340">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-3340">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="887e6-3341">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.</span><span class="sxs-lookup"><span data-stu-id="887e6-3341">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="887e6-3342">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-3342">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-3343">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-3343">Allowed From</span></span>

<span data-ttu-id="887e6-3344">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-3344">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-3345">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-3345">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             my_short_name[13];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Create a Unicode file with the name contained in "my_unicode_name". */

length = fx_unicode_file_create(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the Unicode file is created and "my_short_name"
    contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-3346">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-3346">See Also</span></span>

- <span data-ttu-id="887e6-3347">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-3347">fx_file_allocate</span></span>
- <span data-ttu-id="887e6-3348">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-3348">fx_file_attributes_read</span></span>
- <span data-ttu-id="887e6-3349">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3349">fx_file_attributes_set</span></span>
- <span data-ttu-id="887e6-3350">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-3350">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-3351">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="887e6-3351">fx_file_close</span></span>
- <span data-ttu-id="887e6-3352">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-3352">fx_file_create</span></span>
- <span data-ttu-id="887e6-3353">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3353">fx_file_date_time_set</span></span>
- <span data-ttu-id="887e6-3354">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-3354">fx_file_delete</span></span>
- <span data-ttu-id="887e6-3355">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-3355">fx_file_extended_allocate</span></span>
- <span data-ttu-id="887e6-3356">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-3356">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-3357">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-3357">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="887e6-3358">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-3358">fx_file_extended_seek</span></span>
- <span data-ttu-id="887e6-3359">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-3359">fx_file_extended_truncate</span></span>
- <span data-ttu-id="887e6-3360">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-3360">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="887e6-3361">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="887e6-3361">fx_file_open</span></span>
- <span data-ttu-id="887e6-3362">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="887e6-3362">fx_file_read</span></span>
- <span data-ttu-id="887e6-3363">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-3363">fx_file_relative_seek</span></span>
- <span data-ttu-id="887e6-3364">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-3364">fx_file_rename</span></span>
- <span data-ttu-id="887e6-3365">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-3365">fx_file_seek</span></span>
- <span data-ttu-id="887e6-3366">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-3366">fx_file_truncate</span></span>
- <span data-ttu-id="887e6-3367">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-3367">fx_file_truncate_release</span></span>
- <span data-ttu-id="887e6-3368">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="887e6-3368">fx_file_write</span></span>
- <span data-ttu-id="887e6-3369">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3369">fx_file_write_notify_set</span></span>
- <span data-ttu-id="887e6-3370">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-3370">fx_unicode_file_rename</span></span>
- <span data-ttu-id="887e6-3371">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3371">fx_unicode_name_get</span></span>
- <span data-ttu-id="887e6-3372">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3372">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_file_rename"></a><span data-ttu-id="887e6-3373">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-3373">fx_unicode_file_rename</span></span>

<span data-ttu-id="887e6-3374">Переименовывает файл, используя строку в Юникоде</span><span class="sxs-lookup"><span data-stu-id="887e6-3374">Renames a file using unicode string</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-3375">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-3375">Prototype</span></span>

```c
UINT fx_unicode_file_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length, 
    CHAR *new_short_name);
```

### <a name="description"></a><span data-ttu-id="887e6-3376">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-3376">Description</span></span>

<span data-ttu-id="887e6-3377">Эта служба изменяет файл с именем в Юникоде на указанное новое имя в Юникоде в текущем каталоге по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="887e6-3377">This service changes a Unicode-named file name to specified new Unicode name in current default directory.</span></span> <span data-ttu-id="887e6-3378">Параметры имени в Юникоде не должны содержать сведения о пути.</span><span class="sxs-lookup"><span data-stu-id="887e6-3378">The Unicode name parameters must not have path information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="887e6-3379">*Эта служба не поддерживается на носителях exFAT.*</span><span class="sxs-lookup"><span data-stu-id="887e6-3379">*This service is not supported on exFAT media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-3380">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-3380">Input Parameters</span></span>

- <span data-ttu-id="887e6-3381">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-3381">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="887e6-3382">**old_unicode_name**: указатель на имя в Юникоде для текущего файла</span><span class="sxs-lookup"><span data-stu-id="887e6-3382">**old_unicode_name**: Pointer to the Unicode name for the current file.</span></span>
- <span data-ttu-id="887e6-3383">**old_unicode_name_length**: длина текущего имени в Юникоде</span><span class="sxs-lookup"><span data-stu-id="887e6-3383">**old_unicode_name_length**: Length of current Unicode name.</span></span>
- <span data-ttu-id="887e6-3384">**new_unicode_name**: указатель на новое имя файла Юникода</span><span class="sxs-lookup"><span data-stu-id="887e6-3384">**new_unicode_name**: Pointer to the new Unicode file name.</span></span>
- <span data-ttu-id="887e6-3385">**new_unicode_name_length**: длина нового имени в Юникоде</span><span class="sxs-lookup"><span data-stu-id="887e6-3385">**new_unicode_name_length**: Length of new Unicode name.</span></span>
- <span data-ttu-id="887e6-3386">**new_short_name**: указатель на назначение для краткого имени (формат 8.3) для переименованного файла в Юникода</span><span class="sxs-lookup"><span data-stu-id="887e6-3386">**new_short_name**: Pointer to destination for short name (8.3 format) for the renamed Unicode file.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-3387">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-3387">Return Values</span></span>


- <span data-ttu-id="887e6-3388">**FX_SUCCESS** (0x00) — носитель успешно открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-3388">**FX_SUCCESS** (0x00) Successful media open.</span></span>
- <span data-ttu-id="887e6-3389">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-3389">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="887e6-3390">**FX_ALREADY_CREATED** (0x0B) — файл с указанным именем уже существует.</span><span class="sxs-lookup"><span data-stu-id="887e6-3390">**FX_ALREADY_CREATED** (0x0B) Specified file name already exists.</span></span>
- <span data-ttu-id="887e6-3391">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-3391">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-3392">**FX_PTR_ERROR** (0x18) — один указатель или несколько имеют значение NULL.</span><span class="sxs-lookup"><span data-stu-id="887e6-3392">**FX_PTR_ERROR** (0x18) One or more pointers are NULL.</span></span>
- <span data-ttu-id="887e6-3393">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-3393">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>
- <span data-ttu-id="887e6-3394">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="887e6-3394">**FX_WRITE_PROTECT** (0x23) Specified media is write-protected.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-3395">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-3395">Allowed From</span></span>

<span data-ttu-id="887e6-3396">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-3396">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-3397">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-3397">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
UCHAR                 my_short_name[13];
UCHAR                 my_old_unicode_name[] = {'a', '\0', 'b', '\0', 'c', '\0', '\0', '\0'};
UCHAR                 my_new_unicode_name[] = {'d', '\0', 'e', '\0', 'f', '\0', '\0', '\0'};

/* Change the Unicode-named file "abc" to "def". */

status = fx_unicode_file_rename(&my_media, my_old_unicode_name,
    3, my_new_unicode_name, 3, my_short_name);

/* If status equals FX_SUCCESS, the file name was changed to "def" and
    "my_short_name" contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a><span data-ttu-id="887e6-3398">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-3398">See Also</span></span>

- <span data-ttu-id="887e6-3399">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-3399">fx_file_allocate</span></span>
- <span data-ttu-id="887e6-3400">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-3400">fx_file_attributes_read</span></span>
- <span data-ttu-id="887e6-3401">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3401">fx_file_attributes_set</span></span>
- <span data-ttu-id="887e6-3402">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-3402">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-3403">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="887e6-3403">fx_file_close</span></span>
- <span data-ttu-id="887e6-3404">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-3404">fx_file_create</span></span>
- <span data-ttu-id="887e6-3405">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3405">fx_file_date_time_set</span></span>
- <span data-ttu-id="887e6-3406">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-3406">fx_file_delete</span></span>
- <span data-ttu-id="887e6-3407">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-3407">fx_file_extended_allocate</span></span>
- <span data-ttu-id="887e6-3408">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-3408">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-3409">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-3409">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="887e6-3410">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-3410">fx_file_extended_seek</span></span>
- <span data-ttu-id="887e6-3411">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-3411">fx_file_extended_truncate</span></span>
- <span data-ttu-id="887e6-3412">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-3412">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="887e6-3413">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="887e6-3413">fx_file_open</span></span>
- <span data-ttu-id="887e6-3414">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="887e6-3414">fx_file_read</span></span>
- <span data-ttu-id="887e6-3415">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-3415">fx_file_relative_seek</span></span>
- <span data-ttu-id="887e6-3416">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-3416">fx_file_rename</span></span>
- <span data-ttu-id="887e6-3417">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-3417">fx_file_seek</span></span>
- <span data-ttu-id="887e6-3418">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-3418">fx_file_truncate</span></span>
- <span data-ttu-id="887e6-3419">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-3419">fx_file_truncate_release</span></span>
- <span data-ttu-id="887e6-3420">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="887e6-3420">fx_file_write</span></span>
- <span data-ttu-id="887e6-3421">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3421">fx_file_write_notify_set</span></span>
- <span data-ttu-id="887e6-3422">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-3422">fx_unicode_file_create</span></span>
- <span data-ttu-id="887e6-3423">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3423">fx_unicode_name_get</span></span>
- <span data-ttu-id="887e6-3424">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3424">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_length_get"></a><span data-ttu-id="887e6-3425">fx_unicode_length_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3425">fx_unicode_length_get</span></span>

<span data-ttu-id="887e6-3426">Возвращает длину имени в формате Юникода</span><span class="sxs-lookup"><span data-stu-id="887e6-3426">Gets length of Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-3427">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-3427">Prototype</span></span>

```c
ULONG fx_unicode_length_get(UCHAR *unicode_name);
```
### <a name="description"></a><span data-ttu-id="887e6-3428">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-3428">Description</span></span>

<span data-ttu-id="887e6-3429">Эта служба определяет длину заданного имени в формате Юникода.</span><span class="sxs-lookup"><span data-stu-id="887e6-3429">This service determines the length of the supplied Unicode name.</span></span> <span data-ttu-id="887e6-3430">Символ Юникода представлен двумя байт.</span><span class="sxs-lookup"><span data-stu-id="887e6-3430">A Unicode character is represented by two bytes.</span></span> <span data-ttu-id="887e6-3431">Имя в формате Юникода — это последовательность двухбайтовых символов Юникода, заканчивающихся двумя байт NULL (два байт со значением 0).</span><span class="sxs-lookup"><span data-stu-id="887e6-3431">A Unicode name is a series of two byte Unicode characters terminated by two NULL bytes (two bytes of 0 value).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-3432">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-3432">Input Parameters</span></span>

<span data-ttu-id="887e6-3433">**unicode_name**: указатель на имя в формате Юникода</span><span class="sxs-lookup"><span data-stu-id="887e6-3433">**unicode_name**: Pointer to Unicode name.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-3434">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-3434">Return Values</span></span>

<span data-ttu-id="887e6-3435">**length** — длина имени в формате Юникода (количество символов Юникода в имени).</span><span class="sxs-lookup"><span data-stu-id="887e6-3435">**length**: Length of Unicode name (number of Unicode characters in the name).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-3436">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-3436">Allowed From</span></span>

<span data-ttu-id="887e6-3437">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-3437">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-3438">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-3438">Example</span></span>

```c
UCHAR     my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                           0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                           0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                           0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                           0x63,0x00, 0x00,0x00};

UINT     length;

/* Get the length of "my_unicode_name". */

length = fx_unicode_length_get(my_unicode_name);

/* A value of 17 will be returned for the length of the "my_unicode_name". */
```

### <a name="see-also"></a><span data-ttu-id="887e6-3439">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-3439">See Also</span></span>

- <span data-ttu-id="887e6-3440">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-3440">fx_file_allocate</span></span>
- <span data-ttu-id="887e6-3441">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-3441">fx_file_attributes_read</span></span>
- <span data-ttu-id="887e6-3442">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3442">fx_file_attributes_set</span></span>
- <span data-ttu-id="887e6-3443">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-3443">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-3444">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="887e6-3444">fx_file_close</span></span>
- <span data-ttu-id="887e6-3445">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-3445">fx_file_create</span></span>
- <span data-ttu-id="887e6-3446">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3446">fx_file_date_time_set</span></span>
- <span data-ttu-id="887e6-3447">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-3447">fx_file_delete</span></span>
- <span data-ttu-id="887e6-3448">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-3448">fx_file_extended_allocate</span></span>
- <span data-ttu-id="887e6-3449">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-3449">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-3450">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-3450">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="887e6-3451">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-3451">fx_file_extended_seek</span></span>
- <span data-ttu-id="887e6-3452">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-3452">fx_file_extended_truncate</span></span>
- <span data-ttu-id="887e6-3453">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-3453">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="887e6-3454">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="887e6-3454">fx_file_open</span></span>
- <span data-ttu-id="887e6-3455">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="887e6-3455">fx_file_read</span></span>
- <span data-ttu-id="887e6-3456">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-3456">fx_file_relative_seek</span></span>
- <span data-ttu-id="887e6-3457">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-3457">fx_file_rename</span></span>
- <span data-ttu-id="887e6-3458">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-3458">fx_file_seek</span></span>
- <span data-ttu-id="887e6-3459">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-3459">fx_file_truncate</span></span>
- <span data-ttu-id="887e6-3460">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-3460">fx_file_truncate_release</span></span>
- <span data-ttu-id="887e6-3461">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="887e6-3461">fx_file_write</span></span>
- <span data-ttu-id="887e6-3462">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3462">fx_file_write_notify_set</span></span>
- <span data-ttu-id="887e6-3463">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-3463">fx_unicode_file_create</span></span>
- <span data-ttu-id="887e6-3464">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-3464">fx_unicode_file_rename</span></span>
- <span data-ttu-id="887e6-3465">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3465">fx_unicode_name_get</span></span>
- <span data-ttu-id="887e6-3466">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3466">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_length_get_extended"></a><span data-ttu-id="887e6-3467">fx_unicode_length_get_extended</span><span class="sxs-lookup"><span data-stu-id="887e6-3467">fx_unicode_length_get_extended</span></span>

<span data-ttu-id="887e6-3468">Возвращает длину имени в формате Юникода</span><span class="sxs-lookup"><span data-stu-id="887e6-3468">Gets length of Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-3469">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-3469">Prototype</span></span>

```c
UINT fx_unicode_length_get_extended(
    UCHAR *unicode_name,
    UINT buffer_length);
```
### <a name="description"></a><span data-ttu-id="887e6-3470">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-3470">Description</span></span>

<span data-ttu-id="887e6-3471">Эта служба получает длину заданного имени в формате Юникода.</span><span class="sxs-lookup"><span data-stu-id="887e6-3471">This service gets the length of the supplied Unicode name.</span></span> <span data-ttu-id="887e6-3472">Символ Юникода представлен двумя байт.</span><span class="sxs-lookup"><span data-stu-id="887e6-3472">A Unicode character is represented by two bytes.</span></span> <span data-ttu-id="887e6-3473">Имя в формате Юникода — это последовательность двухбайтовых символов Юникода, заканчивающихся двумя байт NULL (два байт со значением 0).</span><span class="sxs-lookup"><span data-stu-id="887e6-3473">A Unicode name is a series of twobyte Unicode characters terminated by two NULL bytes (two bytes of 0 value).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="887e6-3474">*Эта служба идентична **fx_unicode_length_get()** , за исключением того, что вызывающий объект передает размер буфера **unicode_name**, включая два символа NULL.*</span><span class="sxs-lookup"><span data-stu-id="887e6-3474">*This service is identical to **fx_unicode_length_get()** except the caller passes in the size of the **unicode_name** buffer, including the two NULL characters.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-3475">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-3475">Input Parameters</span></span>

- <span data-ttu-id="887e6-3476">**unicode_name**: указатель на имя в формате Юникода</span><span class="sxs-lookup"><span data-stu-id="887e6-3476">**unicode_name**: Pointer to Unicode name.</span></span>
- <span data-ttu-id="887e6-3477">**buffer_length**: размер буфера имени в формате Юникода</span><span class="sxs-lookup"><span data-stu-id="887e6-3477">**buffer_length**: Size of Unicode name buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-3478">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-3478">Return Values</span></span>

<span data-ttu-id="887e6-3479">**length** — длина имени в формате Юникода (количество символов Юникода в имени).</span><span class="sxs-lookup"><span data-stu-id="887e6-3479">**length**: Length of Unicode name (number of Unicode characters in the name).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-3480">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-3480">Allowed From</span></span>

<span data-ttu-id="887e6-3481">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-3481">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-3482">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-3482">Example</span></span>

```c
UCHAR         my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                 0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                 0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                 0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                 0x63,0x00, 0x00,0x00};

UINT         length;

/* Get the length of "my_unicode_name". */

length = fx_unicode_length_get_extended(my_unicode_name, sizeof(my_unicode_name));

/* A value of 17 will be returned for the length of the "my_unicode_name". */
```

### <a name="see-also"></a><span data-ttu-id="887e6-3483">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-3483">See Also</span></span>

- <span data-ttu-id="887e6-3484">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-3484">fx_file_allocate</span></span>
- <span data-ttu-id="887e6-3485">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-3485">fx_file_attributes_read</span></span>
- <span data-ttu-id="887e6-3486">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3486">fx_file_attributes_set</span></span>
- <span data-ttu-id="887e6-3487">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-3487">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-3488">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="887e6-3488">fx_file_close</span></span>
- <span data-ttu-id="887e6-3489">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-3489">fx_file_create</span></span>
- <span data-ttu-id="887e6-3490">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3490">fx_file_date_time_set</span></span>
- <span data-ttu-id="887e6-3491">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-3491">fx_file_delete</span></span>
- <span data-ttu-id="887e6-3492">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-3492">fx_file_extended_allocate</span></span>
- <span data-ttu-id="887e6-3493">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-3493">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-3494">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-3494">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="887e6-3495">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-3495">fx_file_extended_seek</span></span>
- <span data-ttu-id="887e6-3496">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-3496">fx_file_extended_truncate</span></span>
- <span data-ttu-id="887e6-3497">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-3497">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="887e6-3498">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="887e6-3498">fx_file_open</span></span>
- <span data-ttu-id="887e6-3499">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="887e6-3499">fx_file_read</span></span>
- <span data-ttu-id="887e6-3500">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-3500">fx_file_relative_seek</span></span>
- <span data-ttu-id="887e6-3501">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-3501">fx_file_rename</span></span>
- <span data-ttu-id="887e6-3502">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-3502">fx_file_seek</span></span>
- <span data-ttu-id="887e6-3503">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-3503">fx_file_truncate</span></span>
- <span data-ttu-id="887e6-3504">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-3504">fx_file_truncate_release</span></span>
- <span data-ttu-id="887e6-3505">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="887e6-3505">fx_file_write</span></span>
- <span data-ttu-id="887e6-3506">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3506">fx_file_write_notify_set</span></span>
- <span data-ttu-id="887e6-3507">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-3507">fx_unicode_file_create</span></span>
- <span data-ttu-id="887e6-3508">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-3508">fx_unicode_file_rename</span></span>
- <span data-ttu-id="887e6-3509">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3509">fx_unicode_name_get</span></span>
- <span data-ttu-id="887e6-3510">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3510">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_name_get"></a><span data-ttu-id="887e6-3511">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3511">fx_unicode_name_get</span></span>

<span data-ttu-id="887e6-3512">Получает имя в Юникоде из краткого имени</span><span class="sxs-lookup"><span data-stu-id="887e6-3512">Gets Unicode name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-3513">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-3513">Prototype</span></span>

```c
UINT fx_unicode_name_get(
    FX_MEDIA *media_ptr, 
    CHAR *source_short_name,
    UCHAR *destination_unicode_name, 
    ULONG *destination_unicode_length);
```

### <a name="description"></a><span data-ttu-id="887e6-3514">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-3514">Description</span></span>

<span data-ttu-id="887e6-3515">Эта служба получает имя в Юникоде, связанное с предоставленным кратким именем (формат 8.3) в текущем каталоге по умолчанию — в параметре краткого имени не допускаются сведения о пути.</span><span class="sxs-lookup"><span data-stu-id="887e6-3515">This service retrieves the Unicode-name associated with the supplied short name (8.3 format) within the current default directory—no path information is allowed in the short name parameter.</span></span> <span data-ttu-id="887e6-3516">В случае успешного выполнения служба возвращает имя в Юникоде, связанное с кратким именем.</span><span class="sxs-lookup"><span data-stu-id="887e6-3516">If successful, the Unicode name associated with the short name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="887e6-3517">*Эта служба может использоваться для получения имен в Юникоде для файлов и подкаталогов.*</span><span class="sxs-lookup"><span data-stu-id="887e6-3517">*This service can be used to get Unicode names for both files and subdirectories.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-3518">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-3518">Input Parameters</span></span>

- <span data-ttu-id="887e6-3519">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-3519">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="887e6-3520">**short_name**: указатель на краткое имя (формат 8.3)</span><span class="sxs-lookup"><span data-stu-id="887e6-3520">**short_name** Pointer to short name (8.3 format).</span></span>
- <span data-ttu-id="887e6-3521">**destination_unicode_name**: указатель на назначение для имени в Юникоде, связанного с заданным кратким именем</span><span class="sxs-lookup"><span data-stu-id="887e6-3521">**destination_unicode_name**: Pointer to the destination for the Unicode name associated with the supplied short name.</span></span>
- <span data-ttu-id="887e6-3522">**destination_unicode_length**: указатель на возвращаемую длину имени в Юникоде</span><span class="sxs-lookup"><span data-stu-id="887e6-3522">**destination_unicode_length**: Pointer to returned Unicode name length.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-3523">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-3523">Return Values</span></span>

- <span data-ttu-id="887e6-3524">**FX_SUCCESS** (0x00) — имя в Юникоде успешно получено.</span><span class="sxs-lookup"><span data-stu-id="887e6-3524">**FX_SUCCESS** (0x00) Successful Unicode name retrieval.</span></span>
- <span data-ttu-id="887e6-3525">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать таблицу FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-3525">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="887e6-3526">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-3526">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="887e6-3527">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-3527">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-3528">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-3528">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="887e6-3529">**FX_NOT_FOUND** (0x04) — краткое имя не найдено, или размер назначения Юникода слишком мал.</span><span class="sxs-lookup"><span data-stu-id="887e6-3529">**FX_NOT_FOUND** (0x04) Short name was not found or the Unicode destination size is too small.</span></span>
- <span data-ttu-id="887e6-3530">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-3530">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="887e6-3531">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.</span><span class="sxs-lookup"><span data-stu-id="887e6-3531">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="887e6-3532">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-3532">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-3533">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-3533">Allowed From</span></span>

<span data-ttu-id="887e6-3534">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-3534">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-3535">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-3535">Example</span></span>

```c
FX_MEDIA             ram_disk;
UCHAR                 my_unicode_name[256*2];
ULONG                 unicode_name_length;

/* Get the Unicode name associated with the short name "ABC0~111.TXT".
    Note that the Unicode destination must have 2 times the
    number of maximum characters in the name. */

length = fx_unicode_name_get(&ram_disk, "ABC0~111.TXT", my_unicode_name, unicode_name_length);

/* If successful, the Unicode name is returned in "my_unicode_name". */
```

### <a name="see-also"></a><span data-ttu-id="887e6-3536">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-3536">See Also</span></span>

- <span data-ttu-id="887e6-3537">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-3537">fx_file_allocate</span></span>
- <span data-ttu-id="887e6-3538">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-3538">fx_file_attributes_read</span></span>
- <span data-ttu-id="887e6-3539">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3539">fx_file_attributes_set</span></span>
- <span data-ttu-id="887e6-3540">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-3540">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-3541">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="887e6-3541">fx_file_close</span></span>
- <span data-ttu-id="887e6-3542">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-3542">fx_file_create</span></span>
- <span data-ttu-id="887e6-3543">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3543">fx_file_date_time_set</span></span>
- <span data-ttu-id="887e6-3544">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-3544">fx_file_delete</span></span>
- <span data-ttu-id="887e6-3545">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-3545">fx_file_extended_allocate</span></span>
- <span data-ttu-id="887e6-3546">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-3546">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-3547">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-3547">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="887e6-3548">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-3548">fx_file_extended_seek</span></span>
- <span data-ttu-id="887e6-3549">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-3549">fx_file_extended_truncate</span></span>
- <span data-ttu-id="887e6-3550">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-3550">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="887e6-3551">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="887e6-3551">fx_file_open</span></span>
- <span data-ttu-id="887e6-3552">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="887e6-3552">fx_file_read</span></span>
- <span data-ttu-id="887e6-3553">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-3553">fx_file_relative_seek</span></span>
- <span data-ttu-id="887e6-3554">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-3554">fx_file_rename</span></span>
- <span data-ttu-id="887e6-3555">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-3555">fx_file_seek</span></span>
- <span data-ttu-id="887e6-3556">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-3556">fx_file_truncate</span></span>
- <span data-ttu-id="887e6-3557">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-3557">fx_file_truncate_release</span></span>
- <span data-ttu-id="887e6-3558">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="887e6-3558">fx_file_write</span></span>
- <span data-ttu-id="887e6-3559">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3559">fx_file_write_notify_set</span></span>
- <span data-ttu-id="887e6-3560">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-3560">fx_unicode_file_create</span></span>
- <span data-ttu-id="887e6-3561">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-3561">fx_unicode_file_rename</span></span>
- <span data-ttu-id="887e6-3562">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3562">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_name_get_extended"></a><span data-ttu-id="887e6-3563">fx_unicode_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="887e6-3563">fx_unicode_name_get_extended</span></span>

<span data-ttu-id="887e6-3564">Получает имя в Юникоде из краткого имени</span><span class="sxs-lookup"><span data-stu-id="887e6-3564">Gets Unicode name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-3565">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-3565">Prototype</span></span>

```c
UINT fx_unicode_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *source_short_name,
    UCHAR *destination_unicode_name,
    ULONG *destination_unicode_length,
    ULONG unicode_name_buffer_length);
```
### <a name="description"></a><span data-ttu-id="887e6-3566">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-3566">Description</span></span>

<span data-ttu-id="887e6-3567">Эта служба получает имя в Юникоде, связанное с предоставленным кратким именем (формат 8.3) в текущем каталоге по умолчанию — в параметре краткого имени не допускаются сведения о пути.</span><span class="sxs-lookup"><span data-stu-id="887e6-3567">This service retrieves the Unicode-name associated with the supplied short name (8.3 format) within the current default directory—no path information is allowed in the short name parameter.</span></span> <span data-ttu-id="887e6-3568">В случае успешного выполнения служба возвращает имя в Юникоде, связанное с кратким именем.</span><span class="sxs-lookup"><span data-stu-id="887e6-3568">If successful, the Unicode name associated with the short name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="887e6-3569">\*Эта служба идентична \***fx_unicode_name_get** _, за исключением того, что в качестве входного аргумента вызывающий объект предоставляет размер конечного буфера в Юникоде. Это позволяет службе гарантировать, что она не перезапишет конечный буфер Юникода_.</span><span class="sxs-lookup"><span data-stu-id="887e6-3569">\*This service is identical to \***fx_unicode_name_get**_, except the caller supplies the size of the destination Unicode buffer as an input argument. This allows the service to guarantee that it will not overwrite the destination Unicode buffer_</span></span>

> [!IMPORTANT]
> <span data-ttu-id="887e6-3570">*Эта служба может использоваться для получения имен в Юникоде для файлов и подкаталогов.*</span><span class="sxs-lookup"><span data-stu-id="887e6-3570">*This service can be used to get Unicode names for both files and subdirectories.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-3571">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-3571">Input Parameters</span></span>

- <span data-ttu-id="887e6-3572">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-3572">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="887e6-3573">**short_name**: указатель на краткое имя (формат 8.3)</span><span class="sxs-lookup"><span data-stu-id="887e6-3573">**short_name**: Pointer to short name (8.3 format).</span></span>
- <span data-ttu-id="887e6-3574">**destination_unicode_name**: указатель на назначение для имени в Юникоде, связанного с заданным кратким именем</span><span class="sxs-lookup"><span data-stu-id="887e6-3574">**destination_unicode_name**: Pointer to the destination for the Unicode name associated with the supplied short name.</span></span>
- <span data-ttu-id="887e6-3575">**destination_unicode_length**: указатель на возвращаемую длину имени в Юникоде</span><span class="sxs-lookup"><span data-stu-id="887e6-3575">**destination_unicode_length**: Pointer to returned Unicode name length.</span></span>
- <span data-ttu-id="887e6-3576">**unicode_name_buffer_length**: размер буфера имен в Юникоде</span><span class="sxs-lookup"><span data-stu-id="887e6-3576">**unicode_name_buffer_length**: Size of the Unicode name buffer.</span></span> <span data-ttu-id="887e6-3577">Примечание. Требуется NULL в конце, что добавляет дополнительный байт.</span><span class="sxs-lookup"><span data-stu-id="887e6-3577">Note: A NULL terminator is required, which makes an extra byte.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-3578">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-3578">Return Values</span></span>

- <span data-ttu-id="887e6-3579">**FX_SUCCESS** (0x00) — имя в Юникоде успешно получено.</span><span class="sxs-lookup"><span data-stu-id="887e6-3579">**FX_SUCCESS** (0x00) Successful Unicode name retrieval.</span></span>
- <span data-ttu-id="887e6-3580">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать таблицу FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-3580">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="887e6-3581">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-3581">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="887e6-3582">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-3582">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-3583">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-3583">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="887e6-3584">**FX_NOT_FOUND** (0x04) — краткое имя не найдено, или размер назначения Юникода слишком мал.</span><span class="sxs-lookup"><span data-stu-id="887e6-3584">**FX_NOT_FOUND** (0x04) Short name was not found or the Unicode destination size is too small.</span></span>
- <span data-ttu-id="887e6-3585">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-3585">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="887e6-3586">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.</span><span class="sxs-lookup"><span data-stu-id="887e6-3586">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="887e6-3587">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-3587">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-3588">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-3588">Allowed From</span></span>

<span data-ttu-id="887e6-3589">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-3589">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-3590">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-3590">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             my_unicode_name[256*2];
ULONG             unicode_name_length;

/* Get the Unicode name associated with the short name "ABC0~111.TXT".
    Note that the Unicode destination must have 2 times the number of maximum characters in the name. */

length = fx_unicode_name_get_extended(&ram_disk, "ABC0~111.TXT",
    my_unicode_name,&unicode_name_length, sizeof(ny_unicode_name));

/* If successful, the Unicode name is returned in "my_unicode_name". */
```

### <a name="see-also"></a><span data-ttu-id="887e6-3591">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-3591">See Also</span></span>

- <span data-ttu-id="887e6-3592">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-3592">fx_file_allocate</span></span>
- <span data-ttu-id="887e6-3593">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-3593">fx_file_attributes_read</span></span>
- <span data-ttu-id="887e6-3594">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3594">fx_file_attributes_set</span></span>
- <span data-ttu-id="887e6-3595">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-3595">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-3596">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="887e6-3596">fx_file_close</span></span>
- <span data-ttu-id="887e6-3597">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-3597">fx_file_create</span></span>
- <span data-ttu-id="887e6-3598">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3598">fx_file_date_time_set</span></span>
- <span data-ttu-id="887e6-3599">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-3599">fx_file_delete</span></span>
- <span data-ttu-id="887e6-3600">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-3600">fx_file_extended_allocate</span></span>
- <span data-ttu-id="887e6-3601">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-3601">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-3602">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-3602">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="887e6-3603">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-3603">fx_file_extended_seek</span></span>
- <span data-ttu-id="887e6-3604">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-3604">fx_file_extended_truncate</span></span>
- <span data-ttu-id="887e6-3605">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-3605">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="887e6-3606">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="887e6-3606">fx_file_open</span></span>
- <span data-ttu-id="887e6-3607">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="887e6-3607">fx_file_read</span></span>
- <span data-ttu-id="887e6-3608">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-3608">fx_file_relative_seek</span></span>
- <span data-ttu-id="887e6-3609">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-3609">fx_file_rename</span></span>
- <span data-ttu-id="887e6-3610">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-3610">fx_file_seek</span></span>
- <span data-ttu-id="887e6-3611">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-3611">fx_file_truncate</span></span>
- <span data-ttu-id="887e6-3612">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-3612">fx_file_truncate_release</span></span>
- <span data-ttu-id="887e6-3613">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="887e6-3613">fx_file_write</span></span>
- <span data-ttu-id="887e6-3614">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3614">fx_file_write_notify_set</span></span>
- <span data-ttu-id="887e6-3615">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-3615">fx_unicode_file_create</span></span>
- <span data-ttu-id="887e6-3616">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-3616">fx_unicode_file_rename</span></span>
- <span data-ttu-id="887e6-3617">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3617">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_short_name_get"></a><span data-ttu-id="887e6-3618">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3618">fx_unicode_short_name_get</span></span>

<span data-ttu-id="887e6-3619">Получает краткое имя из имени в Юникоде</span><span class="sxs-lookup"><span data-stu-id="887e6-3619">Gets short name from Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-3620">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-3620">Prototype</span></span>

```c
UINT fx_unicode_short_name_get(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length,
    CHAR *destination_short_name);
```

<span data-ttu-id="887e6-3621">Эта служба получает краткое имя (формат 8.3), связанное с предоставленным именем в Юникоде в текущем каталоге по умолчанию — в параметре имени в Юникоде не допускаются сведения о пути.</span><span class="sxs-lookup"><span data-stu-id="887e6-3621">This service retrieves the short name (8.3 format) associated with the Unicode-name within the current default directory—no path information is allowed in the Unicode name parameter.</span></span> <span data-ttu-id="887e6-3622">В случае успешного выполнения служба возвращает краткое имя, связанное с именем в Юникоде.</span><span class="sxs-lookup"><span data-stu-id="887e6-3622">If successful, the short name associated with the Unicode name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="887e6-3623">*Эта служба может использоваться для получения кратких имен для файлов и подкаталогов.*</span><span class="sxs-lookup"><span data-stu-id="887e6-3623">*This service can be used to get short names for both files and subdirectories.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-3624">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-3624">Input Parameters</span></span>

- <span data-ttu-id="887e6-3625">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-3625">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="887e6-3626">**source_unicode_name**: указатель на имя в формате Юникода</span><span class="sxs-lookup"><span data-stu-id="887e6-3626">**source_unicode_name**: Pointer to Unicode name.</span></span>
- <span data-ttu-id="887e6-3627">**source_unicode_length**: длина имени в Юникоде</span><span class="sxs-lookup"><span data-stu-id="887e6-3627">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="887e6-3628">**destination_short_name**: указатель на назначение краткого имени (формат 8.3)</span><span class="sxs-lookup"><span data-stu-id="887e6-3628">**destination_short_name**: Pointer to destination for the short name (8.3 format).</span></span> <span data-ttu-id="887e6-3629">Размер должен быть не менее 13 байт.</span><span class="sxs-lookup"><span data-stu-id="887e6-3629">This must be at least 13 bytes in size.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-3630">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-3630">Return Values</span></span>

- <span data-ttu-id="887e6-3631">**FX_SUCCESS** (0x00) — краткое имя успешно получено.</span><span class="sxs-lookup"><span data-stu-id="887e6-3631">**FX_SUCCESS** (0x00) Successful short name retrieval.</span></span>
- <span data-ttu-id="887e6-3632">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать таблицу FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-3632">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="887e6-3633">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-3633">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="887e6-3634">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-3634">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-3635">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-3635">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="887e6-3636">**FX_NOT_FOUND** (0x04) — имя в Юникоде не найдено.</span><span class="sxs-lookup"><span data-stu-id="887e6-3636">**FX_NOT_FOUND** (0x04)    Unicode name was not found.</span></span>
- <span data-ttu-id="887e6-3637">**FX_NOT_IMPLEMENTED** (0x22) — служба не реализована для файловой системы exFAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-3637">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="887e6-3638">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-3638">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="887e6-3639">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.</span><span class="sxs-lookup"><span data-stu-id="887e6-3639">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="887e6-3640">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-3640">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-3641">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-3641">Allowed From</span></span>

<span data-ttu-id="887e6-3642">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-3642">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-3643">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-3643">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             my_short_name[13];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Get the short name associated with the Unicode name contained in the array "my_unicode_name". */

length = fx_unicode_short_name_get(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the short name is returned in "my_short_name". */
```

### <a name="see-also"></a><span data-ttu-id="887e6-3644">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-3644">See Also</span></span>

- <span data-ttu-id="887e6-3645">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-3645">fx_file_allocate</span></span>
- <span data-ttu-id="887e6-3646">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-3646">fx_file_attributes_read</span></span>
- <span data-ttu-id="887e6-3647">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3647">fx_file_attributes_set</span></span>
- <span data-ttu-id="887e6-3648">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-3648">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-3649">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="887e6-3649">fx_file_close</span></span>
- <span data-ttu-id="887e6-3650">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-3650">fx_file_create</span></span>
- <span data-ttu-id="887e6-3651">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3651">fx_file_date_time_set</span></span>
- <span data-ttu-id="887e6-3652">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-3652">fx_file_delete</span></span>
- <span data-ttu-id="887e6-3653">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-3653">fx_file_extended_allocate</span></span>
- <span data-ttu-id="887e6-3654">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-3654">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-3655">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-3655">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="887e6-3656">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-3656">fx_file_extended_seek</span></span>
- <span data-ttu-id="887e6-3657">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-3657">fx_file_extended_truncate</span></span>
- <span data-ttu-id="887e6-3658">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-3658">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="887e6-3659">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="887e6-3659">fx_file_open</span></span>
- <span data-ttu-id="887e6-3660">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="887e6-3660">fx_file_read</span></span>
- <span data-ttu-id="887e6-3661">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-3661">fx_file_relative_seek</span></span>
- <span data-ttu-id="887e6-3662">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-3662">fx_file_rename</span></span>
- <span data-ttu-id="887e6-3663">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-3663">fx_file_seek</span></span>
- <span data-ttu-id="887e6-3664">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-3664">fx_file_truncate</span></span>
- <span data-ttu-id="887e6-3665">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-3665">fx_file_truncate_release</span></span>
- <span data-ttu-id="887e6-3666">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="887e6-3666">fx_file_write</span></span>
- <span data-ttu-id="887e6-3667">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3667">fx_file_write_notify_set</span></span>
- <span data-ttu-id="887e6-3668">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-3668">fx_unicode_file_create</span></span>
- <span data-ttu-id="887e6-3669">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-3669">fx_unicode_file_rename</span></span>
- <span data-ttu-id="887e6-3670">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3670">fx_unicode_name_get</span></span>

## <a name="fx_unicode_short_name_get_extended"></a><span data-ttu-id="887e6-3671">fx_unicode_short_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="887e6-3671">fx_unicode_short_name_get_extended</span></span>

<span data-ttu-id="887e6-3672">Получает краткое имя из имени в Юникоде</span><span class="sxs-lookup"><span data-stu-id="887e6-3672">Gets short name from Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="887e6-3673">Прототип</span><span class="sxs-lookup"><span data-stu-id="887e6-3673">Prototype</span></span>

```c
UINT fx_unicode_short_name_get_extended(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *destination_short_name,
    ULONG short_name_buffer_length);
```

### <a name="description"></a><span data-ttu-id="887e6-3674">Описание</span><span class="sxs-lookup"><span data-stu-id="887e6-3674">Description</span></span>

<span data-ttu-id="887e6-3675">Эта служба получает краткое имя (формат 8.3), связанное с предоставленным именем в Юникоде в текущем каталоге по умолчанию — в параметре имени в Юникоде не допускаются сведения о пути.</span><span class="sxs-lookup"><span data-stu-id="887e6-3675">This service retrieves the short name (8.3 format) associated with the Unicode-name within the current default directory—no path information is allowed in the Unicode name parameter.</span></span> <span data-ttu-id="887e6-3676">В случае успешного выполнения служба возвращает краткое имя, связанное с именем в Юникоде.</span><span class="sxs-lookup"><span data-stu-id="887e6-3676">If successful, the short name associated with the Unicode name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="887e6-3677">*Эта служба идентична **fx_unicode_short_name_get()** , за исключением того, что в качестве входного аргумента вызывающий объект предоставляет размер конечного буфера. Это позволяет службе гарантировать, что краткое имя не превысит конечный буфер*.</span><span class="sxs-lookup"><span data-stu-id="887e6-3677">*This service is identical to **fx_unicode_short_name_get()**, except the caller supplies the size of the destination buffer as an input argument. This allows the service to guarantee the short name does not exceed the destination buffer.*</span></span>

<span data-ttu-id="887e6-3678">*Эта служба может использоваться для получения кратких имен для файлов и подкаталогов.*</span><span class="sxs-lookup"><span data-stu-id="887e6-3678">*This service can be used to get short names for both files and subdirectories*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="887e6-3679">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="887e6-3679">Input Parameters</span></span>

- <span data-ttu-id="887e6-3680">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="887e6-3680">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="887e6-3681">**source_unicode_name**: указатель на имя в формате Юникода</span><span class="sxs-lookup"><span data-stu-id="887e6-3681">**source_unicode_name**: Pointer to Unicode name.</span></span>
- <span data-ttu-id="887e6-3682">**source_unicode_length**: длина имени в Юникоде</span><span class="sxs-lookup"><span data-stu-id="887e6-3682">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="887e6-3683">**destination_short_name**: указатель на назначение краткого имени (формат 8.3)</span><span class="sxs-lookup"><span data-stu-id="887e6-3683">**destination_short_name**: Pointer to destination for the short name (8.3 format).</span></span> <span data-ttu-id="887e6-3684">Размер должен быть не менее 13 байт.</span><span class="sxs-lookup"><span data-stu-id="887e6-3684">This must be at least 13 bytes in size.</span></span>
- <span data-ttu-id="887e6-3685">**short_name_buffer_length**: размер буфера назначения</span><span class="sxs-lookup"><span data-stu-id="887e6-3685">**short_name_buffer_length**: Size of the destination buffer.</span></span> <span data-ttu-id="887e6-3686">Размер буфера должен быть не менее 14 байт.</span><span class="sxs-lookup"><span data-stu-id="887e6-3686">The buffer size must be at least 14 bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="887e6-3687">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="887e6-3687">Return Values</span></span>

- <span data-ttu-id="887e6-3688">**FX_SUCCESS** (0x00) — краткое имя успешно получено.</span><span class="sxs-lookup"><span data-stu-id="887e6-3688">**FX_SUCCESS** (0x00) Successful short name retrieval.</span></span>
- <span data-ttu-id="887e6-3689">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать таблицу FAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-3689">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="887e6-3690">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="887e6-3690">**FX_FILE_CORRUPT** (0x08)    File is corrupted</span></span>
- <span data-ttu-id="887e6-3691">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="887e6-3691">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="887e6-3692">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="887e6-3692">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="887e6-3693">**FX_NOT_FOUND** (0x04) — имя в Юникоде не найдено.</span><span class="sxs-lookup"><span data-stu-id="887e6-3693">**FX_NOT_FOUND** (0x04) Unicode name was not found.</span></span>
- <span data-ttu-id="887e6-3694">**FX_NOT_IMPLEMENTED** (0x22) — служба не реализована для файловой системы exFAT.</span><span class="sxs-lookup"><span data-stu-id="887e6-3694">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="887e6-3695">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="887e6-3695">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="887e6-3696">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.</span><span class="sxs-lookup"><span data-stu-id="887e6-3696">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="887e6-3697">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="887e6-3697">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="887e6-3698">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="887e6-3698">Allowed From</span></span>

<span data-ttu-id="887e6-3699">Потоки</span><span class="sxs-lookup"><span data-stu-id="887e6-3699">Threads</span></span>

### <a name="example"></a><span data-ttu-id="887e6-3700">Пример</span><span class="sxs-lookup"><span data-stu-id="887e6-3700">Example</span></span>

```c
#define         SHORT_NAME_BUFFER_SIZE 13
FX_MEDIA         ram_disk;
UCHAR             my_short_name[SHORT_NAME_BUFFER_SIZE];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Get the short name associated with the Unicode name contained in the array "my_unicode_name". */

length = fx_unicode_short_name_get_extended(&ram_disk,
    my_unicode_name, 17, my_short_name,SHORT_NAME_BUFFER_SIZE);

/* If successful, the short name is returned in "my_short_name". */
```

### <a name="see-also"></a><span data-ttu-id="887e6-3701">См. также:</span><span class="sxs-lookup"><span data-stu-id="887e6-3701">See Also</span></span>

- <span data-ttu-id="887e6-3702">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-3702">fx_file_allocate</span></span>
- <span data-ttu-id="887e6-3703">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="887e6-3703">fx_file_attributes_read</span></span>
- <span data-ttu-id="887e6-3704">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3704">fx_file_attributes_set</span></span>
- <span data-ttu-id="887e6-3705">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-3705">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-3706">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="887e6-3706">fx_file_close</span></span>
- <span data-ttu-id="887e6-3707">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-3707">fx_file_create</span></span>
- <span data-ttu-id="887e6-3708">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3708">fx_file_date_time_set</span></span>
- <span data-ttu-id="887e6-3709">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="887e6-3709">fx_file_delete</span></span>
- <span data-ttu-id="887e6-3710">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-3710">fx_file_extended_allocate</span></span>
- <span data-ttu-id="887e6-3711">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="887e6-3711">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="887e6-3712">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-3712">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="887e6-3713">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-3713">fx_file_extended_seek</span></span>
- <span data-ttu-id="887e6-3714">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-3714">fx_file_extended_truncate</span></span>
- <span data-ttu-id="887e6-3715">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-3715">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="887e6-3716">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="887e6-3716">fx_file_open</span></span>
- <span data-ttu-id="887e6-3717">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="887e6-3717">fx_file_read</span></span>
- <span data-ttu-id="887e6-3718">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-3718">fx_file_relative_seek</span></span>
- <span data-ttu-id="887e6-3719">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-3719">fx_file_rename</span></span>
- <span data-ttu-id="887e6-3720">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="887e6-3720">fx_file_seek</span></span>
- <span data-ttu-id="887e6-3721">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="887e6-3721">fx_file_truncate</span></span>
- <span data-ttu-id="887e6-3722">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="887e6-3722">fx_file_truncate_release</span></span>
- <span data-ttu-id="887e6-3723">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="887e6-3723">fx_file_write</span></span>
- <span data-ttu-id="887e6-3724">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="887e6-3724">fx_file_write_notify_set</span></span>
- <span data-ttu-id="887e6-3725">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="887e6-3725">fx_unicode_file_create</span></span>
- <span data-ttu-id="887e6-3726">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="887e6-3726">fx_unicode_file_rename</span></span>
- <span data-ttu-id="887e6-3727">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3727">fx_unicode_name_get</span></span>
- <span data-ttu-id="887e6-3728">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="887e6-3728">fx_unicode_short_name_get</span></span>
