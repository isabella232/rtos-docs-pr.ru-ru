---
title: Глава 1. Введение в NetX Duo TFTP для ОСРВ Azure
description: Протокол TFTP — это нетребовательный к ресурсам протокол, созданный для передачи файлов.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4431b23e143d05214090547e7f179a6f5def8217
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814527"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-tftp"></a><span data-ttu-id="dd2cd-103">Глава 1. Введение в NetX Duo TFTP для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="dd2cd-103">Chapter 1 - Introduction to Azure RTOS NetX Duo TFTP</span></span> 

<span data-ttu-id="dd2cd-104">Протокол TFTP — это нетребовательный к ресурсам протокол, созданный для передачи файлов.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-104">The Trivial File Transfer Protocol (TFTP) is a lightweight protocol designed for file transfers.</span></span> <span data-ttu-id="dd2cd-105">В отличие от более надежных протоколов, TFTP не выполняет развернутую проверку ошибок и может иметь ограниченную производительность, так как работает в режиме остановки и ожидания.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-105">Unlike more robust protocols, TFTP does not perform extensive error checking and can also have limited performance because it is a stop-and-wait protocol.</span></span> <span data-ttu-id="dd2cd-106">Отправив пакет данных TFTP, отправитель ожидает подтверждения от получателя.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-106">After a TFTP data packet is sent, the sender waits for an ACK to be returned by the recipient.</span></span> <span data-ttu-id="dd2cd-107">Хотя это очень простая операция, она ограничивает общую пропускную способность TFTP.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-107">Although this is simple, it does limit the overall TFTP throughput.</span></span> <span data-ttu-id="dd2cd-108">Пакет TFTP позволяет узлам использовать протокол TFTP в IP-сетях.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-108">The TFTP package enables hosts to use the TFTP protocol over IP networks.</span></span>

## <a name="tftp-requirements"></a><span data-ttu-id="dd2cd-109">Требования протокола TFTP</span><span class="sxs-lookup"><span data-stu-id="dd2cd-109">TFTP Requirements</span></span>

<span data-ttu-id="dd2cd-110">Для надлежащей работы часть TFTP-клиента в пакете NetX Duo TFTP требует, чтобы экземпляр IP был уже создан.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-110">In order to function properly, the TFTP Clients portion of the NetX Duo TFTP package requires that an IP instance has already been created.</span></span> <span data-ttu-id="dd2cd-111">Кроме того, в таком экземпляре IP должен быть включен протокол UDP.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-111">In addition, UDP must be enabled on that same IP instance.</span></span> <span data-ttu-id="dd2cd-112">Для части клиента в пакете NetX Duo TFTP нет других требований.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-112">The Client portion of the NetX Duo TFTP package has no further requirements.</span></span>

<span data-ttu-id="dd2cd-113">Часть TFTP-сервера в пакете NetX Duo TFTP имеет несколько дополнительных требований.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-113">The TFTP Server portion of the NetX Duo TFTP package has several additional requirements.</span></span> <span data-ttu-id="dd2cd-114">Во-первых, ему требуется полный доступ к *хорошо известному порту UDP 69* для обработки всех клиентских запросов TFTP.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-114">First, it requires complete access to the UDP *well known port 69* for handling all client TFTP requests.</span></span> <span data-ttu-id="dd2cd-115">TFTP-сервер также разработан для работы с внедренной файловой системой FileX.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-115">The TFTP Server is also designed for use with the FileX embedded file system.</span></span> <span data-ttu-id="dd2cd-116">Если система FileX недоступна, пользователь может портировать используемые разделы FileX в собственную среду.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-116">If FileX is not available, the user may port the portions of FileX used to their own environment.</span></span> <span data-ttu-id="dd2cd-117">Этот процесс рассматривается в последующих разделах этого руководства.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-117">This is discussed in later sections of this guide.</span></span>

