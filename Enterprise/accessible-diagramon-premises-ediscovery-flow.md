---
title: "Доступная схема — поток локального обнаружения электронных данных"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b9dcd692-0485-4eec-870d-87ab6b89d97b
description: "Эта статья представляет собой текстовую версию схемы \"Поток локального обнаружения электронных данных\"."
ms.openlocfilehash: e137a75fb80c9198a332144d82fe405c6884aa52
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a><span data-ttu-id="00364-103">Доступная схема — поток локального обнаружения электронных данных</span><span class="sxs-lookup"><span data-stu-id="00364-103">Accessible diagram - On-premises eDiscovery Flow</span></span>

<span data-ttu-id="00364-104">**Сводка:** Эта статья является доступным текстовая версия схемы с именем локального обнаружения электронных данных потока.</span><span class="sxs-lookup"><span data-stu-id="00364-104">**Summary:** This article is an accessible text version of the diagram named On-premises eDiscovery Flow.</span></span>
  
<span data-ttu-id="00364-105">На этом плакате представлены подробные сведения об архитектуре и потоке данных серверных продуктов.</span><span class="sxs-lookup"><span data-stu-id="00364-105">This poster provides details about the architecture and flow of data across server products.</span></span> 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a><span data-ttu-id="00364-106">В SharePoint, Exchange, Lync и общих файловых ресурсах</span><span class="sxs-lookup"><span data-stu-id="00364-106">Across SharePoint, Exchange, Lync, and file shares</span></span>

<span data-ttu-id="00364-p101">На схеме показана пользователь, отправляющий запрос, который осуществляет доступ к двух ферм серверов, фермы SharePoint 2013 корпоративного приложения и службы фермы SharePoint 2013. В ферме служб SharePoint 2013 взаимодействует с фермой контента SharePoint 2013, Exchange Server 2013 (который взаимодействует с Lync 2013) и общим файловым ресурсам Windows.</span><span class="sxs-lookup"><span data-stu-id="00364-p101">The diagram shows a user sending a query that accesses two server farms, a SharePoint 2013 Enterprise App Farm, and a SharePoint 2013 Services Farm. The SharePoint 2013 Services Farm communicates with a SharePoint 2013 Content Farm, Exchange Server 2013 (which communicates with Lync 2013), and Windows File Shares.</span></span> 
  
<span data-ttu-id="00364-109">Последовательность операций при обнаружении электронных данных описывает поток данных и порядок выполнения действий, связанных с запросами на обнаружение электронных данных в SharePoint, Exchange, Lync и общих файловых ресурсах. </span><span class="sxs-lookup"><span data-stu-id="00364-109">The eDiscovery Flow List describes the flow of data and the order in which eDisovery query actions occur across SharePoint, Exchange, Lync, and file shares.</span></span> 
  
<span data-ttu-id="00364-110">Последовательность операций при обнаружении электронных данных подробно описывается в первую очередь. Затем следует детальное описание функций, изображенных на схеме. </span><span class="sxs-lookup"><span data-stu-id="00364-110">The eDiscovery flow list is described in detail first, followed by a detailed description of the features depicted in the diagram.</span></span> 
  
### <a name="ediscovery-flow-list"></a><span data-ttu-id="00364-111">Последовательность операций при обнаружении электронных данных</span><span class="sxs-lookup"><span data-stu-id="00364-111">eDiscovery Flow List</span></span>

<span data-ttu-id="00364-p102">Номер каждого действия, описанного в этом списке, соответствует шагу, который изображен на схеме. Схема более подробно описана далее в этом документе. </span><span class="sxs-lookup"><span data-stu-id="00364-p102">The numbers for each of the steps described in this list pertain to a step depicted in the diagram. The diagram is described in detail later in this document.</span></span> 
  
