---
title: Архитектуры Microsoft Azure для SharePoint 2013
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Architecture
- seo-marvel-apr2020
ms.assetid: 98fc1006-9399-4ff0-a216-c7c05820d822
description: Узнайте, какие типы решений SharePoint 2013 могут размещаться на виртуальных машинах Microsoft Azure, и как настроить Azure для размещения одного из них.
ms.openlocfilehash: f76d5020ab4695f48edca956d6593040c42dcc70
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605691"
---
# <a name="microsoft-azure-architectures-for-sharepoint-2013"></a><span data-ttu-id="51f51-103">Архитектуры Microsoft Azure для SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="51f51-103">Microsoft Azure Architectures for SharePoint 2013</span></span>

<span data-ttu-id="51f51-104">Среда Azure отлично подходит для размещения решений SharePoint Server 2013.</span><span class="sxs-lookup"><span data-stu-id="51f51-104">Azure is a good environment for hosting a SharePoint Server 2013 solution.</span></span> <span data-ttu-id="51f51-105">В большинстве случаев рекомендуется использовать Microsoft 365, но ферма SharePoint Server, размещенная в Azure, может быть хорошим вариантом для определенных решений.</span><span class="sxs-lookup"><span data-stu-id="51f51-105">In most cases, we recommend Microsoft 365, but a SharePoint Server farm hosted in Azure can be a good option for specific solutions.</span></span> <span data-ttu-id="51f51-106">В этой статье описано, как спроектировать решения SharePoint для обеспечения совместимости с платформой Azure.</span><span class="sxs-lookup"><span data-stu-id="51f51-106">This article describes how to architect SharePoint solutions so they are a good fit in the Azure platform.</span></span> <span data-ttu-id="51f51-107">В качестве примеров используются два следующих решения:</span><span class="sxs-lookup"><span data-stu-id="51f51-107">The following two specific solutions are used as examples:</span></span>
  
- [<span data-ttu-id="51f51-108">Аварийное восстановление SharePoint Server 2013 в Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="51f51-108">SharePoint Server 2013 Disaster Recovery in Microsoft Azure</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)
    