## <a name="tftp-file-names"></a><span data-ttu-id="dd2cd-118">Имена файлов TFTP</span><span class="sxs-lookup"><span data-stu-id="dd2cd-118">TFTP File Names</span></span> 

<span data-ttu-id="dd2cd-119">Имена файлов TFTP должны иметь формат целевой файловой системы.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-119">TFTP file names should be in the format of the target file system.</span></span> <span data-ttu-id="dd2cd-120">Они должны быть строками символов ASCII с завершающим нулем и сведениями о полном пути, если это необходимо.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-120">They should be NULL terminated ASCII strings, with full path information if necessary.</span></span> <span data-ttu-id="dd2cd-121">В реализации NetX Duo TFTP ограничение на размер имен файлов TFTP отсутствует.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-121">There is no specified limit in the size of TFTP file names in the NetX Duo TFTP implementation.</span></span>

## <a name="tftp-messages"></a><span data-ttu-id="dd2cd-122">Сообщения TFTP</span><span class="sxs-lookup"><span data-stu-id="dd2cd-122">TFTP Messages</span></span>

<span data-ttu-id="dd2cd-123">TFTP имеет очень простой механизм для открытия, чтения, записи и закрытия файлов.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-123">The TFTP has a very simple mechanism for opening, reading, writing, and closing files.</span></span> <span data-ttu-id="dd2cd-124">Под заголовком UDP просто указываются 2–4 байта заголовка TFTP.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-124">There are basically 2-4 bytes of TFTP header underneath the UDP header.</span></span> <span data-ttu-id="dd2cd-125">Определение для сообщений открытия файла в TFTP имеет следующий формат:</span><span class="sxs-lookup"><span data-stu-id="dd2cd-125">The definition of the TFTP file open messages has the following format:</span></span>

<span data-ttu-id="dd2cd-126">**oooof…f0OCTET0**</span><span class="sxs-lookup"><span data-stu-id="dd2cd-126">**oooof…f0OCTET0**</span></span>

<span data-ttu-id="dd2cd-127">Где:</span><span class="sxs-lookup"><span data-stu-id="dd2cd-127">Where:</span></span>

- <span data-ttu-id="dd2cd-128">**oooo** — 2-байтовое поле Opcode.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-128">**oooo** 2-byte Opcode field</span></span>  
<span data-ttu-id="dd2cd-129">0x0001 -> открыть для чтения.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-129">0x0001 -> Open for read</span></span>  
<span data-ttu-id="dd2cd-130">0x0002 -> открыть для записи.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-130">0x0002 -> Open for write</span></span>

- <span data-ttu-id="dd2cd-131">**f…f** — n-байтовое поле с именем файла.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-131">**f…f** n-byte Filename field</span></span>

- <span data-ttu-id="dd2cd-132">0 — 1-байтовый завершающий символ NULL.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-132">0  1-byte NULL termination character</span></span>

- <span data-ttu-id="dd2cd-133">**OCTET** — OCTET ASCII для указания передачи в двоичном формате.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-133">**OCTET** ASCII “OCTET” to specify binary transfer</span></span>

- <span data-ttu-id="dd2cd-134">0 — 1-байтовый завершающий символ NULL.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-134">0  1-byte NULL termination character</span></span>

<span data-ttu-id="dd2cd-135">Определение сообщений о записи, подтверждении и ошибке в TFTP немного отличаются и имеют такой вид:</span><span class="sxs-lookup"><span data-stu-id="dd2cd-135">The definition of the TFTP write, ACK, and error messages are slightly different and are defined as follows:</span></span>

<span data-ttu-id="dd2cd-136">**oooobbbbd…d**</span><span class="sxs-lookup"><span data-stu-id="dd2cd-136">**oooobbbbd…d**</span></span>

<span data-ttu-id="dd2cd-137">Где:</span><span class="sxs-lookup"><span data-stu-id="dd2cd-137">Where:</span></span>