1. <span data-ttu-id="00364-p103">вариантах eDiscovery создаются, управляемых и используются в центр обнаружения электронных данных (EDC). EDC — это семейство сайтов SharePoint 2013. Это, где определены в тех случаях, определяемую источников, чтобы отслеживать, запросы отправляются, проверяются результаты запроса и удалены или помещены удержаний на содержимое.</span><span class="sxs-lookup"><span data-stu-id="00364-p103">eDiscovery cases are created, managed, and used in the eDiscovery center (EDC). The EDC is a SharePoint 2013 site collection. This is where cases are defined, sources to be tracked are identified, queries are issued, query results are reviewed, and holds on content are placed or removed.</span></span> 
    
2. <span data-ttu-id="00364-p104">Запрос обнаружения электронных данных или действия, например месте удержания, ReleaseHold или GetStatus, передается от EDC на прокси приложения службы поиска (SSA) в ферме приложения предприятия. Затем SSA прокси-сервер ретранслирует трафик на SSA в ферме приложения служб. В этом примере запрос является поместить все действия в ферме SharePoint, с «CONTOSO» в поле имя файла на удержание.</span><span class="sxs-lookup"><span data-stu-id="00364-p104">The eDiscovery query or action, such as place a Hold, ReleaseHold, or GetStatus, is relayed from the EDC to the Search Service Application (SSA) proxy in the Enterprise App Farm. The SSA proxy then relays the traffic to the SSA in the Services App Farm. In this example, the request is to place anything in the SharePoint Content Farm with "CONTOSO" in the file name on hold.</span></span> 
    
3. <span data-ttu-id="00364-p105">Если целью запроса является дело, приложение службы поиска обращается к индексу поиска. Затем набор результатов запроса на обнаружение электронных данных возвращается пользователю через центр EDC. </span><span class="sxs-lookup"><span data-stu-id="00364-p105">If the request is to query a case, the SSA consults the search index. Then, the eDiscovery query result set returns to the user through the EDC.</span></span> 
    
4. <span data-ttu-id="00364-p106">Если запрос — это действие, такие как удержание или ReleaseHold, это действие записывается Actions_Table в базе данных администрирования SSA. В этом примере записывается Actions_Table запрос удержания в ферме SharePoint, с «CONTOSO».</span><span class="sxs-lookup"><span data-stu-id="00364-p106">If the request is an action, such as place a Hold or ReleaseHold, that action is written to the Actions_Table in the SSA Administrative database. In this example, a hold request for anything in the SharePoint Content Farm with "CONTOSO" is written to the Actions_Table.</span></span> 
    
5. <span data-ttu-id="00364-124">Задание таймера хранения на месте при обнаружении электронных данных регулярно запускается и генерирует запрос об ожидающих действиях, а затем отправляет обновления состояния через прокси-сервер SSA в приложение службы поиска. </span><span class="sxs-lookup"><span data-stu-id="00364-124">At regular intervals the Content Farm eDiscovery in-place hold timer job wakes up and generates a request for pending actions and sends status updates through the SSA proxy to the SSA.</span></span> 
    
6. <span data-ttu-id="00364-p107">Запрос для незавершенных действий передается на центра SSA, который просматривает Action_Table для каких-либо незавершенных действий для фермы контента. Задание таймера хранения на месте фермы контента также отправляет обновления состояния для объектов и действий, полученные, написанные для ActionsTable.</span><span class="sxs-lookup"><span data-stu-id="00364-p107">The query for pending actions is relayed to the central SSA, which consults the Action_Table for any pending actions for the Content Farm. The Content Farm in-place hold timer job also sends status updates for objects and actions it has received, which are written to the ActionsTable.</span></span> 
    
7. <span data-ttu-id="00364-127">Запрос удержания для контента с «CONTOSO» в поле имя в ферме SharePoint 2013 содержимое отправляется с SSA задание таймера хранения на месте обнаружения электронных данных в ферме контента.</span><span class="sxs-lookup"><span data-stu-id="00364-127">The hold request for any content with "CONTOSO" in the name in the SharePoint 2013 Content Farm is sent by the SSA to the eDiscovery in-place hold timer job in the Content Farm.</span></span> 
    
