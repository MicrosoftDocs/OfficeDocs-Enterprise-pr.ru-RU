---
title: Разработка сети для Microsoft SaaS
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: Сводка. В этой статье рассказано, как оптимизировать сеть для доступа к службам SaaS корпорации Майкрософт, в том числе к Office 365, Microsoft Intune и Dynamics 365.
ms.openlocfilehash: 3d47c53de1bc1121ef72eb519c51c0ad9423fff9
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487304"
---
# <a name="designing-networking-for-microsoft-saas"></a><span data-ttu-id="5e44f-103">Разработка сети для Microsoft SaaS</span><span class="sxs-lookup"><span data-stu-id="5e44f-103">Designing networking for Microsoft SaaS</span></span>

 <span data-ttu-id="5e44f-104">**Сводка.** В этой статье рассказано, как оптимизировать сеть для доступа к службам SaaS корпорации Майкрософт, в том числе к Office 365, Microsoft Intune и Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="5e44f-104">**Summary:** Understand how to optimize your network for access to Microsoft's SaaS services, including Office 365, Microsoft Intune, and Dynamics 365.</span></span>
  
<span data-ttu-id="5e44f-105">Оптимизации сети для служб Microsoft SaaS требует настройки внутренних и пограничных устройств для маршрутизации различных категорий трафика в службы Microsoft SaaS.</span><span class="sxs-lookup"><span data-stu-id="5e44f-105">Optimizing your network for Microsoft SaaS services requires the configuration of internal and edge devices to route the different categories of traffic to Microsoft SaaS services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a><span data-ttu-id="5e44f-106">Действия по подготовке сети для служб Microsoft SaaS</span><span class="sxs-lookup"><span data-stu-id="5e44f-106">Steps to prepare your network for Microsoft SaaS services</span></span>

<span data-ttu-id="5e44f-107">Чтобы оптимизировать свою сеть для служб Microsoft SaaS, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="5e44f-107">Follow these steps to optimize your network for Microsoft SaaS services:</span></span>
  
