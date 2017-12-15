---
title: "Федеративная проверка подлинности высокой доступности Azure настроить этап 1"
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
ms.custom:
- DecEntMigration
- Ent_Solutions
ms.assetid: 91266aac-4d00-4b5f-b424-86a1a837792c
description: "Сводка: Настройка инфраструктуры Microsoft Azure для высокой доступности узла федеративной проверки подлинности для Office 365."
ms.openlocfilehash: fed6b24af2ba54bef95be22641fd140f7c1be717
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="high-availability-federated-authentication-phase-1-configure-azure"></a><span data-ttu-id="bb1ba-103">Этап 1. Федеративная проверка подлинности для обеспечения высокой доступности: настройка Azure</span><span class="sxs-lookup"><span data-stu-id="bb1ba-103">High availability federated authentication Phase 1: Configure Azure</span></span>

 <span data-ttu-id="bb1ba-104">**Сводка:** Настройка инфраструктуры Microsoft Azure для использования проверки подлинности федеративные высокой доступности узла для Office 365.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-104">**Summary:** Configure the Microsoft Azure infrastructure to host high availability federated authentication for Office 365.</span></span>
  
<span data-ttu-id="bb1ba-p101">На этом этапе создается группы ресурсов, хранилище учетных записей, виртуальные сети (VNet) и доступность наборы в Azure, в котором будет размещаться виртуальных машин в этапы 2, 3 и 4. Необходимо выполнить данный этап перед перемещением на [высокой доступности федеративных проверки подлинности этап 2: Настройка контроллеров домена](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). В разделе [Развертывание высокой доступности федеративной проверки подлинности для Office 365 в Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) все этапы.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-p101">In this phase, you create the resource groups, storage accounts, virtual network (VNet), and availability sets in Azure that will host the virtual machines in phases 2, 3, and 4. You must complete this phase before moving on to [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
<span data-ttu-id="bb1ba-108">Необходимо быть, подготовленные в Azure с помощью следующих основных компонентов:</span><span class="sxs-lookup"><span data-stu-id="bb1ba-108">Azure must be provisioned with these basic components:</span></span>
  
- <span data-ttu-id="bb1ba-109">Группы ресурсов</span><span class="sxs-lookup"><span data-stu-id="bb1ba-109">Resource groups</span></span>
    
- <span data-ttu-id="bb1ba-110">Нелокальная виртуальная сеть Azure с подсетями для размещения виртуальных машин Azure</span><span class="sxs-lookup"><span data-stu-id="bb1ba-110">A cross-premises Azure virtual network (VNet) with subnets for hosting the Azure virtual machines</span></span>
    
- <span data-ttu-id="bb1ba-111">Группы безопасности сети для изоляции подсети</span><span class="sxs-lookup"><span data-stu-id="bb1ba-111">Network security groups for performing subnet isolation</span></span>
    
- <span data-ttu-id="bb1ba-112">Группы доступности</span><span class="sxs-lookup"><span data-stu-id="bb1ba-112">Availability sets</span></span>
    
## <a name="configure-azure-components"></a><span data-ttu-id="bb1ba-113">Настройка компонентов Azure</span><span class="sxs-lookup"><span data-stu-id="bb1ba-113">Configure Azure components</span></span>

<span data-ttu-id="bb1ba-p102">Перед началом настройки Azure компонентов, заполните поля в следующих таблицах. Для помощи в процедуры для настройки Azure, печать в этом разделе запишите требуемые данные или скопируйте в этом разделе документа и его можно заполнить. Для параметров VNet заполните поля в таблице V.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-p102">Before you begin configuring Azure components, fill in the following tables. To assist you in the procedures for configuring Azure, print this section and write down the needed information or copy this section to a document and fill it in. For the settings of the VNet, fill in Table V.</span></span>
  
