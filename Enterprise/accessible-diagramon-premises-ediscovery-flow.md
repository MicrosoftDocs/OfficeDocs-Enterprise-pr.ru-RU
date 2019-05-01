---
title: Доступная схема — поток локального обнаружения электронных данных
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
description: Эта статья представляет собой текстовую версию схемы "Поток локального обнаружения электронных данных".
ms.openlocfilehash: e137a75fb80c9198a332144d82fe405c6884aa52
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487705"
---
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a><span data-ttu-id="88d80-103">Доступная схема — поток локального обнаружения электронных данных</span><span class="sxs-lookup"><span data-stu-id="88d80-103">Accessible diagram - On-premises eDiscovery Flow</span></span>

<span data-ttu-id="88d80-104">**Сводка:** Эта статья представляет собой текстовую версию схемы, именуемую локальным процессом обнаружения электронных данных.</span><span class="sxs-lookup"><span data-stu-id="88d80-104">**Summary:** This article is an accessible text version of the diagram named On-premises eDiscovery Flow.</span></span>
  
<span data-ttu-id="88d80-105">На этом плакате представлены подробные сведения об архитектуре и потоке данных серверных продуктов.</span><span class="sxs-lookup"><span data-stu-id="88d80-105">This poster provides details about the architecture and flow of data across server products.</span></span> 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a><span data-ttu-id="88d80-106">В SharePoint, Exchange, Lync и общих файловых ресурсах</span><span class="sxs-lookup"><span data-stu-id="88d80-106">Across SharePoint, Exchange, Lync, and file shares</span></span>

<span data-ttu-id="88d80-107">На схеме показан пользователь, отправляющий запрос на доступ к двум фермам серверов, ферме корпоративных приложений SharePoint 2013 и ферме служб SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="88d80-107">The diagram shows a user sending a query that accesses two server farms, a SharePoint 2013 Enterprise App Farm, and a SharePoint 2013 Services Farm.</span></span> <span data-ttu-id="88d80-108">Ферма SharePoint 2013 Services взаимодействуют с фермой контента SharePoint 2013, Exchange Server 2013 (которая взаимодействуют с Lync 2013) и общими файлами Windows.</span><span class="sxs-lookup"><span data-stu-id="88d80-108">The SharePoint 2013 Services Farm communicates with a SharePoint 2013 Content Farm, Exchange Server 2013 (which communicates with Lync 2013), and Windows File Shares.</span></span> 
  
<span data-ttu-id="88d80-109">Последовательность операций при обнаружении электронных данных описывает поток данных и порядок выполнения действий, связанных с запросами на обнаружение электронных данных в SharePoint, Exchange, Lync и общих файловых ресурсах. </span><span class="sxs-lookup"><span data-stu-id="88d80-109">The eDiscovery Flow List describes the flow of data and the order in which eDisovery query actions occur across SharePoint, Exchange, Lync, and file shares.</span></span> 
  
<span data-ttu-id="88d80-110">Последовательность операций при обнаружении электронных данных подробно описывается в первую очередь. Затем следует детальное описание функций, изображенных на схеме. </span><span class="sxs-lookup"><span data-stu-id="88d80-110">The eDiscovery flow list is described in detail first, followed by a detailed description of the features depicted in the diagram.</span></span> 
  
### <a name="ediscovery-flow-list"></a><span data-ttu-id="88d80-111">Последовательность операций при обнаружении электронных данных</span><span class="sxs-lookup"><span data-stu-id="88d80-111">eDiscovery Flow List</span></span>

<span data-ttu-id="88d80-p102">Номер каждого действия, описанного в этом списке, соответствует шагу, который изображен на схеме. Схема более подробно описана далее в этом документе. </span><span class="sxs-lookup"><span data-stu-id="88d80-p102">The numbers for each of the steps described in this list pertain to a step depicted in the diagram. The diagram is described in detail later in this document.</span></span> 
  
