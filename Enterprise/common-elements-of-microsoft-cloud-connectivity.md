---
title: "Общие элементы подключения к Microsoft Cloud"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Architecture
ms.assetid: 061d4507-7360-4029-8f4b-3d4bc6b4ade0
description: "Сводка. Об общих элементах сетевой инфраструктуры и подготовке сети."
ms.openlocfilehash: 28825ad299ee12b55037963c68a289f43ffcc56a
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="common-elements-of-microsoft-cloud-connectivity"></a><span data-ttu-id="f5969-103">Общие элементы подключения к Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="f5969-103">Common elements of Microsoft cloud connectivity</span></span>

 <span data-ttu-id="f5969-104">**Сводка.** Об общих элементах сетевой инфраструктуры и подготовке сети.</span><span class="sxs-lookup"><span data-stu-id="f5969-104">**Summary:** Understand the common elements of networking infrastructure and how to prepare your network.</span></span>
  
<span data-ttu-id="f5969-105">Интеграция вашей сети с Microsoft Cloud обеспечивает оптимальный доступ к широкому спектру служб.</span><span class="sxs-lookup"><span data-stu-id="f5969-105">Integrating your networking with the Microsoft cloud provides optimal access to a broad range of services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-cloud-services"></a><span data-ttu-id="f5969-106">Действия по подготовке сети для служб Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="f5969-106">Steps to prepare your network for Microsoft cloud services</span></span>
<span data-ttu-id="f5969-107"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="f5969-107"><a name="steps"> </a></span></span>

<span data-ttu-id="f5969-108">Для локальной сети:</span><span class="sxs-lookup"><span data-stu-id="f5969-108">For your on-premises network:</span></span>
  
1. <span data-ttu-id="f5969-109">проанализируйте имеющиеся у вас клиентские компьютеры и оптимизируйте сетевое оборудование, программные драйверы, параметры протоколов и веб-браузеры;</span><span class="sxs-lookup"><span data-stu-id="f5969-109">Analyze your client computers and optimize for network hardware, software drivers, protocol settings, and Internet browsers.</span></span>
    
2. <span data-ttu-id="f5969-110">проанализируйте локальную сеть на предмет задержек трафика и оптимальной маршрутизации до пограничного устройства Интернета;</span><span class="sxs-lookup"><span data-stu-id="f5969-110">Analyze your on-premises network for traffic latency and optimal routing to the Internet edge device.</span></span>
    
3. <span data-ttu-id="f5969-111">проанализируйте производительность пограничного устройства Интернета и оптимизируйте ее для повышенных значений интенсивности трафика.</span><span class="sxs-lookup"><span data-stu-id="f5969-111">Analyze the capacity and performance of your Internet edge device and optimize for higher levels of traffic.</span></span>
    
<span data-ttu-id="f5969-112">Для подключения к Интернету:</span><span class="sxs-lookup"><span data-stu-id="f5969-112">For your Internet connection:</span></span>
  
1. <span data-ttu-id="f5969-113">проанализируйте задержку между пограничным устройством Интернета (например, внешним брандмауэром) и региональными расположениями службы Microsoft Cloud, к которой вы подключаетесь;</span><span class="sxs-lookup"><span data-stu-id="f5969-113">Analyze the latency between your Internet edge device (such as your external firewall) and the regional locations of the Microsoft cloud service to which you are connecting.</span></span>
    
2. <span data-ttu-id="f5969-p101">проанализируйте пропускную способность и степень использования вашего текущего подключения к Интернету и при необходимости увеличьте пропускную способность. В качестве альтернативы вы можете добавить подключение ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="f5969-p101">Analyze the capacity and utilization of your current Internet connection and add capacity if needed. Alternately, add an ExpressRoute connection.</span></span>
    
## <a name="microsoft-cloud-connectivity-options"></a><span data-ttu-id="f5969-116">Варианты подключения к Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="f5969-116">Microsoft cloud connectivity options</span></span>
<span data-ttu-id="f5969-117"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="f5969-117"><a name="steps"> </a></span></span>

<span data-ttu-id="f5969-118">Используйте существующий интернет-канал или подключение ExpressRoute к Office 365, Azure и Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="f5969-118">Use your existing Internet pipe or an ExpressRoute connection to Office 365, Azure, and Dynamics 365.</span></span>
  
<span data-ttu-id="f5969-119">**Рис. 1. Варианты подключения к Microsoft Cloud**</span><span class="sxs-lookup"><span data-stu-id="f5969-119">**Figure 1: Options for Microsoft cloud connectivity**</span></span>

![Рис. 1. Варианты подключения к Microsoft Cloud](images/Network_Poster/CommonElements.png)

  
<span data-ttu-id="f5969-p102">На рис. 1 показано, как можно подключить локальную сеть к Microsoft Cloud, используя существующий интернет-канал или подключение ExpressRoute. Интернет-канал представляет зону DMZ и может содержать указанные ниже компоненты.</span><span class="sxs-lookup"><span data-stu-id="f5969-p102">Figure 1 shows how an on-premises network can be connected to Microsoft cloud offerings using their existing Internet pipe or ExpressRoute. The Internet pipe represents a DMZ and can have the following components:</span></span>
  
