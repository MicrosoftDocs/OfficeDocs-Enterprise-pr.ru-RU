---
title: Фаза федеративной проверки подлинности высокого уровня доступности 4 Настройка прокси-серверов веб-приложений
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/15/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 1c903173-67cd-47da-86d9-d333972dda80
description: Сводка. Настройка прокси-серверов веб-приложений для федеративной проверки подлинности с высоким уровнем доступности для Office 365 в Microsoft Azure.
ms.openlocfilehash: c0a469f8945b9e69415b511c253e72a0118a4cfa
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "38027673"
---
# <a name="high-availability-federated-authentication-phase-4-configure-web-application-proxies"></a><span data-ttu-id="ed971-103">Этап 4. Федеративная проверка подлинности для обеспечения высокой доступности: настройка прокси веб-приложений</span><span class="sxs-lookup"><span data-stu-id="ed971-103">High availability federated authentication Phase 4: Configure web application proxies</span></span>

 <span data-ttu-id="ed971-104">**Сводка:** Настройка прокси-серверов веб-приложений для федеративной проверки подлинности с высоким уровнем доступности для Office 365 в Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="ed971-104">**Summary:** Configure the web application proxy servers for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
  
<span data-ttu-id="ed971-105">На этом этапе развертывания федеративной проверки подлинности с высоким уровнем доступности для Office 365 в службах инфраструктуры Azure создаются внутренний балансировщик нагрузки и два сервера AD FS.</span><span class="sxs-lookup"><span data-stu-id="ed971-105">In this phase of deploying high availability for Office 365 federated authentication in Azure infrastructure services, you create an internal load balancer and two AD FS servers.</span></span>
  
<span data-ttu-id="ed971-106">Необходимо выполнить этот этап перед переходом к [этапу федеративной проверки подлинности высокого уровня доступности 5: Настройка федеративной проверки подлинности для Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md).</span><span class="sxs-lookup"><span data-stu-id="ed971-106">You must complete this phase before moving on to [High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md).</span></span> <span data-ttu-id="ed971-107">Описание всех этапов см. в статье [Развертывание в Azure федеративной проверки подлинности для обеспечения высокой доступности в случае использования Office 365](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="ed971-107">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-internet-facing-load-balancer-in-azure"></a><span data-ttu-id="ed971-108">Создание подсистемы балансировки сетевой нагрузки в Azure для выхода из Интернета</span><span class="sxs-lookup"><span data-stu-id="ed971-108">Create the Internet-facing load balancer in Azure</span></span>

<span data-ttu-id="ed971-109">Необходимо создать подсистему балансировки нагрузки с выходом в Интернет, чтобы Azure перегрузил входящий трафик проверки подлинности клиента из Интернета между двумя серверами прокси-сервера веб-приложений.</span><span class="sxs-lookup"><span data-stu-id="ed971-109">You must create an Internet-facing load balancer so that Azure distributes the incoming client authentication traffic from the Internet evenly among the two web application proxy servers.</span></span>
  
> [!NOTE]
> <span data-ttu-id="ed971-110">Для указанных ниже последовательностей команд используется последняя версия Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ed971-110">The following command sets use the latest version of Azure PowerShell.</span></span> <span data-ttu-id="ed971-111">Обратитесь к разделу начало [работы с командлетами Azure PowerShell](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="ed971-111">See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="ed971-112">После того как вы задали значения расположения и группы ресурсов, запустите полученный блок в командной строки Azure PowerShell или в ИНТЕГРИРОВАНной среде выполнения PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ed971-112">When you have supplied location and resource group values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
<!--
> [!TIP]
> For a text file that has all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664). 
-->
  
```
# Set up key variables
$locName="<your Azure location>"
$rgName="<Table R - Item 4 - Resource group name column>"

$publicIP=New-AzPublicIpAddress -ResourceGroupName $rgName -Name "WebProxyPublicIP" -Location $LocName -AllocationMethod "Static"
$frontendIP=New-AzLoadBalancerFrontendIpConfig -Name "WebAppProxyServers-LBFE" -PublicIpAddress $publicIP
$beAddressPool=New-AzLoadBalancerBackendAddressPoolConfig -Name "WebAppProxyServers-LBBE"
$healthProbe=New-AzLoadBalancerProbeConfig -Name "WebServersProbe" -Protocol "TCP" -Port 443 -IntervalInSeconds 15 -ProbeCount 2
$lbrule=New-AzLoadBalancerRuleConfig -Name "WebTraffic" -FrontendIpConfiguration $frontendIP -BackendAddressPool $beAddressPool -Probe $healthProbe -Protocol "TCP" -FrontendPort 443 -BackendPort 443
New-AzLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers" -Location $locName -LoadBalancingRule $lbrule -BackendAddressPool $beAddressPool -Probe $healthProbe -FrontendIpConfiguration $frontendIP
```