1. <span data-ttu-id="88d80-114">Дела eDiscovery создаются, управляются и используются в центре обнаружения электронных данных (EDC).</span><span class="sxs-lookup"><span data-stu-id="88d80-114">eDiscovery cases are created, managed, and used in the eDiscovery center (EDC).</span></span> <span data-ttu-id="88d80-115">ЦЕНТР EDC это семейство веб-сайтов SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="88d80-115">The EDC is a SharePoint 2013 site collection.</span></span> <span data-ttu-id="88d80-116">В этом центре определяются дела, задаются источники для отслеживания, формируются запросы, проверяются результаты запросов, а также устанавливается на удержание и снимается с удержания содержимое.</span><span class="sxs-lookup"><span data-stu-id="88d80-116">This is where cases are defined, sources to be tracked are identified, queries are issued, query results are reviewed, and holds on content are placed or removed.</span></span> 
    
2. <span data-ttu-id="88d80-117">Запрос или действие при обнаружении электронных данных (например, запрос Hold, ReleaseHold или GetStatus) передаются из центра EDC на прокси-сервер приложения службы поиска (SSA) в ферме корпоративных приложений.</span><span class="sxs-lookup"><span data-stu-id="88d80-117">The eDiscovery query or action, such as place a Hold, ReleaseHold, or GetStatus, is relayed from the EDC to the Search Service Application (SSA) proxy in the Enterprise App Farm.</span></span> <span data-ttu-id="88d80-118">Затем прокси-сервер SSA передает трафик в приложение службы поиска (SSA) в ферме приложений служб.</span><span class="sxs-lookup"><span data-stu-id="88d80-118">The SSA proxy then relays the traffic to the SSA in the Services App Farm.</span></span> <span data-ttu-id="88d80-119">В этом примере запрос состоит в том, чтобы поместить все содержимое в ферму контента SharePoint с именем "CONTOSO" в имени файла при удержании.</span><span class="sxs-lookup"><span data-stu-id="88d80-119">In this example, the request is to place anything in the SharePoint Content Farm with "CONTOSO" in the file name on hold.</span></span> 
    
3. <span data-ttu-id="88d80-p105">Если целью запроса является дело, приложение службы поиска обращается к индексу поиска. Затем набор результатов запроса на обнаружение электронных данных возвращается пользователю через центр EDC. </span><span class="sxs-lookup"><span data-stu-id="88d80-p105">If the request is to query a case, the SSA consults the search index. Then, the eDiscovery query result set returns to the user through the EDC.</span></span> 
    
4. <span data-ttu-id="88d80-122">Если запрос является действием (например, Hold или ReleaseHold), то это действие записывается в таблицу Actions_Table в базе данных администрирования SSA.</span><span class="sxs-lookup"><span data-stu-id="88d80-122">If the request is an action, such as place a Hold or ReleaseHold, that action is written to the Actions_Table in the SSA Administrative database.</span></span> <span data-ttu-id="88d80-123">В этом примере запрос на удержание для всех объектов в ферме контента SharePoint с "CONTOSO" записывается в Актионс_табле.</span><span class="sxs-lookup"><span data-stu-id="88d80-123">In this example, a hold request for anything in the SharePoint Content Farm with "CONTOSO" is written to the Actions_Table.</span></span> 
    
5. <span data-ttu-id="88d80-124">Задание таймера хранения на месте при обнаружении электронных данных регулярно запускается и генерирует запрос об ожидающих действиях, а затем отправляет обновления состояния через прокси-сервер SSA в приложение службы поиска.</span><span class="sxs-lookup"><span data-stu-id="88d80-124">At regular intervals the Content Farm eDiscovery in-place hold timer job wakes up and generates a request for pending actions and sends status updates through the SSA proxy to the SSA.</span></span> 
    
6. <span data-ttu-id="88d80-125">Запрос об ожидающих действиях передается в центральное приложение службы поиска, которое обращается к таблице Action_Table, чтобы найти все ожидающие действия для фермы контента.</span><span class="sxs-lookup"><span data-stu-id="88d80-125">The query for pending actions is relayed to the central SSA, which consults the Action_Table for any pending actions for the Content Farm.</span></span> <span data-ttu-id="88d80-126">Кроме того, задание таймера хранения на месте фермы контента отправляет полученные им обновления состояния объектов и действий, которые записаны в таблице действий.</span><span class="sxs-lookup"><span data-stu-id="88d80-126">The Content Farm in-place hold timer job also sends status updates for objects and actions it has received, which are written to the ActionsTable.</span></span> 
    
