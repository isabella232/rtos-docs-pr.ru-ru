---
title: Глава 1. Введение в NetX HTTP
description: В этом документе описывается протокол HTTP, предназначенный для передачи содержимого в Интернете.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6137cc0d8deb753d784be844d5abc7778dd62295
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815199"
---
# <a name="chapter-1---introduction-to-netx-http"></a><span data-ttu-id="cb0b2-103">Глава 1. Введение в NetX HTTP</span><span class="sxs-lookup"><span data-stu-id="cb0b2-103">Chapter 1 - Introduction to NetX HTTP</span></span>

<span data-ttu-id="cb0b2-104">Протокол HTTP предназначен для передачи содержимого в Интернете.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-104">The Hypertext Transfer Protocol (HTTP) is a protocol designed for transferring content on the Web.</span></span> <span data-ttu-id="cb0b2-105">HTTP — это простой протокол, который использует для передачи содержимого надежные службы протокола TCP.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-105">HTTP is a simple protocol that utilizes reliable Transmission Control Protocol (TCP) services to perform its content transfer function.</span></span> <span data-ttu-id="cb0b2-106">Благодаря этому HTTP считается очень надежным протоколом для обмена содержимым.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-106">Because of this, HTTP is a highly reliable content transfer protocol.</span></span> <span data-ttu-id="cb0b2-107">Также HTTP является одним из самых часто используемых протоколов приложений.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-107">HTTP is one of the most used application protocols.</span></span> <span data-ttu-id="cb0b2-108">Все операции в Интернете используют протокол HTTP.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-108">All operations on the Web utilize the HTTP protocol.</span></span>

## <a name="http-requirements"></a><span data-ttu-id="cb0b2-109">Требования для протокола HTTP</span><span class="sxs-lookup"><span data-stu-id="cb0b2-109">HTTP Requirements</span></span>

<span data-ttu-id="cb0b2-110">Для правильной работы пакета NetX HTTP требуется установить NetX 5.2 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-110">In order to function properly, the NetX HTTP package requires that a NetX (version 5.2 or later) is installed.</span></span> <span data-ttu-id="cb0b2-111">Кроме того, должен быть создан экземпляр IP, для которого включено использование протокола TCP.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-111">In addition, an IP instance must already be created and TCP must be enabled on that same IP instance.</span></span> <span data-ttu-id="cb0b2-112">Этот процесс показан в демонстрационном файле в разделе "Пример небольшой системы" **главы 2**.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-112">The demo file in section “Small Example System” in **Chapter 2** will demonstrate how this is done.</span></span>

<span data-ttu-id="cb0b2-113">Для HTTP-клиента из пакета NetX HTTP больше нет дополнительных требований.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-113">The HTTP Client portion of the NetX HTTP package has no further requirements.</span></span>

<span data-ttu-id="cb0b2-114">Но для HTTP-сервера из пакета NetX HTTP существует ряд дополнительных требований.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-114">The HTTP Server portion of the NetX HTTP package has several additional requirements.</span></span> <span data-ttu-id="cb0b2-115">Ему требуется полный доступ к *стандартному TCP-порту 80* для обработки всех запросов от HTTP-клиентов.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-115">First, it requires complete access to TCP *well-known port 80* for handling all Client HTTP requests.</span></span> <span data-ttu-id="cb0b2-116">HTTP-сервер также разработан для работы с внедренной файловой системой FileX.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-116">The HTTP Server is also designed for use with the FileX embedded file system.</span></span> <span data-ttu-id="cb0b2-117">Если система FileX недоступна, пользователь может перенести используемые разделы FileX в собственную среду.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-117">If FileX is not available, the user may port the portions of FileX used to their own environment.</span></span> <span data-ttu-id="cb0b2-118">Этот процесс рассматривается в последующих разделах этого руководства.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-118">This is discussed in later sections of this guide.</span></span>

## <a name="http-constraints"></a><span data-ttu-id="cb0b2-119">Ограничения протокола HTTP</span><span class="sxs-lookup"><span data-stu-id="cb0b2-119">HTTP Constraints</span></span> 

<span data-ttu-id="cb0b2-120">Протокол NetX HTTP реализует стандарт HTTP 1.0.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-120">The NetX HTTP protocol implements the HTTP 1.0 standard.</span></span> <span data-ttu-id="cb0b2-121">Но существует ряд дополнительных ограничений:</span><span class="sxs-lookup"><span data-stu-id="cb0b2-121">However, there are following constraints:</span></span>

1.  <span data-ttu-id="cb0b2-122">не поддерживаются постоянные подключения;</span><span class="sxs-lookup"><span data-stu-id="cb0b2-122">Persistent connections are not supported</span></span>

2.  <span data-ttu-id="cb0b2-123">не поддерживаются конвейеры обработки запросов;</span><span class="sxs-lookup"><span data-stu-id="cb0b2-123">Request pipelining is not supported</span></span>

