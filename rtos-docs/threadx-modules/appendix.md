---
title: Приложение. Примеры для конкретных портов
description: В этой статье приведены примеры модулей ThreadX для конкретных портов.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b54b8b094e608052fdbfc392d93a57ebb34515ed
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815655"
---
# <a name="appendix---port-specific-examples"></a><span data-ttu-id="8fb80-103">Приложение. Примеры для конкретных портов</span><span class="sxs-lookup"><span data-stu-id="8fb80-103">Appendix - Port-specific examples</span></span>

## <a name="arm11-processor"></a><span data-ttu-id="8fb80-104">Процессор ARM11</span><span class="sxs-lookup"><span data-stu-id="8fb80-104">ARM11 processor</span></span>

### <a name="arm11-using-gcc"></a><span data-ttu-id="8fb80-105">ARM11 с поддержкой GCC</span><span class="sxs-lookup"><span data-stu-id="8fb80-105">ARM11 using GCC</span></span>

#### <a name="module-preamble-for-arm11-using-gcc"></a><span data-ttu-id="8fb80-106">Начальная часть модуля для ARM11 с поддержкой GCC</span><span class="sxs-lookup"><span data-stu-id="8fb80-106">Module preamble for ARM11 using GCC</span></span>

```armasm
    .arm
    .section .preamble, "ax"

    /* Define the module preamble.  */

    .global _txm_module_preamble
_txm_module_preamble:
    .word       0x4D4F4455                                      @ Module ID
    .word       0x5                                             @ Module Major Version
    .word       0x6                                             @ Module Minor Version
    .word       32                                              @ Module Preamble Size in 32-bit words
    .word       0x12345678                                      @ Module ID (application defined)
    .word       0x02000000                                      @ Module Properties where:
                                                                @   Bits 31-24: Compiler ID
                                                                @           0 -> IAR
                                                                @           1 -> ARM
                                                                @           2 -> GNU
    .word       _txm_module_thread_shell_entry - . - 0          @ Module Shell Entry Point
    .word       demo_module_start - . - 0                       @ Module Start Thread Entry Point
    .word       0                                               @ Module Stop Thread Entry Point
    .word       1                                               @ Module Start/Stop Thread Priority
    .word       1024                                            @ Module Start/Stop Thread Stack Size
    .word       _txm_module_callback_request_thread_entry - . - 0   @ Module Callback Thread Entry
    .word       1                                               @ Module Callback Thread Priority
    .word       1024                                            @ Module Callback Thread Stack Size
    .word       __code_size__                                   @ Module Code Size
    .word       __data_size__                                   @ Module Data Size
    .word       0                                               @ Reserved 0
    .word       0                                               @ Reserved 1
    .word       0                                               @ Reserved 2
    .word       0                                               @ Reserved 3
    .word       0                                               @ Reserved 4
    .word       0                                               @ Reserved 5
    .word       0                                               @ Reserved 6
    .word       0                                               @ Reserved 7  
    .word       0                                               @ Reserved 8  
    .word       0                                               @ Reserved 9
    .word       0                                               @ Reserved 10
    .word       0                                               @ Reserved 11
    .word       0                                               @ Reserved 12
    .word       0                                               @ Reserved 13
    .word       0                                               @ Reserved 14
    .word       0                                               @ Reserved 15
```

#### <a name="module-properties-for-arm11-using-gcc"></a><span data-ttu-id="8fb80-107">Свойства модуля для ARM11 с поддержкой GCC</span><span class="sxs-lookup"><span data-stu-id="8fb80-107">Module properties for ARM11 using GCC</span></span>

| <span data-ttu-id="8fb80-108">bit</span><span class="sxs-lookup"><span data-stu-id="8fb80-108">Bit</span></span> | <span data-ttu-id="8fb80-109">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-109">Value</span></span> | <span data-ttu-id="8fb80-110">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-110">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="8fb80-111">[23–0]</span><span class="sxs-lookup"><span data-stu-id="8fb80-111">[23-0]</span></span> | <span data-ttu-id="8fb80-112">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-112">0</span></span> | <span data-ttu-id="8fb80-113">Зарезервировано</span><span class="sxs-lookup"><span data-stu-id="8fb80-113">Reserved</span></span>
| <span data-ttu-id="8fb80-114">[31–24]</span><span class="sxs-lookup"><span data-stu-id="8fb80-114">[31-24]</span></span> | <br /><span data-ttu-id="8fb80-115">0x00</span><span class="sxs-lookup"><span data-stu-id="8fb80-115">0x00</span></span><br /><span data-ttu-id="8fb80-116">0x01</span><span class="sxs-lookup"><span data-stu-id="8fb80-116">0x01</span></span><br /><span data-ttu-id="8fb80-117">0x02</span><span class="sxs-lookup"><span data-stu-id="8fb80-117">0x02</span></span> | <span data-ttu-id="8fb80-118">**Идентификатор компилятора**</span><span class="sxs-lookup"><span data-stu-id="8fb80-118">**Compiler ID**</span></span><br /><span data-ttu-id="8fb80-119">IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-119">IAR</span></span><br /><span data-ttu-id="8fb80-120">ARM</span><span class="sxs-lookup"><span data-stu-id="8fb80-120">ARM</span></span><br /><span data-ttu-id="8fb80-121">GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-121">GNU</span></span> |

#### <a name="module-linker-for-arm11-using-gcc"></a><span data-ttu-id="8fb80-122">Компоновщик модулей для ARM11 с поддержкой GCC</span><span class="sxs-lookup"><span data-stu-id="8fb80-122">Module linker for ARM11 using GCC</span></span>

```c
MEMORY
{
  FLASH (rx) : ORIGIN = 0x080F0000, LENGTH = 0x00010000
  RAM   (wx) : ORIGIN = 0x64001800, LENGTH = 0x00100000
}


SECTIONS
{
  __FLASH_segment_start__ = 0x080F0000;
  __FLASH_segment_end__   = 0x080FFFFF;
  __RAM_segment_start__   = 0x64001800;
  __RAM_segment_end__     = 0x64011800;

  __HEAPSIZE__ = 128;

  __preamble_load_start__ = __FLASH_segment_start__;
  .preamble __FLASH_segment_start__ : AT(__FLASH_segment_start__)
  {
    __preamble_start__ = .;
    *(.preamble .preamble.*)
  }
  __preamble_end__ = __preamble_start__ + SIZEOF(.preamble);

  __dynsym_load_start__ =  ALIGN(__preamble_end__ , 4);
  .dynsym ALIGN(__dynsym_load_start__ , 4) : AT(ALIGN(__dynsym_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynsym))
    KEEP (*(.dynsym*))
    . = ALIGN(4);
  }
  __dynsym_end__ = __dynsym_load_start__ + SIZEOF(.dynsym);

  __dynstr_load_start__ =  ALIGN(__dynsym_end__ , 4);
  .dynstr ALIGN(__dynstr_load_start__ , 4) : AT(ALIGN(__dynstr_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynstr))
    KEEP (*(.dynstr*))
    . = ALIGN(4);
  }
  __dynstr_end__ = __dynstr_load_start__ + SIZEOF(.dynstr);

  __reldyn_load_start__ =  ALIGN(__dynstr_end__ , 4);
  .rel.dyn ALIGN(__reldyn_load_start__ , 4) : AT(ALIGN(__reldyn_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.dyn))
    KEEP (*(.rel.dyn*))
    . = ALIGN(4);
  }
  __reldyn_end__ = __reldyn_load_start__ + SIZEOF(.rel.dyn);

  __relplt_load_start__ =  ALIGN(__reldyn_end__ , 4);
  .rel.plt ALIGN(__relplt_load_start__ , 4) : AT(ALIGN(__relplt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.plt))
    KEEP (*(.rel.plt*))
    . = ALIGN(4);
  }
  __relplt_end__ = __relplt_load_start__ + SIZEOF(.rel.plt);

  __plt_load_start__ =  ALIGN(__relplt_end__ , 4);
  .plt ALIGN(__plt_load_start__ , 4) : AT(ALIGN(__plt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.plt))
    KEEP (*(.plt*))
    . = ALIGN(4);
  }
  __plt_end__ = __plt_load_start__ + SIZEOF(.plt);

  __interp_load_start__ =  ALIGN(__plt_end__ , 4);
  .interp ALIGN(__interp_load_start__ , 4) : AT(ALIGN(__interp_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.interp))
    KEEP (*(.interp*))
    . = ALIGN(4);
  }
  __interp_end__ = __interp_load_start__ + SIZEOF(.interp);

  __hash_load_start__ =  ALIGN(__interp_end__ , 4);
  .hash ALIGN(__hash_load_start__ , 4) : AT(ALIGN(__hash_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.hash))
    KEEP (*(.hash*))
    . = ALIGN(4);
  }
  __hash_end__ = __hash_load_start__ + SIZEOF(.hash);

  __text_load_start__ =  ALIGN(__hash_end__ , 4);
  .text ALIGN(__text_load_start__ , 4) : AT(ALIGN(__text_load_start__, 4))
  {
    __text_start__ = .;
    *(.text .text.* .glue_7t .glue_7 .gnu.linkonce.t.* .gcc_except_table  )
  }
  __text_end__ = __text_start__ + SIZEOF(.text);

  __dtors_load_start__ = ALIGN(__text_end__ , 4);
  .dtors ALIGN(__text_end__ , 4) : AT(ALIGN(__text_end__ , 4))
  {
    __dtors_start__ = .;
    KEEP (*(SORT(.dtors.*))) KEEP (*(.dtors))
  }
  __dtors_end__ = __dtors_start__ + SIZEOF(.dtors);

  __ctors_load_start__ = ALIGN(__dtors_end__ , 4);
  .ctors ALIGN(__dtors_end__ , 4) : AT(ALIGN(__dtors_end__ , 4))
  {
    __ctors_start__ = .;
    KEEP (*(SORT(.ctors.*))) KEEP (*(.ctors))
  }
  __ctors_end__ = __ctors_start__ + SIZEOF(.ctors);

  __got_load_start__ = ALIGN(__ctors_end__ , 4);
  .got ALIGN(__ctors_end__ , 4) : AT(ALIGN(__ctors_end__ , 4))
  {
    . = ALIGN(4);
    _sgot = .;
    KEEP (*(.got))
    KEEP (*(.got*))
    . = ALIGN(4);
    _egot = .;
  }
  __got_end__ =  __got_load_start__ + SIZEOF(.got);

  __rodata_load_start__ = ALIGN(__got_end__ , 4);
  .rodata ALIGN(__got_end__ , 4) : AT(ALIGN(__got_end__ , 4))
  {
    __rodata_start__ = .;
    *(.rodata .rodata.* .gnu.linkonce.r.*)
  }
  __rodata_end__ = __rodata_start__ + SIZEOF(.rodata);

  __code_size__ =  __rodata_end__ - __FLASH_segment_start__;

  __fast_load_start__ = ALIGN(__rodata_end__ , 4);

  __fast_load_end__ = __fast_load_start__ + SIZEOF(.fast);

  __new_got_start__ = ALIGN(__RAM_segment_start__ , 4);

  __new_got_end__ =  __new_got_start__ + SIZEOF(.got);

  .fast ALIGN(__new_got_end__ , 4) : AT(ALIGN(__rodata_end__ , 4))
  {
    __fast_start__ = .;
    *(.fast .fast.*)
  }
  __fast_end__ = __fast_start__ + SIZEOF(.fast);

  .fast_run ALIGN(__fast_end__ , 4) (NOLOAD) :
  {
    __fast_run_start__ = .;
    . = MAX(__fast_run_start__ + SIZEOF(.fast), .);
  }
  __fast_run_end__ = __fast_run_start__ + SIZEOF(.fast_run);

  __data_load_start__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4);
  .data ALIGN(__fast_run_end__ , 4) : AT(ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4))
  {
    __data_start__ = .;
    *(.data .data.* .gnu.linkonce.d.*)
  }
  __data_end__ = __data_start__ + SIZEOF(.data);

  __data_load_end__ = __data_load_start__ + SIZEOF(.data);

  __FLASH_segment_used_end__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4) + SIZEOF(.data);

  .data_run ALIGN(__fast_run_end__ , 4) (NOLOAD) :
  {
    __data_run_start__ = .;
    . = MAX(__data_run_start__ + SIZEOF(.data), .);
  }
  __data_run_end__ = __data_run_start__ + SIZEOF(.data_run);

  __bss_load_start__ = ALIGN(__data_run_end__ , 4);
  .bss ALIGN(__data_run_end__ , 4) (NOLOAD) : AT(ALIGN(__data_run_end__ , 4))
  {
    __bss_start__ = .;
    *(.bss .bss.* .gnu.linkonce.b.*) *(COMMON)
  }
  __bss_end__ = __bss_start__ + SIZEOF(.bss);

  __non_init_load_start__ = ALIGN(__bss_end__ , 4);
  .non_init ALIGN(__bss_end__ , 4) (NOLOAD) : AT(ALIGN(__bss_end__ , 4))
  {
    __non_init_start__ = .;
    *(.non_init .non_init.*)
  }
  __non_init_end__ = __non_init_start__ + SIZEOF(.non_init);

  __heap_load_start__ = ALIGN(__non_init_end__ , 4);
  .heap ALIGN(__non_init_end__ , 4) (NOLOAD) : AT(ALIGN(__non_init_end__ , 4))
  {
    __heap_start__ = .;
    *(.heap)
    . = ALIGN(MAX(__heap_start__ + __HEAPSIZE__ , .), 4);
  }
  __heap_end__ = __heap_start__ + SIZEOF(.heap);

  __data_size__ =  __heap_end__ - __RAM_segment_start__;

}
```

#### <a name="building-modules-for-arm11-using-gcc"></a><span data-ttu-id="8fb80-123">Создание модулей для ARM11 с поддержкой GCC</span><span class="sxs-lookup"><span data-stu-id="8fb80-123">Building Modules for ARM11 using GCC</span></span>

<span data-ttu-id="8fb80-124">Простой пример создания модуля ARM11 с поддержкой GCC с помощью командной строки:</span><span class="sxs-lookup"><span data-stu-id="8fb80-124">A simple command-line example for building an ARM11 module using GCC:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=arm1136j-s -msingle-pic-base -fPIC -mpic-register=r9 txm_module_preamble.S
arm-none-eabi-gcc -c -g -mcpu=arm1136j-s -msingle-pic-base -fPIC -mpic-register=r9 gcc_setup.S
arm-none-eabi-gcc -c -g -mcpu=arm1136j-s -msingle-pic-base -fPIC -mpic-register=r9 demo_threadx_module.c
arm-none-eabi-ld -A arm1136j-s -T demo_threadx_module.ld txm_module_preamble.o gcc_setup.o demo_threadx_module.o txm.a txm.a -o demo_threadx_module.out -M > demo_threadx_module.map
```

#### <a name="thread-extension-definition-for-arm11-using-gcc"></a><span data-ttu-id="8fb80-125">Определение расширения потоков для ARM11 с поддержкой GCC</span><span class="sxs-lookup"><span data-stu-id="8fb80-125">Thread extension definition for ARM11 using GCC</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;  \
                                VOID    *tx_thread_module_entry_info_ptr;
```

#### <a name="building-module-manager-for-arm11-using-gcc"></a><span data-ttu-id="8fb80-126">Создание диспетчера модулей для ARM11 с поддержкой GCC</span><span class="sxs-lookup"><span data-stu-id="8fb80-126">Building Module Manager for ARM11 using GCC</span></span>

<span data-ttu-id="8fb80-127">Пример отсутствует.</span><span class="sxs-lookup"><span data-stu-id="8fb80-127">No example is provided.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-arm11-using-gcc"></a><span data-ttu-id="8fb80-128">Атрибуты API включения внешней памяти для ARM11 с поддержкой GCC</span><span class="sxs-lookup"><span data-stu-id="8fb80-128">Attributes for external memory enable API for ARM11 using GCC</span></span>

<span data-ttu-id="8fb80-129">Эта функция не включена для данного порта.</span><span class="sxs-lookup"><span data-stu-id="8fb80-129">This feature not enabled on this port.</span></span>

### <a name="arm11-using-ac5"></a><span data-ttu-id="8fb80-130">ARM11 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-130">ARM11 using AC5</span></span>

#### <a name="module-preamble-for-arm11-using-ac5"></a><span data-ttu-id="8fb80-131">Начальная часть модуля для ARM11 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-131">Module preamble for ARM11 using AC5</span></span>

```armasm
    AREA  Init, CODE, READONLY

;    /* Define public symbols.  */

    EXPORT __txm_module_preamble

;    /* Define application-specific start/stop entry points for the module.  */

    IMPORT demo_module_start

;    /* Define common external references.  */

    IMPORT  _txm_module_thread_shell_entry
    IMPORT  _txm_module_callback_request_thread_entry
    IMPORT  |Image$$ER_RO$$Length|

__txm_module_preamble
        DCD       0x4D4F4455                                        ; Module ID
        DCD       0x5                                               ; Module Major Version
        DCD       0x3                                               ; Module Minor Version
        DCD       32                                                ; Module Preamble Size in 32-bit words
        DCD       0x12345678                                        ; Module ID (application defined)
        DCD       0x01000000                                        ; Module Properties where:
                                                                    ;   Bits 31-24: Compiler ID
                                                                    ;           0 -> IAR
                                                                    ;           1 -> ARM
                                                                    ;           2 -> GNU
                                                                    ;   Bits 23-0:  Reserved
        DCD       _txm_module_thread_shell_entry - . + .            ; Module Shell Entry Point
        DCD       demo_module_start - . + .                         ; Module Start Thread Entry Point
        DCD       0                                                 ; Module Stop Thread Entry Point
        DCD       1                                                 ; Module Start/Stop Thread Priority
        DCD       1024                                              ; Module Start/Stop Thread Stack Size
        DCD       _txm_module_callback_request_thread_entry - . + . ; Module Callback Thread Entry
        DCD       1                                                 ; Module Callback Thread Priority
        DCD       1024                                              ; Module Callback Thread Stack Size
        DCD       |Image$$ER_RO$$Length|                            ; Module Code Size
        DCD       0x4000                                            ; Module Data Size - default to 16K (need to make sure this is large enough for module's data needs!)
        DCD       0                                                 ; Reserved 0
        DCD       0                                                 ; Reserved 1
        DCD       0                                                 ; Reserved 2
        DCD       0                                                 ; Reserved 3
        DCD       0                                                 ; Reserved 4
        DCD       0                                                 ; Reserved 5
        DCD       0                                                 ; Reserved 6
        DCD       0                                                 ; Reserved 7
        DCD       0                                                 ; Reserved 8  
        DCD       0                                                 ; Reserved 9
        DCD       0                                                 ; Reserved 10
        DCD       0                                                 ; Reserved 11
        DCD       0                                                 ; Reserved 12
        DCD       0                                                 ; Reserved 13
        DCD       0                                                 ; Reserved 14
        DCD       0                                                 ; Reserved 15

        END
```

#### <a name="module-properties-for-arm11-using-ac5"></a><span data-ttu-id="8fb80-132">Свойства модуля для ARM11 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-132">Module properties for ARM11 using AC5</span></span>

| <span data-ttu-id="8fb80-133">bit</span><span class="sxs-lookup"><span data-stu-id="8fb80-133">Bit</span></span> | <span data-ttu-id="8fb80-134">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-134">Value</span></span> | <span data-ttu-id="8fb80-135">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-135">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="8fb80-136">[23–0]</span><span class="sxs-lookup"><span data-stu-id="8fb80-136">[23-0]</span></span> | <span data-ttu-id="8fb80-137">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-137">0</span></span> | <span data-ttu-id="8fb80-138">Зарезервировано</span><span class="sxs-lookup"><span data-stu-id="8fb80-138">Reserved</span></span>
| <span data-ttu-id="8fb80-139">[31–24]</span><span class="sxs-lookup"><span data-stu-id="8fb80-139">[31-24]</span></span> | <br /><span data-ttu-id="8fb80-140">0x00</span><span class="sxs-lookup"><span data-stu-id="8fb80-140">0x00</span></span><br /><span data-ttu-id="8fb80-141">0x01</span><span class="sxs-lookup"><span data-stu-id="8fb80-141">0x01</span></span><br /><span data-ttu-id="8fb80-142">0x02</span><span class="sxs-lookup"><span data-stu-id="8fb80-142">0x02</span></span> | <span data-ttu-id="8fb80-143">**Идентификатор компилятора**</span><span class="sxs-lookup"><span data-stu-id="8fb80-143">**Compiler ID**</span></span><br /><span data-ttu-id="8fb80-144">IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-144">IAR</span></span><br /><span data-ttu-id="8fb80-145">ARM</span><span class="sxs-lookup"><span data-stu-id="8fb80-145">ARM</span></span><br /><span data-ttu-id="8fb80-146">GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-146">GNU</span></span> |

#### <a name="module-linker-for-arm11-using-ac5"></a><span data-ttu-id="8fb80-147">Компоновщик модулей для ARM11 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-147">Module linker for ARM11 using AC5</span></span>

<span data-ttu-id="8fb80-148">Пример на основе командной строки без файла компоновщика.</span><span class="sxs-lookup"><span data-stu-id="8fb80-148">Built on command-line, no linker file example.</span></span>

#### <a name="building-modules-for-arm11-using-ac5"></a><span data-ttu-id="8fb80-149">Создание модулей для ARM11 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-149">Building Modules for ARM11 using AC5</span></span>

<span data-ttu-id="8fb80-150">Простой пример создания модуля ARM11 с поддержкой AC5 с помощью командной строки:</span><span class="sxs-lookup"><span data-stu-id="8fb80-150">A simple command-line example for building an ARM11 module using AC5:</span></span>

```dos
armasm -g --cpu ARM1136J-S --apcs /interwork --apcs /ropi --apcs /rwpi txm_module_preamble.s
armcc -g -c -O0 --cpu ARM1136J-S --apcs /interwork --apcs /ropi --apcs /rwpi demo_threadx_module.c
armlink -d -o demo_threadx_module.axf --elf --ro 0 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list demo_threadx_module.map txm_module_preamble.o demo_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-arm11-using-ac5"></a><span data-ttu-id="8fb80-151">Определение расширения потоков для ARM11 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-151">Thread extension definition for ARM11 using AC5</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;  \
                                VOID    *tx_thread_module_entry_info_ptr;
```

#### <a name="building-module-manager-for-arm11-using-ac5"></a><span data-ttu-id="8fb80-152">Создание диспетчера модулей для ARM11 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-152">Building Module Manager for ARM11 using AC5</span></span>

<span data-ttu-id="8fb80-153">Простой пример создания диспетчера модулей ARM11 с поддержкой AC5 с помощью командной строки:</span><span class="sxs-lookup"><span data-stu-id="8fb80-153">A simple command-line example for building an ARM11 module manager using AC5:</span></span>

```dos
armasm -g --cpu ARM1136J-S --apcs /interwork tx_initialize_low_level.s
armcc -g -c -O2 --cpu ARM1136J-S --apcs /interwork demo_threadx_module_manager.c
armcc -g -c -O2 --cpu ARM1136J-S --apcs /interwork module_code.c
armlink -d -o demo_threadx_module_manager.axf --elf --ro 0 --first tx_initialize_low_level.o(Init) --remove --map --symbols --list demo_threadx_module_manager.map tx_initialize_low_level.o demo_threadx_module_manager.o module_code.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-arm11-using-ac5"></a><span data-ttu-id="8fb80-154">Атрибуты API включения внешней памяти для ARM11 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-154">Attributes for external memory enable API for ARM11 using AC5</span></span>

<span data-ttu-id="8fb80-155">Эта функция не включена для данного порта.</span><span class="sxs-lookup"><span data-stu-id="8fb80-155">This feature not enabled on this port.</span></span>

## <a name="cortex-a7-processor"></a><span data-ttu-id="8fb80-156">Процессор Cortex-A7</span><span class="sxs-lookup"><span data-stu-id="8fb80-156">Cortex-A7 processor</span></span>

### <a name="cortex-a7-using-ac5"></a><span data-ttu-id="8fb80-157">Cortex-A7 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-157">Cortex-A7 using AC5</span></span>

#### <a name="module-preamble-for-cortex-a7-using-ac5"></a><span data-ttu-id="8fb80-158">Начальная часть модуля для Cortex-A7 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-158">Module preamble for Cortex-A7 using AC5</span></span>

```armasm
    AREA  Init, CODE, READONLY

;    /* Define public symbols.  */

    EXPORT __txm_module_preamble

;    /* Define application-specific start/stop entry points for the module.  */

    IMPORT demo_module_start

;    /* Define common external references.  */

    IMPORT  _txm_module_thread_shell_entry
    IMPORT  _txm_module_callback_request_thread_entry
    IMPORT  |Image$$ER_RO$$Length|
    IMPORT  |Image$$ER_RW$$Length|