7. <span data-ttu-id="88d80-127">Запрос на удержание для любого контента с именем "CONTOSO" в имени в ферме контента SharePoint 2013 отправляется АДАПТЕРом SSA в задание таймера хранения на месте обнаружения электронных данных на месте в ферме контента.</span><span class="sxs-lookup"><span data-stu-id="88d80-127">The hold request for any content with "CONTOSO" in the name in the SharePoint 2013 Content Farm is sent by the SSA to the eDiscovery in-place hold timer job in the Content Farm.</span></span> 
    
8. <span data-ttu-id="88d80-128">Задание таймера хранения на месте обнаружения электронных данных помещает "сайт CONTOSO" и "CONTOSO Content" на удержание.</span><span class="sxs-lookup"><span data-stu-id="88d80-128">The eDiscovery in-place hold timer job places the "CONTOSO Site" and "CONTOSO content" on hold.</span></span> 
    
9. <span data-ttu-id="88d80-129">Задание таймера хранения на месте при обнаружении электронных данных периодически запускается в ферме корпоративных приложений для проверки состояния действий обнаружения и обновляет состояние. </span><span class="sxs-lookup"><span data-stu-id="88d80-129">The eDiscovery in-place hold timer job periodically runs in the Enterprise App Farm to check the status of discovery actions and to update the status.</span></span> 
    
10. <span data-ttu-id="88d80-130">Запрос о состоянии передается через прокси-сервер SSA фермы корпоративных приложений в приложение службы поиска фермы служб SharePoint. </span><span class="sxs-lookup"><span data-stu-id="88d80-130">The status query is relayed through the Enterprise App Farm SSA proxy to the SharePoint Services Farm SSA.</span></span> 
    
11. <span data-ttu-id="88d80-131">Приложение службы поиска получает состояние из таблицы действий и возвращает его заданию таймера в ферме корпоративных приложений, после чего обновления состояния поступают в центр EDC.</span><span class="sxs-lookup"><span data-stu-id="88d80-131">The SSA retrieves the status from the Actions table and returns it to the timer job in the Enterprise App Farm, which pushes the status updates to the EDC.</span></span> 
    
12. <span data-ttu-id="88d80-132">Когда пользователь обнаружения электронных данных осуществляет поиск (или выполняет действие) по источникам Exchange (например, почтовому ящику или архивированному содержимому Lync), центральное приложение службы поиска использует для запросов к веб-службам Exchange прокси-сервер веб-служб Exchange (EWS).</span><span class="sxs-lookup"><span data-stu-id="88d80-132">When the eDiscovery user is searching (or performing an action) for Exchange sources, such as a mailbox or archived Lync content, the central SSA uses Exchange Web Services (EWS) proxy to query Exchange Web Services.</span></span> <span data-ttu-id="88d80-133">Exchange имеет собственную инфраструктуру поиска и обнаружения данных, а также осуществляет внутреннее управление вызовами для обнаружения электронных данных.</span><span class="sxs-lookup"><span data-stu-id="88d80-133">Exchange has its own search and eDiscovery infrastructure and manages all eDiscovery calls internally.</span></span> 
    
13. <span data-ttu-id="88d80-134">Веб-службы Exchange отвечают приложению службы поиска, предоставляя результаты поиска при обнаружении электронных данных или ответ на запрос о состоянии удержания по запросу, которые в свою очередь передаются в центр EDC. </span><span class="sxs-lookup"><span data-stu-id="88d80-134">Exchange Web Services responds to SSA with eDiscovery search results or a response to a status request for a query-based hold, which, in turn, gets relayed to the EDC.</span></span> 
    
#### <a name="prerequisites"></a><span data-ttu-id="88d80-135">Необходимые компоненты</span><span class="sxs-lookup"><span data-stu-id="88d80-135">Prerequisites</span></span>

