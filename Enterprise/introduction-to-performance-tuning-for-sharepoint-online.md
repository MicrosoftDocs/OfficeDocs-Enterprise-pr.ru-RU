---
title: Общие сведения о настройке производительности для SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/22/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 81c4be5f-327e-435d-a568-526d68cffef0
description: В этой статье описываются конкретные аспекты, которые необходимо учитывать при проектировании страниц для достижения оптимальной производительности в SharePoint Online.
ms.openlocfilehash: 07938770d711477126f78fc583e8d2533ba5c1d1
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487173"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a><span data-ttu-id="4d88e-103">Общие сведения о настройке производительности для SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="4d88e-103">Introduction to performance tuning for SharePoint Online</span></span>

<span data-ttu-id="4d88e-104">В этой статье описываются конкретные аспекты, которые необходимо учитывать при проектировании страниц для достижения оптимальной производительности в SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="4d88e-104">This article explains what specific aspects you need to consider when designing pages for best performance in SharePoint Online.</span></span>
     
## <a name="sharepoint-online-metrics"></a><span data-ttu-id="4d88e-105">Метрики SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="4d88e-105">SharePoint Online metrics</span></span>

<span data-ttu-id="4d88e-106">Следующие обширные показатели для SharePoint Online предоставляют реальные сведения о производительности:</span><span class="sxs-lookup"><span data-stu-id="4d88e-106">The following broad metrics for SharePoint Online provide real world data about performance:</span></span>
  
- <span data-ttu-id="4d88e-107">Скорость загрузки страниц</span><span class="sxs-lookup"><span data-stu-id="4d88e-107">How fast pages load</span></span>
    
- <span data-ttu-id="4d88e-108">Сколько циклов обработки, необходимых для каждой страницы</span><span class="sxs-lookup"><span data-stu-id="4d88e-108">How many round trips required per page</span></span>
    
- <span data-ttu-id="4d88e-109">Проблемы со службой</span><span class="sxs-lookup"><span data-stu-id="4d88e-109">Issues with the service</span></span>
    
- <span data-ttu-id="4d88e-110">Другие факторы, которые приводят к ухудшению производительности</span><span class="sxs-lookup"><span data-stu-id="4d88e-110">Other things that cause performance degradation</span></span>
    
### <a name="conclusions-reached-because-of-the-data"></a><span data-ttu-id="4d88e-111">Выводы, достигнутые из-за данных</span><span class="sxs-lookup"><span data-stu-id="4d88e-111">Conclusions reached because of the data</span></span>

<span data-ttu-id="4d88e-112">Данные сообщают нам:</span><span class="sxs-lookup"><span data-stu-id="4d88e-112">The data tells us:</span></span>
  
- <span data-ttu-id="4d88e-113">Большинство страниц прекрасно подходят для SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="4d88e-113">Most of the pages perform well on SharePoint Online.</span></span>
    
- <span data-ttu-id="4d88e-114">Загрузка ненастраиваемых страниц выполняется очень быстро.</span><span class="sxs-lookup"><span data-stu-id="4d88e-114">Non-customized pages load very quickly.</span></span>
    
- <span data-ttu-id="4d88e-115">OneDrive для бизнеса, сайты групп и системные страницы, такие как _layouts и т. д., быстро загружаются.</span><span class="sxs-lookup"><span data-stu-id="4d88e-115">OneDrive for Business, team sites and system pages, such as _layouts, etc., are all quick to load.</span></span>
    
- <span data-ttu-id="4d88e-116">Медленная загрузка 1% страниц SharePoint Online требует более 5 000 миллисекунд.</span><span class="sxs-lookup"><span data-stu-id="4d88e-116">The slowest 1% of SharePoint Online pages take more than 5,000 milliseconds to load.</span></span>
    
<span data-ttu-id="4d88e-117">Один простой тест производительности можно использовать для измерения производительности путем сравнения времени загрузки вашего собственного портала с временем загрузки домашней страницы OneDrive для бизнеса, так как в ней используется небольшое количество настраиваемых функций.</span><span class="sxs-lookup"><span data-stu-id="4d88e-117">One simple benchmark test you can use would be to measure performance by comparing the load time of your own portal against the load time of the OneDrive for Business home page as it uses few customized features.</span></span> <span data-ttu-id="4d88e-118">Это, как правило, является первым шагом при устранении проблем с производительностью сети.</span><span class="sxs-lookup"><span data-stu-id="4d88e-118">This will often be the first step Support will ask you to complete when troubleshooting network performance issues.</span></span>
  