- <span data-ttu-id="dd2cd-138">**oooo** — 2-байтовое поле Opcode.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-138">**oooo** 2-byte Opcode field</span></span>  
<span data-ttu-id="dd2cd-139">0x0003 -> пакет данных.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-139">0x0003 -> Data packet</span></span>  
<span data-ttu-id="dd2cd-140">0x0004 -> подтверждение последней операции чтения.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-140">0x0004 -> ACK for last read</span></span>  
<span data-ttu-id="dd2cd-141">0x0005 -> условие ошибки.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-141">0x0005 -> Error condition</span></span>  

- <span data-ttu-id="dd2cd-142">**bbbb** — 2-байтовое поле с номером блока (1–n).</span><span class="sxs-lookup"><span data-stu-id="dd2cd-142">**bbbb** 2-byte Block Number field (1-n)</span></span>

- <span data-ttu-id="dd2cd-143">**d…d** — n-байтовое поле данных.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-143">**d…d** n-byte Data field</span></span>


- <span data-ttu-id="dd2cd-144">0x0001 (чтение) — имя файла 0 OCTET 0.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-144">0x0001 (read) File Name 0 OCTET 0</span></span>

- <span data-ttu-id="dd2cd-145">0x0002 (запись) — имя файла 0 OCTET 0.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-145">0x0002 (write) File Name 0 OCTET 0</span></span>

## <a name="tftp-communication"></a><span data-ttu-id="dd2cd-146">Обмен данными по TFTP</span><span class="sxs-lookup"><span data-stu-id="dd2cd-146">TFTP Communication</span></span>

<span data-ttu-id="dd2cd-147">TFTP-серверы используют хорошо известный порт UDP 69 для прослушивания запросов клиентов.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-147">TFTP Servers utilize the well-known UDP port 69 to listen for Client requests.</span></span> <span data-ttu-id="dd2cd-148">Сокеты TFTP-клиенты могут привязываться к любому доступному порту UDP.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-148">TFTP Client sockets may bind to any available UDP port.</span></span> <span data-ttu-id="dd2cd-149">Полезные данные пакета, включающие файл для передачи или скачивания, отправляются фрагментами по 512 байт при этом последний пакет может содержать менее 512 байт.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-149">Data packet payload containing the file to upload or download is sent in 512 byte chunks, until the last packet containing < 512 bytes.</span></span> <span data-ttu-id="dd2cd-150">Поэтому пакет, содержащий менее 512 байт, обозначает конец файла.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-150">Therefore a packet containing fewer than 512 bytes signals the end of file.</span></span> <span data-ttu-id="dd2cd-151">Общая последовательность событий выглядит следующим образом.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-151">The general sequence of events is as follows:</span></span>

<span data-ttu-id="dd2cd-152">Запросы TFTP на чтение файлов:</span><span class="sxs-lookup"><span data-stu-id="dd2cd-152">TFTP Read File Requests:</span></span>

1.  <span data-ttu-id="dd2cd-153">Клиент отправляет запрос открытия для чтения с именем файла и ожидает ответ от сервера.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-153">The Client issues an “Open For Read” request with the file name and waits for a reply from the Server.</span></span>

2.  <span data-ttu-id="dd2cd-154">Сервер отправляет первые 512 байт файла (или менее, если размер файла не превышает 512 байт).</span><span class="sxs-lookup"><span data-stu-id="dd2cd-154">The Server sends the first 512 bytes of the file or less if the file size is less than 512 bytes.</span></span>

3.  <span data-ttu-id="dd2cd-155">Клиент получает данные, отправляет подтверждение и ожидает следующий пакет от сервера для файлов, содержащих более 512 байт.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-155">The Client receives data, sends an ACK, and waits for the next packet from the Server for files containing more than 512 bytes.</span></span>

4.  <span data-ttu-id="dd2cd-156">Последовательность заканчивается, когда клиент получает пакет, содержащий менее 512 байт.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-156">The sequence ends when the Client receives a packet containing fewer than 512 bytes.</span></span>