- <span data-ttu-id="88d80-136">Служба корпоративного поиска SharePoint должна быть настроена. Кроме того, должен успешно выполняться обход контента во всех источниках контента (SharePoint и общих файловых ресурсах Windows), которые должны быть проиндексированы. </span><span class="sxs-lookup"><span data-stu-id="88d80-136">SharePoint Enterprise Search must be configured, search crawls on content sources (SharePoint and Windows file shares) are successfully occurring, and all content sources are in the index.</span></span> 
    
- <span data-ttu-id="88d80-137">Необходимо настроить доверие и проверку подлинности между серверами фермы служб SharePoint и Exchange, а также между службами Exchange и Lync. </span><span class="sxs-lookup"><span data-stu-id="88d80-137">Server-to-server trust and authentication must be configured between the SharePoint Services Farm and Exchange and also between Exchange and Lync.</span></span> 
    
### <a name="description-of-components-in-the-diagram"></a><span data-ttu-id="88d80-138">Описание компонентов на схеме</span><span class="sxs-lookup"><span data-stu-id="88d80-138">Description of components in the diagram</span></span>

<span data-ttu-id="88d80-139">На схеме показан пользователь, отправляющий запрос, который получает доступ к двум фермам серверов, корпоративной ферме приложений SharePoint 2013 и ферме служб SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="88d80-139">The diagram shows a user sending a query, which accesses two server farms, a SharePoint 2013 Enterprise App Farm and a SharePoint 2013 Services Farm.</span></span> <span data-ttu-id="88d80-140">Фермы служб SharePoint Services с фермой контента SharePoint 2013, Exchange Server 2013 (с интерфейсом Lync 2013) и файловыми ресурсами Windows.</span><span class="sxs-lookup"><span data-stu-id="88d80-140">The SharePoint Services Farm interfaces with a SharePoint 2013 Content Farm, Exchange Server 2013 (which interfaces with Lync 2013), and Windows File Shares.</span></span> 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a><span data-ttu-id="88d80-141">Корпоративная ферма приложений SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="88d80-141">SharePoint 2013 Enterprise App Farm</span></span>

<span data-ttu-id="88d80-142">Корпоративная ферма приложений SharePoint 2013 содержит следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="88d80-142">The SharePoint 2013 Enterprise App Farm contains the following components:</span></span> 
  
- <span data-ttu-id="88d80-143">ЦЕНТР EDC</span><span class="sxs-lookup"><span data-stu-id="88d80-143">EDC</span></span>
    
- <span data-ttu-id="88d80-144">прокси-сервер SSA; </span><span class="sxs-lookup"><span data-stu-id="88d80-144">SSA proxy</span></span> 
    
- <span data-ttu-id="88d80-145">задание таймера.</span><span class="sxs-lookup"><span data-stu-id="88d80-145">Timer job</span></span> 
    
<span data-ttu-id="88d80-p110">Запрос или действие, которые отправляет пользователь, направляются в центр EDC в ферме корпоративных приложений. Выполняются следующие действия. </span><span class="sxs-lookup"><span data-stu-id="88d80-p110">A query or action sent by the user is sent to the EDC in the Enterprise App Farm. The following actions occur:</span></span> 
  
- <span data-ttu-id="88d80-148">Запрос или действие передается на прокси-сервер SSA. </span><span class="sxs-lookup"><span data-stu-id="88d80-148">The query or action goes to the SSA proxy.</span></span> 
    
- <span data-ttu-id="88d80-p111">Прокси-сервер SSA отправляет запрос о состоянии или ответ на задание таймера в ферму корпоративных приложений. Этот прокси-сервер также отправляет запрос о состоянии или ответ в службу SSA на ферме служб SharePoint. Действия, которые выполняются в результате этих операций, описаны в разделе о ферме служб SharePoint. </span><span class="sxs-lookup"><span data-stu-id="88d80-p111">The SSA proxy sends a status query or response to the Timer job in the Enterprise App Farm, and it also sends a status query or response to the SSA service in the SharePoint Services Farm. The actions that result from this are described in the section about the SharePoint Services Farm.</span></span> 
    