3.  <span data-ttu-id="cb0b2-124">HTTP-сервер поддерживает обычную проверку подлинности и дайджест-проверку подлинности MD5, но не поддерживает MD5-sess;</span><span class="sxs-lookup"><span data-stu-id="cb0b2-124">The HTTP Server supports both basic and MD5 digest authentication, but not MD5-sess.</span></span> <span data-ttu-id="cb0b2-125">в настоящее время HTTP-клиент поддерживает только обычную проверку подлинности;</span><span class="sxs-lookup"><span data-stu-id="cb0b2-125">At present, the HTTP Client supports only basic authentication.</span></span>

4.  <span data-ttu-id="cb0b2-126">не поддерживается сжатие содержимого;</span><span class="sxs-lookup"><span data-stu-id="cb0b2-126">No content compression is supported.</span></span>

5.  <span data-ttu-id="cb0b2-127">не поддерживаются запросы TRACE, OPTIONS и CONNECT;</span><span class="sxs-lookup"><span data-stu-id="cb0b2-127">TRACE, OPTIONS, and CONNECT requests are not supported.</span></span>

6.  <span data-ttu-id="cb0b2-128">пул пакетов, связанный с HTTP-сервером или HTTP-клиентом, должен быть достаточно большим для размещения заголовка HTTP целиком;</span><span class="sxs-lookup"><span data-stu-id="cb0b2-128">The packet pool associated with the HTTP Server or Client must be large enough to hold the complete HTTP header.</span></span>

7.  <span data-ttu-id="cb0b2-129">службы HTTP-клиента предназначены только для передачи содержимого, а средства для отображения в этом пакете не предоставляются.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-129">HTTP Client services are for content transfer only—there are no display utilities provided in this package.</span></span>

## <a name="http-url-resource-names"></a><span data-ttu-id="cb0b2-130">URL-адрес HTTP (имена ресурсов)</span><span class="sxs-lookup"><span data-stu-id="cb0b2-130">HTTP URL (Resource Names)</span></span>

<span data-ttu-id="cb0b2-131">Протокол HTTP разработан для передачи содержимого через Интернет.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-131">The HTTP protocol is designed to transfer content on Web.</span></span> <span data-ttu-id="cb0b2-132">Запрашиваемое содержимое определяется URL-адресом.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-132">The requested content is specified by the Universal Resource Locator (URL).</span></span> <span data-ttu-id="cb0b2-133">Это основной компонент каждого HTTP-запроса.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-133">This is the primary component of every HTTP request.</span></span> <span data-ttu-id="cb0b2-134">URL-адреса всегда начинаются с символа "/" и обычно обозначают определенные файлы на HTTP-сервере.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-134">URLs always start with a “/” character and typically correspond to files on the HTTP Server.</span></span> <span data-ttu-id="cb0b2-135">Ниже приведены типичные расширения файлов, используемые с протоколом HTTP:</span><span class="sxs-lookup"><span data-stu-id="cb0b2-135">Common HTTP file extensions are shown below:</span></span>

- <span data-ttu-id="cb0b2-136">**HTM (или HTML)** : HTML-файлы (HTML);</span><span class="sxs-lookup"><span data-stu-id="cb0b2-136">**.htm (or .html)** Hypertext Markup Language (HTML)</span></span>
- <span data-ttu-id="cb0b2-137">**TXT**: открытый текст ASCII;</span><span class="sxs-lookup"><span data-stu-id="cb0b2-137">**.txt** Plain ASCII text</span></span>
- <span data-ttu-id="cb0b2-138">**GIF**: двоичное изображение GIF;</span><span class="sxs-lookup"><span data-stu-id="cb0b2-138">**.gif** Binary GIF image</span></span>
- <span data-ttu-id="cb0b2-139">**XBM**: двоичное изображение Xbitmap.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-139">**.xbm** Binary Xbitmap image</span></span>

## <a name="http-client-requests"></a><span data-ttu-id="cb0b2-140">Запросы HTTP-клиента</span><span class="sxs-lookup"><span data-stu-id="cb0b2-140">HTTP Client Requests</span></span>

<span data-ttu-id="cb0b2-141">В протоколе HTTP есть простой механизм для запроса содержимого в Интернете.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-141">The HTTP has a simple mechanism for requesting Web content.</span></span> <span data-ttu-id="cb0b2-142">По сути, это стандартные набор команд HTTP, которые отправляются клиентом после успешного установления подключения по *стандартному TCP-порту 80*.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-142">There is basically a set of standard HTTP commands that are issued by the Client after a connection has been successfully established on the TCP *well-known port 80*.</span></span> <span data-ttu-id="cb0b2-143">Ниже приведены некоторые основные команды HTTP.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-143">The following shows some of the basic HTTP commands:</span></span>

