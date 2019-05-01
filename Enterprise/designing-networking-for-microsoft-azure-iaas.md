---
title: Проектирование сети для Microsoft Azure IaaS
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
ms.assetid: 9cb70c9d-9ed9-47cc-af5a-6403d87d3372
description: Сводка. Узнайте, как разрабатывать оптимизированную сеть для рабочих нагрузок в Microsoft Azure IaaS.
ms.openlocfilehash: c41e92445dd01a94b7d305b521bbd4330311fcb4
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491126"
---
# <a name="designing-networking-for-microsoft-azure-iaas"></a><span data-ttu-id="ca832-103">Проектирование сети для Microsoft Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="ca832-103">Designing networking for Microsoft Azure IaaS</span></span>

 <span data-ttu-id="ca832-104">**Сводка:** Узнайте, как разрабатывать оптимизированную сеть для рабочих нагрузок в Microsoft Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="ca832-104">**Summary:** Understand how to design optimized networking for workloads in Microsoft Azure IaaS.</span></span>
  
<span data-ttu-id="ca832-105">Оптимизация сетей для выполнения ИТ-задач в Azure IaaS требует понимания виртуальных сетей, пространств адресов, маршрутизации, DNS и балансировки нагрузки Azure.</span><span class="sxs-lookup"><span data-stu-id="ca832-105">Optimizing networking for IT workloads hosted in Azure IaaS requires an understanding of Azure virtual networks (VNets), address spaces, routing, DNS, and load balancing.</span></span>
  
## <a name="planning-steps-for-any-vnet"></a><span data-ttu-id="ca832-106">Этапы планирования для любой виртуальной сети</span><span class="sxs-lookup"><span data-stu-id="ca832-106">Planning steps for any VNet</span></span>

<span data-ttu-id="ca832-107">Ниже перечислены шаги, которыми следует руководствоваться при планировании виртуальной сети любого типа.</span><span class="sxs-lookup"><span data-stu-id="ca832-107">Follow these steps for any type of VNet.</span></span>
  
### <a name="step-1-prepare-your-intranet-for-microsoft-cloud-services"></a><span data-ttu-id="ca832-108">Шаг 1. Подготовьте интрасеть для облачных служб (Майкрософт).</span><span class="sxs-lookup"><span data-stu-id="ca832-108">Step 1: Prepare your intranet for Microsoft cloud services.</span></span>