|<span data-ttu-id="bb1ba-117">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="bb1ba-117">**Item**</span></span>|<span data-ttu-id="bb1ba-118">**Параметр конфигурации**</span><span class="sxs-lookup"><span data-stu-id="bb1ba-118">**Configuration setting**</span></span>|<span data-ttu-id="bb1ba-119">**Описание**</span><span class="sxs-lookup"><span data-stu-id="bb1ba-119">**Description**</span></span>|<span data-ttu-id="bb1ba-120">**Значение**</span><span class="sxs-lookup"><span data-stu-id="bb1ba-120">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="bb1ba-121">1.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-121">1.</span></span>  <br/> |<span data-ttu-id="bb1ba-122">Имя виртуальной сети</span><span class="sxs-lookup"><span data-stu-id="bb1ba-122">VNet name</span></span>  <br/> |<span data-ttu-id="bb1ba-123">Имя виртуальной сети (например, FedAuthNet).</span><span class="sxs-lookup"><span data-stu-id="bb1ba-123">A name to assign to the VNet (example FedAuthNet).</span></span>  <br/> |<span data-ttu-id="bb1ba-124">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-124"></span></span>  <br/> |
|<span data-ttu-id="bb1ba-125">2.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-125">2.</span></span>  <br/> |<span data-ttu-id="bb1ba-126">Расположение VNet</span><span class="sxs-lookup"><span data-stu-id="bb1ba-126">VNet location</span></span>  <br/> |<span data-ttu-id="bb1ba-127">Региональный центр обработки данных Azure, в котором будет расположена виртуальная сеть.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-127">The regional Azure datacenter that will contain the virtual network.</span></span>  <br/> |<span data-ttu-id="bb1ba-128">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-128"></span></span>  <br/> |
|<span data-ttu-id="bb1ba-129">3.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-129">3.</span></span>  <br/> |<span data-ttu-id="bb1ba-130">IP-адрес VPN-устройства</span><span class="sxs-lookup"><span data-stu-id="bb1ba-130">VPN device IP address</span></span>  <br/> |<span data-ttu-id="bb1ba-131">Общедоступный IPv4-адрес интерфейса VPN-устройства в Интернете.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-131">The public IPv4 address of your VPN device's interface on the Internet.</span></span>  <br/> |<span data-ttu-id="bb1ba-132">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-132"></span></span>  <br/> |
|<span data-ttu-id="bb1ba-133">4.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-133">4.</span></span>  <br/> |<span data-ttu-id="bb1ba-134">Адресное пространство виртуальной сети</span><span class="sxs-lookup"><span data-stu-id="bb1ba-134">VNet address space</span></span>  <br/> |<span data-ttu-id="bb1ba-p103">Адресное пространство виртуальной сети. Чтобы определить это адресное пространство, обратитесь в ИТ-отдел.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-p103">The address space for the virtual network. Work with your IT department to determine this address space.</span></span>  <br/> |<span data-ttu-id="bb1ba-137">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-137"></span></span>  <br/> |
|<span data-ttu-id="bb1ba-138">5.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-138">5.</span></span>  <br/> |<span data-ttu-id="bb1ba-139">Общий ключ IPsec</span><span class="sxs-lookup"><span data-stu-id="bb1ba-139">IPsec shared key</span></span>  <br/> |<span data-ttu-id="bb1ba-p104">32 символов в случайном порядке, буквенно-цифровой строка, которая будет использоваться для проверки подлинности обеих сторон VPN-подключения веб сайта. Работа с ИТ или отдела безопасности для определения это значение ключа. Кроме того в разделе [Создать строку в случайном порядке для предварительного ключа IPsec](http://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).</span><span class="sxs-lookup"><span data-stu-id="bb1ba-p104">A 32-character random, alphanumeric string that will be used to authenticate both sides of the site-to-site VPN connection. Work with your IT or security department to determine this key value. Alternately, see [Create a random string for an IPsec preshared key](http://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  </span></span><br/> |<span data-ttu-id="bb1ba-143">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-143"></span></span>  <br/> |
   
 <span data-ttu-id="bb1ba-144">**Таблица V. Настройка распределенной виртуальной сети**</span><span class="sxs-lookup"><span data-stu-id="bb1ba-144">**Table V: Cross-premises virtual network configuration**</span></span>
  
<span data-ttu-id="bb1ba-p105">После этого укажите подсети этого решения в таблице S. Все адресные пространства должны быть указаны в формате CIDR (формате префиксов сети). Пример: 10.24.64.0/20.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-p105">Next, fill in Table S for the subnets of this solution. All address spaces should be in Classless Interdomain Routing (CIDR) format, also known as network prefix format. An example is 10.24.64.0/20.</span></span>
  
<span data-ttu-id="bb1ba-p106">Для первых трех подсетей укажите имя и одно пространство IP-адресов на основе адресного пространства виртуальной сети. Для подсети шлюза определите 27-битовое адресное пространство (с длиной префикса /27) для подсети шлюза Azure шлюза. Для этого выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="bb1ba-p106">For the first three subnets, specify a name and a single IP address space based on the virtual network address space. For the gateway subnet, determine the 27-bit address space (with a /27 prefix length) for the Azure gateway subnet with the following:</span></span>
  
