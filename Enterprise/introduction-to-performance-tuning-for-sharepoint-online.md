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
description: В этой статье объясняется, какие определенными аспектами, которым следует уделить внимание при разработке страниц для достижения оптимальной производительности в SharePoint Online.
ms.openlocfilehash: 07938770d711477126f78fc583e8d2533ba5c1d1
ms.sourcegitcommit: ba91a1d2d785c1df425617b309fec2edc093793a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2018
ms.locfileid: "26219879"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a><span data-ttu-id="ba1ad-103">Общие сведения о настройке производительности для SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ba1ad-103">Introduction to performance tuning for SharePoint Online</span></span>

<span data-ttu-id="ba1ad-104">В этой статье объясняется, какие определенными аспектами, которым следует уделить внимание при разработке страниц для достижения оптимальной производительности в SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="ba1ad-104">This article explains what specific aspects you need to consider when designing pages for best performance in SharePoint Online.</span></span>
     
## <a name="sharepoint-online-metrics"></a><span data-ttu-id="ba1ad-105">Метрики SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ba1ad-105">SharePoint Online metrics</span></span>

<span data-ttu-id="ba1ad-106">Реальные данные о производительности предоставляются следующими расширенными метриками для SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="ba1ad-106">The following broad metrics for SharePoint Online provide real world data about performance:</span></span>
  
- <span data-ttu-id="ba1ad-107">скорость загрузки страницы;</span><span class="sxs-lookup"><span data-stu-id="ba1ad-107">How fast pages load</span></span>
    
- <span data-ttu-id="ba1ad-108">количество круговых путей на страницу;</span><span class="sxs-lookup"><span data-stu-id="ba1ad-108">How many round trips required per page</span></span>
    
- <span data-ttu-id="ba1ad-109">проблемы с работой службы;</span><span class="sxs-lookup"><span data-stu-id="ba1ad-109">Issues with the service</span></span>
    
- <span data-ttu-id="ba1ad-110">другие причины снижения производительности.</span><span class="sxs-lookup"><span data-stu-id="ba1ad-110">Other things that cause performance degradation</span></span>
    
### <a name="conclusions-reached-because-of-the-data"></a><span data-ttu-id="ba1ad-111">Выводы, полученные на основе этих данных</span><span class="sxs-lookup"><span data-stu-id="ba1ad-111">Conclusions reached because of the data</span></span>

<span data-ttu-id="ba1ad-112">Эти данные говорят о том, что:</span><span class="sxs-lookup"><span data-stu-id="ba1ad-112">The data tells us:</span></span>
  
- <span data-ttu-id="ba1ad-113">Большая часть страниц в SharePoint Online работает хорошо.</span><span class="sxs-lookup"><span data-stu-id="ba1ad-113">Most of the pages perform well on SharePoint Online.</span></span>
    
- <span data-ttu-id="ba1ad-114">Ненастроенные страницы загружаются очень быстро.</span><span class="sxs-lookup"><span data-stu-id="ba1ad-114">Non-customized pages load very quickly.</span></span>
    
- <span data-ttu-id="ba1ad-115">OneDrive для бизнеса, сайты групп и системные страницы, например _layouts и другие, загружаются быстро.</span><span class="sxs-lookup"><span data-stu-id="ba1ad-115">OneDrive for Business, team sites and system pages, such as _layouts, etc., are all quick to load.</span></span>
    
- <span data-ttu-id="ba1ad-116">Самые медленные страницы SharePoint Online составляют 1 %, и для их загрузки требуется более 5000 миллисекунд.</span><span class="sxs-lookup"><span data-stu-id="ba1ad-116">The slowest 1% of SharePoint Online pages take more than 5,000 milliseconds to load.</span></span>
    
<span data-ttu-id="ba1ad-p101">Чтобы оценить производительность, вы можете использовать один простой тест, который заключается в сравнении времени загрузки своего портала со временем загрузки домашней страницы OneDrive для бизнеса, так как она использует несколько пользовательских функций. Как правило, это первый шаг, который вас попросит выполнить служба поддержки при устранении неполадок производительности сети.</span><span class="sxs-lookup"><span data-stu-id="ba1ad-p101">One simple benchmark test you can use would be to measure performance by comparing the load time of your own portal against the load time of the OneDrive for Business home page as it uses few customized features. This will often be the first step Support will ask you to complete when troubleshooting network performance issues.</span></span>
  
