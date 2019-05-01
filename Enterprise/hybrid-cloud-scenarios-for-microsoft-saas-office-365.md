---
title: Сценарии гибридного облака для Microsoft SaaS (Office 365)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: Сводка. сведения о гибридной архитектуре и сценариях для облачных услуг Майкрософт на основе SaaS (Office 365).
ms.openlocfilehash: 90b751e4bbea42d723961eb2ac339d23faf8c259
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487530"
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a><span data-ttu-id="501d4-103">Гибридные облачные сценарии для SaaS Майкрософт (Office 365)</span><span class="sxs-lookup"><span data-stu-id="501d4-103">Hybrid cloud scenarios for Microsoft SaaS (Office 365)</span></span>

 <span data-ttu-id="501d4-104">**Сводка:** Узнайте, как гибридная архитектура и сценарии для облачных услуг Майкрософт на основе SaaS (Office 365).</span><span class="sxs-lookup"><span data-stu-id="501d4-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's SaaS-based cloud offerings (Office 365).</span></span>
  
<span data-ttu-id="501d4-105">Объедините локальные развертывания Exchange, SharePoint или Skype для бизнеса с их аналогами в Office 365 в рамках переноса в облако или стратегии долгосрочной интеграции.</span><span class="sxs-lookup"><span data-stu-id="501d4-105">Combine on-premises deployments of Exchange, SharePoint, or Skype for Business with their counterparts in Office 365 as part of a cloud migration or long-term integration strategy.</span></span>
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a><span data-ttu-id="501d4-106">Архитектура гибридного сценария Microsoft SaaS</span><span class="sxs-lookup"><span data-stu-id="501d4-106">Microsoft SaaS hybrid scenario architecture</span></span>

<span data-ttu-id="501d4-107">На рисунке 1 показана архитектура гибридных сценариев на основе Microsoft SaaS для Office 365.</span><span class="sxs-lookup"><span data-stu-id="501d4-107">Figure 1 shows the architecture of Microsoft SaaS-based hybrid scenarios for Office 365.</span></span>
  
<span data-ttu-id="501d4-108">**Рис. 1. Гибридные сценарии на основе Microsoft SaaS для Office 365**</span><span class="sxs-lookup"><span data-stu-id="501d4-108">**Figure 1: Microsoft SaaS-based hybrid scenarios for Office 365**</span></span>

![Гибридные сценарии на основе Microsoft SaaS для Office 365](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS.png)
  
<span data-ttu-id="501d4-110">Для каждого слоя архитектуры:</span><span class="sxs-lookup"><span data-stu-id="501d4-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="501d4-111">Приложения и сценарии</span><span class="sxs-lookup"><span data-stu-id="501d4-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="501d4-112">Существуют различные гибридные сценарии на основе SaaS, использующие серверные продукты Office и их аналоги в Office 365:</span><span class="sxs-lookup"><span data-stu-id="501d4-112">There are a variety of SaaS-based hybrid scenarios, aligning around Office Server products and their Office 365 counterparts:</span></span>
    
  - <span data-ttu-id="501d4-113">Exchange Server в сочетании с Exchange Online (гибридная среда Exchange Server);</span><span class="sxs-lookup"><span data-stu-id="501d4-113">Exchange Server combined with Exchange Online (Exchange Server hybrid)</span></span>
    
  - <span data-ttu-id="501d4-114">Skype для бизнеса Server в сочетании со Skype для бизнеса Online, а также новые сценарии "Облачная УАТС" и Cloud Connector Edition;</span><span class="sxs-lookup"><span data-stu-id="501d4-114">Skype for Business Server combined with Skype for Business Online and the new Cloud PBX and Cloud Connector Edition scenarios</span></span>
    
  - <span data-ttu-id="501d4-115">SharePoint Server 2019, SharePoint Server 2016 или SharePoint Server 2013 в сочетании с SharePoint Online (несколько сценариев)</span><span class="sxs-lookup"><span data-stu-id="501d4-115">SharePoint Server 2019, SharePoint Server 2016, or SharePoint Server 2013 combined with SharePoint Online (multiple scenarios)</span></span>
    
    <span data-ttu-id="501d4-116">Кроме того, есть следующий перекрестный гибридный сценарий: Exchange Online с локальным приложением Skype для бизнеса Server.</span><span class="sxs-lookup"><span data-stu-id="501d4-116">There is also Exchange Online with Skype for Business Server on-premises, a cross-product hybrid scenario.</span></span>
    
