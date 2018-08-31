---
title: Параметры навигации для SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/27/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: В этой статье описывается, как для улучшения время загрузки страницы для SharePoint Online с использованием управляемой навигации и Навигация на основе поиска в классическом публикации.
ms.openlocfilehash: 6b2ee613d0cc6a6df92eb9b53374087a0ac2e5b7
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542572"
---
# <a name="navigation-options-for-sharepoint-online"></a><span data-ttu-id="ab850-103">Параметры навигации для SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ab850-103">Navigation options for SharePoint Online</span></span>

<span data-ttu-id="ab850-104">В этой статье описывается, как для улучшения время загрузки страницы для SharePoint Online с использованием управляемой навигации и Навигация на основе поиска в классическом публикации.</span><span class="sxs-lookup"><span data-stu-id="ab850-104">This article describes how to improve page load times for SharePoint Online by using managed navigation or search-driven navigation in Classic publishing.</span></span>
  
<span data-ttu-id="ab850-105">SharePoint Online с поддержкой классический публикацией имеет две области переходов; Глобальных и текущих переходов.</span><span class="sxs-lookup"><span data-stu-id="ab850-105">SharePoint Online with classic publishing enabled has two navigation areas; Global Navigation and Current Navigation.</span></span>
  
<span data-ttu-id="ab850-106">Глобальной навигации — меню верхней панели навигации, когда текущая структура навигации равно со стороны или навигации влево и вправо в контексте зависящие от языка конфигурации и использовать главную страницу.</span><span class="sxs-lookup"><span data-stu-id="ab850-106">Global navigation is the top navigation menu while Current Navigation is the side or in-context left/right navigation dependent on the language configuration and master page utilized.</span></span>
  
<span data-ttu-id="ab850-107">Навигации может отрицательно сказаться производительности для всей портала часто настроены для использования в масштабе портала и таковым является важным элементом любого сайта SharePoint.</span><span class="sxs-lookup"><span data-stu-id="ab850-107">Navigation can negatively impact performance for the entire Portal as it is often configured for portal-wide use and as such is an important element of any SharePoint site.</span></span>
  
<span data-ttu-id="ab850-108">Структуры навигации не параметр рекомендуемые навигации в SharePoint Online, как он был разработан для On-premise топология с фильтрация по ролям безопасности и вызывает чрезмерной звонки и влияет на производительность при использовании этой структуры.</span><span class="sxs-lookup"><span data-stu-id="ab850-108">Structural navigation is not the recommended navigation option in SharePoint Online as it was designed for an On-premise topology with security trimming and this design causes excessive server calls and impacts performance when it is used.</span></span>
  
<span data-ttu-id="ab850-p101">Об изменении структуры вследствие внедрения сайтов SharePoint современных где современных имеет иерархии упрощенный плоская сайта. Это упрощенный навигации с иерархией упрощенный, который не актуальна проблем производительности, связанных с навигации.</span><span class="sxs-lookup"><span data-stu-id="ab850-p101">That design has changed with the introduction of Modern SharePoint sites where Modern has a simplified flattened site hierarchy. This has simplified navigation with a simplified hierarchy that has eliminated performance issues related to navigation.</span></span>
  
<span data-ttu-id="ab850-p102">Существует два варианта ожидания введите переходов в SharePoint, а также третий, настраиваемые подход на основе поиска. Кроме того четвертый и довольно популярные вариант является для создания настраиваемого поставщика навигации. Руководство по поставщика навигации Custom просмотрите [решения навигации для порталов SharePoint Online](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/portal-navigation) .</span><span class="sxs-lookup"><span data-stu-id="ab850-p102">There are two main out-of-the-box navigation options in SharePoint as well as a third, custom, search-driven approach. Alternatively, a fourth and fairly popular option is to build a Custom Navigation Provider. Please review [Navigation solutions for SharePoint Online portals](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/portal-navigation) for guidance on a Custom navigation provider.</span></span> 
  
<span data-ttu-id="ab850-114">Каждый параметр имеет свои преимущества и недостатки, как описано в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="ab850-114">Each option has pros and cons as outlined in the following table.</span></span>
  
