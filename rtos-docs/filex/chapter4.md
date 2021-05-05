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
# <a name="chapter-4--description-of-azure-rtos-filex-services"></a>Глава 4. Описание служб FileX для ОСРВ Azure

В этой главе содержится описание всех служб FileX для ОСРВ Azure в алфавитном порядке. Имена служб реализованы так, что все аналогичные службы группируются вместе.

## <a name="fx_directory_attributes_read"></a>fx_directory_attributes_read

Считывает атрибуты каталога

### <a name="prototype"></a>Прототип

```c
UINT fx_directory_attributes_read ( 
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes_ptr);
```

### <a name="description"></a>Описание

Эта служба считывает атрибуты каталога с указанного носителя.

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **directory_name**: указатель на имя запрашиваемого каталога (путь к каталогу является необязательным)
- **attributes_ptr**: указатель на назначение для размещения атрибутов каталога Атрибуты каталога возвращаются в формате битовой карты со следующими возможными параметрами.
  - FX_READ_ONLY (0x01)
  - FX_HIDDEN (0x02)
  - FX_SYSTEM (0x04)
  - FX_VOLUME (0x08)
  - FX_DIRECTORY (0x10)
  - FX_ARCHIVE (0x20)

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — атрибуты каталога успешно считаны.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_NOT_FOUND** (0x04) — указанный каталог не найден на носителе.
- **FX_NOT_DIRECTORY** (0x0E) — запись является каталогом.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.
- **FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.
- **FX_MEDIA_INVALID** (0x02) — недопустимый носитель.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_MEDIA     my_media;
UINT     status;
/* Retrieve the attributes of "mydir" from the specified media.*/
status = fx_directory_attributes_read(&my_media, "mydir", &attributes);
/* If status equals FX_SUCCESS, "attributes" contains the directory attributes of "mydir". */
```

### <a name="see-also"></a>См. также:

- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_attributes_set"></a>fx_directory_attributes_set

Задает атрибуты каталога

### <a name="prototype"></a>Прототип

```c
UINT fx_directory_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes);
```

### <a name="description"></a>Описание

Эта служба задает атрибуты каталога, указанные вызывающим объектом.

> [!WARNING]
> *Этому приложению разрешено изменять только подмножество атрибутов каталога, используя эту службу. Любая попытка задать дополнительные атрибуты приведет к ошибке.*

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **directory_name**: указатель на имя запрашиваемого каталога (путь к каталогу является необязательным)
- **attributes**: новые атрибуты для этого каталога Допустимые атрибуты каталога определяются следующим образом.
  - FX_READ_ONLY (0x01)
  - FX_HIDDEN (0x02)
  - FX_SYSTEM (0x04)
  - FX_ARCHIVE (0x20)

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — атрибут каталога успешно задан.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_NOT_FOUND** (0x04) — указанный каталог не найден на носителе.
- **FX_NOT_DIRECTORY** (0x0E) — запись является каталогом.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.
- **FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.
- **FX_MEDIA_INVALID** (0x02) — недопустимый носитель.
- **FX_NO_MORE_ENTRIES** (0x0F) — в этом каталоге больше нет записей.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.
- **FX_INVALID_ATTR** (0x19) — выбраны недопустимые атрибуты.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_MEDIA             my_media;
UINT                 status;
status = fx_directory_attributes_set(&my_media, "mydir", FX_READ_ONLY);
/*Set the attributes of "mydir" to read-only. */
/* If status equals FX_SUCCESS, the directory "mydir" is read-only. */
```

### <a name="see-also"></a>См. также:

- fx_directory_attributes_read
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_create"></a>fx_directory_create

Создает подкаталог

### <a name="prototype"></a>Прототип

```c
UINT fx_directory_create(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```
### <a name="description"></a>Описание

Эта служба создает подкаталог в текущем каталоге по умолчанию или в пути, указанном в имени каталога. В отличие от корневого каталога подкаталоги не имеют ограничения на количество файлов, которые могут в них храниться. Корневой каталог может содержать только число записей, которое определено загрузочной записью.

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **directory_name**: указатель на имя создаваемого каталога (путь к каталогу является необязательным)

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — каталог успешно создан.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_NOT_FOUND** (0x04) — указанный каталог не найден на носителе.
- **FX_NOT_DIRECTORY** (0x0E) — запись является каталогом.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.
- **FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.
- **FX_MEDIA_INVALID** (0x02) — недопустимый носитель.
- **FX_NO_MORE_ENTRIES** (0x0F) — в этом каталоге больше нет записей.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.
- **FX_INVALID_ATTR** (0x19) — выбраны недопустимые атрибуты.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_MEDIA             my_media;
UINT                 status;
/* Create a subdirectory called "temp" in the current default directory. */

status = fx_directory_create(&my_media, "temp");