<span data-ttu-id="ed971-113">Чтобы отобразить общедоступный IP-адрес, назначенный подсистеме балансировки нагрузки в Интернете, выполните следующие команды в командной строке Azure PowerShell на локальном компьютере:</span><span class="sxs-lookup"><span data-stu-id="ed971-113">To display the public IP address assigned to your Internet-facing load balancer, run these commands at the Azure PowerShell command prompt on your local computer:</span></span>
  
```
Write-Host (Get-AzPublicIpaddress -Name "WebProxyPublicIP" -ResourceGroup $rgName).IPAddress
```

## <a name="determine-your-federation-service-fqdn-and-create-dns-records"></a><span data-ttu-id="ed971-114">Определение полного доменного имени и создание записей DNS для службы федерации</span><span class="sxs-lookup"><span data-stu-id="ed971-114">Determine your federation service FQDN and create DNS records</span></span>

<span data-ttu-id="ed971-115">Необходимо определить DNS-имя, чтобы определить имя службы федерации в Интернете.</span><span class="sxs-lookup"><span data-stu-id="ed971-115">You need to determine the DNS name to identify your federation service name on the Internet.</span></span> <span data-ttu-id="ed971-116">Azure AD Connect настроит Office 365 с этим именем в фазе 5, которая становится частью URL-адреса, который Office 365 отправляет клиентам для получения маркера безопасности.</span><span class="sxs-lookup"><span data-stu-id="ed971-116">Azure AD Connect will configure Office 365 with this name in Phase 5, which will become part of the URL that Office 365 sends to connecting clients to get a security token.</span></span> <span data-ttu-id="ed971-117">Например, fs.contoso.com (FS означает служба Федерации).</span><span class="sxs-lookup"><span data-stu-id="ed971-117">An example is fs.contoso.com (fs stands for federation service).</span></span>
  
<span data-ttu-id="ed971-118">После того как вы ФДКН службу федерации, создайте запись A общедоступного домена DNS для службы федерации ФДКН, которая разрешается в общедоступный IP-адрес подсистемы балансировки нагрузки Azure, доступного для выхода в Интернет.</span><span class="sxs-lookup"><span data-stu-id="ed971-118">Once you have your federation service FDQN, create a public DNS domain A record for the federation service FDQN that resolves to the public IP address of the Azure Internet-facing load balancer.</span></span>
  
|<span data-ttu-id="ed971-119">**Name**</span><span class="sxs-lookup"><span data-stu-id="ed971-119">**Name**</span></span>|<span data-ttu-id="ed971-120">**Тип**</span><span class="sxs-lookup"><span data-stu-id="ed971-120">**Type**</span></span>|<span data-ttu-id="ed971-121">**TTL**</span><span class="sxs-lookup"><span data-stu-id="ed971-121">**TTL**</span></span>|<span data-ttu-id="ed971-122">**Значение**</span><span class="sxs-lookup"><span data-stu-id="ed971-122">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="ed971-123">Служба федерации ФДКН</span><span class="sxs-lookup"><span data-stu-id="ed971-123">federation service FDQN</span></span>  <br/> |<span data-ttu-id="ed971-124">A</span><span class="sxs-lookup"><span data-stu-id="ed971-124">A</span></span>  <br/> |<span data-ttu-id="ed971-125">3600</span><span class="sxs-lookup"><span data-stu-id="ed971-125">3600</span></span>  <br/> |<span data-ttu-id="ed971-126">общедоступный IP-адрес балансировщика нагрузки с выходом в Интернет Azure (отображается с помощью команды **Write-Host** в предыдущем разделе)</span><span class="sxs-lookup"><span data-stu-id="ed971-126">public IP address of the Azure Internet-facing load balancer (displayed by the **Write-Host** command in the previous section)</span></span> <br/> |
   
