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
ms.custom: Ent_Architecture
ms.assetid: 98fc1006-9399-4ff0-a216-c7c05820d822
description: Сводка. Решения SharePoint 2013 можно размещать на виртуальных машинах Microsoft Azure. Узнайте, какие типы решений хорошо для этого подходят и как настроить Microsoft Azure для их размещения.
ms.openlocfilehash: ff5837030384a7f10dc36bb9c436394a19521254
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844910"
---
# <a name="microsoft-azure-architectures-for-sharepoint-2013"></a><span data-ttu-id="fd374-104">Архитектуры Microsoft Azure для SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="fd374-104">Microsoft Azure Architectures for SharePoint 2013</span></span>

 <span data-ttu-id="fd374-p102">**Сводка.** Решения SharePoint 2013 можно размещать на виртуальных машинах Microsoft Azure. Узнайте, какие типы решений хорошо для этого подходят и как настроить Microsoft Azure для их размещения.</span><span class="sxs-lookup"><span data-stu-id="fd374-p102">**Summary:** SharePoint 2013 solutions can be hosted in Microsoft Azure virtual machines. Learn which type of solutions are a good fit and how to set up Microsoft Azure to host one.</span></span>
  
<span data-ttu-id="fd374-p103">Среда Azure отлично подходит для размещения решений SharePoint Server 2013. В большинстве случаев рекомендуем использовать Office 365, но ферма SharePoint Server, размещенная в Azure, может быть хорошим вариантом для определенных решений. В этой статье описано, как спроектировать решения SharePoint для обеспечения совместимости с платформой Azure. В качестве примеров используются два следующих решения:</span><span class="sxs-lookup"><span data-stu-id="fd374-p103">Azure is a good environment for hosting a SharePoint Server 2013 solution. In most cases, we recommend Office 365, but a SharePoint Server farm hosted in Azure can be a good option for specific solutions. This article describes how to architect SharePoint solutions so they are a good fit in the Azure platform. The following two specific solutions are used as examples:</span></span>
  
- [<span data-ttu-id="fd374-111">Аварийное восстановление SharePoint Server 2013 в Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="fd374-111">SharePoint Server 2013 Disaster Recovery in Microsoft Azure</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)
    