/* If status equals FX_SUCCESS, the new subdirectory "temp" has been created. */
```

### <a name="see-also"></a>См. также:

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_default_get"></a>fx_directory_default_get

Получает последний каталог по умолчанию

### <a name="prototype"></a>Прототип

```c
UINT fx_directory_default_get(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a>Описание

Эта служба возвращает указатель на путь, заданный службой ***fx_directory_default_set*** в последний раз. Если каталог по умолчанию не задан или текущий каталог по умолчанию является корневым каталогом, возвращается значение FX_NULL.

> [!IMPORTANT]
> *Размер по умолчанию для строки внутреннего пути составляет 256 символов; можно указать другой размер, изменив **FX_MAXIMUM_PATH** в файле **fx_api. h** и перестроив всю библиотеку FileX. Путь к строке символов сохраняется для приложения и не используется FileX внутри.*

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **return_path_name**: указатель на назначение для последней строки каталога по умолчанию Если текущим значением каталога по умолчанию является корневой каталог, возвращается значение FX_NULL. При открытии носителя по умолчанию используется корневой каталог.

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — каталог по умолчанию успешно получен.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель места назначения или носителя.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_MEDIA my_media;
CHAR *current_default_dir;
UINT status;
/* Retrieve the current default directory. */
status = fx_directory_default_get(&my_media, &current_default_dir);
/* If status equals FX_SUCCESS, "current_default_dir" 
    contains a pointer to the current default directory).*/
```

### <a name="see-also"></a>См. также:

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_default_set"></a>fx_directory_default_set

Задает каталог по умолчанию

### <a name="prototype"></a>Прототип

```c

UINT fx_directory_default_set(
    FX_MEDIA *media_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a>Описание

Эта служба задает каталог по умолчанию для носителя. Если указано значение FX_NULL, то в качестве каталога по умолчанию задается корневой каталог носителя. Все последующие операции с файлами, в которых явно не указан путь, по умолчанию будут использовать этот каталог.

> [!IMPORTANT]
> *Размер по умолчанию для строки внутреннего пути составляет 256 символов; можно указать другой размер, изменив **FX_MAXIMUM_PATH** в файле **fx_api. h** и перестроив всю библиотеку FileX. Путь к строке символов сохраняется для приложения и не используется FileX внутри.*

> [!IMPORTANT]
> *Для имен, предоставленных приложением, FileX поддерживает как обратную косую черту (\\), так и символ косой черты (/) для разделения каталогов, подкаталогов и имен файлов. Однако в путях, возвращаемых приложению, FileX использует только символ обратной косой черты.*

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **new_path_name**: указатель на новое имя каталога по умолчанию Если указано значение FX_NULL, то в качестве каталога носителя по умолчанию задается корневой каталог носителя.

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — каталог по умолчанию успешно задан.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_INVALID_PATH** (0x0D) — не удалось найти новый каталог.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_default_set(&my_media, "\\abc\\def\\ghi");
/* If status equals FX_SUCCESS, the default directory for this media is \abc\def\ghi. All subsequent file operations that do not explicitly specify a path will default to this directory. Note that the character "\" serves as an escape character in a string. To represent the character "\", use the construct "\\". This is done because of the C language- only one "\" is really present in the string. */
```

### <a name="see-also"></a>См. также:

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_delete"></a>fx_directory_delete

Удаляет подкаталог

### <a name="prototype"></a>Прототип

```c
UINT fx_directory_delete(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a>Описание

Эта служба удаляет указанный каталог. Обратите внимание, что каталог должен быть пустым, чтобы его можно было удалить.

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **directory_name**: указатель на имя удаляемого каталога (путь к каталогу является необязательным)

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — каталог успешно удален.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_NOT_FOUND** (0x04) — указанный каталог не найден.
- **FX_DIR_NOT_EMPTY** (0x10) — указанный каталог не пуст.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.
- **FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.
- **FX_MEDIA_INVALID** (0x02) — недопустимый носитель.
- **FX_NO_MORE_ENTRIES** (0x0F) — в этом каталоге больше нет записей.
- **FX_NOT_DIRECTORY** (0x0E) — не является записью каталога.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример
```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_delete(&my_media, "abc");
/* Delete the subdirectory "abc." */
/* If status equals FX_SUCCESS, the subdirectory "abc" was deleted. */
```

### <a name="see-also"></a>См. также:

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_first_entry_find"></a>fx_directory_first_entry_find

Получает первую запись каталога

### <a name="prototype"></a>Прототип

```c
UINT fx_directory_first_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a>Описание

Эта служба получает имя первой записи в каталоге по умолчанию и копирует его в указанное место назначения.

> [!WARNING]
> *Указанное назначение должно быть достаточно большим, чтобы вместить имя FileX максимального размера, как определено **FX_MAX_LONG_NAME_LEN.***

> [!WARNING]
> *При использовании нелокального пути важно предотвратить изменение этого каталога (с помощью семафора ThreadX, мьютекса или изменения уровня приоритета) другими потоками приложения во время обхода каталога. В противном случае могут быть получены недопустимые результаты.*

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **return_entry_name**: указатель на назначение для имени первой записи в каталоге по умолчанию

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — первая запись каталога успешно найдена.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_NO_MORE_ENTRIES** (0x0F) — в этом каталоге больше нет записей.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель места назначения или носителя.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_MEDIA         my_media;
UINT             status;
CHAR             entry[FX_MAX_LONG_NAME_LEN];
/* Retrieve the first directory entry in the current directory. */
status = fx_directory_first_entry_find(&my_media, entry);
/* If status equals FX_SUCCESS, the entry in the directory is the "entry" string. */
```

### <a name="see-also"></a>См. также:

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_first_full_entry_find"></a>fx_directory_first_full_entry_find

Получает первую запись каталога с полной информацией

### <a name="prototype"></a>Прототип

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **directory_name**: указатель на назначение для имени записи каталога Размер должен быть не меньше FX_MAX_LONG_NAME_LEN.
- **attributes_ptr**: указатель на назначение для размещения атрибутов записи, если не NULL Атрибуты возвращаются в формате битовой карты со следующими возможными параметрами.
  - **FX_READ_ONLY** (0x01)
  - **FX_HIDDEN** (0x02)
  - **FX_SYSTEM** (0x04)
  - **FX_VOLUME** (0x08)
  - **FX_DIRECTORY** (0x10)
  - **FX_ARCHIVE** (0x20)
- **size**: указатель на назначение для размера записи в байтах, если не NULL
- **year**: указатель на назначение для года записи, если не NULL
- **month**: указатель на назначение для месяца записи, если не NULL
- **day**: указатель на назначение для дня записи, если не NULL
- **hour**: указатель на назначение для часа записи, если не NULL
- **minute**: указатель на назначение для минуты записи, если не NULL
- **second**: указатель на назначение для секунды записи, если не NULL

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — первая запись каталога успешно найдена.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_NO_MORE_ENTRIES** (0x0F) — в этом каталоге больше нет записей.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.
- **FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.
- **FX_MEDIA_INVALID** (0x02) — недопустимый носитель.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель места назначения или носителя.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

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

### <a name="see-also"></a>См. также:

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_information_get"></a>fx_directory_information_get:

Получает сведения о записи каталога

### <a name="prototype"></a>Прототип

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **directory_name**: указатель на имя записи каталога
- **attributes**: указатель на назначение для атрибутов
- **size**: указатель на назначение для размера
- **year**: указатель на назначение для года
- **month**: указатель на назначение для месяца
- **day**: указатель на назначение для дня
- **hour**: указатель на назначение для часа
- **minute**: указатель на назначение для минуты
- **second**: указатель на назначение для секунды

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — первая запись каталога успешно найдена.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_NOT_FOUND** (0x04) — указанный каталог не найден на носителе.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_MEDIA_INVALID** (0x02) — недопустимый носитель.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.
- **FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель места назначения или носителя.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

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

### <a name="see-also"></a>См. также:

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_local_path_clear"></a>fx_directory_local_path_clear:

Очищает локальный путь по умолчанию

### <a name="prototype"></a>Прототип

```c
UINT fx_directory_local_path_clear(FX_MEDIA *media_ptr);
```

### <a name="description"></a>Описание

Эта служба очищает предыдущий локальный путь, настроенный для вызывающего потока.

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на открытый ранее носитель

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — локальный путь успешно очищен.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель в настоящее время не открыт.
- **FX_NOT_IMPLEMENTED** (0x22) — определен FX_NO_LCOAL_PATH.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_MEDIA             my_media;
UINT                 status;
/* Clear the previously setup local path for this media. */
status = fx_directory_local_path_clear(&my_media);
/* If status equals FX_SUCCESS the local path is cleared. */
```

### <a name="see-also"></a>См. также:

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_local_path_get"></a>fx_directory_local_path_get:

Возвращает строку текущего локального пути

### <a name="prototype"></a>Прототип

```c
UINT fx_directory_local_path_clear(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a>Описание

Эта служба возвращает указатель локального пути для указанного носителя. Если локальный путь не задан, вызывающему объекту возвращается значение NULL.

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **return_path_name**: указатель на указатель строки назначения для сохраняемой строки локального пути

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — локальный путь успешно получен.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель в настоящее время не открыт.
- **FX_NOT_IMPLEMENTED** (0x22) — NX_NO_LCOAL_PATH
- **FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.


### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_MEDIA         my_media;
CHAR             *my_path;
UINT             status;
/* Retrieve the current local path string. */
status = fx_directory_local_path_get(&my_media, &my_path);
/* If status equals FX_SUCCESS, "my_path" points to the local path string. */
```

### <a name="see-also"></a>См. также:

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_local_path_restore"></a>fx_directory_local_path_restore:

Восстанавливает предыдущий локальный путь

### <a name="prototype"></a>Прототип

```c
UINT fx_directory_local_path_restore(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr);
```

### <a name="description"></a>Описание

Эта служба восстанавливает заданный ранее локальный путь. Также восстанавливается расположение поиска в каталоге по этому локальному пути, что делает эту подпрограмму полезной в рекурсивных обходах каталогов приложением.

> [!IMPORTANT]
> *Каждый локальный путь содержит строку локального пути размером **FX_MAXIMUM_PATH** (значение по умолчанию — 256 символов). Эта строка внутреннего пути не используется FileX и предоставляется только для использования приложением. Если **FX_LOCAL_PATH** будет объявлена как локальная переменная, пользователям следует помнить, что стек увеличивается на размер этой структуры. Пользователи могут уменьшить размер **FX_MAXIMUM_PATH** и перестроить источник библиотеки FileX.*

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **local_path_ptr**: указатель на заданный ранее локальный путь Очень важно убедиться, что этот указатель действительно указывает на ранее использовавшийся, но незатронутый локальный путь.

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — локальный путь успешно восстановлен.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель в настоящее время не открыт.
- **FX_NOT_IMPLEMENTED** (0x22) — определен FX_NO_LCOAL_PATH.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель на носитель или локальный путь.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_MEDIA                  my_media;
FX_LOCAL_PATH             my_previous_local_path;
UINT                      status;
/* Restore the previous local path. */
status = fx_directory_local_path_restore(&my_media, &my_previous_local_path);
/* If status equals FX_SUCCESS, the previous local path has been restored. */
```

### <a name="see-also"></a>См. также:

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_local_path_set"></a>fx_directory_local_path_set

Задает локальный путь для конкретного потока

### <a name="prototype"></a>Прототип

```c
UINT fx_directory_local_path_set(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a>Описание

Эта служба задает путь для конкретного потока, как указано в ***new_path_string** _. После успешного выполнения этой подпрограммы сведения о локальном пути, хранящиеся в файле _ *_local_path_ptr_**, будут иметь приоритет над глобальным путем к носителю для всех операций с файлами и каталогами, выполняемыми этим потоком. Это не влияет на любой другой поток в системе. 
> [!IMPORTANT]
> *Размер по умолчанию для строки локального пути составляет 256 символов; можно указать другой размер, изменив **FX_MAXIMUM_PATH** в файле **fx_api. h** и перестроив всю библиотеку FileX. Путь к строке символов сохраняется для приложения и не используется FileX внутри.*

> [!IMPORTANT]
> *Для имен, предоставленных приложением, FileX поддерживает как обратную косую черту (\\), так и символ косой черты (/) для разделения каталогов, подкаталогов и имен файлов. Однако в путях, возвращаемых приложению, FileX использует только символ обратной косой черты.*

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на открытый ранее носитель
- **local_path_ptr**: назначение для хранения сведений о локальном пути для конкретного потока В будущем для функции восстановления локального пути можно предоставить адрес этой структуры.
- **new_path_name**: указывает локальный путь для настройки

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — каталог по умолчанию успешно задан.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_NOT_IMPLEMENTED** (0x22) — **FX_NO_LCOAL_PATH
- **FX_INVALID_PATH** (0x0D) — не удалось найти новый каталог.
- **FX_NOT_IMPLEMENTED** (0x22) — определен **FX_NO_LOCAL_PATH.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель на носитель или локальный путь.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

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

### <a name="see-also"></a>См. также:

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_long_name_get"></a>fx_directory_long_name_get:

Получает длинное имя из краткого имени

### <a name="prototype"></a>Прототип

```c
UINT fx_directory_long_name_get(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name);
```

### <a name="description"></a>Описание

Эта служба получает длинное имя (если имеется), связанное с переданным кратким именем (формат 8.3). Краткое имя может быть либо именем файла, либо именем каталога.

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **short_name**: указатель на исходное краткое имя (формат 8.3)
- **long_name**: указатель на назначение для длинного имени Если нет длинного имени, возвращается краткое имя. Обратите внимание, что назначение для длинного имени должно быть достаточно большим, чтобы вместить FX_MAX_LONG_NAME_LEN символов.

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — длинное имя успешно получено.
- **FX_NOT_FOUND** (0x04) — краткое имя не найдено.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_MEDIA_INVALID** (0x02) — недопустимый носитель.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.
- **FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_MEDIA            my_media;
UCHAR               my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */
status = fx_directory_long_name_get(&my_media, "TEXT~01.TXT", my_long_name);
/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a>См. также:

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_long_name_get_extended"></a>fx_directory_long_name_get_extended

Получает длинное имя из краткого имени

### <a name="prototype"></a>Прототип

```c
UINT fx_directory_long_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name,
    UINT long_file_name_buffer_length);
```

### <a name="description"></a>Описание

Эта служба получает длинное имя (если имеется), связанное с переданным кратким именем (формат 8.3). Краткое имя может быть либо именем файла, либо именем каталога.

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **short_name**: указатель на исходное краткое имя (формат 8.3)
- **long_name**: указатель на назначение для длинного имени Если нет длинного имени, возвращается краткое имя. Обратите внимание, что назначение для длинного имени должно быть достаточно большим, чтобы вместить **FX_MAX_LONG_NAME_LEN** символов.
- **long_file_name_buffer_length**: длина буфера длинного имени

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — длинное имя успешно получено.
- **FX_NOT_FOUND** (0x04) — краткое имя не найдено.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_MEDIA_INVALID** (0x02) — недопустимый носитель.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.
- **FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_MEDIA        my_media;
UCHAR            my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */

status = fx_directory_long_name_get_extended(&my_media,
    "TEXT~01.TXT", my_long_name), sizeof(my_long_name));

/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a>См. также:

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_name_test"></a>fx_directory_name_test

Проверяет каталог

### <a name="prototype"></a>Прототип

```c
UINT fx_directory_name_test(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a>Описание

Эта служба проверяет, является ли переданное имя каталогом. Если это так, возвращается FX_SUCCESS.

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **directory_name**: указатель на имя записи каталога

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — указанное имя является каталогом.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_NOT_FOUND** (0x04) — не удалось найти запись каталога.
- **FX_NOT_DIRECTORY** (0x0E) — запись не является каталогом.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_MEDIA_INVALID** (0x02) — недопустимый носитель.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.
- **FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_MEDIA        my_media;
UNIT             status;
/* Check to see if the name "abc" is directory */

status = fx_directory_name_test(&my_media, "abc");

/* If status equals FX_SUCCESS "abc" is a directory. */
```

### <a name="see-also"></a>См. также:

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create

## <a name="fx_directory_next_entry_find"></a>fx_directory_next_entry_find:

Выбирает новую запись каталога

### <a name="prototype"></a>Прототип

```c
UINT fx_directory_next_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a>Описание

Эта служба возвращает имя следующей записи в текущем каталоге по умолчанию.

> [!WARNING]
> *При использовании нелокального пути также важно предотвратить изменение этого каталога (с помощью семафора ThreadX или уровня приоритета потока) другими потоками приложения во время обхода каталога. В противном случае могут быть получены недопустимые результаты.*

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **return_entry_name**: указатель на назначение для имени следующей записи в каталоге по умолчанию Буфер, на который указывает этот указатель, должен быть достаточно большим, чтобы вместить имя FileX максимального размера, как определено **_FX_MAX_LONG_NAME_LEN_**.

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — следующая запись успешно найдена.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_NO_MORE_ENTRIES** (0x0F) — в этом каталоге больше нет записей.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_MEDIA        my_media;
CHAR            next_name[FX_MAX_LONG_NAME_LEN];
UINT            status;

/* Retrieve the next entry in the default directory. */

status = fx_directory_next_entry_find(&my_media, next_name);

/* If status equals TX_SUCCESS, the name of the next directory entry is in "next_name". */
```

### <a name="see-also"></a>См. также:

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_next_full_entry_find"></a>fx_directory_next_full_entry_find:

Получает следующую запись каталога с полной информацией

### <a name="prototype"></a>Прототип

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

### <a name="description"></a>Описание

Эта служба получает имя следующей записи в каталоге по умолчанию и копирует его в указанное место назначения. Она также возвращает полные сведения о записи, указанные дополнительными входными параметрами.

> [!WARNING]
> *Указанное назначение должно быть достаточно большим, чтобы вместить имя FileX максимального размера, как определено ***FX_MAX_LONG_NAME_LEN***.

> [!WARNING]
> *При использовании нелокального пути важно предотвратить изменение этого каталога (с помощью семафора ThreadX, мьютекса или изменения уровня приоритета) другими потоками приложения во время обхода каталога. В противном случае могут быть получены недопустимые результаты.*

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **directory_name**: указатель на назначение для имени записи каталога Размер должен быть не меньше **FX_MAX_LONG_NAME_LEN**.
- **attributes**: если значение не равно NULL, указатель на назначение для атрибутов записи, которые необходимо разместить. Атрибуты возвращаются в формате битовой карты со следующими возможными параметрами.
  - **FX_READ_ONLY** (0x01)
  - **FX_HIDDEN** (0x02)
  - **FX_SYSTEM** (0x04)
  - **FX_VOLUME** (0x08)
  - **FX_DIRECTORY** (0x10)
  - **FX_ARCHIVE** (0x20)
- **size**: указатель на назначение для размера записи в байтах, если не NULL
- **month**: указатель на назначение для месяца записи, если не NULL
- **year**: указатель на назначение для года записи, если не NULL
- **day**: указатель на назначение для дня записи, если не NULL
- **hour**: указатель на назначение для часа записи, если не NULL
- **minute**: указатель на назначение для минуты записи, если не NULL
- **second**: указатель на назначение для секунды записи, если не NULL

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — следующая запись каталога успешно найдена.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_NO_MORE_ENTRIES** (0x0F) — в этом каталоге больше нет записей.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.
- **FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.
- **FX_MEDIA_INVALID** (0x02) — недопустимый носитель.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель носителя, или все входные параметры имеют значение NULL.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

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

### <a name="see-also"></a>См. также:

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_rename"></a>fx_directory_rename

Переименовывает каталог

### <a name="prototype"></a>Прототип

```c
UINT fx_directory_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_directory_name,
    CHAR *new_directory_name);
```

### <a name="description"></a>Описание

Эта служба изменяет имя каталога на указанное новое имя каталога. Переименование также выполняется относительно указанного пути или пути по умолчанию. Если в новом имени каталога указан путь, переименованный каталог фактически перемещается по указанному пути. Если путь не указан, переименованный каталог помещается в текущий путь по умолчанию.

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **old_directory_name**: указатель на текущее имя каталога
- **new_directory_name**: указатель на новое имя каталога

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — каталог успешно переименован.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_NOT_FOUND** (0x04) — не удалось найти запись каталога.
- **FX_NOT_DIRECTORY** (0x0E) — запись не является каталогом.
- **FX_INVALID_NAME** (0x0C) — недопустимое имя каталога.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.
- **FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.
- **FX_MEDIA_INVALID** (0x02) — недопустимый носитель.
- **FX_NO_MORE_ENTRIES** (0x0F) — в этом каталоге больше нет записей.
- **FX_INVALID_PATH** (0x0D) — указан недопустимый путь с именем каталога.
- **FX_ALREADY_CREATED** (0x0B) — указанный каталог уже создан.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_MEDIA         my_media;
UINT             status;

/* Change the directory "abc" to "def". */
status = fx_directory_rename(&my_media, "abc", "def");

/* If status equals FX_SUCCESS, the directory was changed to "def". */
```

### <a name="see-also"></a>См. также:

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_short_name_get"></a>fx_directory_short_name_get:

Получение краткого имени из длинного

### <a name="prototype"></a>Прототип

```c
UINT fx_directory_short_name_get(
    FX_MEDIA *media_ptr,
    CHAR *long_name, 
    CHAR *short_name);
```

### <a name="description"></a>Описание

Эта служба получает краткое имя (формат 8.3), связанное с переданным длинным именем. Длинное имя может быть либо именем файла, либо именем каталога.

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **long_name**: указатель на исходное длинное имя
- **short_name**: указатель на назначение краткого имени (формат 8.3) Обратите внимание, что назначение для краткого имени должно быть достаточно большим, чтобы вместить 14 символов.

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — краткое имя успешно получено.
- **FX_NOT_FOUND** (0x04) — длинное имя не найдено.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.
- **FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.
- **FX_MEDIA_INVALID** (0x02) — недопустимый носитель.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_MEDIA         my_media;
UCHAR             my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get(&my_media,
    "my_really_long_name", my_short_name);

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a>См. также:

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_short_name_get_extended"></a>fx_directory_short_name_get_extended

Получение краткого имени из длинного

### <a name="prototype"></a>Прототип

```csharp
UINT fx_directory_short_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *long_name,
    CHAR *short_name,
    UINT short_file_name_length);
```

### <a name="description"></a>Описание

Эта служба получает краткое имя (формат 8.3), связанное с переданным длинным именем. Длинное имя может быть либо именем файла, либо именем каталога.

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **long_name**: указатель на исходное длинное имя
- **short_name**: указатель на назначение краткого имени (формат 8.3) Обратите внимание, что назначение для краткого имени должно быть достаточно большим, чтобы вместить 14 символов.
- **short_file_name_length**: длина буфера коротких имен

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — краткое имя успешно получено.
- **FX_NOT_FOUND** (0x04) — длинное имя не найдено.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.
- **FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.
- **FX_MEDIA_INVALID** (0x02) — недопустимый носитель.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_MEDIA        my_media;
UCHAR            my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get_extended(&my_media,
    "my_really_long_name", my_short_name, sizeof(my_short_name));

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a>См. также:

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_fault_tolerant_enable"></a>fx_fault_tolerant_enable

Включает отказоустойчивую службу

### <a name="prototype"></a>Прототип

```csharp
UINT fx_fault_tolerant_enable(
    FX_MEDIA *media_ptr,
    VOID *memory_buffer,
    UINT memory_size);
```

### <a name="description"></a>Описание

Эта служба включает отказоустойчивый модуль. После запуска отказоустойчивый модуль определяет, находится ли файловая система в режиме отказоустойчивой защиты FileX. Если это не так, служба находит в файловой системе доступные секторы для хранения журналов транзакций файловой системы. Если файловая система находится в режиме отказоустойчивой защиты FileX, она применяет журналы к файловой системе для обеспечения целостности.

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **memory_ptr**: указатель на блок памяти, используемый отказоустойчивым модулем в качестве вспомогательной памяти
- **memory_size**: размер вспомогательной памяти Чтобы отказоустойчивость работала правильно, размер вспомогательной памяти должен составлять не менее 3072 байт и должен быть кратен размеру сектора.

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — отказоустойчивость успешно включена.
- **FX_NOT_ENOUGH_MEMORY** (0x91) — слишком маленький размер памяти.
- **FX_BOOT_ERROR** (0x01) — ошибка загрузочного сектора.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_NO_MORE_ENTRIES** (0x0F) — больше нет свободных кластеров.
- **FX_NO_MORE_SPACE** (0x0A) — на носителе, связанном с этим файлом, недостаточно доступных кластеров.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Пример

```c

/* Declare memory space used for fault tolerant. */

ULONG fault tolerant_memory[3072 / sizeof(ULONG)];

/* Enable fault tolerant. */

fx_fault_tolerant_enable(media_ptr, fault_tolerant_memory, sizeof(fault_tolerant_memory));

```

### <a name="see-also"></a>См. также:

- fx_system_initialize
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write

## <a name="fx_file_allocate"></a>fx_file_allocate

Выделяет место для файла

### <a name="prototype"></a>Прототип

```csharp
UINT fx_file_allocate(
    FX_FILE *file_ptr, 
    ULONG size);
```
### <a name="description"></a>Описание

Эта служба выделяет один кластер или несколько последовательных и связывает их с концом указанного файла. FileX определяет количество кластеров, необходимое для деления запрошенного размера на число байтов на кластер. Затем результат округляется до следующего целого кластера.

Чтобы выделить место свыше 4 ГБ, приложение должно использовать службу *fx_file_extended_allocate*.

### <a name="input-parameters"></a>Входные параметры

- **file_ptr**: указатель на открытый ранее файл
- **size**: число байтов, выделяемых для файла

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — файл успешно выделен.
- **FX_ACCESS_ERROR** (0x06) — указанный файл не открыт для записи.
- **FX_FAT_READ_ERROR** (0x03) — не удалось прочитать запись FAT.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_NOT_OPEN** (0x07) — указанный файл в настоящее время не открыт.
- **FX_NO_MORE_ENTRIES** (0x0F) — больше нет свободных кластеров.
- **FX_NO_MORE_SPACE** (0x0A) — на носителе, связанном с этим файлом, недостаточно доступных кластеров.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель на файл.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c

FX_FILE            my_file;
UINT            status;

/* Allocate 1024 bytes to the end of my_file. */

status = fx_file_allocate(&my_file, 1024);

/* If status equals FX_SUCCESS the file now has one or more
    contiguous cluster(s) that can accommodate at least 1024 bytes of user data. */
```

### <a name="see-also"></a>См. также:

- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open- fx_file_read
- fx_file_relative_seek
- fx_file_rename- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_attributes_read"></a>fx_file_attributes_read

Считывает атрибуты файла

### <a name="prototype"></a>Прототип

```c
    UINT fx_file_attributes_read(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT *attributes_ptr);
```
### <a name="description"></a>Описание

Эта служба считывает атрибуты файла с указанного носителя.

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **file_name**: указатель на имя запрошенного файла (путь к каталогу является необязательным)
- **attributes_ptr**: указатель на назначение для размещения атрибутов файла Атрибуты файла возвращаются в формате битовой карты со следующими возможными параметрами.
  - FX_READ_ONLY (0x01)
  - FX_HIDDEN (0x02)
  - FX_SYSTEM (0x04)
  - FX_VOLUME (0x08)
  - FX_DIRECTORY (0x10)
  - FX_ARCHIVE (0x20)

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — атрибут успешно считан.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_NOT_FOUND** (0x04) — указанный файл не найден на носителе.
- **FX_NOT_A_FILE** (0x05) — указанный файл является каталогом.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.
- **FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_PTR_ERROR** (0x18) — недопустимый носитель или указатель на атрибуты.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c

FX_MEDIA         my_media;
UINT             status;
UINT             attributes;

/* Retrieve the attributes of "myfile.txt" from the specified media. */

status = fx_file_attributes_read(&my_media, "myfile.txt", &attributes);

/* If status equals FX_SUCCESS, "attributes"
    contains the file attributes for "myfile.txt". */

```

### <a name="see-also"></a>См. также:

- fx_file_allocate
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_attributes_set"></a>fx_file_attributes_set

Задает атрибуты файла

### <a name="prototype"></a>Прототип

```c
UINT fx_file_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT attributes);
```
### <a name="description"></a>Описание

Эта служба задает атрибуты файла, указанные вызывающим объектом.

> [!WARNING]
> *Этому приложению разрешено изменять только подмножество атрибутов файла, используя эту службу. Любая попытка задать дополнительные атрибуты приведет к ошибке.*

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **file_name**: указатель на имя запрошенного файла** (путь к каталогу является необязательным)
- **attributes**: новые атрибуты для файла Допустимые атрибуты файла определяются следующим образом.
  - FX_READ_ONLY (0x01)
  - FX_HIDDEN (0x02)
  - FX_SYSTEM (0x04)
  - FX_ARCHIVE (0x20)

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — атрибут успешно задан.
- **FX_ACCESS_ERROR** (0x06) — файл открыт, невозможно задать его атрибуты.
- **FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей в таблице FAT или карте кластера exFAT.
- **FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.
- **FX_NOT_FOUND** (0x04) — указанный файл не найден на носителе.
- **FX_NOT_A_FILE** (0x05) — указанный файл является каталогом.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.
- **FX_MEDIA_INVALID** (0x02) — недопустимый носитель.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.
- **FX_INVALID_ATTR** (0x19) — выбраны недопустимые атрибуты.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c

FX_MEDIA         my_media;
UINT             status;

/* Set the attributes of "myfile.txt" to read-only. */

status = fx_file_attributes_set(&my_media, "myfile.txt", FX_READ_ONLY);

/* If status equals FX_SUCCESS, the file is now read-only. */

```

### <a name="see-also"></a>См. также:

- fx_file_allocate
- fx_file_attributes_read
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_best_effort_allocate"></a>fx_file_best_effort_allocate

Наиболее оптимальное выделение пространства для файла

### <a name="prototype"></a>Прототип

```c
UINT fx_file_best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG size,
    ULONG *actual_size_allocated);
```
### <a name="description"></a>Описание

Эта служба выделяет один кластер или несколько последовательных и связывает их с концом указанного файла. FileX определяет количество кластеров, необходимое для деления запрошенного размера на число байтов на кластер. Затем результат округляется до следующего целого кластера. Если на носителе нет достаточного количества последовательных кластеров, эта служба связывает с файлом самый большой доступный блок последовательных кластеров. Объем пространства, фактически выделяемый файлу, возвращается вызывающему объекту.

Чтобы выделить место свыше 4 ГБ, приложение должно использовать службу *fx_file_extended_best_effort_allocate*.

### <a name="input-parameters"></a>Входные параметры

- **file_ptr**: указатель на открытый ранее файл
- **size**: число байтов, выделяемых для файла

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — наиболее оптимальное выделение пространства для файла успешно выполнено.
- **FX_ACCESS_ERROR** (0x06) — указанный файл не открыт для записи.
- **FX_NOT_OPEN** (0x07) — указанный файл в настоящее время не открыт.
- **FX_NO_MORE_SPACE** (0x0A) — на носителе, связанном с этим файлом, недостаточно доступных кластеров.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель или назначение файла.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c

FX_FILE         my_file;
UINT             status;
ULONG             actual_allocation;

/* Attempt to allocate 1024 bytes to the end of my_file. */

status = fx_file_best_effort_allocate(&my_file, 1024, &actual_allocation);

/* If status equals FX_SUCCESS, the number of bytes
    allocated to the file is found in actual_allocation. */

```

### <a name="see-also"></a>См. также:

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_close"></a>fx_file_close

Закрывает файл

### <a name="prototype"></a>Прототип

```c
UINT fx_file_close(FX_FILE *file_ptr);
```
### <a name="description"></a>Описание

Эта служба закрывает указанный файл. Если файл был открыт для записи и если он был изменен, эта служба завершает процесс изменения файла, обновляя запись каталога с новым размером и текущими системными временем и датой.

### <a name="input-parameters"></a>Входные параметры

- **file_ptr**: указатель на открытый ранее файл

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — файл успешно закрыт.
- **FX_NOT_OPEN** (0x07) — указанный файл не открыт.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_PTR_ERROR** (0x18) — недопустимый носитель или указатель на атрибуты.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c

FX_FILE        my_file;
UINT        status;

/* Close the previously opened file "my_file". */
status = fx_file_close(&my_file);

/* If status equals FX_SUCCESS, the file was closed successfully. */
```

### <a name="see-also"></a>См. также:

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_create"></a>fx_file_create

Создает файл

### <a name="prototype"></a>Прототип

```c
UINT fx_file_create(
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```
### <a name="description"></a>Описание

Эта служба создает указанный файл в каталоге по умолчанию или в каталоге, путь к которому указан с именем файла.

> [!WARNING]
> *Эта служба создает файл нулевой длины, т. е. без выделенных кластеров. Выделение будет автоматически выполняться при последующих операциях записи файла. Также это можно сделать заранее с помощью службы fx_file_allocate или fx_file_extended_allocate, если размер превышает 4 ГБ).*

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **file_name**: указатель на имя создаваемого файла (путь к каталогу является необязательным)

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — файл успешно создан.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_ALREADY_CREATED** (0x0B) — указанный файл уже создан.
- **FX_NO_MORE_SPACE** (0x0A) —  в корневом каталоге больше нет записей, или нет доступных кластеров.
- **FX_INVALID_PATH** (0x0D) — указан недопустимый путь с именем файла.
- **FX_INVALID_NAME** (0x0C) — недопустимое имя файла.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.
- **FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.
- **FX_MEDIA_INVALID** (0x02) — недопустимый носитель.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_WRITE_PROTECT** (0x23) — носитель защищен от записи.
- **FX_PTR_ERROR** (0x18) — недопустимый носитель или указатель имени файла.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c

FX_MEDIA         my_media;
UINT             status;

/* Create a file called "myfile.txt" in the
    root or the default directory of the media. */

status = fx_file_create(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, a zero sized file named "myfile.txt". */
```

### <a name="see-also"></a>См. также:
- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_date_time_set"></a>fx_file_date_time_set

### <a name="sets-file-date-and-time"></a>Задает дату и время файла

Задание даты и времени для файла

### <a name="prototype"></a>Прототип

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
### <a name="description"></a>Описание

Эта служба задает дату и время для указанного файла.

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **file_name**: указатель на имя файла
- **year**: значение года (1980–2107 включительно)
- **month**: значение месяца (1–12 включительно)
- **day**: значение дня (1–31 включительно)
- **hour**: значение часа (0–23 включительно)
- **minute**: значение минуты (0–59 включительно)
- **second**: значение секунды (0–59 включительно)

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — дата/время успешно заданы.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_NOT_FOUND** (0x04) — файл не найден.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.
- **FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.
- **FX_INVALID_YEAR** (0x12) — недопустимый год.
- **FX_INVALID_MONTH** (0x13) — недопустимый месяц.
- **FX_INVALID_DAY** (0x14) — недопустимый день.
- **FX_INVALID_HOUR** (0x15) — недопустимый час.
- **FX_INVALID_MINUTE** (0x16) — недопустимая минута.
- **FX_INVALID_SECOND** (0x17) — недопустимая секунда.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="see-also"></a>См. также:

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_delete"></a>fx_file_delete

### <a name="deletes-file"></a>Удаляет файл

Удаление файла

### <a name="prototype"></a>Прототип

```c
UINT fx_file_delete(
    FX_MEDIA *media_ptr, 
    CHAR *file_name);
```
### <a name="description"></a>Описание

Эта служба удаляет указанный файл.


### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **file_name**: указатель на имя удаляемого файла (путь к каталогу является необязательным)

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — файл успешно удален.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_NOT_FOUND** (0x04) — указанный файл не найден.
- **FX_NOT_A_FILE** (0x05) — указанное имя файла является каталогом или томом.
- **FX_ACCESS_ERROR** (0x06) — указанный файл в настоящее время открыт.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.
- **FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.
- **FX_MEDIA_INVALID** (0x02) — недопустимый носитель.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c

FX_MEDIA            my_media;
UINT                 status;
/* Delete the file "myfile.txt". */

status = fx_file_delete(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, "myfile.txt" has been deleted. */
```

### <a name="see-also"></a>См. также:

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_allocate"></a>fx_file_extended_allocate

Выделяет место для файла

### <a name="prototype"></a>Прототип

```c
UINT fx_file_extended_allocate(
    FX_FILE *file_ptr, 
    ULONG64 size);
```
### <a name="description"></a>Описание

Эта служба выделяет один кластер или несколько последовательных и связывает их с концом указанного файла. FileX определяет количество кластеров, необходимое для деления запрошенного размера на число байтов на кластер. Затем результат округляется до следующего целого кластера.

Эта служба разработана для exFAT. Параметр *size* принимает значение 64-разрядного целого числа, которое позволяет вызывающему объекту предварительно выделить пространство свыше 4 ГБ.

### <a name="input-parameters"></a>Входные параметры

- **file_ptr**: указатель на открытый ранее файл
- **size**: число байтов, выделяемых для файла

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — файл успешно выделен.
- **FX_ACCESS_ERROR** (0x06) — указанный файл не открыт для записи.
- **FX_NOT_OPEN** (0x07) — указанный файл в настоящее время не открыт.
- **FX_NO_MORE_SPACE** (0x0A) — на носителе, связанном с этим файлом, недостаточно доступных кластеров.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель на файл.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c

FX_FILE            my_file;
UINT            status;
/* Allocate 0x100000000 bytes to the end of my_file. */

status = fx_file_extended_allocate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS the file now has
    one or more contiguous cluster(s) that can accommodate at least
    1024 bytes of user data. */
```

### <a name="see-also"></a>См. также:

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_best_effort_allocate"></a>fx_file_extended_best_effort_allocate

Наиболее оптимальное выделение пространства для файла

### <a name="prototype"></a>Прототип

```c
UINT fx_file_extended best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG64 size,
    ULONG64 *actual_size_allocated);
```
### <a name="description"></a>Описание

Эта служба выделяет один кластер или несколько последовательных и связывает их с концом указанного файла. FileX определяет количество кластеров, необходимое для деления запрошенного размера на число байтов на кластер. Затем результат округляется до следующего целого кластера. Если на носителе нет достаточного количества последовательных кластеров, эта служба связывает с файлом самый большой доступный блок последовательных кластеров. Объем пространства, фактически выделяемый файлу, возвращается вызывающему объекту.

Эта служба разработана для exFAT. Параметр *size* принимает значение 64-разрядного целого числа, которое позволяет вызывающему объекту предварительно выделить пространство свыше 4 ГБ.

### <a name="input-parameters"></a>Входные параметры

- **file_ptr**: указатель на открытый ранее файл
- **size**: число байтов, выделяемых для файла

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — файл успешно выделен.
- **FX_ACCESS_ERROR** (0x06) — указанный файл не открыт для записи.
- **FX_NOT_OPEN** (0x07) — указанный файл в настоящее время не открыт.
- **FX_NO_MORE_SPACE** (0x0A) — на носителе, связанном с этим файлом, недостаточно доступных кластеров.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель на файл.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

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

### <a name="see-also"></a>См. также:

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_relative_seek"></a>fx_file_extended_relative_seek

Размещение на указанное относительное смещение в байтах

### <a name="prototype"></a>Прототип

```c
UINT fx_file_extended_relative_seek(
    FX_FILE *file_ptr,
    ULONG64 byte_offset,
    UINT seek_from);
```
### <a name="description"></a>Описание

Эта служба размещает внутренний указатель чтения/записи файла на указанное относительное смещение в байтах. Все последующие запросы на чтение или запись файла будут начинаться с этого места в файле.

Эта служба разработана для exFAT. Параметр *byte_offset* принимает 64-разрядное целочисленное значение, которое позволяет вызывающему объекту изменить расположение указателя чтения/записи за пределами 4 ГБ.

> [!IMPORTANT]
> *Если операция поиска пытается выполнить поиск после конца файла, указатель на чтение и запись файла помещается в конец файла. И наоборот, если операция поиска пытается установить положение после начала файла, указатель на чтение и запись файла помещается в начало файла.*

### <a name="input-parameters"></a>Входные параметры

- **file_ptr**: указатель на открытый ранее файл
- **byte_offset**: требуемое относительное смещение в байтах в файле
- **seek_from**: направление и расположение для выполнения относительного поиска Допустимые параметры чтения определяются следующим образом.
  - FX_SEEK_BEGIN (0x00)
  - FX_SEEK_END (0x01)
  - FX_SEEK_FORWARD (0x02)
  - FX_SEEK_BACK (0x03). Если указан параметр FX_SEEK_BEGIN, операция поиска выполняется с начала файла. Если указан параметр FX_SEEK_END, операция поиска выполняется в обратном направлении с конца файла. Если указан параметр FX_SEEK_FORWARD, операция поиска выполняется вперед от текущего расположения файла. Если указан параметр FX_SEEK_BACK, операция поиска выполняется в обратном направлении от текущей позиции файла.

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — относительный поиск файла успешно выполнен.
- **FX_NOT_OPEN** (0x07) — указанный файл в настоящее время не открыт.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель на файл.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to seek forward 0x100000000 bytes in "my_file". */

status = fx_file_extended_relative_seek(&my_file, 0x100000000, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write
    pointers are positioned 0x100000000 bytes forward. */
```

### <a name="see-also"></a>См. также:

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_seek"></a>fx_file_extended_seek

Размещение на указанное смещение в байтах

### <a name="prototype"></a>Прототип

```c
UINT fx_file_extended_seek(
    FX_FILE *file_ptr, 
    ULONG64 byte_offset);
```
### <a name="description"></a>Описание

Эта служба размещает внутренний указатель чтения/записи файла на указанное смещение в байтах. Все последующие запросы на чтение или запись файла будут начинаться с этого места в файле.

Эта служба разработана для exFAT. Параметр *byte_offset* принимает 64-разрядное целочисленное значение, которое позволяет вызывающему объекту изменить расположение указателя чтения/записи за пределами 4 ГБ.

### <a name="input-parameters"></a>Входные параметры

- **file_ptr**: указатель на блок управления файлом
- **byte_offset**: требуемое смещение в байтах в файле При нулевом значении указатель чтения/записи будет размещен в начале файла, а при значении, превышающем размер файла, указатель чтения/записи будет помещен в конец файла.

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — файл успешно найден.
- **FX_NOT_OPEN** (0x07) — указанный файл не открыт.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель на файл.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_FILE         my_file;
UINT             status;
/* Seek to position 0x100000000 of "my_file." */

status = fx_file_extended_seek(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned 0x100000000 bytes from the beginning of the file. */
```

### <a name="see-also"></a>См. также:

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_truncate"></a>fx_file_extended_truncate

Усекает файл

### <a name="prototype"></a>Прототип

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG64 size);
```
### <a name="description"></a>Описание

Эта служба усекает размер файла до указанного. Если указанный размер превышает фактический размер файла, эта служба не выполняет никаких действий. Ни один из кластеров носителя, связанных с файлом, не освобождается.

> [!WARNING]
> *Проявляйте осторожность при усечении файлов, которые также могут быть открыты для одновременного чтения. Усечение файла, открытого для чтения, может привести к чтению недопустимых данных.*

Эта служба разработана для exFAT. Параметр *size* принимает значение 64-разрядного целого числа, которое позволяет вызывающему объекту действовать за пределами 4 ГБ.

### <a name="input-parameters"></a>Входные параметры

- **file_ptr**: указатель на блок управления файлом
- **size**: новый размер файла Число байтов после нового размера файла не учитывается.

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — файл успешно усечен.
- **FX_NOT_OPEN** (0x07) — указанный файл не открыт.
- **FX_ACCESS_ERROR** (0x06) — указанный файл не открыт для записи.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.
- **FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_WRITE_PROTECT** (0x23) — носитель защищен от записи.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель на файл.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_FILE            my_file;
UINT            status;
/* Truncate "my_file" to 0x100000000 bytes. */

status = fx_file_extended_truncate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, "my_file" contains 0x100000000 or fewer bytes. */
```

### <a name="see-also"></a>См. также:

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_truncate_release"></a>fx_file_extended_truncate_release

Усекает кластеры файлов и выпусков

### <a name="prototype"></a>Прототип

```c
UINT fx_file_extended_truncate_release(
    FX_FILE *file_ptr, 
    ULONG64 size);
```

### <a name="description"></a>Описание

Эта служба усекает размер файла до указанного. Если указанный размер превышает фактический размер файла, эта служба не выполняет никаких действий. В отличие от службы ***fx_file_extended_truncate*** эта служба освобождает неиспользуемые кластеры.

> [!WARNING]
> *Проявляйте осторожность при усечении файлов, которые также могут быть открыты для одновременного чтения. Усечение файла, открытого для чтения, может привести к чтению недопустимых данных.*

Эта служба разработана для exFAT. Параметр *size* принимает значение 64-разрядного целого числа, которое позволяет вызывающему объекту действовать за пределами 4 ГБ.

### <a name="input-parameters"></a>Входные параметры

- **file_ptr**: указатель на открытый ранее файл
- **size**: новый размер файла Число байтов после нового размера файла не учитывается.

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — файл успешно усечен.
- **FX_ACCESS_ERROR** (0x06) — указанный файл не открыт для записи.
- **FX_NOT_OPEN** (0x07) — указанный файл в настоящее время не открыт.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.
- **FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель на файл.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_FILE            my_file;
UINT            status;
/* Attempt to truncate everything after the first 0x100000000 bytes of "my_file". */

status = fx_file_extended_truncate_release(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file is now 0x100000000
    bytes or fewer and all unused clusters have been released. */
```

### <a name="see-also"></a>См. также:

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_open"></a>fx_file_open

Открывает файл

### <a name="prototype"></a>Прототип

```c
UINT fx_file_open(
    FX_MEDIA *media_ptr,
    FX_FILE *file_ptr,
    CHAR *file_name,
    UINT open_type);
```
### <a name="description"></a>Описание

Эта служба открывает указанный файл для чтения или записи. Файл может быть открыт для чтения несколько раз, однако открыть файл для записи можно только один раз, пока модуль записи не закроет файл.

> [!IMPORTANT]
> *Необходимо соблюдать осторожность, если файл параллельно открыт для чтения и записи. Запись файла, выполняемая при одновременном открытии файла для чтения, может не отображаться средством чтения, если только средство чтения не закроет и не откроет файл для чтения. Аналогично, при использовании служб усечения файлов следует соблюдать осторожность. Если файл усекается модулем записи, читатели одного и того же файла могут вернуть недопустимые данные.*

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **file_ptr**: указатель на блок управления файлом
- **file_name**: указатель на имя открываемого файла (путь к каталогу является необязательным)
- **open_type**: тип открываемого файла Допустимые параметры типа открытия
  - FX_OPEN_FOR_READ (0x00)
  - FX_OPEN_FOR_WRITE (0x01)
  - FX_OPEN_FOR_READ_FAST (0x02)

Открытие файлов с помощью FX_OPEN_FOR_READ и FX_OPEN_FOR_READ_FAST выполняется аналогично.

- FX_OPEN_FOR_READ включает проверку того, что связанный список кластеров, составляющих файл, не изменяется, а FX_OPEN_FOR_READ_FAST не выполняет такую проверку, что ускоряет работу.

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — файл успешно открыт.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_NOT_FOUND** (0x04) — указанный файл не найден.
- **FX_NOT_A_FILE** (0x05) — указанное имя файла является каталогом или томом.
- **FX_FILE_CORRUPT** (0x08) — указанный файл поврежден, или его не удалось открыть.
- **FX_ACCESS_ERROR** (0x06) — указанный файл уже открыт, или недопустимый тип открытия.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_MEDIA_INVALID** (0x02) — недопустимый носитель.
- **FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.
- **FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_WRITE_PROTECT** (0x23) — носитель защищен от записи.
- **FX_PTR_ERROR** (0x18) — недопустимый носитель или указатель файла.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_MEDIA     my_media;
FX_FILE     my_file;
UINT         status;

/* Open the file "myfile.txt" for reading. */

status = fx_file_open(&my_media, &my_file, "myfile.txt", FX_OPEN_FOR_READ);

/* If status equals FX_SUCCESS, file "myfile.txt" is now
    open and may be accessed now with the my_file pointer. */
```

### <a name="see-also"></a>См. также:

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_read"></a>fx_file_read

Считывает байты из файла

### <a name="prototype"></a>Прототип

```c
UINT fx_file_read(
    FX_FILE *file_ptr, 
    VOID *buffer_ptr,
    ULONG request_size, 
    ULONG *actual_size);
```
### <a name="description"></a>Описание

Эта служба считывает байты из файла и сохраняет их в заданном буфере. После завершения чтения внутренний указатель чтения файла корректируется так, чтобы он указывал на следующий байт в файле. Если в запросе осталось меньше байтов, в буфер будут сохранены только оставшиеся байты. В любом случае общее число байтов, помещенных в буфер, возвращается вызывающему объекту.

> [!WARNING]
> *Приложение должно гарантировать, что предоставленный буфер способен хранить указанное число запрошенных байтов.*

> [!WARNING]
> *Более высокая производительность достигается тогда, когда буфер назначения находится на границе длинного слова, а запрошенный размер делится на sizeof(**ULONG**) без остатка.*

### <a name="input-parameters"></a>Входные параметры

- **file_ptr**: указатель на блок управления файлом
- **buffer_ptr**: указатель на буфер назначения для чтения
- **request_size**: максимальное количество байтов для чтения
- **actual_size**: указатель на переменную для хранения фактического числа байтов, считанных в указанный буфер

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — чтение из файла успешно выполнено.
- **FX_NOT_OPEN** (0x07) — указанный файл не открыт.
- **FX_FILE_CORRUPT** (0x08) — указанный файл поврежден,и не удалось выполнить чтение.
- **FX_END_OF_FILE** (0x09) — достигнут конец файла.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель на файл или буфер.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

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
### <a name="see-also"></a>См. также:

- fx_file_allocate,
- fx_file_attributes_read,
- fx_file_attributes_set,
- fx_file_best_effort_allocate,
- fx_file_close,
- fx_file_create,
- fx_file_date_time_set,
- fx_file_delete,
- fx_file_extended_allocate,
- fx_file_extended_best_effort_allocate,
- fx_file_extended_relative_seek,
- fx_file_extended_seek,
- fx_file_extended_truncate,
- fx_file_extended_truncate_release,
- fx_file_open,
- fx_file_relative_seek,
- fx_file_rename,
- fx_file_seek,
- fx_file_truncate,
- fx_file_truncate_release,
- fx_file_write,
- fx_file_write_notify_set,
- fx_unicode_file_create,
- fx_unicode_file_rename,
- fx_unicode_name_get,
- fx_unicode_short_name_get

## <a name="fx_file_relative_seek"></a>fx_file_relative_seek

Размещение на указанное относительное смещение в байтах

### <a name="prototype"></a>Прототип

```c
UINT fx_file_relative_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset,
    UINT seek_from);
```
### <a name="description"></a>Описание

Эта служба размещает внутренний указатель чтения/записи файла на указанное относительное смещение в байтах. Все последующие запросы на чтение или запись файла будут начинаться с этого места в файле.

> [!IMPORTANT]
> *Если операция поиска пытается выполнить поиск после конца файла, указатель на чтение и запись файла помещается в конец файла. И наоборот, если операция поиска пытается установить положение после начала файла, указатель на чтение и запись файла помещается в начало файла.*

Чтобы найти значение смещения, превышающее 4 ГБ, приложение должно использовать службу *fx_file_extended_relative_seek*.

### <a name="input-parameters"></a>Входные параметры

- **file_ptr**: указатель на открытый ранее файл
- **byte_offset**: требуемое относительное смещение в байтах в файле
- **seek_from**: направление и расположение для выполнения относительного поиска Допустимые параметры чтения определяются следующим образом.
  - FX_SEEK_BEGIN (0x00)
  - FX_SEEK_END (0x01)
  - FX_SEEK_FORWARD (0x02)
  - FX_SEEK_BACK (0x03)

Если указан параметр FX_SEEK_BEGIN, операция поиска выполняется с начала файла. Если указан параметр FX_SEEK_END, операция поиска выполняется в обратном направлении с конца файла. Если указан параметр FX_SEEK_FORWARD, операция поиска выполняется вперед от текущего расположения файла. Если указан параметр FX_SEEK_BACK, операция поиска выполняется в обратном направлении от текущей позиции файла.

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — относительный поиск файла успешно выполнен.
- **FX_NOT_OPEN** (0x07) — указанный файл в настоящее время не открыт.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель на файл.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to move 10 bytes forward in "my_file". */

status = fx_file_relative_seek(&my_file, 10, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write pointers
    are positioned 10 bytes forward. */
```

### <a name="see-also"></a>См. также:

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_rename"></a>fx_file_rename

Переименовывает файл

### <a name="prototype"></a>Прототип

```c
UINT fx_file_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_file_name,
    CHAR *new_file_name);
```
### <a name="description"></a>Описание

Эта служба изменяет имя файла, указанного параметром *old_file_name*. Переименование также выполняется относительно указанного пути или пути по умолчанию. Если в новом имени файла указан путь, переименованный файл фактически перемещается по указанному пути. Если путь не указан, переименованный файл помещается в текущий путь по умолчанию.

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **old_file_name**: указатель на имя переименовываемого файла (путь к каталогу является необязательным)
- **new_file_name**: указатель на новое имя файла Путь к каталогу не допускается.

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — файл успешно переименован.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_NOT_FOUND** (0x04) — указанный файл не найден.
- **FX_NOT_A_FILE** (0x05) — указанный файл является каталогом.
- **FX_ACCESS_ERROR** (0x06) — указанный файл уже открыт.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.
- **FX_INVALID_NAME** (0x0C) — указанное новое имя файла не является допустимым именем файла.
- **FX_INVALID_PATH** (0x0D) — недопустимый путь.
- **FX_ALREADY_CREATED** (0x0B) — новое имя файла уже используется.
- **FX_MEDIA_INVALID** (0x02) — недопустимый носитель.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.
- **FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.
- **FX_FAT_READ_ERROR** (0x03) — не удается прочитать таблицу FAT.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_MEDIA         my_media;
UINT             status;

/* Rename "myfile1.txt" to "myfile2.txt" in the default directory of the media. */

status = fx_file_rename(&my_media, "myfile1.txt", "myfile2.txt");

/* If status equals FX_SUCCESS, the file was successfully renamed. */
```

### <a name="see-also"></a>См. также:

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_seek"></a>fx_file_seek

Размещение на указанное смещение в байтах

### <a name="prototype"></a>Прототип

```c
UINT fx_file_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset);
```
### <a name="description"></a>Описание

Эта служба размещает внутренний указатель чтения/записи файла на указанное смещение в байтах. Все последующие запросы на чтение или запись файла будут начинаться с этого места в файле.

Чтобы найти значение смещения, превышающее 4 ГБ, приложение должно использовать службу *fx_file_extended_seek*.

### <a name="input-parameters"></a>Входные параметры

- **file_ptr**: указатель на блок управления файлом
- **byte_offset**: требуемое смещение в байтах в файле При нулевом значении указатель чтения/записи будет размещен в начале файла, а при значении, превышающем размер файла, указатель чтения/записи будет помещен в конец файла.

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — файл успешно найден.
- **FX_NOT_OPEN** (0x07) — указанный файл не открыт.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель на файл.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_FILE            my_file;
UINT            status;
/* Seek to the beginning of "my_file." */
status = fx_file_seek(&my_file, 0);
/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned to the beginning of the file. */
```

### <a name="see-also"></a>См. также:

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_truncate"></a>fx_file_truncate

Усекает файл

### <a name="prototype"></a>Прототип

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```

### <a name="description"></a>Описание

Эта служба усекает размер файла до указанного. Если указанный размер превышает фактический размер файла, эта служба не выполняет никаких действий. Ни один из кластеров носителя, связанных с файлом, не освобождается.

> [!WARNING]
> *Проявляйте осторожность при усечении файлов, которые также могут быть открыты для одновременного чтения. Усечение файла, открытого для чтения, может привести к чтению недопустимых данных.*

Если размер превышает 4 ГБ, приложение должно использовать службу *fx_file_extended_truncate*.

### <a name="input-parameters"></a>Входные параметры

- **file_ptr**: указатель на блок управления файлом
- **size**: новый размер файла Число байтов после нового размера файла не учитывается.

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — файл успешно усечен.
- **FX_NOT_OPEN** (0x07) — указанный файл не открыт.
- **FX_ACCESS_ERROR** (0x06) — указанный файл не открыт для записи.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.
- **FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель на файл.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_FILE                my_file;
UINT                status;
/* Truncate "my_file" to 100 bytes. */

status = fx_file_truncate(&my_file, 100);

/* If status equals FX_SUCCESS, "my_file" contains 100 or fewer bytes. */
```

### <a name="see-also"></a>См. также:

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_truncate_release"></a>fx_file_truncate_release

Усекает кластеры файлов и выпусков

### <a name="prototype"></a>Прототип

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```
### <a name="description"></a>Описание

Эта служба усекает размер файла до указанного. Если указанный размер превышает фактический размер файла, эта служба не выполняет никаких действий. В отличие от службы ***fx_file_truncate*** эта служба освобождает неиспользуемые кластеры.

> [!WARNING]
> *Проявляйте осторожность при усечении файлов, которые также могут быть открыты для одновременного чтения. Усечение файла, открытого для чтения, может привести к чтению недопустимых данных.*

Если размер превышает 4 ГБ, приложение должно использовать службу *fx_file_extended_truncate_release*.

### <a name="input-parameters"></a>Входные параметры

- **file_ptr**: указатель на открытый ранее файл
- **size**: новый размер файла Число байтов после нового размера файла не учитывается.

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — файл успешно усечен.
- **FX_ACCESS_ERROR** (0x06) — указанный файл не открыт для записи.
- **FX_NOT_OPEN** (0x07) — указанный файл в настоящее время не открыт.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_WRITE_PROTECT** (0x23) — носитель защищен от записи.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.
- **FX_NO_MORE_SPACE** (0x0A) — нет места для завершения операции.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель на файл.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_FILE         my_file;
UINT             status;

/* Attempt to truncate everything after the first 100 bytes of "my_file". */

status = fx_file_truncate_release(&my_file, 100);

/* If status equals FX_SUCCESS, the file is now 100 bytes
    or fewer and all unused clusters have been released. */
```
### <a name="see-also"></a>См. также:

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_write"></a>fx_file_write

Записывает байты в файл

### <a name="prototype"></a>Прототип

```c
UINT fx_file_write(
    FX_FILE *file_ptr,
    VOID *buffer_ptr,
    ULONG size);
```
### <a name="description"></a>Описание

Эта служба записывает байты из указанного буфера, начиная с текущей позиции файла. После завершения записи внутренний указатель чтения файла корректируется так, чтобы он указывал на следующий байт в файле.

> [!WARNING]
> *Более высокая производительность достигается тогда, когда исходный буфер находится на границе длинного слова, а запрошенный размер делится на sizeof(**ULONG**) без остатка.*

### <a name="input-parameters"></a>Входные параметры

- **file_ptr**: указатель на блок управления файлом
- **buffer_ptr**: указатель на исходный буфер для записи
- **size**: количество байтов для записи

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — запись в файл успешно выполнена.
- **FX_NOT_OPEN** (0x07) — указанный файл не открыт.
- **FX_ACCESS_ERROR** (0x06) — указанный файл не открыт для записи.
- **FX_NO_MORE_SPACE** (0x0A) — недостаточно места на носителе для выполнения этой операции записи.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_FAT_READ_ERROR** (0x03) — не удается прочитать запись FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) — больше нет записей FAT.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель на файл или буфер.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_FILE            my_file;
UINT            status;
/* Write a 10 character buffer to "my_file." */

status = fx_file_write(&my_file, "1234567890", 10);

/* If status equals FX_SUCCESS, the small text string was written out to the file. */
```

### <a name="see-also"></a>См. также:

- fx_file_allocate,
- fx_file_attributes_read,
- fx_file_attributes_set,
- fx_file_best_effort_allocate,
- fx_file_close,
- fx_file_create,
- fx_file_date_time_set,
- fx_file_delete,
- fx_file_extended_allocate,
- fx_file_extended_best_effort_allocate,
- fx_file_extended_relative_seek,
- fx_file_extended_seek,
- fx_file_extended_truncate,
- fx_file_extended_truncate_release,
- fx_file_open,
- fx_file_read,
- fx_file_relative_seek,
- fx_file_rename,
- fx_file_seek,
- fx_file_truncate,
- fx_file_truncate_release,
- fx_file_write_notify_set,
- fx_unicode_file_create,
- fx_unicode_file_rename,
- fx_unicode_name_get,
- fx_unicode_short_name_get

## <a name="fx_file_write_notify_set"></a>fx_file_write_notify_set

Задает функцию уведомления о записи в файл

### <a name="prototype"></a>Прототип

```c
UINT fx_file_write_notify_set(
    FX_FILE *file_ptr,
    VOID (*file_write_notify)(FX_FILE*));
```
### <a name="description"></a>Описание

Эта служба устанавливает функцию обратного вызова, которая вызывается после успешной операции записи в файл.

### <a name="input-parameters"></a>Входные параметры

- **file_ptr**: указатель на блок управления файлом
- **file_write_notify**: устанавливаемая функция обратного вызова записи в файл Задайте для функции обратного вызова значение NULL, чтобы отключить функцию обратного вызова.

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — функция обратного вызова успешно установлена.
- **FX_PTR_ERROR** (0x18) — file_ptr имеет значение NULL.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
fx_file_write_notify_set(file_ptr, my_file_close_callback);

```

### <a name="see-also"></a>См. также:

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_media_abort"></a>fx_media_abort

Прерывает действия носителя

### <a name="prototype"></a>Прототип

```c
UINT fx_media_abort(FX_MEDIA *media_ptr);
```
### <a name="description"></a>Описание

Эта служба прерывает все текущие действия, связанные с носителем, включая закрытие всех открытых файлов, отправку запроса на прерывание соответствующему драйверу и помещение носителя в состояние прерванной работы. Эта служба обычно вызывается при обнаружении ошибок ввода-вывода.

> [!WARNING]
> *Чтобы повторно использовать носитель после выполнения операции прерывания, его необходимо открыть повторно.*

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — работа носителя успешно прервана.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_MEDIA    my_media;
UINT        status;
/* Abort all activity associated with "my_media". */

status = fx_media_abort(&my_media);

/* If status equals FX_SUCCESS, all activity
    associated with the media has been aborted. */

```

### <a name="see-also"></a>См. также:

- fx_fault_tolerant_enable
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_cache_invalidate"></a>fx_media_cache_invalidate

Делает недействительным кэш логического сектора

### <a name="prototype"></a>Прототип

```c
UINT fx_media_cache_invalidate(FX_MEDIA *media_ptr);
```

### <a name="description"></a>Описание

Эта служба очищает все "грязные" секторы в кэше, а затем делает недействительным весь кэш логического сектора.

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — кэш носителя успешно сделан недействительным.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или временной памяти.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_MEDIA     my_media;

/* Invalidate the cache of the media. */
status = fx_media_cache_invalidate(&my_media);

/* If status is FX_SUCCESS the cache in the media
    was successfully flushed and invalidated. */

```

### <a name="see-also"></a>См. также:

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_check"></a>fx_media_check

Проверяет наличие ошибок на носителе

### <a name="prototype"></a>Прототип

```c
UINT fx_media_check(
    FX_MEDIA *media_ptr,
    UCHAR *scratch_memory_ptr,
    ULONG scratch_memory_size,
    ULONG error_correction_option,
    ULONG *errors_detected_ptr);
```
### <a name="description"></a>Описание

Эта служба проверяет указанный носитель на наличие базовых структурных ошибок, включая перекрестные ссылки на файлы и каталоги, недопустимые цепочки FAT и потерянные кластеры. Эта служба также предоставляет возможность исправить обнаруженные ошибки.

Служба fx_media_check требует наличия вспомогательной памяти для предварительного анализа глубины вложения каталогов и файлов на носителе. В частности, вспомогательная память, предоставленная службе проверки носителей, должна быть достаточно большой для хранения нескольких записей каталога, структуры данных для помещения в стек текущей позиции записи каталога перед входом в подкаталоги и, наконец, логической битовой карты FAT. Объем вспомогательной памяти должен составлять по крайней мере 512–1024 байт плюс память для логической файловой системы FAT, для которой требуется столько битов, сколько кластеров находится в носителе. Например, устройству с 8000 кластерам потребовалось бы 1000 байт для представления и, таким образом, требуемый размер общей временной области составляет порядка 2048 байт.

> [!WARNING]
> *Эту службу следует вызывать только сразу после fx_media_open и без каких бы то ни было других действий с файловой системой.*

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **scratch_memory_ptr**: указатель на начало вспомогательной памяти
- **scratch_memory_size**: размер вспомогательной памяти в байтах
- **error_correction_option**: биты при исправлении ошибок, если бит задан, выполняется исправление ошибок Биты параметра исправления ошибок определяются следующим образом.
  - FX_FAT_CHAIN_ERROR (0x01)
  - FX_DIRECTORY_ERROR (0x02)
  - FX_LOST_CLUSTER_ERROR (0x04): просто ИЛИ вместе с необходимыми параметрами исправления ошибок Если исправление ошибок не требуется, необходимо указать значение 0.
- **errors_detected_ptr**: назначение для битов обнаружения ошибок, как определено ниже.
  - FX_FAT_CHAIN_ERROR (0x01)
  - FX_DIRECTORY_ERROR (0x02) FX_LOST_CLUSTER_ERROR (0x04)
  - FX_FILE_SIZE_ERROR (0x08)

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — носитель успешно проверен; ознакомьтесь со сведениями об обнаруженных ошибках.
- **FX_ACCESS_ERROR** (0x06) — не удается выполнить проверку с открытыми файлами.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_NO_MORE_SPACE** (0x0A) — на носителе больше нет места.
- **FX_NOT_ENOUGH_MEMORY** (0x91) — указан недостаточный размер вспомогательной памяти.
- **FX_ERROR_NOT_FIXED** (0x93) — повреждение корневого каталога FAT32, которое не удалось исправить.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или временной памяти.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.


### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

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

### <a name="see-also"></a>См. также:

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_close"></a>fx_media_close

Закрывает носитель

### <a name="prototype"></a>Прототип

```c
UINT fx_media_close(FX_MEDIA *media_ptr);
```
### <a name="description"></a>Описание

Эта служба закрывает указанный носитель. В процессе закрытия носителя все открытые файлы закрываются, а оставшиеся буферы записываются на физический носитель.

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — носитель успешно закрыт.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_MEDIA    my_media;
UINT        status;
/* Close "my_media". */

status = fx_media_close(&my_media);

/* If status equals FX_SUCCESS, "my_media" is closed. */

```

### <a name="see-also"></a>См. также:

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_close_notify_set"></a>fx_media_close_notify_set

Задает функцию уведомления о закрытии носителя

### <a name="prototype"></a>Прототип

```c
UINT fx_media_close_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_close_notify)(FX_MEDIA*));
```

### <a name="description"></a>Описание

Эта служба задает функцию обратного вызова уведомления, которая будет вызываться после успешного закрытия носителя.

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **media_close_notify**: функция обратного вызова уведомления о закрытии носителя для установки Передача значения NULL в качестве функции обратного вызова отключает обратный вызов закрытия носителя.

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — функция обратного вызова успешно установлена.
- **FX_PTR_ERROR** (0x18) — параметр media_ptr имеет значение NULL.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
fx_media_close_notify_set(media_ptr, my_media_close_callback);

```
### <a name="see-also"></a>См. также:

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_exfat_format"></a>fx_media_exFAT_format

Форматирует носитель

### <a name="prototype"></a>Прототип

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
### <a name="description"></a>Описание

Эта служба форматирует указанный носитель в формате, совместимом с exFAT, на основе заданных параметров. Эту службу следует вызывать перед открытием носителя.

> [!WARNING]
> *Форматирование уже отформатированного носителя фактически приводит к удалению всех файлов и каталогов на нем.*

> [!IMPORTANT]
> *Размер тома exFAT должен соответствовать размеру раздела (при наличии макета MBR или GPT) или размеру всего устройства, если макет раздела отсутствует (MBR или GPT). В Windows существует ограничение, из-за которого диск exFAT не будет распознан, если он отформатирован с опреленными значениями общего числа секторов, которое меньше числа доступных секторов.*

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем Он используется только для предоставления некоторых основных сведений, необходимых для функционирования драйвера.
- **driver**: указатель на драйвер ввода-вывода для этого носителя Обычно это тот же драйвер, который передается последующему вызову fx_media_open.
- **driver_info_ptr**: указатель на необязательные сведения, которые может использовать драйвер ввода-вывода
- **memory_ptr**: указатель на рабочую память для носителя memory_size: указывает размер рабочей памяти носителя Размер должен быть не меньше размера сектора носителя.
- **volume_name**: указатель на строку имени тома (не более 11 символов)
- **number_of_fats**: количество FAT на носителе Текущая реализация поддерживает одну FAT на носителе.
- **hidden_sectors**: количество секторов, скрытых перед загрузочным сектором этого носителя Это характерно при наличии нескольких разделов.
- **total_sectors**: общее количество секторов на носителе
- **bytes_per_sector**: число байтов на сектор (обычно 512) Для FileX требуется, чтобы оно было кратным 32.
- **sectors_per_cluster**: количество секторов в каждом кластере Кластер является минимальной единицей размещения в файловой системе FAT.
- **volumne_serial_number**: серийный номер, используемый для этого тома
- **boundary_unit**: размер для выравнивания области физических данных (в количестве секторов)

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — носитель успешно отформатирован.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_PTR_ERROR** (0x18) — недопустимый носитель, драйвер или указатель на память.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

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

### <a name="see-also"></a>См. также:

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_extended_space_available"></a>fx_media_extended_space_available

Возвращает доступное пространство на носителе

### <a name="prototype"></a>Прототип

```c
UINT fx_media_extended_space_available(
    FX_MEDIA *media_ptr,
    ULONG64 *available_bytes_ptr);
```
### <a name="description"></a>Описание

Эта служба возвращает число байтов, доступных на носителе.

Эта служба разработана для exFAT. Указатель на параметр *available_bytes* принимает значение 64-разрядного целого числа, которое позволяет вызывающему объекту работать с носителями объемом свыше 4 ГБ.

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на открытый ранее носитель
- **available_bytes_ptr**: число байтов, доступное на носителе

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — доступное место на носителе успешно получено.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель на носитель, или доступное количество байтов имеет значение NULL.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_MEDIA        my_media;
ULONG64            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_extended_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a>См. также:

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_flush"></a>fx_media_flush

Записывает данные на физический носитель

### <a name="prototype"></a>Прототип

```c
UINT fx_media_flush(FX_MEDIA *media_ptr);
```
### <a name="description"></a>Описание

Эта служба записывает все кэшированные секторы и записи каталога всех измененных файлов на физический носитель.

> [!WARNING]
> *Эта процедура может периодически вызываться приложением для снижения риска повреждения файла и (или) потери данных в случае внезапного отключения питания целевого объекта.*

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — запись на диск успешно выполнена.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_MEDIA         my_media;
UINT             status;

/* Flush all cached sectors and modified file entries to the physical media. */

status = fx_media_flush(&my_media);

/* If status equals FX_SUCCESS, the physical media is completely up-to-date. */

```

### <a name="see-also"></a>См. также:

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_format"></a>fx_media_format

Форматирует носитель

### <a name="prototype"></a>Прототип

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
### <a name="description"></a>Описание

Эта служба форматирует указанный носитель в формате, совместимом с FAT 12/16/32, на основе заданных параметров. Эту службу следует вызывать перед открытием носителя.

> [!WARNING]
> *Форматирование уже отформатированного носителя фактически приводит к удалению всех файлов и каталогов на нем.*

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем Он используется только для предоставления некоторых основных сведений, необходимых для функционирования драйвера.
- **driver**: указатель на драйвер ввода-вывода для этого носителя Обычно это тот же драйвер, который передается последующему вызову fx_media_open.
- **driver_info_ptr**: указатель на необязательные сведения, которые может использовать драйвер ввода-вывода
- **memory_ptr**: указатель на рабочую память для носителя
- **memory_size** указывает размер рабочей памяти носителя Размер должен быть не меньше размера сектора носителя.
- **volume_name**: указатель на строку имени тома (не более 11 символов)
- **number_of_fats**: количество FAT на носителе Минимальное значение равно 1 для основной файловой системы FAT. Значения, превышающие 1, приводят к поддержке дополнительных копий FAT во время выполнения.
- **directory_entries**: количество записей каталога в корневом каталоге
- **hidden_sectors**: количество секторов, скрытых перед загрузочным сектором этого носителя Это характерно при наличии нескольких разделов.
- **total_sectors**: общее количество секторов на носителе
- **bytes_per_sector**: число байтов на сектор (обычно 512) Для FileX требуется, чтобы оно было кратным 32.
- **sectors_per_cluster**: количество секторов в каждом кластере Кластер является минимальной единицей размещения в файловой системе FAT.
- **heads**: количество физических головок
- **sectors_per_track**: количество секторов на дорожке

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — носитель успешно отформатирован.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_PTR_ERROR** (0x18) — недопустимый носитель, драйвер или указатель на память.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

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

### <a name="see-also"></a>См. также:

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_open"></a>fx_media_open

Открывает носитель для доступа к файлам

### <a name="prototype"></a>Прототип

```c
UINT fx_media_open(
    FX_MEDIA *media_ptr, 
    CHAR *media_name,
    VOID(*media_driver)(FX_MEDIA *),
    VOID *driver_info_ptr,
    VOID *memory_ptr, 
    ULONG memory_size);
```
### <a name="description"></a>Описание

Эта служба открывает носитель для доступа к файлам с помощью предоставляемого драйвера ввода-вывода.

> [!WARNING]
> *Память, предоставляемая этой службе, используется для реализации внутреннего кэша логических секторов, поэтому чем больше памяти выделяется, тем меньше снижается объем физического ввода-вывода. Для FileX требуется кэш по крайней мере для одного логического сектора (байт на сектор носителя).*

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **media_name**: указатель на имя носителя
- **media_driver**: указатель на драйвер ввода-вывода для этого носителя Драйвер ввода-вывода должен соответствовать требованиям к драйверу FileX, определенным в главе 5.
- **driver_info_ptr**: указатель на необязательные сведения, которые может использовать указанный драйвер ввода-вывода
- **memory_ptr**: указатель на рабочую память для носителя
- **memory_size** указывает размер рабочей памяти носителя Размер должен быть больше, чем размер сектора носителя (обычно 512 байт).

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — носитель успешно открыт.
- **FX_BOOT_ERROR** (0x01) — ошибка при чтении загрузочного сектора носителя.
- **FX_MEDIA_INVALID** (0x02) — указанный загрузочный сектор носителя поврежден или недопустим. Кроме того, этот код возврата используется, чтобы указать, что либо размер кэша логического сектора, либо размер записи FAT не является степенью 2.
- **FX_FAT_READ_ERROR** (0x03) — ошибка при чтении FAT носителя.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_PTR_ERROR** (0x18) — один указатель или несколько имеют значение NULL.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_MEDIA         ram_disk,
UINT             status;
UCHAR             buffer[128];
/* Open a 32KByte RAM disk starting at the fixed address of 0x800000.
    Note that the total 32KByte media size and 128-byte sector size is defined inside of the driver. */

status = fx_media_open(&ram_disk, "RAM DISK", fx_ram_driver, 0, &buffer[0], sizeof(buffer));

/* If status equals FX_SUCCESS, the RAM disk has been successfully setup and is ready for file access! */

```

### <a name="see-also"></a>См. также:

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_open_notify_set"></a>fx_media_open_notify_set

Задает функцию уведомления об открытии носителя

### <a name="prototype"></a>Прототип

```c
UINT fx_media_open_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_open_notify)(FX_MEDIA*));
```
### <a name="description"></a>Описание

Эта служба задает функцию обратного вызова уведомления, которая будет вызываться после успешного открытия носителя.

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **media_open_notify**: функция обратного вызова уведомления об открытии носителя для установки Передача значения NULL в качестве функции обратного вызова отключает обратный вызов открытия носителя.

### <a name="return-values"></a>Возвращаемые значения


- **FX_SUCCESS** (0x00) — функция обратного вызова успешно установлена.
- **FX_PTR_ERROR** (0x18) — параметр media_ptr имеет значение NULL.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
fx_media_open_notify_set(media_ptr, my_media_open_callback);

```

### <a name="see-also"></a>См. также:

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_read"></a>fx_media_read

Чтение логического сектора с носителя

### <a name="prototype"></a>Прототип

```c
UINT fx_media_read(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector, 
    VOID *buffer_ptr);
```
### <a name="description"></a>Описание

Эта служба считывает логический сектор с носителя и помещает его в указанный буфер.

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на открытый ранее носитель
- **logical_sector**: логический сектор для считывания
- **buffer_ptr**: указатель на назначение для считывания логического сектора

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — носитель успешно считан.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель на носитель или буфер.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_MEDIA         my_media;
UCHAR             my_buffer[128];
UINT            STATUS;
/* Read logical sector 22 into "my_buffer" assuming the
    physical media has a sector size of 128. */
status = fx_media_read(&my_media, 22, my_buffer);
/* If status equals FX_SUCCESS, the contents of logical sector 22 are in "my_buffer". */
```

### <a name="see-also"></a>См. также:

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_space_available"></a>fx_media_space_available

Возвращает доступное пространство на носителе

### <a name="prototype"></a>Прототип

```c
UINT fx_media_space_available(
    FX_MEDIA *media_ptr,
    ULONG *available_bytes_ptr);
```

### <a name="description"></a>Описание

Эта служба возвращает число байтов, доступных на носителе.

Для работы с носителями объемом более 4 ГБ приложение должно использовать службу *fx_media_extended_space_available*.

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на открытый ранее носитель
- **available_bytes_ptr**: число байтов, доступное на носителе

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — доступное место на носителе успешно возвращено.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель на носитель, или доступное количество байтов имеет значение NULL.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_MEDIA        my_media;
ULONG            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a>См. также:

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_volume_get"></a>fx_media_volume_get

Получает имя тома носителя

### <a name="prototype"></a>Прототип

```c
UINT fx_media_volume_get(
    FX_MEDIA *media_ptr,
    CHAR *volume_name,
    UINT volume_source);
```
### <a name="description"></a>Описание

Эта служба получает имя тома ранее открытого носителя.

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **volume_name**: указатель на место назначения для имени тома Обратите внимание, что место назначения должно быть как достаточно большим, чтобы вместить 12 символов.
- **volume_source**: указывает, где следует получить имя из загрузочного или корневого каталога Допустимые значения для этого параметра:
  - FX_BOOT_SECTOR
  - FX_DIRECTORY_SECTOR

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — том носителя успешно получен.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_NOT_FOUND** (0x04) — том не найден.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель места назначения носителя или тома.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_MEDIA        ram_disk;
UCHAR             volume_name[12];
/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name), FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */

```

### <a name="see-also"></a>См. также:

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_volume_get_extended"></a>fx_media_volume_get_extended

Получает имя тома ранее открытого носителя.

### <a name="prototype"></a>Прототип

```c
UINT fx_media_volume_get_extended(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name,
    UINT volume_name_buffer_length,
    UINT volume_source);
```
### <a name="description"></a>Описание

Эта служба получает имя тома ранее открытого носителя.

> [!IMPORTANT]
> Эта служба идентична ***fx_media_volume_get()** _, за исключением того, что вызывающий объект передает размер буфера _ *volume_name**.

### <a name="input-parameters"></a>Входные параметры


- **media_ptr**: указатель на блок управления носителем
- **volume_name**: указатель на место назначения для имени тома Обратите внимание, что место назначения должно быть как достаточно большим, чтобы вместить 12 символов.
- **volume_name_buffer_length**: размер буфера volume_name
- **volume_source**: указывает, где следует получить имя из загрузочного или корневого каталога Допустимые значения для этого параметра:
  - FX_BOOT_SECTOR
  - FX_DIRECTORY_SECTOR

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — том носителя успешно получен.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_NOT_FOUND** (0x04) — том не найден.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель места назначения носителя или тома.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_MEDIA         ram_disk;
UCHAR             volume_name[12];

/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name),
                                      FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */
```

### <a name="see-also"></a>См. также:

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_volume_set"></a>fx_media_volume_set

Задает имя тома носителя

### <a name="prototype"></a>Прототип

```c
UINT fx_media_volume_set(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name);
```
### <a name="description"></a>Описание

Эта служба задает имя тома для ранее открытого носителя.

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **volume_name**: указатель на имя тома

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — том носителя успешно задан.
- **FX_INVALID_NAME** (0x0C) — недопустимый параметр volume_name.
- **FX_MEDIA_INVALID** (0x02) — не удается задать имя тома.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени тома.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
FX_MEDIA ram_disk;

/* Set the volume name to "MY_VOLUME". */

status = fx_media_volume_set(&ram_disk, "MY_VOLUME");

/* If status is FX_SUCCESS, the volume name was successfully set. */
```

### <a name="see-also"></a>См. также:

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_write
- fx_system_initialize

## <a name="fx_media_write"></a>fx_media_write

Записывает логический сектор

### <a name="prototype"></a>Прототип

```c
UINT fx_media_write(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector,
    VOID *buffer_ptr);
```
### <a name="description"></a>Описание

Эта служба записывает указанный буфер в указанный логический сектор.

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на открытый ранее носитель
- **logical_sector**: логический сектор для записи
- **buffer_ptr**: указатель на источник для записи логического сектора

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — запись на носитель успешно выполнена.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель носителя.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

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

### <a name="see-also"></a>См. также:

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_system_initialize

## <a name="fx_system_date_get"></a>fx_system_date_get

Возвращает дату файловой системы

### <a name="prototype"></a>Прототип

```c
UINT fx_system_date_get(
    UINT *year, 
    UINT *month, 
    UINT *day);
```
### <a name="description"></a>Описание

Эта служба возвращает текущую системную дату.

### <a name="input-parameters"></a>Входные параметры

- **year**: указатель на назначение для года
- **month**: указатель на назначение для месяца
- **day**: указатель на назначение для дня

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — дата успешно получена.
- **FX_PTR_ERROR** (0x18) — один входной параметр ил несколько имеют значение NULL.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

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

### <a name="see-also"></a>См. также:

- fx_system_date_set
- fx_system_initialize
- fx_system_time_get
- fx_system_time_set

## <a name="fx_system_date_set"></a>fx_system_date_set

Задает системную дату

### <a name="prototype"></a>Прототип

```c
UINT fx_system_date_set(
    UINT year, 
    UINT month, 
    UINT day);
```

### <a name="description"></a>Описание

Эта служба задает системную дату указанным образом.

> [!WARNING]
> *Эту службу следует вызывать вскоре после **fx_system_initialize** для задания начальной системной даты. По умолчанию системная дата является датой последнего общего выпуска FileX.*

### <a name="input-parameters"></a>Входные параметры

- **year**: новый год Допустимый диапазон — от 1980 до 2107.
- **month**: новый месяц Допустимый диапазон — от 1 до 12.
- **day**: новый день Допустимый диапазон — от 1 до 31 (в зависимости от месяца и високосного года).

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — дата успешно задана.
- **FX_INVALID_YEAR** (0x12) — указан недопустимый год.
- **FX_INVALID_MONTH** (0x13) — указан недопустимый месяц.
- **FX_INVALID_DAY** (0x14) — указан недопустимый день.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Пример

```c
 UINT             status;

/* Set the system date to December 12, 2005. */

status = fx_system_date_set(2005, 12, 12);

/* If status equals FX_SUCCESS, the file system date is now
    12-12-2005. */
```

### <a name="see-also"></a>См. также:

- fx_system_date_get
- fx_system_initialize
- fx_system_time_get
- fx_system_time_set

## <a name="fx_system_initialize"></a>fx_system_initialize

Инициализирует всю систему

### <a name="prototype"></a>Прототип

```c
VOID fx_system_initialize(void);
```

### <a name="description"></a>Описание

Эта служба инициализирует все основные структуры данных FileX. Следует вызывать либо в ***tx_application_define***, либо, возможно, из потока инициализации, а также следует вызывать перед использованием любой другой службы FileX.

> [!WARNING]
> *После инициализации этим вызовом приложение должно вызвать ***fx_system_date_set** _ и _ *fx_system_time_set**, чтобы начать с точных системных даты и времени.*

### <a name="input-parameters"></a>Входные параметры

Нет

### <a name="return-values"></a>Возвращаемые значения

Нет.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Пример

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

### <a name="see-also"></a>См. также:

- fx_system_date_get
- fx_system_date_set
- fx_system_time_get
- fx_system_time_set

## <a name="fx_system_time_get"></a>fx_system_time_get

Получает текущее системное время

### <a name="prototype"></a>Прототип

```c
UINT fx_system_time_get(
    UINT *hour,
    UINT *minute,
    UINT *second);
```

### <a name="description"></a>Описание

Эта служба получает текущее системное время.

### <a name="input-parameters"></a>Входные параметры

- **hour**: указатель на назначение для часа
- **minute**: указатель на назначение для минуты
- **second**: указатель на назначение для секунды

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — системное время успешно получено.
- **FX_PTR_ERROR** (0x18) — один входной параметр или несколько.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

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

### <a name="see-also"></a>См. также:

- fx_system_date_get
- fx_system_date_set
- fx_system_initialize
- fx_system_time_set

## <a name="fx_system_time_set"></a>fx_system_time_set

Задает текущее системное время

### <a name="prototype"></a>Прототип

```c
UINT fx_system_time_set(UINT hour, UINT minute, UINT second);
```

### <a name="description"></a>Описание

Эта служба задает текущее системное время в соответствии с заданными входными параметрами.

> [!WARNING]
> *Эту службу следует вызывать вскоре после **fx_system_initialize** для задания начального системного времени. По умолчанию системным временем является 0:0:0.*

### <a name="input-parameters"></a>Входные параметры

- **hour**: новый час (0–23)
- **minute**: новая минута (0–59)
- **second**: новая секунда (0–59)

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — системное время успешно получено.
- **FX_INVALID_HOUR** (0x15) — недопустимый новый час.
- **FX_INVALID_MINUTE** (0x16) — недопустимая новая минута.
- **FX_INVALID_SECOND** (0x17) — недопустимая новая секунда.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
 UINT status;

/* Set the current system time to hour 23, minute 21, and second 20. */

status = fx_system_time_set(23, 21, 20);

/* If status is FX_SUCCESS, the current system time has been set. */
```

### <a name="see-also"></a>См. также:

- fx_system_date_get
- fx_system_date_set
- fx_system_initialize
- fx_system_time_get

## <a name="fx_unicode_directory_create"></a>fx_unicode_directory_create

Создает каталог Юникода

### <a name="prototype"></a>Прототип

```c
UINT fx_unicode_directory_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```
### <a name="description"></a>Описание

Эта служба создает подкаталог с именем в Юникоде в текущем каталоге по умолчанию — в параметре имени источника в Юникоде не допускаются сведения о пути. В случае успешного выполнения служба возвращает короткое имя (формат 8.3) только что созданного подкаталога Юникода.

> [!WARNING]
> *Все операции в подкаталоге Юникода (выбор в качестве пути по умолчанию, удаление и т. д.) должны выполняться путем предоставления возвращенного краткого имени (формат 8.3) стандартным службам каталогов FileX.*

> [!IMPORTANT]
> *Эта служба не поддерживается на носителях exFAT.*

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **source_unicode_name**: указатель на имя в Юникоде для нового подкаталога
- **source_unicode_length**: длина имени в Юникоде
- **short_name**: указатель на назначение для краткого имени (формат 8.3) для нового подкаталога Юникода

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — каталог Юникода успешно задан.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_ALREADY_CREATED** (0x0B) — указанный каталог уже существует.
- **FX_NO_MORE_SPACE** (0x0A) — на носителе больше нет доступных кластеров для новой записи каталога.
- **FX_NOT_IMPLEMENTED** (0x22) — служба не реализована для файловой системы exFAT.
- **FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

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

### <a name="see-also"></a>См. также:

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_rename

## <a name="fx_unicode_directory_rename"></a>fx_unicode_directory_rename

Переименовывает каталог, используя строку в Юникоде

### <a name="prototype"></a>Прототип

```c
UINT fx_unicode_directory_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length,
    CHAR *new_short_name);
```
### <a name="description"></a>Описание

Эта служба изменяет подкаталог с именем в Юникоде на указанное новое имя в Юникоде в текущем рабочем каталоге. Параметры имени в Юникоде не должны содержать сведения о пути.

> [!IMPORTANT]
> *Эта служба не поддерживается на носителях exFAT.*

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **old_unicode_name**: указатель на имя в Юникоде для текущего файла
- **old_unicode_name_length**: длина текущего имени в Юникоде
- **new_unicode_name**: указатель на новое имя файла Юникода
- **old_unicode_name_length**: длина старого имени в Юникоде
- **new_short_name**: указатель на назначение для краткого имени (формат 8.3) для переименованного файла в Юникода Переименование каталога с помощью Юникода

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — носитель успешно открыт.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_ALREADY_CREATED** (0x0B) — каталог с указанным именем уже существует.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_PTR_ERROR** (0x18) — один указатель или несколько имеют значение NULL.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.
- **FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

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

### <a name="see-also"></a>См. также:

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create

## <a name="fx_unicode_file_create"></a>fx_unicode_file_create

Создает файл в Юникоде

### <a name="prototype"></a>Прототип

```c
UINT fx_unicode_file_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```

### <a name="description"></a>Описание

Эта служба создает файл с именем в Юникоде в текущем каталоге по умолчанию — в параметре имени источника в Юникоде не допускаются сведения о пути. В случае успешного выполнения служба возвращает краткое имя (формат 8.3) только что созданного файла в Юникоде.

> [!WARNING]
> *Все операции с файлом в Юникоде (открытие, запись, чтение, закрытие и т. д.) должны выполняться путем предоставления возвращенного краткого имени (формат 8.3) стандартным файловым службам FileX.*

### <a name="input-parameters"></a>Входные параметры


- **media_ptr**: указатель на блок управления носителем
- **source_unicode_name**: указатель на имя в Юникоде для нового файла
- **source_unicode_length**: длина имени в Юникоде
- **short_name**: указатель на назначение для краткого имени (формат 8.3) для нового файла в Юникоде

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — файл успешно создан.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_ALREADY_CREATED** (0x0B) — указанный файл уже существует.
- **FX_NO_MORE_SPACE** (0x0A) — на носителе больше нет доступных кластеров для новой записи файла.
- **FX_NOT_IMPLEMENTED** (0x22) — служба не реализована для файловой системы exFAT.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

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

### <a name="see-also"></a>См. также:

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_unicode_file_rename"></a>fx_unicode_file_rename

Переименовывает файл, используя строку в Юникоде

### <a name="prototype"></a>Прототип

```c
UINT fx_unicode_file_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length, 
    CHAR *new_short_name);
