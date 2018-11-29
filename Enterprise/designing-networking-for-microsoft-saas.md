---
title: Разработка сети для Microsoft SaaS
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
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872270"
---
# <a name="designing-networking-for-microsoft-saas"></a><span data-ttu-id="7efae-103">Разработка сети для Microsoft SaaS</span><span class="sxs-lookup"><span data-stu-id="7efae-103">Designing networking for Microsoft SaaS</span></span>

 <span data-ttu-id="7efae-104">**Сводка.** В этой статье рассказано, как оптимизировать сеть для доступа к службам SaaS корпорации Майкрософт, в том числе к Office 365, Microsoft Intune и Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="7efae-104">**Summary:** Understand how to optimize your network for access to Microsoft's SaaS services, including Office 365, Microsoft Intune, and Dynamics 365.</span></span>
  
<span data-ttu-id="7efae-105">Оптимизация сети для служб Microsoft SaaS требуется конфигурация внутренних и устройств пограничного сервера для маршрутизации различных категорий трафик к службам Microsoft SaaS.</span><span class="sxs-lookup"><span data-stu-id="7efae-105">Optimizing your network for Microsoft SaaS services requires the configuration of internal and edge devices to route the different categories of traffic to Microsoft SaaS services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a><span data-ttu-id="7efae-106">Действия по подготовке сети для служб Microsoft SaaS</span><span class="sxs-lookup"><span data-stu-id="7efae-106">Steps to prepare your network for Microsoft SaaS services</span></span>

<span data-ttu-id="7efae-107">Чтобы оптимизировать свою сеть для служб Microsoft SaaS, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="7efae-107">Follow these steps to optimize your network for Microsoft SaaS services:</span></span>
  