__txm_module_preamble
    DCD       0x4D4F4455                                        ; Module ID
    DCD       0x5                                               ; Module Major Version
    DCD       0x3                                               ; Module Minor Version
    DCD       32                                                ; Module Preamble Size in 32-bit words
    DCD       0x12345678                                        ; Module ID (application defined)
    DCD       0x01000001                                        ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bits 23-1:  Reserved
                                                                ;   Bit 0:  0 -> Privileged mode execution (no MMU protection)
                                                                ;           1 -> User mode execution (MMU protection)
    DCD       _txm_module_thread_shell_entry - . + .            ; Module Shell Entry Point
    DCD       demo_module_start - . + .                         ; Module Start Thread Entry Point
    DCD       0                                                 ; Module Stop Thread Entry Point
    DCD       1                                                 ; Module Start/Stop Thread Priority
    DCD       1024                                              ; Module Start/Stop Thread Stack Size
    DCD       _txm_module_callback_request_thread_entry - . + . ; Module Callback Thread Entry
    DCD       1                                                 ; Module Callback Thread Priority
    DCD       1024                                              ; Module Callback Thread Stack Size
    DCD       |Image$$ER_RO$$Length| + |Image$$ER_RW$$Length|   ; Module Code Size
    DCD       0x4000                                            ; Module Data Size - default to 16K (need to make sure this is large enough for module's data needs!)
    DCD       0                                                 ; Reserved 0
    DCD       0                                                 ; Reserved 1
    DCD       0                                                 ; Reserved 2
    DCD       0                                                 ; Reserved 3
    DCD       0                                                 ; Reserved 4
    DCD       0                                                 ; Reserved 5
    DCD       0                                                 ; Reserved 6
    DCD       0                                                 ; Reserved 7
    DCD       0                                                 ; Reserved 8
    DCD       0                                                 ; Reserved 9
    DCD       0                                                 ; Reserved 10
    DCD       0                                                 ; Reserved 11
    DCD       0                                                 ; Reserved 12
    DCD       0                                                 ; Reserved 13
    DCD       0                                                 ; Reserved 14
    DCD       0                                                 ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-a7-using-ac5"></a><span data-ttu-id="8fb80-159">Свойства модуля для Cortex-A7 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-159">Module properties for Cortex-A7 using AC5</span></span>

| <span data-ttu-id="8fb80-160">bit</span><span class="sxs-lookup"><span data-stu-id="8fb80-160">Bit</span></span> | <span data-ttu-id="8fb80-161">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-161">Value</span></span> | <span data-ttu-id="8fb80-162">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-162">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="8fb80-163">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-163">0</span></span> | <span data-ttu-id="8fb80-164">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-164">0</span></span><br /><span data-ttu-id="8fb80-165">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-165">1</span></span> | <span data-ttu-id="8fb80-166">Выполнение в привилегированном режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-166">Privileged mode execution</span></span><br /><span data-ttu-id="8fb80-167">Выполнение в пользовательском режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-167">User mode execution</span></span> |
| <span data-ttu-id="8fb80-168">[23–1]</span><span class="sxs-lookup"><span data-stu-id="8fb80-168">[23-1]</span></span> | <span data-ttu-id="8fb80-169">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-169">0</span></span> | <span data-ttu-id="8fb80-170">Зарезервировано</span><span class="sxs-lookup"><span data-stu-id="8fb80-170">Reserved</span></span>
| <span data-ttu-id="8fb80-171">[31–24]</span><span class="sxs-lookup"><span data-stu-id="8fb80-171">[31-24]</span></span> | <br /><span data-ttu-id="8fb80-172">0x00</span><span class="sxs-lookup"><span data-stu-id="8fb80-172">0x00</span></span><br /><span data-ttu-id="8fb80-173">0x01</span><span class="sxs-lookup"><span data-stu-id="8fb80-173">0x01</span></span><br /><span data-ttu-id="8fb80-174">0x02</span><span class="sxs-lookup"><span data-stu-id="8fb80-174">0x02</span></span> | <span data-ttu-id="8fb80-175">**Идентификатор компилятора**</span><span class="sxs-lookup"><span data-stu-id="8fb80-175">**Compiler ID**</span></span><br /><span data-ttu-id="8fb80-176">IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-176">IAR</span></span><br /><span data-ttu-id="8fb80-177">ARM</span><span class="sxs-lookup"><span data-stu-id="8fb80-177">ARM</span></span><br /><span data-ttu-id="8fb80-178">GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-178">GNU</span></span> |

#### <a name="module-linker-for-cortex-a7-using-ac5"></a><span data-ttu-id="8fb80-179">Компоновщик модулей для Cortex-A7 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-179">Module linker for Cortex-A7 using AC5</span></span>

<span data-ttu-id="8fb80-180">Пример на основе командной строки без файла компоновщика.</span><span class="sxs-lookup"><span data-stu-id="8fb80-180">Built on command-line, no linker file example.</span></span>

#### <a name="building-modules-for-cortex-a7-using-ac5"></a><span data-ttu-id="8fb80-181">Создание модулей для Cortex-A7 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-181">Building Modules for Cortex-A7 using AC5</span></span>

<span data-ttu-id="8fb80-182">Простой пример создания модуля Cortex-A7 с поддержкой AC5 с помощью командной строки:</span><span class="sxs-lookup"><span data-stu-id="8fb80-182">A simple command-line example for building a Cortex-A7 module using AC5:</span></span>

```dos
armasm -g --cpu=cortex-a7.no_neon --fpu=softvfp --apcs=/interwork/ropi/rwpi txm_module_preamble.s
armcc  -g --cpu=cortex-a7.no_neon --fpu=softvfp -c --apcs=/interwork/ropi/rwpi --lower_ropi demo_threadx_module.c
armlink -d -o demo_threadx_module.axf --elf --ro 0 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list demo_threadx_module.map txm_module_preamble.o demo_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-a7-using-ac5"></a><span data-ttu-id="8fb80-183">Определение расширения потоков для Cortex-A7 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-183">Thread extension definition for Cortex-A7 using AC5</span></span>

```c
#define TX_THREAD_EXTENSION_2   ULONG   tx_thread_vfp_enable;                   \
                                VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-a7-using-ac5"></a><span data-ttu-id="8fb80-184">Создание диспетчера модулей для Cortex-A7 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-184">Building Module Manager for Cortex-A7 using AC5</span></span>

<span data-ttu-id="8fb80-185">Простой пример создания диспетчера модулей Cortex-A7 с поддержкой AC5 с помощью командной строки:</span><span class="sxs-lookup"><span data-stu-id="8fb80-185">A simple command-line example for building a Cortex-A7 module manager using AC5:</span></span>

```dos
armasm -g --cpu=cortex-a7.no_neon --fpu=softvfp --apcs=interwork tx_initialize_low_level.s
armcc -g --cpu=cortex-a7.no_neon --fpu=softvfp -c demo_threadx_module_manager.c
armcc -g --cpu=cortex-a7.no_neon --fpu=softvfp -c module_code.c
armlink -d -o demo_threadx_module_manager.axf --elf --ro 0x80000000 --first tx_initialize_low_level.o(VECTORS) --remove --map --symbols --list demo_threadx_module_manager.map tx_initialize_low_level.o demo_threadx_module_manager.o module_code.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-a7-using-ac5"></a><span data-ttu-id="8fb80-186">Атрибуты API включения внешней памяти для Cortex-A7 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-186">Attributes for external memory enable API for Cortex-A7 using AC5</span></span>

<span data-ttu-id="8fb80-187">Для настройки параметров общей памяти можно использовать следующие атрибуты:</span><span class="sxs-lookup"><span data-stu-id="8fb80-187">The following attributes can be used to set up shared memory settings:</span></span>
| <span data-ttu-id="8fb80-188">Параметр атрибута</span><span class="sxs-lookup"><span data-stu-id="8fb80-188">Attribute parameter</span></span> | <span data-ttu-id="8fb80-189">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-189">Meaning</span></span> |
|---|---|
| <span data-ttu-id="8fb80-190">TXM_MMU_ATTRIBUTE_XN</span><span class="sxs-lookup"><span data-stu-id="8fb80-190">TXM_MMU_ATTRIBUTE_XN</span></span> | <span data-ttu-id="8fb80-191">Никогда не выполнять.</span><span class="sxs-lookup"><span data-stu-id="8fb80-191">Execute Never</span></span> |
| <span data-ttu-id="8fb80-192">TXM_MMU_ATTRIBUTE_B</span><span class="sxs-lookup"><span data-stu-id="8fb80-192">TXM_MMU_ATTRIBUTE_B</span></span> | <span data-ttu-id="8fb80-193">Параметр B.</span><span class="sxs-lookup"><span data-stu-id="8fb80-193">B setting</span></span> |
| <span data-ttu-id="8fb80-194">TXM_MMU_ATTRIBUTE_C</span><span class="sxs-lookup"><span data-stu-id="8fb80-194">TXM_MMU_ATTRIBUTE_C</span></span> | <span data-ttu-id="8fb80-195">Параметр C.</span><span class="sxs-lookup"><span data-stu-id="8fb80-195">C setting</span></span> |
| <span data-ttu-id="8fb80-196">TXM_MMU_ATTRIBUTE_AP</span><span class="sxs-lookup"><span data-stu-id="8fb80-196">TXM_MMU_ATTRIBUTE_AP</span></span> | <span data-ttu-id="8fb80-197">Параметр AP.</span><span class="sxs-lookup"><span data-stu-id="8fb80-197">AP setting</span></span> |
| <span data-ttu-id="8fb80-198">TXM_MMU_ATTRIBUTE_TEX</span><span class="sxs-lookup"><span data-stu-id="8fb80-198">TXM_MMU_ATTRIBUTE_TEX</span></span> | <span data-ttu-id="8fb80-199">Параметр TEX.</span><span class="sxs-lookup"><span data-stu-id="8fb80-199">TEX setting</span></span> |

<span data-ttu-id="8fb80-200">Сведения о настройке этих параметров см. в документации по ARM.</span><span class="sxs-lookup"><span data-stu-id="8fb80-200">See ARM documentation for how these settings are configured.</span></span>

## <a name="cortex-m3-processor"></a><span data-ttu-id="8fb80-201">Процессор Cortex-M3</span><span class="sxs-lookup"><span data-stu-id="8fb80-201">Cortex-M3 processor</span></span>

### <a name="cortex-m3-using-ac5"></a><span data-ttu-id="8fb80-202">Cortex-M3 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-202">Cortex-M3 using AC5</span></span>

#### <a name="module-preamble-for-cortex-m3-using-ac5"></a><span data-ttu-id="8fb80-203">Начальная часть модуля для Cortex-M3 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-203">Module preamble for Cortex-M3 using AC5</span></span>

```armasm
    AREA Init, CODE, READONLY

    PRESERVE8

    ; Define public symbols

    EXPORT __txm_module_preamble

    ; Define application-specific start/stop entry points for the module

    EXTERN demo_module_start

    ; Define common external references

    IMPORT  _txm_module_thread_shell_entry
    IMPORT  _txm_module_callback_request_thread_entry
    IMPORT  |Image$$ER_RO$$Length|
    IMPORT  |Image$$ER_RW$$Length|
    IMPORT  |Image$$ER_RW$$RW$$Length|
    IMPORT  |Image$$ER_RW$$ZI$$Length|
    IMPORT  |Image$$ER_ZI$$ZI$$Length|

__txm_module_preamble
    DCD     0x4D4F4455                                          ; Module ID
    DCD     0x6                                                 ; Module Major Version
    DCD     0x1                                                 ; Module Minor Version
    DCD     32                                                  ; Module Preamble Size in 32-bit words
    DCD     0x12345678                                          ; Module ID (application defined)
    DCD     0x01000007                                          ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bit 0:  0 -> Privileged mode execution
                                                                ;           1 -> User mode execution
                                                                ;   Bit 1:  0 -> No MPU protection
                                                                ;           1 -> MPU protection (must have user mode selected)
                                                                ;   Bit 2:  0 -> Disable shared/external memory access
                                                                ;           1 -> Enable shared/external memory access
    DCD     _txm_module_thread_shell_entry - __txm_module_preamble              ; Module Shell Entry Point
    DCD     demo_module_start - __txm_module_preamble           ; Module Start Thread Entry Point
    DCD     0                                                   ; Module Stop Thread Entry Point
    DCD     1                                                   ; Module Start/Stop Thread Priority
    DCD     1024                                                ; Module Start/Stop Thread Stack Size
    DCD     _txm_module_callback_request_thread_entry - __txm_module_preamble   ; Module Callback Thread Entry
    DCD     1                                                   ; Module Callback Thread Priority
    DCD     1024                                                ; Module Callback Thread Stack Size
    DCD     |Image$$ER_RO$$Length| + |Image$$ER_RW$$Length|         ; Module Code Size
    DCD     |Image$$ER_RW$$Length| + |Image$$ER_ZI$$ZI$$Length| ; Module Data Size
    DCD     0                                                   ; Reserved 0
    DCD     0                                                   ; Reserved 1
    DCD     0                                                   ; Reserved 2
    DCD     0                                                   ; Reserved 3
    DCD     0                                                   ; Reserved 4
    DCD     0                                                   ; Reserved 5
    DCD     0                                                   ; Reserved 6
    DCD     0                                                   ; Reserved 7
    DCD     0                                                   ; Reserved 8
    DCD     0                                                   ; Reserved 9
    DCD     0                                                   ; Reserved 10
    DCD     0                                                   ; Reserved 11
    DCD     0                                                   ; Reserved 12
    DCD     0                                                   ; Reserved 13
    DCD     0                                                   ; Reserved 14
    DCD     0                                                   ; Reserved 15

    END

```

#### <a name="module-properties-for-cortex-m3-using-ac5"></a><span data-ttu-id="8fb80-204">Свойства модуля для Cortex-M3 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-204">Module properties for Cortex-M3 using AC5</span></span>

| <span data-ttu-id="8fb80-205">bit</span><span class="sxs-lookup"><span data-stu-id="8fb80-205">Bit</span></span> | <span data-ttu-id="8fb80-206">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-206">Value</span></span> | <span data-ttu-id="8fb80-207">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-207">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="8fb80-208">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-208">0</span></span> | <span data-ttu-id="8fb80-209">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-209">0</span></span><br /><span data-ttu-id="8fb80-210">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-210">1</span></span> | <span data-ttu-id="8fb80-211">Выполнение в привилегированном режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-211">Privileged mode execution</span></span><br /><span data-ttu-id="8fb80-212">Выполнение в пользовательском режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-212">User mode execution</span></span> |
| <span data-ttu-id="8fb80-213">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-213">1</span></span> | <span data-ttu-id="8fb80-214">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-214">0</span></span><br /><span data-ttu-id="8fb80-215">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-215">1</span></span> | <span data-ttu-id="8fb80-216">Без защиты MPU.</span><span class="sxs-lookup"><span data-stu-id="8fb80-216">No MPU protection</span></span><br /><span data-ttu-id="8fb80-217">Защита MPU (необходимо выбрать пользовательский режим)</span><span class="sxs-lookup"><span data-stu-id="8fb80-217">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="8fb80-218">2</span><span class="sxs-lookup"><span data-stu-id="8fb80-218">2</span></span> | <span data-ttu-id="8fb80-219">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-219">0</span></span><br /><span data-ttu-id="8fb80-220">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-220">1</span></span> | <span data-ttu-id="8fb80-221">Отключение доступа к общей или внешней памяти</span><span class="sxs-lookup"><span data-stu-id="8fb80-221">Disable shared/external memory access</span></span><br /><span data-ttu-id="8fb80-222">Включение доступа к общей или внешней памяти</span><span class="sxs-lookup"><span data-stu-id="8fb80-222">Enable shared/external memory access</span></span> |
| <span data-ttu-id="8fb80-223">[23–3]</span><span class="sxs-lookup"><span data-stu-id="8fb80-223">[23-3]</span></span> | <span data-ttu-id="8fb80-224">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-224">0</span></span> | <span data-ttu-id="8fb80-225">Зарезервировано</span><span class="sxs-lookup"><span data-stu-id="8fb80-225">Reserved</span></span>
| <span data-ttu-id="8fb80-226">[31–24]</span><span class="sxs-lookup"><span data-stu-id="8fb80-226">[31-24]</span></span> | <br /><span data-ttu-id="8fb80-227">0x00</span><span class="sxs-lookup"><span data-stu-id="8fb80-227">0x00</span></span><br /><span data-ttu-id="8fb80-228">0x01</span><span class="sxs-lookup"><span data-stu-id="8fb80-228">0x01</span></span><br /><span data-ttu-id="8fb80-229">0x02</span><span class="sxs-lookup"><span data-stu-id="8fb80-229">0x02</span></span> | <span data-ttu-id="8fb80-230">**Идентификатор компилятора**</span><span class="sxs-lookup"><span data-stu-id="8fb80-230">**Compiler ID**</span></span><br /><span data-ttu-id="8fb80-231">IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-231">IAR</span></span><br /><span data-ttu-id="8fb80-232">ARM</span><span class="sxs-lookup"><span data-stu-id="8fb80-232">ARM</span></span><br /><span data-ttu-id="8fb80-233">GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-233">GNU</span></span> |

#### <a name="module-linker-for-cortex-m3-using-ac5"></a><span data-ttu-id="8fb80-234">Компоновщик модулей для Cortex-M3 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-234">Module linker for Cortex-M3 using AC5</span></span>

<span data-ttu-id="8fb80-235">Пример файла компоновщика не предоставляется. Компоновка выполняется в командной строке.</span><span class="sxs-lookup"><span data-stu-id="8fb80-235">No example linker file is provided; linking is done on the command line.</span></span> <span data-ttu-id="8fb80-236">Ознакомьтесь со следующим разделом.</span><span class="sxs-lookup"><span data-stu-id="8fb80-236">See next section.</span></span>

#### <a name="building-modules-for-cortex-m3-using-ac5"></a><span data-ttu-id="8fb80-237">Создание модулей для Cortex-M3 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-237">Building Modules for Cortex-M3 using AC5</span></span>

<span data-ttu-id="8fb80-238">Пример сценария создания приведен ниже.</span><span class="sxs-lookup"><span data-stu-id="8fb80-238">An example build script is provided:</span></span>

```dos
armasm -g --cpu=cortex-m3 --apcs=/interwork/ropi/rwpi txm_module_preamble.S
armcc  -g --cpu=cortex-m3 -c --apcs=/interwork/ropi/rwpi --lower_ropi -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module.c
armlink -d -o sample_threadx_module.axf --elf --ro=0x30000 --rw=0x40000 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list sample_threadx_module.map txm_module_preamble.o sample_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-m3-using-ac5"></a><span data-ttu-id="8fb80-239">Определение расширения потоков для Cortex-M3 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-239">Thread extension definition for Cortex-M3 using AC5</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m3-using-ac5"></a><span data-ttu-id="8fb80-240">Создание диспетчера модулей для Cortex-M3 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-240">Building Module Manager for Cortex-M3 using AC5</span></span>

<span data-ttu-id="8fb80-241">Ознакомьтесь с примером build_threadx_module_manager_demo.bat.</span><span class="sxs-lookup"><span data-stu-id="8fb80-241">See example build_threadx_module_manager_demo.bat:</span></span>

```dos
armasm -g --cpu=cortex-m3 --apcs=interwork tx_initialize_low_level.S
armcc -g --cpu=cortex-m3 -c -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module_manager.c
armlink -d -o sample_threadx_module_manager.axf --elf --ro 0x00000000 --first tx_initialize_low_level.o(RESET) --remove --map --symbols --list sample_threadx_module_manager.map tx_initialize_low_level.o sample_threadx_module_manager.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m3-using-ac5"></a><span data-ttu-id="8fb80-242">Атрибуты API включения внешней памяти для Cortex-M3 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-242">Attributes for external memory enable API for Cortex-M3 using AC5</span></span>

<span data-ttu-id="8fb80-243">Модуль всегда имеет доступ на чтение к общей памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-243">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="8fb80-244">Параметр атрибута</span><span class="sxs-lookup"><span data-stu-id="8fb80-244">Attribute parameter</span></span> | <span data-ttu-id="8fb80-245">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-245">Meaning</span></span> |
|---|---|
| <span data-ttu-id="8fb80-246">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="8fb80-246">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="8fb80-247">Доступ для записи.</span><span class="sxs-lookup"><span data-stu-id="8fb80-247">Write access</span></span> |

### <a name="cortex-m3-using-ac6"></a><span data-ttu-id="8fb80-248">Cortex-M3 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-248">Cortex-M3 using AC6</span></span>

#### <a name="module-preamble-for-cortex-m3-using-ac6"></a><span data-ttu-id="8fb80-249">Начальная часть модуля для Cortex-M3 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-249">Module preamble for Cortex-M3 using AC6</span></span>

```armasm
    .text
    .align 4
    .syntax unified
    .section Init
    
    // Define public symbols
    .global __txm_module_preamble

    // Define application-specific start/stop entry points for the module
    .global demo_module_start

    // Define common external references
    .global  _txm_module_thread_shell_entry
    .global  _txm_module_callback_request_thread_entry

    .eabi_attribute Tag_ABI_PCS_RO_data, 1
    .eabi_attribute Tag_ABI_PCS_R9_use,  1
    .eabi_attribute Tag_ABI_PCS_RW_data, 2

__txm_module_preamble:
    .dc.l   0x4D4F4455                                          // Module ID
    .dc.l   0x6                                                 // Module Major Version
    .dc.l   0x1                                                 // Module Minor Version
    .dc.l   32                                                  // Module Preamble Size in 32-bit words
    .dc.l   0x12345678                                          // Module ID (application defined)
    .dc.l   0x01000007                                          // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
    .dc.l   _txm_module_thread_shell_entry - __txm_module_preamble // Module Shell Entry Point
    .dc.l   demo_module_start - __txm_module_preamble           // Module Start Thread Entry Point
    .dc.l   0                                                   // Module Stop Thread Entry Point
    .dc.l   1                                                   // Module Start/Stop Thread Priority
    .dc.l   1024                                                // Module Start/Stop Thread Stack Size
    .dc.l   _txm_module_callback_request_thread_entry - __txm_module_preamble // Module Callback Thread Entry
    .dc.l   1                                                   // Module Callback Thread Priority
    .dc.l   1024                                                // Module Callback Thread Stack Size
    .dc.l   0x10000                                             // Module Code Size
    .dc.l   0x10000                                             // Module Data Size
    .dc.l   0                                                   // Reserved 0
    .dc.l   0                                                   // Reserved 1
    .dc.l   0                                                   // Reserved 2
    .dc.l   0                                                   // Reserved 3
    .dc.l   0                                                   // Reserved 4
    .dc.l   0                                                   // Reserved 5
    .dc.l   0                                                   // Reserved 6
    .dc.l   0                                                   // Reserved 7
    .dc.l   0                                                   // Reserved 8
    .dc.l   0                                                   // Reserved 9
    .dc.l   0                                                   // Reserved 10
    .dc.l   0                                                   // Reserved 11
    .dc.l   0                                                   // Reserved 12
    .dc.l   0                                                   // Reserved 13
    .dc.l   0                                                   // Reserved 14
    .dc.l   0                                                   // Reserved 15
```

#### <a name="module-properties-for-cortex-m3-using-ac6"></a><span data-ttu-id="8fb80-250">Свойства модуля для Cortex-M3 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-250">Module properties for Cortex-M3 using AC6</span></span>

| <span data-ttu-id="8fb80-251">bit</span><span class="sxs-lookup"><span data-stu-id="8fb80-251">Bit</span></span> | <span data-ttu-id="8fb80-252">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-252">Value</span></span> | <span data-ttu-id="8fb80-253">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-253">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="8fb80-254">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-254">0</span></span> | <span data-ttu-id="8fb80-255">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-255">0</span></span><br /><span data-ttu-id="8fb80-256">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-256">1</span></span> | <span data-ttu-id="8fb80-257">Выполнение в привилегированном режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-257">Privileged mode execution</span></span><br /><span data-ttu-id="8fb80-258">Выполнение в пользовательском режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-258">User mode execution</span></span> |
| <span data-ttu-id="8fb80-259">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-259">1</span></span> | <span data-ttu-id="8fb80-260">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-260">0</span></span><br /><span data-ttu-id="8fb80-261">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-261">1</span></span> | <span data-ttu-id="8fb80-262">Без защиты MPU.</span><span class="sxs-lookup"><span data-stu-id="8fb80-262">No MPU protection</span></span><br /><span data-ttu-id="8fb80-263">Защита MPU (необходимо выбрать пользовательский режим).</span><span class="sxs-lookup"><span data-stu-id="8fb80-263">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="8fb80-264">2</span><span class="sxs-lookup"><span data-stu-id="8fb80-264">2</span></span> | <span data-ttu-id="8fb80-265">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-265">0</span></span><br /><span data-ttu-id="8fb80-266">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-266">1</span></span> | <span data-ttu-id="8fb80-267">Отключение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-267">Disable shared/external memory access</span></span><br /><span data-ttu-id="8fb80-268">Включение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-268">Enable shared/external memory access</span></span> |
| <span data-ttu-id="8fb80-269">[23–3]</span><span class="sxs-lookup"><span data-stu-id="8fb80-269">[23-3]</span></span> | <span data-ttu-id="8fb80-270">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-270">0</span></span> | <span data-ttu-id="8fb80-271">Зарезервировано</span><span class="sxs-lookup"><span data-stu-id="8fb80-271">Reserved</span></span>
| <span data-ttu-id="8fb80-272">[31–24]</span><span class="sxs-lookup"><span data-stu-id="8fb80-272">[31-24]</span></span> | <br /><span data-ttu-id="8fb80-273">0x00</span><span class="sxs-lookup"><span data-stu-id="8fb80-273">0x00</span></span><br /><span data-ttu-id="8fb80-274">0x01</span><span class="sxs-lookup"><span data-stu-id="8fb80-274">0x01</span></span><br /><span data-ttu-id="8fb80-275">0x02</span><span class="sxs-lookup"><span data-stu-id="8fb80-275">0x02</span></span> | <span data-ttu-id="8fb80-276">**Идентификатор компилятора**</span><span class="sxs-lookup"><span data-stu-id="8fb80-276">**Compiler ID**</span></span><br /><span data-ttu-id="8fb80-277">IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-277">IAR</span></span><br /><span data-ttu-id="8fb80-278">ARM</span><span class="sxs-lookup"><span data-stu-id="8fb80-278">ARM</span></span><br /><span data-ttu-id="8fb80-279">GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-279">GNU</span></span> |

#### <a name="module-linker-for-cortex-m3-using-ac6"></a><span data-ttu-id="8fb80-280">Компоновщик модулей для Cortex-M3 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-280">Module linker for Cortex-M3 using AC6</span></span>

<span data-ttu-id="8fb80-281">Файл компоновщика не используется.</span><span class="sxs-lookup"><span data-stu-id="8fb80-281">No linker file is used.</span></span> <span data-ttu-id="8fb80-282">Ознакомьтесь с параметрами проекта.</span><span class="sxs-lookup"><span data-stu-id="8fb80-282">See project settings.</span></span>

#### <a name="building-modules-for-cortex-m3-using-ac6"></a><span data-ttu-id="8fb80-283">Создание модулей для Cortex-M3 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-283">Building Modules for Cortex-M3 using AC6</span></span>

<span data-ttu-id="8fb80-284">Предоставлен пример рабочей области.</span><span class="sxs-lookup"><span data-stu-id="8fb80-284">An example workspace is provided.</span></span> <span data-ttu-id="8fb80-285">Можно создать библиотеку ThreadX, библиотеку модулей ThreadX, пример проекта модуля и пример проекта диспетчера модулей.</span><span class="sxs-lookup"><span data-stu-id="8fb80-285">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m3-using-ac6"></a><span data-ttu-id="8fb80-286">Определение расширения потоков для Cortex-M3 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-286">Thread extension definition for Cortex-M3 using AC6</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m3-using-ac6"></a><span data-ttu-id="8fb80-287">Создание диспетчера модулей для Cortex-M3 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-287">Building Module Manager for Cortex-M3 using AC6</span></span>

<span data-ttu-id="8fb80-288">Предоставлен пример рабочей области.</span><span class="sxs-lookup"><span data-stu-id="8fb80-288">An example workspace is provided.</span></span> <span data-ttu-id="8fb80-289">Можно создать библиотеку ThreadX, библиотеку модулей ThreadX, пример проекта модуля и пример проекта диспетчера модулей.</span><span class="sxs-lookup"><span data-stu-id="8fb80-289">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m3-using-ac6"></a><span data-ttu-id="8fb80-290">Атрибуты API включения внешней памяти для Cortex-M3 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-290">Attributes for external memory enable API for Cortex-M3 using AC6</span></span>

<span data-ttu-id="8fb80-291">Модуль всегда имеет доступ на чтение к общей памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-291">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="8fb80-292">Параметр атрибута</span><span class="sxs-lookup"><span data-stu-id="8fb80-292">Attribute parameter</span></span> | <span data-ttu-id="8fb80-293">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-293">Meaning</span></span> |
|---|---|
| <span data-ttu-id="8fb80-294">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="8fb80-294">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="8fb80-295">Доступ для записи.</span><span class="sxs-lookup"><span data-stu-id="8fb80-295">Write access</span></span> |

### <a name="cortex-m3-using-gnu"></a><span data-ttu-id="8fb80-296">Cortex-M3 с поддержкой GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-296">Cortex-M3 using GNU</span></span>

#### <a name="module-preamble-for-cortex-m3-using-gnu"></a><span data-ttu-id="8fb80-297">Начальная часть модуля для Cortex-M3 с поддержкой GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-297">Module preamble for Cortex-M3 using GNU</span></span>

```armasm
    .text
    .align 4
    .syntax unified

    /* Define public symbols.  */
    .global __txm_module_preamble

    /* Define application-specific start/stop entry points for the module.  */
    .global demo_module_start

    /* Define common external refrences.  */
    .global _txm_module_thread_shell_entry
    .global _txm_module_callback_request_thread_entry

__txm_module_preamble:
    .dc.l      0x4D4F4455                                       // Module ID
    .dc.l      0x6                                              // Module Major Version
    .dc.l      0x1                                              // Module Minor Version
    .dc.l      32                                               // Module Preamble Size in 32-bit words
    .dc.l      0x12345678                                       // Module ID (application defined)
    .dc.l      0x02000007                                       // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bits 23-3: Reserved
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
    .dc.l      _txm_module_thread_shell_entry - . - 0           // Module Shell Entry Point
    .dc.l      demo_module_start - . - 0                        // Module Start Thread Entry Point
    .dc.l      0                                                // Module Stop Thread Entry Point 
    .dc.l      1                                                // Module Start/Stop Thread Priority
    .dc.l      1024                                             // Module Start/Stop Thread Stack Size
    .dc.l      _txm_module_callback_request_thread_entry - . - 0 // Module Callback Thread Entry
    .dc.l      1                                                // Module Callback Thread Priority
    .dc.l      1024                                             // Module Callback Thread Stack Size
    .dc.l      __code_size__                                    // Module Code Size
    .dc.l      __data_size__                                    // Module Data Size
    .dc.l      0                                                // Reserved 0
    .dc.l      0                                                // Reserved 1
    .dc.l      0                                                // Reserved 2
    .dc.l      0                                                // Reserved 3
    .dc.l      0                                                // Reserved 4
    .dc.l      0                                                // Reserved 5
    .dc.l      0                                                // Reserved 6
    .dc.l      0                                                // Reserved 7
    .dc.l      0                                                // Reserved 8
    .dc.l      0                                                // Reserved 9
    .dc.l      0                                                // Reserved 10
    .dc.l      0                                                // Reserved 11
    .dc.l      0                                                // Reserved 12
    .dc.l      0                                                // Reserved 13
    .dc.l      0                                                // Reserved 14
    .dc.l      0                                                // Reserved 15

```

#### <a name="module-properties-for-cortex-m3-using-gnu"></a><span data-ttu-id="8fb80-298">Свойства модуля для Cortex-M3 с поддержкой GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-298">Module properties for Cortex-M3 using GNU</span></span>

| <span data-ttu-id="8fb80-299">bit</span><span class="sxs-lookup"><span data-stu-id="8fb80-299">Bit</span></span> | <span data-ttu-id="8fb80-300">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-300">Value</span></span> | <span data-ttu-id="8fb80-301">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-301">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="8fb80-302">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-302">0</span></span> | <span data-ttu-id="8fb80-303">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-303">0</span></span><br /><span data-ttu-id="8fb80-304">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-304">1</span></span> | <span data-ttu-id="8fb80-305">Выполнение в привилегированном режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-305">Privileged mode execution</span></span><br /><span data-ttu-id="8fb80-306">Выполнение в пользовательском режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-306">User mode execution</span></span> |
| <span data-ttu-id="8fb80-307">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-307">1</span></span> | <span data-ttu-id="8fb80-308">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-308">0</span></span><br /><span data-ttu-id="8fb80-309">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-309">1</span></span> | <span data-ttu-id="8fb80-310">Без защиты MPU.</span><span class="sxs-lookup"><span data-stu-id="8fb80-310">No MPU protection</span></span><br /><span data-ttu-id="8fb80-311">Защита MPU (необходимо выбрать пользовательский режим).</span><span class="sxs-lookup"><span data-stu-id="8fb80-311">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="8fb80-312">2</span><span class="sxs-lookup"><span data-stu-id="8fb80-312">2</span></span> | <span data-ttu-id="8fb80-313">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-313">0</span></span><br /><span data-ttu-id="8fb80-314">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-314">1</span></span> | <span data-ttu-id="8fb80-315">Отключение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-315">Disable shared/external memory access</span></span><br /><span data-ttu-id="8fb80-316">Включение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-316">Enable shared/external memory access</span></span> |
| <span data-ttu-id="8fb80-317">[23–3]</span><span class="sxs-lookup"><span data-stu-id="8fb80-317">[23-3]</span></span> | <span data-ttu-id="8fb80-318">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-318">0</span></span> | <span data-ttu-id="8fb80-319">Зарезервировано</span><span class="sxs-lookup"><span data-stu-id="8fb80-319">Reserved</span></span>
| <span data-ttu-id="8fb80-320">[31–24]</span><span class="sxs-lookup"><span data-stu-id="8fb80-320">[31-24]</span></span> | <br /><span data-ttu-id="8fb80-321">0x00</span><span class="sxs-lookup"><span data-stu-id="8fb80-321">0x00</span></span><br /><span data-ttu-id="8fb80-322">0x01</span><span class="sxs-lookup"><span data-stu-id="8fb80-322">0x01</span></span><br /><span data-ttu-id="8fb80-323">0x02</span><span class="sxs-lookup"><span data-stu-id="8fb80-323">0x02</span></span> | <span data-ttu-id="8fb80-324">**Идентификатор компилятора**</span><span class="sxs-lookup"><span data-stu-id="8fb80-324">**Compiler ID**</span></span><br /><span data-ttu-id="8fb80-325">IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-325">IAR</span></span><br /><span data-ttu-id="8fb80-326">ARM</span><span class="sxs-lookup"><span data-stu-id="8fb80-326">ARM</span></span><br /><span data-ttu-id="8fb80-327">GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-327">GNU</span></span> |

#### <a name="module-linker-for-cortex-m3-using-gnu"></a><span data-ttu-id="8fb80-328">Компоновщик модулей для Cortex-M3 с поддержкой GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-328">Module linker for Cortex-M3 using GNU</span></span>

```c
MEMORY
{
  FLASH (rx) : ORIGIN = 0x00030000, LENGTH = 0x00010000
  RAM   (wx) : ORIGIN = 0, LENGTH = 0x00100000
}


SECTIONS
{
  __FLASH_segment_start__ = 0x00030000;
  __FLASH_segment_end__   = 0x00040000;
  __RAM_segment_start__   = 0;
  __RAM_segment_end__     = 0x8000;

  __HEAPSIZE__ = 128;

  __preamble_load_start__ = __FLASH_segment_start__;
  .preamble __FLASH_segment_start__ : AT(__FLASH_segment_start__)
  {
    __preamble_start__ = .;
    *(.preamble .preamble.*)
  }
  __preamble_end__ = __preamble_start__ + SIZEOF(.preamble);

  __dynsym_load_start__ =  ALIGN(__preamble_end__ , 4);
  .dynsym ALIGN(__dynsym_load_start__ , 4) : AT(ALIGN(__dynsym_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynsym))
    KEEP (*(.dynsym*))
    . = ALIGN(4);
  }
  __dynsym_end__ = __dynsym_load_start__ + SIZEOF(.dynsym);

  __dynstr_load_start__ =  ALIGN(__dynsym_end__ , 4);
  .dynstr ALIGN(__dynstr_load_start__ , 4) : AT(ALIGN(__dynstr_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynstr))
    KEEP (*(.dynstr*))
    . = ALIGN(4);
  }
  __dynstr_end__ = __dynstr_load_start__ + SIZEOF(.dynstr);

  __reldyn_load_start__ =  ALIGN(__dynstr_end__ , 4);
  .rel.dyn ALIGN(__reldyn_load_start__ , 4) : AT(ALIGN(__reldyn_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.dyn))
    KEEP (*(.rel.dyn*))
    . = ALIGN(4);
  }
  __reldyn_end__ = __reldyn_load_start__ + SIZEOF(.rel.dyn);

  __relplt_load_start__ =  ALIGN(__reldyn_end__ , 4);
  .rel.plt ALIGN(__relplt_load_start__ , 4) : AT(ALIGN(__relplt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.plt))
    KEEP (*(.rel.plt*))
    . = ALIGN(4);
  }
  __relplt_end__ = __relplt_load_start__ + SIZEOF(.rel.plt);

  __plt_load_start__ =  ALIGN(__relplt_end__ , 4);
  .plt ALIGN(__plt_load_start__ , 4) : AT(ALIGN(__plt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.plt))
    KEEP (*(.plt*))
    . = ALIGN(4);
  }
  __plt_end__ = __plt_load_start__ + SIZEOF(.plt);

  __interp_load_start__ =  ALIGN(__plt_end__ , 4);
  .interp ALIGN(__interp_load_start__ , 4) : AT(ALIGN(__interp_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.interp))
    KEEP (*(.interp*))
    . = ALIGN(4);
  }
  __interp_end__ = __interp_load_start__ + SIZEOF(.interp);

  __hash_load_start__ =  ALIGN(__interp_end__ , 4);
  .hash ALIGN(__hash_load_start__ , 4) : AT(ALIGN(__hash_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.hash))
    KEEP (*(.hash*))
    . = ALIGN(4);
  }
  __hash_end__ = __hash_load_start__ + SIZEOF(.hash);

  __text_load_start__ =  ALIGN(__hash_end__ , 4);
  .text ALIGN(__text_load_start__ , 4) : AT(ALIGN(__text_load_start__, 4))
  {
    __text_start__ = .;
    *(.text .text.* .glue_7t .glue_7 .gnu.linkonce.t.* .gcc_except_table  )
  }
  __text_end__ = __text_start__ + SIZEOF(.text);

  __dtors_load_start__ = ALIGN(__text_end__ , 4);
  .dtors ALIGN(__text_end__ , 4) : AT(ALIGN(__text_end__ , 4))
  {
    __dtors_start__ = .;
    KEEP (*(SORT(.dtors.*))) KEEP (*(.dtors))
  }
  __dtors_end__ = __dtors_start__ + SIZEOF(.dtors);

  __ctors_load_start__ = ALIGN(__dtors_end__ , 4);
  .ctors ALIGN(__dtors_end__ , 4) : AT(ALIGN(__dtors_end__ , 4))
  {
    __ctors_start__ = .;
    KEEP (*(SORT(.ctors.*))) KEEP (*(.ctors))
  }
  __ctors_end__ = __ctors_start__ + SIZEOF(.ctors);

  __got_load_start__ = ALIGN(__ctors_end__ , 4);
  .got ALIGN(__ctors_end__ , 4) : AT(ALIGN(__ctors_end__ , 4))
  {
    . = ALIGN(4);
    _sgot = .;
    KEEP (*(.got))
    KEEP (*(.got*))
    . = ALIGN(4);
    _egot = .;
  } 
  __got_end__ =  __got_load_start__ + SIZEOF(.got);

  __rodata_load_start__ = ALIGN(__got_end__ , 4);
  .rodata ALIGN(__got_end__ , 4) : AT(ALIGN(__got_end__ , 4))
  {
    __rodata_start__ = .;
    *(.rodata .rodata.* .gnu.linkonce.r.*)
  }
  __rodata_end__ = __rodata_start__ + SIZEOF(.rodata);
 
  __code_size__ =  __rodata_end__ - __FLASH_segment_start__;

  __fast_load_start__ = ALIGN(__rodata_end__ , 4);

  __fast_load_end__ = __fast_load_start__ + SIZEOF(.fast);

  __new_got_start__ = ALIGN(__RAM_segment_start__ , 4);

  __new_got_end__ =  __new_got_start__ + SIZEOF(.got);

  .fast ALIGN(__new_got_end__ , 4) : AT(ALIGN(__rodata_end__ , 4))
  {
    __fast_start__ = .;
    *(.fast .fast.*)
  }
  __fast_end__ = __fast_start__ + SIZEOF(.fast);

  .fast_run ALIGN(__fast_end__ , 4) (NOLOAD) :
  {
    __fast_run_start__ = .;
    . = MAX(__fast_run_start__ + SIZEOF(.fast), .);
  }
  __fast_run_end__ = __fast_run_start__ + SIZEOF(.fast_run);

  __data_load_start__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4);
  .data ALIGN(__fast_run_end__ , 4) : AT(ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4))
  {
    __data_start__ = .;
    *(.data .data.* .gnu.linkonce.d.*)
  }
  __data_end__ = __data_start__ + SIZEOF(.data);

  __data_load_end__ = __data_load_start__ + SIZEOF(.data);

  __FLASH_segment_used_end__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4) + SIZEOF(.data);

  .data_run ALIGN(__fast_run_end__ , 4) (NOLOAD) :
  {
    __data_run_start__ = .;
    . = MAX(__data_run_start__ + SIZEOF(.data), .);
  }
  __data_run_end__ = __data_run_start__ + SIZEOF(.data_run);

  __bss_load_start__ = ALIGN(__data_run_end__ , 4);
  .bss ALIGN(__data_run_end__ , 4) (NOLOAD) : AT(ALIGN(__data_run_end__ , 4))
  {
    __bss_start__ = .;
    *(.bss .bss.* .gnu.linkonce.b.*) *(COMMON)
  }
  __bss_end__ = __bss_start__ + SIZEOF(.bss);

  __non_init_load_start__ = ALIGN(__bss_end__ , 4);
  .non_init ALIGN(__bss_end__ , 4) (NOLOAD) : AT(ALIGN(__bss_end__ , 4))
  {
    __non_init_start__ = .;
    *(.non_init .non_init.*)
  }
  __non_init_end__ = __non_init_start__ + SIZEOF(.non_init);

  __heap_load_start__ = ALIGN(__non_init_end__ , 4);
  .heap ALIGN(__non_init_end__ , 4) (NOLOAD) : AT(ALIGN(__non_init_end__ , 4))
  {
    __heap_start__ = .;
    *(.heap)
    . = ALIGN(MAX(__heap_start__ + __HEAPSIZE__ , .), 4);
  }
  __heap_end__ = __heap_start__ + SIZEOF(.heap);

  __data_size__ =  __heap_end__ - __RAM_segment_start__;

}
```

#### <a name="building-modules-for-cortex-m3-using-gnu"></a><span data-ttu-id="8fb80-329">Создание модулей для Cortex-M3 с поддержкой GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-329">Building Modules for Cortex-M3 using GNU</span></span>

<span data-ttu-id="8fb80-330">Ознакомьтесь с файлом build_threadx_module_sample.bat.</span><span class="sxs-lookup"><span data-stu-id="8fb80-330">See build_threadx_module_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base txm_module_preamble.s
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base gcc_setup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module.c
arm-none-eabi-ld -A cortex-m3 -T sample_threadx_module.ld txm_module_preamble.o gcc_setup.o sample_threadx_module.o -e _txm_module_thread_shell_entry txm.a -o sample_threadx_module.axf -M > sample_threadx_module.map
```

