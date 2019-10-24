---
title: Планирование развертывания портала для запуска в SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
description: В этой статье описывается, как можно спланировать запуск портала в SharePoint Online и какие действия предпринять для успешного запуска.
ms.openlocfilehash: 8985ffb4b477ee70f0bf35489ce48fd72f8e4c86
ms.sourcegitcommit: 739024fe2862ab646b36e218b57c5cc16ebe7892
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/08/2019
ms.locfileid: "37422164"
---
# <a name="planning-your-portal-launch-roll-out-plan-in-sharepoint-online"></a><span data-ttu-id="348da-103">Планирование развертывания портала для запуска в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="348da-103">Planning your portal launch roll-out plan in SharePoint Online</span></span>
<span data-ttu-id="348da-104">Портал — это сайт SharePoint по умолчанию для вашей компании; в крупных организациях может быть несколько из них.</span><span class="sxs-lookup"><span data-stu-id="348da-104">A portal is the default SharePoint site for your company; in large organizations there could be several of these.</span></span> <span data-ttu-id="348da-105">Если вы ожидали более 20% пользователей в вашей организации для доступа к странице, следует учесть, что страница портала.</span><span class="sxs-lookup"><span data-stu-id="348da-105">If you expect more than 20% of your users within your organization to access the page, you should consider that a portal page.</span></span> <span data-ttu-id="348da-106">Это не следует путать с сайтом группы, используемым в отделе для совместной совместной использования и совместного использования документов в команде.</span><span class="sxs-lookup"><span data-stu-id="348da-106">This shouldn't be confused with a team site your department uses to collaborate and share documents within your team.</span></span>

<span data-ttu-id="348da-107">В этой статье описано, как спланировать развертывание и развертывание плана в SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="348da-107">This article describes how to plan your deployment and roll-out plan to SharePoint Online.</span></span> <span data-ttu-id="348da-108">Кроме того, в SharePoint Online не разрешается соблюдение традиционных нагрузочного тестирования.</span><span class="sxs-lookup"><span data-stu-id="348da-108">It also provides approaches to follow as traditional load testing is not permitted on SharePoint Online.</span></span> <span data-ttu-id="348da-109">SharePoint Online — это облачная служба, которая управляет возможностями нагрузки, работоспособностью и общим балансом нагрузки в службе.</span><span class="sxs-lookup"><span data-stu-id="348da-109">SharePoint Online is a cloud service and the load capabilities, health and overall balance of load in the service are managed by Microsoft.</span></span>

