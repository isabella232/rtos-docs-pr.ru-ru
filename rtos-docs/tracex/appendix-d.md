---
title: Приложение D. Выполнение дампа и буфер трассировки
description: Выполнение дампа буфера трассировки, созданного ОСРВ Azure ThreadX, в файл на главном компьютере происходит с помощью команд и (или) служебных программ, предоставляемых конкретным средством разработки.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 30f6b5e329feeb2dca37dda391fd738aba587c9a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815868"
---
# <a name="appendix-d---dumping-and-trace-buffer"></a>Приложение D. Выполнение дампа и буфер трассировки

Выполнение дампа буфера трассировки, созданного ОСРВ Azure ThreadX, в файл на главном компьютере происходит с помощью команд и (или) служебных программ, предоставляемых конкретным средством разработки. В этом приложении содержатся примеры выполнения дампа буфера трассировки в файл узла в некоторых более популярных средствах разработки, используемых с ThreadX. 

## <a name="benchx-tools"></a>Средства BenchX

Буфер трассировки можно легко скопировать в файл узла с помощью инструментов BenchX, нажав кнопку ***Store Memory To File** _ (Сохранить память в файл) в _*_представлении памяти_**, как показано ниже:

![Снимок экрана: окно Memory View (Представление памяти) в средствах BenchX.](./media/user-guide/image642.jpg)

На этом этапе укажите адрес буфера трассировки, размер, имя файла назначения (включая путь) и нажмите кнопку ***Сохранить***, как показано ниже. Будет создан двоичный файл трассировки для просмотра в TraceX.

![Снимок экрана: диалоговое окно сохранения средств BenchX.](./media/user-guide/image643.jpg)

## <a name="realview-tools"></a>Средства RealView

Буфер трассировки можно легко скопировать в файл узла с помощью средств ARM RealView, введя в командной строке RealView следующую команду:

```c 
> WRITEFILE,raw trace_file.trx=0x6860..0xE560
```

Файл ***trace_file.trx*** по завершении будет содержать буфер трассировки, расположенный в диапазоне адресов от 0x6860 до 0xE560. Этот файл готов к просмотру в TraceX.

## <a name="iar-tools"></a>Средства IAR

Буфер трассировки можно легко скопировать в файл узла с помощью средств IAR, просто щелкнув правой кнопкой мыши представление памяти и выбрав параметр ***Memory Save…*** (Сохранение памяти), как показано ниже.

![Снимок экрана: параметр "Сохранение памяти" в средствах IAR.](./media/user-guide/image0_311.jpg)

В результате откроется диалоговое окно ***Memory Save** _ (Сохранение памяти). Введите начальный и конечный адреса и имя файла трассировки, а затем нажмите кнопку _*_Сохранить_*_. В приведенном ниже примере средства IAR сохраняют указанный буфер трассировки в шестнадцатеричных записях Intel HEX в файле _*_trace_file.hex_**.

![Снимок экрана: диалоговое окно "Сохранение памяти" в средствах IAR.](./media/user-guide/image648.jpg)

На этом этапе мы сохранили буфер трассировки в файле ***trace_file.hex*** на узле. Теперь он готов к просмотру с помощью TraceX.

## <a name="codewarrior-tools"></a>Средства CodeWarrior

Буфер трассировки можно легко скопировать в файл узла с помощью средств CodeWarrior, введя команду ***save** _ в командном окне. В следующем примере команды _ *_save_** предполагается, что буфер трассировки начинается с адреса 0x102200 и заканчивается адресом 0x109F00:

```c
> save –b p:0x102200..0x109F00 trace_file.trx -a 32bit
```

В результате буфер трассировки сохраняется в файле ***trace_file.trx*** на узле.

## <a name="mplab-tools"></a>Средства MPLAB

MPLAB может создать совместимый с TraceX файл трассировки с помощью служебной программы "Экспорт таблицы", которая позволяет экспортировать любой диапазон памяти в файл узла. Чтобы использовать эту служебную программу для создания файла трассировки для TraceX, выполните следующие действия:

**Шаг 1.** Откройте окно памяти, выбрав "Представление" -> "Память".

![Снимок экрана: окно "Память", выбранное в меню "Представление".](./media/user-guide/image0_316.jpg)

**Шаг 2.** Щелкните правой кнопкой мыши в окне **Memory View** (Представление памяти), чтобы открыть список параметров. Щелкните **Формат отображения — 1 Байт**, чтобы выбрать параметр отображения байта.

![Снимок экрана: окно Memory View (Представление памяти) с выбранным параметром "Формат отображения".](./media/user-guide/image650.png)

![Снимок экрана: диалоговое окно "Перейти".](./media/user-guide/image651.jpg)

**Шаг 3.** Щелкните правой кнопкой мыши в окне **Memory View** (Представление памяти) и выберите пункт **Перейти**, после чего откроется диалоговое окно, в котором можно указать адрес буфера событий. В этом примере показано отображение **_event_buffer_**.

![Снимок экрана: окно Memory View (Представление памяти) с выбранным параметром "Перейти".](./media/user-guide/image0_312.jpg)

![Снимок экрана: пример отображения event_buffer.](./media/user-guide/image653.png)

**Шаг 4.** Здесь выделено содержимое первого расположения буфера трассировки, который всегда является строкой BTXT...

![Снимок экрана: первое расположение буфера трассировки.](./media/user-guide/image0_313.jpg)

**Шаг 5.** Теперь снова щелкните правой кнопкой мыши, чтобы открыть меню параметров, и нажмите кнопку **Export Table** (Экспортировать таблицу).

![Снимок экрана: окно Memory View (Представление памяти) с выбранным параметром Export Table (Экспортировать таблицу).](./media/user-guide/image0_314.jpg)

**Шаг 6.** Откройте диалоговое окно **Export Table** (Экспортировать таблицу), как показано ниже. Определите диапазон адресов для экспорта. Для буфера трассировки размером 8 КБ, который приведен в этом примере, укажите диапазон адресов от 0xA00006AC до 0xA00026AC и введите имя создаваемого файла узла (demo_threadx.trx в этом примере).

![[Снимок экрана: диалоговое окно "Экспортировать как".](./media/user-guide/image656.jpg)

**Шаг 7.** На узле будет создан файл с именем **demo_threadx.trx**. Этот файл можно открыть с помощью TraceX.

## <a name="ghs-tools"></a>Средства GHS

Буфер трассировки можно легко скопировать в файл узла с помощью средств GHS, введя в командной строке окна команд отладки следующую команду:

```c
memdump raw c:releasethreadxdemo_threadx.trx event_buffer 32768
```

После завершения файл **demo_threadx.trx** будет содержать буфер трассировки, находящийся в event_buffer, размером 32 768 байт. Теперь его можно будет просмотреть с помощью TraceX.

## <a name="renesas-hew"></a>Renesas HEW

Буфер трассировки можно легко скопировать в файл узла с помощью средств HEW, выполнив три приведенных ниже шага (подэтапа):

**Шаг 1.** Откройте окно памяти.

![[Снимок экрана: окно памяти.](./media/user-guide/image657.jpg)

**Шаг 2.** Поместите курсор в окно памяти, а затем щелкните правой кнопкой мыши.

![Снимок экрана: окно памяти с выбранным параметром "Сохранить".](./media/user-guide/image0_315.jpg)

**Шаг 3.** Нажмите кнопку "Сохранить", а затем в окне Save Memory As (Сохранить память как) выполните следующие действия:

- Выберите формат файла: двоичный.
- Укажите имя файла: необязательно.
- Укажите начальный адрес: trace_buffer.
- Укажите конечный адрес: (trace_buffer+size).
- Укажите размер доступа: 1.
- Щелкните Сохранить

![Снимок экрана: диалоговое окно Save Memory As (Сохранить память как).](./media/user-guide/image659.jpg)