8. <span data-ttu-id="00364-128">Обнаружение электронных данных на месте нажмите и удерживайте таймера job знаков «Сайт CONTOSO» и «CONTOSO содержимого» на хранение.</span><span class="sxs-lookup"><span data-stu-id="00364-128">The eDiscovery in-place hold timer job places the "CONTOSO Site" and "CONTOSO content" on hold.</span></span> 
    
9. <span data-ttu-id="00364-129">Задание таймера хранения на месте при обнаружении электронных данных периодически запускается в ферме корпоративных приложений для проверки состояния действий обнаружения и обновляет состояние. </span><span class="sxs-lookup"><span data-stu-id="00364-129">The eDiscovery in-place hold timer job periodically runs in the Enterprise App Farm to check the status of discovery actions and to update the status.</span></span> 
    
10. <span data-ttu-id="00364-130">Запрос о состоянии передается через прокси-сервер SSA фермы корпоративных приложений в приложение службы поиска фермы служб SharePoint. </span><span class="sxs-lookup"><span data-stu-id="00364-130">The status query is relayed through the Enterprise App Farm SSA proxy to the SharePoint Services Farm SSA.</span></span> 
    
11. <span data-ttu-id="00364-131">Приложение службы поиска получает состояние из таблицы действий и возвращает его заданию таймера в ферме корпоративных приложений, после чего обновления состояния поступают в центр EDC. </span><span class="sxs-lookup"><span data-stu-id="00364-131">The SSA retrieves the status from the Actions table and returns it to the timer job in the Enterprise App Farm, which pushes the status updates to the EDC.</span></span> 
    
12. <span data-ttu-id="00364-p108">Когда пользователь обнаружения электронных данных — это поиск (или выполнение действия) для Exchange источников, таких как почтовый ящик или архивных Lync контента центра SSA использует прокси-сервера веб-служб Exchange (EWS) для запроса веб-служб Exchange. Exchange имеет собственную инфраструктуру поиска и обнаружения электронных данных и управляет все звонки eDiscovery во внутренней сети.</span><span class="sxs-lookup"><span data-stu-id="00364-p108">When the eDiscovery user is searching (or performing an action) for Exchange sources, such as a mailbox or archived Lync content, the central SSA uses Exchange Web Services (EWS) proxy to query Exchange Web Services. Exchange has its own search and eDiscovery infrastructure and manages all eDiscovery calls internally.</span></span> 
    
13. <span data-ttu-id="00364-134">Веб-службы Exchange отвечают приложению службы поиска, предоставляя результаты поиска при обнаружении электронных данных или ответ на запрос о состоянии удержания по запросу, которые в свою очередь передаются в центр EDC. </span><span class="sxs-lookup"><span data-stu-id="00364-134">Exchange Web Services responds to SSA with eDiscovery search results or a response to a status request for a query-based hold, which, in turn, gets relayed to the EDC.</span></span> 
    
#### <a name="prerequisites"></a><span data-ttu-id="00364-135">Необходимые условия</span><span class="sxs-lookup"><span data-stu-id="00364-135">Prerequisites</span></span>

- <span data-ttu-id="00364-136">Служба корпоративного поиска SharePoint должна быть настроена. Кроме того, должен успешно выполняться обход контента во всех источниках контента (SharePoint и общих файловых ресурсах Windows), которые должны быть проиндексированы. </span><span class="sxs-lookup"><span data-stu-id="00364-136">SharePoint Enterprise Search must be configured, search crawls on content sources (SharePoint and Windows file shares) are successfully occurring, and all content sources are in the index.</span></span> 
    