1. <span data-ttu-id="bb1ba-150">Для переменных битов в адресном пространстве виртуальной сети задайте значение 1 (не больше бит, используемых подсетью шлюза), а для остальных битов задайте значение 0.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-150">Set the variable bits in the address space of the VNet to 1, up to the bits being used by the gateway subnet, then set the remaining bits to 0.</span></span>
    
2. <span data-ttu-id="bb1ba-151">Преобразуйте результат в десятичное число и выразите его как адресное пространство, длина префикса которого соответствует размеру подсети шлюза.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-151">Convert the resulting bits to decimal and express it as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="bb1ba-152">В разделе [Калькулятор пространства адресов для подсетей Azure шлюза](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) блок команд PowerShell и C# или Python консольное приложение, используемая для выполнения этого вычисления для вас.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-152">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for a PowerShell command block and C# or Python console application that performs this calculation for you.</span></span>
  
<span data-ttu-id="bb1ba-153">Чтобы определить эти адресные пространства из адресного пространства виртуальной сети, обратитесь в ИТ-отдел.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-153">Work with your IT department to determine these address spaces from the virtual network address space.</span></span>
  
|<span data-ttu-id="bb1ba-154">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="bb1ba-154">**Item**</span></span>|<span data-ttu-id="bb1ba-155">**Имя подсети**</span><span class="sxs-lookup"><span data-stu-id="bb1ba-155">**Subnet name**</span></span>|<span data-ttu-id="bb1ba-156">**Адресное пространство подсети**</span><span class="sxs-lookup"><span data-stu-id="bb1ba-156">**Subnet address space**</span></span>|<span data-ttu-id="bb1ba-157">**Назначение**</span><span class="sxs-lookup"><span data-stu-id="bb1ba-157">**Purpose**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="bb1ba-158">1.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-158">1.</span></span>  <br/> |<span data-ttu-id="bb1ba-159">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-159"></span></span>  <br/> |<span data-ttu-id="bb1ba-160">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-160"></span></span>  <br/> |<span data-ttu-id="bb1ba-161">Подсеть, используемая контроллером домена Active Directory (AD) Windows Server и виртуальными машинами сервера DirSync.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-161">The subnet used by the Windows Server Active Directory (AD) domain controller and DirSync server virtual machines (VMs).</span></span>  <br/> |
|<span data-ttu-id="bb1ba-162">2.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-162">2.</span></span>  <br/> |<span data-ttu-id="bb1ba-163">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-163"></span></span>  <br/> |<span data-ttu-id="bb1ba-164">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-164"></span></span>  <br/> |<span data-ttu-id="bb1ba-165">Подсеть, используемая виртуальными машинами AD FS.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-165">The subnet used by the AD FS VMs.</span></span>  <br/> |
|<span data-ttu-id="bb1ba-166">3.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-166">3.</span></span>  <br/> |<span data-ttu-id="bb1ba-167">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-167"></span></span>  <br/> |<span data-ttu-id="bb1ba-168">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-168"></span></span>  <br/> |<span data-ttu-id="bb1ba-169">Подсеть, используемая виртуальными машинами прокси-серверов веб-приложений.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-169">The subnet used by the web application proxy VMs.</span></span>  <br/> |
|<span data-ttu-id="bb1ba-170">4.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-170">4.</span></span>  <br/> |<span data-ttu-id="bb1ba-171">GatewaySubnet</span><span class="sxs-lookup"><span data-stu-id="bb1ba-171">GatewaySubnet</span></span>  <br/> |<span data-ttu-id="bb1ba-172">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-172"></span></span>  <br/> |<span data-ttu-id="bb1ba-173">Подсеть, используемая виртуальными машинами шлюза Azure.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-173">The subnet used by the Azure gateway VMs.</span></span>  <br/> |
   
 <span data-ttu-id="bb1ba-174">**Таблица S. Подсети виртуальной сети**</span><span class="sxs-lookup"><span data-stu-id="bb1ba-174">**Table S: Subnets in the virtual network**</span></span>
  
<span data-ttu-id="bb1ba-175">После этого укажите статические IP-адреса, назначенные виртуальным машинам и экземплярам балансировщика нагрузки, в таблице I.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-175">Next, fill in Table I for the static IP addresses assigned to virtual machines and load balancer instances.</span></span>
  