## <a name="use-a-standard-user-account-when-checking-performance"></a><span data-ttu-id="4d88e-119">Использование стандартной учетной записи пользователя при проверке производительности</span><span class="sxs-lookup"><span data-stu-id="4d88e-119">Use a standard user account when checking performance</span></span>

<span data-ttu-id="4d88e-120">Администратор семейства веб-сайтов, владелец сайта, редактор или участник относятся к дополнительным группам безопасности, имеют дополнительные разрешения и, таким образом, имеют дополнительные элементы, загружаемые SharePoint на странице.</span><span class="sxs-lookup"><span data-stu-id="4d88e-120">A Site Collection Administrator, Site Owner, Editor, or Contributor belong to additional security groups, have additional permissions, and therefore have additional elements that SharePoint loads on a page.</span></span>
  
<span data-ttu-id="4d88e-121">Это применимо к локальной среде SharePoint и SharePoint Online, но в локальной ситуации различия не будут отображаться как в SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="4d88e-121">This is applicable to SharePoint on-premises and SharePoint Online but in an on-premises scenario the differences will not be as easily noticed as in SharePoint Online.</span></span>
  
<span data-ttu-id="4d88e-122">Чтобы правильно оценить, как страница будет выполняться для пользователей, следует использовать стандартную учетную запись пользователя, чтобы не загружать элементы управления разработки и дополнительный трафик, связанный с группами безопасности.</span><span class="sxs-lookup"><span data-stu-id="4d88e-122">In order to correctly evaluate how a page will perform for users, you should use a standard user account to avoid loading the authoring controls and additional traffic related to security groups.</span></span>
  
## <a name="connection-categories-for-performance-tuning"></a><span data-ttu-id="4d88e-123">Категории подключений для настройки производительности</span><span class="sxs-lookup"><span data-stu-id="4d88e-123">Connection categories for performance tuning</span></span>

<span data-ttu-id="4d88e-124">Вы можете классифицировать подключения между сервером и пользователем на три основных компонента.</span><span class="sxs-lookup"><span data-stu-id="4d88e-124">You can categorize the connections between the server and the user into three main components.</span></span> <span data-ttu-id="4d88e-125">Учитывайте их при проектировании страниц SharePoint Online, чтобы получить представление о времени загрузки.</span><span class="sxs-lookup"><span data-stu-id="4d88e-125">Consider these when designing SharePoint Online pages for insight into load times.</span></span>
  
- <span data-ttu-id="4d88e-126">**Server (сервер** ) Серверы, размещенные корпорацией Майкрософт в центрах обработки данных.</span><span class="sxs-lookup"><span data-stu-id="4d88e-126">**Server** The servers that Microsoft hosts in datacenters.</span></span>
    
- <span data-ttu-id="4d88e-127">**Network (сеть** ) Сеть Майкрософт, Интернет и локальная сеть между центром обработки данных и пользователями.</span><span class="sxs-lookup"><span data-stu-id="4d88e-127">**Network** The Microsoft network, the Internet, and your on-premises network between the datacenter and your users.</span></span>
    
- <span data-ttu-id="4d88e-128">**Browser (браузер** ) Место загрузки страницы.</span><span class="sxs-lookup"><span data-stu-id="4d88e-128">**Browser** Where the page is loaded.</span></span>
    
<span data-ttu-id="4d88e-129">В этих трех подключениях обычно существует пять причин, вызывающих 95% от медленных страниц.</span><span class="sxs-lookup"><span data-stu-id="4d88e-129">Within these three connections there are typically five reasons that cause 95% of slow pages.</span></span> <span data-ttu-id="4d88e-130">Каждая из этих причин обсуждается в этой статье:</span><span class="sxs-lookup"><span data-stu-id="4d88e-130">Each of these reasons is discussed in this article:</span></span>
  
- <span data-ttu-id="4d88e-131">Проблемы с навигацией</span><span class="sxs-lookup"><span data-stu-id="4d88e-131">Navigation issues</span></span>
    
- <span data-ttu-id="4d88e-132">Сведение контента</span><span class="sxs-lookup"><span data-stu-id="4d88e-132">Content roll up</span></span>
    
- <span data-ttu-id="4d88e-133">Большие файлы</span><span class="sxs-lookup"><span data-stu-id="4d88e-133">Large files</span></span>
    
- <span data-ttu-id="4d88e-134">Большое количество запросов к серверу</span><span class="sxs-lookup"><span data-stu-id="4d88e-134">Many requests to the server</span></span>
    
