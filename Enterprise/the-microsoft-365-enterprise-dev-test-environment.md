---
title: Среда разработки и тестирования Microsoft 365 корпоративный
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
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 6f916a77-301c-4be2-b407-6cec4d80df76
description: 'Сводка: Используйте руководство в лаборатории тестирования для создания среды разработки или тестирования, включающего Office 365 E5, мобильности Enterprise + E5 безопасности (Командной) и компьютера под управлением Windows 10 Enterprise.'
ms.openlocfilehash: 47557b7d7bdb09e2ce2731a17d6e4b35ddcd063d
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="the-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="75f41-103">Среда разработки и тестирования Microsoft 365 корпоративный</span><span class="sxs-lookup"><span data-stu-id="75f41-103">The Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="75f41-104">**Сводка:** В этом документе Test Lab Guide используйте для создания среды разработки или тестирования, включающего Office 365 E5, мобильности Enterprise + E5 безопасности (Командной) и компьютера под управлением Windows 10 Enterprise.</span><span class="sxs-lookup"><span data-stu-id="75f41-104">**Summary:** Use this Test Lab Guide to create a dev/test environment that includes Office 365 E5, Enterprise Mobility + Security (EMS) E5, and a computer running Windows 10 Enterprise.</span></span>
  
<span data-ttu-id="75f41-105">В этой статье предоставляются пошаговые инструкции по созданию упрощенный среде для тестирования компоненты и функциональные возможности [Microsoft 365](https://www.microsoft.com/microsoft-365/enterprise)для предприятия.</span><span class="sxs-lookup"><span data-stu-id="75f41-105">This article provides you with step-by-step instructions to create a simplified environment to test the features and functionality of [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span></span>
  
## <a name="phase-1-create-your-office-365-e5-subscription"></a><span data-ttu-id="75f41-106">Этап 1. Создание подписки Office 365 E5</span><span class="sxs-lookup"><span data-stu-id="75f41-106">Phase 1: Create your Office 365 E5 subscription</span></span>

<span data-ttu-id="75f41-107">Выполните действия, описанные в этап 2 и 3 этапа из [Office 365 dev/тестовой среды](office-365-dev-test-environment.md) для создания среды разработки и тестирования lightweight Office 365, как показано на рисунке 1.</span><span class="sxs-lookup"><span data-stu-id="75f41-107">Follow the steps in Phase 2 and Phase 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md) to create a lightweight Office 365 dev/test environment, as shown in Figure 1.</span></span>
  
<span data-ttu-id="75f41-108">**На рисунке 1: Office 365 E5 подписки по программе его Azure Active Directory (AD) клиента и учетные записи пользователей**</span><span class="sxs-lookup"><span data-stu-id="75f41-108">**Figure 1: Your Office 365 E5 subscription with its Azure Active Directory (AD) tenant and user accounts**</span></span>

![Этап 1 для среды разработки и тестирования Microsoft 365 корпоративный](images/65bb027b-fb59-46eb-aec2-38c0af425168.png)
  
## <a name="phase-2-add-ems"></a><span data-ttu-id="75f41-110">Этап 2. Добавление EMS</span><span class="sxs-lookup"><span data-stu-id="75f41-110">Phase 2: Add EMS</span></span>

<span data-ttu-id="75f41-111">На этом этапе можно оформить пробную подписку на EMS E5 и добавить ее к той же организации, для которой создана пробная подписка на Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="75f41-111">In this phase, you sign up for the EMS E5 trial subscription and add it to the same organization as your Office 365 E5 trial subscription.</span></span>
  
<span data-ttu-id="75f41-112">Во-первых добавьте E5 Командной пробной подписки и назначьте лицензии Командной свою учетную запись глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="75f41-112">First, add the EMS E5 trial subscription and assign an EMS license to your global administrator account.</span></span>
  