- <span data-ttu-id="88d80-151">При получении ответа задание таймера отправляет ответ на прокси-сервер SSA и в центр EDC. </span><span class="sxs-lookup"><span data-stu-id="88d80-151">When it receives a response, the Timer job sends the response to the SSA proxy and to the EDC.</span></span> 
    
- <span data-ttu-id="88d80-152">Все результаты запроса или действия отправляются пользователю из центра EDC. </span><span class="sxs-lookup"><span data-stu-id="88d80-152">Any results from the query or action are sent to the user from the EDC.</span></span> 
    
#### <a name="sharepoint-2013-services-farm"></a><span data-ttu-id="88d80-153">Ферма служб SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="88d80-153">SharePoint 2013 Services Farm</span></span>

<span data-ttu-id="88d80-154">Ферма служб SharePoint 2013 содержит следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="88d80-154">The SharePoint 2013 Services Farm contains the following components:</span></span> 
  
- <span data-ttu-id="88d80-155">служба SSA; </span><span class="sxs-lookup"><span data-stu-id="88d80-155">SSA Service</span></span> 
    
- <span data-ttu-id="88d80-156">база данных индекса поиска;</span><span class="sxs-lookup"><span data-stu-id="88d80-156">Search index database</span></span> 
    
- <span data-ttu-id="88d80-157">База данных админ_дб SSA.</span><span class="sxs-lookup"><span data-stu-id="88d80-157">SSA admin_db database.</span></span> <span data-ttu-id="88d80-158">Таблица Actions в этой базе данных содержит: удержание удержания удержания для снятия состояния</span><span class="sxs-lookup"><span data-stu-id="88d80-158">The Actions Table in this database contains: Hold Release Hold GetStatus</span></span> 
    
- <span data-ttu-id="88d80-159">прокси-сервер EWS. </span><span class="sxs-lookup"><span data-stu-id="88d80-159">EWS proxy</span></span> 
    
<span data-ttu-id="88d80-160">Когда прокси-сервер SSA на ферме корпоративных приложений SharePoint отправляет запрос о состоянии приложению службы поиска (SSA) на ферме служб SharePoint, выполняются следующие действия. </span><span class="sxs-lookup"><span data-stu-id="88d80-160">When the SSA proxy in the SharePoint Enterprise App Farm sends a status query to the SSA in the SharePoint Services Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="88d80-p113">Если целью запроса является собственно запрос, приложение службы поиска обращается к индексу поиска. Обнаруженный ответ возвращается сначала в приложение службы поиска, а затем пользователю через центр EDC. </span><span class="sxs-lookup"><span data-stu-id="88d80-p113">If the request is a query, the SSA consults the search index. The discovery response is returned to the SSA and then to the user through the EDC.</span></span> 
    
- <span data-ttu-id="88d80-163">Если запрос представляет собой действие записи, служба SSA отправляет действие записи в базу данных SSA admin_db. </span><span class="sxs-lookup"><span data-stu-id="88d80-163">If the request is a write action, the SSA service sends the write action to the SSA admin_db.</span></span> 
    
- <span data-ttu-id="88d80-164">Запрос на получение результатов обхода и ответ отправляется из адаптера SSA в ферму контента SharePoint 2013, и ответ возвращается в SSA.</span><span class="sxs-lookup"><span data-stu-id="88d80-164">A crawl and responding results request is sent from the SSA to the SharePoint 2013 Content Farm and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="88d80-165">Запрос на обход контента и результаты ответа отправляется из приложения службы поиска в общие файловые ресурсы Windows, а ответ возвращается в приложение службы поиска. </span><span class="sxs-lookup"><span data-stu-id="88d80-165">A crawl and responding results request is sent from the SSA to the Windows File Shares, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="88d80-166">Запрос на ожидающие действия, ответы или обновления состояния отправляется из приложения службы поиска на прокси-сервер SSA на ферме контента SharePoint, а ответ возвращается в приложение службы поиска. </span><span class="sxs-lookup"><span data-stu-id="88d80-166">A query for pending action(s), responses, or status updates is sent from the SSA to the SSA proxy in the SharePoint Content Farm, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="88d80-167">Запрос на действие или состояние Exchange отправляется из приложения службы поиска на прокси-сервер EWS, который отправляет запрос на действие или состояние Exchange в веб-службы Exchange на сервере Exchange 2013.  </span><span class="sxs-lookup"><span data-stu-id="88d80-167">An Exchange action/status request is sent from the SSA to the EWS proxy, which sends an Exchange Query action/status request to the Exchange Web Service on the Exchange 2013 server.</span></span> 
    