<span data-ttu-id="ca832-109">Выполните **действия по подготовке сети для облачных служб (Майкрософт)**, описанные в статье [Общие элементы подключения к облаку Майкрософт](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="ca832-109">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-2-optimize-your-internet-bandwidth"></a><span data-ttu-id="ca832-110">Шаг 2. Оптимизируйте пропускную способность канала доступа в Интернет.</span><span class="sxs-lookup"><span data-stu-id="ca832-110">Step 2: Optimize your Internet bandwidth.</span></span>

<span data-ttu-id="ca832-111">Оптимизируйте скорость интернет-соединения, выполнив действия 2–4 из раздела **Действия по подготовке сети для служб Microsoft SaaS** статьи [Проектирование сети для Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span><span class="sxs-lookup"><span data-stu-id="ca832-111">Optimize your Internet bandwidth using steps 2 - 4 of the **Steps to prepare your network for Microsoft SaaS services** section in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span></span>
  
### <a name="step-3-determine-the-type-of-vnet-cloud-only-or-cross-premises"></a><span data-ttu-id="ca832-112">Шаг 3. Выберите тип виртуальной сети (только облачная или распределенная).</span><span class="sxs-lookup"><span data-stu-id="ca832-112">Step 3: Determine the type of VNet (cloud-only or cross-premises).</span></span>

<span data-ttu-id="ca832-p101">Только облачные сети не подключаются к локальным сетям. Пример:</span><span class="sxs-lookup"><span data-stu-id="ca832-p101">A cloud-only VNet has no connection to an on-premises network. Here is an example.</span></span>
  
<span data-ttu-id="ca832-115">**Рис. 1. Только облачная виртуальная сеть**</span><span class="sxs-lookup"><span data-stu-id="ca832-115">**Figure 1: A cloud-only VNet**</span></span>

![Рисунок 1: только облачная виртуальная сеть в Azure](media/8be19104-02b3-4a7f-b0a0-30d6fcf8890b.png)
  
<span data-ttu-id="ca832-117">На рисунке 1 показан набор виртуальных машин в только облачной виртуальной сети.</span><span class="sxs-lookup"><span data-stu-id="ca832-117">Figure 1 shows a set of virtual machines in a cloud-only VNet.</span></span>
  
<span data-ttu-id="ca832-p102">В распределенной виртуальной сети имеется подключение VPN типа "сеть-сеть" или ExpressRoute к локальной сети через шлюз Azure. Пример:</span><span class="sxs-lookup"><span data-stu-id="ca832-p102">A cross-premises VNet has a site-to-site (S2S) VPN or ExpressRoute connection to an on-premises network through an Azure gateway. Here is an example.</span></span>
  
<span data-ttu-id="ca832-120">**Рис. 2. Распределенная виртуальная сеть**</span><span class="sxs-lookup"><span data-stu-id="ca832-120">**Figure 2: A cross-premises VNet**</span></span>

![Рисунок 2: локальная виртуальная сеть в Azure](media/caacf007-e0dc-45d3-9531-441109776d25.png)
  
<span data-ttu-id="ca832-122">На рисунке 2 представлен набор виртуальных машин в распределенной виртуальной сети, которая подключена к локальной сети.</span><span class="sxs-lookup"><span data-stu-id="ca832-122">Figure 2 shows a set of virtual machines in a cross-premises VNet, which is connected to an on-premises network.</span></span>
  
<span data-ttu-id="ca832-123">Дополнительные сведения см. в разделе [Этапы планирования для распределенной виртуальной сети](designing-networking-for-microsoft-azure-iaas.md#cross_prem) далее в этой статье.</span><span class="sxs-lookup"><span data-stu-id="ca832-123">See the additional [Planning steps for a cross-premises VNet](designing-networking-for-microsoft-azure-iaas.md#cross_prem) section in this article.</span></span>
  
### <a name="step-4-determine-the-address-space-of-the-vnet"></a><span data-ttu-id="ca832-124">Шаг 4. Определите адресное пространство для виртуальной сети.</span><span class="sxs-lookup"><span data-stu-id="ca832-124">Step 4: Determine the address space of the VNet.</span></span>

<span data-ttu-id="ca832-125">В таблице 1 показаны адресные пространства для различных типов виртуальных сетей.</span><span class="sxs-lookup"><span data-stu-id="ca832-125">Table 1 shows the address spaces for the different types of VNets.</span></span>
  
|<span data-ttu-id="ca832-126">**Тип виртуальной сети**</span><span class="sxs-lookup"><span data-stu-id="ca832-126">**Type of VNet**</span></span>|<span data-ttu-id="ca832-127">**Адресное пространство виртуальной сети**</span><span class="sxs-lookup"><span data-stu-id="ca832-127">**Virtual network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="ca832-128">Только облако</span><span class="sxs-lookup"><span data-stu-id="ca832-128">Cloud-only</span></span>  <br/> |<span data-ttu-id="ca832-129">Произвольное частное адресное пространство</span><span class="sxs-lookup"><span data-stu-id="ca832-129">Arbitrary private address space</span></span>  <br/> |
|<span data-ttu-id="ca832-130">Только облачная с межсоединениями</span><span class="sxs-lookup"><span data-stu-id="ca832-130">Interconnected cloud-only</span></span>  <br/> |<span data-ttu-id="ca832-131">Произвольный частный, но не перекрывающиеся с другими подключенными виртуальных сетей</span><span class="sxs-lookup"><span data-stu-id="ca832-131">Arbitrary private, but not overlapping with other connected VNets</span></span>  <br/> |
|<span data-ttu-id="ca832-132">Распределенная</span><span class="sxs-lookup"><span data-stu-id="ca832-132">Cross-premises</span></span>  <br/> |<span data-ttu-id="ca832-133">Частное адресное пространство, не перекрывающееся с локальными сетями</span><span class="sxs-lookup"><span data-stu-id="ca832-133">Private, but not overlapping with on-premises</span></span>  <br/> |
|<span data-ttu-id="ca832-134">Распределенная с межсоединениями</span><span class="sxs-lookup"><span data-stu-id="ca832-134">Interconnected cross-premises</span></span>  <br/> |<span data-ttu-id="ca832-135">Частное адресное пространство, не перекрывающееся с другими локальными сетями и другими подключенными виртуальными сетями</span><span class="sxs-lookup"><span data-stu-id="ca832-135">Private, but not overlapping with on-premises and other connected VNets</span></span>  <br/> |
   
 <span data-ttu-id="ca832-136">**Таблица 1. Типы виртуальных сетей и соответствующие адресные пространства**</span><span class="sxs-lookup"><span data-stu-id="ca832-136">**Table 1: Types of VNets and their corresponding address space**</span></span>
  
<span data-ttu-id="ca832-137">Виртуальным машинам назначаются конфигурации адресов из адресного пространства подсети. За это отвечает сервер DHCP:</span><span class="sxs-lookup"><span data-stu-id="ca832-137">Virtual machines are assigned an address configuration from the address space of the subnet by DHCP:</span></span>
  
- <span data-ttu-id="ca832-138">Адрес/маска подсети</span><span class="sxs-lookup"><span data-stu-id="ca832-138">Address/subnet mask</span></span>
    
- <span data-ttu-id="ca832-139">Шлюз по умолчанию</span><span class="sxs-lookup"><span data-stu-id="ca832-139">Default gateway</span></span>
    
- <span data-ttu-id="ca832-140">IP-адреса DNS-серверов</span><span class="sxs-lookup"><span data-stu-id="ca832-140">DNS server IP addresses</span></span>
    
<span data-ttu-id="ca832-141">Кроме того, можно зарезервировать статический IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="ca832-141">You can also reserve a static IP address.</span></span>
  
<span data-ttu-id="ca832-142">Виртуальным машинам также можно назначать общедоступные IP-адреса. Это можно сделать как отдельно для каждой машины, так и из облачной службы, содержащей виртуальные машины (только для машин, развернутых классическим способом).</span><span class="sxs-lookup"><span data-stu-id="ca832-142">Virtual machines can also be assigned a public IP address, either individually or from the containing cloud service (for classic deployment machines only).</span></span>
  
### <a name="step-5-determine-the-subnets-within-the-vnet-and-the-address-spaces-assigned-to-each"></a><span data-ttu-id="ca832-143">Шаг 5. Определите подсети в виртуальной сети и назначьте адресное пространство каждой из них.</span><span class="sxs-lookup"><span data-stu-id="ca832-143">Step 5: Determine the subnets within the VNet and the address spaces assigned to each.</span></span>

<span data-ttu-id="ca832-144">В виртуальных сетях существует два типа подсетей: подсеть шлюза и подсеть с размещенными виртуальными машинами.</span><span class="sxs-lookup"><span data-stu-id="ca832-144">There are two types of subnets in a VNet, a gateway subnet and a virtual machine-hosting subnet.</span></span>
  
<span data-ttu-id="ca832-145">**Рис. 3. Два типа подсетей в Azure**</span><span class="sxs-lookup"><span data-stu-id="ca832-145">**Figure 3: The two types of subnets in Azure**</span></span>

![Рис. 3. Два типа подсетей в Azure](media/2eaa512d-1293-4e9b-b927-6bfe0fc0acb4.png)
  
<span data-ttu-id="ca832-147">На рисунке 3 показана виртуальная сеть, содержащая подсеть шлюза с шлюзом Azure и набором подсетей с размещением виртуальных машин, содержащих виртуальные машины.</span><span class="sxs-lookup"><span data-stu-id="ca832-147">Figure 3 shows a VNet containing a gateway subnet that has an Azure gateway and a set of virtual machine-hosting subnets containing virtual machines.</span></span>
  
<span data-ttu-id="ca832-148">Подсеть шлюза Azure требуется службе Azure для размещения двух виртуальных машин шлюза Azure.</span><span class="sxs-lookup"><span data-stu-id="ca832-148">The Azure gateway subnet is needed by Azure to host the two virtual machines of your Azure gateway.</span></span> <span data-ttu-id="ca832-149">Длина префикса для указываемого адресного пространства должна составлять хотя бы 29 бита (например: 192.168.15.248/29).</span><span class="sxs-lookup"><span data-stu-id="ca832-149">Specify an address space with at least a 29-bit prefix length (example: 192.168.15.248/29).</span></span> <span data-ttu-id="ca832-150">Рекомендуется 27-или более короткая длина префикса, особенно при планировании использования ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="ca832-150">A 27-bit or smaller prefix length is recommended, especially if you are planning to use ExpressRoute.</span></span>
  
<span data-ttu-id="ca832-151">Рекомендуется определить адресное пространство подсети шлюза Azure:</span><span class="sxs-lookup"><span data-stu-id="ca832-151">A best practice for determining the address space of the Azure gateway subnet is:</span></span>
  
1. <span data-ttu-id="ca832-152">Выберите размер подсети шлюза.</span><span class="sxs-lookup"><span data-stu-id="ca832-152">Decide on the size of the gateway subnet.</span></span>
    
2. <span data-ttu-id="ca832-153">В переменных битах в адресном пространстве виртуальной сети задайте для битов, используемых для подсети шлюза, значение 0, а для оставшихся битов — значение 1.</span><span class="sxs-lookup"><span data-stu-id="ca832-153">In the variable bits in the address space of the VNet, set the bits used for the gateway subnet to 0 and set the remaining bits to 1.</span></span>
    
3. <span data-ttu-id="ca832-154">Преобразуйте полученный результат в десятичный формат и выразите его как адресное пространство, длина префикса которого соответствует размеру подсети шлюза.</span><span class="sxs-lookup"><span data-stu-id="ca832-154">Convert to decimal and express as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="ca832-155">При использовании этого метода адресное пространство для подсети шлюза всегда будет находиться в самом конце адресного пространства виртуальной сети.</span><span class="sxs-lookup"><span data-stu-id="ca832-155">With this method, the address space for the gateway subnet is always at the farthest end of the VNet address space.</span></span>
  
<span data-ttu-id="ca832-p104">Вот пример определения префикса адреса для подсети шлюза: адресное пространство виртуальной сети — 10.119.0.0/16. Организация изначально будет использовать VPN-подключение типа "сеть-сеть", но в итоге перейдет на ExpressRoute. В таблице 2 представлены действия по определению префикса адреса для подсети шлюза в нотации сетевых префиксов и результаты этих действий.</span><span class="sxs-lookup"><span data-stu-id="ca832-p104">Here is an example of defining the address prefix for the gateway subnet: The address space of the VNet is 10.119.0.0/16. The organization will initially use a site-to-site VPN connection, but will eventually get ExpressRoute. Table 2 shows the steps and results of determining the gateway subnet address prefix in network prefix notation (also known as CIDR).</span></span>

<span data-ttu-id="ca832-159">Ниже приведены действия и примеры определения префикса адреса подсети шлюза.</span><span class="sxs-lookup"><span data-stu-id="ca832-159">Here are the steps and example of determining the gateway subnet address prefix:</span></span>

1. <span data-ttu-id="ca832-160">Выберите размер подсети шлюза.</span><span class="sxs-lookup"><span data-stu-id="ca832-160">Decide on the size of the gateway subnet.</span></span> <span data-ttu-id="ca832-161">В нашем примере мы выбрали/28.</span><span class="sxs-lookup"><span data-stu-id="ca832-161">For our example, we chose /28.</span></span>
2. <span data-ttu-id="ca832-162">Установите биты в переменной области адресов виртуальной сети (b) в 0 для битов подсети шлюза (G), в противном случае — 1 (V).</span><span class="sxs-lookup"><span data-stu-id="ca832-162">Set the bits in the variable portion of the VNet address space (b) to 0 for the gateway subnet bits (G), otherwise 1 (V).</span></span> <span data-ttu-id="ca832-163">Для нашего примера мы используем адресное пространство 10.119.0.0/16 для виртуальной сети.</span><span class="sxs-lookup"><span data-stu-id="ca832-163">For our example, we are using the 10.119.0.0/16 address space for the VNet.</span></span>
<br/>
<br/><span data-ttu-id="ca832-164">10,119.</span><span class="sxs-lookup"><span data-stu-id="ca832-164">10.119.</span></span> <span data-ttu-id="ca832-165">бббббббб.</span><span class="sxs-lookup"><span data-stu-id="ca832-165">bbbbbbbb .</span></span> <span data-ttu-id="ca832-166">бббббббб</span><span class="sxs-lookup"><span data-stu-id="ca832-166">bbbbbbbb</span></span>
<br/><span data-ttu-id="ca832-167">10,119.</span><span class="sxs-lookup"><span data-stu-id="ca832-167">10.119.</span></span> <span data-ttu-id="ca832-168">ВВВВВВВВ.</span><span class="sxs-lookup"><span data-stu-id="ca832-168">VVVVVVVV .</span></span> <span data-ttu-id="ca832-169">ВВВВГГГГ</span><span class="sxs-lookup"><span data-stu-id="ca832-169">VVVVGGGG</span></span>
<br/><span data-ttu-id="ca832-170">10,119.</span><span class="sxs-lookup"><span data-stu-id="ca832-170">10.119.</span></span> <span data-ttu-id="ca832-171">11111111.</span><span class="sxs-lookup"><span data-stu-id="ca832-171">11111111 .</span></span> <span data-ttu-id="ca832-172">11110000</span><span class="sxs-lookup"><span data-stu-id="ca832-172">11110000</span></span>
<br/><br/>
3. <span data-ttu-id="ca832-173">Преобразовать результат из шага 2 в десятичное и выразить в качестве адресного пространства.</span><span class="sxs-lookup"><span data-stu-id="ca832-173">Convert the result from step 2 to decimal and express as an address space.</span></span> <span data-ttu-id="ca832-174">В нашем примере — 10,119.</span><span class="sxs-lookup"><span data-stu-id="ca832-174">For our example, 10.119.</span></span> <span data-ttu-id="ca832-175">11111111.</span><span class="sxs-lookup"><span data-stu-id="ca832-175">11111111 .</span></span> <span data-ttu-id="ca832-176">11110000 — 10.119.255.240, а длина префикса — от шага 1 (28 в нашем примере), то полученный префикс адреса подсети шлюза равен 10.119.255.240/28.</span><span class="sxs-lookup"><span data-stu-id="ca832-176">11110000 is 10.119.255.240, and with the prefix length from step 1, (28 in our example), the resulting gateway subnet address prefix is 10.119.255.240/28.</span></span>
  
<span data-ttu-id="ca832-177">Для получения дополнительных сведений см. [Калькулятор адресного пространства для подсетей шлюза Azure](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) .</span><span class="sxs-lookup"><span data-stu-id="ca832-177">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for more information.</span></span>
  
<span data-ttu-id="ca832-178">Подсети с размещенными виртуальными машинами — это сети, в которых размещаются виртуальные машины Azure, что можно сделать, руководствуясь стандартными инструкциями для локальных сетей, например, используя общую роль, уровень приложений или инструкции по изоляции подсети.</span><span class="sxs-lookup"><span data-stu-id="ca832-178">Virtual machine-hosting subnets are where you place Azure virtual machines, which you can do according to typical on-premises guidelines, such as a common role or tier of an application or for subnet isolation.</span></span>
  
<span data-ttu-id="ca832-179">Azure использует первые 3 адреса в каждой подсети.</span><span class="sxs-lookup"><span data-stu-id="ca832-179">Azure uses the first 3 addresses on each subnet.</span></span> <span data-ttu-id="ca832-180">Таким образом, число возможных адресов в подсети Azure составляет 2<sup>n</sup> -5, где n — это количество битов узла.</span><span class="sxs-lookup"><span data-stu-id="ca832-180">Therefore, the number of possible addresses on an Azure subnet is 2<sup>n</sup> - 5, where n is the number of host bits.</span></span> <span data-ttu-id="ca832-181">В таблице 3 указано требуемое количество виртуальных машин и битов узлов, а также соответствующие размеры подсети.</span><span class="sxs-lookup"><span data-stu-id="ca832-181">Table 3 shows the range of virtual machines required, the number of hosts bits needed, and the corresponding subnet size.</span></span>
  
|<span data-ttu-id="ca832-182">**Необходимо виртуальных машин**</span><span class="sxs-lookup"><span data-stu-id="ca832-182">**Virtual machines required**</span></span>|<span data-ttu-id="ca832-183">**Биты узлов**</span><span class="sxs-lookup"><span data-stu-id="ca832-183">**Host bits**</span></span>|<span data-ttu-id="ca832-184">**Размер подсети**</span><span class="sxs-lookup"><span data-stu-id="ca832-184">**Subnet size**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="ca832-185">1–3</span><span class="sxs-lookup"><span data-stu-id="ca832-185">1-3</span></span>  <br/> |<span data-ttu-id="ca832-186">4</span><span class="sxs-lookup"><span data-stu-id="ca832-186">3</span></span>  <br/> |<span data-ttu-id="ca832-187">/29</span><span class="sxs-lookup"><span data-stu-id="ca832-187">/29</span></span>  <br/> |
|<span data-ttu-id="ca832-188">4–11</span><span class="sxs-lookup"><span data-stu-id="ca832-188">4-11</span></span>  <br/> |<span data-ttu-id="ca832-189">SP4</span><span class="sxs-lookup"><span data-stu-id="ca832-189">4</span></span>  <br/> |<span data-ttu-id="ca832-190">/28</span><span class="sxs-lookup"><span data-stu-id="ca832-190">/28</span></span>  <br/> |
|<span data-ttu-id="ca832-191">12–27</span><span class="sxs-lookup"><span data-stu-id="ca832-191">12-27</span></span>  <br/> |<span data-ttu-id="ca832-192">17:00</span><span class="sxs-lookup"><span data-stu-id="ca832-192">5</span></span>  <br/> |<span data-ttu-id="ca832-193">/27</span><span class="sxs-lookup"><span data-stu-id="ca832-193">/27</span></span>  <br/> |
|<span data-ttu-id="ca832-194">28–59</span><span class="sxs-lookup"><span data-stu-id="ca832-194">28-59</span></span>  <br/> |<span data-ttu-id="ca832-195">ICMPv6</span><span class="sxs-lookup"><span data-stu-id="ca832-195">6</span></span>  <br/> |<span data-ttu-id="ca832-196">/26</span><span class="sxs-lookup"><span data-stu-id="ca832-196">/26</span></span>  <br/> |
|<span data-ttu-id="ca832-197">60–123</span><span class="sxs-lookup"><span data-stu-id="ca832-197">60-123</span></span>  <br/> |<span data-ttu-id="ca832-198">см</span><span class="sxs-lookup"><span data-stu-id="ca832-198">7</span></span>  <br/> |<span data-ttu-id="ca832-199">/25</span><span class="sxs-lookup"><span data-stu-id="ca832-199">/25</span></span>  <br/> |
   
 <span data-ttu-id="ca832-200">**Таблица 3. Требования к виртуальным машинам и размерам подсети**</span><span class="sxs-lookup"><span data-stu-id="ca832-200">**Table 3: Virtual machine requirements and their subnet sizes**</span></span>
  
<span data-ttu-id="ca832-201">Для получения дополнительных сведений о максимальном объеме виртуальных машин в подсети или виртуальной сети ознакомьтесь с разделом [ограничения сети](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span><span class="sxs-lookup"><span data-stu-id="ca832-201">For more information about the maximum amount of virtual machines on a subnet or VNet, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="ca832-202">Для получения дополнительных сведений просмотрите раздел [планирование и проектирование виртуальных сетей Azure](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/).</span><span class="sxs-lookup"><span data-stu-id="ca832-202">For more information, see [Plan and design Azure Virtual Networks](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/).</span></span>
  
### <a name="step-6-determine-the-dns-server-configuration-and-the-addresses-of-the-dns-servers-to-assign-to-vms-in-the-vnet"></a><span data-ttu-id="ca832-203">Шаг 6. Определите конфигурацию DNS-сервера и адреса DNS-серверов для назначения виртуальным машинам в виртуальной сети.</span><span class="sxs-lookup"><span data-stu-id="ca832-203">Step 6: Determine the DNS server configuration and the addresses of the DNS servers to assign to VMs in the VNet.</span></span>

<span data-ttu-id="ca832-p112">Azure назначает виртуальным машинам адреса DNS-серверов с помощью сервера DHCP. DNS-серверы могут:</span><span class="sxs-lookup"><span data-stu-id="ca832-p112">Azure assigns virtual machines the addresses of DNS servers by DHCP. DNS servers can be:</span></span>
  
- <span data-ttu-id="ca832-206">предоставляться Azure: регистрация локального имени, а также разрешение локальных и интернет-имен;</span><span class="sxs-lookup"><span data-stu-id="ca832-206">Supplied by Azure: Provides local name registration and local and Internet name resolution</span></span>
    
- <span data-ttu-id="ca832-207">указываться вами: регистрация локального или интернет-имени, а также разрешение имен в интрасети или Интернете.</span><span class="sxs-lookup"><span data-stu-id="ca832-207">Provided by you: Provides local or intranet name registration and either intranet or Internet name resolution</span></span>
    
<span data-ttu-id="ca832-208">В таблице 4 представлены различные конфигурации DNS-сервера для каждого типа виртуальной сети.</span><span class="sxs-lookup"><span data-stu-id="ca832-208">Table 4 shows the different configurations of DNS servers for each type of VNet.</span></span>
    
|<span data-ttu-id="ca832-209">**Тип виртуальной сети**</span><span class="sxs-lookup"><span data-stu-id="ca832-209">**Type of VNet**</span></span>|<span data-ttu-id="ca832-210">**DNS-сервер**</span><span class="sxs-lookup"><span data-stu-id="ca832-210">**DNS server**</span></span>|
|:-----|:-----|
|<span data-ttu-id="ca832-211">Только облако</span><span class="sxs-lookup"><span data-stu-id="ca832-211">Cloud-only</span></span>  <br/> |<span data-ttu-id="ca832-212">Разрешение локальных и интернет-имен службой Azure</span><span class="sxs-lookup"><span data-stu-id="ca832-212">Azure-supplied for local and Internet name resolution</span></span>  <br/> <span data-ttu-id="ca832-213">Виртуальная машина Azure для разрешения локальных и интернет-имен (переадресация DNS)</span><span class="sxs-lookup"><span data-stu-id="ca832-213">Azure virtual machine for local and Internet name resolution (DNS forwarding)</span></span>  <br/> |
|<span data-ttu-id="ca832-214">Распределенная</span><span class="sxs-lookup"><span data-stu-id="ca832-214">Cross-premises</span></span>  <br/> |<span data-ttu-id="ca832-215">Разрешение локальных и интернет-имен локальной службой</span><span class="sxs-lookup"><span data-stu-id="ca832-215">On-premises for local and intranet name resolution</span></span>  <br/> <span data-ttu-id="ca832-216">Виртуальная машина Azure для разрешения локальных имен и имен в интрасети (репликация и переадресация DNS)</span><span class="sxs-lookup"><span data-stu-id="ca832-216">Azure virtual machine for local and intranet name resolution (DNS replication and forwarding)</span></span>  <br/> |
   
 <span data-ttu-id="ca832-217">**Таблица 4. Варианты DNS-серверов для двух различных типов виртуальных сетей**</span><span class="sxs-lookup"><span data-stu-id="ca832-217">**Table 4: DNS server options for the two different types of VNets**</span></span>
  
<span data-ttu-id="ca832-218">Дополнительные сведения см. в разделе [разрешение имен для виртуальных машин и экземпляров ролей](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances).</span><span class="sxs-lookup"><span data-stu-id="ca832-218">For more information, see [Name Resolution for VMs and Role Instances](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances).</span></span>
  
### <a name="step-7-determine-the-load-balancing-configuration-internet-facing-or-internal"></a><span data-ttu-id="ca832-219">Шаг 7. Определите конфигурацию балансировки нагрузки (для внутреннего или интернет-трафика).</span><span class="sxs-lookup"><span data-stu-id="ca832-219">Step 7: Determine the load balancing configuration (Internet-facing or internal).</span></span>

<span data-ttu-id="ca832-p113">В некоторых случаях входящий трафик требуется распределить по нескольким серверам, которым назначена одна и та же роль. В Azure IaaS имеются встроенные средства для этого в отношении внутреннего и интернет-трафика.</span><span class="sxs-lookup"><span data-stu-id="ca832-p113">In some cases, you want to distribute incoming traffic to a set of servers that have the same role. Azure IaaS has a built-in facility to do this for Internet-facing and internal traffic loads.</span></span>
  
<span data-ttu-id="ca832-222">Подсистема балансировки нагрузки Azure для интернет-трафика случайным образом распределяет нежелательный входящий трафик из Интернета среди участников набора балансировки нагрузки. </span><span class="sxs-lookup"><span data-stu-id="ca832-222">Azure Internet-facing load balancing randomly distributes unsolicited incoming traffic from the Internet to the members of a load-balanced set.</span></span>
  
<span data-ttu-id="ca832-223">**Рис. 4. Внешний балансировщик нагрузки в Azure**</span><span class="sxs-lookup"><span data-stu-id="ca832-223">**Figure 4: An external load balancer in Azure**</span></span>

![Рис. 4. Внешний балансировщик нагрузки в Azure](media/eb5945e5-0c2b-40f1-b9ed-54bb2b0f9e59.png)
  
<span data-ttu-id="ca832-225">На рисунке 4 показана внешняя подсистема балансировки нагрузки в Azure, которая распределяет входящий трафик по правилу или конечной точке входящего NAT в набор виртуальных машин в наборе балансировки нагрузки.</span><span class="sxs-lookup"><span data-stu-id="ca832-225">Figure 4 shows an external load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="ca832-226">Подсистема балансировки нагрузки Azure для внутреннего трафика случайным образом распределяет незапрошенный входящий трафик от других виртуальных машин или компьютеров в интрасети среди участников набора балансировки нагрузки. </span><span class="sxs-lookup"><span data-stu-id="ca832-226">Azure internal load balancing randomly distributes unsolicited incoming traffic from other Azure VMs or from intranet computers to the members of a load-balanced set.</span></span> 
  
<span data-ttu-id="ca832-227">**Рис. 5. Внутренний балансировщик нагрузки в Azure**</span><span class="sxs-lookup"><span data-stu-id="ca832-227">**Figure 5: An internal load balancer in Azure**</span></span>

![Рис. 5. Внутренний балансировщик нагрузки в Azure](media/d1451b73-6465-449d-b3e6-22160ce51f35.png)
  
<span data-ttu-id="ca832-229">На рисунке 5 показана внутренняя подсистема балансировки нагрузки в Azure, которая распределяет входящий трафик по правилу или конечной точке входящего NAT в набор виртуальных машин в наборе балансировки нагрузки.</span><span class="sxs-lookup"><span data-stu-id="ca832-229">Figure 5 shows an internal load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="ca832-230">Дополнительные сведения см. в [подсистеме балансировки нагрузки Azure](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview).</span><span class="sxs-lookup"><span data-stu-id="ca832-230">For more information, see [Azure Load Balancer](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview).</span></span>
  
### <a name="step-8-determine-the-use-of-virtual-appliances-and-user-defined-routes"></a><span data-ttu-id="ca832-231">Шаг 8. Определите порядок использования виртуальных модулей и пользовательских маршрутов в Azure.</span><span class="sxs-lookup"><span data-stu-id="ca832-231">Step 8: Determine the use of virtual appliances and user-defined routes.</span></span>

<span data-ttu-id="ca832-232">Если требуется перенаправить трафик на виртуальные модули в виртуальной сети, возможно, в подсеть потребуется добавить один или несколько пользовательских маршрутов.</span><span class="sxs-lookup"><span data-stu-id="ca832-232">If you need to forward traffic to virtual appliances in your VNet, you may need to add one or more user-defined routes to a subnet.</span></span>
  
<span data-ttu-id="ca832-233">**Рис. 6. Виртуальные устройства и пользовательские маршруты в Azure**</span><span class="sxs-lookup"><span data-stu-id="ca832-233">**Figure 6: Virtual appliances and user-defined routes in Azure**</span></span>

![Рис. 6. Виртуальные устройства и пользовательские маршруты в Azure](media/f181d0f4-ebf9-439e-9c98-dec17428c32b.png)
  
<span data-ttu-id="ca832-235">На рисунке 6 представлена распределенная виртуальная сеть и пользовательский маршрут, назначенный подсети с размещенными виртуальными машинами, которая указывает на виртуальный модуль.</span><span class="sxs-lookup"><span data-stu-id="ca832-235">Figure 6 shows a cross-premises VNet and a user-defined route assigned to a virtual machine-hosting subnet that points to a virtual appliance.</span></span>
  
<span data-ttu-id="ca832-236">Для получения дополнительных сведений см [](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview).</span><span class="sxs-lookup"><span data-stu-id="ca832-236">For more information, see [User Defined Routes and IP Forwarding](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview).</span></span>
  
### <a name="step-9-determine-how-computers-from-the-internet-will-connect-to-virtual-machines"></a><span data-ttu-id="ca832-237">Шаг 9. Определите, как компьютеры из Интернета будут автоматически подключаться к виртуальным машинам.</span><span class="sxs-lookup"><span data-stu-id="ca832-237">Step 9: Determine how computers from the Internet will connect to virtual machines.</span></span>

<span data-ttu-id="ca832-238">Существуют различные способы предоставить виртуальным машинам в виртуальной сети доступ к Интернету, который включает доступ из сети организации через прокси-сервер или другое пограничное устройство.</span><span class="sxs-lookup"><span data-stu-id="ca832-238">There are multiple ways to provide Internet access to the virtual machines on a VNet, which includes access from your organization network through your proxy server or other edge device.</span></span>
  
<span data-ttu-id="ca832-239">В таблице 5 перечислены способы фильтрации или проверки незапрошенного входящего трафика.</span><span class="sxs-lookup"><span data-stu-id="ca832-239">Table 5 lists the methods for filtering or inspecting unsolicited incoming traffic.</span></span>
  
|<span data-ttu-id="ca832-240">**Метод**</span><span class="sxs-lookup"><span data-stu-id="ca832-240">**Method**</span></span>|<span data-ttu-id="ca832-241">**Модель развертывания**</span><span class="sxs-lookup"><span data-stu-id="ca832-241">**Deployment model**</span></span>|
|:-----|:-----|
|<span data-ttu-id="ca832-242">1. Конечные точки и списки управления доступом, настроенные в облачных службах</span><span class="sxs-lookup"><span data-stu-id="ca832-242">1. Endpoints and ACLs configured on cloud services</span></span>  <br/> |<span data-ttu-id="ca832-243">Базовая</span><span class="sxs-lookup"><span data-stu-id="ca832-243">Classic</span></span>  <br/> |
|<span data-ttu-id="ca832-244">2. Группы безопасности сети</span><span class="sxs-lookup"><span data-stu-id="ca832-244">2. Network security groups</span></span>  <br/> |<span data-ttu-id="ca832-245">Классическая с использованием диспетчера ресурсов</span><span class="sxs-lookup"><span data-stu-id="ca832-245">Resource Manager and classic</span></span>  <br/> |
|<span data-ttu-id="ca832-246">3. Подсистема балансировки нагрузки для интернет-трафика с правилами NAT для входящего трафика</span><span class="sxs-lookup"><span data-stu-id="ca832-246">3. Internet-facing load balancer with inbound NAT rules</span></span>  <br/> |<span data-ttu-id="ca832-247">Руководитель ресурсов</span><span class="sxs-lookup"><span data-stu-id="ca832-247">Resource Manager</span></span>  <br/> |
|<span data-ttu-id="ca832-248">4. устройства сетевой безопасности в Azure Marketplace (не показаны)</span><span class="sxs-lookup"><span data-stu-id="ca832-248">4. Network security appliances in the Azure Marketplace (not shown)</span></span>  <br/> |<span data-ttu-id="ca832-249">Классическая с использованием диспетчера ресурсов</span><span class="sxs-lookup"><span data-stu-id="ca832-249">Resource Manager and classic</span></span>  <br/> |
   
 <span data-ttu-id="ca832-250">**Таблица 5. Способы подключения к виртуальным машинам и соответствующие модели развертывания Azure**</span><span class="sxs-lookup"><span data-stu-id="ca832-250">**Table 5: Methods of connecting to virtual machines and their corresponding Azure deployment models**</span></span>
  
<span data-ttu-id="ca832-251">**Рис. 7. Подключение к виртуальным машинам Azure через Интернет**</span><span class="sxs-lookup"><span data-stu-id="ca832-251">**Figure 7: Connecting to Azure virtual machines over the Internet**</span></span>

![Рис. 7. Подключение к виртуальным машинам Azure через Интернет](media/c5e3531b-170a-4482-a6ff-fb8fbbe81b35.png)
  
<span data-ttu-id="ca832-253">На рисунке 7 показано подключение компьютера с доступом в Интернет к виртуальной машине в облачной службе через конечную точку, к виртуальной машине в подсети с помощью группы безопасности сети, а также к виртуальной машине в подсети с помощью внешней подсистемы балансировки нагрузки и правил NAT для входящего трафика.</span><span class="sxs-lookup"><span data-stu-id="ca832-253">Figure 7 shows an Internet-connected computer connecting to a virtual machine in a cloud service using an endpoint, a virtual machine on a subnet using a network security group, and a virtual machine on a subnet using an external load balancer and inbound NAT rules.</span></span>
  
<span data-ttu-id="ca832-254">Дополнительная безопасность обеспечивается за счет следующего:</span><span class="sxs-lookup"><span data-stu-id="ca832-254">Additional security is provided by:</span></span>
  
- <span data-ttu-id="ca832-255">Подключение удаленного рабочего стола и подключение SSH, которые зашифрованы и используют проверку подлинности.</span><span class="sxs-lookup"><span data-stu-id="ca832-255">Remote Desktop and SSH connections, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="ca832-256">Сеансы удаленной среды PowerShell, которые зашифрованы и используют проверку подлинности.</span><span class="sxs-lookup"><span data-stu-id="ca832-256">Remote PowerShell sessions, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="ca832-257">Режим транспорта IPsec, который можно использовать для сквозного шифрования.</span><span class="sxs-lookup"><span data-stu-id="ca832-257">IPsec transport mode, which you can use for end-to-end encryption.</span></span>
    
- <span data-ttu-id="ca832-258">Защита Azure от атак DDoS, позволяющая предотвратить внешние и внутренние атаки.</span><span class="sxs-lookup"><span data-stu-id="ca832-258">Azure DDOS protection, which helps prevent external and internal attacks</span></span>
    
<span data-ttu-id="ca832-259">Для получения дополнительных сведений обратитесь [к разделу Безопасность Microsoft Cloud для корпоративных архитекторов](https://aka.ms/cloudarchsecurity) и [безопасности сети Azure](https://azure.microsoft.com/blog/azure-network-security/).</span><span class="sxs-lookup"><span data-stu-id="ca832-259">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-10-for-multiple-vnets-determine-the-vnet-to-vnet-connection-topology"></a><span data-ttu-id="ca832-260">Шаг 10. Если имеется несколько виртуальных сетей, определите топологию подключения "виртуальная сеть–виртуальная сеть".</span><span class="sxs-lookup"><span data-stu-id="ca832-260">Step 10: For multiple VNets, determine the VNet-to-VNet connection topology.</span></span>

<span data-ttu-id="ca832-261">Виртуальные сети можно подключать между собой, используя для этого такие же топологии, что и для подключения сайтов организации.</span><span class="sxs-lookup"><span data-stu-id="ca832-261">VNets can be connected to each other using topologies similar to those used for connecting the sites of an organization.</span></span>
  
<span data-ttu-id="ca832-262">Гирляндная конфигурация подразумевает последовательное подключение виртуальных сетей.</span><span class="sxs-lookup"><span data-stu-id="ca832-262">A daisy chain configuration connects the VNets in a series.</span></span>
  
<span data-ttu-id="ca832-263">**Рис. 8. Конфигурация с последовательным подключением виртуальных сетей**</span><span class="sxs-lookup"><span data-stu-id="ca832-263">**Figure 8: A daisy-chained configuration for VNets**</span></span>

![Рисунок 8: последовательное конфигурирование для виртуальных сетей Azure](media/264d5dd4-06c5-483f-9428-a18cc1f68ac1.png)
  
<span data-ttu-id="ca832-265">На рисунке 8 показано пять виртуальных сетей, подключенных к ряду с использованием последовательной конфигурации.</span><span class="sxs-lookup"><span data-stu-id="ca832-265">Figure 8 shows five VNets connected in series using a daisy-chained configuration.</span></span>
  
<span data-ttu-id="ca832-266">Звездообразная конфигурация подразумевает подключение нескольких виртуальных сетей к ряду центральных виртуальных сетей, соединенных между собой.</span><span class="sxs-lookup"><span data-stu-id="ca832-266">A spoke and hub configuration connects multiple VNets to a set of central VNets, which are themselves connected to each other.</span></span>
  
<span data-ttu-id="ca832-267">**Рис. 9. Звездообразная конфигурация виртуальных сетей**</span><span class="sxs-lookup"><span data-stu-id="ca832-267">**Figure 9: A spoke and hub configuration for VNets**</span></span>

![На рисунке 9: Конфигурация "лучевой" и "Hub" для виртуальных сетей Azure](media/dd442a38-5b76-4ac5-b743-8fc7711a91ba.png)
  
<span data-ttu-id="ca832-269">На рисунке 9 показаны шесть виртуальных сетей, где две из которых являются центральными сетями, соединенными между собой, а остальные виртуальные сети подключены к этим центральным сетям.</span><span class="sxs-lookup"><span data-stu-id="ca832-269">Figure 9 shows six VNets, two VNets are hubs that are connected to each other and also two other spoke VNets.</span></span>
  
<span data-ttu-id="ca832-270">В конфигурации полной сетки все виртуальные сети соединены непосредственно друг с другом.</span><span class="sxs-lookup"><span data-stu-id="ca832-270">A full mesh configuration connects every VNet to each other.</span></span>
  
<span data-ttu-id="ca832-271">**Рис. 10. Конфигурация полной сетки для виртуальных сетей**</span><span class="sxs-lookup"><span data-stu-id="ca832-271">**Figure 10: A full mesh configuration for VNets**</span></span>

![Рисунок 10: Конфигурация сетки для виртуальных сетей Azure](media/9dda0738-10db-4a63-95b3-79851a399b71.png)
  
<span data-ttu-id="ca832-273">На рисунке 10 показаны четыре виртуальные сети, которые подключены непосредственно друг к другу с помощью шести подключений типа "виртуальная сеть–виртуальная сеть".</span><span class="sxs-lookup"><span data-stu-id="ca832-273">Figure 10 shows four VNets that are all connected to each other, using a total of six VNet-to-VNet connections.</span></span>
  
## <a name="planning-steps-for-a-cross-premises-vnet"></a><span data-ttu-id="ca832-274">Этапы планирования для распределенной виртуальной сети</span><span class="sxs-lookup"><span data-stu-id="ca832-274">Planning steps for a cross-premises VNet</span></span>
<span data-ttu-id="ca832-275"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="ca832-275"></span></span>

<span data-ttu-id="ca832-276">Ниже перечислены шаги, которыми следует руководствоваться при планировании распределенной виртуальной сети.</span><span class="sxs-lookup"><span data-stu-id="ca832-276">Follow these steps for a cross-premises VNet.</span></span>
  
> [!TIP]
> <span data-ttu-id="ca832-277">Сведения о том, как создать имитацию гибридной среды разработки и тестирования в Azure, см. в статье [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="ca832-277">To create a simulated cross-premises dev/test environment, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span> 
  
### <a name="step-1-determine-the-cross-premises-connection-to-the-vnet-s2s-vpn-or-expressroute"></a><span data-ttu-id="ca832-278">Шаг 1. Определите тип подключения к распределенной виртуальной сети (подключение VPN типа "сеть–сеть" или ExpressRoute).</span><span class="sxs-lookup"><span data-stu-id="ca832-278">Step 1: Determine the cross-premises connection to the VNet (S2S VPN or ExpressRoute).</span></span>

<span data-ttu-id="ca832-279">В таблице 6 перечислены различные типы подключений.</span><span class="sxs-lookup"><span data-stu-id="ca832-279">Table 6 lists the different types of connections.</span></span>
  
|<span data-ttu-id="ca832-280">**Тип подключения**</span><span class="sxs-lookup"><span data-stu-id="ca832-280">**Type of connection**</span></span>|<span data-ttu-id="ca832-281">**Назначение**</span><span class="sxs-lookup"><span data-stu-id="ca832-281">**Purpose**</span></span>|
|:-----|:-----|
|<span data-ttu-id="ca832-282">VPN типа "сеть–сеть"</span><span class="sxs-lookup"><span data-stu-id="ca832-282">Site-to-Site (S2S) VPN</span></span>  <br/> |<span data-ttu-id="ca832-283">Подключите сайты 1-10 (в том числе другие виртуальных сетей) к одной виртуальной сети.</span><span class="sxs-lookup"><span data-stu-id="ca832-283">Connect 1-10 sites (including other VNets) to a single VNet.</span></span>  <br/> |
|<span data-ttu-id="ca832-284">ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="ca832-284">ExpressRoute</span></span>  <br/> |<span data-ttu-id="ca832-285">Закрытое, защищенное подключение к Azure через поставщика услуг обмена интернет-трафиком (IXP) или поставщика сетевых услуг (NSP).</span><span class="sxs-lookup"><span data-stu-id="ca832-285">A private, secure link to Azure via an Internet Exchange Provider (IXP) or a Network Service Provider (NSP).</span></span>  <br/> |
|<span data-ttu-id="ca832-286">Подключение VPN типа "точка–сеть"</span><span class="sxs-lookup"><span data-stu-id="ca832-286">Point-to-Site (P2S) VPN</span></span>  <br/> |<span data-ttu-id="ca832-287">Подключение отдельного компьютера к виртуальной сети.</span><span class="sxs-lookup"><span data-stu-id="ca832-287">Connects a single computer to a VNet.</span></span>  <br/> |
|<span data-ttu-id="ca832-288">Пиринговая виртуальная сеть или VNet-to-VNet (V2V) VPN </span><span class="sxs-lookup"><span data-stu-id="ca832-288">VNet peering or VNet-to-VNet (V2V) VPN</span></span>  <br/> |<span data-ttu-id="ca832-289">Подключение одной виртуальной сети к другой.</span><span class="sxs-lookup"><span data-stu-id="ca832-289">Connects a VNet to another VNet.</span></span>  <br/> |
   
 <span data-ttu-id="ca832-290">**Таблица 6. Типы подключений для распределенных виртуальных сетей**</span><span class="sxs-lookup"><span data-stu-id="ca832-290">**Table 6: The types of connections for cross-premises VNets**</span></span>
  
<span data-ttu-id="ca832-291">Для получения дополнительных сведений о максимальном количестве подключений, ознакомьтесь с разделом [ограничения сети](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span><span class="sxs-lookup"><span data-stu-id="ca832-291">For more information on the maximum number of connections, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="ca832-292">Дополнительные сведения о VPN-устройствах можно узнать в статье [VPN-устройства для подключений к виртуальной сети типа](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices)"сеть-сеть".</span><span class="sxs-lookup"><span data-stu-id="ca832-292">For more information about VPN devices, see [VPN devices for site-to-site virtual network connections](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="ca832-293">Для получения дополнительных сведений об одноранговом уровне виртуальной сети обратитесь к разделу [пиринг виртуальной](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview)сети.</span><span class="sxs-lookup"><span data-stu-id="ca832-293">For more information about VNet peering, see [VNet peering](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview).</span></span>
  
<span data-ttu-id="ca832-294">**Рис. 11. Четыре способа подключения к распределенной виртуальной сети**</span><span class="sxs-lookup"><span data-stu-id="ca832-294">**Figure 11: The four ways to connect to a cross-premises VNet**</span></span>

![На рисунке 11: три способа подключения к виртуальной сети Azure с несколькими организациями](media/d5d4a625-cfbd-4a77-9159-eaca69d07e93.png)
  
<span data-ttu-id="ca832-296">На рисунке 11 показана виртуальная сеть с четырьмя типами подключений: подключение к P2S с компьютера, VPN-подключение S2S из локальной сети, подключение ExpressRoute из локальной сети и подключение типа "сеть-сеть" из другой виртуальной сети.</span><span class="sxs-lookup"><span data-stu-id="ca832-296">Figure 11 shows a VNet with the four types of connections: a P2S connection from a computer, an S2S VPN connection from an on-premises network, an ExpressRoute connection from an on-premises network, and a VNet-to-VNet connection from another VNet.</span></span> 
  
<span data-ttu-id="ca832-297">Подключиться к виртуальным машинам в виртуальной сети можно следующими способами:</span><span class="sxs-lookup"><span data-stu-id="ca832-297">You can connect to VMs in a VNet in the following ways:</span></span>
  
- <span data-ttu-id="ca832-298">Администрирование виртуальных машин в виртуальной сети из локальной сети или через Интернет</span><span class="sxs-lookup"><span data-stu-id="ca832-298">Administration of VNet VMs from your on-premises network or the Internet</span></span>
    
- <span data-ttu-id="ca832-299">Доступ к рабочей ИТ-нагрузке из локальной сети</span><span class="sxs-lookup"><span data-stu-id="ca832-299">IT workload access from your on-premises network</span></span>
    
- <span data-ttu-id="ca832-300">Расширение сети с помощью дополнительных виртуальных сетей</span><span class="sxs-lookup"><span data-stu-id="ca832-300">Extension of your network through additional VNets</span></span>
    
<span data-ttu-id="ca832-301">Безопасность подключений обеспечивается за счет следующего:</span><span class="sxs-lookup"><span data-stu-id="ca832-301">Security for connections is provided by the following:</span></span>
  
- <span data-ttu-id="ca832-302">Для подключения типа "точка–сеть" используется протокол Secure Socket Tunneling Protocol (SSTP) </span><span class="sxs-lookup"><span data-stu-id="ca832-302">P2S uses the Secure Socket Tunneling Protocol (SSTP)</span></span> 
    
- <span data-ttu-id="ca832-303">Для подключений VPN типа "сеть–сеть" и "виртуальная сеть–виртуальная сеть" используется туннельный режим IPsec с шифрованием AES256</span><span class="sxs-lookup"><span data-stu-id="ca832-303">S2S and VNet-to-VNet VPN connections use IPsec tunnel mode with AES256</span></span>
    
- <span data-ttu-id="ca832-304">ExpressRoute представляет собой частное подключение WAN</span><span class="sxs-lookup"><span data-stu-id="ca832-304">ExpressRoute is a private WAN connection</span></span>
    
<span data-ttu-id="ca832-305">Для получения дополнительных сведений обратитесь [к разделу Безопасность Microsoft Cloud для корпоративных архитекторов](https://aka.ms/cloudarchsecurity) и [безопасности сети Azure](https://azure.microsoft.com/blog/azure-network-security/).</span><span class="sxs-lookup"><span data-stu-id="ca832-305">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-2-determine-the-on-premises-vpn-device-or-router"></a><span data-ttu-id="ca832-306">Шаг 2. Определите локальное VPN-устройство или маршрутизатор.</span><span class="sxs-lookup"><span data-stu-id="ca832-306">Step 2: Determine the on-premises VPN device or router.</span></span>

<span data-ttu-id="ca832-307">Локальное VPN-устройство или маршрутизатор выступает в качестве:</span><span class="sxs-lookup"><span data-stu-id="ca832-307">Your on-premises VPN device or router acts as:</span></span>
  
- <span data-ttu-id="ca832-308">оконечного узла IPsec подключения VPN типа "сеть–сеть" от шлюза Azure;</span><span class="sxs-lookup"><span data-stu-id="ca832-308">An IPsec peer, terminating the S2S VPN connection from the Azure gateway.</span></span>
    
- <span data-ttu-id="ca832-309">узла BPG и оконечной точки для частного пирингового подключения ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="ca832-309">The BPG peer and termination point for the private peering ExpressRoute connection.</span></span>
    
<span data-ttu-id="ca832-310">**Рис. 12. Локальный маршрутизатор или устройство VPN**</span><span class="sxs-lookup"><span data-stu-id="ca832-310">**Figure 12: The on-premises VPN router or device**</span></span>

![Рис. 12. Локальный маршрутизатор или устройство VPN](media/bd221468-a660-4730-aa55-0426986480b9.png)
  
<span data-ttu-id="ca832-312">На рисунке 12 показана распределенная виртуальная сеть, подключенная к локальному VPN-устройству или маршрутизатору.</span><span class="sxs-lookup"><span data-stu-id="ca832-312">Figure 12 shows a cross-premises VNet connected to an on-premises VPN router or device.</span></span>
  
<span data-ttu-id="ca832-313">Более подробную информацию можно узнать в разделе [о шлюзе VPN](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways).</span><span class="sxs-lookup"><span data-stu-id="ca832-313">For more information, see [About VPN gateway](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways).</span></span>
  
### <a name="step-3-add-routes-to-your-intranet-to-make-the-address-space-of-the-vnet-reachable"></a><span data-ttu-id="ca832-314">Шаг 3: Добавление маршрутов в интрасеть для предоставления достижимости адресного пространства для виртуальной сети.</span><span class="sxs-lookup"><span data-stu-id="ca832-314">Step 3: Add routes to your intranet to make the address space of the VNet reachable.</span></span>

<span data-ttu-id="ca832-315">Маршрут к виртуальной сети из локальной сети включает следующее:</span><span class="sxs-lookup"><span data-stu-id="ca832-315">Routing to VNets from on-premises consists of the following:</span></span>
  
1. <span data-ttu-id="ca832-316">Маршрут для адресного пространства виртуальной сети до вашего VPN-устройства.</span><span class="sxs-lookup"><span data-stu-id="ca832-316">A route for the VNet address space that points toward your VPN device.</span></span>
    
2. <span data-ttu-id="ca832-317">Маршрут для адресного пространства виртуальной сети на VPN-устройстве до подключения VPN типа "сеть–сеть"или подключения ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="ca832-317">A route for the VNet address space on your VPN device that points across the S2S VPN or ExpressRoute connection</span></span>
    
<span data-ttu-id="ca832-318">**Рис. 13. Локальные маршруты, необходимые для того, чтобы сделать виртуальную сеть доступной**</span><span class="sxs-lookup"><span data-stu-id="ca832-318">**Figure 13: The on-premises routes needed to make a VNet reachable**</span></span>

![Рисунок 13: Локальные маршруты, необходимые для обеспечения достижимости виртуальной сети Azure](media/7a1e20c1-fbc4-4cb9-9961-735da4e23307.png)
  
<span data-ttu-id="ca832-320">На рисунке 13 показаны сведения о маршрутах, необходимые локальным маршрутизаторам и VPN-устройству или маршрутизатору, представляющему адресное пространство виртуальной сети.</span><span class="sxs-lookup"><span data-stu-id="ca832-320">Figure 13 shows the routing information needed by the on-premises routers and the VPN router or device that represents the address space of the VNet.</span></span>
  
### <a name="step-4-for-expressroute-plan-for-the-new-connection-with-your-provider"></a><span data-ttu-id="ca832-321">Шаг 4. Если используется подключение ExpressRoute, спланируйте новое подключение вместе со своим поставщиком.</span><span class="sxs-lookup"><span data-stu-id="ca832-321">Step 4: For ExpressRoute, plan for the new connection with your provider.</span></span>

<span data-ttu-id="ca832-322">Создать частное пиринговое соединение ExpressRoute между локальной сетью и облаком Майкрософт можно тремя различными способами:</span><span class="sxs-lookup"><span data-stu-id="ca832-322">You can create an ExpressRoute connection with private peering between your on-premises network and the Microsoft cloud in three different ways:</span></span>
  
- <span data-ttu-id="ca832-323">Совместное размещение в облачном обменнике</span><span class="sxs-lookup"><span data-stu-id="ca832-323">Co-located at a cloud exchange</span></span>
    
- <span data-ttu-id="ca832-324">Подключение типа "точка-точка" через Ethernet</span><span class="sxs-lookup"><span data-stu-id="ca832-324">Point-to-point Ethernet connections</span></span>
    
- <span data-ttu-id="ca832-325">Подключение типа "любой-к-любому" (IP-VPN)</span><span class="sxs-lookup"><span data-stu-id="ca832-325">Any-to-any (IP VPN) networks</span></span>
    
<span data-ttu-id="ca832-326">**Рис. 14. Использование ExpressRoute для подключения к распределенной виртуальной сети**</span><span class="sxs-lookup"><span data-stu-id="ca832-326">**Figure 14: Using ExpressRoute to connect to a cross-premises VNet**</span></span>

![Рисунок 14: использование ExpressRoute для подключения к нескольким локальным виртуальным сетям Azure](media/7030bd39-69a6-4283-8567-3434e1ab6ba6.png)
  
<span data-ttu-id="ca832-328">На рисунке 14 показана распределенная виртуальная сеть и подключение ExpressRoute от локального маршрутизатора к Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="ca832-328">Figure 14 shows a cross-premises VNet and an ExpressRoute connection from an on-premises router to Microsoft Azure.</span></span>
  
<span data-ttu-id="ca832-329">Дополнительные сведения см. в статье [ExpressRoute для подключения к Microsoft Cloud](expressroute-for-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="ca832-329">For more information, see [ExpressRoute for Microsoft cloud connectivity](expressroute-for-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-5-determine-the-local-network-address-space-for-the-azure-gateway"></a><span data-ttu-id="ca832-330">Шаг 5. Определите адресное пространство локальной сети для шлюза Azure.</span><span class="sxs-lookup"><span data-stu-id="ca832-330">Step 5: Determine the Local Network address space for the Azure gateway.</span></span>

<span data-ttu-id="ca832-331">Для маршрутизации трафика в локальную сеть или другие виртуальные сети Azure переадресовывает его через шлюз Azure, соответствующий адресному пространству локальной сети, которое назначено шлюзу.</span><span class="sxs-lookup"><span data-stu-id="ca832-331">For the routing to on-premises or other VNets from a VNet, Azure forwards traffic across an Azure gateway that matches the Local Network address space assigned to the gateway.</span></span>
  
<span data-ttu-id="ca832-332">**Рис. 15. Адресное пространство локальной сети для распределенной виртуальной сети**</span><span class="sxs-lookup"><span data-stu-id="ca832-332">**Figure 15: The Local Network address space for a cross-premises VNet**</span></span>

![Рисунок 15: адресное пространство локальной сети для локальной виртуальной сети Azure](media/e3af2652-8b8e-4551-9a0b-b550e6e7e3c0.png)
  
<span data-ttu-id="ca832-334">На рисунке 15 показаны распределенная виртуальная сеть и адресное пространство локальной сети на шлюзе Azure, которое представляет собой достижимое адресное пространство локальной сети. </span><span class="sxs-lookup"><span data-stu-id="ca832-334">Figure 15 shows a cross-premises VNet and the Local Network address space on the Azure gateway, which represents the reachable address space on the on-premises network.</span></span> 
  
<span data-ttu-id="ca832-335">Адресное пространство локальной сети можно определить следующими способами:</span><span class="sxs-lookup"><span data-stu-id="ca832-335">You can define the Local Network address space in these ways:</span></span>
  
- <span data-ttu-id="ca832-336">Способ 1. Создание списка префиксов адресного пространства, которые требуются или используются (этот список необходимо обновлять при добавлении новых подсетей).</span><span class="sxs-lookup"><span data-stu-id="ca832-336">Option 1: The list of prefixes for the address space currently needed or in use (updates might be needed when you add new subnets).</span></span>
    
- <span data-ttu-id="ca832-337">Способ 2. Использование всего адресного пространства локальной сети (этот список необходимо обновлять только при добавлении нового адресного пространства).</span><span class="sxs-lookup"><span data-stu-id="ca832-337">Option 2: Your entire on-premises address space (updates only needed when you add new address space).</span></span>
    
<span data-ttu-id="ca832-338">Поскольку шлюз Azure не поддерживает суммированные маршруты, необходимо определить адресное пространство локальной сети для способа 2, исключив из него адресное пространство виртуальной сети.</span><span class="sxs-lookup"><span data-stu-id="ca832-338">Because the Azure gateway does not allow summarized routes, you must define the Local Network address space for option 2 so that it does not include the VNet address space.</span></span>
  
<span data-ttu-id="ca832-339">**Рис. 16. Пробел в адресном пространстве, созданный адресным пространством виртуальной сети**</span><span class="sxs-lookup"><span data-stu-id="ca832-339">**Figure 16: The address space hole created by the VNet address space**</span></span>

![Рисунок 16: адресное пространство, созданное адресным пространством виртуальной сети](media/e79c4840-f9e3-4741-9b72-59db6043aefa.png)
  
<span data-ttu-id="ca832-341">На рисунке 16 представлено адресное пространство с корневым пространством и адресным пространством виртуальной сети.</span><span class="sxs-lookup"><span data-stu-id="ca832-341">Figure 16 shows a representation of an address space, with the root space and the VNet address space.</span></span>
  
<span data-ttu-id="ca832-342">Ниже приведен пример определения префиксов для адресного пространства локальной сети вокруг адресного пространства "дыра", созданного виртуальной сетью:</span><span class="sxs-lookup"><span data-stu-id="ca832-342">Here is an example of defining the prefixes for the Local Network address space around the address space "hole" created by the VNet:</span></span>
  
- <span data-ttu-id="ca832-p114">Организация использует фрагменты частного адресного пространства (10.0.0.0/8, 172.16.0.0/12 и 192.168.0.0/16) в своей локальной сети. Был выбран способ 2, а в качестве адресного пространства виртуальной сети — пространство 10.100.100.0/24.</span><span class="sxs-lookup"><span data-stu-id="ca832-p114">An organization uses portions of the private address space (10.0.0.0/8, 172.16.0.0/12, and 192.168.0.0/16) across their on-premises network. They chose option 2 and 10.100.100.0/24 as their VNet address space.</span></span>
    
<span data-ttu-id="ca832-345">В таблице 7 представлены действия и полученные в их результате префиксы, определяющие адресное пространство локальной сети для этого примера.</span><span class="sxs-lookup"><span data-stu-id="ca832-345">Table 7 shows the steps and resulting prefixes that define the Local Network address space for this example.</span></span>
  
|<span data-ttu-id="ca832-346">**Этап**</span><span class="sxs-lookup"><span data-stu-id="ca832-346">**Step**</span></span>|<span data-ttu-id="ca832-347">**Results**</span><span class="sxs-lookup"><span data-stu-id="ca832-347">**Results**</span></span>|
|:-----|:-----|
|<span data-ttu-id="ca832-348">1. Создание списка префиксов, которые отсутствуют в корневом пространстве, для адресного пространства виртуальной сети.</span><span class="sxs-lookup"><span data-stu-id="ca832-348">1. List the prefixes that are not the root space for the VNet address space.</span></span>  <br/> |<span data-ttu-id="ca832-349">172.16.0.0/12 и 192.168.0.0/16</span><span class="sxs-lookup"><span data-stu-id="ca832-349">172.16.0.0/12 and 192.168.0.0/16</span></span>  <br/> |
|<span data-ttu-id="ca832-350">2. переЧислите непересекающиеся префиксы для переменных октетов, которые не включают последний использованный октет в адресном пространстве виртуальной сети.</span><span class="sxs-lookup"><span data-stu-id="ca832-350">2. List the non-overlapping prefixes for variable octets up to but not including the last used octet in the VNet address space.</span></span>  <br/> |<span data-ttu-id="ca832-351">10.0.0.0/16, 10.1.0.0/16... 10.99.0.0/16, 10.101.0.0/16... 10.254.0.0/16, 10.255.0.0/16 (префиксы 255, пропуск 10.100.0.0/16)</span><span class="sxs-lookup"><span data-stu-id="ca832-351">10.0.0.0/16, 10.1.0.0/16…10.99.0.0/16, 10.101.0.0/16…10.254.0.0/16, 10.255.0.0/16 (255 prefixes, skipping 10.100.0.0/16)</span></span>  <br/> |
|<span data-ttu-id="ca832-352">3. переЧислите непересекающиеся префиксы в последнем использованном октете адресного пространства виртуальной сети.</span><span class="sxs-lookup"><span data-stu-id="ca832-352">3. List the non-overlapping prefixes within the last used octet of the VNet address space.</span></span>  <br/> |<span data-ttu-id="ca832-353">10.100.0.0/24, 10.100.1.0/24... 10.100.99.0/24, 10.100.101.0/24... 10.100.254.0/24, 10.100.0.255.0/24 (префиксы 255, пропуск 10.100.100.0/24)</span><span class="sxs-lookup"><span data-stu-id="ca832-353">10.100.0.0/24, 10.100.1.0/24…10.100.99.0/24, 10.100.101.0/24…10.100.254.0/24, 10.100.0.255.0/24 (255 prefixes, skipping 10.100.100.0/24)</span></span>  <br/> |
   
 <span data-ttu-id="ca832-354">**Таблица 7. Пример сетевого пространства локальных адресов**</span><span class="sxs-lookup"><span data-stu-id="ca832-354">**Table 7: Example Local Address network space**</span></span>
  
### <a name="step-6-configure-on-premises-dns-servers-for-dns-replication-with-dns-servers-hosted-in-azure"></a><span data-ttu-id="ca832-355">Шаг 6. Настройте локальные DNS-серверы на репликацию DNS с помощью DNS-серверов, размещенных в Azure.</span><span class="sxs-lookup"><span data-stu-id="ca832-355">Step 6: Configure on-premises DNS servers for DNS replication with DNS servers hosted in Azure.</span></span>

<span data-ttu-id="ca832-356">Чтобы локальные компьютеры могли разрешать имена серверов, размещенных в Azure, а последние могли разрешать имена локальных компьютеров, настройте следующее:</span><span class="sxs-lookup"><span data-stu-id="ca832-356">To ensure that on-premises computers can resolve the names of Azure-based servers and Azure-based servers can resolve the names of on-premises computers, configure:</span></span>
  
- <span data-ttu-id="ca832-357">DNS-серверы в вашей виртуальной сети на переадресацию на локальные DNS-серверы;</span><span class="sxs-lookup"><span data-stu-id="ca832-357">The DNS servers in your VNet to forward to on-premises DNS servers</span></span>
    
- <span data-ttu-id="ca832-358">репликацию DNS для соответствующих зон между DNS-серверами локальной и виртуальной сетей.</span><span class="sxs-lookup"><span data-stu-id="ca832-358">DNS replication of the appropriate zones between DNS servers on-premises and in the VNet</span></span>
    
<span data-ttu-id="ca832-359">**Рис. 17. Репликация и переадресация DNS для DNS-сервера в распределенной виртуальной сети**</span><span class="sxs-lookup"><span data-stu-id="ca832-359">**Figure 17: DNS replication and forwarding for a DNS server in a cross-premises VNet**</span></span>

![Рисунок 17: репликация и пересылка DNS для DNS-сервера в виртуальной сети Azure с несколькими организациями](media/ab55e5ce-ccb0-49d4-a301-657a727f97b2.png)
  
<span data-ttu-id="ca832-p115">На рисунке 17 показана распределенная виртуальная сеть с DNS-серверами в локальной сети и подсети в виртуальной сети. Между этими двумя DNS-серверами настроены репликация и переадресация DNS.</span><span class="sxs-lookup"><span data-stu-id="ca832-p115">Figure 17 shows a cross-premises VNet with DNS servers in the on-premises network and on a subnet in the VNet. DNS replication and forwarding has been configured between the two DNS servers.</span></span>
  
### <a name="step-7-determine-the-use-of-forced-tunneling"></a><span data-ttu-id="ca832-363">Шаг 7. Определите использование принудительного туннелирования.</span><span class="sxs-lookup"><span data-stu-id="ca832-363">Step 7: Determine the use of forced tunneling.</span></span>

<span data-ttu-id="ca832-364">Системный маршрут по умолчанию для подсетей Azure указывает на Интернет.</span><span class="sxs-lookup"><span data-stu-id="ca832-364">The default system route for Azure subnets points to the Internet.</span></span> <span data-ttu-id="ca832-365">Чтобы убедиться, что весь трафик из виртуальных машин проходит через локальное подключение, создайте таблицу маршрутизации с маршрутом по умолчанию, который использует шлюз Azure в качестве адреса следующего прыжка.</span><span class="sxs-lookup"><span data-stu-id="ca832-365">To ensure that all traffic from virtual machines travels across the cross-premises connection, create a routing table with the default route that uses the Azure gateway as its next-hop address.</span></span> <span data-ttu-id="ca832-366">Затем вы связываете таблицу маршрутизации с подсетью.</span><span class="sxs-lookup"><span data-stu-id="ca832-366">You then associate the route table with the subnet.</span></span> <span data-ttu-id="ca832-367">Это называется принудительным туннелированием.</span><span class="sxs-lookup"><span data-stu-id="ca832-367">This is known as forced tunneling.</span></span> <span data-ttu-id="ca832-368">Для получения дополнительных сведений см [Настройка принудительного туннелирования](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm).</span><span class="sxs-lookup"><span data-stu-id="ca832-368">For more information, see [Configure forced tunneling](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm).</span></span>
  
<span data-ttu-id="ca832-369">**Рис. 18. Пользовательские маршруты и принудительное туннелирование для распределенной виртуальной сети**</span><span class="sxs-lookup"><span data-stu-id="ca832-369">**Figure 18: User-defined routes and forced tunneling for a cross-premises VNet**</span></span>

![Рисунок 18: пользовательские маршруты и принудительное туннелирование для виртуальной сети Azure с несколькими организациями](media/1e545ec6-c2d9-48d2-bb5e-e0a581fee004.png)
  
<span data-ttu-id="ca832-371">На рисунке 18 показана распределенная виртуальная сеть с пользовательским маршрутом для подсети, указывающей на шлюз Azure.</span><span class="sxs-lookup"><span data-stu-id="ca832-371">Figure 18 shows a cross-premises VNet with a user-defined route for a subnet pointing to the Azure gateway.</span></span>
  
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="ca832-372">Ферма SharePoint Server 2016 в Azure</span><span class="sxs-lookup"><span data-stu-id="ca832-372">SharePoint Server 2016 farm in Azure</span></span>
<span data-ttu-id="ca832-373"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="ca832-373"></span></span>

<span data-ttu-id="ca832-374">Примером рабочей нагрузки в интрасети, размещенной в Azure IaaS, является высокодоступная многоуровневая ферма SharePoint Server 2016.</span><span class="sxs-lookup"><span data-stu-id="ca832-374">An example of an intranet IT workload hosted in Azure IaaS is a highly-available, multi-tier SharePoint Server 2016 farm.</span></span>
  
<span data-ttu-id="ca832-375">**Рисунок 19. Высокодоступная ферма SharePoint Server 2016 в интрасети в Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="ca832-375">**Figure 19: A highly-available intranet SharePoint Server 2016 farm in Azure IaaS**</span></span>

![Ферма SharePoint Server 2016 С высоким уровнем доступности в Azure IaaS](media/3a922e21-df91-455f-ba90-78abdd48d98d.png)
  
<span data-ttu-id="ca832-377">На рисунке 19 показаны девять серверов фермы SharePoint Server 2016, развернутые в распределенной виртуальной сети, в которой используются внутренние подсистемы балансировки нагрузки для уровней сервера переднего плана и данных.</span><span class="sxs-lookup"><span data-stu-id="ca832-377">Figure 19 shows the nine servers of a SharePoint Server 2016 farm deployed in a cross-premises VNet that uses internal load balancers for the front-end and data tiers.</span></span> <span data-ttu-id="ca832-378">Для получения дополнительных сведений, включая пошаговые инструкции по проектированию и развертыванию, ознакомьтесь со статьей [SharePoint Server 2016 в Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure).</span><span class="sxs-lookup"><span data-stu-id="ca832-378">For more information, including step-by-step design and deployment instructions, see [SharePoint Server 2016 in Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure).</span></span>
  
> [!TIP]
> <span data-ttu-id="ca832-379">Чтобы создать ферму SharePoint Server 2016 с одним сервером в имитируемой распределенной виртуальной сети, ознакомьтесь со статьей [интрасеть SharePoint server 2016 в среде разработки и тестирования Azure](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment).</span><span class="sxs-lookup"><span data-stu-id="ca832-379">To create a single-server SharePoint Server 2016 farm in a simulated cross-premises VNet, see [Intranet SharePoint Server 2016 in Azure dev/test environment](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment).</span></span> 
  
<span data-ttu-id="ca832-380">Дополнительные примеры рабочих нагрузок, развернутых на виртуальных машинах в виртуальной сети Azure, приведены в статье [гибридные облачные сценарии для Azure IaaS](https://docs.microsoft.com/office365/enterprise/hybrid-cloud-scenarios-for-azure-iaas).</span><span class="sxs-lookup"><span data-stu-id="ca832-380">For additional examples of IT workloads deployed on virtual machines in a cross-premises Azure virtual network, see [Hybrid cloud scenarios for Azure IaaS](https://docs.microsoft.com/office365/enterprise/hybrid-cloud-scenarios-for-azure-iaas).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ca832-381">См. также</span><span class="sxs-lookup"><span data-stu-id="ca832-381">See also</span></span>

[<span data-ttu-id="ca832-382">Организация сети в Microsoft Cloud для корпоративных архитекторов</span><span class="sxs-lookup"><span data-stu-id="ca832-382">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="ca832-383">Ресурсы, посвященные ИТ-архитектуре Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="ca832-383">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)


