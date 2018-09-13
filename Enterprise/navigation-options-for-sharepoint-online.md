---
title: Параметры навигации для SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: В этой статье описываются сайты параметры навигации с публикации SharePoint включен в SharePoint Online. Выбор и настройка навигации заметно влияет на производительность и масштабируемость сайтов в SharePoint Online.
ms.openlocfilehash: 08790dcee343e9e69bbaab149cce8a390470e7d6
ms.sourcegitcommit: 5731dce2440e5a7a261f6360e8e2e9639d339d4e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/12/2018
ms.locfileid: "23957454"
---
# <a name="navigation-options-for-sharepoint-online"></a><span data-ttu-id="cb3d4-104">Параметры навигации для SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="cb3d4-104">Navigation options for SharePoint Online</span></span>

<span data-ttu-id="cb3d4-p102">В этой статье описываются сайты параметры навигации с публикации SharePoint включен в SharePoint Online. Выбор и настройка навигации заметно влияет на производительность и масштабируемость сайтов в SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-p102">This article describes navigation options sites with SharePoint Publishing enabled in SharePoint Online. The choice and configuration of navigation significantly impacts the performance and scalability of sites in SharePoint Online.</span></span>

## <a name="overview"></a><span data-ttu-id="cb3d4-107">Общие сведения</span><span class="sxs-lookup"><span data-stu-id="cb3d4-107">Overview</span></span>

<span data-ttu-id="cb3d4-p103">Конфигурации поставщика навигации можно значительно повысить производительность для всего сайта и тщательного анализа необходимо выполнить, чтобы выбрать поставщика навигации и конфигурации, масштабируется эффективно требования к сайту SharePoint. Существует два поставщиков ожидания введите навигации, а также реализации пользовательских переходов.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-p103">Navigation provider configuration can significantly impact performance for the entire site, and careful consideration must be taken to pick a navigation provider and configuration that scales effectively for the requirements of a SharePoint site. There are two out-of-the-box navigation providers, as well as custom navigation implementations.</span></span>