- <span data-ttu-id="88d80-168">Запрос о состоянии или ответ отправляется из приложения службы поиска в базу данных admin_db SSA и возвращается в приложение службы поиска. </span><span class="sxs-lookup"><span data-stu-id="88d80-168">A status query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
- <span data-ttu-id="88d80-169">Запрос об ожидающем действии или ответ отправляется из приложения службы поиска в базу данных admin_db SSA и возвращается в приложение службы поиска. </span><span class="sxs-lookup"><span data-stu-id="88d80-169">A pending action query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
#### <a name="sharepoint-2013-content-farm"></a><span data-ttu-id="88d80-170">Ферма контента SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="88d80-170">SharePoint 2013 Content Farm</span></span>

<span data-ttu-id="88d80-171">Ферма контента SharePoint 2013 содержит следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="88d80-171">The SharePoint 2013 Content Farm contains the following components:</span></span> 
  
- <span data-ttu-id="88d80-172">прокси-сервер SSA; </span><span class="sxs-lookup"><span data-stu-id="88d80-172">SSA proxy</span></span> 
    
- <span data-ttu-id="88d80-173">задание таймера;</span><span class="sxs-lookup"><span data-stu-id="88d80-173">Timer job</span></span> 
    
- <span data-ttu-id="88d80-174">сайт Contoso SharePoint; </span><span class="sxs-lookup"><span data-stu-id="88d80-174">Contoso SharePoint site</span></span> 
    
- <span data-ttu-id="88d80-175">контент Contoso SharePoint. </span><span class="sxs-lookup"><span data-stu-id="88d80-175">Contoso SharePoint content</span></span> 
    
<span data-ttu-id="88d80-176">Когда приложение службы поиска (SSA) на ферме служб SharePoint отправляет запрос о состоянии на прокси-сервер SSA на ферме контента SharePoint, выполняются следующие действия. </span><span class="sxs-lookup"><span data-stu-id="88d80-176">When the SSA in the SharePoint Services Farm sends a status query to the SSA Proxy in the SharePoint Content Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="88d80-177">Прокси-сервер SSA на ферме контента SharePoint отправляет заданию таймера запрос на ответ об ожидающих действиях или состоянии. </span><span class="sxs-lookup"><span data-stu-id="88d80-177">The SSA proxy in the SharePoint Content Farm sends a query for pending actions/status response to the Timer job.</span></span> 
    
- <span data-ttu-id="88d80-178">Задание таймера отправляет запрос на сайт Contoso SharePoint, который просматривает контент Contoso SharePoint. </span><span class="sxs-lookup"><span data-stu-id="88d80-178">The Timer job sends a request to the Contoso SharePoint site, which reviews the Contoso SharePoint content.</span></span> 
    
- <span data-ttu-id="88d80-179">Задание таймера отправляет ответ на запрос об ожидающих действиях или состоянии на прокси-сервер SSA на ферме контента SharePoint. Затем ответ отправляется в службу SSA на ферме служб SharePoint. </span><span class="sxs-lookup"><span data-stu-id="88d80-179">The response to the pending actions/status query is sent from the Timer job to the SSA proxy in the SharePoint Content Farm, and then it is sent to the SSA service in the SharePoint Services Farm</span></span> 
    
#### <a name="exchange-2013"></a><span data-ttu-id="88d80-180">Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="88d80-180">Exchange 2013</span></span>

<span data-ttu-id="88d80-181">Компонент "Сервер Exchange 2013" включает веб-службы Exchange и предоставляет следующие возможности: </span><span class="sxs-lookup"><span data-stu-id="88d80-181">The Exchange 2013 server component contains the Exchange Web Service and provides the following:</span></span> 
  
