---
title: "Базовая конфигурация среды разработки и тестирования"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- jan17entnews
- Strat_O365_Enterprise
- Ent_TLGs
ms.assetid: 6fcbb50c-ac68-4be7-9fc5-dd0f275c1e3d
description: "Сводка: Создание упрощенный интрасети в среде разработки или тестирования в Microsoft Azure."
ms.openlocfilehash: 672486f62a940d812c821fda67d3e92a4164eea8
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="base-configuration-devtest-environment"></a><span data-ttu-id="77852-103">Базовая конфигурация среды разработки и тестирования</span><span class="sxs-lookup"><span data-stu-id="77852-103">Base Configuration dev/test environment</span></span>

 <span data-ttu-id="77852-104">**Сводка:** Создайте упрощенный интрасети в качестве среды разработки или тестирования в Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="77852-104">**Summary:** Create a simplified intranet as a dev/test environment in Microsoft Azure.</span></span>
  
<span data-ttu-id="77852-105">Эта статья содержит пошаговые инструкции по созданию среды разработки и тестирования с базовой конфигурацией в Azure.</span><span class="sxs-lookup"><span data-stu-id="77852-105">This article provides you with step-by-step instructions to create the following Base Configuration dev/test environment in Azure:</span></span>
  
<span data-ttu-id="77852-106">**На рисунке 1: Среде разработки и тестирования базовой конфигурации**</span><span class="sxs-lookup"><span data-stu-id="77852-106">**Figure 1: The Base Configuration dev/test environment**</span></span>