1. <span data-ttu-id="7efae-108">Выполните **действия по подготовке сети для облачных служб (Майкрософт)**, описанные в статье [Общие элементы подключения к облаку Майкрософт](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="7efae-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="7efae-109">Добавление подключения к Интернету для каждого из вашего офисов.</span><span class="sxs-lookup"><span data-stu-id="7efae-109">Add an Internet connection to each of your offices.</span></span>
    
3. <span data-ttu-id="7efae-110">Убедитесь, что поставщиком услуг Интернета для подключений к Интернету используют DNS-сервер с локальный IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="7efae-110">Ensure that the ISPs for all Internet connections use a DNS server with a local IP address.</span></span>
    
4. <span data-ttu-id="7efae-111">Изучите hairpins сети, промежуточные места назначения, такими как службы безопасности на основе облака и устранить их, если это возможно.</span><span class="sxs-lookup"><span data-stu-id="7efae-111">Examine your network hairpins, intermediate destinations such as cloud-based security services, and eliminate them if possible.</span></span>
    
5. <span data-ttu-id="7efae-112">Настройте устройство пограничного сервера для обхода обработки для оптимизации и разрешить категорий Microsoft SaaS трафика.</span><span class="sxs-lookup"><span data-stu-id="7efae-112">Configure your edge devices to bypass processing for the Optimize and Allow categories of Microsoft SaaS traffic.</span></span>

## <a name="optimizing-traffic-to-microsofts-saas-services"></a><span data-ttu-id="7efae-113">Оптимизация трафик к службам SaaS корпорации Майкрософт</span><span class="sxs-lookup"><span data-stu-id="7efae-113">Optimizing traffic to Microsoft’s SaaS services</span></span>    

<span data-ttu-id="7efae-114">Существует три категории Microsoft SaaS трафика:</span><span class="sxs-lookup"><span data-stu-id="7efae-114">There are three categories of Microsoft SaaS traffic:</span></span>

- <span data-ttu-id="7efae-115">Оптимизация</span><span class="sxs-lookup"><span data-stu-id="7efae-115">Optimize</span></span>

  <span data-ttu-id="7efae-116">Требуется для подключения к каждому службы Microsoft SaaS и представляют собой более 75% пропускной способности Microsoft SaaS, подключений и данных.</span><span class="sxs-lookup"><span data-stu-id="7efae-116">Required for connectivity to every Microsoft SaaS service and represent over 75% of Microsoft SaaS bandwidth, connections, and volume of data.</span></span>

- <span data-ttu-id="7efae-117">Разрешить</span><span class="sxs-lookup"><span data-stu-id="7efae-117">Allow</span></span>

  <span data-ttu-id="7efae-118">Требуется для подключения к определенным Microsoft SaaS служб и функций, но не как зависит от производительности сети и задержка, которые в категории, оптимизировать.</span><span class="sxs-lookup"><span data-stu-id="7efae-118">Required for connectivity to specific Microsoft SaaS services and features but are not as sensitive to network performance and latency as those in the Optimize category.</span></span>

- <span data-ttu-id="7efae-119">По умолчанию</span><span class="sxs-lookup"><span data-stu-id="7efae-119">Default</span></span>

  <span data-ttu-id="7efae-p101">Представляют службы Microsoft SaaS и зависимостей, не требующие любого оптимизации. Вы можете работать трафика категории по умолчанию как обычный трафика из Интернета.</span><span class="sxs-lookup"><span data-stu-id="7efae-p101">Represent Microsoft SaaS services and dependencies that do not require any optimization. You can treat Default category traffic like normal Internet traffic.</span></span>


<span data-ttu-id="7efae-122">**На рисунке 1: Рекомендуемая конфигурация для трафика Microsoft SaaS всех офисов**</span><span class="sxs-lookup"><span data-stu-id="7efae-122">**Figure 1: Recommended configuration for Microsoft SaaS traffic for all offices**</span></span>

![На рисунке 1: Рекомендуемая конфигурация для трафика Microsoft SaaS всех офисов](media/Network-Poster/SaaS1.png)

<span data-ttu-id="7efae-124">На рисунке 1 показаны рекомендуемые конфигурации всех офисов, включая офисы и региональных или центра из них, в котором:</span><span class="sxs-lookup"><span data-stu-id="7efae-124">Figure 1 shows the recommended configuration of all offices, including branch offices and regional or central ones, in which:</span></span>

- <span data-ttu-id="7efae-125">Категории **по умолчанию** и общие Интернет-трафик перенаправляется в офисов, имеющих прокси-серверы и другие устройства пограничного сервера для обеспечения защиты от угроз безопасности на основе Интернета.</span><span class="sxs-lookup"><span data-stu-id="7efae-125">**Default** category and general Internet traffic is routed to offices that have proxy servers and other edge devices to provide protection against Internet-based security risks.</span></span>
- <span data-ttu-id="7efae-126">**Оптимизировать** и **Разрешить** категории трафик перенаправляется непосредственно в пограничной сети Microsoft на сервере переднего плана ближайшем office, содержащий подключающегося пользователя, обход прокси-серверы и другие устройства, пограничного сервера.</span><span class="sxs-lookup"><span data-stu-id="7efae-126">**Optimize** and **Allow** category traffic is forwarded directly to the edge of the Microsoft network front end nearest to the office containing the connecting user, bypassing proxy servers and other edge devices.</span></span>

<span data-ttu-id="7efae-127">Программно конфигурируемой широкий сеть (глобальная сеть SD) устройств в филиалах разделить трафик, чтобы:</span><span class="sxs-lookup"><span data-stu-id="7efae-127">Software-defined wide area network (SD-WAN) devices in branch offices separate traffic so that:</span></span> 

- <span data-ttu-id="7efae-128">Категории **по умолчанию** и общие Интернет-трафик переходит к центра или региональных office по глобальной сети магистрали.</span><span class="sxs-lookup"><span data-stu-id="7efae-128">**Default** category and general Internet traffic goes to a central or regional office over the WAN backbone.</span></span> 
- <span data-ttu-id="7efae-129">**Оптимизировать** и **Разрешить** категории трафик проходит с поставщиком услуг Интернета, предоставляя локального подключение к Интернету.</span><span class="sxs-lookup"><span data-stu-id="7efae-129">**Optimize** and **Allow** category traffic goes to the ISP providing the local Internet connection.</span></span>
  
<span data-ttu-id="7efae-130">Дополнительные сведения см. в статьях:</span><span class="sxs-lookup"><span data-stu-id="7efae-130">For more information, see:</span></span>
  
- [<span data-ttu-id="7efae-131">Принципы подключения к сети</span><span class="sxs-lookup"><span data-stu-id="7efae-131">Network connectivity principles</span></span>](https://aka.ms/expressrouteoffice365)

- [<span data-ttu-id="7efae-132">Планирование сети и миграции в Office 365</span><span class="sxs-lookup"><span data-stu-id="7efae-132">Network and migration planning for Office 365</span></span>](https://aka.ms/tune)
    
## <a name="next-step"></a><span data-ttu-id="7efae-133">Следующее действие</span><span class="sxs-lookup"><span data-stu-id="7efae-133">Next step</span></span>

[<span data-ttu-id="7efae-134">Проектирование сети для Microsoft Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="7efae-134">Designing networking for Microsoft Azure PaaS</span></span>](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a><span data-ttu-id="7efae-135">См. также</span><span class="sxs-lookup"><span data-stu-id="7efae-135">See also</span></span>

[<span data-ttu-id="7efae-136">Организация сети в Microsoft Cloud для корпоративных архитекторов</span><span class="sxs-lookup"><span data-stu-id="7efae-136">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="7efae-137">Материалы по архитектуре Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="7efae-137">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