#### <a name="thread-extension-definition-for-cortex-m3-using-gnu"></a><span data-ttu-id="8fb80-331">Определение расширения потоков для Cortex-M3 с поддержкой GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-331">Thread extension definition for Cortex-M3 using GNU</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m3-using-gnu"></a><span data-ttu-id="8fb80-332">Создание диспетчера модулей для Cortex-M3 с поддержкой GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-332">Building Module Manager for Cortex-M3 using GNU</span></span>

<span data-ttu-id="8fb80-333">Ознакомьтесь с файлом build_threadx_module_manager_sample.bat.</span><span class="sxs-lookup"><span data-stu-id="8fb80-333">See build_threadx_module_manager_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -mthumb -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module_manager.c
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -mthumb tx_simulator_startup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -mthumb cortexm_crt0.S
arm-none-eabi-ld -A cortex-m3 -ereset_handler -T sample_threadx.ld tx_simulator_startup.o cortexm_crt0.o sample_threadx_module_manager.o tx.a  libc.a -o sample_threadx_module_manager.axf -M > sample_threadx_module_manager.map
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m3-using-gnu"></a><span data-ttu-id="8fb80-334">Атрибуты API включения внешней памяти для Cortex-M3 с поддержкой GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-334">Attributes for external memory enable API for Cortex-M3 using GNU</span></span>

<span data-ttu-id="8fb80-335">Модуль всегда имеет доступ на чтение к общей памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-335">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="8fb80-336">Параметр атрибута</span><span class="sxs-lookup"><span data-stu-id="8fb80-336">Attribute parameter</span></span> | <span data-ttu-id="8fb80-337">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-337">Meaning</span></span> |
|---|---|
| <span data-ttu-id="8fb80-338">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="8fb80-338">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="8fb80-339">Доступ для записи.</span><span class="sxs-lookup"><span data-stu-id="8fb80-339">Write access</span></span> |

### <a name="cortex-m3-using-iar"></a><span data-ttu-id="8fb80-340">Cortex-M3 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-340">Cortex-M3 using IAR</span></span>

#### <a name="module-preamble-for-cortex-m3-using-iar"></a><span data-ttu-id="8fb80-341">Начальная часть модуля для Cortex-M3 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-341">Module preamble for Cortex-M3 using IAR</span></span>

```c
    SECTION .text:CODE

    AAPCS INTERWORK, ROPI, RWPI_COMPATIBLE,  VFP_COMPATIBLE
    PRESERVE8

    /* Define public symbols.  */

    PUBLIC __txm_module_preamble


    /* Define application-specific start/stop entry points for the module.  */

    EXTERN demo_module_start


    /* Define common external references.  */

    EXTERN  _txm_module_thread_shell_entry
    EXTERN  _txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        ; Module ID
    DC32      0x5                                               ; Module Major Version
    DC32      0x6                                               ; Module Minor Version
    DC32      32                                                ; Module Preamble Size in 32-bit words
    DC32      0x12345678                                        ; Module ID (application defined)
    DC32      0x00000007                                        ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bits 23-3: Reserved
                                                                ;   Bit 2:  0 -> Disable shared/external memory access
                                                                ;           1 -> Enable shared/external memory access
                                                                ;   Bit 1:  0 -> No MPU protection
                                                                ;           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                ;   Bit 0:  0 -> Privileged mode execution
                                                                ;           1 -> User mode execution


    DC32      _txm_module_thread_shell_entry - . - 0            ; Module Shell Entry Point
    DC32      demo_module_start - . - 0                         ; Module Start Thread Entry Point
    DC32      0                                                 ; Module Stop Thread Entry Point
    DC32      1                                                 ; Module Start/Stop Thread Priority
    DC32      1024                                              ; Module Start/Stop Thread Stack Size
    DC32      _txm_module_callback_request_thread_entry - . - 0 ; Module Callback Thread Entry
    DC32      1                                                 ; Module Callback Thread Priority
    DC32      1024                                              ; Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      ; Module Code Size
    DC32      RWPI$$Length                                      ; Module Data Size
    DC32      0                                                 ; Reserved 0
    DC32      0                                                 ; Reserved 1
    DC32      0                                                 ; Reserved 2
    DC32      0                                                 ; Reserved 3
    DC32      0                                                 ; Reserved 4
    DC32      0                                                 ; Reserved 5
    DC32      0                                                 ; Reserved 6
    DC32      0                                                 ; Reserved 7
    DC32      0                                                 ; Reserved 8  
    DC32      0                                                 ; Reserved 9
    DC32      0                                                 ; Reserved 10
    DC32      0                                                 ; Reserved 11
    DC32      0                                                 ; Reserved 12
    DC32      0                                                 ; Reserved 13
    DC32      0                                                 ; Reserved 14
    DC32      0                                                 ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-m3-using-iar"></a><span data-ttu-id="8fb80-342">Свойства модуля для Cortex-M3 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-342">Module properties for Cortex-M3 using IAR</span></span>

| <span data-ttu-id="8fb80-343">bit</span><span class="sxs-lookup"><span data-stu-id="8fb80-343">Bit</span></span> | <span data-ttu-id="8fb80-344">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-344">Value</span></span> | <span data-ttu-id="8fb80-345">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-345">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="8fb80-346">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-346">0</span></span> | <span data-ttu-id="8fb80-347">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-347">0</span></span><br /><span data-ttu-id="8fb80-348">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-348">1</span></span> | <span data-ttu-id="8fb80-349">Выполнение в привилегированном режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-349">Privileged mode execution</span></span><br /><span data-ttu-id="8fb80-350">Выполнение в пользовательском режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-350">User mode execution</span></span> |
| <span data-ttu-id="8fb80-351">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-351">1</span></span> | <span data-ttu-id="8fb80-352">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-352">0</span></span><br /><span data-ttu-id="8fb80-353">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-353">1</span></span> | <span data-ttu-id="8fb80-354">Без защиты MPU.</span><span class="sxs-lookup"><span data-stu-id="8fb80-354">No MPU protection</span></span><br /><span data-ttu-id="8fb80-355">Защита MPU (необходимо выбрать пользовательский режим).</span><span class="sxs-lookup"><span data-stu-id="8fb80-355">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="8fb80-356">2</span><span class="sxs-lookup"><span data-stu-id="8fb80-356">2</span></span> | <span data-ttu-id="8fb80-357">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-357">0</span></span><br /><span data-ttu-id="8fb80-358">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-358">1</span></span> | <span data-ttu-id="8fb80-359">Отключение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-359">Disable shared/external memory access</span></span><br /><span data-ttu-id="8fb80-360">Включение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-360">Enable shared/external memory access</span></span> |
| <span data-ttu-id="8fb80-361">[23–3]</span><span class="sxs-lookup"><span data-stu-id="8fb80-361">[23-3]</span></span> | <span data-ttu-id="8fb80-362">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-362">0</span></span> | <span data-ttu-id="8fb80-363">Зарезервировано</span><span class="sxs-lookup"><span data-stu-id="8fb80-363">Reserved</span></span>
| <span data-ttu-id="8fb80-364">[31–24]</span><span class="sxs-lookup"><span data-stu-id="8fb80-364">[31-24]</span></span> | <br /><span data-ttu-id="8fb80-365">0x00</span><span class="sxs-lookup"><span data-stu-id="8fb80-365">0x00</span></span><br /><span data-ttu-id="8fb80-366">0x01</span><span class="sxs-lookup"><span data-stu-id="8fb80-366">0x01</span></span><br /><span data-ttu-id="8fb80-367">0x02</span><span class="sxs-lookup"><span data-stu-id="8fb80-367">0x02</span></span> | <span data-ttu-id="8fb80-368">**Идентификатор компилятора**</span><span class="sxs-lookup"><span data-stu-id="8fb80-368">**Compiler ID**</span></span><br /><span data-ttu-id="8fb80-369">IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-369">IAR</span></span><br /><span data-ttu-id="8fb80-370">ARM</span><span class="sxs-lookup"><span data-stu-id="8fb80-370">ARM</span></span><br /><span data-ttu-id="8fb80-371">GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-371">GNU</span></span> |

#### <a name="module-linker-for-cortex-m3-using-iar"></a><span data-ttu-id="8fb80-372">Компоновщик модулей для Cortex-M3 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-372">Module linker for Cortex-M3 using IAR</span></span>

```c
/*###ICF### Section handled by ICF editor, don't touch! ****/
/*-Editor annotation file-*/
/* IcfEditorFile="$TOOLKIT_DIR$\config\ide\IcfEditor\a_v1_0.xml" */
/*-Specials-*/
define symbol __ICFEDIT_intvec_start__ = 0x0;
/*-Memory Regions-*/
define symbol __ICFEDIT_region_ROM_start__ = 0x080f0000;
define symbol __ICFEDIT_region_ROM_end__   = 0x080fffff;
define symbol __ICFEDIT_region_RAM_start__ = 0x64002800;
define symbol __ICFEDIT_region_RAM_end__   = 0x64100000;
/*-Sizes-*/
define symbol __ICFEDIT_size_cstack__   = 0;
define symbol __ICFEDIT_size_svcstack__ = 0;
define symbol __ICFEDIT_size_irqstack__ = 0;
define symbol __ICFEDIT_size_fiqstack__ = 0;
define symbol __ICFEDIT_size_undstack__ = 0;
define symbol __ICFEDIT_size_abtstack__ = 0;
define symbol __ICFEDIT_size_heap__     = 0x1000;
/**** End of ICF editor section. ###ICF###*/

define memory mem with size = 4G;
define region ROM_region   = mem:[from __ICFEDIT_region_ROM_start__   to __ICFEDIT_region_ROM_end__];
define region RAM_region   = mem:[from __ICFEDIT_region_RAM_start__   to __ICFEDIT_region_RAM_end__];

//define block CSTACK    with alignment = 8, size = __ICFEDIT_size_cstack__   { };
//define block SVC_STACK with alignment = 8, size = __ICFEDIT_size_svcstack__ { };
//define block IRQ_STACK with alignment = 8, size = __ICFEDIT_size_irqstack__ { };
//define block FIQ_STACK with alignment = 8, size = __ICFEDIT_size_fiqstack__ { };
//define block UND_STACK with alignment = 8, size = __ICFEDIT_size_undstack__ { };
//define block ABT_STACK with alignment = 8, size = __ICFEDIT_size_abtstack__ { };
define block HEAP      with alignment = 8, size = __ICFEDIT_size_heap__     { };

initialize by copy { readwrite };
do not initialize  { section .noinit };

//place at address mem:__ICFEDIT_intvec_start__ { readonly section .intvec };

