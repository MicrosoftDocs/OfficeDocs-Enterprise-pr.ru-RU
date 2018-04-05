---
title: Сценарии гибридного облака для Azure IaaS
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
ms.assetid: 978f2b76-5aba-4e11-9434-f0efda987be1
description: 'Сводка: Сведения о гибридных архитектуры и сценарии для корпорации Майкрософт инфраструктура как служба (IaaS)-на основе облака в Azure.'
ms.openlocfilehash: e64d20987946e05afa7afc4d64e071112ef58d10
ms.sourcegitcommit: 21cc62118b78b76d16ef12e2c3eff2c0c789e3d0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/05/2018
---
# <a name="hybrid-cloud-scenarios-for-azure-iaas"></a><span data-ttu-id="8d929-103">Гибридные облачные сценарии для Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="8d929-103">Hybrid cloud scenarios for Azure IaaS</span></span>

 <span data-ttu-id="8d929-104">**Сводка:** Представление об архитектуре гибридного и сценарии для инфраструктуры корпорации Майкрософт как служба (IaaS)-на основе облака в Azure.</span><span class="sxs-lookup"><span data-stu-id="8d929-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Infrastructure as a Service (IaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="8d929-105">Расширьте свою локальную инфраструктуру вычислений и удостоверений с помощью облака, разместив рабочие ИТ-нагрузки, выполняемые в распределенных виртуальных сетях Azure. </span><span class="sxs-lookup"><span data-stu-id="8d929-105">Extend your on-premises computing and identity infrastructure into the cloud by hosting IT workloads running in cross-premises Azure virtual networks (VNets).</span></span> 
  
## <a name="azure-iaas-hybrid-scenario-architecture"></a><span data-ttu-id="8d929-106">Архитектура гибридного сценария Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="8d929-106">Azure IaaS hybrid scenario architecture</span></span>

<span data-ttu-id="8d929-107">На рисунке 1 показана архитектура гибридных сценариев на основе Microsoft IaaS в Azure.</span><span class="sxs-lookup"><span data-stu-id="8d929-107">Figure 1 shows the architecture of Microsoft IaaS-based hybrid scenarios in Azure.</span></span>
  
<span data-ttu-id="8d929-108">**На рисунке 1: Майкрософт на основе IaaS гибридных сценариев в Azure**</span><span class="sxs-lookup"><span data-stu-id="8d929-108">**Figure 1: Microsoft IaaS-based hybrid scenarios in Azure**</span></span>

![Гибридные сценарии на основе Microsoft IaaS в Azure](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS.png)
  
<span data-ttu-id="8d929-110">Для каждого слоя архитектуры:</span><span class="sxs-lookup"><span data-stu-id="8d929-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="8d929-111">Приложения и сценарии</span><span class="sxs-lookup"><span data-stu-id="8d929-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="8d929-112">Рабочая ИТ-нагрузка обычно представляет собой многоуровневое приложение высокой доступности, которое состоит из виртуальных машин Azure.</span><span class="sxs-lookup"><span data-stu-id="8d929-112">An IT workload is typically a multi-tier, highly-available application composed of Azure virtual machines (VMs).</span></span>
    
- <span data-ttu-id="8d929-113">Удостоверение</span><span class="sxs-lookup"><span data-stu-id="8d929-113">Identity</span></span>
    
    <span data-ttu-id="8d929-114">Для локальной проверки подлинности добавьте серверы удостоверений, например контроллеры доменов Windows Server AD, в набор серверов, работающих в виртуальных сетях Azure.</span><span class="sxs-lookup"><span data-stu-id="8d929-114">Add identity servers, such as Windows Server AD domain controllers, to the set of servers running in Azure VNets for local authentication.</span></span>
    