<span data-ttu-id="ed971-127">Вот пример:</span><span class="sxs-lookup"><span data-stu-id="ed971-127">Here is an example:</span></span>
  
|<span data-ttu-id="ed971-128">**Name**</span><span class="sxs-lookup"><span data-stu-id="ed971-128">**Name**</span></span>|<span data-ttu-id="ed971-129">**Тип**</span><span class="sxs-lookup"><span data-stu-id="ed971-129">**Type**</span></span>|<span data-ttu-id="ed971-130">**TTL**</span><span class="sxs-lookup"><span data-stu-id="ed971-130">**TTL**</span></span>|<span data-ttu-id="ed971-131">**Значение**</span><span class="sxs-lookup"><span data-stu-id="ed971-131">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="ed971-132">fs.contoso.com</span><span class="sxs-lookup"><span data-stu-id="ed971-132">fs.contoso.com</span></span>  <br/> |<span data-ttu-id="ed971-133">A</span><span class="sxs-lookup"><span data-stu-id="ed971-133">A</span></span>  <br/> |<span data-ttu-id="ed971-134">3600</span><span class="sxs-lookup"><span data-stu-id="ed971-134">3600</span></span>  <br/> |<span data-ttu-id="ed971-135">131.107.249.117</span><span class="sxs-lookup"><span data-stu-id="ed971-135">131.107.249.117</span></span>  <br/> |
   
<span data-ttu-id="ed971-136">Затем добавьте запись DNS-адреса в личное пространство имен DNS организации, которая разрешает полное доменное имя службы Федерации к частному IP-адресу, назначенному внутреннему подсистеме балансировки нагрузки для серверов AD FS (таблица I, элемент 4, столбец "значение").</span><span class="sxs-lookup"><span data-stu-id="ed971-136">Next, add a DNS address record to your organization's private DNS namespace that resolves your federation service FQDN to the private IP address assigned to the internal load balancer for the AD FS servers (Table I, item 4, Value column).</span></span>
  
## <a name="create-the-web-application-proxy-server-virtual-machines-in-azure"></a><span data-ttu-id="ed971-137">Создание виртуальных машин прокси-сервера веб-приложений в Azure</span><span class="sxs-lookup"><span data-stu-id="ed971-137">Create the web application proxy server virtual machines in Azure</span></span>

<span data-ttu-id="ed971-138">Используйте следующий блок команд Azure PowerShell, чтобы создать виртуальные машины для двух прокси-серверов веб-приложений.</span><span class="sxs-lookup"><span data-stu-id="ed971-138">Use the following block of Azure PowerShell commands to create the virtual machines for the two web application proxy servers.</span></span> 
  
<span data-ttu-id="ed971-139">Обратите внимание на то, что следующие наборы команд Azure PowerShell используют значения из следующих таблиц:</span><span class="sxs-lookup"><span data-stu-id="ed971-139">Note that the following Azure PowerShell command sets use values from the following tables:</span></span>
  
- <span data-ttu-id="ed971-140">таблица M (для виртуальных машин);</span><span class="sxs-lookup"><span data-stu-id="ed971-140">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="ed971-141">таблица R (для групп ресурсов);</span><span class="sxs-lookup"><span data-stu-id="ed971-141">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="ed971-142">таблица V (для параметров виртуальной сети);</span><span class="sxs-lookup"><span data-stu-id="ed971-142">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="ed971-143">таблица S (для подсетей);</span><span class="sxs-lookup"><span data-stu-id="ed971-143">Table S, for your subnets</span></span>
    
- <span data-ttu-id="ed971-144">таблица I (для статических IP-адресов);</span><span class="sxs-lookup"><span data-stu-id="ed971-144">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="ed971-145">таблица A (для групп доступности).</span><span class="sxs-lookup"><span data-stu-id="ed971-145">Table A, for your availability sets</span></span>
    