<span data-ttu-id="dd2cd-157">Запросы TFTP на запись:</span><span class="sxs-lookup"><span data-stu-id="dd2cd-157">TFTP Write Requests:</span></span>

1.  <span data-ttu-id="dd2cd-158">Клиент отправляет запрос открытия для записи с именем файла и ожидает подтверждения с номером блока 0 от сервера.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-158">The Client issues an “Open for Write” request with the file name and waits for an ACK with a block number of 0 from the Server.</span></span>

2.  <span data-ttu-id="dd2cd-159">Если сервер готов к записи в файл, он отправляет подтверждение с нулевым номером блока.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-159">When the Server is ready to write the file, it sends an ACK with a block number of zero.</span></span>

3.  <span data-ttu-id="dd2cd-160">Клиент отправляет первые 512 байт файла (или меньше для файлов размером не более 512 байт) на сервер и ожидает подтверждения.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-160">The Client sends the first 512 bytes of the file (or less for files less than 512 bytes) to the Server and waits for an ACK back.</span></span>

4.  <span data-ttu-id="dd2cd-161">Сервер отправляет подтверждение после записи байтов.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-161">The Server sends an ACK after the bytes are written.</span></span>

5.  <span data-ttu-id="dd2cd-162">Последовательность заканчивается, когда клиент завершает запись пакета, содержащего менее 512 байт.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-162">The sequence ends when the Client completes writing a packet containing fewer than 512 bytes.</span></span>
 

## <a name="tftp-server-session-timer"></a><span data-ttu-id="dd2cd-163">Таймер сеанса TFTP-сервера</span><span class="sxs-lookup"><span data-stu-id="dd2cd-163">TFTP Server Session Timer</span></span>

<span data-ttu-id="dd2cd-164">TFTP-сервер имеет ограниченное количество слотов для запросов клиента.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-164">The TFTP Server has a limited number of client request slots.</span></span> <span data-ttu-id="dd2cd-165">Если сеанс клиента завершается, такой слот не может быть использован повторно.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-165">If a client session appears to be dropped, that slot cannot be available for re-use.</span></span> <span data-ttu-id="dd2cd-166">Но если включен параметр NX_TFTP_SERVER_RETRANSMIT_ENABLE, TFTP-сервер NetX Duo создает таймер сеанса, который отслеживает время ожидания для каждого сеанса клиента.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-166">However if the NX_TFTP_SERVER_RETRANSMIT_ENABLE option is enabled, the NetX Duo TFTP Server creates an session timer that monitors the timeout on each of its client sessions.</span></span> <span data-ttu-id="dd2cd-167">По истечении времени ожидания сеанс завершается, а все открытые файлы закрываются.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-167">When a session timeout expires it is terminated and any open files are closed.</span></span> <span data-ttu-id="dd2cd-168">После этого слот становится доступен другому запросу TFTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-168">Thus the ‘slot’ becomes available for another TFTP Client request.</span></span>

<span data-ttu-id="dd2cd-169">Чтобы задать время ожидания, измените параметр конфигурации NX_TFTP_SERVER_RETRANSMIT_TIMEOUT, для которого по умолчанию задано значение в 200 тактов таймера.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-169">To set the timeout, adjust the configuration option NX_TFTP_SERVER_RETRANSMIT_TIMEOUT which by default is 200 timer ticks.</span></span> <span data-ttu-id="dd2cd-170">Интервал для проверки времени ожидания сеанса задается параметром NX_TFTP_SERVER_TIMEOUT_PERIOD, который по умолчанию имеет значение в 20 тактов таймера.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-170">The interval between which session timeouts are checked is set by the NX_TFTP_SERVER_TIMEOUT_PERIOD which is 20 timer ticks by default.</span></span>