```

### <a name="description"></a>Описание

Эта служба изменяет файл с именем в Юникоде на указанное новое имя в Юникоде в текущем каталоге по умолчанию. Параметры имени в Юникоде не должны содержать сведения о пути.

> [!IMPORTANT]
> *Эта служба не поддерживается на носителях exFAT.*

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **old_unicode_name**: указатель на имя в Юникоде для текущего файла
- **old_unicode_name_length**: длина текущего имени в Юникоде
- **new_unicode_name**: указатель на новое имя файла Юникода
- **new_unicode_name_length**: длина нового имени в Юникоде
- **new_short_name**: указатель на назначение для краткого имени (формат 8.3) для переименованного файла в Юникода

### <a name="return-values"></a>Возвращаемые значения


- **FX_SUCCESS** (0x00) — носитель успешно открыт.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_ALREADY_CREATED** (0x0B) — файл с указанным именем уже существует.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_PTR_ERROR** (0x18) — один указатель или несколько имеют значение NULL.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.
- **FX_WRITE_PROTECT** (0x23) — указанный носитель защищен от записи.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

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

### <a name="see-also"></a>См. также:

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_unicode_length_get"></a>fx_unicode_length_get

Возвращает длину имени в формате Юникода

### <a name="prototype"></a>Прототип

```c
ULONG fx_unicode_length_get(UCHAR *unicode_name);
```
### <a name="description"></a>Описание

Эта служба определяет длину заданного имени в формате Юникода. Символ Юникода представлен двумя байт. Имя в формате Юникода — это последовательность двухбайтовых символов Юникода, заканчивающихся двумя байт NULL (два байт со значением 0).

### <a name="input-parameters"></a>Входные параметры

**unicode_name**: указатель на имя в формате Юникода

### <a name="return-values"></a>Возвращаемые значения

**length** — длина имени в формате Юникода (количество символов Юникода в имени).

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

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

### <a name="see-also"></a>См. также:

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_unicode_length_get_extended"></a>fx_unicode_length_get_extended

Возвращает длину имени в формате Юникода

### <a name="prototype"></a>Прототип

```c
UINT fx_unicode_length_get_extended(
    UCHAR *unicode_name,
    UINT buffer_length);
