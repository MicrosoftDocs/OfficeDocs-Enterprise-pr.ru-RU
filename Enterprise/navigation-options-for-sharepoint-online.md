---
title: Параметры навигации для SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: В этой статье описываются параметры навигации сайтов с включенной публикацией SharePoint в SharePoint Online. Выбор и настройка навигации значительно влияют на производительность и масштабируемость сайтов в SharePoint Online.
ms.openlocfilehash: 9bf2010000f14b173b63574fab4ee77cb772b3f4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069945"
---
# <a name="navigation-options-for-sharepoint-online"></a><span data-ttu-id="bafb0-104">Параметры навигации для SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bafb0-104">Navigation options for SharePoint Online</span></span>

<span data-ttu-id="bafb0-105">В этой статье описываются параметры навигации сайтов с включенной публикацией SharePoint в SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="bafb0-105">This article describes navigation options sites with SharePoint Publishing enabled in SharePoint Online.</span></span> <span data-ttu-id="bafb0-106">Выбор и настройка навигации значительно влияют на производительность и масштабируемость сайтов в SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="bafb0-106">The choice and configuration of navigation significantly impacts the performance and scalability of sites in SharePoint Online.</span></span>

## <a name="overview"></a><span data-ttu-id="bafb0-107">Обзор</span><span class="sxs-lookup"><span data-stu-id="bafb0-107">Overview</span></span>

<span data-ttu-id="bafb0-108">Конфигурация поставщика навигации может значительно повлиять на производительность всего сайта, поэтому следует тщательно продумать, чтобы выбрать поставщика навигации и конфигурацию, которая эффективно масштабируется для требований сайта SharePoint.</span><span class="sxs-lookup"><span data-stu-id="bafb0-108">Navigation provider configuration can significantly impact performance for the entire site, and careful consideration must be taken to pick a navigation provider and configuration that scales effectively for the requirements of a SharePoint site.</span></span> <span data-ttu-id="bafb0-109">Существует два встроенных поставщика навигации, а также пользовательские реализации навигации.</span><span class="sxs-lookup"><span data-stu-id="bafb0-109">There are two out-of-the-box navigation providers, as well as custom navigation implementations.</span></span>

