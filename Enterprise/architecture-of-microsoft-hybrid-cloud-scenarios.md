---
title: Архитектура гибридного облака Майкрософт
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 06d8c959-39e5-4150-b1ae-aaf0eee4c058
description: Сводка. Сведения об архитектуре гибридных облачных предложений Майкрософт.
ms.openlocfilehash: f5493c0f008b22af412ee95ccb8b7581eee71476
ms.sourcegitcommit: 201d3338d8bbc6da9389e62e2add8a17384fab4d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2019
ms.locfileid: "31038013"
---
# <a name="architecture-of-microsoft-hybrid-cloud-scenarios"></a><span data-ttu-id="3352a-103">Архитектура гибридного облака Майкрософт</span><span class="sxs-lookup"><span data-stu-id="3352a-103">Architecture of Microsoft hybrid cloud scenarios</span></span>

 <span data-ttu-id="3352a-104">**Сводка.** Сведения об архитектуре гибридных облачных предложений Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="3352a-104">**Summary:** Understand the architecture of Microsoft's hybrid cloud offerings.</span></span>
  
<span data-ttu-id="3352a-105">Используйте архитектурный подход при планировании и применении сценариев гибридного облака в облачных службах и платформах Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="3352a-105">Use an architectural approach to plan and implement hybrid cloud scenarios with Microsoft cloud services and platforms.</span></span>
  
<span data-ttu-id="3352a-106">**Рис. 1. Стек гибридного облака Майкрософт**</span><span class="sxs-lookup"><span data-stu-id="3352a-106">**Figure 1: The Microsoft hybrid cloud stack**</span></span>

![Стек гибридного облака Microsoft](media/Hybrid-Poster/Hybrid-Cloud-Stack.png)
  
<span data-ttu-id="3352a-108">На рисунке 1 показан стек гибридного облака Майкрософт и его слои: локальная среда, сеть, удостоверение, приложения и сценарии, а также категория облачной службы (Microsoft SaaS Azure PaaS и Azure PaaS).</span><span class="sxs-lookup"><span data-stu-id="3352a-108">Figure 1 shows the Microsoft hybrid cloud stack and its layer, which include on-premises, network, Identity, apps and scenarios, and the category of cloud service (Microsoft SaaS, Azure PaaS, and Azure PaaS).</span></span>
  
<span data-ttu-id="3352a-109">Уровень приложений и сценариев содержит конкретные сценарии гибридного облака, которые подробно описаны в дополнительных статьях этой модели.</span><span class="sxs-lookup"><span data-stu-id="3352a-109">The Apps and scenarios layer has the specific hybrid cloud scenarios that are detailed in the additional articles of this model.</span></span> <span data-ttu-id="3352a-110">Слои "Удостоверение", "Сеть" и "Локальная среда" могут быть общими для категорий облачных служб (SaaS, PaaS или PaaS).</span><span class="sxs-lookup"><span data-stu-id="3352a-110">The Identity, Network, and On-premises layers can be common to the categories of cloud service (SaaS, PaaS, or PaaS).</span></span>
  
- <span data-ttu-id="3352a-111">Локальная среда</span><span class="sxs-lookup"><span data-stu-id="3352a-111">On-premises</span></span>
    
    <span data-ttu-id="3352a-p102">Локальная инфраструктура для гибридных сценариев может включать серверы SharePoint, Exchange, Skype для бизнеса и бизнес-приложений. Она также может содержать хранилища данных (базы данных, списки и файлы). Без подключений ExpressRoute доступ к локальным хранилищам данных должен предоставляться через обратный прокси-сервер или путем открытия доступа к серверу или данным в DMZ или экстрасети.</span><span class="sxs-lookup"><span data-stu-id="3352a-p102">On-premises infrastructure for hybrid scenarios can include servers for SharePoint, Exchange, Skype for Business, and line of business applications. It can also include data stores (databases, lists, files). Without ExpressRoute connections, access to the on-premises data stores must be allowed through a reverse proxy or by making the server or data accessible on your DMZ or extranet.</span></span>
    
- <span data-ttu-id="3352a-115">Сеть</span><span class="sxs-lookup"><span data-stu-id="3352a-115">Network</span></span>
    
    <span data-ttu-id="3352a-116">Существует два варианта подключения к облачным платформам и службам Майкрософт: существующий интернет-канал и ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="3352a-116">There are two choices for connectivity to Microsoft cloud platforms and services: your existing Internet pipe and ExpressRoute.</span></span> <span data-ttu-id="3352a-117">Если важна предсказуемая производительность, используется подключение ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="3352a-117">Use an ExpressRoute connection if predictable performance is important.</span></span> <span data-ttu-id="3352a-118">Вы можете использовать одно подключение ExpressRoute для прямого подключения к службам Microsoft SaaS (Office 365 и Dynamics 365), службам Azure PaaS и службам Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="3352a-118">You can use one ExpressRoute connection to connect directly to Microsoft SaaS services (Office 365 and Dynamics 365), Azure PaaS services, and Azure IaaS services.</span></span>
    
