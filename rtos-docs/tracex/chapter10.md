---
title: Глава 10. Пользовательские события
description: В этой главе приводится описание создания определяемых пользователем событий, а также настраиваемых значков и полей сведений для таких событий.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 635c2d79922de9d5649bab841ae946cac862056c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815791"
---
# <a name="chapter-10---customer-user-events"></a><span data-ttu-id="b9e98-103">Глава 10. Пользовательские события</span><span class="sxs-lookup"><span data-stu-id="b9e98-103">Chapter 10 - Customer user events</span></span>

<span data-ttu-id="b9e98-104">В этой главе приводится описание создания определяемых пользователем событий, а также настраиваемых значков и полей сведений для таких событий.</span><span class="sxs-lookup"><span data-stu-id="b9e98-104">This chapter contains a description of how to create user-defined events and custom icons and information fields for such events.</span></span> <span data-ttu-id="b9e98-105">Эта глава состоит из следующих разделов.</span><span class="sxs-lookup"><span data-stu-id="b9e98-105">This chapter includes the following sections:</span></span> 

## <a name="inserting-user-defined-events"></a><span data-ttu-id="b9e98-106">Вставка определяемых пользователем событий</span><span class="sxs-lookup"><span data-stu-id="b9e98-106">Inserting User-Defined Events</span></span>

<span data-ttu-id="b9e98-107">ThreadX позволяет разработчикам регистрировать собственные события и указывать еще более точную и полезную информацию, которую можно просматривать в TraceX в графическом виде.</span><span class="sxs-lookup"><span data-stu-id="b9e98-107">ThreadX provides the ability for developers to log their own user-defined events, providing even more useful information that can be viewed graphically by TraceX.</span></span> <span data-ttu-id="b9e98-108">Номера определяемых пользователем событий входят в диапазон от</span><span class="sxs-lookup"><span data-stu-id="b9e98-108">User-defined event numbers range from</span></span>

<span data-ttu-id="b9e98-109">**TX_TRACE_USER_EVENT_START** (4096) до **TX_TRACE_USER_EVENT_END** (65535) включительно.</span><span class="sxs-lookup"><span data-stu-id="b9e98-109">**TX_TRACE_USER_EVENT_START** (4096) through **TX_TRACE_USER_EVENT_END** (65535), inclusive.</span></span> <span data-ttu-id="b9e98-110">Размещение событий в буфере трассировки выполняется с помощью службы ***tx_trace_user_event_insert***, определенной в главе 5.</span><span class="sxs-lookup"><span data-stu-id="b9e98-110">The placement of the events in the trace buffer is done via the ***tx_trace_user_event_insert***, defined in Chapter 5.</span></span> <span data-ttu-id="b9e98-111">В следующем примере приведены вызовы службы для вставки двух определяемых пользователем событий в текущий буфер трассировки в целевом объекте. Это события 4096 и 4098.</span><span class="sxs-lookup"><span data-stu-id="b9e98-111">The following example calls insert two user-defined events into the current trace buffer on the target, namely user-defined event 4096 and event 4098:</span></span>

```c
tx_trace_user_event_insert(4096, 1, 2, 3, 4);
tx_trace_user_event_insert(4098,0x100,0x200,0x300,0x400);
```

## <a name="default-display-of-user-defined-events"></a><span data-ttu-id="b9e98-112">Отображение определяемых пользователем событий по умолчанию</span><span class="sxs-lookup"><span data-stu-id="b9e98-112">Default Display of User-Defined Events</span></span>

![Значок определяемого пользователем события](./media/user-guide/tx-events/image0.png)

