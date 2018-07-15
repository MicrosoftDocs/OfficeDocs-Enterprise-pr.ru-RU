---
title: Этап 2 Настройка контроллеров домена для проверки подлинности федеративные высокой доступности
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/09/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 6b0eff4c-2c5e-4581-8393-a36f7b36a72f
description: Сводка. Настройка контроллеров домена и сервера DirSync для федеративной проверки подлинности с высоким уровнем доступности для Office 365 в Microsoft Azure.
ms.openlocfilehash: 3f898fea8fc92d4f7ea392bfe854425beafb1eb4
ms.sourcegitcommit: 3a4ab28f3f4172d596426f0da40bcab8c46ef74d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2018
ms.locfileid: "20215871"
---
# <a name="high-availability-federated-authentication-phase-2-configure-domain-controllers"></a><span data-ttu-id="09f8e-103">Этап 2. Федеративная проверка подлинности для обеспечения высокой доступности: настройка контроллеров домена</span><span class="sxs-lookup"><span data-stu-id="09f8e-103">High availability federated authentication Phase 2: Configure domain controllers</span></span>

 <span data-ttu-id="09f8e-104">**Сводка.** Настройка контроллеров домена и сервера DirSync для федеративной проверки подлинности с высоким уровнем доступности для Office 365 в Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="09f8e-104">**Summary:** Configure the domain controllers and DirSync server for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
  
<span data-ttu-id="09f8e-p101">На этом этапе развертывания федеративной проверки подлинности с высоким уровнем доступности для Office 365 в службах инфраструктуры Azure настраиваются два контроллера домена и сервер DirSync в виртуальной сети Azure. После этого проверку подлинности клиентов можно выполнять в виртуальной сети Azure, не отправляя трафик проверки подлинности через подключение VPN типа "сеть-сеть" к локальной сети.</span><span class="sxs-lookup"><span data-stu-id="09f8e-p101">In this phase of deploying high availability for Office 365 federated authentication in Azure infrastructure services, you configure two domain controllers and the DirSync server in the Azure virtual network. Client web requests for authentication can then be authenticated in the Azure virtual network, rather than sending that authentication traffic across the site-to-site VPN connection to your on-premises network.</span></span>
  
> [!NOTE]
> <span data-ttu-id="09f8e-107">В службах федерации Active Directory (AD FS) нельзя использовать доменные службы Azure Active Directory вместо контроллеров домена AD Windows Server.</span><span class="sxs-lookup"><span data-stu-id="09f8e-107">Active Directory Federation Services (AD FS) cannot use Azure Active Directory Domain Services as a substitute for Windows Server AD domain controllers.</span></span> 
  