1. <span data-ttu-id="5e44f-108">Выполните **действия по подготовке сети для облачных служб (Майкрософт)**, описанные в статье [Общие элементы подключения к облаку Майкрософт](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="5e44f-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="5e44f-109">Добавьте подключение к Интернету для каждого из Ваших офисов.</span><span class="sxs-lookup"><span data-stu-id="5e44f-109">Add an Internet connection to each of your offices.</span></span>
    
3. <span data-ttu-id="5e44f-110">Убедитесь, что поставщики услуг Интернета для всех подключений к Интернету используют DNS-сервер с локальным IP-адресом.</span><span class="sxs-lookup"><span data-stu-id="5e44f-110">Ensure that the ISPs for all Internet connections use a DNS server with a local IP address.</span></span>
    
4. <span data-ttu-id="5e44f-111">Проверьте сетевые развороты, промежуточные назначения, такие как облачные службы безопасности, и устраните их, если это возможно.</span><span class="sxs-lookup"><span data-stu-id="5e44f-111">Examine your network hairpins, intermediate destinations such as cloud-based security services, and eliminate them if possible.</span></span>
    
5. <span data-ttu-id="5e44f-112">Настройка пограничных устройств для обхода обработки в категориях "оптимизировать" и "разрешить" для трафика Microsoft SaaS.</span><span class="sxs-lookup"><span data-stu-id="5e44f-112">Configure your edge devices to bypass processing for the Optimize and Allow categories of Microsoft SaaS traffic.</span></span>

## <a name="optimizing-traffic-to-microsofts-saas-services"></a><span data-ttu-id="5e44f-113">Оптимизация трафика в службах SaaS корпорации Майкрософт</span><span class="sxs-lookup"><span data-stu-id="5e44f-113">Optimizing traffic to Microsoft’s SaaS services</span></span>    

<span data-ttu-id="5e44f-114">Существует три категории трафика Microsoft SaaS:</span><span class="sxs-lookup"><span data-stu-id="5e44f-114">There are three categories of Microsoft SaaS traffic:</span></span>

- <span data-ttu-id="5e44f-115">Оптимизация</span><span class="sxs-lookup"><span data-stu-id="5e44f-115">Optimize</span></span>

  <span data-ttu-id="5e44f-116">Требуется для подключения к каждой службе Microsoft SaaS и представления пропускной способности Microsoft SaaS, подключений и объема данных за 75%.</span><span class="sxs-lookup"><span data-stu-id="5e44f-116">Required for connectivity to every Microsoft SaaS service and represent over 75% of Microsoft SaaS bandwidth, connections, and volume of data.</span></span>

- <span data-ttu-id="5e44f-117">Разрешить</span><span class="sxs-lookup"><span data-stu-id="5e44f-117">Allow</span></span>

  <span data-ttu-id="5e44f-118">Требуется для подключения к определенным службам и функциям Microsoft SaaS, но не зависит от производительности сети и задержки, как в категории оптимизация.</span><span class="sxs-lookup"><span data-stu-id="5e44f-118">Required for connectivity to specific Microsoft SaaS services and features but are not as sensitive to network performance and latency as those in the Optimize category.</span></span>

- <span data-ttu-id="5e44f-119">По умолчанию</span><span class="sxs-lookup"><span data-stu-id="5e44f-119">Default</span></span>

  <span data-ttu-id="5e44f-120">Представляет службы Microsoft SaaS и зависимости, для которых не требуется оптимизация.</span><span class="sxs-lookup"><span data-stu-id="5e44f-120">Represent Microsoft SaaS services and dependencies that do not require any optimization.</span></span> <span data-ttu-id="5e44f-121">Вы можете обрабатывать трафик категории по умолчанию, например обычный Интернет.</span><span class="sxs-lookup"><span data-stu-id="5e44f-121">You can treat Default category traffic like normal Internet traffic.</span></span>


<span data-ttu-id="5e44f-122">**Рисунок 1: Рекомендуемая конфигурация для трафика Microsoft SaaS для всех офисов**</span><span class="sxs-lookup"><span data-stu-id="5e44f-122">**Figure 1: Recommended configuration for Microsoft SaaS traffic for all offices**</span></span>

![Рисунок 1: Рекомендуемая конфигурация для трафика Microsoft SaaS для всех офисов](media/Network-Poster/SaaS1.png)

<span data-ttu-id="5e44f-124">На рисунке 1 показана Рекомендуемая конфигурация всех офисов, включая офисы филиалов и региональные или центральные, в том числе:</span><span class="sxs-lookup"><span data-stu-id="5e44f-124">Figure 1 shows the recommended configuration of all offices, including branch offices and regional or central ones, in which:</span></span>

- <span data-ttu-id="5e44f-125">Категория **по умолчанию** и общий Интернет-трафик направляются в офисы, у которых есть прокси-серверы и другие пограничные устройства для обеспечения защиты от угроз безопасности на основе Интернета.</span><span class="sxs-lookup"><span data-stu-id="5e44f-125">**Default** category and general Internet traffic is routed to offices that have proxy servers and other edge devices to provide protection against Internet-based security risks.</span></span>
- <span data-ttu-id="5e44f-126">**Оптимизация** и **разрешение** трафика категории пересылается непосредственно на край Microsoft Network переднего плана, ближайший к Office, содержащему подключающегося пользователя, обход прокси-серверов и других пограничных устройств.</span><span class="sxs-lookup"><span data-stu-id="5e44f-126">**Optimize** and **Allow** category traffic is forwarded directly to the edge of the Microsoft network front end nearest to the office containing the connecting user, bypassing proxy servers and other edge devices.</span></span>

<span data-ttu-id="5e44f-127">Определенные программным обеспечением устройства с подключением по протоколу SD в офисах филиалов разделяют трафик таким образом, чтобы:</span><span class="sxs-lookup"><span data-stu-id="5e44f-127">Software-defined wide area network (SD-WAN) devices in branch offices separate traffic so that:</span></span> 

- <span data-ttu-id="5e44f-128">Категория **по умолчанию** и общий трафик в Интернете переносятся в Центральный или региональный офис по магистрали WAN.</span><span class="sxs-lookup"><span data-stu-id="5e44f-128">**Default** category and general Internet traffic goes to a central or regional office over the WAN backbone.</span></span> 
- <span data-ttu-id="5e44f-129">**Оптимизировать** и **разрешать** трафик категорий переДАЕТСЯ поставщику услуг Интернета, который предоставляет локальное подключение к Интернету.</span><span class="sxs-lookup"><span data-stu-id="5e44f-129">**Optimize** and **Allow** category traffic goes to the ISP providing the local Internet connection.</span></span>
  
<span data-ttu-id="5e44f-130">Дополнительные сведения см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="5e44f-130">For more information, see:</span></span>
  
- [<span data-ttu-id="5e44f-131">Принципы сетевого подключения</span><span class="sxs-lookup"><span data-stu-id="5e44f-131">Network connectivity principles</span></span>](https://aka.ms/expressrouteoffice365)

- [<span data-ttu-id="5e44f-132">Планирование сети и миграции в Office 365</span><span class="sxs-lookup"><span data-stu-id="5e44f-132">Network and migration planning for Office 365</span></span>](https://aka.ms/tune)
    
## <a name="next-step"></a><span data-ttu-id="5e44f-133">Следующее действие</span><span class="sxs-lookup"><span data-stu-id="5e44f-133">Next step</span></span>

[<span data-ttu-id="5e44f-134">Проектирование сети для Microsoft Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="5e44f-134">Designing networking for Microsoft Azure PaaS</span></span>](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a><span data-ttu-id="5e44f-135">См. также</span><span class="sxs-lookup"><span data-stu-id="5e44f-135">See also</span></span>

[<span data-ttu-id="5e44f-136">Организация сети в Microsoft Cloud для корпоративных архитекторов</span><span class="sxs-lookup"><span data-stu-id="5e44f-136">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="5e44f-137">Ресурсы, посвященные ИТ-архитектуре Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="5e44f-137">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

