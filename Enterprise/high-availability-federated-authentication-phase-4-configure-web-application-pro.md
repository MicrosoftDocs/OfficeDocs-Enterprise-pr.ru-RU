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
ms.openlocfilehash: 276d28835cbedf7d2eb87b80304fbb0e4e9de2c3
ms.sourcegitcommit: 9c9982badeb95b8ecc083609a1a922cbfdfc9609
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "38793321"
---
# <a name="high-availability-federated-authentication-phase-4-configure-web-application-proxies"></a>Этап 4. Федеративная проверка подлинности для обеспечения высокой доступности: настройка прокси веб-приложений

 **Сводка:** Настройка прокси-серверов веб-приложений для федеративной проверки подлинности с высоким уровнем доступности для Office 365 в Microsoft Azure.
  
На этом этапе развертывания федеративной проверки подлинности с высоким уровнем доступности для Office 365 в службах инфраструктуры Azure создаются внутренний балансировщик нагрузки и два сервера AD FS.
  
Необходимо выполнить этот этап перед переходом к [этапу федеративной проверки подлинности высокого уровня доступности 5: Настройка федеративной проверки подлинности для Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Описание всех этапов см. в статье [Развертывание в Azure федеративной проверки подлинности для обеспечения высокой доступности в случае использования Office 365](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).
  
## <a name="create-the-internet-facing-load-balancer-in-azure"></a>Создание подсистемы балансировки сетевой нагрузки в Azure для выхода из Интернета

Необходимо создать подсистему балансировки нагрузки с выходом в Интернет, чтобы Azure перегрузил входящий трафик проверки подлинности клиента из Интернета между двумя серверами прокси-сервера веб-приложений.
  
> [!NOTE]
> Для указанных ниже последовательностей команд используется последняя версия Azure PowerShell. Обратитесь к разделу начало [работы с командлетами Azure PowerShell](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/). 
  
После того как вы задали значения расположения и группы ресурсов, запустите полученный блок в командной строки Azure PowerShell или в ИНТЕГРИРОВАНной среде выполнения PowerShell.
  
```powershell
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

Чтобы отобразить общедоступный IP-адрес, назначенный подсистеме балансировки нагрузки в Интернете, выполните следующие команды в командной строке Azure PowerShell на локальном компьютере:
  
```powershell
Write-Host (Get-AzPublicIpaddress -Name "WebProxyPublicIP" -ResourceGroup $rgName).IPAddress
```

## <a name="determine-your-federation-service-fqdn-and-create-dns-records"></a>Определение полного доменного имени и создание записей DNS для службы федерации

Необходимо определить DNS-имя, чтобы определить имя службы федерации в Интернете. Azure AD Connect настроит Office 365 с этим именем в фазе 5, которая становится частью URL-адреса, который Office 365 отправляет клиентам для получения маркера безопасности. Например, fs.contoso.com (FS означает служба Федерации).
  
После того как вы ФДКН службу федерации, создайте запись A общедоступного домена DNS для службы федерации ФДКН, которая разрешается в общедоступный IP-адрес подсистемы балансировки нагрузки Azure, доступного для выхода в Интернет.
  
|**Имя**|**Тип**|**TTL**|**Значение**|
|:-----|:-----|:-----|:-----|
|Служба федерации ФДКН  <br/> |A  <br/> |3600  <br/> |общедоступный IP-адрес балансировщика нагрузки с выходом в Интернет Azure (отображается с помощью команды **Write-Host** в предыдущем разделе) <br/> |
   
Вот пример:
  
|**Имя**|**Тип**|**TTL**|**Значение**|
|:-----|:-----|:-----|:-----|
|fs.contoso.com  <br/> |A  <br/> |3600  <br/> |131.107.249.117  <br/> |
   
Затем добавьте запись DNS-адреса в личное пространство имен DNS организации, которая разрешает полное доменное имя службы Федерации к частному IP-адресу, назначенному внутреннему подсистеме балансировки нагрузки для серверов AD FS (таблица I, элемент 4, столбец "значение").
  
## <a name="create-the-web-application-proxy-server-virtual-machines-in-azure"></a>Создание виртуальных машин прокси-сервера веб-приложений в Azure

Используйте следующий блок команд Azure PowerShell, чтобы создать виртуальные машины для двух прокси-серверов веб-приложений. 
  
Обратите внимание на то, что следующие наборы команд Azure PowerShell используют значения из следующих таблиц:
  
- таблица M (для виртуальных машин);
    
- таблица R (для групп ресурсов);
    
- таблица V (для параметров виртуальной сети);
    
- таблица S (для подсетей);
    
- таблица I (для статических IP-адресов);
    
- таблица A (для групп доступности).
    
Помните, что вы определили таблицу M на [этапе высокодоступной федеративной проверки подлинности 2: Configure Domain Controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) and Tables R, V, S, I и A [with High Availability Authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).
  
Задав правильные значения, выполните полученный блок в командной строке Azure PowerShell или в интегрированной среде сценариев PowerShell.
  
```powershell
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
> Эти виртуальные машины предназначены для работы в интрасети, поэтому им не назначается общедоступный IP-адрес или метка доменного имени DNS и они не подключаются к Интернету. Однако это также означает, что к ним невозможно подключиться с помощью портала Azure. Команда **Подключиться** недоступна при просмотре свойств виртуальной машины. Используйте подключение к удаленному рабочему столу или другой инструмент удаленного рабочего стола, чтобы подключиться к виртуальной машине, используя свой частный IP-адрес или DNS-имя интрасети, а также учетные данные локальной учетной записи администратора.
  
Здесь показана конфигурация, полученная в результате успешного выполнения этого этапа (с заполнителями вместо имен компьютеров).
  
**Этап 4: подсистема балансировки нагрузки на основе Интернета и прокси-серверы веб-приложений для инфраструктуры федеративной проверки подлинности с высоким уровнем доступности в Azure**

![Этап 4 инфраструктуры федеративной проверки подлинности Office 365 с высоким уровнем доступности в Azure с помощью прокси-серверов веб-приложений](media/7e03183f-3b3b-4cbe-9028-89cc3f195a63.png)
  
## <a name="next-step"></a>Следующее действие

Применение [федеративной проверки подлинности с высоким уровнем доступности этап 5: Настройка федеративной проверки подлинности для Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) для продолжения настройки этой рабочей нагрузки.
  
## <a name="see-also"></a>См. также

[Развертывание в Azure федеративной проверки подлинности для обеспечения высокой доступности в случае использования Office 365](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[Федеративное удостоверение для среды разработки и тестирования Office 365](federated-identity-for-your-office-365-dev-test-environment.md)
  
[Освоение облака и гибридные решения](cloud-adoption-and-hybrid-solutions.md)