- <span data-ttu-id="501d4-117">Идентификация</span><span class="sxs-lookup"><span data-stu-id="501d4-117">Identity</span></span>
    
    <span data-ttu-id="501d4-118">Может включать синхронизацию службы каталогов с локальными доменными службами Active Directory (AD DS).</span><span class="sxs-lookup"><span data-stu-id="501d4-118">Can include directory synchronization with your on-premises Active Directory Domain Services (AD DS).</span></span> <span data-ttu-id="501d4-119">В качестве альтернативы можно настроить федерацию Azure AD со сторонним поставщиком удостоверений.</span><span class="sxs-lookup"><span data-stu-id="501d4-119">Alternately, you can configure Azure AD to federate with a third-party identity provider.</span></span>
    
- <span data-ttu-id="501d4-120">Сеть</span><span class="sxs-lookup"><span data-stu-id="501d4-120">Network</span></span>
    
    <span data-ttu-id="501d4-121">Состоит из имеющегося интернет-канала или подключения ExpressRoute с пирингом Майкрософт для Office 365 или Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="501d4-121">Consists of either your existing Internet pipe or an ExpressRoute connection with Microsoft peering for Office 365 or Dynamics 365.</span></span>
    
- <span data-ttu-id="501d4-122">Локальная среда</span><span class="sxs-lookup"><span data-stu-id="501d4-122">On-premises</span></span>
    
    <span data-ttu-id="501d4-p102">Может состоять из имеющихся серверов Exchange, SharePoint и Skype для бизнеса, которые необходимо обновить до последних версий. После этого их можно объединить с аналогичными серверами Office 365 для гибридных сценариев.</span><span class="sxs-lookup"><span data-stu-id="501d4-p102">Can consist of existing servers for Exchange, SharePoint, and Skype for Business, which should be updated to their latest versions. You can then combine them with their Office 365 counterparts for hybrid scenarios.</span></span>
    
<span data-ttu-id="501d4-125">Настройте собственную среду разработки и тестирования Office 365, ознакомьтесь с [руководством по лаборатории тестирования office 365](cloud-adoption-test-lab-guides-tlgs.md).</span><span class="sxs-lookup"><span data-stu-id="501d4-125">Set up your own Office 365 dev/test environment, see [Office 365 Test Lab Guides](cloud-adoption-test-lab-guides-tlgs.md).</span></span>
  
## <a name="skype-for-business-hybrid"></a><span data-ttu-id="501d4-126">Гибридное развертывание Skype для бизнеса</span><span class="sxs-lookup"><span data-stu-id="501d4-126">Skype for Business Hybrid</span></span>

<span data-ttu-id="501d4-127">Гибридная среда Skype для бизнеса позволяет объединить существующее локальное развертывание с Skype для бизнеса Online.</span><span class="sxs-lookup"><span data-stu-id="501d4-127">Skype for Business Hybrid lets you combine an existing on-premises deployment with Skype for Business Online.</span></span> <span data-ttu-id="501d4-128">Часть пользователей размещена в локальной среде, а другая часть — в Интернете, но все они используют один домен SIP, например contoso.com.</span><span class="sxs-lookup"><span data-stu-id="501d4-128">Some users are homed on-premises and some users are homed online, but the users share the same Session Initiation Protocol (SIP) domain, such as contoso.com.</span></span> <span data-ttu-id="501d4-129">Эта гибридная конфигурация позволяет постепенно перенести данные из локальной среды в Office 365 по заданному вами расписанию.</span><span class="sxs-lookup"><span data-stu-id="501d4-129">You can use this hybrid configuration to migrate from on-premises to Office 365 over time, on your schedule.</span></span> <span data-ttu-id="501d4-130">Skype для бизнеса также может быть интегрирован с [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint).</span><span class="sxs-lookup"><span data-stu-id="501d4-130">Skype for Business can also be integrated with [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint).</span></span>
  
<span data-ttu-id="501d4-131">**Рисунок 2: Гибридная конфигурация Skype для бизнеса**</span><span class="sxs-lookup"><span data-stu-id="501d4-131">**Figure 2: The Skype for Business hybrid configuration**</span></span>

![Гибридная конфигурация Skype для бизнеса](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB.png)
  
<span data-ttu-id="501d4-133">На рисунке 2 показана гибридная конфигурация Skype для бизнеса, состоящая из локального интерфейсного пула Skype для бизнеса и пограничного сервера, взаимодействующего со Skype для бизнеса Online в Office 365.</span><span class="sxs-lookup"><span data-stu-id="501d4-133">Figure 2 shows the Skype for Business hybrid configuration, consisting of an on-premises Skype for Business front end pool and edge server communicating with Skype for Business Online in Office 365.</span></span>
  