- <span data-ttu-id="00364-137">Необходимо настроить доверие и проверку подлинности между серверами фермы служб SharePoint и Exchange, а также между службами Exchange и Lync. </span><span class="sxs-lookup"><span data-stu-id="00364-137">Server-to-server trust and authentication must be configured between the SharePoint Services Farm and Exchange and also between Exchange and Lync.</span></span> 
    
### <a name="description-of-components-in-the-diagram"></a><span data-ttu-id="00364-138">Описание компонентов на схеме</span><span class="sxs-lookup"><span data-stu-id="00364-138">Description of components in the diagram</span></span>

<span data-ttu-id="00364-p109">На схеме показана пользователь, отправляющий запрос, который осуществляет доступ к двух ферм серверов фермы SharePoint 2013 корпоративного приложения и службы фермы SharePoint 2013. Интерфейсы служб фермы SharePoint с фермой контента SharePoint 2013, Exchange Server 2013 (который взаимодействует с Lync 2013) и общим файловым ресурсам Windows.</span><span class="sxs-lookup"><span data-stu-id="00364-p109">The diagram shows a user sending a query, which accesses two server farms, a SharePoint 2013 Enterprise App Farm and a SharePoint 2013 Services Farm. The SharePoint Services Farm interfaces with a SharePoint 2013 Content Farm, Exchange Server 2013 (which interfaces with Lync 2013), and Windows File Shares.</span></span> 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a><span data-ttu-id="00364-141">Фермы SharePoint 2013 корпоративного приложения</span><span class="sxs-lookup"><span data-stu-id="00364-141">SharePoint 2013 Enterprise App Farm</span></span>

<span data-ttu-id="00364-142">В ферме SharePoint 2013 Enterprise приложения содержит следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="00364-142">The SharePoint 2013 Enterprise App Farm contains the following components:</span></span> 
  
- <span data-ttu-id="00364-143">центр EDC;</span><span class="sxs-lookup"><span data-stu-id="00364-143">EDC</span></span>
    
- <span data-ttu-id="00364-144">прокси-сервер SSA; </span><span class="sxs-lookup"><span data-stu-id="00364-144">SSA proxy</span></span> 
    
- <span data-ttu-id="00364-145">задание таймера.</span><span class="sxs-lookup"><span data-stu-id="00364-145">Timer job</span></span> 
    
<span data-ttu-id="00364-p110">Запрос или действие, которые отправляет пользователь, направляются в центр EDC в ферме корпоративных приложений. Выполняются следующие действия. </span><span class="sxs-lookup"><span data-stu-id="00364-p110">A query or action sent by the user is sent to the EDC in the Enterprise App Farm. The following actions occur:</span></span> 
  
- <span data-ttu-id="00364-148">Запрос или действие передается на прокси-сервер SSA. </span><span class="sxs-lookup"><span data-stu-id="00364-148">The query or action goes to the SSA proxy.</span></span> 
    
- <span data-ttu-id="00364-p111">Прокси-сервер SSA отправляет запрос о состоянии или ответ на задание таймера в ферму корпоративных приложений. Этот прокси-сервер также отправляет запрос о состоянии или ответ в службу SSA на ферме служб SharePoint. Действия, которые выполняются в результате этих операций, описаны в разделе о ферме служб SharePoint. </span><span class="sxs-lookup"><span data-stu-id="00364-p111">The SSA proxy sends a status query or response to the Timer job in the Enterprise App Farm, and it also sends a status query or response to the SSA service in the SharePoint Services Farm. The actions that result from this are described in the section about the SharePoint Services Farm.</span></span> 
    
- <span data-ttu-id="00364-151">При получении ответа задание таймера отправляет ответ на прокси-сервер SSA и в центр EDC. </span><span class="sxs-lookup"><span data-stu-id="00364-151">When it receives a response, the Timer job sends the response to the SSA proxy and to the EDC.</span></span> 
    
- <span data-ttu-id="00364-152">Все результаты запроса или действия отправляются пользователю из центра EDC. </span><span class="sxs-lookup"><span data-stu-id="00364-152">Any results from the query or action are sent to the user from the EDC.</span></span> 
    
