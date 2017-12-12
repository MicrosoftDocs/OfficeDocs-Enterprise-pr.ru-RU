---
title: "Подключение локальной сети к виртуальной сети Microsoft Azure"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 1/13/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
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
---

# Подключение локальной сети к виртуальной сети Microsoft Azure

 **Сводка.** Узнайте, как настроить распределенную виртуальную сеть Azure для рабочих нагрузок Office Server.
  
Виртуальная сеть Azure подключается к вашей локальной сети, расширяя ее за счет подсетей и виртуальных машин, размещенных в службах инфраструктуры Azure. Благодаря этому компьютеры в вашей локальной сети могут подключаться напрямую к виртуальным машинам Azure и наоборот. Например, серверу DirSync, запущенному на виртуальной машине Azure, требуется направить запрос контроллерам локального домена на изменение учетных записей, а также синхронизировать эти изменения с подпиской на Office 365. В этой статье описано, как настроить виртуальную сеть Azure для размещения в ней виртуальных машин Azure.
  
В этой статье
  
- [Общие сведения](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Overview)
    
- [Планирование виртуальной сети Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#PlanningVirtual)
    
- [Схема развертывания](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#DeploymentRoadmap)
    
## Общие сведения
<a name="Overview"> </a>

Виртуальные машины в Azure не должны быть изолированы от локальной среды. Чтобы подключить виртуальные машины Azure к локальным сетевым ресурсам, необходимо настроить виртуальную сеть Azure. На схеме ниже показаны компоненты, необходимые для развертывания виртуальной сети Azure с виртуальной машиной в Azure.
  
![Локальная сеть подключена к Microsoft Azure с помощью VPN-подключения типа "сеть-сеть"](images/CP_ConnectOnPremisesNetworkToAzureVPN.png)
  
На схеме локальная сеть и виртуальная сеть Azure подключены друг к другу с помощью VPN-подключения типа "сеть-сеть". Это подключение прерывается VPN-устройством в локальной сети и VPN-шлюзом Azure в виртуальной сети Azure. В виртуальной сети Azure есть виртуальные машины. Сетевой трафик с виртуальных машин в виртуальной сети Azure направляется на VPN-шлюз, который затем направляет трафик по VPN-подключению типа "сеть-сеть" на VPN-устройство в локальной сети. Далее инфраструктура маршрутизации локальной сети направляет трафик по назначению.
  
Чтобы настроить VPN-подключение между виртуальной сетью Azure и локальной сетью, выполните следующие действия. 
  
1. **Локальная сеть.** Определите и создайте локальный сетевой маршрут для адресного пространства виртуальной сети Azure, который указывает на локальное VPN-устройство.
    
2. **Microsoft Azure.** Создайте виртуальную сеть Azure с VPN-подключением типа "сеть-сеть". В этой статье не описывается использование подключения[ExpressRoute](https://azure.microsoft.com/services/expressroute/).
    
3. **Локальная сеть.** Настройте аппаратное или программное локальное VPN-устройство для прерывания VPN-подключения, которое использует IPsec.
    
После установки VPN-подключения типа "сеть-сеть" добавьте виртуальные машины Azure в подсети виртуальной сети.
  
## Планирование виртуальной сети Azure
<a name="PlanningVirtual"> </a>

### Требования
<a name="Prerequisites"> </a>

- Подписка на Azure. Сведения о подписках на Azure см. на [странице подписки на Microsoft Azure](https://azure.microsoft.com/pricing/purchase-options/).
    
- Доступное частное пространство IPv4-адресов, которое необходимо назначить виртуальной сети и ее подсетям, с достаточным количеством адресов с учетом возможного расширения.
    
- Доступное VPN-устройство в локальной сети для прерывания VPN-подключения типа "сеть-сеть", которое поддерживает требования для IPsec. Дополнительные сведения см. в статье [О VPN-устройствах для подключений VPN-шлюзов типа "сеть-сеть"](https://go.microsoft.com/fwlink/p/?LinkId=393093).
    
- Изменение инфраструктуры маршрутизации для перенаправления трафика, поступающего в адресное пространство виртуальной сети Azure, на VPN-устройство, которое принимает VPN-подключение типа "сеть-сеть".
    
- Веб-прокси, который предоставляет доступ в Интернет компьютерам, подключенным к локальной сети и виртуальной сети Azure.
    
### Допущения по архитектуре решения
<a name="DesignAssumptions"> </a>

Ниже перечислены проектные решения для этой архитектуры.
  
- Это решение использует одну виртуальную сеть Azure с VPN-подключением типа "сеть-сеть". В виртуальной сети Azure размещается одна подсеть, которая может содержать несколько виртуальных машин. 
    
- Вы можете использовать службу RRAS в Windows Server 2016 или Windows Server 2012, чтобы установить VPN-подключение типа "сеть-сеть" с защитой IPsec между локальной сетью и виртуальной сетью Azure. Вы также можете использовать другие VPN-устройства, например Cisco или Juniper Networks.
    
- В локальной сети по-прежнему могут размещаться сетевые службы, такие как Windows Server Active Directory (AD), служба доменных имен (DNS), и прокси-серверы. В зависимости от ваших требований, некоторые из этих сетевых ресурсов может быть удобнее разместить в виртуальной сети Azure.
    
Для существующей виртуальной сети Azure с одной или несколькими подсетями определите, осталось ли адресное пространство для дополнительной подсети и размещения необходимых виртуальных машин, учитывая ваши требования. Если адресного пространства для дополнительной подсети не осталось, создайте дополнительную виртуальную сеть с собственным VPN-подключением типа "сеть-сеть".
  
### Планирование изменения инфраструктуры маршрутизации для виртуальной сети Azure
<a name="routing"> </a>

Локальную инфраструктуру маршрутизации необходимо настроить так, чтобы трафик, поступающий в пространство адресов виртуальной сети Azure, направлялся в локальное VPN-устройство с VPN-подключением типа "сеть-сеть".
  
Конкретный метод обновления инфраструктуры маршрутизации зависит от того, как выполняется управление сведениями о маршрутизации, например:
  
- таблица маршрутизации обновляется в соответствии с ручной настройкой;
    
- таблица маршрутизации обновляется в соответствии с протоколами маршрутизации, например RIP или OSPF.
    
Проконсультируйтесь со своим специалистом по маршрутизации, чтобы убедиться, что трафик, предназначенный для виртуальной сети Azure, перенаправляется на локальное VPN-устройство.
  
### Планирование правил брандмауэра для входящего и исходящего трафика на локальном VPN-устройстве
<a name="firewall"> </a>

Если VPN-устройство размещается в сети периметра, которая соединяется с Интернетом через брандмауэр, рекомендуем настроить на брандмауэре перечисленные ниже правила, чтобы сделать возможным VPN-подключение типа "сеть-сеть".
  
- Трафик к VPN-устройству (входящий):
    
  - Конечный IP-адрес VPN-устройства и протокол IP 50
    
  - Конечный IP-адрес VPN-устройства и конечный порт UDP 500
    
  - Конечный IP-адрес VPN-устройства и конечный порт UDP 4500
    
- Трафик с VPN-устройства (исходящий):
    
  - Исходный IP-адрес VPN-устройства и протокол IP 50
    
  - Исходный IP-адрес VPN-устройства и исходный порт UDP 500
    
  - Исходный IP-адрес VPN-устройства и исходный порт UDP 4500
    
### Планирование пространства частных IP-адресов виртуальной сети Azure
<a name="IPAddresses"> </a>

Пространство частных IP-адресов виртуальной сети Azure должно иметь достаточный размер для адресов, используемых платформой Azure для размещения виртуальной сети как минимум с одной подсетью, в которой достаточно адресов для размещения виртуальных машин Azure.
  
Чтобы определить необходимое количество адресов для подсети, посчитайте количество виртуальных машин, необходимых на данный момент, оцените потенциал роста и определите размер подсети, пользуясь следующей таблицей.
  
|**Необходимое количество виртуальных машин**|**Необходимое количество бит узла**|**Размер подсети**|
|:-----|:-----|:-----|
|1-3  <br/> |3  <br/> |/29  <br/> |
|4-11  <br/> |4  <br/> |/28  <br/> |
|12-27  <br/> |5  <br/> |/27  <br/> |
|28-59  <br/> |6  <br/> |/26  <br/> |
|60-123  <br/> |7  <br/> |/25  <br/> |
   
### Таблица планирования настройки виртуальной сети Azure
<a name="worksheet"> </a>

Прежде чем создавать виртуальную сеть Azure для размещения виртуальных машин, необходимо определить нужные параметры в следующих таблицах.
  
Чтобы задать параметры виртуальной сети, заполните таблицу V.
  
 **Таблица V. Настройка распределенной виртуальной сети**
  
|**Элемент**|**Элемент Configuration**|**Описание**|**Значение**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Имя виртуальной сети  <br/> |Имя, назначаемое виртуальной сети Azure (например, DirSyncNet).  <br/> |__________________  <br/> |
|2.  <br/> |Расположение виртуальной сети  <br/> |Центр обработки данных Azure, в котором будет расположена виртуальная сеть (например, Запад США).  <br/> |__________________  <br/> |
|3.  <br/> |IP-адрес VPN-устройства  <br/> |Общедоступный IPv4-адрес интерфейса VPN-устройства в Интернете. Определите этот адрес при поддержке ИТ-отдела.  <br/> |__________________  <br/> |
|4.  <br/> |Адресное пространство виртуальной сети  <br/> |Адресное пространство (определенное в одном префиксе личного адреса) для виртуальной сети. Определите это адресное пространство при поддержке ИТ-отдела. Оно должно быть представлено в формате CIDR, также известном как формат префикса сети. Пример: 10.24.64.0/20.  <br/> |__________________  <br/> |
|5.  <br/> |Общий ключ IPsec  <br/> |32-значный случайный буквенно-цифровой ключ, который будет использоваться для проверки подлинности обеих сторон VPN-подключения. Определите значение этого ключа при поддержке ИТ-отдела, а затем сохраните его в надежном месте. Вы также можете ознакомиться со статьей [Создание случайной строки для предварительного ключа IPsec](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  <br/> |__________________  <br/> |
   
Заполните таблицу S для подсетей этого решения.
  
- Для первой подсети определите 28-битовое адресное пространство (с длиной префикса /28) подсети шлюза Azure. Сведения о том, как определить это адресное пространство, см. в статье [Расчет адресного пространства подсетей шлюза для виртуальных сетей Azure](https://blogs.technet.microsoft.com/solutions_advisory_board/2016/12/01/calculating-the-gateway-subnet-address-space-for-azure-virtual-networks/).
    
- Для второй подсети укажите понятное имя, одно пространство IP-адресов на основе адресного пространства виртуальной сети.
    
Определите эти адресные пространства из адресного пространства виртуальной сети при поддержке ИТ-отдела. Оба адресных пространства должны быть представлены в формате CIDR.
  
 **Таблица S. Подсети виртуальной сети**
  
|**Элемент**|**Имя подсети**|**Адресное пространство подсети**|**Назначение**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |GatewaySubnet  <br/> |_____________________________  <br/> |Подсеть, используемая шлюзом Azure.  <br/> |
|2.  <br/> |_____________________________  <br/> |_____________________________  <br/> |_____________________________  <br/> |
   
Для локальных DNS-серверов, используемых виртуальными машинами в виртуальной сети, заполните таблицу D. Присвойте каждому DNS-серверу понятное имя и один IP-адрес. Это понятное имя необязательно должно совпадать с именем узла или именем компьютера на DNS-сервере. Обратите внимание, что представлено два пустых поля, но вы можете добавить еще. Определите этот список при поддержке ИТ-отдела.
  
 **Таблица D. Локальные DNS-сервера**
  
|**Элемент**|**Понятное имя DNS-сервера**|**IP-адрес DNS-сервера**|
|:-----|:-----|:-----|
|1.  <br/> |_____________________________  <br/> |_____________________________  <br/> |
|2.  <br/> |_____________________________  <br/> |_____________________________  <br/> |
   
Чтобы отправлять пакеты из виртуальной сети Azure в сеть организации с помощью VPN-подключения типа "сеть-сеть", необходимо настроить виртуальную сеть с локальной сетью. Эта локальная сеть содержит список адресных пространств (в формате CIDR) для всех расположений в локальной сети организации, которые должны быть доступны виртуальным машинам в виртуальной сети. Это могут быть все расположения в локальной сети или подсети. Список адресных пространств, которые определяют локальную сеть, должен быть уникален и не должен пересекаться с адресными пространствами, используемыми для этой или других виртуальных сетей.
  
Укажите список адресных пространств локальной сети в таблице L. Обратите внимание, что представлено три пустых поля, но обычно требуется больше. Определите этот список при поддержке ИТ-отдела.
  
 **Таблица L. Префиксы адресов для локальной сети**
  
|**Элемент**|**Адресное пространство локальной сети**|
|:-----|:-----|
|1.  <br/> |_____________________________  <br/> |
|2.  <br/> |_____________________________  <br/> |
|3.  <br/> |_____________________________  <br/> |
   
## Схема развертывания
<a name="DeploymentRoadmap"> </a>

Создание виртуальной сети и добавление виртуальных машин в Azure состоит из трех этапов:
  
- Этап 1. Подготовка локальной сети.
    
- Этап 2. Создание виртуальной сети в Azure.
    
- Этап 3 (необязательный). Добавление виртуальных машин.
    
### Этап 1. Подготовка локальной сети
<a name="Phase1"> </a>

В локальной сети необходимо настроить маршрут, который указывает на маршрутизатор на границе локальной сети и направляет на него трафик, предназначенный для адресного пространства виртуальной сети. Обратитесь к администратору сети, чтобы определить, как добавить маршрут в инфраструктуру локальной сети.
  
Ниже показана итоговая конфигурация.
  
![Локальная сеть должна иметь маршрут для адресного пространства виртуальной сети, указывающий на VPN-устройство.](images/90bab36b-cb60-4ea5-81d5-4737b696d41c.png)
  
### Этап 2. Создание распределенной виртуальной сети в Azure
<a name="Phase2"> </a>

Сначала откройте командную строку Azure PowerShell. Если вы еще не установили Azure PowerShell, просмотрите статью [Начало работы с командлетами Azure PowerShell](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/).
  
> [!NOTE]
> Эти команды предназначены для Azure PowerShell 1.0 и более поздних версий. Скачать текстовый файл, который содержит все команды PowerShell, указанные в этой статье, можно [здесь](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-commands-for-5c5a7c19). 
  
Затем войдите в свою учетную запись Azure с помощью следующей команды.
  
```
Login-AzureRMAccount
```

Получите имя подписки с помощью следующей команды.
  
```
Get-AzureRMSubscription | Sort SubscriptionName | Select SubscriptionName
```

Задайте свою подписку Azure с помощью этих команд. Замените весь текст в кавычках, в том числе символы "<" и ">", правильными именами подписок.
  
```
$subscrName="<subscription name>"
Select-AzureRMSubscription -SubscriptionName $subscrName -Current
```

Затем создайте группу ресурсов для виртуальной сети. Чтобы определить уникальное имя группы ресурсов, используйте следующую команду для вывода списка имеющихся групп ресурсов.
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Создайте группу ресурсов с помощью следующих команд.
  
```
$rgName="<resource group name>"
$locName="<Table V - Item 2 - Value column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName

```

Виртуальным машинам на основе диспетчера ресурсов требуется соответствующая учетная запись хранения. Для учетной записи хранения необходимо выбрать глобально уникальное имя, которое содержит только буквы нижнего регистра и цифры. Чтобы вывести на экран список имеющихся учетных записей хранения, можно использовать следующую команду.
  
```
Get-AzureRMStorageAccount | Sort Name | Select Name
```

Чтобы проверить, уникально ли предложенное имя учетной записи хранения, воспользуйтесь приведенной ниже командой.
  
```
Get-AzureRmStorageAccountNameAvailability "<proposed name>"
```

Чтобы создать учетную запись хранения, выполните следующие команды.
  
```
$rgName="<your new resource group name>"
$locName="<the location of your new resource group>"
$saName="<unique storage account name>"
New-AzureRMStorageAccount -Name $saName -ResourceGroupName $rgName -Type Standard_LRS -Location $locName
```

Затем необходимо создать виртуальную сеть Azure.
  
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

Ниже показана итоговая конфигурация.
  
![Виртуальная сеть пока не подключена к локальной.](images/54a37782-a6cc-4d48-b38d-73e128b44a82.png)
  
Затем используйте следующие команды, чтобы создать шлюзы для VPN-подключения типа "сеть-сеть".
  
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

Ниже показана итоговая конфигурация.
  
![Для виртуальной сети теперь настроен шлюз.](images/82dd66b2-a4b7-48f6-a89b-cfdd94630980.png)
  
Затем настройте локальное VPN-устройство для подключения к VPN-шлюзу Azure. Дополнительные сведения см. в статье [О VPN-устройствах для подключений VPN-шлюзов типа "сеть-сеть"](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
  
Чтобы настроить VPN-устройство, вам потребуется следующее:
  
- Общедоступный IPv4-адрес VPN-шлюза Azure для виртуальной сети. Чтобы вывести этот адрес на экран, используйте команду **Get-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName**.
    
- Общий ключ IPsec для VPN-подключения типа "сеть-сеть" (таблица V, элемент 5, столбец "Значение").
    
Ниже показана итоговая конфигурация.
  
![Теперь виртуальная сеть подключена к локальной.](images/6379c423-4f22-4453-941b-7ff32484a0a5.png)
  
### Этап 3 (необязательный). Добавление виртуальных машин
<a name="Phase2"> </a>

Создайте необходимые виртуальные машины в Azure. Дополнительные сведения см. в статье [Создание первой виртуальной машины Windows на портале Azure](https://go.microsoft.com/fwlink/p/?LinkId=393098).
  
Используйте следующие параметры:
  
- В области **Основные** выберите ту же подписку и группу ресурсов, что и в виртуальной сети. Запишите имя пользователя и пароль в надежном месте. Они потребуются позже для входа на виртуальной машине.
    
- В области **Размер** выберите подходящий размер.
    
- В области **Параметры** в разделе **Хранилище** выберите тип хранилища **Стандартный** и учетную запись хранения, настроенную для вашей виртуальной сети. В разделе **Сеть** выберите имя виртуальной сети и подсеть для размещения виртуальных машин (не GatewaySubnet). Для всех остальных параметров оставьте значения по умолчанию.
    
Проверьте внутренний DNS, чтобы убедиться, что виртуальная машина правильно использует DNS и для виртуальной машины добавлены адресные записи (A). Чтобы предоставить виртуальным машинам Azure доступ к Интернету, их необходимо настроить на использование прокси-сервера локальной сети. Обратитесь к администратору сети за дополнительными инструкциями по настройке сервера.
  
Ниже показана итоговая конфигурация.
  
![В виртуальной сети теперь размещены виртуальные машины, доступные из локальной сети.](images/86ab63a6-bfae-4f75-8470-bd40dff123ac.png)
  
## See Also
<a name="DeploymentRoadmap"> </a>

#### 

[Освоение облака и гибридные решения](cloud-adoption-and-hybrid-solutions.md)
  
[Развертывание службы синхронизации каталогов Office 365 (DirSync) в Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md)
#### 

[Создание виртуальной машины Windows на портале Azure](https://go.microsoft.com/fwlink/p/?LinkId=393098)
  
[О VPN-устройствах для подключений VPN-шлюзов типа "сеть-сеть"](https://azure.microsoft.com/documentation/articles/vpn-gateway-about-vpn-devices/)
  
[Установка и настройка Azure PowerShell](https://azure.microsoft.com/documentation/articles/powershell-install-configure/#how-to-install-azure-powershell)

