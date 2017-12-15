---
title: "Подключение локальной сети к виртуальной сети Microsoft Azure"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
- Ent_O365_Hybrid_Top
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 81190961-5454-4a5c-8b0e-6ae75b9fb035
description: "Сводка. Узнайте, как настроить распределенную виртуальную сеть Azure для рабочих нагрузок Office Server."
ms.openlocfilehash: 83e5842a4b3192ee2f65048cefe57790cd1e2341
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="connect-an-on-premises-network-to-a-microsoft-azure-virtual-network"></a><span data-ttu-id="76477-103">Подключение локальной сети к виртуальной сети Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="76477-103">Connect an on-premises network to a Microsoft Azure virtual network</span></span>

 <span data-ttu-id="76477-104">**Сводка.** Узнайте, как настроить распределенную виртуальную сеть Azure для рабочих нагрузок Office Server.</span><span class="sxs-lookup"><span data-stu-id="76477-104">**Summary:** Learn how to configure a cross-premises Azure virtual network for Office server workloads.</span></span>
  
<span data-ttu-id="76477-p101">Виртуальная сеть Azure подключается к вашей локальной сети, расширяя ее за счет подсетей и виртуальных машин, размещенных в службах инфраструктуры Azure. Благодаря этому компьютеры в вашей локальной сети могут подключаться напрямую к виртуальным машинам Azure и наоборот. Например, серверу DirSync, запущенному на виртуальной машине Azure, требуется направить запрос контроллерам локального домена на изменение учетных записей, а также синхронизировать эти изменения с подпиской на Office 365. В этой статье описано, как настроить виртуальную сеть Azure для размещения в ней виртуальных машин Azure.</span><span class="sxs-lookup"><span data-stu-id="76477-p101">A cross-premises Azure virtual network is connected to your on-premises network, extending your network to include subnets and virtual machines hosted in Azure infrastructure services. This connection allows computers on your on-premises network to directly access virtual machines in Azure and vice versa. For example, a DirSync server running on an Azure virtual machine needs to query your on-premises domain controllers for changes to accounts and synchronize those changes with your Office 365 subscription. This article shows you how to set up a cross-premises Azure virtual network that is ready to host Azure virtual machines.</span></span>
  
<span data-ttu-id="76477-109">В этой статье</span><span class="sxs-lookup"><span data-stu-id="76477-109">In this article:</span></span>
  
- [<span data-ttu-id="76477-110">Общие сведения</span><span class="sxs-lookup"><span data-stu-id="76477-110">Overview</span></span>](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Overview)
    