<span data-ttu-id="cb3d4-p104">Первый вариант [**навигации Managed (метаданные)**](#using-managed-navigation-and-metadata-in-sharepoint-online), рекомендуется и — это один из параметров по умолчанию в SharePoint Online; Тем не менее рекомендуется отключить фильтрацию по ролям безопасности, если не требуется. Фильтрация по ролям безопасности используется в качестве параметров безопасности по умолчанию для данного поставщика навигации; количество сайтов не требуется дополнительная нагрузка безопасности обрезки с момента элементы навигации часто являются согласованными для всех пользователей сайта. Рекомендуемая конфигурация для отключения фильтрации по ролям безопасности данного поставщика навигации не требует перечисление структуры сайта и хорошо масштабируемое с приемлемой производительности.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-p104">The first option, [**Managed (Metadata) navigation**](#using-managed-navigation-and-metadata-in-sharepoint-online), is recommended, and is one of the default options in SharePoint Online; however, we recommend that security trimming be disabled unless required. Security trimming is enabled as a secure-by-default setting for this navigation provider; however, many sites do not require the overhead of security trimming since navigation elements often are consistent for all users of the site. With the recommended configuration to disable security trimming, this navigation provider does not require enumerating site structure and is highly scalable with acceptable performance impact.</span></span>

<span data-ttu-id="cb3d4-p105">Второй вариант [**структуры навигации**](#using-structural-navigation-in-sharepoint-online), **это не рекомендуется навигации в SharePoint Online**. В этом поставщика навигации был разработан для локальной топологии с ограниченными поддержки в SharePoint Online. Он обеспечивает некоторые дополнительные набор возможностей и других параметров навигации, эти функции, включая фильтрация по ролям безопасности и перечисление структура сайта, поступающие по цене чрезмерной вызовов и влияние масштабирования и производительности при использовании. Сайты, использующие structed навигации, которые потребляют чрезмерное количество ресурсов могут быть может быть регулирования.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-p105">The second option, [**Structural navigation**](#using-structural-navigation-in-sharepoint-online), **is NOT a recommended navigation option in SharePoint Online**. This navigation provider was designed for an on-premises topology has limited support in SharePoint Online. While it provides some additional set of capabilities versus other navigation options, these features, including security trimming and site structure enumeration, comes at a cost of excessive server calls and impacts scalability and performance when it is used. Sites using structed navigation that consume excessive resources may be subject to throttling.</span></span>

<span data-ttu-id="cb3d4-p106">В дополнение к поставщиков навигации ожидания введите многие пользователи реализовано успешно реализации альтернативных пользовательских переходов. Один общий класс реализации пользовательских переходов внедрены шаблоны отобразить клиента разработки, в которых хранятся локального кэша узлов навигации. (См. **[со стороны клиента на основе поиска](#using-search-driven-client-side-scripting)** в этой статье.)</span><span class="sxs-lookup"><span data-stu-id="cb3d4-p106">In addition to the out-of-the-box navigation providers, many customers have successfully implemented alternative custom navigation implementations. One common class of custom navigation implementations embraces client-rendered design patterns that store a local cache of navigation nodes. (See **[Search-driven client-side scripting](#using-search-driven-client-side-scripting)** in this article.)</span></span>

<span data-ttu-id="cb3d4-120">Поставщики навигации существует две основные преимущества:</span><span class="sxs-lookup"><span data-stu-id="cb3d4-120">These navigation providers have a couple of key advantages:</span></span> 
- <span data-ttu-id="cb3d4-121">Они обычно работают, так и с отклика страницы макетов.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-121">They generally work well with responsive page designs.</span></span>
- <span data-ttu-id="cb3d4-122">Они являются очень масштабируемые и высокой производительностью, так как они могут создавать без затрат на ресурсы (и обновления в фоновом режиме после истечения времени ожидания).</span><span class="sxs-lookup"><span data-stu-id="cb3d4-122">They are extremely scalable and performant because they can render with no resource cost (and refresh in the background after a timeout).</span></span> 
- <span data-ttu-id="cb3d4-123">Эти поставщиков навигации можно извлечь данные навигации, с помощью различных стратегий, от простого статических конфигураций для различных поставщиков динамических данных.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-123">These navigation providers can retrieve navigation data using various strategies, ranging from simple static configurations to various dynamic data providers.</span></span> 

<span data-ttu-id="cb3d4-124">Пример поставщика данных является использование **Навигация на основе поиска**, что обеспечивает гибкость для перечисления узлов навигации и обработка эффективно триммер безопасности.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-124">An example of a data provider is to use a **Search-driven navigation**, which allows flexibility for enumerating navigation nodes and handling security trimming efficiently.</span></span> 

<span data-ttu-id="cb3d4-p107">Возможны другие популярные решения для построения **настраиваемых поставщиков навигации**. Просмотрите [решения навигации для порталов SharePoint Online](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) для получения дополнительных инструкций на создание настраиваемого поставщика навигации.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-p107">There are other popular options to build **Custom navigation providers**. Please review [Navigation solutions for SharePoint Online portals](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) for further guidance on building a Custom navigation provider.</span></span>
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a><span data-ttu-id="cb3d4-127">Преимущества и недостатки из SharePoint Online параметры навигации</span><span class="sxs-lookup"><span data-stu-id="cb3d4-127">Pros and Cons of SharePoint Online navigation options</span></span>

<span data-ttu-id="cb3d4-128">В следующей таблице перечислены преимущества и недостатки каждого варианта.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-128">The following table summarizes the pros and cons of each option.</span></span> 


|<span data-ttu-id="cb3d4-129">Управляемая навигация</span><span class="sxs-lookup"><span data-stu-id="cb3d4-129">Managed navigation</span></span>  |<span data-ttu-id="cb3d4-130">Структурная навигация</span><span class="sxs-lookup"><span data-stu-id="cb3d4-130">Structural navigation</span></span>  |<span data-ttu-id="cb3d4-131">Навигация на основе поиска</span><span class="sxs-lookup"><span data-stu-id="cb3d4-131">Search-driven navigation</span></span>  |<span data-ttu-id="cb3d4-132">Поставщик Custom навигации</span><span class="sxs-lookup"><span data-stu-id="cb3d4-132">Custom-navigation provider</span></span>  |
|---------|---------|---------|---------|
|<span data-ttu-id="cb3d4-133">Преимущества:</span><span class="sxs-lookup"><span data-stu-id="cb3d4-133">Pros:</span></span><br/><br/><span data-ttu-id="cb3d4-134">простота поддержки;</span><span class="sxs-lookup"><span data-stu-id="cb3d4-134">Easy to maintain</span></span><br/><span data-ttu-id="cb3d4-135">Рекомендуется использовать параметр</span><span class="sxs-lookup"><span data-stu-id="cb3d4-135">Recommended option</span></span><br/>     |<span data-ttu-id="cb3d4-136">Преимущества:</span><span class="sxs-lookup"><span data-stu-id="cb3d4-136">Pros:</span></span><br/><br/><span data-ttu-id="cb3d4-137">простота настройки;</span><span class="sxs-lookup"><span data-stu-id="cb3d4-137">Easy to configure</span></span><br/><span data-ttu-id="cb3d4-138">Фильтруются по ролям безопасности</span><span class="sxs-lookup"><span data-stu-id="cb3d4-138">Security trimmed</span></span><br/><span data-ttu-id="cb3d4-139">Автоматически меняется по мере добавления содержимого</span><span class="sxs-lookup"><span data-stu-id="cb3d4-139">Automatically updates as content is added</span></span><br/>|<span data-ttu-id="cb3d4-140">Плюсы:</span><span class="sxs-lookup"><span data-stu-id="cb3d4-140">Pros:</span></span><br/><br/><span data-ttu-id="cb3d4-141">Фильтруются по ролям безопасности</span><span class="sxs-lookup"><span data-stu-id="cb3d4-141">Security trimmed</span></span><br/><span data-ttu-id="cb3d4-142">автоматическое обновление при добавлении сайтов;</span><span class="sxs-lookup"><span data-stu-id="cb3d4-142">Automatically updates as sites are added</span></span><br/><span data-ttu-id="cb3d4-143">короткое время загрузки и локальное кэширование структуры навигации.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-143">Fast loading time and locally cached navigation structure</span></span><br/>|<span data-ttu-id="cb3d4-144">Плюсы:</span><span class="sxs-lookup"><span data-stu-id="cb3d4-144">Pros:</span></span><br/><br/><span data-ttu-id="cb3d4-145">Широкий выбор вариантов</span><span class="sxs-lookup"><span data-stu-id="cb3d4-145">Wider choice of options available</span></span><br/><span data-ttu-id="cb3d4-146">Быстрое загрузки при кэшировании используется правильно</span><span class="sxs-lookup"><span data-stu-id="cb3d4-146">Fast loading when caching is used correctly</span></span><br/><span data-ttu-id="cb3d4-147">Широкие возможности работы со макет отклика страницы</span><span class="sxs-lookup"><span data-stu-id="cb3d4-147">Many options work well with responsive page design</span></span><br/>|
|<span data-ttu-id="cb3d4-148">Недостатки:</span><span class="sxs-lookup"><span data-stu-id="cb3d4-148">Cons:</span></span><br/><br/><span data-ttu-id="cb3d4-149">отсутствие автоматического обновления для отражения структуры сайта.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-149">Not automatically updated to reflect site structure</span></span><br/><span data-ttu-id="cb3d4-150">Воздействия на производительность при включении фильтрации по ролям безопасности</span><span class="sxs-lookup"><span data-stu-id="cb3d4-150">Impacts performance if security trimming is enabled</span></span><br/>|<span data-ttu-id="cb3d4-151">Недостатки:</span><span class="sxs-lookup"><span data-stu-id="cb3d4-151">Cons:</span></span><br/><br/><span data-ttu-id="cb3d4-152">**Не рекомендуется**</span><span class="sxs-lookup"><span data-stu-id="cb3d4-152">**Not recommended**</span></span><br/><span data-ttu-id="cb3d4-153">**Воздействия на производительность и масштабируемость**</span><span class="sxs-lookup"><span data-stu-id="cb3d4-153">**Impacts performance and scalability**</span></span><br/><span data-ttu-id="cb3d4-154">**Может быть регулирования**</span><span class="sxs-lookup"><span data-stu-id="cb3d4-154">**Subject to throttling**</span></span><br/>|<span data-ttu-id="cb3d4-155">Недостатки:</span><span class="sxs-lookup"><span data-stu-id="cb3d4-155">Cons:</span></span><br/><br/><span data-ttu-id="cb3d4-156">нет возможности простого упорядочивания сайтов;</span><span class="sxs-lookup"><span data-stu-id="cb3d4-156">No ability to easily order sites</span></span><br/><span data-ttu-id="cb3d4-157">требуется настройка эталонной страницы (необходимы технические навыки).</span><span class="sxs-lookup"><span data-stu-id="cb3d4-157">Requires customization of the master page (technical skills required)</span></span><br/>|<span data-ttu-id="cb3d4-158">Недостатки:</span><span class="sxs-lookup"><span data-stu-id="cb3d4-158">Cons:</span></span><br/><br/><span data-ttu-id="cb3d4-159">Является обязательным, разработки пользовательских решений</span><span class="sxs-lookup"><span data-stu-id="cb3d4-159">Custom development is required</span></span><br/><span data-ttu-id="cb3d4-160">Внешний источник данных аудио- и необходимости кэша хранятся например Azure</span><span class="sxs-lookup"><span data-stu-id="cb3d4-160">External data source / cache stored is needed e.g. Azure</span></span><br/>|

<span data-ttu-id="cb3d4-p108">Наиболее подходящий вариант для веб-узла будет зависят от требований к сайта и технические возможности. Если необходимо, чтобы поставщик навигации масштабируемые ожидания введите, управляемой навигации с фильтрация по ролям безопасности этот параметр отключен является очень хорошим выбором.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-p108">The most appropriate option for your site will depend on your site requirements and on your technical capability. If you want a scalable out-of-the-box navigation provider, then Managed navigation with security trimming disabled is a very good option.</span></span> 

<span data-ttu-id="cb3d4-p109">Параметр управляемой навигации могут поддерживать через конфигурации, не связанных файлов настройки кода, и это значительно быстрее, чем структуры навигации. Если требуется фильтрация по ролям безопасности и готовы, с помощью настраиваемой главной страницы и имеет некоторые возможности в организации, чтобы сохранить изменения, которые могут возникнуть в главную страницу по умолчанию для SharePoint Online, выберите вариант на основе механизмов поиска может привести к более взаимодействие с пользователем. При наличии более сложные требования поставщика пользовательских переходов может быть правильным выбором. Структуры навигации не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-p109">The Managed navigation option can be maintained through configuration, does not involve code customization files, and it is significantly faster than structural navigation. If you require security trimming and are comfortable using a custom master page and have some capability in the organization to maintain the changes that may occur in the default master page for SharePoint Online, then the Search-driven option may produce a better user experience. If you have more complex requirements, then a custom navigation provider may be the right choice. Structural navigation is NOT recommended.</span></span>

<span data-ttu-id="cb3d4-p110">И, наконец важно Обратите внимание на то, что SharePoint добавление поставщиков дополнительных навигации и функции для современных архитектур сайтов SharePoint, использование более плоская иерархии сайтов и модели и звезда с сайтами SharePoint сервера-концентратора. Это позволяет много сценариев для достигнуть, не требующие использования функции публикации SharePoint, и эти конфигурации навигации оптимизированные для улучшения масштабируемости и задержка в SharePoint Online. Обратите внимание на то, что применение же принцип - упрощение Общая структура сайта публикации SharePoint для структуру, часто помогает с общей производительности и масштабирования также. Это означает, что вместо одного семейства веб-сайтов с помощью сотен сайтов (дочерние сайты), лучше иметь множество семейств веб-сайтов с очень небольшого числа дочерних сайтов (дочерние сайты).</span><span class="sxs-lookup"><span data-stu-id="cb3d4-p110">Finally, it’s important to note that SharePoint is adding additional navigation providers and functionality for modern SharePoint site architectures leveraging a more flattened site hierarchy and a hub-and-spoke model with SharePoint hub sites. This allows many scenarios to be achieved that do NOT require the use of SharePoint Publishing feature, and these navigation configurations are optimized for scalability and latency within SharePoint Online. Note that applying the same principle - simplifying the overall structure of your SharePoint Publishing site to a flatter structure, often helps with overall performance and scale as well. What this means is that instead of having a single Site Collection with hundreds of sites (subwebs), a better approach is to have many site collections with very few subsites (subwebs).</span></span>


## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a><span data-ttu-id="cb3d4-171">С помощью управляемой навигации и метаданные в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="cb3d4-171">Using managed navigation and metadata in SharePoint Online</span></span>

<span data-ttu-id="cb3d4-p111">Управляемая Навигация — еще один параметр out поля, которые можно использовать для повторного создания большую часть функциональных возможностей структуры навигации. Управляемые метаданные можно настроить для фильтрации по ролям безопасности включена или отключена. При использовании фильтрации по ролям безопасности этот параметр отключен управляемой навигации довольно эффективно при загрузке все ссылки для перехода с константу количество вызовов сервера. Включение триммеров безопасности, однако инвертирует некоторые преимущества управляемой навигации и клиенты могут использовать для изучения один из пользовательских переходов решений для обеспечения оптимальной производительности и масштабируемости.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-p111">Managed navigation is another out-of-the-box option that you can use to recreate most of the same functionality as structural navigation. Managed metadata can be configured to have security trimming enabled or disabled. When configured with security trimming disabled, managed navigation is fairly efficient as it loads all the navigation links with a constant number of server calls. Enabling security trimming, however, negates some of the advantages of managed navigation, and customers may choose to explore one of the custom navigation solutions for optimal performance and scalability.</span></span>

<span data-ttu-id="cb3d4-p112">Количество сайтов не требуют фильтрация по ролям безопасности, как структура навигации часто согласованным для всех пользователей сайта. Если этот параметр отключен фильтрация по ролям безопасности и ссылка добавляется навигации, которая не все пользователи имеют доступ к, ссылки по-прежнему будут отображаться, но приведут к отказано в доступе. Нет и риска непреднамеренных доступа к содержимому.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-p112">Many sites do not require security trimming, as the navigation structure is often consistent for all users of the site. If security trimming is disabled and a link is added to navigation that not all users have access to, the link will still show but will lead to an access denied message. There is no risk of inadvertent access to the content.</span></span>

### <a name="how-to-implement-managed-navigation-and-the-results"></a><span data-ttu-id="cb3d4-179">Как реализовать управляемую навигацию и результаты</span><span class="sxs-lookup"><span data-stu-id="cb3d4-179">How to implement managed navigation and the results</span></span>

<span data-ttu-id="cb3d4-180">Существует несколько статей на Docs.Microsoft.com о сведения о управляемой навигации, например, в разделе [Обзор управляемой навигации в SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span><span class="sxs-lookup"><span data-stu-id="cb3d4-180">There are several articles on Docs.Microsoft.com about the details of managed navigation, for example, see [Overview of managed navigation in SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span></span>

<span data-ttu-id="cb3d4-p113">Чтобы реализовать управляемую навигацию, настройке условий с URL-адреса, соответствующие структуры переходов сайта. Даже управляемая Навигация может быть вручную curated для замены структуры навигации во многих случаях. Например:</span><span class="sxs-lookup"><span data-stu-id="cb3d4-p113">In order to implement managed navigation, you set up terms with URLs corresponding to the navigation structure of  the site. Managed navigation can even be manually curated to replace structural navigation in many cases. For example:</span></span>

![SharePoint Online структуры сайта](media/SPONavOptionsListOfSites.png)

<span data-ttu-id="cb3d4-185">Следующий пример демонстрирует производительность сложной навигации с использованием управляемой навигации.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-185">The following example shows the performance of the complex navigation using managed navigation.</span></span>

![Производительность сложных навигации, с помощью управляемой навигации](media/SPONavOptionsComplexNavPerf.png)

<span data-ttu-id="cb3d4-187">Использование управляемой навигации постоянно повышает производительность по сравнению с подходом структуры навигации.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-187">Using managed navigation consistently improves performance compared to the structural navigation approach.</span></span>
  
## <a name="using-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="cb3d4-188">Использование структурной навигации в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="cb3d4-188">Using structural navigation in SharePoint Online</span></span>

<span data-ttu-id="cb3d4-p114">Эта функция ожидания введите навигации, используемый по умолчанию и — это самый простой решения, но таким образом имеет компромиссов дорогостоящих производительности. Не требует настройки и не технической пользователя можно также легко добавить элементы, скрыть элементы и управления панели навигации на странице параметры. Это также тем не менее значение true для управляемой навигации, поэтому рекомендуется использовать управляемой навигации как, которые могут также быть легко управляемых и также управляются с помощью улучшить производительность.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-p114">This is the out-of-the-box navigation used by default and is the most straightforward solution but as such has an expensive performance trade-off. It does not require any customization and a non-technical user can also easily add items, hide items, and manage the navigation from the settings page. This is however also true for Managed Navigation so it is recommended to use Managed Navigation as that can also be easily managed and controlled as well with improved performance.</span></span>

![Структуры навигации с Показать дочерними сайтами выбранные](media/SPONavOptionsStructuredShowSubsites.png)
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="cb3d4-193">Переход на структурную навигацию в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="cb3d4-193">Turning on structural navigation in SharePoint Online</span></span>

<span data-ttu-id="cb3d4-p115">В качестве демонстрации как производительности в решении стандартных SharePoint Online с помощью структуры навигации и отображать дочерние сайты вариант включен. Ниже приведен снимок экрана с параметрами на странице " **Параметры сайта** " \> **навигации**.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-p115">To illustrate how the performance in a standard SharePoint Online solution with structural navigation and the show subsites option turned on. Below is a screenshot of settings found on the page **Site Settings** \> **Navigation**.</span></span>
  
![Снимок экрана: дочерние сайты](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a><span data-ttu-id="cb3d4-197">Анализ производительности структурной навигации в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="cb3d4-197">Analyzing structural navigation performance in SharePoint Online</span></span>

<span data-ttu-id="cb3d4-198">Для анализа производительности страниц SharePoint, вкладка **сети** средства разработчика F12 в Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-198">To analyze the performance of a SharePoint page, use the **Network** tab of the F12 developer tools in Internet Explorer.</span></span> 
  
![Снимок экрана: вкладка "Сеть", отображенная после вызова средств разработчика (F12)](media/SPONavOptionsNetworks.png)
  
1. <span data-ttu-id="cb3d4-200">На вкладке **Сеть** выберите загруженную страницу .aspx, а затем — вкладку **Сведения**.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-200">On the **Network** tab, click on the .aspx page that is being loaded and then click on the **Details** tab.</span></span><br/> <span data-ttu-id="cb3d4-201">![Снимок экрана: вкладка "Сведения"](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span><span class="sxs-lookup"><span data-stu-id="cb3d4-201">![Screenshot showing the details tab](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span></span><br/>
2. <span data-ttu-id="cb3d4-202">Щелкните пункт **Заголовки ответов**.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-202">Click **Response headers**.</span></span> <br/><span data-ttu-id="cb3d4-203">![Снимок экрана: вкладка "Сведения"](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span><span class="sxs-lookup"><span data-stu-id="cb3d4-203">![Screenshot of Details tab](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span></span><br/><span data-ttu-id="cb3d4-204">SharePoint возвращает некоторые полезные диагностические сведения в заголовке ответа.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-204">SharePoint returns some useful diagnostic information in its response headers.</span></span> 
3. <span data-ttu-id="cb3d4-p116">Один из самых полезных элементов данных — **SPRequestDuration** , который соответствует значению, в миллисекундах, сколько времени запроса, которое потребовалось для обработки на сервере. На следующем снимке экрана **показано дочерних сайтов** не установлен для структуры навигации. Это значит, что существует только связь семейства сайтов в глобальной навигации.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-p116">One of the most useful pieces of information is **SPRequestDuration** which is the value, in milliseconds, of how long a request took to process on the server. In the following screenshot **show subsites** is unchecked for the structural navigation. This means that there is only the site collection link in the global navigation:</span></span><br/><span data-ttu-id="cb3d4-208">![Снимок экрана: время загрузки как время ответа на запрос](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span><span class="sxs-lookup"><span data-stu-id="cb3d4-208">![Screenshot showing load times as request duration](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span></span><br/>
4. <span data-ttu-id="cb3d4-p117">Клавиша **SPRequestDuration** имеет значение 245 (в миллисекундах). Представляет время, затраченное на возврата запроса. Поскольку существует только один элемент навигации на сайте, это хороший тестирования производительности для SharePoint Online выполнение без толстые навигации. На следующем снимке экрана показано, как добавлять в дочерних сайтов влияет этот ключ.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-p117">The **SPRequestDuration** key has a value of 245 milliseconds. This represents the time it took to return the request. Since there is only one navigation item on the site, this is a good benchmark for how SharePoint Online performs without heavy navigation. The next screen shot shows how adding in the subsites affects this key.</span></span><br/><span data-ttu-id="cb3d4-213">![Снимок экрана: длительность обработки запроса составляет 2502 мс](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span><span class="sxs-lookup"><span data-stu-id="cb3d4-213">![Screenshot showing a request duration of 2502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span></span><br/>
  
<span data-ttu-id="cb3d4-p118">Время, необходимое для возврата запроса страницы для этого сайта относительно простой пример существенно увеличена добавление дочерних сайтов. Иерархии сложных сайтов, включая страницы в области навигации и другие настройки и параметры топологии, можно значительно повысить этой воздействия еще больше.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-p118">Adding the subsites has significantly increased the time it takes to return the page request for this relatively simple sample site. Complex site hierarchies, including pages in navigation, and other configuration and topology options can dramatically increase this impact even further.</span></span>

## <a name="using-search-driven-client-side-scripting"></a><span data-ttu-id="cb3d4-216">Использование скриптов с навигацией на основе поиска на стороне клиента</span><span class="sxs-lookup"><span data-stu-id="cb3d4-216">Using Search-driven client-side scripting</span></span>

<span data-ttu-id="cb3d4-p119">С помощью поиска могут использовать индексы, которые создаются в фоновом режиме, используя непрерывного обхода контента. Результаты поиска которые извлекаются из индекса поиска и результаты, обрезать безопасности. Это обычно быстрее, чем поставщиков навигации ожидания введите, когда требуется фильтрация по ролям безопасности. Использование поиска для структуры навигации, особенно в том случае, если у вас есть структуру сложных сайта будет ускорить загрузки времени значительно страницы. Основное преимущество это через управляемой навигации — преимущества фильтрация по ролям безопасности.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-p119">Using search you can leverage the indexes that are built up in the background using continuous crawl. The search results are pulled from the search index and the results are security-trimmed. This is generally faster than out-of-the-box navigation providers when security trimming is required. Using search for structural navigation, especially if you have a complex site structure, will speed up page loading time considerably. The main advantage of this over managed navigation is that you benefit from security trimming.</span></span>

<span data-ttu-id="cb3d4-p120">Этот подход включает создание настраиваемой главной страницы и заменив навигации ожидания введите код настраиваемого HTML-код. Выполните следующие действия, описанные в следующем примере для замены навигации кода в файле `seattle.html`. В этом примере будет открыт `seattle.html` файл и замените весь элемент `id=”DeltaTopNavigation”` с помощью пользовательского кода HTML.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-p120">This approach involves creating a custom master page and replacing the out-of-the-box navigation code with custom HTML. Follow this procedure outlined in the following example to replace the navigation code in the file `seattle.html`. In this example, you will open the `seattle.html` file and replace the whole element `id=”DeltaTopNavigation”` with custom HTML code.</span></span>

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a><span data-ttu-id="cb3d4-225">Пример: Замена кода ожидания введите переходов на главной странице</span><span class="sxs-lookup"><span data-stu-id="cb3d4-225">Example: Replace the out-of-the-box navigation code in a master page</span></span>

1.  <span data-ttu-id="cb3d4-226">Перейдите на страницу Параметры сайта.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-226">Navigate to the Site Settings page.</span></span>
2.  <span data-ttu-id="cb3d4-227">Откройте коллекцию эталонных страниц, выбрав пункт **Эталонные страницы**.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-227">Open the master page gallery by clicking **Master Pages**.</span></span>
3.  <span data-ttu-id="cb3d4-228">Здесь можно перемещаться по библиотеке и загрузите файл `seattle.master`.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-228">From here you can navigate through the library and download the file `seattle.master`.</span></span>
4.  <span data-ttu-id="cb3d4-229">Измените код с помощью текстового редактора и удалите фрагмент кода, представленный на следующем снимке экрана.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-229">Edit the code using a text editor and delete the code block in the following screen shot.</span></span><br/>![Удалите блок кода показано](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. <span data-ttu-id="cb3d4-231">Удаление кода между `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` и `<\SharePoint:AjaxDelta>` теги и замените его на следующий фрагмент:</span><span class="sxs-lookup"><span data-stu-id="cb3d4-231">Remove the code between the `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` and `<\SharePoint:AjaxDelta>` tags and replace it with the following snippet:</span></span><br/>

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
<br/>
6. <span data-ttu-id="cb3d4-p121">Замените URL-адрес в загрузке тега привязки в начале со ссылкой на изображение загрузки в семействе веб-сайтов "изображение". После внесения изменений, переименуйте файл и отправить его в коллекции главных страниц. Создает новый файл .master.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-p121">Replace the URL in the loading image anchor tag at the beginning, with a link to a loading image in your site collection. After you have made the changes, rename the file and then upload it to the master page gallery. This generates a new .master file.</span></span><br/>
7. <span data-ttu-id="cb3d4-p122">В этом HTML — это базовая разметка, которая будет устанавливаться результаты поиска, возвращаемые из кода JavaScript. Необходимо изменить код, чтобы изменить значение для корневого var = «веб-URL-адрес семейства сайтов», как показано в следующем фрагменте:</span><span class="sxs-lookup"><span data-stu-id="cb3d4-p122">This HTML is the basic markup that will be populated by the search results returned from JavaScript code. You will need to edit the code to change the value for var root = “site collection URL” as demonstrated in the following snippet:</span></span><br/>

```
var root = “https://spperformance.sharepoint.com/sites/NavigationBySearch”;
```
<br/>
8. <span data-ttu-id="cb3d4-p123">Результаты присваиваются в массив self.nodes и иерархия создается из объектов, с помощью linq.js присвоение массива self.heirarchy выходные данные. Этот массив — это объект, связанный с HTML-код. Для этого в функции toggleView(), передав собственный объект в функцию ko.applyBinding().</span><span class="sxs-lookup"><span data-stu-id="cb3d4-p123">The results are assigned to the self.nodes array and a hierarchy is built out of the objects using linq.js assigning the output to an array self.heirarchy. This array is the object that is bound to the HTML. This is done in the toggleView() function by passing the self object to the ko.applyBinding() function.</span></span><br/><span data-ttu-id="cb3d4-240">Затем в результате массив иерархии привязаны к следующий HTML-код:</span><span class="sxs-lookup"><span data-stu-id="cb3d4-240">This then causes the hierarchy array to be bound to the following HTML:</span></span><br/>

```
<div data-bind=”foreach: hierarchy” class=”noindex ms-core-listMenu-horizontalBox”>
```

<span data-ttu-id="cb3d4-241">Обработчики событий для `mouseenter` и `mouseexit` добавляются в панели навигации верхнего уровня для обработки раскрывающихся меню дочернего сайта, которых выполняется в `addEventsToElements()` функции.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-241">The event handlers for `mouseenter` and `mouseexit` are added to the top-level navigation to handle the subsite drop-down menus which is done in the `addEventsToElements()` function.</span></span>

<span data-ttu-id="cb3d4-242">В нашем примере сложных навигации это пустая страница загрузки без локального кэширования показано сократить время, затрачиваемое на сервере из структуры навигации тестирования производительности для получения следующий результат как подход управляемой навигации.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-242">In our complex navigation example, a fresh page load without the local caching shows the time spent on the server has been cut down from the benchmark structural navigation to get a similar result as the managed navigation approach.</span></span>

### <a name="about-the-javascript-file"></a><span data-ttu-id="cb3d4-243">Описание файла JavaScript...</span><span class="sxs-lookup"><span data-stu-id="cb3d4-243">About the JavaScript file...</span></span>

<span data-ttu-id="cb3d4-244">Полный JavaScript-файл выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="cb3d4-244">The entire JavaScript file is as follows:</span></span>

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
var query = baseUrl + "'contentClass=\"STS_Web\"+path:" + root + "'&trimduplicates=false&rowlimit=300";

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

            if (cachedNodes && timeStamp) {
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

            if (elem.children && elem.children.length > 0) {
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
      $("li.level1").mouseover(function () {
          var position = $(this).position();
          $(this).find("ul.level2").css({ width: 100, left: position.left + 10, top: 50 });
      })
   .mouseout(function () {
     $(this).find("ul.level2").css({  left: -99999, top: 0 });
   
    });
   
     $("li.level2").mouseover(function () {
          var position = $(this).position();
          console.log(JSON.stringify(position));
          $(this).find("ul.level3").css({ width: 100, left: position.left + 95, top:  position.top});
      })
   .mouseout(function () {
     $(this).find("ul.level3").css({  left: -99999, top: 0 });
    });
} _spBodyOnLoadFunctionNames.push("InitCustomNav");

``` 

<span data-ttu-id="cb3d4-p124">В целом приведенный выше в `jQuery $(document).ready` функции существует `viewModel object` создан и затем `loadNavigationNodes()` вызове функции для этого объекта. Эта функция загружает либо иерархии построенные навигации, хранящиеся в локальном хранилище HTML5 в клиентском браузере или вызывает функцию `queryRemoteInterface()`.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-p124">To summarize the code shown above in the `jQuery $(document).ready` function there is a `viewModel object` created and then the `loadNavigationNodes()` function on that object is called. This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function `queryRemoteInterface()`.</span></span>

<span data-ttu-id="cb3d4-p125">`QueryRemoteInterface()`выполняет построение запроса с помощью `getRequest()` функция с параметром запроса определенного ранее в сценарии и возвращает данные с сервера. Эти данные — это по сути массив всех сайтов в семействе сайтов, представленные в виде объектов передачи данных с различными свойствами.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-p125">`QueryRemoteInterface()` builds a request using the `getRequest()` function with the query parameter defined earlier in the script and then returns data from the server. This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties.</span></span> 

<span data-ttu-id="cb3d4-249">Затем анализируется эти данные в ранее заданных `SPO.Models.NavigationNode` объекты, которые используют `Knockout.js` Создание наблюдаемых свойств, используемых с привязки значения в HTML, которое было определено ранее данных.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-249">This data is then parsed into the previously defined `SPO.Models.NavigationNode` objects which use `Knockout.js` to create observable properties for use by data binding the values into the HTML that we defined earlier.</span></span> 

<span data-ttu-id="cb3d4-p126">Затем объекты помещаются в массиве результатов. Этот массив синтаксический анализ в JSON, с помощью выход и сохраняются в хранилище локального браузера для улучшения производительности в загрузке будущих страницы.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-p126">The objects are then put into a results array. This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads.</span></span>

### <a name="benefits-of-this-approach"></a><span data-ttu-id="cb3d4-252">Преимущества этого подхода</span><span class="sxs-lookup"><span data-stu-id="cb3d4-252">Benefits of this approach</span></span>

<span data-ttu-id="cb3d4-p127">Одно из основных преимуществ [этого подхода](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) —, что с помощью локальное хранилище HTML5 панели навигации хранится локально для пользователя при последующем их загрузки страницы. Повышение производительности основных, полученных от с помощью API поиска для структуры навигации; Тем не менее требуемое Техническая возможность выполнения и настроить эту функцию.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-p127">One major benefit of [this approach](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) is that by using HTML5 local storage, the navigation is stored locally for the user the next time they load the page. We get major performance improvements from using the search API for structural navigation; however, it takes some technical capability to execute and customize this functionality.</span></span> 

<span data-ttu-id="cb3d4-p128">[Пример реализации](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)сайты упорядочены в так же, как структуры навигации ожидания введите; алфавитном порядке. Если вы хотите отклоняются от этой порядке, было бы более сложный для разработки и обслуживания. Кроме того этот подход требует отклоняются от поддерживаемых главных страниц. Если настраиваемой главной страницы не поддерживаются, веб-узла будет пропуска из внимания обновлений и улучшений, корпорация Майкрософт дает главных страницах.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-p128">In the [example implementation](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), the sites are ordered in the same way as the out-of-the-box structural navigation; alphabetical order. If you wanted to deviate from this order, it would be more complicated to develop and maintain. Also, this approach requires you to deviate from the supported master pages. If the custom master page is not maintained, your site will miss out on updates and improvements that Microsoft makes to the master pages.</span></span>

<span data-ttu-id="cb3d4-259">[Над кода](#about-the-javascript-file) имеет следующие зависимости:</span><span class="sxs-lookup"><span data-stu-id="cb3d4-259">The [above code](#about-the-javascript-file) has the following dependencies:</span></span>

- <span data-ttu-id="cb3d4-260">jQuery-http://jquery.com/</span><span class="sxs-lookup"><span data-stu-id="cb3d4-260">jQuery - http://jquery.com/</span></span>
- <span data-ttu-id="cb3d4-261">KnockoutJS-http://knockoutjs.com/</span><span class="sxs-lookup"><span data-stu-id="cb3d4-261">KnockoutJS - http://knockoutjs.com/</span></span>
- <span data-ttu-id="cb3d4-262">LINQ.js - http://linqjs.codeplex.com/, или github.com/neuecc/linq.js</span><span class="sxs-lookup"><span data-stu-id="cb3d4-262">Linq.js - http://linqjs.codeplex.com/, or github.com/neuecc/linq.js</span></span>

<span data-ttu-id="cb3d4-p129">Текущая версия LinqJS не содержит метод ByHierarchy, используемый в предыдущем примере кода и нарушит работу кода навигации. Чтобы устранить эту проблему, добавьте следующий метод в файл Linq.js перед строкой `Flatten: function ()`.</span><span class="sxs-lookup"><span data-stu-id="cb3d4-p129">The current version of LinqJS does not contain the ByHierarchy method used in the above code and will break the navigation code. To fix this, add the following method to the Linq.js file before the line `Flatten: function ()`.</span></span>

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
  
## <a name="related-topics"></a><span data-ttu-id="cb3d4-265">Смежные темы</span><span class="sxs-lookup"><span data-stu-id="cb3d4-265">Related topics</span></span>

[<span data-ttu-id="cb3d4-266">Обзор управляемой навигации в SharePoint Server</span><span class="sxs-lookup"><span data-stu-id="cb3d4-266">Overview of managed navigation in SharePoint Server</span></span>](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)