- <span data-ttu-id="f5969-p103">**Брандмауэр Интернета:** барьер между надежной и ненадежной сетями. Выполняет фильтрацию (на основе правил) и мониторинг трафика.</span><span class="sxs-lookup"><span data-stu-id="f5969-p103">**Internal firewall:** A barrier between your trusted network and an untrusted one. Performs traffic filtering (based on rules) and monitoring.</span></span>
    
- <span data-ttu-id="f5969-125">**Внешняя рабочая нагрузка:** веб-сайты или другие рабочие нагрузки, доступные для внешних пользователей в Интернете.</span><span class="sxs-lookup"><span data-stu-id="f5969-125">**External workload:** Web sites or other workloads made available to external users on the Internet.</span></span>
    
- <span data-ttu-id="f5969-p104">**Прокси-сервер.** Обслуживает запросы служб на веб-содержимое от имени пользователей интрасети. Обратный прокси-сервер разрешает незапрошенные входящие запросы.</span><span class="sxs-lookup"><span data-stu-id="f5969-p104">**Proxy server:** Services requests for web content on behalf of intranet users. A reverse proxy allows unsolicited inbound requests.</span></span>
    
- <span data-ttu-id="f5969-p105">**Внешний брандмауэр.** Разрешает исходящий трафик и указанный входящий трафик. Может выполнять преобразование адресов.</span><span class="sxs-lookup"><span data-stu-id="f5969-p105">**External firewall:** Allows outbound traffic and specified inbound traffic. Can perform address translation.</span></span>
    
- <span data-ttu-id="f5969-130">**Подключение глобальной сети к поставщику услуг Интернета.** Обеспечиваемое оператором подключение к поставщику услуг Интернета, который осуществляет подключение к Интернету и маршрутизацию в Интернете.</span><span class="sxs-lookup"><span data-stu-id="f5969-130">**WAN connection to ISP:** A carrier-based connection to an ISP, who peers with the Internet for connectivity and routing.</span></span>
    
## <a name="areas-of-networking-common-to-all-microsoft-cloud-services"></a><span data-ttu-id="f5969-131">Области сети, общие для всех служб Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="f5969-131">Areas of networking common to all Microsoft cloud services</span></span>
<span data-ttu-id="f5969-132"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="f5969-132"><a name="steps"> </a></span></span>

<span data-ttu-id="f5969-133">При внедрении любых облачных служб Майкрософт вам следует рассмотреть указанные ниже вопросы, касающиеся сети.</span><span class="sxs-lookup"><span data-stu-id="f5969-133">You need to consider these areas of networking when adopting any of Microsoft's cloud services.</span></span>
  
- <span data-ttu-id="f5969-134">**Производительность интрасети.** Если ваша интрасеть, включающая клиентские компьютеры, не оптимизирована, это отрицательно скажется на производительности ресурсов в Интернете.</span><span class="sxs-lookup"><span data-stu-id="f5969-134">**Intranet performance:** Performance to Internet-based resources will suffer if your intranet, including client computers, is not optimized.</span></span>
    
- <span data-ttu-id="f5969-135">**Пограничные устройства.** Устройства, расположенные на границе вашей сети, являются точками выхода и могут включать трансляторы сетевых адресов (NAT), прокси-серверы (включая обратные прокси-серверы), брандмауэры, устройства обнаружения вторжений или сочетания этих средств и устройств.</span><span class="sxs-lookup"><span data-stu-id="f5969-135">**Edge devices:** Devices at the edge of your network are egress points and can include Network Address Translators (NATs), proxy servers (including reverse proxies), firewalls, intrusion detection devices, or a combination.</span></span>
    
- <span data-ttu-id="f5969-p106">**Подключение к Интернету.** Подключение глобальной сети к поставщику услуг Интернета и к Интернету должно иметь пропускную способность, достаточную для обработки пиковых нагрузок. В качестве альтернативы вы можете использовать подключение ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="f5969-p106">**Internet connection:** Your WAN connection to your ISP and the Internet should have enough capacity to handle peak loads. You can also use an ExpressRoute connection.</span></span>
    
- <span data-ttu-id="f5969-p107">**DNS Интернета.** Записи A, AAAA, CNAME, MX, PTR и другие записи, необходимые для поиска Microsoft Cloud или ваших служб, размещенных в облаке. Например, для вашего приложения, размещенного в Azure PaaS, может понадобиться запись CNAME.</span><span class="sxs-lookup"><span data-stu-id="f5969-p107">**Internet DNS:** A, AAAA, CNAME, MX, PTR and other records to locate Microsoft cloud or your services hosted in the cloud. For example, you might need a CNAME record for your app hosted in Azure PaaS.</span></span>
    

## <a name="next-step"></a><span data-ttu-id="f5969-140">Следующее действие</span><span class="sxs-lookup"><span data-stu-id="f5969-140">Next step</span></span>

[<span data-ttu-id="f5969-141">ExpressRoute для подключения к Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="f5969-141">ExpressRoute for Microsoft cloud connectivity</span></span>](expressroute-for-microsoft-cloud-connectivity.md)

## <a name="see-also"></a><span data-ttu-id="f5969-142">См. также</span><span class="sxs-lookup"><span data-stu-id="f5969-142">See also</span></span>

<span data-ttu-id="f5969-143"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="f5969-143"></span></span>

[<span data-ttu-id="f5969-144">Облачные сети Майкрософт для корпоративных архитекторов</span><span class="sxs-lookup"><span data-stu-id="f5969-144">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="f5969-145">Материалы по архитектуре Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="f5969-145">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)


