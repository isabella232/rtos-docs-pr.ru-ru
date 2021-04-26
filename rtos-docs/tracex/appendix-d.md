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
# <a name="appendix-d---dumping-and-trace-buffer"></a><span data-ttu-id="c66c9-103">Приложение D. Выполнение дампа и буфер трассировки</span><span class="sxs-lookup"><span data-stu-id="c66c9-103">Appendix D - Dumping and trace buffer</span></span>

<span data-ttu-id="c66c9-104">Выполнение дампа буфера трассировки, созданного ОСРВ Azure ThreadX, в файл на главном компьютере происходит с помощью команд и (или) служебных программ, предоставляемых конкретным средством разработки.</span><span class="sxs-lookup"><span data-stu-id="c66c9-104">Dumping the trace buffer created by Azure RTOS ThreadX to a file on the host computer is done via commands and/or utilities provided by the specific development tool being used.</span></span> <span data-ttu-id="c66c9-105">В этом приложении содержатся примеры выполнения дампа буфера трассировки в файл узла в некоторых более популярных средствах разработки, используемых с ThreadX.</span><span class="sxs-lookup"><span data-stu-id="c66c9-105">This appendix contains examples of dumping a trace buffer to a host file in some of the more popular development tools used with ThreadX.</span></span> 

## <a name="benchx-tools"></a><span data-ttu-id="c66c9-106">Средства BenchX</span><span class="sxs-lookup"><span data-stu-id="c66c9-106">BenchX Tools</span></span>

<span data-ttu-id="c66c9-107">Буфер трассировки можно легко скопировать в файл узла с помощью инструментов BenchX, нажав кнопку ***Store Memory To File** _ (Сохранить память в файл) в _*_представлении памяти_\*\*, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="c66c9-107">The trace buffer can be dumped to a host file easily with the BenchX tools by selecting the ***Store Memory To File** _ button within the _*_Memory View_\*\*, as shown below:</span></span>

![Снимок экрана: окно Memory View (Представление памяти) в средствах BenchX.](./media/user-guide/image642.jpg)

<span data-ttu-id="c66c9-109">На этом этапе укажите адрес буфера трассировки, размер, имя файла назначения (включая путь) и нажмите кнопку ***Сохранить***, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="c66c9-109">At this point, specify the trace buffer address, size, destination file name (including path), and select the ***Save*** button as shown below.</span></span> <span data-ttu-id="c66c9-110">Будет создан двоичный файл трассировки для просмотра в TraceX.</span><span class="sxs-lookup"><span data-stu-id="c66c9-110">This will create the binary trace file for viewing within TraceX.</span></span>

![Снимок экрана: диалоговое окно сохранения средств BenchX.](./media/user-guide/image643.jpg)

## <a name="realview-tools"></a><span data-ttu-id="c66c9-112">Средства RealView</span><span class="sxs-lookup"><span data-stu-id="c66c9-112">RealView Tools</span></span>

<span data-ttu-id="c66c9-113">Буфер трассировки можно легко скопировать в файл узла с помощью средств ARM RealView, введя в командной строке RealView следующую команду:</span><span class="sxs-lookup"><span data-stu-id="c66c9-113">The trace buffer can be dumped to a host file easily with the ARM RealView tools by entering the following command at the command-line prompt in RealView:</span></span>

```c 
> WRITEFILE,raw trace_file.trx=0x6860..0xE560
```

<span data-ttu-id="c66c9-114">Файл ***trace_file.trx*** по завершении будет содержать буфер трассировки, расположенный в диапазоне адресов от 0x6860 до 0xE560.</span><span class="sxs-lookup"><span data-stu-id="c66c9-114">Upon completion, the file ***trace_file.trx*** will contain the trace buffer that is located starting at the address 0x6860 and goes up to address 0xE560.</span></span> <span data-ttu-id="c66c9-115">Этот файл готов к просмотру в TraceX.</span><span class="sxs-lookup"><span data-stu-id="c66c9-115">This file is ready for viewing by TraceX.</span></span>

## <a name="iar-tools"></a><span data-ttu-id="c66c9-116">Средства IAR</span><span class="sxs-lookup"><span data-stu-id="c66c9-116">IAR Tools</span></span>