<span data-ttu-id="09f8e-p102">Необходимо выполнить данный этап перед перемещением на [высокой доступности федеративных проверки подлинности этап 3: настройте серверы AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). В разделе [Развертывание высокой доступности федеративной проверки подлинности для Office 365 в Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) все этапы.</span><span class="sxs-lookup"><span data-stu-id="09f8e-p102">You must complete this phase before moving on to [High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-domain-controller-virtual-machines-in-azure"></a><span data-ttu-id="09f8e-110">Создание виртуальных машин контроллеров домена в Azure</span><span class="sxs-lookup"><span data-stu-id="09f8e-110">Create the domain controller virtual machines in Azure</span></span>

<span data-ttu-id="09f8e-111">Для начала необходимо заполнить столбец **Имя виртуальной машины** в таблице M и при необходимости изменить размеры виртуальных машин в столбце **Минимальный размер**.</span><span class="sxs-lookup"><span data-stu-id="09f8e-111">First, you need to fill out the **Virtual machine name** column of Table M and modify virtual machine sizes as needed in the **Minimum size** column.</span></span>
  
|<span data-ttu-id="09f8e-112">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="09f8e-112">**Item**</span></span>|<span data-ttu-id="09f8e-113">**Имя виртуальной машины**</span><span class="sxs-lookup"><span data-stu-id="09f8e-113">**Virtual machine name**</span></span>|<span data-ttu-id="09f8e-114">**Образ коллекции**</span><span class="sxs-lookup"><span data-stu-id="09f8e-114">**Gallery image**</span></span>|<span data-ttu-id="09f8e-115">**Тип хранилища**</span><span class="sxs-lookup"><span data-stu-id="09f8e-115">**Storage type**</span></span>|<span data-ttu-id="09f8e-116">**Минимальный размер**</span><span class="sxs-lookup"><span data-stu-id="09f8e-116">**Minimum size**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="09f8e-117">1.</span><span class="sxs-lookup"><span data-stu-id="09f8e-117">1.</span></span>  <br/> |<span data-ttu-id="09f8e-118">![](./images/Common_Images/TableLine.png) (первый контроллер домена, например DC1)</span><span class="sxs-lookup"><span data-stu-id="09f8e-118">![](./images/Common_Images/TableLine.png) (first domain controller, example DC1)</span></span>  <br/> |<span data-ttu-id="09f8e-119">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="09f8e-119">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="09f8e-120">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="09f8e-120">Standard_LRS</span></span>  <br/> |<span data-ttu-id="09f8e-121">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="09f8e-121">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="09f8e-122">2.</span><span class="sxs-lookup"><span data-stu-id="09f8e-122">2.</span></span>  <br/> |<span data-ttu-id="09f8e-123">![](./images/Common_Images/TableLine.png) (второй контроллер домена, например DC2)</span><span class="sxs-lookup"><span data-stu-id="09f8e-123">![](./images/Common_Images/TableLine.png) (second domain controller, example DC2)</span></span>  <br/> |<span data-ttu-id="09f8e-124">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="09f8e-124">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="09f8e-125">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="09f8e-125">Standard_LRS</span></span>  <br/> |<span data-ttu-id="09f8e-126">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="09f8e-126">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="09f8e-127">3.</span><span class="sxs-lookup"><span data-stu-id="09f8e-127">3.</span></span>  <br/> |<span data-ttu-id="09f8e-128">![](./images/Common_Images/TableLine.png)(Сервер синхронизации каталогов, пример DS1)</span><span class="sxs-lookup"><span data-stu-id="09f8e-128">![](./images/Common_Images/TableLine.png) (DirSync server, example DS1)</span></span>  <br/> |<span data-ttu-id="09f8e-129">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="09f8e-129">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="09f8e-130">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="09f8e-130">Standard_LRS</span></span>  <br/> |<span data-ttu-id="09f8e-131">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="09f8e-131">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="09f8e-132">4.</span><span class="sxs-lookup"><span data-stu-id="09f8e-132">4.</span></span>  <br/> |<span data-ttu-id="09f8e-133">![](./images/Common_Images/TableLine.png)(первого сервера AD FS, пример ADFS1)</span><span class="sxs-lookup"><span data-stu-id="09f8e-133">![](./images/Common_Images/TableLine.png) (first AD FS server, example ADFS1)</span></span>  <br/> |<span data-ttu-id="09f8e-134">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="09f8e-134">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="09f8e-135">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="09f8e-135">Standard_LRS</span></span>  <br/> |<span data-ttu-id="09f8e-136">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="09f8e-136">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="09f8e-137">5.</span><span class="sxs-lookup"><span data-stu-id="09f8e-137">5.</span></span>  <br/> |<span data-ttu-id="09f8e-138">![](./images/Common_Images/TableLine.png)(второго сервера AD FS, пример ADFS2)</span><span class="sxs-lookup"><span data-stu-id="09f8e-138">![](./images/Common_Images/TableLine.png) (second AD FS server, example ADFS2)</span></span>  <br/> |<span data-ttu-id="09f8e-139">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="09f8e-139">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="09f8e-140">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="09f8e-140">Standard_LRS</span></span>  <br/> |<span data-ttu-id="09f8e-141">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="09f8e-141">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="09f8e-142">6.</span><span class="sxs-lookup"><span data-stu-id="09f8e-142">6.</span></span>  <br/> |<span data-ttu-id="09f8e-143">![](./images/Common_Images/TableLine.png)(первый сервер веб-приложения прокси, пример WEB1)</span><span class="sxs-lookup"><span data-stu-id="09f8e-143">![](./images/Common_Images/TableLine.png) (first web application proxy server, example WEB1)</span></span>  <br/> |<span data-ttu-id="09f8e-144">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="09f8e-144">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="09f8e-145">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="09f8e-145">Standard_LRS</span></span>  <br/> |<span data-ttu-id="09f8e-146">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="09f8e-146">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="09f8e-147">7.</span><span class="sxs-lookup"><span data-stu-id="09f8e-147">7.</span></span>  <br/> |<span data-ttu-id="09f8e-148">![](./images/Common_Images/TableLine.png)(второй веб-прокси сервер приложений, пример WEB2)</span><span class="sxs-lookup"><span data-stu-id="09f8e-148">![](./images/Common_Images/TableLine.png) (second web application proxy server, example WEB2)</span></span>  <br/> |<span data-ttu-id="09f8e-149">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="09f8e-149">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="09f8e-150">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="09f8e-150">Standard_LRS</span></span>  <br/> |<span data-ttu-id="09f8e-151">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="09f8e-151">Standard_D2</span></span>  <br/> |
   
 <span data-ttu-id="09f8e-152">**В таблице M - виртуальных машин для проверки подлинности федеративные высокой доступности для Office 365 в Azure**</span><span class="sxs-lookup"><span data-stu-id="09f8e-152">**Table M - Virtual machines for the high availability federated authentication for Office 365 in Azure**</span></span>
  
<span data-ttu-id="09f8e-153">Полный список размеров виртуальных машин представлен в [этой статье](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes).</span><span class="sxs-lookup"><span data-stu-id="09f8e-153">For the complete list of virtual machine sizes, see [Sizes for virtual machines](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes).</span></span>
  
<span data-ttu-id="09f8e-p103">Следующий блок Azure PowerShell команда создает виртуальных машин для два контроллера домена. Укажите значения для переменных, удаление \< и > символов. Обратите внимание, что этот блок Azure PowerShell команда использует значениями, полученными из следующей таблицы:</span><span class="sxs-lookup"><span data-stu-id="09f8e-p103">The following Azure PowerShell command block creates the virtual machines for the two domain controllers. Specify the values for the variables, removing the \< and > characters. Note that this Azure PowerShell command block uses values from the following tables:</span></span>
  
- <span data-ttu-id="09f8e-157">таблица M (для виртуальных машин);</span><span class="sxs-lookup"><span data-stu-id="09f8e-157">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="09f8e-158">таблица R (для групп ресурсов);</span><span class="sxs-lookup"><span data-stu-id="09f8e-158">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="09f8e-159">таблица V (для параметров виртуальной сети);</span><span class="sxs-lookup"><span data-stu-id="09f8e-159">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="09f8e-160">таблица S (для подсетей);</span><span class="sxs-lookup"><span data-stu-id="09f8e-160">Table S, for your subnets</span></span>
    
- <span data-ttu-id="09f8e-161">таблица I (для статических IP-адресов);</span><span class="sxs-lookup"><span data-stu-id="09f8e-161">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="09f8e-162">таблица A (для групп доступности).</span><span class="sxs-lookup"><span data-stu-id="09f8e-162">Table A, for your availability sets</span></span>
    
<span data-ttu-id="09f8e-163">Помните, что вы задали таблицы R, V, S, I и A в [высокой доступности федеративных проверки подлинности этап 1: Настройка Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span><span class="sxs-lookup"><span data-stu-id="09f8e-163">Recall that you defined Tables R, V, S, I, and A in [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="09f8e-p104">Для приведенных ниже последовательностей команд используется последняя версия Azure PowerShell. См. статью [Общие сведения об Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="09f8e-p104">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="09f8e-166">Указав правильные значения, выполните полученный блок в командной строке Azure PowerShell или в интегрированной среде сценариев PowerShell (ISE) на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="09f8e-166">When you have supplied all the correct values, run the resulting block at the Azure PowerShell prompt or in the PowerShell Integrated Script Environment (ISE) on your local computer.</span></span>
  
> [!TIP]
> <span data-ttu-id="09f8e-167">Текстовый файл, содержащий все команды PowerShell в данной статье и конфигурации книги Microsoft Excel, которое создает все готово к запуску PowerShell команду блоки на основе настраиваемых параметров содержатся в [федеративном проверки подлинности для Office 365 Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span><span class="sxs-lookup"><span data-stu-id="09f8e-167">For a text file that contains all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
  
```
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table S - Item 1 - Value column>"
$avName="<Table A - Item 1 - Availability set name column>"
$rgNameTier="<Table R - Item 1 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$rgName=$rgNameTier
$avSet=Get-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName 

# Create the first domain controller
$vmName="<Table M - Item 1 - Virtual machine name column>"
$vmSize="<Table M - Item 1 - Minimum size column>"
$staticIP="<Table I - Item 1 - Value column>"
$diskStorageType="<Table M - Item 1 - Storage type column>"
$diskSize=<size of the extra disk for Windows Server AD data in GB>

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzureRmDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzureRmDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first domain controller." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second domain controller
$vmName="<Table M - Item 2 - Virtual machine name column>"
$vmSize="<Table M - Item 2 - Minimum size column>"
$staticIP="<Table I - Item 2 - Value column>"
$diskStorageType="<Table M - Item 2 - Storage type column>"
$diskSize=<size of the extra disk for Windows Server AD data in GB>

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzureRmDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzureRmDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second domain controller." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the DirSync server
$vmName="<Table M - Item 3 - Virtual machine name column>"
$vmSize="<Table M - Item 3 - Minimum size column>"
$staticIP="<Table I - Item 3 - Value column>"
$diskStorageType="<Table M - Item 3 - Storage type column>"

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the DirSync server." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="09f8e-p105">Так как эти виртуальные машины для приложения интрасети, они не назначен общедоступный IP-адрес или имя домена DNS и выход в Интернет. Тем не менее это также означает, что не удается подключиться к ним с Azure портала. Параметр **Подключить** недоступна при просмотре свойств виртуальной машины. Используйте стандартную программу подключения к удаленному рабочему столу или другого средства удаленного рабочего стола для подключения к виртуальной машине с помощью его частных IP-адресов интрасети или адреса DNS-имени.</span><span class="sxs-lookup"><span data-stu-id="09f8e-p105">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span></span>
  
## <a name="configure-the-first-domain-controller"></a><span data-ttu-id="09f8e-172">Настройка первого контроллера домена</span><span class="sxs-lookup"><span data-stu-id="09f8e-172">Configure the first domain controller</span></span>

<span data-ttu-id="09f8e-p106">Используя любой клиент удаленного рабочего стола, создайте подключение к удаленному рабочему столу для виртуальной машины первого контроллера домена. Используйте DNS-имя интрасети или имя компьютера, а также учетные данные локального администратора.</span><span class="sxs-lookup"><span data-stu-id="09f8e-p106">Use the remote desktop client of your choice and create a remote desktop connection to the first domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="09f8e-175">Добавьте на диске дополнительных данных для первого контроллера домена с помощью этой команды из Windows PowerShell командной строки **на виртуальной машине первого контроллера домена**:</span><span class="sxs-lookup"><span data-stu-id="09f8e-175">Next, add the extra data disk to the first domain controller with this command from a Windows PowerShell command prompt **on the first domain controller virtual machine**:</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="09f8e-176">Затем протестируйте соединение первого контроллера домена с расположениями в сети организации с помощью команды **ping** для имен и IP-адресов ресурсов в этой сети.</span><span class="sxs-lookup"><span data-stu-id="09f8e-176">Next, test the first domain controller's connectivity to locations on your organization network by using the **ping** command to ping names and IP addresses of resources on your organization network.</span></span>
  
<span data-ttu-id="09f8e-p107">Это позволяет убедиться, что разрешение DNS-имен работает надлежащим образом (виртуальная машина правильно настроена с указанием локальных DNS-серверов), а в распределенную виртуальную сеть и из нее можно отправлять пакеты. В случае сбоя базового теста обратитесь в ИТ-отдел для устранения проблем с разрешением DNS-имен и доставкой пакетов.</span><span class="sxs-lookup"><span data-stu-id="09f8e-p107">This procedure ensures that DNS name resolution is working correctly (that the virtual machine is correctly configured with on-premises DNS servers) and that packets can be sent to and from the cross-premises virtual network. If this basic test fails, contact your IT department to troubleshoot the DNS name resolution and packet delivery issues.</span></span>
  
<span data-ttu-id="09f8e-179">Затем в командной строке Windows PowerShell на первом контроллере домена выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="09f8e-179">Next, from the Windows PowerShell command prompt on the first domain controller, run the following commands:</span></span>
  
```
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred
```

<span data-ttu-id="09f8e-p108">Вам будет предложено указать учетные данные администратора домена. Компьютер перезагрузится.</span><span class="sxs-lookup"><span data-stu-id="09f8e-p108">You will be prompted to supply the credentials of a domain administrator account. The computer will restart.</span></span>
  
## <a name="configure-the-second-domain-controller"></a><span data-ttu-id="09f8e-182">Настройка второго контроллера домена</span><span class="sxs-lookup"><span data-stu-id="09f8e-182">Configure the second domain controller</span></span>

<span data-ttu-id="09f8e-p109">Используя любой клиент удаленного рабочего стола, создайте подключение к удаленному рабочему столу на виртуальной машине второго контроллера домена. Используйте DNS-имя интрасети или имя компьютера, а также учетные данные локального администратора.</span><span class="sxs-lookup"><span data-stu-id="09f8e-p109">Use the remote desktop client of your choice and create a remote desktop connection to the second domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="09f8e-185">Затем необходимо добавить дополнительные данные в второго контроллера домена с помощью этой команды из Windows PowerShell командной строки **на виртуальной машине второго контроллера домена**:</span><span class="sxs-lookup"><span data-stu-id="09f8e-185">Next, you need to add the extra data disk to the second domain controller with this command from a Windows PowerShell command prompt **on the second domain controller virtual machine**:</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="09f8e-186">Затем выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="09f8e-186">Next, run the following commands:</span></span>
  
```
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred

```

<span data-ttu-id="09f8e-p110">Вам будет предложено указать учетные данные администратора домена. Компьютер перезагрузится.</span><span class="sxs-lookup"><span data-stu-id="09f8e-p110">You will be prompted to supply the credentials of a domain administrator account. The computer will restart.</span></span>
  
<span data-ttu-id="09f8e-p111">Затем необходимо обновить DNS-серверов для виртуальной сети, так что Azure назначает виртуальных машин IP-адреса двух новых контроллеров домена для использования в качестве DNS-серверов. Заполните поля в переменные и затем выполните следующие команды в командной строке Windows PowerShell на локальном компьютере:</span><span class="sxs-lookup"><span data-stu-id="09f8e-p111">Next, you need to update the DNS servers for your virtual network so that Azure assigns virtual machines the IP addresses of the two new domain controllers to use as their DNS servers. Fill in the variables and then run these commands from a Windows PowerShell command prompt on your local computer:</span></span>
  
```
$rgName="<Table R - Item 4 - Resource group name column>"
$adrgName="<Table R - Item 1 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$onpremDNSIP1="<Table D - Item 1 - DNS server IP address column>"
$onpremDNSIP2="<Table D - Item 2 - DNS server IP address column>"
$staticIP1="<Table I - Item 1 - Value column>"
$staticIP2="<Table I - Item 2 - Value column>"
$firstDCName="<Table M - Item 1 - Virtual machine name column>"
$secondDCName="<Table M - Item 2 - Virtual machine name column>"

$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$vnet.DhcpOptions.DnsServers.Add($staticIP1)
$vnet.DhcpOptions.DnsServers.Add($staticIP2) 
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP1)
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP2) 
Set-AzureRMVirtualNetwork -VirtualNetwork $vnet
Restart-AzureRMVM -ResourceGroupName $adrgName -Name $firstDCName
Restart-AzureRMVM -ResourceGroupName $adrgName -Name $secondDCName
```

<span data-ttu-id="09f8e-p112">Обратите внимание, что мы перезагружаем два контроллера домена, чтобы они не были настроены с указанием локальных DNS-серверов. Так как они оба сами являются DNS-серверами, эти контроллеры были автоматически настроены с указанием локальных DNS-серверов пересылки при повышении до контроллеров домена.</span><span class="sxs-lookup"><span data-stu-id="09f8e-p112">Note that we restart the two domain controllers so that they are not configured with the on-premises DNS servers as DNS servers. Because they are both DNS servers themselves, they were automatically configured with the on-premises DNS servers as DNS forwarders when they were promoted to domain controllers.</span></span>
  
<span data-ttu-id="09f8e-p113">После этого необходимо создать сайт репликации Active Directory, чтобы убедиться, что серверы в виртуальной сети Azure используют локальные контроллеры домена. Подключитесь к любому контроллеру домена, используя учетную запись администратора домена, и выполните следующие команды в командной строке Windows PowerShell с правами администратора:</span><span class="sxs-lookup"><span data-stu-id="09f8e-p113">Next, we need to create an Active Directory replication site to ensure that servers in the Azure virtual network use the local domain controllers. Connect to either domain controller with a domain administrator account and run the following commands from an administrator-level Windows PowerShell prompt:</span></span>
  
```
$vnet="<Table V - Item 1 - Value column>"
$vnetSpace="<Table V - Item 4 - Value column>"
New-ADReplicationSite -Name $vnet 
New-ADReplicationSubnet -Name $vnetSpace -Site $vnet
```

## <a name="configure-the-dirsync-server"></a><span data-ttu-id="09f8e-195">Настройка сервера DirSync</span><span class="sxs-lookup"><span data-stu-id="09f8e-195">Configure the DirSync server</span></span>

<span data-ttu-id="09f8e-p114">Используйте клиента удаленного рабочего стола на свой выбор и создайте виртуальную машину DirSync сервера удаленного рабочего стола. С помощью его интрасети DNS или имя компьютера и учетные данные учетной записи локального администратора.</span><span class="sxs-lookup"><span data-stu-id="09f8e-p114">Use the remote desktop client of your choice and create a remote desktop connection to the DirSync server virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="09f8e-198">После этого настройте соединение с соответствующим доменом Windows Server AD, выполнив указанные ниже команды в командной строке Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="09f8e-198">Next, join it to the appropriate Windows Server AD domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
$domName="<Windows Server AD domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

<span data-ttu-id="09f8e-199">Здесь показана конфигурация, полученная в результате успешного выполнения этого этапа (с заполнителями вместо имен компьютеров).</span><span class="sxs-lookup"><span data-stu-id="09f8e-199">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="09f8e-200">**Этап 2. Контроллеры домена и сервер DirSync для инфраструктуры федеративной проверки подлинности с высоким уровнем доступности в Azure**</span><span class="sxs-lookup"><span data-stu-id="09f8e-200">**Phase 2: The domain controllers and DirSync server for your high availability federated authentication infrastructure in Azure**</span></span>

![Этап 2. Инфраструктура федеративной проверки подлинности для Office 365 с высокой доступностью, развертывание которой выполняется в Azure с использованием контроллеров доменов](images/b0c1013b-3fb4-499e-93c1-bf310d8f4c32.png)
  
## <a name="next-step"></a><span data-ttu-id="09f8e-202">Следующий шаг</span><span class="sxs-lookup"><span data-stu-id="09f8e-202">Next step</span></span>

<span data-ttu-id="09f8e-203">Продолжение здесь: [High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md).</span><span class="sxs-lookup"><span data-stu-id="09f8e-203">Use [High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="09f8e-204">См. также</span><span class="sxs-lookup"><span data-stu-id="09f8e-204">See Also</span></span>

[<span data-ttu-id="09f8e-205">Развертывание в Azure федеративной проверки подлинности для обеспечения высокой доступности в случае использования Office 365</span><span class="sxs-lookup"><span data-stu-id="09f8e-205">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="09f8e-206">Федеративное удостоверение для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="09f8e-206">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="09f8e-207">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="09f8e-207">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="09f8e-208">Федеративные удостоверения для Office 365</span><span class="sxs-lookup"><span data-stu-id="09f8e-208">Federated identity for Office 365</span></span>](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


