---
title: Емкость планирования и нагрузочного тестирования SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/18/2016
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c932bd9b-fb9a-47ab-a330-6979d03688c0
description: В этой статье описывается, как можно развернуть в SharePoint Online без выполнения традиционных нагрузочного тестирования, так как он является недопустимым.
ms.openlocfilehash: 6a22ee089adc0817f5c52bbfee5f2b41d7e5d80c
ms.sourcegitcommit: 82c8fe6393457f0271d1737a09402a420a81c986
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/06/2018
ms.locfileid: "27181030"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a><span data-ttu-id="bc8c8-103">Емкость планирования и нагрузочного тестирования SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bc8c8-103">Capacity planning and load testing SharePoint Online</span></span>

<span data-ttu-id="bc8c8-104">В этой статье описывается, как можно развернуть в SharePoint Online без традиционных нагрузочного тестирования, поскольку нагрузочного тестирования не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="bc8c8-104">This article describes how you can deploy to SharePoint Online without traditional load testing, since load-testing is strongly discouraged.</span></span>
  
<span data-ttu-id="bc8c8-105">Несмотря на то, что active нагрузочного тестирования в SharePoint Online не рекомендуется, можно и другими способами, которые вы можете убедиться в том, сайт не дает низкого уровня пользовательского интерфейса, при запуске сайта.</span><span class="sxs-lookup"><span data-stu-id="bc8c8-105">Although active load testing on SharePoint Online is strongly discouraged, there are other ways you can make sure that a site will not produce a poor user experience when you launch the site.</span></span> 
  
<span data-ttu-id="bc8c8-p101">С помощью SharePoint Online не нужно выполнить планирование емкости, как это делается в процессе наших услуг. С локальной сред нагрузочного тестирования используется для проверки допущения масштабирования и в конечном счете найти точку разбиение на ферме; с загружая его с нагрузки. С помощью SharePoint Online необходимо выполнить действия по-разному. Выполняется в среде с несколькими клиентами, у нас есть для защиты всех клиентов в той же ферме, поэтому мы будет автоматически регулировать нагрузочных тестов. Это означает, что вы будете получать разочаровать и потенциально вводящих в заблуждение результатов при попытке загрузки тестирование вашей среды.</span><span class="sxs-lookup"><span data-stu-id="bc8c8-p101">With SharePoint Online you don't have to do capacity planning, as this is done for you as part of our service offering. With on-premises environments, load testing is used to validate scale assumption and ultimately find the breaking point of a farm; by saturating it with load. With SharePoint Online we need to do things differently. Being a multi-tenant environment, we have to protect all tenants in the same farm, so we will automatically throttle any load tests. This means you will receive disappointing and potentially misleading results if you attempt to load test your environment.</span></span>
  
<span data-ttu-id="bc8c8-p102">Одним из основных преимуществ использования SharePoint Online по локальным развертыванием является эластичности облаке. Нашей среде большого масштаба настроен на службы миллионы пользователей на ежедневной основе, не важно, мы обрабатывать емкости эффективно, развернув автоматически фермы по мере необходимости. В этой статье объясняется, как мы Планирование емкости роста и горизонтальным масштабирование на месте. В статье рассматриваются также подходов для использования, которые не используют нагрузочного тестирования.</span><span class="sxs-lookup"><span data-stu-id="bc8c8-p102">One of the main benefits of SharePoint Online over an on-premises deployment is the elasticity of the cloud. Our large scale environment is set up to service millions of users on a daily basis so it is important that we handle capacity effectively by automatically expanding farms, as and when needed. This article explains how we plan for capacity growth and scale out in place. The article also covers approaches for you to use that don't involve load testing.</span></span>
  
## <a name="how-office-365-predicts-load-and-expands-capacity"></a><span data-ttu-id="bc8c8-115">Как Office 365 прогнозы нагрузки и разворачивает емкости</span><span class="sxs-lookup"><span data-stu-id="bc8c8-115">How Office 365 predicts load and expands capacity</span></span>

<span data-ttu-id="bc8c8-116">SharePoint Online работу мощности сервера одним из двух способов:</span><span class="sxs-lookup"><span data-stu-id="bc8c8-116">SharePoint Online server capacity management work is done through two methods:</span></span>
  
- <span data-ttu-id="bc8c8-117">Прогнозирование емкостью</span><span class="sxs-lookup"><span data-stu-id="bc8c8-117">Capacity forecasting</span></span>
    
- <span data-ttu-id="bc8c8-118">Балансировка нагрузки на одном сервере фермах</span><span class="sxs-lookup"><span data-stu-id="bc8c8-118">Load-balancing on single server farms</span></span>
    
<span data-ttu-id="bc8c8-p103">В отличие от планирования для локальной среды, емкость прогнозирования в SharePoint Online, можно компилировать статистики и создать диаграмму потенциальных требования в любую группу данного сервера. Агрегированные запросами может выглядеть запросы в зоне (где зона — это группа фермах SharePoint) роста строки на следующем рисунке:</span><span class="sxs-lookup"><span data-stu-id="bc8c8-p103">Unlike planning for an on-premises environment, for capacity forecasting in SharePoint Online, we are able to compile statistics and graph potential requirements in any given server group. The aggregate demand might look something like the Requests in zone (where a zone is a group of SharePoint farms) growth line in the image below:</span></span>
  
![Диаграмма "Предсказуемая мощность: прогноз"](media/ca800cb6-cc59-451f-98bd-55e035489af3.png)
  