- <span data-ttu-id="cb0b2-144">GET <ресурс> HTTP/1.0: *получение указанного ресурса*.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-144">GET resource HTTP/1.0 *Get the specified resource*</span></span>
- <span data-ttu-id="cb0b2-145">POST <ресурс> HTTP/1.0: *получение указанного ресурса и передача вложенных входных данных на HTTP-сервер*.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-145">POST resource HTTP/1.0 *Get the specified resource and pass attached input to the HTTP Server*</span></span>
- <span data-ttu-id="cb0b2-146">HEAD <ресурс> HTTP/1.0: *выполняется так же, как GET, но HTTP-сервер не возвращает содержимое*.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-146">HEAD resource HTTP/1.0 *Treated like a GET but not content is returned by the HTTP Server*</span></span>
- <span data-ttu-id="cb0b2-147">PUT <ресурс> HTTP/1.0: *размещение ресурса на HTTP-сервере*.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-147">PUT resource HTTP/1.0 *Place resource on HTTP Server*</span></span>
- <span data-ttu-id="cb0b2-148">DELETE <ресурс> HTTP/1.0: *удаление ресурса с сервера*.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-148">DELETE resource HTTP/1.0 *Delete resource on the Server*</span></span>

<span data-ttu-id="cb0b2-149">Эти команды ASCII обычно генерируются веб-браузерами и службами клиента NetX Web HTTP для выполнения операций HTTP на HTTP-сервере.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-149">These ASCII commands are generated internally by Web browsers and the NetX HTTP Client services to perform HTTP operations with an HTTP Server.</span></span>

>[!NOTE] 
> <span data-ttu-id="cb0b2-150">По умолчанию приложение HTTP-клиента использует для подключения порт 80.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-150">The HTTP Client application default to the connect port of 80.</span></span> <span data-ttu-id="cb0b2-151">Но используемый для подключения к HTTP-серверу порт можно изменить во время выполнения с помощью службы *nx_http_client_set_connect_port*.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-151">However, it can change the connect port to the HTTP Server at runtime using the *nx_http_client_set_connect_port* service.</span></span> <span data-ttu-id="cb0b2-152">Дополнительные сведения об этой службе см. в главе 4.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-152">See Chapter 4 for more details of this service.</span></span> <span data-ttu-id="cb0b2-153">Это полезно для работы с теми веб-серверами, которые иногда используют альтернативные порты для клиентских подключений.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-153">This is to accommodate web servers that occasionally use alternate ports for Client connections.</span></span>

## <a name="http-server-responses"></a><span data-ttu-id="cb0b2-154">Ответы HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="cb0b2-154">HTTP Server Responses</span></span>

<span data-ttu-id="cb0b2-155">HTTP-сервер использует для отправки ответов на команды клиента тот же самый *стандартный TCP-порт 80*.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-155">The HTTP Server utilizes the same *well-known TCP port 80* to send Client command responses.</span></span> <span data-ttu-id="cb0b2-156">Когда HTTP-сервер завершает обработку команды клиента, он возвращает строку ответа ASCII, которая включает в себя 3-значный числовой код состояния.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-156">Once the HTTP Server processes the Client command, it returns an ASCII response string that includes a 3-digit numeric status code.</span></span> <span data-ttu-id="cb0b2-157">Программное обеспечение клиента по этому числовому ответу определяет, была ли операция выполнена успешно или завершилась сбоем.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-157">The numeric response is used by the HTTP Client software to determine whether the operation succeeded or failed.</span></span> <span data-ttu-id="cb0b2-158">Ниже приведен список ответов HTTP-сервера на команды клиента.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-158">Following is a list of various HTTP Server responses to Client commands:</span></span>

- <span data-ttu-id="cb0b2-159">200: *запрос выполнен успешно*.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-159">200 *Request was successful*</span></span>
- <span data-ttu-id="cb0b2-160">400: *запрос не сформирован должным образом*.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-160">400 *Request was not formed properly*</span></span>
- <span data-ttu-id="cb0b2-161">401: *несанкционированный запрос, клиент должен отправить данные проверки подлинности*.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-161">401 *Unauthorized request, client needs to send authentication*</span></span>
- <span data-ttu-id="cb0b2-162">404: *указанный ресурс в запросе не найден*.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-162">404 *Specified resource in request was not found*</span></span>
- <span data-ttu-id="cb0b2-163">500: *внутренняя ошибка HTTP-сервера*.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-163">500 *Internal HTTP Server error*</span></span>
- <span data-ttu-id="cb0b2-164">501: *запрос не реализован в HTTP-сервере*.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-164">501 *Request not implemented by HTTP Server*</span></span>
- <span data-ttu-id="cb0b2-165">502: *служба недоступна*.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-165">502 *Service is not available*</span></span>

<span data-ttu-id="cb0b2-166">Например, на запрос клиента PUT для файла test.htm в случае успешного выполнения будет возвращено сообщение "HTTP/1.0 200 OK".</span><span class="sxs-lookup"><span data-stu-id="cb0b2-166">For example, a successful Client request to PUT the file “test.htm” is responded with the message “HTTP/1.0 200 OK.”</span></span>