|<span data-ttu-id="bb1ba-176">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="bb1ba-176">**Item**</span></span>|<span data-ttu-id="bb1ba-177">**Назначение**</span><span class="sxs-lookup"><span data-stu-id="bb1ba-177">**Purpose**</span></span>|<span data-ttu-id="bb1ba-178">**IP-адрес в подсети**</span><span class="sxs-lookup"><span data-stu-id="bb1ba-178">**IP address on the subnet**</span></span>|<span data-ttu-id="bb1ba-179">**Значение**</span><span class="sxs-lookup"><span data-stu-id="bb1ba-179">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="bb1ba-180">1.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-180">1.</span></span>  <br/> |<span data-ttu-id="bb1ba-181">Статический IP-адрес первого контроллера домена</span><span class="sxs-lookup"><span data-stu-id="bb1ba-181">Static IP address of the first domain controller</span></span>  <br/> |<span data-ttu-id="bb1ba-182">Четвертый возможный IP-адрес для адресного пространства подсети, определенной в элементе 1 таблицы S.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-182">The fourth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |<span data-ttu-id="bb1ba-183">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-183"></span></span>  <br/> |
|<span data-ttu-id="bb1ba-184">2.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-184">2.</span></span>  <br/> |<span data-ttu-id="bb1ba-185">Статический IP-адрес второго контроллера домена</span><span class="sxs-lookup"><span data-stu-id="bb1ba-185">Static IP address of the second domain controller</span></span>  <br/> |<span data-ttu-id="bb1ba-186">Пятый возможный IP-адрес адресного пространства подсети, определенной в элементе 1 таблицы S.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-186">The fifth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |<span data-ttu-id="bb1ba-187">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-187"></span></span>  <br/> |
|<span data-ttu-id="bb1ba-188">3.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-188">3.</span></span>  <br/> |<span data-ttu-id="bb1ba-189">Статический IP-адрес сервера DirSync</span><span class="sxs-lookup"><span data-stu-id="bb1ba-189">Static IP address of the DirSync server</span></span>  <br/> |<span data-ttu-id="bb1ba-190">Шестой возможный IP-адрес адресного пространства подсети, определенной в элементе 1 таблицы S.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-190">The sixth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |<span data-ttu-id="bb1ba-191">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-191"></span></span>  <br/> |
|<span data-ttu-id="bb1ba-192">4.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-192">4.</span></span>  <br/> |<span data-ttu-id="bb1ba-193">Статический IP-адрес внутреннего балансировщика нагрузки для серверов AD FS</span><span class="sxs-lookup"><span data-stu-id="bb1ba-193">Static IP address of the internal load balancer for the AD FS servers</span></span>  <br/> |<span data-ttu-id="bb1ba-194">Четвертый возможный IP-адрес для адресного пространства подсети, определенный в элементе 2 таблицы S.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-194">The fourth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |<span data-ttu-id="bb1ba-195">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-195"></span></span>  <br/> |
|<span data-ttu-id="bb1ba-196">5.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-196">5.</span></span>  <br/> |<span data-ttu-id="bb1ba-197">Статический IP-адрес первого сервера AD FS</span><span class="sxs-lookup"><span data-stu-id="bb1ba-197">Static IP address of the first AD FS server</span></span>  <br/> |<span data-ttu-id="bb1ba-198">Пятый возможный IP-адрес адресного пространства подсети, определенной в элементе 2 таблицы S.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-198">The fifth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |<span data-ttu-id="bb1ba-199">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-199"></span></span>  <br/> |
|<span data-ttu-id="bb1ba-200">6.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-200">6.</span></span>  <br/> |<span data-ttu-id="bb1ba-201">Статический IP-адрес второго сервера AD FS</span><span class="sxs-lookup"><span data-stu-id="bb1ba-201">Static IP address of the second AD FS server</span></span>  <br/> |<span data-ttu-id="bb1ba-202">Шестой возможный IP-адрес адресного пространства подсети, определенной в элементе 2 таблицы S.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-202">The sixth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |<span data-ttu-id="bb1ba-203">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-203"></span></span>  <br/> |
|<span data-ttu-id="bb1ba-204">7.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-204">7.</span></span>  <br/> |<span data-ttu-id="bb1ba-205">Статический IP-адрес первого прокси-сервера веб-приложений</span><span class="sxs-lookup"><span data-stu-id="bb1ba-205">Static IP address of the first web application proxy server</span></span>  <br/> |<span data-ttu-id="bb1ba-206">Четвертый возможный IP-адрес для адресного пространства подсети, определенный в элементе 3 таблицы S.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-206">The fourth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |<span data-ttu-id="bb1ba-207">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-207"></span></span>  <br/> |
|<span data-ttu-id="bb1ba-208">8.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-208">8.</span></span>  <br/> |<span data-ttu-id="bb1ba-209">Статический IP-адрес второго прокси-сервера веб-приложений</span><span class="sxs-lookup"><span data-stu-id="bb1ba-209">Static IP address of the second web application proxy server</span></span>  <br/> |<span data-ttu-id="bb1ba-210">Пятый возможный IP-адрес адресного пространства подсети, определенной в элементе 3 таблицы S.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-210">The fifth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |<span data-ttu-id="bb1ba-211">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-211"></span></span>  <br/> |
   
 <span data-ttu-id="bb1ba-212">**В таблице по созданию статических IP-адресов в виртуальной сети**</span><span class="sxs-lookup"><span data-stu-id="bb1ba-212">**Table I: Static IP addresses in the virtual network**</span></span>
  