```
### <a name="description"></a>Описание

Эта служба получает длину заданного имени в формате Юникода. Символ Юникода представлен двумя байт. Имя в формате Юникода — это последовательность двухбайтовых символов Юникода, заканчивающихся двумя байт NULL (два байт со значением 0).

> [!IMPORTANT]
> *Эта служба идентична **fx_unicode_length_get()** , за исключением того, что вызывающий объект передает размер буфера **unicode_name**, включая два символа NULL.*

### <a name="input-parameters"></a>Входные параметры

- **unicode_name**: указатель на имя в формате Юникода
- **buffer_length**: размер буфера имени в формате Юникода

### <a name="return-values"></a>Возвращаемые значения

**length** — длина имени в формате Юникода (количество символов Юникода в имени).

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

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

### <a name="see-also"></a>См. также:

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_unicode_name_get"></a>fx_unicode_name_get

Получает имя в Юникоде из краткого имени

### <a name="prototype"></a>Прототип

```c
UINT fx_unicode_name_get(
    FX_MEDIA *media_ptr, 
    CHAR *source_short_name,
    UCHAR *destination_unicode_name, 
    ULONG *destination_unicode_length);
```

### <a name="description"></a>Описание

Эта служба получает имя в Юникоде, связанное с предоставленным кратким именем (формат 8.3) в текущем каталоге по умолчанию — в параметре краткого имени не допускаются сведения о пути. В случае успешного выполнения служба возвращает имя в Юникоде, связанное с кратким именем.

> [!IMPORTANT]
> *Эта служба может использоваться для получения имен в Юникоде для файлов и подкаталогов.*

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **short_name**: указатель на краткое имя (формат 8.3)
- **destination_unicode_name**: указатель на назначение для имени в Юникоде, связанного с заданным кратким именем
- **destination_unicode_length**: указатель на возвращаемую длину имени в Юникоде

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — имя в Юникоде успешно получено.
- **FX_FAT_READ_ERROR** (0x03) — не удается прочитать таблицу FAT.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_NOT_FOUND** (0x04) — краткое имя не найдено, или размер назначения Юникода слишком мал.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

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

### <a name="see-also"></a>См. также:

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_short_name_get

## <a name="fx_unicode_name_get_extended"></a>fx_unicode_name_get_extended

Получает имя в Юникоде из краткого имени

### <a name="prototype"></a>Прототип

```c
UINT fx_unicode_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *source_short_name,
    UCHAR *destination_unicode_name,
    ULONG *destination_unicode_length,
    ULONG unicode_name_buffer_length);