1. <span data-ttu-id="75f41-p101">С помощью закрытого экземпляр веб-браузер войдите в портал Office 365 с свои учетные данные глобального администратора. Дополнительные сведения см [Where для входа в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="75f41-p101">With a private instance of an Internet browser, sign in to the Office 365 portal with your global administrator account credentials. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="75f41-115">Выберите плитку **Администрирование**.</span><span class="sxs-lookup"><span data-stu-id="75f41-115">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="75f41-116">На вкладке **Центр администрирования Office** в браузере на панели навигации слева щелкните **Выставление счетов > Приобретение служб**.</span><span class="sxs-lookup"><span data-stu-id="75f41-116">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="75f41-p102">На странице " **службы приобретения** " Поиск элемента **мобильной работы предприятия + E5 безопасности** . Наведите указатель мыши на его и нажмите кнопку **Пуск бесплатную пробную версию**.</span><span class="sxs-lookup"><span data-stu-id="75f41-p102">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="75f41-119">На странице **Подтверждение заказа** щелкните **Попробовать сейчас**.</span><span class="sxs-lookup"><span data-stu-id="75f41-119">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="75f41-120">На странице **Получение заказа** нажмите кнопку **Продолжить**.</span><span class="sxs-lookup"><span data-stu-id="75f41-120">On the **Order receipt** page, click **Continue**.</span></span>
    
7. <span data-ttu-id="75f41-121">На вкладке браузера **Центр администрирования Office365** на панели навигации слева щелкните **Пользователи > Активные пользователи**.</span><span class="sxs-lookup"><span data-stu-id="75f41-121">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
8. <span data-ttu-id="75f41-122">Выберите учетную запись глобального администратора и нажмите кнопку **Изменить** для **лицензий на продукт**.</span><span class="sxs-lookup"><span data-stu-id="75f41-122">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
9. <span data-ttu-id="75f41-123">В области **лицензий на продукт** включить лицензии для **мобильных устройств предприятия + E5 безопасности** для **на**, нажмите кнопку **Сохранить** и дважды нажмите кнопку **Закрыть** .</span><span class="sxs-lookup"><span data-stu-id="75f41-123">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
> [!NOTE]
> <span data-ttu-id="75f41-p103">Период пробной подписки на Enterprise Mobility + Security E5 составляет 90 дней. Чтобы создать постоянную среду тестирования и разработки, создайте новую платную подписку с небольшим количеством лицензий.</span><span class="sxs-lookup"><span data-stu-id="75f41-p103">The Enterprise Mobility + Security E5 trial subscription is 90 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
 <span data-ttu-id="75f41-126">***Завершения этапа 3*** [Office 365 dev/тестовой среде](office-365-dev-test-environment.md), повторите шаги 8 и 9 предыдущей процедуры для всех других учетных записей (2 пользователя, пользователь 3, 4 пользователя и пользователь 5).</span><span class="sxs-lookup"><span data-stu-id="75f41-126">***If you completed Phase 3 of the*** [Office 365 dev/test environment](office-365-dev-test-environment.md), repeat steps 8 and 9 of the previous procedure for all of your other accounts (User 2, User 3, User 4, and User 5).</span></span>
  
<span data-ttu-id="75f41-127">Теперь ваша среда разработки и тестирования содержит:</span><span class="sxs-lookup"><span data-stu-id="75f41-127">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="75f41-128">Пробные подписки на Office 365 корпоративный E5 и EMS для одной организации, а также один и тот же клиент Azure AD для всех учетных записей пользователей из списка.</span><span class="sxs-lookup"><span data-stu-id="75f41-128">Office 365 E5 Enterprise and EMS trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
- <span data-ttu-id="75f41-129">Использование Office 365 E5 и E5 Командной включены все соответствующие учетные записи пользователей (только что глобального администратора или все пять учетных записей пользователей).</span><span class="sxs-lookup"><span data-stu-id="75f41-129">All your appropriate user accounts (either just the global administrator or all five user accounts) are enabled to use Office 365 E5 and EMS E5.</span></span>
    
<span data-ttu-id="75f41-130">На рисунке 2 показана полученная в итоге конфигурация с EMS.</span><span class="sxs-lookup"><span data-stu-id="75f41-130">Figure 2 shows your resulting configuration, which adds EMS.</span></span>
  
<span data-ttu-id="75f41-131">**На рисунке 2: Добавление Командной пробной подписки**</span><span class="sxs-lookup"><span data-stu-id="75f41-131">**Figure 2: Adding the EMS trial subscription**</span></span>

![Этап 2 для среды разработки и тестирования Microsoft 365 корпоративный](images/8a01a483-3de2-41f3-a845-141c7edd0cb0.png)
  
## <a name="phase-3-create-a-windows-10-enterprise-computer"></a><span data-ttu-id="75f41-133">Этап 3. Создание изолированного компьютера с ОС Windows 10 Корпоративная</span><span class="sxs-lookup"><span data-stu-id="75f41-133">Phase 3: Create a Windows 10 Enterprise computer</span></span>

<span data-ttu-id="75f41-134">На этом этапе можно создать изолированный компьютер под управлением Windows 10 Корпоративная.</span><span class="sxs-lookup"><span data-stu-id="75f41-134">In this phase, you create a standalone computer running Windows 10 Enterprise.</span></span>
  
### <a name="physical-computer"></a><span data-ttu-id="75f41-135">Физический компьютер</span><span class="sxs-lookup"><span data-stu-id="75f41-135">Physical computer</span></span>

<span data-ttu-id="75f41-p104">Получите личный компьютер и установить Windows 10 Enterprise на него. Вы можете загрузить Windows 10 корпоративной пробной версии [здесь](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span><span class="sxs-lookup"><span data-stu-id="75f41-p104">Obtain a personal computer and install Windows 10 Enterprise on it. You can download the Windows 10 Enterprise trial [here](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span></span>
  
### <a name="virtual-machine"></a><span data-ttu-id="75f41-138">Виртуальная машина</span><span class="sxs-lookup"><span data-stu-id="75f41-138">Virtual machine</span></span>

<span data-ttu-id="75f41-p105">Создание виртуальной машины с помощью низкоуровневой оболочки собственное и установить Windows 10 Enterprise на него. Вы можете загрузить Windows 10 корпоративной пробной версии [здесь](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span><span class="sxs-lookup"><span data-stu-id="75f41-p105">Create a virtual machine using the hypervisor of your choice and install Windows 10 Enterprise on it. You can download the Windows 10 Enterprise trial [here](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span></span>
  
### <a name="virtual-machine-in-azure"></a><span data-ttu-id="75f41-141">Виртуальная машина в Azure</span><span class="sxs-lookup"><span data-stu-id="75f41-141">Virtual machine in Azure</span></span>

<span data-ttu-id="75f41-p106">Создание виртуальной машины Windows 10 в Microsoft Azure, ***необходимо иметь подписку на основе Visual Studio***, которой имеют доступ к нужному изображению для Windows 10 Enterprise. Другие типы Azure подписки, например пробной версии и платной подписки нет доступа на данное изображение.</span><span class="sxs-lookup"><span data-stu-id="75f41-p106">To create a Windows 10 virtual machine in Microsoft Azure, ***you must have a Visual Studio-based subscription***, which has access to the image for Windows 10 Enterprise. Other types of Azure subscriptions, such as trial and paid subscriptions, do not have access to this image.</span></span>
  
> [!NOTE]
> <span data-ttu-id="75f41-p107">Следующие наборы команд использовать последнюю версию Windows Azure PowerShell. В разделе [Начало работы с Windows Azure PowerShell командлетов](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/). Эти команды построения наборов виртуальной машины Windows 10 Enterprise с именем WIN10 и всех его инфраструктура, необходимая, включая группы ресурсов, учетной записи хранилища и виртуальной сети. Если вы уже знакомы с помощью служб инфраструктуры, можно адаптировать эти инструкции в соответствии с уже развернутого инфраструктуры.</span><span class="sxs-lookup"><span data-stu-id="75f41-p107">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/). These command sets build a Windows 10 Enterprise virtual machine named WIN10 and all of its required infrastructure, including a resource group, a storage account, and a virtual network. If you are already familiar with Azure infrastructure services, please adapt these instructions to suit your currently deployed infrastructure.</span></span> 
  
<span data-ttu-id="75f41-148">Сначала запустите командную строку Microsoft PowerShell.</span><span class="sxs-lookup"><span data-stu-id="75f41-148">First, start a Microsoft PowerShell prompt.</span></span>
  
<span data-ttu-id="75f41-149">Войдите в свою учетную запись Azure с помощью указанной ниже команды.</span><span class="sxs-lookup"><span data-stu-id="75f41-149">Sign in to your Azure account with the following command.</span></span>
  
```
Login-AzureRMAccount
```

<span data-ttu-id="75f41-150">Получите имя подписки с помощью следующей команды.</span><span class="sxs-lookup"><span data-stu-id="75f41-150">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="75f41-p108">Задайте подпиской Azure. Замените все содержимое в кавычки, включая \< и > символов с правильным именем.</span><span class="sxs-lookup"><span data-stu-id="75f41-p108">Set your Azure subscription. Replace everything within the quotes, including the \< and > characters, with the correct name.</span></span>
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

<span data-ttu-id="75f41-p109">Затем создайте группу ресурсов. Чтобы выбрать уникальное имя для группы ресурсов, с помощью этой команды отобразите имеющиеся группы ресурсов.</span><span class="sxs-lookup"><span data-stu-id="75f41-p109">Next, create a new resource group. To determine a unique resource group name, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="75f41-p110">Создание новой группы ресурсов с помощью следующих команд. Замените все содержимое в кавычки, включая \< и > символов с правильные имена.</span><span class="sxs-lookup"><span data-stu-id="75f41-p110">Create your new resource group with these commands. Replace everything within the quotes, including the \< and > characters, with the correct names.</span></span>
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="75f41-p111">Далее используйте приведенные ниже команды для создания новой виртуальной сети и виртуальной машины WIN10. При появлении запроса укажите имя и пароль учетной записи локального администратора WIN10 и сохраните их в надежном месте.</span><span class="sxs-lookup"><span data-stu-id="75f41-p111">Next, you create a new virtual network and the WIN10 virtual machine with these commands. When prompted, provide the name and password of the local administrator account for WIN10 and store these in a secure location.</span></span>
  
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

## <a name="phase-4-join-your-windows-10-computer-to-azure-ad"></a><span data-ttu-id="75f41-159">Этап 4. Присоединение компьютера с Windows 10 к Azure AD</span><span class="sxs-lookup"><span data-stu-id="75f41-159">Phase 4: Join your Windows 10 computer to Azure AD</span></span>

<span data-ttu-id="75f41-160">После создания физической или виртуальной машине с Windows 10 Enterprise вход с учетной записью локального администратора.</span><span class="sxs-lookup"><span data-stu-id="75f41-160">After the physical or virtual machine with Windows 10 Enterprise is created, sign in with a local administrator account.</span></span>
  
> [!NOTE]
> <span data-ttu-id="75f41-p112">Для виртуальных машин в Azure подключиться к ней с помощью [этих инструкций](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon). Вход с помощью учетных данных учетной записи локального администратора.</span><span class="sxs-lookup"><span data-stu-id="75f41-p112">For a virtual machine in Azure, connect to it using [these instructions](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon). Sign in with the credentials of the local administrator account.</span></span> 
  
<span data-ttu-id="75f41-163">Затем присоедините компьютер WIN10 к клиенту Azure AD, отвечающему за ваши подписки Office 365 и EMS.</span><span class="sxs-lookup"><span data-stu-id="75f41-163">Next, join the WIN10 computer to the Azure AD tenant of your Office 365 and EMS subscriptions.</span></span>
  
1. <span data-ttu-id="75f41-164">На рабочем столе компьютера WIN10, нажмите кнопку **Пуск > Параметры > учетные записи > доступа к работе и в школе > подключить**.</span><span class="sxs-lookup"><span data-stu-id="75f41-164">At the desktop of the WIN10 computer, click **Start > Settings > Accounts > Access work or school > Connect**.</span></span>
    
2. <span data-ttu-id="75f41-165">В диалоговом окне **Настройка рабочего или школы учетной записи** нажмите кнопку **присоединиться к устройству Azure Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="75f41-165">In the **Set up a work or school account** dialog box, click **Join this device to Azure Active Directory**.</span></span>
    
3. <span data-ttu-id="75f41-166">В **работы или учетная запись школа**, введите имя учетной записи глобального администратора подписки Office 365 и нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="75f41-166">In **Work or school account**, type the global administrator account name of your Office 365 subscription, and then click **Next**.</span></span>
    
4. <span data-ttu-id="75f41-167">В поле **Введите пароль**введите пароль для учетной записи глобального администратора и нажмите кнопку **Вход**.</span><span class="sxs-lookup"><span data-stu-id="75f41-167">In **Enter password**, type the password for your global administrator account, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="75f41-168">При появлении запроса убедитесь в том, что это вашей организации, нажмите кнопку **присоединиться**и нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="75f41-168">When prompted to make sure this is your organization, click **Join**, and then click **Done**.</span></span>
    
6. <span data-ttu-id="75f41-169">Закройте окно параметров.</span><span class="sxs-lookup"><span data-stu-id="75f41-169">Close the settings window.</span></span>
    
<span data-ttu-id="75f41-170">Затем установите Office 2016 на компьютере WIN10.</span><span class="sxs-lookup"><span data-stu-id="75f41-170">Next, install Office 2016 on the WIN10 computer.</span></span>
  
1. <span data-ttu-id="75f41-p113">Откройте браузер пограничного сервера Microsoft и вход на портал Office 365 свои учетные данные глобального администратора. Дополнительные сведения см [Where для входа в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="75f41-p113">Open the Microsoft Edge browser and sign in to the Office 365 portal with your global administrator account credentials. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="75f41-173">На вкладке **Microsoft Office для дома** щелкните **установить 2016 Office**.</span><span class="sxs-lookup"><span data-stu-id="75f41-173">On the **Microsoft Office Home** tab, click **Install Office 2016**.</span></span>
    
3. <span data-ttu-id="75f41-174">При появлении запроса в возможные действия, выберите пункт **выполнить**и нажмите кнопку **Да** для **Контроль учетных записей пользователей**.</span><span class="sxs-lookup"><span data-stu-id="75f41-174">When prompted with what to do, click **Run**, and then click **Yes** for **User Account Control**.</span></span>
    
4. <span data-ttu-id="75f41-p114">Дождитесь Office для завершения установки. При появлении **вы все set!**, дважды нажмите кнопку **Закрыть** .</span><span class="sxs-lookup"><span data-stu-id="75f41-p114">Wait for Office to complete its installation. When you see **You're all set!**, click **Close** twice.</span></span>
    
<span data-ttu-id="75f41-177">На рисунке 3 представлена итоговая среда, в которую входит компьютер WIN10, присоединенный к клиенту Azure AD, отвечающему за подписки Office 365 и EMS.</span><span class="sxs-lookup"><span data-stu-id="75f41-177">Figure 3 shows your resulting environment, which includes the WIN10 computer that has joined the Azure AD tenant of your Office 365 and EMS subscriptions.</span></span>
  
<span data-ttu-id="75f41-178">**На рисунке 3: Добавление учетной записи компьютера WIN10 к клиенту Azure AD**</span><span class="sxs-lookup"><span data-stu-id="75f41-178">**Figure 3: Adding the WIN10 computer account to the Azure AD tenant**</span></span>

![Этап 4 для среды разработки и тестирования Microsoft 365 корпоративный](images/20680f6a-f77e-4333-aaa9-f7cf5e4b0d03.png)
  
<span data-ttu-id="75f41-180">Теперь вы готовы экспериментировать с дополнительными возможностями [Microsoft 365 для предприятия](https://www.microsoft.com/microsoft-365/enterprise).</span><span class="sxs-lookup"><span data-stu-id="75f41-180">You are now ready to experiment with additional features of [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="75f41-181">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="75f41-181">Next steps</span></span>

<span data-ttu-id="75f41-182">Изучите возможности Microsoft 365 корпоративный, ознакомившись со следующими дополнительными статьями:</span><span class="sxs-lookup"><span data-stu-id="75f41-182">Use these additional articles to explore features of Microsoft 365 Enterprise:</span></span>
  
- [<span data-ttu-id="75f41-183">Добавление политики управления (MAM) мобильных приложений</span><span class="sxs-lookup"><span data-stu-id="75f41-183">Add mobile application management (MAM) policies</span></span>](https://technet.microsoft.com/library/mt764059.aspx)
    
- [<span data-ttu-id="75f41-184">Регистрация операций ввода-вывода и Android</span><span class="sxs-lookup"><span data-stu-id="75f41-184">Enroll iOS and Android devices</span></span>](https://technet.microsoft.com/library/mt743077.aspx)
    
- [<span data-ttu-id="75f41-185">Настройки и тестирования расширенного управления безопасностью</span><span class="sxs-lookup"><span data-stu-id="75f41-185">Configure and test Advanced Security Management</span></span>](https://technet.microsoft.com/library/mt757250.aspx)
    
- [<span data-ttu-id="75f41-186">Настройки и тестирования расширенного защиту от угроз</span><span class="sxs-lookup"><span data-stu-id="75f41-186">Configure and test Advanced Threat Protection</span></span>](https://technet.microsoft.com/library/mt490479.aspx)
    
## <a name="see-also"></a><span data-ttu-id="75f41-187">См. также</span><span class="sxs-lookup"><span data-stu-id="75f41-187">See Also</span></span>

- [<span data-ttu-id="75f41-188">Документация по Microsoft 365 для предприятия</span><span class="sxs-lookup"><span data-stu-id="75f41-188">Microsoft 365 Enterprise documentation</span></span>](https://docs.microsoft.com/microsoft-365-enterprise/)
- [<span data-ttu-id="75f41-189">Развертывание Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="75f41-189">Deploy Microsoft 365 Enterprise</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/deploy-microsoft-365-enterprise)
- [<span data-ttu-id="75f41-190">Один Microsoft Cloud dev/тестовой среды</span><span class="sxs-lookup"><span data-stu-id="75f41-190">The One Microsoft Cloud dev/test environment</span></span>](the-one-microsoft-cloud-dev-test-environment.md)
