---
title: Использование кэша объектов в SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 38bc9c14-3826-449c-beb6-b1003bcbeaaf
description: В этой статье объясняется разница между с помощью кэша объектов в SharePoint Server 2013 в локальной и SharePoint Online.
ms.openlocfilehash: 8aa505645bb5f39c65684412ddebbd2b02baa13f
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542458"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a><span data-ttu-id="d02cb-103">Использование кэша объектов в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="d02cb-103">Using the object cache with SharePoint Online</span></span>

<span data-ttu-id="d02cb-104">В этой статье объясняется разница между с помощью кэша объектов в SharePoint Server 2013 в локальной и SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="d02cb-104">This article explains the difference between using the object cache in SharePoint Server 2013 on-premises and SharePoint Online.</span></span>
  
<span data-ttu-id="d02cb-p101">Использовать кэш объектов в развертывании SharePoint Online крайне нежелательно. Любая зависимость от кэша объектов в SharePoint Online снизит надежность вашей страницы.</span><span class="sxs-lookup"><span data-stu-id="d02cb-p101">There is significant negative impact of relying on the object cache in SharePoint Online deployment. Any dependency on object cache in SharePoint Online will reduce the reliability of your page.</span></span> 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a><span data-ttu-id="d02cb-107">Как работает кэша объектов SharePoint Online и SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="d02cb-107">How the SharePoint Online and SharePoint Server 2013 object cache works</span></span>

<span data-ttu-id="d02cb-p102">Когда SharePoint Server 2013 размещенных в локальной, клиент имеет закрытый интерфейсных веб-серверов, на которых размещается кэша объектов. Это означает, что кэш выделенным для одного клиента и ограничивается только объем памяти, выделенный для кэша объектов и доступные. Поскольку только один клиент в сценарии локального интерфейсных веб-серверов обычно у пользователей и запросы на одном веб-сайты и снова. Это означает, что кэш получает полное быстро и остается полный список результатов запроса и объектов SharePoint, которые запрашивают пользователей на регулярной основе.</span><span class="sxs-lookup"><span data-stu-id="d02cb-p102">When SharePoint Server 2013 is hosted on-premises, the customer has private front-end web servers that host the object cache. This means the cache is dedicated to one customer and is only limited by how much memory is available and allocated to the object cache. Because only one customer is served in the on-premises scenario the front-end web servers typically have users making requests to the same sites over and over. This means that the cache gets full quickly and remains full of the list query results and SharePoint objects that your users are requesting on a regular basis.</span></span>
  
![Показывает трафик и нагрузку на локальные веб-серверы переднего плана](media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
<span data-ttu-id="d02cb-p103">В результате, когда пользователь посещает страницу во второй раз, время загрузки страницы сокращается. После как минимум четырех загрузок одной и той же страницы она кэшируется на всех интерфейсных веб-серверах.</span><span class="sxs-lookup"><span data-stu-id="d02cb-p103">As a result, the second time a user visits a page, the page load time improves. After a minimum of four loads of the same page, the page is cached on all of the front-end web servers.</span></span>
  
<span data-ttu-id="d02cb-p104">С другой стороны в SharePoint Online существует множество дополнительных серверов, но также несколько дополнительных сайтов. Каждому пользователю могут подключаться к другой интерфейсный веб-сервер, не имеющим кэш заполняется. Или, возможно получение заполнение кэша для сервера, но следующего пользователя, интерфейсный веб-сервер запрашивает страницу с другого сайта. Или даже в том случае, если Далее пользователь запрашивает эту же страницу на их предыдущей посетить, они являются со сбалансированной нагрузкой для различных интерфейсного веб-сервера, не имеющим этой страницы в кэше. В этом последнем случае кэширование не помогут пользователям вообще.</span><span class="sxs-lookup"><span data-stu-id="d02cb-p104">In contrast, in SharePoint Online there are many more servers but also many more sites. Each user may connect to a different front-end web server that doesn't have the cache populated. Or, perhaps the cache does get populated for a server, but the the next user to that front-end web server requests a page from a different site. Or, even if the next user requests the same page as on their previous visit, they are load-balanced to a different front-end web server that doesn't have that page in its cache. In this last case, caching doesn't help the users at all.</span></span>
  
<span data-ttu-id="d02cb-p105">На следующем рисунке каждая точка представляет страницу, которую запросил пользователь, и место, где она кэширована. Различные цвета представляют различных пользователей, образуя схему совместного использования инфраструктуры программного обеспечения как услуги.</span><span class="sxs-lookup"><span data-stu-id="d02cb-p105">In the following figure, each dot represents a page that a user is requesting and where it cached. Different colors represent different customers making shared use of the SaaS infrastructure.</span></span>
  
![Показывает результаты кэширования объектов в SharePoint Online](media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
<span data-ttu-id="d02cb-p106">Как видно из диаграммы, тонкий вероятность любого пользователя попадание на сервер с кэшированной версии своих страниц. Кроме того из-за большой пропускной способности и фактов, что серверы совместно используемые количество сайтов, кэш не последний срок с момента только слишком мало места для кэширования.</span><span class="sxs-lookup"><span data-stu-id="d02cb-p106">As you can see from the diagram, the chances of any given user hitting a server with the cached version of their page are slim. Also, due to the large throughput and fact that the servers are shared between many sites, the cache doesn't last long since there is only so much space for caching available.</span></span>
  
<span data-ttu-id="d02cb-125">Поэтому полагаться на то, что пользователи получат кэшированные объекты, — неэффективный способ оптимизировать работу пользователя и время загрузки страницы в SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="d02cb-125">For all of these reasons, relying on users getting cached objects is not an effective way to ensure a quality user experience and page load times in SharePoint Online.</span></span>
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a><span data-ttu-id="d02cb-126">Тогда что делать, если невозможно положиться на кэш объектов для улучшения производительности в SharePoint Online?</span><span class="sxs-lookup"><span data-stu-id="d02cb-126">If we can't rely on the object cache to improve performance in SharePoint Online, what do we use instead?</span></span>

<span data-ttu-id="d02cb-p107">Так как в SharePoint Online не следует полагаться на кэширование, вы должны оценить альтернативные подходы проектирования для настроек SharePoint, которые используют кэш объектов. То есть, чтобы обеспечить для пользователей хорошие результаты, используйте методы борьбы с проблемами производительности, которые не зависят от кэширования объектов. Они описаны в других статьях этой серии и включают:</span><span class="sxs-lookup"><span data-stu-id="d02cb-p107">Since you shouldn't rely on caching in SharePoint Online, you should evaluate alternative design approaches for SharePoint customizations that use the object cache. This means using approaches for performance issues which do not rely on the object caching in order to produce good results for users. This is described in some of the other articles in this series and include:</span></span>
  
- [<span data-ttu-id="d02cb-130">Параметры навигации для SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="d02cb-130">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="d02cb-131">Минификация и объединение в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="d02cb-131">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="d02cb-132">Использование сетей доставки содержимого</span><span class="sxs-lookup"><span data-stu-id="d02cb-132">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="d02cb-133">Задержка при загрузке изображений и JavaScript-файлов в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="d02cb-133">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    