- <span data-ttu-id="8d929-115">Сеть</span><span class="sxs-lookup"><span data-stu-id="8d929-115">Network</span></span>
    
    <span data-ttu-id="8d929-116">Используйте подключение к VPN типа "сеть-сеть" в Интернете или подключение ExpressRoute с частным пирингом к Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="8d929-116">Use either a site-to-site VPN connection over the Internet or an ExpressRoute connection with private peering to Azure IaaS.</span></span>
    
- <span data-ttu-id="8d929-117">Локальная среда</span><span class="sxs-lookup"><span data-stu-id="8d929-117">On-premises</span></span>
    
    <span data-ttu-id="8d929-p101">Содержит серверы удостоверений, которые синхронизируются с серверами удостоверений в Azure. Также может содержать ресурсы, к которым имеют доступ виртуальные машины, работающие в Azure, например хранилище или инфраструктуру управления системами.</span><span class="sxs-lookup"><span data-stu-id="8d929-p101">Contains identity servers that are synchronized with the identity servers running in Azure. Can also contain resources that VMs running in Azure can access, such as storage and systems management infrastructure.</span></span>
    
## <a name="dirsync-server-for-office-365"></a><span data-ttu-id="8d929-120">Сервер DirSync для Office 365</span><span class="sxs-lookup"><span data-stu-id="8d929-120">DirSync server for Office 365</span></span>

<span data-ttu-id="8d929-121">Использование сервера синхронизации каталогов (DirSync) в виртуальной сети Azure, как показано на рисунке 2, — пример развертывания инфраструктуры вычислений и идентификации в облаке.</span><span class="sxs-lookup"><span data-stu-id="8d929-121">Running your directory synchronization (DirSync) server from an Azure VNet, as shown in Figure 2, is an example of extending your computing and identity infrastructure to the cloud.</span></span>
  
<span data-ttu-id="8d929-122">**На рисунке 2: Сервер синхронизации каталогов для Office 365 в Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="8d929-122">**Figure 2: DirSync server for Office 365 in Azure IaaS**</span></span>

![Сервер DirSync для Office 365 в Azure IaaS](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS_DirSync.png)
  
<span data-ttu-id="8d929-p102">На рисунке 2 локальной сети, где размещается в инфраструктуре Windows Server AD с прокси-сервера и маршрутизатора в его пограничного сервера. Маршрутизатор подключается к Azure шлюза на границе VNet Azure с подключением через VPN или ExpressRoute веб сайта. Внутри VNet сервер синхронизации каталогов выполняется подключение Azure AD.</span><span class="sxs-lookup"><span data-stu-id="8d929-p102">In Figure 2, an on-premises network hosts a Windows Server AD infrastructure, with a proxy server and a router at its edge. The router connects to an Azure gateway at the edge of an Azure VNet with a site-to-site VPN or ExpressRoute connection. Inside the VNet, a DirSync server runs Azure AD Connect.</span></span>
  
<span data-ttu-id="8d929-127">Сервер DirSync для Office 365 синхронизирует список учетных записей в Windows Server AD с клиентом Azure AD, предусмотренном в плане подписки на Office 365.</span><span class="sxs-lookup"><span data-stu-id="8d929-127">A DirSync server for Office 365 synchronizes the list of accounts in Windows Server AD with the Azure AD tenant of an Office 365 subscription.</span></span>
  
<span data-ttu-id="8d929-p103">Сервер DirSync — это сервер под управлением Windows, на котором работает Azure AD Connect. Чтобы ускорить подготовку или уменьшить количество локальных серверов в организации, разверните сервер DirSync в виртуальной сети в Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="8d929-p103">A DirSync server is a Windows-based server that runs Azure AD Connect. For faster provisioning or to reduce the number of on-premises servers in your organization, deploy your DirSync server in a virtual network (VNet) in Azure IaaS.</span></span>
  
<span data-ttu-id="8d929-130">Сервер DirSync опрашивает Windows Server AD для определения наличия изменений, а затем синхронизирует их с Office 365.</span><span class="sxs-lookup"><span data-stu-id="8d929-130">The DirSync server polls Windows Server AD for changes and then synchronizes them with the Office 365 subscription.</span></span>
  
