---
title: С помощью веб-части поиска содержимого вместо веб-части запроса содержимого для повышения производительности в SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: e8ce6b72-745b-464a-85c7-cbf6eb53391b
description: В этой статье описывается, как для повышения производительности путем замены контента веб-части запроса содержимого веб-части поиска в SharePoint Server 2013 и SharePoint Online.
ms.openlocfilehash: f86a4b75c4bf75ebaa99924411d017c7eb7b6760
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542623"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a><span data-ttu-id="b61d1-103">С помощью веб-части поиска содержимого вместо веб-части запроса содержимого для повышения производительности в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="b61d1-103">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>

<span data-ttu-id="b61d1-104">В этой статье описывается, как для повышения производительности путем замены контента веб-части запроса содержимого веб-части поиска в SharePoint Server 2013 и SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="b61d1-104">This article describes how to increase performance by replacing the Content Query Web Part with the Content Search Web Part in SharePoint Server 2013 and SharePoint Online.</span></span>
  
<span data-ttu-id="b61d1-p101">Одно из наиболее эффективные новые возможности SharePoint Server 2013 и SharePoint Online — часть содержимого Web поиска (CSWP). Эта веб-часть использует индекс поиска для быстрого извлечения результатов, которые отображаются для пользователя. Используйте вместо содержимого запроса веб части (CQWP) на страницах контента веб-части поиска для повышения производительности для пользователей.</span><span class="sxs-lookup"><span data-stu-id="b61d1-p101">One of the most powerful new features of SharePoint Server 2013 and SharePoint Online is the Content Search Web Part (CSWP). This Web Part uses the search index to quickly retrieve results which are shown to the user. Use the Content Search Web Part instead of the Content Query Web Part (CQWP) in your pages to improve performance for your users.</span></span>
  
<span data-ttu-id="b61d1-p102">Использование контента веб-части поиска контента веб-часть запроса почти всегда приведет к значительно повысить производительность загрузки страницы в SharePoint Online. Существует немного дополнительной настройки для получения правом запроса, но преимущества повышения производительности и happier пользователей.</span><span class="sxs-lookup"><span data-stu-id="b61d1-p102">Using a Content Search Web Part over a Content Query Web Part will almost always result in significantly better page load performance on SharePoint Online. There is a little additional configuration to get the right query, but the rewards are improved performance and happier users.</span></span>
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a><span data-ttu-id="b61d1-110">Сравнение рост производительности, которые можно получить с помощью веб-части поиска контента, а не веб-части запроса содержимого</span><span class="sxs-lookup"><span data-stu-id="b61d1-110">Comparing the performance gain you get from using Content Search Web Part instead of Content Query Web Part</span></span>

<span data-ttu-id="b61d1-p103">В следующих примерах показано относительное производительность, может возникнуть при использовании контента веб-части поиска вместо контента веб-части запроса. Влияние более очевидны со структурой сложных сайта и широчайший запросах содержимого.</span><span class="sxs-lookup"><span data-stu-id="b61d1-p103">The following examples show the relative performance gains you may receive when you use a Content Search Web Part instead of a Content Query Web Part. The effects are more obvious with a complex site structure and very broad content queries.</span></span>
  
<span data-ttu-id="b61d1-113">В этом примере сайт имеет следующие характеристики:</span><span class="sxs-lookup"><span data-stu-id="b61d1-113">This example site has the following characteristics:</span></span>
  
- <span data-ttu-id="b61d1-114">8 уровней дочерних сайтов.</span><span class="sxs-lookup"><span data-stu-id="b61d1-114">8 levels of subsites.</span></span>
    
- <span data-ttu-id="b61d1-115">Список с помощью настраиваемого «Фрукты» тип контента.</span><span class="sxs-lookup"><span data-stu-id="b61d1-115">Lists using a custom "fruit" content type.</span></span>
    
- <span data-ttu-id="b61d1-116">В веб-части запроса содержимого широкий, возвращает все элементы с типом контента «Фрукты».</span><span class="sxs-lookup"><span data-stu-id="b61d1-116">In the Web Part, the content query is broad, returning all items with the content type of "fruit".</span></span>
    
