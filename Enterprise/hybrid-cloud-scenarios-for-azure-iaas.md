---
title: Сценарии гибридного облака для Azure IaaS
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 978f2b76-5aba-4e11-9434-f0efda987be1
description: Сводка. сведения о гибридной архитектуре и сценариях для инфраструктуры корпорации Майкрософт в качестве облачного решения на основе службы IaaS в Azure.
ms.openlocfilehash: 429af408ca3f21fe667b36cdb9767d3916a6b1a4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067355"
---
# <a name="hybrid-cloud-scenarios-for-azure-iaas"></a><span data-ttu-id="a5572-103">Гибридные облачные сценарии для Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="a5572-103">Hybrid cloud scenarios for Azure IaaS</span></span>

 <span data-ttu-id="a5572-104">**Сводка:** В Azure вы ознакомитесь с архитектурой гибридной архитектуры и сценариями для инфраструктуры корпорации Майкрософт в качестве облачных служб (IaaS).</span><span class="sxs-lookup"><span data-stu-id="a5572-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Infrastructure as a Service (IaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="a5572-105">Расширьте свою локальную инфраструктуру вычислений и удостоверений с помощью облака, разместив рабочие ИТ-нагрузки, выполняемые в распределенных виртуальных сетях Azure.</span><span class="sxs-lookup"><span data-stu-id="a5572-105">Extend your on-premises computing and identity infrastructure into the cloud by hosting IT workloads running in cross-premises Azure virtual networks (VNets).</span></span> 
  
## <a name="azure-iaas-hybrid-scenario-architecture"></a><span data-ttu-id="a5572-106">Архитектура гибридного сценария Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="a5572-106">Azure IaaS hybrid scenario architecture</span></span>

<span data-ttu-id="a5572-107">На рисунке 1 показана архитектура гибридных сценариев на основе Microsoft IaaS в Azure.</span><span class="sxs-lookup"><span data-stu-id="a5572-107">Figure 1 shows the architecture of Microsoft IaaS-based hybrid scenarios in Azure.</span></span>
  
<span data-ttu-id="a5572-108">**Рис. 1. Гибридные сценарии на основе Microsoft IaaS в Azure**</span><span class="sxs-lookup"><span data-stu-id="a5572-108">**Figure 1: Microsoft IaaS-based hybrid scenarios in Azure**</span></span>

![Гибридные сценарии на основе Microsoft IaaS в Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS.png)
  
<span data-ttu-id="a5572-110">Для каждого слоя архитектуры:</span><span class="sxs-lookup"><span data-stu-id="a5572-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="a5572-111">Приложения и сценарии</span><span class="sxs-lookup"><span data-stu-id="a5572-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="a5572-112">Рабочая ИТ-нагрузка обычно представляет собой многоуровневое приложение высокой доступности, которое состоит из виртуальных машин Azure.</span><span class="sxs-lookup"><span data-stu-id="a5572-112">An IT workload is typically a multi-tier, highly-available application composed of Azure virtual machines (VMs).</span></span>
    
- <span data-ttu-id="a5572-113">Удостоверение</span><span class="sxs-lookup"><span data-stu-id="a5572-113">Identity</span></span>
    
    <span data-ttu-id="a5572-114">Добавьте серверы удостоверений, такие как контроллеры домена доменных служб Active Directory (AD DS), в набор серверов, работающих в Azure виртуальных сетей для локальной проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="a5572-114">Add identity servers, such as Active Directory Domain Services (AD DS) domain controllers, to the set of servers running in Azure VNets for local authentication.</span></span>
    
- <span data-ttu-id="a5572-115">Сеть</span><span class="sxs-lookup"><span data-stu-id="a5572-115">Network</span></span>
    
    <span data-ttu-id="a5572-116">Используйте подключение к VPN типа "сеть-сеть" в Интернете или подключение ExpressRoute с частным пирингом к Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="a5572-116">Use either a site-to-site VPN connection over the Internet or an ExpressRoute connection with private peering to Azure IaaS.</span></span>
    
- <span data-ttu-id="a5572-117">Локальная среда</span><span class="sxs-lookup"><span data-stu-id="a5572-117">On-premises</span></span>
    
    <span data-ttu-id="a5572-p101">Содержит серверы удостоверений, которые синхронизируются с серверами удостоверений в Azure. Также может содержать ресурсы, к которым имеют доступ виртуальные машины, работающие в Azure, например хранилище или инфраструктуру управления системами.</span><span class="sxs-lookup"><span data-stu-id="a5572-p101">Contains identity servers that are synchronized with the identity servers running in Azure. Can also contain resources that VMs running in Azure can access, such as storage and systems management infrastructure.</span></span>
    