<span data-ttu-id="b9e98-114">По умолчанию TraceX отображает все пользовательские события с заданным по умолчанию значком, как описано в главе 6.</span><span class="sxs-lookup"><span data-stu-id="b9e98-114">By default, TraceX displays all user events with a default user-defined Event icon as described in Chapter 6.</span></span> <span data-ttu-id="b9e98-115">На рис. 28 показан заданный по умолчанию значок для определяемых пользователем событий 452 и 453, которые были помещены в буфер событий с помощью предыдущих примеров использования службы ***tx_trace_user_event_insert***.</span><span class="sxs-lookup"><span data-stu-id="b9e98-115">Figure 28 shows the default user-defined event icon for events 452 and 453, which were placed in the event buffer via the previous ***tx_trace_user_event_insert*** examples.</span></span>

<span data-ttu-id="b9e98-116">![Снимок экрана: отображение определяемых пользователем событий по умолчанию](./media/user-guide/10.1.png)
**РИС. 28**</span><span class="sxs-lookup"><span data-stu-id="b9e98-116">![Screenshot of the default display of user-defined events.](./media/user-guide/10.1.png)
**FIGURE 28**</span></span>

<span data-ttu-id="b9e98-117">Для определяемых пользователем событий также доступны подробные сведения.</span><span class="sxs-lookup"><span data-stu-id="b9e98-117">Detailed information is also available for user-defined Events.</span></span> <span data-ttu-id="b9e98-118">На рис. 28 показаны подробные сведения о событии 452 с номером события 4096 и указаны четыре поля сведений.</span><span class="sxs-lookup"><span data-stu-id="b9e98-118">Figure 28 shows the detailed event information for event 452, which has event number 4096 and shows the specified four information fields.</span></span>

<span data-ttu-id="b9e98-119">![Снимок экрана: отображение определяемых пользователем событий по умолчанию](./media/user-guide/10.2.png)
**РИС. 29**</span><span class="sxs-lookup"><span data-stu-id="b9e98-119">![Screenshot of the detailed display of user-defined events.](./media/user-guide/10.2.png)
**FIGURE 29**</span></span>

## <a name="defining-custom-user-defined-event-icons"></a><span data-ttu-id="b9e98-120">Определение настраиваемых значков для определяемых пользователем событий</span><span class="sxs-lookup"><span data-stu-id="b9e98-120">Defining Custom User-Defined Event Icons</span></span>

<span data-ttu-id="b9e98-121">TraceX предоставляет возможность создания настраиваемых значков для определяемых пользователем событий и настраиваемых меток полей сведений.</span><span class="sxs-lookup"><span data-stu-id="b9e98-121">TraceX also provides the user the ability to create custom user-defined event icons and custom information field labels.</span></span> <span data-ttu-id="b9e98-122">Она реализуется путем добавления спецификаций значков событий в файл конфигурации \***tracex_custom.trxc** _.</span><span class="sxs-lookup"><span data-stu-id="b9e98-122">This capability is achieved by adding event icon specifications to the \***tracex_custom.trxc** _ configuration file.</span></span> <span data-ttu-id="b9e98-123">Этот файл находится в подкаталоге _ *_CustomEvents_*\* определяемого пользователем каталога установки TraceX. По умолчанию это каталог C:\Azure_RTOS\TraceX.</span><span class="sxs-lookup"><span data-stu-id="b9e98-123">This file is located in the _ *_CustomEvents_*\* subdirectory of your user-defined TraceX installation directory, which defaults to c:\Azure_RTOS\TraceX.</span></span> <span data-ttu-id="b9e98-124">На рис. 30 показан пример пути к каталогу.</span><span class="sxs-lookup"><span data-stu-id="b9e98-124">An example directory path is shown in Figure 30.</span></span>

<span data-ttu-id="b9e98-125">![Снимок экрана: пример пути к каталогу](./media/user-guide/custom_events_folder.png)
**РИС. 30**</span><span class="sxs-lookup"><span data-stu-id="b9e98-125">![Screenshot of an example directory path.](./media/user-guide/custom_events_folder.png)
**FIGURE 30**</span></span>