#### <a name="sharepoint-2013-services-farm"></a><span data-ttu-id="00364-153">Службы фермы SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="00364-153">SharePoint 2013 Services Farm</span></span>

<span data-ttu-id="00364-154">В ферме служб SharePoint 2013 содержит следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="00364-154">The SharePoint 2013 Services Farm contains the following components:</span></span> 
  
- <span data-ttu-id="00364-155">служба SSA; </span><span class="sxs-lookup"><span data-stu-id="00364-155">SSA Service</span></span> 
    
- <span data-ttu-id="00364-156">база данных индекса поиска; </span><span class="sxs-lookup"><span data-stu-id="00364-156">Search index database</span></span> 
    
- <span data-ttu-id="00364-p112">База данных admin_db SSA. Содержит таблицы действия в этой базе данных: хранение GetStatus удержание выпуска</span><span class="sxs-lookup"><span data-stu-id="00364-p112">SSA admin_db database. The Actions Table in this database contains: Hold Release Hold GetStatus</span></span> 
    
- <span data-ttu-id="00364-159">прокси-сервер EWS. </span><span class="sxs-lookup"><span data-stu-id="00364-159">EWS proxy</span></span> 
    
<span data-ttu-id="00364-160">Когда прокси-сервер SSA на ферме корпоративных приложений SharePoint отправляет запрос о состоянии приложению службы поиска (SSA) на ферме служб SharePoint, выполняются следующие действия. </span><span class="sxs-lookup"><span data-stu-id="00364-160">When the SSA proxy in the SharePoint Enterprise App Farm sends a status query to the SSA in the SharePoint Services Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="00364-p113">Если целью запроса является собственно запрос, приложение службы поиска обращается к индексу поиска. Обнаруженный ответ возвращается сначала в приложение службы поиска, а затем пользователю через центр EDC. </span><span class="sxs-lookup"><span data-stu-id="00364-p113">If the request is a query, the SSA consults the search index. The discovery response is returned to the SSA and then to the user through the EDC.</span></span> 
    
- <span data-ttu-id="00364-163">Если запрос представляет собой действие записи, служба SSA отправляет действие записи в базу данных SSA admin_db. </span><span class="sxs-lookup"><span data-stu-id="00364-163">If the request is a write action, the SSA service sends the write action to the SSA admin_db.</span></span> 
    
- <span data-ttu-id="00364-164">Обход контента и отвечать на запросы результаты отправляется запрос из SSA в ферме SharePoint 2013 контент и ответ возвращается SSA.</span><span class="sxs-lookup"><span data-stu-id="00364-164">A crawl and responding results request is sent from the SSA to the SharePoint 2013 Content Farm and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="00364-165">Запрос на обход контента и результаты ответа отправляется из приложения службы поиска в общие файловые ресурсы Windows, а ответ возвращается в приложение службы поиска. </span><span class="sxs-lookup"><span data-stu-id="00364-165">A crawl and responding results request is sent from the SSA to the Windows File Shares, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="00364-166">Запрос на ожидающие действия, ответы или обновления состояния отправляется из приложения службы поиска на прокси-сервер SSA на ферме контента SharePoint, а ответ возвращается в приложение службы поиска. </span><span class="sxs-lookup"><span data-stu-id="00364-166">A query for pending action(s), responses, or status updates is sent from the SSA to the SSA proxy in the SharePoint Content Farm, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="00364-167">Запрос на действие или состояние Exchange отправляется из приложения службы поиска на прокси-сервер EWS, который отправляет запрос на действие или состояние Exchange в веб-службы Exchange на сервере Exchange 2013.  </span><span class="sxs-lookup"><span data-stu-id="00364-167">An Exchange action/status request is sent from the SSA to the EWS proxy, which sends an Exchange Query action/status request to the Exchange Web Service on the Exchange 2013 server.</span></span> 
    