- [<span data-ttu-id="76477-111">Планирование виртуальной сети Azure</span><span class="sxs-lookup"><span data-stu-id="76477-111">Plan your Azure virtual network</span></span>](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#PlanningVirtual)
    
- [<span data-ttu-id="76477-112">Схема развертывания</span><span class="sxs-lookup"><span data-stu-id="76477-112">Deployment roadmap</span></span>](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#DeploymentRoadmap)
    
## <a name="overview"></a><span data-ttu-id="76477-113">Общие сведения</span><span class="sxs-lookup"><span data-stu-id="76477-113">Overview</span></span>
<span data-ttu-id="76477-114"><a name="Overview"> </a></span><span class="sxs-lookup"><span data-stu-id="76477-114"><a name="Overview"> </a></span></span>

<span data-ttu-id="76477-p102">Виртуальные машины в Azure не должны быть изолированы от локальной среды. Чтобы подключить виртуальные машины Azure к локальным сетевым ресурсам, необходимо настроить виртуальную сеть Azure. На схеме ниже показаны компоненты, необходимые для развертывания виртуальной сети Azure с виртуальной машиной в Azure.</span><span class="sxs-lookup"><span data-stu-id="76477-p102">Your virtual machines in Azure don't have to be isolated from your on-premises environment. To connect Azure virtual machines to your on-premises network resources, you must configure a cross-premises Azure virtual network. The following diagram shows the required components to deploy a cross-premises Azure virtual network with a virtual machine in Azure.</span></span>
  
![Локальная сеть подключена к Microsoft Azure с помощью VPN-подключения типа "сеть-сеть"](images/CP_ConnectOnPremisesNetworkToAzureVPN.png)
  
<span data-ttu-id="76477-p103">На схеме локальная сеть и виртуальная сеть Azure подключены друг к другу с помощью VPN-подключения типа "сеть-сеть". Это подключение прерывается VPN-устройством в локальной сети и VPN-шлюзом Azure в виртуальной сети Azure. В виртуальной сети Azure есть виртуальные машины. Сетевой трафик с виртуальных машин в виртуальной сети Azure направляется на VPN-шлюз, который затем направляет трафик по VPN-подключению типа "сеть-сеть" на VPN-устройство в локальной сети. Далее инфраструктура маршрутизации локальной сети направляет трафик по назначению.</span><span class="sxs-lookup"><span data-stu-id="76477-p103">In the diagram, there are two networks connected by a site-to-site virtual private network (VPN) connection: the on-premises network and the Azure virtual network. The site-to-site VPN connection is terminated by a VPN device on the on-premises network and an Azure VPN gateway on the Azure virtual network. The Azure virtual network has virtual machines. Network traffic originating from virtual machines on the Azure virtual network gets forwarded to the VPN gateway, which then forwards the traffic across the site-to-site VPN connection to the VPN device on the on-premises network. The routing infrastructure of the on-premises network then forwards the traffic to its destination.</span></span>
  
<span data-ttu-id="76477-124">Чтобы настроить VPN-подключение между виртуальной сетью Azure и локальной сетью, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="76477-124">To set up the VPN connection between your Azure virtual network and your on-premises network, do the following steps:</span></span> 
  
1. <span data-ttu-id="76477-125">**Локальная сеть.** Определите и создайте локальный сетевой маршрут для адресного пространства виртуальной сети Azure, который указывает на локальное VPN-устройство.</span><span class="sxs-lookup"><span data-stu-id="76477-125">**On-premises:** Define and create an on-premises network route for the address space of the Azure virtual network that points to your on-premises VPN device.</span></span>
    
2. <span data-ttu-id="76477-p104">**Microsoft Azure:** Создайте Azure виртуальной сети с помощью VPN-подключения веб сайта. В этой статье не рассматриваются использование [ExpressRoute](https://azure.microsoft.com/services/expressroute/).</span><span class="sxs-lookup"><span data-stu-id="76477-p104">**Microsoft Azure:** Create an Azure virtual network with a site-to-site VPN connection. This article does not describe the use of [ExpressRoute](https://azure.microsoft.com/services/expressroute/).</span></span>
    
3. <span data-ttu-id="76477-128">**Локальная сеть.** Настройте аппаратное или программное локальное VPN-устройство для прерывания VPN-подключения, которое использует IPsec.</span><span class="sxs-lookup"><span data-stu-id="76477-128">**On premises:** Configure your on-premises hardware or software VPN device to terminate the VPN connection, which uses Internet Protocol security (IPsec).</span></span>
    
<span data-ttu-id="76477-129">После установки VPN-подключения типа "сеть-сеть" добавьте виртуальные машины Azure в подсети виртуальной сети.</span><span class="sxs-lookup"><span data-stu-id="76477-129">After you establish the site-to-site VPN connection, you add Azure virtual machines to the subnets of the virtual network.</span></span>
  
## <a name="plan-your-azure-virtual-network"></a><span data-ttu-id="76477-130">Планирование виртуальной сети Azure</span><span class="sxs-lookup"><span data-stu-id="76477-130">Plan your Azure virtual network</span></span>
<span data-ttu-id="76477-131"><a name="PlanningVirtual"> </a></span><span class="sxs-lookup"><span data-stu-id="76477-131"><a name="PlanningVirtual"> </a></span></span>

### <a name="prerequisites"></a><span data-ttu-id="76477-132">Требования</span><span class="sxs-lookup"><span data-stu-id="76477-132">Prerequisites</span></span>
<span data-ttu-id="76477-133"><a name="Prerequisites"> </a></span><span class="sxs-lookup"><span data-stu-id="76477-133"><a name="Prerequisites"> </a></span></span>

- <span data-ttu-id="76477-p105">Подписка на Azure. Сведения о подписках на Azure см. на [странице подписки на Microsoft Azure](https://azure.microsoft.com/pricing/purchase-options/).</span><span class="sxs-lookup"><span data-stu-id="76477-p105">An Azure subscription. For information about Azure subscriptions, go to the [Microsoft Azure subscription page](https://azure.microsoft.com/pricing/purchase-options/).</span></span>
    
- <span data-ttu-id="76477-136">Доступное частное пространство IPv4-адресов, которое необходимо назначить виртуальной сети и ее подсетям, с достаточным количеством адресов с учетом возможного расширения.</span><span class="sxs-lookup"><span data-stu-id="76477-136">An available private IPv4 address space to assign to the virtual network and its subnets, with sufficient room for growth to accommodate the number of virtual machines needed now and in the future.</span></span>
    
- <span data-ttu-id="76477-p106">Доступное VPN-устройство в локальной сети для прерывания VPN-подключения типа "сеть-сеть", которое поддерживает требования для IPsec. Дополнительные сведения см. в статье [О VPN-устройствах для подключений VPN-шлюзов типа "сеть-сеть"](https://go.microsoft.com/fwlink/p/?LinkId=393093).</span><span class="sxs-lookup"><span data-stu-id="76477-p106">An available VPN device in your on-premises network to terminate the site-to-site VPN connection that supports the requirements for IPsec. For more information, see [About VPN devices for site-to-site virtual network connections](https://go.microsoft.com/fwlink/p/?LinkId=393093).</span></span>
    
- <span data-ttu-id="76477-139">Изменение инфраструктуры маршрутизации для перенаправления трафика, поступающего в адресное пространство виртуальной сети Azure, на VPN-устройство, которое принимает VPN-подключение типа "сеть-сеть".</span><span class="sxs-lookup"><span data-stu-id="76477-139">Changes to your routing infrastructure so that traffic routed to the address space of the Azure virtual network gets forwarded to the VPN device that hosts the site-to-site VPN connection.</span></span>
    
- <span data-ttu-id="76477-140">Веб-прокси, который предоставляет доступ в Интернет компьютерам, подключенным к локальной сети и виртуальной сети Azure.</span><span class="sxs-lookup"><span data-stu-id="76477-140">A web proxy that gives computers that are connected to the on-premises network and the Azure virtual network access to the Internet.</span></span>
    
### <a name="solution-architecture-design-assumptions"></a><span data-ttu-id="76477-141">Допущения по архитектуре решения</span><span class="sxs-lookup"><span data-stu-id="76477-141">Solution architecture design assumptions</span></span>
<span data-ttu-id="76477-142"><a name="DesignAssumptions"> </a></span><span class="sxs-lookup"><span data-stu-id="76477-142"><a name="DesignAssumptions"> </a></span></span>

<span data-ttu-id="76477-143">Ниже перечислены проектные решения для этой архитектуры.</span><span class="sxs-lookup"><span data-stu-id="76477-143">The following list represents the design choices that have been made for this solution architecture.</span></span> 
  
- <span data-ttu-id="76477-p107">Это решение использует одну виртуальную сеть Azure с VPN-подключением типа "сеть-сеть". В виртуальной сети Azure размещается одна подсеть, которая может содержать несколько виртуальных машин.</span><span class="sxs-lookup"><span data-stu-id="76477-p107">This solution uses a single Azure virtual network with a site-to-site VPN connection. The Azure virtual network hosts a single subnet that can contain multiple virtual machines.</span></span> 
    
- <span data-ttu-id="76477-p108">Вы можете использовать службу RRAS в Windows Server 2016 или Windows Server 2012, чтобы установить VPN-подключение типа "сеть-сеть" с защитой IPsec между локальной сетью и виртуальной сетью Azure. Вы также можете использовать другие VPN-устройства, например Cisco или Juniper Networks.</span><span class="sxs-lookup"><span data-stu-id="76477-p108">You can use the Routing and Remote Access Service (RRAS) in Windows Server 2016 or Windows Server 2012 to establish an IPsec site-to-site VPN connection between the on-premises network and the Azure virtual network. You can also use other options, such as Cisco or Juniper Networks VPN devices.</span></span>
    
- <span data-ttu-id="76477-p109">В локальной сети по-прежнему могут размещаться сетевые службы, такие как Windows Server Active Directory (AD), служба доменных имен (DNS), и прокси-серверы. В зависимости от ваших требований, некоторые из этих сетевых ресурсов может быть удобнее разместить в виртуальной сети Azure.</span><span class="sxs-lookup"><span data-stu-id="76477-p109">The on-premises network might still have network services like Windows Server Active Directory (AD), Domain Name System (DNS), and proxy servers. Depending on your requirements, it might be beneficial to place some of these network resources in the Azure virtual network.</span></span>
    
<span data-ttu-id="76477-p110">Для существующей виртуальной сети Azure с одной или несколькими подсетями определите, осталось ли адресное пространство для дополнительной подсети и размещения необходимых виртуальных машин, учитывая ваши требования. Если адресного пространства для дополнительной подсети не осталось, создайте дополнительную виртуальную сеть с собственным VPN-подключением типа "сеть-сеть".</span><span class="sxs-lookup"><span data-stu-id="76477-p110">For an existing Azure virtual network with one or more subnets, determine whether there is remaining address space for an additional subnet to host your needed virtual machines, based on your requirements. If you don't have remaining address space for an additional subnet, create an additional virtual network that has its own site-to-site VPN connection.</span></span>
  
### <a name="plan-the-routing-infrastructure-changes-for-the-azure-virtual-network"></a><span data-ttu-id="76477-152">Планирование изменения инфраструктуры маршрутизации для виртуальной сети Azure</span><span class="sxs-lookup"><span data-stu-id="76477-152">Plan the routing infrastructure changes for the Azure virtual network</span></span>
<span data-ttu-id="76477-153"><a name="routing"> </a></span><span class="sxs-lookup"><span data-stu-id="76477-153"><a name="routing"> </a></span></span>

<span data-ttu-id="76477-154">Локальную инфраструктуру маршрутизации необходимо настроить так, чтобы трафик, поступающий в пространство адресов виртуальной сети Azure, направлялся в локальное VPN-устройство с VPN-подключением типа "сеть-сеть".</span><span class="sxs-lookup"><span data-stu-id="76477-154">You must configure your on-premises routing infrastructure to forward traffic destined for the address space of the Azure virtual network to the on-premises VPN device that is hosting the site-to-site VPN connection.</span></span>
  
<span data-ttu-id="76477-155">Конкретный метод обновления инфраструктуры маршрутизации зависит от того, как выполняется управление сведениями о маршрутизации, например:</span><span class="sxs-lookup"><span data-stu-id="76477-155">The exact method of updating your routing infrastructure depends on how you manage routing information, which can be:</span></span>
  
- <span data-ttu-id="76477-156">таблица маршрутизации обновляется в соответствии с ручной настройкой;</span><span class="sxs-lookup"><span data-stu-id="76477-156">Routing table updates based on manual configuration.</span></span>
    
- <span data-ttu-id="76477-157">таблица маршрутизации обновляется в соответствии с протоколами маршрутизации, например RIP или OSPF.</span><span class="sxs-lookup"><span data-stu-id="76477-157">Routing table updates based on routing protocols, such as Routing Information Protocol (RIP) or Open Shortest Path First (OSPF).</span></span>
    
<span data-ttu-id="76477-158">Проконсультируйтесь со своим специалистом по маршрутизации, чтобы убедиться, что трафик, предназначенный для виртуальной сети Azure, перенаправляется на локальное VPN-устройство.</span><span class="sxs-lookup"><span data-stu-id="76477-158">Consult with your routing specialist to make sure that traffic destined for the Azure virtual network is forwarded to the on-premises VPN device.</span></span>
  
### <a name="plan-for-firewall-rules-for-traffic-to-and-from-the-on-premises-vpn-device"></a><span data-ttu-id="76477-159">Планирование правил брандмауэра для входящего и исходящего трафика на локальном VPN-устройстве</span><span class="sxs-lookup"><span data-stu-id="76477-159">Plan for firewall rules for traffic to and from the on-premises VPN device</span></span>
<span data-ttu-id="76477-160"><a name="firewall"> </a></span><span class="sxs-lookup"><span data-stu-id="76477-160"><a name="firewall"> </a></span></span>

<span data-ttu-id="76477-161">Если VPN-устройство размещается в сети периметра, которая соединяется с Интернетом через брандмауэр, рекомендуем настроить на брандмауэре перечисленные ниже правила, чтобы сделать возможным VPN-подключение типа "сеть-сеть".</span><span class="sxs-lookup"><span data-stu-id="76477-161">If your VPN device is on a perimeter network that has a firewall between the perimeter network and the Internet, you might have to configure the firewall for the following rules to allow the site-to-site VPN connection.</span></span>
  
- <span data-ttu-id="76477-162">Трафик к VPN-устройству (входящий):</span><span class="sxs-lookup"><span data-stu-id="76477-162">Traffic to the VPN device (incoming from the Internet):</span></span>
    
  - <span data-ttu-id="76477-163">Конечный IP-адрес VPN-устройства и протокол IP 50</span><span class="sxs-lookup"><span data-stu-id="76477-163">Destination IP address of the VPN device and IP protocol 50</span></span>
    
  - <span data-ttu-id="76477-164">Конечный IP-адрес VPN-устройства и конечный порт UDP 500</span><span class="sxs-lookup"><span data-stu-id="76477-164">Destination IP address of the VPN device and UDP destination port 500</span></span>
    
  - <span data-ttu-id="76477-165">Конечный IP-адрес VPN-устройства и конечный порт UDP 4500</span><span class="sxs-lookup"><span data-stu-id="76477-165">Destination IP address of the VPN device and UDP destination port 4500</span></span>
    
- <span data-ttu-id="76477-166">Трафик с VPN-устройства (исходящий):</span><span class="sxs-lookup"><span data-stu-id="76477-166">Traffic from the VPN device (outgoing to the Internet):</span></span>
    
  - <span data-ttu-id="76477-167">Исходный IP-адрес VPN-устройства и протокол IP 50</span><span class="sxs-lookup"><span data-stu-id="76477-167">Source IP address of the VPN device and IP protocol 50</span></span>
    
  - <span data-ttu-id="76477-168">Исходный IP-адрес VPN-устройства и исходный порт UDP 500</span><span class="sxs-lookup"><span data-stu-id="76477-168">Source IP address of the VPN device and UDP source port 500</span></span>
    
  - <span data-ttu-id="76477-169">Исходный IP-адрес VPN-устройства и исходный порт UDP 4500</span><span class="sxs-lookup"><span data-stu-id="76477-169">Source IP address of the VPN device and UDP source port 4500</span></span>
    
### <a name="plan-for-the-private-ip-address-space-of-the-azure-virtual-network"></a><span data-ttu-id="76477-170">Планирование пространства частных IP-адресов виртуальной сети Azure</span><span class="sxs-lookup"><span data-stu-id="76477-170">Plan for the private IP address space of the Azure virtual network</span></span>
<span data-ttu-id="76477-171"><a name="IPAddresses"> </a></span><span class="sxs-lookup"><span data-stu-id="76477-171"><a name="IPAddresses"> </a></span></span>

<span data-ttu-id="76477-172">Пространство частных IP-адресов виртуальной сети Azure должно иметь достаточный размер для адресов, используемых платформой Azure для размещения виртуальной сети как минимум с одной подсетью, в которой достаточно адресов для размещения виртуальных машин Azure.</span><span class="sxs-lookup"><span data-stu-id="76477-172">The private IP address space of the Azure virtual network must be able to accommodate addresses used by Azure to host the virtual network and with at least one subnet that has enough addresses for your Azure virtual machines.</span></span>
  
<span data-ttu-id="76477-173">Чтобы определить необходимое количество адресов для подсети, посчитайте количество виртуальных машин, необходимых на данный момент, оцените потенциал роста и определите размер подсети, пользуясь следующей таблицей.</span><span class="sxs-lookup"><span data-stu-id="76477-173">To determine the number of addresses needed for the subnet, count the number of virtual machines that you need now, estimate for future growth, and then use the following table to determine the size of the subnet.</span></span>
  
|<span data-ttu-id="76477-174">**Необходимое количество виртуальных машин**</span><span class="sxs-lookup"><span data-stu-id="76477-174">**Number of virtual machines needed**</span></span>|<span data-ttu-id="76477-175">**Необходимое количество бит узла**</span><span class="sxs-lookup"><span data-stu-id="76477-175">**Number of host bits needed**</span></span>|<span data-ttu-id="76477-176">**Размер подсети**</span><span class="sxs-lookup"><span data-stu-id="76477-176">**Size of the subnet**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="76477-177">1-3</span><span class="sxs-lookup"><span data-stu-id="76477-177">1-3</span></span>  <br/> |<span data-ttu-id="76477-178">3</span><span class="sxs-lookup"><span data-stu-id="76477-178">3</span></span>  <br/> |<span data-ttu-id="76477-179">/29</span><span class="sxs-lookup"><span data-stu-id="76477-179">/29</span></span>  <br/> |
|<span data-ttu-id="76477-180">4-11</span><span class="sxs-lookup"><span data-stu-id="76477-180">4-11</span></span>  <br/> |<span data-ttu-id="76477-181">4</span><span class="sxs-lookup"><span data-stu-id="76477-181">4</span></span>  <br/> |<span data-ttu-id="76477-182">/28</span><span class="sxs-lookup"><span data-stu-id="76477-182">/28</span></span>  <br/> |
|<span data-ttu-id="76477-183">12-27</span><span class="sxs-lookup"><span data-stu-id="76477-183">12-27</span></span>  <br/> |<span data-ttu-id="76477-184">5</span><span class="sxs-lookup"><span data-stu-id="76477-184">5</span></span>  <br/> |<span data-ttu-id="76477-185">/27</span><span class="sxs-lookup"><span data-stu-id="76477-185">/27</span></span>  <br/> |
|<span data-ttu-id="76477-186">28-59</span><span class="sxs-lookup"><span data-stu-id="76477-186">28-59</span></span>  <br/> |<span data-ttu-id="76477-187">6</span><span class="sxs-lookup"><span data-stu-id="76477-187">6</span></span>  <br/> |<span data-ttu-id="76477-188">/26</span><span class="sxs-lookup"><span data-stu-id="76477-188">/26</span></span>  <br/> |
|<span data-ttu-id="76477-189">60-123</span><span class="sxs-lookup"><span data-stu-id="76477-189">60-123</span></span>  <br/> |<span data-ttu-id="76477-190">7</span><span class="sxs-lookup"><span data-stu-id="76477-190">7</span></span>  <br/> |<span data-ttu-id="76477-191">/25</span><span class="sxs-lookup"><span data-stu-id="76477-191">/25</span></span>  <br/> |
   
### <a name="planning-worksheet-for-configuring-your-azure-virtual-network"></a><span data-ttu-id="76477-192">Таблица планирования настройки виртуальной сети Azure</span><span class="sxs-lookup"><span data-stu-id="76477-192">Planning worksheet for configuring your Azure virtual network</span></span>
<span data-ttu-id="76477-193"><a name="worksheet"> </a></span><span class="sxs-lookup"><span data-stu-id="76477-193"><a name="worksheet"> </a></span></span>

<span data-ttu-id="76477-194">Прежде чем создавать виртуальную сеть Azure для размещения виртуальных машин, необходимо определить нужные параметры в следующих таблицах.</span><span class="sxs-lookup"><span data-stu-id="76477-194">Before you create an Azure virtual network to host virtual machines, you must determine the settings needed in the following tables.</span></span>
  
<span data-ttu-id="76477-195">Чтобы задать параметры виртуальной сети, заполните таблицу V.</span><span class="sxs-lookup"><span data-stu-id="76477-195">For the settings of the virtual network, fill in Table V.</span></span>
  
 <span data-ttu-id="76477-196">**Таблица V. Настройка распределенной виртуальной сети**</span><span class="sxs-lookup"><span data-stu-id="76477-196">**Table V: Cross-premises virtual network configuration**</span></span>
  
|<span data-ttu-id="76477-197">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="76477-197">**Item**</span></span>|<span data-ttu-id="76477-198">**Элемент Configuration**</span><span class="sxs-lookup"><span data-stu-id="76477-198">**Configuration element**</span></span>|<span data-ttu-id="76477-199">**Описание**</span><span class="sxs-lookup"><span data-stu-id="76477-199">**Description**</span></span>|<span data-ttu-id="76477-200">**Значение**</span><span class="sxs-lookup"><span data-stu-id="76477-200">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="76477-201">1.</span><span class="sxs-lookup"><span data-stu-id="76477-201">1.</span></span>  <br/> |<span data-ttu-id="76477-202">Имя виртуальной сети</span><span class="sxs-lookup"><span data-stu-id="76477-202">Virtual network name</span></span>  <br/> |<span data-ttu-id="76477-203">Имя, назначаемое виртуальной сети Azure (например, DirSyncNet).</span><span class="sxs-lookup"><span data-stu-id="76477-203">A name to assign to the Azure virtual network (example DirSyncNet).</span></span>  <br/> |<span data-ttu-id="76477-204">__________________</span><span class="sxs-lookup"><span data-stu-id="76477-204">__________________</span></span>  <br/> |
|<span data-ttu-id="76477-205">2.</span><span class="sxs-lookup"><span data-stu-id="76477-205">2.</span></span>  <br/> |<span data-ttu-id="76477-206">Расположение виртуальной сети</span><span class="sxs-lookup"><span data-stu-id="76477-206">Virtual network location</span></span>  <br/> |<span data-ttu-id="76477-207">Центр обработки данных Azure, в котором будет расположена виртуальная сеть (например, Запад США).</span><span class="sxs-lookup"><span data-stu-id="76477-207">The Azure datacenter that will contain the virtual network (such as West US).</span></span>  <br/> |<span data-ttu-id="76477-208">__________________</span><span class="sxs-lookup"><span data-stu-id="76477-208">__________________</span></span>  <br/> |
|<span data-ttu-id="76477-209">3.</span><span class="sxs-lookup"><span data-stu-id="76477-209">3.</span></span>  <br/> |<span data-ttu-id="76477-210">IP-адрес VPN-устройства</span><span class="sxs-lookup"><span data-stu-id="76477-210">VPN device IP address</span></span>  <br/> |<span data-ttu-id="76477-p111">Общедоступный IPv4-адрес интерфейса VPN-устройства в Интернете. Определите этот адрес при поддержке ИТ-отдела.</span><span class="sxs-lookup"><span data-stu-id="76477-p111">The public IPv4 address of your VPN device's interface on the Internet. Work with your IT department to determine this address.</span></span>  <br/> |<span data-ttu-id="76477-213">__________________</span><span class="sxs-lookup"><span data-stu-id="76477-213">__________________</span></span>  <br/> |
|<span data-ttu-id="76477-214">4.</span><span class="sxs-lookup"><span data-stu-id="76477-214">4.</span></span>  <br/> |<span data-ttu-id="76477-215">Адресное пространство виртуальной сети</span><span class="sxs-lookup"><span data-stu-id="76477-215">Virtual network address space</span></span>  <br/> |<span data-ttu-id="76477-p112">Адресное пространство (определенное в одном префиксе личного адреса) для виртуальной сети. Определите это адресное пространство при поддержке ИТ-отдела. Оно должно быть представлено в формате CIDR, также известном как формат префикса сети. Пример: 10.24.64.0/20.</span><span class="sxs-lookup"><span data-stu-id="76477-p112">The address space (defined in a single private address prefix) for the virtual network. Work with your IT department to determine this address space. The address space should be in Classless Interdomain Routing (CIDR) format, also known as network prefix format. An example is 10.24.64.0/20.</span></span>  <br/> |<span data-ttu-id="76477-220">__________________</span><span class="sxs-lookup"><span data-stu-id="76477-220">__________________</span></span>  <br/> |
|<span data-ttu-id="76477-221">5.</span><span class="sxs-lookup"><span data-stu-id="76477-221">5.</span></span>  <br/> |<span data-ttu-id="76477-222">Общий ключ IPsec</span><span class="sxs-lookup"><span data-stu-id="76477-222">IPsec shared key</span></span>  <br/> |<span data-ttu-id="76477-p113">32-значный случайный буквенно-цифровой ключ, который будет использоваться для проверки подлинности обеих сторон VPN-подключения. Определите значение этого ключа при поддержке ИТ-отдела, а затем сохраните его в надежном месте. Вы также можете ознакомиться со статьей [Создание случайной строки для предварительного ключа IPsec](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).</span><span class="sxs-lookup"><span data-stu-id="76477-p113">A 32-character random, alphanumeric string that will be used to authenticate both sides of the site-to-site VPN connection. Work with your IT or security department to determine this key value and then store it in a secure location. Alternately, see [Create a random string for an IPsec preshared key](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  </span></span><br/> |<span data-ttu-id="76477-226">__________________</span><span class="sxs-lookup"><span data-stu-id="76477-226">__________________</span></span>  <br/> |
   
<span data-ttu-id="76477-227">Заполните таблицу S для подсетей этого решения.</span><span class="sxs-lookup"><span data-stu-id="76477-227">Fill in Table S for the subnets of this solution.</span></span>
  
- <span data-ttu-id="76477-p114">Для первой подсети определите 28-битовое адресное пространство (с длиной префикса /28) подсети шлюза Azure. Сведения о том, как определить это адресное пространство, см. в статье [Расчет адресного пространства подсетей шлюза для виртуальных сетей Azure](https://blogs.technet.microsoft.com/solutions_advisory_board/2016/12/01/calculating-the-gateway-subnet-address-space-for-azure-virtual-networks/).</span><span class="sxs-lookup"><span data-stu-id="76477-p114">For the first subnet, determine a 28-bit address space (with a /28 prefix length) for the Azure gateway subnet. See [Calculating the gateway subnet address space for Azure virtual networks](https://blogs.technet.microsoft.com/solutions_advisory_board/2016/12/01/calculating-the-gateway-subnet-address-space-for-azure-virtual-networks/) for information about how to determine this address space.</span></span>
    
- <span data-ttu-id="76477-230">Для второй подсети укажите понятное имя, одно пространство IP-адресов на основе адресного пространства виртуальной сети.</span><span class="sxs-lookup"><span data-stu-id="76477-230">For the second subnet, specify a friendly name, a single IP address space based on the virtual network address space, and a descriptive purpose.</span></span>
    
<span data-ttu-id="76477-p115">Определите эти адресные пространства из адресного пространства виртуальной сети при поддержке ИТ-отдела. Оба адресных пространства должны быть представлены в формате CIDR.</span><span class="sxs-lookup"><span data-stu-id="76477-p115">Work with your IT department to determine these address spaces from the virtual network address space. Both address spaces should be in CIDR format.</span></span>
  
 <span data-ttu-id="76477-233">**Таблица S. Подсети виртуальной сети**</span><span class="sxs-lookup"><span data-stu-id="76477-233">**Table S: Subnets in the virtual network**</span></span>
  
|<span data-ttu-id="76477-234">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="76477-234">**Item**</span></span>|<span data-ttu-id="76477-235">**Имя подсети**</span><span class="sxs-lookup"><span data-stu-id="76477-235">**Subnet name**</span></span>|<span data-ttu-id="76477-236">**Адресное пространство подсети**</span><span class="sxs-lookup"><span data-stu-id="76477-236">**Subnet address space**</span></span>|<span data-ttu-id="76477-237">**Назначение**</span><span class="sxs-lookup"><span data-stu-id="76477-237">**Purpose**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="76477-238">1.</span><span class="sxs-lookup"><span data-stu-id="76477-238">1.</span></span>  <br/> |<span data-ttu-id="76477-239">GatewaySubnet</span><span class="sxs-lookup"><span data-stu-id="76477-239">GatewaySubnet</span></span>  <br/> |<span data-ttu-id="76477-240">_____________________________</span><span class="sxs-lookup"><span data-stu-id="76477-240">_____________________________</span></span>  <br/> |<span data-ttu-id="76477-241">Подсеть, используемая шлюзом Azure.</span><span class="sxs-lookup"><span data-stu-id="76477-241">The subnet used by the Azure gateway.</span></span>  <br/> |
|<span data-ttu-id="76477-242">2.</span><span class="sxs-lookup"><span data-stu-id="76477-242">2.</span></span>  <br/> |<span data-ttu-id="76477-243">_____________________________</span><span class="sxs-lookup"><span data-stu-id="76477-243">_____________________________</span></span>  <br/> |<span data-ttu-id="76477-244">_____________________________</span><span class="sxs-lookup"><span data-stu-id="76477-244">_____________________________</span></span>  <br/> |<span data-ttu-id="76477-245">_____________________________</span><span class="sxs-lookup"><span data-stu-id="76477-245">_____________________________</span></span>  <br/> |
   
<span data-ttu-id="76477-p116">Для локальных DNS-серверов, используемых виртуальными машинами в виртуальной сети, заполните таблицу D. Присвойте каждому DNS-серверу понятное имя и один IP-адрес. Это понятное имя необязательно должно совпадать с именем узла или именем компьютера на DNS-сервере. Обратите внимание, что представлено два пустых поля, но вы можете добавить еще. Определите этот список при поддержке ИТ-отдела.</span><span class="sxs-lookup"><span data-stu-id="76477-p116">For the on-premises DNS servers that you want the virtual machines in the virtual network to use, fill in Table D. Give each DNS server a friendly name and a single IP address. This friendly name does not need to match the host name or computer name of the DNS server. Note that two blank entries are listed, but you can add more. Work with your IT department to determine this list.</span></span>
  
 <span data-ttu-id="76477-250">**Таблица D. Локальные DNS-сервера**</span><span class="sxs-lookup"><span data-stu-id="76477-250">**Table D: On-premises DNS servers**</span></span>
  
|<span data-ttu-id="76477-251">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="76477-251">**Item**</span></span>|<span data-ttu-id="76477-252">**Понятное имя DNS-сервера**</span><span class="sxs-lookup"><span data-stu-id="76477-252">**DNS server friendly name**</span></span>|<span data-ttu-id="76477-253">**IP-адрес DNS-сервера**</span><span class="sxs-lookup"><span data-stu-id="76477-253">**DNS server IP address**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="76477-254">1.</span><span class="sxs-lookup"><span data-stu-id="76477-254">1.</span></span>  <br/> |<span data-ttu-id="76477-255">_____________________________</span><span class="sxs-lookup"><span data-stu-id="76477-255">_____________________________</span></span>  <br/> |<span data-ttu-id="76477-256">_____________________________</span><span class="sxs-lookup"><span data-stu-id="76477-256">_____________________________</span></span>  <br/> |
|<span data-ttu-id="76477-257">2.</span><span class="sxs-lookup"><span data-stu-id="76477-257">2.</span></span>  <br/> |<span data-ttu-id="76477-258">_____________________________</span><span class="sxs-lookup"><span data-stu-id="76477-258">_____________________________</span></span>  <br/> |<span data-ttu-id="76477-259">_____________________________</span><span class="sxs-lookup"><span data-stu-id="76477-259">_____________________________</span></span>  <br/> |
   
<span data-ttu-id="76477-p117">Чтобы отправлять пакеты из виртуальной сети Azure в сеть организации с помощью VPN-подключения типа "сеть-сеть", необходимо настроить виртуальную сеть с локальной сетью. Эта локальная сеть содержит список адресных пространств (в формате CIDR) для всех расположений в локальной сети организации, которые должны быть доступны виртуальным машинам в виртуальной сети. Это могут быть все расположения в локальной сети или подсети. Список адресных пространств, которые определяют локальную сеть, должен быть уникален и не должен пересекаться с адресными пространствами, используемыми для этой или других виртуальных сетей.</span><span class="sxs-lookup"><span data-stu-id="76477-p117">To route packets from the Azure virtual network to your organization network across the site-to-site VPN connection, you must configure the virtual network with a local network. This local network contains a list of the address spaces (in CIDR format) for all of the locations on your organization's on-premises network that the virtual machines in the virtual network must reach. This can be all of the locations on the on-premises network or a subset. The list of address spaces that define your local network must be unique and must not overlap with the address spaces used for this virtual network or your other cross-premises virtual networks.</span></span>
  
<span data-ttu-id="76477-p118">Укажите список адресных пространств локальной сети в таблице L. Обратите внимание, что представлено три пустых поля, но обычно требуется больше. Определите этот список при поддержке ИТ-отдела.</span><span class="sxs-lookup"><span data-stu-id="76477-p118">For the set of local network address spaces, fill in Table L. Note that three blank entries are listed but you will typically need more. Work with your IT department to determine this list.</span></span>
  
 <span data-ttu-id="76477-266">**Таблица L. Префиксы адресов для локальной сети**</span><span class="sxs-lookup"><span data-stu-id="76477-266">**Table L: Address prefixes for the local network**</span></span>
  
|<span data-ttu-id="76477-267">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="76477-267">**Item**</span></span>|<span data-ttu-id="76477-268">**Адресное пространство локальной сети**</span><span class="sxs-lookup"><span data-stu-id="76477-268">**Local network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="76477-269">1.</span><span class="sxs-lookup"><span data-stu-id="76477-269">1.</span></span>  <br/> |<span data-ttu-id="76477-270">_____________________________</span><span class="sxs-lookup"><span data-stu-id="76477-270">_____________________________</span></span>  <br/> |
|<span data-ttu-id="76477-271">2.</span><span class="sxs-lookup"><span data-stu-id="76477-271">2.</span></span>  <br/> |<span data-ttu-id="76477-272">_____________________________</span><span class="sxs-lookup"><span data-stu-id="76477-272">_____________________________</span></span>  <br/> |
|<span data-ttu-id="76477-273">3.</span><span class="sxs-lookup"><span data-stu-id="76477-273">3.</span></span>  <br/> |<span data-ttu-id="76477-274">_____________________________</span><span class="sxs-lookup"><span data-stu-id="76477-274">_____________________________</span></span>  <br/> |
   
## <a name="deployment-roadmap"></a><span data-ttu-id="76477-275">Схема развертывания</span><span class="sxs-lookup"><span data-stu-id="76477-275">Deployment roadmap</span></span>
<span data-ttu-id="76477-276"><a name="DeploymentRoadmap"> </a></span><span class="sxs-lookup"><span data-stu-id="76477-276"><a name="DeploymentRoadmap"> </a></span></span>

<span data-ttu-id="76477-277">Создание виртуальной сети и добавление виртуальных машин в Azure состоит из трех этапов:</span><span class="sxs-lookup"><span data-stu-id="76477-277">Creating the cross-premises virtual network and adding virtual machines in Azure consists of three phases:</span></span>
  
- <span data-ttu-id="76477-278">Этап 1. Подготовка локальной сети.</span><span class="sxs-lookup"><span data-stu-id="76477-278">Phase 1: Prepare your on-premises network.</span></span>
    
- <span data-ttu-id="76477-279">Этап 2. Создание виртуальной сети в Azure.</span><span class="sxs-lookup"><span data-stu-id="76477-279">Phase 2: Create the cross-premises virtual network in Azure.</span></span>
    
- <span data-ttu-id="76477-280">Этап 3 (необязательный). Добавление виртуальных машин.</span><span class="sxs-lookup"><span data-stu-id="76477-280">Phase 3 (Optional): Add virtual machines.</span></span>
    
### <a name="phase-1-prepare-your-on-premises-network"></a><span data-ttu-id="76477-281">Этап 1. Подготовка локальной сети</span><span class="sxs-lookup"><span data-stu-id="76477-281">Phase 1: Prepare your on-premises network</span></span>
<span data-ttu-id="76477-282"><a name="Phase1"> </a></span><span class="sxs-lookup"><span data-stu-id="76477-282"><a name="Phase1"> </a></span></span>

<span data-ttu-id="76477-p119">В локальной сети необходимо настроить маршрут, который указывает на маршрутизатор на границе локальной сети и направляет на него трафик, предназначенный для адресного пространства виртуальной сети. Обратитесь к администратору сети, чтобы определить, как добавить маршрут в инфраструктуру локальной сети.</span><span class="sxs-lookup"><span data-stu-id="76477-p119">You must configure your on-premises network with a route that points to and ultimately delivers traffic destined for the address space of the virtual network to the router on the edge of the on-premises network. Consult with your network administrator to determine how to add the route to the routing infrastructure of your on-premises network.</span></span>
  
<span data-ttu-id="76477-285">Ниже показана итоговая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="76477-285">Here is your resulting configuration.</span></span>
  
![Локальная сеть должна иметь маршрут для адресного пространства виртуальной сети, указывающий на VPN-устройство.](images/90bab36b-cb60-4ea5-81d5-4737b696d41c.png)
  
### <a name="phase-2-create-the-cross-premises-virtual-network-in-azure"></a><span data-ttu-id="76477-287">Этап 2. Создание распределенной виртуальной сети в Azure</span><span class="sxs-lookup"><span data-stu-id="76477-287">Phase 2: Create the cross-premises virtual network in Azure</span></span>
<span data-ttu-id="76477-288"><a name="Phase2"> </a></span><span class="sxs-lookup"><span data-stu-id="76477-288"><a name="Phase2"> </a></span></span>

<span data-ttu-id="76477-p120">Сначала откройте командную строку Azure PowerShell. Если вы еще не установили Azure PowerShell, просмотрите статью [Начало работы с командлетами Azure PowerShell](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="76477-p120">First, open an Azure PowerShell prompt. If you have not installed Azure PowerShell, see [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/).</span></span>
  
> [!NOTE]
> <span data-ttu-id="76477-p121">Эти команды предназначены для Azure PowerShell 1.0 и более поздних версий. Скачать текстовый файл, который содержит все команды PowerShell, указанные в этой статье, можно [здесь](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-commands-for-5c5a7c19).</span><span class="sxs-lookup"><span data-stu-id="76477-p121">These commands are for Azure PowerShell 1.0 and above. For a text file that contains all the PowerShell commands in this article, click [here](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-commands-for-5c5a7c19).</span></span> 
  
<span data-ttu-id="76477-293">Затем войдите в свою учетную запись Azure с помощью следующей команды.</span><span class="sxs-lookup"><span data-stu-id="76477-293">Next, login to your Azure account with this command.</span></span>
  
```
Login-AzureRMAccount
```

<span data-ttu-id="76477-294">Получите имя подписки с помощью следующей команды.</span><span class="sxs-lookup"><span data-stu-id="76477-294">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort SubscriptionName | Select SubscriptionName
```

<span data-ttu-id="76477-p122">Задайте свою подписку Azure с помощью этих команд. Замените весь текст в кавычках, в том числе символы "<" и ">", правильными именами подписок.</span><span class="sxs-lookup"><span data-stu-id="76477-p122">Set your Azure subscription with these commands. Replace everything within the quotes, including the < and > characters, with the correct subscription name.</span></span>
  
```
$subscrName="<subscription name>"
Select-AzureRMSubscription -SubscriptionName $subscrName -Current
```

<span data-ttu-id="76477-p123">Затем создайте группу ресурсов для виртуальной сети. Чтобы определить уникальное имя группы ресурсов, используйте следующую команду для вывода списка имеющихся групп ресурсов.</span><span class="sxs-lookup"><span data-stu-id="76477-p123">Next, create a new resource group for your virtual network. To determine a unique resource group name, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="76477-299">Создайте группу ресурсов с помощью следующих команд.</span><span class="sxs-lookup"><span data-stu-id="76477-299">Create your new resource group with these commands.</span></span>
  
```
$rgName="<resource group name>"
$locName="<Table V - Item 2 - Value column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName

```

<span data-ttu-id="76477-p124">Виртуальным машинам на основе диспетчера ресурсов требуется соответствующая учетная запись хранения. Для учетной записи хранения необходимо выбрать глобально уникальное имя, которое содержит только буквы нижнего регистра и цифры. Чтобы вывести на экран список имеющихся учетных записей хранения, можно использовать следующую команду.</span><span class="sxs-lookup"><span data-stu-id="76477-p124">Resource Manager-based virtual machines require a Resource Manager-based storage account. You must pick a globally unique name for your storage account that contains only lowercase letters and numbers. You can use this command to list the existing storage accounts.</span></span>
  
```
Get-AzureRMStorageAccount | Sort Name | Select Name
```

<span data-ttu-id="76477-303">Чтобы проверить, уникально ли предложенное имя учетной записи хранения, воспользуйтесь приведенной ниже командой.</span><span class="sxs-lookup"><span data-stu-id="76477-303">Use this command to test whether a proposed storage account name is unique.</span></span>
  
```
Get-AzureRmStorageAccountNameAvailability "<proposed name>"
```

<span data-ttu-id="76477-304">Чтобы создать учетную запись хранения, выполните следующие команды.</span><span class="sxs-lookup"><span data-stu-id="76477-304">To create a new storage account, run these commands.</span></span>
  
```
$rgName="<your new resource group name>"
$locName="<the location of your new resource group>"
$saName="<unique storage account name>"
New-AzureRMStorageAccount -Name $saName -ResourceGroupName $rgName -Type Standard_LRS -Location $locName
```

<span data-ttu-id="76477-305">Затем необходимо создать виртуальную сеть Azure.</span><span class="sxs-lookup"><span data-stu-id="76477-305">Next, you create the Azure virtual network.</span></span>
  
```
# Fill in the variables from previous values and from Tables V, S, and D
$rgName="<name of your new resource group>"
$locName="<Azure location of your new resource group>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$gwSubnetPrefix="<Table S - Item 1 - Subnet address space column>"
$SubnetName="<Table S - Item 2 - Subnet name column>"
$SubnetPrefix="<Table S - Item 2 - Subnet address space column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )

# Get the shortened version of the location
$rg=Get-AzureRmResourceGroup -Name $rgName
$locShortName=$rg.Location

# Create the Azure virtual network and a network security group that allows incoming remote desktop connections to the subnet that is hosting virtual machines
$gatewaySubnet=New-AzureRmVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnetPrefix
$vmSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name $SubnetName -AddressPrefix $SubnetPrefix
New-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gatewaySubnet,$vmSubnet -DNSServer $dnsServers
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name $SubnetName -ResourceGroupName $rgName -Location $locShortName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $SubnetName -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $SubnetName -AddressPrefix $SubnetPrefix -NetworkSecurityGroup $nsg
```

<span data-ttu-id="76477-306">Ниже показана итоговая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="76477-306">Here is your resulting configuration.</span></span>
  
![Виртуальная сеть пока не подключена к локальной.](images/54a37782-a6cc-4d48-b38d-73e128b44a82.png)
  
<span data-ttu-id="76477-308">Затем используйте следующие команды, чтобы создать шлюзы для VPN-подключения типа "сеть-сеть".</span><span class="sxs-lookup"><span data-stu-id="76477-308">Next, use these commands to create the gateways for the site-to-site VPN connection.</span></span>
  
```
# Fill in the variables from previous values and from Tables V and L
$vnetName="<Table V - Item 1 - Value column>"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzureRMVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -SubnetId $vnet.Subnets[0].Id
# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzureRMVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig
# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGateway=New-AzureRMLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix
# Create the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnection=New-AzureRMVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway
```

<span data-ttu-id="76477-309">Ниже показана итоговая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="76477-309">Here is your resulting configuration.</span></span>
  
![Для виртуальной сети теперь настроен шлюз.](images/82dd66b2-a4b7-48f6-a89b-cfdd94630980.png)
  
<span data-ttu-id="76477-p125">Затем настройте локальное VPN-устройство для подключения к VPN-шлюзу Azure. Дополнительные сведения см. в статье [О VPN-устройствах для подключений VPN-шлюзов типа "сеть-сеть"](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span><span class="sxs-lookup"><span data-stu-id="76477-p125">Next, configure your on-premises VPN device to connect to the Azure VPN gateway. For more information, see [About VPN Devices for site-to-site Azure Virtual Network connections](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="76477-313">Чтобы настроить VPN-устройство, вам потребуется следующее:</span><span class="sxs-lookup"><span data-stu-id="76477-313">To configure your VPN device, you will need the following:</span></span>
  
- <span data-ttu-id="76477-p126">Общедоступный IPv4-адрес VPN-шлюза Azure для виртуальной сети. Чтобы вывести этот адрес на экран, используйте команду **Get-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName**.</span><span class="sxs-lookup"><span data-stu-id="76477-p126">The public IPv4 address of the Azure VPN gateway for your virtual network. Use the **Get-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName** command to display this address.</span></span>
    
- <span data-ttu-id="76477-316">Общий ключ IPsec для VPN-подключения типа "сеть-сеть" (таблица V, элемент 5, столбец "Значение").</span><span class="sxs-lookup"><span data-stu-id="76477-316">The IPsec pre-shared key for the site-to-site VPN connection (Table V- Item 5 - Value column).</span></span>
    
<span data-ttu-id="76477-317">Ниже показана итоговая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="76477-317">Here is your resulting configuration.</span></span>
  
![Теперь виртуальная сеть подключена к локальной.](images/6379c423-4f22-4453-941b-7ff32484a0a5.png)
  
### <a name="phase-3-optional-add-virtual-machines"></a><span data-ttu-id="76477-319">Этап 3 (необязательный). Добавление виртуальных машин</span><span class="sxs-lookup"><span data-stu-id="76477-319">Phase 3 (Optional): Add virtual machines</span></span>
<span data-ttu-id="76477-320"><a name="Phase2"> </a></span><span class="sxs-lookup"><span data-stu-id="76477-320"><a name="Phase2"> </a></span></span>

<span data-ttu-id="76477-p127">Создайте необходимые виртуальные машины в Azure. Дополнительные сведения см. в статье [Создание первой виртуальной машины Windows на портале Azure](https://go.microsoft.com/fwlink/p/?LinkId=393098).</span><span class="sxs-lookup"><span data-stu-id="76477-p127">Create the virtual machines you need in Azure. For more information, see [Create your first Windows virtual machine in the Azure portal](https://go.microsoft.com/fwlink/p/?LinkId=393098).</span></span>
  
<span data-ttu-id="76477-323">Используйте следующие параметры:</span><span class="sxs-lookup"><span data-stu-id="76477-323">Use the following settings:</span></span>
  
- <span data-ttu-id="76477-p128">В области **Основные** выберите ту же подписку и группу ресурсов, что и в виртуальной сети. Запишите имя пользователя и пароль в надежном месте. Они потребуются позже для входа на виртуальной машине.</span><span class="sxs-lookup"><span data-stu-id="76477-p128">On the **Basics** pane, select the same subscription and resource group as your virtual network. Record the user name and password in a secure location. You will need these later to sign in to the virtual machine.</span></span>
    
- <span data-ttu-id="76477-327">В области **Размер** выберите подходящий размер.</span><span class="sxs-lookup"><span data-stu-id="76477-327">On the **Size** pane, choose the appropriate size.</span></span>
    
- <span data-ttu-id="76477-p129">В области **Параметры** в разделе **Хранилище** выберите тип хранилища **Стандартный** и учетную запись хранения, настроенную для вашей виртуальной сети. В разделе **Сеть** выберите имя виртуальной сети и подсеть для размещения виртуальных машин (не GatewaySubnet). Для всех остальных параметров оставьте значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="76477-p129">On the **Settings** pane, in the **Storage** section, select the **Standard** storage type and the storage account set up with your virtual network. In the **Network** section, select the name of your virtual network and the subnet for hosting virtual machines (not the GatewaySubnet). Leave all other settings at their default values.</span></span>
    
<span data-ttu-id="76477-p130">Проверьте внутренний DNS, чтобы убедиться, что виртуальная машина правильно использует DNS и для виртуальной машины добавлены адресные записи (A). Чтобы предоставить виртуальным машинам Azure доступ к Интернету, их необходимо настроить на использование прокси-сервера локальной сети. Обратитесь к администратору сети за дополнительными инструкциями по настройке сервера.</span><span class="sxs-lookup"><span data-stu-id="76477-p130">Verify that your virtual machine is using DNS correctly by checking your internal DNS to ensure that Address (A) records were added for you new virtual machine. To access the Internet, your Azure virtual machines must be configured to use your on-premises network's proxy server. Contact your network administrator for additional configuration steps to perform on the server.</span></span>
  
<span data-ttu-id="76477-334">Ниже показана итоговая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="76477-334">Here is your resulting configuration.</span></span>
  
![В виртуальной сети теперь размещены виртуальные машины, доступные из локальной сети.](images/86ab63a6-bfae-4f75-8470-bd40dff123ac.png)
  
## <a name="see-also"></a><span data-ttu-id="76477-336">See Also</span><span class="sxs-lookup"><span data-stu-id="76477-336">See Also</span></span>

<span data-ttu-id="76477-337"><a name="DeploymentRoadmap"> </a></span><span class="sxs-lookup"><span data-stu-id="76477-337"><a name="DeploymentRoadmap"> </a></span></span>

[<span data-ttu-id="76477-338">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="76477-338">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="76477-339">Развертывание службы синхронизации каталогов Office 365 (DirSync) в Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="76477-339">Deploy Office 365 Directory Synchronization (DirSync) in Microsoft Azure</span></span>](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md)

[<span data-ttu-id="76477-340">Создание виртуальной машины Windows на портале Azure</span><span class="sxs-lookup"><span data-stu-id="76477-340">How to create the virtual machine</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=393098)
  
[<span data-ttu-id="76477-341">О VPN-устройствах для подключений VPN-шлюзов типа "сеть-сеть"</span><span class="sxs-lookup"><span data-stu-id="76477-341">About VPN Devices for site-to-site Azure Virtual Network connections</span></span>](https://azure.microsoft.com/documentation/articles/vpn-gateway-about-vpn-devices/)
  
[<span data-ttu-id="76477-342">Установка и настройка Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="76477-342">How to install and configure Azure PowerShell</span></span>](https://azure.microsoft.com/documentation/articles/powershell-install-configure/#how-to-install-azure-powershell)