## <a name="directory-synchronization-server-for-office-365"></a><span data-ttu-id="a5572-120">Сервер синхронизации каталогов для Office 365</span><span class="sxs-lookup"><span data-stu-id="a5572-120">Directory synchronization server for Office 365</span></span>

<span data-ttu-id="a5572-121">Запустите сервер синхронизации каталогов из виртуальной сети Azure, как показано на рисунке 2, — это пример расширения инфраструктуры инфраструктуры и идентификации в облако.</span><span class="sxs-lookup"><span data-stu-id="a5572-121">Running your directory synchronization server from an Azure VNet, as shown in Figure 2, is an example of extending your computing and identity infrastructure to the cloud.</span></span>
  
<span data-ttu-id="a5572-122">**Рисунок 2: сервер синхронизации каталогов для Office 365 в Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="a5572-122">**Figure 2: Directory synchronization server for Office 365 in Azure IaaS**</span></span>

![Сервер синхронизации каталогов для Office 365 в Azure IaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-DirSync.png)
  
<span data-ttu-id="a5572-124">На рисунке 2 в локальной сети размещается инфраструктура доменных служб Active Directory с прокси-сервером и маршрутизатором на его стороне.</span><span class="sxs-lookup"><span data-stu-id="a5572-124">In Figure 2, an on-premises network hosts a AD DS infrastructure, with a proxy server and a router at its edge.</span></span> <span data-ttu-id="a5572-125">Маршрутизатор подключается к шлюзу Azure на границе виртуальной сети Azure с подключением VPN типа "сеть-сеть" или ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="a5572-125">The router connects to an Azure gateway at the edge of an Azure VNet with a site-to-site VPN or ExpressRoute connection.</span></span> <span data-ttu-id="a5572-126">В виртуальной сети сервер синхронизации каталогов запускает Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="a5572-126">Inside the VNet, a directory synchronization server runs Azure AD Connect.</span></span>
  
<span data-ttu-id="a5572-127">Сервер синхронизации каталогов для Office 365 синхронизирует список учетных записей в доменных СЛУЖБах Active Directory с клиентом Azure AD подписки на Office 365.</span><span class="sxs-lookup"><span data-stu-id="a5572-127">A directory synchronization server for Office 365 synchronizes the list of accounts in AD DS with the Azure AD tenant of an Office 365 subscription.</span></span>
  
<span data-ttu-id="a5572-128">Сервер синхронизации службы каталогов — это сервер на основе Windows, на котором выполняется Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="a5572-128">A directory synchronization server is a Windows-based server that runs Azure AD Connect.</span></span> <span data-ttu-id="a5572-129">Для ускорения подготовки или уменьшения количества локальных серверов в Организации разверните сервер синхронизации каталогов в виртуальной сети (VNet) в Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="a5572-129">For faster provisioning or to reduce the number of on-premises servers in your organization, deploy your directory synchronization server in a virtual network (VNet) in Azure IaaS.</span></span>
  
<span data-ttu-id="a5572-130">Сервер синхронизации каталогов опрашивает AD DS на наличие изменений и синхронизирует их с подпиской на Office 365.</span><span class="sxs-lookup"><span data-stu-id="a5572-130">The directory synchronization server polls AD DS for changes and then synchronizes them with the Office 365 subscription.</span></span>
  
