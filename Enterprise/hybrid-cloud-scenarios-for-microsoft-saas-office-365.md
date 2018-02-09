---
title: "Сценарии гибридного облака для Microsoft SaaS (Office 365)"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: "Сводка: Сведения о гибридных архитектуры и сценарии для Майкрософт на основе SaaS в облаке и услуги (Office 365)."
ms.openlocfilehash: 65b1841a155e286af8862c2fb7c37d0bfb61e1e8
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a><span data-ttu-id="9488c-103">Сценарии гибридного облака для Microsoft SaaS (Office 365)</span><span class="sxs-lookup"><span data-stu-id="9488c-103">Hybrid cloud scenarios for Microsoft SaaS (Office 365)</span></span>

 <span data-ttu-id="9488c-104">**Сводка:** Представление об архитектуре гибридного и сценарии для Майкрософт на основе SaaS в облаке и услуги (Office 365).</span><span class="sxs-lookup"><span data-stu-id="9488c-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's SaaS-based cloud offerings (Office 365).</span></span>
  
<span data-ttu-id="9488c-105">Объедините локальные развертывания Exchange, SharePoint или Skype для бизнеса с их аналогами в Office 365 в рамках переноса в облако или стратегии долгосрочной интеграции.</span><span class="sxs-lookup"><span data-stu-id="9488c-105">Combine on-premises deployments of Exchange, SharePoint, or Skype for Business with their counterparts in Office 365 as part of a cloud migration or long-term integration strategy.</span></span>
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a><span data-ttu-id="9488c-106">Архитектура гибридного сценария Microsoft SaaS</span><span class="sxs-lookup"><span data-stu-id="9488c-106">Microsoft SaaS hybrid scenario architecture</span></span>

<span data-ttu-id="9488c-107">На рисунке 1 показана архитектура гибридных сценариев на основе Microsoft SaaS для Office 365.</span><span class="sxs-lookup"><span data-stu-id="9488c-107">Figure 1 shows the architecture of Microsoft SaaS-based hybrid scenarios for Office 365.</span></span>
  
<span data-ttu-id="9488c-108">**На рисунке 1: Майкрософт на основе SaaS гибридных сценариев для Office 365**</span><span class="sxs-lookup"><span data-stu-id="9488c-108">**Figure 1: Microsoft SaaS-based hybrid scenarios for Office 365**</span></span>

![Гибридные сценарии на основе Microsoft SaaS для Office 365](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS.png)
  
<span data-ttu-id="9488c-110">Для каждого слоя архитектуры:</span><span class="sxs-lookup"><span data-stu-id="9488c-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="9488c-111">Приложения и сценарии</span><span class="sxs-lookup"><span data-stu-id="9488c-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="9488c-112">Существуют различные гибридные сценарии на основе SaaS, использующие серверные продукты Office и их аналоги в Office 365:</span><span class="sxs-lookup"><span data-stu-id="9488c-112">There are a variety of SaaS-based hybrid scenarios, aligning around Office Server products and their Office 365 counterparts:</span></span>
    
  - <span data-ttu-id="9488c-113">Exchange Server в сочетании с Exchange Online (гибридная среда Exchange Server);</span><span class="sxs-lookup"><span data-stu-id="9488c-113">Exchange Server combined with Exchange Online (Exchange Server hybrid)</span></span>
    
  - <span data-ttu-id="9488c-114">Skype для бизнеса Server в сочетании со Skype для бизнеса Online, а также новые сценарии "Облачная УАТС" и Cloud Connector Edition;</span><span class="sxs-lookup"><span data-stu-id="9488c-114">Skype for Business Server combined with Skype for Business Online and the new Cloud PBX and Cloud Connector Edition scenarios</span></span>
    
  - <span data-ttu-id="9488c-115">SharePoint Server 2016 или SharePoint Server 2013 в сочетании с SharePoint Online (несколько сценариев).</span><span class="sxs-lookup"><span data-stu-id="9488c-115">SharePoint Server 2016 or SharePoint Server 2013 combined with SharePoint Online (multiple scenarios)</span></span>
    
    <span data-ttu-id="9488c-116">Кроме того, есть следующий перекрестный гибридный сценарий: Exchange Online с локальным приложением Skype для бизнеса Server.</span><span class="sxs-lookup"><span data-stu-id="9488c-116">There is also Exchange Online with Skype for Business Server on-premises, a cross-product hybrid scenario.</span></span>
    