define movable block ROPI with alignment = 4, fixed order
{
  ro object txm_module_preamble_stm32f2xx.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base
{
  rw,
  block HEAP
};

place in ROM_region   { block ROPI };
place in RAM_region   { block RWPI };
```

#### <a name="building-modules-for-cortex-m3-using-iar"></a><span data-ttu-id="8fb80-373">Создание модулей для Cortex-M3 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-373">Building Modules for Cortex-M3 using IAR</span></span>

<span data-ttu-id="8fb80-374">Предоставлен пример рабочей области.</span><span class="sxs-lookup"><span data-stu-id="8fb80-374">An example workspace is provided.</span></span> <span data-ttu-id="8fb80-375">Можно создать библиотеку ThreadX, библиотеку модулей ThreadX, проект демонстрационного модуля и проект демонстрационного диспетчера модулей.</span><span class="sxs-lookup"><span data-stu-id="8fb80-375">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m3-using-iar"></a><span data-ttu-id="8fb80-376">Определение расширения потоков для Cortex-M3 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-376">Thread extension definition for Cortex-M3 using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                ULONG   tx_thread_module_saved_lr;              \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;             \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-cortex-m3-using-iar"></a><span data-ttu-id="8fb80-377">Создание диспетчера модулей для Cortex-M3 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-377">Building Module Manager for Cortex-M3 using IAR</span></span>

<span data-ttu-id="8fb80-378">Предоставлен пример рабочей области.</span><span class="sxs-lookup"><span data-stu-id="8fb80-378">An example workspace is provided.</span></span> <span data-ttu-id="8fb80-379">Можно создать библиотеку ThreadX, библиотеку модулей ThreadX, проект демонстрационного модуля и проект демонстрационного диспетчера модулей.</span><span class="sxs-lookup"><span data-stu-id="8fb80-379">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m3-using-iar"></a><span data-ttu-id="8fb80-380">Атрибуты API включения внешней памяти для Cortex-M3 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-380">Attributes for external memory enable API for Cortex-M3 using IAR</span></span>

<span data-ttu-id="8fb80-381">Модуль всегда имеет доступ на чтение к общей памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-381">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="8fb80-382">Параметр атрибута</span><span class="sxs-lookup"><span data-stu-id="8fb80-382">Attribute parameter</span></span> | <span data-ttu-id="8fb80-383">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-383">Meaning</span></span> |
|---|---|
| <span data-ttu-id="8fb80-384">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="8fb80-384">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="8fb80-385">Доступ для записи.</span><span class="sxs-lookup"><span data-stu-id="8fb80-385">Write access</span></span> |

## <a name="cortex-m33-processor"></a><span data-ttu-id="8fb80-386">Процессор Cortex-M33</span><span class="sxs-lookup"><span data-stu-id="8fb80-386">Cortex-M33 processor</span></span>

### <a name="cortex-m33-using-ac6"></a><span data-ttu-id="8fb80-387">Cortex-M33 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-387">Cortex-M33 using AC6</span></span>

#### <a name="module-preamble-for-cortex-m33-using-ac6"></a><span data-ttu-id="8fb80-388">Начальная часть модуля для Cortex-M33 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-388">Module preamble for Cortex-M33 using AC6</span></span>

```c
    .text
    .align 4
    .syntax unified
    .section RESET
    
    // Define public symbols
    .global __txm_module_preamble

    // Define application-specific start/stop entry points for the module
    .global demo_module_start

    // Define common external references
    .global  _txm_module_thread_shell_entry
    .global  _txm_module_callback_request_thread_entry

    .eabi_attribute Tag_ABI_PCS_RO_data, 1
    .eabi_attribute Tag_ABI_PCS_R9_use,  1
    .eabi_attribute Tag_ABI_PCS_RW_data, 2

__txm_module_preamble:
    .dc.l   0x4D4F4455                                          // Module ID
    .dc.l   0x6                                                 // Module Major Version
    .dc.l   0x1                                                 // Module Minor Version
    .dc.l   32                                                  // Module Preamble Size in 32-bit words
    .dc.l   0x12345678                                          // Module ID (application defined)
    .dc.l   0x01000007                                          // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
    .dc.l   _txm_module_thread_shell_entry - __txm_module_preamble // Module Shell Entry Point
    .dc.l   demo_module_start - __txm_module_preamble           // Module Start Thread Entry Point
    .dc.l   0                                                   // Module Stop Thread Entry Point
    .dc.l   1                                                   // Module Start/Stop Thread Priority
    .dc.l   1024                                                // Module Start/Stop Thread Stack Size
    .dc.l   _txm_module_callback_request_thread_entry - __txm_module_preamble // Module Callback Thread Entry
    .dc.l   1                                                   // Module Callback Thread Priority
    .dc.l   1024                                                // Module Callback Thread Stack Size
    //the tools can't add two symbols together, but it should look like this:
    //.dc.l   Image$$ER_RO$$Length + Image$$ER_RW$$Length         // Module Code Size
    //.dc.l   Image$$ER_RW$$Length + Image$$ER_ZI$$ZI$$Length     // Module Data Size
    //so instead we'll define hard values:
    .dc.l   0x4000                                              // Module Code Size
    .dc.l   0x4000                                              // Module Data Size
    .dc.l   0                                                   // Reserved 0
    .dc.l   0                                                   // Reserved 1
    .dc.l   0                                                   // Reserved 2
    .dc.l   0                                                   // Reserved 3
    .dc.l   0                                                   // Reserved 4
    .dc.l   0                                                   // Reserved 5
    .dc.l   0                                                   // Reserved 6
    .dc.l   0                                                   // Reserved 7
    .dc.l   0                                                   // Reserved 8
    .dc.l   0                                                   // Reserved 9
    .dc.l   0                                                   // Reserved 10
    .dc.l   0                                                   // Reserved 11
    .dc.l   0                                                   // Reserved 12
    .dc.l   0                                                   // Reserved 13
    .dc.l   0                                                   // Reserved 14
    .dc.l   0                                                   // Reserved 15
```

#### <a name="module-properties-for-cortex-m33-using-ac6"></a><span data-ttu-id="8fb80-389">Свойства модуля для Cortex-M33 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-389">Module properties for Cortex-M33 using AC6</span></span>

| <span data-ttu-id="8fb80-390">bit</span><span class="sxs-lookup"><span data-stu-id="8fb80-390">Bit</span></span> | <span data-ttu-id="8fb80-391">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-391">Value</span></span> | <span data-ttu-id="8fb80-392">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-392">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="8fb80-393">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-393">0</span></span> | <span data-ttu-id="8fb80-394">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-394">0</span></span><br /><span data-ttu-id="8fb80-395">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-395">1</span></span> | <span data-ttu-id="8fb80-396">Выполнение в привилегированном режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-396">Privileged mode execution</span></span><br /><span data-ttu-id="8fb80-397">Выполнение в пользовательском режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-397">User mode execution</span></span> |
| <span data-ttu-id="8fb80-398">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-398">1</span></span> | <span data-ttu-id="8fb80-399">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-399">0</span></span><br /><span data-ttu-id="8fb80-400">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-400">1</span></span> | <span data-ttu-id="8fb80-401">Без защиты MPU.</span><span class="sxs-lookup"><span data-stu-id="8fb80-401">No MPU protection</span></span><br /><span data-ttu-id="8fb80-402">Защита MPU (необходимо выбрать пользовательский режим).</span><span class="sxs-lookup"><span data-stu-id="8fb80-402">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="8fb80-403">2</span><span class="sxs-lookup"><span data-stu-id="8fb80-403">2</span></span> | <span data-ttu-id="8fb80-404">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-404">0</span></span><br /><span data-ttu-id="8fb80-405">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-405">1</span></span> | <span data-ttu-id="8fb80-406">Отключение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-406">Disable shared/external memory access</span></span><br /><span data-ttu-id="8fb80-407">Включение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-407">Enable shared/external memory access</span></span> |
| <span data-ttu-id="8fb80-408">[23–3]</span><span class="sxs-lookup"><span data-stu-id="8fb80-408">[23-3]</span></span> | <span data-ttu-id="8fb80-409">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-409">0</span></span> | <span data-ttu-id="8fb80-410">Зарезервировано</span><span class="sxs-lookup"><span data-stu-id="8fb80-410">Reserved</span></span>
| <span data-ttu-id="8fb80-411">[31–24]</span><span class="sxs-lookup"><span data-stu-id="8fb80-411">[31-24]</span></span> | <br /><span data-ttu-id="8fb80-412">0x00</span><span class="sxs-lookup"><span data-stu-id="8fb80-412">0x00</span></span><br /><span data-ttu-id="8fb80-413">0x01</span><span class="sxs-lookup"><span data-stu-id="8fb80-413">0x01</span></span><br /><span data-ttu-id="8fb80-414">0x02</span><span class="sxs-lookup"><span data-stu-id="8fb80-414">0x02</span></span> | <span data-ttu-id="8fb80-415">**Идентификатор компилятора**</span><span class="sxs-lookup"><span data-stu-id="8fb80-415">**Compiler ID**</span></span><br /><span data-ttu-id="8fb80-416">IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-416">IAR</span></span><br /><span data-ttu-id="8fb80-417">ARM</span><span class="sxs-lookup"><span data-stu-id="8fb80-417">ARM</span></span><br /><span data-ttu-id="8fb80-418">GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-418">GNU</span></span> |

#### <a name="module-linker-for-cortex-m33-using-ac6"></a><span data-ttu-id="8fb80-419">Компоновщик модулей для Cortex-M33 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-419">Module linker for Cortex-M33 using AC6</span></span>

<span data-ttu-id="8fb80-420">Файл компоновщика для цепочки инструментов Keil не требуется.</span><span class="sxs-lookup"><span data-stu-id="8fb80-420">No linker file needed for Keil toolchain.</span></span> <span data-ttu-id="8fb80-421">Ознакомьтесь с параметрами сборки в примере проекта.</span><span class="sxs-lookup"><span data-stu-id="8fb80-421">See build settings in example project.</span></span>
<span data-ttu-id="8fb80-422">Ниже перечислены важные параметры компоновщика.</span><span class="sxs-lookup"><span data-stu-id="8fb80-422">Important linker options are listed below:</span></span>

```c
--entry demo_module_start --first __txm_module_preamble
```

#### <a name="building-modules-for-cortex-m33-using-ac6"></a><span data-ttu-id="8fb80-423">Создание модулей для Cortex-M33 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-423">Building Modules for Cortex-M33 using AC6</span></span>

<span data-ttu-id="8fb80-424">Параметры компилятора.</span><span class="sxs-lookup"><span data-stu-id="8fb80-424">Compiler settings:</span></span>

```c
-xc -std=c99 --target=arm-arm-none-eabi -mcpu=cortex-m33 -mfpu=fpv5-sp-d16 -mfloat-abi=hard -c
-fno-rtti -funsigned-char -fshort-enums -fshort-wchar
-mlittle-endian -gdwarf-3 -fropi -frwpi -O1 -ffunction-sections -Wno-packed -Wno-missing-variable-declarations -Wno-missing-prototypes -Wno-missing-noreturn -Wno-sign-conversion -Wno-nonportable-include-path -Wno-reserved-id-macro -Wno-unused-macros -Wno-documentation-unknown-command -Wno-documentation -Wno-license-management -Wno-parentheses-equality -I ../../../../../common_modules/inc -I ../../../../../common/inc -I ../../../../../ports_module/cortex_m33/ac6/inc -I ../demo_secure_zone
-I./RTE/_FVP_Simulation_Model
-IC:/Users/your_path/AppData/Local/Arm/Packs/ARM/CMSIS/5.5.1/CMSIS/Core/Include
-IC:/Users/your_path/AppData/Local/Arm/Packs/ARM/CMSIS/5.5.1/Device/ARM/ARMCM33/Include
-D__UVISION_VERSION="531" -D_RTE_ -DARMCM33_DSP_FP_TZ -D_RTE_
-o ./Objects/*.o -MD
```

#### <a name="thread-extension-definition-for-cortex-m33-using-ac6"></a><span data-ttu-id="8fb80-425">Определение расширения потоков для Cortex-M33 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-425">Thread extension definition for Cortex-M33 using AC6</span></span>

```c
#define TX_THREAD_EXTENSION_2                   VOID    *tx_thread_module_instance_ptr;         \
                                                VOID    *tx_thread_module_entry_info_ptr;       \
                                                ULONG   tx_thread_module_current_user_mode;     \
                                                ULONG   tx_thread_module_user_mode;             \
                                                ULONG   tx_thread_module_saved_lr;              \
                                                VOID    *tx_thread_module_kernel_stack_start;   \
                                                VOID    *tx_thread_module_kernel_stack_end;     \
                                                ULONG   tx_thread_module_kernel_stack_size;     \
                                                VOID    *tx_thread_module_stack_ptr;            \
                                                VOID    *tx_thread_module_stack_start;          \
                                                VOID    *tx_thread_module_stack_end;            \
                                                ULONG   tx_thread_module_stack_size;            \
                                                VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m33-using-ac6"></a><span data-ttu-id="8fb80-426">Создание диспетчера модулей для Cortex-M33 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-426">Building Module Manager for Cortex-M33 using AC6</span></span>

<span data-ttu-id="8fb80-427">Предоставлен пример рабочей области.</span><span class="sxs-lookup"><span data-stu-id="8fb80-427">An example workspace is provided.</span></span> <span data-ttu-id="8fb80-428">Можно создать библиотеку ThreadX, библиотеку модулей ThreadX, проектsample_threadx_module и проект demo_threadx_non-secure_zone.</span><span class="sxs-lookup"><span data-stu-id="8fb80-428">Build the ThreadX library, ThreadX Modules library, sample_threadx_module project, and demo_threadx_non-secure_zone project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m33-using-ac6"></a><span data-ttu-id="8fb80-429">Атрибуты API включения внешней памяти для Cortex-M33 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-429">Attributes for external memory enable API for Cortex-M33 using AC6</span></span>

| <span data-ttu-id="8fb80-430">Параметр атрибута</span><span class="sxs-lookup"><span data-stu-id="8fb80-430">Attribute parameter</span></span> |
|---|
| <span data-ttu-id="8fb80-431">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="8fb80-431">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span></span> |
| <span data-ttu-id="8fb80-432">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="8fb80-432">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span></span> |
| <span data-ttu-id="8fb80-433">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="8fb80-433">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span></span> |
| <span data-ttu-id="8fb80-434">TXM_MODULE_ATTRIBUTE_READ_WRITE</span><span class="sxs-lookup"><span data-stu-id="8fb80-434">TXM_MODULE_ATTRIBUTE_READ_WRITE</span></span> |
| <span data-ttu-id="8fb80-435">TXM_MODULE_ATTRIBUTE_READ_ONLY</span><span class="sxs-lookup"><span data-stu-id="8fb80-435">TXM_MODULE_ATTRIBUTE_READ_ONLY</span></span> |

### <a name="cortex-m33-using-gnu"></a><span data-ttu-id="8fb80-436">Cortex-M33 с поддержкой GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-436">Cortex-M33 using GNU</span></span>

#### <a name="module-preamble-for-cortex-m33-using-gnu"></a><span data-ttu-id="8fb80-437">Начальная часть модуля для Cortex-M33 с поддержкой GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-437">Module preamble for Cortex-M33 using GNU</span></span>

#### <a name="module-properties-for-cortex-m33-using-gnu"></a><span data-ttu-id="8fb80-438">Свойства модуля для Cortex-M33 с поддержкой GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-438">Module properties for Cortex-M33 using GNU</span></span>

| <span data-ttu-id="8fb80-439">bit</span><span class="sxs-lookup"><span data-stu-id="8fb80-439">Bit</span></span> | <span data-ttu-id="8fb80-440">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-440">Value</span></span> | <span data-ttu-id="8fb80-441">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-441">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="8fb80-442">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-442">0</span></span> | <span data-ttu-id="8fb80-443">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-443">0</span></span><br /><span data-ttu-id="8fb80-444">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-444">1</span></span> | <span data-ttu-id="8fb80-445">Выполнение в привилегированном режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-445">Privileged mode execution</span></span><br /><span data-ttu-id="8fb80-446">Выполнение в пользовательском режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-446">User mode execution</span></span> |
| <span data-ttu-id="8fb80-447">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-447">1</span></span> | <span data-ttu-id="8fb80-448">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-448">0</span></span><br /><span data-ttu-id="8fb80-449">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-449">1</span></span> | <span data-ttu-id="8fb80-450">Без защиты MPU.</span><span class="sxs-lookup"><span data-stu-id="8fb80-450">No MPU protection</span></span><br /><span data-ttu-id="8fb80-451">Защита MPU (необходимо выбрать пользовательский режим).</span><span class="sxs-lookup"><span data-stu-id="8fb80-451">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="8fb80-452">2</span><span class="sxs-lookup"><span data-stu-id="8fb80-452">2</span></span> | <span data-ttu-id="8fb80-453">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-453">0</span></span><br /><span data-ttu-id="8fb80-454">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-454">1</span></span> | <span data-ttu-id="8fb80-455">Отключение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-455">Disable shared/external memory access</span></span><br /><span data-ttu-id="8fb80-456">Включение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-456">Enable shared/external memory access</span></span> |
| <span data-ttu-id="8fb80-457">[23–3]</span><span class="sxs-lookup"><span data-stu-id="8fb80-457">[23-3]</span></span> | <span data-ttu-id="8fb80-458">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-458">0</span></span> | <span data-ttu-id="8fb80-459">Зарезервировано</span><span class="sxs-lookup"><span data-stu-id="8fb80-459">Reserved</span></span>
| <span data-ttu-id="8fb80-460">[31–24]</span><span class="sxs-lookup"><span data-stu-id="8fb80-460">[31-24]</span></span> | <br /><span data-ttu-id="8fb80-461">0x00</span><span class="sxs-lookup"><span data-stu-id="8fb80-461">0x00</span></span><br /><span data-ttu-id="8fb80-462">0x01</span><span class="sxs-lookup"><span data-stu-id="8fb80-462">0x01</span></span><br /><span data-ttu-id="8fb80-463">0x02</span><span class="sxs-lookup"><span data-stu-id="8fb80-463">0x02</span></span> | <span data-ttu-id="8fb80-464">**Идентификатор компилятора**</span><span class="sxs-lookup"><span data-stu-id="8fb80-464">**Compiler ID**</span></span><br /><span data-ttu-id="8fb80-465">IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-465">IAR</span></span><br /><span data-ttu-id="8fb80-466">ARM</span><span class="sxs-lookup"><span data-stu-id="8fb80-466">ARM</span></span><br /><span data-ttu-id="8fb80-467">GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-467">GNU</span></span> |

#### <a name="module-linker-for-cortex-m33-using-gnu"></a><span data-ttu-id="8fb80-468">Компоновщик модулей для Cortex-M33 с поддержкой GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-468">Module linker for Cortex-M33 using GNU</span></span>

#### <a name="building-modules-for-cortex-m33-using-gnu"></a><span data-ttu-id="8fb80-469">Создание модулей для Cortex-M33 с поддержкой GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-469">Building Modules for Cortex-M33 using GNU</span></span>

#### <a name="thread-extension-definition-for-cortex-m33-using-gnu"></a><span data-ttu-id="8fb80-470">Определение расширения потоков для Cortex-M33 с поддержкой GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-470">Thread extension definition for Cortex-M33 using GNU</span></span>

#### <a name="building-module-manager-for-cortex-m33-using-gnu"></a><span data-ttu-id="8fb80-471">Создание диспетчера модулей для Cortex-M33 с поддержкой GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-471">Building Module Manager for Cortex-M33 using GNU</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m33-using-gnu"></a><span data-ttu-id="8fb80-472">Атрибуты API включения внешней памяти для Cortex-M33 с поддержкой GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-472">Attributes for external memory enable API for Cortex-M33 using GNU</span></span>

| <span data-ttu-id="8fb80-473">Параметр атрибута</span><span class="sxs-lookup"><span data-stu-id="8fb80-473">Attribute parameter</span></span> |
|---|
| <span data-ttu-id="8fb80-474">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="8fb80-474">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span></span> |
| <span data-ttu-id="8fb80-475">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="8fb80-475">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span></span> |
| <span data-ttu-id="8fb80-476">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="8fb80-476">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span></span> |
| <span data-ttu-id="8fb80-477">TXM_MODULE_ATTRIBUTE_READ_WRITE</span><span class="sxs-lookup"><span data-stu-id="8fb80-477">TXM_MODULE_ATTRIBUTE_READ_WRITE</span></span> |
| <span data-ttu-id="8fb80-478">TXM_MODULE_ATTRIBUTE_READ_ONLY</span><span class="sxs-lookup"><span data-stu-id="8fb80-478">TXM_MODULE_ATTRIBUTE_READ_ONLY</span></span> |

### <a name="cortex-m33-using-iar"></a><span data-ttu-id="8fb80-479">Cortex-M33 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-479">Cortex-M33 using IAR</span></span>

#### <a name="module-preamble-for-cortex-m33-using-iar"></a><span data-ttu-id="8fb80-480">Начальная часть модуля для Cortex-M33 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-480">Module preamble for Cortex-M33 using IAR</span></span>

```c
    SECTION .text:CODE

    AAPCS INTERWORK, ROPI, RWPI_COMPATIBLE,  VFP_COMPATIBLE
    PRESERVE8

    /* Define public symbols.  */

    PUBLIC __txm_module_preamble


    /* Define application-specific start/stop entry points for the module.  */

    EXTERN demo_module_start


    /* Define common external refrences.  */

    EXTERN  _txm_module_thread_shell_entry
    EXTERN  _txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        // Module ID
    DC32      0x6                                               // Module Major Version
    DC32      0x1                                               // Module Minor Version
    DC32      32                                                // Module Preamble Size in 32-bit words
    DC32      0x12345678                                        // Module ID (application defined)
    DC32      0x00000007                                        // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bits 23-3: Reserved
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
    DC32      _txm_module_thread_shell_entry - . - 0            // Module Shell Entry Point
    DC32      demo_module_start - . - 0                         // Module Start Thread Entry Point
    DC32      0                                                 // Module Stop Thread Entry Point
    DC32      1                                                 // Module Start/Stop Thread Priority
    DC32      1024                                              // Module Start/Stop Thread Stack Size
    DC32      _txm_module_callback_request_thread_entry - . - 0 // Module Callback Thread Entry
    DC32      1                                                 // Module Callback Thread Priority
    DC32      1024                                              // Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      // Module Code Size
    DC32      RWPI$$Length                                      // Module Data Size
    DC32      0                                                 // Reserved 0
    DC32      0                                                 // Reserved 1
    DC32      0                                                 // Reserved 2
    DC32      0                                                 // Reserved 3
    DC32      0                                                 // Reserved 4
    DC32      0                                                 // Reserved 5
    DC32      0                                                 // Reserved 6
    DC32      0                                                 // Reserved 7
    DC32      0                                                 // Reserved 8
    DC32      0                                                 // Reserved 9
    DC32      0                                                 // Reserved 10
    DC32      0                                                 // Reserved 11
    DC32      0                                                 // Reserved 12
    DC32      0                                                 // Reserved 13
    DC32      0                                                 // Reserved 14
    DC32      0                                                 // Reserved 15

    END

```

#### <a name="module-properties-for-cortex-m33-using-iar"></a><span data-ttu-id="8fb80-481">Свойства модуля для Cortex-M33 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-481">Module properties for Cortex-M33 using IAR</span></span>

| <span data-ttu-id="8fb80-482">bit</span><span class="sxs-lookup"><span data-stu-id="8fb80-482">Bit</span></span> | <span data-ttu-id="8fb80-483">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-483">Value</span></span> | <span data-ttu-id="8fb80-484">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-484">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="8fb80-485">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-485">0</span></span> | <span data-ttu-id="8fb80-486">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-486">0</span></span><br /><span data-ttu-id="8fb80-487">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-487">1</span></span> | <span data-ttu-id="8fb80-488">Выполнение в привилегированном режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-488">Privileged mode execution</span></span><br /><span data-ttu-id="8fb80-489">Выполнение в пользовательском режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-489">User mode execution</span></span> |
| <span data-ttu-id="8fb80-490">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-490">1</span></span> | <span data-ttu-id="8fb80-491">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-491">0</span></span><br /><span data-ttu-id="8fb80-492">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-492">1</span></span> | <span data-ttu-id="8fb80-493">Без защиты MPU.</span><span class="sxs-lookup"><span data-stu-id="8fb80-493">No MPU protection</span></span><br /><span data-ttu-id="8fb80-494">Защита MPU (необходимо выбрать пользовательский режим).</span><span class="sxs-lookup"><span data-stu-id="8fb80-494">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="8fb80-495">2</span><span class="sxs-lookup"><span data-stu-id="8fb80-495">2</span></span> | <span data-ttu-id="8fb80-496">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-496">0</span></span><br /><span data-ttu-id="8fb80-497">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-497">1</span></span> | <span data-ttu-id="8fb80-498">Отключение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-498">Disable shared/external memory access</span></span><br /><span data-ttu-id="8fb80-499">Включение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-499">Enable shared/external memory access</span></span> |
| <span data-ttu-id="8fb80-500">[23–3]</span><span class="sxs-lookup"><span data-stu-id="8fb80-500">[23-3]</span></span> | <span data-ttu-id="8fb80-501">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-501">0</span></span> | <span data-ttu-id="8fb80-502">Зарезервировано</span><span class="sxs-lookup"><span data-stu-id="8fb80-502">Reserved</span></span>
| <span data-ttu-id="8fb80-503">[31–24]</span><span class="sxs-lookup"><span data-stu-id="8fb80-503">[31-24]</span></span> | <br /><span data-ttu-id="8fb80-504">0x00</span><span class="sxs-lookup"><span data-stu-id="8fb80-504">0x00</span></span><br /><span data-ttu-id="8fb80-505">0x01</span><span class="sxs-lookup"><span data-stu-id="8fb80-505">0x01</span></span><br /><span data-ttu-id="8fb80-506">0x02</span><span class="sxs-lookup"><span data-stu-id="8fb80-506">0x02</span></span> | <span data-ttu-id="8fb80-507">**Идентификатор компилятора**</span><span class="sxs-lookup"><span data-stu-id="8fb80-507">**Compiler ID**</span></span><br /><span data-ttu-id="8fb80-508">IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-508">IAR</span></span><br /><span data-ttu-id="8fb80-509">ARM</span><span class="sxs-lookup"><span data-stu-id="8fb80-509">ARM</span></span><br /><span data-ttu-id="8fb80-510">GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-510">GNU</span></span> |

#### <a name="module-linker-for-cortex-m33-using-iar"></a><span data-ttu-id="8fb80-511">Компоновщик модулей для Cortex-M33 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-511">Module linker for Cortex-M33 using IAR</span></span>

```c
/*###ICF### Section handled by ICF editor, don't touch! ****/
/*-Editor annotation file-*/
/* IcfEditorFile="$TOOLKIT_DIR$\config\ide\IcfEditor\a_v1_0.xml" */
/*-Specials-*/
define symbol __ICFEDIT_intvec_start__ = 0x0;
/*-Memory Regions-*/
define symbol __ICFEDIT_region_ROM_start__ = 0x080f0000;
define symbol __ICFEDIT_region_ROM_end__   = 0x080fffff;
define symbol __ICFEDIT_region_RAM_start__ = 0x64002800;
define symbol __ICFEDIT_region_RAM_end__   = 0x64100000;
/*-Sizes-*/
define symbol __ICFEDIT_size_cstack__   = 0;
define symbol __ICFEDIT_size_svcstack__ = 0;
define symbol __ICFEDIT_size_irqstack__ = 0;
define symbol __ICFEDIT_size_fiqstack__ = 0;
define symbol __ICFEDIT_size_undstack__ = 0;
define symbol __ICFEDIT_size_abtstack__ = 0;
define symbol __ICFEDIT_size_heap__     = 0x1000;
/**** End of ICF editor section. ###ICF###*/

define memory mem with size = 4G;
define region ROM_region   = mem:[from __ICFEDIT_region_ROM_start__   to __ICFEDIT_region_ROM_end__];
define region RAM_region   = mem:[from __ICFEDIT_region_RAM_start__   to __ICFEDIT_region_RAM_end__];

//define block CSTACK    with alignment = 8, size = __ICFEDIT_size_cstack__   { };
//define block SVC_STACK with alignment = 8, size = __ICFEDIT_size_svcstack__ { };
//define block IRQ_STACK with alignment = 8, size = __ICFEDIT_size_irqstack__ { };
//define block FIQ_STACK with alignment = 8, size = __ICFEDIT_size_fiqstack__ { };
//define block UND_STACK with alignment = 8, size = __ICFEDIT_size_undstack__ { };
//define block ABT_STACK with alignment = 8, size = __ICFEDIT_size_abtstack__ { };
define block HEAP      with alignment = 8, size = __ICFEDIT_size_heap__     { };

initialize by copy { readwrite };
do not initialize  { section .noinit };

//place at address mem:__ICFEDIT_intvec_start__ { readonly section .intvec };

define movable block ROPI with alignment = 4, fixed order 
{ 
  ro object txm_module_preamble.o,
  ro, 
  ro data 
};

define movable block RWPI with alignment = 8, fixed order, static base
{
  rw,
  block HEAP
};

place in ROM_region   { block ROPI };
place in RAM_region   { block RWPI };
```

#### <a name="building-modules-for-cortex-m33-using-iar"></a><span data-ttu-id="8fb80-512">Создание модулей для Cortex-M33 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-512">Building Modules for Cortex-M33 using IAR</span></span>

#### <a name="thread-extension-definition-for-cortex-m33-using-iar"></a><span data-ttu-id="8fb80-513">Определение расширения потоков для Cortex-M33 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-513">Thread extension definition for Cortex-M33 using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2                   VOID    *tx_thread_module_instance_ptr;         \
                                                VOID    *tx_thread_module_entry_info_ptr;       \
                                                ULONG   tx_thread_module_current_user_mode;     \
                                                ULONG   tx_thread_module_user_mode;             \
                                                ULONG   tx_thread_module_saved_lr;              \
                                                VOID    *tx_thread_module_kernel_stack_start;   \
                                                VOID    *tx_thread_module_kernel_stack_end;     \
                                                ULONG   tx_thread_module_kernel_stack_size;     \
                                                VOID    *tx_thread_module_stack_ptr;            \
                                                VOID    *tx_thread_module_stack_start;          \
                                                VOID    *tx_thread_module_stack_end;            \
                                                ULONG   tx_thread_module_stack_size;            \
                                                VOID    *tx_thread_module_reserved;             \
                                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-cortex-m33-using-iar"></a><span data-ttu-id="8fb80-514">Создание диспетчера модулей для Cortex-M33 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-514">Building Module Manager for Cortex-M33 using IAR</span></span>

<span data-ttu-id="8fb80-515">Пример рабочей области еще не предоставлен.</span><span class="sxs-lookup"><span data-stu-id="8fb80-515">An example workspace is not yet provided.</span></span> <span data-ttu-id="8fb80-516">Ожидается в ближайшее время.</span><span class="sxs-lookup"><span data-stu-id="8fb80-516">Coming soon.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m33-using-iar"></a><span data-ttu-id="8fb80-517">Атрибуты API включения внешней памяти для Cortex-M33 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-517">Attributes for external memory enable API for Cortex-M33 using IAR</span></span>

| <span data-ttu-id="8fb80-518">Параметр атрибута</span><span class="sxs-lookup"><span data-stu-id="8fb80-518">Attribute parameter</span></span> |
|---|
| <span data-ttu-id="8fb80-519">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="8fb80-519">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span></span> |
| <span data-ttu-id="8fb80-520">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="8fb80-520">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span></span> |
| <span data-ttu-id="8fb80-521">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="8fb80-521">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span></span> |
| <span data-ttu-id="8fb80-522">TXM_MODULE_ATTRIBUTE_READ_WRITE</span><span class="sxs-lookup"><span data-stu-id="8fb80-522">TXM_MODULE_ATTRIBUTE_READ_WRITE</span></span> |
| <span data-ttu-id="8fb80-523">TXM_MODULE_ATTRIBUTE_READ_ONLY</span><span class="sxs-lookup"><span data-stu-id="8fb80-523">TXM_MODULE_ATTRIBUTE_READ_ONLY</span></span> |

## <a name="cortex-m4-processor"></a><span data-ttu-id="8fb80-524">Процессор Cortex-M4</span><span class="sxs-lookup"><span data-stu-id="8fb80-524">Cortex-M4 processor</span></span>

### <a name="cortex-m4-using-ac5"></a><span data-ttu-id="8fb80-525">Cortex-M4 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-525">Cortex-M4 using AC5</span></span>

#### <a name="module-preamble-for-cortex-m4-using-ac5"></a><span data-ttu-id="8fb80-526">Начальная часть модуля для Cortex-M4 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-526">Module preamble for Cortex-M4 using AC5</span></span>

```armasm
    AREA Init, CODE, READONLY

    PRESERVE8

    /* Define public symbols.  */

    EXPORT __txm_module_preamble

    ; Define application-specific start/stop entry points for the module

    EXTERN demo_module_start

    /* Define common external references.  */

    IMPORT  _txm_module_thread_shell_entry
    IMPORT  _txm_module_callback_request_thread_entry
    IMPORT  |Image$$ER_RO$$Length|
    IMPORT  |Image$$ER_RW$$Length|
    IMPORT  |Image$$ER_RW$$RW$$Length|
    IMPORT  |Image$$ER_RW$$ZI$$Length|
    IMPORT  |Image$$ER_ZI$$ZI$$Length|

__txm_module_preamble
    DCD     0x4D4F4455                                          // Module ID
    DCD     0x6                                                 // Module Major Version
    DCD     0x1                                                 // Module Minor Version
    DCD     32                                                  // Module Preamble Size in 32-bit words
    DCD     0x12345678                                          // Module ID (application defined)
    DCD     0x01000007                                          // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bits 23-3: Reserved
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
    DCD     _txm_module_thread_shell_entry - __txm_module_preamble              // Module Shell Entry Point
    DCD     demo_module_start - __txm_module_preamble           // Module Start Thread Entry Point
    DCD     0                                                   // Module Stop Thread Entry Point
    DCD     1                                                   // Module Start/Stop Thread Priority
    DCD     1024                                                // Module Start/Stop Thread Stack Size
    DCD     _txm_module_callback_request_thread_entry - __txm_module_preamble   // Module Callback Thread Entry
    DCD     1                                                   // Module Callback Thread Priority
    DCD     1024                                                // Module Callback Thread Stack Size
    DCD     |Image$$ER_RO$$Length| + |Image$$ER_RW$$Length|     // Module Code Size
    DCD     |Image$$ER_RW$$Length| + |Image$$ER_ZI$$ZI$$Length| // Module Data Size
    DCD     0                                                   // Reserved 0
    DCD     0                                                   // Reserved 1
    DCD     0                                                   // Reserved 2
    DCD     0                                                   // Reserved 3
    DCD     0                                                   // Reserved 4
    DCD     0                                                   // Reserved 5
    DCD     0                                                   // Reserved 6
    DCD     0                                                   // Reserved 7
    DCD     0                                                   // Reserved 8
    DCD     0                                                   // Reserved 9
    DCD     0                                                   // Reserved 10
    DCD     0                                                   // Reserved 11
    DCD     0                                                   // Reserved 12
    DCD     0                                                   // Reserved 13
    DCD     0                                                   // Reserved 14
    DCD     0                                                   // Reserved 15

    END
```

#### <a name="module-properties-for-cortex-m4-using-ac5"></a><span data-ttu-id="8fb80-527">Свойства модуля для Cortex-M4 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-527">Module properties for Cortex-M4 using AC5</span></span>

| <span data-ttu-id="8fb80-528">bit</span><span class="sxs-lookup"><span data-stu-id="8fb80-528">Bit</span></span> | <span data-ttu-id="8fb80-529">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-529">Value</span></span> | <span data-ttu-id="8fb80-530">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-530">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="8fb80-531">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-531">0</span></span> | <span data-ttu-id="8fb80-532">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-532">0</span></span><br /><span data-ttu-id="8fb80-533">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-533">1</span></span> | <span data-ttu-id="8fb80-534">Выполнение в привилегированном режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-534">Privileged mode execution</span></span><br /><span data-ttu-id="8fb80-535">Выполнение в пользовательском режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-535">User mode execution</span></span> |
| <span data-ttu-id="8fb80-536">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-536">1</span></span> | <span data-ttu-id="8fb80-537">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-537">0</span></span><br /><span data-ttu-id="8fb80-538">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-538">1</span></span> | <span data-ttu-id="8fb80-539">Без защиты MPU.</span><span class="sxs-lookup"><span data-stu-id="8fb80-539">No MPU protection</span></span><br /><span data-ttu-id="8fb80-540">Защита MPU (необходимо выбрать пользовательский режим).</span><span class="sxs-lookup"><span data-stu-id="8fb80-540">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="8fb80-541">2</span><span class="sxs-lookup"><span data-stu-id="8fb80-541">2</span></span> | <span data-ttu-id="8fb80-542">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-542">0</span></span><br /><span data-ttu-id="8fb80-543">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-543">1</span></span> | <span data-ttu-id="8fb80-544">Отключение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-544">Disable shared/external memory access</span></span><br /><span data-ttu-id="8fb80-545">Включение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-545">Enable shared/external memory access</span></span> |
| <span data-ttu-id="8fb80-546">[23–3]</span><span class="sxs-lookup"><span data-stu-id="8fb80-546">[23-3]</span></span> | <span data-ttu-id="8fb80-547">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-547">0</span></span> | <span data-ttu-id="8fb80-548">Зарезервировано</span><span class="sxs-lookup"><span data-stu-id="8fb80-548">Reserved</span></span>
| <span data-ttu-id="8fb80-549">[31–24]</span><span class="sxs-lookup"><span data-stu-id="8fb80-549">[31-24]</span></span> | <br /><span data-ttu-id="8fb80-550">0x00</span><span class="sxs-lookup"><span data-stu-id="8fb80-550">0x00</span></span><br /><span data-ttu-id="8fb80-551">0x01</span><span class="sxs-lookup"><span data-stu-id="8fb80-551">0x01</span></span><br /><span data-ttu-id="8fb80-552">0x02</span><span class="sxs-lookup"><span data-stu-id="8fb80-552">0x02</span></span> | <span data-ttu-id="8fb80-553">**Идентификатор компилятора**</span><span class="sxs-lookup"><span data-stu-id="8fb80-553">**Compiler ID**</span></span><br /><span data-ttu-id="8fb80-554">IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-554">IAR</span></span><br /><span data-ttu-id="8fb80-555">ARM</span><span class="sxs-lookup"><span data-stu-id="8fb80-555">ARM</span></span><br /><span data-ttu-id="8fb80-556">GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-556">GNU</span></span> |

#### <a name="module-linker-for-cortex-m4-using-ac5"></a><span data-ttu-id="8fb80-557">Компоновщик модулей для Cortex-M4 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-557">Module linker for Cortex-M4 using AC5</span></span>

<span data-ttu-id="8fb80-558">Пример файла компоновщика не предоставляется. Компоновка выполняется в командной строке.</span><span class="sxs-lookup"><span data-stu-id="8fb80-558">No example linker file is provided; linking is done on the command line.</span></span> <span data-ttu-id="8fb80-559">Ознакомьтесь со следующим разделом.</span><span class="sxs-lookup"><span data-stu-id="8fb80-559">See next section.</span></span>

#### <a name="building-modules-for-cortex-m4-using-ac5"></a><span data-ttu-id="8fb80-560">Создание модулей для Cortex-M4 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-560">Building Modules for Cortex-M4 using AC5</span></span>

<span data-ttu-id="8fb80-561">Ознакомьтесь с примером файла build_threadx_module_demo.bat.</span><span class="sxs-lookup"><span data-stu-id="8fb80-561">See example build_threadx_module_demo.bat:</span></span>

```dos
armasm -g --cpreproc --cpu=cortex-m4 --fpu=vfpv4 --apcs=/interwork/ropi/rwpi txm_module_preamble.S
armcc  -g --cpu=cortex-m4 --fpu=vfpv4 -c --apcs=/interwork/ropi/rwpi --lower_ropi -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module.c
armlink -d -o sample_threadx_module.axf --elf --ro=0x30000 --rw=0x40000 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list sample_threadx_module.map txm_module_preamble.o sample_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-m4-using-ac5"></a><span data-ttu-id="8fb80-562">Определение расширения потоков для Cortex-M4 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-562">Thread extension definition for Cortex-M4 using AC5</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m4-using-ac5"></a><span data-ttu-id="8fb80-563">Создание диспетчера модулей для Cortex-M4 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-563">Building Module Manager for Cortex-M4 using AC5</span></span>

<span data-ttu-id="8fb80-564">Ознакомьтесь с примером файла build_threadx_module_manager_demo.bat.</span><span class="sxs-lookup"><span data-stu-id="8fb80-564">See example build_threadx_module_manager_demo.bat:</span></span>

```dos
armasm -g --cpreproc --cpu=cortex-m4 --fpu=vfpv4 --apcs=/interwork tx_initialize_low_level.S
armcc -g --cpu=cortex-m4 --fpu=vfpv4 -c -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module_manager.c
armlink -d -o sample_threadx_module_manager.axf --elf --ro 0x00000000 --first tx_initialize_low_level.o(RESET) --remove --map --symbols --list sample_threadx_module_manager.map tx_initialize_low_level.o sample_threadx_module_manager.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m4-using-ac5"></a><span data-ttu-id="8fb80-565">Атрибуты API включения внешней памяти для Cortex-M4 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-565">Attributes for external memory enable API for Cortex-M4 using AC5</span></span>

<span data-ttu-id="8fb80-566">Модуль всегда имеет доступ на чтение к общей памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-566">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="8fb80-567">Параметр атрибута</span><span class="sxs-lookup"><span data-stu-id="8fb80-567">Attribute parameter</span></span> | <span data-ttu-id="8fb80-568">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-568">Meaning</span></span> |
|---|---|
| <span data-ttu-id="8fb80-569">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="8fb80-569">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="8fb80-570">Доступ для записи.</span><span class="sxs-lookup"><span data-stu-id="8fb80-570">Write access</span></span> |

### <a name="cortex-m4-using-ac6"></a><span data-ttu-id="8fb80-571">Cortex-M4 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-571">Cortex-M4 using AC6</span></span>

#### <a name="module-preamble-for-cortex-m4-using-ac6"></a><span data-ttu-id="8fb80-572">Начальная часть модуля для Cortex-M4 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-572">Module preamble for Cortex-M4 using AC6</span></span>

```armasm
    .text
    .align 4
    .syntax unified
    .section Init
    
    // Define public symbols
    .global __txm_module_preamble

    // Define application-specific start/stop entry points for the module
    .global demo_module_start

    // Define common external references
    .global  _txm_module_thread_shell_entry
    .global  _txm_module_callback_request_thread_entry

    .eabi_attribute Tag_ABI_PCS_RO_data, 1
    .eabi_attribute Tag_ABI_PCS_R9_use,  1
    .eabi_attribute Tag_ABI_PCS_RW_data, 2

__txm_module_preamble:
    .dc.l   0x4D4F4455                                          // Module ID
    .dc.l   0x6                                                 // Module Major Version
    .dc.l   0x1                                                 // Module Minor Version
    .dc.l   32                                                  // Module Preamble Size in 32-bit words
    .dc.l   0x12345678                                          // Module ID (application defined)
    .dc.l   0x01000007                                          // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
    .dc.l   _txm_module_thread_shell_entry - __txm_module_preamble // Module Shell Entry Point
    .dc.l   demo_module_start - __txm_module_preamble           // Module Start Thread Entry Point
    .dc.l   0                                                   // Module Stop Thread Entry Point
    .dc.l   1                                                   // Module Start/Stop Thread Priority
    .dc.l   1024                                                // Module Start/Stop Thread Stack Size
    .dc.l   _txm_module_callback_request_thread_entry - __txm_module_preamble // Module Callback Thread Entry
    .dc.l   1                                                   // Module Callback Thread Priority
    .dc.l   1024                                                // Module Callback Thread Stack Size
    .dc.l   0x10000                                             // Module Code Size
    .dc.l   0x10000                                             // Module Data Size
    .dc.l   0                                                   // Reserved 0
    .dc.l   0                                                   // Reserved 1
    .dc.l   0                                                   // Reserved 2
    .dc.l   0                                                   // Reserved 3
    .dc.l   0                                                   // Reserved 4
    .dc.l   0                                                   // Reserved 5
    .dc.l   0                                                   // Reserved 6
    .dc.l   0                                                   // Reserved 7
    .dc.l   0                                                   // Reserved 8
    .dc.l   0                                                   // Reserved 9
    .dc.l   0                                                   // Reserved 10
    .dc.l   0                                                   // Reserved 11
    .dc.l   0                                                   // Reserved 12
    .dc.l   0                                                   // Reserved 13
    .dc.l   0                                                   // Reserved 14
    .dc.l   0                                                   // Reserved 15
```

#### <a name="module-properties-for-cortex-m4-using-ac6"></a><span data-ttu-id="8fb80-573">Свойства модуля для Cortex-M4 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-573">Module properties for Cortex-M4 using AC6</span></span>

| <span data-ttu-id="8fb80-574">bit</span><span class="sxs-lookup"><span data-stu-id="8fb80-574">Bit</span></span> | <span data-ttu-id="8fb80-575">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-575">Value</span></span> | <span data-ttu-id="8fb80-576">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-576">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="8fb80-577">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-577">0</span></span> | <span data-ttu-id="8fb80-578">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-578">0</span></span><br /><span data-ttu-id="8fb80-579">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-579">1</span></span> | <span data-ttu-id="8fb80-580">Выполнение в привилегированном режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-580">Privileged mode execution</span></span><br /><span data-ttu-id="8fb80-581">Выполнение в пользовательском режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-581">User mode execution</span></span> |
| <span data-ttu-id="8fb80-582">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-582">1</span></span> | <span data-ttu-id="8fb80-583">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-583">0</span></span><br /><span data-ttu-id="8fb80-584">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-584">1</span></span> | <span data-ttu-id="8fb80-585">Без защиты MPU.</span><span class="sxs-lookup"><span data-stu-id="8fb80-585">No MPU protection</span></span><br /><span data-ttu-id="8fb80-586">Защита MPU (необходимо выбрать пользовательский режим).</span><span class="sxs-lookup"><span data-stu-id="8fb80-586">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="8fb80-587">2</span><span class="sxs-lookup"><span data-stu-id="8fb80-587">2</span></span> | <span data-ttu-id="8fb80-588">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-588">0</span></span><br /><span data-ttu-id="8fb80-589">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-589">1</span></span> | <span data-ttu-id="8fb80-590">Отключение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-590">Disable shared/external memory access</span></span><br /><span data-ttu-id="8fb80-591">Включение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-591">Enable shared/external memory access</span></span> |
| <span data-ttu-id="8fb80-592">[23–3]</span><span class="sxs-lookup"><span data-stu-id="8fb80-592">[23-3]</span></span> | <span data-ttu-id="8fb80-593">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-593">0</span></span> | <span data-ttu-id="8fb80-594">Зарезервировано</span><span class="sxs-lookup"><span data-stu-id="8fb80-594">Reserved</span></span>
| <span data-ttu-id="8fb80-595">[31–24]</span><span class="sxs-lookup"><span data-stu-id="8fb80-595">[31-24]</span></span> | <br /><span data-ttu-id="8fb80-596">0x00</span><span class="sxs-lookup"><span data-stu-id="8fb80-596">0x00</span></span><br /><span data-ttu-id="8fb80-597">0x01</span><span class="sxs-lookup"><span data-stu-id="8fb80-597">0x01</span></span><br /><span data-ttu-id="8fb80-598">0x02</span><span class="sxs-lookup"><span data-stu-id="8fb80-598">0x02</span></span> | <span data-ttu-id="8fb80-599">**Идентификатор компилятора**</span><span class="sxs-lookup"><span data-stu-id="8fb80-599">**Compiler ID**</span></span><br /><span data-ttu-id="8fb80-600">IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-600">IAR</span></span><br /><span data-ttu-id="8fb80-601">ARM</span><span class="sxs-lookup"><span data-stu-id="8fb80-601">ARM</span></span><br /><span data-ttu-id="8fb80-602">GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-602">GNU</span></span> |

#### <a name="module-linker-for-cortex-m4-using-ac6"></a><span data-ttu-id="8fb80-603">Компоновщик модулей для Cortex-M4 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-603">Module linker for Cortex-M4 using AC6</span></span>

<span data-ttu-id="8fb80-604">Файл компоновщика не используется.</span><span class="sxs-lookup"><span data-stu-id="8fb80-604">No linker file is used.</span></span> <span data-ttu-id="8fb80-605">Ознакомьтесь с параметрами проекта.</span><span class="sxs-lookup"><span data-stu-id="8fb80-605">See project settings.</span></span>

#### <a name="building-modules-for-cortex-m4-using-ac6"></a><span data-ttu-id="8fb80-606">Создание модулей для Cortex-M4 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-606">Building Modules for Cortex-M4 using AC6</span></span>

<span data-ttu-id="8fb80-607">Предоставлен пример рабочей области.</span><span class="sxs-lookup"><span data-stu-id="8fb80-607">An example workspace is provided.</span></span> <span data-ttu-id="8fb80-608">Можно создать библиотеку ThreadX, библиотеку модулей ThreadX, пример проекта модуля и пример проекта диспетчера модулей.</span><span class="sxs-lookup"><span data-stu-id="8fb80-608">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m4-using-ac6"></a><span data-ttu-id="8fb80-609">Определение расширения потоков для Cortex-M4 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-609">Thread extension definition for Cortex-M4 using AC6</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m4-using-ac6"></a><span data-ttu-id="8fb80-610">Создание диспетчера модулей для Cortex-M4 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-610">Building Module Manager for Cortex-M4 using AC6</span></span>

<span data-ttu-id="8fb80-611">Предоставлен пример рабочей области.</span><span class="sxs-lookup"><span data-stu-id="8fb80-611">An example workspace is provided.</span></span> <span data-ttu-id="8fb80-612">Можно создать библиотеку ThreadX, библиотеку модулей ThreadX, пример проекта модуля и пример проекта диспетчера модулей.</span><span class="sxs-lookup"><span data-stu-id="8fb80-612">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m4-using-ac6"></a><span data-ttu-id="8fb80-613">Атрибуты API включения внешней памяти для Cortex-M4 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-613">Attributes for external memory enable API for Cortex-M4 using AC6</span></span>

<span data-ttu-id="8fb80-614">Модуль всегда имеет доступ на чтение к общей памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-614">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="8fb80-615">Параметр атрибута</span><span class="sxs-lookup"><span data-stu-id="8fb80-615">Attribute parameter</span></span> | <span data-ttu-id="8fb80-616">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-616">Meaning</span></span> |
|---|---|
| <span data-ttu-id="8fb80-617">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="8fb80-617">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="8fb80-618">Доступ для записи.</span><span class="sxs-lookup"><span data-stu-id="8fb80-618">Write access</span></span> |

### <a name="cortex-m4-using-gnu"></a><span data-ttu-id="8fb80-619">Cortex-M4 с поддержкой GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-619">Cortex-M4 using GNU</span></span>

#### <a name="module-preamble-for-cortex-m4-using-gnu"></a><span data-ttu-id="8fb80-620">Начальная часть модуля для Cortex-M4 с поддержкой GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-620">Module preamble for Cortex-M4 using GNU</span></span>

```armasm
    .text
    .align 4
    .syntax unified

    /* Define public symbols.  */
    .global __txm_module_preamble

    /* Define application-specific start/stop entry points for the module.  */
    .global demo_module_start

    /* Define common external refrences.  */
    .global _txm_module_thread_shell_entry
    .global _txm_module_callback_request_thread_entry

__txm_module_preamble:
    .dc.l      0x4D4F4455                                       // Module ID
    .dc.l      0x6                                              // Module Major Version
    .dc.l      0x1                                              // Module Minor Version
    .dc.l      32                                               // Module Preamble Size in 32-bit words
    .dc.l      0x12345678                                       // Module ID (application defined)
    .dc.l      0x02000007                                       // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bits 23-3: Reserved
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
    .dc.l      _txm_module_thread_shell_entry - . - 0           // Module Shell Entry Point
    .dc.l      demo_module_start - . - 0                        // Module Start Thread Entry Point
    .dc.l      0                                                // Module Stop Thread Entry Point 
    .dc.l      1                                                // Module Start/Stop Thread Priority
    .dc.l      1024                                             // Module Start/Stop Thread Stack Size
    .dc.l      _txm_module_callback_request_thread_entry - . - 0 // Module Callback Thread Entry
    .dc.l      1                                                // Module Callback Thread Priority
    .dc.l      1024                                             // Module Callback Thread Stack Size
    .dc.l      __code_size__                                    // Module Code Size
    .dc.l      __data_size__                                    // Module Data Size
    .dc.l      0                                                // Reserved 0
    .dc.l      0                                                // Reserved 1
    .dc.l      0                                                // Reserved 2
    .dc.l      0                                                // Reserved 3
    .dc.l      0                                                // Reserved 4
    .dc.l      0                                                // Reserved 5
    .dc.l      0                                                // Reserved 6
    .dc.l      0                                                // Reserved 7
    .dc.l      0                                                // Reserved 8
    .dc.l      0                                                // Reserved 9
    .dc.l      0                                                // Reserved 10
    .dc.l      0                                                // Reserved 11
    .dc.l      0                                                // Reserved 12
    .dc.l      0                                                // Reserved 13
    .dc.l      0                                                // Reserved 14
    .dc.l      0                                                // Reserved 15
```

#### <a name="module-properties-for-cortex-m4-using-gnu"></a><span data-ttu-id="8fb80-621">Свойства модуля для Cortex-M4 с поддержкой GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-621">Module properties for Cortex-M4 using GNU</span></span>

| <span data-ttu-id="8fb80-622">bit</span><span class="sxs-lookup"><span data-stu-id="8fb80-622">Bit</span></span> | <span data-ttu-id="8fb80-623">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-623">Value</span></span> | <span data-ttu-id="8fb80-624">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-624">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="8fb80-625">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-625">0</span></span> | <span data-ttu-id="8fb80-626">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-626">0</span></span><br /><span data-ttu-id="8fb80-627">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-627">1</span></span> | <span data-ttu-id="8fb80-628">Выполнение в привилегированном режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-628">Privileged mode execution</span></span><br /><span data-ttu-id="8fb80-629">Выполнение в пользовательском режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-629">User mode execution</span></span> |
| <span data-ttu-id="8fb80-630">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-630">1</span></span> | <span data-ttu-id="8fb80-631">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-631">0</span></span><br /><span data-ttu-id="8fb80-632">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-632">1</span></span> | <span data-ttu-id="8fb80-633">Без защиты MPU.</span><span class="sxs-lookup"><span data-stu-id="8fb80-633">No MPU protection</span></span><br /><span data-ttu-id="8fb80-634">Защита MPU (необходимо выбрать пользовательский режим).</span><span class="sxs-lookup"><span data-stu-id="8fb80-634">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="8fb80-635">2</span><span class="sxs-lookup"><span data-stu-id="8fb80-635">2</span></span> | <span data-ttu-id="8fb80-636">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-636">0</span></span><br /><span data-ttu-id="8fb80-637">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-637">1</span></span> | <span data-ttu-id="8fb80-638">Отключение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-638">Disable shared/external memory access</span></span><br /><span data-ttu-id="8fb80-639">Включение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-639">Enable shared/external memory access</span></span> |
| <span data-ttu-id="8fb80-640">[23–3]</span><span class="sxs-lookup"><span data-stu-id="8fb80-640">[23-3]</span></span> | <span data-ttu-id="8fb80-641">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-641">0</span></span> | <span data-ttu-id="8fb80-642">Зарезервировано</span><span class="sxs-lookup"><span data-stu-id="8fb80-642">Reserved</span></span>
| <span data-ttu-id="8fb80-643">[31–24]</span><span class="sxs-lookup"><span data-stu-id="8fb80-643">[31-24]</span></span> | <br /><span data-ttu-id="8fb80-644">0x00</span><span class="sxs-lookup"><span data-stu-id="8fb80-644">0x00</span></span><br /><span data-ttu-id="8fb80-645">0x01</span><span class="sxs-lookup"><span data-stu-id="8fb80-645">0x01</span></span><br /><span data-ttu-id="8fb80-646">0x02</span><span class="sxs-lookup"><span data-stu-id="8fb80-646">0x02</span></span> | <span data-ttu-id="8fb80-647">**Идентификатор компилятора**</span><span class="sxs-lookup"><span data-stu-id="8fb80-647">**Compiler ID**</span></span><br /><span data-ttu-id="8fb80-648">IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-648">IAR</span></span><br /><span data-ttu-id="8fb80-649">ARM</span><span class="sxs-lookup"><span data-stu-id="8fb80-649">ARM</span></span><br /><span data-ttu-id="8fb80-650">GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-650">GNU</span></span> |

#### <a name="module-linker-for-cortex-m4-using-gnu"></a><span data-ttu-id="8fb80-651">Компоновщик модулей для Cortex-M4 с поддержкой GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-651">Module linker for Cortex-M4 using GNU</span></span>

```c
MEMORY
{
  FLASH (rx) : ORIGIN = 0x00030000, LENGTH = 0x00010000
  RAM   (wx) : ORIGIN = 0, LENGTH = 0x00100000
}


SECTIONS
{
  __FLASH_segment_start__ = 0x00030000;
  __FLASH_segment_end__   = 0x00040000;
  __RAM_segment_start__   = 0;
  __RAM_segment_end__     = 0x8000;

  __HEAPSIZE__ = 128;

  __preamble_load_start__ = __FLASH_segment_start__;
  .preamble __FLASH_segment_start__ : AT(__FLASH_segment_start__)
  {
    __preamble_start__ = .;
    *(.preamble .preamble.*)
  }
  __preamble_end__ = __preamble_start__ + SIZEOF(.preamble);

  __dynsym_load_start__ =  ALIGN(__preamble_end__ , 4);
  .dynsym ALIGN(__dynsym_load_start__ , 4) : AT(ALIGN(__dynsym_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynsym))
    KEEP (*(.dynsym*))
    . = ALIGN(4);
  }
  __dynsym_end__ = __dynsym_load_start__ + SIZEOF(.dynsym);

  __dynstr_load_start__ =  ALIGN(__dynsym_end__ , 4);
  .dynstr ALIGN(__dynstr_load_start__ , 4) : AT(ALIGN(__dynstr_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynstr))
    KEEP (*(.dynstr*))
    . = ALIGN(4);
  }
  __dynstr_end__ = __dynstr_load_start__ + SIZEOF(.dynstr);

  __reldyn_load_start__ =  ALIGN(__dynstr_end__ , 4);
  .rel.dyn ALIGN(__reldyn_load_start__ , 4) : AT(ALIGN(__reldyn_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.dyn))
    KEEP (*(.rel.dyn*))
    . = ALIGN(4);
  }
  __reldyn_end__ = __reldyn_load_start__ + SIZEOF(.rel.dyn);

  __relplt_load_start__ =  ALIGN(__reldyn_end__ , 4);
  .rel.plt ALIGN(__relplt_load_start__ , 4) : AT(ALIGN(__relplt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.plt))
    KEEP (*(.rel.plt*))
    . = ALIGN(4);
  }
  __relplt_end__ = __relplt_load_start__ + SIZEOF(.rel.plt);

  __plt_load_start__ =  ALIGN(__relplt_end__ , 4);
  .plt ALIGN(__plt_load_start__ , 4) : AT(ALIGN(__plt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.plt))
    KEEP (*(.plt*))
    . = ALIGN(4);
  }
  __plt_end__ = __plt_load_start__ + SIZEOF(.plt);

  __interp_load_start__ =  ALIGN(__plt_end__ , 4);
  .interp ALIGN(__interp_load_start__ , 4) : AT(ALIGN(__interp_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.interp))
    KEEP (*(.interp*))
    . = ALIGN(4);
  }
  __interp_end__ = __interp_load_start__ + SIZEOF(.interp);

  __hash_load_start__ =  ALIGN(__interp_end__ , 4);
  .hash ALIGN(__hash_load_start__ , 4) : AT(ALIGN(__hash_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.hash))
    KEEP (*(.hash*))
    . = ALIGN(4);
  }
  __hash_end__ = __hash_load_start__ + SIZEOF(.hash);

  __text_load_start__ =  ALIGN(__hash_end__ , 4);
  .text ALIGN(__text_load_start__ , 4) : AT(ALIGN(__text_load_start__, 4))
  {
    __text_start__ = .;
    *(.text .text.* .glue_7t .glue_7 .gnu.linkonce.t.* .gcc_except_table  )
  }
  __text_end__ = __text_start__ + SIZEOF(.text);

  __dtors_load_start__ = ALIGN(__text_end__ , 4);
  .dtors ALIGN(__text_end__ , 4) : AT(ALIGN(__text_end__ , 4))
  {
    __dtors_start__ = .;
    KEEP (*(SORT(.dtors.*))) KEEP (*(.dtors))
  }
  __dtors_end__ = __dtors_start__ + SIZEOF(.dtors);

  __ctors_load_start__ = ALIGN(__dtors_end__ , 4);
  .ctors ALIGN(__dtors_end__ , 4) : AT(ALIGN(__dtors_end__ , 4))
  {
    __ctors_start__ = .;
    KEEP (*(SORT(.ctors.*))) KEEP (*(.ctors))
  }
  __ctors_end__ = __ctors_start__ + SIZEOF(.ctors);

  __got_load_start__ = ALIGN(__ctors_end__ , 4);
  .got ALIGN(__ctors_end__ , 4) : AT(ALIGN(__ctors_end__ , 4))
  {
    . = ALIGN(4);
    _sgot = .;
    KEEP (*(.got))
    KEEP (*(.got*))
    . = ALIGN(4);
    _egot = .;
  } 
  __got_end__ =  __got_load_start__ + SIZEOF(.got);

  __rodata_load_start__ = ALIGN(__got_end__ , 4);
  .rodata ALIGN(__got_end__ , 4) : AT(ALIGN(__got_end__ , 4))
  {
    __rodata_start__ = .;
    *(.rodata .rodata.* .gnu.linkonce.r.*)
  }
  __rodata_end__ = __rodata_start__ + SIZEOF(.rodata);
 
  __code_size__ =  __rodata_end__ - __FLASH_segment_start__;

  __fast_load_start__ = ALIGN(__rodata_end__ , 4);

  __fast_load_end__ = __fast_load_start__ + SIZEOF(.fast);

  __new_got_start__ = ALIGN(__RAM_segment_start__ , 4);

  __new_got_end__ =  __new_got_start__ + SIZEOF(.got);

  .fast ALIGN(__new_got_end__ , 4) : AT(ALIGN(__rodata_end__ , 4))
  {
    __fast_start__ = .;
    *(.fast .fast.*)
  }
  __fast_end__ = __fast_start__ + SIZEOF(.fast);

  .fast_run ALIGN(__fast_end__ , 4) (NOLOAD) :
  {
    __fast_run_start__ = .;
    . = MAX(__fast_run_start__ + SIZEOF(.fast), .);
  }
  __fast_run_end__ = __fast_run_start__ + SIZEOF(.fast_run);

  __data_load_start__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4);
  .data ALIGN(__fast_run_end__ , 4) : AT(ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4))
  {
    __data_start__ = .;
    *(.data .data.* .gnu.linkonce.d.*)
  }
  __data_end__ = __data_start__ + SIZEOF(.data);

  __data_load_end__ = __data_load_start__ + SIZEOF(.data);

  __FLASH_segment_used_end__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4) + SIZEOF(.data);

  .data_run ALIGN(__fast_run_end__ , 4) (NOLOAD) :
  {
    __data_run_start__ = .;
    . = MAX(__data_run_start__ + SIZEOF(.data), .);
  }
  __data_run_end__ = __data_run_start__ + SIZEOF(.data_run);

  __bss_load_start__ = ALIGN(__data_run_end__ , 4);
  .bss ALIGN(__data_run_end__ , 4) (NOLOAD) : AT(ALIGN(__data_run_end__ , 4))
  {
    __bss_start__ = .;
    *(.bss .bss.* .gnu.linkonce.b.*) *(COMMON)
  }
  __bss_end__ = __bss_start__ + SIZEOF(.bss);

  __non_init_load_start__ = ALIGN(__bss_end__ , 4);
  .non_init ALIGN(__bss_end__ , 4) (NOLOAD) : AT(ALIGN(__bss_end__ , 4))
  {
    __non_init_start__ = .;
    *(.non_init .non_init.*)
  }
  __non_init_end__ = __non_init_start__ + SIZEOF(.non_init);

  __heap_load_start__ = ALIGN(__non_init_end__ , 4);
  .heap ALIGN(__non_init_end__ , 4) (NOLOAD) : AT(ALIGN(__non_init_end__ , 4))
  {
    __heap_start__ = .;
    *(.heap)
    . = ALIGN(MAX(__heap_start__ + __HEAPSIZE__ , .), 4);
  }
  __heap_end__ = __heap_start__ + SIZEOF(.heap);

  __data_size__ =  __heap_end__ - __RAM_segment_start__;

}
```

#### <a name="building-modules-for-cortex-m4-using-gnu"></a><span data-ttu-id="8fb80-652">Создание модулей для Cortex-M4 с поддержкой GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-652">Building Modules for Cortex-M4 using GNU</span></span>

<span data-ttu-id="8fb80-653">Ознакомьтесь с файлом build_threadx_module_sample.bat.</span><span class="sxs-lookup"><span data-stu-id="8fb80-653">See build_threadx_module_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base txm_module_preamble.s
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base gcc_setup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module.c
arm-none-eabi-ld -A cortex-m4 -T sample_threadx_module.ld txm_module_preamble.o gcc_setup.o sample_threadx_module.o -e _txm_module_thread_shell_entry txm.a -o sample_threadx_module.axf -M > sample_threadx_module.map
```

