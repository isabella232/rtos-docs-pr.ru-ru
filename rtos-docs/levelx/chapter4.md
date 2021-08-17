---
title: Глава 4. API-интерфейсы NAND для LevelX в ОСРВ Azure
description: API-интерфейсы NAND для LevelX в ОСРВ Azure, доступные для приложения.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d92b6c10921b4d04345610e139101e93c7a439ff695a89a79245894ad9ef1fec
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790290"
---
# <a name="chapter-4---azure-rtos-levelx-nand-apis"></a>Глава 4. API-интерфейсы NAND для LevelX в ОСРВ Azure

Приложению доступны следующие API-интерфейсы NAND для LevelX в ОСРВ Azure:

- ***lx_nand_flash_close** _: _закрытие экземпляра флэш-памяти NAND*;
- ***lx_nand_flash_defragment** _: _дефрагментация экземпляра флэш-памяти NAND*;
- ***lx_nand_flash_extended_cache_enable** _: _включение и отключение расширенного кэша NAND*;
- ***lx_nand_flash_initialize** _: _инициализация поддержки флэш-памяти NAND*;
- ***lx_nand_flash_open** _: _открытие экземпляра флэш-памяти NAND*;
- ***lx_nand_flash_page_ecc_check** _: _проверка страницы на наличие ошибок ECC с коррекцией*;
- ***lx_nand_flash_page_ecc_compute** _: _вычисление ECC для страницы*;
- ***lx_nand_flash_partial_defragment** _: _частичная дефрагментация экземпляра флэш-памяти NAND*;
- ***lx_nand_flash_sector_read** _: _чтение сектора флэш-памяти NAND*;
- ***lx_nand_flash_sector_release** _: _освобождение сектора флэш-памяти NAND*;
- ***lx_nand_flash_sector_write** _: _запись сектора флэш-памяти NAND*.

## <a name="lx_nand_flash_close"></a>lx_nand_flash_close

Закрытие экземпляра флэш-памяти NAND.

### <a name="prototype"></a>Прототип

```c
UINT lx_nand_flash_close(LX_NAND_FLASH *nand_flash);
```

### <a name="description"></a>Описание

Эта служба закрывает ранее открытый экземпляр флэш-памяти NAND.

### <a name="input-parameters"></a>Входные параметры

- **nand_flash**: указатель на экземпляр флэш-памяти NAND.

### <a name="return-values"></a>Возвращаемые значения