- <span data-ttu-id="9488c-117">Удостоверение</span><span class="sxs-lookup"><span data-stu-id="9488c-117">Identity</span></span>
    
    <span data-ttu-id="9488c-p101">Может включать синхронизацию службы каталогов с локальным каталогом Windows Server AD. В качестве альтернативы можно настроить федерацию Azure AD со сторонним поставщиком удостоверений.</span><span class="sxs-lookup"><span data-stu-id="9488c-p101">Can include directory synchronization with your on-premises Windows Server AD. Alternately, you can configure Azure AD to federate with a third-party identity provider.</span></span>
    
- <span data-ttu-id="9488c-120">Сеть</span><span class="sxs-lookup"><span data-stu-id="9488c-120">Network</span></span>
    
    <span data-ttu-id="9488c-121">Состоит из имеющегося интернет-канала или подключения ExpressRoute с пирингом Майкрософт для Office 365 или Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="9488c-121">Consists of either your existing Internet pipe or an ExpressRoute connection with Microsoft peering for Office 365 or Dynamics 365.</span></span>
    
- <span data-ttu-id="9488c-122">Локальная среда</span><span class="sxs-lookup"><span data-stu-id="9488c-122">On-premises</span></span>
    
    <span data-ttu-id="9488c-p102">Может состоять из имеющихся серверов Exchange, SharePoint и Skype для бизнеса, которые необходимо обновить до последних версий. После этого их можно объединить с аналогичными серверами Office 365 для гибридных сценариев.</span><span class="sxs-lookup"><span data-stu-id="9488c-p102">Can consist of existing servers for Exchange, SharePoint, and Skype for Business, which should be updated to their latest versions. You can then combine them with their Office 365 counterparts for hybrid scenarios.</span></span>
    