## <a name="http-communication"></a><span data-ttu-id="cb0b2-167">Взаимодействие по протоколу HTTP</span><span class="sxs-lookup"><span data-stu-id="cb0b2-167">HTTP Communication</span></span>

<span data-ttu-id="cb0b2-168">Как упоминалось ранее, HTTP-сервер принимает запросы от клиентов через *стандартный TCP-порт 80*.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-168">As mentioned previously, the HTTP Server utilizes the *well-known TCP port 80* to field Client requests.</span></span> <span data-ttu-id="cb0b2-169">HTTP-клиенты могут использовать любой доступный TCP-порт.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-169">HTTP Clients may use any available TCP port.</span></span> <span data-ttu-id="cb0b2-170">Общая последовательность событий HTTP выглядит следующим образом.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-170">The general sequence of HTTP events is as follows:</span></span>

<span data-ttu-id="cb0b2-171">**HTTP-запрос GET**</span><span class="sxs-lookup"><span data-stu-id="cb0b2-171">**HTTP GET Request**:</span></span>

1.  <span data-ttu-id="cb0b2-172">Клиент отправляет запрос на подключение к TCP-порту 80 сервера.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-172">Client issues TCP connect to Server port 80.</span></span>

2.  <span data-ttu-id="cb0b2-173">Клиент отправляет запрос **GET <ресурс> HTTP/1.0** и другие заголовки.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-173">Client sends “**GET resource HTTP/1.0**” request (along with other header information).</span></span>

3.  <span data-ttu-id="cb0b2-174">Сервер создает сообщение **HTTP/1.0 200 OK** с дополнительной информацией, за которой следует содержимое запрошенного ресурса (при наличии).</span><span class="sxs-lookup"><span data-stu-id="cb0b2-174">Server builds an “**HTTP/1.0 200 OK**” message with additional information followed immediately by the resource content (if any).</span></span>

4.  <span data-ttu-id="cb0b2-175">Сервер разрывает подключение.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-175">Server performs a disconnection.</span></span>

5.  <span data-ttu-id="cb0b2-176">Клиент разрывает подключение.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-176">Client performs a disconnection.</span></span>

<span data-ttu-id="cb0b2-177">**HTTP-запрос PUT**</span><span class="sxs-lookup"><span data-stu-id="cb0b2-177">**HTTP PUT Request**:</span></span>

1. <span data-ttu-id="cb0b2-178">Клиент отправляет запрос на подключение к TCP-порту 80 сервера.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-178">Client issues TCP connect to Server port 80.</span></span>

2. <span data-ttu-id="cb0b2-179">Клиент отправляет запрос **PUT <ресурс> HTTP/1.0** и другие заголовки, за которыми следует содержимое ресурса.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-179">Client sends “**PUT resource HTTP/1.0**” request, along with other header information, and followed by the resource content.</span></span>

3. <span data-ttu-id="cb0b2-180">Сервер создает сообщение **HTTP/1.0 200 OK** с дополнительной информацией, за которой следует содержимое запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-180">Server builds an “**HTTP/1.0 200 OK**” message with additional information followed immediately by the resource content.</span></span>

4. <span data-ttu-id="cb0b2-181">Сервер разрывает подключение.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-181">Server performs a disconnection.</span></span>

5. <span data-ttu-id="cb0b2-182">Клиент разрывает подключение.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-182">Client performs a disconnection.</span></span>

>[!NOTE] 
> <span data-ttu-id="cb0b2-183">Как уже упоминалось, HTTP-клиент может изменить стандартный порт 80 на любой другой порт с помощью службы *nx_http_client_set_connect_port*, что позволяет связаться с веб-серверами, использующими альтернативные порты.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-183">As mentioned previously, the HTTP Client can change the default connect port from 80 to another port using the *nx_http_client_set_connect_port* for web servers that use alternate ports to connect to clients.</span></span>

## <a name="http-authentication"></a><span data-ttu-id="cb0b2-184">Проверка подлинности HTTP</span><span class="sxs-lookup"><span data-stu-id="cb0b2-184">HTTP Authentication</span></span>