#### <a name="thread-extension-definition-for-cortex-m4-using-gnu"></a><span data-ttu-id="8fb80-654">Определение расширения потоков для Cortex-M4 с поддержкой GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-654">Thread extension definition for Cortex-M4 using GNU</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m4-using-gnu"></a><span data-ttu-id="8fb80-655">Создание диспетчера модулей для Cortex-M4 с поддержкой GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-655">Building Module Manager for Cortex-M4 using GNU</span></span>

<span data-ttu-id="8fb80-656">Ознакомьтесь с файлом build_threadx_module_manager_sample.bat.</span><span class="sxs-lookup"><span data-stu-id="8fb80-656">See build_threadx_module_manager_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb cortexm_vectors.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb cortexm_crt0.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb tx_initialize_low_level.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module_manager.c
arm-none-eabi-gcc -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb -T sample_threadx.ld -ereset_handler -nostartfiles -o sample_threadx_module_manager.out -Wl,-Map=sample_threadx_module_manager.map cortexm_vectors.o cortexm_crt0.o tx_initialize_low_level.o sample_threadx_module_manager.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m4-using-gnu"></a><span data-ttu-id="8fb80-657">Атрибуты API включения внешней памяти для Cortex-M4 с поддержкой GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-657">Attributes for external memory enable API for Cortex-M4 using GNU</span></span>

<span data-ttu-id="8fb80-658">Модуль всегда имеет доступ на чтение к общей памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-658">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="8fb80-659">Параметр атрибута</span><span class="sxs-lookup"><span data-stu-id="8fb80-659">Attribute parameter</span></span> | <span data-ttu-id="8fb80-660">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-660">Meaning</span></span> |
|---|---|
| <span data-ttu-id="8fb80-661">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="8fb80-661">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="8fb80-662">Доступ для записи.</span><span class="sxs-lookup"><span data-stu-id="8fb80-662">Write access</span></span> |

### <a name="cortex-m4-using-iar"></a><span data-ttu-id="8fb80-663">Cortex-M4 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-663">Cortex-M4 using IAR</span></span>

#### <a name="module-preamble-for-cortex-m4-using-iar"></a><span data-ttu-id="8fb80-664">Начальная часть модуля для Cortex-M4 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-664">Module preamble for Cortex-M4 using IAR</span></span>

```c
    SECTION .text:CODE

    AAPCS INTERWORK, ROPI, RWPI_COMPATIBLE,  VFP_COMPATIBLE
    PRESERVE8

    /* Define public symbols.  */

    PUBLIC __txm_module_preamble


    /* Define application-specific start/stop entry points for the module.  */

    EXTERN demo_module_start


    /* Define common external references.  */

    EXTERN  _txm_module_thread_shell_entry
    EXTERN  _txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        ; Module ID
    DC32      0x5                                               ; Module Major Version
    DC32      0x6                                               ; Module Minor Version
    DC32      32                                                ; Module Preamble Size in 32-bit words
    DC32      0x12345678                                        ; Module ID (application defined)
    DC32      0x00000007                                        ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bits 23-3: Reserved
                                                                ;   Bit 2:  0 -> Disable shared/external memory access
                                                                ;           1 -> Enable shared/external memory access
                                                                ;   Bit 1:  0 -> No MPU protection
                                                                ;           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                ;   Bit 0:  0 -> Privileged mode execution
                                                                ;           1 -> User mode execution


    DC32      _txm_module_thread_shell_entry - . - 0            ; Module Shell Entry Point
    DC32      demo_module_start - . - 0                         ; Module Start Thread Entry Point
    DC32      0                                                 ; Module Stop Thread Entry Point
    DC32      1                                                 ; Module Start/Stop Thread Priority
    DC32      1024                                              ; Module Start/Stop Thread Stack Size
    DC32      _txm_module_callback_request_thread_entry - . - 0 ; Module Callback Thread Entry
    DC32      1                                                 ; Module Callback Thread Priority
    DC32      1024                                              ; Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      ; Module Code Size
    DC32      RWPI$$Length                                      ; Module Data Size
    DC32      0                                                 ; Reserved 0
    DC32      0                                                 ; Reserved 1
    DC32      0                                                 ; Reserved 2
    DC32      0                                                 ; Reserved 3
    DC32      0                                                 ; Reserved 4
    DC32      0                                                 ; Reserved 5
    DC32      0                                                 ; Reserved 6
    DC32      0                                                 ; Reserved 7
    DC32      0                                                 ; Reserved 8  
    DC32      0                                                 ; Reserved 9
    DC32      0                                                 ; Reserved 10
    DC32      0                                                 ; Reserved 11
    DC32      0                                                 ; Reserved 12
    DC32      0                                                 ; Reserved 13
    DC32      0                                                 ; Reserved 14
    DC32      0                                                 ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-m4-using-iar"></a><span data-ttu-id="8fb80-665">Свойства модуля для Cortex-M4 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-665">Module properties for Cortex-M4 using IAR</span></span>

| <span data-ttu-id="8fb80-666">bit</span><span class="sxs-lookup"><span data-stu-id="8fb80-666">Bit</span></span> | <span data-ttu-id="8fb80-667">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-667">Value</span></span> | <span data-ttu-id="8fb80-668">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-668">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="8fb80-669">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-669">0</span></span> | <span data-ttu-id="8fb80-670">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-670">0</span></span><br /><span data-ttu-id="8fb80-671">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-671">1</span></span> | <span data-ttu-id="8fb80-672">Выполнение в привилегированном режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-672">Privileged mode execution</span></span><br /><span data-ttu-id="8fb80-673">Выполнение в пользовательском режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-673">User mode execution</span></span> |
| <span data-ttu-id="8fb80-674">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-674">1</span></span> | <span data-ttu-id="8fb80-675">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-675">0</span></span><br /><span data-ttu-id="8fb80-676">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-676">1</span></span> | <span data-ttu-id="8fb80-677">Без защиты MPU.</span><span class="sxs-lookup"><span data-stu-id="8fb80-677">No MPU protection</span></span><br /><span data-ttu-id="8fb80-678">Защита MPU (необходимо выбрать пользовательский режим).</span><span class="sxs-lookup"><span data-stu-id="8fb80-678">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="8fb80-679">2</span><span class="sxs-lookup"><span data-stu-id="8fb80-679">2</span></span> | <span data-ttu-id="8fb80-680">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-680">0</span></span><br /><span data-ttu-id="8fb80-681">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-681">1</span></span> | <span data-ttu-id="8fb80-682">Отключение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-682">Disable shared/external memory access</span></span><br /><span data-ttu-id="8fb80-683">Включение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-683">Enable shared/external memory access</span></span> |
| <span data-ttu-id="8fb80-684">[23–3]</span><span class="sxs-lookup"><span data-stu-id="8fb80-684">[23-3]</span></span> | <span data-ttu-id="8fb80-685">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-685">0</span></span> | <span data-ttu-id="8fb80-686">Зарезервировано</span><span class="sxs-lookup"><span data-stu-id="8fb80-686">Reserved</span></span>
| <span data-ttu-id="8fb80-687">[31–24]</span><span class="sxs-lookup"><span data-stu-id="8fb80-687">[31-24]</span></span> | <br /><span data-ttu-id="8fb80-688">0x00</span><span class="sxs-lookup"><span data-stu-id="8fb80-688">0x00</span></span><br /><span data-ttu-id="8fb80-689">0x01</span><span class="sxs-lookup"><span data-stu-id="8fb80-689">0x01</span></span><br /><span data-ttu-id="8fb80-690">0x02</span><span class="sxs-lookup"><span data-stu-id="8fb80-690">0x02</span></span> | <span data-ttu-id="8fb80-691">**Идентификатор компилятора**</span><span class="sxs-lookup"><span data-stu-id="8fb80-691">**Compiler ID**</span></span><br /><span data-ttu-id="8fb80-692">IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-692">IAR</span></span><br /><span data-ttu-id="8fb80-693">ARM</span><span class="sxs-lookup"><span data-stu-id="8fb80-693">ARM</span></span><br /><span data-ttu-id="8fb80-694">GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-694">GNU</span></span> |

#### <a name="module-linker-for-cortex-m4-using-iar"></a><span data-ttu-id="8fb80-695">Компоновщик модулей для Cortex-M4 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-695">Module linker for Cortex-M4 using IAR</span></span>

```c
/*###ICF### Section handled by ICF editor, don't touch! ****/
/*-Editor annotation file-*/
/* IcfEditorFile="$TOOLKIT_DIR$\config\ide\IcfEditor\a_v1_0.xml" */
/*-Specials-*/
define symbol __ICFEDIT_intvec_start__ = 0x0;
/*-Memory Regions-*/
define symbol __ICFEDIT_region_ROM_start__ = 0x080f0000;
define symbol __ICFEDIT_region_ROM_end__   = 0x080fffff;
define symbol __ICFEDIT_region_RAM_start__ = 0x64002800;
define symbol __ICFEDIT_region_RAM_end__   = 0x64100000;
/*-Sizes-*/
define symbol __ICFEDIT_size_cstack__   = 0;
define symbol __ICFEDIT_size_svcstack__ = 0;
define symbol __ICFEDIT_size_irqstack__ = 0;
define symbol __ICFEDIT_size_fiqstack__ = 0;
define symbol __ICFEDIT_size_undstack__ = 0;
define symbol __ICFEDIT_size_abtstack__ = 0;
define symbol __ICFEDIT_size_heap__     = 0x1000;
/**** End of ICF editor section. ###ICF###*/

define memory mem with size = 4G;
define region ROM_region   = mem:[from __ICFEDIT_region_ROM_start__   to __ICFEDIT_region_ROM_end__];
define region RAM_region   = mem:[from __ICFEDIT_region_RAM_start__   to __ICFEDIT_region_RAM_end__];

//define block CSTACK    with alignment = 8, size = __ICFEDIT_size_cstack__   { };
//define block SVC_STACK with alignment = 8, size = __ICFEDIT_size_svcstack__ { };
//define block IRQ_STACK with alignment = 8, size = __ICFEDIT_size_irqstack__ { };
//define block FIQ_STACK with alignment = 8, size = __ICFEDIT_size_fiqstack__ { };
//define block UND_STACK with alignment = 8, size = __ICFEDIT_size_undstack__ { };
//define block ABT_STACK with alignment = 8, size = __ICFEDIT_size_abtstack__ { };
define block HEAP      with alignment = 8, size = __ICFEDIT_size_heap__     { };

initialize by copy { readwrite };
do not initialize  { section .noinit };

//place at address mem:__ICFEDIT_intvec_start__ { readonly section .intvec };