<span data-ttu-id="9488c-125">Настройка собственных [Office 365 dev/тестовой среды](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="9488c-125">Set up your own [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
## <a name="skype-for-business-2015-hybrid"></a><span data-ttu-id="9488c-126">Гибридный сценарий в Skype для бизнеса 2015</span><span class="sxs-lookup"><span data-stu-id="9488c-126">Skype for Business 2015 Hybrid</span></span>

<span data-ttu-id="9488c-p103">Скайп для гибридных 2015 Business позволяет объединять существующей в локальной среде с Скайп для бизнеса в Интернет. Некоторые пользователи, размещенные локально и некоторые пользователи размещаются в Интернете, но пользователи совместно использовать один домен Session Initiation Protocol (SIP), например contoso.com. В этом гибридной конфигурации можно использовать для переноса из локальной в Office 365 со временем в расписании. Скайп для бизнеса 2015 можно объединить с Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="9488c-p103">Skype for Business 2015 Hybrid allows you to combine an existing on-premises deployment with Skype for Business Online. Some users are homed on-premises and some users are homed online, but the users share the same Session Initiation Protocol (SIP) domain, such as contoso.com. You can use this hybrid configuration to migrate from on-premises to Office 365 over time, on your schedule. Skype for Business 2015 can also be integrated with Exchange Online.</span></span>
  
<span data-ttu-id="9488c-130">**На рисунке 2: Скайп для бизнеса 2015 гибридной конфигурации**</span><span class="sxs-lookup"><span data-stu-id="9488c-130">**Figure 2: The Skype for Business 2015 hybrid configuration**</span></span>

![Гибридная конфигурация Skype для бизнеса 2015](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SfB.png)
  
<span data-ttu-id="9488c-132">На рисунке 2 показано Скайп для бизнеса 2015 гибридной конфигурации, состоящий из локальной Скайп для бизнеса 2015 интерфейсного пула и пограничного сервера связи с Скайп для бизнеса в Интернет в Office 365.</span><span class="sxs-lookup"><span data-stu-id="9488c-132">Figure 2 shows the Skype for Business 2015 hybrid configuration, consisting of an on-premises Skype for Business 2015 front end pool and edge server communicating with Skype for Business Online in Office 365.</span></span>
  
<span data-ttu-id="9488c-133">Дополнительные сведения см. в следующих разделах:</span><span class="sxs-lookup"><span data-stu-id="9488c-133">For more information, see:</span></span>
  
- [<span data-ttu-id="9488c-134">Планирование гибридного подключения между Скайп для Business Server и Скайп для бизнеса в Интернет</span><span class="sxs-lookup"><span data-stu-id="9488c-134">Plan hybrid connectivity between Skype for Business Server and Skype for Business Online</span></span>](https://technet.microsoft.com/library/jj205403.aspx)
    
- [<span data-ttu-id="9488c-135">Поддерживаемые гибридные конфигурации для Скайп Business Server 2015</span><span class="sxs-lookup"><span data-stu-id="9488c-135">Supported hybrid configurations for Skype for Business Server 2015</span></span>](https://technet.microsoft.com/library/jj945633.aspx)
    
- [<span data-ttu-id="9488c-136">Скайп для гибридных бизнеса</span><span class="sxs-lookup"><span data-stu-id="9488c-136">Skype for Business Hybrid</span></span>](http://hybrid.office.com/skype-for-business/)
    
## <a name="cloud-pbx-with-skype-for-business-server"></a><span data-ttu-id="9488c-137">Облачная УАТС со Skype для бизнеса Server</span><span class="sxs-lookup"><span data-stu-id="9488c-137">Cloud PBX with Skype for Business Server</span></span>

<span data-ttu-id="9488c-138">Сценарий "Облачная УАТС со Skype для бизнеса Server" позволяет перенести имеющееся локальное развертывание Skype для бизнеса Server на топологию с возможностью подключения к локальной телефонной сети общего пользования (ТСОП). </span><span class="sxs-lookup"><span data-stu-id="9488c-138">Cloud PBX with Skype for Business Server allows you to transition an existing Skype for Business Server on-premises deployment to a topology with on-premises Public Switched Telephone Network (PSTN) connectivity.</span></span> 
  
<span data-ttu-id="9488c-139">**На рисунке 3: Cloud УАТС с Скайп для Business Server**</span><span class="sxs-lookup"><span data-stu-id="9488c-139">**Figure 3: Cloud PBX with Skype for Business Server**</span></span>

![Облачная УАТС со Skype для бизнеса Server](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SfB_CloudPBX.png)
  
<span data-ttu-id="9488c-141">На рисунке 3 показаны облачных УАТС с Скайп для конфигурации Business Server, состоящий из локальной, существующей УАТС или Telco шлюз, Скайп для Business Server и PSTN подключенный к УАТС облаке Майкрософт в Office 365, который включает в себя Скайп для бизнеса Онлайн.</span><span class="sxs-lookup"><span data-stu-id="9488c-141">Figure 3 shows the Cloud PBX with Skype for Business Server configuration, consisting of an on-premises existing PBX or Telco gateway, a Skype for Business Server, and the PSTN connected to the Microsoft Cloud PBX in Office 365, which includes Skype for Business Online.</span></span>
  
<span data-ttu-id="9488c-142">Пользователи в организации, расположенные в облаке, могут получать из облака Майкрософт службы УАТС, которые включают в себя передачу сигналов и голосовую почту, но подключение к ТСОП (гудок) осуществляется с помощью корпоративной голосовой связи из локального развертывания Skype для бизнеса Server.</span><span class="sxs-lookup"><span data-stu-id="9488c-142">Users in the organization who are homed in the cloud can receive private branch exchange (PBX) services from the Microsoft cloud that include signaling and voicemail, but PSTN connectivity (dial tone) is provided through Enterprise Voice from your on-premises Skype for Business Server deployment.</span></span>
  
<span data-ttu-id="9488c-p104">Вот хороший пример гибридной конфигурации, которая позволяет выполнить постепенный перенос в облачную службу. При переносе функций голосовой связи своих пользователей в Skype для бизнеса в Online вы можете сохранить эти функции. Перенос пользователей может выполняться в удобном для вас режиме, при этом вы можете быть уверены в том, что функции голосовой связи будут сохранены независимо от расположения пользователей. </span><span class="sxs-lookup"><span data-stu-id="9488c-p104">This is a great example of a hybrid configuration that allows you to gradually migrate to a cloud-based service. You can retain your users' voice capabilities as you begin to move them to Skype for Business Online. You can move your users at your own pace, knowing that their voice features will continue no matter where they are homed.</span></span> 
  
<span data-ttu-id="9488c-146">Дополнительные сведения см в [планировании гибридного подключения между Скайп Business Server и Скайп для бизнеса в Интернет или Lync Server 2013](https://technet.microsoft.com/library/jj205403.aspx).</span><span class="sxs-lookup"><span data-stu-id="9488c-146">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online or Lync Server 2013](https://technet.microsoft.com/library/jj205403.aspx).</span></span>
  
<span data-ttu-id="9488c-147">Если у вас пока не развернуто решение Lync Server или Skype для бизнеса Server, вы можете использовать Cloud Connector Edition для Skype для бизнеса, набор упакованных виртуальных машин, которые реализуют возможность подключения к ТСОП с помощью облачной УАТС.</span><span class="sxs-lookup"><span data-stu-id="9488c-147">If you do not already have an existing Lync Server or Skype for Business Server deployment, you can use Skype for Business Cloud Connector Edition, a set of packaged virtual machines (VMs) that implement on-premises PSTN connectivity with Cloud PBX.</span></span>
  
<span data-ttu-id="9488c-148">Для получения дополнительных сведений см [Скайп облаке соединитель для выпуска для бизнеса](https://technet.microsoft.com/library/mt605227.aspx).</span><span class="sxs-lookup"><span data-stu-id="9488c-148">For more information, see [Plan for Skype for Business Cloud Connector Edition](https://technet.microsoft.com/library/mt605227.aspx).</span></span>
  
## <a name="sharepoint-hybrid"></a><span data-ttu-id="9488c-149">Гибридная среда SharePoint</span><span class="sxs-lookup"><span data-stu-id="9488c-149">SharePoint Hybrid</span></span>

<span data-ttu-id="9488c-150">Гибридная среда SharePoint объединяет SharePoint Online в Office 365 с локальной фермой SharePoint в оптимальном решении с возможностями обоих продуктов.</span><span class="sxs-lookup"><span data-stu-id="9488c-150">SharePoint hybrid combines SharePoint Online in Office 365 with your on-premises SharePoint farm for a best of both worlds, connected experience.</span></span>
  
<span data-ttu-id="9488c-151">**На рисунке 4: Гибридной конфигурации SharePoint**</span><span class="sxs-lookup"><span data-stu-id="9488c-151">**Figure 4: The SharePoint hybrid configuration**</span></span>

![Гибридная конфигурация SharePoint](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SP.png)
  
<span data-ttu-id="9488c-153">На рисунке 4 показано гибридной конфигурации SharePoint, состоящий из локальной фермы SharePoint, данными с SharePoint Online в Office 365.</span><span class="sxs-lookup"><span data-stu-id="9488c-153">Figure 4 shows the SharePoint hybrid configuration, consisting of an on-premises SharePoint farm communicating with SharePoint Online in Office 365.</span></span>
  
<span data-ttu-id="9488c-154">Гибридные сценарии SharePoint</span><span class="sxs-lookup"><span data-stu-id="9488c-154">SharePoint hybrid scenarios:</span></span>
  
- [<span data-ttu-id="9488c-155">Гибридные OneDrive для бизнеса</span><span class="sxs-lookup"><span data-stu-id="9488c-155">Hybrid OneDrive for Business</span></span>](https://technet.microsoft.com/library/mt147425%28v=office.16%29.aspx)
    
- [<span data-ttu-id="9488c-156">Гибридные веб-сайтов групп</span><span class="sxs-lookup"><span data-stu-id="9488c-156">Hybrid team sites</span></span>](https://technet.microsoft.com/library/mt346110%28v=office.16%29.aspx)
    
- [<span data-ttu-id="9488c-157">Гибридные B2B экстрасети</span><span class="sxs-lookup"><span data-stu-id="9488c-157">Hybrid Extranet B2B</span></span>](https://support.office.com/article/SharePoint-Business-to-Business-Collaboration-Extranet-for-Partners-with-Office-365-7b087413-165a-4e94-8871-4393e0b9c037)
    
- [<span data-ttu-id="9488c-158">Гибридного поиска</span><span class="sxs-lookup"><span data-stu-id="9488c-158">Hybrid search</span></span>](https://technet.microsoft.com/library/dn720906%28v=office.16%29.aspx)
    
- [<span data-ttu-id="9488c-159">Гибридные профилей</span><span class="sxs-lookup"><span data-stu-id="9488c-159">Hybrid profiles</span></span>](https://support.office.com/article/Plan-hybrid-profiles-96d1eaf0-94eb-40c5-ab76-c82907777db4)
    
- [<span data-ttu-id="9488c-160">Средство выбора гибридного</span><span class="sxs-lookup"><span data-stu-id="9488c-160">Hybrid Picker</span></span>](https://support.office.com/article/Hybrid-picker-in-the-SharePoint-Online-admin-center-efce8417-c9bc-4a2c-ac9d-cce6c4e84a9c)
    
    <span data-ttu-id="9488c-161">Гибридные сценарии можно легко включить с помощью мастеров, которые автоматически реализуют гибридные конфигурации, доступные в Центре администрирования SharePoint Online в Office 365.</span><span class="sxs-lookup"><span data-stu-id="9488c-161">It is easy to enable hybrid scenarios using the wizards that automate hybrid configuration, available from the SharePoint Online admin center in Office 365.</span></span>
    
- [<span data-ttu-id="9488c-162">Расширяемые гибридного запуска приложения</span><span class="sxs-lookup"><span data-stu-id="9488c-162">Extensible hybrid app launcher</span></span>](https://support.office.com/article/The-extensible-hybrid-app-launcher-617a7cb5-53da-4128-961a-64a840c0ab91)
    
    <span data-ttu-id="9488c-163">Позволяет пользователям просматривать и использовать видео Office 365, а также приложения и возможности Delve на страницах их локальной фермы SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9488c-163">Allows users to view and use Office 365 video and Delve apps and experiences within the pages of their on-premises SharePoint farm.</span></span>
    
<span data-ttu-id="9488c-164">Все эти гибридные сценарии SharePoint, за исключением расширяемого гибридного средства запуска приложений, доступны пользователям SharePoint 2016 и SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="9488c-164">All of these SharePoint hybrid scenarios, except the Extensible hybrid app launcher, are available for both SharePoint 2016 and SharePoint 2013 users.</span></span>
  
<span data-ttu-id="9488c-165">Для получения дополнительных сведений см [Гибридной среды SharePoint](http://hybrid.office.com/sharepoint/).</span><span class="sxs-lookup"><span data-stu-id="9488c-165">For more information, see [SharePoint Hybrid](http://hybrid.office.com/sharepoint/).</span></span>
  
## <a name="exchange-server-2016-hybrid"></a><span data-ttu-id="9488c-166">Гибридный сценарий в Exchange Server 2016</span><span class="sxs-lookup"><span data-stu-id="9488c-166">Exchange Server 2016 Hybrid</span></span>

<span data-ttu-id="9488c-167">Гибридный сценарий в Exchange Server 2016 позволяет пользователям в сети воспользоваться преимуществами Exchange Online в Office 365, в то время как локальные пользователи смогут и дальше использовать имеющуюся инфраструктуру Exchange Server. </span><span class="sxs-lookup"><span data-stu-id="9488c-167">With Exchange Server 2016 Hybrid, you can realize the benefits of Exchange Online in Office 365 for online users while on-premises users continue to use existing Exchange Server infrastructure.</span></span> 
  
<span data-ttu-id="9488c-168">**На рисунке 5: Exchange 2016 гибридной конфигурации**</span><span class="sxs-lookup"><span data-stu-id="9488c-168">**Figure 5: The Exchange 2016 hybrid configuration**</span></span>

![Гибридная конфигурация Exchange 2016](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_EX.png)
  
<span data-ttu-id="9488c-170">На рисунке 5 показана конфигурация гибридного Exchange 2016, состоящий из локальных серверов почтовых ящиков Exchange связи с почтовых ящиков в Office 365 и Exchange Online Protection.</span><span class="sxs-lookup"><span data-stu-id="9488c-170">Figure 5 shows the Exchange 2016 hybrid configuration, consisting of on-premises Exchange mailbox servers communicating with Exchange Online Protection and mailboxes in Office 365.</span></span>
  
<span data-ttu-id="9488c-171">Некоторые пользователи применяют локальный сервер электронной почты, а другие — Exchange Online, но все пользователи совместно используют одно пространство адресов электронной почты. </span><span class="sxs-lookup"><span data-stu-id="9488c-171">Some users have an on-premises email server and some users use Exchange Online, but all users share the same e-mail address space.</span></span> 
  
<span data-ttu-id="9488c-172">Эта гибридная конфигурация:</span><span class="sxs-lookup"><span data-stu-id="9488c-172">This hybrid configuration:</span></span>
  
- <span data-ttu-id="9488c-173">Использует существующую инфраструктуру Exchange Server при переходе на Exchange Online со временем в расписании.</span><span class="sxs-lookup"><span data-stu-id="9488c-173">Leverages your existing Exchange Server infrastructure while you migrate to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="9488c-174">позволяет обеспечить поддержку удаленных сайтов без инвестиций в создание инфраструктуры филиалов;</span><span class="sxs-lookup"><span data-stu-id="9488c-174">Allows you to support remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="9488c-175">позволяет направить входящую электронную почту через Exchange Online Protection в Office 365;</span><span class="sxs-lookup"><span data-stu-id="9488c-175">Allows you to route incoming Internet email through Exchange Online Protection in Office 365.</span></span>
    
- <span data-ttu-id="9488c-176">выполняет задачи транснациональных организаций с дочерними компаниями, которым необходимо локальное размещение данных.</span><span class="sxs-lookup"><span data-stu-id="9488c-176">Serves the needs of multinational organizations with subsidiaries that require data to reside on-premises.</span></span>
    
<span data-ttu-id="9488c-177">Вы также можете интегрировать эту гибридную конфигурацию с другими приложениями Microsoft Office 365, в том числе Skype для бизнеса Online и SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="9488c-177">You can also integrate this hybrid configuration with other Microsoft Office 365 applications, including Skype for Business Online and SharePoint Online.</span></span>
  
<span data-ttu-id="9488c-178">Для получения дополнительных сведений см [Гибридные развертывания Exchange Server](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx) и [Гибридное развертывание Exchange](http://hybrid.office.com/exchange/).</span><span class="sxs-lookup"><span data-stu-id="9488c-178">For more information, see [Exchange Server Hybrid Deployments](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx) and [Exchange Hybrid](http://hybrid.office.com/exchange/).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9488c-179">См. также</span><span class="sxs-lookup"><span data-stu-id="9488c-179">See Also</span></span>

[<span data-ttu-id="9488c-180">Гибридное облако Майкрософт для корпоративных архитекторов</span><span class="sxs-lookup"><span data-stu-id="9488c-180">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="9488c-181">Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="9488c-181">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="9488c-182">Стратегия Enterprise Cloud корпорации Майкрософт: ресурсы для лиц, принимающих решения в области ИТ</span><span class="sxs-lookup"><span data-stu-id="9488c-182">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