<span data-ttu-id="a5572-131">Дополнительные сведения см. [в статье Deploy Office 365 Directory Synchronization in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span><span class="sxs-lookup"><span data-stu-id="a5572-131">For more information, see [Deploy Office 365 Directory Synchronization in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span></span>
  
## <a name="line-of-business-lob-application"></a><span data-ttu-id="a5572-132">Бизнес-приложение</span><span class="sxs-lookup"><span data-stu-id="a5572-132">Line of business (LOB) application</span></span>

<span data-ttu-id="a5572-133">На рисунке 3 показана конфигурация серверного бизнес-приложения, работающего в Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="a5572-133">Figure 3 shows the configuration of a server-based LOB application running in Azure IaaS.</span></span>
  
<span data-ttu-id="a5572-134">**Рис. 3. Бизнес-приложение в Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="a5572-134">**Figure 3: LOB application in Azure IaaS**</span></span>

![Серверное бизнес-приложение в Azure IaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-Ex.png)
  
<span data-ttu-id="a5572-p104">На рисунке 3 показана локальная сеть, в которой размещены инфраструктура идентификации и пользователи. Она подключена к шлюзу Azure IaaS с помощью соединения VPN типа "сеть-сеть" или ExpressRoute. В Azure IaaS размещена виртуальная сеть, содержащая серверы бизнес-приложения.</span><span class="sxs-lookup"><span data-stu-id="a5572-p104">In Figure 3, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. Azure IaaS hosts a virtual network containing the servers of the LOB application.</span></span>
  
<span data-ttu-id="a5572-139">Вы можете создать бизнес-приложения, которые будут выполняться на виртуальных машинах Azure и размещаться в подсетях виртуальной сети Azure в центре данных Azure (который также называется расположением).</span><span class="sxs-lookup"><span data-stu-id="a5572-139">You can create LOB applications running on Azure VMs, which reside on subnets of an Azure VNet in an Azure datacenter (also known as a location).</span></span>
  
<span data-ttu-id="a5572-140">Так как вы, по сути, расширяете локальную инфраструктуру до Azure, необходимо назначить уникальное пространство частных адресов своим виртуальным сетям и обновить таблицы локальной маршрутизации, чтобы обеспечить доступность каждой виртуальной сети.</span><span class="sxs-lookup"><span data-stu-id="a5572-140">Because you are essentially extending your on-premises infrastructure to Azure, you must assign unique private address space to your VNets and update your on-premises routing tables to ensure reachability to each VNet.</span></span>
  
<span data-ttu-id="a5572-141">После подключения этими виртуальными машинами можно управлять с помощью подключений к удаленному рабочему столу или программного обеспечения для управления системами (так же, как и локальными серверами).</span><span class="sxs-lookup"><span data-stu-id="a5572-141">Once connected, these VMs can be managed with remote desktop connections or with your systems management software, just like your on-premises servers.</span></span>
  
<span data-ttu-id="a5572-142">После настройки общедоступных портов мобильные или удаленные пользователи также могут получить доступ к этим виртуальным машинам через Интернет.</span><span class="sxs-lookup"><span data-stu-id="a5572-142">By configuring publically-exposed ports, these VMs can also be accessed from the Internet by mobile or remote users.</span></span>
  
<span data-ttu-id="a5572-143">В случае конфигурации для подтверждения концепции см. статью [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="a5572-143">For a proof-of-concept configuration, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span>
  
<span data-ttu-id="a5572-144">Атрибуты бизнес-приложений, размещенных на виртуальных машинах Azure:</span><span class="sxs-lookup"><span data-stu-id="a5572-144">Attributes of LOB applications hosted on Azure VMs are the following:</span></span>
  
- <span data-ttu-id="a5572-145">Несколько уровней</span><span class="sxs-lookup"><span data-stu-id="a5572-145">Multiple tiers</span></span>
    
    <span data-ttu-id="a5572-p105">В типичных бизнес-приложениях используется многоуровневый подход. Наборы серверов обеспечивают обработку удостоверений, баз данных, приложений и логики, а также предоставляют интерфейсные веб-серверы для доступа со стороны сотрудников или клиентов. </span><span class="sxs-lookup"><span data-stu-id="a5572-p105">Typical LOB applications use a tiered approach. Sets of servers provide identity, database processing, application and logic processing, and front-end web servers for employee or customer access.</span></span> 
    
- <span data-ttu-id="a5572-148">Высокая доступность</span><span class="sxs-lookup"><span data-stu-id="a5572-148">High availability</span></span>
    
    <span data-ttu-id="a5572-p106">Типичные бизнес-приложения обеспечивают высокую доступность с помощью нескольких серверов на каждом уровне. Azure IaaS обеспечивает 99,9 % времени непрерывной работы (согласно SLA) для серверов в группах доступности Azure. </span><span class="sxs-lookup"><span data-stu-id="a5572-p106">Typical LOB applications provide high availability by using multiple servers in each tier. Azure IaaS provides a 99.9% uptime SLA for servers in Azure availability sets.</span></span> 
    
- <span data-ttu-id="a5572-151">Распределение нагрузки</span><span class="sxs-lookup"><span data-stu-id="a5572-151">Load distribution</span></span>
    
    <span data-ttu-id="a5572-p107">Чтобы распределить нагрузку сетевого трафика между несколькими серверами на одном уровне, можно использовать балансировщик нагрузки для Интернета или внутренний балансировщик нагрузки Azure. Можно также использовать специальный виртуальный модуль балансировки нагрузки, доступный в службе Azure Marketplace.</span><span class="sxs-lookup"><span data-stu-id="a5572-p107">To distribute the load of network traffic among multiple servers in a tier, you can use an Internet-facing or internal Azure load balancer. Or, you can use a dedicated load balancer appliance available from the Azure marketplace.</span></span>
    
- <span data-ttu-id="a5572-154">Безопасность</span><span class="sxs-lookup"><span data-stu-id="a5572-154">Security</span></span>
    
    <span data-ttu-id="a5572-p108">Чтобы защитить серверы от нежелательного входящего трафика из Интернета, можно использовать группы безопасности сети Azure. Вы можете определить допустимый или запрещенный трафик для подсети или сетевого интерфейса отдельных виртуальных машин.</span><span class="sxs-lookup"><span data-stu-id="a5572-p108">To protect servers from unsolicited incoming traffic from the Internet, you can use Azure network security groups. You can define allowed or denied traffic for a subnet or the network interface of an individual virtual machine.</span></span>
    
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="a5572-157">Ферма SharePoint Server 2016 в Azure</span><span class="sxs-lookup"><span data-stu-id="a5572-157">SharePoint Server 2016 farm in Azure</span></span>

<span data-ttu-id="a5572-158">Ферма SharePoint Server 2016, показанная на рисунке 4, является примером многоуровневого высокодоступного бизнес-приложения в Azure.</span><span class="sxs-lookup"><span data-stu-id="a5572-158">An example of a multi-tier, highly-available LOB application in Azure is a SharePoint Server 2016 farm, as shown in Figure 4.</span></span>
  
<span data-ttu-id="a5572-159">**Рис. 4. Высокодоступная ферма SharePoint Server 2016 в Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="a5572-159">**Figure 4: A high-availability SharePoint Server 2016 farm in Azure IaaS**</span></span>

![Ферма SharePoint Server 2016 С высоким уровнем доступности в Azure IaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-SP2016.png)
  
<span data-ttu-id="a5572-p109">На рисунке 4 показана локальная сеть, в которой размещены инфраструктура идентификации и пользователи. Она подключена к шлюзу Azure IaaS с помощью соединения VPN типа "сеть-сеть" или ExpressRoute. Виртуальная сеть Azure содержит серверы фермы SharePoint Server 2016, которая включает отдельные уровни для серверов переднего плана, серверов приложений, кластера SQL Server и контроллеров домена.</span><span class="sxs-lookup"><span data-stu-id="a5572-p109">In Figure 4, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. The Azure VNet contains the servers of the SharePoint Server 2016 farm, which includes separate tiers for the front-end servers, the application servers, the SQL Server cluster, and the domain controllers.</span></span>
  
<span data-ttu-id="a5572-164">У этой конфигурации есть указанные ниже атрибуты бизнес-приложений в Azure.</span><span class="sxs-lookup"><span data-stu-id="a5572-164">This configuration has the following attributes of LOB applications in Azure:</span></span> 
  
- <span data-ttu-id="a5572-165">Уровней</span><span class="sxs-lookup"><span data-stu-id="a5572-165">Tiers</span></span>
    
    <span data-ttu-id="a5572-166">Серверы, выполняющие разные роли в ферме, создают уровни, и каждый уровень имеет собственную подсеть.</span><span class="sxs-lookup"><span data-stu-id="a5572-166">Servers running different roles within the farm create the tiers and each tier has its own subnet.</span></span>
    
- <span data-ttu-id="a5572-167">Высокая доступность</span><span class="sxs-lookup"><span data-stu-id="a5572-167">High-availability</span></span>
    
    <span data-ttu-id="a5572-168">Достигается за счет использования нескольких серверов на каждом уровне и размещения всех серверов уровня в одной группе доступности.</span><span class="sxs-lookup"><span data-stu-id="a5572-168">Achieved by using more than one server in each tier and placing all the servers of a tier in the same availability set.</span></span>
    
- <span data-ttu-id="a5572-169">Распределение нагрузки</span><span class="sxs-lookup"><span data-stu-id="a5572-169">Load distribution</span></span>
    
    <span data-ttu-id="a5572-170">Внутренние балансировщики нагрузки Azure отправляют входящий клиентский веб-трафик на серверы переднего плана (WEB1 и WEB2) и на IP-адрес прослушивателя кластера SQL Server (SQL1, SQL2 и MN1).</span><span class="sxs-lookup"><span data-stu-id="a5572-170">Internal Azure load balancers distribute the incoming client web traffic to the front-end servers (WEB1 and WEB2) and to the listener IP address of the SQL Server cluster (SQL1, SQL2, and MN1).</span></span>
    
- <span data-ttu-id="a5572-171">Безопасность</span><span class="sxs-lookup"><span data-stu-id="a5572-171">Security</span></span>
    
    <span data-ttu-id="a5572-172">Группы безопасности сети для каждой подсети позволяют настроить разрешенный входящий и исходящий трафик.</span><span class="sxs-lookup"><span data-stu-id="a5572-172">Network security groups for each subnet let you to configure allowed inbound and outbound traffic.</span></span>
    
<span data-ttu-id="a5572-173">Используйте такой путь для успешного внедрения:</span><span class="sxs-lookup"><span data-stu-id="a5572-173">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="a5572-174">Оценка и эксперимент</span><span class="sxs-lookup"><span data-stu-id="a5572-174">Evaluate and experiment</span></span>
    
    <span data-ttu-id="a5572-175">Ознакомьтесь со статьей [SharePoint server 2016 в Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure) , чтобы понять преимущества запуска SharePoint Server 2016 в Azure.</span><span class="sxs-lookup"><span data-stu-id="a5572-175">See [SharePoint Server 2016 in Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure) to understand the benefits of running SharePoint Server 2016 in Azure.</span></span>
    
    <span data-ttu-id="a5572-176">Чтобы создать имитируемую среду разработки и тестирования, ознакомьтесь со статьей [интрасети SharePoint Server 2016 в Azure dev/test Environment](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment) .</span><span class="sxs-lookup"><span data-stu-id="a5572-176">See [Intranet SharePoint Server 2016 in Azure dev/test environment](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment) to build a simulated dev/test environment</span></span>
    
2. <span data-ttu-id="a5572-177">Проектирование</span><span class="sxs-lookup"><span data-stu-id="a5572-177">Design</span></span>
    
    <span data-ttu-id="a5572-178">Ознакомьтесь с разработкой [фермы SharePoint Server 2016 в Azure](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure) для пошагового указания набора элементов Azure IaaS Network, COMPUTE и Storage для размещения фермы и их параметров.</span><span class="sxs-lookup"><span data-stu-id="a5572-178">See [Designing a SharePoint Server 2016 farm in Azure](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure) to step through a process to determine the set of Azure IaaS networking, compute, and storage elements to host your farm and their settings.</span></span>
    
3. <span data-ttu-id="a5572-179">Развертывание</span><span class="sxs-lookup"><span data-stu-id="a5572-179">Deploy</span></span>
    
    <span data-ttu-id="a5572-180">В этой статье описывается [развертывание SharePoint server 2016 с использованием групп доступности ALWAYSON SQL Server в Azure](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in) для пошаговой настройки сквозной конфигурации фермы с высоким уровнем доступности в пять этапов.</span><span class="sxs-lookup"><span data-stu-id="a5572-180">See [Deploying SharePoint Server 2016 with SQL Server AlwaysOn Availability Groups in Azure](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in) to step through the end-to-end configuration of the high-availability farm in five phases.</span></span>
    
## <a name="federated-identity-for-office-365-in-azure"></a><span data-ttu-id="a5572-181">Федеративная идентификация для Office 365 в Azure</span><span class="sxs-lookup"><span data-stu-id="a5572-181">Federated identity for Office 365 in Azure</span></span>

<span data-ttu-id="a5572-182">Еще один пример многоуровневого высокодоступного бизнес-приложения в Azure — Федеративная идентификация для Office 365.</span><span class="sxs-lookup"><span data-stu-id="a5572-182">Another example of a multi-tier, highly-available LOB application in Azure is federated identity for Office 365.</span></span>
  
<span data-ttu-id="a5572-183">**Рис. 5: инфраструктура федеративного удостоверения высокой доступности для Office 365 в Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="a5572-183">**Figure 5: A high-availability federated identity infrastructure for Office 365 in Azure IaaS**</span></span>

![Инфраструктура федеративной проверки подлинности Office 365 С высоким уровнем доступности в Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-ADFS.png)
  
<span data-ttu-id="a5572-185">На рисунке 5 в локальной сети размещается инфраструктура удостоверений и пользователи.</span><span class="sxs-lookup"><span data-stu-id="a5572-185">In Figure 5, an on-premises network hosts an identity infrastructure and users.</span></span> <span data-ttu-id="a5572-186">Она подключена к шлюзу Azure IaaS с помощью соединения VPN типа "сеть-сеть" или ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="a5572-186">It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection.</span></span> <span data-ttu-id="a5572-187">Виртуальная сеть Azure содержит серверы веб-прокси, серверы служб федерации Active Directory (AD FS) и контроллеры домена доменных служб Active Directory (AD DS).</span><span class="sxs-lookup"><span data-stu-id="a5572-187">The Azure VNet contains web proxy servers, Active Directory Federation Services (AD FS) servers, and Active Directory Domain Services (AD DS) domain controllers.</span></span>
  
<span data-ttu-id="a5572-188">У этой конфигурации есть указанные ниже атрибуты бизнес-приложений в Azure.</span><span class="sxs-lookup"><span data-stu-id="a5572-188">This configuration has the following attributes of LOB applications in Azure:</span></span>
  
- <span data-ttu-id="a5572-189">**Уровни:** Существуют уровни для серверов веб-прокси, серверов AD FS и контроллеров домена AD DS.</span><span class="sxs-lookup"><span data-stu-id="a5572-189">**Tiers:** There are tiers for web proxy servers, AD FS servers, and AD DS domain controllers.</span></span>
    
- <span data-ttu-id="a5572-190">**Распределение нагрузки:** Внешняя подсистема балансировки нагрузки Azure распространяет входящие запросы проверки подлинности клиента на веб-прокси, а внутренний балансировщик нагрузки Azure распространяет запросы на проверку подлинности на серверы AD FS.</span><span class="sxs-lookup"><span data-stu-id="a5572-190">**Load distribution:** An external Azure load balancer distributes the incoming client authentication requests to the web proxies and an internal Azure load balancer distributes authentication requests to the AD FS servers.</span></span>
    
<span data-ttu-id="a5572-191">Используйте такой путь для успешного внедрения:</span><span class="sxs-lookup"><span data-stu-id="a5572-191">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="a5572-192">Оценка и эксперимент</span><span class="sxs-lookup"><span data-stu-id="a5572-192">Evaluate and experiment</span></span>
    
    <span data-ttu-id="a5572-193">Чтобы создать имитируемую среду разработки и тестирования для федеративной проверки подлинности с помощью Office 365, ознакомьтесь со статьей [федеративного удостоверения для вашей среды разработки и тестирования Office 365](federated-identity-for-your-office-365-dev-test-environment.md) .</span><span class="sxs-lookup"><span data-stu-id="a5572-193">See [Federated identity for your Office 365 dev/test environment](federated-identity-for-your-office-365-dev-test-environment.md) to build a simulated dev/test environment for federated authentication with Office 365.</span></span>
    
2. <span data-ttu-id="a5572-194">Развертывание</span><span class="sxs-lookup"><span data-stu-id="a5572-194">Deploy</span></span>
    
    <span data-ttu-id="a5572-195">В статье [развертывание федеративной проверки подлинности с высоким уровнем доступности для Office 365 в Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) для пошаговой настройки инфраструктуры AD FS с высоким уровнем доступности в пять этапов.</span><span class="sxs-lookup"><span data-stu-id="a5572-195">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) to step through the end-to-end configuration of the high availability AD FS infrastructure in five phases.</span></span>
    
    
## <a name="see-also"></a><span data-ttu-id="a5572-196">См. также</span><span class="sxs-lookup"><span data-stu-id="a5572-196">See Also</span></span>

[<span data-ttu-id="a5572-197">Гибридное облако Майкрософт для корпоративных архитекторов</span><span class="sxs-lookup"><span data-stu-id="a5572-197">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="a5572-198">Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="a5572-198">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)


