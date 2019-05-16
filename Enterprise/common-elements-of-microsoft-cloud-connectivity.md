---
title: Общие элементы облачного подключения Майкрософт
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 061d4507-7360-4029-8f4b-3d4bc6b4ade0
description: Сводка. Об общих элементах сетевой инфраструктуры и подготовке сети.
ms.openlocfilehash: f092e3fb0a2f009aa7c6bbb14229fe98b35700ea
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068115"
---
# <a name="common-elements-of-microsoft-cloud-connectivity"></a><span data-ttu-id="7f694-103">Общие элементы подключения к Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="7f694-103">Common elements of Microsoft cloud connectivity</span></span>

 <span data-ttu-id="7f694-104">**Сводка.** Об общих элементах сетевой инфраструктуры и подготовке сети.</span><span class="sxs-lookup"><span data-stu-id="7f694-104">**Summary:** Understand the common elements of networking infrastructure and how to prepare your network.</span></span>
  
<span data-ttu-id="7f694-105">Интеграция вашей сети с Microsoft Cloud обеспечивает оптимальный доступ к широкому спектру служб.</span><span class="sxs-lookup"><span data-stu-id="7f694-105">Integrating your networking with the Microsoft cloud provides optimal access to a broad range of services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-cloud-services"></a><span data-ttu-id="7f694-106">Действия по подготовке сети для служб Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="7f694-106">Steps to prepare your network for Microsoft cloud services</span></span>
<span data-ttu-id="7f694-107"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="7f694-107"></span></span>

<span data-ttu-id="7f694-108">Для локальной сети:</span><span class="sxs-lookup"><span data-stu-id="7f694-108">For your on-premises network:</span></span>
  
1. <span data-ttu-id="7f694-109">проанализируйте имеющиеся у вас клиентские компьютеры и оптимизируйте сетевое оборудование, программные драйверы, параметры протоколов и веб-браузеры;</span><span class="sxs-lookup"><span data-stu-id="7f694-109">Analyze your client computers and optimize for network hardware, software drivers, protocol settings, and Internet browsers.</span></span>
    
2. <span data-ttu-id="7f694-110">проанализируйте локальную сеть на предмет задержек трафика и оптимальной маршрутизации до пограничного устройства Интернета;</span><span class="sxs-lookup"><span data-stu-id="7f694-110">Analyze your on-premises network for traffic latency and optimal routing to the Internet edge device.</span></span>
    
3. <span data-ttu-id="7f694-111">проанализируйте производительность пограничного устройства Интернета и оптимизируйте ее для повышенных значений интенсивности трафика.</span><span class="sxs-lookup"><span data-stu-id="7f694-111">Analyze the capacity and performance of your Internet edge device and optimize for higher levels of traffic.</span></span>
    
<span data-ttu-id="7f694-112">Для подключения к Интернету:</span><span class="sxs-lookup"><span data-stu-id="7f694-112">For your Internet connection:</span></span>
  
1. <span data-ttu-id="7f694-113">проанализируйте задержку между пограничным устройством Интернета (например, внешним брандмауэром) и региональными расположениями службы Microsoft Cloud, к которой вы подключаетесь;</span><span class="sxs-lookup"><span data-stu-id="7f694-113">Analyze the latency between your Internet edge device (such as your external firewall) and the regional locations of the Microsoft cloud service to which you are connecting.</span></span>
    
2. <span data-ttu-id="7f694-p101">проанализируйте пропускную способность и степень использования вашего текущего подключения к Интернету и при необходимости увеличьте пропускную способность. В качестве альтернативы вы можете добавить подключение ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="7f694-p101">Analyze the capacity and utilization of your current Internet connection and add capacity if needed. Alternately, add an ExpressRoute connection.</span></span>
    
## <a name="microsoft-cloud-connectivity-options"></a><span data-ttu-id="7f694-116">Варианты подключения к Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="7f694-116">Microsoft cloud connectivity options</span></span>
<span data-ttu-id="7f694-117"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="7f694-117"></span></span>

<span data-ttu-id="7f694-118">Используйте существующий интернет-канал или подключение ExpressRoute к Office 365, Azure и Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="7f694-118">Use your existing Internet pipe or an ExpressRoute connection to Office 365, Azure, and Dynamics 365.</span></span>
  
<span data-ttu-id="7f694-119">**Рис. 1. Варианты подключения к Microsoft Cloud**</span><span class="sxs-lookup"><span data-stu-id="7f694-119">**Figure 1: Options for Microsoft cloud connectivity**</span></span>

![Рис. 1. Варианты подключения к Microsoft Cloud](media/Network-Poster/CommonElements.png)

  
<span data-ttu-id="7f694-p102">На рис. 1 показано, как подключить локальную сеть к Microsoft Cloud, используя существующий интернет-канал или подключение ExpressRoute. Интернет-канал представляет зону DMZ и может содержать указанные ниже компоненты.</span><span class="sxs-lookup"><span data-stu-id="7f694-p102">Figure 1 shows how an on-premises network can be connected to Microsoft cloud offerings using their existing Internet pipe or ExpressRoute. The Internet pipe represents a DMZ and can have the following components:</span></span>
  
- <span data-ttu-id="7f694-p103">**Брандмауэр Интернета:** барьер между надежной и ненадежной сетями. Выполняет фильтрацию (на основе правил) и мониторинг трафика.</span><span class="sxs-lookup"><span data-stu-id="7f694-p103">**Internal firewall:** A barrier between your trusted network and an untrusted one. Performs traffic filtering (based on rules) and monitoring.</span></span>
    