<span data-ttu-id="cb0b2-185">Проверка подлинности HTTP является необязательной и не требуется для всех веб-запросов.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-185">HTTP authentication is optional and isn’t required for all Web requests.</span></span> <span data-ttu-id="cb0b2-186">Существуют две разновидности проверки подлинности: *обычная* и *на основе дайджеста*.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-186">There are two flavors of authentication, namely *basic* and *digest*.</span></span> <span data-ttu-id="cb0b2-187">Обычная проверка подлинности по *имени* и *паролю* работает точно так же, как во многих других протоколах.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-187">Basic authentication is equivalent to the *name* and *password* authentication found in many protocols.</span></span> <span data-ttu-id="cb0b2-188">При обычной проверке подлинности HTTP имя и пароли объединяются в одну строку и кодируются в формате Base64.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-188">In HTTP basic authentication, the name and passwords are concatenated and encoded in the base64 format.</span></span> <span data-ttu-id="cb0b2-189">Основным недостатком обычной проверки подлинности является то, что имя и пароль передаются в запросе в открытом виде.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-189">The main disadvantage of basic authentication is the name and password are transmitted openly in the request.</span></span> <span data-ttu-id="cb0b2-190">Это позволяет достаточно легко похищать такие имена и пароли.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-190">This makes it somewhat easy for the name and password to be stolen.</span></span> <span data-ttu-id="cb0b2-191">Дайджест-проверка подлинности устраняет эту проблему, так как при ней имя и пароль не передаются вместе с запросом.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-191">Digest authentication addresses this problem by never transmitting the name and password in the request.</span></span> <span data-ttu-id="cb0b2-192">Вместо этого применяется специальный механизм вычисления 128-битного ключа (дайджеста) по имени пользователя, паролю и некоторым другим параметрам.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-192">Instead, an algorithm is used to derive a 128-bit key or digest from the name, password, and other information.</span></span> <span data-ttu-id="cb0b2-193">Сервер NetX HTTP поддерживает стандартный алгоритм дайджеста MD5.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-193">The NetX HTTP Server supports the standard MD5 digest algorithm.</span></span>

<span data-ttu-id="cb0b2-194">Когда нужна проверка подлинности?</span><span class="sxs-lookup"><span data-stu-id="cb0b2-194">When is authentication required?</span></span> <span data-ttu-id="cb0b2-195">По сути, HTTP-сервер самостоятельно решает, требуется ли проверка подлинности для запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-195">Basically, the HTTP Server decides if a requested resource requires authentication.</span></span> <span data-ttu-id="cb0b2-196">Если проверка подлинности нужна, но в запросе от клиента нет необходимой информации, клиенту возвращается ответ "HTTP/1.0 401 Unauthorized" с указанием требуемого типа проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-196">If authentication is required and the Client request did not include the proper authentication, a “HTTP/1.0 401 Unauthorized” response with the type of authentication required is sent to the Client.</span></span> <span data-ttu-id="cb0b2-197">Ожидается, что клиент в этом случае сформирует новый запрос с правильными данными проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-197">The Client is then expected to form a new request with the proper authentication.</span></span>

## <a name="http-authentication-callback"></a><span data-ttu-id="cb0b2-198">Обратный вызов проверки подлинности HTTP</span><span class="sxs-lookup"><span data-stu-id="cb0b2-198">HTTP Authentication Callback</span></span>

<span data-ttu-id="cb0b2-199">Как уже упоминалось, проверка подлинности HTTP является необязательной, то есть используется не при любой передаче данных через Интернет.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-199">As mentioned before, HTTP authentication is optional and isn’t required on all Web transfers.</span></span> <span data-ttu-id="cb0b2-200">Кроме того, проверка подлинности обычно зависит от конкретного ресурса.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-200">In addition, authentication is typically resource dependent.</span></span> <span data-ttu-id="cb0b2-201">Один и тот же сервер может требовать проверку подлинности для доступа к некоторым ресурсам и не требовать для доступа к другим.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-201">Access of some resources on the Server require authentication, while others do not.</span></span> <span data-ttu-id="cb0b2-202">Пакет сервера NetX HTTP позволяет приложению указать (с помощью вызова ***nx_http_server_create***) подпрограмму обратного вызова для проверки подлинности, которая будет вызываться в начале обработки каждого запроса от HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-202">The NetX HTTP Server package allows the application to specify (via the ***nx_http_server_create*** call) an authentication callback routine that is called at the beginning of handling each HTTP Client request.</span></span>

<span data-ttu-id="cb0b2-203">Эта подпрограмма обратного вызова предоставляет серверу NetX HTTP строковые значения имени пользователя, пароля и области, которые связаны с конкретным ресурсом, и возвращает необходимый тип проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-203">The callback routine provides the NetX HTTP Server with the username, password, and realm strings associated with the resource and return the type of authentication necessary.</span></span> <span data-ttu-id="cb0b2-204">Если для ресурса не требуется проверка подлинности, обратный вызов проверки подлинности должен возвращать значение **NX_HTTP_DONT_AUTHENTICATE**.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-204">If no authentication is necessary for the resource, the authentication callback should return the value of **NX_HTTP_DONT_AUTHENTICATE**.</span></span> <span data-ttu-id="cb0b2-205">Если для указанного ресурса требуется обычная проверка подлинности, то подпрограмма должна возвращать **NX_HTTP_BASIC_AUTHENTICATE**.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-205">Otherwise, if basic authentication is required for the specified resource, the routine should return **NX_HTTP_BASIC_AUTHENTICATE**.</span></span> <span data-ttu-id="cb0b2-206">И, наконец, если требуется дайджест-проверка подлинности MD5, то подпрограмма обратного вызова должна возвращать **NX_HTTP_DIGEST_AUTHENTICATE**.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-206">And finally, if MD5 digest authentication is required, the callback routine should return **NX_HTTP_DIGEST_AUTHENTICATE**.</span></span> <span data-ttu-id="cb0b2-207">Если ни для одного из ресурсов, предоставляемого HTTP-сервером, не требуется проверка подлинности, обратный вызов можно не указывать, передав в вызов создания для HTTP-сервера пустой указатель.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-207">If no authentication is required for any resource provided by the HTTP Server, the callback is not needed and a NULL pointer can be provided to the HTTP Server create call.</span></span>