<span data-ttu-id="348da-110">Для создания успешного портала следуйте основным принципам, рекомендациям и рекомендациям, описанным в разделе [Создание, запуск и обслуживание работоспособного портала](https://go.microsoft.com/fwlink/?linkid=2105838) .</span><span class="sxs-lookup"><span data-stu-id="348da-110">To help in creating a successful portal, follow the basic principles, practices and recommendations detailed in the [Creating, launching and maintaining a healthy portal](https://go.microsoft.com/fwlink/?linkid=2105838)</span></span> 

<span data-ttu-id="348da-111">Подход к развертыванию выделен ниже.</span><span class="sxs-lookup"><span data-stu-id="348da-111">The deployment approach is highlighted below.</span></span>

## <a name="overview-of-capacity-planning-in-sharepoint-online"></a><span data-ttu-id="348da-112">Обзор планирования мощности в SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="348da-112">Overview of capacity planning in SharePoint Online</span></span>
<span data-ttu-id="348da-113">Чтобы эффективно использовать возможности и работать с непредвиденным ростом, в любой ферме существует Автоматизация, которая отслеживает определенные сценарии использования.</span><span class="sxs-lookup"><span data-stu-id="348da-113">In order to efficiently use capacity and deal with unexpected growth, in any farm, we have automation that tracks certain usage scenarios.</span></span> <span data-ttu-id="348da-114">Хотя точное увеличение непредсказуемо для любого клиента в одной ферме, суммарная сумма запросов предсказуема по времени.</span><span class="sxs-lookup"><span data-stu-id="348da-114">While exact growth is unpredictable for any one tenant in any one farm, the aggregated sum of requests is predictable over time.</span></span> <span data-ttu-id="348da-115">Определяя тенденции роста в SharePoint Online, мы можем запланировать будущее расширение.</span><span class="sxs-lookup"><span data-stu-id="348da-115">By identifying the growth trends in SharePoint Online, we can plan for future expansion.</span></span> <span data-ttu-id="348da-116">Для получения дополнительных сведений о [планировании мощности и тестировании нагрузки SharePoint Online](https://docs.microsoft.com/en-us/office365/enterprise/capacity-planning-and-load-testing-sharepoint-online).</span><span class="sxs-lookup"><span data-stu-id="348da-116">For more information on [Capacity planning and load testing SharePoint Online](https://docs.microsoft.com/en-us/office365/enterprise/capacity-planning-and-load-testing-sharepoint-online).</span></span>

<span data-ttu-id="348da-117">Основной частью успешного запуска является метод "Wave" или "поэтапная выгрузка", описанные ниже.</span><span class="sxs-lookup"><span data-stu-id="348da-117">A key part of a successful launch is the "wave" or "phased roll-out" approach detailed below.</span></span> 

## <a name="can-i-load-test-sharepoint-online"></a><span data-ttu-id="348da-118">Можно ли загрузить тест SharePoint Online?</span><span class="sxs-lookup"><span data-stu-id="348da-118">Can I load test SharePoint Online?</span></span>
<span data-ttu-id="348da-119">SharePoint Online — это общедоступная многоклиентская среда, сбалансированная между фермами и масштабированием.</span><span class="sxs-lookup"><span data-stu-id="348da-119">SharePoint Online is a shared multi-tenanted environment which is balanced across farms and scale is adjusted in an on-going basis.</span></span> <span data-ttu-id="348da-120">Нагрузочное тестирование среды, например SharePoint Online, в которой изменения масштаба непрерывно не только приводят к непредвиденным результатам, но не разрешены.</span><span class="sxs-lookup"><span data-stu-id="348da-120">Load testing an environment, like SharePoint Online, whose scale changes continuously will not only  give you unexpected results but it is not permitted.</span></span> 

<span data-ttu-id="348da-121">Дополнительные сведения: [SharePoint Online по планированию мощности и тестированию нагрузки](https://docs.microsoft.com/en-us/office365/enterprise/capacity-planning-and-load-testing-sharepoint-online)</span><span class="sxs-lookup"><span data-stu-id="348da-121">Learn more:  [Capacity planning and load testing SharePoint Online](https://docs.microsoft.com/en-us/office365/enterprise/capacity-planning-and-load-testing-sharepoint-online)</span></span>

## <a name="optimize-pages-by-following-recommended-guidelines"></a><span data-ttu-id="348da-122">Оптимизируйте страницы, следуя рекомендациям</span><span class="sxs-lookup"><span data-stu-id="348da-122">Optimize pages by following recommended guidelines</span></span>
<span data-ttu-id="348da-123">Страницы из локального развертывания не следует просто перемещать в SharePoint Online, не изменяя их на рекомендации для SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="348da-123">Pages from an on-Premise deployment should not simply be moved as they are onto SharePoint Online without reviewing them against recommended guidelines for SharePoint Online.</span></span> <span data-ttu-id="348da-124">Наилучший подход состоит в том, чтобы всегда оптимизировать любую домашнюю страницу для любого сайта или портала в SharePoint, так как в этом случае большинство пользователей в организации будут иметь доступ к отправной точке для сайтов.</span><span class="sxs-lookup"><span data-stu-id="348da-124">The best approach is to always optimize any home page for any site or portal in SharePoint, as this is where most users in your organization will access as the starting point for your site(s).</span></span>

<span data-ttu-id="348da-125">Следует учитывать несколько основных факторов:</span><span class="sxs-lookup"><span data-stu-id="348da-125">A few basic factors should be considered:</span></span>
- <span data-ttu-id="348da-126">Локальные развертывания могут использовать традиционные кэши на стороне сервера, такие как кэш объектов, кэш вывода и кэш больших двоичных объектов.</span><span class="sxs-lookup"><span data-stu-id="348da-126">On-Premise deployments can leverage traditional server-side caches like object cache, output cache and blob cache.</span></span> <span data-ttu-id="348da-127">При различиях топологии в облаке эти параметры необязательно доступны, так как различия в масштабах делают их менее приемлемыми.</span><span class="sxs-lookup"><span data-stu-id="348da-127">With the topology differences in the cloud, these options are not necessarily available as the sheer scale differences make them less viable approaches.</span></span>
- <span data-ttu-id="348da-128">Все страницы/функции и настройки, используемые для облачного использования, должны быть оптимизированы для большей задержки, а также для распределенных расположений пользователей, чтобы пользователи в разных областях или регионах могли использовать более единообразные возможности.</span><span class="sxs-lookup"><span data-stu-id="348da-128">Any pages / features / customizations used for cloud consumption should be optimized for higher latency as well as the distributed locations of users, so that users in different areas or regions have a more consistent experience.</span></span> <span data-ttu-id="348da-129">В облаке предусмотрены такие оптимизации, как сети доставки контента (CDN) для оптимизации для распределенной базы пользователей, а также для современных сред SharePoint, что в ЛКГ используются наши преимущества (OOTB).</span><span class="sxs-lookup"><span data-stu-id="348da-129">Cloud offers optimizations like Content Delivery Networks (CDN) to optimize for a distributed user base as well as for modern SharePoint, the last known good (LKG) is utilized by our out of the box (OOTB) web parts.</span></span>

### <a name="what-to-do"></a><span data-ttu-id="348da-130">Что делать:</span><span class="sxs-lookup"><span data-stu-id="348da-130">What to do:</span></span>
 - <span data-ttu-id="348da-131">Для всех страниц сайта в SharePoint Online используйте [средство диагностики страниц](https://aka.ms/perftool), которое представляет собой расширение чромиум, которое поможет анализировать и предоставлять рекомендации.</span><span class="sxs-lookup"><span data-stu-id="348da-131">For all site pages in SharePoint Online use the [Page Diagnostics tool](https://aka.ms/perftool), which is a Chromium extension which will assist with analyzing and providing guidance.</span></span> <span data-ttu-id="348da-132">Они могут использоваться владельцами, редакторами, администраторами и разработчиками сайтов, так как они разрабатываются как отправную точку для анализа и оптимизации.</span><span class="sxs-lookup"><span data-stu-id="348da-132">This can be used by site owners, editors, administrators and developers as it is designed to be a starting point for analysis and optimization.</span></span>
 - <span data-ttu-id="348da-133">Разработчикам также следует использовать средства разработки, такие как средство разработчика F12, а также CTRL – F12 в браузере на современных страницах.</span><span class="sxs-lookup"><span data-stu-id="348da-133">Developers should also use development tools like F12 browser developer tool as well as CTRL-F12 in the browser on modern pages.</span></span> <span data-ttu-id="348da-134">[Fiddler](https://www.telerik.com/download/fiddler) также можно использовать для просмотра веса размера страницы, а также количества вызовов и элементов, влияющих на общую загрузку страницы.</span><span class="sxs-lookup"><span data-stu-id="348da-134">[Fiddler](https://www.telerik.com/download/fiddler) can also be used to review the size weight (how large the page is in megabytes) of the page and the number of calls and elements impacting the overall page load.</span></span> 

<span data-ttu-id="348da-135">В этом разделе приведен краткий обзор оптимизации страниц.</span><span class="sxs-lookup"><span data-stu-id="348da-135">This section was a brief summary for optimizing pages.</span></span>  <span data-ttu-id="348da-136">Дополнительные сведения: [Создание, запуск и обслуживание работоспособного портала](https://go.microsoft.com/fwlink/?linkid=2105838).</span><span class="sxs-lookup"><span data-stu-id="348da-136">To learn more see:  [Creating, launching and maintaining a healthy portal](https://go.microsoft.com/fwlink/?linkid=2105838).</span></span>

## <a name="follow-a-wave--phased-roll-out-approach"></a><span data-ttu-id="348da-137">Следуйте принципу поэтапного и поэтапного развертывания</span><span class="sxs-lookup"><span data-stu-id="348da-137">Follow a Wave / Phased roll-out approach</span></span>
<span data-ttu-id="348da-138">Традиционный большой подход к отвосклицательному знаку для запуска сайта не позволит проверить, что настройки, внешние источники, службы или процессы были проверены в правильном масштабе.</span><span class="sxs-lookup"><span data-stu-id="348da-138">The traditional big bang approach for site launches will not allow verification that customizations, external sources, services or processes have been tested at the right scale.</span></span> <span data-ttu-id="348da-139">Это не означает, что для запуска потребуется заданный месяц, но рекомендуется по крайней мере несколько дней в зависимости от размера организации.</span><span class="sxs-lookup"><span data-stu-id="348da-139">This doesn't mean that it will take months to launch, but it is recommended over at least several days dependent on your organization size.</span></span> <span data-ttu-id="348da-140">После этого вы можете приостановить и устранить проблемы, прежде чем переходить к следующему этапу и, таким образом, уменьшить потенциальное количество пользователей, на которые влияют все проблемы.</span><span class="sxs-lookup"><span data-stu-id="348da-140">Following a wave roll-out plan therefore gives you the option to pause and resolve issues before proceeding with the next phase and therefore lowers the potential number of users impacted by any issues.</span></span> <span data-ttu-id="348da-141">SharePoint в качестве службы масштабирует мощность на основе использования и прогнозирования использования и в течение этого нам не нужно уведомлять о своем запуске, следуйте рекомендациям по обеспечению успеха.</span><span class="sxs-lookup"><span data-stu-id="348da-141">SharePoint as a service scales your capacity based on usage and predicted usage and whilst we don't need you to notify us of your launch, you should follow the guidelines to ensure success.</span></span>
  
<span data-ttu-id="348da-142">Как показано на следующем рисунке, часто это количество приглашенных пользователей значительно выше, чем на самом деле использует сайт.</span><span class="sxs-lookup"><span data-stu-id="348da-142">As shown in the following image, often the number of users that are invited is significantly higher than those that actually use the site.</span></span> <span data-ttu-id="348da-143">На этом рисунке показана стратегия развертывания выпуска.</span><span class="sxs-lookup"><span data-stu-id="348da-143">This image shows a strategy about how to roll out a release.</span></span> <span data-ttu-id="348da-144">Этот метод помогает определить способы усовершенствования сайта SharePoint, прежде чем большинство пользователей увидят его.</span><span class="sxs-lookup"><span data-stu-id="348da-144">This method helps identify ways to improve the SharePoint site before the majority of the users see it.</span></span>
  
![Диаграмма, показывающая приглашенных и активных пользователей](media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)
  
<span data-ttu-id="348da-146">На этапе пилотного развертывания удобно получать отзывы пользователей о том, что ваша организация доверяется и знает о них.</span><span class="sxs-lookup"><span data-stu-id="348da-146">In the pilot phase, it is good to get feedback from users that the organization trusts and knows will be engaged.</span></span> <span data-ttu-id="348da-147">Таким образом, можно оценить, как используется система, а также как она выполняется.</span><span class="sxs-lookup"><span data-stu-id="348da-147">This way it is possible to gauge how the system is being used, as well as how it is performing.</span></span>
  
<span data-ttu-id="348da-148">Во время каждой волны Соберите отзывы пользователей о функциях, а также о производительности во время каждой волны развертывания.</span><span class="sxs-lookup"><span data-stu-id="348da-148">During each of the waves, gather user feedback around the features as well as the performance during each wave of deployment.</span></span> <span data-ttu-id="348da-149">Благодаря этому у вас есть преимущества медленного введения системы и улучшения работы системы.</span><span class="sxs-lookup"><span data-stu-id="348da-149">This has the advantage of slowly introducing the system and making improvements as the system gets more use.</span></span> <span data-ttu-id="348da-150">Это также позволяет нам реагировать на повышенную нагрузку при развертывании сайта до большего числа пользователей, а также в сочетании с соблюдением рекомендаций по оптимизации страниц, что позволяет пользователям получить положительную среду.</span><span class="sxs-lookup"><span data-stu-id="348da-150">This also allows us to react to the increased load as the site is rolled out to more and more users and combined with following the guidelines for page optimization ensures a positive experience for your users.</span></span>

### <a name="what-to-do"></a><span data-ttu-id="348da-151">Что делать:</span><span class="sxs-lookup"><span data-stu-id="348da-151">What to do:</span></span>
- <span data-ttu-id="348da-152">Определите время каждого этапа и убедитесь, что у вас есть непредвиденная или временная возможность, прежде чем продолжить</span><span class="sxs-lookup"><span data-stu-id="348da-152">Decide on the timing of each phase and ensure that you have a contingency / pause opportunity, should you need to make adjustments before continuing</span></span>
- <span data-ttu-id="348da-153">Запланируйте первую группу пользователей, которую вы хотите включить, чтобы убедиться, что вы получили отзывы, которые необходимо переместить вперед.</span><span class="sxs-lookup"><span data-stu-id="348da-153">Plan your first group of users that you want to enable, to ensure you receive the feedback you need to move forward.</span></span> <span data-ttu-id="348da-154">Это означает, что если это возможно, выберите активную группу пользователей, которые будут своевременно предоставлять отзывы</span><span class="sxs-lookup"><span data-stu-id="348da-154">This means that where possible, select an active group of users that will provide feedback in a timely fashion</span></span>
- <span data-ttu-id="348da-155">Когда вы планируете каждую из них, попробуйте и начните с маленькой пользовательской базы (менее 5000 пользователей), а затем увеличьте размер группы, как только вы продолжите с каждой волновой волны.</span><span class="sxs-lookup"><span data-stu-id="348da-155">As you plan each wave, try and start with a small user base (less than 5000 users), and then increase the group sizes as you proceed with each wave.</span></span> <span data-ttu-id="348da-156">Это позволяет создать побросой подход и упростить приостановку работы, которая может потребоваться.</span><span class="sxs-lookup"><span data-stu-id="348da-156">This helps to create a staggered approach and allows easier pause opportunities that may be needed.</span></span>