---
title: Среда разработки и тестирования Microsoft 365 корпоративный
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 6f916a77-301c-4be2-b407-6cec4d80df76
description: 'Сводка: Используйте руководство в лаборатории тестирования для создания среды разработки или тестирования, включающего Office 365 E5, мобильности Enterprise + E5 безопасности (Командной) и компьютера под управлением Windows 10 Enterprise.'
ms.openlocfilehash: 9ef1c13d7ae194ff4ba31abaf379529220ffa14f
ms.sourcegitcommit: 62c0630cc0d2611710e73e0592bddfe093e00783
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="the-microsoft-365-enterprise-devtest-environment"></a>Среда разработки и тестирования Microsoft 365 корпоративный

 **Сводка:** В этом документе Test Lab Guide используйте для создания среды разработки или тестирования, включающего Office 365 E5, мобильности Enterprise + E5 безопасности (Командной) и компьютера под управлением Windows 10 Enterprise.
  
В этой статье предоставляются пошаговые инструкции по созданию упрощенный среде для тестирования компоненты и функциональные возможности [Microsoft 365](https://www.microsoft.com/microsoft-365/enterprise)для предприятия.
  
## <a name="phase-1-create-your-office-365-e5-subscription"></a>Этап 1. Создание подписки Office 365 E5

Выполните действия, описанные в этап 2 и 3 этапа [разработки и тестовой среде Office 365](office-365-dev-test-environment.md) для создания среды разработки и тестирования lightweight Office 365, как показано на рисунке 1.
  
**На рисунке 1: Office 365 E5 подписки по программе его Azure Active Directory (AD) клиента и учетные записи пользователей**

![Этап 1 для среды разработки и тестирования Microsoft 365 корпоративный](images/65bb027b-fb59-46eb-aec2-38c0af425168.png)

> [!NOTE]
> Пробной подписки Office 365 E5 — 30 дней, которые могут быть легко расширены до 60 дней. Для постоянного dev/тестовой среды создайте новую оплата за подписки с небольшого числа лицензий. 
  
## <a name="phase-2-add-ems"></a>Этап 2. Добавление EMS

На этом этапе можно оформить пробную подписку на EMS E5 и добавить ее к той же организации, для которой создана пробная подписка на Office 365 E5.
  
Во-первых добавьте E5 Командной пробной подписки и назначьте лицензии Командной свою учетную запись глобального администратора.
  
1. С помощью закрытого экземпляр веб-браузер войдите в портал Office 365 с свои учетные данные глобального администратора. Дополнительные сведения см [Where для входа в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Выберите плитку **Администрирование**.
    
3. На вкладке **Центр администрирования Office** в браузере на панели навигации слева щелкните **Выставление счетов > Приобретение служб**.
    
4. На странице " **службы приобретения** " Поиск элемента **мобильной работы предприятия + E5 безопасности** . Наведите указатель мыши на его и нажмите кнопку **Пуск бесплатную пробную версию**.
    
5. На странице **Подтверждение заказа** щелкните **Попробовать сейчас**.
    
6. На странице **Получение заказа** нажмите кнопку **Продолжить**.
    
7. На вкладке браузера **Центр администрирования Office365** на панели навигации слева щелкните **Пользователи > Активные пользователи**.
    
8. Выберите учетную запись глобального администратора и нажмите кнопку **Изменить** для **лицензий на продукт**.
    
9. В области **лицензий на продукт** включить лицензии для **мобильных устройств предприятия + E5 безопасности** для **на**, нажмите кнопку **Сохранить** и дважды нажмите кнопку **Закрыть** .
    
> [!NOTE]
> Период пробной подписки на Enterprise Mobility + Security E5 составляет 90 дней. Чтобы создать постоянную среду тестирования и разработки, создайте новую платную подписку с небольшим количеством лицензий. 
  
 ***Завершения этапа 3*** [Office 365 dev/тестовой среде](office-365-dev-test-environment.md), повторите шаги 8 и 9 предыдущей процедуры для всех других учетных записей (2 пользователя, пользователь 3, 4 пользователя и пользователь 5).
  
Теперь ваша среда разработки и тестирования содержит:
  
- Office 365 корпоративный E5 и E5 Командной пробной подписки, общий доступ к одной Azure AD клиента со списком учетных записей пользователей.
- Использование Office 365 E5 и E5 Командной включены все соответствующие учетные записи пользователей (только что глобального администратора или все пять учетных записей пользователей).
    
На рисунке 2 показана полученная в итоге конфигурация с EMS.
  
**На рисунке 2: Добавление Командной пробной подписки**

![Этап 2 для среды разработки и тестирования Microsoft 365 корпоративный](images/8a01a483-3de2-41f3-a845-141c7edd0cb0.png)
  
## <a name="phase-3-create-a-windows-10-enterprise-computer"></a>Этап 3. Создание изолированного компьютера с ОС Windows 10 Корпоративная

На этом этапе можно создать изолированный компьютер под управлением Windows 10 Корпоративная.
  
### <a name="physical-computer"></a>Физический компьютер

Получите личный компьютер и установить Windows 10 Enterprise на него. Вы можете загрузить Windows 10 корпоративной пробной версии [здесь](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).
  
### <a name="virtual-machine"></a>Виртуальная машина

Создание виртуальной машины с помощью низкоуровневой оболочки собственное и установить Windows 10 Enterprise на него. Вы можете загрузить Windows 10 корпоративной пробной версии [здесь](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).
  
### <a name="virtual-machine-in-azure"></a>Виртуальная машина в Azure

Создание виртуальной машины Windows 10 в Microsoft Azure, ***необходимо иметь подписку на основе Visual Studio***, которой имеют доступ к нужному изображению для Windows 10 Enterprise. Другие типы Azure подписки, например пробной версии и платной подписки нет доступа на данное изображение.
  
> [!NOTE]
> Следующие наборы команд использовать последнюю версию Windows Azure PowerShell. В разделе [Начало работы с Windows Azure PowerShell командлетов](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/). Эти команды построения наборов виртуальной машины Windows 10 Enterprise с именем WIN10 и всех его инфраструктура, необходимая, включая группы ресурсов, учетной записи хранилища и виртуальной сети. Если вы уже знакомы с помощью служб инфраструктуры, можно адаптировать эти инструкции в соответствии с уже развернутого инфраструктуры. 
  
Сначала запустите командную строку Microsoft PowerShell.
  
Войдите в свою учетную запись Azure с помощью указанной ниже команды.
  
```
Login-AzureRMAccount
```

Получите имя подписки с помощью следующей команды.
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

Задайте подпиской Azure. Замените все содержимое в кавычки, включая \< и > символов с правильным именем.
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

Затем создайте группу ресурсов. Чтобы выбрать уникальное имя для группы ресурсов, с помощью этой команды отобразите имеющиеся группы ресурсов.
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Создание новой группы ресурсов с помощью следующих команд. Замените все содержимое в кавычки, включая \< и > символов с правильные имена.
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

Далее используйте приведенные ниже команды для создания новой виртуальной сети и виртуальной машины WIN10. При появлении запроса укажите имя и пароль учетной записи локального администратора WIN10 и сохраните их в надежном месте.
  
```
$corpnetSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzureRMVirtualNetwork -Name "M365Ent-TestLab" -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name "M365Ent-TestLab"
$nsg=Get-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
$pip=New-AzureRMPublicIpAddress -Name WIN10-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name WIN10-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName WIN10 -VMSize Standard_D1_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for WIN10."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName WIN10 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsDesktop -Offer Windows-10 -Skus RS3-Pro -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name WIN10-TestLab-OSDisk -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

## <a name="phase-4-join-your-windows-10-computer-to-azure-ad"></a>Этап 4. Присоединение компьютера с Windows 10 к Azure AD

После создания физической или виртуальной машине с Windows 10 Enterprise вход с учетной записью локального администратора.
  
> [!NOTE]
> Для виртуальных машин в Azure подключиться к ней с помощью [этих инструкций](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon). Вход с помощью учетных данных учетной записи локального администратора. 
  
Затем присоедините компьютер WIN10 к клиенту Azure AD, отвечающему за ваши подписки Office 365 и EMS.
  
1. На рабочем столе компьютера WIN10, нажмите кнопку **Пуск > Параметры > учетные записи > доступа к работе и в школе > подключить**.
    
2. В диалоговом окне **Настройка рабочего или школы учетной записи** нажмите кнопку **присоединиться к устройству Azure Active Directory**.
    
3. В **работы или учетная запись школа**, введите имя учетной записи глобального администратора подписки Office 365 и нажмите кнопку **Далее**.
    
4. В поле **Введите пароль**введите пароль для учетной записи глобального администратора и нажмите кнопку **Вход**.
    
5. При появлении запроса убедитесь в том, что это вашей организации, нажмите кнопку **присоединиться**и нажмите кнопку **Готово**.
    
6. Закройте окно параметров.
    
Затем установите Office 2016 на компьютере WIN10.
  
1. Откройте браузер пограничного сервера Microsoft и вход на портал Office 365 свои учетные данные глобального администратора. Дополнительные сведения см [Where для входа в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. На вкладке **Microsoft Office для дома** щелкните **установить 2016 Office**.
    
3. При появлении запроса в возможные действия, выберите пункт **выполнить**и нажмите кнопку **Да** для **Контроль учетных записей пользователей**.
    
4. Дождитесь Office для завершения установки. При появлении **вы все set!**, дважды нажмите кнопку **Закрыть** .
    
На рисунке 3 представлена итоговая среда, в которую входит компьютер WIN10, присоединенный к клиенту Azure AD, отвечающему за подписки Office 365 и EMS.
  
**На рисунке 3: Добавление учетной записи компьютера WIN10 к клиенту Azure AD**

![Этап 4 для среды разработки и тестирования Microsoft 365 корпоративный](images/20680f6a-f77e-4333-aaa9-f7cf5e4b0d03.png)
  
Теперь вы готовы экспериментировать с дополнительными возможностями [Microsoft 365 для предприятия](https://www.microsoft.com/microsoft-365/enterprise).
  
## <a name="next-steps"></a>Дальнейшие действия

Изучите возможности Microsoft 365 корпоративный, ознакомившись со следующими дополнительными статьями:
  
- [Добавление политики управления (MAM) мобильных приложений](https://technet.microsoft.com/library/mt764059.aspx)
    
- [Регистрация операций ввода-вывода и Android](https://technet.microsoft.com/library/mt743077.aspx)
    
- [Настройки и тестирования расширенного управления безопасностью](https://technet.microsoft.com/library/mt757250.aspx)
    
- [Настройки и тестирования расширенного защиту от угроз](https://technet.microsoft.com/library/mt490479.aspx)
    
## <a name="see-also"></a>Понятия

- [Документация по Microsoft 365 для предприятия](https://docs.microsoft.com/microsoft-365-enterprise/)
- [Развертывание Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365/enterprise/deploy-microsoft-365-enterprise)
- [Один Microsoft Cloud dev/тестовой среды](the-one-microsoft-cloud-dev-test-environment.md)
- [Руководства по лаборатории тестирования для принятия облачных решений](cloud-adoption-test-lab-guides-tlgs.md)
