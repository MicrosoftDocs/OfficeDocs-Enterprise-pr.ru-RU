---
title: "Разработка сети для Microsoft Azure PaaS"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 19568184-705b-493b-b713-b484367adba9
description: "Сводка: в этой статье рассказывается о том, как оптимизировать сеть для доступа к Microsoft Azure PaaS."
ms.openlocfilehash: 8ea344b5c18f9224b1a939a05c6e5a4eda2eeec5
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/11/2018
---
# <a name="designing-networking-for-microsoft-azure-paas"></a><span data-ttu-id="6a61e-103">Разработка сети для Microsoft Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="6a61e-103">Designing networking for Microsoft Azure PaaS</span></span>

 <span data-ttu-id="6a61e-104">**Сводка:** в этой статье рассказывается о том, как оптимизировать сеть для доступа к Microsoft Azure PaaS.</span><span class="sxs-lookup"><span data-stu-id="6a61e-104">**Summary:** Understand how to optimize your network for access to Microsoft Azure PaaS.</span></span>
  
<span data-ttu-id="6a61e-105">Оптимизация сетей для работы с приложениями Azure PaaS требует соответствующей пропускной способности подключения к Интернету и распределения сетевого трафика по нескольким сайтам или приложениям (при необходимости).</span><span class="sxs-lookup"><span data-stu-id="6a61e-105">Optimizing networking for Azure PaaS apps requires adequate Internet bandwidth and can require the distribution of network traffic across multiple sites or apps.</span></span>
  
## <a name="planning-steps-for-hosting-organization-paas-applications-in-azure"></a><span data-ttu-id="6a61e-106">Планирование действий по размещению приложений PaaS организации в Azure</span><span class="sxs-lookup"><span data-stu-id="6a61e-106">Planning steps for hosting organization PaaS applications in Azure</span></span>

<span data-ttu-id="6a61e-107">Вставьте сюда основную часть.</span><span class="sxs-lookup"><span data-stu-id="6a61e-107">Insert section body here.</span></span>
  