- <span data-ttu-id="4d88e-135">Обработка веб-части</span><span class="sxs-lookup"><span data-stu-id="4d88e-135">Web Part processing</span></span>
    
### <a name="server-connection"></a><span data-ttu-id="4d88e-136">Подключение к серверу</span><span class="sxs-lookup"><span data-stu-id="4d88e-136">Server connection</span></span>

<span data-ttu-id="4d88e-137">Многие проблемы, влияющие на производительность в локальной среде SharePoint, также применимы к SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="4d88e-137">Many of the issues that affect performance with SharePoint on-premises also apply to SharePoint Online.</span></span>
  
<span data-ttu-id="4d88e-138">Как вы ожидали, у вас есть гораздо больший контроль над тем, как серверы выполняют с локальной SharePoint.</span><span class="sxs-lookup"><span data-stu-id="4d88e-138">As you would expect, you have far more control over how servers perform with on-premises SharePoint.</span></span> <span data-ttu-id="4d88e-139">Некоторые функции SharePoint Online немного отличаются.</span><span class="sxs-lookup"><span data-stu-id="4d88e-139">With SharePoint Online things are a little different.</span></span> <span data-ttu-id="4d88e-140">Чем больше усилий вы сделаете сервер, тем дольше он занимается отображением страницы.</span><span class="sxs-lookup"><span data-stu-id="4d88e-140">The more work you make a server do, the longer it takes to render a page.</span></span> <span data-ttu-id="4d88e-141">В SharePoint самым существенным виновником является сложная страница с несколькими веб-частями.</span><span class="sxs-lookup"><span data-stu-id="4d88e-141">With SharePoint, the biggest culprit in this respect are complex pages with multiple web parts.</span></span>
  
<span data-ttu-id="4d88e-142">Локальная среда SharePoint Server</span><span class="sxs-lookup"><span data-stu-id="4d88e-142">SharePoint Server on-premises</span></span>
  