<span data-ttu-id="b9e98-126">Файл конфигурации пользовательского события ***tracex_custom.trxc*** — это простой текстовый файл в формате ASCII, содержащий ноль определений пользовательских событий или более.</span><span class="sxs-lookup"><span data-stu-id="b9e98-126">The ***tracex_custom.trxc*** custom event configuration file is a simple ASCII text file containing zero or more custom event definitions.</span></span> <span data-ttu-id="b9e98-127">Формат файла выглядит следующим образом.</span><span class="sxs-lookup"><span data-stu-id="b9e98-127">The format of the file is as follows:</span></span>

```c
//Comments
**Start **
[custom event definition(s)] **End **
```

<span data-ttu-id="b9e98-128">Каждая строка между метками Start и End используется для определения одного пользовательского события.</span><span class="sxs-lookup"><span data-stu-id="b9e98-128">Each line between Start and End is used to define a single custom event.</span></span> <span data-ttu-id="b9e98-129">В TraceX доступна версия шаблона этого файла без определенных пользовательских событий (между метками Start и End ничего не указано).</span><span class="sxs-lookup"><span data-stu-id="b9e98-129">TraceX provides a template version of this file with no custom events defined (nothing between the "Start" and "End" labels).</span></span> <span data-ttu-id="b9e98-130">Определение пользовательского события имеет следующий формат.</span><span class="sxs-lookup"><span data-stu-id="b9e98-130">The format of a custom event definition is as follows:</span></span>

<span data-ttu-id="b9e98-131">**number, name, abbreviation, top_color, bottom_color, label1, label2, label2, label4**</span><span class="sxs-lookup"><span data-stu-id="b9e98-131">**number, name, abbreviation, top_color, bottom_color, label1, label2, label2, label4**</span></span>

<span data-ttu-id="b9e98-132">где:</span><span class="sxs-lookup"><span data-stu-id="b9e98-132">where:</span></span>

- <span data-ttu-id="b9e98-133">number определяет номер определяемого пользователем события в диапазоне от 4096 до 65535 включительно.</span><span class="sxs-lookup"><span data-stu-id="b9e98-133">number: Defines the user-defined event number, between 4096 and 65535, inclusive.</span></span></th>
- <span data-ttu-id="b9e98-134">name определяет логическое имя для определяемого пользователем события.</span><span class="sxs-lookup"><span data-stu-id="b9e98-134">name: Defines the logical name for the user-defined event.</span></span></td>
- <span data-ttu-id="b9e98-135">abbreviation определяет двухбуквенное сокращенное обозначение определяемого пользователем события.</span><span class="sxs-lookup"><span data-stu-id="b9e98-135">abbreviation: Defines the two-letter user-defined event abbreviation.</span></span></td>
- <span data-ttu-id="b9e98-136">top_color определяет значение RGB для верхней половины значка, которое представляет собой трехзначное число в круглых скобках.</span><span class="sxs-lookup"><span data-stu-id="b9e98-136">top_color: Defines the RGB value for the top-half of the icon, which is a three-digit number in parenthesis.</span></span> <span data-ttu-id="b9e98-137">Далее приведены некоторые стандартные определения RGB.</span><span class="sxs-lookup"><span data-stu-id="b9e98-137">Some typical RGB definitions are</span></span>
  - <span data-ttu-id="b9e98-138">BLACK = (0,0,0)</span><span class="sxs-lookup"><span data-stu-id="b9e98-138">BLACK = (0,0,0)</span></span>       
  - <span data-ttu-id="b9e98-139">WHITE = (255,255,255)</span><span class="sxs-lookup"><span data-stu-id="b9e98-139">WHITE = (255,255,255)</span></span>
  - <span data-ttu-id="b9e98-140">RED = (255,0,0)</span><span class="sxs-lookup"><span data-stu-id="b9e98-140">RED = (255,0,0)</span></span>     
  - <span data-ttu-id="b9e98-141">GREEN = (0,255,0)</span><span class="sxs-lookup"><span data-stu-id="b9e98-141">GREEN = (0,255,0)</span></span>     
  - <span data-ttu-id="b9e98-142">BLUE = (0,0,255)</span><span class="sxs-lookup"><span data-stu-id="b9e98-142">BLUE = (0,0,255)</span></span>     
  - <span data-ttu-id="b9e98-143">YELLOW = (255,255,0)</span><span class="sxs-lookup"><span data-stu-id="b9e98-143">YELLOW = (255,255,0)</span></span>   
  - <span data-ttu-id="b9e98-144">CYAN = (0,255,255)</span><span class="sxs-lookup"><span data-stu-id="b9e98-144">CYAN = (0,255,255)</span></span>   
  - <span data-ttu-id="b9e98-145">MAGENTA = (255,0,255)</span><span class="sxs-lookup"><span data-stu-id="b9e98-145">MAGENTA = (255,0,255)</span></span>   
  <span data-ttu-id="b9e98-146">Используя спецификацию RBG, пользователь может применять широкий спектр цветов при создании настраиваемых значков.</span><span class="sxs-lookup"><span data-stu-id="b9e98-146">Using the RBG specification gives the user a broad range of colors for each user-defined icon.</span></span> <span data-ttu-id="b9e98-147">Дополнительные сведения об определениях цветов RBG см. по адресу https://en.wikipedia.org/wiki/RGB#Digital_representations.</span><span class="sxs-lookup"><span data-stu-id="b9e98-147">For more information on RBG color definition, see: https://en.wikipedia.org/wiki/RGB#Digital_representations</span></span>