<span data-ttu-id="cb0b2-208">Формат подпрограммы обратного вызова проверки подлинности для приложения достаточно прост и определен ниже.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-208">The format of the application authenticate callback routine is very simple and is defined below:</span></span>

```c
UINT nx_http_server_authentication_check (NX_HTTP_SERVER *server_ptr,
                                         UINT request_type, CHAR *resource,
                                         CHAR **name, CHAR **password,
                                         CHAR **realm);
```

<span data-ttu-id="cb0b2-209">Входные параметры определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-209">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="cb0b2-210">*request_type*: указывает запрос HTTP-клиента, который может иметь одно из следующих значений:</span><span class="sxs-lookup"><span data-stu-id="cb0b2-210">*request_type* Specifies the HTTP Client request, valid requests are defined as:</span></span>
  - <span data-ttu-id="cb0b2-211">**NX_HTTP_SERVER_GET_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="cb0b2-211">**NX_HTTP_SERVER_GET_REQUEST**</span></span>
  - <span data-ttu-id="cb0b2-212">**NX_HTTP_SERVER_POST_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="cb0b2-212">**NX_HTTP_SERVER_POST_REQUEST**</span></span>
  - <span data-ttu-id="cb0b2-213">**NX_HTTP_SERVER_HEAD_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="cb0b2-213">**NX_HTTP_SERVER_HEAD_REQUEST**</span></span>
  - <span data-ttu-id="cb0b2-214">**NX_HTTP_SERVER_PUT_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="cb0b2-214">**NX_HTTP_SERVER_PUT_REQUEST**</span></span>
  - <span data-ttu-id="cb0b2-215">**NX_HTTP_SERVER_DELETE_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="cb0b2-215">**NX_HTTP_SERVER_DELETE_REQUEST**</span></span>
- <span data-ttu-id="cb0b2-216">*resource*: запрашиваемый ресурс.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-216">*resource* Specific resource requested.</span></span>
- <span data-ttu-id="cb0b2-217">*name*: указатель на требуемое имя пользователя.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-217">*name* Destination for the pointer to the required username.</span></span>
- <span data-ttu-id="cb0b2-218">*password*: указатель на требуемый пароль.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-218">*password* Destination for the pointer to the required password.</span></span>
- <span data-ttu-id="cb0b2-219">*realm*: указатель на область определения приложений для данной проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-219">*realm* Destination for the pointer to the realm for this authentication.</span></span>

<span data-ttu-id="cb0b2-220">Возвращаемое значение подпрограммы проверки подлинности указывает, требуется ли проверка подлинности.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-220">The return value of the authentication routine specifies if authentication is required.</span></span> <span data-ttu-id="cb0b2-221">Указатели на имя, пароль и область определения приложения не используются, если подпрограмма обратного вызова проверки подлинности возвращает значение **NX_HTTP_DONT_AUTHENTICATE**.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-221">name, password, and realm pointers are not used if **NX_HTTP_DONT_AUTHENTICATE** is returned by the authentication callback routine.</span></span> <span data-ttu-id="cb0b2-222">В противном случае разработчик HTTP-сервера должен убедиться, что значения **NX_HTTP_MAX_USERNAME** и **NX_HTTP_MAX_PASSWORD**, определенные в файле *nx_http_server.h*, достаточно велики для размещения имени пользователя и пароля, указанных в подпрограмме обратного вызова проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-222">Otherwise the HTTP server developer must ensure that **NX_HTTP_MAX_USERNAME** and **NX_HTTP_MAX_PASSWORD** defined in *nx_http_server.h* are large enough for the username and password specified in the authentication callback.</span></span> <span data-ttu-id="cb0b2-223">Оба этих значения по умолчанию имеют размер в 20 символов.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-223">These are both defaulted to size 20 chars.</span></span>

## <a name="http-invalid-usernamepassword-callback"></a><span data-ttu-id="cb0b2-224">Обратный вызов для недопустимых значений имени пользователя или пароля HTTP</span><span class="sxs-lookup"><span data-stu-id="cb0b2-224">HTTP Invalid Username/Password Callback</span></span>