<span data-ttu-id="c66c9-117">Буфер трассировки можно легко скопировать в файл узла с помощью средств IAR, просто щелкнув правой кнопкой мыши представление памяти и выбрав параметр ***Memory Save…*** (Сохранение памяти),</span><span class="sxs-lookup"><span data-stu-id="c66c9-117">The trace buffer can be dumped to a host file easily with the IAR tools by simply right-clicking in the memory view and selecting the ***Memory Save…***</span></span> <span data-ttu-id="c66c9-118">как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="c66c9-118">option, as shown below.</span></span>

![Снимок экрана: параметр "Сохранение памяти" в средствах IAR.](./media/user-guide/image0_311.jpg)

<span data-ttu-id="c66c9-120">В результате откроется диалоговое окно \***Memory Save** _ (Сохранение памяти).</span><span class="sxs-lookup"><span data-stu-id="c66c9-120">This results in the \***Memory Save** _ dialog to be displayed.</span></span> <span data-ttu-id="c66c9-121">Введите начальный и конечный адреса и имя файла трассировки, а затем нажмите кнопку _\*_Сохранить_\*_.</span><span class="sxs-lookup"><span data-stu-id="c66c9-121">Enter the starting and ending address and the trace file name, then select the _*_Save_*_ button.</span></span> <span data-ttu-id="c66c9-122">В приведенном ниже примере средства IAR сохраняют указанный буфер трассировки в шестнадцатеричных записях Intel HEX в файле _\*_trace_file.hex_\*\*.</span><span class="sxs-lookup"><span data-stu-id="c66c9-122">In the example shown below, the IAR tools save the specified trace buffer into Intel HEX records in the file _\*_trace_file.hex_\*\*.</span></span>

![Снимок экрана: диалоговое окно "Сохранение памяти" в средствах IAR.](./media/user-guide/image648.jpg)

<span data-ttu-id="c66c9-124">На этом этапе мы сохранили буфер трассировки в файле ***trace_file.hex*** на узле. Теперь он готов к просмотру с помощью TraceX.</span><span class="sxs-lookup"><span data-stu-id="c66c9-124">At this point, we have the trace buffer saved in the ***trace_file.hex*** file on the host and is ready for viewing with TraceX.</span></span>

## <a name="codewarrior-tools"></a><span data-ttu-id="c66c9-125">Средства CodeWarrior</span><span class="sxs-lookup"><span data-stu-id="c66c9-125">CodeWarrior Tools</span></span>

<span data-ttu-id="c66c9-126">Буфер трассировки можно легко скопировать в файл узла с помощью средств CodeWarrior, введя команду \***save** _ в командном окне.</span><span class="sxs-lookup"><span data-stu-id="c66c9-126">The trace buffer can be dumped to a host file easily with the CodeWarrior tools by entering the \***save** _ command in the Command Window.</span></span> <span data-ttu-id="c66c9-127">В следующем примере команды _ *_save_*\* предполагается, что буфер трассировки начинается с адреса 0x102200 и заканчивается адресом 0x109F00:</span><span class="sxs-lookup"><span data-stu-id="c66c9-127">The following example _ *_save_*\* command assumes the trace buffer starts at 0x102200 and ends at 0x109F00:</span></span>

```c
> save –b p:0x102200..0x109F00 trace_file.trx -a 32bit
```

<span data-ttu-id="c66c9-128">В результате буфер трассировки сохраняется в файле ***trace_file.trx*** на узле.</span><span class="sxs-lookup"><span data-stu-id="c66c9-128">This results in the trace buffer being saved in the file ***trace_file.trx*** on the host.</span></span>

## <a name="mplab-tools"></a><span data-ttu-id="c66c9-129">Средства MPLAB</span><span class="sxs-lookup"><span data-stu-id="c66c9-129">MPLAB Tools</span></span>

<span data-ttu-id="c66c9-130">MPLAB может создать совместимый с TraceX файл трассировки с помощью служебной программы "Экспорт таблицы", которая позволяет экспортировать любой диапазон памяти в файл узла.</span><span class="sxs-lookup"><span data-stu-id="c66c9-130">MPLAB can create a TraceX-compatible trace file through its Export Table utility, which allows the export of any range of memory to a host file.</span></span> <span data-ttu-id="c66c9-131">Чтобы использовать эту служебную программу для создания файла трассировки для TraceX, выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="c66c9-131">To use this utility to create a trace file for TraceX, proceed as follows:</span></span>

<span data-ttu-id="c66c9-132">**Шаг 1.** Откройте окно памяти, выбрав "Представление" -> "Память".</span><span class="sxs-lookup"><span data-stu-id="c66c9-132">**Step 1** Open a memory window by selecting View -> Memory.</span></span>

