---
title: Имитация распределенной виртуальной сети в Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/09/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 0a3555dc-6f96-49a5-b9e2-7760e16630b3
description: Сводка. Создание имитации распределенной виртуальной сети в Microsoft Azure как среды разработки и тестирования.
ms.openlocfilehash: 57262ee58f539fffbb0fc5b92c3a24f4c9204293
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741215"
---
# <a name="simulated-cross-premises-virtual-network-in-azure"></a><span data-ttu-id="35e73-103">Имитация распределенной виртуальной сети в Azure</span><span class="sxs-lookup"><span data-stu-id="35e73-103">Simulated cross-premises virtual network in Azure</span></span>

 <span data-ttu-id="35e73-104">**Сводка.** Создание имитации распределенной виртуальной сети в Microsoft Azure как среды разработки и тестирования.</span><span class="sxs-lookup"><span data-stu-id="35e73-104">**Summary:** Create a simulated cross-premises virtual network in Microsoft Azure as a dev/test environment.</span></span>
  
<span data-ttu-id="35e73-p101">В этой статье описаны действия по созданию имитации гибридной облачной среды в Microsoft Azure с помощью двух виртуальных сетей Azure. Ниже показана итоговая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="35e73-p101">This article steps you through creating a simulated hybrid cloud environment with Microsoft Azure using two Azure virtual networks. Here is the resulting configuration.</span></span> 
  