<span data-ttu-id="bb1ba-213">В таблице D укажите два DNS-сервера в локальной сети, которые необходимо использовать при начальной настройке контроллеров домена в виртуальной сети. Чтобы определить этот список, обратитесь в ИТ-отдел.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-213">For two Domain Name System (DNS) servers in your on-premises network that you want to use when initially setting up the domain controllers in your virtual network, fill in Table D. Work with your IT department to determine this list.</span></span>
  
|<span data-ttu-id="bb1ba-214">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="bb1ba-214">**Item**</span></span>|<span data-ttu-id="bb1ba-215">**Понятное имя DNS-сервера**</span><span class="sxs-lookup"><span data-stu-id="bb1ba-215">**DNS server friendly name**</span></span>|<span data-ttu-id="bb1ba-216">**IP-адрес DNS-сервера**</span><span class="sxs-lookup"><span data-stu-id="bb1ba-216">**DNS server IP address**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="bb1ba-217">1.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-217">1.</span></span>  <br/> |<span data-ttu-id="bb1ba-218">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-218"></span></span>  <br/> |<span data-ttu-id="bb1ba-219">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-219"></span></span>  <br/> |
|<span data-ttu-id="bb1ba-220">2.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-220">2.</span></span>  <br/> |<span data-ttu-id="bb1ba-221">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-221"></span></span>  <br/> |<span data-ttu-id="bb1ba-222">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-222"></span></span>  <br/> |
   
 <span data-ttu-id="bb1ba-223">**Таблица D. Локальные DNS-сервера**</span><span class="sxs-lookup"><span data-stu-id="bb1ba-223">**Table D: On-premises DNS servers**</span></span>
  
<span data-ttu-id="bb1ba-p107">Чтобы отправлять пакеты из нелокальной сети в сеть организации с помощью VPN-подключения типа "сеть-сеть", необходимо настроить виртуальную сеть с локальной сетью, которая содержит список адресных пространств (в формате CIDR) для всех доступных расположений в локальной сети организации. Список адресных пространств, которые определяют локальную сеть, должен быть уникален и не должен пересекаться с адресным пространством, используемым для других виртуальных или локальных сетей.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-p107">To route packets from the cross-premises network to your organization network across the site-to-site VPN connection, you must configure the virtual network with a local network that contains a list of the address spaces (in CIDR notation) for all of the reachable locations on your organization's on-premises network. The list of address spaces that define your local network must be unique and must not overlap with the address space used for other virtual networks or other local networks.</span></span>
  
<span data-ttu-id="bb1ba-p108">Укажите список адресных пространств локальной сети в таблице L. Обратите внимание, что представлено три пустых поля, но обычно требуется больше. Определите этот список адресных пространств при поддержке ИТ-отдела.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-p108">For the set of local network address spaces, fill in Table L. Note that three blank entries are listed but you will typically need more. Work with your IT department to determine this list of address spaces.</span></span>
  
|<span data-ttu-id="bb1ba-228">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="bb1ba-228">**Item**</span></span>|<span data-ttu-id="bb1ba-229">**Адресное пространство локальной сети**</span><span class="sxs-lookup"><span data-stu-id="bb1ba-229">**Local network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="bb1ba-230">1.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-230">1.</span></span>  <br/> |<span data-ttu-id="bb1ba-231">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-231"></span></span>  <br/> |
|<span data-ttu-id="bb1ba-232">2.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-232">2.</span></span>  <br/> |<span data-ttu-id="bb1ba-233">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-233"></span></span>  <br/> |
|<span data-ttu-id="bb1ba-234">3.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-234">3.</span></span>  <br/> |<span data-ttu-id="bb1ba-235">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-235"></span></span>  <br/> |
   
 <span data-ttu-id="bb1ba-236">**Таблица L. Префиксы адресов для локальной сети**</span><span class="sxs-lookup"><span data-stu-id="bb1ba-236">**Table L: Address prefixes for the local network**</span></span>
  