## <a name="use-a-standard-user-account-when-checking-performance"></a><span data-ttu-id="ba1ad-119">Используйте стандартную учетную запись пользователя, при проверке производительности</span><span class="sxs-lookup"><span data-stu-id="ba1ad-119">Use a standard user account when checking performance</span></span>

<span data-ttu-id="ba1ad-120">Администратор семейства веб-сайтов, владельца веб-сайта, редактора или участник принадлежать к группам обеспечения дополнительного уровня безопасности, имеют дополнительные разрешения и поэтому имеют дополнительные элементы, которые загружает SharePoint на странице.</span><span class="sxs-lookup"><span data-stu-id="ba1ad-120">A Site Collection Administrator, Site Owner, Editor, or Contributor belong to additional security groups, have additional permissions, and therefore have additional elements that SharePoint loads on a page.</span></span>
  
<span data-ttu-id="ba1ad-121">Это относится к SharePoint для локальной и SharePoint Online, но в сценарии локального различия будет не замечено так же легко, как и в SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="ba1ad-121">This is applicable to SharePoint on-premises and SharePoint Online but in an on-premises scenario the differences will not be as easily noticed as in SharePoint Online.</span></span>
  
<span data-ttu-id="ba1ad-122">Чтобы правильно оценить, как страница будет выполнять для пользователей, следует использовать стандартную учетную запись пользователя во избежание загрузки Разработка элементов управления и дополнительных трафика, связанные с группами безопасности.</span><span class="sxs-lookup"><span data-stu-id="ba1ad-122">In order to correctly evaluate how a page will perform for users, you should use a standard user account to avoid loading the authoring controls and additional traffic related to security groups.</span></span>
  
## <a name="connection-categories-for-performance-tuning"></a><span data-ttu-id="ba1ad-123">Категории соединений для настройки производительности</span><span class="sxs-lookup"><span data-stu-id="ba1ad-123">Connection categories for performance tuning</span></span>

<span data-ttu-id="ba1ad-p102">Соединения между сервером и пользователем могут относится к трем основным компонентам. Учитывайте их при создании страниц SharePoint Online, чтобы знать время загрузки.</span><span class="sxs-lookup"><span data-stu-id="ba1ad-p102">You can categorize the connections between the server and the user into three main components. Consider these when designing SharePoint Online pages for insight into load times.</span></span>
  
- <span data-ttu-id="ba1ad-126">**Сервер** Серверы, что Майкрософт размещается в центрах обработки данных.</span><span class="sxs-lookup"><span data-stu-id="ba1ad-126">**Server** The servers that Microsoft hosts in datacenters.</span></span>
    
- <span data-ttu-id="ba1ad-127">**Сеть** Microsoft network, Интернета и локальной сети между центра обработки данных и вашим пользователям.</span><span class="sxs-lookup"><span data-stu-id="ba1ad-127">**Network** The Microsoft network, the Internet, and your on-premises network between the datacenter and your users.</span></span>
    
- <span data-ttu-id="ba1ad-128">**Браузер** Где загрузки страницы.</span><span class="sxs-lookup"><span data-stu-id="ba1ad-128">**Browser** Where the page is loaded.</span></span>
    
<span data-ttu-id="ba1ad-p103">С этими тремя соединениями связаны пять наиболее частых причин, которые приводят к 95 % случаев медленной загрузке страниц. В данной статье рассматривается каждая из этих причин:</span><span class="sxs-lookup"><span data-stu-id="ba1ad-p103">Within these three connections there are typically five reasons that cause 95% of slow pages. Each of these reasons is discussed in this article:</span></span>
  
- <span data-ttu-id="ba1ad-131">проблемы навигации;</span><span class="sxs-lookup"><span data-stu-id="ba1ad-131">Navigation issues</span></span>
    