- <span data-ttu-id="b9e98-148">botton_color определяет значение RGB для нижней половины значка, которое представляет собой трехзначное число в круглых скобках.</span><span class="sxs-lookup"><span data-stu-id="b9e98-148">botton_color: Defines the RGB value for the bottom half of the icon, which is a three-digit number in parenthesis.</span></span>
- <span data-ttu-id="b9e98-149">label1 — метка для поля \***info_field_1** _, как указано в вызове службы _ \*_tx_trace_user_event_insert_\*\*.</span><span class="sxs-lookup"><span data-stu-id="b9e98-149">label1: Label for ***info_field_1** _, as specified in the _ *_tx_trace_user_event_insert_** call.</span></span>
- <span data-ttu-id="b9e98-150">label2 — метка для поля \***info_field_2** _, как указано в вызове службы _ \*_tx_trace_user_event_insert_\*\*.</span><span class="sxs-lookup"><span data-stu-id="b9e98-150">label2: Label for ***info_field_2** _, as specified in the _ *_tx_trace_user_event_insert_** call.</span></span>
- <span data-ttu-id="b9e98-151">label3 — метка для поля \***info_field_3** _, как указано в вызове службы _ \*_tx_trace_user_event_insert_\*\*.</span><span class="sxs-lookup"><span data-stu-id="b9e98-151">label3: Label for ***info_field_3** _, as specified in the _ *_tx_trace_user_event_insert_** call.</span></span>
- <span data-ttu-id="b9e98-152">label4 — метка для поля \***info_field_4** _, как указано в вызове службы _ \*_tx_trace_user_event_insert_\*\*.</span><span class="sxs-lookup"><span data-stu-id="b9e98-152">label4: Label for ***info_field_4** _, as specified in the _ *_tx_trace_user_event_insert_** call.</span></span>