![Этап 4. Базовая конфигурация в Azure, включающая виртуальную машину CLIENT1](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
<span data-ttu-id="77852-p101">Среда разработки и тестирования с базовой конфигурацией, представленная на рис. 1, состоит из корпоративной подсети в облачной виртуальной сети Azure под названием TestLab. Последняя является симуляцией упрощенной частной интрасети, подключенной к Интернету. Она содержит три виртуальные машины Azure под управлением Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="77852-p101">The Base Configuration dev/test environment in Figure 1 consists of the Corpnet subnet in a cloud-only Azure virtual network named TestLab that simulates a simplified, private intranet connected to the Internet. It contains three Azure virtual machines running Windows Server 2016:</span></span>
  
- <span data-ttu-id="77852-110">DC1 настроена в качестве контроллера домена интрасети и сервера доменных имен (DNS).</span><span class="sxs-lookup"><span data-stu-id="77852-110">DC1 is configured as an intranet domain controller and Domain Name System (DNS) server</span></span>
    
- <span data-ttu-id="77852-111">APP1 настроена в качестве общего сервера приложений и веб-сервера.</span><span class="sxs-lookup"><span data-stu-id="77852-111">APP1 is configured as a general application and web server</span></span>
    
- <span data-ttu-id="77852-112">	CLIENT1 действует как клиент интрасети.</span><span class="sxs-lookup"><span data-stu-id="77852-112">CLIENT1 acts as an intranet client</span></span>
    
<span data-ttu-id="77852-113">Вот что обеспечивает такая конфигурация для виртуальных машин DC1, APP1, CLIENT1 и дополнительных компьютеров корпоративной подсети: </span><span class="sxs-lookup"><span data-stu-id="77852-113">This configuration allows DC1, APP1, CLIENT1, and additional Corpnet subnet computers to be:</span></span> 
  
- <span data-ttu-id="77852-114">Подключение к Интернету для установки обновлений, доступ к ресурсам Интернета в режиме реального времени и участвовать в общедоступное облако технологии, такие как Microsoft Office 365 и других служб Azure.</span><span class="sxs-lookup"><span data-stu-id="77852-114">Connected to the Internet to install updates, access Internet resources in real time, and participate in public cloud technologies such as Microsoft Office 365 and other Azure services.</span></span>
    
- <span data-ttu-id="77852-115">	Управление при помощи подключения к удаленному рабочему столу с компьютера, соединенного с Интернетом или сетью организации.</span><span class="sxs-lookup"><span data-stu-id="77852-115">Remotely managed using Remote Desktop connections from your computer that is connected to the Internet or your organization network.</span></span>
    
<span data-ttu-id="77852-116">Цели использования получившейся тестовой среды:</span><span class="sxs-lookup"><span data-stu-id="77852-116">You can use the resulting test environment:</span></span>
  
- <span data-ttu-id="77852-117">Разработка и тестирование приложений.</span><span class="sxs-lookup"><span data-stu-id="77852-117">For application development and testing.</span></span>
    
- <span data-ttu-id="77852-118">Как начальной настройке среды расширенного теста проекта, который включает в себя дополнительных виртуальных машин, служб Azure или другие предложения облаке Майкрософт: Office 365 и безопасности предприятия + мобильности.</span><span class="sxs-lookup"><span data-stu-id="77852-118">As the initial configuration of an extended test environment of your own design that includes additional virtual machines, Azure services, or other Microsoft cloud offerings such as Office 365 and Enterprise Security + Mobility.</span></span>
    
<span data-ttu-id="77852-119">Существует четыре этапа настройки тестовой среды с базовой конфигурацией в Azure:</span><span class="sxs-lookup"><span data-stu-id="77852-119">There are four phases to setting up the Base Configuration test environment in Azure:</span></span>
  
1. <span data-ttu-id="77852-120">создание виртуальной сети;</span><span class="sxs-lookup"><span data-stu-id="77852-120">Create the virtual network.</span></span>
    
2. <span data-ttu-id="77852-121">	настройка DC1;</span><span class="sxs-lookup"><span data-stu-id="77852-121">Configure DC1.</span></span>
    
3. <span data-ttu-id="77852-122">	настройка APP1;</span><span class="sxs-lookup"><span data-stu-id="77852-122">Configure APP1.</span></span>
    
4. <span data-ttu-id="77852-123">	настройка CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="77852-123">Configure CLIENT1.</span></span>
    
<span data-ttu-id="77852-p102">Если вы уже нет Azure подписки, можно Зарегистрируйтесь бесплатную пробную версию в [Попробуйте Azure](https://azure.microsoft.com/pricing/free-trial/). Если у вас есть подписка на MSDN или Visual Studio, видеть [кредит ежемесячный Azure для подписчиков Visual Studio](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span><span class="sxs-lookup"><span data-stu-id="77852-p102">If you do not already have an Azure subscription, you can sign up for a free trial at [Try Azure](https://azure.microsoft.com/pricing/free-trial/). If you have an MSDN or Visual Studio subscription, see [Monthly Azure credit for Visual Studio subscribers](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span></span>
  
> [!NOTE]
> <span data-ttu-id="77852-p103">Виртуальных машин в Azure требует текущие расходы на денежные они выполняются. Расходы на этом международные с подпиской MSDN бесплатную пробную, или оплата за подписку. Дополнительные сведения о стоимости под управлением виртуальных машин Azure просмотрите [Сведения о ценах виртуальных машин](https://azure.microsoft.com/pricing/details/virtual-machines/) и [Калькулятор цен Azure](https://azure.microsoft.com/pricing/calculator/). Чтобы сократить издержки, обратитесь к разделу [сокращение расходов на тестовой среды виртуальных машин в Azure](base-configuration-dev-test-environment.md#mincost).</span><span class="sxs-lookup"><span data-stu-id="77852-p103">Virtual machines in Azure incur an ongoing monetary cost when they are running. This cost is billed against your free trial, MSDN subscription, or paid subscription. For more information about the costs of running Azure virtual machines, see [Virtual Machines Pricing Details](https://azure.microsoft.com/pricing/details/virtual-machines/) and [Azure Pricing Calculator](https://azure.microsoft.com/pricing/calculator/). To keep costs down, see [Minimizing the costs of test environment virtual machines in Azure](base-configuration-dev-test-environment.md#mincost).</span></span> 
  
![Руководства по лаборатории тестирования в Microsoft Cloud](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="77852-131">Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="77852-131">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-virtual-network"></a><span data-ttu-id="77852-132">Этап 1. Создание виртуальной сети</span><span class="sxs-lookup"><span data-stu-id="77852-132">Phase 1: Create the virtual network</span></span>

<span data-ttu-id="77852-133">Сначала запустите командную строку Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="77852-133">First, start an Azure PowerShell prompt.</span></span>
  
> [!NOTE]
> <span data-ttu-id="77852-p104">Следующие наборы команд использовать последнюю версию Windows Azure PowerShell. В разделе [Начало работы с Windows Azure PowerShell командлетов](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="77852-p104">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="77852-136">Войдите в свою учетную запись Azure с помощью указанной ниже команды.</span><span class="sxs-lookup"><span data-stu-id="77852-136">Sign in to your Azure account with the following command.</span></span>
  
```
Login-AzureRMAccount
```

> [!TIP]
> <span data-ttu-id="77852-137">Щелкните [здесь](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d) для получения текстовый файл, содержащий все команды PowerShell в данной статье.</span><span class="sxs-lookup"><span data-stu-id="77852-137">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d) to get a text file that contains all the PowerShell commands in this article.</span></span>
  
<span data-ttu-id="77852-138">Получите имя подписки с помощью следующей команды.</span><span class="sxs-lookup"><span data-stu-id="77852-138">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="77852-p105">Укажите свою подписку Azure. Замените текст в кавычках, в том числе символы "<" и ">", на правильное имя.</span><span class="sxs-lookup"><span data-stu-id="77852-p105">Set your Azure subscription. Replace everything within the quotes, including the < and > characters, with the correct name.</span></span>
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

<span data-ttu-id="77852-p106">Затем создайте группу ресурсов для лаборатории тестирования с базовой конфигурацией. Чтобы определить уникальное имя группы ресурсов, используйте указанную ниже команду для вывода списка имеющихся групп ресурсов.</span><span class="sxs-lookup"><span data-stu-id="77852-p106">Next, create a new resource group for your Base Configuration test lab. To determine a unique resource group name, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="77852-p107">Создайте группу ресурсов с помощью приведенных ниже команд. Замените все символы в кавычках (в том числе символы "<" и ">") правильными именами.</span><span class="sxs-lookup"><span data-stu-id="77852-p107">Create your new resource group with these commands. Replace everything within the quotes, including the < and > characters, with the correct names.</span></span>
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="77852-145">Затем создайте виртуальную сеть TestLab, в которой будет размещена корпоративная подсеть базовой конфигурации, и защитите ее с помощью группы безопасности сети.</span><span class="sxs-lookup"><span data-stu-id="77852-145">Next, you create the TestLab virtual network that will host the Corpnet subnet of the base configuration and protect it with a network security group.</span></span>
  
```
$rgName="<name of your new resource group>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$corpnetSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet -DNSServer 10.0.0.4
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$nsg=Get-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
```

<span data-ttu-id="77852-146">Это — ваша текущая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="77852-146">This is your current configuration.</span></span>
  
![Этап 1. Базовая конфигурация в Azure, включающая виртуальную сеть и подсеть](images/0b5634fc-4e1c-469d-873d-97ed7e587411.png)
  
## <a name="phase-2-configure-dc1"></a><span data-ttu-id="77852-148">Этап 2. Настройка DC1</span><span class="sxs-lookup"><span data-stu-id="77852-148">Phase 2: Configure DC1</span></span>

<span data-ttu-id="77852-149">На этом этапе мы создадим виртуальную машину DC1 и настроим ее как контроллер для домена Windows Server Active Directory corp.contoso.com и DNS-сервер для виртуальных машин сети TestLab.</span><span class="sxs-lookup"><span data-stu-id="77852-149">In this phase, we create the DC1 virtual machine and configure it as a domain controller for the corp.contoso.com Windows Server Active Directory (AD) domain and a DNS server for the virtual machines of the TestLab virtual network.</span></span>
  
<span data-ttu-id="77852-150">Чтобы создать Azure виртуальной машины для DC1, заполните поля имя группы ресурсов и выполните следующие команды в командной строке Windows Azure PowerShell на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="77852-150">To create an Azure virtual machine for DC1, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name DC1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name DC1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 10.0.0.4
$vm=New-AzureRMVMConfig -VMName DC1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName DC1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "DC1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
$diskConfig=New-AzureRmDiskConfig -AccountType "StandardLRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzureRmDisk -DiskName "DC1-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name "DC1-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="77852-p108">Вам будет предложено ввести имя пользователя и пароль учетной записи локального администратора на DC1. Задайте надежный пароль и запишите его вместе с именем пользователя в безопасном месте.</span><span class="sxs-lookup"><span data-stu-id="77852-p108">You will be prompted for a user name and password for the local administrator account on DC1. Use a strong password and record both the name and password in a secure location.</span></span>
  
<span data-ttu-id="77852-153">После этого подключитесь к виртуальной машине DC1.</span><span class="sxs-lookup"><span data-stu-id="77852-153">Next, connect to the DC1 virtual machine.</span></span>
  
### <a name="connect-to-dc1-using-local-administrator-account-credentials"></a><span data-ttu-id="77852-154">Подключение к DC1 с помощью учетных данных учетной записи локального администратора</span><span class="sxs-lookup"><span data-stu-id="77852-154">Connect to DC1 using local administrator account credentials</span></span>

1. <span data-ttu-id="77852-155">В [Azure портала](https://portal.azure.com), нажмите кнопку **группы ресурсов >** <the name of your new resource group> **> DC1 > подключить**.</span><span class="sxs-lookup"><span data-stu-id="77852-155">In the [Azure portal](https://portal.azure.com), click **Resource Groups >** <the name of your new resource group> **> DC1 > Connect**.</span></span>
    
2. <span data-ttu-id="77852-156">Откройте файл DC1.rdp, который будет загружен и нажмите кнопку **Подключить**.</span><span class="sxs-lookup"><span data-stu-id="77852-156">Open the DC1.rdp file that is downloaded, and then click **Connect**.</span></span>
    
3. <span data-ttu-id="77852-157">Укажите имя учетной записи локального администратора DC1.</span><span class="sxs-lookup"><span data-stu-id="77852-157">Specify the DC1 local administrator account name:</span></span>
    
  - <span data-ttu-id="77852-158">Для Windows 7:</span><span class="sxs-lookup"><span data-stu-id="77852-158">For Windows 7:</span></span>
    
    <span data-ttu-id="77852-p109">В диалоговом окне **Безопасности Windows** выберите **использовать другую учетную запись**. В поле **имя пользователя**введите **DC1\\**[имя учетной записи локального администратора].</span><span class="sxs-lookup"><span data-stu-id="77852-p109">In the **Windows Security** dialog box, click **Use another account**. In **User name**, type **DC1\\**[Local administrator account name].</span></span>
    
  - <span data-ttu-id="77852-161">Для Windows 8 или Windows 10:</span><span class="sxs-lookup"><span data-stu-id="77852-161">For Windows 8 or Windows 10:</span></span>
    
    <span data-ttu-id="77852-p110">В диалоговом окне **Безопасности Windows** нажмите кнопку **Дополнительные параметры**и нажмите кнопку **использовать другую учетную запись**. В поле **имя пользователя**введите **DC1\\**[имя учетной записи локального администратора].</span><span class="sxs-lookup"><span data-stu-id="77852-p110">In the **Windows Security** dialog box, click **More choices**, and then click **Use a different account**. In **User name**, type **DC1\\**[Local administrator account name].</span></span>
    
4. <span data-ttu-id="77852-164">В поле **пароль**введите пароль учетной записи локального администратора и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="77852-164">In **Password**, type the password of the local administrator account, and then click **OK**.</span></span>
    
5. <span data-ttu-id="77852-165">При появлении запроса нажмите кнопку **Да**.</span><span class="sxs-lookup"><span data-stu-id="77852-165">When prompted, click **Yes**.</span></span>
    
<span data-ttu-id="77852-166">После этого добавьте диска с дополнительных данных как новый том с диска F:, с помощью этой команды в командной строке Windows PowerShell правами администратора на DC1.</span><span class="sxs-lookup"><span data-stu-id="77852-166">Next, add an extra data disk as a new volume with the drive letter F: with this command at an administrator-level Windows PowerShell command prompt on DC1.</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="77852-p111">Затем настройте виртуальную машину DC1 как контроллер домена и DNS-сервер для домена corp.contoso.com. От имени администратора выполните указанные ниже команды в командной строке Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="77852-p111">Next, configure DC1 as a domain controller and DNS server for the corp.contoso.com domain. Run these commands at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName corp.contoso.com -DatabasePath "F:\\NTDS" -SysvolPath "F:\\SYSVOL" -LogPath "F:\\Logs"
```

<span data-ttu-id="77852-p112">Потребуется указать пароль администратора для безопасного режима. Храните этот пароль в надежном месте.</span><span class="sxs-lookup"><span data-stu-id="77852-p112">You will need to specify a safe mode administrator password. Store this password in a secure location.</span></span>
  
<span data-ttu-id="77852-171">Обратите внимание, что на выполнение этих команд может потребоваться несколько минут.</span><span class="sxs-lookup"><span data-stu-id="77852-171">Note that these commands can take a few minutes to complete.</span></span>
  
<span data-ttu-id="77852-172">После перезапуска виртуальной машины DC1 снова подключитесь к ней.</span><span class="sxs-lookup"><span data-stu-id="77852-172">After DC1 restarts, reconnect to the DC1 virtual machine.</span></span>
  
### <a name="connect-to-dc1-using-domain-credentials"></a><span data-ttu-id="77852-173">Подключение к DC1 с помощью учетных данных домена</span><span class="sxs-lookup"><span data-stu-id="77852-173">Connect to DC1 using domain credentials</span></span>

1. <span data-ttu-id="77852-174">В [Azure портала](https://portal.azure.com), нажмите кнопку **группы ресурсов >** <your resource group name> **> DC1 > подключить**.</span><span class="sxs-lookup"><span data-stu-id="77852-174">In the [Azure portal](https://portal.azure.com), click **Resource Groups >** <your resource group name> **> DC1 > Connect**.</span></span>
    
2. <span data-ttu-id="77852-175">Запустите файл DC1.rdp, который будет загружен и нажмите кнопку **Подключить**.</span><span class="sxs-lookup"><span data-stu-id="77852-175">Run the DC1.rdp file that is downloaded, and then click **Connect**.</span></span>
    
3. <span data-ttu-id="77852-p113">В системе **Безопасности Windows**выберите **использовать другую учетную запись**. В поле **имя пользователя**введите **CORP\\**[имя учетной записи локального администратора].</span><span class="sxs-lookup"><span data-stu-id="77852-p113">In **Windows Security**, click **Use another account**. In **User name**, type **CORP\\**[Local administrator account name].</span></span>
    
4. <span data-ttu-id="77852-178">В поле **пароль**введите пароль учетной записи локального администратора и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="77852-178">In **Password**, type the password of the local administrator account, and then click **OK**.</span></span>
    
5. <span data-ttu-id="77852-179">При появлении запроса нажмите кнопку **Да**.</span><span class="sxs-lookup"><span data-stu-id="77852-179">When prompted, click **Yes**.</span></span>
    
<span data-ttu-id="77852-p114">Затем создайте учетную запись пользователя в Active Directory, которая будет использоваться при входе в систему на компьютерах, входящих в домен CORP. От имени администратора выполните указанную ниже команду в командной строке Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="77852-p114">Next, create a user account in Active Directory that will be used when logging in to CORP domain member computers. Run this command at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
New-ADUser -SamAccountName User1 -AccountPassword (read-host "Set user password" -assecurestring) -name "User1" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

<span data-ttu-id="77852-p115">Обратите внимание на то, что при выполнении этой команды вам будет предложено ввести пароль учетной записи User1. Так как эта учетная запись будет использоваться для подключения к удаленному рабочему столу для всех компьютеров, входящих в домен CORP, используйте надежный пароль. Запишите пароль к учетной записи User1 и храните его в безопасном месте.</span><span class="sxs-lookup"><span data-stu-id="77852-p115">Note that this command prompts you to supply the User1 account password. Because this account will be used for remote desktop connections for all CORP domain member computers, choose a strong password. Record the User1 account password and store it in a secured location.</span></span>
  
<span data-ttu-id="77852-p116">Затем настройте новую учетную запись User1 как учетную запись администратора предприятия. От имени администратора выполните указанную ниже команду в командной строке Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="77852-p116">Next, configure the new User1 account as an Enterprise Administrator. Run this command at the administrator-level Windows PowerShell command prompt.</span></span>
  
```
Add-ADPrincipalGroupMembership -Identity "CN=User1,CN=Users,DC=corp,DC=contoso,DC=com" -MemberOf "CN=Enterprise Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Domain Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Schema Admins,CN=Users,DC=corp,DC=contoso,DC=com"
```

<span data-ttu-id="77852-187">Закрыть сеанс удаленного рабочего стола с DC1 и затем снова подключить с помощью CORP\\учетной записи User1.</span><span class="sxs-lookup"><span data-stu-id="77852-187">Close the Remote Desktop session with DC1 and then reconnect using the CORP\\User1 account.</span></span>
  
<span data-ttu-id="77852-188">Чтобы разрешить трафик для средства Ping, выполните указанную ниже команду в командной строке Windows PowerShell от имени администратора.</span><span class="sxs-lookup"><span data-stu-id="77852-188">Next, to allow traffic for the Ping tool, run this command at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
```

<span data-ttu-id="77852-189">Это — ваша текущая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="77852-189">This is your current configuration.</span></span>
  
![Этап 2. Базовая конфигурация в Azure, включающая виртуальную машину DC1](images/49069908-29c3-4d73-87f7-debbea067261.png)
  
## <a name="phase-3-configure-app1"></a><span data-ttu-id="77852-191">Этап 3. Настройка APP1</span><span class="sxs-lookup"><span data-stu-id="77852-191">Phase 3: Configure APP1</span></span>

<span data-ttu-id="77852-192">APP1 предоставляет веб-службы и службы общего доступа к файлам.</span><span class="sxs-lookup"><span data-stu-id="77852-192">APP1 provides web and file sharing services.</span></span>
  
<span data-ttu-id="77852-193">Чтобы создать виртуальную машину Azure для APP1, укажите имя группы ресурсов, расположение Azure и имя учетной записи хранения. Затем выполните указанные ниже команды в командной строке Azure PowerShell на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="77852-193">To create an Azure Virtual Machine for APP1, fill in the name of your resource group, Azure location, and storage account name and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name APP1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name APP1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName APP1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for APP1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName APP1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "APP1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="77852-194">После этого подключитесь к виртуальной машине APP1, используя имя и пароль для учетной записи локального администратора APP1. Затем откройте командную строку Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="77852-194">Next, connect to the APP1 virtual machine using the APP1 local administrator account name and password, and then open a Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="77852-195">Чтобы проверить имя разрешения и сети обмена данными между APP1 и DC1, выполните команду **ping dc1.corp.contoso.com** и убедитесь, что существует четыре ответа.</span><span class="sxs-lookup"><span data-stu-id="77852-195">To check name resolution and network communication between APP1 and DC1, run the **ping dc1.corp.contoso.com** command and verify that there are four replies.</span></span>
  
<span data-ttu-id="77852-196">Затем присоедините виртуальную машину APP1 к домену CORP, выполнив указанные ниже команды в командной строке Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="77852-196">Next, join the APP1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

<span data-ttu-id="77852-197">Обратите внимание, что необходимо задать CORP\\учетные данные учетной записи User1 домена после выполнения команды **Добавить компьютер** .</span><span class="sxs-lookup"><span data-stu-id="77852-197">Note that you must supply the CORP\\User1 domain account credentials after running the **Add-Computer** command.</span></span>
  
<span data-ttu-id="77852-198">После перезагрузки APP1 подключиться к ней с помощью CORP\\учетной записи User1, а затем откройте Windows PowerShell администраторские командную строку.</span><span class="sxs-lookup"><span data-stu-id="77852-198">After APP1 restarts, connect to it using the CORP\\User1 account, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="77852-199">После этого сделайте APP1 веб-сервером, выполнив указанную ниже команду в командной строке Windows PowerShell в APP1.</span><span class="sxs-lookup"><span data-stu-id="77852-199">Next, make APP1 a web server with this command at the Windows PowerShell command prompt on APP1.</span></span>
  
```
Install-WindowsFeature Web-WebServer -IncludeManagementTools
```

<span data-ttu-id="77852-200">Создайте общую папку и текстовый файл в папке на APP1 с помощью указанных ниже команд PowerShell.</span><span class="sxs-lookup"><span data-stu-id="77852-200">Next, create a shared folder and a text file within the folder on APP1 with these PowerShell commands.</span></span>
  
```
New-Item -path c:\\files -type directory
Write-Output "This is a shared file." | out-file c:\\files\\example.txt
New-SmbShare -name files -path c:\\files -changeaccess CORP\\User1
```

<span data-ttu-id="77852-201">Это — ваша текущая конфигурация.</span><span class="sxs-lookup"><span data-stu-id="77852-201">This is your current configuration.</span></span>
  
![Этап 3. Базовая конфигурация в Azure, включающая виртуальную машину APP1](images/92cfabb0-7f9d-4291-964d-ac32d52748d7.png)
  
## <a name="phase-4-configure-client1"></a><span data-ttu-id="77852-203">Этап 4. Настройка CLIENT1</span><span class="sxs-lookup"><span data-stu-id="77852-203">Phase 4: Configure CLIENT1</span></span>

<span data-ttu-id="77852-204">CLIENT1 действует как типичный ноутбук, планшет или компьютер в интрасети Contoso.</span><span class="sxs-lookup"><span data-stu-id="77852-204">CLIENT1 acts as a typical laptop, tablet, or desktop computer on the Contoso intranet.</span></span>
  
> [!NOTE]
> <span data-ttu-id="77852-p117">Следующие команды set создает CLIENT1 под управлением Windows Server 2016 центра обработки данных, который может выполняться для всех типов Azure подписок. Если у вас есть подписка Azure на основе Visual Studio, можно создать CLIENT1 выполняемого-Windows 10, Windows 8 или Windows 7 с [Azure портала](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="77852-p117">The following command set creates CLIENT1 running Windows Server 2016 Datacenter, which can be done for all types of Azure subscriptions. If you have an Visual Studio-based Azure subscription, you can create CLIENT1 running Windows 10, Windows 8, or Windows 7 with the [Azure portal](https://portal.azure.com).</span></span> 
  
<span data-ttu-id="77852-207">Чтобы создать виртуальную машину Azure для CLIENT1, укажите имя группы ресурсов, расположение Azure и имя учетной записи хранения. Затем выполните указанные ниже команды в командной строке Azure PowerShell на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="77852-207">To create an Azure Virtual Machine for CLIENT1, fill in the name of your resource group, Azure location, and storage account name and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name CLIENT1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name CLIENT1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName CLIENT1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for CLIENT1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName CLIENT1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "CLIENT1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="77852-208">После этого подключитесь к виртуальной машине CLIENT1, используя имя и пароль для учетной записи локального администратора CLIENT1. Затем откройте командную строку Windows PowerShell от имени администратора.</span><span class="sxs-lookup"><span data-stu-id="77852-208">Next, connect to the CLIENT1 virtual machine using the CLIENT1 local administrator account name and password, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="77852-209">Чтобы проверить имя разрешения и сети обмена данными между CLIENT1 и DC1, выполните команду **ping dc1.corp.contoso.com** в командной строке Windows PowerShell и убедитесь, что существует четыре ответа.</span><span class="sxs-lookup"><span data-stu-id="77852-209">To check name resolution and network communication between CLIENT1 and DC1, run the **ping dc1.corp.contoso.com** command at a Windows PowerShell command prompt and verify that there are four replies.</span></span>
  
<span data-ttu-id="77852-210">Затем присоедините виртуальную машину CLIENT1 к домену CORP, выполнив указанные ниже команды в командной строке Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="77852-210">Next, join the CLIENT1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

<span data-ttu-id="77852-211">Обратите внимание, что необходимо предоставить вашей CORP\\учетные данные учетной записи User1 домена после выполнения команды **Добавить компьютер** .</span><span class="sxs-lookup"><span data-stu-id="77852-211">Note that you must supply your CORP\\User1 domain account credentials after running the **Add-Computer** command.</span></span>
  
<span data-ttu-id="77852-212">После перезагрузки компьютера CLIENT1, подключиться к ней с помощью CORP\\User1 учетной записи имя и пароль, а затем откройте командную строку Windows PowerShell уровня администратора.</span><span class="sxs-lookup"><span data-stu-id="77852-212">After CLIENT1 restarts, connect to it using the CORP\\User1 account name and password, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="77852-213">Затем убедитесь, что у CLIENT1 есть доступ к веб-ресурсам и общим файловым ресурсам на виртуальной машине APP1.</span><span class="sxs-lookup"><span data-stu-id="77852-213">Next, verify that you can access web and file share resources on APP1 from CLIENT1.</span></span>
  
### <a name="verify-client-access-to-app1"></a><span data-ttu-id="77852-214">Проверка возможности доступа к APP1 для CLIENT1</span><span class="sxs-lookup"><span data-stu-id="77852-214">Verify CLIENT access to APP1</span></span>

1. <span data-ttu-id="77852-215">В диспетчере сервера в древовидном представлении щелкните **Локального сервера**.</span><span class="sxs-lookup"><span data-stu-id="77852-215">In Server Manager, in the tree pane, click **Local Server**.</span></span>
    
2. <span data-ttu-id="77852-216">В окне **свойств для CLIENT1**щелкните **на** рядом с пунктом **Конфигурация усиленной безопасности обозревателя IE**.</span><span class="sxs-lookup"><span data-stu-id="77852-216">In **Properties for CLIENT1**, click **On** next to **IE Enhanced Security Configuration**.</span></span>
    
3. <span data-ttu-id="77852-217">В разделе **Конфигурация усиленной безопасности Internet Explorer**нажмите кнопку **Отключить** для **администраторов** и **пользователей**и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="77852-217">In **Internet Explorer Enhanced Security Configuration**, click **Off** for **Administrators** and **Users**, and then click **OK**.</span></span>
    
4. <span data-ttu-id="77852-218">На начальном экране выберите пункт **Internet Explorer**и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="77852-218">From the Start screen, click **Internet Explorer**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="77852-p118">В адресной строке введите **http://app1.corp.contoso.com/**и нажмите клавишу ВВОД. Вы увидите веб-страницу по умолчанию службы IIS для APP1.</span><span class="sxs-lookup"><span data-stu-id="77852-p118">In the Address bar, type **http://app1.corp.contoso.com/**, and then press ENTER. You should see the default Internet Information Services web page for APP1.</span></span>
    
6. <span data-ttu-id="77852-221">Щелкните значок проводника на панели задач рабочего стола.</span><span class="sxs-lookup"><span data-stu-id="77852-221">From the desktop taskbar, click the File Explorer icon.</span></span>
    
7. <span data-ttu-id="77852-p119">В адресной строке введите ** \\ \\app1\\файлы**, а затем нажмите клавишу ВВОД. Вы должны увидеть окне папки с содержимым в общую папку файлов.</span><span class="sxs-lookup"><span data-stu-id="77852-p119">In the address bar, type **\\\\app1\\Files**, and then press ENTER. You should see a folder window with the contents of the Files shared folder.</span></span>
    
8. <span data-ttu-id="77852-p120">В окне общую папку **файлов** дважды щелкните файл **Example.txt** . Вы должны увидеть содержимое файла Example.txt.</span><span class="sxs-lookup"><span data-stu-id="77852-p120">In the **Files** shared folder window, double-click the **Example.txt** file. You should see the contents of the Example.txt file.</span></span>
    
9. <span data-ttu-id="77852-226">Закройте **example.txt - Блокнот** и windows **файлы** общих папок.</span><span class="sxs-lookup"><span data-stu-id="77852-226">Close the **example.txt - Notepad** and the **Files** shared folder windows.</span></span>
    
<span data-ttu-id="77852-227">Это — ваша окончательная конфигурация.</span><span class="sxs-lookup"><span data-stu-id="77852-227">This is your final configuration.</span></span>
  
![Этап 4. Базовая конфигурация в Azure, включающая виртуальную машину CLIENT1](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
<span data-ttu-id="77852-229">Теперь ваша базовая конфигурация в Azure готова к разработке и тестированию приложений, а также к созданию дополнительных тестовых сред.</span><span class="sxs-lookup"><span data-stu-id="77852-229">Your Base Configuration in Azure is now ready for application development and testing or for building additional test environments.</span></span> 
  
> [!TIP]
> <span data-ttu-id="77852-230">Щелкните [здесь](http://aka.ms/catlgstack) для visual карты для всех статей в стеке один Microsoft Cloud руководство по лаборатории тестирования.</span><span class="sxs-lookup"><span data-stu-id="77852-230">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="minimizing-the-costs-of-test-environment-virtual-machines-in-azure"></a><span data-ttu-id="77852-231">Минимизация расходов на виртуальные машины в тестовой среде в Azure</span><span class="sxs-lookup"><span data-stu-id="77852-231">Minimizing the costs of test environment virtual machines in Azure</span></span>
<span data-ttu-id="77852-232"><a name="mincost"> </a></span><span class="sxs-lookup"><span data-stu-id="77852-232"></span></span>

<span data-ttu-id="77852-233">Чтобы снизить затраты на работу виртуальных машин тестовой среды, можно выполнить одно из указанных ниже действий.</span><span class="sxs-lookup"><span data-stu-id="77852-233">To minimize the cost of running the test environment virtual machines, you can do one of the following:</span></span>
  
- <span data-ttu-id="77852-p121">Создайте тестовую среду и проведите необходимое тестирование и демонстрацию как можно скорее. После завершения удалите группу ресурсов для тестовой среды.</span><span class="sxs-lookup"><span data-stu-id="77852-p121">Create the test environment and perform your needed testing and demonstration as quickly as possible. When complete, delete the resource group for the test environment.</span></span>
    
- <span data-ttu-id="77852-236">	Завершите работу виртуальных машин своей тестовой среды, приведя их в освобожденное состояние.</span><span class="sxs-lookup"><span data-stu-id="77852-236">Shut down your test environment virtual machines into a deallocated state.</span></span>
    
<span data-ttu-id="77852-237">Чтобы завершить работу виртуальных машин с помощью Azure PowerShell, введите имя группы ресурсов и выполните указанные ниже команды.</span><span class="sxs-lookup"><span data-stu-id="77852-237">To shut down the virtual machines with Azure PowerShell, fill in the resource group name and run these commands.</span></span>
  
```
$rgName="<your resource group name>"
Stop-AzureRMVM -ResourceGroupName $rgName -Name "CLIENT1" -Force
Stop-AzureRMVM -ResourceGroupName $rgName -Name "APP1" -Force
Stop-AzureRMVM -ResourceGroupName $rgName -Name "DC1" -Force
```

<span data-ttu-id="77852-238">Чтобы виртуальные машины, находящиеся в остановленном (освобожденном) состоянии, работали должным образом после запуска и вывода их из этого состояния, запускайте их в следующем порядке:</span><span class="sxs-lookup"><span data-stu-id="77852-238">To ensure that your virtual machines work properly when starting all of them from the Stopped (Deallocated) state, you should start them in the following order:</span></span>
  
1. <span data-ttu-id="77852-239">DC1</span><span class="sxs-lookup"><span data-stu-id="77852-239">DC1</span></span>
    
2. <span data-ttu-id="77852-240">APP1</span><span class="sxs-lookup"><span data-stu-id="77852-240">APP1</span></span>
    
3. <span data-ttu-id="77852-241">CLIENT1</span><span class="sxs-lookup"><span data-stu-id="77852-241">CLIENT1</span></span>
    
<span data-ttu-id="77852-242">Чтобы запустить виртуальные машины по порядку с помощью Azure PowerShell, введите имя группы ресурсов и выполните указанные ниже команды.</span><span class="sxs-lookup"><span data-stu-id="77852-242">To start the virtual machines in order with Azure PowerShell, fill in the resource group name and run these commands.</span></span>
  
```
$rgName="<your resource group name>"
Start-AzureRMVM -ResourceGroupName $rgName -Name "DC1"
Start-AzureRMVM -ResourceGroupName $rgName -Name "APP1"
Start-AzureRMVM -ResourceGroupName $rgName -Name "CLIENT1"
```

## <a name="see-also"></a><span data-ttu-id="77852-243">See Also</span><span class="sxs-lookup"><span data-stu-id="77852-243">See Also</span></span>

<span data-ttu-id="77852-244"><a name="mincost"> </a></span><span class="sxs-lookup"><span data-stu-id="77852-244"></span></span>

[<span data-ttu-id="77852-245">Среда разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="77852-245">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="77852-246">DirSync для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="77852-246">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="77852-247">Облако безопасности приложения для Office 365 dev/тестовой среды</span><span class="sxs-lookup"><span data-stu-id="77852-247">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="77852-248">Дополнительные защиту от угроз для вашей среды разработки или тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="77852-248">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="77852-249">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="77852-249">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