- <span data-ttu-id="ba1ad-132">свертывание контента;</span><span class="sxs-lookup"><span data-stu-id="ba1ad-132">Content roll up</span></span>
    
- <span data-ttu-id="ba1ad-133">большие файлы;</span><span class="sxs-lookup"><span data-stu-id="ba1ad-133">Large files</span></span>
    
- <span data-ttu-id="ba1ad-134">большое количество запросов на сервер;</span><span class="sxs-lookup"><span data-stu-id="ba1ad-134">Many requests to the server</span></span>
    
- <span data-ttu-id="ba1ad-135">обработка веб-частей.</span><span class="sxs-lookup"><span data-stu-id="ba1ad-135">Web Part processing</span></span>
    
### <a name="server-connection"></a><span data-ttu-id="ba1ad-136">Соединение серверов</span><span class="sxs-lookup"><span data-stu-id="ba1ad-136">Server connection</span></span>

<span data-ttu-id="ba1ad-137">Большая часть проблем, влияющих на производительность с локальными системами SharePoint, распространяется и на SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="ba1ad-137">Many of the issues that affect performance with SharePoint on-premises also apply to SharePoint Online.</span></span>
  
<span data-ttu-id="ba1ad-p104">Как и ожидалось, вы имеете гораздо больше возможностей для управления работой серверов при использовании локальной среды SharePoint. Ситуация, когда вы используете SharePoint Online, немного отличается. Чем больше работы вы поручаете серверу, тем больше времени требуется для обработки страницы. В этом плане самые большие трудности с SharePoint возникают при обработке сложных страниц с несколькими веб-частями.</span><span class="sxs-lookup"><span data-stu-id="ba1ad-p104">As you would expect, you have far more control over how servers perform with on-premises SharePoint. With SharePoint Online things are a little different. The more work you make a server do, the longer it takes to render a page. With SharePoint, the biggest culprit in this respect are complex pages with multiple web parts.</span></span>
  
<span data-ttu-id="ba1ad-142">SharePoint Server в локальной</span><span class="sxs-lookup"><span data-stu-id="ba1ad-142">SharePoint Server on-premises</span></span>
  