![Снимок экрана: локальный сервер](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
<span data-ttu-id="4d88e-144">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="4d88e-144">SharePoint Online</span></span>
  
![Снимок экрана: сервер в сети](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
<span data-ttu-id="4d88e-146">В SharePoint Online некоторые запросы страниц могут фактически вызывать несколько серверов.</span><span class="sxs-lookup"><span data-stu-id="4d88e-146">With SharePoint Online, certain page requests may actually end up calling multiple servers.</span></span> <span data-ttu-id="4d88e-147">Вы можете получить матрицу запросов между серверами для отдельного запроса.</span><span class="sxs-lookup"><span data-stu-id="4d88e-147">You could end up with a matrix of requests between servers for an individual request.</span></span> <span data-ttu-id="4d88e-148">Эти взаимодействия требуют значительных затрат на загрузку страницы и замедляют выполнение.</span><span class="sxs-lookup"><span data-stu-id="4d88e-148">These interactions are expensive from a page load perspective and will make things slow.</span></span>
  
<span data-ttu-id="4d88e-149">Примеры взаимодействия между сервером и сервером:</span><span class="sxs-lookup"><span data-stu-id="4d88e-149">Examples of these server to server interactions are:</span></span>
  
- <span data-ttu-id="4d88e-150">Веб-серверы SQL Server</span><span class="sxs-lookup"><span data-stu-id="4d88e-150">Web to SQL Servers</span></span>
    
- <span data-ttu-id="4d88e-151">Веб-сайт для серверов приложений</span><span class="sxs-lookup"><span data-stu-id="4d88e-151">Web to application servers</span></span>
    
<span data-ttu-id="4d88e-152">Еще одна вещь, которая может замедлить взаимодействие с сервером, — это промахи кэша.</span><span class="sxs-lookup"><span data-stu-id="4d88e-152">The other thing that can slow down server interactions is cache misses.</span></span> <span data-ttu-id="4d88e-153">В отличие от локальной SharePoint, существует очень тонкая вероятность того, что вы найдете на тот же сервер для страницы, которую вы посещали ранее; Это делает кэширование объектов устаревшим.</span><span class="sxs-lookup"><span data-stu-id="4d88e-153">Unlike on-premises SharePoint, there is a very slim chance that you will hit the same server for a page that you have visited previously; this makes object caching obsolete.</span></span>
  
### <a name="network-connection"></a><span data-ttu-id="4d88e-154">Подключение к сети </span><span class="sxs-lookup"><span data-stu-id="4d88e-154">Network connection</span></span>

<span data-ttu-id="4d88e-155">Если локальная среда SharePoint не использует ГЛОБАЛЬную сеть, вы можете использовать высокоскоростное подключение между центром обработки данных и конечными пользователями.</span><span class="sxs-lookup"><span data-stu-id="4d88e-155">With on-premises SharePoint that doesn't make use of a WAN, you may use a high-speed connection between datacenter and end-users.</span></span> <span data-ttu-id="4d88e-156">Как правило, управление с точки зрения сети упрощается.</span><span class="sxs-lookup"><span data-stu-id="4d88e-156">Generally, things are easy to manage from a network perspective.</span></span>
  
<span data-ttu-id="4d88e-157">В SharePoint Online можно рассмотреть еще несколько факторов. Например:</span><span class="sxs-lookup"><span data-stu-id="4d88e-157">With SharePoint Online, there are a few more factors to consider; for example:</span></span>
  
- <span data-ttu-id="4d88e-158">Сеть Майкрософт</span><span class="sxs-lookup"><span data-stu-id="4d88e-158">The Microsoft network</span></span>
    
- <span data-ttu-id="4d88e-159">Интернет</span><span class="sxs-lookup"><span data-stu-id="4d88e-159">The Internet</span></span>
    
- <span data-ttu-id="4d88e-160">ПОСТАВЩИК услуг Интернета</span><span class="sxs-lookup"><span data-stu-id="4d88e-160">The ISP</span></span>
    
<span data-ttu-id="4d88e-161">Независимо от того, какая версия SharePoint (и какая сеть используется), то, что обычно вызывает загрузку сети, не зависит от следующих факторов:</span><span class="sxs-lookup"><span data-stu-id="4d88e-161">Regardless of which version of SharePoint (and which network) you are using, things that will typically cause the network to be busy include:</span></span>
  
- <span data-ttu-id="4d88e-162">Большие полезные данные</span><span class="sxs-lookup"><span data-stu-id="4d88e-162">Large payload</span></span>
    
- <span data-ttu-id="4d88e-163">Много файлов</span><span class="sxs-lookup"><span data-stu-id="4d88e-163">Many files</span></span>
    
- <span data-ttu-id="4d88e-164">Большое физическое расстояние до сервера</span><span class="sxs-lookup"><span data-stu-id="4d88e-164">Large physical distance to the server</span></span>
    
<span data-ttu-id="4d88e-165">В SharePoint Online можно использовать одну функциональную возможность — Microsoft CDN (сеть доставки содержимого).</span><span class="sxs-lookup"><span data-stu-id="4d88e-165">One feature that you can leverage in SharePoint Online is the Microsoft CDN (Content Delivery Network).</span></span> <span data-ttu-id="4d88e-166">Сеть CDN — это, по сути, распределенная коллекция серверов, развернутых в нескольких центрах обработки данных.</span><span class="sxs-lookup"><span data-stu-id="4d88e-166">A CDN is basically a distributed collection of servers deployed across multiple datacenters.</span></span> <span data-ttu-id="4d88e-167">С помощью сети CDN содержимое страниц может размещаться на сервере, близком к клиенту, даже если клиент находится далеко от исходного сервера SharePoint.</span><span class="sxs-lookup"><span data-stu-id="4d88e-167">With a CDN, content on pages can be hosted on a server close to the client even if the client is far away from the originating SharePoint Server.</span></span> <span data-ttu-id="4d88e-168">В дальнейшем Майкрософт будет использовать эту возможность для хранения локальных экземпляров страниц, которые нельзя изменить, например домашней страницы администратора SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="4d88e-168">Microsoft will be using this more in the future to store local instances of pages which cannot be customized, for example the SharePoint Online admin home page.</span></span> <span data-ttu-id="4d88e-169">Дополнительные сведения о сети CDN можно найти в статье [Доставка содержимого в сети](https://docs.microsoft.com/en-us/office365/enterprise/content-delivery-networks).</span><span class="sxs-lookup"><span data-stu-id="4d88e-169">For more information about CDNs, see [Content delivery networks](https://docs.microsoft.com/en-us/office365/enterprise/content-delivery-networks).</span></span>
  
<span data-ttu-id="4d88e-170">Что вам нужно знать о том, что вам не удастся выполнить многие действия — скорость подключения поставщика услуг Интернета.</span><span class="sxs-lookup"><span data-stu-id="4d88e-170">Something that you need to be aware of but may not be able to do much about is the connection speed of your ISP.</span></span> <span data-ttu-id="4d88e-171">С помощью средства простого теста скорости вы узнаете скорость подключения.</span><span class="sxs-lookup"><span data-stu-id="4d88e-171">A simple speed test tool will tell you the connection speed.</span></span>
  
### <a name="browser-connection"></a><span data-ttu-id="4d88e-172">Подключение к браузеру</span><span class="sxs-lookup"><span data-stu-id="4d88e-172">Browser connection</span></span>

<span data-ttu-id="4d88e-173">Существует несколько факторов, которые следует учитывать в веб-браузерах с точки зрения производительности.</span><span class="sxs-lookup"><span data-stu-id="4d88e-173">There are a few factors to consider with web browsers from a performance perspective.</span></span>
  
<span data-ttu-id="4d88e-174">Посещение сложных страниц повлияет на производительность.</span><span class="sxs-lookup"><span data-stu-id="4d88e-174">Visiting complex pages will affect performance.</span></span> <span data-ttu-id="4d88e-175">Большинство браузеров имеют небольшой кэш (вокруг 90MB), в то время как средняя веб-страница обычно около 1,6 МБ.</span><span class="sxs-lookup"><span data-stu-id="4d88e-175">Most browsers only have a small cache (around 90MB), while the average web page is typically around 1.6MB.</span></span> <span data-ttu-id="4d88e-176">Это не займет много времени.</span><span class="sxs-lookup"><span data-stu-id="4d88e-176">This doesn't take long to get used up.</span></span>
  
<span data-ttu-id="4d88e-177">ПроПускная способность также может быть ошибкой.</span><span class="sxs-lookup"><span data-stu-id="4d88e-177">Bandwidth may also be an issue.</span></span> <span data-ttu-id="4d88e-178">Например, если пользователь смотрит видео в другом сеансе, это повлияет на производительность страницы SharePoint.</span><span class="sxs-lookup"><span data-stu-id="4d88e-178">For example, if a user is watching videos in another session, this will affect the performance of your SharePoint page.</span></span> <span data-ttu-id="4d88e-179">Несмотря на то, что вы не можете запретить пользователям потоковой передачи мультимедиа, вы можете управлять тем, как страница будет загружаться для пользователей.</span><span class="sxs-lookup"><span data-stu-id="4d88e-179">While you can't prevent users from streaming media, you can control the way a page will load for users.</span></span>
  
<span data-ttu-id="4d88e-180">Ознакомьтесь со следующими статьями для различных способов настройки страниц SharePoint Online и другими рекомендациями, которые помогут добиться оптимальной производительности.</span><span class="sxs-lookup"><span data-stu-id="4d88e-180">Check out the following articles for different SharePoint Online page customization techniques and other best practices to help you achieve optimal performance.</span></span>
  
- [<span data-ttu-id="4d88e-181">Параметры навигации для SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="4d88e-181">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="4d88e-182">Использование средства диагностики страниц для SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="4d88e-182">Use the Page Diagnostics tool for SharePoint Online</span></span>](page-diagnostics-for-spo.md)
    
- [<span data-ttu-id="4d88e-183">Оптимизация изображений для SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="4d88e-183">Image optimization for SharePoint Online</span></span>](image-optimization-for-sharepoint-online.md)
    
- [<span data-ttu-id="4d88e-184">Задержка при загрузке изображений и JavaScript-файлов в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="4d88e-184">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [<span data-ttu-id="4d88e-185">Минификация и объединение в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="4d88e-185">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="4d88e-186">Использование сетей доставки содержимого</span><span class="sxs-lookup"><span data-stu-id="4d88e-186">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="4d88e-187">Использование веб-части поиска контента вместо веб-части "Запрос контента" для улучшения производительности в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="4d88e-187">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [<span data-ttu-id="4d88e-188">Планирование и тестирование загрузки SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="4d88e-188">Capacity planning and load testing SharePoint Online</span></span>](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [<span data-ttu-id="4d88e-189">Диагностика проблем производительности в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="4d88e-189">Diagnosing performance issues with SharePoint Online</span></span>](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [<span data-ttu-id="4d88e-190">Использование кэша объектов в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="4d88e-190">Using the object cache with SharePoint Online</span></span>](using-the-object-cache-with-sharepoint-online.md)
    
- [<span data-ttu-id="4d88e-191">Как избежать регулирования количества запросов или блокировки в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="4d88e-191">How to: Avoid getting throttled or blocked in SharePoint Online</span></span>](https://msdn.microsoft.com/en-us/library/office/dn889829.aspx)
    

