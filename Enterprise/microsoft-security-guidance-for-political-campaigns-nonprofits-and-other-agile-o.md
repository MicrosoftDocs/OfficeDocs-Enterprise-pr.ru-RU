---
title: "Руководство по безопасности (Майкрософт) для политических кампаний, некоммерческих и других динамических организаций"
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Normal
ms.custom: Strat_O365_Enterprise
ms.assetid: 10d1004b-42b6-4e2b-aaa2-18ddd9118f64
description: "Обзор: Планирование и внедрение руководство по переносу fast организации, которые профиль увеличению угроз."
ms.openlocfilehash: b35b7a49343b21fdd8e6584e113fcbf771b4a1ef
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-organizations"></a><span data-ttu-id="5ef72-103">Руководство по безопасности (Майкрософт) для политических кампаний, некоммерческих и других динамических организаций</span><span class="sxs-lookup"><span data-stu-id="5ef72-103">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>

 <span data-ttu-id="5ef72-104">**Сводка:** Планирование и внедрение руководства по перемещению fast организации, которые профиль увеличению угроз.</span><span class="sxs-lookup"><span data-stu-id="5ef72-104">**Summary:** Planning and implementation guidance for fast-moving organizations that have an increased threat profile.</span></span>
  
<span data-ttu-id="5ef72-p101">Если у вас динамичная организация, небольшая команда ИТ-специалистов, а профиль угроз выше среднего, это руководство — именно то, что вам нужно. Здесь вы узнаете, как быстро создать среду с основными облачными службами, куда изначально входят и элементы управления безопасностью. В этом руководстве приводятся рекомендации по защите данных, электронной почты и удостоверений, а также по организации безопасного доступа с мобильных устройств.</span><span class="sxs-lookup"><span data-stu-id="5ef72-p101">If your organization is agile, you have a small IT team, and your threat profile is higher than average, this guidance is designed for you. This solution demonstrates how to quickly build an environment with essential cloud services that include secure controls from the start. This guidance includes prescriptive security recommendations for protecting data, identities, email, and access from mobile devices.</span></span>
  
## <a name="security-solution-guidance"></a><span data-ttu-id="5ef72-108">Руководство по безопасности</span><span class="sxs-lookup"><span data-stu-id="5ef72-108">Security solution guidance</span></span>

