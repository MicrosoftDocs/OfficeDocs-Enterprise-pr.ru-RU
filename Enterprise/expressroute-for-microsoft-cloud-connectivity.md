---
title: ExpressRoute для подключения к Microsoft Cloud
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/03/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: bf2295c4-d411-49cd-aaa5-116a4a456c5a
description: 'Сводка: в этой статье рассказывается, как с помощью ExpressRoute создать более быстрые и надежные подключения к облачным службам и платформам корпорации Майкрософт.'
ms.openlocfilehash: 55ac09e3c3cf65649d24d67ea79e185808d83cdb
ms.sourcegitcommit: c23b95d32a865e45be7843f38a1f23b5693ba76d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "20188117"
---
# <a name="expressroute-for-microsoft-cloud-connectivity"></a><span data-ttu-id="1ad8e-103">ExpressRoute для подключения к Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="1ad8e-103">ExpressRoute for Microsoft cloud connectivity</span></span>

 <span data-ttu-id="1ad8e-104">**Сводка:** в этой статье рассказывается, как с помощью ExpressRoute создать более быстрые и надежные подключения к облачным службам и платформам корпорации Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-104">**Summary:** Understand how ExpressRoute can help you with faster and more reliable connections to Microsoft's cloud services and platforms.</span></span>
  
<span data-ttu-id="1ad8e-105">ExpressRoute обеспечивает частное выделенное скоростное сетевое подключение к Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-105">ExpressRoute provides a private, dedicated, high-throughput network connection to Microsoft's cloud.</span></span>
  
## <a name="expressroute-to-the-microsoft-cloud"></a><span data-ttu-id="1ad8e-106">Подключение ExpressRoute к Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="1ad8e-106">ExpressRoute to the Microsoft cloud</span></span>

<span data-ttu-id="1ad8e-107">Ниже показан сетевой путь к Microsoft Cloud без подключения ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-107">Here is the networking path to the Microsoft cloud without an ExpressRoute connection.</span></span>
  
<span data-ttu-id="1ad8e-108">**Рис. 1. Сетевой путь без ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="1ad8e-108">**Figure 1: The networking path without ExpressRoute**</span></span>

![Рис. 1. Сетевой путь без ExpressRoute](images/Network_Poster/ExpressRoute.png)
  
<span data-ttu-id="1ad8e-p101">На рисунке 1 показан типичный путь между локальной сетью и облаком Майкрософт. Периметр локальной сети подключен к Интернету через WAN-канал от поставщика услуг Интернета. Трафик идет через Интернет к периметру облака Майкрософт. Среди предложений, доступных в облаке Майкрософт, есть Office 365, Microsoft Azure, Microsoft Intune и Dynamics 365. Пользователи в организации могут находиться в локальной сети или в Интернете.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-p101">Figure 1 shows the typical path between an on-premises network and the Microsoft cloud. The on-premises network edge connects to the Internet through a WAN link to an ISP. The traffic then travels across the Internet to the edge of the Microsoft cloud. Cloud offerings within the Microsoft cloud include Office 365, Microsoft Azure, Microsoft Intune, and Dynamics 365. Users of an organization can be located on the on-premises network or on the Internet.</span></span>
  
<span data-ttu-id="1ad8e-115">Без подключения ExpressRoute единственная часть пути трафика к Microsoft Cloud, которую вы можете контролировать (и поддерживать связь с поставщиком услуг) — это канал между границей локальной сети и поставщиком услуг Интернета.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-115">Without an ExpressRoute connection, the only part of the traffic path to the Microsoft cloud that you can control (and have a relationship with the service provider) is the link between your on-premises network edge and your ISP.</span></span> 
  
<span data-ttu-id="1ad8e-116">Путь между поставщиком услуг Интернета и границей Microsoft Cloud — это система доставки в Интернете, больше всего подверженная сбоям, перегрузкам и мониторингу со стороны пользователей-злоумышленников.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-116">The path between your ISP and the Microsoft cloud edge is a best-effort delivery system on the Internet subject to outages, traffic congestion, and monitoring by malicious users.</span></span>
  
<span data-ttu-id="1ad8e-117">Пользователи в Интернете, например путешествующие или удаленные пользователи, отправляют трафик в Microsoft Cloud через Интернет.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-117">Users on the Internet, such as roaming or remote users, send their traffic to the Microsoft cloud over the Internet.</span></span>
  
<span data-ttu-id="1ad8e-118">Ниже показан сетевой путь к Microsoft Cloud с подключением ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-118">Here are the networking paths to the Microsoft cloud with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="1ad8e-119">**Рис. 2. Сетевые пути с ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="1ad8e-119">**Figure 2: The networking paths with ExpressRoute**</span></span>

![Рис. 2. Сетевой путь с ExpressRoute](images/Network_Poster/ExpressRoute_post.png)
  
<span data-ttu-id="1ad8e-p102">На рисунке 2 показаны два сетевых пути. Трафик, направляемый в Microsoft Intune, проходит тот же путь, что и обычный интернет-трафик. Трафик, направляемый в Office 365, Microsoft Azure и Dynamics 365, проходит через подключение ExpressRoute, представляющее собой выделенный путь между параметром локальной сети и параметром облака Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-p102">Figure 2 shows two networking paths. Traffic to Microsoft Intune travels the same path as normal Internet traffic. Traffic to Office 365, Microsoft Azure, and Dynamics 365 travels across the ExpressRoute connection, a dedicated path between the edge of the on-premises network and the edge of the Microsoft cloud.</span></span>
  