```
### <a name="description"></a>Описание

Эта служба получает имя в Юникоде, связанное с предоставленным кратким именем (формат 8.3) в текущем каталоге по умолчанию — в параметре краткого имени не допускаются сведения о пути. В случае успешного выполнения служба возвращает имя в Юникоде, связанное с кратким именем.

> [!IMPORTANT]
> *Эта служба идентична ***fx_unicode_name_get** _, за исключением того, что в качестве входного аргумента вызывающий объект предоставляет размер конечного буфера в Юникоде. Это позволяет службе гарантировать, что она не перезапишет конечный буфер Юникода_.

> [!IMPORTANT]
> *Эта служба может использоваться для получения имен в Юникоде для файлов и подкаталогов.*

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **short_name**: указатель на краткое имя (формат 8.3)
- **destination_unicode_name**: указатель на назначение для имени в Юникоде, связанного с заданным кратким именем
- **destination_unicode_length**: указатель на возвращаемую длину имени в Юникоде
- **unicode_name_buffer_length**: размер буфера имен в Юникоде Примечание. Требуется NULL в конце, что добавляет дополнительный байт.

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — имя в Юникоде успешно получено.
- **FX_FAT_READ_ERROR** (0x03) — не удается прочитать таблицу FAT.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_NOT_FOUND** (0x04) — краткое имя не найдено, или размер назначения Юникода слишком мал.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

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

### <a name="see-also"></a>См. также:

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_short_name_get

## <a name="fx_unicode_short_name_get"></a>fx_unicode_short_name_get

Получает краткое имя из имени в Юникоде

### <a name="prototype"></a>Прототип

```c
UINT fx_unicode_short_name_get(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length,
    CHAR *destination_short_name);