- <span data-ttu-id="7f694-125">**Внешняя рабочая нагрузка:** веб-сайты или другие рабочие нагрузки, доступные для внешних пользователей в Интернете.</span><span class="sxs-lookup"><span data-stu-id="7f694-125">**External workload:** Web sites or other workloads made available to external users on the Internet.</span></span>
    
- <span data-ttu-id="7f694-126">**Прокси-сервер:** Службы запрашивают веб-контент от имени пользователей интрасети.</span><span class="sxs-lookup"><span data-stu-id="7f694-126">**Proxy server:** Services requests for web content on behalf of intranet users.</span></span> <span data-ttu-id="7f694-127">Обратный прокси-сервер разрешает незапрошенные входящие запросы.</span><span class="sxs-lookup"><span data-stu-id="7f694-127">A reverse proxy permits unsolicited inbound requests.</span></span>
    
- <span data-ttu-id="7f694-128">**Внешний брандмауэр:** Разрешает исходящий трафик и заданный входящий трафик.</span><span class="sxs-lookup"><span data-stu-id="7f694-128">**External firewall:** Allows outbound traffic and specified inbound traffic.</span></span> <span data-ttu-id="7f694-129">Позволяет выполнять преобразование адресов, проверку пакетов, а также проверку и перехвата SSL, а также защиту от потери данных.</span><span class="sxs-lookup"><span data-stu-id="7f694-129">Can perform address translation, packet inspection, SSL Break and Inspect, or data loss prevention.</span></span>
    
- <span data-ttu-id="7f694-130">**Подключение глобальной сети к поставщику услуг Интернета.** Обеспечиваемое оператором подключение к поставщику услуг Интернета, который осуществляет подключение к Интернету и маршрутизацию в Интернете.</span><span class="sxs-lookup"><span data-stu-id="7f694-130">**WAN connection to ISP:** A carrier-based connection to an ISP, who peers with the Internet for connectivity and routing.</span></span>
    
## <a name="areas-of-networking-common-to-all-microsoft-cloud-services"></a><span data-ttu-id="7f694-131">Области сети, общие для всех служб Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="7f694-131">Areas of networking common to all Microsoft cloud services</span></span>
<span data-ttu-id="7f694-132"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="7f694-132"></span></span>

<span data-ttu-id="7f694-133">При внедрении любых облачных служб Майкрософт вам следует рассмотреть указанные ниже вопросы, касающиеся сети.</span><span class="sxs-lookup"><span data-stu-id="7f694-133">You need to consider these areas of networking when adopting any of Microsoft's cloud services.</span></span>
  
- <span data-ttu-id="7f694-134">**Производительность интрасети.** Если ваша интрасеть, включающая клиентские компьютеры, не оптимизирована, это отрицательно скажется на производительности ресурсов в Интернете.</span><span class="sxs-lookup"><span data-stu-id="7f694-134">**Intranet performance:** Performance to Internet-based resources will suffer if your intranet, including client computers, is not optimized.</span></span>
    
- <span data-ttu-id="7f694-135">**Пограничные устройства.** Устройства, расположенные на границе вашей сети, являются точками выхода и могут включать трансляторы сетевых адресов (NAT), прокси-серверы (включая обратные прокси-серверы), брандмауэры, устройства обнаружения вторжений или сочетания этих средств и устройств.</span><span class="sxs-lookup"><span data-stu-id="7f694-135">**Edge devices:** Devices at the edge of your network are egress points and can include Network Address Translators (NATs), proxy servers (including reverse proxies), firewalls, intrusion detection devices, or a combination.</span></span>
    
- <span data-ttu-id="7f694-p106">**Подключение к Интернету.** Подключение глобальной сети к поставщику услуг Интернета и к Интернету должно иметь пропускную способность, достаточную для обработки пиковых нагрузок. В качестве альтернативы вы можете использовать подключение ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="7f694-p106">**Internet connection:** Your WAN connection to your ISP and the Internet should have enough capacity to handle peak loads. You can also use an ExpressRoute connection.</span></span>
    
- <span data-ttu-id="7f694-p107">**DNS Интернета.** Записи A, AAAA, CNAME, MX, PTR и другие записи, необходимые для поиска Microsoft Cloud или ваших служб, размещенных в облаке. Например, для вашего приложения, размещенного в Azure PaaS, может понадобиться запись CNAME.</span><span class="sxs-lookup"><span data-stu-id="7f694-p107">**Internet DNS:** A, AAAA, CNAME, MX, PTR and other records to locate Microsoft cloud or your services hosted in the cloud. For example, you might need a CNAME record for your app hosted in Azure PaaS.</span></span>
    

## <a name="next-step"></a><span data-ttu-id="7f694-140">Следующее действие</span><span class="sxs-lookup"><span data-stu-id="7f694-140">Next step</span></span>

[<span data-ttu-id="7f694-141">ExpressRoute для подключения к Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="7f694-141">ExpressRoute for Microsoft cloud connectivity</span></span>](expressroute-for-microsoft-cloud-connectivity.md)

## <a name="see-also"></a><span data-ttu-id="7f694-142">См. также</span><span class="sxs-lookup"><span data-stu-id="7f694-142">See also</span></span>

<span data-ttu-id="7f694-143"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="7f694-143"></span></span>

[<span data-ttu-id="7f694-144">Облачные сети Майкрософт для корпоративных архитекторов</span><span class="sxs-lookup"><span data-stu-id="7f694-144">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="7f694-145">Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="7f694-145">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)