<span data-ttu-id="1ad8e-p103">С помощью подключения к ExpressRoute вы теперь обеспечивает контроль через отношение с поставщиком услуг, через путь весь трафик от вашей пограничного сервера в корпорацию Майкрософт в облаке пограничного сервера. Это подключение можно предоставлять прогнозируемой производительности и [99,95% времени работоспособности соглашения об уровне ОБСЛУЖИВАНИЯ](https://azure.microsoft.com/support/legal/sla/expressroute/v1_3/).</span><span class="sxs-lookup"><span data-stu-id="1ad8e-p103">With an ExpressRoute connection, you now have control, through a relationship with your service provider, over the entire traffic path from your edge to the Microsoft cloud edge. This connection can offer predictable performance and a [99.95% uptime SLA](https://azure.microsoft.com/support/legal/sla/expressroute/v1_3/).</span></span>
  
<span data-ttu-id="1ad8e-p104">Теперь вы можете рассчитывать предсказуемые величины пропускной способности и задержек при работе со службами Office 365, Azure и Dynamics 365, учитывая параметры подключения, предоставленного поставщиком услуг. На данный момент подключения ExpressRoute к Microsoft Intune не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-p104">You can now count on predictable throughput and latency, based on your service provider's connection, to Office 365, Azure, and Dynamics 365 services. ExpressRoute connections to Microsoft Intune are not supported at this time.</span></span>
  
<span data-ttu-id="1ad8e-128">На трафик, отправляемый через подключение ExpressRoute, не оказывают влияние сбои в Интернете и перегрузки каналов. Кроме того, он не подвержен мониторингу со стороны злоумышленников.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-128">Traffic sent over the ExpressRoute connection is no longer subject to Internet outages, traffic congestion, and monitoring.</span></span>
  
<span data-ttu-id="1ad8e-p105">Пользователи в Интернете, например путешествующие или удаленные пользователи, по-прежнему будут отправлять трафик в Microsoft Cloud через Интернет. Единственное исключение — трафик бизнес-приложения, размещенного в Azure IaaS, направляемый в линию интрасети. Он будет проходить через подключение ExpressRoute через подключение удаленного доступа к локальной сети.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-p105">Users on the Internet, such as roaming or remote users, still send their traffic to the Microsoft cloud over the Internet. One exception is traffic to an intranet line of business application hosted in Azure IaaS, which is sent over the ExpressRoute connection via a remote access connection to the on-premises network.</span></span>
  
<span data-ttu-id="1ad8e-131">Даже при наличии подключения ExpressRoute часть трафика, например запросы DNS, проверки списков отзыва сертификатов и запросы сети доставки содержимого, будет передаваться через Интернет.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-131">Even with an ExpressRoute connection, some traffic is still sent over the Internet, such as DNS queries, certificate revocation list checking, and content delivery network (CDN) requests.</span></span>
  
<span data-ttu-id="1ad8e-132">Дополнительные сведения см. в указанных ниже ресурсах.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-132">See these additional resources for more information:</span></span>
  
- [<span data-ttu-id="1ad8e-133">ExpressRoute для Office 365</span><span class="sxs-lookup"><span data-stu-id="1ad8e-133">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
- [<span data-ttu-id="1ad8e-134">ExpressRoute для Azure</span><span class="sxs-lookup"><span data-stu-id="1ad8e-134">ExpressRoute for Azure</span></span>](https://azure.microsoft.com/services/expressroute/)
    
## <a name="advantages-of-expressroute-for-azure"></a><span data-ttu-id="1ad8e-135">Преимущества ExpressRoute для Azure</span><span class="sxs-lookup"><span data-stu-id="1ad8e-135">Advantages of ExpressRoute for Azure</span></span>

<span data-ttu-id="1ad8e-136">Ниже описан ряд преимуществ использования подключений ExpressRoute для облачных служб на основе Azure.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-136">Here are some advantages of using ExpressRoute for Azure-based cloud services:</span></span>
  
- <span data-ttu-id="1ad8e-p106">**Предсказуемая производительность.** Благодаря выделенному пути к границе Microsoft Cloud производительность подключения не будет зависеть от сбоев по вине поставщика услуг Интернета или от пиков интернет-трафика. Вы можете определить параметры пропускной способности и величины задержек для подключений к Microsoft Cloud в соглашении об уровне обслуживания и требовать от поставщика услуг Интернета соблюдать эти условия.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-p106">**Predictable performance:** With a dedicated path to the edge of the Microsoft cloud, your performance is not subject to Internet provider outages and spikes in Internet traffic. You can determine and hold your providers accountable to a throughput and latency SLA to the Microsoft cloud.</span></span>
    
- <span data-ttu-id="1ad8e-p107">**Конфиденциальность данных, передаваемых в трафике.** Трафик, отправляемый через выделенное подключение ExpressRoute, не подвергается мониторингу в Интернете, а пользователи-злоумышленники не смогут перехватывать пакеты трафика и анализировать их. Передача данных по такому каналу так же безопасна, как и при использовании каналов глобальной сети на основе MPLS.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-p107">**Data privacy for your traffic:** Traffic sent over your dedicated ExpressRoute connection is not subject to Internet monitoring or packet capture and analysis by malicious users. It is as secure as using Multiprotocol Label Switching (MPLS)-based WAN links.</span></span>
    
- <span data-ttu-id="1ad8e-141">**Высокая пропускная способность подключений.** Благодаря широкой поддержке подключений ExpressRoute поставщиками обменников и сетевых услуг вы можете использовать канал к Microsoft Cloud со скоростью до 10 Гбит/с.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-141">**High throughput connections:** With wide support for ExpressRoute connections by exchange providers and network service providers, you can obtain up to a 10 Gbps link to the Microsoft cloud.</span></span>
    
- <span data-ttu-id="1ad8e-142">**Сниженная цена для ряда конфигураций.** Несмотря на то что подключения ExpressRoute предоставляются за отдельную плату, в некоторых случаях расходы на одно подключение ExpressRoute могут быть меньше, чем затраты на увеличение пропускной способности интернет-канала в нескольких расположениях организации до уровня, необходимого для нормальной работы со службами Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-142">**Lower cost for some configurations:** Although ExpressRoute connections are an additional cost, in some cases a single ExpressRoute connection can cost less than increasing your Internet capacity at multiple locations of your organization to provide adequate throughput to Microsoft cloud services.</span></span>
    
<span data-ttu-id="1ad8e-p108">Подключение ExpressRoute обеспечивает более высокую производительность не во всех конфигурациях. Возможно, что производительность подключения ExpressRoute с низкой пропускной способностью будет меньше высокоскоростного интернет-подключения, особенно если путь до регионального центра обработки данных корпорации Майкрософт состоит всего из нескольких прыжков.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-p108">An ExpressRoute connection is not a guarantee of higher performance in every configuration. It is possible to have lower performance over a low-bandwidth ExpressRoute connection than a high-bandwidth Internet connection that is only a few hops away from a regional Microsoft datacenter.</span></span>
  
<span data-ttu-id="1ad8e-145">Самые актуальные рекомендации по использованию ExpressRoute в Office 365 представлены в статье [Azure ExpressRoute для Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span><span class="sxs-lookup"><span data-stu-id="1ad8e-145">For the latest recommendations for using ExpressRoute with Office 365, see [ExpressRoute for Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span></span>
  
## <a name="expressroute-connectivity-models"></a><span data-ttu-id="1ad8e-146">Модели подключений ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="1ad8e-146">ExpressRoute connectivity models</span></span>

<span data-ttu-id="1ad8e-147">В таблице 1 показаны три основные модели подключений ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-147">Table 1 shows the three primary connectivity models for ExpressRoute connections.</span></span>
  
|<span data-ttu-id="1ad8e-148">**Совместное размещение в облачном обменнике**</span><span class="sxs-lookup"><span data-stu-id="1ad8e-148">**Co-located at a cloud exchange**</span></span>|<span data-ttu-id="1ad8e-149">**Подключение "точка-точка" через Ethernet**</span><span class="sxs-lookup"><span data-stu-id="1ad8e-149">**Point-to-point Ethernet**</span></span>|<span data-ttu-id="1ad8e-150">**Подключение "любой-к-любому" (IP-VPN)**</span><span class="sxs-lookup"><span data-stu-id="1ad8e-150">**Any-to-any (IP VPN) connection**</span></span>|
|:-----|:-----|:-----|
|![Модель подключения ExpressRoute: совместное размещение в облачном обменнике](images/Network_Poster/ER_Conn1.png)|![Модель подключения ExpressRoute: подключение "точка-точка" через Ethernet](images/Network_Poster/ER_Conn2.png)|![Модель подключения ExpressRoute: подключение "любой-к-любому" (IP-VPN)](images/Network_Poster/ER_Conn3.png)|
|<span data-ttu-id="1ad8e-154">Если используемый вами центр обработки данных размещен на одном объекте с облачным обменником, вы можете заказать виртуальное перекрестное подключение к Microsoft Cloud через Ethernet-обменник поставщика услуг.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-154">If your datacenter is co-located in a facility with a cloud exchange, you can order a virtual cross-connection to the Microsoft cloud through the co-location provider's Ethernet exchange.</span></span>  <br/> |<span data-ttu-id="1ad8e-155">Если используемый вами центр обработки данных расположен на том же объекте, что и ваша организация, то для подключения к Microsoft Cloud вы можете использовать Ethernet-канал "точка-точка".</span><span class="sxs-lookup"><span data-stu-id="1ad8e-155">If your datacenter is located on your premises, you can use a point-to-point Ethernet link to connect to the Microsoft cloud.</span></span>  <br/> |<span data-ttu-id="1ad8e-156">Если вы уже используете IP VPN (MPLS) для подключения к сайтам своей организации, то подключение ExpressRoute к Microsoft Cloud будет представлять собой дополнительное расположение в вашей частной глобальной сети.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-156">If you are already using an IP VPN (MPLS) provider to connect the sites of your organization, an ExpressRoute connection to the Microsoft cloud acts like another location on your private WAN.</span></span>  <br/> |
   
 <span data-ttu-id="1ad8e-157">**Табл. 1. Модели подключений ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="1ad8e-157">**Table 1: ExpressRoute connectivity models**</span></span>
  
## <a name="expressroute-peering-relationships-to-microsoft-cloud-services"></a><span data-ttu-id="1ad8e-158">Пиринговые связи ExpressRoute со службами Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="1ad8e-158">ExpressRoute peering relationships to Microsoft cloud services</span></span>

<span data-ttu-id="1ad8e-p109">Одно подключение ExpressRoute поддерживает до трех различных пиринговых связей по протоколу BGP к различным частям Microsoft Cloud. В протоколе BPG пиринговые связи используются для создания доверия и обмена информацией о маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-p109">A single ExpressRoute connection supports up to three different Border Gateway Protocol (BGP) peering relationships to different parts of the Microsoft cloud. BPG uses peering relationships to establish trust and exchange routing information.</span></span>
  
<span data-ttu-id="1ad8e-161">**Рис. 3. Три различные связи по протоколу BGP связи в одном подключении ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="1ad8e-161">**Figure 3: The three different BGP relationships in a single ExpressRoute connection**</span></span>

![Рис. 3. Три различные связи по протоколу BGP связи в одном подключении ExpressRoute](images/Network_Poster/ERPeering.png)
  
<span data-ttu-id="1ad8e-p110">На рис. 3 показано подключение ExpressRoute из локальной сети. Подключение ExpressRoute содержит три логические пиринговые связи. Через пиринговую связь Майкрософт можно получить доступ к службам Microsoft SaaS, включая Office 365 и Dynamcs CRM Online. Через общедоступную пиринговую связь можно получить доступ к службам Azure PaaS. Через частную пиринговую связь можно получить доступ к Azure IaaS и шлюзу виртуальной сети, в которой размещены виртуальные машины.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-p110">Figure 3 shows an ExpressRoute connection from an on-premises network. The ExpressRoute connection contains three logical peering relationships. A Microsoft peering relationship goes to Microsoft SaaS services, including Office 365 and Dynamcs CRM Online. A public peering relationship goes to Azure PaaS services. A private peering relationship goes to Azure IaaS and to a virtual network gateway that hosts virtual machines.</span></span>
  
<span data-ttu-id="1ad8e-168">Пиринговая связь Майкрософт по протоколу BGP предоставляет указанные ниже возможности.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-168">The Microsoft peering BGP relationship:</span></span> 
  
- <span data-ttu-id="1ad8e-169">Соединяет маршрутизатор в вашей сети периметра с общедоступными адресами служб Office 365 и Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-169">Is from a router in your DMZ to the public addresses of Office 365 and Dynamics 365 services.</span></span> 
    
- <span data-ttu-id="1ad8e-170">Поддерживает двунаправленно-инициированную связь.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-170">Supports bidirectional-initiated communication.</span></span>
    
<span data-ttu-id="1ad8e-171">Общедоступная пиринговая связь по протоколу BGP предоставляет указанные ниже возможности.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-171">The public peering BGP relationship:</span></span>
  
- <span data-ttu-id="1ad8e-172">Соединяет маршрутизатор в вашей зоне DMZ с общедоступными IP-адресами служб Azure.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-172">Is from a router in your DMZ to the public IP addresses of Azure services.</span></span>
    
- <span data-ttu-id="1ad8e-p111">Поддерживает только однонаправленно-инициированную связь из локальных систем. Пиринговая связь не поддерживает обмен данными, инициированный службами Azure PaaS.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-p111">Supports unidirectional-initiated communication from on-premises systems only. The peering relationship does not support communication initiated from Azure PaaS services.</span></span>
    
<span data-ttu-id="1ad8e-175">Частная пиринговая связь по протоколу BGP предоставляет указанные ниже возможности.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-175">The private peering BGP relationship:</span></span>
  
- <span data-ttu-id="1ad8e-176">Соединяет маршрутизатор на границе сети вашей организации с частными адресами, назначенными вашим виртуальным сетям Azure.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-176">Is from a router on the edge of your organization network to the private IP addresses assigned to your Azure VNets.</span></span>
    
- <span data-ttu-id="1ad8e-177">Поддерживает двунаправленно-инициированную связь.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-177">Supports bidirectional-initiated communication.</span></span>
    
- <span data-ttu-id="1ad8e-178">Представляет собой расширение сети вашей организации в Microsoft Cloud с полностью внутренне согласованными адресацией и маршрутизацией.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-178">Is an extension of your organization network to the Microsoft cloud, complete with internally-consistent addressing and routing.</span></span>
    
## <a name="example-of-application-deployment-and-traffic-flow-with-expressroute"></a><span data-ttu-id="1ad8e-179">Пример развертывания приложения и потока трафик при использовании ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="1ad8e-179">Example of application deployment and traffic flow with ExpressRoute</span></span>

<span data-ttu-id="1ad8e-p112">То, как трафик проходит через подключения ExpressRoute и внутри Microsoft Cloud, зависит от маршрутов прыжков пути между источником и местом назначения, а также от действий приложения. Ниже показан пример приложения, работающего на виртуальной машине Azure и получающего доступ к локальной ферме SharePoint через подключение VPN типа "сеть-сеть".</span><span class="sxs-lookup"><span data-stu-id="1ad8e-p112">How traffic travels across ExpressRoute connections and within the Microsoft cloud is a function of the routes at the hops of the path between the source and the destination and application behavior. Here is an example of an application running on an Azure virtual machine that accesses an on-premises SharePoint farm over a site-to-site VPN connection.</span></span>
  
<span data-ttu-id="1ad8e-182">**Рис. 4. Приложение на виртуальной машине Azure, получающее доступ к локальной ферме SharePoint**</span><span class="sxs-lookup"><span data-stu-id="1ad8e-182">**Figure 4: An application on an Azure virtual machine accessing an on-premises SharePoint farm**</span></span>

![Рис. 4. Приложение на виртуальной машине Azure, получающее доступ к локальной ферме SharePoint](images/Network_Poster/ER_App_Flow1.png)

  
<span data-ttu-id="1ad8e-184">На рис. 4 показаны локальная ферма SharePoint, подключение VPN типа "сеть-сеть" между локальной сетью и виртуальной сетью в Azure IaaS, сервер приложений, работающий в качестве виртуальной машины Azure IaaS, и поток трафика между сервером приложений и фермой SharePoint.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-184">Figure 4 shows an on-premises SharePoint farm, a site-to-site VPN connection between the on-premises network and a virtual network in Azure IaaS, an application server running as an Azure IaaS virtual machine, and the traffic flow between the application server and the SharePoint farm.</span></span>
  
<span data-ttu-id="1ad8e-185">Приложение находит IP-адрес фермы SharePoint с помощью локальной DNS, и весь трафик направляется через подключение VPN типа "сеть-сеть".</span><span class="sxs-lookup"><span data-stu-id="1ad8e-185">The application locates the IP address of the SharePoint farm using the on-premises DNS and all traffic goes over the site-to-site VPN connection.</span></span>
  
<span data-ttu-id="1ad8e-186">Эта организация выполнила миграцию своей локальной фермы SharePoint в SharePoint Online в Office 365 и развернула подключение ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-186">This organization migrated their on-premises SharePoint farm to SharePoint Online in Office 365 and deployed an ExpressRoute connection.</span></span>
  
<span data-ttu-id="1ad8e-187">**Рис. 5. Перемещение локальной фермы SharePoint в SharePoint Online**</span><span class="sxs-lookup"><span data-stu-id="1ad8e-187">**Figure 5: Moving the on-premises SharePoint farm to SharePoint Online**</span></span>

![Рис. 5. Перемещение локальной фермы SharePoint в SharePoint Online](images/Network_Poster/Hairpin1.png)
  
<span data-ttu-id="1ad8e-p113">На рис. 5 показано, как добавить подключение ExpressRoute с пиринговыми связями к Microsoft SaaS и Office 365, а также к службе Azure IaaS, содержащей сервер приложений в виртуальной сети. Локальная ферма SharePoint была перенесена в Office 365.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-p113">Figure 5 shows the addition of an ExpressRoute connection with peering relationships to Microsoft SaaS and Office 365 and to Azure IaaS containing the application server on a virtual network. The SharePoint on-premises farm has been migrated to Office 365.</span></span>
  
<span data-ttu-id="1ad8e-191">Благодаря пиринговым связям Майкрософт и частным пиринговым связям:</span><span class="sxs-lookup"><span data-stu-id="1ad8e-191">With the Microsoft and private peering relationships:</span></span>
  
- <span data-ttu-id="1ad8e-192">из шлюза виртуальной сети Azure локальные расположения доступны через подключение ExpressRoute;</span><span class="sxs-lookup"><span data-stu-id="1ad8e-192">From the Azure virtual network gateway, on-premises locations are available across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="1ad8e-193">из подписки на Office 365 общедоступные IP-адреса пограничных устройств, например прокси-серверов, доступны через подключение ExpressRoute;</span><span class="sxs-lookup"><span data-stu-id="1ad8e-193">From the Office 365 subscription, public IP addresses of edge devices, such as proxy servers, are available across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="1ad8e-194">с границы локальной сети частные IP-адреса виртуальной сети Azure и общедоступные IP-адреса Office 365 доступны через подключение ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-194">From the on-premises network edge, the private IP addresses of the Azure VNet and the public IP addresses of Office 365 are available across the ExpressRoute connection.</span></span>
    
<span data-ttu-id="1ad8e-195">Когда приложение получает доступ к URL-адресам SharePoint Online, оно перенаправляет свой трафик через подключение ExpressRoute на прокси-сервер, который расположен на границе.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-195">When the application accesses the URLs of SharePoint Online, it forwards its traffic across the ExpressRoute connection to a proxy server in the edge.</span></span> 
  
<span data-ttu-id="1ad8e-p114">Когда прокси-сервер находит IP-адрес SharePoint Online, он перенаправляет трафик обратно через подключение ExpressRoute. Ответный трафик проходит обратный путь.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-p114">When the proxy server locates the IP address of SharePoint Online, it forwards the traffic back over the ExpressRoute connection. Response traffic travels the reverse path.</span></span>
  
<span data-ttu-id="1ad8e-198">**Рис. 6. Поток трафика после миграции фермы SharePoint в SharePoint Online в Office 365**</span><span class="sxs-lookup"><span data-stu-id="1ad8e-198">**Figure 6: Traffic flow when the SharePoint farm has been migrated to SharePoint Online in Office 365**</span></span>

![Рис. 6. Поток трафика после миграции фермы SharePoint в SharePoint Online в Office 365](images/Network_Poster/Hairpin2.png)

  
<span data-ttu-id="1ad8e-200">На рис. 6 показано, как трафик между сервером приложений и SharePoint Online в Office 365 проходит через частную пиринговую связь от сервера приложений к границе локальной сети, а затем  от границы (через пиринговую связь Майкрософт) до Office 365.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-200">Figure 6 shows how the traffic between the application server and SharePoint Online in Office 365 flows over the private peering relationship from the application server to the on-premises network edge, and then from the edge over the Microsoft peering relationship to Office 365.</span></span>
  
<span data-ttu-id="1ad8e-201">В результате мы получим режим разворота пакетов, который является следствием использованной схемы маршрутизации и действий приложения.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-201">The result is hair pinning, a consequence of the routing and application behavior.</span></span>
  
## <a name="expressroute-and-microsofts-cloud-network"></a><span data-ttu-id="1ad8e-202">ExpressRoute и сеть Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="1ad8e-202">ExpressRoute and Microsoft's cloud network</span></span>

<span data-ttu-id="1ad8e-203">Доступны две различные версии подключений ExpressRoute: ExpressRoute и ExpressRoute Premium.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-203">ExpressRoute connections are available in two different versions: ExpressRoute and ExpressRoute Premium.</span></span>
  
### <a name="expressroute"></a><span data-ttu-id="1ad8e-204">ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="1ad8e-204">ExpressRoute</span></span>

<span data-ttu-id="1ad8e-205">То, как трафик перемещается между сетью вашей организации и центром обработки данных Майкрософт, зависит от:</span><span class="sxs-lookup"><span data-stu-id="1ad8e-205">How traffic travels between your organization network and a Microsoft datacenter is a combination of:</span></span>
  
- <span data-ttu-id="1ad8e-206">вашего расположения;</span><span class="sxs-lookup"><span data-stu-id="1ad8e-206">Your locations.</span></span>
    
- <span data-ttu-id="1ad8e-207">расположений пиринга Microsoft Cloud (физических расположений для подключения к границе Майкрософт);</span><span class="sxs-lookup"><span data-stu-id="1ad8e-207">Microsoft cloud peering locations (the physical locations to connect to the Microsoft edge).</span></span>
    
- <span data-ttu-id="1ad8e-208">расположений центров обработки данных Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-208">Microsoft datacenter locations.</span></span>
    
<span data-ttu-id="1ad8e-209">Расположения центров обработки данных Майкрософт и облачного пиринга подключены к сети Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-209">Microsoft datacenter and cloud peering locations are all connected to the Microsoft cloud network.</span></span>
  
<span data-ttu-id="1ad8e-p115">При создании подключения ExpressRoute к расположению пиринга Microsoft Cloud вы будете подключены к сети Microsoft Cloud и всем расположениям центров обработки данных Майкрософт на одном и том же континенте. Трафик, передаваемый между расположением облачного пиринга и целевым центром обработки данных Майкрософт, проходит через сеть Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-p115">When you create an ExpressRoute connection to a Microsoft cloud peering location, you are connected to the Microsoft cloud network and all the Microsoft datacenter locations in the same continent. The traffic between the cloud peering location and the destination Microsoft datacenter is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="1ad8e-212">Это может стать причиной неоптимальной доставки данных в локальные центры обработки данных Майкрософт при использовании модели подключения "любой-к-любому".</span><span class="sxs-lookup"><span data-stu-id="1ad8e-212">This can result in non-optimal delivery to local Microsoft datacenters for the any-to-any connectivity model.</span></span>
  
<span data-ttu-id="1ad8e-213">**Рис. 7. Пример географически распределенной организации, использующей одно подключение ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="1ad8e-213">**Figure 7: Example of an geographically-distributed organization that uses a single ExpressRoute connection**</span></span>

![Рис. 7. Пример географически распределенной организации, использующей одно подключение ExpressRoute](images/Network_Poster/MSNet1.png)
  
<span data-ttu-id="1ad8e-p116">На рис. 7 показана организация с двумя расположениями: расположением 1 на северо-западе США и расположением 2 на северо-востоке. Они соединены через поставщика услуг глобальной сети по схеме "любой-к-любому". Кроме того, в этой организации имеется подключение ExpressRoute к расположению пиринга Майкрософт на западном побережье. Трафик из расположения 2 на северо-востоке, предназначенный для центра обработки данных на восточном побережье, должен проходить весь путь через глобальную сеть организации на западное побережье (в расположение пиринга Майкрософт), а затем через всю страну возвращаться через сеть Microsoft Cloud в центр обработки данных на восточном побережье.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-p116">Figure 7 shows an organization with two locations, Location 1 in the northwest of the United States and Location 2 in the northeast. They are connected by an any-to-any WAN provider. This organization also has an ExpressRoute connection to a Microsoft peering location on the west coast. Traffic from Location 2 in the northeast destined for an east coast datacenter must travel all the way across the organization's WAN to the west coast, to the Microsoft peering location, and then back across the country over the Microsoft cloud network to the east coast datacenter.</span></span>
  
<span data-ttu-id="1ad8e-219">Для оптимальной доставки данных используйте несколько подключений ExpressRoute к региональным расположениям пиринга Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-219">For optimal delivery, use multiple ExpressRoute connections to regional Microsoft cloud peering locations.</span></span> 
  
<span data-ttu-id="1ad8e-220">**Рис. 8. Использование нескольких подключений ExpressRoute для оптимальной доставки данных в региональные центры обработки данных**</span><span class="sxs-lookup"><span data-stu-id="1ad8e-220">**Figure 8: The use of multiple ExpressRoute connections for optimal delivery to regional datacenters**</span></span>

![Рис. 8. Использование нескольких подключений ExpressRoute для оптимальной доставки данных в региональные центры обработки данных](images/Network_Poster/MSNet2.png)
  
<span data-ttu-id="1ad8e-p117">На рис. 8 показана та же организация с двумя подключениями ExpressRoute (по одному для каждого расположения) к регионально-локальным расположениям пиринга Майкрософт. В этой конфигурации трафик из расположения 2 на северо-востоке, предназначенный для центра обработки данных на восточном побережье, направляется непосредственно в расположение пиринга на восточном побережье, в сеть Microsoft Cloud, а затем  в центр обработки данных на восточном побережье.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-p117">Figure 8 shows the same organization with two ExpressRoute connections, one for each location, to regionally local Microsoft peering locations. In this configuration, traffic from Location 2 in the northeast destined for an east coast datacenter goes directly to an east coast peering location, to the Microsoft cloud network, and then to the east coast datacenter.</span></span>
  
<span data-ttu-id="1ad8e-224">Используя несколько подключений ExpressRoute, можно:</span><span class="sxs-lookup"><span data-stu-id="1ad8e-224">Multiple ExpressRoute connections can provide:</span></span>
  
- <span data-ttu-id="1ad8e-225">увеличить производительность при обращении к регионально-локальным расположениям центров обработки данных Майкрософт;</span><span class="sxs-lookup"><span data-stu-id="1ad8e-225">Better performance to regionally local Microsoft datacenter locations.</span></span>
    
- <span data-ttu-id="1ad8e-226">повысить доступность облака Майкрософт, когда локальное подключение ExpressRoute становится недоступным.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-226">Higher availability to the Microsoft cloud when a local ExpressRoute connection becomes unavailable.</span></span>
    
<span data-ttu-id="1ad8e-p118">Эта схема хорошо работает для организаций, расположенных на одном континенте. Тем не менее трафик, направляемый в центры обработки данных Майкрософт, расположенные вне континента, на котором находится организация, передается через Интернет.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-p118">This works well for organizations in the same continent. However, traffic to Microsoft datacenters outside the organization's continent travels over the Internet.</span></span>
  
<span data-ttu-id="1ad8e-229">Для передачи трафика через сеть Microsoft Cloud между континентами необходимо использовать подключения ExpressRoute Premium.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-229">For intercontinental traffic over the Microsoft cloud network, you must use ExpressRoute Premium connections.</span></span>
  
### <a name="expressroute-premium"></a><span data-ttu-id="1ad8e-230">ExpressRoute Premium</span><span class="sxs-lookup"><span data-stu-id="1ad8e-230">ExpressRoute Premium</span></span>

<span data-ttu-id="1ad8e-231">Для глобально распределенных организаций, расположенных на разных континентах, можно использовать подключения ExpressRoute Premium.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-231">For organizations that are globally distributed across continents, you can use ExpressRoute Premium.</span></span> 
  
<span data-ttu-id="1ad8e-p119">С помощью ExpressRoute Premium вы можете передавать данные в любой центр обработки данных Майкрософт на любом континенте из любого расположения пиринга Майкрософт на любом континенте. Трафик между континентами передается по сети Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-p119">With ExpressRoute Premium, you can reach any Microsoft datacenter on any continent from any Microsoft peering location on any continent. The traffic between continents is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="1ad8e-234">Используя несколько подключений ExpressRoute Premium, можно:</span><span class="sxs-lookup"><span data-stu-id="1ad8e-234">With multiple ExpressRoute Premium connections, you can have:</span></span>
  
- <span data-ttu-id="1ad8e-235">увеличить производительность при обращении к континентально-локальным центрам обработки данных Майкрософт;</span><span class="sxs-lookup"><span data-stu-id="1ad8e-235">Better performance to continentally local Microsoft datacenters.</span></span>
    
- <span data-ttu-id="1ad8e-236">повысить доступность глобального облака Майкрософт, когда локальное подключение ExpressRoute становится недоступным.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-236">Higher availability to the global Microsoft cloud when a local ExpressRoute connection becomes unavailable.</span></span>
    
<span data-ttu-id="1ad8e-p120">Для подключений ExpressRoute на основе Office 365 необходимо использовать ExpressRoute Premium. Предприятия, у которых не менее 500 лицензированных пользователей, могут использовать ExpressRoute Premium бесплатно.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-p120">ExpressRoute Premium is required for Office 365-based ExpressRoute connections. However, there is no additional cost for enterprises with 500 or more licensed users.</span></span>
  
<span data-ttu-id="1ad8e-239">**Рис. 9. Всемирная сеть Microsoft Cloud**</span><span class="sxs-lookup"><span data-stu-id="1ad8e-239">**Figure 9: The world-wide Microsoft cloud network**</span></span>

![Рис. 9. Всемирная сеть Microsoft Cloud](images/Network_Poster/MSNet3.png)
  
<span data-ttu-id="1ad8e-p121">На рис. 9 показана логическая схема всемирной сети Microsoft Cloud с сетями, охватывающими континенты и регионы мира, а также взаимосвязи между ними. С помощью имеющейся на каждом континенте части сети Microsoft Cloud глобальное предприятие может из своих офисов региональных филиалов создавать подключения ExpressRoute Premium к локальным расположениям пиринга Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-p121">Figure 9 shows a logical diagram of the worldwide Microsoft cloud network, with networks that span the continents and regions of the world and their interconnections. With a portion of the Microsoft cloud network in each continent, a global enterprise creates ExpressRoute Premium connections from its regional hub offices to local Microsoft peering locations.</span></span>
  
<span data-ttu-id="1ad8e-243">Для регионального офиса соответствующий трафик Office 365:</span><span class="sxs-lookup"><span data-stu-id="1ad8e-243">For a regional office, appropriate Office 365 traffic to:</span></span>
  
- <span data-ttu-id="1ad8e-244">направляемый к континентальным центрам обработки данных Office 365, проходит через сеть Microsoft Cloud в пределах одного континента;</span><span class="sxs-lookup"><span data-stu-id="1ad8e-244">Continental Office 365 datacenters travels over the Microsoft cloud network within the continent.</span></span>
    
- <span data-ttu-id="1ad8e-245">направляемый к центрам обработки данных Office 365 на другом континенте, проходит через межконтинентальную сеть Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-245">Office 365 datacenters in another continent travels over the intercontinental Microsoft cloud network.</span></span>
    
<span data-ttu-id="1ad8e-246">Дополнительные сведения см. в следующих разделах:</span><span class="sxs-lookup"><span data-stu-id="1ad8e-246">For more information, see:</span></span>
  
- [<span data-ttu-id="1ad8e-247">Azure ExpressRoute для обучения работе с Office 365</span><span class="sxs-lookup"><span data-stu-id="1ad8e-247">Azure ExpressRoute for Office 365 Training</span></span>](https://channel9.msdn.com/series/aer/)
    
- [<span data-ttu-id="1ad8e-248">Планирование использования сетей и настройка производительности для Office 365</span><span class="sxs-lookup"><span data-stu-id="1ad8e-248">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)
    
- [<span data-ttu-id="1ad8e-249">Управление производительностью Office 365</span><span class="sxs-lookup"><span data-stu-id="1ad8e-249">Office 365 Performance Management</span></span>](https://mva.microsoft.com/en-US/training-courses/office-365-performance-management-8416)
    
## <a name="expressroute-options"></a><span data-ttu-id="1ad8e-250">Дополнительные возможности для ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="1ad8e-250">ExpressRoute options</span></span>

<span data-ttu-id="1ad8e-251">Вы можете использовать указанные ниже дополнительные возможности для развертывания ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-251">You can also incorporate the following options into your ExpressRoute deployment:</span></span>
  
- <span data-ttu-id="1ad8e-252">**Безопасность на границе вашей среды.** Для повышения безопасности трафика, отправляемого и получаемого через подключение ExpressRoute, например для проверки трафика или обнаружения вторжений и вредоносного программного обеспечения, разместите свои устройства обеспечения безопасности на пути трафика в вашей зоне DMZ или на границе вашей интрасети.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-252">**Security at your edge:** To provide advanced security for the traffic sent and received over the ExpressRoute connection, such as traffic inspection or intrusion/malware detection, place your security appliances in the traffic path within your DMZ or at the border of your intranet.</span></span>
    
    <span data-ttu-id="1ad8e-p122">Интернет-трафик для виртуальных машин. Чтобы запретить виртуальным машинам Azure инициировать трафик напрямую в расположения в Интернете, объявите в качестве маршрута, используемого по умолчанию, маршрут в Майкрософт. Трафик, направляемый в Интернет, будет маршрутизироваться через подключение ExpressRoute и через ваши локальные прокси-серверы. Трафик из виртуальных машин Azure в службы Azure PaaS или Office 365, будет маршрутизироваться обратно через подключение ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-p122">Internet traffic for VMs To prevent Azure VMs from initiating traffic directly with Internet locations, advertise the default route to Microsoft. Traffic to the Internet is routed across the ExpressRoute connection and through your on-premises proxy servers. Traffic from Azure VMs to Azure PaaS services or Office 365 is routed back across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="1ad8e-p123">**Оптимизаторы глобальной сети.** Вы можете развернуть оптимизаторы глобальной сети на обеих сторонах частного пирингового подключения для распределенной виртуальной сети Azure. Внутри виртуальной сети Azure используйте сетевое средство оптимизатора глобальной сети из Azure Marketplace и настройте пользовательскую маршрутизацию трафика через это средство.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-p123">**WAN optimizers:** You can deploy WAN optimizers on both sides of a private peering connection for a cross-premises Azure virtual network (VNet). Inside the Azure VNet, use a WAN optimizer network appliance from the Azure marketplace and user-defined routing to route the traffic through the appliance.</span></span>
    
- <span data-ttu-id="1ad8e-p124">**Качество обслуживания.** Используйте значения DSCP в заголовке IPv4 своего трафика, чтобы промаркировать его для доставки голоса, видео и интерактивных материалов или использования лучших вариантов. Это особенно важно для трафика пиринговой связи Майкрософт и Skype для бизнеса Online.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-p124">**Quality of service:** Use Differentiated Services Code Point (DSCP) values in the IPv4 header of your traffic to mark it for voice, video/interactive, or best-effort delivery. This is especially important for the Microsoft peering relationship and Skype for Business Online traffic.</span></span>
    
<span data-ttu-id="1ad8e-260">Дополнительные сведения см. в указанных ниже ресурсах.</span><span class="sxs-lookup"><span data-stu-id="1ad8e-260">See these additional resources for more information:</span></span>
  
- [<span data-ttu-id="1ad8e-261">ExpressRoute для Office 365</span><span class="sxs-lookup"><span data-stu-id="1ad8e-261">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
- [<span data-ttu-id="1ad8e-262">Azure ExpressRoute для обучения работе с Office 365</span><span class="sxs-lookup"><span data-stu-id="1ad8e-262">Azure ExpressRoute for Office 365 Training</span></span>](https://channel9.msdn.com/series/aer/)
    
- [<span data-ttu-id="1ad8e-263">ExpressRoute для Azure</span><span class="sxs-lookup"><span data-stu-id="1ad8e-263">ExpressRoute for Azure</span></span>](https://azure.microsoft.com/services/expressroute/)
    
## <a name="next-step"></a><span data-ttu-id="1ad8e-264">Следующее действие</span><span class="sxs-lookup"><span data-stu-id="1ad8e-264">Next step</span></span>

[<span data-ttu-id="1ad8e-265">Проектирование сети для Microsoft SaaS</span><span class="sxs-lookup"><span data-stu-id="1ad8e-265">Designing networking for Microsoft SaaS</span></span>](designing-networking-for-microsoft-saas.md)

## <a name="see-also"></a><span data-ttu-id="1ad8e-266">См. также</span><span class="sxs-lookup"><span data-stu-id="1ad8e-266">See also</span></span>

[<span data-ttu-id="1ad8e-267">Организация сети в Microsoft Cloud для корпоративных архитекторов</span><span class="sxs-lookup"><span data-stu-id="1ad8e-267">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="1ad8e-268">Ресурсы для администраторов, посвященные архитектуре Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="1ad8e-268">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="1ad8e-269">Стратегия Enterprise Cloud корпорации Майкрософт: ресурсы для лиц, принимающих решения в области ИТ</span><span class="sxs-lookup"><span data-stu-id="1ad8e-269">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