- <span data-ttu-id="00364-168">Запрос о состоянии или ответ отправляется из приложения службы поиска в базу данных admin_db SSA и возвращается в приложение службы поиска. </span><span class="sxs-lookup"><span data-stu-id="00364-168">A status query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
- <span data-ttu-id="00364-169">Запрос об ожидающем действии или ответ отправляется из приложения службы поиска в базу данных admin_db SSA и возвращается в приложение службы поиска. </span><span class="sxs-lookup"><span data-stu-id="00364-169">A pending action query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
#### <a name="sharepoint-2013-content-farm"></a><span data-ttu-id="00364-170">Контент фермы SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="00364-170">SharePoint 2013 Content Farm</span></span>

<span data-ttu-id="00364-171">В ферме SharePoint 2013 контента содержит следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="00364-171">The SharePoint 2013 Content Farm contains the following components:</span></span> 
  
- <span data-ttu-id="00364-172">прокси-сервер SSA; </span><span class="sxs-lookup"><span data-stu-id="00364-172">SSA proxy</span></span> 
    
- <span data-ttu-id="00364-173">задание таймера;</span><span class="sxs-lookup"><span data-stu-id="00364-173">Timer job</span></span> 
    
- <span data-ttu-id="00364-174">сайт Contoso SharePoint; </span><span class="sxs-lookup"><span data-stu-id="00364-174">Contoso SharePoint site</span></span> 
    
- <span data-ttu-id="00364-175">контент Contoso SharePoint. </span><span class="sxs-lookup"><span data-stu-id="00364-175">Contoso SharePoint content</span></span> 
    
<span data-ttu-id="00364-176">Когда приложение службы поиска (SSA) на ферме служб SharePoint отправляет запрос о состоянии на прокси-сервер SSA на ферме контента SharePoint, выполняются следующие действия. </span><span class="sxs-lookup"><span data-stu-id="00364-176">When the SSA in the SharePoint Services Farm sends a status query to the SSA Proxy in the SharePoint Content Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="00364-177">Прокси-сервер SSA на ферме контента SharePoint отправляет заданию таймера запрос на ответ об ожидающих действиях или состоянии. </span><span class="sxs-lookup"><span data-stu-id="00364-177">The SSA proxy in the SharePoint Content Farm sends a query for pending actions/status response to the Timer job.</span></span> 
    
- <span data-ttu-id="00364-178">Задание таймера отправляет запрос на сайт Contoso SharePoint, который просматривает контент Contoso SharePoint. </span><span class="sxs-lookup"><span data-stu-id="00364-178">The Timer job sends a request to the Contoso SharePoint site, which reviews the Contoso SharePoint content.</span></span> 
    
- <span data-ttu-id="00364-179">Задание таймера отправляет ответ на запрос об ожидающих действиях или состоянии на прокси-сервер SSA на ферме контента SharePoint. Затем ответ отправляется в службу SSA на ферме служб SharePoint. </span><span class="sxs-lookup"><span data-stu-id="00364-179">The response to the pending actions/status query is sent from the Timer job to the SSA proxy in the SharePoint Content Farm, and then it is sent to the SSA service in the SharePoint Services Farm</span></span> 
    
#### <a name="exchange-2013"></a><span data-ttu-id="00364-180">Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="00364-180">Exchange 2013</span></span>

<span data-ttu-id="00364-181">Компонент "Сервер Exchange 2013" включает веб-службы Exchange и предоставляет следующие возможности: </span><span class="sxs-lookup"><span data-stu-id="00364-181">The Exchange 2013 server component contains the Exchange Web Service and provides the following:</span></span> 
  
- <span data-ttu-id="00364-182">Сервер сервер управления безопасностью/OAuth обрабатывается между фермой контента SharePoint 2013 и Exchange 2013.</span><span class="sxs-lookup"><span data-stu-id="00364-182">Server-to-server Trust/OAuth is handled between the SharePoint 2013 Content Farm and Exchange 2013.</span></span> 
    
