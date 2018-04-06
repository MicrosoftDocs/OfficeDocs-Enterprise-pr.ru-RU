---
title: Базовая конфигурация среды разработки и тестирования
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/05/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Strat_O365_Enterprise
- Ent_TLGs
ms.assetid: 6fcbb50c-ac68-4be7-9fc5-dd0f275c1e3d
description: 'Сводка: Создание упрощенный интрасети в среде разработки или тестирования в Microsoft Azure.'
ms.openlocfilehash: b2bd1c7bb2b0cd100326867fc3603b6afb6cd8db
ms.sourcegitcommit: 1db536d09343bdf6b4eb695ab07890164c047bd3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="base-configuration-devtest-environment"></a>Базовая конфигурация среды разработки и тестирования

 **Сводка:** Создайте упрощенный интрасети в качестве среды разработки или тестирования в Microsoft Azure.
  
Эта статья содержит пошаговые инструкции по созданию среды разработки и тестирования с базовой конфигурацией в Azure.
  
**На рисунке 1: Среде разработки и тестирования базовой конфигурации**

![Этап 4. Базовая конфигурация в Azure, включающая виртуальную машину CLIENT1](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
Среда разработки и тестирования базовой конфигурации на рисунке 1 состоит из корпоративной сети подсети в только в облаке Azure виртуальную сеть с именем лаборатория тестирования, которая моделирует простая и частной интрасети, подключенных к Интернету. Он содержит три виртуальных машин Azure:
  
- DC1 настроена в качестве контроллера домена интрасети и сервера доменных имен (DNS).
    
- APP1 настроена в качестве общего сервера приложений и веб-сервера.
    
- 	CLIENT1 действует как клиент интрасети.
    
Вот что обеспечивает такая конфигурация для виртуальных машин DC1, APP1, CLIENT1 и дополнительных компьютеров корпоративной подсети:  
  
- Подключение к Интернету для установки обновлений, доступ к ресурсам Интернета в режиме реального времени и участвовать в общедоступное облако технологии, такие как Microsoft Office 365 и других служб Azure.
    
- 	Управление при помощи подключения к удаленному рабочему столу с компьютера, соединенного с Интернетом или сетью организации.
    
Цели использования получившейся тестовой среды:
  
- Разработка и тестирование приложений.
    
- Как начальной настройке среды расширенного теста проекта, который включает в себя дополнительных виртуальных машин, служб Azure или другие предложения облачных Microsoft, такие как Office 365 и безопасности предприятия + мобильных устройств (Командной).
    
Существует четыре этапа настройки тестовой среды с базовой конфигурацией в Azure:
  
1. создание виртуальной сети;
    
2. 	настройка DC1;
    
3. 	настройка APP1;
    
4. 	настройка CLIENT1.
    
Если вы уже нет Azure подписки, можно Зарегистрируйтесь бесплатную пробную версию в [Попробуйте Azure](https://azure.microsoft.com/pricing/free-trial/). Если у вас есть подписка на MSDN или Visual Studio, видеть [кредит ежемесячный Azure для подписчиков Visual Studio](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).
  
> [!NOTE]
> Виртуальных машин в Azure требует текущие расходы на денежные они выполняются. Расходы на этом международные с подпиской MSDN бесплатную пробную, или оплата за подписку. Дополнительные сведения о стоимости под управлением виртуальных машин Azure просмотрите [Сведения о ценах виртуальных машин](https://azure.microsoft.com/pricing/details/virtual-machines/) и [Калькулятор цен Azure](https://azure.microsoft.com/pricing/calculator/). Чтобы сократить издержки, обратитесь к разделу [сокращение расходов на тестовой среды виртуальных машин в Azure](base-configuration-dev-test-environment.md#mincost). 
  
![Руководства по лаборатории тестирования в Microsoft Cloud](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования в One Microsoft Cloud.
  
## <a name="phase-1-create-the-virtual-network"></a>Этап 1. Создание виртуальной сети

Сначала запустите командную строку Azure PowerShell.
  
> [!NOTE]
> Следующие наборы команд использовать последнюю версию Windows Azure PowerShell. В разделе [Начало работы с Windows Azure PowerShell командлетов](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/). 
  
Войдите в свою учетную запись Azure с помощью указанной ниже команды.
  
```
Login-AzureRMAccount
```

> [!TIP]
> Щелкните [здесь](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d) для получения текстовый файл, содержащий все команды PowerShell в данной статье.
  
Получите имя подписки с помощью следующей команды.
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

Укажите свою подписку Azure. Замените текст в кавычках, в том числе символы "<" и ">", на правильное имя.
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

Затем создайте группу ресурсов для лаборатории тестирования с базовой конфигурацией. Чтобы определить уникальное имя группы ресурсов, используйте указанную ниже команду для вывода списка имеющихся групп ресурсов.
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Создайте группу ресурсов с помощью приведенных ниже команд. Замените все символы в кавычках (в том числе символы "<" и ">") правильными именами.
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

Затем создайте виртуальную сеть TestLab, в которой будет размещена корпоративная подсеть базовой конфигурации, и защитите ее с помощью группы безопасности сети.
  
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

Это — ваша текущая конфигурация.
  
![Этап 1. Базовая конфигурация в Azure, включающая виртуальную сеть и подсеть](images/0b5634fc-4e1c-469d-873d-97ed7e587411.png)
  
## <a name="phase-2-configure-dc1"></a>Этап 2. Настройка DC1

На этом этапе мы создадим виртуальную машину DC1 и настроим ее как контроллер для домена Windows Server Active Directory corp.contoso.com и DNS-сервер для виртуальных машин сети TestLab.
  
Чтобы создать Azure виртуальной машины для DC1, заполните поля имя группы ресурсов и выполните следующие команды в командной строке Windows Azure PowerShell на локальном компьютере.
  
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

Вам будет предложено ввести имя пользователя и пароль учетной записи локального администратора на DC1. Задайте надежный пароль и запишите его вместе с именем пользователя в безопасном месте.
  
После этого подключитесь к виртуальной машине DC1.
  
### <a name="connect-to-dc1-using-local-administrator-account-credentials"></a>Подключение к DC1 с помощью учетных данных учетной записи локального администратора

1. В [Azure портала](https://portal.azure.com), нажмите кнопку **группы ресурсов >** [имя новой группы ресурсов] **> DC1 > подключить**.
    
2. Откройте файл DC1.rdp, который будет загружен и нажмите кнопку **Подключить**.
    
3. Укажите имя учетной записи локального администратора DC1.
    
  - Для Windows 7:
    
    В диалоговом окне **Безопасности Windows** выберите **использовать другую учетную запись**. В поле **имя пользователя**введите **DC1\\**[имя учетной записи локального администратора].
    
  - Для Windows 8 или Windows 10:
    
    В диалоговом окне **Безопасности Windows** нажмите кнопку **Дополнительные параметры**и нажмите кнопку **использовать другую учетную запись**. В поле **имя пользователя**введите **DC1\\**[имя учетной записи локального администратора].
    
4. В поле **пароль**введите пароль учетной записи локального администратора и нажмите кнопку **ОК**.
    
5. При появлении запроса нажмите кнопку **Да**.
    
После этого добавьте диска с дополнительных данных как новый том с диска F:, с помощью этой команды в командной строке Windows PowerShell правами администратора на DC1.
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Затем настройте виртуальную машину DC1 как контроллер домена и DNS-сервер для домена corp.contoso.com. От имени администратора выполните указанные ниже команды в командной строке Windows PowerShell.
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName corp.contoso.com -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs"
```

Потребуется указать пароль администратора для безопасного режима. Храните этот пароль в надежном месте.
  
Обратите внимание, что на выполнение этих команд может потребоваться несколько минут.
  
После перезапуска виртуальной машины DC1 снова подключитесь к ней.
  
### <a name="connect-to-dc1-using-domain-credentials"></a>Подключение к DC1 с помощью учетных данных домена

1. В [Azure портала](https://portal.azure.com), нажмите кнопку **группы ресурсов >** [имя группы ресурсов] **> DC1 > подключить**.
    
2. Запустите файл DC1.rdp, который будет загружен и нажмите кнопку **Подключить**.
    
3. В системе **Безопасности Windows**выберите **использовать другую учетную запись**. В поле **имя пользователя**введите **CORP\\**[имя учетной записи локального администратора].
    
4. В поле **пароль**введите пароль учетной записи локального администратора и нажмите кнопку **ОК**.
    
5. При появлении запроса нажмите кнопку **Да**.
    
Затем создайте учетную запись пользователя в Active Directory, которая будет использоваться при входе в систему на компьютерах, входящих в домен CORP. От имени администратора выполните указанную ниже команду в командной строке Windows PowerShell.
  
```
New-ADUser -SamAccountName User1 -AccountPassword (read-host "Set user password" -assecurestring) -name "User1" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

Обратите внимание на то, что при выполнении этой команды вам будет предложено ввести пароль учетной записи User1. Так как эта учетная запись будет использоваться для подключения к удаленному рабочему столу для всех компьютеров, входящих в домен CORP, используйте надежный пароль. Запишите пароль к учетной записи User1 и храните его в безопасном месте.
  
Затем настройте новую учетную запись User1 как учетную запись администратора предприятия. От имени администратора выполните указанную ниже команду в командной строке Windows PowerShell.
  
```
Add-ADPrincipalGroupMembership -Identity "CN=User1,CN=Users,DC=corp,DC=contoso,DC=com" -MemberOf "CN=Enterprise Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Domain Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Schema Admins,CN=Users,DC=corp,DC=contoso,DC=com"
```

Закрыть сеанс удаленного рабочего стола с DC1 и затем снова подключить с помощью CORP\\учетной записи User1.
  
Чтобы разрешить трафик для средства Ping, выполните указанную ниже команду в командной строке Windows PowerShell от имени администратора.
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
```

Это — ваша текущая конфигурация.
  
![Этап 2. Базовая конфигурация в Azure, включающая виртуальную машину DC1](images/49069908-29c3-4d73-87f7-debbea067261.png)
  
## <a name="phase-3-configure-app1"></a>Этап 3. Настройка APP1

APP1 предоставляет веб-службы и службы общего доступа к файлам.
  
Создание виртуальной машины Azure для APP1, введите имя группы ресурсов и выполните следующие команды в командной строке Windows Azure PowerShell на локальном компьютере.
  
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

После этого подключитесь к виртуальной машине APP1, используя имя и пароль для учетной записи локального администратора APP1. Затем откройте командную строку Windows PowerShell.
  
Чтобы проверить имя разрешения и сети обмена данными между APP1 и DC1, выполните команду **ping dc1.corp.contoso.com** и убедитесь, что существует четыре ответа.
  
Затем присоедините виртуальную машину APP1 к домену CORP, выполнив указанные ниже команды в командной строке Windows PowerShell.
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

Обратите внимание, что необходимо задать CORP\\учетные данные учетной записи User1 домена после выполнения команды **Добавить компьютер** .
  
После перезагрузки APP1 подключиться к ней с помощью CORP\\учетной записи User1, а затем откройте Windows PowerShell администраторские командную строку.
  
После этого сделайте APP1 веб-сервером, выполнив указанную ниже команду в командной строке Windows PowerShell в APP1.
  
```
Install-WindowsFeature Web-WebServer -IncludeManagementTools
```

Создайте общую папку и текстовый файл в папке на APP1 с помощью указанных ниже команд PowerShell.
  
```
New-Item -path c:\files -type directory
Write-Output "This is a shared file." | out-file c:\files\example.txt
New-SmbShare -name files -path c:\files -changeaccess CORP\User1
```

Это — ваша текущая конфигурация.
  
![Этап 3. Базовая конфигурация в Azure, включающая виртуальную машину APP1](images/92cfabb0-7f9d-4291-964d-ac32d52748d7.png)
  
## <a name="phase-4-configure-client1"></a>Этап 4. Настройка CLIENT1

CLIENT1 действует как типичный ноутбук, планшет или компьютер в интрасети Contoso.
  
Создание виртуальной машины Azure для CLIENT1, введите имя группы ресурсов и выполните следующие команды в командной строке Windows Azure PowerShell на локальном компьютере.
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name CLIENT1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name CLIENT1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName CLIENT1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for CLIENT1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName CLIENT1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsDesktop -Offer Windows-10 -Skus RS3-Pro -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "CLIENT1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

После этого подключитесь к виртуальной машине CLIENT1, используя имя и пароль для учетной записи локального администратора CLIENT1. Затем откройте командную строку Windows PowerShell от имени администратора.
  
Чтобы проверить имя разрешения и сети обмена данными между CLIENT1 и DC1, выполните команду **ping dc1.corp.contoso.com** в командной строке Windows PowerShell и убедитесь, что существует четыре ответа.
  
Затем присоедините виртуальную машину CLIENT1 к домену CORP, выполнив указанные ниже команды в командной строке Windows PowerShell.
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

Обратите внимание, что необходимо предоставить вашей CORP\\учетные данные учетной записи User1 домена после выполнения команды **Добавить компьютер** .
  
После перезагрузки компьютера CLIENT1, подключиться к ней с помощью CORP\\User1 учетной записи имя и пароль, а затем откройте командную строку Windows PowerShell уровня администратора.
  
Затем убедитесь, что у CLIENT1 есть доступ к веб-ресурсам и общим файловым ресурсам на виртуальной машине APP1.
  
### <a name="verify-client-access-to-app1"></a>Проверка возможности доступа к APP1 для CLIENT1

1. В диспетчере сервера в древовидном представлении щелкните **Локального сервера**.
    
2. В окне **свойств для CLIENT1**щелкните **на** рядом с пунктом **Конфигурация усиленной безопасности обозревателя IE**.
    
3. В разделе **Конфигурация усиленной безопасности Internet Explorer**нажмите кнопку **Отключить** для **администраторов** и **пользователей**и нажмите кнопку **ОК**.
    
4. На начальном экране выберите пункт **Internet Explorer**и нажмите кнопку **ОК**.
    
5. В адресной строке введите **http://app1.corp.contoso.com/**, а затем нажмите клавишу ВВОД. Вы увидите веб-страницу по умолчанию службы IIS для APP1.
    
6. Щелкните значок проводника на панели задач рабочего стола.
    
7. В адресной строке введите ** \\ \\app1\\файлы**, а затем нажмите клавишу ВВОД. Вы должны увидеть окне папки с содержимым в общую папку файлов.
    
8. В окне общую папку **файлов** дважды щелкните файл **Example.txt** . Вы должны увидеть содержимое файла Example.txt.
    
9. Закройте **example.txt - Блокнот** и windows **файлы** общих папок.
    
Это — ваша окончательная конфигурация.
  
![Этап 4. Базовая конфигурация в Azure, включающая виртуальную машину CLIENT1](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
Теперь ваша базовая конфигурация в Azure готова к разработке и тестированию приложений, а также к созданию дополнительных тестовых сред. 
  
> [!TIP]
> Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования Microsoft Cloud.
  
<a name="mincost"> </a>
## <a name="minimizing-the-costs-of-test-environment-virtual-machines-in-azure"></a>Минимизация расходов на виртуальные машины в тестовой среде в Azure

Чтобы снизить затраты на работу виртуальных машин тестовой среды, можно выполнить одно из указанных ниже действий.
  
- Создайте тестовую среду и проведите необходимое тестирование и демонстрацию как можно скорее. После завершения удалите группу ресурсов для тестовой среды.
    
- 	Завершите работу виртуальных машин своей тестовой среды, приведя их в освобожденное состояние.
    
Чтобы завершить работу виртуальных машин с помощью Azure PowerShell, введите имя группы ресурсов и выполните указанные ниже команды.
  
```
$rgName="<your resource group name>"
Stop-AzureRMVM -ResourceGroupName $rgName -Name "CLIENT1" -Force
Stop-AzureRMVM -ResourceGroupName $rgName -Name "APP1" -Force
Stop-AzureRMVM -ResourceGroupName $rgName -Name "DC1" -Force
```

Чтобы виртуальные машины, находящиеся в остановленном (освобожденном) состоянии, работали должным образом после запуска и вывода их из этого состояния, запускайте их в следующем порядке:
  
1. DC1
2. APP1
3. CLIENT1
    
Чтобы запустить виртуальные машины по порядку с помощью Azure PowerShell, введите имя группы ресурсов и выполните указанные ниже команды.
  
```
$rgName="<your resource group name>"
Start-AzureRMVM -ResourceGroupName $rgName -Name "DC1"
Start-AzureRMVM -ResourceGroupName $rgName -Name "APP1"
Start-AzureRMVM -ResourceGroupName $rgName -Name "CLIENT1"
```

## <a name="see-also"></a>См. также

- [Среда разработки и тестирования Office 365](office-365-dev-test-environment.md)
- [DirSync для среды разработки и тестирования Office 365](dirsync-for-your-office-365-dev-test-environment.md)
- [Cloud App Security для среды разработки и тестирования Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
- [Advanced Threat Protection в среде разработки и тестирования Office 365](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
- [Освоение облака и гибридные решения](cloud-adoption-and-hybrid-solutions.md)