```

Эта служба получает краткое имя (формат 8.3), связанное с предоставленным именем в Юникоде в текущем каталоге по умолчанию — в параметре имени в Юникоде не допускаются сведения о пути. В случае успешного выполнения служба возвращает краткое имя, связанное с именем в Юникоде.

> [!IMPORTANT]
> *Эта служба может использоваться для получения кратких имен для файлов и подкаталогов.*

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **source_unicode_name**: указатель на имя в формате Юникода
- **source_unicode_length**: длина имени в Юникоде
- **destination_short_name**: указатель на назначение краткого имени (формат 8.3) Размер должен быть не менее 13 байт.

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — краткое имя успешно получено.
- **FX_FAT_READ_ERROR** (0x03) — не удается прочитать таблицу FAT.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_NOT_FOUND** (0x04) — имя в Юникоде не найдено.
- **FX_NOT_IMPLEMENTED** (0x22) — служба не реализована для файловой системы exFAT.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

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

### <a name="see-also"></a>См. также:

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get

## <a name="fx_unicode_short_name_get_extended"></a>fx_unicode_short_name_get_extended

Получает краткое имя из имени в Юникоде

### <a name="prototype"></a>Прототип

```c
UINT fx_unicode_short_name_get_extended(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *destination_short_name,
    ULONG short_name_buffer_length);
