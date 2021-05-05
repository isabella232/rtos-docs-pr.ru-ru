---
title: Глава 4. Описание служб FileX для ОСРВ Azure
description: В этой главе содержится описание всех служб FileX для ОСРВ Azure в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f70b8890be6b12f917ac1724a29559afab33b88d
ms.sourcegitcommit: 0520b2afb6b7f8ae1ea48581e160459fc9292ca7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/30/2021
ms.locfileid: "108297502"
---
# <a name="chapter-4--description-of-azure-rtos-filex-services"></a><span data-ttu-id="ec793-103">Глава 4. Описание служб FileX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="ec793-103">Chapter 4- Description of Azure RTOS FileX services</span></span>

<span data-ttu-id="ec793-104">В этой главе содержится описание всех служб FileX для ОСРВ Azure в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="ec793-104">This chapter contains a description of all Azure RTOS FileX services in alphabetic order.</span></span> <span data-ttu-id="ec793-105">Имена служб реализованы так, что все аналогичные службы группируются вместе.</span><span class="sxs-lookup"><span data-stu-id="ec793-105">Service names are designed so all similar services are grouped together.</span></span>

## <a name="fx_directory_attributes_read"></a><span data-ttu-id="ec793-106">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-106">fx_directory_attributes_read</span></span>

<span data-ttu-id="ec793-107">Считывает атрибуты каталога</span><span class="sxs-lookup"><span data-stu-id="ec793-107">Reads directory attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-108">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-108">Prototype</span></span>

```c
UINT fx_directory_attributes_read ( 
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes_ptr);
```

### <a name="description"></a><span data-ttu-id="ec793-109">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-109">Description</span></span>

<span data-ttu-id="ec793-110">Эта служба считывает атрибуты каталога с указанного носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-110">This service reads the directory's attributes from the specified media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-111">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-111">Input Parameters</span></span>

- <span data-ttu-id="ec793-112">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-112">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="ec793-113">**directory_name**: указатель на имя запрашиваемого каталога (путь к каталогу является необязательным)</span><span class="sxs-lookup"><span data-stu-id="ec793-113">**directory_name**: Pointer to the name of the requested directory (directory path is optional).</span></span>
- <span data-ttu-id="ec793-114">**attributes_ptr**: указатель на назначение для размещения атрибутов каталога</span><span class="sxs-lookup"><span data-stu-id="ec793-114">**attributes** _ptr: Pointer to the destination for the directory's attributes to be placed.</span></span> <span data-ttu-id="ec793-115">Атрибуты каталога возвращаются в формате битовой карты со следующими возможными параметрами.</span><span class="sxs-lookup"><span data-stu-id="ec793-115">The directory attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="ec793-116">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="ec793-116">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="ec793-117">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="ec793-117">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="ec793-118">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="ec793-118">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="ec793-119">FX_VOLUME (0x08)</span><span class="sxs-lookup"><span data-stu-id="ec793-119">FX_VOLUME (0x08)</span></span>
  - <span data-ttu-id="ec793-120">FX_DIRECTORY (0x10)</span><span class="sxs-lookup"><span data-stu-id="ec793-120">FX_DIRECTORY (0x10)</span></span>
  - <span data-ttu-id="ec793-121">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="ec793-121">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-122">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-122">Return Values</span></span>

- <span data-ttu-id="ec793-123">**FX_SUCCESS** (0x00) — атрибуты каталога успешно считаны.</span><span class="sxs-lookup"><span data-stu-id="ec793-123">**FX_SUCCESS** (0x00) Successful directory attributes read</span></span>
- <span data-ttu-id="ec793-124">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-124">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="ec793-125">**FX_NOT_FOUND** (0x04) — указанный каталог не найден на носителе.</span><span class="sxs-lookup"><span data-stu-id="ec793-125">**FX _NOT FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="ec793-126">**FX_NOT_DIRECTORY** (0x0E) — запись является каталогом.</span><span class="sxs-lookup"><span data-stu-id="ec793-126">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory</span></span>
- <span data-ttu-id="ec793-127">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-127">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="ec793-128">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-128">**FX_FILE_CORRUPT** 0x08) File is corrupted</span></span>
- <span data-ttu-id="ec793-129">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-129">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="ec793-130">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-130">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="ec793-131">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="ec793-131">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="ec793-132">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="ec793-132">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="ec793-133">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-133">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="ec793-134">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-134">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-135">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-135">Allowed From</span></span>

<span data-ttu-id="ec793-136">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-136">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-137">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-137">Example</span></span>

```c
FX_MEDIA     my_media;
UINT     status;
/* Retrieve the attributes of "mydir" from the specified media.*/
status = fx_directory_attributes_read(&my_media, "mydir", &attributes);
/* If status equals FX_SUCCESS, "attributes" contains the directory attributes of "mydir". */
```

### <a name="see-also"></a><span data-ttu-id="ec793-138">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-138">See Also</span></span>

- <span data-ttu-id="ec793-139">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-139">fx_directory_attributes_set</span></span>
- <span data-ttu-id="ec793-140">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-140">fx_directory_create</span></span>
- <span data-ttu-id="ec793-141">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="ec793-141">fx_directory_default_get</span></span>
- <span data-ttu-id="ec793-142">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="ec793-142">fx_directory_default_set</span></span>
- <span data-ttu-id="ec793-143">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-143">fx_directory_delete</span></span>
- <span data-ttu-id="ec793-144">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-144">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="ec793-145">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-145">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="ec793-146">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="ec793-146">fx_directory_information_get</span></span>
- <span data-ttu-id="ec793-147">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="ec793-147">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="ec793-148">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="ec793-148">fx_directory_local_path_get</span></span>
- <span data-ttu-id="ec793-149">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="ec793-149">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="ec793-150">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="ec793-150">fx_directory_local_path_set</span></span>
- <span data-ttu-id="ec793-151">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-151">fx_directory_long_name_get</span></span>
- <span data-ttu-id="ec793-152">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="ec793-152">fx_directory_name_test</span></span>
- <span data-ttu-id="ec793-153">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-153">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="ec793-154">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-154">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="ec793-155">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-155">fx_directory_rename</span></span>
- <span data-ttu-id="ec793-156">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-156">fx_directory_short_name_get</span></span>
- <span data-ttu-id="ec793-157">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-157">fx_unicode_directory_create</span></span>
- <span data-ttu-id="ec793-158">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-158">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_attributes_set"></a><span data-ttu-id="ec793-159">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-159">fx_directory_attributes_set</span></span>

<span data-ttu-id="ec793-160">Задает атрибуты каталога</span><span class="sxs-lookup"><span data-stu-id="ec793-160">Sets directory attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-161">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-161">Prototype</span></span>

```c
UINT fx_directory_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes);
```

### <a name="description"></a><span data-ttu-id="ec793-162">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-162">Description</span></span>

<span data-ttu-id="ec793-163">Эта служба задает атрибуты каталога, указанные вызывающим объектом.</span><span class="sxs-lookup"><span data-stu-id="ec793-163">This service sets the directory's attributes to those specified by the caller.</span></span>

> [!WARNING]
> <span data-ttu-id="ec793-164">*Этому приложению разрешено изменять только подмножество атрибутов каталога, используя эту службу. Любая попытка задать дополнительные атрибуты приведет к ошибке.*</span><span class="sxs-lookup"><span data-stu-id="ec793-164">*This application is only allowed to modify a subset of the directory's attributes with this service. Any attempt to set additional attributes will result in an error.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-165">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-165">Input Parameters</span></span>

- <span data-ttu-id="ec793-166">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-166">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="ec793-167">**directory_name**: указатель на имя запрашиваемого каталога (путь к каталогу является необязательным)</span><span class="sxs-lookup"><span data-stu-id="ec793-167">**directory_name**: Pointer to the name of the requested directory (directory path is optional).</span></span>
- <span data-ttu-id="ec793-168">**attributes**: новые атрибуты для этого каталога</span><span class="sxs-lookup"><span data-stu-id="ec793-168">**attributes**: The new attributes to this directory.</span></span> <span data-ttu-id="ec793-169">Допустимые атрибуты каталога определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ec793-169">The valid directory attributes are defined as follows:</span></span>
  - <span data-ttu-id="ec793-170">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="ec793-170">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="ec793-171">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="ec793-171">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="ec793-172">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="ec793-172">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="ec793-173">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="ec793-173">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-174">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-174">Return Values</span></span>

- <span data-ttu-id="ec793-175">**FX_SUCCESS** (0x00) — атрибут каталога успешно задан.</span><span class="sxs-lookup"><span data-stu-id="ec793-175">**FX_SUCCESS** (0x00) Successful directory attribute set</span></span>
- <span data-ttu-id="ec793-176">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-176">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="ec793-177">**FX_NOT_FOUND** (0x04) — указанный каталог не найден на носителе.</span><span class="sxs-lookup"><span data-stu-id="ec793-177">**FX_NOT_FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="ec793-178">**FX_NOT_DIRECTORY** (0x0E) — запись является каталогом.</span><span class="sxs-lookup"><span data-stu-id="ec793-178">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory</span></span>
- <span data-ttu-id="ec793-179">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-179">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="ec793-180">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-180">**FX_WRITE_PROTECT** (0x23) Specified media is write protected</span></span>
- <span data-ttu-id="ec793-181">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-181">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="ec793-182">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-182">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="ec793-183">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-183">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="ec793-184">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="ec793-184">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="ec793-185">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="ec793-185">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="ec793-186">**FX_NO_MORE_ENTRIES** (0x0F) — в этом каталоге больше нет записей.</span><span class="sxs-lookup"><span data-stu-id="ec793-186">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="ec793-187">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-187">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="ec793-188">**FX_INVALID_ATTR** (0x19) — выбраны недопустимые атрибуты.</span><span class="sxs-lookup"><span data-stu-id="ec793-188">**FX_INVALID_ATTR** (0x19) Invalid attributes selected.</span></span>
- <span data-ttu-id="ec793-189">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-189">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-190">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-190">Allowed From</span></span>

<span data-ttu-id="ec793-191">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-191">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-192">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-192">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
status = fx_directory_attributes_set(&my_media, "mydir", FX_READ_ONLY);
/*Set the attributes of "mydir" to read-only. */
/* If status equals FX_SUCCESS, the directory "mydir" is read-only. */
```

### <a name="see-also"></a><span data-ttu-id="ec793-193">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-193">See Also</span></span>

- <span data-ttu-id="ec793-194">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-194">fx_directory_attributes_read</span></span>
- <span data-ttu-id="ec793-195">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-195">fx_directory_create</span></span>
- <span data-ttu-id="ec793-196">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="ec793-196">fx_directory_default_get</span></span>
- <span data-ttu-id="ec793-197">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="ec793-197">fx_directory_default_set</span></span>
- <span data-ttu-id="ec793-198">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-198">fx_directory_delete</span></span>
- <span data-ttu-id="ec793-199">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-199">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="ec793-200">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-200">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="ec793-201">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="ec793-201">fx_directory_information_get</span></span>
- <span data-ttu-id="ec793-202">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="ec793-202">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="ec793-203">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="ec793-203">fx_directory_local_path_get</span></span>
- <span data-ttu-id="ec793-204">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="ec793-204">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="ec793-205">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="ec793-205">fx_directory_local_path_set</span></span>
- <span data-ttu-id="ec793-206">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-206">fx_directory_long_name_get</span></span>
- <span data-ttu-id="ec793-207">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="ec793-207">fx_directory_name_test</span></span>
- <span data-ttu-id="ec793-208">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-208">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="ec793-209">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-209">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="ec793-210">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-210">fx_directory_rename</span></span>
- <span data-ttu-id="ec793-211">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-211">fx_directory_short_name_get</span></span>
- <span data-ttu-id="ec793-212">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-212">fx_unicode_directory_create</span></span>
- <span data-ttu-id="ec793-213">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-213">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_create"></a><span data-ttu-id="ec793-214">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-214">fx_directory_create</span></span>

<span data-ttu-id="ec793-215">Создает подкаталог</span><span class="sxs-lookup"><span data-stu-id="ec793-215">Creates subdirectory</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-216">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-216">Prototype</span></span>

```c
UINT fx_directory_create(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```
### <a name="description"></a><span data-ttu-id="ec793-217">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-217">Description</span></span>

<span data-ttu-id="ec793-218">Эта служба создает подкаталог в текущем каталоге по умолчанию или в пути, указанном в имени каталога.</span><span class="sxs-lookup"><span data-stu-id="ec793-218">This service creates a subdirectory in the current default directory or in the path supplied in the directory name.</span></span> <span data-ttu-id="ec793-219">В отличие от корневого каталога подкаталоги не имеют ограничения на количество файлов, которые могут в них храниться.</span><span class="sxs-lookup"><span data-stu-id="ec793-219">Unlike the root directory, subdirectories do not have a limit on the number of files they can hold.</span></span> <span data-ttu-id="ec793-220">Корневой каталог может содержать только число записей, которое определено загрузочной записью.</span><span class="sxs-lookup"><span data-stu-id="ec793-220">The root directory can only hold the number of entries determined by the boot record.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-221">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-221">Input Parameters</span></span>

- <span data-ttu-id="ec793-222">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-222">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="ec793-223">**directory_name**: указатель на имя создаваемого каталога (путь к каталогу является необязательным)</span><span class="sxs-lookup"><span data-stu-id="ec793-223">**directory_name**: Pointer to the name of the directory to create (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-224">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-224">Return Values</span></span>

- <span data-ttu-id="ec793-225">**FX_SUCCESS** (0x00) — каталог успешно создан.</span><span class="sxs-lookup"><span data-stu-id="ec793-225">**FX_SUCCESS** (0x00) Successful directory create.</span></span>
- <span data-ttu-id="ec793-226">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-226">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="ec793-227">**FX_NOT_FOUND** (0x04) — указанный каталог не найден на носителе.</span><span class="sxs-lookup"><span data-stu-id="ec793-227">**FX_NOT_FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="ec793-228">**FX_NOT_DIRECTORY** (0x0E) — запись является каталогом.</span><span class="sxs-lookup"><span data-stu-id="ec793-228">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory</span></span>
- <span data-ttu-id="ec793-229">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-229">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="ec793-230">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-230">**FX_FILE _CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="ec793-231">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-231">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="ec793-232">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-232">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="ec793-233">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="ec793-233">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="ec793-234">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="ec793-234">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="ec793-235">**FX_NO_MORE_ENTRIES** (0x0F) — в этом каталоге больше нет записей.</span><span class="sxs-lookup"><span data-stu-id="ec793-235">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="ec793-236">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-236">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="ec793-237">**FX_INVALID_ATTR** (0x19) — выбраны недопустимые атрибуты.</span><span class="sxs-lookup"><span data-stu-id="ec793-237">**FX_INVALID_ATTR** (0x19) Invalid attributes selected.</span></span>
- <span data-ttu-id="ec793-238">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-238">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-239">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-239">Allowed From</span></span>

<span data-ttu-id="ec793-240">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-240">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-241">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-241">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
/* Create a subdirectory called "temp" in the current default directory. */

status = fx_directory_create(&my_media, "temp");

/* If status equals FX_SUCCESS, the new subdirectory "temp" has been created. */
```

### <a name="see-also"></a><span data-ttu-id="ec793-242">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-242">See Also</span></span>

- <span data-ttu-id="ec793-243">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-243">fx_directory_attributes_read</span></span>
- <span data-ttu-id="ec793-244">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-244">fx_directory_attributes_set</span></span>
- <span data-ttu-id="ec793-245">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="ec793-245">fx_directory_default_get</span></span>
- <span data-ttu-id="ec793-246">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="ec793-246">fx_directory_default_set</span></span>
- <span data-ttu-id="ec793-247">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-247">fx_directory_delete</span></span>
- <span data-ttu-id="ec793-248">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-248">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="ec793-249">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-249">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="ec793-250">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="ec793-250">fx_directory_information_get</span></span>
- <span data-ttu-id="ec793-251">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="ec793-251">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="ec793-252">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="ec793-252">fx_directory_local_path_get</span></span>
- <span data-ttu-id="ec793-253">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="ec793-253">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="ec793-254">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="ec793-254">fx_directory_local_path_set</span></span>
- <span data-ttu-id="ec793-255">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-255">fx_directory_long_name_get</span></span>
- <span data-ttu-id="ec793-256">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="ec793-256">fx_directory_name_test</span></span>
- <span data-ttu-id="ec793-257">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-257">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="ec793-258">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-258">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="ec793-259">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-259">fx_directory_rename</span></span>
- <span data-ttu-id="ec793-260">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-260">fx_directory_short_name_get</span></span>
- <span data-ttu-id="ec793-261">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-261">fx_unicode_directory_create</span></span>
- <span data-ttu-id="ec793-262">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-262">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_default_get"></a><span data-ttu-id="ec793-263">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="ec793-263">fx_directory_default_get</span></span>

<span data-ttu-id="ec793-264">Получает последний каталог по умолчанию</span><span class="sxs-lookup"><span data-stu-id="ec793-264">Gets last default directory</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-265">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-265">Prototype</span></span>

```c
UINT fx_directory_default_get(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a><span data-ttu-id="ec793-266">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-266">Description</span></span>

<span data-ttu-id="ec793-267">Эта служба возвращает указатель на путь, заданный службой ***fx_directory_default_set*** в последний раз.</span><span class="sxs-lookup"><span data-stu-id="ec793-267">This service returns the pointer to the path last set by ***fx_directory_default_set***.</span></span> <span data-ttu-id="ec793-268">Если каталог по умолчанию не задан или текущий каталог по умолчанию является корневым каталогом, возвращается значение FX_NULL.</span><span class="sxs-lookup"><span data-stu-id="ec793-268">If the default directory has not been set or if the current default directory is the root directory, a value of FX_NULL is returned.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec793-269">*Размер по умолчанию для строки внутреннего пути составляет 256 символов; можно указать другой размер, изменив **FX_MAXIMUM_PATH** в файле **fx_api. h** и перестроив всю библиотеку FileX. Путь к строке символов сохраняется для приложения и не используется FileX внутри.*</span><span class="sxs-lookup"><span data-stu-id="ec793-269">*The default size of the internal path string is 256 characters; it can be changed by modifying **FX_MAXIMUM_PATH** in **fx_api.h** and rebuilding the entire FileX library. The character string path is maintained for the application and is not used internally by FileX.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-270">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-270">Input Parameters</span></span>

- <span data-ttu-id="ec793-271">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-271">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="ec793-272">**return_path_name**: указатель на назначение для последней строки каталога по умолчанию</span><span class="sxs-lookup"><span data-stu-id="ec793-272">**return_path_name**: Pointer to the destination for the last default directory string.</span></span> <span data-ttu-id="ec793-273">Если текущим значением каталога по умолчанию является корневой каталог, возвращается значение FX_NULL.</span><span class="sxs-lookup"><span data-stu-id="ec793-273">A value of FX_NULL is returned if the current setting of the default directory is the root.</span></span> <span data-ttu-id="ec793-274">При открытии носителя по умолчанию используется корневой каталог.</span><span class="sxs-lookup"><span data-stu-id="ec793-274">When the media is opened, root is the default.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-275">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-275">Return Values</span></span>

- <span data-ttu-id="ec793-276">**FX_SUCCESS** (0x00) — каталог по умолчанию успешно получен.</span><span class="sxs-lookup"><span data-stu-id="ec793-276">**FX_SUCCESS** (0x00) Successful default directory get</span></span>
- <span data-ttu-id="ec793-277">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-277">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="ec793-278">**FX_PTR_ERROR** (0x18) — недопустимый указатель места назначения или носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-278">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer.</span></span>
- <span data-ttu-id="ec793-279">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-279">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-280">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-280">Allowed From</span></span>

<span data-ttu-id="ec793-281">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-281">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-282">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-282">Example</span></span>

```c
FX_MEDIA my_media;
CHAR *current_default_dir;
UINT status;
/* Retrieve the current default directory. */
status = fx_directory_default_get(&my_media, &current_default_dir);
/* If status equals FX_SUCCESS, "current_default_dir" 
    contains a pointer to the current default directory).*/
```

### <a name="see-also"></a><span data-ttu-id="ec793-283">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-283">See Also</span></span>

- <span data-ttu-id="ec793-284">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-284">fx_directory_attributes_read</span></span>
- <span data-ttu-id="ec793-285">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-285">fx_directory_attributes_set</span></span>
- <span data-ttu-id="ec793-286">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-286">fx_directory_create</span></span>
- <span data-ttu-id="ec793-287">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="ec793-287">fx_directory_default_set</span></span>
- <span data-ttu-id="ec793-288">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-288">fx_directory_delete</span></span>
- <span data-ttu-id="ec793-289">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-289">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="ec793-290">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-290">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="ec793-291">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="ec793-291">fx_directory_information_get</span></span>
- <span data-ttu-id="ec793-292">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="ec793-292">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="ec793-293">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="ec793-293">fx_directory_local_path_get</span></span>
- <span data-ttu-id="ec793-294">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="ec793-294">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="ec793-295">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="ec793-295">fx_directory_local_path_set</span></span>
- <span data-ttu-id="ec793-296">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-296">fx_directory_long_name_get</span></span>
- <span data-ttu-id="ec793-297">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="ec793-297">fx_directory_name_test</span></span>
- <span data-ttu-id="ec793-298">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-298">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="ec793-299">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-299">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="ec793-300">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-300">fx_directory_rename</span></span>
- <span data-ttu-id="ec793-301">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-301">fx_directory_short_name_get</span></span>
- <span data-ttu-id="ec793-302">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-302">fx_unicode_directory_create</span></span>
- <span data-ttu-id="ec793-303">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-303">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_default_set"></a><span data-ttu-id="ec793-304">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="ec793-304">fx_directory_default_set</span></span>

<span data-ttu-id="ec793-305">Задает каталог по умолчанию</span><span class="sxs-lookup"><span data-stu-id="ec793-305">Sets default directory</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-306">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-306">Prototype</span></span>

```c

UINT fx_directory_default_set(
    FX_MEDIA *media_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a><span data-ttu-id="ec793-307">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-307">Description</span></span>

<span data-ttu-id="ec793-308">Эта служба задает каталог по умолчанию для носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-308">This service sets the default directory of the media.</span></span> <span data-ttu-id="ec793-309">Если указано значение FX_NULL, то в качестве каталога по умолчанию задается корневой каталог носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-309">If a value of FX_NULL is supplied, the default directory is set to the media's root directory.</span></span> <span data-ttu-id="ec793-310">Все последующие операции с файлами, в которых явно не указан путь, по умолчанию будут использовать этот каталог.</span><span class="sxs-lookup"><span data-stu-id="ec793-310">All subsequent file operations that do not explicitly specify a path will default to this directory.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec793-311">*Размер по умолчанию для строки внутреннего пути составляет 256 символов; можно указать другой размер, изменив **FX_MAXIMUM_PATH** в файле **fx_api. h** и перестроив всю библиотеку FileX. Путь к строке символов сохраняется для приложения и не используется FileX внутри.*</span><span class="sxs-lookup"><span data-stu-id="ec793-311">*The default size of the internal path string is 256 characters; it can be changed by modifying **FX_MAXIMUM_PATH** in **fx_api.h** and rebuilding the entire FileX library. The character string path is maintained for the application and is not used internally by FileX.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec793-312">*Для имен, предоставленных приложением, FileX поддерживает как обратную косую черту (\\), так и символ косой черты (/) для разделения каталогов, подкаталогов и имен файлов. Однако в путях, возвращаемых приложению, FileX использует только символ обратной косой черты.*</span><span class="sxs-lookup"><span data-stu-id="ec793-312">*For names supplied by the application, FileX supports both backslash (\\) and forward slash (/) characters to separate directories, subdirectories, and file names. However, FileX only uses the backslash character in paths returned to the application.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-313">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-313">Input Parameters</span></span>

- <span data-ttu-id="ec793-314">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-314">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="ec793-315">**new_path_name**: указатель на новое имя каталога по умолчанию</span><span class="sxs-lookup"><span data-stu-id="ec793-315">**new_path_name**: Pointer to new default directory name.</span></span> <span data-ttu-id="ec793-316">Если указано значение FX_NULL, то в качестве каталога носителя по умолчанию задается корневой каталог носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-316">If a value of FX_NULL is supplied, the default directory of the media is set to the media's root directory.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-317">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-317">Return Values</span></span>

- <span data-ttu-id="ec793-318">**FX_SUCCESS** (0x00) — каталог по умолчанию успешно задан.</span><span class="sxs-lookup"><span data-stu-id="ec793-318">**FX_SUCCESS** (0x00)  Successful default directory set</span></span>
- <span data-ttu-id="ec793-319">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-319">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="ec793-320">**FX_INVALID_PATH** (0x0D) — не удалось найти новый каталог.</span><span class="sxs-lookup"><span data-stu-id="ec793-320">**FX_INVALID_PATH** (0x0D) New directory could not be found</span></span>
- <span data-ttu-id="ec793-321">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-321">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="ec793-322">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-322">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-323">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-323">Allowed From</span></span>

<span data-ttu-id="ec793-324">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-324">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-325">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-325">Example</span></span>

```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_default_set(&my_media, "\\abc\\def\\ghi");
/* If status equals FX_SUCCESS, the default directory for this media is \abc\def\ghi. All subsequent file operations that do not explicitly specify a path will default to this directory. Note that the character "\" serves as an escape character in a string. To represent the character "\", use the construct "\\". This is done because of the C language- only one "\" is really present in the string. */
```

### <a name="see-also"></a><span data-ttu-id="ec793-326">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-326">See Also</span></span>

- <span data-ttu-id="ec793-327">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-327">fx_directory_attributes_read</span></span>
- <span data-ttu-id="ec793-328">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-328">fx_directory_attributes_set</span></span>
- <span data-ttu-id="ec793-329">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-329">fx_directory_create</span></span>
- <span data-ttu-id="ec793-330">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="ec793-330">fx_directory_default_get</span></span>
- <span data-ttu-id="ec793-331">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-331">fx_directory_delete</span></span>
- <span data-ttu-id="ec793-332">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-332">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="ec793-333">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-333">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="ec793-334">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="ec793-334">fx_directory_information_get</span></span>
- <span data-ttu-id="ec793-335">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="ec793-335">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="ec793-336">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="ec793-336">fx_directory_local_path_get</span></span>
- <span data-ttu-id="ec793-337">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="ec793-337">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="ec793-338">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="ec793-338">fx_directory_local_path_set</span></span>
- <span data-ttu-id="ec793-339">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-339">fx_directory_long_name_get</span></span>
- <span data-ttu-id="ec793-340">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="ec793-340">fx_directory_name_test</span></span>
- <span data-ttu-id="ec793-341">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-341">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="ec793-342">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-342">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="ec793-343">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-343">fx_directory_rename</span></span>
- <span data-ttu-id="ec793-344">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-344">fx_directory_short_name_get</span></span>
- <span data-ttu-id="ec793-345">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-345">fx_unicode_directory_create</span></span>
- <span data-ttu-id="ec793-346">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-346">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_delete"></a><span data-ttu-id="ec793-347">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-347">fx_directory_delete</span></span>

<span data-ttu-id="ec793-348">Удаляет подкаталог</span><span class="sxs-lookup"><span data-stu-id="ec793-348">Deletes subdirectory</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-349">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-349">Prototype</span></span>

```c
UINT fx_directory_delete(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a><span data-ttu-id="ec793-350">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-350">Description</span></span>

<span data-ttu-id="ec793-351">Эта служба удаляет указанный каталог.</span><span class="sxs-lookup"><span data-stu-id="ec793-351">This service deletes the specified directory.</span></span> <span data-ttu-id="ec793-352">Обратите внимание, что каталог должен быть пустым, чтобы его можно было удалить.</span><span class="sxs-lookup"><span data-stu-id="ec793-352">Note that the directory must be empty to delete it.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-353">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-353">Input Parameters</span></span>

- <span data-ttu-id="ec793-354">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-354">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="ec793-355">**directory_name**: указатель на имя удаляемого каталога (путь к каталогу является необязательным)</span><span class="sxs-lookup"><span data-stu-id="ec793-355">**directory_name**: Pointer to name of directory to delete (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-356">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-356">Return Values</span></span>

- <span data-ttu-id="ec793-357">**FX_SUCCESS** (0x00) — каталог успешно удален.</span><span class="sxs-lookup"><span data-stu-id="ec793-357">**FX_SUCCESS** (0x00) Successful directory delete</span></span>
- <span data-ttu-id="ec793-358">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-358">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="ec793-359">**FX_NOT_FOUND** (0x04) — указанный каталог не найден.</span><span class="sxs-lookup"><span data-stu-id="ec793-359">**FX_NOT_FOUND** (0x04) Specified directory was not found</span></span>
- <span data-ttu-id="ec793-360">**FX_DIR_NOT_EMPTY** (0x10) — указанный каталог не пуст.</span><span class="sxs-lookup"><span data-stu-id="ec793-360">**FX_DIR_NOT_EMPTY** (0x10) Specified directory is not empty</span></span>
- <span data-ttu-id="ec793-361">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-361">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="ec793-362">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-362">**FX_WRITE_PROTECT** (0x23) Specified media is write protected</span></span>
- <span data-ttu-id="ec793-363">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-363">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="ec793-364">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-364">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="ec793-365">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-365">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="ec793-366">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="ec793-366">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="ec793-367">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="ec793-367">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="ec793-368">**FX_NO_MORE_ENTRIES** (0x0F) — в этом каталоге больше нет записей.</span><span class="sxs-lookup"><span data-stu-id="ec793-368">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="ec793-369">**FX_NOT_DIRECTORY** (0x0E) — не является записью каталога.</span><span class="sxs-lookup"><span data-stu-id="ec793-369">**FX_NOT_DIRECTORY** (0x0E) Not a directory entry</span></span>
- <span data-ttu-id="ec793-370">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-370">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="ec793-371">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-371">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-372">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-372">Allowed From</span></span>

<span data-ttu-id="ec793-373">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-373">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-374">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-374">Example</span></span>
```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_delete(&my_media, "abc");
/* Delete the subdirectory "abc." */
/* If status equals FX_SUCCESS, the subdirectory "abc" was deleted. */
```

### <a name="see-also"></a><span data-ttu-id="ec793-375">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-375">See Also</span></span>

- <span data-ttu-id="ec793-376">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-376">fx_directory_attributes_read</span></span>
- <span data-ttu-id="ec793-377">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-377">fx_directory_attributes_set</span></span>
- <span data-ttu-id="ec793-378">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-378">fx_directory_create</span></span>
- <span data-ttu-id="ec793-379">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="ec793-379">fx_directory_default_get</span></span>
- <span data-ttu-id="ec793-380">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="ec793-380">fx_directory_default_set</span></span>
- <span data-ttu-id="ec793-381">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-381">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="ec793-382">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-382">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="ec793-383">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="ec793-383">fx_directory_information_get</span></span>
- <span data-ttu-id="ec793-384">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="ec793-384">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="ec793-385">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="ec793-385">fx_directory_local_path_get</span></span>
- <span data-ttu-id="ec793-386">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="ec793-386">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="ec793-387">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="ec793-387">fx_directory_local_path_set</span></span>
- <span data-ttu-id="ec793-388">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-388">fx_directory_long_name_get</span></span>
- <span data-ttu-id="ec793-389">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="ec793-389">fx_directory_name_test</span></span>
- <span data-ttu-id="ec793-390">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-390">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="ec793-391">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-391">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="ec793-392">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-392">fx_directory_rename</span></span>
- <span data-ttu-id="ec793-393">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-393">fx_directory_short_name_get</span></span>
- <span data-ttu-id="ec793-394">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-394">fx_unicode_directory_create</span></span>
- <span data-ttu-id="ec793-395">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-395">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_first_entry_find"></a><span data-ttu-id="ec793-396">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-396">fx_directory_first_entry_find</span></span>

<span data-ttu-id="ec793-397">Получает первую запись каталога</span><span class="sxs-lookup"><span data-stu-id="ec793-397">Gets first directory entry</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-398">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-398">Prototype</span></span>

```c
UINT fx_directory_first_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a><span data-ttu-id="ec793-399">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-399">Description</span></span>

<span data-ttu-id="ec793-400">Эта служба получает имя первой записи в каталоге по умолчанию и копирует его в указанное место назначения.</span><span class="sxs-lookup"><span data-stu-id="ec793-400">This service retrieves the first entry name in the default directory and copies it to the specified destination.</span></span>

> [!WARNING]
> <span data-ttu-id="ec793-401">*Указанное назначение должно быть достаточно большим, чтобы вместить имя FileX максимального размера, как определено **FX_MAX_LONG_NAME_LEN.***</span><span class="sxs-lookup"><span data-stu-id="ec793-401">*The specified destination must be large enough to hold the maximum sized FileX name, as defined by **FX_MAX_LONG_NAME_LEN.***</span></span>

> [!WARNING]
> <span data-ttu-id="ec793-402">*При использовании нелокального пути важно предотвратить изменение этого каталога (с помощью семафора ThreadX, мьютекса или изменения уровня приоритета) другими потоками приложения во время обхода каталога. В противном случае могут быть получены недопустимые результаты.*</span><span class="sxs-lookup"><span data-stu-id="ec793-402">*If using a non-local path, it is important to prevent (with a ThreadX semaphore, mutex, or priority level change) other application threads from changing this directory while a directory traversal is taking place. Otherwise, invalid results may be obtained.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-403">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-403">Input Parameters</span></span>

- <span data-ttu-id="ec793-404">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-404">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="ec793-405">**return_entry_name**: указатель на назначение для имени первой записи в каталоге по умолчанию</span><span class="sxs-lookup"><span data-stu-id="ec793-405">**return_entry_name**: Pointer to destination for the first entry name in the default directory.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-406">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-406">Return Values</span></span>

- <span data-ttu-id="ec793-407">**FX_SUCCESS** (0x00) — первая запись каталога успешно найдена.</span><span class="sxs-lookup"><span data-stu-id="ec793-407">**FX_SUCCESS** (0x00) Successful first directory entry find</span></span>
- <span data-ttu-id="ec793-408">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-408">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="ec793-409">**FX_NO_MORE_ENTRIES** (0x0F) — в этом каталоге больше нет записей.</span><span class="sxs-lookup"><span data-stu-id="ec793-409">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="ec793-410">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-410">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="ec793-411">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-411">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="ec793-412">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-412">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="ec793-413">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-413">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="ec793-414">**FX_PTR_ERROR** (0x18) — недопустимый указатель места назначения или носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-414">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer</span></span>
- <span data-ttu-id="ec793-415">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-415">**FX_CALLER_ERROR** (0x20) Caller is not a thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-416">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-416">Allowed From</span></span>

<span data-ttu-id="ec793-417">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-417">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-418">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-418">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;
CHAR             entry[FX_MAX_LONG_NAME_LEN];
/* Retrieve the first directory entry in the current directory. */
status = fx_directory_first_entry_find(&my_media, entry);
/* If status equals FX_SUCCESS, the entry in the directory is the "entry" string. */
```

### <a name="see-also"></a><span data-ttu-id="ec793-419">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-419">See Also</span></span>

- <span data-ttu-id="ec793-420">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-420">fx_directory_attributes_read</span></span>
- <span data-ttu-id="ec793-421">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-421">fx_directory_attributes_set</span></span>
- <span data-ttu-id="ec793-422">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-422">fx_directory_create</span></span>
- <span data-ttu-id="ec793-423">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="ec793-423">fx_directory_default_get</span></span>
- <span data-ttu-id="ec793-424">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="ec793-424">fx_directory_default_set</span></span>
- <span data-ttu-id="ec793-425">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-425">fx_directory_delete</span></span>
- <span data-ttu-id="ec793-426">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-426">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="ec793-427">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="ec793-427">fx_directory_information_get</span></span>
- <span data-ttu-id="ec793-428">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="ec793-428">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="ec793-429">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="ec793-429">fx_directory_local_path_get</span></span>
- <span data-ttu-id="ec793-430">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="ec793-430">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="ec793-431">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="ec793-431">fx_directory_local_path_set</span></span>
- <span data-ttu-id="ec793-432">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-432">fx_directory_long_name_get</span></span>
- <span data-ttu-id="ec793-433">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="ec793-433">fx_directory_name_test</span></span>
- <span data-ttu-id="ec793-434">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-434">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="ec793-435">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-435">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="ec793-436">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-436">fx_directory_rename</span></span>
- <span data-ttu-id="ec793-437">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-437">fx_directory_short_name_get</span></span>
- <span data-ttu-id="ec793-438">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-438">fx_unicode_directory_create</span></span>
- <span data-ttu-id="ec793-439">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-439">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_first_full_entry_find"></a><span data-ttu-id="ec793-440">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-440">fx_directory_first_full_entry_find</span></span>

<span data-ttu-id="ec793-441">Получает первую запись каталога с полной информацией</span><span class="sxs-lookup"><span data-stu-id="ec793-441">Gets first directory entry with full information</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-442">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-442">Prototype</span></span>

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a><span data-ttu-id="ec793-443">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-443">Input Parameters</span></span>

- <span data-ttu-id="ec793-444">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-444">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="ec793-445">**directory_name**: указатель на назначение для имени записи каталога</span><span class="sxs-lookup"><span data-stu-id="ec793-445">**directory_name**: Pointer to the destination for the name of a directory entry.</span></span> <span data-ttu-id="ec793-446">Размер должен быть не меньше FX_MAX_LONG_NAME_LEN.</span><span class="sxs-lookup"><span data-stu-id="ec793-446">Must be at least as big as FX_MAX_LONG_NAME_LEN.</span></span>
- <span data-ttu-id="ec793-447">**attributes_ptr**: указатель на назначение для размещения атрибутов записи, если не NULL</span><span class="sxs-lookup"><span data-stu-id="ec793-447">**attributes**: If non-null, pointer to the destination for the entry's attributes to be placed.</span></span> <span data-ttu-id="ec793-448">Атрибуты возвращаются в формате битовой карты со следующими возможными параметрами.</span><span class="sxs-lookup"><span data-stu-id="ec793-448">The attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="ec793-449">**FX_READ_ONLY** (0x01)</span><span class="sxs-lookup"><span data-stu-id="ec793-449">**FX_READ_ONLY** (0x01)</span></span>
  - <span data-ttu-id="ec793-450">**FX_HIDDEN** (0x02)</span><span class="sxs-lookup"><span data-stu-id="ec793-450">**FX_HIDDEN** (0x02)</span></span>
  - <span data-ttu-id="ec793-451">**FX_SYSTEM** (0x04)</span><span class="sxs-lookup"><span data-stu-id="ec793-451">**FX_SYSTEM** (0x04)</span></span>
  - <span data-ttu-id="ec793-452">**FX_VOLUME** (0x08)</span><span class="sxs-lookup"><span data-stu-id="ec793-452">**FX_VOLUME** (0x08)</span></span>
  - <span data-ttu-id="ec793-453">**FX_DIRECTORY** (0x10)</span><span class="sxs-lookup"><span data-stu-id="ec793-453">**FX_DIRECTORY** (0x10)</span></span>
  - <span data-ttu-id="ec793-454">**FX_ARCHIVE** (0x20)</span><span class="sxs-lookup"><span data-stu-id="ec793-454">**FX_ARCHIVE** (0x20)</span></span>
- <span data-ttu-id="ec793-455">**size**: указатель на назначение для размера записи в байтах, если не NULL</span><span class="sxs-lookup"><span data-stu-id="ec793-455">**size**: If non-null, pointer to the destination for the entry's size in bytes.</span></span>
- <span data-ttu-id="ec793-456">**year**: указатель на назначение для года записи, если не NULL</span><span class="sxs-lookup"><span data-stu-id="ec793-456">**year**: If non-null, pointer to the destination for the entry's year of modification.</span></span>
- <span data-ttu-id="ec793-457">**month**: указатель на назначение для месяца записи, если не NULL</span><span class="sxs-lookup"><span data-stu-id="ec793-457">**month**: If non-null, pointer to the destination for the entry's month of modification.</span></span>
- <span data-ttu-id="ec793-458">**day**: указатель на назначение для дня записи, если не NULL</span><span class="sxs-lookup"><span data-stu-id="ec793-458">**day**: If non-null, pointer to the destination for the entry's day of modification.</span></span>
- <span data-ttu-id="ec793-459">**hour**: указатель на назначение для часа записи, если не NULL</span><span class="sxs-lookup"><span data-stu-id="ec793-459">**hour**: If non-null, pointer to the destination for the entry's hour of modification.</span></span>
- <span data-ttu-id="ec793-460">**minute**: указатель на назначение для минуты записи, если не NULL</span><span class="sxs-lookup"><span data-stu-id="ec793-460">**minute**: If non-null, pointer to the destination for the entry's minute of modification.</span></span>
- <span data-ttu-id="ec793-461">**second**: указатель на назначение для секунды записи, если не NULL</span><span class="sxs-lookup"><span data-stu-id="ec793-461">**second**: If non-null, pointer to the destination for the entry's second of modification.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-462">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-462">Return Values</span></span>

- <span data-ttu-id="ec793-463">**FX_SUCCESS** (0x00) — первая запись каталога успешно найдена.</span><span class="sxs-lookup"><span data-stu-id="ec793-463">**FX_SUCCESS** (0x00) Successful first directory entry find</span></span>
- <span data-ttu-id="ec793-464">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-464">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="ec793-465">**FX_NO_MORE_ENTRIES** (0x0F) — в этом каталоге больше нет записей.</span><span class="sxs-lookup"><span data-stu-id="ec793-465">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="ec793-466">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-466">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="ec793-467">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-467">**FX_WRITE_PROTECT** (0x23) Specified media is write protected</span></span>
- <span data-ttu-id="ec793-468">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-468">**FX_FILE _CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="ec793-469">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-469">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="ec793-470">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-470">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="ec793-471">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="ec793-471">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="ec793-472">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="ec793-472">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="ec793-473">**FX_PTR_ERROR** (0x18) — недопустимый указатель места назначения или носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-473">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer.</span></span>
- <span data-ttu-id="ec793-474">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-474">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-475">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-475">Allowed From</span></span>

<span data-ttu-id="ec793-476">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-476">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-477">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-477">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="ec793-478">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-478">See Also</span></span>

- <span data-ttu-id="ec793-479">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-479">fx_directory_attributes_read</span></span>
- <span data-ttu-id="ec793-480">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-480">fx_directory_attributes_set</span></span>
- <span data-ttu-id="ec793-481">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-481">fx_directory_create</span></span>
- <span data-ttu-id="ec793-482">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="ec793-482">fx_directory_default_get</span></span>
- <span data-ttu-id="ec793-483">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="ec793-483">fx_directory_default_set</span></span>
- <span data-ttu-id="ec793-484">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-484">fx_directory_delete</span></span>
- <span data-ttu-id="ec793-485">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-485">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="ec793-486">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="ec793-486">fx_directory_information_get</span></span>
- <span data-ttu-id="ec793-487">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="ec793-487">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="ec793-488">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="ec793-488">fx_directory_local_path_get</span></span>
- <span data-ttu-id="ec793-489">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="ec793-489">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="ec793-490">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="ec793-490">fx_directory_local_path_set</span></span>
- <span data-ttu-id="ec793-491">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-491">fx_directory_long_name_get</span></span>
- <span data-ttu-id="ec793-492">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="ec793-492">fx_directory_name_test</span></span>
- <span data-ttu-id="ec793-493">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-493">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="ec793-494">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-494">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="ec793-495">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-495">fx_directory_rename</span></span>
- <span data-ttu-id="ec793-496">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-496">fx_directory_short_name_get</span></span>
- <span data-ttu-id="ec793-497">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-497">fx_unicode_directory_create</span></span>
- <span data-ttu-id="ec793-498">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-498">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_information_get"></a><span data-ttu-id="ec793-499">fx_directory_information_get:</span><span class="sxs-lookup"><span data-stu-id="ec793-499">fx_directory_information_get:</span></span>

<span data-ttu-id="ec793-500">Получает сведения о записи каталога</span><span class="sxs-lookup"><span data-stu-id="ec793-500">Gets directory entry information</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-501">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-501">Prototype</span></span>

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a><span data-ttu-id="ec793-502">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-502">Input Parameters</span></span>

- <span data-ttu-id="ec793-503">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-503">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="ec793-504">**directory_name**: указатель на имя записи каталога</span><span class="sxs-lookup"><span data-stu-id="ec793-504">**directory_name**: Pointer to name of the directory entry.</span></span>
- <span data-ttu-id="ec793-505">**attributes**: указатель на назначение для атрибутов</span><span class="sxs-lookup"><span data-stu-id="ec793-505">**attributes**: Pointer to the destination for the attributes.</span></span>
- <span data-ttu-id="ec793-506">**size**: указатель на назначение для размера</span><span class="sxs-lookup"><span data-stu-id="ec793-506">**size**: Pointer to the destination for the size.</span></span>
- <span data-ttu-id="ec793-507">**year**: указатель на назначение для года</span><span class="sxs-lookup"><span data-stu-id="ec793-507">**year**: Pointer to the destination for the year.</span></span>
- <span data-ttu-id="ec793-508">**month**: указатель на назначение для месяца</span><span class="sxs-lookup"><span data-stu-id="ec793-508">**month**: Pointer to the destination for the month.</span></span>
- <span data-ttu-id="ec793-509">**day**: указатель на назначение для дня</span><span class="sxs-lookup"><span data-stu-id="ec793-509">**day**: Pointer to the destination for the day.</span></span>
- <span data-ttu-id="ec793-510">**hour**: указатель на назначение для часа</span><span class="sxs-lookup"><span data-stu-id="ec793-510">**hour**: Pointer to the destination for the hour.</span></span>
- <span data-ttu-id="ec793-511">**minute**: указатель на назначение для минуты</span><span class="sxs-lookup"><span data-stu-id="ec793-511">**minute**: Pointer to the destination for the minute.</span></span>
- <span data-ttu-id="ec793-512">**second**: указатель на назначение для секунды</span><span class="sxs-lookup"><span data-stu-id="ec793-512">**second**: Pointer to the destination for the second.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-513">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-513">Return Values</span></span>

- <span data-ttu-id="ec793-514">**FX_SUCCESS** (0x00) — первая запись каталога успешно найдена.</span><span class="sxs-lookup"><span data-stu-id="ec793-514">**FX_SUCCESS** (0x00) Successful first directory entry find</span></span>
- <span data-ttu-id="ec793-515">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-515">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="ec793-516">**FX_NOT_FOUND** (0x04) — указанный каталог не найден на носителе.</span><span class="sxs-lookup"><span data-stu-id="ec793-516">**FX_NOT_FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="ec793-517">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-517">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="ec793-518">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="ec793-518">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="ec793-519">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-519">**FX_FILE _CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="ec793-520">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-520">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="ec793-521">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="ec793-521">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="ec793-522">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-522">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="ec793-523">**FX_PTR_ERROR** (0x18) — недопустимый указатель места назначения или носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-523">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer.</span></span>
- <span data-ttu-id="ec793-524">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-524">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-525">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-525">Allowed From</span></span>

<span data-ttu-id="ec793-526">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-526">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-527">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-527">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="ec793-528">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-528">See Also</span></span>

- <span data-ttu-id="ec793-529">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-529">fx_directory_attributes_read</span></span>
- <span data-ttu-id="ec793-530">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-530">fx_directory_attributes_set</span></span>
- <span data-ttu-id="ec793-531">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-531">fx_directory_create</span></span>
- <span data-ttu-id="ec793-532">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="ec793-532">fx_directory_default_get</span></span>
- <span data-ttu-id="ec793-533">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="ec793-533">fx_directory_default_set</span></span>
- <span data-ttu-id="ec793-534">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-534">fx_directory_delete</span></span>
- <span data-ttu-id="ec793-535">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-535">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="ec793-536">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-536">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="ec793-537">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="ec793-537">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="ec793-538">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="ec793-538">fx_directory_local_path_get</span></span>
- <span data-ttu-id="ec793-539">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="ec793-539">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="ec793-540">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="ec793-540">fx_directory_local_path_set</span></span>
- <span data-ttu-id="ec793-541">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-541">fx_directory_long_name_get</span></span>
- <span data-ttu-id="ec793-542">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="ec793-542">fx_directory_name_test</span></span>
- <span data-ttu-id="ec793-543">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-543">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="ec793-544">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-544">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="ec793-545">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-545">fx_directory_rename</span></span>
- <span data-ttu-id="ec793-546">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-546">fx_directory_short_name_get</span></span>
- <span data-ttu-id="ec793-547">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-547">fx_unicode_directory_create</span></span>
- <span data-ttu-id="ec793-548">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-548">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_clear"></a><span data-ttu-id="ec793-549">fx_directory_local_path_clear:</span><span class="sxs-lookup"><span data-stu-id="ec793-549">fx_directory_local_path_clear:</span></span>

<span data-ttu-id="ec793-550">Очищает локальный путь по умолчанию</span><span class="sxs-lookup"><span data-stu-id="ec793-550">Clears default local path</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-551">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-551">Prototype</span></span>

```c
UINT fx_directory_local_path_clear(FX_MEDIA *media_ptr);
```

### <a name="description"></a><span data-ttu-id="ec793-552">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-552">Description</span></span>

<span data-ttu-id="ec793-553">Эта служба очищает предыдущий локальный путь, настроенный для вызывающего потока.</span><span class="sxs-lookup"><span data-stu-id="ec793-553">This service clears the previous local path set up for the calling thread.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-554">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-554">Input Parameters</span></span>

- <span data-ttu-id="ec793-555">**media_ptr**: указатель на открытый ранее носитель</span><span class="sxs-lookup"><span data-stu-id="ec793-555">**media_ptr**: Pointer to a previously opened media.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-556">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-556">Return Values</span></span>

- <span data-ttu-id="ec793-557">**FX_SUCCESS** (0x00) — локальный путь успешно очищен.</span><span class="sxs-lookup"><span data-stu-id="ec793-557">**FX_SUCCESS** (0x00) Successful local path clear.</span></span>
- <span data-ttu-id="ec793-558">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель в настоящее время не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-558">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not currently open</span></span>
- <span data-ttu-id="ec793-559">**FX_NOT_IMPLEMENTED** (0x22) — определен FX_NO_LCOAL_PATH.</span><span class="sxs-lookup"><span data-stu-id="ec793-559">**FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH is defined</span></span>
- <span data-ttu-id="ec793-560">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-560">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-561">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-561">Allowed From</span></span>

<span data-ttu-id="ec793-562">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-562">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-563">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-563">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
/* Clear the previously setup local path for this media. */
status = fx_directory_local_path_clear(&my_media);
/* If status equals FX_SUCCESS the local path is cleared. */
```

### <a name="see-also"></a><span data-ttu-id="ec793-564">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-564">See Also</span></span>

- <span data-ttu-id="ec793-565">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-565">fx_directory_attributes_read</span></span>
- <span data-ttu-id="ec793-566">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-566">fx_directory_attributes_set</span></span>
- <span data-ttu-id="ec793-567">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-567">fx_directory_create</span></span>
- <span data-ttu-id="ec793-568">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="ec793-568">fx_directory_default_get</span></span>
- <span data-ttu-id="ec793-569">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="ec793-569">fx_directory_default_set</span></span>
- <span data-ttu-id="ec793-570">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-570">fx_directory_delete</span></span>
- <span data-ttu-id="ec793-571">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-571">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="ec793-572">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-572">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="ec793-573">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="ec793-573">fx_directory_information_get</span></span>
- <span data-ttu-id="ec793-574">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="ec793-574">fx_directory_local_path_get</span></span>
- <span data-ttu-id="ec793-575">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="ec793-575">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="ec793-576">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="ec793-576">fx_directory_local_path_set</span></span>
- <span data-ttu-id="ec793-577">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-577">fx_directory_long_name_get</span></span>
- <span data-ttu-id="ec793-578">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="ec793-578">fx_directory_name_test</span></span>
- <span data-ttu-id="ec793-579">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-579">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="ec793-580">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-580">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="ec793-581">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-581">fx_directory_rename</span></span>
- <span data-ttu-id="ec793-582">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-582">fx_directory_short_name_get</span></span>
- <span data-ttu-id="ec793-583">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-583">fx_unicode_directory_create</span></span>
- <span data-ttu-id="ec793-584">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-584">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_get"></a><span data-ttu-id="ec793-585">fx_directory_local_path_get:</span><span class="sxs-lookup"><span data-stu-id="ec793-585">fx_directory_local_path_get:</span></span>

<span data-ttu-id="ec793-586">Возвращает строку текущего локального пути</span><span class="sxs-lookup"><span data-stu-id="ec793-586">Gets the current local path string</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-587">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-587">Prototype</span></span>

```c
UINT fx_directory_local_path_clear(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a><span data-ttu-id="ec793-588">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-588">Description</span></span>

<span data-ttu-id="ec793-589">Эта служба возвращает указатель локального пути для указанного носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-589">This service returns the local path pointer of the specified media.</span></span> <span data-ttu-id="ec793-590">Если локальный путь не задан, вызывающему объекту возвращается значение NULL.</span><span class="sxs-lookup"><span data-stu-id="ec793-590">If there is no local path set, a NULL is returned to the caller.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-591">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-591">Input Parameters</span></span>

- <span data-ttu-id="ec793-592">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-592">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="ec793-593">**return_path_name**: указатель на указатель строки назначения для сохраняемой строки локального пути</span><span class="sxs-lookup"><span data-stu-id="ec793-593">**return_path_name**: Pointer to the destination string pointer for the local path string to be stored.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-594">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-594">Return Values</span></span>

- <span data-ttu-id="ec793-595">**FX_SUCCESS** (0x00) — локальный путь успешно получен.</span><span class="sxs-lookup"><span data-stu-id="ec793-595">**FX_SUCCESS** (0x00) Successful local path get.</span></span>
- <span data-ttu-id="ec793-596">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель в настоящее время не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-596">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not currently open</span></span>
- <span data-ttu-id="ec793-597">**FX_NOT_IMPLEMENTED** (0x22) — NX_NO_LCOAL_PATH</span><span class="sxs-lookup"><span data-stu-id="ec793-597">**FX_NOT_IMPLEMENTED** (0x22) NX_NO_LCOAL_PATH</span></span>
- <span data-ttu-id="ec793-598">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-598">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>


### <a name="allowed-from"></a><span data-ttu-id="ec793-599">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-599">Allowed From</span></span>

<span data-ttu-id="ec793-600">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-600">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-601">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-601">Example</span></span>

```c
FX_MEDIA         my_media;
CHAR             *my_path;
UINT             status;
/* Retrieve the current local path string. */
status = fx_directory_local_path_get(&my_media, &my_path);
/* If status equals FX_SUCCESS, "my_path" points to the local path string. */
```

### <a name="see-also"></a><span data-ttu-id="ec793-602">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-602">See Also</span></span>

- <span data-ttu-id="ec793-603">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-603">fx_directory_attributes_read</span></span>
- <span data-ttu-id="ec793-604">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-604">fx_directory_attributes_set</span></span>
- <span data-ttu-id="ec793-605">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-605">fx_directory_create</span></span>
- <span data-ttu-id="ec793-606">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="ec793-606">fx_directory_default_get</span></span>
- <span data-ttu-id="ec793-607">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="ec793-607">fx_directory_default_set</span></span>
- <span data-ttu-id="ec793-608">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-608">fx_directory_delete</span></span>
- <span data-ttu-id="ec793-609">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-609">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="ec793-610">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-610">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="ec793-611">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="ec793-611">fx_directory_information_get</span></span>
- <span data-ttu-id="ec793-612">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="ec793-612">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="ec793-613">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="ec793-613">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="ec793-614">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="ec793-614">fx_directory_local_path_set</span></span>
- <span data-ttu-id="ec793-615">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-615">fx_directory_long_name_get</span></span>
- <span data-ttu-id="ec793-616">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="ec793-616">fx_directory_name_test</span></span>
- <span data-ttu-id="ec793-617">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-617">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="ec793-618">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-618">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="ec793-619">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-619">fx_directory_rename</span></span>
- <span data-ttu-id="ec793-620">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-620">fx_directory_short_name_get</span></span>
- <span data-ttu-id="ec793-621">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-621">fx_unicode_directory_create</span></span>
- <span data-ttu-id="ec793-622">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-622">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_restore"></a><span data-ttu-id="ec793-623">fx_directory_local_path_restore:</span><span class="sxs-lookup"><span data-stu-id="ec793-623">fx_directory_local_path_restore:</span></span>

<span data-ttu-id="ec793-624">Восстанавливает предыдущий локальный путь</span><span class="sxs-lookup"><span data-stu-id="ec793-624">Restores previous local path</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-625">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-625">Prototype</span></span>

```c
UINT fx_directory_local_path_restore(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr);
```

### <a name="description"></a><span data-ttu-id="ec793-626">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-626">Description</span></span>

<span data-ttu-id="ec793-627">Эта служба восстанавливает заданный ранее локальный путь.</span><span class="sxs-lookup"><span data-stu-id="ec793-627">This service restores a previously set local path.</span></span> <span data-ttu-id="ec793-628">Также восстанавливается расположение поиска в каталоге по этому локальному пути, что делает эту подпрограмму полезной в рекурсивных обходах каталогов приложением.</span><span class="sxs-lookup"><span data-stu-id="ec793-628">The directory search position made on this local path is also restored, which makes this routine useful in recursive directory traversals by the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec793-629">*Каждый локальный путь содержит строку локального пути размером **FX_MAXIMUM_PATH** (значение по умолчанию — 256 символов). Эта строка внутреннего пути не используется FileX и предоставляется только для использования приложением. Если **FX_LOCAL_PATH** будет объявлена как локальная переменная, пользователям следует помнить, что стек увеличивается на размер этой структуры. Пользователи могут уменьшить размер **FX_MAXIMUM_PATH** и перестроить источник библиотеки FileX.*</span><span class="sxs-lookup"><span data-stu-id="ec793-629">*Each local path contains a local path string of **FX_MAXIMUM_PATH** in size, which by default is 256 characters. This internal path string is not used by FileX and is provided only for the application's use. If **FX_LOCAL_PATH** is going to be declared as a local variable, users should beware of the stack growing by the size of this structure. Users are welcome to reduce the size of **FX_MAXIMUM_PATH** and rebuild the FileX library source.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-630">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-630">Input Parameters</span></span>

- <span data-ttu-id="ec793-631">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-631">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="ec793-632">**local_path_ptr**: указатель на заданный ранее локальный путь</span><span class="sxs-lookup"><span data-stu-id="ec793-632">**local_path_ptr**: Pointer to the previously set local path.</span></span> <span data-ttu-id="ec793-633">Очень важно убедиться, что этот указатель действительно указывает на ранее использовавшийся, но незатронутый локальный путь.</span><span class="sxs-lookup"><span data-stu-id="ec793-633">It's very important to ensure that this pointer does indeed point to a previously used and still intact local path.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-634">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-634">Return Values</span></span>

- <span data-ttu-id="ec793-635">**FX_SUCCESS** (0x00) — локальный путь успешно восстановлен.</span><span class="sxs-lookup"><span data-stu-id="ec793-635">**FX_SUCCESS** (0x00) Successful local path restore.</span></span>
- <span data-ttu-id="ec793-636">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель в настоящее время не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-636">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not currently open.</span></span>
- <span data-ttu-id="ec793-637">**FX_NOT_IMPLEMENTED** (0x22) — определен FX_NO_LCOAL_PATH.</span><span class="sxs-lookup"><span data-stu-id="ec793-637">**FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH is defined.</span></span>
- <span data-ttu-id="ec793-638">**FX_PTR_ERROR** (0x18) — недопустимый указатель на носитель или локальный путь.</span><span class="sxs-lookup"><span data-stu-id="ec793-638">**FX_PTR_ERROR** (0x18) Invalid media or local path pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-639">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-639">Allowed From</span></span>

<span data-ttu-id="ec793-640">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-640">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-641">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-641">Example</span></span>

```c
FX_MEDIA                  my_media;
FX_LOCAL_PATH             my_previous_local_path;
UINT                      status;
/* Restore the previous local path. */
status = fx_directory_local_path_restore(&my_media, &my_previous_local_path);
/* If status equals FX_SUCCESS, the previous local path has been restored. */
```

### <a name="see-also"></a><span data-ttu-id="ec793-642">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-642">See Also</span></span>

- <span data-ttu-id="ec793-643">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-643">fx_directory_attributes_read</span></span>
- <span data-ttu-id="ec793-644">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-644">fx_directory_attributes_set</span></span>
- <span data-ttu-id="ec793-645">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-645">fx_directory_create</span></span>
- <span data-ttu-id="ec793-646">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="ec793-646">fx_directory_default_get</span></span>
- <span data-ttu-id="ec793-647">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="ec793-647">fx_directory_default_set</span></span>
- <span data-ttu-id="ec793-648">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-648">fx_directory_delete</span></span>
- <span data-ttu-id="ec793-649">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-649">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="ec793-650">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-650">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="ec793-651">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="ec793-651">fx_directory_information_get</span></span>
- <span data-ttu-id="ec793-652">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="ec793-652">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="ec793-653">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="ec793-653">fx_directory_local_path_get</span></span>
- <span data-ttu-id="ec793-654">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="ec793-654">fx_directory_local_path_set</span></span>
- <span data-ttu-id="ec793-655">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-655">fx_directory_long_name_get</span></span>
- <span data-ttu-id="ec793-656">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="ec793-656">fx_directory_name_test</span></span>
- <span data-ttu-id="ec793-657">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-657">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="ec793-658">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-658">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="ec793-659">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-659">fx_directory_rename</span></span>
- <span data-ttu-id="ec793-660">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-660">fx_directory_short_name_get</span></span>
- <span data-ttu-id="ec793-661">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-661">fx_unicode_directory_create</span></span>
- <span data-ttu-id="ec793-662">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-662">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_set"></a><span data-ttu-id="ec793-663">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="ec793-663">fx_directory_local_path_set</span></span>

<span data-ttu-id="ec793-664">Задает локальный путь для конкретного потока</span><span class="sxs-lookup"><span data-stu-id="ec793-664">Sets up a thread-specific local path</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-665">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-665">Prototype</span></span>

```c
UINT fx_directory_local_path_set(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a><span data-ttu-id="ec793-666">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-666">Description</span></span>

<span data-ttu-id="ec793-667">Эта служба задает путь для конкретного потока, как указано в \***new_path_string** _.</span><span class="sxs-lookup"><span data-stu-id="ec793-667">This service sets up a thread-specific path as specified by the \***new_path_string** _.</span></span> <span data-ttu-id="ec793-668">После успешного выполнения этой подпрограммы сведения о локальном пути, хранящиеся в файле _ \*_local_path_ptr_\*\*, будут иметь приоритет над глобальным путем к носителю для всех операций с файлами и каталогами, выполняемыми этим потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-668">After successful completion of this routine, the local path information stored in _ *_local_path_ptr_*\* will take precedence over the global media path for all file and directory operations made by this thread.</span></span> <span data-ttu-id="ec793-669">Это не влияет на любой другой поток в системе.</span><span class="sxs-lookup"><span data-stu-id="ec793-669">This will have no impact on any other thread in the system</span></span> 
> [!IMPORTANT]
> <span data-ttu-id="ec793-670">*Размер по умолчанию для строки локального пути составляет 256 символов; можно указать другой размер, изменив **FX_MAXIMUM_PATH** в файле **fx_api. h** и перестроив всю библиотеку FileX. Путь к строке символов сохраняется для приложения и не используется FileX внутри.*</span><span class="sxs-lookup"><span data-stu-id="ec793-670">*The default size of the local path string is 256 characters; it can be changed by modifying **FX_MAXIMUM_PATH** in **fx_api.h** and rebuilding the entire FileX library. The character string path is maintained for the application and is not used internally by FileX.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec793-671">*Для имен, предоставленных приложением, FileX поддерживает как обратную косую черту (\\), так и символ косой черты (/) для разделения каталогов, подкаталогов и имен файлов. Однако в путях, возвращаемых приложению, FileX использует только символ обратной косой черты.*</span><span class="sxs-lookup"><span data-stu-id="ec793-671">*For names supplied by the application, FileX supports both backslash (\\) and forward slash (/) characters to separate directories, subdirectories, and file names. However, FileX only uses the backslash character in paths returned to the application.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-672">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-672">Input Parameters</span></span>

- <span data-ttu-id="ec793-673">**media_ptr**: указатель на открытый ранее носитель</span><span class="sxs-lookup"><span data-stu-id="ec793-673">**media_ptr**: Pointer to the previously opened media.</span></span>
- <span data-ttu-id="ec793-674">**local_path_ptr**: назначение для хранения сведений о локальном пути для конкретного потока</span><span class="sxs-lookup"><span data-stu-id="ec793-674">**local_path_ptr**: Destination for holding the thread-specific local path information.</span></span> <span data-ttu-id="ec793-675">В будущем для функции восстановления локального пути можно предоставить адрес этой структуры.</span><span class="sxs-lookup"><span data-stu-id="ec793-675">The address of this structure may be supplied to the local path restore function in the future.</span></span>
- <span data-ttu-id="ec793-676">**new_path_name**: указывает локальный путь для настройки</span><span class="sxs-lookup"><span data-stu-id="ec793-676">**new_path_name**: Specifies the local path to setup.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-677">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-677">Return Values</span></span>

- <span data-ttu-id="ec793-678">**FX_SUCCESS** (0x00) — каталог по умолчанию успешно задан.</span><span class="sxs-lookup"><span data-stu-id="ec793-678">**FX_SUCCESS** (0x00) Successful default directory set.</span></span>
- <span data-ttu-id="ec793-679">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-679">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="ec793-680">**FX_NOT_IMPLEMENTED** (0x22) — \*\*FX_NO_LCOAL_PATH</span><span class="sxs-lookup"><span data-stu-id="ec793-680">**FX_NOT_IMPLEMENTED** (0x22) \*\*FX_NO_LCOAL_PATH</span></span>
- <span data-ttu-id="ec793-681">**FX_INVALID_PATH** (0x0D) — не удалось найти новый каталог.</span><span class="sxs-lookup"><span data-stu-id="ec793-681">**FX_INVALID_PATH** (0x0D) New directory could not be found.</span></span>
- <span data-ttu-id="ec793-682">**FX_NOT_IMPLEMENTED** (0x22) — определен \*\*FX_NO_LOCAL_PATH.</span><span class="sxs-lookup"><span data-stu-id="ec793-682">**FX_NOT_IMPLEMENTED** (0x22)- \*\*FX_NO_LOCAL_PATH is defined.</span></span>
- <span data-ttu-id="ec793-683">**FX_PTR_ERROR** (0x18) — недопустимый указатель на носитель или локальный путь.</span><span class="sxs-lookup"><span data-stu-id="ec793-683">**FX_PTR_ERROR** (0x18) Invalid media or local path pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-684">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-684">Allowed From</span></span>

<span data-ttu-id="ec793-685">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-685">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-686">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-686">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="ec793-687">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-687">See Also</span></span>

- <span data-ttu-id="ec793-688">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-688">fx_directory_attributes_read</span></span>
- <span data-ttu-id="ec793-689">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-689">fx_directory_attributes_set</span></span>
- <span data-ttu-id="ec793-690">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-690">fx_directory_create</span></span>
- <span data-ttu-id="ec793-691">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="ec793-691">fx_directory_default_get</span></span>
- <span data-ttu-id="ec793-692">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="ec793-692">fx_directory_default_set</span></span>
- <span data-ttu-id="ec793-693">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-693">fx_directory_delete</span></span>
- <span data-ttu-id="ec793-694">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-694">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="ec793-695">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-695">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="ec793-696">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="ec793-696">fx_directory_information_get</span></span>
- <span data-ttu-id="ec793-697">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="ec793-697">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="ec793-698">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="ec793-698">fx_directory_local_path_get</span></span>
- <span data-ttu-id="ec793-699">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="ec793-699">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="ec793-700">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-700">fx_directory_long_name_get</span></span>
- <span data-ttu-id="ec793-701">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="ec793-701">fx_directory_name_test</span></span>
- <span data-ttu-id="ec793-702">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-702">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="ec793-703">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-703">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="ec793-704">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-704">fx_directory_rename</span></span>
- <span data-ttu-id="ec793-705">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-705">fx_directory_short_name_get</span></span>
- <span data-ttu-id="ec793-706">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-706">fx_unicode_directory_create</span></span>
- <span data-ttu-id="ec793-707">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-707">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_long_name_get"></a><span data-ttu-id="ec793-708">fx_directory_long_name_get:</span><span class="sxs-lookup"><span data-stu-id="ec793-708">fx_directory_long_name_get:</span></span>

<span data-ttu-id="ec793-709">Получает длинное имя из краткого имени</span><span class="sxs-lookup"><span data-stu-id="ec793-709">Gets long name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-710">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-710">Prototype</span></span>

```c
UINT fx_directory_long_name_get(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name);
```

### <a name="description"></a><span data-ttu-id="ec793-711">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-711">Description</span></span>

<span data-ttu-id="ec793-712">Эта служба получает длинное имя (если имеется), связанное с переданным кратким именем (формат 8.3).</span><span class="sxs-lookup"><span data-stu-id="ec793-712">This service retrieves the long name (if any) associated with the supplied short (8.3 format) name.</span></span> <span data-ttu-id="ec793-713">Краткое имя может быть либо именем файла, либо именем каталога.</span><span class="sxs-lookup"><span data-stu-id="ec793-713">The short name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-714">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-714">Input Parameters</span></span>

- <span data-ttu-id="ec793-715">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-715">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="ec793-716">**short_name**: указатель на исходное краткое имя (формат 8.3)</span><span class="sxs-lookup"><span data-stu-id="ec793-716">**short_name**: Pointer to source short name (8.3 format).</span></span>
- <span data-ttu-id="ec793-717">**long_name**: указатель на назначение для длинного имени</span><span class="sxs-lookup"><span data-stu-id="ec793-717">**long_name**: Pointer to destination for the long name.</span></span> <span data-ttu-id="ec793-718">Если нет длинного имени, возвращается краткое имя.</span><span class="sxs-lookup"><span data-stu-id="ec793-718">If there is no long name, the short name is returned.</span></span> <span data-ttu-id="ec793-719">Обратите внимание, что назначение для длинного имени должно быть достаточно большим, чтобы вместить FX_MAX_LONG_NAME_LEN символов.</span><span class="sxs-lookup"><span data-stu-id="ec793-719">Note that the destination for the long name must be large enough to hold FX_MAX_LONG_NAME_LEN characters.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-720">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-720">Return Values</span></span>

- <span data-ttu-id="ec793-721">**FX_SUCCESS** (0x00) — длинное имя успешно получено.</span><span class="sxs-lookup"><span data-stu-id="ec793-721">**FX_SUCCESS** (0x00) Successful long name get</span></span>
- <span data-ttu-id="ec793-722">**FX_NOT_FOUND** (0x04) — краткое имя не найдено.</span><span class="sxs-lookup"><span data-stu-id="ec793-722">**FX_NOT_FOUND** (0x04) Short name was not found</span></span>
- <span data-ttu-id="ec793-723">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-723">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="ec793-724">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="ec793-724">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="ec793-725">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-725">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="ec793-726">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-726">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="ec793-727">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-727">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="ec793-728">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="ec793-728">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="ec793-729">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.</span><span class="sxs-lookup"><span data-stu-id="ec793-729">**FX_PTR_ERROR** (0x18) Invalid media or name pointer</span></span>
- <span data-ttu-id="ec793-730">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-730">**FX_CALLER_ERROR** (0x20) Caller is not a thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-731">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-731">Allowed From</span></span>

<span data-ttu-id="ec793-732">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-732">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-733">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-733">Example</span></span>

```c
FX_MEDIA            my_media;
UCHAR               my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */
status = fx_directory_long_name_get(&my_media, "TEXT~01.TXT", my_long_name);
/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ec793-734">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-734">See Also</span></span>

- <span data-ttu-id="ec793-735">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-735">fx_directory_attributes_read</span></span>
- <span data-ttu-id="ec793-736">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-736">fx_directory_attributes_set</span></span>
- <span data-ttu-id="ec793-737">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-737">fx_directory_create</span></span>
- <span data-ttu-id="ec793-738">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="ec793-738">fx_directory_default_get</span></span>
- <span data-ttu-id="ec793-739">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="ec793-739">fx_directory_default_set</span></span>
- <span data-ttu-id="ec793-740">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-740">fx_directory_delete</span></span>
- <span data-ttu-id="ec793-741">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-741">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="ec793-742">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-742">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="ec793-743">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="ec793-743">fx_directory_information_get</span></span>
- <span data-ttu-id="ec793-744">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="ec793-744">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="ec793-745">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="ec793-745">fx_directory_local_path_get</span></span>
- <span data-ttu-id="ec793-746">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="ec793-746">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="ec793-747">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="ec793-747">fx_directory_local_path_set</span></span>
- <span data-ttu-id="ec793-748">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="ec793-748">fx_directory_name_test</span></span>
- <span data-ttu-id="ec793-749">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-749">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="ec793-750">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-750">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="ec793-751">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-751">fx_directory_rename</span></span>
- <span data-ttu-id="ec793-752">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-752">fx_directory_short_name_get</span></span>
- <span data-ttu-id="ec793-753">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-753">fx_unicode_directory_create</span></span>
- <span data-ttu-id="ec793-754">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-754">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_long_name_get_extended"></a><span data-ttu-id="ec793-755">fx_directory_long_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="ec793-755">fx_directory_long_name_get_extended</span></span>

<span data-ttu-id="ec793-756">Получает длинное имя из краткого имени</span><span class="sxs-lookup"><span data-stu-id="ec793-756">Gets long name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-757">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-757">Prototype</span></span>

```c
UINT fx_directory_long_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name,
    UINT long_file_name_buffer_length);
```

### <a name="description"></a><span data-ttu-id="ec793-758">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-758">Description</span></span>

<span data-ttu-id="ec793-759">Эта служба получает длинное имя (если имеется), связанное с переданным кратким именем (формат 8.3).</span><span class="sxs-lookup"><span data-stu-id="ec793-759">This service retrieves the long name (if any) associated with the supplied short (8.3 format) name.</span></span> <span data-ttu-id="ec793-760">Краткое имя может быть либо именем файла, либо именем каталога.</span><span class="sxs-lookup"><span data-stu-id="ec793-760">The short name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-761">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-761">Input Parameters</span></span>

- <span data-ttu-id="ec793-762">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-762">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="ec793-763">**short_name**: указатель на исходное краткое имя (формат 8.3)</span><span class="sxs-lookup"><span data-stu-id="ec793-763">**short_name**: Pointer to source short name (8.3 format).</span></span>
- <span data-ttu-id="ec793-764">**long_name**: указатель на назначение для длинного имени</span><span class="sxs-lookup"><span data-stu-id="ec793-764">**long_name**: Pointer to destination for the long name.</span></span> <span data-ttu-id="ec793-765">Если нет длинного имени, возвращается краткое имя.</span><span class="sxs-lookup"><span data-stu-id="ec793-765">If there is no long name, the short name is returned.</span></span> <span data-ttu-id="ec793-766">Обратите внимание, что назначение для длинного имени должно быть достаточно большим, чтобы вместить **FX_MAX_LONG_NAME_LEN** символов.</span><span class="sxs-lookup"><span data-stu-id="ec793-766">Note: Destination for the long name must be large enough to hold **FX_MAX_LONG_NAME_LEN** characters.</span></span>
- <span data-ttu-id="ec793-767">**long_file_name_buffer_length**: длина буфера длинного имени</span><span class="sxs-lookup"><span data-stu-id="ec793-767">**long_file_name_buffer_length**: Length of the long name buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-768">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-768">Return Values</span></span>

- <span data-ttu-id="ec793-769">**FX_SUCCESS** (0x00) — длинное имя успешно получено.</span><span class="sxs-lookup"><span data-stu-id="ec793-769">**FX_SUCCESS** (0x00) Successful long name get.</span></span>
- <span data-ttu-id="ec793-770">**FX_NOT_FOUND** (0x04) — краткое имя не найдено.</span><span class="sxs-lookup"><span data-stu-id="ec793-770">**FX_NOT_FOUND** (0x04) Short name was not found.</span></span>
- <span data-ttu-id="ec793-771">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-771">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-772">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="ec793-772">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="ec793-773">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-773">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="ec793-774">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-774">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="ec793-775">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-775">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="ec793-776">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="ec793-776">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="ec793-777">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.</span><span class="sxs-lookup"><span data-stu-id="ec793-777">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="ec793-778">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-778">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-779">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-779">Allowed From</span></span>

<span data-ttu-id="ec793-780">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-780">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-781">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-781">Example</span></span>

```c
FX_MEDIA        my_media;
UCHAR            my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */

status = fx_directory_long_name_get_extended(&my_media,
    "TEXT~01.TXT", my_long_name), sizeof(my_long_name));

/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ec793-782">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-782">See Also</span></span>

- <span data-ttu-id="ec793-783">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-783">fx_directory_attributes_read</span></span>
- <span data-ttu-id="ec793-784">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-784">fx_directory_attributes_set</span></span>
- <span data-ttu-id="ec793-785">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-785">fx_directory_create</span></span>
- <span data-ttu-id="ec793-786">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="ec793-786">fx_directory_default_get</span></span>
- <span data-ttu-id="ec793-787">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="ec793-787">fx_directory_default_set</span></span>
- <span data-ttu-id="ec793-788">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-788">fx_directory_delete</span></span>
- <span data-ttu-id="ec793-789">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-789">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="ec793-790">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-790">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="ec793-791">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="ec793-791">fx_directory_information_get</span></span>
- <span data-ttu-id="ec793-792">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="ec793-792">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="ec793-793">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="ec793-793">fx_directory_local_path_get</span></span>
- <span data-ttu-id="ec793-794">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="ec793-794">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="ec793-795">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="ec793-795">fx_directory_local_path_set</span></span>
- <span data-ttu-id="ec793-796">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-796">fx_directory_long_name_get</span></span>
- <span data-ttu-id="ec793-797">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-797">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="ec793-798">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-798">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="ec793-799">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-799">fx_directory_rename</span></span>
- <span data-ttu-id="ec793-800">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-800">fx_directory_short_name_get</span></span>
- <span data-ttu-id="ec793-801">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-801">fx_unicode_directory_create</span></span>
- <span data-ttu-id="ec793-802">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-802">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_name_test"></a><span data-ttu-id="ec793-803">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="ec793-803">fx_directory_name_test</span></span>

<span data-ttu-id="ec793-804">Проверяет каталог</span><span class="sxs-lookup"><span data-stu-id="ec793-804">Tests for directory</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-805">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-805">Prototype</span></span>

```c
UINT fx_directory_name_test(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a><span data-ttu-id="ec793-806">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-806">Description</span></span>

<span data-ttu-id="ec793-807">Эта служба проверяет, является ли переданное имя каталогом.</span><span class="sxs-lookup"><span data-stu-id="ec793-807">This service tests whether or not the supplied name is a directory.</span></span> <span data-ttu-id="ec793-808">Если это так, возвращается FX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="ec793-808">If so, a FX_SUCCESS is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-809">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-809">Input Parameters</span></span>

- <span data-ttu-id="ec793-810">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-810">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="ec793-811">**directory_name**: указатель на имя записи каталога</span><span class="sxs-lookup"><span data-stu-id="ec793-811">**directory_name**: Pointer to name of the directory entry.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-812">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-812">Return Values</span></span>

- <span data-ttu-id="ec793-813">**FX_SUCCESS** (0x00) — указанное имя является каталогом.</span><span class="sxs-lookup"><span data-stu-id="ec793-813">**FX_SUCCESS** (0x00) Supplied name is a directory.</span></span>
- <span data-ttu-id="ec793-814">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-814">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="ec793-815">**FX_NOT_FOUND** (0x04) — не удалось найти запись каталога.</span><span class="sxs-lookup"><span data-stu-id="ec793-815">**FX_NOT_FOUND** (0x04) Directory entry could not be found.</span></span>
- <span data-ttu-id="ec793-816">**FX_NOT_DIRECTORY** (0x0E) — запись не является каталогом.</span><span class="sxs-lookup"><span data-stu-id="ec793-816">**FX_NOT_DIRECTORY** (0x0E)  Entry is not a directory</span></span>
- <span data-ttu-id="ec793-817">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-817">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-818">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="ec793-818">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="ec793-819">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-819">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="ec793-820">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-820">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="ec793-821">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-821">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="ec793-822">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="ec793-822">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="ec793-823">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.</span><span class="sxs-lookup"><span data-stu-id="ec793-823">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="ec793-824">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-824">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-825">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-825">Allowed From</span></span>

<span data-ttu-id="ec793-826">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-826">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-827">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-827">Example</span></span>

```c
FX_MEDIA        my_media;
UNIT             status;
/* Check to see if the name "abc" is directory */

status = fx_directory_name_test(&my_media, "abc");

/* If status equals FX_SUCCESS "abc" is a directory. */
```

### <a name="see-also"></a><span data-ttu-id="ec793-828">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-828">See Also</span></span>

- <span data-ttu-id="ec793-829">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-829">fx_directory_attributes_read</span></span>
- <span data-ttu-id="ec793-830">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-830">fx_directory_attributes_set</span></span>
- <span data-ttu-id="ec793-831">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-831">fx_directory_create</span></span>
- <span data-ttu-id="ec793-832">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="ec793-832">fx_directory_default_get</span></span>
- <span data-ttu-id="ec793-833">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="ec793-833">fx_directory_default_set</span></span>
- <span data-ttu-id="ec793-834">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-834">fx_directory_delete</span></span>
- <span data-ttu-id="ec793-835">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-835">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="ec793-836">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-836">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="ec793-837">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="ec793-837">fx_directory_information_get</span></span>
- <span data-ttu-id="ec793-838">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="ec793-838">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="ec793-839">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="ec793-839">fx_directory_local_path_get</span></span>
- <span data-ttu-id="ec793-840">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="ec793-840">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="ec793-841">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="ec793-841">fx_directory_local_path_set</span></span>
- <span data-ttu-id="ec793-842">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-842">fx_directory_long_name_get</span></span>
- <span data-ttu-id="ec793-843">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-843">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="ec793-844">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-844">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="ec793-845">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-845">fx_directory_rename</span></span>
- <span data-ttu-id="ec793-846">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-846">fx_directory_short_name_get</span></span>
- <span data-ttu-id="ec793-847">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-847">fx_unicode_directory_create</span></span>

## <a name="fx_directory_next_entry_find"></a><span data-ttu-id="ec793-848">fx_directory_next_entry_find:</span><span class="sxs-lookup"><span data-stu-id="ec793-848">fx_directory_next_entry_find:</span></span>

<span data-ttu-id="ec793-849">Выбирает новую запись каталога</span><span class="sxs-lookup"><span data-stu-id="ec793-849">Picks up next directory entry</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-850">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-850">Prototype</span></span>

```c
UINT fx_directory_next_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a><span data-ttu-id="ec793-851">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-851">Description</span></span>

<span data-ttu-id="ec793-852">Эта служба возвращает имя следующей записи в текущем каталоге по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ec793-852">This service returns the next entry name in the current default directory.</span></span>

> [!WARNING]
> <span data-ttu-id="ec793-853">*При использовании нелокального пути также важно предотвратить изменение этого каталога (с помощью семафора ThreadX или уровня приоритета потока) другими потоками приложения во время обхода каталога. В противном случае могут быть получены недопустимые результаты.*</span><span class="sxs-lookup"><span data-stu-id="ec793-853">*If using a non-local path, it is also important to prevent (with a ThreadX semaphore or thread priority level) other application threads from changing this directory while a directory traversal is taking place. Otherwise, invalid results may be obtained.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-854">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-854">Input Parameters</span></span>

- <span data-ttu-id="ec793-855">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-855">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="ec793-856">**return_entry_name**: указатель на назначение для имени следующей записи в каталоге по умолчанию</span><span class="sxs-lookup"><span data-stu-id="ec793-856">**return_entry_name**: Pointer to destination for the next entry name in the default directory.</span></span> <span data-ttu-id="ec793-857">Буфер, на который указывает этот указатель, должен быть достаточно большим, чтобы вместить имя FileX максимального размера, как определено **_FX_MAX_LONG_NAME_LEN_**.</span><span class="sxs-lookup"><span data-stu-id="ec793-857">The buffer this pointer points to must be large enough to hold the maximum size of FileX name, defined by **_FX_MAX_LONG_NAME_LEN_**.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-858">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-858">Return Values</span></span>

- <span data-ttu-id="ec793-859">**FX_SUCCESS** (0x00) — следующая запись успешно найдена.</span><span class="sxs-lookup"><span data-stu-id="ec793-859">**FX_SUCCESS** (0x00) Successful next entry find</span></span>
- <span data-ttu-id="ec793-860">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-860">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="ec793-861">**FX_NO_MORE_ENTRIES** (0x0F) — в этом каталоге больше нет записей.</span><span class="sxs-lookup"><span data-stu-id="ec793-861">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory.</span></span>
- <span data-ttu-id="ec793-862">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-862">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-863">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-863">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="ec793-864">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-864">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="ec793-865">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-865">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="ec793-866">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-866">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="ec793-867">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-867">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="ec793-868">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-868">**FX_CALLER_ERROR** (0x20)     Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-869">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-869">Allowed From</span></span>

<span data-ttu-id="ec793-870">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-870">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-871">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-871">Example</span></span>

```c
FX_MEDIA        my_media;
CHAR            next_name[FX_MAX_LONG_NAME_LEN];
UINT            status;

/* Retrieve the next entry in the default directory. */

status = fx_directory_next_entry_find(&my_media, next_name);

/* If status equals TX_SUCCESS, the name of the next directory entry is in "next_name". */
```

### <a name="see-also"></a><span data-ttu-id="ec793-872">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-872">See Also</span></span>

- <span data-ttu-id="ec793-873">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-873">fx_directory_attributes_read</span></span>
- <span data-ttu-id="ec793-874">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-874">fx_directory_attributes_set</span></span>
- <span data-ttu-id="ec793-875">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-875">fx_directory_create</span></span>
- <span data-ttu-id="ec793-876">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="ec793-876">fx_directory_default_get</span></span>
- <span data-ttu-id="ec793-877">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="ec793-877">fx_directory_default_set</span></span>
- <span data-ttu-id="ec793-878">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-878">fx_directory_delete</span></span>
- <span data-ttu-id="ec793-879">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-879">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="ec793-880">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-880">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="ec793-881">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="ec793-881">fx_directory_information_get</span></span>
- <span data-ttu-id="ec793-882">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="ec793-882">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="ec793-883">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="ec793-883">fx_directory_local_path_get</span></span>
- <span data-ttu-id="ec793-884">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="ec793-884">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="ec793-885">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="ec793-885">fx_directory_local_path_set</span></span>
- <span data-ttu-id="ec793-886">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-886">fx_directory_long_name_get</span></span>
- <span data-ttu-id="ec793-887">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="ec793-887">fx_directory_name_test</span></span>
- <span data-ttu-id="ec793-888">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-888">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="ec793-889">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-889">fx_directory_rename</span></span>
- <span data-ttu-id="ec793-890">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-890">fx_directory_short_name_get</span></span>
- <span data-ttu-id="ec793-891">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-891">fx_unicode_directory_create</span></span>
- <span data-ttu-id="ec793-892">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-892">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_next_full_entry_find"></a><span data-ttu-id="ec793-893">fx_directory_next_full_entry_find:</span><span class="sxs-lookup"><span data-stu-id="ec793-893">fx_directory_next_full_entry_find:</span></span>

<span data-ttu-id="ec793-894">Получает следующую запись каталога с полной информацией</span><span class="sxs-lookup"><span data-stu-id="ec793-894">Gets next directory entry with full information</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-895">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-895">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="ec793-896">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-896">Description</span></span>

<span data-ttu-id="ec793-897">Эта служба получает имя следующей записи в каталоге по умолчанию и копирует его в указанное место назначения.</span><span class="sxs-lookup"><span data-stu-id="ec793-897">This service retrieves the next entry name in the default directory and copies it to the specified destination.</span></span> <span data-ttu-id="ec793-898">Она также возвращает полные сведения о записи, указанные дополнительными входными параметрами.</span><span class="sxs-lookup"><span data-stu-id="ec793-898">It also returns full information about the entry as specified by the additional input parameters.</span></span>

> [!WARNING]
> <span data-ttu-id="ec793-899">\*Указанное назначение должно быть достаточно большим, чтобы вместить имя FileX максимального размера, как определено ***FX_MAX_LONG_NAME_LEN***.</span><span class="sxs-lookup"><span data-stu-id="ec793-899">\*The specified destination must be large enough to hold the maximum sized FileX name, as defined by \*\*\*FX_MAX_LONG_NAME_LEN\*\*\*\*</span></span>

> [!WARNING]
> <span data-ttu-id="ec793-900">*При использовании нелокального пути важно предотвратить изменение этого каталога (с помощью семафора ThreadX, мьютекса или изменения уровня приоритета) другими потоками приложения во время обхода каталога. В противном случае могут быть получены недопустимые результаты.*</span><span class="sxs-lookup"><span data-stu-id="ec793-900">*If using a non-local path, it is important to prevent (with a ThreadX semaphore, mutex, or priority level change) other application threads from changing this directory while a directory traversal is taking place. Otherwise, invalid results may be obtained.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-901">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-901">Input Parameters</span></span>

- <span data-ttu-id="ec793-902">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-902">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="ec793-903">**directory_name**: указатель на назначение для имени записи каталога</span><span class="sxs-lookup"><span data-stu-id="ec793-903">**directory_name**: Pointer to the destination for the name of a directory entry.</span></span> <span data-ttu-id="ec793-904">Размер должен быть не меньше **FX_MAX_LONG_NAME_LEN**.</span><span class="sxs-lookup"><span data-stu-id="ec793-904">Must be at least as big as **FX_MAX_LONG_NAME_LEN**.</span></span>
- <span data-ttu-id="ec793-905">**attributes**: если значение не равно NULL, указатель на назначение для атрибутов записи, которые необходимо разместить. Атрибуты возвращаются в формате битовой карты со следующими возможными параметрами.</span><span class="sxs-lookup"><span data-stu-id="ec793-905">**attributes**: If non-null, pointer to the destination for the entry's attributes to be placed.The attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="ec793-906">**FX_READ_ONLY** (0x01)</span><span class="sxs-lookup"><span data-stu-id="ec793-906">**FX_READ_ONLY** (0x01)</span></span>
  - <span data-ttu-id="ec793-907">**FX_HIDDEN** (0x02)</span><span class="sxs-lookup"><span data-stu-id="ec793-907">**FX_HIDDEN** (0x02)</span></span>
  - <span data-ttu-id="ec793-908">**FX_SYSTEM** (0x04)</span><span class="sxs-lookup"><span data-stu-id="ec793-908">**FX_SYSTEM** (0x04)</span></span>
  - <span data-ttu-id="ec793-909">**FX_VOLUME** (0x08)</span><span class="sxs-lookup"><span data-stu-id="ec793-909">**FX_VOLUME** (0x08)</span></span>
  - <span data-ttu-id="ec793-910">**FX_DIRECTORY** (0x10)</span><span class="sxs-lookup"><span data-stu-id="ec793-910">**FX_DIRECTORY** (0x10)</span></span>
  - <span data-ttu-id="ec793-911">**FX_ARCHIVE** (0x20)</span><span class="sxs-lookup"><span data-stu-id="ec793-911">**FX_ARCHIVE** (0x20)</span></span>
- <span data-ttu-id="ec793-912">**size**: указатель на назначение для размера записи в байтах, если не NULL</span><span class="sxs-lookup"><span data-stu-id="ec793-912">**size**: If non-null, pointer to the destination for the entry's size in bytes.</span></span>
- <span data-ttu-id="ec793-913">**month**: указатель на назначение для месяца записи, если не NULL</span><span class="sxs-lookup"><span data-stu-id="ec793-913">**month**: If non-null, pointer to the destination for the entry's month of modification.</span></span>
- <span data-ttu-id="ec793-914">**year**: указатель на назначение для года записи, если не NULL</span><span class="sxs-lookup"><span data-stu-id="ec793-914">**year**: If non-null, pointer to the destination for the entry's year of modification.</span></span>
- <span data-ttu-id="ec793-915">**day**: указатель на назначение для дня записи, если не NULL</span><span class="sxs-lookup"><span data-stu-id="ec793-915">**day**: If non-null, pointer to the destination for the entry's day of modification.</span></span>
- <span data-ttu-id="ec793-916">**hour**: указатель на назначение для часа записи, если не NULL</span><span class="sxs-lookup"><span data-stu-id="ec793-916">**hour**: If non-null, pointer to the destination for the entry's hour of modification.</span></span>
- <span data-ttu-id="ec793-917">**minute**: указатель на назначение для минуты записи, если не NULL</span><span class="sxs-lookup"><span data-stu-id="ec793-917">**minute**: If non-null, pointer to the destination for the entry's minute of modification.</span></span>
- <span data-ttu-id="ec793-918">**second**: указатель на назначение для секунды записи, если не NULL</span><span class="sxs-lookup"><span data-stu-id="ec793-918">**second**: If non-null, pointer to the destination for the entry's second of modification.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-919">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-919">Return Values</span></span>

- <span data-ttu-id="ec793-920">**FX_SUCCESS** (0x00) — следующая запись каталога успешно найдена.</span><span class="sxs-lookup"><span data-stu-id="ec793-920">**FX_SUCCESS** (0x00) Successful directory next entry find.</span></span>
- <span data-ttu-id="ec793-921">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-921">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="ec793-922">**FX_NO_MORE_ENTRIES** (0x0F) — в этом каталоге больше нет записей.</span><span class="sxs-lookup"><span data-stu-id="ec793-922">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory.</span></span>
- <span data-ttu-id="ec793-923">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-923">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-924">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-924">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="ec793-925">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-925">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="ec793-926">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-926">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="ec793-927">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="ec793-927">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="ec793-928">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="ec793-928">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="ec793-929">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя, или все входные параметры имеют значение NULL.</span><span class="sxs-lookup"><span data-stu-id="ec793-929">**FX_PTR_ERROR** (0x18) Invalid media pointer or all input parameters are NULL.</span></span>
- <span data-ttu-id="ec793-930">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-930">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-931">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-931">Allowed From</span></span>

<span data-ttu-id="ec793-932">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-932">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-933">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-933">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="ec793-934">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-934">See Also</span></span>

- <span data-ttu-id="ec793-935">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-935">fx_directory_attributes_read</span></span>
- <span data-ttu-id="ec793-936">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-936">fx_directory_attributes_set</span></span>
- <span data-ttu-id="ec793-937">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-937">fx_directory_create</span></span>
- <span data-ttu-id="ec793-938">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="ec793-938">fx_directory_default_get</span></span>
- <span data-ttu-id="ec793-939">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="ec793-939">fx_directory_default_set</span></span>
- <span data-ttu-id="ec793-940">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-940">fx_directory_delete</span></span>
- <span data-ttu-id="ec793-941">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-941">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="ec793-942">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-942">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="ec793-943">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="ec793-943">fx_directory_information_get</span></span>
- <span data-ttu-id="ec793-944">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="ec793-944">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="ec793-945">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="ec793-945">fx_directory_local_path_get</span></span>
- <span data-ttu-id="ec793-946">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="ec793-946">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="ec793-947">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="ec793-947">fx_directory_local_path_set</span></span>
- <span data-ttu-id="ec793-948">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-948">fx_directory_long_name_get</span></span>
- <span data-ttu-id="ec793-949">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="ec793-949">fx_directory_name_test</span></span>
- <span data-ttu-id="ec793-950">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-950">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="ec793-951">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-951">fx_directory_rename</span></span>
- <span data-ttu-id="ec793-952">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-952">fx_directory_short_name_get</span></span>
- <span data-ttu-id="ec793-953">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-953">fx_unicode_directory_create</span></span>
- <span data-ttu-id="ec793-954">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-954">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_rename"></a><span data-ttu-id="ec793-955">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-955">fx_directory_rename</span></span>

<span data-ttu-id="ec793-956">Переименовывает каталог</span><span class="sxs-lookup"><span data-stu-id="ec793-956">Renames directory</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-957">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-957">Prototype</span></span>

```c
UINT fx_directory_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_directory_name,
    CHAR *new_directory_name);
```

### <a name="description"></a><span data-ttu-id="ec793-958">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-958">Description</span></span>

<span data-ttu-id="ec793-959">Эта служба изменяет имя каталога на указанное новое имя каталога.</span><span class="sxs-lookup"><span data-stu-id="ec793-959">This service changes the directory name to the specified new directory name.</span></span> <span data-ttu-id="ec793-960">Переименование также выполняется относительно указанного пути или пути по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ec793-960">Renaming is also done relative to the specified path or the default path.</span></span> <span data-ttu-id="ec793-961">Если в новом имени каталога указан путь, переименованный каталог фактически перемещается по указанному пути.</span><span class="sxs-lookup"><span data-stu-id="ec793-961">If a path is specified in the new directory name, the renamed directory is effectively moved to the specified path.</span></span> <span data-ttu-id="ec793-962">Если путь не указан, переименованный каталог помещается в текущий путь по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ec793-962">If no path is specified, the renamed directory is placed in the current default path.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-963">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-963">Input Parameters</span></span>

- <span data-ttu-id="ec793-964">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-964">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="ec793-965">**old_directory_name**: указатель на текущее имя каталога</span><span class="sxs-lookup"><span data-stu-id="ec793-965">**old_directory_name**: Pointer to current directory name.</span></span>
- <span data-ttu-id="ec793-966">**new_directory_name**: указатель на новое имя каталога</span><span class="sxs-lookup"><span data-stu-id="ec793-966">**new_directory_name**: Pointer to new directory name.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-967">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-967">Return Values</span></span>

- <span data-ttu-id="ec793-968">**FX_SUCCESS** (0x00) — каталог успешно переименован.</span><span class="sxs-lookup"><span data-stu-id="ec793-968">**FX_SUCCESS** (0x00) Successful directory rename.</span></span>
- <span data-ttu-id="ec793-969">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-969">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="ec793-970">**FX_NOT_FOUND** (0x04) — не удалось найти запись каталога.</span><span class="sxs-lookup"><span data-stu-id="ec793-970">**FX_NOT_FOUND** (0x04) Directory entry could not be found.</span></span>
- <span data-ttu-id="ec793-971">**FX_NOT_DIRECTORY** (0x0E) — запись не является каталогом.</span><span class="sxs-lookup"><span data-stu-id="ec793-971">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory.</span></span>
- <span data-ttu-id="ec793-972">**FX_INVALID_NAME** (0x0C) — недопустимое имя каталога.</span><span class="sxs-lookup"><span data-stu-id="ec793-972">**FX_INVALID_NAME** (0x0C) New directory name is invalid.</span></span>
- <span data-ttu-id="ec793-973">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-973">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-974">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-974">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="ec793-975">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-975">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="ec793-976">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-976">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="ec793-977">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-977">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="ec793-978">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="ec793-978">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="ec793-979">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="ec793-979">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="ec793-980">**FX_NO_MORE_ENTRIES** (0x0F) — в этом каталоге больше нет записей.</span><span class="sxs-lookup"><span data-stu-id="ec793-980">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory.</span></span>
- <span data-ttu-id="ec793-981">**FX_INVALID_PATH** (0x0D) — указан недопустимый путь с именем каталога.</span><span class="sxs-lookup"><span data-stu-id="ec793-981">**FX_INVALID_PATH** (0x0D) Invalid path supplied with directory name.</span></span>
- <span data-ttu-id="ec793-982">**FX_ALREADY_CREATED** (0x0B) — указанный каталог уже создан.</span><span class="sxs-lookup"><span data-stu-id="ec793-982">**FX_ALREADY_CREATED** (0x0B) Specified directory was already created.</span></span>
- <span data-ttu-id="ec793-983">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-983">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="ec793-984">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-984">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-985">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-985">Allowed From</span></span>

<span data-ttu-id="ec793-986">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-986">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-987">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-987">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;

/* Change the directory "abc" to "def". */
status = fx_directory_rename(&my_media, "abc", "def");

/* If status equals FX_SUCCESS, the directory was changed to "def". */
```

### <a name="see-also"></a><span data-ttu-id="ec793-988">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-988">See Also</span></span>

- <span data-ttu-id="ec793-989">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-989">fx_directory_attributes_read</span></span>
- <span data-ttu-id="ec793-990">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-990">fx_directory_attributes_set</span></span>
- <span data-ttu-id="ec793-991">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-991">fx_directory_create</span></span>
- <span data-ttu-id="ec793-992">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="ec793-992">fx_directory_default_get</span></span>
- <span data-ttu-id="ec793-993">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="ec793-993">fx_directory_default_set</span></span>
- <span data-ttu-id="ec793-994">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-994">fx_directory_delete</span></span>
- <span data-ttu-id="ec793-995">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-995">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="ec793-996">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-996">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="ec793-997">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="ec793-997">fx_directory_information_get</span></span>
- <span data-ttu-id="ec793-998">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="ec793-998">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="ec793-999">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="ec793-999">fx_directory_local_path_get</span></span>
- <span data-ttu-id="ec793-1000">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="ec793-1000">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="ec793-1001">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1001">fx_directory_local_path_set</span></span>
- <span data-ttu-id="ec793-1002">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1002">fx_directory_long_name_get</span></span>
- <span data-ttu-id="ec793-1003">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="ec793-1003">fx_directory_name_test</span></span>
- <span data-ttu-id="ec793-1004">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-1004">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="ec793-1005">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-1005">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="ec793-1006">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1006">fx_directory_short_name_get</span></span>
- <span data-ttu-id="ec793-1007">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1007">fx_unicode_directory_create</span></span>
- <span data-ttu-id="ec793-1008">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1008">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_short_name_get"></a><span data-ttu-id="ec793-1009">fx_directory_short_name_get:</span><span class="sxs-lookup"><span data-stu-id="ec793-1009">fx_directory_short_name_get:</span></span>

<span data-ttu-id="ec793-1010">Получение краткого имени из длинного</span><span class="sxs-lookup"><span data-stu-id="ec793-1010">Gets short name from a long name</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-1011">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-1011">Prototype</span></span>

```c
UINT fx_directory_short_name_get(
    FX_MEDIA *media_ptr,
    CHAR *long_name, 
    CHAR *short_name);
```

### <a name="description"></a><span data-ttu-id="ec793-1012">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-1012">Description</span></span>

<span data-ttu-id="ec793-1013">Эта служба получает краткое имя (формат 8.3), связанное с переданным длинным именем.</span><span class="sxs-lookup"><span data-stu-id="ec793-1013">This service retrieves the short (8.3 format) name associated with the supplied long name.</span></span> <span data-ttu-id="ec793-1014">Длинное имя может быть либо именем файла, либо именем каталога.</span><span class="sxs-lookup"><span data-stu-id="ec793-1014">The long name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-1015">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-1015">Input Parameters</span></span>

- <span data-ttu-id="ec793-1016">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-1016">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="ec793-1017">**long_name**: указатель на исходное длинное имя</span><span class="sxs-lookup"><span data-stu-id="ec793-1017">**long_name**: Pointer to source long name.</span></span>
- <span data-ttu-id="ec793-1018">**short_name**: указатель на назначение краткого имени (формат 8.3)</span><span class="sxs-lookup"><span data-stu-id="ec793-1018">**short_name**: Pointer to destination short name (8.3 format).</span></span> <span data-ttu-id="ec793-1019">Обратите внимание, что назначение для краткого имени должно быть достаточно большим, чтобы вместить 14 символов.</span><span class="sxs-lookup"><span data-stu-id="ec793-1019">Note that the destination for the short name must be large enough to hold 14 characters.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-1020">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-1020">Return Values</span></span>

- <span data-ttu-id="ec793-1021">**FX_SUCCESS** (0x00) — краткое имя успешно получено.</span><span class="sxs-lookup"><span data-stu-id="ec793-1021">**FX_SUCCESS** (0x00) Successful short name get.</span></span>
- <span data-ttu-id="ec793-1022">**FX_NOT_FOUND** (0x04) — длинное имя не найдено.</span><span class="sxs-lookup"><span data-stu-id="ec793-1022">**FX_NOT_FOUND** (0x04) Long name was not found.</span></span>
- <span data-ttu-id="ec793-1023">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-1023">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-1024">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-1024">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="ec793-1025">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-1025">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="ec793-1026">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-1026">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="ec793-1027">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-1027">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="ec793-1028">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="ec793-1028">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="ec793-1029">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="ec793-1029">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="ec793-1030">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.</span><span class="sxs-lookup"><span data-stu-id="ec793-1030">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="ec793-1031">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-1031">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-1032">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-1032">Allowed From</span></span>

<span data-ttu-id="ec793-1033">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-1033">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-1034">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-1034">Example</span></span>

```c
FX_MEDIA         my_media;
UCHAR             my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get(&my_media,
    "my_really_long_name", my_short_name);

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ec793-1035">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-1035">See Also</span></span>

- <span data-ttu-id="ec793-1036">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1036">fx_directory_attributes_read</span></span>
- <span data-ttu-id="ec793-1037">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1037">fx_directory_attributes_set</span></span>
- <span data-ttu-id="ec793-1038">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1038">fx_directory_create</span></span>
- <span data-ttu-id="ec793-1039">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1039">fx_directory_default_get</span></span>
- <span data-ttu-id="ec793-1040">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1040">fx_directory_default_set</span></span>
- <span data-ttu-id="ec793-1041">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-1041">fx_directory_delete</span></span>
- <span data-ttu-id="ec793-1042">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-1042">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="ec793-1043">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-1043">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="ec793-1044">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1044">fx_directory_information_get</span></span>
- <span data-ttu-id="ec793-1045">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="ec793-1045">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="ec793-1046">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1046">fx_directory_local_path_get</span></span>
- <span data-ttu-id="ec793-1047">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="ec793-1047">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="ec793-1048">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1048">fx_directory_local_path_set</span></span>
- <span data-ttu-id="ec793-1049">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1049">fx_directory_long_name_get</span></span>
- <span data-ttu-id="ec793-1050">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="ec793-1050">fx_directory_name_test</span></span>
- <span data-ttu-id="ec793-1051">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-1051">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="ec793-1052">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-1052">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="ec793-1053">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1053">fx_directory_rename</span></span>
- <span data-ttu-id="ec793-1054">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1054">fx_unicode_directory_create</span></span>
- <span data-ttu-id="ec793-1055">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1055">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_short_name_get_extended"></a><span data-ttu-id="ec793-1056">fx_directory_short_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="ec793-1056">fx_directory_short_name_get_extended</span></span>

<span data-ttu-id="ec793-1057">Получение краткого имени из длинного</span><span class="sxs-lookup"><span data-stu-id="ec793-1057">Gets short name from a long name</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-1058">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-1058">Prototype</span></span>

```csharp
UINT fx_directory_short_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *long_name,
    CHAR *short_name,
    UINT short_file_name_length);
```

### <a name="description"></a><span data-ttu-id="ec793-1059">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-1059">Description</span></span>

<span data-ttu-id="ec793-1060">Эта служба получает краткое имя (формат 8.3), связанное с переданным длинным именем.</span><span class="sxs-lookup"><span data-stu-id="ec793-1060">This service retrieves the short (8.3 format) name associated with the supplied long name.</span></span> <span data-ttu-id="ec793-1061">Длинное имя может быть либо именем файла, либо именем каталога.</span><span class="sxs-lookup"><span data-stu-id="ec793-1061">The long name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-1062">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-1062">Input Parameters</span></span>

- <span data-ttu-id="ec793-1063">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-1063">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="ec793-1064">**long_name**: указатель на исходное длинное имя</span><span class="sxs-lookup"><span data-stu-id="ec793-1064">**long_name**: Pointer to source long name.</span></span>
- <span data-ttu-id="ec793-1065">**short_name**: указатель на назначение краткого имени (формат 8.3)</span><span class="sxs-lookup"><span data-stu-id="ec793-1065">**short_name**: Pointer to destination short name (8.3 format).</span></span> <span data-ttu-id="ec793-1066">Обратите внимание, что назначение для краткого имени должно быть достаточно большим, чтобы вместить 14 символов.</span><span class="sxs-lookup"><span data-stu-id="ec793-1066">Note: Destination for the short name must be large enough to hold 14 characters.</span></span>
- <span data-ttu-id="ec793-1067">**short_file_name_length**: длина буфера коротких имен</span><span class="sxs-lookup"><span data-stu-id="ec793-1067">**short_file_name_length**: Length of short name buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-1068">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-1068">Return Values</span></span>

- <span data-ttu-id="ec793-1069">**FX_SUCCESS** (0x00) — краткое имя успешно получено.</span><span class="sxs-lookup"><span data-stu-id="ec793-1069">**FX_SUCCESS** (0x00) Successful short name get.</span></span>
- <span data-ttu-id="ec793-1070">**FX_NOT_FOUND** (0x04) — длинное имя не найдено.</span><span class="sxs-lookup"><span data-stu-id="ec793-1070">**FX_NOT_FOUND** (0x04) Long name was not found.</span></span>
- <span data-ttu-id="ec793-1071">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-1071">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-1072">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-1072">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="ec793-1073">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-1073">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="ec793-1074">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-1074">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="ec793-1075">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-1075">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="ec793-1076">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="ec793-1076">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="ec793-1077">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="ec793-1077">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="ec793-1078">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.</span><span class="sxs-lookup"><span data-stu-id="ec793-1078">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="ec793-1079">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-1079">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-1080">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-1080">Allowed From</span></span>

<span data-ttu-id="ec793-1081">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-1081">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-1082">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-1082">Example</span></span>

```c
FX_MEDIA        my_media;
UCHAR            my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get_extended(&my_media,
    "my_really_long_name", my_short_name, sizeof(my_short_name));

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ec793-1083">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-1083">See Also</span></span>

- <span data-ttu-id="ec793-1084">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1084">fx_directory_attributes_read</span></span>
- <span data-ttu-id="ec793-1085">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1085">fx_directory_attributes_set</span></span>
- <span data-ttu-id="ec793-1086">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1086">fx_directory_create</span></span>
- <span data-ttu-id="ec793-1087">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1087">fx_directory_default_get</span></span>
- <span data-ttu-id="ec793-1088">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1088">fx_directory_default_set</span></span>
- <span data-ttu-id="ec793-1089">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-1089">fx_directory_delete</span></span>
- <span data-ttu-id="ec793-1090">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-1090">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="ec793-1091">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-1091">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="ec793-1092">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1092">fx_directory_information_get</span></span>
- <span data-ttu-id="ec793-1093">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="ec793-1093">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="ec793-1094">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1094">fx_directory_local_path_get</span></span>
- <span data-ttu-id="ec793-1095">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="ec793-1095">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="ec793-1096">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1096">fx_directory_local_path_set</span></span>
- <span data-ttu-id="ec793-1097">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1097">fx_directory_long_name_get</span></span>
- <span data-ttu-id="ec793-1098">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="ec793-1098">fx_directory_name_test</span></span>
- <span data-ttu-id="ec793-1099">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-1099">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="ec793-1100">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-1100">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="ec793-1101">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1101">fx_directory_rename</span></span>
- <span data-ttu-id="ec793-1102">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1102">fx_unicode_directory_create</span></span>
- <span data-ttu-id="ec793-1103">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1103">fx_unicode_directory_rename</span></span>

## <a name="fx_fault_tolerant_enable"></a><span data-ttu-id="ec793-1104">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="ec793-1104">fx_fault_tolerant_enable</span></span>

<span data-ttu-id="ec793-1105">Включает отказоустойчивую службу</span><span class="sxs-lookup"><span data-stu-id="ec793-1105">Enables the fault tolerant service</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-1106">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-1106">Prototype</span></span>

```csharp
UINT fx_fault_tolerant_enable(
    FX_MEDIA *media_ptr,
    VOID *memory_buffer,
    UINT memory_size);
```

### <a name="description"></a><span data-ttu-id="ec793-1107">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-1107">Description</span></span>

<span data-ttu-id="ec793-1108">Эта служба включает отказоустойчивый модуль.</span><span class="sxs-lookup"><span data-stu-id="ec793-1108">This service enables the fault tolerant module.</span></span> <span data-ttu-id="ec793-1109">После запуска отказоустойчивый модуль определяет, находится ли файловая система в режиме отказоустойчивой защиты FileX.</span><span class="sxs-lookup"><span data-stu-id="ec793-1109">Upon starting, the fault tolerant module detects whether or not the file system is under FileX fault tolerant protection.</span></span> <span data-ttu-id="ec793-1110">Если это не так, служба находит в файловой системе доступные секторы для хранения журналов транзакций файловой системы.</span><span class="sxs-lookup"><span data-stu-id="ec793-1110">If it is not, the service finds available sectors on the file system to store logs on file system transactions.</span></span> <span data-ttu-id="ec793-1111">Если файловая система находится в режиме отказоустойчивой защиты FileX, она применяет журналы к файловой системе для обеспечения целостности.</span><span class="sxs-lookup"><span data-stu-id="ec793-1111">If the file system is under FileX fault tolerant protection, it applies the logs to the file system to maintain its integrity.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-1112">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-1112">Input Parameters</span></span>

- <span data-ttu-id="ec793-1113">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-1113">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="ec793-1114">**memory_ptr**: указатель на блок памяти, используемый отказоустойчивым модулем в качестве вспомогательной памяти</span><span class="sxs-lookup"><span data-stu-id="ec793-1114">**memory_ptr**: Pointer to a block of memory used by the fault tolerant module as scratch memory.</span></span>
- <span data-ttu-id="ec793-1115">**memory_size**: размер вспомогательной памяти</span><span class="sxs-lookup"><span data-stu-id="ec793-1115">**memory_size**: The size of the scratch memory.</span></span> <span data-ttu-id="ec793-1116">Чтобы отказоустойчивость работала правильно, размер вспомогательной памяти должен составлять не менее 3072 байт и должен быть кратен размеру сектора.</span><span class="sxs-lookup"><span data-stu-id="ec793-1116">In order for fault tolerant to work properly, the scratch memory size shall be at least 3072 bytes,- and must be multiple of sector size.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-1117">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-1117">Return Values</span></span>

- <span data-ttu-id="ec793-1118">**FX_SUCCESS** (0x00) — отказоустойчивость успешно включена.</span><span class="sxs-lookup"><span data-stu-id="ec793-1118">**FX_SUCCESS** (0x00) Successfully enabled fault tolerant.</span></span>
- <span data-ttu-id="ec793-1119">**FX_NOT_ENOUGH_MEMORY** (0x91) — слишком маленький размер памяти.</span><span class="sxs-lookup"><span data-stu-id="ec793-1119">**FX_NOT_ENOUGH_MEMORY** (0x91)    memory size too small.</span></span>
- <span data-ttu-id="ec793-1120">**FX_BOOT_ERROR** (0x01) — ошибка загрузочного сектора.</span><span class="sxs-lookup"><span data-stu-id="ec793-1120">**FX_BOOT_ERROR** (0x01) Boot sector error.</span></span>
- <span data-ttu-id="ec793-1121">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-1121">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="ec793-1122">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет свободных кластеров.</span><span class="sxs-lookup"><span data-stu-id="ec793-1122">**FX_NO_MORE_ENTRIES** (0x0F) No more free cluster available.</span></span>
- <span data-ttu-id="ec793-1123">**FX_NO_MORE_SPACE** (0x0A) — на носителе, связанном с этим файлом, недостаточно доступных кластеров.</span><span class="sxs-lookup"><span data-stu-id="ec793-1123">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="ec793-1124">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-1124">**FX_SECTOR_INVALID** (0x89) Sector is invalid</span></span>
- <span data-ttu-id="ec793-1125">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-1125">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-1126">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-1126">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="ec793-1127">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-1127">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-1128">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-1128">Allowed From</span></span>

<span data-ttu-id="ec793-1129">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-1129">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-1130">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-1130">Example</span></span>

```c

/* Declare memory space used for fault tolerant. */

ULONG fault tolerant_memory[3072 / sizeof(ULONG)];

/* Enable fault tolerant. */

fx_fault_tolerant_enable(media_ptr, fault_tolerant_memory, sizeof(fault_tolerant_memory));

```

### <a name="see-also"></a><span data-ttu-id="ec793-1131">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-1131">See Also</span></span>

- <span data-ttu-id="ec793-1132">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ec793-1132">fx_system_initialize</span></span>
- <span data-ttu-id="ec793-1133">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="ec793-1133">fx_media_abort</span></span>
- <span data-ttu-id="ec793-1134">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="ec793-1134">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="ec793-1135">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="ec793-1135">fx_media_check</span></span>
- <span data-ttu-id="ec793-1136">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="ec793-1136">fx_media_close</span></span>
- <span data-ttu-id="ec793-1137">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1137">fx_media_close_notify_set</span></span>
- <span data-ttu-id="ec793-1138">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="ec793-1138">fx_media_exFAT_format</span></span>
- <span data-ttu-id="ec793-1139">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-1139">fx_media_extended_space_available</span></span>
- <span data-ttu-id="ec793-1140">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="ec793-1140">fx_media_flush</span></span>
- <span data-ttu-id="ec793-1141">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="ec793-1141">fx_media_format</span></span>
- <span data-ttu-id="ec793-1142">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="ec793-1142">fx_media_open</span></span>
- <span data-ttu-id="ec793-1143">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1143">fx_media_open_notify_set</span></span>
- <span data-ttu-id="ec793-1144">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1144">fx_media_read</span></span>
- <span data-ttu-id="ec793-1145">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-1145">fx_media_space_available</span></span>
- <span data-ttu-id="ec793-1146">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1146">fx_media_volume_get</span></span>
- <span data-ttu-id="ec793-1147">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1147">fx_media_volume_set</span></span>
- <span data-ttu-id="ec793-1148">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="ec793-1148">fx_media_write</span></span>

## <a name="fx_file_allocate"></a><span data-ttu-id="ec793-1149">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1149">fx_file_allocate</span></span>

<span data-ttu-id="ec793-1150">Выделяет место для файла</span><span class="sxs-lookup"><span data-stu-id="ec793-1150">Allocates space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-1151">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-1151">Prototype</span></span>

```csharp
UINT fx_file_allocate(
    FX_FILE *file_ptr, 
    ULONG size);
```
### <a name="description"></a><span data-ttu-id="ec793-1152">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-1152">Description</span></span>

<span data-ttu-id="ec793-1153">Эта служба выделяет один кластер или несколько последовательных и связывает их с концом указанного файла.</span><span class="sxs-lookup"><span data-stu-id="ec793-1153">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="ec793-1154">FileX определяет количество кластеров, необходимое для деления запрошенного размера на число байтов на кластер.</span><span class="sxs-lookup"><span data-stu-id="ec793-1154">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="ec793-1155">Затем результат округляется до следующего целого кластера.</span><span class="sxs-lookup"><span data-stu-id="ec793-1155">The result is then rounded up to the next whole cluster.</span></span>

<span data-ttu-id="ec793-1156">Чтобы выделить место свыше 4 ГБ, приложение должно использовать службу *fx_file_extended_allocate*.</span><span class="sxs-lookup"><span data-stu-id="ec793-1156">To allocate space beyond 4GB, application shall use the service *fx_file_extended_allocate*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-1157">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-1157">Input Parameters</span></span>

- <span data-ttu-id="ec793-1158">**file_ptr**: указатель на открытый ранее файл</span><span class="sxs-lookup"><span data-stu-id="ec793-1158">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="ec793-1159">**size**: число байтов, выделяемых для файла</span><span class="sxs-lookup"><span data-stu-id="ec793-1159">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-1160">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-1160">Return Values</span></span>

- <span data-ttu-id="ec793-1161">**FX_SUCCESS** (0x00) — файл успешно выделен.</span><span class="sxs-lookup"><span data-stu-id="ec793-1161">**FX_SUCCESS** (0x00) Successful file allocation.</span></span>
- <span data-ttu-id="ec793-1162">**FX_ACCESS_ERROR** (0x06) — указанный файл не открыт для записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-1162">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="ec793-1163">**FX_FAT_READ_ERROR** (0x03) — не удалось прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-1163">**FX_FAT_READ_ERROR** (0x03) Failed to read FAT entry.</span></span>
- <span data-ttu-id="ec793-1164">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-1164">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="ec793-1165">**FX_NOT_OPEN** (0x07) — указанный файл в настоящее время не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-1165">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="ec793-1166">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет свободных кластеров.</span><span class="sxs-lookup"><span data-stu-id="ec793-1166">**FX_NO_MORE_ENTRIES** (0x0F) No more free cluster available.</span></span>
- <span data-ttu-id="ec793-1167">**FX_NO_MORE_SPACE** (0x0A) — на носителе, связанном с этим файлом, недостаточно доступных кластеров.</span><span class="sxs-lookup"><span data-stu-id="ec793-1167">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="ec793-1168">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-1168">**FX_SECTOR_INVALID** (0x89) Sector is invalid</span></span>
- <span data-ttu-id="ec793-1169">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-1169">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-1170">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-1170">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="ec793-1171">**FX_PTR_ERROR** (0x18) — недопустимый указатель на файл.</span><span class="sxs-lookup"><span data-stu-id="ec793-1171">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="ec793-1172">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-1172">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-1173">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-1173">Allowed From</span></span>

<span data-ttu-id="ec793-1174">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-1174">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-1175">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-1175">Example</span></span>

```c

FX_FILE            my_file;
UINT            status;

/* Allocate 1024 bytes to the end of my_file. */

status = fx_file_allocate(&my_file, 1024);

/* If status equals FX_SUCCESS the file now has one or more
    contiguous cluster(s) that can accommodate at least 1024 bytes of user data. */
```

### <a name="see-also"></a><span data-ttu-id="ec793-1176">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-1176">See Also</span></span>

- <span data-ttu-id="ec793-1177">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1177">fx_file_attributes_read</span></span>
- <span data-ttu-id="ec793-1178">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1178">fx_file_attributes_set</span></span>
- <span data-ttu-id="ec793-1179">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1179">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-1180">fx_file_close- fx_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1180">fx_file_close- fx_file_create</span></span>
- <span data-ttu-id="ec793-1181">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1181">fx_file_date_time_set</span></span>
- <span data-ttu-id="ec793-1182">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-1182">fx_file_delete</span></span>
- <span data-ttu-id="ec793-1183">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1183">fx_file_extended_allocate</span></span>
- <span data-ttu-id="ec793-1184">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1184">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-1185">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1185">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="ec793-1186">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1186">fx_file_extended_seek</span></span>
- <span data-ttu-id="ec793-1187">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-1187">fx_file_extended_truncate</span></span>
- <span data-ttu-id="ec793-1188">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-1188">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="ec793-1189">fx_file_open- fx_file_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1189">fx_file_open- fx_file_read</span></span>
- <span data-ttu-id="ec793-1190">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1190">fx_file_relative_seek</span></span>
- <span data-ttu-id="ec793-1191">fx_file_rename- fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1191">fx_file_rename- fx_file_seek</span></span>
- <span data-ttu-id="ec793-1192">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-1192">fx_file_truncate</span></span>
- <span data-ttu-id="ec793-1193">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-1193">fx_file_truncate_release</span></span>
- <span data-ttu-id="ec793-1194">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="ec793-1194">fx_file_write</span></span>
- <span data-ttu-id="ec793-1195">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1195">fx_file_write_notify_set</span></span>
- <span data-ttu-id="ec793-1196">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1196">fx_unicode_file_create</span></span>
- <span data-ttu-id="ec793-1197">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1197">fx_unicode_file_rename</span></span>
- <span data-ttu-id="ec793-1198">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1198">fx_unicode_name_get</span></span>
- <span data-ttu-id="ec793-1199">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1199">fx_unicode_short_name_get</span></span>

## <a name="fx_file_attributes_read"></a><span data-ttu-id="ec793-1200">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1200">fx_file_attributes_read</span></span>

<span data-ttu-id="ec793-1201">Считывает атрибуты файла</span><span class="sxs-lookup"><span data-stu-id="ec793-1201">Reads file attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-1202">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-1202">Prototype</span></span>

```c
    UINT fx_file_attributes_read(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT *attributes_ptr);
```
### <a name="description"></a><span data-ttu-id="ec793-1203">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-1203">Description</span></span>

<span data-ttu-id="ec793-1204">Эта служба считывает атрибуты файла с указанного носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-1204">This service reads the file's attributes from the specified media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-1205">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-1205">Input Parameters</span></span>

- <span data-ttu-id="ec793-1206">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-1206">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="ec793-1207">**file_name**: указатель на имя запрошенного файла (путь к каталогу является необязательным)</span><span class="sxs-lookup"><span data-stu-id="ec793-1207">**file_name**: Pointer to the name of the requested file (directory path is optional).</span></span>
- <span data-ttu-id="ec793-1208">**attributes_ptr**: указатель на назначение для размещения атрибутов файла</span><span class="sxs-lookup"><span data-stu-id="ec793-1208">**attributes_ptr**: Pointer to the destination for the file's attributes to be placed.</span></span> <span data-ttu-id="ec793-1209">Атрибуты файла возвращаются в формате битовой карты со следующими возможными параметрами.</span><span class="sxs-lookup"><span data-stu-id="ec793-1209">The file attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="ec793-1210">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="ec793-1210">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="ec793-1211">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="ec793-1211">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="ec793-1212">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="ec793-1212">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="ec793-1213">FX_VOLUME (0x08)</span><span class="sxs-lookup"><span data-stu-id="ec793-1213">FX_VOLUME (0x08)</span></span>
  - <span data-ttu-id="ec793-1214">FX_DIRECTORY (0x10)</span><span class="sxs-lookup"><span data-stu-id="ec793-1214">FX_DIRECTORY (0x10)</span></span>
  - <span data-ttu-id="ec793-1215">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="ec793-1215">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-1216">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-1216">Return Values</span></span>

- <span data-ttu-id="ec793-1217">**FX_SUCCESS** (0x00) — атрибут успешно считан.</span><span class="sxs-lookup"><span data-stu-id="ec793-1217">**FX_SUCCESS** (0x00) Successful attribute read.</span></span>
- <span data-ttu-id="ec793-1218">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-1218">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="ec793-1219">**FX_NOT_FOUND** (0x04) — указанный файл не найден на носителе.</span><span class="sxs-lookup"><span data-stu-id="ec793-1219">**FX_NOT_FOUND** (0x04) Specified file was not found in the media.</span></span>
- <span data-ttu-id="ec793-1220">**FX_NOT_A_FILE** (0x05) — указанный файл является каталогом.</span><span class="sxs-lookup"><span data-stu-id="ec793-1220">**FX_NOT_A_FILE** (0x05) Specified file is a directory.</span></span>
- <span data-ttu-id="ec793-1221">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-1221">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="ec793-1222">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-1222">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="ec793-1223">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-1223">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="ec793-1224">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="ec793-1224">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="ec793-1225">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-1225">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-1226">**FX_PTR_ERROR** (0x18) — недопустимый носитель или указатель на атрибуты.</span><span class="sxs-lookup"><span data-stu-id="ec793-1226">**FX_PTR_ERROR** (0x18) Invalid media or attributes pointer.</span></span>
- <span data-ttu-id="ec793-1227">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-1227">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-1228">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-1228">Allowed From</span></span>

<span data-ttu-id="ec793-1229">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-1229">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-1230">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-1230">Example</span></span>

```c

FX_MEDIA         my_media;
UINT             status;
UINT             attributes;

/* Retrieve the attributes of "myfile.txt" from the specified media. */

status = fx_file_attributes_read(&my_media, "myfile.txt", &attributes);

/* If status equals FX_SUCCESS, "attributes"
    contains the file attributes for "myfile.txt". */

```

### <a name="see-also"></a><span data-ttu-id="ec793-1231">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-1231">See Also</span></span>

- <span data-ttu-id="ec793-1232">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1232">fx_file_allocate</span></span>
- <span data-ttu-id="ec793-1233">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1233">fx_file_attributes_set</span></span>
- <span data-ttu-id="ec793-1234">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1234">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-1235">fx_file_close- fx_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1235">fx_file_close- fx_file_create</span></span>
- <span data-ttu-id="ec793-1236">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1236">fx_file_date_time_set</span></span>
- <span data-ttu-id="ec793-1237">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-1237">fx_file_delete</span></span>
- <span data-ttu-id="ec793-1238">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1238">fx_file_extended_allocate</span></span>
- <span data-ttu-id="ec793-1239">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1239">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-1240">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1240">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="ec793-1241">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1241">fx_file_extended_seek</span></span>
- <span data-ttu-id="ec793-1242">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-1242">fx_file_extended_truncate</span></span>
- <span data-ttu-id="ec793-1243">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-1243">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="ec793-1244">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="ec793-1244">fx_file_open</span></span>
- <span data-ttu-id="ec793-1245">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1245">fx_file_read</span></span>
- <span data-ttu-id="ec793-1246">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1246">fx_file_relative_seek</span></span>
- <span data-ttu-id="ec793-1247">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1247">fx_file_rename</span></span>
- <span data-ttu-id="ec793-1248">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1248">fx_file_seek</span></span>
- <span data-ttu-id="ec793-1249">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-1249">fx_file_truncate</span></span>
- <span data-ttu-id="ec793-1250">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-1250">fx_file_truncate_release</span></span>
- <span data-ttu-id="ec793-1251">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="ec793-1251">fx_file_write</span></span>
- <span data-ttu-id="ec793-1252">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1252">fx_file_write_notify_set</span></span>
- <span data-ttu-id="ec793-1253">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1253">fx_unicode_file_create</span></span>
- <span data-ttu-id="ec793-1254">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1254">fx_unicode_file_rename</span></span>
- <span data-ttu-id="ec793-1255">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1255">fx_unicode_name_get</span></span>
- <span data-ttu-id="ec793-1256">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1256">fx_unicode_short_name_get</span></span>

## <a name="fx_file_attributes_set"></a><span data-ttu-id="ec793-1257">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1257">fx_file_attributes_set</span></span>

<span data-ttu-id="ec793-1258">Задает атрибуты файла</span><span class="sxs-lookup"><span data-stu-id="ec793-1258">Sets file attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-1259">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-1259">Prototype</span></span>

```c
UINT fx_file_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT attributes);
```
### <a name="description"></a><span data-ttu-id="ec793-1260">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-1260">Description</span></span>

<span data-ttu-id="ec793-1261">Эта служба задает атрибуты файла, указанные вызывающим объектом.</span><span class="sxs-lookup"><span data-stu-id="ec793-1261">This service sets the file's attributes to those specified by the caller.</span></span>

> [!WARNING]
> <span data-ttu-id="ec793-1262">*Этому приложению разрешено изменять только подмножество атрибутов файла, используя эту службу. Любая попытка задать дополнительные атрибуты приведет к ошибке.*</span><span class="sxs-lookup"><span data-stu-id="ec793-1262">*The application is only allowed to modify a subset of the file's attributes with this service. Any attempt to set additional attributes will result in an error.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-1263">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-1263">Input Parameters</span></span>

- <span data-ttu-id="ec793-1264">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-1264">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="ec793-1265">**file_name**: указатель на имя запрошенного файла\*\* (путь к каталогу является необязательным)</span><span class="sxs-lookup"><span data-stu-id="ec793-1265">**file_name**: Pointer to the name of the requested file\*\* (directory path is optional).</span></span>
- <span data-ttu-id="ec793-1266">**attributes**: новые атрибуты для файла</span><span class="sxs-lookup"><span data-stu-id="ec793-1266">**attributes**: The new attributes for the file.</span></span> <span data-ttu-id="ec793-1267">Допустимые атрибуты файла определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ec793-1267">The valid file attributes are defined as follows:</span></span>
  - <span data-ttu-id="ec793-1268">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="ec793-1268">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="ec793-1269">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="ec793-1269">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="ec793-1270">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="ec793-1270">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="ec793-1271">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="ec793-1271">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-1272">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-1272">Return Values</span></span>

- <span data-ttu-id="ec793-1273">**FX_SUCCESS** (0x00) — атрибут успешно задан.</span><span class="sxs-lookup"><span data-stu-id="ec793-1273">**FX_SUCCESS** (0x00) Successful attribute set.</span></span>
- <span data-ttu-id="ec793-1274">**FX_ACCESS_ERROR** (0x06) — файл открыт, невозможно задать его атрибуты.</span><span class="sxs-lookup"><span data-stu-id="ec793-1274">**FX_ACCESS_ERROR** (0x06) File is open and cannot have its attributes set.</span></span>
- <span data-ttu-id="ec793-1275">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-1275">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="ec793-1276">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-1276">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="ec793-1277">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-1277">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="ec793-1278">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей в таблице FAT или карте кластера exFAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-1278">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in the FAT table or exFAT cluster map.</span></span>
- <span data-ttu-id="ec793-1279">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="ec793-1279">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="ec793-1280">**FX_NOT_FOUND** (0x04) — указанный файл не найден на носителе.</span><span class="sxs-lookup"><span data-stu-id="ec793-1280">**FX_NOT_FOUND** (0x04) Specified file was not found in the media.</span></span>
- <span data-ttu-id="ec793-1281">**FX_NOT_A_FILE** (0x05) — указанный файл является каталогом.</span><span class="sxs-lookup"><span data-stu-id="ec793-1281">**FX_NOT_A_FILE** (0x05) Specified file is a directory.</span></span>
- <span data-ttu-id="ec793-1282">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-1282">**FX_SECTOR_INVALID** (0x89) Sector is invalid</span></span>
- <span data-ttu-id="ec793-1283">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-1283">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-1284">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-1284">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="ec793-1285">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="ec793-1285">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="ec793-1286">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-1286">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="ec793-1287">**FX_INVALID_ATTR** (0x19) — выбраны недопустимые атрибуты.</span><span class="sxs-lookup"><span data-stu-id="ec793-1287">**FX_INVALID_ATTR** (0x19) Invalid attributes selected.</span></span>
- <span data-ttu-id="ec793-1288">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-1288">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-1289">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-1289">Allowed From</span></span>

<span data-ttu-id="ec793-1290">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-1290">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-1291">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-1291">Example</span></span>

```c

FX_MEDIA         my_media;
UINT             status;

/* Set the attributes of "myfile.txt" to read-only. */

status = fx_file_attributes_set(&my_media, "myfile.txt", FX_READ_ONLY);

/* If status equals FX_SUCCESS, the file is now read-only. */

```

### <a name="see-also"></a><span data-ttu-id="ec793-1292">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-1292">See Also</span></span>

- <span data-ttu-id="ec793-1293">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1293">fx_file_allocate</span></span>
- <span data-ttu-id="ec793-1294">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1294">fx_file_attributes_read</span></span>
- <span data-ttu-id="ec793-1295">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1295">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-1296">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="ec793-1296">fx_file_close</span></span>
- <span data-ttu-id="ec793-1297">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1297">fx_file_create</span></span>
- <span data-ttu-id="ec793-1298">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1298">fx_file_date_time_set</span></span>
- <span data-ttu-id="ec793-1299">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-1299">fx_file_delete</span></span>
- <span data-ttu-id="ec793-1300">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1300">fx_file_extended_allocate</span></span>
- <span data-ttu-id="ec793-1301">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1301">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-1302">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1302">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="ec793-1303">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1303">fx_file_extended_seek</span></span>
- <span data-ttu-id="ec793-1304">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-1304">fx_file_extended_truncate</span></span>
- <span data-ttu-id="ec793-1305">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-1305">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="ec793-1306">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="ec793-1306">fx_file_open</span></span>
- <span data-ttu-id="ec793-1307">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1307">fx_file_read</span></span>
- <span data-ttu-id="ec793-1308">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1308">fx_file_relative_seek</span></span>
- <span data-ttu-id="ec793-1309">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1309">fx_file_rename</span></span>
- <span data-ttu-id="ec793-1310">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1310">fx_file_seek</span></span>
- <span data-ttu-id="ec793-1311">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-1311">fx_file_truncate</span></span>
- <span data-ttu-id="ec793-1312">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-1312">fx_file_truncate_release</span></span>
- <span data-ttu-id="ec793-1313">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="ec793-1313">fx_file_write</span></span>
- <span data-ttu-id="ec793-1314">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1314">fx_file_write_notify_set</span></span>
- <span data-ttu-id="ec793-1315">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1315">fx_unicode_file_create</span></span>
- <span data-ttu-id="ec793-1316">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1316">fx_unicode_file_rename</span></span>
- <span data-ttu-id="ec793-1317">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1317">fx_unicode_name_get</span></span>
- <span data-ttu-id="ec793-1318">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1318">fx_unicode_short_name_get</span></span>

## <a name="fx_file_best_effort_allocate"></a><span data-ttu-id="ec793-1319">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1319">fx_file_best_effort_allocate</span></span>

<span data-ttu-id="ec793-1320">Наиболее оптимальное выделение пространства для файла</span><span class="sxs-lookup"><span data-stu-id="ec793-1320">Best effort to allocate space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-1321">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-1321">Prototype</span></span>

```c
UINT fx_file_best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG size,
    ULONG *actual_size_allocated);
```
### <a name="description"></a><span data-ttu-id="ec793-1322">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-1322">Description</span></span>

<span data-ttu-id="ec793-1323">Эта служба выделяет один кластер или несколько последовательных и связывает их с концом указанного файла.</span><span class="sxs-lookup"><span data-stu-id="ec793-1323">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="ec793-1324">FileX определяет количество кластеров, необходимое для деления запрошенного размера на число байтов на кластер.</span><span class="sxs-lookup"><span data-stu-id="ec793-1324">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="ec793-1325">Затем результат округляется до следующего целого кластера.</span><span class="sxs-lookup"><span data-stu-id="ec793-1325">The result is then rounded up to the next whole cluster.</span></span> <span data-ttu-id="ec793-1326">Если на носителе нет достаточного количества последовательных кластеров, эта служба связывает с файлом самый большой доступный блок последовательных кластеров.</span><span class="sxs-lookup"><span data-stu-id="ec793-1326">If there are not enough consecutive clusters available in the media, this service links the largest available block of consecutive clusters to the file.</span></span> <span data-ttu-id="ec793-1327">Объем пространства, фактически выделяемый файлу, возвращается вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="ec793-1327">The amount of space actually allocated to the file is returned to the caller.</span></span>

<span data-ttu-id="ec793-1328">Чтобы выделить место свыше 4 ГБ, приложение должно использовать службу *fx_file_extended_best_effort_allocate*.</span><span class="sxs-lookup"><span data-stu-id="ec793-1328">To allocate space beyond 4GB, application shall use the service *fx_file_extended_best_effort_allocate*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-1329">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-1329">Input Parameters</span></span>

- <span data-ttu-id="ec793-1330">**file_ptr**: указатель на открытый ранее файл</span><span class="sxs-lookup"><span data-stu-id="ec793-1330">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="ec793-1331">**size**: число байтов, выделяемых для файла</span><span class="sxs-lookup"><span data-stu-id="ec793-1331">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-1332">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-1332">Return Values</span></span>

- <span data-ttu-id="ec793-1333">**FX_SUCCESS** (0x00) — наиболее оптимальное выделение пространства для файла успешно выполнено.</span><span class="sxs-lookup"><span data-stu-id="ec793-1333">**FX_SUCCESS** (0x00) Successful best-effort file allocation.</span></span>
- <span data-ttu-id="ec793-1334">**FX_ACCESS_ERROR** (0x06) — указанный файл не открыт для записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-1334">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="ec793-1335">**FX_NOT_OPEN** (0x07) — указанный файл в настоящее время не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-1335">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="ec793-1336">**FX_NO_MORE_SPACE** (0x0A) — на носителе, связанном с этим файлом, недостаточно доступных кластеров.</span><span class="sxs-lookup"><span data-stu-id="ec793-1336">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="ec793-1337">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-1337">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="ec793-1338">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-1338">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="ec793-1339">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-1339">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="ec793-1340">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-1340">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="ec793-1341">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-1341">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-1342">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-1342">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="ec793-1343">**FX_PTR_ERROR** (0x18) — недопустимый указатель или назначение файла.</span><span class="sxs-lookup"><span data-stu-id="ec793-1343">**FX_PTR_ERROR** (0x18) Invalid file pointer or destination.</span></span>
- <span data-ttu-id="ec793-1344">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-1344">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-1345">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-1345">Allowed From</span></span>

<span data-ttu-id="ec793-1346">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-1346">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-1347">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-1347">Example</span></span>

```c

FX_FILE         my_file;
UINT             status;
ULONG             actual_allocation;

/* Attempt to allocate 1024 bytes to the end of my_file. */

status = fx_file_best_effort_allocate(&my_file, 1024, &actual_allocation);

/* If status equals FX_SUCCESS, the number of bytes
    allocated to the file is found in actual_allocation. */

```

### <a name="see-also"></a><span data-ttu-id="ec793-1348">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-1348">See Also</span></span>

- <span data-ttu-id="ec793-1349">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1349">fx_file_allocate</span></span>
- <span data-ttu-id="ec793-1350">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1350">fx_file_attributes_read</span></span>
- <span data-ttu-id="ec793-1351">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1351">fx_file_attributes_set</span></span>
- <span data-ttu-id="ec793-1352">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="ec793-1352">fx_file_close</span></span>
- <span data-ttu-id="ec793-1353">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1353">fx_file_create</span></span>
- <span data-ttu-id="ec793-1354">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1354">fx_file_date_time_set</span></span>
- <span data-ttu-id="ec793-1355">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-1355">fx_file_delete</span></span>
- <span data-ttu-id="ec793-1356">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1356">fx_file_extended_allocate</span></span>
- <span data-ttu-id="ec793-1357">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1357">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-1358">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1358">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="ec793-1359">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1359">fx_file_extended_seek</span></span>
- <span data-ttu-id="ec793-1360">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-1360">fx_file_extended_truncate</span></span>
- <span data-ttu-id="ec793-1361">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-1361">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="ec793-1362">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="ec793-1362">fx_file_open</span></span>
- <span data-ttu-id="ec793-1363">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1363">fx_file_read</span></span>
- <span data-ttu-id="ec793-1364">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1364">fx_file_relative_seek</span></span>
- <span data-ttu-id="ec793-1365">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1365">fx_file_rename</span></span>
- <span data-ttu-id="ec793-1366">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1366">fx_file_seek</span></span>
- <span data-ttu-id="ec793-1367">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-1367">fx_file_truncate</span></span>
- <span data-ttu-id="ec793-1368">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-1368">fx_file_truncate_release</span></span>
- <span data-ttu-id="ec793-1369">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="ec793-1369">fx_file_write</span></span>
- <span data-ttu-id="ec793-1370">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1370">fx_file_write_notify_set</span></span>
- <span data-ttu-id="ec793-1371">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1371">fx_unicode_file_create</span></span>
- <span data-ttu-id="ec793-1372">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1372">fx_unicode_file_rename</span></span>
- <span data-ttu-id="ec793-1373">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1373">fx_unicode_name_get</span></span>
- <span data-ttu-id="ec793-1374">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1374">fx_unicode_short_name_get</span></span>

## <a name="fx_file_close"></a><span data-ttu-id="ec793-1375">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="ec793-1375">fx_file_close</span></span>

<span data-ttu-id="ec793-1376">Закрывает файл</span><span class="sxs-lookup"><span data-stu-id="ec793-1376">Closes file</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-1377">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-1377">Prototype</span></span>

```c
UINT fx_file_close(FX_FILE *file_ptr);
```
### <a name="description"></a><span data-ttu-id="ec793-1378">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-1378">Description</span></span>

<span data-ttu-id="ec793-1379">Эта служба закрывает указанный файл.</span><span class="sxs-lookup"><span data-stu-id="ec793-1379">This service closes the specified file.</span></span> <span data-ttu-id="ec793-1380">Если файл был открыт для записи и если он был изменен, эта служба завершает процесс изменения файла, обновляя запись каталога с новым размером и текущими системными временем и датой.</span><span class="sxs-lookup"><span data-stu-id="ec793-1380">If the file was open for writing and if it was modified, this service completes the file modification process by updating its directory entry with the new size and the current system time and date.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-1381">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-1381">Input Parameters</span></span>

- <span data-ttu-id="ec793-1382">**file_ptr**: указатель на открытый ранее файл</span><span class="sxs-lookup"><span data-stu-id="ec793-1382">**file_ptr**: Pointer to a previously opened file.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-1383">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-1383">Return Values</span></span>

- <span data-ttu-id="ec793-1384">**FX_SUCCESS** (0x00) — файл успешно закрыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-1384">**FX_SUCCESS** (0x00) Successful file close.</span></span>
- <span data-ttu-id="ec793-1385">**FX_NOT_OPEN** (0x07) — указанный файл не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-1385">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="ec793-1386">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-1386">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="ec793-1387">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-1387">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="ec793-1388">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-1388">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-1389">**FX_PTR_ERROR** (0x18) — недопустимый носитель или указатель на атрибуты.</span><span class="sxs-lookup"><span data-stu-id="ec793-1389">**FX_PTR_ERROR** (0x18) Invalid media or attributes pointer.</span></span>
- <span data-ttu-id="ec793-1390">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-1390">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-1391">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-1391">Allowed From</span></span>

<span data-ttu-id="ec793-1392">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-1392">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-1393">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-1393">Example</span></span>

```c

FX_FILE        my_file;
UINT        status;

/* Close the previously opened file "my_file". */
status = fx_file_close(&my_file);

/* If status equals FX_SUCCESS, the file was closed successfully. */
```

### <a name="see-also"></a><span data-ttu-id="ec793-1394">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-1394">See Also</span></span>

- <span data-ttu-id="ec793-1395">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1395">fx_file_allocate</span></span>
- <span data-ttu-id="ec793-1396">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1396">fx_file_attributes_read</span></span>
- <span data-ttu-id="ec793-1397">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1397">fx_file_attributes_set</span></span>
- <span data-ttu-id="ec793-1398">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1398">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-1399">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1399">fx_file_create</span></span>
- <span data-ttu-id="ec793-1400">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1400">fx_file_date_time_set</span></span>
- <span data-ttu-id="ec793-1401">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-1401">fx_file_delete</span></span>
- <span data-ttu-id="ec793-1402">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1402">fx_file_extended_allocate</span></span>
- <span data-ttu-id="ec793-1403">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1403">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-1404">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1404">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="ec793-1405">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1405">fx_file_extended_seek</span></span>
- <span data-ttu-id="ec793-1406">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-1406">fx_file_extended_truncate</span></span>
- <span data-ttu-id="ec793-1407">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-1407">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="ec793-1408">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="ec793-1408">fx_file_open</span></span>
- <span data-ttu-id="ec793-1409">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1409">fx_file_read</span></span>
- <span data-ttu-id="ec793-1410">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1410">fx_file_relative_seek</span></span>
- <span data-ttu-id="ec793-1411">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1411">fx_file_rename</span></span>
- <span data-ttu-id="ec793-1412">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1412">fx_file_seek</span></span>
- <span data-ttu-id="ec793-1413">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-1413">fx_file_truncate</span></span>
- <span data-ttu-id="ec793-1414">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-1414">fx_file_truncate_release</span></span>
- <span data-ttu-id="ec793-1415">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="ec793-1415">fx_file_write</span></span>
- <span data-ttu-id="ec793-1416">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1416">fx_file_write_notify_set</span></span>
- <span data-ttu-id="ec793-1417">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1417">fx_unicode_file_create</span></span>
- <span data-ttu-id="ec793-1418">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1418">fx_unicode_file_rename</span></span>
- <span data-ttu-id="ec793-1419">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1419">fx_unicode_name_get</span></span>
- <span data-ttu-id="ec793-1420">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1420">fx_unicode_short_name_get</span></span>

## <a name="fx_file_create"></a><span data-ttu-id="ec793-1421">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1421">fx_file_create</span></span>

<span data-ttu-id="ec793-1422">Создает файл</span><span class="sxs-lookup"><span data-stu-id="ec793-1422">Creates file</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-1423">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-1423">Prototype</span></span>

```c
UINT fx_file_create(
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```
### <a name="description"></a><span data-ttu-id="ec793-1424">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-1424">Description</span></span>

<span data-ttu-id="ec793-1425">Эта служба создает указанный файл в каталоге по умолчанию или в каталоге, путь к которому указан с именем файла.</span><span class="sxs-lookup"><span data-stu-id="ec793-1425">This service creates the specified file in the default directory or in the directory path supplied with the file name.</span></span>

> [!WARNING]
> <span data-ttu-id="ec793-1426">*Эта служба создает файл нулевой длины, т. е. без выделенных кластеров. Выделение будет автоматически выполняться при последующих операциях записи файла. Также это можно сделать заранее с помощью службы fx_file_allocate или fx_file_extended_allocate, если размер превышает 4 ГБ).*</span><span class="sxs-lookup"><span data-stu-id="ec793-1426">*This service creates a file of zero length, i.e., no clusters allocated. Allocation will automatically take place on subsequent file writes or can be done in advance with the fx_file_allocate service or fx_file_extended_allocate for space beyond 4GB) service.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-1427">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-1427">Input Parameters</span></span>

- <span data-ttu-id="ec793-1428">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-1428">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="ec793-1429">**file_name**: указатель на имя создаваемого файла (путь к каталогу является необязательным)</span><span class="sxs-lookup"><span data-stu-id="ec793-1429">**file_name**: Pointer to the name of the file to create (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-1430">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-1430">Return Values</span></span>

- <span data-ttu-id="ec793-1431">**FX_SUCCESS** (0x00) — файл успешно создан.</span><span class="sxs-lookup"><span data-stu-id="ec793-1431">**FX_SUCCESS** (0x00) Successful file create.</span></span>
- <span data-ttu-id="ec793-1432">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-1432">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="ec793-1433">**FX_ALREADY_CREATED** (0x0B) — указанный файл уже создан.</span><span class="sxs-lookup"><span data-stu-id="ec793-1433">**FX_ALREADY_CREATED** (0x0B) Specified file was already created.</span></span>
- <span data-ttu-id="ec793-1434">**FX_NO_MORE_SPACE** (0x0A) —  в корневом каталоге больше нет записей, или нет доступных кластеров.</span><span class="sxs-lookup"><span data-stu-id="ec793-1434">**FX_NO_MORE_SPACE** (0x0A)    Either there are no more entries in the root directory or there are no more clusters available.</span></span>
- <span data-ttu-id="ec793-1435">**FX_INVALID_PATH** (0x0D) — указан недопустимый путь с именем файла.</span><span class="sxs-lookup"><span data-stu-id="ec793-1435">**FX_INVALID_PATH** (0x0D) Invalid path supplied with file name.</span></span>
- <span data-ttu-id="ec793-1436">**FX_INVALID_NAME** (0x0C) — недопустимое имя файла.</span><span class="sxs-lookup"><span data-stu-id="ec793-1436">**FX_INVALID_NAME** (0x0C) File name is invalid.</span></span>
- <span data-ttu-id="ec793-1437">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-1437">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="ec793-1438">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-1438">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="ec793-1439">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-1439">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="ec793-1440">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-1440">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="ec793-1441">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="ec793-1441">**FX_NO_MORE_SPACE** (0x0A)    No more space to complete the operation</span></span>
- <span data-ttu-id="ec793-1442">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="ec793-1442">**FX_MEDIA_INVALID** (0x02)Invalid media.</span></span>
- <span data-ttu-id="ec793-1443">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-1443">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-1444">**FX_WRITE_PROTECT** (0x23) — носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-1444">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="ec793-1445">**FX_PTR_ERROR** (0x18) — недопустимый носитель или указатель имени файла.</span><span class="sxs-lookup"><span data-stu-id="ec793-1445">**FX_PTR_ERROR** (0x18) Invalid media or file name pointer.</span></span>
- <span data-ttu-id="ec793-1446">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-1446">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-1447">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-1447">Allowed From</span></span>

<span data-ttu-id="ec793-1448">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-1448">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-1449">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-1449">Example</span></span>

```c

FX_MEDIA         my_media;
UINT             status;

/* Create a file called "myfile.txt" in the
    root or the default directory of the media. */

status = fx_file_create(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, a zero sized file named "myfile.txt". */
```

### <a name="see-also"></a><span data-ttu-id="ec793-1450">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-1450">See Also</span></span>
- <span data-ttu-id="ec793-1451">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1451">fx_file_allocate</span></span>
- <span data-ttu-id="ec793-1452">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1452">fx_file_attributes_read</span></span>
- <span data-ttu-id="ec793-1453">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1453">fx_file_attributes_set</span></span>
- <span data-ttu-id="ec793-1454">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1454">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-1455">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="ec793-1455">fx_file_close</span></span>
- <span data-ttu-id="ec793-1456">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1456">fx_file_date_time_set</span></span>
- <span data-ttu-id="ec793-1457">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-1457">fx_file_delete</span></span>
- <span data-ttu-id="ec793-1458">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1458">fx_file_extended_allocate</span></span>
- <span data-ttu-id="ec793-1459">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1459">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-1460">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1460">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="ec793-1461">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1461">fx_file_extended_seek</span></span>
- <span data-ttu-id="ec793-1462">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-1462">fx_file_extended_truncate</span></span>
- <span data-ttu-id="ec793-1463">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-1463">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="ec793-1464">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="ec793-1464">fx_file_open</span></span>
- <span data-ttu-id="ec793-1465">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1465">fx_file_read</span></span>
- <span data-ttu-id="ec793-1466">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1466">fx_file_relative_seek</span></span>
- <span data-ttu-id="ec793-1467">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1467">fx_file_rename</span></span>
- <span data-ttu-id="ec793-1468">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1468">fx_file_seek</span></span>
- <span data-ttu-id="ec793-1469">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-1469">fx_file_truncate</span></span>
- <span data-ttu-id="ec793-1470">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-1470">fx_file_truncate_release</span></span>
- <span data-ttu-id="ec793-1471">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="ec793-1471">fx_file_write</span></span>
- <span data-ttu-id="ec793-1472">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1472">fx_file_write_notify_set</span></span>
- <span data-ttu-id="ec793-1473">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1473">fx_unicode_file_create</span></span>
- <span data-ttu-id="ec793-1474">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1474">fx_unicode_file_rename</span></span>
- <span data-ttu-id="ec793-1475">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1475">fx_unicode_name_get</span></span>
- <span data-ttu-id="ec793-1476">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1476">fx_unicode_short_name_get</span></span>

## <a name="fx_file_date_time_set"></a><span data-ttu-id="ec793-1477">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1477">fx_file_date_time_set</span></span>

### <a name="sets-file-date-and-time"></a><span data-ttu-id="ec793-1478">Задает дату и время файла</span><span class="sxs-lookup"><span data-stu-id="ec793-1478">Sets file date and time</span></span>

<span data-ttu-id="ec793-1479">Задание даты и времени для файла</span><span class="sxs-lookup"><span data-stu-id="ec793-1479">Setting File Date and Time</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-1480">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-1480">Prototype</span></span>

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
### <a name="description"></a><span data-ttu-id="ec793-1481">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-1481">Description</span></span>

<span data-ttu-id="ec793-1482">Эта служба задает дату и время для указанного файла.</span><span class="sxs-lookup"><span data-stu-id="ec793-1482">This service sets the date and time of the specified file.</span></span>

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="input-parameters"></a><span data-ttu-id="ec793-1483">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-1483">Input Parameters</span></span>

- <span data-ttu-id="ec793-1484">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-1484">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="ec793-1485">**file_name**: указатель на имя файла</span><span class="sxs-lookup"><span data-stu-id="ec793-1485">**file_name**: Pointer to name of the file.</span></span>
- <span data-ttu-id="ec793-1486">**year**: значение года (1980–2107 включительно)</span><span class="sxs-lookup"><span data-stu-id="ec793-1486">**year**: Value of year (1980-2107 inclusive).</span></span>
- <span data-ttu-id="ec793-1487">**month**: значение месяца (1–12 включительно)</span><span class="sxs-lookup"><span data-stu-id="ec793-1487">**month**: Value of month (1-12 inclusive).</span></span>
- <span data-ttu-id="ec793-1488">**day**: значение дня (1–31 включительно)</span><span class="sxs-lookup"><span data-stu-id="ec793-1488">**day**: Value of day (1-31 inclusive).</span></span>
- <span data-ttu-id="ec793-1489">**hour**: значение часа (0–23 включительно)</span><span class="sxs-lookup"><span data-stu-id="ec793-1489">**hour**: Value of hour (0-23 inclusive).</span></span>
- <span data-ttu-id="ec793-1490">**minute**: значение минуты (0–59 включительно)</span><span class="sxs-lookup"><span data-stu-id="ec793-1490">**minute**: Value of minute (0-59 inclusive).</span></span>
- <span data-ttu-id="ec793-1491">**second**: значение секунды (0–59 включительно)</span><span class="sxs-lookup"><span data-stu-id="ec793-1491">**second**: Value of second (0-59 inclusive).</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-1492">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-1492">Return Values</span></span>

- <span data-ttu-id="ec793-1493">**FX_SUCCESS** (0x00) — дата/время успешно заданы.</span><span class="sxs-lookup"><span data-stu-id="ec793-1493">**FX_SUCCESS** (0x00) Successful date/time set.</span></span>
- <span data-ttu-id="ec793-1494">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-1494">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="ec793-1495">**FX_NOT_FOUND** (0x04) — файл не найден.</span><span class="sxs-lookup"><span data-stu-id="ec793-1495">**FX_NOT_FOUND** (0x04)    File was not found.</span></span>
- <span data-ttu-id="ec793-1496">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-1496">**FX_FILE_CORRUPT** (0x08)    File is corrupted.</span></span>
- <span data-ttu-id="ec793-1497">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-1497">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="ec793-1498">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-1498">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="ec793-1499">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-1499">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="ec793-1500">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="ec793-1500">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="ec793-1501">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-1501">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-1502">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-1502">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="ec793-1503">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.</span><span class="sxs-lookup"><span data-stu-id="ec793-1503">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="ec793-1504">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-1504">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>
- <span data-ttu-id="ec793-1505">**FX_INVALID_YEAR** (0x12) — недопустимый год.</span><span class="sxs-lookup"><span data-stu-id="ec793-1505">**FX_INVALID_YEAR** (0x12) Year is invalid.</span></span>
- <span data-ttu-id="ec793-1506">**FX_INVALID_MONTH** (0x13) — недопустимый месяц.</span><span class="sxs-lookup"><span data-stu-id="ec793-1506">**FX_INVALID_MONTH** (0x13) Month is invalid.</span></span>
- <span data-ttu-id="ec793-1507">**FX_INVALID_DAY** (0x14) — недопустимый день.</span><span class="sxs-lookup"><span data-stu-id="ec793-1507">**FX_INVALID_DAY** (0x14) Day is invalid.</span></span>
- <span data-ttu-id="ec793-1508">**FX_INVALID_HOUR** (0x15) — недопустимый час.</span><span class="sxs-lookup"><span data-stu-id="ec793-1508">**FX_INVALID_HOUR** (0x15)    Hour is invalid.</span></span>
- <span data-ttu-id="ec793-1509">**FX_INVALID_MINUTE** (0x16) — недопустимая минута.</span><span class="sxs-lookup"><span data-stu-id="ec793-1509">**FX_INVALID_MINUTE** (0x16) Minute is invalid.</span></span>
- <span data-ttu-id="ec793-1510">**FX_INVALID_SECOND** (0x17) — недопустимая секунда.</span><span class="sxs-lookup"><span data-stu-id="ec793-1510">**FX_INVALID_SECOND** (0x17) Second is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-1511">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-1511">Allowed From</span></span>

<span data-ttu-id="ec793-1512">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-1512">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-1513">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-1513">Example</span></span>

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="see-also"></a><span data-ttu-id="ec793-1514">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-1514">See Also</span></span>

- <span data-ttu-id="ec793-1515">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1515">fx_file_allocate</span></span>
- <span data-ttu-id="ec793-1516">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1516">fx_file_attributes_read</span></span>
- <span data-ttu-id="ec793-1517">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1517">fx_file_attributes_set</span></span>
- <span data-ttu-id="ec793-1518">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1518">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-1519">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="ec793-1519">fx_file_close</span></span>
- <span data-ttu-id="ec793-1520">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1520">fx_file_create</span></span>
- <span data-ttu-id="ec793-1521">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-1521">fx_file_delete</span></span>
- <span data-ttu-id="ec793-1522">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1522">fx_file_extended_allocate</span></span>
- <span data-ttu-id="ec793-1523">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1523">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-1524">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1524">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="ec793-1525">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1525">fx_file_extended_seek</span></span>
- <span data-ttu-id="ec793-1526">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-1526">fx_file_extended_truncate</span></span>
- <span data-ttu-id="ec793-1527">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-1527">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="ec793-1528">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="ec793-1528">fx_file_open</span></span>
- <span data-ttu-id="ec793-1529">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1529">fx_file_read</span></span>
- <span data-ttu-id="ec793-1530">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1530">fx_file_relative_seek</span></span>
- <span data-ttu-id="ec793-1531">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1531">fx_file_rename</span></span>
- <span data-ttu-id="ec793-1532">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1532">fx_file_seek</span></span>
- <span data-ttu-id="ec793-1533">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-1533">fx_file_truncate</span></span>
- <span data-ttu-id="ec793-1534">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-1534">fx_file_truncate_release</span></span>
- <span data-ttu-id="ec793-1535">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="ec793-1535">fx_file_write</span></span>
- <span data-ttu-id="ec793-1536">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1536">fx_file_write_notify_set</span></span>
- <span data-ttu-id="ec793-1537">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1537">fx_unicode_file_create</span></span>
- <span data-ttu-id="ec793-1538">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1538">fx_unicode_file_rename</span></span>
- <span data-ttu-id="ec793-1539">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1539">fx_unicode_name_get</span></span>
- <span data-ttu-id="ec793-1540">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1540">fx_unicode_short_name_get</span></span>

## <a name="fx_file_delete"></a><span data-ttu-id="ec793-1541">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-1541">fx_file_delete</span></span>

### <a name="deletes-file"></a><span data-ttu-id="ec793-1542">Удаляет файл</span><span class="sxs-lookup"><span data-stu-id="ec793-1542">Deletes file</span></span>

<span data-ttu-id="ec793-1543">Удаление файла</span><span class="sxs-lookup"><span data-stu-id="ec793-1543">File Deletion</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-1544">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-1544">Prototype</span></span>

```c
UINT fx_file_delete(
    FX_MEDIA *media_ptr, 
    CHAR *file_name);
```
### <a name="description"></a><span data-ttu-id="ec793-1545">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-1545">Description</span></span>

<span data-ttu-id="ec793-1546">Эта служба удаляет указанный файл.</span><span class="sxs-lookup"><span data-stu-id="ec793-1546">This service deletes the specified file.</span></span>


### <a name="input-parameters"></a><span data-ttu-id="ec793-1547">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-1547">Input Parameters</span></span>

- <span data-ttu-id="ec793-1548">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-1548">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="ec793-1549">**file_name**: указатель на имя удаляемого файла (путь к каталогу является необязательным)</span><span class="sxs-lookup"><span data-stu-id="ec793-1549">**file_name**: Pointer to the name of the file to delete (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-1550">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-1550">Return Values</span></span>

- <span data-ttu-id="ec793-1551">**FX_SUCCESS** (0x00) — файл успешно удален.</span><span class="sxs-lookup"><span data-stu-id="ec793-1551">**FX_SUCCESS** (0x00) Successful file delete.</span></span>
- <span data-ttu-id="ec793-1552">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-1552">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="ec793-1553">**FX_NOT_FOUND** (0x04) — указанный файл не найден.</span><span class="sxs-lookup"><span data-stu-id="ec793-1553">**FX_NOT_FOUND** (0x04) Specified file was not found.</span></span>
- <span data-ttu-id="ec793-1554">**FX_NOT_A_FILE** (0x05) — указанное имя файла является каталогом или томом.</span><span class="sxs-lookup"><span data-stu-id="ec793-1554">**FX_NOT_A_FILE** (0x05) Specified file name was a directory or volume.</span></span>
- <span data-ttu-id="ec793-1555">**FX_ACCESS_ERROR** (0x06) — указанный файл в настоящее время открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-1555">**FX_ACCESS_ERROR** (0x06) Specified file is currently open.</span></span>
- <span data-ttu-id="ec793-1556">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-1556">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="ec793-1557">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-1557">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="ec793-1558">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-1558">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="ec793-1559">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-1559">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="ec793-1560">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="ec793-1560">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="ec793-1561">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-1561">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-1562">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-1562">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="ec793-1563">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="ec793-1563">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="ec793-1564">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-1564">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="ec793-1565">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-1565">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-1566">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-1566">Allowed From</span></span>

<span data-ttu-id="ec793-1567">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-1567">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-1568">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-1568">Example</span></span>

```c

FX_MEDIA            my_media;
UINT                 status;
/* Delete the file "myfile.txt". */

status = fx_file_delete(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, "myfile.txt" has been deleted. */
```

### <a name="see-also"></a><span data-ttu-id="ec793-1569">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-1569">See Also</span></span>

- <span data-ttu-id="ec793-1570">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1570">fx_file_allocate</span></span>
- <span data-ttu-id="ec793-1571">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1571">fx_file_attributes_read</span></span>
- <span data-ttu-id="ec793-1572">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1572">fx_file_attributes_set</span></span>
- <span data-ttu-id="ec793-1573">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1573">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-1574">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="ec793-1574">fx_file_close</span></span>
- <span data-ttu-id="ec793-1575">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1575">fx_file_create</span></span>
- <span data-ttu-id="ec793-1576">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1576">fx_file_date_time_set</span></span>
- <span data-ttu-id="ec793-1577">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1577">fx_file_extended_allocate</span></span>
- <span data-ttu-id="ec793-1578">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1578">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-1579">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1579">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="ec793-1580">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1580">fx_file_extended_seek</span></span>
- <span data-ttu-id="ec793-1581">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-1581">fx_file_extended_truncate</span></span>
- <span data-ttu-id="ec793-1582">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-1582">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="ec793-1583">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="ec793-1583">fx_file_open</span></span>
- <span data-ttu-id="ec793-1584">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1584">fx_file_read</span></span>
- <span data-ttu-id="ec793-1585">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1585">fx_file_relative_seek</span></span>
- <span data-ttu-id="ec793-1586">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1586">fx_file_rename</span></span>
- <span data-ttu-id="ec793-1587">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1587">fx_file_seek</span></span>
- <span data-ttu-id="ec793-1588">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-1588">fx_file_truncate</span></span>
- <span data-ttu-id="ec793-1589">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-1589">fx_file_truncate_release</span></span>
- <span data-ttu-id="ec793-1590">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="ec793-1590">fx_file_write</span></span>
- <span data-ttu-id="ec793-1591">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1591">fx_file_write_notify_set</span></span>
- <span data-ttu-id="ec793-1592">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1592">fx_unicode_file_create</span></span>
- <span data-ttu-id="ec793-1593">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1593">fx_unicode_file_rename</span></span>
- <span data-ttu-id="ec793-1594">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1594">fx_unicode_name_get</span></span>
- <span data-ttu-id="ec793-1595">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1595">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_allocate"></a><span data-ttu-id="ec793-1596">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1596">fx_file_extended_allocate</span></span>

<span data-ttu-id="ec793-1597">Выделяет место для файла</span><span class="sxs-lookup"><span data-stu-id="ec793-1597">Allocates space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-1598">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-1598">Prototype</span></span>

```c
UINT fx_file_extended_allocate(
    FX_FILE *file_ptr, 
    ULONG64 size);
```
### <a name="description"></a><span data-ttu-id="ec793-1599">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-1599">Description</span></span>

<span data-ttu-id="ec793-1600">Эта служба выделяет один кластер или несколько последовательных и связывает их с концом указанного файла.</span><span class="sxs-lookup"><span data-stu-id="ec793-1600">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="ec793-1601">FileX определяет количество кластеров, необходимое для деления запрошенного размера на число байтов на кластер.</span><span class="sxs-lookup"><span data-stu-id="ec793-1601">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="ec793-1602">Затем результат округляется до следующего целого кластера.</span><span class="sxs-lookup"><span data-stu-id="ec793-1602">The result is then rounded up to the next whole cluster.</span></span>

<span data-ttu-id="ec793-1603">Эта служба разработана для exFAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-1603">This service is designed for exFAT.</span></span> <span data-ttu-id="ec793-1604">Параметр *size* принимает значение 64-разрядного целого числа, которое позволяет вызывающему объекту предварительно выделить пространство свыше 4 ГБ.</span><span class="sxs-lookup"><span data-stu-id="ec793-1604">The *size* parameter takes a 64-bit integer value, which allows the caller to pre-allocate space beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-1605">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-1605">Input Parameters</span></span>

- <span data-ttu-id="ec793-1606">**file_ptr**: указатель на открытый ранее файл</span><span class="sxs-lookup"><span data-stu-id="ec793-1606">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="ec793-1607">**size**: число байтов, выделяемых для файла</span><span class="sxs-lookup"><span data-stu-id="ec793-1607">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-1608">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-1608">Return Values</span></span>

- <span data-ttu-id="ec793-1609">**FX_SUCCESS** (0x00) — файл успешно выделен.</span><span class="sxs-lookup"><span data-stu-id="ec793-1609">**FX_SUCCESS** (0x00) Successful file allocation.</span></span>
- <span data-ttu-id="ec793-1610">**FX_ACCESS_ERROR** (0x06) — указанный файл не открыт для записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-1610">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="ec793-1611">**FX_NOT_OPEN** (0x07) — указанный файл в настоящее время не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-1611">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="ec793-1612">**FX_NO_MORE_SPACE** (0x0A) — на носителе, связанном с этим файлом, недостаточно доступных кластеров.</span><span class="sxs-lookup"><span data-stu-id="ec793-1612">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="ec793-1613">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-1613">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="ec793-1614">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-1614">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="ec793-1615">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-1615">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="ec793-1616">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-1616">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="ec793-1617">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-1617">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-1618">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-1618">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="ec793-1619">**FX_PTR_ERROR** (0x18) — недопустимый указатель на файл.</span><span class="sxs-lookup"><span data-stu-id="ec793-1619">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="ec793-1620">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-1620">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-1621">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-1621">Allowed From</span></span>

<span data-ttu-id="ec793-1622">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-1622">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-1623">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-1623">Example</span></span>

```c

FX_FILE            my_file;
UINT            status;
/* Allocate 0x100000000 bytes to the end of my_file. */

status = fx_file_extended_allocate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS the file now has
    one or more contiguous cluster(s) that can accommodate at least
    1024 bytes of user data. */
```

### <a name="see-also"></a><span data-ttu-id="ec793-1624">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-1624">See Also</span></span>

- <span data-ttu-id="ec793-1625">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1625">fx_file_allocate</span></span>
- <span data-ttu-id="ec793-1626">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1626">fx_file_attributes_read</span></span>
- <span data-ttu-id="ec793-1627">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1627">fx_file_attributes_set</span></span>
- <span data-ttu-id="ec793-1628">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1628">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-1629">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="ec793-1629">fx_file_close</span></span>
- <span data-ttu-id="ec793-1630">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1630">fx_file_create</span></span>
- <span data-ttu-id="ec793-1631">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1631">fx_file_date_time_set</span></span>
- <span data-ttu-id="ec793-1632">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-1632">fx_file_delete</span></span>
- <span data-ttu-id="ec793-1633">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1633">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-1634">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1634">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="ec793-1635">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1635">fx_file_extended_seek</span></span>
- <span data-ttu-id="ec793-1636">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-1636">fx_file_extended_truncate</span></span>
- <span data-ttu-id="ec793-1637">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-1637">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="ec793-1638">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="ec793-1638">fx_file_open</span></span>
- <span data-ttu-id="ec793-1639">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1639">fx_file_read</span></span>
- <span data-ttu-id="ec793-1640">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1640">fx_file_relative_seek</span></span>
- <span data-ttu-id="ec793-1641">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1641">fx_file_rename</span></span>
- <span data-ttu-id="ec793-1642">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1642">fx_file_seek</span></span>
- <span data-ttu-id="ec793-1643">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-1643">fx_file_truncate</span></span>
- <span data-ttu-id="ec793-1644">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-1644">fx_file_truncate_release</span></span>
- <span data-ttu-id="ec793-1645">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="ec793-1645">fx_file_write</span></span>
- <span data-ttu-id="ec793-1646">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1646">fx_file_write_notify_set</span></span>
- <span data-ttu-id="ec793-1647">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1647">fx_unicode_file_create</span></span>
- <span data-ttu-id="ec793-1648">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1648">fx_unicode_file_rename</span></span>
- <span data-ttu-id="ec793-1649">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1649">fx_unicode_name_get</span></span>
- <span data-ttu-id="ec793-1650">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1650">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_best_effort_allocate"></a><span data-ttu-id="ec793-1651">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1651">fx_file_extended_best_effort_allocate</span></span>

<span data-ttu-id="ec793-1652">Наиболее оптимальное выделение пространства для файла</span><span class="sxs-lookup"><span data-stu-id="ec793-1652">Best effort to allocate space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-1653">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-1653">Prototype</span></span>

```c
UINT fx_file_extended best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG64 size,
    ULONG64 *actual_size_allocated);
```
### <a name="description"></a><span data-ttu-id="ec793-1654">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-1654">Description</span></span>

<span data-ttu-id="ec793-1655">Эта служба выделяет один кластер или несколько последовательных и связывает их с концом указанного файла.</span><span class="sxs-lookup"><span data-stu-id="ec793-1655">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="ec793-1656">FileX определяет количество кластеров, необходимое для деления запрошенного размера на число байтов на кластер.</span><span class="sxs-lookup"><span data-stu-id="ec793-1656">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="ec793-1657">Затем результат округляется до следующего целого кластера.</span><span class="sxs-lookup"><span data-stu-id="ec793-1657">The result is then rounded up to the next whole cluster.</span></span> <span data-ttu-id="ec793-1658">Если на носителе нет достаточного количества последовательных кластеров, эта служба связывает с файлом самый большой доступный блок последовательных кластеров.</span><span class="sxs-lookup"><span data-stu-id="ec793-1658">If there are not enough consecutive clusters available in the media, this service links the largest available block of consecutive clusters to the file.</span></span> <span data-ttu-id="ec793-1659">Объем пространства, фактически выделяемый файлу, возвращается вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="ec793-1659">The amount of space actually allocated to the file is returned to the caller.</span></span>

<span data-ttu-id="ec793-1660">Эта служба разработана для exFAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-1660">This service is designed for exFAT.</span></span> <span data-ttu-id="ec793-1661">Параметр *size* принимает значение 64-разрядного целого числа, которое позволяет вызывающему объекту предварительно выделить пространство свыше 4 ГБ.</span><span class="sxs-lookup"><span data-stu-id="ec793-1661">The *size* parameter takes a 64-bit integer value, which allows the caller to pre-allocate space beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-1662">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-1662">Input Parameters</span></span>

- <span data-ttu-id="ec793-1663">**file_ptr**: указатель на открытый ранее файл</span><span class="sxs-lookup"><span data-stu-id="ec793-1663">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="ec793-1664">**size**: число байтов, выделяемых для файла</span><span class="sxs-lookup"><span data-stu-id="ec793-1664">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-1665">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-1665">Return Values</span></span>

- <span data-ttu-id="ec793-1666">**FX_SUCCESS** (0x00) — файл успешно выделен.</span><span class="sxs-lookup"><span data-stu-id="ec793-1666">**FX_SUCCESS** (0x00) Successful file allocation.</span></span>
- <span data-ttu-id="ec793-1667">**FX_ACCESS_ERROR** (0x06) — указанный файл не открыт для записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-1667">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="ec793-1668">**FX_NOT_OPEN** (0x07) — указанный файл в настоящее время не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-1668">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="ec793-1669">**FX_NO_MORE_SPACE** (0x0A) — на носителе, связанном с этим файлом, недостаточно доступных кластеров.</span><span class="sxs-lookup"><span data-stu-id="ec793-1669">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="ec793-1670">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-1670">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="ec793-1671">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-1671">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="ec793-1672">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-1672">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="ec793-1673">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-1673">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="ec793-1674">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-1674">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-1675">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-1675">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="ec793-1676">**FX_PTR_ERROR** (0x18) — недопустимый указатель на файл.</span><span class="sxs-lookup"><span data-stu-id="ec793-1676">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="ec793-1677">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-1677">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-1678">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-1678">Allowed From</span></span>

<span data-ttu-id="ec793-1679">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-1679">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-1680">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-1680">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="ec793-1681">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-1681">See Also</span></span>

- <span data-ttu-id="ec793-1682">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1682">fx_file_allocate</span></span>
- <span data-ttu-id="ec793-1683">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1683">fx_file_attributes_read</span></span>
- <span data-ttu-id="ec793-1684">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1684">fx_file_attributes_set</span></span>
- <span data-ttu-id="ec793-1685">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1685">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-1686">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="ec793-1686">fx_file_close</span></span>
- <span data-ttu-id="ec793-1687">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1687">fx_file_create</span></span>
- <span data-ttu-id="ec793-1688">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1688">fx_file_date_time_set</span></span>
- <span data-ttu-id="ec793-1689">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-1689">fx_file_delete</span></span>
- <span data-ttu-id="ec793-1690">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1690">fx_file_extended_allocate</span></span>
- <span data-ttu-id="ec793-1691">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1691">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="ec793-1692">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1692">fx_file_extended_seek</span></span>
- <span data-ttu-id="ec793-1693">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-1693">fx_file_extended_truncate</span></span>
- <span data-ttu-id="ec793-1694">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-1694">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="ec793-1695">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="ec793-1695">fx_file_open</span></span>
- <span data-ttu-id="ec793-1696">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1696">fx_file_read</span></span>
- <span data-ttu-id="ec793-1697">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1697">fx_file_relative_seek</span></span>
- <span data-ttu-id="ec793-1698">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1698">fx_file_rename</span></span>
- <span data-ttu-id="ec793-1699">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1699">fx_file_seek</span></span>
- <span data-ttu-id="ec793-1700">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-1700">fx_file_truncate</span></span>
- <span data-ttu-id="ec793-1701">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-1701">fx_file_truncate_release</span></span>
- <span data-ttu-id="ec793-1702">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="ec793-1702">fx_file_write</span></span>
- <span data-ttu-id="ec793-1703">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1703">fx_file_write_notify_set</span></span>
- <span data-ttu-id="ec793-1704">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1704">fx_unicode_file_create</span></span>
- <span data-ttu-id="ec793-1705">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1705">fx_unicode_file_rename</span></span>
- <span data-ttu-id="ec793-1706">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1706">fx_unicode_name_get</span></span>
- <span data-ttu-id="ec793-1707">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1707">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_relative_seek"></a><span data-ttu-id="ec793-1708">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1708">fx_file_extended_relative_seek</span></span>

<span data-ttu-id="ec793-1709">Размещение на указанное относительное смещение в байтах</span><span class="sxs-lookup"><span data-stu-id="ec793-1709">Positions to a relative byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-1710">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-1710">Prototype</span></span>

```c
UINT fx_file_extended_relative_seek(
    FX_FILE *file_ptr,
    ULONG64 byte_offset,
    UINT seek_from);
```
### <a name="description"></a><span data-ttu-id="ec793-1711">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-1711">Description</span></span>

<span data-ttu-id="ec793-1712">Эта служба размещает внутренний указатель чтения/записи файла на указанное относительное смещение в байтах.</span><span class="sxs-lookup"><span data-stu-id="ec793-1712">This service positions the internal file read/write pointer to the specified relative byte offset.</span></span> <span data-ttu-id="ec793-1713">Все последующие запросы на чтение или запись файла будут начинаться с этого места в файле.</span><span class="sxs-lookup"><span data-stu-id="ec793-1713">Any subsequent file read or write request will begin at this location in the file.</span></span>

<span data-ttu-id="ec793-1714">Эта служба разработана для exFAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-1714">This service is designed for exFAT.</span></span> <span data-ttu-id="ec793-1715">Параметр *byte_offset* принимает 64-разрядное целочисленное значение, которое позволяет вызывающему объекту изменить расположение указателя чтения/записи за пределами 4 ГБ.</span><span class="sxs-lookup"><span data-stu-id="ec793-1715">The *byte_offset* parameter takes a 64bit integer value, which allows the caller to reposition the read/write pointer beyond 4GB range.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec793-1716">*Если операция поиска пытается выполнить поиск после конца файла, указатель на чтение и запись файла помещается в конец файла. И наоборот, если операция поиска пытается установить положение после начала файла, указатель на чтение и запись файла помещается в начало файла.*</span><span class="sxs-lookup"><span data-stu-id="ec793-1716">*If the seek operation attempts to seek past the end of the file, the file's read/write pointer is positioned to the end of the file. Conversely, if the seek operation attempts to position past the beginning of the file, the file's read/write pointer is positioned to the beginning of the file.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-1717">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-1717">Input Parameters</span></span>

- <span data-ttu-id="ec793-1718">**file_ptr**: указатель на открытый ранее файл</span><span class="sxs-lookup"><span data-stu-id="ec793-1718">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="ec793-1719">**byte_offset**: требуемое относительное смещение в байтах в файле</span><span class="sxs-lookup"><span data-stu-id="ec793-1719">**byte_offset**: Desired relative byte offset in file.</span></span>
- <span data-ttu-id="ec793-1720">**seek_from**: направление и расположение для выполнения относительного поиска</span><span class="sxs-lookup"><span data-stu-id="ec793-1720">**seek_from**: The direction and location of where to perform the relative seek from.</span></span> <span data-ttu-id="ec793-1721">Допустимые параметры чтения определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ec793-1721">Valid seek options are defined as follows:</span></span>
  - <span data-ttu-id="ec793-1722">FX_SEEK_BEGIN (0x00)</span><span class="sxs-lookup"><span data-stu-id="ec793-1722">FX_SEEK_BEGIN (0x00)</span></span>
  - <span data-ttu-id="ec793-1723">FX_SEEK_END (0x01)</span><span class="sxs-lookup"><span data-stu-id="ec793-1723">FX_SEEK_END (0x01)</span></span>
  - <span data-ttu-id="ec793-1724">FX_SEEK_FORWARD (0x02)</span><span class="sxs-lookup"><span data-stu-id="ec793-1724">FX_SEEK_FORWARD (0x02)</span></span>
  - <span data-ttu-id="ec793-1725">FX_SEEK_BACK (0x03). Если указан параметр FX_SEEK_BEGIN, операция поиска выполняется с начала файла.</span><span class="sxs-lookup"><span data-stu-id="ec793-1725">FX_SEEK_BACK (0x03) If FX_SEEK_BEGIN is specified, the seek operation is performed from the beginning of the file.</span></span> <span data-ttu-id="ec793-1726">Если указан параметр FX_SEEK_END, операция поиска выполняется в обратном направлении с конца файла.</span><span class="sxs-lookup"><span data-stu-id="ec793-1726">If FX_SEEK_END is specified the seek operation is performed backward from the end of the file.</span></span> <span data-ttu-id="ec793-1727">Если указан параметр FX_SEEK_FORWARD, операция поиска выполняется вперед от текущего расположения файла.</span><span class="sxs-lookup"><span data-stu-id="ec793-1727">If FX_SEEK_FORWARD is specified, the seek operation is performed forward from the current file position.</span></span> <span data-ttu-id="ec793-1728">Если указан параметр FX_SEEK_BACK, операция поиска выполняется в обратном направлении от текущей позиции файла.</span><span class="sxs-lookup"><span data-stu-id="ec793-1728">If FX_SEEK_BACK is specified, the seek operation is performed backward from the current file position.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-1729">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-1729">Return Values</span></span>

- <span data-ttu-id="ec793-1730">**FX_SUCCESS** (0x00) — относительный поиск файла успешно выполнен.</span><span class="sxs-lookup"><span data-stu-id="ec793-1730">**FX_SUCCESS** (0x00) Successful file relative seek.</span></span>
- <span data-ttu-id="ec793-1731">**FX_NOT_OPEN** (0x07) — указанный файл в настоящее время не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-1731">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="ec793-1732">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-1732">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="ec793-1733">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-1733">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="ec793-1734">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="ec793-1734">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="ec793-1735">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-1735">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-1736">**FX_PTR_ERROR** (0x18) — недопустимый указатель на файл.</span><span class="sxs-lookup"><span data-stu-id="ec793-1736">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="ec793-1737">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-1737">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-1738">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-1738">Allowed From</span></span>

<span data-ttu-id="ec793-1739">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-1739">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-1740">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-1740">Example</span></span>

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to seek forward 0x100000000 bytes in "my_file". */

status = fx_file_extended_relative_seek(&my_file, 0x100000000, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write
    pointers are positioned 0x100000000 bytes forward. */
```

### <a name="see-also"></a><span data-ttu-id="ec793-1741">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-1741">See Also</span></span>

- <span data-ttu-id="ec793-1742">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1742">fx_file_allocate</span></span>
- <span data-ttu-id="ec793-1743">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1743">fx_file_attributes_read</span></span>
- <span data-ttu-id="ec793-1744">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1744">fx_file_attributes_set</span></span>
- <span data-ttu-id="ec793-1745">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1745">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-1746">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="ec793-1746">fx_file_close</span></span>
- <span data-ttu-id="ec793-1747">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1747">fx_file_create</span></span>
- <span data-ttu-id="ec793-1748">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1748">fx_file_date_time_set</span></span>
- <span data-ttu-id="ec793-1749">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-1749">fx_file_delete</span></span>
- <span data-ttu-id="ec793-1750">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1750">fx_file_extended_allocate</span></span>
- <span data-ttu-id="ec793-1751">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1751">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-1752">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1752">fx_file_extended_seek</span></span>
- <span data-ttu-id="ec793-1753">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-1753">fx_file_extended_truncate</span></span>
- <span data-ttu-id="ec793-1754">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-1754">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="ec793-1755">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="ec793-1755">fx_file_open</span></span>
- <span data-ttu-id="ec793-1756">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1756">fx_file_read</span></span>
- <span data-ttu-id="ec793-1757">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1757">fx_file_relative_seek</span></span>
- <span data-ttu-id="ec793-1758">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1758">fx_file_rename</span></span>
- <span data-ttu-id="ec793-1759">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1759">fx_file_seek</span></span>
- <span data-ttu-id="ec793-1760">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-1760">fx_file_truncate</span></span>
- <span data-ttu-id="ec793-1761">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-1761">fx_file_truncate_release</span></span>
- <span data-ttu-id="ec793-1762">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="ec793-1762">fx_file_write</span></span>
- <span data-ttu-id="ec793-1763">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1763">fx_file_write_notify_set</span></span>
- <span data-ttu-id="ec793-1764">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1764">fx_unicode_file_create</span></span>
- <span data-ttu-id="ec793-1765">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1765">fx_unicode_file_rename</span></span>
- <span data-ttu-id="ec793-1766">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1766">fx_unicode_name_get</span></span>
- <span data-ttu-id="ec793-1767">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1767">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_seek"></a><span data-ttu-id="ec793-1768">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1768">fx_file_extended_seek</span></span>

<span data-ttu-id="ec793-1769">Размещение на указанное смещение в байтах</span><span class="sxs-lookup"><span data-stu-id="ec793-1769">Positions to byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-1770">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-1770">Prototype</span></span>

```c
UINT fx_file_extended_seek(
    FX_FILE *file_ptr, 
    ULONG64 byte_offset);
```
### <a name="description"></a><span data-ttu-id="ec793-1771">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-1771">Description</span></span>

<span data-ttu-id="ec793-1772">Эта служба размещает внутренний указатель чтения/записи файла на указанное смещение в байтах.</span><span class="sxs-lookup"><span data-stu-id="ec793-1772">This service positions the internal file read/write pointer to the specified byte offset.</span></span> <span data-ttu-id="ec793-1773">Все последующие запросы на чтение или запись файла будут начинаться с этого места в файле.</span><span class="sxs-lookup"><span data-stu-id="ec793-1773">Any subsequent file read or write request will begin at this location in the file.</span></span>

<span data-ttu-id="ec793-1774">Эта служба разработана для exFAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-1774">This service is designed for exFAT.</span></span> <span data-ttu-id="ec793-1775">Параметр *byte_offset* принимает 64-разрядное целочисленное значение, которое позволяет вызывающему объекту изменить расположение указателя чтения/записи за пределами 4 ГБ.</span><span class="sxs-lookup"><span data-stu-id="ec793-1775">The *byte_offset* parameter takes a 64bit integer value, which allows the caller to reposition the read/write pointer beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-1776">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-1776">Input Parameters</span></span>

- <span data-ttu-id="ec793-1777">**file_ptr**: указатель на блок управления файлом</span><span class="sxs-lookup"><span data-stu-id="ec793-1777">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="ec793-1778">**byte_offset**: требуемое смещение в байтах в файле</span><span class="sxs-lookup"><span data-stu-id="ec793-1778">**byte_offset**: Desired byte offset in file.</span></span> <span data-ttu-id="ec793-1779">При нулевом значении указатель чтения/записи будет размещен в начале файла, а при значении, превышающем размер файла, указатель чтения/записи будет помещен в конец файла.</span><span class="sxs-lookup"><span data-stu-id="ec793-1779">A value of zero will position the read/write pointer at the beginning of the file, while a value greater than the file's size will position the read/write pointer at the end of the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-1780">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-1780">Return Values</span></span>

- <span data-ttu-id="ec793-1781">**FX_SUCCESS** (0x00) — файл успешно найден.</span><span class="sxs-lookup"><span data-stu-id="ec793-1781">**FX_SUCCESS** (0x00) Successful file seek.</span></span>
- <span data-ttu-id="ec793-1782">**FX_NOT_OPEN** (0x07) — указанный файл не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-1782">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="ec793-1783">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-1783">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="ec793-1784">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-1784">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="ec793-1785">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="ec793-1785">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="ec793-1786">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-1786">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-1787">**FX_PTR_ERROR** (0x18) — недопустимый указатель на файл.</span><span class="sxs-lookup"><span data-stu-id="ec793-1787">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="ec793-1788">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-1788">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-1789">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-1789">Allowed From</span></span>

<span data-ttu-id="ec793-1790">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-1790">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-1791">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-1791">Example</span></span>

```c
FX_FILE         my_file;
UINT             status;
/* Seek to position 0x100000000 of "my_file." */

status = fx_file_extended_seek(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned 0x100000000 bytes from the beginning of the file. */
```

### <a name="see-also"></a><span data-ttu-id="ec793-1792">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-1792">See Also</span></span>

- <span data-ttu-id="ec793-1793">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1793">fx_file_allocate</span></span>
- <span data-ttu-id="ec793-1794">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1794">fx_file_attributes_read</span></span>
- <span data-ttu-id="ec793-1795">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1795">fx_file_attributes_set</span></span>
- <span data-ttu-id="ec793-1796">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1796">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-1797">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="ec793-1797">fx_file_close</span></span>
- <span data-ttu-id="ec793-1798">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1798">fx_file_create</span></span>
- <span data-ttu-id="ec793-1799">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1799">fx_file_date_time_set</span></span>
- <span data-ttu-id="ec793-1800">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-1800">fx_file_delete</span></span>
- <span data-ttu-id="ec793-1801">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1801">fx_file_extended_allocate</span></span>
- <span data-ttu-id="ec793-1802">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1802">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-1803">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1803">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="ec793-1804">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-1804">fx_file_extended_truncate</span></span>
- <span data-ttu-id="ec793-1805">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-1805">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="ec793-1806">fx_file_open- fx_file_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1806">fx_file_open- fx_file_read</span></span>
- <span data-ttu-id="ec793-1807">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1807">fx_file_relative_seek</span></span>
- <span data-ttu-id="ec793-1808">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1808">fx_file_rename</span></span>
- <span data-ttu-id="ec793-1809">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1809">fx_file_seek</span></span>
- <span data-ttu-id="ec793-1810">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-1810">fx_file_truncate</span></span>
- <span data-ttu-id="ec793-1811">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-1811">fx_file_truncate_release</span></span>
- <span data-ttu-id="ec793-1812">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="ec793-1812">fx_file_write</span></span>
- <span data-ttu-id="ec793-1813">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1813">fx_file_write_notify_set</span></span>
- <span data-ttu-id="ec793-1814">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1814">fx_unicode_file_create</span></span>
- <span data-ttu-id="ec793-1815">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1815">fx_unicode_file_rename</span></span>
- <span data-ttu-id="ec793-1816">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1816">fx_unicode_name_get</span></span>
- <span data-ttu-id="ec793-1817">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1817">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_truncate"></a><span data-ttu-id="ec793-1818">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-1818">fx_file_extended_truncate</span></span>

<span data-ttu-id="ec793-1819">Усекает файл</span><span class="sxs-lookup"><span data-stu-id="ec793-1819">Truncates file</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-1820">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-1820">Prototype</span></span>

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG64 size);
```
### <a name="description"></a><span data-ttu-id="ec793-1821">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-1821">Description</span></span>

<span data-ttu-id="ec793-1822">Эта служба усекает размер файла до указанного.</span><span class="sxs-lookup"><span data-stu-id="ec793-1822">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="ec793-1823">Если указанный размер превышает фактический размер файла, эта служба не выполняет никаких действий.</span><span class="sxs-lookup"><span data-stu-id="ec793-1823">If the supplied size is greater than the actual file size, this service doesn't do anything.</span></span> <span data-ttu-id="ec793-1824">Ни один из кластеров носителя, связанных с файлом, не освобождается.</span><span class="sxs-lookup"><span data-stu-id="ec793-1824">None of the media clusters associated with the file are released.</span></span>

> [!WARNING]
> <span data-ttu-id="ec793-1825">*Проявляйте осторожность при усечении файлов, которые также могут быть открыты для одновременного чтения. Усечение файла, открытого для чтения, может привести к чтению недопустимых данных.*</span><span class="sxs-lookup"><span data-stu-id="ec793-1825">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="ec793-1826">Эта служба разработана для exFAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-1826">This service is designed for exFAT.</span></span> <span data-ttu-id="ec793-1827">Параметр *size* принимает значение 64-разрядного целого числа, которое позволяет вызывающему объекту действовать за пределами 4 ГБ.</span><span class="sxs-lookup"><span data-stu-id="ec793-1827">The *size* parameter takes a 64-bit integer value, which allows the caller to operate beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-1828">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-1828">Input Parameters</span></span>

- <span data-ttu-id="ec793-1829">**file_ptr**: указатель на блок управления файлом</span><span class="sxs-lookup"><span data-stu-id="ec793-1829">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="ec793-1830">**size**: новый размер файла</span><span class="sxs-lookup"><span data-stu-id="ec793-1830">**size**: New file size.</span></span> <span data-ttu-id="ec793-1831">Число байтов после нового размера файла не учитывается.</span><span class="sxs-lookup"><span data-stu-id="ec793-1831">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-1832">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-1832">Return Values</span></span>

- <span data-ttu-id="ec793-1833">**FX_SUCCESS** (0x00) — файл успешно усечен.</span><span class="sxs-lookup"><span data-stu-id="ec793-1833">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="ec793-1834">**FX_NOT_OPEN** (0x07) — указанный файл не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-1834">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="ec793-1835">**FX_ACCESS_ERROR** (0x06) — указанный файл не открыт для записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-1835">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="ec793-1836">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-1836">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="ec793-1837">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-1837">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="ec793-1838">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-1838">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="ec793-1839">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="ec793-1839">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="ec793-1840">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-1840">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-1841">**FX_WRITE_PROTECT** (0x23) — носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-1841">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="ec793-1842">**FX_PTR_ERROR** (0x18) — недопустимый указатель на файл.</span><span class="sxs-lookup"><span data-stu-id="ec793-1842">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="ec793-1843">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-1843">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-1844">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-1844">Allowed From</span></span>

<span data-ttu-id="ec793-1845">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-1845">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-1846">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-1846">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Truncate "my_file" to 0x100000000 bytes. */

status = fx_file_extended_truncate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, "my_file" contains 0x100000000 or fewer bytes. */
```

### <a name="see-also"></a><span data-ttu-id="ec793-1847">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-1847">See Also</span></span>

- <span data-ttu-id="ec793-1848">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1848">fx_file_allocate</span></span>
- <span data-ttu-id="ec793-1849">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1849">fx_file_attributes_read</span></span>
- <span data-ttu-id="ec793-1850">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1850">fx_file_attributes_set</span></span>
- <span data-ttu-id="ec793-1851">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1851">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-1852">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="ec793-1852">fx_file_close</span></span>
- <span data-ttu-id="ec793-1853">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1853">fx_file_create</span></span>
- <span data-ttu-id="ec793-1854">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1854">fx_file_date_time_set</span></span>
- <span data-ttu-id="ec793-1855">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-1855">fx_file_delete</span></span>
- <span data-ttu-id="ec793-1856">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1856">fx_file_extended_allocate</span></span>
- <span data-ttu-id="ec793-1857">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1857">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-1858">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1858">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="ec793-1859">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1859">fx_file_extended_seek</span></span>
- <span data-ttu-id="ec793-1860">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-1860">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="ec793-1861">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="ec793-1861">fx_file_open</span></span>
- <span data-ttu-id="ec793-1862">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1862">fx_file_read</span></span>
- <span data-ttu-id="ec793-1863">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1863">fx_file_relative_seek</span></span>
- <span data-ttu-id="ec793-1864">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1864">fx_file_rename</span></span>
- <span data-ttu-id="ec793-1865">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1865">fx_file_seek</span></span>
- <span data-ttu-id="ec793-1866">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-1866">fx_file_truncate</span></span>
- <span data-ttu-id="ec793-1867">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-1867">fx_file_truncate_release</span></span>
- <span data-ttu-id="ec793-1868">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="ec793-1868">fx_file_write</span></span>
- <span data-ttu-id="ec793-1869">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1869">fx_file_write_notify_set</span></span>
- <span data-ttu-id="ec793-1870">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1870">fx_unicode_file_create</span></span>
- <span data-ttu-id="ec793-1871">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1871">fx_unicode_file_rename</span></span>
- <span data-ttu-id="ec793-1872">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1872">fx_unicode_name_get</span></span>
- <span data-ttu-id="ec793-1873">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1873">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_truncate_release"></a><span data-ttu-id="ec793-1874">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-1874">fx_file_extended_truncate_release</span></span>

<span data-ttu-id="ec793-1875">Усекает кластеры файлов и выпусков</span><span class="sxs-lookup"><span data-stu-id="ec793-1875">Truncates file and releases cluster(s)</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-1876">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-1876">Prototype</span></span>

```c
UINT fx_file_extended_truncate_release(
    FX_FILE *file_ptr, 
    ULONG64 size);
```

### <a name="description"></a><span data-ttu-id="ec793-1877">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-1877">Description</span></span>

<span data-ttu-id="ec793-1878">Эта служба усекает размер файла до указанного.</span><span class="sxs-lookup"><span data-stu-id="ec793-1878">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="ec793-1879">Если указанный размер превышает фактический размер файла, эта служба не выполняет никаких действий.</span><span class="sxs-lookup"><span data-stu-id="ec793-1879">If the supplied size is greater than the actual file size, this service does not do anything.</span></span> <span data-ttu-id="ec793-1880">В отличие от службы ***fx_file_extended_truncate*** эта служба освобождает неиспользуемые кластеры.</span><span class="sxs-lookup"><span data-stu-id="ec793-1880">Unlike the ***fx_file_extended_truncate*** service, this service does release any unused clusters.</span></span>

> [!WARNING]
> <span data-ttu-id="ec793-1881">*Проявляйте осторожность при усечении файлов, которые также могут быть открыты для одновременного чтения. Усечение файла, открытого для чтения, может привести к чтению недопустимых данных.*</span><span class="sxs-lookup"><span data-stu-id="ec793-1881">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="ec793-1882">Эта служба разработана для exFAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-1882">This service is designed for exFAT.</span></span> <span data-ttu-id="ec793-1883">Параметр *size* принимает значение 64-разрядного целого числа, которое позволяет вызывающему объекту действовать за пределами 4 ГБ.</span><span class="sxs-lookup"><span data-stu-id="ec793-1883">The *size* parameter takes a 64-bit integer value, which allows the caller to operate beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-1884">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-1884">Input Parameters</span></span>

- <span data-ttu-id="ec793-1885">**file_ptr**: указатель на открытый ранее файл</span><span class="sxs-lookup"><span data-stu-id="ec793-1885">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="ec793-1886">**size**: новый размер файла</span><span class="sxs-lookup"><span data-stu-id="ec793-1886">**size**: New file size.</span></span> <span data-ttu-id="ec793-1887">Число байтов после нового размера файла не учитывается.</span><span class="sxs-lookup"><span data-stu-id="ec793-1887">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-1888">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-1888">Return Values</span></span>

- <span data-ttu-id="ec793-1889">**FX_SUCCESS** (0x00) — файл успешно усечен.</span><span class="sxs-lookup"><span data-stu-id="ec793-1889">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="ec793-1890">**FX_ACCESS_ERROR** (0x06) — указанный файл не открыт для записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-1890">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="ec793-1891">**FX_NOT_OPEN** (0x07) — указанный файл в настоящее время не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-1891">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="ec793-1892">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-1892">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="ec793-1893">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-1893">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="ec793-1894">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-1894">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="ec793-1895">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-1895">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="ec793-1896">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="ec793-1896">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="ec793-1897">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-1897">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-1898">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-1898">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="ec793-1899">**FX_PTR_ERROR** (0x18) — недопустимый указатель на файл.</span><span class="sxs-lookup"><span data-stu-id="ec793-1899">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="ec793-1900">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-1900">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-1901">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-1901">Allowed From</span></span>

<span data-ttu-id="ec793-1902">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-1902">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-1903">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-1903">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Attempt to truncate everything after the first 0x100000000 bytes of "my_file". */

status = fx_file_extended_truncate_release(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file is now 0x100000000
    bytes or fewer and all unused clusters have been released. */
```

### <a name="see-also"></a><span data-ttu-id="ec793-1904">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-1904">See Also</span></span>

- <span data-ttu-id="ec793-1905">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1905">fx_file_allocate</span></span>
- <span data-ttu-id="ec793-1906">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1906">fx_file_attributes_read</span></span>
- <span data-ttu-id="ec793-1907">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1907">fx_file_attributes_set</span></span>
- <span data-ttu-id="ec793-1908">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1908">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-1909">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="ec793-1909">fx_file_close</span></span>
- <span data-ttu-id="ec793-1910">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1910">fx_file_create</span></span>
- <span data-ttu-id="ec793-1911">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1911">fx_file_date_time_set</span></span>
- <span data-ttu-id="ec793-1912">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-1912">fx_file_delete</span></span>
- <span data-ttu-id="ec793-1913">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1913">fx_file_extended_allocate</span></span>
- <span data-ttu-id="ec793-1914">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1914">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-1915">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1915">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="ec793-1916">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1916">fx_file_extended_seek</span></span>
- <span data-ttu-id="ec793-1917">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-1917">fx_file_extended_truncate</span></span>
- <span data-ttu-id="ec793-1918">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="ec793-1918">fx_file_open</span></span>
- <span data-ttu-id="ec793-1919">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1919">fx_file_read</span></span>
- <span data-ttu-id="ec793-1920">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1920">fx_file_relative_seek</span></span>
- <span data-ttu-id="ec793-1921">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1921">fx_file_rename</span></span>
- <span data-ttu-id="ec793-1922">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1922">fx_file_seek</span></span>
- <span data-ttu-id="ec793-1923">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-1923">fx_file_truncate</span></span>
- <span data-ttu-id="ec793-1924">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-1924">fx_file_truncate_release</span></span>
- <span data-ttu-id="ec793-1925">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="ec793-1925">fx_file_write</span></span>
- <span data-ttu-id="ec793-1926">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1926">fx_file_write_notify_set</span></span>
- <span data-ttu-id="ec793-1927">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1927">fx_unicode_file_create</span></span>
- <span data-ttu-id="ec793-1928">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1928">fx_unicode_file_rename</span></span>
- <span data-ttu-id="ec793-1929">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1929">fx_unicode_name_get</span></span>
- <span data-ttu-id="ec793-1930">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1930">fx_unicode_short_name_get</span></span>

## <a name="fx_file_open"></a><span data-ttu-id="ec793-1931">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="ec793-1931">fx_file_open</span></span>

<span data-ttu-id="ec793-1932">Открывает файл</span><span class="sxs-lookup"><span data-stu-id="ec793-1932">Opens file</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-1933">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-1933">Prototype</span></span>

```c
UINT fx_file_open(
    FX_MEDIA *media_ptr,
    FX_FILE *file_ptr,
    CHAR *file_name,
    UINT open_type);
```
### <a name="description"></a><span data-ttu-id="ec793-1934">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-1934">Description</span></span>

<span data-ttu-id="ec793-1935">Эта служба открывает указанный файл для чтения или записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-1935">This service opens the specified file for either reading or writing.</span></span> <span data-ttu-id="ec793-1936">Файл может быть открыт для чтения несколько раз, однако открыть файл для записи можно только один раз, пока модуль записи не закроет файл.</span><span class="sxs-lookup"><span data-stu-id="ec793-1936">A file may be opened for reading multiple times, while a file can only be opened for writing once until the writer closes the file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec793-1937">*Необходимо соблюдать осторожность, если файл параллельно открыт для чтения и записи. Запись файла, выполняемая при одновременном открытии файла для чтения, может не отображаться средством чтения, если только средство чтения не закроет и не откроет файл для чтения. Аналогично, при использовании служб усечения файлов следует соблюдать осторожность. Если файл усекается модулем записи, читатели одного и того же файла могут вернуть недопустимые данные.*</span><span class="sxs-lookup"><span data-stu-id="ec793-1937">*Care must be taken if a file is concurrently open for reading and writing. File writing performed when a file is simultaneously opened for reading may not be seen by the reader, unless the reader closes and reopens the file for reading. Similarly, the file writer should be careful when using file truncate services. If a file is truncated by the writer, readers of the same file could return invalid data.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-1938">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-1938">Input Parameters</span></span>

- <span data-ttu-id="ec793-1939">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-1939">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="ec793-1940">**file_ptr**: указатель на блок управления файлом</span><span class="sxs-lookup"><span data-stu-id="ec793-1940">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="ec793-1941">**file_name**: указатель на имя открываемого файла (путь к каталогу является необязательным)</span><span class="sxs-lookup"><span data-stu-id="ec793-1941">**file_name**: Pointer to the name of the file to open (directory path is optional).</span></span>
- <span data-ttu-id="ec793-1942">**open_type**: тип открываемого файла</span><span class="sxs-lookup"><span data-stu-id="ec793-1942">**open_type**: Type of file open.</span></span> <span data-ttu-id="ec793-1943">Допустимые параметры типа открытия</span><span class="sxs-lookup"><span data-stu-id="ec793-1943">Valid open type options are:</span></span>
  - <span data-ttu-id="ec793-1944">FX_OPEN_FOR_READ (0x00)</span><span class="sxs-lookup"><span data-stu-id="ec793-1944">FX_OPEN_FOR_READ (0x00)</span></span>
  - <span data-ttu-id="ec793-1945">FX_OPEN_FOR_WRITE (0x01)</span><span class="sxs-lookup"><span data-stu-id="ec793-1945">FX_OPEN_FOR_WRITE (0x01)</span></span>
  - <span data-ttu-id="ec793-1946">FX_OPEN_FOR_READ_FAST (0x02)</span><span class="sxs-lookup"><span data-stu-id="ec793-1946">FX_OPEN_FOR_READ_FAST (0x02)</span></span>

<span data-ttu-id="ec793-1947">Открытие файлов с помощью FX_OPEN_FOR_READ и FX_OPEN_FOR_READ_FAST выполняется аналогично.</span><span class="sxs-lookup"><span data-stu-id="ec793-1947">Opening files with FX_OPEN_FOR_READ and FX_OPEN_FOR_READ_FAST is similar:</span></span>

- <span data-ttu-id="ec793-1948">FX_OPEN_FOR_READ включает проверку того, что связанный список кластеров, составляющих файл, не изменяется, а FX_OPEN_FOR_READ_FAST не выполняет такую проверку, что ускоряет работу.</span><span class="sxs-lookup"><span data-stu-id="ec793-1948">FX_OPEN_FOR_READ includes verification that the linked-list of clusters that comprise the file are intact, and FX_OPEN_FOR_READ_FAST does not perform this verification, which makes it faster.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-1949">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-1949">Return Values</span></span>

- <span data-ttu-id="ec793-1950">**FX_SUCCESS** (0x00) — файл успешно открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-1950">**FX_SUCCESS** (0x00) Successful file open.</span></span>
- <span data-ttu-id="ec793-1951">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-1951">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="ec793-1952">**FX_NOT_FOUND** (0x04) — указанный файл не найден.</span><span class="sxs-lookup"><span data-stu-id="ec793-1952">**FX_NOT_FOUND** (0x04) Specified file was not found.</span></span>
- <span data-ttu-id="ec793-1953">**FX_NOT_A_FILE** (0x05) — указанное имя файла является каталогом или томом.</span><span class="sxs-lookup"><span data-stu-id="ec793-1953">**FX_NOT_A_FILE** (0x05) Specified file name was a directory or volume.</span></span>
- <span data-ttu-id="ec793-1954">**FX_FILE_CORRUPT** (0x08) — указанный файл поврежден, или его не удалось открыть.</span><span class="sxs-lookup"><span data-stu-id="ec793-1954">**FX_FILE_CORRUPT** (0x08) Specified file is corrupt and the open failed.</span></span>
- <span data-ttu-id="ec793-1955">**FX_ACCESS_ERROR** (0x06) — указанный файл уже открыт, или недопустимый тип открытия.</span><span class="sxs-lookup"><span data-stu-id="ec793-1955">**FX_ACCESS_ERROR** (0x06) Specified file is already open or open type is invalid.</span></span>
- <span data-ttu-id="ec793-1956">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-1956">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="ec793-1957">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="ec793-1957">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="ec793-1958">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-1958">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="ec793-1959">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="ec793-1959">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="ec793-1960">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-1960">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-1961">**FX_WRITE_PROTECT** (0x23) — носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-1961">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="ec793-1962">**FX_PTR_ERROR** (0x18) — недопустимый носитель или указатель файла.</span><span class="sxs-lookup"><span data-stu-id="ec793-1962">**FX_PTR_ERROR** (0x18) Invalid media or file pointer.</span></span>
- <span data-ttu-id="ec793-1963">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-1963">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-1964">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-1964">Allowed From</span></span>

<span data-ttu-id="ec793-1965">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-1965">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-1966">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-1966">Example</span></span>

```c
FX_MEDIA     my_media;
FX_FILE     my_file;
UINT         status;

/* Open the file "myfile.txt" for reading. */

status = fx_file_open(&my_media, &my_file, "myfile.txt", FX_OPEN_FOR_READ);

/* If status equals FX_SUCCESS, file "myfile.txt" is now
    open and may be accessed now with the my_file pointer. */
```

### <a name="see-also"></a><span data-ttu-id="ec793-1967">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-1967">See Also</span></span>

- <span data-ttu-id="ec793-1968">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1968">fx_file_allocate</span></span>
- <span data-ttu-id="ec793-1969">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1969">fx_file_attributes_read</span></span>
- <span data-ttu-id="ec793-1970">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1970">fx_file_attributes_set</span></span>
- <span data-ttu-id="ec793-1971">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1971">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-1972">fx_file_close- fx_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1972">fx_file_close- fx_file_create</span></span>
- <span data-ttu-id="ec793-1973">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1973">fx_file_date_time_set</span></span>
- <span data-ttu-id="ec793-1974">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-1974">fx_file_delete</span></span>
- <span data-ttu-id="ec793-1975">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1975">fx_file_extended_allocate</span></span>
- <span data-ttu-id="ec793-1976">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-1976">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-1977">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1977">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="ec793-1978">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1978">fx_file_extended_seek</span></span>
- <span data-ttu-id="ec793-1979">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-1979">fx_file_extended_truncate</span></span>
- <span data-ttu-id="ec793-1980">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-1980">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="ec793-1981">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1981">fx_file_read</span></span>
- <span data-ttu-id="ec793-1982">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1982">fx_file_relative_seek</span></span>
- <span data-ttu-id="ec793-1983">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1983">fx_file_rename</span></span>
- <span data-ttu-id="ec793-1984">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-1984">fx_file_seek</span></span>
- <span data-ttu-id="ec793-1985">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-1985">fx_file_truncate</span></span>
- <span data-ttu-id="ec793-1986">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-1986">fx_file_truncate_release</span></span>
- <span data-ttu-id="ec793-1987">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="ec793-1987">fx_file_write</span></span>
- <span data-ttu-id="ec793-1988">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-1988">fx_file_write_notify_set</span></span>
- <span data-ttu-id="ec793-1989">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-1989">fx_unicode_file_create</span></span>
- <span data-ttu-id="ec793-1990">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-1990">fx_unicode_file_rename</span></span>
- <span data-ttu-id="ec793-1991">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1991">fx_unicode_name_get</span></span>
- <span data-ttu-id="ec793-1992">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-1992">fx_unicode_short_name_get</span></span>

## <a name="fx_file_read"></a><span data-ttu-id="ec793-1993">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="ec793-1993">fx_file_read</span></span>

<span data-ttu-id="ec793-1994">Считывает байты из файла</span><span class="sxs-lookup"><span data-stu-id="ec793-1994">Reads bytes from file</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-1995">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-1995">Prototype</span></span>

```c
UINT fx_file_read(
    FX_FILE *file_ptr, 
    VOID *buffer_ptr,
    ULONG request_size, 
    ULONG *actual_size);
```
### <a name="description"></a><span data-ttu-id="ec793-1996">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-1996">Description</span></span>

<span data-ttu-id="ec793-1997">Эта служба считывает байты из файла и сохраняет их в заданном буфере.</span><span class="sxs-lookup"><span data-stu-id="ec793-1997">This service reads bytes from the file and stores them in the supplied buffer.</span></span> <span data-ttu-id="ec793-1998">После завершения чтения внутренний указатель чтения файла корректируется так, чтобы он указывал на следующий байт в файле.</span><span class="sxs-lookup"><span data-stu-id="ec793-1998">After the read is complete, the file's internal read pointer is adjusted to point at the next byte in the file.</span></span> <span data-ttu-id="ec793-1999">Если в запросе осталось меньше байтов, в буфер будут сохранены только оставшиеся байты.</span><span class="sxs-lookup"><span data-stu-id="ec793-1999">If there are fewer bytes remaining in the request, only the bytes remaining are stored in the buffer.</span></span> <span data-ttu-id="ec793-2000">В любом случае общее число байтов, помещенных в буфер, возвращается вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="ec793-2000">In any case, the total number of bytes placed in the buffer is returned to the caller.</span></span>

> [!WARNING]
> <span data-ttu-id="ec793-2001">*Приложение должно гарантировать, что предоставленный буфер способен хранить указанное число запрошенных байтов.*</span><span class="sxs-lookup"><span data-stu-id="ec793-2001">*The application must ensure that the buffer supplied is able to store the specified number of requested bytes.*</span></span>

> [!WARNING]
> <span data-ttu-id="ec793-2002">*Более высокая производительность достигается тогда, когда буфер назначения находится на границе длинного слова, а запрошенный размер делится на sizeof(**ULONG**) без остатка.*</span><span class="sxs-lookup"><span data-stu-id="ec793-2002">*Faster performance is achieved if the destination buffer is on a long-word boundary and the requested size is evenly divisible by sizeof(**ULONG**).*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-2003">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-2003">Input Parameters</span></span>

- <span data-ttu-id="ec793-2004">**file_ptr**: указатель на блок управления файлом</span><span class="sxs-lookup"><span data-stu-id="ec793-2004">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="ec793-2005">**buffer_ptr**: указатель на буфер назначения для чтения</span><span class="sxs-lookup"><span data-stu-id="ec793-2005">**buffer_ptr**: Pointer to the destination buffer for the read.</span></span>
- <span data-ttu-id="ec793-2006">**request_size**: максимальное количество байтов для чтения</span><span class="sxs-lookup"><span data-stu-id="ec793-2006">**request_size**: Maximum number of bytes to read.</span></span>
- <span data-ttu-id="ec793-2007">**actual_size**: указатель на переменную для хранения фактического числа байтов, считанных в указанный буфер</span><span class="sxs-lookup"><span data-stu-id="ec793-2007">**actual_size**: Pointer to the variable to hold the actual number of bytes read into the supplied buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-2008">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-2008">Return Values</span></span>

- <span data-ttu-id="ec793-2009">**FX_SUCCESS** (0x00) — чтение из файла успешно выполнено.</span><span class="sxs-lookup"><span data-stu-id="ec793-2009">**FX_SUCCESS** (0x00) Successful file read.</span></span>
- <span data-ttu-id="ec793-2010">**FX_NOT_OPEN** (0x07) — указанный файл не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-2010">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="ec793-2011">**FX_FILE_CORRUPT** (0x08) — указанный файл поврежден,и не удалось выполнить чтение.</span><span class="sxs-lookup"><span data-stu-id="ec793-2011">**FX_FILE_CORRUPT** (0x08) Specified file is corrupt and the read failed.</span></span>
- <span data-ttu-id="ec793-2012">**FX_END_OF_FILE** (0x09) — достигнут конец файла.</span><span class="sxs-lookup"><span data-stu-id="ec793-2012">**FX_END_OF_FILE** (0x09) End of file has been reached.</span></span>
- <span data-ttu-id="ec793-2013">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-2013">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="ec793-2014">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="ec793-2014">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="ec793-2015">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-2015">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-2016">**FX_PTR_ERROR** (0x18) — недопустимый указатель на файл или буфер.</span><span class="sxs-lookup"><span data-stu-id="ec793-2016">**FX_PTR_ERROR** (0x18) Invalid file or buffer pointer.</span></span>
- <span data-ttu-id="ec793-2017">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-2017">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-2018">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-2018">Allowed From</span></span>

<span data-ttu-id="ec793-2019">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-2019">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-2020">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-2020">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="ec793-2021">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-2021">See Also</span></span>

- <span data-ttu-id="ec793-2022">fx_file_allocate,</span><span class="sxs-lookup"><span data-stu-id="ec793-2022">fx_file_allocate,</span></span>
- <span data-ttu-id="ec793-2023">fx_file_attributes_read,</span><span class="sxs-lookup"><span data-stu-id="ec793-2023">fx_file_attributes_read,</span></span>
- <span data-ttu-id="ec793-2024">fx_file_attributes_set,</span><span class="sxs-lookup"><span data-stu-id="ec793-2024">fx_file_attributes_set,</span></span>
- <span data-ttu-id="ec793-2025">fx_file_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="ec793-2025">fx_file_best_effort_allocate,</span></span>
- <span data-ttu-id="ec793-2026">fx_file_close,</span><span class="sxs-lookup"><span data-stu-id="ec793-2026">fx_file_close,</span></span>
- <span data-ttu-id="ec793-2027">fx_file_create,</span><span class="sxs-lookup"><span data-stu-id="ec793-2027">fx_file_create,</span></span>
- <span data-ttu-id="ec793-2028">fx_file_date_time_set,</span><span class="sxs-lookup"><span data-stu-id="ec793-2028">fx_file_date_time_set,</span></span>
- <span data-ttu-id="ec793-2029">fx_file_delete,</span><span class="sxs-lookup"><span data-stu-id="ec793-2029">fx_file_delete,</span></span>
- <span data-ttu-id="ec793-2030">fx_file_extended_allocate,</span><span class="sxs-lookup"><span data-stu-id="ec793-2030">fx_file_extended_allocate,</span></span>
- <span data-ttu-id="ec793-2031">fx_file_extended_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="ec793-2031">fx_file_extended_best_effort_allocate,</span></span>
- <span data-ttu-id="ec793-2032">fx_file_extended_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="ec793-2032">fx_file_extended_relative_seek,</span></span>
- <span data-ttu-id="ec793-2033">fx_file_extended_seek,</span><span class="sxs-lookup"><span data-stu-id="ec793-2033">fx_file_extended_seek,</span></span>
- <span data-ttu-id="ec793-2034">fx_file_extended_truncate,</span><span class="sxs-lookup"><span data-stu-id="ec793-2034">fx_file_extended_truncate,</span></span>
- <span data-ttu-id="ec793-2035">fx_file_extended_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="ec793-2035">fx_file_extended_truncate_release,</span></span>
- <span data-ttu-id="ec793-2036">fx_file_open,</span><span class="sxs-lookup"><span data-stu-id="ec793-2036">fx_file_open,</span></span>
- <span data-ttu-id="ec793-2037">fx_file_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="ec793-2037">fx_file_relative_seek,</span></span>
- <span data-ttu-id="ec793-2038">fx_file_rename,</span><span class="sxs-lookup"><span data-stu-id="ec793-2038">fx_file_rename,</span></span>
- <span data-ttu-id="ec793-2039">fx_file_seek,</span><span class="sxs-lookup"><span data-stu-id="ec793-2039">fx_file_seek,</span></span>
- <span data-ttu-id="ec793-2040">fx_file_truncate,</span><span class="sxs-lookup"><span data-stu-id="ec793-2040">fx_file_truncate,</span></span>
- <span data-ttu-id="ec793-2041">fx_file_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="ec793-2041">fx_file_truncate_release,</span></span>
- <span data-ttu-id="ec793-2042">fx_file_write,</span><span class="sxs-lookup"><span data-stu-id="ec793-2042">fx_file_write,</span></span>
- <span data-ttu-id="ec793-2043">fx_file_write_notify_set,</span><span class="sxs-lookup"><span data-stu-id="ec793-2043">fx_file_write_notify_set,</span></span>
- <span data-ttu-id="ec793-2044">fx_unicode_file_create,</span><span class="sxs-lookup"><span data-stu-id="ec793-2044">fx_unicode_file_create,</span></span>
- <span data-ttu-id="ec793-2045">fx_unicode_file_rename,</span><span class="sxs-lookup"><span data-stu-id="ec793-2045">fx_unicode_file_rename,</span></span>
- <span data-ttu-id="ec793-2046">fx_unicode_name_get,</span><span class="sxs-lookup"><span data-stu-id="ec793-2046">fx_unicode_name_get,</span></span>
- <span data-ttu-id="ec793-2047">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-2047">fx_unicode_short_name_get</span></span>

## <a name="fx_file_relative_seek"></a><span data-ttu-id="ec793-2048">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-2048">fx_file_relative_seek</span></span>

<span data-ttu-id="ec793-2049">Размещение на указанное относительное смещение в байтах</span><span class="sxs-lookup"><span data-stu-id="ec793-2049">Positions to a relative byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-2050">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-2050">Prototype</span></span>

```c
UINT fx_file_relative_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset,
    UINT seek_from);
```
### <a name="description"></a><span data-ttu-id="ec793-2051">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-2051">Description</span></span>

<span data-ttu-id="ec793-2052">Эта служба размещает внутренний указатель чтения/записи файла на указанное относительное смещение в байтах.</span><span class="sxs-lookup"><span data-stu-id="ec793-2052">This service positions the internal file read/write pointer to the specified relative byte offset.</span></span> <span data-ttu-id="ec793-2053">Все последующие запросы на чтение или запись файла будут начинаться с этого места в файле.</span><span class="sxs-lookup"><span data-stu-id="ec793-2053">Any subsequent file read or write request will begin at this location in the file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec793-2054">*Если операция поиска пытается выполнить поиск после конца файла, указатель на чтение и запись файла помещается в конец файла. И наоборот, если операция поиска пытается установить положение после начала файла, указатель на чтение и запись файла помещается в начало файла.*</span><span class="sxs-lookup"><span data-stu-id="ec793-2054">*If the seek operation attempts to seek past the end of the file, the file's read/write pointer is positioned to the end of the file. Conversely, if the seek operation attempts to position past the beginning of the file, the file's read/write pointer is positioned to the beginning of the file.*</span></span>

<span data-ttu-id="ec793-2055">Чтобы найти значение смещения, превышающее 4 ГБ, приложение должно использовать службу *fx_file_extended_relative_seek*.</span><span class="sxs-lookup"><span data-stu-id="ec793-2055">To seek with an offset value beyond 4GB, application shall use the service *fx_file_extended_relative_seek*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-2056">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-2056">Input Parameters</span></span>

- <span data-ttu-id="ec793-2057">**file_ptr**: указатель на открытый ранее файл</span><span class="sxs-lookup"><span data-stu-id="ec793-2057">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="ec793-2058">**byte_offset**: требуемое относительное смещение в байтах в файле</span><span class="sxs-lookup"><span data-stu-id="ec793-2058">**byte_offset**: Desired relative byte offset in file.</span></span>
- <span data-ttu-id="ec793-2059">**seek_from**: направление и расположение для выполнения относительного поиска</span><span class="sxs-lookup"><span data-stu-id="ec793-2059">**seek_from**: The direction and location of where to perform the relative seek from.</span></span> <span data-ttu-id="ec793-2060">Допустимые параметры чтения определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ec793-2060">Valid seek options are defined as follows:</span></span>
  - <span data-ttu-id="ec793-2061">FX_SEEK_BEGIN (0x00)</span><span class="sxs-lookup"><span data-stu-id="ec793-2061">FX_SEEK_BEGIN (0x00)</span></span>
  - <span data-ttu-id="ec793-2062">FX_SEEK_END (0x01)</span><span class="sxs-lookup"><span data-stu-id="ec793-2062">FX_SEEK_END (0x01)</span></span>
  - <span data-ttu-id="ec793-2063">FX_SEEK_FORWARD (0x02)</span><span class="sxs-lookup"><span data-stu-id="ec793-2063">FX_SEEK_FORWARD (0x02)</span></span>
  - <span data-ttu-id="ec793-2064">FX_SEEK_BACK (0x03)</span><span class="sxs-lookup"><span data-stu-id="ec793-2064">FX_SEEK_BACK (0x03)</span></span>

<span data-ttu-id="ec793-2065">Если указан параметр FX_SEEK_BEGIN, операция поиска выполняется с начала файла.</span><span class="sxs-lookup"><span data-stu-id="ec793-2065">If FX_SEEK_BEGIN is specified, the seek operation is performed from the beginning of the file.</span></span> <span data-ttu-id="ec793-2066">Если указан параметр FX_SEEK_END, операция поиска выполняется в обратном направлении с конца файла.</span><span class="sxs-lookup"><span data-stu-id="ec793-2066">If FX_SEEK_END is specified the seek operation is performed backward from the end of the file.</span></span> <span data-ttu-id="ec793-2067">Если указан параметр FX_SEEK_FORWARD, операция поиска выполняется вперед от текущего расположения файла.</span><span class="sxs-lookup"><span data-stu-id="ec793-2067">If FX_SEEK_FORWARD is specified, the seek operation is performed forward from the current file position.</span></span> <span data-ttu-id="ec793-2068">Если указан параметр FX_SEEK_BACK, операция поиска выполняется в обратном направлении от текущей позиции файла.</span><span class="sxs-lookup"><span data-stu-id="ec793-2068">If FX_SEEK_BACK is specified, the seek operation is performed backward from the current file position.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-2069">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-2069">Return Values</span></span>

- <span data-ttu-id="ec793-2070">**FX_SUCCESS** (0x00) — относительный поиск файла успешно выполнен.</span><span class="sxs-lookup"><span data-stu-id="ec793-2070">**FX_SUCCESS** (0x00) Successful file relative seek.</span></span>
- <span data-ttu-id="ec793-2071">**FX_NOT_OPEN** (0x07) — указанный файл в настоящее время не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-2071">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="ec793-2072">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-2072">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-2073">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-2073">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="ec793-2074">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-2074">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="ec793-2075">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-2075">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="ec793-2076">**FX_PTR_ERROR** (0x18) — недопустимый указатель на файл.</span><span class="sxs-lookup"><span data-stu-id="ec793-2076">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="ec793-2077">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-2077">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-2078">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-2078">Allowed From</span></span>

<span data-ttu-id="ec793-2079">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-2079">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-2080">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-2080">Example</span></span>

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to move 10 bytes forward in "my_file". */

status = fx_file_relative_seek(&my_file, 10, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write pointers
    are positioned 10 bytes forward. */
```

### <a name="see-also"></a><span data-ttu-id="ec793-2081">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-2081">See Also</span></span>

- <span data-ttu-id="ec793-2082">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-2082">fx_file_allocate</span></span>
- <span data-ttu-id="ec793-2083">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-2083">fx_file_attributes_read</span></span>
- <span data-ttu-id="ec793-2084">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2084">fx_file_attributes_set</span></span>
- <span data-ttu-id="ec793-2085">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-2085">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-2086">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="ec793-2086">fx_file_close</span></span>
- <span data-ttu-id="ec793-2087">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-2087">fx_file_create</span></span>
- <span data-ttu-id="ec793-2088">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2088">fx_file_date_time_set</span></span>
- <span data-ttu-id="ec793-2089">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-2089">fx_file_delete</span></span>
- <span data-ttu-id="ec793-2090">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-2090">fx_file_extended_allocate</span></span>
- <span data-ttu-id="ec793-2091">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-2091">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-2092">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-2092">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="ec793-2093">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-2093">fx_file_extended_seek</span></span>
- <span data-ttu-id="ec793-2094">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-2094">fx_file_extended_truncate</span></span>
- <span data-ttu-id="ec793-2095">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-2095">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="ec793-2096">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="ec793-2096">fx_file_open</span></span>
- <span data-ttu-id="ec793-2097">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="ec793-2097">fx_file_read</span></span>
- <span data-ttu-id="ec793-2098">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-2098">fx_file_rename</span></span>
- <span data-ttu-id="ec793-2099">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-2099">fx_file_seek</span></span>
- <span data-ttu-id="ec793-2100">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-2100">fx_file_truncate</span></span>
- <span data-ttu-id="ec793-2101">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-2101">fx_file_truncate_release</span></span>
- <span data-ttu-id="ec793-2102">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="ec793-2102">fx_file_write</span></span>
- <span data-ttu-id="ec793-2103">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2103">fx_file_write_notify_set</span></span>
- <span data-ttu-id="ec793-2104">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-2104">fx_unicode_file_create</span></span>
- <span data-ttu-id="ec793-2105">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-2105">fx_unicode_file_rename</span></span>
- <span data-ttu-id="ec793-2106">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-2106">fx_unicode_name_get</span></span>
- <span data-ttu-id="ec793-2107">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-2107">fx_unicode_short_name_get</span></span>

## <a name="fx_file_rename"></a><span data-ttu-id="ec793-2108">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-2108">fx_file_rename</span></span>

<span data-ttu-id="ec793-2109">Переименовывает файл</span><span class="sxs-lookup"><span data-stu-id="ec793-2109">Renames  file</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-2110">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-2110">Prototype</span></span>

```c
UINT fx_file_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_file_name,
    CHAR *new_file_name);
```
### <a name="description"></a><span data-ttu-id="ec793-2111">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-2111">Description</span></span>

<span data-ttu-id="ec793-2112">Эта служба изменяет имя файла, указанного параметром *old_file_name*.</span><span class="sxs-lookup"><span data-stu-id="ec793-2112">This service changes the name of the file specified by *old_file_name*.</span></span> <span data-ttu-id="ec793-2113">Переименование также выполняется относительно указанного пути или пути по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ec793-2113">Renaming is also done relative to the specified path or the default path.</span></span> <span data-ttu-id="ec793-2114">Если в новом имени файла указан путь, переименованный файл фактически перемещается по указанному пути.</span><span class="sxs-lookup"><span data-stu-id="ec793-2114">If a path is specified in the new file name, the renamed file is effectively moved to the specified path.</span></span> <span data-ttu-id="ec793-2115">Если путь не указан, переименованный файл помещается в текущий путь по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ec793-2115">If no path is specified, the renamed file is placed in the current default path.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-2116">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-2116">Input Parameters</span></span>

- <span data-ttu-id="ec793-2117">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-2117">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="ec793-2118">**old_file_name**: указатель на имя переименовываемого файла (путь к каталогу является необязательным)</span><span class="sxs-lookup"><span data-stu-id="ec793-2118">**old_file_name**: Pointer to the name of the file to rename (directory path is optional).</span></span>
- <span data-ttu-id="ec793-2119">**new_file_name**: указатель на новое имя файла</span><span class="sxs-lookup"><span data-stu-id="ec793-2119">**new_file_name**: Pointer to the new file name.</span></span> <span data-ttu-id="ec793-2120">Путь к каталогу не допускается.</span><span class="sxs-lookup"><span data-stu-id="ec793-2120">The directory path is not allowed.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-2121">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-2121">Return Values</span></span>

- <span data-ttu-id="ec793-2122">**FX_SUCCESS** (0x00) — файл успешно переименован.</span><span class="sxs-lookup"><span data-stu-id="ec793-2122">**FX_SUCCESS** (0x00) Successful file rename.</span></span>
- <span data-ttu-id="ec793-2123">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-2123">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="ec793-2124">**FX_NOT_FOUND** (0x04) — указанный файл не найден.</span><span class="sxs-lookup"><span data-stu-id="ec793-2124">**FX_NOT_FOUND** (0x04)    Specified file was not found.</span></span>
- <span data-ttu-id="ec793-2125">**FX_NOT_A_FILE** (0x05) — указанный файл является каталогом.</span><span class="sxs-lookup"><span data-stu-id="ec793-2125">**FX_NOT_A_FILE** (0x05) Specified file is a directory.</span></span>
- <span data-ttu-id="ec793-2126">**FX_ACCESS_ERROR** (0x06) — указанный файл уже открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-2126">**FX_ACCESS_ERROR** (0x06) Specified file is already open.</span></span>
- <span data-ttu-id="ec793-2127">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-2127">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-2128">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-2128">**FX_WRITE_PROTECT** (0x23)    Specified media is write protected.</span></span>
- <span data-ttu-id="ec793-2129">**FX_INVALID_NAME** (0x0C) — указанное новое имя файла не является допустимым именем файла.</span><span class="sxs-lookup"><span data-stu-id="ec793-2129">**FX_INVALID_NAME** (0x0C) Specified new file name is not a valid file name.</span></span>
- <span data-ttu-id="ec793-2130">**FX_INVALID_PATH** (0x0D) — недопустимый путь.</span><span class="sxs-lookup"><span data-stu-id="ec793-2130">**FX_INVALID_PATH** (0x0D)    Path is invalid.</span></span>
- <span data-ttu-id="ec793-2131">**FX_ALREADY_CREATED** (0x0B) — новое имя файла уже используется.</span><span class="sxs-lookup"><span data-stu-id="ec793-2131">**FX_ALREADY_CREATED** (0x0B) The new file name is used.</span></span>
- <span data-ttu-id="ec793-2132">**FX_MEDIA_INVALID** (0x02) — недопустимый носитель.</span><span class="sxs-lookup"><span data-stu-id="ec793-2132">**FX_MEDIA_INVALID** (0x02)    Media is invalid.</span></span>
- <span data-ttu-id="ec793-2133">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-2133">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="ec793-2134">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-2134">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="ec793-2135">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-2135">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="ec793-2136">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="ec793-2136">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="ec793-2137">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать таблицу FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-2137">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="ec793-2138">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-2138">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="ec793-2139">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-2139">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-2140">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-2140">Allowed From</span></span>

<span data-ttu-id="ec793-2141">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-2141">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-2142">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-2142">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;

/* Rename "myfile1.txt" to "myfile2.txt" in the default directory of the media. */

status = fx_file_rename(&my_media, "myfile1.txt", "myfile2.txt");

/* If status equals FX_SUCCESS, the file was successfully renamed. */
```

### <a name="see-also"></a><span data-ttu-id="ec793-2143">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-2143">See Also</span></span>

- <span data-ttu-id="ec793-2144">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-2144">fx_file_allocate</span></span>
- <span data-ttu-id="ec793-2145">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-2145">fx_file_attributes_read</span></span>
- <span data-ttu-id="ec793-2146">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2146">fx_file_attributes_set</span></span>
- <span data-ttu-id="ec793-2147">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-2147">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-2148">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="ec793-2148">fx_file_close</span></span>
- <span data-ttu-id="ec793-2149">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-2149">fx_file_create</span></span>
- <span data-ttu-id="ec793-2150">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2150">fx_file_date_time_set</span></span>
- <span data-ttu-id="ec793-2151">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-2151">fx_file_delete</span></span>
- <span data-ttu-id="ec793-2152">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-2152">fx_file_extended_allocate</span></span>
- <span data-ttu-id="ec793-2153">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-2153">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-2154">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-2154">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="ec793-2155">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-2155">fx_file_extended_seek</span></span>
- <span data-ttu-id="ec793-2156">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-2156">fx_file_extended_truncate</span></span>
- <span data-ttu-id="ec793-2157">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-2157">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="ec793-2158">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="ec793-2158">fx_file_open</span></span>
- <span data-ttu-id="ec793-2159">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="ec793-2159">fx_file_read</span></span>
- <span data-ttu-id="ec793-2160">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-2160">fx_file_relative_seek</span></span>
- <span data-ttu-id="ec793-2161">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-2161">fx_file_seek</span></span>
- <span data-ttu-id="ec793-2162">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-2162">fx_file_truncate</span></span>
- <span data-ttu-id="ec793-2163">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-2163">fx_file_truncate_release</span></span>
- <span data-ttu-id="ec793-2164">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="ec793-2164">fx_file_write</span></span>
- <span data-ttu-id="ec793-2165">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2165">fx_file_write_notify_set</span></span>
- <span data-ttu-id="ec793-2166">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-2166">fx_unicode_file_create</span></span>
- <span data-ttu-id="ec793-2167">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-2167">fx_unicode_file_rename</span></span>
- <span data-ttu-id="ec793-2168">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-2168">fx_unicode_name_get</span></span>
- <span data-ttu-id="ec793-2169">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-2169">fx_unicode_short_name_get</span></span>

## <a name="fx_file_seek"></a><span data-ttu-id="ec793-2170">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-2170">fx_file_seek</span></span>

<span data-ttu-id="ec793-2171">Размещение на указанное смещение в байтах</span><span class="sxs-lookup"><span data-stu-id="ec793-2171">Positions to byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-2172">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-2172">Prototype</span></span>

```c
UINT fx_file_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset);
```
### <a name="description"></a><span data-ttu-id="ec793-2173">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-2173">Description</span></span>

<span data-ttu-id="ec793-2174">Эта служба размещает внутренний указатель чтения/записи файла на указанное смещение в байтах.</span><span class="sxs-lookup"><span data-stu-id="ec793-2174">This service positions the internal file read/write pointer to the specified byte offset.</span></span> <span data-ttu-id="ec793-2175">Все последующие запросы на чтение или запись файла будут начинаться с этого места в файле.</span><span class="sxs-lookup"><span data-stu-id="ec793-2175">Any subsequent file read or write request will begin at this location in the file.</span></span>

<span data-ttu-id="ec793-2176">Чтобы найти значение смещения, превышающее 4 ГБ, приложение должно использовать службу *fx_file_extended_seek*.</span><span class="sxs-lookup"><span data-stu-id="ec793-2176">To seek with an offset value beyond 4GB, application shall use the service *fx_file_extended_seek*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-2177">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-2177">Input Parameters</span></span>

- <span data-ttu-id="ec793-2178">**file_ptr**: указатель на блок управления файлом</span><span class="sxs-lookup"><span data-stu-id="ec793-2178">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="ec793-2179">**byte_offset**: требуемое смещение в байтах в файле</span><span class="sxs-lookup"><span data-stu-id="ec793-2179">**byte_offset**: Desired byte offset in file.</span></span> <span data-ttu-id="ec793-2180">При нулевом значении указатель чтения/записи будет размещен в начале файла, а при значении, превышающем размер файла, указатель чтения/записи будет помещен в конец файла.</span><span class="sxs-lookup"><span data-stu-id="ec793-2180">A value of zero will position the read/write pointer at the beginning of the file, while a value greater than the file's size will position the read/write pointer at the end of the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-2181">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-2181">Return Values</span></span>

- <span data-ttu-id="ec793-2182">**FX_SUCCESS** (0x00) — файл успешно найден.</span><span class="sxs-lookup"><span data-stu-id="ec793-2182">**FX_SUCCESS** (0x00) Successful file seek.</span></span>
- <span data-ttu-id="ec793-2183">**FX_NOT_OPEN** (0x07) — указанный файл не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-2183">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="ec793-2184">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-2184">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-2185">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-2185">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="ec793-2186">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-2186">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="ec793-2187">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="ec793-2187">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="ec793-2188">**FX_PTR_ERROR** (0x18) — недопустимый указатель на файл.</span><span class="sxs-lookup"><span data-stu-id="ec793-2188">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="ec793-2189">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-2189">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-2190">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-2190">Allowed From</span></span>

<span data-ttu-id="ec793-2191">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-2191">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-2192">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-2192">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Seek to the beginning of "my_file." */
status = fx_file_seek(&my_file, 0);
/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned to the beginning of the file. */
```

### <a name="see-also"></a><span data-ttu-id="ec793-2193">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-2193">See Also</span></span>

- <span data-ttu-id="ec793-2194">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-2194">fx_file_allocate</span></span>
- <span data-ttu-id="ec793-2195">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-2195">fx_file_attributes_read</span></span>
- <span data-ttu-id="ec793-2196">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2196">fx_file_attributes_set</span></span>
- <span data-ttu-id="ec793-2197">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-2197">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-2198">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="ec793-2198">fx_file_close</span></span>
- <span data-ttu-id="ec793-2199">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-2199">fx_file_create</span></span>
- <span data-ttu-id="ec793-2200">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2200">fx_file_date_time_set</span></span>
- <span data-ttu-id="ec793-2201">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-2201">fx_file_delete</span></span>
- <span data-ttu-id="ec793-2202">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-2202">fx_file_extended_allocate</span></span>
- <span data-ttu-id="ec793-2203">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-2203">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-2204">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-2204">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="ec793-2205">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-2205">fx_file_extended_seek</span></span>
- <span data-ttu-id="ec793-2206">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-2206">fx_file_extended_truncate</span></span>
- <span data-ttu-id="ec793-2207">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-2207">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="ec793-2208">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="ec793-2208">fx_file_open</span></span>
- <span data-ttu-id="ec793-2209">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="ec793-2209">fx_file_read</span></span>
- <span data-ttu-id="ec793-2210">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-2210">fx_file_rename</span></span>
- <span data-ttu-id="ec793-2211">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-2211">fx_file_seek</span></span>
- <span data-ttu-id="ec793-2212">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-2212">fx_file_truncate</span></span>
- <span data-ttu-id="ec793-2213">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-2213">fx_file_truncate_release</span></span>
- <span data-ttu-id="ec793-2214">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="ec793-2214">fx_file_write</span></span>
- <span data-ttu-id="ec793-2215">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2215">fx_file_write_notify_set</span></span>
- <span data-ttu-id="ec793-2216">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-2216">fx_unicode_file_create</span></span>
- <span data-ttu-id="ec793-2217">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-2217">fx_unicode_file_rename</span></span>
- <span data-ttu-id="ec793-2218">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-2218">fx_unicode_name_get</span></span>
- <span data-ttu-id="ec793-2219">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-2219">fx_unicode_short_name_get</span></span>

## <a name="fx_file_truncate"></a><span data-ttu-id="ec793-2220">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-2220">fx_file_truncate</span></span>

<span data-ttu-id="ec793-2221">Усекает файл</span><span class="sxs-lookup"><span data-stu-id="ec793-2221">Truncates file</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-2222">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-2222">Prototype</span></span>

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```

### <a name="description"></a><span data-ttu-id="ec793-2223">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-2223">Description</span></span>

<span data-ttu-id="ec793-2224">Эта служба усекает размер файла до указанного.</span><span class="sxs-lookup"><span data-stu-id="ec793-2224">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="ec793-2225">Если указанный размер превышает фактический размер файла, эта служба не выполняет никаких действий.</span><span class="sxs-lookup"><span data-stu-id="ec793-2225">If the supplied size is greater than the actual file size, this service doesn't do anything.</span></span> <span data-ttu-id="ec793-2226">Ни один из кластеров носителя, связанных с файлом, не освобождается.</span><span class="sxs-lookup"><span data-stu-id="ec793-2226">None of the media clusters associated with the file are released.</span></span>

> [!WARNING]
> <span data-ttu-id="ec793-2227">*Проявляйте осторожность при усечении файлов, которые также могут быть открыты для одновременного чтения. Усечение файла, открытого для чтения, может привести к чтению недопустимых данных.*</span><span class="sxs-lookup"><span data-stu-id="ec793-2227">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="ec793-2228">Если размер превышает 4 ГБ, приложение должно использовать службу *fx_file_extended_truncate*.</span><span class="sxs-lookup"><span data-stu-id="ec793-2228">To operate beyond 4GB, application shall use the service *fx_file_extended_truncate*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-2229">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-2229">Input Parameters</span></span>

- <span data-ttu-id="ec793-2230">**file_ptr**: указатель на блок управления файлом</span><span class="sxs-lookup"><span data-stu-id="ec793-2230">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="ec793-2231">**size**: новый размер файла</span><span class="sxs-lookup"><span data-stu-id="ec793-2231">**size**: New file size.</span></span> <span data-ttu-id="ec793-2232">Число байтов после нового размера файла не учитывается.</span><span class="sxs-lookup"><span data-stu-id="ec793-2232">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-2233">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-2233">Return Values</span></span>

- <span data-ttu-id="ec793-2234">**FX_SUCCESS** (0x00) — файл успешно усечен.</span><span class="sxs-lookup"><span data-stu-id="ec793-2234">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="ec793-2235">**FX_NOT_OPEN** (0x07) — указанный файл не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-2235">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="ec793-2236">**FX_ACCESS_ERROR** (0x06) — указанный файл не открыт для записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-2236">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="ec793-2237">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-2237">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-2238">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-2238">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="ec793-2239">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-2239">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="ec793-2240">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-2240">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="ec793-2241">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-2241">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="ec793-2242">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="ec793-2242">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="ec793-2243">**FX_PTR_ERROR** (0x18) — недопустимый указатель на файл.</span><span class="sxs-lookup"><span data-stu-id="ec793-2243">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="ec793-2244">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-2244">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-2245">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-2245">Allowed From</span></span>

<span data-ttu-id="ec793-2246">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-2246">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-2247">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-2247">Example</span></span>

```c
FX_FILE                my_file;
UINT                status;
/* Truncate "my_file" to 100 bytes. */

status = fx_file_truncate(&my_file, 100);

/* If status equals FX_SUCCESS, "my_file" contains 100 or fewer bytes. */
```

### <a name="see-also"></a><span data-ttu-id="ec793-2248">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-2248">See Also</span></span>

- <span data-ttu-id="ec793-2249">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-2249">fx_file_allocate</span></span>
- <span data-ttu-id="ec793-2250">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-2250">fx_file_attributes_read</span></span>
- <span data-ttu-id="ec793-2251">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2251">fx_file_attributes_set</span></span>
- <span data-ttu-id="ec793-2252">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-2252">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-2253">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="ec793-2253">fx_file_close</span></span>
- <span data-ttu-id="ec793-2254">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-2254">fx_file_create</span></span>
- <span data-ttu-id="ec793-2255">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2255">fx_file_date_time_set</span></span>
- <span data-ttu-id="ec793-2256">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-2256">fx_file_delete</span></span>
- <span data-ttu-id="ec793-2257">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-2257">fx_file_extended_allocate</span></span>
- <span data-ttu-id="ec793-2258">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-2258">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-2259">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-2259">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="ec793-2260">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-2260">fx_file_extended_seek</span></span>
- <span data-ttu-id="ec793-2261">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-2261">fx_file_extended_truncate</span></span>
- <span data-ttu-id="ec793-2262">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-2262">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="ec793-2263">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="ec793-2263">fx_file_open</span></span>
- <span data-ttu-id="ec793-2264">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="ec793-2264">fx_file_read</span></span>
- <span data-ttu-id="ec793-2265">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-2265">fx_file_relative_seek</span></span>
- <span data-ttu-id="ec793-2266">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-2266">fx_file_rename</span></span>
- <span data-ttu-id="ec793-2267">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-2267">fx_file_seek</span></span>
- <span data-ttu-id="ec793-2268">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-2268">fx_file_truncate_release</span></span>
- <span data-ttu-id="ec793-2269">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="ec793-2269">fx_file_write</span></span>
- <span data-ttu-id="ec793-2270">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2270">fx_file_write_notify_set</span></span>
- <span data-ttu-id="ec793-2271">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-2271">fx_unicode_file_create</span></span>
- <span data-ttu-id="ec793-2272">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-2272">fx_unicode_file_rename</span></span>
- <span data-ttu-id="ec793-2273">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-2273">fx_unicode_name_get</span></span>
- <span data-ttu-id="ec793-2274">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-2274">fx_unicode_short_name_get</span></span>

## <a name="fx_file_truncate_release"></a><span data-ttu-id="ec793-2275">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-2275">fx_file_truncate_release</span></span>

<span data-ttu-id="ec793-2276">Усекает кластеры файлов и выпусков</span><span class="sxs-lookup"><span data-stu-id="ec793-2276">Truncates file and releases cluster(s)</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-2277">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-2277">Prototype</span></span>

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```
### <a name="description"></a><span data-ttu-id="ec793-2278">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-2278">Description</span></span>

<span data-ttu-id="ec793-2279">Эта служба усекает размер файла до указанного.</span><span class="sxs-lookup"><span data-stu-id="ec793-2279">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="ec793-2280">Если указанный размер превышает фактический размер файла, эта служба не выполняет никаких действий.</span><span class="sxs-lookup"><span data-stu-id="ec793-2280">If the supplied size is greater than the actual file size, this service does not do anything.</span></span> <span data-ttu-id="ec793-2281">В отличие от службы ***fx_file_truncate*** эта служба освобождает неиспользуемые кластеры.</span><span class="sxs-lookup"><span data-stu-id="ec793-2281">Unlike the ***fx_file_truncate*** service, this service does release any unused clusters.</span></span>

> [!WARNING]
> <span data-ttu-id="ec793-2282">*Проявляйте осторожность при усечении файлов, которые также могут быть открыты для одновременного чтения. Усечение файла, открытого для чтения, может привести к чтению недопустимых данных.*</span><span class="sxs-lookup"><span data-stu-id="ec793-2282">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="ec793-2283">Если размер превышает 4 ГБ, приложение должно использовать службу *fx_file_extended_truncate_release*.</span><span class="sxs-lookup"><span data-stu-id="ec793-2283">To operate beyond 4GB, application shall use the service *fx_file_extended_truncate_release*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-2284">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-2284">Input Parameters</span></span>

- <span data-ttu-id="ec793-2285">**file_ptr**: указатель на открытый ранее файл</span><span class="sxs-lookup"><span data-stu-id="ec793-2285">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="ec793-2286">**size**: новый размер файла</span><span class="sxs-lookup"><span data-stu-id="ec793-2286">**size**: New file size.</span></span> <span data-ttu-id="ec793-2287">Число байтов после нового размера файла не учитывается.</span><span class="sxs-lookup"><span data-stu-id="ec793-2287">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-2288">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-2288">Return Values</span></span>

- <span data-ttu-id="ec793-2289">**FX_SUCCESS** (0x00) — файл успешно усечен.</span><span class="sxs-lookup"><span data-stu-id="ec793-2289">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="ec793-2290">**FX_ACCESS_ERROR** (0x06) — указанный файл не открыт для записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-2290">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="ec793-2291">**FX_NOT_OPEN** (0x07) — указанный файл в настоящее время не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-2291">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="ec793-2292">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-2292">**FX_IO_ERROR** (0x90)    Driver I/O error.</span></span>
- <span data-ttu-id="ec793-2293">**FX_WRITE_PROTECT** (0x23) — носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-2293">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="ec793-2294">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-2294">**FX_FILE_CORRUPT** (0x08)    File is corrupted.</span></span>
- <span data-ttu-id="ec793-2295">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-2295">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="ec793-2296">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-2296">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="ec793-2297">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-2297">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="ec793-2298">**FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="ec793-2298">**FX_NO_MORE_SPACE** (0x0A)    No more space to complete the operation.</span></span>
- <span data-ttu-id="ec793-2299">**FX_PTR_ERROR** (0x18) — недопустимый указатель на файл.</span><span class="sxs-lookup"><span data-stu-id="ec793-2299">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="ec793-2300">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-2300">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-2301">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-2301">Allowed From</span></span>

<span data-ttu-id="ec793-2302">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-2302">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-2303">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-2303">Example</span></span>

```c
FX_FILE         my_file;
UINT             status;

/* Attempt to truncate everything after the first 100 bytes of "my_file". */

status = fx_file_truncate_release(&my_file, 100);

/* If status equals FX_SUCCESS, the file is now 100 bytes
    or fewer and all unused clusters have been released. */
```
### <a name="see-also"></a><span data-ttu-id="ec793-2304">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-2304">See Also</span></span>

- <span data-ttu-id="ec793-2305">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-2305">fx_file_allocate</span></span>
- <span data-ttu-id="ec793-2306">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-2306">fx_file_attributes_read</span></span>
- <span data-ttu-id="ec793-2307">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2307">fx_file_attributes_set</span></span>
- <span data-ttu-id="ec793-2308">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-2308">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-2309">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="ec793-2309">fx_file_close</span></span>
- <span data-ttu-id="ec793-2310">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-2310">fx_file_create</span></span>
- <span data-ttu-id="ec793-2311">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2311">fx_file_date_time_set</span></span>
- <span data-ttu-id="ec793-2312">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-2312">fx_file_delete</span></span>
- <span data-ttu-id="ec793-2313">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-2313">fx_file_extended_allocate</span></span>
- <span data-ttu-id="ec793-2314">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-2314">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-2315">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-2315">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="ec793-2316">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-2316">fx_file_extended_seek</span></span>
- <span data-ttu-id="ec793-2317">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-2317">fx_file_extended_truncate</span></span>
- <span data-ttu-id="ec793-2318">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-2318">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="ec793-2319">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="ec793-2319">fx_file_open</span></span>
- <span data-ttu-id="ec793-2320">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="ec793-2320">fx_file_read</span></span>
- <span data-ttu-id="ec793-2321">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-2321">fx_file_relative_seek</span></span>
- <span data-ttu-id="ec793-2322">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-2322">fx_file_rename</span></span>
- <span data-ttu-id="ec793-2323">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-2323">fx_file_seek</span></span>
- <span data-ttu-id="ec793-2324">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-2324">fx_file_truncate</span></span>
- <span data-ttu-id="ec793-2325">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="ec793-2325">fx_file_write</span></span>
- <span data-ttu-id="ec793-2326">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2326">fx_file_write_notify_set</span></span>
- <span data-ttu-id="ec793-2327">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-2327">fx_unicode_file_create</span></span>
- <span data-ttu-id="ec793-2328">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-2328">fx_unicode_file_rename</span></span>
- <span data-ttu-id="ec793-2329">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-2329">fx_unicode_name_get</span></span>
- <span data-ttu-id="ec793-2330">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-2330">fx_unicode_short_name_get</span></span>

## <a name="fx_file_write"></a><span data-ttu-id="ec793-2331">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="ec793-2331">fx_file_write</span></span>

<span data-ttu-id="ec793-2332">Записывает байты в файл</span><span class="sxs-lookup"><span data-stu-id="ec793-2332">Writes bytes to file</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-2333">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-2333">Prototype</span></span>

```c
UINT fx_file_write(
    FX_FILE *file_ptr,
    VOID *buffer_ptr,
    ULONG size);
```
### <a name="description"></a><span data-ttu-id="ec793-2334">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-2334">Description</span></span>

<span data-ttu-id="ec793-2335">Эта служба записывает байты из указанного буфера, начиная с текущей позиции файла.</span><span class="sxs-lookup"><span data-stu-id="ec793-2335">This service writes bytes from the specified buffer starting at the file's current position.</span></span> <span data-ttu-id="ec793-2336">После завершения записи внутренний указатель чтения файла корректируется так, чтобы он указывал на следующий байт в файле.</span><span class="sxs-lookup"><span data-stu-id="ec793-2336">After the write is complete, the file's internal read pointer is adjusted to point at the next byte in the file.</span></span>

> [!WARNING]
> <span data-ttu-id="ec793-2337">*Более высокая производительность достигается тогда, когда исходный буфер находится на границе длинного слова, а запрошенный размер делится на sizeof(**ULONG**) без остатка.*</span><span class="sxs-lookup"><span data-stu-id="ec793-2337">*Faster performance is achieved if the source buffer is on a long-word boundary and the requested size is evenly divisible by sizeof(**ULONG**).*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-2338">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-2338">Input Parameters</span></span>

- <span data-ttu-id="ec793-2339">**file_ptr**: указатель на блок управления файлом</span><span class="sxs-lookup"><span data-stu-id="ec793-2339">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="ec793-2340">**buffer_ptr**: указатель на исходный буфер для записи</span><span class="sxs-lookup"><span data-stu-id="ec793-2340">**buffer_ptr**: Pointer to the source buffer for the write.</span></span>
- <span data-ttu-id="ec793-2341">**size**: количество байтов для записи</span><span class="sxs-lookup"><span data-stu-id="ec793-2341">**size**: Number of bytes to write.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-2342">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-2342">Return Values</span></span>

- <span data-ttu-id="ec793-2343">**FX_SUCCESS** (0x00) — запись в файл успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="ec793-2343">**FX_SUCCESS** (0x00) Successful file write.</span></span>
- <span data-ttu-id="ec793-2344">**FX_NOT_OPEN** (0x07) — указанный файл не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-2344">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="ec793-2345">**FX_ACCESS_ERROR** (0x06) — указанный файл не открыт для записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-2345">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="ec793-2346">**FX_NO_MORE_SPACE** (0x0A) — недостаточно места на носителе для выполнения этой операции записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-2346">**FX_NO_MORE_SPACE** (0x0A) There is no more room available in the media to perform this write.</span></span>
- <span data-ttu-id="ec793-2347">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-2347">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-2348">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-2348">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="ec793-2349">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-2349">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="ec793-2350">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-2350">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="ec793-2351">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-2351">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="ec793-2352">**FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-2352">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="ec793-2353">**FX_PTR_ERROR** (0x18) — недопустимый указатель на файл или буфер.</span><span class="sxs-lookup"><span data-stu-id="ec793-2353">**FX_PTR_ERROR** (0x18) Invalid file or buffer pointer.</span></span>
- <span data-ttu-id="ec793-2354">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-2354">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-2355">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-2355">Allowed From</span></span>

<span data-ttu-id="ec793-2356">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-2356">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-2357">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-2357">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Write a 10 character buffer to "my_file." */

status = fx_file_write(&my_file, "1234567890", 10);

/* If status equals FX_SUCCESS, the small text string was written out to the file. */
```

### <a name="see-also"></a><span data-ttu-id="ec793-2358">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-2358">See Also</span></span>

- <span data-ttu-id="ec793-2359">fx_file_allocate,</span><span class="sxs-lookup"><span data-stu-id="ec793-2359">fx_file_allocate,</span></span>
- <span data-ttu-id="ec793-2360">fx_file_attributes_read,</span><span class="sxs-lookup"><span data-stu-id="ec793-2360">fx_file_attributes_read,</span></span>
- <span data-ttu-id="ec793-2361">fx_file_attributes_set,</span><span class="sxs-lookup"><span data-stu-id="ec793-2361">fx_file_attributes_set,</span></span>
- <span data-ttu-id="ec793-2362">fx_file_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="ec793-2362">fx_file_best_effort_allocate,</span></span>
- <span data-ttu-id="ec793-2363">fx_file_close,</span><span class="sxs-lookup"><span data-stu-id="ec793-2363">fx_file_close,</span></span>
- <span data-ttu-id="ec793-2364">fx_file_create,</span><span class="sxs-lookup"><span data-stu-id="ec793-2364">fx_file_create,</span></span>
- <span data-ttu-id="ec793-2365">fx_file_date_time_set,</span><span class="sxs-lookup"><span data-stu-id="ec793-2365">fx_file_date_time_set,</span></span>
- <span data-ttu-id="ec793-2366">fx_file_delete,</span><span class="sxs-lookup"><span data-stu-id="ec793-2366">fx_file_delete,</span></span>
- <span data-ttu-id="ec793-2367">fx_file_extended_allocate,</span><span class="sxs-lookup"><span data-stu-id="ec793-2367">fx_file_extended_allocate,</span></span>
- <span data-ttu-id="ec793-2368">fx_file_extended_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="ec793-2368">fx_file_extended_best_effort_allocate,</span></span>
- <span data-ttu-id="ec793-2369">fx_file_extended_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="ec793-2369">fx_file_extended_relative_seek,</span></span>
- <span data-ttu-id="ec793-2370">fx_file_extended_seek,</span><span class="sxs-lookup"><span data-stu-id="ec793-2370">fx_file_extended_seek,</span></span>
- <span data-ttu-id="ec793-2371">fx_file_extended_truncate,</span><span class="sxs-lookup"><span data-stu-id="ec793-2371">fx_file_extended_truncate,</span></span>
- <span data-ttu-id="ec793-2372">fx_file_extended_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="ec793-2372">fx_file_extended_truncate_release,</span></span>
- <span data-ttu-id="ec793-2373">fx_file_open,</span><span class="sxs-lookup"><span data-stu-id="ec793-2373">fx_file_open,</span></span>
- <span data-ttu-id="ec793-2374">fx_file_read,</span><span class="sxs-lookup"><span data-stu-id="ec793-2374">fx_file_read,</span></span>
- <span data-ttu-id="ec793-2375">fx_file_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="ec793-2375">fx_file_relative_seek,</span></span>
- <span data-ttu-id="ec793-2376">fx_file_rename,</span><span class="sxs-lookup"><span data-stu-id="ec793-2376">fx_file_rename,</span></span>
- <span data-ttu-id="ec793-2377">fx_file_seek,</span><span class="sxs-lookup"><span data-stu-id="ec793-2377">fx_file_seek,</span></span>
- <span data-ttu-id="ec793-2378">fx_file_truncate,</span><span class="sxs-lookup"><span data-stu-id="ec793-2378">fx_file_truncate,</span></span>
- <span data-ttu-id="ec793-2379">fx_file_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="ec793-2379">fx_file_truncate_release,</span></span>
- <span data-ttu-id="ec793-2380">fx_file_write_notify_set,</span><span class="sxs-lookup"><span data-stu-id="ec793-2380">fx_file_write_notify_set,</span></span>
- <span data-ttu-id="ec793-2381">fx_unicode_file_create,</span><span class="sxs-lookup"><span data-stu-id="ec793-2381">fx_unicode_file_create,</span></span>
- <span data-ttu-id="ec793-2382">fx_unicode_file_rename,</span><span class="sxs-lookup"><span data-stu-id="ec793-2382">fx_unicode_file_rename,</span></span>
- <span data-ttu-id="ec793-2383">fx_unicode_name_get,</span><span class="sxs-lookup"><span data-stu-id="ec793-2383">fx_unicode_name_get,</span></span>
- <span data-ttu-id="ec793-2384">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-2384">fx_unicode_short_name_get</span></span>

## <a name="fx_file_write_notify_set"></a><span data-ttu-id="ec793-2385">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2385">fx_file_write_notify_set</span></span>

<span data-ttu-id="ec793-2386">Задает функцию уведомления о записи в файл</span><span class="sxs-lookup"><span data-stu-id="ec793-2386">Sets the file write notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-2387">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-2387">Prototype</span></span>

```c
UINT fx_file_write_notify_set(
    FX_FILE *file_ptr,
    VOID (*file_write_notify)(FX_FILE*));
```
### <a name="description"></a><span data-ttu-id="ec793-2388">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-2388">Description</span></span>

<span data-ttu-id="ec793-2389">Эта служба устанавливает функцию обратного вызова, которая вызывается после успешной операции записи в файл.</span><span class="sxs-lookup"><span data-stu-id="ec793-2389">This service installs callback function that is invoked after a successful file write operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-2390">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-2390">Input Parameters</span></span>

- <span data-ttu-id="ec793-2391">**file_ptr**: указатель на блок управления файлом</span><span class="sxs-lookup"><span data-stu-id="ec793-2391">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="ec793-2392">**file_write_notify**: устанавливаемая функция обратного вызова записи в файл</span><span class="sxs-lookup"><span data-stu-id="ec793-2392">**file_write_notify**: File write callback function to be installed.</span></span> <span data-ttu-id="ec793-2393">Задайте для функции обратного вызова значение NULL, чтобы отключить функцию обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="ec793-2393">Set the callback function to NULL disables the callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-2394">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-2394">Return Values</span></span>

- <span data-ttu-id="ec793-2395">**FX_SUCCESS** (0x00) — функция обратного вызова успешно установлена.</span><span class="sxs-lookup"><span data-stu-id="ec793-2395">**FX_SUCCESS** (0x00) Successfully installed the callback function.</span></span>
- <span data-ttu-id="ec793-2396">**FX_PTR_ERROR** (0x18) — file_ptr имеет значение NULL.</span><span class="sxs-lookup"><span data-stu-id="ec793-2396">**FX_PTR_ERROR** (0x18) file_ptr is NULL.</span></span>
- <span data-ttu-id="ec793-2397">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-2397">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-2398">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-2398">Allowed From</span></span>

<span data-ttu-id="ec793-2399">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-2399">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-2400">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-2400">Example</span></span>

```c
fx_file_write_notify_set(file_ptr, my_file_close_callback);

```

### <a name="see-also"></a><span data-ttu-id="ec793-2401">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-2401">See Also</span></span>

- <span data-ttu-id="ec793-2402">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-2402">fx_file_allocate</span></span>
- <span data-ttu-id="ec793-2403">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-2403">fx_file_attributes_read</span></span>
- <span data-ttu-id="ec793-2404">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2404">fx_file_attributes_set</span></span>
- <span data-ttu-id="ec793-2405">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-2405">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-2406">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="ec793-2406">fx_file_close</span></span>
- <span data-ttu-id="ec793-2407">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-2407">fx_file_create</span></span>
- <span data-ttu-id="ec793-2408">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2408">fx_file_date_time_set</span></span>
- <span data-ttu-id="ec793-2409">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-2409">fx_file_delete</span></span>
- <span data-ttu-id="ec793-2410">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-2410">fx_file_extended_allocate</span></span>
- <span data-ttu-id="ec793-2411">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-2411">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-2412">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-2412">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="ec793-2413">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-2413">fx_file_extended_seek</span></span>
- <span data-ttu-id="ec793-2414">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-2414">fx_file_extended_truncate</span></span>
- <span data-ttu-id="ec793-2415">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-2415">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="ec793-2416">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="ec793-2416">fx_file_open</span></span>
- <span data-ttu-id="ec793-2417">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="ec793-2417">fx_file_read</span></span>
- <span data-ttu-id="ec793-2418">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-2418">fx_file_relative_seek</span></span>
- <span data-ttu-id="ec793-2419">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-2419">fx_file_rename</span></span>
- <span data-ttu-id="ec793-2420">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-2420">fx_file_seek</span></span>
- <span data-ttu-id="ec793-2421">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-2421">fx_file_truncate</span></span>
- <span data-ttu-id="ec793-2422">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-2422">fx_file_truncate_release</span></span>
- <span data-ttu-id="ec793-2423">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="ec793-2423">fx_file_write</span></span>
- <span data-ttu-id="ec793-2424">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-2424">fx_unicode_file_create</span></span>
- <span data-ttu-id="ec793-2425">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-2425">fx_unicode_file_rename</span></span>
- <span data-ttu-id="ec793-2426">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-2426">fx_unicode_name_get</span></span>
- <span data-ttu-id="ec793-2427">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-2427">fx_unicode_short_name_get</span></span>

## <a name="fx_media_abort"></a><span data-ttu-id="ec793-2428">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="ec793-2428">fx_media_abort</span></span>

<span data-ttu-id="ec793-2429">Прерывает действия носителя</span><span class="sxs-lookup"><span data-stu-id="ec793-2429">Aborts media activities</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-2430">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-2430">Prototype</span></span>

```c
UINT fx_media_abort(FX_MEDIA *media_ptr);
```
### <a name="description"></a><span data-ttu-id="ec793-2431">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-2431">Description</span></span>

<span data-ttu-id="ec793-2432">Эта служба прерывает все текущие действия, связанные с носителем, включая закрытие всех открытых файлов, отправку запроса на прерывание соответствующему драйверу и помещение носителя в состояние прерванной работы.</span><span class="sxs-lookup"><span data-stu-id="ec793-2432">This service aborts all current activities associated with the media, including closing all open files, sending an abort request to the associated driver, and placing the media in an aborted state.</span></span> <span data-ttu-id="ec793-2433">Эта служба обычно вызывается при обнаружении ошибок ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="ec793-2433">This service is typically called when I/O errors are detected.</span></span>

> [!WARNING]
> <span data-ttu-id="ec793-2434">*Чтобы повторно использовать носитель после выполнения операции прерывания, его необходимо открыть повторно.*</span><span class="sxs-lookup"><span data-stu-id="ec793-2434">*The media must be re-opened to use it again after an abort operation is performed.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-2435">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-2435">Input Parameters</span></span>

- <span data-ttu-id="ec793-2436">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-2436">**media_ptr**: Pointer to media control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-2437">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-2437">Return Values</span></span>

- <span data-ttu-id="ec793-2438">**FX_SUCCESS** (0x00) — работа носителя успешно прервана.</span><span class="sxs-lookup"><span data-stu-id="ec793-2438">**FX_SUCCESS** (0x00) Successful media abort.</span></span>
- <span data-ttu-id="ec793-2439">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-2439">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="ec793-2440">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-2440">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="ec793-2441">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-2441">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-2442">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-2442">Allowed From</span></span>

<span data-ttu-id="ec793-2443">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-2443">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-2444">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-2444">Example</span></span>

```c
FX_MEDIA    my_media;
UINT        status;
/* Abort all activity associated with "my_media". */

status = fx_media_abort(&my_media);

/* If status equals FX_SUCCESS, all activity
    associated with the media has been aborted. */

```

### <a name="see-also"></a><span data-ttu-id="ec793-2445">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-2445">See Also</span></span>

- <span data-ttu-id="ec793-2446">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="ec793-2446">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="ec793-2447">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="ec793-2447">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="ec793-2448">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="ec793-2448">fx_media_check</span></span>
- <span data-ttu-id="ec793-2449">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="ec793-2449">fx_media_close</span></span>
- <span data-ttu-id="ec793-2450">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2450">fx_media_close_notify_set</span></span>
- <span data-ttu-id="ec793-2451">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="ec793-2451">fx_media_exFAT_format</span></span>
- <span data-ttu-id="ec793-2452">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-2452">fx_media_extended_space_available</span></span>
- <span data-ttu-id="ec793-2453">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="ec793-2453">fx_media_flush</span></span>
- <span data-ttu-id="ec793-2454">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="ec793-2454">fx_media_format</span></span>
- <span data-ttu-id="ec793-2455">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="ec793-2455">fx_media_open</span></span>
- <span data-ttu-id="ec793-2456">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2456">fx_media_open_notify_set</span></span>
- <span data-ttu-id="ec793-2457">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="ec793-2457">fx_media_read</span></span>
- <span data-ttu-id="ec793-2458">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-2458">fx_media_space_available</span></span>
- <span data-ttu-id="ec793-2459">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="ec793-2459">fx_media_volume_get</span></span>
- <span data-ttu-id="ec793-2460">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2460">fx_media_volume_set</span></span>
- <span data-ttu-id="ec793-2461">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="ec793-2461">fx_media_write</span></span>
- <span data-ttu-id="ec793-2462">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ec793-2462">fx_system_initialize</span></span>

## <a name="fx_media_cache_invalidate"></a><span data-ttu-id="ec793-2463">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="ec793-2463">fx_media_cache_invalidate</span></span>

<span data-ttu-id="ec793-2464">Делает недействительным кэш логического сектора</span><span class="sxs-lookup"><span data-stu-id="ec793-2464">Invalidates logical sector cache</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-2465">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-2465">Prototype</span></span>

```c
UINT fx_media_cache_invalidate(FX_MEDIA *media_ptr);
```

### <a name="description"></a><span data-ttu-id="ec793-2466">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-2466">Description</span></span>

<span data-ttu-id="ec793-2467">Эта служба очищает все "грязные" секторы в кэше, а затем делает недействительным весь кэш логического сектора.</span><span class="sxs-lookup"><span data-stu-id="ec793-2467">This service flushes all dirty sectors in the cache and then invalidates the entire logical sector cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-2468">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-2468">Input Parameters</span></span>

- <span data-ttu-id="ec793-2469">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-2469">**media_ptr**: Pointer to media control block</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-2470">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-2470">Return Values</span></span>

- <span data-ttu-id="ec793-2471">**FX_SUCCESS** (0x00) — кэш носителя успешно сделан недействительным.</span><span class="sxs-lookup"><span data-stu-id="ec793-2471">**FX_SUCCESS** (0x00) Successful media cache invalidate.</span></span>
- <span data-ttu-id="ec793-2472">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-2472">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="ec793-2473">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-2473">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-2474">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или временной памяти.</span><span class="sxs-lookup"><span data-stu-id="ec793-2474">**FX_PTR_ERROR** (0x18) Invalid media or scratch pointer.</span></span>
- <span data-ttu-id="ec793-2475">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-2475">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-2476">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-2476">Allowed From</span></span>

<span data-ttu-id="ec793-2477">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-2477">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-2478">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-2478">Example</span></span>

```c
FX_MEDIA     my_media;

/* Invalidate the cache of the media. */
status = fx_media_cache_invalidate(&my_media);

/* If status is FX_SUCCESS the cache in the media
    was successfully flushed and invalidated. */

```

### <a name="see-also"></a><span data-ttu-id="ec793-2479">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-2479">See Also</span></span>

- <span data-ttu-id="ec793-2480">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="ec793-2480">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="ec793-2481">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="ec793-2481">fx_media_abort</span></span>
- <span data-ttu-id="ec793-2482">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="ec793-2482">fx_media_check</span></span>
- <span data-ttu-id="ec793-2483">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="ec793-2483">fx_media_close</span></span>
- <span data-ttu-id="ec793-2484">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2484">fx_media_close_notify_set</span></span>
- <span data-ttu-id="ec793-2485">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="ec793-2485">fx_media_exFAT_format</span></span>
- <span data-ttu-id="ec793-2486">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-2486">fx_media_extended_space_available</span></span>
- <span data-ttu-id="ec793-2487">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="ec793-2487">fx_media_flush</span></span>
- <span data-ttu-id="ec793-2488">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="ec793-2488">fx_media_format</span></span>
- <span data-ttu-id="ec793-2489">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="ec793-2489">fx_media_open</span></span>
- <span data-ttu-id="ec793-2490">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2490">fx_media_open_notify_set</span></span>
- <span data-ttu-id="ec793-2491">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="ec793-2491">fx_media_read</span></span>
- <span data-ttu-id="ec793-2492">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-2492">fx_media_space_available</span></span>
- <span data-ttu-id="ec793-2493">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="ec793-2493">fx_media_volume_get</span></span>
- <span data-ttu-id="ec793-2494">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2494">fx_media_volume_set</span></span>
- <span data-ttu-id="ec793-2495">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="ec793-2495">fx_media_write</span></span>
- <span data-ttu-id="ec793-2496">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ec793-2496">fx_system_initialize</span></span>

## <a name="fx_media_check"></a><span data-ttu-id="ec793-2497">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="ec793-2497">fx_media_check</span></span>

<span data-ttu-id="ec793-2498">Проверяет наличие ошибок на носителе</span><span class="sxs-lookup"><span data-stu-id="ec793-2498">Checks media for errors</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-2499">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-2499">Prototype</span></span>

```c
UINT fx_media_check(
    FX_MEDIA *media_ptr,
    UCHAR *scratch_memory_ptr,
    ULONG scratch_memory_size,
    ULONG error_correction_option,
    ULONG *errors_detected_ptr);
```
### <a name="description"></a><span data-ttu-id="ec793-2500">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-2500">Description</span></span>

<span data-ttu-id="ec793-2501">Эта служба проверяет указанный носитель на наличие базовых структурных ошибок, включая перекрестные ссылки на файлы и каталоги, недопустимые цепочки FAT и потерянные кластеры.</span><span class="sxs-lookup"><span data-stu-id="ec793-2501">This service checks the specified media for basic structural errors, including file/directory cross-linking, invalid FAT chains, and lost clusters.</span></span> <span data-ttu-id="ec793-2502">Эта служба также предоставляет возможность исправить обнаруженные ошибки.</span><span class="sxs-lookup"><span data-stu-id="ec793-2502">This service also provides the capability to correct detected errors.</span></span>

<span data-ttu-id="ec793-2503">Служба fx_media_check требует наличия вспомогательной памяти для предварительного анализа глубины вложения каталогов и файлов на носителе.</span><span class="sxs-lookup"><span data-stu-id="ec793-2503">The fx_media_check service requires scratch memory for its depth-first analysis of directories and files in the media.</span></span> <span data-ttu-id="ec793-2504">В частности, вспомогательная память, предоставленная службе проверки носителей, должна быть достаточно большой для хранения нескольких записей каталога, структуры данных для помещения в стек текущей позиции записи каталога перед входом в подкаталоги и, наконец, логической битовой карты FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-2504">Specifically, the scratch memory supplied to the media check service must be large enough to hold several directory entries, a data structure to "stack" the current directory entry position before entering into subdirectories, and finally the logical FAT bit map.</span></span> <span data-ttu-id="ec793-2505">Объем вспомогательной памяти должен составлять по крайней мере 512–1024 байт плюс память для логической файловой системы FAT, для которой требуется столько битов, сколько кластеров находится в носителе.</span><span class="sxs-lookup"><span data-stu-id="ec793-2505">The scratch memory should be at least 512-1024 bytes plus memory for the logical FAT bit map, which requires as many bits as there are clusters in the media.</span></span> <span data-ttu-id="ec793-2506">Например, устройству с 8000 кластерам потребовалось бы 1000 байт для представления и, таким образом, требуемый размер общей временной области составляет порядка 2048 байт.</span><span class="sxs-lookup"><span data-stu-id="ec793-2506">For example, a device with 8000 clusters would require 1000 bytes to represent and thus require a total scratch area on the order of 2048 bytes.</span></span>

> [!WARNING]
> <span data-ttu-id="ec793-2507">*Эту службу следует вызывать только сразу после fx_media_open и без каких бы то ни было других действий с файловой системой.*</span><span class="sxs-lookup"><span data-stu-id="ec793-2507">*This service should only be called immediately after fx_media_open and without any other file system activity.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-2508">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-2508">Input Parameters</span></span>

- <span data-ttu-id="ec793-2509">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-2509">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="ec793-2510">**scratch_memory_ptr**: указатель на начало вспомогательной памяти</span><span class="sxs-lookup"><span data-stu-id="ec793-2510">**scratch_memory_ptr**: Pointer to the start of scratch memory.</span></span>
- <span data-ttu-id="ec793-2511">**scratch_memory_size**: размер вспомогательной памяти в байтах</span><span class="sxs-lookup"><span data-stu-id="ec793-2511">**scratch_memory_size**: Size of scratch memory in bytes.</span></span>
- <span data-ttu-id="ec793-2512">**error_correction_option**: биты при исправлении ошибок, если бит задан, выполняется исправление ошибок</span><span class="sxs-lookup"><span data-stu-id="ec793-2512">**error_correction_option**: Error correction option bits, when the bit is set, error correction is performed.</span></span> <span data-ttu-id="ec793-2513">Биты параметра исправления ошибок определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ec793-2513">The error correction option bits are defined as follows:</span></span>
  - <span data-ttu-id="ec793-2514">FX_FAT_CHAIN_ERROR (0x01)</span><span class="sxs-lookup"><span data-stu-id="ec793-2514">FX_FAT_CHAIN_ERROR (0x01)</span></span>
  - <span data-ttu-id="ec793-2515">FX_DIRECTORY_ERROR (0x02)</span><span class="sxs-lookup"><span data-stu-id="ec793-2515">FX_DIRECTORY_ERROR (0x02)</span></span>
  - <span data-ttu-id="ec793-2516">FX_LOST_CLUSTER_ERROR (0x04): просто ИЛИ вместе с необходимыми параметрами исправления ошибок</span><span class="sxs-lookup"><span data-stu-id="ec793-2516">FX_LOST_CLUSTER_ERROR (0x04) Simply OR together the required error correction options.</span></span> <span data-ttu-id="ec793-2517">Если исправление ошибок не требуется, необходимо указать значение 0.</span><span class="sxs-lookup"><span data-stu-id="ec793-2517">If no error correction is required, a value of 0 should be supplied.</span></span>
- <span data-ttu-id="ec793-2518">**errors_detected_ptr**: назначение для битов обнаружения ошибок, как определено ниже.</span><span class="sxs-lookup"><span data-stu-id="ec793-2518">**errors_detected_ptr**: Destination for error detection bits, as defined below:</span></span>
  - <span data-ttu-id="ec793-2519">FX_FAT_CHAIN_ERROR (0x01)</span><span class="sxs-lookup"><span data-stu-id="ec793-2519">FX_FAT_CHAIN_ERROR (0x01)</span></span>
  - <span data-ttu-id="ec793-2520">FX_DIRECTORY_ERROR (0x02) FX_LOST_CLUSTER_ERROR (0x04)</span><span class="sxs-lookup"><span data-stu-id="ec793-2520">FX_DIRECTORY_ERROR (0x02) FX_LOST_CLUSTER_ERROR (0x04)</span></span>
  - <span data-ttu-id="ec793-2521">FX_FILE_SIZE_ERROR (0x08)</span><span class="sxs-lookup"><span data-stu-id="ec793-2521">FX_FILE_SIZE_ERROR (0x08)</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-2522">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-2522">Return Values</span></span>

- <span data-ttu-id="ec793-2523">**FX_SUCCESS** (0x00) — носитель успешно проверен; ознакомьтесь со сведениями об обнаруженных ошибках.</span><span class="sxs-lookup"><span data-stu-id="ec793-2523">**FX_SUCCESS** (0x00) Successful media check, view the errors detected destination for details.</span></span>
- <span data-ttu-id="ec793-2524">**FX_ACCESS_ERROR** (0x06) — не удается выполнить проверку с открытыми файлами.</span><span class="sxs-lookup"><span data-stu-id="ec793-2524">**FX_ACCESS_ERROR** (0x06) Unable to perform check with open files.</span></span>
- <span data-ttu-id="ec793-2525">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-2525">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="ec793-2526">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-2526">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="ec793-2527">**FX_NO_MORE_SPACE** (0x0A) — на носителе больше нет места.</span><span class="sxs-lookup"><span data-stu-id="ec793-2527">**FX_NO_MORE_SPACE** (0x0A) No more space on the media.</span></span>
- <span data-ttu-id="ec793-2528">**FX_NOT_ENOUGH_MEMORY** (0x91) — указан недостаточный размер вспомогательной памяти.</span><span class="sxs-lookup"><span data-stu-id="ec793-2528">**FX_NOT_ENOUGH_MEMORY** (0x91) Supplied scratch memory is not large enough.</span></span>
- <span data-ttu-id="ec793-2529">**FX_ERROR_NOT_FIXED** (0x93) — повреждение корневого каталога FAT32, которое не удалось исправить.</span><span class="sxs-lookup"><span data-stu-id="ec793-2529">**FX_ERROR_NOT_FIXED** (0x93) Corruption of FAT32 root directory that could not be fixed.</span></span>
- <span data-ttu-id="ec793-2530">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-2530">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-2531">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-2531">**FX_SECTOR_INVALID** (0x89) Sector is invalid.</span></span>
- <span data-ttu-id="ec793-2532">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или временной памяти.</span><span class="sxs-lookup"><span data-stu-id="ec793-2532">**FX_PTR_ERROR** (0x18) Invalid media or scratch pointer.</span></span>
- <span data-ttu-id="ec793-2533">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-2533">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="ec793-2534">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-2534">Allowed From</span></span>

<span data-ttu-id="ec793-2535">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-2535">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-2536">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-2536">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="ec793-2537">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-2537">See Also</span></span>

- <span data-ttu-id="ec793-2538">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="ec793-2538">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="ec793-2539">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="ec793-2539">fx_media_abort</span></span>
- <span data-ttu-id="ec793-2540">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="ec793-2540">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="ec793-2541">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="ec793-2541">fx_media_close</span></span>
- <span data-ttu-id="ec793-2542">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2542">fx_media_close_notify_set</span></span>
- <span data-ttu-id="ec793-2543">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="ec793-2543">fx_media_exFAT_format</span></span>
- <span data-ttu-id="ec793-2544">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-2544">fx_media_extended_space_available</span></span>
- <span data-ttu-id="ec793-2545">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="ec793-2545">fx_media_flush</span></span>
- <span data-ttu-id="ec793-2546">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="ec793-2546">fx_media_format</span></span>
- <span data-ttu-id="ec793-2547">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="ec793-2547">fx_media_open</span></span>
- <span data-ttu-id="ec793-2548">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2548">fx_media_open_notify_set</span></span>
- <span data-ttu-id="ec793-2549">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="ec793-2549">fx_media_read</span></span>
- <span data-ttu-id="ec793-2550">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-2550">fx_media_space_available</span></span>
- <span data-ttu-id="ec793-2551">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="ec793-2551">fx_media_volume_get</span></span>
- <span data-ttu-id="ec793-2552">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2552">fx_media_volume_set</span></span>
- <span data-ttu-id="ec793-2553">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="ec793-2553">fx_media_write</span></span>
- <span data-ttu-id="ec793-2554">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ec793-2554">fx_system_initialize</span></span>

## <a name="fx_media_close"></a><span data-ttu-id="ec793-2555">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="ec793-2555">fx_media_close</span></span>

<span data-ttu-id="ec793-2556">Закрывает носитель</span><span class="sxs-lookup"><span data-stu-id="ec793-2556">Closes media</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-2557">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-2557">Prototype</span></span>

```c
UINT fx_media_close(FX_MEDIA *media_ptr);
```
### <a name="description"></a><span data-ttu-id="ec793-2558">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-2558">Description</span></span>

<span data-ttu-id="ec793-2559">Эта служба закрывает указанный носитель.</span><span class="sxs-lookup"><span data-stu-id="ec793-2559">This service closes the specified media.</span></span> <span data-ttu-id="ec793-2560">В процессе закрытия носителя все открытые файлы закрываются, а оставшиеся буферы записываются на физический носитель.</span><span class="sxs-lookup"><span data-stu-id="ec793-2560">In the process of closing the media, all open files are closed and any remaining buffers are flushed to the physical media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-2561">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-2561">Input Parameters</span></span>

- <span data-ttu-id="ec793-2562">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-2562">**media_ptr**: Pointer to media control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-2563">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-2563">Return Values</span></span>

- <span data-ttu-id="ec793-2564">**FX_SUCCESS** (0x00) — носитель успешно закрыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-2564">**FX_SUCCESS** (0x00) Successful media close.</span></span>
- <span data-ttu-id="ec793-2565">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-2565">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="ec793-2566">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-2566">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-2567">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-2567">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="ec793-2568">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-2568">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-2569">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-2569">Allowed From</span></span>

<span data-ttu-id="ec793-2570">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-2570">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-2571">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-2571">Example</span></span>

```c
FX_MEDIA    my_media;
UINT        status;
/* Close "my_media". */

status = fx_media_close(&my_media);

/* If status equals FX_SUCCESS, "my_media" is closed. */

```

### <a name="see-also"></a><span data-ttu-id="ec793-2572">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-2572">See Also</span></span>

- <span data-ttu-id="ec793-2573">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="ec793-2573">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="ec793-2574">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="ec793-2574">fx_media_abort</span></span>
- <span data-ttu-id="ec793-2575">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="ec793-2575">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="ec793-2576">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="ec793-2576">fx_media_check</span></span>
- <span data-ttu-id="ec793-2577">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2577">fx_media_close_notify_set</span></span>
- <span data-ttu-id="ec793-2578">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="ec793-2578">fx_media_exFAT_format</span></span>
- <span data-ttu-id="ec793-2579">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-2579">fx_media_extended_space_available</span></span>
- <span data-ttu-id="ec793-2580">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="ec793-2580">fx_media_flush</span></span>
- <span data-ttu-id="ec793-2581">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="ec793-2581">fx_media_format</span></span>
- <span data-ttu-id="ec793-2582">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="ec793-2582">fx_media_open</span></span>
- <span data-ttu-id="ec793-2583">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2583">fx_media_open_notify_set</span></span>
- <span data-ttu-id="ec793-2584">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="ec793-2584">fx_media_read</span></span>
- <span data-ttu-id="ec793-2585">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-2585">fx_media_space_available</span></span>
- <span data-ttu-id="ec793-2586">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="ec793-2586">fx_media_volume_get</span></span>
- <span data-ttu-id="ec793-2587">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2587">fx_media_volume_set</span></span>
- <span data-ttu-id="ec793-2588">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="ec793-2588">fx_media_write</span></span>
- <span data-ttu-id="ec793-2589">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ec793-2589">fx_system_initialize</span></span>

## <a name="fx_media_close_notify_set"></a><span data-ttu-id="ec793-2590">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2590">fx_media_close_notify_set</span></span>

<span data-ttu-id="ec793-2591">Задает функцию уведомления о закрытии носителя</span><span class="sxs-lookup"><span data-stu-id="ec793-2591">Sets the media close notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-2592">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-2592">Prototype</span></span>

```c
UINT fx_media_close_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_close_notify)(FX_MEDIA*));
```

### <a name="description"></a><span data-ttu-id="ec793-2593">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-2593">Description</span></span>

<span data-ttu-id="ec793-2594">Эта служба задает функцию обратного вызова уведомления, которая будет вызываться после успешного закрытия носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-2594">This service sets a notify callback function which will be invoked after a media is successfully closed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-2595">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-2595">Input Parameters</span></span>

- <span data-ttu-id="ec793-2596">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-2596">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="ec793-2597">**media_close_notify**: функция обратного вызова уведомления о закрытии носителя для установки</span><span class="sxs-lookup"><span data-stu-id="ec793-2597">**media_close_notify**: Media close notify callback function to be installed.</span></span> <span data-ttu-id="ec793-2598">Передача значения NULL в качестве функции обратного вызова отключает обратный вызов закрытия носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-2598">Passing NULL as the callback function disables the media close callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-2599">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-2599">Return Values</span></span>

- <span data-ttu-id="ec793-2600">**FX_SUCCESS** (0x00) — функция обратного вызова успешно установлена.</span><span class="sxs-lookup"><span data-stu-id="ec793-2600">**FX_SUCCESS** (0x00) Successfully installed the callback function.</span></span>
- <span data-ttu-id="ec793-2601">**FX_PTR_ERROR** (0x18) — параметр media_ptr имеет значение NULL.</span><span class="sxs-lookup"><span data-stu-id="ec793-2601">**FX_PTR_ERROR** (0x18) media_ptr is NULL.</span></span>
- <span data-ttu-id="ec793-2602">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-2602">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-2603">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-2603">Allowed From</span></span>

<span data-ttu-id="ec793-2604">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-2604">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-2605">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-2605">Example</span></span>

```c
fx_media_close_notify_set(media_ptr, my_media_close_callback);

```
### <a name="see-also"></a><span data-ttu-id="ec793-2606">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-2606">See Also</span></span>

- <span data-ttu-id="ec793-2607">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="ec793-2607">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="ec793-2608">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="ec793-2608">fx_media_abort</span></span>
- <span data-ttu-id="ec793-2609">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="ec793-2609">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="ec793-2610">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="ec793-2610">fx_media_check</span></span>
- <span data-ttu-id="ec793-2611">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="ec793-2611">fx_media_close</span></span>
- <span data-ttu-id="ec793-2612">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="ec793-2612">fx_media_exFAT_format</span></span>
- <span data-ttu-id="ec793-2613">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-2613">fx_media_extended_space_available</span></span>
- <span data-ttu-id="ec793-2614">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="ec793-2614">fx_media_flush</span></span>
- <span data-ttu-id="ec793-2615">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="ec793-2615">fx_media_format</span></span>
- <span data-ttu-id="ec793-2616">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="ec793-2616">fx_media_open</span></span>
- <span data-ttu-id="ec793-2617">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2617">fx_media_open_notify_set</span></span>
- <span data-ttu-id="ec793-2618">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="ec793-2618">fx_media_read</span></span>
- <span data-ttu-id="ec793-2619">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-2619">fx_media_space_available</span></span>
- <span data-ttu-id="ec793-2620">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="ec793-2620">fx_media_volume_get</span></span>
- <span data-ttu-id="ec793-2621">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2621">fx_media_volume_set</span></span>
- <span data-ttu-id="ec793-2622">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="ec793-2622">fx_media_write</span></span>
- <span data-ttu-id="ec793-2623">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ec793-2623">fx_system_initialize</span></span>

## <a name="fx_media_exfat_format"></a><span data-ttu-id="ec793-2624">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="ec793-2624">fx_media_exFAT_format</span></span>

<span data-ttu-id="ec793-2625">Форматирует носитель</span><span class="sxs-lookup"><span data-stu-id="ec793-2625">Formats media</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-2626">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-2626">Prototype</span></span>

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
### <a name="description"></a><span data-ttu-id="ec793-2627">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-2627">Description</span></span>

<span data-ttu-id="ec793-2628">Эта служба форматирует указанный носитель в формате, совместимом с exFAT, на основе заданных параметров.</span><span class="sxs-lookup"><span data-stu-id="ec793-2628">This service formats the supplied media in an exFAT compatible manner based on the supplied parameters.</span></span> <span data-ttu-id="ec793-2629">Эту службу следует вызывать перед открытием носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-2629">This service must be called prior to opening the media.</span></span>

> [!WARNING]
> <span data-ttu-id="ec793-2630">*Форматирование уже отформатированного носителя фактически приводит к удалению всех файлов и каталогов на нем.*</span><span class="sxs-lookup"><span data-stu-id="ec793-2630">*Formatting an already formatted media effectively erases all files and directories on the media.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec793-2631">*Размер тома exFAT должен соответствовать размеру раздела (при наличии макета MBR или GPT) или размеру всего устройства, если макет раздела отсутствует (MBR или GPT). В Windows существует ограничение, из-за которого диск exFAT не будет распознан, если он отформатирован с опреленными значениями общего числа секторов, которое меньше числа доступных секторов.*</span><span class="sxs-lookup"><span data-stu-id="ec793-2631">*The exFAT volume size should match the size of the partition (if there is an MBR or GPT layout), or the size of the whole device if there is no partition layout (no MBR or GPT). There is a limitation on Windows that exFAT Disk will not be recoginzed if formatted with some values of total sectors that are less than available sectors*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-2632">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-2632">Input Parameters</span></span>

- <span data-ttu-id="ec793-2633">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-2633">**media_ptr**: Pointer to media control block.</span></span> <span data-ttu-id="ec793-2634">Он используется только для предоставления некоторых основных сведений, необходимых для функционирования драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-2634">This is used only to provide some basic information necessary for the driver to operate.</span></span>
- <span data-ttu-id="ec793-2635">**driver**: указатель на драйвер ввода-вывода для этого носителя</span><span class="sxs-lookup"><span data-stu-id="ec793-2635">**driver**: Pointer to the I/O driver for this media.</span></span> <span data-ttu-id="ec793-2636">Обычно это тот же драйвер, который передается последующему вызову fx_media_open.</span><span class="sxs-lookup"><span data-stu-id="ec793-2636">This will typically be the same driver supplied to the subsequent fx_media_open call.</span></span>
- <span data-ttu-id="ec793-2637">**driver_info_ptr**: указатель на необязательные сведения, которые может использовать драйвер ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="ec793-2637">**driver_info_ptr**: Pointer to optional information that the I/O driver may utilize.</span></span>
- <span data-ttu-id="ec793-2638">**memory_ptr**: указатель на рабочую память для носителя</span><span class="sxs-lookup"><span data-stu-id="ec793-2638">**memory_ptr**: Pointer to the working memory for the media.</span></span> <span data-ttu-id="ec793-2639">memory_size: указывает размер рабочей памяти носителя</span><span class="sxs-lookup"><span data-stu-id="ec793-2639">memory_size Specifies the size of the working media memory.</span></span> <span data-ttu-id="ec793-2640">Размер должен быть не меньше размера сектора носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-2640">The size must be at least as large as the media's sector size.</span></span>
- <span data-ttu-id="ec793-2641">**volume_name**: указатель на строку имени тома (не более 11 символов)</span><span class="sxs-lookup"><span data-stu-id="ec793-2641">**volume_name**: Pointer to the volume name string, which is a maximum of 11 characters.</span></span>
- <span data-ttu-id="ec793-2642">**number_of_fats**: количество FAT на носителе</span><span class="sxs-lookup"><span data-stu-id="ec793-2642">**number_of_fats**: Number of FATs on the media.</span></span> <span data-ttu-id="ec793-2643">Текущая реализация поддерживает одну FAT на носителе.</span><span class="sxs-lookup"><span data-stu-id="ec793-2643">Current implementation supports one FAT on the media.</span></span>
- <span data-ttu-id="ec793-2644">**hidden_sectors**: количество секторов, скрытых перед загрузочным сектором этого носителя</span><span class="sxs-lookup"><span data-stu-id="ec793-2644">**hidden_sectors**: Number of sectors hidden before this media's boot sector.</span></span> <span data-ttu-id="ec793-2645">Это характерно при наличии нескольких разделов.</span><span class="sxs-lookup"><span data-stu-id="ec793-2645">This is typical when multiple partitions are present.</span></span>
- <span data-ttu-id="ec793-2646">**total_sectors**: общее количество секторов на носителе</span><span class="sxs-lookup"><span data-stu-id="ec793-2646">**total_sectors**: Total number of sectors in the media.</span></span>
- <span data-ttu-id="ec793-2647">**bytes_per_sector**: число байтов на сектор (обычно 512)</span><span class="sxs-lookup"><span data-stu-id="ec793-2647">**bytes_per_sector**: Number of bytes per sector, which is typically 512.</span></span> <span data-ttu-id="ec793-2648">Для FileX требуется, чтобы оно было кратным 32.</span><span class="sxs-lookup"><span data-stu-id="ec793-2648">FileX requires this to be a multiple of 32.</span></span>
- <span data-ttu-id="ec793-2649">**sectors_per_cluster**: количество секторов в каждом кластере</span><span class="sxs-lookup"><span data-stu-id="ec793-2649">**sectors_per_cluster**: Number of sectors in each cluster.</span></span> <span data-ttu-id="ec793-2650">Кластер является минимальной единицей размещения в файловой системе FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-2650">The cluster is the minimum allocation unit in a FAT file system.</span></span>
- <span data-ttu-id="ec793-2651">**volumne_serial_number**: серийный номер, используемый для этого тома</span><span class="sxs-lookup"><span data-stu-id="ec793-2651">**volumne_serial_number**: Serial number to be used for this volume.</span></span>
- <span data-ttu-id="ec793-2652">**boundary_unit**: размер для выравнивания области физических данных (в количестве секторов)</span><span class="sxs-lookup"><span data-stu-id="ec793-2652">**boundary_unit**: Physical data area alignment size, in number of sectors.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-2653">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-2653">Return Values</span></span>

- <span data-ttu-id="ec793-2654">**FX_SUCCESS** (0x00) — носитель успешно отформатирован.</span><span class="sxs-lookup"><span data-stu-id="ec793-2654">**FX_SUCCESS** (0x00) Successful media format.</span></span>
- <span data-ttu-id="ec793-2655">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-2655">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-2656">**FX_PTR_ERROR** (0x18) — недопустимый носитель, драйвер или указатель на память.</span><span class="sxs-lookup"><span data-stu-id="ec793-2656">**FX_PTR_ERROR** (0x18) Invalid media, driver, or memory pointer.</span></span>
- <span data-ttu-id="ec793-2657">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-2657">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-2658">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-2658">Allowed From</span></span>

<span data-ttu-id="ec793-2659">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-2659">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-2660">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-2660">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="ec793-2661">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-2661">See Also</span></span>

- <span data-ttu-id="ec793-2662">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="ec793-2662">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="ec793-2663">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="ec793-2663">fx_media_abort</span></span>
- <span data-ttu-id="ec793-2664">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="ec793-2664">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="ec793-2665">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="ec793-2665">fx_media_check</span></span>
- <span data-ttu-id="ec793-2666">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="ec793-2666">fx_media_close</span></span>
- <span data-ttu-id="ec793-2667">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2667">fx_media_close_notify_set</span></span>
- <span data-ttu-id="ec793-2668">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-2668">fx_media_extended_space_available</span></span>
- <span data-ttu-id="ec793-2669">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="ec793-2669">fx_media_flush</span></span>
- <span data-ttu-id="ec793-2670">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="ec793-2670">fx_media_format</span></span>
- <span data-ttu-id="ec793-2671">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="ec793-2671">fx_media_open</span></span>
- <span data-ttu-id="ec793-2672">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2672">fx_media_open_notify_set</span></span>
- <span data-ttu-id="ec793-2673">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="ec793-2673">fx_media_read</span></span>
- <span data-ttu-id="ec793-2674">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-2674">fx_media_space_available</span></span>
- <span data-ttu-id="ec793-2675">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="ec793-2675">fx_media_volume_get</span></span>
- <span data-ttu-id="ec793-2676">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2676">fx_media_volume_set</span></span>
- <span data-ttu-id="ec793-2677">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="ec793-2677">fx_media_write</span></span>
- <span data-ttu-id="ec793-2678">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ec793-2678">fx_system_initialize</span></span>

## <a name="fx_media_extended_space_available"></a><span data-ttu-id="ec793-2679">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-2679">fx_media_extended_space_available</span></span>

<span data-ttu-id="ec793-2680">Возвращает доступное пространство на носителе</span><span class="sxs-lookup"><span data-stu-id="ec793-2680">Returns available media space</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-2681">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-2681">Prototype</span></span>

```c
UINT fx_media_extended_space_available(
    FX_MEDIA *media_ptr,
    ULONG64 *available_bytes_ptr);
```
### <a name="description"></a><span data-ttu-id="ec793-2682">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-2682">Description</span></span>

<span data-ttu-id="ec793-2683">Эта служба возвращает число байтов, доступных на носителе.</span><span class="sxs-lookup"><span data-stu-id="ec793-2683">This service returns the number of bytes available in the media.</span></span>

<span data-ttu-id="ec793-2684">Эта служба разработана для exFAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-2684">This service is designed for exFAT.</span></span> <span data-ttu-id="ec793-2685">Указатель на параметр *available_bytes* принимает значение 64-разрядного целого числа, которое позволяет вызывающему объекту работать с носителями объемом свыше 4 ГБ.</span><span class="sxs-lookup"><span data-stu-id="ec793-2685">The pointer to *available_bytes* parameter takes a 64-bit integer value, which allows the caller to work with media beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-2686">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-2686">Input Parameters</span></span>

- <span data-ttu-id="ec793-2687">**media_ptr**: указатель на открытый ранее носитель</span><span class="sxs-lookup"><span data-stu-id="ec793-2687">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="ec793-2688">**available_bytes_ptr**: число байтов, доступное на носителе</span><span class="sxs-lookup"><span data-stu-id="ec793-2688">**available_bytes_ptr**: Available bytes left in the media.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-2689">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-2689">Return Values</span></span>

- <span data-ttu-id="ec793-2690">**FX_SUCCESS** (0x00) — доступное место на носителе успешно получено.</span><span class="sxs-lookup"><span data-stu-id="ec793-2690">**FX_SUCCESS** (0x00) Successfully retrieved space available on the media.</span></span>
- <span data-ttu-id="ec793-2691">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-2691">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="ec793-2692">**FX_PTR_ERROR** (0x18) — недопустимый указатель на носитель, или доступное количество байтов имеет значение NULL.</span><span class="sxs-lookup"><span data-stu-id="ec793-2692">**FX_PTR_ERROR** (0x18) Invalid media pointer or available bytes pointer is NULL.</span></span>
- <span data-ttu-id="ec793-2693">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-2693">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-2694">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-2694">Allowed From</span></span>

<span data-ttu-id="ec793-2695">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-2695">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-2696">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-2696">Example</span></span>

```c
FX_MEDIA        my_media;
ULONG64            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_extended_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a><span data-ttu-id="ec793-2697">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-2697">See Also</span></span>

- <span data-ttu-id="ec793-2698">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="ec793-2698">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="ec793-2699">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="ec793-2699">fx_media_abort</span></span>
- <span data-ttu-id="ec793-2700">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="ec793-2700">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="ec793-2701">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="ec793-2701">fx_media_check</span></span>
- <span data-ttu-id="ec793-2702">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="ec793-2702">fx_media_close</span></span>
- <span data-ttu-id="ec793-2703">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2703">fx_media_close_notify_set</span></span>
- <span data-ttu-id="ec793-2704">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="ec793-2704">fx_media_exFAT_format</span></span>
- <span data-ttu-id="ec793-2705">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="ec793-2705">fx_media_flush</span></span>
- <span data-ttu-id="ec793-2706">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="ec793-2706">fx_media_format</span></span>
- <span data-ttu-id="ec793-2707">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="ec793-2707">fx_media_open</span></span>
- <span data-ttu-id="ec793-2708">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2708">fx_media_open_notify_set</span></span>
- <span data-ttu-id="ec793-2709">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="ec793-2709">fx_media_read</span></span>
- <span data-ttu-id="ec793-2710">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-2710">fx_media_space_available</span></span>
- <span data-ttu-id="ec793-2711">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="ec793-2711">fx_media_volume_get</span></span>
- <span data-ttu-id="ec793-2712">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2712">fx_media_volume_set</span></span>
- <span data-ttu-id="ec793-2713">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="ec793-2713">fx_media_write</span></span>
- <span data-ttu-id="ec793-2714">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ec793-2714">fx_system_initialize</span></span>

## <a name="fx_media_flush"></a><span data-ttu-id="ec793-2715">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="ec793-2715">fx_media_flush</span></span>

<span data-ttu-id="ec793-2716">Записывает данные на физический носитель</span><span class="sxs-lookup"><span data-stu-id="ec793-2716">Flushes data to physical media</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-2717">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-2717">Prototype</span></span>

```c
UINT fx_media_flush(FX_MEDIA *media_ptr);
```
### <a name="description"></a><span data-ttu-id="ec793-2718">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-2718">Description</span></span>

<span data-ttu-id="ec793-2719">Эта служба записывает все кэшированные секторы и записи каталога всех измененных файлов на физический носитель.</span><span class="sxs-lookup"><span data-stu-id="ec793-2719">This service flushes all cached sectors and directory entries of any modified files to the physical media.</span></span>

> [!WARNING]
> <span data-ttu-id="ec793-2720">*Эта процедура может периодически вызываться приложением для снижения риска повреждения файла и (или) потери данных в случае внезапного отключения питания целевого объекта.*</span><span class="sxs-lookup"><span data-stu-id="ec793-2720">*This routine may be called periodically by the application to reduce the risk of file corruption and/or data loss in the event of a sudden loss of power on the target.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-2721">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-2721">Input Parameters</span></span>

- <span data-ttu-id="ec793-2722">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-2722">**media_ptr**: Pointer to media control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-2723">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-2723">Return Values</span></span>

- <span data-ttu-id="ec793-2724">**FX_SUCCESS** (0x00) — запись на диск успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="ec793-2724">**FX_SUCCESS** (0x00) Successful media flush.</span></span>
- <span data-ttu-id="ec793-2725">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-2725">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="ec793-2726">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-2726">**FX_FILE_CORRUPT**    (0x08) File is corrupted.</span></span>
- <span data-ttu-id="ec793-2727">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-2727">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="ec793-2728">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-2728">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-2729">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-2729">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="ec793-2730">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-2730">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="ec793-2731">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-2731">**FX_CALLER_ERROR**    (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-2732">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-2732">Allowed From</span></span>

<span data-ttu-id="ec793-2733">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-2733">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-2734">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-2734">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;

/* Flush all cached sectors and modified file entries to the physical media. */

status = fx_media_flush(&my_media);

/* If status equals FX_SUCCESS, the physical media is completely up-to-date. */

```

### <a name="see-also"></a><span data-ttu-id="ec793-2735">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-2735">See Also</span></span>

- <span data-ttu-id="ec793-2736">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="ec793-2736">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="ec793-2737">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="ec793-2737">fx_media_abort</span></span>
- <span data-ttu-id="ec793-2738">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="ec793-2738">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="ec793-2739">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="ec793-2739">fx_media_check</span></span>
- <span data-ttu-id="ec793-2740">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="ec793-2740">fx_media_close</span></span>
- <span data-ttu-id="ec793-2741">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2741">fx_media_close_notify_set</span></span>
- <span data-ttu-id="ec793-2742">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="ec793-2742">fx_media_exFAT_format</span></span>
- <span data-ttu-id="ec793-2743">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-2743">fx_media_extended_space_available</span></span>
- <span data-ttu-id="ec793-2744">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="ec793-2744">fx_media_format</span></span>
- <span data-ttu-id="ec793-2745">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="ec793-2745">fx_media_open</span></span>
- <span data-ttu-id="ec793-2746">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2746">fx_media_open_notify_set</span></span>
- <span data-ttu-id="ec793-2747">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="ec793-2747">fx_media_read</span></span>
- <span data-ttu-id="ec793-2748">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-2748">fx_media_space_available</span></span>
- <span data-ttu-id="ec793-2749">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="ec793-2749">fx_media_volume_get</span></span>
- <span data-ttu-id="ec793-2750">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2750">fx_media_volume_set</span></span>
- <span data-ttu-id="ec793-2751">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="ec793-2751">fx_media_write</span></span>
- <span data-ttu-id="ec793-2752">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ec793-2752">fx_system_initialize</span></span>

## <a name="fx_media_format"></a><span data-ttu-id="ec793-2753">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="ec793-2753">fx_media_format</span></span>

<span data-ttu-id="ec793-2754">Форматирует носитель</span><span class="sxs-lookup"><span data-stu-id="ec793-2754">Formats media</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-2755">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-2755">Prototype</span></span>

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
### <a name="description"></a><span data-ttu-id="ec793-2756">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-2756">Description</span></span>

<span data-ttu-id="ec793-2757">Эта служба форматирует указанный носитель в формате, совместимом с FAT 12/16/32, на основе заданных параметров.</span><span class="sxs-lookup"><span data-stu-id="ec793-2757">This service formats the supplied media in a FAT 12/16/32 compatible manner based on the supplied parameters.</span></span> <span data-ttu-id="ec793-2758">Эту службу следует вызывать перед открытием носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-2758">This service must be called prior to opening the media.</span></span>

> [!WARNING]
> <span data-ttu-id="ec793-2759">*Форматирование уже отформатированного носителя фактически приводит к удалению всех файлов и каталогов на нем.*</span><span class="sxs-lookup"><span data-stu-id="ec793-2759">*Formatting an already formatted media effectively erases all files and directories on the media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-2760">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-2760">Input Parameters</span></span>

- <span data-ttu-id="ec793-2761">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-2761">**media_ptr**: Pointer to media control block.</span></span> <span data-ttu-id="ec793-2762">Он используется только для предоставления некоторых основных сведений, необходимых для функционирования драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-2762">This is used only to provide some basic information necessary for the driver to operate.</span></span>
- <span data-ttu-id="ec793-2763">**driver**: указатель на драйвер ввода-вывода для этого носителя</span><span class="sxs-lookup"><span data-stu-id="ec793-2763">**driver**: Pointer to the I/O driver for this media.</span></span> <span data-ttu-id="ec793-2764">Обычно это тот же драйвер, который передается последующему вызову fx_media_open.</span><span class="sxs-lookup"><span data-stu-id="ec793-2764">This will typically be the same driver supplied to the subsequent fx_media_open call.</span></span>
- <span data-ttu-id="ec793-2765">**driver_info_ptr**: указатель на необязательные сведения, которые может использовать драйвер ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="ec793-2765">**driver_info_ptr**: Pointer to optional information that the I/O driver may utilize.</span></span>
- <span data-ttu-id="ec793-2766">**memory_ptr**: указатель на рабочую память для носителя</span><span class="sxs-lookup"><span data-stu-id="ec793-2766">**memory_ptr**: Pointer to the working memory for the media.</span></span>
- <span data-ttu-id="ec793-2767">**memory_size** указывает размер рабочей памяти носителя</span><span class="sxs-lookup"><span data-stu-id="ec793-2767">**memory_size**: Specifies the size of the working media memory.</span></span> <span data-ttu-id="ec793-2768">Размер должен быть не меньше размера сектора носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-2768">The size must be at least as large as the media's sector size.</span></span>
- <span data-ttu-id="ec793-2769">**volume_name**: указатель на строку имени тома (не более 11 символов)</span><span class="sxs-lookup"><span data-stu-id="ec793-2769">**volume_name**: Pointer to the volume name string, which is a maximum of 11 characters.</span></span>
- <span data-ttu-id="ec793-2770">**number_of_fats**: количество FAT на носителе</span><span class="sxs-lookup"><span data-stu-id="ec793-2770">**number_of_fats**: Number of FATs in the media.</span></span> <span data-ttu-id="ec793-2771">Минимальное значение равно 1 для основной файловой системы FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-2771">The minimal value is 1 for the primary FAT.</span></span> <span data-ttu-id="ec793-2772">Значения, превышающие 1, приводят к поддержке дополнительных копий FAT во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="ec793-2772">Values greater than 1 result in additional FAT copies being maintained at run-time.</span></span>
- <span data-ttu-id="ec793-2773">**directory_entries**: количество записей каталога в корневом каталоге</span><span class="sxs-lookup"><span data-stu-id="ec793-2773">**directory_entries**: Number of directory entries in the root directory.</span></span>
- <span data-ttu-id="ec793-2774">**hidden_sectors**: количество секторов, скрытых перед загрузочным сектором этого носителя</span><span class="sxs-lookup"><span data-stu-id="ec793-2774">**hidden_sectors**: Number of sectors hidden before this media's boot sector.</span></span> <span data-ttu-id="ec793-2775">Это характерно при наличии нескольких разделов.</span><span class="sxs-lookup"><span data-stu-id="ec793-2775">This is typical when multiple partitions are present.</span></span>
- <span data-ttu-id="ec793-2776">**total_sectors**: общее количество секторов на носителе</span><span class="sxs-lookup"><span data-stu-id="ec793-2776">**total_sectors**: Total number of sectors in the media.</span></span>
- <span data-ttu-id="ec793-2777">**bytes_per_sector**: число байтов на сектор (обычно 512)</span><span class="sxs-lookup"><span data-stu-id="ec793-2777">**bytes_per_sector**: Number of bytes per sector, which is typically 512.</span></span> <span data-ttu-id="ec793-2778">Для FileX требуется, чтобы оно было кратным 32.</span><span class="sxs-lookup"><span data-stu-id="ec793-2778">FileX requires this to be a multiple of 32.</span></span>
- <span data-ttu-id="ec793-2779">**sectors_per_cluster**: количество секторов в каждом кластере</span><span class="sxs-lookup"><span data-stu-id="ec793-2779">**sectors_per_cluster**: Number of sectors in each cluster.</span></span> <span data-ttu-id="ec793-2780">Кластер является минимальной единицей размещения в файловой системе FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-2780">The cluster is the minimum allocation unit in a FAT file system.</span></span>
- <span data-ttu-id="ec793-2781">**heads**: количество физических головок</span><span class="sxs-lookup"><span data-stu-id="ec793-2781">**heads**: Number of physical heads.</span></span>
- <span data-ttu-id="ec793-2782">**sectors_per_track**: количество секторов на дорожке</span><span class="sxs-lookup"><span data-stu-id="ec793-2782">**sectors_per_track**: Number of sectors per track.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-2783">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-2783">Return Values</span></span>

- <span data-ttu-id="ec793-2784">**FX_SUCCESS** (0x00) — носитель успешно отформатирован.</span><span class="sxs-lookup"><span data-stu-id="ec793-2784">**FX_SUCCESS** (0x00) Successful media format.</span></span>
- <span data-ttu-id="ec793-2785">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-2785">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-2786">**FX_PTR_ERROR** (0x18) — недопустимый носитель, драйвер или указатель на память.</span><span class="sxs-lookup"><span data-stu-id="ec793-2786">**FX_PTR_ERROR** (0x18) Invalid media, driver, or memory pointer.</span></span>
- <span data-ttu-id="ec793-2787">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-2787">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-2788">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-2788">Allowed From</span></span>

<span data-ttu-id="ec793-2789">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-2789">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-2790">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-2790">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="ec793-2791">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-2791">See Also</span></span>

- <span data-ttu-id="ec793-2792">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="ec793-2792">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="ec793-2793">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="ec793-2793">fx_media_abort</span></span>
- <span data-ttu-id="ec793-2794">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="ec793-2794">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="ec793-2795">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="ec793-2795">fx_media_check</span></span>
- <span data-ttu-id="ec793-2796">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="ec793-2796">fx_media_close</span></span>
- <span data-ttu-id="ec793-2797">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2797">fx_media_close_notify_set</span></span>
- <span data-ttu-id="ec793-2798">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="ec793-2798">fx_media_exFAT_format</span></span>
- <span data-ttu-id="ec793-2799">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-2799">fx_media_extended_space_available</span></span>
- <span data-ttu-id="ec793-2800">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="ec793-2800">fx_media_flush</span></span>
- <span data-ttu-id="ec793-2801">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="ec793-2801">fx_media_open</span></span>
- <span data-ttu-id="ec793-2802">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2802">fx_media_open_notify_set</span></span>
- <span data-ttu-id="ec793-2803">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="ec793-2803">fx_media_read</span></span>
- <span data-ttu-id="ec793-2804">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-2804">fx_media_space_available</span></span>
- <span data-ttu-id="ec793-2805">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="ec793-2805">fx_media_volume_get</span></span>
- <span data-ttu-id="ec793-2806">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2806">fx_media_volume_set</span></span>
- <span data-ttu-id="ec793-2807">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="ec793-2807">fx_media_write</span></span>
- <span data-ttu-id="ec793-2808">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ec793-2808">fx_system_initialize</span></span>

## <a name="fx_media_open"></a><span data-ttu-id="ec793-2809">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="ec793-2809">fx_media_open</span></span>

<span data-ttu-id="ec793-2810">Открывает носитель для доступа к файлам</span><span class="sxs-lookup"><span data-stu-id="ec793-2810">Opens media for file access</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-2811">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-2811">Prototype</span></span>

```c
UINT fx_media_open(
    FX_MEDIA *media_ptr, 
    CHAR *media_name,
    VOID(*media_driver)(FX_MEDIA *),
    VOID *driver_info_ptr,
    VOID *memory_ptr, 
    ULONG memory_size);
```
### <a name="description"></a><span data-ttu-id="ec793-2812">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-2812">Description</span></span>

<span data-ttu-id="ec793-2813">Эта служба открывает носитель для доступа к файлам с помощью предоставляемого драйвера ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="ec793-2813">This service opens a media for file access using the supplied I/O driver.</span></span>

> [!WARNING]
> <span data-ttu-id="ec793-2814">*Память, предоставляемая этой службе, используется для реализации внутреннего кэша логических секторов, поэтому чем больше памяти выделяется, тем меньше снижается объем физического ввода-вывода. Для FileX требуется кэш по крайней мере для одного логического сектора (байт на сектор носителя).*</span><span class="sxs-lookup"><span data-stu-id="ec793-2814">*The memory supplied to this service is used to implement an internal logical sector cache, hence, the more memory supplied the more physical I/O is reduced. FileX requires a cache of at least one logical sector (bytes per sector of the media).*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-2815">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-2815">Input Parameters</span></span>

- <span data-ttu-id="ec793-2816">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-2816">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="ec793-2817">**media_name**: указатель на имя носителя</span><span class="sxs-lookup"><span data-stu-id="ec793-2817">**media_name**: Pointer to media's name.</span></span>
- <span data-ttu-id="ec793-2818">**media_driver**: указатель на драйвер ввода-вывода для этого носителя</span><span class="sxs-lookup"><span data-stu-id="ec793-2818">**media_driver**: Pointer to I/O driver for this media.</span></span> <span data-ttu-id="ec793-2819">Драйвер ввода-вывода должен соответствовать требованиям к драйверу FileX, определенным в главе 5.</span><span class="sxs-lookup"><span data-stu-id="ec793-2819">The I/O driver must conform to FileX driver requirements defined in Chapter 5.</span></span>
- <span data-ttu-id="ec793-2820">**driver_info_ptr**: указатель на необязательные сведения, которые может использовать указанный драйвер ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="ec793-2820">**driver_info_ptr**: Pointer to optional information that the supplied I/O driver may utilize.</span></span>
- <span data-ttu-id="ec793-2821">**memory_ptr**: указатель на рабочую память для носителя</span><span class="sxs-lookup"><span data-stu-id="ec793-2821">**memory_ptr**: Pointer to the working memory for the media.</span></span>
- <span data-ttu-id="ec793-2822">**memory_size** указывает размер рабочей памяти носителя</span><span class="sxs-lookup"><span data-stu-id="ec793-2822">**memory_size**: Specifies the size of the working media memory.</span></span> <span data-ttu-id="ec793-2823">Размер должен быть больше, чем размер сектора носителя (обычно 512 байт).</span><span class="sxs-lookup"><span data-stu-id="ec793-2823">The size must be as large as the media's sector size (typically 512 bytes).</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-2824">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-2824">Return Values</span></span>

- <span data-ttu-id="ec793-2825">**FX_SUCCESS** (0x00) — носитель успешно открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-2825">**FX_SUCCESS** (0x00) Successful media open.</span></span>
- <span data-ttu-id="ec793-2826">**FX_BOOT_ERROR** (0x01) — ошибка при чтении загрузочного сектора носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-2826">**FX_BOOT_ERROR** (0x01) Error reading the media's boot sector.</span></span>
- <span data-ttu-id="ec793-2827">**FX_MEDIA_INVALID** (0x02) — указанный загрузочный сектор носителя поврежден или недопустим.</span><span class="sxs-lookup"><span data-stu-id="ec793-2827">**FX_MEDIA_INVALID** (0x02) Specified media's boot sector is corrupt or invalid.</span></span> <span data-ttu-id="ec793-2828">Кроме того, этот код возврата используется, чтобы указать, что либо размер кэша логического сектора, либо размер записи FAT не является степенью 2.</span><span class="sxs-lookup"><span data-stu-id="ec793-2828">In addition, this return code is used to indicate that either the logical sector cache size or the FAT entry size is not a power of 2.</span></span>
- <span data-ttu-id="ec793-2829">**FX_FAT_READ_ERROR** (0x03) — ошибка при чтении FAT носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-2829">**FX_FAT_READ_ERROR** (0x03) Error reading the media FAT.</span></span>
- <span data-ttu-id="ec793-2830">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-2830">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-2831">**FX_PTR_ERROR** (0x18) — один указатель или несколько имеют значение NULL.</span><span class="sxs-lookup"><span data-stu-id="ec793-2831">**FX_PTR_ERROR** (0x18) One or more pointers are NULL.</span></span>
- <span data-ttu-id="ec793-2832">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-2832">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-2833">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-2833">Allowed From</span></span>

<span data-ttu-id="ec793-2834">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-2834">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-2835">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-2835">Example</span></span>

```c
FX_MEDIA         ram_disk,
UINT             status;
UCHAR             buffer[128];
/* Open a 32KByte RAM disk starting at the fixed address of 0x800000.
    Note that the total 32KByte media size and 128-byte sector size is defined inside of the driver. */

status = fx_media_open(&ram_disk, "RAM DISK", fx_ram_driver, 0, &buffer[0], sizeof(buffer));

/* If status equals FX_SUCCESS, the RAM disk has been successfully setup and is ready for file access! */

```

### <a name="see-also"></a><span data-ttu-id="ec793-2836">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-2836">See Also</span></span>

- <span data-ttu-id="ec793-2837">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="ec793-2837">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="ec793-2838">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="ec793-2838">fx_media_abort</span></span>
- <span data-ttu-id="ec793-2839">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="ec793-2839">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="ec793-2840">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="ec793-2840">fx_media_check</span></span>
- <span data-ttu-id="ec793-2841">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="ec793-2841">fx_media_close</span></span>
- <span data-ttu-id="ec793-2842">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2842">fx_media_close_notify_set</span></span>
- <span data-ttu-id="ec793-2843">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="ec793-2843">fx_media_exFAT_format</span></span>
- <span data-ttu-id="ec793-2844">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-2844">fx_media_extended_space_available</span></span>
- <span data-ttu-id="ec793-2845">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="ec793-2845">fx_media_flush</span></span>
- <span data-ttu-id="ec793-2846">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="ec793-2846">fx_media_format</span></span>
- <span data-ttu-id="ec793-2847">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2847">fx_media_open_notify_set</span></span>
- <span data-ttu-id="ec793-2848">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="ec793-2848">fx_media_read</span></span>
- <span data-ttu-id="ec793-2849">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-2849">fx_media_space_available</span></span>
- <span data-ttu-id="ec793-2850">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="ec793-2850">fx_media_volume_get</span></span>
- <span data-ttu-id="ec793-2851">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2851">fx_media_volume_set</span></span>
- <span data-ttu-id="ec793-2852">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="ec793-2852">fx_media_write</span></span>
- <span data-ttu-id="ec793-2853">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ec793-2853">fx_system_initialize</span></span>

## <a name="fx_media_open_notify_set"></a><span data-ttu-id="ec793-2854">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2854">fx_media_open_notify_set</span></span>

<span data-ttu-id="ec793-2855">Задает функцию уведомления об открытии носителя</span><span class="sxs-lookup"><span data-stu-id="ec793-2855">Sets the media open notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-2856">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-2856">Prototype</span></span>

```c
UINT fx_media_open_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_open_notify)(FX_MEDIA*));
```
### <a name="description"></a><span data-ttu-id="ec793-2857">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-2857">Description</span></span>

<span data-ttu-id="ec793-2858">Эта служба задает функцию обратного вызова уведомления, которая будет вызываться после успешного открытия носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-2858">This service sets a notify callback function which will be invoked after a media is successfully opened.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-2859">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-2859">Input Parameters</span></span>

- <span data-ttu-id="ec793-2860">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-2860">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="ec793-2861">**media_open_notify**: функция обратного вызова уведомления об открытии носителя для установки</span><span class="sxs-lookup"><span data-stu-id="ec793-2861">**media_open_notify**: Media open notify callback function to be installed.</span></span> <span data-ttu-id="ec793-2862">Передача значения NULL в качестве функции обратного вызова отключает обратный вызов открытия носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-2862">Passing NULL as the callback function disables the media open callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-2863">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-2863">Return Values</span></span>


- <span data-ttu-id="ec793-2864">**FX_SUCCESS** (0x00) — функция обратного вызова успешно установлена.</span><span class="sxs-lookup"><span data-stu-id="ec793-2864">**FX_SUCCESS** (0x00) Successfuly installed the callback function.</span></span>
- <span data-ttu-id="ec793-2865">**FX_PTR_ERROR** (0x18) — параметр media_ptr имеет значение NULL.</span><span class="sxs-lookup"><span data-stu-id="ec793-2865">**FX_PTR_ERROR** (0x18) media_ptr is NULL.</span></span>
- <span data-ttu-id="ec793-2866">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-2866">**FX_CALLER_ERROR**    (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-2867">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-2867">Allowed From</span></span>

<span data-ttu-id="ec793-2868">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-2868">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-2869">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-2869">Example</span></span>

```c
fx_media_open_notify_set(media_ptr, my_media_open_callback);

```

### <a name="see-also"></a><span data-ttu-id="ec793-2870">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-2870">See Also</span></span>

- <span data-ttu-id="ec793-2871">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="ec793-2871">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="ec793-2872">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="ec793-2872">fx_media_abort</span></span>
- <span data-ttu-id="ec793-2873">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="ec793-2873">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="ec793-2874">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="ec793-2874">fx_media_check</span></span>
- <span data-ttu-id="ec793-2875">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="ec793-2875">fx_media_close</span></span>
- <span data-ttu-id="ec793-2876">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2876">fx_media_close_notify_set</span></span>
- <span data-ttu-id="ec793-2877">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="ec793-2877">fx_media_exFAT_format</span></span>
- <span data-ttu-id="ec793-2878">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-2878">fx_media_extended_space_available</span></span>
- <span data-ttu-id="ec793-2879">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="ec793-2879">fx_media_flush</span></span>
- <span data-ttu-id="ec793-2880">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="ec793-2880">fx_media_format</span></span>
- <span data-ttu-id="ec793-2881">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="ec793-2881">fx_media_open</span></span>
- <span data-ttu-id="ec793-2882">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2882">fx_media_open_notify_set</span></span>
- <span data-ttu-id="ec793-2883">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-2883">fx_media_space_available</span></span>
- <span data-ttu-id="ec793-2884">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="ec793-2884">fx_media_volume_get</span></span>
- <span data-ttu-id="ec793-2885">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2885">fx_media_volume_set</span></span>
- <span data-ttu-id="ec793-2886">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="ec793-2886">fx_media_write</span></span>
- <span data-ttu-id="ec793-2887">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ec793-2887">fx_system_initialize</span></span>

## <a name="fx_media_read"></a><span data-ttu-id="ec793-2888">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="ec793-2888">fx_media_read</span></span>

<span data-ttu-id="ec793-2889">Чтение логического сектора с носителя</span><span class="sxs-lookup"><span data-stu-id="ec793-2889">Reads logical sector from media</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-2890">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-2890">Prototype</span></span>

```c
UINT fx_media_read(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector, 
    VOID *buffer_ptr);
```
### <a name="description"></a><span data-ttu-id="ec793-2891">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-2891">Description</span></span>

<span data-ttu-id="ec793-2892">Эта служба считывает логический сектор с носителя и помещает его в указанный буфер.</span><span class="sxs-lookup"><span data-stu-id="ec793-2892">This service reads a logical sector from the media and places it into the supplied buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-2893">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-2893">Input Parameters</span></span>

- <span data-ttu-id="ec793-2894">**media_ptr**: указатель на открытый ранее носитель</span><span class="sxs-lookup"><span data-stu-id="ec793-2894">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="ec793-2895">**logical_sector**: логический сектор для считывания</span><span class="sxs-lookup"><span data-stu-id="ec793-2895">**logical_sector**: Logical sector to read.</span></span>
- <span data-ttu-id="ec793-2896">**buffer_ptr**: указатель на назначение для считывания логического сектора</span><span class="sxs-lookup"><span data-stu-id="ec793-2896">**buffer_ptr**: Pointer to the destination for the logical sector read.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-2897">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-2897">Return Values</span></span>

- <span data-ttu-id="ec793-2898">**FX_SUCCESS** (0x00) — носитель успешно считан.</span><span class="sxs-lookup"><span data-stu-id="ec793-2898">**FX_SUCCESS** (0x00) Successful media read.</span></span>
- <span data-ttu-id="ec793-2899">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-2899">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="ec793-2900">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-2900">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-2901">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-2901">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="ec793-2902">**FX_PTR_ERROR** (0x18) — недопустимый указатель на носитель или буфер.</span><span class="sxs-lookup"><span data-stu-id="ec793-2902">**FX_PTR_ERROR** (0x18) Invalid media or buffer pointer.</span></span>
- <span data-ttu-id="ec793-2903">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-2903">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-2904">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-2904">Allowed From</span></span>

<span data-ttu-id="ec793-2905">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-2905">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-2906">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-2906">Example</span></span>

```c
FX_MEDIA         my_media;
UCHAR             my_buffer[128];
UINT            STATUS;
/* Read logical sector 22 into "my_buffer" assuming the
    physical media has a sector size of 128. */
status = fx_media_read(&my_media, 22, my_buffer);
/* If status equals FX_SUCCESS, the contents of logical sector 22 are in "my_buffer". */
```

### <a name="see-also"></a><span data-ttu-id="ec793-2907">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-2907">See Also</span></span>

- <span data-ttu-id="ec793-2908">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="ec793-2908">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="ec793-2909">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="ec793-2909">fx_media_abort</span></span>
- <span data-ttu-id="ec793-2910">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="ec793-2910">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="ec793-2911">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="ec793-2911">fx_media_check</span></span>
- <span data-ttu-id="ec793-2912">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="ec793-2912">fx_media_close</span></span>
- <span data-ttu-id="ec793-2913">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2913">fx_media_close_notify_set</span></span>
- <span data-ttu-id="ec793-2914">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="ec793-2914">fx_media_exFAT_format</span></span>
- <span data-ttu-id="ec793-2915">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-2915">fx_media_extended_space_available</span></span>
- <span data-ttu-id="ec793-2916">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="ec793-2916">fx_media_flush</span></span>
- <span data-ttu-id="ec793-2917">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="ec793-2917">fx_media_format</span></span>
- <span data-ttu-id="ec793-2918">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="ec793-2918">fx_media_open</span></span>
- <span data-ttu-id="ec793-2919">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2919">fx_media_open_notify_set</span></span>
- <span data-ttu-id="ec793-2920">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-2920">fx_media_space_available</span></span>
- <span data-ttu-id="ec793-2921">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="ec793-2921">fx_media_volume_get</span></span>
- <span data-ttu-id="ec793-2922">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2922">fx_media_volume_set</span></span>
- <span data-ttu-id="ec793-2923">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="ec793-2923">fx_media_write</span></span>
- <span data-ttu-id="ec793-2924">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ec793-2924">fx_system_initialize</span></span>

## <a name="fx_media_space_available"></a><span data-ttu-id="ec793-2925">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-2925">fx_media_space_available</span></span>

<span data-ttu-id="ec793-2926">Возвращает доступное пространство на носителе</span><span class="sxs-lookup"><span data-stu-id="ec793-2926">Returns available media space</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-2927">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-2927">Prototype</span></span>

```c
UINT fx_media_space_available(
    FX_MEDIA *media_ptr,
    ULONG *available_bytes_ptr);
```

### <a name="description"></a><span data-ttu-id="ec793-2928">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-2928">Description</span></span>

<span data-ttu-id="ec793-2929">Эта служба возвращает число байтов, доступных на носителе.</span><span class="sxs-lookup"><span data-stu-id="ec793-2929">This service returns the number of bytes available in the media.</span></span>

<span data-ttu-id="ec793-2930">Для работы с носителями объемом более 4 ГБ приложение должно использовать службу *fx_media_extended_space_available*.</span><span class="sxs-lookup"><span data-stu-id="ec793-2930">To work with the media larger than 4GB, application shall use the service *fx_media_extended_space_available*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-2931">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-2931">Input Parameters</span></span>

- <span data-ttu-id="ec793-2932">**media_ptr**: указатель на открытый ранее носитель</span><span class="sxs-lookup"><span data-stu-id="ec793-2932">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="ec793-2933">**available_bytes_ptr**: число байтов, доступное на носителе</span><span class="sxs-lookup"><span data-stu-id="ec793-2933">**available_bytes_ptr**: Available bytes left in the media.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-2934">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-2934">Return Values</span></span>

- <span data-ttu-id="ec793-2935">**FX_SUCCESS** (0x00) — доступное место на носителе успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="ec793-2935">**FX_SUCCESS** (0x00) Successfully returned available space on media.</span></span>
- <span data-ttu-id="ec793-2936">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-2936">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="ec793-2937">**FX_PTR_ERROR** (0x18) — недопустимый указатель на носитель, или доступное количество байтов имеет значение NULL.</span><span class="sxs-lookup"><span data-stu-id="ec793-2937">**FX_PTR_ERROR** (0x18) Invalid media pointer or available bytes pointer is NULL.</span></span>
- <span data-ttu-id="ec793-2938">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-2938">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-2939">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-2939">Allowed From</span></span>

<span data-ttu-id="ec793-2940">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-2940">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-2941">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-2941">Example</span></span>

```c
FX_MEDIA        my_media;
ULONG            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a><span data-ttu-id="ec793-2942">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-2942">See Also</span></span>

- <span data-ttu-id="ec793-2943">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="ec793-2943">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="ec793-2944">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="ec793-2944">fx_media_abort</span></span>
- <span data-ttu-id="ec793-2945">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="ec793-2945">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="ec793-2946">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="ec793-2946">fx_media_check</span></span>
- <span data-ttu-id="ec793-2947">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="ec793-2947">fx_media_close</span></span>
- <span data-ttu-id="ec793-2948">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2948">fx_media_close_notify_set</span></span>
- <span data-ttu-id="ec793-2949">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="ec793-2949">fx_media_exFAT_format</span></span>
- <span data-ttu-id="ec793-2950">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-2950">fx_media_extended_space_available</span></span>
- <span data-ttu-id="ec793-2951">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="ec793-2951">fx_media_flush</span></span>
- <span data-ttu-id="ec793-2952">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="ec793-2952">fx_media_format</span></span>
- <span data-ttu-id="ec793-2953">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="ec793-2953">fx_media_open</span></span>
- <span data-ttu-id="ec793-2954">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2954">fx_media_open_notify_set</span></span>
- <span data-ttu-id="ec793-2955">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="ec793-2955">fx_media_read</span></span>
- <span data-ttu-id="ec793-2956">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="ec793-2956">fx_media_volume_get</span></span>
- <span data-ttu-id="ec793-2957">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2957">fx_media_volume_set</span></span>
- <span data-ttu-id="ec793-2958">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="ec793-2958">fx_media_write</span></span>
- <span data-ttu-id="ec793-2959">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ec793-2959">fx_system_initialize</span></span>

## <a name="fx_media_volume_get"></a><span data-ttu-id="ec793-2960">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="ec793-2960">fx_media_volume_get</span></span>

<span data-ttu-id="ec793-2961">Получает имя тома носителя</span><span class="sxs-lookup"><span data-stu-id="ec793-2961">Gets media volume name</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-2962">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-2962">Prototype</span></span>

```c
UINT fx_media_volume_get(
    FX_MEDIA *media_ptr,
    CHAR *volume_name,
    UINT volume_source);
```
### <a name="description"></a><span data-ttu-id="ec793-2963">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-2963">Description</span></span>

<span data-ttu-id="ec793-2964">Эта служба получает имя тома ранее открытого носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-2964">This service retrieves the volume name of the previously opened media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-2965">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-2965">Input Parameters</span></span>

- <span data-ttu-id="ec793-2966">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-2966">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="ec793-2967">**volume_name**: указатель на место назначения для имени тома</span><span class="sxs-lookup"><span data-stu-id="ec793-2967">**volume_name**: Pointer to destination for volume name.</span></span> <span data-ttu-id="ec793-2968">Обратите внимание, что место назначения должно быть как достаточно большим, чтобы вместить 12 символов.</span><span class="sxs-lookup"><span data-stu-id="ec793-2968">Note that the destination must be at least large enough to hold 12 characters.</span></span>
- <span data-ttu-id="ec793-2969">**volume_source**: указывает, где следует получить имя из загрузочного или корневого каталога</span><span class="sxs-lookup"><span data-stu-id="ec793-2969">**volume_source**: Designates where to retrieve the name, either from the boot sector or the root directory.</span></span> <span data-ttu-id="ec793-2970">Допустимые значения для этого параметра:</span><span class="sxs-lookup"><span data-stu-id="ec793-2970">Valid values for this parameter are:</span></span>
  - <span data-ttu-id="ec793-2971">FX_BOOT_SECTOR</span><span class="sxs-lookup"><span data-stu-id="ec793-2971">FX_BOOT_SECTOR</span></span>
  - <span data-ttu-id="ec793-2972">FX_DIRECTORY_SECTOR</span><span class="sxs-lookup"><span data-stu-id="ec793-2972">FX_DIRECTORY_SECTOR</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-2973">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-2973">Return Values</span></span>

- <span data-ttu-id="ec793-2974">**FX_SUCCESS** (0x00) — том носителя успешно получен.</span><span class="sxs-lookup"><span data-stu-id="ec793-2974">**FX_SUCCESS** (0x00) Successful media volume get.</span></span>
- <span data-ttu-id="ec793-2975">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-2975">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="ec793-2976">**FX_NOT_FOUND** (0x04) — том не найден.</span><span class="sxs-lookup"><span data-stu-id="ec793-2976">**FX_NOT_FOUND** (0x04) Volume not found.</span></span>
- <span data-ttu-id="ec793-2977">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-2977">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-2978">**FX_PTR_ERROR** (0x18) — недопустимый указатель места назначения носителя или тома.</span><span class="sxs-lookup"><span data-stu-id="ec793-2978">**FX_PTR_ERROR** (0x18) Invalid media or volume destination pointer.</span></span>
- <span data-ttu-id="ec793-2979">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-2979">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-2980">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-2980">Allowed From</span></span>

<span data-ttu-id="ec793-2981">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-2981">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-2982">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-2982">Example</span></span>

```c
FX_MEDIA        ram_disk;
UCHAR             volume_name[12];
/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name), FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */

```

### <a name="see-also"></a><span data-ttu-id="ec793-2983">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-2983">See Also</span></span>

- <span data-ttu-id="ec793-2984">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="ec793-2984">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="ec793-2985">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="ec793-2985">fx_media_abort</span></span>
- <span data-ttu-id="ec793-2986">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="ec793-2986">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="ec793-2987">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="ec793-2987">fx_media_check</span></span>
- <span data-ttu-id="ec793-2988">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="ec793-2988">fx_media_close</span></span>
- <span data-ttu-id="ec793-2989">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2989">fx_media_close_notify_set</span></span>
- <span data-ttu-id="ec793-2990">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="ec793-2990">fx_media_exFAT_format</span></span>
- <span data-ttu-id="ec793-2991">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-2991">fx_media_extended_space_available</span></span>
- <span data-ttu-id="ec793-2992">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="ec793-2992">fx_media_flush</span></span>
- <span data-ttu-id="ec793-2993">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="ec793-2993">fx_media_format</span></span>
- <span data-ttu-id="ec793-2994">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="ec793-2994">fx_media_open</span></span>
- <span data-ttu-id="ec793-2995">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2995">fx_media_open_notify_set</span></span>
- <span data-ttu-id="ec793-2996">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="ec793-2996">fx_media_read</span></span>
- <span data-ttu-id="ec793-2997">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-2997">fx_media_space_available</span></span>
- <span data-ttu-id="ec793-2998">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="ec793-2998">fx_media_volume_set</span></span>
- <span data-ttu-id="ec793-2999">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="ec793-2999">fx_media_write</span></span>
- <span data-ttu-id="ec793-3000">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ec793-3000">fx_system_initialize</span></span>

## <a name="fx_media_volume_get_extended"></a><span data-ttu-id="ec793-3001">fx_media_volume_get_extended</span><span class="sxs-lookup"><span data-stu-id="ec793-3001">fx_media_volume_get_extended</span></span>

<span data-ttu-id="ec793-3002">Получает имя тома ранее открытого носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-3002">Gets media volume name of previously opened media</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-3003">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-3003">Prototype</span></span>

```c
UINT fx_media_volume_get_extended(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name,
    UINT volume_name_buffer_length,
    UINT volume_source);
```
### <a name="description"></a><span data-ttu-id="ec793-3004">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-3004">Description</span></span>

<span data-ttu-id="ec793-3005">Эта служба получает имя тома ранее открытого носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-3005">This service retrieves the volume name of the previously opened media.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec793-3006">Эта служба идентична \***fx_media_volume_get()** _, за исключением того, что вызывающий объект передает размер буфера _ \*volume_name\*\*.</span><span class="sxs-lookup"><span data-stu-id="ec793-3006">This service is identical to ***fx_media_volume_get()** _ except the caller passes in the size of the _ *volume_name** buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-3007">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-3007">Input Parameters</span></span>


- <span data-ttu-id="ec793-3008">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-3008">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="ec793-3009">**volume_name**: указатель на место назначения для имени тома</span><span class="sxs-lookup"><span data-stu-id="ec793-3009">**volume_name**: Pointer to destination for volume name.</span></span> <span data-ttu-id="ec793-3010">Обратите внимание, что место назначения должно быть как достаточно большим, чтобы вместить 12 символов.</span><span class="sxs-lookup"><span data-stu-id="ec793-3010">Note that the destination must be at least large enough to hold 12 characters.</span></span>
- <span data-ttu-id="ec793-3011">**volume_name_buffer_length**: размер буфера volume_name</span><span class="sxs-lookup"><span data-stu-id="ec793-3011">**volume_name_buffer_length**: Size of volume_name buffer.</span></span>
- <span data-ttu-id="ec793-3012">**volume_source**: указывает, где следует получить имя из загрузочного или корневого каталога</span><span class="sxs-lookup"><span data-stu-id="ec793-3012">**volume_source**: Designates where to retrieve the name, either from the boot sector or the root directory.</span></span> <span data-ttu-id="ec793-3013">Допустимые значения для этого параметра:</span><span class="sxs-lookup"><span data-stu-id="ec793-3013">Valid values for this parameter are:</span></span>
  - <span data-ttu-id="ec793-3014">FX_BOOT_SECTOR</span><span class="sxs-lookup"><span data-stu-id="ec793-3014">FX_BOOT_SECTOR</span></span>
  - <span data-ttu-id="ec793-3015">FX_DIRECTORY_SECTOR</span><span class="sxs-lookup"><span data-stu-id="ec793-3015">FX_DIRECTORY_SECTOR</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-3016">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-3016">Return Values</span></span>

- <span data-ttu-id="ec793-3017">**FX_SUCCESS** (0x00) — том носителя успешно получен.</span><span class="sxs-lookup"><span data-stu-id="ec793-3017">**FX_SUCCESS** (0x00) Successful media volume get.</span></span>
- <span data-ttu-id="ec793-3018">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-3018">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="ec793-3019">**FX_NOT_FOUND** (0x04) — том не найден.</span><span class="sxs-lookup"><span data-stu-id="ec793-3019">**FX_NOT_FOUND** (0x04) Volume not found.</span></span>
- <span data-ttu-id="ec793-3020">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-3020">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-3021">**FX_PTR_ERROR** (0x18) — недопустимый указатель места назначения носителя или тома.</span><span class="sxs-lookup"><span data-stu-id="ec793-3021">**FX_PTR_ERROR** (0x18) Invalid media or volume destination pointer.</span></span>
- <span data-ttu-id="ec793-3022">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-3022">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-3023">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-3023">Allowed From</span></span>

<span data-ttu-id="ec793-3024">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-3024">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-3025">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-3025">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             volume_name[12];

/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name),
                                      FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ec793-3026">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-3026">See Also</span></span>

- <span data-ttu-id="ec793-3027">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="ec793-3027">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="ec793-3028">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="ec793-3028">fx_media_abort</span></span>
- <span data-ttu-id="ec793-3029">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="ec793-3029">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="ec793-3030">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="ec793-3030">fx_media_check</span></span>
- <span data-ttu-id="ec793-3031">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="ec793-3031">fx_media_close</span></span>
- <span data-ttu-id="ec793-3032">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3032">fx_media_close_notify_set</span></span>
- <span data-ttu-id="ec793-3033">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="ec793-3033">fx_media_exFAT_format</span></span>
- <span data-ttu-id="ec793-3034">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-3034">fx_media_extended_space_available</span></span>
- <span data-ttu-id="ec793-3035">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="ec793-3035">fx_media_flush</span></span>
- <span data-ttu-id="ec793-3036">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="ec793-3036">fx_media_format</span></span>
- <span data-ttu-id="ec793-3037">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="ec793-3037">fx_media_open</span></span>
- <span data-ttu-id="ec793-3038">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3038">fx_media_open_notify_set</span></span>
- <span data-ttu-id="ec793-3039">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="ec793-3039">fx_media_read</span></span>
- <span data-ttu-id="ec793-3040">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-3040">fx_media_space_available</span></span>
- <span data-ttu-id="ec793-3041">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3041">fx_media_volume_set</span></span>
- <span data-ttu-id="ec793-3042">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="ec793-3042">fx_media_write</span></span>
- <span data-ttu-id="ec793-3043">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ec793-3043">fx_system_initialize</span></span>

## <a name="fx_media_volume_set"></a><span data-ttu-id="ec793-3044">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3044">fx_media_volume_set</span></span>

<span data-ttu-id="ec793-3045">Задает имя тома носителя</span><span class="sxs-lookup"><span data-stu-id="ec793-3045">Sets media volume name</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-3046">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-3046">Prototype</span></span>

```c
UINT fx_media_volume_set(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name);
```
### <a name="description"></a><span data-ttu-id="ec793-3047">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-3047">Description</span></span>

<span data-ttu-id="ec793-3048">Эта служба задает имя тома для ранее открытого носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-3048">This service sets the volume name of the previously opened media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-3049">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-3049">Input Parameters</span></span>

- <span data-ttu-id="ec793-3050">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-3050">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="ec793-3051">**volume_name**: указатель на имя тома</span><span class="sxs-lookup"><span data-stu-id="ec793-3051">**volume_name**: Pointer to the volume name.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-3052">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-3052">Return Values</span></span>

- <span data-ttu-id="ec793-3053">**FX_SUCCESS** (0x00) — том носителя успешно задан.</span><span class="sxs-lookup"><span data-stu-id="ec793-3053">**FX_SUCCESS** (0x00) Successful media volume set.</span></span>
- <span data-ttu-id="ec793-3054">**FX_INVALID_NAME** (0x0C) — недопустимый параметр volume_name.</span><span class="sxs-lookup"><span data-stu-id="ec793-3054">**FX_INVALID_NAME** (0x0C) Volume_name is invalid.</span></span>
- <span data-ttu-id="ec793-3055">**FX_MEDIA_INVALID** (0x02) — не удается задать имя тома.</span><span class="sxs-lookup"><span data-stu-id="ec793-3055">**FX_MEDIA_INVALID** (0x02) Unable to set volume name.</span></span>
- <span data-ttu-id="ec793-3056">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-3056">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="ec793-3057">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-3057">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-3058">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-3058">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="ec793-3059">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени тома.</span><span class="sxs-lookup"><span data-stu-id="ec793-3059">**FX_PTR_ERROR** (0x18) Invalid media or volume name pointer.</span></span>
- <span data-ttu-id="ec793-3060">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-3060">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-3061">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-3061">Allowed From</span></span>

<span data-ttu-id="ec793-3062">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-3062">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-3063">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-3063">Example</span></span>

```c
FX_MEDIA ram_disk;

/* Set the volume name to "MY_VOLUME". */

status = fx_media_volume_set(&ram_disk, "MY_VOLUME");

/* If status is FX_SUCCESS, the volume name was successfully set. */
```

### <a name="see-also"></a><span data-ttu-id="ec793-3064">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-3064">See Also</span></span>

- <span data-ttu-id="ec793-3065">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="ec793-3065">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="ec793-3066">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="ec793-3066">fx_media_abort</span></span>
- <span data-ttu-id="ec793-3067">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="ec793-3067">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="ec793-3068">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="ec793-3068">fx_media_check</span></span>
- <span data-ttu-id="ec793-3069">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="ec793-3069">fx_media_close</span></span>
- <span data-ttu-id="ec793-3070">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3070">fx_media_close_notify_set</span></span>
- <span data-ttu-id="ec793-3071">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="ec793-3071">fx_media_exFAT_format</span></span>
- <span data-ttu-id="ec793-3072">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-3072">fx_media_extended_space_available</span></span>
- <span data-ttu-id="ec793-3073">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="ec793-3073">fx_media_flush</span></span>
- <span data-ttu-id="ec793-3074">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="ec793-3074">fx_media_format</span></span>
- <span data-ttu-id="ec793-3075">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="ec793-3075">fx_media_open</span></span>
- <span data-ttu-id="ec793-3076">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3076">fx_media_open_notify_set</span></span>
- <span data-ttu-id="ec793-3077">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="ec793-3077">fx_media_read</span></span>
- <span data-ttu-id="ec793-3078">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-3078">fx_media_space_available</span></span>
- <span data-ttu-id="ec793-3079">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3079">fx_media_volume_get</span></span>
- <span data-ttu-id="ec793-3080">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="ec793-3080">fx_media_write</span></span>
- <span data-ttu-id="ec793-3081">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ec793-3081">fx_system_initialize</span></span>

## <a name="fx_media_write"></a><span data-ttu-id="ec793-3082">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="ec793-3082">fx_media_write</span></span>

<span data-ttu-id="ec793-3083">Записывает логический сектор</span><span class="sxs-lookup"><span data-stu-id="ec793-3083">Writes logical sector</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-3084">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-3084">Prototype</span></span>

```c
UINT fx_media_write(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector,
    VOID *buffer_ptr);
```
### <a name="description"></a><span data-ttu-id="ec793-3085">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-3085">Description</span></span>

<span data-ttu-id="ec793-3086">Эта служба записывает указанный буфер в указанный логический сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-3086">This service writes the supplied buffer to the specified logical sector.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-3087">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-3087">Input Parameters</span></span>

- <span data-ttu-id="ec793-3088">**media_ptr**: указатель на открытый ранее носитель</span><span class="sxs-lookup"><span data-stu-id="ec793-3088">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="ec793-3089">**logical_sector**: логический сектор для записи</span><span class="sxs-lookup"><span data-stu-id="ec793-3089">**logical_sector**: Logical sector to write.</span></span>
- <span data-ttu-id="ec793-3090">**buffer_ptr**: указатель на источник для записи логического сектора</span><span class="sxs-lookup"><span data-stu-id="ec793-3090">**buffer_ptr**: Pointer to the source for the logical sector write.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-3091">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-3091">Return Values</span></span>

- <span data-ttu-id="ec793-3092">**FX_SUCCESS** (0x00) — запись на носитель успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="ec793-3092">**FX_SUCCESS** (0x00) Successful media write.</span></span>
- <span data-ttu-id="ec793-3093">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-3093">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="ec793-3094">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-3094">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="ec793-3095">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-3095">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-3096">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-3096">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="ec793-3097">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.</span><span class="sxs-lookup"><span data-stu-id="ec793-3097">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="ec793-3098">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-3098">**FX_CALLER_ERROR**    (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-3099">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-3099">Allowed From</span></span>

<span data-ttu-id="ec793-3100">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-3100">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-3101">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-3101">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="ec793-3102">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-3102">See Also</span></span>

- <span data-ttu-id="ec793-3103">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="ec793-3103">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="ec793-3104">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="ec793-3104">fx_media_abort</span></span>
- <span data-ttu-id="ec793-3105">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="ec793-3105">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="ec793-3106">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="ec793-3106">fx_media_check</span></span>
- <span data-ttu-id="ec793-3107">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="ec793-3107">fx_media_close</span></span>
- <span data-ttu-id="ec793-3108">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3108">fx_media_close_notify_set</span></span>
- <span data-ttu-id="ec793-3109">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="ec793-3109">fx_media_exFAT_format</span></span>
- <span data-ttu-id="ec793-3110">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-3110">fx_media_extended_space_available</span></span>
- <span data-ttu-id="ec793-3111">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="ec793-3111">fx_media_flush</span></span>
- <span data-ttu-id="ec793-3112">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="ec793-3112">fx_media_format</span></span>
- <span data-ttu-id="ec793-3113">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="ec793-3113">fx_media_open</span></span>
- <span data-ttu-id="ec793-3114">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3114">fx_media_open_notify_set</span></span>
- <span data-ttu-id="ec793-3115">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="ec793-3115">fx_media_read</span></span>
- <span data-ttu-id="ec793-3116">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="ec793-3116">fx_media_space_available</span></span>
- <span data-ttu-id="ec793-3117">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3117">fx_media_volume_get</span></span>
- <span data-ttu-id="ec793-3118">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3118">fx_media_volume_set</span></span>
- <span data-ttu-id="ec793-3119">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ec793-3119">fx_system_initialize</span></span>

## <a name="fx_system_date_get"></a><span data-ttu-id="ec793-3120">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3120">fx_system_date_get</span></span>

<span data-ttu-id="ec793-3121">Возвращает дату файловой системы</span><span class="sxs-lookup"><span data-stu-id="ec793-3121">Gets file system date</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-3122">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-3122">Prototype</span></span>

```c
UINT fx_system_date_get(
    UINT *year, 
    UINT *month, 
    UINT *day);
```
### <a name="description"></a><span data-ttu-id="ec793-3123">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-3123">Description</span></span>

<span data-ttu-id="ec793-3124">Эта служба возвращает текущую системную дату.</span><span class="sxs-lookup"><span data-stu-id="ec793-3124">This service returns the current system date.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-3125">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-3125">Input Parameters</span></span>

- <span data-ttu-id="ec793-3126">**year**: указатель на назначение для года</span><span class="sxs-lookup"><span data-stu-id="ec793-3126">**year**: Pointer to destination for year.</span></span>
- <span data-ttu-id="ec793-3127">**month**: указатель на назначение для месяца</span><span class="sxs-lookup"><span data-stu-id="ec793-3127">**month**: Pointer to destination for month.</span></span>
- <span data-ttu-id="ec793-3128">**day**: указатель на назначение для дня</span><span class="sxs-lookup"><span data-stu-id="ec793-3128">**day**: Pointer to destination for day.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-3129">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-3129">Return Values</span></span>

- <span data-ttu-id="ec793-3130">**FX_SUCCESS** (0x00) — дата успешно получена.</span><span class="sxs-lookup"><span data-stu-id="ec793-3130">**FX_SUCCESS** (0x00) Successful date retrieval.</span></span>
- <span data-ttu-id="ec793-3131">**FX_PTR_ERROR** (0x18) — один входной параметр ил несколько имеют значение NULL.</span><span class="sxs-lookup"><span data-stu-id="ec793-3131">**FX_PTR_ERROR** (0x18) One or more of the input parameters are NULL.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-3132">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-3132">Allowed From</span></span>

<span data-ttu-id="ec793-3133">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-3133">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-3134">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-3134">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="ec793-3135">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-3135">See Also</span></span>

- <span data-ttu-id="ec793-3136">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3136">fx_system_date_set</span></span>
- <span data-ttu-id="ec793-3137">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ec793-3137">fx_system_initialize</span></span>
- <span data-ttu-id="ec793-3138">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3138">fx_system_time_get</span></span>
- <span data-ttu-id="ec793-3139">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3139">fx_system_time_set</span></span>

## <a name="fx_system_date_set"></a><span data-ttu-id="ec793-3140">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3140">fx_system_date_set</span></span>

<span data-ttu-id="ec793-3141">Задает системную дату</span><span class="sxs-lookup"><span data-stu-id="ec793-3141">Sets system date</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-3142">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-3142">Prototype</span></span>

```c
UINT fx_system_date_set(
    UINT year, 
    UINT month, 
    UINT day);
```

### <a name="description"></a><span data-ttu-id="ec793-3143">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-3143">Description</span></span>

<span data-ttu-id="ec793-3144">Эта служба задает системную дату указанным образом.</span><span class="sxs-lookup"><span data-stu-id="ec793-3144">This service sets the system date as specified.</span></span>

> [!WARNING]
> <span data-ttu-id="ec793-3145">*Эту службу следует вызывать вскоре после **fx_system_initialize** для задания начальной системной даты. По умолчанию системная дата является датой последнего общего выпуска FileX.*</span><span class="sxs-lookup"><span data-stu-id="ec793-3145">*This service should be called shortly after **fx_system_initialize** to set the initial system date. By default, the system date is that of the last generic FileX release.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-3146">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-3146">Input Parameters</span></span>

- <span data-ttu-id="ec793-3147">**year**: новый год</span><span class="sxs-lookup"><span data-stu-id="ec793-3147">**year**: New year.</span></span> <span data-ttu-id="ec793-3148">Допустимый диапазон — от 1980 до 2107.</span><span class="sxs-lookup"><span data-stu-id="ec793-3148">The valid range is from 1980 through the year 2107.</span></span>
- <span data-ttu-id="ec793-3149">**month**: новый месяц</span><span class="sxs-lookup"><span data-stu-id="ec793-3149">**month**: New month.</span></span> <span data-ttu-id="ec793-3150">Допустимый диапазон — от 1 до 12.</span><span class="sxs-lookup"><span data-stu-id="ec793-3150">The valid range is from 1 through 12.</span></span>
- <span data-ttu-id="ec793-3151">**day**: новый день</span><span class="sxs-lookup"><span data-stu-id="ec793-3151">**day**: New day.</span></span> <span data-ttu-id="ec793-3152">Допустимый диапазон — от 1 до 31 (в зависимости от месяца и високосного года).</span><span class="sxs-lookup"><span data-stu-id="ec793-3152">The valid range is from 1 through 31, depending on month and leap year conditions.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-3153">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-3153">Return Values</span></span>

- <span data-ttu-id="ec793-3154">**FX_SUCCESS** (0x00) — дата успешно задана.</span><span class="sxs-lookup"><span data-stu-id="ec793-3154">**FX_SUCCESS** (0x00) Successful date setting.</span></span>
- <span data-ttu-id="ec793-3155">**FX_INVALID_YEAR** (0x12) — указан недопустимый год.</span><span class="sxs-lookup"><span data-stu-id="ec793-3155">**FX_INVALID_YEAR** (0x12) Invalid year specified.</span></span>
- <span data-ttu-id="ec793-3156">**FX_INVALID_MONTH** (0x13) — указан недопустимый месяц.</span><span class="sxs-lookup"><span data-stu-id="ec793-3156">**FX_INVALID_MONTH** (0x13) Invalid month specified.</span></span>
- <span data-ttu-id="ec793-3157">**FX_INVALID_DAY** (0x14) — указан недопустимый день.</span><span class="sxs-lookup"><span data-stu-id="ec793-3157">**FX_INVALID_DAY** (0x14) Invalid day specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-3158">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-3158">Allowed From</span></span>

<span data-ttu-id="ec793-3159">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-3159">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-3160">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-3160">Example</span></span>

```c
 UINT             status;

/* Set the system date to December 12, 2005. */

status = fx_system_date_set(2005, 12, 12);

/* If status equals FX_SUCCESS, the file system date is now
    12-12-2005. */
```

### <a name="see-also"></a><span data-ttu-id="ec793-3161">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-3161">See Also</span></span>

- <span data-ttu-id="ec793-3162">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3162">fx_system_date_get</span></span>
- <span data-ttu-id="ec793-3163">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ec793-3163">fx_system_initialize</span></span>
- <span data-ttu-id="ec793-3164">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3164">fx_system_time_get</span></span>
- <span data-ttu-id="ec793-3165">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3165">fx_system_time_set</span></span>

## <a name="fx_system_initialize"></a><span data-ttu-id="ec793-3166">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ec793-3166">fx_system_initialize</span></span>

<span data-ttu-id="ec793-3167">Инициализирует всю систему</span><span class="sxs-lookup"><span data-stu-id="ec793-3167">Initializes entire system</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-3168">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-3168">Prototype</span></span>

```c
VOID fx_system_initialize(void);
```

### <a name="description"></a><span data-ttu-id="ec793-3169">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-3169">Description</span></span>

<span data-ttu-id="ec793-3170">Эта служба инициализирует все основные структуры данных FileX.</span><span class="sxs-lookup"><span data-stu-id="ec793-3170">This service initializes all the major FileX data structures.</span></span> <span data-ttu-id="ec793-3171">Следует вызывать либо в ***tx_application_define***, либо, возможно, из потока инициализации, а также следует вызывать перед использованием любой другой службы FileX.</span><span class="sxs-lookup"><span data-stu-id="ec793-3171">It should be called either in ***tx_application_define*** or possibly from an initialization thread and must be called prior to using any other FileX service.</span></span>

> [!WARNING]
> <span data-ttu-id="ec793-3172">\*После инициализации этим вызовом приложение должно вызвать \***fx_system_date_set** _ и _ *fx_system_time_set\*\*, чтобы начать с точных системных даты и времени.*</span><span class="sxs-lookup"><span data-stu-id="ec793-3172">*Once initialized by this call, the application should call ***fx_system_date_set** _ and _ *fx_system_time_set** to start with an accurate system date and time.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-3173">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-3173">Input Parameters</span></span>

<span data-ttu-id="ec793-3174">Нет</span><span class="sxs-lookup"><span data-stu-id="ec793-3174">None</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-3175">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-3175">Return Values</span></span>

<span data-ttu-id="ec793-3176">Нет.</span><span class="sxs-lookup"><span data-stu-id="ec793-3176">None.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-3177">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-3177">Allowed From</span></span>

<span data-ttu-id="ec793-3178">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-3178">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-3179">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-3179">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="ec793-3180">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-3180">See Also</span></span>

- <span data-ttu-id="ec793-3181">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3181">fx_system_date_get</span></span>
- <span data-ttu-id="ec793-3182">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3182">fx_system_date_set</span></span>
- <span data-ttu-id="ec793-3183">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3183">fx_system_time_get</span></span>
- <span data-ttu-id="ec793-3184">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3184">fx_system_time_set</span></span>

## <a name="fx_system_time_get"></a><span data-ttu-id="ec793-3185">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3185">fx_system_time_get</span></span>

<span data-ttu-id="ec793-3186">Получает текущее системное время</span><span class="sxs-lookup"><span data-stu-id="ec793-3186">Gets current system time</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-3187">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-3187">Prototype</span></span>

```c
UINT fx_system_time_get(
    UINT *hour,
    UINT *minute,
    UINT *second);
```

### <a name="description"></a><span data-ttu-id="ec793-3188">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-3188">Description</span></span>

<span data-ttu-id="ec793-3189">Эта служба получает текущее системное время.</span><span class="sxs-lookup"><span data-stu-id="ec793-3189">This service retrieves the current system time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-3190">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-3190">Input Parameters</span></span>

- <span data-ttu-id="ec793-3191">**hour**: указатель на назначение для часа</span><span class="sxs-lookup"><span data-stu-id="ec793-3191">**hour**: Pointer to destination for hour.</span></span>
- <span data-ttu-id="ec793-3192">**minute**: указатель на назначение для минуты</span><span class="sxs-lookup"><span data-stu-id="ec793-3192">**minute**: Pointer to destination for minute.</span></span>
- <span data-ttu-id="ec793-3193">**second**: указатель на назначение для секунды</span><span class="sxs-lookup"><span data-stu-id="ec793-3193">**second**: Pointer to destination for second.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-3194">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-3194">Return Values</span></span>

- <span data-ttu-id="ec793-3195">**FX_SUCCESS** (0x00) — системное время успешно получено.</span><span class="sxs-lookup"><span data-stu-id="ec793-3195">**FX_SUCCESS** (0x00) Successful system time retrieval.</span></span>
- <span data-ttu-id="ec793-3196">**FX_PTR_ERROR** (0x18) — один входной параметр или несколько.</span><span class="sxs-lookup"><span data-stu-id="ec793-3196">**FX_PTR_ERROR** (0x18) One or more of the input parameters</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-3197">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-3197">Allowed From</span></span>

<span data-ttu-id="ec793-3198">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-3198">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-3199">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-3199">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="ec793-3200">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-3200">See Also</span></span>

- <span data-ttu-id="ec793-3201">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3201">fx_system_date_get</span></span>
- <span data-ttu-id="ec793-3202">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3202">fx_system_date_set</span></span>
- <span data-ttu-id="ec793-3203">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ec793-3203">fx_system_initialize</span></span>
- <span data-ttu-id="ec793-3204">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3204">fx_system_time_set</span></span>

## <a name="fx_system_time_set"></a><span data-ttu-id="ec793-3205">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3205">fx_system_time_set</span></span>

<span data-ttu-id="ec793-3206">Задает текущее системное время</span><span class="sxs-lookup"><span data-stu-id="ec793-3206">Sets current system time</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-3207">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-3207">Prototype</span></span>

```c
UINT fx_system_time_set(UINT hour, UINT minute, UINT second);
```

### <a name="description"></a><span data-ttu-id="ec793-3208">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-3208">Description</span></span>

<span data-ttu-id="ec793-3209">Эта служба задает текущее системное время в соответствии с заданными входными параметрами.</span><span class="sxs-lookup"><span data-stu-id="ec793-3209">This service sets the current system time to that specified by the input parameters.</span></span>

> [!WARNING]
> <span data-ttu-id="ec793-3210">*Эту службу следует вызывать вскоре после **fx_system_initialize** для задания начального системного времени. По умолчанию системным временем является 0:0:0.*</span><span class="sxs-lookup"><span data-stu-id="ec793-3210">*This service should be called shortly after **fx_system_initialize** to set the initial system time. By default, the system time is 0:0:0.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-3211">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-3211">Input Parameters</span></span>

- <span data-ttu-id="ec793-3212">**hour**: новый час (0–23)</span><span class="sxs-lookup"><span data-stu-id="ec793-3212">**hour**: New hour (0-23).</span></span>
- <span data-ttu-id="ec793-3213">**minute**: новая минута (0–59)</span><span class="sxs-lookup"><span data-stu-id="ec793-3213">**minute**: New minute (0-59).</span></span>
- <span data-ttu-id="ec793-3214">**second**: новая секунда (0–59)</span><span class="sxs-lookup"><span data-stu-id="ec793-3214">**second**: New second (0-59).</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-3215">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-3215">Return Values</span></span>

- <span data-ttu-id="ec793-3216">**FX_SUCCESS** (0x00) — системное время успешно получено.</span><span class="sxs-lookup"><span data-stu-id="ec793-3216">**FX_SUCCESS** (0x00) Successful system time retrieval.</span></span>
- <span data-ttu-id="ec793-3217">**FX_INVALID_HOUR** (0x15) — недопустимый новый час.</span><span class="sxs-lookup"><span data-stu-id="ec793-3217">**FX_INVALID_HOUR**    (0x15) New hour is invalid.</span></span>
- <span data-ttu-id="ec793-3218">**FX_INVALID_MINUTE** (0x16) — недопустимая новая минута.</span><span class="sxs-lookup"><span data-stu-id="ec793-3218">**FX_INVALID_MINUTE** (0x16) New minute is invalid.</span></span>
- <span data-ttu-id="ec793-3219">**FX_INVALID_SECOND** (0x17) — недопустимая новая секунда.</span><span class="sxs-lookup"><span data-stu-id="ec793-3219">**FX_INVALID_SECOND** (0x17) New second is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-3220">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-3220">Allowed From</span></span>

<span data-ttu-id="ec793-3221">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-3221">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-3222">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-3222">Example</span></span>

```c
 UINT status;

/* Set the current system time to hour 23, minute 21, and second 20. */

status = fx_system_time_set(23, 21, 20);

/* If status is FX_SUCCESS, the current system time has been set. */
```

### <a name="see-also"></a><span data-ttu-id="ec793-3223">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-3223">See Also</span></span>

- <span data-ttu-id="ec793-3224">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3224">fx_system_date_get</span></span>
- <span data-ttu-id="ec793-3225">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3225">fx_system_date_set</span></span>
- <span data-ttu-id="ec793-3226">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ec793-3226">fx_system_initialize</span></span>
- <span data-ttu-id="ec793-3227">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3227">fx_system_time_get</span></span>

## <a name="fx_unicode_directory_create"></a><span data-ttu-id="ec793-3228">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-3228">fx_unicode_directory_create</span></span>

<span data-ttu-id="ec793-3229">Создает каталог Юникода</span><span class="sxs-lookup"><span data-stu-id="ec793-3229">Creates a Unicode directory</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-3230">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-3230">Prototype</span></span>

```c
UINT fx_unicode_directory_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```
### <a name="description"></a><span data-ttu-id="ec793-3231">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-3231">Description</span></span>

<span data-ttu-id="ec793-3232">Эта служба создает подкаталог с именем в Юникоде в текущем каталоге по умолчанию — в параметре имени источника в Юникоде не допускаются сведения о пути.</span><span class="sxs-lookup"><span data-stu-id="ec793-3232">This service creates a Unicode-named subdirectory in the current default directory—no path information is allowed in the Unicode source name parameter.</span></span> <span data-ttu-id="ec793-3233">В случае успешного выполнения служба возвращает короткое имя (формат 8.3) только что созданного подкаталога Юникода.</span><span class="sxs-lookup"><span data-stu-id="ec793-3233">If successful, the short name (8.3 format) of the newly created Unicode subdirectory is returned by the service.</span></span>

> [!WARNING]
> <span data-ttu-id="ec793-3234">*Все операции в подкаталоге Юникода (выбор в качестве пути по умолчанию, удаление и т. д.) должны выполняться путем предоставления возвращенного краткого имени (формат 8.3) стандартным службам каталогов FileX.*</span><span class="sxs-lookup"><span data-stu-id="ec793-3234">*All operations on the Unicode subdirectory (making it the default path, deleting, etc.) should be done by supplying the returned short name (8.3 format) to the standard FileX directory services.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec793-3235">*Эта служба не поддерживается на носителях exFAT.*</span><span class="sxs-lookup"><span data-stu-id="ec793-3235">*This service is not supported on exFAT media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-3236">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-3236">Input Parameters</span></span>

- <span data-ttu-id="ec793-3237">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-3237">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="ec793-3238">**source_unicode_name**: указатель на имя в Юникоде для нового подкаталога</span><span class="sxs-lookup"><span data-stu-id="ec793-3238">**source_unicode_name**: Pointer to the Unicode name for the new subdirectory.</span></span>
- <span data-ttu-id="ec793-3239">**source_unicode_length**: длина имени в Юникоде</span><span class="sxs-lookup"><span data-stu-id="ec793-3239">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="ec793-3240">**short_name**: указатель на назначение для краткого имени (формат 8.3) для нового подкаталога Юникода</span><span class="sxs-lookup"><span data-stu-id="ec793-3240">**short_name**: Pointer to destination for short name (8.3 format) for the new Unicode subdirectory.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-3241">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-3241">Return Values</span></span>

- <span data-ttu-id="ec793-3242">**FX_SUCCESS** (0x00) — каталог Юникода успешно задан.</span><span class="sxs-lookup"><span data-stu-id="ec793-3242">**FX_SUCCESS** (0x00) Successful Unicode directory create.</span></span>
- <span data-ttu-id="ec793-3243">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-3243">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="ec793-3244">**FX_ALREADY_CREATED** (0x0B) — указанный каталог уже существует.</span><span class="sxs-lookup"><span data-stu-id="ec793-3244">**FX_ALREADY_CREATED** (0x0B) Specified directory already exists.</span></span>
- <span data-ttu-id="ec793-3245">**FX_NO_MORE_SPACE** (0x0A) — на носителе больше нет доступных кластеров для новой записи каталога.</span><span class="sxs-lookup"><span data-stu-id="ec793-3245">**FX_NO_MORE_SPACE** (0x0A) No more clusters available in the media for the new directory entry.</span></span>
- <span data-ttu-id="ec793-3246">**FX_NOT_IMPLEMENTED** (0x22) — служба не реализована для файловой системы exFAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-3246">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="ec793-3247">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-3247">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="ec793-3248">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.</span><span class="sxs-lookup"><span data-stu-id="ec793-3248">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="ec793-3249">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-3249">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>
- <span data-ttu-id="ec793-3250">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-3250">**FX_IO_ERROR    (0x90)** Driver I/O error.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-3251">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-3251">Allowed From</span></span>

<span data-ttu-id="ec793-3252">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-3252">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-3253">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-3253">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="ec793-3254">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-3254">See Also</span></span>

- <span data-ttu-id="ec793-3255">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-3255">fx_directory_attributes_read</span></span>
- <span data-ttu-id="ec793-3256">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3256">fx_directory_attributes_set</span></span>
- <span data-ttu-id="ec793-3257">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-3257">fx_directory_create</span></span>
- <span data-ttu-id="ec793-3258">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3258">fx_directory_default_get</span></span>
- <span data-ttu-id="ec793-3259">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3259">fx_directory_default_set</span></span>
- <span data-ttu-id="ec793-3260">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-3260">fx_directory_delete</span></span>
- <span data-ttu-id="ec793-3261">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-3261">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="ec793-3262">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-3262">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="ec793-3263">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3263">fx_directory_information_get</span></span>
- <span data-ttu-id="ec793-3264">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="ec793-3264">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="ec793-3265">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3265">fx_directory_local_path_get</span></span>
- <span data-ttu-id="ec793-3266">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="ec793-3266">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="ec793-3267">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3267">fx_directory_local_path_set</span></span>
- <span data-ttu-id="ec793-3268">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3268">fx_directory_long_name_get</span></span>
- <span data-ttu-id="ec793-3269">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="ec793-3269">fx_directory_name_test</span></span>
- <span data-ttu-id="ec793-3270">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-3270">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="ec793-3271">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-3271">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="ec793-3272">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-3272">fx_directory_rename</span></span>
- <span data-ttu-id="ec793-3273">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3273">fx_directory_short_name_get</span></span>
- <span data-ttu-id="ec793-3274">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-3274">fx_unicode_directory_rename</span></span>

## <a name="fx_unicode_directory_rename"></a><span data-ttu-id="ec793-3275">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-3275">fx_unicode_directory_rename</span></span>

<span data-ttu-id="ec793-3276">Переименовывает каталог, используя строку в Юникоде</span><span class="sxs-lookup"><span data-stu-id="ec793-3276">Renames directory using Unicode string</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-3277">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-3277">Prototype</span></span>

```c
UINT fx_unicode_directory_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length,
    CHAR *new_short_name);
```
### <a name="description"></a><span data-ttu-id="ec793-3278">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-3278">Description</span></span>

<span data-ttu-id="ec793-3279">Эта служба изменяет подкаталог с именем в Юникоде на указанное новое имя в Юникоде в текущем рабочем каталоге.</span><span class="sxs-lookup"><span data-stu-id="ec793-3279">This service changes a Unicode-named subdirectory to specified new Unicode name in current working directory.</span></span> <span data-ttu-id="ec793-3280">Параметры имени в Юникоде не должны содержать сведения о пути.</span><span class="sxs-lookup"><span data-stu-id="ec793-3280">The Unicode name parameters must not have path information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec793-3281">*Эта служба не поддерживается на носителях exFAT.*</span><span class="sxs-lookup"><span data-stu-id="ec793-3281">*This service is not supported on exFAT media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-3282">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-3282">Input Parameters</span></span>

- <span data-ttu-id="ec793-3283">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-3283">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="ec793-3284">**old_unicode_name**: указатель на имя в Юникоде для текущего файла</span><span class="sxs-lookup"><span data-stu-id="ec793-3284">**old_unicode_name**: Pointer to the Unicode name for the current file.</span></span>
- <span data-ttu-id="ec793-3285">**old_unicode_name_length**: длина текущего имени в Юникоде</span><span class="sxs-lookup"><span data-stu-id="ec793-3285">**old_unicode_name_length**: Length of current Unicode name.</span></span>
- <span data-ttu-id="ec793-3286">**new_unicode_name**: указатель на новое имя файла Юникода</span><span class="sxs-lookup"><span data-stu-id="ec793-3286">**new_unicode_name**: Pointer to the new Unicode file name.</span></span>
- <span data-ttu-id="ec793-3287">**old_unicode_name_length**: длина старого имени в Юникоде</span><span class="sxs-lookup"><span data-stu-id="ec793-3287">**old_unicode_name_length**: Length of new Unicode name.</span></span>
- <span data-ttu-id="ec793-3288">**new_short_name**: указатель на назначение для краткого имени (формат 8.3) для переименованного файла в Юникода</span><span class="sxs-lookup"><span data-stu-id="ec793-3288">**new_short_name**: Pointer to destination for short name (8.3 format) for the renamed Unicode file.</span></span> <span data-ttu-id="ec793-3289">Переименование каталога с помощью Юникода</span><span class="sxs-lookup"><span data-stu-id="ec793-3289">Rename Directory with Unicode</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-3290">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-3290">Return Values</span></span>

- <span data-ttu-id="ec793-3291">**FX_SUCCESS** (0x00) — носитель успешно открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-3291">**FX_SUCCESS** (0x00) Successful media open.</span></span>
- <span data-ttu-id="ec793-3292">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-3292">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="ec793-3293">**FX_ALREADY_CREATED** (0x0B) — каталог с указанным именем уже существует.</span><span class="sxs-lookup"><span data-stu-id="ec793-3293">**FX_ALREADY_CREATED** (0x0B) Specified directory name already exists.</span></span>
- <span data-ttu-id="ec793-3294">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-3294">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-3295">**FX_PTR_ERROR** (0x18) — один указатель или несколько имеют значение NULL.</span><span class="sxs-lookup"><span data-stu-id="ec793-3295">**FX_PTR_ERROR** (0x18) One or more pointers are NULL.</span></span>
- <span data-ttu-id="ec793-3296">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-3296">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>
- <span data-ttu-id="ec793-3297">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-3297">**FX_WRITE_PROTECT** (0x23) Specified media is write-protected.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-3298">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-3298">Allowed From</span></span>

<span data-ttu-id="ec793-3299">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-3299">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-3300">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-3300">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="ec793-3301">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-3301">See Also</span></span>

- <span data-ttu-id="ec793-3302">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-3302">fx_directory_attributes_read</span></span>
- <span data-ttu-id="ec793-3303">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3303">fx_directory_attributes_set</span></span>
- <span data-ttu-id="ec793-3304">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-3304">fx_directory_create</span></span>
- <span data-ttu-id="ec793-3305">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3305">fx_directory_default_get</span></span>
- <span data-ttu-id="ec793-3306">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3306">fx_directory_default_set</span></span>
- <span data-ttu-id="ec793-3307">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-3307">fx_directory_delete</span></span>
- <span data-ttu-id="ec793-3308">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-3308">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="ec793-3309">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-3309">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="ec793-3310">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3310">fx_directory_information_get</span></span>
- <span data-ttu-id="ec793-3311">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="ec793-3311">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="ec793-3312">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3312">fx_directory_local_path_get</span></span>
- <span data-ttu-id="ec793-3313">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="ec793-3313">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="ec793-3314">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3314">fx_directory_local_path_set</span></span>
- <span data-ttu-id="ec793-3315">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3315">fx_directory_long_name_get</span></span>
- <span data-ttu-id="ec793-3316">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="ec793-3316">fx_directory_name_test</span></span>
- <span data-ttu-id="ec793-3317">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-3317">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="ec793-3318">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="ec793-3318">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="ec793-3319">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-3319">fx_directory_rename</span></span>
- <span data-ttu-id="ec793-3320">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3320">fx_directory_short_name_get</span></span>
- <span data-ttu-id="ec793-3321">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="ec793-3321">fx_unicode_directory_create</span></span>

## <a name="fx_unicode_file_create"></a><span data-ttu-id="ec793-3322">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-3322">fx_unicode_file_create</span></span>

<span data-ttu-id="ec793-3323">Создает файл в Юникоде</span><span class="sxs-lookup"><span data-stu-id="ec793-3323">Creates a Unicode file</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-3324">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-3324">Prototype</span></span>

```c
UINT fx_unicode_file_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```

### <a name="description"></a><span data-ttu-id="ec793-3325">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-3325">Description</span></span>

<span data-ttu-id="ec793-3326">Эта служба создает файл с именем в Юникоде в текущем каталоге по умолчанию — в параметре имени источника в Юникоде не допускаются сведения о пути.</span><span class="sxs-lookup"><span data-stu-id="ec793-3326">This service creates a Unicode-named file in the current default directory—no path information is allowed in the Unicode source name parameter.</span></span> <span data-ttu-id="ec793-3327">В случае успешного выполнения служба возвращает краткое имя (формат 8.3) только что созданного файла в Юникоде.</span><span class="sxs-lookup"><span data-stu-id="ec793-3327">If successful, the short name (8.3 format) of the newly created Unicode file is returned by the service.</span></span>

> [!WARNING]
> <span data-ttu-id="ec793-3328">*Все операции с файлом в Юникоде (открытие, запись, чтение, закрытие и т. д.) должны выполняться путем предоставления возвращенного краткого имени (формат 8.3) стандартным файловым службам FileX.*</span><span class="sxs-lookup"><span data-stu-id="ec793-3328">*All operations on the Unicode file (opening, writing, reading, closing, etc.) should be done by supplying the returned short name (8.3 format) to the standard FileX file services.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-3329">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-3329">Input Parameters</span></span>


- <span data-ttu-id="ec793-3330">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-3330">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="ec793-3331">**source_unicode_name**: указатель на имя в Юникоде для нового файла</span><span class="sxs-lookup"><span data-stu-id="ec793-3331">**source_unicode_name**: Pointer to the Unicode name for the new file.</span></span>
- <span data-ttu-id="ec793-3332">**source_unicode_length**: длина имени в Юникоде</span><span class="sxs-lookup"><span data-stu-id="ec793-3332">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="ec793-3333">**short_name**: указатель на назначение для краткого имени (формат 8.3) для нового файла в Юникоде</span><span class="sxs-lookup"><span data-stu-id="ec793-3333">**short_name**: Pointer to destination for short name (8.3 format) for the new Unicode file.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-3334">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-3334">Return Values</span></span>

- <span data-ttu-id="ec793-3335">**FX_SUCCESS** (0x00) — файл успешно создан.</span><span class="sxs-lookup"><span data-stu-id="ec793-3335">**FX_SUCCESS** (0x00) Successful file create.</span></span>
- <span data-ttu-id="ec793-3336">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-3336">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="ec793-3337">**FX_ALREADY_CREATED** (0x0B) — указанный файл уже существует.</span><span class="sxs-lookup"><span data-stu-id="ec793-3337">**FX_ALREADY_CREATED** (0x0B) Specified file already exists.</span></span>
- <span data-ttu-id="ec793-3338">**FX_NO_MORE_SPACE** (0x0A) — на носителе больше нет доступных кластеров для новой записи файла.</span><span class="sxs-lookup"><span data-stu-id="ec793-3338">**FX_NO_MORE_SPACE** (0x0A) No more clusters available in the media for the new file entry.</span></span>
- <span data-ttu-id="ec793-3339">**FX_NOT_IMPLEMENTED** (0x22) — служба не реализована для файловой системы exFAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-3339">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="ec793-3340">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-3340">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-3341">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-3341">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="ec793-3342">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.</span><span class="sxs-lookup"><span data-stu-id="ec793-3342">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="ec793-3343">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-3343">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-3344">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-3344">Allowed From</span></span>

<span data-ttu-id="ec793-3345">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-3345">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-3346">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-3346">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="ec793-3347">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-3347">See Also</span></span>

- <span data-ttu-id="ec793-3348">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-3348">fx_file_allocate</span></span>
- <span data-ttu-id="ec793-3349">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-3349">fx_file_attributes_read</span></span>
- <span data-ttu-id="ec793-3350">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3350">fx_file_attributes_set</span></span>
- <span data-ttu-id="ec793-3351">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-3351">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-3352">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="ec793-3352">fx_file_close</span></span>
- <span data-ttu-id="ec793-3353">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-3353">fx_file_create</span></span>
- <span data-ttu-id="ec793-3354">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3354">fx_file_date_time_set</span></span>
- <span data-ttu-id="ec793-3355">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-3355">fx_file_delete</span></span>
- <span data-ttu-id="ec793-3356">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-3356">fx_file_extended_allocate</span></span>
- <span data-ttu-id="ec793-3357">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-3357">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-3358">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-3358">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="ec793-3359">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-3359">fx_file_extended_seek</span></span>
- <span data-ttu-id="ec793-3360">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-3360">fx_file_extended_truncate</span></span>
- <span data-ttu-id="ec793-3361">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-3361">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="ec793-3362">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="ec793-3362">fx_file_open</span></span>
- <span data-ttu-id="ec793-3363">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="ec793-3363">fx_file_read</span></span>
- <span data-ttu-id="ec793-3364">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-3364">fx_file_relative_seek</span></span>
- <span data-ttu-id="ec793-3365">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-3365">fx_file_rename</span></span>
- <span data-ttu-id="ec793-3366">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-3366">fx_file_seek</span></span>
- <span data-ttu-id="ec793-3367">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-3367">fx_file_truncate</span></span>
- <span data-ttu-id="ec793-3368">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-3368">fx_file_truncate_release</span></span>
- <span data-ttu-id="ec793-3369">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="ec793-3369">fx_file_write</span></span>
- <span data-ttu-id="ec793-3370">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3370">fx_file_write_notify_set</span></span>
- <span data-ttu-id="ec793-3371">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-3371">fx_unicode_file_rename</span></span>
- <span data-ttu-id="ec793-3372">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3372">fx_unicode_name_get</span></span>
- <span data-ttu-id="ec793-3373">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3373">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_file_rename"></a><span data-ttu-id="ec793-3374">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-3374">fx_unicode_file_rename</span></span>

<span data-ttu-id="ec793-3375">Переименовывает файл, используя строку в Юникоде</span><span class="sxs-lookup"><span data-stu-id="ec793-3375">Renames a file using unicode string</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-3376">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-3376">Prototype</span></span>

```c
UINT fx_unicode_file_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length, 
    CHAR *new_short_name);
```

### <a name="description"></a><span data-ttu-id="ec793-3377">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-3377">Description</span></span>

<span data-ttu-id="ec793-3378">Эта служба изменяет файл с именем в Юникоде на указанное новое имя в Юникоде в текущем каталоге по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ec793-3378">This service changes a Unicode-named file name to specified new Unicode name in current default directory.</span></span> <span data-ttu-id="ec793-3379">Параметры имени в Юникоде не должны содержать сведения о пути.</span><span class="sxs-lookup"><span data-stu-id="ec793-3379">The Unicode name parameters must not have path information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec793-3380">*Эта служба не поддерживается на носителях exFAT.*</span><span class="sxs-lookup"><span data-stu-id="ec793-3380">*This service is not supported on exFAT media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-3381">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-3381">Input Parameters</span></span>

- <span data-ttu-id="ec793-3382">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-3382">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="ec793-3383">**old_unicode_name**: указатель на имя в Юникоде для текущего файла</span><span class="sxs-lookup"><span data-stu-id="ec793-3383">**old_unicode_name**: Pointer to the Unicode name for the current file.</span></span>
- <span data-ttu-id="ec793-3384">**old_unicode_name_length**: длина текущего имени в Юникоде</span><span class="sxs-lookup"><span data-stu-id="ec793-3384">**old_unicode_name_length**: Length of current Unicode name.</span></span>
- <span data-ttu-id="ec793-3385">**new_unicode_name**: указатель на новое имя файла Юникода</span><span class="sxs-lookup"><span data-stu-id="ec793-3385">**new_unicode_name**: Pointer to the new Unicode file name.</span></span>
- <span data-ttu-id="ec793-3386">**new_unicode_name_length**: длина нового имени в Юникоде</span><span class="sxs-lookup"><span data-stu-id="ec793-3386">**new_unicode_name_length**: Length of new Unicode name.</span></span>
- <span data-ttu-id="ec793-3387">**new_short_name**: указатель на назначение для краткого имени (формат 8.3) для переименованного файла в Юникода</span><span class="sxs-lookup"><span data-stu-id="ec793-3387">**new_short_name**: Pointer to destination for short name (8.3 format) for the renamed Unicode file.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-3388">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-3388">Return Values</span></span>


- <span data-ttu-id="ec793-3389">**FX_SUCCESS** (0x00) — носитель успешно открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-3389">**FX_SUCCESS** (0x00) Successful media open.</span></span>
- <span data-ttu-id="ec793-3390">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-3390">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="ec793-3391">**FX_ALREADY_CREATED** (0x0B) — файл с указанным именем уже существует.</span><span class="sxs-lookup"><span data-stu-id="ec793-3391">**FX_ALREADY_CREATED** (0x0B) Specified file name already exists.</span></span>
- <span data-ttu-id="ec793-3392">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-3392">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-3393">**FX_PTR_ERROR** (0x18) — один указатель или несколько имеют значение NULL.</span><span class="sxs-lookup"><span data-stu-id="ec793-3393">**FX_PTR_ERROR** (0x18) One or more pointers are NULL.</span></span>
- <span data-ttu-id="ec793-3394">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-3394">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>
- <span data-ttu-id="ec793-3395">**FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.</span><span class="sxs-lookup"><span data-stu-id="ec793-3395">**FX_WRITE_PROTECT** (0x23) Specified media is write-protected.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-3396">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-3396">Allowed From</span></span>

<span data-ttu-id="ec793-3397">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-3397">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-3398">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-3398">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="ec793-3399">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-3399">See Also</span></span>

- <span data-ttu-id="ec793-3400">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-3400">fx_file_allocate</span></span>
- <span data-ttu-id="ec793-3401">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-3401">fx_file_attributes_read</span></span>
- <span data-ttu-id="ec793-3402">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3402">fx_file_attributes_set</span></span>
- <span data-ttu-id="ec793-3403">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-3403">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-3404">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="ec793-3404">fx_file_close</span></span>
- <span data-ttu-id="ec793-3405">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-3405">fx_file_create</span></span>
- <span data-ttu-id="ec793-3406">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3406">fx_file_date_time_set</span></span>
- <span data-ttu-id="ec793-3407">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-3407">fx_file_delete</span></span>
- <span data-ttu-id="ec793-3408">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-3408">fx_file_extended_allocate</span></span>
- <span data-ttu-id="ec793-3409">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-3409">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-3410">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-3410">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="ec793-3411">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-3411">fx_file_extended_seek</span></span>
- <span data-ttu-id="ec793-3412">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-3412">fx_file_extended_truncate</span></span>
- <span data-ttu-id="ec793-3413">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-3413">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="ec793-3414">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="ec793-3414">fx_file_open</span></span>
- <span data-ttu-id="ec793-3415">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="ec793-3415">fx_file_read</span></span>
- <span data-ttu-id="ec793-3416">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-3416">fx_file_relative_seek</span></span>
- <span data-ttu-id="ec793-3417">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-3417">fx_file_rename</span></span>
- <span data-ttu-id="ec793-3418">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-3418">fx_file_seek</span></span>
- <span data-ttu-id="ec793-3419">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-3419">fx_file_truncate</span></span>
- <span data-ttu-id="ec793-3420">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-3420">fx_file_truncate_release</span></span>
- <span data-ttu-id="ec793-3421">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="ec793-3421">fx_file_write</span></span>
- <span data-ttu-id="ec793-3422">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3422">fx_file_write_notify_set</span></span>
- <span data-ttu-id="ec793-3423">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-3423">fx_unicode_file_create</span></span>
- <span data-ttu-id="ec793-3424">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3424">fx_unicode_name_get</span></span>
- <span data-ttu-id="ec793-3425">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3425">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_length_get"></a><span data-ttu-id="ec793-3426">fx_unicode_length_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3426">fx_unicode_length_get</span></span>

<span data-ttu-id="ec793-3427">Возвращает длину имени в формате Юникода</span><span class="sxs-lookup"><span data-stu-id="ec793-3427">Gets length of Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-3428">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-3428">Prototype</span></span>

```c
ULONG fx_unicode_length_get(UCHAR *unicode_name);
```
### <a name="description"></a><span data-ttu-id="ec793-3429">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-3429">Description</span></span>

<span data-ttu-id="ec793-3430">Эта служба определяет длину заданного имени в формате Юникода.</span><span class="sxs-lookup"><span data-stu-id="ec793-3430">This service determines the length of the supplied Unicode name.</span></span> <span data-ttu-id="ec793-3431">Символ Юникода представлен двумя байт.</span><span class="sxs-lookup"><span data-stu-id="ec793-3431">A Unicode character is represented by two bytes.</span></span> <span data-ttu-id="ec793-3432">Имя в формате Юникода — это последовательность двухбайтовых символов Юникода, заканчивающихся двумя байт NULL (два байт со значением 0).</span><span class="sxs-lookup"><span data-stu-id="ec793-3432">A Unicode name is a series of two byte Unicode characters terminated by two NULL bytes (two bytes of 0 value).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-3433">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-3433">Input Parameters</span></span>

<span data-ttu-id="ec793-3434">**unicode_name**: указатель на имя в формате Юникода</span><span class="sxs-lookup"><span data-stu-id="ec793-3434">**unicode_name**: Pointer to Unicode name.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-3435">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-3435">Return Values</span></span>

<span data-ttu-id="ec793-3436">**length** — длина имени в формате Юникода (количество символов Юникода в имени).</span><span class="sxs-lookup"><span data-stu-id="ec793-3436">**length**: Length of Unicode name (number of Unicode characters in the name).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-3437">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-3437">Allowed From</span></span>

<span data-ttu-id="ec793-3438">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-3438">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-3439">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-3439">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="ec793-3440">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-3440">See Also</span></span>

- <span data-ttu-id="ec793-3441">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-3441">fx_file_allocate</span></span>
- <span data-ttu-id="ec793-3442">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-3442">fx_file_attributes_read</span></span>
- <span data-ttu-id="ec793-3443">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3443">fx_file_attributes_set</span></span>
- <span data-ttu-id="ec793-3444">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-3444">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-3445">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="ec793-3445">fx_file_close</span></span>
- <span data-ttu-id="ec793-3446">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-3446">fx_file_create</span></span>
- <span data-ttu-id="ec793-3447">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3447">fx_file_date_time_set</span></span>
- <span data-ttu-id="ec793-3448">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-3448">fx_file_delete</span></span>
- <span data-ttu-id="ec793-3449">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-3449">fx_file_extended_allocate</span></span>
- <span data-ttu-id="ec793-3450">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-3450">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-3451">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-3451">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="ec793-3452">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-3452">fx_file_extended_seek</span></span>
- <span data-ttu-id="ec793-3453">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-3453">fx_file_extended_truncate</span></span>
- <span data-ttu-id="ec793-3454">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-3454">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="ec793-3455">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="ec793-3455">fx_file_open</span></span>
- <span data-ttu-id="ec793-3456">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="ec793-3456">fx_file_read</span></span>
- <span data-ttu-id="ec793-3457">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-3457">fx_file_relative_seek</span></span>
- <span data-ttu-id="ec793-3458">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-3458">fx_file_rename</span></span>
- <span data-ttu-id="ec793-3459">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-3459">fx_file_seek</span></span>
- <span data-ttu-id="ec793-3460">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-3460">fx_file_truncate</span></span>
- <span data-ttu-id="ec793-3461">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-3461">fx_file_truncate_release</span></span>
- <span data-ttu-id="ec793-3462">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="ec793-3462">fx_file_write</span></span>
- <span data-ttu-id="ec793-3463">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3463">fx_file_write_notify_set</span></span>
- <span data-ttu-id="ec793-3464">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-3464">fx_unicode_file_create</span></span>
- <span data-ttu-id="ec793-3465">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-3465">fx_unicode_file_rename</span></span>
- <span data-ttu-id="ec793-3466">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3466">fx_unicode_name_get</span></span>
- <span data-ttu-id="ec793-3467">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3467">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_length_get_extended"></a><span data-ttu-id="ec793-3468">fx_unicode_length_get_extended</span><span class="sxs-lookup"><span data-stu-id="ec793-3468">fx_unicode_length_get_extended</span></span>

<span data-ttu-id="ec793-3469">Возвращает длину имени в формате Юникода</span><span class="sxs-lookup"><span data-stu-id="ec793-3469">Gets length of Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-3470">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-3470">Prototype</span></span>

```c
UINT fx_unicode_length_get_extended(
    UCHAR *unicode_name,
    UINT buffer_length);
```
### <a name="description"></a><span data-ttu-id="ec793-3471">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-3471">Description</span></span>

<span data-ttu-id="ec793-3472">Эта служба получает длину заданного имени в формате Юникода.</span><span class="sxs-lookup"><span data-stu-id="ec793-3472">This service gets the length of the supplied Unicode name.</span></span> <span data-ttu-id="ec793-3473">Символ Юникода представлен двумя байт.</span><span class="sxs-lookup"><span data-stu-id="ec793-3473">A Unicode character is represented by two bytes.</span></span> <span data-ttu-id="ec793-3474">Имя в формате Юникода — это последовательность двухбайтовых символов Юникода, заканчивающихся двумя байт NULL (два байт со значением 0).</span><span class="sxs-lookup"><span data-stu-id="ec793-3474">A Unicode name is a series of twobyte Unicode characters terminated by two NULL bytes (two bytes of 0 value).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec793-3475">*Эта служба идентична **fx_unicode_length_get()** , за исключением того, что вызывающий объект передает размер буфера **unicode_name**, включая два символа NULL.*</span><span class="sxs-lookup"><span data-stu-id="ec793-3475">*This service is identical to **fx_unicode_length_get()** except the caller passes in the size of the **unicode_name** buffer, including the two NULL characters.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-3476">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-3476">Input Parameters</span></span>

- <span data-ttu-id="ec793-3477">**unicode_name**: указатель на имя в формате Юникода</span><span class="sxs-lookup"><span data-stu-id="ec793-3477">**unicode_name**: Pointer to Unicode name.</span></span>
- <span data-ttu-id="ec793-3478">**buffer_length**: размер буфера имени в формате Юникода</span><span class="sxs-lookup"><span data-stu-id="ec793-3478">**buffer_length**: Size of Unicode name buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-3479">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-3479">Return Values</span></span>

<span data-ttu-id="ec793-3480">**length** — длина имени в формате Юникода (количество символов Юникода в имени).</span><span class="sxs-lookup"><span data-stu-id="ec793-3480">**length**: Length of Unicode name (number of Unicode characters in the name).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-3481">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-3481">Allowed From</span></span>

<span data-ttu-id="ec793-3482">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-3482">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-3483">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-3483">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="ec793-3484">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-3484">See Also</span></span>

- <span data-ttu-id="ec793-3485">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-3485">fx_file_allocate</span></span>
- <span data-ttu-id="ec793-3486">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-3486">fx_file_attributes_read</span></span>
- <span data-ttu-id="ec793-3487">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3487">fx_file_attributes_set</span></span>
- <span data-ttu-id="ec793-3488">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-3488">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-3489">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="ec793-3489">fx_file_close</span></span>
- <span data-ttu-id="ec793-3490">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-3490">fx_file_create</span></span>
- <span data-ttu-id="ec793-3491">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3491">fx_file_date_time_set</span></span>
- <span data-ttu-id="ec793-3492">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-3492">fx_file_delete</span></span>
- <span data-ttu-id="ec793-3493">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-3493">fx_file_extended_allocate</span></span>
- <span data-ttu-id="ec793-3494">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-3494">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-3495">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-3495">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="ec793-3496">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-3496">fx_file_extended_seek</span></span>
- <span data-ttu-id="ec793-3497">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-3497">fx_file_extended_truncate</span></span>
- <span data-ttu-id="ec793-3498">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-3498">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="ec793-3499">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="ec793-3499">fx_file_open</span></span>
- <span data-ttu-id="ec793-3500">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="ec793-3500">fx_file_read</span></span>
- <span data-ttu-id="ec793-3501">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-3501">fx_file_relative_seek</span></span>
- <span data-ttu-id="ec793-3502">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-3502">fx_file_rename</span></span>
- <span data-ttu-id="ec793-3503">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-3503">fx_file_seek</span></span>
- <span data-ttu-id="ec793-3504">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-3504">fx_file_truncate</span></span>
- <span data-ttu-id="ec793-3505">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-3505">fx_file_truncate_release</span></span>
- <span data-ttu-id="ec793-3506">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="ec793-3506">fx_file_write</span></span>
- <span data-ttu-id="ec793-3507">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3507">fx_file_write_notify_set</span></span>
- <span data-ttu-id="ec793-3508">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-3508">fx_unicode_file_create</span></span>
- <span data-ttu-id="ec793-3509">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-3509">fx_unicode_file_rename</span></span>
- <span data-ttu-id="ec793-3510">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3510">fx_unicode_name_get</span></span>
- <span data-ttu-id="ec793-3511">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3511">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_name_get"></a><span data-ttu-id="ec793-3512">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3512">fx_unicode_name_get</span></span>

<span data-ttu-id="ec793-3513">Получает имя в Юникоде из краткого имени</span><span class="sxs-lookup"><span data-stu-id="ec793-3513">Gets Unicode name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-3514">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-3514">Prototype</span></span>

```c
UINT fx_unicode_name_get(
    FX_MEDIA *media_ptr, 
    CHAR *source_short_name,
    UCHAR *destination_unicode_name, 
    ULONG *destination_unicode_length);
```

### <a name="description"></a><span data-ttu-id="ec793-3515">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-3515">Description</span></span>

<span data-ttu-id="ec793-3516">Эта служба получает имя в Юникоде, связанное с предоставленным кратким именем (формат 8.3) в текущем каталоге по умолчанию — в параметре краткого имени не допускаются сведения о пути.</span><span class="sxs-lookup"><span data-stu-id="ec793-3516">This service retrieves the Unicode-name associated with the supplied short name (8.3 format) within the current default directory—no path information is allowed in the short name parameter.</span></span> <span data-ttu-id="ec793-3517">В случае успешного выполнения служба возвращает имя в Юникоде, связанное с кратким именем.</span><span class="sxs-lookup"><span data-stu-id="ec793-3517">If successful, the Unicode name associated with the short name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec793-3518">*Эта служба может использоваться для получения имен в Юникоде для файлов и подкаталогов.*</span><span class="sxs-lookup"><span data-stu-id="ec793-3518">*This service can be used to get Unicode names for both files and subdirectories.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-3519">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-3519">Input Parameters</span></span>

- <span data-ttu-id="ec793-3520">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-3520">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="ec793-3521">**short_name**: указатель на краткое имя (формат 8.3)</span><span class="sxs-lookup"><span data-stu-id="ec793-3521">**short_name** Pointer to short name (8.3 format).</span></span>
- <span data-ttu-id="ec793-3522">**destination_unicode_name**: указатель на назначение для имени в Юникоде, связанного с заданным кратким именем</span><span class="sxs-lookup"><span data-stu-id="ec793-3522">**destination_unicode_name**: Pointer to the destination for the Unicode name associated with the supplied short name.</span></span>
- <span data-ttu-id="ec793-3523">**destination_unicode_length**: указатель на возвращаемую длину имени в Юникоде</span><span class="sxs-lookup"><span data-stu-id="ec793-3523">**destination_unicode_length**: Pointer to returned Unicode name length.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-3524">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-3524">Return Values</span></span>

- <span data-ttu-id="ec793-3525">**FX_SUCCESS** (0x00) — имя в Юникоде успешно получено.</span><span class="sxs-lookup"><span data-stu-id="ec793-3525">**FX_SUCCESS** (0x00) Successful Unicode name retrieval.</span></span>
- <span data-ttu-id="ec793-3526">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать таблицу FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-3526">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="ec793-3527">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-3527">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="ec793-3528">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-3528">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-3529">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-3529">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="ec793-3530">**FX_NOT_FOUND** (0x04) — краткое имя не найдено, или размер назначения Юникода слишком мал.</span><span class="sxs-lookup"><span data-stu-id="ec793-3530">**FX_NOT_FOUND** (0x04) Short name was not found or the Unicode destination size is too small.</span></span>
- <span data-ttu-id="ec793-3531">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-3531">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="ec793-3532">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.</span><span class="sxs-lookup"><span data-stu-id="ec793-3532">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="ec793-3533">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-3533">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-3534">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-3534">Allowed From</span></span>

<span data-ttu-id="ec793-3535">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-3535">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-3536">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-3536">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="ec793-3537">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-3537">See Also</span></span>

- <span data-ttu-id="ec793-3538">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-3538">fx_file_allocate</span></span>
- <span data-ttu-id="ec793-3539">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-3539">fx_file_attributes_read</span></span>
- <span data-ttu-id="ec793-3540">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3540">fx_file_attributes_set</span></span>
- <span data-ttu-id="ec793-3541">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-3541">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-3542">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="ec793-3542">fx_file_close</span></span>
- <span data-ttu-id="ec793-3543">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-3543">fx_file_create</span></span>
- <span data-ttu-id="ec793-3544">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3544">fx_file_date_time_set</span></span>
- <span data-ttu-id="ec793-3545">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-3545">fx_file_delete</span></span>
- <span data-ttu-id="ec793-3546">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-3546">fx_file_extended_allocate</span></span>
- <span data-ttu-id="ec793-3547">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-3547">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-3548">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-3548">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="ec793-3549">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-3549">fx_file_extended_seek</span></span>
- <span data-ttu-id="ec793-3550">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-3550">fx_file_extended_truncate</span></span>
- <span data-ttu-id="ec793-3551">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-3551">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="ec793-3552">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="ec793-3552">fx_file_open</span></span>
- <span data-ttu-id="ec793-3553">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="ec793-3553">fx_file_read</span></span>
- <span data-ttu-id="ec793-3554">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-3554">fx_file_relative_seek</span></span>
- <span data-ttu-id="ec793-3555">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-3555">fx_file_rename</span></span>
- <span data-ttu-id="ec793-3556">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-3556">fx_file_seek</span></span>
- <span data-ttu-id="ec793-3557">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-3557">fx_file_truncate</span></span>
- <span data-ttu-id="ec793-3558">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-3558">fx_file_truncate_release</span></span>
- <span data-ttu-id="ec793-3559">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="ec793-3559">fx_file_write</span></span>
- <span data-ttu-id="ec793-3560">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3560">fx_file_write_notify_set</span></span>
- <span data-ttu-id="ec793-3561">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-3561">fx_unicode_file_create</span></span>
- <span data-ttu-id="ec793-3562">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-3562">fx_unicode_file_rename</span></span>
- <span data-ttu-id="ec793-3563">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3563">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_name_get_extended"></a><span data-ttu-id="ec793-3564">fx_unicode_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="ec793-3564">fx_unicode_name_get_extended</span></span>

<span data-ttu-id="ec793-3565">Получает имя в Юникоде из краткого имени</span><span class="sxs-lookup"><span data-stu-id="ec793-3565">Gets Unicode name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-3566">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-3566">Prototype</span></span>

```c
UINT fx_unicode_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *source_short_name,
    UCHAR *destination_unicode_name,
    ULONG *destination_unicode_length,
    ULONG unicode_name_buffer_length);
```
### <a name="description"></a><span data-ttu-id="ec793-3567">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-3567">Description</span></span>

<span data-ttu-id="ec793-3568">Эта служба получает имя в Юникоде, связанное с предоставленным кратким именем (формат 8.3) в текущем каталоге по умолчанию — в параметре краткого имени не допускаются сведения о пути.</span><span class="sxs-lookup"><span data-stu-id="ec793-3568">This service retrieves the Unicode-name associated with the supplied short name (8.3 format) within the current default directory—no path information is allowed in the short name parameter.</span></span> <span data-ttu-id="ec793-3569">В случае успешного выполнения служба возвращает имя в Юникоде, связанное с кратким именем.</span><span class="sxs-lookup"><span data-stu-id="ec793-3569">If successful, the Unicode name associated with the short name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec793-3570">\*Эта служба идентична \***fx_unicode_name_get** _, за исключением того, что в качестве входного аргумента вызывающий объект предоставляет размер конечного буфера в Юникоде. Это позволяет службе гарантировать, что она не перезапишет конечный буфер Юникода_.</span><span class="sxs-lookup"><span data-stu-id="ec793-3570">\*This service is identical to \***fx_unicode_name_get**_, except the caller supplies the size of the destination Unicode buffer as an input argument. This allows the service to guarantee that it will not overwrite the destination Unicode buffer_</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec793-3571">*Эта служба может использоваться для получения имен в Юникоде для файлов и подкаталогов.*</span><span class="sxs-lookup"><span data-stu-id="ec793-3571">*This service can be used to get Unicode names for both files and subdirectories.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-3572">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-3572">Input Parameters</span></span>

- <span data-ttu-id="ec793-3573">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-3573">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="ec793-3574">**short_name**: указатель на краткое имя (формат 8.3)</span><span class="sxs-lookup"><span data-stu-id="ec793-3574">**short_name**: Pointer to short name (8.3 format).</span></span>
- <span data-ttu-id="ec793-3575">**destination_unicode_name**: указатель на назначение для имени в Юникоде, связанного с заданным кратким именем</span><span class="sxs-lookup"><span data-stu-id="ec793-3575">**destination_unicode_name**: Pointer to the destination for the Unicode name associated with the supplied short name.</span></span>
- <span data-ttu-id="ec793-3576">**destination_unicode_length**: указатель на возвращаемую длину имени в Юникоде</span><span class="sxs-lookup"><span data-stu-id="ec793-3576">**destination_unicode_length**: Pointer to returned Unicode name length.</span></span>
- <span data-ttu-id="ec793-3577">**unicode_name_buffer_length**: размер буфера имен в Юникоде</span><span class="sxs-lookup"><span data-stu-id="ec793-3577">**unicode_name_buffer_length**: Size of the Unicode name buffer.</span></span> <span data-ttu-id="ec793-3578">Примечание. Требуется NULL в конце, что добавляет дополнительный байт.</span><span class="sxs-lookup"><span data-stu-id="ec793-3578">Note: A NULL terminator is required, which makes an extra byte.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-3579">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-3579">Return Values</span></span>

- <span data-ttu-id="ec793-3580">**FX_SUCCESS** (0x00) — имя в Юникоде успешно получено.</span><span class="sxs-lookup"><span data-stu-id="ec793-3580">**FX_SUCCESS** (0x00) Successful Unicode name retrieval.</span></span>
- <span data-ttu-id="ec793-3581">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать таблицу FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-3581">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="ec793-3582">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-3582">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="ec793-3583">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-3583">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-3584">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-3584">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="ec793-3585">**FX_NOT_FOUND** (0x04) — краткое имя не найдено, или размер назначения Юникода слишком мал.</span><span class="sxs-lookup"><span data-stu-id="ec793-3585">**FX_NOT_FOUND** (0x04) Short name was not found or the Unicode destination size is too small.</span></span>
- <span data-ttu-id="ec793-3586">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-3586">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="ec793-3587">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.</span><span class="sxs-lookup"><span data-stu-id="ec793-3587">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="ec793-3588">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-3588">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-3589">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-3589">Allowed From</span></span>

<span data-ttu-id="ec793-3590">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-3590">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-3591">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-3591">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="ec793-3592">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-3592">See Also</span></span>

- <span data-ttu-id="ec793-3593">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-3593">fx_file_allocate</span></span>
- <span data-ttu-id="ec793-3594">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-3594">fx_file_attributes_read</span></span>
- <span data-ttu-id="ec793-3595">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3595">fx_file_attributes_set</span></span>
- <span data-ttu-id="ec793-3596">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-3596">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-3597">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="ec793-3597">fx_file_close</span></span>
- <span data-ttu-id="ec793-3598">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-3598">fx_file_create</span></span>
- <span data-ttu-id="ec793-3599">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3599">fx_file_date_time_set</span></span>
- <span data-ttu-id="ec793-3600">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-3600">fx_file_delete</span></span>
- <span data-ttu-id="ec793-3601">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-3601">fx_file_extended_allocate</span></span>
- <span data-ttu-id="ec793-3602">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-3602">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-3603">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-3603">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="ec793-3604">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-3604">fx_file_extended_seek</span></span>
- <span data-ttu-id="ec793-3605">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-3605">fx_file_extended_truncate</span></span>
- <span data-ttu-id="ec793-3606">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-3606">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="ec793-3607">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="ec793-3607">fx_file_open</span></span>
- <span data-ttu-id="ec793-3608">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="ec793-3608">fx_file_read</span></span>
- <span data-ttu-id="ec793-3609">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-3609">fx_file_relative_seek</span></span>
- <span data-ttu-id="ec793-3610">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-3610">fx_file_rename</span></span>
- <span data-ttu-id="ec793-3611">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-3611">fx_file_seek</span></span>
- <span data-ttu-id="ec793-3612">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-3612">fx_file_truncate</span></span>
- <span data-ttu-id="ec793-3613">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-3613">fx_file_truncate_release</span></span>
- <span data-ttu-id="ec793-3614">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="ec793-3614">fx_file_write</span></span>
- <span data-ttu-id="ec793-3615">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3615">fx_file_write_notify_set</span></span>
- <span data-ttu-id="ec793-3616">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-3616">fx_unicode_file_create</span></span>
- <span data-ttu-id="ec793-3617">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-3617">fx_unicode_file_rename</span></span>
- <span data-ttu-id="ec793-3618">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3618">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_short_name_get"></a><span data-ttu-id="ec793-3619">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3619">fx_unicode_short_name_get</span></span>

<span data-ttu-id="ec793-3620">Получает краткое имя из имени в Юникоде</span><span class="sxs-lookup"><span data-stu-id="ec793-3620">Gets short name from Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-3621">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-3621">Prototype</span></span>

```c
UINT fx_unicode_short_name_get(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length,
    CHAR *destination_short_name);
```

<span data-ttu-id="ec793-3622">Эта служба получает краткое имя (формат 8.3), связанное с предоставленным именем в Юникоде в текущем каталоге по умолчанию — в параметре имени в Юникоде не допускаются сведения о пути.</span><span class="sxs-lookup"><span data-stu-id="ec793-3622">This service retrieves the short name (8.3 format) associated with the Unicode-name within the current default directory—no path information is allowed in the Unicode name parameter.</span></span> <span data-ttu-id="ec793-3623">В случае успешного выполнения служба возвращает краткое имя, связанное с именем в Юникоде.</span><span class="sxs-lookup"><span data-stu-id="ec793-3623">If successful, the short name associated with the Unicode name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec793-3624">*Эта служба может использоваться для получения кратких имен для файлов и подкаталогов.*</span><span class="sxs-lookup"><span data-stu-id="ec793-3624">*This service can be used to get short names for both files and subdirectories.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-3625">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-3625">Input Parameters</span></span>

- <span data-ttu-id="ec793-3626">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-3626">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="ec793-3627">**source_unicode_name**: указатель на имя в формате Юникода</span><span class="sxs-lookup"><span data-stu-id="ec793-3627">**source_unicode_name**: Pointer to Unicode name.</span></span>
- <span data-ttu-id="ec793-3628">**source_unicode_length**: длина имени в Юникоде</span><span class="sxs-lookup"><span data-stu-id="ec793-3628">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="ec793-3629">**destination_short_name**: указатель на назначение краткого имени (формат 8.3)</span><span class="sxs-lookup"><span data-stu-id="ec793-3629">**destination_short_name**: Pointer to destination for the short name (8.3 format).</span></span> <span data-ttu-id="ec793-3630">Размер должен быть не менее 13 байт.</span><span class="sxs-lookup"><span data-stu-id="ec793-3630">This must be at least 13 bytes in size.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-3631">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-3631">Return Values</span></span>

- <span data-ttu-id="ec793-3632">**FX_SUCCESS** (0x00) — краткое имя успешно получено.</span><span class="sxs-lookup"><span data-stu-id="ec793-3632">**FX_SUCCESS** (0x00) Successful short name retrieval.</span></span>
- <span data-ttu-id="ec793-3633">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать таблицу FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-3633">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="ec793-3634">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-3634">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="ec793-3635">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-3635">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-3636">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-3636">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="ec793-3637">**FX_NOT_FOUND** (0x04) — имя в Юникоде не найдено.</span><span class="sxs-lookup"><span data-stu-id="ec793-3637">**FX_NOT_FOUND** (0x04)    Unicode name was not found.</span></span>
- <span data-ttu-id="ec793-3638">**FX_NOT_IMPLEMENTED** (0x22) — служба не реализована для файловой системы exFAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-3638">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="ec793-3639">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-3639">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="ec793-3640">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.</span><span class="sxs-lookup"><span data-stu-id="ec793-3640">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="ec793-3641">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-3641">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-3642">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-3642">Allowed From</span></span>

<span data-ttu-id="ec793-3643">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-3643">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-3644">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-3644">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="ec793-3645">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-3645">See Also</span></span>

- <span data-ttu-id="ec793-3646">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-3646">fx_file_allocate</span></span>
- <span data-ttu-id="ec793-3647">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-3647">fx_file_attributes_read</span></span>
- <span data-ttu-id="ec793-3648">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3648">fx_file_attributes_set</span></span>
- <span data-ttu-id="ec793-3649">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-3649">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-3650">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="ec793-3650">fx_file_close</span></span>
- <span data-ttu-id="ec793-3651">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-3651">fx_file_create</span></span>
- <span data-ttu-id="ec793-3652">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3652">fx_file_date_time_set</span></span>
- <span data-ttu-id="ec793-3653">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-3653">fx_file_delete</span></span>
- <span data-ttu-id="ec793-3654">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-3654">fx_file_extended_allocate</span></span>
- <span data-ttu-id="ec793-3655">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-3655">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-3656">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-3656">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="ec793-3657">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-3657">fx_file_extended_seek</span></span>
- <span data-ttu-id="ec793-3658">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-3658">fx_file_extended_truncate</span></span>
- <span data-ttu-id="ec793-3659">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-3659">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="ec793-3660">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="ec793-3660">fx_file_open</span></span>
- <span data-ttu-id="ec793-3661">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="ec793-3661">fx_file_read</span></span>
- <span data-ttu-id="ec793-3662">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-3662">fx_file_relative_seek</span></span>
- <span data-ttu-id="ec793-3663">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-3663">fx_file_rename</span></span>
- <span data-ttu-id="ec793-3664">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-3664">fx_file_seek</span></span>
- <span data-ttu-id="ec793-3665">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-3665">fx_file_truncate</span></span>
- <span data-ttu-id="ec793-3666">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-3666">fx_file_truncate_release</span></span>
- <span data-ttu-id="ec793-3667">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="ec793-3667">fx_file_write</span></span>
- <span data-ttu-id="ec793-3668">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3668">fx_file_write_notify_set</span></span>
- <span data-ttu-id="ec793-3669">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-3669">fx_unicode_file_create</span></span>
- <span data-ttu-id="ec793-3670">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-3670">fx_unicode_file_rename</span></span>
- <span data-ttu-id="ec793-3671">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3671">fx_unicode_name_get</span></span>

## <a name="fx_unicode_short_name_get_extended"></a><span data-ttu-id="ec793-3672">fx_unicode_short_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="ec793-3672">fx_unicode_short_name_get_extended</span></span>

<span data-ttu-id="ec793-3673">Получает краткое имя из имени в Юникоде</span><span class="sxs-lookup"><span data-stu-id="ec793-3673">Gets short name from Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="ec793-3674">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec793-3674">Prototype</span></span>

```c
UINT fx_unicode_short_name_get_extended(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *destination_short_name,
    ULONG short_name_buffer_length);
```

### <a name="description"></a><span data-ttu-id="ec793-3675">Описание</span><span class="sxs-lookup"><span data-stu-id="ec793-3675">Description</span></span>

<span data-ttu-id="ec793-3676">Эта служба получает краткое имя (формат 8.3), связанное с предоставленным именем в Юникоде в текущем каталоге по умолчанию — в параметре имени в Юникоде не допускаются сведения о пути.</span><span class="sxs-lookup"><span data-stu-id="ec793-3676">This service retrieves the short name (8.3 format) associated with the Unicode-name within the current default directory—no path information is allowed in the Unicode name parameter.</span></span> <span data-ttu-id="ec793-3677">В случае успешного выполнения служба возвращает краткое имя, связанное с именем в Юникоде.</span><span class="sxs-lookup"><span data-stu-id="ec793-3677">If successful, the short name associated with the Unicode name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec793-3678">*Эта служба идентична **fx_unicode_short_name_get()** , за исключением того, что в качестве входного аргумента вызывающий объект предоставляет размер конечного буфера. Это позволяет службе гарантировать, что краткое имя не превысит конечный буфер*.</span><span class="sxs-lookup"><span data-stu-id="ec793-3678">*This service is identical to **fx_unicode_short_name_get()**, except the caller supplies the size of the destination buffer as an input argument. This allows the service to guarantee the short name does not exceed the destination buffer.*</span></span>

<span data-ttu-id="ec793-3679">*Эта служба может использоваться для получения кратких имен для файлов и подкаталогов.*</span><span class="sxs-lookup"><span data-stu-id="ec793-3679">*This service can be used to get short names for both files and subdirectories*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec793-3680">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec793-3680">Input Parameters</span></span>

- <span data-ttu-id="ec793-3681">**media_ptr**: указатель на блок управления носителем</span><span class="sxs-lookup"><span data-stu-id="ec793-3681">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="ec793-3682">**source_unicode_name**: указатель на имя в формате Юникода</span><span class="sxs-lookup"><span data-stu-id="ec793-3682">**source_unicode_name**: Pointer to Unicode name.</span></span>
- <span data-ttu-id="ec793-3683">**source_unicode_length**: длина имени в Юникоде</span><span class="sxs-lookup"><span data-stu-id="ec793-3683">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="ec793-3684">**destination_short_name**: указатель на назначение краткого имени (формат 8.3)</span><span class="sxs-lookup"><span data-stu-id="ec793-3684">**destination_short_name**: Pointer to destination for the short name (8.3 format).</span></span> <span data-ttu-id="ec793-3685">Размер должен быть не менее 13 байт.</span><span class="sxs-lookup"><span data-stu-id="ec793-3685">This must be at least 13 bytes in size.</span></span>
- <span data-ttu-id="ec793-3686">**short_name_buffer_length**: размер буфера назначения</span><span class="sxs-lookup"><span data-stu-id="ec793-3686">**short_name_buffer_length**: Size of the destination buffer.</span></span> <span data-ttu-id="ec793-3687">Размер буфера должен быть не менее 14 байт.</span><span class="sxs-lookup"><span data-stu-id="ec793-3687">The buffer size must be at least 14 bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec793-3688">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec793-3688">Return Values</span></span>

- <span data-ttu-id="ec793-3689">**FX_SUCCESS** (0x00) — краткое имя успешно получено.</span><span class="sxs-lookup"><span data-stu-id="ec793-3689">**FX_SUCCESS** (0x00) Successful short name retrieval.</span></span>
- <span data-ttu-id="ec793-3690">**FX_FAT_READ_ERROR** (0x03) — не удается прочитать таблицу FAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-3690">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="ec793-3691">**FX_FILE_CORRUPT** (0x08) — файл поврежден.</span><span class="sxs-lookup"><span data-stu-id="ec793-3691">**FX_FILE_CORRUPT** (0x08)    File is corrupted</span></span>
- <span data-ttu-id="ec793-3692">**FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.</span><span class="sxs-lookup"><span data-stu-id="ec793-3692">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="ec793-3693">**FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.</span><span class="sxs-lookup"><span data-stu-id="ec793-3693">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="ec793-3694">**FX_NOT_FOUND** (0x04) — имя в Юникоде не найдено.</span><span class="sxs-lookup"><span data-stu-id="ec793-3694">**FX_NOT_FOUND** (0x04) Unicode name was not found.</span></span>
- <span data-ttu-id="ec793-3695">**FX_NOT_IMPLEMENTED** (0x22) — служба не реализована для файловой системы exFAT.</span><span class="sxs-lookup"><span data-stu-id="ec793-3695">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="ec793-3696">**FX_SECTOR_INVALID** (0x89) — недопустимый сектор.</span><span class="sxs-lookup"><span data-stu-id="ec793-3696">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="ec793-3697">**FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.</span><span class="sxs-lookup"><span data-stu-id="ec793-3697">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="ec793-3698">**FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="ec793-3698">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec793-3699">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec793-3699">Allowed From</span></span>

<span data-ttu-id="ec793-3700">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec793-3700">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec793-3701">Пример</span><span class="sxs-lookup"><span data-stu-id="ec793-3701">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="ec793-3702">См. также:</span><span class="sxs-lookup"><span data-stu-id="ec793-3702">See Also</span></span>

- <span data-ttu-id="ec793-3703">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-3703">fx_file_allocate</span></span>
- <span data-ttu-id="ec793-3704">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ec793-3704">fx_file_attributes_read</span></span>
- <span data-ttu-id="ec793-3705">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3705">fx_file_attributes_set</span></span>
- <span data-ttu-id="ec793-3706">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-3706">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-3707">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="ec793-3707">fx_file_close</span></span>
- <span data-ttu-id="ec793-3708">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-3708">fx_file_create</span></span>
- <span data-ttu-id="ec793-3709">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3709">fx_file_date_time_set</span></span>
- <span data-ttu-id="ec793-3710">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="ec793-3710">fx_file_delete</span></span>
- <span data-ttu-id="ec793-3711">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-3711">fx_file_extended_allocate</span></span>
- <span data-ttu-id="ec793-3712">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="ec793-3712">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="ec793-3713">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-3713">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="ec793-3714">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-3714">fx_file_extended_seek</span></span>
- <span data-ttu-id="ec793-3715">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-3715">fx_file_extended_truncate</span></span>
- <span data-ttu-id="ec793-3716">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-3716">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="ec793-3717">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="ec793-3717">fx_file_open</span></span>
- <span data-ttu-id="ec793-3718">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="ec793-3718">fx_file_read</span></span>
- <span data-ttu-id="ec793-3719">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-3719">fx_file_relative_seek</span></span>
- <span data-ttu-id="ec793-3720">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-3720">fx_file_rename</span></span>
- <span data-ttu-id="ec793-3721">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="ec793-3721">fx_file_seek</span></span>
- <span data-ttu-id="ec793-3722">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="ec793-3722">fx_file_truncate</span></span>
- <span data-ttu-id="ec793-3723">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="ec793-3723">fx_file_truncate_release</span></span>
- <span data-ttu-id="ec793-3724">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="ec793-3724">fx_file_write</span></span>
- <span data-ttu-id="ec793-3725">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="ec793-3725">fx_file_write_notify_set</span></span>
- <span data-ttu-id="ec793-3726">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="ec793-3726">fx_unicode_file_create</span></span>
- <span data-ttu-id="ec793-3727">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="ec793-3727">fx_unicode_file_rename</span></span>
- <span data-ttu-id="ec793-3728">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3728">fx_unicode_name_get</span></span>
- <span data-ttu-id="ec793-3729">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="ec793-3729">fx_unicode_short_name_get</span></span>
