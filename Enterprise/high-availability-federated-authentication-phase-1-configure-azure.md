---
title: Федеративная проверка подлинности высокой доступности Azure настроить этап 1
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/06/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 91266aac-4d00-4b5f-b424-86a1a837792c
description: Сводка. Настройка инфраструктуры Microsoft Azure для размещения федеративной проверки подлинности с высоким уровнем доступности для Office 365.
ms.openlocfilehash: e88204d7f69c56c951f5d6ebd4d978c96e4c52ba
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915464"
---
# <a name="high-availability-federated-authentication-phase-1-configure-azure"></a><span data-ttu-id="9e017-103">Этап 1. Федеративная проверка подлинности для обеспечения высокой доступности: настройка Azure</span><span class="sxs-lookup"><span data-stu-id="9e017-103">High availability federated authentication Phase 1: Configure Azure</span></span>

 <span data-ttu-id="9e017-104">**Сводка.** Настройка инфраструктуры Microsoft Azure для размещения федеративной проверки подлинности с высоким уровнем доступности для Office 365.</span><span class="sxs-lookup"><span data-stu-id="9e017-104">**Summary:** Configure the Microsoft Azure infrastructure to host high availability federated authentication for Office 365.</span></span>
  
<span data-ttu-id="9e017-p101">На этом этапе создается группы ресурсов, виртуальные сети (VNet) и доступность наборы в Azure, в котором будет размещаться виртуальных машин в этапы 2, 3 и 4. Необходимо выполнить данный этап перед перемещением на [высокой доступности федеративных проверки подлинности этап 2: Настройка контроллеров домена](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). В разделе [Развертывание высокой доступности федеративной проверки подлинности для Office 365 в Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) все этапы.</span><span class="sxs-lookup"><span data-stu-id="9e017-p101">In this phase, you create the resource groups, virtual network (VNet), and availability sets in Azure that will host the virtual machines in phases 2, 3, and 4. You must complete this phase before moving on to [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
<span data-ttu-id="9e017-108">Необходимо быть, подготовленные в Azure с помощью следующих основных компонентов:</span><span class="sxs-lookup"><span data-stu-id="9e017-108">Azure must be provisioned with these basic components:</span></span>
  
- <span data-ttu-id="9e017-109">Группы ресурсов</span><span class="sxs-lookup"><span data-stu-id="9e017-109">Resource groups</span></span>
    
- <span data-ttu-id="9e017-110">Нелокальная виртуальная сеть Azure с подсетями для размещения виртуальных машин Azure</span><span class="sxs-lookup"><span data-stu-id="9e017-110">A cross-premises Azure virtual network (VNet) with subnets for hosting the Azure virtual machines</span></span>
    
- <span data-ttu-id="9e017-111">Группы безопасности сети для изоляции подсети</span><span class="sxs-lookup"><span data-stu-id="9e017-111">Network security groups for performing subnet isolation</span></span>
    
- <span data-ttu-id="9e017-112">Группы доступности</span><span class="sxs-lookup"><span data-stu-id="9e017-112">Availability sets</span></span>
    
## <a name="configure-azure-components"></a><span data-ttu-id="9e017-113">Настройка компонентов Azure</span><span class="sxs-lookup"><span data-stu-id="9e017-113">Configure Azure components</span></span>

<span data-ttu-id="9e017-p102">Перед началом настройки Azure компонентов, заполните поля в следующих таблицах. Для помощи в процедуры для настройки Azure, печать в этом разделе запишите требуемые данные или скопируйте в этом разделе документа и его можно заполнить. Для параметров VNet заполните поля в таблице V.</span><span class="sxs-lookup"><span data-stu-id="9e017-p102">Before you begin configuring Azure components, fill in the following tables. To assist you in the procedures for configuring Azure, print this section and write down the needed information or copy this section to a document and fill it in. For the settings of the VNet, fill in Table V.</span></span>
  
|<span data-ttu-id="9e017-117">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="9e017-117">**Item**</span></span>|<span data-ttu-id="9e017-118">**Параметр конфигурации**</span><span class="sxs-lookup"><span data-stu-id="9e017-118">**Configuration setting**</span></span>|<span data-ttu-id="9e017-119">**Описание**</span><span class="sxs-lookup"><span data-stu-id="9e017-119">**Description**</span></span>|<span data-ttu-id="9e017-120">**Значение**</span><span class="sxs-lookup"><span data-stu-id="9e017-120">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="9e017-121">1.</span><span class="sxs-lookup"><span data-stu-id="9e017-121">1.</span></span>  <br/> |<span data-ttu-id="9e017-122">Имя виртуальной сети</span><span class="sxs-lookup"><span data-stu-id="9e017-122">VNet name</span></span>  <br/> |<span data-ttu-id="9e017-123">Имя виртуальной сети (например, FedAuthNet).</span><span class="sxs-lookup"><span data-stu-id="9e017-123">A name to assign to the VNet (example FedAuthNet).</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="9e017-124">2.</span><span class="sxs-lookup"><span data-stu-id="9e017-124">2.</span></span>  <br/> |<span data-ttu-id="9e017-125">
Расположение виртуальной сети</span><span class="sxs-lookup"><span data-stu-id="9e017-125">VNet location</span></span>  <br/> |<span data-ttu-id="9e017-126">Региональный центр обработки данных Azure, в котором будет расположена виртуальная сеть.</span><span class="sxs-lookup"><span data-stu-id="9e017-126">The regional Azure datacenter that will contain the virtual network.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="9e017-127">3.</span><span class="sxs-lookup"><span data-stu-id="9e017-127">3.</span></span>  <br/> |<span data-ttu-id="9e017-128">IP-адрес VPN-устройства</span><span class="sxs-lookup"><span data-stu-id="9e017-128">VPN device IP address</span></span>  <br/> |<span data-ttu-id="9e017-129">Общедоступный IPv4-адрес интерфейса VPN-устройства в Интернете.</span><span class="sxs-lookup"><span data-stu-id="9e017-129">The public IPv4 address of your VPN device's interface on the Internet.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="9e017-130">4.</span><span class="sxs-lookup"><span data-stu-id="9e017-130">4.</span></span>  <br/> |<span data-ttu-id="9e017-131">Адресное пространство виртуальной сети</span><span class="sxs-lookup"><span data-stu-id="9e017-131">VNet address space</span></span>  <br/> |<span data-ttu-id="9e017-p103">Адресное пространство виртуальной сети. Чтобы определить это адресное пространство, обратитесь в ИТ-отдел.</span><span class="sxs-lookup"><span data-stu-id="9e017-p103">The address space for the virtual network. Work with your IT department to determine this address space.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="9e017-134">5.</span><span class="sxs-lookup"><span data-stu-id="9e017-134">5.</span></span>  <br/> |<span data-ttu-id="9e017-135">Общий ключ IPsec</span><span class="sxs-lookup"><span data-stu-id="9e017-135">IPsec shared key</span></span>  <br/> |<span data-ttu-id="9e017-p104">32 символов в случайном порядке, буквенно-цифровой строка, которая будет использоваться для проверки подлинности обеих сторон VPN-подключения веб сайта. Работа с ИТ или отдела безопасности для определения это значение ключа. Кроме того в разделе [Создать строку в случайном порядке для предварительного ключа IPsec](http://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).</span><span class="sxs-lookup"><span data-stu-id="9e017-p104">A 32-character random, alphanumeric string that will be used to authenticate both sides of the site-to-site VPN connection. Work with your IT or security department to determine this key value. Alternately, see [Create a random string for an IPsec preshared key](http://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  </span></span><br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="9e017-139">**Таблица V. Настройка распределенной виртуальной сети**</span><span class="sxs-lookup"><span data-stu-id="9e017-139">**Table V: Cross-premises virtual network configuration**</span></span>
  
<span data-ttu-id="9e017-p105">После этого укажите подсети этого решения в таблице S. Все адресные пространства должны быть указаны в формате CIDR (формате префиксов сети). Пример: 10.24.64.0/20.</span><span class="sxs-lookup"><span data-stu-id="9e017-p105">Next, fill in Table S for the subnets of this solution. All address spaces should be in Classless Interdomain Routing (CIDR) format, also known as network prefix format. An example is 10.24.64.0/20.</span></span>
  
<span data-ttu-id="9e017-p106">Для первых трех подсетей укажите имя и одно пространство IP-адресов на основе адресного пространства виртуальной сети. Для подсети шлюза определите 27-битовое адресное пространство (с длиной префикса /27) для подсети шлюза Azure шлюза. Для этого выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="9e017-p106">For the first three subnets, specify a name and a single IP address space based on the virtual network address space. For the gateway subnet, determine the 27-bit address space (with a /27 prefix length) for the Azure gateway subnet with the following:</span></span>
  
1. <span data-ttu-id="9e017-145">Для переменных битов в адресном пространстве виртуальной сети задайте значение 1 (не больше бит, используемых подсетью шлюза), а для остальных битов задайте значение 0.</span><span class="sxs-lookup"><span data-stu-id="9e017-145">Set the variable bits in the address space of the VNet to 1, up to the bits being used by the gateway subnet, then set the remaining bits to 0.</span></span>
    
2. <span data-ttu-id="9e017-146">Преобразуйте результат в десятичное число и выразите его как адресное пространство, длина префикса которого соответствует размеру подсети шлюза.</span><span class="sxs-lookup"><span data-stu-id="9e017-146">Convert the resulting bits to decimal and express it as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="9e017-147">В разделе [Калькулятор пространства адресов для подсетей Azure шлюза](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) блок команд PowerShell и C# или Python консольное приложение, используемая для выполнения этого вычисления для вас.</span><span class="sxs-lookup"><span data-stu-id="9e017-147">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for a PowerShell command block and C# or Python console application that performs this calculation for you.</span></span>
  
<span data-ttu-id="9e017-148">Чтобы определить эти адресные пространства из адресного пространства виртуальной сети, обратитесь в ИТ-отдел.</span><span class="sxs-lookup"><span data-stu-id="9e017-148">Work with your IT department to determine these address spaces from the virtual network address space.</span></span>
  
|<span data-ttu-id="9e017-149">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="9e017-149">**Item**</span></span>|<span data-ttu-id="9e017-150">**Имя подсети**</span><span class="sxs-lookup"><span data-stu-id="9e017-150">**Subnet name**</span></span>|<span data-ttu-id="9e017-151">**Адресное пространство подсети**</span><span class="sxs-lookup"><span data-stu-id="9e017-151">**Subnet address space**</span></span>|<span data-ttu-id="9e017-152">**Назначение**</span><span class="sxs-lookup"><span data-stu-id="9e017-152">**Purpose**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="9e017-153">1.</span><span class="sxs-lookup"><span data-stu-id="9e017-153">1.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="9e017-154">Подсеть, используемая контроллером домена Active Directory (AD) Windows Server и виртуальными машинами сервера DirSync.</span><span class="sxs-lookup"><span data-stu-id="9e017-154">The subnet used by the Windows Server Active Directory (AD) domain controller and DirSync server virtual machines (VMs).</span></span>  <br/> |
|<span data-ttu-id="9e017-155">2.</span><span class="sxs-lookup"><span data-stu-id="9e017-155">2.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="9e017-156">Подсеть, используемая виртуальными машинами AD FS.</span><span class="sxs-lookup"><span data-stu-id="9e017-156">The subnet used by the AD FS VMs.</span></span>  <br/> |
|<span data-ttu-id="9e017-157">3.</span><span class="sxs-lookup"><span data-stu-id="9e017-157">3.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="9e017-158">Подсеть, используемая виртуальными машинами прокси-серверов веб-приложений.</span><span class="sxs-lookup"><span data-stu-id="9e017-158">The subnet used by the web application proxy VMs.</span></span>  <br/> |
|<span data-ttu-id="9e017-159">4.</span><span class="sxs-lookup"><span data-stu-id="9e017-159">4.</span></span>  <br/> |<span data-ttu-id="9e017-160">GatewaySubnet</span><span class="sxs-lookup"><span data-stu-id="9e017-160">GatewaySubnet</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="9e017-161">Подсеть, используемая виртуальными машинами шлюза Azure.</span><span class="sxs-lookup"><span data-stu-id="9e017-161">The subnet used by the Azure gateway VMs.</span></span>  <br/> |
   
 <span data-ttu-id="9e017-162">**Таблица S. Подсети виртуальной сети**</span><span class="sxs-lookup"><span data-stu-id="9e017-162">**Table S: Subnets in the virtual network**</span></span>
  
<span data-ttu-id="9e017-163">После этого укажите статические IP-адреса, назначенные виртуальным машинам и экземплярам балансировщика нагрузки, в таблице I.</span><span class="sxs-lookup"><span data-stu-id="9e017-163">Next, fill in Table I for the static IP addresses assigned to virtual machines and load balancer instances.</span></span>
  
|<span data-ttu-id="9e017-164">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="9e017-164">**Item**</span></span>|<span data-ttu-id="9e017-165">**Назначение**</span><span class="sxs-lookup"><span data-stu-id="9e017-165">**Purpose**</span></span>|<span data-ttu-id="9e017-166">**IP-адрес в подсети**</span><span class="sxs-lookup"><span data-stu-id="9e017-166">**IP address on the subnet**</span></span>|<span data-ttu-id="9e017-167">**Значение**</span><span class="sxs-lookup"><span data-stu-id="9e017-167">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="9e017-168">1.</span><span class="sxs-lookup"><span data-stu-id="9e017-168">1.</span></span>  <br/> |<span data-ttu-id="9e017-169">Статический IP-адрес первого контроллера домена</span><span class="sxs-lookup"><span data-stu-id="9e017-169">Static IP address of the first domain controller</span></span>  <br/> |<span data-ttu-id="9e017-170">Четвертый возможный IP-адрес для адресного пространства подсети, определенной в элементе 1 таблицы S.</span><span class="sxs-lookup"><span data-stu-id="9e017-170">The fourth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="9e017-171">2.</span><span class="sxs-lookup"><span data-stu-id="9e017-171">2.</span></span>  <br/> |<span data-ttu-id="9e017-172">Статический IP-адрес второго контроллера домена</span><span class="sxs-lookup"><span data-stu-id="9e017-172">Static IP address of the second domain controller</span></span>  <br/> |<span data-ttu-id="9e017-173">Пятый возможный IP-адрес адресного пространства подсети, определенной в элементе 1 таблицы S.</span><span class="sxs-lookup"><span data-stu-id="9e017-173">The fifth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="9e017-174">3.</span><span class="sxs-lookup"><span data-stu-id="9e017-174">3.</span></span>  <br/> |<span data-ttu-id="9e017-175">Статический IP-адрес сервера DirSync</span><span class="sxs-lookup"><span data-stu-id="9e017-175">Static IP address of the DirSync server</span></span>  <br/> |<span data-ttu-id="9e017-176">Шестой возможный IP-адрес адресного пространства подсети, определенной в элементе 1 таблицы S.</span><span class="sxs-lookup"><span data-stu-id="9e017-176">The sixth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="9e017-177">4.</span><span class="sxs-lookup"><span data-stu-id="9e017-177">4.</span></span>  <br/> |<span data-ttu-id="9e017-178">Статический IP-адрес внутреннего балансировщика нагрузки для серверов AD FS</span><span class="sxs-lookup"><span data-stu-id="9e017-178">Static IP address of the internal load balancer for the AD FS servers</span></span>  <br/> |<span data-ttu-id="9e017-179">Четвертый возможный IP-адрес для адресного пространства подсети, определенный в элементе 2 таблицы S.</span><span class="sxs-lookup"><span data-stu-id="9e017-179">The fourth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="9e017-180">5.</span><span class="sxs-lookup"><span data-stu-id="9e017-180">5.</span></span>  <br/> |<span data-ttu-id="9e017-181">Статический IP-адрес первого сервера AD FS</span><span class="sxs-lookup"><span data-stu-id="9e017-181">Static IP address of the first AD FS server</span></span>  <br/> |<span data-ttu-id="9e017-182">Пятый возможный IP-адрес адресного пространства подсети, определенной в элементе 2 таблицы S.</span><span class="sxs-lookup"><span data-stu-id="9e017-182">The fifth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="9e017-183">6.</span><span class="sxs-lookup"><span data-stu-id="9e017-183">6.</span></span>  <br/> |<span data-ttu-id="9e017-184">Статический IP-адрес второго сервера AD FS</span><span class="sxs-lookup"><span data-stu-id="9e017-184">Static IP address of the second AD FS server</span></span>  <br/> |<span data-ttu-id="9e017-185">Шестой возможный IP-адрес адресного пространства подсети, определенной в элементе 2 таблицы S.</span><span class="sxs-lookup"><span data-stu-id="9e017-185">The sixth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="9e017-186">7.</span><span class="sxs-lookup"><span data-stu-id="9e017-186">7.</span></span>  <br/> |<span data-ttu-id="9e017-187">Статический IP-адрес первого прокси-сервера веб-приложений</span><span class="sxs-lookup"><span data-stu-id="9e017-187">Static IP address of the first web application proxy server</span></span>  <br/> |<span data-ttu-id="9e017-188">Четвертый возможный IP-адрес для адресного пространства подсети, определенный в элементе 3 таблицы S.</span><span class="sxs-lookup"><span data-stu-id="9e017-188">The fourth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="9e017-189">8.</span><span class="sxs-lookup"><span data-stu-id="9e017-189">8.</span></span>  <br/> |<span data-ttu-id="9e017-190">Статический IP-адрес второго прокси-сервера веб-приложений</span><span class="sxs-lookup"><span data-stu-id="9e017-190">Static IP address of the second web application proxy server</span></span>  <br/> |<span data-ttu-id="9e017-191">Пятый возможный IP-адрес адресного пространства подсети, определенной в элементе 3 таблицы S.</span><span class="sxs-lookup"><span data-stu-id="9e017-191">The fifth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="9e017-192">**Таблица I. Статические IP-адреса в виртуальной сети**</span><span class="sxs-lookup"><span data-stu-id="9e017-192">**Table I: Static IP addresses in the virtual network**</span></span>
  
<span data-ttu-id="9e017-193">В таблице D укажите два DNS-сервера в локальной сети, которые необходимо использовать при начальной настройке контроллеров домена в виртуальной сети. Чтобы определить этот список, обратитесь в ИТ-отдел.</span><span class="sxs-lookup"><span data-stu-id="9e017-193">For two Domain Name System (DNS) servers in your on-premises network that you want to use when initially setting up the domain controllers in your virtual network, fill in Table D. Work with your IT department to determine this list.</span></span>
  
|<span data-ttu-id="9e017-194">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="9e017-194">**Item**</span></span>|<span data-ttu-id="9e017-195">**Понятное имя DNS-сервера**</span><span class="sxs-lookup"><span data-stu-id="9e017-195">**DNS server friendly name**</span></span>|<span data-ttu-id="9e017-196">**IP-адрес DNS-сервера**</span><span class="sxs-lookup"><span data-stu-id="9e017-196">**DNS server IP address**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="9e017-197">1.</span><span class="sxs-lookup"><span data-stu-id="9e017-197">1.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="9e017-198">2.</span><span class="sxs-lookup"><span data-stu-id="9e017-198">2.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="9e017-199">**Таблица D. Локальные DNS-сервера**</span><span class="sxs-lookup"><span data-stu-id="9e017-199">**Table D: On-premises DNS servers**</span></span>
  
<span data-ttu-id="9e017-p107">Чтобы отправлять пакеты из нелокальной сети в сеть организации с помощью VPN-подключения типа "сеть-сеть", необходимо настроить виртуальную сеть с локальной сетью, которая содержит список адресных пространств (в формате CIDR) для всех доступных расположений в локальной сети организации. Список адресных пространств, которые определяют локальную сеть, должен быть уникален и не должен пересекаться с адресным пространством, используемым для других виртуальных или локальных сетей.</span><span class="sxs-lookup"><span data-stu-id="9e017-p107">To route packets from the cross-premises network to your organization network across the site-to-site VPN connection, you must configure the virtual network with a local network that contains a list of the address spaces (in CIDR notation) for all of the reachable locations on your organization's on-premises network. The list of address spaces that define your local network must be unique and must not overlap with the address space used for other virtual networks or other local networks.</span></span>
  
<span data-ttu-id="9e017-p108">Укажите список адресных пространств локальной сети в таблице L. Обратите внимание, что представлено три пустых поля, но обычно требуется больше. Определите этот список адресных пространств при поддержке ИТ-отдела.</span><span class="sxs-lookup"><span data-stu-id="9e017-p108">For the set of local network address spaces, fill in Table L. Note that three blank entries are listed but you will typically need more. Work with your IT department to determine this list of address spaces.</span></span>
  
|<span data-ttu-id="9e017-204">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="9e017-204">**Item**</span></span>|<span data-ttu-id="9e017-205">**Адресное пространство локальной сети**</span><span class="sxs-lookup"><span data-stu-id="9e017-205">**Local network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="9e017-206">1.</span><span class="sxs-lookup"><span data-stu-id="9e017-206">1.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="9e017-207">2.</span><span class="sxs-lookup"><span data-stu-id="9e017-207">2.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="9e017-208">3.</span><span class="sxs-lookup"><span data-stu-id="9e017-208">3.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="9e017-209">**Таблица L. Префиксы адресов для локальной сети**</span><span class="sxs-lookup"><span data-stu-id="9e017-209">**Table L: Address prefixes for the local network**</span></span>
  
<span data-ttu-id="9e017-210">Теперь приступим к созданию инфраструктуры Azure для размещения федеративной проверки подлинности для Office 365.</span><span class="sxs-lookup"><span data-stu-id="9e017-210">Now let's begin building the Azure infrastructure to host your federated authentication for Office 365.</span></span>
  
> [!NOTE]
> <span data-ttu-id="9e017-p109">Приведенные ниже наборы команд основаны на последней версии Azure PowerShell. См. статью [Начало работы с командлетами Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="9e017-p109">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="9e017-213">Запустите командную строку Azure PowerShell и войдите в свою учетную запись.</span><span class="sxs-lookup"><span data-stu-id="9e017-213">First, start an Azure PowerShell prompt and login to your account.</span></span>
  
```
Login-AzureRMAccount
```

> [!TIP]
> <span data-ttu-id="9e017-214">Текстовый файл, содержащий все команды PowerShell в данной статье и конфигурации книги Microsoft Excel, которое создает все готово к запуску PowerShell команду блоки на основе настраиваемых параметров содержатся в [федеративном проверки подлинности для Office 365 Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span><span class="sxs-lookup"><span data-stu-id="9e017-214">For a text file that contains all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
  
<span data-ttu-id="9e017-215">Получите имя подписки с помощью следующей команды.</span><span class="sxs-lookup"><span data-stu-id="9e017-215">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="9e017-216">Для предыдущих версий Windows Azure PowerShell используйте следующую команду.</span><span class="sxs-lookup"><span data-stu-id="9e017-216">For older versions of Azure PowerShell, use this command instead.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select SubscriptionName
```

<span data-ttu-id="9e017-p110">Укажите свою подписку Azure. Замените текст в кавычках, в том числе символы "\<" и ">", на правильное имя.</span><span class="sxs-lookup"><span data-stu-id="9e017-p110">Set your Azure subscription. Replace everything within the quotes, including the \< and > characters, with the correct name.</span></span>
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

<span data-ttu-id="9e017-p111">После этого создайте новые группы ресурсов. Чтобы задать уникальные имена, отобразите уже существующие группы ресурсов с помощью указанной команды.</span><span class="sxs-lookup"><span data-stu-id="9e017-p111">Next, create the new resource groups. To determine a unique set of resource group names, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="9e017-221">Укажите уникальные имена групп ресурсов в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="9e017-221">Fill in the following table for the set of unique resource group names.</span></span>
  
|<span data-ttu-id="9e017-222">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="9e017-222">**Item**</span></span>|<span data-ttu-id="9e017-223">**Имя группы ресурсов**</span><span class="sxs-lookup"><span data-stu-id="9e017-223">**Resource group name**</span></span>|<span data-ttu-id="9e017-224">**Назначение**</span><span class="sxs-lookup"><span data-stu-id="9e017-224">**Purpose**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="9e017-225">1.</span><span class="sxs-lookup"><span data-stu-id="9e017-225">1.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="9e017-226">Контроллеры доменов</span><span class="sxs-lookup"><span data-stu-id="9e017-226">Domain controllers</span></span>  <br/> |
|<span data-ttu-id="9e017-227">2.</span><span class="sxs-lookup"><span data-stu-id="9e017-227">2.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="9e017-228">Серверы AD FS</span><span class="sxs-lookup"><span data-stu-id="9e017-228">AD FS servers</span></span>  <br/> |
|<span data-ttu-id="9e017-229">3.</span><span class="sxs-lookup"><span data-stu-id="9e017-229">3.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="9e017-230">Прокси-серверы веб-приложений</span><span class="sxs-lookup"><span data-stu-id="9e017-230">Web application proxy servers</span></span>  <br/> |
|<span data-ttu-id="9e017-231">4.</span><span class="sxs-lookup"><span data-stu-id="9e017-231">4.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="9e017-232">Элементы инфраструктуры</span><span class="sxs-lookup"><span data-stu-id="9e017-232">Infrastructure elements</span></span>  <br/> |
   
 <span data-ttu-id="9e017-233">**Таблица R. Группы ресурсов**</span><span class="sxs-lookup"><span data-stu-id="9e017-233">**Table R: Resource groups**</span></span>
  
<span data-ttu-id="9e017-234">Создайте новые группы ресурсов с помощью этих команд.</span><span class="sxs-lookup"><span data-stu-id="9e017-234">Create your new resource groups with these commands.</span></span>
  
```
$locName="<an Azure location, such as West US>"
$rgName="<Table R - Item 1 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 2 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 3 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 4 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="9e017-235">Затем создайте виртуальную сеть Azure и подсети.</span><span class="sxs-lookup"><span data-stu-id="9e017-235">Next, you create the Azure virtual network and its subnets.</span></span>
  
```
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )
# Get the shortened version of the location
$locShortName=(Get-AzureRmResourceGroup -Name $rgName).Location

# Create the subnets
$subnet1Name="<Table S - Item 1 - Subnet name column>"
$subnet1Prefix="<Table S - Item 1 - Subnet address space column>"
$subnet1=New-AzureRMVirtualNetworkSubnetConfig -Name $subnet1Name -AddressPrefix $subnet1Prefix
$subnet2Name="<Table S - Item 2 - Subnet name column>"
$subnet2Prefix="<Table S - Item 2 - Subnet address space column>"
$subnet2=New-AzureRMVirtualNetworkSubnetConfig -Name $subnet2Name -AddressPrefix $subnet2Prefix
$subnet3Name="<Table S - Item 3 - Subnet name column>"
$subnet3Prefix="<Table S - Item 3 - Subnet address space column>"
$subnet3=New-AzureRMVirtualNetworkSubnetConfig -Name $subnet3Name -AddressPrefix $subnet3Prefix
$gwSubnet4Prefix="<Table S - Item 4 - Subnet address space column>"
$gwSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnet4Prefix

# Create the virtual network
New-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gwSubnet,$subnet1,$subnet2,$subnet3 -DNSServer $dnsServers

```

<span data-ttu-id="9e017-p112">Создайте сеть группы безопасности для каждой подсети, которая содержит виртуальных машин. Для выполнения изоляции подсети, можно добавить правила для определенных типов трафика запрещен в группу безопасности сети подсети, или.</span><span class="sxs-lookup"><span data-stu-id="9e017-p112">Next, you create network security groups for each subnet that contains virtual machines. To perform subnet isolation, you can add rules for the specific types of traffic allowed or denied to the network security group of a subnet.</span></span>
  
```
# Create network security groups
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name $vnetName

New-AzureRMNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet1Name -AddressPrefix $subnet1Prefix -NetworkSecurityGroup $nsg

New-AzureRMNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet2Name -AddressPrefix $subnet2Prefix -NetworkSecurityGroup $nsg

New-AzureRMNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet3Name -AddressPrefix $subnet3Prefix -NetworkSecurityGroup $nsg
```

<span data-ttu-id="9e017-238">Затем используйте следующие команды, чтобы создать шлюзы для VPN-подключения типа "сеть-сеть".</span><span class="sxs-lookup"><span data-stu-id="9e017-238">Next, use these commands to create the gateways for the site-to-site VPN connection.</span></span>
  
```
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "GatewaySubnet"

# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzureRMVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -Subnet $subnet

# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzureRMVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig

# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$localGateway=New-AzureRMLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix

# Define the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnetConnection=New-AzureRMVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway

```

> [!NOTE]
> <span data-ttu-id="9e017-p113">Федеративная проверка подлинности пользователей, не зависит от любого локальным ресурсам. Тем не менее недоступность VPN-подключения веб сайта контроллеры доменов в VNet не будут получать обновления для учетных записей пользователей и групп, выполненных в Windows на локальный сервер AD. Чтобы убедиться, что это не происходит, можно настроить высокой доступности для VPN-подключение к веб сайта. Для получения дополнительных сведений см [сильно доступные между организациями и связи с VNet-VNet](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span><span class="sxs-lookup"><span data-stu-id="9e017-p113">Federated authentication of individual users does not rely on any on-premises resources. However, if this site-to-site VPN connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Windows Server AD. To ensure this does not happen, you can configure high availability for your site-to-site VPN connection. For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="9e017-243">После этого запишите общедоступный IPv4-адрес VPN-шлюза Azure для виртуальной сети из результата этой команды:</span><span class="sxs-lookup"><span data-stu-id="9e017-243">Next, record the public IPv4 address of the Azure VPN gateway for your virtual network from the display of this command:</span></span>
  
```
Get-AzureRMPublicIpAddress -Name $publicGatewayVipName -ResourceGroupName $rgName
```

<span data-ttu-id="9e017-p114">Настройте устройство VPN локальной для подключения к виртуальной частной сети Azure шлюза. Дополнительные сведения в статье [Configure VPN-устройства](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span><span class="sxs-lookup"><span data-stu-id="9e017-p114">Next, configure your on-premises VPN device to connect to the Azure VPN gateway. For more information, see [Configure your VPN device](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="9e017-246">Чтобы настроить локальное VPN-устройство, вам потребуется следующее:</span><span class="sxs-lookup"><span data-stu-id="9e017-246">To configure your on-premises VPN device, you will need the following:</span></span>
  
- <span data-ttu-id="9e017-247">Общедоступный IPv4-адрес VPN-шлюза Azure.</span><span class="sxs-lookup"><span data-stu-id="9e017-247">The public IPv4 address of the Azure VPN gateway.</span></span>
    
- <span data-ttu-id="9e017-248">Предварительный ключ IPsec для VPN-подключения веб сайта (столбец таблицы V - элемента 5 - значение).</span><span class="sxs-lookup"><span data-stu-id="9e017-248">The IPsec pre-shared key for the site-to-site VPN connection (Table V - Item 5 - Value column).</span></span>
    
<span data-ttu-id="9e017-p115">Убедитесь, что адресное пространство виртуальной сети доступно из локальной сети. Для этого добавьте маршрут, соответствующий адресному пространству виртуальной сети на вашем VPN-устройстве и сообщите этот маршрут остальной инфраструктуре маршрутизации в сети организации. Чтобы определить, как это сделать, обратитесь в ИТ-отдел.</span><span class="sxs-lookup"><span data-stu-id="9e017-p115">Next, ensure that the address space of the virtual network is reachable from your on-premises network. This is usually done by adding a route corresponding to the virtual network address space to your VPN device and then advertising that route to the rest of the routing infrastructure of your organization network. Work with your IT department to determine how to do this.</span></span>
  
<span data-ttu-id="9e017-p116">После этого определите имена четырех групп доступности. Заполните таблицу A.</span><span class="sxs-lookup"><span data-stu-id="9e017-p116">Next, define the names of three availability sets. Fill out Table A.</span></span> 
  
|<span data-ttu-id="9e017-254">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="9e017-254">**Item**</span></span>|<span data-ttu-id="9e017-255">**Назначение**</span><span class="sxs-lookup"><span data-stu-id="9e017-255">**Purpose**</span></span>|<span data-ttu-id="9e017-256">**Имя группы доступности**</span><span class="sxs-lookup"><span data-stu-id="9e017-256">**Availability set name**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="9e017-257">1.</span><span class="sxs-lookup"><span data-stu-id="9e017-257">1.</span></span>  <br/> |<span data-ttu-id="9e017-258">Контроллеры доменов</span><span class="sxs-lookup"><span data-stu-id="9e017-258">Domain controllers</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="9e017-259">2.</span><span class="sxs-lookup"><span data-stu-id="9e017-259">2.</span></span>  <br/> |<span data-ttu-id="9e017-260">Серверы AD FS</span><span class="sxs-lookup"><span data-stu-id="9e017-260">AD FS servers</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="9e017-261">3.</span><span class="sxs-lookup"><span data-stu-id="9e017-261">3.</span></span>  <br/> |<span data-ttu-id="9e017-262">Прокси-серверы веб-приложений</span><span class="sxs-lookup"><span data-stu-id="9e017-262">Web application proxy servers</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="9e017-263">**Таблица A. Группы доступности**</span><span class="sxs-lookup"><span data-stu-id="9e017-263">**Table A: Availability sets**</span></span>
  
<span data-ttu-id="9e017-264">Вам потребуются эти имена при создании виртуальных машин на этапах 2, 3 и 4.</span><span class="sxs-lookup"><span data-stu-id="9e017-264">You will need these names when you create the virtual machines in phases 2, 3, and 4.</span></span>
  
<span data-ttu-id="9e017-265">Создайте новые группы доступности с помощью этих команд Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9e017-265">Create the new availability sets with these Azure PowerShell commands.</span></span>
  
```
$locName="<the Azure location for your new resource group>"
$rgName="<Table R - Item 1 - Resource group name column>"
$avName="<Table A - Item 1 - Availability set name column>"
New-AzureRMAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
$rgName="<Table R - Item 2 - Resource group name column>"
$avName="<Table A - Item 2 - Availability set name column>"
New-AzureRMAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
$rgName="<Table R - Item 3 - Resource group name column>"
$avName="<Table A - Item 3 - Availability set name column>"
New-AzureRMAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
```

<span data-ttu-id="9e017-266">Ниже показана конфигурация, полученная в результате успешного выполнения этого этапа.</span><span class="sxs-lookup"><span data-stu-id="9e017-266">This is the configuration resulting from the successful completion of this phase.</span></span>
  
<span data-ttu-id="9e017-267">**Этап 1. Инфраструктура Azure для федеративной проверки подлинности с высоким уровнем доступности для Office 365**</span><span class="sxs-lookup"><span data-stu-id="9e017-267">**Phase 1: The Azure infrastructure for high availability federated authentication for Office 365**</span></span>

![Этап 1. Федеративная проверка подлинности для Office 365 с высокой доступностью, развертывание которой выполняется в Azure с использованием инфраструктуры Azure](media/4e7ba678-07df-40ce-b372-021bf7fc91fa.png)
  
## <a name="next-step"></a><span data-ttu-id="9e017-269">Следующий шаг</span><span class="sxs-lookup"><span data-stu-id="9e017-269">Next step</span></span>

<span data-ttu-id="9e017-270">Используйте [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md), чтобы продолжить настройку этой нагрузки.</span><span class="sxs-lookup"><span data-stu-id="9e017-270">Use [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) to continue with the configuration of this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9e017-271">См. также</span><span class="sxs-lookup"><span data-stu-id="9e017-271">See Also</span></span>

[<span data-ttu-id="9e017-272">Развертывание в Azure федеративной проверки подлинности для обеспечения высокой доступности в случае использования Office 365</span><span class="sxs-lookup"><span data-stu-id="9e017-272">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="9e017-273">Федеративное удостоверение для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="9e017-273">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="9e017-274">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="9e017-274">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="9e017-275">Идентификация в Office 365 и Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="9e017-275">Understanding Office 365 identity and Azure Active Directory</span></span>](about-office-365-identity.md)


