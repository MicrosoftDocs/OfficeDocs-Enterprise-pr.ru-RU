---
title: Тестирование Office 365 с помощью руководств по лаборатории тестирования
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/12/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: Сводка. Воспользуйтесь этими руководствами по лаборатории тестирования, чтобы настроить среды для демонстрации, экспериментальной установки, разработки и тестирования продуктов Office 365.
ms.openlocfilehash: 32675683846789f1e7be0e398e5b140d25d7ba80
ms.sourcegitcommit: d58cdc7b2296df12f7a05d14ba05ab224ffb3e0c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/13/2019
ms.locfileid: "36302741"
---
# <a name="test-office-365-with-test-lab-guides-tlgs"></a><span data-ttu-id="0e1de-103">Тестирование Office 365 с помощью руководств по лаборатории тестирования</span><span class="sxs-lookup"><span data-stu-id="0e1de-103">Test Office 365 with cloud adoption Test Lab Guides (TLGs)</span></span>

 <span data-ttu-id="0e1de-104">**Сводка.** Используйте эту статью, чтобы настроить среды для демонстрации, экспериментальной установки, разработки и тестирования продуктов Office 365.</span><span class="sxs-lookup"><span data-stu-id="0e1de-104">**Summary:** Use these cloud adoption Test Lab Guides (TLGs) to set up demonstration, proof of concept, or dev/test environments for Office 365.</span></span>
  
<span data-ttu-id="0e1de-p101">Руководства по лаборатории тестирования содержат краткие сведения о продуктах Майкрософт. Они отлично подходят для ситуаций, в которых нужно оценить технологию или конфигурацию, прежде чем решать, подходит ли она вам, или прежде чем начинать проектировать, планировать и развертывать ее для пользователей. Такой интерактивный подход помогает ознакомиться с требованиями для развертывания нового продукта или решения и позволяет лучше спланировать его размещение в производственной среде.</span><span class="sxs-lookup"><span data-stu-id="0e1de-p101">TLGs help you quickly learn about Microsoft products. They're great for situations where you need to evaluate a technology or configuration before you decide whether it's right for you and before you begin the design, planning, and rollout to users. The "I built it out myself and it works" hands-on experience helps you understand the deployment requirements of a new product or solution so you can better plan for hosting it in production.</span></span>
  
<span data-ttu-id="0e1de-108">Кроме того, эти руководства помогают создавать типичные среды для разработки и тестирования приложений.</span><span class="sxs-lookup"><span data-stu-id="0e1de-108">TLGs also create representative environments for development and testing of applications, also known as dev/test environments.</span></span>
  