<span data-ttu-id="bc8c8-p104">Роста непредсказуемое во время любого одной фермы, сводные суммы запросы в зоне предсказуемым. С учетом тенденции роста в SharePoint Online, можно планировать будущее расширение.</span><span class="sxs-lookup"><span data-stu-id="bc8c8-p104">While the growth is unpredictable in any one farm, the aggregated sum of requests in a zone is predictable. By identifying the growth trends in SharePoint Online, we can plan for future expansion.</span></span>
  
<span data-ttu-id="bc8c8-p105">Чтобы эффективно использовать емкости и работать с непредвиденного роста в любой ферме у нас есть автоматизации, который отслеживает интерфейсные нагрузки и масштабируются на месте, при необходимости. Основной показатель, мы используем как сигнал масштабировать заранее заканчивается — загрузка ЦП. Цель — оставьте Пиковая загрузка ЦП в разделе 40%. Это, чтобы выделить непредвиденные пики достаточно буфера. Как нагрузки подходов 40% в стабильном состоянии мы добавьте интерфейсы ферм.</span><span class="sxs-lookup"><span data-stu-id="bc8c8-p105">In order to efficiently use capacity and deal with unexpected growth, in any farm, we have automation that tracks front-end load and scales up in place, when needed. The main metric we use as a signal to scale up front ends is CPU load. Our goal is to keep peak CPU load under 40%. This is in order to have enough buffer to absorb unexpected spikes. As load approaches 40% in steady state, we add front ends to farms.</span></span>
  
![Диаграмма "Предсказуемая мощность: управление фермами"](media/6b2a8c63-24c1-4504-b7a3-3d3b3be2583a.png)
  
<span data-ttu-id="bc8c8-130">Дополнительные серверы можно быстро добавить в ферму, используя те, которые ранее были добавлены в зону через прогноз об использовании.</span><span class="sxs-lookup"><span data-stu-id="bc8c8-130">Additional servers can be quickly added to a farm, using those which have been previously added to the zone through the usage forecast.</span></span> 
  
## <a name="how-do-i-plan-for-a-site-launch"></a><span data-ttu-id="bc8c8-131">Как спланировать запуска сайта?</span><span class="sxs-lookup"><span data-stu-id="bc8c8-131">How do I plan for a site launch?</span></span>

<span data-ttu-id="bc8c8-p106">Следует ожидать, что фермы, на котором запускается новый сайт будет автоматически отслеживаться, чтобы добавляются новые серверы переднего плана, как описано выше. По этой причине нет необходимости уведомлений для запуска вашего нового сайта.</span><span class="sxs-lookup"><span data-stu-id="bc8c8-p106">You should expect that the farm on which your new site launches will automatically be monitored so that new front-end servers are added, as described above. For this reason, we don't need any notification for your new site launch.</span></span>
  
<span data-ttu-id="bc8c8-134">После другие рекомендации по работе с одной страницы на SharePoint Online маловероятно, что новый сайт запуска даже 100 000 пользователей будут иметь любое влияние на ферму.</span><span class="sxs-lookup"><span data-stu-id="bc8c8-134">Following other best practices for a single page on SharePoint Online it is unlikely that a new site launch to even 100,000 users will have any impact to the farm.</span></span>
  
<span data-ttu-id="bc8c8-p107">Существует несколько стратегий для планирования для выпуска новый сайт SharePoint Online. Как показано на следующем рисунке, часто количество пользователей, которые получают приглашения значительно выше, чем те, которые фактически используют сайта. На этом рисунке показана стратегия о том, как к развертыванию выпуска. Этот метод не только помогает с загрузкой производительности, но также помогает определить способы повышения на сайте SharePoint, перед его увидеть больших большинство пользователей.</span><span class="sxs-lookup"><span data-stu-id="bc8c8-p107">There are a few strategies to plan for a release of a new SharePoint Online site. As shown in the following image, often the amount of users that are invited is significantly higher than those that actually use the site. This image shows a strategy about how to roll out a release. This method not only helps with performance loading but also can help identify ways to improve the SharePoint site before the large majority of the users see it.</span></span>
  
![Диаграмма, показывающая приглашенных и активных пользователей](media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)
  
<span data-ttu-id="bc8c8-p108">В пилотный этап рекомендуется для получения обратной связи с пользователями отношения доверия и знает будет иметь мероприятиям организации. Таким образом можно оценить допустимое для системы об использовании, а также как выполняется.</span><span class="sxs-lookup"><span data-stu-id="bc8c8-p108">In the pilot phase, it is good to get feedback from users that the organization trusts and knows will be engaged. This way it is possible to gauge how the system is being used, as well as how it is performing.</span></span>
  
<span data-ttu-id="bc8c8-p109">После этого начинает развертывание для всех пользователей в этапами; обратная связь и проверки производительности регулярно. Это преимущество медленно краткие сведения о системе и усовершенствования, как система получает дополнительные использования. Это также позволяет реагировать на увеличения нагрузки, как сайт является для развертывания для больше и больше пользователей.</span><span class="sxs-lookup"><span data-stu-id="bc8c8-p109">After this, begins a roll out to all users in waves; getting feedback and reviewing the performance regularly. This has the advantage of slowly introducing the system and making improvements as the system gets more use. This also allows us to react to the increased load as the site is rolled out to more and more users.</span></span>
  
<span data-ttu-id="bc8c8-p110">И, наконец пока запрещены нагрузочных тестов, клиенты может потребоваться настроить периодический команды ping для службы в мер доступность и задержка. Определяет базовый план для веб-узла. Тем не менее они должны поддерживаться низкой частоте, чтобы избежать регулирование описанных выше проблем.</span><span class="sxs-lookup"><span data-stu-id="bc8c8-p110">Finally, while load tests are prohibited, customers may want to set up periodical pings to the service to measure availability and latency. This will identify a baseline for their site. However, these must be kept to low frequency to avoid throttling issues previously described.</span></span>
  

