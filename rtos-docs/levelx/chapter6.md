---
title: Глава 6. API-интерфейсы NOR для LevelX для ОСРВ Azure
description: API-интерфейсы NOR для LevelX для ОСРВ Azure, доступные для приложения.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2e109f5916a9e903aa3341f2855ade085e9d9a22b80ec7cb2e0c310e43ff3eac
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790247"
---
# <a name="chapter-6---azure-rtos-levelx-nor-apis"></a>Глава 6. API-интерфейсы NOR для LevelX для ОСРВ Azure

Приложениям доступны следующие функции API NOR для LevelX для ОСРВ Azure:

- ***lx_nor_flash_close** _: _закрытие экземпляра флэш-памяти NOR*;
- ***lx_nor_flash_defragment** _: _дефрагментация экземпляра флэш-памяти NOR*;
- ***lx_nor_flash_extended_cache_enable** _: _включение и выключение расширенного кэша NOR*;
- ***lx_nor_flash_initialize** _: _инициализация поддержки флэш-памяти NOR*;
- ***lx_nor_flash_open** _: _открытие экземпляра флэш-памяти NOR*;
- ***lx_nor_flash_partial_defragment** _: _частичная дефрагментация экземпляра флэш-памяти NOR*;
- ***lx_nor_flash_sector_read** _: _чтение сектора флэш-памяти NOR*;
- ***lx_nor_flash_sector_release** _: _освобождение сектора флэш-памяти NOR*;
- ***lx_nor_flash_sector_write** _: _запись сектора флэш-памяти NOR*.

## <a name="lx_nor_flash_close"></a>lx_nor_flash_close

Закрытие экземпляра флэш-памяти NOR.

### <a name="prototype"></a>Прототип

```c
UINT lx_nor_flash_close(LX_NOR_FLASH *nor_flash);
```

### <a name="description"></a>Описание

Эта служба закрывает ранее открытый экземпляр флэш-памяти NOR.

### <a name="input-parameters"></a>Входные параметры

- *nor_flash*: указатель на экземпляр флэш-памяти NOR.

### <a name="return-values"></a>Возвращаемые значения

- **LX_SUCCESS** (0x00): запрос успешно выполнен.
- **LX_ERROR** (0x01): ошибка закрытия экземпляра флэш-памяти.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
/* Close NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_close(&my_nor_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>См. также:

- lx_nor_flash_defragment;
- lx_nor_flash_extended_cache_enable;
- lx_nor_flash_initialize;
- lx_nor_flash_open;
- lx_nor_flash_partial_defragment;
- lx_nor_flash_sector_read;
- lx_nor_flash_sector_release;
- lx_nor_flash_sector_write.

## <a name="lx_nor_flash_defragment"></a>lx_nor_flash_defragment

Дефрагментация экземпляра флэш-памяти NOR.

### <a name="prototype"></a>Прототип

```c
UINT lx_nor_flash_defragment(LX_NOR_FLASH *nor_flash);
```

### <a name="description"></a>Описание

Эта служба дефрагментирует ранее открытый экземпляр флэш-памяти NOR. Процесс дефрагментации позволяет максимально увеличить количество свободных секторов и блоков.

### <a name="input-parameters"></a>Входные параметры

- *nor_flash*: указатель на экземпляр флэш-памяти NOR.

### <a name="return-values"></a>Возвращаемые значения

- **LX_SUCCESS** (0x00): запрос успешно выполнен.
- **LX_ERROR** (0x01): ошибка дефрагментации экземпляра флэш-памяти.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
/* Defragment NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_defragment(&my_nor_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>См. также:

- lx_nor_flash_close;
- lx_nor_flash_extended_cache_enable;
- lx_nor_flash_initialize;
- lx_nor_flash_open;
- lx_nor_flash_partial_defragment;
- lx_nor_flash_sector_read;
- lx_nor_flash_sector_release;
- lx_nor_flash_sector_write.

## <a name="lx_nor_flash_extended_cache_enable"></a>lx_nor_flash_extended_cache_enable

Включение и выключение расширенного кэша NOR.

### <a name="prototype"></a>Прототип

```c
UINT lx_nor_flash_extended_cache_enable(
    LX_NOR_FLASH *nor_flash,  
    VOID *memory, 
    ULONG size);
```

### <a name="description"></a>Описание

Эта служба реализует в ОЗУ уровень кэша секторов NOR, используя предоставленную приложением память. Каждые 512 байт предоставленной памяти преобразуются в пространство кэша для одного сектора NOR. Кэшируются секторы, которые содержат сведения об управлении блоками: число удалений, карта свободных секторов, сведения о сопоставлении секторов. Секторы данных в этом кэше не хранятся.

### <a name="input-parameters"></a>Входные параметры

- **nor_flash**: указатель на экземпляр флэш-памяти NOR.  
- **memory**: начальный адрес памяти для кэша с округлением для адресации в формате ULONG. Значение LX_NULL позволяет отключить кэш.  
- **size**: размер предоставленной памяти в байтах (должен быть кратным 512 байтам).

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00): запрос успешно выполнен.
- **LX_ERROR** (0x01): недостаточно памяти для одного сектора NOR
- **LX_DISABLED** (0x09): расширенный кэш NOR отключен параметром конфигурации

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
/* Enable the NOR flash cache for the instance "my_nor_flash". */  
status = lx_nor_flash_extended_cache_enable(&my_nor_flash,  
    &my_memory, sizeof(my_memory));  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>См. также:

- lx_nor_flash_close;
- lx_nor_flash_defragment;
- lx_nor_flash_initialize;
- lx_nor_flash_open;
- lx_nor_flash_partial_defragment;
- lx_nor_flash_sector_read;
- lx_nor_flash_sector_release;
- lx_nor_flash_sector_write.

## <a name="lx_nor_flash_initialize"></a>lx_nor_flash_initialize

Инициализация поддержки флэш-памяти NOR.

### <a name="prototype"></a>Прототип

```c
UINT lx_nor_flash_initialize(void);
```

### <a name="description"></a>Описание

Эта служба инициализирует поддержку флэш-памяти NOR. Ее необходимо вызывать раньше любых других API-интерфейсов NOR для LevelX.

### <a name="input-parameters"></a>Входные параметры

- **Нет**

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00): запрос успешно выполнен.
- **LX_ERROR** (0x01): ошибка инициализации поддержки флэш-памяти NOR.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Пример

```c
/* Initialize NOR flash support. */  
status = lx_nor_flash_initialize();  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>См. также:

- lx_nor_flash_close;
- lx_nor_flash_defragment;
- lx_nor_flash_extended_cache_enable;
- lx_nor_flash_partial_defragment;
- lx_nor_flash_open;
- lx_nor_flash_sector_read;
- lx_nor_flash_sector_release;
- lx_nor_flash_sector_write.

## <a name="lx_nor_flash_open"></a>lx_nor_flash_open

Открытие экземпляра флэш-памяти NOR.

### <a name="prototype"></a>Прототип

```c
UINT lx_nor_flash_open(
    LX_NOR_FLASH *nor_flash, 
    CHAR *name,  
    UINT (*nor_driver_initialize) (LX_NOR_FLASH *));
```

### <a name="description"></a>Описание

Эта служба открывает экземпляр флэш-памяти NOR с использованием предоставленного блока управления флэш-памятью NOR и функции инициализации драйвера. Обратите внимание, что функция инициализации драйвера отвечает за установку указателей на функции чтения, записи и стирания блоков в оборудовании NOR, сопоставленным с этим экземпляром флэш-памяти NOR.

### <a name="input-parameters"></a>Входные параметры

- *nor_flash*: указатель на экземпляр флэш-памяти NOR.
- *name*: имя экземпляра флэш-памяти NOR.
- *nor_driver_initialize*: указатель на функцию для инициализации драйвера флэш-памяти NOR. Дополнительные сведения о функциях, которые должен реализовать драйвер флэш-памяти NOR, см. в главе 5 этого руководства.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00): запрос успешно выполнен.
- **LX_ERROR** (0x01): ошибка открытия экземпляра флэш-памяти NOR.
- **LX_NO_MEMORY** (0x08): драйвер не предоставил буфера для считывания сектора NOR в ОЗУ.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
/* Open NOR flash instance "my_nor_flash" with the driver "my_nor_driver_initialize". */  
status = lx_nor_flash_open(&my_nor_flash,"my NOR flash",  
    my_nor_driver_initialize);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>См. также:

- lx_nor_flash_close;
- lx_nor_flash_defragment;
- lx_nor_flash_extended_cache_enable;
- lx_nor_flash_initialize;
- lx_nor_flash_partial_defragment;
- lx_nor_flash_sector_read;
- lx_nor_flash_sector_release;
- lx_nor_flash_sector_write.

## <a name="lx_nor_flash_partial_defragment"></a>lx_nor_flash_partial_defragment

Частичная дефрагментация экземпляра флэш-памяти NOR.

### <a name="prototype"></a>Прототип

```c
UINT lx_nor_flash_partial_defragment(
    LX_NOR_FLASH *nor_flash, 
    UINT max_blocks);