define movable block ROPI with alignment = 4, fixed order
{
  ro object txm_module_preamble_stm32f4xx.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base
{
  rw,
  block HEAP
};

place in ROM_region   { block ROPI };
place in RAM_region   { block RWPI };
```

#### <a name="building-modules-for-cortex-m4-using-iar"></a><span data-ttu-id="8fb80-696">Создание модулей для Cortex-M4 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-696">Building Modules for Cortex-M4 using IAR</span></span>

<span data-ttu-id="8fb80-697">Предоставлен пример рабочей области.</span><span class="sxs-lookup"><span data-stu-id="8fb80-697">An example workspace is provided.</span></span> <span data-ttu-id="8fb80-698">Можно создать библиотеку ThreadX, библиотеку модулей ThreadX, проект демонстрационного модуля и проект демонстрационного диспетчера модулей.</span><span class="sxs-lookup"><span data-stu-id="8fb80-698">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m4-using-iar"></a><span data-ttu-id="8fb80-699">Определение расширения потоков для Cortex-M4 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-699">Thread extension definition for Cortex-M4 using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                ULONG   tx_thread_module_saved_lr;              \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;             \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-cortex-m4-using-iar"></a><span data-ttu-id="8fb80-700">Создание диспетчера модулей для Cortex-M4 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-700">Building Module Manager for Cortex-M4 using IAR</span></span>

<span data-ttu-id="8fb80-701">Предоставлен пример рабочей области.</span><span class="sxs-lookup"><span data-stu-id="8fb80-701">An example workspace is provided.</span></span> <span data-ttu-id="8fb80-702">Можно создать библиотеку ThreadX, библиотеку модулей ThreadX, проект демонстрационного модуля и проект демонстрационного диспетчера модулей.</span><span class="sxs-lookup"><span data-stu-id="8fb80-702">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m4-using-iar"></a><span data-ttu-id="8fb80-703">Атрибуты API включения внешней памяти для Cortex-M4 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-703">Attributes for external memory enable API for Cortex-M4 using IAR</span></span>

<span data-ttu-id="8fb80-704">Модуль всегда имеет доступ на чтение к общей памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-704">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="8fb80-705">Параметр атрибута</span><span class="sxs-lookup"><span data-stu-id="8fb80-705">Attribute parameter</span></span> | <span data-ttu-id="8fb80-706">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-706">Meaning</span></span> |
|---|---|
| <span data-ttu-id="8fb80-707">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="8fb80-707">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="8fb80-708">Доступ для записи.</span><span class="sxs-lookup"><span data-stu-id="8fb80-708">Write access</span></span> |

## <a name="cortex-m7-processor"></a><span data-ttu-id="8fb80-709">Процессор Cortex-M7</span><span class="sxs-lookup"><span data-stu-id="8fb80-709">Cortex-M7 processor</span></span>

### <a name="cortex-m7-using-ac5"></a><span data-ttu-id="8fb80-710">Cortex-M7 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-710">Cortex-M7 using AC5</span></span>

#### <a name="module-preamble-for-cortex-m7-using-ac5"></a><span data-ttu-id="8fb80-711">Начальная часть модуля для Cortex-M7 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-711">Module preamble for Cortex-M7 using AC5</span></span>

```c
    AREA Init, CODE, READONLY

    PRESERVE8

    ; Define public symbols

    EXPORT __txm_module_preamble


    ; Define application-specific start/stop entry points for the module

    EXTERN demo_module_start


    ; Define common external references

    IMPORT  _txm_module_thread_shell_entry
    IMPORT  _txm_module_callback_request_thread_entry
    IMPORT  |Image$$ER_RO$$Length|
    IMPORT  |Image$$ER_RW$$Length|
    IMPORT  |Image$$ER_RW$$RW$$Length|
    IMPORT  |Image$$ER_RW$$ZI$$Length|
    IMPORT  |Image$$ER_ZI$$ZI$$Length|

__txm_module_preamble
    DCD     0x4D4F4455                                          ; Module ID
    DCD     0x5                                                 ; Module Major Version
    DCD     0x6                                                 ; Module Minor Version
    DCD     32                                                  ; Module Preamble Size in 32-bit words
    DCD     0x12345678                                          ; Module ID (application defined)
    DCD     0x01000007                                          ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bit 0:  0 -> Privileged mode execution
                                                                ;           1 -> User mode execution
                                                                ;   Bit 1:  0 -> No MPU protection
                                                                ;           1 -> MPU protection (must have user mode selected)
                                                                ;   Bit 2:  0 -> Disable shared/external memory access
                                                                ;           1 -> Enable shared/external memory access
    DCD     _txm_module_thread_shell_entry - __txm_module_preamble              ; Module Shell Entry Point
    DCD     demo_module_start - __txm_module_preamble           ; Module Start Thread Entry Point
    DCD     0                                                   ; Module Stop Thread Entry Point
    DCD     1                                                   ; Module Start/Stop Thread Priority
    DCD     1024                                                ; Module Start/Stop Thread Stack Size
    DCD     _txm_module_callback_request_thread_entry - __txm_module_preamble   ; Module Callback Thread Entry
    DCD     1                                                   ; Module Callback Thread Priority
    DCD     1024                                                ; Module Callback Thread Stack Size
    DCD     |Image$$ER_RO$$Length| + |Image$$ER_RW$$Length|         ; Module Code Size
    DCD     |Image$$ER_RW$$Length| + |Image$$ER_ZI$$ZI$$Length| ; Module Data Size
    DCD     0                                                   ; Reserved 0
    DCD     0                                                   ; Reserved 1
    DCD     0                                                   ; Reserved 2
    DCD     0                                                   ; Reserved 3
    DCD     0                                                   ; Reserved 4
    DCD     0                                                   ; Reserved 5
    DCD     0                                                   ; Reserved 6
    DCD     0                                                   ; Reserved 7
    DCD     0                                                   ; Reserved 8
    DCD     0                                                   ; Reserved 9
    DCD     0                                                   ; Reserved 10
    DCD     0                                                   ; Reserved 11
    DCD     0                                                   ; Reserved 12
    DCD     0                                                   ; Reserved 13
    DCD     0                                                   ; Reserved 14
    DCD     0                                                   ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-m7-using-ac5"></a><span data-ttu-id="8fb80-712">Свойства модуля для Cortex-M7 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-712">Module properties for Cortex-M7 using AC5</span></span>

| <span data-ttu-id="8fb80-713">bit</span><span class="sxs-lookup"><span data-stu-id="8fb80-713">Bit</span></span> | <span data-ttu-id="8fb80-714">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-714">Value</span></span> | <span data-ttu-id="8fb80-715">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-715">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="8fb80-716">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-716">0</span></span> | <span data-ttu-id="8fb80-717">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-717">0</span></span><br /><span data-ttu-id="8fb80-718">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-718">1</span></span> | <span data-ttu-id="8fb80-719">Выполнение в привилегированном режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-719">Privileged mode execution</span></span><br /><span data-ttu-id="8fb80-720">Выполнение в пользовательском режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-720">User mode execution</span></span> |
| <span data-ttu-id="8fb80-721">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-721">1</span></span> | <span data-ttu-id="8fb80-722">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-722">0</span></span><br /><span data-ttu-id="8fb80-723">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-723">1</span></span> | <span data-ttu-id="8fb80-724">Без защиты MPU.</span><span class="sxs-lookup"><span data-stu-id="8fb80-724">No MPU protection</span></span><br /><span data-ttu-id="8fb80-725">Защита MPU (необходимо выбрать пользовательский режим).</span><span class="sxs-lookup"><span data-stu-id="8fb80-725">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="8fb80-726">2</span><span class="sxs-lookup"><span data-stu-id="8fb80-726">2</span></span> | <span data-ttu-id="8fb80-727">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-727">0</span></span><br /><span data-ttu-id="8fb80-728">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-728">1</span></span> | <span data-ttu-id="8fb80-729">Отключение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-729">Disable shared/external memory access</span></span><br /><span data-ttu-id="8fb80-730">Включение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-730">Enable shared/external memory access</span></span> |
| <span data-ttu-id="8fb80-731">[23–3]</span><span class="sxs-lookup"><span data-stu-id="8fb80-731">[23-3]</span></span> | <span data-ttu-id="8fb80-732">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-732">0</span></span> | <span data-ttu-id="8fb80-733">Зарезервировано</span><span class="sxs-lookup"><span data-stu-id="8fb80-733">Reserved</span></span>
| <span data-ttu-id="8fb80-734">[31–24]</span><span class="sxs-lookup"><span data-stu-id="8fb80-734">[31-24]</span></span> | <br /><span data-ttu-id="8fb80-735">0x00</span><span class="sxs-lookup"><span data-stu-id="8fb80-735">0x00</span></span><br /><span data-ttu-id="8fb80-736">0x01</span><span class="sxs-lookup"><span data-stu-id="8fb80-736">0x01</span></span><br /><span data-ttu-id="8fb80-737">0x02</span><span class="sxs-lookup"><span data-stu-id="8fb80-737">0x02</span></span> | <span data-ttu-id="8fb80-738">**Идентификатор компилятора**</span><span class="sxs-lookup"><span data-stu-id="8fb80-738">**Compiler ID**</span></span><br /><span data-ttu-id="8fb80-739">IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-739">IAR</span></span><br /><span data-ttu-id="8fb80-740">ARM</span><span class="sxs-lookup"><span data-stu-id="8fb80-740">ARM</span></span><br /><span data-ttu-id="8fb80-741">GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-741">GNU</span></span> |

#### <a name="module-linker-for-cortex-m7-using-ac5"></a><span data-ttu-id="8fb80-742">Компоновщик модулей для Cortex-M7 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-742">Module linker for Cortex-M7 using AC5</span></span>

<span data-ttu-id="8fb80-743">Пример на основе командной строки без файла компоновщика.</span><span class="sxs-lookup"><span data-stu-id="8fb80-743">Built on command-line, no linker file example.</span></span>

#### <a name="building-modules-for-cortex-m7-using-ac5"></a><span data-ttu-id="8fb80-744">Создание модулей для Cortex-M7 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-744">Building Modules for Cortex-M7 using AC5</span></span>

<span data-ttu-id="8fb80-745">Простой пример создания модуля Cortex-M7 с поддержкой AC5 с помощью командной строки:</span><span class="sxs-lookup"><span data-stu-id="8fb80-745">A simple command-line example for building a Cortex-M7 module using AC5:</span></span>

```dos
armasm -g --cpu=cortex-m7 --fpu=softvfp --apcs=/interwork/ropi/rwpi txm_module_preamble.s
armcc  -g --cpu=cortex-m7 --fpu=softvfp -c --apcs=/interwork/ropi/rwpi --lower_ropi -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module.c
armlink -d -o sample_threadx_module.axf --elf --ro 0 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list sample_threadx_module.map txm_module_preamble.o sample_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-m7-using-ac5"></a><span data-ttu-id="8fb80-746">Определение расширения потоков для Cortex-M7 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-746">Thread extension definition for Cortex-M7 using AC5</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                ULONG   tx_thread_module_saved_lr;              \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m7-using-ac5"></a><span data-ttu-id="8fb80-747">Создание диспетчера модулей для Cortex-M7 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-747">Building Module Manager for Cortex-M7 using AC5</span></span>

<span data-ttu-id="8fb80-748">Простой пример создания диспетчера модулей Cortex-M7 с поддержкой AC5 с помощью командной строки:</span><span class="sxs-lookup"><span data-stu-id="8fb80-748">A simple command-line example for building a Cortex-M7 module manager using AC5:</span></span>

```dos
armasm -g --cpu=cortex-m7 --fpu=softvfp --apcs=interwork tx_initialize_low_level.s
armcc -g --cpu=cortex-m7 --fpu=softvfp -c demo_threadx_module_manager.c
armcc -g --cpu=cortex-m7 --fpu=softvfp -c module_code.c
armlink -d -o demo_threadx_module_manager.axf --elf --ro 0x00000000 --first tx_initialize_low_level.o(RESET) --remove --map --symbols --list demo_threadx_module_manager.map tx_initialize_low_level.o demo_threadx_module_manager.o module_code.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m7-using-ac5"></a><span data-ttu-id="8fb80-749">Атрибуты API включения внешней памяти для Cortex-M7 с поддержкой AC5</span><span class="sxs-lookup"><span data-stu-id="8fb80-749">Attributes for external memory enable API for Cortex-M7 using AC5</span></span>

### <a name="cortex-m7-using-ac6"></a><span data-ttu-id="8fb80-750">Cortex-M7 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-750">Cortex-M7 using AC6</span></span>

#### <a name="module-properties-for-cortex-m7-using-ac6"></a><span data-ttu-id="8fb80-751">Свойства модуля для Cortex-M7 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-751">Module properties for Cortex-M7 using AC6</span></span>

| <span data-ttu-id="8fb80-752">bit</span><span class="sxs-lookup"><span data-stu-id="8fb80-752">Bit</span></span> | <span data-ttu-id="8fb80-753">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-753">Value</span></span> | <span data-ttu-id="8fb80-754">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-754">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="8fb80-755">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-755">0</span></span> | <span data-ttu-id="8fb80-756">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-756">0</span></span><br /><span data-ttu-id="8fb80-757">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-757">1</span></span> | <span data-ttu-id="8fb80-758">Выполнение в привилегированном режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-758">Privileged mode execution</span></span><br /><span data-ttu-id="8fb80-759">Выполнение в пользовательском режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-759">User mode execution</span></span> |
| <span data-ttu-id="8fb80-760">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-760">1</span></span> | <span data-ttu-id="8fb80-761">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-761">0</span></span><br /><span data-ttu-id="8fb80-762">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-762">1</span></span> | <span data-ttu-id="8fb80-763">Без защиты MPU.</span><span class="sxs-lookup"><span data-stu-id="8fb80-763">No MPU protection</span></span><br /><span data-ttu-id="8fb80-764">Защита MPU (необходимо выбрать пользовательский режим).</span><span class="sxs-lookup"><span data-stu-id="8fb80-764">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="8fb80-765">2</span><span class="sxs-lookup"><span data-stu-id="8fb80-765">2</span></span> | <span data-ttu-id="8fb80-766">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-766">0</span></span><br /><span data-ttu-id="8fb80-767">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-767">1</span></span> | <span data-ttu-id="8fb80-768">Отключение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-768">Disable shared/external memory access</span></span><br /><span data-ttu-id="8fb80-769">Включение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-769">Enable shared/external memory access</span></span> |
| <span data-ttu-id="8fb80-770">[23–3]</span><span class="sxs-lookup"><span data-stu-id="8fb80-770">[23-3]</span></span> | <span data-ttu-id="8fb80-771">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-771">0</span></span> | <span data-ttu-id="8fb80-772">Зарезервировано</span><span class="sxs-lookup"><span data-stu-id="8fb80-772">Reserved</span></span>
| <span data-ttu-id="8fb80-773">[31–24]</span><span class="sxs-lookup"><span data-stu-id="8fb80-773">[31-24]</span></span> | <br /><span data-ttu-id="8fb80-774">0x00</span><span class="sxs-lookup"><span data-stu-id="8fb80-774">0x00</span></span><br /><span data-ttu-id="8fb80-775">0x01</span><span class="sxs-lookup"><span data-stu-id="8fb80-775">0x01</span></span><br /><span data-ttu-id="8fb80-776">0x02</span><span class="sxs-lookup"><span data-stu-id="8fb80-776">0x02</span></span> | <span data-ttu-id="8fb80-777">**Идентификатор компилятора**</span><span class="sxs-lookup"><span data-stu-id="8fb80-777">**Compiler ID**</span></span><br /><span data-ttu-id="8fb80-778">IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-778">IAR</span></span><br /><span data-ttu-id="8fb80-779">ARM</span><span class="sxs-lookup"><span data-stu-id="8fb80-779">ARM</span></span><br /><span data-ttu-id="8fb80-780">GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-780">GNU</span></span> |

#### <a name="module-linker-for-cortex-m7-using-ac6"></a><span data-ttu-id="8fb80-781">Компоновщик модулей для Cortex-M7 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-781">Module linker for Cortex-M7 using AC6</span></span>

<span data-ttu-id="8fb80-782">Файл компоновщика не используется.</span><span class="sxs-lookup"><span data-stu-id="8fb80-782">No linker file is used.</span></span> <span data-ttu-id="8fb80-783">Ознакомьтесь с параметрами проекта.</span><span class="sxs-lookup"><span data-stu-id="8fb80-783">See project settings.</span></span>

#### <a name="building-modules-for-cortex-m7-using-ac6"></a><span data-ttu-id="8fb80-784">Создание модулей для Cortex-M7 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-784">Building Modules for Cortex-M7 using AC6</span></span>

<span data-ttu-id="8fb80-785">Предоставлен пример рабочей области.</span><span class="sxs-lookup"><span data-stu-id="8fb80-785">An example workspace is provided.</span></span> <span data-ttu-id="8fb80-786">Можно создать библиотеку ThreadX, библиотеку модулей ThreadX, пример проекта модуля и пример проекта диспетчера модулей.</span><span class="sxs-lookup"><span data-stu-id="8fb80-786">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m7-using-ac6"></a><span data-ttu-id="8fb80-787">Определение расширения потоков для Cortex-M7 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-787">Thread extension definition for Cortex-M7 using AC6</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m7-using-ac6"></a><span data-ttu-id="8fb80-788">Создание диспетчера модулей для Cortex-M7 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-788">Building Module Manager for Cortex-M7 using AC6</span></span>

<span data-ttu-id="8fb80-789">Предоставлен пример рабочей области.</span><span class="sxs-lookup"><span data-stu-id="8fb80-789">An example workspace is provided.</span></span> <span data-ttu-id="8fb80-790">Можно создать библиотеку ThreadX, библиотеку модулей ThreadX, пример проекта модуля и пример проекта диспетчера модулей.</span><span class="sxs-lookup"><span data-stu-id="8fb80-790">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m7-using-ac6"></a><span data-ttu-id="8fb80-791">Атрибуты API включения внешней памяти для Cortex-M7 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-791">Attributes for external memory enable API for Cortex-M7 using AC6</span></span>

<span data-ttu-id="8fb80-792">Модуль всегда имеет доступ на чтение к общей памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-792">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="8fb80-793">Параметр атрибута</span><span class="sxs-lookup"><span data-stu-id="8fb80-793">Attribute parameter</span></span> | <span data-ttu-id="8fb80-794">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-794">Meaning</span></span> |
|---|---|
| <span data-ttu-id="8fb80-795">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="8fb80-795">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="8fb80-796">Доступ для записи.</span><span class="sxs-lookup"><span data-stu-id="8fb80-796">Write access</span></span> |

### <a name="cortex-m7-using-gnu"></a><span data-ttu-id="8fb80-797">Cortex-M7 с поддержкой GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-797">Cortex-M7 using GNU</span></span>

#### <a name="module-properties-for-cortex-m7-using-gnu"></a><span data-ttu-id="8fb80-798">Свойства модуля для Cortex-M7 с поддержкой GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-798">Module properties for Cortex-M7 using GNU</span></span>

| <span data-ttu-id="8fb80-799">bit</span><span class="sxs-lookup"><span data-stu-id="8fb80-799">Bit</span></span> | <span data-ttu-id="8fb80-800">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-800">Value</span></span> | <span data-ttu-id="8fb80-801">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-801">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="8fb80-802">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-802">0</span></span> | <span data-ttu-id="8fb80-803">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-803">0</span></span><br /><span data-ttu-id="8fb80-804">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-804">1</span></span> | <span data-ttu-id="8fb80-805">Выполнение в привилегированном режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-805">Privileged mode execution</span></span><br /><span data-ttu-id="8fb80-806">Выполнение в пользовательском режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-806">User mode execution</span></span> |
| <span data-ttu-id="8fb80-807">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-807">1</span></span> | <span data-ttu-id="8fb80-808">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-808">0</span></span><br /><span data-ttu-id="8fb80-809">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-809">1</span></span> | <span data-ttu-id="8fb80-810">Без защиты MPU.</span><span class="sxs-lookup"><span data-stu-id="8fb80-810">No MPU protection</span></span><br /><span data-ttu-id="8fb80-811">Защита MPU (необходимо выбрать пользовательский режим).</span><span class="sxs-lookup"><span data-stu-id="8fb80-811">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="8fb80-812">2</span><span class="sxs-lookup"><span data-stu-id="8fb80-812">2</span></span> | <span data-ttu-id="8fb80-813">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-813">0</span></span><br /><span data-ttu-id="8fb80-814">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-814">1</span></span> | <span data-ttu-id="8fb80-815">Отключение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-815">Disable shared/external memory access</span></span><br /><span data-ttu-id="8fb80-816">Включение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-816">Enable shared/external memory access</span></span> |
| <span data-ttu-id="8fb80-817">[23–3]</span><span class="sxs-lookup"><span data-stu-id="8fb80-817">[23-3]</span></span> | <span data-ttu-id="8fb80-818">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-818">0</span></span> | <span data-ttu-id="8fb80-819">Зарезервировано</span><span class="sxs-lookup"><span data-stu-id="8fb80-819">Reserved</span></span>
| <span data-ttu-id="8fb80-820">[31–24]</span><span class="sxs-lookup"><span data-stu-id="8fb80-820">[31-24]</span></span> | <br /><span data-ttu-id="8fb80-821">0x00</span><span class="sxs-lookup"><span data-stu-id="8fb80-821">0x00</span></span><br /><span data-ttu-id="8fb80-822">0x01</span><span class="sxs-lookup"><span data-stu-id="8fb80-822">0x01</span></span><br /><span data-ttu-id="8fb80-823">0x02</span><span class="sxs-lookup"><span data-stu-id="8fb80-823">0x02</span></span> | <span data-ttu-id="8fb80-824">**Идентификатор компилятора**</span><span class="sxs-lookup"><span data-stu-id="8fb80-824">**Compiler ID**</span></span><br /><span data-ttu-id="8fb80-825">IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-825">IAR</span></span><br /><span data-ttu-id="8fb80-826">ARM</span><span class="sxs-lookup"><span data-stu-id="8fb80-826">ARM</span></span><br /><span data-ttu-id="8fb80-827">GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-827">GNU</span></span> |

#### <a name="module-linker-for-cortex-m7-using-gnu"></a><span data-ttu-id="8fb80-828">Компоновщик модулей для Cortex-M7 с поддержкой GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-828">Module linker for Cortex-M7 using GNU</span></span>

```c
MEMORY
{
  FLASH (rx) : ORIGIN = 0x00030000, LENGTH = 0x00010000
  RAM   (wx) : ORIGIN = 0, LENGTH = 0x00100000
}


SECTIONS
{
  __FLASH_segment_start__ = 0x00030000;
  __FLASH_segment_end__   = 0x00040000;
  __RAM_segment_start__   = 0;
  __RAM_segment_end__     = 0x8000;

  __HEAPSIZE__ = 128;

  __preamble_load_start__ = __FLASH_segment_start__;
  .preamble __FLASH_segment_start__ : AT(__FLASH_segment_start__)
  {
    __preamble_start__ = .;
    *(.preamble .preamble.*)
  }
  __preamble_end__ = __preamble_start__ + SIZEOF(.preamble);

  __dynsym_load_start__ =  ALIGN(__preamble_end__ , 4);
  .dynsym ALIGN(__dynsym_load_start__ , 4) : AT(ALIGN(__dynsym_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynsym))
    KEEP (*(.dynsym*))
    . = ALIGN(4);
  }
  __dynsym_end__ = __dynsym_load_start__ + SIZEOF(.dynsym);

  __dynstr_load_start__ =  ALIGN(__dynsym_end__ , 4);
  .dynstr ALIGN(__dynstr_load_start__ , 4) : AT(ALIGN(__dynstr_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynstr))
    KEEP (*(.dynstr*))
    . = ALIGN(4);
  }
  __dynstr_end__ = __dynstr_load_start__ + SIZEOF(.dynstr);

  __reldyn_load_start__ =  ALIGN(__dynstr_end__ , 4);
  .rel.dyn ALIGN(__reldyn_load_start__ , 4) : AT(ALIGN(__reldyn_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.dyn))
    KEEP (*(.rel.dyn*))
    . = ALIGN(4);
  }
  __reldyn_end__ = __reldyn_load_start__ + SIZEOF(.rel.dyn);

  __relplt_load_start__ =  ALIGN(__reldyn_end__ , 4);
  .rel.plt ALIGN(__relplt_load_start__ , 4) : AT(ALIGN(__relplt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.plt))
    KEEP (*(.rel.plt*))
    . = ALIGN(4);
  }
  __relplt_end__ = __relplt_load_start__ + SIZEOF(.rel.plt);

  __plt_load_start__ =  ALIGN(__relplt_end__ , 4);
  .plt ALIGN(__plt_load_start__ , 4) : AT(ALIGN(__plt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.plt))
    KEEP (*(.plt*))
    . = ALIGN(4);
  }
  __plt_end__ = __plt_load_start__ + SIZEOF(.plt);

  __interp_load_start__ =  ALIGN(__plt_end__ , 4);
  .interp ALIGN(__interp_load_start__ , 4) : AT(ALIGN(__interp_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.interp))
    KEEP (*(.interp*))
    . = ALIGN(4);
  }
  __interp_end__ = __interp_load_start__ + SIZEOF(.interp);

  __hash_load_start__ =  ALIGN(__interp_end__ , 4);
  .hash ALIGN(__hash_load_start__ , 4) : AT(ALIGN(__hash_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.hash))
    KEEP (*(.hash*))
    . = ALIGN(4);
  }
  __hash_end__ = __hash_load_start__ + SIZEOF(.hash);

  __text_load_start__ =  ALIGN(__hash_end__ , 4);
  .text ALIGN(__text_load_start__ , 4) : AT(ALIGN(__text_load_start__, 4))
  {
    __text_start__ = .;
    *(.text .text.* .glue_7t .glue_7 .gnu.linkonce.t.* .gcc_except_table  )
  }
  __text_end__ = __text_start__ + SIZEOF(.text);

  __dtors_load_start__ = ALIGN(__text_end__ , 4);
  .dtors ALIGN(__text_end__ , 4) : AT(ALIGN(__text_end__ , 4))
  {
    __dtors_start__ = .;
    KEEP (*(SORT(.dtors.*))) KEEP (*(.dtors))
  }
  __dtors_end__ = __dtors_start__ + SIZEOF(.dtors);

  __ctors_load_start__ = ALIGN(__dtors_end__ , 4);
  .ctors ALIGN(__dtors_end__ , 4) : AT(ALIGN(__dtors_end__ , 4))
  {
    __ctors_start__ = .;
    KEEP (*(SORT(.ctors.*))) KEEP (*(.ctors))
  }
  __ctors_end__ = __ctors_start__ + SIZEOF(.ctors);

  __got_load_start__ = ALIGN(__ctors_end__ , 4);
  .got ALIGN(__ctors_end__ , 4) : AT(ALIGN(__ctors_end__ , 4))
  {
    . = ALIGN(4);
    _sgot = .;
    KEEP (*(.got))
    KEEP (*(.got*))
    . = ALIGN(4);
    _egot = .;
  } 
  __got_end__ =  __got_load_start__ + SIZEOF(.got);

  __rodata_load_start__ = ALIGN(__got_end__ , 4);
  .rodata ALIGN(__got_end__ , 4) : AT(ALIGN(__got_end__ , 4))
  {
    __rodata_start__ = .;
    *(.rodata .rodata.* .gnu.linkonce.r.*)
  }
  __rodata_end__ = __rodata_start__ + SIZEOF(.rodata);
 
  __code_size__ =  __rodata_end__ - __FLASH_segment_start__;

  __fast_load_start__ = ALIGN(__rodata_end__ , 4);

  __fast_load_end__ = __fast_load_start__ + SIZEOF(.fast);

  __new_got_start__ = ALIGN(__RAM_segment_start__ , 4);

  __new_got_end__ =  __new_got_start__ + SIZEOF(.got);

  .fast ALIGN(__new_got_end__ , 4) : AT(ALIGN(__rodata_end__ , 4))
  {
    __fast_start__ = .;
    *(.fast .fast.*)
  }
  __fast_end__ = __fast_start__ + SIZEOF(.fast);

  .fast_run ALIGN(__fast_end__ , 4) (NOLOAD) :
  {
    __fast_run_start__ = .;
    . = MAX(__fast_run_start__ + SIZEOF(.fast), .);
  }
  __fast_run_end__ = __fast_run_start__ + SIZEOF(.fast_run);

  __data_load_start__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4);
  .data ALIGN(__fast_run_end__ , 4) : AT(ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4))
  {
    __data_start__ = .;
    *(.data .data.* .gnu.linkonce.d.*)
  }
  __data_end__ = __data_start__ + SIZEOF(.data);

  __data_load_end__ = __data_load_start__ + SIZEOF(.data);

  __FLASH_segment_used_end__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4) + SIZEOF(.data);

  .data_run ALIGN(__fast_run_end__ , 4) (NOLOAD) :
  {
    __data_run_start__ = .;
    . = MAX(__data_run_start__ + SIZEOF(.data), .);
  }
  __data_run_end__ = __data_run_start__ + SIZEOF(.data_run);

  __bss_load_start__ = ALIGN(__data_run_end__ , 4);
  .bss ALIGN(__data_run_end__ , 4) (NOLOAD) : AT(ALIGN(__data_run_end__ , 4))
  {
    __bss_start__ = .;
    *(.bss .bss.* .gnu.linkonce.b.*) *(COMMON)
  }
  __bss_end__ = __bss_start__ + SIZEOF(.bss);

  __non_init_load_start__ = ALIGN(__bss_end__ , 4);
  .non_init ALIGN(__bss_end__ , 4) (NOLOAD) : AT(ALIGN(__bss_end__ , 4))
  {
    __non_init_start__ = .;
    *(.non_init .non_init.*)
  }
  __non_init_end__ = __non_init_start__ + SIZEOF(.non_init);

  __heap_load_start__ = ALIGN(__non_init_end__ , 4);
  .heap ALIGN(__non_init_end__ , 4) (NOLOAD) : AT(ALIGN(__non_init_end__ , 4))
  {
    __heap_start__ = .;
    *(.heap)
    . = ALIGN(MAX(__heap_start__ + __HEAPSIZE__ , .), 4);
  }
  __heap_end__ = __heap_start__ + SIZEOF(.heap);

  __data_size__ =  __heap_end__ - __RAM_segment_start__;

}
```

#### <a name="building-modules-for-cortex-m7-using-gnu"></a><span data-ttu-id="8fb80-829">Создание модулей для Cortex-M7 с поддержкой GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-829">Building Modules for Cortex-M7 using GNU</span></span>

<span data-ttu-id="8fb80-830">Ознакомьтесь с файлом build_threadx_module_sample.bat.</span><span class="sxs-lookup"><span data-stu-id="8fb80-830">See build_threadx_module_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base txm_module_preamble.s
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base gcc_setup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module.c
arm-none-eabi-ld -A cortex-m7 -T sample_threadx_module.ld txm_module_preamble.o gcc_setup.o sample_threadx_module.o -e _txm_module_thread_shell_entry txm.a -o sample_threadx_module.axf -M > sample_threadx_module.map
```

#### <a name="thread-extension-definition-for-cortex-m7-using-gnu"></a><span data-ttu-id="8fb80-831">Определение расширения потоков для Cortex-M7 с поддержкой GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-831">Thread extension definition for Cortex-M7 using GNU</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m7-using-gnu"></a><span data-ttu-id="8fb80-832">Создание диспетчера модулей для Cortex-M7 с поддержкой GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-832">Building Module Manager for Cortex-M7 using GNU</span></span>

<span data-ttu-id="8fb80-833">Ознакомьтесь с файлом build_threadx_module_manager_sample.bat.</span><span class="sxs-lookup"><span data-stu-id="8fb80-833">See build_threadx_module_manager_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -mthumb -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module_manager.c
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -mthumb tx_simulator_startup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -mthumb cortexm_crt0.S
arm-none-eabi-gcc -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -mthumb -nostartfiles -ereset_handler -T sample_threadx.ld tx_simulator_startup.o cortexm_crt0.o sample_threadx_module_manager.o tx.a -o sample_threadx_module_manager.axf -Wl,-Map=sample_threadx_module_manager.map
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m7-using-gnu"></a><span data-ttu-id="8fb80-834">Атрибуты API включения внешней памяти для Cortex-M7 с поддержкой GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-834">Attributes for external memory enable API for Cortex-M7 using GNU</span></span>

<span data-ttu-id="8fb80-835">Модуль всегда имеет доступ на чтение к общей памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-835">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="8fb80-836">Параметр атрибута</span><span class="sxs-lookup"><span data-stu-id="8fb80-836">Attribute parameter</span></span> | <span data-ttu-id="8fb80-837">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-837">Meaning</span></span> |
|---|---|
| <span data-ttu-id="8fb80-838">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="8fb80-838">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="8fb80-839">Доступ для записи.</span><span class="sxs-lookup"><span data-stu-id="8fb80-839">Write access</span></span> |

### <a name="cortex-m7-using-iar"></a><span data-ttu-id="8fb80-840">Cortex-M7 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-840">Cortex-M7 using IAR</span></span>

#### <a name="module-preamble-for-cortex-m7-using-iar"></a><span data-ttu-id="8fb80-841">Начальная часть модуля для Cortex-M7 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-841">Module preamble for Cortex-M7 using IAR</span></span>

```c
    SECTION .text:CODE

    AAPCS INTERWORK, ROPI, RWPI_COMPATIBLE,  VFP_COMPATIBLE
    PRESERVE8

    /* Define public symbols.  */

    PUBLIC __txm_module_preamble


    /* Define application-specific start/stop entry points for the module.  */

    EXTERN demo_module_start


    /* Define common external references.  */

    EXTERN  _txm_module_thread_shell_entry
    EXTERN  _txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        ; Module ID
    DC32      0x5                                               ; Module Major Version
    DC32      0x6                                               ; Module Minor Version
    DC32      32                                                ; Module Preamble Size in 32-bit words
    DC32      0x12345678                                        ; Module ID (application defined)
    DC32      0x00000007                                        ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bits 23-3: Reserved
                                                                ;   Bit 2:  0 -> Disable shared/external memory access
                                                                ;           1 -> Enable shared/external memory access
                                                                ;   Bit 1:  0 -> No MPU protection
                                                                ;           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                ;   Bit 0:  0 -> Privileged mode execution
                                                                ;           1 -> User mode execution


    DC32      _txm_module_thread_shell_entry - . - 0            ; Module Shell Entry Point
    DC32      demo_module_start - . - 0                         ; Module Start Thread Entry Point
    DC32      0                                                 ; Module Stop Thread Entry Point
    DC32      1                                                 ; Module Start/Stop Thread Priority
    DC32      1024                                              ; Module Start/Stop Thread Stack Size
    DC32      _txm_module_callback_request_thread_entry - . - 0 ; Module Callback Thread Entry
    DC32      1                                                 ; Module Callback Thread Priority
    DC32      1024                                              ; Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      ; Module Code Size
    DC32      RWPI$$Length                                      ; Module Data Size
    DC32      0                                                 ; Reserved 0
    DC32      0                                                 ; Reserved 1
    DC32      0                                                 ; Reserved 2
    DC32      0                                                 ; Reserved 3
    DC32      0                                                 ; Reserved 4
    DC32      0                                                 ; Reserved 5
    DC32      0                                                 ; Reserved 6
    DC32      0                                                 ; Reserved 7
    DC32      0                                                 ; Reserved 8  
    DC32      0                                                 ; Reserved 9
    DC32      0                                                 ; Reserved 10
    DC32      0                                                 ; Reserved 11
    DC32      0                                                 ; Reserved 12
    DC32      0                                                 ; Reserved 13
    DC32      0                                                 ; Reserved 14
    DC32      0                                                 ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-m7-using-iar"></a><span data-ttu-id="8fb80-842">Свойства модуля для Cortex-M7 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-842">Module properties for Cortex-M7 using IAR</span></span>

| <span data-ttu-id="8fb80-843">bit</span><span class="sxs-lookup"><span data-stu-id="8fb80-843">Bit</span></span> | <span data-ttu-id="8fb80-844">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-844">Value</span></span> | <span data-ttu-id="8fb80-845">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-845">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="8fb80-846">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-846">0</span></span> | <span data-ttu-id="8fb80-847">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-847">0</span></span><br /><span data-ttu-id="8fb80-848">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-848">1</span></span> | <span data-ttu-id="8fb80-849">Выполнение в привилегированном режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-849">Privileged mode execution</span></span><br /><span data-ttu-id="8fb80-850">Выполнение в пользовательском режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-850">User mode execution</span></span> |
| <span data-ttu-id="8fb80-851">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-851">1</span></span> | <span data-ttu-id="8fb80-852">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-852">0</span></span><br /><span data-ttu-id="8fb80-853">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-853">1</span></span> | <span data-ttu-id="8fb80-854">Без защиты MPU.</span><span class="sxs-lookup"><span data-stu-id="8fb80-854">No MPU protection</span></span><br /><span data-ttu-id="8fb80-855">Защита MPU (необходимо выбрать пользовательский режим).</span><span class="sxs-lookup"><span data-stu-id="8fb80-855">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="8fb80-856">2</span><span class="sxs-lookup"><span data-stu-id="8fb80-856">2</span></span> | <span data-ttu-id="8fb80-857">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-857">0</span></span><br /><span data-ttu-id="8fb80-858">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-858">1</span></span> | <span data-ttu-id="8fb80-859">Отключение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-859">Disable shared/external memory access</span></span><br /><span data-ttu-id="8fb80-860">Включение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-860">Enable shared/external memory access</span></span> |
| <span data-ttu-id="8fb80-861">[23–3]</span><span class="sxs-lookup"><span data-stu-id="8fb80-861">[23-3]</span></span> | <span data-ttu-id="8fb80-862">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-862">0</span></span> | <span data-ttu-id="8fb80-863">Зарезервировано</span><span class="sxs-lookup"><span data-stu-id="8fb80-863">Reserved</span></span>
| <span data-ttu-id="8fb80-864">[31–24]</span><span class="sxs-lookup"><span data-stu-id="8fb80-864">[31-24]</span></span> | <br /><span data-ttu-id="8fb80-865">0x00</span><span class="sxs-lookup"><span data-stu-id="8fb80-865">0x00</span></span><br /><span data-ttu-id="8fb80-866">0x01</span><span class="sxs-lookup"><span data-stu-id="8fb80-866">0x01</span></span><br /><span data-ttu-id="8fb80-867">0x02</span><span class="sxs-lookup"><span data-stu-id="8fb80-867">0x02</span></span> | <span data-ttu-id="8fb80-868">**Идентификатор компилятора**</span><span class="sxs-lookup"><span data-stu-id="8fb80-868">**Compiler ID**</span></span><br /><span data-ttu-id="8fb80-869">IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-869">IAR</span></span><br /><span data-ttu-id="8fb80-870">ARM</span><span class="sxs-lookup"><span data-stu-id="8fb80-870">ARM</span></span><br /><span data-ttu-id="8fb80-871">GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-871">GNU</span></span> |

#### <a name="module-linker-for-cortex-m7-using-iar"></a><span data-ttu-id="8fb80-872">Компоновщик модулей для Cortex-M7 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-872">Module linker for Cortex-M7 using IAR</span></span>

```c
/*###ICF### Section handled by ICF editor, don't touch! ****/
/*-Editor annotation file-*/
/* IcfEditorFile="$TOOLKIT_DIR$\config\ide\IcfEditor\cortex_v1_0.xml" */
/*-Specials-*/
define symbol __ICFEDIT_intvec_start__     = 0x00400000;
/*-Memory Regions-*/
define symbol __ICFEDIT_region_RAM_start__ = 0x20450000;
define symbol __ICFEDIT_region_RAM_end__   = 0x2045f000 -1;
define symbol __ICFEDIT_region_RAM_NOCACHE_start__ = 0x2045f000;
define symbol __ICFEDIT_region_RAM_NOCACHE_end__   = 0x20460000 -1;
define symbol __ICFEDIT_region_ROM_start__ = 0x00500000;
define symbol __ICFEDIT_region_ROM_end__   = 0x00600000 -1;
define symbol __ICFEDIT_region_SDRAM_start__ = 0x70000000;
define symbol __ICFEDIT_region_SDRAM_end__   = 0x70200000 -1;

/*-Sizes-*/
define symbol __ICFEDIT_size_cstack__      = 0x2000;
define symbol __ICFEDIT_size_heap__        = 0x1000;
/**** End of ICF editor section. ###ICF###*/

define memory mem with size = 4G;
define region RAM_region    = mem:[from __ICFEDIT_region_RAM_start__ to __ICFEDIT_region_RAM_end__];
define region RAM_NOCACHE_region = mem:[from __ICFEDIT_region_RAM_NOCACHE_start__ to __ICFEDIT_region_RAM_NOCACHE_end__];
define region ROM_region    = mem:[from __ICFEDIT_region_ROM_start__ to __ICFEDIT_region_ROM_end__];
define region SDRAM_region  = mem:[from __ICFEDIT_region_SDRAM_start__ to __ICFEDIT_region_SDRAM_end__];

define block HEAP   with alignment = 8, size = __ICFEDIT_size_heap__   { };

initialize by copy { readwrite };
do not initialize  { section .noinit };

define movable block ROPI with alignment = 4, fixed order
{
  ro object txm_module_preamble.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base
{
  rw,
  block HEAP
};

place in ROM_region   { block ROPI };
place in RAM_region   { block RWPI };
```

#### <a name="building-modules-for-cortex-m7-using-iar"></a><span data-ttu-id="8fb80-873">Создание модулей для Cortex-M7 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-873">Building Modules for Cortex-M7 using IAR</span></span>

<span data-ttu-id="8fb80-874">Предоставлен пример рабочей области.</span><span class="sxs-lookup"><span data-stu-id="8fb80-874">An example workspace is provided.</span></span> <span data-ttu-id="8fb80-875">Можно создать библиотеку ThreadX, библиотеку модулей ThreadX, проект демонстрационного модуля и проект демонстрационного диспетчера модулей.</span><span class="sxs-lookup"><span data-stu-id="8fb80-875">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m7-using-iar"></a><span data-ttu-id="8fb80-876">Определение расширения потоков для Cortex-M7 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-876">Thread extension definition for Cortex-M7 using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                ULONG   tx_thread_module_saved_lr;              \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;             \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-cortex-m7-using-iar"></a><span data-ttu-id="8fb80-877">Создание диспетчера модулей для Cortex-M7 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-877">Building Module Manager for Cortex-M7 using IAR</span></span>

<span data-ttu-id="8fb80-878">Предоставлен пример рабочей области.</span><span class="sxs-lookup"><span data-stu-id="8fb80-878">An example workspace is provided.</span></span> <span data-ttu-id="8fb80-879">Можно создать библиотеку ThreadX, библиотеку модулей ThreadX, проект демонстрационного модуля и проект демонстрационного диспетчера модулей.</span><span class="sxs-lookup"><span data-stu-id="8fb80-879">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m7-using-iar"></a><span data-ttu-id="8fb80-880">Атрибуты API включения внешней памяти для Cortex-M7 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-880">Attributes for external memory enable API for Cortex-M7 using IAR</span></span>

<span data-ttu-id="8fb80-881">Модуль всегда имеет доступ на чтение к общей памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-881">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="8fb80-882">Параметр атрибута</span><span class="sxs-lookup"><span data-stu-id="8fb80-882">Attribute parameter</span></span> | <span data-ttu-id="8fb80-883">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-883">Meaning</span></span> |
|---|---|
| <span data-ttu-id="8fb80-884">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="8fb80-884">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="8fb80-885">Доступ для записи.</span><span class="sxs-lookup"><span data-stu-id="8fb80-885">Write access</span></span> |

## <a name="cortex-r4-processor"></a><span data-ttu-id="8fb80-886">Процессор Cortex-R4</span><span class="sxs-lookup"><span data-stu-id="8fb80-886">Cortex-R4 processor</span></span>

### <a name="cortex-r4-using-ac6"></a><span data-ttu-id="8fb80-887">Cortex-R4 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-887">Cortex-R4 using AC6</span></span>

#### <a name="module-preamble-for-cortex-r4-using-ac6"></a><span data-ttu-id="8fb80-888">Начальная часть модуля для Cortex-R4 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-888">Module preamble for Cortex-R4 using AC6</span></span>

```c
    .text

/* Define common external references.  */

.global     _txm_module_thread_shell_entry
.global     demo_module_start
.global     _txm_module_callback_request_thread_entry
.global     Image$$ER_RO$$Length
.global     Image$$ER_RW$$Length
.global     Image$$ER_ZI$$ZI$$Length

/* Stack aligned, ROPI and RWPI, R9 used as data offset register.  */
.eabi_attribute Tag_ABI_align_preserved, 1
.eabi_attribute Tag_ABI_PCS_RO_data, 1
.eabi_attribute Tag_ABI_PCS_R9_use,  1
.eabi_attribute Tag_ABI_PCS_RW_data, 2

__txm_module_preamble:
.word   0x4D4F4455                                          /* Module ID  */
.word   0x5                                                 /* Module Major Version  */
.word   0x3                                                 /* Module Minor Version  */
.word   32                                                  /* Module Preamble Size in 32-bit words  */
.word   0x12345678                                          /* Module ID (application defined)  */
.word   0x01000001                                          /* Module Properties where:
                                                               Bits 31-24: Compiler ID
                                                                       0 -> IAR
                                                                       1 -> RVDS/ARM
                                                                       2 -> GNU
                                                               Bits 23-1:  Reserved
                                                               Bit 0:  0 -> Privileged mode execution (no MMU protection)
                                                                       1 -> User mode execution (MMU protection)  */
.word   _txm_module_thread_shell_entry - __txm_module_preamble  /* Module Shell Entry Point  */
.word   demo_module_start - __txm_module_preamble           /* Module Start Thread Entry Point  */
.word   0                                                   /* Module Stop Thread Entry Point   */
.word   1                                                   /* Module Start/Stop Thread Priority  */
.word   1024                                                /* Module Start/Stop Thread Stack Size  */
.word   _txm_module_callback_request_thread_entry - __txm_module_preamble   /* Module Callback Thread Entry  */
.word   1                                                   /* Module Callback Thread Priority  */
.word   1024                                                /* Module Callback Thread Stack Size  */
.word   9000                                                /* Module Code Size */
.word   11000                                               /* Module Data Size */
.word   0                                                   /* Reserved 0  */
.word   0                                                   /* Reserved 1  */
.word   0                                                   /* Reserved 2  */
.word   0                                                   /* Reserved 3  */
.word   0                                                   /* Reserved 4  */
.word   0                                                   /* Reserved 5  */
.word   0                                                   /* Reserved 6  */
.word   0                                                   /* Reserved 7  */
.word   0                                                   /* Reserved 8  */
.word   0                                                   /* Reserved 9  */
.word   0                                                   /* Reserved 10  */
.word   0                                                   /* Reserved 11  */
.word   0                                                   /* Reserved 12  */
.word   0                                                   /* Reserved 13  */
.word   0                                                   /* Reserved 14  */
.word   0                                                   /* Reserved 15  */
```

#### <a name="module-properties-for-cortex-r4-using-ac6"></a><span data-ttu-id="8fb80-889">Свойства модуля для Cortex-R4 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-889">Module properties for Cortex-R4 using AC6</span></span>

| <span data-ttu-id="8fb80-890">bit</span><span class="sxs-lookup"><span data-stu-id="8fb80-890">Bit</span></span> | <span data-ttu-id="8fb80-891">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-891">Value</span></span> | <span data-ttu-id="8fb80-892">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-892">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="8fb80-893">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-893">0</span></span> | <span data-ttu-id="8fb80-894">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-894">0</span></span><br /><span data-ttu-id="8fb80-895">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-895">1</span></span> | <span data-ttu-id="8fb80-896">Выполнение в привилегированном режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-896">Privileged mode execution</span></span><br /><span data-ttu-id="8fb80-897">Выполнение в пользовательском режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-897">User mode execution</span></span> |
| <span data-ttu-id="8fb80-898">[23–1]</span><span class="sxs-lookup"><span data-stu-id="8fb80-898">[23-1]</span></span> | <span data-ttu-id="8fb80-899">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-899">0</span></span> | <span data-ttu-id="8fb80-900">Зарезервировано</span><span class="sxs-lookup"><span data-stu-id="8fb80-900">Reserved</span></span>
| <span data-ttu-id="8fb80-901">[31–24]</span><span class="sxs-lookup"><span data-stu-id="8fb80-901">[31-24]</span></span> | <br /><span data-ttu-id="8fb80-902">0x00</span><span class="sxs-lookup"><span data-stu-id="8fb80-902">0x00</span></span><br /><span data-ttu-id="8fb80-903">0x01</span><span class="sxs-lookup"><span data-stu-id="8fb80-903">0x01</span></span><br /><span data-ttu-id="8fb80-904">0x02</span><span class="sxs-lookup"><span data-stu-id="8fb80-904">0x02</span></span> | <span data-ttu-id="8fb80-905">**Идентификатор компилятора**</span><span class="sxs-lookup"><span data-stu-id="8fb80-905">**Compiler ID**</span></span><br /><span data-ttu-id="8fb80-906">IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-906">IAR</span></span><br /><span data-ttu-id="8fb80-907">ARM</span><span class="sxs-lookup"><span data-stu-id="8fb80-907">ARM</span></span><br /><span data-ttu-id="8fb80-908">GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-908">GNU</span></span> |

#### <a name="module-linker-for-cortex-r4-using-ac6"></a><span data-ttu-id="8fb80-909">Компоновщик модулей для Cortex-R4 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-909">Module linker for Cortex-R4 using AC6</span></span>

<span data-ttu-id="8fb80-910">Пример на основе командной строки без файла компоновщика.</span><span class="sxs-lookup"><span data-stu-id="8fb80-910">Built on command-line, no linker file example.</span></span>

#### <a name="building-modules-for-cortex-r4-using-ac6"></a><span data-ttu-id="8fb80-911">Создание модулей для Cortex-R4 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-911">Building Modules for Cortex-R4 using AC6</span></span>

<span data-ttu-id="8fb80-912">Простой пример создания модуля Cortex-R4 с поддержкой AC6 с помощью командной строки:</span><span class="sxs-lookup"><span data-stu-id="8fb80-912">A simple command-line example for building a Cortex-R4 module using AC6:</span></span>

```dos
armclang -c -g -fropi -frwpi --target=arm-arm-none-eabi -mcpu=cortex-r4 demo_threadx_module.c
armclang -c -g -fropi -frwpi --target=arm-arm-none-eabi -mcpu=cortex-r4 txm_module_preamble.S
armclang -c -g -fropi -frwpi --target=arm-arm-none-eabi -mcpu=cortex-r4 semihosting.c
armlink -d -o demo_threadx_module.axf --elf --ro 0x00100000 --first txm_module_preamble.o --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --datacompressor=off --list demo_threadx_module.map txm_module_preamble.o demo_threadx_module.o semihosting.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-r4-using-ac6"></a><span data-ttu-id="8fb80-913">Определение расширения потоков для Cortex-R4 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-913">Thread extension definition for Cortex-R4 using AC6</span></span>

```c
#define TX_THREAD_EXTENSION_2   ULONG   tx_thread_vfp_enable;                   \
                                VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-r4-using-ac6"></a><span data-ttu-id="8fb80-914">Создание диспетчера модулей для Cortex-R4 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-914">Building Module Manager for Cortex-R4 using AC6</span></span>

<span data-ttu-id="8fb80-915">Простой пример создания модуля Cortex-R4 с поддержкой AC6 с помощью командной строки:</span><span class="sxs-lookup"><span data-stu-id="8fb80-915">A simple command-line example for building a Cortex-R4 module manager using AC6:</span></span>

```dos
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 demo_threadx_module_manager.c
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 timer.c
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 gic.c
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 tx_initialize_low_level.S
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 startup.S
armlink -d -o demo_threadx_module_manager.axf --elf --scatter=demo_threadx.scat --remove --map --symbols --list demo_threadx_module_manager.map startup.o timer.o gic.o demo_threadx_module_manager.o tx_initialize_low_level.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-r4-using-ac6"></a><span data-ttu-id="8fb80-916">Атрибуты API включения внешней памяти для Cortex-R4 с поддержкой AC6</span><span class="sxs-lookup"><span data-stu-id="8fb80-916">Attributes for external memory enable API for Cortex-R4 using AC6</span></span>

<span data-ttu-id="8fb80-917">Модуль всегда имеет доступ на чтение к общей памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-917">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="8fb80-918">Параметр атрибута</span><span class="sxs-lookup"><span data-stu-id="8fb80-918">Attribute parameter</span></span> | <span data-ttu-id="8fb80-919">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-919">Meaning</span></span> |
|---|---|
| <span data-ttu-id="8fb80-920">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="8fb80-920">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="8fb80-921">Доступ для записи.</span><span class="sxs-lookup"><span data-stu-id="8fb80-921">Write access</span></span> |

### <a name="cortex-r4-using-iar"></a><span data-ttu-id="8fb80-922">Cortex-R4 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-922">Cortex-R4 using IAR</span></span>

#### <a name="module-preamble-for-cortex-r4-using-iar"></a><span data-ttu-id="8fb80-923">Начальная часть модуля для Cortex-R4 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-923">Module preamble for Cortex-R4 using IAR</span></span>

```c
    SECTION .text:CODE

    AAPCS INTERWORK, ROPI, RWPI_COMPATIBLE,  VFP_COMPATIBLE
    PRESERVE8

    /* Define public symbols.  */
    PUBLIC __txm_module_preamble

    /* Define application-specific start/stop entry points for the module.  */
    EXTERN demo_module_start

    /* Define common external references.  */
    EXTERN  _txm_module_thread_shell_entry
    EXTERN  _txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        ; Module ID
    DC32      0x5                                               ; Module Major Version
    DC32      0x6                                               ; Module Minor Version
    DC32      32                                                ; Module Preamble Size in 32-bit words
    DC32      0x12345678                                        ; Module ID (application defined)
    DC32      0x00000001                                        ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bits 23-1: Reserved
                                                                ;   Bit 0:  0 -> Privileged mode execution (no MPU protection)
                                                                ;           1 -> User mode execution (MPU protection)
    DC32      _txm_module_thread_shell_entry - . - 0            ; Module Shell Entry Point
    DC32      demo_module_start - . - 0                         ; Module Start Thread Entry Point
    DC32      0                                                 ; Module Stop Thread Entry Point
    DC32      1                                                 ; Module Start/Stop Thread Priority
    DC32      1024                                              ; Module Start/Stop Thread Stack Size
    DC32      _txm_module_callback_request_thread_entry - . - 0 ; Module Callback Thread Entry
    DC32      1                                                 ; Module Callback Thread Priority
    DC32      1024                                              ; Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      ; Module Code Size
    DC32      RWPI$$Length                                      ; Module Data Size
    DC32      0                                                 ; Reserved 0
    DC32      0                                                 ; Reserved 1
    DC32      0                                                 ; Reserved 2
    DC32      0                                                 ; Reserved 3
    DC32      0                                                 ; Reserved 4
    DC32      0                                                 ; Reserved 5
    DC32      0                                                 ; Reserved 6
    DC32      0                                                 ; Reserved 7
    DC32      0                                                 ; Reserved 8  
    DC32      0                                                 ; Reserved 9
    DC32      0                                                 ; Reserved 10
    DC32      0                                                 ; Reserved 11
    DC32      0                                                 ; Reserved 12
    DC32      0                                                 ; Reserved 13
    DC32      0                                                 ; Reserved 14
    DC32      0                                                 ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-r4-using-iar"></a><span data-ttu-id="8fb80-924">Свойства модуля для Cortex-R4 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-924">Module properties for Cortex-R4 using IAR</span></span>

| <span data-ttu-id="8fb80-925">bit</span><span class="sxs-lookup"><span data-stu-id="8fb80-925">Bit</span></span> | <span data-ttu-id="8fb80-926">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-926">Value</span></span> | <span data-ttu-id="8fb80-927">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-927">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="8fb80-928">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-928">0</span></span> | <span data-ttu-id="8fb80-929">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-929">0</span></span><br /><span data-ttu-id="8fb80-930">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-930">1</span></span> | <span data-ttu-id="8fb80-931">Выполнение в привилегированном режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-931">Privileged mode execution</span></span><br /><span data-ttu-id="8fb80-932">Выполнение в пользовательском режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-932">User mode execution</span></span> |
| <span data-ttu-id="8fb80-933">[23–1]</span><span class="sxs-lookup"><span data-stu-id="8fb80-933">[23-1]</span></span> | <span data-ttu-id="8fb80-934">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-934">0</span></span> | <span data-ttu-id="8fb80-935">Зарезервировано</span><span class="sxs-lookup"><span data-stu-id="8fb80-935">Reserved</span></span>
| <span data-ttu-id="8fb80-936">[31–24]</span><span class="sxs-lookup"><span data-stu-id="8fb80-936">[31-24]</span></span> | <br /><span data-ttu-id="8fb80-937">0x00</span><span class="sxs-lookup"><span data-stu-id="8fb80-937">0x00</span></span><br /><span data-ttu-id="8fb80-938">0x01</span><span class="sxs-lookup"><span data-stu-id="8fb80-938">0x01</span></span><br /><span data-ttu-id="8fb80-939">0x02</span><span class="sxs-lookup"><span data-stu-id="8fb80-939">0x02</span></span> | <span data-ttu-id="8fb80-940">**Идентификатор компилятора**</span><span class="sxs-lookup"><span data-stu-id="8fb80-940">**Compiler ID**</span></span><br /><span data-ttu-id="8fb80-941">IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-941">IAR</span></span><br /><span data-ttu-id="8fb80-942">ARM</span><span class="sxs-lookup"><span data-stu-id="8fb80-942">ARM</span></span><br /><span data-ttu-id="8fb80-943">GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-943">GNU</span></span> |

#### <a name="module-linker-for-cortex-r4-using-iar"></a><span data-ttu-id="8fb80-944">Компоновщик модулей для Cortex-R4 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-944">Module linker for Cortex-R4 using IAR</span></span>

```c
/*###ICF### Section handled by ICF editor, don't touch! ****/
/*-Editor annotation file-*/
/* IcfEditorFile="$TOOLKIT_DIR$\config\ide\IcfEditor\a_v1_0.xml" */
/*-Specials-*/
/*-Memory Regions-*/
define symbol __ICFEDIT_region_ROM_start__ = 0x00100000;
define symbol __ICFEDIT_region_ROM_end__   = 0x0013FFFF;
define symbol __ICFEDIT_region_RAM_start__ = 0x08000000;
define symbol __ICFEDIT_region_RAM_end__   = 0x0800FFFF;
/*-Sizes-*/
define symbol __ICFEDIT_size_cstack__   = 0;
define symbol __ICFEDIT_size_svcstack__ = 0;
define symbol __ICFEDIT_size_irqstack__ = 0;
define symbol __ICFEDIT_size_fiqstack__ = 0;
define symbol __ICFEDIT_size_undstack__ = 0;
define symbol __ICFEDIT_size_abtstack__ = 0;
define symbol __ICFEDIT_size_heap__     = 0x100;
/**** End of ICF editor section. ###ICF###*/

define memory mem with size = 4G;
define region ROM_region   = mem:[from __ICFEDIT_region_ROM_start__   to __ICFEDIT_region_ROM_end__];
define region RAM_region   = mem:[from __ICFEDIT_region_RAM_start__   to __ICFEDIT_region_RAM_end__];

define block HEAP      with alignment = 8, size = __ICFEDIT_size_heap__     { };

initialize by copy { readwrite };
do not initialize  { section .noinit };

define movable block ROPI with alignment = 4, fixed order
{
  ro object txm_module_preamble.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base
{
  rw,
  block HEAP
};

place in ROM_region   { block ROPI };
place in RAM_region   { block RWPI };
```

#### <a name="building-modules-for-cortex-r4-using-iar"></a><span data-ttu-id="8fb80-945">Создание модулей для Cortex-R4 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-945">Building Modules for Cortex-R4 using IAR</span></span>

<span data-ttu-id="8fb80-946">Предоставлен пример рабочей области.</span><span class="sxs-lookup"><span data-stu-id="8fb80-946">An example workspace is provided.</span></span> <span data-ttu-id="8fb80-947">Можно создать библиотеку ThreadX, библиотеку модулей ThreadX, проект демонстрационного модуля и проект демонстрационного диспетчера модулей.</span><span class="sxs-lookup"><span data-stu-id="8fb80-947">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-r4-using-iar"></a><span data-ttu-id="8fb80-948">Определение расширения потоков для Cortex-R4 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-948">Thread extension definition for Cortex-R4 using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   ULONG   tx_thread_vfp_enable;                   \
                                VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;             \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-cortex-r4-using-iar"></a><span data-ttu-id="8fb80-949">Создание диспетчера модулей для Cortex-R4 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-949">Building Module Manager for Cortex-R4 using IAR</span></span>

<span data-ttu-id="8fb80-950">Предоставлен пример рабочей области.</span><span class="sxs-lookup"><span data-stu-id="8fb80-950">An example workspace is provided.</span></span> <span data-ttu-id="8fb80-951">Можно создать библиотеку ThreadX, библиотеку модулей ThreadX, проект демонстрационного модуля и проект демонстрационного диспетчера модулей.</span><span class="sxs-lookup"><span data-stu-id="8fb80-951">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-r4-using-iar"></a><span data-ttu-id="8fb80-952">Атрибуты API включения внешней памяти для Cortex-R4 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-952">Attributes for external memory enable API for Cortex-R4 using IAR</span></span>

<span data-ttu-id="8fb80-953">Модуль всегда имеет доступ на чтение к общей памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-953">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="8fb80-954">Параметр атрибута</span><span class="sxs-lookup"><span data-stu-id="8fb80-954">Attribute parameter</span></span> | <span data-ttu-id="8fb80-955">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-955">Meaning</span></span> |
|---|---|
| <span data-ttu-id="8fb80-956">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="8fb80-956">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="8fb80-957">Доступ для записи.</span><span class="sxs-lookup"><span data-stu-id="8fb80-957">Write access</span></span> |

## <a name="mcf544xx-processor"></a><span data-ttu-id="8fb80-958">Процессор MCF544xx</span><span class="sxs-lookup"><span data-stu-id="8fb80-958">MCF544xx processor</span></span>

### <a name="mcf544xx-using-ghs"></a><span data-ttu-id="8fb80-959">MCF544xx с поддержкой GHS</span><span class="sxs-lookup"><span data-stu-id="8fb80-959">MCF544xx using GHS</span></span>

#### <a name="module-preamble-for-mcf544xx-using-ghs"></a><span data-ttu-id="8fb80-960">Начальная часть модуля для MCF544xx с поддержкой GHS</span><span class="sxs-lookup"><span data-stu-id="8fb80-960">Module preamble for MCF544xx using GHS</span></span>

```c
    SECT    .preamble, x

    /* Define public symbols.  */
    XDEF __txm_module_preamble

__txm_module_preamble:
    DC.L    0x4D4F4455                                  /* Module ID                                */
    DC.L    0x5                                         /* Module Major Version                     */
    DC.L    0x3                                         /* Module Minor Version                     */
    DC.L    32                                          /* Module Preamble Size in 32-bit words     */
    DC.L    0x12345678                                  /* Module ID (application defined)          */
    DC.L    0x03000003                                  /* Module Properties where:                 */
                                                        /* Bits 31-24: Compiler ID                  */
                                                        /*           3 -> GHS                       */
                                                        /* Bits 23-2: Reserved                      */
                                                        /* Bit 1:  0 -> No MMU protection           */
                                                        /*         1 -> MMU protection (must have   */
                                                        /*              user mode selected)         */
                                                        /* Bit 0:  0 -> Supervisor mode execution   */
                                                        /*         1 -> User mode execution         */
    DC.L    _txm_module_thread_shell_entry              /* Module Shell Entry Point                 */
    DC.L    demo_module_start                           /* Module Start Thread Entry Point          */
    DC.L    0                                           /* Module Stop Thread Entry Point           */
    DC.L    1                                           /* Module Start/Stop Thread Priority        */
    DC.L    2048                                        /* Module Start/Stop Thread Stack Size      */
    DC.L    _txm_module_callback_request_thread_entry   /* Module Callback Thread Entry             */
    DC.L    1                                           /* Module Callback Thread Priority          */
    DC.L    2048                                        /* Module Callback Thread Stack Size        */
    DC.L    module_code_size                            /* Module Code Size                         */
    DC.L    module_data_size                            /* Module Data Size                         */
    DC.L    0                                           /* Reserved 0                               */
    DC.L    0                                           /* Reserved 1                               */
    DC.L    0                                           /* Reserved 2                               */
    DC.L    0                                           /* Reserved 3                               */
    DC.L    0                                           /* Reserved 4                               */
    DC.L    0                                           /* Reserved 5                               */
    DC.L    0                                           /* Reserved 6                               */
    DC.L    0                                           /* Reserved 7                               */
    DC.L    0                                           /* Reserved 8                               */
    DC.L    0                                           /* Reserved 9                               */
    DC.L    0                                           /* Reserved 10                              */
    DC.L    0                                           /* Reserved 11                              */
    DC.L    0                                           /* Reserved 12                              */
    DC.L    0                                           /* Reserved 13                              */
    DC.L    0                                           /* Reserved 14                              */
    DC.L    0                                           /* Reserved 15                              */

    END
```

#### <a name="module-properties-for-mcf544xx-using-ghs"></a><span data-ttu-id="8fb80-961">Свойства модуля для MCF544xx с поддержкой GHS</span><span class="sxs-lookup"><span data-stu-id="8fb80-961">Module properties for MCF544xx using GHS</span></span>

| <span data-ttu-id="8fb80-962">bit</span><span class="sxs-lookup"><span data-stu-id="8fb80-962">Bit</span></span> | <span data-ttu-id="8fb80-963">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-963">Value</span></span> | <span data-ttu-id="8fb80-964">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-964">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="8fb80-965">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-965">0</span></span> | <span data-ttu-id="8fb80-966">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-966">0</span></span><br /><span data-ttu-id="8fb80-967">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-967">1</span></span> | <span data-ttu-id="8fb80-968">Выполнение в привилегированном режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-968">Privileged mode execution</span></span><br /><span data-ttu-id="8fb80-969">Выполнение в пользовательском режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-969">User mode execution</span></span> |
| <span data-ttu-id="8fb80-970">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-970">1</span></span> | <span data-ttu-id="8fb80-971">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-971">0</span></span><br /><span data-ttu-id="8fb80-972">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-972">1</span></span> | <span data-ttu-id="8fb80-973">Без защиты MMU.</span><span class="sxs-lookup"><span data-stu-id="8fb80-973">No MMU protection</span></span><br /><span data-ttu-id="8fb80-974">Защита MMU (необходимо выбрать пользовательский режим).</span><span class="sxs-lookup"><span data-stu-id="8fb80-974">MMU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="8fb80-975">2</span><span class="sxs-lookup"><span data-stu-id="8fb80-975">2</span></span> | <span data-ttu-id="8fb80-976">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-976">0</span></span><br /><span data-ttu-id="8fb80-977">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-977">1</span></span> | <span data-ttu-id="8fb80-978">Отключение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-978">Disable shared/external memory access</span></span><br /><span data-ttu-id="8fb80-979">Включение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-979">Enable shared/external memory access</span></span> |
| <span data-ttu-id="8fb80-980">[23–3]</span><span class="sxs-lookup"><span data-stu-id="8fb80-980">[23-3]</span></span> | <span data-ttu-id="8fb80-981">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-981">0</span></span> | <span data-ttu-id="8fb80-982">Зарезервировано</span><span class="sxs-lookup"><span data-stu-id="8fb80-982">Reserved</span></span>
| <span data-ttu-id="8fb80-983">[31–24]</span><span class="sxs-lookup"><span data-stu-id="8fb80-983">[31-24]</span></span> | <br /><span data-ttu-id="8fb80-984">0x03</span><span class="sxs-lookup"><span data-stu-id="8fb80-984">0x03</span></span> | <span data-ttu-id="8fb80-985">**Идентификатор компилятора**</span><span class="sxs-lookup"><span data-stu-id="8fb80-985">**Compiler ID**</span></span><br /><span data-ttu-id="8fb80-986">GHS</span><span class="sxs-lookup"><span data-stu-id="8fb80-986">GHS</span></span> |

#### <a name="module-linker-for-mcf544xx-using-ghs"></a><span data-ttu-id="8fb80-987">Компоновщик модулей для MCF544xx с поддержкой GHS</span><span class="sxs-lookup"><span data-stu-id="8fb80-987">Module linker for MCF544xx using GHS</span></span>

```c
DEFAULTS {

    heap_reserve =  256
    stack_reserve = 256
}

//
// Program layout for PIC and PID built programs.
//

-sec
{
//
// The data segment
//
    .pidbase                0x00000000 :
    .sdabase                           :
    .sbss                   NOCLEAR    :
    .sdata                             :
    .data                   NOLOAD     :
    .bss                    NOCLEAR    :
    .heap                   ALIGN(16) PAD( heap_reserve +
        // Add space for call-graph profiling if used:
        (isdefined(__ghs_indgcount)?(2000+(sizeof(.text)/2)):0) +
        // Add estimated space for call-count profiling if used:
        (isdefined(__ghs_indmcount)?10000:0) )
                                             :
    .stack      ALIGN(16) PAD(stack_reserve) :

    module_data_size = sizeof(.pidbase) + sizeof(.sdabase) + sizeof(.sbss) + sizeof(.sdata) + sizeof(.data) + sizeof(.bss) + sizeof(.heap) + sizeof(.stack);

//
// The code segment
//

    .picbase                0x00000000 :
    .preamble                          :
    .text                              :
    .syscall                           :
    .fixaddr                           :
    .fixtype                           :
    .rodata                            :
    .ROM.data               ROM(.data) :
    .secinfo                           :

    module_code_size =  endaddr(.secinfo);
}
```

#### <a name="building-modules-for-mcf544xx-using-ghs"></a><span data-ttu-id="8fb80-988">Создание модулей для MCF544xx с поддержкой GHS</span><span class="sxs-lookup"><span data-stu-id="8fb80-988">Building Modules for MCF544xx using GHS</span></span>

<span data-ttu-id="8fb80-989">Предоставлен пример рабочей области.</span><span class="sxs-lookup"><span data-stu-id="8fb80-989">An example workspace is provided.</span></span> <span data-ttu-id="8fb80-990">Можно создать библиотеку ThreadX, библиотеку модулей ThreadX, проект демонстрационного модуля и проект демонстрационного диспетчера модулей.</span><span class="sxs-lookup"><span data-stu-id="8fb80-990">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-mcf544xx-using-ghs"></a><span data-ttu-id="8fb80-991">Определение расширения потоков для MCF544xx с поддержкой GHS</span><span class="sxs-lookup"><span data-stu-id="8fb80-991">Thread extension definition for MCF544xx using GHS</span></span>

```c
#define TX_THREAD_EXTENSION_2   int     Errno;                                  \
                                VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                ULONG   tx_thread_module_mmu_protection;        \
                                VOID *  tx_thread_module_dispatch_return;       \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-mcf544xx-using-ghs"></a><span data-ttu-id="8fb80-992">Создание диспетчера модулей для MCF544xx с поддержкой GHS</span><span class="sxs-lookup"><span data-stu-id="8fb80-992">Building Module Manager for MCF544xx using GHS</span></span>

<span data-ttu-id="8fb80-993">Предоставлен пример рабочей области.</span><span class="sxs-lookup"><span data-stu-id="8fb80-993">An example workspace is provided.</span></span> <span data-ttu-id="8fb80-994">Можно создать библиотеку ThreadX, библиотеку модулей ThreadX, проект демонстрационного модуля и проект демонстрационного диспетчера модулей.</span><span class="sxs-lookup"><span data-stu-id="8fb80-994">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-mcf544xx-using-ghs"></a><span data-ttu-id="8fb80-995">Атрибуты API включения внешней памяти для MCF544xx с поддержкой GHS</span><span class="sxs-lookup"><span data-stu-id="8fb80-995">Attributes for external memory enable API for MCF544xx using GHS</span></span>

<span data-ttu-id="8fb80-996">Эта функция не включена в MCF544xx.</span><span class="sxs-lookup"><span data-stu-id="8fb80-996">This feature not enabled on MCF544xx.</span></span>

## <a name="rx63-processor"></a><span data-ttu-id="8fb80-997">Процессор RX63</span><span class="sxs-lookup"><span data-stu-id="8fb80-997">RX63 processor</span></span>

### <a name="rx63-using-iar"></a><span data-ttu-id="8fb80-998">RX63 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-998">RX63 using IAR</span></span>

#### <a name="module-preamble-for-rx63-using-iar"></a><span data-ttu-id="8fb80-999">Начальная часть модуля для RX63 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-999">Module preamble for RX63 using IAR</span></span>

```c
    /* Alignment of 4 (16-byte) */
    SECTION .text:CODE (4)

    /* Define public symbols.  */
    PUBLIC __txm_module_preamble

    /* Define application-specific start/stop entry points for the module.  */
    EXTERN _demo_module_start

    /* Define common external references.  */
    EXTERN  __txm_module_thread_shell_entry
    EXTERN  __txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        // Module ID
    DC32      0x5                                               // Module Major Version
    DC32      0x6                                               // Module Minor Version
    DC32      32                                                // Module Preamble Size in 32-bit words
    DC32      0x12345678                                        // Module ID (application defined)
    DC32      0x00000007                                        // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
    DC32      __txm_module_thread_shell_entry - $               // Module Shell Entry Point
    DC32      _demo_module_start - $                            // Module Start Thread Entry Point
    DC32      0                                                 // Module Stop Thread Entry Point
    DC32      1                                                 // Module Start/Stop Thread Priority
    DC32      1024                                              // Module Start/Stop Thread Stack Size
    DC32      __txm_module_callback_request_thread_entry - $    // Module Callback Thread Entry
    DC32      1                                                 // Module Callback Thread Priority
    DC32      1024                                              // Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      // Module Code Size
    DC32      RWPI$$Length                                      // Module Data Size
    DC32      0                                                 // Reserved 0
    DC32      0                                                 // Reserved 1
    DC32      0                                                 // Reserved 2
    DC32      0                                                 // Reserved 3
    DC32      0                                                 // Reserved 4
    DC32      0                                                 // Reserved 5
    DC32      0                                                 // Reserved 6
    DC32      0                                                 // Reserved 7
    DC32      0                                                 // Reserved 8  
    DC32      0                                                 // Reserved 9
    DC32      0                                                 // Reserved 10
    DC32      0                                                 // Reserved 11
    DC32      0                                                 // Reserved 12
    DC32      0                                                 // Reserved 13
    DC32      0                                                 // Reserved 14
    DC32      0                                                 // Reserved 15

    END
```

#### <a name="module-properties-for-rx63-using-iar"></a><span data-ttu-id="8fb80-1000">Свойства модуля для RX63 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-1000">Module properties for RX63 using IAR</span></span>

| <span data-ttu-id="8fb80-1001">bit</span><span class="sxs-lookup"><span data-stu-id="8fb80-1001">Bit</span></span> | <span data-ttu-id="8fb80-1002">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-1002">Value</span></span> | <span data-ttu-id="8fb80-1003">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-1003">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="8fb80-1004">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-1004">0</span></span> | <span data-ttu-id="8fb80-1005">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-1005">0</span></span><br /><span data-ttu-id="8fb80-1006">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-1006">1</span></span> | <span data-ttu-id="8fb80-1007">Выполнение в привилегированном режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-1007">Privileged mode execution</span></span><br /><span data-ttu-id="8fb80-1008">Выполнение в пользовательском режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-1008">User mode execution</span></span> |
| <span data-ttu-id="8fb80-1009">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-1009">1</span></span> | <span data-ttu-id="8fb80-1010">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-1010">0</span></span><br /><span data-ttu-id="8fb80-1011">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-1011">1</span></span> | <span data-ttu-id="8fb80-1012">Без защиты MPU.</span><span class="sxs-lookup"><span data-stu-id="8fb80-1012">No MPU protection</span></span><br /><span data-ttu-id="8fb80-1013">Защита MPU (необходимо выбрать пользовательский режим).</span><span class="sxs-lookup"><span data-stu-id="8fb80-1013">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="8fb80-1014">2</span><span class="sxs-lookup"><span data-stu-id="8fb80-1014">2</span></span> | <span data-ttu-id="8fb80-1015">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-1015">0</span></span><br /><span data-ttu-id="8fb80-1016">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-1016">1</span></span> | <span data-ttu-id="8fb80-1017">Отключение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-1017">Disable shared/external memory access</span></span><br /><span data-ttu-id="8fb80-1018">Включение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-1018">Enable shared/external memory access</span></span> |
| <span data-ttu-id="8fb80-1019">[23–3]</span><span class="sxs-lookup"><span data-stu-id="8fb80-1019">[23-3]</span></span> | <span data-ttu-id="8fb80-1020">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-1020">0</span></span> | <span data-ttu-id="8fb80-1021">Зарезервировано</span><span class="sxs-lookup"><span data-stu-id="8fb80-1021">Reserved</span></span>
| <span data-ttu-id="8fb80-1022">[31–24]</span><span class="sxs-lookup"><span data-stu-id="8fb80-1022">[31-24]</span></span> | <br /><span data-ttu-id="8fb80-1023">0x00</span><span class="sxs-lookup"><span data-stu-id="8fb80-1023">0x00</span></span><br /><span data-ttu-id="8fb80-1024">0x02</span><span class="sxs-lookup"><span data-stu-id="8fb80-1024">0x02</span></span> | <span data-ttu-id="8fb80-1025">**Идентификатор компилятора**</span><span class="sxs-lookup"><span data-stu-id="8fb80-1025">**Compiler ID**</span></span><br /><span data-ttu-id="8fb80-1026">IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-1026">IAR</span></span><br /><span data-ttu-id="8fb80-1027">GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-1027">GNU</span></span> |

#### <a name="module-linker-for-rx63-using-iar"></a><span data-ttu-id="8fb80-1028">Компоновщик модулей для RX63 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-1028">Module linker for RX63 using IAR</span></span>

```c
//-----------------------------------------------------------------------------
// ILINK command file template for the Renesas RX microcontroller R5F563NB
//-----------------------------------------------------------------------------
define exported symbol __link_file_version_4 = 1;

define memory mem with size = 4G;

// ID Code Protection
define exported symbol __ID_BYTES_1_4   = 0xFFFFFFFF;
define exported symbol __ID_BYTES_5_8   = 0xFFFFFFFF;
define exported symbol __ID_BYTES_9_12  = 0xFFFFFFFF;
define exported symbol __ID_BYTES_13_16 = 0xFFFFFFFF;

// Endian Select Register (MDE)
// Choose between Little endian=0xFFFFFFFF or Big endian=0xFFFFFFF8
define exported symbol __MDES           = 0xFFFFFFFF;

// Option Function Select Register 0 (OFS0)
define exported symbol __OFS0           = 0xFFFFFFFF;

// Option Function Select Register 1 (OFS1)
define exported symbol __OFS1           = 0xFFFFFFFF;

//define region ROM_region16 = mem:[from 0xFFFF8000 to 0xFFFFFFFF];
define region RAM_region16 = mem:[from 0x00010000 to 0x00017FFF];
//define region ROM_region24 = mem:[from 0xFFF00000 to 0xFFFFFFFF];
//define region RAM_region24 = mem:[from 0x00000004 to 0x0001FFFF];
define region ROM_region32 = mem:[from 0xFFF10400 to 0xFFFFFFFF];
//define region RAM_region32 = mem:[from 0x00000004 to 0x0001FFFF];
//define region DATA_FLASH_region = mem:[from 0x00100000 to 0x00107FFF];

initialize by copy { rw, ro section D, ro section D_1, ro section D_2 };
do not initialize  { section .*.noinit };

define block HEAP     with alignment = 4, size = _HEAP_SIZE { };
//define block USTACK   with alignment = 4, size = _USTACK_SIZE { };
//define block ISTACK   with alignment = 4, size = _ISTACK_SIZE { };

//define block STACKS with fixed order { block ISTACK,
//                                       block USTACK };

//place at address mem:0xFFFFFF80 { ro section .nmivec };
//"ROM16":place in ROM_region16        { ro section .code16*,
//                                       ro section .data16* };
//"RAM16":place in RAM_region16        { rw section .data16*,
//                                       rw section __DLIB_PERTHREAD };
//"ROM24":place in ROM_region24        { ro section .code24*,
//                                       ro section .data24* };
//"RAM24":place in RAM_region24        { rw section .data24* };
//"ROM32":place in ROM_region32        { ro };
//"RAM32":place in RAM_region32        { rw,
//                                       ro section D,
//                                       ro section D_1,
//                                       ro section D_2,
//                                       block HEAP,
//                                       block STACKS,
//                                       last section FREEMEM };

//"DATAFLASH":place in DATA_FLASH_region
//                                     { ro section .dataflash* };

define movable block ROPI with alignment = 4, fixed order, static base CB
{
  ro object txm_module_preamble_rx63n.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base SB
{
  rw section .sbdata*,
  rw section .sbrel*,
  rw section __DLIB_PERTHREAD,
  block HEAP
};

place in ROM_region32   { block ROPI };
place in RAM_region16   { block RWPI };
```

#### <a name="building-modules-for-rx63-using-iar"></a><span data-ttu-id="8fb80-1029">Создание модулей для RX63 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-1029">Building Modules for RX63 using IAR</span></span>

<span data-ttu-id="8fb80-1030">Предоставлен пример рабочей области.</span><span class="sxs-lookup"><span data-stu-id="8fb80-1030">An example workspace is provided.</span></span> <span data-ttu-id="8fb80-1031">Можно создать библиотеку ThreadX, библиотеку модулей ThreadX, проект демонстрационного модуля и проект демонстрационного диспетчера модулей.</span><span class="sxs-lookup"><span data-stu-id="8fb80-1031">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-rxrx635n-using-iar"></a><span data-ttu-id="8fb80-1032">Определение расширения потоков для RX635N с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-1032">Thread extension definition for RXRX635N using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;       \
                                VOID    *tx_thread_module_entry_info_ptr;     \
                                ULONG   tx_thread_module_current_user_mode;   \
                                ULONG   tx_thread_module_user_mode;           \
                                VOID    *tx_thread_module_kernel_stack_start; \
                                VOID    *tx_thread_module_kernel_stack_end;   \
                                ULONG   tx_thread_module_kernel_stack_size;   \
                                VOID    *tx_thread_module_stack_ptr;          \
                                VOID    *tx_thread_module_stack_start;        \
                                VOID    *tx_thread_module_stack_end;          \
                                ULONG   tx_thread_module_stack_size;          \
                                VOID    *tx_thread_module_reserved;           \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-rx63-using-iar"></a><span data-ttu-id="8fb80-1033">Создание диспетчера модулей для RX63 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-1033">Building Module Manager for RX63 using IAR</span></span>

<span data-ttu-id="8fb80-1034">Предоставлен пример рабочей области.</span><span class="sxs-lookup"><span data-stu-id="8fb80-1034">An example workspace is provided.</span></span> <span data-ttu-id="8fb80-1035">Можно создать библиотеку ThreadX, библиотеку модулей ThreadX, проект демонстрационного модуля и проект демонстрационного диспетчера модулей.</span><span class="sxs-lookup"><span data-stu-id="8fb80-1035">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-rx63-using-iar"></a><span data-ttu-id="8fb80-1036">Атрибуты API включения внешней памяти для RX63 с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-1036">Attributes for external memory enable API for RX63 using IAR</span></span>

| <span data-ttu-id="8fb80-1037">Параметр атрибута</span><span class="sxs-lookup"><span data-stu-id="8fb80-1037">Attribute Parameter</span></span> | <span data-ttu-id="8fb80-1038">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-1038">Meaning</span></span> |
|---|---|
| <span data-ttu-id="8fb80-1039">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_EXECUTE</span><span class="sxs-lookup"><span data-stu-id="8fb80-1039">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_EXECUTE</span></span> | <span data-ttu-id="8fb80-1040">Выполнение кода</span><span class="sxs-lookup"><span data-stu-id="8fb80-1040">Execute code</span></span> |
| <span data-ttu-id="8fb80-1041">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="8fb80-1041">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="8fb80-1042">Доступ для записи.</span><span class="sxs-lookup"><span data-stu-id="8fb80-1042">Write access</span></span> |
| <span data-ttu-id="8fb80-1043">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_READ</span><span class="sxs-lookup"><span data-stu-id="8fb80-1043">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_READ</span></span> | <span data-ttu-id="8fb80-1044">Доступ на чтение.</span><span class="sxs-lookup"><span data-stu-id="8fb80-1044">Read access</span></span> |

## <a name="rx65n-processor"></a><span data-ttu-id="8fb80-1045">Процессор RX65N</span><span class="sxs-lookup"><span data-stu-id="8fb80-1045">RX65N processor</span></span>

### <a name="rx65n-using-iar"></a><span data-ttu-id="8fb80-1046">RX65N с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-1046">RX65N using IAR</span></span>

#### <a name="module-preamble-for-rx65n-using-iar"></a><span data-ttu-id="8fb80-1047">Начальная часть модуля для RX65N с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-1047">Module preamble for RX65N using IAR</span></span>

```c
    /* Alignment of 4 (16-byte) */
    SECTION .text:CODE (4)

    /* Define public symbols.  */
    PUBLIC __txm_module_preamble

    /* Define application-specific start/stop entry points for the module.  */
    EXTERN _demo_module_start

    /* Define common external references.  */
    EXTERN  __txm_module_thread_shell_entry
    EXTERN  __txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        // Module ID
    DC32      0x5                                               // Module Major Version
    DC32      0x6                                               // Module Minor Version
    DC32      32                                                // Module Preamble Size in 32-bit words
    DC32      0x12345678                                        // Module ID (application defined)
    DC32      0x00000007                                        // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
    DC32      __txm_module_thread_shell_entry - $               // Module Shell Entry Point
    DC32      _demo_module_start - $                            // Module Start Thread Entry Point
    DC32      0                                                 // Module Stop Thread Entry Point
    DC32      1                                                 // Module Start/Stop Thread Priority
    DC32      1024                                              // Module Start/Stop Thread Stack Size
    DC32      __txm_module_callback_request_thread_entry - $    // Module Callback Thread Entry
    DC32      1                                                 // Module Callback Thread Priority
    DC32      1024                                              // Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      // Module Code Size
    DC32      RWPI$$Length                                      // Module Data Size
    DC32      0                                                 // Reserved 0
    DC32      0                                                 // Reserved 1
    DC32      0                                                 // Reserved 2
    DC32      0                                                 // Reserved 3
    DC32      0                                                 // Reserved 4
    DC32      0                                                 // Reserved 5
    DC32      0                                                 // Reserved 6
    DC32      0                                                 // Reserved 7
    DC32      0                                                 // Reserved 8  
    DC32      0                                                 // Reserved 9
    DC32      0                                                 // Reserved 10
    DC32      0                                                 // Reserved 11
    DC32      0                                                 // Reserved 12
    DC32      0                                                 // Reserved 13
    DC32      0                                                 // Reserved 14
    DC32      0                                                 // Reserved 15

    END
```

#### <a name="module-properties-for-rx65n-using-iar"></a><span data-ttu-id="8fb80-1048">Свойства модуля для RX65N с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-1048">Module properties for RX65N using IAR</span></span>

| <span data-ttu-id="8fb80-1049">bit</span><span class="sxs-lookup"><span data-stu-id="8fb80-1049">Bit</span></span> | <span data-ttu-id="8fb80-1050">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-1050">Value</span></span> | <span data-ttu-id="8fb80-1051">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-1051">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="8fb80-1052">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-1052">0</span></span> | <span data-ttu-id="8fb80-1053">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-1053">0</span></span><br /><span data-ttu-id="8fb80-1054">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-1054">1</span></span> | <span data-ttu-id="8fb80-1055">Выполнение в привилегированном режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-1055">Privileged mode execution</span></span><br /><span data-ttu-id="8fb80-1056">Выполнение в пользовательском режиме.</span><span class="sxs-lookup"><span data-stu-id="8fb80-1056">User mode execution</span></span> |
| <span data-ttu-id="8fb80-1057">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-1057">1</span></span> | <span data-ttu-id="8fb80-1058">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-1058">0</span></span><br /><span data-ttu-id="8fb80-1059">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-1059">1</span></span> | <span data-ttu-id="8fb80-1060">Без защиты MPU.</span><span class="sxs-lookup"><span data-stu-id="8fb80-1060">No MPU protection</span></span><br /><span data-ttu-id="8fb80-1061">Защита MPU (необходимо выбрать пользовательский режим).</span><span class="sxs-lookup"><span data-stu-id="8fb80-1061">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="8fb80-1062">2</span><span class="sxs-lookup"><span data-stu-id="8fb80-1062">2</span></span> | <span data-ttu-id="8fb80-1063">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-1063">0</span></span><br /><span data-ttu-id="8fb80-1064">1</span><span class="sxs-lookup"><span data-stu-id="8fb80-1064">1</span></span> | <span data-ttu-id="8fb80-1065">Отключение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-1065">Disable shared/external memory access</span></span><br /><span data-ttu-id="8fb80-1066">Включение доступа к общей или внешней памяти.</span><span class="sxs-lookup"><span data-stu-id="8fb80-1066">Enable shared/external memory access</span></span> |
| <span data-ttu-id="8fb80-1067">[23–3]</span><span class="sxs-lookup"><span data-stu-id="8fb80-1067">[23-3]</span></span> | <span data-ttu-id="8fb80-1068">0</span><span class="sxs-lookup"><span data-stu-id="8fb80-1068">0</span></span> | <span data-ttu-id="8fb80-1069">Зарезервировано</span><span class="sxs-lookup"><span data-stu-id="8fb80-1069">Reserved</span></span>
| <span data-ttu-id="8fb80-1070">[31–24]</span><span class="sxs-lookup"><span data-stu-id="8fb80-1070">[31-24]</span></span> | <br /><span data-ttu-id="8fb80-1071">0x00</span><span class="sxs-lookup"><span data-stu-id="8fb80-1071">0x00</span></span><br /><span data-ttu-id="8fb80-1072">0x02</span><span class="sxs-lookup"><span data-stu-id="8fb80-1072">0x02</span></span> | <span data-ttu-id="8fb80-1073">**Идентификатор компилятора**</span><span class="sxs-lookup"><span data-stu-id="8fb80-1073">**Compiler ID**</span></span><br /><span data-ttu-id="8fb80-1074">IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-1074">IAR</span></span><br /><span data-ttu-id="8fb80-1075">GNU</span><span class="sxs-lookup"><span data-stu-id="8fb80-1075">GNU</span></span> |

#### <a name="module-linker-for-rx65n-using-iar"></a><span data-ttu-id="8fb80-1076">Компоновщик модулей для RX65N с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-1076">Module linker for RX65N using IAR</span></span>

```c
//-----------------------------------------------------------------------------
// ILINK command file template for the Renesas RX microcontroller R5F565N
//-----------------------------------------------------------------------------
define exported symbol __link_file_version_4 = 1;

define memory mem with size = 4G;

// ID Code Protection
define exported symbol __ID_BYTES_1_4   = 0xFFFFFFFF;
define exported symbol __ID_BYTES_5_8   = 0xFFFFFFFF;
define exported symbol __ID_BYTES_9_12  = 0xFFFFFFFF;
define exported symbol __ID_BYTES_13_16 = 0xFFFFFFFF;

// Endian Select Register (MDE)
// Choose between Little endian=0xFFFFFFFF or Big endian=0xFFFFFFF8
define exported symbol __MDES           = 0xFFFFFFFF;

// Option Function Select Register 0 (OFS0)
define exported symbol __OFS0           = 0xFFFFFFFF;

// Option Function Select Register 1 (OFS1)
define exported symbol __OFS1           = 0xFFFFFFFF;

//define region ROM_region16 = mem:[from 0xFFFF8000 to 0xFFFFFFFF];
define region RAM_region16 = mem:[from 0x00010000 to 0x00017FFF];
//define region ROM_region24 = mem:[from 0xFFF00000 to 0xFFFFFFFF];
//define region RAM_region24 = mem:[from 0x00000004 to 0x0001FFFF];
define region ROM_region32 = mem:[from 0xFFF10400 to 0xFFFFFFFF];
//define region RAM_region32 = mem:[from 0x00000004 to 0x0001FFFF];
//define region DATA_FLASH_region = mem:[from 0x00100000 to 0x00107FFF];

initialize by copy { rw, ro section D, ro section D_1, ro section D_2 };
do not initialize  { section .*.noinit };

define block HEAP     with alignment = 4, size = _HEAP_SIZE { };
//define block USTACK   with alignment = 4, size = _USTACK_SIZE { };
//define block ISTACK   with alignment = 4, size = _ISTACK_SIZE { };

//define block STACKS with fixed order { block ISTACK,
//                                       block USTACK };

//place at address mem:0xFFFFFF80 { ro section .nmivec };
//"ROM16":place in ROM_region16        { ro section .code16*,
//                                       ro section .data16* };
//"RAM16":place in RAM_region16        { rw section .data16*,
//                                       rw section __DLIB_PERTHREAD };
//"ROM24":place in ROM_region24        { ro section .code24*,
//                                       ro section .data24* };
//"RAM24":place in RAM_region24        { rw section .data24* };
//"ROM32":place in ROM_region32        { ro };
//"RAM32":place in RAM_region32        { rw,
//                                       ro section D,
//                                       ro section D_1,
//                                       ro section D_2,
//                                       block HEAP,
//                                       block STACKS,
//                                       last section FREEMEM };

//"DATAFLASH":place in DATA_FLASH_region
//                                     { ro section .dataflash* };

define movable block ROPI with alignment = 4, fixed order, static base CB
{
  ro object txm_module_preamble_rx65n.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base SB
{
  rw section .sbdata*,
  rw section .sbrel*,
  rw section __DLIB_PERTHREAD,
  block HEAP
};

place in ROM_region32   { block ROPI };
place in RAM_region16   { block RWPI };
```

#### <a name="building-modules-for-rx65n-using-iar"></a><span data-ttu-id="8fb80-1077">Создание модулей для RX65N с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-1077">Building Modules for RX65N using IAR</span></span>

<span data-ttu-id="8fb80-1078">Предоставлен пример рабочей области.</span><span class="sxs-lookup"><span data-stu-id="8fb80-1078">An example workspace is provided.</span></span> <span data-ttu-id="8fb80-1079">Можно создать библиотеку ThreadX, библиотеку модулей ThreadX, проект демонстрационного модуля и проект демонстрационного диспетчера модулей.</span><span class="sxs-lookup"><span data-stu-id="8fb80-1079">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-rx65n-using-iar"></a><span data-ttu-id="8fb80-1080">Определение расширения потоков для RX65N с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-1080">Thread extension definition for RX65N using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;             \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-rx65n-using-iar"></a><span data-ttu-id="8fb80-1081">Создание диспетчера модулей для RX65N с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-1081">Building Module Manager for RX65N using IAR</span></span>

<span data-ttu-id="8fb80-1082">Предоставлен пример рабочей области.</span><span class="sxs-lookup"><span data-stu-id="8fb80-1082">An example workspace is provided.</span></span> <span data-ttu-id="8fb80-1083">Можно создать библиотеку ThreadX, библиотеку модулей ThreadX, проект демонстрационного модуля и проект демонстрационного диспетчера модулей.</span><span class="sxs-lookup"><span data-stu-id="8fb80-1083">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-rx65n-using-iar"></a><span data-ttu-id="8fb80-1084">Атрибуты API включения внешней памяти для RX65N с поддержкой IAR</span><span class="sxs-lookup"><span data-stu-id="8fb80-1084">Attributes for external memory enable API for RX65N using IAR</span></span>

| <span data-ttu-id="8fb80-1085">Параметр атрибута</span><span class="sxs-lookup"><span data-stu-id="8fb80-1085">Attribute Parameter</span></span> | <span data-ttu-id="8fb80-1086">Значение</span><span class="sxs-lookup"><span data-stu-id="8fb80-1086">Meaning</span></span> |
|---|---|
| <span data-ttu-id="8fb80-1087">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_EXECUTE</span><span class="sxs-lookup"><span data-stu-id="8fb80-1087">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_EXECUTE</span></span> | <span data-ttu-id="8fb80-1088">Выполнение кода</span><span class="sxs-lookup"><span data-stu-id="8fb80-1088">Execute code</span></span> |
| <span data-ttu-id="8fb80-1089">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="8fb80-1089">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="8fb80-1090">Доступ для записи.</span><span class="sxs-lookup"><span data-stu-id="8fb80-1090">Write access</span></span> |
| <span data-ttu-id="8fb80-1091">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_READ</span><span class="sxs-lookup"><span data-stu-id="8fb80-1091">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_READ</span></span> | <span data-ttu-id="8fb80-1092">Доступ на чтение.</span><span class="sxs-lookup"><span data-stu-id="8fb80-1092">Read access</span></span> |