![Снимок экрана: окно "Память", выбранное в меню "Представление".](./media/user-guide/image0_316.jpg)

<span data-ttu-id="c66c9-134">**Шаг 2.** Щелкните правой кнопкой мыши в окне **Memory View** (Представление памяти), чтобы открыть список параметров.</span><span class="sxs-lookup"><span data-stu-id="c66c9-134">**Step 2** Right-click within the **Memory View** to display a list of options.</span></span> <span data-ttu-id="c66c9-135">Щелкните **Формат отображения — 1 Байт**, чтобы выбрать параметр отображения байта.</span><span class="sxs-lookup"><span data-stu-id="c66c9-135">Specify **Display Format -1 Byte** to select byte display..</span></span>

![Снимок экрана: окно Memory View (Представление памяти) с выбранным параметром "Формат отображения".](./media/user-guide/image650.png)

![Снимок экрана: диалоговое окно "Перейти".](./media/user-guide/image651.jpg)

<span data-ttu-id="c66c9-138">**Шаг 3.** Щелкните правой кнопкой мыши в окне **Memory View** (Представление памяти) и выберите пункт **Перейти**, после чего откроется диалоговое окно, в котором можно указать адрес буфера событий.</span><span class="sxs-lookup"><span data-stu-id="c66c9-138">**Step 3** Right-click again within the **Memory View** Window and select **Go To**, which opens a dialog box that enables you to specify the address of the event buffer.</span></span> <span data-ttu-id="c66c9-139">В этом примере показано отображение **_event_buffer_**.</span><span class="sxs-lookup"><span data-stu-id="c66c9-139">This example shows **_event_buffer_** being displayed.</span></span>

![Снимок экрана: окно Memory View (Представление памяти) с выбранным параметром "Перейти".](./media/user-guide/image0_312.jpg)

![Снимок экрана: пример отображения event_buffer.](./media/user-guide/image653.png)

<span data-ttu-id="c66c9-142">**Шаг 4.** Здесь выделено содержимое первого расположения буфера трассировки, который всегда является строкой BTXT...</span><span class="sxs-lookup"><span data-stu-id="c66c9-142">**Step 4** This highlights the contents of the first location of the trace buffer, which is always the string BTXT….</span></span>

![Снимок экрана: первое расположение буфера трассировки.](./media/user-guide/image0_313.jpg)

<span data-ttu-id="c66c9-144">**Шаг 5.** Теперь снова щелкните правой кнопкой мыши, чтобы открыть меню параметров, и нажмите кнопку **Export Table** (Экспортировать таблицу).</span><span class="sxs-lookup"><span data-stu-id="c66c9-144">**Step 5** Now, right-click again to bring up the options menu, and select **Export Table**.</span></span>

![Снимок экрана: окно Memory View (Представление памяти) с выбранным параметром Export Table (Экспортировать таблицу).](./media/user-guide/image0_314.jpg)

<span data-ttu-id="c66c9-146">**Шаг 6.** Откройте диалоговое окно **Export Table** (Экспортировать таблицу), как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="c66c9-146">**Step 6** This brings up the **Export Table** dialog, as shown.</span></span> <span data-ttu-id="c66c9-147">Определите диапазон адресов для экспорта.</span><span class="sxs-lookup"><span data-stu-id="c66c9-147">Specify the range of addresses to export.</span></span> <span data-ttu-id="c66c9-148">Для буфера трассировки размером 8 КБ, который приведен в этом примере, укажите диапазон адресов от 0xA00006AC до 0xA00026AC и введите имя создаваемого файла узла (demo_threadx.trx в этом примере).</span><span class="sxs-lookup"><span data-stu-id="c66c9-148">For an 8K trace buffer, as is the case in this example, specify the range 0xA00006AC to 0xA00026AC, and enter a name for the host file to be created (demo_threadx.trx in this example).</span></span>