|<span data-ttu-id="ab850-115">**Структурная навигация**</span><span class="sxs-lookup"><span data-stu-id="ab850-115">**Structural navigation**</span></span>|<span data-ttu-id="ab850-116">**Управляемая навигация**</span><span class="sxs-lookup"><span data-stu-id="ab850-116">**Managed navigation**</span></span>|<span data-ttu-id="ab850-117">**Навигация на основе поиска**</span><span class="sxs-lookup"><span data-stu-id="ab850-117">**Search-driven navigation**</span></span>||<span data-ttu-id="ab850-118">**Поставщик пользовательских переходов**</span><span class="sxs-lookup"><span data-stu-id="ab850-118">**Custom Navigation Provider**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
| <span data-ttu-id="ab850-119">Преимущества:</span><span class="sxs-lookup"><span data-stu-id="ab850-119">Pros:</span></span>  <br/>  <span data-ttu-id="ab850-120">простота настройки;</span><span class="sxs-lookup"><span data-stu-id="ab850-120">Easy to configure</span></span>  <br/>  <span data-ttu-id="ab850-121">фильтрация по ролям безопасности;</span><span class="sxs-lookup"><span data-stu-id="ab850-121">Security-trimmed</span></span>  <br/>  <span data-ttu-id="ab850-122">автоматическое обновление при добавлении сайтов.</span><span class="sxs-lookup"><span data-stu-id="ab850-122">Automatically updates as sites are added</span></span>  <br/> | <span data-ttu-id="ab850-123">Преимущества:</span><span class="sxs-lookup"><span data-stu-id="ab850-123">Pros:</span></span>  <br/>  <span data-ttu-id="ab850-124">простота поддержки;</span><span class="sxs-lookup"><span data-stu-id="ab850-124">Easy to maintain</span></span>  <br/>  <span data-ttu-id="ab850-125">Рекомендуется использовать параметр</span><span class="sxs-lookup"><span data-stu-id="ab850-125">Recommended option</span></span>  <br/> | <span data-ttu-id="ab850-126">Преимущества:</span><span class="sxs-lookup"><span data-stu-id="ab850-126">Pros:</span></span>  <br/>  <span data-ttu-id="ab850-127">фильтрация по ролям безопасности;</span><span class="sxs-lookup"><span data-stu-id="ab850-127">Security-trimmed</span></span>  <br/>  <span data-ttu-id="ab850-128">автоматическое обновление при добавлении сайтов;</span><span class="sxs-lookup"><span data-stu-id="ab850-128">Automatically updates as sites are added</span></span>  <br/>  <span data-ttu-id="ab850-129">короткое время загрузки и локальное кэширование структуры навигации.</span><span class="sxs-lookup"><span data-stu-id="ab850-129">Fast loading time and locally cached navigation structure</span></span>  <br/> || <span data-ttu-id="ab850-130">Плюсы:</span><span class="sxs-lookup"><span data-stu-id="ab850-130">Pros:</span></span>  <br/>    <br/>  <span data-ttu-id="ab850-131">Широкий выбор аудио- и параметры недоступны</span><span class="sxs-lookup"><span data-stu-id="ab850-131">Wider choice / options available</span></span>  <br/>  <span data-ttu-id="ab850-132">Быстрое загрузки при кэшировании используется правильно</span><span class="sxs-lookup"><span data-stu-id="ab850-132">Fast loading when caching is used correctly</span></span>  <br/> |
| <span data-ttu-id="ab850-133">Недостатки:</span><span class="sxs-lookup"><span data-stu-id="ab850-133">Cons:</span></span>  <br/> <span data-ttu-id="ab850-134">**Не рекомендуется**</span><span class="sxs-lookup"><span data-stu-id="ab850-134">**Not recommended**</span></span> <br/> <span data-ttu-id="ab850-135">**Воздействия на производительность**</span><span class="sxs-lookup"><span data-stu-id="ab850-135">**Impacts performance**</span></span> <br/> | <span data-ttu-id="ab850-136">Недостатки:</span><span class="sxs-lookup"><span data-stu-id="ab850-136">Cons:</span></span>  <br/>  <span data-ttu-id="ab850-137">отсутствие автоматического обновления для отражения структуры сайта.</span><span class="sxs-lookup"><span data-stu-id="ab850-137">Not automatically updated to reflect site structure</span></span>  <br/>  <span data-ttu-id="ab850-138">Воздействия на производительность при включении фильтрации по ролям безопасности</span><span class="sxs-lookup"><span data-stu-id="ab850-138">Impacts performance if security trimming is enabled</span></span>  <br/> | <span data-ttu-id="ab850-139">Недостатки:</span><span class="sxs-lookup"><span data-stu-id="ab850-139">Cons:</span></span>  <br/>  <span data-ttu-id="ab850-140">нет возможности простого упорядочивания сайтов;</span><span class="sxs-lookup"><span data-stu-id="ab850-140">No ability to easily order sites</span></span>  <br/>  <span data-ttu-id="ab850-141">требуется настройка эталонной страницы (необходимы технические навыки).</span><span class="sxs-lookup"><span data-stu-id="ab850-141">Requires customization of the master page (technical skills required)</span></span>  <br/> || <span data-ttu-id="ab850-142">Недостатки:</span><span class="sxs-lookup"><span data-stu-id="ab850-142">Cons:</span></span>  <br/>  <span data-ttu-id="ab850-143">Является обязательным, разработки пользовательских решений</span><span class="sxs-lookup"><span data-stu-id="ab850-143">Custom development is required</span></span>  <br/>  <span data-ttu-id="ab850-144">Внешний источник данных аудио- и необходимости кэша хранятся например Azure</span><span class="sxs-lookup"><span data-stu-id="ab850-144">External data source / cache stored is needed e.g. Azure</span></span>  <br/> |
   
<span data-ttu-id="ab850-p103">Наиболее подходящий вариант для веб-узла будет зависят от требований к сайта и технические возможности. Если готовы, с помощью настраиваемой главной страницы и имеет некоторые возможности в организации, чтобы сохранить изменения, которые могут возникнуть в главную страницу по умолчанию для SharePoint Online, параметр на основе механизмов поиска будут создавать максимальное удобство работы пользователей. Если вы хотите простой промежуточный вариант между ожидания введите структуры навигации и поиска, управляемая Навигация является очень хорошим выбором. Параметр управляемой навигации могут поддерживать через конфигурации, не связанных файлов настройки кода, и это значительно быстрее, чем ожидания введите структуры навигации.</span><span class="sxs-lookup"><span data-stu-id="ab850-p103">The most appropriate option for your site will depend on your site requirements and on your technical capability. If you are comfortable using a custom master page and have some capability in the organization to maintain the changes that may occur in the default master page for SharePoint Online, then the search-driven option will produce the best user experience. If you want a simple middle ground between the out-of-the-box structural navigation and search, then the managed navigation is a very good option. The managed navigation option can be maintained through configuration, does not involve code customization files, and it is significantly faster than the out-of-the-box structural navigation.</span></span>
  