<span data-ttu-id="8d929-131">Дополнительные сведения можно [Развернуть Office 365 DirSync в Azure](https://technet.microsoft.com/library/dn635310.aspx).</span><span class="sxs-lookup"><span data-stu-id="8d929-131">For more information, see [Deploy Office 365 DirSync in Azure](https://technet.microsoft.com/library/dn635310.aspx).</span></span>
  
## <a name="line-of-business-lob-application"></a><span data-ttu-id="8d929-132">Бизнес-приложение</span><span class="sxs-lookup"><span data-stu-id="8d929-132">Line of business (LOB) application</span></span>

<span data-ttu-id="8d929-133">На рисунке 3 показана конфигурация серверного бизнес-приложения, работающего в Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="8d929-133">Figure 3 shows the configuration of a server-based LOB application running in Azure IaaS.</span></span>
  
<span data-ttu-id="8d929-134">**На рисунке 3: Бизнес-приложение в Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="8d929-134">**Figure 3: LOB application in Azure IaaS**</span></span>

![Серверное бизнес-приложение в Azure IaaS](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS_Ex.png)
  
<span data-ttu-id="8d929-p104">На рисунке 3 показана локальная сеть, в которой размещены инфраструктура идентификации и пользователи. Она подключена к шлюзу Azure IaaS с помощью соединения VPN типа "сеть-сеть" или ExpressRoute. В Azure IaaS размещена виртуальная сеть, содержащая серверы бизнес-приложения.</span><span class="sxs-lookup"><span data-stu-id="8d929-p104">In Figure 3, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. Azure IaaS hosts a virtual network containing the servers of the LOB application.</span></span>
  
<span data-ttu-id="8d929-139">Можно создать бизнес-приложения, работающего на виртуальных машин Azure, в которой хранятся на устройстве подсети VNet Azure в Azure обработки данных (также известной как расположение).</span><span class="sxs-lookup"><span data-stu-id="8d929-139">You can create LOB applications running on Azure VMs, which reside on subnets of an Azure VNet in an Azure datacenter (also known as a location).</span></span>
  
<span data-ttu-id="8d929-140">Так как вы, по сути, расширяете локальную инфраструктуру до Azure, необходимо назначить уникальное пространство частных адресов своим виртуальным сетям и обновить таблицы локальной маршрутизации, чтобы обеспечить доступность каждой виртуальной сети.</span><span class="sxs-lookup"><span data-stu-id="8d929-140">Because you are essentially extending your on-premises infrastructure to Azure, you must assign unique private address space to your VNets and update your on-premises routing tables to ensure reachability to each VNet.</span></span>
  
<span data-ttu-id="8d929-141">После подключения этими виртуальными машинами можно управлять с помощью подключений к удаленному рабочему столу или программного обеспечения для управления системами (так же, как и локальными серверами).</span><span class="sxs-lookup"><span data-stu-id="8d929-141">Once connected, these VMs can be managed with remote desktop connections or with your systems management software, just like your on-premises servers.</span></span>
  
<span data-ttu-id="8d929-142">После настройки общедоступных портов мобильные или удаленные пользователи также могут получить доступ к этим виртуальным машинам через Интернет.</span><span class="sxs-lookup"><span data-stu-id="8d929-142">By configuring publically-exposed ports, these VMs can also be accessed from the Internet by mobile or remote users.</span></span>
  
<span data-ttu-id="8d929-143">Конфигурация обоснования концепции в разделе [модель распределенной виртуальной сети в Azure](simulated-cross-premises-virtual-network-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="8d929-143">For a proof-of-concept configuration, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span>
  
<span data-ttu-id="8d929-144">Атрибуты бизнес-приложений, размещенных на виртуальных машинах Azure:</span><span class="sxs-lookup"><span data-stu-id="8d929-144">Attributes of LOB applications hosted on Azure VMs are the following:</span></span>
  
- <span data-ttu-id="8d929-145">Несколько уровней</span><span class="sxs-lookup"><span data-stu-id="8d929-145">Multiple tiers</span></span>
    
    <span data-ttu-id="8d929-p105">В типичных бизнес-приложениях используется многоуровневый подход. Наборы серверов обеспечивают обработку удостоверений, баз данных, приложений и логики, а также предоставляют интерфейсные веб-серверы для доступа со стороны сотрудников или клиентов. </span><span class="sxs-lookup"><span data-stu-id="8d929-p105">Typical LOB applications use a tiered approach. Sets of servers provide identity, database processing, application and logic processing, and front-end web servers for employee or customer access.</span></span> 
    
- <span data-ttu-id="8d929-148">Высокая доступность</span><span class="sxs-lookup"><span data-stu-id="8d929-148">High availability</span></span>
    
    <span data-ttu-id="8d929-p106">Типичные бизнес-приложения обеспечивают высокую доступность с помощью нескольких серверов на каждом уровне. Azure IaaS обеспечивает 99,9 % времени непрерывной работы (согласно SLA) для серверов в группах доступности Azure. </span><span class="sxs-lookup"><span data-stu-id="8d929-p106">Typical LOB applications provide high availability by using multiple servers in each tier. Azure IaaS provides a 99.9% uptime SLA for servers in Azure availability sets.</span></span> 
    
- <span data-ttu-id="8d929-151">Распределение нагрузки</span><span class="sxs-lookup"><span data-stu-id="8d929-151">Load distribution</span></span>
    
    <span data-ttu-id="8d929-p107">Чтобы распределить нагрузку сетевого трафика между несколькими серверами на одном уровне, можно использовать балансировщик нагрузки для Интернета или внутренний балансировщик нагрузки Azure. Можно также использовать специальный виртуальный модуль балансировки нагрузки, доступный в службе Azure Marketplace.</span><span class="sxs-lookup"><span data-stu-id="8d929-p107">To distribute the load of network traffic among multiple servers in a tier, you can use an Internet-facing or internal Azure load balancer. Or, you can use a dedicated load balancer appliance available from the Azure marketplace.</span></span>
    
- <span data-ttu-id="8d929-154">Безопасность</span><span class="sxs-lookup"><span data-stu-id="8d929-154">Security</span></span>
    
    <span data-ttu-id="8d929-p108">Чтобы защитить серверы от нежелательного входящего трафика из Интернета, можно использовать группы безопасности сети Azure. Вы можете определить допустимый или запрещенный трафик для подсети или сетевого интерфейса отдельных виртуальных машин.</span><span class="sxs-lookup"><span data-stu-id="8d929-p108">To protect servers from unsolicited incoming traffic from the Internet, you can use Azure network security groups. You can define allowed or denied traffic for a subnet or the network interface of an individual virtual machine.</span></span>
    
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="8d929-157">Ферма SharePoint Server 2016 в Azure</span><span class="sxs-lookup"><span data-stu-id="8d929-157">SharePoint Server 2016 farm in Azure</span></span>

<span data-ttu-id="8d929-158">Ферма SharePoint Server 2016, показанная на рисунке 4, является примером многоуровневого высокодоступного бизнес-приложения в Azure.</span><span class="sxs-lookup"><span data-stu-id="8d929-158">An example of a multi-tier, highly-available LOB application in Azure is a SharePoint Server 2016 farm, as shown in Figure 4.</span></span>
  
<span data-ttu-id="8d929-159">**На рисунке 4: Высокого уровня доступности SharePoint Server 2016 фермы в Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="8d929-159">**Figure 4: A high-availability SharePoint Server 2016 farm in Azure IaaS**</span></span>

![Высокодоступная ферма SharePoint Server 2016 в Azure IaaS](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS_SP2016.png)
  
<span data-ttu-id="8d929-p109">На рисунке 4 показана локальная сеть, в которой размещены инфраструктура идентификации и пользователи. Она подключена к шлюзу Azure IaaS с помощью соединения VPN типа "сеть-сеть" или ExpressRoute. Виртуальная сеть Azure содержит серверы фермы SharePoint Server 2016, которая включает отдельные уровни для серверов переднего плана, серверов приложений, кластера SQL Server и контроллеров домена.</span><span class="sxs-lookup"><span data-stu-id="8d929-p109">In Figure 4, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. The Azure VNet contains the servers of the SharePoint Server 2016 farm, which includes separate tiers for the front-end servers, the application servers, the SQL Server cluster, and the domain controllers.</span></span>
  
<span data-ttu-id="8d929-164">У этой конфигурации есть указанные ниже атрибуты бизнес-приложений в Azure. </span><span class="sxs-lookup"><span data-stu-id="8d929-164">This configuration has the following attributes of LOB applications in Azure:</span></span> 
  
- <span data-ttu-id="8d929-165">Уровни</span><span class="sxs-lookup"><span data-stu-id="8d929-165">Tiers</span></span>
    
    <span data-ttu-id="8d929-166">Под управлением различных ролей в ферме серверов создайте по уровням и каждого уровня имеет свой собственный подсети.</span><span class="sxs-lookup"><span data-stu-id="8d929-166">Servers running different roles within the farm create the tiers and each tier has its own subnet.</span></span>
    
- <span data-ttu-id="8d929-167">Высокая доступность</span><span class="sxs-lookup"><span data-stu-id="8d929-167">High-availability</span></span>
    
    <span data-ttu-id="8d929-168">Достигается за счет использования нескольких серверов на каждом уровне и размещения всех серверов уровня в одной группе доступности.</span><span class="sxs-lookup"><span data-stu-id="8d929-168">Achieved by using more than one server in each tier and placing all the servers of a tier in the same availability set.</span></span>
    
- <span data-ttu-id="8d929-169">Распределение нагрузки</span><span class="sxs-lookup"><span data-stu-id="8d929-169">Load distribution</span></span>
    
    <span data-ttu-id="8d929-170">Внутренние балансировщики нагрузки Azure отправляют входящий клиентский веб-трафик на серверы переднего плана (WEB1 и WEB2) и на IP-адрес прослушивателя кластера SQL Server (SQL1, SQL2 и MN1).</span><span class="sxs-lookup"><span data-stu-id="8d929-170">Internal Azure load balancers distribute the incoming client web traffic to the front-end servers (WEB1 and WEB2) and to the listener IP address of the SQL Server cluster (SQL1, SQL2, and MN1).</span></span>
    
- <span data-ttu-id="8d929-171">Безопасность</span><span class="sxs-lookup"><span data-stu-id="8d929-171">Security</span></span>
    
    <span data-ttu-id="8d929-172">Группы безопасности сети для каждой подсети позволяют настроить разрешенный входящий и исходящий трафик.</span><span class="sxs-lookup"><span data-stu-id="8d929-172">Network security groups for each subnet let you to configure allowed inbound and outbound traffic.</span></span>
    
<span data-ttu-id="8d929-173">Используйте такой путь для успешного внедрения:</span><span class="sxs-lookup"><span data-stu-id="8d929-173">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="8d929-174">Оценка и эксперимент</span><span class="sxs-lookup"><span data-stu-id="8d929-174">Evaluate and experiment</span></span>
    
    <span data-ttu-id="8d929-175">В разделе [2016 сервера SharePoint в Microsoft Azure](https://technet.microsoft.com/library/mt779107%28v=office.16%29.aspx) понять преимущества под управлением SharePoint Server 2016 в Azure.</span><span class="sxs-lookup"><span data-stu-id="8d929-175">See [SharePoint Server 2016 in Microsoft Azure](https://technet.microsoft.com/library/mt779107%28v=office.16%29.aspx) to understand the benefits of running SharePoint Server 2016 in Azure.</span></span>
    
    <span data-ttu-id="8d929-176">Просмотреть [интрасети 2016 сервера SharePoint в среде Azure разработку и тестирование](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx) для построения имитации dev/тестовой среды</span><span class="sxs-lookup"><span data-stu-id="8d929-176">See [Intranet SharePoint Server 2016 in Azure dev/test environment](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx) to build a simulated dev/test environment</span></span>
    
2. <span data-ttu-id="8d929-177">Проектирование</span><span class="sxs-lookup"><span data-stu-id="8d929-177">Design</span></span>
    
    <span data-ttu-id="8d929-178">В разделе [Разработка фермы SharePoint Server 2016 в Azure](https://technet.microsoft.com/library/mt779108%28v=office.16%29.aspx) пошаговое выполнение процесса для определения набора сети Azure IaaS, compute и хранения элементов для размещения фермы и их параметров.</span><span class="sxs-lookup"><span data-stu-id="8d929-178">See [Designing a SharePoint Server 2016 farm in Azure](https://technet.microsoft.com/library/mt779108%28v=office.16%29.aspx) to step through a process to determine the set of Azure IaaS networking, compute, and storage elements to host your farm and their settings.</span></span>
    
3. <span data-ttu-id="8d929-179">Развернуть</span><span class="sxs-lookup"><span data-stu-id="8d929-179">Deploy</span></span>
    
    <span data-ttu-id="8d929-180">В разделе [Развертывание 2016 SharePoint Server с помощью группы обеспечения доступности AlwaysOn SQL Server в среде Azure](https://technet.microsoft.com/library/mt793552%28v=office.16%29.aspx) для пошагового выполнения начала до конца конфигурации фермы высокой доступности в пять этапов.</span><span class="sxs-lookup"><span data-stu-id="8d929-180">See [Deploying SharePoint Server 2016 with SQL Server AlwaysOn Availability Groups in Azure](https://technet.microsoft.com/library/mt793552%28v=office.16%29.aspx) to step through the end-to-end configuration of the high-availability farm in five phases.</span></span>
    
## <a name="federated-identity-for-office-365-in-azure"></a><span data-ttu-id="8d929-181">Федеративное удостоверение для Office 365 в Azure</span><span class="sxs-lookup"><span data-stu-id="8d929-181">Federated identity for Office 365 in Azure</span></span>

<span data-ttu-id="8d929-182">Другой пример многоуровневых, высокой доступностью бизнес-приложение в Azure — федеративных удостоверений для Office 365.</span><span class="sxs-lookup"><span data-stu-id="8d929-182">Another example of a multi-tier, highly-available LOB application in Azure is federated identity for Office 365.</span></span>
  
<span data-ttu-id="8d929-183">**На рисунке 5: В инфраструктуре федеративных удостоверений высокого уровня доступности для Office 365 в Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="8d929-183">**Figure 5: A high-availability federated identity infrastructure for Office 365 in Azure IaaS**</span></span>

![Окончательная конфигурация инфраструктуры для федеративной проверки подлинности Office 365 с высоким уровнем доступности в Azure](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS_ADFS.png)
  
<span data-ttu-id="8d929-p110">На рисунке 5 локальной сети размещается инфраструктуру удостоверения и пользователей. Подключения шлюза Azure IaaS с веб сайта VPN или ExpressRoute подключения. Azure VNet содержит прокси-сервера веб-серверов, серверов служб федерации Active Directory (AD FS) и контроллеры домена Active Directory Windows Server (AD).</span><span class="sxs-lookup"><span data-stu-id="8d929-p110">In Figure 5, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. The Azure VNet contains web proxy servers, Active Directory Federation Services (AD FS) servers, and Windows Server Active Directory (AD) domain controllers.</span></span>
  
<span data-ttu-id="8d929-188">У этой конфигурации есть указанные ниже атрибуты бизнес-приложений в Azure. </span><span class="sxs-lookup"><span data-stu-id="8d929-188">This configuration has the following attributes of LOB applications in Azure:</span></span>
  
- <span data-ttu-id="8d929-189">**Уровней:** Существует уровней для прокси-сервера веб-серверов, серверов AD FS и контроллеров домена Windows Server AD.</span><span class="sxs-lookup"><span data-stu-id="8d929-189">**Tiers:** There are tiers for web proxy servers, AD FS servers, and Windows Server AD domain controllers.</span></span>
    
- <span data-ttu-id="8d929-190">**Распределения нагрузки:** Внешние Azure нагрузки распределяет входящие запросы проверки подлинности клиента для прокси-серверов веб и внутреннего Azure балансировщика распространять запросы проверки подлинности на серверах AD FS.</span><span class="sxs-lookup"><span data-stu-id="8d929-190">**Load distribution:** An external Azure load balancer distributes the incoming client authentication requests to the web proxies and an internal Azure load balancer distributes authentication requests to the AD FS servers.</span></span>
    
<span data-ttu-id="8d929-191">Используйте такой путь для успешного внедрения:</span><span class="sxs-lookup"><span data-stu-id="8d929-191">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="8d929-192">Оценка и эксперимент</span><span class="sxs-lookup"><span data-stu-id="8d929-192">Evaluate and experiment</span></span>
    
    <span data-ttu-id="8d929-193">В разделе [федеративных удостоверений для Office 365 dev/тестовой среды](federated-identity-for-your-office-365-dev-test-environment.md) для построения имитации dev/тестовой среды для федеративной проверки подлинности с помощью Office 365.</span><span class="sxs-lookup"><span data-stu-id="8d929-193">See [Federated identity for your Office 365 dev/test environment](federated-identity-for-your-office-365-dev-test-environment.md) to build a simulated dev/test environment for federated authentication with Office 365.</span></span>
    
2. <span data-ttu-id="8d929-194">Развернуть</span><span class="sxs-lookup"><span data-stu-id="8d929-194">Deploy</span></span>
    
    <span data-ttu-id="8d929-195">В разделе [Развертывание высокой доступности федеративной проверки подлинности для Office 365 в Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) для пошаговой настройки начала до конца высокой доступности инфраструктуру AD FS в пять этапов.</span><span class="sxs-lookup"><span data-stu-id="8d929-195">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) to step through the end-to-end configuration of the high availability AD FS infrastructure in five phases.</span></span>
    
<span data-ttu-id="8d929-196">Дополнительные материалы:</span><span class="sxs-lookup"><span data-stu-id="8d929-196">See these additional resources:</span></span>
  
- [<span data-ttu-id="8d929-197">Разработка архитектуры гибридных облачных средах</span><span class="sxs-lookup"><span data-stu-id="8d929-197">Architecting Hybrid Cloud Environments</span></span>](https://gallery.technet.microsoft.com/Architecting-Hybrid-Cloud-a7dc9f24/file/147475/1/Architecting%20Hybrid%20Cloud%20Environments%20V1.docx)
    
- [<span data-ttu-id="8d929-198">Разработка и Создание бизнес-приложение в Azure</span><span class="sxs-lookup"><span data-stu-id="8d929-198">Design and Build an LOB application in Azure </span></span>](https://techcommunity.microsoft.com/t5/CAAB-Cloud-Adoption-Advisory/EXTRA-November-2016-Webinar/m-p/30058#M41)
    
## <a name="see-also"></a><span data-ttu-id="8d929-199">См. также</span><span class="sxs-lookup"><span data-stu-id="8d929-199">See Also</span></span>

[<span data-ttu-id="8d929-200">Гибридное облако Майкрософт для корпоративных архитекторов</span><span class="sxs-lookup"><span data-stu-id="8d929-200">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="8d929-201">Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="8d929-201">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="8d929-202">Стратегия Enterprise Cloud корпорации Майкрософт: ресурсы для лиц, принимающих решения в области ИТ</span><span class="sxs-lookup"><span data-stu-id="8d929-202">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