- <span data-ttu-id="b61d1-p104">В примере используется только 50 элементов по 8 сайтам. Результаты будут еще более произносится для сайтов с другое содержимое.</span><span class="sxs-lookup"><span data-stu-id="b61d1-p104">The example only uses 50 items across the 8 sites. The effects will be even more pronounced for sites with more content.</span></span>
    
<span data-ttu-id="b61d1-119">Ниже показан пример результатов веб-части запроса содержимого.</span><span class="sxs-lookup"><span data-stu-id="b61d1-119">Here is a screen shot of the results of the Content Query Web Part.</span></span>
  
![Рисунок: запрос контента для веб-части](media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
<span data-ttu-id="b61d1-p105">В Internet Explorer используйте вкладку **сети** средства разработчика F12 для просмотра сведений для заголовка ответа. На следующем снимке экрана 924 миллисекундах имеет значение **SPRequestDuration** для загрузки этой страницы.</span><span class="sxs-lookup"><span data-stu-id="b61d1-p105">In Internet Explorer, use the **Network** tab of the F12 developer tools to look at the details for the response header. In the following screen shot, the value for the **SPRequestDuration** for this page load is 924 milliseconds.</span></span> 
  
![Снимок экрана со значением длительности запроса (924)](media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 <span data-ttu-id="b61d1-p106">**SPRequestDuration** указывает объем работ, который выполняется на сервере для подготовки страницы. Переключение содержимого по веб-части запроса содержимого с веб-частей поиска значительно сокращает время, необходимое для отображения страницы. В то же время страница с эквивалентный контента поиска веб-части, возвращая такое же число результатов имеет значение **SPRequestDuration** 106 миллисекунд, как показано на этом снимке экрана:</span><span class="sxs-lookup"><span data-stu-id="b61d1-p106">**SPRequestDuration** indicates the amount of work that is done on the server to prepare the page. Switching Content by Query Web Parts with Content by Search Web Parts dramatically reduces the time it takes to render the page. By contrast, a page with an equivalent Content Search Web Part, returning the same number of results has an **SPRequestDuration** value of 106 milliseconds as shown in this screen shot:</span></span> 
  
![Снимок экрана со значением длительности запроса (106)](media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a><span data-ttu-id="b61d1-128">Добавление веб-части поиска контента в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="b61d1-128">Adding a Content Search Web Part in SharePoint Online</span></span>

<span data-ttu-id="b61d1-p107">Добавление контента веб-части поиска является очень похоже на регулярные контента веб-части запроса. В разделе *«Добавление контента веб-части поиска»* в разделе [Configure контента веб-части поиска в SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span><span class="sxs-lookup"><span data-stu-id="b61d1-p107">Adding a Content Search Web Part is very similar to a regular Content Query Web Part. See the section  *"Add a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a><span data-ttu-id="b61d1-131">Создание в правом поисковый запрос для контента веб-части поиска</span><span class="sxs-lookup"><span data-stu-id="b61d1-131">Creating the right search query for your Content Search Web Part</span></span>

<span data-ttu-id="b61d1-p108">После добавления контента веб-части поиска можно уточнить поиск и возвращают требуемые элементы. Подробные инструкции о том, как это сделать см раздел *«Отображение содержимого, настроив расширенный запрос в контента веб-части поиска»* в статье [Настройка веб-части поиска контента в SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span><span class="sxs-lookup"><span data-stu-id="b61d1-p108">Once you have added a Content Search Web Part, you can refine the search and return the items you want. For detailed instructions on how to do this, see the section,  *"Display content by configuring an advanced query in a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="query-building-and-testing-tool"></a><span data-ttu-id="b61d1-134">Запрос созданию и тестированию средства</span><span class="sxs-lookup"><span data-stu-id="b61d1-134">Query building and testing tool</span></span>

<span data-ttu-id="b61d1-135">Средства для построения и тестирования сложные запросы в разделе [Средства запросов поиска](https://sp2013searchtool.codeplex.com/) на сайте Codeplex.</span><span class="sxs-lookup"><span data-stu-id="b61d1-135">For a tool to build and test complex queries, see the [Search Query Tool](https://sp2013searchtool.codeplex.com/) on Codeplex.</span></span> 
  