<span data-ttu-id="cb0b2-225">Необязательный обратный вызов для недопустимых значений имени пользователя или пароля на HTTP-сервере в NetX выполняется в тех случаях, когда HTTP-сервер получает в запросе от клиента недопустимое сочетание имени пользователя и пароля.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-225">The optional invalid username/password callback in NetX HTTP Server is invoked if HTTP server receives an invalid username and password combination in a Client request.</span></span> <span data-ttu-id="cb0b2-226">Если приложение HTTP-сервера зарегистрирует этот обратный вызов, указанная подпрограмма будет вызываться в случае ошибки обычной или дайджест-проверки подлинности в *nx_http_server_get_process*, *nx_http_server_put_process* или *nx_http_server_delete_process*.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-226">If the HTTP server application registers a callback with HTTP server it will be invoked if either basic or digest authentication fails *in nx_http_server_get_process*, in *nx_http_server_put_process,* or *in nx_http_server_delete_process.*</span></span>

<span data-ttu-id="cb0b2-227">Чтобы зарегистрировать обратный вызов на HTTP-сервере, используйте следующую службу, которая определена в сервере NetX HTTP.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-227">To register a callback with the HTTP server, the following service is defined in NetX HTTP Server.</span></span>

```c
UINT nx_http_server_invalid_userpassword_notify_set (NX_HTTP_SERVER *http_server_ptr,
                                                    UINT *invalid_username_password_callback)
                                                    (CHAR *resource,
                                                    ULONG *client_nx_address,
                                                    UINT request_type));
```
<span data-ttu-id="cb0b2-228">Определены следующие типы запроса:</span><span class="sxs-lookup"><span data-stu-id="cb0b2-228">The request types are defined as follows:</span></span>

- <span data-ttu-id="cb0b2-229">**NX_HTTP_SERVER_GET_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="cb0b2-229">**NX_HTTP_SERVER_GET_REQUEST**</span></span>
- <span data-ttu-id="cb0b2-230">**NX_HTTP_SERVER_POST_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="cb0b2-230">**NX_HTTP_SERVER_POST_REQUEST**</span></span>
- <span data-ttu-id="cb0b2-231">**NX_HTTP_SERVER_HEAD_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="cb0b2-231">**NX_HTTP_SERVER_HEAD_REQUEST**</span></span>
- <span data-ttu-id="cb0b2-232">**NX_HTTP_SERVER_PUT_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="cb0b2-232">**NX_HTTP_SERVER_PUT_REQUEST**</span></span>
- <span data-ttu-id="cb0b2-233">**NX_HTTP_SERVER_DELETE_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="cb0b2-233">**NX_HTTP_SERVER_DELETE_REQUEST**</span></span>

## <a name="http-insert-gmt-date-header-callback"></a><span data-ttu-id="cb0b2-234">Обратный вызов для добавления заголовка даты GMT в HTTP</span><span class="sxs-lookup"><span data-stu-id="cb0b2-234">HTTP Insert GMT Date Header Callback</span></span>

<span data-ttu-id="cb0b2-235">Этот необязательный обратный вызов в сервере NetX HTTP позволяет вставлять в ответные сообщения заголовок со значением даты.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-235">There is an optional callback in NetX HTTP Server to insert a date header in its response messages.</span></span> <span data-ttu-id="cb0b2-236">Он вызывается, когда HTTP-сервер отвечает на запрос PUT или GET.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-236">This callback is invoked when the HTTP Server is responding to a put or get request</span></span>

<span data-ttu-id="cb0b2-237">Чтобы зарегистрировать обратный вызов даты GMT на HTTP-сервере, используйте следующую службу, которая определена на сервере NetX HTTP.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-237">To register a GMT date callback with the HTTP server, the following service is defined in the NetX HTTP Server.</span></span>

```c
UINT _nx_http_server_gmt_callback_set(NX_HTTP_SERVER *server_ptr,
                                     VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date);
```

<span data-ttu-id="cb0b2-238">Тип данных NX_HTTP_SERVER_DATE определяется следующим образом:</span><span class="sxs-lookup"><span data-stu-id="cb0b2-238">The NX_HTTP_SERVER_DATE data type is defined as follows:</span></span>

```c
typedef struct NX_HTTP_SERVER_DATE_STRUCT
{
    USHORT     nx_http_server_year;         /* Year        */
    UCHAR      nx_http_server_month;        /* Month       */
    UCHAR      nx_http_server_day;          /* Day         */
    UCHAR      nx_http_server_hour;         /* Hour        */
    UCHAR      nx_http_server_minute;       /* Minute      */
    UCHAR      nx_http_server_second;       /* Second      */
    UCHAR      nx_http_server_weekday;      /* Weekday     */
} NX_HTTP_SERVER_DATE;
```

## <a name="http-cache-info-get-callback"></a><span data-ttu-id="cb0b2-239">Обратный вызов для получения сведений из кэша HTTP</span><span class="sxs-lookup"><span data-stu-id="cb0b2-239">HTTP Cache Info Get Callback</span></span>