```

### <a name="description"></a>Описание

Эта служба выполняет дефрагментацию ранее открытого экземпляра флэш-памяти NOR вплоть до максимального указанного числа блоков. Процесс дефрагментации позволяет максимально увеличить количество свободных секторов и блоков.

### <a name="input-parameters"></a>Входные параметры

- *nor_flash*: указатель на экземпляр флэш-памяти NOR.
- *max_blocks*: максимальное количество блоков.

### <a name="return-values"></a>Возвращаемые значения

- **LX_SUCCESS** (0x00): запрос успешно выполнен.
- **LX_ERROR** (0x01): ошибка дефрагментации экземпляра флэш-памяти.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
/* Defragment of one block in NOR flash instance* *"my_nor_flash". */  
status = lx_nor_flash_partial_defragment(&my_nor_flash, 1);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>См. также:

- lx_nor_flash_close;
- lx_nor_flash_defragment;
- lx_nor_flash_extended_cache_enable;
- lx_nor_flash_initialize;
- lx_nor_flash_open;
- lx_nor_flash_sector_read;
- lx_nor_flash_sector_release;
- lx_nor_flash_sector_write.

## <a name="lx_nor_flash_sector_read"></a>lx_nor_flash_sector_read

Чтение сектора флэш-памяти NOR.

### <a name="prototype"></a>Прототип

```c
UINT lx_nor_flash_sector_read(
    LX_NOR_FLASH *nor_flash,  
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>Описание

Эта служба считывает логический сектор из экземпляра флэш-памяти NOR, а при успешном выполнении возвращает содержимое в предоставленном буфере. Обратите внимание, что размер сектора NOR не всегда составляет 512 байт.

### <a name="input-parameters"></a>Входные параметры

- *nor_flash*: указатель на экземпляр флэш-памяти NOR.
- *logical_sector*: логический сектор для считывания.
- *buffer*: указатель на место назначения для содержимого логического сектора. Обратите внимание, что ожидается буфер размером 512 байт с округлением для адресации в формате ULONG.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00): запрос успешно выполнен.
- **LX_ERROR** (0x01): ошибка чтения сектора флэш-памяти NOR.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
/* Read logical sector 20 of the NOR flash instance "my_nor_flash" and place contents in "buffer". */ 
status = lx_nor_flash_sector_read(&my_nor_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, "buffer" contains the contents of logical sector 20. */
```

### <a name="see-also"></a>См. также:

- lx_nor_flash_close;
- lx_nor_flash_defragment;
- lx_nor_flash_extended_cache_enable;
- lx_nor_flash_initialize;
- lx_nor_flash_open;
- lx_nor_flash_partial_defragment;
- lx_nor_flash_sector_release;
- lx_nor_flash_sector_write.

## <a name="lx_nor_flash_sector_release"></a>lx_nor_flash_sector_release

Освобождение сектора флэш-памяти NOR.

### <a name="prototype"></a>Прототип

```c
UINT lx_nor_flash_sector_release(
    LX_NOR_FLASH *nor_flash,
    ULONG logical_sector);
```

### <a name="description"></a>Описание

Эта служба освобождает сопоставление для логического сектора в экземпляре флэш-памяти NOR. Освобождение логического сектора, который не используется, повышает эффективность выравнивания износа в LevelX.

### <a name="input-parameters"></a>Входные параметры

- *nor_flash*: указатель на экземпляр флэш-памяти NOR.
- *logical_sector*: логический сектор для освобождения.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00): запрос успешно выполнен.
- **LX_ERROR** (0x01): ошибка записи в сектор флэш-памяти NOR.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
/* Release logical sector 20 of the NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_sector_release(&my_nor_flash, 20);  
  
/* If status is LX_SUCCESS, logical sector 20 has been released. */
```

### <a name="see-also"></a>См. также:

- lx_nor_flash_close;
- lx_nor_flash_defragment;
- lx_nor_flash_extended_cache_enable;
- lx_nor_flash_initialize;
- lx_nor_flash_open;
- lx_nor_flash_partial_defragment;
- lx_nor_flash_sector_read;
- lx_nor_flash_sector_write.

## <a name="lx_nor_flash_sector_write"></a>lx_nor_flash_sector_write

Запись в сектор флэш-памяти NOR.

### <a name="prototype"></a>Прототип

```c
UINT lx_nor_flash_sector_write(
    LX_nor_FLASH *NOR_flash,
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>Описание

Эта служба записывает указанный логический сектор в экземпляр флэш-памяти NOR.

### <a name="input-parameters"></a>Входные параметры

- *nor_flash*: указатель на экземпляр флэш-памяти NOR.
- *logical_sector*: логический сектор для записи.
- *buffer*: указатель на содержимое логического сектора. Обратите внимание, что ожидается буфер размером 512 байтов с округлением для адресации в формате ULONG.

### <a name="return-values"></a>Возвращаемые значения

- **LX_SUCCESS** (0x00): запрос успешно выполнен.
- **LX_NO_SECTORS** (0x02): больше нет свободных секторов для выполнения записи
- **LX_ERROR** (0x01): ошибка освобождения сектора флэш-памяти NOR.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
/* Write logical sector 20 of the NOR flash instance "my_nor_flash" with the contents pointed to by "buffer". */ 
status = lx_nor_flash_sector_write(&my_nor_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, logical sector 20 has been written with the contents of "buffer". */
```

### <a name="see-also"></a>См. также:

- lx_nor_flash_close;
- lx_nor_flash_defragment;
- lx_nor_flash_extended_cache_enable;
- lx_nor_flash_initialize;
- lx_nor_flash_open;
- lx_nor_flash_partial_defragment;
- lx_nor_flash_sector_read;
- lx_nor_flash_sector_release.
