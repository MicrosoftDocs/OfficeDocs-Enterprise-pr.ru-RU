---
title: "Руководство по безопасности (Майкрософт) для политических кампаний, некоммерческих и других динамических организаций"
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
ms.assetid: 10d1004b-42b6-4e2b-aaa2-18ddd9118f64
description: "Обзор: Планирование и внедрение руководство по переносу fast организации, которые профиль увеличению угроз."
ms.openlocfilehash: 0177e91ac0cbd7ba6ce7ffe95206036036c43da4
ms.sourcegitcommit: 4a347cfb16405d5213b28f332d80e244fca0fb8f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/18/2017
---
# <a name="microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-organizations"></a><span data-ttu-id="73a6c-103">Руководство по безопасности (Майкрософт) для политических кампаний, некоммерческих и других динамических организаций</span><span class="sxs-lookup"><span data-stu-id="73a6c-103">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>

 <span data-ttu-id="73a6c-104">**Сводка:** Планирование и внедрение руководства по перемещению fast организации, которые профиль увеличению угроз.</span><span class="sxs-lookup"><span data-stu-id="73a6c-104">**Summary:** Planning and implementation guidance for fast-moving organizations that have an increased threat profile.</span></span>
  
<span data-ttu-id="73a6c-p101">Если у вас динамичная организация, небольшая команда ИТ-специалистов, а профиль угроз выше среднего, это руководство — именно то, что вам нужно. Здесь вы узнаете, как быстро создать среду с основными облачным службами, куда изначально входят и элементы управления безопасностью. В этом руководстве приводятся рекомендации по защите данных, электронной почты и удостоверений, а также по организации безопасного доступа с мобильных устройств.</span><span class="sxs-lookup"><span data-stu-id="73a6c-p101">If your organization is agile, you have a small IT team, and your threat profile is higher than average, this guidance is designed for you. This solution demonstrates how to quickly build an environment with essential cloud services that include secure controls from the start. This guidance includes prescriptive security recommendations for protecting data, identities, email, and access from mobile devices.</span></span>
  
## <a name="security-solution-guidance"></a><span data-ttu-id="73a6c-108">Руководство по вариантам обеспечения безопасности</span><span class="sxs-lookup"><span data-stu-id="73a6c-108">Security solution guidance</span></span>