<span data-ttu-id="b9e98-153">Примеры определений для каждого из двух определяемых пользователем событий, используемых в этой главе, показаны на рис. 10.4.</span><span class="sxs-lookup"><span data-stu-id="b9e98-153">Example definitions for each of the two user-defined events used in this chapter are shown in Figure 10.4.</span></span> <span data-ttu-id="b9e98-154">Первое определение предназначено для события 4096 в строке 5 файла \***tracex_custom.trxc** _.</span><span class="sxs-lookup"><span data-stu-id="b9e98-154">The first definition is for event 4096 at line 5 of the \***tracex_custom.trxc** _ file.</span></span> <span data-ttu-id="b9e98-155">Это определение задает пользовательскому событию 4096 имя _\*First_User_Event\*\*, присваивает двухбуквенное сокращение **FE**, выделяет верхнюю часть значка красным цветом, выделяет нижнюю часть значка зеленым цветом и задает полям сведений имена **First_Info1**, **First_Info2**, **First_Info3** и **First_Info4**.</span><span class="sxs-lookup"><span data-stu-id="b9e98-155">This definition gives user-defined event 4096 the name _\*First_User_Event\*\*, specifies a two-letter abbreviation of **FE**, makes the top portion of the icon red, the bottom portion of the icon green, and names the information fields as **First_Info1**, **First_Info2**, **First_Info3**, and **First_Info4**.</span></span> <span data-ttu-id="b9e98-156">Определяемое пользователем событие 4098 определяется аналогичным образом в строке 6 файла **_tracex_custom.trxc_**.</span><span class="sxs-lookup"><span data-stu-id="b9e98-156">User-defined event 4098 is defined similarly at line 6 of **_tracex_custom.trxc_**.</span></span>

<span data-ttu-id="b9e98-157">![Снимок экрана: примеры определений для определяемых пользователем событий](./media/user-guide/10.4.png)
**РИС. 31**</span><span class="sxs-lookup"><span data-stu-id="b9e98-157">![Screenshot of the example definitions for the user-defined events.](./media/user-guide/10.4.png)
**FIGURE 31**</span></span>

<span data-ttu-id="b9e98-158">Так как TraceX считывает файл \***tracex_custom.trxc** _ во время инициализации, для вступления в силу определений настраиваемых значков необходимо выйти из TraceX и затем перезапустить ее.</span><span class="sxs-lookup"><span data-stu-id="b9e98-158">Since the \***tracex_custom.trxc** _ file is read by TraceX during initialization, TraceX must be exited and restarted before the custom icon definitions can take effect.</span></span> <span data-ttu-id="b9e98-159">На рис. 32 показано отображение определяемых пользователем событий 452 и 453 с настраиваемыми значками, определенными в файле _\*_tracex_custom.trxc_\*\*.</span><span class="sxs-lookup"><span data-stu-id="b9e98-159">Figure 32 shows the TraceX display of user-defined events 452 and 453 with the custom event icons defined in _\*_tracex_custom.trxc_\*\*.</span></span>

<span data-ttu-id="b9e98-160">![Снимок экрана: TraceX с отображением определяемых пользователем событий с настраиваемыми значками](./media/user-guide/10.5.png)
**РИС. 32**</span><span class="sxs-lookup"><span data-stu-id="b9e98-160">![Screenshot of the TraceX display of user defined events with the custom event icons.](./media/user-guide/10.5.png)
**FIGURE 32**</span></span>

<span data-ttu-id="b9e98-161">Дополнительные сведения в определении пользовательского события отображаются при двойном щелчке события, наведении на него курсора или нажатии кнопки текущего события.</span><span class="sxs-lookup"><span data-stu-id="b9e98-161">The additional information in the custom event definition is shown when the event you select using a double-click, mouse-over, or clicking the current event button.</span></span> <span data-ttu-id="b9e98-162">На рис. 33 показан выбор события 452 двойным щелчком мыши.</span><span class="sxs-lookup"><span data-stu-id="b9e98-162">Figure 33 shows the double-click selection on event 452.</span></span> <span data-ttu-id="b9e98-163">Имя события и поля сведений соответствуют примеру определения, которое было добавлено в файл ***tracex_custom.trxc***.</span><span class="sxs-lookup"><span data-stu-id="b9e98-163">The event name and information fields all match the sample definition that was added to ***tracex_custom.trxc***.</span></span>

<span data-ttu-id="b9e98-164">![Снимок экрана: выбор события двойным щелчком мыши](./media/user-guide/10.6.png)
**РИС. 33**</span><span class="sxs-lookup"><span data-stu-id="b9e98-164">![Screenshot of the double-click selection on an event.](./media/user-guide/10.6.png)
**FIGURE 33**</span></span>