<span data-ttu-id="c66c9-149">![[Снимок экрана: диалоговое окно "Экспортировать как".](./media/user-guide/image656.jpg)</span><span class="sxs-lookup"><span data-stu-id="c66c9-149">![[Screenshot of the Export As dialog.](./media/user-guide/image656.jpg)</span></span>

<span data-ttu-id="c66c9-150">**Шаг 7.** На узле будет создан файл с именем **demo_threadx.trx**. Этот файл можно открыть с помощью TraceX.</span><span class="sxs-lookup"><span data-stu-id="c66c9-150">**Step 7** A file named **demo_threadx.trx** will be created on the host, and this file can be opened by TraceX.</span></span>

## <a name="ghs-tools"></a><span data-ttu-id="c66c9-151">Средства GHS</span><span class="sxs-lookup"><span data-stu-id="c66c9-151">GHS Tools</span></span>

<span data-ttu-id="c66c9-152">Буфер трассировки можно легко скопировать в файл узла с помощью средств GHS, введя в командной строке окна команд отладки следующую команду:</span><span class="sxs-lookup"><span data-stu-id="c66c9-152">The trace buffer can be dumped to a host file easily with the GHS tools by entering the following command at the command-line prompt in the debug command window:</span></span>

```c
memdump raw c:releasethreadxdemo_threadx.trx event_buffer 32768
```

<span data-ttu-id="c66c9-153">После завершения файл **demo_threadx.trx** будет содержать буфер трассировки, находящийся в event_buffer, размером 32 768 байт. Теперь его можно будет просмотреть с помощью TraceX.</span><span class="sxs-lookup"><span data-stu-id="c66c9-153">Upon completion, the file **demo_threadx.trx** will contain the trace buffer that is located in the event_buffer with a size of 32,768 bytes and is ready for viewing by TraceX.</span></span>

## <a name="renesas-hew"></a><span data-ttu-id="c66c9-154">Renesas HEW</span><span class="sxs-lookup"><span data-stu-id="c66c9-154">Renesas HEW</span></span>

<span data-ttu-id="c66c9-155">Буфер трассировки можно легко скопировать в файл узла с помощью средств HEW, выполнив три приведенных ниже шага (подэтапа):</span><span class="sxs-lookup"><span data-stu-id="c66c9-155">The trace buffer can be dumped to a host file easily with the Renasas HEW tools by following the three steps (and substeps) below:</span></span>

<span data-ttu-id="c66c9-156">**Шаг 1.** Откройте окно памяти.</span><span class="sxs-lookup"><span data-stu-id="c66c9-156">**Step 1** Open Memory Window.</span></span>

<span data-ttu-id="c66c9-157">![[Снимок экрана: окно памяти.](./media/user-guide/image657.jpg)</span><span class="sxs-lookup"><span data-stu-id="c66c9-157">![[Screenshot of the Memory Window.](./media/user-guide/image657.jpg)</span></span>

<span data-ttu-id="c66c9-158">**Шаг 2.** Поместите курсор в окно памяти, а затем щелкните правой кнопкой мыши.</span><span class="sxs-lookup"><span data-stu-id="c66c9-158">**Step 2** Place cursor within memory window and right click.</span></span>

![Снимок экрана: окно памяти с выбранным параметром "Сохранить".](./media/user-guide/image0_315.jpg)

<span data-ttu-id="c66c9-160">**Шаг 3.** Нажмите кнопку "Сохранить", а затем в окне Save Memory As (Сохранить память как) выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="c66c9-160">**Step 3** Select Save, then in the Save Memory As window do the following:</span></span>

- <span data-ttu-id="c66c9-161">Выберите формат файла: двоичный.</span><span class="sxs-lookup"><span data-stu-id="c66c9-161">Select File format: Binary.</span></span>
- <span data-ttu-id="c66c9-162">Укажите имя файла: необязательно.</span><span class="sxs-lookup"><span data-stu-id="c66c9-162">Specify Filename: As Desired</span></span>
- <span data-ttu-id="c66c9-163">Укажите начальный адрес: trace_buffer.</span><span class="sxs-lookup"><span data-stu-id="c66c9-163">Specify Start address: trace_buffer</span></span>
- <span data-ttu-id="c66c9-164">Укажите конечный адрес: (trace_buffer+size).</span><span class="sxs-lookup"><span data-stu-id="c66c9-164">Specify End address: (trace_buffer+size)</span></span>
- <span data-ttu-id="c66c9-165">Укажите размер доступа: 1.</span><span class="sxs-lookup"><span data-stu-id="c66c9-165">Specify Access size: 1</span></span>
- <span data-ttu-id="c66c9-166">Щелкните Сохранить</span><span class="sxs-lookup"><span data-stu-id="c66c9-166">Click Save</span></span>

![Снимок экрана: диалоговое окно Save Memory As (Сохранить память как).](./media/user-guide/image659.jpg)