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
# <a name="high-availability-federated-authentication-phase-1-configure-azure"></a>Этап 1. Федеративная проверка подлинности для обеспечения высокой доступности: настройка Azure

 **Сводка:** Настройка инфраструктуры Microsoft Azure для использования проверки подлинности федеративные высокой доступности узла для Office 365.
  
На этом этапе создается группы ресурсов, хранилище учетных записей, виртуальные сети (VNet) и доступность наборы в Azure, в котором будет размещаться виртуальных машин в этапы 2, 3 и 4. Необходимо выполнить данный этап перед перемещением на [высокой доступности федеративных проверки подлинности этап 2: Настройка контроллеров домена](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). В разделе [Развертывание высокой доступности федеративной проверки подлинности для Office 365 в Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) все этапы.
  
Необходимо быть, подготовленные в Azure с помощью следующих основных компонентов:
  
- Группы ресурсов
    
- Нелокальная виртуальная сеть Azure с подсетями для размещения виртуальных машин Azure
    
- Группы безопасности сети для изоляции подсети
    
- Группы доступности
    
## <a name="configure-azure-components"></a>Настройка компонентов Azure

Перед началом настройки Azure компонентов, заполните поля в следующих таблицах. Для помощи в процедуры для настройки Azure, печать в этом разделе запишите требуемые данные или скопируйте в этом разделе документа и его можно заполнить. Для параметров VNet заполните поля в таблице V.
  