1. <span data-ttu-id="6a61e-108">Выполните **действия по подготовке сети для облачных служб (Майкрософт)**, описанные в статье [Общие элементы подключения к облаку Майкрософт](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="6a61e-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="6a61e-109">Оптимизируйте скорость интернет-соединения, выполнив действия 2–4 из раздела **Действия по подготовке сети для служб Microsoft SaaS** статьи [Проектирование сети для Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span><span class="sxs-lookup"><span data-stu-id="6a61e-109">Optimize your Internet bandwidth using steps 2 - 4 of the **Steps to prepare your network for Microsoft SaaS services** section in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span></span>
    
3. <span data-ttu-id="6a61e-110">Определите, нужно ли создавать подключение ExpressRoute к Azure.</span><span class="sxs-lookup"><span data-stu-id="6a61e-110">Determine whether you need an ExpressRoute connection to Azure.</span></span>
    
4. <span data-ttu-id="6a61e-111">Определите, необходим ли для рабочих веб-нагрузок шлюз приложений Azure.</span><span class="sxs-lookup"><span data-stu-id="6a61e-111">For web-based workloads, determine whether you need the Azure Application Gateway.</span></span>
    
5. <span data-ttu-id="6a61e-112">Определите, необходим ли вам диспетчер трафика Azure для распределения трафика в различные конечные точки.</span><span class="sxs-lookup"><span data-stu-id="6a61e-112">For distribution of traffic to different endpoints in different data centers, determine whether you need Azure Traffic Manager.</span></span>
    
## <a name="internet-bandwidth-for-organization-paas-applications"></a><span data-ttu-id="6a61e-113">Полоса пропускания подключения к Интернету для приложений PaaS организации</span><span class="sxs-lookup"><span data-stu-id="6a61e-113">Internet bandwidth for organization PaaS applications</span></span>

<span data-ttu-id="6a61e-p101">Для работы пользователей, находящихся в интрасети, с приложениями организации, размещенными в Azure PaaS, требуется определенная часть полосы пропускания подключения к Интернету. Вы можете использовать два указанных ниже варианта.</span><span class="sxs-lookup"><span data-stu-id="6a61e-p101">Organization applications hosted in Azure PaaS require Internet bandwidth for intranet users. There are two options:</span></span>
  
- <span data-ttu-id="6a61e-p102">**Вариант 1:** использование существующего канала, оптимизированного для интернет-трафика и способного справиться с пиковыми нагрузками. Сведения о подключении к Интернету, использовании клиентов и ИТ-операциях см. в статье[Разработка сети для Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span><span class="sxs-lookup"><span data-stu-id="6a61e-p102">**Option 1:** Use your existing pipe, optimized for Internet traffic with the capacity to handle peak loads. See[Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md) for Internet edge, client usage, and IT operations considerations.</span></span>
    
- <span data-ttu-id="6a61e-118">**Вариант 2:** использование подключения ExpressRoute к Azure для задач, требующих широкой полосы пропускания или малых задержек.</span><span class="sxs-lookup"><span data-stu-id="6a61e-118">**Option 2:** For high-bandwidth or low latency needs, use an ExpressRoute connection to Azure.</span></span>
    
<span data-ttu-id="6a61e-119">**Рис. 1. Варианты подключения к службам Azure PaaS**</span><span class="sxs-lookup"><span data-stu-id="6a61e-119">**Figure 1: Connection options for connecting the Azure PaaS services**</span></span>

![Рис. 1. Варианты подключения к службам Azure PaaS](images/Network_Poster/PaaS1.png)
  
<span data-ttu-id="6a61e-121">На рис. 1 показано подключение локальной сети к службам Azure PaaS через интернет-канал или ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="6a61e-121">Figure 1 shows an on-premises network connecting to Azure PaaS services over an Internet pipe or ExpressRoute.</span></span>
  
## <a name="azure-application-gateway"></a><span data-ttu-id="6a61e-122">Шлюз приложений Azure</span><span class="sxs-lookup"><span data-stu-id="6a61e-122">Azure Application Gateway</span></span>

<span data-ttu-id="6a61e-123">Службы маршрутизации и балансировки нагрузки уровня приложений, позволяющие создавать масштабируемый внешний веб-интерфейс с высоким уровнем доступности в Azure для веб-приложений, облачных служб и виртуальных машин.</span><span class="sxs-lookup"><span data-stu-id="6a61e-123">Application-level routing and load balancing services that let you build a scalable and highly-available web front end in Azure for web apps, cloud services, and virtual machines.</span></span> 
  
<span data-ttu-id="6a61e-124">**Рис. 2. Шлюз приложений Azure**</span><span class="sxs-lookup"><span data-stu-id="6a61e-124">**Figure 2: Azure Application Gateway**</span></span>

![Рис. 2. Служба шлюза приложений Azure](images/Network_Poster/PaaS2.png)
  
<span data-ttu-id="6a61e-126">На рис. 2 показан шлюз приложений Azure и способы маршрутизации запросов пользователей из Интернета в веб-приложения, облачные службы или виртуальные машины Azure.</span><span class="sxs-lookup"><span data-stu-id="6a61e-126">Figure 2 shows the Azure Application Gateway and how user requests from the Internet can be routed to Azure web apps, cloud services, or virtual machines.</span></span>
  
<span data-ttu-id="6a61e-127">На данный момент шлюз приложений поддерживает доставку приложений уровня 7 для следующих задач:</span><span class="sxs-lookup"><span data-stu-id="6a61e-127">Application Gateway currently supports layer 7 application delivery for the following:</span></span>
  
- <span data-ttu-id="6a61e-128">балансировка нагрузки HTTP;</span><span class="sxs-lookup"><span data-stu-id="6a61e-128">HTTP load balancing</span></span>
    
- <span data-ttu-id="6a61e-129">сходство сеансов на основе файлов cookie;</span><span class="sxs-lookup"><span data-stu-id="6a61e-129">Cookie-based session affinity</span></span>
    
- <span data-ttu-id="6a61e-130">разгрузка SSL.</span><span class="sxs-lookup"><span data-stu-id="6a61e-130">SSL offload</span></span>
    
<span data-ttu-id="6a61e-131">Дополнительные сведения см. в статье [Обзор шлюза приложений](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction).</span><span class="sxs-lookup"><span data-stu-id="6a61e-131">For more information, see [Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction).</span></span>
  
## <a name="azure-traffic-manager"></a><span data-ttu-id="6a61e-132">Диспетчер трафика Azure</span><span class="sxs-lookup"><span data-stu-id="6a61e-132">Azure Traffic Manager</span></span>

<span data-ttu-id="6a61e-133">Распределение трафика по различным конечным точкам, включающим облачные службы или веб-приложения Azure, расположенные в разных центрах обработки данных или внешних конечных точках.</span><span class="sxs-lookup"><span data-stu-id="6a61e-133">Distribution of traffic to different endpoints, which can include cloud services or Azure web apps located in different data centers or external endpoints.</span></span>
  
<span data-ttu-id="6a61e-134">Диспетчер трафика использует указанные ниже методы маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="6a61e-134">Traffic Manager uses the following routing methods:</span></span>
  
- <span data-ttu-id="6a61e-135">**Отработка отказа:** конечные точки размещены в одном или нескольких центрах обработки данных Azure, и вы хотите использовать первичную конечную точку для всего трафика, но при этом вам необходимо обеспечить резерв на случай, если первичная или резервные конечные точки станут недоступными.</span><span class="sxs-lookup"><span data-stu-id="6a61e-135">**Failover:** The endpoints are in the same or different Azure datacenters and you want to use a primary endpoint for all traffic, but provide backups in case the primary or the backup endpoints are unavailable.</span></span>
    
- <span data-ttu-id="6a61e-136">**Циклический перебор:** вы хотите распределять нагрузку среди определенного количества конечных точек, расположенных в одном или нескольких центрах обработки данных.</span><span class="sxs-lookup"><span data-stu-id="6a61e-136">**Round robin:** You want to distribute load across a set of endpoints in the same datacenter or across different datacenters.</span></span>
    
- <span data-ttu-id="6a61e-137">**Эффективность:** у вас имеются конечные точки в различных географических расположениях и вы хотите, чтобы клиенты, отправляющие запросы, использовали "ближайшую" конечную точку с точки зрения минимальных задержек.</span><span class="sxs-lookup"><span data-stu-id="6a61e-137">**Performance:** You have endpoints in different geographic locations and you want requesting clients to use the "closest" endpoint in terms of the lowest latency.</span></span>
    
<span data-ttu-id="6a61e-138">Ниже показан пример трех географически распределенных веб-приложений.</span><span class="sxs-lookup"><span data-stu-id="6a61e-138">Here is an example for three geographically-distributed web apps.</span></span>
  
<span data-ttu-id="6a61e-139">**Рис. 3. Диспетчер трафика Azure**</span><span class="sxs-lookup"><span data-stu-id="6a61e-139">**Figure 3: Azure Traffic Manager**</span></span>

![Рис. 3. Диспетчер трафика Azure](images/Network_Poster/PaaS3.png)
  
<span data-ttu-id="6a61e-p103">На рис. 3 показан основной процесс, который диспетчер трафика использует для маршрутизации запросов в три различных веб-приложения Azure в США, Европе и Азии. В этом примере происходит указанный ниже процесс.</span><span class="sxs-lookup"><span data-stu-id="6a61e-p103">Figure 3 shows the basic process that Traffic Manager uses to route requests to three different Azure web apps in United States, Europe, and Asia. In the example:</span></span>
  
1. <span data-ttu-id="6a61e-143">Запрос DNS пользователя на URL-адрес веб-сайта направляется в диспетчер трафика Azure, который возвращает имя регионального веб-приложения на основе метода эффективной маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="6a61e-143">A user DNS query for a web site URL gets directed to Azure Traffic Manager, which returns the name of a regional web app, based on the performance routing method.</span></span>
    
2. <span data-ttu-id="6a61e-144">Пользователь инициирует трафик к региональному веб-приложению в Европе.</span><span class="sxs-lookup"><span data-stu-id="6a61e-144">The user initiates traffic with the regional web app in Europe.</span></span>
    
<span data-ttu-id="6a61e-145">Дополнительные сведения см. в статье [Что такое диспетчер трафика](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span><span class="sxs-lookup"><span data-stu-id="6a61e-145">For more information, see [Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6a61e-146">См. также</span><span class="sxs-lookup"><span data-stu-id="6a61e-146">See Also</span></span>

[<span data-ttu-id="6a61e-147">Облачные сети Майкрософт для корпоративных архитекторов</span><span class="sxs-lookup"><span data-stu-id="6a61e-147">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="6a61e-148">Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="6a61e-148">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

<span data-ttu-id="6a61e-149">[Стратегия Enterprise Cloud корпорации Майкрософт: ресурсы для лиц, принимающих решения в области ИТ](https://sway.com/FJ2xsyWtkJc2taRD)</span><span class="sxs-lookup"><span data-stu-id="6a61e-149">[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://sway.com/FJ2xsyWtkJc2taRD)</span></span>