<span data-ttu-id="73a6c-p102">В этом руководстве описано внедрение безопасной облачной среде. Руководство по решениям можно использовать с любой организации. Оно включает в себя помощь для гибкой организаций с BYOD доступа и гостевые учетные записи. Данное руководство можно использовать как за основу для разработки собственной среде. Мы будем рады свой отзыв на [CloudAdopt@microsoft.com](mailto:CloudAdopt@microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="73a6c-p102">This guidance describes how to implement a secure cloud environment. The solution guidance can be used by any organization. It includes extra help for agile organizations with BYOD access and guest accounts. You can use this guidance as a starting-point for designing your own environment. We welcome your feedback at [CloudAdopt@microsoft.com](mailto:CloudAdopt@microsoft.com).</span></span> 
  
|||
|:-----|:-----|
|<span data-ttu-id="73a6c-114">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="73a6c-114">**Item**</span></span> <br/> |<span data-ttu-id="73a6c-115">**Описание**</span><span class="sxs-lookup"><span data-stu-id="73a6c-115">**Description**</span></span> <br/> |
|<span data-ttu-id="73a6c-116">**Руководство по безопасности корпорации Майкрософт для политических кампании**</span><span class="sxs-lookup"><span data-stu-id="73a6c-116">**Microsoft Security Guidance for Political Campaigns**</span></span> <br/> <span data-ttu-id="73a6c-117">[![Эскиз гвоздями для мини-плакат набора.](images/d370ce28-ca40-4930-9a2c-907312aa06c8.png)          ](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)</span><span class="sxs-lookup"><span data-stu-id="73a6c-117">[![Thumb nail for mini poster set.](images/d370ce28-ca40-4930-9a2c-907312aa06c8.png)          ](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)</span></span> <br/> <span data-ttu-id="73a6c-118">[PDF](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)  \\</span><span class="sxs-lookup"><span data-stu-id="73a6c-118">[PDF](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)  \\</span></span>| [<span data-ttu-id="73a6c-119">Visio</span><span class="sxs-lookup"><span data-stu-id="73a6c-119">Visio</span></span>](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.vsdx) <br/> |<span data-ttu-id="73a6c-p103">В этом руководстве в качестве примера приведена организация, проводящая политические кампании. Это руководство — отправная точка при разработке любой среды. </span><span class="sxs-lookup"><span data-stu-id="73a6c-p103">This guidance uses a political campaign organization as an example. Use this guidance as a starting point for any environment.</span></span>  <br/> |
|<span data-ttu-id="73a6c-122">**Руководство по безопасности корпорации Майкрософт для некоммерческим организациями**</span><span class="sxs-lookup"><span data-stu-id="73a6c-122">**Microsoft Security Guidance for Nonprofits**</span></span> <br/> <span data-ttu-id="73a6c-123">[![Эскиз изображения загружаемого файла](images/e4784889-1c69-4067-9a8f-31d31d1eceea.png)          ](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)</span><span class="sxs-lookup"><span data-stu-id="73a6c-123">[![Thumnail image for downloadable file](images/e4784889-1c69-4067-9a8f-31d31d1eceea.png)          ](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)</span></span> <br/> <span data-ttu-id="73a6c-124">[PDF](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)  \\</span><span class="sxs-lookup"><span data-stu-id="73a6c-124">[PDF](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)  \\</span></span>| [<span data-ttu-id="73a6c-125">Visio</span><span class="sxs-lookup"><span data-stu-id="73a6c-125">Visio</span></span>](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.vsdx) <br/> |<span data-ttu-id="73a6c-p104">В это руководство внесены незначительные изменения, благодаря которым оно подходит некоммерческим организациям. Например, рассмотрены планы Office 365 для некоммерческих организаций. Техническое руководство ничем не отличается от такового для организаций, проводящих политические кампании.</span><span class="sxs-lookup"><span data-stu-id="73a6c-p104">This guide is slightly revised for nonprofit organizations. For example, it references Office 365 Nonprofit plans. The technical guidance is the same as the political campaign solution guide.</span></span>  <br/> |
   
## <a name="test-lab-guides"></a><span data-ttu-id="73a6c-129">Руководства по лаборатории тестирования</span><span class="sxs-lookup"><span data-stu-id="73a6c-129">Test Lab Guides</span></span>

<span data-ttu-id="73a6c-130">Чтобы создать среду разработки и тестирования для этого решения, используйте следующие руководства:  </span><span class="sxs-lookup"><span data-stu-id="73a6c-130">To create a dev/test environment for this solution, use the following test lab guides:</span></span> 
  
- [<span data-ttu-id="73a6c-131">Настройка групп и пользователей в среде разработки и тестирования политических кампаний (en)</span><span class="sxs-lookup"><span data-stu-id="73a6c-131">Configure groups and users for a political campaign dev/test environment</span></span>](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
    
     <span data-ttu-id="73a6c-132">Создание пробной подписки для Office 365 и Командной и создайте для типичной политических кампании пользователей и групп.</span><span class="sxs-lookup"><span data-stu-id="73a6c-132">Create trial subscriptions for Office 365 and EMS and then create groups and users for a representative political campaign.</span></span>
    
- [<span data-ttu-id="73a6c-133">Создание веб-сайтов групп в среде разработки и тестирования политических кампаний (en)</span><span class="sxs-lookup"><span data-stu-id="73a6c-133">Create team sites in a political campaign dev/test environment</span></span>](create-team-sites-in-a-political-campaign-dev-test-environment.md)
    
    <span data-ttu-id="73a6c-134">Создайте четыре SharePoint Online веб-сайтов групп с помощью Internal, Private, конфиденциальные и конфиденциальными уровней безопасности.</span><span class="sxs-lookup"><span data-stu-id="73a6c-134">Create four SharePoint Online team sites with Internal, Private, Sensitive, and Highly Confidential levels of security.</span></span>
    
<span data-ttu-id="73a6c-135">Дополнительные функции безопасности для демонстрации или пробной версии в разделе [Руководства по тестовой лаборатории Office 365](http://aka.ms/o365tlgs).</span><span class="sxs-lookup"><span data-stu-id="73a6c-135">For additional security features for demonstration or proof of concept, see [Office 365 Test Lab Guides](http://aka.ms/o365tlgs).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="73a6c-136">See Also</span><span class="sxs-lookup"><span data-stu-id="73a6c-136">See Also</span></span>

[<span data-ttu-id="73a6c-137">Решения для обеспечения безопасности</span><span class="sxs-lookup"><span data-stu-id="73a6c-137">Security solutions</span></span>](security-solutions.md)
  
[<span data-ttu-id="73a6c-138">Руководства по лаборатории тестирования для принятия облачных решений</span><span class="sxs-lookup"><span data-stu-id="73a6c-138">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="73a6c-139">Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="73a6c-139">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)