<span data-ttu-id="ab850-p104">Упрощение Общая структура классический портала так же, как современная сортировка, помогает общую производительность и масштаб также. Что означает, что вместо одного семейства веб-сайтов с помощью нескольких сотен и тысяч узлов (дочерние сайты), лучший подход заключается в большое количество семейств с лишь несколько дочерних сайтов (дочерние сайты).</span><span class="sxs-lookup"><span data-stu-id="ab850-p104">Simplifying the overall structure of your Classic Portal much like Modern, helps with overall performance and scale as well. What this means is that instead of having a single Site Collection with hundreds / thousands of sites (subwebs), a better approach is to have many site collections with very few subsites (subwebs).</span></span>
  
<span data-ttu-id="ab850-151">Это обеспечивает дополнительные параметры масштабирования в службе, позволяет избежать помещения все содержимое в один большой базы данных и в конечном счете обеспечивает большую свободу действий для навигации и важнее безопасности.</span><span class="sxs-lookup"><span data-stu-id="ab850-151">This provides additional scaling options in the service, avoids putting all content into one big database and ultimately allows greater flexibility for navigation and more importantly security.</span></span>
  
## <a name="using-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="ab850-152">Использование структурной навигации в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ab850-152">Using structural navigation in SharePoint Online</span></span>

<span data-ttu-id="ab850-p105">Эта функция ожидания введите навигации, используемый по умолчанию и — это самый простой решения, но таким образом имеет компромиссов дорогостоящих производительности. Не требует настройки и не технической пользователя можно также легко добавить элементы, скрыть элементы и управления панели навигации на странице параметры. Это также тем не менее значение true для управляемой навигации, поэтому рекомендуется использовать управляемой навигации в качестве которых может также быть легко управляемых, а также управление.</span><span class="sxs-lookup"><span data-stu-id="ab850-p105">This is the out-of-the-box navigation used by default and is the most straightforward solution but as such has an expensive performance trade-off. It does not require any customization and a non-technical user can also easily add items, hide items, and manage the navigation from the settings page. This is however also true for Managed Navigation so it is recommended to use Managed Navigation as that can also be easily managed and controlled as well.</span></span>
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="ab850-156">Переход на структурную навигацию в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ab850-156">Turning on structural navigation in SharePoint Online</span></span>

<span data-ttu-id="ab850-p106">В качестве демонстрации как производительности в решении стандартных SharePoint Online с помощью структуры навигации и отображать дочерние сайты вариант включен. Ниже снимок экрана, параметры, находящиеся на странице " **Параметры сайта** " \> **навигации**.</span><span class="sxs-lookup"><span data-stu-id="ab850-p106">To illustrate how the performance in a standard SharePoint Online solution with structural navigation and the show subsites option turned on. Below is a screen shot settings found on the page **Site Settings** \> **Navigation**.</span></span>
  