![Снимок экрана: локальный сервер](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
<span data-ttu-id="ba1ad-144">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ba1ad-144">SharePoint Online</span></span>
  
![Снимок экрана: сервер в сети](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
<span data-ttu-id="ba1ad-p105">Что касается SharePoint Online, то фактически некоторые запросы страниц могут вызвать несколько серверов. Для отдельного запроса вы бы получили матрицу запросов между серверами. Эти взаимодействия требуют значительных затрат с точки зрения загрузки страницы и приводят к медлительности.</span><span class="sxs-lookup"><span data-stu-id="ba1ad-p105">With SharePoint Online, certain page requests may actually end up calling multiple servers. You could end up with a matrix of requests between servers for an individual request. These interactions are expensive from a page load perspective and will make things slow.</span></span>
  
<span data-ttu-id="ba1ad-149">Примеры таких взаимодействий между серверами:</span><span class="sxs-lookup"><span data-stu-id="ba1ad-149">Examples of these server to server interactions are:</span></span>
  
- <span data-ttu-id="ba1ad-150">Интернет и серверы SQL.</span><span class="sxs-lookup"><span data-stu-id="ba1ad-150">Web to SQL Servers</span></span>
    
- <span data-ttu-id="ba1ad-151">Интернет и серверы приложений.</span><span class="sxs-lookup"><span data-stu-id="ba1ad-151">Web to application servers</span></span>
    
<span data-ttu-id="ba1ad-p106">Другая причина замедления взаимодействия с серверами — промахи кэша. В отличие от локальных систем SharePoint, есть небольшой шанс, что вы попадете на предыдущую посещенную страницу этого же сервера. Это приводит к устареванию объектов в кэше.</span><span class="sxs-lookup"><span data-stu-id="ba1ad-p106">The other thing that can slow down server interactions is cache misses. Unlike on-premises SharePoint, there is a very slim chance that you will hit the same server for a page that you have visited previously; this makes object caching obsolete.</span></span>
  
### <a name="network-connection"></a><span data-ttu-id="ba1ad-154">Сетевое подключение</span><span class="sxs-lookup"><span data-stu-id="ba1ad-154">Network connection</span></span>

<span data-ttu-id="ba1ad-p107">С помощью локального развертывания SharePoint, не использовать глобальной сети могут использовать высокоскоростное подключение между центра обработки данных и конечных пользователей. Как правило обстоятельства упрощает управление с точки зрения сети.</span><span class="sxs-lookup"><span data-stu-id="ba1ad-p107">With on-premises SharePoint that doesn't make use of a WAN, you may use a high-speed connection between datacenter and end-users. Generally, things are easy to manage from a network perspective.</span></span>
  
<span data-ttu-id="ba1ad-157">Что касается SharePoint Online, то необходимо рассмотреть еще несколько факторов. Например:</span><span class="sxs-lookup"><span data-stu-id="ba1ad-157">With SharePoint Online, there are a few more factors to consider; for example:</span></span>
  
- <span data-ttu-id="ba1ad-158">сеть Майкрософт;</span><span class="sxs-lookup"><span data-stu-id="ba1ad-158">The Microsoft network</span></span>
    
- <span data-ttu-id="ba1ad-159">Интернет;</span><span class="sxs-lookup"><span data-stu-id="ba1ad-159">The Internet</span></span>
    
- <span data-ttu-id="ba1ad-160">поставщик услуг Интернета.</span><span class="sxs-lookup"><span data-stu-id="ba1ad-160">The ISP</span></span>
    
<span data-ttu-id="ba1ad-161">Независимо от того, какая версия SharePoint (и какая сеть) используется, чаще всего причины занятости сети заключаются в следующем:</span><span class="sxs-lookup"><span data-stu-id="ba1ad-161">Regardless of which version of SharePoint (and which network) you are using, things that will typically cause the network to be busy include:</span></span>
  
- <span data-ttu-id="ba1ad-162">высокая полезная нагрузка;</span><span class="sxs-lookup"><span data-stu-id="ba1ad-162">Large payload</span></span>
    
- <span data-ttu-id="ba1ad-163">большое количество файлов;</span><span class="sxs-lookup"><span data-stu-id="ba1ad-163">Many files</span></span>
    
- <span data-ttu-id="ba1ad-164">большое физическое расстояние до сервера.</span><span class="sxs-lookup"><span data-stu-id="ba1ad-164">Large physical distance to the server</span></span>
    
<span data-ttu-id="ba1ad-p108">Один компонент, который можно использовать в SharePoint Online — это CDN Майкрософт (сети доставки содержимого). CDN по сути является коллекцией распределенных серверов, развернутых для нескольких центров обработки данных. С CDN контент на страницах могут размещаться на сервере закрыть для клиента, даже если клиент далеко от отправляющего сервера SharePoint. Корпорация Майкрософт будет использовать подробнее в будущем для хранения локальной экземпляры страниц, которые не могут настраивать, например SharePoint Online домашней странице администрирования. Дополнительные сведения о CDN можно [сети доставки содержимого](https://docs.microsoft.com/en-us/office365/enterprise/content-delivery-networks).</span><span class="sxs-lookup"><span data-stu-id="ba1ad-p108">One feature that you can leverage in SharePoint Online is the Microsoft CDN (Content Delivery Network). A CDN is basically a distributed collection of servers deployed across multiple datacenters. With a CDN, content on pages can be hosted on a server close to the client even if the client is far away from the originating SharePoint Server. Microsoft will be using this more in the future to store local instances of pages which cannot be customized, for example the SharePoint Online admin home page. For more information about CDNs, see [Content delivery networks](https://docs.microsoft.com/en-us/office365/enterprise/content-delivery-networks).</span></span>
  
<span data-ttu-id="ba1ad-p109">То, что вам необходимо знать, но на что вы не можете повлиять — это скорость соединения вашего поставщика Интернета. Простой инструмент проверки скорости расскажет вам о скорости соединения.</span><span class="sxs-lookup"><span data-stu-id="ba1ad-p109">Something that you need to be aware of but may not be able to do much about is the connection speed of your ISP. A simple speed test tool will tell you the connection speed.</span></span>
  
### <a name="browser-connection"></a><span data-ttu-id="ba1ad-172">Подключение в браузере</span><span class="sxs-lookup"><span data-stu-id="ba1ad-172">Browser connection</span></span>

<span data-ttu-id="ba1ad-173">Существует несколько факторов, которые следует учитывать при оценке производительности веб-браузеров.</span><span class="sxs-lookup"><span data-stu-id="ba1ad-173">There are a few factors to consider with web browsers from a performance perspective.</span></span>
  
<span data-ttu-id="ba1ad-p110">Посетив сложные страницы повлияет на производительность. Большинством браузеров иметь только небольшой кэша (около 90 МБ), при среднего веб-страницы обычно составляет около 1.6 МБ. Не требует времени на получение используется.</span><span class="sxs-lookup"><span data-stu-id="ba1ad-p110">Visiting complex pages will affect performance. Most browsers only have a small cache (around 90MB), while the average web page is typically around 1.6MB. This doesn't take long to get used up.</span></span>
  
<span data-ttu-id="ba1ad-p111">Пропускная способность может также приведет к возникновению проблем. Например если пользователь видеозаписей в сеансе, это отразится на производительности страницы SharePoint. Пока вы не можете запретить пользователям потоковой передачи мультимедиа, можно управлять того, который будет загружать страницы для пользователей.</span><span class="sxs-lookup"><span data-stu-id="ba1ad-p111">Bandwidth may also be an issue. For example, if a user is watching videos in another session, this will affect the performance of your SharePoint page. While you can't prevent users from streaming media, you can control the way a page will load for users.</span></span>
  
<span data-ttu-id="ba1ad-180">Изучите следующие статьи для различных способов настройки SharePoint Online страницы и другие рекомендации для достижения оптимальной производительности.</span><span class="sxs-lookup"><span data-stu-id="ba1ad-180">Check out the following articles for different SharePoint Online page customization techniques and other best practices to help you achieve optimal performance.</span></span>
  
- [<span data-ttu-id="ba1ad-181">Параметры навигации для SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ba1ad-181">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="ba1ad-182">Использование средства диагностики страницы для SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ba1ad-182">Use the Page Diagnostics tool for SharePoint Online</span></span>](page-diagnostics-for-spo.md)
    
- [<span data-ttu-id="ba1ad-183">Оптимизация изображений для SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ba1ad-183">Image optimization for SharePoint Online</span></span>](image-optimization-for-sharepoint-online.md)
    
- [<span data-ttu-id="ba1ad-184">Задержка при загрузке изображений и JavaScript-файлов в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ba1ad-184">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [<span data-ttu-id="ba1ad-185">Минификация и объединение в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ba1ad-185">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="ba1ad-186">Использование сетей доставки содержимого</span><span class="sxs-lookup"><span data-stu-id="ba1ad-186">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="ba1ad-187">С помощью веб-части поиска содержимого вместо веб-части запроса содержимого для повышения производительности в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ba1ad-187">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [<span data-ttu-id="ba1ad-188">Емкость планирования и нагрузочного тестирования SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ba1ad-188">Capacity planning and load testing SharePoint Online</span></span>](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [<span data-ttu-id="ba1ad-189">Диагностика проблем производительности в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ba1ad-189">Diagnosing performance issues with SharePoint Online</span></span>](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [<span data-ttu-id="ba1ad-190">Использование кэша объектов в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ba1ad-190">Using the object cache with SharePoint Online</span></span>](using-the-object-cache-with-sharepoint-online.md)
    
- [<span data-ttu-id="ba1ad-191">Инструкции: как избежать регулирования нагрузки или блокировки в SharePoint Online?</span><span class="sxs-lookup"><span data-stu-id="ba1ad-191">How to: Avoid getting throttled or blocked in SharePoint Online</span></span>](https://msdn.microsoft.com/en-us/library/office/dn889829.aspx)
    