<span data-ttu-id="cb0b2-240">HTTP-сервер поддерживает обратный вызов для запроса ограничений по возрасту и датам для определенного ресурса в приложении HTTP.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-240">The HTTP Server has a callback to request the max age and date from the HTTP application for a specific resource.</span></span> <span data-ttu-id="cb0b2-241">Эти сведения позволяют определить, будет ли HTTP-сервер отправлять всю страницу клиенту по запросу GET.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-241">This information is used to determine if the HTTP server sends the entire page in response to a Client Get request.</span></span> <span data-ttu-id="cb0b2-242">Если в запросе клиента нет строки "if modified since" (если изменено позднее) или это значение не совпадает с датой "last modified" (последнее изменение), полученной в обратном вызове запроса сведений из кэша, то клиенту отправляется вся страница.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-242">If the “if modified since” in the Client request is not found or does not match the “last modified” date returned by the get cache callback, the entire page is sent.</span></span>

<span data-ttu-id="cb0b2-243">Чтобы зарегистрировать обратный вызов на HTTP-сервере, определена приведенная ниже служба.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-243">To register the callback with the HTTP server the following service is defined:</span></span>

```c
UINT _nx_http_server_cache_info_callback_set(NX_HTTP_SERVER *server_ptr,
                                            UINT (*cache_info_get)
                                            (CHAR *, UINT *, NX_HTTP_SERVER_DATE *));
```

## <a name="http-multipart-support"></a><span data-ttu-id="cb0b2-244">Поддержка многокомпонентных сообщений HTTP</span><span class="sxs-lookup"><span data-stu-id="cb0b2-244">HTTP Multipart Support</span></span>

<span data-ttu-id="cb0b2-245">Протокол MIME изначально предназначался для взаимодействия с протоколом SMTP, но теперь он используется и с протоколом HTTP.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-245">Multipurpose Internet Mail Extensions (MIME) was originally intended for the SMTP protocol, but its use has spread to HTTP.</span></span> <span data-ttu-id="cb0b2-246">Протокол MIME позволяет включать в одно сообщение смешанные типы данных (например, image/jpg и text/plain).</span><span class="sxs-lookup"><span data-stu-id="cb0b2-246">MIME allows messages to contain mixed message types (e.g. image/jpg and text/plain) within the same message.</span></span> <span data-ttu-id="cb0b2-247">Сервер NetX HTTP включает в себя дополнительные службы для определения типа содержимого в полученных от клиента сообщениях HTTP, содержащих данные MIME.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-247">NetX HTTP Server has added services to determine content type in HTTP messages containing MIME from the Client.</span></span> <span data-ttu-id="cb0b2-248">Чтобы включить поддержку составных сообщений для протокола HTTP и использовать эти службы, необходимо определить параметр конфигурации **NX_HTTP_MULTIPART_ENABLE**.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-248">To enable HTTP multipart support and use these services, the configuration option **NX_HTTP_MULTIPART_ENABLE** must be defined.</span></span>

```c
UINT nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                     NX_PACKET **packet_pptr,
                                     UCHAR *entity_header_buffer,
                                     ULONG buffer_size);

UINT nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                      NX_PACKET **packet_pptr,
                                      ULONG *available_offset,
                                      ULONG *available_length);
```

<span data-ttu-id="cb0b2-249">Дополнительные сведения об использовании этих служб можно найти в главе 3 "Описание служб HTTP".</span><span class="sxs-lookup"><span data-stu-id="cb0b2-249">For more details on the use of these services, see their description in Chapter 3 “Description of HTTP Services”.</span></span>

## <a name="http-multi-thread-support"></a><span data-ttu-id="cb0b2-250">Поддержка многопоточности HTTP</span><span class="sxs-lookup"><span data-stu-id="cb0b2-250">HTTP Multi-Thread Support</span></span>

<span data-ttu-id="cb0b2-251">Службы клиента NetX HTTP можно вызывать из нескольких потоков одновременно.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-251">The NetX HTTP Client services can be called from multiple threads simultaneously.</span></span> <span data-ttu-id="cb0b2-252">Но запросы на чтение или запись для конкретного экземпляра HTTP-клиента должны выполняться последовательно из одного потока.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-252">However, read or write requests for a particular HTTP Client instance should be done in sequence from the same thread.</span></span>

## <a name="http-rfcs"></a><span data-ttu-id="cb0b2-253">Соответствие протокола HTTP положениям документов RFC</span><span class="sxs-lookup"><span data-stu-id="cb0b2-253">HTTP RFCs</span></span>

<span data-ttu-id="cb0b2-254">Реализация NetX HTTP соответствует требованиям стандартов RFC 1945 "Hypertext Transfer Protocol/1.0" (Протокол передачи гипертекста, версия 1.0), RFC 2581 "TCP Congestion Control" (Контроль перегрузки TCP), RFC 1122 "Requirements for Internet Hosts" (Требования к Интернет-узлам) и других связанных с ними спецификаций RFC.</span><span class="sxs-lookup"><span data-stu-id="cb0b2-254">NetX HTTP is compliant with RFC1945 “Hypertext Transfer Protocol/1.0”, RFC 2581 “TCP Congestion Control”, RFC 1122 “Requirements for Internet Hosts”, and related RFCs.</span></span>