<span data-ttu-id="ed971-146">Помните, что вы определили таблицу M на [этапе высокодоступной федеративной проверки подлинности 2: Configure Domain Controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) and Tables R, V, S, I и A [with High Availability Authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span><span class="sxs-lookup"><span data-stu-id="ed971-146">Recall that you defined Table M in [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) and Tables R, V, S, I, and A in [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
<span data-ttu-id="ed971-147">Задав правильные значения, выполните полученный блок в командной строке Azure PowerShell или в интегрированной среде сценариев PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ed971-147">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
```
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 3 - Subnet name column>"
$avName="<Table A - Item 3 - Availability set name column>"
$rgNameTier="<Table R - Item 3 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName
$backendSubnet=Get-AzVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $vnet
$webLB=Get-AzLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers"

$rgName=$rgNameTier
$avSet=Get-AzAvailabilitySet -Name $avName -ResourceGroupName $rgName

# Create the first web application proxy server virtual machine
$vmName="<Table M - Item 6 - Virtual machine name column>"
$vmSize="<Table M - Item 6 - Minimum size column>"
$staticIP="<Table I - Item 7 - Value column>"
$diskStorageType="<Table M - Item 6 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first web application proxy server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second web application proxy virtual machine
$vmName="<Table M - Item 7 - Virtual machine name column>"
$vmSize="<Table M - Item 7 - Minimum size column>"
$staticIP="<Table I - Item 8 - Value column>"
$diskStorageType="<Table M - Item 7 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName  -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second web application proxy server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="ed971-148">Эти виртуальные машины предназначены для работы в интрасети, поэтому им не назначается общедоступный IP-адрес или метка доменного имени DNS и они не подключаются к Интернету.</span><span class="sxs-lookup"><span data-stu-id="ed971-148">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet.</span></span> <span data-ttu-id="ed971-149">Однако это также означает, что к ним невозможно подключиться с помощью портала Azure.</span><span class="sxs-lookup"><span data-stu-id="ed971-149">However, this also means that you cannot connect to them from the Azure portal.</span></span> <span data-ttu-id="ed971-150">Команда **Подключиться** недоступна при просмотре свойств виртуальной машины.</span><span class="sxs-lookup"><span data-stu-id="ed971-150">The **Connect** option is unavailable when you view the properties of the virtual machine.</span></span> <span data-ttu-id="ed971-151">Используйте подключение к удаленному рабочему столу или другой инструмент удаленного рабочего стола, чтобы подключиться к виртуальной машине, используя свой частный IP-адрес или DNS-имя интрасети, а также учетные данные локальной учетной записи администратора.</span><span class="sxs-lookup"><span data-stu-id="ed971-151">Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="ed971-152">Здесь показана конфигурация, полученная в результате успешного выполнения этого этапа (с заполнителями вместо имен компьютеров).</span><span class="sxs-lookup"><span data-stu-id="ed971-152">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="ed971-153">**Этап 4: подсистема балансировки нагрузки на основе Интернета и прокси-серверы веб-приложений для инфраструктуры федеративной проверки подлинности с высоким уровнем доступности в Azure**</span><span class="sxs-lookup"><span data-stu-id="ed971-153">**Phase 4: The Internet-facing load balancer and web application proxy servers for your high availability federated authentication infrastructure in Azure**</span></span>

![Этап 4 инфраструктуры федеративной проверки подлинности Office 365 с высоким уровнем доступности в Azure с помощью прокси-серверов веб-приложений](media/7e03183f-3b3b-4cbe-9028-89cc3f195a63.png)
  
## <a name="next-step"></a><span data-ttu-id="ed971-155">Следующее действие</span><span class="sxs-lookup"><span data-stu-id="ed971-155">Next step</span></span>

<span data-ttu-id="ed971-156">Применение [федеративной проверки подлинности с высоким уровнем доступности этап 5: Настройка федеративной проверки подлинности для Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) для продолжения настройки этой рабочей нагрузки.</span><span class="sxs-lookup"><span data-stu-id="ed971-156">Use [High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ed971-157">См. также</span><span class="sxs-lookup"><span data-stu-id="ed971-157">See Also</span></span>

[<span data-ttu-id="ed971-158">Развертывание в Azure федеративной проверки подлинности для обеспечения высокой доступности в случае использования Office 365</span><span class="sxs-lookup"><span data-stu-id="ed971-158">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="ed971-159">Федеративное удостоверение для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="ed971-159">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="ed971-160">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="ed971-160">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