|**Элемент**|**Параметр конфигурации**|**Описание**|**Значение**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Имя виртуальной сети  <br/> |Имя виртуальной сети (например, FedAuthNet).  <br/> |_______________________________  <br/> |
|2.  <br/> |Расположение VNet  <br/> |Региональный центр обработки данных Azure, в котором будет расположена виртуальная сеть.  <br/> |_______________________________  <br/> |
|3.  <br/> |IP-адрес VPN-устройства  <br/> |Общедоступный IPv4-адрес интерфейса VPN-устройства в Интернете.  <br/> |_______________________________  <br/> |
|4.  <br/> |Адресное пространство виртуальной сети  <br/> |Адресное пространство виртуальной сети. Чтобы определить это адресное пространство, обратитесь в ИТ-отдел.  <br/> |_______________________________  <br/> |
|5.  <br/> |Общий ключ IPsec  <br/> |32 символов в случайном порядке, буквенно-цифровой строка, которая будет использоваться для проверки подлинности обеих сторон VPN-подключения веб сайта. Работа с ИТ или отдела безопасности для определения это значение ключа. Кроме того в разделе [Создать строку в случайном порядке для предварительного ключа IPsec](http://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).<br/> |_______________________________  <br/> |
   
 **Таблица V. Настройка распределенной виртуальной сети**
  
После этого укажите подсети этого решения в таблице S. Все адресные пространства должны быть указаны в формате CIDR (формате префиксов сети). Пример: 10.24.64.0/20.
  
Для первых трех подсетей укажите имя и одно пространство IP-адресов на основе адресного пространства виртуальной сети. Для подсети шлюза определите 27-битовое адресное пространство (с длиной префикса /27) для подсети шлюза Azure шлюза. Для этого выполните следующие действия:
  
1. Для переменных битов в адресном пространстве виртуальной сети задайте значение 1 (не больше бит, используемых подсетью шлюза), а для остальных битов задайте значение 0.
    
2. Преобразуйте результат в десятичное число и выразите его как адресное пространство, длина префикса которого соответствует размеру подсети шлюза.
    
В разделе [Калькулятор пространства адресов для подсетей Azure шлюза](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) блок команд PowerShell и C# или Python консольное приложение, используемая для выполнения этого вычисления для вас.
  
Чтобы определить эти адресные пространства из адресного пространства виртуальной сети, обратитесь в ИТ-отдел.
  
|**Элемент**|**Имя подсети**|**Адресное пространство подсети**|**Назначение**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |_______________________________  <br/> |_______________________________  <br/> |Подсеть, используемая контроллером домена Active Directory (AD) Windows Server и виртуальными машинами сервера DirSync.  <br/> |
|2.  <br/> |_______________________________  <br/> |_______________________________  <br/> |Подсеть, используемая виртуальными машинами AD FS.  <br/> |
|3.  <br/> |_______________________________  <br/> |_______________________________  <br/> |Подсеть, используемая виртуальными машинами прокси-серверов веб-приложений.  <br/> |
|4.  <br/> |GatewaySubnet  <br/> |_______________________________  <br/> |Подсеть, используемая виртуальными машинами шлюза Azure.  <br/> |
   
 **Таблица S. Подсети виртуальной сети**
  
После этого укажите статические IP-адреса, назначенные виртуальным машинам и экземплярам балансировщика нагрузки, в таблице I.
  
|**Элемент**|**Назначение**|**IP-адрес в подсети**|**Значение**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Статический IP-адрес первого контроллера домена  <br/> |Четвертый возможный IP-адрес для адресного пространства подсети, определенной в элементе 1 таблицы S.  <br/> |_______________________________  <br/> |
|2.  <br/> |Статический IP-адрес второго контроллера домена  <br/> |Пятый возможный IP-адрес адресного пространства подсети, определенной в элементе 1 таблицы S.  <br/> |_______________________________  <br/> |
|3.  <br/> |Статический IP-адрес сервера DirSync  <br/> |Шестой возможный IP-адрес адресного пространства подсети, определенной в элементе 1 таблицы S.  <br/> |_______________________________  <br/> |
|4.  <br/> |Статический IP-адрес внутреннего балансировщика нагрузки для серверов AD FS  <br/> |Четвертый возможный IP-адрес для адресного пространства подсети, определенный в элементе 2 таблицы S.  <br/> |_______________________________  <br/> |
|5.  <br/> |Статический IP-адрес первого сервера AD FS  <br/> |Пятый возможный IP-адрес адресного пространства подсети, определенной в элементе 2 таблицы S.  <br/> |_______________________________  <br/> |
|6.  <br/> |Статический IP-адрес второго сервера AD FS  <br/> |Шестой возможный IP-адрес адресного пространства подсети, определенной в элементе 2 таблицы S.  <br/> |_______________________________  <br/> |
|7.  <br/> |Статический IP-адрес первого прокси-сервера веб-приложений  <br/> |Четвертый возможный IP-адрес для адресного пространства подсети, определенный в элементе 3 таблицы S.  <br/> |_______________________________  <br/> |
|8.  <br/> |Статический IP-адрес второго прокси-сервера веб-приложений  <br/> |Пятый возможный IP-адрес адресного пространства подсети, определенной в элементе 3 таблицы S.  <br/> |_______________________________  <br/> |
   
 **В таблице по созданию статических IP-адресов в виртуальной сети**
  
В таблице D укажите два DNS-сервера в локальной сети, которые необходимо использовать при начальной настройке контроллеров домена в виртуальной сети. Чтобы определить этот список, обратитесь в ИТ-отдел.
  
|**Элемент**|**Понятное имя DNS-сервера**|**IP-адрес DNS-сервера**|
|:-----|:-----|:-----|
|1.  <br/> |_______________________________  <br/> |_______________________________  <br/> |
|2.  <br/> |_______________________________  <br/> |_______________________________  <br/> |
   
 **Таблица D. Локальные DNS-сервера**
  
Чтобы отправлять пакеты из нелокальной сети в сеть организации с помощью VPN-подключения типа "сеть-сеть", необходимо настроить виртуальную сеть с локальной сетью, которая содержит список адресных пространств (в формате CIDR) для всех доступных расположений в локальной сети организации. Список адресных пространств, которые определяют локальную сеть, должен быть уникален и не должен пересекаться с адресным пространством, используемым для других виртуальных или локальных сетей.
  
Укажите список адресных пространств локальной сети в таблице L. Обратите внимание, что представлено три пустых поля, но обычно требуется больше. Определите этот список адресных пространств при поддержке ИТ-отдела.
  
|**Элемент**|**Адресное пространство локальной сети**|
|:-----|:-----|
|1.  <br/> |_______________________________  <br/> |
|2.  <br/> |_______________________________  <br/> |
|3.  <br/> |_______________________________  <br/> |
   
 **Таблица L. Префиксы адресов для локальной сети**
  
Теперь приступим к созданию инфраструктуры Azure для размещения федеративной проверки подлинности для Office 365.
  
> [!NOTE]
> Следующие наборы команд использовать последнюю версию Windows Azure PowerShell. В разделе [Начало работы с Windows Azure PowerShell командлетов](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/). 
  
Запустите командную строку Azure PowerShell и войдите в свою учетную запись.
  
```
Login-AzureRMAccount
```

> [!TIP]
> Текстовый файл, содержащий все команды PowerShell в данной статье и конфигурации книги Microsoft Excel, которое создает все готово к запуску PowerShell команду блоки на основе настраиваемых параметров содержатся в [федеративном проверки подлинности для Office 365 Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664). 
  
Получите имя подписки с помощью следующей команды.
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

Для предыдущих версий Windows Azure PowerShell используйте следующую команду.
  
```
Get-AzureRMSubscription | Sort Name | Select SubscriptionName
```

Задайте подпиской Azure. Замените все содержимое в кавычки, включая \< и > символов с правильным именем.
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

После этого создайте новые группы ресурсов. Чтобы задать уникальные имена, отобразите уже существующие группы ресурсов с помощью указанной команды.
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Укажите уникальные имена групп ресурсов в следующей таблице.
  
|**Элемент**|**Имя группы ресурсов**|**Назначение**|
|:-----|:-----|:-----|
|1.  <br/> |_______________________________  <br/> |Контроллеры доменов  <br/> |
|2.  <br/> |_______________________________  <br/> |Серверы AD FS  <br/> |
|3.  <br/> |_______________________________  <br/> |Прокси-серверы веб-приложений  <br/> |
|4.  <br/> |_______________________________  <br/> |Элементы инфраструктуры  <br/> |
   
 **В таблице центральный группы ресурсов**
  
Создайте новые группы ресурсов с помощью этих команд.
  
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

Затем создайте виртуальную сеть Azure и подсети.
  
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

Создайте сеть группы безопасности для каждой подсети, которая содержит виртуальных машин. Для выполнения изоляции подсети, можно добавить правила для определенных типов трафика запрещен в группу безопасности сети подсети, или.
  
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

Затем используйте следующие команды, чтобы создать шлюзы для VPN-подключения типа "сеть-сеть".
  
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
> Федеративная проверка подлинности пользователей, не зависит от любого локальным ресурсам. Тем не менее недоступность VPN-подключения веб сайта контроллеры доменов в VNet не будут получать обновления для учетных записей пользователей и групп, выполненных в Windows на локальный сервер AD. Чтобы убедиться, что это не происходит, можно настроить высокой доступности для VPN-подключение к веб сайта. Для получения дополнительных сведений см [сильно доступные между организациями и связи с VNet-VNet](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)
  
После этого запишите общедоступный IPv4-адрес VPN-шлюза Azure для виртуальной сети из результата этой команды:
  
```
Get-AzureRMPublicIpAddress -Name $publicGatewayVipName -ResourceGroupName $rgName
```

Настройте устройство VPN локальной для подключения к виртуальной частной сети Azure шлюза. Дополнительные сведения в статье [Configure VPN-устройства](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
  
Чтобы настроить локальное VPN-устройство, вам потребуется следующее:
  
- Общедоступный IPv4-адрес VPN-шлюза Azure.
    
- Предварительный ключ IPsec для VPN-подключения веб сайта (столбец таблицы V - элемента 5 - значение).
    
Убедитесь, что адресное пространство виртуальной сети доступно из локальной сети. Для этого добавьте маршрут, соответствующий адресному пространству виртуальной сети на вашем VPN-устройстве и сообщите этот маршрут остальной инфраструктуре маршрутизации в сети организации. Чтобы определить, как это сделать, обратитесь в ИТ-отдел.
  
После этого определите имена четырех групп доступности. Заполните таблицу A. 
  
|**Элемент**|**Назначение**|**Имя набора доступности**|
|:-----|:-----|:-----|
|1.  <br/> |Контроллеры доменов  <br/> |_______________________________  <br/> |
|2.  <br/> |Серверы AD FS  <br/> |_______________________________  <br/> |
|3.  <br/> |Прокси-серверы веб-приложений  <br/> |_______________________________  <br/> |
   
 **Задает доступность ответ: таблицы**
  
Вам потребуются эти имена при создании виртуальных машин на этапах 2, 3 и 4.
  
Создайте новые группы доступности с помощью этих команд Azure PowerShell.
  
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

Ниже показана конфигурация, полученная в результате успешного выполнения этого этапа.
  
**Этап 1: Azure инфраструктуры для обеспечения высокой доступности федеративной проверки подлинности для Office 365**

![Этап 1. Федеративная проверка подлинности для Office 365 с высокой доступностью, развертывание которой выполняется в Azure с использованием инфраструктуры Azure](images/4e7ba678-07df-40ce-b372-021bf7fc91fa.png)
  
## <a name="next-step"></a>Следующее действие

Использование [высокой доступности федеративных проверки подлинности этап 2: Настройка контроллеров домена](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) чтобы продолжить работу конфигурации этой рабочей нагрузкой.
  
## <a name="see-also"></a>See Also

[Развертывание в Azure федеративной проверки подлинности для обеспечения высокой доступности в случае использования Office 365](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[Федеративное удостоверение для среды разработки и тестирования Office 365](federated-identity-for-your-office-365-dev-test-environment.md)
  
[Освоение облака и гибридные решения](cloud-adoption-and-hybrid-solutions.md)

[Федеративные удостоверения для Office 365](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)