- [<span data-ttu-id="51f51-109">Веб-сайты в Microsoft Azure с использованием SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="51f51-109">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
    
## <a name="recommended-sharepoint-solutions-for-azure-infrastructure-services"></a><span data-ttu-id="51f51-110">Рекомендуемые решения SharePoint для служб инфраструктуры Azure</span><span class="sxs-lookup"><span data-stu-id="51f51-110">Recommended SharePoint solutions for Azure Infrastructure Services</span></span>

<span data-ttu-id="51f51-p102">Службы инфраструктуры Azure отлично подходят для размещения решений SharePoint. Не все решения одинаково совместимы с этой платформой. В приведенной ниже таблице представлены рекомендуемые решения.</span><span class="sxs-lookup"><span data-stu-id="51f51-p102">Azure infrastructure services is a compelling option for hosting SharePoint solutions. Some solutions are a better fit for this platform than others. The following table shows recommended solutions.</span></span>
  
|<span data-ttu-id="51f51-114">**Решение**</span><span class="sxs-lookup"><span data-stu-id="51f51-114">**Solution**</span></span>|<span data-ttu-id="51f51-115">**Преимущества работы с Azure**</span><span class="sxs-lookup"><span data-stu-id="51f51-115">**Why this solution is recommended for Azure**</span></span>|
|:-----|:-----|
|<span data-ttu-id="51f51-116">Среды разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="51f51-116">Development and test environments</span></span>  <br/> |<span data-ttu-id="51f51-117">Создавать такие среды и управлять ими легко.</span><span class="sxs-lookup"><span data-stu-id="51f51-117">It's easy to create and manage these environments.</span></span>  <br/> |
|<span data-ttu-id="51f51-118">Аварийное восстановление локальных ферм SharePoint в Azure</span><span class="sxs-lookup"><span data-stu-id="51f51-118">Disaster recovery of on-premises SharePoint farms to Azure</span></span>  <br/> |<span data-ttu-id="51f51-119">**Размещенный вспомогательный центр обработки данных** Используйте Azure, чтобы не вкладывать средства во вспомогательный центр обработки данных в другом регионе.</span><span class="sxs-lookup"><span data-stu-id="51f51-119">**Hosted secondary datacenter** Use Azure instead of investing in a secondary datacenter in a different region.</span></span> <br/> <span data-ttu-id="51f51-p103">**Снижение затрат на среды аварийного восстановления** По сравнению с локальной средой аварийного восстановления потребуется обслуживать и оплачивать меньше ресурсов. Их количество зависит от выбранной среды аварийного восстановления: с холодным или горячим резервированием либо горячей заменой.</span><span class="sxs-lookup"><span data-stu-id="51f51-p103">**Lower-cost disaster-recovery environments** Maintain and pay for fewer resources than an on-premises disaster recovery environment. The number of resources depends on the disaster recovery environment you choose: cold standby, warm standby, or hot standby. </span></span><br/> <span data-ttu-id="51f51-p104">**Более эластичная платформа** В случае аварии вы можете с легкостью развернуть ферму восстановления SharePoint в соответствии с требованиями к нагрузке. Когда необходимость в дополнительных ресурсах пропадет, вы можете свернуть ферму.</span><span class="sxs-lookup"><span data-stu-id="51f51-p104">**More elastic platform** In the event of a disaster, easily scale-out your recovery SharePoint farm to meet load requirements. Scale in when you no longer need the resources. </span></span><br/> <span data-ttu-id="51f51-124">См. статью [Аварийное восстановление SharePoint Server 2013 в Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md).</span><span class="sxs-lookup"><span data-stu-id="51f51-124">See [SharePoint Server 2013 Disaster Recovery in Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md).</span></span>  <br/> |
|<span data-ttu-id="51f51-125">Веб-сайты, использующие функции и масштабируемые, не поддерживаемые в Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="51f51-125">Internet-facing sites that use features and scale not available in Microsoft 365</span></span>  <br/> |<span data-ttu-id="51f51-126">**Правильные приоритеты** Сосредоточьтесь на создании отличного сайта, а не инфраструктуры.</span><span class="sxs-lookup"><span data-stu-id="51f51-126">**Focus your efforts** Concentrate on building a great site rather than building infrastructure.</span></span> <br/> <span data-ttu-id="51f51-p105">**Воспользуйтесь преимуществами эластичности Azure** Изменяйте размер фермы в соответствии с потребностями, добавляя новые серверы, и платите только за необходимые вам ресурсы. Динамическое распределение машин не поддерживается (автомасштабирование).</span><span class="sxs-lookup"><span data-stu-id="51f51-p105">**Take advantage of elasticity in Azure** Size the farm for the demand by adding new servers, and pay only for resources you need. Dynamic machine allocation is not supported (auto scale). </span></span><br/> <span data-ttu-id="51f51-129">**Использование службы Azure Active Directory (AD)** Воспользуйтесь преимуществами Azure AD для учетных записей клиентов.</span><span class="sxs-lookup"><span data-stu-id="51f51-129">**Use Azure Active Directory (AD)** Take advantage of Azure AD for customer accounts.</span></span> <br/> <span data-ttu-id="51f51-130">**Добавление функций SharePoint, недоступных в Microsoft 365** Добавьте глубокую отчетность и Web Analytics.</span><span class="sxs-lookup"><span data-stu-id="51f51-130">**Add SharePoint functionality not available in Microsoft 365** Add deep reporting and web analytics.</span></span> <br/> <span data-ttu-id="51f51-131">См. статью [Веб-сайты в Microsoft Azure с использованием SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md).</span><span class="sxs-lookup"><span data-stu-id="51f51-131">See [Internet Sites in Microsoft Azure using SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md).</span></span>  <br/> |
|<span data-ttu-id="51f51-132">Фермы приложений для поддержки Microsoft 365 или локальных сред</span><span class="sxs-lookup"><span data-stu-id="51f51-132">App farms to support Microsoft 365 or on-premises environments</span></span>  <br/> |<span data-ttu-id="51f51-133">**Создание, тестирование и размещение приложений** в Azure для поддержки как локальных, так и облачных сред.</span><span class="sxs-lookup"><span data-stu-id="51f51-133">**Build, test, and host apps** in Azure to support both on-premises and cloud environments.</span></span> <br/> <span data-ttu-id="51f51-134">**Разместите эту роль** в Azure, не покупая новое оборудование для локальных сред.</span><span class="sxs-lookup"><span data-stu-id="51f51-134">**Host this role** in Azure instead of buying new hardware for on-premises environments.</span></span> <br/> |
   
<span data-ttu-id="51f51-135">Для решений интрасети и совместной работы рассмотрите следующие факторы.</span><span class="sxs-lookup"><span data-stu-id="51f51-135">For intranet and collaboration solutions and workloads, consider the following options:</span></span>
  
- <span data-ttu-id="51f51-136">Определите, соответствует ли Microsoft 365 требованиям бизнес-требований или является частью решения.</span><span class="sxs-lookup"><span data-stu-id="51f51-136">Determine if Microsoft 365 meets your business requirements or can be part of the solution.</span></span> <span data-ttu-id="51f51-137">Microsoft 365 предоставляет богатый набор функций, которые всегда актуальны.</span><span class="sxs-lookup"><span data-stu-id="51f51-137">Microsoft 365 provides a rich feature set that is always up to date.</span></span>
    
- <span data-ttu-id="51f51-138">Если Microsoft 365 не отвечает всем бизнес-требованиям, рекомендуем использовать стандартную реализацию SharePoint 2013 в локальной среде консультационных служб Майкрософт (MCS).</span><span class="sxs-lookup"><span data-stu-id="51f51-138">If Microsoft 365 does not meet all your business requirements, consider a standard implementation of SharePoint 2013 on premises from Microsoft Consulting Services (MCS).</span></span> <span data-ttu-id="51f51-139">Поддерживать стандартную архитектуру может быть дешевле и проще, чем персонализированное решение.</span><span class="sxs-lookup"><span data-stu-id="51f51-139">A standard architecture can be a quicker, cheaper, and easier solution for you to support than a customized one.</span></span> 
    
- <span data-ttu-id="51f51-140">Если стандартная реализация не соответствует вашим бизнес-требованиям, рекомендуется персонализированное локальное решение.</span><span class="sxs-lookup"><span data-stu-id="51f51-140">If a standard implementation doesn't meet your business requirements, consider a customized on-premises solution.</span></span>
    
- <span data-ttu-id="51f51-p108">Если ваши бизнес-требования включают использование облачной платформы, рассмотрите возможность стандартной или персонализированной реализации SharePoint 2013 с размещением в службах инфраструктуры Azure. Поддерживать решения SharePoint в Azure намного проще, чем другие общедоступные облачные платформы (не корпорации Майкрософт).</span><span class="sxs-lookup"><span data-stu-id="51f51-p108">If using a cloud platform is important for your business requirements, consider a standard or customized implementation of SharePoint 2013 hosted in Azure infrastructure services. SharePoint solutions are much easier to support in Azure than other non-native Microsoft public cloud platforms.</span></span>
    
## <a name="before-you-design-the-azure-environment"></a><span data-ttu-id="51f51-143">Перед разработкой среды Azure</span><span class="sxs-lookup"><span data-stu-id="51f51-143">Before you design the Azure environment</span></span>

<span data-ttu-id="51f51-p109">Хотя в этой статье используются примеры топологий SharePoint, вы можете использовать эти проектные решения с любой топологией фермы SharePoint. Прежде чем разрабатывать среду Azure, используйте указанные ниже топологию, архитектуру, емкость и производительность для разработки фермы SharePoint.</span><span class="sxs-lookup"><span data-stu-id="51f51-p109">While this article uses example SharePoint topologies, you can use these design concepts with any SharePoint farm topology. Before you design the Azure environment, use the following topology, architecture, capacity, and performance guidance to design the SharePoint farm:</span></span>
  
- [<span data-ttu-id="51f51-146">Архитектура SharePoint 2013 для ИТ-специалистов</span><span class="sxs-lookup"><span data-stu-id="51f51-146">Architecture design for SharePoint 2013 IT pros</span></span>](https://technet.microsoft.com/sharepoint/fp123594.aspx)
    
- [<span data-ttu-id="51f51-147">Plan for performance and capacity management in SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="51f51-147">Plan for performance and capacity management in SharePoint Server 2013</span></span>](https://technet.microsoft.com/library/8dd52916-f77d-4444-b593-1f7d6f330e5f.aspx)
    
## <a name="determine-the-active-directory-domain-type"></a><span data-ttu-id="51f51-148">Определение типа домена Active Directory</span><span class="sxs-lookup"><span data-stu-id="51f51-148">Determine the Active Directory domain type</span></span>

<span data-ttu-id="51f51-p110">Каждая ферма SharePoint Server использует службу Active Directory для создания учетных записей администраторов. В настоящее время существует два варианта для решений SharePoint в Azure. Они описываются в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="51f51-p110">Each SharePoint Server farm relies on Active Directory to provide administrative accounts for farm setup. At this time, there are two options for SharePoint solutions in Azure. These are described in the following table.</span></span>
  
|<span data-ttu-id="51f51-152">**Вариант**</span><span class="sxs-lookup"><span data-stu-id="51f51-152">**Option**</span></span>|<span data-ttu-id="51f51-153">**Описание**</span><span class="sxs-lookup"><span data-stu-id="51f51-153">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="51f51-154">Выделенный домен</span><span class="sxs-lookup"><span data-stu-id="51f51-154">Dedicated domain</span></span>  <br/> |<span data-ttu-id="51f51-p111">Вы можете развернуть выделенный изолированный домен Active Directory в Azure для поддержки фермы SharePoint. Этот вариант хорошо подходит для общедоступных сайтов в Интернете.</span><span class="sxs-lookup"><span data-stu-id="51f51-p111">You can deploy a dedicated and isolated Active Directory domain to Azure to support your SharePoint farm. This is a good choice for public-facing Internet sites.</span></span>  <br/> |
|<span data-ttu-id="51f51-157">Расширение локального домена через подключение между организациями</span><span class="sxs-lookup"><span data-stu-id="51f51-157">Extend the on-premises domain through a cross-premises connection</span></span>  <br/> |<span data-ttu-id="51f51-p112">Когда вы расширяете локальный домен через подключение между организациями, пользователи получают доступ к ферме SharePoint через интрасеть, как будто она размещена локально. Вы можете использовать локальные службы Active Directory и DNS.</span><span class="sxs-lookup"><span data-stu-id="51f51-p112">When you extend the on-premises domain through a cross-premises connection, users access the SharePoint farm via your intranet as if it were hosted on-premises. You can take advantage of your on-premises Active Directory and DNS implementation.</span></span>  <br/> <span data-ttu-id="51f51-160">Для создания среды аварийного восстановления в Azure необходимо соединение между организациями, чтобы обрабатывать отказы локальной фермы.</span><span class="sxs-lookup"><span data-stu-id="51f51-160">A cross-premises connection is required for building a disaster-recovery environment in Azure to fail over to from your on-premises farm.</span></span>  <br/> |
   
<span data-ttu-id="51f51-p113">В этой статье представлены проектные решения для расширения локального домена через подключение между организациями. Если ваше решение использует выделенный домен, подключение между организациями не требуется.</span><span class="sxs-lookup"><span data-stu-id="51f51-p113">This article includes design concepts for extending the on-premises domain through a cross-premises connection. If your solution uses a dedicated domain, you don't need a cross-premises connection.</span></span>
  
## <a name="design-the-virtual-network"></a><span data-ttu-id="51f51-163">Разработка виртуальной сети</span><span class="sxs-lookup"><span data-stu-id="51f51-163">Design the virtual network</span></span>

<span data-ttu-id="51f51-p114">Для начала вам потребуется виртуальная сеть в Azure, включающая подсети, в которых будут размещаться виртуальные машины. Для виртуальной сети необходимо пространство частных IP-адресов, части которого назначаются подсетям.</span><span class="sxs-lookup"><span data-stu-id="51f51-p114">First you need a virtual network in Azure, which includes subnets on which you will place your virtual machines. The virtual network needs a private IP address space, portions of which you assign to the subnets.</span></span>
  
<span data-ttu-id="51f51-166">Если вы расширяете локальную сеть в Azure через подключение между организациями (требуется для среды аварийного восстановления), необходимо выбрать пространство частных адресов, которое еще не используется в сети организации и может включать локальную среду и другие виртуальные сети Azure.</span><span class="sxs-lookup"><span data-stu-id="51f51-166">If you are extending your on-premises network to Azure through a cross-premises connection (required for a disaster recovery environment), you must choose a private address space that is not already in use elsewhere in your organization network, which can include your on-premises environment and other Azure virtual networks.</span></span> 
  
<span data-ttu-id="51f51-167">**Рисунок 1. Локальная среда с виртуальной сетью в Azure**</span><span class="sxs-lookup"><span data-stu-id="51f51-167">**Figure 1: On-premises environment with a virtual network in Azure**</span></span>

![Конструкция виртуальной сети Microsoft Azure для решения SharePoint. Одна подсеть для шлюза Azure. Одна подсеть для виртуальных машин.](media/OPrrasconWA-AZarch.png)
  
<span data-ttu-id="51f51-171">На этой схеме:</span><span class="sxs-lookup"><span data-stu-id="51f51-171">In this diagram:</span></span>
  
- <span data-ttu-id="51f51-p116">Виртуальная сеть в Azure показана рядом с локальной средой. Между двумя средами еще не установлено подключение (VPN-подключение типа "сеть-сеть" или подключение ExpressRoute);</span><span class="sxs-lookup"><span data-stu-id="51f51-p116">A virtual network in Azure is illustrated side-by-side to the on-premises environment. The two environments are not yet connected by a cross-premises connection, which can be a site-to-site VPN connection or ExpressRoute.</span></span>
    
- <span data-ttu-id="51f51-p117">Сейчас виртуальная сеть включает только подсети без остальных элементов архитектуры. В одной подсети будет размещаться шлюз Azure, а в других — уровни фермы SharePoint с дополнительной подсетью для Active Directory и DNS.</span><span class="sxs-lookup"><span data-stu-id="51f51-p117">At this point, the virtual network just includes the subnets and no other architectural elements. One subnet will host the Azure gateway and other subnets host the tiers of the SharePoint farm, with an additional one for Active Directory and DNS.</span></span>
    
## <a name="add-cross-premises-connectivity"></a><span data-ttu-id="51f51-176">Добавление подключения между организациями</span><span class="sxs-lookup"><span data-stu-id="51f51-176">Add cross-premises connectivity</span></span>

<span data-ttu-id="51f51-p118">Следующий этап развертывания  создание подключения между организациями (если это применимо к вашему решению). В схеме подключений между организациями шлюз Azure находится в отдельной подсети, которую необходимо создать и которой нужно назначить пространство адресов.</span><span class="sxs-lookup"><span data-stu-id="51f51-p118">The next deployment step is to create the cross-premises connection (if this applies to your solution). For cross-premises connections, a Azure gateway resides in a separate gateway subnet, which you must create and assign an address space.</span></span> 
  
<span data-ttu-id="51f51-179">При планировании подключения между организациями необходимо определить и создать шлюз Azure и подключение к локальному устройству шлюза.</span><span class="sxs-lookup"><span data-stu-id="51f51-179">When you plan for a cross-premises connection, you define and create an Azure gateway and connection to an on-premises gateway device.</span></span>
  
<span data-ttu-id="51f51-180">**Рисунок 2. Использование шлюза Azure и локального устройства шлюза для установки подключения типа "сеть-сеть" между локальной средой и Azure**</span><span class="sxs-lookup"><span data-stu-id="51f51-180">**Figure 2: Using an Azure gateway and an on-premises gateway device to provide site-to-site connectivity between the on-premises environment and Azure**</span></span>

![Локальная среда подключена к виртуальной сети Azure с помощью VPN-подключения типа "сеть-сеть" или подключения ExpressRoute](media/AZarch-VPNgtwyconnct.png)
  
<span data-ttu-id="51f51-182">На этой схеме:</span><span class="sxs-lookup"><span data-stu-id="51f51-182">In this diagram:</span></span>
  
- <span data-ttu-id="51f51-183">В отличие от предыдущей схемы, здесь добавлено подключение между локальной средой и виртуальной сетью Azure (VPN-подключение типа "сеть-сеть" или подключение ExpressRoute).</span><span class="sxs-lookup"><span data-stu-id="51f51-183">Adding to the previous diagram, the on-premises environment is connected to the Azure virtual network by a cross-premise connection, which can be a site-to-site VPN connection or ExpressRoute.</span></span>
    
- <span data-ttu-id="51f51-184">Шлюз Azure находится в подсети шлюза.</span><span class="sxs-lookup"><span data-stu-id="51f51-184">An Azure gateway is on a gateway subnet.</span></span>
    
- <span data-ttu-id="51f51-185">Локальная среда включает устройство шлюза, например маршрутизатор или VPN-сервер.</span><span class="sxs-lookup"><span data-stu-id="51f51-185">The on-premises environment includes a gateway device, such as a router or VPN server.</span></span>
    
<span data-ttu-id="51f51-186">Дополнительные сведения о планировании и создании распределенной виртуальной сети см. в статье [Подключение локальной сети к виртуальной сети Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="51f51-186">For additional information to plan for and create a cross-premises virtual network, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
  
## <a name="add-active-directory-domain-services-ad-ds-and-dns"></a><span data-ttu-id="51f51-187">Добавление доменных служб Active Directory (AD DS) и DNS</span><span class="sxs-lookup"><span data-stu-id="51f51-187">Add Active Directory Domain Services (AD DS) and DNS</span></span>

<span data-ttu-id="51f51-188">Для аварийного восстановления в Azure доменные службы AD на сервере Windows и DNS развертываются в гибридном сценарии, где AD на сервере Windows развертывается как в локальной среде, так и на виртуальных машинах Azure.</span><span class="sxs-lookup"><span data-stu-id="51f51-188">For disaster recovery in Azure, you deploy Windows Server AD and DNS in a hybrid scenario where Windows Server AD is deployed both on-premises and on Azure virtual machines.</span></span>
  
<span data-ttu-id="51f51-189">**Рисунок 3. Гибридная конфигурация домена Active Directory**</span><span class="sxs-lookup"><span data-stu-id="51f51-189">**Figure 3: Hybrid Active Directory domain configuration**</span></span>

![Две виртуальные машины, развернутые в виртуальной сети Azure и подсети фермы SharePoint — это реплики контроллеров домена и DNS-серверы](media/AZarch-HyADdomainConfig.png)
  
<span data-ttu-id="51f51-p119">В отличие от предыдущих схем, на этой схеме в подсеть AD на сервере Windows и DNS добавлены две виртуальные машины. Это реплики контроллеров доменов и DNS-серверов. Они являются расширением локальной среды AD на сервере Windows.</span><span class="sxs-lookup"><span data-stu-id="51f51-p119">This diagram builds on the previous diagrams by adding two virtual machines to a Windows Server AD and DNS subnet. These virtual machines are replica domain controllers and DNS servers. They are an extension of the on-premises Windows Server AD environment.</span></span> 
  
<span data-ttu-id="51f51-p120">В таблице ниже приведены рекомендации по настройке этих виртуальных машин в Azure. Используйте их в качестве основы для разработки своей среды  даже для выделенного домена, где среда Azure не подключена к локальной среде.</span><span class="sxs-lookup"><span data-stu-id="51f51-p120">The following table provides configuration recommendations for these virtual machines in Azure. Use these as a starting point for designing your own environment—even for a dedicated domain where your Azure environment doesn't communicate with your on-premises environment.</span></span>
  
|<span data-ttu-id="51f51-196">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="51f51-196">**Item**</span></span>|<span data-ttu-id="51f51-197">**Конфигурация**</span><span class="sxs-lookup"><span data-stu-id="51f51-197">**Configuration**</span></span>|
|:-----|:-----|
|<span data-ttu-id="51f51-198">Размер виртуальных машин в Azure</span><span class="sxs-lookup"><span data-stu-id="51f51-198">Virtual machine size in Azure</span></span>  <br/> |<span data-ttu-id="51f51-199">Размер A1 или A2 стандартного уровня</span><span class="sxs-lookup"><span data-stu-id="51f51-199">A1 or A2 size in the Standard tier</span></span>  <br/> |
|<span data-ttu-id="51f51-200">Операционная система</span><span class="sxs-lookup"><span data-stu-id="51f51-200">Operating system</span></span>  <br/> |<span data-ttu-id="51f51-201">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="51f51-201">Windows Server 2012 R2</span></span>  <br/> |
|<span data-ttu-id="51f51-202">Роль Active Directory</span><span class="sxs-lookup"><span data-stu-id="51f51-202">Active Directory role</span></span>  <br/> |<span data-ttu-id="51f51-p121">Контроллер домена AD DS, выбранный в качестве сервера глобального каталога. Эта конфигурация снижает выходной трафик соединения между организациями.</span><span class="sxs-lookup"><span data-stu-id="51f51-p121">AD DS domain controller designated as a global catalog server. This configuration reduces egress traffic across the cross-premises connection.</span></span>  <br/> <span data-ttu-id="51f51-205">В среде с несколькими доменами и высокими темпами роста (такие среды встречаются редко) настройте локальные контроллеры домена так, чтобы они не синхронизировались с серверами глобального каталога в Azure, что позволяет снизить трафик репликации.</span><span class="sxs-lookup"><span data-stu-id="51f51-205">In a multidomain environment with high rates of change (this is not common), configure domain controllers on premises not to sync with the global catalog servers in Azure, to reduce replication traffic.</span></span>  <br/> |
|<span data-ttu-id="51f51-206">Роль DNS</span><span class="sxs-lookup"><span data-stu-id="51f51-206">DNS role</span></span>  <br/> |<span data-ttu-id="51f51-207">Установка и настройка службы DNS-серверов на контроллерах доменов.</span><span class="sxs-lookup"><span data-stu-id="51f51-207">Install and configure the DNS Server service on the domain controllers.</span></span>  <br/> |
|<span data-ttu-id="51f51-208">Диски с данными</span><span class="sxs-lookup"><span data-stu-id="51f51-208">Data disks</span></span>  <br/> |<span data-ttu-id="51f51-p122">Разместите базу данных Active Directory, журналы и SYSVOL на дополнительных дисках с данными Azure. Не размещайте их на диске операционной системы и временных дисках, предоставленных Azure.</span><span class="sxs-lookup"><span data-stu-id="51f51-p122">Place the Active Directory database, logs, and SYSVOL on additional Azure data disks. Do not place these on the operating system disk or the temporary disks provided by Azure.</span></span>  <br/> |
|<span data-ttu-id="51f51-211">IP-адреса</span><span class="sxs-lookup"><span data-stu-id="51f51-211">IP addresses</span></span>  <br/> |<span data-ttu-id="51f51-212">Используйте статические IP-адреса и настройте виртуальную сеть, чтобы назначить эти адреса виртуальным машинам в виртуальной сети после того, как будут настроены контроллеры доменов.</span><span class="sxs-lookup"><span data-stu-id="51f51-212">Use static IP addresses and configure the virtual network to assign these addresses to the virtual machines in the virtual network after the domain controllers have been configured.</span></span>  <br/> |
   
> [!IMPORTANT]
> <span data-ttu-id="51f51-p123">Перед развертыванием Active Directory в Azure прочитайте [руководства по развертыванию Windows Server Active Directory на виртуальных машинах Azure](https://go.microsoft.com/fwlink/p/?linkid=392681). Они помогут вам определить, требуются ли для вашего решения другие параметры конфигурации или другая архитектура.</span><span class="sxs-lookup"><span data-stu-id="51f51-p123">Before you deploy Active Directory in Azure, read [Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines](https://go.microsoft.com/fwlink/p/?linkid=392681). These help you determine if a different architecture or different configuration settings are needed for your solution.</span></span> 
  
## <a name="add-the-sharepoint-farm"></a><span data-ttu-id="51f51-215">Добавление фермы SharePoint</span><span class="sxs-lookup"><span data-stu-id="51f51-215">Add the SharePoint farm</span></span>

<span data-ttu-id="51f51-216">Разместите виртуальные машины фермы SharePoint по уровням соответствующей подсети.</span><span class="sxs-lookup"><span data-stu-id="51f51-216">Place the virtual machines of the SharePoint farm in tiers on the appropriate subnets.</span></span>
  
<span data-ttu-id="51f51-217">**Рисунок 4. Размещение виртуальных машин SharePoint**</span><span class="sxs-lookup"><span data-stu-id="51f51-217">**Figure 4: Placement of SharePoint virtual machines**</span></span>

![Серверы баз данных и роли сервера SharePoint добавлены в виртуальную сеть Azure в подсети фермы SharePoint](media/AZarch-SPVMsinCloudSer.png)
  
<span data-ttu-id="51f51-219">В отличие от предыдущих схем, на этой схеме на соответствующие уровни добавлены роли серверов фермы SharePoint.</span><span class="sxs-lookup"><span data-stu-id="51f51-219">This diagram builds on the previous diagrams by adding the SharePoint farm server roles in their respective tiers.</span></span>
  
- <span data-ttu-id="51f51-220">Две виртуальные машины баз данных, на которых запущен SQL Server, образуют уровень баз данных.</span><span class="sxs-lookup"><span data-stu-id="51f51-220">Two database virtual machines running SQL Server create the database tier.</span></span>
    
- <span data-ttu-id="51f51-221">Две виртуальные машины, на которых запущен SharePoint Server 2013, на каждый из следующих уровней: серверы переднего плана, серверы распределенного кэша и тыловые серверы.</span><span class="sxs-lookup"><span data-stu-id="51f51-221">Two virtual machines running SharePoint Server 2013 for each of the following tiers: front end servers, distributed cache servers, and back end servers.</span></span>
    
## <a name="design-and-fine-tune-server-roles-for-availability-sets-and-fault-domains"></a><span data-ttu-id="51f51-222">Разработка и точная настройка ролей серверов для групп доступности и доменов сбоя</span><span class="sxs-lookup"><span data-stu-id="51f51-222">Design and fine tune server roles for availability sets and fault domains</span></span>

<span data-ttu-id="51f51-p124">Домен сбоя  это набор оборудования, на котором выполняются экземпляры ролей. Инфраструктура Azure может одновременно обновлять все виртуальные машины в одном домене сбоя. Тем не менее они могут одновременно отказать, так как используют одну стойку. Чтобы не размещать две виртуальные машины в одном домене сбоя, вы можете настроить их как группу доступности, тогда каждая виртуальная машина будет размещаться в отдельном домене сбоя. Если три виртуальные машины настроены как группа доступности, Azure гарантирует, что в одном домене сбоя размещается не больше двух виртуальных машин.</span><span class="sxs-lookup"><span data-stu-id="51f51-p124">A fault domain is a grouping of hardware in which role instances run. Virtual machines within the same fault domain can be updated by the Azure infrastructure at the same time. Or, they can fail at the same time because they share the same rack. To avoid the risk of having two virtual machines on the same fault domain, you can configure your virtual machines as an availability set, which ensures that each virtual machine is in a different fault domain. If three virtual machines are configured as an availability set, Azure guarantees that no more than two of the virtual machines are located in the same fault domain.</span></span>
  
<span data-ttu-id="51f51-p125">При разработке архитектуры Azure для фермы SharePoint настройте одинаковые роли серверов как группу доступности. Это обеспечит распределение виртуальных машин между несколькими доменами сбоя.</span><span class="sxs-lookup"><span data-stu-id="51f51-p125">When you design the Azure architecture for a SharePoint farm, configure identical server roles to be part of an availability set. This ensures that your virtual machines are spread across multiple fault domains.</span></span>
  
<span data-ttu-id="51f51-230">**Рисунок 5. Использование групп доступности Azure для обеспечения высокой доступности уровней фермы SharePoint**</span><span class="sxs-lookup"><span data-stu-id="51f51-230">**Figure 5: Use Azure Availability Sets to provide high availability for the SharePoint farm tiers**</span></span>

![Конфигурация групп доступности в инфраструктуре Azure для решения SharePoint 2013](media/AZenv-WinAzureAvailSetsHA.png)
  
<span data-ttu-id="51f51-p126">На этой схеме показана конфигурация групп доступности в инфраструктуре Azure. Перечисленные ниже роли используют отдельную группу доступности.</span><span class="sxs-lookup"><span data-stu-id="51f51-p126">This diagram calls out the configuration of availability sets within the Azure infrastructure. Each of the following roles share a separate availability set:</span></span>
  
- <span data-ttu-id="51f51-234">Active Directory и DNS</span><span class="sxs-lookup"><span data-stu-id="51f51-234">Active Directory and DNS</span></span>
    
- <span data-ttu-id="51f51-235">База данных</span><span class="sxs-lookup"><span data-stu-id="51f51-235">Database</span></span>
    
- <span data-ttu-id="51f51-236">Тыловой сервер</span><span class="sxs-lookup"><span data-stu-id="51f51-236">Back end</span></span>
    
- <span data-ttu-id="51f51-237">Сервер распределенного кэша</span><span class="sxs-lookup"><span data-stu-id="51f51-237">Distribute cache</span></span>
    
- <span data-ttu-id="51f51-238">Интерфейсный сервер</span><span class="sxs-lookup"><span data-stu-id="51f51-238">Front end</span></span>
    
<span data-ttu-id="51f51-p127">Может потребоваться точная настройка фермы SharePoint на платформе Azure. Чтобы обеспечить высокую доступность всех компонентов, убедитесь, что все роли серверов настроены одинаково.</span><span class="sxs-lookup"><span data-stu-id="51f51-p127">The SharePoint farm might need to be fine tuned in the Azure platform. To ensure high availability of all components, ensure that the server roles are all configured identically.</span></span>
  
<span data-ttu-id="51f51-p128">Ниже приводится пример стандартной архитектуры веб-сайтов, которая соответствует определенным требованиям к мощности и производительности. Этот пример представлен в модели [Архитектуры поиска на веб-сайтах для SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=261519).</span><span class="sxs-lookup"><span data-stu-id="51f51-p128">Here is an example that shows a standard Internet Sites architecture that meets specific capacity and performance goals. This example is featured in the following architecture model: [Internet Sites Search Architectures for SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=261519).</span></span>
  
<span data-ttu-id="51f51-243">**Рисунок 6. Пример планирования емкости и производительности в трехуровневой ферме**</span><span class="sxs-lookup"><span data-stu-id="51f51-243">**Figure 6: Planning example for capacity and performance goals in a three-tier farm**</span></span>

![Стандартная архитектура SharePoint 2013 Internet Sites с распределением компонентов, которое соответствует определенным требованиям к мощности и производительности](media/AZarch-CapPerfexmpArch.png)
  
<span data-ttu-id="51f51-245">На этой схеме:</span><span class="sxs-lookup"><span data-stu-id="51f51-245">In this diagram:</span></span>
  
- <span data-ttu-id="51f51-246">Представлена трехуровневая ферма: веб-серверы, серверы приложений и серверы баз данных;</span><span class="sxs-lookup"><span data-stu-id="51f51-246">A three-tier farm is represented: web servers, application servers, and database servers.</span></span>
    
- <span data-ttu-id="51f51-247">Три веб-сервера настроены одинаково с несколькими компонентами.</span><span class="sxs-lookup"><span data-stu-id="51f51-247">The three web servers are configured identically with multiple components.</span></span>
    
- <span data-ttu-id="51f51-248">Два сервера баз данных настроены одинаково.</span><span class="sxs-lookup"><span data-stu-id="51f51-248">The two database servers are configured identically.</span></span>
    
- <span data-ttu-id="51f51-p129">Три сервера приложений настроены по-разному. Эти роли серверов требуют точной настройки для групп доступности в Azure.</span><span class="sxs-lookup"><span data-stu-id="51f51-p129">The three application servers are not configured identically. These server roles require fine tuning for availability sets in Azure.</span></span>
    
<span data-ttu-id="51f51-251">Рассмотрим уровень серверов приложений подробнее.</span><span class="sxs-lookup"><span data-stu-id="51f51-251">Let's look closer at the application server tier.</span></span>
  
<span data-ttu-id="51f51-252">**Рисунок 7. Уровень серверов приложений перед точной настройкой**</span><span class="sxs-lookup"><span data-stu-id="51f51-252">**Figure 7: Application server tier before fine tuning**</span></span>

![Пример уровня серверов приложений SharePoint Server 2013 перед настройкой для групп доступности Microsoft Azure](media/AZarch-AppServtierBefore.png)
  
<span data-ttu-id="51f51-254">На этой схеме:</span><span class="sxs-lookup"><span data-stu-id="51f51-254">In this diagram:</span></span>
  
- <span data-ttu-id="51f51-255">уровень приложений включает три сервера;</span><span class="sxs-lookup"><span data-stu-id="51f51-255">Three servers are included in the application tier.</span></span>
    
- <span data-ttu-id="51f51-256">первый сервер включает четыре компонента;</span><span class="sxs-lookup"><span data-stu-id="51f51-256">The first server includes four components.</span></span>
    
- <span data-ttu-id="51f51-257">второй сервер включает три компонента;</span><span class="sxs-lookup"><span data-stu-id="51f51-257">The second server includes three components.</span></span>
    
- <span data-ttu-id="51f51-258">третий сервер включает два компонента.</span><span class="sxs-lookup"><span data-stu-id="51f51-258">The third server includes two components.</span></span>
    
<span data-ttu-id="51f51-p130">Количество компонентов определяется требованиями к производительности и емкости фермы. Чтобы адаптировать эту архитектуру для Azure, мы реплицируем четыре компонента на всех трех серверах. Таким образом, количество компонентов будет превышать необходимое. С другой стороны, такая схема обеспечивает высокую доступность всех четырех компонентов на платформе Azure, когда эти три виртуальные машины назначаются группе доступности.</span><span class="sxs-lookup"><span data-stu-id="51f51-p130">You determine the number of components by the performance and capacity targets for the farm. To adapt this architecture for Azure, we'll replicate the four components across all three servers. This increases the number of components beyond what is necessary for performance and capacity. The tradeoff is that this design ensures high availability of all four components in the Azure platform when these three virtual machines are assigned to an availability set.</span></span>
  
<span data-ttu-id="51f51-263">**Рисунок 8. Уровень серверов приложений после точной настройки**</span><span class="sxs-lookup"><span data-stu-id="51f51-263">**Figure 8: Application server tier after fine tuning**</span></span>

![Пример уровня серверов приложений SharePoint Server 2013 после настройки для групп доступности Microsoft Azure](media/AZarch-AppServtierAfter.png)
  
<span data-ttu-id="51f51-265">На этой схеме показаны все три сервера приложений, настроенных одинаково с одними и теми же четырьмя компонентами.</span><span class="sxs-lookup"><span data-stu-id="51f51-265">This diagram shows all three application servers configured identically with the same four components.</span></span>
  
<span data-ttu-id="51f51-266">После того как мы добавили к уровням фермы SharePoint группы доступности, этап реализации завершен.</span><span class="sxs-lookup"><span data-stu-id="51f51-266">When we add availability sets to the tiers of the SharePoint farm, the implementation is complete.</span></span>
  
<span data-ttu-id="51f51-267">**Рисунок 9. Готовая ферма SharePoint в службах инфраструктуры Azure**</span><span class="sxs-lookup"><span data-stu-id="51f51-267">**Figure 9: The completed SharePoint farm in Azure infrastructure services**</span></span>

![Пример фермы SharePoint 2013 в службах инфраструктуры Azure с виртуальной сетью, подключением между организациями, подсетями, виртуальными машинами и группами доступности](media/7256292f-bf11-485b-8917-41ba206153ee.png)
  
<span data-ttu-id="51f51-269">На этой схеме показана ферма SharePoint, реализованная в службах инфраструктуры Azure: группы доступности обеспечивают домены сбоя для серверов на каждом уровне.</span><span class="sxs-lookup"><span data-stu-id="51f51-269">This diagram shows the SharePoint farm implemented in Azure infrastructure services, with availability sets to provide fault domains for the servers in each tier.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="51f51-270">См. также</span><span class="sxs-lookup"><span data-stu-id="51f51-270">See Also</span></span>

[<span data-ttu-id="51f51-271">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="51f51-271">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.yml)
  
[<span data-ttu-id="51f51-272">Веб-сайты в Microsoft Azure с использованием SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="51f51-272">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
  
[<span data-ttu-id="51f51-273">Аварийное восстановление SharePoint Server 2013 в Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="51f51-273">SharePoint Server 2013 Disaster Recovery in Microsoft Azure</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)