<span data-ttu-id="bb1ba-237">Теперь приступим к созданию инфраструктуры Azure для размещения федеративной проверки подлинности для Office 365.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-237">Now let's begin building the Azure infrastructure to host your federated authentication for Office 365.</span></span>
  
> [!NOTE]
> <span data-ttu-id="bb1ba-p109">Следующие наборы команд использовать последнюю версию Windows Azure PowerShell. В разделе [Начало работы с Windows Azure PowerShell командлетов](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="bb1ba-p109">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="bb1ba-240">Запустите командную строку Azure PowerShell и войдите в свою учетную запись.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-240">First, start an Azure PowerShell prompt and login to your account.</span></span>
  
```
Login-AzureRMAccount
```

> [!TIP]
> <span data-ttu-id="bb1ba-241">Текстовый файл, содержащий все команды PowerShell в данной статье и конфигурации книги Microsoft Excel, которое создает все готово к запуску PowerShell команду блоки на основе настраиваемых параметров содержатся в [федеративном проверки подлинности для Office 365 Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span><span class="sxs-lookup"><span data-stu-id="bb1ba-241">For a text file that contains all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
  
<span data-ttu-id="bb1ba-242">Получите имя подписки с помощью следующей команды.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-242">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="bb1ba-243">Для предыдущих версий Windows Azure PowerShell используйте следующую команду.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-243">For older versions of Azure PowerShell, use this command instead.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select SubscriptionName
```

<span data-ttu-id="bb1ba-p110">Задайте подпиской Azure. Замените все содержимое в кавычки, включая \< и > символов с правильным именем.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-p110">Set your Azure subscription. Replace everything within the quotes, including the \< and > characters, with the correct name.</span></span>
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

<span data-ttu-id="bb1ba-p111">После этого создайте новые группы ресурсов. Чтобы задать уникальные имена, отобразите уже существующие группы ресурсов с помощью указанной команды.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-p111">Next, create the new resource groups. To determine a unique set of resource group names, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="bb1ba-248">Укажите уникальные имена групп ресурсов в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-248">Fill in the following table for the set of unique resource group names.</span></span>
  
|<span data-ttu-id="bb1ba-249">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="bb1ba-249">**Item**</span></span>|<span data-ttu-id="bb1ba-250">**Имя группы ресурсов**</span><span class="sxs-lookup"><span data-stu-id="bb1ba-250">**Resource group name**</span></span>|<span data-ttu-id="bb1ba-251">**Назначение**</span><span class="sxs-lookup"><span data-stu-id="bb1ba-251">**Purpose**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="bb1ba-252">1.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-252">1.</span></span>  <br/> |<span data-ttu-id="bb1ba-253">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-253"></span></span>  <br/> |<span data-ttu-id="bb1ba-254">Контроллеры доменов</span><span class="sxs-lookup"><span data-stu-id="bb1ba-254">Domain controllers</span></span>  <br/> |
|<span data-ttu-id="bb1ba-255">2.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-255">2.</span></span>  <br/> |<span data-ttu-id="bb1ba-256">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-256"></span></span>  <br/> |<span data-ttu-id="bb1ba-257">Серверы AD FS</span><span class="sxs-lookup"><span data-stu-id="bb1ba-257">AD FS servers</span></span>  <br/> |
|<span data-ttu-id="bb1ba-258">3.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-258">3.</span></span>  <br/> |<span data-ttu-id="bb1ba-259">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-259"></span></span>  <br/> |<span data-ttu-id="bb1ba-260">Прокси-серверы веб-приложений</span><span class="sxs-lookup"><span data-stu-id="bb1ba-260">Web application proxy servers</span></span>  <br/> |
|<span data-ttu-id="bb1ba-261">4.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-261">4.</span></span>  <br/> |<span data-ttu-id="bb1ba-262">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-262"></span></span>  <br/> |<span data-ttu-id="bb1ba-263">Элементы инфраструктуры</span><span class="sxs-lookup"><span data-stu-id="bb1ba-263">Infrastructure elements</span></span>  <br/> |
   
 <span data-ttu-id="bb1ba-264">**В таблице центральный группы ресурсов**</span><span class="sxs-lookup"><span data-stu-id="bb1ba-264">**Table R: Resource groups**</span></span>
  
<span data-ttu-id="bb1ba-265">Создайте новые группы ресурсов с помощью этих команд.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-265">Create your new resource groups with these commands.</span></span>
  
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

<span data-ttu-id="bb1ba-266">Затем создайте виртуальную сеть Azure и подсети.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-266">Next, you create the Azure virtual network and its subnets.</span></span>
  
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

<span data-ttu-id="bb1ba-p112">Создайте сеть группы безопасности для каждой подсети, которая содержит виртуальных машин. Для выполнения изоляции подсети, можно добавить правила для определенных типов трафика запрещен в группу безопасности сети подсети, или.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-p112">Next, you create network security groups for each subnet that contains virtual machines. To perform subnet isolation, you can add rules for the specific types of traffic allowed or denied to the network security group of a subnet.</span></span>
  
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

<span data-ttu-id="bb1ba-269">Затем используйте следующие команды, чтобы создать шлюзы для VPN-подключения типа "сеть-сеть".</span><span class="sxs-lookup"><span data-stu-id="bb1ba-269">Next, use these commands to create the gateways for the site-to-site VPN connection.</span></span>
  
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
> <span data-ttu-id="bb1ba-p113">Федеративная проверка подлинности пользователей, не зависит от любого локальным ресурсам. Тем не менее недоступность VPN-подключения веб сайта контроллеры доменов в VNet не будут получать обновления для учетных записей пользователей и групп, выполненных в Windows на локальный сервер AD. Чтобы убедиться, что это не происходит, можно настроить высокой доступности для VPN-подключение к веб сайта. Для получения дополнительных сведений см [сильно доступные между организациями и связи с VNet-VNet](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span><span class="sxs-lookup"><span data-stu-id="bb1ba-p113">Federated authentication of individual users does not rely on any on-premises resources. However, if this site-to-site VPN connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Windows Server AD. To ensure this does not happen, you can configure high availability for your site-to-site VPN connection. For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="bb1ba-274">После этого запишите общедоступный IPv4-адрес VPN-шлюза Azure для виртуальной сети из результата этой команды:</span><span class="sxs-lookup"><span data-stu-id="bb1ba-274">Next, record the public IPv4 address of the Azure VPN gateway for your virtual network from the display of this command:</span></span>
  
```
Get-AzureRMPublicIpAddress -Name $publicGatewayVipName -ResourceGroupName $rgName
```

<span data-ttu-id="bb1ba-p114">Настройте устройство VPN локальной для подключения к виртуальной частной сети Azure шлюза. Дополнительные сведения в статье [Configure VPN-устройства](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span><span class="sxs-lookup"><span data-stu-id="bb1ba-p114">Next, configure your on-premises VPN device to connect to the Azure VPN gateway. For more information, see [Configure your VPN device](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="bb1ba-277">Чтобы настроить локальное VPN-устройство, вам потребуется следующее:</span><span class="sxs-lookup"><span data-stu-id="bb1ba-277">To configure your on-premises VPN device, you will need the following:</span></span>
  
- <span data-ttu-id="bb1ba-278">Общедоступный IPv4-адрес VPN-шлюза Azure.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-278">The public IPv4 address of the Azure VPN gateway.</span></span>
    
- <span data-ttu-id="bb1ba-279">Предварительный ключ IPsec для VPN-подключения веб сайта (столбец таблицы V - элемента 5 - значение).</span><span class="sxs-lookup"><span data-stu-id="bb1ba-279">The IPsec pre-shared key for the site-to-site VPN connection (Table V - Item 5 - Value column).</span></span>
    
<span data-ttu-id="bb1ba-p115">Убедитесь, что адресное пространство виртуальной сети доступно из локальной сети. Для этого добавьте маршрут, соответствующий адресному пространству виртуальной сети на вашем VPN-устройстве и сообщите этот маршрут остальной инфраструктуре маршрутизации в сети организации. Чтобы определить, как это сделать, обратитесь в ИТ-отдел.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-p115">Next, ensure that the address space of the virtual network is reachable from your on-premises network. This is usually done by adding a route corresponding to the virtual network address space to your VPN device and then advertising that route to the rest of the routing infrastructure of your organization network. Work with your IT department to determine how to do this.</span></span>
  
<span data-ttu-id="bb1ba-p116">После этого определите имена четырех групп доступности. Заполните таблицу A.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-p116">Next, define the names of three availability sets. Fill out Table A.</span></span> 
  
|<span data-ttu-id="bb1ba-285">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="bb1ba-285">**Item**</span></span>|<span data-ttu-id="bb1ba-286">**Назначение**</span><span class="sxs-lookup"><span data-stu-id="bb1ba-286">**Purpose**</span></span>|<span data-ttu-id="bb1ba-287">**Имя набора доступности**</span><span class="sxs-lookup"><span data-stu-id="bb1ba-287">**Availability set name**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="bb1ba-288">1.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-288">1.</span></span>  <br/> |<span data-ttu-id="bb1ba-289">Контроллеры доменов</span><span class="sxs-lookup"><span data-stu-id="bb1ba-289">Domain controllers</span></span>  <br/> |<span data-ttu-id="bb1ba-290">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-290"></span></span>  <br/> |
|<span data-ttu-id="bb1ba-291">2.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-291">2.</span></span>  <br/> |<span data-ttu-id="bb1ba-292">Серверы AD FS</span><span class="sxs-lookup"><span data-stu-id="bb1ba-292">AD FS servers</span></span>  <br/> |<span data-ttu-id="bb1ba-293">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-293"></span></span>  <br/> |
|<span data-ttu-id="bb1ba-294">3.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-294">3.</span></span>  <br/> |<span data-ttu-id="bb1ba-295">Прокси-серверы веб-приложений</span><span class="sxs-lookup"><span data-stu-id="bb1ba-295">Web application proxy servers</span></span>  <br/> |<span data-ttu-id="bb1ba-296">_______________________________</span><span class="sxs-lookup"><span data-stu-id="bb1ba-296"></span></span>  <br/> |
   
 <span data-ttu-id="bb1ba-297">**Задает доступность ответ: таблицы**</span><span class="sxs-lookup"><span data-stu-id="bb1ba-297">**Table A: Availability sets**</span></span>
  
<span data-ttu-id="bb1ba-298">Вам потребуются эти имена при создании виртуальных машин на этапах 2, 3 и 4.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-298">You will need these names when you create the virtual machines in phases 2, 3, and 4.</span></span>
  
<span data-ttu-id="bb1ba-299">Создайте новые группы доступности с помощью этих команд Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-299">Create the new availability sets with these Azure PowerShell commands.</span></span>
  
```
$locName="<the Azure location for your new resource group>"
$rgName="<Table R - Item 1 - Resource group name column>"
$avName="<Table A - Item 1 - Availability set name column>"
New-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName -Location $locName
$rgName="<Table R - Item 2 - Resource group name column>"
$avName="<Table A - Item 2 - Availability set name column>"
New-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName -Location $locName
$rgName="<Table R - Item 3 - Resource group name column>"
$avName="<Table A - Item 3 - Availability set name column>"
New-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName -Location $locName
```

<span data-ttu-id="bb1ba-300">Ниже показана конфигурация, полученная в результате успешного выполнения этого этапа.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-300">This is the configuration resulting from the successful completion of this phase.</span></span>
  
<span data-ttu-id="bb1ba-301">**Этап 1: Azure инфраструктуры для обеспечения высокой доступности федеративной проверки подлинности для Office 365**</span><span class="sxs-lookup"><span data-stu-id="bb1ba-301">**Phase 1: The Azure infrastructure for high availability federated authentication for Office 365**</span></span>

![Этап 1. Федеративная проверка подлинности для Office 365 с высокой доступностью, развертывание которой выполняется в Azure с использованием инфраструктуры Azure](images/4e7ba678-07df-40ce-b372-021bf7fc91fa.png)
  
## <a name="next-step"></a><span data-ttu-id="bb1ba-303">Следующее действие</span><span class="sxs-lookup"><span data-stu-id="bb1ba-303">Next step</span></span>

<span data-ttu-id="bb1ba-304">Использование [высокой доступности федеративных проверки подлинности этап 2: Настройка контроллеров домена](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) чтобы продолжить работу конфигурации этой рабочей нагрузкой.</span><span class="sxs-lookup"><span data-stu-id="bb1ba-304">Use [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) to continue with the configuration of this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bb1ba-305">See Also</span><span class="sxs-lookup"><span data-stu-id="bb1ba-305">See Also</span></span>

[<span data-ttu-id="bb1ba-306">Развертывание в Azure федеративной проверки подлинности для обеспечения высокой доступности в случае использования Office 365</span><span class="sxs-lookup"><span data-stu-id="bb1ba-306">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="bb1ba-307">Федеративное удостоверение для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="bb1ba-307">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="bb1ba-308">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="bb1ba-308">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="bb1ba-309">Федеративные удостоверения для Office 365</span><span class="sxs-lookup"><span data-stu-id="bb1ba-309">Federated identity for Office 365</span></span>](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