- <span data-ttu-id="88d80-182">Отношения доверия между серверами и OAuth выполняются между фермой контента SharePoint 2013 и Exchange 2013.</span><span class="sxs-lookup"><span data-stu-id="88d80-182">Server-to-server Trust/OAuth is handled between the SharePoint 2013 Content Farm and Exchange 2013.</span></span> 
    
- <span data-ttu-id="88d80-183">обработка межсерверных отношений доверия и протокола OAuth между Exchange 2013 и Lync 2013. </span><span class="sxs-lookup"><span data-stu-id="88d80-183">Server-to-server Trust/OAuth is handled between Exchange 2013 and Lync 2013.</span></span> 
    
#### <a name="lync-2013"></a><span data-ttu-id="88d80-184">Lync 2013</span><span class="sxs-lookup"><span data-stu-id="88d80-184">Lync 2013</span></span>

<span data-ttu-id="88d80-185">Компонент Lync 2013 архивирует содержимое Lync в Exchange 2013. </span><span class="sxs-lookup"><span data-stu-id="88d80-185">The Lync 2013 component archives Lync content in Exchange 2013.</span></span> 
  
#### <a name="windows-file-shares"></a><span data-ttu-id="88d80-186">Общие файловые ресурсы Windows</span><span class="sxs-lookup"><span data-stu-id="88d80-186">Windows File Shares</span></span>

<span data-ttu-id="88d80-187">Компонент "Общие файловые ресурсы Windows" предоставляет результаты обхода контента приложению службы поиска на ферме служб SharePoint. </span><span class="sxs-lookup"><span data-stu-id="88d80-187">The Windows File Shares component provides crawl results to the SSA in the SharePoint Services Farm.</span></span> 
  
### <a name="legend"></a><span data-ttu-id="88d80-188">Условные обозначения</span><span class="sxs-lookup"><span data-stu-id="88d80-188">Legend</span></span>

<span data-ttu-id="88d80-189">В условных обозначениях на этой схеме указаны типы трафика между компонентами, представленные следующими цветными линиями. </span><span class="sxs-lookup"><span data-stu-id="88d80-189">The legend for this diagram graphically shows the different types of traffic depicted among the components in different colored lines as follows:</span></span> 
  
- <span data-ttu-id="88d80-190">Светло-синяя линия: запрос и действие — запрос на обнаружение электронных данных или данные действий</span><span class="sxs-lookup"><span data-stu-id="88d80-190">Light blue line: Query/action - eDiscovery query or action data</span></span> 
    
- <span data-ttu-id="88d80-191">Оранжевая строка: данные ответа на запрос Едисовери для ответа на обнаружение электронных данных</span><span class="sxs-lookup"><span data-stu-id="88d80-191">Orange line: eDisovery response - eDiscovery query response data</span></span> 
    
- <span data-ttu-id="88d80-192">Зеленая линия: состояние "запрос/ответ-состояние обнаружения электронных данных". данные запроса/ответа</span><span class="sxs-lookup"><span data-stu-id="88d80-192">Green line: Status query/response - eDiscovery status query/response data</span></span> 
    
- <span data-ttu-id="88d80-193">Фиолетовая линия: запрос действий или состояния Exchange — запрос обнаружения электронных данных для трафика Exchange.</span><span class="sxs-lookup"><span data-stu-id="88d80-193">Purple line: Exchange action/status request - eDiscovery request for action status for Exchange traffic.</span></span> 
    
- <span data-ttu-id="88d80-194">Красная линия: Exchange Data/Status Response — запрос eDiscovery или ответ о состоянии из Exchange.</span><span class="sxs-lookup"><span data-stu-id="88d80-194">Red line: Exchange data/status response - eDiscovery query or status response from Exchange.</span></span> 
    
- <span data-ttu-id="88d80-195">Пунктирная черная: межсерверные отношения доверия или протокол OAuth. </span><span class="sxs-lookup"><span data-stu-id="88d80-195">Dotted black line: Server-to-Server Trust/Oauth</span></span> 
    
- <span data-ttu-id="88d80-196">Черная: обход контента и его результаты. </span><span class="sxs-lookup"><span data-stu-id="88d80-196">Solid black line: Crawl/results</span></span> 
    