- **LX_SUCCESS** (0x00): запрос успешно выполнен.
- **LX_ERROR** (0x01): ошибка закрытия экземпляра флэш-памяти.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
/* Close NAND flash instance "my_nand_flash". */
status = lx_nand_flash_close(&my_nand_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>См. также:

- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_defragment"></a>lx_nand_flash_defragment

Дефрагментация экземпляра флэш-памяти NAND.

### <a name="prototype"></a>Прототип

```c
UINT lx_nand_flash_defragment(LX_NAND_FLASH *nand_flash);
```

### <a name="description"></a>Описание

Эта служба дефрагментирует ранее открытый экземпляр флэш-памяти NAND. Процесс дефрагментации позволяет максимально увеличить количество свободных страниц и блоков.

### <a name="input-parameters"></a>Входные параметры

- **nand_flash**: указатель на экземпляр флэш-памяти NAND.

### <a name="return-values"></a>Возвращаемые значения

- **LX_SUCCESS** (0x00): запрос успешно выполнен.
- **LX_ERROR** (0x01): ошибка дефрагментации экземпляра флэш-памяти.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
/* Defragment NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_defragment(&my_nand_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>См. также:

- lx_nand_flash_close
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_extended_cache_enable"></a>lx_nand_flash_extended_cache_enable

Включение и выключение расширенного кэша NAND.

### <a name="prototype"></a>Прототип

```c
UINT lx_nand_flash_extended_cache_enable(
    LX_NAND_FLASH
    *nand_flash,  
    VOID *memory, 
    ULONG size);
```

### <a name="description"></a>Описание

Эта служба реализует в ОЗУ уровень кэша, используя предоставленную приложением память. Общий объем памяти, необходимый для операции полного кэширования, можно вычислить следующим образом:

```c
size (in_bytes) = number_of_blocks (rounded up to be divisible by 4) +  
    ((number_of_blocks * pages_per_block) * 4)  +  
    ((number_of_blocks * (pages_per_block + 1)) * 4)
```

Если предоставленная память недостаточно велика для размещения полного кэша NAND, эта подпрограмма включит как можно большую часть кэша флэш-памяти NAND, основываясь на предоставленной памяти.

Кэш NAND отключается, если указанный адрес памяти имеет значение NULL. Таким образом, возможно временное использование кэша NAND.

### <a name="input-parameters"></a>Входные параметры

- **nand_flash**: указатель на экземпляр флэш-памяти NAND.  
- **memory**: начальный адрес памяти для кэша с выравниванием для адресации в формате ULONG. Значение LX_NULL позволяет отключить кэш.  
- **size**: размер предоставленной памяти в байтах.

### <a name="return-values"></a>Возвращаемые значения

- **LX_SUCCESS** (0x00): запрос успешно выполнен.
- **LX_ERROR** (0x01): недостаточно памяти для одного элемента кэша NAND.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
/* Enable the NAND flash cache for the instance "my_nand_flash". */
status = lx_nand_flash_extended_cache_enable(&my_nand_flash,  
    &my_memory, sizeof(my_memory));  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>См. также:

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_initialize"></a>lx_nand_flash_initialize

Инициализация поддержки флэш-памяти NAND.

### <a name="prototype"></a>Прототип

```c
UINT lx_nand_flash_initialize(void);
```

### <a name="description"></a>Описание

Эта служба инициализирует поддержку флэш-памяти NAND. Ее необходимо вызывать раньше любых других API-интерфейсов NAND для LevelX.

### <a name="input-parameters"></a>Входные параметры

- **Нет**

### <a name="return-values"></a>Возвращаемые значения

- **LX_SUCCESS** (0x00): запрос успешно выполнен.
- **LX_ERROR** (0x01): ошибка инициализации поддержки флэш-памяти NAND.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Пример

```c
/* Initialize NAND flash support. */
status = lx_nand_flash_initialize();  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>См. также:

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_open"></a>lx_nand_flash_open

Открытие экземпляра флэш-памяти NAND.

### <a name="prototype"></a>Прототип

```c
UINT lx_nand_flash_open(
    LX_NAND_FLASH *nand_flash, 
    CHAR *name,  
    UINT (*nand_driver_initialize) (LX_NAND_FLASH *));
```

### <a name="description"></a>Описание

Эта служба открывает экземпляр флэш-памяти NAND с использованием предоставленного блока управления флэш-памятью NAND и функции инициализации драйвера. Обратите внимание, что функция инициализации драйвера отвечает за установку указателей на функции чтения, записи и стирания блоков или страниц в оборудовании NAND, сопоставленным с этим экземпляром флэш-памяти NAND.

### <a name="input-parameters"></a>Входные параметры

- **nand_flash**: указатель на экземпляр флэш-памяти NAND.
- **name**: имя экземпляра флэш-памяти NAND.
- **nand_driver_initialize**: указатель на функцию для инициализации драйвера флэш-памяти NAND. Дополнительные сведения о функциях, которые должен реализовать драйвер флэш-памяти NAND, см. в главе 3 этого руководства.

### <a name="return-values"></a>Возвращаемые значения

- **LX_SUCCESS** (0x00): запрос успешно выполнен.
- **LX_ERROR** (0x01): ошибка открытия экземпляра флэш-памяти NAND.
- **LX_NO_MEMORY** (0x08): драйвер не предоставил буфер для считывания одной страницы в ОЗУ.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
/* Open NAND flash instance "my_nand_flash" with the driver "my_nand_driver_initialize". */ 
status = lx_nand_flash_open(&my_nand_flash,"my nand flash",  
    my_nand_driver_initialize);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>См. также:

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_page_ecc_check"></a>lx_nand_flash_page_ecc_check

Проверка страницы на наличие ошибок ECC с коррекцией

### <a name="prototype"></a>Прототип

```c
UINT lx_nand_flash_page_ecc_check(
    LX_NAND_FLASH *nand_flash,  
    UCHAR *page_buffer, 
    UCHAR *ecc_buffer);
```

### <a name="description"></a>Описание

Эта служба проверяет целостность предоставленного буфера страниц NAND с помощью заданного кода ECC. Предполагается, что размер страницы (определенный в указателе экземпляра флэш-памяти NAND) является кратным 256 байтам, а указанный код ECC способен исправить ошибку в 1 бит в каждой из 256-байтовой части страницы.

### <a name="input-parameters"></a>Входные параметры

- **nand_flash**: указатель на экземпляр флэш-памяти NAND.
- **page_buffer**: указатель на буфер флэш-памяти NAND.
- **ecc_buffer**: указатель на ECC для страницы флэш-памяти NAND. Обратите внимание, что для каждой 256-байтовой части страницы имеется 3 байта ECC.

### <a name="return-values"></a>Возвращаемые значения

- **LX_SUCCESS** (0x00): страница NAND не содержит ошибки.
- **LX_NAND_ERROR_CORRECTED** (0x06): одна или несколько 1-байтовых ошибок были исправлены на странице NAND — исправления находятся в буфере страниц.
- **LX_NAND_ERROR_NOT_CORRECTED** (0x07): слишком много ошибок для исправления на странице NAND.

### <a name="allowed-from"></a>Допустимые источники

Драйвер LevelX

### <a name="example"></a>Пример

```c
/* Check the NAND page pointed to by "page_pointer" of the NAND flash instance "my_nand_flash" . */
status = lx_nand_flash_page_ecc_check(&my_nand_flash, page_pointer, ecc_pointer);  
  
/* If status is LX_SUCCESS the page is valid. */
```

### <a name="see-also"></a>См. также:

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_page_ecc_compute"></a>lx_nand_flash_page_ecc_compute

Вычисление ECC для страницы.

### <a name="prototype"></a>Прототип

```c
UINT lx_nand_flash_page_ecc_compute(
    LX_NAND_FLASH *nand_flash,  
    UCHAR *page_buffer, 
    UCHAR *ecc_buffer);
```

### <a name="description"></a>Описание

Эта служба вычисляет код ECC для заданного буфера страниц NAND и возвращает код ECC в заданном буфере ECC. Предполагается, что размер страницы кратен 256 байтам (что определено в указателе экземпляра флэш-памяти NAND). Код ECC используется для проверки целостности страницы при ее последующем считывании.

### <a name="input-parameters"></a>Входные параметры

- **nand_flash**: указатель на экземпляр флэш-памяти NAND.
- **page_buffer**: указатель на буфер флэш-памяти NAND.
- **ecc_buffer**: указатель на назначение для ECC страницы флэш-памяти NAND. Обратите внимание, что на 256-байтовую часть страницы должно быть сохранено 3 байта ECC. Например, 2048-байтовая страница потребовала бы 24 байта для ECC.

### <a name="return-values"></a>Возвращаемые значения

- **LX_SUCCESS** (0x00): код ECC успешно вычислен.
- **LX_ERROR** (0x01): ошибка при вычислении ECC.

### <a name="allowed-from"></a>Допустимые источники

Драйвер LevelX

### <a name="example"></a>Пример

```c
/* Compute ECC for the NAND page pointed to by "page_pointer" of the NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_page_ecc_compute(&my_nand_flash, page_pointer, ecc_pointer);  
  
/* If status is LX_SUCCESS the ECC was calculated and Can be found in the memory pointed to by "ecc_pointer." */
```

### <a name="see-also"></a>См. также:

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_partial_defragment"></a>lx_nand_flash_partial_defragment

Частичная дефрагментация экземпляра флэш-памяти NAND.

### <a name="prototype"></a>Прототип

```c
UINT lx_nand_flash_partial_defragment(
    LX_NAND_FLASH *nand_flash,  
    UINT max_blocks);
```

### <a name="description"></a>Описание

Эта служба выполняет дефрагментацию ранее открытого экземпляра флэш-памяти NAND вплоть до максимального указанного числа блоков. Процесс дефрагментации позволяет максимально увеличить количество свободных страниц и блоков.

### <a name="input-parameters"></a>Входные параметры

- **nand_flash**: указатель на экземпляр флэш-памяти NAND.
- **max_blocks**: максимальное количество блоков.

### <a name="return-values"></a>Возвращаемые значения

- **LX_SUCCESS** (0x00): запрос успешно выполнен.
- **LX_ERROR** (0x01): ошибка дефрагментации экземпляра флэш-памяти.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
/* Defragment 1 block of NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_partial_defragment(&my_nand_flash, 1);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>См. также:

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_sector_read"></a>lx_nand_flash_sector_read

Чтение сектора флэш-памяти NAND.

### <a name="prototype"></a>Прототип

```c
UINT lx_nand_flash_sector_read(
    LX_NAND_FLASH *nand_flash,  
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>Описание

Эта служба считывает логический сектор из экземпляра флэш-памяти NAND, а при успешном выполнении возвращает содержимое в предоставленном буфере. Обратите внимание, что размер сектора NAND всегда равен размеру страницы базового оборудования NAND.

### <a name="input-parameters"></a>Входные параметры

- **nand_flash**: указатель на экземпляр флэш-памяти NAND.
- **logical_sector**: логический сектор для считывания.
- **buffer**: указатель на место назначения для содержимого логического сектора. Обратите внимание, что ожидается буфер размером, равным размеру страницы флэш-памяти NAND, и с выравниванием для адресации в формате ULONG.

### <a name="return-values"></a>Возвращаемые значения

- **LX_SUCCESS** (0x00): запрос успешно выполнен.
- **LX_ERROR** (0x01): ошибка чтения сектора флэш-памяти NAND.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
/* Read logical sector 20 of the NAND flash instance "my_nand_flash" and place contents in "buffer". */
status = lx_nand_flash_sector_read(&my_nand_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, "buffer" contains the contentsnof logical sector 20. */
```

### <a name="see-also"></a>См. также:

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_sector_release"></a>lx_nand_flash_sector_release

Освобождение сектора флэш-памяти NAND.

### <a name="prototype"></a>Прототип

```c
UINT lx_nand_flash_sector_release(
    LX_NAND_FLASH *nand_flash,
    ULONG logical_sector);
```

### <a name="description"></a>Описание

Эта служба освобождает сопоставление для логического сектора в экземпляре флэш-памяти NAND. Освобождение логического сектора, который не используется, повышает эффективность выравнивания износа в LevelX.

### <a name="input-parameters"></a>Входные параметры

- **nand_flash**: указатель на экземпляр флэш-памяти NAND.
- **logical_sector**: логический сектор для освобождения.

### <a name="return-values"></a>Возвращаемые значения

- **LX_SUCCESS** (0x00): запрос успешно выполнен.
- **LX_ERROR** (0x01): ошибка записи в сектор флэш-памяти NAND.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
/* Release logical sector 20 of the NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_sector_release(&my_nand_flash, 20);  
  
/* If status is LX_SUCCESS, logical sector 20 has been released. */
```

### <a name="see-also"></a>См. также:

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_sector_write"></a>lx_nand_flash_sector_write

Запись сектора флэш-памяти NAND.

### <a name="prototype"></a>Прототип

```c
UINT lx_nand_flash_sector_write(
    LX_NAND_FLASH *nand_flash,
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>Описание

Эта служба записывает указанный логический сектор в экземпляр флэш-памяти NAND.

### <a name="input-parameters"></a>Входные параметры

- **nand_flash**: указатель на экземпляр флэш-памяти NAND.
- **logical_sector**: логический сектор для записи.
- **buffer**: указатель на содержимое логического сектора. Обратите внимание, что ожидается буфер размером, равным размеру страницы флэш-памяти NAND, и с выравниванием для адресации в формате ULONG.

### <a name="return-values"></a>Возвращаемые значения

- **LX_SUCCESS** (0x00): запрос успешно выполнен.
- **LX_NO_SECTORS** (0x02): больше нет свободных секторов для выполнения записи.
- **LX_ERROR** (0x01): ошибка освобождения сектора флэш-памяти NAND.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
/* Write logical sector 20 of the NAND flash instance "my_nand_flash" with the contents pointed to by "buffer". */  
status = lx_nand_flash_sector_write(&my_nand_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, logical sector 20 has been written with the contents of "buffer". */
```

### <a name="see-also"></a>См. также:

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