<span data-ttu-id="bafb0-110">Первым вариантом является [**управляемая (Metadata) Навигация**](#using-managed-navigation-and-metadata-in-sharepoint-online), рекомендуемая и является одним из параметров по умолчанию в SharePoint Online; Однако рекомендуется отключить фильтрацию по ролям безопасности, если это не требуется.</span><span class="sxs-lookup"><span data-stu-id="bafb0-110">The first option, [**Managed (Metadata) navigation**](#using-managed-navigation-and-metadata-in-sharepoint-online), is recommended, and is one of the default options in SharePoint Online; however, we recommend that security trimming be disabled unless required.</span></span> <span data-ttu-id="bafb0-111">Фильтрация по ролям безопасности включена по умолчанию для этого поставщика навигации; Однако многие сайты не требуют дополнительных затрат на фильтрацию по ролям безопасности, так как элементы навигации часто являются согласованными для всех пользователей сайта.</span><span class="sxs-lookup"><span data-stu-id="bafb0-111">Security trimming is enabled as a secure-by-default setting for this navigation provider; however, many sites do not require the overhead of security trimming since navigation elements often are consistent for all users of the site.</span></span> <span data-ttu-id="bafb0-112">С рекомендуемой конфигурацией для отключения фильтрации по ролям безопасности этот поставщик навигации не нуждается в перечислении структуры сайта и имеет высокую масштабируемость с приемлемым влиянием на производительность.</span><span class="sxs-lookup"><span data-stu-id="bafb0-112">With the recommended configuration to disable security trimming, this navigation provider does not require enumerating site structure and is highly scalable with acceptable performance impact.</span></span>

<span data-ttu-id="bafb0-113">Второй параметр, [**структурная навигация**](#using-structural-navigation-in-sharepoint-online), **не является рекомендуемым параметром навигации в SharePoint Online**.</span><span class="sxs-lookup"><span data-stu-id="bafb0-113">The second option, [**Structural navigation**](#using-structural-navigation-in-sharepoint-online), **is NOT a recommended navigation option in SharePoint Online**.</span></span> <span data-ttu-id="bafb0-114">Этот поставщик навигации был разработан для локальной топологии и обладает ограниченной поддержкой в SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="bafb0-114">This navigation provider was designed for an on-premises topology has limited support in SharePoint Online.</span></span> <span data-ttu-id="bafb0-115">При этом предоставляется дополнительный набор возможностей и другие параметры навигации, эти функции, включая фильтрацию по ролям безопасности и перечисление структуры сайта, поступают за счет избыточных вызовов сервера и влияют на масштабируемость и производительность при использовании.</span><span class="sxs-lookup"><span data-stu-id="bafb0-115">While it provides some additional set of capabilities versus other navigation options, these features, including security trimming and site structure enumeration, comes at a cost of excessive server calls and impacts scalability and performance when it is used.</span></span> <span data-ttu-id="bafb0-116">Сайты, использующие структурную навигацию, которые потребляют чрезмерные ресурсы, могут подвергаться регулированиям.</span><span class="sxs-lookup"><span data-stu-id="bafb0-116">Sites using structed navigation that consume excessive resources may be subject to throttling.</span></span>

<span data-ttu-id="bafb0-117">В дополнение к встроенным поставщикам навигации многие клиенты успешно реализовали альтернативные реализации пользовательских переходов.</span><span class="sxs-lookup"><span data-stu-id="bafb0-117">In addition to the out-of-the-box navigation providers, many customers have successfully implemented alternative custom navigation implementations.</span></span> <span data-ttu-id="bafb0-118">Один из распространенных классов реализации пользовательских переходов применяет к просмотру клиентские шаблоны, которые хранят локальный кэш узлов навигации.</span><span class="sxs-lookup"><span data-stu-id="bafb0-118">One common class of custom navigation implementations embraces client-rendered design patterns that store a local cache of navigation nodes.</span></span> <span data-ttu-id="bafb0-119">(В этой статье вы найдете **[сценарии на основе поиска на стороне клиента](#using-search-driven-client-side-scripting)** .)</span><span class="sxs-lookup"><span data-stu-id="bafb0-119">(See **[Search-driven client-side scripting](#using-search-driven-client-side-scripting)** in this article.)</span></span>

<span data-ttu-id="bafb0-120">Эти поставщики навигации имеют несколько ключевых преимуществ:</span><span class="sxs-lookup"><span data-stu-id="bafb0-120">These navigation providers have a couple of key advantages:</span></span> 
- <span data-ttu-id="bafb0-121">Как правило, они хорошо работают с откликом от макетов страниц.</span><span class="sxs-lookup"><span data-stu-id="bafb0-121">They generally work well with responsive page designs.</span></span>
- <span data-ttu-id="bafb0-122">Они чрезвычайно масштабируемыми и выполняемыми, так как они могут отображаться без затрат на ресурсы (и обновлять в фоновом режиме после истечения времени ожидания).</span><span class="sxs-lookup"><span data-stu-id="bafb0-122">They are extremely scalable and performant because they can render with no resource cost (and refresh in the background after a timeout).</span></span> 
- <span data-ttu-id="bafb0-123">Эти поставщики навигации могут получать данные навигации с помощью различных стратегий, начиная от простых статических конфигураций к различным поставщикам динамических данных.</span><span class="sxs-lookup"><span data-stu-id="bafb0-123">These navigation providers can retrieve navigation data using various strategies, ranging from simple static configurations to various dynamic data providers.</span></span> 

<span data-ttu-id="bafb0-124">В качестве примера поставщика данных можно использовать навигацию на **основе поиска**, что обеспечивает гибкость для перечисления узлов навигации и эффективного обработки фильтрации по ролям безопасности.</span><span class="sxs-lookup"><span data-stu-id="bafb0-124">An example of a data provider is to use a **Search-driven navigation**, which allows flexibility for enumerating navigation nodes and handling security trimming efficiently.</span></span> 

<span data-ttu-id="bafb0-125">Существуют и другие популярные возможности для создания **пользовательских поставщиков навигации**.</span><span class="sxs-lookup"><span data-stu-id="bafb0-125">There are other popular options to build **Custom navigation providers**.</span></span> <span data-ttu-id="bafb0-126">Ознакомьтесь с [решениями навигации для порталов SharePoint Online](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) , чтобы получить дополнительные рекомендации по созданию настраиваемого поставщика навигации.</span><span class="sxs-lookup"><span data-stu-id="bafb0-126">Please review [Navigation solutions for SharePoint Online portals](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) for further guidance on building a Custom navigation provider.</span></span>
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a><span data-ttu-id="bafb0-127">Преимущества и недостатки параметров навигации SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bafb0-127">Pros and Cons of SharePoint Online navigation options</span></span>

<span data-ttu-id="bafb0-128">В следующей таблице обобщены преимущества и недостатки каждого из вариантов.</span><span class="sxs-lookup"><span data-stu-id="bafb0-128">The following table summarizes the pros and cons of each option.</span></span> 


|<span data-ttu-id="bafb0-129">Управляемая навигация</span><span class="sxs-lookup"><span data-stu-id="bafb0-129">Managed navigation</span></span>  |<span data-ttu-id="bafb0-130">Структурная навигация</span><span class="sxs-lookup"><span data-stu-id="bafb0-130">Structural navigation</span></span>  |<span data-ttu-id="bafb0-131">Навигация на основе поиска</span><span class="sxs-lookup"><span data-stu-id="bafb0-131">Search-driven navigation</span></span>  |<span data-ttu-id="bafb0-132">Поставщик настраиваемой навигации</span><span class="sxs-lookup"><span data-stu-id="bafb0-132">Custom-navigation provider</span></span>  |
|---------|---------|---------|---------|
|<span data-ttu-id="bafb0-133">Технология</span><span class="sxs-lookup"><span data-stu-id="bafb0-133">Pros:</span></span><br/><br/><span data-ttu-id="bafb0-134">Простота обслуживания</span><span class="sxs-lookup"><span data-stu-id="bafb0-134">Easy to maintain</span></span><br/><span data-ttu-id="bafb0-135">Рекомендуемый вариант</span><span class="sxs-lookup"><span data-stu-id="bafb0-135">Recommended option</span></span><br/>     |<span data-ttu-id="bafb0-136">Технология</span><span class="sxs-lookup"><span data-stu-id="bafb0-136">Pros:</span></span><br/><br/><span data-ttu-id="bafb0-137">Простота настройки</span><span class="sxs-lookup"><span data-stu-id="bafb0-137">Easy to configure</span></span><br/><span data-ttu-id="bafb0-138">Фильтрация по ролям безопасности</span><span class="sxs-lookup"><span data-stu-id="bafb0-138">Security trimmed</span></span><br/><span data-ttu-id="bafb0-139">Автоматически обновляется при добавлении контента</span><span class="sxs-lookup"><span data-stu-id="bafb0-139">Automatically updates as content is added</span></span><br/>|<span data-ttu-id="bafb0-140">Технология</span><span class="sxs-lookup"><span data-stu-id="bafb0-140">Pros:</span></span><br/><br/><span data-ttu-id="bafb0-141">Фильтрация по ролям безопасности</span><span class="sxs-lookup"><span data-stu-id="bafb0-141">Security trimmed</span></span><br/><span data-ttu-id="bafb0-142">Автоматически обновляются при добавлении сайтов</span><span class="sxs-lookup"><span data-stu-id="bafb0-142">Automatically updates as sites are added</span></span><br/><span data-ttu-id="bafb0-143">Время быстрой загрузки и локально кэшированная структура навигации</span><span class="sxs-lookup"><span data-stu-id="bafb0-143">Fast loading time and locally cached navigation structure</span></span><br/>|<span data-ttu-id="bafb0-144">Технология</span><span class="sxs-lookup"><span data-stu-id="bafb0-144">Pros:</span></span><br/><br/><span data-ttu-id="bafb0-145">Широкий выбор доступных параметров</span><span class="sxs-lookup"><span data-stu-id="bafb0-145">Wider choice of options available</span></span><br/><span data-ttu-id="bafb0-146">Быстрая загрузка при правильном использовании кэширования</span><span class="sxs-lookup"><span data-stu-id="bafb0-146">Fast loading when caching is used correctly</span></span><br/><span data-ttu-id="bafb0-147">Многие параметры хорошо подходят для страниц с откликом</span><span class="sxs-lookup"><span data-stu-id="bafb0-147">Many options work well with responsive page design</span></span><br/>|
|<span data-ttu-id="bafb0-148">Недостатк</span><span class="sxs-lookup"><span data-stu-id="bafb0-148">Cons:</span></span><br/><br/><span data-ttu-id="bafb0-149">Не обновляется автоматически с учетом структуры сайта</span><span class="sxs-lookup"><span data-stu-id="bafb0-149">Not automatically updated to reflect site structure</span></span><br/><span data-ttu-id="bafb0-150">Влияет на производительность, если включена фильтрация по ролям безопасности</span><span class="sxs-lookup"><span data-stu-id="bafb0-150">Impacts performance if security trimming is enabled</span></span><br/>|<span data-ttu-id="bafb0-151">Недостатк</span><span class="sxs-lookup"><span data-stu-id="bafb0-151">Cons:</span></span><br/><br/><span data-ttu-id="bafb0-152">**Не рекомендуется**</span><span class="sxs-lookup"><span data-stu-id="bafb0-152">**Not recommended**</span></span><br/><span data-ttu-id="bafb0-153">**Влияет на производительность и масштабируемость**</span><span class="sxs-lookup"><span data-stu-id="bafb0-153">**Impacts performance and scalability**</span></span><br/><span data-ttu-id="bafb0-154">**Тема регулирования**</span><span class="sxs-lookup"><span data-stu-id="bafb0-154">**Subject to throttling**</span></span><br/>|<span data-ttu-id="bafb0-155">Недостатк</span><span class="sxs-lookup"><span data-stu-id="bafb0-155">Cons:</span></span><br/><br/><span data-ttu-id="bafb0-156">Нет возможности легко упорядочивать сайты</span><span class="sxs-lookup"><span data-stu-id="bafb0-156">No ability to easily order sites</span></span><br/><span data-ttu-id="bafb0-157">Требует настройки эталонной страницы (требуются технические навыки)</span><span class="sxs-lookup"><span data-stu-id="bafb0-157">Requires customization of the master page (technical skills required)</span></span><br/>|<span data-ttu-id="bafb0-158">Недостатк</span><span class="sxs-lookup"><span data-stu-id="bafb0-158">Cons:</span></span><br/><br/><span data-ttu-id="bafb0-159">Необходима настраиваемая разработка</span><span class="sxs-lookup"><span data-stu-id="bafb0-159">Custom development is required</span></span><br/><span data-ttu-id="bafb0-160">Необходимо хранить внешний источник данных/кэш, например Azure</span><span class="sxs-lookup"><span data-stu-id="bafb0-160">External data source / cache stored is needed e.g. Azure</span></span><br/>|

<span data-ttu-id="bafb0-161">Наиболее подходящий вариант для сайта будет зависеть от требований к сайту и технической возможности.</span><span class="sxs-lookup"><span data-stu-id="bafb0-161">The most appropriate option for your site will depend on your site requirements and on your technical capability.</span></span> <span data-ttu-id="bafb0-162">Если требуется масштабируемый встроенный поставщик навигации, то управляемая Навигация с отключенной фильтрацией по ролям безопасности является очень хорошим вариантом.</span><span class="sxs-lookup"><span data-stu-id="bafb0-162">If you want a scalable out-of-the-box navigation provider, then Managed navigation with security trimming disabled is a very good option.</span></span> 

<span data-ttu-id="bafb0-163">Управляемую навигацию можно поддерживать с помощью настройки, но не включает файлы настройки кода и значительно быстрее, чем при структурной навигации.</span><span class="sxs-lookup"><span data-stu-id="bafb0-163">The Managed navigation option can be maintained through configuration, does not involve code customization files, and it is significantly faster than structural navigation.</span></span> <span data-ttu-id="bafb0-164">Если требуется фильтрация по ролям безопасности и удобнее использовать настраиваемую эталонную страницу и иметь некоторые возможности в Организации для поддержки изменений, которые могут возникнуть на главной странице по умолчанию для SharePoint Online, то функция на основе поиска может улучшить взаимодействие с пользователем.</span><span class="sxs-lookup"><span data-stu-id="bafb0-164">If you require security trimming and are comfortable using a custom master page and have some capability in the organization to maintain the changes that may occur in the default master page for SharePoint Online, then the Search-driven option may produce a better user experience.</span></span> <span data-ttu-id="bafb0-165">При наличии более сложных требований можно выбрать подходящий поставщик навигации.</span><span class="sxs-lookup"><span data-stu-id="bafb0-165">If you have more complex requirements, then a custom navigation provider may be the right choice.</span></span> <span data-ttu-id="bafb0-166">НЕ рекомендуется использовать структурную навигацию.</span><span class="sxs-lookup"><span data-stu-id="bafb0-166">Structural navigation is NOT recommended.</span></span>

<span data-ttu-id="bafb0-167">Наконец, обратите внимание, что SharePoint добавляет дополнительных поставщиков навигации и функций для современных архитектур сайтов SharePoint, использующих более плоскую иерархию сайтов и Центрально-лучевую модель с центральными сайтами SharePoint.</span><span class="sxs-lookup"><span data-stu-id="bafb0-167">Finally, it’s important to note that SharePoint is adding additional navigation providers and functionality for modern SharePoint site architectures leveraging a more flattened site hierarchy and a hub-and-spoke model with SharePoint hub sites.</span></span> <span data-ttu-id="bafb0-168">Это позволяет добиться многих сценариев, для которых не требуется использовать функцию публикации SharePoint, и эти конфигурации навигации оптимизированы для обеспечения масштабируемости и задержки в SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="bafb0-168">This allows many scenarios to be achieved that do NOT require the use of SharePoint Publishing feature, and these navigation configurations are optimized for scalability and latency within SharePoint Online.</span></span> <span data-ttu-id="bafb0-169">Обратите внимание, что применение того же принципа — упрощение общей структуры сайта публикации SharePoint до структуры плоская часто способствует общей производительности и масштабируемости.</span><span class="sxs-lookup"><span data-stu-id="bafb0-169">Note that applying the same principle - simplifying the overall structure of your SharePoint Publishing site to a flatter structure, often helps with overall performance and scale as well.</span></span> <span data-ttu-id="bafb0-170">Это означает, что вместо одного семейства веб-сайтов с сотнями сайтов (дочерние веб-сайты) лучшим подходом будет наличие большого числа семейств веб-сайтов с очень малой дочерними сайтами (дочерние веб-сайты).</span><span class="sxs-lookup"><span data-stu-id="bafb0-170">What this means is that instead of having a single Site Collection with hundreds of sites (subwebs), a better approach is to have many site collections with very few subsites (subwebs).</span></span>


## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a><span data-ttu-id="bafb0-171">Использование управляемой навигации и метаданных в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bafb0-171">Using managed navigation and metadata in SharePoint Online</span></span>

<span data-ttu-id="bafb0-172">Управляемая Навигация — это еще один встроенный параметр, который можно использовать для повторного создания большей части функций с структурной навигацией.</span><span class="sxs-lookup"><span data-stu-id="bafb0-172">Managed navigation is another out-of-the-box option that you can use to recreate most of the same functionality as structural navigation.</span></span> <span data-ttu-id="bafb0-173">Управляемые метаданные можно настроить так, чтобы фильтрация по ролям безопасности была включена или отключена.</span><span class="sxs-lookup"><span data-stu-id="bafb0-173">Managed metadata can be configured to have security trimming enabled or disabled.</span></span> <span data-ttu-id="bafb0-174">Если фильтрация по ролям безопасности отключена, управляемая Навигация довольно эффективна, так как она загружает все навигационные ссылки с постоянным числом вызовов сервера.</span><span class="sxs-lookup"><span data-stu-id="bafb0-174">When configured with security trimming disabled, managed navigation is fairly efficient as it loads all the navigation links with a constant number of server calls.</span></span> <span data-ttu-id="bafb0-175">Однако включение фильтрации по ролям безопасности отменяет некоторые преимущества управляемой навигации, а клиенты могут рассмотреть одно из пользовательских решений навигации, чтобы обеспечить оптимальную производительность и масштабируемость.</span><span class="sxs-lookup"><span data-stu-id="bafb0-175">Enabling security trimming, however, negates some of the advantages of managed navigation, and customers may choose to explore one of the custom navigation solutions for optimal performance and scalability.</span></span>

<span data-ttu-id="bafb0-176">Многие сайты не нуждаются в фильтрации по ролям безопасности, так как структура навигации часто согласована для всех пользователей сайта.</span><span class="sxs-lookup"><span data-stu-id="bafb0-176">Many sites do not require security trimming, as the navigation structure is often consistent for all users of the site.</span></span> <span data-ttu-id="bafb0-177">Если фильтрация по ролям безопасности отключена и ссылка добавлена на навигацию, к которой у всех пользователей есть доступ, ссылка по-прежнему будет отображаться, но будет вызывать сообщение об отказе в доступе.</span><span class="sxs-lookup"><span data-stu-id="bafb0-177">If security trimming is disabled and a link is added to navigation that not all users have access to, the link will still show but will lead to an access denied message.</span></span> <span data-ttu-id="bafb0-178">Нет риска случайного доступа к содержимому.</span><span class="sxs-lookup"><span data-stu-id="bafb0-178">There is no risk of inadvertent access to the content.</span></span>

### <a name="how-to-implement-managed-navigation-and-the-results"></a><span data-ttu-id="bafb0-179">Как реализовать управляемую навигацию и результаты</span><span class="sxs-lookup"><span data-stu-id="bafb0-179">How to implement managed navigation and the results</span></span>

<span data-ttu-id="bafb0-180">В Docs.Microsoft.com содержатся несколько статей, посвященных управлению навигацией, например [Обзор управляемой навигации в SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span><span class="sxs-lookup"><span data-stu-id="bafb0-180">There are several articles on Docs.Microsoft.com about the details of managed navigation, for example, see [Overview of managed navigation in SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span></span>

<span data-ttu-id="bafb0-181">Чтобы реализовать управляемую навигацию, вы можете настроить термины с URL-адресами, соответствующими структуре навигации сайта.</span><span class="sxs-lookup"><span data-stu-id="bafb0-181">In order to implement managed navigation, you set up terms with URLs corresponding to the navigation structure of  the site.</span></span> <span data-ttu-id="bafb0-182">Управляемую навигацию можно также выполнить вручную, чтобы заменить структурную навигацию во многих случаях.</span><span class="sxs-lookup"><span data-stu-id="bafb0-182">Managed navigation can even be manually curated to replace structural navigation in many cases.</span></span> <span data-ttu-id="bafb0-183">Примеры:</span><span class="sxs-lookup"><span data-stu-id="bafb0-183">For example:</span></span>

![Структура сайта SharePoint Online](media/SPONavOptionsListOfSites.png)

<span data-ttu-id="bafb0-185">В следующем примере показана производительность сложной навигации с помощью управляемой навигации.</span><span class="sxs-lookup"><span data-stu-id="bafb0-185">The following example shows the performance of the complex navigation using managed navigation.</span></span>

![Производительность сложной навигации с помощью управляемой навигации](media/SPONavOptionsComplexNavPerf.png)

<span data-ttu-id="bafb0-187">Использование управляемой навигации согласованно повышает производительность по сравнению с подходом структурной навигации.</span><span class="sxs-lookup"><span data-stu-id="bafb0-187">Using managed navigation consistently improves performance compared to the structural navigation approach.</span></span>
  
## <a name="using-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="bafb0-188">Использование структурной навигации в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bafb0-188">Using structural navigation in SharePoint Online</span></span>

<span data-ttu-id="bafb0-189">Это встроенная Навигация, используемая по умолчанию и которая является самым простым решением, но так как это приводит к дорогостоящему снижению производительности.</span><span class="sxs-lookup"><span data-stu-id="bafb0-189">This is the out-of-the-box navigation used by default and is the most straightforward solution but as such has an expensive performance trade-off.</span></span> <span data-ttu-id="bafb0-190">Для него не требуется никаких настроек, и пользователь, не являющийся техническим, может легко добавлять элементы, скрывать элементы и управлять навигацией на странице "Параметры".</span><span class="sxs-lookup"><span data-stu-id="bafb0-190">It does not require any customization and a non-technical user can also easily add items, hide items, and manage the navigation from the settings page.</span></span> <span data-ttu-id="bafb0-191">Кроме того, это справедливо для управляемой навигации, поэтому рекомендуется использовать управляемую навигацию, так как ее можно легко управлять и контролировать, а также повысить производительность.</span><span class="sxs-lookup"><span data-stu-id="bafb0-191">This is however also true for Managed Navigation so it is recommended to use Managed Navigation as that can also be easily managed and controlled as well with improved performance.</span></span>

![Структурная навигация с выбранными дочерними сайтами](media/SPONavOptionsStructuredShowSubsites.png)
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="bafb0-193">Включение структурной навигации в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bafb0-193">Turning on structural navigation in SharePoint Online</span></span>

<span data-ttu-id="bafb0-194">Чтобы продемонстрировать, как работает стандартное решение SharePoint Online с структурной навигацией и включенным параметром Показать дочерние сайты.</span><span class="sxs-lookup"><span data-stu-id="bafb0-194">To illustrate how the performance in a standard SharePoint Online solution with structural navigation and the show subsites option turned on.</span></span> <span data-ttu-id="bafb0-195">Ниже приведен снимок экрана параметров, найденных в \> **навигации**по **параметрам сайта** страницы.</span><span class="sxs-lookup"><span data-stu-id="bafb0-195">Below is a screenshot of settings found on the page **Site Settings** \> **Navigation**.</span></span>
  
![Снимок экрана: дочерние сайты](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a><span data-ttu-id="bafb0-197">Анализ производительности структурной навигации в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bafb0-197">Analyzing structural navigation performance in SharePoint Online</span></span>

<span data-ttu-id="bafb0-198">Чтобы проанализировать производительность страницы SharePoint, используйте вкладку **сеть** средств разработчика F12 в Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="bafb0-198">To analyze the performance of a SharePoint page, use the **Network** tab of the F12 developer tools in Internet Explorer.</span></span> 
  
![Снимок экрана: вкладка "Сеть", отображенная после вызова средств разработчика (F12)](media/SPONavOptionsNetworks.png)
  
1. <span data-ttu-id="bafb0-200">На вкладке **сеть** щелкните загружается ASPX-страницу, а затем щелкните вкладку **сведения** .</span><span class="sxs-lookup"><span data-stu-id="bafb0-200">On the **Network** tab, click on the .aspx page that is being loaded and then click on the **Details** tab.</span></span><br/> <span data-ttu-id="bafb0-201">![Снимок экрана: вкладка "Сведения"](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span><span class="sxs-lookup"><span data-stu-id="bafb0-201">![Screenshot showing the details tab](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span></span><br/>
2. <span data-ttu-id="bafb0-202">Щелкните **заголовки ответа**.</span><span class="sxs-lookup"><span data-stu-id="bafb0-202">Click **Response headers**.</span></span> <br/><span data-ttu-id="bafb0-203">![Снимок экрана: вкладка "Сведения"](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span><span class="sxs-lookup"><span data-stu-id="bafb0-203">![Screenshot of Details tab](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span></span><br/><span data-ttu-id="bafb0-204">SharePoint возвращает некоторую полезную диагностическую информацию в заголовках откликов.</span><span class="sxs-lookup"><span data-stu-id="bafb0-204">SharePoint returns some useful diagnostic information in its response headers.</span></span> 
3. <span data-ttu-id="bafb0-205">Одним из наиболее удобных сведений является **SPRequestDuration** , который представляет собой значение (в миллисекундах) того, сколько времени занимает обработка запроса на сервере.</span><span class="sxs-lookup"><span data-stu-id="bafb0-205">One of the most useful pieces of information is **SPRequestDuration** which is the value, in milliseconds, of how long a request took to process on the server.</span></span> <span data-ttu-id="bafb0-206">На следующем снимке экрана **показаны дочерние сайты** , не отмеченные для структуры навигации.</span><span class="sxs-lookup"><span data-stu-id="bafb0-206">In the following screenshot **show subsites** is unchecked for the structural navigation.</span></span> <span data-ttu-id="bafb0-207">Это означает, что существует только ссылка на семейство веб-сайтов в глобальной структуре навигации:</span><span class="sxs-lookup"><span data-stu-id="bafb0-207">This means that there is only the site collection link in the global navigation:</span></span><br/><span data-ttu-id="bafb0-208">![Снимок экрана: время загрузки как время ответа на запрос](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span><span class="sxs-lookup"><span data-stu-id="bafb0-208">![Screenshot showing load times as request duration](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span></span><br/>
4. <span data-ttu-id="bafb0-209">Ключ **SPRequestDuration** имеет значение 245 миллисекунд.</span><span class="sxs-lookup"><span data-stu-id="bafb0-209">The **SPRequestDuration** key has a value of 245 milliseconds.</span></span> <span data-ttu-id="bafb0-210">Представляет время, затраченное на возврат запроса.</span><span class="sxs-lookup"><span data-stu-id="bafb0-210">This represents the time it took to return the request.</span></span> <span data-ttu-id="bafb0-211">Так как на сайте есть только один элемент навигации, это хороший тест, который выполняет SharePoint Online без высокой навигации.</span><span class="sxs-lookup"><span data-stu-id="bafb0-211">Since there is only one navigation item on the site, this is a good benchmark for how SharePoint Online performs without heavy navigation.</span></span> <span data-ttu-id="bafb0-212">На следующем снимке экрана показано, как добавление на дочерних сайтах влияет на этот ключ.</span><span class="sxs-lookup"><span data-stu-id="bafb0-212">The next screen shot shows how adding in the subsites affects this key.</span></span><br/><span data-ttu-id="bafb0-213">![Снимок экрана: длительность обработки запроса составляет 2502 мс](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span><span class="sxs-lookup"><span data-stu-id="bafb0-213">![Screenshot showing a request duration of 2502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span></span><br/>
  
<span data-ttu-id="bafb0-214">Добавление дочерних сайтов значительно увеличило время, необходимое для возврата запроса страницы для этого относительно простого примера сайта.</span><span class="sxs-lookup"><span data-stu-id="bafb0-214">Adding the subsites has significantly increased the time it takes to return the page request for this relatively simple sample site.</span></span> <span data-ttu-id="bafb0-215">Сложные иерархии сайтов, включая страницы в навигации, а также другие параметры конфигурации и топологии могут значительно увеличить это воздействие еще.</span><span class="sxs-lookup"><span data-stu-id="bafb0-215">Complex site hierarchies, including pages in navigation, and other configuration and topology options can dramatically increase this impact even further.</span></span>

## <a name="using-search-driven-client-side-scripting"></a><span data-ttu-id="bafb0-216">Использование скрипта на стороне клиента на основе поиска</span><span class="sxs-lookup"><span data-stu-id="bafb0-216">Using Search-driven client-side scripting</span></span>

<span data-ttu-id="bafb0-217">С помощью функции поиска можно использовать индексы, встроенные в фоновый режим с помощью непрерывного обхода.</span><span class="sxs-lookup"><span data-stu-id="bafb0-217">Using search you can leverage the indexes that are built up in the background using continuous crawl.</span></span> <span data-ttu-id="bafb0-218">Результаты поиска берутся из индекса поиска, и результаты отбрасываются с помощью средств безопасности.</span><span class="sxs-lookup"><span data-stu-id="bafb0-218">The search results are pulled from the search index and the results are security-trimmed.</span></span> <span data-ttu-id="bafb0-219">Как правило, это работает быстрее, чем готовые поставщики навигации, если фильтрация по ролям безопасности необходима.</span><span class="sxs-lookup"><span data-stu-id="bafb0-219">This is generally faster than out-of-the-box navigation providers when security trimming is required.</span></span> <span data-ttu-id="bafb0-220">С помощью функции поиска структурной навигации, особенно при наличии сложной структуры сайта, значительно ускоряется время загрузки страниц.</span><span class="sxs-lookup"><span data-stu-id="bafb0-220">Using search for structural navigation, especially if you have a complex site structure, will speed up page loading time considerably.</span></span> <span data-ttu-id="bafb0-221">Основное преимущество этого подхода к управляемой навигации заключается в преимуществах фильтрации по ролям безопасности.</span><span class="sxs-lookup"><span data-stu-id="bafb0-221">The main advantage of this over managed navigation is that you benefit from security trimming.</span></span>

<span data-ttu-id="bafb0-222">Такой подход включает создание настраиваемой эталонной страницы и замена встроенного кода навигации на пользовательский HTML-код.</span><span class="sxs-lookup"><span data-stu-id="bafb0-222">This approach involves creating a custom master page and replacing the out-of-the-box navigation code with custom HTML.</span></span> <span data-ttu-id="bafb0-223">Выполните эту процедуру, описанную в следующем примере, чтобы заменить код навигации в файле `seattle.html`.</span><span class="sxs-lookup"><span data-stu-id="bafb0-223">Follow this procedure outlined in the following example to replace the navigation code in the file `seattle.html`.</span></span> <span data-ttu-id="bafb0-224">В этом примере открывается `seattle.html` файл и заменяется весь элемент `id=”DeltaTopNavigation”` на пользовательский HTML-код.</span><span class="sxs-lookup"><span data-stu-id="bafb0-224">In this example, you will open the `seattle.html` file and replace the whole element `id=”DeltaTopNavigation”` with custom HTML code.</span></span>

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a><span data-ttu-id="bafb0-225">Пример: замена встроенного кода навигации на главной странице</span><span class="sxs-lookup"><span data-stu-id="bafb0-225">Example: Replace the out-of-the-box navigation code in a master page</span></span>

1.  <span data-ttu-id="bafb0-226">Перейдите на страницу Параметры сайта.</span><span class="sxs-lookup"><span data-stu-id="bafb0-226">Navigate to the Site Settings page.</span></span>
2.  <span data-ttu-id="bafb0-227">Откройте коллекцию главных страниц, щелкнув **эталонные страницы**.</span><span class="sxs-lookup"><span data-stu-id="bafb0-227">Open the master page gallery by clicking **Master Pages**.</span></span>
3.  <span data-ttu-id="bafb0-228">Отсюда вы можете перейти к библиотеке и скачать файл `seattle.master`.</span><span class="sxs-lookup"><span data-stu-id="bafb0-228">From here you can navigate through the library and download the file `seattle.master`.</span></span>
4.  <span data-ttu-id="bafb0-229">Измените код с помощью текстового редактора и удалите блок кода на следующем снимке экрана.</span><span class="sxs-lookup"><span data-stu-id="bafb0-229">Edit the code using a text editor and delete the code block in the following screen shot.</span></span><br/>![Удаление блока кода, показанного](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. <span data-ttu-id="bafb0-231">Удалите код между тегами `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` и `<\SharePoint:AjaxDelta>` замените его следующим фрагментом кода:</span><span class="sxs-lookup"><span data-stu-id="bafb0-231">Remove the code between the `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` and `<\SharePoint:AjaxDelta>` tags and replace it with the following snippet:</span></span><br/>

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
6. <span data-ttu-id="bafb0-232">Замените URL-адрес в открывающем теге привязки изображения на ссылку на загружаемое изображение в семействе веб-сайтов.</span><span class="sxs-lookup"><span data-stu-id="bafb0-232">Replace the URL in the loading image anchor tag at the beginning, with a link to a loading image in your site collection.</span></span> <span data-ttu-id="bafb0-233">После внесения изменений переименуйте файл и отправьте его в коллекцию главных страниц.</span><span class="sxs-lookup"><span data-stu-id="bafb0-233">After you have made the changes, rename the file and then upload it to the master page gallery.</span></span> <span data-ttu-id="bafb0-234">При этом создается новый главный файл.</span><span class="sxs-lookup"><span data-stu-id="bafb0-234">This generates a new .master file.</span></span><br/>
7. <span data-ttu-id="bafb0-235">Этот HTML-код представляет собой базовую разметку, которая будет заполнена результатами поиска, возвращаемыми из кода JavaScript.</span><span class="sxs-lookup"><span data-stu-id="bafb0-235">This HTML is the basic markup that will be populated by the search results returned from JavaScript code.</span></span> <span data-ttu-id="bafb0-236">Вам потребуется изменить код, чтобы изменить значение для параметра var root = "URL-адрес семейства веб-сайтов", как показано в следующем фрагменте кода:</span><span class="sxs-lookup"><span data-stu-id="bafb0-236">You will need to edit the code to change the value for var root = “site collection URL” as demonstrated in the following snippet:</span></span><br/>

```
var root = “https://spperformance.sharepoint.com/sites/NavigationBySearch”;
```
<br/>
8. <span data-ttu-id="bafb0-237">Результаты назначаются для массива "My. Nodes", а иерархия — из объектов, использующих LINQ. js, назначает выходные данные в виде массива.</span><span class="sxs-lookup"><span data-stu-id="bafb0-237">The results are assigned to the self.nodes array and a hierarchy is built out of the objects using linq.js assigning the output to an array self.hierarchy.</span></span> <span data-ttu-id="bafb0-238">Этот массив — это объект, связанный с HTML-кодом.</span><span class="sxs-lookup"><span data-stu-id="bafb0-238">This array is the object that is bound to the HTML.</span></span> <span data-ttu-id="bafb0-239">Для этого в функции Тогглевиев () необходимо передать сам объект в функцию KO. Апплибиндинг ().</span><span class="sxs-lookup"><span data-stu-id="bafb0-239">This is done in the toggleView() function by passing the self object to the ko.applyBinding() function.</span></span><br/><span data-ttu-id="bafb0-240">Это приводит к тому, что массив иерархии будет привязан к следующему HTML-коду:</span><span class="sxs-lookup"><span data-stu-id="bafb0-240">This then causes the hierarchy array to be bound to the following HTML:</span></span><br/>

```
<div data-bind=”foreach: hierarchy” class=”noindex ms-core-listMenu-horizontalBox”>
```

<span data-ttu-id="bafb0-241">Обработчики событий для `mouseenter` и `mouseexit` добавляются в навигацию верхнего уровня для обработки раскрывающихся меню дочернего сайта, выполняемых в `addEventsToElements()` функции.</span><span class="sxs-lookup"><span data-stu-id="bafb0-241">The event handlers for `mouseenter` and `mouseexit` are added to the top-level navigation to handle the subsite drop-down menus which is done in the `addEventsToElements()` function.</span></span>

<span data-ttu-id="bafb0-242">В нашем сложном примере навигации Новая загрузка страницы без локального кэширования показывает, что время, затраченное на работу сервера, было обрезано от структурной навигации, чтобы получить похожий результат в подходе управляемой навигации.</span><span class="sxs-lookup"><span data-stu-id="bafb0-242">In our complex navigation example, a fresh page load without the local caching shows the time spent on the server has been cut down from the benchmark structural navigation to get a similar result as the managed navigation approach.</span></span>

### <a name="about-the-javascript-file"></a><span data-ttu-id="bafb0-243">О файле JavaScript...</span><span class="sxs-lookup"><span data-stu-id="bafb0-243">About the JavaScript file...</span></span>

<span data-ttu-id="bafb0-244">Весь файл JavaScript выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="bafb0-244">The entire JavaScript file is as follows:</span></span>

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

<span data-ttu-id="bafb0-245">Чтобы обобщеть код, приведенный выше `jQuery $(document).ready` в функции, `viewModel object` создается, а затем вызывается `loadNavigationNodes()` функция для этого объекта.</span><span class="sxs-lookup"><span data-stu-id="bafb0-245">To summarize the code shown above in the `jQuery $(document).ready` function there is a `viewModel object` created and then the `loadNavigationNodes()` function on that object is called.</span></span> <span data-ttu-id="bafb0-246">Эта функция либо загружает ранее созданную иерархию навигации, хранящуюся в локальном хранилище HTML5 клиентского браузера, либо вызывает функцию `queryRemoteInterface()`.</span><span class="sxs-lookup"><span data-stu-id="bafb0-246">This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function `queryRemoteInterface()`.</span></span>

<span data-ttu-id="bafb0-247">`QueryRemoteInterface()`создает запрос с помощью `getRequest()` функции с параметром запроса, определенным ранее в сценарии, а затем возвращает данные с сервера.</span><span class="sxs-lookup"><span data-stu-id="bafb0-247">`QueryRemoteInterface()` builds a request using the `getRequest()` function with the query parameter defined earlier in the script and then returns data from the server.</span></span> <span data-ttu-id="bafb0-248">По сути, эти данные представляют собой массив всех сайтов в семействе веб-сайтов, представленных в виде объектов передачи данных с различными свойствами.</span><span class="sxs-lookup"><span data-stu-id="bafb0-248">This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties.</span></span> 

<span data-ttu-id="bafb0-249">Затем эти данные анализируются в ранее определенных `SPO.Models.NavigationNode` объектах, которые используются `Knockout.js` для создания наблюдаемых свойств для использования данными в коде HTML, который мы определили ранее.</span><span class="sxs-lookup"><span data-stu-id="bafb0-249">This data is then parsed into the previously defined `SPO.Models.NavigationNode` objects which use `Knockout.js` to create observable properties for use by data binding the values into the HTML that we defined earlier.</span></span> 

<span data-ttu-id="bafb0-250">Затем объекты помещаются в массив Results.</span><span class="sxs-lookup"><span data-stu-id="bafb0-250">The objects are then put into a results array.</span></span> <span data-ttu-id="bafb0-251">Этот массив разбивается на JSON с помощью функции маскирования и хранится в хранилище локального браузера для улучшения производительности при последующих загрузках страниц.</span><span class="sxs-lookup"><span data-stu-id="bafb0-251">This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads.</span></span>

### <a name="benefits-of-this-approach"></a><span data-ttu-id="bafb0-252">Преимущества этого подхода</span><span class="sxs-lookup"><span data-stu-id="bafb0-252">Benefits of this approach</span></span>

<span data-ttu-id="bafb0-253">Одним из основных преимуществ [этого подхода](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) является то, что с помощью ЛОКАЛЬНОГО хранилища HTML5 структура навигации хранится локально для пользователя при следующей загрузке страницы.</span><span class="sxs-lookup"><span data-stu-id="bafb0-253">One major benefit of [this approach](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) is that by using HTML5 local storage, the navigation is stored locally for the user the next time they load the page.</span></span> <span data-ttu-id="bafb0-254">Мы получаем значительные улучшения производительности при использовании API поиска для структурной навигации; Тем не менее, для выполнения и настройки этих функций требуется техническая поддержка.</span><span class="sxs-lookup"><span data-stu-id="bafb0-254">We get major performance improvements from using the search API for structural navigation; however, it takes some technical capability to execute and customize this functionality.</span></span> 

<span data-ttu-id="bafb0-255">В [примере реализации](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)сайты упорядочиваются так же, как и встроенная структурная навигация; Алфавитный порядок.</span><span class="sxs-lookup"><span data-stu-id="bafb0-255">In the [example implementation](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), the sites are ordered in the same way as the out-of-the-box structural navigation; alphabetical order.</span></span> <span data-ttu-id="bafb0-256">Если вы хотели бы отказываться от этого порядка, он был бы более сложным для разработки и обслуживания.</span><span class="sxs-lookup"><span data-stu-id="bafb0-256">If you wanted to deviate from this order, it would be more complicated to develop and maintain.</span></span> <span data-ttu-id="bafb0-257">Кроме того, этот подход требует отклонения от поддерживаемых эталонных страниц.</span><span class="sxs-lookup"><span data-stu-id="bafb0-257">Also, this approach requires you to deviate from the supported master pages.</span></span> <span data-ttu-id="bafb0-258">Если настраиваемая эталонная страница не поддерживается, ваш сайт будет проигнорирован при обновлениях и улучшениях, которые корпорация Майкрософт делает с эталонными страницами.</span><span class="sxs-lookup"><span data-stu-id="bafb0-258">If the custom master page is not maintained, your site will miss out on updates and improvements that Microsoft makes to the master pages.</span></span>

<span data-ttu-id="bafb0-259">[Приведенный выше код](#about-the-javascript-file) имеет следующие зависимости:</span><span class="sxs-lookup"><span data-stu-id="bafb0-259">The [above code](#about-the-javascript-file) has the following dependencies:</span></span>

- <span data-ttu-id="bafb0-260">jQueryhttp://jquery.com/</span><span class="sxs-lookup"><span data-stu-id="bafb0-260">jQuery - http://jquery.com/</span></span>
- <span data-ttu-id="bafb0-261">Кноккаутжс —http://knockoutjs.com/</span><span class="sxs-lookup"><span data-stu-id="bafb0-261">KnockoutJS - http://knockoutjs.com/</span></span>
- <span data-ttu-id="bafb0-262">LINQ. js — http://linqjs.codeplex.com/или GitHub.com/neuecc/LINQ.js</span><span class="sxs-lookup"><span data-stu-id="bafb0-262">Linq.js - http://linqjs.codeplex.com/, or github.com/neuecc/linq.js</span></span>

<span data-ttu-id="bafb0-263">Текущая версия Линкжс не содержит метод Бихиерарчи, используемый в приведенном выше коде, и нарушает код навигации.</span><span class="sxs-lookup"><span data-stu-id="bafb0-263">The current version of LinqJS does not contain the ByHierarchy method used in the above code and will break the navigation code.</span></span> <span data-ttu-id="bafb0-264">Чтобы устранить эту проблему, добавьте следующий метод в файл LINQ. js перед строкой `Flatten: function ()`.</span><span class="sxs-lookup"><span data-stu-id="bafb0-264">To fix this, add the following method to the Linq.js file before the line `Flatten: function ()`.</span></span>

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
  
## <a name="related-topics"></a><span data-ttu-id="bafb0-265">Статьи по теме</span><span class="sxs-lookup"><span data-stu-id="bafb0-265">Related topics</span></span>

[<span data-ttu-id="bafb0-266">Обзор управляемой навигации в SharePoint Server</span><span class="sxs-lookup"><span data-stu-id="bafb0-266">Overview of managed navigation in SharePoint Server</span></span>](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)