<span data-ttu-id="501d4-134">Для получения дополнительных сведений ознакомьтесь [со статьЕй планирование гибридного подключения между Skype для бизнеса Server и Skype для бизнеса Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span><span class="sxs-lookup"><span data-stu-id="501d4-134">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span></span>
    
## <a name="cloud-pbx-with-skype-for-business-server"></a><span data-ttu-id="501d4-135">Облачная УАТС со Skype для бизнеса Server</span><span class="sxs-lookup"><span data-stu-id="501d4-135">Cloud PBX with Skype for Business Server</span></span>

<span data-ttu-id="501d4-136">Облачная УАТС со Skype для бизнеса Server позволяет переходить из существующего локального развертывания Skype для бизнеса Server в топологию с подключением к локальной телефонной сети общего пользования (PSTN).</span><span class="sxs-lookup"><span data-stu-id="501d4-136">Cloud PBX with Skype for Business Server lets you transition an existing Skype for Business Server on-premises deployment to a topology with on-premises Public Switched Telephone Network (PSTN) connectivity.</span></span> 
  
<span data-ttu-id="501d4-137">**Рис. 3. Облачная УАТС со Skype для бизнеса Server**</span><span class="sxs-lookup"><span data-stu-id="501d4-137">**Figure 3: Cloud PBX with Skype for Business Server**</span></span>

![Облачная УАТС со Skype для бизнеса Server](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB-CloudPBX.png)
  
<span data-ttu-id="501d4-139">На рисунке 3 показана облачная УАТС с конфигурацией Skype для бизнеса Server, состоящей из локального существующего шлюза УАТС или Telco, Skype для бизнеса Server и PSTN, подключенного к облачной УАТС Майкрософт в Office 365, которая включает Skype для бизнеса Онлайн.</span><span class="sxs-lookup"><span data-stu-id="501d4-139">Figure 3 shows the Cloud PBX with Skype for Business Server configuration, consisting of an on-premises existing PBX or Telco gateway, a Skype for Business Server, and the PSTN connected to the Microsoft Cloud PBX in Office 365, which includes Skype for Business Online.</span></span>
  
<span data-ttu-id="501d4-140">Пользователи в организации, расположенные в облаке, могут получать из облака Майкрософт службы УАТС, которые включают в себя передачу сигналов и голосовую почту, но подключение к ТСОП (гудок) осуществляется с помощью корпоративной голосовой связи из локального развертывания Skype для бизнеса Server.</span><span class="sxs-lookup"><span data-stu-id="501d4-140">Users in the organization who are homed in the cloud can receive private branch exchange (PBX) services from the Microsoft cloud that include signaling and voicemail, but PSTN connectivity (dial tone) is provided through Enterprise Voice from your on-premises Skype for Business Server deployment.</span></span>
  
<span data-ttu-id="501d4-141">Это отличный пример гибридной конфигурации, который позволяет постепенно переходить на облачную службу.</span><span class="sxs-lookup"><span data-stu-id="501d4-141">This is a great example of a hybrid configuration that lets you gradually migrate to a cloud-based service.</span></span> <span data-ttu-id="501d4-142">При переносе функций голосовой связи своих пользователей в Skype для бизнеса в Online вы можете сохранить эти функции.</span><span class="sxs-lookup"><span data-stu-id="501d4-142">You can retain your users' voice capabilities as you begin to move them to Skype for Business Online.</span></span> <span data-ttu-id="501d4-143">Перенос пользователей может выполняться в удобном для вас режиме, при этом вы можете быть уверены в том, что функции голосовой связи будут сохранены независимо от расположения пользователей.</span><span class="sxs-lookup"><span data-stu-id="501d4-143">You can move your users at your own pace, knowing that their voice features will continue no matter where they are homed.</span></span> 
  
<span data-ttu-id="501d4-144">Для получения дополнительных сведений ознакомьтесь [со статьЕй планирование гибридного подключения между Skype для бизнеса Server и Skype для бизнеса Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span><span class="sxs-lookup"><span data-stu-id="501d4-144">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span></span>
  
<span data-ttu-id="501d4-145">Если у вас пока не развернуто решение Lync Server или Skype для бизнеса Server, вы можете использовать Cloud Connector Edition для Skype для бизнеса, набор упакованных виртуальных машин, которые реализуют возможность подключения к ТСОП с помощью облачной УАТС.</span><span class="sxs-lookup"><span data-stu-id="501d4-145">If you do not already have an existing Lync Server or Skype for Business Server deployment, you can use Skype for Business Cloud Connector Edition, a set of packaged virtual machines (VMs) that implement on-premises PSTN connectivity with Cloud PBX.</span></span>
  
<span data-ttu-id="501d4-146">Более подробную информацию можно найти в статье [Plan for Skype for Business Cloud Connector Edition](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).</span><span class="sxs-lookup"><span data-stu-id="501d4-146">For more information, see [Plan for Skype for Business Cloud Connector Edition](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).</span></span>

  
## <a name="sharepoint-hybrid"></a><span data-ttu-id="501d4-147">Гибридная среда SharePoint</span><span class="sxs-lookup"><span data-stu-id="501d4-147">SharePoint Hybrid</span></span>

<span data-ttu-id="501d4-148">Гибридная среда SharePoint объединяет SharePoint Online в Office 365 с локальной фермой SharePoint в оптимальном решении с возможностями обоих продуктов.</span><span class="sxs-lookup"><span data-stu-id="501d4-148">SharePoint hybrid combines SharePoint Online in Office 365 with your on-premises SharePoint farm for a best of both worlds, connected experience.</span></span>
  
<span data-ttu-id="501d4-149">**Рис. 4. Гибридная конфигурация SharePoint**</span><span class="sxs-lookup"><span data-stu-id="501d4-149">**Figure 4: The SharePoint hybrid configuration**</span></span>

![Гибридная конфигурация SharePoint](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SP.png)
  
<span data-ttu-id="501d4-151">На рисунке 4 показана гибридная конфигурация SharePoint, состоящая из локальной фермы SharePoint, которая взаимодействует с SharePoint Online в Office 365.</span><span class="sxs-lookup"><span data-stu-id="501d4-151">Figure 4 shows the SharePoint hybrid configuration, consisting of an on-premises SharePoint farm communicating with SharePoint Online in Office 365.</span></span>
  
<span data-ttu-id="501d4-152">Гибридные сценарии SharePoint</span><span class="sxs-lookup"><span data-stu-id="501d4-152">SharePoint hybrid scenarios:</span></span>
  
- [<span data-ttu-id="501d4-153">Гибридная служба OneDrive для бизнеса</span><span class="sxs-lookup"><span data-stu-id="501d4-153">Hybrid OneDrive for Business</span></span>](https://docs.microsoft.com/SharePoint/hybrid/configure-hybrid-onedrive-for-businessroadmap)
    
- [<span data-ttu-id="501d4-154">Гибридная сеть B2B</span><span class="sxs-lookup"><span data-stu-id="501d4-154">Hybrid Extranet B2B</span></span>](https://docs.microsoft.com/sharepoint/create-b2b-extranet)
    
- [<span data-ttu-id="501d4-155">Гибридный поиск</span><span class="sxs-lookup"><span data-stu-id="501d4-155">Hybrid search</span></span>](https://docs.microsoft.com/SharePoint/hybrid/configure-cloud-hybrid-searchroadmap)
    
- [<span data-ttu-id="501d4-156">Гибридные профили</span><span class="sxs-lookup"><span data-stu-id="501d4-156">Hybrid profiles</span></span>](https://docs.microsoft.com/SharePoint/hybrid/plan-hybrid-profiles)
    
- [<span data-ttu-id="501d4-157">Мастер выбора гибридной конфигурации</span><span class="sxs-lookup"><span data-stu-id="501d4-157">Hybrid Picker</span></span>](https://docs.microsoft.com/SharePoint/hybrid/hybrid-picker-in-the-sharepoint-online-admin-center)
    
    <span data-ttu-id="501d4-158">Гибридные сценарии можно легко включить с помощью мастеров, которые автоматически реализуют гибридные конфигурации, доступные в Центре администрирования SharePoint Online в Office 365.</span><span class="sxs-lookup"><span data-stu-id="501d4-158">It is easy to enable hybrid scenarios using the wizards that automate hybrid configuration, available from the SharePoint Online admin center in Office 365.</span></span>
    
- [<span data-ttu-id="501d4-159">Расширяемое гибридное средство запуска приложений</span><span class="sxs-lookup"><span data-stu-id="501d4-159">Extensible hybrid app launcher</span></span>](https://docs.microsoft.com/SharePoint/hybrid/the-extensible-hybrid-app-launcher)
    
    <span data-ttu-id="501d4-160">Позволяет пользователям просматривать и использовать видео Office 365, а также приложения и возможности Delve на страницах их локальной фермы SharePoint.</span><span class="sxs-lookup"><span data-stu-id="501d4-160">Allows users to view and use Office 365 video and Delve apps and experiences within the pages of their on-premises SharePoint farm.</span></span>
    
<span data-ttu-id="501d4-161">Все эти гибридные сценарии SharePoint, за исключением расширяемого гибридного средства запуска приложений, доступны пользователям SharePoint 2016 и SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="501d4-161">All of these SharePoint hybrid scenarios, except the Extensible hybrid app launcher, are available for both SharePoint 2016 and SharePoint 2013 users.</span></span>
  
## <a name="exchange-server-2016-hybrid"></a><span data-ttu-id="501d4-162">Гибридный сценарий в Exchange Server 2016</span><span class="sxs-lookup"><span data-stu-id="501d4-162">Exchange Server 2016 Hybrid</span></span>

<span data-ttu-id="501d4-163">Гибридный сценарий в Exchange Server 2016 позволяет пользователям в сети воспользоваться преимуществами Exchange Online в Office 365, в то время как локальные пользователи смогут и дальше использовать имеющуюся инфраструктуру Exchange Server. </span><span class="sxs-lookup"><span data-stu-id="501d4-163">With Exchange Server 2016 Hybrid, you can realize the benefits of Exchange Online in Office 365 for online users while on-premises users continue to use existing Exchange Server infrastructure.</span></span> 
  
<span data-ttu-id="501d4-164">**Рис. 5. Гибридная конфигурация Exchange 2016**</span><span class="sxs-lookup"><span data-stu-id="501d4-164">**Figure 5: The Exchange 2016 hybrid configuration**</span></span>

![Гибридная конфигурация Exchange 2016](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-EX.png)
  
<span data-ttu-id="501d4-166">На рисунке 5 показана гибридная конфигурация Exchange 2016, состоящая из локальных серверов почтовых ящиков Exchange, взаимодействующих с Exchange Online Protection и почтовыми ящиками в Office 365.</span><span class="sxs-lookup"><span data-stu-id="501d4-166">Figure 5 shows the Exchange 2016 hybrid configuration, consisting of on-premises Exchange mailbox servers communicating with Exchange Online Protection and mailboxes in Office 365.</span></span>
  
<span data-ttu-id="501d4-167">Некоторые пользователи применяют локальный сервер электронной почты, а другие — Exchange Online, но все пользователи совместно используют одно пространство адресов электронной почты. </span><span class="sxs-lookup"><span data-stu-id="501d4-167">Some users have an on-premises email server and some users use Exchange Online, but all users share the same e-mail address space.</span></span> 
  
<span data-ttu-id="501d4-168">Эта гибридная конфигурация:</span><span class="sxs-lookup"><span data-stu-id="501d4-168">This hybrid configuration:</span></span>
  
- <span data-ttu-id="501d4-169">использует имеющуюся инфраструктуру Exchange Server при постепенном переносе данных на Exchange Online по расписанию;</span><span class="sxs-lookup"><span data-stu-id="501d4-169">Leverages your existing Exchange Server infrastructure while you migrate to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="501d4-170">позволяет обеспечить поддержку удаленных сайтов без инвестиций в создание инфраструктуры филиалов;</span><span class="sxs-lookup"><span data-stu-id="501d4-170">Allows you to support remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="501d4-171">позволяет направить входящую электронную почту через Exchange Online Protection в Office 365;</span><span class="sxs-lookup"><span data-stu-id="501d4-171">Allows you to route incoming Internet email through Exchange Online Protection in Office 365.</span></span>
    
- <span data-ttu-id="501d4-172">выполняет задачи транснациональных организаций с дочерними компаниями, которым необходимо локальное размещение данных.</span><span class="sxs-lookup"><span data-stu-id="501d4-172">Serves the needs of multinational organizations with subsidiaries that require data to reside on-premises.</span></span>
    
<span data-ttu-id="501d4-173">Вы также можете интегрировать эту гибридную конфигурацию с другими приложениями Microsoft Office 365, в том числе Skype для бизнеса Online и SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="501d4-173">You can also integrate this hybrid configuration with other Microsoft Office 365 applications, including Skype for Business Online and SharePoint Online.</span></span>
  
<span data-ttu-id="501d4-174">Для получения дополнительных сведений обратитесь к разделу [гибридНые развертывания Exchange Server](https://docs.microsoft.com/exchange/exchange-hybrid).</span><span class="sxs-lookup"><span data-stu-id="501d4-174">For more information, see [Exchange Server Hybrid Deployments](https://docs.microsoft.com/exchange/exchange-hybrid).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="501d4-175">См. также</span><span class="sxs-lookup"><span data-stu-id="501d4-175">See Also</span></span>

[<span data-ttu-id="501d4-176">Гибридное облако Майкрософт для корпоративных архитекторов</span><span class="sxs-lookup"><span data-stu-id="501d4-176">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="501d4-177">Ресурсы, посвященные ИТ-архитектуре Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="501d4-177">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