![Этап 3: создание имитации распределенной виртуальной сети как среды разработки и тестирования (с виртуальной машиной DC2 в сети XPrem)](media/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
<span data-ttu-id="35e73-108">Так имитируется гибридная облачная рабочая среда Azure IaaS, которая включает:</span><span class="sxs-lookup"><span data-stu-id="35e73-108">This simulates an Azure IaaS hybrid cloud production environment and consists of:</span></span>
  
- <span data-ttu-id="35e73-109">Имитацию упрощенной локальной сети, размещенной в виртуальной сети Azure (TestLab).</span><span class="sxs-lookup"><span data-stu-id="35e73-109">A simulated and simplified on-premises network hosted in an Azure virtual network (the TestLab virtual network).</span></span>
    
- <span data-ttu-id="35e73-110">Имитацию распределенной виртуальной сети, размещенной в Azure (XPrem).</span><span class="sxs-lookup"><span data-stu-id="35e73-110">A simulated cross-premises virtual network hosted in Azure (XPrem).</span></span>
    
- <span data-ttu-id="35e73-111">Пиринговую связь между двумя виртуальными сетями.</span><span class="sxs-lookup"><span data-stu-id="35e73-111">A VNet peering relationship between the two virtual networks.</span></span>
    
- <span data-ttu-id="35e73-112">Дополнительный контроллер домена в виртуальной сети XPrem.</span><span class="sxs-lookup"><span data-stu-id="35e73-112">A secondary domain controller in the XPrem virtual network.</span></span>
    
<span data-ttu-id="35e73-113">Это обеспечивает общую исходную точку, начиная с которой, вы можете:</span><span class="sxs-lookup"><span data-stu-id="35e73-113">This provides a basis and common starting point from which you can:</span></span> 
  
- <span data-ttu-id="35e73-114">Разрабатывать и тестировать приложения в имитированной гибридной облачной среде Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="35e73-114">Develop and test applications in a simulated Azure IaaS hybrid cloud environment.</span></span>
    
- <span data-ttu-id="35e73-115">Создавать тестовые конфигурации компьютеров внутри виртуальной сети (для некоторых это TestLab, а для некоторых — XPrem), чтобы имитировать рабочие ИТ-нагрузки на основе гибридного облака.</span><span class="sxs-lookup"><span data-stu-id="35e73-115">Create test configurations of computers, some within the TestLab virtual network and some within the XPrem virtual network, to simulate hybrid cloud-based IT workloads.</span></span>
    
<span data-ttu-id="35e73-116">Процесс настройки этой среды разработки и тестирования состоит из трех перечисленных ниже основных этапов.</span><span class="sxs-lookup"><span data-stu-id="35e73-116">There are three major phases to setting up this dev/test environment:</span></span>
  
1. <span data-ttu-id="35e73-117">Настраивать виртуальную сеть TestLab.</span><span class="sxs-lookup"><span data-stu-id="35e73-117">Configure the TestLab virtual network.</span></span>
    
2. <span data-ttu-id="35e73-118">Создавать распределенную виртуальную сеть.</span><span class="sxs-lookup"><span data-stu-id="35e73-118">Create the cross-premises virtual network.</span></span>
    
3. <span data-ttu-id="35e73-119">Настраивать DC2.</span><span class="sxs-lookup"><span data-stu-id="35e73-119">Configure DC2.</span></span>
    
> [!NOTE]
> <span data-ttu-id="35e73-120">Эта конфигурация требует платной подписки на Azure.</span><span class="sxs-lookup"><span data-stu-id="35e73-120">This configuration requires a paid Azure subscription.</span></span> 
  
![Руководства по лаборатории тестирования в Microsoft Cloud](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="35e73-122">Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования в Office 365.</span><span class="sxs-lookup"><span data-stu-id="35e73-122">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Microsoft 365 Enterprise Test Lab Guide stack.</span></span>
  
## <a name="phase-1-configure-the-testlab-virtual-network"></a><span data-ttu-id="35e73-123">Этап 1. Настройка виртуальной сети TestLab</span><span class="sxs-lookup"><span data-stu-id="35e73-123">Phase 1: Configure the TestLab virtual network</span></span>

<span data-ttu-id="35e73-124">Воспользуйтесь инструкциями в статье [Базовая конфигурация среды разработки и тестирования](base-configuration-dev-test-environment.md), чтобы настроить компьютеры DC1, APP1 и CLIENT1 в виртуальной сети Azure под названием TestLab.</span><span class="sxs-lookup"><span data-stu-id="35e73-124">Use the instructions in [Base Configuration dev/test environment](base-configuration-dev-test-environment.md) to configure the DC1, APP1, and CLIENT1 computers in the Azure virtual network named TestLab.</span></span>
  
<span data-ttu-id="35e73-125">Это ваша текущая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="35e73-125">This is your current configuration.</span></span> 
  
![Этап 4. Базовая конфигурация в Azure, включающая виртуальную машину CLIENT1](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
## <a name="phase-2-create-the-xprem-virtual-network"></a><span data-ttu-id="35e73-127">Этап 2. Создание виртуальной сети XPrem</span><span class="sxs-lookup"><span data-stu-id="35e73-127">Phase 2: Create the XPrem virtual network</span></span>

<span data-ttu-id="35e73-128">На этом этапе создается и настраивается новая виртуальная сеть XPrem, а затем подключается к пиринговой виртуальной сети TestLab.</span><span class="sxs-lookup"><span data-stu-id="35e73-128">In this phase, you create and configure the new XPrem virtual network and then connect it to the TestLab virtual network with VNet peering.</span></span>
  
<span data-ttu-id="35e73-129">Во-первых, запустите командную строку Azure PowerShell на своем локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="35e73-129">First, start an Azure PowerShell prompt on your local computer.</span></span>
  
> [!NOTE]
> <span data-ttu-id="35e73-p102">Для приведенных ниже последовательностей команд используется последняя версия Azure PowerShell. См. статью [Общие сведения об Azure PowerShell](https://docs.microsoft.com/ru-RU/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="35e73-p102">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/ru-RU/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="35e73-132">Войдите в свою учетную запись Azure с помощью указанной ниже команды.</span><span class="sxs-lookup"><span data-stu-id="35e73-132">Sign in to your Azure account with this command.</span></span>
  
```
Connect-AzAccount
```

<!--
> [!TIP]
> Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-7844edd0) to get a text file that has all of the PowerShell commands in this article.
-->
  
<span data-ttu-id="35e73-133">Получите имя подписки с помощью приведенной ниже команды.</span><span class="sxs-lookup"><span data-stu-id="35e73-133">Get your subscription name using this command.</span></span>
  
```
Get-AzSubscription | Sort Name | Select Name
```

<span data-ttu-id="35e73-p103">Укажите свою подписку Azure. Замените текст в кавычках, в том числе символы "\<" и ">", на правильное имя.</span><span class="sxs-lookup"><span data-stu-id="35e73-p103">Set your Azure subscription. Replace everything within the quotes, including the \< and > characters, with the correct names.</span></span>
  
```
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

<span data-ttu-id="35e73-136">Далее создайте виртуальную сеть XPrem и защитите ее с помощью группы безопасности сети, воспользовавшись этими командами.</span><span class="sxs-lookup"><span data-stu-id="35e73-136">Next, create the XPrem virtual network and protect it with a network security group with these commands.</span></span>
  
```
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$Testnet=New-AzVirtualNetworkSubnetConfig -Name "Testnet" -AddressPrefix 192.168.0.0/24
New-AzVirtualNetwork -Name "XPrem" -ResourceGroupName $rgName -Location $locName -AddressPrefix 192.168.0.0/16 -Subnet $Testnet -DNSServer 10.0.0.4
$rule1=New-AzNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzNetworkSecurityGroup -Name "Testnet" -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name XPrem
$nsg=Get-AzNetworkSecurityGroup -Name "Testnet" -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "Testnet" -AddressPrefix 192.168.0.0/24 -NetworkSecurityGroup $nsg
```

<span data-ttu-id="35e73-137">Затем создайте пиринговую связь между виртуальными сетями TestLab и XPrem с помощью этих команд.</span><span class="sxs-lookup"><span data-stu-id="35e73-137">Next, you create the VNet peering relationship between the TestLab and XPrem VNets with these commands.</span></span>
  
```
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$vnet1=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$vnet2=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name XPrem
Add-AzVirtualNetworkPeering -Name TestLab2XPrem -VirtualNetwork $vnet1 -RemoteVirtualNetworkId $vnet2.Id
Add-AzVirtualNetworkPeering -Name XPrem2TestLab -VirtualNetwork $vnet2 -RemoteVirtualNetworkId $vnet1.Id
```

<span data-ttu-id="35e73-138">Это ваша текущая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="35e73-138">This is your current configuration.</span></span> 
  
![Этап 2: создание имитации распределенной виртуальной сети как среды разработки и тестирования (с сетью XPrem и пиринговыми отношениями)](media/cac5e999-69c7-4f4c-bfce-a7f4006115ef.png)
  
## <a name="phase-3-configure-dc2"></a><span data-ttu-id="35e73-140">Этап 3. Настройка DC2</span><span class="sxs-lookup"><span data-stu-id="35e73-140">Phase 3: Configure DC2</span></span>

<span data-ttu-id="35e73-141">На этом этапе нужно создать виртуальную машину DC2 в виртуальной сети XPrem, а затем настроить ее в качестве контроллера домена реплики.</span><span class="sxs-lookup"><span data-stu-id="35e73-141">In this phase, you create the DC2 virtual machine in the XPrem virtual network and then configure it as a replica domain controller.</span></span>
  
<span data-ttu-id="35e73-p104">Сначала создайте виртуальную машину для DC2. Выполните эти команды в командной строке Azure PowerShell на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="35e73-p104">First, create a virtual machine for DC2. Run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<your resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name XPrem -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name DC2-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name DC2-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 192.168.0.4
$vm=New-AzVMConfig -VMName DC2 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC2."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName DC2 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "DC2-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
$diskConfig=New-AzDiskConfig -AccountType "Standard_LRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzDisk -DiskName "DC2-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name "DC2-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="35e73-144">Затем подключитесь к новой виртуальной машине DC2 на [портале Azure](https://portal.azure.com) с помощью имени и пароля учетной записи администратора.</span><span class="sxs-lookup"><span data-stu-id="35e73-144">Next, connect to the new DC2 virtual machine from the [Azure portal](https://portal.azure.com) using its local administrator account name and password.</span></span>
  
<span data-ttu-id="35e73-p105">Далее настройте правило брандмауэра Windows, разрешающее трафик для тестирования базовых параметров подключения. С помощью командной строки Windows PowerShell уровня администратора на DC2 выполните эти команды.</span><span class="sxs-lookup"><span data-stu-id="35e73-p105">Next, configure a Windows Firewall rule to allow traffic for basic connectivity testing. From an administrator-level Windows PowerShell command prompt on DC2, run these commands.</span></span> 
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
ping dc1.corp.contoso.com
```

<span data-ttu-id="35e73-p106">В результате команды проверки связи должны прийти четыре успешных ответа с IP-адреса 10.0.0.4. Это тест трафика в рамках пиринговой виртуальной сети.</span><span class="sxs-lookup"><span data-stu-id="35e73-p106">The ping command should result in four successful replies from IP address 10.0.0.4. This is a test of traffic across the VNet peering relationship.</span></span> 
  
<span data-ttu-id="35e73-149">Далее добавьте на контроллере домена DC2 дополнительный диск с данными в качестве нового тома с буквой диска "F:", используя для этого указанные ниже команды в командной строке Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="35e73-149">Next, add the extra data disk as a new volume with the drive letter F: with this command from the Windows PowerShell command prompt on DC2.</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="35e73-p107">Затем настройте виртуальную машину DC2 как контроллер домена реплики для corp.contoso.com. Выполните указанные ниже команды в командной строке Windows PowerShell на DC2.</span><span class="sxs-lookup"><span data-stu-id="35e73-p107">Next, configure DC2 as a replica domain controller for the corp.contoso.com domain. Run these commands from the Windows PowerShell command prompt on DC2.</span></span>
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -Credential (Get-Credential CORP\User1) -DomainName "corp.contoso.com" -InstallDns:$true -DatabasePath "F:\NTDS" -LogPath "F:\Logs" -SysvolPath "F:\SYSVOL"
```

<span data-ttu-id="35e73-152">Обратите внимание: вам предлагается указать пароли как пользователя CORP\\User1, так и режима восстановления службы каталогов (DSRM), а затем перезапустить DC2.</span><span class="sxs-lookup"><span data-stu-id="35e73-152">Note that you are prompted to supply both the CORP\\User1 password and a Directory Services Restore Mode (DSRM) password, and to restart DC2.</span></span> 
  
<span data-ttu-id="35e73-p108">Теперь, когда у виртуальной сети XPrem есть свой DNS-сервер (DC2), вам нужно настроить XPrem для использования этого DNS-сервера. Выполните эти команды в командной строке Azure PowerShell на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="35e73-p108">Now that the XPrem virtual network has its own DNS server (DC2), you must configure the XPrem virtual network to use this DNS server. Run these commands from the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -name "XPrem"
$vnet.DhcpOptions.DnsServers="192.168.0.4" 
Set-AzVirtualNetwork -VirtualNetwork $vnet
Restart-AzVM -ResourceGroupName $rgName -Name "DC2"
```

<span data-ttu-id="35e73-p109">На портале Azure на локальном компьютере подключитесь к DC1 с помощью учетных данных CORP\\User1. Чтобы настроить домен CORP для проверки подлинности пользователей и компьютеров с помощью их локального контроллера домена, выполните эти команды из командной строки Windows PowerShell уровня администратора на DC1.</span><span class="sxs-lookup"><span data-stu-id="35e73-p109">From the Azure portal on your local computer, connect to DC1 with the CORP\\User1 credentials. To configure the CORP domain so that computers and users use their local domain controller for authentication, run these commands from an administrator-level Windows PowerShell command prompt on DC1.</span></span>
  
```
New-ADReplicationSite -Name "TestLab" 
New-ADReplicationSite -Name "XPrem"
New-ADReplicationSubnet -Name "10.0.0.0/8" -Site "TestLab"
New-ADReplicationSubnet -Name "192.168.0.0/16" -Site "XPrem"
```

<span data-ttu-id="35e73-157">Это ваша текущая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="35e73-157">This is your current configuration.</span></span> 
  
![Этап 3: создание имитации распределенной виртуальной сети как среды разработки и тестирования (с виртуальной машиной DC2 в сети XPrem)](media/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
<span data-ttu-id="35e73-159">Ваша имитированная гибридная облачная среда Azure готова к тестированию.</span><span class="sxs-lookup"><span data-stu-id="35e73-159">Your simulated Azure hybrid cloud environment is now ready for testing.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="35e73-160">Следующее действие</span><span class="sxs-lookup"><span data-stu-id="35e73-160">Next step</span></span>

<span data-ttu-id="35e73-161">Используйте эту среду тестирования и разработки для имитации [фермы SharePoint Server 2016 с интрасетью, размещенной в Azure](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx).</span><span class="sxs-lookup"><span data-stu-id="35e73-161">Use this dev/test environment to simulate a [SharePoint Server 2016 intranet farm hosted in Azure](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="35e73-162">См. также</span><span class="sxs-lookup"><span data-stu-id="35e73-162">See Also</span></span>

[<span data-ttu-id="35e73-163">Базовая конфигурация среды разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="35e73-163">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="35e73-164">Среда разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="35e73-164">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="35e73-165">DirSync для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="35e73-165">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="35e73-166">Cloud App Security для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="35e73-166">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="35e73-167">Advanced Threat Protection в среде разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="35e73-167">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="35e73-168">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="35e73-168">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