```

### <a name="description"></a>Описание

Эта служба получает краткое имя (формат 8.3), связанное с предоставленным именем в Юникоде в текущем каталоге по умолчанию — в параметре имени в Юникоде не допускаются сведения о пути. В случае успешного выполнения служба возвращает краткое имя, связанное с именем в Юникоде.

> [!IMPORTANT]
> *Эта служба идентична **fx_unicode_short_name_get()** , за исключением того, что в качестве входного аргумента вызывающий объект предоставляет размер конечного буфера. Это позволяет службе гарантировать, что краткое имя не превысит конечный буфер*.

*Эта служба может использоваться для получения кратких имен для файлов и подкаталогов.*

### <a name="input-parameters"></a>Входные параметры

- **media_ptr**: указатель на блок управления носителем
- **source_unicode_name**: указатель на имя в формате Юникода
- **source_unicode_length**: длина имени в Юникоде
- **destination_short_name**: указатель на назначение краткого имени (формат 8.3) Размер должен быть не менее 13 байт.
- **short_name_buffer_length**: размер буфера назначения Размер буфера должен быть не менее 14 байт.

### <a name="return-values"></a>Возвращаемые значения

- **FX_SUCCESS** (0x00) — краткое имя успешно получено.
- **FX_FAT_READ_ERROR** (0x03) — не удается прочитать таблицу FAT.
- **FX_FILE_CORRUPT** (0x08) — файл поврежден.
- **FX_IO_ERROR** (0x90) — ошибка ввода-вывода драйвера.
- **FX_MEDIA_NOT_OPEN** (0x11) — указанный носитель не открыт.
- **FX_NOT_FOUND** (0x04) — имя в Юникоде не найдено.
- **FX_NOT_IMPLEMENTED** (0x22) — служба не реализована для файловой системы exFAT.
- **FX_SECTOR_INVALID** (0x89) — недопустимый сектор.
- **FX_PTR_ERROR** (0x18) — недопустимый указатель носителя или имени.
- **FX_CALLER_ERROR** (0x20) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

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

### <a name="see-also"></a>См. также:

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get