- [<span data-ttu-id="fd374-112">Веб-сайты в Microsoft Azure с использованием SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="fd374-112">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
    
## <a name="recommended-sharepoint-solutions-for-azure-infrastructure-services"></a><span data-ttu-id="fd374-113">Рекомендуемые решения SharePoint для служб инфраструктуры Azure</span><span class="sxs-lookup"><span data-stu-id="fd374-113">Recommended SharePoint solutions for Azure Infrastructure Services</span></span>

<span data-ttu-id="fd374-p104">Службы инфраструктуры Azure отлично подходят для размещения решений SharePoint. Не все решения одинаково совместимы с этой платформой. В приведенной ниже таблице представлены рекомендуемые решения.</span><span class="sxs-lookup"><span data-stu-id="fd374-p104">Azure infrastructure services is a compelling option for hosting SharePoint solutions. Some solutions are a better fit for this platform than others. The following table shows recommended solutions.</span></span>
  
|<span data-ttu-id="fd374-117">**Решение**</span><span class="sxs-lookup"><span data-stu-id="fd374-117">**Solution**</span></span>|<span data-ttu-id="fd374-118">**Преимущества работы с Azure**</span><span class="sxs-lookup"><span data-stu-id="fd374-118">**Why this solution is recommended for Azure**</span></span>|
|:-----|:-----|
|<span data-ttu-id="fd374-119">Среды разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="fd374-119">Development and test environments</span></span>  <br/> |<span data-ttu-id="fd374-120">Создавать такие среды и управлять ими легко.</span><span class="sxs-lookup"><span data-stu-id="fd374-120">It's easy to create and manage these environments.</span></span>  <br/> |
|<span data-ttu-id="fd374-121">Аварийное восстановление локальных ферм SharePoint в Azure</span><span class="sxs-lookup"><span data-stu-id="fd374-121">Disaster recovery of on-premises SharePoint farms to Azure</span></span>  <br/> |<span data-ttu-id="fd374-122">**Размещенный вспомогательный центр обработки данных** Используйте Azure, чтобы не вкладывать средства во вспомогательный центр обработки данных в другом регионе.</span><span class="sxs-lookup"><span data-stu-id="fd374-122">**Hosted secondary datacenter** Use Azure instead of investing in a secondary datacenter in a different region.</span></span> <br/> <span data-ttu-id="fd374-p105">**Снижение затрат на среды аварийного восстановления** По сравнению с локальной средой аварийного восстановления потребуется обслуживать и оплачивать меньше ресурсов. Их количество зависит от выбранной среды аварийного восстановления: с холодным или горячим резервированием либо горячей заменой.</span><span class="sxs-lookup"><span data-stu-id="fd374-p105">**Lower-cost disaster-recovery environments** Maintain and pay for fewer resources than an on-premises disaster recovery environment. The number of resources depends on the disaster recovery environment you choose: cold standby, warm standby, or hot standby. </span></span><br/> <span data-ttu-id="fd374-p106">**Более эластичная платформа** В случае аварии вы можете с легкостью развернуть ферму восстановления SharePoint в соответствии с требованиями к нагрузке. Когда необходимость в дополнительных ресурсах пропадет, вы можете свернуть ферму.</span><span class="sxs-lookup"><span data-stu-id="fd374-p106">**More elastic platform** In the event of a disaster, easily scale-out your recovery SharePoint farm to meet load requirements. Scale in when you no longer need the resources. </span></span><br/> <span data-ttu-id="fd374-127">См. статью [Аварийное восстановление SharePoint Server 2013 в Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md).</span><span class="sxs-lookup"><span data-stu-id="fd374-127">See [SharePoint Server 2013 Disaster Recovery in Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md).</span></span>  <br/> |
|<span data-ttu-id="fd374-128">Сайты в Интернете, которые используют функции и масштабирование, недоступные в Office 365</span><span class="sxs-lookup"><span data-stu-id="fd374-128">Internet-facing sites that use features and scale not available in Office 365</span></span>  <br/> |<span data-ttu-id="fd374-129">**Правильные приоритеты** Сосредоточьтесь на создании отличного сайта, а не инфраструктуры.</span><span class="sxs-lookup"><span data-stu-id="fd374-129">**Focus your efforts** Concentrate on building a great site rather than building infrastructure.</span></span> <br/> <span data-ttu-id="fd374-p107">**Воспользуйтесь преимуществами эластичности Azure** Изменяйте размер фермы в соответствии с потребностями, добавляя новые серверы, и платите только за необходимые вам ресурсы. Динамическое распределение машин не поддерживается (автомасштабирование).</span><span class="sxs-lookup"><span data-stu-id="fd374-p107">**Take advantage of elasticity in Azure** Size the farm for the demand by adding new servers, and pay only for resources you need. Dynamic machine allocation is not supported (auto scale). </span></span><br/> <span data-ttu-id="fd374-132">**Использование службы Azure Active Directory (AD)** Воспользуйтесь преимуществами Azure AD для учетных записей клиентов.</span><span class="sxs-lookup"><span data-stu-id="fd374-132">**Use Azure Active Directory (AD)** Take advantage of Azure AD for customer accounts.</span></span> <br/> <span data-ttu-id="fd374-133">**Добавление функций SharePoint, недоступных в Office 365** Добавьте функции подробных отчетов и аналитики.</span><span class="sxs-lookup"><span data-stu-id="fd374-133">**Add SharePoint functionality not available in Office 365** Add deep reporting and web analytics.</span></span> <br/> <span data-ttu-id="fd374-134">См. статью [Веб-сайты в Microsoft Azure с использованием SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md).</span><span class="sxs-lookup"><span data-stu-id="fd374-134">See [Internet Sites in Microsoft Azure using SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md).</span></span>  <br/> |
|<span data-ttu-id="fd374-135">Фермы приложений для поддержки Office 365 или локальных сред</span><span class="sxs-lookup"><span data-stu-id="fd374-135">App farms to support Office 365 or on-premises environments</span></span>  <br/> |<span data-ttu-id="fd374-136">**Создание, тестирование и размещение приложений** в Azure для поддержки как локальных, так и облачных сред.</span><span class="sxs-lookup"><span data-stu-id="fd374-136">**Build, test, and host apps** in Azure to support both on-premises and cloud environments.</span></span> <br/> <span data-ttu-id="fd374-137">**Разместите эту роль** в Azure, не покупая новое оборудование для локальных сред.</span><span class="sxs-lookup"><span data-stu-id="fd374-137">**Host this role** in Azure instead of buying new hardware for on-premises environments.</span></span> <br/> |
   
<span data-ttu-id="fd374-138">Для решений интрасети и совместной работы рассмотрите следующие факторы.</span><span class="sxs-lookup"><span data-stu-id="fd374-138">For intranet and collaboration solutions and workloads, consider the following options:</span></span>
  
- <span data-ttu-id="fd374-p108">Определите, соответствует ли Office 365 бизнес-требованиям и может ли быть частью решения. В Office 365 представлено много функций, которые постоянно обновляются.</span><span class="sxs-lookup"><span data-stu-id="fd374-p108">Determine if Office 365 meets your business requirements or can be part of the solution. Office 365 provides a rich feature set that is always up to date.</span></span>
    
- <span data-ttu-id="fd374-p109">Если Office 365 не соответствует вашим бизнес-требованиям, рекомендуется стандартная локальная реализация SharePoint 2013 из служб консультации Майкрософт (MCS). Поддерживать стандартную архитектуру может быть дешевле и проще, чем персонализированное решение.</span><span class="sxs-lookup"><span data-stu-id="fd374-p109">If Office 365 does not meet all your business requirements, consider a standard implementation of SharePoint 2013 on premises from Microsoft Consulting Services (MCS). A standard architecture can be a quicker, cheaper, and easier solution for you to support than a customized one.</span></span> 
    
- <span data-ttu-id="fd374-143">Если стандартная реализация не соответствует вашим бизнес-требованиям, рекомендуется персонализированное локальное решение.</span><span class="sxs-lookup"><span data-stu-id="fd374-143">If a standard implementation doesn't meet your business requirements, consider a customized on-premises solution.</span></span>
    
- <span data-ttu-id="fd374-p110">Если ваши бизнес-требования включают использование облачной платформы, рассмотрите возможность стандартной или персонализированной реализации SharePoint 2013 с размещением в службах инфраструктуры Azure. Поддерживать решения SharePoint в Azure намного проще, чем другие общедоступные облачные платформы (не корпорации Майкрософт).</span><span class="sxs-lookup"><span data-stu-id="fd374-p110">If using a cloud platform is important for your business requirements, consider a standard or customized implementation of SharePoint 2013 hosted in Azure infrastructure services. SharePoint solutions are much easier to support in Azure than other non-native Microsoft public cloud platforms.</span></span>
    
## <a name="before-you-design-the-azure-environment"></a><span data-ttu-id="fd374-146">Перед разработкой среды Azure</span><span class="sxs-lookup"><span data-stu-id="fd374-146">Before you design the Azure environment</span></span>

<span data-ttu-id="fd374-p111">Хотя в этой статье используются примеры топологий SharePoint, вы можете использовать эти проектные решения с любой топологией фермы SharePoint. Прежде чем разрабатывать среду Azure, используйте указанные ниже топологию, архитектуру, емкость и производительность для разработки фермы SharePoint.</span><span class="sxs-lookup"><span data-stu-id="fd374-p111">While this article uses example SharePoint topologies, you can use these design concepts with any SharePoint farm topology. Before you design the Azure environment, use the following topology, architecture, capacity, and performance guidance to design the SharePoint farm:</span></span>
  
- [<span data-ttu-id="fd374-149">Архитектура SharePoint 2013 для ИТ-специалистов</span><span class="sxs-lookup"><span data-stu-id="fd374-149">Architecture design for SharePoint 2013 IT pros</span></span>](https://technet.microsoft.com/sharepoint/fp123594.aspx)
    
- [<span data-ttu-id="fd374-150">Plan for performance and capacity management in SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="fd374-150">Plan for performance and capacity management in SharePoint Server 2013</span></span>](https://technet.microsoft.com/library/8dd52916-f77d-4444-b593-1f7d6f330e5f.aspx)
    
## <a name="determine-the-active-directory-domain-type"></a><span data-ttu-id="fd374-151">Определение типа домена Active Directory</span><span class="sxs-lookup"><span data-stu-id="fd374-151">Determine the Active Directory domain type</span></span>

<span data-ttu-id="fd374-p112">Каждая ферма SharePoint Server использует службу Active Directory для создания учетных записей администраторов. В настоящее время существует два варианта для решений SharePoint в Azure. Они описываются в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="fd374-p112">Each SharePoint Server farm relies on Active Directory to provide administrative accounts for farm setup. At this time, there are two options for SharePoint solutions in Azure. These are described in the following table.</span></span>
  
|<span data-ttu-id="fd374-155">**Вариант**</span><span class="sxs-lookup"><span data-stu-id="fd374-155">**Option**</span></span>|<span data-ttu-id="fd374-156">**Описание**</span><span class="sxs-lookup"><span data-stu-id="fd374-156">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="fd374-157">Выделенный домен</span><span class="sxs-lookup"><span data-stu-id="fd374-157">Dedicated domain</span></span>  <br/> |<span data-ttu-id="fd374-p113">Вы можете развернуть выделенный изолированный домен Active Directory в Azure для поддержки фермы SharePoint. Этот вариант хорошо подходит для общедоступных сайтов в Интернете.</span><span class="sxs-lookup"><span data-stu-id="fd374-p113">You can deploy a dedicated and isolated Active Directory domain to Azure to support your SharePoint farm. This is a good choice for public-facing Internet sites.</span></span>  <br/> |
|<span data-ttu-id="fd374-160">Расширение локального домена через подключение между организациями</span><span class="sxs-lookup"><span data-stu-id="fd374-160">Extend the on-premises domain through a cross-premises connection</span></span>  <br/> |<span data-ttu-id="fd374-p114">Когда вы расширяете локальный домен через подключение между организациями, пользователи получают доступ к ферме SharePoint через интрасеть, как будто она размещена локально. Вы можете использовать локальные службы Active Directory и DNS.</span><span class="sxs-lookup"><span data-stu-id="fd374-p114">When you extend the on-premises domain through a cross-premises connection, users access the SharePoint farm via your intranet as if it were hosted on-premises. You can take advantage of your on-premises Active Directory and DNS implementation.</span></span>  <br/> <span data-ttu-id="fd374-163">Для создания среды аварийного восстановления в Azure необходимо соединение между организациями, чтобы обрабатывать отказы локальной фермы.</span><span class="sxs-lookup"><span data-stu-id="fd374-163">A cross-premises connection is required for building a disaster-recovery environment in Azure to fail over to from your on-premises farm.</span></span>  <br/> |
   
<span data-ttu-id="fd374-p115">В этой статье представлены проектные решения для расширения локального домена через подключение между организациями. Если ваше решение использует выделенный домен, подключение между организациями не требуется.</span><span class="sxs-lookup"><span data-stu-id="fd374-p115">This article includes design concepts for extending the on-premises domain through a cross-premises connection. If your solution uses a dedicated domain, you don't need a cross-premises connection.</span></span>
  
## <a name="design-the-virtual-network"></a><span data-ttu-id="fd374-166">Разработка виртуальной сети</span><span class="sxs-lookup"><span data-stu-id="fd374-166">Design the virtual network</span></span>

<span data-ttu-id="fd374-p116">Для начала вам потребуется виртуальная сеть в Azure, включающая подсети, в которых будут размещаться виртуальные машины. Для виртуальной сети необходимо пространство частных IP-адресов, части которого назначаются подсетям.</span><span class="sxs-lookup"><span data-stu-id="fd374-p116">First you need a virtual network in Azure, which includes subnets on which you will place your virtual machines. The virtual network needs a private IP address space, portions of which you assign to the subnets.</span></span>
  
<span data-ttu-id="fd374-169">Если вы расширяете локальную сеть в Azure через подключение между организациями (требуется для среды аварийного восстановления), необходимо выбрать пространство частных адресов, которое еще не используется в сети организации и может включать локальную среду и другие виртуальные сети Azure.</span><span class="sxs-lookup"><span data-stu-id="fd374-169">If you are extending your on-premises network to Azure through a cross-premises connection (required for a disaster recovery environment), you must choose a private address space that is not already in use elsewhere in your organization network, which can include your on-premises environment and other Azure virtual networks.</span></span> 
  
<span data-ttu-id="fd374-170">**Рисунок 1. Локальная среда с виртуальной сетью в Azure**</span><span class="sxs-lookup"><span data-stu-id="fd374-170">**Figure 1: On-premises environment with a virtual network in Azure**</span></span>

![Конструкция виртуальной сети Microsoft Azure для решения SharePoint. Одна подсеть для шлюза Azure. Одна подсеть для виртуальных машин.](media/OPrrasconWA-AZarch.png)
  
<span data-ttu-id="fd374-174">На этой схеме:</span><span class="sxs-lookup"><span data-stu-id="fd374-174">In this diagram:</span></span>
  
- <span data-ttu-id="fd374-p118">Виртуальная сеть в Azure показана рядом с локальной средой. Между двумя средами еще не установлено подключение (VPN-подключение типа "сеть-сеть" или подключение ExpressRoute);</span><span class="sxs-lookup"><span data-stu-id="fd374-p118">A virtual network in Azure is illustrated side-by-side to the on-premises environment. The two environments are not yet connected by a cross-premises connection, which can be a site-to-site VPN connection or ExpressRoute.</span></span>
    
- <span data-ttu-id="fd374-p119">Сейчас виртуальная сеть включает только подсети без остальных элементов архитектуры. В одной подсети будет размещаться шлюз Azure, а в других — уровни фермы SharePoint с дополнительной подсетью для Active Directory и DNS.</span><span class="sxs-lookup"><span data-stu-id="fd374-p119">At this point, the virtual network just includes the subnets and no other architectural elements. One subnet will host the Azure gateway and other subnets host the tiers of the SharePoint farm, with an additional one for Active Directory and DNS.</span></span>
    
## <a name="add-cross-premises-connectivity"></a><span data-ttu-id="fd374-179">Добавление подключения между организациями</span><span class="sxs-lookup"><span data-stu-id="fd374-179">Add cross-premises connectivity</span></span>

<span data-ttu-id="fd374-p120">Следующий этап развертывания  создание подключения между организациями (если это применимо к вашему решению). В схеме подключений между организациями шлюз Azure находится в отдельной подсети, которую необходимо создать и которой нужно назначить пространство адресов.</span><span class="sxs-lookup"><span data-stu-id="fd374-p120">The next deployment step is to create the cross-premises connection (if this applies to your solution). For cross-premises connections, a Azure gateway resides in a separate gateway subnet, which you must create and assign an address space.</span></span> 
  
<span data-ttu-id="fd374-182">При планировании подключения между организациями необходимо определить и создать шлюз Azure и подключение к локальному устройству шлюза.</span><span class="sxs-lookup"><span data-stu-id="fd374-182">When you plan for a cross-premises connection, you define and create an Azure gateway and connection to an on-premises gateway device.</span></span>
  
<span data-ttu-id="fd374-183">**Рисунок 2. Использование шлюза Azure и локального устройства шлюза для установки подключения типа "сеть-сеть" между локальной средой и Azure**</span><span class="sxs-lookup"><span data-stu-id="fd374-183">**Figure 2: Using an Azure gateway and an on-premises gateway device to provide site-to-site connectivity between the on-premises environment and Azure**</span></span>

![Локальная среда подключена к виртуальной сети Azure с помощью VPN-подключения типа "сеть-сеть" или подключения ExpressRoute](media/AZarch-VPNgtwyconnct.png)
  
<span data-ttu-id="fd374-185">На этой схеме:</span><span class="sxs-lookup"><span data-stu-id="fd374-185">In this diagram:</span></span>
  
- <span data-ttu-id="fd374-186">В отличие от предыдущей схемы, здесь добавлено подключение между локальной средой и виртуальной сетью Azure (VPN-подключение типа "сеть-сеть" или подключение ExpressRoute).</span><span class="sxs-lookup"><span data-stu-id="fd374-186">Adding to the previous diagram, the on-premises environment is connected to the Azure virtual network by a cross-premise connection, which can be a site-to-site VPN connection or ExpressRoute.</span></span>
    
- <span data-ttu-id="fd374-187">Шлюз Azure находится в подсети шлюза.</span><span class="sxs-lookup"><span data-stu-id="fd374-187">An Azure gateway is on a gateway subnet.</span></span>
    
- <span data-ttu-id="fd374-188">Локальная среда включает устройство шлюза, например маршрутизатор или VPN-сервер.</span><span class="sxs-lookup"><span data-stu-id="fd374-188">The on-premises environment includes a gateway device, such as a router or VPN server.</span></span>
    
<span data-ttu-id="fd374-189">Дополнительные сведения о планировании и создании распределенной виртуальной сети см. в статье [Подключение локальной сети к виртуальной сети Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="fd374-189">For additional information to plan for and create a cross-premises virtual network, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
  
## <a name="add-active-directory-domain-services-ad-ds-and-dns"></a><span data-ttu-id="fd374-190">Добавление доменных служб Active Directory (AD DS) и DNS</span><span class="sxs-lookup"><span data-stu-id="fd374-190">Add Active Directory Domain Services (AD DS) and DNS</span></span>

<span data-ttu-id="fd374-191">Для аварийного восстановления в Azure доменные службы AD на сервере Windows и DNS развертываются в гибридном сценарии, где AD на сервере Windows развертывается как в локальной среде, так и на виртуальных машинах Azure.</span><span class="sxs-lookup"><span data-stu-id="fd374-191">For disaster recovery in Azure, you deploy Windows Server AD and DNS in a hybrid scenario where Windows Server AD is deployed both on-premises and on Azure virtual machines.</span></span>
  
<span data-ttu-id="fd374-192">**Рисунок 3. Гибридная конфигурация домена Active Directory**</span><span class="sxs-lookup"><span data-stu-id="fd374-192">**Figure 3: Hybrid Active Directory domain configuration**</span></span>

![Две виртуальные машины, развернутые в виртуальной сети Azure и подсети фермы SharePoint — это реплики контроллеров домена и DNS-серверы](media/AZarch-HyADdomainConfig.png)
  
<span data-ttu-id="fd374-p121">В отличие от предыдущих схем, на этой схеме в подсеть AD на сервере Windows и DNS добавлены две виртуальные машины. Это реплики контроллеров доменов и DNS-серверов. Они являются расширением локальной среды AD на сервере Windows.</span><span class="sxs-lookup"><span data-stu-id="fd374-p121">This diagram builds on the previous diagrams by adding two virtual machines to a Windows Server AD and DNS subnet. These virtual machines are replica domain controllers and DNS servers. They are an extension of the on-premises Windows Server AD environment.</span></span> 
  
<span data-ttu-id="fd374-p122">В таблице ниже приведены рекомендации по настройке этих виртуальных машин в Azure. Используйте их в качестве основы для разработки своей среды  даже для выделенного домена, где среда Azure не подключена к локальной среде.</span><span class="sxs-lookup"><span data-stu-id="fd374-p122">The following table provides configuration recommendations for these virtual machines in Azure. Use these as a starting point for designing your own environment—even for a dedicated domain where your Azure environment doesn't communicate with your on-premises environment.</span></span>
  
|<span data-ttu-id="fd374-199">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="fd374-199">**Item**</span></span>|<span data-ttu-id="fd374-200">**Конфигурация**</span><span class="sxs-lookup"><span data-stu-id="fd374-200">**Configuration**</span></span>|
|:-----|:-----|
|<span data-ttu-id="fd374-201">Размер виртуальных машин в Azure</span><span class="sxs-lookup"><span data-stu-id="fd374-201">Virtual machine size in Azure</span></span>  <br/> |<span data-ttu-id="fd374-202">Размер A1 или A2 стандартного уровня</span><span class="sxs-lookup"><span data-stu-id="fd374-202">A1 or A2 size in the Standard tier</span></span>  <br/> |
|<span data-ttu-id="fd374-203">Операционная система</span><span class="sxs-lookup"><span data-stu-id="fd374-203">Operating system</span></span>  <br/> |<span data-ttu-id="fd374-204">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="fd374-204">Windows Server 2012 R2</span></span>  <br/> |
|<span data-ttu-id="fd374-205">Роль Active Directory</span><span class="sxs-lookup"><span data-stu-id="fd374-205">Active Directory role</span></span>  <br/> |<span data-ttu-id="fd374-p123">Контроллер домена AD DS, выбранный в качестве сервера глобального каталога. Эта конфигурация снижает выходной трафик соединения между организациями.</span><span class="sxs-lookup"><span data-stu-id="fd374-p123">AD DS domain controller designated as a global catalog server. This configuration reduces egress traffic across the cross-premises connection.</span></span>  <br/> <span data-ttu-id="fd374-208">В среде с несколькими доменами и высокими темпами роста (такие среды встречаются редко) настройте локальные контроллеры домена так, чтобы они не синхронизировались с серверами глобального каталога в Azure, что позволяет снизить трафик репликации.</span><span class="sxs-lookup"><span data-stu-id="fd374-208">In a multidomain environment with high rates of change (this is not common), configure domain controllers on premises not to sync with the global catalog servers in Azure, to reduce replication traffic.</span></span>  <br/> |
|<span data-ttu-id="fd374-209">Роль DNS</span><span class="sxs-lookup"><span data-stu-id="fd374-209">DNS role</span></span>  <br/> |<span data-ttu-id="fd374-210">Установка и настройка службы DNS-серверов на контроллерах доменов.</span><span class="sxs-lookup"><span data-stu-id="fd374-210">Install and configure the DNS Server service on the domain controllers.</span></span>  <br/> |
|<span data-ttu-id="fd374-211">Диски с данными</span><span class="sxs-lookup"><span data-stu-id="fd374-211">Data disks</span></span>  <br/> |<span data-ttu-id="fd374-p124">Разместите базу данных Active Directory, журналы и SYSVOL на дополнительных дисках с данными Azure. Не размещайте их на диске операционной системы и временных дисках, предоставленных Azure.</span><span class="sxs-lookup"><span data-stu-id="fd374-p124">Place the Active Directory database, logs, and SYSVOL on additional Azure data disks. Do not place these on the operating system disk or the temporary disks provided by Azure.</span></span>  <br/> |
|<span data-ttu-id="fd374-214">IP-адреса</span><span class="sxs-lookup"><span data-stu-id="fd374-214">IP addresses</span></span>  <br/> |<span data-ttu-id="fd374-215">Используйте статические IP-адреса и настройте виртуальную сеть, чтобы назначить эти адреса виртуальным машинам в виртуальной сети после того, как будут настроены контроллеры доменов.</span><span class="sxs-lookup"><span data-stu-id="fd374-215">Use static IP addresses and configure the virtual network to assign these addresses to the virtual machines in the virtual network after the domain controllers have been configured.</span></span>  <br/> |
   
> [!IMPORTANT]
> <span data-ttu-id="fd374-p125">Перед развертыванием Active Directory в Azure прочитайте [руководства по развертыванию Windows Server Active Directory на виртуальных машинах Azure](https://go.microsoft.com/fwlink/p/?linkid=392681). Они помогут вам определить, требуются ли для вашего решения другие параметры конфигурации или другая архитектура.</span><span class="sxs-lookup"><span data-stu-id="fd374-p125">Before you deploy Active Directory in Azure, read [Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines](https://go.microsoft.com/fwlink/p/?linkid=392681). These help you determine if a different architecture or different configuration settings are needed for your solution.</span></span> 
  
## <a name="add-the-sharepoint-farm"></a><span data-ttu-id="fd374-218">Добавление фермы SharePoint</span><span class="sxs-lookup"><span data-stu-id="fd374-218">Add the SharePoint farm</span></span>

<span data-ttu-id="fd374-219">Разместите виртуальные машины фермы SharePoint по уровням соответствующей подсети.</span><span class="sxs-lookup"><span data-stu-id="fd374-219">Place the virtual machines of the SharePoint farm in tiers on the appropriate subnets.</span></span>
  
<span data-ttu-id="fd374-220">**Рисунок 4. Размещение виртуальных машин SharePoint**</span><span class="sxs-lookup"><span data-stu-id="fd374-220">**Figure 4: Placement of SharePoint virtual machines**</span></span>

![Серверы баз данных и роли сервера SharePoint добавлены в виртуальную сеть Azure в подсети фермы SharePoint](media/AZarch-SPVMsinCloudSer.png)
  
<span data-ttu-id="fd374-222">В отличие от предыдущих схем, на этой схеме на соответствующие уровни добавлены роли серверов фермы SharePoint.</span><span class="sxs-lookup"><span data-stu-id="fd374-222">This diagram builds on the previous diagrams by adding the SharePoint farm server roles in their respective tiers.</span></span>
  
- <span data-ttu-id="fd374-223">Две виртуальные машины баз данных, на которых запущен SQL Server, образуют уровень баз данных.</span><span class="sxs-lookup"><span data-stu-id="fd374-223">Two database virtual machines running SQL Server create the database tier.</span></span>
    
- <span data-ttu-id="fd374-224">Две виртуальные машины, на которых запущен SharePoint Server 2013, на каждый из следующих уровней: серверы переднего плана, серверы распределенного кэша и тыловые серверы.</span><span class="sxs-lookup"><span data-stu-id="fd374-224">Two virtual machines running SharePoint Server 2013 for each of the following tiers: front end servers, distributed cache servers, and back end servers.</span></span>
    
## <a name="design-and-fine-tune-server-roles-for-availability-sets-and-fault-domains"></a><span data-ttu-id="fd374-225">Разработка и точная настройка ролей серверов для групп доступности и доменов сбоя</span><span class="sxs-lookup"><span data-stu-id="fd374-225">Design and fine tune server roles for availability sets and fault domains</span></span>

<span data-ttu-id="fd374-p126">Домен сбоя  это набор оборудования, на котором выполняются экземпляры ролей. Инфраструктура Azure может одновременно обновлять все виртуальные машины в одном домене сбоя. Тем не менее они могут одновременно отказать, так как используют одну стойку. Чтобы не размещать две виртуальные машины в одном домене сбоя, вы можете настроить их как группу доступности, тогда каждая виртуальная машина будет размещаться в отдельном домене сбоя. Если три виртуальные машины настроены как группа доступности, Azure гарантирует, что в одном домене сбоя размещается не больше двух виртуальных машин.</span><span class="sxs-lookup"><span data-stu-id="fd374-p126">A fault domain is a grouping of hardware in which role instances run. Virtual machines within the same fault domain can be updated by the Azure infrastructure at the same time. Or, they can fail at the same time because they share the same rack. To avoid the risk of having two virtual machines on the same fault domain, you can configure your virtual machines as an availability set, which ensures that each virtual machine is in a different fault domain. If three virtual machines are configured as an availability set, Azure guarantees that no more than two of the virtual machines are located in the same fault domain.</span></span>
  
<span data-ttu-id="fd374-p127">При разработке архитектуры Azure для фермы SharePoint настройте одинаковые роли серверов как группу доступности. Это обеспечит распределение виртуальных машин между несколькими доменами сбоя.</span><span class="sxs-lookup"><span data-stu-id="fd374-p127">When you design the Azure architecture for a SharePoint farm, configure identical server roles to be part of an availability set. This ensures that your virtual machines are spread across multiple fault domains.</span></span>
  
<span data-ttu-id="fd374-233">**Рисунок 5. Использование групп доступности Azure для обеспечения высокой доступности уровней фермы SharePoint**</span><span class="sxs-lookup"><span data-stu-id="fd374-233">**Figure 5: Use Azure Availability Sets to provide high availability for the SharePoint farm tiers**</span></span>

![Конфигурация групп доступности в инфраструктуре Azure для решения SharePoint 2013](media/AZenv-WinAzureAvailSetsHA.png)
  
<span data-ttu-id="fd374-p128">На этой схеме показана конфигурация групп доступности в инфраструктуре Azure. Перечисленные ниже роли используют отдельную группу доступности.</span><span class="sxs-lookup"><span data-stu-id="fd374-p128">This diagram calls out the configuration of availability sets within the Azure infrastructure. Each of the following roles share a separate availability set:</span></span>
  
- <span data-ttu-id="fd374-237">Active Directory и DNS</span><span class="sxs-lookup"><span data-stu-id="fd374-237">Active Directory and DNS</span></span>
    
- <span data-ttu-id="fd374-238">База данных</span><span class="sxs-lookup"><span data-stu-id="fd374-238">Database</span></span>
    
- <span data-ttu-id="fd374-239">Тыловой сервер</span><span class="sxs-lookup"><span data-stu-id="fd374-239">Back end</span></span>
    
- <span data-ttu-id="fd374-240">Сервер распределенного кэша</span><span class="sxs-lookup"><span data-stu-id="fd374-240">Distribute cache</span></span>
    
- <span data-ttu-id="fd374-241">Интерфейсный сервер</span><span class="sxs-lookup"><span data-stu-id="fd374-241">Front end</span></span>
    
<span data-ttu-id="fd374-p129">Может потребоваться точная настройка фермы SharePoint на платформе Azure. Чтобы обеспечить высокую доступность всех компонентов, убедитесь, что все роли серверов настроены одинаково.</span><span class="sxs-lookup"><span data-stu-id="fd374-p129">The SharePoint farm might need to be fine tuned in the Azure platform. To ensure high availability of all components, ensure that the server roles are all configured identically.</span></span>
  
<span data-ttu-id="fd374-p130">Ниже приводится пример стандартной архитектуры веб-сайтов, которая соответствует определенным требованиям к мощности и производительности. Этот пример представлен в модели [Архитектуры поиска на веб-сайтах для SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=261519).</span><span class="sxs-lookup"><span data-stu-id="fd374-p130">Here is an example that shows a standard Internet Sites architecture that meets specific capacity and performance goals. This example is featured in the following architecture model: [Internet Sites Search Architectures for SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=261519).</span></span>
  
<span data-ttu-id="fd374-246">**Рисунок 6. Пример планирования емкости и производительности в трехуровневой ферме**</span><span class="sxs-lookup"><span data-stu-id="fd374-246">**Figure 6: Planning example for capacity and performance goals in a three-tier farm**</span></span>

![Стандартная архитектура SharePoint 2013 Internet Sites с распределением компонентов, которое соответствует определенным требованиям к мощности и производительности](media/AZarch-CapPerfexmpArch.png)
  
<span data-ttu-id="fd374-248">На этой схеме:</span><span class="sxs-lookup"><span data-stu-id="fd374-248">In this diagram:</span></span>
  
- <span data-ttu-id="fd374-249">Представлена трехуровневая ферма: веб-серверы, серверы приложений и серверы баз данных;</span><span class="sxs-lookup"><span data-stu-id="fd374-249">A three-tier farm is represented: web servers, application servers, and database servers.</span></span>
    
- <span data-ttu-id="fd374-250">Три веб-сервера настроены одинаково с несколькими компонентами.</span><span class="sxs-lookup"><span data-stu-id="fd374-250">The three web servers are configured identically with multiple components.</span></span>
    
- <span data-ttu-id="fd374-251">Два сервера баз данных настроены одинаково.</span><span class="sxs-lookup"><span data-stu-id="fd374-251">The two database servers are configured identically.</span></span>
    
- <span data-ttu-id="fd374-p131">Три сервера приложений настроены по-разному. Эти роли серверов требуют точной настройки для групп доступности в Azure.</span><span class="sxs-lookup"><span data-stu-id="fd374-p131">The three application servers are not configured identically. These server roles require fine tuning for availability sets in Azure.</span></span>
    
<span data-ttu-id="fd374-254">Рассмотрим уровень серверов приложений подробнее.</span><span class="sxs-lookup"><span data-stu-id="fd374-254">Let's look closer at the application server tier.</span></span>
  
<span data-ttu-id="fd374-255">**Рисунок 7. Уровень серверов приложений перед точной настройкой**</span><span class="sxs-lookup"><span data-stu-id="fd374-255">**Figure 7: Application server tier before fine tuning**</span></span>

![Пример уровня серверов приложений SharePoint Server 2013 перед настройкой для групп доступности Microsoft Azure](media/AZarch-AppServtierBefore.png)
  
<span data-ttu-id="fd374-257">На этой схеме:</span><span class="sxs-lookup"><span data-stu-id="fd374-257">In this diagram:</span></span>
  
- <span data-ttu-id="fd374-258">уровень приложений включает три сервера;</span><span class="sxs-lookup"><span data-stu-id="fd374-258">Three servers are included in the application tier.</span></span>
    
- <span data-ttu-id="fd374-259">первый сервер включает четыре компонента;</span><span class="sxs-lookup"><span data-stu-id="fd374-259">The first server includes four components.</span></span>
    
- <span data-ttu-id="fd374-260">второй сервер включает три компонента;</span><span class="sxs-lookup"><span data-stu-id="fd374-260">The second server includes three components.</span></span>
    
- <span data-ttu-id="fd374-261">третий сервер включает два компонента.</span><span class="sxs-lookup"><span data-stu-id="fd374-261">The third server includes two components.</span></span>
    
<span data-ttu-id="fd374-p132">Количество компонентов определяется требованиями к производительности и емкости фермы. Чтобы адаптировать эту архитектуру для Azure, мы реплицируем четыре компонента на всех трех серверах. Таким образом, количество компонентов будет превышать необходимое. С другой стороны, такая схема обеспечивает высокую доступность всех четырех компонентов на платформе Azure, когда эти три виртуальные машины назначаются группе доступности.</span><span class="sxs-lookup"><span data-stu-id="fd374-p132">You determine the number of components by the performance and capacity targets for the farm. To adapt this architecture for Azure, we'll replicate the four components across all three servers. This increases the number of components beyond what is necessary for performance and capacity. The tradeoff is that this design ensures high availability of all four components in the Azure platform when these three virtual machines are assigned to an availability set.</span></span>
  
<span data-ttu-id="fd374-266">**Рисунок 8. Уровень серверов приложений после точной настройки**</span><span class="sxs-lookup"><span data-stu-id="fd374-266">**Figure 8: Application server tier after fine tuning**</span></span>

![Пример уровня серверов приложений SharePoint Server 2013 после настройки для групп доступности Microsoft Azure](media/AZarch-AppServtierAfter.png)
  
<span data-ttu-id="fd374-268">На этой схеме показаны все три сервера приложений, настроенных одинаково с одними и теми же четырьмя компонентами.</span><span class="sxs-lookup"><span data-stu-id="fd374-268">This diagram shows all three application servers configured identically with the same four components.</span></span>
  
<span data-ttu-id="fd374-269">После того как мы добавили к уровням фермы SharePoint группы доступности, этап реализации завершен.</span><span class="sxs-lookup"><span data-stu-id="fd374-269">When we add availability sets to the tiers of the SharePoint farm, the implementation is complete.</span></span>
  
<span data-ttu-id="fd374-270">**Рисунок 9. Готовая ферма SharePoint в службах инфраструктуры Azure**</span><span class="sxs-lookup"><span data-stu-id="fd374-270">**Figure 9: The completed SharePoint farm in Azure infrastructure services**</span></span>

![Пример фермы SharePoint 2013 в службах инфраструктуры Azure с виртуальной сетью, подключением между организациями, подсетями, виртуальными машинами и группами доступности](media/7256292f-bf11-485b-8917-41ba206153ee.png)
  
<span data-ttu-id="fd374-272">На этой схеме показана ферма SharePoint, реализованная в службах инфраструктуры Azure: группы доступности обеспечивают домены сбоя для серверов на каждом уровне.</span><span class="sxs-lookup"><span data-stu-id="fd374-272">This diagram shows the SharePoint farm implemented in Azure infrastructure services, with availability sets to provide fault domains for the servers in each tier.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="fd374-273">См. также</span><span class="sxs-lookup"><span data-stu-id="fd374-273">See Also</span></span>

[<span data-ttu-id="fd374-274">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="fd374-274">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="fd374-275">Веб-сайты в Microsoft Azure с использованием SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="fd374-275">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
  
[<span data-ttu-id="fd374-276">Аварийное восстановление SharePoint Server 2013 в Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="fd374-276">SharePoint Server 2013 Disaster Recovery in Microsoft Azure</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)