<span data-ttu-id="5ef72-p102">В этом руководстве описано, как реализовать безопасную облачную среду. Это руководство может использовать любая организация. В него входят дополнительные справочные сведения для организации с гибкими возможностями работы с доступом BYOD и учетными записями гостей. Его можно взять за основу при разработке собственной среды. Отзывы можно отправлять по адресу [CloudAdopt@microsoft.com](mailto:CloudAdopt@microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="5ef72-p102">This guidance describes how to implement a secure cloud environment. The solution guidance can be used by any organization. It includes extra help for agile organizations with BYOD access and guest accounts. You can use this guidance as a starting-point for designing your own environment. We welcome your feedback at [CloudAdopt@microsoft.com](mailto:CloudAdopt@microsoft.com).</span></span> 
  
|||
|:-----|:-----|
|<span data-ttu-id="5ef72-114">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="5ef72-114">**Item**</span></span> <br/> |<span data-ttu-id="5ef72-115">**Описание**</span><span class="sxs-lookup"><span data-stu-id="5ef72-115">**Description**</span></span> <br/> |
|<span data-ttu-id="5ef72-116">**Руководство по безопасности (Майкрософт) для политических кампаний**</span><span class="sxs-lookup"><span data-stu-id="5ef72-116">**Microsoft Security Guidance for Political Campaigns**</span></span> <br/> <span data-ttu-id="5ef72-117">[![Эскиз гвоздями для мини-плакат набора.](images/d370ce28-ca40-4930-9a2c-907312aa06c8.png)          ](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)</span><span class="sxs-lookup"><span data-stu-id="5ef72-117">[![Thumb nail for mini poster set.](images/d370ce28-ca40-4930-9a2c-907312aa06c8.png)          ](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)</span></span> <br/> <span data-ttu-id="5ef72-118">[Версия в формате](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf) \| [Visio](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.vsdx)  </span><span class="sxs-lookup"><span data-stu-id="5ef72-118">[PDF](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)  \| [Visio](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.vsdx)</span></span> <br/> |<span data-ttu-id="5ef72-p103">В этом руководстве в качестве примера используется организация, проводящая политические кампании. Используйте это руководство в качестве отправной точки для любой среды.</span><span class="sxs-lookup"><span data-stu-id="5ef72-p103">This guidance uses a political campaign organization as an example. Use this guidance as a starting point for any environment.</span></span>  <br/> |
|<span data-ttu-id="5ef72-121">**Руководство по безопасности (Майкрософт) для некоммерческих организаций**</span><span class="sxs-lookup"><span data-stu-id="5ef72-121">**Microsoft Security Guidance for Nonprofits**</span></span> <br/> <span data-ttu-id="5ef72-122">[![Эскиз изображения загружаемого файла](images/e4784889-1c69-4067-9a8f-31d31d1eceea.png)          ](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)</span><span class="sxs-lookup"><span data-stu-id="5ef72-122">[![Thumnail image for downloadable file](images/e4784889-1c69-4067-9a8f-31d31d1eceea.png)          ](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)</span></span> <br/> <span data-ttu-id="5ef72-123">[Версия в формате](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf) \| [Visio](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.vsdx)  </span><span class="sxs-lookup"><span data-stu-id="5ef72-123">[PDF](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)  \| [Visio](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.vsdx)</span></span> <br/> |<span data-ttu-id="5ef72-p104">В это руководство внесены незначительные изменения, благодаря которым оно подходит некоммерческим организациям. Например, рассмотрены планы Office 365 для некоммерческих организаций. Техническое руководство ничем не отличается от такового для организаций, проводящих политические кампании.</span><span class="sxs-lookup"><span data-stu-id="5ef72-p104">This guide is slightly revised for nonprofit organizations. For example, it references Office 365 Nonprofit plans. The technical guidance is the same as the political campaign solution guide.</span></span>  <br/> |
   
## <a name="test-lab-guides"></a><span data-ttu-id="5ef72-127">Руководства по лаборатории тестирования</span><span class="sxs-lookup"><span data-stu-id="5ef72-127">Test Lab Guides</span></span>

<span data-ttu-id="5ef72-128">Чтобы создать среду разработки и тестирования для этого решения, используйте следующие руководства:  </span><span class="sxs-lookup"><span data-stu-id="5ef72-128">To create a dev/test environment for this solution, use the following test lab guides:</span></span> 
  
- [<span data-ttu-id="5ef72-129">Настройка групп и пользователей в среде разработки и тестирования политических кампаний (en)</span><span class="sxs-lookup"><span data-stu-id="5ef72-129">Configure groups and users for a political campaign dev/test environment</span></span>](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
    
     <span data-ttu-id="5ef72-130">Создание пробной подписки для Office 365 и Командной и создайте для типичной политических кампании пользователей и групп.</span><span class="sxs-lookup"><span data-stu-id="5ef72-130">Create trial subscriptions for Office 365 and EMS and then create groups and users for a representative political campaign.</span></span>
    
- [<span data-ttu-id="5ef72-131">Создание веб-сайтов групп в среде разработки и тестирования политических кампаний (en)</span><span class="sxs-lookup"><span data-stu-id="5ef72-131">Create team sites in a political campaign dev/test environment</span></span>](create-team-sites-in-a-political-campaign-dev-test-environment.md)
    
    <span data-ttu-id="5ef72-132">Создайте четыре SharePoint Online веб-сайтов групп с помощью Internal, Private, конфиденциальные и конфиденциальными уровней безопасности.</span><span class="sxs-lookup"><span data-stu-id="5ef72-132">Create four SharePoint Online team sites with Internal, Private, Sensitive, and Highly Confidential levels of security.</span></span>
    
<span data-ttu-id="5ef72-133">Дополнительные функции безопасности для демонстрации или пробной версии в разделе [Руководства по тестовой лаборатории Office 365](http://aka.ms/o365tlgs).</span><span class="sxs-lookup"><span data-stu-id="5ef72-133">For additional security features for demonstration or proof of concept, see [Office 365 Test Lab Guides](http://aka.ms/o365tlgs).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5ef72-134">См. также</span><span class="sxs-lookup"><span data-stu-id="5ef72-134">See Also</span></span>

[<span data-ttu-id="5ef72-135">Решения для обеспечения безопасности</span><span class="sxs-lookup"><span data-stu-id="5ef72-135">Security solutions</span></span>](security-solutions.md)
  
[<span data-ttu-id="5ef72-136">Руководства по созданию сред разработки и тестирования облачных решений</span><span class="sxs-lookup"><span data-stu-id="5ef72-136">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="5ef72-137">Материалы по архитектуре Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="5ef72-137">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)