![Руководства по лаборатории тестирования в Microsoft Cloud](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
## <a name="office-365-devtest-environment"></a><span data-ttu-id="0e1de-110">Среда разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="0e1de-110">Office 365 dev/test environment</span></span>

<span data-ttu-id="0e1de-111">Следующие статьи помогут вам создать среду разработки и тестирования Office 365:</span><span class="sxs-lookup"><span data-stu-id="0e1de-111">Use these articles to build your Office 365 dev/test environment:</span></span>
  
- [<span data-ttu-id="0e1de-112">Базовая конфигурация среды разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="0e1de-112">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
    
    <span data-ttu-id="0e1de-p102">Создание упрощенной интрасети, выполняющейся в службах инфраструктуры Microsoft Azure. Это действие не является обязательным для создания имитации конфигурации предприятия.</span><span class="sxs-lookup"><span data-stu-id="0e1de-p102">Create a simplified intranet running in Microsoft Azure infrastructure services. This is an optional step if you want to build a simulated enterprise configuration.</span></span>
    
- [<span data-ttu-id="0e1de-115">Среда разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="0e1de-115">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
    
    <span data-ttu-id="0e1de-116">Подписка на бесплатную пробную версию Office 365 корпоративный Е5, которую можно оформить со своего компьютера или через упрощенную интрасеть в службах инфраструктуры Azure.</span><span class="sxs-lookup"><span data-stu-id="0e1de-116">Create an Office 365 Enterprise E5 trial subscription, which you can do from your computer or from a simplified intranet running in Azure infrastructure services.</span></span>
    
- [<span data-ttu-id="0e1de-117">Синхронизация каталогов</span><span class="sxs-lookup"><span data-stu-id="0e1de-117">Directory synchronization</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="0e1de-p103">Установка и настройка Azure AD Connect для синхронизации каталогов с синхронизацией хэша паролей. Это действие не является обязательным для создания имитации конфигурации предприятия.</span><span class="sxs-lookup"><span data-stu-id="0e1de-p103">Install and configure Azure AD Connect for directory synchronization with password hash synchronization. This is an optional step if you want to build a simulated enterprise configuration.</span></span>
    
<span data-ttu-id="0e1de-120">Следующие статьи можно использовать для демонстрации компонентов корпоративного выпуска Office 365 в среде разработки и тестирования Office 365:</span><span class="sxs-lookup"><span data-stu-id="0e1de-120">For your Office 365 dev/test environment, use these articles to demonstrate enterprise features of Office 365:</span></span>
  
- [<span data-ttu-id="0e1de-121">Многофакторная проверка подлинности</span><span class="sxs-lookup"><span data-stu-id="0e1de-121">Multi-factor authentication</span></span>](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="0e1de-122">Настройте и протестируйте дополнительную проверку подлинности, отправив текстовое сообщение на свой смартфон для учетной записи, указанной при подписке на Office 365.</span><span class="sxs-lookup"><span data-stu-id="0e1de-122">Configure and test secondary authentication using a text message sent to your smart phone for an account in your Office 365 subscription.</span></span>
    
- [<span data-ttu-id="0e1de-123">Федеративное удостоверение</span><span class="sxs-lookup"><span data-stu-id="0e1de-123">Federated identity</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="0e1de-124">Настройка и демонстрация федеративной проверки подлинности для учетных записей, настроенных в доменных службах Active Directory (AD DS).</span><span class="sxs-lookup"><span data-stu-id="0e1de-124">Configure and demonstrate federated authentication with the accounts of an Active Directory Domain Services (AD DS) domain.</span></span>
    
- [<span data-ttu-id="0e1de-125">Расширенная защита от угроз</span><span class="sxs-lookup"><span data-stu-id="0e1de-125">Advanced Threat Protection</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="0e1de-126">Настройка и демонстрация Advanced Threat Protection — компонента Exchange Online Protection (EOP), позволяющего оградить электронную почту от вредоносных программ.</span><span class="sxs-lookup"><span data-stu-id="0e1de-126">Configure and demonstrate Advanced Threat Protection, which is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email.</span></span>

## <a name="simulated-cross-premises-devtest-environment"></a><span data-ttu-id="0e1de-127">Имитация распределенной среды разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="0e1de-127">Simulated cross-premises dev/test environments</span></span>

<span data-ttu-id="0e1de-128">Создание [имитации интрасети](simulated-cross-premises-virtual-network-in-azure.md), подключенной к виртуальной сети Azure в гибридной облачной конфигурации.</span><span class="sxs-lookup"><span data-stu-id="0e1de-128">Create a simulated intranet connected to an Azure virtual network in a hybrid cloud configuration.</span></span>
    
## <a name="sharepoint-server-2016-devtest-environment"></a><span data-ttu-id="0e1de-129">Среда разработки и тестирования SharePoint Server 2016</span><span class="sxs-lookup"><span data-stu-id="0e1de-129">SharePoint Server 2016 dev/test environment in Azure</span></span>

<span data-ttu-id="0e1de-130">Создание [односерверной фермы SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-dev-test-environment-in-azure) в службах инфраструктуры Azure.</span><span class="sxs-lookup"><span data-stu-id="0e1de-130">Build a single-server SharePoint Server 2016 farm in Azure infrastructure services.</span></span>

## <a name="microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="0e1de-131">Среда разработки и тестирования Microsoft 365 корпоративный</span><span class="sxs-lookup"><span data-stu-id="0e1de-131">The Microsoft 365 Enterprise dev/test environment</span></span>

<span data-ttu-id="0e1de-132">Создание среды разработки и тестирования для [Microsoft 365 корпоративный](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides).</span><span class="sxs-lookup"><span data-stu-id="0e1de-132">Create dev/test environment for [Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides) with these articles.</span></span>  
    
## <a name="see-also"></a><span data-ttu-id="0e1de-133">См. также</span><span class="sxs-lookup"><span data-stu-id="0e1de-133">See Also</span></span>

[<span data-ttu-id="0e1de-134">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="0e1de-134">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="0e1de-135">Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="0e1de-135">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="0e1de-136">Архитектурные модели для SharePoint, Exchange, Skype для бизнеса и Lync</span><span class="sxs-lookup"><span data-stu-id="0e1de-136">Architectural models for SharePoint, Exchange, Skype for Business, and Lync</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[<span data-ttu-id="0e1de-137">Гибридные решения</span><span class="sxs-lookup"><span data-stu-id="0e1de-137">Hybrid solutions</span></span>](hybrid-solutions.md)
