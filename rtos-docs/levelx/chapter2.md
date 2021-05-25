---
title: Глава 2. Установка и использование LevelX для ОСРВ Azure
description: Установка и использование LevelX очень просты. Все необходимые процессы описываются в следующих разделах этой главы.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 34110e74e8ad0a6acd376c00c1284a3ea715c5f5
ms.sourcegitcommit: 4ebe7c51ba850951c6a9d0f15e22d07bb752bc28
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/20/2021
ms.locfileid: "110223321"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-levelx"></a>Глава 2. Установка и использование LevelX для ОСРВ Azure

Установка и использование LevelX для ОСРВ Azure очень проста. Все необходимые процессы описываются в следующих разделах этой главы.

## <a name="distribution"></a>Distribution

LevelX распространяется в формате ANSI на C, где каждая функция содержится в отдельном файле C. Ниже перечислены файлы, входящие в дистрибутив LevelX.
- lx_api.h
- lx_nand_flash_256byte_ecc_check.c
- lx_nand_flash_256byte_ecc_compute.c
- lx_nand_flash_block_full_update.c
- lx_nand_flash_block_reclaim.c
- lx_nand_flash_close.c
- lx_nand_flash_defragment.c  
- lx_nand_flash_extended_cache_enable.c
- lx_nand_flash_initialize.c
- lx_nand_flash_logical_sector_find.c
- lx_nand_flash_next_block_to_erase_find.c
- lx_nand_flash_open.c
- lx_nand_flash_page_ecc_check.c
- lx_nand_flash_page_ecc_compute.c  
- lx_nand_flash_partial_defragment.c
- lx_nand_flash_physical_page_allocate.c
- lx_nand_flash_sector_mapping_cache_invalidate.c
- lx_nand_flash_sector_read.c
- lx_nand_flash_sector_release.c
- lx_nand_flash_sector_write.c
- lx_nand_flash_system_error.c
- lx_nor_flash_block_reclaim.c
- lx_nor_flash_close.c
- lx_nor_flash_defragment.c  
- lx_nor_flash_extended_cache_enable.c
- lx_nor_flash_initialize.c
- lx_nor_flash_logical_sector_find.c
- lx_nor_flash_next_block_to_erase_find.c
- lx_nor_flash_open.c
- lx_nor_flash_partial_defragment.c
- lx_nor_flash_physical_sector_allocate.c
- lx_nor_flash_sector_mapping_cache_invalidate.c
- lx_nor_flash_sector_read.c
- lx_nor_flash_sector_release.c
- lx_nor_flash_sector_write.c
- lx_nor_flash_system_error.c

Существуют также симуляторы и примеры драйверов FileX для работы экземпляров LevelX с флэш-памятью NAND и NOR, которые перечислены ниже.

- demo_filex_nand_flash.c  
- fx_nand_flash_simulated_driver.c
- lx_nand_flash_simulator.c
- demo_filex_nor_flash.c  
- fx_nor_flash_simulated_driver.c
- lx_nor_flash_simulator.c

Конечно, если вам нужна только флэш-память NAND, достаточно использовать файлы LevelX для NAND (***lx_nand_\*.c***). Аналогично, если нужна только флэш-память NOR, достаточно использовать файлы LevelX для NOR (**_lx_nor_\_.c***).

## <a name="configuration-options"></a>Параметры конфигурации

Для LevelX во время компиляции можно настроить перечисленные ниже условные определения. Чтобы использовать любой из этих параметров, просто добавьте требуемое определение в процесс компиляции исходного кода LevelX.

- **LX_DIRECT_READ**: если определен этот параметр, процедура чтения в драйвере флэш-памяти NOR обходится в пользу прямого чтения из памяти NOR, что дает значительное повышение производительности.
- **LX_FREE_SECTOR_DATA_VERIFY**: если определен этот параметр, экземпляр LevelX NOR использует "открытую логику" для проверки того, что все пустые секторы NOR состоят только из единиц.
- **LX_NAND_SECTOR_MAPPING_CACHE_SIZE**: определяет размер кэша для сопоставлений логических секторов. По умолчанию имеет значение 16. Более высокие значения повышают производительность, но увеличивают нагрузку на память. Этот размер не может быть меньше 8 и всегда должен быть степенью числа 2.
- **LX_NAND_FLASH_DIRECT_MAPPING_CACHE**: если определен этот параметр, создается прямой кэш сопоставлений, например, для устранения промахов кэша. Для этого требуется, чтобы LX_NAND_SECTOR_MAPPING_CACHE_SIZE был точно равен количеству страниц в устройстве флэш-памяти.
- **LX_NOR_DISABLE_EXTENDED_CACHE**: если определен этот параметр, отключается расширенный кэш NOR.
- **LX_NOR_EXTENDED_CACHE_SIZE**: по умолчанию имеет значение 8, что означает возможность кэшировать максимум 8 секторов для экземпляра NOR.
- **LX_NOR_SECTOR_MAPPING_CACHE_SIZE**: определяет размер кэша для сопоставлений логических секторов. По умолчанию имеет значение 16. Более высокие значения повышают производительность, но увеличивают нагрузку на память. Этот размер не может быть меньше 8 и всегда должен быть степенью числа 2.
- **LX_THREAD_SAFE_ENABLE**: если определен этот параметр, LevelX обеспечивает потокобезопасность благодаря использованию объекта мьютекса ThreadX через соответствующий API.
- **LX_STANDALONE_ENABLE**: если этот параметр определен, он позволяет использовать LevelX в изолированном режиме (без ОСРВ Azure). По умолчанию этот символ не определен.

> [!IMPORTANT]
> При использовании LevelX в автономном режиме (должен быть задан параметр **LX_STANDALONE_ENABLE**) файлы и библиотеки ThreadX не требуются. В этом режиме функция потокобезопасного режима LevelX.

## <a name="using-levelx"></a>Использование LevelX

Чтобы использовать LevelX отдельно или в сочетании с FileX, включите файл ***lx_api.h** _ в код, который ссылается на API LevelX. Также обеспечьте доступность объектного кода LevelX во время компоновки. В файлах _*_demo_filex_nand_flash.c_*_ и _ *_demo_filex_nor_flash.c_** просмотрите примеры работы с LevelX.