![Снимок экрана: дочерние сайты](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a><span data-ttu-id="ab850-160">Анализ производительности структурной навигации в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ab850-160">Analyzing structural navigation performance in SharePoint Online</span></span>

<span data-ttu-id="ab850-161">Чтобы проанализировать производительность страницы SharePoint, используйте вкладку **Сеть** средств разработчика (F12) в Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="ab850-161">To analyze the performance of a SharePoint page use the **Network** tab of the F12 developer tools in Internet Explorer.</span></span> 
  
![Снимок экрана: вкладка "Сеть", отображенная после вызова средств разработчика (F12)](media/e2aed8af-0843-487a-8b68-4f5260a2685e.png)
  
<span data-ttu-id="ab850-163">На вкладке **Сеть** выберите загруженную страницу .aspx, а затем — вкладку **Сведения**.</span><span class="sxs-lookup"><span data-stu-id="ab850-163">On the **Network** tab, click on the .aspx page that is being loaded and then click on the **Details** tab.</span></span> 
  
![Снимок экрана: вкладка "Сведения"](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)
  
<span data-ttu-id="ab850-165">Щелкните пункт **Заголовки ответов**.</span><span class="sxs-lookup"><span data-stu-id="ab850-165">Click **Response headers**.</span></span>
  
![Снимок экрана: вкладка "Сведения"](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)
  
<span data-ttu-id="ab850-p107">SharePoint возвращает некоторую полезную диагностическую информацию в своих заголовках ответов. Одно из наиболее полезных — значение **SPRequestDuration**, обозначающее время обработки запроса на сервере в миллисекундах.</span><span class="sxs-lookup"><span data-stu-id="ab850-p107">SharePoint returns some useful diagnostic information in its response headers. One of the most useful is **SPRequestDuration** which is the value, in milliseconds, of how long a request took to process on the server.</span></span> 
  
<span data-ttu-id="ab850-p108">В следующем рисунке **показано дочерних сайтов** не установлен для структуры навигации. Это значит, что существует только связь семейства сайтов в глобальной навигации.</span><span class="sxs-lookup"><span data-stu-id="ab850-p108">In the following screen shot **show subsites** is unchecked for the structural navigation. This means that there is only the site collection link in the global navigation:</span></span> 
  
![Снимок экрана: время загрузки как время ответа на запрос](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)
  
<span data-ttu-id="ab850-p109">Клавиша **SPRequestDuration** имеет значение 245 (в миллисекундах). Представляет время, затраченное на возврата запроса. Поскольку существует только один элемент навигации на сайте, это хороший тестирования производительности для SharePoint Online выполнение без толстые навигации. На следующем снимке экрана показано, как добавлять в дочерних сайтов влияет этот ключ.</span><span class="sxs-lookup"><span data-stu-id="ab850-p109">The **SPRequestDuration** key has a value of 245 milliseconds. This represents the time it took to return the request. Since there is only one navigation item on the site, this is a good benchmark for how SharePoint Online performs without heavy navigation. The next screen shot shows how adding in the subsites affects this key.</span></span> 
  
![Снимок экрана: длительность обработки запроса составляет 2502 мс](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)
  
<span data-ttu-id="ab850-177">Добавление дочерних сайтов существенно увеличивает время возврата запроса страницы.</span><span class="sxs-lookup"><span data-stu-id="ab850-177">Adding the subsites has significantly increased the time it takes to return the page request.</span></span>
  
<span data-ttu-id="ab850-178">Преимущества использования регулярного структурированная навигация — можно легко организовать порядке, скрыть сайты, добавление страниц, результатом будет обрезать безопасности, что вы не отклоняться от поддерживаемых главных страниц, используемых в SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="ab850-178">The advantages of using the regular structured navigation is that you can easily organize the order, hide sites, add pages, the results are security-trimmed, and you are not deviating from the supported master pages used in SharePoint Online.</span></span>
  
## <a name="using-managed-navigation-and-managed-metadata-in-sharepoint-online"></a><span data-ttu-id="ab850-179">Использование управляемой навигации и управляемых метаданных в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ab850-179">Using managed navigation and managed metadata in SharePoint Online</span></span>

<span data-ttu-id="ab850-180">Управляемая навигация — другой готовый параметр, который вы можете использовать для воссоздания функциональности, которая аналогична структурной навигации.</span><span class="sxs-lookup"><span data-stu-id="ab850-180">Managed navigation is another out-of-the-box option that you can use to recreate the same sort of functionality as structural navigation.</span></span>
  
<span data-ttu-id="ab850-p110">Преимущества использования управляемых метаданных, что является значительно быстрее для извлечения данных, а не с помощью содержимого по запросу для создания структуры переходов сайта. Хотя это и что намного быстрее нет возможности безопасности обрезки результатов так если у пользователя нет доступа на данном сайте, ссылки по-прежнему будут отображаться, но приведет к сообщение об ошибке.</span><span class="sxs-lookup"><span data-stu-id="ab850-p110">The advantage of using managed metadata is that it is much faster to retrieve the data than using content by query to build the site navigation. Although it is much faster there is no way to security trim the results so if a user doesn't have access to a given site, the link will still show but will lead to an error message.</span></span>
  
 <span data-ttu-id="ab850-183">**Как реализовать управляемую навигацию и результаты**</span><span class="sxs-lookup"><span data-stu-id="ab850-183">**How to implement managed navigation and the results**</span></span>
  
<span data-ttu-id="ab850-184">Существует несколько статей на сайте TechNet о сведения о управляемой навигации, например, в разделе [Обзор управляемой навигации в SharePoint Server 2013](https://go.microsoft.com/fwlink/?LinkId=708689).</span><span class="sxs-lookup"><span data-stu-id="ab850-184">There are several articles on TechNet about the details of managed navigation, for example, see [Overview of managed navigation in SharePoint Server 2013](https://go.microsoft.com/fwlink/?LinkId=708689).</span></span>
  
<span data-ttu-id="ab850-p111">Для реализации управляемой навигации вы должны иметь права администратора банка терминов. С помощью настройки терминов с URL-адресами, которые соответствуют структуре семейства сайта, управляемую навигацию можно использовать для замены структурной навигации. Например:</span><span class="sxs-lookup"><span data-stu-id="ab850-p111">In order to implement managed navigation, you need to have term store administrator permissions. By setting up terms with URLs that match the structure of a site collection, managed navigation can be used to replace structural navigation. For example:</span></span>
  
![Снимок экрана: пример Subsite1](media/4155b4da-ccff-4e2a-92de-7803ac62982b.png)
  
<span data-ttu-id="ab850-189">Следующий пример демонстрирует производительность сложной навигации с использованием управляемой навигации.</span><span class="sxs-lookup"><span data-stu-id="ab850-189">The following example shows the performance of the complex navigation using managed navigation.</span></span>
  
![Снимок экрана: пример SPRequestDuration](media/72257528-0ec6-48b0-85a5-efeb7432db5b.png)
  
<span data-ttu-id="ab850-191">Использование управляемой навигации последовательно повышает производительность по сравнению со структурной навигацией с содержимым по запросу.</span><span class="sxs-lookup"><span data-stu-id="ab850-191">Using managed navigation consistently improves performance compared to the content by query structural navigation approach.</span></span>
  
## <a name="using-search-driven-client-side-scripting"></a><span data-ttu-id="ab850-192">Использование скриптов с навигацией на основе поиска на стороне клиента</span><span class="sxs-lookup"><span data-stu-id="ab850-192">Using Search-driven client-side scripting</span></span>

<span data-ttu-id="ab850-p112">С помощью поиска вы можете выгодно использовать индексы, которые создаются в фоне, используя непрерывный обход контента. Это значит, что громоздких запросов содержимого нет. Результаты поиска извлекаются из индекса поиска, а результаты отфильтровываются по ролям безопасности. Этот подход быстрее, чем использование обычных запросов на содержимое. Использование поиска для структурной навигации позволит значительно повысить скорость загрузки страниц, особенно если на вашем сайте сложная структура. Основное преимущество этого вида навигации над управляемой состоит в том, что вы выигрываете от фильтрации по ролям безопасности.</span><span class="sxs-lookup"><span data-stu-id="ab850-p112">Using search you can leverage the indexes that are built up in the background using continuous crawl. This means there are no heavy content queries. The search results are pulled from the search index and the results are security-trimmed. This is faster than using regular content queries. Using search for structural navigation, especially if you have a complex site structure, will speed up page loading time considerably. The main advantage of this over managed navigation is that you benefit from security trimming.</span></span>
  
<span data-ttu-id="ab850-p113">Этот подход включает в себя создание эталонной страницы и замену коробочного кода навигации пользовательским HTML-кодом. Следуйте этой процедуре, чтобы заменить код навигации в файле seattle.html.</span><span class="sxs-lookup"><span data-stu-id="ab850-p113">This approach involves creating a custom master page and replacing the out-of-the-box navigation code with custom HTML. Follow this procedure to replace the navigation code in the file seattle.html.</span></span>
  
<span data-ttu-id="ab850-201">В этом примере будет откройте файл seattle.html и замените весь элемент **id = «DeltaTopNavigation»** с помощью пользовательского кода HTML.</span><span class="sxs-lookup"><span data-stu-id="ab850-201">In this example, you will open the seattle.html file and replace the whole element **id="DeltaTopNavigation"** with the custom HTML code.</span></span> 
  
 <span data-ttu-id="ab850-202">**Пример: Чтобы заменить коробочный код навигации на эталонной странице:**</span><span class="sxs-lookup"><span data-stu-id="ab850-202">**Example: To replace the out-of-the-box navigation code in a master page**</span></span>
  
1. <span data-ttu-id="ab850-203">Перейдите на страницу **Параметры сайта**.</span><span class="sxs-lookup"><span data-stu-id="ab850-203">Navigate to the **Site Settings** page.</span></span> 
    
2. <span data-ttu-id="ab850-204">Откройте коллекцию эталонных страниц, выбрав пункт **Эталонные страницы**.</span><span class="sxs-lookup"><span data-stu-id="ab850-204">Open the master page gallery by clicking **Master Pages**.</span></span>
    
3. <span data-ttu-id="ab850-205">Отсюда вы можете перейти через библиотеку и скачать файл **seattle.master**.</span><span class="sxs-lookup"><span data-stu-id="ab850-205">From here you can navigate through the library and download the file **seattle.master**.</span></span>
    
4. <span data-ttu-id="ab850-206">Измените код с помощью текстового редактора и удалите фрагмент кода, представленный на следующем снимке экрана.</span><span class="sxs-lookup"><span data-stu-id="ab850-206">Edit the code using a text editor and delete the code block in the following screen shot.</span></span>
    
    ![Снимок экрана: удаление кода DeltaTopNavigation](media/70db2cd2-660d-4e0d-9d5c-a5df331c73b4.png)
  
5. <span data-ttu-id="ab850-208">Удаление кода между \<SharePoint:AjaxDelta id = «DeltaTopNavigation»\> и \<\SharePoint:AjaxDelta\> теги и замените его на следующий фрагмент:</span><span class="sxs-lookup"><span data-stu-id="ab850-208">Remove the code between the \<SharePoint:AjaxDelta id="DeltaTopNavigation"\> and \<\SharePoint:AjaxDelta\> tags and replace it with the following snippet:</span></span>
    
  ```
  <div id="loading">
    <!--Replace with path to loading image.-->
    <div style="background-image: url(''); height: 22px; width: 22px; ">
    </div>
  </div>
  <!-- Main Content-->
  <div id="navContainer" style="display:none">
      <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
          <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
              <span class="menu-item-text" data-bind="text: item.Title">
              </span>
          </a>
          <ul id="menu" data-bind="foreach: $data.children" style="padding-left:20px">
              <li class="static dynamic-children level1">
                  <a class="static dynamic-children menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
                 
                   <!-- ko if: children.length > 0-->
                      <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
                          <span class="menu-item-text" data-bind="text: item.Title">
                          </span>
                      </span>
                  <!-- /ko -->
                  <!-- ko if: children.length == 0-->   
                      <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
                          <span class="menu-item-text" data-bind="text: item.Title">
                          </span>
                      </span>
                  <!-- /ko -->   
                  </a>
                 
                  <!-- ko if: children.length > 0-->                                                       
                  <ul id="menu"  data-bind="foreach: children;" class="dynamic  level2" >
                      <li class="dynamic level2">
                          <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline  ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
           
            <!-- ko if: children.length > 0-->
            <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
             <span class="menu-item-text" data-bind="text: item.Title">
             </span>
            </span>
             <!-- /ko -->
            <!-- ko if: children.length == 0-->
            <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
             <span class="menu-item-text" data-bind="text: item.Title">
             </span>
            </span>                 
            <!-- /ko -->   
                          </a>
            <!-- ko if: children.length > 0-->
           <ul id="menu" data-bind="foreach: children;" class="dynamic level3" >
            <li class="dynamic level3">
             <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
              <span class="menu-item-text" data-bind="text: item.Title">
              </span>
             </a>
            </li>
           </ul>
             <!-- /ko -->
                      </li>
                  </ul>
                  <!-- /ko -->
              </li>
          </ul>
      </div>
  </div>
  ```

6. <span data-ttu-id="ab850-p114">Замените URL-адрес в загрузке тега привязки в начале со ссылкой на изображение загрузки в семействе веб-сайтов "изображение". После внесения изменений, переименуйте файл и отправить его в коллекции главных страниц. Создает новый файл .master.</span><span class="sxs-lookup"><span data-stu-id="ab850-p114">Replace the URL in the loading image anchor tag at the beginning, with a link to a loading image in your site collection. After you have made the changes, rename the file and then upload it to the master page gallery. This generates a new .master file.</span></span>
    
7. <span data-ttu-id="ab850-p115">В этом HTML — это базовая разметка, которая будет устанавливаться результаты поиска, возвращаемые из кода JavaScript. Нужно изменить следующий код, чтобы изменить значение для `var root = "site collection URL"` как показано в следующем фрагменте:</span><span class="sxs-lookup"><span data-stu-id="ab850-p115">This HTML is the basic markup that will be populated by the search results returned from JavaScript code. You will need to edit the following code to change the value for the  `var root = "site collection URL"` as demonstrated in the following snippet:</span></span> 
    
  ```
  var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
  ```

    <span data-ttu-id="ab850-214">Полный JavaScript-файл выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="ab850-214">The entire JavaScript file is as follows:</span></span>
    
  ```
  //Models and Namespaces
  var SPOCustom = SPOCustom || {};
  SPOCustom.Models = SPOCustom.Models || {}
  SPOCustom.Models.NavigationNode = function () {
      this.Url = ko.observable("");
      this.Title = ko.observable("");
      this.Parent = ko.observable("");
  };
  var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
  var baseUrl = root + "/_api/search/query?querytext=";
  var query = baseUrl + "'contentClass=\"STS_Web\"+path:" + root + "'&amp;trimduplicates=false&amp;rowlimit=300";
  var baseRequest = {
      url: "",
      type: ""
  };
  //Parses a local object from JSON search result.
  function getNavigationFromDto(dto) {
      var item = new SPOCustom.Models.NavigationNode();
      if (dto != undefined) {
          var webTemplate = getSearchResultsValue(dto.Cells.results, 'WebTemplate');
          if (webTemplate != "APP") {
              item.Title(getSearchResultsValue(dto.Cells.results, 'Title')); //Key = Title
              item.Url(getSearchResultsValue(dto.Cells.results, 'Path')); //Key = Path
              item.Parent(getSearchResultsValue(dto.Cells.results, 'ParentLink')); //Key = ParentLink
          }
      }
      return item;
  }
  function getSearchResultsValue(results, key) {
      for (i = 0; i < results.length; i++) {
          if (results[i].Key == key) {
              return results[i].Value;
          }
      }
      return null;
  }
  //Parse a local object from the serialized cache.
  function getNavigationFromCache(dto) {
      var item = new SPOCustom.Models.NavigationNode();
      if (dto != undefined) {
          item.Title(dto.Title);
          item.Url(dto.Url);
          item.Parent(dto.Parent);
      }
      return item;
  }
  /* create a new OData request for JSON response */
  function getRequest(endpoint) {
      var request = baseRequest;
      request.type = "GET";
      request.url = endpoint;
      request.headers = { ACCEPT: "application/json;odata=verbose" };
      return request;
  };
  /* Navigation Module*/
  function NavigationViewModel() {
      "use strict";
      var self = this;
      self.nodes = ko.observableArray([]);
      self.hierarchy = ko.observableArray([]);;
      self.loadNavigatioNodes = function () {
          //Check local storage for cached navigation datasource.
          var fromStorage = localStorage["nodesCache"];
          if (false) {
              var cachedNodes = JSON.parse(localStorage["nodesCache"]);
              if (cachedNodes &amp;&amp; timeStamp) {
                  //Check for cache expiration. Currently set to 3 hrs.
                  var now = new Date();
                  var diff = now.getTime() - timeStamp;
                  if (Math.round(diff / (1000 * 60 * 60)) < 3) {
                      //return from cache.
                      var cacheResults = [];
                      $.each(cachedNodes, function (i, item) {
                          var nodeitem = getNavigationFromCache(item, true);
                          cacheResults.push(nodeitem);
                      });
                      self.buildHierarchy(cacheResults);
                      self.toggleView();
                      addEventsToElements();
                      return;
                  }
              }
          }
          //No cache hit, REST call required.
          self.queryRemoteInterface();
      };
      //Executes a REST call and builds the navigation hierarchy.
      self.queryRemoteInterface = function () {
          var oDataRequest = getRequest(query);
          $.ajax(oDataRequest).done(function (data) {
              var results = [];
              $.each(data.d.query.PrimaryQueryResult.RelevantResults.Table.Rows.results, function (i, item) {
                  if (i == 0) {
                      //Add root element.
                      var rootItem = new SPOCustom.Models.NavigationNode();
                      rootItem.Title("Root");
                      rootItem.Url(root);
                      rootItem.Parent(null);
                      results.push(rootItem);
                  }
                  var navItem = getNavigationFromDto(item);
                  results.push(navItem);
              });
              //Add to local cache
              localStorage["nodesCache"] = ko.toJSON(results);
              localStorage["nodesCachedAt"] = new Date().getTime();
              self.nodes(results);
              if (self.nodes().length > 0) {
                  var unsortedArray = self.nodes();
                  var sortedArray = unsortedArray.sort(self.sortObjectsInArray);
                  self.buildHierarchy(sortedArray);
                  self.toggleView();
                  addEventsToElements();
              }
          }).fail(function () {
              //Handle error here!!
              $("#loading").hide();
              $("#error").show();
          });
      };
      self.toggleView = function () {
          var navContainer = document.getElementById("navContainer");
          ko.applyBindings(self, navContainer);
          $("#loading").hide();
          $("#navContainer").show();
      };
      //Uses linq.js to build the navigation tree.
      self.buildHierarchy = function (enumerable) {
          self.hierarchy(Enumerable.From(enumerable).ByHierarchy(function (d) {
              return d.Parent() == null;
          }, function (parent, child) {
              if (parent.Url() == null || child.Parent() == null)
                  return false;
              return parent.Url().toUpperCase() == child.Parent().toUpperCase();
          }).ToArray());
          self.sortChildren(self.hierarchy()[0]);
      };
      self.sortChildren = function (parent) {
          // sjip processing if no children
          if (!parent || !parent.children || parent.children.length === 0) {
              return;
          }
          parent.children = parent.children.sort(self.sortObjectsInArray2);
          for (var i = 0; i < parent.children.length; i++) {
              var elem = parent.children[i];
              if (elem.children &amp;&amp; elem.children.length > 0) {
                  self.sortChildren(elem);
              }
          }
      };
      // ByHierarchy method breaks the sorting in chrome and firefix 
      // we need to resort  as ascending
      self.sortObjectsInArray2 = function (a, b) {
          if (a.item.Title() > b.item.Title())
              return 1;
          if (a.item.Title() < b.item.Title())
              return -1;
          return 0;
      };
      self.sortObjectsInArray = function (a, b) {
          if (a.Title() > b.Title())
              return -1;
          if (a.Title() < b.Title())
              return 1;
          return 0;
      }
  }
  //Loads the navigation on load and binds the event handlers for mouse interaction.
  function InitCustomNav() {
      var viewModel = new NavigationViewModel();
      viewModel.loadNavigatioNodes();
  }
  function addEventsToElements() {
      //events.
  
  ```

     <span data-ttu-id="ab850-215">$("li.level1").mouseover (функция {)</span><span class="sxs-lookup"><span data-stu-id="ab850-215">$("li.level1").mouseover(function () {</span></span> 
  
<span data-ttu-id="ab850-216">положение var = $(this).position();</span><span class="sxs-lookup"><span data-stu-id="ab850-216">var position = $(this).position();</span></span>
  
<span data-ttu-id="ab850-217">$(это).find("ul.level2").css ({ширины: 100, слева: position.left + 10, наиболее распространенные: 50});</span><span class="sxs-lookup"><span data-stu-id="ab850-217">$(this).find("ul.level2").css({ width: 100, left: position.left + 10, top: 50 });</span></span>
    
     }) 
  
<span data-ttu-id="ab850-218">.mouseout (функция {)</span><span class="sxs-lookup"><span data-stu-id="ab850-218">.mouseout(function () {</span></span>
  
<span data-ttu-id="ab850-219">$(это).find("ul.level2").css ({левой:-99999 верхней: 0});</span><span class="sxs-lookup"><span data-stu-id="ab850-219">$(this).find("ul.level2").css({ left: -99999, top: 0 });</span></span>
  
<span data-ttu-id="ab850-220">});</span><span class="sxs-lookup"><span data-stu-id="ab850-220"></span></span>
  
<span data-ttu-id="ab850-221">$("li.level2").mouseover (функция {)</span><span class="sxs-lookup"><span data-stu-id="ab850-221">$("li.level2").mouseover(function () {</span></span>
  
<span data-ttu-id="ab850-222">положение var = $(this).position();</span><span class="sxs-lookup"><span data-stu-id="ab850-222">var position = $(this).position();</span></span>
  
<span data-ttu-id="ab850-223">Console.log(JSON.stringify(Position));</span><span class="sxs-lookup"><span data-stu-id="ab850-223">console.log(JSON.stringify(position));</span></span>
  
<span data-ttu-id="ab850-224">$(это).find("ul.level3").css ({ширины: 100, слева: position.left + 95, наиболее распространенные: position.top});</span><span class="sxs-lookup"><span data-stu-id="ab850-224">$(this).find("ul.level3").css({ width: 100, left: position.left + 95, top: position.top});</span></span>
    
     }) 
  
<span data-ttu-id="ab850-225">.mouseout (функция {)</span><span class="sxs-lookup"><span data-stu-id="ab850-225">.mouseout(function () {</span></span>
  
<span data-ttu-id="ab850-226">$(это).find("ul.level3").css ({левой:-99999 верхней: 0});</span><span class="sxs-lookup"><span data-stu-id="ab850-226">$(this).find("ul.level3").css({ left: -99999, top: 0 });</span></span>
  
<span data-ttu-id="ab850-227">});</span><span class="sxs-lookup"><span data-stu-id="ab850-227"></span></span>
    
    } _spBodyOnLoadFunctionNames.push("InitCustomNav");
    
    To summarize the code shown above in the jQuery **[$(document).ready]** function there is a **[viewModel]** object created and then the **[loadNavigationNodes()]** function on that object is called. This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function **[queryRemoteInterface()]**. 
    
    **[QueryRemoteInterface()]** builds a request using the **[getRequest()]** function with the query parameter defined earlier in the script and then returns data from the server. This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties. This data is then parsed into the previously defined **[SPO.Models.NavigationNode]** objects which use Knockout.js to create observable properties for use by data binding the values into the HTML that we defined earlier. The objects are then put into a results array. This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads. 
    
8. <span data-ttu-id="ab850-p116">Затем результаты присваиваются массив **[self.nodes]** и иерархия создается из объектов, с помощью linq.js присвоение массива **[self.heirarchy]** выходные данные. Этот массив — это объект, связанный с HTML-код. Для этого в функции **[toggleView()]** , передав собственный объект в функцию **[ko.applyBinding()]** . Затем в результате массив иерархии привязаны к следующий HTML-код:</span><span class="sxs-lookup"><span data-stu-id="ab850-p116">Next, the results are assigned to the **[self.nodes]** array and a hierarchy is built out of the objects using linq.js assigning the output to an array **[self.heirarchy]**. This array is the object that is bound to the HTML. This is done in the **[toggleView()]** function by passing the self object to the **[ko.applyBinding()]** function. This then causes the hierarchy array to be bound to the following HTML:</span></span> 
    
  ```
  <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
  ```

    <span data-ttu-id="ab850-232">И, наконец обработчики событий для **[mouseenter]** и **[mouseexit]** добавляются навигации верхнего уровня для обработки раскрывающихся меню дочернего сайта которого выполняется в функции **[addEventsToElements()]** .</span><span class="sxs-lookup"><span data-stu-id="ab850-232">Finally, the event handlers for **[mouseenter]** and **[mouseexit]** are added to the top-level navigation to handle the subsite drop-down menus which is done in the **[addEventsToElements()]** function.</span></span> 
    
    <span data-ttu-id="ab850-233">В приведенном ниже снимке экрана можно увидеть результаты панели навигации:</span><span class="sxs-lookup"><span data-stu-id="ab850-233">The results of the navigation can be seen in the screen shot below:</span></span>
    
    ![Снимок экрана с результатами навигации](media/020d34d2-942a-431b-9b26-6d2c8a6fde30.png)
  
    <span data-ttu-id="ab850-235">В нашем примере сложной навигации загрузка новой страницы без локального кэширования показывает, что время обработки на сервере было удалено при тестовой структурной навигации, чтобы получить такой же результат, как при управляемой навигации.</span><span class="sxs-lookup"><span data-stu-id="ab850-235">In our complex navigation example a fresh page load without the local caching shows the time spent on the server has been cut down from the benchmark structural navigation to get a similar result as the managed navigation approach.</span></span>
    
    ![Снимок экрана: SPRequestDuration 301](media/307d7caf-e83a-40d9-a551-91d842521d03.png)
  
    <span data-ttu-id="ab850-237">Одно из главных преимуществ такого подхода — то, что при использовании локального хранилища HTML5 данные навигации хранятся локально для пользователя на случай загрузки этой страницы в будущем.</span><span class="sxs-lookup"><span data-stu-id="ab850-237">One major benefit of this approach is that by using HTML5 local storage, the navigation is stored locally for the user the next time they load the page.</span></span>
    
<span data-ttu-id="ab850-p117">Мы получаем значительные улучшения производительности от использования поискового API для структурной навигации. Однако для реализации и настройки этого функционала необходимы некоторые технические возможности. В этом примере реализации сайты упорядочены так же, как и в готовой структурной навигации, — в алфавитном порядке. Если вы хотите отойти от этого порядка, то сложность разработки и сопровождения возрастет. Кроме того, этот подход требует отказа от поддерживаемых эталонных страниц. Если пользовательские эталонные страницы не поддерживаются, то ваш сайт перестанет получать обновления и улучшения, которые Майкрософт разрабатывает для эталонных страниц.</span><span class="sxs-lookup"><span data-stu-id="ab850-p117">We get major performance improvements from using the search API for structural navigation; however, it takes some technical capability to execute and customize this functionality. In the example implementation, the sites are ordered in the same way as the out-of-the-box structural navigation; alphabetical order. If you wanted to deviate from this order, it would be more complicated to develop and maintain. Also, this approach requires you to deviate from the supported master pages. If the custom master page is not maintained, your site will miss out on updates and improvements that Microsoft makes to the master pages.</span></span>
  
<span data-ttu-id="ab850-243">Этот код имеет следующие зависимости:</span><span class="sxs-lookup"><span data-stu-id="ab850-243">The above code has the following dependencies:</span></span>
  
- <span data-ttu-id="ab850-244">jQuery-[http://jquery.com/](http://jquery.com/)</span><span class="sxs-lookup"><span data-stu-id="ab850-244">jQuery - [http://jquery.com/](http://jquery.com/)</span></span>
    
- <span data-ttu-id="ab850-245">KnockoutJS-[http://knockoutjs.com/](http://knockoutjs.com/)</span><span class="sxs-lookup"><span data-stu-id="ab850-245">KnockoutJS - [http://knockoutjs.com/](http://knockoutjs.com/)</span></span>
    
- <span data-ttu-id="ab850-246">LINQ.js - [http://linqjs.codeplex.com/](http://linqjs.codeplex.com/), или [github.com/neuecc/linq.js](https://github.com/neuecc/linq.js/)</span><span class="sxs-lookup"><span data-stu-id="ab850-246">Linq.js - [http://linqjs.codeplex.com/](http://linqjs.codeplex.com/), or [github.com/neuecc/linq.js](https://github.com/neuecc/linq.js/)</span></span>
    
<span data-ttu-id="ab850-p118">Текущая версия LinqJS не содержит метод ByHierarchy, используемый в предыдущем примере кода и нарушит работу кода навигации. Чтобы устранить эту проблему, добавьте следующий метод в файл Linq.js перед строкой «Flatten: работать ()».</span><span class="sxs-lookup"><span data-stu-id="ab850-p118">The current version of LinqJS does not contain the ByHierarchy method used in the above code and will break the navigation code. To fix this, add the following method to the Linq.js file before the line "Flatten: function ()".</span></span>
  
```
ByHierarchy: function(firstLevel, connectBy, orderBy, ascending, parent) {
     ascending = ascending == undefined ? true : ascending;
     var orderMethod = ascending == true ? 'OrderBy' : 'OrderByDescending';
     var source = this;
     firstLevel = Utils.CreateLambda(firstLevel);
     connectBy = Utils.CreateLambda(connectBy);
     orderBy = Utils.CreateLambda(orderBy);
    
     //Initiate or increase level
     var level = parent === undefined ? 1 : parent.level + 1;
    return new Enumerable(function() {
         var enumerator;
         var index = 0;
        var createLevel = function() {
                 var obj = {
                     item: enumerator.Current(),
                     level : level
                 };
                 obj.children = Enumerable.From(source).ByHierarchy(firstLevel, connectBy, orderBy, ascending, obj);
                 if (orderBy !== undefined) {
                     obj.children = obj.children[orderMethod](function(d) {
                         return orderBy(d.item); //unwrap the actual item for sort to work
                     });
                 }
                 obj.children = obj.children.ToArray();
                 Enumerable.From(obj.children).ForEach(function(child) {
                     child.getParent = function() {
                         return obj;
                     };
                 });
                 return obj;
             };
        return new IEnumerator(
        function() {
             enumerator = source.GetEnumerator();
         }, function() {
             while (enumerator.MoveNext()) {
                 var returnArr;
                 if (!parent) {
                     if (firstLevel(enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }
                } else {
                     if (connectBy(parent.item, enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }
                 }
             }
             return false;
         }, function() {
             Utils.Dispose(enumerator);
         })
     });
 },

```