- <span data-ttu-id="3352a-119">Удостоверение</span><span class="sxs-lookup"><span data-stu-id="3352a-119">Identity</span></span>
    
    <span data-ttu-id="3352a-120">Для инфраструктуры облачных удостоверений существует два варианта в зависимости от облачной платформы Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="3352a-120">For cloud identity infrastructure, there are two ways to go, depending on the Microsoft cloud platform.</span></span> <span data-ttu-id="3352a-121">Для SaaS и Azure PaaS можно интегрировать локальную инфраструктуру удостоверений с Azure AD или создать федерацию с локальной инфраструктурой удостоверений или сторонними поставщиками удостоверений.</span><span class="sxs-lookup"><span data-stu-id="3352a-121">For SaaS and Azure PaaS, integrate your on-premises identity infrastructure with Azure AD or federate with your on-premises identity infrastructure or third-party identity providers.</span></span> <span data-ttu-id="3352a-122">Для виртуальных машин, работающих в Azure, вы можете расширить свою локальную инфраструктуру идентификации, например доменные службы Active Directory (AD DS), на виртуальные сети (виртуальных сетей), в которых находятся виртуальные машины.</span><span class="sxs-lookup"><span data-stu-id="3352a-122">For VMs running in Azure, you can extend your on-premises identity infrastructure, such as Active Directory Domain Services (AD DS), to the virtual networks (VNets) where your VMs reside.</span></span>
    
## <a name="hybrid-cloud-scenarios-for-the-three-phase-cloud-adoption-process"></a><span data-ttu-id="3352a-123">Сценарии гибридного облака для трехэтапного процесса принятия облака</span><span class="sxs-lookup"><span data-stu-id="3352a-123">Hybrid cloud scenarios for the three-phase cloud adoption process</span></span>

<span data-ttu-id="3352a-p105">Многие предприятия, в том числе корпорация Майкрософт, при принятии облака используют трехэтапный подход. Сценарии гибридного облака могут играть значительную роль на каждом этапе.</span><span class="sxs-lookup"><span data-stu-id="3352a-p105">Many enterprises, including Microsoft's, use a three-phase approach to adopting the cloud. Hybrid cloud scenarios can play a role in each phase.</span></span>
  
1. <span data-ttu-id="3352a-126">Перемещение рабочих нагрузок в SaaS</span><span class="sxs-lookup"><span data-stu-id="3352a-126">Move productivity workloads to SaaS</span></span>
    
    <span data-ttu-id="3352a-127">Если рабочие нагрузки в настоящее время находятся или должны находиться в локальной среде, гибридные сценарии позволяют интегрировать их с аналогичными рабочими нагрузками в облаке.</span><span class="sxs-lookup"><span data-stu-id="3352a-127">For productivity workloads that currently are or must stay on-premises, hybrid scenarios allow them to be integrated with their cloud counterparts.</span></span>
    
2. <span data-ttu-id="3352a-128">Разработка новых и современных приложений в Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="3352a-128">Develop new and modern applications in Azure PaaS</span></span>
    
    <span data-ttu-id="3352a-129">Гибридные приложения Azure PaaS могут безопасно использовать локальный сервер или ресурсы хранилища.</span><span class="sxs-lookup"><span data-stu-id="3352a-129">Azure PaaS hybrid applications can securely leverage on-premises server or storage resources.</span></span>
    
3. <span data-ttu-id="3352a-130">Перемещение существующих приложений в Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="3352a-130">Move existing applications to Azure IaaS</span></span>
    
    <span data-ttu-id="3352a-131">Для сценариев простого перемещения и встраивания в облако серверные приложения, запущенные на виртуальных машинах Azure, обеспечивают простую подготовку и масштабирование.</span><span class="sxs-lookup"><span data-stu-id="3352a-131">For lift-and-shift and build-in-the-cloud scenarios, server-based applications running on Azure VMs provide easy provisioning and scaling.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="3352a-132">См. также</span><span class="sxs-lookup"><span data-stu-id="3352a-132">See Also</span></span>

[<span data-ttu-id="3352a-133">Гибридное облако Майкрософт для корпоративных архитекторов</span><span class="sxs-lookup"><span data-stu-id="3352a-133">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="3352a-134">Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="3352a-134">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