<span data-ttu-id="dd2cd-171">Если TFTP-клиент передал (записал) файлы на носитель FileX TFTP, такой носитель нужно очистить, чтобы данные можно было записать с электронного диска TFTP-сервера на базовый носитель (дисковая память TFTP-клиента).</span><span class="sxs-lookup"><span data-stu-id="dd2cd-171">When the TFTP Client has uploaded (written) files to the TFTP FileX media, the media needs to be flushed so that data can be written from the TFTP server ram disk to the underlying media (TFTP Client disk memory).</span></span> <span data-ttu-id="dd2cd-172">Это можно сделать с помощью службы fx_media_flush, если приложение не требует закрыть TFTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-172">This can be done using the fx_media_flush service if the application does not wish to close the TFTP Server.</span></span>

<span data-ttu-id="dd2cd-173">Но после закрытия TFTP-сервера приложению нужно (если оно больше не будет использовать носитель FileX) закрыть носитель с помощью службы fx_media_close.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-173">However, after closing the TFTP server, the application should, if it has no further use for the FileX media, then close the media using the fx_media_close service.</span></span> <span data-ttu-id="dd2cd-174">Это приведет к записи данных обратно на диск TFTP-клиента, закрытию открытых файлов и обновлению сведений о каталоге для носителя.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-174">This will flush the file data back to the TFTP Client disk, close open files, and update the directory information to the media.</span></span>

<span data-ttu-id="dd2cd-175">Демонстрацию этого можно найти в разделе "Небольшой пример" этой главы.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-175">The “Small Example” section in this chapter demonstrates this.</span></span>

<span data-ttu-id="dd2cd-176">Третий вариант обновления носителя FileX — это компиляция библиотеки FileX с параметрами FX_FAULT_TOLERANT или FX_FAULT_TOLERANT_DATA вместо явного использования служб FileX.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-176">A third option for updating the FileX media is to compile the FileX library with the FX_FAULT_TOLERANT or the FX_FAULT_TOLERANT_DATA options instead of using FileX services explicitly.</span></span> <span data-ttu-id="dd2cd-177">Если эти параметры определены, FileX автоматически передает запросы на запись драйверу носителя.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-177">If defined, FileX automatically passes write requests to the media driver.</span></span> <span data-ttu-id="dd2cd-178">Такие параметры могут ограничить производительность, но обеспечивают повышенную защиту от потерь данных файлов или кластеров.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-178">These options may limit performance but offer greater protection from lost file data or lost clusters.</span></span> <span data-ttu-id="dd2cd-179">Дополнительные сведения и общие данные о FileX см. в руководстве пользователя Express Logic FileX.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-179">For more information about this and FileX in general, please see the Express Logic FileX User Guide.</span></span>

## <a name="tftp-multi-thread-support"></a><span data-ttu-id="dd2cd-180">Поддержка нескольких потоков в TFTP</span><span class="sxs-lookup"><span data-stu-id="dd2cd-180">TFTP Multi-Thread Support</span></span>

<span data-ttu-id="dd2cd-181">Службы TFTP-клиента NetX Duo можно вызывать из нескольких потоков одновременно.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-181">The NetX Duo TFTP Client services can be called from multiple threads simultaneously.</span></span> <span data-ttu-id="dd2cd-182">Однако запросы на чтение или запись для конкретного экземпляра TFTP-клиента должны выполняться последовательно из одного потока.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-182">However, read or write requests for a particular TFTP Client instance should be done in sequence from the same thread.</span></span>

## <a name="tftp-rfcs"></a><span data-ttu-id="dd2cd-183">Стандарты RFC для протокола TFTP</span><span class="sxs-lookup"><span data-stu-id="dd2cd-183">TFTP RFCs</span></span>

<span data-ttu-id="dd2cd-184">NetX Duo TFTP совместим с RFC 1350 и связанными стандартами RFC.</span><span class="sxs-lookup"><span data-stu-id="dd2cd-184">NetX Duo TFTP is compliant with RFC1350 and related RFCs.</span></span>