- <span data-ttu-id="00364-183">обработка межсерверных отношений доверия и протокола OAuth между Exchange 2013 и Lync 2013. </span><span class="sxs-lookup"><span data-stu-id="00364-183">Server-to-server Trust/OAuth is handled between Exchange 2013 and Lync 2013.</span></span> 
    
#### <a name="lync-2013"></a><span data-ttu-id="00364-184">Lync 2013</span><span class="sxs-lookup"><span data-stu-id="00364-184">Lync 2013</span></span>

<span data-ttu-id="00364-185">Компонент Lync 2013 архивирует содержимое Lync в Exchange 2013. </span><span class="sxs-lookup"><span data-stu-id="00364-185">The Lync 2013 component archives Lync content in Exchange 2013.</span></span> 
  
#### <a name="windows-file-shares"></a><span data-ttu-id="00364-186">Общие файловые ресурсы Windows</span><span class="sxs-lookup"><span data-stu-id="00364-186">Windows File Shares</span></span>

<span data-ttu-id="00364-187">Компонент "Общие файловые ресурсы Windows" предоставляет результаты обхода контента приложению службы поиска на ферме служб SharePoint. </span><span class="sxs-lookup"><span data-stu-id="00364-187">The Windows File Shares component provides crawl results to the SSA in the SharePoint Services Farm.</span></span> 
  
### <a name="legend"></a><span data-ttu-id="00364-188">Условные обозначения</span><span class="sxs-lookup"><span data-stu-id="00364-188">Legend</span></span>

<span data-ttu-id="00364-189">В условных обозначениях на этой схеме указаны типы трафика между компонентами, представленные следующими цветными линиями. </span><span class="sxs-lookup"><span data-stu-id="00364-189">The legend for this diagram graphically shows the different types of traffic depicted among the components in different colored lines as follows:</span></span> 
  
- <span data-ttu-id="00364-190">Светло-синий строки: запрос и действия - электронного обнаружения данных запроса или действие</span><span class="sxs-lookup"><span data-stu-id="00364-190">Light blue line: Query/action - eDiscovery query or action data</span></span> 
    
- <span data-ttu-id="00364-191">Оранжевый строки: eDisovery ответа - данные ответа запросов обнаружения электронных данных</span><span class="sxs-lookup"><span data-stu-id="00364-191">Orange line: eDisovery response - eDiscovery query response data</span></span> 
    
- <span data-ttu-id="00364-192">Зеленый строки: запрос и ответ состояние - запрос и ответ данных состояние обнаружения электронных данных</span><span class="sxs-lookup"><span data-stu-id="00364-192">Green line: Status query/response - eDiscovery status query/response data</span></span> 
    
- <span data-ttu-id="00364-193">Фиолетовый строки: запрос действие/состоянии Exchange - запрос обнаружения электронных данных на состояние действия для трафика Exchange.</span><span class="sxs-lookup"><span data-stu-id="00364-193">Purple line: Exchange action/status request - eDiscovery request for action status for Exchange traffic.</span></span> 
    
- <span data-ttu-id="00364-194">Красная линия: обмена данных и состояния ответа - eDiscovery запроса или состояния ответа из Exchange.</span><span class="sxs-lookup"><span data-stu-id="00364-194">Red line: Exchange data/status response - eDiscovery query or status response from Exchange.</span></span> 
    
- <span data-ttu-id="00364-195">Пунктирная черная: межсерверные отношения доверия или протокол OAuth. </span><span class="sxs-lookup"><span data-stu-id="00364-195">Dotted black line: Server-to-Server Trust/Oauth</span></span> 
    
- <span data-ttu-id="00364-196">Черная: обход контента и его результаты. </span><span class="sxs-lookup"><span data-stu-id="00364-196">Solid black line: Crawl/results</span></span> 
    

